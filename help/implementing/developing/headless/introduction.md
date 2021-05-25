---
title: Développement découplé pour AEM Sites as a Cloud Service
description: Découvrez comment AEM en tant que Cloud Service de puissantes fonctionnalités sans interface telles que les modèles de contenu, les fragments de contenu et l’API GraphQL fonctionnent ensemble pour vous permettre de gérer vos expériences de manière centralisée et de les diffuser sur l’ensemble des canaux.
exl-id: 24300499-ae9c-49d0-aa25-f51e14d9cf79
source-git-commit: 816c08b9351b3ce2fd4f31974d707e9d4a4eea27
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 61%

---


# Développement découplé pour AEM Sites as a Cloud Service {#headless-development}

Découvrez comment AEM en tant que Cloud Service de puissantes fonctionnalités sans interface telles que les modèles de contenu, les fragments de contenu et l’API GraphQL fonctionnent ensemble pour vous permettre de gérer vos expériences de manière centralisée et de les diffuser sur l’ensemble des canaux.

## Présentation {#overview}

L’implémentation découplée devient de plus en plus importante pour offrir des expériences à votre public, où qu’il se trouve et quel que soit son canal.

L’implémentation découplée renonce à la gestion des pages et des composants, comme c’est généralement le cas avec les solutions hybrides et complètes, et se concentre sur la création de fragments de contenu réutilisables et neutres du point de vue du canal, ainsi que sur leur diffusion entre canaux. Il s’agit d’un modèle de développement moderne et dynamique pour l’implémentation d’expériences Web.

![Modèles d’implémentation AEM](assets/aem-implementation-models.png)

## Comparaison entre couplage et découplage {#headful-headless}

Ce document se concentre sur le modèle de mise en œuvre entièrement découplée d’AEM. Pour autant, le choix entre couplage et découplage n’est pas nécessairement binaire dans AEM. Vous pouvez utiliser des fonctions découplées afin de gérer et diffuser votre contenu pour différents points d’entrée tout en permettant aux auteurs de contenu de modifier des applications sur une seule page. Le tout dans AEM.

>[!TIP]
>
>Voir le document [Couplage et découplage dans AEM](/help/implementing/developing/headful-headless.md) pour plus d’informations.

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
   * L’API GraphQL d’AEM prend en charge la diffusion de fragments de contenu.
   * L’API REST AEM Assets prend en charge les opérations CRUD sur les fragments de contenu.
   * La diffusion directe de contenu est également possible avec l’[exportation JSON du composant principal de fragment de contenu.](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/components/content-fragment-component.html)

## Vos premières étapes avec AEM sans affichage {#first-steps}

Un certain nombre de ressources sont disponibles pour que vous puissiez commencer à utiliser AEM fonctionnalités sans interface. Ils sont conçus pour différents cas d’utilisation, mais ils donnent tous une vue d’ensemble complète des fonctionnalités AEM sans interface.

| Ressource | Description | Type | Public | Est. Heure |
|---|---|---|---|---|
| [Parcours de développement sans tête](/help/journey-headless/developer/overview.md) | Pour une vue d&#39;ensemble complète des fonctionnalités AEM sans tête, de la théorie de l&#39;absence de tête à la mise en ligne de votre premier projet sans tête, commencez ici. | Guide d’ | Développeurs | 1 heure |
| [Guide de prise en main sans affichage](/help/implementing/developing/headless/getting-started/introduction.md) | Pour un bref résumé des principales fonctionnalités AEM sans interface, consultez cet aperçu de démarrage rapide. | Démarrage rapide | Développeurs, Administrateurs | 20 minutes |
| [Prise en main d’AEM tutoriel pratique sans affichage](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html) | Si vous préférez une approche pratique, ce tutoriel aborde directement la création d’un projet simple sans tête. | Tutoriel | Développeurs | 2 heures |
