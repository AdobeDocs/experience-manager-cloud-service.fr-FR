---
title: API AEM pour la diffusion de contenu structuré et la gestion des fragments de contenu
description: Découvrez les API disponibles pour la diffusion de contenu structuré et la gestion des fragments de contenu
feature: Headless, Content Fragments, Edge Delivery Services
role: Admin, Developer
exl-id: 95aecd30-566a-42a9-b97a-7efe45fd389c
source-git-commit: e427bd34867974c663e67a2124f257cd12e946ae
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# API AEM pour la diffusion et la gestion de contenu structuré {#aem-apis-structured-content-delivery-and-management}

Adobe Experience Manager (AEM) as a Cloud Service propose plusieurs API pour la diffusion de contenu structuré à partir de fragments de contenu et la gestion de fragments de contenu. Voir les pages individuelles pour plus de détails sur les API spécifiques.

* [Diffusion de fragments de contenu AEM avec OpenAPI](/help/headless/aem-content-fragment-delivery-with-openapi.md)
   * Cette API crée des réponses JSON pour diffuser du contenu structuré à partir de fragments de contenu dans AEM.
   * Elle utilise un chemin d’accès vers un fragment de contenu comme point d’entrée.
   * Cette API est basée sur REST.
   * Elle est optimisée pour la diffusion de contenu, y compris l’intégration du réseau CDN.
* [API GraphQL AEM pour la diffusion de fragments de contenu](/help/headless/graphql-api/content-fragments.md)
   * Cette API est basée sur les schémas. Les schémas d’API sont représentés par des modèles de fragment de contenu, qui définissent la structure du contenu.
   * Cette API est basée sur GraphQL.
* [API OpenAPI de fragments de contenu et de modèles de fragment de contenu](/help/headless/content-fragment-openapis.md)
   * Ces API sont destinées à la gestion de contenu structuré.
   * Les opérateurs GET respectifs ne sont pas optimisés pour la diffusion de contenu.
   * Cette API est basée sur REST.
* [Prise en charge des fragments de contenu dans l’API HTTP AEM Assets](/help/assets/content-fragments/assets-api-content-fragments.md)
   * API d’origine pour la sortie JSON pour la diffusion de contenu structuré dans AEM.
      * Bien que robuste et éprouvée, cette API ne fournit pas de sortie JSON *entièrement hydratée*. Les références ne sont générées que comme chemins d’accès, ce qui nécessite des requêtes d’API secondaires pour récupérer du contenu supplémentaire.
   * L’API HTTP Assets peut également être utilisée pour gérer les fragments de contenu et les modèles de fragment de contenu (CRUD).
   * Cette API est basée sur REST.
   * La prise en charge des fragments de contenu dans l’API HTTP Assets sera abandonnée à l’avenir, car elle sera remplacée par l’API REST JSON Edge Delivery Services. Le calendrier n’a pas encore été fixé.

## REST par rapport à GraphQL {#rest-vs-graphql}

L’API utilisée est une décision qui appartient aux développeurs, car AEM prend en charge les deux.

De nombreuses comparaisons sont disponibles en ligne, mais les points forts et les avantages de REST sont les suivants :

* Simplicité

   * Les développeurs connaissent (souvent) bien HTTP et REST. Selon le rapport État [Postman des API ](https://www.postman.com/state-of-api/), un pourcentage élevé de développeurs utilisent REST.

   * Avec la simplicité vient la familiarité. Avec REST, il n’existe aucune question organisationnelle concernant le propriétaire des requêtes et celui de l’application, alors que ces questions peuvent se poser avec GraphQL.

   * La familiarité s’accompagne (généralement) d’une large communauté et d’un paysage d’outils. Il ne s’agit pas d’un inconvénient inhérent à GraphQL, mais il sera probablement plus large et plus profond pour REST.

   * L’approche plus simple peut également faciliter la mise en œuvre de la sécurité. Avec REST, le filtrage permettant de déterminer le contenu à rendre a lieu dans l’application cliente. Avec GraphQL, cela se produit dans une requête basée sur un schéma entre le client et le serveur.

* Flexibilité

   * Avec REST, le développeur peut `GET` n’importe quelle ressource. Avec GraphQL, elles sont limitées aux ressources définies dans un schéma.

* Mise en cache

   * Les réponses JSON aux requêtes de `GET` REST peuvent par nature être mises en cache. Les requêtes `POST` de GraphQL ne peuvent pas être mises en cache, à moins que cela ne soit le cas, par exemple, en utilisant les Requêtes persistantes d’AEM qui sont stockées sur le serveur et demandées avec des requêtes `GET` de type REST.

Les avantages de GraphQL sont les suivants :

* Efficacité de la diffusion de contenu

   * Cible d’action

      * Avec GraphQL, les applications clientes peuvent demander le contenu exact dont elles ont besoin pour le rendu, et rien de plus. Cette approche évite la surdiffusion du contenu, avec des payloads de contenu excessifs et une consommation de bande passante inutile.

   * Point d’entrée unique

      * Alors que dans REST, chaque requête d’API est un point d’entrée, dans GraphQL, il n’existe qu’un seul point d’entrée commun et les différentes requêtes de contenu sont exprimées sous forme de requêtes utilisant ce point d’entrée commun.

* Prototypage rapide

   * Avec GraphQL, il s’agit d’un processus en une étape, regroupé dans la requête GraphQL, qui peut faciliter le prototypage. Le REST, en revanche, est un processus en 2 étapes :

      1. Récupérer du contenu avec l’API.
      2. Dans la réponse JSON, déterminez ce qui doit être utilisé pour le rendu dans l’application cliente.
