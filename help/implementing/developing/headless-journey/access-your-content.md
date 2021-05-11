---
title: Comment accéder à votre contenu via les API d'Diffusion AEM
description: Dans cette partie du Parcours de développement AEM sans tête, apprenez à utiliser les requêtes GraphQL pour accéder à votre contenu Fragments de contenu.
hide: true
hidefromtoc: true
index: false
exl-id: 5ef557ff-e299-4910-bf8c-81c5154ea03f
translation-type: tm+mt
source-git-commit: 4a36cd3206784c0e4e3ed3d7007c83f44f1d5ee0
workflow-type: tm+mt
source-wordcount: '1381'
ht-degree: 18%

---

# Comment accéder à votre contenu via les API d&#39;Diffusion d&#39;AEM {#access-your-content}

>[!CAUTION]
>
>TRAVAUX EN COURS - La création de ce document est en cours et ne doit pas être comprise comme complète ou définitive ni être utilisée à des fins de production.

Dans cette partie du [Parcours de développement AEM sans en-tête,](overview.md) vous pouvez apprendre à utiliser les requêtes GraphQL pour accéder au contenu de vos fragments de contenu et le transmettre à votre application (diffusion sans en-tête).

## L&#39;histoire jusqu&#39;à présent {#story-so-far}

Dans le document précédent du parcours sans tête AEM, [Comment modéliser votre contenu](model-your-content.md) vous avez appris les principes de base de la modélisation du contenu dans AEM. Vous devez donc maintenant comprendre comment modéliser votre structure de contenu, puis réaliser cette structure à l’aide des modèles de fragments de contenu et des fragments de contenu AEM :

* Reconnaissez les concepts et la terminologie liés à la modélisation du contenu.
* Comprenez pourquoi la modélisation du contenu est nécessaire pour la diffusion de contenu sans en-tête.
* Découvrez comment réaliser cette structure à l’aide de modèles AEM de fragments de contenu (et créez du contenu avec des fragments de contenu).
* comprendre comment modéliser votre contenu ; principes avec des exemples de base.

Cet article s&#39;appuie sur ces principes de base pour vous aider à accéder à votre contenu sans en-tête existant dans AEM à l&#39;aide de l&#39;API AEM GraphQL.

* **Audience** : Début
* **Objectif** : Découvrez comment accéder au contenu de vos fragments de contenu à l’aide des requêtes GraphQL AEM :
   * Présentation de GraphQL et de l’API GraphQL AEM.
   * Découvrez les détails de l’API GraphQL AEM.
   * Regardez quelques exemples de requêtes pour voir comment les choses fonctionnent dans la pratique.

## Vous souhaitez donc accéder à votre contenu ? {#so-youd-like-to-access-your-content}

Donc...vous disposez de tout ce contenu, soigneusement structuré (dans Fragments de contenu), et vous n’avez qu’à attendre pour alimenter votre nouvelle application. La question est : comment y arriver ?

Vous avez besoin d’un moyen de cible de contenu spécifique, de sélectionner ce dont vous avez besoin et de le renvoyer à votre application pour un traitement ultérieur.

Avec Adobe Experience Manager (AEM) en tant que Cloud Service, vous pouvez accéder de manière sélective à vos fragments de contenu, à l’aide de l’API AEM GraphQL, pour renvoyer uniquement le contenu dont vous avez besoin. Cela signifie que vous pouvez réaliser une diffusion illisible de contenu structuré à utiliser dans vos applications.

>[!NOTE]
>
>AEM API GraphQL est une implémentation personnalisée, basée sur la spécification standard de l&#39;API GraphQL.

## GraphQL - Introduction {#graphql-introduction}

GraphQL est une spécification open source qui fournit :

* langage de requête qui vous permet de sélectionner un contenu spécifique à partir d’objets structurés.
* un runtime pour réaliser ces requêtes avec votre contenu structuré.

