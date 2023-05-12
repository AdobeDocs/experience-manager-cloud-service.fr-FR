---
title: Notes de mise à jour de la maintenance actuelle de [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle de [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 3823b9369c612058998e265346b3f727001aef4b
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 21%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante présente les notes techniques de mise à jour de la version de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 11873 {#release-11873}

Vous trouverez ci-dessous un résumé des améliorations continues apportées à la version de maintenance 11873, publiée publiquement le 3 mai 2023. Cette version de maintenance est une mise à jour de la version de maintenance 11835 précédente.

L’activation des fonctionnalités de cette version de maintenance vous fournira l’ensemble des fonctionnalités. Consultez les [notes de mise à jour actuelles](/help/release-notes/release-notes-cloud/release-notes-current.md) pour plus d’informations.

### Améliorations {#enhancements}

- SITES-1200 - Améliorations de l’API de recherche avec le filtrage basé sur les balises
- GRANITE-42939 - Ajout d’annotations et d’avertissements d’obsolescence au code oauth-server

### Problèmes connus {#known-issues-11873}

- SITES-13253 - RecursionTooDeepException dans les composants principaux v2.22.6
- SITES-13256 - Teaser WCM principal configuré avec rendu de page de coupures d’URL spéciales
- GRANITE-45462 - Configuration multirégion du client de messagerie
- GRANITE-45562 - Problèmes avec la combinaison d’images renvoyant 200 au lieu de 404

### Problèmes résolus {#fixed-issues-11873}

- SKYSI-19884/SKYOPS-53745 - Correction d’un problème avec PublishPageRenderingErrorsHigh
- GRANITE-4388 - Correction de la dégradation du débit après un grand nombre d’écritures de ressources DAM sur Mongo
- SITES-11922 - Correction d’un problème lié à l’annulation de la publication de l’aperçu qui ne supprimait pas l’état de synchronisation
- ASSETS-21648 - Correction d’un problème d’autorisation avec la fonctionnalité Asset Relate.

### Technologies intégrées {#embedded-tech-11873}

| Technologie | Version | Lien |
|---|---|---|
| AEM OAK | 1.44-T20221206170501-6d59064 | [API 1.44.0 Oak](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.44.0/index.html) |
| API SLING AEM | Version 2.27.0 | [API Apache Sling 2.27.0](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Spécification du langage de modèle de HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | Version 2.21.2 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
