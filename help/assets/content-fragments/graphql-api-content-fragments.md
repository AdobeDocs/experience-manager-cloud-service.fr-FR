---
title: aem API GraphQL à utiliser avec les fragments de contenu
description: Découvrez comment utiliser les fragments de contenu dans Adobe Experience Manager (AEM) en tant que Cloud Service avec l’API AEM GraphQL pour la Diffusion de contenu sans en-tête.
translation-type: tm+mt
source-git-commit: 47ed0f516b724c4d9a966bd051a022f322acb08e
workflow-type: tm+mt
source-wordcount: '3192'
ht-degree: 1%

---


# aem API GraphQL à utiliser avec les fragments de contenu {#graphql-api-for-use-with-content-fragments}

L’API Adobe Experience Manager en tant que Cloud Service (AEM) GraphQL utilisée avec Content Fragments repose principalement sur l’API GraphQL Open Source standard.

L’utilisation de l’API GraphQL dans AEM permet la diffusion efficace des fragments de contenu aux clients JavaScript dans les implémentations CMS sans affichage :

* Éviter les demandes d&#39;API itératives comme avec REST,
* veiller à ce que la diffusion soit limitée aux exigences spécifiques,
* Permet la diffusion en bloc de ce qui est exactement nécessaire pour le rendu en tant que réponse à une seule requête d&#39;API.

## API GraphQL {#graphql-api}

GraphQL est :

