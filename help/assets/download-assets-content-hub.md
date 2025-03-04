---
title: Téléchargement de ressources à partir de Content Hub
description: Découvrez comment télécharger des ressources à partir du portail Content Hub
role: User
exl-id: 96d4ffba-4e3e-4496-9da2-6eb36be8331f
source-git-commit: 07d533962ae2922c8a467924361fdfefc5c594eb
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 9%

---

# Téléchargement de ressources à partir du Content Hub {#download-assets}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [Bonnes pratiques relatives aux métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Fonctionnalités Dynamic Media avec OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation de développement pour AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

<!-- ![Download assets](assets/download-asset.jpg) -->
![Télécharger des ressources](assets/download-asset-genstudio.jpeg)

>[!AVAILABILITY]
>
>Le guide de Content Hub est désormais disponible au format PDF. Téléchargez l’intégralité du guide et utilisez l’assistant IA Adobe Acrobat pour répondre à vos requêtes.
>
>[!BADGE Guide PDF de Content Hub]{type=Informative url="https://helpx.adobe.com/content/dam/help/fr/experience-manager/aem-assets/content-hub.pdf"}

Le Content Hub vous permet de télécharger et de partager vos ressources. L’interface utilisateur de Content Hub affiche uniquement les ressources approuvées. Ces ressources peuvent inclure des images, des vidéos ou tout autre contenu numérique. Content Hub améliore l’accessibilité et l’adaptabilité pour une distribution efficace des ressources.

Vous pouvez télécharger une ou plusieurs ressources et leurs rendus disponibles à l’aide de Content Hub.

