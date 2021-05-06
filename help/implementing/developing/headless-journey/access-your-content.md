---
title: Comment accéder à votre contenu via les API d'Diffusion AEM
description: Dans cette partie du Parcours de développement AEM sans tête, apprenez à utiliser les requêtes GraphQL pour accéder à votre contenu Fragments de contenu.
hide: true
hidefromtoc: true
index: false
exl-id: 5ef557ff-e299-4910-bf8c-81c5154ea03f
translation-type: tm+mt
source-git-commit: dd30bbb57d2746a7b16cb0546b90df0758fc3740
workflow-type: tm+mt
source-wordcount: '2120'
ht-degree: 32%

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

## AEM et GraphQL {#aem-graphql}

GraphQL est utilisé à divers endroits dans AEM; par exemple :

* Fragments de contenu
   * Une API personnalisée a été développée pour ce cas d’utilisation (Diffusion sans en-tête à votre application).
      * Il s’agit de l’API AEM GraphQL.
* Commerce
   * AEM Commerce utilise les données d&#39;une plateforme Commerce via GraphQL.
   * Il existe des intégrations GraphQL entre AEM et diverses solutions de commerce tierces, utilisées avec les crochets d&#39;extension fournis par les composants principaux de CIF.
      * Cette opération n’utilise pas l’API AEM GraphQL.

>[!NOTE]
>
>Cette étape du Parcours sans en-tête concerne uniquement l’API GraphQL AEM et les fragments de contenu.

## API AEM GraphQL {#aem-graphql-api}

L’API GraphQL AEM est une version personnalisée basée sur la spécification standard de l’API GraphQL, spécialement configurée pour vous permettre d’effectuer des requêtes (complexes) sur vos fragments de contenu.

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
   * Contenu de la requête pour l’application JS (cas d’utilisation standard)

* Environnement de création, utilisé pour :
   * Contenu de la requête à des &quot;fins de gestion de contenu&quot; :
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

* Est un type de données spécifique disponible lors de la définition d’un modèle de fragment de contenu.

* fait référence à un autre fragment, en fonction d’un modèle de fragment de contenu spécifique ;

* Permet de créer, puis de récupérer, des données structurées.

   * Lorsqu’elle est définie comme **référence à sources multiples**, plusieurs sous-fragments peuvent être référencés (récupérés) par le fragment principal.

### Prévisualisation JSON {#json-preview}

Pour faciliter la conception et le développement de vos modèles de fragments de contenu, vous pouvez prévisualisation la sortie JSON dans l’éditeur de fragments de contenu.

## Génération de Schéma GraphQL à partir de fragments de contenu {#graphql-schema-generation-content-fragments}

GraphQL est une API fortement typée, ce qui signifie que le contenu doit être clairement structuré et organisé par type. La spécification GraphQL fournit une série de directives sur la création d’une API robuste pour interroger du contenu sur une instance donnée. Un client doit pour cela récupérer le Schéma, qui contient tous les types nécessaires pour une requête.

Pour les fragments de contenu, les schémas GraphQL (structure et types) reposent sur des Modèles de fragments de contenu **activés** et leurs types de données

>[!CAUTION]
>
>Tous les schémas GraphQL (dérivés de modèles de fragments de contenu qui ont été **activés**) sont lisibles par le point d’entrée GraphQL.
>
>Cela signifie que vous devez vous assurer qu’aucun contenu sensible n’est disponible pour vous assurer qu’aucune donnée sensible n’est exposée au moyen de points de terminaison GraphQL ; par exemple, cela inclut des informations qui peuvent être présentes sous forme de noms de champ dans la définition de modèle.

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

## Utilisation de l’API GraphQL d’AEM {#actually-using-aem-graphiql}

Pour utiliser effectivement l’API GraphQL AEM dans une requête, nous pouvons utiliser les deux structures de base du modèle de fragment de contenu :

* Entreprise
   * Nom
   * PDG (Personne)
   * Employés (personnes)
* Personne
   * Nom
   * Prénom

Comme vous pouvez le voir, les champs PDG et Employés font référence aux fragments Personne.

Les modèles de fragments seront utilisés :

* lors de la création du contenu dans l’éditeur de fragments de contenu
* pour générer les schémas GraphQL que vous allez requête

Les requêtes peuvent être entrées dans l’interface GraphiQL, par exemple à l’adresse suivante :

* `http://localhost:4502/content/graphiql.html `

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
