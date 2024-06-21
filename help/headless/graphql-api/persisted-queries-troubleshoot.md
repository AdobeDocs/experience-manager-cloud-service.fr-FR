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

La variable [Centre d’actions](/help/operations/actions-center.md) inclut la variable **Erreur de requête persistante de GraphQL** alerte Cela signifie que vous êtes informé chaque fois que l’une de vos requêtes persistantes GraphQL renvoie une erreur.

Pour vous aider à résoudre ces problèmes, cette page couvre les *le plus courant* causes des échecs et étapes à suivre pour les corriger.

## Modifications apportées au modèle de fragment de contenu {#changes-to-content-fragment-model}

Une requête GraphQL persistante peut échouer lorsqu’elle est basée sur des types GraphQL obsolètes, souvent en raison d’un changement dans les modèles de fragment de contenu sous-jacents.

De telles erreurs peuvent se produire pour diverses raisons. Par exemple (la liste n’est pas exhaustive), lorsque l’auteur d’un modèle de fragment de contenu :

* supprime ou renomme un champ
* met à jour la variable **Type de modèle** qui définit les modèles autorisés pour la référence au fragment
* annule la publication d’un modèle référencé par d’autres modèles.

Pour résoudre ces erreurs, vous devez :

* mettre à jour la requête persistante qui ne prend pas en charge les modifications apportées au modèle de fragment de contenu ;
* rétablir la modification sur le modèle qui a introduit le problème

## Point de terminaison GraphQL non configuré {#graphql-endpoint-not-configured}

Lorsque les requêtes conservées renvoient la variable `404` code d’erreur, ainsi que les informations `No suitable endpoint found`, cela signifie qu’aucun point de terminaison GraphQL n’est configuré dans l’environnement AEM.

Pour corriger ce problème, procédez comme suit pour activer et publier votre point de terminaison à partir de [Gestion des points de fin GraphQL dans AEM](/help/headless/graphql-api/graphql-endpoint.md).

## Chemin d’accès manquant dans l’URL de requête persistante de GraphQL {#missing-path-query-url}

Si les requêtes conservées renvoient la variable `400` code d’erreur avec les informations `Suffix: '/' does not contain a path`, le servlet GraphQL est appelé sans suffixe de chemin.

Le modèle doit être `/graphql/execute.json/thePath`.

## Blocage en raison de la liste autorisée IP {#blocked-due-to-ip-allow-list}

Dans ce cas, la requête renvoie la variable `405` code d’erreur.

Une telle erreur n’est pas spécifique à GraphQL. Voir l’article de la base de connaissances [Erreur 405 non autorisée](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-20824).

## Blocage par Dispatcher {#blocked-dispatcher}

Si le point de terminaison GraphQL renvoie la variable `404` erreur lors de la publication pour `POST` , cela signifie que les requêtes GraphQL sont bloquées au niveau du dispatcher et que le point de terminaison doit être activé manuellement.

Cela ne doit pas être le cas par défaut, mais une configuration Dispatcher personnalisée peut entraîner ce problème. Voir plus sous [Dispatcher : configuration du point d’entrée avec AEM sans affichage](/help/headless/deployment/dispatcher.md).
