---
title: Notes de mise à jour de la version 2024.3.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2024.3.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: b3816929-2c0a-4d6a-b583-c928d2182ecd
feature: Release Information
role: Admin
source-git-commit: 7f63f66cb1753fc32996e4672214eccc33ca8d92
workflow-type: tm+mt
source-wordcount: '2293'
ht-degree: 95%

---

# Notes de mise à jour de la version 2024.3.0 d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour de la version 2024.3.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2021 ou 2022.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle (2024.3.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le 11 avril 2024. La prochaine disponibilité des fonctionnalités (2024.4.0) est prévue pour le 25 avril 2024.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Vidéo de mise à jour {#release-video}

Regardez la vidéo de vue d’ensemble de la version de mars 2024 pour obtenir un résumé des fonctionnalités ajoutées dans la version 2024.3.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3428342?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités de [!DNL Experience Manager Sites] {#sites-features}

**Création AEM pour Edge Delivery Services**

AEM Sites peut désormais être utilisé comme source de contenu pour Edge Delivery Services. Les auteurs et les autrices gèrent leurs sites web dans AEM à l’aide du nouvel éditeur universel avec création WYSIWYG en contexte. Cela permet aux entreprises de créer rapidement des pages web hautes performances avec Edge Delivery Services tout en tirant parti des fonctionnalités puissantes de gestion du contenu d’AEM.

![Création AEM](/help/edge/assets/universal_editor_edge_delivery_services.png)

Pour plus d’informations, consultez la [documentation](/help/edge/overview.md) et regardez [AEM Gems - Commencer avec la création AEM et Edge Delivery Services](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/aem-gems-getting-started-with-aem-authoring-and-edge-delivery/m-p/652694?profile.language=fr#M43905)

**Éditeur universel pour des implémentations découplées**

L’éditeur universel permet également aux applications web découplées d’exploiter la même création WYSIWYG intuitive en contexte, auparavant réservée aux sites traditionnels. Les créateurs et les créatrices de contenu peuvent désormais composer visuellement des dispositions à l’aide de fragments de contenu avec la même facilité que les composants dans les pages.

Ce qui distingue l’éditeur universel, c’est son adaptabilité à différentes architectures web, ce qui permet le rendu côté serveur et côté client, de rester indépendant du framework et d’éliminer la nécessité d’un hébergement AEM. L’intégration d’applications web existantes à l’éditeur universel pour la modification de contenu est simple et nécessite principalement que les développeurs et les développeuses incorporent des attributs de données spécifiques dans leurs balisage.

L’éditeur universel assure ainsi une expérience de modification cohérente, quelle que soit la structure du contenu ou la pile technologique sous-jacente. Pour plus d’informations, voir la [Présentation de l’éditeur universel](/help/implementing/universal-editor/introduction.md).

**API OpenAPI de gestion du contenu pour les fragments de contenu et les modèles**

Les développeurs et les développeuses peuvent désormais interagir par programmation avec les fragments de contenu et les modèles de fragment de contenu et effectuer des opérations CruD sur ceux-ci à l’aide des API OpenAPI de gestion du contenu. Pour plus d’informations, voir la [documentation de l’API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/).

**Prise en charge de la gestion multisite pour les fragments d’expérience**

La prise en charge de la gestion multisite a été étendue pour les structures de dossiers qui stockent des fragments d’expérience, ce qui permet aux utilisateurs et utilisatrices de déployer une structure de contenu complète avec des fragments d’expérience.

**Comparer les versions de fragments de contenu**

Le nouvel éditeur de fragment de contenu permet désormais aux auteurs et autrices de contenu de comparer et d’afficher les différences entre la version actuelle d’un fragment de contenu et une version précédente.

### Programme d’adoption précoce {#sites-early-adopter}

**Générer des variations**

Tirez profit de GenAI grâce à une nouvelle fonctionnalité d’AEM, [générer des variations](/help/generative-ai/generate-variations.md), maintenant accessible dans Cloud Service. La génération de variations vous permet de générer et d’adapter la création de contenu grâce à l’utilisation de l’IA générative. Contactez votre équipe Adobe en charge des comptes pour en savoir plus sur le programme.

**Explorer les ressources dans la console de fragments de contenu**

Les auteurs et les autrices de contenu peuvent désormais parcourir, afficher et agir sur les images et d’autres ressources sans avoir à quitter la console de fragments de contenu.

![Explorer des ressources](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

Vous souhaitez tester la fonctionnalité et partager vos commentaires ? Envoyez un e-mail à aemcs-headless-adopter@adobe.com à partir de votre ID d’e-mail officiel pour en savoir plus le programme d’adoption précoce.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de la vue d’administration {#admin-view}

**Intégration native à Adobe Express**

AEM Assets s’intègre de manière native à Adobe Express, ce qui vous permet d’accéder directement aux ressources stockées dans AEM Assets depuis l’interface utilisateur d’Adobe Express. Vous pouvez placer du contenu géré dans AEM Assets dans la zone de travail d’Express, puis enregistrer du contenu nouveau ou modifié dans un référentiel AEM Assets.

![Inclure des ressources à partir du module complémentaire Assets](/help/assets/assets/adobe-express-native-integration.png)

**Rendus d’aperçu pour tous les types de vidéo pris en charge**

Experience Manager Assets génère désormais par défaut des rendus d’aperçu de tous les types de vidéo pris en charge sans nécessiter de configuration de profil de traitement.

### Nouvelles fonctionnalités de la vue Assets {#assets-view}

**Gérer les autorisations des collections**

Grâce à Assets Essentials, les administrateurs et les administratrices peuvent gérer les niveaux d’accès aux collections disponibles dans le référentiel. En tant qu’administrateur ou administratrice, vous pouvez créer des groupes d’utilisateurs et d’utilisatrices et leur attribuer des autorisations afin de gérer les niveaux d’accès. Vous pouvez également déléguer les privilèges de gestion des autorisations aux groupes d’utilisateurs et d’utilisatrices.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Nouvelles fonctionnalités pour AEM Forms {#forms-new-features}

* **[Adobe Experience Manager Forms Edge Delivery Services](/help/edge/docs/forms/overview.md)** : Edge Delivery Services pour AEM Forms est un ensemble composable de services qui permet un environnement de développement rapide dans lequel les auteurs et autrices peuvent mettre à jour, publier et lancer rapidement de nouveaux formulaires. Ces services offrent des expériences de formulaires exceptionnelles et à fort impact qui favorisent l’engagement et les conversions. Ces expériences de formulaires sont faciles à créer et à développer.

  ![Fonctionnalités d’EDS Forms](/help/edge/assets/eds-forms-features.png)

Ces services permettent d’effectuer les opérations suivantes :

* Utilisez plusieurs sources de contenu sur le même site de formulaires et utilisez vos outils de création préférés, tels que Microsoft Excel, Google Sheets ou l’éditeur de formulaires adaptatifs.
* Proposez des expériences d’inscription numérique qui chargent et rendent rapidement et surveillent en permanence les performances de vos formulaires par le biais de la surveillance d’utilisation réelle (RUM).
* Utilisez du HTML brut, du code CSS moderne et du code Vanilla JavaScript pour créer des expériences exceptionnelles, en évitant la courbe abrupte d’apprentissage d’un framework spécifique.


### Nouvelles fonctionnalités de la version préliminaire pour AEM Forms {#forms-pre-release}

* **Éditeur de règles visuel amélioré pour les formulaires adaptatifs basés sur les composants principaux** : cette version introduit une mise à niveau significative de l’éditeur de règles visuel pour les formulaires adaptatifs basés sur les composants principaux. Cette version introduit une mise à niveau significative de l’éditeur de règles visuel pour les formulaires adaptatifs basés sur les composants principaux. Cette mise à jour porte sur la rationalisation des interactions avec des fonctions personnalisées, ce qui vous permet de créer des formulaires plus robustes et efficaces.

  Vous pouvez désormais rationaliser les interactions de fonctions personnalisées en :

   * utilisant de nouvelles annotations pour fournir des définitions de fonction plus claires ;
   * utilisant des mécanismes de mise en cache pour les fonctions personnalisées, ce qui accélère les performances du formulaire ;
   * utilisant en toute transparence des objets globaux dans des fonctions personnalisées ;
   * définissant et en utilisant des paramètres facultatifs dans des fonctions personnalisées.

  Cette mise à jour introduit également les améliorations suivantes aux fonctionnalités de l’éditeur de règles. Vous pouvez :

   * implémenter une logique « when-then-else » (lorsque-alors-sinon) puissante pour l’exécution conditionnelle ;
   * tirer profit de fonctionnalités JavaScript modernes telles que les fonctions let et arrow (prise en charge d’ES10) ;
   * valider ou réinitialiser non seulement des champs, mais également des panneaux et des formulaires entiers, en optimisant le contrôle sur les interactions des utilisateurs et utilisatrices.

  Ces améliorations offrent une expérience plus intuitive et plus puissante pour l’élaboration de règles et de fonctions personnalisées dans l’éditeur de règles visuel.

* **Créer plusieurs versions d’un formulaire adaptatif** : vous pouvez désormais gérer facilement les variations de formulaires existants. Cela simplifie la gestion de versions et facilite la comparaison pour l’optimisation des formulaires, le tout au sein d’un seul workflow simplifié.

* **Comparer des formulaires adaptatifs** : vous pouvez désormais comparer facilement deux formulaires pour identifier les différences entre eux. Cela facilite la collaboration en permettant aux personnes membres de l’équipe de comparer les révisions et de discuter efficacement des changements.

* **Améliorations de l’accessibilité pour le composant Signature tactile** : cette mise à jour introduit des améliorations importantes de l’accessibilité au composant Signature tactile :

  **Navigation au clavier améliorée :**
   * En appuyant sur la touche de tabulation, les utilisateurs et utilisatrices peuvent parcourir tous les éléments interactifs dans la boîte de dialogue de signature.
   * Signer avec un pinceau ou un clavier et appuyer sur la touche Entrée entraîne la fermeture de la boîte de dialogue.
   * Le focus reste sur la commande de signature après avoir signé et cliqué sur « OK ».

  **Fonctionnalité Effacer la signature :**

   * Une icône en forme de croix claire pour effacer la signature est accessible via la touche de tabulation.
   * La boîte de dialogue de confirmation « Effacer la signature » est également accessible via la navigation à l’aide de la touche de tabulation.

  **Libellés et contrôles améliorés :**
   * Le libellé du bouton de signature au clavier est désormais plus clair, et utilise « aria-label » pour annoncer la fonctionnalité (par exemple, « aria-label=&#39;Signer à l’aide du clavier&#39; »).
   * Un contraste amélioré permet de distinguer facilement tous les contrôles de la signature tactile.
   * Le bouton OK/coche indique désormais visuellement quand il est inactif.

  **Retour audio de signature pour les lecteurs d’écran :**
   * Lorsqu’une signature est saisie, les utilisateurs et les utilisatrices du lecteur d’écran peuvent entendre le texte utilisé pour créer la signature.

Cette mise à jour offre une expérience plus inclusive aux utilisateurs et utilisatrices présentant un handicap en améliorant la navigation, la clarté et le retour audio pour le composant Signature tactile.

### Programme d’adoption précoce {#forms-early-adopter}

* **[Envoi d’un formulaire adaptatif à un scénario Adobe Workfront Fusion](/help/forms/submit-adaptive-form-to-workfront-fusion.md)** : Forms as a Cloud Service propose une option prête à l’emploi pour connecter facilement un formulaire adaptatif à Adobe Workfront. Cela simplifie le processus d’envoi d’un formulaire adaptatif à un scénario Adobe Workfront, ce qui permet de déclencher un scénario Workfront Fusion lors de l’envoi d’un formulaire adaptatif.

  <br/> ![Adobe Workfront](/help/forms/assets/adobe-workfront.png) <br/> Avec le connecteur Adobe Workfront Fusion, vous pouvez concevoir des workflows qui sont déclenchés automatiquement lors de l’envoi d’un formulaire adaptatif. Par exemple, envisagez un scénario où un workflow est lancé pour affecter à une personne spécifique la tâche de révision des données envoyées, ce qui permet d’approuver ou de rejeter une application en fonction des informations capturées par le biais du formulaire adaptatif. Cette intégration rationalisée améliore l’efficacité et offre un nouveau niveau d’automatisation à vos processus de workflow.

* **Reader Extension Service** : les API de communication d’AEM Forms ont introduit Reader Extension Service pour vous permettre d’ajouter des fonctionnalités telles que le remplissage de formulaires et les commentaires dans des PDF standard, ce qui les rend interactifs pour les utilisateurs et les utilisatrices disposant de la version gratuite d’Adobe Reader.

* [Prise en charge des langues de droite à gauche](/help/forms/supporting-new-language-localization-core-components.md) : les formulaires adaptatifs reposant sur les composants principaux peuvent désormais être présentés dans une langue de droite à gauche telle que l’arabe, le persan et l’ourdou. Les langues s’écrivant de droite à gauche sont parlées par plus de 2 milliards de personnes dans le monde. L’utilisation d’un formulaire pour les langues s’écrivant de droite à gauche permet d’étendre la portée de vos formulaires adaptatifs pour répondre à ces diverses audiences et aux marchés correspondants. Dans certaines régions, il en va d’une obligation légale de fournir des formulaires dans la langue locale. En vous adaptant aux langues locales, vous vous ouvrez non seulement à un public plus large, mais vous garantissez aussi le respect des lois et réglementations pertinentes.

* **[Protégez vos documents avec les API DocAssurance (qui font partie des API de communication)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)** : les API DocAssurance vous permettent de protéger les informations sensibles en signant et en chiffrant les documents. Grâce au chiffrement, le contenu d’un document est transformé en un format illisible, ce qui garantit que seules les personnes autorisées peuvent y accéder. Cette couche renforcée de protection protège non seulement les données précieuses des yeux non autorisés, mais offre également une certaine tranquillité d’esprit. Les API Signature permettent à votre entreprise de garantir la sécurité et la confidentialité des documents Adobe PDF qu’elle diffuse et reçoit. Ce service utilise les signatures numériques et la certification pour s’assurer que seules les personnes destinataires prévues peuvent modifier les documents.

  Vous pouvez écrire à `aem-forms-ea@adobe.com` depuis votre adresse e-mail officielle pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité.

* **[Vous pouvez tirer parti du service de données de surveillance de l’utilisation réelle (RUM)](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)** pour activer la collecte côté client pour AEM as a Cloud Service.
La surveillance de l’utilisation en temps réel (RUM) offre un reflet plus précis des interactions des utilisateurs et utilisatrices, assurant une mesure fiable de l’engagement du site web. Il constitue une excellente opportunité d’obtenir des informations avancées sur les performances de votre page. Il est ainsi utile pour la clientèle qui utilise un réseau CDN géré ou non par Adobe. Par ailleurs, pour les personnes utilisant un réseau CDN non géré par Adobe, il est désormais possible de créer automatiquement des rapports sur le trafic, ce qui leur évite d’avoir à partager n’importe quel rapport sur le trafic avec Adobe.

  Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail à `aemcs-rum-adopter@adobe.com`, avec le nom de domaine de chacun des environnements pour lesquels vous souhaitez activer l’utilisation de RUM depuis votre adresse e-mail associée à votre Adobe ID. L’équipe produit d’Adobe activera alors le service de données de surveillance d’utilisation réelle (RUM) pour vous.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Programmes d’adoption précoce {#foundation-early-adopter}

#### Alertes relatives aux règles de filtrage du trafic (programme d’adoption précoce) {#traffic-filter-rules-alerts-early-adopter}

Les [Règles de filtrage du trafic](/help/security/traffic-filter-rules-including-waf.md) récemment publiées qui incluent les règles WAF (Web Application Firewall) sous licence optionnelle vous permettent de configurer le trafic qui doit être autorisé ou refusé.

Vous pouvez maintenant envoyer un e-mail à **<aemcs-cdn-config-adopter@adobe.com>** pour rejoindre le programme d’adoption précoce pour pouvoir recevoir une alerte chaque fois que vos règles de filtrage du trafic sont déclenchées. Les notifications par e-mail du Centre d’actions vous tiendront au courant lorsque certaines conditions de trafic se produisent afin que vous puissiez prendre les mesures appropriées.

#### Configuration du réseau CDN (Programme d’adoption précoce) {#cdn-config-early-adopter}

Outre les [Règles de filtrage du trafic](/help/security/traffic-filter-rules-including-waf.md) récemment publiées qui incluent les règles WAF (Web Application Firewall) sous licence optionnelle, il existe une opportunité d’utiliser le pipeline de configuration pour déclarer et déployer d’autres types de configuration du réseau CDN. [En savoir plus](/help/implementing/dispatcher/cdn-configuring-traffic.md) et rejoindre le programme d’adoption précoce en envoyant un e-mail à **<aemcs-cdn-config-adopter@adobe.com>** pour accéder aux éléments suivants :

* Redirections côté serveur 301/302
* Établir un proxy des requêtes en périphérie vers des origines arbitraires (comme les applications non AEM)
* Transformations d’URL
* Définir ou modifier des en-têtes de requête ou de réponse
* Pages d’erreur personnalisées lorsque le réseau CDN ne peut pas atteindre AEM.

#### Ingestion d’exécution d’Apache/du Dispatcher des mappages de réécriture (programme d’adoption précoce) {#apache-rewritemaps-early-adopter}

Comme pour AEM 6.5, Apache/le Dispatcher ingère des mappages de réécriture placées à un emplacement spécifique dans le référentiel de publication et les charge, sans nécessiter d’exécution de pipeline de niveau web. Un utilisateur professionnel ou une utilisatrice professionnelle peut ainsi déclarer des redirections à l’aide d’une interface utilisateur, comme celle proposée par le gestionnaire de mappage de redirection ACS Commons. Contactez **<aemcs-cdn-config-adopter@adobe.com>** pour plus d’informations.

#### Edge Side Includes (ESI) pour le chargement de contenu dynamique (programme d’adoption précoce) {#esi-early-adopter}

Le réseau CDN géré par Adobe prend désormais en charge Edge Side Includes (ESI), un langage de balisage pour l’assemblage de contenu web dynamique au niveau Edge. En incluant des extraits de code ESI, vous pouvez mettre en cache la page HTML globale sur le réseau CDN avec des TTL plus élevés, tout en récupérant plus fréquemment de l’origine les sections plus petites qui nécessitent des mises à jour à un rythme supérieur (TTL moins élevés). Veuillez contacter **<aemcs-cdn-config-adopter@adobe.com>** pour plus d’informations.

#### Prise en charge du RDE pour le code en front-end à l’aide des thèmes du site et des modèles de site (programme d’adoption précoce) {#rde-frontend-early-adopter}

Les [environnements de développement rapide (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md) prennent désormais en charge le code en front-end basé sur les [thèmes de site](/help/sites-cloud/administering/site-creation/site-themes.md) et les [modèles de site](/help/sites-cloud/administering/site-creation/site-templates.md), pour les utilisateurs et utilisatrices bénéficiant de l’adoption précoce. Avec les RDE, la prise en charge s’effectue à l’aide d’une directive de ligne de commande plutôt que d’un [pipeline front-end](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md). Veuillez contacter **<aemcs-rde-support@adobe.com>** pour essayer cette fonctionnalité et fournir des commentaires.

#### Amélioration de la journalisation des RDE (programme d’adoption précoce) {#rde-logging-early-adopter}

Lors du débogage du code dans un [environnement de développement rapide (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md), les développeurs et développeuses peuvent désormais configurer et diffuser plus efficacement les journaux à l’aide de la ligne de commande, et cela sans modifier les propriétés OSGi dans la gestion de versions. Les fonctionnalités incluent les suivantes :

* déclarer des niveaux de journal par niveau de package ou de classe ;
* personnaliser le format de sortie du journal ;
* diffuser plusieurs journaux en parallèle.

Veuillez contacter **<aemcs-rde-support@adobe.com>** pour essayer cette fonctionnalité et fournir des commentaires.

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
