---
title: Compréhension des requêtes de contenu Cloud Service
description: Si vous avez acheté des licences de demande de contenu à Adobe, découvrez les types de demandes de contenu que Adobe Experience Cloud as a Service mesure et les écarts avec les outils de création de rapports d’analyse d’une entreprise.
exl-id: 3666328a-79a7-4dd7-b952-38bb60f0967d
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: a1b0d37b2f2f4e58b491651cb8e6504a6909393e
workflow-type: tm+mt
source-wordcount: '1381'
ht-degree: 10%

---

# Demandes de contenu Cloud Service

## Présentation {#introduction}

Les demandes de contenu sont des demandes qui arrivent dans AEM Sites (y compris en relation avec les Edge Delivery Services pour AEM Sites) ou tout autre système de mise en cache fourni par le client (comme un réseau de diffusion de contenu) pour diffuser du contenu ou des données au format HTML par le biais de pages vues (par exemple, des pages et des fragments d’expérience) ou au format JSON par le biais d’appels API (sans interface). Les demandes de contenu sont comptabilisées sous la forme d’une page vue ou de 5 appels d’API et sont mesurées à l’entrée du premier système de mise en cache qui reçoit une demande de contenu. Certaines requêtes HTTP sont incluses ou exclues à des fins de comptage des requêtes de contenu. La liste complète des requêtes HTTP incluses et exclues, ainsi que leurs définitions techniques, sont disponibles dans la documentation.

## Compréhension des requêtes de contenu Cloud Service {#understanding-cloud-service-content-requests}

Pour les clients qui utilisent le réseau de diffusion de contenu prêt à l’emploi, les demandes de contenu du Cloud Service sont mesurées par le biais d’une collecte de données côté serveur. Cette collection est activée via l’analyse des logs CDN. Les demandes de contenu sont automatiquement collectées côté serveur à la périphérie d’Adobe Experience Manager as a Cloud Service, via une analyse automatisée des fichiers journaux provenant du réseau de diffusion de contenu as a Cloud Service AEM. Pour ce faire, isolez le HTML de renvoi des demandes. `(text/html)` ou JSON `(application/json)` contenu du réseau de diffusion de contenu. Il est basé sur plusieurs règles d’inclusion et d’exclusion détaillées ci-dessous. Une demande de contenu se produit indépendamment du contenu renvoyé qui est diffusé à partir des caches CDN ou du contenu qui retourne à l’origine du CDN (AEM dispatchers).

Pour les clients qui utilisent leur propre réseau de diffusion de contenu, la collection côté client offre un reflet plus précis des interactions, assurant une mesure fiable de l’engagement du site web via la variable [Surveillance de l’utilisation réelle](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md) service. Les clients disposent ainsi d’informations avancées sur le trafic et les performances de leurs pages. Bien qu’il soit bénéfique pour tous les clients, il offre un reflet représentatif des interactions des utilisateurs, ce qui garantit une mesure fiable de l’engagement du site web en capturant le nombre de pages vues du côté client.

Pour les clients qui placent leur propre réseau de diffusion de contenu en plus des rapports as a Cloud Service côté serveur, les résultats des rapports sont des nombres qui ne peuvent pas être utilisés pour comparer avec les demandes de contenu sous licence. Avec la variable [Surveillance de l’utilisation réelle](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md), l’Adobe peut refléter une mesure fiable de l’engagement du site web.


### Écarts entre les demandes de contenu de Cloud Service {#content-requests-variances}

Les requêtes de contenu peuvent présenter des variations dans les outils de création de rapports Analytics d’une organisation, comme illustré dans le tableau suivant. En général, *ne pas* utiliser des outils analytics qui collectent des données par le biais d’une instrumentation côté client pour générer des rapports sur le nombre de demandes de contenu pour un site donné, simplement parce qu’elles dépendent souvent du consentement de l’utilisateur pour être déclenchées, ce qui fait qu’il manque une partie significative du trafic. Les outils Analytics qui collectent les données côté serveur dans les fichiers journaux ou les rapports CDN pour les clients qui ajoutent leur propre CDN en plus de l’AEM as a Cloud Service, offrent de meilleurs décomptes. Pour la création de rapports sur les pages vues et leurs performances associées, la variable [Adobe RUM Data Service](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md) est l’option recommandée pour l’Adobe.

