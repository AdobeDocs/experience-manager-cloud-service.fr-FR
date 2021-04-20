---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2020.9.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2020.9.0
feature: Release Information
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 100%

---


# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2020.9.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service 2020.9.0.

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2020.9.0 est le 3 septembre 2020.

## Nouveautés {#whats-new-cloud-manager}

* La fonction Audit de contenu se nomme désormais Contrôle de l’expérience.
* Le processus de création a été divisé en trois commandes Maven distinctes.
* Si le clonage du référentiel Git échoue, il sera tenté à nouveau jusqu’à trois fois.

### Correctifs {#bug-fixes-cm}

* L’onglet Audit de contenu affichait incorrectement l’URL de base à l’aide du domaine de création et non du domaine de publication.