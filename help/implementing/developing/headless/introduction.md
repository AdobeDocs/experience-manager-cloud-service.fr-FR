---
title: Développement découplé pour AEM Sites as a Cloud Service
description: Les fonctionnalités puissantes telles que les modèles de contenu, les fragments de contenu et l’API GraphQL d’AEM as a Cloud Service permettent de gérer vos expériences de manière centralisée et de les diffuser sur plusieurs canaux.
translation-type: tm+mt
source-git-commit: e1db93e8f4cf8ef881b274879e800c9993753a66
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 88%

---


# Développement découplé pour AEM Sites as a Cloud Service {#headless-development}

Les fonctionnalités puissantes telles que les modèles de contenu, les fragments de contenu et l’API GraphQL d’AEM as a Cloud Service permettent de gérer vos expériences de manière centralisée et de les diffuser sur plusieurs canaux.

## Présentation {#overview}

L’implémentation découplée devient de plus en plus importante pour offrir des expériences à votre public, où qu’il se trouve et quel que soit son canal.

L’implémentation découplée renonce à la gestion des pages et des composants, comme c’est généralement le cas avec les solutions hybrides et complètes, et se concentre sur la création de fragments de contenu réutilisables et neutres du point de vue du canal, ainsi que sur leur diffusion entre canaux. Il s’agit d’un modèle de développement moderne et dynamique pour l’implémentation d’expériences Web.

![Modèles d’implémentation AEM](assets/aem-implementation-models.png)

## Comparaison entre En-tête et Sans en-tête {#headful-headless}

Ce document se concentre sur le modèle complet de mise en oeuvre sans tête des AEM. Cependant, le choix entre tête et tête n&#39;est pas nécessairement un choix binaire en AEM. Vous pouvez utiliser des fonctions sans en-tête pour gérer et diffuser votre contenu sur divers points de terminaison tout en permettant aux auteurs de contenu de modifier des applications d’une seule page. Tout en AEM.

>[!TIP]
>
>Voir le document [En-tête et sans-tête dans AEM](/help/implementing/developing/headful-headless.md) pour plus d’informations.

## AEM as a Cloud Service et le découplage {#aem-headless}

AEM as a Cloud Service est un outil couple pour le modèle d’implémentation découplée avec trois services puissants :

1. Modèles de contenu
   * Les modèles de contenu sont une représentation structurée du contenu.
   * Ils sont définies par des architectes des informations dans l’éditeur de modèles de fragments de contenu AEM.
   * Les modèles de contenu servent de base aux fragments de contenu.
1. Fragments de contenu
   * Les fragments de contenu sont des instanciations de modèles de contenu.
   * Ils sont créés par les auteurs de contenu à l’aide de l’éditeur de fragments de contenu d’AEM.
   * Ils sont stockés dans AEM Assets et gérés dans l’interface utilisateur d’administration d’Assets.
1. API de contenu pour la diffusion
   * L’API AEM GraphQL prend en charge la diffusion de fragments de contenu.
   * L’API REST AEM Assets prend en charge les opérations CRUD sur les fragments de contenu.
   * La diffusion directe de contenu est également possible avec l’[exportation JSON du composant principal de fragment de contenu.](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/components/content-fragment-component.html)

## Guides de prise en main du découplage {#getting-started}

Les guides de prise en main du découplage proposent un chemin d’accès simple pour la création, la gestion et la diffusion d’expériences avec AEM as a Cloud Service en cinq étapes. Chaque guide s’appuie sur le précédent ; il est donc recommandé de les étudier en détail et dans l’ordre.

1. [Création d’une configuration](getting-started/create-configuration.md)
1. [Création d’un modèle de fragment de contenu](getting-started/create-content-model.md)
1. [Création d’un dossier Ressources](getting-started/create-assets-folder.md)
1. [Création d’un fragment de contenu](getting-started/create-content-fragment.md)
1. [Accès et diffusion de fragments de contenu](getting-started/create-api-request.md)

## Public {#audience}

Les tâches décrites dans les [Guides de prise en main du découplage](#getting-started) sont nécessaires pour une démonstration de base de bout en bout des capacités de découplage d’AEM. Toute personne disposant d’un accès administrateur à une instance AEM de test peut suivre ces guides pour comprendre la diffusion découplée dans AEM, même si une personne avec une expérience de développeur est idéale.

Cependant, dans une situation de production, les tâches seront exécutées par des personnes différentes un nombre variable de fois. Par exemple :

* Les **administrateurs** ne doivent normalement configurer la configuration initiale et la structure des dossiers pour le contenu qu’une seule fois ou de manière sporadique.
* Les **architectures des informations** ajoutent généralement de nouveaux modèles au fur et à mesure que les besoins de l’organisation évoluent.
* Les **auteurs de contenu** créent continuellement des contenus sur la base des modèles définis par les architectes.

Les guides de prise en main du découplage indiquent qui effectuerait généralement les tâches décrites et à quelle fréquence.

## Étape suivante {#next-step}

Prêt à en apprendre plus ? Alors commencez par lire la première partie du Guide de prise en main du découplage : [Création d’une configuration](getting-started/create-configuration.md).
