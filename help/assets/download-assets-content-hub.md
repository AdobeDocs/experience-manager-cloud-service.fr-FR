---
title: Téléchargement de ressources à partir de Content Hub
description: Découvrez comment télécharger des ressources à partir du portail Content Hub
role: User
exl-id: 96d4ffba-4e3e-4496-9da2-6eb36be8331f
source-git-commit: 28424cb184d0378669498c78e571961227f6539a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Téléchargement de ressources à partir de Content Hub {#download-assets}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [Bonnes pratiques relatives aux métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Fonctionnalités Dynamic Media avec OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation de développement pour AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

<!-- ![Download assets](assets/download-asset.jpg) -->
![Télécharger des ressources](assets/download-asset-genstudio.jpeg)

>[!AVAILABILITY]
>
>Le guide de Content Hub est désormais disponible au format PDF. Téléchargez l’intégralité du guide et utilisez l’assistant IA Adobe Acrobat pour répondre à vos requêtes.
>
>[!BADGE Guide PDF de Content Hub]{type=Informative url="https://helpx.adobe.com/content/dam/help/fr/experience-manager/aem-assets/content-hub.pdf"}

Content Hub vous permet de télécharger et de partager vos ressources. L’interface utilisateur de Content Hub affiche uniquement les ressources approuvées. Ces ressources peuvent inclure des images, des vidéos ou tout autre contenu numérique. Content Hub améliore l’accessibilité et l’adaptabilité pour une distribution efficace des ressources.

Vous pouvez télécharger une ou plusieurs ressources et leurs rendus disponibles à l’aide de Content Hub.

## Téléchargement d’une ressource et de ses rendus {#download-asset-renditions}

Pour télécharger une ressource et ses rendus, procédez comme suit :

1. Cliquez sur la ressource pour afficher ses propriétés.

1. Cliquez sur ![télécharger](/help/assets/assets/download-icon.svg) pour lancer le processus de téléchargement. Le panneau Télécharger répertorie tous les rendus de ressources disponibles (Original + autres rendus).

   >[!NOTE]
   >
   Les rendus s’affichent uniquement si leur visibilité est activée à l’aide de l’interface utilisateur [Configuration](/help/assets/configure-content-hub-ui-options.md#renditions-content-hub).

1. Sélectionnez le ou les rendus et cliquez sur **[!UICONTROL Télécharger]**.

   ![Télécharger des rendus de ressource uniques](/help/assets/assets/download-single-asset-renditions.png)


Si vous téléchargez une ressource sous licence, sélectionnez **[!UICONTROL J’ai lu et accepté les conditions générales mentionnées ci-dessus]**, puis cliquez sur **[!UICONTROL Télécharger]**. Vous pouvez également cliquer sur **[!UICONTROL termes et conditions]** pour afficher la licence de ressource. L’aperçu de la licence s’affiche uniquement si la ressource est approuvée à l’aide de l’environnement de création as a Cloud Service d’Assets. Pour plus d’informations, consultez la section [Gestion des ressources sous licence sur Content Hub](/help/assets/manage-licensed-assets-on-content-hub.md).

## Téléchargement de plusieurs ressources et de leurs rendus {#download-multiple-assets-renditions}

Pour télécharger plusieurs ressources et leurs rendus, procédez comme suit :

1. Sélectionnez les ressources et cliquez sur ![télécharger](/help/assets/assets/download-icon.svg) **[!UICONTROL Télécharger]**. L’écran [!UICONTROL Télécharger des ressources] répertorie toutes les ressources sélectionnées.
1. Cliquez sur **[!UICONTROL Télécharger]** pour sélectionner l’une des différentes options de téléchargement pour commencer le téléchargement :

   * **Télécharger les [!UICONTROL originaux]** : sélectionnez cette option pour télécharger les ressources sélectionnées dans le formulaire d’origine.
   * **Télécharger [!UICONTROL uniquement les rendus]** : sélectionnez cette option pour télécharger tous les rendus disponibles des ressources, à l’exception des ressources d’origine.
   * **Télécharger [!UICONTROL Originals &amp; All renditions]** : sélectionnez cette option pour télécharger les rendus et les originaux des ressources sélectionnées.

     ![Télécharger plusieurs rendus](/help/assets/assets/download-multiple-renditions.png)

     >[!NOTE]
     >
     Les rendus s’affichent uniquement si leur visibilité est activée à l’aide de l’interface utilisateur [Configuration](/help/assets/configure-content-hub-ui-options.md#renditions-content-hub).

   Si l’une des ressources sélectionnées est une ressource sous licence, cliquez sur la licence de la ressource dans le volet de gauche pour en afficher l’aperçu, ce qui vous permet de sélectionner **[!UICONTROL J’ai lu et accepté les conditions générales mentionnées ci-dessus]**, puis cliquez sur **[!UICONTROL Télécharger]**. L’aperçu de la licence s’affiche uniquement si la ressource est approuvée à l’aide de l’environnement de création as a Cloud Service d’Assets. Pour plus d’informations, consultez la section [Gestion des ressources sous licence sur Content Hub](/help/assets/manage-licensed-assets-on-content-hub.md).

   ![download-multiple-license](/help/assets/assets/download-multiple-license.png)

<!--1. On the Content Hub homepage, select the asset and click **Download**. The **Download assets** dialog box displays a license or list of licenses associated with the selected assets in the left pane. 
1. Click a license in the left pane to see its PDF in the middle pane and the associated assets with it in the right pane. The license PDF preview is displayed only if the license is approved in your Assets as a Cloud Service environment. [Approve the license PDFs](/help/assets/approve-assets-content-hub.md) of the selected assets to see their previews.
1. Optional: Click ![remove-icon](/help/assets/assets/remove-icon.svg) to remove a license from the dialog box.
1. Select **I have read and accept all the terms and conditions mentioned above.** 
1. Click **Download** to download the selected assets.-->

<!---This dialog box displays the list of licenses associated with the selected assets in the left pane. Select a license to preview its terms and conditions (in pdf format) in the middle pane and the preview of the associated assets to the license in the right. Reviewed licenses are highlighted in light blue.


The dialog box that displays depends on whether the download list includes expired assets or only non-expired assets. <br/>
**Download expired assets dialog box:** This dialog box displays the expired assets' preview along with their expiry date in the left pane. The expired assets' count out of total selected displays in the right pane. Click **Proceed with all assets** to download expired assets with other assets (if present). The Download assets dialog box displays. See the [Download assets dialog box](#Download-asset-dialog-box) to proceed further.
    
    >[!NOTE]
    >
    >[Enable the download option for expired assets](/help/assets/configure-content-hub-ui-options.md#expired-assets-content-hub) to download them. Only expired assets that have enabled downloading are available for download.

   <a id="Download-asset-dialog-box"></a> **Download assets dialog box:** This dialog box displays the list of licenses associated with the selected assets in the left pane. Select a license to preview its terms and conditions (in pdf format) in the middle pane and the associated assets' preview and their count in the right pane. Reviewed licenses are highlighted in light blue.

    >[!NOTE]
    >
    > The **Download Asset dialog box** previews licensing terms and conditions only for approved licenses. [Approve the assets' licenses](/help/assets/approve-assets-content-hub.md) before downloading them to preview their licensing terms in the **Download Asset dialog box**.

1. Click  ![remove-icon](/help/assets/assets/remove-icon.svg) to remove a license from the download dialog box. 

1. Accept the terms and conditions and then click **Download** to download assets associated with the available licenses in the left pane.-->
<!--![download-multiple-license](/help/assets/assets/download-multiple-license.png)-->

<!---
### Download non-licensed Assets {#download-non-licensed-assets}

 To download non-licensed assets, select the assets and click ![download](/help/assets/assets/download-icon.svg) from the top rail.-->