| Raison de l’écart | Explication |
|---|---|
| Consentement des utilisateurs finaux | Les outils Analytics reposant sur l’instrumentation côté client dépendent souvent du consentement de l’utilisateur à déclencher. Cela peut représenter la majorité du trafic non suivi. Pour les clients qui souhaitent mesurer leurs requêtes de contenu par eux-mêmes, il est recommandé de s’appuyer sur les outils d’analyse qui collectent des rapports côté serveur ou sur le réseau de diffusion de contenu. |
| Balisage | Il se peut que tous les appels de page ou d’API qui sont suivis en tant que requêtes de contenu Adobe Experience Manager ne soient pas balisés avec le suivi Analytics. |
| Règles de gestion des balises | Les paramètres des règles de gestion des balises peuvent entraîner diverses configurations de collecte de données sur une page, ce qui entraîne une combinaison d’incohérences avec le suivi des demandes de contenu. |
| Robots | Les robots inconnus qui n’ont pas été préalablement identifiés et supprimés par AEM peuvent entraîner des incohérences dans le suivi. |
| Suites de rapports | Les pages qui font partie d’une même instance AEM et d’un même domaine peuvent envoyer des données à différentes suites de rapports Analytics. |
| Outils de surveillance et de sécurité tiers | Les outils de surveillance et d’analyse de sécurité peuvent générer des demandes de contenu pour AEM qui ne sont pas suivies dans les rapports Analytics. |
| Accès API | Un accès programmatique aux pages ou aux API Adobe Experience Manager peut générer des demandes de contenu pour les AEM qui ne sont pas suivies dans les rapports Analytics. |
| Pré-récupérer des demandes | L’utilisation d’un service de pré-récupération pour précharger les pages afin d’augmenter la vitesse peut entraîner une augmentation significative du trafic de demandes de contenu. |
| DDOS | Bien qu’Adobe tente de détecter et de filtrer automatiquement le trafic provenant des attaques DDOS, rien ne garantit que toutes les attaques DDOS possibles soient détectées. |
| Bloqueurs de trafic | L’utilisation d’un bloqueur de suivi dans un navigateur peut exclure certaines requêtes du suivi. |
| Pare-feux | Les pare-feu peuvent bloquer le suivi Analytics. Ce scénario est plus fréquent avec les pare-feu d’entreprise. |

Voir aussi [Tableau de bord des licences](/help/implementing/cloud-manager/license-dashboard.md).

## Règles de collecte côté serveur {#serverside-collection}

Il existe des règles pour exclure les robots les plus connus, notamment les services les plus connus qui visitent régulièrement le site pour actualiser leur index ou service de recherche.

### Types de requêtes de contenu incluses {#included-content-requests}

