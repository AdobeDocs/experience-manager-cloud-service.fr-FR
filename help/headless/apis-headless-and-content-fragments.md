---
title: AEM API pour la diffusion structurée de contenu et la gestion des fragments de contenu
description: Découvrez les API disponibles pour la diffusion de contenu structuré et la gestion des fragments de contenu
feature: Headless, Content Fragments, Edge Delivery Services
role: Admin, Developer
exl-id: 95aecd30-566a-42a9-b97a-7efe45fd389c
source-git-commit: d9db32110e1e0aaa5bdc20bd6b4bff6da6a3a3a3
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 41%

---

# API AEM pour la diffusion et la gestion de contenu structuré {#aem-apis-structured-content-delivery-and-management}

Adobe Experience Manager (AEM) as a Cloud Service propose plusieurs API pour la diffusion de contenu structuré à partir de fragments de contenu et la gestion de fragments de contenu. Voir les pages individuelles pour plus de détails sur les API spécifiques.

* [AEM diffusion de fragments de contenu avec OpenAPI](/help/headless/aem-content-fragment-delivery-with-openapi.md)
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

<!--
## JSON vs HTML {#json-vs-HTML}

The content delivery format used is driven by frontend implementation. Unstructured content/HTML for full-stack implementations, structured content/JSON for headless implementations, or a combination of both in hybrid implementations. 

Key considerations include:

* Definition
  * JSON (JavaScript Object Notation) - used to represent, access and process structured data. 
  * HTML (HyperText Markup Language) - a markup language of tags and elements in a hierarchical structure.
* Primary Purpose
  * JSON is often used for transferring structure content between the server and client app.
  * HTML is the standard markup language for creating and rendering web pages in a browser.
-->

## REST par rapport à GraphQL {#rest-vs-graphql}

L’API utilisée est une décision qui appartient aux développeurs, car AEM prend en charge les deux.

De nombreuses comparaisons sont disponibles en ligne, mais voici quelques points forts et avantages de REST :

* Simplicité

   * Les développeurs sont (souvent) familiarisés avec HTTP et REST. Selon le [rapport](https://www.postman.com/state-of-api/) Postman State of the APIs, un pourcentage élevé de développeurs utilisent REST.

   * Avec la simplicité vient la familiarité. Avec REST, il n’y a pas de questions organisationnelles de savoir qui possède les requêtes et qui possède l’application, alors que ces questions peuvent se poser avec GraphQL.

   * La familiarité (généralement) s’accompagne d’une vaste communauté et d’un vaste paysage d’outillage. Pas un inconvénient inhérent à GraphQL, mais susceptible d’être plus large et plus profond pour REST.

   * L’approche plus simple peut également faciliter la mise en œuvre de la sécurité. Avec REST, le filtrage pour déterminer le contenu à rendre se produit dans l’application cliente. Avec GraphQL, cela se produit dans une requête basée sur un schéma entre le client et le serveur.

* Flexibilité

   * Avec REST, le développeur peut `GET` n’importe quelle ressource. Avec GraphQL, elles sont limitées aux ressources définies dans un schéma.

* Mise en cache

   * Les réponses JSON aux requêtes REST `GET` peuvent intrinsèquement être mises en cache. Les requêtes GraphQL `POST` ne peuvent pas être mises en cache, sauf si elles sont ainsi effectuées, par exemple à l’aide de AEM requêtes persistantes stockées sur le serveur et demandées avec des requêtes de type `GET`REST.

Les avantages de GraphQL incluent :

* Efficacité de la diffusion de contenu

   * Cible d’action

      * Avec GraphQL, les applications clientes peuvent demander le contenu exact dont elles ont besoin pour le rendu - et pas plus. Cette approche empêche la diffusion excessive de contenu, avec des charges utiles de contenu excessives et une consommation inutile de bande passante.

   * Point de terminaison unique

      * Alors que dans REST, chaque requête API est un point de terminaison, dans GraphQL, il n’y a qu’un seul point de terminaison commun, et différentes demandes de contenu sont exprimées sous forme de requêtes utilisant ce point de terminaison commun.

* Prototypage rapide

   * Avec GraphQL, il s’agit d’un processus en une étape, regroupé dans la requête GraphQL, qui peut faciliter le prototypage. REST, quant à lui, est un processus en 2 étapes :

      1. Récupérer le contenu avec l’API.
      2. Dans la réponse JSON, déterminez ce qu’il faut utiliser pour le rendu dans l’application cliente.
