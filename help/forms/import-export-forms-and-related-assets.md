---
title: Importation et exportation de ressources dans [!DNL AEM Forms]?
description: Découvrez comment utiliser DocuSign avec un formulaire adaptatif pour collecter des signatures électroniques.
source-git-commit: abe5f8a4b19473c3dddfb79674fb5f5ab7e52fbf
workflow-type: tm+mt
source-wordcount: '1313'
ht-degree: 73%

---


# Importation et exportation des ressources {#importing-and-exporting-assets-to-aem-forms}

Vous pouvez déplacer des formulaires, des thèmes, des modèles, des fragments de document, des thèmes et autres ressources entre différentes instances [!DNL AEM Forms]. Ce déplacement est nécessaire lors de la migration des systèmes ou du déplacement des formulaires d’un serveur de développement ou d’évaluation vers un serveur de production.

Pour les ressources pour lesquelles le chargement et l’importation sont pris en charge via l’interface utilisateur [!DNL AEM Forms], l’utilisation de l’interface utilisateur de Forms est recommandée pour l’exportation ou l’importation. L’utilisation du gestionnaire de packages d’AEM pour l’exportation ou l’importation de ces ressources n’est pas recommandée.

## Téléchargement et chargement de ressources de formulaires et documents {#download-or-upload-forms-amp-documents-assets}

[!DNL AEM Forms] L’interface utilisateur vous permet d’exporter des ressources à partir d’une instance AEM en les téléchargeant sous la forme d’un package CRX ou de fichiers binaires AEM. Vous pouvez ensuite importer le package CRX ou le fichier binaire AEM téléchargé dans une autre instance AEM.

L’exportation et l’importation via l’interface utilisateur [!DNL AEM Forms] sont prises en charge pour toutes les ressources, à l’exception des modèles et des politiques de contenu de formulaires adaptatifs. Par conséquent, lors de l’exportation d’un formulaire adaptatif depuis l’interface utilisateur [!DNL AEM Forms], le modèle de formulaire adaptatif associé et les politiques de contenus ne sont pas automatiquement exportés comme d’autres ressources associées.

Pour ces types de ressources, vous devez utiliser le gestionnaire de modules d’AEM pour créer un package CRX sur le serveur AEM source et pour installer le module sur le serveur de destination. Pour plus d’informations sur la création et l’installation de packages, consultez [Déploiement sur AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=fr).

### Téléchargement des ressources de formulaires et documents {#download-forms-amp-documents-assets}

Pour télécharger des ressources de formulaires et de documents :

1. Connectez-vous à l’instance [!DNL AEM Forms].
1. Sélectionner un Experience Manager ![adobeexperiencemanager](assets/adobeexperiencemanager.png) icône > navigation ![boussole](assets/Smock_Compass_18_N.svg) icon> **[!UICONTROL Forms]** > **[!UICONTROL Forms et documents]**.
1. Sélectionnez les actifs de formulaire et sélectionnez l’événement **[!UICONTROL Télécharger]** Icône
1. Dans la ou les ressources de téléchargement, choisissez l’une des options suivantes, puis sélectionnez **[!UICONTROL Télécharger]**.

   * **Télécharger en tant que package CRX :** utilisez cette option pour télécharger et déplacer toutes les ressources sélectionnées et les dépendances connexes d’une instance [!DNL AEM Forms] vers une autre. Toutes les ressources et tous les dossiers sont téléchargés sous forme de package CRX. Tous les actifs de formulaire, y compris les formulaires créés dans AEM (Adaptive Forms et Fragments de formulaire adaptatif), les documents PDF et les ressources (XSD, XFS, images) peuvent être téléchargés en tant que package depuis [!DNL AEM Forms] Interface utilisateur.
