---
title: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2024.05.0
description: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2024.05.0
feature: Release Information
role: Admin
exl-id: f50a74fa-ad7d-4837-b0a1-9945c32af02f
source-git-commit: 3b2ed44b438fe8587a9b9603ddfacc41111fb903
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 35%

---

# Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2024.05.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2024.05.0.

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de la version 2.1.5 de l’analyseur des bonnes pratiques est mai 2024.

### Nouveautés {#what-is-new-bpa}

* L’analyseur des bonnes pratiques (BPA) prend désormais en charge le téléchargement automatique des rapports générés par BPA directement vers Cloud Acceleration Manager (CAM). Les utilisateurs n’auront plus besoin de télécharger manuellement le rapport et de le charger dans la CAM. Pour plus d’informations, voir [Utilisation de l’analyseur des bonnes pratiques](/help/journey-migration/best-practices-analyzer/using-best-practices-analyzer.md)

### Correctifs {#bug-fixes-bpa}

* L’analyseur des bonnes pratiques détecte désormais tous les noeuds de plus de 16 Mo.
* Les conditions de race causant la correction d&#39;occurrences non-conformistes.

## Cloud Acceleration Manager {#cam-release}

### Nouveautés {#what-is-new-cam}

* Cloud Acceleration Manager (CAM) prend désormais en charge le chargement automatique des rapports générés par BPA directement vers CAM. Pour en savoir plus, voir [Phase de préparation dans Cloud Acceleration Manager - Utilisation de la carte d’analyse des bonnes pratiques](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#best-practices-analysis)

* Cloud Acceleration Manager fournit désormais une estimation de la durée d’ingestion, compte tenu de facteurs tels que le nombre de noeuds, la taille de l’entrepôt de données, etc. En savoir plus avec [Ingestion de contenu dans Cloud Service](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md)
