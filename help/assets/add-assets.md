---
title: Add your digital assets to [!DNL Adobe Experience Manager].
description: Add your digital assets to [!DNL Adobe Experience Manager] as a Cloud Service.
translation-type: tm+mt
source-git-commit: 3e9697d27337b39f5667cc94930de6ea7f0b68c5
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 76%

---


# Ajout de ressources numériques à Adobe Experience Manager {#add-assets-to-experience-manager}

[!DNL Adobe Experience Manager] enrichit le contenu binaire des fichiers numériques chargés avec des métadonnées enrichies, des balises intelligentes, des rendus et autres services de gestion des ressources numériques (DAM). Vous pouvez charger divers types de fichiers, tels que des images, des documents et des fichiers d’images brutes, depuis votre dossier local ou un lecteur réseau vers [!DNL Experience Manager Assets].

Plusieurs méthodes de chargement sont fournies. Outre le téléchargement de navigateur le plus souvent utilisé, il existe d’autres méthodes d’ajout d’actifs au référentiel de Experience Manager, notamment des clients de bureau, tels que Adobe Asset Link ou l’application de bureau Experience Manager, le téléchargement et l’assimilation de scripts que les clients créeraient et des intégrations d’assimilation automatisées ajoutées en tant qu’extensions Experience Manager.

Dans ce chapitre, nous nous focaliserons sur les méthodes de chargements destinées aux utilisateurs finaux. Nous vous proposerons également des liens vers des articles décrivant les aspects techniques du chargement et de l’ingestion de ressources à l’aide des kits SDK et des API d’Experience Manager.

Experience Manager vous permet de charger et de gérer n’importe quel fichier binaire. Cependant, les formats de fichiers les plus courants prennent en charge des services supplémentaires, tels que l’extraction de métadonnées ou la génération d’aperçus et de rendus. Pour plus d’informations, reportez-vous aux [formats de fichiers pris en charge](file-format-support.md).

