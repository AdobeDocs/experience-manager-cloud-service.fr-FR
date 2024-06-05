---
title: Création de contenu avec l’éditeur universel
description: Découvrez à quel point il est facile et intuitif pour les personnes en charge de la création de créer du contenu à l’aide de l’éditeur universel.
exl-id: 15fbf5bc-2e30-4ae7-9e7f-5891442228dd
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '2313'
ht-degree: 25%

---


# Création de contenu avec l’éditeur universel {#authoring}

Découvrez à quel point il est facile et intuitif pour les personnes en charge de la création de créer du contenu à l’aide de l’éditeur universel.

## Présentation {#introduction}

L’éditeur universel permet de modifier n’importe quel aspect de contenu dans n’importe quelle mise en œuvre pour que vous puissiez fournir des expériences exceptionnelles, d’augmenter la vitesse du contenu et d’offrir une expérience de développement à la pointe de la technologie.

Pour ce faire, l’éditeur universel offre aux auteurs de contenu une interface utilisateur intuitive qui nécessite une formation minimale pour simplement pouvoir intervenir et commencer à modifier le contenu. Ce document décrit l’expérience de création d’Universal Editor.

>[!TIP]
>
>Pour une présentation plus détaillée de l’éditeur universel, consultez le document [Présentation de l’éditeur universel.](/help/implementing/universal-editor/introduction.md)

## Préparer l’application {#prepare-app}

Pour créer du contenu pour une application à l’aide de l’éditeur universel, l’application doit être instrumentée par un développeur ou une développeuse afin de prendre en charge l’éditeur.

>[!TIP]
>
>Consultez [Prise en main de l’éditeur universel dans AEM](/help/implementing/universal-editor/getting-started.md) pour obtenir un exemple de configuration d’une application AEM pour qu’elle fonctionne avec l’éditeur universel.

## Accès à l’éditeur universel {#accessing}

Une fois que l’application est instrumentée pour fonctionner avec l’éditeur universel, l’éditeur universel peut être accessible à la fois à l’intérieur d’AEM as a Cloud Service et directement sans accéder à AEM.

### Accès dans AEM as a Cloud Service {#accessing-aem}

1. Connectez-vous à votre instance de création as a Cloud Service AEM.
1. Utilisez la variable [**Sites** console](/help/sites-cloud/authoring/sites-console/introduction.md) pour accéder à la page créée à utiliser avec l’éditeur universel que vous souhaitez modifier.
1. Modifiez la page.
1. L’éditeur universel s’ouvre pour modifier la page sélectionnée.

>[!NOTE]
>
>Lors de la modification d’une page dans le [**Sites** console,](/help/sites-cloud/authoring/sites-console/introduction.md) la console ouvre l’éditeur approprié à la page. [modèle :](/help/sites-cloud/authoring/sites-console/templates.md) soit l’éditeur universel décrit dans ce document, soit l’éditeur [éditeur de page.](/help/sites-cloud/authoring/page-editor/introduction.md)

### Accès direct {#accessing-directly}

