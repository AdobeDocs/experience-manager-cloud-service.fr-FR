---
title: Importation ou exportation d’actifs Forms adaptatifs et AEM Forms
description: Vous souhaitez migrer des formulaires adaptatifs et des ressources depuis et vers une instance AEM ? Découvrez dans cette section comment importer et exporter des formulaires adaptatifs, des formulaires PDF, des thèmes et d’autres ressources depuis une instance [!DNL AEM Forms]
seo-description: Looking to migrate Adaptive Forms and assets to and from an AEM instances? Learn here how to import and export Adaptive Forms, PDF forms, themes, and other supporting assets from an [!DNL AEM Forms] instance.
topic-tags: forms-manager
source-git-commit: b8366fc19a89582f195778c92278cc1e15b15617
workflow-type: tm+mt
source-wordcount: '1206'
ht-degree: 87%

---

# Importation ou exportation d’actifs Forms adaptatifs et AEM Forms {#importing-and-exporting-assets-to-aem-forms}

Vous pouvez déplacer des formulaires adaptatifs et des ressources connexes telles que des thèmes de formulaire adaptatif, des modèles de données de formulaire, des modèles de formulaire adaptatif, des fragments de document et des formulaires PDF entre des instances [!DNL AEM Forms]. Vous pouvez importer et exporter des ressources dans un package CRX ou dans des formats de fichiers binaires.

