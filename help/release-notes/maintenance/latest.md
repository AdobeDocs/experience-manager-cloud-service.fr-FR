---
title: Notes de mise à jour de la maintenance actuelle de [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle de [!DNL Adobe Experience Manager] as a Cloud Service.
source-git-commit: 7e66c9f26211bd92119c74f311f3e9b3195a8d98
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 6%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante présente les notes techniques de mise à jour de la version de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 11382 {#release-11382}

Vous trouverez ci-dessous un résumé des améliorations continues apportées à la version de maintenance 11382, publiée publiquement le 28 mars 2023. Cette version de maintenance est une mise à jour de la version de maintenance 11289 précédente.

L’activation des fonctionnalités de cette version de maintenance vous fournira l’ensemble des fonctionnalités. Voir [notes de mise à jour actuelles](/help/release-notes/release-notes-cloud/release-notes-current.md) pour plus d’informations.

### Problèmes résolus {#fixed-issues}

- ASSETS-21023 - Correction du rendu de recadrage intelligent, grâce auquel les clients pouvaient observer une exception de pointeur nul sur l’instance de l’éditeur de tous les environnements AEM lorsqu’ils tentaient d’accéder à ces rendus via l’API.
- SKYOPS-49280 - Lors de l’installation d’une configuration ou d’une mise à jour de lot à l’aide de RDE dans Publier, le résultat peut ne pas être observable, car le cache du Dispatcher de publication n’est pas invalidé.

#### Sites {#sites-issues}

- SITES-7796 - Possibilité pour l’auteur de contenu de publier le fragment de contenu de Principal et ses variantes respectives lors de l’exportation vers la cible

#### Ressources {#assets-issues}

- ASSETS-20076 - Ajout de la prise en charge du filigrane vidéo correspondant à la prise en charge actuelle du filigrane d’image
- ASSETS-21428 - Ajout d’exclusions pour les modifications CSS

#### Forms {#forms-issues}

- CQ-4351502 - Mise à jour du mappage utilisateur du service pour autoriser l’accès en lecture dans Sites

#### Plateforme {#platform-issues}

- SITES-11040 - Activation conditionnelle de la mise en cache des requêtes persistantes de GraphQL dans Dispatcher

### Technologies intégrées {#embedded-tech}

| Technologie | d’Adobe Experience Manager Forms 6.5 | Lien |
|---|---|---|
| AEM OAK | 1.44-T20221206170501-6d59064 | [API 1.44.0 Oak](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.44.0/index.html) |
| API SLING AEM | Version 2.27.0 | [API Apache Sling 2.27.0](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Spécification du langage de modèle de HTML](https://github.com/adobe/htl-spec) |
| Composants principaux AEM | Version 2.21.2 | [AEM composants principaux WCM](https://github.com/adobe/aem-core-wcm-components) |
