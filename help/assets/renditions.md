---
title: Affichage et gestion des rendus dans Experience Manager Assets
description: Découvrez comment AEM Assets et Dynamic Media simplifient la gestion efficace des images avec des rendus d’image statiques et dynamiques.
exl-id: 006dc493-c400-4d0f-b314-c1978582b7fb
feature: Renditions
role: User
source-git-commit: b6c753ec581a80991f0f79134bec019c3ad6d1d0
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 8%

---

# Affichage et gestion des rendus dans Experience Manager Assets{#renditions}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime et Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Intégration d’AEM Assets à Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Extensibilité de l’IU</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Activer Dynamic Media Prime et Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Bonnes pratiques de recherche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Bonnes pratiques relatives aux métadonnées</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Hub de contenus</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Fonctionnalités Dynamic Media avec OpenAPI</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Documentation de développement pour AEM Assets</b></a>
        </td>
    </tr>
</table>

Les rendus dans Adobe Experience Manager (AEM) sont des versions personnalisées des ressources numériques, telles que les images, conçues pour différents appareils et plateformes afin d’assurer des performances optimales. AEM facilite la création et la gestion de ces rendus, améliorant ainsi l’expérience client. Vous pouvez créer des miniatures, optimiser les images pour le web ou les appareils mobiles, ajouter des filigranes, afficher et télécharger des rendus dynamiques ou des rendus de recadrage intelligent, et bien plus encore.

Les paramètres d’image prédéfinis Dynamic Media et les rendus de recadrage intelligent favorisent une gestion d’image systématique alignée sur les normes de la marque, maximisant ainsi la cohésion de celle-ci. Cela simplifie le processus de localisation et d’utilisation rapides des rendus d’image dynamiques selon les besoins, sans accès administrateur.

Les rendus sont classés comme statiques et dynamiques, chaque type présentant des fonctionnalités uniques qui sont abordées plus en détail.

## Rendus statiques {#static-renditions}

Les rendus statiques sont des versions prégénérées de ressources numériques, généralement créées lors de l’ingestion ou de la modification de ressources. Ces rendus sont optimisés pour des objectifs et des plateformes spécifiques, tels que des miniatures web, des formats compatibles avec les appareils mobiles pour le responsive design ou des versions haute résolution pour l’impression, afin d’assurer une expérience efficace et cohérente.
Découvrez comment [ afficher et télécharger des rendus statiques ](#view-and-download-static-renditions) dans Experience Manager Assets.

### Affichage et téléchargement des rendus statiques{#view-and-download-static-renditions}

Pour afficher les rendus de ressources et les télécharger, procédez comme suit :

1. Dans la vue Assets, cliquez sur **Assets**, accédez à un dossier, sélectionnez une ressource, puis cliquez sur **Détails**.
1. Cliquez sur l’icône du rendu disponible dans le volet de droite.
1. Sélectionnez un rendu pour le prévisualiser, puis cliquez sur ![icône de téléchargement](/help/assets/assets/download-icon.svg) pour le télécharger.

   ![Affichage et téléchargement des rendus dynamiques](/help/assets/assets/view-download-static-rendition.png)

## Rendus dynamiques {#dynamic-renditions}

Les rendus dynamiques sont des versions personnalisées des ressources créées en temps réel pour répondre à des besoins spécifiques, tels que le redimensionnement des images en fonction de la résolution de l’appareil ou le recadrage pour les adapter à différents proportions.
Ces rendus permettent aux entreprises de fournir des expériences personnalisées et optimisées à divers besoins d’audience. Vous pouvez afficher et télécharger des rendus dynamiques dans Experience Manager Assets.

## Rendus Dynamic Media {#dynamic-media-renditions}

### Avant de commencer

* Vous devez être un utilisateur d’AEM Dynamic Media sous licence.
* Utilisez la vue [!UICONTROL Admin] pour configurer :
   * [Profils d’image de recadrage intelligent](/help/assets/dynamic-media/image-profiles.md#creating-image-profiles)
   * [Paramètres d’image prédéfinis](/help/assets/dynamic-media/managing-image-presets.md)

  Vous pouvez [changer de vue](/help/assets/assets-view-introduction.md#how-to-access-assets-view) ultérieurement pour prévisualiser les rendus dynamiques dans la vue Assets.
* Publiez des ressources dans Dynamic Media pour rendre les rendus Dynamic Media disponibles dans la vue Assets. Pour plus d’informations, voir [Publication d’Assets dans AEM et Dynamic Media](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/publish-assets-to-aem-and-dm).


### Affichage et téléchargement des rendus Dynamic Media {#view-download-dm-renditions}

Pour afficher ou télécharger des rendus dynamiques d’images dans Experience Manager Assets, procédez comme suit :

1. Accédez à **[!UICONTROL Gestion Assets]** > **[!UICONTROL Assets]**.

1. Accédez au dossier de ressources approprié.

1. Cliquez sur la ressource à afficher, puis sur **[!UICONTROL Détails]**.

1. Dans le menu de droite, cliquez sur l’icône **[!UICONTROL Dynamic Media]**. Le panneau **[!UICONTROL Dynamic Media]** affiche les rendus Dynamic Media et de recadrage intelligent.

   ![Rendus dynamiques](/help/assets/assets/dm-scene7-renditions.png)
   <!-- ![dynamic renditions](assets/preset_smart_crop_view.png) -->

1. Sélectionnez le rendu à prévisualiser et cliquez sur **Copier l’URL** pour copier l’URL du rendu sélectionné. Cliquez sur **Télécharger le rendu** pour télécharger les rendus des ressources d’image.
1. Sélectionnez le rendu de recadrage intelligent à prévisualiser, puis cliquez sur **Copier l’URL** pour copier l’URL du rendu sélectionné.
1. Cliquez sur ![icône de téléchargement](assets/do-not-localize/download-icon.png) pour télécharger tous les rendus de recadrage intelligent disponibles sous la forme d’un seul fichier zip.
   ![icône de téléchargement](/help/assets/assets/smartcrop-rendition.png)

   >[!NOTE]
   >
   >Ces rendus ne sont disponibles que pour les ressources d’image.

## Rendus Dynamic Media avec les fonctionnalités OpenAPI {#dm-with-openapi-renditions}

### Avant de commencer {#prereqs-dm-with-openapi-renditions}

* Vous devez être un utilisateur d’AEM Dynamic Media sous licence.
* Assets doit être approuvé pour afficher Dynamic Media avec les rendus de fonctionnalités OpenAPI. Pour plus d’informations, voir [Approuver des ressources dans Experience Manager](/help/assets/approve-assets.md#copy-delivery-url-approved-assets)
* Dynamic Media avec les fonctionnalités OpenAPI doit être activé sur votre instance AEM as a Cloud Service.

### Affichage des rendus Dynamic Media avec les fonctionnalités OpenAPI {#view-download-dm-with-openapi-renditions}

1. Sélectionnez la ressource et cliquez sur **Détails**.
1. Cliquez sur l’icône Dynamic Media disponible dans le volet de droite. Le panneau Dynamic Media affiche le rendu Dynamic Media avec les fonctionnalités OpenAPI pour tous les types de ressources.
   ![icône de téléchargement](/help/assets/assets/dm-with-open-api-copy-url.png)
1. Sélectionnez l’option **Dynamic Media avec OpenAPI**, puis cliquez sur **Copier l’URL** pour copier l’URL de diffusion de la ressource.


