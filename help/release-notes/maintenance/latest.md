---
title: Dernières notes de mise à jour de maintenance d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Dernières notes de mise à jour de maintenance d’ [!DNL Adobe Experience Manager] as a Cloud Service.
source-git-commit: 76da86d31e2780c2d22419cb8a338cf37963fad8
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 7%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les versions techniques de la dernière version de maintenance d’Experience Manager as a Cloud Service.

## Version 10912 {#release-10912}

Vous trouverez ci-dessous un résumé des améliorations continues apportées à la version de maintenance 10912, publiée publiquement le 3 février 2023. Cette version de maintenance est une mise à jour de la version de maintenance 9850 précédente.

L’activation des fonctionnalités de cette version de maintenance vous fournira l’ensemble des fonctionnalités. Voir [notes de mise à jour actuelles](/help/release-notes/release-notes-cloud/release-notes-current.md) pour plus d’informations.

### Problèmes connus {#known-issues}

Ne mettez pas à niveau si vous utilisez CORS. Nous avons identifié un problème affectant la partie diffusion de contenu GraphQL dans cette version. Un changement dans la configuration Dispatcher par défaut AEM la manière dont les requêtes persistantes de GraphQL sont mises en cache peut interrompre la diffusion de contenu GraphQL des requêtes persistantes pour les clients utilisant une configuration CORS.

### Technologies intégrées {#embedded-tech}

| Technologie | Version | Lien |
|---|---|---|
| AEM composants principaux WCM | Version 2.21.2 | [GitHub](https://github.com/adobe/aem-core-wcm-components) |
