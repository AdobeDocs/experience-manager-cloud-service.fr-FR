---
title: Références du développeur pour  [!DNL Assets]
description: '[!DNL Assets] APIs and developer reference content lets you manage assets, including binary files, metadata, renditions, comments, and [!DNL Content Fragments].'
contentOwner: AG
feature: API,API HTTP Assets
role: Developer,Architect,Admin
exl-id: c75ff177-b74e-436b-9e29-86e257be87fb
source-git-commit: 3051475d20d5b534b74c84f9d541dcaf1a5492f9
workflow-type: tm+mt
source-wordcount: '1436'
ht-degree: 90%

---

# [!DNL Adobe Experience Manager Assets] Cas d’utilisation pour les développeurs, API et documents de référence {#assets-cloud-service-apis}

L’article contient des recommandations, des documents de référence et des ressources pour les développeurs de [!DNL Assets] as a [!DNL Cloud Service]. Il comprend un nouveau module de chargement de ressources, des références d’API et des informations sur la prise en charge fournie dans les workflows de post-traitement.

## [!DNL Experience Manager Assets] API et opérations {#use-cases-and-apis}

[!DNL Assets] as a [!DNL Cloud Service] fournit plusieurs API pour interagir par programmation avec des ressources numériques. Chaque API prend en charge des cas d’utilisation spécifiques, comme indiqué dans le tableau ci-dessous. L’interface utilisateur [!DNL Assets], l’application de bureau [!DNL Experience Manager] et [!DNL Adobe Asset Link] prennent en charge l’ensemble ou une partie des opérations.

>[!CAUTION]
>
>Certaines API existent toujours mais ne sont pas activement prises en charge (signalées par un ×). Dans la mesure du possible, n’utilisez pas ces API.

| Niveau de prise en charge | Description |
| ------------- | --------------------------- |
| ✓ | Pris en charge |
| × | Pas de prise en charge. Ne pas utiliser. |
| - | Non disponible |

