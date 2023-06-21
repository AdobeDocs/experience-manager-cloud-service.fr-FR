---
title: Configuration de la mise en réseau avancée pour AEM as a Cloud Service
description: Découvrez comment configurer des fonctionnalités de mise en réseau avancées telles qu’un VPN ou une adresse IP de sortie flexible ou dédiée pour AEM as a Cloud Service
exl-id: 968cb7be-4ed5-47e5-8586-440710e4aaa9
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '3579'
ht-degree: 82%

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

Une fois par programme, le point d’entrée `/program/<programId>/networkInfrastructures` POST est invoqué, simplement en transmettant la valeur du `flexiblePortEgress` pour le paramètre de `kind` et de région. Le point d’entrée répond avec le `network_id`, ainsi que d’autres informations, y compris le statut. Le jeu complet de paramètres et la syntaxe exacte, ainsi que des informations importantes comme les paramètres qui ne peuvent pas être modifiés plus tard, [peuvent être référencés dans la documentation de l’API.](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/createNetworkInfrastructure)

Une fois l’appel lancé, l’approvisionnement de l’infrastructure réseau prend généralement environ 15 minutes. Un appel au [point d’entrée GET de l’infrastructure réseau de Cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getNetworkInfrastructure) affiche l’état « ready ».

Si la configuration de sortie de port flexible à l’échelle du programme est prête, le point d’entrée `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` doit être invoqué pour chaque environnement afin d’activer la mise en réseau au niveau de l’environnement et de déclarer éventuellement toute règle de transfert de port. Les paramètres sont configurables par environnement pour offrir une certaine flexibilité.

Les règles de transfert de port doivent être déclarées pour tout port de destination autre que le port 80/443, uniquement si le protocole http ou https n’est pas utilisé,
en spécifiant le jeu d’hôtes de destination (noms ou adresses IP, avec les ports). Pour chaque hôte de destination, les clients doivent mapper le port de destination prévu à un port entre 30 000 et 30 999.

L’API doit répondre en quelques secondes seulement et indiquer un statut de mise à jour et, après environ 10 minutes, le point d’entrée `GET` indique que la mise en réseau avancée est activée.

### Mises à jour {#updating-flexible-port-egress-provision}

La configuration au niveau du programme peut être mise à jour en invoquant la méthode `PUT /api/program/<program_id>/network/<network_id>` et prendront effet dans quelques minutes.

>[!NOTE]
>
> Le paramètre « kind » (`flexiblePortEgress`, `dedicatedEgressIP` ou `VPN`) ne peut pas être modifié. Contactez le service clientèle pour obtenir de l’aide, en décrivant ce qui a déjà été créé et la raison du changement.

Les règles de transfert de port par environnement peuvent être mises à jour en invoquant à nouveau le point d’entrée `PUT /program/{programId}/environment/{environmentId}/advancedNetworking`, en veillant à inclure l’ensemble complet des paramètres de configuration, plutôt qu’un sous-ensemble.

### Désactivation de sortie de port flexible {#disabling-flexible-port-egress-provision}

À **disable** sortie de port flexible à partir d’un environnement particulier, appel `DELETE [/program/{programId}/environment/{environmentId}/advancedNetworking]()`.

Pour plus d’informations sur les API, consultez la [documentation de l’API Cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/disableEnvironmentAdvancedNetworkingConfiguration).

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

La principale différence est que le trafic sortira toujours d’une adresse IP dédiée et unique. Pour trouver cette adresse IP, utilisez un résolveur DNS pour identifier l’adresse IP associée à `p{PROGRAM_ID}.external.adobeaemcloud.com`. L’adresse IP ne doit pas changer, mais si elle doit changer à l’avenir, une notification avancée est fournie.

