---
title: Utilisation de Dynamic Media
description: Découvrez comment utiliser Dynamic Media pour diffuser des ressources pour une utilisation sur le web, les appareils mobiles et les réseaux sociaux.
role: Administrator,Business Practitioner
exl-id: 3ec3cb85-88ce-4277-a45c-30e52c75ed42
source-git-commit: 1ad89be4ebddec0705c6f557fed3d697b9f1f3a7
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 83%

---

# Utilisation de Dynamic Media {#working-with-dynamic-media}

[Dynamic Media](https://business.adobe.com/products/experience-manager/assets/dynamic-media.html) fournit des ressources visuelles de marchandisage et de marketing à la demande, automatiquement dimensionnées pour une utilisation sur le web, les appareils mobiles et les réseaux sociaux. À partir d’un ensemble de ressources de sources originales, Dynamic Media génère et diffuse en temps réel plusieurs variantes d’un même contenu enrichi par le biais de son réseau mondial et évolutif, aux performances optimisées.

Dynamic Media offre des expériences de visualisation interactives, notamment des fonctions vidéo, de zoom et de rotation à 360°. Cette fonctionnalité intègre de manière unique les processus de la solution de gestion des ressources numériques Adobe Experience Manager (Assets), afin de simplifier et rationaliser le processus de gestion des campagnes numériques.

<!-- >[!NOTE]
>
>A Community article is available on [Working with Adobe Experience Manager and Dynamic Media](https://helpx.adobe.com/experience-manager/using/aem_dynamic_media.html). -->

## Tâches que vous pouvez effectuer avec Dynamic Media  {#what-you-can-do-with-dynamic-media}

Dynamic Media permet de gérer les ressources avant de les publier. L’utilisation générale des ressources est décrite en détail à la rubrique [Utilisation de ressources numériques](/help/assets/manage-digital-assets.md). Les rubriques générales incluent le chargement, le téléchargement, la modification et la publication des ressources, l’affichage et la modification des propriétés et la recherche de ressources.

Les fonctionnalités uniquement incluses dans Dynamic Media sont les suivantes :

* [Bannières de carrousel](carousel-banners.md)
* [Visionneuses d’images](image-sets.md)
* [Images interactives](interactive-images.md)
* [Vidéos interactives](interactive-videos.md)
* [Visionneuses de médias mixtes](mixed-media-sets.md)
* [Images panoramiques](panoramic-images.md)

* [Visionneuses à 360°](spin-sets.md)
* [Vidéo](video.md)
* [Diffusion de ressources Dynamic Media](delivering-dynamic-media-assets.md)
* [Gestion des ressources](managing-assets.md)
* [Utilisation d’aperçus rapides pour créer une fenêtre contextuelle personnalisée®](custom-pop-ups.md)

Voir également [Configuration de Dynamic Media](administering-dynamic-media.md).

<!-- 

OBSOLETE UNTIL INTEGRATING SCENE7 TOPIC GETS A MAJOR UPDATE
>[!NOTE]
>
>To understand the differences between using Dynamic Media and integrating Dynamic Media Classic with AEM, see [Dynamic Media Classic integration versus Dynamic Media](/help/sites-cloud/administering/integrating-scene7.md#aem-scene-integration-versus-dynamic-media).

-->

## Dynamic Media activé ou Dynamic Media désactivé {#dynamic-media-on-versus-dynamic-media-off}

Les caractéristiques suivantes permettent de déterminer si Dynamic Media est activé ou non :

* Des rendus dynamiques sont disponibles lors du téléchargement ou de la prévisualisation des ressources.
* Des visionneuses d’images, à 360° et de supports variés sont disponibles.
* Des rendus PTIFF sont créés.

Lorsque vous cliquez sur une ressource image, l’affichage de la ressource est différent avec Dynamic Media activé. Dynamic Media utilise les visionneuses HTML5 à la demande.

### Rendus dynamiques {#dynamic-renditions}

Des rendus dynamiques, tels que des paramètres d’image et de visionneuse prédéfinis (sous **[!UICONTROL Dynamique]**), sont disponibles lorsque Dynamic Media est activé.

![chlimage_1-358](assets/chlimage_1-358.png)

### Visionneuses d’images, à 360° et de supports variés {#image-sets-spins-sets-mixed-media-sets}

Des visionneuses d’images, à 360° et de supports variés sont disponibles lorsque Dynamic Media est activé.

![chlimage_1-359](assets/chlimage_1-359.png)

### Rendus PTIFF {#ptiff-renditions}

Les ressources prises en charge par Dynamic Media comprennent `pyramid.tiffs`.

![chlimage_1-360](assets/chlimage_1-360.png)

### Modification des vues des ressources {#asset-views-change}

Lorsque Dynamic Media est activé, vous pouvez effectuer un zoom avant ou arrière en cliquant sur les boutons `+` et `-` . Vous pouvez également cliquer/appuyer sur pour effectuer un zoom sur une zone spécifique. L’option Rétablir vous ramène à la version d’origine. Vous pouvez afficher l’image en plein écran en cliquant sur les flèches diagonales. Dynamic Media activé ressemble à ce qui suit :

![chlimage_1-361](assets/chlimage_1-361.png)

Lorsque Dynamic Media est désactivé, vous pouvez effectuer un zoom avant et arrière et revenir à la taille d’origine :

![chlimage_1-362](assets/chlimage_1-362.png)
