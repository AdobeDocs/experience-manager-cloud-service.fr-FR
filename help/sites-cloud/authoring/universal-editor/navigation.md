---
title: Accès et navigation dans l’éditeur universel
description: Découvrez les principes de base de l’accès et de la navigation dans l’éditeur universel.
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: eecbc48a77e92b064be9fcdbe547fb330f8d40e0
workflow-type: tm+mt
source-wordcount: '1576'
ht-degree: 22%

---


# Accès et navigation dans l’éditeur universel {#navigating}

Découvrez les principes de base de l’accès et de la navigation dans l’éditeur universel.

## Présentation {#introduction}

L’éditeur universel permet de modifier n’importe quel aspect de contenu dans n’importe quelle mise en œuvre pour que vous puissiez fournir des expériences exceptionnelles, d’augmenter la vitesse du contenu et d’offrir une expérience de développement à la pointe de la technologie.

Pour ce faire, l’éditeur universel offre aux auteurs de contenu une interface utilisateur intuitive qui nécessite une formation minimale pour simplement pouvoir intervenir et commencer à modifier le contenu. Ce document décrit comment naviguer dans l’éditeur universel.

>[!TIP]
>
>* Pour plus d&#39;informations sur la création à l&#39;aide d&#39;Universal Editor, consultez le document [Création de contenu avec l&#39;Universal Editor.](/help/sites-cloud/authoring/universal-editor/authoring.md)
>* Pour une présentation plus détaillée de l’éditeur universel, consultez le document [Présentation de l’éditeur universel.](/help/implementing/universal-editor/introduction.md)

## Préparer l’application {#prepare-app}

Pour créer du contenu pour une application à l’aide de l’éditeur universel, l’application doit être instrumentée par un développeur ou une développeuse afin de prendre en charge l’éditeur.

>[!TIP]
>
>Consultez [Prise en main de l’éditeur universel dans AEM](/help/implementing/universal-editor/getting-started.md) pour obtenir un exemple de configuration d’une application AEM pour qu’elle fonctionne avec l’éditeur universel.

## Accès à l’éditeur universel {#accessing}

Une fois que l’application est instrumentée pour fonctionner avec l’éditeur universel, l’éditeur universel peut accéder à la fois à l’intérieur d’AEM as a Cloud Service et directement sans accéder à AEM.

### Accès dans AEM as a Cloud Service {#accessing-aem}

1. Connectez-vous à votre instance de création AEM as a Cloud Service.
1. Utilisez la [**console Sites**](/help/sites-cloud/authoring/sites-console/introduction.md) pour accéder à la page créée à utiliser avec l’éditeur universel que vous souhaitez modifier.
1. Modifiez la page.
1. L’éditeur universel s’ouvre pour modifier la page sélectionnée.

>[!NOTE]
>
>Lors de la modification d’une page dans la console [**Sites**,](/help/sites-cloud/authoring/sites-console/introduction.md), la console ouvre l’éditeur approprié au [modèle:](/help/sites-cloud/authoring/sites-console/templates.md) de la page, soit l’éditeur universel décrit dans ce document, soit l’[éditeur de page.](/help/sites-cloud/authoring/page-editor/introduction.md)

### Accès direct {#accessing-directly}

1. Connectez-vous à l’éditeur universel. Vous avez besoin d&#39;une Adobe ID pour vous connecter et [ avoir accès à l&#39;éditeur universel.](/help/implementing/universal-editor/getting-started.md#request-access)

