---
title: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.4.0
description: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.4.0
feature: Release Information
exl-id: 4941736b-82cd-4050-b3e9-aef250d5c4c7
source-git-commit: 717b2c851a18ef5171d64a462509ce08fb87a59c
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 100%

---

# Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.4.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2022.4.0.

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de l’analyseur de bonnes pratiques v2.1.28 est le 22 avril 2022.

### Nouveautés {#what-is-new-bpa}

* Possibilité de détecter et de générer des rapports sur l’utilisation des API Asset Manager non prises en charge. Quatre API ne sont plus prises en charge dans AEM as a Cloud Service. Les clients doivent s’assurer qu’ils n’utilisent plus ces API et qu’ils utilisent la nouvelle méthode de chargement de ressources.

* Possibilité de détecter l’utilisation de modèles de fragments de contenu. Les modèles de fragment de contenu ne sont plus pris en charge pour la création de fragments de contenu sur AEM as a Cloud Service. Les clients devront créer des modèles de fragment de contenu pour remplacer les modèles de fragment de contenu.

* Possibilité de détecter des ressources avec plus de 100 descendants sous le nœud de métadonnées de la ressource dans le référentiel. Il est recommandé de supprimer les nœuds de métadonnées qui ne sont pas nécessaires pour améliorer les performances lors du chargement de dossiers composés de ces ressources.

* Possibilité de détecter et de générer des rapports sur le type d’entrepôt de données utilisé.

* Modèle mis à jour pour le Portail Formulaires AEM.

### Correctifs {#bug-fixes-bpa}

* L’analyseur de bonnes pratiques consignait les résultats pour les composants principaux au lieu de générer des rapports uniquement sur les composants clients. Ce problème a été résolu.
