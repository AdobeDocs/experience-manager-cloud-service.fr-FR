---
title: Guide de prise en main pour l’accès et la diffusion de fragments de contenu découplés
description: L’API REST Assets permet de gérer les fragments de contenu et l’API GraphQL permet une simple diffusion découplée du contenu des fragments de contenu.
translation-type: tm+mt
source-git-commit: 472f691cf8b2ec502611ee88bc4abdcabb6d8412
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 97%

---


# Guide de prise en main pour l’accès et la diffusion de fragments de contenu découplés {#accessing-delivering-content-fragments}

L’API REST Assets permet de gérer les fragments de contenu et l’API GraphQL permet une simple diffusion découplée du contenu des fragments de contenu.

## Que sont les API GraphQL et REST Assets ? {#what-are-the-apis}

[Maintenant que vous avez créé des fragments de contenu](create-content-fragment.md), vous pouvez utiliser les API d’AEM pour une diffusion découplée.

* [L’API GraphQL](/help/assets/content-fragments/graphql-api-content-fragments.md) permet de créer des requêtes d’accès et de diffusion de fragments de contenu.
* [L’API REST Assets](/help/assets/content-fragments/assets-api-content-fragments.md) permet de créer et de modifier des fragments de contenu (et d’autres ressources).

Le reste de ce guide porte sur l’accès à GraphQL et la diffusion de fragments de contenu.

## Comment diffuser un fragment de contenu avec GraphQL {#how-to-deliver-a-content-fragment}

Les architectes de l’information doivent concevoir des requêtes pour leurs points d’entrée de canaux afin de diffuser du contenu. Ces requêtes ne doivent généralement être prises en compte qu’une seule fois par point d’entrée et par modèle. Pour les besoins de ce guide de prise en main, nous ne devrons en créer qu’une.

<!-- Not in the UI yet - will need updating when it is -->
<!--
1. Log into AEM as a Cloud Service and from the main menu select **Tools -&gt; Assets -&gt; GraphQL** 
   * Alternatively open the page directly at `https://<host>:<port>/content/graphiql.html`.
-->

1. Connectez-vous à AEM en tant que Cloud Service et accédez à l’interface GraphiQL :
   * Par exemple : `https://<host>:<port>/content/graphiql.html`.

1. GraphiQL est un éditeur de requêtes intégré au navigateur pour GraphQL. Vous pouvez l’utiliser pour créer des requêtes permettant de récupérer des fragments de contenu afin de les diffuser de manière découplée en mode JSON.
   * Le volet de gauche permet de construire votre requête.
   * Le volet de droite affiche les résultats.
   * L’éditeur de requêtes comprend la saisie du code et des touches d’accès rapide pour exécuter facilement la requête.
      ![Éditeur GraphiQL](../assets/graphiql.png)

1. En supposant que le modèle que nous avons créé s’appelle `person`, avec les champs `firstName`, `lastName` et `position`, nous pouvons créer une requête simple pour récupérer le contenu de notre fragment de contenu.

   ```text
   query 
   {
     personList {
       items {
         _path
         firstName
         lastName
         position
       }
     }
   }
   ```

1. Entrez la requête dans le volet de gauche.
   ![Requête GraphiQL](../assets/graphiql-query.png)

1. Cliquez sur le bouton **Exécuter la requête** ou utilisez le raccourci `Ctrl-Enter` pour faire apparaître les résultats sous la forme JSON dans le volet de droite.
   ![Résultats GraphiQL](../assets/graphiql-results.png)

1. Cliquez sur le lien **Docs** en haut à droite de la page pour afficher la documentation contextuelle afin de vous aider à créer vos requêtes adaptées à vos propres modèles.
   ![Documentation GraphiQL](../assets/graphiql-documentation.png)

GraphQL permet d’utiliser des requêtes structurées qui peuvent cibler non seulement des ensembles de données spécifiques ou des objets de données individuels, mais peuvent également fournir des éléments spécifiques des objets, des résultats imbriqués, prend en charge les variables de requête, et bien plus encore.

GraphQL permet d’éviter les requêtes d’API itératives ainsi que la surdiffusion, et permet la diffusion en masse de ce qui est exactement nécessaire pour le rendu en réponse à une requête d’API unique. Le fichier JSON produit peut être utilisé pour diffuser des données vers d’autres sites ou applications.

## Étapes suivantes {#next-steps}

C’est terminé ! Vous possédez maintenant une compréhension de base de la gestion de contenu découplée dans AEM. Bien entendu, il existe beaucoup d’autres ressources que vous pouvez approfondir pour une compréhension complète des fonctionnalités disponibles.

* **Explorateur de configurations** – Pour plus d’informations sur l’Explorateur de configurations AEM
* **[Fragments de contenu](/help/assets/content-fragments/content-fragments.md)** – Pour plus d’informations sur la création et la gestion de fragments de contenu
* **[Prise en charge des fragments de contenu dans l’API HTTP AEM Assets](/help/assets/content-fragments/assets-api-content-fragments.md)** – Pour plus d’informations sur l’accès direct au contenu AEM via l’API HTTP, via des opérations CRUD (création, lecture, mise à jour, suppression)
* **[API GraphQL](/help/assets/content-fragments/graphql-api-content-fragments.md)** – Pour plus d’informations sur la diffusion découplée de fragments de contenu
