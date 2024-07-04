---
title: Comment importer, exporter et organiser des PDF forms ou des Forms adaptatifs sur une instance AEM Forms ?
description: Découvrez comment migrer les PDF forms, les thèmes et autres ressources adaptatives de Forms vers et depuis une instance d’AEM.
topic-tags: forms-manager
role: Admin, User
feature: Adaptive Forms
exl-id: f5105fb7-b8c0-4656-8095-b21d392746c0
source-git-commit: 6f547bd743932d45e45e0a3c47ff5eb2129cb664
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 47%

---



| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/manage-administer-aem-forms/import-export-forms-templates) |
| AEM as a Cloud Service | Cet article |

# Importation ou exportation d’actifs Forms adaptatifs et AEM Forms {#importing-and-exporting-assets-to-aem-forms}

Vous pouvez déplacer le Forms adaptatif et les ressources connexes telles que les thèmes de formulaire adaptatif, le modèle de données de formulaire (FDM), les modèles de formulaire adaptatif, les fragments et les PDF forms entre [!DNL AEM Forms] instances.

## Téléchargement d’Forms adaptatif, de PDF forms ou de ressources connexes {#download-forms-amp-documents-assets}

Pour télécharger des formulaires ou des ressources connexes :

1. Connectez-vous à l’instance [!DNL Experience Manager Forms].
1. Sélectionnez **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.

   ![Sélectionner Forms](/help/forms/assets/select-forms.png)

1. Sélectionnez les ressources, puis cliquez sur le bouton **[!UICONTROL Télécharger]** à partir du rail supérieur.

   ![Télécharger Forms](/help/forms/assets/download-form.png)

   Lorsque vous téléchargez le formulaire, la variable **[!UICONTROL Télécharger les ressources]** s’affiche.

   ![Téléchargement de ressources de formulaires](/help/forms/assets/download-form-assets.png)

1. Cliquez sur **[!UICONTROL Télécharger]**.

Les ressources sélectionnées sont téléchargées sous forme d’archive (fichier .zip).

## Chargement de ressources adaptatives Forms, de PDF forms ou connexes {#upload-forms-amp-documents-assets}

Vous pouvez charger les types de ressource pris en charge individuellement ou sous la forme d’une archive ZIP. Pour un fichier ZIP, les chemins d’accès relatifs de toutes les ressources prises en charge s’affichent. Les ressources non prises en charge dans le fichier ZIP sont ignorées et ne sont pas répertoriées. Cependant, si l’archive ZIP contient uniquement des éléments non pris en charge, un message d’erreur s’affiche à la place de la boîte de dialogue pop-up.
Pour charger un formulaire ou une ressource connexe :

1. Connectez-vous à l’instance [!DNL Experience Manager Forms].
1. Sélectionnez **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.

   ![Sélectionner Forms](/help/forms/assets/select-forms.png)

1. Sélectionnez **[!UICONTROL Créer]** > **[!UICONTROL Charger un fichier]**. Une boîte de dialogue s’affiche.

   ![Chargement de Forms](/help/forms/assets/form-upload.png)

1. Dans la boîte de dialogue, recherchez et sélectionnez le package ou l’archive à importer. Vous pouvez également sélectionner d’autres types de fichiers pris en charge. Sélectionnez **[!UICONTROL Ouvrir]**. Le nom de dossier ou de fichier que vous sélectionnez ne doit pas contenir de caractères spéciaux.

   Dans la boîte de dialogue, vérifiez les détails des ressources à charger, puis sélectionnez **[!UICONTROL Charger]**.

   Si vous chargez une ressource de formulaires existants, la ressource est mise à jour.

   >[!NOTE]
   >
   > Lorsqu’un nom entre en conflit avec différents types de ressources, le chargement d’un package ne remplace pas la hiérarchie de dossiers existante. Par exemple, si vous disposez d’un formulaire adaptatif nommé &quot;Formation&quot; à l’emplacement `/content/dam/formsanddocuments` sur un serveur. Vous pouvez télécharger le formulaire adaptatif et le télécharger sur un autre serveur. Le deuxième serveur comporte également un dossier nommé &quot;Entraînement&quot; au même emplacement. `/content/dam/formsanddocuments`. Le chargement échoue.

## Télécharger un thème

Vous pouvez exporter des thèmes dans [!DNL AEM Forms] que vous pouvez utiliser dans d’autres projets ou instances. AEM permet de télécharger des thèmes sous la forme d&#39;un fichier zip, que vous pouvez télécharger sur l&#39;instance.
Pour télécharger un thème :

1. Connectez-vous à [!DNL Experience Manager Forms] Instance de création.
1. Sélectionner **[!UICONTROL Forms]** > **[!UICONTROL Thèmes]**.

   ![Sélectionner un thème](/help/forms/assets/select-theme.png)

