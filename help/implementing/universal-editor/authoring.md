---
title: Création de contenu avec l’éditeur universel
description: Découvrez à quel point il est facile et intuitif pour les personnes en charge de la création de créer du contenu à l’aide de l’éditeur universel.
exl-id: 15fbf5bc-2e30-4ae7-9e7f-5891442228dd
source-git-commit: c6ab2d9b01a3f1abedb06d1d413e7eceb8b1c031
workflow-type: tm+mt
source-wordcount: '1557'
ht-degree: 49%

---

# Création de contenu avec l’éditeur universel {#authoring}

Découvrez à quel point il est facile et intuitif pour les personnes en charge de la création de créer du contenu à l’aide de l’éditeur universel.

## Présentation {#introduction}

L’éditeur universel permet de modifier n’importe quel aspect de contenu dans n’importe quelle mise en oeuvre afin de proposer des expériences exceptionnelles, d’augmenter la vitesse du contenu et de fournir une expérience de développement à la pointe de la technologie.

Pour ce faire, l’éditeur universel offre aux auteurs de contenu une interface utilisateur intuitive qui nécessite une formation minimale pour simplement pouvoir intervenir et commencer à modifier le contenu.

>[!TIP]
>
>Pour une présentation plus détaillée de l’éditeur universel, consultez le document [Présentation de l’éditeur universel.](introduction.md)

>[!NOTE]
>
>L’éditeur universel est toujours en développement et ne peut pas modifier tous les types de contenu pour le moment.

## Préparer l’application {#prepare-app}

Pour créer du contenu pour une application à l’aide d’Universal Editor, l’application doit être instrumentée par un développeur afin de prendre en charge l’éditeur.

>[!TIP]
>
>Voir [Prise en main d’Universal Editor dans AEM](getting-started.md) pour obtenir un exemple de configuration d’une application AEM pour qu’elle fonctionne avec l’éditeur universel.

## Se connecter {#sign-in}

