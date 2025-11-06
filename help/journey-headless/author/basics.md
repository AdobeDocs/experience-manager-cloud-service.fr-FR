---
title: Découvrez les bases de la création
description: Découvrez les concepts et les mécanismes de la création de contenu pour votre CMS Headless à l’aide de fragments de contenu.
exl-id: 3eca973f-b210-41bb-98da-ecbd2bae9803
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1733'
ht-degree: 98%

---

# Principes de base de la création en découplage avec AEM {#author-headless-basics}

## Un peu d’histoire… {#story-so-far}

Au début du [Parcours de création de contenu découplé AEM](overview.md), l’[Introduction](introduction.md) présentait les concepts de base et la terminologie relatifs à la création découplée.

Cet article s’appuie sur ces éléments afin que vous compreniez comment créer votre propre contenu pour votre projet AEM découplé.

## Objectif {#objective}

* **Audience** : débutant
* **Objectif** : présentation des principes de base de la création CMS découplée :
   * Présentation de la création avec AEMaaCS
   * Présentation des fragments de contenu

## Manipulation de base {#basic-handling}

Avant de vous familiariser avec les fragments de contenu, voici une introduction (très) rapide à l’utilisation d’AEM...mais rien ne remplace vraiment l’expérience de connexion et d’utilisation du système.

### Création, prévisualisation et publication {#author-preview-publish}

Une installation AEM se compose généralement de trois environnements :

* Création
* Publication
* Prévisualisation

Vous vous connectez et utilisez l’environnement de création pour générer votre contenu. Une fois prêt, vous publiez votre contenu afin qu’il soit largement disponible. Pour les applications découplées, il serait destiné aux autres applications, pour les pages web, il serait destiné aux lecteurs sur le web.

Pour plus d’informations, consultez les concepts de création.

Dans la console **Fragments de contenu**, vous pouvez également publier sur le **Service de prévisualisation**, pour le test et la prévisualisation, avant la publication. Voir Publication et prévisualisation d’un fragment.

### Connexion {#signing-in}

Comme pour la plupart des systèmes, vous devez vous connecter. En tant qu’auteur ou autrice, vous recevez les informations suivantes :

* Nom de l’utilisateur (compte)
* Mot de passe
* Lien d’accès à l’écran de connexion

Votre compte a été configuré avec les privilèges dont vous avez besoin. Si vous rencontrez des problèmes, nous vous recommandons de contacter votre équipe interne d’assistance projet.

### Navigation {#navigation}

La première fois que vous vous connectez, un petit tutoriel en ligne vous présentera certaines des principales fonctionnalités de l’interface utilisateur.

Vous pouvez ensuite utiliser le panneau de navigation pour accéder aux principales zones d’AEM. Pour les fragments de contenu, vous utilisez la console **Fragments de contenu** (pour certaines actions, vous utiliserez également la console **Ressources**).

Vous pouvez ouvrir le panneau de navigation en sélectionnant l’icône d’Adobe en haut à gauche, puis la petite icône en forme de boussole.

>[!NOTE]
>Bien que les fragments de contenu soient une fonctionnalité d’AEM **Sites**, ils sont enregistrés en tant que **Ressources**. Ce détail technique ne devrait pas vous affecter, mais il peut s’avérer utile de le savoir.

Dans la console Fragments de contenu , vous pouvez sélectionner des dossiers dans le panneau de gauche pour accéder à votre fragment de contenu. Vous pouvez également filtrer et/ou rechercher.

![Console Fragments de contenu](/help/sites-cloud/administering/content-fragments/assets/cf-managing-console-filter.png)

### Actions, sélection, affichage {#actions-selecting-viewing}

La console **Fragments de contenu** met à disposition différentes actions pour vos fragments de contenu à partir de la barre d’outils :

* **Ouvrir dans Assets**
* **Créer**
* La colonne **Référencé par** fournit également un lien direct pour afficher toutes les références parentes de ce fragment. Cela inclut notamment le référencement de fragments de contenu, de fragments d’expérience et de pages.
* Placez le pointeur de la souris sur le nom du dossier pour afficher le chemin d’accès JCR.

Une fois le fragment sélectionné, d’autres actions sont disponibles (selon les besoins) :

