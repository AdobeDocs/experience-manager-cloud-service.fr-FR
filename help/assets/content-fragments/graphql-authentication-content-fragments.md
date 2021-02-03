---
title: Authentification pour les Requêtes GraphQL d'AEM distantes sur les fragments de contenu
description: Découvrez l'authentification requise pour les requêtes GraphQL AEM distantes.
translation-type: tm+mt
source-git-commit: 42ca0c70f7018a6e3c9be68ef13adefafc987864
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---


# Authentification pour les Requêtes GraphQL d&#39;AEM distantes sur les fragments de contenu {#authentication-for-remote-aem-graphql-queries-on-content-fragments}

Une utilisation Principale de l&#39;API [Adobe Experience Manager en tant qu&#39;API GraphQL Cloud Service (AEM) pour la Diffusion de fragments de contenu](/help/assets/content-fragments/graphql-api-content-fragments.md) consiste à accepter les requêtes distantes provenant d&#39;applications ou de services tiers.  Ces requêtes distantes peuvent nécessiter un accès aux API authentifiées.

>[!NOTE]
>
>Pour les tests et le développement, vous pouvez également accéder à l&#39;API GraphQL AEM directement à l&#39;aide de l&#39;interface [GraphiQL](/help/assets/content-fragments/graphql-api-content-fragments.md#graphiql-interface).

Pour l’authentification, le service tiers doit utiliser un [Jeton d&#39;accès](#access-token), qui peut ensuite être [utilisé dans la demande GraphQL](#use-access-token-in-graphql-request).

## Récupération d&#39;un Jeton d&#39;accès {#retrieving-access-token}

Voir [Génération de Jetons d&#39;accès pour les API côté serveur](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) pour en savoir plus.

## Utilisation du Jeton d&#39;accès dans une requête GraphQL {#use-access-token-in-graphql-request}

Pour qu’un service tiers se connecte à une instance AEM, il doit avoir un *Jeton d&#39;accès*. Le service doit ensuite ajouter ce jeton à l&#39;en-tête `Authorization` de la demande du POST.

Par exemple, un en-tête d’autorisation GraphQL :

```xml
Authorization: Bearer <access_token>
```

## Exigences d&#39;autorisation {#permission-requirements}

Toutes les requêtes effectuées à l’aide du jeton d&#39;accès sont en fait effectuées *par le compte utilisateur qui a généré le jeton*.

Cela signifie que vous devez vérifier que le compte dispose des autorisations nécessaires pour exécuter les requêtes GraphQL.

Vous pouvez vérifier cela en utilisant GraphiQL sur l&#39;instance locale.