L’avantage du téléchargement des ressources sous forme de package est le téléchargement des ressources qui ont été utilisées par la ressource à télécharger. Par exemple, si vous avez un formulaire adaptatif qui utilise un modèle de formulaire, le schéma XSD et l’image. Lorsque vous sélectionnez ce formulaire adaptatif et vous le téléchargez sous forme de package, le package téléchargé contient également le modèle de formulaire, le schéma XSD et l’image. Toutes les propriétés de métadonnées (propriétés personnalisées incluses) associées à la ressource sont également téléchargées.

   * **Téléchargement de ressources sous forme de fichiers binaires :** Utilisez l’option pour télécharger uniquement les modèles de formulaire (XDP), les PDF forms (PDF), le document (PDF) et les ressources (images, schémas, feuilles de style). Vous pouvez modifier ces ressources dans des applications externes. Cette option permet de télécharger les ressources de formulaires qui possèdent des fichiers binaires, telles que des fichiers XSD, XDP, des images, des fichiers PDF et XDP comme un fichier .zip.
Vous ne pouvez pas télécharger de Forms adaptatif, de fragments de formulaire adaptatif et de thèmes avec **[!UICONTROL Téléchargement de ressources en tant que fichiers binaires]** . Pour télécharger ces ressources, vous devez utiliser l’option **[!UICONTROL Télécharger sous forme de package CRX]**.

   Les ressources sélectionnées sont téléchargées sous forme d’archive (fichier .zip).

   >[!NOTE]
   >
   >Le package et les fichiers binaires AEM sont téléchargés sous forme d’archive (fichier .zip). Les modèles des ressources ne sont pas téléchargés avec les ressources. Vous devez exporter les modèles de ressources séparément.

### Charger des ressources {#upload-forms-amp-documents-assets}

Pour charger des ressources de formulaires et documents :

1. Connectez-vous à l’instance [!DNL AEM Forms].
1. Sélectionner un Experience Manager ![adobeexperiencemanager](assets/adobeexperiencemanager.png) icône > navigation ![boussole](assets/Smock_Compass_18_N.svg) icon> **[!UICONTROL Forms]** > **[!UICONTROL Forms et documents]**.
1. Sélectionner **Créer** >**Téléchargement du fichier**. Une boîte de dialogue de téléchargement de formulaires ou de package apparaît.
1. Dans la boîte de dialogue, recherchez et sélectionnez le package ou l’archive à importer. Vous pouvez également sélectionner le document PDF, les fichiers XSD, les images, les feuilles de style et les formulaires XDP. Sélectionner **[!UICONTROL Ouvrir]**. Le dossier ou le nom de fichier que vous sélectionnez ne doit pas contenir de caractères spéciaux.

   Dans la boîte de dialogue, vérifiez les détails des ressources en cours de chargement, puis sélectionnez **[!UICONTROL Télécharger]**.

   Si vous chargez une ressource de formulaires existants, la ressource est mise à jour.

   >[!NOTE]
   >
   >Le téléchargement du package ne remplace pas la hiérarchie des dossiers existante. Par exemple, si vous avez un formulaire adaptatif nommé « Training » à l’emplacement /content/dam/formsanddocuments sur un serveur. Vous téléchargez le formulaire adaptatif et le chargez sur un autre serveur. Le deuxième serveur dispose également d’un dossier nommé « Training » au même emplacement /content/dam/formsanddocuments. Le chargement échoue.

## Téléchargement ou chargement d’un thème {#downloading-or-uploading-a-theme}

Avec [!DNL AEM Forms], vous pouvez créer, télécharger et charger des thèmes. Un thème est créé comme d’autres ressources tels que les formulaires, les documents et les lettres. Vous pouvez créer un thème, le télécharger et le charger sur une instance distincte pour le réutiliser. Pour plus d’informations sur les thèmes, consultez [Thèmes](themes.md) dans [!DNL AEM Forms].

### Téléchargement d’un thème {#downloading-a-theme}

Vous pouvez exporter des thèmes dans [!DNL AEM Forms] que vous pouvez utiliser dans d’autres projets ou instances. AEM vous permet de télécharger le thème sous la forme d’un fichier zip, que vous pouvez charger sur l’instance.