GraphQL est une API *fortement* typée. Cela signifie que *tout* contenu doit être clairement structuré et organisé par type, de sorte que GraphQL *comprenne* ce à quoi accéder et comment. Les champs de données sont définis dans des schémas GraphQL, qui définissent la structure de vos objets de contenu.

Les points de terminaison GraphQL fournissent ensuite les chemins qui répondent aux requêtes GraphQL.

Cela signifie que votre application peut sélectionner précisément, de manière fiable et efficace le contenu dont elle a besoin - exactement ce dont vous avez besoin lorsqu&#39;elle est utilisée avec AEM.

>[!NOTE]
>
>Voir *GraphQL*.org et *GraphQL*.com.

<!--
## AEM and GraphQL {#aem-graphql}

GraphQL is used in various locations in AEM; for example:

* Content Fragments
  * A customized API has been developed for this use-case (Headless Delivery to your app).
    * This is the AEM GraphQL API.
* Commerce
  * AEM Commerce consumes data from a Commerce platform via GraphQL.
  * There are GraphQL integrations between AEM and various third-party commerce solutions, used with the extension hooks provided by the CIF Core Components.
    * This does not use the AEM GraphQL API.

>[!NOTE]
>
>This step of the Headless Journey is only concerned with the AEM GraphQL API and Content Fragments.
-->

## API AEM GraphQL {#aem-graphql-api}

L’API GraphQL AEM est une version personnalisée basée sur la spécification standard de l’API GraphQL, spécialement configurée pour vous permettre d’effectuer des requêtes (complexes) sur vos fragments de contenu.

Les fragments de contenu sont utilisés, dans la mesure où le contenu est structuré selon les modèles de fragments de contenu. Cela répond à une exigence de base de GraphQL.

* Un modèle de fragment de contenu est constitué d’un ou de plusieurs champs.
   * Chaque champ est défini selon un type de données.
* Les modèles de fragments de contenu sont utilisés pour générer les Schémas GraphQL AEM correspondants.

Pour accéder à GraphQL pour AEM (et au contenu), un point de terminaison est utilisé pour fournir le chemin d&#39;accès.

Le contenu renvoyé, via l&#39;API AEM GraphQL, peut alors être utilisé par vos applications.

Pour vous aider à saisir directement et à tester des requêtes, une mise en oeuvre de l&#39;interface standard de GraphiQL est également disponible pour une utilisation avec AEM GraphQL (cela peut être installé avec AEM). Il fournit des fonctionnalités telles que la mise en surbrillance de la syntaxe, la saisie semi-automatique et la suggestion automatique, ainsi qu’un historique et une documentation en ligne.

>[!NOTE]
>
>L’implémentation de l’API AEM GraphQL repose sur les bibliothèques Java GraphQL.

<!--
### Use Cases for Author and Publish Environments {#use-cases-author-publish-environments}

The use cases for the AEM GraphQL API can depend on the type of AEM as a Cloud Service environment:

* Publish environment; used to: 
  * Query content for JS application (standard use-case)

* Author environment; used to: 
  * Query content for "content management purposes":
    * GraphQL in AEM as a Cloud Service is currently a read-only API.
    * The REST API can be used for CR(u)D operations.
-->

## Fragments de contenu à utiliser avec l’API AEM GraphQL {#content-fragments-use-with-aem-graphql-api}

Les fragments de contenu peuvent servir de base à GraphQL pour les schémas et requêtes AEM en tant que :

* Ils vous permettent de concevoir, de créer, de traiter et de publier du contenu indépendant des pages qui peut être diffusé sans encombre.
* Ils sont basés sur un modèle de fragment de contenu, qui prédéfinit la structure du fragment obtenu à l’aide d’une sélection de types de données.
* D’autres couches de structure peuvent être obtenues avec le type de données Référence de fragment, disponible lors de la définition d’un modèle.

### Modèles de fragment de contenu {#content-fragments-models}

Ces modèles de fragment de contenu :