* **Ouvrir**
* **Publier** (et **Dépublier**)
* **Gérer les balises**
* **Copier**
* **Remplacer**
* **Déplacer**
* **Renommer**
* **Supprimer**

>[!NOTE]
>
>Des actions telles que Publier, Dépublier, Supprimer, Déplacer, Renommer ou Copier déclenchent un traitement asynchrone. Il est possible de surveiller la progression de ce traitement via l’interface utilisateur des traitements asynchrones AEM.

## Créer des fragments de contenu {#authoring-content-fragments}

Malgré cette introduction très rapide à l’interface utilisateur d’AEM, j’espère que vous avez eu la chance de l’essayer. Maintenant, revenons-en à votre véritable point d’intérêt : les fragments de contenu découplé.

Nous devrons passer en revue les éléments du début à la fin, mais il se peut que votre instance dispose de dossiers ou de fragments déjà créés, et qu’ils se trouvent à des emplacements différents. Les principes restent les mêmes.

### Organisation et navigation {#organizing-and-navigating}

À moins que vous n’ayez que très peu de fragments de contenu, vous souhaiterez les organiser afin que vous (et d’autres) puissiez les retrouver facilement.

#### Création d’un dossier {#creating-folder}

Pour ce faire, créez une série de dossiers dans la section **Fichiers** de la console **Ressources**. Sélectionnez l’option **Créer** (en haut à droite), puis **Dossier** :

![Option Créer un dossier](/help/journey-headless/author/assets/headless-journey-author-folder-01.png)

Une boîte de dialogue s’ouvre dans laquelle vous pouvez saisir les informations ; confirmez ensuite en sélectionnant **Créer** :

![Boîte de dialogue Créer un dossier](/help/journey-headless/author/assets/headless-journey-author-folder-02.png)

#### Utilisation des chemins et des balises pour limiter les modèles de fragment de contenu disponibles dans le dossier {#tags-paths-for-models-in-folder}

Cette section est d’un niveau légèrement plus avancé. Vous n’en avez pas vraiment besoin si vous venez juste de commencer, mais c&#39;est *très* utile lorsque vous avez de nombreux fragments. Il est donc bon de savoir qu’elle est là, même si vous ne l’exploiterez pas encore à son plein potentiel.

Votre architecte de contenu aura créé tous les modèles de fragment de contenu requis pour votre projet actuel, ainsi que peut-être d’autres projets. Pour vous simplifier les choses ainsi qu’aux autres auteurs, vous pouvez limiter la liste des modèles disponibles pour un dossier spécifique.

Après avoir créé votre dossier, vous pouvez ouvrir ses **Propriétés**. Cette section comporte différents onglets avec des informations et des détails de configuration sur le dossier. Pour les fragments de contenu, vous pouvez notamment utiliser l’onglet **Politiques** pour définir des chemins d’accès ou des balises spécifiques pour ce dossier. Cette configuration limite les modèles de fragment de contenu disponibles dans le dossier, car cela signifie que les modèles de fragment de contenu doivent satisfaire à ces exigences avant de pouvoir être utilisés pour générer des fragments dans ce dossier.

![Création de propriétés de dossier – Politiques](/help/journey-headless/author/assets/headless-journey-author-folder-04.png)

>[!NOTE]
>
>Pour plus d’informations, reportez-vous à la section Modèles de fragment de contenu – Autorisation de modèles de fragments de contenu dans votre dossier de ressources.

Vous pouvez ensuite parcourir ces dossiers pour créer et modifier vos fragments de contenu.

#### Juste au cas où – Configuration des services cloud de dossiers {#cloud-services-folder}

Juste au cas où...

Vous recevrez probablement un dossier initial dans lequel vous pourrez créer vos dossiers. En effet, certains détails de configuration doivent être appliqués (généralement par un développeur ou un administrateur système) au dossier racine. Cela ne vous intéressera probablement pas mais vous pouvez, au besoin, vérifier la **Configuration** dans les **Services cloud** du dossier **Propriétés** :

![Création de propriétés de dossier – Configuration](/help/journey-headless/author/assets/headless-journey-author-folder-03.png)

>[!NOTE]
>
>Pour en savoir plus, consultez Application de la configuration à votre dossier de ressources.

