---
title: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2023.03.0
description: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2023.03.0
feature: Release Information
exl-id: cdc57cca-e10a-4b0d-b803-910ccc9350a6
role: Admin
source-git-commit: fecbebde808c545a84889da5610a79c088f2f459
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 95%

---

# Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2023.03.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2023.03.0.

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

La date de publication de l’outil de transfert de contenu version v2.0.16 est le jeudi 8 mars 2023.

### Nouveautés {#what-is-new-ctt}

* Le mappage des utilisateurs et utilisatrices a été rationnalisé et intégré à l’étape d’extraction de contenu. Aucune configuration n’est nécessaire et le mappage utilisateur est effectué automatiquement par défaut lorsque l’utilisateur ou l’utilisatrice lance l’extraction de contenu. L’utilisateur a la possibilité de désactiver le mappage des utilisateurs si nécessaire.
* L’étape de précopie à l’aide d’[AzCopy](https://learn.microsoft.com/fr-fr/azure/storage/common/storage-use-azcopy-v10) a été intégrée à l’outil de transfert de contenu pour accélérer considérablement les extractions de contenu. La précopie est automatiquement configurée et installée lorsque cette version de l’outil de transfert de contenu est installée. Par défaut, lorsque l’extraction est lancée, la précopie s’exécute automatiquement pour les jeux de migration de plus de 200 Go. L’utilisateur ou l’utilisatrice a la possibilité de la désactiver si nécessaire. En savoir plus [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/handling-large-content-repositories.html).
* L’outil de transfert de contenu peut désormais être utilisé sur les serveurs Windows.

### Correctifs {#bug-fixes-ctt}

* Plusieurs correctifs permettent d’améliorer la résilience de l’extraction de contenu.
