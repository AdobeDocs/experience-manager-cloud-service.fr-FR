---
title: Comprendre les requêtes de contenu Cloud Service
description: Si vous avez acheté des licences de demande de contenu auprès d’Adobe, découvrez les types de demandes de contenu que Adobe Experience Cloud as a Service mesure et les écarts avec les outils de création de rapports Analytics d’une organisation.
exl-id: 3666328a-79a7-4dd7-b952-38bb60f0967d
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f57d90078b5fc0e0c8a79ca60cbc19e7b37323cd
workflow-type: tm+mt
source-wordcount: '1250'
ht-degree: 9%

---

# Comprendre les demandes de contenu de Cloud Service

## Présentation {#introduction}

Les demandes de contenu font référence aux demandes adressées à AEM Sites, y compris les demandes liées aux Edge Delivery Services ou aux systèmes de mise en cache fournis par le client, tels qu’un réseau de diffusion de contenu. Ces requêtes diffusent du contenu ou des données au format HTML par le biais de pages vues (par exemple, des pages et des fragments d’expérience) ou au format JSON par le biais d’appels d’API de manière découplée. Les requêtes de contenu sont comptées comme une page vue ou cinq appels d’API et sont mesurées à l’entrée du premier système de mise en cache à recevoir une requête de contenu. Certaines requêtes HTTP sont incluses ou exclues à des fins de comptage des requêtes de contenu. La liste complète de ces requêtes HTTP incluses et exclues, ainsi que leurs définitions techniques, sont disponibles dans la documentation de .

## À propos des demandes de contenu de Cloud Service {#understanding-cloud-service-content-requests}

Pour les clients qui utilisent le réseau CDN prêt à l’emploi, les demandes de contenu du Cloud Service sont mesurées via la collecte de données côté serveur. Cette collection est activée via l’analyse du journal du réseau CDN. AEM (Adobe Experience Manager as a Cloud Service) collecte automatiquement les demandes de contenu côté serveur à la périphérie. Il analyse les fichiers journaux générés par le réseau CDN d’AEM as a Cloud Service. Ce processus est effectué en isolant les requêtes qui renvoient du contenu de `(application/json)` JSON ou `(text/html)` d’HTML du réseau CDN et repose sur plusieurs règles d’inclusion et d’exclusion détaillées ci-dessous. Une demande de contenu se produit que le contenu soit diffusé à partir des caches du réseau CDN ou renvoyé à l’origine du réseau CDN (Dispatchers AEM).

<!-- REMOVED AS PER EMAIL REQUEST FROM SHWETA DUA, JULY 30, 2024 TO RICK BROUGH AND ALEXANDRU SARCHIZ   For customers employing their own CDN, client-side collection offers a more precise reflection of interactions, ensuring a reliable measure of website engagement via the [Real Use Monitoring](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md) service. This gives customers advanced insights into their page traffic and performance. While it is beneficial for all customers, it offers a representative reflection of user interactions, ensuring a reliable measure of website engagement by capturing the number of page views from the client side. 

For customers that bring their own CDN on top of AEM as a Cloud Service, server-side reporting results in numbers that cannot be used to compare with the licensed content requests. With the [Real Use Monitoring](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md), Adobe can reflect a reliable measure of website engagement. -->

### Variances des demandes de contenu du Cloud Service {#content-requests-variances}

Les requêtes de contenu peuvent présenter des variations au sein des outils de création de rapports Analytics d’une organisation, comme résumé dans le tableau suivant. En règle générale, évitez d’utiliser des outils d’analyse qui reposent sur une instrumentation côté client pour signaler le nombre de demandes de contenu pour un site. Ces outils manquent souvent une grande partie du trafic, car leur activation dépend du consentement de l’utilisateur. Les outils Analytics qui collectent des données côté serveur dans les fichiers journaux, ou les rapports de réseau CDN pour les clients qui ajoutent leur propre réseau CDN en plus d’AEM as a Cloud Service, fournissent de meilleurs chiffres.

