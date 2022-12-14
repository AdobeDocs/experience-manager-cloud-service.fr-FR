---
title: API AEM GraphQL à utiliser avec des fragments de contenu
description: Découvrez comment utiliser les fragments de contenu dans Adobe Experience Manager (AEM) as a Cloud Service avec l’API AEM GraphQL pour la diffusion de contenu en mode découplé.
feature: Content Fragments,GraphQL API
exl-id: bdd60e7b-4ab9-4aa5-add9-01c1847f37f6
source-git-commit: 666125abe28ed71e85fdcf4a3b44f26e61c7795f
workflow-type: tm+mt
source-wordcount: '4174'
ht-degree: 58%

---


# API AEM GraphQL à utiliser avec des fragments de contenu {#graphql-api-for-use-with-content-fragments}

Découvrez comment utiliser les fragments de contenu dans Adobe Experience Manager (AEM) as a Cloud Service avec l’API AEM GraphQL pour la diffusion de contenu en mode découplé.

L’API GraphQL d’AEM as a Cloud Service utilisée avec des fragments de contenu repose principalement sur l’API open source standard GraphQL.

L’utilisation de l’API GraphQL dans AEM permet la diffusion efficace de fragments de contenu aux clients JavaScript dans les implémentations CMS découplées :

* en évitant les demandes d’API itératives comme avec REST ;
* en veillant à ce que la diffusion soit limitée aux exigences spécifiques ;
* en permettant de diffuser en bloc exactement ce qui est nécessaire pour le rendu en réponse à une seule requête d’API.

>[!NOTE]
>
>GraphQL est actuellement utilisé dans deux scénarios (distincts) dans Adobe Experience Manager (AEM) as a Cloud Service :
>
>* [AEM Commerce utilise les données d’une plateforme commerciale par le biais de GraphQL](/help/commerce-cloud/integrating/magento.md).
>* Les fragments de contenu d’AEM fonctionnent conjointement avec l’API AEM GraphQL (une implémentation personnalisée, basée sur GraphQL standard), pour fournir du contenu structuré à utiliser dans vos applications.


## L’API GraphQL {#graphql-api}

GraphQL est :