* Sont utilisés pour générer les Schémas, une fois **Activés**.
* fournissent les types de données et les champs requis pour GraphQL ; garantissent que votre application ne demande que ce qui est possible et reçoive ce qui est attendu.
* Le type de données **Références de fragments** peut être utilisé dans votre modèle pour faire référence à un autre fragment de contenu et introduit ainsi des niveaux de structure supplémentaires.

### Références à un fragment {#fragment-references}

La **référence à un fragment** :

* Est un type de données spécifique disponible lors de la définition d’un modèle de fragment de contenu.
* fait référence à un autre fragment, en fonction d’un modèle de fragment de contenu spécifique ;
* Permet de créer, puis de récupérer, des données structurées.

   * Lorsqu’elle est définie comme **référence à sources multiples**, plusieurs sous-fragments peuvent être référencés (récupérés) par le fragment principal.

### Prévisualisation JSON {#json-preview}

Pour faciliter la conception et le développement de vos modèles de fragments de contenu, vous pouvez prévisualisation la sortie JSON dans l’éditeur de fragments de contenu.

![Prévisualisation JSON ](assets/cfm-model-json-preview.png "PreviewJSON")

<!--
## GraphQL Schema Generation from Content Fragments {#graphql-schema-generation-content-fragments}

GraphQL is a strongly typed API, which means that content must be clearly structured and organized by type. The GraphQL specification provides a series of guidelines on how to create a robust API for interrogating content on a certain instance. To do this, a client needs to fetch the Schema, which contains all the types necessary for a query. 

For Content Fragments, the GraphQL schemas (structure and types) are based on **Enabled** Content Fragment Models and their data types.

>[!CAUTION]
>
>All the GraphQL schemas (derived from Content Fragment Models that have been **Enabled**) are readable through the GraphQL endpoint.
>
>This means that you need to ensure that no sensitive content is available, to ensure that no sensitive data is exposed via GraphQL endpoints; for example, this includes information that could be present as field names in the model definition.

For example, if a user created a Content Fragment Model called `Article`, then AEM generates the object `article` that is of a type `ArticleModel`. The fields within this type correspond to the fields and data types defined in the model.

1. A Content Fragment Model:

   ![Content Fragment Model for use with GraphQL](assets/graphqlapi-cfmodel.png "Content Fragment Model for use with GraphQL")

