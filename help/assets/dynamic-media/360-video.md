---
title: Vidéo 360/VR
description: Découvrez comment utiliser les vidéos à 360° et de réalité virtuelle (VR) dans Dynamic Media.
feature: Vidéo 360 VR
role: Business Practitioner
exl-id: ffd092d3-2188-47b0-a475-8bfa660c03c1
translation-type: tm+mt
source-git-commit: 1fe6ce1259972c1805d934327aa2f24cdcdc0bc8
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 59%

---

# Vidéo 360/VR {#vr-video}

Les vidéos 360 enregistrent une vue dans chaque direction au même moment. Elles sont tournées à l’aide d’une caméra omnidirectionnelle ou d’un ensemble de caméras. Lors de la lecture, sur un écran plat, l’utilisateur contrôle l’angle d’affichage ; la lecture sur les périphériques mobiles applique généralement leurs commandes gyroscopiques intégrées.

Dynamic Media inclut une prise en charge native de la diffusion de ressources vidéo 360. Par défaut, aucune configuration supplémentaire n’est nécessaire pour l’affichage ou la lecture. Vous diffusez une vidéo 360 avec des extensions vidéo standard telles que .mp4, .mkv et .mov. Le codec le plus courant est H.264.

Vous pouvez utiliser la visionneuse vidéo 360/VR pour effectuer le rendu d’une vidéo équirectangulaire. Le résultat est une expérience de visualisation immersive d&#39;une pièce, d&#39;une propriété, d&#39;un lieu, d&#39;un paysage, d&#39;une procédure médicale, etc.

L’audio spatial n’est actuellement pas pris en charge ; si l’audio est mixé en stéréo, la balance (G/D) ne change pas lorsque le client change l’angle de vue de la caméra.

