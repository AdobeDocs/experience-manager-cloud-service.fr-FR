---
title: Affichage et gestion des rendus dans Experience Manager Assets
description: Découvrez comment AEM Assets et Dynamic Media simplifient la gestion efficace des images avec des rendus d’image statiques et dynamiques.
exl-id: 006dc493-c400-4d0f-b314-c1978582b7fb
feature: Renditions
role: User
source-git-commit: eb5886b5ed6a6f5b52303b4fccf5c266178b36f8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Affichage et gestion des rendus dans Experience Manager Assets{#renditions}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [Bonnes pratiques relatives aux métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Fonctionnalités Dynamic Media avec OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation de développement pour AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Les rendus dans Adobe Experience Manager (AEM) sont des versions personnalisées des ressources numériques, telles que les images, conçues pour différents appareils et plateformes afin d’assurer des performances optimales. AEM facilite la création et la gestion de ces rendus, ce qui améliore l’expérience utilisateur. Vous pouvez créer des miniatures, optimiser des images pour le web ou mobile, ajouter des filigranes, afficher et télécharger des rendus dynamiques ou de recadrage intelligent, et bien plus encore.

Les paramètres d’image prédéfinis Dynamic Media et les rendus de recadrage intelligent favorisent une gestion systématique des images en phase avec les normes de la marque, ce qui optimise la cohésion de la marque. Cela simplifie le processus de localisation et d’utilisation rapide des rendus d’image dynamiques si nécessaire sans accès administrateur.

Les rendus sont classés comme statiques et dynamiques, chaque type présentant des fonctionnalités et des fonctionnalités uniques qui sont expliquées plus en détail.

## Rendus statiques {#static-renditions}

Les rendus statiques sont des versions prégénérées de ressources numériques, généralement créées lors de l’assimilation ou de la modification de ressources. Ces rendus sont optimisés à des fins et plateformes spécifiques, telles que les miniatures web, les formats compatibles avec les appareils mobiles pour le responsive design ou les versions haute résolution pour l’impression, ce qui garantit une expérience efficace et cohérente.
Découvrez comment [afficher et télécharger des rendus statiques](#view-and-download-static-renditions) dans Experience Manager Assets.

### Affichage et téléchargement de rendus statiques{#view-and-download-static-renditions}

Pour afficher les rendus de ressources et les télécharger, procédez comme suit :

1. Dans la vue Assets, cliquez sur **Assets**, accédez à un dossier, sélectionnez une ressource, puis cliquez sur **Détails**.
1. Cliquez sur l’icône du rendu disponible dans le volet de droite.
1. Sélectionnez un rendu pour le prévisualiser, puis cliquez sur ![icône de téléchargement](/help/assets/assets/download-icon.svg) pour le télécharger.

   ![ Afficher et télécharger des rendus dynamiques](/help/assets/assets/view-download-static-rendition.png)

## Rendus dynamiques {#dynamic-renditions}

Les rendus dynamiques sont des versions personnalisées des ressources créées en temps réel pour répondre à des besoins spécifiques, tels que le redimensionnement des images en fonction de la résolution de l’appareil ou le recadrage pour s’adapter à différents formats.
Ces rendus permettent aux entreprises de fournir des expériences personnalisées et optimisées à divers besoins d’audience. Vous pouvez afficher et télécharger des rendus dynamiques dans Experience Manager Assets.

## Rendus Dynamic Media {#dynamic-media-renditions}

### Avant de commencer

* Vous devez être un utilisateur Dynamic Media sous licence AEM.
* Utilisez la [!UICONTROL vue d’administration] pour configurer :
   * [Profils d’image avec recadrage intelligent](/help/assets/dynamic-media/image-profiles.md#creating-image-profiles)
   * [Paramètres d’image prédéfinis](/help/assets/dynamic-media/managing-image-presets.md)

  Vous pouvez [changer de vue](/help/assets/assets-view-introduction.md#how-to-access-assets-view) ultérieurement pour prévisualiser les rendus dynamiques dans la vue Assets.
* Ressources Publish vers Dynamic Media pour rendre les rendus Dynamic Media disponibles dans la vue Assets. Pour plus d’informations, voir [Publish Assets vers AEM et Dynamic Media](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/publish-assets-to-aem-and-dm).


### Affichage et téléchargement de rendus Dynamic Media {#view-download-dm-renditions}

Pour afficher ou télécharger des rendus dynamiques d’images dans Experience Manager Assets, procédez comme suit :

1. Accédez à **[!UICONTROL Gestion Assets]** > **[!UICONTROL Assets]**.

1. Accédez au dossier de ressources approprié.

1. Cliquez sur la ressource à afficher, puis sur **[!UICONTROL Details]**.

1. Dans le menu de droite, cliquez sur l’icône **[!UICONTROL Dynamic Media]** . Le panneau **[!UICONTROL Dynamic Media]** affiche les rendus Dynamic Media et de recadrage intelligent.

   ![Rendus dynamiques](/help/assets/assets/dm-scene7-renditions.png)
   <!-- ![dynamic renditions](assets/preset_smart_crop_view.png) -->

1. Sélectionnez le rendu à prévisualiser et cliquez sur **Copier l’URL** pour copier l’URL du rendu sélectionné. Cliquez sur **Télécharger le rendu** pour télécharger les rendus des ressources d’image.
1. Sélectionnez le rendu de recadrage intelligent à prévisualiser, puis cliquez sur **Copier l’URL** pour copier l’URL du rendu sélectionné.
1. Cliquez sur ![icône de téléchargement](assets/do-not-localize/download-icon.png) pour télécharger tous les rendus de recadrage intelligent disponibles sous la forme d’un fichier zip unique.
   ![Icône de téléchargement](/help/assets/assets/smartcrop-rendition.png)

   >[!NOTE]
   >
   >Ces rendus sont disponibles uniquement pour les ressources d’image.

## Dynamic Media avec rendus OpenAPI Capabilities {#dm-with-openapi-renditions}

### Avant de commencer

* Vous devez être un utilisateur Dynamic Media sous licence AEM.
* Assets doit être approuvé pour afficher Dynamic Media avec les rendus de fonctionnalités OpenAPI. Pour plus d’informations, voir [Approbation de ressources dans Experience Manager](/help/assets/approve-assets.md#copy-delivery-url-approved-assets)
* Les fonctionnalités Dynamic Media avec OpenAPI doivent être activées sur votre instance AEM as a Cloud Service.

### Affichage de Dynamic Media avec des rendus OpenAPI Capabilities {#view-download-dm-with-openapi-renditions}

1. Sélectionnez la ressource et cliquez sur **Details**.
1. Cliquez sur l’icône Dynamic Media disponible dans le volet de droite. Le panneau Dynamic Media affiche le rendu Dynamic Media avec fonctionnalités OpenAPI pour tous les types de ressources.
   ![Icône de téléchargement](/help/assets/assets/dm-with-open-api-copy-url.png)
1. Sélectionnez l’option **Dynamic Media with OpenAPI** , puis cliquez sur **Copier l’URL** pour copier l’URL de diffusion de la ressource.


