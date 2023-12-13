---
title: Compréhension des requêtes de contenu Cloud Service
description: Si vous avez acheté des licences de demande de contenu à Adobe, découvrez les types de demandes de contenu que Adobe Experience Cloud as a Service mesure et les écarts avec les outils de création de rapports d’analyse d’une entreprise.
exl-id: 3666328a-79a7-4dd7-b952-38bb60f0967d
source-git-commit: e31b05f0cef6c5ca3a1c00b757eac013aa43bb90
workflow-type: tm+mt
source-wordcount: '2690'
ht-degree: 4%

---

# Demandes de contenu Cloud Service

## Présentation {#introduction}

Les demandes de contenu de Cloud Service sont mesurées par le biais d’une collecte de données côté serveur. La collection est activée via l’analyse des journaux CDN.

>[!NOTE]
>En outre, pour un nombre limité de [Clients Adopteurs anticipés](/help/release-notes/release-notes-cloud/release-notes-current.md#sites-early-adopter), la collecte côté client sera également activée via la mesure RUM (surveillance des utilisateurs réels). Pour en savoir plus, consultez la documentation de la section [cet article](#real-user-monitoring-for-aem-as-a-cloud-service).

## Compréhension des requêtes de contenu Cloud Service {#understaing-cloud-service-content-requests}

Les demandes de contenu sont automatiquement collectées côté serveur à la périphérie d’Adobe Experience Manager as a Cloud Service, via une analyse automatisée des fichiers journaux provenant du réseau de diffusion de contenu as a Cloud Service AEM. Pour ce faire, isolez le HTML de renvoi des demandes. `(text/html)` ou JSON `(application /Json)` contenu du réseau de diffusion de contenu, et selon plusieurs règles d’inclusion et d’exclusion détaillées ci-dessous. Une demande de contenu se produit indépendamment du contenu renvoyé qui est diffusé à partir des caches CDN ou du contenu qui retourne à l’origine du CDN (AEM dispatchers).

Le service de données de surveillance des utilisateurs réels (RUM), la collection côté client, offre un reflet plus précis des interactions utilisateur, assurant une mesure fiable de l’engagement du site web. Les clients disposent ainsi d’informations avancées sur le trafic et les performances de leurs pages. Bien que cela soit bénéfique pour les clients qui utilisent le réseau de diffusion de contenu géré par Adobe ou un réseau de diffusion de contenu géré par non Adobe. En outre, la création de rapports de trafic automatique peut désormais être activée pour les clients qui utilisent un réseau de diffusion de contenu géré par un autre Adobe, ce qui évite d’avoir à partager les rapports de trafic avec Adobe.

Pour les clients qui placent leur propre réseau de diffusion de contenu en plus des rapports as a Cloud Service côté serveur, les nombres ne peuvent pas être utilisés pour comparer les demandes de contenu sous licence. Ces chiffres devront être mesurés par le client au bord du réseau de diffusion de contenu externe. Pour ces clients, la création de rapports côté client et les performances associées, la variable [Adobe RUM Data Service](#real-user-monitoring-for-aem-as-a-cloud-service) est l’option recommandée pour l’Adobe. Voir [notes de mise à jour](/help/release-notes/release-notes-cloud/release-notes-current.md#sites-early-adopter) pour obtenir des informations sur la manière de souscrire.

## Collection côté serveur {#serverside-collection}

Il existe des règles pour exclure les robots les plus connus, notamment les services les plus connus qui visitent régulièrement le site pour actualiser leur index ou service de recherche.

### Écarts entre les demandes de contenu de Cloud Service {#content-requests-variances}

Les requêtes de contenu peuvent présenter des écarts avec les outils de création de rapports Analytics d’une organisation, comme illustré dans le tableau suivant. En général, *ne pas* utiliser des outils analytics qui collectent des données au moyen d’une instrumentation côté client pour générer des rapports sur le nombre de demandes de contenu pour un site donné, simplement parce qu’elles dépendent souvent du consentement de l’utilisateur pour être déclenchées, ce qui fait qu’elles ne couvrent qu’une partie significative du trafic. Les outils Analytics qui collectent les données côté serveur dans les fichiers journaux ou les rapports CDN pour les clients qui ajoutent leur propre CDN en plus de l’AEM as a Cloud Service, offrent de meilleurs décomptes. Pour la création de rapports sur les pages vues et leurs performances associées, le service de données Adobe RUM est l’option recommandée par Adobe.

| Raison de l’écart | Explication |
|---|---|
| Consentement des utilisateurs finaux | Les outils Analytics reposant sur l’instrumentation côté client dépendent souvent du consentement de l’utilisateur à déclencher. Cela peut représenter la majorité du trafic non suivi. Pour les clients qui souhaitent mesurer leurs requêtes de contenu par eux-mêmes, il est recommandé de s’appuyer sur les outils d’analyse qui collectent des rapports côté serveur ou sur le réseau de diffusion de contenu. |
| Balisage | Il se peut que tous les appels de page ou d’API qui sont suivis en tant que requêtes de contenu Adobe Experience Manager (AEM) ne soient pas balisés avec le suivi Analytics. |
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
| AEM surveillance NewRelic as a Cloud Service | Exclu | AEM surveillance mondiale as a Cloud Service. |
| URL permettant aux clients de surveiller leur programme de Cloud Service | Exclu | URL recommandée pour surveiller la disponibilité en externe.<br><br>`/system/probes/health` |
| AEM service de réchauffement de la capsule as a Cloud Service | Exclu | Agent utilisateur : skyline-service-chauffe/1.* |
| Moteurs de recherche, réseaux sociaux et bibliothèques HTTP (balisés Fastly) connus | Exclu | Services connus qui visitent régulièrement le site pour actualiser leur index ou service de recherche :<br><br>Exemples :<br>・ AddSearchBot<br>・ AhrefsBot<br>・ Applebot<br>・ Poser des questions à l’araignée d’entreprise à Jeeves<br>・ Bingbot<br>・ BingPreview<br>・ BLEXBot<br>・ builtWith<br>・ Bytespider<br>・ CrawlerKengo<br>・ Facebook externalhit<br>・ Google AdsBot<br>・ Google AdsBot Mobile<br>・ Googlebot<br>・ Googlebot Mobile<br>・ lmspider<br>・ LucidWorks<br>・ MJ12bot<br>・ Pingdom<br>・ Pinterest<br>・ SemrushBot<br>・ SiteAméliorer<br>・ StashBot<br>・ StatusCake<br>・ YandexBot |
| Exclusion des appels de Commerce integration framework | Exclu | Il s’agit de requêtes envoyées à AEM qui sont transférées au Commerce integration framework : l’URL commence par `/api/graphql`—pour éviter le double comptage, ils ne sont pas facturables au Cloud Service. |
| Exclure `manifest.json` | Exclu | Le manifeste n’est pas un appel API, il fournit des informations sur la manière d’installer des sites web sur un ordinateur ou un téléphone mobile. Adobe ne doit pas comptabiliser la requête JSON à `/etc.clientlibs/*/manifest.json` |
| Exclure `favicon.ico` | Exclu | Bien que le contenu renvoyé ne doive pas être HTML ou JSON, nous observons que, dans certains cas, comme les flux d’authentification SAML, les favicons peuvent être renvoyées en tant que HTML, par conséquent, sont explicitement exclues du décompte. |

## Collection côté client {#cliendside-collection}

### Surveillance des utilisateurs réels (RUM) pour AEM as a Cloud Service {#real-user-monitoring-for-aem-as-a-cloud-service}

>[!INFO]
>
>Cette fonction est uniquement disponible pour le programme des premiers adopteurs.
>Vous devez utiliser la version AEM Cloud Service **2023.11.14227** et au-dessus afin d’activer le service de données RUM.

### Vue d’ensemble {#overview}

La surveillance des utilisateurs réels (RUM) est un type de technologie de surveillance des performances qui capture et analyse en temps réel les expériences utilisateur numériques d’un site web ou d’une application. Il offre une visibilité sur les performances en temps réel d’une application web et fournit des informations précises sur l’expérience de l’utilisateur final.

La surveillance des utilisateurs réels (RUM) fournit des informations détaillées sur les principales mesures de performances, depuis le lancement de l’URL jusqu’à ce que la demande soit renvoyée au navigateur. Cela aide les développeurs à améliorer l’application afin qu’elle soit facile à utiliser pour les utilisateurs finaux.

### Qui peut bénéficier du service de surveillance des données RUM ? {#who-can-benefit-from-rum-data-monitoring-service}

Le service de données RUM est bénéfique pour ceux qui utilisent le réseau de diffusion de contenu d’Adobe, car il offre un reflet plus précis des interactions utilisateur, ce qui garantit une mesure fiable de l’engagement du site web en reflétant le nombre de pages vues côté client qui peuvent être comparées aux pages vues du journal de contenu côté serveur existantes. En outre, pour les clients qui utilisent leur propre réseau de diffusion de contenu, Adobe peut désormais rationaliser la création de rapports de trafic automatique qui inclut les pages vues pour eux, ce qui signifie qu’ils n’ont pas à partager de rapport de trafic avec Adobe.

C’est également une excellente opportunité d’obtenir des informations avancées sur les performances de votre page pour les clients qui utilisent le réseau de diffusion de contenu d’Adobe et ceux qui utilisent leur propre réseau de diffusion de contenu.

### Comprendre le fonctionnement du service de données Real User Monitoring (RUM) {#understand-how-the-rum-data-service-works}

Adobe Experience Manager utilise la surveillance des utilisateurs réels (RUM) pour aider les clients et les Adobes à comprendre la manière dont les visiteurs interagissent avec les sites utilisant Adobe Experience Manager, à diagnostiquer les problèmes de performances et à mesurer l’efficacité des expériences. RUM protège la confidentialité des visiteurs par échantillonnage (seule une petite partie de toutes les pages vues sera surveillée) et une exclusion judicieuse de toutes les informations d’identification personnelle (PII).

### Surveillance des utilisateurs réels (RUM) et confidentialité {#rum-and-privacy}

La surveillance des utilisateurs réels dans Adobe Experience Manager est conçue pour préserver la confidentialité des visiteurs et minimiser la collecte de données. En tant que visiteur, cela signifie qu’aucune information personnelle ne sera collectée par le site que vous visitez ou mise à disposition de l’Adobe.

En tant qu’opérateur de site, cela signifie qu’aucun opt-in supplémentaire n’est nécessaire pour activer la surveillance par le biais de cette fonctionnalité. Par conséquent, il n’y aura pas de pop-up supplémentaire que les utilisateurs finaux pourront accepter pour activer la surveillance RUM.

### Etapes des données RUM {#rum-data-sampling}

Les solutions d’analyse web traditionnelles tentent de collecter des données sur chaque visiteur. La surveillance des utilisateurs réels de Adobe Experience Manager ne capture que les informations provenant d’une petite fraction des pages vues. La surveillance des utilisateurs réels (RUM) est destinée à être échantillonnée et rendue anonyme plutôt qu’un remplacement pour les analyses. Par défaut, le ratio d’échantillonnage des pages est de 1:100. Les opérateurs du site ne peuvent pas configurer ce nombre pour augmenter ou diminuer le taux d&#39;échantillonnage à ce jour. Pour estimer précisément le trafic total, nous rassemblons des données détaillées d’une seule page pour chaque centaine de pages vues, ce qui vous permet d’approximer de manière fiable le trafic global.&quot;

Comme la décision de collecter les données est prise sur une page vue par page, il devient pratiquement impossible de suivre les interactions sur plusieurs pages. RUM n’a aucun concept de visites, de visiteurs ou de sessions, uniquement des pages vues. C&#39;est par conception.

### Données en cours de collecte {#what-data-is-being-collected}

La surveillance des utilisateurs réels (RUM) est conçue pour empêcher la collecte d’informations d’identification personnelle. L’ensemble complet des informations pouvant être collectées par la surveillance des utilisateurs réels de Adobe Experience Manager est répertorié ci-dessous :

* Nom d’hôte du site visité, par exemple : `experienceleague.adobe.com`
* Type d’agent utilisateur large utilisé pour afficher la page, par exemple : bureau ou mobile
* Heure de la collecte des données, par exemple : `2021-06-26 06:00:02.596000 UTC (in order to preserve privacy, we round all minutes to the previous hour, so that only seconds and milliseconds are tracked)`
* URL de la page visitée, par exemple : `https://experienceleague.adobe.com/docs`
* URL du référent (URL de la page qui a lié à la page active, si l’utilisateur a suivi un lien)
* Identifiant généré de manière aléatoire de la page vue, dans un format similaire à : `2Ac6`
* Le poids ou l’inverse du taux d’échantillonnage, par exemple : `100`. Cela signifie que seulement une page vue sur cent sera enregistrée.
* Point de contrôle ou nom d’un événement particulier dans la séquence de chargement de la page ou d’interaction avec lui en tant que visiteur
* Source, ou identifiant de l’élément DOM avec lequel l’utilisateur interagit pour le point de contrôle mentionné ci-dessus. Par exemple, il peut s’agir d’une image.
* La cible, ou le lien vers une page ou une ressource externe avec laquelle l’utilisateur interagit pour le point de contrôle mentionné ci-dessus. Par exemple : `https://blog.adobe.com/jp/publish/2022/06/29/media_162fb947c7219d0537cce36adf22315d64fb86e94.png`
* Les mesures de performances des principales caractéristiques du web (CWV), la plus grande peinture de contenu (LCP), le premier délai d’entrée (FID) et le changement de mise en page cumulatif (CLS) qui décrivent la qualité de l’expérience du visiteur.

### Configuration du service de données de surveillance des utilisateurs réels (RUM) {#how-to-set-up-them-rum-data-service}

* Si vous souhaitez faire partie de notre programme d&#39;adoption précoce, veuillez envoyer un email à `aemcs-rum-adopter@adobe.com`, ainsi que le nom de domaine de l’environnement de production, d’évaluation et de développement à partir de l’adresse électronique associée à votre Adobe ID. L’équipe produit d’Adobe activera alors le service de données de surveillance des utilisateurs réels (RUM) pour vous.
* Une fois cette opération terminée, l’équipe produit de l’Adobe crée un canal de collaboration client.
* L’équipe produit de l’Adobe vous contactera pour vous fournir la clé de domaine et l’URL du tableau de bord de données dans lesquelles vous pouvez afficher les pages vues et [Les principales vitales du Web (CWV)](https://web.dev/vitals/) mesures collectées par la collection Real User Monitoring (RUM) côté client.
* Vous recevrez alors des conseils sur l’utilisation de la clé de domaine pour accéder à l’URL du tableau de bord de données et afficher les mesures.

### Utilisation des données de surveillance des utilisateurs réels (RUM) {#how-rum-data-is-being-used}

Les données RUM sont bénéfiques aux fins suivantes :

* Pour identifier et corriger les goulets d’étranglement en termes de performances pour les sites clients
* Création de rapports de trafic automatique rationalisés qui incluent Pages vues pour les clients utilisant leur propre réseau de diffusion de contenu, ce qui signifie qu’ils n’ont pas à partager de rapport de trafic avec Adobe.
* Pour comprendre comment Adobe Experience Manager interagit avec d’autres scripts (tels que les analyses, le ciblage ou les bibliothèques externes) sur la même page, afin d’améliorer la compatibilité.

### Limites et compréhension des différences dans les mesures de performances et les pages vues {#limitations-and-understanding-variance-in-page-views-and-performance-metrics}

Lorsque vous analyserez ces données, il se peut qu’il y ait ou non des écarts dans les pages vues et d’autres mesures de performances signalées par Real User Monitoring (RUM). Ces écarts peuvent être attribués à plusieurs facteurs inhérents à la surveillance en temps réel côté client. Voici les points essentiels à prendre en compte par les clients lors de l’interprétation de leurs données RUM :

1. **Blocage des dispositifs de suivi**

   * Les utilisateurs finaux qui utilisent des bloqueurs de suivi ou des extensions de confidentialité peuvent empêcher la collecte de données de Real User Monitoring (RUM), car ces outils limitent l’exécution des scripts de suivi. Cette restriction peut entraîner des pages vues et des interactions utilisateur sous-estimées, ce qui crée une incohérence entre l’activité réelle du site et les données capturées par RUM.

1. **Limites de la capture d’appels API/JSON**

   * Le service de données RUM se concentre sur l’expérience côté client et ne capture pas actuellement l’API principal ou les appels JSON. L’exclusion de ces appels des données de surveillance des utilisateurs réels (RUM) créera des écarts par rapport aux demandes de contenu mesurées par CDN Analytics.

### FAQ {#faq}

1. **Comment configurer les chemins à inclure ou à exclure dans la surveillance ?**

   Les clients pourront configurer les chemins d’accès pour inclure ou exclure les URL à des fins de surveillance en définissant les variables d’environnement dans la configuration de Cloud Manager à l’aide de ces variables : `AEM_WEBVITALS_EXCLUDE` et `AEM_WEBVITALS_INCLUDE_PATHS`

   Veuillez noter que par défaut, le paramètre &quot;inclure&quot; est configuré pour cibler &quot;/content&quot;. Il est important de rappeler que les chemins que vous devez configurer ici sont des chemins de contenu dans le système, et non les chemins d’URL que vous voyez dans votre navigateur. Cette distinction est essentielle pour configurer et personnaliser précisément votre configuration en fonction de vos besoins spécifiques.

1. **Adobe peut-il effectuer le suivi de toutes les pages vues avant que l’interaction n’atteigne le réseau de diffusion de contenu géré par le client ou au moment où l’interaction atteint le réseau de diffusion de contenu géré par le client ?**

   Oui.

1. **Les clients seront-ils en mesure d’intégrer les scripts du service de données RUM à des systèmes tiers tels que Dynatrace ?**

   Oui.

1. **Les mesures &quot;Interaction vers la prochaine peinture&quot;, &quot;Temps jusqu’au premier octet&quot; et &quot;Première peinture contentée&quot; des vitaux web sont-elles collectées ?**

   L’interaction avec la prochaine peinture (INP) et le temps jusqu’au premier octet (TTF) sont collectés.  La première peinture contentée n’est pas collectée pour le moment.
