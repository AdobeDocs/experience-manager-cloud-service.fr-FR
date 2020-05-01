---
title: 'API Assets pour la gestion des ressources numériques dans Adobe Experience Manager as a Cloud Service '
description: Les API Assets permettent d’effectuer des opérations CRUD (création, lecture, mise à jour, suppression) de base afin de gérer des ressources, y compris des fichiers binaires, des métadonnées, des rendus, des commentaires et des fragments de contenu.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0686acbc61b3902c6c926eaa6424828db0a6421a

---


# API Assets as a Cloud Service{#assets-cloud-service-apis}

<!-- 
Give a list of and overview of all reference information available.
* New upload method
* Javadocs
* Assets HTTP API documented at [https://helpx.adobe.com/experience-manager/6-5/assets/using/mac-api-assets.html](https://helpx.adobe.com/experience-manager/6-5/assets/using/mac-api-assets.html)

-->

## Chargement de ressources {#asset-upload-technical}

Experience Manager as a Cloud Service offre une nouvelle méthode de chargements des ressources vers le référentiel : chargement binaire direct vers un espace de stockage de fichiers binaires dans le cloud. Cette section vous présente un aperçu technique.

### Présentation du chargement binaire direct {#overview-binary-upload}

L’algorithme de haut niveau pour le chargement d’un fichier binaire est le suivant :

1. Envoyez une requête HTTP informant AEM de l’intention de charger un nouveau fichier binaire.
1. Publiez le contenu du fichier binaire sur un ou plusieurs URI fournis par la requête de lancement.
1. Envoyez une requête HTTP pour informer le serveur que le contenu du fichier binaire a bien été chargé.

![Présentation du protocole de chargement binaire direct](assets/add-assets-technical.png)

Voici un aperçu des différences importantes par rapport aux versions antérieures d’AEM :

* Les fichiers binaires ne passent pas par AEM, qui désormais coordonne simplement le processus de chargement avec l’espace de stockage des fichiers binaires dans le cloud configuré pour le déploiement.
* L’espace de stockage des fichiers binaires est dirigé par un réseau de diffusion de contenu (CDN, Content Delivery Network) qui rapproche le point de terminaison de chargement du client. Cela contribue à améliorer les performances de chargement et l’expérience utilisateur, en particulier pour les équipes distribuées géographiquement qui chargent des ressources.

Cette méthode doit permettre une gestion plus évolutive et plus performante des chargements de ressources.

> !![NOTE]
To review client code that implements this approach, refer to the open-source [aem-upload library](https://github.com/adobe/aem-upload)

### Lancement du chargement {#initiate-upload}

La première étape consiste à envoyer une requête HTTP POST au dossier où la ressource doit être créée ou mise à jour ; incluez le sélecteur `.initiateUpload.json` pour indiquer que la requête doit démarrer un chargement binaire. Par exemple, le chemin d’accès au dossier dans lequel la ressource doit être créée est `/assets/folder` :

```
POST https://[aem_server]/content/dam/assets/folder.initiateUpload.json
````

Le corps de la requête doit être constitué de données de formulaire `application/x-www-form-urlencoded`, contenant les champs suivants :

* `(string) fileName` : obligatoire. Nom de la ressource tel qu’il apparaîtra dans l’instance.
* `(number) fileSize` : obligatoire. Longueur totale, en octets, du fichier binaire à charger.

Une seule requête peut être utilisée pour lancer des téléchargements pour plusieurs binaires, à condition que chaque binaire contienne les champs requis. If successful, the request responds with a `201` status code and a body containing JSON data in the following format:

```
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

* `completeURI` (chaîne) : Appelez cet URI lorsque le téléchargement du fichier binaire est terminé. L&#39;URI peut être un URI absolu ou relatif et les clients doivent pouvoir gérer l&#39;un ou l&#39;autre. En d’autres termes, la valeur peut être `"https://author.acme.com/content/dam.completeUpload.json"` ou `"/content/dam.completeUpload.json"` Voir téléchargement [](#complete-upload)complet.
* `folderPath` (chaîne) : Chemin d’accès complet au dossier dans lequel le fichier binaire est téléchargé.
* `(files)` (tableau) : liste d’éléments dont la longueur et l’ordre correspondent à la longueur et à l’ordre de la liste des informations binaires fournies dans la demande d’ouverture.
* `fileName` (chaîne) : Nom du binaire correspondant, tel qu’il est fourni dans la demande de lancement. Cette valeur doit être incluse dans la requête de fin.
* `mimeType` (chaîne) : Type MIME du binaire correspondant, tel qu’il est fourni dans la demande de lancement en cours. Cette valeur doit être incluse dans la requête de fin.
* `uploadToken` (chaîne) : Jeton de téléchargement pour le binaire correspondant. Cette valeur doit être incluse dans la requête de fin.
* `uploadURIs` (tableau) : liste de chaînes dont les valeurs sont des URI complets vers lesquels le contenu du binaire doit être téléchargé (voir [Télécharger le binaire](#upload-binary)).
* `minPartSize` (nombre) : Longueur minimale, en octets, des données pouvant être fournies à l’un des URI de téléchargement, s’il existe plusieurs URI.
* `maxPartSize` (nombre) : Longueur maximale, en octets, des données pouvant être fournies à l’un des URI de téléchargement, s’il existe plusieurs URI.

### Chargement d’un binaire {#upload-binary}

La sortie de lancement d’un chargement comprend une ou plusieurs valeurs d’URI de chargement. Si plusieurs URI sont fournis, il est de la responsabilité du client de « diviser » le binaire en plusieurs parties et de publier (requête POST) chacune d’elles, dans l’ordre, vers chaque URI. Tous les URI doivent être utilisés, et la taille de chaque partie doit être supérieure à la taille minimale et inférieure à la taille maximale spécifiée dans la réponse de lancement. Ces requêtes seront traitées par les nœuds de périphérie du réseau CDN pour accélérer le chargement des binaires.

Pour ce faire, une méthode consiste à calculer la taille de la partie en fonction du nombre d’URI de chargement fournis par l’API. Voici un exemple en supposant que la taille totale du fichier binaire soit de 20 000 octets et que le nombre d’URI de chargement soit de 2 :

* Calculez la taille d’une pièce en divisant la taille totale par le nombre d’URI : 20 000 / 2 = 10 000
* Publiez la plage d’octets 0 à 9 999 du binaire sur le premier URI de la liste des URI de chargement
* Publiez la plage d’octets 10 000 à 19 999 du binaire sur le deuxième URI de la liste des URI de chargement

En cas de succès, le serveur répond à chaque requête avec un code d’état `201`.

### Fin du chargement {#complete-upload}

Après avoir téléchargé toutes les parties d’un fichier binaire, envoyez une requête HTTP POST à l’URI complet fourni par les données d’initialisation. The content type of the request body should be `application/x-www-form-urlencoded` form data, containing the following fields.

| Champs | Type | Obligatoire ou non | Description |
|---|---|---|---|
| `fileName` | Chaîne | Requis | Nom de la ressource, tel qu’il est fourni par les données de lancement. |
| `mimeType` | Chaîne | Requis | Type de contenu HTTP du binaire, tel qu’il est fourni par les données de lancement. |
| `uploadToken` | Chaîne | Requis | Jeton de chargement du binaire, tel qu’il est fourni par les données de lancement. |
| `createVersion` | Booléen | Facultatif | If `True` and an asset with the specified name already exists, then Experience Manager creates a new version of the asset. |
| `versionLabel` | Chaîne | Facultatif | Si une nouvelle version est créée, l’étiquette associée à la nouvelle version d’un fichier. |
| `versionComment` | Chaîne | Facultatif | Si une nouvelle version est créée, les commentaires associés à la version. |
| `replace` | Booléen | Facultatif | Si `True` et qu’un fichier portant le nom spécifié existe déjà, Experience Manager supprime le fichier, puis le recrée. |

>!![NOTE]
>
> If the asset already exists and neither `createVersion` nor `replace` is specified, then Experience Manager updates the asset&#39;s current version with the new binary.

Comme c’est le cas pour le processus de lancement, les données de la requête de fin peuvent contenir des informations pour plusieurs fichiers.

Le processus de chargement d’un binaire n’est pas terminé tant que l’URL complète n’est pas appelée pour le fichier. Même si le binaire d’un fichier est intégralement chargé, la ressource n’est pas traitée par l’instance tant que son processus de chargement n’est pas terminé.

En cas de succès, le serveur répond avec un code d’état `200`.

### Bibliothèque de chargement Open Source {#open-source-upload-library}

Pour en savoir plus sur les algorithmes de téléchargement ou pour créer vos propres scripts et outils de téléchargement, Adobe fournit des bibliothèques et des outils open source comme point de départ :

* [Bibliothèque de téléchargement aem open-source](https://github.com/adobe/aem-upload)
* [Outil de ligne de commande open-source](https://github.com/adobe/aio-cli-plugin-aem)

### API de chargement de ressources obsolètes {#deprecated-asset-upload-api}

<!-- #ENGCHECK review / update the list of deprecated APIs below. -->

Pour Adobe Experience Manager en tant que service Cloud, seules les nouvelles API de téléchargement sont prises en charge. Les API d’Adobe Experience Manager 6.5 sont obsolètes. Les méthodes liées au téléchargement ou à la mise à jour des ressources ou des rendus (tout transfert binaire) sont déconseillées dans les API suivantes :

* [API HTTP AEM Assets](mac-api-assets.md)
* API Java `AssetManager`, comme `AssetManager.createAsset(..)`

>[!MORELIKETHIS]
* [Bibliothèque](https://github.com/adobe/aem-upload)de téléchargement aem open source.
* [Outil](https://github.com/adobe/aio-cli-plugin-aem)de ligne de commande open-source.


## Workflows de traitement et de post-traitement des ressources {#post-processing-workflows}

Dans Experience Manager, le traitement des ressources est basé sur la configuration des Profils **[!UICONTROL de]** traitement qui utilise des microservices [de](asset-microservices-configure-and-use.md#get-started-using-asset-microservices)ressources. Le traitement ne nécessite pas d’extensions développeur.

Pour la configuration du processus de post-traitement, utilisez les workflows standard avec des extensions avec des étapes personnalisées.

## Prise en charge des étapes du processus dans le processus de post-traitement {#post-processing-workflows-steps}

Les clients qui effectuent la mise à niveau vers Experience Manager en tant que service Cloud à partir des versions précédentes d’Experience Manager peuvent utiliser des microservices de ressources pour le traitement des ressources. Les microservices de ressources natifs au cloud sont beaucoup plus simples à configurer et à utiliser. Certaines étapes de processus utilisées dans le processus de mise à jour des ressources [!UICONTROL de] gestion des actifs dans la version précédente ne sont pas prises en charge.

Les étapes de processus suivantes sont prises en charge dans Experience Manager en tant que service Cloud.

* `com.day.cq.dam.similaritysearch.internal.workflow.process.AutoTagAssetProcess`
* `com.day.cq.dam.core.impl.process.CreateAssetLanguageCopyProcess`
* `com.day.cq.wcm.workflow.process.CreateVersionProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.StartTrainingProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.TransferTrainingDataProcess`
* `com.day.cq.dam.core.impl.process.TranslateAssetLanguageCopyProcess`
* `com.day.cq.dam.core.impl.process.UpdateAssetLanguageCopyProcess`
* `com.adobe.cq.workflow.replication.impl.ReplicationWorkflowProcess`
* `com.day.cq.dam.core.impl.process.DamUpdateAssetWorkflowCompletedProcess`

Les modèles de workflow techniques suivants ont été remplacés par des microservices de ressources ou la prise en charge n’est pas disponible.

* `com.day.cq.dam.core.impl.process.DamMetadataWritebackWorkflowCompletedProcess`
* `com.day.cq.dam.core.process.DeleteImagePreviewProcess`
* `com.day.cq.dam.s7dam.common.process.DMEncodeVideoWorkflowCompletedProcess`
* `com.day.cq.dam.core.process.GateKeeperProcess`
* `com.day.cq.dam.core.process.AssetOffloadingProcess`
* `com.day.cq.dam.core.process.MetadataProcessorProcess`
* `com.day.cq.dam.core.process.XMPWritebackProcess`
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
* `com.day.cq.dam.core.impl.process.SendTransientWorkflowCompletedEmailProcess`

<!-- PPTX source: slide in add-assets.md - overview of direct binary upload section of 
https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->
