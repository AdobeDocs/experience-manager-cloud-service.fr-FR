---
title: Apprendre à utiliser GraphQL avec AEM – Exemple de contenu et de requêtes
description: Découvrez comment utiliser GraphQL avec AEM pour diffuser du contenu en mode découplé en explorant des exemples de contenu et de requêtes.
feature: Content Fragments,GraphQL API
exl-id: b60fcf97-4736-4606-8b41-4051b8b0c8a7
source-git-commit: 6be7cc7678162c355c39bc3000716fdaf421884d
workflow-type: tm+mt
source-wordcount: '1430'
ht-degree: 98%

---

# Apprendre à utiliser GraphQL avec AEM – Exemple de contenu et de requêtes {#learn-graphql-with-aem-sample-content-queries}

Découvrez comment utiliser GraphQL avec AEM pour diffuser du contenu en mode découplé en explorant des exemples de contenu et de requêtes.

>[!NOTE]
>
>Il est préférable de lire cette page à la lumière des sections suivantes :
>
>* [Fragments de contenu](/help/sites-cloud/administering/content-fragments/content-fragments.md)
>* [Modèles de fragment de contenu](/help/sites-cloud/administering/content-fragments/content-fragments-models.md)
>* [API GraphQL d’AEM à utiliser avec des fragments de contenu](/help/headless/graphql-api/content-fragments.md)


Pour prendre en main les requêtes GraphQL et leur fonctionnement avec les fragments de contenu AEM, il peut être utile de consulter quelques exemples pratiques.

Pour obtenir de l’aide à ce sujet, voir les éléments suivants :