1. Connectez-vous à l’éditeur universel. Vous avez besoin d’une Adobe ID pour vous connecter et [ont accès à l’éditeur universel.](/help/implementing/universal-editor/getting-started.md#request-access)

1. Une fois connecté, saisissez l’URL de la page à modifier dans le [la barre d’emplacement.](#location-bar) pour pouvoir commencer à modifier du contenu, par exemple [contenu texte](#text-mode) ou [contenu multimédia.](#media-mode)

## Présentation de l’interface utilisateur {#ui}

L’interface utilisateur est divisée en deux zones principales.

* [En-tête Experience Cloud](#experience-cloud-header)
* [Barre d’outils de l’éditeur universel](#universal-editor-toolbar)
* [L’éditeur](#editor)
* [Rail Propriétés](#properties-rail)

![Interface utilisateur de l’éditeur universel](assets/ui.png)

### En-tête Experience Cloud {#experience-cloud-header}

L’en-tête Experience Cloud est toujours présent en haut de l’écran. Il s’agit d’une ancre de lien qui vous indique où vous vous trouvez dans Experience Cloud et vous aide à accéder à d’autres applications Experience Cloud.

![En-tête Experience Cloud](assets/experience-cloud-header.png)

#### Experience Manager {#experience-manager}

Sélectionnez le lien Adobe Experience Cloud à gauche de l’en-tête pour accéder à la racine de votre solution Experience Manager et aux outils tels que [Cloud Manager,](/help/onboarding/cloud-manager-introduction.md) [Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/introduction/overview-cam.md) et [Distribution logicielle.](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=fr)

![Bouton Navigation globale](assets/global-navigation.png)

#### Organisation {#organization}

L’organisation dans laquelle vous êtes actuellement connecté s’affiche. Sélectionnez cette option pour passer à une autre organisation si votre Adobe ID est associé à plusieurs.

![Indicateur d’organisation](assets/organization.png)

#### Solutions {#solutions}

Appuyez ou cliquez sur le sélecteur de solutions pour accéder rapidement à d’autres solutions Experience Cloud.

![Sélecteur de solutions](assets/solutions.png)

#### Aide {#help}

L’icône d’aide permet d’accéder rapidement aux ressources d’apprentissage et d’assistance.

![Aide](assets/help.png)

#### Notifications {#notifications}

Cette icône comporte un badge indiquant le nombre d’éléments incomplets actuellement attribués. [notifications.](/help/implementing/cloud-manager/notifications.md)

![Notifications](assets/notifications.png)

#### Propriétés de l’utilisateur ou de l’utilisatrice {#user-properties}

Appuyez ou cliquez sur l’icône qui représente votre utilisateur ou votre utilisatrice pour accéder à vos paramètres d’utilisateur ou d’utilisatrice. Si vous n’avez configuré aucune image d’utilisateur ou d’utilisatrice, une icône est attribuée de manière aléatoire.

![Propriétés de l’utilisateur](assets/user-properties.png)

### Barre d’outils de l’éditeur universel {#universal-editor-toolbar}

La barre d’outils de l’éditeur universel est toujours présente en haut de l’écran, juste en dessous. [l’en-tête de l’Experience Cloud.](#experience-cloud-header) Il vous permet d’accéder rapidement à une autre page à modifier et de publier la page active.

![Barre d’outils de l’éditeur universel](assets/universal-editor-toolbar.png)

#### Bouton Accueil {#home-button}

Le bouton d’accueil vous renvoie à la page de début de l’éditeur universel.

![Menu Hamburger](assets/home-button.png)

Sur la page de début, vous pouvez saisir l’URL du site à modifier à l’aide de l’éditeur universel.

![Page de début](assets/start-page.png)

>[!NOTE]
>
>Toute page que vous souhaitez modifier à l’aide d’Universal Editor doit être [instrumenté pour prendre en charge l’éditeur universel.](/help/implementing/universal-editor/getting-started.md)

#### Barre d’emplacement {#location-bar}

La barre d’emplacement affiche l’adresse de la page que vous modifiez. Sélectionnez cette option pour saisir l’adresse d’une autre page à modifier.

![Barre d’emplacement](assets/location-bar.png)

>[!TIP]
>
>Utiliser le raccourci clavier `L` pour ouvrir la barre d’adresse.

>[!NOTE]
>
>Toute page que vous souhaitez modifier à l’aide d’Universal Editor doit être [instrumenté pour prendre en charge l’éditeur universel.](/help/implementing/universal-editor/getting-started.md)

#### Paramètres d’en-tête d’authentification {#authentication-settings}

Sélectionnez l’icône des paramètres d’en-tête d’authentification si vous devez [définissez un en-tête d’authentification personnalisé à des fins de développement local.](/help/implementing/universal-editor/developer-overview.md#auth-header)

![Bouton Paramètres de l’en-tête d’authentification](assets/authentication-header-settings.png)

#### Paramètres de l&#39;émulateur {#emulator}

Sélectionnez l’icône d’émulation pour définir comment l’éditeur universel effectue le rendu de la page.

![Icône Émulateur](assets/emulator.png)

Appuyez ou cliquez sur l’icône d’émulation pour afficher les options.

![Options d’émulation](assets/emulation-options.png)

Par défaut, l’éditeur s’ouvre dans la mise en page pour ordinateur où la hauteur et la largeur sont automatiquement définies par le navigateur.

Vous pouvez également choisir d’émuler un appareil mobile et dans l’éditeur universel :

* Définir son orientation
* Définir la largeur et la hauteur
* Modification de l’orientation

#### Mode Aperçu {#preview-mode}

En mode Aperçu, la page rendue dans l’éditeur est telle qu’elle apparaîtrait sur votre service publié. Cela permet à l’auteur de contenu de parcourir le contenu en cliquant sur des liens, etc.

![Mode Aperçu.](assets/preview-mode.png)

>[!TIP]
>
>Utiliser la touche chaude `P` pour basculer vers et depuis le mode aperçu.

#### Ouvrir l’aperçu de l’application {#open-app-preview}

Sélectionnez l’icône d’aperçu de l’application ouverte pour ouvrir la page que vous êtes en train de modifier dans son propre onglet de navigateur, sans l’éditeur pour prévisualiser votre contenu.

![Ouvrir l’aperçu de l’application](assets/open-app-preview.png)

>[!TIP]
>
>Utiliser la touche chaude `O` (lettre O) pour ouvrir l’aperçu de l’application.

#### Publier {#publish}

Sélectionnez le bouton Publier pour que vous puissiez publier les modifications apportées au contenu en direct pour que vos lecteurs puissent les utiliser.

![Bouton Publier](assets/publish.png)

>[!TIP]
>
>Voir le document [Publication de contenu avec l’éditeur universel](publishing.md) pour plus d’informations sur la publication avec Universal Editor.

### L’éditeur {#editor}

L’éditeur occupe la majeure partie de la fenêtre et est l’endroit où la page indiquée dans [la barre d’emplacement ;](#location-bar) est rendue.

![Éditeur](assets/editor.png)

Si l’éditeur se trouve dans [mode aperçu,](#preview-mode) le contenu sera navigable et vous pouvez suivre les liens, mais vous ne pouvez pas le modifier.

### Rail des propriétés {#properties-rail}

Le rail des propriétés est toujours présent le long du côté droit de l’éditeur. En fonction de son mode, il peut afficher les détails d’un composant sélectionné dans le contenu ou la hiérarchie du contenu de la page.

![Rail Propriétés](assets/component-rail.png)

#### Mode Propriétés {#properties-mode}

En mode Propriétés, le rail affiche les propriétés du composant actuellement sélectionné dans l’éditeur. Il s’agit du mode par défaut du rail des propriétés lorsqu’une page est chargée.

![Mode Propriétés](assets/properties-mode.png)

Selon le type de composant sélectionné, les détails peuvent être affichés et modifiés dans le rail des propriétés.

![Détails du composant](assets/component-details.png)

Tous les composants ne comportent pas de détails qui peuvent être affichés et/ou modifiés.

>[!TIP]
>
>Utiliser la touche chaude `D` pour passer en mode propriétés.

#### Mode Arborescence de contenu {#content-tree-mode}

En mode Arborescence de contenu, le rail affiche la hiérarchie du contenu de la page.

![Mode Arborescence de contenu](assets/content-tree-mode.png)

Lors de la sélection d’un élément dans l’arborescence de contenu, l’éditeur fait défiler le contenu jusqu’à ce qu’il le sélectionne.

![Arborescence de contenu](assets/content-tree.png)

>[!TIP]
>
>Utiliser la touche chaude `F` pour passer en mode arborescence de contenu.

##### Modifier {#edit}

Lors de la modification, les options du composant sélectionné s’affichent dans le rail des propriétés, où vous pouvez modifier le composant sélectionné. Si le composant sélectionné est un fragment de contenu, vous pouvez également sélectionner le bouton Modifier .

![Icône Modifier](assets/edit.png)

Appuyez ou cliquez sur le bouton Modifier pour ouvrir la [Éditeur de fragment de contenu](/help/assets/content-fragments/content-fragments-managing.md#opening-the-fragment-editor) dans un nouvel onglet. Cela vous permet d’accéder à toute la puissance de l’éditeur de fragments de contenu pour modifier le fragment de contenu associé.

Selon les besoins de votre workflow, vous pouvez modifier le fragment de contenu dans l’éditeur universel ou directement dans l’éditeur de fragment de contenu.

>[!TIP]
>
>Utiliser la touche chaude `E` pour modifier un composant sélectionné.

##### Ajouter {#add}

Si vous sélectionnez un composant de conteneur dans l’arborescence de contenu ou dans l’éditeur, l’option d’ajout s’affiche sur le rail des propriétés.

![Icône Ajouter](assets/ue-add-component-icon.png)

Appuyez ou cliquez sur le bouton d’ajout pour ouvrir un menu déroulant des composants disponibles pour [ajoutez au conteneur sélectionné.](#adding-components)

![Menu contextuel](assets/add-context-menu.png)

>[!TIP]
>
>Utiliser la touche chaude `A` pour ajouter un composant à un composant de conteneur sélectionné.

##### Supprimer {#delete}

Si vous sélectionnez un composant dans un composant de conteneur dans l’arborescence de contenu ou dans l’éditeur, l’option de suppression s’affiche sur le rail des propriétés.

![Icône de suppression](assets/ue-delete-component-icon.png)

Appuyez ou cliquez sur le bouton de suppression [supprime le composant.](#deleting-components)

>[!TIP]
>
>Utiliser la touche chaude `Shift+Backspace` pour supprimer un composant sélectionné d’un conteneur.

## Modification du contenu {#editing-content}

La modification du contenu est simple et intuitive. Lorsque vous placez le pointeur de la souris sur le contenu de l’éditeur, le contenu modifiable est mis en surbrillance avec une zone bleue.

![Le contenu modifiable est mis en surbrillance dans une case bleue.](assets/editable-content.png)

>[!TIP]
>
>Par défaut, appuyer ou cliquer sur le contenu le sélectionne pour le modifier. Si vous souhaitez parcourir votre contenu en suivant les liens, passez à [mode aperçu.](#preview-mode)

Selon le contenu que vous sélectionnez, vous pouvez avoir différentes options de modification statique et des informations et options supplémentaires pour le contenu dans la variable [rail de propriétés.](#properties-rail)

### Modification de texte brut {#edit-plain-text}

Vous pouvez modifier le texte en place en double-cliquant ou en appuyant deux fois sur le composant.

![Modification du contenu](assets/editing-content.png)

Appuyez sur Entrée/Retour ou sélectionnez en dehors de la zone de texte pour enregistrer vos modifications.

Lorsque vous sélectionnez le composant de texte, ses détails s’affichent dans le rail des propriétés. Vous pouvez également modifier le texte dans le rail.

![Modification de texte dans le rail des propriétés](assets/ue-editing-text-component-rail.png)

En outre, des détails sur votre texte sont disponibles dans le rail de propriétés. Les modifications sont automatiquement enregistrées lorsque le focus quitte le champ modifié dans le rail des propriétés.

### Modification de texte enrichi {#edit-rich-text}

Vous pouvez modifier le texte en place en double-cliquant ou en appuyant deux fois sur le composant.

![Modification d’un composant de texte enrichi](assets/rich-text-editing.png)

Pour votre commodité, les options de mise en forme et les détails de votre texte sont disponibles à deux endroits.

* La variable **menu contextuel** s’ouvre au-dessus du bloc de texte enrichi et propose des options de mise en forme de base en contexte. En raison des restrictions d’espace, certaines options peuvent être masquées derrière le bouton représentant des points de suspension.
* La variable **rail des propriétés** affiche toutes les options de formatage disponibles avec le texte.

Les modifications sont automatiquement enregistrées lorsque le focus quitte le champ modifié.

### Modification du média {#edit-media}

Vous pouvez afficher ses détails dans le rail des propriétés.

![Modification du média](assets/ue-edit-media.png)

1. Appuyez ou cliquez sur l’aperçu de l’image sélectionnée dans le rail des propriétés.
1. La variable [sélecteur de ressources](/help/assets/asset-selector.md#using-asset-selector) s’ouvre pour vous permettre de sélectionner une ressource.
1. Sélectionnez cette option pour sélectionner une nouvelle ressource.
1. Sélectionner **Sélectionner** pour revenir au rail des propriétés où la ressource a été remplacée.

Les modifications sont automatiquement enregistrées dans votre contenu.

### Modification de fragments de contenu {#edit-content-fragment}

Si vous sélectionnez une [Fragment de contenu,](/help/sites-cloud/administering/content-fragments/overview.md) vous pouvez modifier ses détails dans le rail des propriétés.

![Modification d’un fragment de contenu](assets/ue-edit-cf.png)

Les champs définis dans le modèle de contenu du fragment de contenu sélectionné sont affichés et modifiables dans le rail des propriétés.

Si vous sélectionnez un champ lié à un fragment de contenu, celui-ci se charge dans le rail des composants et le champ est automatiquement défilé vers .

Les modifications sont automatiquement enregistrées lorsque le focus quitte le champ modifié dans le rail des propriétés.

Si vous souhaitez modifier votre fragment de contenu dans le [Éditeur de fragment de contenu](/help/sites-cloud/administering/content-fragments/authoring.md) cliquez sur [bouton d’édition](#edit) dans le rail de mode.

Selon les besoins de votre workflow, vous pouvez modifier le fragment de contenu dans l’éditeur universel ou directement dans l’éditeur de fragment de contenu.

### Ajout de composants aux conteneurs {#adding-components}

1. Sélectionnez un composant de conteneur dans l’arborescence de contenu ou dans l’éditeur.
1. Sélectionnez ensuite l’icône d’ajout dans le rail des propriétés.

   ![Sélectionner un composant à ajouter à un conteneur](assets/ue-add-component.png)

Le composant est inséré dans le conteneur et peut être modifié dans l’éditeur.

>[!TIP]
>
>Utiliser la touche chaude `A` pour ajouter un composant au conteneur sélectionné.

### Suppression de composants des conteneurs {#deleting-components}

1. Sélectionnez un composant de conteneur dans l’arborescence de contenu ou dans l’éditeur.
1. Sélectionnez l’icône chevron du conteneur pour développer son contenu dans l’arborescence de contenu.
1. Sélectionnez ensuite, dans l’arborescence de contenu, un composant dans le conteneur.
1. Sélectionnez l’icône de suppression dans le rail des propriétés.

   ![Suppression d’un composant](assets/ue-delete-component.png)

Le composant sélectionné a été supprimé.

>[!TIP]
>
>Utiliser la touche chaude `Shift+Backspace` pour supprimer le composant sélectionné de son conteneur.

### Réorganisation des composants dans les conteneurs {#reordering-components}

1. Sélectionnez un composant de conteneur dans l’arborescence de contenu ou dans l’éditeur.
1. Si ce n’est pas déjà fait dans [le mode arborescence de contenu,](#content-tree-mode) passez-y.
1. Sélectionnez l’icône chevron du conteneur pour développer son contenu dans l’arborescence de contenu.
1. Faites glisser les icônes de poignée en regard des composants dans le conteneur pour afficher que vous puissiez les réorganiser. Faites glisser les composants pour les réorganiser dans le conteneur.

   ![Réorganisation des composants](assets/ue-reordering-components.png)

1. Le composant déplacé devient gris dans l’arborescence du composant, tandis que votre point d’insertion est représenté par une ligne bleue. Libérez le composant pour le placer à son nouvel emplacement.

Les composants sont réorganisés dans l’arborescence de contenu et dans l’éditeur.

## Prévisualisation du contenu {#previewing-content}

Une fois le contenu modifié, vous aimez généralement le parcourir pour voir à quoi il ressemble dans le contenu d’autres pages. En [mode Aperçu](#preview-mode), vous pouvez cliquer sur les liens pour parcourir votre contenu comme le ferait un lecteur ou une lectrice. Le contenu est rendu dans l’éditeur tel qu’il serait publié.

En mode d’aperçu, appuyer ou cliquer sur le contenu réagit comme il le ferait à un lecteur du contenu. Si vous souhaitez sélectionner le contenu à modifier, désactivez l’option [mode aperçu.](#preview-mode)

## Ressources supplémentaires {#additional-resources}

Pour savoir comment publier du contenu avec l’éditeur universel, consultez ce document.

* [Publication de contenu avec l’éditeur universel](publishing.md) - Découvrez comment l’éditeur universel publie du contenu et comment vos applications peuvent gérer le contenu publié.

Pour en savoir plus sur les détails techniques d’Universal Editor, consultez ces documents de développement.

* [Présentation de l’éditeur universel](/help/implementing/universal-editor/introduction.md) - Découvrez comment l’éditeur universel permet de modifier n’importe quel aspect d’un contenu dans n’importe quelle implémentation afin de fournir des expériences exceptionnelles, d’augmenter la vitesse du contenu et d’offrir une expérience de développement à la pointe de la technologie.
* [Prise en main de l’éditeur universel dans AEM](/help/implementing/universal-editor/getting-started.md) - Découvrez comment accéder à l’éditeur universel et comment commencer à instrumenter votre première application AEM pour l’utiliser.
* [Architecture de l’éditeur universel](/help/implementing/universal-editor/architecture.md) - Découvrez l’architecture de l’éditeur universel et le flux de données entre ses services et calques.
* [Attributs et types](/help/implementing/universal-editor/attributes-types.md) - Découvrez les attributs et les types de données requis par l’éditeur universel.
* [Authentification de l’éditeur universel](/help/implementing/universal-editor/authentication.md) - Découvrez comment l’éditeur universel s’authentifie.

