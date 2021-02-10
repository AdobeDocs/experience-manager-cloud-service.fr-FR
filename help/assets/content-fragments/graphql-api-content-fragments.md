---
title: API GraphQL d’AEM à utiliser avec des fragments de contenu
description: Découvrez comment utiliser les fragments de contenu dans Adobe Experience Manager (AEM) as a Cloud Service avec l’API GraphQL d’AEM pour la diffusion de contenu découplée.
translation-type: tm+mt
source-git-commit: 20f90d46d24fa211d51ef4b59bb56f4b9f963bc3
workflow-type: tm+mt
source-wordcount: '3167'
ht-degree: 71%

---


# API GraphQL d’AEM à utiliser avec des fragments de contenu {#graphql-api-for-use-with-content-fragments}

L’API GraphQL d’Adobe Experience Manager as a Cloud Service (AEM) utilisée avec des fragments de contenu repose principalement sur l’API open source standard GraphQL.

L’utilisation de l’API GraphQL dans AEM permet la diffusion efficace de fragments de contenu aux clients JavaScript dans les implémentations CMS découplées :

* en évitant les demandes d’API itératives comme avec REST ;
* en veillant à ce que la diffusion soit limitée aux exigences spécifiques ;
* Permet la diffusion en bloc de ce qui est exactement nécessaire pour le rendu en tant que réponse à une seule requête d&#39;API.

## L’API GraphQL {#graphql-api}

GraphQL est :