* Un [exemple de structure de fragment de contenu](#content-fragment-structure-graphql)

* Un certain nombre d’[exemples de requêtes GraphQL](#graphql-sample-queries), basés sur l’exemple de structure de fragments de contenu (modèles de fragments de contenu et fragments de contenu associés).


## GraphQL - Exemples de requêtes utilisant la structure de fragment de contenu type {#graphql-sample-queries-sample-content-fragment-structure}

Consultez ces exemples de requêtes pour obtenir un aperçu de la création de requêtes, ainsi que des exemples de résultats.

>[!NOTE]
>
>Selon votre instance, vous pouvez accéder directement à l’[interface GraphiQL incluse avec l’API GraphQL d’AEM](/help/headless/graphql-api/graphiql-ide.md) pour soumettre et tester des requêtes.
>
>Vous pouvez accéder à l’éditeur de requêtes à partir de :
>
>* **Outils** -> **Général** -> **Éditeur de requêtes GraphQL**
>* directement; par exemple, `http://localhost:4502/aem/graphiql.html`


>[!NOTE]
>
>Les exemples de requêtes sont basés sur l’[exemple de structure de fragment de contenu à utiliser avec GraphQL](#content-fragment-structure-graphql)

### Exemple de requête - Tous les schémas et types de données disponibles {#sample-all-schemes-datatypes}

Tous les `types` seront renvoyés pour tous les schémas disponibles.

**Exemple de requête**

```xml
{
  __schema {
    types {
      name
      description
    }
  }
}
```

**Exemple de résultat**

```xml
{
  "data": {
    "__schema": {
      "types": [
        {
          "name": "AdventureModel",
          "description": null
        },
        {
          "name": "AdventureModelArrayFilter",
          "description": null
        },
        {
          "name": "AdventureModelFilter",
          "description": null
        },
        {
          "name": "AdventureModelResult",
          "description": null
        },
        {
          "name": "AdventureModelResults",
          "description": null
        },
        {
          "name": "AllFragmentModels",
          "description": null
        },
        {
          "name": "ArchiveRef",
          "description": null
        },
        {
          "name": "ArrayMode",
          "description": null
        },
        {
          "name": "ArticleModel",
          "description": null
        },

...more results...

        {
          "name": "__EnumValue",
          "description": null
        },
        {
          "name": "__Field",
          "description": null
        },
        {
          "name": "__InputValue",
          "description": null
        },
        {
          "name": "__Schema",
          "description": "A GraphQL Introspection defines the capabilities of a GraphQL server. It exposes all available types and directives on the server, the entry points for query, mutation, and subscription operations."
        },
        {
          "name": "__Type",
          "description": null
        },
        {
          "name": "__TypeKind",
          "description": "An enum describing what kind of type a given __Type is"
        }
      ]
    }
  }
}
```

### Exemple de requête - Toutes les informations sur toutes les villes {#sample-all-information-all-cities}

Pour récupérer toutes les informations sur toutes les villes, vous pouvez utiliser la requête de base :
**Exemple de requête**

```xml
{
  cityList {
    items
  }
}
```

Une fois l’exécution effectuée, le système développe automatiquement la requête pour inclure tous les champs :

```xml
{
  cityList {
    items {
      _path
      name
      country
      population
    }
  }
}
```

**Exemples de résultats**

```xml
{
  "data": {
    "cityList": {
      "items": [
        {
          "_path": "/content/dam/sample-content-fragments/cities/basel",
          "name": "Basel",
          "country": "Switzerland",
          "population": 172258
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/berlin",
          "name": "Berlin",
          "country": "Germany",
          "population": 3669491
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/bucharest",
          "name": "Bucharest",
          "country": "Romania",
          "population": 1821000
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/san-francisco",
          "name": "San Francisco",
          "country": "USA",
          "population": 883306
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/san-jose",
          "name": "San Jose",
          "country": "USA",
          "population": 1026350
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/stuttgart",
          "name": "Stuttgart",
          "country": "Germany",
          "population": 634830
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/zurich",
          "name": "Zurich",
          "country": "Switzerland",
          "population": 415367
        }
      ]
    }
  }
}
```

### Exemple de requête - Noms de toutes les villes {#sample-names-all-cities}

Il s’agit d’une requête simple pour renvoyer l’élément `name`de toutes les entrées dans le schéma`city`.

**Exemple de requête**

```xml
query {
  cityList {
    items {
      name
    }
  }
}
```

**Exemples de résultats**

```xml
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "Basel"
        },
        {
          "name": "Berlin"
        },
        {
          "name": "Bucharest"
        },
        {
          "name": "San Francisco"
        },
        {
          "name": "San Jose"
        },
        {
          "name": "Stuttgart"
        },
        {
          "name": "Zurich"
        }
      ]
    }
  }
}
```

### Exemple de requête - Un fragment de ville unique et spécifique {#sample-single-specific-city-fragment}

Il s’agit d’une requête qui renvoie les détails d’une entrée de fragment unique vers un emplacement spécifique dans le référentiel.

**Exemple de requête**

```xml
{
  cityByPath (_path: "/content/dam/sample-content-fragments/cities/berlin") {
    item {
      _path
      name
      country
      population
     categories
    }
  }
}
```

**Exemples de résultats**

```xml
{
  "data": {
    "cityByPath": {
      "item": {
        "_path": "/content/dam/sample-content-fragments/cities/berlin",
        "name": "Berlin",
        "country": "Germany",
        "population": 3669491,
        "categories": [
          "city:capital",
          "city:emea"
        ]
      }
    }
  }
}
```

### Exemple de requête - Toutes les villes avec une variante nommée {#sample-cities-named-variation}

Si vous créez une nouvelle variante, appelée « Centre de Berlin » (`berlin_centre`), pour Berlin en tant que `city`, vous pouvez utiliser une requête afin de renvoyer des détails sur la variante.

**Exemple de requête**

```xml
{
  cityList (variation: "berlin_center") {
    items {
      _path
      name
      country
      population
      categories
    }
  }
}
```

**Exemples de résultats**

```xml
{
  "data": {
    "cityList": {
      "items": [
        {
          "_path": "/content/dam/sample-content-fragments/cities/berlin",
          "name": "Berlin",
          "country": "Germany",
          "population": 3669491,
          "categories": [
            "city:capital",
            "city:emea"
          ]
        }
      ]
    }
  }
}
```

### Exemple de requête - Détails complets relatifs au PDG et aux employés d’une entreprise {#sample-full-details-company-ceos-employees}

Grâce à la structure des fragments imbriqués, cette requête renvoie tous les détails relatifs au PDG d’une entreprise et à tous ses employés.

**Exemple de requête**

```xml
query {
  companyList {
    items {
      name
      ceo {
        _path
        name
        firstName
        awards {
        id
          title
        }
      }
      employees {
       name
        firstName
       awards {
         id
          title
        }
      }
    }
  }
}
```

**Exemples de résultats**

```xml
{
  "data": {
    "companyList": {
      "items": [
        {
          "name": "Apple Inc.",
          "ceo": {
            "_path": "/content/dam/sample-content-fragments/persons/steve-jobs",
            "name": "Jobs",
            "firstName": "Steve",
            "awards": []
          },
          "employees": [
            {
              "name": "Marsh",
              "firstName": "Duke",
              "awards": []
            },
            {
              "name": "Caulfield",
              "firstName": "Max",
              "awards": [
                {
                  "id": "GB",
                  "title": "Gameblitz"
                }
              ]
            }
          ]
        },
        {
          "name": "Little Pony, Inc.",
          "ceo": {
            "_path": "/content/dam/sample-content-fragments/persons/adam-smith",
            "name": "Smith",
            "firstName": "Adam",
            "awards": []
          },
          "employees": [
            {
              "name": "Croft",
              "firstName": "Lara",
              "awards": [
                {
                  "id": "GS",
                  "title": "Gamestar"
                }
              ]
            },
            {
              "name": "Slade",
              "firstName": "Cutter",
              "awards": [
                {
                  "id": "GB",
                  "title": "Gameblitz"
                },
                {
                  "id": "GS",
                  "title": "Gamestar"
                }
              ]
            }
          ]
        },
        {
          "name": "NextStep Inc.",
          "ceo": {
            "_path": "/content/dam/sample-content-fragments/persons/steve-jobs",
            "name": "Jobs",
            "firstName": "Steve",
            "awards": []
          },
          "employees": [
            {
              "name": "Smith",
              "firstName": "Joe",
              "awards": []
            },
            {
              "name": "Lincoln",
              "firstName": "Abraham",
              "awards": []
            }
          ]
        }
      ]
    }
  }
}
```

### Exemple de Requête - Toutes les personnes qui portent le nom « Jobs » ou « Smith » {#sample-all-persons-jobs-smith}

Elle filtre toutes les `persons` qui portent le nom `Jobs` ou `Smith`.

**Exemple de requête**

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

**Exemples de résultats**

```xml
{
  "data": {
    "personList": {
      "items": [
        {
          "name": "Smith",
          "firstName": "Adam"
        },
        {
          "name": "Smith",
          "firstName": "Joe"
        },
        {
          "name": "Jobs",
          "firstName": "Steve"
        }
      ]
    }
  }
}
```

### Exemple de requête - Toutes les personnes qui ne portent pas le nom « Jobs » {#sample-all-persons-not-jobs}

Elle filtre toutes les `persons` qui portent le nom `Jobs` ou `Smith`.

**Exemple de requête**

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

**Exemples de résultats**

```xml
{
  "data": {
    "personList": {
      "items": [
        {
          "name": "Lincoln",
          "firstName": "Abraham"
        },
        {
          "name": "Smith",
          "firstName": "Adam"
        },
        {
          "name": "Slade",
          "firstName": "Cutter"
        },
        {
          "name": "Marsh",
          "firstName": "Duke"
        },
        {
          "name": "Smith",
          "firstName": "Joe"
        },
        {
          "name": "Croft",
          "firstName": "Lara"
        },
        {
          "name": "Caulfield",
          "firstName": "Max"
        }
      ]
    }
  }
}
```

### Exemple de requête - Toutes les aventures dont `_path` commence par un préfixe spécifique {#sample-wknd-all-adventures-cycling-path-filter}

Toutes les `adventures` où `_path` commence par un préfixe spécifique (`/content/dam/wknd/en/adventures/cycling`).

**Exemple de requête**

```xml
query {
  adventureList(
    filter: {
      _path: {
        _expressions: [
        {
          value: "/content/dam/wknd/en/adventures/cycling"
         _operator: STARTS_WITH
        }]
       }
    })
    {
    items {
      _path
    }
  }
}
```

**Exemples de résultats**

```xml
{
  "data": {
    "adventureList": {
      "items": [
        {
          "_path": "/content/dam/wknd/en/adventures/cycling-southern-utah/cycling-southern-utah"
        },
        {
          "_path": "/content/dam/wknd/en/adventures/cycling-tuscany/cycling-tuscany"
        }
      ]
    }
  }
}
```

### Exemple de requête - Toutes les villes situées en Allemagne ou en Suisse et dont la population se situe entre 400 000 et 999 999 {#sample-all-cities-d-ch-population}

Ici, le filtrage concerne une combinaison de champs. Un opérateur `AND` (implicite) est utilisé pour sélectionner la plage `population`, tandis qu’un opérateur `OR` (explicite) est utilisé pour sélectionner les villes requises.

**Exemple de requête**

```xml
query {
  cityList(filter: {
    population: {
      _expressions: [
        {
          value: 400000
          _operator: GREATER_EQUAL
        }, {
          value: 1000000
          _operator: LOWER
        }
      ]
    },
    country: {
      _logOp: OR
      _expressions: [
        {
          value: "Germany"
        }, {
          value: "Switzerland"
        }
      ]
    }
  }) {
    items {
      name
      population
      country
    }
  }
}
```

**Exemples de résultats**

```xml
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "Stuttgart",
          "population": 634830,
          "country": "Germany"
        },
        {
          "name": "Zurich",
          "population": 415367,
          "country": "Switzerland"
        }
      ]
    }
  }
}
```

### Exemple de requête - Toutes les villes dont le nom contient SAN, indépendamment de la casse {#sample-all-cities-san-ignore-case}

Cette requête interroge toutes les villes dont le nom contient `SAN`, indépendamment de la casse.

**Exemple de requête**

```xml
query {
  cityList(filter: {
    name: {
      _expressions: [
        {
          value: "SAN"
          _operator: CONTAINS
          _ignoreCase: true
        }
      ]
    }
  }) {
    items {
      name
      population
      country
    }
  }
}
```

**Exemples de résultats**

```xml
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "San Francisco",
          "population": 883306,
          "country": "USA"
        },
        {
          "name": "San Jose",
          "population": 1026350,
          "country": "USA"
        }
      ]
    }
  }
}
```

### Exemple de requête - Filtrage sur un tableau avec un élément qui doit apparaître au moins une fois {#sample-array-item-occur-at-least-once}

Cette requête effectue un filtrage sur un tableau avec un élément (`city:na`) qui doit se produire au moins une fois.

**Exemple de requête**

```xml
query {
  cityList(filter: {
    categories: {
      _expressions: [
        {
          value: "city:na"
          _apply: AT_LEAST_ONCE
        }
      ]
    }
  }) {
    items {
      name
      population
      country
      categories
    }
  }
}
```

**Exemples de résultats**

```xml
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "San Francisco",
          "population": 883306,
          "country": "USA",
          "categories": [
            "city:beach",
            "city:na"
          ]
        },
        {
          "name": "San Jose",
          "population": 1026350,
          "country": "USA",
          "categories": [
            "city:na"
          ]
        }
      ]
    }
  }
}
```

### Exemple de requête - Filtrage sur une valeur de tableau exacte {#sample-array-exact-value}

Cette requête effectue un filtrage sur une valeur de tableau exacte.

**Exemple de requête**

```xml
query {
  cityList(filter: {
    categories: {
      _expressions: [
        {
          values: [
            "city:beach",
            "city:na"
          ]
        }
      ]
    }
  }) {
    items {
      name
      population
      country
      categories
    }
  }
}
```

**Exemples de résultats**

```xml
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "San Francisco",
          "population": 883306,
          "country": "USA",
          "categories": [
            "city:beach",
            "city:na"
          ]
        }
      ]
    }
  }
}
```

### Exemple de requête pour les fragments de contenu imbriqués - Toutes les entreprises dont au moins un employé porte le nom « Smith » {#sample-companies-employee-smith}

Cette requête illustre le filtrage pour toute `person` portant le `name` « Smith », qui renvoie des informations provenant de deux fragments imbriqués – `company` et `employee`.

**Exemple de requête**

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

**Exemples de résultats**

```xml
{
  "data": {
    "companyList": {
      "items": [
        {
          "name": "NextStep Inc.",
          "ceo": {
            "name": "Jobs",
            "firstName": "Steve"
          },
          "employees": [
            {
              "name": "Smith",
              "firstName": "Joe"
            },
            {
              "name": "Lincoln",
              "firstName": "Abraham"
            }
          ]
        }
      ]
    }
  }
}
```

### Exemple de requête pour les fragments de contenu imbriqués - Toutes les entreprises dont tous les employés ont remporté le prix « Gamestar » {#sample-all-companies-employee-gamestar-award}

Cette requête illustre le filtrage de trois fragments imbriqués : `company`, `employee` et `award`.

**Exemple de requête**

```xml
query {
  companyList(filter: {
    employees: {
      _apply: ALL
      _match: {
        awards: {
          _match: {
            id: {
              _expressions: [
                {
                  value: "GS"
                  _operator:EQUALS
                }
              ]
            }
          }
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
        awards {
          id
          title
        }
      }
    }
  }
}
```

**Exemples de résultats**

```xml
{
  "data": {
    "companyList": {
      "items": [
        {
          "name": "Little Pony, Inc.",
          "ceo": {
            "name": "Smith",
            "firstName": "Adam"
          },
          "employees": [
            {
              "name": "Croft",
              "firstName": "Lara",
              "awards": [
                {
                  "id": "GS",
                  "title": "Gamestar"
                }
              ]
            },
            {
              "name": "Slade",
              "firstName": "Cutter",
              "awards": [
                {
                  "id": "GB",
                  "title": "Gameblitz"
                },
                {
                  "id": "GS",
                  "title": "Gamestar"
                }
              ]
            }
          ]
        }
      ]
    }
  }
}
```

### Exemple de requête pour les métadonnées - Liste des métadonnées des prix intitulés GB {#sample-metadata-awards-gb}

Cette requête illustre le filtrage de trois fragments imbriqués : `company`, `employee` et `award`.

**Exemple de requête**

```xml
query {
  awardList(filter: {
      id: {
        _expressions: [
          {
            value:"GB"
          }
        ]
    }
  }) {
    items {
      _metadata {
        stringMetadata {
          name,
          value
        }
      }
      id
      title
    }
  }
}
```

**Exemples de résultats**

```xml
{
  "data": {
    "awardList": {
      "items": [
        {
          "_metadata": {
            "stringMetadata": [
              {
                "name": "title",
                "value": "Gameblitz Award"
              },
              {
                "name": "description",
                "value": ""
              }
            ]
          },
          "id": "GB",
          "title": "Gameblitz"
        }
      ]
    }
  }
}
```

## Exemples de requêtes utilisant le projet WKND {#sample-queries-using-wknd-project}

Ces exemples de requêtes sont basés sur le projet WKND. Il s’agit des éléments suivants :

* Modèles de fragments de contenu disponibles sous :
   `http://<hostname>:<port>/libs/dam/cfm/models/console/content/models.html/conf/wknd`

* Fragments de contenu (et autres contenus) disponibles sous :
   `http://<hostname>:<port>/assets.html/content/dam/wknd/en`

>[!NOTE]
>
>Les résultats pouvant être volumineux, ils ne sont pas reproduits ici.

### Exemple de requête pour tous les fragments de contenu d’un modèle donné avec les propriétés spécifiées {#sample-wknd-all-model-properties}

Cet exemple de requête interroge :

* à la recherche de tous les fragments de contenu de type `article` ;
* avec les propriétés `path` et `author`.

**Exemple de requête**

```xml
{
  articleList {
    items {
      _path
      author
    }
  }
}
```

### Exemple de requête de métadonnées {#sample-wknd-metadata}

Cette requête interroge :

* à la recherche de tous les fragments de contenu de type `adventure` ;
* metadata

**Exemple de requête**

```xml
{
  adventureList {
    items {
      _path,
      _metadata {
        stringMetadata {
          name,
          value
        }
        stringArrayMetadata {
          name,
          value
        }
        intMetadata {
          name,
          value
        }
        intArrayMetadata {
          name,
          value
        }
        floatMetadata {
          name,
          value
        }
        floatArrayMetadata {
          name,
          value
        }
        booleanMetadata {
          name,
          value
        }
        booleanArrayMetadata {
          name,
          value
        }
        calendarMetadata {
          name,
          value
        }
        calendarArrayMetadata {
          name,
          value
        }
      }
    }
  }
}
```

### Exemple de requête pour un fragment de contenu unique d’un modèle donné {#sample-wknd-single-content-fragment-of-given-model}

Cet exemple de requête interroge :

* à la recherche d’un fragment de contenu unique de type `article` avec un chemin spécifique ;
   * parmi cela, tous les formats de contenu :
      * HTML
      * Texte (Markdown)
      * Texte brut
      * JSON

**Exemple de requête**

```xml
{
  articleByPath (_path: "/content/dam/wknd/en/magazine/alaska-adventure/alaskan-adventures") {
    item {
        _path
        author
        main {
          html
          markdown
          plaintext
          json
        }
    }
  }
}
```

### Exemple de requête pour un modèle de fragment de contenu à partir d’un modèle {#sample-wknd-content-fragment-model-from-model}

Cet exemple de requête interroge :

* à la recherche d’un seul fragment de contenu ;
   * les détails du modèle de fragment de contenu sous-jacent.

**Exemple de requête**

```xml
{
  adventureByPath(_path: "/content/dam/wknd/en/adventures/riverside-camping-australia/riverside-camping-australia") {
    item {
      _path
      adventureTitle
      _model {
        _path
        title
      }
    }
  }
}
```

### Exemple de requête pour un fragment de contenu imbriqué - Type de modèle unique{#sample-wknd-nested-fragment-single-model}

Cette requête interroge :

* à la recherche d’un fragment de contenu unique de type `article` avec un chemin spécifique ;
   * parmi cela, le chemin d’accès et l’auteur du fragment référencé (imbriqué).

>[!NOTE]
>
>Le champ `referencearticle` a le type de données `fragment-reference`.

**Exemple de requête**

```xml
{
  articleByPath (_path: "/content/dam/wknd/en/magazine/skitouring/skitouring") {
    item {
        _path
        author
        referencearticle {
          _path
          author
      }
    }
  }
}
```

### Exemple de requête pour un fragment de contenu imbriqué - Type de modèle multiple{#sample-wknd-nested-fragment-multiple-model}

Cette requête interroge :

* à la recherche de différents fragments de contenu de type `bookmark` ;
   * avec des références de fragments à d’autres fragments de types de modèles spécifiques `article` et `adventure`.

>[!NOTE]
>
>Le champ `fragments` présente le type de données `fragment-reference`, avec les modèles `Article`, `Adventure` sélectionnés.

```xml
{
  bookmarkList {
    items {
        fragments {
          ... on ArticleModel {
            _path
            author
          }
          ... on AdventureModel {
            _path
            adventureTitle
          }
        }
     }
  }
}
```

### Exemple de requête pour un fragment de contenu d’un modèle spécifique avec des références de contenu{#sample-wknd-fragment-specific-model-content-reference}

Cette requête possède deux versions :

1. Pour renvoyer toutes les références au contenu.
1. Pour renvoyer les références de contenu spécifiques de type `attachments`

Ces requêtes interrogent :

* à la recherche de différents fragments de contenu de type `bookmark` ;
   * avec des références de contenu à d’autres fragments.

#### Exemple de requête pour plusieurs fragments de contenu avec des références prérécupérées {#sample-wknd-multiple-fragments-prefetched-references}

La requête suivante renvoie toutes les références de contenu en utilisant `_references` :

```xml
{
  bookmarkList {
     _references {
         ... on ImageRef {
          _path
          type
          height
        }
        ... on MultimediaRef {
          _path
          type
          size
        }
        ... on DocumentRef {
          _path
          type
          author
        }
        ... on ArchiveRef {
          _path
          type
          format
        }
    }
    items {
        _path
    }
  }
}
```

#### Exemple de requête pour plusieurs fragments de contenu avec pièces jointes {#sample-wknd-multiple-fragments-attachments}

La requête suivante renvoie tous les `attachments` – un champ spécifique (sous-groupe) de type `content-reference` :

>[!NOTE]
>
>Le champ `attachments` présente le type de données `content-reference`, avec différents formulaires sélectionnés.

```xml
{
  bookmarkList {
    items {
      attachments {
        ... on PageRef {
          _path
          type
        }
        ... on ImageRef {
          _path
          width
        }
        ... on MultimediaRef {
          _path
          size
        }
        ... on DocumentRef {
          _path
          author
        }
        ... on ArchiveRef {
          _path
          format
        }
      }
    }
  }
}
```

### Exemple de requête pour un fragment de contenu unique avec référence en ligne RTE {#sample-wknd-single-fragment-rte-inline-reference}

Cette requête interroge :

* à la recherche d’un fragment de contenu unique de type `bookmark` avec un chemin spécifique ;
   * à l’intérieur de cela, les références intégrées RTE.

>[!NOTE]
>
>Les références en ligne RTE sont alimentées dans `_references`.

**Exemple de requête**

```xml
{
  bookmarkByPath(_path: "/content/dam/wknd/en/bookmarks/skitouring") {
    item {
      _path
      description {
        json
      }
    }
    _references {
      ... on ArticleModel {
        _path
      }
      ... on AdventureModel {
        _path
      }
      ... on ImageRef {
        _path
      }
      ... on MultimediaRef {
        _path
      }
      ... on DocumentRef {
        _path
      }
      ... on ArchiveRef {
        _path
      }
    }
  }
}
```

### Exemple de requête pour une variation de fragment de contenu unique d’un modèle donné {#sample-wknd-single-fragment-given-model}

Cette requête interroge :

* à la recherche d’un fragment de contenu unique de type `article` avec un chemin spécifique ;
   * à l’intérieur de cela, les données sont liées à la variation : `variation1`.

**Exemple de requête**

```xml
{
  articleByPath (_path: "/content/dam/wknd/en/magazine/alaska-adventure/alaskan-adventures", variation: "variation1") {
    item {
      _path
      author
      main {
        html
        markdown
        plaintext
        json
      }
    }
  }
}
```

### Exemple de requête pour une variante nommée de plusieurs fragments de contenu d’un modèle donné {#sample-wknd-variation-multiple-fragment-given-model}

Cette requête interroge :

* à la recherche de fragments de contenu de type `article` avec une variation spécifique : `variation1`

**Exemple de requête**

```xml
{
  articleList (variation: "variation1") {
    items {
      _path
      author
      main {
        html
        markdown
        plaintext
        json
      }
    }
  }
}
```

### Exemple de requête pour plusieurs fragments de contenu d’un paramètre régional donné {#sample-wknd-multiple-fragments-given-locale}

Cette requête interroge :

* à la recherche de fragments de contenu de type `article` dans le paramètre régional `fr`

**Exemple de requête**

```xml
{ 
  articleList (_locale: "fr") {
    items {
      _path
      author
      main {
        html
        markdown
        plaintext
        json
      }
    }
  }
}
```

## Exemple de structure de fragment de contenu (utilisée avec GraphQL) {#content-fragment-structure-graphql}

Les exemples de requêtes sont basés sur la structure suivante, qui utilise :

* Un ou plusieurs [exemples de modèles de fragments de contenu](#sample-content-fragment-models-schemas) constituent la base des schémas GraphQL

* [Exemples de fragments de contenu](#sample-content-fragments) basés sur les modèles ci-dessus

### Exemples de modèles de fragments de contenu (schémas) {#sample-content-fragment-models-schemas}

Pour les exemples de requêtes, nous utiliserons les modèles de contenu suivants et leurs relations mutuelles (références ->) :

* [Entreprise](#model-company)
-> [Personne](#model-person)
-> [Distinction](#model-award)

* [Ville](#model-city)

#### Entreprise {#model-company}

Les champs de base définissant l’entreprise sont les suivants :

| Nom du champ | Type de données | Référence |
|--- |--- |--- |
| Nom de l’entreprise | Une seule ligne de texte |  |
| PDG | Référence du fragment (unique) | [Personne](#model-person) |
| Employés | Référence du fragment (champ multiple) | [Personne](#model-person) |

#### Personne {#model-person}

Champs définissant une personne, qui peut également être un employé :

| Nom du champ | Type de données | Référence |
|--- |--- |--- |
| Nom | Une seule ligne de texte |  |
| Prénom | Une seule ligne de texte |  |
| Distinctions | Référence du fragment (champ multiple) | [Distinction](#model-award) |

#### Distinction {#model-award}

Les champs définissant une distinction sont les suivants :

| Nom du champ | Type de données | Référence |
|--- |--- |--- |
| Raccourci/ID | Une seule ligne de texte |  |
| Titre | Une seule ligne de texte |  |

#### Ville {#model-city}

Les champs permettant de définir une ville sont les suivants :

| Nom du champ | Type de données | Référence |
|--- |--- |--- |
| Nom | Une seule ligne de texte |  |
| Pays | Une seule ligne de texte |  |
| Population | Nombre |  |
| Catégories | Balises |  |

### Exemples de fragments de contenu {#sample-content-fragments}

Les fragments suivants sont utilisés pour le modèle approprié.

#### Entreprise {#fragment-company}

| Nom de l’entreprise | PDG | Employés |
|--- |--- |--- |
| Apple | Steve Jobs | Duke Marsh<br>Max Caulfield |
|  Little Pony Inc. | Adam Smith | Lara Croft<br>Cutter Slade |
| NextStep Inc. | Steve Jobs | Joe Smith<br>Abe Lincoln |

#### Personne {#fragment-person}

| Nom | Prénom | Distinctions |
|--- |--- |--- |
| Lincoln |  Abe |  |
| Smith | Adam |   |
| Slade |  Cutter |  Gameblitz<br>Gamestar |
| Marsh |  Duke |   |   |
|  Smith |  Joe |   |
| Croft |  Lara | Gamestar |
| Caulfield |  Max |  Gameblitz |
|  Jobs |  Steve |   |

#### Distinction {#fragment-award}

| Raccourci/ID | Titre |
|--- |--- |
| GB | Gameblitz |
|  GS | Gamestar |
|  OSC | Oscar |

#### Ville {#fragment-city}

| Nom | Pays | Population | Catégories |
|--- |--- |--- |--- |
| Bâle | Suisse | 172258 | city:emea |
| Berlin | Allemagne | 3669491 | city:capital<br>city:emea |
| Bucarest | Roumanie | 1821000 |  city:capital<br>city:emea |
| San Francisco |  États-Unis |  883306 |  city:beach<br>city:na |
| San Jose |  États-Unis |  102635 |  city:na |
| Stuttgart |  Allemagne |  634830 |  city:emea |
|  Zurich |  Suisse |  415367 |  ville:capital<br>city:emea |