1. Sur la page Thèmes, sélectionnez le thème et cliquez sur le bouton **[!UICONTROL Télécharger]** à partir du rail supérieur.

   ![Télécharger le thème](/help/forms/assets/download-theme.png)

   Lorsque vous téléchargez le thème, la variable **[!UICONTROL Télécharger les ressources]** s’affiche.

   ![Téléchargement de ressources de thème](/help/forms/assets/download-theme-asset.png)

1. Cliquez sur **[!UICONTROL Télécharger]**.

Les ressources sélectionnées sont téléchargées sous forme d’archive (fichier .zip).

## Charger un thème {#uploading-a-theme}

Vous pouvez télécharger et utiliser des thèmes que d’autres créent dans vos formulaires.
Pour charger un thème :

1. Connectez-vous à l’instance [!DNL Experience Manager Forms].
1. Dans Experience Manager, accédez à **[!UICONTROL Formulaires]** > **[!UICONTROL Thèmes]**.

   ![Sélectionner un thème](/help/forms/assets/select-theme.png)

1. Sur la page Thèmes, cliquez sur **[!UICONTROL Créer]** > **[!UICONTROL Chargement de fichier]**.

   ![Télécharger le thème](/help/forms/assets/theme-upload.png)

1. Recherchez et sélectionnez un module de thème sur votre ordinateur, puis cliquez sur **[!UICONTROL Télécharger]**. Le thème chargé devient disponible sur la page Thèmes.

## Utilisez des dossiers pour organiser les formulaires adaptatifs, les PDF forms et les ressources connexes  {#folders-and-organizing-assets}

Vous pouvez utiliser des dossiers pour classer et organiser les fichiers. L’organisation des documents et des ressources dans un dossier vous permet de regrouper les fichiers pour une gestion simplifiée. Vous pouvez sélectionner un fichier et choisir de le télécharger ou de le supprimer.

### Créer un dossier {#create-a-folder}

Pour créer un dossier :

1. Connectez-vous à l’instance [!DNL Experience Manager Forms].
1. Sélectionnez **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.

   ![Sélectionner le formulaire](/help/forms/assets/select-forms.png)

1. Sélectionner **[!UICONTROL Créer]** > **[!UICONTROL Dossier]**.

   ![Créer un dossier](/help/forms/assets/create-folder.png)

   La variable **[!UICONTROL Ajouter un dossier]** s’affiche.
1. Saisissez le **[!UICONTROL Titre]**. La variable **[!UICONTROL Nom]** renseigne automatiquement lorsque vous tapez le **[!UICONTROL Titre]**.

   ![Ajouter un dossier](/help/forms/assets/add-folder.png)

1. Cliquez sur **[!UICONTROL Créer]**.

   >[!NOTE]
   >
   >Par défaut, la valeur du champ Nom est automatiquement renseignée à partir du titre. Le nom ne peut contenir que des caractères alphanumériques ou des tirets (-) et des traits de soulignement (_). Tous les autres caractères spéciaux saisis dans le titre sont automatiquement remplacés par un trait d’union. Il vous est demandé de confirmer le nouveau nom. Vous pouvez choisir de conserver le nom proposé ou de le modifier.

Un nouveau dossier avec le titre que vous avez défini s’affiche à l’emplacement spécifié dans la liste des ressources.

Si un dossier portant le même nom que celui spécifié existe déjà, l’envoi échoue avec une erreur. Vous pouvez afficher le message d’erreur en pointant sur l’icône d’erreur ![aem6forms_error_alert](assets/Smock_Alert_18_N.svg) qui s’affiche en regard du champ Nom.

Vous pouvez sélectionner le dossier créé pour y accéder et y créer des ressources ou des dossiers. De plus, vous pouvez sélectionner un dossier et choisir de le mettre en file d’attente pour le télécharger, le supprimer ou modifier son nom.

### Création de copies d’une ou de plusieurs ressources {#create-copies-of-one-or-more-assets-or-letters}

Vous pouvez utiliser des ressources existantes pour créer rapidement une ressource avec des propriétés, du contenu et des ressources héritées similaires.

Pour créer des copies de ressources :

