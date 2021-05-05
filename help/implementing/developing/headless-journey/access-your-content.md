---
title: Comment accéder à votre contenu via les API d'Diffusion AEM
description: Dans cette partie du Parcours de développement AEM sans tête, apprenez à utiliser les requêtes GraphQL pour accéder à votre contenu Fragments de contenu.
hide: true
hidefromtoc: true
index: false
exl-id: 5ef557ff-e299-4910-bf8c-81c5154ea03f
translation-type: tm+mt
source-git-commit: 7b04ae2bfa75fe3d3af13271efe567a5fc401f49
workflow-type: tm+mt
source-wordcount: '4636'
ht-degree: 55%

---

# Comment accéder à votre contenu via les API d&#39;Diffusion d&#39;AEM {#access-your-content}

>[!CAUTION]
>
>TRAVAUX EN COURS - La création de ce document est en cours et ne doit pas être comprise comme complète ou définitive ni être utilisée à des fins de production.

Dans cette partie du [Parcours de développement AEM sans en-tête](overview.md), vous pouvez apprendre à utiliser les requêtes GraphQL pour accéder au contenu de vos fragments de contenu.

## L&#39;histoire jusqu&#39;à présent {#story-so-far}

Dans le document précédent du parcours sans tête AEM, [Comment modéliser votre contenu](model-your-content.md) vous avez appris les principes de base de la modélisation des données dans AEM. Vous devez donc maintenant comprendre comment modéliser votre structure de contenu, puis réaliser cette structure à l’aide de modèles de fragments de contenu et de fragments de contenu AEM :

