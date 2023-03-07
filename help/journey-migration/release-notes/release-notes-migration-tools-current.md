---
title: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2023.03.0
description: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.03.0
feature: Release Information
exl-id: 2f787321-f156-480d-bbe8-1a6d04f110c5
source-git-commit: 5815dacd2806cc7886aa0c7c5c9fd329306b3e1b
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 49%

---

# Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2023.03.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2022.03.0.

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de l’analyseur de bonnes pratiques v2.1.40 est le 03 mars 2023.

### Nouveautés {#what-is-new-bpa}

* BPA peut désormais détecter et générer des rapports sur les noeuds en conflit - noeuds ayant le même `jcr:uuid`. Ces résultats sont considérés comme critiques, car ils peuvent entraîner des problèmes d’ingestion de contenu lors du déplacement du contenu vers AEM as a Cloud Service.
* BPA peut désormais détecter et générer des rapports sur l’utilisation des écouteurs d’événements. Il est recommandé de refactoriser ce type de mécanisme de gestion des événements en tâches sling lors du passage à AEM as a Cloud Service.

### Correctifs {#bug-fixes-bpa}

* BPA signalait des faux positifs sur `grouprendercondition`. Ce problème a été résolu.