Voir [Utilisation de vidéos 360 Dynamic Media et d’une miniature vidéo personnalisée avec AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-360-video-custom-thumbnail-feature-video-use.html#dynamic-media).

Voir également [Gestion des paramètres prédéfinis de visionneuse](/help/assets/dynamic-media/managing-viewer-presets.md).

## Vidéo 360 en action {#video-in-action}

Appuyez sur [Station spatiale 360](https://mobiletest.scene7.com/s7viewers/html5/Video360Viewer.html?asset=Viewers/space_station_360-AVS) pour ouvrir une fenêtre de navigateur et visionner une vidéo à 360 degrés. Pendant la lecture de la vidéo, faites glisser le pointeur vers un nouvel emplacement pour modifier l’angle de visualisation.

![Exemple de vidéo 360](assets/6_5_360videoiss_simplified.png)
*Image vidéo de la station spatiale 360*

## Vidéo 360/VR et Adobe Premiere Pro {#vr-video-and-adobe-premiere-pro}

Vous pouvez utiliser Adobe Premier Pro pour visualiser et modifier des séquences vidéo 360/VR. Par exemple, vous pouvez placer des logos et du texte correctement dans une scène et appliquer des effets et des transitions conçus spécialement pour les médias équirectangulaires.

Voir [Modification de la vidéo 360/VR](https://helpx.adobe.com/fr/premiere-pro/how-to/edit-360-vr-video.html).

## Chargement de ressources pour une utilisation avec la visionneuse de vidéos 360 {#uploading-assets-for-use-with-the-video-viewer}

Les ressources vidéo 360 chargées dans Experience Manager sont considérées comme des fichiers **multimédias** sur une page de ressource, tout comme une ressource vidéo normale.

![6_5_360video-selecttopreview](assets/6_5_360video-selecttopreview.png)
*Une ressource vidéo 360 chargée et affichée en mode Carte. La ressource est considérée comme multimédia.*

**Pour charger des ressources pour une utilisation avec la visionneuse de vidéos 360 :**

1. Créez un dossier dédié à votre ressource vidéo 360.
1. [Appliquez un profil de vidéo adaptative au dossier](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders).

   Les exigences du rendu de contenu vidéo 360 sont plus élevées pour la résolution vidéo source et pour la résolution des rendus codée que pour le contenu vidéo standard.

   Vous pouvez utiliser le profil de vidéo adaptative prêt à l’emploi qui est déjà fourni avec Dynamic Media. Cependant, la qualité vidéo est nettement inférieure à 360 que celle obtenue pour les vidéos non codées en 360 avec les mêmes paramètres que pour les vidéos non codées en 360. Par conséquent, si une vidéo 360 de qualité supérieure est requise, procédez comme suit :

   * Idéalement, votre contenu vidéo de 360 d’origine est doté de l’une des résolutions suivantes :

      * 1080p – 1920 x 1080, connu sous le nom de résolution Full HD ou FHD ou,
      * 2160p – 3840 x 2160, connu sous le nom de résolution 4K, UHD ou Ultra HD. Cette grande résolution d&#39;affichage est le plus souvent présente sur les téléviseurs et les moniteurs d&#39;ordinateur de grande qualité. La résolution 2160p est souvent appelée « 4K », car la largeur est proche de 4 000 pixels. En d’autres termes, elle offre quatre fois plus de pixels que la résolution 1080p.
   * [Créez un ](/help/assets/dynamic-media/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming) profil de vidéo adaptative personnalisé avec des rendus de meilleure qualité. Par exemple, vous pouvez créer un Profil de vidéo adaptative qui contient les trois paramètres suivants :

      * Largeur=auto; Hauteur=720; Débit=2 500 kbit/s
      * Largeur=auto; Hauteur=1080; Débit=5 000 kbit/s
      * Largeur=auto; Hauteur=1440; Débit=6 600 kbit/s
   * Traitez le contenu vidéo 360 dans un dossier destiné exclusivement aux ressources vidéo 360.

   Cette approche impose des exigences plus élevées au réseau et au processeur de l’utilisateur final.

1. [Chargez votre vidéo dans le dossier](/help/assets/manage-video-assets.md#upload-and-preview-video-assets).

<!--

## Overriding the default aspect ratio of 360 videos  {#overriding-the-default-aspect-ratio-of-videos}

For an uploaded asset to qualify as a 360 video that you intend to use with the 360 Video viewer, the asset must have an aspect ratio of 2.

By default, AEM detects video as "360" if its aspect ratio (width/height) is 2.0. If you are an Administrator, you can override the default aspect ratio setting of 2 by setting the optional `s7video360AR` property in CRXDE Lite at the following:

* `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

  * **Property type**: Double
  * **Value**: floating-point aspect ratio, default 2.0.

After you set this property, it takes effect immediately on both existing videos and newly uploaded videos.

The aspect ratio applies to 360 video assets for the asset details page and the [Video 360 Media WCM component](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#dynamic-media-components).

Start by uploading 360 Videos.

-->

## Prévisualisation d’une vidéo 360 {#previewing-video}

Vous pouvez utiliser la Prévisualisation pour voir comment votre vidéo 360 s’affiche pour les clients et vous assurer qu’elle se comporte comme prévu.

Voir également [Modification de paramètres de visionneuse prédéfinis](/help/assets/dynamic-media/managing-viewer-presets.md#editing-viewer-presets).

Lorsque vous êtes satisfait de la vidéo 360, vous pouvez la publier.

Voir [Incorporation de la visionneuse de vidéos ou d’images dans une page web](/help/assets/dynamic-media/embed-code.md).
Voir [Liaison d’URL à une application web](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md). La méthode de liaison basée sur des URL n’est pas possible si votre contenu interactif comporte des liens avec des URL relatives, en particulier des liens vers des pages de sites Experience Manager.
Reportez-vous à la section [Ajout de ressources Dynamic Media aux pages](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

**Prévisualisation de vidéos 360**

1. Dans **[!UICONTROL Assets]**, accédez à une vidéo 360 que vous avez créée. Pour l’ouvrir en mode prévisualisation, appuyez sur la ressource vidéo 360.

   ![6_5_360video-selecttopreview-1](assets/6_5_360video-selecttopreview-1.png)

   Pour prévisualisation à la vidéo, appuyez sur la ressource vidéo 360.

1. Dans la page d’aperçu, dans le coin supérieur gauche de la page, appuyez sur le menu déroulant puis sélectionnez **[!UICONTROL Visionneuses]**.

   ![6_5_360video-preview-viewers](assets/6_5_360video-preview-viewers.png)

   Dans la liste des visionneuses, appuyez sur **[!UICONTROL Video360_social]**, puis effectuez l’une des opérations suivantes :

   * Pour modifier l’angle d’affichage de la scène statique, faites glisser le pointeur sur la vidéo.
   * Pour commencer la lecture, appuyez sur le bouton **[!UICONTROL Lecture]** de la vidéo. Pendant la lecture de la vidéo, faites glisser le pointeur sur la vidéo pour modifier l’angle de visionnage.

   ![6_5_360video-preview-video360-social ](assets/6_5_360video-preview-video360-social.png)*Capture d’écran d’une vidéo 360.*

   * Dans la liste des visionneuses, appuyez sur **[!UICONTROL Video360VR]**.

      Virtual Reality (VR) est un contenu vidéo immersif accessible à l&#39;aide de casques de réalité virtuelle. Comme pour les vidéos ordinaires, vous créez des vidéos VR au début lorsqu&#39;une vidéo est enregistrée ou capturée à l&#39;aide de caméras vidéo à 360 degrés.
   ![6_5_360video-preview-video360vr](assets/6_5_360video-preview-video360vr.png)
   *Capture d’écran d’une vidéo 360 VR*

1. Près de l’angle supérieur droit de la page de prévisualisation, appuyez sur **[!UICONTROL Fermer]**.

## Publication d’une vidéo 360 {#publishing-video}

Pour utiliser la vidéo 360, vous devez la publier. La publication d’une vidéo 360 active l’URL et le code intégré. Elle publie également la vidéo 360 sur le cloud Dynamic Media intégré au CDN pour un débit évolutif et performant.

Voir [Publication de ressources Dynamic Media](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) pour savoir comment publier des vidéos 360.
Voir aussi [Incorporation de la visionneuse de vidéos ou d’images dans une page web](/help/assets/dynamic-media/embed-code.md).
Voir aussi [Liaison d’URL à une application web](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md). La méthode de liaison basée sur des URL n’est pas possible si votre contenu interactif comporte des liens avec des URL relatives, en particulier des liens vers des pages de sites Experience Manager.
Voir aussi [Ajout de ressources Dynamic Media aux pages](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).