Outre les règles de routage prises en charge par la sortie de port flexible dans le point d’entrée `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking`, l’adresse IP sortante dédiée prend en charge un paramètre `nonProxyHosts`. Cela vous permet de déclarer un ensemble d’hôtes qui doivent passer par une plage d’adresses IP partagées plutôt que par l’adresse IP dédiée, ce qui peut s’avérer utile puisque le trafic passant par les adresses IP partagées peut être encore optimisé. Les URL `nonProxyHost` peuvent être calquées sur `example.com` ou `*.example.com`, le caractère générique n’étant pris en charge qu’au début du domaine.

Lorsque vous hésitez entre une adresse IP de sortie de port flexible et de sortie dédiée, il est recommandé de choisir une sortie de port flexible si aucune adresse IP spécifique n’est requise, car Adobe peut optimiser les performances du trafic de sortie de port flexible.

### Désactiver l’adresse IP sortante dédiée {#disabling-dedicated-egress-IP-address}

À **disable** Adresse IP sortante dédiée d’un environnement particulier, invoquez `DELETE [/program/{programId}/environment/{environmentId}/advancedNetworking]()`.

Pour plus d’informations sur les API, consultez la [documentation de l’API Cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/disableEnvironmentAdvancedNetworkingConfiguration).

### Routage du trafic {#dedcated-egress-ip-traffic-routing}

Le trafic HTTP ou HTTPS passe par un proxy préconfiguré, à condition qu’il utilise des propriétés système Java standard pour les configurations de proxy.

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

