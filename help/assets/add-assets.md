---
title: Ajout de vos ressources numériques à [!DNL Adobe Experience Manager].
description: Ajoutez vos ressources numériques à  [!DNL Adobe Experience Manager] en tant que  [!DNL Cloud Service].
translation-type: tm+mt
source-git-commit: 5be8ab734306ad1442804b3f030a56be1d3b5dfa
workflow-type: tm+mt
source-wordcount: '1972'
ht-degree: 47%

---


# Ajout de ressources numériques à Adobe Experience Manager {#add-assets-to-experience-manager}

[!DNL Adobe Experience Manager] enrichit le contenu binaire des fichiers numériques chargés avec des métadonnées enrichies, des balises intelligentes, des rendus et autres services de gestion des ressources numériques (DAM). Vous pouvez charger divers types de fichiers, tels que des images, des documents et des fichiers d’images brutes, depuis votre dossier local ou un lecteur réseau vers [!DNL Experience Manager Assets].

Plusieurs méthodes de chargement sont proposées. Outre la méthode la plus courante qui consiste à utiliser le navigateur, il existe d’autres méthodes pour ajouter des ressources au référentiel Experience Manager : clients de bureau, comme Adobe Asset Link ou l’application de bureau Experience Manager, scripts de chargement et d’ingestion créés par les clients, ou encore intégrations d’ingestion automatisées ajoutées sous la forme d’extensions Experience Manager.

Dans ce chapitre, nous nous focaliserons sur les méthodes de chargements destinées aux utilisateurs finaux. Nous vous proposerons également des liens vers des articles décrivant les aspects techniques du chargement et de l’ingestion de ressources à l’aide des kits SDK et des API d’Experience Manager.

Experience Manager vous permet de charger et de gérer n’importe quel fichier binaire. Cependant, les formats de fichiers les plus courants prennent en charge des services supplémentaires, tels que l’extraction de métadonnées ou la génération d’aperçus et de rendus. Pour plus d’informations, reportez-vous aux [formats de fichiers pris en charge](file-format-support.md).

