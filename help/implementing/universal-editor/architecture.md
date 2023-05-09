---
title: Architecture d’éditeur universelle
description: Découvrez l’architecture d’Universal Editor et le flux de données entre ses services et calques.
exl-id: e6f40743-0f21-4fb6-bf23-76426ee174be
source-git-commit: 9cff6e94b38016f008fd8177be2e071a530d80b6
workflow-type: tm+mt
source-wordcount: '662'
ht-degree: 1%

---

# Architecture d’éditeur universelle {#architecture}

Découvrez l’architecture d’Universal Editor et le flux de données entre ses services et calques.

## Blocs de création d’architecture {#building-blocks}

L’éditeur universel est constitué de quatre blocs de création essentiels qui interagissent pour permettre aux auteurs de contenu de modifier n’importe quel aspect de tout contenu dans n’importe quelle mise en oeuvre afin de fournir des expériences exceptionnelles, d’augmenter la vitesse du contenu et de fournir une expérience de développement à la pointe de la technologie.

1. [Editeurs](#editors)
1. [Application distante](#remote-app)
1. [Couche d’API](#api-layer)
1. [Couche de persistance](#persistence-layer)

Ce document décrit chacun de ces blocs de création et la manière dont ils échangent des données.

![Architecture d’Universal Editor](assets/architecture.png)

>[!TIP]
>
>Si vous souhaitez voir l’éditeur universel et son architecture en action, reportez-vous au document . [Prise en main d’Universal Editor dans AEM](getting-started.md) pour savoir comment accéder à l’éditeur universel et comment commencer à instrumenter votre première application AEM pour l’utiliser.

### Editeurs {#editors}

* **Éditeur universel** - Universal Editor utilise un DOM instrumenté pour permettre la modification statique du contenu. Consultez le document [Attributs et types](attributes-types.md) pour plus d’informations sur les métadonnées nécessaires. Voir le document [Prise en main d’Universal Editor dans AEM](getting-started.md) pour un exemple de l’instrumentation dans AEM.
* **Rail Propriétés** - Certaines propriétés des composants ne peuvent pas être modifiées en contexte ; par exemple, l’heure de rotation d’un carrousel ou quel onglet accordéon doit toujours être ouvert ou fermé. Pour permettre la modification de ces informations de composant, un éditeur basé sur les formulaires est fourni dans le rail latéral de l’éditeur.

### Application distante {#remote-app}

Pour rendre une application modifiable en contexte dans l’éditeur universel, le modèle DOM doit être instrumenté. L’application distante doit effectuer le rendu de certains attributs dans le DOM. Consultez le document [Attributs et types](attributes-types.md) pour plus d’informations sur les métadonnées nécessaires. Voir le document [Prise en main d’Universal Editor dans AEM](getting-started.md) pour un exemple de l’instrumentation dans AEM.

Universal Editor s’efforce d’obtenir un SDK minimal. Par conséquent, l’instrumentation est la responsabilité de la mise en oeuvre de l’application distante.

### Couche d’API {#api-layer}

* **Données de contenu** - Pour l’éditeur universel, ni les systèmes source des données de contenu, ni la manière dont elles sont utilisées ne sont importants. Il est uniquement important de définir et de fournir les attributs requis à l’aide de données modifiables dans le contexte.
* **Données persistantes** - Pour chaque donnée modifiable, il existe un identifiant d’URL. Cette URL est utilisée pour acheminer la persistance vers le système et la ressource appropriés.

### Couche de persistance {#persistence-layer}

* **Modèle de fragment de contenu** - Pour prendre en charge le rail de modification des propriétés de fragment de contenu, l’éditeur de fragment de contenu et les éditeurs basés sur des formulaires, des modèles par composant et fragment de contenu sont requis.
* **Contenu** - Le contenu peut être stocké n’importe où, par exemple dans AEM, Magento, etc.

![Couche de persistance](assets/persistence-layer.png)

## Universal Editor Service et Backend System Dispatcher {#service}

Universal Editor distribue toutes les modifications de contenu à un service centralisé appelé Universal Editor Service. Ce service, exécuté sur Adobe I/O Runtime, charge les modules externes disponibles dans le registre des extensions en fonction de l’URL fournie. Le module externe est chargé de communiquer avec le serveur principal et de renvoyer une réponse unifiée.

![Service d’éditeur universel](assets/universal-editor-service.png)

## Rendu des pipelines {#rendering-pipelines}

### Rendu côté serveur {#server-side}

![Rendu côté serveur](assets/server-side.png)

### Génération statique du site {#static-generation}

![Génération statique du site](assets/static-generation.png)

### Rendu côté client {#client-side}

![Rendu côté client](assets/client-side.png)

## Ressources supplémentaires {#additional-resources}

Pour en savoir plus sur Universal Editor, consultez ces documents.

* [Présentation de l’éditeur universel](introduction.md) - Découvrez comment Universal Editor permet de modifier n’importe quel aspect de contenu dans n’importe quelle mise en oeuvre afin de fournir des expériences exceptionnelles, d’augmenter la vitesse du contenu et de fournir une expérience de développement à la pointe de la technologie.
* [Création de contenu avec l’éditeur universel](authoring.md) - Découvrez à quel point il est facile et intuitif pour les auteurs de contenu de créer du contenu à l’aide de l’éditeur universel.
* [Publication de contenu avec l’éditeur universel](publishing.md) - Découvrez comment l’éditeur visuel universel publie du contenu et comment vos applications peuvent gérer le contenu publié.
* [Prise en main d’Universal Editor dans AEM](getting-started.md) - Découvrez comment accéder à l’éditeur universel et comment commencer à instrumenter votre première application AEM pour l’utiliser.
* [Attributs et types](attributes-types.md) - Découvrez les attributs et les types de données requis par Universal Editor.
* [Authentification de l’éditeur universel](authentication.md) - Découvrez comment l’éditeur universel s’authentifie.
