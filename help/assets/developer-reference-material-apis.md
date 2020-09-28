---
title: Références du développeur pour [!DNL Assets]
description: Les API [ ! Ressources DNL] et le contenu de référence du développeur vous permettent de gérer les ressources, y compris les fichiers binaires, les métadonnées, les rendus, les commentaires et les [!DNL Content Fragments]éléments.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 8b1cc8af67c6d12d7e222e12ac4ff77e32ec7e0e
workflow-type: tm+mt
source-wordcount: '1236'
ht-degree: 48%

---


# [!DNL Assets] API et matériel de référence pour les développeurs {#assets-cloud-service-apis}

L&#39;article contient du matériel de référence et des ressources pour les développeurs de [!DNL Assets] Cloud Service. Il comprend une nouvelle méthode de téléchargement, une référence à l’API et des informations sur la prise en charge fournie dans les workflows de post-traitement.

## Chargement de ressources {#asset-upload-technical}

[!DNL Experience Manager] as a Cloud Service fournit une nouvelle méthode pour télécharger des ressources vers le référentiel. Les utilisateurs peuvent directement télécharger les ressources vers l’enregistrement cloud à l’aide de l’API HTTP. Pour télécharger un fichier binaire, procédez comme suit :

1. [Envoyez une requête](#initiate-upload)HTTP. Il informe [!DNL Experience Manage]ou le déploiement de votre intention de télécharger un nouveau binaire.
1. [Publiez le contenu du fichier binaire sur un ou plusieurs URI fournis par la requête de lancement.](#upload-binary)
1. [Envoyez une requête HTTP pour informer le serveur que le contenu du fichier binaire a bien été chargé.](#complete-upload)

![Présentation du protocole de chargement binaire direct](assets/add-assets-technical.png)

Cette approche permet une gestion évolutive et plus performante des transferts de ressources. Les différences par rapport à [!DNL Experience Manager] 6,5 sont les suivantes :

* Binaries do not go through [!DNL Experience Manager], which is now simply coordinating the upload process with the binary cloud storage configured for the deployment.
* L’enregistrement cloud binaire fonctionne avec un réseau CDN (Content Diffusion Network) ou Edge. Un CDN sélectionne un point de terminaison de transfert plus proche pour un client. Lorsque les données parcourent une distance plus courte jusqu’à un point de terminaison voisin, les performances de transfert et l’expérience utilisateur s’améliorent, en particulier pour les équipes géographiquement réparties.

>[!NOTE]
>
>Voir le code client pour implémenter cette approche dans la bibliothèque [de téléchargement](https://github.com/adobe/aem-upload)aem open source.

### Lancement du chargement {#initiate-upload}

Envoyez une demande de POST HTTP au dossier de votre choix. Les ressources sont créées ou mises à jour dans ce dossier. Incluez le sélecteur `.initiateUpload.json` pour indiquer que la demande doit lancer le téléchargement d’un fichier binaire. For example, the path to the folder where the asset should be created is `/assets/folder`. La demande du POST est `POST https://[aem_server]:[port]/content/dam/assets/folder.initiateUpload.json`.

Le corps de la requête doit être constitué de données de formulaire `application/x-www-form-urlencoded`, contenant les champs suivants :

* `(string) fileName` : obligatoire. Nom du fichier tel qu’il apparaît dans [!DNL Experience Manager].
* `(number) fileSize` : obligatoire. Taille de fichier, en octets, de la ressource en cours de téléchargement.

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

* `completeURI` (chaîne) : Appelez cet URI lorsque le chargement du fichier binaire est terminé. Il peut s’agir d’un URI absolu ou relatif, et les clients doivent être en mesure de gérer l’un ou l’autre. En d’autres termes, la valeur peut être `"https://author.acme.com/content/dam.completeUpload.json"` ou `"/content/dam.completeUpload.json"` ; voir [Fin du chargement](#complete-upload).
* `folderPath` (chaîne) : Chemin d’accès complet au dossier dans lequel le fichier binaire est téléchargé.
* `(files)` (tableau) : Liste d’éléments dont la longueur et l’ordre correspondent à la longueur et à l’ordre de la liste des informations binaires fournies dans la demande de lancement.
* `fileName` (chaîne) : nom du fichier binaire correspondant, tel qu’il est fourni dans la requête de lancement. Cette valeur doit être incluse dans la requête de fin.
* `mimeType` (chaîne) : Type MIME du binaire correspondant, fourni dans la demande de lancement. Cette valeur doit être incluse dans la requête de fin.
* `uploadToken` (chaîne) : jeton de chargement du fichier binaire correspondant. Cette valeur doit être incluse dans la requête de fin.
* `uploadURIs` (tableau) : liste des chaînes dont les valeurs sont des URI complets vers lesquels le contenu du fichier binaire doit être chargé (voir [Chargement d’un fichier binaire](#upload-binary)).
* `minPartSize` (nombre) : longueur minimale, en octets, des données pouvant être fournies à l’un des URI de chargement, s’il en existe plusieurs.
* `maxPartSize` (nombre) : longueur maximale, en octets, des données pouvant être fournies à l’un des URI de chargement, s’il en existe plusieurs.

### Chargement d’un fichier binaire {#upload-binary}

La sortie de déclenchement d’un transfert comprend une ou plusieurs valeurs URI de transfert. Si plusieurs URI sont fournis, le client divise le binaire en parties et effectue la demande POST de chaque partie à chaque URI, dans l’ordre. Utilisez tous les URI. Assurez-vous que la taille de chaque pièce est inférieure aux tailles minimale et maximale spécifiées dans la réponse d’initialisation. Les noeuds CDN Edge permettent d’accélérer le téléchargement demandé de fichiers binaires.

Pour ce faire, il est possible de calculer la taille de la pièce en fonction du nombre d’URI de téléchargement fournis par l’API. Supposons, par exemple, que la taille totale du fichier binaire soit de 20 000 octets et que le nombre d’URI de téléchargement soit de 2. Procédez ensuite comme suit :

* Calculez la taille d’une pièce en divisant la taille totale par le nombre d’URI : 20 000 / 2 = 10 000.
* Publiez la plage d’octets 0 à 9 999 du binaire sur le premier URI de la liste des URI de chargement.
* Publiez la plage d’octets 10 000 à 19 999 du binaire sur le deuxième URI de la liste des URI de chargement.

If the upload is successful, the server responds to each request with a `201` status code.

### Fin du chargement {#complete-upload}

Après avoir téléchargé toutes les parties d’un fichier binaire, envoyez une requête HTTP POST à l’URI complet fourni par les données d’initialisation. Le corps de la requête doit être constitué de données de formulaire `application/x-www-form-urlencoded`, contenant les champs suivants.

| Champs | Type | Requis ou non | Description |
|---|---|---|---|
| `fileName` | Chaîne | Requis | Nom de la ressource, tel qu’il est fourni par les données de lancement. |
| `mimeType` | Chaîne | Requis | Type de contenu HTTP du binaire, tel qu’il est fourni par les données de lancement. |
| `uploadToken` | Chaîne | Requis | Jeton de chargement du binaire, tel qu’il est fourni par les données de lancement. |
| `createVersion` | Booléen | Facultatif | If `True` and an asset with the specified name exists, then [!DNL Experience Manager] creates a new version of the asset. |
| `versionLabel` | Chaîne | Facultatif | Si une version est créée, le libellé associé à la nouvelle version d’une ressource. |
| `versionComment` | Chaîne | Facultatif | Si une version est créée, les commentaires associés à la version. |
| `replace` | Booléen | Facultatif | If `True` and an asset with the specified name exists, [!DNL Experience Manager] deletes the asset then re-create it. |

>!![NOTE]
If the asset exists and neither `createVersion` nor `replace` is specified, then [!DNL Experience Manager] updates the asset&#39;s current version with the new binary.

Comme c’est le cas pour le processus de lancement, les données de la requête de fin peuvent contenir des informations pour plusieurs fichiers.

Le processus de chargement d’un binaire n’est pas terminé tant que l’URL complète n’est pas appelée pour le fichier. Une ressource est traitée une fois le processus de transfert terminé. Le traitement ne s’effectue pas même si le fichier binaire de la ressource est complètement téléchargé mais que le processus de téléchargement n’est pas terminé.

En cas de succès, le serveur répond avec un code d’état `200`.

### Bibliothèque de chargement Open Source {#open-source-upload-library}

Pour en savoir plus sur les algorithmes de téléchargement ou pour créer vos propres scripts et outils de téléchargement, Adobe fournit des bibliothèques et des outils open source :

* [Bibliothèque de chargement AEM Open Source](https://github.com/adobe/aem-upload).
* [Outil de ligne de commande Open Source](https://github.com/adobe/aio-cli-plugin-aem).

### API de chargement de ressources obsolètes {#deprecated-asset-upload-api}

<!-- #ENGCHECK review / update the list of deprecated APIs below. -->

La nouvelle méthode de téléchargement n’est prise en charge que pour [!DNL Adobe Experience Manager] un Cloud Service. Les API de la version [!DNL Adobe Experience Manager] 6.5 sont obsolètes. Les méthodes liées au chargement ou à la mise à jour de ressources ou de rendus (tout chargement de binaires) sont obsolètes dans les API suivantes :

* [API HTTP des ressources Experience Manager](mac-api-assets.md)
* API Java `AssetManager`, comme `AssetManager.createAsset(..)`

>[!MORELIKETHIS]
* [Bibliothèque de chargement AEM Open Source](https://github.com/adobe/aem-upload).
* [Outil de ligne de commande Open Source](https://github.com/adobe/aio-cli-plugin-aem).


## Workflows de traitement et de post-traitement des ressources {#post-processing-workflows}

In [!DNL Experience Manager], the asset processing is based on **[!UICONTROL Processing Profiles]** configuration that uses [asset microservices](asset-microservices-configure-and-use.md#get-started-using-asset-microservices). Le traitement ne nécessite pas d’extensions de développeur.

Pour la configuration du workflow de post-traitement, utilisez les workflows standard avec des extensions pour les étapes personnalisées.

## Prise en charge des étapes d’un workflow de post-traitement {#post-processing-workflows-steps}

Les clients effectuant une mise à niveau à partir de versions précédentes de peuvent utiliser des microservices de ressources pour traiter des ressources. [!DNL Experience Manager] Les microservices de ressources natifs en mode cloud sont beaucoup plus simples à configurer et à utiliser. Certaines étapes appliquées dans le workflow [!UICONTROL Ressource de mise à jour de la gestion des actifs numériques] de la version précédente ne sont pas prises en charge.

[!DNL Experience Manager] en tant que Cloud Service prend en charge les étapes de processus suivantes :

* `com.day.cq.dam.similaritysearch.internal.workflow.process.AutoTagAssetProcess`
* `com.day.cq.dam.core.impl.process.CreateAssetLanguageCopyProcess`
* `com.day.cq.wcm.workflow.process.CreateVersionProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.StartTrainingProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.TransferTrainingDataProcess`
* `com.day.cq.dam.core.impl.process.TranslateAssetLanguageCopyProcess`
* `com.day.cq.dam.core.impl.process.UpdateAssetLanguageCopyProcess`
* `com.adobe.cq.workflow.replication.impl.ReplicationWorkflowProcess`
* `com.day.cq.dam.core.impl.process.DamUpdateAssetWorkflowCompletedProcess`

Les modèles de workflow techniques suivants ont été remplacés par des microservices de ressources ou la prise en charge n’est pas disponible:

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

>[!MORELIKETHIS]
* [L’Experience Cloud en tant que SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)Cloud Service.

