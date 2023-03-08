---
title: Dernières notes de mise à jour de maintenance d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Dernières notes de mise à jour de maintenance d’ [!DNL Adobe Experience Manager] as a Cloud Service.
source-git-commit: edb8949b532b80a55106e706a49e2ada68722a67
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 7%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les versions techniques de la dernière version de maintenance d’Experience Manager as a Cloud Service.

## Version 11289 {#release-11289}

Vous trouverez ci-dessous un résumé des améliorations continues apportées à la version de maintenance 11289, publiée publiquement le 7 mars 2023. Cette version de maintenance est une mise à jour de la version de maintenance 10912 précédente.

L’activation des fonctionnalités de cette version de maintenance vous fournira l’ensemble des fonctionnalités. Voir [notes de mise à jour actuelles](/help/release-notes/release-notes-cloud/release-notes-current.md) pour plus d’informations.

### Problèmes connus {#known-issues}

Ne mettez pas à niveau si vous utilisez CORS. Un problème affectant la fonctionnalité de diffusion de contenu GraphQL a été identifié dans cette version. Une modification de la configuration Dispatcher d’AEM par défaut concernant la mise en cache des requêtes persistantes de GraphQL peut interrompre la diffusion du contenu GraphQL de ces requêtes. Ce problème sera corrigé dans notre prochaine version de maintenance.

### Problèmes résolus {#fixed-issues}

#### Sites {#sites-issues}

- SITES-11584 Correction d’un problème lié aux Live Copies qui ne pouvaient pas être créées pour les pages avec des annotations.
- SITES-11683 Désactivation des Live Copies MSM avec un héritage partiellement rompu

#### Ressources {#assets-issues}

- ASSETS-20879 Correction d’une régression qui empêchait le bon fonctionnement de l’interface utilisateur des rapports de ressources et générait des résultats incorrects dans les rapports générés.
- ASSETS-21020 Correction d’un problème lié au téléchargement de ressource rompu : le profil d’image n’existe pas après le déplacement de la ressource.
- ASSETS-21023 Correction d’un problème lié aux rendus d’image dans Dynamic Media qui empêchait l’accès via l’API.

#### Forms {#forms-issues}

- Aucun

#### Plateforme {#platform-issues}

- GRANITE-44467 - Correction d’un problème en raison duquel l’importation échouait lors de la mise à jour d’un noeud existant, Filevault sous certaines instances ne conservait pas les types de mixin et les noeuds enfants.

### Technologies intégrées {#embedded-tech}

| Technologie | Version | Lien |
|---|---|---|
| AEM OAK | 1.44-T20221206170501-6d59064 | [API 1.44.0 Oak](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.44.0/index.html) |
| API SLING AEM | Version 2.27.0 | [API Apache Sling 2.27.0](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Spécification du langage de modèle de HTML](https://github.com/adobe/htl-spec) |
| Composants principaux AEM | Version 2.21.2 | [AEM composants principaux WCM](https://github.com/adobe/aem-core-wcm-components) |