* Reconnaissez les concepts et la terminologie liés à la modélisation des données [](#data-modeling).
* Comprenez [pourquoi la modélisation des données est nécessaire pour la diffusion de contenu sans en-tête](#data-modeling-for-aem-headless).
* Comprenez [comment réaliser cette structure à l’aide de modèles de fragments de contenu AEM](#create-structure-content-fragment-models) (et créez du contenu avec [Fragments de contenu](#use-content-to-author-content)).
* comprendre [comment modéliser votre contenu](#getting-started-examples); principes avec des exemples de base.

Cet article s&#39;appuie sur ces principes de base pour vous aider à accéder à votre contenu sans en-tête existant dans AEM à l&#39;aide de l&#39;API AEM GraphQL.

* **Audience** : Début
* **Objectif** : Découvrez comment accéder au contenu de vos fragments de contenu à l’aide des requêtes GraphQL AEM :
   * Présentation de GraphQL et de l’API GraphQL AEM.
   * Découvrez les détails de l’API GraphQL AEM.
   * Regardez quelques exemples de requêtes pour voir comment les choses fonctionnent dans la pratique.

## Vous souhaitez donc accéder à vos données ? {#so-youd-like-to-access-your-data}

Donc...vous disposez de tout ce contenu, soigneusement structuré (dans Fragments de contenu), et vous n’avez qu’à attendre pour alimenter votre nouvelle application. La question est : comment y arriver ?

Vous avez besoin d’un moyen de cible de contenu spécifique, de sélectionner ce dont vous avez besoin et de le renvoyer à votre application pour un traitement ultérieur.

Avec Adobe Experience Manager (AEM) en tant que Cloud Service, vous pouvez accéder de manière sélective à vos fragments de contenu, à l’aide de l’API AEM GraphQL, pour renvoyer uniquement le contenu dont vous avez besoin. Cela signifie que vous pouvez réaliser une diffusion illisible de contenu structuré à utiliser dans vos applications.

>[!NOTE]
>
>AEM API GraphQL est une implémentation personnalisée, basée sur la norme GraphQL.

## GraphQL - Introduction {#graphql-introduction}

GraphQL est une spécification open source qui fournit :

* langage de requête qui vous permet de sélectionner un contenu spécifique à partir d’objets structurés.
* un runtime pour réaliser ces requêtes avec votre contenu structuré.

GraphQL est une API *fortement* typée. Cela signifie que *tout* contenu doit être clairement structuré et organisé par type, de sorte que GraphQL *comprenne* ce à quoi accéder et comment. Les champs de données sont définis dans des schémas GraphQL, qui définissent la structure de vos objets de contenu.

Les points de terminaison GraphQL fournissent ensuite les chemins qui répondent aux requêtes GraphQL.

Cela signifie que votre application peut sélectionner avec précision, fiabilité et efficacité les données dont elle a besoin - exactement ce dont vous avez besoin lorsqu&#39;elle est utilisée avec AEM.

>[!NOTE]
>
>Voir *GraphQL*.org et *GraphQL*.com.

## AEM et GraphQL {#aem-graphql}

GraphQL est utilisé à divers endroits dans AEM; par exemple :

* Commerce
   * Il existe des intégrations GraphQL entre AEM et diverses solutions de commerce tierces, utilisées avec les crochets d&#39;extension fournis par les composants principaux de CIF.
* Fragments de contenu
   * Une API personnalisée a été développée pour ce cas d’utilisation.
   * Il s’agit de l’API AEM GraphQL.

>[!NOTE]
>
>Cette étape du Parcours sans en-tête concerne uniquement l’API GraphQL AEM et les fragments de contenu.

## API AEM GraphQL {#aem-graphql-api}

L’API GraphQL AEM est une version personnalisée de l’API GraphQL standard, spécialement configurée pour vous permettre d’effectuer des requêtes (complexes) sur vos fragments de contenu.

Les fragments de contenu sont utilisés, dans la mesure où le contenu est structuré selon les modèles de fragments de contenu. Cela répond à une exigence de base de GraphQL.

* Un modèle de fragment de contenu est constitué d’un ou de plusieurs champs.
   * Chaque champ est défini selon un type de données.
* Les modèles de fragments de contenu sont utilisés pour générer les Schémas GraphQL AEM correspondants.

Pour accéder à GraphQL pour AEM (et au contenu), un point de terminaison est utilisé pour fournir le chemin d&#39;accès.

Le contenu renvoyé, via l&#39;API AEM GraphQL, peut alors être utilisé par vos applications.

>[!NOTE]
>
>L’implémentation de l’API AEM GraphQL repose sur les bibliothèques Java GraphQL.

### Cas d’utilisation pour les environnements de création et de publication {#use-cases-author-publish-environments}

Les cas d’utilisation de l’API GraphQL AEM peuvent dépendre du type d’AEM en tant qu’environnement Cloud Service :

* Environnement de publication, utilisé pour :
   * Réaliser des requête de données pour l’application JS (cas d’utilisation standard)

* Environnement de création, utilisé pour :
   * Réaliser des requêtes de données à des fins de gestion de contenu :
      * GraphQL dans AEM as a Cloud Service est actuellement une API en lecture seule.
      * L’API REST peut être utilisée pour les opérations CR(u)D.

## Fragments de contenu à utiliser avec l’API AEM GraphQL {#content-fragments-use-with-aem-graphql-api}

Les fragments de contenu peuvent servir de base à GraphQL pour les schémas et requêtes AEM en tant que :

* Ils permettent de concevoir, créer, traiter et publier du contenu indépendant des pages.
* Ils sont basés sur un modèle de fragment de contenu, qui prédéfinit la structure du fragment obtenu au moyen de types de données définis.
* D’autres couches de structure peuvent être obtenues avec le type de données Référence de fragment, disponible lors de la définition d’un modèle.

### Modèles de fragment de contenu {#content-fragments-models}

Ces modèles de fragment de contenu :

* Sont utilisés pour générer les Schémas, une fois **Activés**.

* fournissent les types de données et les champs requis pour GraphQL ; garantissent que votre application ne demande que ce qui est possible et reçoive ce qui est attendu.

* Le type de données **Références de fragments** peut être utilisé dans votre modèle pour faire référence à un autre fragment de contenu et introduit ainsi des niveaux de structure supplémentaires.

### Références à un fragment {#fragment-references}

La **référence à un fragment** :

* est particulièrement intéressante en lien avec GraphQL ;

* est un type de données spécifique qui peut être utilisé lors de la définition d’un modèle de fragment de contenu ;

* fait référence à un autre fragment, en fonction d’un modèle de fragment de contenu spécifique ;

* permet de récupérer des données structurées.

   * Lorsqu’elle est définie comme **référence à sources multiples**, plusieurs sous-fragments peuvent être référencés (récupérés) par le fragment principal.

### Prévisualisation JSON {#json-preview}

Pour faciliter la conception et le développement de vos modèles de fragments de contenu, vous pouvez prévisualisation la sortie JSON dans l’éditeur de fragments de contenu.

## Génération de Schéma GraphQL à partir de fragments de contenu {#graphql-schema-generation-content-fragments}

GraphQL est une API dans laquelle les données doivent être clairement structurées et organisées par type. La spécification GraphQL fournit une série de directives sur la création d’une API robuste pour interroger les données sur une certaine instance. Un client doit pour cela récupérer le Schéma, qui contient tous les types nécessaires pour une requête.

Pour les fragments de contenu, les schémas GraphQL (structure et types) reposent sur des Modèles de fragments de contenu **activés** et leurs types de données

>[!CAUTION]
>
>Tous les schémas GraphQL (dérivés de modèles de fragments de contenu qui ont été **activés**) sont lisibles par le point d’entrée GraphQL.
>
>En d’autres termes, vous devez vous assurer qu’aucune donnée sensible n’est disponible, car elle peut être divulguée de cette façon ; par exemple, cela concerne des informations qui peuvent être présentes sous forme de noms de champ dans la définition de modèle.

Par exemple, si un utilisateur a créé un modèle de fragment de contenu nommé `Article`, AEM génère l’objet `article` de type `ArticleModel`. Les champs de ce type correspondent aux champs et aux types de données définis dans le modèle.

1. Un modèle de fragment de contenu :

   ![Modèle de fragment de contenu à utiliser avec GraphQL](assets/graphqlapi-cfmodel.png "Modèle de fragment de contenu à utiliser avec GraphQL")

1. Schéma GraphQL correspondant (sortie de la documentation automatique GraphiQL) :
   ![Schéma GraphQL basé sur le modèle de fragment de contenu](assets/graphqlapi-cfm-schema.png "Schéma GraphQL basé sur le modèle de fragment de contenu")

   Cela montre que le type généré `ArticleModel` contient plusieurs [champs](#fields).

   * Trois d’entre eux ont été contrôlés par l’utilisateur : `author`, `main` et `referencearticle`.

   * Les autres champs ont été ajoutés automatiquement par AEM et représentent des méthodes utiles pour fournir des informations sur un certain fragment de contenu ; dans cet exemple, `_path`, `_metadata` et `_variations`. Ces [champs d&#39;assistance](#helper-fields) sont marqués par un `_` précédent pour distinguer ce qui a été défini par l&#39;utilisateur de ce qui a été généré automatiquement.

1. Après qu’un utilisateur a créé un fragment de contenu reposant sur le modèle d’article, il peut être interrogé via GraphQL. Pour obtenir des exemples, voir Exemple de Requêtes.md#graphql-sample-requêtes (basé sur un exemple de structure de fragment de contenu à utiliser avec GraphQL).

Dans GraphQL pour AEM, le schéma est flexible. Cela signifie qu’il est généré automatiquement à chaque fois qu’un modèle de fragment de contenu est créé, mis à jour ou supprimé. Les caches de schémas de données sont également actualisés lorsque vous mettez à jour un modèle de fragment de contenu.

Le service Sites GraphQL écoute (en arrière-plan) toutes les modifications apportées à un modèle de fragment de contenu. Lorsque des mises à jour sont détectées, seule cette partie du schéma est régénérée. Cette optimisation permet de gagner du temps et de garantir la stabilité.

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

### Génération de schéma - Modèles non publiés {#schema-generation-unpublished-models}

Lorsque des fragments de contenu sont imbriqués, il se peut qu’un modèle de fragment de contenu parent soit publié, mais pas un modèle référencé.

>[!NOTE]
>
>L’interface utilisateur AEM empêche cela, mais si la publication est effectuée par programmation ou avec des packages de contenu, elle peut se produire.

Dans ce cas, AEM génère un Schéma *incomplet* pour le modèle de fragment de contenu parent. Cela signifie que la référence au fragment, qui dépend du modèle non publié, est supprimée du schéma.

## AEM Points de terminaison GraphQL {#aem-graphql-endpoints}

<!--
need details/examples
-->

Un point de terminaison est le chemin utilisé pour accéder à GraphQL pour l&#39;AEM. Avec ce chemin, vous (ou votre application) pouvez :

* accéder aux schémas GraphQL,
* envoyer vos requêtes GraphQL ;
* recevoir les réponses (à vos requêtes GraphQL).

AEM permet :

* Point de terminaison global - disponible pour tous les sites.
* Points de terminaison du client - que vous pouvez configurer, spécifiques à un site/projet spécifique.

## Autorisations {#permissions}

Les autorisations sont celles requises pour accéder aux ressources.

## AEM Interface GraphiQL {#aem-graphiql-interface}

Pour vous aider à saisir directement et à tester des requêtes, une implémentation de l&#39;interface standard de GraphiQL est disponible pour une utilisation avec AEM GraphQL. Cette interface peut être installée avec AEM.

Il fournit des fonctionnalités telles que la mise en surbrillance de la syntaxe, la saisie semi-automatique et la suggestion automatique, ainsi qu’un historique et une documentation en ligne.

![Interface GraphiQL](assets/graphiql-interface.png "Interface GraphiQL")

<!--
new page?
-->

## Utilisation de l’API GraphQL AEM {#using-aem-graphiql}

### Points de terminaison {#endpoints}

Le chemin d’accès au référentiel de GraphQL pour AEM point de terminaison global est :

`/content/cq:graphql/global/endpoint`

Pour lequel votre application peut utiliser le chemin d’accès suivant dans l’URL de demande :

`/content/_cq_graphql/global/endpoint.json`

Pour un point de terminaison locataire, les chemins sont comparables :

`/content/cq:graphql/your-tenant/endpoint`
`/content/_cq_graphql/your-tenant/endpoint.json`

Avant l’utilisation, tous les points de fin doivent être activés. Pour activer un point de terminaison, global ou locataire, pour GraphQL pour AEM vous devez :

* Activation de votre point d’entrée GraphQL
* Publier votre point de terminaison

>[!CAUTION]
>
>L’éditeur de fragments de contenu peut autoriser un fragment de contenu d’un client à référencer un fragment de contenu d’un autre client (par le biais de stratégies).
>
>Dans ce cas, tout le contenu ne peut pas être récupéré à l’aide d’un point de terminaison spécifique au client.
>
>L&#39;auteur du contenu doit contrôler ce scénario ; par exemple, il peut s’avérer utile d’envisager de placer des modèles de fragments de contenu partagés sous le client global.

### Activation de votre point d’entrée GraphQL {#enabling-graphql-endpoint}

Pour activer un point de terminaison GraphQL, vous devez d&#39;abord disposer d&#39;une configuration appropriée dans le navigateur de configuration.

>[!CAUTION]
>
>Si l’utilisation des modèles de contenu du fragment n’a pas été activée, l’option **Créer** n’est pas disponible.

Pour activer le point de terminaison correspondant :

1. Accédez à **Outils**, **Sites**, puis sélectionnez **GraphQL**.
1. Sélectionnez **Créer**.
1. La boîte de dialogue **Créer un nouveau point de terminaison GraphQL** s&#39;ouvre. Vous pouvez spécifier ici :
   * **Nom** : nom du point de terminaison ; vous pouvez saisir n’importe quel texte.
   * **Utilisez le schéma GraphQL fourni par** : utilisez la liste déroulante pour sélectionner le site/projet requis.

   >[!NOTE]
   >
   >L’avertissement suivant s’affiche dans la boîte de dialogue :
   >
   >* *Les points d’entrée GraphQL peuvent présenter des problèmes de sécurité et de performance des données si ils ne sont pas gérés de manière adaptée. Veillez à définir les autorisations appropriées après la création d’un point d’entrée.*


1. Confirmez avec **Créer**.
1. La boîte de dialogue **Étapes suivantes** fournit un lien direct vers la console de sécurité afin que vous puissiez vous assurer que le nouveau point de terminaison dispose des autorisations appropriées.

   >[!CAUTION]
   >
   >Le point d’entrée est accessible à tous. Cela peut entraîner un problème de sécurité, en particulier pour les instances de publication, car les requêtes GraphQL peuvent imposer une charge importante au serveur.
   >
   >Vous pouvez configurer des listes de contrôle d’accès pour le point d’entrée en fonction de votre cas d’utilisation.

### Publication de votre point de terminaison GraphQL {#publishing-graphql-endpoint}

Sélectionnez le nouveau point de terminaison et **Publier** pour le rendre entièrement disponible dans tous les environnements.

>[!CAUTION]
>
>Le point d’entrée est accessible à tous.
>
>Sur les instances de publication, cela peut poser un problème de sécurité, car les requêtes GraphQL peuvent imposer une charge importante au serveur.
>
>Vous devez configurer des listes de contrôle d&#39;accès appropriées à votre cas d&#39;utilisation sur le point de terminaison.

### Installation de l’interface AEM GraphiQL {#installing-graphiql-interface}

L&#39;interface utilisateur de GraphiQL peut être installée sur AEM avec un package dédié : le package [GraphiQL Content Package v0.0.6 (2021.3)](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-graphql/graphiql-0.0.6.zip).

### AEM Schémas GraphQL {#aem-graphql-schemas}

Pour accéder à vos données, vous devez d’abord sélectionner le type de modèle de fragment de contenu requis, représenté par un Schéma GraphQL. AEM Schémas GraphQL sont dérivés de vos modèles de fragments de contenu - à utiliser dans vos requêtes GraphQL.

<!--
Confirm is the schema city or CityModel? -->

Si vous avez un modèle de fragment de contenu nommé `City`, il y aura un schéma correspondant appelé `city`. Vous pouvez utiliser la requête suivante pour liste du `name` de tous les fragments de contenu basés sur ce modèle.

```xml
query {
  cityList {
    items {
      name
    }
  }
}
```

Vous pouvez utiliser la requête suivante pour liste des `name` et `description` de tous les `types` schémas disponibles :

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

### AEM champs GraphQL {#aem-graphql-fields}

Une fois que vous avez sélectionné le schéma dont vous avez besoin, vous souhaitez accéder à des données spécifiques, représentées par des champs du schéma.

Le schéma comporte des champs individuels de deux catégories de base :

* Champs que vous générez.

   Une sélection de [types de champs](#field-types) est utilisée pour créer des champs en fonction de la configuration du modèle de fragment de contenu. Les noms des champs proviennent du champ **Nom de la propriété** du **Type de données**.

   * Il faut également tenir compte de la propriété **Rendre comme**, car les utilisateurs peuvent configurer certains types de données, par exemple comme une seule ligne de texte ou avec plusieurs champs.

* GraphQL pour AEM génère également un certain nombre de champs d’assistance.

   Ils servent à identifier un fragment de contenu ou à obtenir plus d’informations sur un fragment.

### Types de champs {#field-types}

GraphQL pour AEM prend en charge une liste de types. Tous les types de données de modèles de fragments de contenu pris en charge et les types GraphQL correspondants sont représentés :

| Modèle de fragment de contenu – Type de données | Type GraphQL | Description |
|--- |--- |--- |
| Texte sur une seule ligne | Chaîne, [Chaîne] | Utilisé pour les chaînes simples telles que les noms d’auteur, les noms d’emplacement, etc. |
| Texte multiligne | Chaîne | Utilisé pour générer du texte, tel que le corps d’un article |
| Nombre | Flottant, [Flottant] | Utilisé pour afficher le nombre à virgule flottante et les nombres réguliers |
| Booléen | Booléen | Utilisé pour afficher les cases à cocher → simples instructions vrai/faux |
| Date et heure | Calendrier | Utilisé pour afficher la date et l’heure au format ISO 8086. Selon le type sélectionné, trois saveurs peuvent être utilisées dans AEM GraphQL : `onlyDate`, `onlyTime`, `dateTime` |
| Énumération | Chaîne | Utilisé pour afficher une option à partir d’une liste d’options définies lors de la création du modèle |
| Balises | [Chaîne] | Utilisé pour afficher une liste de chaînes représentant les balises utilisées dans AEM |
| Référence de contenu | Chaîne | Utilisé pour afficher le chemin vers une autre ressource dans AEM |
| Référence du fragment | *Un type de modèle* | Utilisé pour référencer un autre fragment de contenu d’un certain type de modèle, défini lors de la création du modèle |

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

>[!NOTE]
>
>Voir Exemple de requête – Un fragment de ville unique et spécifique.

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
| `booleanArrayMetadata:[booleanArrayMetadata]!` |
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

>[!NOTE]
>
>Voir Modèle de recherche de métadonnées – Répertorier les métadonnées des prix intitulés GB.

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

>[!NOTE]
>
>Voir Exemple de requête – Toutes les villes avec une variante nommée.

### AEM Variables GraphQL {#aem-graphql-variables}

Les variables sont utiles dans toute forme de programmation ou d’interrogation, car elles vous permettent de stocker des valeurs différentes à un seul emplacement. Pour AEM GraphQL, cela signifie qu’au lieu d’avoir à écrire une requête distincte pour chaque valeur, vous pouvez écrire votre requête pour une variable, et la valeur de cette variable peut changer si nécessaire.

GraphQL permet de placer des variables dans la requête.

>[!NOTE]
>
>Pour plus d’informations, consultez la documentation GraphQL relative aux variables.

Par exemple, pour obtenir tous les fragments de contenu de type `Article` qui présentent une variation spécifique, vous pouvez spécifier la variable `variation` dans GraphiQL. Toutes les instances seront récupérées dans `GetArticlesByVariation`, puis transmises pour être utilisées dans `articleList`.

![Variables GraphQL](assets/graphqlapi-variables.png "Variables GraphQL")

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

### AEM GraphQL Directives {#aem-graphql-directives}

Dans GraphQL, il est possible de modifier la requête en fonction de variables, nommées directives GraphQL.

Par exemple, vous pouvez inclure ici le champ `adventurePrice` dans une requête pour tous les `AdventureModels`, en fonction d’une variable `includePrice`.

!![GraphQL Directives](assets/graphqlapi-directives.png &quot;GraphQL Directives&quot;)

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

### AEM Filtres GraphQL {#aem-graphql-filters}

Vous pouvez également utiliser le filtrage dans vos requêtes GraphQL pour renvoyer des données spécifiques.

Le filtrage utilise une syntaxe basée sur des expressions et des opérateurs logiques.

Par exemple, la requête (de base) suivante filtre toutes les personnes dont le nom est `Jobs` ou `Smith` :

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

Pour accéder à d’autres exemples, voir :

* détails des extensions GraphQL pour AEM

* Modèles de requêtes utilisant ce modèle de contenu et de structure

### AEM Extensions GraphQL {#aem-graphql-extensions}

Le fonctionnement de base des requêtes avec GraphQL pour AEM est conforme à la spécification GraphQL standard. Pour les requêtes GraphQL avec AEM, il existe quelques extensions :

* Si vous avez besoin d’un seul résultat :
   * Utilisez le nom du modèle ; p. ex. city.

* Si vous prévoyez une liste de résultats :
   * Ajoutez `List` au nom du modèle ; par exemple, `cityList`
   * Voir [Exemple de requête – Toutes les informations sur toutes les villes ](#sample-all-information-all-cities)

* Si vous souhaitez utiliser un OU logique :
   * Utilisez ` _logOp: OR`
   * Voir [Exemple de requête – Toutes les personnes qui portent le nom « Jobs » ou « Smith »](#sample-all-persons-jobs-smith)

* L’opérateur logique ET existe également, mais est (souvent) implicite

* Vous pouvez appliquer des requêtes aux noms de champ qui correspondent aux champs du modèle de fragment de contenu.
   * Voir [Exemple de requête – Détails complets relatifs au PDG et aux employés d’une entreprise ](#sample-full-details-company-ceos-employees)

* Outre les champs de votre modèle, il existe certains champs générés par le système (précédés d’un trait de soulignement) :

   * Pour le contenu :

      * `_locale` : pour afficher la langue ; basé sur Language Manager
         * Voir [Exemple de requête pour plusieurs fragments de contenu d’un paramètre régional donné ](#sample-wknd-multiple-fragments-given-locale)
      * `_metadata` : pour afficher les métadonnées de votre fragment
         * Voir [Modèle de recherche de métadonnées – Répertorier les métadonnées des prix intitulés GB](#sample-metadata-awards-gb)
      * `_model` : autoriser l’interrogation d’un modèle de fragment de contenu (chemin et titre)
         * Voir [Exemple de requête pour un modèle de fragment de contenu à partir d’un modèle](#sample-wknd-content-fragment-model-from-model)
      * `_path` : chemin d’accès à votre fragment de contenu dans le référentiel
         * Voir [Exemple de requête – Un fragment de ville unique et spécifique](#sample-single-specific-city-fragment)
      * `_reference` : pour afficher les références ; y compris les références intégrées dans l’éditeur de texte enrichi
         * Voir [Exemple de requête pour plusieurs fragments de contenu avec des références préalablement récupérées ](#sample-wknd-multiple-fragments-prefetched-references)
      * `_variation` : pour afficher des variantes spécifiques dans votre fragment de contenu
         * Voir [Exemple de requête – Toutes les villes avec une variante nommée](#sample-cities-named-variation)
   * Et les opérations :

      * `_operator` : pour appliquer des opérateurs spécifiques ; `EQUALS`, `EQUALS_NOT`, `GREATER_EQUAL`, `LOWER`, `CONTAINS`,, `STARTS_WITH`
         * Voir [Exemple de requête – Toutes les personnes qui ne portent pas le nom « Jobs »](#sample-all-persons-not-jobs)
         * Voir [Exemple de Requête - Toutes les aventures où `_path` début avec un préfixe spécifique](#sample-wknd-all-adventures-cycling-path-filter)
      * `_apply` : pour appliquer des conditions spécifiques ; par exemple `AT_LEAST_ONCE`
         * Voir [Exemple de requête : effectuer un filtrage sur un tableau avec un élément qui doit se produire au moins une fois ](#sample-array-item-occur-at-least-once)
      * `_ignoreCase` : pour ignorer la casse lors de l’application de la requête
         * Voir [Exemple de requête : toutes les villes dont le nom contient SAN, indépendamment de la casse ](#sample-all-cities-san-ignore-case)









* Les types d’union GraphQL sont pris en charge :

   * Utilisez `... on`
      * Voir [Exemple de requête pour un fragment de contenu d’un modèle spécifique avec une référence de contenu ](#sample-wknd-fragment-specific-model-content-reference)

### Requêtes conservées (cache) {#persisted-queries-caching}

Après avoir préparé une requête avec une requête POST, elle peut être exécutée avec une requête GET qui peut être mise en cache par des caches HTTP ou un réseau CDN.

Cela est nécessaire, car les requêtes POST ne sont généralement pas mises en cache et si vous utilisez GET avec la requête comme paramètre, il existe un risque important que le paramètre devienne trop volumineux pour les services et intermédiaires HTTP.

Les requêtes persistantes doivent toujours utiliser le point de terminaison lié à la configuration appropriée (locataire) ; pour qu&#39;ils puissent utiliser l&#39;une ou l&#39;autre des méthodes suivantes, ou les deux :

* Configuration globale et point de terminaison
La requête a accès à tous les modèles de fragments de contenu.
* Configuration(s) de client(s) spécifique(s) et point(s) de terminaison(s)
La création d’une requête persistante pour une configuration de client spécifique requiert un point de terminaison spécifique au client correspondant (pour fournir l’accès aux modèles de fragment de contenu connexes).
Par exemple, pour créer une requête persistante spécifiquement pour le client WKND, une configuration de client spécifique WKND correspondante et un point de terminaison spécifique WKND doivent être créés à l&#39;avance.

>[!NOTE]
>
>Voir Activation de la fonctionnalité de fragment de contenu dans le navigateur de configuration pour plus d’informations.
>
>Les **Requêtes de persistance GraphQL** doivent être activées pour la configuration de locataire appropriée.

Par exemple, s’il existe une requête particulière appelée `my-query`, qui utilise un modèle `my-model` de la configuration du client `my-conf` :

* Vous pouvez créer une requête à l&#39;aide du point de terminaison `my-conf` spécifique, puis la requête sera enregistrée comme suit :
   `/conf/my-conf/settings/graphql/persistentQueries/my-query`
* Vous pouvez créer la même requête à l’aide du point de terminaison `global`, mais la requête sera enregistrée comme suit :
   `/conf/global/settings/graphql/persistentQueries/my-query`

>[!NOTE]
>
>Il s&#39;agit de deux requêtes différentes - enregistrées sous des chemins différents.
>
>Il se trouve qu&#39;ils utilisent le même modèle - mais via des points de terminaison différents.

Vous trouverez ci-dessous les étapes nécessaires à la conservation d’une requête donnée :

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

### Requête du point d’entrée GraphQL à partir d’un site Web externe {#query-graphql-endpoint-from-external-website}

Pour accéder au point de terminaison GraphQL à partir d’un site Web externe, vous devez configurer les éléments suivants :

* Filtre CORS
* Filtre de parrain

#### Filtre CORS {#cors-filter}

>[!NOTE]
>
>Pour un aperçu détaillé de la politique de partage des ressources CORS dans AEM, voir Description du partage des ressources Cross-Origin (CORS).

Pour accéder au point de terminaison GraphQL, une stratégie CORS doit être configurée dans le référentiel Git du client. Pour ce faire, vous devez ajouter un fichier de configuration CORS OSGi approprié pour les points de terminaison souhaités.

Cette configuration doit spécifier une origine de site Web approuvée `alloworigin` ou `alloworiginregexp` pour laquelle l&#39;accès doit être accordé.

Par exemple, pour accorder l’accès au point de terminaison GraphQL et au point de terminaison de requêtes persistantes pour `https://my.domain`, vous pouvez utiliser :

```xml
{
  "supportscredentials":true,
  "supportedmethods":[
    "GET",
    "HEAD",
    "POST"
  ],
  "exposedheaders":[
    ""
  ],
  "alloworigin":[
    "https://my.domain"
  ],
  "maxage:Integer":1800,
  "alloworiginregexp":[
    ""
  ],
  "supportedheaders":[
    "Origin",
    "Accept",
    "X-Requested-With",
    "Content-Type",
    "Access-Control-Request-Method",
    "Access-Control-Request-Headers"
  ],
  "allowedpaths":[
    "/content/_cq_graphql/global/endpoint.json",
    "/graphql/execute.json/.*"
  ]
}
```

Si vous avez configuré un chemin d&#39;accès à la vanité pour le point de terminaison, vous pouvez également l&#39;utiliser dans `allowedpaths`.

#### Filtre de parrain {#referrer-filter}

Outre la configuration CORS, un filtre de Parrain doit être configuré pour autoriser l’accès à partir d’hôtes tiers.

Pour ce faire, ajoutez un fichier de configuration de filtre de Parrain OSGi approprié qui :

* spécifie un nom d&#39;hôte de site Web approuvé ; soit `allow.hosts`, soit `allow.hosts.regexp`,
* accorde l&#39;accès pour ce nom d&#39;hôte.

Par exemple, pour accorder l’accès aux requêtes avec le Parrain `my.domain`, vous pouvez :

```xml
{
    "allow.empty":false,
    "allow.hosts":[
      "my.domain"
    ],
    "allow.hosts.regexp":[
      ""
    ],
    "filter.methods":[
      "POST",
      "PUT",
      "DELETE",
      "COPY",
      "MOVE"
    ],
    "exclude.agents.regexp":[
      ""
    ]
}
```

>[!CAUTION]
>
>Il incombe au client de :
>
>* n’accorder l’accès qu’aux domaines approuvés ;
>* s’assurer qu’aucune information sensible n’est exposée
>* ne pas utiliser la syntaxe de caractère générique [*] ; cette méthode désactive à la fois l’accès authentifié au point d’entrée GraphQL et l’expose par ailleurs vis-à-vis du monde entier.


>[!CAUTION]
>
>Tous les schémas GraphQL (dérivés de modèles de fragments de contenu qui ont été **activés**) sont lisibles par le point d’entrée GraphQL.
>
>En d’autres termes, vous devez vous assurer qu’aucune donnée sensible n’est disponible, car elle peut être divulguée de cette façon ; par exemple, cela concerne des informations qui peuvent être présentes sous forme de noms de champ dans la définition de modèle.

### Authentification GraphQL {#aem-graphql-authentication} AEM

Une utilisation Principale de l’API GraphQL de Adobe Experience Manager en tant qu’API Cloud Service (AEM) pour la Diffusion de fragments de contenu consiste à accepter les requêtes distantes provenant d’applications ou de services tiers. Ces requêtes distantes peuvent nécessiter un accès aux API authentifiées pour sécuriser la diffusion de contenu sans en-tête.

>[!NOTE]
>
>Pour les tests et le développement, vous pouvez également directement accéder à l’API GraphQL d’AEM avec l’interface GraphiQL.

Pour l’authentification, le service tiers doit utiliser un jeton d’accès, qui peut ensuite être utilisé dans la requête GraphQL.

#### Récupération d’un jeton d’accès {#retrieving-access-token}

Pour en savoir plus, voir Génération de jetons d’accès pour les API côté serveur.

#### Utilisation du jeton d’accès dans une requête GraphQL {#use-access-token-in-graphql-request}

Pour qu’un service tiers se connecte à une instance AEM, il doit avoir un *jeton d’accès*. Le service doit ensuite ajouter ce jeton à l’en-tête `Authorization` de la requête POST.

Par exemple, un en-tête Authorization GraphQL :

```xml
Authorization: Bearer <access_token>
```

#### Exigences d’autorisation {#permission-requirements}

Toutes les requêtes réalisées à l’aide du jeton d’accès sont en fait effectuées *par le compte utilisateur qui a généré le jeton*.

Cela signifie que vous devez vérifier que le compte dispose des autorisations nécessaires pour exécuter les requêtes GraphQL.

Vous pouvez vérifier cela en utilisant GraphiQL sur l’instance locale.

## Exemples de Requêtes GraphQL d&#39;AEM {#samples-aem-graphql-queries}

Voir Apprendre à utiliser GraphQL avec AEM - Exemple de contenu et de Requêtes pour obtenir une gamme complète d’exemples de requêtes.

<!--
## Code Samples for AEM GraphQL Queries {#code-samples-aem-graphql-queries}
-->

## Eléments suivants {#whats-next}

Maintenant que vous avez appris à accéder à votre contenu sans en-tête et à le requête à l’aide de l’API AEM GraphQL, vous pouvez [apprendre à utiliser l’API REST pour accéder au contenu de vos fragments de contenu](/help/implementing/developing/headless-journey/update-your-content.md) et le mettre à jour.

## Ressources supplémentaires {#additional-resources}

* [GraphQL.org](https://graphql.org)
   * [Schémas](https://graphql.org/learn/schema/)
   * [Variables](https://graphql.org/learn/queries/#variables)
   * [Bibliothèques Java GraphQL](https://graphql.org/code/#java)
* [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql)
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
* [Prise en main de AEM sans tête](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html?lang=fr)  - Une courte série de didacticiels vidéo qui présente un aperçu de l&#39;utilisation des fonctionnalités sans tête AEM, y compris la modélisation des données et GraphQL.
