---
title: Configuration de la mise en réseau avancée pour AEM as a Cloud Service
description: Découvrez comment configurer des fonctionnalités de mise en réseau avancées telles qu’un VPN ou une adresse IP de sortie flexible ou dédiée pour AEM as a Cloud Service
exl-id: 968cb7be-4ed5-47e5-8586-440710e4aaa9
source-git-commit: a284c0139b45e618749866385cdcc81d1ceb61e7
workflow-type: tm+mt
source-wordcount: '5145'
ht-degree: 44%

---


# Configuration de la mise en réseau avancée pour AEM as a Cloud Service {#configuring-advanced-networking}

Cet article présente les différentes fonctionnalités de mise en réseau avancées d’AEM as a Cloud Service, y compris la mise en service en libre-service et l’approvisionnement API des ports VPN, non standard et des adresses IP de sortie dédiées.

>[!TIP]
>
>Outre cette documentation, il existe également une série de tutoriels conçus pour vous guider dans les différentes options de mise en réseau avancées de cette [emplacement.](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/advanced-networking.html?lang=fr)

## Vue d’ensemble {#overview}

AEM as a Cloud Service propose les options de mise en réseau avancées suivantes :

* [Sortie de port flexible](#flexible-port-egress) - Configurez AEM as a Cloud Service pour autoriser le trafic sortant des ports non standard.
* [Adresse IP sortante dédiée](#dedicated-egress-ip-address) - Configurez le trafic en dehors d’AEM as a Cloud Service pour qu’il puisse provenir d’une adresse IP unique.
* [Réseau privé virtuel (VPN)](#vpn) - Sécurisez le trafic entre votre infrastructure et AEM as a Cloud Service, si vous disposez d’un VPN.

Cet article décrit d’abord en détail chacune de ces options et les raisons pour lesquelles vous pouvez les utiliser, avant de décrire comment elles sont configurées à l’aide de l’interface utilisateur de Cloud Manager et de l’API, et se termine par quelques cas d’utilisation avancés.

>[!CAUTION]
>
>Si vous disposez déjà d’une technologie de sortie dédiée héritée et que vous souhaitez configurer l’une de ces options de mise en réseau avancées, [veuillez d’abord contacter le service à la clientèle d’Adobe.](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;lang=fr#home)
>
>Toute tentative de configuration d’une mise en réseau avancée à l’aide de la technologie héritée peut avoir un impact sur la connectivité du site.

### Exigences et restrictions {#requirements}

Lors de la configuration de fonctionnalités réseau avancées, les restrictions suivantes s’appliquent.

* Un programme peut fournir une option de mise en réseau avancée unique (sortie de port flexible, adresse IP de sortie dédiée ou VPN).
* La mise en réseau avancée n’est pas disponible pour [programmes sandbox.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)
* Un utilisateur dans doit avoir la variable **Administrateur** rôle afin d’ajouter et de configurer l’infrastructure réseau dans votre programme.
* L’environnement de production doit être créé avant que l’infrastructure réseau puisse être ajoutée à votre programme.
* Votre infrastructure réseau doit se trouver dans la même région que la région principale de votre environnement de production.
   * Dans le cas où votre environnement de production possède [des régions de publication supplémentaires,](/help/implementing/cloud-manager/manage-environments.md#multiple-regions) vous pouvez créer une infrastructure réseau supplémentaire reflétant chaque région supplémentaire.
   * Vous ne serez pas autorisé à créer plus d&#39;infrastructures réseau que le nombre maximum de régions configurées dans votre environnement de production.
   * Vous pouvez définir autant d&#39;infrastructures réseau que de régions disponibles dans votre environnement de production, mais la nouvelle infrastructure doit être du même type que l&#39;infrastructure créée précédemment.
   * Lors de la création de plusieurs infrastructures, vous êtes autorisé à choisir parmi uniquement les régions dans lesquelles aucune infrastructure réseau avancée n&#39;a été créée.

### Configuration et activation de la mise en réseau avancée {#configuring-enabling}

L’utilisation de fonctionnalités de mise en réseau avancées nécessite deux étapes :

1. Configuration de l’option de mise en réseau avancée, selon que [sortie de port flexible,](#flexible-port-egress) [adresse IP sortante dédiée,](#dedicated-egress-ip-address) ou [VPN,](#vpn) doit d’abord être effectué au niveau du programme.
1. Pour être utilisée, l’option de mise en réseau avancée doit ensuite être activée au niveau de l’environnement.

Les deux étapes peuvent être effectuées à l’aide de l’interface utilisateur de Cloud Manager ou de l’API de Cloud Manager.

* Lorsque vous utilisez l’interface utilisateur de Cloud Manager, cela signifie créer des configurations réseau avancées à l’aide d’un assistant au niveau du programme, puis modifier chaque environnement dans lequel vous souhaitez activer la configuration.

* Lors de l’utilisation de l’API Cloud Manager, la variable `/networkInfrastructures` Le point de terminaison de l’API est appelé au niveau du programme pour déclarer le type souhaité de mise en réseau avancée, suivi d’un appel au `/advancedNetworking` point d’entrée pour chaque environnement afin d’activer l’infrastructure et de configurer des paramètres spécifiques à l’environnement.

## Sortie de port flexible {#flexible-port-egress}

Cette fonctionnalité de mise en réseau avancée vous permet de configurer AEM as a Cloud Service pour récupérer le trafic par des ports autres que HTTP (port 80) et HTTPS (port 443), qui sont ouverts par défaut.

>[!TIP]
>
>Lorsque vous hésitez entre une adresse IP de sortie de port flexible et de sortie dédiée, il est recommandé de choisir une sortie de port flexible si aucune adresse IP spécifique n’est requise, car Adobe peut optimiser les performances du trafic de sortie de port flexible.

>[!NOTE]
>
>Une fois créés, les types d’infrastructure de sortie de port flexibles ne peuvent pas être modifiés. La seule façon de modifier les valeurs de configuration consiste à les supprimer et à les recréer.

### Configuration de l’interface utilisateur {#configuring-flexible-port-egress-provision-ui}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur le **[Mes programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#my-programs)** sélectionnez le programme.

1. Dans la **Aperçu du programme** , accédez à la **Environnements** et sélectionnez **Infrastructure réseau** dans le panneau de gauche.

   ![Ajouter une infrastructure réseau](assets/advanced-networking-ui-network-infrastructure.png)

1. Dans le **Ajout d’une infrastructure réseau** assistant qui démarre, sélectionnez **Sortie de port flexible** et de la région dans laquelle il doit être créé à partir de la variable **Région** menu déroulant, puis appuyez ou cliquez sur **Continuer**.

   ![Configuration d’une sortie de port flexible](assets/advanced-networking-ui-flexible-port-egress.png)

1. La variable **Confirmation** résume votre sélection et les étapes suivantes. Appuyez ou cliquez sur **Enregistrer** pour créer l’infrastructure.

   ![Confirmation de la configuration d’une sortie de port flexible](assets/advanced-networking-ui-flexible-port-egress-confirmation.png)

Un nouvel enregistrement s’affiche sous le **Infrastructure réseau** dans le panneau latéral, y compris des détails sur le type d’infrastructure, l’état, la région et les environnements sur lesquels elle a été activée.

![Nouvelle entrée sous infrastructure réseau](assets/advanced-networking-ui-flexible-port-egress-new-entry.png)

>[!NOTE]
>
>La création de l&#39;infrastructure pour une sortie de port flexible peut prendre jusqu&#39;à une heure après laquelle elle peut être configurée au niveau de l&#39;environnement.

### Configuration de l’API {#configuring-flexible-port-egress-provision-api}

Une fois par programme, le point d’entrée `/program/<programId>/networkInfrastructures` POST est invoqué, simplement en transmettant la valeur du `flexiblePortEgress` pour le paramètre de `kind` et de région. Le point de terminaison répond avec la variable `network_id`, ainsi que d’autres informations, y compris l’état.

Une fois l’appel lancé, l’approvisionnement de l’infrastructure réseau prend généralement environ 15 minutes. Un appel au [point d’entrée des infrastructures réseau](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getNetworkInfrastructure) afficherait un état de **ready**.

>[!TIP]
>
>L&#39;ensemble complet des paramètres, la syntaxe exacte et des informations importantes telles que les paramètres qui ne peuvent pas être modifiés plus tard, [peut être référencé dans la documentation de l’API.](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/createNetworkInfrastructure)

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

#### Configuration Apache/Dispatcher {#apache-dispatcher}

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

## Adresse IP Egress dédiée {#dedicated-egress-ip-address}

Une adresse IP dédiée peut améliorer la sécurité lors de l’intégration avec les fournisseurs SaaS (comme un fournisseur de gestion de la relation client) ou d’autres intégrations en dehors d’AEM as a Cloud Service qui offrent une liste autorisée d’adresses IP. L’ajout de l’adresse IP dédiée à la liste autorisée garantit que seul le trafic provenant de l’instance AEM as a Cloud Service du client est autorisé à circuler dans le service externe. Cela s’ajoute au trafic provenant de toute autre adresse IP autorisée.

La même adresse IP dédiée est appliquée à tous les programmes de votre organisation Adobe et à tous les environnements de chacun de vos programmes. Elle s’applique aux services de création et de publication.

Si la fonction d’adresse IP dédiée n’est pas activée, le trafic provenant d’AEM as a Cloud Service passe par un ensemble d’adresses IP partagées avec d’autres clients AEM as a Cloud Service.

La configuration de l’adresse IP sortante dédiée est similaire à [sortie de port flexible.](#flexible-port-egress) La principale différence est qu’après la configuration, le trafic sortira toujours d’une adresse IP dédiée et unique. Pour trouver cette adresse IP, utilisez un résolveur DNS pour identifier l’adresse IP associée à `p{PROGRAM_ID}.external.adobeaemcloud.com`. L’adresse IP ne doit pas changer, mais si elle doit changer, une notification avancée est fournie.

>[!TIP]
>
>Lorsque vous hésitez entre une adresse IP de sortie de port flexible et de sortie dédiée, il est recommandé de choisir une sortie de port flexible si aucune adresse IP spécifique n’est requise, car Adobe peut optimiser les performances du trafic de sortie de port flexible.

>[!NOTE]
>
>Si une adresse IP de sortie dédiée vous a été fournie avant la version 2021.09.30 (c’est-à-dire avant la version de septembre 2021), votre fonction IP de sortie dédiée ne prend en charge que les ports HTTP et HTTPS.
>
>Inclut le HTTP/1.1 et HTTP/2 lorsqu’ils sont chiffrés. De plus, un point d’entrée de sortie dédié peut uniquement communiquer avec une cible via HTTP/HTTPS sur les ports 80/443, respectivement.

>[!NOTE]
>
>Une fois créés, les types d’infrastructure d’adresses IP sortantes dédiés ne peuvent pas être modifiés. La seule façon de modifier les valeurs de configuration consiste à les supprimer et à les recréer.

>[!INFO]
>
>La fonctionnalité de transfert Splunk n’est pas possible à partir d’une adresse IP de sortie dédiée.

### Configuration de l’interface utilisateur {#configuring-dedicated-egress-provision-ui}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur le **[Mes programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#my-programs)** sélectionnez le programme.

1. Dans la **Aperçu du programme** , accédez à la **Environnements** et sélectionnez **Infrastructure réseau** dans le panneau de gauche.

   ![Ajouter une infrastructure réseau](assets/advanced-networking-ui-network-infrastructure.png)

1. Dans le **Ajout d’une infrastructure réseau** assistant qui démarre, sélectionnez **Adresse IP sortante dédiée** et de la région dans laquelle il doit être créé à partir de la variable **Région** menu déroulant, puis appuyez ou cliquez sur **Continuer**.

   ![Configuration d’une adresse IP de sortie dédiée](assets/advanced-networking-ui-dedicated-egress.png)

1. La variable **Confirmation** résume votre sélection et les étapes suivantes. Appuyez ou cliquez sur **Enregistrer** pour créer l’infrastructure.

   ![Confirmation de la configuration d’une sortie de port flexible](assets/advanced-networking-ui-dedicated-egress-confirmation.png)

Un nouvel enregistrement s’affiche sous le **Infrastructure réseau** dans le panneau latéral, y compris des détails sur le type d’infrastructure, l’état, la région et les environnements sur lesquels elle a été activée.

![Nouvelle entrée sous infrastructure réseau](assets/advanced-networking-ui-flexible-port-egress-new-entry.png)

>[!NOTE]
>
>La création de l&#39;infrastructure pour une sortie de port flexible peut prendre jusqu&#39;à une heure après laquelle elle peut être configurée au niveau de l&#39;environnement.

### Configuration de l’API {#configuring-dedicated-egress-provision-api}

Une fois par programme, le point d’entrée `/program/<programId>/networkInfrastructures` POST est invoqué, simplement en transmettant la valeur du `dedicatedEgressIp` pour le paramètre de `kind` et de région. Le point de terminaison répond avec la variable `network_id`, ainsi que d’autres informations, y compris l’état.

Une fois l’appel lancé, l’approvisionnement de l’infrastructure réseau prend généralement environ 15 minutes. Un appel au [point d’entrée des infrastructures réseau](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getNetworkInfrastructure) afficherait un état de **ready**.

>[!TIP]
>
>L&#39;ensemble complet des paramètres, la syntaxe exacte et des informations importantes telles que les paramètres qui ne peuvent pas être modifiés plus tard, [peut être référencé dans la documentation de l’API.](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/createNetworkInfrastructure)

### Routage du trafic {#dedicated-egress-ip-traffic-routing}

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

### Considérations relatives au débogage {#debugging-considerations}

Pour contrôler que le trafic est effectivement sortant sur l’adresse IP dédiée attendue, vérifiez les journaux dans le service de destination, si disponible. Dans le cas contraire, il peut s’avérer utile d’appeler un service de débogage tel que [https://ifconfig.me/IP](https://ifconfig.me/IP), qui renverra l’adresse IP d’appel.

## Réseau privé virtuel (VPN) {#vpn}

Un VPN permet de se connecter à une infrastructure on-premise ou à un centre de données à partir des instances d’auteur, de publication ou d’aperçu. Cela peut être utile, par exemple, pour sécuriser l’accès à une base de données. Il permet également de se connecter aux fournisseurs SaaS tels qu’un fournisseur de gestion de la relation client qui prend en charge VPN ou de se connecter à partir d’un réseau d’entreprise AEM une instance as a Cloud Service de création, de prévisualisation ou de publication.

La plupart des appareils VPN dotés de la technologie IPSec sont pris en charge. Consultez les informations de la section **Instructions de configuration basées sur la route** colonne dans [cette liste d’appareils.](https://docs.microsoft.com/fr-fr/azure/vpn-gateway/vpn-gateway-about-vpn-devices#devicetable) Configurez le périphérique comme décrit dans le tableau.

>[!NOTE]
>
>Veuillez noter ces limitations à l&#39;infrastructure VPN :
>
>* La prise en charge est limitée à une VPN unique.
>* La fonctionnalité de transfert Splunk n’est pas possible via une connexion VPN.
>* Les résolveurs DNS doivent être répertoriés dans l’espace Adresse de passerelle pour résoudre les noms d’hôte privés.

### Configuration de l’interface utilisateur {#configuring-vpn-ui}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur le **[Mes programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#my-programs)** sélectionnez le programme.

1. Dans la **Aperçu du programme** , accédez à la **Environnements** et sélectionnez **Infrastructure réseau** dans le panneau de gauche.

   ![Ajouter une infrastructure réseau](assets/advanced-networking-ui-network-infrastructure.png)

1. Dans le **Ajout d’une infrastructure réseau** assistant qui démarre, sélectionnez **Réseau privé virtuel** et fournissez les informations nécessaires avant d’appuyer ou de cliquer sur **Continuer**.

   * **Région** - C&#39;est la région dans laquelle les infrastructures doivent être créées.
   * **Emplacement de l’adresse** - L’espace d’adresse ne peut être que d’un /26 CIDR (64 adresses IP) ou d’une plage d’adresses IP plus grande dans l’espace client.
      * Cette valeur ne peut pas être modifiée ultérieurement.
   * **Informations DNS** - Il s’agit d’une liste de résolveurs DNS distants.
      * Presse `Enter` après avoir saisi une adresse de serveur DNS pour en ajouter une autre.
      * Appuyez ou cliquez sur le bouton `X` après une adresse pour la supprimer.
   * **Clé partagée** - Il s&#39;agit de votre clé prépartagée VPN.
      * Sélectionner **Afficher la clé partagée** pour afficher la clé afin de vérifier sa valeur.

   ![Configuration de vpn](assets/advanced-networking-ui-vpn.png)

1. Sur le **Connexions** de l’assistant, fournissez un **Nom de la connexion** pour identifier votre connexion VPN, appuyez ou cliquez sur **Ajouter une connexion**.

   ![Ajout d’une connexion](assets/advanced-networking-ui-vpn-add-connection.png)

1. Dans le **Ajout d’une connexion** , définissez votre connexion VPN, puis appuyez ou cliquez sur **Enregistrer**.

   * **Nom de la connexion** - Il s’agit d’un nom descriptif de votre connexion VPN, que vous avez fourni à l’étape précédente et que vous pouvez mettre à jour ici.
   * **Adresse** - Il s’agit de l’adresse IP du périphérique VPN.
   * **Emplacement de l’adresse** - Il s’agit des plages d’adresses IP à acheminer par le VPN.
      * Presse `Enter` après avoir saisi une plage pour en ajouter une autre.
      * Appuyez ou cliquez sur le bouton `X` après une plage à supprimer.
   * **Stratégie de sécurité IP** - Ajustez les valeurs par défaut selon les besoins.

   ![Ajouter une connexion VPN](assets/advanced-networking-ui-vpn-adding-connection.png)

1. La boîte de dialogue se ferme et vous revenez à la **Connexions** de l’assistant. Cliquez ou appuyez sur **Continuer**.

   ![Ajout d’une connexion VPN](assets/advanced-networking-ui-vpn-connection-added.png)

1. La variable **Confirmation** résume votre sélection et les étapes suivantes. Appuyez ou cliquez sur **Enregistrer** pour créer l’infrastructure.

   ![Confirmation de la configuration d’une sortie de port flexible](assets/advanced-networking-ui-vpn-confirm.png)

Un nouvel enregistrement s’affiche sous le **Infrastructure réseau** dans le panneau latéral, y compris des détails sur le type d’infrastructure, l’état, la région et les environnements sur lesquels elle a été activée.

### Configuration de l’API {#configuring-vpn-api}

Une fois par programme, le POST `/program/<programId>/networkInfrastructures` Le point de terminaison est appelé, transmettant un payload d’informations de configuration, notamment : la valeur de **vpn** pour le `kind` paramètre, région, espace d’adresse (liste des CIDR - notez que cela ne peut pas être modifié plus tard), les résolveurs DNS (pour résoudre les noms dans le réseau du client) et les informations de connexion VPN telles que la configuration de la passerelle, la clé VPN partagée et la politique de sécurité IP. Le point de terminaison répond avec la variable `network_id`, ainsi que d’autres informations, y compris l’état.

Une fois l’appel lancé, l’approvisionnement de l’infrastructure réseau prend généralement entre 45 et 60 minutes. La méthode GET de l’API peut être appelée pour renvoyer le statut actuel, qui finira par passer de `creating` à `ready`. Consultez la documentation de l’API pour connaître tous les statuts.

>[!TIP]
>
>L&#39;ensemble complet des paramètres, la syntaxe exacte et des informations importantes telles que les paramètres qui ne peuvent pas être modifiés plus tard, [peut être référencé dans la documentation de l’API.](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/createNetworkInfrastructure)

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
    <td>Si l’adresse IP n’est pas comprise dans la plage d’<i>espace d’adressage de la passerelle VPN</i>, et par la configuration du proxy http (configurée par défaut pour le trafic http/s à l’aide de la bibliothèque cliente HTTP Java standard)</td>
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
    <td>Si l’adresse IP n’est pas comprise dans la plage d’<i>espace d’adressage de la passerelle VPN</i> et que le client ou la cliente se connecte à la variable d’environnement <code>AEM_PROXY_HOST</code> à l’aide d’un <code>portOrig</code> déclaré dans le paramètre d’API <code>portForwards</code></td>
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

### Domaines utiles à la configuration {#vpn-useful-domains-for-configuration}

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

#### Exemple de configuration Httpd {#httpd-example}

```
Order deny,allow
Deny from all
Allow from 192.168.0.1
Header always set Cache-Control private
```

## Activation des configurations réseau avancées dans les environnements {#enabling}

Une fois que vous avez configuré une option de mise en réseau avancée pour un programme, indiquez si [sortie de port flexible,](#flexible-port-egress) [adresse IP sortante dédiée,](#dedicated-egress-ip-address) ou [VPN,](#vpn) pour l&#39;utiliser, vous devez l&#39;activer au niveau de l&#39;environnement.

Lorsque vous activez une configuration réseau avancée pour un environnement, vous avez la possibilité d’activer le transfert de port facultatif et les hôtes non proxy. Les paramètres sont configurables par environnement afin d’offrir une certaine flexibilité.

* **Transfert de port** - Les règles de transfert de port doivent être déclarées pour les ports de destination autres que le port 80/443, mais uniquement si vous n’utilisez pas le protocole http ou https.
   * Les règles de transfert de port sont définies en spécifiant l’ensemble des hôtes de destination (noms ou adresses IP, et ports).
   * La connexion client utilisant le port 80/443 via http/https doit toujours utiliser les paramètres proxy dans leur connexion pour que les propriétés de la mise en réseau avancée soient appliquées à la connexion.
   * Pour chaque hôte de destination, les clients doivent mapper le port de destination prévu à un port entre 30 000 et 30 999.
   * Les règles de transfert de port sont disponibles pour tous les types de mise en réseau avancés.

* **Hôtes non proxy** - Les hôtes non proxy vous permettent de déclarer un ensemble d’hôtes qui doivent passer par une plage d’adresses IP partagées plutôt que par l’adresse IP dédiée.
   * Cela peut s’avérer utile, car le trafic passant par les adresses IP partagées peut être encore optimisé.
   * Les hôtes non proxy ne sont disponibles que pour les adresses IP de sortie dédiées et les types de réseau avancé VPN.

>[!NOTE]
>
>Si l’environnement se trouve dans la variable **Mise à jour** statut.

### Activation de l’interface utilisateur {#enabling-ui}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur le **[Mes programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#my-programs)** sélectionnez le programme.

1. Dans la **Aperçu du programme** , accédez à la **Environnements** et sélectionnez l’environnement dans lequel vous souhaitez activer la configuration réseau avancée sous l’onglet **Environnements** dans le panneau de gauche. Sélectionnez ensuite le **Configuration réseau avancée** de l’environnement sélectionné, puis appuyez ou cliquez sur **Activation de l’infrastructure réseau**.

   ![Sélection de l’environnement pour activer la mise en réseau avancée](assets/advanced-networking-ui-enable-environments.png)

1. La variable **Configuration de la mise en réseau avancée** s’ouvre.

1. Sur le **Hôtes non proxy** , pour les adresses IP sortantes dédiées et les VPN, vous pouvez éventuellement définir un ensemble d’hôtes, qui doivent être acheminés par une plage d’adresses IP partagées plutôt que par l’adresse IP dédiée, en fournissant le nom d’hôte dans la variable **Hôte non proxy** champ et appuyer ou cliquer **Ajouter**.

   * L’hôte est ajouté à la liste des hôtes sur l’onglet .
   * Répétez cette étape pour ajouter plusieurs hôtes.
   * Appuyez ou cliquez sur le X situé à droite de la ligne pour supprimer un hôte.
   * Cet onglet n’est pas disponible pour les configurations flexibles de sortie de port.

   ![Ajout d’hôtes non-proxy](assets/advanced-networking-ui-enable-non-proxy-hosts.png)

1. Sur le **Port en avant** , vous pouvez éventuellement définir des règles de transfert de port pour les ports de destination autres que le port 80/443 si vous n’utilisez pas le protocole HTTP ou HTTPS. Fournissez une **Nom**, **Orig de port**, et **Port Dest** et appuyez ou cliquez sur **Ajouter**.

   * La règle est ajoutée à la liste des règles de l’onglet .
   * Répétez cette étape pour ajouter plusieurs règles.
   * Appuyez ou cliquez sur le X situé à droite de la ligne pour supprimer une règle.

   ![Définir les transferts de port facultatifs](assets/advanced-networking-ui-port-forwards.png)

1. Appuyez ou cliquez sur **Enregistrer** dans la boîte de dialogue pour appliquer la configuration à l’environnement.

La configuration réseau avancée est appliquée à l’environnement sélectionné. De retour sur le **Environnements** vous pouvez voir les détails de la configuration appliquée à l&#39;environnement sélectionné et leur état.

![Environnement configuré avec une mise en réseau avancée](assets/advanced-networking-ui-configured-environment.png)

### Activation à l’aide de l’API {#enabling-api}

Pour activer une configuration réseau avancée pour un environnement, la méthode `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` Le point de terminaison doit être appelé par environnement.

L’API doit répondre en quelques secondes seulement et indiquer un statut `updating` et, au bout d’environ 10 minutes, un appel au point d’entrée de l’environnement de Cloud Manager affiche le statut `ready`, indiquant que la mise à jour de l’environnement a été appliquée.

Les règles de transfert de port par environnement peuvent être mises à jour en appelant la fonction `PUT /program/{programId}/environment/{environmentId}/advancedNetworking` et inclure l’ensemble complet des paramètres de configuration, plutôt qu’un sous-ensemble.

Les types de réseau avancé VPN et les adresses IP sortantes dédiées prennent en charge une `nonProxyHosts` . Vous pouvez ainsi déclarer un ensemble d’hôtes qui doivent passer par une plage d’adresses IP partagées plutôt que par l’adresse IP dédiée. Les URL `nonProxyHost` peuvent être calquées sur `example.com` ou `*.example.com`, le caractère générique n’étant pris en charge qu’au début du domaine.

Notez que même en l’absence de règles de routage du trafic de l’environnement (hôtes ou contournements), `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` doit toujours être appelé mais avec une payload vide.

>[!TIP]
>
>L&#39;ensemble complet des paramètres, la syntaxe exacte et des informations importantes telles que les paramètres qui ne peuvent pas être modifiés plus tard, [peut être référencé dans la documentation de l’API.](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/createNetworkInfrastructure)

## Modification et suppression de configurations réseau avancées dans des environnements {#editing-deleting-environments}

Après [l&#39;activation d&#39;une configuration réseau avancée pour les environnements,](#enabling) vous pouvez mettre à jour les détails de ces configurations ou les supprimer.

>[!NOTE]
>
>Vous ne pouvez pas modifier l’infrastructure réseau si elle a le statut **Création**, **Mise à jour**, ou **Suppression**.

### Modification ou suppression dans l’interface utilisateur {#editing-ui}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur le **[Mes programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#my-programs)** sélectionnez le programme.

1. Dans la **Aperçu du programme** , accédez à la **Environnements** et sélectionnez l’environnement dans lequel vous souhaitez activer la configuration réseau avancée sous l’onglet **Environnements** dans le panneau de gauche. Sélectionnez ensuite le **Configuration réseau avancée** de l’environnement sélectionné et appuyez ou cliquez sur le bouton représentant des points de suspension.

   ![Sélectionner la modification ou la suppression de la mise en réseau avancée au niveau du programme](assets/advanced-networking-ui-edit-delete.png)

1. Dans le menu représentant des points de suspension, sélectionnez **Modifier** ou **Supprimer**.

   * Si vous choisissez **Modifier**, mettre à jour les informations selon les étapes décrites dans la section précédente, [Activation de l’interface utilisateur,](#enabling-ui) et appuyez ou cliquez sur **Enregistrer**.
   * Si vous choisissez **Supprimer**, confirmez la suppression dans le **Suppression de la configuration réseau** Boîte de dialogue avec **Supprimer** ou abandonner avec **Annuler**.

Les modifications seront répercutées sur la variable **Environnements** .

### Modification ou suppression à l’aide de l’API {#editing-api}

Pour supprimer la mise en réseau avancée pour un environnement particulier, appelez `DELETE [/program/{programId}/environment/{environmentId}/advancedNetworking]()`.

>[!TIP]
>
>L&#39;ensemble complet des paramètres, la syntaxe exacte et des informations importantes telles que les paramètres qui ne peuvent pas être modifiés plus tard, [peut être référencé dans la documentation de l’API.](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/createNetworkInfrastructure)

## Modification et suppression de l’infrastructure réseau d’un programme {#editing-deleting-program}

Une fois l’infrastructure réseau créée pour un programme, seules les propriétés limitées peuvent être modifiées. Si vous n’en avez plus besoin, vous pouvez supprimer l’infrastructure réseau avancée pour l’ensemble de votre programme.

>[!NOTE]
>
>Veuillez noter que les restrictions suivantes s’appliquent à la modification et à la suppression de l’infrastructure réseau :
>
>* La suppression ne supprime l’infrastructure que si les réseaux avancés de tous les environnements sont désactivés.
>* Vous ne pouvez pas modifier l’infrastructure réseau si elle a le statut **Création**, **Mise à jour**, ou **Suppression**.
>* Seul le type d&#39;infrastructure réseau avancé VPN peut être modifié une fois créé, puis uniquement des champs limités.
>* Pour des raisons de sécurité, la variable **Clé partagée** doit toujours être fourni lors de l&#39;édition d&#39;une infrastructure réseau avancée VPN, même si vous ne modifiez pas la clé elle-même.

### Modification et suppression dans l’interface utilisateur {#delete-ui}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée

1. Sur le **[Mes programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#my-programs)** sélectionnez le programme.

1. Dans la **Aperçu du programme** , accédez à la **Environnements** et sélectionnez **Infrastructure réseau** dans le panneau de gauche. Ensuite, appuyez ou cliquez sur le bouton représentant des points de suspension en regard de l’infrastructure que vous souhaitez supprimer.

   ![Sélectionner la modification ou la suppression de la mise en réseau avancée au niveau du programme](assets/advanced-networking-ui-delete-infrastructure.png)

1. Dans le menu représentant des points de suspension, sélectionnez **Modifier** ou **Supprimer**.

1. Si vous choisissez **Modifier**, la variable **Modification de l’infrastructure réseau** s’ouvre. Modifiez selon les besoins en suivant les étapes décrites lors de la création de l’infrastructure.

1. Si vous choisissez **Supprimer**, confirmez la suppression dans le **Suppression de la configuration réseau** Boîte de dialogue avec **Supprimer** ou abandonner avec **Annuler**.

Les modifications seront répercutées sur la variable **Environnements** .

### Modification et suppression avec l’API {#delete-api}

Pour **supprimer** l’infrastructure réseau d’un programme, appelez `DELETE /program/{program ID}/networkinfrastructure/{networkinfrastructureID}`.

## Modification du type d’infrastructure réseau avancée d’un programme {#changing-program}

Il n’est possible de configurer qu’un seul type d’infrastructure réseau avancée pour un programme à la fois, soit une sortie de port flexible, une adresse IP de sortie dédiée ou un VPN.

Si vous décidez que vous avez besoin d’un autre type d’infrastructure réseau avancé que celui que vous avez déjà configuré, vous devez supprimer le type existant et en créer un nouveau. Procédez comme suit :

1. [Supprimez la mise en réseau avancée dans tous les environnements.](#editing-deleting-environments)
1. [Supprimez l’infrastructure réseau avancée.](#editing-deleting-program)
1. Créez le type d’infrastructure réseau avancé dont vous avez besoin, au choix : [sortie de port flexible,](#flexible-port-egress) [adresse IP sortante dédiée,](#dedicated-egress-ip-address) ou [VPN.](#vpn)
1. [Réactivez la mise en réseau avancée au niveau de l’environnement.](#enabling)

>[!WARNING]
>
> Cette procédure entraîne une interruption des services de mise en réseau avancés entre la suppression et la recréation.
> Si l’interruption devait entraîner un impact important sur l’activité, contactez le service clientèle pour obtenir de l’aide, en décrivant ce qui a déjà été créé et la raison du changement.

## Configuration de réseau avancée pour des régions de publication supplémentaires {#advanced-networking-configuration-for-additional-publish-regions}

Lorsqu’une région supplémentaire est ajoutée à un environnement qui dispose déjà d’une mise en réseau avancée configurée, le trafic de la région de publication supplémentaire qui correspond aux règles de mise en réseau avancée traverse par défaut la région principale. Toutefois, si la région principale n’est plus disponible, le trafic de mise en réseau avancée est abandonné si la mise en réseau avancée n’a pas été activée dans la région supplémentaire. Si vous souhaitez optimiser la latence et augmenter la disponibilité en cas de panne de l’une des régions, il est nécessaire d’activer une mise en réseau avancée pour la ou les régions de publication supplémentaires. Les sections ci-après décrivent deux scénarios différents.

>[!NOTE]
>
>Toutes les régions partagent la même [configuration de mise en réseau avancée de l’environnement](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Environment-Advanced-Networking-Configuration), il n’est donc pas possible d’acheminer le trafic vers différentes destinations en fonction de la région d’où il provient.

### Adresse IP de sortie dédiée {#additional-publish-regions-dedicated-egress}

#### Mise en réseau avancée déjà activée dans la région principale {#already-enabled}

Si une configuration de mise en réseau avancée est déjà activée dans la région principale, procédez comme suit :

1. Si vous avez verrouillé votre infrastructure de sorte que l’adresse IP AEM dédiée soit répertoriée, il est recommandé de désactiver temporairement toute règle de refus dans cette infrastructure. Si ce n’est pas fait, il y a une courte période pendant laquelle les demandes provenant des adresses IP de la nouvelle région sont refusées par votre propre infrastructure. Notez que cela n’est pas nécessaire si vous avez verrouillé votre infrastructure via le nom de domaine complet (`p1234.external.adobeaemcloud.com`, par exemple), car toutes les régions AEM émettent un trafic de mise réseau avancée du même nom de domaine complet.
1. Créez l’infrastructure de mise en réseau à portée de programme pour la région secondaire par le biais d’un appel POST à l’API de création d’infrastructure réseau de Cloud Manager, comme décrit dans la documentation de mise en réseau avancée. La seule différence dans la configuration JSON du payload par rapport à la région principale est la propriété de la région
1. Si votre infrastructure doit être verrouillée par IP pour autoriser le trafic AEM, ajoutez les adresses IP qui correspondent à `p1234.external.adobeaemcloud.com`. Il devrait y en avoir une par région.

#### Mise en réseau avancée non configurée dans une région {#not-yet-configured}

La procédure est essentiellement similaire aux instructions précédentes. Cependant, si l’environnement de production n’a pas encore été activé pour la mise en réseau avancée, vous avez la possibilité de tester la configuration en l’activant d’abord dans un environnement d’évaluation :

1. Créez une infrastructure de mise en réseau pour toutes les régions à l’aide d’un appel POST à l’[API de création d’infrastructure réseau de Cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Network-infrastructure/operation/createNetworkInfrastructure). La seule différence dans la configuration JSON du payload par rapport à la région principale est la propriété de la région.
1. Pour l’environnement d’évaluation, activez et configurez l’environnement mis en réseau avancé en exécutant `PUT api/program/{programId}/environment/{environmentId}/advancedNetworking`. Pour plus d’informations, voir la documentation de l’API [ici](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Environment-Advanced-Networking-Configuration/operation/enableEnvironmentAdvancedNetworkingConfiguration)
1. Si nécessaire, verrouillez l’infrastructure externe, de préférence par le nom de domaine complet (par exemple, `p1234.external.adobeaemcloud.com`). Vous pouvez également le faire par adresse IP
1. Si l’environnement d’évaluation fonctionne comme prévu, activez et configurez la configuration de mise en réseau avancée de l’environnement pour la production.

#### VPN {#vpn-regions}

La procédure est presque identique aux instructions d’adresses IP sortantes dédiées. La seule différence est qu’en plus de la propriété de région configurée différemment de la région principale, le champ `connections.gateway` peut éventuellement être configuré pour l’acheminement vers un autre point d’entrée VPN exploité par votre organisation, peut-être géographiquement plus proche de la nouvelle région.