Une fois que l’application est instrumentée pour fonctionner avec l’éditeur universel, vous devez vous connecter à l’éditeur universel. Vous aurez besoin d’un Adobe ID pour vous connecter et d’[avoir accès à l’éditeur universel.](getting-started.md#request-access)

Une fois connecté, saisissez l’URL de la page à modifier dans le [la barre d’emplacement.](#location-bar) pour pouvoir commencer à modifier du contenu, par exemple [contenu texte](#text-mode) ou [contenu multimédia.](#media-mode)

## Présentation de l’interface utilisateur {#ui}

L’interface utilisateur est divisée en cinq zones principales.

* [En-tête Experience Cloud](#experience-cloud-header)
* [En-tête de l’éditeur universel](#universal-editor-header)
* [Le rail de mode](#mode-rail)
* [L’éditeur](#editor)
* [Rail des composants](#component-rail)

![Interface utilisateur de l’éditeur universel](assets/ui.png)

### En-tête Experience Cloud {#experience-cloud-header}

L’en-tête Experience Cloud est toujours présent en haut de l’écran. Il s’agit d’une ancre de lien qui vous indique où vous vous trouvez dans Experience Cloud et vous aide à accéder à d’autres applications Experience Cloud.

![En-tête Experience Cloud](assets/experience-cloud-header.png)

#### Experience Manager {#experience-manager}

Sélectionnez le lien Adobe Experience Cloud à gauche de l’en-tête pour accéder à la racine de votre solution Experience Manager et aux outils tels que [Cloud Manager,](/help/onboarding/cloud-manager-introduction.md) [Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/introduction/overview-cam.md) et [Distribution logicielle.](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=fr)

![Bouton Navigation globale](assets/global-navigation.png)

#### Organisation {#organization}

L’organisation dans laquelle vous êtes actuellement connecté s’affiche. Appuyez ou cliquez sur pour passer à une autre organisation si votre Adobe ID est associé à plusieurs d’entre elles.

![Indicateur d’organisation](assets/organization.png)

#### Solutions {#solutions}

Appuyez ou cliquez sur le sélecteur de solutions pour accéder rapidement à d’autres solutions Experience Cloud.

![Sélecteur de solutions](assets/solutions.png)

#### Aide {#help}

L’icône d’aide permet d’accéder rapidement aux ressources d’apprentissage et d’assistance.

![Aide](assets/help.png)

#### Notifications {#notifications}

Cette icône comporte un badge indiquant le nombre d’éléments incomplets actuellement attribués. [notifications.](/help/implementing/cloud-manager/notifications.md)

![Notifications](assets/notifications.png)

#### Propriétés de l’utilisateur ou de l’utilisatrice {#user-properties}

Appuyez ou cliquez sur l’icône représentant votre utilisateur ou votre utilisatrice pour accéder à vos paramètres utilisateur. Si aucune image d’utilisateur n’est configurée, une icône est attribuée de manière aléatoire.

![Propriétés de l’utilisateur](assets/user-properties.png)

### En-tête de l’éditeur universel {#universal-editor-header}

L’en-tête de l’éditeur universel est toujours présent en haut de l’écran, juste en dessous de [l’en-tête Experience Cloud.](#experience-cloud-header) Il vous permet d’accéder rapidement à une autre page pour la modifier et la publier.

![En-tête de l’éditeur universel](assets/universal-editor-header.png)

#### Le menu Hamburger {#hamburger-menu}

Le menu Hamburger n’a pas encore été mis en œuvre.

![Menu Hamburger](assets/hamburger-menu.png)

#### Barre d’emplacement {#location-bar}

La barre d’emplacement affiche l’adresse de la page que vous modifiez. Appuyez ou cliquez pour saisir l’adresse d’une autre page à modifier.

![Barre d’emplacement](assets/location-bar.png)

>[!TIP]
>
>Utiliser le raccourci clavier `L` pour ouvrir la barre d’adresse.

>[!NOTE]
>
>Toute page que vous souhaitez modifier à l’aide de l’éditeur universel doit être [instrumentée pour prendre en charge l’éditeur universel.](getting-started.md)

#### Paramètres de l&#39;émulateur {#emulator}

Appuyez ou cliquez sur l’icône d’émulation pour définir la manière dont l’éditeur universel effectue le rendu de la page.

![Icône Émulateur](assets/emulator.png)

Appuyez ou cliquez sur l’icône d’émulation pour afficher les options.

![Options d’émulation](assets/emulation-options.png)

Par défaut, l’éditeur s’ouvre dans la mise en page pour ordinateur où la hauteur et la largeur sont automatiquement définies par le navigateur.

Vous pouvez également choisir d’émuler un appareil mobile et dans l’éditeur universel :

* Définir son orientation
* Définition de la largeur et de la hauteur
* Modification de l’orientation

#### Ouvrir l’aperçu de l’application {#open-app-preview}

Appuyez ou cliquez sur l’icône Ouvrir l’aperçu de l’application pour ouvrir la page que vous êtes en train de modifier dans son propre navigateur, sans passer par l’éditeur pour prévisualiser les modifications.

![Ouvrir l’aperçu de l’application](assets/open-app-preview.png)

>[!TIP]
>
>Utiliser la touche chaude `O` (lettre O) pour ouvrir l’aperçu de l’application.

#### Publier {#publish}

Appuyez ou cliquez sur le bouton Publier afin de publier les modifications apportées au contenu en direct pour que vos lecteurs puissent les utiliser.

![Bouton Publier](assets/publish.png)

>[!TIP]
>
>Voir le document [Publication de contenu avec l’éditeur visuel universel](publishing.md) pour plus d’informations sur la publication avec l’éditeur universel.

### Rail de mode {#rail}

Le rail de mode est toujours présent le long du côté gauche de l’éditeur. Cela permet de basculer facilement l’éditeur entre différents modes de modification.

![Le rail de mode](assets/mode-rail.png)

#### Mode Aperçu {#preview-mode}

En mode Aperçu, la page rendue dans l’éditeur est telle qu’elle apparaîtrait sur votre service publié. Cela permet à la personne en charge de la création de contenu de parcourir le contenu en cliquant sur des liens, etc.

![Mode Aperçu](assets/preview-mode.png)

>[!TIP]
>
>Utilisez la touche de raccourci `P` pour passer en mode Aperçu.

#### Mode texte {#text-mode}

En mode texte, la page est rendue dans l’éditeur, mais l’auteur du contenu peut cliquer pour sélectionner le contenu texte à modifier. Il s’agit du mode par défaut de l’éditeur lorsqu’une page est chargée.

![Mode texte](assets/text-mode.png)

>[!TIP]
>
>Utiliser la touche chaude `T` pour passer en mode texte.

#### Mode multimédia {#media-mode}

En mode multimédia, la page est rendue dans l’éditeur, mais l’auteur du contenu peut cliquer pour sélectionner le contenu multimédia à modifier.

![Mode média](assets/media-mode.png)

>[!TIP]
>
>Utiliser la touche chaude `M` pour passer en mode média.

#### Mode de composant {#component-mode}

En mode Composant, la page est rendue dans l’éditeur, mais l’auteur du contenu peut cliquer pour sélectionner les composants de page.

![Mode Composant](assets/component-mode.png)

>[!TIP]
>
>Utiliser la touche chaude `C` pour passer en mode composant.

>[!NOTE]
>
>Le mode Composant est toujours en cours de développement et se limite actuellement à la sélection de composants.

### L’éditeur {#editor}

L’éditeur occupe la majeure partie de la fenêtre et est l’endroit où la page indiquée dans [la barre d’emplacement ;](#location-bar) est rendue.

* Si l’éditeur est en mode de modification, par exemple [mode texte](#text-mode) ou [mode média,](#media-mode) le contenu sera modifiable et vous ne pouvez pas suivre les liens.
* Si l’éditeur se trouve dans [mode aperçu,](#preview-mode) le contenu sera navigable et vous pouvez suivre les liens, mais vous ne pouvez pas le modifier.

![Éditeur](assets/editor.png)

### Rail des composants {#component-rail}

Le rail du composant est toujours présent le long du côté gauche de l’éditeur. En fonction de son mode, il peut afficher les détails d’un composant sélectionné dans le contenu ou la hiérarchie du contenu de la page.

![Rail des composants](assets/component-rail.png)

#### Mode Propriétés {#properties-mode}

En mode Propriétés, le rail affiche les propriétés du composant actuellement sélectionné dans l’éditeur. Il s’agit du mode par défaut du rail des composants lorsqu’une page est chargée.

![Mode Propriétés](assets/properties-mode.png)

Les détails du composant sélectionné s’affichent dans le rail. Notez que certains composants ne comportent pas de détails à afficher.

![Détails du composant](assets/component-details.png)

>[!TIP]
>
>Utiliser la touche chaude `D` pour passer en mode propriétés.

#### Mode Arborescence de contenu {#Content-tree-mode}

En mode Arborescence de contenu, le rail affiche la hiérarchie du contenu de la page.

![Mode Arborescence de contenu](assets/content-tree-mode.png)

Lors de la sélection d’un élément dans l’arborescence de contenu, l’éditeur fait défiler le contenu jusqu’à ce qu’il le sélectionne.

![Arborescence de contenu](assets/content-tree.png)

>[!TIP]
>
>Utiliser la touche chaude `F` pour passer en mode arborescence de contenu.


## Modification du contenu {#editing-content}

La modification du contenu est simple et intuitive. Dans les modes de modification ([mode texte](#text-mode), [mode média](#media-mode), et [mode composant](#component-mode)), lorsque vous placez le pointeur de la souris sur le contenu de l’éditeur, le contenu modifiable est mis en surbrillance avec une zone bleue.

![Le contenu modifiable est mis en surbrillance dans une case bleue.](assets/editable-content.png)

Il vous suffit d’appuyer ou de cliquer sur le contenu dans la case bleue pour lancer un éditeur statique et pouvoir ainsi apporter vos modifications. Appuyez sur Entrée ou Retour pour enregistrer les modifications.

![Modification du contenu](assets/editing-content.png)

Notez qu’en mode d’édition, le fait d’appuyer ou de cliquer sur du contenu sélectionne ce dernier en vue de le modifier. Si vous souhaitez parcourir votre contenu en suivant les liens, passez en [mode Aperçu.](#preview-mode)

Selon le mode dans lequel vous vous trouvez et le contenu que vous sélectionnez, il se peut que vous disposiez de différentes options d’édition statique. En outre, vous pouvez consulter des propriétés supplémentaires pour le contenu à l’aide de la variable [rail de composant.](#component-rail)

## Prévisualisation du contenu {#previewing-content}

Une fois le contenu modifié, vous aimez généralement le parcourir pour voir à quoi il ressemble dans le contenu d’autres pages. En [mode Aperçu](#preview-mode), vous pouvez cliquer sur les liens pour parcourir votre contenu comme le ferait un lecteur ou une lectrice. Le contenu est rendu dans l’éditeur tel qu’il serait publié.

Notez qu’en mode Aperçu, le fait d’appuyer ou de cliquer sur le contenu fait réagir ce dernier comme il le ferait avec un lecteur ou une lectrice du contenu. Si vous souhaitez sélectionner le contenu à modifier, basculez vers un mode de modification tel que [mode texte](#text-mode) ou [mode média.](#media-mode)

## Ressources supplémentaires {#additional-resources}

Pour en savoir plus sur l’éditeur universel, consultez ces documents.

* [Présentation de l’éditeur universel](introduction.md) - Découvrez comment Universal Editor permet de modifier n’importe quel aspect de contenu dans n’importe quelle mise en oeuvre afin de vous permettre de proposer des expériences exceptionnelles, d’augmenter la vitesse du contenu et de fournir une expérience de développement à la pointe de la technologie.
* [Publication de contenu avec l’éditeur universel](publishing.md) - Découvrez comment l’éditeur visuel universel publie du contenu et comment vos applications peuvent gérer le contenu publié.
* [Prise en main de l’éditeur universel dans AEM](getting-started.md) - Découvrez comment accéder à l’éditeur universel et comment commencer à instrumenter votre première application AEM pour l’utiliser.
* [Architecture de l’éditeur universel](architecture.md) - Découvrez l’architecture de l’éditeur universel et le flux de données entre ses services et calques.
* [Attributs et types](attributes-types.md) - Découvrez les attributs et les types de données requis par l’éditeur universel.
* [Authentification de l’éditeur universel](authentication.md) - Découvrez comment l’éditeur universel s’authentifie.
