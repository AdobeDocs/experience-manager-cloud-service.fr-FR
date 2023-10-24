---
title: Compréhension des requêtes de contenu Cloud Service
description: Si vous avez acheté des licences de demande de contenu à Adobe, découvrez les types de demandes de contenu que Adobe Experience Cloud as a Service mesure et les écarts avec les outils de création de rapports d’analyse d’une entreprise.
source-git-commit: e34b21194e35b2f56dd1e7df2165c3fa5c0cb7da
workflow-type: tm+mt
source-wordcount: '1171'
ht-degree: 12%

---


# Demandes de contenu Cloud Service

## Écarts entre les demandes de contenu de Cloud Service{#content-requests-variances}

Les requêtes de contenu peuvent présenter des écarts avec les outils de création de rapports Analytics d’une organisation, comme illustré dans le tableau suivant. En général, les outils Analytics collectent des données par le biais d’une instrumentation côté client. <b>ne doit pas être utilisé</b> pour signaler le nombre de demandes de contenu pour un site donné, simplement parce qu’elles dépendent souvent du consentement de l’utilisateur final pour être déclenchées, ce qui fait défaut à une fraction significative du trafic. Les outils Analytics qui collectent les données côté serveur dans les fichiers journaux ou les rapports CDN pour les clients qui ajoutent leur propre CDN en plus de l’AEM as a Cloud Service, offrent de meilleurs décomptes. Pour la création de rapports sur les pages vues et leurs performances associées, le service de données Adobe RUM est l’option recommandée pour les Adobes.

| Raison de l’écart | Explication |
|---|---|
| Consentement des utilisateurs finaux | Les outils Analytics reposant sur l’instrumentation côté client dépendent souvent du consentement de l’utilisateur final à déclencher. Cela peut représenter la majorité du trafic non suivi. Pour les clients qui souhaitent mesurer leurs requêtes de contenu par eux-mêmes, il est recommandé de s’appuyer sur les outils d’analyse qui collectent des rapports côté serveur ou sur le réseau de diffusion de contenu. |
| Balisage | Il se peut que tous les appels de page ou d’API qui sont suivis en tant que requêtes de contenu Adobe Experience Manager (AEM) ne soient pas balisés avec le suivi Analytics. |
| Règles de gestion des balises | Les paramètres des règles de gestion des balises peuvent entraîner diverses configurations de collecte de données sur une page, ce qui entraîne une combinaison d’incohérences avec le suivi des demandes de contenu. |
| Robots | Les robots inconnus qui n’ont pas été préalablement identifiés et supprimés par AEM peuvent entraîner des incohérences dans le suivi. |
| Suites de rapports | Les pages qui font partie d’une même instance AEM et d’un même domaine peuvent envoyer des données à différentes suites de rapports Analytics. |
| Outils de surveillance et de sécurité tiers | Les outils de surveillance et d’analyse de sécurité peuvent générer des demandes de contenu pour AEM qui ne sont pas suivies dans les rapports Analytics. |
| Accès API | Un accès programmatique aux pages ou aux API Adobe Experience Manager peut générer des demandes de contenu pour les AEM qui ne sont pas suivies dans les rapports Analytics. |
| Pré-récupérer des demandes | L’utilisation d’un service de pré-récupération pour précharger les pages afin d’augmenter la vitesse peut entraîner une augmentation significative du trafic de demandes de contenu. |
| DDOS | Bien qu’Adobe s’efforce de détecter et de filtrer automatiquement le trafic provenant des attaques DDOS, il n’existe aucune garantie que toutes les attaques DDOS possibles soient détectées |
| Bloqueurs de trafic | L’utilisation d’un bloqueur de suivi dans un navigateur peut exclure certaines requêtes du suivi. |
| Pare-feux | Les pare-feu peuvent bloquer le suivi Analytics. Ce scénario est plus fréquent avec les pare-feu d’entreprise. |

Voir aussi [Tableau de bord des licences](/help/implementing/cloud-manager/license-dashboard.md).

## Compréhension des requêtes de contenu Cloud Service {#about-content-request}

Les demandes de contenu sont automatiquement suivies en périphérie de Adobe Experience Manager (AEM) as a Cloud Service, par le biais d’une analyse automatisée des fichiers journaux provenant du réseau de diffusion de contenu as a Cloud Service AEM, isolant les demandes renvoyant le contenu du HTML (texte/html) ou JSON (application/json) du réseau de diffusion de contenu, et en fonction d’un certain nombre de règles d’inclusion et d’exclusion détaillées ci-dessous. Une demande de contenu se produit indépendamment du contenu renvoyé qui est diffusé à partir des caches CDN ou en revenant à l’origine du CDN (AEM dispatchers).

Pour les clients qui placent leur propre réseau de diffusion de contenu au-dessus d’AEM as a Cloud Service, ce suivi se traduira par des nombres qui ne peuvent pas être utilisés à des fins de comparaison avec les demandes de contenu sous licence, qui devront être mesurées par le client à la périphérie du réseau de diffusion de contenu externe.

Il existe des règles pour exclure les robots les plus connus, notamment les services les plus connus qui visitent régulièrement le site pour actualiser leur index ou service de recherche.

### Types de requêtes de contenu incluses{#included-content-requests}

