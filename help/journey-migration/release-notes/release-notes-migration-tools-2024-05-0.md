---
title: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2024.05.0
description: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2024.05.0
feature: Release Information
role: Admin
exl-id: f50a74fa-ad7d-4837-b0a1-9945c32af02f
source-git-commit: 3b2ed44b438fe8587a9b9603ddfacc41111fb903
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 33%

---

# Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2024.05.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2024.05.0.

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de l’analyseur de bonnes pratiques v2.1.50 est le mai 2024.

### Nouveautés {#what-is-new-bpa}

* L’analyseur de bonnes pratiques (BPA) prend désormais en charge le chargement automatique des rapports générés par BPA directement vers Cloud Acceleration Manager (CAM). Les utilisateurs n’auront plus besoin de télécharger manuellement le rapport et de le charger dans CAM. Pour plus d’informations, voir [&#x200B; Utilisation de l’analyseur des bonnes pratiques &#x200B;](/help/journey-migration/best-practices-analyzer/using-best-practices-analyzer.md)

### Correctifs {#bug-fixes-bpa}

* L’analyseur de bonnes pratiques détecte désormais tous les nœuds de plus de 16 Mo
* Condition de race provoquant des occurrences sporadiques de résultats NCC corrigés.

## Cloud Acceleration Manager {#cam-release}

### Nouveautés {#what-is-new-cam}

* Cloud Acceleration Manager (CAM) prend désormais en charge le chargement automatique des rapports générés par BPA directement vers CAM. Pour en savoir plus, consultez [Phase de préparation dans Cloud Acceleration Manager - Utilisation de la carte d’analyse des bonnes pratiques](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#best-practices-analysis)

* Cloud Acceleration Manager fournit désormais une estimation de la durée d’une ingestion, en fonction de facteurs tels que le nombre de nœuds, la taille du magasin de données, etc. En savoir plus avec [Ingestion de contenu dans Cloud Service](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md)
