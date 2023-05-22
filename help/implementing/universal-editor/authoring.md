---
title: Création de contenu avec l’éditeur universel
description: Découvrez à quel point il est facile et intuitif pour les personnes en charge de la création de créer du contenu à l’aide de l’éditeur universel.
exl-id: 15fbf5bc-2e30-4ae7-9e7f-5891442228dd
source-git-commit: 9cff6e94b38016f008fd8177be2e071a530d80b6
workflow-type: tm+mt
source-wordcount: '1152'
ht-degree: 100%

---

# Création de contenu avec l’éditeur universel {#authoring}

Découvrez à quel point il est facile et intuitif pour les personnes en charge de la création de créer du contenu à l’aide de l’éditeur universel.

## Présentation {#introduction}

L’éditeur universel permet de modifier n’importe quel aspect de contenu dans n’importe quelle mise en œuvre afin de fournir des expériences exceptionnelles, d’augmenter la vitesse du contenu et d’offrir une expérience de développement à la pointe de la technologie.

Pour ce faire, il fournit aux personnes en charge de la création de contenu une interface utilisateur intuitive qui nécessite une formation minimale pour se lancer et commencer à modifier le contenu.

>[!TIP]
>
>Pour une présentation plus détaillée de l’éditeur universel, consultez le document [Présentation de l’éditeur universel.](introduction.md)

>[!NOTE]
>
>L’éditeur universel est toujours en développement et ne peut pas modifier tous les types de contenu pour le moment.

## Préparer l’application {#prepare-app}

Pour créer du contenu pour une application à l’aide de l’éditeur universel, l’application doit être instrumentée par un développeur ou une développeuse afin de prendre en charge l’éditeur.

>[!TIP]
>
>Consultez le document [Prise en main de l’éditeur universel dans AEM](getting-started.md) pour obtenir un exemple de configuration d’une application AEM pour qu’elle fonctionne avec l’éditeur universel.

## Se connecter {#sign-in}

