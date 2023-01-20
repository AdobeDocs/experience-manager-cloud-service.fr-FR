---
title: Gestion des référentiels de contenu volumineux
description: Cette section décrit la gestion des référentiels de contenu volumineux
exl-id: 21bada73-07f3-4743-aae6-2e37565ebe08
source-git-commit: 7a9c601dd42aed9fbd0113e71c1c7a58b5bba8f7
workflow-type: ht
source-wordcount: '1732'
ht-degree: 100%

---

# Gestion des référentiels de contenu volumineux {#handling-large-content-repositories}

## Présentation {#overview}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_precopy"
>title="Gestion des référentiels de contenu volumineux"
>abstract="Pour accélérer considérablement les phases d’extraction et d’ingestion de l’activité de transfert de contenu afin de déplacer le contenu vers AEM as a Cloud Service, le CTT peut utiliser AzCopy comme étape de pré-copie facultative. Une fois cette étape préalable configurée, dans la phase d’extraction, AzCopy copie les blobs d’Amazon S3 ou Azure Blob Storage vers la boutique blob du jeu de migration. Au cours de la phase d’ingestion, AzCopy copie les objets blob de la boutique blob du jeu de migration vers la boutique blob d‘AEM as a Cloud Service."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=fr#setting-up-pre-copy-step" text="Prise en main d’étape AzCopy en tant qu’étape de pré-copie"