| Cas d’utilisation | [aem-upload](https://github.com/adobe/aem-upload) | [API Experience Manager/Sling/](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/index.html) JCRJava | [Asset Compute Service](https://experienceleague.adobe.com/docs/asset-compute/using/extend/understand-extensibility.html?lang=fr) | API HTTP [[!DNL Assets]  ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/mac-api-assets.html?lang=fr#create-an-asset) | Servlets Sling [GET](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html) / [POST](https://sling.apache.org/documentation/bundles/manipulating-content-the-slingpostservlet-servlets-post.html) | [GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html?lang=fr) _(Prévisualisation)_ |
| ----------------|:---:|:---:|:---:|:---:|:---:|:---:|
| **Binaire original** |  |  |  |  |  |  |
| Créer l’original | ✓ | × | - | × | × | - |
| Lire l’original | - | × | ✓ | ✓ | ✓ | - |
| Mettre à jour l’original | ✓ | × | ✓ | × | × | - |
| Supprimer l’original | - | ✓ | - | ✓ | ✓ | - |
| Copier l’original | - | ✓ | - | ✓ | ✓ | - |
| Déplacer l’original | - | ✓ | - | ✓ | ✓ | - |
| **Métadonnées** |  |  |  |  |  |  |
| Créer des métadonnées | - | ✓ | ✓ | ✓ | ✓ | - |
| Lire les métadonnées | - | ✓ | - | ✓ | ✓ | - |
| Mettre à jour les métadonnées | - | ✓ | ✓ | ✓ | ✓ | - |
| Supprimer les métadonnées | - | ✓ | ✓ | ✓ | ✓ | - |
| Copier les métadonnées | - | ✓ | - | ✓ | ✓ | - |
| Déplacer les métadonnées | - | ✓ | - | ✓ | ✓ | - |
| **Fragments de contenu (CF)** |  |  |  |  |  |  |
| Créer un CF | - | ✓ | - | ✓ | - | - |
| Lire un CF | - | ✓ | - | ✓ | - | ✓ |
| Mettre à jour un CF | - | ✓ | - | ✓ | - | - |
| Supprimer un CF | - | ✓ | - | ✓ | - | - |
| Copier un CF | - | ✓ | - | ✓ | - | - |
| Déplacer un CF | - | ✓ | - | ✓ | - | - |
| **Versions** |  |  |  |  |  |  |
| Créer une version | ✓ | ✓ | - | - | - | - |
| Lire une version | - | ✓ | - | - | - | - |
| Supprimer une version | - | ✓ | - | - | - | - |
| **Dossiers** |  |  |  |  |  |  |
| Créer un dossier | ✓ | ✓ | - | ✓ | - | - |
| Lire un dossier | - | ✓ | - | ✓ | - | - |
| Supprimer un dossier | ✓ | ✓ | - | ✓ | - | - |
| Copier un dossier | ✓ | ✓ | - | ✓ | - | - |
| Déplacer un dossier | ✓ | ✓ | - | ✓ | - | - |

## Chargement de ressources {#asset-upload}

Dans [!DNL Experience Manager] as a [!DNL Cloud Service], vous pouvez charger directement les ressources dans l’espace de stockage cloud à l’aide de l’API HTTP. Les étapes de téléchargement d’un fichier binaire sont les suivantes. Exécutez ces étapes dans une application externe et non dans la JVM [!DNL Experience Manager].

1. [Envoyez une requête HTTP](#initiate-upload). Cela permet d’informer le déploiement [!DNL Experience Manage] de votre intention de charger un nouveau fichier binaire.
1. [PUT du contenu du ](#upload-binary) fichier binaire sur un ou plusieurs URI fournis par la demande de lancement.
1. [Envoyez une requête HTTP](#complete-upload) pour informer le serveur que le contenu du fichier binaire a bien été chargé.

![Présentation du protocole de chargement binaire direct](assets/add-assets-technical.png)

>[!IMPORTANT]
Exécutez les étapes ci-dessus dans une application externe et non dans la JVM [!DNL Experience Manager].

Cette approche permet une gestion évolutive et plus performante des chargements de ressources. Les différences par rapport à [!DNL Experience Manager] 6.5 sont les suivantes :

* Les fichiers binaires ne passent pas par [!DNL Experience Manager], qui coordonne désormais simplement le processus de chargement avec l’espace de stockage de fichiers binaires configuré pour le déploiement.
* L’espace de stockage de fichiers binaires fonctionne avec un réseau CDN (réseau de diffusion de contenu) ou Edge. Un CDN sélectionne un point d’entrée de chargement plus proche pour un client. Lorsque les données parcourent une distance plus courte jusqu’à un point d’entrée voisin, les performances de chargement et l’expérience utilisateur s’améliorent, en particulier pour les équipes réparties géographiquement.

>[!NOTE]
Consultez le code client pour implémenter cette approche dans la [bibliothèque de chargement aem](https://github.com/adobe/aem-upload) open-source.

### Lancement du chargement {#initiate-upload}

Envoyez une requête HTTP POST vers le dossier souhaité. Les ressources sont créées ou mises à jour dans ce dossier. Incluez le sélecteur `.initiateUpload.json` pour indiquer que la requête est de lancer le chargement d’un fichier binaire. Par exemple, le chemin d’accès au dossier dans lequel la ressource doit être créée est `/assets/folder`. La requête POST est `POST https://[aem_server]:[port]/content/dam/assets/folder.initiateUpload.json`.

Le corps de la requête doit être constitué de données de formulaire `application/x-www-form-urlencoded`, contenant les champs suivants :

* `(string) fileName` : obligatoire. Le nom de la ressource tel qu’il apparaît dans [!DNL Experience Manager].
* `(number) fileSize` : obligatoire. La taille de fichier, en octets, de la ressource en cours de chargement.

Une seule requête peut être utilisée afin de lancer des chargements pour plusieurs fichiers binaires, à condition que chaque binaire contienne les champs obligatoires. En cas de succès, la requête renverra un code d’état `201` et un corps contenant des données JSON au format suivant :

```json
{
    "completeURI": "(string)",
    "folderPath": (string)",
    "files": [
        {
            "fileName": "(string)",
            "mimeType": "(string)",
            "uploadToken": "(string)",
            "uploadURIs": [
                "(string)"
            ]
        }
    ]
}
```

* `completeURI` (chaîne) : appelez cet URI lorsque le chargement du fichier binaire est terminé. Il peut s’agir d’un URI absolu ou relatif, et les clients doivent être en mesure de gérer l’un ou l’autre. En d’autres termes, la valeur peut être `"https://[aem_server]:[port]/content/dam.completeUpload.json"` ou `"/content/dam.completeUpload.json"` ; voir [Fin du chargement](#complete-upload).
* `folderPath` (chaîne) : chemin d’accès complet au dossier dans lequel le fichier binaire est chargé.
* `(files)` (tableau) : liste des éléments dont la longueur et l’ordre correspondent à la longueur et à l’ordre de la liste des informations binaires fournies dans la requête de lancement.
* `fileName` (chaîne) : nom du fichier binaire correspondant, tel qu’il est fourni dans la requête de lancement. Cette valeur doit être incluse dans la requête de fin.
* `mimeType` (chaîne) : type MIME du fichier binaire correspondant, tel qu’il est fourni dans la requête de lancement. Cette valeur doit être incluse dans la requête de fin.
* `uploadToken` (chaîne) : jeton de chargement du fichier binaire correspondant. Cette valeur doit être incluse dans la requête de fin.
* `uploadURIs` (tableau) : liste des chaînes dont les valeurs sont des URI complets vers lesquels le contenu du fichier binaire doit être chargé (voir [Chargement d’un fichier binaire](#upload-binary)).
* `minPartSize` (nombre) : longueur minimale, en octets, des données pouvant être fournies à l’un des `uploadURIs`, s’il en existe plusieurs.
* `maxPartSize`(nombre) : longueur maximale, en octets, des données pouvant être fournies à l’un des `uploadURIs`, s’il en existe plusieurs.

### Chargement d’un fichier binaire {#upload-binary}

La sortie de lancement d’un chargement comprend une ou plusieurs valeurs d’URI de chargement. Si plusieurs URI sont fournis, le client divise le fichier binaire en plusieurs parties et effectue des requêtes PUT de chaque partie vers chaque URI, dans l’ordre. Utilisez tous les URI. Assurez-vous que la taille de chaque partie soit sur la plage spécifiée dans la réponse au lancement. Les nœuds de bordure CDN permettent d’accélérer le chargement de fichiers binaires requis.

Pour ce faire, une méthode consiste à calculer la taille de la partie en fonction du nombre d’URI de chargement fournis par l’API. Voici un exemple en supposant que la taille totale du fichier binaire soit de 20 000 octets et que le nombre d’URI de chargement soit de 2. Procédez ensuite comme suit :

* Calculez la taille d’une pièce en divisant la taille totale par le nombre d’URI : 20 000 / 2 = 10 000.
* Publiez la plage d’octets 0 à 9 999 du binaire sur le premier URI de la liste des URI de chargement.
* Publiez la plage d’octets 10 000 à 19 999 du binaire sur le deuxième URI de la liste des URI de chargement.

En cas de succès du chargement, le serveur répond à chaque requête avec un code d’état `201`.

### Fin du chargement {#complete-upload}

Après avoir chargé toutes les parties d’un fichier binaire, envoyez une requête HTTP POST à l’URI complet fourni par les données d’initialisation. Le corps de la requête doit être constitué de données de formulaire `application/x-www-form-urlencoded`, contenant les champs suivants.

| Champs | Type | Requis ou non | Description |
|---|---|---|---|
| `fileName` | Chaîne | Requis | Nom de la ressource, tel qu’il est fourni par les données de lancement. |
| `mimeType` | Chaîne | Requis | Type de contenu HTTP du binaire, tel qu’il est fourni par les données de lancement. |
| `uploadToken` | Chaîne | Requis | Jeton de chargement du binaire, tel qu’il est fourni par les données de lancement. |
| `createVersion` | Booléen | Facultatif | Si la valeur est définie sur `True` et qu’il existe une ressource portant le nom spécifié, [!DNL Experience Manager] crée une nouvelle version de la ressource. |
| `versionLabel` | Chaîne | Facultatif | Si une version est créée, le libellé associé à la nouvelle version d’une ressource. |
| `versionComment` | Chaîne | Facultatif | Si une version est créée, les commentaires associés à la version. |
| `replace` | Booléen | Facultatif | Si `True` et qu’une ressource portant le nom spécifié existe, [!DNL Experience Manager] supprime la ressource, puis la recrée. |

>[!NOTE]
Si la ressource existe et que ni `createVersion` ni `replace` n’est spécifié, [!DNL Experience Manager] met à jour la version actuelle de la ressource avec le nouveau fichier binaire.

Comme c’est le cas pour le processus de lancement, les données de la requête de fin peuvent contenir des informations pour plusieurs fichiers.

Le processus de chargement d’un binaire n’est pas terminé tant que l’URL complète n’est pas appelée pour le fichier. Une ressource est traitée une fois le processus de chargement terminé. Le traitement ne commence pas même si le fichier binaire de la ressource est complètement chargé, mais que le processus de chargement n’est pas terminé. Si le téléchargement est réussi, le serveur répond avec un code d’état `200`.

### Bibliothèque de chargement Open Source {#open-source-upload-library}

Pour en savoir plus sur les algorithmes de chargement ou pour créer vos propres scripts et outils de chargement, Adobe fournit des bibliothèques et des outils Open Source :

* [Bibliothèque de chargement AEM Open Source](https://github.com/adobe/aem-upload).
* [Outil de ligne de commande Open Source](https://github.com/adobe/aio-cli-plugin-aem).

### API de chargement de ressources obsolètes {#deprecated-asset-upload-api}

<!-- #ENGCHECK review / update the list of deprecated APIs below. -->

La nouvelle méthode de chargement n’est prise en charge que pour [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]. Les API de [!DNL Adobe Experience Manager] 6.5 sont obsolètes. Les méthodes liées au chargement ou à la mise à jour de ressources ou de rendus (tout chargement de binaires) sont obsolètes dans les API suivantes :

* [API HTTP des ressources Experience Manager](mac-api-assets.md)
* API Java `AssetManager`, comme `AssetManager.createAsset(..)`

>[!MORELIKETHIS]
* [Bibliothèque de chargement AEM Open Source](https://github.com/adobe/aem-upload).
* [Outil de ligne de commande Open Source](https://github.com/adobe/aio-cli-plugin-aem).


## Workflows de traitement et de post-traitement des ressources {#post-processing-workflows}

Dans [!DNL Experience Manager], le traitement des ressources est basé sur la configuration des **[!UICONTROL Profils de traitement]** qui utilise des [microservices de ressources](asset-microservices-configure-and-use.md#get-started-using-asset-microservices). Le traitement ne nécessite pas d’extensions de développeur.

Pour la configuration du workflow de post-traitement, utilisez les workflows standard avec des extensions pour les étapes personnalisées.

## Prise en charge des étapes d’un workflow de post-traitement {#post-processing-workflows-steps}

Si vous effectuez une mise à niveau à partir d’une version précédente de [!DNL Experience Manager], vous pouvez utiliser les microservices de ressources pour traiter les ressources. Les microservices de ressources basés sur le cloud sont plus simples à configurer et à utiliser. Certaines étapes appliquées dans le workflow [!UICONTROL Ressource de mise à jour de la gestion des actifs numériques] de la version précédente ne sont pas prises en charge. Pour plus d’informations sur les classes prises en charge, voir [Référence de l’API Java](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/index.html).

Les modèles de workflow techniques suivants ont été remplacés par des microservices de ressources ou la prise en charge n’est pas disponible :

* `com.day.cq.dam.cameraraw.process.CameraRawHandlingProcess`
* `com.day.cq.dam.core.process.CommandLineProcess`
* `com.day.cq.dam.pdfrasterizer.process.PdfRasterizerHandlingProcess`
* `com.day.cq.dam.core.process.AddPropertyWorkflowProcess`
* `com.day.cq.dam.core.process.CreateSubAssetsProcess`
* `com.day.cq.dam.core.process.DownloadAssetProcess`
* `com.day.cq.dam.word.process.ExtractImagesProcess`
* `com.day.cq.dam.word.process.ExtractPlainProcess`
* `com.day.cq.dam.ids.impl.process.IDSJobProcess`
* `com.day.cq.dam.indd.process.INDDMediaExtractProcess`
* `com.day.cq.dam.indd.process.INDDPageExtractProcess`
* `com.day.cq.dam.core.impl.lightbox.LightboxUpdateAssetProcess`
* `com.day.cq.dam.pim.impl.sourcing.upload.process.ProductAssetsUploadProcess`
* `com.day.cq.dam.core.process.SendDownloadAssetEmailProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.StartTrainingProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.TransferTrainingDataProcess`
* `com.day.cq.dam.switchengine.process.SwitchEngineHandlingProcess`
* `com.day.cq.dam.core.process.GateKeeperProcess`
* `com.day.cq.dam.s7dam.common.process.DMEncodeVideoWorkflowCompletedProcess`
* `com.day.cq.dam.core.process.DeleteImagePreviewProcess`
* `com.day.cq.dam.video.FFMpegTranscodeProcess`
* `com.day.cq.dam.core.process.ThumbnailProcess`
* `com.day.cq.dam.video.FFMpegThumbnailProcess`
* `com.day.cq.dam.core.process.CreateWebEnabledImageProcess`
* `com.day.cq.dam.core.process.CreatePdfPreviewProcess`
* `com.day.cq.dam.s7dam.common.process.VideoUserUploadedThumbnailProcess`
* `com.day.cq.dam.s7dam.common.process.VideoThumbnailDownloadProcess`
* `com.day.cq.dam.s7dam.common.process.VideoProxyServiceProcess`
* `com.day.cq.dam.scene7.impl.process.Scene7UploadProcess`
* `com.day.cq.dam.s7dam.common.process.S7VideoThumbnailProcess`
* `com.day.cq.dam.core.process.MetadataProcessorProcess`
* `com.day.cq.dam.core.process.AssetOffloadingProcess`
* `com.adobe.cq.dam.dm.process.workflow.DMImageProcess`

<!-- Commenting the previous list documented at the time of GA. Replacing it with the updated list via cqdoc-18231.

* `com.day.cq.dam.core.process.DeleteImagePreviewProcess`
* `com.day.cq.dam.s7dam.common.process.DMEncodeVideoWorkflowCompletedProcess`
* `com.day.cq.dam.core.process.GateKeeperProcess`
* `com.day.cq.dam.core.process.AssetOffloadingProcess`
* `com.day.cq.dam.core.process.MetadataProcessorProcess`
* `com.adobe.cq.dam.dm.process.workflow.DMImageProcess`
* `com.day.cq.dam.s7dam.common.process.S7VideoThumbnailProcess`
* `com.day.cq.dam.scene7.impl.process.Scene7UploadProcess`
* `com.day.cq.dam.s7dam.common.process.VideoProxyServiceProcess`
* `com.day.cq.dam.s7dam.common.process.VideoThumbnailDownloadProcess`
* `com.day.cq.dam.s7dam.common.process.VideoUserUploadedThumbnailProcess`
* `com.day.cq.dam.core.process.CreatePdfPreviewProcess`
* `com.day.cq.dam.core.process.CreateWebEnabledImageProcess`
* `com.day.cq.dam.video.FFMpegThumbnailProcess`
* `com.day.cq.dam.core.process.ThumbnailProcess`
* `com.day.cq.dam.cameraraw.process.CameraRawHandlingProcess`
* `com.day.cq.dam.core.process.CommandLineProcess`
* `com.day.cq.dam.pdfrasterizer.process.PdfRasterizerHandlingProcess`
* `com.day.cq.dam.core.process.AddPropertyWorkflowProcess`
* `com.day.cq.dam.core.process.CreateSubAssetsProcess`
* `com.day.cq.dam.core.process.DownloadAssetProcess`
* `com.day.cq.dam.word.process.ExtractImagesProcess`
* `com.day.cq.dam.word.process.ExtractPlainProcess`
* `com.day.cq.dam.video.FFMpegTranscodeProcess`
* `com.day.cq.dam.ids.impl.process.IDSJobProcess`
* `com.day.cq.dam.indd.process.INDDMediaExtractProcess`
* `com.day.cq.dam.indd.process.INDDPageExtractProcess`
* `com.day.cq.dam.core.impl.lightbox.LightboxUpdateAssetProcess`
* `com.day.cq.dam.pim.impl.sourcing.upload.process.ProductAssetsUploadProcess`
* `com.day.cq.dam.core.process.ScheduledPublishBPProcess`
* `com.day.cq.dam.core.process.ScheduledUnPublishBPProcess`
* `com.day.cq.dam.core.process.SendDownloadAssetEmailProcess`
-->

<!-- PPTX source: slide in add-assets.md - overview of direct binary upload section of 
https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

>[!MORELIKETHIS]
* SDK [[!DNL Experience Cloud] as a [!DNL Cloud Service]  ](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md).