1. The corresponding GraphQL schema (output from GraphiQL automatic documentation):
   ![GraphQL Schema based on Content Fragment Model](assets/graphqlapi-cfm-schema.png "GraphQL Schema based on Content Fragment Model")

   This shows that the generated type `ArticleModel` contains several [fields](#fields). 
   
   * Three of them have been controlled by the user: `author`, `main` and `referencearticle`.

   * The other fields were added automatically by AEM, and represent helpful methods to provide information about a certain Content Fragment; in this example, `_path`, `_metadata`, `_variations`. These [helper fields](#helper-fields) are marked with a preceding `_` to distinguish between what has been defined by the user and what has been auto-generated.

1. After a user creates a Content Fragment based on the Article model, it can then be interrogated through GraphQL. For examples, see the Sample Queries.md#graphql-sample-queries) (based on a sample Content Fragment structure for use with GraphQL.

In GraphQL for AEM, the schema is flexible. This means that it is auto-generated each and every time a Content Fragment Model is created, updated or deleted. The data schema caches are also refreshed when you update a Content Fragment Model.

The Sites GraphQL service listens (in the background) for any modifications made to a Content Fragment Model. When updates are detected, only that part of the schema is regenerated. This optimization saves time and provides stability.

So for example, if you:

1. Install a package containing `Content-Fragment-Model-1` and `Content-Fragment-Model-2`:
 
   1. GraphQL types for `Model-1` and `Model-2` will be generated.

1. Then modify `Content-Fragment-Model-2`:

   1. Only the `Model-2` GraphQL type will get updated.

   1. Whereas `Model-1` will remain the same. 

>[!NOTE]
>
>This is important to note in case you want to do bulk updates on Content Fragment Models through the REST api, or otherwise.

The schema is served through the same endpoint as the GraphQL queries, with the client handling the fact that the schema is called with the extension `GQLschema`. For example, performing a simple `GET` request on `/content/cq:graphql/global/endpoint.GQLschema` will result in the output of the schema with the Content-type: `text/x-graphql-schema;charset=iso-8859-1`.

### Schema Generation - Unpublished Models {#schema-generation-unpublished-models}

When Content Fragments are nested it can happen that a parent Content Fragment Model is published, but a referenced model is not.

>[!NOTE]
>
>The AEM UI prevents this happening, but if publishing is made programmatically, or with content packages, it can occur.

When this happens, AEM generates an *incomplete* Schema for the parent Content Fragment Model. This means that the Fragment Reference, which is dependent on the unpublished model, is removed from the schema.

## AEM GraphQL Endpoints {#aem-graphql-endpoints}

An endpoint is the path used to access GraphQL for AEM. Using this path you (or your app) can:

* access the GraphQL schemas,
* send your GraphQL queries,
* receive the responses (to your GraphQL queries).

AEM allows for:

* A global endpoint - available for use by all sites.
* Endpoints for specific Sites configurations - that you can configure (in the Configuration Browser), specific to a specified site/project.

## Permissions {#permissions}

The permissions are those required for accessing Assets.

## The AEM GraphiQL Interface {#aem-graphiql-interface}

To help you directly input, and test queries, an implementation of the standard GraphiQL interface is available for use with AEM GraphQL. This can be installed with AEM.

>[!NOTE]
>
>GraphiQL is bound the global endpoint (and does not work with other endpoints for specific Sites configurations).

It provides features such as syntax-highlighting, auto-complete, auto-suggest, together with a history and online documentation.

![GraphiQL Interface](assets/graphiql-interface.png "GraphiQL Interface")
-->

## Utilisation de l’API GraphQL d’AEM {#actually-using-aem-graphiql}

### Configuration initiale {#initial-setup}

Avant de commencer avec des requêtes sur votre contenu, vous devez :

* Activer votre point de terminaison
   * Utiliser Outils -> Sites -> GraphQL
   * [Activation de votre point d’entrée GraphQL](/help/assets/content-fragments/graphql-api-content-fragments.md#enabling-graphql-endpoint)

* Installer GraphiQL (si nécessaire)
   * Installé en tant que package dédié
   * [Installation de l’interface AEM GraphiQL](/help/assets/content-fragments/graphql-api-content-fragments.md#installing-graphiql-interface)

### Exemple de structure {#sample-structure}

Pour utiliser effectivement l’API GraphQL AEM dans une requête, nous pouvons utiliser les deux structures de base du modèle de fragment de contenu :

* Entreprise
   * Nom - Texte
   * PDG (Personne) - Référence sur les fragments
   * Employés (personnes) - Référence(s) de fragment
* Personne
   * Nom - Texte
   * Prénom - Texte

Comme vous pouvez le voir, les champs PDG et Employés font référence aux fragments Personne.

Les modèles de fragments seront utilisés :

* lors de la création du contenu dans l’éditeur de fragments de contenu
* pour générer les schémas GraphQL que vous allez requête

### Où tester vos Requêtes {#where-to-test-your-queries}

Les requêtes peuvent être entrées dans l’interface GraphiQL, par exemple à l’adresse suivante :

* `http://localhost:4502/content/graphiql.html `

![Interface GraphiQL](assets/graphiql-interface.png "Interface GraphiQL")

### Prise en main des Requêtes {#getting-Started-with-queries}

Une requête simple consiste à renvoyer le nom de toutes les entrées du schéma de Société. Vous demandez ici une liste de tous les noms de société :

```xml
query {
  companyList {
    items {
      name
    }
  }
}
```

Une requête un peu plus complexe consiste à sélectionner toutes les personnes qui n&#39;ont pas de nom &quot;Emplois&quot;. Ceci filtrera toutes les personnes pour celles qui ne portent pas le nom Tâches. Ceci est réalisé avec l&#39;opérateur EQUALS_NOT (il y en a beaucoup d&#39;autres) :

```xml
query {
  personList(filter: {
    name: {
      _expressions: [
        {
          value: "Jobs"
          _operator: EQUALS_NOT
        }
      ]
    }
  }) {
    items {
      name
      firstName
    }
  }
}
```

Vous pouvez également créer des requêtes plus complexes. Par exemple, requête pour toutes les sociétés qui ont au moins un employé nommé &quot;Smith&quot;. Cette requête illustre le filtrage pour toute personne du nom de &quot;Smith&quot;, renvoyant des informations à partir des fragments imbriqués :

```xml
query {
  companyList(filter: {
    employees: {
      _match: {
        name: {
          _expressions: [
            {
              value: "Smith"
            }
          ]
        }
      }
    }
  }) {
    items {
      name
      ceo {
        name
        firstName
      }
      employees {
        name
        firstName
      }
    }
  }
}
```

<!-- need code / curl / cli examples-->

Pour obtenir des détails complets sur l’utilisation de l’API GraphQL AEM, ainsi que la configuration des éléments nécessaires, vous pouvez vous reporter aux éléments suivants :

* Apprendre à utiliser GraphQL avec AEM
* Exemple de structure de fragment de contenu
* Apprendre à utiliser GraphQL avec AEM – Exemple de contenu et de requêtes

## Eléments suivants {#whats-next}

Maintenant que vous avez appris à accéder à votre contenu sans en-tête et à le requête à l’aide de l’API AEM GraphQL, vous pouvez [apprendre à utiliser l’API REST pour accéder au contenu de vos fragments de contenu](/help/implementing/developing/headless-journey/update-your-content.md) et le mettre à jour.

## Ressources supplémentaires {#additional-resources}

* [GraphQL.org](https://graphql.org)
   * [Schémas](https://graphql.org/learn/schema/)
   * [Variables](https://graphql.org/learn/queries/#variables)
   * [Bibliothèques Java GraphQL](https://graphql.org/code/#java)
* [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql)
* [Apprendre à utiliser GraphQL avec AEM](/help/assets/content-fragments/graphql-api-content-fragments.md)
   * [Activation de votre point d’entrée GraphQL](/help/assets/content-fragments/graphql-api-content-fragments.md#enabling-graphql-endpoint)
   * [Installation de l’interface AEM GraphiQL](/help/assets/content-fragments/graphql-api-content-fragments.md#installing-graphiql-interface)
* [Exemple de structure de fragment de contenu](/help/assets/content-fragments/content-fragments-graphql-samples.md#content-fragment-structure-graphql)
* [Apprendre à utiliser GraphQL avec AEM – Exemple de contenu et de requêtes](/help/assets/content-fragments/content-fragments-graphql-samples.md)
   * [Exemple de requête – Un fragment de ville unique et spécifique](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-single-specific-city-fragment)
   * [Exemple de requête pour des métadonnées – Liste des métadonnées pour les distinctions intitulées GB](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-metadata-awards-gb)
   * [Exemple de requête – Toutes les villes avec une variante nommée](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-cities-named-variation)
* [Activation de la fonctionnalité de fragments de contenu dans l’explorateur de configurations](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser)
* [Utilisation de fragments de contenu](/help/assets/content-fragments/content-fragments.md)
   * [Modèles de fragment de contenu](/help/assets/content-fragments/content-fragments-models.md)
   * [Sortie JSON](/help/assets/content-fragments/content-fragments-json-preview.md)
* [Comprendre le partage des ressources entre Origines (CORS)](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=fr#understand-cross-origin-resource-sharing-(cors))
* [Génération de jetons d’accès pour les API côté serveur](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md)
* [Prise en main de AEM sans](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html?lang=fr)  en-tête - Une courte série de didacticiels vidéo qui présente un aperçu de l&#39;utilisation des fonctionnalités sans en-tête AEM, y compris la modélisation de contenu et GraphQL.
