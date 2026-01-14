---
title: Téléchargement de ressources à partir de Content Hub
description: Découvrez comment télécharger une ou plusieurs ressources et leurs rendus à partir du portail Content Hub.
role: User
exl-id: 96d4ffba-4e3e-4496-9da2-6eb36be8331f
source-git-commit: 281a8efcd18920dd926d92db9c757c0513d599fd
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 1%

---

# Téléchargement de ressources à partir de Content Hub {#download-assets}

Le [!DNL Content Hub] vous permet de télécharger et de partager vos ressources. L’interface utilisateur d’[!DNL Content Hub] affiche uniquement les ressources approuvées. Ces ressources peuvent inclure des images, des vidéos ou tout autre contenu numérique. Le [!DNL Content Hub] améliore l’accessibilité et l’adaptabilité pour une distribution efficace des ressources.

Vous pouvez télécharger une ou plusieurs ressources et leurs rendus disponibles à l’aide de [!DNL Content Hub].

Consultez les [types de rendus disponibles dans Content Hub](#types-of-renditions).

## Téléchargement d’une ou de plusieurs ressources et de leurs rendus {#download-asset-renditions}

Pour télécharger une ou plusieurs ressources et leurs rendus, procédez comme suit :

* Pour télécharger une seule ressource et ses rendus :
   1. Sélectionnez ![Télécharger](/help/assets/assets/download-icon.svg) disponible sur la carte de la ressource pour prévisualiser la ressource et ses rendus disponibles.
   1. Sélectionnez les rendus disponibles et cliquez sur l’option **[!UICONTROL Télécharger]** dans la boîte de dialogue pour télécharger les rendus sélectionnés sous la forme d’un fichier ZIP. Si la boîte de dialogue affiche une licence de ressource (pour une ressource sous licence), acceptez les termes et conditions de la licence et cliquez sur **[!UICONTROL Télécharger]**.
      ![télécharger une ressource](/help/assets/assets/download-an-asset-CH-from-asset-card.png)
Vous pouvez également cliquer sur la miniature de la ressource, puis sur ![Télécharger](/help/assets/assets/download-icon.svg) pour sélectionner et afficher les rendus disponibles dans la boîte de dialogue avant de les télécharger.

* Pour télécharger plusieurs ressources et leurs rendus :
   1. Sélectionnez les ressources, cliquez sur ![Télécharger](/help/assets/assets/download-icon.svg) **[!UICONTROL Télécharger]** et consultez la liste des ressources sélectionnées dans la boîte de dialogue **[!UICONTROL Télécharger les ressources]**. Cliquez sur ![désélectionner](/help/assets/assets/Close.svg) en regard d’une ressource pour la désélectionner de la liste.
   1. Sélectionnez un ou plusieurs rendus à télécharger sous forme de fichier ZIP. La sélection des options **[!UICONTROL Recadrage intelligent]** et **[!UICONTROL Rendus statiques]** télécharge tous les rendus de recadrage statique et intelligent disponibles de chaque ressource sélectionnée.
   1. Facultatif : désélectionnez l’option **[!UICONTROL Créer un dossier distinct pour chaque ressource]** pour télécharger les ressources sélectionnées et leurs rendus sous la forme d’une hiérarchie plate dans un dossier du fichier compressé. Par défaut, [!DNL Content Hub] télécharge les ressources sélectionnées et leurs rendus dans des dossiers distincts au sein d’un fichier zip.

      >[!NOTE]
      >
      > * Content Hub enregistre votre sélection (**[!UICONTROL Créer un dossier distinct pour chaque ressource]**) comme préférence et la conserve pour les téléchargements ultérieurs.
      > * L’option **[!UICONTROL Créer un dossier distinct pour chaque ressource]** n’est disponible que pour les utilisateurs [!DNL Content Hub] authentifiés. [!DNL Content Hub] permet aux utilisateurs publics de télécharger des ressources sous la forme de ressources individuelles.

   1. Cliquez sur **[!UICONTROL Télécharger]** pour télécharger les ressources sélectionnées et leurs rendus.
      ![téléchargement de plusieurs ressources](/help/assets/assets/bulk-asset-download-content-hub.png)

Vous pouvez continuer à utiliser [!DNL Content Hub] pendant le téléchargement est en cours. Content Hub n’interrompt pas votre workflow pendant le processus de téléchargement.
![téléchargement de plusieurs ressources](/help/assets/assets/download-assets-notification-ch.png)
Si la boîte de dialogue **[!UICONTROL Télécharger des ressources]** affiche les licences des ressources, sélectionnez chaque licence dans le volet de gauche (section [!UICONTROL Documents T&amp;C]) pour prévisualiser la licence et afficher les ressources sélectionnées associées à la licence dans le volet central de la boîte de dialogue. Après avoir examiné chaque licence, sélectionnez les rendus, cliquez sur **[!UICONTROL J’ai lu et accepté les conditions générales mentionnées ci-dessus]** puis sélectionnez **[!UICONTROL Télécharger]** pour les télécharger.
![téléchargement de plusieurs ressources](/help/assets/assets/download-multiple-licensed-assets-CH.png)

>[!NOTE]
>
>* Les rendus s’affichent uniquement si leur visibilité est activée à l’aide de l’interface utilisateur [[!UICONTROL Configuration]](/help/assets/configure-content-hub-ui-options.md#renditions-content-hub).
>* Les utilisateurs ayant accès à [[!DNL Dynamic Media with Open API capabilities]](/help/assets/dynamic-media-open-apis-overview.md) peuvent afficher et télécharger des rendus de recadrage dynamique et intelligent.
>* L’aperçu de la licence s’affiche uniquement si la ressource est approuvée à l’aide de [!DNL Assets as a Cloud Service] environnement de création. Pour plus d’informations, consultez la section [Gestion des ressources sous licence sur Content Hub](/help/assets/manage-licensed-assets-on-content-hub.md).

<!--

## Download an asset and its renditions {#download-asset-renditions} 

To download an asset and its renditions, execute the following steps: 

1. Click the asset to view its properties.

1. Click ![download](/help/assets/assets/download-icon.svg) to see the list of available asset renditions in the **[!UICONTROL Download]** panel.

   >[!NOTE]
   >
   >* The renditions display only if their visibility is enabled using the [Configuration](/help/assets/configure-content-hub-ui-options.md#renditions-content-hub) User Interface.
   >* You can download all [static, dynamic, and smart crop renditions](#types-of-renditions) while downloading an asset.

1. Select one or more renditions and click **[!UICONTROL Download]** to download the selected renditions as a zip file. 
While downloading a licensed asset, select **[!UICONTROL I have read and accepted the terms & conditions mentioned above]** before clicking **[!UICONTROL Download]**. You can also click **[!UICONTROL terms & conditions]** to view the asset license. The preview of the license displays only if the asset is approved using Assets as a Cloud Service authoring environment. For more information, see [Manage licensed assets on Content Hub](/help/assets/manage-licensed-assets-on-content-hub.md).

   ![Download single asset renditions](/help/assets/assets/download-single-asset-renditions.png)


If you are downloading a licensed asset, select **[!UICONTROL I have read and accepted the terms & conditions mentioned above]** and then click **[!UICONTROL Download]**. You can also click **[!UICONTROL terms & conditions]** to view the asset license. The preview of the license displays only if the asset is approved using Assets as a Cloud Service authoring environment. For more information, see [Manage licensed assets on Content Hub](/help/assets/manage-licensed-assets-on-content-hub.md).

>[!NOTE]
>
> The users with access to [Dynamic Media with Open API capabilities](/help/assets/dynamic-media-open-apis-overview.md) can view and download dynamic and smart crop renditions.

## Download multiple assets and their renditions {#download-multiple-assets-renditions} 

To download multiple assets and their renditions, execute the following steps: 

1. Select the assets and click ![download](/help/assets/assets/download-icon.svg) **[!UICONTROL Download]**. The [!UICONTROL Download assets] screen displays listing all the selected assets. 
1. Click **[!UICONTROL Download]** to select from the various download options to begin download:

    * **Download [!UICONTROL Originals]**: Select this option to download the selected assets in the original form.
    * **Download [!UICONTROL Static Renditions only]**: Select this option to download all available static renditions of assets except the original assets.
    * **Download [!UICONTROL Originals & Static Renditions]**: Select this option to download both original and static renditions of the selected assets. 

      ![Download multiple renditions](/help/assets/assets/download-multiple-renditions.png)

      >[!NOTE]
      >
      >* The renditions display only if their visibility is enabled using the [Configuration](/help/assets/configure-content-hub-ui-options.md#renditions-content-hub) User Interface.
      >* You can only download [static renditions](#types-of-renditions) while downloading multiple assets.

    If any of the selected asset is a licensed asset, click the license of the asset in left pane to see its preview, which enables you to select **[!UICONTROL I have read and accepted the terms & conditions mentioned above]** and then click **[!UICONTROL Download]**. The preview of the license displays only if the asset is approved using Assets as a Cloud Service authoring environment. For more information, see [Manage licensed assets on Content Hub](/help/assets/manage-licensed-assets-on-content-hub.md).

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

Les rendus de ressources sont différentes représentations du fichier d’origine d’une ressource. Ces rendus peuvent inclure des miniatures, des versions optimisées pour le web ou les appareils mobiles, des fichiers avec filigrane ou protégés par DRM, ou même des éléments dynamiques tels que des recadrages intelligents. Ils n’ont pas besoin de correspondre au type de fichier d’origine, mais servent à représenter la ressource dans divers cas d’utilisation.

En savoir plus sur [affichage et gestion des rendus dans [!DNL Experience Manager Assets]](/help/assets/renditions.md).

[!DNL Experience Manager Assets] prend en charge les types de rendus suivants :

* [Rendus statiques](/help/assets/renditions.md#static-renditions) : les rendus statiques sont des versions précréées des ressources numériques, généralement générées lors de l’ingestion ou de la modification des ressources. Ils sont optimisés pour des utilisations et des plateformes spécifiques, telles que les miniatures web, les formats compatibles avec les appareils mobiles pour les conceptions réactives ou les fichiers haute résolution pour l’impression, offrant ainsi une expérience rationalisée et cohérente.

* [Rendus dynamiques](/help/assets/renditions.md#dynamic-renditions) : les rendus dynamiques sont des versions personnalisées en temps réel des ressources permettant d’effectuer diverses actions, telles que le redimensionnement des images pour différentes résolutions d’appareil ou le recadrage pour s’adapter à divers proportions. Ces rendus vous permettent d’offrir des expériences personnalisées et optimisées pour des besoins plus larges. Les rendus dynamiques des ressources sont créés dans [!DNL Adobe Experience Manager Assets] environnement de création. Pour plus d’informations sur les étapes requises pour activer les rendus dynamiques, voir [&#x200B; Activation des rendus dynamiques &#x200B;](#enable-dynamic-media-renditions).

* [Recadrage intelligent](/help/assets/dynamic-media/image-profiles.md#creating-image-profiles) : le recadrage intelligent se concentre uniquement sur la partie essentielle d’une ressource pendant le processus de recadrage. Le recadrage intelligent Dynamic Media utilise l’intelligence artificielle optimisée par l’IA d’Adobe pour effectuer le suivi du point ciblé, en s’assurant que nos ressources ont l’aspect le plus attrayant sur toutes les tailles d’écran. [!DNL Adobe Experience Manager] recadrage intelligent affiche la largeur et la hauteur des rendus d’une ressource avec le titre. Pour en savoir plus, consultez la section [Utilisation du recadrage intelligent avec AEM Assets Dynamic Media](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use).

  Les rendus de recadrage intelligent s’affichent et ne peuvent être téléchargés que si vous avez accès à [Dynamic Media avec les fonctionnalités OpenAPI](/help/assets/dynamic-media-open-apis-overview.md). Les rendus de recadrage intelligent ne sont disponibles que pour les ressources d’image.

  ![Types de rendus](/help/assets/assets/renditions-types.png)

  >[!NOTE]
  > 
  > Le panneau Télécharger affiche uniquement les rendus statiques personnalisés. Les miniatures de `cq5dam.*` par défaut ne s’affichent pas dans Content Hub.

### Activation des rendus dynamiques {#enable-dynamic-media-renditions}

Pour activer les rendus dynamiques :

1. Vérifiez que vous avez accès à [Dynamic Media avec les fonctionnalités OpenAPI](/help/assets/dynamic-media-open-apis-overview.md).

   Une fois que vous avez accès à Dynamic Media avec les fonctionnalités OpenAPI, toutes les ressources marquées comme `Approved` peuvent être diffusées au public à l’aide de Dynamic Media.

1. Définissez la [&#x200B; cible d’approbation de la ressource &#x200B;](/help/assets/approve-assets-content-hub.md#set-approval-target) sur Content Hub afin d’approuver les ressources uniquement pour Content Hub.

1. Activez le bouton (bascule) **[!UICONTROL Activer la disponibilité des rendus]** disponible dans l’onglet **[!UICONTROL Rendus]** de l’interface utilisateur [Configuration](/help/assets/configure-content-hub-ui-options.md#access-configuration-options-content-hub).

1. Enregistrez à nouveau les paramètres d’image prédéfinis existants pour les rendre disponibles sur Content Hub. Il s’applique uniquement si vous avez récemment intégré Dynamic Media avec OpenAPI.

   Pour enregistrer à nouveau les paramètres d’image prédéfinis existants, accédez à la vue Administration et sélectionnez **[!UICONTROL Outils]** > **[!UICONTROL Assets]** > **[!UICONTROL Paramètres d’image prédéfinis]**. Sélectionnez un paramètre prédéfini, cliquez sur **[!UICONTROL Modifier]** puis sur **[!UICONTROL Enregistrer]**.



   >[!NOTE]
   > 
   > Les rendus dynamiques sont disponibles uniquement pour les ressources d’image.



