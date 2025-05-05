---
title: Dépannage des requêtes GraphQL persistantes
description: Découvrez comment résoudre les problèmes liés aux requêtes GraphQL persistantes dans Adobe Experience Manager as a Cloud Service.
feature: Headless, Content Fragments,GraphQL API
exl-id: 71bd1f68-ca96-4c78-a936-abed250ecec1
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Résolution des problèmes liés aux requêtes GraphQL persistantes {#troubleshoot-persisted-graphql-queries}

Le [centre d’actions](/help/operations/actions-center.md) comprend l’alerte **erreur de requête persistante GraphQL** . Cela signifie que vous êtes informé chaque fois que l’une de vos requêtes persistantes GraphQL renvoie une erreur.

Pour vous aider à résoudre ces problèmes, cette page décrit les *causes d’échec les plus courantes* et les étapes à suivre pour les résoudre.

## Modifications apportées au modèle de fragment de contenu {#changes-to-content-fragment-model}

Une requête GraphQL persistante peut échouer lorsqu’elle est basée sur des types GraphQL obsolètes, souvent en raison d’un changement dans les modèles de fragment de contenu sous-jacents.

De telles erreurs peuvent se produire pour diverses raisons. Par exemple (la liste n’est pas exhaustive), lorsque l’auteur d’un modèle de fragment de contenu :

* supprime ou renomme un champ
* met à jour le **Type de modèle** qui définit les modèles autorisés pour la référence au fragment
* annule la publication d’un modèle référencé par d’autres modèles.

Pour résoudre ces erreurs, vous devez :

* mettre à jour la requête persistante qui ne prend pas en charge les modifications apportées au modèle de fragment de contenu ;
* rétablir la modification sur le modèle qui a introduit le problème

## Point de terminaison GraphQL non configuré {#graphql-endpoint-not-configured}

Lorsque des requêtes persistantes renvoient le code d’erreur `404`, ainsi que les informations `No suitable endpoint found`, cela signifie qu’aucun point de terminaison GraphQL n’est configuré dans l’environnement AEM.

Pour corriger ce problème, suivez les étapes pour activer et publier votre point de terminaison à partir de [Gérer les points de terminaison GraphQL dans AEM](/help/headless/graphql-api/graphql-endpoint.md).

## Chemin d’accès manquant dans l’URL de requête persistante de GraphQL {#missing-path-query-url}

Si les requêtes persistantes renvoient le code d’erreur `400` avec les informations `Suffix: '/' does not contain a path`, le servlet GraphQL est appelé sans suffixe de chemin.

Le modèle doit être `/graphql/execute.json/thePath`.

## Blocage en raison de la liste autorisée IP {#blocked-due-to-ip-allow-list}

Dans ce cas, la requête renvoie le code d’erreur `405`.

Une telle erreur n’est pas spécifique à GraphQL. Consultez l’article de la base de connaissances [405 Error Not Allowed](https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-20824).

## Blocage par Dispatcher {#blocked-dispatcher}

Si le point de terminaison GraphQL renvoie l’erreur `404` lors de la publication des requêtes `POST`, cela signifie que les requêtes GraphQL sont bloquées au niveau du Dispatcher et que le point de terminaison doit être activé manuellement.

Cela ne doit pas être le cas par défaut, mais une configuration Dispatcher personnalisée peut entraîner ce problème. Pour en savoir plus, voir [Dispatcher - Configuration de point d’entrée avec AEM sans affichage](/help/headless/deployment/dispatcher.md).
