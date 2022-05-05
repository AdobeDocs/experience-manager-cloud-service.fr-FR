---
title: Création d’une requête API - Configuration sans affichage
description: Découvrez comment utiliser l’API GraphQL pour diffuser sans interface du contenu de fragment de contenu et AEM l’API REST Assets pour gérer les fragments de contenu.
exl-id: 2b72f222-2ba5-4a21-86e4-40c763679c32
source-git-commit: c44c58398da3d82be04e22a5e4293e79361a8def
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 59%

---

# Création d’une requête API - Configuration sans affichage {#accessing-delivering-content-fragments}

Découvrez comment utiliser l’API GraphQL pour diffuser sans interface du contenu de fragment de contenu et AEM l’API REST Assets pour gérer les fragments de contenu.

>[!NOTE]
>
>Certaines fonctionnalités de cette fonctionnalité sont disponibles dans le canal de version préliminaire. En particulier, les fonctionnalités liées aux requêtes persistantes.
> 
>Voir [Documentation sur les canaux de version préliminaire](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#enable-prerelease) pour plus d’informations sur l’activation de la fonctionnalité dans votre environnement.

## En quoi consistent les API REST GraphQL et Assets ? {#what-are-the-apis}

[Maintenant que vous avez créé des fragments de contenu](create-content-fragment.md), vous pouvez utiliser les API d’AEM pour une diffusion découplée.

* [L’API GraphQL](/help/headless/graphql-api/content-fragments.md) permet de créer des requêtes d’accès et de diffusion de fragments de contenu. Cette API offre l’ensemble de fonctionnalités le plus robuste pour interroger et utiliser du contenu de fragment de contenu.
   * Pour l’utiliser, les [points de fin doivent être définis et activés dans AEM](/help/headless/graphql-api/graphql-endpoint.md), et si nécessaire, l’[interface GraphiQL installée](/help/headless/graphql-api/graphiql-ide.md).
* [L’API REST Assets](/help/assets/content-fragments/assets-api-content-fragments.md) permet de créer et de modifier des fragments de contenu (et d’autres ressources).

Le reste de ce guide porte sur l’accès à GraphQL et la diffusion de fragments de contenu.

## Activation du point d’entrée GraphQL

Avant de pouvoir utiliser les API GraphQL, un point d’entrée GraphQL doit être créé.

1. Accédez à **Outils**, **Général**, puis sélectionnez **GraphQL**.
1. Sélectionnez **Créer**.
1. La boîte de dialogue **Créer un point d’entrée GraphQL** s’ouvre. Vous pouvez spécifier ici les éléments suivants :
   * **Nom** : nom du point d’entrée ; vous pouvez saisir du texte.
   * **Utilisation du schéma GraphQL fourni par**: utilisez la liste déroulante pour sélectionner la configuration requise.
1. Confirmez avec **Créer**.
1. Dans la console, une **Chemin** s’affiche désormais en fonction de la configuration créée précédemment. Il s’agit du chemin utilisé pour exécuter des requêtes GraphQL.

   ```
   /content/cq:graphql/<configuration-name>/endpoint
   ```

Plus d’informations sur l’activation [Les points d’entrée GraphQL se trouvent ici](/help/headless/graphql-api/graphql-endpoint.md).

## Requête de contenu à l’aide de GraphQL avec GraphiQL

Les architectes de l’information doivent concevoir des requêtes pour leurs points d’entrée de canaux afin de diffuser du contenu. Ces requêtes ne doivent généralement être prises en compte qu’une seule fois par point d’entrée et par modèle. Pour les besoins de ce guide de prise en main, nous ne devrons en créer qu’une.

GraphiQL est un IDE qui peut être installé sur un environnement AEM. Suivez les étapes de la section [Utilisation de l’IDE GraphiQL](/help/headless/graphql-api/graphiql-ide.md) pour effectuer l’installation sur votre environnement AEM.

1. Connectez-vous à AEM en as a Cloud Service et accédez à l’interface GraphiQL :

   Vous pouvez accéder à l’éditeur de requêtes à partir de :

   * **Outils** -> **Général** -> **Éditeur de requêtes GraphQL**
   * directement; par exemple, `http://localhost:4502/aem/graphiql.html`

1. L’IDE GraphiQL est un éditeur de requêtes intégré au navigateur pour GraphQL. Vous pouvez l’utiliser pour créer des requêtes afin de récupérer des fragments de contenu afin de les diffuser sans affichage au format JSON.
   * La liste déroulante en haut à droite vous permet de sélectionner le point de terminaison.
   * Un panneau de gauche répertorie les requêtes persistantes (le cas échéant).
   * Le panneau du milieu à gauche vous permet de créer votre requête.
   * Le panneau du milieu droit affiche les résultats.
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

* **[Fragments de contenu](/help/assets/content-fragments/content-fragments.md)** – Pour plus d’informations sur la création et la gestion de fragments de contenu
* **[Prise en charge des fragments de contenu dans l’API HTTP AEM Assets](/help/assets/content-fragments/assets-api-content-fragments.md)** – Pour plus d’informations sur l’accès direct au contenu AEM via l’API HTTP, via des opérations CRUD (création, lecture, mise à jour, suppression)
* **[API GraphQL](/help/headless/graphql-api/content-fragments.md)** – Pour plus d’informations sur la diffusion découplée de fragments de contenu
