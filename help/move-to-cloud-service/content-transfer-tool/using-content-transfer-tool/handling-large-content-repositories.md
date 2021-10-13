---
title: Gestion des référentiels de contenu volumineux
description: Cette section décrit la gestion des référentiels de contenu volumineux
exl-id: 2eca7fa6-fb34-4b08-b3ec-4e9211e94275
source-git-commit: 65847fc03770fe973c3bfee4a515748f7e487ab6
workflow-type: tm+mt
source-wordcount: '1282'
ht-degree: 1%

---

# Gestion des référentiels de contenu volumineux {#handling-large-content-repositories}

## Présentation {#overview}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_precopy"
>title="Gestion des référentiels de contenu volumineux"
>abstract="Pour accélérer considérablement les phases d’extraction et d’ingestion de l’activité de transfert de contenu afin de déplacer le contenu vers AEM as a Cloud Service, CTT peut utiliser AzCopy en tant qu’étape de précopie facultative. Une fois cette étape préalable configurée, dans la phase d’extraction, AzCopy copie les blobs d’Amazon S3 ou Azure Blob Storage vers le magasin blob du jeu de migration. Au cours de la phase d’ingestion, AzCopy copie les objets blob de la banque de paramètres blob du jeu de migration vers la banque d’objets blob as a Cloud Service de l’AEM de destination."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en#setting-up-pre-copy-step" text="Prise en main de l’étape AzCopy en tant que pré-copie"

La copie d’un grand nombre de objets Blob avec l’outil de transfert de contenu (CTT) peut prendre plusieurs jours.
Pour accélérer considérablement les phases d’extraction et d’ingestion de l’activité de transfert de contenu afin de déplacer le contenu vers AEM as a Cloud Service, CTT peut utiliser [AzCopy](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) comme étape de précopie facultative. Cette étape de précopie peut être utilisée lorsque l’instance d’AEM source est configurée pour utiliser un entrepôt de données Amazon S3 ou Azure Blob Storage.  Une fois cette étape préalable configurée, dans la phase d’extraction, AzCopy copie les blobs d’Amazon S3 ou Azure Blob Storage vers le magasin blob du jeu de migration. Au cours de la phase d’ingestion, AzCopy copie les objets blob de la banque de paramètres blob du jeu de migration vers la banque d’objets blob as a Cloud Service de l’AEM de destination.

>[!NOTE]
> Cette fonctionnalité a été introduite dans la version 1.5.4 de CTT.

## Points importants avant de commencer {#important-considerations}

Consultez la section ci-dessous pour comprendre les points importants à prendre en compte avant de commencer :

