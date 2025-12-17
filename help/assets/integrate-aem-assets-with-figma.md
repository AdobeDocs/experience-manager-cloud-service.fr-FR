---
title: Intégration  [!DNL AEM Assets]  à  [!DNL Figma].
description: Découvrez comment intégrer  [!DNL AEM Assets]  avec pour accéder  [!DNL Figma]  ressources de votre entreprise et les utiliser dans votre workflow  [!DNL Figma]  conception.
hide: false
role: User
exl-id: 530561ca-497b-4331-a014-72c561e1ca84
source-git-commit: a9c1f5472092b3b9fa7a5e5570feb92f32e9ef6c
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 1%

---


# Intégration d’[!DNL AEM Assets] à [!DNL Figma]{#integrate-aem-assets-with-figma}

[!DNL AEM Assets] s’intègre de manière native à [!DNL Figma], ce qui permet aux concepteurs d’accéder directement aux ressources stockées dans [!DNL AEM Assets] depuis l’interface utilisateur d’[!DNL Figma]. Vous pouvez placer le contenu géré dans [!DNL AEM Assets] dans la zone de travail [!DNL Figma], puis enregistrer le contenu nouveau ou modifié dans le référentiel [!DNL AEM Assets].

## Avant de commencer{#prerequisites-for-aem-assets-and-figma-integration}

* La version minimale requise d’AEM est `19149`.

* Vous devez disposer de licences [!DNL AEM Assets] et [!DNL Figma] valides pour intégrer [!DNL AEM Assets] à [!DNL Figma].

## Formats de fichiers pris en charge {#supported-file-formats-integration-figma}


* Pour importer des ressources [!DNL AEM] dans Figma, les formats pris en charge sont les ressources d’image (JPEG, PNG), les fichiers vidéo (MP4, MOV, WebM), les fichiers animés (GIF) et les fichiers vectoriels (SVG).
* Pour l’exportation de conceptions de [!DNL Figma] vers [!DNL AEM Assets], les formats pris en charge sont les suivants : **PNG**, **PDF**, **JPG**, **SVG**.

## Accéder Au Connecteur Assets [!UICONTROL Adobe Experience Manager (AEM)]{#access-aem-assets-connector}

Exécutez les étapes suivantes pour accéder au connecteur Assets [!UICONTROL Adobe Experience Manager (AEM)] :

1. Sur votre page d’accueil [!DNL Figma], cliquez sur **[!UICONTROL Actions]** dans la barre d’outils située au bas de la zone de travail et recherchez [!DNL Adobe Experience Manager (AEM) Assets Connector] dans la barre de recherche disponible dans la boîte de dialogue.
1. Sélectionnez [!DNL Adobe Experience Manager (AEM) Assets Connector] pour afficher le panneau [!DNL Adobe Experience Manager (AEM) Assets Connector]. [Importez  [!DNL AEM]  ressources dans la zone  [!DNL Figma]  travail](#import-aem-assets-into-figma-workflow) à l’aide de ce panneau.
   ![actions &#x200B;](/help/assets/assets/actions-on-figma.png)
Vous pouvez également accéder aux [[!DNL Adobe Experience Manager (AEM) Assets Connector]](https://www.figma.com/community/plugin/1512561378275712210/adobe-experience-manager-aem-assets-connector) disponibles sur [!DNL Figma] communauté, cliquer sur **[!UICONTROL Ouvrir dans...]**, sélectionner un fichier récent ou créer un fichier et cliquer sur **[!UICONTROL Exécuter]** pour accéder au panneau [!DNL Adobe Experience Manager (AEM) Assets Connector].
   ![plugin-page-on-figma-community](/help/assets/assets/plugin-page-on-figma-community.png)

>[!NOTE]
>
> [Contactez l’assistance Adobe](https://helpx.adobe.com/fr/contact.html) pour obtenir de l’aide si un message **[!UICONTROL Erreur réseau]** s’affiche après vous être connecté à votre environnement [!DNL AEM].

## Importation de ressources [!DNL AEM] dans [!DNL Figma] zone de travail{#import-aem-assets-into-figma-workflow}

[Accédez au panneau Connecteur Assets [!UICONTROL Adobe Experience Manager (AEM)] &#x200B;](#access-aem-assets-connector) dans l’interface de conception de [!DNL Figma] et procédez comme suit :

1. Recherchez des ressources dans le panneau Connecteur Assets [!UICONTROL Adobe Experience Manager (AEM)]. Pour plus d’informations, voir [&#x200B; Utilisation du sélecteur de ressources &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector#using-asset-selector).

1. Faites glisser et déposez la ressource sur la zone de travail ou sélectionnez la ressource et cliquez sur **[!UICONTROL Sélectionner]** pour apporter la ressource sur la zone de travail.

1. Cliquez sur ![trois points](/help/assets/assets/three-dots.svg) dans le chemin du dossier pour afficher tous les dossiers parents et enfants dans la hiérarchie actuelle. Sélectionnez un dossier pour accéder à cet emplacement.
   ![trois points](/help/assets/assets/figma-v2-plugin.png)

1. [Facultatif] Cliquez sur **[!UICONTROL Rechercher les mises à jour]**. Les ressources utilisées dans le document Figma actuel sont comparées aux ressources qui existent dans AEM. Toutes les mises à jour sont répertoriées dans une fenêtre distincte. Cliquez sur **[!UICONTROL Mettre à jour]** pour obtenir la ressource mise à jour d’AEM dans votre document Figma.

Une fois votre conception Figma prête, vous pouvez [exporter la ressource vers le référentiel AEM Assets](#export-figma-design-to-aem-assets-folder).

## Exporter des ressources vers [!DNL AEM Assets] référentiel{#export-figma-design-to-aem-assets-folder}

[Accédez au panneau Connecteur Assets [!UICONTROL Adobe Experience Manager (AEM)] &#x200B;](#access-aem-assets-connector) dans l’interface de conception [!DNL Figma] et suivez les étapes ci-après pour exporter votre conception vers le référentiel [!DNL AEM Assets] :

1. Accédez au dossier de destination dans lequel vous souhaitez enregistrer votre conception de [!DNL Figma]. Si vous vous trouvez déjà dans un dossier, cliquez sur Autres options (![points de suspension](/help/assets/assets/three-dots.svg)) dans le chemin du dossier pour sélectionner un autre dossier de destination.
1. Facultatif : regroupez les ressources sur la zone de travail pour les sélectionner en tant qu’unité unique à charger dans votre dossier.
1. Cliquez sur ![Chargement de fichier](/help/assets/assets/upload-icon.svg) **[!UICONTROL Charger]** pour afficher la boîte de dialogue **[!UICONTROL Charger une ressource]**.
1. Dans la boîte de dialogue, sélectionnez **[!UICONTROL Élément sélectionné]** ou **[!UICONTROL Page]**, spécifiez un nom de fichier ou de page, définissez une configuration d’exportation et cliquez sur **[!UICONTROL Télécharger]** pour charger la ressource sélectionnée ou la conception entière dans le dossier de destination.

   La configuration de l’exportation comprend le format, l’échelle et la qualité du fichier. Par exemple, si vous sélectionnez JPG comme format de fichier, vous pouvez également définir l’échelle et la qualité de l’image. De même, si vous sélectionnez le format PNG comme format de fichier, vous pouvez également définir l’échelle de l’image.
   ![charger la conception figma](/help/assets/assets/upload-figma-design.png)
