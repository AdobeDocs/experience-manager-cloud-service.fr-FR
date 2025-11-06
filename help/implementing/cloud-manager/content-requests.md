---
title: Comprendre les requêtes de contenu Cloud Service
description: Si vous avez acheté des licences de demande de contenu auprès d’Adobe, découvrez les types de demandes de contenu que Adobe Experience Cloud as a Service mesure et les écarts avec les outils de création de rapports Analytics d’une organisation.
exl-id: 3666328a-79a7-4dd7-b952-38bb60f0967d
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1918'
ht-degree: 2%

---

# Comprendre les requêtes de contenu Cloud Service

## Présentation {#introduction}

Les demandes de contenu incluent les demandes envoyées à AEM Sites. Ces requêtes peuvent être acheminées via Edge Delivery Services ou des systèmes de mise en cache fournis par le client, tels qu’un réseau de diffusion de contenu (CDN). Ces requêtes diffusent des données structurées au format HTML ou JSON et prennent en charge les pages vues (par exemple, les pages et les fragments d’expérience) ou les retours JSON par le biais d’API de manière découplée.

Le système comptabilise les demandes de contenu lorsqu’un utilisateur ou une utilisatrice consulte une page à l’aide d’HTML ou de JSON. Il mesure la requête au moment où le premier système de mise en cache la reçoit. Certaines requêtes HTTP sont incluses ou exclues à des fins de comptage des requêtes de contenu. Consultez la liste complète des [demandes de contenu incluses](#included-content-requests) et [demandes de contenu exclues](#excluded-content-request) HTTP.

>[!NOTE]
>
>Les données affichées dans la vue Demandes de contenu sont actualisées toutes les 24 heures.

## À propos des demandes de contenu Cloud Service {#understanding-cloud-service-content-requests}

Une *requête de page* fait référence à une requête HTTP qui récupère le contenu structuré de base (par exemple, HTML ou JSON) nécessaire pour effectuer le rendu de l’expérience de la page principale. Elle n’inclut pas les demandes de ressources, telles que des images ou des scripts.

Pour les clients qui utilisent le réseau de diffusion de contenu prêt à l’emploi, AEM as a Cloud Service comptabilise les demandes de contenu au niveau du serveur. Cette mesure se produit automatiquement et ne dépend pas du suivi de l’analyse côté client.

AEM (Adobe Experience Manager) as a Cloud Service identifie les demandes de contenu en fonction des types de réponse générés par l’instance AEM et reçus sur le réseau CDN. Plus précisément, les requêtes qui renvoient HTML (`text/html`) ou JSON (`application/json`) sont comptabilisées. Ces formats diffusent généralement le contenu de la page principale pour un rendu de site classique ou une diffusion découplée.

Les demandes de ressources statiques telles que des fichiers JavaScript, des feuilles de style CSS et des images ne sont pas comptabilisées comme des demandes de contenu.

>[!NOTE]
>Si une requête d’API renvoie HTML ou JSON qui sert de contenu au niveau de la page (par exemple, dans une diffusion découplée), elle peut toujours être comptabilisée comme une requête de contenu, selon son contexte.

Les requêtes de contenu sont mesurées que la réponse ait été diffusée à partir du cache du réseau CDN ou transférée vers l’environnement AEM d’origine.

<!-- REMOVED AS PER EMAIL REQUEST FROM SHWETA DUA, JULY 30, 2024 TO RICK BROUGH AND ALEXANDRU SARCHIZ   For customers employing their own CDN, client-side collection offers a more precise reflection of interactions, ensuring a reliable measure of website engagement via the [Real Use Monitoring](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md) service. This gives customers advanced insights into their page traffic and performance. While it is beneficial for all customers, it offers a representative reflection of user interactions, ensuring a reliable measure of website engagement by capturing the number of page views from the client side. 

For customers that bring their own CDN on top of AEM as a Cloud Service, server-side reporting results in numbers that cannot be used to compare with the licensed content requests. With the [Real Use Monitoring](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md), Adobe can reflect a reliable measure of website engagement. -->

### Variances des demandes de contenu Cloud Service {#content-requests-variances}

Les requêtes de contenu peuvent présenter des variations au sein des outils de création de rapports d’analyse d’une organisation, comme résumé dans le tableau suivant. En règle générale, évitez d’utiliser des outils d’analyse qui reposent sur une instrumentation côté client pour signaler le nombre de demandes de contenu pour un site. Ces outils manquent souvent une grande partie du trafic, car leur activation dépend du consentement de l’utilisateur. Les outils Analytics qui collectent des données côté serveur dans les fichiers journaux, ou les rapports de réseau CDN pour les clients qui ajoutent leur propre réseau CDN en plus d’AEM as a Cloud Service, fournissent de meilleurs chiffres.

| Raison de l’écart | Explication |
|---|---|
| Consentement de l’utilisateur final | Le déclenchement des outils Analytics qui reposent sur une instrumentation côté client dépend souvent du consentement de l’utilisateur. Ce workflow peut représenter la majorité du trafic non suivi. Pour les clients qui souhaitent mesurer eux-mêmes les demandes de contenu, Adobe vous recommande de vous fier aux outils d’analyse pour collecter les données à partir de rapports côté serveur ou CDN. |
| Balisage | Toutes les pages ou appels d’API qui font l’objet d’un suivi sous forme de demandes de contenu Adobe Experience Manager peuvent ne pas être balisés avec le suivi Analytics. |
| Règles de gestion des balises | Les paramètres des règles de gestion des balises peuvent entraîner diverses configurations de collecte de données sur une page, ce qui entraîne une combinaison d’incohérences avec le suivi des demandes de contenu. |
| Robots | Les robots inconnus qu’AEM n’a pas pré-identifiés et supprimés peuvent entraîner des incohérences dans le suivi. |
| Suites de rapports | Les pages d’une même instance AEM peuvent créer des rapports vers différentes suites de rapports d’analyse. Ce processus peut fractionner les données entre plusieurs suites, selon la configuration. |
| Outils de surveillance et de sécurité tiers | Les outils de surveillance et d’analyse de sécurité (par exemple, les vérificateurs de disponibilité ou les analyseurs de vulnérabilité) peuvent demander des pages, générant des demandes de contenu côté serveur non visibles dans les rapports d’analyse. |
| Accès à l’API | Les requêtes envoyées aux pages ou au contenu AEM par le biais des API (par exemple, via Adobe Experience Manager as a Headless CMS) sont toujours comptabilisées comme des requêtes de contenu, mais ne déclenchent pas de suivi Analytics. |
| Pré-récupérer des demandes | La prérécupération (par exemple à l’aide d’un service worker ou d’une fonction Edge) peut augmenter les volumes de trafic en demandant des pages à l’avance. Ces requêtes sont comptabilisées côté serveur, mais n’exécutent pas le code d’analyse côté client. |
| DDOS | Adobe utilise le filtrage pour détecter et bloquer de nombreuses attaques DDoS. Cependant, certaines requêtes d’attaque peuvent toujours être comptabilisées comme des requêtes de contenu avant l’application des filtres. |
| Bloqueurs de trafic | Les fonctionnalités de confidentialité dans le navigateur ou les pare-feu d’entreprise peuvent bloquer le chargement des scripts d’analyse. Ces utilisateurs génèrent toujours des demandes de contenu côté serveur. |
| Pare-feux | Les pare-feu d’entreprise ou régionaux peuvent empêcher les appels Analytics d’atteindre les serveurs Adobe, ce qui entraîne une sous-déclaration dans Analytics sans affecter le nombre de comptes côté serveur. |

Consultez le [Tableau de bord des licences](/help/implementing/cloud-manager/license-dashboard.md) pour plus d’informations sur l’affichage et le suivi de l’utilisation des demandes de contenu par rapport à vos limites de licence.

## Règles de collecte côté serveur {#serverside-collection}

AEM as a Cloud Service applique des règles de collecte côté serveur pour comptabiliser les requêtes de contenu. Ces règles excluent les robots connus (tels que les robots de moteur de recherche) et un ensemble de services de surveillance qui effectuent régulièrement des requêtes ping sur le site. Tout autre trafic de type synthétique ou surveillance ne figurant pas sur cette liste d’exclusion est comptabilisé comme des demandes de contenu facturables.

Les tableaux suivants répertorient les types de demandes de contenu incluses et exclues, avec de brèves descriptions de chacune d’elles.

### Types de demandes de contenu incluses {#included-content-requests}

>[!NOTE]
>Si une requête API renvoie une réponse HTML, elle peut être classée comme une requête de contenu, selon son contexte d’utilisation. Les requêtes d’API renvoyant des données hors interface utilisateur sont généralement exclues.

| Type de demande | Demande de contenu | Description |
| --- | --- | --- |
| Code HTTP 100-299 | Inclus | Inclut les requêtes réussies qui renvoient un contenu HTML ou JSON complet ou partiel.<br>Code HTTP 206 : ces requêtes ne diffusent qu’une partie du contenu complet. Par exemple, une vidéo ou une image volumineuse. Les requêtes de contenu partielles sont incluses lorsqu’elles diffusent une partie d’une réponse HTML ou JSON utilisée dans le rendu du contenu de la page. |
| Bibliothèques HTTP à automatiser | Inclus | Les requêtes effectuées par les outils ou les bibliothèques qui récupèrent le contenu des pages. Par exemple : <br>· Amazon CloudFront<br>· Client Apache Http<br>· Client HTTP asynchrone<br>· Axios<br>· Azureus<br>· Curl<br>· Récupération de nœud GitHub<br>· Guzzle<br>· Go-http-client<br>· Chrome découplé· Java™ Client<br>· Jersey<br>· Nœud Oembed<br>· okhttp<br>· Requêtes Python<br>· Reactor Netty<br>· WinHTTP<br>· HTTP<br> rapide· Nœud GitHub Fetch<br> <br> <br>· Reactor |
| Outils de surveillance et de contrôle de l’intégrité | Inclus | Demandes utilisées pour surveiller l’intégrité ou la disponibilité des pages.<br>Voir [Types de demandes de contenu exclues](#excluded-content-request).<br>Par exemple :<br>· `Amazon-Route53-Health-Check-Service`<br>· EyeMonIT_bot_version_0.1_[(https://eyemonit.com/)](https://eyemonit.com/)<br>· Investis-Site24x7<br>· Mozilla/5.0+(compatible ; UptimeRobot/2.0 ; [https://uptimerobot.com/](https://uptimerobot.com/))<br>· ThousandEyes-Dragonfly-x1<br>· OmtrBot/1.0<br>· WebMon/2.0.0 |
| `<link rel="prefetch">` requêtes | Inclus | Lorsque les clients préchargent ou prérécupèrent du contenu (par exemple, avec `<link rel="prefetch">`), le système comptabilise ces requêtes côté serveur. Gardez à l’esprit que cette approche peut augmenter le trafic, selon le nombre de pages prérécupérées. |
| Trafic qui bloque les rapports Adobe Analytics ou Google Analytics | Inclus | Il est plus courant que les visiteurs et visiteuses de sites disposent d’un logiciel de confidentialité installé (bloqueurs de publicités, etc.) qui affecte la précision de Google Analytics ou d’Adobe Analytics. AEM as a Cloud Service comptabilise les requêtes sur le premier point d’entrée de l’infrastructure gérée par Adobe et non du côté client. |

Voir aussi [Tableau de bord des licences](/help/implementing/cloud-manager/license-dashboard.md).

### Types de demandes de contenu exclues {#excluded-content-request}

| Type de demande | Demande de contenu | Description |
| --- | --- | --- |
| Code HTTP 500+ | Exclu | Erreurs renvoyées au visiteur lorsqu’un problème se produit sur AEM as a Cloud Service ou dans le code personnalisé du client. |
| Code HTTP 400-499 | Exclu | Erreurs renvoyées au visiteur lorsque le contenu n’existe pas (404) ou qu’il existe d’autres problèmes liés au contenu ou aux requêtes. |
| Code HTTP 300-399 | Exclu | Bonnes requêtes permettant de vérifier si quelque chose a changé sur le serveur ou de rediriger la requête vers une autre ressource. Ils ne contiennent pas de contenu lui-même et ne sont donc pas facturables. |
| Demandes allant dans `/libs/`* | Exclu | Requêtes JSON internes AEM, telles que le jeton CSRF qui n’est pas facturable. |
| Trafic provenant d’attaques DDOS | Exclu | Protection DDOS. AEM détecte automatiquement certaines des attaques DDOS et les bloque. Les attaques DDOS détectées ne sont pas facturables. |
| Surveillance d’AEM as a Cloud Service New Relic | Exclu | Surveillance globale d’AEM as a Cloud Service. |
| URL permettant aux clients de surveiller leur programme Cloud Service | Exclu | Adobe vous recommande d’utiliser l’URL pour surveiller la disponibilité ou le contrôle d’intégrité en externe.<br><br>`/system/probes/health` |
| Service de préchauffage de capsule AEM as a Cloud Service | Exclu |
| Agent : skyline-service-préchauffage/1.* |
| Moteurs de recherche connus, réseaux sociaux et bibliothèques HTTP (avec le tag Fastly) | Exclu | Services connus visitant régulièrement le site pour actualiser leur index ou service de recherche :<br><br>Exemples :<br>· AddSearchBot<br>· AhrefsBot<br>· Applebot<br>· Ask Jeeves Corporate Spider<br>· Bingbot<br>· BingPreview<br>· BLEXBot<br>· BuiltWith<br>· Bytespider<br>· CrawlerKengo<br>· Facebookexternalhit<br>· Google AdsBot<br>· Google AdsBot Mobile<br>· Googlebot<br>· Googlebot Mobile<br> lmspider<br>· LucidWorks<br>· Pinterest`MJ12bot`<br>· SemrushBot<br>· SiteImprov<br>· StashBot<br>· StatusCake<br>· YandexBot<br>· ContentKing<br> <br>· Claudebot |
| Exclure les appels Commerce integration framework | Exclu | Les demandes envoyées à AEM qui sont transférées vers Commerce integration framework (l’URL commence par `/api/graphql`) ne sont pas facturables pour Cloud Service afin d’éviter un double comptage. |
| Exclure le `manifest.json` | Exclu | Le manifeste n’est pas un appel API. Il permet de fournir des informations sur la manière d’installer des sites web sur un ordinateur ou un téléphone mobile. Adobe ne doit pas compter les requêtes JSON à `/etc.clientlibs/*/manifest.json` |
| Exclure le `favicon.ico` | Exclu | Bien que le contenu renvoyé ne doive pas être HTML ou JSON, il a été observé que certains scénarios tels que les flux d’authentification SAML renvoient des icônes en tant qu’HTML. Par conséquent, les favicons sont explicitement exclus du décompte. |
| Fragment d’expérience (XF) - Réutilisation dans le même domaine | Exclu | Les requêtes envoyées aux chemins d’accès XF (tels que `/content/experience-fragments/...`) à partir de pages hébergées sur le même domaine (tel qu’identifié par l’en-tête référent correspondant à l’hôte de requête).<br><br> exemple : une page d’accueil sur `aem.customer.com` extrayant un fichier XF pour une bannière ou une carte du même domaine.<br><br>· Correspondances d’URL /content/experience-fragments/...<br>· Correspondances de domaine référent `request_x_forwarded_host`<br><br>**Remarque :** si le chemin d’accès au fragment d’expérience est personnalisé (par exemple à l’aide de `/XFrags/...` ou de tout chemin d’accès en dehors de `/content/experience-fragments/`), la requête ne sera pas exclue et pourra être comptabilisée, même si elle concerne le même domaine. Nous vous recommandons d’utiliser la structure de chemin XF standard d’Adobe pour vous assurer que la logique d’exclusion s’applique correctement. |

## Gestion des demandes de contenu {#managing-content-requests}

Comme mentionné dans la section ci-dessus [Variances des requêtes de contenu Cloud Service](#content-requests-variances), les requêtes de contenu peuvent être plus élevées que prévu pour plusieurs raisons, un thread commun étant le trafic atteignant le réseau CDN.  En tant que client AEM, il est à votre avantage de surveiller et de gérer vos demandes de contenu pour respecter votre budget de licence.  La gestion des requêtes de contenu est généralement une combinaison de techniques d’implémentation et de [&#x200B; règles de filtrage du trafic](/help/security/traffic-filter-rules-including-waf.md).

### Techniques d’implémentation pour gérer les demandes de contenu {#implementation-techniques-to-manage-crs}

* Assurez-vous que toutes les réponses Page introuvable sont diffusées avec un statut HTTP 404.  Si elles sont renvoyées avec un statut 200, elles sont prises en compte dans les demandes de contenu.
* Acheminez les outils de contrôle ou de surveillance de l’intégrité vers l’URL /systems/probes/health ou utilisez la méthode HEAD au lieu de GET pour éviter toute demande de contenu.
* Trouvez l’équilibre entre vos besoins de fraîcheur de contenu et le coût de licence AEM pour tout moteur de recherche personnalisé que vous avez intégré à votre site.  Un robot d’exploration trop agressif peut consommer beaucoup de requêtes de contenu.
* Gérez les redirections comme côté serveur (statut 301 ou 302) plutôt que côté client (statut 200 avec redirection JavaScript) pour éviter deux requêtes de contenu distinctes.
* Combiner ou réduire les appels d’API, qui sont des réponses JSON d’AEM pouvant être chargées pour effectuer le rendu de la page.

### Règles de filtrage du trafic pour la gestion des demandes de contenu {#traffic-filter-rules-to-manage-crs}

* Un modèle de robot courant consiste à utiliser un agent utilisateur vide.  Vous devez passer en revue votre implémentation et les modèles de trafic pour voir si l’agent utilisateur vide est utile ou non.  Si vous souhaitez bloquer ce trafic, la [syntaxe](/help/security/traffic-filter-rules-including-waf.md#rules-syntax) recommandée est la suivante :

```
trafficFilters:
  rules:
    - name: block-missing-user-agent
      when:
        anyOf:
          - { reqHeader: user-agent, exists: false }
          - { reqHeader: user-agent, equals: '' }
      action: block
```

* Certains robots ont frappé un site très lourdement un jour et disparaissent le lendemain.  Cela peut empêcher toute tentative de blocage d’une adresse IP ou d’un agent utilisateur spécifique.  Une approche générique consiste à introduire une [&#x200B; règle de limitation des taux](/help/security/traffic-filter-rules-including-waf.md#rate-limit-rules).  Examinez les [exemples](/help/security/traffic-filter-rules-including-waf.md#ratelimiting-examples) et créez une règle qui correspond à votre tolérance pour un taux rapide de requêtes.  Consultez la syntaxe [Structure de condition](/help/security/traffic-filter-rules-including-waf.md#condition-structure) pour connaître les exceptions que vous souhaitez peut-être autoriser à une limite de taux générique.
