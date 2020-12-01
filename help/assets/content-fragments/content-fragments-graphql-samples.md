---
title: Apprendre à utiliser GraphQL avec AEM - Exemple de contenu et de Requêtes
description: Apprendre à utiliser GraphQL avec AEM - Exemple de contenu et de Requêtes.
translation-type: tm+mt
source-git-commit: 46e179faa7875c4b3e9da30356d2b82d4b25b130
workflow-type: tm+mt
source-wordcount: '1283'
ht-degree: 6%

---


# Apprendre à utiliser GraphQL avec AEM - Exemple de contenu et de Requêtes {#learn-graphql-with-aem-sample-content-queries}

>[!CAUTION]
>
>L’AEM API GraphQL, pour Content Fragment Diffusion, sera disponible début 2021.
>
>La documentation correspondante est déjà disponible à des fins de prévisualisation.

Pour commencer à utiliser les requêtes GraphQL et comment elles fonctionnent avec AEM Content Fragments, vous pouvez consulter quelques exemples pratiques.

Pour obtenir de l’aide sur ce point, voir :

* Un [exemple de structure de fragment de contenu](#content-fragment-structure-graphql)

* Et certains [exemples de requêtes GraphQL](#graphql-sample-queries), basés sur l’exemple de structure de fragments de contenu (modèles de fragments de contenu et fragments de contenu associés).

## GraphQL pour AEM - Certaines extensions {#graphql-some-extensions}

Le fonctionnement de base des requêtes avec GraphQL pour AEM adhère à la spécification GraphQL standard. Pour les requêtes GraphQL avec AEM il existe quelques extensions :

* Si vous avez besoin d’un seul résultat :
   * utiliser le nom du modèle ; eg ville

* Si vous prévoyez une liste de résultats :
   * ajouter &quot;Liste&quot; au nom du modèle ; par exemple, `cityList`

* Si vous souhaitez utiliser un OU logique :
   * utiliser &quot;_logOp : OR&quot;

* L&#39;opérateur logique ET existe également, mais est (souvent) implicite

* Vous pouvez requête sur les noms de champ qui correspondent aux champs du modèle de fragment de contenu.

* Outre les champs de votre modèle, il existe certains champs générés par le système (précédés d’un trait de soulignement) :

   * Pour le contenu :

      * `_locale` : révéler la langue ; basé sur Language Manager

      * `_metadata` : pour afficher les métadonnées de votre fragment

      * `_path` : le chemin d’accès à votre gestion de contenu dans le référentiel.

      * `_references` : révéler les références ; y compris les références intégrées dans l’éditeur de texte enrichi

      * `_variations` : pour afficher des variations spécifiques dans votre fragment de contenu
   * Et les opérations :

      * `_operator` : appliquer des opérateurs spécifiques ;  `EQUALS`,  `EQUALS_NOT`,  `GREATER_EQUAL`,  `LOWER`,  `CONTAINS`,

      * `_apply` : d&#39;appliquer des conditions spécifiques ; par exemple,   `AT_LEAST_ONCE`

      * `_ignoreCase` : pour ignorer la casse lors de l’interrogation


* Les types d’union GraphQL sont pris en charge :

   * use `...on`


## Exemple de structure de fragment de contenu à utiliser avec GraphQL {#content-fragment-structure-graphql}

Pour un exemple simple, nous avons besoin de :

* Un ou plusieurs [modèles de fragments de contenu ](#sample-content-fragment-models-schemas) constituent la base des schémas GraphQL

* [Exemples de ](#sample-content-fragments) fragments de contenu basés sur les modèles ci-dessus

### Exemples de modèles de fragments de contenu (Schémas) {#sample-content-fragment-models-schemas}

Pour les exemples de requêtes, nous utiliserons les modèles de contenu suivants et leurs interrelations (références ->) :

* [Société](#model-company)
->  [Personne](#model-person)
    ->  [Prix](#model-award)

* [Ville](#model-city)

#### Entreprise {#model-company}

Les champs de base définissant la société sont les suivants :

| Nom du champ | Type de données | Référence  |
|--- |--- |--- |
| Nom de la société | Une seule ligne de texte |  |
| Directeur | Référence du fragment (unique) | [Personne](#model-person) |
| Employés | Référence du fragment (champ multiple) | [Personne](#model-person) |

#### Personne {#model-person}

Champs définissant une personne, qui peut également être un employé :

| Nom du champ | Type de données | Référence  |
|--- |--- |--- |
| Nom | Une seule ligne de texte |  |
| Prénom | Une seule ligne de texte |  |
| Prix | Référence du fragment (champ multiple) | [Prix](#model-award) |

#### Attribution {#model-award}

Les champs définissant une récompense sont les suivants :

| Nom du champ | Type de données | Référence  |
|--- |--- |--- |
| Raccourci/ID | Une seule ligne de texte |  |
| Title (Titre) | Une seule ligne de texte |  |

#### Ville {#model-city}

Les champs permettant de définir une ville sont les suivants :

| Nom du champ | Type de données | Référence  |
|--- |--- |--- |
| Nom | Une seule ligne de texte |  |
| Pays | Une seule ligne de texte |  |
| Population | Nombre |  |
| Catégories | Balises |  |

### Exemples de fragments de contenu {#sample-content-fragments}

Les fragments suivants sont utilisés pour le modèle approprié.

#### Entreprise {#fragment-company}

| Nom de la société | Directeur | Employés |
|--- |--- |--- |
| Apple | Steve Jobs | Duke Marsh<br>Max Caulfield |
|  Little Pony Inc. | Adam Smith | Lara Croft<br>Étalure de découpe |
| NextStep Inc. | Steve Jobs | Joe Smith<br>Abe Lincoln |

#### Personne {#fragment-person}

| Nom | Prénom | Prix |
|--- |--- |--- |
| Lincoln |  Abe |  |
| Smith | Adam |   |
| Étalon |  Cutter |  Gameblitz<br>Gamestar |
| Marsh |  Duke |   |   |
|  Smith |  Joe |   |
| Croisement |  Lara | Gamestar |
| Caulfield |  Max |  Gameblitz |
|  Tâches |  Steve |   |

#### Attribution {#fragment-award}

| Raccourci/ID | Title (Titre) |
|--- |--- |
|  Go | Gameblitz |
|  GS | Gamestar |
|  OSC | Oscar |

#### Ville {#fragment-city}

| Nom | Pays | Population | Catégories |
|--- |--- |--- |--- |
| Basel | Suisse | 172258 | ville:emea |
| Berlin | Allemagne | 3669491 | ville:capital<br>ville:emea |
| Bucarest | Roumanie | 1821000 |  ville:capital<br>ville:emea |
| San Francisco |  USA |  883306 |  ville:plage<br>ville:na |
| San Jose |  USA |  102635 |  ville:na |
| Stuttgart |  Allemagne |  634830 |  ville:emea |
|  Zurich |  Suisse |  415367 |  ville:capital<br>ville:emea |

## GraphQL - Exemples de Requêtes utilisant la structure de fragment de contenu d’exemple {#graphql-sample-queries-sample-content-fragment-structure}

Consultez les exemples de requêtes pour obtenir des illustrations de requêtes de création, ainsi que des exemples de résultats.

>[!NOTE]
>
>Selon votre instance, vous pouvez accéder directement à l&#39;interface [Graph *i* QL incluse avec l&#39;API GraphQL AEM](/help/assets/content-fragments/graphql-api-content-fragments.md#graphiql-interface) pour envoyer et tester des requêtes.
>
>Par exemple : `http://localhost:4502/content/graphiql.html`

### Exemple de Requête - Tous les Schémas et types de données disponibles {#sample-all-schemes-datatypes}

Tous les types seront renvoyés pour tous les schémas disponibles.

**Exemple de Requête**

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

### Exemple de Requête - Détails complets du PDG et des employés d&#39;une Société {#sample-full-details-company-ceos-employees}

À l’aide de la structure des fragments imbriqués, cette requête renvoie tous les détails du PDG d’une société et de tous ses employés.

**Exemple de Requête**

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

### Exemple de Requête - Toutes les informations sur toutes les villes {#sample-all-information-all-cities}

Pour récupérer toutes les informations sur toutes les villes, vous pouvez utiliser la requête de base :
**Exemple de Requête**

```xml
{
  cityList {
    items
  }
}
```

Une fois exécuté, le système développe automatiquement la requête pour inclure tous les champs :

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

### Exemple de Requête - Noms de toutes les villes {#sample-names-all-cities}

Il s&#39;agit d&#39;une requête simple pour renvoyer l&#39;élément `name`de toutes les entrées dans le `city`schéma.

**Exemple de Requête**

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

### Exemple de Requête - Un fragment de ville unique {#sample-single-city-fragment}

Il s’agit d’une requête de renvoi des détails d’une entrée de fragment unique à un emplacement spécifique dans le référentiel.

**Exemple de Requête**

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

### Exemple de Requête - Toutes les villes avec une variante nommée {#sample-cities-named-variation}

Si vous créez une nouvelle variation, appelée &quot;Centre de Berlin&quot; (`berlin_centre`), pour le Berlin `city`, vous pouvez utiliser une requête pour renvoyer des détails sur la variation.

**Exemple de Requête**

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

### Exemple de Requête - Toutes les personnes qui portent le nom &quot;Tâches&quot; ou &quot;Smith&quot; {#sample-all-persons-jobs-smith}

Ceci filtrera tous les `persons` pour ceux qui portent le nom `Jobs`ou `Smith`.

**Exemple de Requête**

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

### Exemple de Requête - Toutes les personnes qui n&#39;ont pas de nom &quot;Tâches&quot; {#sample-all-persons-not-jobs}

Ceci filtrera tous les `persons` pour ceux qui portent le nom `Jobs`ou `Smith`.

**Exemple de Requête**

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

### Échantillon de Requête - Toutes les villes situées en Allemagne ou en Suisse et dont la population se situe entre 400000 et 999999 {#sample-all-cities-d-ch-population}

Ici, une combinaison de champs est filtrée. Un `AND` (implicite) est utilisé pour sélectionner la plage `population`tandis qu&#39;un `OR` (explicite) est utilisé pour sélectionner les villes requises.

**Exemple de Requête**

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

### Exemple de Requête : toutes les villes dont le nom contient un SAN, indépendamment de la casse {#sample-all-cities-san-ignore-case}

Cette requête interroge toutes les villes dont le nom contient `SAN`, indépendamment de la casse.

**Exemple de Requête**

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

### Exemple de Requête : filtrer sur un tableau avec un élément qui doit se produire au moins une fois {#sample-array-item-occur-at-least-once}

Cette requête filtres sur un tableau avec un élément (`city:na`) qui doit se produire au moins une fois.

**Exemple de Requête**

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

### Exemple de Requête : filtrer sur une valeur de tableau exacte {#sample-array-exact-value}

Cette requête filtres sur une valeur de tableau exacte.

**Exemple de Requête**

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

### Exemple de Requête pour les fragments de contenu imbriqué - Toutes les sociétés qui ont au moins un employé portant le nom &quot;Smith&quot; {#sample-companies-employee-smith}

Cette requête illustre le filtrage pour tout `person` de `name` &quot;Smith&quot;, renvoyant des informations provenant de deux fragments imbriqués - `company` et `employee`.

**Exemple de Requête**

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

### Exemple de Requête pour les fragments de contenu imbriqué - Toutes les sociétés où tous les employés ont gagné le prix &quot;Gamestar&quot; {#sample-all-companies-employee-gamestar-award}

Cette requête illustre le filtrage sur trois fragments imbriqués : `company`, `employee` et `award`.

**Exemple de Requête**

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

### Exemple de Requête de métadonnées - Liste des métadonnées pour les prix intitulées GB {#sample-metadata-awards-gb}

Cette requête illustre le filtrage sur trois fragments imbriqués : `company`, `employee` et `award`.

**Exemple de Requête**

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

## Exemples de Requêtes utilisant le projet WKND {#sample-queries-using-wknd-project}

Ces exemples de requêtes sont basés sur le projet WKND.

>[!NOTE]
>
>Comme les résultats peuvent être complets, ils ne sont pas reproduits ici.

### Exemple de Requête pour tous les fragments de contenu d’un modèle donné avec les propriétés spécifiées {#sample-wknd-all-model-properties}

Cet exemple de requête interroge :

* pour tous les fragments de contenu de type `article`
* avec les propriétés `path`et `author`.

**Exemple de Requête**

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

### Exemple de Requête de métadonnées {#sample-wknd-metadata}

Cette requête interroge :

* pour tous les fragments de contenu de type `adventure`
* metadata

**Exemple de Requête**

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

### Exemple de Requête pour un fragment de contenu unique d&#39;un modèle donné {#sample-wknd-single-content-fragment-of-given-model}

Cet exemple de requête interroge :

* pour un fragment de contenu unique d’un modèle donné
* pour tous les formats de contenu :
   * HTML
   * Texte (Markdown)
   * Texte brut
   * JSON

**Exemple de Requête**

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

### Exemple de Requête pour un fragment de contenu imbriqué - Type de modèle unique{#sample-wknd-nested-fragment-single-model}

**Exemple de Requête**

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

### Exemple de Requête pour un fragment de contenu imbriqué - Type de modèle multiple{#sample-wknd-nested-fragment-multiple-model}

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

### Exemple de Requête pour un fragment de contenu d&#39;un modèle spécifique avec une référence de contenu{#sample-wknd-fragment-specific-model-content-reference}

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

### Exemple de Requête pour plusieurs fragments de contenu avec des références prérécupérées {#sample-wknd-multiple-fragments-prefetched-references}

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
  }
}
```

### Exemple de Requête pour une variation de fragment de contenu unique d&#39;un modèle donné {#sample-wknd-single-fragment-given-model}

**Exemple de Requête**

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

### Exemple de Requête pour plusieurs fragments de contenu d’un paramètre régional donné {#sample-wknd-multiple-fragments-given-locale}

**Exemple de Requête**

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

### Exemple de Requête pour un fragment de contenu unique avec référence en ligne RTE {#sample-wknd-single-fragment-rte-inline-reference}

**Exemple de Requête**

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

### Exemple de Requête pour une Variation nommée de plusieurs fragments de contenu d&#39;un modèle donné {#sample-wknd-variation-multiple-fragment-given-model}

**Exemple de Requête**

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