Pour télécharger un thème :

1. Connectez-vous à l’instance [!DNL AEM Forms].
1. Sélectionner un Experience Manager ![adobeexperiencemanager](assets/adobeexperiencemanager.png) icône > navigation ![boussole](assets/Smock_Compass_18_N.svg) icon> **[!UICONTROL Forms]** > **[!UICONTROL Thèmes]**.
1. Sélectionnez le thème et sélectionnez **[!UICONTROL Télécharger]**. Le thème est téléchargé sous forme d’archive (fichier .zip).

### Chargement d’un thème {#uploading-a-theme}

Vous pouvez utiliser des thèmes créés avec des paramètres prédéfinis de style sur votre projet. Vous pouvez importer des packages de thème que d’autres créent en les chargeant sur votre projet.

Pour charger un thème :

1. Dans Experience Manager, accédez à **[!UICONTROL Formulaires]** > **[!UICONTROL Thèmes de formulaires]**.
1. Dans la page Thèmes, cliquez sur **[!UICONTROL Créer un formulaire]** > **[!UICONTROL Charger un fichier de formulaire]**.
1. Dans l’invite de téléchargement de fichier, recherchez et sélectionnez un package de thème sur votre ordinateur et cliquez sur **[!UICONTROL Charger un formulaire]**. Le thème est chargé.

<!--

## Import and export assets in Correspondence Management {#import-and-export-assets-in-correspondence-management}

To share assets, such as data dictionaries, letters, and document fragments, between two different implementations of Correspondence Management, you can create and share .cmp files. A .cmp file can include one or more data dictionaries, letters, document fragments, and forms.

### Export Document Fragments, Letters, and/or Data Dictionaries {#export-document-fragments-letters-and-or-data-dictionaries}

1. In the letters, document fragments, or data dictionary pages, select and select the assets you want to export to a single package, and then select Queue For Download. The assets are lined-up for export.
1. As required, repeat the above step to add letters, document fragments, and data dictionaries.
1. Select **Download**.
1. Correspondence Management displays Download Asset(s) dialog with a list of assets in the export list.

   ![export](assets/export.png)

1. To view the dependencies that are exported, Select Resolve. Or skip to the next step. Even if you do not select resolve, the dependencies are still exported.
1. To download the .cmp file, select **OK**.
1. Correspondence Management downloads a .cmp file to your computer.

   The .cmp file includes the exported assets. You can share the .cmp file with others. Other users can import the .cmp file in a different server to get all the assets in the new server.

### Export all the Correspondence Management assets as a package {#export-all-the-correspondence-management-assets-as-a-package}

Use this option to download all the Correspondence Management assets and related dependencies as a package from an [!DNL AEM Forms] instance.

