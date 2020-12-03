---
title: Diffusion de contenu sans en-tête utilisant des fragments de contenu avec GraphQL
description: Découvrez comment utiliser les fragments de contenu dans Adobe Experience Manager (AEM) en tant que Cloud Service avec GraphQL pour la Diffusion de contenu sans en-tête.
translation-type: tm+mt
source-git-commit: 1e9596fb12a38f5c4c6e15d7c33af86e59e76083
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 0%

---


# Diffusion de contenu sans en-tête utilisant des fragments de contenu avec GraphQL {#headless-content-delivery-using-content-fragments-with-graphQL}

>[!CAUTION]
>
>L’AEM API GraphQL, pour Content Fragment Diffusion, sera disponible début 2021.
>
>La documentation correspondante est déjà disponible à des fins de prévisualisation.

Avec Adobe Experience Manager (AEM) en tant que Cloud Service, vous pouvez utiliser les fragments de contenu, ainsi que l’API AEM GraphQL (une implémentation personnalisée, basée sur la norme GraphQL), pour fournir du contenu structuré à utiliser dans vos applications.

## CMS sans en-tête {#headless-cms}

Un système de Gestion de contenu sans affichage (CMS) est :

* &quot;*Un système de gestion de contenu sans tête, ou CMS sans tête, est un système de gestion de contenu dorsal uniquement (CMS) créé à partir du sol en tant que référentiel de contenu qui rend le contenu accessible via une API pour l&#39;affichage sur n&#39;importe quel périphérique.*

   *Le terme &quot;sans tête&quot; vient du concept de découper la &quot;tête&quot; (le front end, c&#39;est-à-dire le site web) du &quot;corps&quot; (le back end, c&#39;est-à-dire le référentiel de contenu)*&quot;.

   Voir [Wikipedia](https://en.wikipedia.org/wiki/Headless_content_management_system).

En termes de création de fragments de contenu en AEM, cela signifie que :

* Vous pouvez utiliser Fragments de contenu pour créer du contenu qui n’est pas principalement destiné à être publié directement (1:1) sur des pages formatées.

* Le contenu de vos fragments de contenu sera structuré d’une manière prédéterminée, selon les modèles de fragments de contenu. Cela simplifie l&#39;accès à vos applications, ce qui permettra de traiter davantage votre contenu.

>[!NOTE]
>
>Voir [En-tête et AEM](/help/implementing/developing/headless/introduction.md) pour une introduction au développement sans tête pour AEM Sites en tant que Cloud Service.

## GraphQL - Présentation {#graphql-overview}

GraphQL est :

* &quot;*...un langage de requête pour les API et un runtime pour répondre à ces requêtes avec vos données existantes. GraphQL fournit une description complète et compréhensible des données de votre API, donne aux clients la possibilité de demander exactement ce dont ils ont besoin et rien de plus, facilite l&#39;évolution des API au fil du temps et permet de puissants outils de développement.*&quot;.

   Voir [GraphQL.org](https://graphql.org)

* &quot;*...une spécification ouverte pour une couche d’API flexible. Placez GraphQL sur vos soutiens existants pour créer des produits plus rapidement que jamais...*&quot;.

   Voir [Explore GraphQL](https://www.graphql.com). &quot;*Explore GraphQL est géré par l&#39;équipe Apollo. Notre objectif est de donner aux développeurs et aux leaders techniques du monde entier tous les outils dont ils ont besoin pour comprendre et adopter GraphQL.*&quot;.

L&#39;[AEM API GraphQL](#aem-graphql-api) vous permet d&#39;effectuer des requêtes (complexes) sur vos [Fragments de contenu](/help/assets/content-fragments/content-fragments.md); chaque requête étant conforme à un type de modèle spécifique. Le contenu renvoyé peut alors être utilisé par vos applications.

### Terminologie GraphQL {#graphql-terminology}

GraphQL utilise les éléments suivants :

* **[Requêtes](https://graphql.org/learn/queries/)**

* **[Schémas et types](https://graphql.org/learn/schema/)**  : à l&#39;aide de ces éléments, GraphQL présente les types et les opérations autorisés pour l&#39;implémentation de AEM GraphQL.

* **[Champs](https://graphql.org/learn/queries/#fields)**

* **Point de terminaison**  GraphQL : chemin d’AEM qui répond aux requêtes GraphQL et permet d’accéder aux schémas GraphQL.

Voir l&#39;[(GraphQL.org) Introduction à GraphQL](https://graphql.org/learn/) pour des détails complets, y compris les [Bonnes pratiques](https://graphql.org/learn/best-practices/).

### Types de Requêtes GraphQL {#graphql-query-types}

Avec GraphQL, vous pouvez effectuer des requêtes pour l&#39;un ou l&#39;autre des éléments suivants :

* **Entrée unique**

* **[Liste des entrées](https://graphql.org/learn/schema/#lists-and-non-null)**

## aem API GraphQL {#aem-graphql-api}

Pour [Adobe Experience as a Cloud Experience, une implémentation personnalisée de l’API GraphQL standard](/help/assets/content-fragments/graphql-api-content-fragments.md) a été implémentée.

L’implémentation de l’API GraphQL AEM est basée sur les [bibliothèques Java GraphQL](https://graphql.org/code/#java).

## Fragments de contenu à utiliser avec l’API AEM GraphQL {#content-fragments-use-with-aem-graphql-api}

[Les ](#content-fragments) fragments de contenu peuvent servir de base à GraphQL pour les requêtes AEM en tant que :

* Ils vous permettent de concevoir, créer, traiter et publier du contenu indépendant des pages.
* Les [modèles de fragments de contenu](#content-fragments-models) fournissent la structure requise au moyen de types de données définis.
* La [Référence du fragment](#fragment-references), disponible lors de la définition d&#39;un modèle, peut être utilisée pour définir des couches supplémentaires de structure.

![Fragments de contenu à utiliser avec des fragments ](assets/cfm-nested-01.png "GraphQLContent pour une utilisation avec GraphQL")

### Fragments de contenu {#content-fragments}

Fragments de contenu:

* Contient du contenu structuré.

* Ils sont basés sur un [modèle de fragment de contenu](#content-fragments-models), qui prédéfinit la structure du fragment obtenu.

### Modèles de fragment de contenu {#content-fragments-models}

[Modèles de fragment de contenu](/help/assets/content-fragments/content-fragments-models.md) :

* Fournissez les types de données et les champs requis pour GraphQL. Ils s&#39;assurent que votre application ne demande que ce qui est possible et reçoit ce qui est attendu.

* Le type de données **[Références de fragment](#fragment-references)** peut être utilisé dans votre modèle pour référencer un autre fragment de contenu et ainsi introduire des niveaux de structure supplémentaires.

### Références de fragments {#fragment-references}

Référence du fragment **[](/help/assets/content-fragments/content-fragments-models.md#fragment-reference-nested-fragments)** :

* Est particulièrement intéressant en conjonction avec GraphQL.

* Type de données spécifique qui peut être utilisé lors de la définition d’un modèle de fragment de contenu.

* Fait référence à un autre fragment, en fonction d’un modèle de fragment de contenu spécifique.

* Permet de récupérer des données structurées.

   * Lorsqu’il est défini comme **flux multiple**, plusieurs sous-fragments peuvent être référencés (récupérés) par le fragment principal.

### Prévisualisation JSON {#json-preview}

Pour faciliter la conception et le développement de votre modèle de fragment de contenu, vous pouvez prévisualisation [sortie JSON](/help/assets/content-fragments/content-fragments-json-preview.md).

## Apprendre à utiliser GraphQL avec AEM - Exemple de contenu et de Requêtes {#learn-graphql-with-aem-sample-content-queries}

Voir [Apprendre à utiliser GraphQL avec AEM - Exemple de contenu et de Requêtes](/help/assets/content-fragments/content-fragments-graphql-samples.md) pour une présentation de l&#39;utilisation de l&#39;API AEM GraphQL.

## Didacticiel - Prise en main de AEM sans en-tête et de GraphQL

Vous recherchez un didacticiel pratique ? Consultez [Prise en main de AEM didacticiel sans en-tête et GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html) de bout en bout illustrant comment créer et exposer du contenu à l’aide des API GraphQL d’AEM et consommé par une application externe, dans un scénario CMS sans en-tête.