* La version d’AEM source doit être 6.3 à 6.5.
* Le magasin de données d’AEM source est configuré pour utiliser Amazon S3 ou Azure Blob Storage. Pour plus d’informations, voir [Configuration des entrepôts de noeuds et de données dans AEM 6](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html?lang=en).
* L’ensemble de l’entrepôt de données sera copié pendant l’extraction. Comme le transfert de données en dehors du stockage Blob Amazon S3 et Azure entraîne un coût, le coût du transfert sera relatif à la quantité totale de données dans le conteneur de stockage (qu’il soit référencé dans AEM ou non). Pour plus d’informations, voir [Amazon S3](https://aws.amazon.com/s3/pricing/) et [Azure Blob Storage](https://azure.microsoft.com/en-us/pricing/details/bandwidth/).
* Chaque jeu de migration copiera l’ensemble de l’entrepôt de données. Par conséquent, un seul jeu de migration doit être utilisé.
* Vous devez accéder à [AzCopy](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) sur l’instance (ou la machine virtuelle) exécutant l’instance d’AEM source.
* Vous aurez besoin soit d’une paire clé d’accès et clé secrète pour le compartiment source Amazon S3, soit d’un URI SAS pour le conteneur de stockage Azure Blob (l’accès en lecture seule est correct).
* Le nettoyage de la mémoire d’entrepôt de données a été exécuté au cours des 7 jours précédents sur la source. Pour plus d’informations, voir [Nettoyage de la mémoire d’entrepôt de données](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html?lang=en#data-store-garbage-collection).
* La majorité des données de l’instance source seront incluses dans la migration.

## Configuration pour utiliser AzCopy en tant qu’étape de précopie {#setting-up-pre-copy-step}

Consultez cette section pour savoir comment configurer l’utilisation d’AzCopy comme étape de précopie avec l’outil de transfert de contenu afin de migrer le contenu vers AEM as a Cloud Service :

### 0. Déterminer la taille totale de tout le contenu de l’entrepôt de données {#determine-total-size}

#### Stockage de données Azure Blob {#azure-blob-storage}

Sur la page des propriétés du conteneur du portail Azure, utilisez le bouton **Calculer la taille** pour déterminer la taille de tout le contenu du conteneur. Par exemple :

![image](/help/move-to-cloud-service/content-transfer-tool/assets/Azure-blob-storage-data-store.png)

#### Entrepôt de données S3 Amazon {#amazon-data}

Vous pouvez utiliser l’onglet Mesures du conteneur pour déterminer la taille de tout le contenu du conteneur. Par exemple :


![image](/help/move-to-cloud-service/content-transfer-tool/assets/amazon-s3-data-store.png)

### 1. Installez AzCopy {#install-azcopy}

[](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) AzCopyest un outil de ligne de commande fourni par Microsoft qui doit être disponible sur l’instance source pour activer cette fonctionnalité.

En résumé, vous voudrez probablement télécharger le binaire Linux x86-64 à partir de la [page de documents AzCopy](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) et le décompresser à un emplacement tel que /usr/bin. Prenez note de l’emplacement où vous avez placé le fichier binaire, car vous aurez besoin du chemin d’accès complet pour celui-ci à une étape ultérieure.

### 2. Installez une version de l’outil de transfert de contenu (CTT) avec la prise en charge d’AzCopy. {#install-ctt-azcopy-support}

La prise en charge d’AzCopy est incluse dans la version 1.5.4 de CTT. Vous pouvez télécharger la dernière version de CTT à partir du portail [Distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

### 3. Configuration d’un fichier azcopy.config {#configure-azcopy-config-file}

Sur l’instance d’AEM source, dans `crx-quickstart/cloud-migration`, créez un fichier appelé azcopy.config .

Le contenu de ce fichier de configuration sera différent selon que votre instance d’AEM source utilise un entrepôt de données Azure ou Amazon S3.

#### Stockage de données Azure Blob {#azure-blob-storage-data}

Votre fichier azcopy.config doit inclure les propriétés suivantes (veillez à utiliser les azCopyPath et azureSas corrects pour votre instance).

>[!NOTE]
>
> Si vous ne souhaitez pas accorder l’accès en écriture au conteneur de stockage blob, vous pouvez générer un nouvel URI SAS qui ne dispose que des autorisations de lecture et de liste.

```
azCopyPath=/usr/bin/azcopy
azureSas=https://example-resource.blob.core.windows.net/example-container?sig=--REDACTED--
```

#### Entrepôt de données S3 Amazon {#amazon-sdata-store}

Votre fichier azcopy.config doit inclure les propriétés suivantes (veillez à utiliser les valeurs correctes pour votre instance).

>[!NOTE]
>
> Si votre instance utilise des rôles IAM pour permettre à AEM d’accéder à S3, vous devez créer une stratégie et un utilisateur avec les actions ListBucket et GetObject activées pour le compartiment S3. Une fois configuré, utilisez la clé d’accès et la clé secrète de cet utilisateur.

```
azCopyPath=/usr/bin/azcopy
s3Bucket=aem-63
s3Region=us-west-2
s3AccessKey=--REDACTED--
s3SecretKey=--REDACTED--
```

### 4. Extraction avec AzCopy {#extracting-azcopy}

Une fois le fichier de configuration ci-dessus en place, la phase de précopie AzCopy s’exécute dans le cadre de chaque extraction ultérieure. Pour l’empêcher d’exécuter, vous pouvez renommer ce fichier ou le supprimer.

1. Commencez une extraction à partir de l’interface utilisateur de CTT. Pour plus d’informations, voir [Prise en main de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=en) et [Processus d’extraction](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/extracting-content.html?lang=en) .

1. Vérifiez que la ligne suivante est imprimée dans le journal d&#39;extraction :

```
c.a.g.s.m.commons.ContentExtractor - *************** Beginning AzCopy Pre-Copy phase ***************
```

Félicitations ! Cette entrée de journal signifie que votre configuration a été considérée comme valide et qu’AzCopy copie actuellement tous les objets Blob du conteneur source vers le conteneur de migration.

Les entrées de journal d’AzCopy apparaissent dans le journal d’extraction et sont précédées du préfixe c.a.g.s.m.c.azcopy.AzCopyBlobPreCopy - [Pré-copie AzCopy]

>[!CAUTION]
>
> Pendant les premières minutes d&#39;une extraction, regardez attentivement les logs d&#39;extraction pour savoir s&#39;il y a un problème. Par exemple, voici ce qui serait consigné si le conteneur Azure source est introuvable :

```
[AzCopy pre-copy] failed to perform copy command due to error: cannot start job due to error: cannot list files due to reason -> github.com/Azure/azure-storage-blob-go/azblob.newStorageError, github.com/Azure/azure-storage-blob-go@v0.10.1-0.20210407023846-16cf969ec1c3/azblob/zc_storage_error.go:42
[AzCopy pre-copy] ===== RESPONSE ERROR (ServiceCode=ContainerNotFound) =====
[AzCopy pre-copy] Description=The specified container does not exist.
[AzCopy pre-copy] RequestId:5fb674b9-201e-001b-2a5b-527400000000
[AzCopy pre-copy] Time:2021-05-26T18:18:07.5931967Z, Details: 
[AzCopy pre-copy] Code: ContainerNotFound
```

En cas de problème avec AzCopy, l&#39;extraction échoue immédiatement et les logs d&#39;extraction contiennent des détails sur l&#39;échec.

Les objets Blob qui ont été copiés avant l’erreur seront automatiquement ignorés par AzCopy lors des exécutions suivantes et n’auront pas besoin d’être copiés à nouveau.

### 5. Ingestion avec AzCopy {#ingesting-azcopy}

Avec la version 1.5.4 de l’outil de transfert de contenu, nous avons ajouté la prise en charge d’AzCopy à l’ingestion par auteur.

>[!NOTE]
>Il est recommandé d’exécuter l’ingestion par l’auteur en premier. Cela permettra d’accélérer l’ingestion de publication lorsqu’elle est exécutée ultérieurement.

Pour tirer parti d’AzCopy lors de l’ingestion, nous vous demandons d’utiliser une version as a Cloud Service AEM qui est au moins la version 2021.6.5561.

Commencez l’ingestion de l’auteur à partir de l’interface utilisateur de CTT. Pour plus d’informations, voir [Processus d’ingestion](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/ingesting-content.html?lang=en) .
Les entrées de journal d’AzCopy apparaissent dans le journal d’ingestion. Ils ressembleront à ceci :

```
*************** Beginning AzCopy pre-copy phase ***************
INFO: Scanning...
INFO: Failed to create one or more destination container(s). Your transfers may still succeed if the container already exists.
INFO: Any empty folders will not be processed, because source and/or destination doesn't have full folder support
INFO: azcopy: A newer version 10.11.0 is available to download
 
 
Job 419d98da-fc05-2a45-70cc-797fee632031 has started
Log file is located at: /root/.azcopy/419d98da-fc05-2a45-70cc-797fee632031.log
 
 
0.0 %, 0 Done, 0 Failed, 886 Pending, 0 Skipped, 886 Total,
 
 
Job 419d98da-fc05-2a45-70cc-797fee632031 summary
Elapsed Time (Minutes): 0.0334
Number of File Transfers: 886
Number of Folder Property Transfers: 0
Total Number of Transfers: 886
Number of Transfers Completed: 17
Number of Transfers Failed: 0
Number of Transfers Skipped: 869
TotalBytesTransferred: 248350
Final Job Status: CompletedWithSkipped
 
*************** Completed AzCopy pre-copy phase ***************
```

## Et après ? {#whats-next}

Une fois que vous avez appris à gérer les référentiels de contenu volumineux afin d’accélérer considérablement les phases d’extraction et d’ingestion de l’activité de transfert de contenu pour déplacer le contenu vers AEM as a Cloud Service, vous êtes prêt à apprendre le processus d’extraction dans l’outil de transfert de contenu. Voir [Extraction de contenu de la source dans l’outil de transfert de contenu](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool/extracting-content.md) pour savoir comment extraire votre jeu de migration de l’outil de transfert de contenu.