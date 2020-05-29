---
title: 'API Assets pour la gestion des ressources numériques dans Adobe Experience Manager as a Cloud Service '
description: Les API Assets permettent d’effectuer des opérations CRUD (création, lecture, mise à jour, suppression) de base afin de gérer des ressources, y compris des fichiers binaires, des métadonnées, des rendus, des commentaires et des fragments de contenu.
contentOwner: AG
translation-type: ht
source-git-commit: 27e72bbc0d852eb2c2eb059967c91e6108613965
workflow-type: ht
source-wordcount: '1249'
ht-degree: 100%

---


# API Assets as a Cloud Service {#assets-cloud-service-apis}

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
Pour examiner le code client qui implémente cette méthode, reportez-vous à la bibliothèque Open Source [aem-upload](https://github.com/adobe/aem-upload).

### Lancement du chargement {#initiate-upload}

La première étape consiste à envoyer une requête HTTP POST au dossier où la ressource doit être créée ou mise à jour ; incluez le sélecteur `.initiateUpload.json` pour indiquer que la requête doit démarrer un chargement binaire. Par exemple, le chemin d’accès au dossier dans lequel la ressource doit être créée est `/assets/folder` :

```
POST https://[aem_server]/content/dam/assets/folder.initiateUpload.json
```

Le corps de la requête doit être constitué de données de formulaire `application/x-www-form-urlencoded`, contenant les champs suivants :

* `(string) fileName` : obligatoire. Nom de la ressource tel qu’il apparaîtra dans l’instance.
* `(number) fileSize` : obligatoire. Longueur totale, en octets, du fichier binaire à charger.

Une seule requête peut être utilisée afin de lancer des chargements pour plusieurs fichiers binaires, à condition que chaque binaire contienne les champs obligatoires. En cas de succès, la requête renverra un code d’état `201` et un corps contenant des données JSON au format suivant :

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

* `completeURI` (chaîne) : appelez cet URI lorsque le chargement du fichier binaire est terminé. Il peut s’agir d’un URI absolu ou relatif, et les clients doivent être en mesure de gérer l’un ou l’autre. En d’autres termes, la valeur peut être `"https://author.acme.com/content/dam.completeUpload.json"` ou `"/content/dam.completeUpload.json"` ; voir [Fin du chargement](#complete-upload).
* `folderPath` (chaîne) : chemin d’accès complet au dossier dans lequel le fichier binaire est chargé.
* `(files)` (tableau) : liste des éléments dont la longueur et l’ordre correspondent à la longueur et à l’ordre de la liste des informations binaires fournies dans la requête de lancement.
* `fileName` (chaîne) : nom du fichier binaire correspondant, tel qu’il est fourni dans la requête de lancement. Cette valeur doit être incluse dans la requête de fin.
* `mimeType` (chaîne) : type MIME du fichier binaire correspondant, tel qu’il est fourni dans la requête de lancement. Cette valeur doit être incluse dans la requête de fin.
* `uploadToken` (chaîne) : jeton de chargement du fichier binaire correspondant. Cette valeur doit être incluse dans la requête de fin.
* `uploadURIs` (tableau) : liste des chaînes dont les valeurs sont des URI complets vers lesquels le contenu du fichier binaire doit être chargé (voir [Chargement d’un fichier binaire](#upload-binary)).
* `minPartSize` (nombre) : longueur minimale, en octets, des données pouvant être fournies à l’un des URI de chargement, s’il en existe plusieurs.
* `maxPartSize` (nombre) : longueur maximale, en octets, des données pouvant être fournies à l’un des URI de chargement, s’il en existe plusieurs.

### Chargement d’un fichier binaire {#upload-binary}

La sortie de lancement d’un chargement comprend une ou plusieurs valeurs d’URI de chargement. Si plusieurs URI sont fournis, il est de la responsabilité du client de « diviser » le binaire en plusieurs parties et de publier (requête POST) chacune d’elles, dans l’ordre, vers chaque URI. Tous les URI doivent être utilisés, et la taille de chaque partie doit être supérieure à la taille minimale et inférieure à la taille maximale spécifiée dans la réponse de lancement. Ces requêtes seront traitées par les nœuds de périphérie du réseau CDN pour accélérer le chargement des binaires.

Pour ce faire, une méthode consiste à calculer la taille de la partie en fonction du nombre d’URI de chargement fournis par l’API. Voici un exemple en supposant que la taille totale du fichier binaire soit de 20 000 octets et que le nombre d’URI de chargement soit de 2 :

* Calculez la taille d’une pièce en divisant la taille totale par le nombre d’URI : 20 000 / 2 = 10 000
* Publiez la plage d’octets 0 à 9 999 du binaire sur le premier URI de la liste des URI de chargement
* Publiez la plage d’octets 10 000 à 19 999 du binaire sur le deuxième URI de la liste des URI de chargement

En cas de succès, le serveur répond à chaque requête avec un code d’état `201`.

### Fin du chargement {#complete-upload}

Après avoir téléchargé toutes les parties d’un fichier binaire, envoyez une requête HTTP POST à l’URI complet fourni par les données d’initialisation. Le corps de la requête doit être constitué de données de formulaire `application/x-www-form-urlencoded`, contenant les champs suivants.

| Champs | Type | Requis ou non | Description |
|---|---|---|---|
| `fileName` | Chaîne | Requis | Nom de la ressource, tel qu’il est fourni par les données de lancement. |
| `mimeType` | Chaîne | Requis | Type de contenu HTTP du binaire, tel qu’il est fourni par les données de lancement. |
| `uploadToken` | Chaîne | Requis | Jeton de chargement du binaire, tel qu’il est fourni par les données de lancement. |
| `createVersion` | Booléen | Facultatif | Si la valeur est définie sur `True` et qu’il existe déjà une ressource portant le nom spécifié, Experience Manager crée une nouvelle version de la ressource. |
| `versionLabel` | Chaîne | Facultatif | Si une version est créée, le libellé associé à la nouvelle version d’une ressource. |
| `versionComment` | Chaîne | Facultatif | Si une version est créée, les commentaires associés à la version. |
| `replace` | Booléen | Facultatif | Si `True` et qu’une ressource portant le nom spécifié existe déjà, Experience Manager supprime la ressource, puis la recrée. |

>!![NOTE]
>
> Si la ressource existe déjà et que les champs `createVersion` et `replace` ne sont ni l’un ni l’autre spécifiés, l’instance met à jour la version actuelle de la ressource avec le nouveau fichier binaire.

Comme c’est le cas pour le processus de lancement, les données de la requête de fin peuvent contenir des informations pour plusieurs fichiers.

Le processus de chargement d’un binaire n’est pas terminé tant que l’URL complète n’est pas appelée pour le fichier. Même si le binaire d’un fichier est intégralement chargé, la ressource n’est pas traitée par l’instance tant que son processus de chargement n’est pas terminé.

En cas de succès, le serveur répond avec un code d’état `200`.

### Bibliothèque de chargement Open Source {#open-source-upload-library}

Pour en savoir plus sur les algorithmes de chargement ou pour créer vos propres scripts et outils de chargement, Adobe fournit des bibliothèques et des outils Open Source comme point de départ :

* [Bibliothèque de chargement AEM Open Source](https://github.com/adobe/aem-upload)
* [Outil de ligne de commande Open Source](https://github.com/adobe/aio-cli-plugin-aem)

### API de chargement de ressources obsolètes {#deprecated-asset-upload-api}

<!-- #ENGCHECK review / update the list of deprecated APIs below. -->

Pour Adobe Experience Manager as a Cloud Service, seules les nouvelles API de chargement sont prises en charge. Les API d’Adobe Experience Manager 6.5 sont obsolètes. Les méthodes liées au chargement ou à la mise à jour de ressources ou de rendus (tout chargement de binaires) sont obsolètes dans les API suivantes :

* [API HTTP AEM Assets](mac-api-assets.md)
* API Java `AssetManager`, comme `AssetManager.createAsset(..)`

>[!MORELIKETHIS]
* [Bibliothèque de chargement AEM Open Source](https://github.com/adobe/aem-upload).
* [Outil de ligne de commande Open Source](https://github.com/adobe/aio-cli-plugin-aem).


## Workflows de traitement et de post-traitement des ressources {#post-processing-workflows}

Dans Experience Manager, le traitement des ressources est basé sur la configuration des **[!UICONTROL Profils de traitement]** qui utilise des [microservices de ressources](asset-microservices-configure-and-use.md#get-started-using-asset-microservices). Le traitement ne nécessite pas d’extensions de développeur.

Pour la configuration du workflow de post-traitement, utilisez les workflows standard avec des extensions pour les étapes personnalisées.

## Prise en charge des étapes d’un workflow de post-traitement {#post-processing-workflows-steps}

Les clients qui effectuent la mise à niveau vers Experience Manager as a Cloud Service à partir des versions précédentes d’Experience Manager peuvent utiliser des microservices pour le traitement des ressources. Les microservices de ressources natifs en mode cloud sont beaucoup plus simples à configurer et à utiliser. Certaines étapes appliquées dans le workflow [!UICONTROL Ressource de mise à jour de la gestion des actifs numériques] de la version précédente ne sont pas prises en charge.

Les étapes de workflow suivantes sont prises en charge dans Experience Manager as a Cloud Service.

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