For example, if Correspondence Management has a letter that uses an image and text, the downloaded package also contains the image and the text related to the letter. All the metadata properties (including custom properties) associated with the asset are also downloaded. Once you have downloaded the package (.cmp), you can [import the package to a different [!DNL AEM Forms] instance](import-export-forms-templates.md#p-upload-forms-documents-assets-p).

To download all the Correspondence Management assets and related dependencies as a package, complete the following steps:

1. Log in to [!DNL AEM Forms] server as a forms user.
1. Select **Adobe Experience Manager** in the Global Navigation bar.
1. Select tools ( ![tools](assets/tools.png)) and then select **Forms**.
1. Select **Export Correspondence Management Assets**.

   ![publish-cmp-assets-1](assets/publish-cmp-assets-1.png)

   ( ``The Export All Correspondence Management Assets page appears and displays the information about the last time the Export process was attempted and a link to download the last successfully exported package.

   ![export-last-run-details](assets/export-last-run-details.png)

1. Select **Export** and, in the confirm message, select **OK**.

   After a batch process is complete, the last run details and the link to download the package are updated. This includes information such as the Administrator login and if the batch run successfully or failed. The assets are exported to a package and the Download Exported Package link appears.

   >[!NOTE]
   >
   >The Export All Assets process cannot be canceled once initiated. Also, while the export all operation is in process, do not create, delete, modify, or publish any assets or initiate Publish All Assets process.a

1. Select the **Download Exported Package** link to download the package file.

   To add the assets in the package to another instance of Correspondence Management, [import the package to an [!DNL AEM Forms] instance](import-export-forms-templates.md#p-upload-forms-documents-assets-p).

### Import Document Fragments, Letters and/or Data Dictionaries into Correspondence Management {#import-document-fragments-letters-and-or-data-dictionaries-into-correspondence-management}

You can import assets that are exported into a .cmp file. A .cmp file can have one or more letters, data dictionaries, document fragments, and dependent assets.

>[!NOTE]
>
>While importing old Correspondence Management assets for migration, log in using an Admin account. For more information on Migrating old Correspondence Management assets, see [Migrate Correspondence Management assets to AEM 6.1 forms](migration-utility.md).

1. On the data dictionary, letters, or document fragments page, select **Create &gt; File Upload** and select the .cmp file.
1. Correspondence Management displays the Import Assets dialog with the list of assets that are imported. Select **Import**.

   After importing the assets, the following properties of the assets are updated while the other properties remain the same:

    * Author: Displays the ID of the user that imported the asset to the server
    * Modified: The time when the asset was imported to the server

   >[!NOTE]
   >
   >For you to be able to upload XDPs (as part of the cmp file or otherwise), you need to be a part of forms-power-users group. For access rights, contact the administrator.
-->

## Exporter une application de workflow {#export-a-workflow-application}

Vous pouvez utiliser le gestionnaire de packages AEM pour exporter des applications de workflow. Pour ce faire, procédez comme suit :

1. Ouvrez le gestionnaire de packages [!DNL AEM Forms].
1. Cliquez sur **[!UICONTROL Créer un package]**. La boîte de dialogue **[!UICONTROL Nouveau package]** apparaît.
1. Indiquez le nom, la version et le groupe du package. Cliquez sur **[!UICONTROL OK]**.
1. Cliquez sur **[!UICONTROL Modifier]** et ouvrez l’onglet **[!UICONTROL Filtres]**. Cliquez sur **[!UICONTROL Ajouter un filtre]**. Spécifiez le chemin d’accès de l’application de workflow. Par exemple, /etc/fd/dashboard/startpoints/homemortgage. Cliquez sur **[!UICONTROL Ajouter une règle]**.

1. Ouvrez l’onglet **[!UICONTROL Avancé]**. Sélectionnez **[!UICONTROL Fusionner]** ou **[!UICONTROL Remplacer]** dans le champ Gestion de l’ACL. Cliquez sur **[!UICONTROL Enregistrer]**.
1. Cliquez sur **[!UICONTROL Générer]** pour créer le package.

   Une fois le package créé, vous pouvez le télécharger et l’importer sur l’autre serveur. L’application de workflow apparaît sur le serveur sur lequel le package est téléchargé.

   >[!NOTE]
   >
   >Pour que l’application de processus fonctionne correctement, exportez également le formulaire adaptatif et le modèle de processus correspondants avec l’application de travail.

## Dossiers et organisation des ressources {#folders-and-organizing-assets}

L’interface utilisateur [!DNL AEM Forms] utilise des dossiers pour classer les ressources. Ces dossiers sont utilisés pour classer les ressources créées dans l’interface utilisateur [!DNL AEM Forms]. Vous pouvez renommer, créer des sous-dossiers et stocker des ressources et des documents dans ces dossiers. L’organisation des documents et des ressources dans un dossier vous permet de regrouper les fichiers pour une gestion simplifiée. Vous pouvez sélectionner un fichier et choisir de le télécharger ou de le supprimer.

Pour créer un dossier, procédez comme suit :

### Créer un dossier {#create-a-folder}

1. Connectez-vous à l’interface utilisateur [!DNL AEM Forms] à l’adresse `https://<server>:<port>/aem/forms.html`.
1. Accédez à l’emplacement où vous souhaitez créer un dossier.
1. Sélectionner **[!UICONTROL Créer]** > **[!UICONTROL Dossier]**.
1. Saisissez les informations suivantes :

   * **Titre** : nom d’affichage du dossier.
   * **Nom** : *(Obligatoire)* nom du nœud sous lequel vous souhaitez stocker le dossier dans le référentiel.

   >[!NOTE]
   >
   >par défaut, la valeur du champ Nom est automatiquement renseignée à partir du titre. Le nom ne peut contenir que des caractères alphanumériques ou des tirets (-) et des traits de soulignement (_). Tous les autres caractères spéciaux saisis dans le titre sont automatiquement remplacés par un trait d’union. Vous êtes invité à confirmer le nouveau nom. Vous pouvez continuer avec le nom proposé ou le modifier davantage.

1. Un nouveau dossier avec le titre que vous avez défini s’affiche à l’emplacement spécifié dans la liste des ressources.

   Si un dossier portant le même nom que celui spécifié existe déjà, l’envoi échoue avec une erreur. Vous pouvez afficher le message d’erreur en pointant sur l’icône d’erreur ![aem6forms_error_alert](assets/Smock_Alert_18_N.svg) qui s’affiche en regard du champ Nom.

   Vous pouvez sélectionner le dossier créé pour y accéder et y créer des ressources ou des dossiers. De plus, vous pouvez sélectionner un dossier et choisir de le mettre en file d’attente pour le télécharger, le supprimer ou modifier son nom.

<!-- ### Create copies of one or more assets or letters {#create-copies-of-one-or-more-assets-or-letters}

You can use an existing assets and letters to quickly create a assets and letters with similar properties, content, and inherited assets. You can copy and paste data dictionaries, document fragments, and letters.

Complete the following steps to create copies of assets and letters:

1. In the relevant Assets or Letters page, select one or more assets/letters. The UI displays the Copy icon.
1. Select Copy. The UI displays the Paste icon. You can also choose to go/navigate inside a folder before you paste. Different folders can contain assets with same names. For more information on folders, see [Folders and organizing assets](#folders-and-organizing-assets).
1. Select Paste. The Paste dialog appears. The system auto generates names and titles to the new copies of assets/letters, but you can edit the titles and names of the assets/letters.

   If you are copying and pasting the assets/letters at the same place, a suffix "-CopyXX" gets added to the existing name of the asset/letter. If no title existed for the copied asset/letter, the auto generated title field remains blank.

1. If necessary, edit the Title and Name with which you want to save the copy of the asset/letter.
1. Select Paste. New copies of the copied assets are created.

## Search {#search-forms}

[!DNL AEM Forms] UI lets you search your content. Using the top bar, you can select Search **[A]** to search your content for resources such as assets and documents.

When you search for assets, [!DNL AEM Forms] displays the side panel. You can also select ![assets-browser-content-only](assets/assets-browser-content-only.png) &gt; Filter **[B]** to invoke the side panel. Using the various filters in the side panel, you can narrow down your search. The side panel also lets you save your searches.

![search_topbar](assets/search_topbar.png)

**A.** Search **B.** Filter

![Side panel - Filters](assets/search_sidepanel.png)

Side panel - Filters

On the side panel, you can use the following to narrow down your search results:

* Search Directory
* Tags
* Search Criteria; for example, Modified Dates, Publish Status, LiveCopy Status.

The side panel also lets you save your search settings with names of your choice.

For more information and instructions on using search, filters, saved search, and side panel, see [Search](/help/sites-authoring/search.md).

-->

>[!MORELIKETHIS]
>
>* [Importation de modèles de formulaires d’exportation](/help/forms/import-export-forms-templates.md)
>* [Utilisation de thèmes dans les composants principaux de formulaire adaptatif](/help/forms/using-themes-in-core-components.md)