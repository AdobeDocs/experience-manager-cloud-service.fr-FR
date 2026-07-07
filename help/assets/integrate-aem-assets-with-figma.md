---
title: Intégration  [!DNL AEM Assets]  à  [!DNL Figma].
description: Découvrez comment intégrer  [!DNL AEM Assets]  avec pour accéder  [!DNL Figma]  ressources de votre entreprise et les utiliser dans votre workflow  [!DNL Figma]  conception.
role: User
badgeSaas: label="AEM Assets" type="Positive" tooltip="S’applique à AEM Assets)."
exl-id: 530561ca-497b-4331-a014-72c561e1ca84
source-git-commit: d37ebf94f617e8424799757c18037a73e97820b4
workflow-type: tm+mt
source-wordcount: '1520'
ht-degree: 4%

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
1. Sélectionnez [!DNL Adobe Experience Manager (AEM) Assets Connector] pour afficher le panneau [!DNL Adobe Experience Manager (AEM) Assets Connector]. [Importez  [!DNL AEM]  ressources dans la zone  [!DNL Figma]  travail](#import-aem-assets-into-figma-workflow) à l’aide de ce panneau.   ![actions](/help/assets/assets/actions-on-figma.png)
Vous pouvez également accéder aux [[!DNL Adobe Experience Manager (AEM) Assets Connector]](https://www.figma.com/community/plugin/1512561378275712210/adobe-experience-manager-aem-assets-connector) disponibles sur [!DNL Figma] communauté, cliquer sur **[!UICONTROL Ouvrir dans...]**, sélectionner un fichier récent ou créer un fichier et cliquer sur **[!UICONTROL Exécuter]** pour accéder au panneau [!DNL Adobe Experience Manager (AEM) Assets Connector].   ![plugin-page-on-figma-community](/help/assets/assets/plugin-page-on-figma-community.png)

>[!NOTE]
>
> [Contactez l’assistance Adobe](https://helpx.adobe.com/fr/contact.html) pour obtenir de l’aide si un message **[!UICONTROL Erreur réseau]** s’affiche après vous être connecté à votre environnement [!DNL AEM].

## Importation de ressources [!DNL AEM] dans [!DNL Figma] zone de travail{#import-aem-assets-into-figma-workflow}

[Accédez au panneau Connecteur Assets [!UICONTROL Adobe Experience Manager (AEM)] &#x200B;](#access-aem-assets-connector) dans l’interface de conception de [!DNL Figma] et procédez comme suit :

1. Recherchez des ressources dans le panneau Connecteur Assets [!UICONTROL Adobe Experience Manager (AEM)]. Pour plus d’informations, voir [Utilisation du gestionnaire d’accès](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector#using-asset-selector).

1. Faites glisser et déposez la ressource sur la zone de travail ou sélectionnez la ressource et cliquez sur **[!UICONTROL Sélectionner]** pour apporter la ressource sur la zone de travail.

1. Cliquez sur ![trois points](/help/assets/assets/three-dots.svg) dans le chemin du dossier pour afficher tous les dossiers parents et enfants dans la hiérarchie actuelle. Sélectionnez un dossier pour accéder à cet emplacement.   ![trois points](/help/assets/assets/figma-v2-plugin.png)

1. [Facultatif] Cliquez sur **[!UICONTROL Rechercher les mises à jour]**. Les ressources utilisées dans le document Figma actuel sont comparées aux ressources qui existent dans AEM. Toutes les mises à jour sont répertoriées dans une fenêtre distincte. Cliquez sur **[!UICONTROL Mettre à jour]** pour obtenir la ressource mise à jour d’AEM dans votre document Figma.

Une fois votre conception Figma prête, vous pouvez [exporter la ressource vers le référentiel AEM Assets](#export-figma-design-to-aem-assets-folder).

## Exporter des ressources vers [!DNL AEM Assets] référentiel{#export-figma-design-to-aem-assets-folder}

[Accédez au panneau Connecteur Assets [!UICONTROL Adobe Experience Manager (AEM)] &#x200B;](#access-aem-assets-connector) dans l’interface de conception [!DNL Figma] et suivez les étapes ci-après pour exporter votre conception vers le référentiel [!DNL AEM Assets] :

1. Accédez au dossier de destination dans lequel vous souhaitez enregistrer votre conception de [!DNL Figma]. Si vous vous trouvez déjà dans un dossier, cliquez sur Autres options (![points de suspension](/help/assets/assets/three-dots.svg)) dans le chemin du dossier pour sélectionner un autre dossier de destination.
1. Facultatif : regroupez les ressources sur la zone de travail pour les sélectionner en tant qu’unité unique à charger dans votre dossier.
1. Cliquez sur ![Chargement de fichier](/help/assets/assets/upload-icon.svg) **[!UICONTROL Charger]** pour afficher la boîte de dialogue **[!UICONTROL Charger une ressource]**.
1. Dans la boîte de dialogue, sélectionnez **[!UICONTROL Élément sélectionné]** ou **[!UICONTROL Page]**, spécifiez un nom de fichier ou de page, définissez une configuration d’exportation et cliquez sur **[!UICONTROL Télécharger]** pour charger la ressource sélectionnée ou la conception entière dans le dossier de destination.

   La configuration de l’exportation comprend le format, l’échelle et la qualité du fichier. Par exemple, si vous sélectionnez JPG comme format de fichier, vous pouvez également définir l’échelle et la qualité de l’image. De même, si vous sélectionnez le format PNG comme format de fichier, vous pouvez également définir l’échelle de l’image.   ![charger la conception figma](/help/assets/assets/upload-figma-design.png)


## Questions fréquentes {#frequently-asked-questions-aem-assets-figma-integration}

### Que permet de faire l&#39;intégration d&#39;AEM Assets avec Figma ? {#aem-assets-figma-integration-overview}

L’intégration d’AEM Assets à Figma permet aux concepteurs d’accéder directement aux ressources stockées dans Adobe Experience Manager depuis l’interface utilisateur de Figma, sans passer d’un outil à l’autre. Les concepteurs et conceptrices peuvent rechercher et importer des images, des vidéos, des fichiers animés et des vecteurs d’AEM Assets dans la zone de travail Figma, et exporter les conceptions terminées ou modifiées dans le référentiel AEM Assets dans les formats pris en charge. L’intégration est native, et ne nécessite aucun connecteur tiers en dehors du connecteur AEM Assets Adobe Experience Manager disponible sur la communauté Figma.

### Quelles sont les conditions préalables à l&#39;intégration d&#39;AEM Assets avec Figma ? {#aem-assets-figma-prerequisites}

L’intégration d’AEM Assets à Figma nécessite deux conditions préalables : une version minimale d’AEM de 19149 et des licences valides pour AEM Assets et Figma. Ces deux conditions doivent être remplies pour que le connecteur Adobe Experience Manager AEM Assets soit accessible et utilisé dans Figma. Si un message d’erreur réseau s’affiche après la connexion à l’environnement AEM au cours de la configuration, contactez le support technique d’Adobe pour obtenir de l’aide.

### Comment puis-je accéder au connecteur Adobe Experience Manager AEM Assets dans Figma ? {#access-aem-assets-connector-figma}

Le connecteur Adobe Experience Manager AEM Assets est accessible de deux manières depuis Figma. Sur la page d’accueil de Figma, cliquez sur **Actions** dans la barre d’outils située au bas de la zone de travail, recherchez Adobe Experience Manager AEM Assets Connector dans la boîte de dialogue, puis sélectionnez-le pour ouvrir le panneau du connecteur. Vous pouvez également accéder au connecteur directement à partir de la page de la communauté Figma, cliquer sur **Ouvrir dans**, sélectionner un fichier récent ou créer un nouveau fichier, puis cliquer sur **Exécuter** pour lancer le panneau du connecteur.

### Quels formats de fichiers peuvent être importés d&#39;AEM Assets dans Figma ? {#aem-assets-figma-import-formats}

Les formats de fichiers pris en charge pour l’importation d’AEM Assets dans Figma sont les suivants : ressources d’image aux formats JPEG et PNG, fichiers vidéo aux formats MP4, MOV et WebM, fichiers animés au format GIF et fichiers vectoriels au format SVG. Dans ces formats, il est possible de rechercher Assets dans le panneau Connecteur Adobe Experience Manager AEM Assets et de le placer directement sur la zone de travail Figma en effectuant un glisser-déposer ou en sélectionnant la ressource et en cliquant sur Sélectionner .

### Comment importer une ressource d’AEM Assets dans ma zone de travail Figma ? {#import-aem-assets-figma-canvas}

Pour importer une ressource d’AEM Assets dans Figma, ouvrez le panneau Connecteur Adobe Experience Manager AEM Assets dans l’interface de conception de Figma. Recherchez la ressource à l’aide du gestionnaire d’accès dans le panneau du connecteur. Une fois la ressource localisée, faites-la glisser et déposez-la sur la zone de travail ou sélectionnez-la et cliquez sur **Sélectionner** pour la placer sur la zone de travail. Pour parcourir les dossiers dans le référentiel, cliquez sur l’icône des trois points dans le chemin du dossier pour afficher et parcourir les dossiers parents et enfants dans la hiérarchie actuelle.

### Comment puis-je vérifier si AEM Assets utilisé dans mon document Figma a été mis à jour ? {#check-aem-assets-updates-figma}

Le connecteur AEM Assets Adobe Experience Manager dans Figma comprend une option **Vérifier les mises à jour** qui compare les ressources actuellement utilisées dans le document Figma ouvert à leurs versions dans AEM Assets. Pour l’utiliser, ouvrez le panneau des connecteurs et cliquez sur **Rechercher des mises à jour**. Toutes les ressources qui ont été mises à jour dans AEM sont répertoriées dans une fenêtre distincte. Cliquez sur **Mettre à jour** pour extraire la dernière version de chaque ressource mise à jour d’AEM dans le document Figma.

### Quels formats de fichier sont pris en charge lors de l’exportation d’une conception Figma vers AEM Assets ? {#figma-export-aem-assets-formats}

Lors de l’exportation d’une conception Figma dans le référentiel AEM Assets, quatre formats de fichier sont pris en charge : PNG, PDF, JPG et SVG. La configuration de l’exportation permet également de définir des paramètres supplémentaires en fonction du format sélectionné. Pour les exportations JPG, l’échelle et la qualité de l’image peuvent être spécifiées. Pour les exportations PNG, l’échelle de l’image peut être définie. Ces paramètres sont configurés dans la boîte de dialogue Charger la ressource pendant le processus d’exportation.

### Comment exporter une conception Figma vers le référentiel AEM Assets ? {#export-figma-design-aem-assets}

Pour exporter une conception Figma vers AEM Assets, ouvrez le panneau Adobe Experience Manager AEM Assets Connector dans Figma et accédez au dossier de destination dans le référentiel AEM Assets. Cliquez sur l’icône Charger pour ouvrir la boîte de dialogue Charger une ressource . Dans la boîte de dialogue, sélectionnez Élément sélectionné pour charger une ressource spécifique ou Page pour charger la page de conception entière, spécifiez un nom de fichier ou de page, définissez la configuration d’exportation, y compris le format, l’échelle et la qualité, puis cliquez sur Charger. La conception est enregistrée dans le dossier de destination AEM Assets sélectionné.

### Puis-je regrouper des ressources dans Figma avant de les exporter vers AEM Assets ? {#group-assets-figma-export-aem}

Les conceptions Figma peuvent être regroupées sur la zone de travail avant d’être exportées vers le référentiel AEM Assets. Le regroupement de ressources permet de les sélectionner en une seule unité et de les charger ensemble dans le dossier de destination en une seule opération. Après le regroupement, ouvrez le panneau Connecteur Adobe Experience Manager AEM Assets, accédez au dossier de destination, cliquez sur Charger, sélectionnez les éléments regroupés en tant qu’Élément sélectionné dans la boîte de dialogue Charger une ressource, configurez les paramètres d’exportation, puis cliquez sur Charger.

### Comment naviguer dans les dossiers du référentiel AEM Assets depuis Figma ? {#navigate-aem-folders-figma}

La navigation entre les dossiers du référentiel AEM Assets est disponible directement dans le panneau du connecteur AEM Assets de Adobe Experience Manager dans Figma. Cliquez sur l’icône en forme de trois points dans le chemin du dossier pour afficher tous les dossiers parents et enfants dans la hiérarchie actuelle. Sélectionnez un dossier dans la liste pour accéder à cet emplacement. Lors de l’exportation d’une conception dans un autre dossier de destination, cliquez sur Autres options dans le chemin du dossier pour sélectionner un autre dossier dans le référentiel AEM Assets.


**Voir également**

* [Traduire les ressources](/help/assets/translate-assets.md)
* [API HTTP Assets](/help/assets/mac-api-assets.md)
* [Formats de fichiers pris en charge par Assets](/help/assets/file-format-support.md)
* [Rechercher des ressources](/help/assets/search-assets.md)
* [Ressources connectées](/help/assets/use-assets-across-connected-assets-instances.md)
* [Rapports de ressources](/help/assets/asset-reports.md)
* [Schémas de métadonnées](/help/assets/metadata-schemas.md)
* [Télécharger des ressources](/help/assets/download-assets-from-aem.md)
* [Gestion des métadonnées](/help/assets/manage-metadata.md)
* [Gérer les modèles Dynamic Media](/help/assets/dynamic-media/manage-dynamic-media-templates.md)
* [Gérer les rapports](/help/assets/manage-reports-assets-view.md)
* [Facettes de recherche](/help/assets/search-facets.md)
* [Gérer les collections](/help/assets/manage-collections.md)
* [Import des métadonnées en bloc](/help/assets/metadata-import-export.md)
* [Publier des ressources sur AEM et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

