---
title: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2023.07.0
description: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2023.07.0
feature: Release Information
exl-id: 2f787321-f156-480d-bbe8-1a6d04f110c5
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 42%

---

# Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2023.07.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2023.07.0.

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de l’analyseur des bonnes pratiques v2.1.42 est le 6 juillet 2023.

### Nouveautés {#what-is-new-bpa}

* Plusieurs modèles de bonnes pratiques ont été ajoutés à cette version de l’analyseur des bonnes pratiques. Ces informations comprennent les éléments suivants :
   * Identification de la configuration minimale de la tâche de maintenance
   * Détection de requêtes longues/lourdes
   * Détection d’un grand nombre de workflows de création en cours d’exécution ou à l’état obsolète
   * Détection de la configuration de la tâche Sling Apache OSGI
   * Détection de caches goyaves personnalisés

### Correctifs {#bug-fixes-bpa}

* Le BPA a été amélioré afin d’éviter les échecs de génération de rapports en mémoire insuffisante pour les rapports avec un grand nombre de résultats.
* L’application d’une seule page (BPA) a été améliorée afin de détecter les caractères d’échappement dans les chemins d’accès afin d’éviter les échecs d’ingestion de contenu lors de la migration de contenu vers AEM as a Cloud Service.
