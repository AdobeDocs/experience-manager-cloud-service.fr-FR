---
title: Utilisation de Dynamic Media
description: Découvrez comment utiliser Dynamic Media pour diffuser des ressources pour une utilisation sur le web, les appareils mobiles et les réseaux sociaux.
translation-type: tm+mt
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6

---


# Utilisation de Dynamic Media {#working-with-dynamic-media}

[Dynamic Media](https://www.adobe.com/solutions/web-experience-management/dynamic-media.html) fournit des ressources visuelles de marchandisage et de marketing à la demande, automatiquement dimensionnées pour une utilisation sur le Web, les appareils mobiles et les réseaux sociaux. A partir d’un ensemble de ressources, Dynamic Media génère et diffuse en temps réel plusieurs variantes d’un même contenu enrichi par le biais de son réseau mondial et évolutif, aux performances optimisées.

Dynamic Media permet un affichage interactif, notamment le zoom, la rotation à 360° et la vidéo. Dynamic Media incorpore de manière unique les processus de la gestion des actifs numériques d’Adobe Experience Manager pour simplifier et rationaliser le processus de gestion des campagnes numériques.

>[!NOTE]
>
>Un article de la communauté (en anglais) intitulé [Working with Adobe Experience Manager and Dynamic Media](https://helpx.adobe.com/experience-manager/using/aem_dynamic_media.html) porte sur l’utilisation d’Adobe Experience Manager et de Dynamic Media.

## Tâches que vous pouvez effectuer avec Dynamic Media {#what-you-can-do-with-dynamic-media}

Dynamic Media permet de gérer les ressources avant de les publier. L’utilisation générale des ressources est décrite en détail à la rubrique [Utilisation de ressources numériques](/help/assets/manage-digital-assets.md). Les rubriques générales incluent le chargement, le téléchargement, la modification et la publication des ressources, l’affichage et la modification des propriétés et la recherche de ressources.

Les fonctionnalités Contenu multimédia dynamique uniquement sont les suivantes :

* [Bannières de carrousel](carousel-banners.md)
* [Visionneuses d’images](image-sets.md)
* [Images interactives](interactive-images.md)
* [Vidéos interactives](interactive-videos.md)
* [Visionneuses de supports variés](mixed-media-sets.md)
* [Images panoramiques](panoramic-images.md)

* [Visionneuses à 360°](spin-sets.md)
* [Vidéo](video.md)
* [Diffusion de ressources Dynamic Media](delivering-dynamic-media-assets.md)
* [Gestion des ressources](managing-assets.md)
* [Utilisation d’aperçus rapides pour créer des fenêtres contextuelles personnalisées](custom-pop-ups.md)

Voir également [Configuration de Dynamic Media](administering-dynamic-media.md).

<!-- 

OBSOLETE UNTIL INTEGRATING SCENE7 TOPIC GETS A MAJOR UPDATE
>[!NOTE]
>
>To understand the differences between using Dynamic Media and integrating Dynamic Media Classic with AEM, see [Dynamic Media Classic integration versus Dynamic Media](/help/sites-cloud/administering/integrating-scene7.md#aem-scene-integration-versus-dynamic-media).

-->

## Contenu multimédia dynamique activé ou Contenu multimédia dynamique désactivé {#dynamic-media-on-versus-dynamic-media-off}

Vous pouvez déterminer si la fonction Contenu multimédia dynamique est activée en fonction des caractéristiques suivantes :

* Des rendus dynamiques sont disponibles lors du téléchargement ou de la prévisualisation de fichiers.
* Des visionneuses d’images, des visionneuses à 360°, des visionneuses de supports mixtes sont disponibles.
* Des rendus PTIFF sont créés.

Lorsque vous cliquez sur un fichier d’image, la vue du fichier est différente avec l’option Contenu multimédia dynamique activée. Dynamic Media utilise les visionneuses HTML5 à la demande.

### Dynamic renditions {#dynamic-renditions}

Des rendus dynamiques, tels que des paramètres d’image et de visionneuse prédéfinis (sous **[!UICONTROL Dynamique]**), sont disponibles lorsque Dynamic Media est activé.

![chlimage_1-358](assets/chlimage_1-358.png)

### Visionneuses d’images, à 360° et de supports variés {#image-sets-spins-sets-mixed-media-sets}

Des visionneuses d’images, à 360° et de supports variés sont disponibles lorsque Dynamic Media est activé.

![chlimage_1-359](assets/chlimage_1-359.png)

### PTIFF renditions {#ptiff-renditions}

Dynamic media enabled assets include `pyramid.tiffs`.

![chlimage_1-360](assets/chlimage_1-360.png)

### Modification des vues des ressources {#asset-views-change}

With Dynamic Media enabled, you can zoom in and out by clicking the `+` and `-` buttons. You can also click/tap to zoom into certain area. Revert brings you to the original version and you can make the image full screen by clicking the diagonal arrows. Dynamic Media enabled looks like this:

![chlimage_1-361](assets/chlimage_1-361.png)

Avec Contenu multimédia dynamique désactivé, vous pouvez effectuer un zoom avant ou arrière et rétablir la taille d’origine :

![chlimage_1-362](assets/chlimage_1-362.png)