* &quot;*...un langage de requête pour les API et un runtime pour répondre à ces requêtes avec vos données existantes. GraphQL fournit une description complète et compréhensible des données de votre API, donne aux clients la possibilité de demander exactement ce dont ils ont besoin et rien de plus, facilite l&#39;évolution des API au fil du temps et permet de puissants outils de développement.*&quot;.

   Voir [GraphQL.org](https://graphql.org)

* &quot;*...une spécification ouverte pour une couche d’API flexible. Placez GraphQL sur vos soutiens existants pour créer des produits plus rapidement que jamais...*&quot;.

   Voir [Explore GraphQL](https://www.graphql.com).

* *&quot;...un langage et une spécification de requête de données développé en interne par Facebook en 2012 avant d&#39;être publiquement ouvert en 2015. Il offre une alternative aux architectures basées sur le REST dans le but d&#39;accroître la productivité des développeurs et de minimiser les quantités de données transférées. GraphQL est utilisé en production par des centaines d&#39;organisations de toutes tailles...&quot;*

   Voir [GraphQL Foundation](https://foundation.graphql.org/).

<!--
"*Explore GraphQL is maintained by the Apollo team. Our goal is to give developers and technical leaders around the world all of the tools they need to understand and adopt GraphQL.*". 
-->

Pour plus d’informations sur l’API GraphQL, voir les sections suivantes (entre autres ressources) :

* [graphql.org](https://graphql.org) :

   * [Présentation de GraphQL](https://graphql.org/learn)

   * [Spécification GraphQL](http://spec.graphql.org/)

* [graphql.com](https://graphql.com) :

   * [Guides](https://www.graphql.com/guides/)

   * [Tutoriels](https://www.graphql.com/tutorials/)

   * [Études de cas](https://www.graphql.com/case-studies/)

La valeur GraphQL pour l’implémentation AEM est basée sur la bibliothèque Java GraphQL standard. Voir :

* [graphQL.org - Java](https://graphql.org/code/#java)

* [Java GraphQL sur GitHub](https://github.com/graphql-java)

### Terminologie GraphQL {#graphql-terminology}

GraphQL utilise les éléments suivants :

* **[Requêtes](https://graphql.org/learn/queries/)**

* **[Schémas et types](https://graphql.org/learn/schema/)** :

   * Les schémas sont générés par AEM en fonction des modèles de fragment de contenu.
   * A l’aide de vos schémas, GraphQL présente les types et les opérations autorisés pour l’implémentation AEM GraphQL.

* **[Champs](https://graphql.org/learn/queries/#fields)**

* **[Point de terminaison GraphQL](#graphql-aem-endpoint)**
   * Chemin d’accès dans AEM qui répond aux requêtes GraphQL et permet d’accéder aux schémas GraphQL.

   * Voir [Activation de votre point de terminaison GraphQL](#enabling-graphql-endpoint) pour plus de détails.

Voir l&#39;[(GraphQL.org) Introduction à GraphQL](https://graphql.org/learn/) pour des détails complets, y compris les [Bonnes pratiques](https://graphql.org/learn/best-practices/).

### Types de Requêtes GraphQL {#graphql-query-types}

Avec GraphQL, vous pouvez exécuter des requêtes pour renvoyer l&#39;un ou l&#39;autre des éléments suivants :

* Une **entrée unique**

* A **[liste des entrées](https://graphql.org/learn/schema/#lists-and-non-null)**

Vous pouvez également effectuer les opérations suivantes :

* [Requêtes persistantes, mises en cache](#persisted-queries-caching)

## GraphQL pour le point de terminaison AEM {#graphql-aem-endpoint}

Le point de terminaison est le chemin utilisé pour accéder à GraphQL pour AEM. En utilisant ce chemin, vous (ou votre application) pouvez :

* accéder au schéma GraphQL,
* envoyer vos requêtes GraphQL,
* recevez les réponses (à vos requêtes GraphQL).

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

Il fournit des fonctionnalités telles que la mise en surbrillance de la syntaxe, la saisie semi-automatique et la suggestion automatique, ainsi qu’un historique et une documentation en ligne :

![Interface GraphiQL ](assets/cfm-graphiql-interface.png "InterfaceGraphiQL")

### Installation de l&#39;interface AEM GraphiQL {#installing-graphiql-interface}

L&#39;interface utilisateur de GraphiQL peut être installée sur AEM avec un package dédié : le package [GraphiQL Content Package v0.0.4](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faemcloud%2Fpublic%2Faem-graphql%2Fgraphiql-0.0.4.zip).

Voir le package **README** pour plus de détails ; comprenant des détails complets sur la façon dont il peut être installé sur une instance AEM, selon divers scénarios.

## Cas d’utilisation pour les Environnements d’auteur et de publication {#use-cases-author-publish-environments}

Les cas d’utilisation peuvent dépendre du type d’AEM en tant qu’environnement Cloud Service :

* Environnement de publication ; utilisé pour :
   * Données de requête pour l’application JS (cas d’utilisation standard)

* Environnement auteur ; utilisé pour :
   * Données de requête à des &quot;fins de gestion de contenu&quot; :
      * GraphQL en AEM en tant que Cloud Service est actuellement une API en lecture seule.
      * L’API REST peut être utilisée pour les opérations CR(u)D.

## Autorisations {#permission}

Les autorisations sont celles requises pour accéder aux ressources.

## Génération de schéma {#schema-generation}

GraphQL est une API fortement typée, ce qui signifie que les données doivent être clairement structurées et organisées par type.

La spécification GraphQL fournit une série de directives sur la création d&#39;une API robuste pour interroger les données sur une certaine instance. Pour ce faire, un client doit récupérer le [Schéma](#schema-generation), qui contient tous les types nécessaires pour une requête.

Pour les fragments de contenu, les schémas GraphQL (structure et types) sont basés sur **Activé** [Modèles de fragments de contenu](/help/assets/content-fragments/content-fragments-models.md) et leurs types de données.

>[!CAUTION]
>
>Tous les schémas GraphQL (dérivés de modèles de fragments de contenu qui ont été **activés**) sont lisibles par le point de terminaison GraphQL.
>
>Cela signifie que vous devez vous assurer qu’aucune donnée sensible n’est disponible, car elle peut être divulguée de cette façon ; par exemple, cela inclut des informations qui peuvent être présentes sous forme de noms de champ dans la définition de modèle.

Par exemple, si un utilisateur a créé un modèle de fragment de contenu appelé `Article`, AEM génère l’objet `article` de type `ArticleModel`. Les champs de ce type correspondent aux champs et aux types de données définis dans le modèle.

1. Un modèle de fragment de contenu :

   ![Modèle de fragment de contenu à utiliser avec le modèle de fragment ](assets/cfm-graphqlapi-01.png "GraphQLContent à utiliser avec GraphQL")

1. Schéma GraphQL correspondant (sortie de la documentation automatique GraphiQL) :
   ![Schéma GraphQL basé sur le Schéma Content Fragment ](assets/cfm-graphqlapi-02.png "ModelGraphQL basé sur le modèle Content Fragment Model")

   Cela montre que le type généré `ArticleModel` contient plusieurs [champs](#fields).

   * Trois d&#39;entre eux ont été contrôlés par l&#39;utilisateur : `author`, `main` et `referencearticle`.

   * Les autres champs ont été automatiquement ajoutés par AEM et représentent des méthodes utiles pour fournir des informations sur un certain fragment de contenu ; dans cet exemple, `_path`, `_metadata`, `_variations`. Ces [champs d&#39;assistance](#helper-fields) sont marqués par un `_` précédent pour distinguer ce qui a été défini par l&#39;utilisateur de ce qui a été généré automatiquement.

1. Après qu’un utilisateur a créé un fragment de contenu basé sur le modèle d’article, il peut être interrogé via GraphQL. Pour obtenir des exemples, reportez-vous à la section [Exemples de Requêtes](/help/assets/content-fragments/content-fragments-graphql-samples.md#graphql-sample-queries) (basée sur un modèle de structure de fragment de contenu [utilisé avec GraphQL](/help/assets/content-fragments/content-fragments-graphql-samples.md#content-fragment-structure-graphql)).

Dans GraphQL pour AEM, le schéma est flexible. Cela signifie qu’il est généré automatiquement chaque fois qu’un modèle de fragment de contenu est créé, mis à jour ou supprimé. Les caches de schéma de données sont également actualisés lorsque vous mettez à jour un modèle de fragment de contenu.

Le service Sites GraphQL écoute (en arrière-plan) toutes les modifications apportées à un modèle de fragment de contenu. Lorsque des mises à jour sont détectées, seule cette partie du schéma est régénérée. Cette optimisation permet de gagner du temps et de garantir la stabilité.

Par exemple, si vous :

1. Installez un package contenant `Content-Fragment-Model-1` et `Content-Fragment-Model-2` :

   1. Les types GraphQL pour `Model-1` et `Model-2` seront générés.

1. Modifiez ensuite `Content-Fragment-Model-2` :

   1. Seul le type `Model-2` GraphQL sera mis à jour.

   1. Alors que `Model-1` restera le même.

>[!NOTE]
>
>Il est important de le noter si vous souhaitez effectuer des mises à jour en masse sur les modèles de fragments de contenu via l’api REST, ou autrement.

Le schéma est desservi par le même point de terminaison que les requêtes GraphQL, le client gérant le fait que le schéma est appelé avec l&#39;extension `GQLschema`. Par exemple, l’exécution d’une requête simple `GET` sur `/content/cq:graphql/global/endpoint.GQLschema` entraîne la sortie du schéma avec le type de contenu : `text/x-graphql-schema;charset=iso-8859-1`.

## Champs {#fields}

Dans le schéma, il y a des champs individuels, de deux catégories de base :

* Champs que vous générez.

   Une sélection de [types de champs](#field-types) est utilisée pour créer des champs en fonction de la configuration du modèle de fragment de contenu. Les noms des champs proviennent du champ **Nom de la propriété** du **Type de données**.

   * Il existe également la propriété **Render As** à prendre en compte, car les utilisateurs peuvent configurer certains types de données ; par exemple, en tant que texte d’une seule ligne ou de plusieurs champs.

* GraphQL pour AEM génère également un certain nombre de [champs d&#39;aide](#helper-fields).

   Elles servent à identifier un fragment de contenu ou à obtenir plus d’informations sur ce fragment.

### Types de champ {#field-types}

GraphQL pour AEM prend en charge une liste de types. Tous les types de données de modèle de fragment de contenu pris en charge et les types GraphQL correspondants sont représentés :

| Modèle de fragment de contenu - Type de données | Type GraphQL | Description |
|--- |--- |--- |
| Une seule ligne de texte | Chaîne [Chaîne] |  Utilisé pour les chaînes simples telles que les noms d’auteur, les noms d’emplacement, etc. |
| Texte multiligne | Chaîne |  Utilisé pour la sortie de texte, tel que le corps d’un article |
| Nombre |  Flottant, [Float] | Utilisé pour afficher le nombre à virgule flottante et les nombres réguliers |
| Booléen |  Booléen |  Utilisé pour afficher les cases à cocher → simples instructions vrai/faux |
| Date et heure | Calendrier |  Utilisé pour afficher la date et l’heure au format ISO 8086 |
| Énumération |  Chaîne |  Utilisé pour afficher une option à partir d&#39;une liste d&#39;options définies lors de la création du modèle |
|  Balises |  [Chaîne] |  Utilisé pour afficher une liste de chaînes représentant les balises utilisées dans AEM |
| Référence de contenu |  Chaîne |  Utilisé pour afficher le chemin vers un autre fichier dans AEM |
| Référence du fragment |  *Type de modèle* |  Utilisé pour référencer un autre fragment de contenu d&#39;un certain type de modèle, défini lors de la création du modèle |

### Champs de l&#39;assistance {#helper-fields}

Outre les types de données des champs générés par l’utilisateur, GraphQL pour AEM génère également un certain nombre de champs *aide* afin d’identifier un fragment de contenu ou de fournir des informations supplémentaires sur un fragment de contenu.

#### Chemin {#path}

Le champ de chemin est utilisé comme identificateur dans GraphQL. Il représente le chemin d’accès de la ressource Fragment de contenu dans le référentiel AEM. Nous l’avons choisi comme identifiant d’un fragment de contenu, car il :

* est unique dans AEM,
* peut être facilement récupéré.

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

Pour récupérer un fragment de contenu unique d’un type spécifique, vous devez également déterminer d’abord son chemin d’accès. par exemple:

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

Par le biais de GraphQL, AEM expose également les métadonnées d’un fragment de contenu. Les métadonnées sont les informations qui décrivent un fragment de contenu, comme le titre d’un fragment de contenu, le chemin d’accès à la miniature, la description d’un fragment de contenu, la date de création, entre autres.

Etant donné que les métadonnées sont générées par l’éditeur de Schéma et que, à ce titre, elles ne comportent pas de structure spécifique, le type `TypedMetaData` GraphQL a été implémenté pour exposer les métadonnées d’un fragment de contenu. `TypedMetaData` expose les informations regroupées selon les types scalaires suivants :

| Field (Champ) |
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

Chaque type scalaire représente soit une paire nom-valeur unique, soit un tableau de paires nom-valeur, où la valeur de cette paire est du type dans lequel elle a été regroupée.

Par exemple, si vous souhaitez récupérer le titre d’un fragment de contenu, nous savons que cette propriété est une propriété String, de sorte que nous requêtes toutes les métadonnées String :

Pour requête des métadonnées :

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

Vous pouvez vue tous les types GraphQL de métadonnées si vous vue le schéma Generated GraphQL. Tous les types de modèle ont le même `TypedMetaData`.

>[!NOTE]
>
>**Différence entre les métadonnées normales et les métadonnées de tableau**
>Gardez à l’esprit que `StringMetadata` et `StringArrayMetadata` se rapportent tous deux à ce qui est stocké dans le référentiel et non à la façon dont vous les récupérez.
>
>Par exemple, en appelant le champ `stringMetadata`, vous recevriez un tableau de toutes les métadonnées stockées dans le référentiel sous la forme `String` et si vous appelez `stringArrayMetadata`, vous recevriez un tableau de toutes les métadonnées stockées dans le référentiel sous la forme `String[]`.

Voir [Exemple de Requête de métadonnées - Liste des métadonnées pour les prix intitulés GB](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-metadata-awards-gb).

#### Variations {#variations}

Le champ `_variations` a été implémenté pour simplifier l’interrogation des variations d’un fragment de contenu. Par exemple :

```xml
{
  personByPath(_path: "/content/dam/path/to/fragment/john-doe") {
    item {
      _variations
    }
  }
}
```

Voir [Exemple de Requête - Toutes les villes avec une variante nommée ](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-cities-named-variation).

<!--
## Security Considerations {#security-considerations}
-->

## Variables GraphQL {#graphql-variables}

GraphQL permet de placer des variables dans la requête. Pour plus d’informations, voir la documentation [GraphQL pour GraphiQL](https://graphql.org/learn/queries/#variables).

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

Dans GraphQL, il existe une possibilité de modifier la requête en fonction de variables, appelées directives GraphQL.

Par exemple, vous pouvez inclure le champ `adventurePrice` dans une requête pour tous les `AdventureModels`, en fonction d&#39;une variable `includePrice`.

![GraphQL ](assets/cfm-graphqlapi-04.png "DirectivesGraphQL Directives")

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

Le filtrage utilise une syntaxe basée sur des opérateurs logiques et des expressions.

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

* détails de [GraphQL pour les extensions AEM](/help/assets/content-fragments/content-fragments-graphql-samples.md#graphql-extensions)

* [Exemples de Requêtes utilisant cet exemple de contenu et de structure](/help/assets/content-fragments/content-fragments-graphql-samples.md#graphql-sample-queries-sample-content-fragment-structure)

   * Et l&#39;[exemple de contenu et de structure](/help/assets/content-fragments/content-fragments-graphql-samples.md#content-fragment-structure-graphql) préparé pour être utilisé dans des exemples de requêtes

* [Exemples de Requêtes basées sur le projet WKND](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-queries-using-wknd-project)

## Requêtes persistantes (mise en cache) {#persisted-queries-caching}

Après avoir préparé une requête avec une requête de POST, elle peut être exécutée avec une requête de GET qui peut être mise en cache par des caches HTTP ou un CDN.

Cela est nécessaire car les requêtes POST ne sont généralement pas mises en cache et si vous utilisez GET avec la requête comme paramètre, il existe un risque important que le paramètre devienne trop volumineux pour les services et intermédiaires HTTP.

Vous trouverez ci-dessous les étapes nécessaires à la persistance d’une requête donnée :

>[!NOTE]
>Avant cela, les **Requêtes de persistance GraphQL** doivent être activées, pour la configuration appropriée. Voir [Activer la fonctionnalité de fragment de contenu dans l’explorateur de configuration](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser) pour plus d’informations.

1. Préparez la requête en la plaçant dans la nouvelle URL de point de terminaison `/graphql/persist.json/<config>/<persisted-label>`.

   Par exemple, créez une requête persistante :

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

   Par exemple, recherchez la réussite :

   ```xml
   {
     "action": "create",
     "configurationName": "wknd",
     "name": "plain-article-query",
     "shortPath": "/wknd/plain-article-query",
     "path": "/conf/wknd/settings/graphql/persistentQueries/plain-article-query"
   }
   ```

1. Vous pouvez ensuite réexécuter la requête conservée en recherchant l’URL `/graphql/execute.json/<shortPath>`.

   Par exemple, utilisez la requête persistante :

   ```xml
   $ curl -X GET \
       http://localhost:4502/graphql/execute.json/wknd/plain-article-query
   ```

1. Mettez à jour une requête persistante de POSTing vers un chemin de requête existant.

   Par exemple, utilisez la requête persistante :

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

1. Créez une requête ordinaire enveloppée.

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

1. Créez une requête persistante avec des paramètres :

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

   * Utilisation d&#39;un POST pour la réplication :

      ```xml
      $curl -X POST   http://localhost:4502/bin/replicate.json \
        -H 'authorization: Basic YWRtaW46YWRtaW4=' \
        -F path=/conf/wknd/settings/graphql/persistentQueries/plain-article-query \
        -F cmd=activate
      ```

   * Utilisation d’un package :
      1. Créez une définition de package.
      1. Incluez la configuration (par exemple, `/conf/wknd/settings/graphql/persistentQueries`).
      1. Créez le module.
      1. Répliquez le package.
   * Utilisation de l&#39;outil de réplication/distribution.
      1. Accédez à l’outil Distribution.
      1. Sélectionnez l&#39;activation de l&#39;arborescence pour la configuration (par exemple, `/conf/wknd/settings/graphql/persistentQueries`).
   * Utilisation d’un processus (via la configuration du lanceur de processus) :
      1. Définissez une règle de lancement de processus pour exécuter un modèle de processus qui répliquerait la configuration sur différents événements (par exemple, créer, modifier, entre autres).



1. Une fois que la configuration de la requête est publiée, les mêmes principes s’appliquent, en utilisant simplement le point de terminaison de publication.

   >[!NOTE]
   >
   >Pour un accès anonyme, le système suppose que l’ACL permet à &quot;tout le monde&quot; d’avoir accès à la configuration de la requête.
   >
   >Si ce n&#39;est pas le cas, il ne pourra pas s&#39;exécuter.

   >[!NOTE]
   >
   >Les points-virgules (&quot;;&quot;) des URL doivent être codés.
   >
   >Par exemple, comme dans la demande d’exécution d’une requête persistante :
   >
   >
   ```xml
   >curl -X GET \ "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters%3bapath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
   >```

## Interrogation du point de terminaison GraphQL à partir d&#39;un site Web externe {#query-graphql-endpoint-from-external-website}

>[!NOTE]
>
>Pour un aperçu détaillé de la politique de partage des ressources CORS dans AEM voir [Comprendre le partage des ressources entre Origines (CORS)](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=en#understand-cross-origin-resource-sharing-(cors)).

Pour autoriser un site Web tiers à consommer la sortie JSON, une stratégie CORS doit être configurée dans le référentiel Git client. Pour ce faire, vous devez ajouter un fichier de configuration CORS OSGi approprié pour le point de terminaison souhaité. Cette configuration doit spécifier un nom de site Web approuvé (ou regex) pour lequel l&#39;accès doit être accordé.

* Accès au point de terminaison GraphQL :

   * alloworigine : [votre domaine] ou alloworiginregexp : [votre domaine regex]
   * méthodes prises en charge : [POST]
   * allowedpaths : [&quot;/content/graphql/global/endpoint.json&quot;]

* Accès au point de terminaison des requêtes persistantes GraphQL :

   * alloworigine : [votre domaine] ou alloworiginregexp : [votre domaine regex]
   * méthodes prises en charge : [GET]
   * allowedpaths : [&quot;/graphql/execute.json/.*&quot;]

>[!CAUTION]
>
>Il incombe au client de :
>
>* accorder uniquement l’accès aux domaines approuvés
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

Questions soulevées :

1. **Q** : &quot;*En quoi l&#39;API GraphQL pour AEM est-elle différente de l&#39;API Requête Builder ?*&quot;

   * **A** : &quot;*L’offre de l’API GraphQL  un contrôle total sur la sortie JSON et est une norme du secteur pour interroger du contenu.
AEM prévoit d&#39;investir dans l&#39;API AEM GraphQL.*&quot;

## Didacticiel - Pour commencer avec AEM sans en-tête et GraphQL {#tutorial}

Vous recherchez un didacticiel pratique ? Consultez [Prise en main de AEM didacticiel sans en-tête et GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html) de bout en bout illustrant comment créer et exposer du contenu à l’aide des API GraphQL d’AEM et consommé par une application externe, dans un scénario CMS sans en-tête.
