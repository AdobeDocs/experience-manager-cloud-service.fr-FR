---
title: API AEM pour la diffusion de contenu structuré et la gestion des fragments de contenu
description: Découvrez les API disponibles pour la diffusion de contenu structuré et la gestion des fragments de contenu
feature: Headless, Content Fragments, Edge Delivery Services
role: Admin, Developer
exl-id: 95aecd30-566a-42a9-b97a-7efe45fd389c
source-git-commit: 243adc6f6428cea23c04ca788bd8ad0bda7e4501
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 28%

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

>[!NOTE]
>
>[La prise en charge des fragments de contenu dans l’API HTTP Assets](/help/assets/content-fragments/assets-api-content-fragments.md) est désormais [obsolète](/help/release-notes/deprecated-removed-features.md). Elle a été remplacée par [Diffusion de fragments de contenu avec OpenAPI](/help/headless/aem-content-fragment-delivery-with-openapi.md) ainsi que [Fragments de contenu et Gestion des modèles de fragments de contenu OpenAPI](/help/headless/content-fragment-openapis.md).

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
