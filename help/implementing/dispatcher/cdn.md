---
title: Réseau CDN dans AEM as a Cloud Service
description: Découvrez comment utiliser le réseau de diffusion de contenu géré par AEM et comment pointer votre propre réseau de diffusion de contenu vers le réseau de diffusion de contenu géré par AEM.
feature: Dispatcher
exl-id: a3f66d99-1b9a-4f74-90e5-2cad50dc345a
role: Admin
source-git-commit: dd696580758e7ab9a5427d47fda4275f9ad7997f
workflow-type: tm+mt
source-wordcount: '1607'
ht-degree: 38%

---


# Réseau de diffusion de contenu dans AEM as a Cloud Service {#cdn}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_cdn"
>title="Réseau de diffusion de contenu dans AEM as a Cloud Service"
>abstract="AEM as a Cloud Service est fourni avec un réseau CDN. Son principal objectif est de réduire la latence en fournissant du contenu pouvant être mis en cache à partir des nœuds CDN en périphérie, près du navigateur. Il est entièrement géré et configuré afin de permettre des performances optimales des applications AEM."

AEM as a Cloud Service est fourni avec un réseau de diffusion de contenu intégré, conçu pour réduire la latence en fournissant du contenu pouvant être mis en cache à partir des noeuds périphériques proches du navigateur de l’utilisateur. Ce réseau de diffusion de contenu entièrement géré est optimisé pour AEM performances de l’application.

Le réseau de diffusion de contenu géré par AEM répond aux besoins de performances et de sécurité de la plupart des clients. Pour le niveau de publication, les clients peuvent choisir d’acheminer le trafic par le biais de leur propre réseau de diffusion de contenu, qu’ils doivent gérer. Cette option est disponible au cas par cas, en particulier lorsque les clients disposent d’intégrations héritées existantes avec un fournisseur CDN difficiles à remplacer.

