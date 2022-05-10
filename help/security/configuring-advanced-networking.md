---
title: Configuration de la mise en réseau avancée pour AEM as a Cloud Service
description: Découvrez comment configurer des fonctionnalités de mise en réseau avancées telles qu’un VPN ou une adresse IP de sortie flexible ou dédiée pour AEM as a Cloud Service
exl-id: 968cb7be-4ed5-47e5-8586-440710e4aaa9
source-git-commit: d5d17c554cc0877ebe89710b3ea512355fec2a84
workflow-type: tm+mt
source-wordcount: '2977'
ht-degree: 98%

---

# Configuration de la mise en réseau avancée pour AEM as a Cloud Service {#configuring-advanced-networking}

Cet article vise à vous présenter les différentes fonctionnalités de mise en réseau avancées d’AEM as a Cloud Service, y compris la mise en œuvre en libre-service de VPN, de ports non standard et d’adresses IP de sortie dédiées.

>[!INFO]
>
>Vous trouverez également à cet [emplacement](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/advanced-networking.html?lang=fr) une série d’articles conçus pour vous guider dans les différentes options avancées de mise en réseau.

## Présentation {#overview}

AEM as a Cloud Service propose plusieurs types de fonctionnalités de mise en réseau avancées, qui peuvent être configurées par les clients à l’aide des API de Cloud Manager. Celles-ci comprennent les éléments suivants :