Vous pouvez également choisir d’effectuer un traitement supplémentaire sur les fichiers chargés. Plusieurs profils de traitement de ressources peuvent être configurés sur le dossier dans lequel les ressources sont chargées, afin d’ajouter des services de traitement des images, des rendus ou des métadonnées spécifiques. Pour plus d’informations, voir [Traitement supplémentaire](#additional-processing) ci-dessous.

>[!NOTE]
>
>Avec Experience Manager as a Cloud Service, vous disposez d’une nouvelle méthode de chargement de ressources appelée chargement binaire direct. Il est pris en charge par défaut par les fonctionnalités de produit prêtes à l’emploi et les clients, tels que l’interface utilisateur du Experience Manager, Adobe Asset Link, l’application de bureau du Experience Manager, et donc transparent pour les utilisateurs finaux.
>
>Le code de chargement personnalisé ou étendu par les équipes techniques des clients doit utiliser les nouvelles API et les nouveaux protocoles de chargement.

## Chargement des ressources {#upload-assets}

Pour télécharger un fichier (ou plusieurs fichiers), vous pouvez les sélectionner sur votre bureau et faire glisser sur l’interface utilisateur (navigateur Web) le dossier de destination. Vous pouvez également lancer le chargement à partir de l’interface utilisateur.

1. In the [!DNL Assets] user interface, navigate to the location where you want to add digital assets.
1. Pour charger les ressources, effectuez l’une des opérations suivantes :

   * Appuyez sur l’icône **[!UICONTROL Créer]** de la barre d’outils. Ensuite, dans le menu, appuyez sur **[!UICONTROL Fichiers]**. Au besoin, vous pouvez renommer le fichier dans la boîte de dialogue affichée.
   * In a browser that supports HTML5, drag the assets directly on the [!DNL Assets] user interface. La boîte de dialogue permettant de renommer les fichiers n’est pas affichée.

   ![create_menu](assets/create_menu.png)

   Pour sélectionner plusieurs fichiers, appuyez sur la touche Ctrl ou Commande et sélectionnez les ressources dans la boîte de dialogue de sélecteur de fichiers. Si vous utilisez un iPad, vous ne pouvez sélectionner qu’un seul fichier à la fois.

<!-- #ENGCHECK do we support pausing? I couldn't get pause to show with 1.5GB upload.... If not, this should be removed#

   You can pause the uploading of large assets (greater than 500 MB) and resume it later from the same page. Tap the **[!UICONTROL Pause]** icon beside progress bar that appears when an upload starts.

   ![chlimage_1-211](assets/chlimage_1-211.png)

   The size above which an asset is considered a large asset is configurable. For example, you can configure the system to consider assets above 1000 MB (instead of 500 MB) as large assets. In this case, **[!UICONTROL Pause]** appears on the progress bar when assets of size greater than 1000 MB are uploaded.

   The Pause button does not show if a file greater than 1000 MB is uploaded with a file less than 1000 MB. However, if you cancel the less than 1000 MB file upload, the **[!UICONTROL Pause]** button appears.

   To modify the size limit, configure the `chunkUploadMinFileSize` property of the `fileupload`node in the CRX repository.

   When you click the **[!UICONTROL Pause]** icon, it toggles to a **[!UICONTROL Play]** icon. To resume uploading, click the **[!UICONTROL Play]** icon.

   ![chlimage_1-212](assets/chlimage_1-212.png)
-->

1. Pour annuler une opération de chargement en cours, cliquez sur le bouton de fermeture (`X`) en regard de la barre de progression. When you cancel the upload operation, [!DNL Assets] deletes the partially uploaded portion of the asset.

   If you cancel the upload operation before the files are uploaded, [!DNL Assets] stops uploading the current file and refreshes the content. Toutefois, les fichiers déjà téléchargés ne sont pas supprimés.

<!-- #ENGCHECK do we support pausing? I couldn't get pause to show with 1.5GB upload.... If not, this should be removed#
   The ability to resume uploading is especially helpful in low-bandwidth scenarios and network glitches, where it takes a long time to upload a large asset. You can pause the upload operation and continue later when the situation improves. When you resume, uploading starts from the point where you paused it.
-->

<!-- #ENGCHECK assuming this is not relevant? remove after confirming#
   During the upload operation, [!DNL Experience Manager] saves the portions of the asset being uploaded as chunks of data in the CRX repository. When the upload completes, [!DNL Experience Manager] consolidates these chunks into a single block of data in the repository.

   To configure the cleanup task for the unfinished chunk upload jobs, go to `https://[aem_server]:[port]/system/console/configMgr/org.apache.sling.servlets.post.impl.helper.ChunkCleanUpTask`.
-->

1. The upload progress dialog in [!DNL Assets] displays the count of successfully uploaded files and the files that failed to upload.

De plus, l’interface utilisateur d’Assets affiche la ressource la plus récente que vous avez chargée ou le dossier que vous avez créé en premier.

>[!NOTE]
>
>To upload nested folder hierarchies to AEM, see [bulk upload assets](#bulk-upload).

<!-- #ENGCHECK I'm assuming this is no longer relevant.... If yes, this should be removed#

### Serial uploads {#serialuploads}

Uploading numerous assets in bulk consumes significant I/O resources, which may adversely impact the performance of [!DNL Assets]. In particular, if you have a slow internet connection, the time to upload drastically increases due to a spike in disk I/O. Moreover, your web browser may introduce additional restrictions to the number of POST requests [!DNL Assets] can handle for concurrent asset uploads. As a result, the upload operation fails or terminate prematurely. In other words, [!DNL Assets] may miss some files while ingesting a bunch of files or altogether fail to ingest any file.

To overcome this situation, [!DNL Assets] ingests one asset at a time (serial upload) during a bulk upload operation, instead of the concurrently ingesting all the assets.

Serial uploading of assets is enabled by default. To disable the feature and allow concurrent uploading, overlay the `fileupload` node in Crx-de and set the value of the `parallelUploads` property to `true`.

### Streamed uploads {#streamed-uploads}

If you upload many assets to [!DNL Experience Manager], the I/O requests to server increase drastically, which reduces the upload efficiency and can even cause some upload task to time out. [!DNL Assets] supports streamed uploading of assets. Streamed uploading reduces the disk I/O during the upload operation by avoiding asset storage in a temporary folder on the server before copying it to the repository. Instead, the data is transferred directly to the repository. This way, the time to upload large assets and the possibility of timeouts is reduced. Streamed upload is enabled by default in [!DNL Assets].

>[!NOTE]
>
>Streaming upload is disabled for [!DNL Experience Manager] running on JEE server with servlet-api version lower than 3.1.
-->

### Gestion des chargements lorsque des ressources existent déjà {#handling-upload-existing-file}

Si vous transférez une ressource portant le même nom qu’une ressource déjà disponible à l’emplacement où vous transférez la ressource, un message d’avertissement s’affiche.

Vous pouvez choisir de remplacer une ressource existante, de créer une autre version ou de garder les deux en renommant la nouvelle ressource téléchargée. Si vous remplacez une ressource existante, les métadonnées de la ressource et les modifications antérieures (annotations, recadrage, etc.) apportées à une ressource existante sont supprimées. Si vous choisissez de conserver les deux ressources, la nouvelle ressource est renommée en ajoutant le chiffre `1` à son nom.

>[!NOTE]
>
>Lorsque vous sélectionnez **[!UICONTROL Remplacer]** dans la boîte de dialogue [!UICONTROL Conflit de noms], l’ID de la ressource est régénéré pour la nouvelle ressource. Cet ID est différent de celui de la ressource précédente.
>
>Si la fonction Statistiques sur les ressources est activée pour effectuer le suivi des impressions/clics avec Adobe Analytics, l’ID de ressource régénéré invalide les données capturées pour la ressource dans Analytics.

Pour conserver la ressource de duplicata dans [!DNL Assets], cliquez sur **[!UICONTROL Conserver]**. Pour supprimer la ressource en double que vous avez chargée, appuyez/cliquez sur **[!UICONTROL Supprimer]**.

### Gestion des noms de fichier et caractères interdits {#filename-handling}

[!DNL Experience Manager Assets] vous empêche de charger des ressources dont le nom de fichier contient des caractères interdits. If you try to upload an asset with file name containing a disallowed character or more, [!DNL Assets] displays a warning message and stops the upload until you remove these characters or upload with an allowed name.

Pour prendre en compte les conventions d’appellation en vigueur dans votre entreprise, la boîte de dialogue [!UICONTROL Charger les ressources] vous permet de spécifier des noms longs pour les fichiers chargés.

Toutefois, la liste de caractères suivante, séparée par des espaces, n’est pas prise en charge :

* Le nom du fichier de ressource ne doit pas contenir `* / : [ \\ ] | # % { } ? &`
* Le nom du dossier de ressources ne doit pas contenir `* / : [ \\ ] | # % { } ? \" . ^ ; + & \t`

## Chargement en masse de ressources {#bulk-upload}

Pour charger un plus grand nombre de fichiers, en particulier s’ils existent dans une hiérarchie de dossiers imbriqués sur le disque, vous pouvez utiliser les méthodes suivantes :

* Utilisez un script ou un outil de chargement personnalisé qui exploite des [API de chargement de ressources](developer-reference-material-apis.md#asset-upload-technical). Un tel outil personnalisé peut donner lieu à un traitement supplémentaire des ressources (comme la traduction des métadonnées ou l’affectation de nouveaux noms aux fichiers).
* Utilisez l’[application de bureau Experience Manager](https://docs.adobe.com/content/help/fr-FR/experience-manager-desktop-app/using/using.html) pour charger des hiérarchies de dossiers imbriqués.

>[!NOTE]
>
>Pour effectuer un téléchargement massif dans le cadre de la migration de contenu à partir d’autres systèmes lors de la configuration et du déploiement vers Experience Manager, la planification et le choix des outils doivent faire l’objet d’une attention particulière. Consultez le [guide de déploiement](/help/implementing/deploying/overview.md) pour en savoir plus sur les méthodes de migration de contenu.

## Chargement de ressources à l’aide de clients pour ordinateur de bureau {#upload-assets-desktop-clients}

Outre l’interface utilisateur du navigateur web, Experience Manager prend en charge d’autres clients pour ordinateur de bureau. Ils permettent également de télécharger du contenu sans devoir passer par le navigateur web.

* [Adobe Asset Link](https://helpx.adobe.com/fr/enterprise/using/adobe-asset-link.html) permet d’accéder aux ressources provenant [!DNL Experience Manager] des applications de bureau Adobe Photoshop, Adobe Illustrator et Adobe InDesign. You can upload the currently open document into [!DNL Experience Manager] directly from Adobe Asset Link user interface from within these desktop applications.
* L’[application de bureau Experience Manager](https://docs.adobe.com/content/help/fr-FR/experience-manager-desktop-app/using/using.html) simplifie l’utilisation des ressources sur l’ordinateur, indépendamment du type de fichier ou de l’application native affectée à leur gestion. Il est particulièrement utile de charger des fichiers dans des hiérarchies de dossiers imbriqués à partir de votre système de fichiers local, car le téléchargement à l’aide du navigateur ne prend en charge que les listes de fichiers plats.

## Traitement supplémentaire {#additional-processing}

Pour qu’un traitement supplémentaire soit réalisé sur les ressources chargées, vous pouvez utiliser des profils de traitement des ressources sur le dossier de chargement. Ils sont disponibles dans la boîte de dialogue **[!UICONTROL Propriétés]** du dossier.

![assets-folder-properties](assets/assets-folder-properties.png)

Les profils suivants sont disponibles :

* Les [profils de métadonnées](metadata-profiles.md) vous permettent d’appliquer des propriétés de métadonnées par défaut aux ressources chargées dans ce dossier.
* [Les profils](asset-microservices-configure-and-use.md) de traitement vous permettent de générer plus de rendus que ce qui est possible par défaut.

De plus, si Dynamic Media est activé dans votre environnement :

* Les [profils d’image Dynamic Media](dynamic-media/image-profiles.md) vous permettent d’appliquer un recadrage spécifique (**[!UICONTROL Recadrage intelligent]** et recadrage de pixels) et une configuration d’accentuation aux ressources chargées.
* Les [profils vidéo Dynamic Media](dynamic-media/video-profiles.md) vous permettent d’appliquer des profils de codage vidéo spécifiques (résolution, format, paramètres).

>[!NOTE]
>
>Le recadrage Dynamic Media et les autres opérations effectuées sur les ressources ne sont pas destructifs. En d’autres termes, ce type d’opération ne modifie pas l’élément original chargé, mais fournit des paramètres de recadrage ou de transformation des médias à effectuer lors de la diffusion des ressources.

Pour les dossiers auxquels un profil de traitement est affecté, le nom du profil s’affiche sur la vignette en mode Carte. En mode Liste, le nom du profil s’affiche dans la colonne **[!UICONTROL Profil de traitement.]**

## Chargement ou ingestion de fichiers à l’aide d’API {#upload-using-apis}

Les détails techniques du protocole et des API de chargement, ainsi que les liens vers les exemples de clients et le kit SDK Open Source, sont fournis dans la section [Chargement de ressources](developer-reference-material-apis.md#asset-upload-technical) de la documentation de référence du développeur.

>[!MORELIKETHIS]
>
>* [Application de bureau Adobe Experience Manager](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/introduction.html)
>* [Adobe Asset Link](https://www.adobe.com/creativecloud/business/enterprise/adobe-asset-link.html)
>* [Documentation d’Adobe Asset Link](https://helpx.adobe.com/fr/enterprise/using/adobe-asset-link.html)
>* [Référence technique pour le chargement de ressources](developer-reference-material-apis.md#asset-upload-technical)