| Raison de l’écart | Explication |
|---|---|
| Consentement de l’utilisateur final | Le déclenchement des outils Analytics qui reposent sur une instrumentation côté client dépend souvent du consentement de l’utilisateur. Ce workflow peut représenter la majorité du trafic non suivi. Pour les clients qui souhaitent mesurer eux-mêmes les demandes de contenu, il est recommandé de s’appuyer sur les outils d’analyse collectant des rapports de données côté serveur ou sur le réseau CDN. |
| Balisage | Toutes les pages ou appels d’API qui font l’objet d’un suivi sous forme de demandes de contenu Adobe Experience Manager peuvent ne pas être balisés avec le suivi Analytics. |
| Règles de gestion des balises | Les paramètres des règles de gestion des balises peuvent entraîner diverses configurations de collecte de données sur une page, ce qui entraîne une combinaison d’incohérences avec le suivi des demandes de contenu. |
| Robots | Les robots inconnus qu’AEM n’a pas pré-identifiés et supprimés peuvent entraîner des incohérences dans le suivi. |
| Suites de rapports | Les pages qui font partie d’une même instance AEM et d’un même domaine peuvent envoyer des données à différentes suites de rapports Analytics. |
| Outils de surveillance et de sécurité tiers | Les outils de surveillance et d’analyse de sécurité peuvent générer des demandes de contenu pour AEM qui ne sont pas suivies dans les rapports Analytics. |
| Accès à l’API | L’accès par programmation aux pages ou aux API Adobe Experience Manager peut générer des demandes de contenu pour AEM qui ne sont pas suivies dans les rapports Analytics. |
| Pré-récupérer des demandes | L’utilisation d’un service de pré-récupération pour précharger les pages afin d’augmenter la vitesse peut entraîner une augmentation significative du trafic de demandes de contenu. |
| DDOS | Bien qu’Adobe tente de détecter et de filtrer automatiquement le trafic provenant des attaques DDOS, il n’existe aucune garantie que toutes les attaques DDOS possibles sont détectées. |
| Bloqueurs de trafic | L’utilisation d’un bloqueur de suivi dans un navigateur peut exclure certaines requêtes du suivi. |
| Pare-feux | Les pare-feu peuvent bloquer le suivi Analytics. Ce scénario est plus fréquent avec les pare-feu d’entreprise. |

Voir aussi [Tableau de bord des licences](/help/implementing/cloud-manager/license-dashboard.md).

## Règles de collecte côté serveur {#serverside-collection}

Des règles sont en place pour exclure les robots connus, notamment les services connus qui visitent régulièrement le site pour actualiser leur index ou service de recherche.

### Types de demandes de contenu incluses {#included-content-requests}

