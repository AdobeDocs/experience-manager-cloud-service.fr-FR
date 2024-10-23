---
title: Création de contenu WYSIWYG pour les Edge Delivery Services
description: Découvrez le fonctionnement de la création de contenu avec Edge Delivery Services et comment créer du contenu AEM avec Edge Delivery Services.
feature: Edge Delivery Services
exl-id: 963ff71a-8176-4d9d-8240-dc429405d139
role: User
source-git-commit: 7e8446bec18eaeb4eb017dd63436a066d3a90fed
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 64%

---


# Création de contenu WYSIWYG pour les Edge Delivery Services {#authoring-edge}

Avec Edge Delivery Services, la création est facile, rapide et flexible. Vous disposez de deux options pour créer du contenu pour Edge Delivery Services :

* [Éditeur universel](#universal-editor) - Interface utilisateur moderne de WYSIWYG pour la création de contenu dans AEM
* [Création basée sur des documents](#document-based) - Microsoft Word ou Google Docs, par exemple

## Création avec l’éditeur universel {#universal-editor}

Lorsque vous utilisez Edge Delivery Services avec AEM as a Cloud Service, l’aspect le plus important à comprendre est que le contenu que vous créez est conservé dans AEM as a Cloud Service.

![Fonctionnement de la création WYSIWYG avec les Edge Delivery Services](assets/how-aem-edge-works.png)

1. [L’environnement AEM Sites](/help/sites-cloud/authoring/quick-start.md) est utilisé pour la gestion de contenu, par exemple pour créer de nouvelles pages, des fragments d’expérience, des fragments de contenu, etc.
   * Toutes les fonctionnalités d’AEM sont disponibles : workflows, MSM, traduction, lancements, etc.
1. [L’éditeur universel](/help/sites-cloud/authoring/universal-editor/authoring.md) est utilisé pour créer le contenu géré dans AEM.
   * Il propose une nouvelle interface utilisateur moderne pour la création de contenu.
   * Pour la création, AEM effectue le rendu du HTML, mais inclut les scripts, les styles, les icônes et d’autres ressources provenant d’Edge Delivery Services.
   * Bien que l’on utilise l’éditeur universel, toutes les modifications sont conservées dans AEM.
   * L’éditeur universel n’est pas encore à parité avec l’éditeur de page d’AEM et certaines fonctions d’AEM risquent de ne pas être disponibles dans l’éditeur universel.
1. Le contenu que vous créez avec l’éditeur universel et conservez dans AEM est publié dans Edge Delivery Services.
   * Le contenu reste stocké dans AEM.
   * AEM effectue le rendu du HTML sémantique nécessaire à l’ingestion.
   * Le contenu est publié dans Edge Delivery Services.
1. [Edge Delivery Services](/help/edge/developer/keeping-it-100.md) garantit un score Lighthouse de 100 %.

Les blocs sont des composants fondamentaux d’une page diffusée par Edge Delivery Services. Les auteurs et autrices peuvent choisir parmi les blocs par défaut fournis en standard par Adobe ou parmi les blocs personnalisés pour votre projet par votre équipe de développement.

Universal Editor fournit une interface utilisateur graphique moderne et intuitive pour créer votre contenu en ajoutant et en organisant des blocs.

![Ajout et organisation de blocs dans l’éditeur universel](assets/blocks.png)

Les détails des blocs peuvent ensuite être configurés dans le rail Propriétés.

![Configuration des propriétés de bloc](assets/block-properties.png)

Pour plus d’informations sur la création à l’aide de l’éditeur universel, consultez le document [Créer du contenu avec l’éditeur universel](/help/sites-cloud/authoring/universal-editor/authoring.md).

Consultez le [Guide de prise en main du développeur pour la création WYSIWYG avec des Edge Delivery Services](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) pour découvrir comment lancer votre propre projet de création avec des AEM et des Edge Delivery Services.

## Méthodes de création supplémentaires  {#authoring-methods}

La création WYSIWYG est un outil puissant et intuitif pour les auteurs de contenu. Cependant, il existe de nombreux cas d’utilisation de création, raison pour laquelle AEM propose des solutions de création supplémentaires.

Consultez le document [Choix d’une méthode de création](/help/edge/authoring-methods.md) pour en savoir plus sur les solutions de création AEM offres, y compris la création basée sur des documents et sans interface.
