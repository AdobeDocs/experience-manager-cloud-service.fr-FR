---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
translation-type: tm+mt
source-git-commit: 8ca3fe045aba4ec9e546fee0700d1bec08e337fb
workflow-type: tm+mt
source-wordcount: '1879'
ht-degree: 5%

---


# Notes de mise à jour actuelles pour[!DNL Adobe Experience Manager]as a Cloud Service {#release-notes}

La section suivante décrit les Notes de mise à jour générales de la version actuelle (dernière) de [!DNL Experience Manager] en tant que Cloud Service.

>[!NOTE]
>A partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, pour ceux de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d&#39;informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de [!DNL Adobe Experience Manager] en tant que Cloud Service 2021.4.0 est le 6 mai 2021.
La version suivante (2021.5.0) sera publiée le 27 mai 2021.

## AEM as a Cloud Service Foundation{#aem-as-a-cloud-service-foundation}

### Nouveautés {#what-is-new-foundation}

* [Processus](/help/operations/replication.md#publish-content-tree-workflow)  de publication de l’arborescence de contenu : une nouvelle étape et un nouveau modèle de processus offrent des performances accrues lors de la publication de hiérarchies de contenu profondes.

## [!DNL Adobe Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouveautés de [!DNL Sites] {#what-is-new-sites}

* Points de terminaison GraphQL : il est maintenant possible d&#39;activer l&#39;API GraphQL AEM pour les configurations AEM Sites individuelles et de créer des points de terminaison GraphQL personnalisés pour ces configurations à l&#39;aide d&#39;une nouvelle interface utilisateur de la console GraphQL. L’interface utilisateur permet également de gérer les points de terminaison GraphQL.

* Modèles de contenu, type de données Date&amp;Heure amélioré : il est désormais possible de configurer le type de date Date&amp;Heure afin de n’autoriser la création que de la date, de l’heure ou de la date et de l’heure.

* Modèles de contenu, type de données Balises amélioré : il est désormais possible de configurer le type de données Balises pour permettre la création de balises uniques ou multiples.

* Modèles de contenu, nouveau type de données d’espace réservé à l’onglet : le nouveau type de données d’espace réservé à l’onglet permet de regrouper les types de données dans des sections qui seront rendues sous des onglets dans l’éditeur de fragments de contenu.

### Correctifs de bogues dans [!DNL Sites] {#bug-fixes-sites}

* Fragments de contenu : le déplacement de fragments ou de dossiers de contenu met à jour les références imbriquées dans le fragment (CQ-4320815)

* GraphQL : les requêtes persistantes prennent désormais en charge les points de terminaison définis par l’utilisateur et spécifiques aux configurations AEM Sites (CQ-4315928).

## [!DNL Adobe Experience Manager Assets] comme  [!DNL Cloud Service] {#assets}

### Nouveautés de [!DNL Assets] {#what-is-new-assets}

* [!DNL Experience Manager] n’archive pas les téléchargements de ressources uniques où le fichier d’origine est téléchargé. Cette amélioration permet des téléchargements plus rapides.

* Lorsqu’un fichier est téléchargé via l’option linkshare, vous pouvez désormais choisir de télécharger ou non les rendus. Auparavant, tous les rendus de ressource étaient téléchargés.

* Les administrateurs peuvent configurer [!DNL Experience Manager] pour supprimer la source des ressources après une assimilation de ressources en vrac. Voir [importation de ressources en vrac](/help/assets/add-assets.md#asset-bulk-ingestor).

* Lors de l’exécution d’un contrôle d’intégrité pour importer des actifs en vrac, le Experience Manager fournit désormais davantage d’informations sur les raisons des échecs. Voir [importation de ressources en vrac](/help/assets/add-assets.md#asset-bulk-ingestor).

* Lors de l’importation de fichiers à l’aide de l’outil d’importation en bloc, les administrateurs peuvent désormais supprimer les fichiers source une fois l’importation réussie. Voir [importation de ressources en vrac](/help/assets/add-assets.md#asset-bulk-ingestor).

* Lors de la modification d’un schéma de métadonnées, un nouveau champ de sélecteur de chemin racine permet aux administrateurs d’effectuer rapidement et facilement la sélection, réduisant ainsi le temps de configuration.

* Les métadonnées de nombreux fichiers peuvent être importées en bloc à l’aide d’un fichier CSV et être exportées dans un fichier CSV. Le format de date par défaut est désormais `yyyy-MM-dd'T'HH:mm:ss.SSSXXX`. Les utilisateurs peuvent utiliser un format différent en mettant à jour l’en-tête de colonne. Par exemple, ajoutez `Date: DateFormat: yyyy-MM-dd'T'HH:mm:ssXXX` comme en-tête de colonne dans le fichier CSV au lieu du mot `Date`.

* Lorsque vous parcourez des ressources dans la vue des colonnes, un indicateur visuel affiche l’état approuvé ou rejeté de chaque ressource.

* Lorsque vous parcourez des ressources dans la vue des colonnes, un indicateur visuel s’affiche pour les ressources arrivées à expiration.

### Correctifs de bogues dans [!DNL Assets] {#bug-fixes-assets}

* Lors de la tentative de déplacement de plusieurs fichiers ou dossiers, une erreur est consignée dans la console et l’opération de déplacement n’est pas terminée. L&#39;opération de déplacement échoue si le titre ne peut pas être mis à jour. (CQ-4322080)

* Un champ de métadonnées peut être masqué en fonction d’une règle de sorte que, lorsqu’une condition prédéfinie est remplie, les métadonnées ne sont pas obligatoires. Toutefois, ces champs de métadonnées masqués s’affichent sous forme de champs obligatoires. (CQ-4321285)

* L&#39;importation des métadonnées en bloc échoue en raison d&#39;un format de date incorrect. (CQ-4319014)

* Lorsqu’une sélection est effectuée dans la page Propriétés pour mettre à jour les métadonnées, l’interface tarde à répondre lorsqu’il existe de nombreuses options fournies par le schéma. (CQ-4318538)

* Lors de la mise à jour et de l’enregistrement de la valeur de métadonnées dans un champ de texte d’une seule ligne, les valeurs du menu déroulant sont supprimées, même si les modifications sont désactivées dans le menu déroulant. (CQ-4317077)

* Vous pouvez utiliser des points de suspension comme annotation pour consulter des fichiers. Lorsqu&#39;une petite ellipse est utilisée, elle chevauche le numéro de l&#39;annotation dans la version imprimée. (CQ-4316792)

## [!DNL Adobe Experience Manager Forms] comme  [!DNL Cloud Service] {#forms}

### Nouveautés de [!DNL Forms] {#what-is-new-forms}

Vous pouvez utiliser [AEM Forms en tant que Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/home.html) pour créer des formulaires numériques, connecter des formulaires à des sources de données existantes, intégrer des formulaires à Adobe Sign pour ajouter des signatures électroniques aux formulaires, générer un Document d’enregistrement (DE) pour archiver les formulaires envoyés en tant que fichiers PDF. Le service peut également convertir vos PDF forms existants en formulaires numériques. Outre les fonctionnalités standard d’AEM Forms, le service offre plusieurs fonctionnalités natives du cloud, telles que la mise à l’échelle automatique, un temps d’arrêt zéro pour les mises à niveau et un environnement de développement natif du cloud. Lisez [ce billet de blog](https://blog.adobe.com/en/publish/2021/03/11/experience-manager-forms-as-a-cloud-service.html) pour en savoir plus sur les capacités et les fonctionnalités de AEM Forms en tant que Cloud Service.

* **Utiliser la méthode d&#39;authentification d&#39;identité d&#39;identification de l&#39;administration dans le Forms adaptatif activé par Adobe Sign**

   Optimisé par des algorithmes d’apprentissage automatique élaborés, le processus d’identification du gouvernement de l’Adobe Sign permet aux sociétés du monde entier d’obtenir une authentification de haute qualité de leur identité de destinataire. Désormais, vous pouvez utiliser la méthode d’authentification de l’identité de l’ID de gouvernement dans Adaptive Forms compatible Adobe Sign.

   L’ID gouvernemental est une méthode d’authentification d’identité haut de gamme qui demande au destinataire de [télécharger l’image d’un document d’identité délivré par le gouvernement (permis de conduire, carte d’identité nationale, passeport)](https://helpx.adobe.com/in/sign/using/adobesign-authentication-government-id.html), puis d’évaluer ce document pour s’assurer qu’il est authentique.

* **Prise en charge de l’utilisation de la signature dans les formulaires pour les envois de formulaires adaptatifs asynchrones**

   Vous pouvez désormais utiliser l’expérience de signature dans un formulaire pour les envois asynchrones de formulaires adaptatifs. Vous pouvez également incorporer un formulaire adaptatif dans une page [!DNL Experience Manager Sites] et utiliser l’expérience de signature dans un formulaire pour les envois de formulaire adaptatif.

* **Prise en charge de l’utilisation d’une variable pour spécifier une pièce jointe lors du préremplissage d’un formulaire adaptatif pour une étape d’affectation de Tâche**

   Lors du préremplissage d’un formulaire adaptatif pour une étape d’affectation de Tâche, vous pouvez désormais utiliser une variable de type de document pour sélectionner une pièce jointe d’entrée pour le formulaire adaptatif.

* **Prise en charge de l’utilisation de l’option littérale pour définir la valeur d’une variable de type JSON**

   Vous pouvez utiliser l’option littérale pour définir la valeur d’une variable de type JSON dans l’étape de variable définie d’un flux de travail AEM. L’option littérale vous permet de spécifier un fichier JSON sous la forme d’une chaîne.

* **Utiliser l&#39;environnement de développement local pour créer un Document d&#39;enregistrement (DE)**

   Vous pouvez utiliser un modèle XDP comme modèle Document d’enregistrement sur les instances de Cloud Service et AEM Forms comme SDK Cloud Service (environnement de développement local). Auparavant, la prise en charge était limitée aux instances de Cloud Service uniquement.

### Correctifs de bogues dans [!DNL Forms] {#bug-fixes-forms}

* Lorsqu’un formulaire adaptatif configuré pour ne pas générer de Document d’enregistrement est envoyé à un flux de travail AEM configuré pour générer un Document d’enregistrement, aucun message d’erreur ne s’affiche et la tâche ne parvient pas à envoyer.

### Autres mises à jour {#misc-2021-04-0-forms}

* Pour faciliter la reconnaissance du contenu, le service génère désormais des vignettes dynamiques pour les fichiers XDP, PDF dynamiques et de Schéma.
* Ajoutez la possibilité de déplacer un fichier PDF vers un dossier placé dans l’interface utilisateur AEM Forms.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Prise en charge de l’identifiant d’utilisateur de catégorie - Déverrouille les intégrations commerciales tierces pour les systèmes qui utilisent des chaînes pour les identifiants de catégorie

* Extension AEM pour PWA Studio incl. exemple d’intégration

* Nouveau composant de base de navigation CIF qui étend le composant de base de navigation WCM

* Indicateur visuel pour les données de catalogue par étapes dans AEM vitrine

* Le point de terminaison commercial peut désormais être configuré via l’interface utilisateur de Cloud Manager.

### Correctifs {#bug-fixes-commerce}

* Le champ de catégorie racine n’était pas affiché sous l’onglet Commerce dans les propriétés de page des pages de catégorie.


## Cloud Manager {#cloud-manager}

Cette section décrit les Notes de mise à jour de Cloud Manager dans AEM en tant que Cloud Service 2021.5.0 et 2021.4.0.

### Date de publication {#release-date-cm-may}

La date de publication de Cloud Manager en AEM Cloud Service 2021.5.0 est le 06 mai 2021.
La prochaine version est prévue pour le 3 juin 2021.

### Nouveautés {#what-is-new-may}

* La règle de qualité PackageOverlaps détecte désormais les cas où le même package a été déployé plusieurs fois, c’est-à-dire dans plusieurs emplacements incorporés, dans le même jeu de packages déployé.

* Le point de terminaison du référentiel dans l’API publique inclut désormais l’URL Git.

* Le journal de déploiement téléchargé par un utilisateur de Cloud Manager sera plus instructif et comprendra désormais des détails sur les échecs et les scénarios de réussite.

* Les échecs intermittents rencontrés lors de la publication du code à l&#39;Adobe git ont maintenant été résolus.

* Le module complémentaire Commerce peut désormais être appliqué aux programmes Sandbox pendant le processus de modification du programme.

* L’expérience Modifier le programme a été actualisée.

* Le tableau Noms de domaine de la page Détails de l&#39;Environnement affiche jusqu&#39;à 250 noms de domaine par pagination.

* L&#39;onglet Solutions des workflows de Programme d&#39;Ajoute et de Programme de modification affiche la solution, même si une seule solution est disponible pour le Programme.

* Le message d’erreur dans le journal des étapes de génération lorsque la génération n’a pas produit de packages de contenu déployés n’était pas clair.

### Correctifs {#bug-fixes-cm-may}

* Il arrive que l’utilisateur voit un état &quot;principal&quot; vert en regard d’une Liste autorisée IP, même si cette configuration n’a pas été déployée.

* Au lieu de supprimer les variables &quot;supprimées&quot;, l&#39;API des variables de pipeline les marquerait uniquement avec l&#39;état **DELETED**.

* Certains problèmes de qualité du type de code ont eu une incidence incorrecte sur la cote de fiabilité.

* Comme les domaines génériques ne sont pas pris en charge, l’interface utilisateur empêche l’utilisateur d’envoyer un domaine générique.

* Lorsqu’une exécution de pipeline a été démarrée entre minuit et 1h heure UTC, la version d’artefact générée par Cloud Manager n’était pas garantie supérieure à une version créée le jour précédent.

* Lors de la configuration du programme Sandbox, une fois que le projet avec un exemple de code a été créé, Gérer Git s&#39;affiche comme un lien à partir de la carte de héros dans la page Aperçu.

### Date de publication {#release-date-cm-april}

La date de publication de Cloud Manager en tant que Cloud Service 2021.4.0 est le 08 avril 2021.

### Nouveautés {#what-is-new-april}

* L’interface utilisateur met à jour les workflows d’Ajoute et de modification de Programme pour les rendre plus intuitifs.

* Un utilisateur disposant des autorisations requises peut désormais envoyer le point de terminaison du commerce via l’interface utilisateur.

* Les variables d’Environnement peuvent désormais être étendues à un service spécifique, qu’il s’agisse de l’auteur ou de la publication. Requiert AEM version `2021.03.5104.20210328T185548Z` ou supérieure.

* Le bouton **Gérer Git** s&#39;affiche sur la carte Pipelines même si aucun pipeline n&#39;a été configuré.

* La version de l’archétype de projet AEM utilisée par Cloud Manager a été mise à jour vers la version 27.

* Les projets de la console de développement des Adobes I/O créés par Cloud Manager ne peuvent plus être modifiés ou supprimés involontairement.

* Lorsqu’un utilisateur ajoute un nouvel environnement, il est informé qu’une fois qu’un environnement est créé, il ne peut plus être déplacé dans une autre région.

* Les variables d’Environnement peuvent désormais être étendues à un service spécifique, qu’il s’agisse de l’auteur ou de la publication. Requiert AEM version 2021.03.5104.20210328T185548Z ou supérieure.

* Le message d&#39;erreur lors du démarrage d&#39;un pipeline lorsqu&#39;un environnement a été supprimé a été clarifié.

* Les lots OSGi fournis par les projets Eclipse sont maintenant exclus de la règle `CQBP-84--dependencies`.

### Correctifs {#bug-fixes-cm-april}

* Lors de la modification de la page de contrôle d’expérience d’un pipeline, un chemin d’entrée commençant par une barre oblique `( / )` n’entraîne plus l’blocage de l’étape dans l’état en attente.

* Lors de la création d&#39;un nouveau pipeline de production, si aucun remplacement de contrôle du contenu n&#39;est ajouté par l&#39;utilisateur, la page d&#39;accueil par défaut n&#39;a pas été contrôlée.

* La gravité des problèmes de `CloudServiceIncompatibleWorkflowProcess` était incorrecte dans le fichier CSV de publication téléchargeable.

* La vérification `Runmode` produisait des faux positifs sur les noeuds non-dossiers.

## Analyseur de bonnes pratiques {#best-practices-analyzer}

### Date de publication {#release-date-bpa}

La date de publication pour la version 2.1.12 de Best Practices Analyzer est le 12 avril 2021.

### Correctifs {#bug-fixes-bpa-april}

* Des lignes de duplicata ont été vues dans le BPA rapporté. Ce problème a été résolu.
* L&#39;interface utilisateur BPA de AEM version 6.4.2 affichait une erreur JS qui désactivait le bouton Générer le rapport. Ce problème a été résolu

