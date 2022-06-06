---
title: Authentification pour les requêtes AEM GraphQL distantes sur les fragments de contenu
description: Découvrez l’authentification requise pour les requêtes distantes GraphQL d’AEM afin de sécuriser votre diffusion de contenu découplé.
feature: Content Fragments,GraphQL API
exl-id: dfeae661-06a1-4001-af24-b52ae12d625f
source-git-commit: 4e37db128aa31d6e8e950be0d077eae921a27468
workflow-type: ht
source-wordcount: '239'
ht-degree: 100%

---

# Authentification pour les requêtes AEM GraphQL distantes sur les fragments de contenu {#authentication-for-remote-aem-graphql-queries-on-content-fragments}

Un des principaux cas d’utilisation de l’[API Adobe Experience Manager as a Cloud Service (AEM) GraphQL pour la diffusion de fragments de contenu](/help/headless/graphql-api/content-fragments.md) consiste à accepter les requêtes distantes provenant d’applications ou de services tiers. Ces requêtes à distance peuvent nécessiter un accès authentifié à l’API afin de sécuriser la diffusion de contenu découplé.

>[!NOTE]
>
>Pour les tests et le développement, vous pouvez également directement accéder à l’API AEM GraphQL avec l’[interface GraphiQL](/help/headless/graphql-api/graphiql-ide.md).

Pour l’authentification, le service tiers doit utiliser un [jeton d’accès](#retrieving-access-token), qui peut ensuite être [utilisé dans la requête GraphQL](#use-access-token-in-graphql-request).

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

Vous pouvez vérifier cela en utilisant GraphiQL sur l’instance locale. Vous trouverez plus d’informations sur les [autorisations ici](/help/headless/security/permissions.md).