| Type de requête | Requête de contenu | Description |
| --- | --- | --- |
| Code HTTP 100-299 | Inclus | Il s’agit de requêtes régulières qui diffusent tout ou partie du contenu. |
| Bibliothèques HTTP pour l’automatisation | Inclus | Exemples :<br>・ Amazon CloudFront<br>・ Client Apache Http<br>・ Client Http Asynchrone<br>・ Axios<br>・ Azureus<br>・ Curl<br>・ Récupération des noeuds GitHub<br>・ Guise<br>・ Go-http-client<br>・ Chrome sans affichage<br>・ Client Java™<br>・ Jersey<br>・ Node Oembed<br>・ okhttp<br>・ Requêtes Python<br>・ Nettoyage du réacteur<br>・ Wget<br>・ WinHTTP |
| Outils de contrôle et de contrôle de l’intégrité | Inclus | Ils sont configurés par le client pour surveiller un certain aspect du site. Par exemple, la disponibilité ou les performances réelles de l’utilisateur. Utilisation `/system/probes/health` et non les pages de HTML du site.<br>Exemples :<br>・ Amazon-Route53-Health-Check-Service<br>・ EyeMonIT_bot_version_0.1_[(https://www.eyemon.it/)](https://www.eyemon.it/)<br>・ Investis-Site24x7<br>・ Mozilla/5.0+ (compatible ; UptimeRobot/2.0 ; [https://uptimerobot.com/](https://uptimerobot.com/))<br>・ ThousandEyes-Dragonfly-x1<br>・ OmtrBot/1.0<br>・ WebMon/2.0.0 |
| `<link rel="prefetch">` requests | Inclus | Pour accélérer le chargement de la page suivante, les clients peuvent demander au navigateur de charger un ensemble de pages avant que l’utilisateur ne clique sur le lien, de sorte qu’elles se trouvent déjà dans le cache. *Mind : cela augmente considérablement le trafic*: selon le nombre de ces pages prérécupérées. |
| Trafic qui bloque les rapports Adobe Analytics ou Google Analytics | Inclus | Il est plus courant que des logiciels de confidentialité (Ad-blockers, etc.) soient installés sur les visiteurs de sites pour affecter la précision des Google Analytics ou d’Adobe Analytics. AEM as a Cloud Service comptabilise les requêtes sur le premier point d’entrée de l’infrastructure exploitée par l’Adobe et non sur le côté client. |

Voir aussi [Tableau de bord des licences](/help/implementing/cloud-manager/license-dashboard.md).

### Types de requêtes de contenu exclues {#excluded-content-request}

| Type de requête | Requête de contenu | Description |
| --- | --- | --- |
| Code HTTP 500+ | Exclu | Erreurs renvoyées au visiteur lorsqu’un problème se produit sur AEM code as a Cloud Service ou personnalisé du client. |
| Code HTTP 400-499 | Exclu | Erreurs renvoyées au visiteur lorsque le contenu n’existe pas (404) ou qu’il existe d’autres problèmes liés au contenu ou aux requêtes. |
| Code HTTP 300-399 | Exclu | Il s’agit de bonnes requêtes qui vérifient si quelque chose a changé sur le serveur ou redirigent la requête vers une autre ressource. Ils ne contiennent pas de contenu, donc ils ne sont pas facturables. |
| Demandes allant à /libs/* | Exclu | AEM les requêtes JSON internes, telles que le jeton CSRF non facturable. |
| Trafic provenant des attaques DOS | Exclu | Protection DDOS. AEM détecte automatiquement certaines attaques DOS et les bloque. Si des attaques DOS sont détectées, elles ne sont pas facturables. |
| Surveillance New Relic as a Cloud Service AEM | Exclu | AEM surveillance mondiale as a Cloud Service. |
| URL permettant aux clients de surveiller leur programme de Cloud Service | Exclu | URL recommandée pour surveiller la disponibilité en externe.<br><br>`/system/probes/health` |
| AEM service de réchauffement de la capsule as a Cloud Service | Exclu |
| Agent : skyline-service-chauffe/1.* |
| Moteurs de recherche, réseaux sociaux et bibliothèques HTTP (balisés Fastly) connus | Exclu | Services connus qui visitent régulièrement le site pour actualiser leur index ou service de recherche :<br><br>Exemples :<br>・ AddSearchBot<br>・ AhrefsBot<br>・ Applebot<br>・ Poser des questions à l’araignée d’entreprise à Jeeves<br>・ Bingbot<br>・ BingPreview<br>・ BLEXBot<br>・ builtWith<br>・ Bytespider<br>・ CrawlerKengo<br>・ Facebook externalhit<br>・ Google AdsBot<br>・ Google AdsBot Mobile<br>・ Googlebot<br>・ Googlebot Mobile<br>・ lmspider<br>・ LucidWorks<br>・ MJ12bot<br>・ Pingdom<br>・ Pinterest<br>・ SemrushBot<br>・ SiteAméliorer<br>・ StashBot<br>・ StatusCake<br>・ YandexBot |
| Exclusion des appels de Commerce integration framework | Exclu | Il s’agit de requêtes envoyées à AEM qui sont transférées au Commerce integration framework : l’URL commence par `/api/graphql`—pour éviter le double comptage, ils ne sont pas facturables au Cloud Service. |
| Exclure `manifest.json` | Exclu | Le manifeste n’est pas un appel API, il fournit des informations sur la manière d’installer des sites web sur un ordinateur ou un téléphone mobile. Adobe ne doit pas comptabiliser la requête JSON à `/etc.clientlibs/*/manifest.json` |
| Exclure `favicon.ico` | Exclu | Bien que le contenu renvoyé ne doive pas être HTML ou JSON, nous observons que, dans certains cas, comme les flux d’authentification SAML, les favicons peuvent être renvoyées en tant que HTML, par conséquent, sont explicitement exclues du décompte. |
