---
title: 'API Assets pour la gestion des ressources numériques dans Adobe Experience Manager as a Cloud Service '
description: Les API Assets permettent d’effectuer des opérations CRUD (création, lecture, mise à jour, suppression) de base afin de gérer des ressources, y compris des fichiers binaires, des métadonnées, des rendus, des commentaires et des fragments de contenu.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

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
Pour examiner le code client qui implémente cette méthode, reportez-vous à la bibliothèque Open Source [aem-upload](https://github.com/adobe/aem-upload).

### Lancement du chargement {#initiate-upload}

La première étape consiste à envoyer une requête HTTP POST au dossier où la ressource doit être créée ou mise à jour ; incluez le sélecteur `.initiateUpload.json` pour indiquer que la requête doit démarrer un chargement binaire. Par exemple, le chemin d’accès au dossier dans lequel la ressource doit être créée est `/assets/folder` :

```
POST https://[aem_server]/content/dam/assets/folder.initiateUpload.json
````

Le corps de la requête doit être constitué de données de formulaire `application/x-www-form-urlencoded`, contenant les champs suivants :

* `(string) fileName` : obligatoire. Nom de la ressource tel qu’il apparaîtra dans l’instance.
* `(number) fileSize` : obligatoire. Longueur totale, en octets, du fichier binaire à charger.

Notez qu’une seule requête peut être utilisée pour lancer des chargements pour plusieurs fichiers binaires, à condition que chaque binaire contienne les champs obligatoires.

En cas de succès, la requête renverra un code d’état 201 et un corps contenant des données JSON au format suivant :

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
````

* `(string) completeURI` : URI qui doit être appelé lorsque le chargement du fichier binaire est terminé. Il peut s’agir d’un URI absolu ou relatif, et les clients doivent être en mesure de gérer l’un ou l’autre. En d’autres termes, la valeur peut être `"https://author.acme.com/content/dam.completeUpload.json"` ou `"/content/dam.completeUpload.json"` (voir [Fin du chargement](#complete-upload)).
* `(string) folderPath` : chemin d’accès complet au dossier dans lequel le fichier binaire est chargé.
* `(array) (files)` : liste des éléments dont la longueur et l’ordre correspondent à la longueur et à l’ordre de la liste des informations binaires fournies dans la requête de lancement.
* `(string) fileName` : nom du binaire correspondant, tel qu’il est fourni dans la requête de lancement. Cette valeur doit être incluse dans la requête de fin.
* `(string) mimeType` : type MIME du binaire correspondant, tel qu’il est fourni dans la requête de lancement. Cette valeur doit être incluse dans la requête de fin.
* `(string) uploadToken` : jeton de chargement pour le binaire correspondant. Cette valeur doit être incluse dans la requête de fin.
* `(array) uploadURIs` : liste des chaînes dont les valeurs sont des URI complets vers lesquels le contenu du binaire doit être chargé (voir [Chargement d’un binaire](#upload-binary)).
* `(number) minPartSize` : longueur minimale, en octets, des données pouvant être fournies à l’un des URI de chargement, s’il en existe plusieurs.
* `(number) maxPartSize` : longueur maximale, en octets, des données pouvant être fournies à l’un des URI de chargement, s’il en existe plusieurs.

### Chargement d’un binaire {#upload-binary}

La sortie de lancement d’un chargement comprend une ou plusieurs valeurs d’URI de chargement. Si plusieurs URI sont fournis, il est de la responsabilité du client de « diviser » le binaire en plusieurs parties et de publier (requête POST) chacune d’elles, dans l’ordre, vers chaque URI. Tous les URI doivent être utilisés, et la taille de chaque partie doit être supérieure à la taille minimale et inférieure à la taille maximale spécifiée dans la réponse de lancement. Ces requêtes seront traitées par les nœuds de périphérie du réseau CDN pour accélérer le chargement des binaires.

Pour ce faire, une méthode consiste à calculer la taille de la partie en fonction du nombre d’URI de chargement fournis par l’API. Voici un exemple en supposant que la taille totale du fichier binaire soit de 20 000 octets et que le nombre d’URI de chargement soit de 2 :

* Calculez la taille d’une pièce en divisant la taille totale par le nombre d’URI : 20 000 / 2 = 10 000
* Publiez la plage d’octets 0 à 9 999 du binaire sur le premier URI de la liste des URI de chargement
* Publiez la plage d’octets 10 000 à 19 999 du binaire sur le deuxième URI de la liste des URI de chargement

En cas de succès, le serveur répond à chaque requête avec un code d’état `201`.

### Fin du chargement {#complete-upload}

Une fois toutes les parties d’un fichier binaire chargées, la dernière étape consiste à envoyer une requête HTTP POST à l’URI complet fourni par les données de lancement. Le corps de la requête doit être constitué de données de formulaire application/`x-www-form-urlencoded`, contenant les champs suivants :

* `(string) fileName` : obligatoire. Nom de la ressource, tel qu’il est fourni par les données de lancement.
* `(string) mimeType` : obligatoire. Type de contenu HTTP du binaire, tel qu’il est fourni par les données de lancement.
* `(string) uploadToken` : obligatoire. Jeton de chargement du binaire, tel qu’il est fourni par les données de lancement.
* `(bool) createVersion` : facultatif. Si la valeur est définie sur True et qu’il existe déjà une ressource portant le nom spécifié, l’instance crée une nouvelle version de la ressource.
* `(string) versionLabel` : facultatif. Libellé qui sera associé à la version, en cas de création d’une version.
* `(string) versionComment` : facultatif. Commentaires qui seront associés à la version, en cas de création d’une version.
* `(bool) replace` : facultatif. Si la valeur est définie sur True et qu’il existe déjà une ressource portant le nom spécifié, l’instance supprime la ressource, puis la recrée.

>!![NOTE]
>
> Si la ressource existe déjà et que ni le champ createVersion, ni le champ replace ne sont spécifiés, l’instance met à jour la version actuelle de la ressource avec le nouveau fichier binaire.

Comme c’est le cas pour le processus de lancement, les données de la requête de fin peuvent contenir des informations pour plusieurs fichiers.

Le processus de chargement d’un binaire n’est pas terminé tant que l’URL complète n’est pas appelée pour le fichier. Même si le binaire d’un fichier est intégralement chargé, la ressource n’est pas traitée par l’instance tant que son processus de chargement n’est pas terminé.

En cas de succès, le serveur répond avec un code d’état `200`.

### Bibliothèque de chargement Open Source {#open-source-upload-library}

Pour en savoir plus sur les algorithmes de chargement ou pour créer vos propres scripts et outils de chargement, Adobe fournit des bibliothèques et des outils Open Source comme point de départ :

* [Bibliothèque Open Source aem-upload](https://github.com/adobe/aem-upload)
* [Outil de ligne de commande Open Source](https://github.com/adobe/aio-cli-plugin-aem)

### API de chargement de ressources obsolètes {#deprecated-asset-upload-api}

<!-- #ENGCHECK please review / update the list of deprecated APIs below -->

>[!NOTE]
Pour Experience Manager as a Cloud Service, seules les nouvelles API de chargement sont prises en charge. Les API d’Experience Manager 6.5 sont obsolètes.

Les méthodes liées au chargement ou à la mise à jour de ressources ou de rendus (tout chargement de binaires) sont obsolètes dans les API suivantes :

* [API HTTP AEM Assets](mac-api-assets.md)
* API Java `AssetManager`, comme `AssetManager.createAsset(..)`

>[!MORELIKETHIS]
* [Bibliothèque Open Source aem-upload](https://github.com/adobe/aem-upload)
* [Outil de ligne de commande Open Source](https://github.com/adobe/aio-cli-plugin-aem)


## Workflows de traitement et de post-traitement des ressources {#post-processing-workflows}

La majeure partie du traitement des ressources est exécutée en fonction de la configuration des **[!UICONTROL profils de traitement]** par les [microservices de ressources](asset-microservices-configure-and-use.md#get-started-using-asset-microservices) et ne nécessite pas d’extensions de développeur.

Pour la configuration du workflow de post-traitement, les workflows AEM standard avec extensions (des étapes personnalisées, par exemple) peuvent être utilisés. Consultez la sous-section suivante pour comprendre quelles étapes de workflow peuvent être utilisées dans les workflows de post-traitement des ressources.

### Étapes du workflow de post-traitement {#post-processing-workflows-steps}

>[!NOTE]
Cette section s’applique principalement aux clients qui effectuent la mise à jour d’une version antérieure d’AEM vers AEM as a Cloud Service.

En raison d’un nouveau modèle de déploiement introduit avec Experience Manager as a Cloud Service, il se peut que certaines étapes utilisées dans le workflow `DAM Update Asset` avant l’introduction des microservices de ressources ne soient plus prises en charge pour les workflows de post-traitement. Notez que la plupart d’entre elles sont remplacées par une méthode beaucoup plus simple pour configurer et utiliser les microservices de ressources.

Vous trouverez ci-dessous une liste de modèles de workflows techniques, accompagnés de leur niveau de prise en charge dans AEM as a Cloud Service :

### Étapes de workflow prises en charge {#supported-workflow-steps}

Les étapes de workflow suivantes sont prises en charge dans le Cloud Service.

* `com.day.cq.dam.similaritysearch.internal.workflow.process.AutoTagAssetProcess`
* `com.day.cq.dam.core.impl.process.CreateAssetLanguageCopyProcess`
* `com.day.cq.wcm.workflow.process.CreateVersionProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.StartTrainingProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.TransferTrainingDataProcess`
* `com.day.cq.dam.core.impl.process.TranslateAssetLanguageCopyProcess`
* `com.day.cq.dam.core.impl.process.UpdateAssetLanguageCopyProcess`
* `com.adobe.cq.workflow.replication.impl.ReplicationWorkflowProcess`
* `com.day.cq.dam.core.impl.process.DamUpdateAssetWorkflowCompletedProcess`

### Modèles non pris en charge ou remplacés {#unsupported-replaced-models}

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