1. Connectez-vous à l’instance [!DNL Experience Manager Forms].
1. Sur la page Ressources appropriées, sélectionnez une ou plusieurs ressources. L’interface utilisateur affiche la variable **[!UICONTROL Copier]** Icône
1. Sélectionner **[!UICONTROL Copier]**. L’interface utilisateur affiche la variable ![Icône Coller](/help/forms/assets/Smock_Paste_18_N.svg) Icône

   ![Copie d’une ressource](/help/forms/assets/copy-asset.png)

   Vous pouvez également choisir d’accéder à un dossier avant de le coller. Différents dossiers peuvent contenir des ressources portant le même nom. Pour plus d’informations sur les dossiers, voir [Dossiers et organisation des actifs](#folders-and-organizing-assets).
1. Sélectionner **[!UICONTROL Coller]**.

   ![Coller la ressource](/help/forms/assets/paste-asset.png)

1. La variable **[!UICONTROL Coller]** s’affiche. Le système génère automatiquement des noms et des titres aux nouvelles copies des ressources, mais vous pouvez modifier les titres et les noms des ressources.

   Si vous copiez et collez les ressources au même endroit, un suffixe &quot;-CopyXX&quot; est ajouté au nom existant de la variable `asset`. Si aucun titre n’existait pour la ressource copiée, le champ de titre généré automatiquement reste vide.

   ![Coller la ressource à un nouvel emplacement](/help/forms/assets/paste-click-asset.png)

   Si nécessaire, modifiez la variable **[!UICONTROL Titre]** avec lequel vous souhaitez enregistrer la copie de la ressource. La variable **[!UICONTROL Nom]** renseigne automatiquement lorsque vous tapez le **[!UICONTROL Titre]**.
1. Sélectionner **[!UICONTROL Coller]**. De nouvelles copies des ressources copiées sont créées.

## Rechercher {#search-forms}

Lorsque vous disposez d’un grand nombre de ressources, la recherche de la ressource appropriée prend du temps. Vous pouvez effectuer une recherche textuelle pour une ressource spécifique sur la page de la ressource.

Pour rechercher la ressource :

1. Connectez-vous à l’instance [!DNL Experience Manager Forms].
1. Cliquez sur le bouton ![icône de recherche](assets/folder-search-icon.svg) icône de recherche.

   ![Formulaire de recherche](/help/forms/assets/search-form.png)

1. Saisissez le nom de la ressource que vous souhaitez rechercher dans la barre de recherche.

1. Une liste des ressources associées s’affiche. Sélectionnez la ressource souhaitée dans la liste des ressources affichées.

   ![Recherche de ressources](/help/forms/assets/search-bar.png)

Pour plus d’informations et d’instructions sur l’utilisation de la recherche, voir [Rechercher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=fr).

<!--
## Export or create a package {#export-a-workflow-application}

You can use packages to install new content, install new functionality, transfer content between instances, and back up content.
To export or create a package:

1. Log in to your [!DNL Experience Manager Forms] instance.
1. Navigate to **[!UICONTROL Tools]** ![hammer](assets/hammer.png) &gt; **[!UICONTROL Deployment]** &gt; **[!UICONTROL Packages]**.

   ![Package Manager](/help/forms/assets/package-manager.png)

1. Click **[!UICONTROL Create Package]**.

   ![Create package](/help/forms/assets/create-package.png)   
   
   When **[!UICONTROL Create Package]** is clicked, the **[!UICONTROL New Package]** dialog box appears.
1. Specify the package name, version, and group for the package. 
   
   ![New package](/help/forms/assets/new-package.png)  

   * **Package Name** - Select a descriptive name to help you identify the contents of the package.

   * **Version** - It is a textual field to indicate a version. This is appended to the package name to form the name of the zip file.

   * **Group** - This is the target group (or folder) name. Groups help you organize your packages. A folder is created for the group if it does not already exist. If you leave the group name blank, it creates the package in the main package list.

1. Click **[!UICONTROL OK]**.

   Once the package is created, it appears at the top of the list of packages.

1. Click **[!UICONTROL Edit]**.
   
   ![Edit Package](/help/forms/assets/edit-package.png)
    
1. Open the **[!UICONTROL Filters]** tab.
   
   ![Open filter tab](/help/forms/assets/add-filter-package.png)
   
1.  Click **[!UICONTROL Add Filter]**. 
   
      ![Add filter](/help/forms/assets/add-filter.png)

      You can specify the path of the package. You can also add rules and other validations for the package.

      ![Add path](/help/forms/assets/add-path.png)

1. Click **[!UICONTROL Save]** after you are finished editing the settings.
1. Click **[!UICONTROL Build]** to create the package.
    
     ![Build path](/help/forms/assets/build-package.png)

   After the package is built, you can download the package and import it to the other server. The workflow application appears on the server where the package is uploaded.

   >[!NOTE]
   >
   >For the workflow application to work properly, also export the corresponding Adaptive Form and workflow model with the work application.

   Once a package is uploaded to AEM, you can modify its settings. You can also download or delete the package.

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

<!-- ### Import Document Fragments, Letters and/or Data Dictionaries into Correspondence Management {#import-document-fragments-letters-and-or-data-dictionaries-into-correspondence-management}

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
   >For you to be able to upload XDPs (as part of the cmp file or otherwise), you need to be a part of forms-power-users group. For access rights, contact the administrator. -->

## Voir également {#see-also}

{{see-also}}