### Création d’un fragment de contenu {#creating-fragment}

Dans la console **Fragments de contenu**, vous pouvez utiliser **Créer** pour ouvrir la boîte de dialogue **Nouveau fragment de contenu** :

![Console Fragments de contenu - Création d’un fragment](/help/sites-cloud/administering/content-fragments/assets/cfc-console-create.png)

Spécifiez les éléments suivants :

* **Emplacement**
* **Modèle de fragment de contenu**
* **Titre**
* **Nom**
* **Description**

Confirmez en cliquant sur **Créer** ou **Créer et ouvrir**.

### Modifier un fragment {#editing-fragment}

Vous pouvez ouvrir un fragment immédiatement après sa création ou en le sélectionnant dans la console Fragments de contenu (également disponible dans la console Ressources).

>[!NOTE]
>
>Les fragments de contenu sont une fonctionnalité de sites, mais sont stockés sous la forme **Ressources**.
>
>Il existe deux éditeurs pour la création de fragments de contenu.
>
>* Le nouvel éditeur, principalement accessible à partir du **Fragments de contenu** console.
>* L’éditeur d’origine, principalement accessible à partir de **Ressources** console.

Lorsque l’éditeur s’ouvre pour la première fois, les éléments suivants s’affichent :

* barre d’outils supérieure : pour obtenir des informations clés et des actions
   * lien vers la console de fragments de contenu (icône Accueil)
   * informations sur le modèle et le dossier
   * Liens vers Aperçu ; si le modèle d’URL d’aperçu par défaut est configuré pour le modèle
   * Actions Publier et Annuler la publication
   * une option pour afficher tout **Références parentes** (icône de lien)
   * le fragment **État**, et les dernières informations enregistrées ;
   * bascule pour passer à l’éditeur d’origine (basé sur les ressources)
* panneau de gauche : affiche la variable **Variations** pour le fragment de contenu et son **Champs**:
   * ces liens peuvent être utilisés pour parcourir la structure de fragment de contenu
* panneau de droite : présente des onglets présentant les propriétés (métadonnées) et les balises, des informations sur l’historique des versions et des informations relatives aux copies de langue.
   * dans le **Propriétés** vous pouvez mettre à jour l’onglet **Titre** et **Description** pour le fragment, ou **Variation**
* panneau central : affiche les champs réels et le contenu de la variation sélectionnée.
   * permet de modifier le contenu.
   * if **Espace réservé de tabulation** Les champs sont définis dans le modèle qu’ils sont affichés ici et peuvent être utilisés pour naviguer

Par exemple, un fragment peut :

* Nécessite plusieurs informations, dont certaines avec un type spécifique. Pour le contenu découplé, les références sont essentielles (vous en apprendrez plus sur votre parcours ultérieurement).

* Permet d&#39;écrire une longue section de texte. Il existe ici d’autres options pour gérer et mettre en forme le texte. Vous pouvez même ouvrir les champs de texte individuels dans un éditeur plein écran (à l’aide de la petite icône d’écran située à droite).

![Éditeur de fragment de contenu – Alaska Spirits](/help/sites-cloud/administering/content-fragments/assets/cf-authoring-overview.png)

>[!NOTE]
>
>Une documentation spécifique au projet peut être nécessaire pour aider les auteurs à obtenir des informations sur la manière de remplir certains champs.
>
>Consultez « Modèles de fragments de contenu – Types et propriétés de données » pour obtenir des informations générales.

Confirmez vos mises à jour en effectuant l’une des opérations suivantes : **Enregistrer** ou **Enregistrer et fermer**.

>[!NOTE]
>
>Pour plus d’informations, vous pouvez lire Variations – Création de fragments de contenu.

#### Ce dont vous ne devez (probablement) pas vous inquiéter {#what-you-probably-do-not-need-to-worry-about}

Cette section peut sembler un peu étrange, mais une fois que vous avez ouvert l’éditeur de fragments de contenu et que vous commencez à l’explorer, vous pouvez voir diverses options qui ne s’appliquent (probablement) pas à votre parcours découplé en tant qu’auteur ou autrice de contenu. Il s’agit simplement d’une rapide mise en garde sur ce que vous devriez pouvoir ignorer dans un contexte découplé :