| Type de requête | Requête de contenu | Description |
| --- | --- | --- |
| Code HTTP 100-299 | Inclus | Il s’agit de requêtes régulières qui diffusent tout ou partie du contenu. |
| Bibliothèques HTTP pour l’automatisation | Inclus | Exemples :<br>・ Amazon CloudFront<br>・ Client Apache Http<br>・ Client Http Asynchrone<br>・ Axios<br>・ Azureus<br>・ Curl<br>・ Récupération des noeuds GitHub<br>・ Guise<br>・ Go-http-client<br>・ Chrome sans affichage<br>・ Client Java™<br>・ Jersey<br>・ Node Oembed<br>・ okhttp<br>・ Requêtes Python<br>・ Nettoyage du réacteur<br>・ Wget<br>・ WinHTTP |
| Outils de contrôle et de contrôle de l’intégrité | Inclus | Ils sont configurés par le client pour surveiller un certain aspect du site. Par exemple, la disponibilité ou les performances réelles de l’utilisateur. Utilisation `/system/probes/health` et non les pages de HTML du site.<br>Exemples :<br>・ Amazon-Route53-Health-Check-Service<br>・ EyeMonIT_bot_version_0.1_[(https://www.eyemon.it/)](https://www.eyemon.it/)<br>・ Investis-Site24x7<br>・ Mozilla/5.0+ (compatible ; UptimeRobot/2.0 ; [https://uptimerobot.com/](https://uptimerobot.com/))<br>・ ThousandEyes-Dragonfly-x1<br>・ OmtrBot/1.0<br>・ WebMon/2.0.0 |
| `<link rel="prefetch">` requests | Inclus | Pour accélérer le chargement de la page suivante, les clients peuvent demander au navigateur de charger un ensemble de pages avant que l’utilisateur ne clique sur le lien, de sorte qu’elles se trouvent déjà dans le cache. *Mind : cela augmente considérablement le trafic*: selon le nombre de ces pages prérécupérées. |
| Trafic qui bloque les rapports Adobe Analytics ou Google Analytics | Inclus | Il est plus courant que des logiciels de confidentialité (Ad-blockers, etc.) soient installés sur les visiteurs de sites pour affecter la précision des Google Analytics ou d’Adobe Analytics. AEM as a Cloud Service comptabilise les requêtes sur le premier point d’entrée de l’infrastructure exploitée par l’Adobe et non sur le côté client. |

Voir aussi [Tableau de bord des licences](/help/implementing/cloud-manager/license-dashboard.md).

### Types de requêtes de contenu exclues{#excluded-content-request}

| Type de requête | Requête de contenu | Description |
| --- | --- | --- |
| Code HTTP 500+ | Exclu | Erreurs renvoyées au visiteur lorsqu’un problème se produit sur AEM code as a Cloud Service ou personnalisé du client. |
| Code HTTP 400-499 | Exclu | Erreurs renvoyées au visiteur lorsque le contenu n’existe pas (404) ou qu’il existe d’autres problèmes liés au contenu ou aux requêtes. |
| Code HTTP 300-399 | Exclu | Il s’agit de bonnes requêtes qui vérifient si quelque chose a changé sur le serveur ou redirigent la requête vers une autre ressource. Ils ne contiennent pas de contenu, donc ils ne sont pas facturables. |
| Demandes allant à /libs/* | Exclu | AEM les requêtes JSON internes, telles que le jeton CSRF non facturable. |
| Trafic provenant des attaques DOS | Exclu | Protection DDOS. AEM détecte automatiquement certaines attaques DOS et les bloque. Si des attaques DOS sont détectées, elles ne sont pas facturables.<br><br>Types de DDOS détectés automatiquement :<br>・ DOSBlockedCiphersSHA<br>・ DOSBlockedPattern<br>・ DDOSSuspiciousRequest |
| AEM surveillance NewRelic as a Cloud Service | Exclu | AEM surveillance mondiale as a Cloud Service. |
| URL permettant aux clients de surveiller leur programme de Cloud Service | Exclu | URL recommandée pour surveiller la disponibilité en externe.<br><br>`/system/probes/health` |
| AEM service de réchauffement de la capsule as a Cloud Service | Exclu | Agent utilisateur : skyline-service-chauffe/1.* |
| Moteurs de recherche, réseaux sociaux et bibliothèques HTTP (balisés Fastly) connus | Exclu | Services connus qui visitent régulièrement le site pour actualiser leur index ou service de recherche :<br><br>Exemples :<br>・ AddSearchBot<br>・ AhrefsBot<br>・ Applebot<br>・ Poser des questions à l’araignée d’entreprise à Jeeves<br>・ Bingbot<br>・ BingPreview<br>・ BLEXBot<br>・ builtWith<br>・ Bytespider<br>・ CrawlerKengo<br>・ Facebook externalhit<br>・ Google AdsBot<br>・ Google AdsBot Mobile<br>・ Googlebot<br>・ Googlebot Mobile<br>・ lmspider<br>・ LucidWorks<br>・ MJ12bot<br>・ Pingdom<br>・ Pinterest<br>・ SemrushBot<br>・ SiteAméliorer<br>・ StashBot<br>・ StatusCake<br>・ YandexBot |
| Exclusion des appels de Commerce integration framework | Exclu | Il s’agit de requêtes envoyées à AEM qui sont transférées au Commerce integration framework : l’URL commence par `/api/graphql`—pour éviter le double comptage, ils ne sont pas facturables au Cloud Service. |
| Exclure `manifest.json` | Exclu | Le manifeste n’est pas un appel API, il fournit des informations sur la manière d’installer des sites web sur un ordinateur ou un téléphone mobile. Adobe ne doit pas comptabiliser la requête JSON à `/etc.clientlibs/*/manifest.json` |
| Exclure `favicon.ico` | Exclu | Bien que le contenu renvoyé ne doive pas être HTML ou JSON, nous observons que, dans certains cas, comme les flux d’authentification SAML, les favicons peuvent être renvoyées en tant que HTML, par conséquent, sont explicitement exclues du décompte. |


