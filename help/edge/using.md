---
title: Utiliser Edge Delivery Services avec AEM
description: Découvrez comment AEM as a Cloud Service peut être utilisé avec Edge Delivery Services.
feature: Edge Delivery Services
exl-id: 41999302-b4c9-4f5a-b659-6e7398a3c4f4
role: Admin, Architect, Developer
source-git-commit: 16531cf084ad1b9619f4dffc6d028c7df4002ff5
workflow-type: ht
source-wordcount: '338'
ht-degree: 100%

---


# Utiliser Edge Delivery Services avec AEM {#using-edge}

Edge Delivery Services est découplé de la source de contenu et peut ingérer du contenu provenant de différentes sources. Cela signifie que vous pouvez utiliser plusieurs sources de contenu sur le même site web et obtenir une publication transparente et rationalisée, quelle que soit la source choisie.

Grâce à Edge Delivery Services, vous pouvez créer rapidement des environnements de développement dans lesquels les personnes créant du contenu peuvent rapidement mettre à jour et publier du contenu, ou encore lancer de nouveaux sites de manière rapide. Il ne faut que quelques secondes pour passer de l’édition à la vue du contenu en direct sur Internet.

![Sources de contenu pour Edge Delivery.](assets/content-sources.png)

L’ingestion de plusieurs sources de contenu offre une flexibilité maximale. Adobe fournit des conseils pour vous aider à choisir les sources de contenu qui conviennent le mieux à votre projet.

Dans certains cas, la source de contenu est prédéfinie ou n’est pas flexible (par exemple, le projet ne peut pas utiliser SharePoint ou Google Drive). Mais dans de nombreux cas, l’outil n’est pas prédéterminé et son choix n’est pas si simple.

Le principe directeur d’Adobe est la simplicité. Commencez par la création basée sur des documents et ajoutez de la complexité si nécessaire. Si un changement d’outil est nécessaire, l’intégration d’Edge Delivery Services d’AEM couvre la migration de contenu.

![Flexibilité de la source de contenu.](assets/content-source-flexiblity.png)

## Création {#authoring-edge}

Avec Edge Delivery Services, la création est facile, rapide et flexible. Vous pouvez choisir la création basée sur les documents ou la création WYSIWYG avec l’éditeur universel.

Consultez le document [Création de contenu pour Edge Delivery Services](/help/edge/wysiwyg-authoring/authoring.md) pour plus d’informations.

## Publication {#publishing-edge}

Avec Edge Delivery Services, la publication de contenu est transparente, quelle que soit votre source de contenu.

Consultez le document [Publication de contenu pour Edge Delivery Services](/help/edge/wysiwyg-authoring/publishing.md) pour plus d’informations.

## Développement {#developing-edge}

Edge Delivery Services est basé sur le concept de blocs. AEM est fourni avec une bibliothèque complète de blocs prédéfinis, qui peut être étendue pour répondre aux besoins de votre projet. Le code pour les projets Edge Delivery Services est géré dans GitHub.

Pour plus d’informations, consultez le document [Guide de prise en main pour le développement pour la création WYSIWYG avec Edge Delivery Services](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md).
