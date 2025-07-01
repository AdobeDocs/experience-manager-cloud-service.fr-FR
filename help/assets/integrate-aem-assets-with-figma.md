---
title: Intégration  [!DNL AEM Assets]  à  [!DNL Figma].
description: Découvrez comment intégrer  [!DNL AEM Assets]  avec pour accéder  [!DNL Figma]  ressources de votre entreprise et les utiliser dans votre workflow  [!DNL Figma]  conception.
hide: false
role: User
exl-id: 530561ca-497b-4331-a014-72c561e1ca84
source-git-commit: 3603a98dfee62db49f3201c8d75aa8eee4909cc1
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 1%

---


# Intégration d’[!DNL AEM Assets] à [!DNL Figma]{#integrate-aem-assets-with-figma}

[!DNL AEM Assets] s’intègre de manière native à [!DNL Figma], ce qui permet aux concepteurs d’accéder directement aux ressources stockées dans [!DNL AEM Assets] depuis l’interface utilisateur d’[!DNL Figma]. Vous pouvez placer le contenu géré dans [!DNL AEM Assets] dans la zone de travail [!DNL Figma], puis enregistrer le contenu nouveau ou modifié dans le référentiel [!DNL AEM Assets].

## Avant de commencer{#prerequisites-for-aem-assets-and-figma-integration}

* La version minimale requise d’AEM est `19149`.

* Vous devez disposer de licences [!DNL AEM Assets] et [!DNL Figma] valides pour intégrer [!DNL AEM Assets] à [!DNL Figma].

## Accéder Au Connecteur Assets [!UICONTROL Adobe Experience Manager (AEM)]{#access-aem-assets-connector}

Exécutez les étapes suivantes pour accéder au connecteur Assets [!UICONTROL Adobe Experience Manager (AEM)] :

1. Sur votre page d’accueil [!DNL Figma], cliquez sur **[!UICONTROL Actions]** dans la barre d’outils située au bas de la zone de travail et recherchez [!DNL Adobe Experience Manager (AEM) Assets Connector] dans la barre de recherche disponible dans la boîte de dialogue.
1. Sélectionnez [!DNL Adobe Experience Manager (AEM) Assets Connector] pour afficher le panneau [!DNL Adobe Experience Manager (AEM) Assets Connector]. [Importez  [!DNL AEM]  ressources dans la zone  [!DNL Figma]  travail](#import-aem-assets-into-figma-workflow) à l’aide de ce panneau.
   ![actions ](/help/assets/assets/actions-on-figma.png)
Vous pouvez également accéder aux [[!DNL Adobe Experience Manager (AEM) Assets Connector]](https://www.figma.com/community/plugin/1512561378275712210/adobe-experience-manager-aem-assets-connector) disponibles sur [!DNL Figma] communauté, cliquer sur **[!UICONTROL Ouvrir dans...]**, sélectionner un fichier récent ou créer un fichier et cliquer sur **[!UICONTROL Exécuter]** pour accéder au panneau [!DNL Adobe Experience Manager (AEM) Assets Connector].
   ![plugin-page-on-figma-community](/help/assets/assets/plugin-page-on-figma-community.png)

>[!NOTE]
>
> [Contactez l’assistance Adobe](https://helpx.adobe.com/fr/contact.html) pour obtenir de l’aide si un message **[!UICONTROL Erreur réseau]** s’affiche après vous être connecté à votre environnement [!DNL AEM].

## Importation de ressources [!DNL AEM] dans [!DNL Figma] zone de travail{#import-aem-assets-into-figma-workflow}

[Accédez au panneau Connecteur Assets [!UICONTROL Adobe Experience Manager (AEM)] ](#access-aem-assets-connector) dans l’interface de conception de [!DNL Figma] et procédez comme suit :

1. Recherchez des ressources dans le panneau Connecteur Assets [!UICONTROL Adobe Experience Manager (AEM)]. Pour plus d’informations, voir [ Utilisation du sélecteur de ressources ](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector#using-asset-selector).

1. Faites glisser et déposez la ressource sur la zone de travail ou sélectionnez la ressource et cliquez sur **[!UICONTROL Sélectionner]** pour apporter la ressource sur la zone de travail.

1. Cliquez sur ![trois points](/help/assets/assets/three-dots.svg) dans le chemin du dossier pour afficher tous les dossiers parents et enfants dans la hiérarchie actuelle. Sélectionnez un dossier pour accéder à cet emplacement.
   ![trois points](/help/assets/assets/assets-folder-structure.png)

Une fois votre conception Figma prête, vous pouvez [exporter la ressource vers le référentiel AEM Assets](#export-figma-design-to-aem-assets-folder).

## Exporter des ressources vers [!DNL AEM Assets] référentiel{#export-figma-design-to-aem-assets-folder}

[Accédez au panneau Connecteur Assets [!UICONTROL Adobe Experience Manager (AEM)] ](#access-aem-assets-connector) dans l’interface de conception [!DNL Figma] et suivez les étapes ci-après pour exporter votre conception vers le référentiel [!DNL AEM Assets] :

1. Accédez au dossier de destination dans lequel vous souhaitez enregistrer votre conception de [!DNL Figma]. Si vous vous trouvez déjà dans un dossier, cliquez sur Autres options (![points de suspension](/help/assets/assets/three-dots.svg)) dans le chemin du dossier pour sélectionner un autre dossier de destination.
1. Facultatif : regroupez les ressources sur la zone de travail pour les sélectionner en tant qu’unité unique à charger dans votre dossier.
1. Cliquez sur ![Chargement de fichier](/help/assets/assets/upload-icon.svg) **[!UICONTROL Charger]** pour afficher la boîte de dialogue **[!UICONTROL Charger une ressource]**.
1. Dans la boîte de dialogue, spécifiez un nom de fichier, choisissez un format de fichier, sélectionnez **[!UICONTROL Élément sélectionné]** ou **[!UICONTROL Page]**, puis cliquez sur **[!UICONTROL Télécharger]** pour charger la ressource sélectionnée ou la conception entière dans le dossier de destination.
   ![charger la conception figma](/help/assets/assets/upload-figma-design.png)

## Points importants à noter{#Limitations-of-using-aem-assets-into-figma}

Cette intégration présente actuellement les limites suivantes :

* Pour importer des ressources [!DNL AEM] dans Figma, les formats pris en charge sont **JPEG** et **PNG**.
* Pour l’exportation de conceptions de [!DNL Figma] vers [!DNL AEM Assets], les formats pris en charge sont les suivants : **PNG**, **PDF**, **JPG**, **SVG**.