| Type de demande | Demande de contenu | Description |
| --- | --- | --- |
| Code HTTP 100-299 | Inclus | Requêtes régulières qui diffusent l’intégralité ou une partie du contenu. |
| Bibliothèques HTTP à automatiser | Inclus | Exemples :<br>· Amazon CloudFront<br>· Client Apache Http<br>· Client HTTP asynchrone<br>· Axios<br>· Azureus<br>· Curl<br>· Récupération de nœud GitHub<br>· Guzzle<br>· Go-http-client<br>· Chrome découplé<br>· Client Java™· Jersey<br>· Node Oembed<br>· okhttp<br>· Requêtes Python<br>· Reactor Netty<br>· Wget<br>· WinHTTP<br>· Fast HTTP<br>· GitHub Node Fetch<br> <br>· Reactor Netty |
| Outils de surveillance et de contrôle de l’intégrité | Inclus | Paramétré par le client pour surveiller un certain aspect du site. Par exemple, la disponibilité ou les performances réelles de l’utilisateur. S’ils ciblent des points d’entrée spécifiques, tels que `/system/probes/health` pour les contrôles d’intégrité, Adobe vous recommande d’utiliser `/system/probes/health` point d’entrée et non les pages d’HTML réelles du site. [Voir ci-dessous](#excluded-content-request)<br>Exemples :<br>· `Amazon-Route53-Health-Check-Service`<br>· EyeMonIT_bot_version_0.1_[(https://eyemonit.com/)](https://eyemonit.com/)<br>· Investis-Site24x7<br>· Mozilla/5.0+(compatible ; UptimeRobot/2.0 ; [https://uptimerobot.com/](https://uptimerobot.com/))<br>· ThousandEyes-Dragonfly-x1<br>· OmtrBot/1.0<br>· WebMon/2.0.0 |
| `<link rel="prefetch">` requêtes | Inclus | Pour accélérer le chargement de la page suivante, le navigateur peut charger un ensemble de pages avant que l’utilisateur ne clique sur le lien, de sorte qu’il se trouve déjà dans le cache. *Remarque : cette approche augmente considérablement le trafic* selon le nombre de ces pages prérécupérées. |
| Trafic qui bloque le reporting d’Adobe Analytics ou des Google Analytics | Inclus | Il est plus courant que les visiteurs des sites disposent de logiciels de protection des données personnelles installés (bloqueurs de publicités, etc.) qui affectent la précision des Google Analytics ou d’Adobe Analytics. AEM as a Cloud Service comptabilise les requêtes sur le premier point d’entrée de l’infrastructure gérée par l’Adobe et non du côté client. |

Voir aussi [Tableau de bord des licences](/help/implementing/cloud-manager/license-dashboard.md).

### Types de demandes de contenu exclues {#excluded-content-request}

| Type de demande | Demande de contenu | Description |
| --- | --- | --- |
| Code HTTP 500+ | Exclu | Erreurs renvoyées au visiteur lorsqu’un problème se produit sur AEM as a Cloud Service ou dans le code personnalisé du client. |
| Code HTTP 400-499 | Exclu | Erreurs renvoyées au visiteur lorsque le contenu n’existe pas (404) ou qu’il existe d’autres problèmes liés au contenu ou aux requêtes. |
| Code HTTP 300-399 | Exclu | Bonnes requêtes permettant de vérifier si quelque chose a changé sur le serveur ou de rediriger la requête vers une autre ressource. Ils ne contiennent pas de contenu lui-même et ne sont donc pas facturables. |
| Demandes allant dans /libs/* | Exclu | Requêtes JSON internes AEM, telles que le jeton CSRF qui n’est pas facturable. |
| Trafic provenant d’attaques DDOS | Exclu | Protection DDOS. AEM détecte automatiquement certaines des attaques DDOS et les bloque. Les attaques DDOS détectées ne sont pas facturables. |
| Surveillance d’AEM as a Cloud Service New Relic | Exclu | Surveillance globale d’AEM as a Cloud Service. |
| URL permettant aux clients de surveiller leur programme de Cloud Service | Exclu | Adobe recommande d’utiliser l’URL pour surveiller la disponibilité ou le contrôle d’intégrité en externe.<br><br>`/system/probes/health` |
| Service de préchauffage de capsule AEM as a Cloud Service | Exclu |
| Agent : skyline-service-préchauffage/1.* |
| Moteurs de recherche connus, réseaux sociaux et bibliothèques HTTP (avec le tag Fastly) | Exclu | Services connus visitant régulièrement le site pour actualiser leur index ou service de recherche :<br><br>Exemples :<br>· AddSearchBot<br>· AhrefsBot<br>· Applebot<br>· Ask Jeeves Corporate Spider<br>· Bingbot<br>· BingPreview<br>· BLEXBot<br>· BuiltWith<br>· Bytespider<br>· CrawlerKengo<br>· Facebookexternalhit<br>· Google AdsBot<br>· Google AdsBot Mobile<br>· Googlebot<br>· Googlebot Mobile<br> lmspider<br>· LucidWorks<br>· Pinterest`MJ12bot`<br>· SemrushBot<br>· SiteImprov<br>· StashBot<br>· StatusCake<br>· YandexBot<br>· ContentKing<br> <br>· Claudebot |
| Exclure les appels de Commerce integration framework | Exclu | Les demandes envoyées à AEM qui sont transférées vers le Commerce integration framework (l’URL commence par `/api/graphql`) ne sont pas facturables pour le Cloud Service afin d’éviter un double comptage. |
| Exclure le `manifest.json` | Exclu | Le manifeste n’est pas un appel API. Il permet de fournir des informations sur la manière d’installer des sites web sur un ordinateur ou un téléphone mobile. L’Adobe ne doit pas compter les requêtes JSON à `/etc.clientlibs/*/manifest.json` |
| Exclure le `favicon.ico` | Exclu | Bien que le contenu renvoyé ne doive pas être HTML ou JSON, il a été observé que certains scénarios tels que les flux d’authentification SAML renvoient des favicons en tant qu’HTML. Par conséquent, les favicons sont explicitement exclus du décompte. |
