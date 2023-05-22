---
title: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2023.03.0
description: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.03.0
feature: Release Information
exl-id: 2f787321-f156-480d-bbe8-1a6d04f110c5
source-git-commit: b2681113f5565e4f63c76abeaf46d5f4b1a8a8ea
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 100%

---

# Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2023.03.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2022.03.0.

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de l’analyseur de bonnes pratiques v2.1.40 est le 03 mars 2023.

### Nouveautés {#what-is-new-bpa}

* BPA peut désormais détecter et générer des rapports sur les nœuds en conflit - nœuds ayant le même `jcr:uuid`. Ces résultats sont considérés comme critiques, car ils peuvent entraîner des problèmes d’ingestion de contenu lors du déplacement du contenu vers AEM as a Cloud Service.
* BPA peut désormais détecter et générer des rapports sur l’utilisation des écouteurs d’événements. Il est recommandé de refactoriser ce type de mécanisme de gestion des événements en tâches sling lors du transfert vers AEM as a Cloud Service.

### Correctifs {#bug-fixes-bpa}

* BPA signalait des faux positifs sur `grouprendercondition`. Ce problème a été résolu.

## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu version v2.0.16 est le 08 mars 2022.

### Nouveautés {#what-is-new-ctt}

* Le mappage des utilisateurs et utilisatrices a été rationnalisé et intégré à l’étape d’extraction de contenu. Aucune configuration n’est nécessaire et le mappage utilisateur est effectué automatiquement par défaut lorsque l’utilisateur ou l’utilisatrice lance l’extraction de contenu. L’utilisateur ou l’utilisatrice a la possibilité de désactiver le mappage utilisateur en cas de besoin. En savoir plus [ici.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/user-mapping-and-migration.html?lang=fr#user-mapping-detail)
* L’étape de précopie à l’aide d’[AzCopy](https://learn.microsoft.com/fr-fr/azure/storage/common/storage-use-azcopy-v10) a été intégrée à l’outil de transfert de contenu pour accélérer considérablement les extractions de contenu. La précopie est automatiquement configurée et installée lorsque cette version de l’outil de transfert de contenu est installée. Par défaut, lorsque l’extraction est lancée, la précopie s’exécute automatiquement pour les jeux de migration de plus de 200 Go. L’utilisateur ou l’utilisatrice a la possibilité de la désactiver si nécessaire. En savoir plus [ici.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=fr)
* L’outil de transfert de contenu peut désormais être utilisé sur les serveurs Windows.

### Correctifs {#bug-fixes-ctt}

* Plusieurs correctifs permettent d’améliorer la résilience de l’extraction de contenu.
