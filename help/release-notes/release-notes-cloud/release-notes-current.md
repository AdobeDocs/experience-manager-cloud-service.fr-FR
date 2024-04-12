---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: ff8d04878da521b55121c9460a9d4b159ec617a4
workflow-type: tm+mt
source-wordcount: '2285'
ht-degree: 31%

---

# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour techniques de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2021 ou 2022.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle (2024.3.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le vendredi 11 avril 2024. La prochaine disponibilité des fonctionnalités (2024.4.0) est prévue pour le vendredi 25 avril 2024.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Vidéo de mise à jour {#release-video}

Regardez la vidéo Présentation de la version de mars 2024 pour un résumé des fonctionnalités ajoutées dans la version 2024.3.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3425864?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités de [!DNL Experience Manager Sites] {#sites-features}

**Création d’AEM pour les Edge Delivery Services**

AEM Sites peut désormais être utilisé comme source de contenu pour les Edge Delivery Services. Les auteurs gèrent leurs sites web dans AEM à l’aide du nouvel éditeur universel avec création wysiwyg dans le contexte. Cela permet aux entreprises de créer rapidement des pages web hautes performances avec des Edge Delivery Services tout en tirant parti AEM puissantes fonctionnalités de gestion de contenu.

![Création AEM](/help/edge/assets/universal_editor_edge_delivery_services.png)

Pour plus d’informations, voir [documentation](/help/edge/overview.md) et regardez le [AEM Gems - Prise en main de la création et des Edge Delivery Services AEM](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/aem-gems-getting-started-with-aem-authoring-and-edge-delivery/m-p/652694#M43905)

**Éditeur universel pour les implémentations sans affichage**

L’éditeur universel permet également aux applications web découplées d’exploiter la même création WYSIWYG intuitive dans le contexte, auparavant réservée aux sites traditionnels. Les créateurs de contenu peuvent désormais composer visuellement des mises en page à l’aide de fragments de contenu avec la même facilité que les composants dans les pages.

Ce qui distingue l’éditeur universel, c’est son adaptabilité à différentes architectures web, ce qui permet le rendu côté serveur et côté client, reste indépendant du framework et élimine la nécessité d’AEM hébergement. L’intégration d’applications web existantes à l’éditeur universel pour la modification de contenu est simple, ce qui nécessite principalement que les développeurs incorporent des attributs de données spécifiques dans leurs balises.

L’éditeur universel assure ainsi une expérience de modification cohérente, quelle que soit la structure de contenu ou la pile technologique sous-jacente. Pour plus d’informations, voir [Présentation de l’éditeur universel](/help/implementing/universal-editor/introduction.md).

**API ouvertes de la gestion de contenu pour les fragments de contenu et les modèles**

Les développeurs peuvent désormais interagir par programmation avec les modèles de fragments de contenu et de fragments de contenu et y effectuer des opérations CruD à l’aide des API OpenAPI de la gestion de contenu. Pour plus d’informations, voir [Documentation de l’API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/)

**Prise en charge de la gestion multisite pour les fragments d’expérience**

La prise en charge de la gestion multisite a été étendue pour les structures de dossiers qui stockent les fragments d’expérience, ce qui permet aux utilisateurs de déployer une structure de contenu complète avec des fragments d’expérience.

**Comparaison des versions de fragments de contenu**

Le nouvel éditeur de fragment de contenu permet désormais aux auteurs de contenu de comparer et d’afficher les différences entre la version actuelle d’un fragment de contenu et une version précédente.

### Programme d’adoption précoce {#sites-early-adopter}

**Générer des variations**

Tirer parti de GenAI grâce à AEM nouvelle fonctionnalité, [générer des variations ;](/help/generative-ai/generate-variations.md), accessible maintenant en Cloud Service. La génération de variations vous permet de générer et d’adapter la création de contenu grâce à l’utilisation de l’IA générative. Contactez votre équipe de compte d’Adobe pour qu’elle prenne en compte le programme.

**Exploration des ressources dans la console de fragments de contenu**

Les auteurs de contenu peuvent désormais parcourir, afficher et agir sur les images et d’autres ressources sans avoir à quitter la console de fragments de contenu.

![Exploration des ressources](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

Vous souhaitez tester la fonctionnalité et partager vos commentaires ? Envoyez un courrier électronique à aemcs-headless-adopter@adobe.com à partir de votre ID de courrier électronique officiel pour en savoir plus sur le programme des premiers adopteurs.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de la vue Assets {#admin-view}

**Intégration native avec Adobe Express**

AEM Assets s’intègre de manière native à Adobe Express, ce qui vous permet d’accéder directement aux ressources stockées dans AEM Assets depuis l’interface utilisateur d’Adobe Express. Vous pouvez placer du contenu géré dans AEM Assets dans la zone de travail express, puis enregistrer du contenu nouveau ou modifié dans un référentiel AEM Assets.

![Inclusion de ressources à partir du module complémentaire Assets.](/help/assets/assets/adobe-express-native-integration.png)

**Rendus d’aperçu pour tous les types de vidéo pris en charge.**

Experience Manager Assets génère désormais par défaut des rendus d’aperçu de tous les types de vidéo pris en charge sans nécessiter de configuration de profil de traitement.

### Nouvelles fonctionnalités de la vue Assets {#assets-view}

**Gestion des autorisations pour les collections**

Assets Essentials permet aux administrateurs de gérer les niveaux d’accès pour les collections privées disponibles dans le référentiel. En tant qu’administrateur, vous pouvez créer des groupes d’utilisateurs et leur attribuer des autorisations afin de gérer les niveaux d’accès. Vous pouvez également déléguer les privilèges de gestion des autorisations aux groupes d’utilisateurs.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Nouvelles fonctionnalités d’AEM Forms {#forms-new-features}

* **[Edge Delivery Services Adobe Experience Manager Forms](/help/edge/docs/forms/overview.md)**: AEM Forms Edge Delivery Services est un ensemble de services composable qui permet un environnement de développement rapide dans lequel les auteurs peuvent rapidement mettre à jour, publier et lancer de nouveaux formulaires. Ces services offrent des expériences de formulaires exceptionnelles et à fort impact qui favorisent l’engagement et les conversions. Ces expériences de formulaires sont faciles à créer et à développer.

  ![Fonctionnalités d’EDS Forms](/help/edge/assets/eds-forms-features.png)

Ces services permettent d’effectuer les opérations suivantes :

* Utilisez plusieurs sources de contenu sur le même site de formulaires et utilisez vos outils de création préférés, tels que Microsoft Excel, Google Sheets ou Adaptive Forms Editor.
* Diffusez des expériences d’inscription numérique qui se chargent et s’affichent rapidement et en permanence pour surveiller les performances de vos formulaires grâce à la surveillance des utilisateurs réels (RUM).
* Utilisez du HTML brut, du code CSS moderne et du code JavaScript vanille pour créer des expériences exceptionnelles, en évitant la courbe d’apprentissage détaillée d’une structure spécifique.


### Nouvelles fonctionnalités de la version préliminaire d’AEM Forms {#forms-pre-release}

* **Éditeur de règles visuel amélioré pour Forms adaptatif basé sur les composants principaux**: cette version apporte une mise à niveau significative de l’éditeur de règles visuel pour les formulaires adaptatifs basés sur les composants principaux. Cette version apporte une mise à niveau significative de l’éditeur de règles visuel pour les formulaires adaptatifs basés sur les composants principaux. Cette mise à jour porte sur la rationalisation des interactions avec des fonctions personnalisées, ce qui vous permet de créer des formulaires plus robustes et efficaces.

  Vous pouvez désormais rationaliser les interactions de fonctions personnalisées en procédant comme suit :

   * Utilisation de nouvelles annotations pour fournir des définitions de fonction plus claires.
   * Utilisation de mécanismes de mise en cache pour les fonctions personnalisées, ce qui accélère les performances du formulaire.
   * Utilisation transparente d’objets globaux dans des fonctions personnalisées.
   * Définir et utiliser des paramètres facultatifs dans des fonctions personnalisées.

  Cette mise à jour apporte également les améliorations suivantes aux fonctionnalités de l’éditeur de règles. Vous pouvez :

   * Implémentez une logique &quot;lorsque-alors-autre&quot; puissante pour l’exécution conditionnelle.
   * Tirez parti des fonctionnalités JavaScript modernes telles que les fonctions de gauche et de flèche (prise en charge d’ES10).
   * Validez ou réinitialisez non seulement des champs, mais également des panneaux et des formulaires entiers, en développant le contrôle sur les interactions utilisateur.

  Ces améliorations offrent une expérience plus intuitive et plus puissante pour l’élaboration de règles et de fonctions personnalisées dans l’éditeur de règles visuel.

* **Création de plusieurs versions d’un formulaire adaptatif**: vous pouvez désormais gérer facilement les variantes de formulaires existants. Cela simplifie le contrôle des versions et facilite la comparaison pour l’optimisation des formulaires, le tout au sein d’un seul processus simplifié.

* **Comparer un formulaire adaptatif**: vous pouvez désormais facilement comparer deux formulaires pour identifier les différences entre deux formulaires. Cela facilite la collaboration en permettant aux membres de l’équipe de comparer les révisions et de discuter efficacement des changements.

* **Améliorations de l’accessibilité pour le composant Signature tactile**: cette mise à jour apporte des améliorations importantes de l’accessibilité au composant Signature tactile :

  **Navigation au clavier améliorée :**
   * Appuyez sur la touche de tabulation pour permettre aux utilisateurs de parcourir tous les éléments interactifs dans la boîte de dialogue de signature.
   * La signature à l’aide d’une brosse ou d’un clavier et la pression sur Entrée ferme la boîte de dialogue.
   * Le focus reste sur le contrôle de signature après avoir signé et cliqué sur &quot;OK&quot;.

  **Effacer la fonctionnalité de signature :**

   * Une croix claire pour effacer la signature est accessible à partir de la touche de tabulation.
   * La boîte de dialogue &quot;Effacer la confirmation de signature&quot; est également accessible via la navigation par onglets.

  **Étiquettes et contrôles améliorés :**
   * Le libellé du bouton de signature au clavier est désormais plus clair, avec &quot;aria-label&quot; pour annoncer la fonctionnalité (par exemple &quot;aria-label=&#39;Sign using Keyboard&#39;&quot;).
   * Un contraste amélioré permet de distinguer facilement tous les contrôles de la signature tactile.
   * Le bouton OK/Cocher indique désormais visuellement à quel moment il est inactif.

  **Commentaires de signature pour les Readers d’écran :**
   * Lorsqu’une signature est saisie, les utilisateurs du lecteur d’écran peuvent entendre le texte utilisé pour créer la signature.

Cette mise à jour offre une expérience plus inclusive aux utilisateurs présentant un handicap en améliorant la navigation, la clarté et les commentaires pour le composant Signature tactile.



### Programme d’adoption précoce {#forms-early-adopter}

* **[Envoyer un formulaire adaptatif au scénario de fusion Adobe Workfront](/help/forms/submit-adaptive-form-to-workfront-fusion.md)**: Forms as a Cloud Service offre une option prête à l’emploi pour connecter facilement un formulaire adaptatif à Adobe Workfront. Cela simplifie le processus d’envoi d’un formulaire adaptatif à un scénario Adobe Workfront, ce qui permet de déclencher un scénario Workfront Fusion lors de l’envoi d’un formulaire adaptatif.

  <br/> ![Adobe Workfront](/help/forms/assets/adobe-workfront.png) <br/> Avec Adobe Workfront Fusion Connector, vous pouvez concevoir des processus qui sont déclenchés automatiquement lors de l’envoi d’un formulaire adaptatif. Par exemple, envisagez un scénario où un processus est lancé pour affecter à une personne spécifique la tâche de vérifier les données envoyées, ce qui permet l’approbation ou le rejet d’une demande en fonction des informations capturées par le biais du formulaire adaptatif. Cette intégration rationalisée améliore l’efficacité et apporte un nouveau niveau d’automatisation à vos processus de workflow.|

* **Service d’extension de Reader**: les API de communication d’AEM Forms ont introduit Reader Extension Service pour vous permettre d’ajouter des fonctionnalités telles que le remplissage de formulaires et les commentaires à des PDF standard, ce qui les rend interactifs pour les utilisateurs disposant d’Adobe Reader gratuit.

* [Prise en charge des langues de droite à gauche](/help/forms/supporting-new-language-localization-core-components.md) : les formulaires adaptatifs reposant sur les composants principaux peuvent désormais être présentés dans une langue de droite à gauche telle que l’arabe, le persan et l’ourdou. Les langues s’écrivant de droite à gauche sont parlées par plus de 2 milliards de personnes dans le monde. L’utilisation d’un formulaire pour les langues s’écrivant de droite à gauche permet d’étendre la portée de vos formulaires adaptatifs pour répondre à ces diverses audiences et aux marchés correspondants. Dans certaines régions, il en va d’une obligation légale de fournir des formulaires dans la langue locale. En vous adaptant aux langues locales, vous vous ouvrez non seulement à un public plus large, mais vous garantissez aussi le respect des lois et réglementations pertinentes.

* **[Protégez vos documents avec les API DocAssurance (qui font partie des API de communication)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)** : les API DocAssurance vous permettent de protéger les informations sensibles en signant et en chiffrant les documents. Grâce au chiffrement, le contenu d’un document est transformé en un format illisible, ce qui garantit que seules les personnes autorisées peuvent y accéder. Cette couche renforcée de protection protège non seulement les données précieuses des yeux non autorisés, mais offre également une certaine tranquillité d’esprit. Les API Signature permettent à votre entreprise de garantir la sécurité et la confidentialité des documents Adobe PDF qu’elle diffuse et reçoit. Ce service utilise les signatures numériques et la certification pour s’assurer que seules les personnes destinataires prévues peuvent modifier les documents.

  Vous pouvez écrire à `aem-forms-ea@adobe.com` depuis votre adresse e-mail officielle pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité.

* **[Vous pouvez utiliser le Service de données Real User Monitoring (RUM)](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)** pour activer la collecte côté client pour AEM as a Cloud Service.
Le Service de données Real User Monitoring (RUM) offre un reflet plus précis des interactions des utilisateurs et utilisatrices, assurant une mesure fiable de l’engagement du site web. Il constitue une excellente opportunité d’obtenir des informations avancées sur les performances de votre page. Il est ainsi utile pour la clientèle qui utilise un réseau CDN géré ou non par Adobe. Par ailleurs, pour les personnes utilisant un réseau CDN non géré par Adobe, il est désormais possible de créer automatiquement des rapports sur le trafic, ce qui leur évite d’avoir à partager n’importe quel rapport sur le trafic avec Adobe.

  Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail à `aemcs-rum-adopter@adobe.com`, avec le nom de domaine de chacun des environnements pour lesquels vous souhaitez activer l’utilisation de RUM depuis votre adresse e-mail associée à votre Adobe ID. L’équipe produit d’Adobe activera alors le service de données Real User Monitoring (RUM) pour vous.

## Principes de base d’[!DNL Experience Manager] as a [!DNL Cloud Service] {#foundation}

### Programmes d&#39;adoption précoce {#foundation-early-adopter}

#### Alertes relatives aux règles de filtrage du trafic (programme des premiers adopteurs) {#traffic-filter-rules-alerts-early-adopter}

La version récemment publiée [Règles de filtrage du trafic](/help/security/traffic-filter-rules-including-waf.md), qui inclut les règles WAF (Web Application Firewall) (Pare-feu d’applications web) facultatives, vous permet de configurer le trafic qui doit être autorisé ou refusé.

Maintenant, vous pouvez envoyer un email **<aemcs-cdn-config-adopter@adobe.com>** pour rejoindre le programme des premiers adopteurs afin que vous puissiez être alerté chaque fois que vos règles de filtre de trafic sont déclenchées. Les notifications par e-mail du centre d’actions vous tiendront informé lorsque certaines conditions de trafic se produisent afin que vous puissiez prendre les mesures appropriées.

#### Configuration du réseau de diffusion de contenu (Programme des Adopteurs Anticipés) {#cdn-config-early-adopter}

Outre la version récemment publiée [Règles de filtrage du trafic](/help/security/traffic-filter-rules-including-waf.md), qui incluent éventuellement les règles WAF (Web Application Firewall) concédables, il existe une opportunité d’utiliser le pipeline de configuration pour déclarer et déployer d’autres types de configuration CDN. [En savoir plus](/help/implementing/dispatcher/cdn-configuring-traffic.md) et rejoindre le programme des premiers adopteurs en envoyant un courrier électronique **<aemcs-cdn-config-adopter@adobe.com>** pour accéder à :

* Redirections côté client 301/302
* proxy des requêtes en périphérie vers des origines arbitraires (comme des applications non AEM)
* Transformations d’URL
* Définir ou modifier des en-têtes de requête ou de réponse
* Pages d’erreur personnalisées lorsque le réseau CDN ne peut pas atteindre AEM.

#### Ingestion du temps d’exécution Apache/Dispatcher des cartes de réécriture (programme d’adoption précoce) {#apache-rewritemaps-early-adopter}

Comme pour AEM 6.5, Apache/dispatcher ingère des cartes de réécriture placées à un emplacement spécifique dans le référentiel de publication et les charge, sans nécessiter d’exécution de pipeline de niveau web. Un utilisateur chargé de la conception de parcours peut ainsi déclarer des redirections à l’aide d’une interface utilisateur, comme celle proposée par ACS Commons Redirect Map Manager. Veuillez contacter **<aemcs-cdn-config-adopter@adobe.com>** pour plus d’informations.

#### Edge Side Inclut (ESI) pour le chargement de contenu dynamique (Programme des premiers adopteurs) {#esi-early-adopter}

Le réseau de diffusion de contenu géré par Adobe prend désormais en charge Edge Side Includes (ESI), un langage de balisage pour l’assemblage de contenu web dynamique de niveau périphérie. En incluant des fragments de code ESI, vous pouvez mettre en cache la page de HTML globale sur le réseau de diffusion de contenu avec des TTL plus élevés, tout en récupérant plus souvent à partir de l’origine les sections plus petites qui nécessitent des mises à jour de cadence plus élevées (TTL moins élevées). Veuillez contacter **<aemcs-cdn-config-adopter@adobe.com>** pour plus d’informations.

#### Prise en charge de RDE pour le code frontal à l’aide des thèmes du site et des modèles de site (programme des membres précoces) {#rde-frontend-early-adopter}

Les [environnements de développement rapide (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md) prennent désormais en charge le code en front-end basé sur les [thèmes de site](/help/sites-cloud/administering/site-creation/site-themes.md) et les [modèles de site](/help/sites-cloud/administering/site-creation/site-templates.md), pour les utilisateurs et utilisatrices bénéficiant de l’adoption précoce. Avec les RDE, la prise en charge s’effectue à l’aide d’une directive de ligne de commande plutôt que d’un [pipeline front-end](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md). Veuillez contacter **<aemcs-rde-support@adobe.com>** pour essayer et fournir des commentaires.

#### Amélioration de la journalisation des RDE (Programme des premiers adopteurs) {#rde-logging-early-adopter}

Lors du débogage du code dans une [Environnement de développement rapide (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md), les développeurs peuvent désormais configurer et diffuser plus efficacement les journaux à l’aide de la ligne de commande, et sans modifier les propriétés OSGI dans le contrôle de version. Les fonctionnalités incluent :

* déclarer des niveaux de journal à chaque niveau de package ou de classe
* personnaliser le format de sortie du journal ;
* flux de plusieurs journaux en parallèle

Veuillez contacter **<aemcs-rde-support@adobe.com>** pour essayer et fournir des commentaires.

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
