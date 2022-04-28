---
title: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.4.0
description: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.4.0
feature: Release Information
source-git-commit: 87e3291b4a72c24fc6cf8df488df305f1a078ea5
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 31%

---

# Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.4.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2022.4.0.

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de l’analyseur de bonnes pratiques v2.1.28 est le 22 avril 2022.

### Nouveautés {#what-is-new-bpa}

* Possibilité de détecter et de générer des rapports sur l’utilisation des API Asset Manager non prises en charge. Quatre API ne sont plus prises en charge dans AEM as a Cloud Service. Les clients doivent s’assurer qu’ils n’utilisent plus ces API et qu’ils doivent utiliser la nouvelle méthode de chargement de ressources.

* Possibilité de détecter l’utilisation de modèles de fragments de contenu. Les modèles de fragment de contenu ne sont plus pris en charge pour la création de fragments de contenu sur AEM as a Cloud Service. Les clients devront créer des modèles de fragment de contenu pour remplacer les modèles de fragment de contenu.

* Possibilité de détecter des ressources avec plus de 100 descendants sous le noeud de métadonnées de la ressource dans le référentiel. Il est recommandé de supprimer les noeuds de métadonnées qui ne sont pas nécessaires pour améliorer les performances lors du chargement de dossiers composés de ces ressources.

* Possibilité de détecter et de générer des rapports sur le type d’entrepôt de données utilisé.

* Modèle mis à jour pour AEM Portail de formulaires.

### Correctifs {#bug-fixes-bpa}

* BPA consignait les résultats pour les composants principaux au lieu de générer des rapports uniquement sur les composants clients. Ce problème a été résolu.