---
title: Création de contenu pour les Edge Delivery Services
description: Découvrez comment la création de contenu fonctionne avec des Edge Delivery Services et comment créer AEM contenu avec des Edge Delivery Services.
feature: Edge Delivery Services
exl-id: 963ff71a-8176-4d9d-8240-dc429405d139
source-git-commit: d91254b52c257a3758da200a2c74b736ca457884
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 17%

---

# Création de contenu pour les Edge Delivery Services {#authoring-edge}

Avec Edge Delivery Services, la création est facile, rapide et flexible. Vous disposez de deux options pour créer du contenu pour les Edge Delivery Services :

* [Création basée sur des documents](#document-based) - Documents Microsoft Word ou Google, par exemple
* [Éditeur universel](#universal-editor) - Interface utilisateur moderne pour la création de contenu dans AEM

## Création basée sur des documents  {#document-based}

Dans le cas de la création basée sur les documents , vous pouvez utiliser diverses sources telles que Microsoft Word et Google Docs. Les documents provenant de ces sources deviennent des pages de votre site web. Les en-têtes, listes, images, éléments de police et vidéos peuvent tous être transférés de la source initiale vers votre site web. Vous pouvez ajouter des métadonnées à des fins d’optimisation pour les moteurs de recherche ou utiliser des blocs pour travailler avec du contenu structuré et ajouter des fonctionnalités.

Pour plus d’informations sur la création basée sur les documents , reportez-vous à la section [ce document dans la documentation Edge Delivery Services.](/help/edge/docs/authoring.md)

## Création universelle de l’éditeur {#universal-editor}

Lorsque vous utilisez des Edge Delivery Services avec AEM as a Cloud Service, le fait le plus fondamental à comprendre est que le contenu que vous créez est conservé dans AEM as a Cloud Service.

![Fonctionnement de la création AEM avec les Edge Delivery Services](assets/how-aem-edge-works.png)

1. [Environnement de création AEM](/help/sites-cloud/authoring/quick-start.md) est utilisé pour la gestion de contenu, par exemple pour créer des pages, des fragments d’expérience, des fragments de contenu, etc.
   * Toutes les fonctionnalités d’AEM sont disponibles : workflows, MSM, traduction, lancements, etc.
1. [Éditeur universel](/help/sites-cloud/authoring/universal-editor/authoring.md) est utilisé pour créer le contenu géré dans AEM.
   * Universal Editor offre une nouvelle interface utilisateur moderne pour la création de contenu.
   * Pour la création, AEM effectue le rendu du HTML, mais inclut les scripts, les styles, les icônes et d’autres ressources provenant d’Edge Delivery Services.
   * Bien que l’éditeur universel soit utilisé, toutes les modifications sont conservées dans AEM.
   * L’éditeur universel n’est pas encore à parité avec l’éditeur de page d’AEM et certaines fonctions d’AEM ne sont peut-être pas disponibles dans l’éditeur universel.
1. Le contenu que vous créez avec l’éditeur universel et conservez dans AEM est publié sur les Edge Delivery Services.
   * Le contenu reste stocké dans AEM.
   * AEM effectue le rendu du HTML sémantique nécessaire à l’ingestion.
   * Le contenu est publié pour les Edge Delivery Services.
1. [Edge Delivery Services](/help/edge/developer/keeping-it-100.md) vérifiez un score Lighthouse 100 %.

Les blocs sont des composants fondamentaux d’une page fournie par des Edge Delivery Services. Les auteurs peuvent choisir parmi les blocs par défaut fournis en standard par Adobe ou parmi les blocs personnalisés pour votre projet par vos développeurs.

Universal Editor fournit une interface utilisateur graphique moderne et intuitive pour créer votre contenu en faisant glisser des blocs.

![Glisser-déposer des blocs dans l’éditeur universel](assets/blocks.png)

Les détails des blocs peuvent ensuite être configurés dans le rail Propriétés .

![Configuration des propriétés de bloc](assets/block-properties.png)

Pour plus d’informations sur la création à l’aide d’Universal Editor, consultez le document . [Création de contenu avec l’éditeur universel.](/help/sites-cloud/authoring/universal-editor/authoring.md)

Veuillez consulter le [Guide de prise en main du développement pour la création AEM avec Edge Delivery Services](/help/edge/edge-dev-getting-started.md) afin d’apprendre à démarrer votre propre projet pour créer avec AEM et Edge Delivery Services.

## Prise en main {#how-to-get-started}

Veuillez contacter votre représentant d’Adobe pour accéder à cette fonctionnalité.