La copie d’un grand nombre d’objets Blob avec l’outil de transfert de contenu (CTT) peut prendre plusieurs jours.
Pour accélérer considérablement les phases d’extraction et d’ingestion de l’activité de transfert de contenu afin de déplacer le contenu vers AEM as a Cloud Service, le CTT peut utiliser [AzCopy](https://docs.microsoft.com/fr-fr/azure/storage/common/storage-use-azcopy-v10) comme étape de pré-copie facultative. Cette étape de pré-copie peut être utilisée lorsque l’instance AEM source est configurée pour utiliser une banque de données Amazon S3, Azure Blob Storage ou File Data Store. L’étape de précopie est la plus efficace pour la première occurrence complète d’extraction et d’ingestion. Toutefois, l’utilisation de la précopie pour les complément ultérieurs n’est pas recommandée (si la taille du complément est inférieure à 200 Go), car cela peut allonger la durée de l’ensemble du processus. Une fois cette étape préalable configurée, dans la phase d’extraction, AzCopy copie les objets blob d’Amazon S3, d’Azure Blob Storage ou du File Data Store vers le magasin d’objets blob du jeu de migration. Au cours de la phase d’ingestion, AzCopy copie les objets blob de la boutique blob du jeu de migration vers la boutique blob d‘AEM as a Cloud Service.

## Points importants avant de commencer {#important-considerations}

Consultez la section ci-dessous pour comprendre les points importants à prendre en compte avant de commencer :

* La version d’AEM source doit être 6.3 à 6.5..

* L’entrepôt de données d’AEM source est configuré pour utiliser Amazon S3 ou Azure Blob Storage. Pour plus d’informations, voir [Configuration des entrepôts de nœuds et de données dans AEM 6](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html?lang=fr).

* Chaque jeu de migration copiera l’ensemble de l’entrepôt de données. Par conséquent, un seul jeu de migration doit être utilisé.

* Vous devez accéder à [AzCopy](https://docs.microsoft.com/fr-fr/azure/storage/common/storage-use-azcopy-v10) sur l’instance (ou la machine virtuelle) exécutant l’instance AEM source.

* Le nettoyage de la mémoire d’entrepôt de données a été exécuté au cours des 7 jours précédents sur la source. Pour plus d’informations, voir [Récupération de l’espace mémoire de l’entrepôt de données](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html?lang=fr#data-store-garbage-collection).


### Considérations supplémentaires si l’instance d’AEM source est configurée pour utiliser une banque de données Amazon S3 ou Azure Blob Storage. {#additional-considerations-amazons3-azure}

* Comme le transfert de données en dehors de Amazon S3 et du stockage Blob Azure entraîne un coût, le coût du transfert sera relatif à la quantité totale de données dans votre conteneur de stockage existant (qu’il soit référencé dans AEM ou non). Pour plus d’informations, voir [Amazon S3](https://aws.amazon.com/s3/pricing/) et [Stockage Blob Azure](https://azure.microsoft.com/fr-fr/pricing/details/bandwidth/).

* Vous aurez besoin soit d’une clé d’accès et d’une clé secrète pour le compartiment source Amazon S3 existant, soit d’un URI SAS pour le conteneur de stockage Blob Azure existant (l’accès en lecture seule est correct).

### Considérations supplémentaires si l’instance d’AEM source est configurée pour utiliser le File Data Store. {#additional-considerations-aem-instance-filedatastore}

* Le système local doit disposer d’un espace libre strictement supérieur à 1/256 taille de la banque de données source. Par exemple, si la taille de la banque de données est de 3 To, l’espace libre supérieur à 11,72 Go doit exister dans le fichier `crx-quickstart/cloud-migration` sur la source pour que AzCopy fonctionne. Au minimum, le système source doit disposer de 1 Go d’espace libre. Il est possible d’obtenir de l’espace libre en utilisant la commande `df -h` sur les instances Linux ou la commande DIR dans les instances Windows.

* Chaque fois que l’extraction est exécutée avec AzCopy activé, la banque de données de l’ensemble du fichier est aplatie et copiée dans le conteneur de migration dans le cloud. Si votre jeu de migration est beaucoup plus petit que la taille de votre banque de données, l’extraction AzCopy n’est pas l’approche optimale.

* Une fois que l’option AzCopy a été utilisée pour copier sur le magasin de données existant, désactivez-la pour les extractions delta ou de compléments.

## Configuration pour utiliser AzCopy en tant qu’étape de pré-copie {#setting-up-pre-copy-step}

Consultez cette section pour savoir comment configurer l’utilisation d’AzCopy en tant qu’étape de pré-copie avec l’outil de transfert de contenu afin de migrer le contenu vers AEM as a Cloud Service :

### 0. Déterminer la taille totale de tout le contenu de l’entrepôt de données {#determine-total-size}

Il est important de déterminer la taille totale de la banque de données pour deux raisons :

* Si l’AEM source est configuré pour utiliser File Data Store, le système local doit disposer d’un espace libre strictement supérieur à 1/256 de la taille de la banque de données source.

#### Entrepôt de données du stockage Blob Azure {#azure-blob-storage}

Sur la page des propriétés du conteneur existant du portail Azure, utilisez le bouton **Calculer la taille** pour déterminer la taille de tout le contenu du conteneur. Par exemple :

![image](/help/journey-migration/content-transfer-tool/assets/Azure-blob-storage-data-store.png)

#### Entrepôt de données S3 Amazon {#amazon-data}

Vous pouvez utiliser l’onglet Mesures du conteneur pour déterminer la taille de tout le contenu du conteneur. Par exemple :


![image](/help/journey-migration/content-transfer-tool/assets/amazon-s3-data-store.png)

#### Banque de données Fichier {#file-data-store-determine-size}

* Pour mac, systèmes UNIX, exécutez la commande du sur le répertoire de la banque de données pour obtenir sa taille :
   `du -sh [path to datastore on the instance]`. Par exemple, si votre banque de données se trouve à l’adresse `/mnt/author/crx-quickstart/repository/datastore`, la commande suivante vous permet d’obtenir sa taille : `du -sh /mnt/author/crx-quickstart/repository/datastore`.

* Pour Windows, utilisez la commande DIR du répertoire de la banque de données pour obtenir sa taille :
   `dir /a/s [location of datastore]`.

### 1. Installez AzCopy {#install-azcopy}

[AzCopy](https://docs.microsoft.com/fr-fr/azure/storage/common/storage-use-azcopy-v10) est un outil de ligne de commande fourni par Microsoft qui doit être disponible sur l’instance source pour activer cette fonctionnalité.

En résumé, vous voudrez probablement télécharger le binaire Linux x86-64 à partir de la [page de documents AzCopy](https://docs.microsoft.com/fr-fr/azure/storage/common/storage-use-azcopy-v10) et le décompresser à un emplacement tel que /usr/bin.

>[!IMPORTANT]
>Prenez note de l’emplacement auquel vous avez placé le fichier binaire, car vous aurez besoin du chemin d’accès complet pour celui-ci à une étape ultérieure.

### 2. Installez une version de l’outil de transfert de contenu (CTT) avec la prise en charge d’AzCopy. {#install-ctt-azcopy-support}

>[!IMPORTANT]
>La version la plus récente de CTT doit être utilisée.

La prise en charge d’AzCopy pour Amazon S3, le stockage Blob Azure et File Data Store est incluse dans la dernière version de CTT.
Vous pouvez télécharger la dernière version du CTT à partir du portail [Distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).


### 3. Configuration d’un fichier azcopy.config. {#configure-azcopy-config-file}

Sur l’instance AEM source, dans `crx-quickstart/cloud-migration`, créez un nouveau fichier appelé `azcopy.config`.

>[!NOTE]
>Le contenu de ce fichier de configuration sera différent selon que votre instance AEM source utilise un entrepôt de données Azure ou Amazon S3 ou un File Data Store.

#### Entrepôt de données de stockage Azure Blob {#azure-blob-storage-data}

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

#### Banque de données Fichier {#file-data-store-azcopy-config}

Votre fichier `azcopy.config` doit contenir la propriété azCopyPath, ainsi qu’une propriété facultative repository.home qui pointe vers l’emplacement du magasin de données de fichiers. Utilisez les valeurs correctes pour votre instance.
Banque de données Fichier

```
azCopyPath=/usr/bin/azcopy
repository.home=/mnt/crx/author/crx-quickstart/repository/datastore
```

La propriété azCopyPath doit contenir le chemin d’accès complet de l’emplacement où l’outil de ligne de commande azCopy est installé sur l’instance d’AEM source. Si la propriété azCopyPath est manquante, l’étape de pré-copie Blob n’est pas exécutée.

Si la propriété `repository.home` est manquante dans azcopy.config, alors l’emplacement par défaut de la banque de données `/mnt/crx/author/crx-quickstart/repository/datastore` sera utilisé pour effectuer la précopie.

### 4. Extraction avec AzCopy {#extracting-azcopy}

Une fois le fichier de configuration ci-dessus en place, la phase de pré-copie AzCopy s’exécute dans le cadre de chaque extraction ultérieure. Pour l’empêcher d’exécuter, vous pouvez renommer ce fichier ou le supprimer.

>[!NOTE]
>Si AzCopy n’est pas configuré correctement, ce message s’affiche dans les journaux :
>`INFO c.a.g.s.m.c.a.AzCopyCloudBlobPreCopy - Blob pre-copy is not supported`.

1. Commencez une extraction à partir de l’interface utilisateur de CTT. Pour plus d’informations, consultez [Prise en main de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=fr) et [Processus d’extraction](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/extracting-content.html?lang=fr).

1. Vérifiez que la ligne suivante est imprimée dans le journal d’extraction :

```
c.a.g.s.m.commons.ContentExtractor - *************** Beginning AzCopy Pre-Copy phase ***************
```

Félicitations ! Cette entrée de journal signifie que votre configuration a été considérée comme valide et qu’AzCopy copie actuellement tous les objets Blob du conteneur source vers le conteneur de migration.

Les entrées de journal d’AzCopy apparaissent dans le journal d’extraction et sont précédées du préfixe c.a.g.s.m.c.azcopy.AzCopyBlobPreCopy - [Pré-copie AzCopy]

>[!CAUTION]
>
> Pendant les premières minutes d’une extraction, regardez attentivement les logs d’extraction pour savoir s’il y a un problème. Par exemple, voici ce qui serait consigné si le conteneur Azure source était introuvable :

```
[AzCopy pre-copy] failed to perform copy command due to error: cannot start job due to error: cannot list files due to reason -> github.com/Azure/azure-storage-blob-go/azblob.newStorageError, github.com/Azure/azure-storage-blob-go@v0.10.1-0.20210407023846-16cf969ec1c3/azblob/zc_storage_error.go:42
[AzCopy pre-copy] ===== RESPONSE ERROR (ServiceCode=ContainerNotFound) =====
[AzCopy pre-copy] Description=The specified container does not exist.
[AzCopy pre-copy] RequestId:5fb674b9-201e-001b-2a5b-527400000000
[AzCopy pre-copy] Time:2021-05-26T18:18:07.5931967Z, Details: 
[AzCopy pre-copy] Code: ContainerNotFound
```

En cas de problème avec AzCopy, l’extraction échoue immédiatement et les logs d’extraction contiennent des détails sur l’échec.

Les objets Blob qui ont été copiés avant l’erreur seront automatiquement ignorés par AzCopy lors des exécutions suivantes et n’auront pas besoin d’être copiés à nouveau.

#### Pour File Data Store {#file-data-store-extract}

Lorsque AzCopy est en cours d’exécution pour le fichier source dataStore, vous devriez voir des messages comme ceux-ci dans les journaux indiquant que les dossiers sont en cours de traitement :
`c.a.g.s.m.c.a.AzCopyFileSourceBlobPreCopy - [AzCopy pre-copy] Processing folder (1/24) crx-quickstart/repository/datastore/5d`

### 5. Ingestion avec AzCopy {#ingesting-azcopy}

Consultez la section [Ingérer du contenu dans Target](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/ingesting-content.html?lang=fr)
pour obtenir des informations générales sur l’ingestion de contenu dans Target à partir de Cloud Acceleration Manager (CAM), y compris des
instructions sur l’utilisation d’AzCopy (pré-copie), ou non, dans la boîte de dialogue « Nouvelle ingestion ».

Pour tirer parti d’AzCopy lors de l’ingestion, AEM as a Cloud Service version 2021.6.5561 ou ultérieure est nécessaire.

Consultez la liste « Tâches d’ingestion » dans Cloud Acceleration  Manager et les journaux d’ingestion pour voir la progression.  Les entrées de journal concernant les tâches AzCopy réussies s’affichent comme suit (sous réserve de quelques différences). La consultation périodique des journaux peut vous alerter d’un problème dès son apparition et vous permettre d’apporter une solution rapide.

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

## Prochaines étapes {#whats-next}

Une fois que vous avez appris à gérer les référentiels de contenu volumineux afin d’accélérer considérablement les phases d’extraction et d’ingestion de l’activité de transfert de contenu et déplacer le contenu vers AEM as a Cloud Service, vous êtes prêt à apprendre comment fonctionne le processus d’extraction à l’aide de l’outil de transfert de contenu. Consultez [Extraction de contenu de la source dans l’outil de transfert de contenu](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md) pour savoir comment extraire votre jeu de migration à partir de l’outil de transfert de contenu.
