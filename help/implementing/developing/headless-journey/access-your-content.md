---
title: Comment accéder à votre contenu via les API d'Diffusion AEM
description: Dans cette partie du Parcours de développement AEM sans tête, apprenez à utiliser les requêtes GraphQL pour accéder à votre contenu Fragments de contenu.
hide: true
hidefromtoc: true
index: false
translation-type: tm+mt
source-git-commit: 6097cb8961f604ec2d3f5f6d602c927efc7344d5
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 53%

---


# Comment accéder à votre contenu via les API d&#39;Diffusion d&#39;AEM {#access-your-content}

>[!CAUTION]
>
>TRAVAUX EN COURS - La création de ce document est en cours et ne doit pas être comprise comme complète ou définitive ni être utilisée à des fins de production.

Dans cette partie du [Parcours de développement AEM sans en-tête,](#overview.md) apprenez à utiliser les requêtes GraphQL pour accéder au contenu de vos fragments de contenu.

## L&#39;histoire jusqu&#39;à présent {#story-so-far}

Dans le document précédent du parcours sans tête AEM, [Comment modéliser votre contenu](model-your-content.md) vous avez appris les bases de la modélisation des données dans AEM et vous devez maintenant :

* Découvrez les points importants de la planification pour concevoir votre contenu.
* Comprenez les étapes à suivre pour implémenter sans tête en fonction des exigences de votre niveau d’intégration.
* Configurez les outils et les configurations AEM nécessaires.
* Découvrez les meilleures pratiques pour simplifier votre parcours sans tête, optimiser la génération de contenu et garantir la diffusion rapide du contenu.

Cet article s&#39;appuie sur ces principes de base pour vous aider à accéder à votre contenu sans en-tête existant dans AEM via l&#39;API.

* **Audience** : Début
* **Objectif** : Découvrez comment accéder au contenu de vos fragments de contenu à l’aide des requêtes GraphQL AEM :
   * Introduisez GraphQL.
   * Présentation de l’API AEM GraphQL.
   * Découvrez les détails de l’API GraphQL AEM.
   * Regardez quelques exemples de requêtes pour voir comment les choses fonctionnent dans la pratique.

Avec Adobe Experience Manager (AEM) en tant que Cloud Service, vous pouvez utiliser les fragments de contenu, ainsi que l’API AEM GraphQL, pour diffuser sans encombre du contenu structuré destiné à vos applications. La possibilité de personnaliser une seule requête d’API vous permet de récupérer et de diffuser le contenu spécifique que vous souhaitez rendre, ou avez besoin de rendre (comme réponse à la requête d’API unique).

>[!NOTE]
>AEM API GraphQL est une implémentation personnalisée, basée sur la norme GraphQL.

## GraphQL - Introduction {#graphql-introduction}

GraphQL est :

* « *...un langage de requête pour les API et un environnement d’exécution pour répondre à ces requêtes avec vos données existantes* ». 

   Voir *GraphQL*.

### GraphQL - Types {#graphql-types}

### GraphQL - Schémas {#graphql-schemas}

### GraphQL - Requêtes {#graphql-queries}

## AEM et GraphQL {#aem-graphql}

GraphQL est utilisé à divers emplacements dans AEM :

* Commerce
   * Espace réservé
* Fragments de contenu
   * Une API personnalisée a été développée pour ce cas d’utilisation.
   * Il s’agit de l’API AEM GraphQL.

## API AEM GraphQL {#aem-graphql-api}

Une implémentation personnalisée de l’API GraphQL standard a été développée pour Adobe Experience as a Cloud Experience.

L’API AEM GraphQL permet d’effectuer des requêtes (complexes) sur vos fragments de contenu ; chaque requête étant conforme à un type de modèle spécifique. Le contenu renvoyé peut alors être utilisé par vos applications.

>[!NOTE]
>
>L’implémentation de l’API AEM GraphQL repose sur les bibliothèques Java GraphQL.

### AEM API GraphQL et fragments de contenu {#aem-graphql-content-fragments}

## Fragments de contenu à utiliser avec l’API AEM GraphQL {#content-fragments-use-with-aem-graphql-api}

Les fragments de contenu peuvent servir de base à GraphQL pour les requêtes AEM car :

* Ils permettent de concevoir, créer, traiter et publier du contenu indépendant des pages.
* Les modèles de fragments de contenu fournissent la structure requise au moyen de types de données définis.
* La Référence du fragment, disponible lors de la définition d’un modèle, peut être utilisée pour définir des couches supplémentaires de structure.

### Fragments de contenu {#content-fragments}

Les fragments de contenu :

* contiennent du contenu structuré ;

* reposent sur un modèle de fragment de contenu, qui prédéfinit la structure pour le fragment résultant.

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

Pour faciliter la conception et le développement de vos modèles de fragments de contenu, vous pouvez prévisualiser la [sortie JSON](/help/assets/content-fragments/content-fragments-json-preview.md).

## Eléments suivants {#whats-next}

[Découvrez comment utiliser l’API REST pour accéder au contenu de vos fragments](/help/implementing/developing/headless-journey/update-your-content.md) de contenu et le mettre à jour.

## Ressources supplémentaires {#additional-resources}

* [GraphQL.org](https://graphql.org)
   * [Schémas](https://graphql.org/learn/schema/)
   * [Bibliothèques Java GraphQL](https://graphql.org/code/#java)
* [API GraphQL d’AEM à utiliser avec des fragments de contenu](/help/assets/content-fragments/graphql-api-content-fragments.md)
   * [Apprendre à utiliser GraphQL avec AEM – Exemple de contenu et de requêtes](/help/assets/content-fragments/content-fragments-graphql-samples.md)
   * [Authentification pour les requêtes AEM GraphQL distantes sur les fragments de contenu](/help/assets/content-fragments/graphql-authentication-content-fragments.md)
* [Utilisation de fragments de contenu](/help/assets/content-fragments/content-fragments.md)
   * [Modèles de fragment de contenu](/help/assets/content-fragments/content-fragments-models.md)
   * [Sortie JSON](/help/assets/content-fragments/content-fragments-json-preview.md)