* « *...un langage de requête pour les API et un environnement d’exécution pour répondre à ces requêtes avec vos données existantes. GraphQL fournit une description complète et compréhensible des données de votre API, permet aux clients de demander exactement ce dont ils ont besoin et rien de plus, facilite l’évolution des API au fil du temps et donne accès à de puissants outils de développement.* ».

   Voir [GraphQL.org](https://graphql.org)

* « *...une spécification ouverte pour une couche d’API flexible. Placez GraphQL sur vos back-ends existants pour créer des produits plus rapidement que jamais...* ».

   Voir [Explore GraphQL](https://www.graphql.com).

* *« ... un langage et une spécification de requête de données développés en interne par Facebook en 2012 avant d’être rendus open source en 2015. C’est une alternative aux architectures basées sur REST destinée à accroître la productivité des développeurs et à réduire les quantités de données transférées. GraphQL est utilisé en production par des centaines d’entreprises de toutes tailles... »*

   Voir [GraphQL Foundation](https://foundation.graphql.org/).

<!--
"*Explore GraphQL is maintained by the Apollo team. Our goal is to give developers and technical leaders around the world all of the tools they need to understand and adopt GraphQL.*". 
-->

Pour plus d’informations sur l’API GraphQL, voir les sections suivantes (parmi de nombreuses autres ressources) :

* Sur [graphql.org](https://graphql.org) :

   * [Présentation de GraphQL](https://graphql.org/learn)

   * [La spécification GraphQL](https://spec.graphql.org/)

* Sur [graphql.com](https://graphql.com) :

   * [Guides](https://www.graphql.com/guides/)

   * [Tutoriels](https://www.graphql.com/tutorials/)

   * [Études de cas](https://www.graphql.com/case-studies/)

La mise en œuvre GraphQL pour AEM repose sur la bibliothèque Java GraphQL standard. Voir :

* [graphQL.org – Java](https://graphql.org/code/#java)

* [GraphQL Java sur GitHub](https://github.com/graphql-java)

### Terminologie GraphQL {#graphql-terminology}

GraphQL utilise les éléments suivants :

* **[Requêtes](https://graphql.org/learn/queries/)**

* **[Schémas et types](https://graphql.org/learn/schema/)** :

   * Les schémas sont générés par AEM en fonction des modèles de fragment de contenu.
   * Grâce à vos schémas, GraphQL présente les types et les opérations autorisés pour l’implémentation de GraphQL pour AEM.

* **[Champs](https://graphql.org/learn/queries/#fields)**

* **[Point d’entrée GraphQL](graphql-endpoint.md)**
   * Le chemin d’accès dans AEM qui répond aux requêtes GraphQL et permet d’accéder aux schémas GraphQL.

   * Voir [Activation de votre point d’entrée GraphQL](graphql-endpoint.md) pour plus de détails.

Voir la [Présentation de GraphQL (GraphQL.org)](https://graphql.org/learn/) pour des détails complets, y compris les [Bonnes pratiques](https://graphql.org/learn/best-practices/).

### Types de requêtes GraphQL {#graphql-query-types}

GraphQL permet de réaliser des requêtes pour renvoyer, au choix :

* Une **entrée unique**

* Une **[liste d’entrées](https://graphql.org/learn/schema/#lists-and-non-null)**

AEM fournit des fonctionnalités pour convertir les requêtes (les deux types) en [Requêtes persistantes, qui peuvent être mises en cache](/help/headless/graphql-api/persisted-queries.md) par Dispatcher et le réseau de diffusion de contenu.

### Bonnes pratiques de requête GraphQL (Dispatcher et CDN) {#graphql-query-best-practices}

Le [Requêtes persistantes](/help/headless/graphql-api/persisted-queries.md) sont la méthode recommandée à utiliser sur les instances de publication en tant que :

* Elles sont mises en cache.
* Elles sont gérées de manière centralisée par AEM as a Cloud Service.

>[!NOTE]
>
>En règle générale, il n’y a pas de dispatcher/CDN sur l’auteur. Il n’y a donc pas d’intérêt à utiliser des requêtes persistantes dans cet environnement. à part les tester.

Les requêtes GraphQL utilisant des requêtes de POST ne sont pas recommandées, car elles ne sont pas mises en cache. Par conséquent, sur une instance par défaut, Dispatcher est configuré pour bloquer ces requêtes.

Bien que GraphQL prenne également en charge les requêtes de GET, celles-ci peuvent atteindre des limites (par exemple, la longueur de l’URL) qui peuvent être évitées à l’aide de requêtes persistantes.

>[!NOTE]
>
>Pour autoriser les requêtes directes et/ou POST dans Dispatcher, vous pouvez demander à votre administrateur système de :
>
>* Créez un [Variable d’environnement Cloud Manager](/help/implementing/cloud-manager/environment-variables.md) appelé `ENABLE_GRAPHQL_ENDPOINT`
>* avec la valeur `true`.


>[!NOTE]
>
>Il se peut que la possibilité d’effectuer des requêtes directes devienne obsolète à un moment donné.

### IDE GraphiQL {#graphiql-ide}

Vous pouvez tester et déboguer des requêtes GraphQL à l’aide de l’[IDE GraphiQL](/help/headless/graphql-api/graphiql-ide.md).

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

Les requêtes GraphQL sont exécutées avec l’autorisation de l’utilisateur AEM de la requête sous-jacente. Si l’utilisateur ne dispose pas d’un accès en lecture à certains fragments (stockés en tant que ressources), ils ne feront pas partie du jeu de résultats.

En outre, l’utilisateur doit avoir accès à un point de terminaison GraphQL pour pouvoir exécuter des requêtes GraphQL.

## Création de schémas {#schema-generation}

GraphQL est une API dans laquelle les données doivent être clairement structurées et organisées par type.

La spécification GraphQL fournit une série de directives sur la création d’une API robuste pour interroger les données sur une certaine instance. Un client doit pour cela récupérer le [Schéma](#schema-generation), qui contient tous les types nécessaires pour une requête.

Pour les fragments de contenu, les schémas GraphQL (structure et types) reposent sur des [Modèles de fragments de contenu](/help/sites-cloud/administering/content-fragments/content-fragments-models.md) **activés** et leurs types de données

>[!CAUTION]
>
>Tous les schémas GraphQL (dérivés de modèles de fragments de contenu qui ont été **activés**) sont lisibles par le point d’entrée GraphQL.
>
>En d’autres termes, vous devez vous assurer qu’aucune donnée sensible n’est disponible, car elle peut être divulguée de cette façon ; par exemple, cela concerne des informations qui peuvent être présentes sous forme de noms de champ dans la définition de modèle.

Par exemple, si un utilisateur a créé un modèle de fragment de contenu appelé `Article`, puis AEM génère un type GraphQL `ArticleModel`. Les champs de ce type correspondent aux champs et aux types de données définis dans le modèle. En outre, il crée certains points d’entrée pour les requêtes de ce type, comme `articleByPath` ou `articleList`.

1. Un modèle de fragment de contenu :

   ![Modèle de fragment de contenu à utiliser avec GraphQL](assets/cfm-graphqlapi-01.png "Modèle de fragment de contenu à utiliser avec GraphQL")

1. Le schéma GraphQL correspondant (sortie de la documentation automatique GraphiQL) :
   ![Schéma GraphQL basé sur le modèle de fragment de contenu](assets/cfm-graphqlapi-02.png "Schéma GraphQL basé sur le modèle de fragment de contenu")

   Cela montre que le type généré `ArticleModel` contient plusieurs [champs](#fields).

   * Trois d’entre eux ont été contrôlés par l’utilisateur : `author`, `main` et `referencearticle`.

   * Les autres champs ont été automatiquement ajoutés par AEM et représentent des méthodes utiles pour fournir des informations sur un certain fragment de contenu ; dans cet exemple, (la variable [champ d’assistance](#helper-fields)) `_path`, `_metadata`, `_variations`.

1. Après qu’un utilisateur a créé un fragment de contenu reposant sur le modèle d’article, il peut être interrogé via GraphQL. Vous trouverez des exemples à la section [Exemples de Requêtes](/help/headless/graphql-api/sample-queries.md#graphql-sample-queries) (basée sur un [modèle de structure de fragment de contenu à utiliser avec GraphQL](/help/headless/graphql-api/sample-queries.md#content-fragment-structure-graphql)).

Dans GraphQL pour AEM, le schéma est flexible. Cela signifie qu’il est généré automatiquement à chaque fois qu’un modèle de fragment de contenu est créé, mis à jour ou supprimé. Les caches de schémas de données sont également actualisés lorsque vous mettez à jour un modèle de fragment de contenu.

<!-- move the following to a separate "in depth" page -->

Les caches de schémas de données sont également actualisés lorsque vous mettez à jour un modèle de fragment de contenu.

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

<!-- move through to here to a separate "in depth" page -->

### Génération de schémas – Modèles non publiés {#schema-generation-unpublished-models}

Lorsque des fragments de contenu sont imbriqués, il se peut qu’un modèle de fragment de contenu parent soit publié, mais pas un modèle référencé.

>[!NOTE]
>
>L’interface utilisateur d’AEM empêche cela, mais si la publication est effectuée par programmation ou avec des modules de contenu, elle peut être effectuée.

Dans ce cas, AEM génère un schéma *incomplet* pour le modèle de fragment de contenu parent. Cela signifie que la référence au fragment, qui dépend du modèle non publié, est supprimée du schéma.

## Champs {#fields}

Le schéma comporte des champs individuels de deux catégories de base :

* Champs que vous générez.

   Une sélection de [Types de données](#Data-types) sont utilisés pour créer des champs en fonction de la configuration de votre modèle de fragment de contenu. Les noms des champs proviennent de la variable **Nom de la propriété** du champ **Type de données** .

   * Il y a également la **Render As** , car les utilisateurs peuvent configurer certains types de données. Par exemple, un champ de texte d’une seule ligne peut être configuré pour contenir plusieurs textes d’une seule ligne en choisissant `multifield` dans la liste déroulante.

* GraphQL pour AEM génère également un certain nombre de [champs d’assistance](#helper-fields).

### Types de données {#data-types}

GraphQL pour AEM prend en charge une liste de types. Tous les types de données de modèles de fragments de contenu pris en charge et les types GraphQL correspondants sont représentés :

| Modèle de fragment de contenu – Type de données | Type GraphQL | Description |
|--- |--- |--- |
| Une seule ligne de texte | Chaîne, [Chaîne] |  Utilisé pour les chaînes simples telles que les noms d’auteurs, les noms d’emplacements, etc.. |
| Plusieurs lignes de texte | Chaîne, [Chaîne] |  Utilisé pour la sortie de texte, tel que le corps d’un article |
| Nombre |  Flottant, [Flottant] | Utilisé pour afficher le nombre à virgule flottante et les nombres réguliers |
| Booléen |  Booléen |  Utilisé pour afficher les cases à cocher → simples instructions vrai/faux |
| Date et heure | Calendrier |  Utilisé pour afficher la date et l’heure au format ISO 8601. Selon le type sélectionné, trois versions sont disponibles dans AEM GraphQL : `onlyDate`, `onlyTime`, `dateTime` |
| Énumération |  Chaîne |  Utilisé pour afficher une option à partir d’une liste d’options définies lors de la création du modèle |
|  Balises |  [Chaîne] |  Utilisé pour afficher une liste de chaînes représentant les balises utilisées dans AEM |
| Référence de contenu |  Chaîne, [Chaîne] |  Utilisé pour afficher le chemin vers une autre ressource dans AEM |
| Référence du fragment |  *Un type de modèle* |  Utilisé pour référencer un autre fragment de contenu d’un certain type de modèle, défini lors de la création du modèle |

### Champs d’assistance {#helper-fields}

Outre les types de données des champs générés par l’utilisateur, GraphQL pour AEM génère également un certain nombre de champs *d’assistance* afin de faciliter l’identification d’un fragment de contenu ou de fournir des informations supplémentaires sur un fragment de contenu.

Ces [champs d’assistance](#helper-fields) sont précédés d’un `_` pour distinguer ce qui a été défini par l’utilisateur de ce qui a été généré automatiquement.

#### Chemin {#path}

Le champ de chemin d’accès est utilisé comme identifiant dans AEM GraphQL. Il représente le chemin d’accès de la ressource de fragment de contenu dans le référentiel AEM. Nous l’avons choisi comme identifiant d’un fragment de contenu, car il :

* est unique dans AEM ;
* peut facilement être récupéré.

Le code suivant affiche les chemins d’accès de tous les fragments de contenu créés en fonction du modèle de fragment de contenu. `Author`, comme indiqué dans le tutoriel WKND.

```graphql
{
  authorList {
    items {
      _path
    }
  }
}
```

Pour récupérer un fragment de contenu unique d’un type spécifique, vous devez commencer par déterminer son chemin d’accès. Par exemple :

```graphql
{
  authorByPath(_path: "/content/dam/wknd-shared/en/contributors/sofia-sj-berg") {
    item {
      _path
      firstName
      lastName
    }
  }
}
```

Voir [Exemple de requête – Un fragment de ville unique et spécifique](/help/headless/graphql-api/sample-queries.md#sample-single-specific-city-fragment).

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

```graphql
{
  authorByPath(_path: "/content/dam/wknd-shared/en/contributors/sofia-sj-berg") {
    item {
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

Voir [Modèle de recherche de métadonnées – Répertorier les métadonnées des prix intitulés GB](/help/headless/graphql-api/sample-queries.md#sample-metadata-awards-gb).

#### Variations {#variations}

Le champ `_variations` a été implémenté pour simplifier la recherche de variations d’un fragment de contenu. Par exemple :

```graphql
{
  authorByPath(_path: "/content/dam/wknd-shared/en/contributors/ian-provo") {
    item {
      _variations
    }
  }
}
```

>[!NOTE]
>
>Notez que la variable `_variations` ne contient pas de champ `master` variation, car techniquement, les données d’origine (référencées comme *Principal* dans l’interface utilisateur) n’est pas considérée comme une variation explicite.

Voir [Modèle de requête – Toutes les villes avec une variante nommée](/help/headless/graphql-api/sample-queries.md#sample-cities-named-variation).

>[!NOTE]
>
>Si la variation donnée n’existe pas pour un fragment de contenu, les données d’origine (également appelées variation principale) sont renvoyées comme valeur par défaut (de secours).

<!--
## Security Considerations {#security-considerations}
-->

## Variables GraphQL {#graphql-variables}

GraphQL permet de placer des variables dans la requête. Pour plus d’informations, voir la [documentation GraphQL des Variables](https://graphql.org/learn/queries/#variables).

Par exemple, pour obtenir tous les fragments de contenu de type `Author` dans une variation spécifique (le cas échéant), vous pouvez spécifier l’argument . `variation` dans GraphiQL.

![Variables GraphQL](assets/cfm-graphqlapi-03.png "Variables GraphQL")

**Requête**:

```graphql
query($variation: String!) {
  authorList(variation: $variation) {
    items {
      _variation
      lastName
      firstName
    }
  }
}
```

**Variables de requête**:

```json
{
  "variation": "another"
}
```

Cette requête renverra la liste complète des auteurs. Les auteurs sans `another` la variation revient aux données d’origine (`_variation` rapport `master` dans ce cas).

Si vous souhaitez limiter la liste aux auteurs qui fournissent la variation spécifiée (et ignorer les auteurs qui reviennent aux données d’origine), vous devez appliquer une [filter](#filtering):

```graphql
query($variation: String!) {
  authorList(variation: $variation, filter: {
    _variation: {
      _expressions: {
        value: $variation
      }
    }
  }) {
    items {
      _variation
      lastName
      firstName
    }
  }
}
```

## Directives GraphQL {#graphql-directives}

Dans GraphQL, il est possible de modifier la requête en fonction de variables, nommées directives GraphQL.

Par exemple, vous pouvez inclure ici le champ `adventurePrice` dans une requête pour tous les `AdventureModels`, en fonction d’une variable `includePrice`.

![Directives GraphQL](assets/cfm-graphqlapi-04.png "Directives GraphQL")

**Requête**:

```graphql
query GetAdventureByType($includePrice: Boolean!) {
  adventureList {
    items {
      title
      price @include(if: $includePrice)
    }
  }
}
```

**Variables de requête**:

```json
{
    "includePrice": true
}
```

## Filtrage {#filtering}

Vous pouvez également utiliser le filtrage dans vos requêtes GraphQL pour renvoyer des données spécifiques.

Le filtrage utilise une syntaxe basée sur des expressions et des opérateurs logiques.

La partie la plus atomique est une expression unique qui peut être appliquée au contenu d&#39;un certain champ. Il compare le contenu du champ avec une valeur constante donnée.

Par exemple, l’expression

```graphql
{
  value: "some text"
  _op: EQUALS
}
```

compare le contenu du champ à la valeur `some text` et réussit si le contenu est égal à la valeur . Sinon, l’expression échouera.

Les

Les opérateurs suivants peuvent être utilisés pour comparer les champs à une certaine valeur :

| Opérateur | Type(s) | L’expression réussit si ... |
|--- |--- |--- |
| `EQUALS` | `String`, `ID`, `Boolean` | ...la valeur est exactement la même que le contenu du champ. |
| `EQUALS_NOT` | `String`, `ID` | ... la valeur est *not* identique au contenu du champ |
| `CONTAINS` | `String` | ... le contenu du champ contient la valeur (`{ value: "mas", _op: CONTAINS }` correspond à `Christmas`, `Xmas`, `master`, ...) |
| `CONTAINS_NOT` | `String` | ... le contenu du champ est *not* contient la valeur |
| `STARTS_WITH` | `ID` | ... l’identifiant commence par une certaine valeur (`{ value: "/content/dam/", _op: STARTS_WITH` correspond à `/content/dam/path/to/fragment`, mais pas `/namespace/content/dam/something` |
| `EQUAL` | `Int`, `Float` | ...la valeur est exactement la même que le contenu du champ. |
| `UNEQUAL` | `Int`, `Float` | ... la valeur est *not* identique au contenu du champ |
| `GREATER` | `Int`, `Float` | ...le contenu du champ est supérieur à la valeur |
| `GREATER_EQUAL` | `Int`, `Float` | ...le contenu du champ est supérieur ou égal à la valeur |
| `LOWER` | `Int`, `Float` | ...le contenu du champ est inférieur à la valeur |
| `LOWER_EQUAL` | `Int`, `Float` | ...le contenu du champ est inférieur ou égal à la valeur |
| `AT` | `Calendar`, `Date`, `Time` | ...le contenu du champ est exactement identique à la valeur (paramètre de fuseau horaire inclus) |
| `NOT_AT` | `Calendar`, `Date`, `Time` | ... le contenu du champ est *not* identique à la valeur |
| `BEFORE` | `Calendar`, `Date`, `Time` | ...le moment indiqué par la valeur est antérieur au moment indiqué par le contenu du champ. |
| `AT_OR_BEFORE` | `Calendar`, `Date`, `Time` | ...le moment indiqué par la valeur est avant ou au même moment indiqué par le contenu du champ. |
| `AFTER` | `Calendar`, `Date`, `Time` | ... le moment indiqué par la valeur est le moment où le contenu du champ indique le point dans le temps. |
| `AT_OR_AFTER` | `Calendar`, `Date`, `Time` | ...le moment indiqué par la valeur est postérieur ou en même temps identifié par le contenu du champ. |

Certains types permettent également de spécifier des options supplémentaires qui modifient la manière dont une expression est évaluée :

| Option | Type(s) | Description |
|--- |--- |--- |
| `_ignoreCase` | `String` | Ignore la casse d’une chaîne, par exemple une valeur de `time` correspond à `TIME`, `time`, `tImE`, ... |
| `_sensitiveness` | `Float` | Permet une certaine marge pour `float` valeurs à considérer comme identiques (pour contourner les limitations techniques en raison de la représentation interne des `float` les valeurs; à éviter, car cette option peut avoir un impact négatif sur les performances. |

Les expressions peuvent être combinées à un ensemble à l’aide d’un opérateur logique (`_logOp`) :

* `OR` - l’ensemble d’expressions réussira si au moins une expression réussit
* `AND` : l’ensemble d’expressions réussit si toutes les expressions réussissent (par défaut).

Chaque champ peut être filtré par son propre ensemble d’expressions. Les ensembles d’expressions de tous les champs mentionnés dans l’argument de filtre seront finalement combinés par son propre opérateur logique.

Une définition de filtre (transmise comme `filter` à une requête) contient :

* Une sous-définition pour chaque champ (le champ est accessible via son nom, par exemple il y a une `lastName` dans le filtre pour la variable `lastName` champ dans le Type de données (champ)
* Chaque sous-définition contient le paramètre `_expressions` , fournissant le jeu d’expressions et la variable `_logOp` champ définissant l’opérateur logique avec lequel les expressions doivent être combinées
* Chaque expression est définie par la valeur (`value` ) et l’opérateur (`_operator` ) le contenu d’un champ doit être comparé à

Notez que vous pouvez omettre `_logOp` si vous souhaitez combiner des éléments avec `AND` et `_operator` si vous souhaitez vérifier l’égalité, car il s’agit des valeurs par défaut.

L’exemple suivant illustre une requête complète qui filtre toutes les personnes ayant une `lastName` de `Provo` ou contenant `sjö`, indépendamment de l’affaire :

```graphql
{
  authorList(filter: {
    lastname: {
      _logOp: OR
      _expressions: [
        {
          value: "sjö",
          _operator: CONTAINS,
          _ignoreCase: true
        },
        {
          value: "Provo"
        }
      ]
    }
  }) {
    items {
      lastName
      firstName
    }
  }
}
```

Bien que vous puissiez également filtrer les champs imbriqués, il n’est pas recommandé, car cela peut entraîner des problèmes de performances.

Pour accéder à d’autres exemples, voir :

* détails des [extensions GraphQL pour AEM](#graphql-extensions)

* [Modèles de requêtes utilisant ce modèle de contenu et de structure](/help/headless/graphql-api/sample-queries.md#graphql-sample-queries-sample-content-fragment-structure)

   * Et [Modèle de contenu et de structure](/help/headless/graphql-api/sample-queries.md#content-fragment-structure-graphql) préparé pour une utilisation dans des modèles de requêtes

* [Modèles de requêtes basées sur le projet WKND](/help/headless/graphql-api/sample-queries.md#sample-queries-using-wknd-project)

## Tri {#sorting}

Cette fonctionnalité vous permet de trier les résultats de la requête en fonction d’un champ spécifié.

Les critères de tri :

* est une liste de valeurs séparées par des virgules représentant le chemin du champ.
   * le premier champ de la liste définit l&#39;ordre de tri Principal, le second champ est utilisé si deux valeurs du critère de tri Principal sont égales, le troisième si les deux premiers critères sont égaux, etc.
   * notation pointillée, c’est-à-dire field1.subfield.subfield, etc..
* avec une direction de commande facultative
   * ASC (ascendant) ou DESC (descendant); comme l’attribut ASC par défaut est appliqué
   * la direction peut être spécifiée par champ ; cela signifie que vous pouvez trier un champ par ordre croissant, un autre par ordre décroissant (name, firstName DESC).

Par exemple :

```graphql
query {
  authorList(sort: "lastName, firstName") {
    items {
      firstName
      lastName
    }
  }
}
```

Et aussi :

```graphql
{
  authorList(sort: "lastName DESC, firstName DESC") {
    items {
        lastName
        firstName
    }
  }
}
```

<!-- to be included? -->

Vous pouvez également trier un champ dans un fragment imbriqué au format de `nestedFragmentname.fieldname`.

>[!NOTE]
>
>Cela peut avoir un impact négatif sur les performances.

Par exemple :

```graphql
query {
  articleList(sort: "authorFragment.lastName")  {
    items {
      title
      authorFragment {
        firstName
        lastName
        birthDay
      }
      slug
    }
  }
}
```

## Pagination {#paging}

Cette fonctionnalité vous permet d’effectuer une pagination sur les types de requête qui renvoient une liste. Deux méthodes sont fournies :

* `offset` et `limit` dans `List` query
* `first` et `after` dans `Paginated` query

### Requête de liste - décalage et limite {#list-offset-limit}

Dans un `...List`requête que vous pouvez utiliser `offset` et `limit` pour renvoyer un sous-ensemble spécifique de résultats :

* `offset`: Spécifie le premier jeu de données à renvoyer.
* `limit`: Spécifie le nombre maximal de jeux de données à renvoyer.

Par exemple, pour générer la page de résultats contenant jusqu’à cinq articles, à partir du cinquième article de la *complete* liste de résultats :

```graphql
query {
   articleList(offset: 5, limit: 5) {
    items {
      authorFragment {
        lastName
        firstName
      }
    }
  }
}
```

<!-- When available link to BP and replace "JCR query level" with a more neutral term. -->

<!-- When available link to BP and replace "JCR query result set" with a more neutral term. -->

>[!NOTE]
>
>* La pagination nécessite un ordre de tri stable pour fonctionner correctement sur plusieurs requêtes demandant différentes pages du même jeu de résultats. Par défaut, il utilise le chemin d’accès au référentiel de chaque élément du jeu de résultats pour s’assurer que l’ordre est toujours le même. Si un ordre de tri différent est utilisé et si ce tri ne peut pas être effectué au niveau de la requête JCR, il y aura un impact négatif sur les performances, car l’ensemble de résultats doit être chargé en mémoire avant que les pages puissent être déterminées.
>
>* Plus le décalage est élevé, plus il faudra de temps pour ignorer les éléments du jeu de résultats de requête JCR complet. Une autre solution pour les jeux de résultats volumineux consiste à utiliser la requête Paginée avec `first` et `after` .


### Requête paginée - Première et après {#paginated-first-after}

Le `...Paginated` le type de requête réutilise la plupart des `...List` fonctions de type requête (filtrage, tri), mais au lieu d’utiliser `offset`/`limit` arguments, il utilise la variable `first`/`after` arguments tels que définis par [Spécification des connexions au curseur GraphQL](https://relay.dev/graphql/connections.htm). Vous trouverez une introduction moins formelle dans la [Présentation de GraphQL](https://graphql.org/learn/pagination/#pagination-and-edges).

* `first`: Le `n` les premiers éléments à renvoyer.
La valeur par défaut est `50`.
La valeur maximale est `100`.
* `after`: Le curseur qui détermine le début de la page demandée ; notez que l’élément représenté par le curseur n’est pas inclus dans le jeu de résultats ; le curseur d’un élément est déterminé par `cursor` du champ `edges` structure.

Par exemple, générez la page de résultats contenant jusqu’à cinq aventures, en commençant par l’élément de curseur donné dans la variable *complete* liste de résultats :

```graphql
query {
    adventurePaginated(first: 5, after: "ODg1MmMyMmEtZTAzMy00MTNjLThiMzMtZGQyMzY5ZTNjN2M1") {
        edges {
          cursor
          node {
            title
          }
        }
        pageInfo {
          endCursor
          hasNextPage
        }
    }
}
```

<!-- When available link to BP -->
<!-- Due to internal technical constraints, performance will degrade if sorting and filtering is applied on nested fields. Therefore it is recommended to use filter/sort fields stored at root level. For more information, see the [Best Practices document](link). -->

>[!NOTE]
>
>* Par défaut, la pagination utilise l’UUID du noeud de référentiel représentant le fragment pour assurer que l’ordre des résultats est toujours le même. When `sort` est utilisé, l’UUID est implicitement utilisé pour assurer un tri unique ; même pour deux éléments avec des clés de tri identiques.
>
>* En raison de contraintes techniques internes, les performances se dégradent si le tri et le filtrage sont appliqués aux champs imbriqués. Il est donc recommandé d’utiliser des champs de filtrage/tri stockés au niveau racine. Il s’agit également de la méthode recommandée si vous souhaitez interroger des jeux de résultats paginés volumineux.


## GraphQL pour AEM – Résumé des extensions {#graphql-extensions}

Le fonctionnement de base des requêtes avec GraphQL pour AEM est conforme à la spécification GraphQL standard. Pour les requêtes GraphQL avec AEM, il existe quelques extensions :

* Si vous prévoyez une liste de résultats :
   * Ajoutez `List` au nom du modèle ; par exemple, `cityList`
   * Voir [Exemple de requête – Toutes les informations sur toutes les villes](/help/headless/graphql-api/sample-queries.md#sample-all-information-all-cities)

   Vous pouvez ensuite :

   * [Tri des résultats](#sorting)

      * `ASC` : croissant
      * `DESC` : décroissant
   * Renvoi d’une page de résultats à l’aide de l’une des méthodes suivantes :

      * [Requête Liste avec décalage et limite](#list-offset-limit)
      * [Une requête paginée avec les première et après](#paginated-first-after)
   * Voir [Exemple de requête – Toutes les informations sur toutes les villes](/help/headless/graphql-api/sample-queries.md#sample-all-information-all-cities)



* Si vous avez besoin d’un seul résultat :
   * Utilisez le nom du modèle ; p. ex. city.

* Si vous prévoyez une liste de résultats :
   * Ajoutez `List` au nom du modèle ; par exemple, `cityList`
   * Voir [Exemple de requête – Toutes les informations sur toutes les villes](/help/headless/graphql-api/sample-queries.md#sample-all-information-all-cities)

* Si vous souhaitez utiliser un OU logique :
   * Utilisez ` _logOp: OR`
   * Voir [Exemple de requête – Toutes les personnes qui portent le nom « Jobs » ou « Smith »](/help/headless/graphql-api/sample-queries.md#sample-all-persons-jobs-smith)

* L’opérateur logique ET existe également, mais est (souvent) implicite

* Vous pouvez appliquer des requêtes aux noms de champ qui correspondent aux champs du modèle de fragment de contenu.
   * Voir [Exemple de requête – Détails complets relatifs au PDG et aux employés d’une entreprise](/help/headless/graphql-api/sample-queries.md#sample-full-details-company-ceos-employees)

* Outre les champs de votre modèle, il existe certains champs générés par le système (précédés d’un trait de soulignement) :

   * Pour le contenu :

      * `_locale` : pour afficher la langue ; basé sur Language Manager
         * Voir [Exemple de requête pour plusieurs fragments de contenu d’un paramètre régional donné](/help/headless/graphql-api/sample-queries.md#sample-wknd-multiple-fragments-given-locale)
      * `_metadata` : pour afficher les métadonnées de votre fragment
         * Voir [Modèle de recherche de métadonnées – Répertorier les métadonnées des prix intitulés GB](/help/headless/graphql-api/sample-queries.md#sample-metadata-awards-gb)
      * `_model` : autoriser l’interrogation d’un modèle de fragment de contenu (chemin et titre)
         * Voir [Exemple de requête pour un modèle de fragment de contenu à partir d’un modèle](/help/headless/graphql-api/sample-queries.md#sample-wknd-content-fragment-model-from-model)
      * `_path` : chemin d’accès au fragment de contenu dans le référentiel.
         * Voir [Exemple de requête – Un fragment de ville unique et spécifique](/help/headless/graphql-api/sample-queries.md#sample-single-specific-city-fragment)
      * `_reference` : pour afficher les références ; y compris les références intégrées dans l’éditeur de texte enrichi
         * Voir [Exemple de requête pour plusieurs fragments de contenu avec des références préalablement récupérées](/help/headless/graphql-api/sample-queries.md#sample-wknd-multiple-fragments-prefetched-references)
      * `_variation` : pour afficher des variantes spécifiques dans votre fragment de contenu

         >[!NOTE]
         >
         >Si la variation donnée n’existe pas pour un fragment de contenu, la variation principale est renvoyée comme valeur (de secours) par défaut.

         * Voir [Exemple de requête – Toutes les villes avec une variante nommée](#sample-cities-named-variation)
   * Et les opérations :

      * `_operator` : pour appliquer des opérateurs spécifiques ; `EQUALS`, `EQUALS_NOT`, `GREATER_EQUAL`, `LOWER`, `CONTAINS`, `STARTS_WITH`
         * Voir [Exemple de requête – Toutes les personnes qui ne portent pas le nom « Jobs »](/help/headless/graphql-api/sample-queries.md#sample-all-persons-not-jobs)
         * Voir [Exemple de requête – Toutes les aventures où `_path` commence par un préfixe spécifique](/help/headless/graphql-api/sample-queries.md#sample-wknd-all-adventures-cycling-path-filter)
      * `_apply` : pour appliquer des conditions spécifiques ; par exemple `AT_LEAST_ONCE`
         * Voir [Exemple de requête : effectuer un filtrage sur un tableau avec un élément qui doit se produire au moins une fois](/help/headless/graphql-api/sample-queries.md#sample-array-item-occur-at-least-once)
      * `_ignoreCase` : pour ignorer la casse lors de l’application de la requête
         * Voir [Exemple de requête : toutes les villes dont le nom contient SAN, indépendamment de la casse](/help/headless/graphql-api/sample-queries.md#sample-all-cities-san-ignore-case)









* Les types d’union GraphQL sont pris en charge :

   * Utilisez `... on`
      * Voir [Exemple de requête pour un fragment de contenu d’un modèle spécifique avec une référence de contenu](/help/headless/graphql-api/sample-queries.md#sample-wknd-fragment-specific-model-content-reference)

* Secours lors de l’interrogation de fragments imbriqués :

   * Si une variation donnée n’existe pas dans un fragment imbriqué, la variation **Principal** est renvoyée.

## Requête du point d’entrée GraphQL à partir d’un site web externe {#query-graphql-endpoint-from-external-website}

Pour accéder au point d’entrée GraphQL à partir d’un site web externe, vous devez configurer les éléments suivants :

* [Filtre CORS](/help/headless/deployment/cross-origin-resource-sharing.md)
* [Filtre Référent](/help/headless/deployment/referrer-filter.md)

## Authentification {#authentication}

Voir [Authentification pour les requêtes distantes AEM GraphQL sur les fragments de contenu](/help/headless/security/authentication.md).

## FAQ {#faqs}

Questions soulevées :

1. **Q** : « *En quoi l’API GraphQL pour AEM est-elle différente de l’API Query Builder ?* »

   * **R** : « *L’API AEM GraphQL offre un contrôle total sur la sortie JSON et est une norme du secteur pour les requêtes de contenu.
AEM prévoit d’investir dans l’API AEM GraphQL.* »

## Tutoriel – Prise en main d’AEM découplé et de GraphQL {#tutorial}

Vous cherchez un tutoriel pratique ? Consultez le tutoriel complet [Prise en main d’AEM découplé et de GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html?lang=fr) illustrant comment créer et exposer du contenu à l’aide des API GraphQL d’AEM et consommé par une application externe, dans un scénario CMS découplé.