Les clients qui souhaitent publier du contenu sur le niveau Edge Delivery Services peuvent tirer parti du réseau de diffusion de contenu géré par Adobe. Voir [Adobe du réseau de diffusion de contenu géré ](#aem-managed-cdn). <!-- CQDOC-21758, 5b -->


<!-- ERROR: NEITHER URL IS FOUND (HTTP ERROR 404) Also, see the following videos [Cloud 5 AEM CDN Part 1](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-cdn-part1.html) and [Cloud 5 AEM CDN Part 2](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-cdn-part2.html) for additional information about CDN in AEM as a Cloud Service. -->

## Réseau CDN géré par Adobe {#aem-managed-cdn}

<!-- CQDOC-21758, 5a -->

Pour vous préparer à la diffusion de contenu à l’aide AEM du réseau de diffusion de contenu intégré via l’interface utilisateur en libre-service Cloud Manager, vous pouvez tirer parti des fonctionnalités de réseau de diffusion de contenu géré par Adobe. Cette fonctionnalité vous permet de gérer la gestion du réseau de diffusion de contenu en libre-service, y compris de configurer et d’installer des certificats SSL tels que DV (Domain Validation) ou EV/OV (Extended/Organization Validation). Pour plus d’informations sur ces méthodes, voir :

* [Gestion des certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
* [Ajouter une configuration CDN](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md)
* [Gestion des noms de domaine personnalisés](/help/implementing/cloud-manager/custom-domain-names/introduction.md)
* [Assistance Edge Delivery Services dans Cloud Manager](/help/implementing/cloud-manager/edge-delivery-services.md)


**Limitation du trafic**

Par défaut, dans le cas d’une configuration de réseau CDN géré par AEM, tout le trafic public peut se diriger vers le service de publication, tant pour les environnements de production que les environnements de non-production (de développement et d’évaluation). Vous pouvez limiter le trafic vers le service de publication pour un environnement donné (par exemple, en limitant l’évaluation par une plage d’adresses IP) au moyen de l’interface utilisateur de Cloud Manager.

Consultez [Gestion des listes d’adresses IP autorisées](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) pour en savoir plus.

>[!CAUTION]
>
>L’AEM du réseau de diffusion de contenu géré ne diffuse des requêtes qu’à partir des adresses IP autorisées. Si vous pointez votre propre réseau de diffusion de contenu vers le réseau de diffusion de contenu géré par AEM, assurez-vous que les adresses IP de votre réseau de diffusion de contenu sont incluses dans la Liste autorisée IP.

### Configuration du trafic sur le réseau de diffusion de contenu {#cdn-configuring-cloud}

Vous pouvez configurer le trafic sur le réseau de diffusion de contenu de différentes manières, notamment :

* blocage du trafic malveillant avec les [règles de filtrage du trafic](/help/security/traffic-filter-rules-including-waf.md) (y compris, éventuellement, les règles WAF avancées sous licence)
* modification de la nature de la [requête et réponse](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations)
* application 301/302 [redirections côté client](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors)
* déclaration de [sélecteurs d’origine](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors) pour inverser le proxy d’une requête aux serveurs principaux non AEM

Utilisez les fichiers YAML dans Git pour configurer ces fonctionnalités. Utilisez également le [pipeline de configuration](/help/implementing/dispatcher/cdn-configuring-traffic.md) de Cloud Manager pour les déployer.

### Configuration des pages d’erreur CDN {#cdn-error-pages}

Vous pouvez configurer une page d’erreur CDN pour remplacer la page sans marque par défaut. Cette page personnalisée s’affiche dans le rare cas où AEM n’est pas disponible. Pour plus d’informations, voir [Configuration des pages d’erreur CDN](/help/implementing/dispatcher/cdn-error-pages.md).

### Purge du contenu mis en cache sur le réseau de diffusion de contenu {#purge-cdn}

La définition de la durée de vie (TTL) à l’aide de l’en-tête de contrôle du cache HTTP est une approche efficace pour équilibrer les performances de diffusion du contenu et l’actualisation du contenu. Cependant, dans les cas où il est essentiel de diffuser du contenu mis à jour immédiatement, il peut être bénéfique de purger directement le cache CDN.

Découvrez [la configuration d&#39;un jeton API de purge](/help/implementing/dispatcher/cdn-credentials-authentication.md/#purge-API-token) et [la purge du contenu CDN mis en cache](/help/implementing/dispatcher/cdn-cache-purge.md).

### Authentification de base sur le réseau de diffusion de contenu {#basic-auth}

Pour les cas d’utilisation de l’authentification légère, y compris les parties prenantes de l’entreprise qui examinent le contenu, protégez le contenu en affichant une boîte de dialogue d’authentification de base nécessitant un nom d’utilisateur et un mot de passe. [En savoir plus](/help/implementing/dispatcher/cdn-credentials-authentication.md) et rejoignez le programme des premiers adopteurs.

## Le réseau de diffusion de contenu géré par le client pointe vers AEM réseau de diffusion de contenu géré {#point-to-point-CDN}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_byocdn"
>title="Le réseau de diffusion de contenu du client pointe vers le réseau de diffusion de contenu géré par AEM"
>abstract="AEM as a Cloud Service offre aux clients une option pour utiliser son réseau CDN. Pour le niveau de publication, les clients et clientes peuvent éventuellement privilégier leur propre réseau CDN, mais il leur appartiendra de le gérer. Ce scénario sera possible au cas par cas, en fonction de certaines conditions préalables, y compris, mais sans s’y limiter, le fait que le client ou la cliente possède une ancienne intégration avec son fournisseur CDN, et qu’il soit difficile de l’abandonner."

Si un client doit utiliser son réseau de diffusion de contenu existant, il peut le gérer et le pointer vers le réseau de diffusion de contenu géré par AEM, à condition que les conditions suivantes soient satisfaites :

* Le client doit disposer d’un réseau de diffusion de contenu existant qui serait onéreux à remplacer.
* Le client doit le gérer.
* Le client doit être en mesure de configurer le réseau de diffusion de contenu pour qu’il fonctionne avec AEM as a Cloud Service. Voir les instructions de configuration présentées ci-dessous.
* Le client doit disposer d’ingénieurs maîtrisant le réseau de diffusion de contenu et disponibles pour résoudre les problèmes liés aux cas.
* Le client doit effectuer et réussir un test de charge avant de passer en production.

Instructions de configuration :

1. Pointez votre réseau CDN sur l’entrée du réseau CDN d’Adobe en tant que domaine d’origine. Par exemple, `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.
1. Définissez le SNI sur l’entrée du réseau CDN d’Adobe.
1. Définissez l’en-tête hôte sur le domaine d’origine. Par exemple : `Host:publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.
1. Définissez l’en-tête `X-Forwarded-Host` avec le nom de domaine afin qu’AEM puisse déterminer l’en-tête hôte. Par exemple : `X-Forwarded-Host:example.com`.
1. Définir `X-AEM-Edge-Key`. La valeur doit être configurée à l’aide d’un pipeline de configuration Cloud Manager, comme décrit dans [cet article](/help/implementing/dispatcher/cdn-credentials-authentication.md#CDN-HTTP-value).

   * Ce paramétrage est nécessaire afin que le réseau CDN d’Adobe puisse valider la source des requêtes et transmettre les en-têtes `X-Forwarded-*` à l’application AEM. Par exemple,`X-Forwarded-For` est utilisé pour déterminer l’adresse IP du client. Il incombe donc à l’appelant de confiance (c’est-à-dire au réseau de diffusion de contenu géré par le client) de s’assurer que les en-têtes `X-Forwarded-*` sont corrects (voir la note ci-dessous).
   * L’accès à l’entrée du réseau CDN d’Adobe peut être aussi bloqué lorsqu’une balise `X-AEM-Edge-Key` n’est pas présente. Informez Adobe si vous avez besoin d’un accès direct à l’entrée du CDN d’Adobe (à bloquer).

Voir [Exemples de configurations de fournisseur de réseau CDN](#sample-configurations) pour consulter des exemples de configuration provenant de principaux fournisseurs de réseau CDN.

Avant d’accepter le trafic en direct, vous devez vérifier auprès du service clientèle d’Adobe que le routage du trafic de bout en bout fonctionne correctement.

Après avoir défini le `X-AEM-Edge-Key`, vous pouvez tester que la requête est correctement acheminée comme suit.

Sous Linux® :

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com -H "X-Forwarded-Host: example.com" -H "X-AEM-Edge-Key: <PROVIDED_EDGE_KEY>"
```

Sous Windows :

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com --header "X-Forwarded-Host: example.com" --header "X-AEM-Edge-Key: <PROVIDED_EDGE_KEY>"
```

>[!NOTE]
>
>Lorsque vous utilisez votre propre réseau CDN, il n’est pas nécessaire d’installer les domaines et les certificats dans Cloud Manager. Le routage dans le réseau de diffusion de contenu Adobe est effectué à l’aide du domaine par défaut `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`, qui doit être envoyé dans l’en-tête de la requête `Host`. Le remplacement de l’en-tête de la requête `Host` par un nom de domaine personnalisé peut incorrectement acheminer la requête via le réseau de diffusion de contenu Adobe.

>[!NOTE]
>
>Les clients qui gèrent leur propre réseau de diffusion de contenu doivent garantir l’intégrité des en-têtes envoyés au réseau de diffusion de contenu AEM. Par exemple, il est recommandé aux clients d’effacer tous les en-têtes `X-Forwarded-*` et de les définir sur des valeurs connues et contrôlées. Par exemple, `X-Forwarded-For` doit contenir l’adresse IP du client, tandis que `X-Forwarded-Host` doit contenir l’hôte du site.

>[!NOTE]
>
>Les environnements de programme Sandbox ne prennent pas en charge le réseau de diffusion de contenu fourni par le client.

Le passage du réseau CDN client au réseau CDN géré par AEM n’est nécessaire que dans le cas d’une interruption du cache. En utilisant les stratégies d’optimisation du cache décrites dans cet article, l’ajout d’un réseau CDN client ne doit introduire qu’une latence négligeable.

Cette configuration de réseau CDN client est prise en charge pour le niveau de publication, mais pas au niveau de la création.

### Exemples de configurations de fournisseur de réseau CDN {#sample-configurations}

Vous trouverez ci-dessous plusieurs exemples de configuration de plusieurs grands fournisseurs de réseau CDN.

**Akamai**

![Akamai1](assets/akamai1.png "Akamai")
![Akamai2](assets/akamai2.png "Akamai")

**Amazon CloudFront**

![CloudFront1](assets/cloudfront1.png "Amazon CloudFront")
![CloudFront2](assets/cloudfront2.png "Amazon CloudFront")

**Cloudflare**

![Cloudflare1](assets/cloudflare1.png "Cloudflare")
![Cloudflare2](assets/cloudflare2.png "Cloudflare")

### Erreurs courantes {#common-errors}

Les exemples de configurations fournis affichent les paramètres de base nécessaires. Cependant, une configuration client peut avoir d’autres règles d’impact qui suppriment, modifient ou réorganisent les en-têtes nécessaires pour qu’AEM as a Cloud Service diffuse le trafic. Vous trouverez ci-dessous des erreurs courantes qui se produisent lors de la configuration d’un réseau de diffusion de contenu géré par le client pour pointer vers AEM as a Cloud Service.

**Redirection vers le point d’entrée du service de publication**

Lorsqu’une requête reçoit une réponse 403 interdite, cela signifie que certains en-têtes requis lui manquent. Cela est généralement dû au fait que le réseau de diffusion de contenu gère à la fois le trafic de domaine apex et `www`, mais n’ajoute pas l’en-tête correct pour le domaine `www`. Ce problème peut être résolu en vérifiant vos journaux de réseau de diffusion de contenu AEM as a Cloud Service et en vérifiant les en-têtes de requête nécessaires.

**Trop de redirections Boucle**

Lorsqu’une page reçoit une boucle &quot;Trop de redirection&quot;, un en-tête de requête est ajouté au réseau de diffusion de contenu qui correspond à une redirection qui la force à se rediriger. Par exemple :

* Une règle CDN est créée pour correspondre au domaine apex ou au domaine www et ajoute l’en-tête X-Forwarded-Host du domaine apex uniquement.
* Une requête pour un domaine apex correspond à cette règle CDN, qui ajoute le domaine apex en tant qu’en-tête X-Forwarded-Host.
* Une requête est envoyée à l’origine où une redirection correspond explicitement à l’en-tête hôte pour le domaine d’application (par exemple, ^example.com).
* Une règle de réécriture est déclenchée, ce qui réécrit la demande pour le domaine d’expression vers https avec le sous-domaine www.
* Cette redirection est ensuite envoyée au serveur Edge du client, où la règle CDN est redéclenchée en ajoutant à nouveau l’en-tête X-Forwarded-Host pour le domaine apex et non le sous-domaine www. Ensuite, le processus recommence jusqu’à l’échec de la requête.

Pour résoudre ce problème, évaluez votre stratégie de redirection SSL, les règles CDN, les combinaisons de règles de redirection et de réécriture.

## En-têtes de géolocalisation {#geo-headers}

Le réseau de diffusion de contenu géré par AEM ajoute des en-têtes à chaque requête avec les éléments suivants :

* Le code de pays : `x-aem-client-country`
* Le code continent : `x-aem-client-continent`

>[!NOTE]
>
>S’il existe un réseau de diffusion de contenu géré par le client, ces en-têtes reflètent l’emplacement du serveur proxy CDN du client plutôt que le client réel. Les clients doivent gérer les en-têtes de géolocalisation par le biais de leur propre réseau de diffusion de contenu lors de l’utilisation d’un réseau de diffusion de contenu géré par le client.

Les valeurs des codes pays sont les codes Alpha-2 décrits sous [ISO 3166-1](https://fr.wikipedia.org/wiki/ISO_3166-1).

Les valeurs des codes du continent sont les suivantes :

* AF Afrique
* AN Antarctique
* AS Asie
* EU Europe
* NA Amérique du Nord
* OC Océanie
* SA Amérique du Sud

Ces informations sont utiles pour rediriger vers une autre URL basée sur le pays d’origine de la demande. Utilisez l’en-tête Vary pour mettre en cache les réponses qui dépendent des informations géographiques. Par exemple, les redirections vers la page de destination d’un pays spécifique doivent toujours contenir `Vary: x-aem-client-country`. Si nécessaire, vous pouvez utiliser `Cache-Control: private` pour empêcher la mise en cache. Voir aussi [Mise en cache](/help/implementing/dispatcher/caching.md#html-text).
