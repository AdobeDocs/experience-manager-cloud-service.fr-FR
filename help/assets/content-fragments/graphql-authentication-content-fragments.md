---
title: Authentification pour les requêtes AEM GraphQL distantes sur les fragments de contenu
description: Comprenez l'authentification requise pour les requêtes GraphQL d'AEM distantes afin de sécuriser votre diffusion de contenu sans en-tête.
feature: Fragments de contenu, API GraphQL
translation-type: tm+mt
source-git-commit: 6fa911f39d707687e453de270bc0f3ece208d380
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 84%

---


# Authentification pour les requêtes AEM GraphQL distantes sur les fragments de contenu {#authentication-for-remote-aem-graphql-queries-on-content-fragments}

Un des principaux cas d’utilisation de l’[API Adobe Experience Manager as a Cloud Service (AEM) GraphQL pour la diffusion de fragments de contenu](/help/assets/content-fragments/graphql-api-content-fragments.md) consiste à accepter les requêtes distantes provenant d’applications ou de services tiers. Ces requêtes distantes peuvent nécessiter un accès aux API authentifiées pour sécuriser la diffusion de contenu sans en-tête.

>[!NOTE]
>
>Pour les tests et le développement, vous pouvez également directement accéder à l’API GraphQL d’AEM avec l’[interface GraphiQL](/help/assets/content-fragments/graphql-api-content-fragments.md#graphiql-interface).

Pour l’authentification, le service tiers doit utiliser un [jeton d’accès](#access-token), qui peut ensuite être [utilisé dans la requête GraphQL](#use-access-token-in-graphql-request).

## Récupération d’un jeton d’accès {#retrieving-access-token}

Pour en savoir plus, voir [Génération de jetons d’accès pour les API côté serveur](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md).

## Utilisation du jeton d’accès dans une requête GraphQL {#use-access-token-in-graphql-request}

Pour qu’un service tiers se connecte à une instance AEM, il doit avoir un *jeton d’accès*. Le service doit ensuite ajouter ce jeton à l’en-tête `Authorization` de la requête POST.

Par exemple, un en-tête Authorization GraphQL :

```xml
Authorization: Bearer <access_token>
```

## Exigences d’autorisation {#permission-requirements}

Toutes les requêtes réalisées à l’aide du jeton d’accès sont en fait effectuées *par le compte utilisateur qui a généré le jeton*.

Cela signifie que vous devez vérifier que le compte dispose des autorisations nécessaires pour exécuter les requêtes GraphQL.

Vous pouvez vérifier cela en utilisant GraphiQL sur l’instance locale.