1. Une fois connecté, saisissez l’URL de la page à modifier dans la barre d’emplacement [.](#location-bar) afin que vous puissiez commencer à modifier du contenu tel que [contenu texte](#text-mode) ou [contenu multimédia.](#media-mode)

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

Cette icône comporte un badge avec le nombre de [notifications incomplètes actuellement attribuées.](/help/implementing/cloud-manager/notifications.md)

![Notifications](assets/notifications.png)

#### Propriétés de l’utilisateur ou de l’utilisatrice {#user-properties}

Appuyez ou cliquez sur l’icône qui représente votre utilisateur ou votre utilisatrice pour accéder à vos paramètres d’utilisateur ou d’utilisatrice. Si vous n’avez configuré aucune image d’utilisateur ou d’utilisatrice, une icône est attribuée de manière aléatoire.

![Propriétés de l’utilisateur](assets/user-properties.png)

### Barre d’outils de l’éditeur universel {#universal-editor-toolbar}

La barre d’outils de l’éditeur universel est toujours présente en haut de l’écran, juste sous l’en-tête [de l’Experience Cloud.](#experience-cloud-header) Il vous permet d’accéder rapidement à une autre page à modifier et de publier la page active.

![Barre d’outils de l’éditeur universel](assets/universal-editor-toolbar.png)

#### Bouton Accueil {#home-button}

Le bouton d’accueil vous renvoie à la page de début de l’éditeur universel.

![Menu Hamburger](assets/home-button.png)

Sur la page de début, vous pouvez saisir l’URL du site à modifier à l’aide de l’éditeur universel.

![Page de démarrage](assets/start-page.png)

>[!NOTE]
>
>Toute page que vous souhaitez modifier avec l’éditeur universel doit être [ instrumentée pour prendre en charge l’éditeur universel.](/help/implementing/universal-editor/getting-started.md)

#### Barre d’emplacement {#location-bar}

La barre d’emplacement affiche l’adresse de la page que vous modifiez. Sélectionnez cette option pour saisir l’adresse d’une autre page à modifier.

![Barre d’emplacement](assets/location-bar.png)

>[!TIP]
>
>Utilisez la clé d&#39;accès `l` (la lettre l) pour ouvrir la barre d&#39;adresse.

>[!NOTE]
>
>Toute page que vous souhaitez modifier avec l’éditeur universel doit être [ instrumentée pour prendre en charge l’éditeur universel.](/help/implementing/universal-editor/getting-started.md)

#### Paramètres d’en-tête d’authentification {#authentication-settings}

Sélectionnez l&#39;icône des paramètres d&#39;en-tête d&#39;authentification si vous devez [définir un en-tête d&#39;authentification personnalisé à des fins de développement local.](/help/implementing/universal-editor/developer-overview.md#auth-header)

![Bouton Paramètres d’en-tête d’authentification](assets/authentication-header-settings.png)

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
>Utilisez la touche d’accès rapide `p` pour basculer vers et depuis le mode Aperçu.

#### Ouvrir l’aperçu de l’application {#open-app-preview}

Sélectionnez l’icône d’aperçu de l’application ouverte pour ouvrir la page que vous êtes en train de modifier dans son propre onglet de navigateur, sans l’éditeur pour prévisualiser votre contenu.

![Ouvrir l’aperçu de l’application](assets/open-app-preview.png)

>[!TIP]
>
>Utilisez la touche d’accès rapide `o` (lettre o) pour ouvrir l’aperçu de l’application.

>[!TIP]
>
>L&#39;URL d&#39;aperçu de votre application [ peut être personnalisée.](/help/implementing/universal-editor/customizing.md#custom-preview-urls)

#### Publier {#publish}

Sélectionnez le bouton Publier pour que vous puissiez publier les modifications apportées au contenu en direct pour que vos lecteurs puissent les utiliser.

![Bouton Publier](assets/publish.png)

>[!TIP]
>
>Consultez le document [Publication de contenu avec l’éditeur universel](publishing.md) pour plus d’informations sur la publication avec l’éditeur universel.

#### Ellipse {#ellipsis}

D’autres options standard sont accessibles à l’aide du bouton représentant des points de suspension.

![Bouton représentant des points de suspension](assets/ellipsis.png)

Par exemple, la possibilité d’annuler la publication d’une page (c’est-à-dire d’inverser l’action du bouton [**Publish**](#publish)) est accessible via le bouton représentant des points de suspension.

#### Boutons supplémentaires {#additional-toolbar-buttons}

Universal Editor offre une expérience de création personnalisable et extensible. Si d’autres boutons s’affichent dans la barre d’outils, votre éditeur universel a été étendu.

* Pour plus d’informations sur les possibilités d’extension, consultez la section [Personnalisation et extension de l’éditeur universel.](/help/implementing/universal-editor/customizing.md)
* Pour plus d’informations sur le fonctionnement d’une extension individuelle, consultez la [documentation sur l’Extension Manager.](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/)

### L’éditeur {#editor}

L’éditeur occupe la plupart de la fenêtre et est l’endroit où la page spécifiée dans [la barre d’emplacement](#location-bar) est rendue.

![Éditeur](assets/editor.png)

Si l’éditeur est en mode [aperçu,](#preview-mode) le contenu est navigable et vous pouvez suivre les liens, mais vous ne pouvez pas modifier le contenu.

### Rail des propriétés {#properties-rail}

Le rail des propriétés est toujours présent le long du côté droit de l’éditeur. En fonction de son mode, il peut afficher les détails d’un composant sélectionné dans le contenu ou la hiérarchie du contenu de la page.

![Le rail de propriétés](assets/properties-rail.png)

#### Mode Propriétés {#properties-mode}

En mode Propriétés, le rail affiche les propriétés du composant actuellement sélectionné dans l’éditeur. Il s’agit du mode par défaut du rail des propriétés lorsqu’une page est chargée.

![Mode Propriétés](assets/properties-mode.png)

Selon le type de composant sélectionné, les détails peuvent être affichés et modifiés dans le rail des propriétés.

![Détails du composant](assets/component-details.png)

Tous les composants ne comportent pas de détails qui peuvent être affichés et/ou modifiés.

>[!TIP]
>
>Utilisez la touche d’accès rapide `d` pour passer en mode Propriétés.

#### Mode Arborescence de contenu {#content-tree-mode}

En mode Arborescence de contenu, le rail affiche la hiérarchie du contenu de la page.

![Mode Arborescence de contenu](assets/content-tree-mode.png)

Lors de la sélection d’un élément dans l’arborescence de contenu, l’éditeur fait défiler le contenu jusqu’à ce qu’il le sélectionne.

![Arborescence de contenu](assets/content-tree.png)

>[!TIP]
>
>Utilisez la touche d’accès rapide `f` pour passer en mode arborescence de contenu.

##### Ouvrir dans l’éditeur CF {#edit}

Lors de la modification, les options du composant sélectionné s’affichent dans le rail des propriétés, où vous pouvez modifier le composant sélectionné. Si le composant sélectionné est un fragment de contenu, vous pouvez également sélectionner le bouton **Ouvrir dans l’éditeur CF**.

![Icône Ouvrir dans l’éditeur de fragment de contenu](assets/open-in-cf-editor.png)

Appuyez ou cliquez sur le bouton **Ouvrir dans l’éditeur de fragment de contenu** pour ouvrir l’ [ éditeur de fragment de contenu](/help/assets/content-fragments/content-fragments-managing.md#opening-the-fragment-editor) dans un nouvel onglet. Cela vous permet d’accéder à toute la puissance de l’éditeur de fragments de contenu pour modifier le fragment de contenu associé.

Selon les besoins de votre workflow, vous pouvez modifier le fragment de contenu dans l’éditeur universel ou directement dans l’éditeur de fragment de contenu.

>[!TIP]
>
>Utilisez la touche d’accès rapide `e` pour ouvrir un fragment de contenu sélectionné dans l’éditeur de fragment de contenu.

##### Ajouter {#add}

Si vous sélectionnez un composant de conteneur dans l’arborescence de contenu ou dans l’éditeur, l’option d’ajout s’affiche sur le rail des propriétés.

![Ajouter une icône](assets/ue-add-component-icon.png)

Appuyez ou cliquez sur le bouton Ajouter pour ouvrir un menu déroulant des composants disponibles pour [ajouter au conteneur sélectionné.](#adding-components)

![Ajouter un menu contextuel](assets/add-context-menu.png)

>[!TIP]
>
>Utilisez la touche d’accès rapide `a` pour ajouter un composant à un composant de conteneur sélectionné.

##### Supprimer {#delete}

Si vous sélectionnez un composant dans un composant de conteneur dans l’arborescence de contenu ou dans l’éditeur, l’option de suppression s’affiche sur le rail des propriétés.

![Icône de suppression](assets/ue-delete-component-icon.png)

Appuyez ou cliquez sur le bouton de suppression [ pour supprimer le composant.](#deleting-components)

>[!TIP]
>
>Utilisez la touche d&#39;accès rapide `Shift+Backspace` pour supprimer un composant sélectionné d&#39;un conteneur.

#### Boutons supplémentaires {#additional-properties-rail-buttons}

Universal Editor offre une expérience de création personnalisable et extensible. Si d’autres boutons s’affichent dans le rail des propriétés, votre éditeur universel a été étendu.

* Pour plus d’informations sur les possibilités d’extension, consultez la section [Personnalisation et extension de l’éditeur universel.](/help/implementing/universal-editor/customizing.md)
* Pour plus d’informations sur le fonctionnement d’une extension individuelle, consultez la [documentation sur l’Extension Manager.](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/)

## Étapes suivantes {#next-steps}

Maintenant que vous savez comment accéder à l’éditeur universel et naviguer dans celui-ci, vous êtes prêt à [créer du contenu à l’aide de cet éditeur.](/help/sites-cloud/authoring/universal-editor/authoring.md)
