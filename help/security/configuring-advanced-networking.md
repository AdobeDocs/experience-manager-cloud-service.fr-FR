---
title: Configuration de la mise en réseau avancée pour AEM as a Cloud Service
description: Découvrez comment configurer des fonctionnalités de réseau avancé telles que VPN ou une adresse IP de sortie dédiée pour AEM as a Cloud Service
source-git-commit: e9fa68869ca92945c44a79b783fbc8a53a875e81
workflow-type: tm+mt
source-wordcount: '2797'
ht-degree: 7%

---


# Configuration de la mise en réseau avancée pour AEM as a Cloud Service {#configuring-advanced-networking}

>[!INFO]
>
>La fonctionnalité de mise en réseau avancée fait partie de la version 2021.9.0 et sera activée pour les clients à la mi-octobre.

AEM as a Cloud Service propose plusieurs types de fonctionnalités de mise en réseau avancées, qui peuvent être configurées par les clients à l’aide des API de Cloud Manager. Celles-ci comprennent :

* [Sortie de port flexible](#flexible-port-egress)  : configurez AEM as a Cloud Service pour autoriser le trafic sortant des ports non standard.
* [Adresse IP sortante dédiée](#dedicated-egress-IP-address)  : configurez le trafic en dehors de AEM as a Cloud Service pour qu’il provient d’une adresse IP unique.
* [Réseau privé virtuel](#vpn)  : trafic sécurisé entre l’infrastructure d’un client et AEM as a Cloud Service, pour les clients qui disposent d’une technologie VPN.

Cet article décrit en détail chacune de ces options, y compris leur configuration. Pour une stratégie de configuration générale, le point d’entrée de l’API `/networkInfrastructures` est appelé au niveau du programme pour déclarer le type souhaité de mise en réseau avancée, suivi d’un appel au point d’entrée `/advancedNetworking` pour chaque environnement afin d’activer l’infrastructure et de configurer des paramètres spécifiques à l’environnement. Pour chaque syntaxe formelle, ainsi que les exemples de requêtes et de réponses, reportez-vous aux points de terminaison appropriés dans la documentation de l’API Cloud Manager .

Lorsque vous décidez entre une sortie de port flexible et une adresse IP de sortie dédiée, il est recommandé de choisir une sortie de port flexible si aucune adresse IP spécifique n’est requise, car Adobe peut optimiser les performances du trafic de sortie de port flexible.

>[!INFO]
>
>La mise en réseau avancée n’est pas disponible pour le programme Sandbox.

>[!NOTE]
>
>Les clients déjà configurés avec la technologie de sortie dédiée héritée qui doivent configurer l’une de ces options ne doivent pas le faire ou la connectivité du site peut être affectée. Pour obtenir de l’aide, contactez l’assistance Adobe.

## Sortie de port flexible {#flexible-port-egress}

Cette fonctionnalité de mise en réseau avancée vous permet de configurer AEM as a Cloud Service pour récupérer le trafic via des ports autres que HTTP (port 80) et HTTPS (port 443), qui sont ouverts par défaut.

### Considérations {#flexible-port-egress-considerations}

Une sortie de port flexible est recommandée si vous n’avez pas besoin de VPN et n’avez pas besoin d’une adresse IP de sortie dédiée, car le trafic qui ne dépend pas d’une sortie dédiée peut atteindre un débit supérieur.

### Configuration {#configuring-flexible-port-egress-provision}

Une fois par programme, le point de terminaison `/program/<programId>/networkInfrastructures` du POST est appelé, il suffit de transmettre la valeur `flexiblePortEgress` pour le paramètre `kind` et la région. Le point de terminaison répond avec la balise `network_id`, ainsi que d’autres informations, y compris le statut. L’ensemble complet des paramètres et la syntaxe exacte doivent être référencés dans la documentation API.

Une fois appelée, l’approvisionnement de l’infrastructure réseau prend généralement environ 15 minutes. Un appel au [point de terminaison de l’environnement ](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getEnvironment) de Cloud Manager afficherait l’état &quot;prêt&quot;.

Si la configuration de sortie de port flexible à l’échelle du programme est prête, le point de terminaison `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` doit être appelé par environnement pour activer la mise en réseau au niveau de l’environnement et déclarer toute règle de transfert de port. Les paramètres sont configurables par environnement afin d’offrir une certaine flexibilité.

Les règles de transfert de port doivent être déclarées pour tout port autre que le port 80/443 en spécifiant l’ensemble des hôtes de destination (noms ou adresses IP, et avec les ports). Pour chaque hôte de destination, les clients doivent mapper le port de destination prévu à un port entre 30 000 et 30 999.

L’API doit répondre en quelques secondes seulement, indiquant un état de mise à jour. Après environ 10 minutes, la méthode `GET` du point de terminaison doit indiquer que la mise en réseau avancée est activée.

### Mises à jour {#updating-flexible-port-egress-provision}

La configuration au niveau du programme peut être mise à jour en appelant le point de terminaison `PUT /api/program/<program_id>/network/<network_id>` et prendra effet dans quelques minutes.

>[!NOTE]
>
> Le paramètre &quot;type&quot; (`flexiblePortEgress`, `dedicatedEgressIP` ou `VPN`) ne peut pas être modifié. Contactez l’assistance clientèle pour obtenir de l’aide, en décrivant ce qui a déjà été créé et la raison du changement.

Les règles de transfert de port par environnement peuvent être mises à jour en appelant à nouveau le point de terminaison `PUT /program/{programId}/environment/{environmentId}/advancedNetworking`, en veillant à inclure l’ensemble complet des paramètres de configuration, plutôt qu’un sous-ensemble.

### Suppression ou désactivation d’une sortie de port flexible {#deleting-disabling-flexible-port-egress-provision}

Pour **supprimer** l’infrastructure réseau, soumettez un ticket d’assistance clientèle, décrivant ce qui a été créé et pourquoi il doit être supprimé.

Pour **désactiver** sortie de port flexible à partir d’un environnement particulier, appelez `DELETE [/program/{programId}/environment/{environmentId}/advancedNetworking]()`.

Pour plus d’informations, voir la [Documentation de l’API Cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/disableEnvironmentAdvancedNetworkingConfiguration).

### Routage du trafic {#flexible-port-egress-traffic-routing}

Le trafic HTTP ou https qui va vers des destinations via les ports 80 ou 443 passe par un proxy préconfiguré, en supposant que la bibliothèque de réseau Java standard soit utilisée. Pour le trafic http ou https passant par d’autres ports, un proxy doit être configuré à l’aide des propriétés suivantes.

* `AEM_HTTP_PROXY_HOST / AEM_HTTPS_PROXY_HOST`
* `AEM_HTTP_PROXY_PORT / AEM_HTTPS_PROXY_PORT`

Par exemple, voici un exemple de code pour envoyer une requête à `www.example.com:8443` :

```java
HttpsHost target = new HttpsHost("example.com", 8443, "https");
 
HttpHost proxy = new HttpHost(System.getenv("AEM_HTTPS_PROXY_HOST"),
                              Integer.parseInt(System.getenv("AEM_HTTPS_PROXY_PORT")),
                              "https");
 
RequestConfig config = RequestConfig.custom().setProxy(proxy).build();
 
HttpGet request = new HttpGet("/");
request.setConfig(config);
CloseableHttpResponse response = httpclient.execute(target, request);
```

Si vous utilisez des bibliothèques réseau Java non standard, configurez des proxies à l’aide des propriétés ci-dessus, pour tout le trafic.

Le trafic non http/s avec des destinations par le biais de ports déclarés dans le paramètre `portForwards` doit référencer une propriété appelée `AEM_PROXY_HOST`, ainsi que le port mappé. Par exemple :

```java
DriverManager.getConnection("jdbc:mysql://" + System.getenv("AEM_PROXY_HOST") + ":53306/test");
```

Le tableau ci-dessous décrit le routage du trafic :

<table>
<thead>
  <tr>
    <th>Trafic</th>
    <th>Condition de destination</th>
    <th>Port</th>
    <th>Connexion</th>
    <th>Exemple</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><b>Protocole Http ou https</b></td>
    <td>Trafic http/s standard</td>
    <td>80 ou 443</td>
    <td>Autorisé</td>
    <td></td>
  </tr> 
  <tr>
    <td></td>
    <td>Trafic non standard (sur d’autres ports en dehors des ports 80 ou 443) via un proxy http configuré à l’aide de ces variables d’environnement :<br><ul>
     <li>AEM_HTTP_PROXY_HOST / AEM_HTTPS_PROXY_HOST</li>
     <li>AEM_HTTP_PROXY_PORT / AEM_HTTPS_PROXY_PORT</li>
    </ul>
    <td>Ports en dehors de 80 ou 443</td>
    <td>Autorisé</td>
  </tr>
  <tr>
    <td></td>
    <td>Trafic non standard (sur d’autres ports en dehors des ports 80 ou 443) n’utilisant pas de proxy http</td>
    <td>Ports en dehors de 80 ou 443</td>
    <td>Bloquée</td>
    <td></td>
  </tr>
  <tr>
    <td><b>Non http ou non https</b></td>
    <td>Le client se connecte à la variable d’environnement <code>AEM_PROXY_HOST</code> à l’aide d’une balise <code>portOrig</code> déclarée dans le paramètre de l’API <code>portForwards</code>.</td>
    <td>Valeur nulle ou non nulle</td>
    <td>Autorisé</td>
    <td><code>mysql.example.com:3306</code></td>
  </tr>
  <tr>
    <td></td>
    <td>Tout le reste</td>
    <td>Valeur nulle ou non nulle</td>
    <td>Bloquée</td>
    <td><code>db.example.com:5555</code></td>
  </tr>
</tbody>
</table>

**Configuration Apache/Dispatcher**

La directive `mod_proxy` du niveau Apache/Dispatcher AEM Cloud Service peut être configurée à l’aide des propriétés décrites ci-dessus.

```
ProxyRemote "http://example.com" "http://${AEM_HTTP_PROXY_HOST}:${AEM_HTTP_PROXY_PORT}"
ProxyPass "/somepath" "http://example.com"
ProxyPassReverse "/somepath" "http://example.com"
```

```
SSLProxyEngine on //needed for https backends
 
ProxyRemote "https://example.com:8443" "http://${AEM_HTTPS_PROXY_HOST}:${AEM_HTTPS_PROXY_PORT}"
ProxyPass "/somepath" "https://example.com:8443"
ProxyPassReverse "/somepath" "https://example.com:8443"
```

## Adresse IP Egress dédiée {#dedicated-egress-IP-address}

>[!NOTE]
>
>Si vous avez reçu une adresse IP de sortie dédiée avant la version de septembre 2021 (10/6/21), reportez-vous à la section [Clients d’adresse sortante dédiée hérités](#legacy-dedicated-egress-address-customers).

### Avantages {#benefits}

Cette adresse IP dédiée peut améliorer la sécurité lors de l’intégration avec les fournisseurs SaaS (comme un fournisseur de solutions de gestion de la relation client) ou d’autres intégrations en dehors d’AEM as a Cloud Service qui offrent une liste d’adresses IP autorisées. En ajoutant l’adresse IP dédiée à la liste autorisée, elle garantit que seul le trafic provenant de l’AEM Cloud Service du client est autorisé à circuler dans le service externe. Cela s’ajoute au trafic provenant de toute autre adresse IP autorisée.

Si la fonction d’adresse IP dédiée n’est pas activée, le trafic provenant d’AEM as a Cloud Service passe par un jeu d’adresses IP partagées avec d’autres clients.

### Configuration {#configuring-dedicated-egress-provision}

>[!INFO]
>
>La fonctionnalité de transfert Splunk n’est pas possible à partir d’une adresse IP de sortie dédiée.

La configuration de l’adresse IP de sortie dédiée est identique à [sortie de port flexible](#configuring-flexible-port-egress-provision).

La principale différence est que le trafic sortira toujours d’une adresse IP dédiée et unique. Pour trouver cette adresse IP, utilisez un résolveur DNS pour identifier l’adresse IP associée à `p{PROGRAM_ID}.external.adobeaemcloud.com`. L’adresse IP ne doit pas changer, mais si elle doit changer à l’avenir, une notification avancée sera fournie.

En plus des règles de routage prises en charge par la sortie de port flexible dans le point de terminaison `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking`, l’adresse IP de sortie dédiée prend en charge un paramètre `nonProxyHosts`. Cela vous permet de déclarer un ensemble d’hôtes qui doivent passer par une plage d’adresses IP partagées plutôt que par l’adresse IP dédiée, ce qui peut s’avérer utile puisque le trafic passant par les adresses IP partagées peut être encore optimisé. Les URL `nonProxyHost` peuvent suivre les modèles de `example.com` ou `*.example.com`, où le caractère générique n’est pris en charge qu’au début du domaine.

Lors du choix entre une sortie de port flexible et une adresse IP de sortie dédiée, les clients doivent choisir une sortie de port flexible si aucune adresse IP spécifique n’est requise, car l’Adobe peut optimiser les performances du trafic de sortie de port flexible.

### Routage du trafic {#dedcated-egress-ip-traffic-routing}

<table>
<thead>
  <tr>
    <th>Trafic</th>
    <th>Condition de destination</th>
    <th>Port</th>
    <th>Connexion</th>
    <th>Exemple</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><b>Protocole Http ou https</b></td>
    <td>Trafic vers Azure ou les services Adobe</td>
    <td>Valeur nulle ou non nulle</td>
    <td>Via les adresses IP partagées de la grappe (et non l’adresse IP dédiée)</td>
    <td>adobe.io<br>api.windows.net</td>
  </tr>
  <tr>
    <td></td>
    <td>Hôte correspondant au paramètre <code>nonProxyHosts</code></td>
    <td>80 ou 443</td>
    <td>Via les adresses IP de la grappe partagée</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Hôte correspondant au paramètre <code>nonProxyHosts</code></td>
    <td>Ports en dehors de 80 ou 443</td>
    <td>Bloquée</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Par le biais de la configuration du proxy http, configurée par défaut pour le trafic http/s à l’aide de la bibliothèque cliente HTTP Java standard</td>
    <td>Valeur nulle ou non nulle</td>
    <td>Via l’adresse IP sortante dédiée</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Ignore la configuration du proxy http (par exemple, si elle est explicitement supprimée de la bibliothèque cliente HTTP Java standard ou si une bibliothèque Java qui ignore la configuration du proxy standard est utilisée).</td>
    <td>80 ou 443</td>
    <td>Via les adresses IP de la grappe partagée</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Ignore la configuration du proxy http (par exemple, si elle est explicitement supprimée de la bibliothèque cliente HTTP Java standard ou si une bibliothèque Java qui ignore la configuration du proxy standard est utilisée).</td>
    <td>Ports en dehors de 80 ou 443</td>
    <td>Bloquée</td>
    <td></td>
  </tr>
  <tr>
    <td><b>Non http ou non https</b></td>
    <td>Le client se connecte à la variable <code>AEM_PROXY_HOST</code> env à l’aide d’un <code>portOrig</code> déclaré dans le paramètre de l’API <code>portForwards</code>.</td>
    <td>Valeur nulle ou non nulle</td>
    <td>Via l’adresse IP sortante dédiée</td>
    <td><code>mysql.example.com:3306</code></td>
  </tr>
  <tr>
    <td></td>
    <td>Autre chose</td>
    <td></td>
    <td>Bloquée</td>
    <td></td>
  </tr>
</tbody>
</table>

## Clients d’adresse sortante dédiés hérités {#legacy-dedicated-egress-address-customers}

Si vous avez reçu l’attribution d’une adresse IP de sortie dédiée avant la version 2021.09.30, votre fonction IP de sortie dédiée fonctionnera comme décrit ci-dessous.

### Utilisation de la fonctionnalité {#feature-usage}

Cette fonctionnalité est compatible avec les bibliothèques ou le code Java qui génèrent du trafic sortant, à condition qu’ils utilisent les propriétés système Java standard pour les configurations de proxy. Dans la pratique, cela devrait inclure la plupart des bibliothèques courantes.

Voici un exemple de code :

```java
public JSONObject getJsonObject(String relativePath, String queryString) throws IOException, JSONException {
  String relativeUri = queryString.isEmpty() ? relativePath : (relativePath + '?' + queryString);
  URL finalUrl = endpointUri.resolve(relativeUri).toURL();
  URLConnection connection = finalUrl.openConnection();
  connection.addRequestProperty("Accept", "application/json");
  connection.addRequestProperty("X-API-KEY", apiKey);

  try (InputStream responseStream = connection.getInputStream(); Reader responseReader = new BufferedReader(new InputStreamReader(responseStream, Charsets.UTF_8))) {
    return new JSONObject(new JSONTokener(responseReader));
  }
}
```

Certaines bibliothèques nécessitent une configuration explicite pour utiliser les propriétés système Java standard pour les configurations de proxy.

Exemple utilisant Apache HttpClient qui nécessite des appels explicites à
[`HttpClientBuilder.useSystemProperties()`](https://hc.apache.org/httpcomponents-client-4.5.x/current/httpclient/apidocs/org/apache/http/impl/client/HttpClientBuilder.html) ou utilisez
[`HttpClients.createSystem()`](https://hc.apache.org/httpcomponents-client-4.5.x/current/httpclient/apidocs/org/apache/http/impl/client/HttpClients.html#createSystem()) :

```java
public JSONObject getJsonObject(String relativePath, String queryString) throws IOException, JSONException {
  String relativeUri = queryString.isEmpty() ? relativePath : (relativePath + '?' + queryString);
  URL finalUrl = endpointUri.resolve(relativeUri).toURL();

  HttpClient httpClient = HttpClientBuilder.create().useSystemProperties().build();
  HttpGet request = new HttpGet(finalUrl.toURI());
  request.setHeader("Accept", "application/json");
  request.setHeader("X-API-KEY", apiKey);
  HttpResponse response = httpClient.execute(request);
  String result = EntityUtils.toString(response.getEntity());
}
```

La même adresse IP dédiée est appliquée à tous les programmes d’un client dans son organisation Adobe ainsi qu’à tous les environnements de chacun de ses programmes. Elle s’applique aux services de création et de publication.

Seuls les ports HTTP et HTTPS sont pris en charge. Cela inclut HTTP/1.1 et HTTP/2 lorsqu’ils sont chiffrés.

### Considérations relatives au débogage {#debugging-considerations}

Afin de vérifier que le trafic est effectivement sortant sur l’adresse IP dédiée attendue, vérifiez les journaux dans le service de destination, si disponible. Dans le cas contraire, il peut s’avérer utile d’appeler un service de débogage tel que [https://ifconfig.me/IP](https://ifconfig.me/IP), qui renverra l’adresse IP d’appel.

## Réseau privé virtuel (VPN) {#vpn}

VPN permet de se connecter à une infrastructure ou un centre de données on-premise à partir de l’auteur, de la publication ou de l’aperçu. Par exemple, pour accéder à une base de données.

Il permet également de se connecter aux fournisseurs SaaS tels qu’un fournisseur de gestion de la relation client qui prend en charge VPN ou de se connecter à partir d’un réseau d’entreprise pour AEM l’auteur, l’aperçu ou la publication as a Cloud Service.

La plupart des périphériques VPN avec technologie IPSec sont pris en charge. Consultez la liste des périphériques sur [cette page](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpn-devices#devicetable), en fonction des informations de la colonne **Instructions de configuration basées sur la route**. Configurez le périphérique comme décrit dans le tableau.

### Remarques générales {#general-vpn-considerations}

* La prise en charge est limitée à une connexion VPN unique.
* La fonctionnalité de transfert Splunk n’est pas possible via une connexion VPN.

### Création {#vpn-creation}

Une fois par programme, le point de terminaison `/program/<programId>/networkInfrastructures` du POST est appelé, transmettant un payload des informations de configuration, notamment : la valeur de &quot;vpn&quot; pour le paramètre `kind`, la région, l’espace d’adresse (liste des CIDR - notez que cela ne peut pas être modifié plus tard), les résolveurs DNS (pour résoudre les noms dans le réseau du client) et les informations de connexion VPN telles que la configuration de la passerelle, la clé VPN partagée et la politique de sécurité IP. Le point de terminaison répond avec la balise `network_id`, ainsi que d’autres informations, y compris le statut. L’ensemble complet des paramètres et la syntaxe exacte doivent être référencés dans la [documentation de l’API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/createNetworkInfrastructure).

Une fois appelée, l’approvisionnement de l’infrastructure réseau prend généralement entre 45 et 60 minutes. La méthode de GET de l’API peut être appelée pour renvoyer l’état actuel, qui va éventuellement passer de `creating` à `ready`. Consultez la documentation de l’API pour tous les états.

Si la configuration VPN à portée de programme est prête, le point de terminaison `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` doit être appelé par environnement pour activer la mise en réseau au niveau de l’environnement et déclarer toute règle de transfert de port. Les paramètres sont configurables par environnement afin d’offrir une certaine flexibilité.

Pour plus d’informations, consultez la [documentation de l’API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/enableEnvironmentAdvancedNetworkingConfiguration) .

Les règles de transfert de port doivent être déclarées pour tout trafic TCP non http/s qui doit être acheminé via le VPN en spécifiant le jeu d’hôtes de destination (noms ou adresses IP, et avec des ports). Pour chaque hôte de destination, les clients doivent mapper le port de destination prévu à un port compris entre 30 000 et 30 999, où les valeurs doivent être uniques dans tous les environnements du programme. Les clients peuvent également répertorier un ensemble d’URL dans le paramètre `nonProxyHosts`, qui déclare l’URL pour laquelle le trafic doit contourner le routage VPN, mais au lieu de cela via une plage IP partagée. Il suit les modèles de `example.com` ou `*.example.com`, où le caractère générique n’est pris en charge qu’au début du domaine.

L’API doit répondre en quelques secondes seulement, indiquant un état de `updating` et après environ 10 minutes, un appel au point de terminaison de l’environnement de Cloud Manager afficherait un état de `ready`, indiquant que la mise à jour de l’environnement a été appliquée.

Notez que même s’il n’existe aucune règle de routage du trafic de l’environnement (hôtes ou contours), `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` doit toujours être appelé, avec une charge utile vide.

### Mettre à jour le VPN {#updating-the-vpn}

La configuration VPN au niveau du programme peut être mise à jour en appelant le point d’entrée `PUT /api/program/<program_id>/network/<network_id>`.

Notez que l’espace d’adresse ne peut pas être modifié après la configuration VPN initiale. Si cela est nécessaire, contactez le service clientèle. De plus, le paramètre `kind` (`flexiblePortEgress`, `dedicatedEgressIP` ou `VPN`) ne peut pas être modifié. Contactez l’assistance clientèle pour obtenir de l’aide, en décrivant ce qui a déjà été créé et la raison du changement.

Les règles de routage par environnement peuvent être mises à jour en appelant de nouveau le point de terminaison `PUT /program/{programId}/environment/{environmentId}/advancedNetworking`, en veillant à inclure l’ensemble du paramètre de configuration, plutôt qu’un sous-ensemble. Les mises à jour d’environnement prennent généralement 5 à 10 minutes à être appliquées.

### Suppression ou désactivation du VPN {#deleting-or-disabling-the-vpn}

Pour supprimer l’infrastructure réseau, soumettez un ticket d’assistance clientèle, décrivant ce qui a été créé et pourquoi il doit être supprimé.

Pour désactiver le VPN pour un environnement particulier, appelez `DELETE /program/{programId}/environment/{environmentId}/advancedNetworking`. Pour plus d’informations, consultez la [documentation de l’API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/disableEnvironmentAdvancedNetworkingConfiguration).

### Routage du trafic {#vpn-traffic-routing}

Le tableau ci-dessous décrit le routage du trafic.

<table>
<thead>
  <tr>
    <th>Trafic</th>
    <th>Condition de destination</th>
    <th>Port</th>
    <th>Connexion</th>
    <th>Exemple</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><b>Protocole Http ou https</b></td>
    <td>Trafic vers Azure ou les services Adobe</td>
    <td>Valeur nulle ou non nulle</td>
    <td>Via les adresses IP partagées de la grappe (et non l’adresse IP dédiée)</td>
    <td>adobe.io<br>api.windows.net</td>
  </tr>
  <tr>
    <td></td>
    <td>Hôte correspondant au paramètre <code>nonProxyHosts</code></td>
    <td>80 ou 443</td>
    <td>Via les adresses IP de la grappe partagée</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Hôte correspondant au paramètre <code>nonProxyHosts</code></td>
    <td>Ports en dehors de 80 ou 443</td>
    <td>Bloquée</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Si l’adresse IP tombe dans la plage d’adresses <i>de la passerelle VPN</i> et par le biais d’une configuration de proxy http (configurée par défaut pour le trafic http/s à l’aide de la bibliothèque cliente HTTP Java standard)</td>
    <td>Valeur nulle ou non nulle</td>
    <td>Par le VPN</td>
    <td><code>10.0.0.1:443</code>Il peut également s’agir d’un nom d’hôte.</td>
  </tr>
  <tr>
    <td></td>
    <td>Si l'adresse IP ne tombe pas dans la plage <i>espace d'adresse de la passerelle VPN</i>, et par le biais d'une configuration de proxy http (configurée par défaut pour le trafic http/s à l'aide de la bibliothèque cliente HTTP Java standard)</td>
    <td>Valeur nulle ou non nulle</td>
    <td>Via l’adresse IP sortante dédiée</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Ignore la configuration du proxy http (par exemple, si elle est explicitement supprimée de la bibliothèque cliente HTTP Java standard ou si vous utilisez une bibliothèque Java qui ignore la configuration du proxy standard).
</td>
    <td>80 ou 443</td>
    <td>Via les adresses IP de la grappe partagée</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Ignore la configuration du proxy http (par exemple, si elle est explicitement supprimée de la bibliothèque cliente HTTP Java standard ou si vous utilisez une bibliothèque Java qui ignore la configuration du proxy standard).</td>
    <td>Ports en dehors de 80 ou 443</td>
    <td>Bloquée</td>
    <td></td>
  </tr>
  <tr>
    <td><b>Non http ou non https</b></td>
    <td>Si l’adresse IP tombe dans la plage <i>espace d’adresse de passerelle VPN</i> et que le client se connecte à la variable env <code>AEM_PROXY_HOST</code> à l’aide d’un <code>portOrig</code> déclaré dans le paramètre de l’API <code>portForwards</code></td>
    <td>Valeur nulle ou non nulle</td>
    <td>Par le VPN</td>
    <td><code>10.0.0.1:3306</code>Il peut également s’agir d’un nom d’hôte.</td>
  </tr>
  <tr>
    <td></td>
    <td>Si l’adresse IP ne tombe pas dans la plage <i>Espace d’adresse de passerelle VPN</i> et que le client se connecte à la variable env <code>AEM_PROXY_HOST</code> à l’aide d’un <code>portOrig</code> déclaré dans le paramètre de l’API <code>portForwards</code></td>
    <td>Valeur nulle ou non nulle</td>
    <td>Via l’adresse IP sortante dédiée</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Autre chose</td>
    <td>Valeur nulle ou non nulle</td>
    <td>Bloquée</td>
    <td></td>
  </tr>
</tbody>
</table>

### Domaines utiles à la configuration{#vpn-useful-domains-for-configuration}

Le diagramme ci-dessous fournit une représentation visuelle d’un ensemble de domaines et d’adresses IP associées utiles à la configuration et au développement. Le tableau ci-dessous décrit ces domaines et adresses IP.

![Configuration de domaine VPN](/help/security/assets/AdvancedNetworking.jpg)

<table>
<thead>
  <tr>
    <th>Modèle de domaine</th>
    <th>Sortie (à partir d’AEM) signifie</th>
    <th>Entrée (pour AEM) signifie</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><code>p{PROGRAM_ID}.external.adobeaemcloud.com</code></td>
    <td>Adresse IP sortante dédiée pour le trafic se dirigeant vers Internet plutôt que par le biais de réseaux privés </td>
    <td>Les connexions du VPN s’afficheraient sur le réseau de diffusion de contenu comme provenant de cette adresse IP. Pour autoriser uniquement les connexions du VPN à accéder à AEM, configurez Cloud Manager afin d’autoriser uniquement cette adresse IP et de bloquer tout le reste. Pour plus d’informations, voir la section "Restreindre l’entrée aux connexions VPN" .</td>
  </tr>
  <tr>
    <td><code>p{PROGRAM_ID}-gateway.external.adobeaemcloud.com</code></td>
    <td>N/A</td>
    <td>L’adresse IP de la passerelle VPN côté AEM. L’équipe d’ingénierie réseau d’un client peut l’utiliser pour autoriser uniquement les connexions VPN à sa passerelle VPN à partir d’une adresse IP spécifique. </td>
  </tr>
  <tr>
    <td><code>p{PROGRAM_ID}.inner.adobeaemcloud.net</code></td>
    <td>L’adresse IP du trafic provenant du côté AEM du VPN au côté client. Cela peut être placé sur la liste autorisée dans la configuration du client pour s’assurer que les connexions ne peuvent être établies qu’à partir d’AEM.</td>
    <td>Si le client souhaite n’autoriser que l’accès VPN à AEM, il doit configurer les entrées DNS CNAME pour mapper <code>author-p{PROGRAM_ID}-e{ENVIRONMENT_ID}.adobeaemcloud.com</code> et/ou <code>publish-p{PROGRAM_ID}-e{ENVIRONMENT_ID}.adobeaemcloud.com</code> à cet accès.</td>
  </tr>
</tbody>
</table>

### Restreindre VPN aux connexions entrantes {#restrict-vpn-to-ingress-connections}

Si vous souhaitez n’autoriser que l’accès VPN à AEM, les listes autorisées d’environnement peuvent être configurées dans Cloud Manager afin que seule l’adresse IP définie par `p{PROGRAM_ID}.external.adobeaemcloud.com` soit autorisée à parler à l’environnement. Vous pouvez le faire de la même manière que toute autre liste autorisée basée sur les adresses IP dans Cloud Manager.

Si les règles doivent être basées sur un chemin d’accès, utilisez des directives http standard au niveau du Dispatcher pour refuser ou autoriser certaines adresses IP. Ils doivent s’assurer que les chemins souhaités ne peuvent pas être mis en cache sur le réseau de diffusion de contenu, de sorte que la demande puisse toujours être mise en origine.

**Exemple de configuration Httpd**

```
Order deny,allow
Deny from all
Allow from 192.168.0.1
Header always set Cache-Control private
```

## Transition Entre Les Types De Mise En Réseau Avancés {#transitioning-between-advanced-networking-types}

Comme le paramètre `kind` ne peut pas être modifié, contactez le service clientèle pour obtenir de l’aide, en décrivant ce qui a déjà été créé et la raison de la modification.