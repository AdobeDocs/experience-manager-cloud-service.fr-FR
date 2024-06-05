---
title: Notes de mise à jour de la version 2021.4.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour de la version 2021.4.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 775332b5-24ce-430e-97a2-6eeb80877c64
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1545'
ht-degree: 93%

---

# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour générales de la version actuelle (la plus récente) d’[!DNL Adobe Experience Manager] as a Cloud Service.

>[!NOTE]
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication d’[!DNL Adobe Experience Manager] as a Cloud Service version 2021.4.0 est le 6 mai 2021.
La version suivante (2021.5.0) sera publiée le 27 mai 2021.

## AEM as a Cloud Service Foundation{#aem-as-a-cloud-service-foundation}

### Nouveautés {#what-is-new-foundation}

* [Processus Publier l’arborescence de contenu](/help/operations/replication.md#publish-content-tree-workflow) – Une nouvelle étape et un nouveau modèle de processus offrent des performances accrues lors de la publication de hiérarchies de contenu profondes.

## [!DNL Adobe Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouveautés d’[!DNL Sites]  {#what-is-new-sites}

* Points d’entrée GraphQL – Il est désormais possible d’activer l’API AEM GraphQL pour les configurations d’AEM Sites individuelles et de créer des points d’entrée GraphQL personnalisés pour ces configurations à l’aide d’une nouvelle interface utilisateur de la console GraphQL. L’interface utilisateur permet également de gérer les points d’entrée GraphQL.

* Modèles de contenu, type de données Date&amp;Time amélioré – Il est désormais possible de configurer le type de date Date&amp;Time afin d’autoriser la création des informations de date uniquement, d’heure uniquement ou les informations de date et d’heure.

* Modèles de contenu, type de données Balises amélioré – Il est désormais possible de configurer le type de données Balises pour permettre la création de balises uniques ou multiples.

* Modèles de contenu, nouveau type de données Espace réservé d’onglet : le nouveau type de données Espace réservé d’onglet permet de regrouper les types de données dans des sections rendues sous des onglets dans l’éditeur de fragment de contenu.

### Bogues corrigés dans [!DNL Sites] {#bug-fixes-sites}

* Fragments de contenu – Le déplacement de fragments de contenu ou de dossiers met désormais à jour les références imbriquées dans le fragment (CQ-4320815).

* GraphQL – Les requêtes persistantes prennent désormais en charge les points d’entrée définis par l’utilisateur et spécifiques aux configurations AEM Sites (CQ-4315928).

## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouveautés d’[!DNL Assets]  {#what-is-new-assets}

* [!DNL Experience Manager] n’archive pas les téléchargements de ressources uniques où le fichier d’origine est téléchargé. Cette amélioration permet des téléchargements plus rapides.

* Lorsque vous téléchargez une ressource à l’aide d’un lien, vous pouvez désormais choisir de télécharger ou non les rendus. Auparavant, tous les rendus de ressources étaient téléchargés.

* Les administrateurs peuvent configurer [!DNL Experience Manager] pour supprimer la source des ressources après une ingestion de ressources en masse. Voir la section [Ingestion de ressources en bloc](/help/assets/add-assets.md#asset-bulk-ingestor).

* Lors de l’exécution d’un contrôle de l’intégrité pour importer des ressources en bloc, Experience Manager fournit désormais plus d’informations sur les raisons des échecs. Voir la section [Ingestion de ressources en bloc](/help/assets/add-assets.md#asset-bulk-ingestor).

* Lors de l’importation de ressources à l’aide de l’outil d’importation en bloc, les administrateurs ont désormais la possibilité de supprimer les fichiers source une fois l’importation réussie. Voir la section [Ingestion de ressources en bloc](/help/assets/add-assets.md#asset-bulk-ingestor).

* Lors de la modification d’un schéma de métadonnées, un nouveau champ de sélecteur de chemin racine permet aux administrateurs d’effectuer rapidement et facilement la sélection, et donc de réduire le temps de configuration.

* Lors de la modification d’un schéma de métadonnées, un type de données est ajouté, qui fournit une zone de texte de forme libre dans l’éditeur de métadonnées. Les utilisateurs peuvent utiliser cette zone de texte pour saisir du texte de forme libre en tant que métadonnées d’une ressource. Voir [Éditeur de schéma de métadonnées](/help/assets/metadata-schemas.md).

* Les métadonnées de nombreuses ressources peuvent être importées en bloc à l’aide d’un fichier CSV et exportées dans un fichier CSV. Le format de date par défaut est désormais `yyyy-MM-dd'T'HH:mm:ss.SSSXXX`. Les utilisateurs peuvent utiliser un format différent en mettant à jour l’en-tête de colonne. Par exemple, ajoutez `Date: DateFormat: yyyy-MM-dd'T'HH:mm:ssXXX` comme en-tête de colonne dans le fichier CSV au lieu du mot `Date`.

* Lorsque vous parcourez des ressources en mode Colonne, un indicateur visuel affiche l’état approuvé ou rejeté de chaque ressource.

* Lorsque vous parcourez des ressources en mode Colonne, un indicateur visuel s’affiche pour les ressources expirées.

### Bogues corrigés dans [!DNL Assets] {#bug-fixes-assets}

* Lorsque vous tentez de déplacer plusieurs ressources ou dossiers, une erreur est consignée dans la console et l’opération de déplacement n’est pas effectuée. L’opération de déplacement échoue si le titre ne peut pas être mis à jour. (CQ-4322080)

* Un champ de métadonnées peut être masqué en fonction d’une règle de sorte que, lorsqu’une condition prédéfinie est remplie, les métadonnées ne soient pas obligatoires. Toutefois, ces champs de métadonnées masqués s’affichent sous forme de champs obligatoires. (CQ-4321285)

* L’importation de métadonnées en bloc échoue en raison d’un format de date incorrect. (CQ-4319014)

* Lorsqu’une sélection est effectuée dans la page Propriétés pour mettre à jour les métadonnées, l’interface tarde à répondre lorsque de nombreuses options sont fournies par le schéma. (CQ-4318538)

* Lors de la mise à jour et de l’enregistrement de la valeur de métadonnées dans un champ de texte d’une seule ligne, les valeurs du menu de liste déroulante sont supprimées, même si les modifications sont désactivées dans le menu de liste déroulante. (CQ-4317077)

* Vous pouvez utiliser des points de suspension comme annotation pour passer en revue les ressources. Lorsqu’une petite ellipse est utilisée, elle chevauche le numéro de l’annotation dans la version imprimée. (CQ-4316792)

* L’option de publication rapide ne s’affiche pas lorsqu’une ressource est sélectionnée dans les résultats de recherche après avoir été recherchée. (CQ-4317748)

## [!DNL Adobe Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouveautés d’[!DNL Forms]  {#what-is-new-forms}

* **Utiliser la méthode d’authentification par pièce d’identité officielle dans les formulaires adaptatifs prenant en charge Adobe Sign**

  Optimisé par des algorithmes de machine learning avancés, le processus d’identification par pièce d’identité officielle d’Adobe Sign permet aux entreprises du monde entier de sécuriser une authentification de grande qualité de l’identité de leur personne destinataire. Vous pouvez maintenant utiliser la méthode d’authentification par pièce d’identité officielle dans les formulaires adaptatifs prenant en charge Adobe Sign.

  Le processus d’identification par pièce d’identité officielle est une méthode d’authentification d’identité de haute qualité qui demande aux personnes destinataires de [charger l’image d’un document d’identité émis par le gouvernement (permis de conduire, carte d’identité nationale, passeport)](https://helpx.adobe.com/fr/sign/using/adobesign-authentication-government-id.html), puis qui évalue ce document pour s’assurer qu’il est authentique.

* **Prise en charge de l’utilisation de l’expérience de signature dans les formulaires pour les envois asynchrones de formulaires adaptatifs**

  Vous pouvez maintenant utiliser l’expérience de signature dans les formulaires pour les envois asynchrones de formulaires adaptatifs. Vous avez également la possibilité d’incorporer un formulaire adaptatif dans une page [!DNL Experience Manager Sites] et d’utiliser l’expérience de signature dans les formulaires pour les envois de formulaires adaptatifs.

* **Prise en charge de l’utilisation d’une variable pour spécifier une pièce jointe lors du remplissage préalable d’un formulaire adaptatif pour une étape d’affectation d’une tâche**

  Lors du remplissage préalable d’un formulaire adaptatif pour une étape d’affectation d’une tâche, vous pouvez désormais utiliser une variable de type document pour sélectionner une pièce jointe d’entrée pour le formulaire adaptatif.

* **Prise en charge de l’utilisation de l’option littérale pour définir la valeur d’une variable de type JSON**

  Vous pouvez utiliser l’option littérale pour définir la valeur d’une variable de type JSON à l’étape de définition de la variable d’un processus AEM. L’option littérale vous permet de spécifier un fichier JSON sous la forme d’une chaîne.

* **Utilisation de l’environnement de développement local pour créer un document d’enregistrement**

  Vous pouvez utiliser un fichier XDP comme modèle de document d’enregistrement sur les instances de Cloud Service et dans le SDK AEM Forms as a Cloud Service (environnement de développement local). Auparavant, la prise en charge était limitée uniquement aux instances de Cloud Service.

### Bogues corrigés dans [!DNL Forms] {#bug-fixes-forms}

* Lorsqu’un formulaire adaptatif configuré pour ne pas générer de document d’enregistrement est envoyé à un workflow AEM configuré pour générer un document d’enregistrement, aucun message d’erreur ne s’affiche et la tâche ne parvient pas à effectuer l’envoi.

### Autres mises à jour {#misc-2021-04-0-forms}

* Pour faciliter la reconnaissance du contenu, le service génère maintenant des vignettes dynamiques pour les fichiers de schéma, XDP et PDF dynamiques.
* Ajout de la possibilité de déplacer un fichier PDF vers un dossier placé dans l’interface utilisateur d’AEM Forms.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Prise en charge de l’UID de catégorie – Cette option ouvre les intégrations commerciales tierces pour les systèmes qui utilisent des chaînes pour les ID de catégorie.

* Extension AEM pour PWA Studio, avec un exemple d’intégration

* Nouveau composant principal de navigation CIF qui étend le composant principal de navigation WCM

* Indicateur visuel pour les données de catalogue intermédiaires dans AEM Storefront

* Le point d’entrée Commerce peut désormais être configuré via l’interface utilisateur de Cloud Manager.

### Correctifs {#bug-fixes-commerce}

* Le champ de catégorie racine n’était pas affiché sous l’onglet Commerce dans les propriétés de page des pages de catégorie.

## Cloud Manager {#cloud-manager}

Cette section présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.4.0.

### Date de publication {#release-date-cm-april}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.4.0 est le 8 avril 2021.
La prochaine version est prévue pour le 6 mai 2021.

### Nouveautés {#what-is-new-april}

* Mises à jour de l’interface utilisateur des workflows Ajouter et Modifier le programme pour la rendre plus intuitive.

* Un utilisateur disposant des autorisations requises peut désormais envoyer le point d’entrée de Commerce grâce à l’interface utilisateur.

* Les variables d’environnement peuvent désormais être incluses dans un service spécifique, qu’il s’agisse de création ou de publication. Nécessite AEM version `2021.03.5104.20210328T185548Z` ou supérieure.

* Le bouton **Gérer Git** s’affiche sur la carte Pipelines même si aucun pipeline n’a été configuré.

* L’archétype de projet AEM utilisé par Cloud Manager a été mis à jour à la version 27.

* Il n’est plus possible de modifier ni de supprimer involontairement les projets créés par Cloud Manager dans Adobe I/O Developer Console.

* Lorsqu’un utilisateur ajoute un nouvel environnement, il est informé qu’une fois un environnement créé, il ne peut pas être déplacé vers une autre région.

* Les variables d’environnement peuvent désormais être incluses dans un service spécifique, qu’il s’agisse de création ou de publication. Nécessite AEM version 2021.03.5104.20210328T185548Z, ou ultérieure.

* Le message d’erreur, lors de la suppression d’un environnement au démarrage d’un pipeline, a été clarifié.

* Les lots OSGi fournis par les projets Eclipse sont désormais exclus de la règle `CQBP-84--dependencies`.

### Correctifs {#bug-fixes-cm-april}

* Lors de la modification de la page de contrôle de l’expérience d’un pipeline, un chemin d’entrée commençant par une barre oblique `( / )` n’entraîne plus le blocage de l’étape à l’état En attente.

* Lorsqu’un pipeline de production est créé, si aucun remplacement d’audit de contenu n’est ajouté par l’utilisateur, la page d’accueil par défaut n’a pas été contrôlée.

* La gravité des problèmes de `CloudServiceIncompatibleWorkflowProcess` était incorrecte dans le fichier CSV de problème téléchargeable.

* La vérification `Runmode` produisait des faux positifs sur les nœuds autres que des dossiers.

## Analyseur des bonnes pratiques {#best-practices-analyzer}

### Date de publication {#release-date-bpa}

La date de publication de l’analyseur de bonnes pratiques v2.1.12 est le 12 avril 2021.

### Correctifs {#bug-fixes-bpa-april}

* Des lignes en double étaient affichées dans le rapport BPA. Ce problème a été résolu.
* L’interface utilisateur BPA d’AEM version 6.4.2 renvoyait une erreur JS qui désactivait le bouton Générer le rapport. Ce problème a été résolu
