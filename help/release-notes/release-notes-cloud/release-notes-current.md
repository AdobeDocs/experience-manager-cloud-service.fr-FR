---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 6c1320d43b551247e63962dd52ada58d463fb92e
workflow-type: tm+mt
source-wordcount: '1996'
ht-degree: 8%

---


# Notes de la mise à jour actuelle d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour générales de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes. par exemple, pour ceux de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de [!DNL Adobe Experience Manager] en tant que Cloud Service 2021.4.0 est le 6 mai 2021.
La version suivante (2021.5.0) sera publiée le 27 mai 2021.

## AEM as a Cloud Service Foundation{#aem-as-a-cloud-service-foundation}

### Nouveautés {#what-is-new-foundation}

* [Processus](/help/operations/replication.md#publish-content-tree-workflow)  Publier l’arborescence de contenu : une nouvelle étape et un nouveau modèle de processus offrent des performances accrues lors de la publication de hiérarchies de contenu profondes.

## [!DNL Adobe Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouveautés d’[!DNL Sites] {#what-is-new-sites}

* Points de terminaison GraphQL : il est désormais possible d’activer l’API GraphQL AEM pour les configurations AEM Sites individuelles et de créer des points de terminaison GraphQL personnalisés pour ces configurations à l’aide d’une nouvelle interface utilisateur de la console GraphQL. L’interface utilisateur permet également de gérer les points d’entrée GraphQL.

* Modèles de contenu, type de données Date&amp;Time amélioré : il est désormais possible de configurer le type de date Date&amp;Time afin de n’autoriser la création que des informations de date, d’heure ou de date et d’heure.

* Modèles de contenu, type de données Balises amélioré : il est désormais possible de configurer le type de données Balises pour permettre la création de balises uniques ou multiples.

* Modèles de contenu, nouveau type de données Espace réservé d’onglet : le nouveau type de données Espace réservé d’onglet permet de regrouper les types de données dans des sections qui seront rendues sous les onglets de l’éditeur de fragment de contenu.

### Bogues corrigés dans [!DNL Sites] {#bug-fixes-sites}

* Fragments de contenu : le déplacement de fragments de contenu ou de dossiers met désormais à jour les références imbriquées dans le fragment (CQ-4320815)

* GraphQL : les requêtes persistantes prennent désormais en charge les points de terminaison définis par l’utilisateur et spécifiques aux configurations AEM Sites (CQ-4315928).

## [!DNL Adobe Experience Manager Assets] as a  [!DNL Cloud Service] {#assets}

### Nouveautés d’[!DNL Assets] {#what-is-new-assets}

* [!DNL Experience Manager] ne archive pas les téléchargements de ressources uniques où le fichier d’origine est téléchargé. Cette amélioration permet des téléchargements plus rapides. Voir [téléchargement de ressources](/help/assets/download-assets-from-aem.md).

* Lorsque vous téléchargez une ressource via une option linkshare, vous pouvez désormais choisir de télécharger ou non les rendus. Auparavant, tous les rendus de ressources étaient téléchargés. Voir [options de téléchargement](/help/assets/download-assets-from-aem.md).

* Lors de l’exécution d’un contrôle de l’intégrité pour importer des ressources en bloc, Experience Manager fournit désormais plus d’informations sur les raisons des échecs. Voir [ingestion de ressources en bloc](/help/assets/add-assets.md#asset-bulk-ingestor).

* Lors de l’importation de ressources à l’aide de l’outil d’importation en bloc, les administrateurs ont désormais la possibilité de supprimer les fichiers source une fois l’importation réussie. Voir [ingestion de ressources en bloc](/help/assets/add-assets.md#asset-bulk-ingestor).

* Lors de la modification d’un schéma de métadonnées, un nouveau champ de sélecteur de chemin racine permet aux administrateurs d’effectuer rapidement et facilement la sélection. Cette amélioration permet de réduire le temps de configuration des métadonnées.

* Les métadonnées de nombreuses ressources peuvent être importées en bloc à l’aide d’un fichier CSV et exportées dans un fichier CSV. Le format de date par défaut est désormais `yyyy-MM-dd'T'HH:mm:ss.SSSXXX`. Les utilisateurs peuvent utiliser un format différent en mettant à jour l’en-tête de colonne. Par exemple, ajoutez `Date: DateFormat: yyyy-MM-dd'T'HH:mm:ssXXX` comme en-tête de colonne dans le fichier CSV au lieu du mot `Date`. Voir [Importation de métadonnées](/help/assets/metadata-import-export.md).

* Lorsque vous parcourez des ressources en mode Colonne, un indicateur visuel affiche l’état approuvé ou rejeté de chaque ressource.

* Lorsque vous parcourez des ressources en mode Colonne, un indicateur visuel s’affiche pour les ressources expirées.

* Un type de données de zone de texte est disponible dans l’éditeur de métadonnées [!DNL Assets]. Vous pouvez utiliser cette option pour permettre à vos utilisateurs de saisir des métadonnées dans un champ de texte à structure libre.

### Bogues corrigés dans [!DNL Assets] {#bug-fixes-assets}

* Lorsque vous tentez de déplacer plusieurs ressources ou dossiers, une erreur est consignée dans la console et l’opération de déplacement n’est pas terminée. L’opération de déplacement échoue si le titre ne peut pas être mis à jour. (CQ-4322080)

* Un champ de métadonnées peut être masqué en fonction d’une règle de sorte que, lorsqu’une condition prédéfinie est remplie, les métadonnées ne soient pas obligatoires. Toutefois, ces champs de métadonnées masqués s’affichent sous forme de champs obligatoires. (CQ-4321285)

* L’importation de métadonnées en bloc échoue en raison d’un format de date incorrect. (CQ-4319014)

* Lorsqu’une sélection est effectuée dans la page Propriétés pour mettre à jour les métadonnées, l’interface tarde à répondre lorsque de nombreuses options sont fournies par le schéma. (CQ-4318538)

* Lors de la mise à jour et de l’enregistrement de la valeur de métadonnées dans un champ de texte d’une seule ligne, les valeurs du menu déroulant sont supprimées, même si les modifications sont désactivées dans le menu déroulant. (CQ-4317077)

* Vous pouvez utiliser des points de suspension comme annotation pour passer en revue les ressources. Lorsqu’une petite ellipse est utilisée, elle chevauche le numéro de l’annotation dans la version imprimée. (CQ-4316792)

## [!DNL Adobe Experience Manager Forms] as a  [!DNL Cloud Service] {#forms}

### Nouveautés d’[!DNL Forms] {#what-is-new-forms}

Vous pouvez utiliser [AEM Forms as aCloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/home.html) pour créer des formulaires numériques, connecter des formulaires à des sources de données existantes, intégrer des formulaires à Adobe Sign pour ajouter des signatures électroniques aux formulaires, générer un document d’enregistrement (DoR) afin d’archiver les formulaires envoyés sous forme de fichiers PDF. Le service peut également convertir vos PDF forms existants en formulaires numériques. Outre les fonctionnalités AEM Forms standard, le service propose plusieurs fonctionnalités natives dans le cloud, telles que la mise à l’échelle automatique, le zéro temps d’arrêt pour les mises à niveau et l’environnement de développement natif dans le cloud. Lisez [cet article de blog](https://blog.adobe.com/en/publish/2021/03/11/experience-manager-forms-as-a-cloud-service.html) pour en savoir plus sur les fonctionnalités d’AEM Forms en tant que Cloud Service.

* **Utilisation de la méthode d’authentification d’identité des identifiants de gouvernement dans Adobe Sign enabled Adaptive Forms**

   Optimisé par des algorithmes d’apprentissage automatique avancés, le processus d’identification des gouvernements d’Adobe Sign permet aux entreprises du monde entier d’assurer une authentification de haute qualité de l’identité de leur destinataire. Désormais, vous pouvez utiliser la méthode d’authentification d’identité des identifiants de gouvernement dans Forms adaptatif activé par Adobe Sign.

   La carte d’identité officielle est une méthode d’authentification d’identité premium qui demande au destinataire de [télécharger l’image d’un document d’identité émis par le gouvernement (permis de conduire, carte d’identité nationale, passeport)](https://helpx.adobe.com/in/sign/using/adobesign-authentication-government-id.html), puis d’évaluer ce document pour s’assurer qu’il est authentique.

* **Prise en charge de l’utilisation de l’expérience de signature dans les formulaires pour les envois de formulaires adaptatifs asynchrones**

   Vous pouvez désormais utiliser l’expérience de signature dans le formulaire pour les envois asynchrones de formulaires adaptatifs. Vous pouvez également incorporer un formulaire adaptatif dans une page [!DNL Experience Manager Sites] et utiliser l’expérience de signature dans le formulaire pour les envois de formulaire adaptatif.

* **Prise en charge de l’utilisation d’une variable pour spécifier une pièce jointe lors du préremplissage d’un formulaire adaptatif pour une étape Affecter une tâche**

   Lors du préremplissage d’un formulaire adaptatif pour une étape Affecter une tâche, vous pouvez désormais utiliser une variable de type document pour sélectionner une pièce jointe d’entrée pour le formulaire adaptatif.

* **Prise en charge de l’utilisation de l’option littérale pour définir la valeur d’une variable de type JSON**

   Vous pouvez utiliser l’option littérale pour définir la valeur d’une variable de type JSON à l’étape de définition de la variable d’un workflow AEM. L’option littérale vous permet de spécifier un fichier JSON sous la forme d’une chaîne.

* **Utilisation de l’environnement de développement local pour créer un document d’enregistrement (DE)**

   Vous pouvez utiliser un XDP comme modèle de document d’enregistrement sur les instances de Cloud Service et AEM Forms comme SDK Cloud Service (environnement de développement local). Auparavant, la prise en charge était limitée aux instances de Cloud Service uniquement.

### Bogues corrigés dans [!DNL Forms] {#bug-fixes-forms}

* Lorsqu’un formulaire adaptatif configuré pour ne pas générer de document d’enregistrement est envoyé à un processus AEM configuré pour générer un document d’enregistrement, aucun message d’erreur n’est affiché et la tâche ne parvient pas à envoyer.

### Autres mises à jour {#misc-2021-04-0-forms}

* Pour faciliter la reconnaissance du contenu, le service génère désormais des miniatures en direct pour les fichiers XDP, PDF dynamique et de schéma.
* Permet de déplacer un fichier PDF vers un dossier placé dans l’interface utilisateur d’AEM Forms.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Prise en charge de l’UID de catégorie : cette option ouvre les intégrations commerciales tierces pour les systèmes qui utilisent des chaînes pour les ID de catégorie.

* Extension AEM pour PWA Studio, y compris exemple d’intégration

* Nouveau composant principal de navigation CIF qui étend le composant principal de navigation WCM

* Indicateur visuel pour les données de catalogue intermédiaires dans AEM storefront

* Le point de terminaison Commerce peut désormais être configuré via l’interface utilisateur de Cloud Manager.

### Correctifs {#bug-fixes-commerce}

* Le champ de catégorie racine n’était pas affiché sous l’onglet Commerce dans les propriétés de page des pages de catégorie.


## Cloud Manager {#cloud-manager}

Cette section présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service 2021.5.0 et 2021.4.0.

### Date de publication {#release-date-cm-may}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.5.0 est le 6 mai 2021.
La prochaine version est prévue pour le 3 juin 2021.

### Nouveautés {#what-is-new-may}

* La règle de qualité PackageOverlaps détecte désormais les cas où le même package a été déployé plusieurs fois, c’est-à-dire dans plusieurs emplacements incorporés, dans le même ensemble de packages déployé.

* Le point de terminaison du référentiel dans l’API publique inclut désormais l’URL Git.

* Le journal de déploiement téléchargé par un utilisateur de Cloud Manager sera plus informatif et comprendra désormais des détails sur les échecs et les scénarios de succès.

* Les échecs intermittents rencontrés lors de la publication du code vers le git d’Adobe ont maintenant été résolus.

* Le module complémentaire Commerce peut désormais être appliqué aux programmes Sandbox pendant le workflow Modifier le programme .

* L’expérience de modification du programme a été actualisée.

* Le tableau Noms de domaine de la page Détails de l’environnement affiche jusqu’à 250 noms de domaine par pagination.

* L’onglet Solutions des workflows Ajouter un programme et Modifier le programme affiche la solution, même si une seule solution est disponible pour le programme.

* Le message d’erreur dans le journal de l’étape de génération lorsque la version ne produisait aucun module de contenu déployé n’était pas clair.

### Correctifs {#bug-fixes-cm-may}

* Parfois, l’utilisateur peut voir un état &quot;principal&quot; vert en regard d’une Liste autorisée IP même lorsque cette configuration n’a pas été déployée.

* Au lieu de supprimer des variables &quot;supprimées&quot;, l’API des variables de pipelines ne les marquerait que avec le statut **DELETED**.

* Certains problèmes de qualité du type d’odeur de code affectaient incorrectement l’évaluation de fiabilité.

* Comme les domaines génériques ne sont pas pris en charge, l’interface utilisateur ne permet pas à l’utilisateur d’envoyer un domaine de caractères génériques.

* Lorsqu’une exécution de pipeline était lancée entre minuit et 1h du matin (UTC), il n’était pas garanti que la version d’artefact générée par Cloud Manager était supérieure à une version créée le jour précédent.

* Lors de la configuration du programme Sandbox, une fois que le projet avec un exemple de code a été créé, Gérer Git s’affiche sous la forme d’un lien à partir de la carte principale de la page Aperçu.

### Date de publication {#release-date-cm-april}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.4.0 est le 8 avril 2021.

### Nouveautés {#what-is-new-april}

* Mises à jour de l’interface utilisateur des workflows Ajouter et modifier le programme pour le rendre plus intuitif.

* Un utilisateur disposant des autorisations requises peut désormais envoyer le point de terminaison du commerce via l’interface utilisateur.

* Les variables d’environnement peuvent désormais être incluses dans un service spécifique, qu’il s’agisse de création ou de publication. Nécessite AEM version `2021.03.5104.20210328T185548Z` ou supérieure.

* Le bouton **Gérer Git** s’affiche sur la carte Pipelines même si aucun pipeline n’a été configuré.

* La version de l’archétype de projet AEM utilisé par Cloud Manager a été mise à jour vers la version 27.

* Les projets dans Adobe I/O Developer Console créés par Cloud Manager ne peuvent plus être modifiés ou supprimés involontairement.

* Lorsqu’un utilisateur ajoute un nouvel environnement, il est informé qu’une fois qu’un environnement est créé, il ne peut pas être déplacé vers une autre région.

* Les variables d’environnement peuvent désormais être incluses dans un service spécifique, qu’il s’agisse de création ou de publication. Nécessite AEM version 2021.03.5104.20210328T185548Z ou ultérieure.

* Le message d’erreur lors du démarrage d’un pipeline lorsqu’un environnement a été supprimé a été clarifié.

* Les lots OSGi fournis par les projets Eclipse sont désormais exclus de la règle `CQBP-84--dependencies`.

### Correctifs {#bug-fixes-cm-april}

* Lors de la modification de la page de contrôle de l’expérience d’un pipeline, un chemin d’entrée commençant par une barre oblique `( / )` n’entraîne plus le blocage de l’étape à l’état en attente.

* Lorsqu’un nouveau pipeline de production est créé, si aucun remplacement d’audit de contenu n’est ajouté par l’utilisateur, la page d’accueil par défaut n’a pas été contrôlée.

* Les problèmes pour `CloudServiceIncompatibleWorkflowProcess` étaient de gravité incorrecte dans le fichier CSV de problème téléchargeable.

* La vérification `Runmode` produisait des faux positifs sur les noeuds non-dossiers.

## Outil de transfert de contenu {#content-transfer-tool}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu v1.4.0 est le 11 mai 2021.

### Nouveautés {#what-is-new-ctt-may}

* Cette version de l’outil de transfert de contenu crée des rendus de texte pour les ressources migrées vers Cloud Service. Les rendus de texte sont nécessaires pour prendre en charge la recherche de texte intégral sur les ressources ingérées.
* Le nombre maximal de jeux de migration de l’outil de transfert de contenu qu’un utilisateur peut créer a été augmenté de 4 à 10.

### Correctifs {#bug-fixes-ctt-may}

* Plusieurs correctifs de bogues liés à la fonction d’actualisation automatique dans l’interface utilisateur de l’outil de transfert de contenu.
* L’outil de transfert de contenu avec `wipe=true` générait un index de compteur incorrect sur la cible. Ce problème a été résolu.

## Analyseur de bonnes pratiques {#best-practices-analyzer}

### Date de publication {#release-date-bpa}

La date de publication de la version 2.1.12 de l’analyseur des bonnes pratiques est le 12 avril 2021.

### Correctifs {#bug-fixes-bpa-april}

* Des lignes en double ont été affichées dans le rapport BPA. Ce problème a été résolu.
* L’interface utilisateur BPA de AEM version 6.4.2 renvoyait une erreur JS qui désactivait le bouton Générer le rapport. Ce problème a été résolu

