---
title: API AEM pour la diffusion de contenu structurée et la gestion des fragments de contenu
description: En savoir plus sur les API disponibles pour la diffusion de contenu structurée et la gestion des fragments de contenu
feature: Headless, Content Fragments, Edge Delivery Services
role: Admin, Developer
source-git-commit: 21599676916068f3529976410a93951b02f750b0
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 0%

---


# API AEM pour la diffusion et la gestion de contenu structurées {#aem-apis-structured-content-delivery-and-management}

Adobe Experience Manager (AEM) as a Cloud Service offre plusieurs API pour la diffusion de contenu structuré à partir de fragments de contenu et de la gestion des fragments de contenu. Consultez les pages individuelles pour plus d’informations sur les API spécifiques.

* [AEM REST OpenAPI pour la diffusion de fragments de contenu](/help/headless/aem-rest-openapi-content-fragment-delivery.md)
   * Cette API crée des réponses JSON pour la diffusion de contenu structuré à partir de fragments de contenu dans AEM.
   * Il utilise un chemin d’accès à un fragment de contenu comme point de terminaison.
   * Cette API est basée sur REST.
   * Il est optimisé pour la diffusion de contenu, y compris l’intégration CDN.
* [API GraphQL AEM pour la diffusion de fragments de contenu](/help/headless/graphql-api/content-fragments.md)
   * Cette API est basée sur des schémas. Les schémas d’API sont représentés par des modèles de fragment de contenu, qui définissent la structure de contenu.
   * Cette API est basée sur GraphQL.
* [API ouvertes de fragments de contenu et de modèles de fragments de contenu](/help/headless/content-fragment-openapis.md)
   * Ces API sont destinées à la gestion de contenu structuré.
   * Les opérateurs de GET respectifs ne sont pas optimisés pour la diffusion de contenu.
   * Cette API est basée sur REST.
* [Prise en charge des fragments de contenu dans l’API HTTP AEM Assets](/help/assets/content-fragments/assets-api-content-fragments.md)
   * API d’origine pour la sortie JSON pour la diffusion de contenu structuré dans AEM.
      * Bien qu’elle soit robuste et prouvée, cette API ne fournit pas de sortie JSON *entièrement hydratée*. Les références ne sont générées que sous forme de chemins d’accès, ce qui nécessite des requêtes d’API secondaires pour récupérer du contenu supplémentaire.
   * L’API HTTP Assets peut également être utilisée pour gérer les fragments de contenu et les modèles de fragments de contenu (CRUD).
   * Cette API est basée sur REST.
   * La prise en charge des fragments de contenu dans l’API HTTP Assets sera abandonnée à l’avenir, car elle sera remplacée par l’API REST JSON Edge Delivery Services. Le calendrier n&#39;a pas encore été fixé.

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

## REST et GraphQL {#rest-vs-graphql}

L’API utilisée est une décision pour les développeurs. AEM prend en charge les deux.

De nombreuses comparaisons sont disponibles en ligne, mais quelques points forts et avantages de REST sont les suivants :

* Simplicité

   * Les développeurs sont (souvent) familiarisés avec HTTP et REST. Selon le rapport [Postman State of the APIs](https://www.postman.com/state-of-api/), un pourcentage élevé de développeurs utilisent REST.

   * Avec la simplicité vient la familiarité. Avec REST, il n’existe aucune question d’organisation concernant le propriétaire des requêtes et le propriétaire de l’application, alors que ces questions peuvent se poser avec GraphQL.

   * La familiarité (typiquement) s’accompagne d’une vaste communauté et d’un vaste paysage d’outils. Pas un inconvénient inhérent à GraphQL, mais susceptible d’être plus large et plus profond pour REST.

   * L’approche plus simple peut également faciliter la mise en oeuvre de la sécurité. Avec REST, le filtrage permettant de déterminer le contenu dont le rendu doit être effectué s’effectue dans l’application cliente. Avec GraphQL, cela se produit dans une requête basée sur un schéma entre le client et le serveur.

* Flexibilité

   * Avec REST, le développeur peut `GET` n’importe quelle ressource. Avec GraphQL, elles sont limitées aux ressources définies dans un schéma.

* Mise en cache

   * Les réponses JSON aux requêtes REST `GET` peuvent par nature être mises en cache. Les requêtes GraphQL `POST` ne peuvent pas être mises en cache, sauf si elles le sont ; par exemple, en utilisant AEM requêtes persistantes stockées sur le serveur et demandées avec des requêtes de type REST `GET`.

Les avantages de GraphQL sont les suivants :

* Efficacité de la diffusion de contenu

   * Cible d’action

      * Avec GraphQL, les applications clientes peuvent demander le contenu exact dont elles ont besoin pour le rendu - et pas plus. Cette approche empêche la sur-diffusion du contenu, avec des charges de contenu excessives et une consommation de bande passante inutile.

   * Point d’entrée unique

      * Bien que dans REST, chaque requête d’API soit un point de terminaison, dans GraphQL, il n’y a qu’un seul point de terminaison commun et les différentes requêtes de contenu sont exprimées sous la forme de requêtes utilisant ce point de terminaison commun.

* Prototypage rapide

   * Avec GraphQL, il s’agit d’un processus à une étape, rassemblé dans la requête GraphQL, qui peut faciliter le prototypage. REST, en revanche, est un processus en 2 étapes :

      1. Récupérez du contenu avec l’API.
      2. Dans la réponse JSON, déterminez les éléments à utiliser pour le rendu dans l’application cliente.
