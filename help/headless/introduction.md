---
title: Introduction à AEM sans tête
description: Découvrez Adobe Experience Manager (AEM) en tant que CMS sans affichage avec une combinaison de documentation détaillée et de parcours sans affichage. Découvrez comment des fonctionnalités telles que les modèles de contenu, les fragments de contenu et une API GraphQL sont utilisés pour alimenter des expériences sans interface.
landing-page-description: Apprenez comment utiliser et administrer Experience Manager Headless as a Cloud Service.
exl-id: 24300499-ae9c-49d0-aa25-f51e14d9cf79
source-git-commit: 30272a4729bc2e2b5213796789eb1422ba105074
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 31%

---


# Présentation d’Adobe Experience Manager as a Headless CMS {#introduction-aem-headless}

Découvrez comment utiliser Adobe Experience Manager (AEM) en tant que CMS sans affichage, avec des fonctionnalités telles que les modèles de contenu, les fragments de contenu et une API GraphQL qui optimisent les expériences sans affichage à grande échelle.

Vous pouvez lire la documentation détaillée des différentes fonctionnalités impliquées et/ou suivre la sélection de [Parcours sans affichage pour obtenir un aperçu des premières étapes](#first-steps).

## Présentation {#overview}

AEM Headless est une solution CMS de Experience Manager qui permet l’utilisation de contenu structuré (fragments de contenu) dans AEM par n’importe quelle application via HTTP à l’aide de GraphQL. Les implémentations sans affichage permettent la diffusion d’expériences sur les plateformes et les canaux à grande échelle.

L’implémentation découplée renonce à la gestion des pages et des composants, comme c’est généralement le cas avec les solutions hybrides et complètes, et se concentre sur la création de fragments de contenu réutilisables et neutres du point de vue du canal, ainsi que sur leur diffusion entre canaux. Il s’agit d’un modèle de développement moderne et dynamique pour l’implémentation d’expériences Web.

![Modèles d’implémentation AEM](assets/aem-implementation-models.png)

## Fonctionnalités d’AEM sans affichage {#aem-headless-features}

AEM as a Cloud Service est un outil flexible pour le modèle d’implémentation sans interface utilisateur graphique, qui offre trois fonctionnalités puissantes :

1. **Modèles de contenu**
   * Les modèles de contenu sont une représentation structurée du contenu.
   * Les modèles de contenu sont définis par les architectes d’informations dans l’éditeur de modèle de fragment de contenu AEM.
   * Les modèles de contenu servent de base aux fragments de contenu.
1. **Fragments de contenu**
   * Les fragments de contenu sont créés à partir d’un modèle de contenu.
   * Créé par les auteurs de contenu à l’aide de l’éditeur de fragment de contenu AEM.
   * Les fragments de contenu sont stockés dans AEM Assets et gérés dans l’interface utilisateur d’administration des ressources.
1. **API de contenu pour la diffusion**
   * L’API AEM GraphQL prend en charge la diffusion de fragments de contenu.
   * L’API REST AEM Assets prend en charge les opérations CRUD sur les fragments de contenu.
   * La diffusion de contenu direct est également possible avec la fonction [Exportation JSON du composant principal Fragment de contenu](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html?lang=fr).

## Vos premiers pas avec AEM découplé {#first-steps}

Plusieurs ressources sont disponibles pour commencer à utiliser AEM fonctionnalités sans interface. Chaque guide est adapté à différents cas d’utilisation et audiences.

| Ressource | Description | Type | Public | Temps estimé |
|---|---|---|---|---|
| [Parcours de développement découplé](/help/journey-headless/developer/overview.md) | **Pour les développeurs qui découvrent les AEM et qui n’ont pas d’interface** pour une présentation complète de l&#39;AEM et de ses fonctionnalités sans tête, depuis la théorie de l&#39;absence de tête jusqu&#39;à la mise en ligne de votre premier projet sans tête. | Guide | Développeurs **débutants avec AEM et le découplage** | 1 heure |
| [Configuration sans affichage](/help/headless/setup/introduction.md) | **Pour les utilisateurs AEM expérimentés** qui ont besoin d’un bref résumé des principales fonctionnalités d’AEM découplé, consultez cet aperçu de démarrage rapide. | Configuration des références | Développeurs, Administrateurs **avec AEM expérience** | 20 minutes |
| [Tutoriel pratique sans tête](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html?lang=fr) | **Si vous préférez une approche pratique et que vous connaissez les AEM**, ce tutoriel aborde directement la mise en oeuvre d’une application simple sans interface utilisateur. | Tutoriel | Développeurs | 2 heures |
| [Parcours d’architecture découplée](/help/journey-headless/architect/overview.md) | **Pour les architectes nouveaux à AEM et sans tête** technologies, commencez ici pour découvrir les fonctionnalités puissantes, flexibles et sans interface d’Adobe Experience Manager as a Cloud Service, et comment modéliser le contenu de votre projet. | Guide | Architectes | 1 heure |
| [Parcours de création découplée](/help/journey-headless/author/overview.md) | **Pour les utilisateurs professionnels qui découvrent AEM et qui n’ont pas d’interface utilisateur** technologies, commencez ici pour découvrir les fonctionnalités puissantes, flexibles et sans interface d’Adobe Experience Manager as a Cloud Service, et comment modéliser le contenu de votre projet. | Guide | Créateurs de contenu | 1 heure |
| [Parcours de traduction découplée](/help/journey-headless/translation/overview.md) | Pour ceux **intéressé par l&#39;AEM de l&#39;approche de la traduction à l&#39;absence de tête**. Découvrez les technologies sans interface et comment créer et mettre à jour des projets de traduction dans AEM de A à Z. | Guide | Spécialistes de la traduction | 1 heure |

## Comparaison entre couplage et découplage {#headful-headless}

Ce guide se concentre sur le modèle complet de mise en oeuvre sans interface d’AEM. Pour autant, le choix entre couplage et découplage n’est pas nécessairement binaire dans AEM. Des fonctionnalités sans affichage peuvent être utilisées pour gérer et diffuser du contenu sur plusieurs points de contact, tout en permettant aux auteurs de contenu de modifier des applications d’une seule page. Le tout dans AEM.

>[!TIP]
>
>Voir le document [Couplage et découplage dans AEM](/help/implementing/developing/headful-headless.md) pour plus d’informations.