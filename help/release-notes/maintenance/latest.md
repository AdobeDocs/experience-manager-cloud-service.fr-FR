---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 26178edc3308801e0273aca67b7cd82180131483
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 36%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 12255 {#release-12255}

Vous trouverez ci-dessous un résumé des améliorations continues apportées à la version de maintenance 12255, publiée publiquement le 13 juin 2023. Cette mise à jour de maintenance est une mise à jour de la version de maintenance 12142 précédente.

L’activation des fonctionnalités de cette version de maintenance vous fournira l’ensemble des fonctionnalités. Consultez les [notes de mise à jour actuelles](/help/release-notes/release-notes-cloud/release-notes-current.md) pour plus d’informations.

### Améliorations {#enhancements-12255}

Aucun.

### Problèmes connus {#known-issues-12255}

- ASSETS-25729 - Le menu de sélecteur d’affichage est désactivé.
- ASSETS-25728 - L’option Retraiter les ressources n’est pas disponible dans la vue de recherche
- ASSETS-22603 - Certaines colonnes du rapport de ressources de type Téléchargement affichent des valeurs &quot;null&quot; dans l’interface utilisateur. Le fichier CSV téléchargeable n’est pas affecté.

### Problèmes résolus {#fixed-issues-12255}

- Diverses mises à jour liées à l’accessibilité
- ASSETS-15116 - Option &quot;Aller à l’emplacement&quot; disponible dans la vue de recherche Assets
- ASSETS-17453 - (Dynamic Media) Impossible de sélectionner une miniature personnalisée pour les vidéos
- ASSETS-19279 - Archive de téléchargement des ressources pour les fichiers volumineux
- ASSETS-19544 - Dernière modification par l’utilisateur pour les mises à jour de ressources
- ASSETS-20146 - (IU tactile) Rapports sur les téléchargements de ressources Échec en raison des erreurs de validation s’affichent toujours en haut de la page de liste pour les rapports.
- ASSETS-21056 - Optimisation des performances de référence des ressources pour réduire les écritures
- ASSETS-21909 - Impossible d’afficher la vidéo de recadrage intelligent lorsque vtt ne parvient pas à télécharger
- ASSETS-22261 - La structure de dossiers des téléchargements Linkshare est incohérente avec les téléchargements de l’interface utilisateur Assets
- ASSETS-22550 - Le panneau Filtre de recherche s’ouvre désormais par défaut.
- ASSETS-22920 - L’annulation de la publication du dossier à partir de Brand Portal ne marque pas les ressources dans comme non publiées.
- ASSETS-22922 - Les paramètres prédéfinis de visionneuse désactivés s’affichent dans le composant Dynamic Media
- ASSETS-23461 - Publication rapide Brand Portal à partir de la vue de recherche Ressources
- ASSETS-23466 - La gestion des liens inaccessibles de l’InDesign Server ne parvient pas à résoudre les liens AAL contenant des espaces
- ASSETS-23469 - Les filtres de ressources par défaut entrent en conflit avec les filtres personnalisés
- ASSETS-23981 - Fonction de tri pour les titres qui ne fonctionnent pas dans les liens de collection
- ASSETS-24723 - Les ressources publiées ont été retraitées sans intervention de l’utilisateur.
- GRANITE-45385 - Migration de l’activation de l’arborescence pour utiliser la tâche sling au lieu du workflow

### Technologies intégrées {#embedded-tech-12255}

| Technologie | Version | Lien |
|---|---|---|
| AEM OAK | 1.50-T20230405052634-f9df4aa | [API Oak 1.50.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.50.0/index.html) |
| API SLING AEM | Version 2.27.0 | [API Apache Sling 2.27.0](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | Version 2.23.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
