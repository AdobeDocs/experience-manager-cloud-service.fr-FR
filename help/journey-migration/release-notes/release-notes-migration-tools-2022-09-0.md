---
title: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.9.0
description: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.9.0
feature: Release Information
exl-id: 581370ba-e3e8-487e-af83-a1eacbda2763
source-git-commit: dd4515bdbba81dcec0868c3058c7745775cc80ff
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 100%

---

# Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.9.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2022.9.0.

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de Best Practices Analyzer v2.1.34 est le 12 septembre 2022.

### Nouveautés {#what-is-new-bpa}

* BPA peut désormais détecter et signaler si le client a ajouté une configuration de journal personnalisée. AEM as a Cloud Service ne prend pas en charge les fichiers journaux personnalisés. Tous les fichiers journaux doivent être transmis à `error.log`.
* BPA peut désormais générer des rapports sur les différents types MIME binaires présents dans le référentiel du client et les nombres qui y sont associés.

### Correctifs {#bug-fixes-bpa}

* L’interface utilisateur de BPA présentait des problèmes de rendu lors de l’affichage d’un grand nombre de résultats sous un seul motif. Ce problème a été résolu.
* BPA signalait de manière incorrecte certains résultats comme des modifications non compatibles avec gravité critique. Ce problème a été résolu.