Vous pouvez également choisir d’effectuer un traitement supplémentaire sur les fichiers chargés. Plusieurs profils de traitement de ressources peuvent être configurés sur le dossier dans lequel les ressources sont chargées, afin d’ajouter des services de traitement des images, des rendus ou des métadonnées spécifiques. Voir [traiter les ressources lors du transfert](#process-when-uploaded).

>[!NOTE]
>
>Experience Manager en tant que [!DNL Cloud Service] utilise une nouvelle méthode de transfert de ressources : le transfert binaire direct. Cette méthode est prise en charge par défaut par les clients et fonctionnalités standard du produit, comme l’interface utilisateur Experience Manager, Adobe Asset Link et l’application de bureau Experience Manager. Elle est donc transparente pour les utilisateurs finaux.
>
>Le code de chargement personnalisé ou étendu par les équipes techniques des clients doit utiliser les nouvelles API et les nouveaux protocoles de chargement.

Assets as a [!DNL Cloud Service] fournit les méthodes de téléchargement suivantes. Adobe vous conseille de comprendre votre cas d’utilisation et l’applicabilité d’une option de téléchargement avant de l’utiliser.

| Méthode de téléchargement | Quand utiliser la personnalisation? | Principal Persona |
|---------------------|----------------|-----------------|
| [Interface utilisateur de la console Ressources](#upload-assets) | Téléchargement occasionnel, facilité de pression et de glisser, téléchargement de recherche. N’utilisez pas pour télécharger un grand nombre de fichiers. | Tous les utilisateurs |
| [API de téléchargement](#upload-using-apis) | Pour les décisions dynamiques lors du transfert. | Développeur |
| [[!DNL Experience Manager] application de bureau](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) | Importation de ressources en faible volume, mais pour la migration. | Administrateur, Marketer |
| [Adobe Asset Link](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html) | Utile lorsque les créatifs et les marketeurs travaillent sur des ressources à partir des applications de bureau [!DNL Creative Cloud] prises en charge. | Créatif, spécialiste du marketing |
| [Intégrateur en masse de ressources](#asset-bulk-ingestor) | Recommandé pour les migrations à grande échelle et les ingestions occasionnelles en vrac. Uniquement pour les banques de données prises en charge. | Administrateur, développeur |

## Chargement des ressources {#upload-assets}

<!-- #ENGCHECK do we support pausing? I couldn't get pause to show with 1.5GB upload.... If not, this should be removed#

   You can pause the uploading of large assets (greater than 500 MB) and resume it later from the same page. Tap the **[!UICONTROL Pause]** icon beside progress bar that appears when an upload starts.

   ![chlimage_1-211](assets/chlimage_1-211.png)

   The size above which an asset is considered a large asset is configurable. For example, you can configure the system to consider assets above 1000 MB (instead of 500 MB) as large assets. In this case, **[!UICONTROL Pause]** appears on the progress bar when assets of size greater than 1000 MB are uploaded.

   The Pause button does not show if a file greater than 1000 MB is uploaded with a file less than 1000 MB. However, if you cancel the less than 1000 MB file upload, the **[!UICONTROL Pause]** button appears.

   To modify the size limit, configure the `chunkUploadMinFileSize` property of the `fileupload`node in the CRX repository.

   When you click the **[!UICONTROL Pause]** icon, it toggles to a **[!UICONTROL Play]** icon. To resume uploading, click the **[!UICONTROL Play]** icon.

   ![chlimage_1-212](assets/chlimage_1-212.png)
-->

<!-- #ENGCHECK do we support pausing? I couldn't get pause to show with 1.5GB upload.... If not, this should be removed#
   The ability to resume uploading is especially helpful in low-bandwidth scenarios and network glitches, where it takes a long time to upload a large asset. You can pause the upload operation and continue later when the situation improves. When you resume, uploading starts from the point where you paused it.
-->

<!-- #ENGCHECK assuming this is not relevant? remove after confirming#
   During the upload operation, [!DNL Experience Manager] saves the portions of the asset being uploaded as chunks of data in the CRX repository. When the upload completes, [!DNL Experience Manager] consolidates these chunks into a single block of data in the repository.

   To configure the cleanup task for the unfinished chunk upload jobs, go to `https://[aem_server]:[port]/system/console/configMgr/org.apache.sling.servlets.post.impl.helper.ChunkCleanUpTask`.
-->

Pour charger un ou plusieurs fichiers, vous pouvez les sélectionner sur votre bureau et les faire glisser vers le dossier de destination dans l’interface utilisateur (navigateur web). Vous pouvez également lancer le chargement à partir de l’interface utilisateur.

1. Dans l’interface utilisateur [!DNL Assets], accédez à l’emplacement où vous voulez ajouter des ressources numériques.
1. Pour charger les ressources, effectuez l’une des opérations suivantes :

   * Dans la barre d’outils, cliquez sur **[!UICONTROL Créer]** > **[!UICONTROL Fichiers]**. Au besoin, vous pouvez renommer le fichier dans la boîte de dialogue affichée.
   * Dans un navigateur prenant en charge HTML5, faites glisser directement les ressources dans l’interface utilisateur [!DNL Assets]. La boîte de dialogue permettant de renommer les fichiers n’est pas affichée.

   ![create_menu](assets/create_menu.png)

   Pour sélectionner plusieurs fichiers, sélectionnez la clé `Ctrl` ou `Command` et sélectionnez les actifs dans la boîte de dialogue du sélecteur de fichiers. Si vous utilisez un iPad, vous ne pouvez sélectionner qu’un seul fichier à la fois.

1. Pour annuler une opération de chargement en cours, cliquez sur le bouton de fermeture (`X`) en regard de la barre de progression. Lorsque vous annulez le chargement, [!DNL Assets] supprime la partie partiellement chargée de la ressource.
Si vous annulez une opération de téléchargement avant que les fichiers ne soient téléchargés, [!DNL Assets] arrête de télécharger le fichier actif et actualise le contenu. Toutefois, les fichiers déjà chargés ne sont pas supprimés.

1. La boîte de dialogue de progression du chargement dans [!DNL Assets] affiche le nombre de fichiers dont le chargement a réussi et ceux dont le chargement a échoué.
En outre, l’interface utilisateur [!DNL Assets] affiche la ressource la plus récente que vous téléchargez ou le dossier que vous avez créé en premier.

>[!NOTE]
>
>Pour charger des hiérarchies de dossiers imbriqués, voir [Chargement en masse de ressources](#bulk-upload).

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

Vous pouvez télécharger un fichier avec le même chemin d’accès (même nom et même emplacement) que celui d’un fichier existant. Cependant, une boîte de dialogue d’avertissement s’affiche avec les options suivantes :

* Remplacer la ressource existante : Si vous remplacez une ressource existante, les métadonnées de la ressource et les modifications antérieures (annotations, recadrage, etc.) que vous avez apportées à la ressource existante sont supprimées.
* Créez une autre version : Une nouvelle version de la ressource existante est créée dans le référentiel. Vous pouvez vue les deux versions dans le [!UICONTROL Journal] et revenir à la version précédente si nécessaire.
* Conservez les deux : Si vous choisissez de conserver les deux fichiers, le nouveau fichier est renommé avec le numéro `1` ajouté à son nom.

>[!NOTE]
>
>Lorsque vous sélectionnez **[!UICONTROL Remplacer]** dans la boîte de dialogue [!UICONTROL Conflit de noms], l’ID de la ressource est régénéré pour la nouvelle ressource. Cet ID est différent de celui de la ressource précédente.
>
>Si Asset Insights est activé pour effectuer le suivi des impressions ou des clics avec [!DNL Adobe Analytics], l’ID de ressource régénéré invalide les données capturées pour la ressource sur [!DNL Analytics].

Pour conserver le duplicata de ressource dans [!DNL Assets], cliquez sur **[!UICONTROL Conserver]**. Pour supprimer la ressource en double que vous avez chargée, appuyez/cliquez sur **[!UICONTROL Supprimer]**.

### Gestion des noms de fichier et caractères interdits {#filename-handling}

[!DNL Experience Manager Assets] essaie de vous empêcher de télécharger des fichiers dont le nom de fichier contient des caractères interdits. Si vous essayez de charger une ressource dont le nom de fichier contient un ou plusieurs caractères interdits, [!DNL Assets] affiche un message d’avertissement à ce sujet et interrompt l’opération jusqu’à ce que vous supprimiez les caractères concernés ou utilisiez un nom autorisé. Certaines méthodes de téléchargement n’empêchent pas le téléchargement de fichiers dont les noms de fichier contiennent des caractères interdits, mais les remplacent par `-`.

Pour prendre en compte les conventions d’appellation en vigueur dans votre entreprise, la boîte de dialogue [!UICONTROL Charger les ressources] vous permet de spécifier des noms longs pour les fichiers chargés. Les caractères suivants (liste de ceux-ci séparés par des espaces) ne sont pas pris en charge :

* caractères non valides pour le nom de fichier `* / : [ \\ ] | # % { } ? &`
* caractères non valides pour le nom de dossier de ressources `* / : [ \\ ] | # % { } ? \" . ^ ; + & \t`

## Chargement en masse de ressources {#bulk-upload}

L’analyseur de ressources en vrac peut gérer efficacement des milliers de ressources. Cependant, une ingestion à grande échelle n&#39;est pas simplement un vidage de fichiers volumineux ou une migration aveugle. Pour qu&#39;il s&#39;agisse d&#39;un projet significatif qui répond à vos besoins commerciaux, la planification et la gestion des actifs conduisent à une assimilation beaucoup plus efficace. Toutes les intégrations ne sont pas les mêmes et les généralisations ne peuvent pas être faites sans tenir compte de la composition nuancée du référentiel et des besoins commerciaux. Voici des suggestions globales pour planifier et exécuter une ingestion en masse :

* Traiter les ressources : Supprimez les actifs qui ne sont pas nécessaires dans le DAM. Envisagez de supprimer les actifs inutilisés, obsolètes ou de duplicata. Cela permet de réduire les données transférées et les ressources ingérées, ce qui accélère les saisies.
* Organiser les ressources : Envisagez d’organiser le contenu dans un ordre logique, par exemple par taille de fichier, format de fichier, cas d’utilisation ou priorité. En général, les fichiers complexes volumineux nécessitent un traitement plus poussé. Vous pouvez également envisager d’importer des fichiers volumineux séparément à l’aide de l’option de filtrage de la taille de fichier (décrite ci-dessous).
* Sens plus importants : Envisagez de diviser votre ingestion en plusieurs projets d&#39;ingestion en masse. Cela vous permet de voir le contenu plus tôt et de mettre à jour votre assimilation si nécessaire. Par exemple, vous pouvez ingérer des ressources à forte intensité de traitement pendant les heures creuses ou graduellement en plusieurs tranches. Cependant, vous pouvez ingérer des ressources plus petites et plus simples qui ne nécessitent pas un traitement important en une seule fois.

Pour télécharger un plus grand nombre de fichiers, utilisez l’une des méthodes suivantes. Voir aussi les [cas d’utilisation et les méthodes](#upload-methods-comparison)

* [API](developer-reference-material-apis.md#asset-upload-technical) de transfert de ressources : Utilisez un script ou un outil de téléchargement personnalisé qui utilise les API pour ajouter une gestion supplémentaire des ressources (par exemple, traduire des métadonnées ou renommer des fichiers), si nécessaire.
* [Application](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) de bureau Experience Manager : Utile pour les professionnels de la création et les marketeurs qui téléchargent des fichiers à partir de leur système de fichiers local. Utilisez-la pour télécharger les dossiers imbriqués disponibles localement.
* [Outil](#asset-bulk-ingestor) d&#39;assimilation en masse : Utilisation pour l’assimilation de grandes quantités de ressources, occasionnellement ou initialement, lors du déploiement  [!DNL Experience Manager].

### Outil d&#39;assimilation en masse de ressources {#asset-bulk-ingestor}

L&#39;outil est fourni uniquement au groupe d&#39;administrateurs à utiliser pour l&#39;assimilation à grande échelle d&#39;actifs à partir de banques de données Azure ou S3.

Pour configurer l’outil, procédez comme suit :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Importation en bloc]**. Sélectionnez l’option **[!UICONTROL Créer]**.

![Configuration de l&#39;importateur en vrac](assets/bulk-import-config.png)

1. Sur la page [!UICONTROL configuration d&#39;importation en bloc], indiquez les valeurs requises.

   * [!UICONTROL Titre] : Titre descriptif.
   * [!UICONTROL Source] d&#39;importation : Sélectionnez la source de données appropriée.
   * [!UICONTROL Filtrer par taille] min. : Indiquez la taille de fichier minimale des ressources en Mo.
   * [!UICONTROL Filtrer par taille] maximale : Fournissez une taille de fichier maximale de ressources en Mo.
   * [!UICONTROL Exclure les types] Mime : Liste de types MIME séparés par des virgules à exclure de l&#39;assimilation. Par exemple, `image/jpeg, image/.*, video/mp4`.
   * [!UICONTROL Inclure les types] MIME : Liste de types MIME séparés par des virgules à inclure dans l&#39;assimilation. Voir [tous les formats de fichier pris en charge](/help/assets/file-format-support.md).
   * [!UICONTROL Mode] d&#39;importation : Sélectionnez Ignorer, Remplacer ou Créer une version. Le mode Ignorer est le mode par défaut et dans ce mode, l’analyseur ignore l’importation d’un fichier s’il existe déjà. Voir la signification de [remplacer et créer des options de version](#handling-upload-existing-file).
   * [!UICONTROL Dossier] de la Cible Ressources : Importer un dossier dans DAM où les actifs doivent être importés. Par exemple, `/content/dam/imported_assets`

1. Vous pouvez supprimer, modifier, exécuter et en faire plus avec les configurations d&#39;intégrateur que vous avez créées. Lorsque vous sélectionnez une configuration d’importateur d’importation en bloc, l’option suivante est disponible dans la barre d’outils.

   * [!UICONTROL Modifier] : Modifiez la configuration sélectionnée.
   * [!UICONTROL Supprimer] : Supprimez la configuration sélectionnée.
   * [!UICONTROL Vérifier] : Validez la connexion à la banque de données.
   * [!UICONTROL Exécution] sèche : Appelez une série de tests de l&#39;assimilation en masse.
   * [!UICONTROL Exécuter] : Exécutez la configuration sélectionnée.
   * [!UICONTROL Arrêter] : Arrêtez une configuration principale.
   * [!UICONTROL État] de la tâche : Vue l’état de la configuration lorsqu’elle est utilisée dans une tâche d’importation en cours ou pour une tâche terminée.
   * [!UICONTROL Ressources] de vue : Vue le dossier de cible s’il existe.

>[!NOTE]
>
>Pour effectuer un téléchargement massif dans le cadre de la migration de contenu à partir d’autres systèmes lors de la configuration et du déploiement vers Experience Manager, la planification et le choix des outils doivent faire l’objet d’une attention particulière. Consultez le [guide de déploiement](/help/implementing/deploying/overview.md) pour en savoir plus sur les méthodes de migration de contenu.

## Chargement de ressources à l’aide de clients pour ordinateur de bureau {#upload-assets-desktop-clients}

Outre l’interface utilisateur du navigateur web, Experience Manager prend en charge d’autres clients pour ordinateur de bureau. Ils permettent également de télécharger du contenu sans devoir passer par le navigateur web.

* [Adobe Asset Link](https://helpx.adobe.com/fr/enterprise/using/adobe-asset-link.html) permet d’accéder aux ressources [!DNL Experience Manager] dans les applications de bureau Adobe Photoshop, Adobe Illustrator et Adobe InDesign. Ces applications vous offrent la possibilité de charger directement le document ouvert vers [!DNL Experience Manager] depuis l’interface utilisateur d’Adobe Asset Link.
* L’[application de bureau Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) simplifie l’utilisation des ressources sur l’ordinateur, indépendamment du type de fichier ou de l’application native affectée à leur gestion. Il est particulièrement utile de charger des fichiers dans des hiérarchies de dossiers imbriqués à partir de votre système de fichiers local, car le téléchargement à l’aide du navigateur ne prend en charge que les listes de fichiers plats.

## Traiter les ressources lors du transfert {#process-when-uploaded}

Pour effectuer un traitement supplémentaire sur les fichiers téléchargés, vous pouvez appliquer des profils de traitement sur les dossiers de téléchargement. Les profils sont disponibles dans la page **[!UICONTROL Propriétés]** d&#39;un dossier dans [!DNL Assets].

![assets-folder-properties](assets/assets-folder-properties.png)

Les onglets suivants sont disponibles :

* Les [profils de métadonnées](metadata-profiles.md) vous permettent d’appliquer des propriétés de métadonnées par défaut aux ressources chargées dans ce dossier.
* Les [profils de traitement](asset-microservices-configure-and-use.md) vous permettent de générer davantage de rendus que ce qui est possible par défaut.

De plus, si [!DNL Dynamic Media] est activé sur votre déploiement, les onglets suivants sont disponibles :

* Les [profils d’image Dynamic Media](dynamic-media/image-profiles.md) vous permettent d’appliquer un recadrage spécifique (**[!UICONTROL Recadrage intelligent]** et recadrage de pixels) et une configuration d’accentuation aux ressources chargées.
* Les [profils vidéo Dynamic Media](dynamic-media/video-profiles.md) vous permettent d’appliquer des profils de codage vidéo spécifiques (résolution, format, paramètres).

>[!NOTE]
>
>Le recadrage Dynamic Media et les autres opérations effectuées sur les ressources ne sont pas destructifs. En d’autres termes, ce type d’opération ne modifie pas l’élément original chargé, mais fournit des paramètres de recadrage ou de transformation des médias à effectuer lors de la diffusion des ressources.

Pour les dossiers auxquels un profil de traitement est affecté, le nom du profil s’affiche sur la vignette en mode Carte. En mode Liste, le nom du profil s’affiche dans la colonne **[!UICONTROL Profil de traitement.]**

## Chargement ou ingestion de fichiers à l’aide d’API {#upload-using-apis}

Les détails techniques du protocole et des API de chargement, ainsi que les liens vers les exemples de clients et le SDK Open Source, sont fournis dans la section [Chargement de ressources](developer-reference-material-apis.md#asset-upload-technical) de la documentation de référence du développeur.

>[!MORELIKETHIS]
>
>* [Application de bureau Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html)
>* [À propos d’Adobe Asset Link](https://www.adobe.com/creativecloud/business/enterprise/adobe-asset-link.html)
>* [Documentation d’Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)
>* [Référence technique pour le chargement de ressources](developer-reference-material-apis.md#asset-upload-technical)

