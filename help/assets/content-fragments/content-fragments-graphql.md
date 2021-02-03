---
title: Diffusion de contenu sans en-tête utilisant des fragments de contenu avec GraphQL
description: Découvrez comment utiliser les fragments de contenu dans Adobe Experience Manager (AEM) en tant que Cloud Service avec GraphQL pour la Diffusion de contenu sans en-tête.
translation-type: tm+mt
source-git-commit: 54b377c6d98398fd5066dc4a3337a3877b9e3ed7
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 1%

---


# Diffusion de contenu sans en-tête utilisant des fragments de contenu avec GraphQL {#headless-content-delivery-using-content-fragments-with-graphQL}

Avec Adobe Experience Manager (AEM) en tant que Cloud Service, vous pouvez utiliser les fragments de contenu, ainsi que l’API AEM GraphQL (une implémentation personnalisée, basée sur la norme GraphQL), pour fournir du contenu structuré à utiliser dans vos applications. La possibilité de personnaliser une seule requête d&#39;API vous permet de récupérer et de diffuser le contenu spécifique que vous souhaitez/souhaitez rendre (en tant que réponse à la requête d&#39;API unique).

>[!NOTE]
>
>Voir [En-tête et AEM](/help/implementing/developing/headless/introduction.md) pour une introduction au développement sans tête pour AEM Sites en tant que Cloud Service.

## CMS sans en-tête {#headless-cms}

Un système de Gestion de contenu sans affichage (CMS) est :

* &quot;*Un système de gestion de contenu sans tête, ou CMS sans tête, est un système de gestion de contenu dorsal uniquement (CMS) créé à partir du sol en tant que référentiel de contenu qui rend le contenu accessible via une API pour l&#39;affichage sur n&#39;importe quel périphérique.*

   Voir [Wikipedia](https://en.wikipedia.org/wiki/Headless_content_management_system).

En termes de création de fragments de contenu en AEM, cela signifie que :

* Vous pouvez utiliser Fragments de contenu pour créer du contenu qui n’est pas principalement destiné à être publié directement (1:1) sur des pages formatées.

* Le contenu de vos fragments de contenu sera structuré d’une manière prédéterminée, selon les modèles de fragments de contenu. Cela simplifie l&#39;accès à vos applications, ce qui permettra de traiter davantage votre contenu.

## GraphQL - Présentation {#graphql-overview}

GraphQL est :

* &quot;*...un langage de requête pour les API et un runtime pour répondre à ces requêtes avec vos données existantes.*&quot;.

   Voir [GraphQL.org](https://graphql.org)

L&#39;[AEM API GraphQL](#aem-graphql-api) vous permet d&#39;effectuer des requêtes (complexes) sur vos [Fragments de contenu](/help/assets/content-fragments/content-fragments.md); chaque requête étant conforme à un type de modèle spécifique. Le contenu renvoyé peut alors être utilisé par vos applications.

## aem API GraphQL {#aem-graphql-api}

Pour Adobe Experience as a Cloud Experience, une implémentation personnalisée de l’API GraphQL standard a été développée. Voir [AEM API GraphQL à utiliser avec les fragments de contenu](/help/assets/content-fragments/graphql-api-content-fragments.md) pour plus d’informations.

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

* Sont utilisés pour générer les [Schémas](https://graphql.org/learn/schema/), une fois **Activé**.

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

Pour faciliter la conception et le développement de vos modèles de fragments de contenu, vous pouvez prévisualisation [sortie JSON](/help/assets/content-fragments/content-fragments-json-preview.md).

## Apprendre à utiliser GraphQL avec AEM - Exemple de contenu et de Requêtes {#learn-graphql-with-aem-sample-content-queries}

Voir [Apprendre à utiliser GraphQL avec AEM - Exemple de contenu et de Requêtes](/help/assets/content-fragments/content-fragments-graphql-samples.md) pour une présentation de l&#39;utilisation de l&#39;API AEM GraphQL.

## Didacticiel - Prise en main de AEM sans en-tête et de GraphQL

Vous recherchez un didacticiel pratique ? Consultez [Prise en main de AEM didacticiel sans en-tête et GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html) de bout en bout illustrant comment créer et exposer du contenu à l’aide des API GraphQL d’AEM et consommé par une application externe, dans un scénario CMS sans en-tête.