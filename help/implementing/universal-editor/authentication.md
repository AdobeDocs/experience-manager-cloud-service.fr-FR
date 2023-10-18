---
title: Authentification de l’éditeur universel
description: Découvrez comment l’éditeur universel utilise le système Identity Management (IMS) d’Adobe pour l’authentification.
exl-id: fb86c510-3c41-4511-81b7-1bdf2f5e7dd3
source-git-commit: 79fe3133a6b0553209b14c4cf47faa9db28caacc
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 89%

---


# Authentification de l’éditeur universel {#authentication}

Découvrez comment l’éditeur universel s’authentifie.

## Options {#options}

L’éditeur universel utilise l’authentification IMS (Identity Management System) d’Adobe, fournie par Unified Shell.

Toutes les applications/pages distantes sont chargées de l’authentification sur les systèmes principaux requis. Le service d’éditeur universel a besoin de cette authentification aux systèmes afin d’effectuer des opérations CRUD, car il s’agit d’un service autonome.

## Flux standard {#standard-flow}

Il s’agit de la solution pour AEM as a Cloud Service et AMS utilisant IMS pour utiliser l’éditeur universel.

Pour utiliser l’éditeur universel, il est nécessaire d’être connecté à Unified Shell qui s’authentifie auprès d’IMS. Le jeton IMS fourni est stocké dans le magasin de sessions des utilisateurs et des utilisatrices.

Chaque fois qu’une opération CRUD est effectuée, un appel est envoyé au service d’éditeur universel avec le jeton porteur IMS dans l’en-tête HTTP. Le service d’éditeur universel utilise ensuite le jeton porteur pour authentifier la requête sur le système principal AEM afin d’exécuter des opérations au nom de l’utilisateur ou de l’utilisatrice.

![Flux d’authentification standard](assets/standard-flow.png)

## Ressources supplémentaires {#additional-resources}

Pour en savoir plus sur l’éditeur universel, consultez ces documents.

* [Présentation de l’éditeur universel](introduction.md) - Découvrez comment l’éditeur universel permet de modifier n’importe quel aspect d’un contenu dans n’importe quelle implémentation afin de fournir des expériences exceptionnelles, d’augmenter la vitesse du contenu et d’offrir une expérience de développement à la pointe de la technologie.
* [Création de contenu avec l’éditeur universel](authoring.md) - Découvrez à quel point il est facile et intuitif pour les créateurs et les créatrices de contenu de créer du contenu à l’aide de l’éditeur universel.
* [Publication de contenu avec l’éditeur universel](publishing.md) - Découvrez comment l’éditeur universel publie du contenu et comment vos applications peuvent gérer le contenu publié.
* [Prise en main de l’éditeur universel dans AEM](getting-started.md) - Découvrez comment accéder à l’éditeur universel et comment commencer à instrumenter votre première application AEM pour l’utiliser.
* [Architecture de l’éditeur universel](architecture.md) - Découvrez l’architecture de l’éditeur universel et le flux de données entre ses services et calques.
* [Attributs et types](attributes-types.md) : découvrez les attributs et les types de données requis par l’éditeur universel.
