---
title: Utilisation de Dynamic Media
description: Découvrez Dynamic Media et utilisez Dynamic Media pour diffuser des ressources à des fins d’utilisation sur le web, les appareils mobiles et les réseaux sociaux.
contentOwner: Rick Brough
feature: Dynamic Media,Asset Management
role: Admin,User
exl-id: 3ec3cb85-88ce-4277-a45c-30e52c75ed42
source-git-commit: 57fb7a011cb2da853cdca4f3233cd56775f4a459
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 52%

---

# Utilisation de Dynamic Media {#working-with-dynamic-media}

[Dynamic Media](https://business.adobe.com/fr/products/experience-manager/assets/dynamic-media.html) fournit des ressources visuelles de marchandisage et de marketing à la demande, automatiquement dimensionnées pour une utilisation sur le web, les appareils mobiles et les réseaux sociaux. À partir d’un ensemble de ressources de sources originales, Dynamic Media génère et diffuse en temps réel plusieurs variantes d’un même contenu enrichi par le biais de son réseau mondial et évolutif, aux performances optimisées.

Dynamic Media permet un affichage interactif, notamment le zoom, la rotation à 360° et la vidéo. Dynamic Media incorpore de manière unique les workflows de la gestion des ressources numériques d’Adobe Experience Manager pour simplifier et rationaliser le processus de gestion des campagnes numériques.

<!-- >[!NOTE]
>
>A Community article is available on [Working with Adobe Experience Manager and Dynamic Media](https://helpx.adobe.com/experience-manager/using/aem_dynamic_media.html). -->

## Qu’est-ce que Dynamic Media ?

Dynamic Media in Adobe Experience Manager (AEM) est une solution puissante conçue pour vous aider à gérer, diffuser et optimiser des ressources multimédias enrichies telles que des images et des vidéos sur plusieurs plateformes numériques. Il transforme les médias statiques en expériences dynamiques et attrayantes en autorisant des modifications en temps réel, telles que le redimensionnement, le recadrage et l’ajustement de la qualité en fonction de l’appareil ou de la taille de l’écran de l’utilisateur. Avec Dynamic Media, vos ressources s’adaptent automatiquement pour offrir une expérience visuelle optimale, que les utilisateurs se trouvent sur un ordinateur de bureau, un appareil mobile ou une tablette.

L’un des principaux avantages de Dynamic Media réside dans sa capacité à rationaliser la gestion des médias. Vous n’avez pas besoin de créer plusieurs versions d’images ou de vidéos : Dynamic Media gère tout cela en fournissant le format le plus approprié à chaque situation. Par exemple, les entreprises d’e-commerce peuvent tirer parti de vues de produits à 360 degrés ou d’images zoomables pour créer des expériences interactives, tandis que les sites web riches en contenu peuvent garantir une diffusion vidéo en continu rapide et de haute qualité. Cela se traduit par des temps de chargement plus rapides et des expériences utilisateur plus attrayantes, ce qui entraîne une plus grande satisfaction des clients et de meilleurs taux de conversion.

Dynamic Media s’intègre de manière transparente à votre système de gestion des ressources numériques (DAM) dans AEM, ce qui vous permet de stocker, d’organiser et de déployer vos médias sur une seule plateforme. Cette approche centralisée simplifie la collaboration entre les équipes et fournit des informations en temps réel sur les performances des ressources. Que vous vous consacriez à diffuser des visuels captivants ou à améliorer les interactions utilisateur pilotées par les médias, Dynamic Media vous aide à optimiser votre contenu pour n’importe quel canal, ce qui en fait un outil essentiel pour les entreprises qui souhaitent améliorer leur présence numérique.

## Tâches que vous pouvez effectuer avec Dynamic Media {#what-you-can-do-with-dynamic-media}

Dynamic Media permet de gérer les ressources avant de les publier. L’utilisation des ressources en général est traitée en détail dans la section [Utilisation d’Assets numériques](/help/assets/manage-digital-assets.md). Les rubriques générales incluent le chargement, le téléchargement, la modification et la publication des ressources, l’affichage et la modification des propriétés et la recherche de ressources.

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
* [Utilisation des aperçus rapides pour créer des fenêtres contextuelles personnalisées](custom-pop-ups.md)

Consultez également [Configuration de Dynamic Media](administering-dynamic-media.md).

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

### Visionneuses d’images Dynamic Media, visionneuses à 360°, visionneuses de supports variés {#image-sets-spins-sets-mixed-media-sets}

Des visionneuses d’images, à 360° et de supports variés sont disponibles lorsque Dynamic Media est activé.

![chlimage_1-359](assets/chlimage_1-359.png)

### Rendus PTIFF activés pour Dynamic Media {#ptiff-renditions}

Les ressources compatibles avec Dynamic Media comprennent les `pyramid.tiffs`.

![chlimage_1-360](assets/chlimage_1-360.png)

### Modification des vues des ressources Dynamic Media {#asset-views-change}

Lorsque Dynamic Media est activé, vous pouvez effectuer un zoom avant ou arrière en cliquant sur les boutons `+` et `-`. Vous pouvez également choisir d’effectuer un zoom sur certaines zones. L’option Rétablir vous ramène à la version d’origine. Vous pouvez afficher l’image en plein écran en cliquant sur les flèches diagonales. Lorsque Dynamic Media est activé, cette fonctionnalité ressemble à celle-ci :

![chlimage_1-361](assets/chlimage_1-361.png)

Lorsque Dynamic Media est désactivé, vous pouvez effectuer un zoom avant et arrière et revenir à la taille d’origine :

![chlimage_1-362](assets/chlimage_1-362.png)
