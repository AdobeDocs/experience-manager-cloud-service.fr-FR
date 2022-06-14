---
title: Dépannage de l’outil de transfert de contenu (Legacy)
description: Dépannage de l’outil de transfert de contenu
hide: true
hidefromtoc: true
exl-id: b99f8f2b-b1b7-4ec1-b1d2-0efe83e17e91
source-git-commit: 22bbf15e33ab3d5608dc01ed293bb04b07cb6c8c
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 100%

---

# Dépannage de l’outil de transfert de contenu (Hérité) {#troubleshoot-content-transfer-tool}


## ID d’objets blob manquants {#missing-blobs}

Si l’absence d’ID d’objets blob est signalée, comme indiqué ci-dessous, il est nécessaire d’exécuter une vérification de cohérence du référentiel existant et de restaurer les blobs manquants.
`ERROR o.a.j.o.p.b.AbstractSharedCachingDataStore - Error retrieving record [ba45c53f8b687e7056c85dceebf8156a0e6abc7e]`

La commande suivante est exécutée

>[!NOTE]
>
>`--verbose`(indicateur) est nécessaire pour signaler les chemins d’accès aux nœuds permettant de référencer les objets blob.

**Pour les référentiels AEM 6.5 (Oak 1.8 et versions antérieures)**

```shell
java -jar oak-run.jar datastorecheck --consistency --store [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds] <DATASTORE_CFG> --verbose <OUT_DIR> --dump
```

**Pour les référentiels dotés d’Oak > 1.10**

```shell
java -jar oak-run.jar datastore --check-consistency [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds|azureds] <DATASTORE_CFG> --out-dir <OUT_DIR> --work-dir <TEMP_DIR> --verbose
```

Pour plus d’informations, voir [Fichier jar exécutable Oak](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run).

Les fichiers créés dans *OUT_DIR*, spécifiés ci-dessus pour assurer la cohérence, peuvent ensuite être vérifiés pour détecter les chemins manquants de binaires et les actions appropriées mises en œuvre (restauration à partir d’une sauvegarde, suppression des chemins, réindexation, etc.).


## Comportement de l’interface utilisateur {#ui-behavior}

En tant qu’utilisateur, il est possible que vous constatiez les changements de comportement suivants dans l’interface utilisateur de l’outil de transfert de contenu :

* Selon la version de l’instance AEM source, les icônes de l’interface utilisateur de l’outil de transfert de contenu peuvent apparaître sous des formes différentes des captures d’écran de ce guide ou ne pas apparaître du tout.
