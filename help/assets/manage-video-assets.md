---
title: 'Gestion des ressources vidéo '
description: Téléchargez, prévisualisation, annotez et publiez des fichiers vidéo dans [!DNL Adobe Experience Manager].
contentOwner: AG
translation-type: tm+mt
source-git-commit: 8b1cc8af67c6d12d7e222e12ac4ff77e32ec7e0e
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 27%

---


# Gestion des ressources vidéo  {#manage-video-assets}

Le format vidéo est un élément essentiel des ressources numériques d’une entreprise. [!DNL Adobe Experience Manager] Les offres développent des offres et des fonctionnalités pour gérer tout le cycle de vie des ressources vidéo après leur création.

Learn how to manage and edit the video assets in [!DNL Adobe Experience Manager Assets]. Le codage et le transcodage vidéo, par exemple, le transcodage FFmpeg, sont possibles à l’aide des Profils de traitement et de [!DNL Dynamic Media] l’intégration. Without [!DNL Dynamic Media] license, [!DNL Experience Manager] provides basic support for videos, such as transcoding using FFmpeg, extraction of preview thumbnails for the supported file formats, and preview in the user interface for formats that are supported for playback in the browser directly.

## Chargement et prévisualisation des ressources vidéo {#upload-and-preview-video-assets}

[!DNL Adobe Experience Manager Assets] génère des prévisualisations pour les fichiers vidéo avec l’extension MP4. Vous pouvez prévisualisation les rendus dans l’interface [!DNL Assets] utilisateur.

1. Dans le dossier ou les sous-dossiers des ressources numériques, accédez à l’emplacement où vous souhaitez ajouter des ressources numériques.
1. To upload the asset, click **[!UICONTROL Create]** from the toolbar and choose **[!UICONTROL Files]**. Vous pouvez également faire glisser un fichier vers l’interface utilisateur. Voir [Ressources chargées](manage-digital-assets.md#uploading-assets) pour plus d’informations.
1. To preview a video in the card view, click the **[!UICONTROL Play]** ![play option](assets/do-not-localize/play.png) option on the video asset. Vous pouvez suspendre ou lire une vidéo en mode Carte uniquement. The [!UICONTROL Play] and [!UICONTROL Pause] options are not available in the list view.
1. To preview the video in the asset details page, select **[!UICONTROL Edit]** on the card. La vidéo se joue dans le lecteur vidéo natif du navigateur. Vous pouvez lire, suspendre, afficher la vidéo en plein écran et en contrôler le volume.

## Publication de ressources vidéo {#publish-video-assets}

Après la publication, vous pouvez inclure les fichiers vidéo dans une page Web sous la forme d’une URL ou les incorporer directement. Pour plus d’informations, voir [Publication de fichiers](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)Contenu multimédia dynamique.

## Transcoder à l’aide du Profil de traitement {#transcode-video}

[!DNL Experience Manager] en tant que Cloud Service vous permet d’effectuer un transcodage de base de fichiers vidéo MP4 à l’aide de Profils de traitement. Cette fonctionnalité vous permet non seulement de télécharger mais aussi de prévisualisation et de mettre à l’échelle un fichier vidéo MP4.

![Création d’un Profil de traitement pour le transcodage vidéo dans le Experience Manager](assets/video-processing-profile-for-mp4.png)

*Figure : Profil de traitement pour le transcodage vidéo dans[!DNL Experience Manager].*

Si vous indiquez uniquement la largeur ou la hauteur et laissez l’autre champ vide, les rendus conservent les proportions. Actuellement, seul le codec h264 est disponible pour le transcodage.

Pour traiter des fichiers à l’aide d’un profil de traitement, ajoutez un profil à un dossier. Voir [Utilisation de profils de traitement pour traiter des ressources](/help/assets/asset-microservices-configure-and-use.md#use-profiles).

## Annotation de ressources vidéo {#annotate-video-assets}

1. Dans la [!DNL Assets] console, sélectionnez **[!UICONTROL Modifier]** sur la carte de ressources pour afficher la page des détails de la ressource.
1. Pour lire la vidéo, cliquez sur **[!UICONTROL Prévisualisation]**.
1. To annotate the video, click **[!UICONTROL Annotate]**. Une annotation est ajoutée au moment (image) particulier de la vidéo. Lorsque vous annotez, vous pouvez dessiner sur le canevas et inclure un commentaire avec le dessin. Les commentaires sont automatiquement enregistrés. Pour quitter l’assistant d’annotation, cliquez sur **[!UICONTROL Fermer]**.
1. Pour passer à un point spécifique de la vidéo, indiquez le moment en secondes dans le champ **texte** et cliquez sur **Aller**. Par exemple, pour sauter les 20 premières secondes de la vidéo, saisissez 20 dans le champ texte.
1. Pour l’afficher dans la chronologie, cliquez sur une annotation. Pour supprimer l’annotation de la chronologie, cliquez sur **[!UICONTROL Supprimer]**.

## Bonnes pratiques et restrictions {#tips-limitations}

* Sans licence Contenu multimédia dynamique, vous ne pouvez traiter que les fichiers MP4 à l’aide de profils de traitement.
* Pour le transcodage de base à l’aide de

>[!MORELIKETHIS]
>
>* [Documentation](/help/assets/dynamic-media/video.md)vidéo sur les médias dynamiques.
>* [En savoir plus sur l’utilisation, les types et la configuration des profils](/help/assets/asset-microservices-configure-and-use.md)de traitement.