Voir [types de rendus disponibles dans Content Hub](#types-of-renditions).

## Téléchargement d’une ressource et de ses rendus {#download-asset-renditions}

Pour télécharger une ressource et ses rendus, procédez comme suit :

1. Cliquez sur la ressource pour afficher ses propriétés.

1. Cliquez sur ![télécharger](/help/assets/assets/download-icon.svg) pour lancer le processus de téléchargement. Le panneau Télécharger répertorie tous les rendus de ressources disponibles.

   >[!NOTE]
   >
   * Les rendus s’affichent uniquement si leur visibilité est activée à l’aide de l’interface utilisateur [Configuration](/help/assets/configure-content-hub-ui-options.md#renditions-content-hub).
   * Vous pouvez télécharger tous les rendus [statiques, dynamiques et de recadrage intelligent](#types-of-renditions) lors du téléchargement d’une ressource.

1. Sélectionnez un ou plusieurs rendus, puis cliquez sur **[!UICONTROL Télécharger]**.

   ![Télécharger des rendus de ressources uniques](/help/assets/assets/download-single-asset-renditions.png)


Si vous téléchargez une ressource sous licence, sélectionnez **[!UICONTROL J’ai lu et accepté les conditions générales mentionnées ci-dessus]** puis cliquez sur **[!UICONTROL Télécharger]**. Vous pouvez également cliquer sur **[!UICONTROL termes et conditions]** pour afficher la licence de la ressource. L’aperçu de la licence s’affiche uniquement si la ressource est approuvée à l’aide de l’environnement de création Assets as a Cloud Service. Pour plus d’informations, consultez la section [Gestion des ressources sous licence sur Content Hub](/help/assets/manage-licensed-assets-on-content-hub.md).

>[!NOTE]
>
Les utilisateurs ayant accès à [Dynamic Media avec fonctionnalités d’API ouvertes](/help/assets/dynamic-media-open-apis-overview.md) peuvent afficher et télécharger des rendus de recadrage dynamique et intelligent.

## Téléchargement de plusieurs ressources et de leurs rendus {#download-multiple-assets-renditions}

Pour télécharger plusieurs ressources et leurs rendus, procédez comme suit :

1. Sélectionnez les ressources et cliquez sur ![Télécharger](/help/assets/assets/download-icon.svg) **[!UICONTROL Télécharger]**. L’écran [!UICONTROL  Télécharger les ressources ] répertorie toutes les ressources sélectionnées.
1. Cliquez sur **[!UICONTROL Télécharger]** pour effectuer une sélection parmi les différentes options de téléchargement pour commencer le téléchargement :

   * **Télécharger [!UICONTROL les originaux]** : sélectionnez cette option pour télécharger les ressources sélectionnées dans le formulaire d’origine.
   * **Télécharger [!UICONTROL les rendus statiques uniquement]** : sélectionnez cette option pour télécharger tous les rendus statiques disponibles des ressources, à l’exception des ressources d’origine.
   * **Télécharger [!UICONTROL les rendus originaux et statiques]** : sélectionnez cette option pour télécharger les rendus originaux et statiques des ressources sélectionnées.

     ![Télécharger plusieurs rendus](/help/assets/assets/download-multiple-renditions.png)

     >[!NOTE]
     >
     * Les rendus s’affichent uniquement si leur visibilité est activée à l’aide de l’interface utilisateur [Configuration](/help/assets/configure-content-hub-ui-options.md#renditions-content-hub).
     * Vous pouvez uniquement télécharger des [rendus statiques](#types-of-renditions) lors du téléchargement de plusieurs ressources.

   Si l’une des ressources sélectionnées est une ressource sous licence, cliquez sur la licence de la ressource dans le volet de gauche pour afficher son aperçu, ce qui vous permet de sélectionner **[!UICONTROL J’ai lu et accepté les conditions générales mentionnées ci-dessus]** puis cliquez sur **[!UICONTROL Télécharger]**. L’aperçu de la licence s’affiche uniquement si la ressource est approuvée à l’aide de l’environnement de création Assets as a Cloud Service. Pour plus d’informations, consultez la section [Gestion des ressources sous licence sur Content Hub](/help/assets/manage-licensed-assets-on-content-hub.md).

   <!--![download-multiple-license](/help/assets/assets/download-multiple-license.png)-->

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


## Types de rendus {#types-of-renditions}

Les rendus de ressources sont différentes représentations du fichier d’origine d’une ressource. Il peut s’agir de miniatures, de versions optimisées pour le web ou les appareils mobiles, de fichiers avec filigrane ou protégés par DRM, ou même d’éléments dynamiques tels que des recadrages intelligents. Ils n’ont pas besoin de correspondre au type de fichier d’origine, mais servent à représenter la ressource dans divers cas d’utilisation.

En savoir plus sur [affichage et gestion des rendus dans Experience Manager Assets](/help/assets/renditions.md).

[!DNL Experience Manager Assets] prend en charge les types de rendus suivants :

* [Rendus statiques](/help/assets/renditions.md#static-renditions) : les rendus statiques sont des versions précréées des ressources numériques, généralement générées lors de l’ingestion ou de la modification des ressources. Ils sont optimisés pour des utilisations et des plateformes spécifiques, telles que les miniatures web, les formats compatibles avec les appareils mobiles pour les conceptions réactives ou les fichiers haute résolution pour l’impression, offrant ainsi une expérience rationalisée et cohérente.

* [Rendus dynamiques](/help/assets/renditions.md#dynamic-renditions) : les rendus dynamiques sont des versions personnalisées en temps réel des ressources permettant d’effectuer diverses actions, telles que le redimensionnement des images pour différentes résolutions d’appareil ou le recadrage pour s’adapter à divers proportions. Ces rendus vous permettent d’offrir des expériences personnalisées et optimisées pour des besoins plus larges. Les rendus dynamiques des ressources sont créés dans [!DNL Adobe Experience Manager Assets] environnement de création.

* [Recadrage intelligent](/help/assets/dynamic-media/image-profiles.md#creating-image-profiles) : le recadrage intelligent se concentre uniquement sur la partie essentielle d’une ressource pendant le processus de recadrage. Le recadrage intelligent Dynamic Media pour tire parti de l’intelligence artificielle optimisée par Adobe Sensei pour effectuer le suivi du point ciblé, en s’assurant que vos ressources ont l’aspect le plus favorable quelle que soit la taille de l’écran. [!DNL Adobe Experience Manager] recadrage intelligent affiche la largeur et la hauteur des rendus d’une ressource avec le titre. Pour en savoir plus, consultez la section [Utilisation du recadrage intelligent avec AEM Assets Dynamic Media](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use).

  ![Types de rendus](/help/assets/assets/renditions-types.png)


>[!NOTE]
> 
* Pour obtenir un accès anticipé au compte Dynamic Media, [créez et envoyez un dossier de support client Adobe](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html).
* Les clients nouvellement intégrés aux [services d’API ouverts Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) doivent réviser leurs paramètres d’image prédéfinis existants pour approbation.