* **Modèles de fragment de contenu**

  Le nom du modèle de fragment de contenu s’affiche dans le panneau de droite de l’éditeur. Il s’agit également d’un lien qui vous mène à l’éditeur de modèles.
Les modèles de fragment de contenu sont essentiels à vos fragments de contenu, car ils définissent la structure que vous utilisez. Cependant, leur création et leur modification relèvent (généralement) de la responsabilité d’une autre personne, l’architecte de contenu.

  >[!NOTE]
  >
  >Si vous souhaitez en savoir plus, vous pouvez consultez le parcours d’architecture de contenu découplé AEM.

### Publication {#publishing}

<!-- needs more details -->

Une fois le fragment terminé, vous pouvez le **Publier** pour qu’il soit disponible pour les applications découplées.

Les actions de publication sont disponibles dans l’éditeur :

![Éditeur de fragment de contenu – Mon fragment](/help/journey-headless/author/assets/headless-journey-author-content-fragment-06.png)

>[!NOTE]
>
>Vous pouvez également publier votre fragment à partir de la console **Ressources** ou **Fragments de contenu**.

## Prochaines étapes {#whats-next}

Maintenant que vous avez appris les principes de base, l’étape suivante consiste à [en découvrir plus sur les références](references.md). Cette section présente et discute les différentes références disponibles, ainsi que la manière de créer des niveaux de structure à l’aide des références de fragment, un élément clé de la création de contenu découplé.

## Ressources supplémentaires {#additional-resources}

* [Concepts de création](/help/sites-cloud/authoring/author-publish.md)

* [Manipulation de base](/help/sites-cloud/authoring/basic-handling.md) : cette page est principalement basée sur la console **Sites**, mais de nombreuses ou la plupart des fonctionnalités sont également pertinentes pour la création de **Fragments de contenu** dans la console **Assets**.

   * [Panneau de navigation](/help/sites-cloud/authoring/basic-handling.md#navigation-panel)

   * [En-tête](/help/sites-cloud/authoring/basic-handling.md#the-header)

   * [Barre d’outils d’Actions](/help/sites-cloud/authoring/basic-handling.md#actions-toolbar)

   * [Actions rapides](/help/sites-cloud/authoring/basic-handling.md#quick-actions)

   * [Affichage et sélection de ressources](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources)

   * [Sélecteur de rail](/help/sites-cloud/authoring/basic-handling.md#rail-selector)

* [Utilisation de fragments de contenu](/help/sites-cloud/administering/content-fragments/overview.md)

   * [Gestion des fragments de contenu](/help/sites-cloud/administering/content-fragments/managing.md)

   * [Application de la configuration à votre dossier de ressources](/help/sites-cloud/administering/content-fragments/setup.md#apply-the-configuration-to-your-folder)

   * [Création d’un fragment de contenu](/help/sites-cloud/administering/content-fragments/managing.md#creating-a-content-fragment)

   * [Créer des fragments de contenu](/help/sites-cloud/administering/content-fragments/authoring.md)

   * Publication

      * Dans l’éditeur, ou la console **Ressources**

         * [Publication rapide](/help/assets/manage-publication.md#quick-publish)

         * [Gérer la publication](/help/assets/manage-publication.md#manage-publication)

      * Dans la console **Fragments de contenu**

         * [Publication et aperçu d’un fragment de contenu](/help/sites-cloud/administering/content-fragments/managing.md#publishing-and-previewing-a-fragment)

   * [Modèles de fragment de contenu](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md)

      * [Modèles de fragment de contenu – Types de données](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types)

      * [Modèles de fragment de contenu – Propriétés](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#properties)

      * [Modèles de fragment de contenu - Autoriser des modèles de fragments de contenu dans votre dossier de ressources](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#allowing-content-fragment-models-assets-folder)

* [Fragments de contenu - éditeur d’origine, à partir de la console Ressources](/help/assets/content-fragments/content-fragments-variations.md)

* Guides de prise en main
   * [Création d’une configuration découplée d’un dossier de ressources](/help/headless/setup/create-assets-folder.md)

* Parcours d’architecture de contenu découplé AEM

* Parcours de traduction découplée AEM