Pour vérifier que le trafic est effectivement sortant sur l’adresse IP dédiée attendue, vérifiez les journaux dans le service de destination, le cas échéant. Dans le cas contraire, il peut s’avérer utile d’appeler un service de débogage tel que [https://ifconfig.me/IP](https://ifconfig.me/IP), qui renverra l’adresse IP d’appel.

## Clients avec une adresse sortante dédiée héritée {#legacy-dedicated-egress-address-customers}

Si vous avez reçu une adresse IP de sortie dédiée avant le 30/09/2021, votre fonction d’adresse IP de sortie dédiée ne prend en charge que les ports HTTP et HTTPS.
Inclut le HTTP/1.1 et HTTP/2 lorsqu’ils sont chiffrés. De plus, un point d’entrée de sortie dédié peut uniquement communiquer avec une cible via HTTP/HTTPS sur les ports 80/443, respectivement.

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

Si la configuration de sortie de VPN à l’échelle du programme est prête, le point d’entrée `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` doit être invoqué pour chaque environnement pour activer la mise en réseau au niveau de l’environnement et pour déclarer chaque règle de transfert de port. Les paramètres sont configurables par environnement pour offrir une certaine flexibilité.

Pour plus d’informations, consultez la [documentation de l’API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/enableEnvironmentAdvancedNetworkingConfiguration).

Les règles de transfert de port doivent être déclarées pour tout trafic TCP non http/s qui doit être acheminé via le VPN en spécifiant le jeu d’hôtes de destination (noms ou adresses IP, et avec les ports). Pour chaque hôte de destination, les clients doivent mapper le port de destination prévu à un port compris entre 30 000 et 30 999, et les valeurs doivent être uniques dans tous les environnements du programme. Les clients peuvent également répertorier un ensemble d’URL dans la variable `nonProxyHosts` qui déclare l’URL pour laquelle le trafic doit contourner le routage VPN et passer par une plage IP partagée. Ces URLS peuvent être calquées sur `example.com` ou sur `*.example.com`, le caractère générique n’étant pris en charge qu’au début du domaine.

L’API doit répondre en quelques secondes seulement et indiquer un statut `updating` et, au bout d’environ 10 minutes, un appel au point d’entrée de l’environnement de Cloud Manager affiche le statut `ready`, indiquant que la mise à jour de l’environnement a été appliquée.

Notez que même en l’absence de règles de routage du trafic de l’environnement (hôtes ou contournements), `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` doit toujours être appelé mais avec un payload vide.

### Mise à jour du VPN {#updating-the-vpn}

La configuration VPN au niveau du programme peut être mise à jour en invoquant le point d’entrée `PUT /api/program/<program_id>/network/<network_id>`.

Notez que l’espace d’adresse ne peut pas être modifié après la configuration VPN initiale. En cas de besoin, contactez le service clientèle. En outre, le paramètre `kind` (`flexiblePortEgress`, `dedicatedEgressIP` ou `VPN`) ne peut pas être modifié. Contactez le service clientèle pour obtenir de l’aide, en décrivant ce qui a déjà été créé et la raison du changement.

Les règles de routage par environnement peuvent être mises à jour en invoquant à nouveau le point d’entrée `PUT /program/{programId}/environment/{environmentId}/advancedNetworking`, en veillant à inclure l’ensemble complet des paramètres de configuration, plutôt qu’un sous-ensemble. Les mises à jour d’environnement prennent généralement 5 à 10 minutes avant d’être appliquées.

### Désactivation du VPN {#disabling-the-vpn}

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
    <td><code>10.0.0.1:443</code><br>Il peut également s’agir d’un nom d’hôte.</td>
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
    <td><code>10.0.0.1:3306</code><br>Il peut également s’agir d’un nom d’hôte.</td>
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
    <td><code>p{PROGRAM_ID}.{REGION}-gateway.external.adobeaemcloud.com</code></td>
    <td>S/O</td>
    <td>L’adresse IP de la passerelle VPN côté AEM. L’équipe d’ingénierie réseau d’un client peut l’utiliser pour autoriser uniquement les connexions VPN à sa passerelle VPN à partir d’une adresse IP spécifique. </td>
  </tr>
  <tr>
    <td><code>p{PROGRAM_ID}.{REGION}.inner.adobeaemcloud.net</code></td>
    <td>L’adresse IP du trafic provenant du côté AEM du VPN au côté client. Elle peut être placée dans la liste autorisée de la configuration du client pour s’assurer que les connexions ne peuvent être établies qu’à partir d’AEM.</td>
    <td>Si le client souhaite autoriser l’accès VPN à AEM, il doit configurer les entrées DNS CNAME pour mapper leur domaine personnalisé <code>author-p{PROGRAM_ID}-e{ENVIRONMENT_ID}.adobeaemcloud.com</code> et <code>publish-p{PROGRAM_ID}-e{ENVIRONMENT_ID}.adobeaemcloud.com</code> à celui-ci.</td>
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

## Suppression de l’infrastructure réseau d’un programme {#deleting-network-infrastructure}

Pour **supprimer** l’infrastructure réseau d’un programme, appelez `DELETE /program/{program ID}/networkinfrastructure/{networkinfrastructureID}`.

>[!NOTE]
>
> La suppression ne supprime l’infrastructure que si les réseaux avancés de tous les environnements sont désactivés.
> 

## Transition entre les types de mise en réseau avancée {#transitioning-between-advanced-networking-types}

Il est possible de migrer entre les types de réseaux avancés en procédant comme suit :

* Désactivez la mise en réseau avancée dans tous les environnements.
* Supprimez l’infrastructure réseau avancée.
* Recréez les infrastructures réseau avancées avec les valeurs correctes.
* Réactivez la mise en réseau avancée au niveau de l’environnement.

>[!WARNING]
>
> Cette procédure entraîne une interruption des services de mise en réseau avancés entre la suppression et la recréation.
> 

Si l’interruption devait entraîner un impact important sur l’activité, contactez le service clientèle pour obtenir de l’aide, en décrivant ce qui a déjà été créé et la raison du changement.

## Configuration de réseau avancée pour d’autres régions de publication {#advanced-networking-configuration-for-additional-publish-regions}

Lorsqu’une région supplémentaire est ajoutée à un environnement qui dispose déjà d’une mise en réseau avancée configurée, le trafic de la région de publication supplémentaire qui correspond aux règles de mise en réseau avancées traverse par défaut la région Principale. Toutefois, si la région Principale n’est plus disponible, le trafic réseau avancé est abandonné si la mise en réseau avancée n’a pas été activée dans la région supplémentaire. Si vous souhaitez optimiser la latence et augmenter la disponibilité en cas de panne de l’une des régions, il est nécessaire d’activer une mise en réseau avancée pour la ou les régions de publication supplémentaires. Les sections suivantes décrivent deux scénarios différents.

>[!NOTE]
>
>Toutes les régions partagent la même [configuration de réseau avancé de l’environnement](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Environment-Advanced-Networking-Configuration), il n’est donc pas possible d’acheminer le trafic vers différentes destinations en fonction de la région d’où provient le trafic.

### Adresses IP Egress dédiées {#additional-publish-regions-dedicated-egress}

#### Mise en réseau avancée déjà activée dans la région Principale {#already-enabled}

Si une configuration réseau avancée est déjà activée dans la région Principale, procédez comme suit :

1. Si vous avez verrouillé votre infrastructure de sorte que l’adresse IP AEM dédiée soit répertoriée, il est recommandé de désactiver temporairement toute règle de refus dans cette infrastructure. Si ce n’est pas le cas, il y a une courte période pendant laquelle les demandes provenant des adresses IP de la nouvelle région sont refusées par votre propre infrastructure. Notez que cela n’est pas nécessaire si vous avez verrouillé votre infrastructure via le nom de domaine complet (FQDN), (`p1234.external.adobeaemcloud.com`, par exemple), car toutes les régions AEM reçoivent un trafic réseau avancé du même nom de domaine complet (FQDN).
1. Créez l’infrastructure réseau à portée de programme pour la région secondaire par le biais d’un appel POST à l’API Cloud Manager Create Network Infrastructure, comme décrit dans la documentation réseau avancée. La seule différence dans la configuration JSON de la payload par rapport à la région Principale est la propriété region .
1. Si votre infrastructure doit être verrouillée par IP pour autoriser AEM trafic, ajoutez les adresses IP qui correspondent `p1234.external.adobeaemcloud.com`. Il devrait y en avoir une par région.

#### Mise en réseau avancée non encore configurée dans une région {#not-yet-configured}

La procédure est essentiellement similaire aux instructions précédentes. Cependant, si l’environnement de production n’a pas encore été activé pour la mise en réseau avancée, vous avez la possibilité de tester la configuration en l’activant d’abord dans un environnement intermédiaire :

1. Créez une infrastructure de réseau pour toutes les régions à l’aide de l’appel du POST à la fonction [API de création d’infrastructure réseau de Cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Network-infrastructure/operation/createNetworkInfrastructure). La seule différence dans la configuration JSON de la payload par rapport à la région Principale est la propriété region.
1. Pour l’environnement d’évaluation, activez et configurez l’environnement mis en réseau avancé en exécutant `PUT api/program/{programId}/environment/{environmentId}/advancedNetworking`. Pour plus d’informations, consultez la documentation de l’API . [here](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Environment-Advanced-Networking-Configuration/operation/enableEnvironmentAdvancedNetworkingConfiguration)
1. Si nécessaire, verrouiller l’infrastructure externe, de préférence par le nom de domaine complet (par exemple `p1234.external.adobeaemcloud.com`). Vous pouvez le faire autrement par adresse IP.
1. Si l’environnement d’évaluation fonctionne comme prévu, activez et configurez la configuration de mise en réseau avancée de l’environnement pour la production.

#### VPN {#vpn-regions}

La procédure est presque identique aux instructions d’adresses IP sortantes dédiées. La seule différence est qu’en plus de la propriété de région configurée différemment de la région Principale, la variable `connections.gateway` peut éventuellement être configuré pour acheminer vers un autre point d’entrée VPN opéré par votre organisation, peut-être géographiquement plus proche de la nouvelle région.
