---
title: Création d’une requête API - Configuration découplée
description: Découvrez comment utiliser l’API GraphQL pour une diffusion découplée du contenu du fragment de contenu et l’API REST AEM Assets pour gérer les fragments de contenu.
exl-id: 2b72f222-2ba5-4a21-86e4-40c763679c32
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: 38a4bf89e099432163163e90e08aa0f47407724f
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 88%

---

# Création d’une requête API - Configuration découplée {#accessing-delivering-content-fragments}

Découvrez comment utiliser l’API GraphQL pour une diffusion découplée du contenu du fragment de contenu et l’API REST AEM Assets pour gérer les fragments de contenu.

## En quoi consistent les API REST GraphQL et Assets ? {#what-are-the-apis}

[Maintenant que vous avez créé des fragments de contenu](create-content-fragment.md) vous pouvez utiliser les API d’AEM pour une diffusion découplée.

* [L’API GraphQL](/help/headless/graphql-api/content-fragments.md) permet de créer des requêtes d’accès et de diffusion de fragments de contenu. Cette API offre l’ensemble de fonctionnalités le plus robuste pour interroger et utiliser du contenu de fragment de contenu.
   * Pour utiliser l’API, [définissez et activez des points d’entrée dans AEM](/help/headless/graphql-api/graphql-endpoint.md), et si nécessaire, l’[interface GraphiQL installée](/help/headless/graphql-api/graphiql-ide.md).
* Une sélection de [API AEM pour la diffusion et la gestion de contenu structuré](/help/headless/apis-headless-and-content-fragments.md) peut être utilisée avec des fragments de contenu.

Le reste de ce guide porte sur l’accès à GraphQL et la diffusion de fragments de contenu.

## Activation du point d’entrée GraphQL {#enable-graphql-endpoint}

Avant de pouvoir utiliser les API GraphQL, un point d’entrée GraphQL doit être créé.

Pour plus d’informations, consultez [Gestion des points d’entrée GraphQL dans AEM](/help/headless/graphql-api/graphql-endpoint.md).

## Requête de contenu à l’aide de GraphQL avec GraphiQL

Les architectes d’informations créent des requêtes pour leurs points d’entrée de canal afin de diffuser du contenu. Considérez ces requêtes une seule fois par point d’entrée et par modèle. Pour les besoins de ce guide de prise en main, il suffit d’en créer une.

GraphiQL est un IDE inclus dans votre environnement AEM ; il est accessible/visible après la [configuration des points d’entrée](#enable-graphql-endpoint).

Pour plus d’informations, voir [Utilisation de l’IDE GraphiQL](/help/headless/graphql-api/graphiql-ide.md).

GraphQL permet d’utiliser des requêtes structurées qui peuvent cibler non seulement des jeux de données spécifiques ou des objets de données particuliers, mais peuvent également fournir des éléments spécifiques d’objets, des résultats imbriqués, prendre en charge des variables de requête, etc.

GraphQL permet d’éviter les requêtes d’API itératives ainsi que la surdiffusion, et permet au contraire la diffusion en masse de ce qui est nécessaire au rendu en réponse à une requête d’API unique. Le fichier JSON produit peut être utilisé pour diffuser des données vers d’autres sites ou applications.

## Étapes suivantes {#next-steps}

C’est terminé ! Vous possédez maintenant une compréhension de base de la gestion de contenu découplée dans AEM. Bien entendu, il existe beaucoup d’autres ressources que vous pouvez approfondir pour une compréhension complète des fonctionnalités disponibles.

* **[Fragments de contenu](/help/sites-cloud/administering/content-fragments/managing.md)** – Pour plus d’informations sur la création et la gestion de fragments de contenu
* **[Prise en charge des fragments de contenu dans l’API HTTP AEM Assets](/help/assets/content-fragments/assets-api-content-fragments.md)** – Pour plus d’informations sur l’accès direct au contenu AEM via l’API HTTP, via des opérations CRUD (création, lecture, mise à jour, suppression)
* **[API GraphQL](/help/headless/graphql-api/content-fragments.md)** – Pour plus d’informations sur la diffusion découplée de fragments de contenu

>[!NOTE]
>
>Les [OpenAPI de modèle de fragment de contenu et de fragment de contenu](/help/headless/content-fragment-openapis.md) sont également disponibles.
