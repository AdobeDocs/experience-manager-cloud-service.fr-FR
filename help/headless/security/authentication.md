---
title: Authentification pour les requêtes AEM GraphQL distantes sur les fragments de contenu
description: Comprenez l’authentification requise pour les requêtes GraphQL d’Adobe Experience Manager à distance afin de sécuriser votre diffusion de contenu sans interface utilisateur.
feature: Content Fragments,GraphQL API
exl-id: dfeae661-06a1-4001-af24-b52ae12d625f
source-git-commit: 7260649eaab303ba5bab55ccbe02395dc8159949
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 26%

---

# Authentification pour les requêtes AEM GraphQL distantes sur les fragments de contenu {#authentication-for-remote-aem-graphql-queries-on-content-fragments}

Un cas d’utilisation Principal pour la variable [API GraphQL Adobe Experience Manager as a Cloud Service (AEM) pour la diffusion de fragments de contenu](/help/headless/graphql-api/content-fragments.md) accepte des requêtes distantes provenant d’applications ou de services tiers. Ces requêtes distantes peuvent nécessiter un accès à l’API authentifié pour sécuriser la diffusion de contenu sans interface utilisateur.

>[!NOTE]
>
>Pour les tests et le développement, vous pouvez également accéder à l’API GraphQL d’AEM directement à l’aide de la variable [Interface GraphiQL](/help/headless/graphql-api/graphiql-ide.md).

Pour l’authentification, le service tiers doit [récupération d’un jeton d’accès](#retrieving-access-token) qui peut alors être [utilisé dans la requête GraphQL](#use-access-token-in-graphql-request).

## Récupération d’un jeton d’accès {#retrieving-access-token}

Voir [Génération de jetons d’accès pour les API côté serveur](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) pour plus d’informations.

## Utilisation du jeton d’accès dans une requête GraphQL {#use-access-token-in-graphql-request}

Pour qu’un service tiers se connecte à une instance AEM, il doit avoir une *Jeton d’accès*. Le service doit ensuite ajouter ce jeton à l’en-tête `Authorization` de la requête POST.

Par exemple, un en-tête Authorization GraphQL :

```xml
Authorization: Bearer <access_token>
```

## Exigences d’autorisation {#permission-requirements}

Toutes les demandes effectuées à l’aide du jeton d’accès sont effectuées *par le compte utilisateur qui a généré le jeton*.

Ce compte utilisateur signifie que vous devez vérifier que le compte dispose des autorisations requises pour exécuter des requêtes GraphQL.

Vous pouvez vérifier ces autorisations à l’aide de GraphiQL sur l’instance locale. Vous trouverez plus d’informations sur les [autorisations ici](/help/headless/security/permissions.md).