Lorsque vous exportez un formulaire adaptatif, les politiques de contenu et les modèles ne sont pas exportés. Utilisez le [gestionnaire de packages](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=fr#how-rolling-deployments-work) pour exporter de telles ressources.

## Téléchargement de formulaires adaptatifs, de PDF forms ou de ressources connexes {#download-forms-amp-documents-assets}

Pour télécharger des formulaires ou des ressources connexes :

1. Connectez-vous à l’instance [!DNL AEM Forms].
1. Appuyez sur **[!UICONTROL Adobe Experience Manager]** icône ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** icône ![compass](assets/Smock_Compass_18_N.svg) > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.
1. Sélectionnez les ressources et appuyez sur l’icône de **[!UICONTROL téléchargement]**.
1. Dans Télécharger la ou les ressources, choisissez l’une des options suivantes, puis cliquez sur **[!UICONTROL Télécharger]**.

   * **Télécharger en tant que package CRX :** utilisez cette option pour télécharger et déplacer toutes les ressources sélectionnées et les dépendances connexes d’une instance [!DNL AEM Forms] vers une autre. Cette option permet de télécharger toutes les ressources et tous les dossiers sous la forme d’un package CRX, y compris les formulaires créés dans AEM (formulaires adaptatifs et fragments de formulaire adaptatif), les ensembles de formulaires, le modèle de données de formulaire, les modèles de formulaire, les documents PDF et les ressources référencées (schémas XSD et images).
L’avantage du téléchargement des ressources sous la forme d’un package est que les ressources référencées par les ressources sélectionnées sont également téléchargées. C’est le cas par exemple si vous disposez d’un formulaire adaptatif qui utilise un modèle de formulaire, le schéma XSD et une image. Lorsque vous sélectionnez ce formulaire adaptatif et que vous le téléchargez sous forme de package, le package téléchargé contient également le modèle de formulaire, le schéma XSD et l’image. Toutes les propriétés de métadonnées (propriétés personnalisées incluses) associées à la ressource sont également téléchargées.

   * **Télécharger la/les ressources sous forme de fichiers binaires :** utilisez cette option pour télécharger uniquement les modèles de formulaire (XDP), les formulaires PDF (PDF), les documents (PDF) et les ressources (images, schémas, feuilles de style). Vous pouvez modifier ces ressources dans des applications externes. Il télécharge les ressources comportant des fichiers binaires, tels que des images, des fichiers PDF et d’autres formats pris en charge sous la forme d’un fichier .zip.
Vous ne pouvez pas télécharger de formulaires adaptatifs, de fragments de formulaires adaptatifs, de thèmes ni d’ensembles de formulaires avec l’option **[!UICONTROL Télécharger des ressources en tant que fichiers binaires]**. Pour télécharger ces ressources, vous devez utiliser l’option **[!UICONTROL Télécharger sous forme de package CRX]**.

   Les ressources sélectionnées sont téléchargées sous forme d’archive (fichier .zip).

   >[!NOTE]
   >
   >Le package et les fichiers binaires AEM sont téléchargés sous forme d’archive (fichier .zip). Les modèles des ressources ne sont pas téléchargés avec les ressources. Vous devez exporter les modèles de ressources séparément.

## Chargement de formulaires adaptatifs, de PDF forms ou de ressources connexes {#upload-forms-amp-documents-assets}

Vous pouvez charger les types de ressource pris en charge individuellement ou sous la forme d’une archive ZIP. Pour un fichier ZIP, les chemins d’accès relatifs de toutes les ressources prises en charge s’affichent. Les ressources non prises en charge dans le fichier ZIP sont ignorées et ne sont pas répertoriées. Cependant, si l’archive ZIP contient uniquement des éléments non pris en charge, un message d’erreur s’affiche à la place de la boîte de dialogue pop-up.
Pour charger un formulaire ou une ressource connexe :

1. Connectez-vous à l’instance [!DNL AEM Forms].
1. Cliquez sur **[!UICONTROL Adobe Experience Manager]** icône ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** icône ![compass](assets/Smock_Compass_18_N.svg) > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.
1. Appuyez sur **[!UICONTROL Créer]** > **[!UICONTROL Chargement de fichier]**. Une boîte de dialogue s’affiche.
1. Dans la boîte de dialogue, recherchez et sélectionnez le package ou l’archive à importer. Vous pouvez également sélectionner d’autres types de fichiers pris en charge. Appuyez sur **[!UICONTROL Ouvrir]**. Le dossier ou le nom de fichier que vous sélectionnez ne doit pas contenir de caractères spéciaux.

   Dans la boîte de dialogue, vérifiez les détails des ressources en cours de chargement, puis appuyez sur **[!UICONTROL Charger]**.

   Si vous chargez une ressource de formulaires existants, la ressource est mise à jour.

   >[!NOTE]
   >
   > * Lorsqu’un nom entre en conflit avec différents types de ressources, le chargement d’un package ne remplace pas la hiérarchie de dossiers existante. Par exemple, si vous avez un formulaire adaptatif nommé « Training » à l’emplacement /content/dam/formsanddocuments sur un serveur. Vous téléchargez le formulaire adaptatif et le chargez sur un autre serveur. Le deuxième serveur dispose également d’un dossier nommé « Formation » au même emplacement /content/dam/formsanddocuments. Le chargement échoue.
   > * Seul un membre du groupe `form-power-user` peut charger des fichiers XDP.


## Télécharger un thème {#downloading-a-theme}

Vous pouvez exporter des thèmes dans [!DNL AEM Forms] que vous pouvez utiliser dans d’autres projets ou instances. AEM vous permet de télécharger des thèmes sous la forme d’un fichier zip, que vous pouvez charger sur l’instance.

Pour télécharger un thème :

1. Connectez-vous à l’instance [!DNL AEM Forms].
1. Appuyez sur **[!UICONTROL Adobe Experience Manager]** icône ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** icône ![compass](assets/Smock_Compass_18_N.svg) > **[!UICONTROL Formulaires]** > **[!UICONTROL Thèmes]**.
1. Sélectionnez le composant et appuyez sur **[!UICONTROL Télécharger]**. Le thème est téléchargé sous forme d’archive (fichier .zip).

## Charger un thème {#uploading-a-theme}

Vous pouvez charger et utiliser des thèmes que d’autres créent dans vos formulaires. Pour charger un thème :

1. Dans Experience Manager, accédez à **[!UICONTROL Formulaires]** > **[!UICONTROL Thèmes]**.
1. Sur la page Thèmes, cliquez sur **[!UICONTROL Créer]** > **[!UICONTROL Chargement de fichier]**.
1. Dans l’invite de chargement de fichier, recherchez et sélectionnez un package de thème sur votre ordinateur et cliquez sur **[!UICONTROL Charger]**. Le thème chargé est disponible dans la page Thèmes.

<!-- ## Import and export assets in Correspondence Management {#import-and-export-assets-in-correspondence-management}

To share assets, such as data dictionaries, letters, and document fragments, between two different implementations of Correspondence Management, you can create and share .cmp files. A .cmp file can include one or more data dictionaries, letters, document fragments, and forms.

### Export Document Fragments, Letters, and/or Data Dictionaries {#export-document-fragments-letters-and-or-data-dictionaries}

1. In the letters, document fragments, or data dictionary pages, tap and select the assets you want to export to a single package, and then tap Queue For Download. The assets are lined-up for export.
1. As required, repeat the above step to add letters, document fragments, and data dictionaries.
1. Tap **Download**.
1. Correspondence Management displays Download Asset(s) dialog with a list of assets in the export list.

   ![export](assets/export.png)

1. To view the dependencies that are exported, Tap Resolve. Or skip to the next step. Even if you do not tap resolve, the dependencies are still exported.
1. To download the .cmp file, tap **OK**.
1. Correspondence Management downloads a .cmp file to your computer.

   The .cmp file includes the exported assets. You can share the .cmp file with others. Other users can import the .cmp file in a different server to get all the assets in the new server.

### Export all the Correspondence Management assets as a package {#export-all-the-correspondence-management-assets-as-a-package}

Use this option to download all the Correspondence Management assets and related dependencies as a package from an [!DNL AEM Forms] instance.

For example, if Correspondence Management has a letter that uses an image and text, the downloaded package also contains the image and the text related to the letter. All the metadata properties (including custom properties) associated with the asset are also downloaded. Once you have downloaded the package (.cmp), you can [import the package to a different [!DNL AEM Forms] instance](import-export-forms-templates.md#p-upload-forms-documents-assets-p).

To download all the Correspondence Management assets and related dependencies as a package, complete the following steps:

1. Log in to [!DNL AEM Forms] server as a forms user.
1. Tap **Adobe Experience Manager** in the Global Navigation bar.
1. Tap tools ( ![tools](assets/tools.png)) and then tap **Forms**.
1. Tap **Export Correspondence Management Assets**.

   ![publish-cmp-assets-1](assets/publish-cmp-assets-1.png)

   ( ``The Export All Correspondence Management Assets page appears and displays the information about the last time the Export process was attempted and a link to download the last successfully exported package.

   ![export-last-run-details](assets/export-last-run-details.png)

1. Tap **Export** and, in the confirm message, tap **OK**.

   After a batch process is complete, the last run details and the link to download the package are updated. This includes information such as the Administrator login and if the batch run successfully or failed. The assets are exported to a package and the Download Exported Package link appears.

   >[!NOTE]
   >
   >The Export All Assets process cannot be canceled once initiated. Also, while the export all operation is in process, do not create, delete, modify, or publish any assets or initiate Publish All Assets process.a

1. Tap the **Download Exported Package** link to download the package file.

   To add the assets in the package to another instance of Correspondence Management, [import the package to an [!DNL AEM Forms] instance](import-export-forms-templates.md#p-upload-forms-documents-assets-p).

<!-- ### Import Document Fragments, Letters and/or Data Dictionaries into Correspondence Management {#import-document-fragments-letters-and-or-data-dictionaries-into-correspondence-management}

You can import assets that are exported into a .cmp file. A .cmp file can have one or more letters, data dictionaries, document fragments, and dependent assets.

>[!NOTE]
>
>While importing old Correspondence Management assets for migration, log in using an Admin account. For more information on Migrating old Correspondence Management assets, see [Migrate Correspondence Management assets to AEM 6.1 forms](migration-utility.md).

1. On the data dictionary, letters, or document fragments page, tap **Create &gt; File Upload** and select the .cmp file.
1. Correspondence Management displays the Import Assets dialog with the list of assets that are imported. Tap **Import**.

   After importing the assets, the following properties of the assets are updated while the other properties remain the same:

    * Author: Displays the ID of the user that imported the asset to the server
    * Modified: The time when the asset was imported to the server

   >[!NOTE]
   >
   >For you to be able to upload XDPs (as part of the cmp file or otherwise), you need to be a part of forms-power-users group. For access rights, contact the administrator. -->

## Exporter une application de workflow {#export-a-workflow-application}

Vous pouvez utiliser le gestionnaire de packages pour exporter des applications de workflow. Pour ce faire, procédez comme suit :

1. Ouvrez le gestionnaire de packages [!DNL AEM Forms]. L’URL du gestionnaire de packages est `https://[server]:[port]/crx/packmgr`.
1. Cliquez sur **[!UICONTROL Créer un package]**. La boîte de dialogue **[!UICONTROL Nouveau package]** apparaît.
1. Indiquez le nom, la version et le groupe du package. Cliquez sur **[!UICONTROL OK]**.
1. Cliquez sur **[!UICONTROL Modifier]** et ouvrez l’onglet **[!UICONTROL Filtres]**. Cliquez sur **[!UICONTROL Ajouter un filtre]**. Spécifiez le chemin d’accès de l’application de workflow. Par exemple, /etc/fd/dashboard/startpoints/homemortgage. Cliquez sur **[!UICONTROL Ajouter une règle]**.

1. Ouvrez l’onglet **[!UICONTROL Avancé]**. Sélectionnez **[!UICONTROL Fusionner]** ou **[!UICONTROL Remplacer]** dans le champ Gestion de l’ACL. Cliquez sur **[!UICONTROL Enregistrer]**.
1. Cliquez sur **[!UICONTROL Générer]** pour créer le package.

   Une fois le package créé, vous pouvez le télécharger et l’importer sur l’autre serveur. L’application de workflow apparaît sur le serveur sur lequel le package est téléchargé.

   >[!NOTE]
   >
   >Pour que l’application de processus fonctionne correctement, exportez également le formulaire adaptatif et le modèle de processus correspondants avec l’application de travail.

## Utilisez des dossiers pour organiser les formulaires adaptatifs, les PDF forms et les ressources connexes  {#folders-and-organizing-assets}

Vous pouvez utiliser des dossiers pour classer et organiser les fichiers. L’organisation des documents et des ressources dans un dossier vous permet de regrouper les fichiers pour une gestion simplifiée. Vous pouvez sélectionner un fichier et choisir de le télécharger ou de le supprimer. Pour créer un dossier, procédez comme suit :

### Créer un dossier {#create-a-folder}

1. Connectez-vous à l’instance [!DNL AEM Forms].
1. Cliquez sur Experience Manager icône ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > navigation icône ![compass](assets/Smock_Compass_18_N.svg) > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.
1. Appuyez sur **[!UICONTROL Créer]** > **[!UICONTROL Dossier]**.
1. Saisissez les informations suivantes :

   * **[!UICONTROL Titre]** : nom d’affichage du dossier
   * **[!UICONTROL Nom]** : *(Obligatoire)* nom du nœud sous lequel vous souhaitez stocker le dossier dans le référentiel

   >[!NOTE]
   >
   >Par défaut, la valeur du champ Nom est automatiquement renseignée à partir du titre. Le nom ne peut contenir que des caractères alphanumériques ou des tirets (-) et des traits de soulignement (_). Tous les autres caractères spéciaux saisis dans le titre sont automatiquement remplacés par un trait d’union. Vous êtes invité à confirmer le nouveau nom. Vous pouvez choisir de conserver le nom proposé ou de le modifier.

1. Un nouveau dossier avec le titre que vous avez défini s’affiche à l’emplacement spécifié dans la liste des ressources.

   Si un dossier portant le même nom que celui spécifié existe déjà, l’envoi échoue avec une erreur. Vous pouvez afficher le message d’erreur en pointant sur l’icône d’erreur ![aem6forms_error_alert](assets/Smock_Alert_18_N.svg) qui s’affiche en regard du champ Nom.

   Vous pouvez appuyer sur le dossier nouvellement créé pour accéder au dossier et créer des ressources ou des dossiers dans le dossier. De plus, vous pouvez sélectionner un dossier et choisir de le mettre en file d’attente pour le télécharger, le supprimer ou modifier son nom.


<!-- ### Create copies of one or more assets or letters {#create-copies-of-one-or-more-assets-or-letters}

You can use an existing assets to quickly create an asset with similar properties, content, and inherited assets.

Complete the following steps to create copies of assets and letters:

1. On the relevant assets page, select one or more assets. The UI displays the Copy icon.
1. Tap **[!UICONTROL Copy]**. The UI displays the **[!UICONTROL Paste]** icon. You can also choose to go/navigate inside a folder before you paste. Different folders can contain assets with same names. For more information on folders, see [Folders and organizing assets](#folders-and-organizing-assets).
1. Tap **[!UICONTROL Paste]**. The **[!UICONTROL Paste]** dialog appears. The system auto generates names and titles to the new copies of assets/letters, but you can edit the titles and names of the assets/letters.

   If you are copying and pasting the assets/letters at the same place, a suffix "-CopyXX" gets added to the existing name of the asset/letter. If no title existed for the copied asset/letter, the auto generated title field remains blank.

1. If required, edit the Title and Name with which you want to save the copy of the asset/letter.
1. Tap **[!UICONTROL Paste]**. New copies of the copied assets are created.

## Search {#search-forms}

You ca use the top bar **[A]** to search your content. When you search for assets, a side panel is displayed. You can also tap ![assets-browser-content-only](assets/assets-browser-content-only.png) &gt; Filter **[B]** to invoke the side panel. Using the various filters in the side panel, you can narrow down your search. The side panel also lets you save your searches.

![search_topbar](assets/search_topbar.png)

**A.** Search **B.** Filter

![Side panel - Filters](assets/search_sidepanel.png)

Side panel - Filters

On the side panel, you can use the following to narrow down your search results:

* Search Directory
* Tags
* Search Criteria; for example, Modified Dates, Publish Status, LiveCopy Status.

The side panel also lets you save your search settings with names of your choice.

For more information and instructions on using search, filters, saved search, and side panel, see [Search](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html). -->
