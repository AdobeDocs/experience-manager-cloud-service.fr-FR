---
title: Authentification de l’éditeur universel
description: Découvrez comment l’éditeur universel s’authentifie.
source-git-commit: 0e66c379e10d275610d85a699da272dc0c32a9a8
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# Authentification de l’éditeur universel {#authentication}

Découvrez comment l’éditeur universel s’authentifie.

## Options {#options}

L’éditeur universel utilise l’authentification IMS (Identity Management System) d’Adobe, fournie par l’intermédiaire du Shell unifié.

Toutes les applications/pages distantes sont chargées de l’authentification sur les systèmes principaux requis. Le service Universal Editor a besoin de cette authentification pour appuyer les systèmes afin d’effectuer des opérations CRUD, car il s’agit d’un service autonome.

## Flux standard {#standard-flow}

Il s’agit de la solution pour AEM as a Cloud Service et AMS utilisant IMS pour utiliser l’éditeur universel.

Pour utiliser l’éditeur universel, l’utilisateur doit être connecté au Shell unifié qui s’authentifie auprès d’IMS. Le jeton IMS fourni est stocké dans le magasin de sessions des utilisateurs.

Chaque fois qu’un utilisateur effectue une opération CRUD, un appel est envoyé au service Universal Editor avec le jeton porteur IMS dans l’en-tête HTTP. Le service Universal Editor utilise ensuite le jeton porteur pour authentifier la requête sur le système principal AEM afin d’exécuter des opérations au nom de l’utilisateur.

![Flux d’authentification standard](assets/standard-flow.png)

## Ressources supplémentaires {#additional-resources}

Pour en savoir plus sur Universal Editor, consultez ces documents.

* [Présentation de l’éditeur universel](introduction.md) - Découvrez comment Universal Editor permet de modifier n’importe quel aspect de contenu dans n’importe quelle mise en oeuvre afin de fournir des expériences exceptionnelles, d’augmenter la vitesse du contenu et de fournir une expérience de développement à la pointe de la technologie.
* [Création de contenu avec l’éditeur universel](authoring.md) - Découvrez à quel point il est facile et intuitif pour les auteurs de contenu de créer du contenu à l’aide de l’éditeur universel.
* [Publication de contenu avec l’éditeur universel](publishing.md) - Découvrez comment l’éditeur visuel universel publie du contenu et comment vos applications peuvent gérer le contenu publié.
* [Prise en main d’Universal Editor dans AEM](getting-started.md) - Découvrez comment accéder à l’éditeur universel et comment commencer à instrumenter votre première application AEM pour l’utiliser.
* [Architecture d’éditeur universelle](architecture.md) - Découvrez l’architecture d’Universal Editor et le flux de données entre ses services et calques.
* [Attributs et types](attributes-types.md) - Découvrez les attributs et les types de données requis par Universal Editor.