* Une [sortie de port flexible](#flexible-port-egress) : configurez AEM as a Cloud Service pour autoriser le trafic sortant des ports non standard
* Une [adresse IP sortante dédiée](#dedicated-egress-IP-address) : configurez le trafic sortant d’AEM as a Cloud Service pour qu’il provienne d’une adresse IP unique
* Un [réseau privé virtuel (VPN)](#vpn) : sécurisez le trafic entre l’infrastructure d’un client et AEM as a Cloud Service, pour les clients qui disposent d’une technologie VPN

Cet article décrit en détail chacune de ces options, y compris leur configuration. La stratégie de configuration générale invoque le point d’entrée de l’API `/networkInfrastructures` au niveau du programme pour déclarer le type souhaité de mise en réseau avancée, puis fait appel au point d’entrée `/advancedNetworking` pour chaque environnement afin d’activer l’infrastructure et de configurer des paramètres spécifiques à l’environnement. Pour chaque syntaxe formelle, ainsi que les exemples de requêtes et de réponses, reportez-vous aux points d’entrée appropriés dans la documentation de l’API Cloud Manager.

Un programme peut fournir une variation réseau avancée unique. Lorsque vous hésitez entre une adresse IP de sortie de port flexible et de sortie dédiée, il est recommandé de choisir une sortie de port flexible si aucune adresse IP spécifique n’est requise, car Adobe peut optimiser les performances du trafic de sortie de port flexible.

>[!INFO]
>
>La mise en réseau avancée n’est pas disponible pour le programme Sandbox.
>En outre, les environnements doivent être mis à niveau vers AEM version 5958 ou supérieure.

>[!NOTE]
>
>Les clients déjà configurés avec la technologie de sortie dédiée héritée qui doivent configurer l’une de ces options ne doivent pas le faire, sans quoi la connectivité du site peut être affectée. Pour obtenir de l’aide, contactez l’assistance Adobe.

## Sortie de port flexible {#flexible-port-egress}

Cette fonctionnalité de mise en réseau avancée vous permet de configurer AEM as a Cloud Service pour récupérer le trafic par des ports autres que HTTP (port 80) et HTTPS (port 443), qui sont ouverts par défaut.

### Considérations {#flexible-port-egress-considerations}

Une sortie de port flexible est recommandée si vous n’avez pas besoin de VPN et n’avez pas besoin d’une adresse IP de sortie dédiée, car le trafic qui ne dépend pas d’une sortie dédiée peut atteindre un débit supérieur.

### Configuration {#configuring-flexible-port-egress-provision}

Une fois par programme, le point d’entrée `/program/<programId>/networkInfrastructures` POST est invoqué, simplement en transmettant la valeur du `flexiblePortEgress` pour le paramètre de `kind` et de région. Le point d’entrée répond avec le `network_id`, ainsi que d’autres informations, y compris le statut. L’ensemble complet des paramètres et la syntaxe exacte doivent être référencés dans la documentation API.

Une fois l’appel lancé, l’approvisionnement de l’infrastructure réseau prend généralement environ 15 minutes. Un appel au [point d’entrée GET de l’infrastructure réseau de Cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getNetworkInfrastructure) affiche l’état « ready ».

Si la configuration de sortie de port flexible à l’échelle du programme est prête, le point d’entrée `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` doit être invoqué pour chaque environnement afin d’activer la mise en réseau au niveau de l’environnement et de déclarer éventuellement toute règle de transfert de port. Les paramètres sont configurables par environnement afin d’offrir une certaine flexibilité.

Les règles de transfert de port doivent être déclarées pour tout port autre que le port 80/443 en spécifiant l’ensemble des hôtes de destination (noms ou adresses IP, et avec les ports). Pour chaque hôte de destination, les clients doivent mapper le port de destination prévu à un port entre 30 000 et 30 999.

L’API doit répondre en quelques secondes seulement et indiquer un statut de mise à jour et, après environ 10 minutes, le point d’entrée `GET` indique que la mise en réseau avancée est activée.

### Mises à jour {#updating-flexible-port-egress-provision}

La configuration au niveau du programme peut être mise à jour en invoquant la méthode `PUT /api/program/<program_id>/network/<network_id>` et prendront effet dans quelques minutes.

>[!NOTE]
>
> Le paramètre « kind » (`flexiblePortEgress`, `dedicatedEgressIP` ou `VPN`) ne peut pas être modifié. Contactez le service clientèle pour obtenir de l’aide, en décrivant ce qui a déjà été créé et la raison du changement.

Les règles de transfert de port par environnement peuvent être mises à jour en invoquant à nouveau le point d’entrée `PUT /program/{programId}/environment/{environmentId}/advancedNetworking`, en veillant à inclure l’ensemble complet des paramètres de configuration, plutôt qu’un sous-ensemble.

### Suppression ou désactivation d’une sortie de port flexible {#deleting-disabling-flexible-port-egress-provision}

À **delete** appel de l’infrastructure réseau d’un programme `DELETE /program/{program ID}/ networkinfrastructure/{networkinfrastructureID}`.

>[!NOTE]
>
> La suppression ne supprime pas l’infrastructure si des environnements l’utilisent.

Pour **désactiver** une sortie de port flexible à partir d’un environnement en particulier, appelez `DELETE [/program/{programId}/environment/{environmentId}/advancedNetworking]()`.

Pour plus d’informations sur les API, voir [Documentation de l’API Cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/disableEnvironmentAdvancedNetworkingConfiguration).

### Routage du trafic {#flexible-port-egress-traffic-routing}

Pour le trafic http ou https se rendant dans des ports autres que 80 ou 443, un proxy doit être configuré à l’aide des variables d’environnement hôte et port suivantes :

* pour HTTP : `AEM_PROXY_HOST` / `AEM_HTTP_PROXY_PORT ` (valeur par défaut `proxy.tunnel:3128` dans les versions d’AEM &lt; 6094)
* pour HTTPS : `AEM_PROXY_HOST` / `AEM_HTTPS_PROXY_PORT ` (valeur par défaut `proxy.tunnel:3128` dans les versions d’AEM &lt; 6094)

Par exemple, voici un exemple de code pour envoyer une requête à `www.example.com:8443` :

```java
String url = "www.example.com:8443"
String proxyHost = System.getenv().getOrDefault("AEM_PROXY_HOST", "proxy.tunnel");
int proxyPort = Integer.parseInt(System.getenv().getOrDefault("AEM_HTTPS_PROXY_PORT", "3128"));
HttpClient client = HttpClient.newBuilder()
      .proxy(ProxySelector.of(new InetSocketAddress(proxyHost, proxyPort)))
      .build();
 
HttpRequest request = HttpRequest.newBuilder().uri(URI.create(url)).build();
HttpResponse<String> response = client.send(request, BodyHandlers.ofString());
```

Si vous utilisez des bibliothèques réseau Java non standard, configurez des proxys à l’aide des propriétés ci-dessus, pour tout le trafic.

Le trafic non http/s pointant vers des destinations via des ports déclarés dans le paramètre `portForwards` doit référencer une propriété appelée `AEM_PROXY_HOST`, ainsi que le port mappé. Par exemple :

```java
DriverManager.getConnection("jdbc:mysql://" + System.getenv("AEM_PROXY_HOST") + ":53306/test");
```

Le tableau ci-dessous décrit le routage du trafic :

<table>
<thead>
  <tr>
    <th>Trafic</th>
    <th>Condition de destination</th>
    <th>Port</th>
    <th>Connexion</th>
    <th>Exemple de destination externe</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><b>Protocole http ou https</b></td>
    <td>Trafic http/s standard</td>
    <td>80 ou 443</td>
    <td>Autorisée</td>
    <td></td>
  </tr> 
  <tr>
    <td></td>
    <td>Trafic non standard (sur d’autres ports en dehors de 80 ou 443) via un proxy http configuré à l’aide de la variable d’environnement et du numéro de port du proxy suivant. Ne déclarez pas le port de destination dans le paramètre portForwards de l’appel API Cloud Manager :<br><ul>
     <li>AEM_PROXY_HOST (par défaut « proxy.tunnel » dans les versions d’AEM &lt; 6094)</li>
     <li>AEM_HTTPS_PROXY_PORT (port par défaut 3128 dans les versions d’AEM &lt; 6094)</li>
    </ul>
    <td>Ports autres que 80 ou 443</td>
    <td>Autorisée</td>
    <td>example.com:8443</td>
  </tr>
  <tr>
    <td></td>
    <td>Trafic non standard (sur d’autres ports autres que 80 ou 443) n’utilisant pas de proxy http</td>
    <td>Ports autres que 80 ou 443</td>
    <td>Bloquée</td>
    <td></td>
  </tr>
  <tr>
    <td><b>Non http ou non https</b></td>
    <td>Le client se connecte à la variable d’environnement <code>AEM_PROXY_HOST</code> à l’aide d’un <code>portOrig</code> déclaré dans le paramètre <code>portForwards</code> de l’API.</td>
    <td>N’importe lequel</td>
    <td>Autorisée</td>
    <td><code>mysql.example.com:3306</code></td>
  </tr>
  <tr>
    <td></td>
    <td>Tout le reste</td>
    <td>N’importe lequel</td>
    <td>Bloquée</td>
    <td><code>db.example.com:5555</code></td>
  </tr>
</tbody>
</table>

**Configuration Apache/Dispatcher**

La directive `mod_proxy` Apache au niveau du Dispatcher d’AEM Cloud Service peut être configurée à l’aide des propriétés décrites ci-dessus.

```
ProxyRemote "http://example.com:8080" "http://${AEM_PROXY_HOST}:3128"
ProxyPass "/somepath" "http://example.com:8080"
ProxyPassReverse "/somepath" "http://example.com:8080"
```

```
SSLProxyEngine on //needed for https backends
 
ProxyRemote "https://example.com:8443" "http://${AEM_PROXY_HOST}:3128"
ProxyPass "/somepath" "https://example.com:8443"
ProxyPassReverse "/somepath" "https://example.com:8443"
```

## Adresse IP Egress dédiée {#dedicated-egress-IP-address}

>[!NOTE]
>
>Si vous avez reçu une adresse IP de sortie dédiée avant la publication de la version de septembre 2021 (10/6/21), reportez-vous à la section [Clients avec une adresse sortante dédiée héritée](#legacy-dedicated-egress-address-customers).

### Avantages {#benefits}

Cette adresse IP dédiée peut améliorer la sécurité lors de l’intégration avec les fournisseurs SaaS (comme un fournisseur de solutions de gestion de la relation client) ou d’autres intégrations en dehors d’AEM as a Cloud Service qui offrent une liste d’adresses IP autorisées. L’ajout de l’adresse IP dédiée à la liste autorisée garantit que seul le trafic provenant de l’instance AEM as a Cloud Service du client est autorisé à circuler dans le service externe. Cela s’ajoute au trafic provenant de toute autre adresse IP autorisée.

Si la fonction d’adresse IP dédiée n’est pas activée, le trafic provenant d’AEM as a Cloud Service passe par un jeu d’adresses IP partagées avec d’autres clients.

### Configuration {#configuring-dedicated-egress-provision}

>[!INFO]
>
>La fonctionnalité de transfert Splunk n’est pas possible à partir d’une adresse IP de sortie dédiée.

La configuration de l’adresse IP de sortie dédiée est identique à celle d’une [sortie de port flexible](#configuring-flexible-port-egress-provision).

La principale différence est que le trafic sortira toujours d’une adresse IP dédiée et unique. Pour trouver cette adresse IP, utilisez un résolveur DNS pour identifier l’adresse IP associée à `p{PROGRAM_ID}.external.adobeaemcloud.com`. L’adresse IP n’est pas censée changer mais si elle le doit malgré tout, vous recevrez une notification avancée.

Outre les règles de routage prises en charge par la sortie de port flexible dans le point d’entrée `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking`, l’adresse IP sortante dédiée prend en charge un paramètre `nonProxyHosts`. Cela vous permet de déclarer un ensemble d’hôtes qui doivent passer par une plage d’adresses IP partagées plutôt que par l’adresse IP dédiée, ce qui peut s’avérer utile puisque le trafic passant par les adresses IP partagées peut être encore optimisé. Les URL `nonProxyHost` peuvent être calquées sur `example.com` ou `*.example.com`, le caractère générique n’étant pris en charge qu’au début du domaine.

Lorsque vous hésitez entre une adresse IP de sortie de port flexible et de sortie dédiée, il est recommandé de choisir une sortie de port flexible si aucune adresse IP spécifique n’est requise, car Adobe peut optimiser les performances du trafic de sortie de port flexible.

### Routage du trafic {#dedcated-egress-ip-traffic-routing}

Le trafic http ou https pointant vers des destinations via les ports 80 ou 443 passe par un proxy préconfiguré, en supposant que la bibliothèque de réseau Java standard soit utilisée. Pour le trafic http ou https passant par d’autres ports, un proxy doit être configuré à l’aide des propriétés suivantes.

```
AEM_HTTP_PROXY_HOST / AEM_HTTPS_PROXY_HOST
AEM_HTTP_PROXY_PORT / AEM_HTTPS_PROXY_PORT
```

Par exemple, voici un exemple de code pour envoyer une requête à `www.example.com:8443` :

```java
String url = "www.example.com:8443"
String proxyHost = System.getenv("AEM_HTTPS_PROXY_HOST");
int proxyPort = Integer.parseInt(System.getenv("AEM_HTTPS_PROXY_PORT"));

HttpClient client = HttpClient.newBuilder()
      .proxy(ProxySelector.of(new InetSocketAddress(proxyHost, proxyPort)))
      .build();
 
HttpRequest request = HttpRequest.newBuilder().uri(URI.create(url)).build();
HttpResponse<String> response = client.send(request, BodyHandlers.ofString());
```

Si vous utilisez des bibliothèques réseau Java non standard, configurez des proxys à l’aide des propriétés ci-dessus, pour tout le trafic.

Le trafic non http/s pointant vers des destinations via des ports déclarés dans le paramètre `portForwards` doit référencer une propriété appelée `AEM_PROXY_HOST`, ainsi que le port mappé. Par exemple :

```java
DriverManager.getConnection("jdbc:mysql://" + System.getenv("AEM_PROXY_HOST") + ":53306/test");
```

<table>
<thead>
  <tr>
    <th>Trafic</th>
    <th>Condition de destination</th>
    <th>Port</th>
    <th>Connexion</th>
    <th>Exemple de destination externe</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><b>Protocole http ou https</b></td>
    <td>Trafic vers Azure ou vers les services Adobe</td>
    <td>N’importe lequel</td>
    <td>Via les adresses IP partagées du cluster (et non l’adresse IP dédiée)</td>
    <td>adobe.io<br>api.windows.net</td>
  </tr>
  <tr>
    <td></td>
    <td>Hôte correspondant au paramètre <code>nonProxyHosts</code></td>
    <td>80 ou 443</td>
    <td>Via les adresses IP partagées du cluster</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Hôte correspondant au paramètre <code>nonProxyHosts</code></td>
    <td>Ports autres que 80 ou 443</td>
    <td>Bloquée</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Via la configuration du proxy http, configurée par défaut pour le trafic http/s à l’aide de la bibliothèque cliente HTTP Java standard</td>
    <td>N’importe lequel</td>
    <td>Via l’adresse IP sortante dédiée</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Ignore la configuration du proxy http (par exemple, si elle est explicitement supprimée de la bibliothèque cliente HTTP Java standard ou si une bibliothèque Java qui ignore la configuration du proxy standard est utilisée)</td>
    <td>80 ou 443</td>
    <td>Via les adresses IP partagées du cluster</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Ignore la configuration du proxy http (par exemple, si elle est explicitement supprimée de la bibliothèque cliente HTTP Java standard ou si une bibliothèque Java qui ignore la configuration du proxy standard est utilisée)</td>
    <td>Ports autres que 80 ou 443</td>
    <td>Bloquée</td>
    <td></td>
  </tr>
  <tr>
    <td><b>Non http ou non https</b></td>
    <td>Le client se connecte à la variable d’environnement <code>AEM_PROXY_HOST</code> à l’aide du <code>portOrig</code> déclaré dans le paramètre d’API <code>portForwards</code></td>
    <td>N’importe lequel</td>
    <td>Via l’adresse IP sortante dédiée</td>
    <td><code>mysql.example.com:3306</code></td>
  </tr>
  <tr>
    <td></td>
    <td>Autre</td>
    <td></td>
    <td>Bloquée</td>
    <td></td>
  </tr>
</tbody>
</table>

## Utilisation de la fonctionnalité {#feature-usage}

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
[`HttpClientBuilder.useSystemProperties()`](https://hc.apache.org/httpcomponents-client-4.5.x/current/httpclient/apidocs/org/apache/http/impl/client/HttpClientBuilder.html) ou l’utilisation de 
[`HttpClients.createSystem()`](https://hc.apache.org/httpcomponents-client-4.5.x/current/httpclient/apidocs/org/apache/http/impl/client/HttpClients.html#createSystem()) :

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

### Considérations relatives au débogage {#debugging-considerations}

Afin de vérifier que le trafic est effectivement sortant sur l’adresse IP dédiée attendue, vérifiez les journaux dans le service de destination, si disponible. Dans le cas contraire, il peut s’avérer utile d’appeler un service de débogage tel que [https://ifconfig.me/IP](https://ifconfig.me/IP), qui renverra l’adresse IP d’appel.

## Clients avec une adresse sortante dédiée héritée {#legacy-dedicated-egress-address-customers}

Si vous avez reçu l’attribution d’une adresse IP de sortie dédiée avant la version 2021.09.30, votre fonction d’adresse IP de sortie dédiée ne prend en charge que les ports HTTP et HTTPS.
Inclut le HTTP/1.1 et HTTP/2 lorsqu’ils sont chiffrés.

## Réseau privé virtuel (VPN) {#vpn}

Un VPN permet de se connecter à une infrastructure ou à un centre de données on-premise de l’auteur, de la publication ou de l’aperçu. Par exemple, il permet d’accéder à une base de données.

Il permet également de se connecter aux fournisseurs SaaS tels qu’un fournisseur de gestion de la relation client qui prend en charge les VPN ou de se connecter à l’auteur, la prévisualisation ou la publication AEM as a Cloud Service à partir d’un réseau d’entreprise.

La plupart des périphériques VPN dotés de la technologie IPSec sont pris en charge. Consultez la liste des périphériques sur [cette page](https://docs.microsoft.com/fr-fr/azure/vpn-gateway/vpn-gateway-about-vpn-devices#devicetable), en fonction des informations dans la colonne **Instructions de configuration basées sur les routes**. Configurez le périphérique comme décrit dans le tableau.

### Remarques générales {#general-vpn-considerations}

* La prise en charge est limitée à une VPN unique.
* La fonctionnalité de transfert Splunk n’est pas possible via une connexion VPN.

### Création {#vpn-creation}

Une fois par programme, le point d’entrée `/program/<programId>/networkInfrastructures` POST est invoqué, transmettant un payload d’informations de configuration, notamment : la valeur de « vpn » pour le paramètre `kind`, la région, l’espace d’adresse (liste des CIDR ; notez que cela ne peut pas être modifié plus tard), les résolveurs DNS (pour résoudre les noms dans le réseau du client) et les informations de connexion VPN telles que la configuration de la passerelle, la clé VPN partagée et la politique de sécurité IP. Le point d’entrée répond avec le `network_id`, ainsi que d’autres informations, y compris le statut. L’ensemble complet des paramètres et la syntaxe exacte doivent être référencés dans la [documentation de l’API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/createNetworkInfrastructure).

Une fois l’appel lancé, l’approvisionnement de l’infrastructure réseau prend généralement entre 45 et 60 minutes. La méthode GET de l’API peut être appelée pour renvoyer le statut actuel, qui finira par passer de `creating` à `ready`. Consultez la documentation de l’API pour connaître tous les statuts.

Si la configuration de sortie de VPN à l’échelle du programme est prête, le point d’entrée `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` doit être invoqué pour chaque environnement pour activer la mise en réseau au niveau de l’environnement et pour déclarer chaque règle de transfert de port. Les paramètres sont configurables par environnement afin d’offrir une certaine flexibilité.

Pour plus d’informations, consultez la [documentation de l’API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/enableEnvironmentAdvancedNetworkingConfiguration).

Les règles de transfert de port doivent être déclarées pour tout trafic TCP non http/s qui doit être acheminé via le VPN en spécifiant le jeu d’hôtes de destination (noms ou adresses IP, et avec les ports). Pour chaque hôte de destination, les clients doivent mapper le port de destination prévu à un port compris entre 30 000 et 30 999, et les valeurs doivent être uniques dans tous les environnements du programme. Les clients peuvent également répertorier un ensemble d’URL dans la variable `nonProxyHosts` qui déclare l’URL pour laquelle le trafic doit contourner le routage VPN et passer par une plage IP partagée. Ces URLS peuvent être calquées sur `example.com` ou sur `*.example.com`, le caractère générique n’étant pris en charge qu’au début du domaine.

L’API doit répondre en quelques secondes seulement et indiquer un statut `updating` et, au bout d’environ 10 minutes, un appel au point d’entrée de l’environnement de Cloud Manager affiche le statut `ready`, indiquant que la mise à jour de l’environnement a été appliquée.

Notez que même en l’absence de règles de routage du trafic de l’environnement (hôtes ou contournements), `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` doit toujours être appelé mais avec un payload vide.

### Mise à jour du VPN {#updating-the-vpn}

La configuration VPN au niveau du programme peut être mise à jour en invoquant le point d’entrée `PUT /api/program/<program_id>/network/<network_id>`.

Notez que l’espace d’adresse ne peut pas être modifié après la configuration VPN initiale. En cas de besoin, contactez le service clientèle. En outre, le paramètre `kind` (`flexiblePortEgress`, `dedicatedEgressIP` ou `VPN`) ne peut pas être modifié. Contactez le service clientèle pour obtenir de l’aide, en décrivant ce qui a déjà été créé et la raison du changement.

Les règles de routage par environnement peuvent être mises à jour en invoquant à nouveau le point d’entrée `PUT /program/{programId}/environment/{environmentId}/advancedNetworking`, en veillant à inclure l’ensemble complet des paramètres de configuration, plutôt qu’un sous-ensemble. Les mises à jour d’environnement prennent généralement 5 à 10 minutes avant d’être appliquées.

### Suppression ou désactivation du VPN {#deleting-or-disabling-the-vpn}

Pour supprimer l’infrastructure réseau, soumettez un ticket de service clientèle, décrivant ce qui a été créé et la raison de la suppression.

Pour désactiver un VPN pour un environnement en particulier, appelez `DELETE /program/{programId}/environment/{environmentId}/advancedNetworking`. Pour plus d’informations, consultez la [documentation de l’API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/disableEnvironmentAdvancedNetworkingConfiguration).

### Routage du trafic {#vpn-traffic-routing}

Le tableau ci-dessous décrit le routage du trafic.

<table>
<thead>
  <tr>
    <th>Trafic</th>
    <th>Condition de destination</th>
    <th>Port</th>
    <th>Connexion</th>
    <th>Exemple de destination externe</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><b>Protocole http ou https</b></td>
    <td>Trafic vers Azure ou vers les services Adobe</td>
    <td>N’importe lequel</td>
    <td>Via les adresses IP partagées du cluster (et non l’adresse IP dédiée)</td>
    <td>adobe.io<br>api.windows.net</td>
  </tr>
  <tr>
    <td></td>
    <td>Hôte correspondant au paramètre <code>nonProxyHosts</code></td>
    <td>80 ou 443</td>
    <td>Via les adresses IP partagées du cluster</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Hôte correspondant au paramètre <code>nonProxyHosts</code></td>
    <td>Ports autres que 80 ou 443</td>
    <td>Bloquée</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Si l’adresse IP est comprise dans la plage d’espace d’<i>adresse de la passerelle VPN</i>, et par la configuration du proxy http (configurée par défaut pour le trafic http/s à l’aide de la bibliothèque cliente HTTP Java standard)</td>
    <td>N’importe lequel</td>
    <td>Par le VPN</td>
    <td><code>10.0.0.1:443</code>Il peut également s’agir d’un nom d’hôte.</td>
  </tr>
  <tr>
    <td></td>
    <td>Si l’adresse IP n’est pas comprise dans la plage d’<i>espace d’adresse de la passerelle VPN</i>, et par la configuration du proxy http (configurée par défaut pour le trafic http/s à l’aide de la bibliothèque cliente HTTP Java standard)</td>
    <td>N’importe lequel</td>
    <td>Via l’adresse IP sortante dédiée</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Ignore la configuration du proxy http (par exemple, si elle est explicitement supprimée de la bibliothèque cliente HTTP Java standard ou si vous utilisez une bibliothèque Java qui ignore la configuration du proxy standard)
</td>
    <td>80 ou 443</td>
    <td>Via les adresses IP partagées du cluster</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Ignore la configuration du proxy http (par exemple, si elle est explicitement supprimée de la bibliothèque cliente HTTP Java standard ou si vous utilisez une bibliothèque Java qui ignore la configuration du proxy standard)</td>
    <td>Ports autres que 80 ou 443</td>
    <td>Bloquée</td>
    <td></td>
  </tr>
  <tr>
    <td><b>Non http ou non https</b></td>
    <td>Si l’adresse IP est comprise dans la plage d’<i>espace d’adresse de la passerelle VPN</i> et que le client se connecte à la variable d’environnement <code>AEM_PROXY_HOST</code> à l’aide d’un <code>portOrig</code> déclaré dans le paramètre d’API <code>portForwards</code></td>
    <td>N’importe lequel</td>
    <td>Par le VPN</td>
    <td><code>10.0.0.1:3306</code>Il peut également s’agir d’un nom d’hôte.</td>
  </tr>
  <tr>
    <td></td>
    <td>Si l’adresse IP n’est pas comprise dans la plage d’<i>espace d’adresse de la passerelle VPN</i> et que le client se connecte à la variable d’environnement <code>AEM_PROXY_HOST</code> à l’aide d’un <code>portOrig</code> déclaré dans le paramètre d’API <code>portForwards</code></td>
    <td>N’importe lequel</td>
    <td>Via l’adresse IP sortante dédiée</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Autre</td>
    <td>N’importe lequel</td>
    <td>Bloquée</td>
    <td></td>
  </tr>
</tbody>
</table>

### Domaines utiles à la configuration{#vpn-useful-domains-for-configuration}

Le diagramme ci-dessous offre une représentation visuelle d’un ensemble de domaines et d’adresses IP associées utiles à la configuration et au développement. Le tableau sous le diagramme décrit ces domaines et adresses IP.

![Configuration de domaine VPN](/help/security/assets/AdvancedNetworking.jpg)

<table>
<thead>
  <tr>
    <th>Modèle de domaine</th>
    <th>Destination de la sortie (à partir d’AEM)</th>
    <th>Destination de l’entrée (vers AEM)</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><code>p{PROGRAM_ID}.external.adobeaemcloud.com</code></td>
    <td>Adresse IP sortante dédiée au trafic envoyé vers Internet plutôt que par des réseaux privés </td>
    <td>Les connexions à partir du VPN s’afficheraient sur le réseau de diffusion de contenu comme provenant de cette adresse IP. Pour autoriser uniquement les connexions venant du VPN à accéder à AEM, configurez Cloud Manager afin d’autoriser uniquement cette adresse IP et de bloquer tout le reste. Pour plus d’informations, consultez la section « Restreindre le VPN aux connexions entrantes ».</td>
  </tr>
  <tr>
    <td><code>p{PROGRAM_ID}-gateway.external.adobeaemcloud.com</code></td>
    <td>S/O</td>
    <td>L’adresse IP de la passerelle VPN côté AEM. L’équipe d’ingénierie réseau d’un client peut l’utiliser pour autoriser uniquement les connexions VPN à sa passerelle VPN à partir d’une adresse IP spécifique. </td>
  </tr>
  <tr>
    <td><code>p{PROGRAM_ID}.inner.adobeaemcloud.net</code></td>
    <td>L’adresse IP du trafic provenant du côté AEM du VPN au côté client. Elle peut être placée dans la liste autorisée de la configuration du client pour s’assurer que les connexions ne peuvent être établies qu’à partir d’AEM.</td>
    <td>Si le client souhaite autoriser uniquement l’accès VPN à AEM, il doit configurer les entrées DNS CNAME pour mapper <code>author-p{PROGRAM_ID}-e{ENVIRONMENT_ID}.adobeaemcloud.com</code> et/ou <code>publish-p{PROGRAM_ID}-e{ENVIRONMENT_ID}.adobeaemcloud.com</code>.</td>
  </tr>
</tbody>
</table>

### Restreindre le VPN aux connexions entrantes {#restrict-vpn-to-ingress-connections}

Si vous souhaitez n’autoriser que l’accès VPN à AEM, les listes autorisées d’environnement peuvent être configurées dans Cloud Manager, de sorte que seule l’adresse IP définie par `p{PROGRAM_ID}.external.adobeaemcloud.com` est autorisée à s’adresser à l’environnement. Vous pouvez le faire de la même manière que pour toute autre liste autorisée basée sur les adresses IP dans Cloud Manager.

Si les règles doivent être basées sur un chemin d’accès, utilisez des directives http standard au niveau du Dispatcher pour refuser ou autoriser certaines adresses IP. Elles doivent s’assurer que les chemins souhaités ne peuvent pas être mis en cache sur le réseau de diffusion de contenu, de sorte que la demande puisse toujours être mise en origine.

**Exemple de configuration httpd**

```
Order deny,allow
Deny from all
Allow from 192.168.0.1
Header always set Cache-Control private
```

## Transition entre les types de mise en réseau avancée {#transitioning-between-advanced-networking-types}

Puisque le paramètre `kind` ne peut pas être modifié, contactez le service clientèle pour obtenir de l’aide, en décrivant ce qui a déjà été créé et la raison de la modification.