* « *...un langage de requête pour les API et un environnement d’exécution pour répondre à ces requêtes avec vos données existantes. GraphQL fournit une description complète et compréhensible des données de votre API, permet aux clients de demander exactement ce dont ils ont besoin et rien de plus, facilite l’évolution des API au fil du temps et donne accès à de puissants outils de développement.* ».

   Voir [GraphQL.org](https://graphql.org)

* « *...une spécification ouverte pour une couche d’API flexible. Placez GraphQL sur vos back-ends existants pour créer des produits plus rapidement que jamais...* ».

   Voir [Explore GraphQL](https://www.graphql.com).

* *&quot;...un langage et une spécification de requête de données développé en interne par Facebook en 2012 avant d&#39;être publiquement ouvert en 2015. C’est une alternative aux architectures basées sur REST destinée à accroître la productivité des développeurs et à réduire les quantités de données transférées. GraphQL est utilisé en production par des centaines d&#39;organisations de toutes tailles...&quot;*

   Voir [GraphQL Foundation](https://foundation.graphql.org/).

<!--
"*Explore GraphQL is maintained by the Apollo team. Our goal is to give developers and technical leaders around the world all of the tools they need to understand and adopt GraphQL.*". 
-->

Pour plus d’informations sur l’API GraphQL, voir les sections suivantes (parmi de nombreuses autres ressources) :

* Sur [graphql.org](https://graphql.org) :

   * [Présentation de GraphQL](https://graphql.org/learn)

   * [La spécification GraphQL](http://spec.graphql.org/)

* Sur [graphql.com](https://graphql.com) :

   * [Guides](https://www.graphql.com/guides/)

   * [Tutoriels](https://www.graphql.com/tutorials/)

   * [Études de cas](https://www.graphql.com/case-studies/)

La mise en œuvre GraphQL pour AEM repose sur la bibliothèque Java GraphQL standard. Voir :

* [graphQL.org - Java](https://graphql.org/code/#java)

* [GraphQL Java sur GitHub](https://github.com/graphql-java)

### Terminologie GraphQL {#graphql-terminology}

GraphQL utilise les éléments suivants :

* **[Requêtes](https://graphql.org/learn/queries/)**

* **[Schémas et types](https://graphql.org/learn/schema/)** :

   * Les schémas sont générés par AEM en fonction des modèles de fragment de contenu.
   * A l’aide de vos schémas, GraphQL présente les types et les opérations autorisés pour l’implémentation AEM GraphQL.

* **[Champs](https://graphql.org/learn/queries/#fields)**

* **[Point de terminaison GraphQL](#graphql-aem-endpoint)**
   * Chemin d’accès dans AEM qui répond aux requêtes GraphQL et permet d’accéder aux schémas GraphQL.

   * Voir [Activation de votre point de terminaison GraphQL](#enabling-graphql-endpoint) pour plus de détails.

Voir la [Présentation de GraphQL (GraphQL.org)](https://graphql.org/learn/) pour des détails complets, y compris les [Bonnes pratiques](https://graphql.org/learn/best-practices/).

### Types de requêtes GraphQL {#graphql-query-types}

Avec GraphQL, vous pouvez exécuter des requêtes pour renvoyer l&#39;un ou l&#39;autre des éléments suivants :

* Une **entrée unique**

* A **[liste des entrées](https://graphql.org/learn/schema/#lists-and-non-null)**

Vous pouvez également effectuer les opérations suivantes :

* [Requêtes persistantes, mises en cache](#persisted-queries-caching)

## GraphQL pour le point de terminaison AEM {#graphql-aem-endpoint}

Le point d’entrée est le chemin utilisé pour accéder à GraphQL pour AEM. Avec ce chemin, vous (ou votre application) pouvez :

* accéder au schéma GraphQL ;
* envoyer vos requêtes GraphQL ;
* recevoir les réponses (à vos requêtes GraphQL).

Le chemin d’accès au référentiel de GraphQL pour AEM point de terminaison est :

`/content/cq:graphql/global/endpoint`

Votre application peut utiliser le chemin d’accès suivant dans l’URL de demande :

`/content/_cq_graphql/global/endpoint.json`

Pour activer le point de terminaison pour GraphQL pour AEM, vous devez :

>[!CAUTION]
>
>Ces mesures sont susceptibles de changer dans un avenir proche.

* [Activation de votre point de terminaison GraphQL](#enabling-graphql-endpoint)
* [Exécution de configurations supplémentaires](#additional-configurations-graphql-endpoint)

### Activation de votre point de terminaison GraphQL {#enabling-graphql-endpoint}

>[!NOTE]
>
>Voir [Supporting Packages](#supporting-packages) pour plus d&#39;informations sur les packages fournis par Adobe pour simplifier ces étapes.

Pour activer les requêtes GraphQL dans AEM, créez un point de terminaison à `/content/cq:graphql/global/endpoint` :

* Les noeuds `cq:graphql` et `global` doivent être de type `sling:Folder`.
* Le noeud `endpoint` doit être de type `nt:unstructured` et contenir `sling:resourceType` de `graphql/sites/components/endpoint`.

>[!CAUTION]
>
>Un problème est actuellement connu avec le point de terminaison :
>
>* L&#39;entrée `cq:graphql` est visible dans la console **Sites**; au niveau supérieur.
   >  Il ne doit pas être utilisé.


>[!CAUTION]
>
>Le point de terminaison est accessible à tous. Ceci peut, en particulier sur les instances de publication, poser un problème de sécurité, car les requêtes GraphQL peuvent imposer une charge importante au serveur.
>
>Vous pouvez configurer des listes de contrôle d’accès, en fonction de votre cas d’utilisation, sur le point de terminaison.

>[!NOTE]
>
>Votre point de terminaison ne fonctionnera pas de manière standard. Vous devrez fournir [d&#39;autres configurations pour le point de terminaison GraphQL](#additional-configurations-graphql-endpoint) séparément.

>[!NOTE]
>De plus, vous pouvez tester et déboguer des requêtes GraphQL à l&#39;aide de l&#39;IDE [GraphiQL](#graphiql-interface).

### Autres configurations pour le point de terminaison GraphQL {#additional-configurations-graphql-endpoint}

>[!NOTE]
>
>Voir [Supporting Packages](#supporting-packages) pour plus d&#39;informations sur les packages fournis par Adobe pour simplifier ces étapes.

Des configurations supplémentaires sont requises :

* Dispatcher:
   * Pour autoriser les URL requises
   * Obligatoire
* URL Vanity:
   * Pour allouer une URL simplifiée pour le point de terminaison
   * Facultatif
* Configuration OSGi:
   * Configuration de la servlet GraphQL :
      * Gère les requêtes au point de terminaison
      * Le nom de la configuration est `org.apache.sling.graphql.core.GraphQLServlet`. Il doit être fourni en tant que configuration d’usine OSGi.
      * `sling.servlet.extensions` doit être définie sur  `[json]`
      * `sling.servlet.methods` doit être définie sur  `[GET,POST]`
      * `sling.servlet.resourceTypes` doit être définie sur  `[graphql/sites/components/endpoint]`
      * Obligatoire
   * Configuration du servlet schéma :
      * Crée le schéma GraphQL
      * Le nom de la configuration est `com.adobe.aem.graphql.sites.adapters.SlingSchemaServlet`. Il doit être fourni en tant que configuration d’usine OSGi.
      * `sling.servlet.extensions` doit être définie sur  `[GQLschema]`
      * `sling.servlet.methods` doit être définie sur  `[GET]`
      * `sling.servlet.resourceTypes` doit être définie sur  `[graphql/sites/components/endpoint]`
      * Obligatoire
   * Configuration CSRF :
      * Protection de sécurité du point de terminaison
      * Le nom de la configuration est `com.adobe.granite.csrf.impl.CSRFFilter`
      * Ajouter `/content/cq:graphql/global/endpoint` à la liste existante des chemins exclus (`filter.excluded.paths`)
      * Obligatoire

### Packages pris en charge {#supporting-packages}

Pour simplifier la configuration d’un point de terminaison GraphQL, l’Adobe fournit le package [Exemple de projet GraphQL](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faemcloud%2Fpublic%2Faem-graphql%2Fgraphql-sample.zip).

Cette archive contient à la fois [la configuration supplémentaire requise](#additional-configurations-graphql-endpoint) et [le point de terminaison GraphQL](#enabling-graphql-endpoint). S&#39;il est installé sur une instance AEM ordinaire, il expose un point de terminaison GraphQL entièrement fonctionnel à `/content/cq:graphql/global/endpoint`.

Ce paquet est destiné à être un plan d&#39;ensemble pour vos propres projets GraphQL. Consultez le package **README** pour plus d&#39;informations sur l&#39;utilisation du package.

Si vous préférez créer manuellement la configuration requise, Adobe fournit également un [package de contenu GraphQL Endpoint Content](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faemcloud%2Fpublic%2Faem-graphql%2Fgraphql-global-endpoint.zip) dédié. Ce package de contenu contient uniquement le point de terminaison GraphQL, sans aucune configuration.

## Interface GraphiQL {#graphiql-interface}

<!--
AEM Graph API includes an implementation of the standard [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql) interface. This allows you to directly input, and test, queries.
-->

Une implémentation de l&#39;interface standard [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql) est disponible pour une utilisation avec AEM GraphQL. Il peut être [installé avec AEM](#installing-graphiql-interface).

Cette interface vous permet de saisir directement et de tester les requêtes.

Par exemple :

* `http://localhost:4502/content/graphiql.html`

Vous disposez de fonctionnalités telles que la mise en surbrillance de la syntaxe, la saisie semi-automatique et la suggestion automatique, ainsi qu’un historique et une documentation en ligne :

![Interface GraphiQL](assets/cfm-graphiql-interface.png "Interface GraphiQL")

### Installation de l&#39;interface AEM GraphiQL {#installing-graphiql-interface}

L&#39;interface utilisateur de GraphiQL peut être installée sur AEM avec un package dédié : le package [GraphiQL Content Package v0.0.4](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faemcloud%2Fpublic%2Faem-graphql%2Fgraphiql-0.0.4.zip).

<!--
See the package **README** for full details; including full details of how it can be installed on an AEM instance - in a variety of scenarios.
-->

## Cas d’utilisation pour les environnements de création et de publication {#use-cases-author-publish-environments}

Les cas d’utilisation peuvent dépendre du type d’environnement AEM as a Cloud Service :

* Environnement de publication, utilisé pour :
   * Réaliser des requête de données pour l’application JS (cas d’utilisation standard)

* Environnement de création, utilisé pour :
   * Réaliser des requêtes de données à des fins de gestion de contenu :
      * GraphQL dans AEM as a Cloud Service est actuellement une API en lecture seule.
      * L’API REST peut être utilisée pour les opérations CR(u)D.

## Autorisations {#permission}

Les autorisations sont celles requises pour accéder aux ressources.

## Création de schémas {#schema-generation}

GraphQL est une API dans laquelle les données doivent être clairement structurées et organisées par type.

La spécification GraphQL fournit une série de directives sur la création d’une API robuste pour interroger les données sur une certaine instance. Un client doit pour cela récupérer le [Schéma](#schema-generation), qui contient tous les types nécessaires pour une requête.

Pour les fragments de contenu, les schémas GraphQL (structure et types) sont basés sur **Activé** [Modèles de fragments de contenu](/help/assets/content-fragments/content-fragments-models.md) et leurs types de données.

>[!CAUTION]
>
>Tous les schémas GraphQL (dérivés de modèles de fragments de contenu qui ont été **activés**) sont lisibles par le point de terminaison GraphQL.
>
>Cela signifie que vous devez vous assurer qu’aucune donnée sensible n’est disponible, car elle peut être divulguée de cette façon ; par exemple, cela inclut des informations qui peuvent être présentes sous forme de noms de champ dans la définition de modèle.

Par exemple, si un utilisateur a créé un modèle de fragment de contenu nommé `Article`, AEM génère l’objet `article` de type `ArticleModel`. Les champs de ce type correspondent aux champs et aux types de données définis dans le modèle.

1. Un modèle de fragment de contenu :

   ![Modèle de fragment de contenu à utiliser avec GraphQL](assets/cfm-graphqlapi-01.png "Modèle de fragment de contenu à utiliser avec GraphQL")

1. Le schéma GraphQL correspondant (sortie de la documentation automatique GraphiQL) :
   ![Schéma GraphQL basé sur le modèle de fragment de contenu](assets/cfm-graphqlapi-02.png "Schéma GraphQL basé sur le modèle de fragment de contenu")

   Cela montre que le type généré `ArticleModel` contient plusieurs [champs](#fields).

   * Trois d’entre eux ont été contrôlés par l’utilisateur : `author`, `main` et `referencearticle`.

   * Les autres champs ont été ajoutés automatiquement par AEM et représentent des méthodes utiles pour fournir des informations sur un certain fragment de contenu ; dans cet exemple, `_path`, `_metadata` et `_variations`. Ces [champs d’assistance](#helper-fields) sont précédés d’un `_` pour distinguer ce qui a été défini par l’utilisateur de ce qui a été généré automatiquement.

1. Après qu’un utilisateur a créé un fragment de contenu reposant sur le modèle d’article, il peut être interrogé via GraphQL. Vous trouverez des exemples à la section [Exemples de Requêtes](/help/assets/content-fragments/content-fragments-graphql-samples.md#graphql-sample-queries) (basée sur un [modèle de structure de fragment de contenu à utiliser avec GraphQL](/help/assets/content-fragments/content-fragments-graphql-samples.md#content-fragment-structure-graphql)).

Dans GraphQL pour AEM, le schéma est flexible. Cela signifie qu’il est généré automatiquement à chaque fois qu’un modèle de fragment de contenu est créé, mis à jour ou supprimé. Les caches de schémas de données sont également actualisés lorsque vous mettez à jour un modèle de fragment de contenu.

Le service Sites GraphQL écoute (en arrière-plan) toutes les modifications apportées à un modèle de fragment de contenu. Lorsque des mises à jour sont détectées, seule cette partie du schéma est régénérée. Cette optimisation permet de gagner du temps et d’apporter de la stabilité.

Par exemple, si vous :

1. Installez un package contenant `Content-Fragment-Model-1` et `Content-Fragment-Model-2` :

   1. Les types GraphQL pour `Model-1` et `Model-2` seront générés.

1. Puis modifiez `Content-Fragment-Model-2` :

   1. Seul le type `Model-2` GraphQL sera mis à jour.

   1. Alors que `Model-1` restera le même.

>[!NOTE]
>
>Il est important de le noter si vous souhaitez effectuer des mises à jour en bloc sur les modèles de fragments de contenu via l’API REST, ou autrement.

Le schéma est desservi par le même point d’entrée que les requêtes GraphQL, le client gérant le fait que le schéma est appelé avec l’extension `GQLschema`. Par exemple, l’exécution d’une requête `GET` simple sur `/content/cq:graphql/global/endpoint.GQLschema` entraîne la sortie du schéma avec le type de contenu : `text/x-graphql-schema;charset=iso-8859-1`.

## Champs {#fields}

Le schéma comporte des champs individuels de deux catégories de base :

* Champs que vous générez.

   Une sélection de [types de champs](#field-types) est utilisée pour créer des champs en fonction de la configuration du modèle de fragment de contenu. Les noms des champs proviennent du champ **Nom de la propriété** du **Type de données**.

   * Il faut également tenir compte de la propriété **Rendre comme**, car les utilisateurs peuvent configurer certains types de données, par exemple comme une seule ligne de texte ou avec plusieurs champs.

* GraphQL pour AEM génère également un certain nombre de [champs d’assistance](#helper-fields).

   Ils servent à identifier un fragment de contenu ou à obtenir plus d’informations sur un fragment.

### Types de champs {#field-types}

GraphQL pour AEM prend en charge une liste de types. Tous les types de données de modèles de fragments de contenu pris en charge et les types GraphQL correspondants sont représentés :

| Modèle de fragment de contenu – Type de données | Type GraphQL | sa description ; |
|--- |--- |--- |
| Une seule ligne de texte | Chaîne, [Chaîne] |  Utilisé pour les chaînes simples telles que les noms d’auteurs, les noms d’emplacements, etc. |
| Plusieurs lignes de texte | Chaîne |  Utilisé pour la sortie de texte, tel que le corps d’un article |
| Nombre |  Flottant, [Flottant] | Utilisé pour afficher le nombre à virgule flottante et les nombres réguliers |
| Booléen |  Booléen |  Utilisé pour afficher les cases à cocher → simples instructions vrai/faux |
| Date et heure | Calendrier |  Utilisé pour afficher la date et l’heure au format ISO 8086 |
| Énumération |  Chaîne |  Utilisé pour afficher une option à partir d’une liste d’options définies lors de la création du modèle |
|  Balises |  [Chaîne] |  Utilisé pour afficher une liste de chaînes représentant les balises utilisées dans AEM |
| Référence de contenu |  Chaîne |  Utilisé pour afficher le chemin vers une autre ressource dans AEM |
| Référence du fragment |  *Un type de modèle* |  Utilisé pour référencer un autre fragment de contenu d’un certain type de modèle, défini lors de la création du modèle |

### Champs d’assistance {#helper-fields}

Outre les types de données des champs générés par l’utilisateur, GraphQL pour AEM génère également un certain nombre de champs *d’assistance* afin de faciliter l’identification d’un fragment de contenu ou de fournir des informations supplémentaires sur un fragment de contenu.

#### Chemin {#path}

Le champ de chemin est utilisé comme identificateur dans GraphQL. Il représente le chemin d’accès de la ressource de fragment de contenu dans le référentiel AEM. Nous l’avons choisi comme identificateur d’un fragment de contenu, car il :

* est unique dans AEM ;
* peut facilement être récupéré.

Le code suivant affiche les chemins de tous les fragments de contenu créés à partir du modèle de fragment de contenu `Person`.

```xml
{
  personList {
    items {
      _path
    }
  }
}
```

Pour récupérer un fragment de contenu unique d’un type spécifique, vous devez commencer par déterminer son chemin d’accès. par exemple :

```xml
{
  personByPath(_path: "/content/dam/path/to/fragment/john-doe") {
    item {
      _path
      firstName
      name
    }
  }
}
```

Voir [Exemple de Requête - Un fragment de ville spécifique unique](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-single-specific-city-fragment).

#### Métadonnées {#metadata}

Par le biais de GraphQL, AEM expose également les métadonnées d’un fragment de contenu. Les métadonnées sont les informations qui décrivent un fragment de contenu, comme le titre d’un fragment de contenu, le chemin d’accès à la miniature, la description d’un fragment de contenu, la date de création, etc.

Les métadonnées étant générées par l’éditeur de schémas et n’ayant donc pas de structure spécifique, le type `TypedMetaData` GraphQL a été implémenté pour exposer les métadonnées d’un fragment de contenu. `TypedMetaData` expose les informations regroupées selon les types scalaires suivants :

| Champ |
|--- |
| `stringMetadata:[StringMetadata]!` |
| `stringArrayMetadata:[StringArrayMetadata]!` |
| `intMetadata:[IntMetadata]!` |
| `intArrayMetadata:[IntArrayMetadata]!` |
| `floatMetadata:[FloatMetadata]!` |
| `floatArrayMetadata:[FloatArrayMetadata]!` |
| `booleanMetadata:[BooleanMetadata]!` |
| `booleanArrayMetadata:[booleanArrayMetadata]!`  |
| `calendarMetadata:[CalendarMetadata]!` |
| `calendarArrayMetadata:[CalendarArrayMetadata]!` |

Chaque type scalaire représente soit une paire nom-valeur unique, soit un tableau de paires nom-valeur, où la valeur d’une paire est du type dans lequel elle a été regroupée.

Par exemple, si vous souhaitez récupérer le titre d’un fragment de contenu, nous savons que cette propriété est une propriété Chaîne et recherchons donc toutes les métadonnées Chaîne :

Pour rechercher des métadonnées :

```xml
{
  personByPath(_path: "/content/dam/path/to/fragment/john-doe") {
    item {
      _path
      _metadata {
        stringMetadata {
          name
          value
        }
      }
    }
  }
}
```

Vous pouvez afficher tous les types GraphQL de métadonnées si vous affichez le schéma GraphQL généré. Tous les types de modèle ont le même `TypedMetaData`.

>[!NOTE]
>
>**Différence entre les métadonnées normales et les métadonnées de tableau**
>Gardez à l’esprit que `StringMetadata` et `StringArrayMetadata` se rapportent tous deux à ce qui est stocké dans le référentiel et non à la façon dont vous les récupérez.
>
>Par exemple, en appelant le champ `stringMetadata`, vous recevriez un tableau de toutes les métadonnées stockées dans le référentiel comme `String` et en appelant `stringArrayMetadata`, vous recevriez un tableau de toutes les métadonnées stockées dans le référentiel comme `String[]`.

Voir [Modèle de recherche de métadonnées – Répertorier les métadonnées des prix intitulés GB](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-metadata-awards-gb).

#### Variations {#variations}

Le champ `_variations` a été implémenté pour simplifier la recherche de variations d’un fragment de contenu. Par exemple :

```xml
{
  personByPath(_path: "/content/dam/path/to/fragment/john-doe") {
    item {
      _variations
    }
  }
}
```

Voir [Modèle de requête – Toutes les villes avec une variante nommée](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-cities-named-variation).

<!--
## Security Considerations {#security-considerations}
-->

## Variables GraphQL {#graphql-variables}

GraphQL permet de placer des variables dans la requête. Pour plus d’informations, voir la [documentation GraphQL pour GraphiQL](https://graphql.org/learn/queries/#variables).

Par exemple, pour obtenir tous les fragments de contenu de type `Article` présentant une variation spécifique, vous pouvez spécifier la variable `variation` dans GraphiQL.

![Variables GraphQL](assets/cfm-graphqlapi-03.png "Variables GraphQL")

```xml
### query
query GetArticlesByVariation($variation: String!) {
    articleList(variation: $variation) {
        items {
            _path
            author
        }
    }
}
 
### in query variables
{
    "variation": "uk"
}
```

## Directives GraphQL {#graphql-directives}

Dans GraphQL, il est possible de modifier la requête en fonction de variables, nommées directives GraphQL.

Par exemple, vous pouvez inclure ici le champ `adventurePrice` dans une requête pour tous les `AdventureModels`, en fonction d’une variable `includePrice`.

![Directives GraphQL](assets/cfm-graphqlapi-04.png "Directives GraphQL")

```xml
### query
query GetAdventureByType($includePrice: Boolean!) {
  adventureList {
    items {
      adventureTitle
      adventurePrice @include(if: $includePrice)
    }
  }
}
 
### in query variables
{
    "includePrice": true
}
```

## Filtrage {#filtering}

Vous pouvez également utiliser le filtrage dans vos requêtes GraphQL pour renvoyer des données spécifiques.

Le filtrage utilise une syntaxe basée sur des expressions et des opérateurs logiques.

Par exemple, la requête (de base) suivante filtres toutes les personnes dont le nom est `Jobs` ou `Smith` :

```xml
query {
  personList(filter: {
    name: {
      _logOp: OR
      _expressions: [
        {
          value: "Jobs"
        },
        {
          value: "Smith"
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

Pour d&#39;autres exemples, voir :

* détails des [extensions GraphQL pour AEM](/help/assets/content-fragments/content-fragments-graphql-samples.md#graphql-extensions)

* [Modèles de requêtes utilisant ce modèle de contenu et de structure](/help/assets/content-fragments/content-fragments-graphql-samples.md#graphql-sample-queries-sample-content-fragment-structure)

   * Et l&#39;[exemple de contenu et de structure](/help/assets/content-fragments/content-fragments-graphql-samples.md#content-fragment-structure-graphql) préparé pour être utilisé dans des exemples de requêtes

* [Modèles de requêtes basées sur le projet WKND](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-queries-using-wknd-project)

## Requêtes conservées (cache) {#persisted-queries-caching}

Après avoir préparé une requête avec une requête POST, elle peut être exécutée avec une requête GET qui peut être mise en cache par des caches HTTP ou un réseau CDN.

Cela est nécessaire, car les requêtes POST ne sont généralement pas mises en cache et si vous utilisez GET avec la requête comme paramètre, il existe un risque important que le paramètre devienne trop volumineux pour les services et intermédiaires HTTP.

Vous trouverez ci-dessous les étapes nécessaires à la conservation d’une requête donnée :

>[!NOTE]
>Avant cela, les **Requêtes de persistance GraphQL** doivent être activées pour la configuration appropriée. Voir [Activation de la fonctionnalité de fragment de contenu dans le navigateur de configuration](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser) pour plus d’informations.

1. Préparez la requête avec une commande PUT sur l’URL du nouveau point d’entrée `/graphql/persist.json/<config>/<persisted-label>`.

   Par exemple, créez une requête persistante :

   ```xml
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query" \
       -d \
   '{
     articleList {
       items{
           _path
           author
           main {
               json
           }
       }
     }
   }'
   ```

1. À ce stade, vérifiez la réponse.

   Par exemple, contrôlez le succès :

   ```xml
   {
     "action": "create",
     "configurationName": "wknd",
     "name": "plain-article-query",
     "shortPath": "/wknd/plain-article-query",
     "path": "/conf/wknd/settings/graphql/persistentQueries/plain-article-query"
   }
   ```

1. Vous pouvez ensuite exécuter à nouveau la requête conservée avec une commande GET sur l’URL `/graphql/execute.json/<shortPath>`.

   Par exemple, utilisez la requête persistante :

   ```xml
   $ curl -X GET \
       http://localhost:4502/graphql/execute.json/wknd/plain-article-query
   ```

1. Mettez à jour une requête persistante avec une commande POST vers un chemin de requête existant.

   Par exemple, utilisez la requête persistante :

   ```xml
   $ curl -X POST \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query" \
       -d \
   '{
     articleList {
       items{
           _path
           author
           main {
               json
           }
         referencearticle {
           _path
         }
       }
     }
   }'
   ```

1. Créez une requête ordinaire encapsulée.

   Par exemple :

   ```xml
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-wrapped" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }"}'
   ```

1. Créez une requête ordinaire encapsulée avec le contrôle de cache.

   Par exemple :

   ```xml
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }", "cache-control": { "max-age": 300 }}'
   ```

1. Créez une requête persistante avec des paramètres :

   Par exemple :

   ```xml
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-parameters" \
       -d \
   'query GetAsGraphqlModelTestByPath($apath: String!, $withReference: Boolean = true) {
     articleByPath(_path: $apath) {
       item {
         _path
           author
           main {
           plaintext
           }
           referencearticle @include(if: $withReference) {
           _path
           }
         }
       }
     }'
   ```

1. Exécution d’une requête avec des paramètres.

   Par exemple :

   ```xml
   $ curl -X POST \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters;apath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
   
   $ curl -X GET \
       "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters;apath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
   ```

1. Pour exécuter la requête lors de la publication, l’arborescence persistante associée doit être répliquée.

   * Utilisation d’un POST pour la réplication :

      ```xml
      $curl -X POST   http://localhost:4502/bin/replicate.json \
        -H 'authorization: Basic YWRtaW46YWRtaW4=' \
        -F path=/conf/wknd/settings/graphql/persistentQueries/plain-article-query \
        -F cmd=activate
      ```

   * Utilisation d’un module :
      1. Créez une définition de module.
      1. Incluez la configuration (par exemple, `/conf/wknd/settings/graphql/persistentQueries`).
      1. Créez le module.
      1. Répliquez le module.
   * Utilisation de l’outil de réplication/distribution.
      1. Accédez à l’outil Distribution.
      1. Sélectionnez l’activation de l’arborescence pour la configuration (par exemple, `/conf/wknd/settings/graphql/persistentQueries`).
   * Utilisation d’un workflow (via la configuration du lanceur de workflow) :
      1. Définissez une règle de lancement de workflow pour exécuter un modèle de workflow qui répliquerait la configuration sur différents événements (par exemple, créer, modifier, entre autres).



1. Une fois que la configuration de la requête est publiée, les mêmes principes s’appliquent, en utilisant simplement le point d’entrée de publication.

   >[!NOTE]
   >
   >Pour un accès anonyme, le système suppose que l’ACL permet à « tout le monde » d’avoir accès à la configuration de la requête.
   >
   >Si ce n’est pas le cas, l’exécution sera impossible.

   >[!NOTE]
   >
   >Les points-virgules (;) des URL doivent être codés.
   >
   >Par exemple, comme dans la demande d’exécution d’une requête persistante :
   >
   >
   ```xml
   >curl -X GET \ "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters%3bapath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
   >```

## Requête du point d’entrée GraphQL à partir d’un site Web externe {#query-graphql-endpoint-from-external-website}

>[!NOTE]
>
>Pour un aperçu détaillé de la politique de partage des ressources CORS dans AEM, voir [Description du partage des ressources Cross-Origin (CORS)](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=fr#understand-cross-origin-resource-sharing-(cors)).

Pour autoriser un site Web tiers à consommer la sortie JSON, une politique CORS doit être configurée dans le référentiel Git client. Vous devez pour cela ajouter un fichier de configuration CORS OSGi approprié pour le point d’entrée souhaité. Cette configuration doit spécifier un nom de site Web approuvé (ou regex) pour lequel l’accès doit être accordé.

* Accès au point d’entrée GraphQL :

   * alloworigin : [votre domaine] ou alloworiginregexp : [votre domaine regex]
   * supportedmethods : [POST]
   * allowedpaths : [&quot;/content/graphql/global/endpoint.json&quot;]

* Accès au point d’entrée des requêtes persistantes GraphQL :

   * alloworigin : [votre domaine] ou alloworiginregexp : [votre domaine regex]
   * supportedmethods : [GET]
   * allowedpaths : [&quot;/graphql/execute.json/.*&quot;]

>[!CAUTION]
>
>Il incombe au client de :
>
>* n’accorder l’accès qu’aux domaines approuvés ;
>* s&#39;assurer qu&#39;aucune information sensible n&#39;est exposée
>* n’utilisez pas la syntaxe de caractère générique [*] ; ceci désactive à la fois l&#39;accès authentifié au point de terminaison GraphQL et l&#39;expose également au monde entier.


>[!CAUTION]
>
>Tous les schémas GraphQL [](#schema-generation) (dérivés des modèles de fragments de contenu qui ont été **activés**) sont lisibles par le point de terminaison GraphQL.
>
>Cela signifie que vous devez vous assurer qu’aucune donnée sensible n’est disponible, car elle peut être divulguée de cette façon ; par exemple, cela inclut des informations qui peuvent être présentes sous forme de noms de champ dans la définition de modèle.

## Authentification {#authentication}

Voir [Authentification pour les Requêtes GraphQL d&#39;AEM distantes sur les fragments de contenu](/help/assets/content-fragments/graphql-authentication-content-fragments.md).

<!-- to be addressed later -->

<!--
## Sorting {#sorting}
-->

<!-- to be addressed later -->

<!--
## Paging {#paging}
-->

## FAQ {#faqs}

Questions soulevées :

1. **Q** : « *En quoi l’API GraphQL pour AEM est-elle différente de l’API Query Builder ?* »

   * **R** : « *L’API GraphQL d’AEM offre un contrôle total sur la sortie JSON et est une norme du secteur pour les requêtes de contenu.
AEM prévoit d’investir dans l’API GraphQL d’AEM.* »

## Tutoriel – Prise en main d’AEM découplé et de GraphQL {#tutorial}

Vous cherchez un tutoriel pratique ? Consultez le tutoriel complet [Prise en main d’AEM découplé et de GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html?lang=fr) illustrant comment créer et exposer du contenu à l’aide des API GraphQL d’AEM et consommé par une application externe, dans un scénario CMS découplé.