Une fois que l’application est instrumentée pour fonctionner avec l’éditeur universel, vous devez vous connecter à l’éditeur universel. Vous aurez besoin d’un Adobe ID pour vous connecter et d’[avoir accès à l’éditeur universel.](getting-started.md#request-access)

Une fois connecté, saisissez l’URL de la page que vous souhaitez modifier dans la [barre d’adresse.](#address-bar) pour commencer à [modifier le contenu.](#edit-content)

## Présentation de l’interface utilisateur {#ui}

L’interface utilisateur est divisée en quatre zones principales.

* [En-tête Experience Cloud](#experience-cloud-header)
* [En-tête de l’éditeur universel](#universal-editor-header)
* [Le rail](#rail)
* [L’éditeur](#editor)

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

Cette icône contiendra un badge indiquant le nombre de [notifications](/help/implementing/cloud-manager/notifications.md) incomplètes actuellement attribuées.

![Notifications](assets/notifications.png)

#### Propriétés de l’utilisateur ou de l’utilisatrice {#user-properties}

Appuyez ou cliquez sur l’icône représentant votre utilisateur ou votre utilisatrice pour accéder à vos paramètres utilisateur. Si vous n’avez configuré aucune image d’utilisateur, une icône est attribuée de manière aléatoire.

![Propriétés de l’utilisateur](assets/user-properties.png)

### En-tête de l’éditeur universel {#universal-editor-header}

L’en-tête de l’éditeur universel est toujours présent en haut de l’écran, juste en dessous de [l’en-tête Experience Cloud.](#experience-cloud-header) Il vous permet d’accéder rapidement à une autre page à modifier et de publier la page active.

![En-tête de l’éditeur universel](assets/universal-editor-header.png)

#### Le menu Hamburger {#hamburger-menu}

Le menu Hamburger n’a pas encore été mis en œuvre.

![Menu Hamburger](assets/hamburger-menu.png)

#### Barre d’emplacement {#Location-bar}

La barre d’emplacement affiche l’adresse de la page que vous modifiez. Appuyez ou cliquez pour saisir l’adresse d’une autre page à modifier.

![Barre d’emplacement](assets/address-bar.png)

>[!TIP]
>
>Utiliser le raccourci clavier `L` pour ouvrir la barre d’adresse.

>[!NOTE]
>
>Toute page que vous souhaitez modifier à l’aide de l’éditeur universel doit être [instrumentée pour prendre en charge l’éditeur universel.](getting-started.md)

#### Ouvrir l’aperçu de l’application {#open-app-preview}

Appuyez ou cliquez sur l’icône Ouvrir l’aperçu de l’application pour ouvrir la page que vous êtes en train de modifier dans son propre navigateur, sans passer par l’éditeur pour prévisualiser les modifications.

![Ouvrir l’aperçu de l’application](assets/open-app-preview.png)

>[!TIP]
>
>Utiliser la touche de raccourci `O` pour ouvrir l’aperçu de l’application.

#### Publier {#publish}

Appuyez ou cliquez sur le bouton Publier pour publier les modifications apportées au contenu dynamique pour que vos lecteurs et lectrices puissent les utiliser.

![Bouton Publier](assets/publish.png)

>[!TIP]
>
>Voir le document [Publication de contenu avec l’éditeur visuel universel](publishing.md) pour plus d’informations sur la publication avec l’éditeur universel.

### Le rail {#rail}

Un rail est toujours présent le long du côté gauche de l’éditeur. Il permet de faire basculer facilement l’éditeur entre le mode aperçu et le mode d’édition.

![Le rail](assets/rail.png)

#### Mode Aperçu {#preview-mode}

En mode Aperçu, la page rendue dans l’éditeur est telle qu’elle apparaîtrait sur votre service publié. Cela permet à la personne en charge de la création de contenu de parcourir le contenu en cliquant sur des liens, etc.

![Mode Aperçu](assets/preview-mode.png)

>[!TIP]
>
>Utilisez la touche de raccourci `P` pour passer en mode Aperçu.

#### Mode d’édition {#edit-mode}

En mode d’édition, la page est rendue dans l’éditeur, mais la personne en charge de la création de contenu peut cliquer sur un contenu pour le modifier. Il s’agit du mode par défaut de l’éditeur lorsqu’une page est chargée.

![Mode d’édition](assets/edit-mode.png)

### L’éditeur {#editor}

L’éditeur occupe la majeure partie de la fenêtre et c’est l’endroit où la page indiquée dans [la barre d’adresse](#address-bar) est rendue.

Selon si l’éditeur se trouve en [mode d’édition](#edit-mode) ou en [mode Aperçu,](#edit-mode) le contenu sera modifiable ou navigable, respectivement.

![Éditeur](assets/editor.png)

## Modification du contenu {#editing-content}

La modification du contenu est simple et intuitive. En [mode d’édition,](#edit-mode) lorsque vous placez le pointeur de la souris sur le contenu de l’éditeur, le contenu modifiable se met en surbrillance dans une case bleue.

![Le contenu modifiable est mis en surbrillance dans une case bleue.](assets/editable-content.png)

Il vous suffit d’appuyer ou de cliquer sur le contenu dans la case bleue pour lancer un éditeur statique et pouvoir ainsi apporter vos modifications. Appuyez sur Entrée ou Retour pour enregistrer les modifications.

![Modification du contenu](assets/editing-content.png)

Notez qu’en mode d’édition, le fait d’appuyer ou de cliquer sur du contenu sélectionne ce dernier en vue de le modifier. Si vous souhaitez parcourir votre contenu en suivant les liens, passez en [mode Aperçu.](#preview-mode)

## Prévisualisation du contenu {#previewing-content}

Une fois le contenu modifié, vous aimez généralement le parcourir pour voir à quoi il ressemble dans le contenu d’autres pages. En [mode Aperçu](#preview-mode), vous pouvez cliquer sur les liens pour parcourir votre contenu comme le ferait un lecteur ou une lectrice. Le contenu est rendu dans l’éditeur tel qu’il serait publié.

Notez qu’en mode Aperçu, le fait d’appuyer ou de cliquer sur le contenu fait réagir ce dernier comme il le ferait avec un lecteur ou une lectrice du contenu. Si vous souhaitez sélectionner le contenu à modifier, passez au [mode d’édition.](#edit-mode)

## Ressources supplémentaires {#additional-resources}

Pour en savoir plus sur l’éditeur universel, consultez ces documents.

* [Présentation de l’éditeur universel](introduction.md) - Découvrez comment l’éditeur universel permet de modifier n’importe quel aspect de n’importe quel contenu et dans n’importe quelle mise en œuvre afin de fournir des expériences exceptionnelles, d’augmenter la vitesse du contenu et de fournir une expérience de développement à la pointe de la technologie.
* [Publication de contenu avec l’éditeur universel](publishing.md) - Découvrez comment l’éditeur visuel universel publie du contenu et comment vos applications peuvent gérer le contenu publié.
* [Prise en main de l’éditeur universel dans AEM](getting-started.md) - Découvrez comment accéder à l’éditeur universel et comment commencer à instrumenter votre première application AEM pour l’utiliser.
* [Architecture de l’éditeur universel](architecture.md) - Découvrez l’architecture de l’éditeur universel et le flux de données entre ses services et calques.
* [Attributs et types](attributes-types.md) - Découvrez les attributs et les types de données requis par l’éditeur universel.
* [Authentification de l’éditeur universel](authentication.md) - Découvrez comment l’éditeur universel s’authentifie.
