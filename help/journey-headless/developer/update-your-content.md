---
title: Comment mettre à jour votre contenu à l’aide des API AEM
description: Dans cette partie du Parcours de développement découplé AEM, découvrez comment utiliser les API disponibles pour accéder au contenu de vos fragments de contenu et le mettre à jour.
exl-id: 84120856-fd1d-40f7-8df4-73d4cdfcc43b
solution: Experience Manager
feature: Headless, Content Fragments, GraphQL API
role: Admin, Architect, Developer
source-git-commit: d8e4fdc4f79e40a43a6845ab083dc231444b9c99
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 33%

---

# Comment mettre à jour votre contenu à l’aide des API AEM {#update-your-content}

Dans cette partie du [Parcours de développement découplé AEM](overview.md), découvrez comment utiliser les API disponibles pour accéder au contenu de vos fragments de contenu et le mettre à jour.

## Un peu d’histoire... {#story-so-far}

Dans le document précédent du parcours découplé AEM, [Comment accéder à votre contenu à l’aide des API de diffusion AEM](access-your-content.md), vous avez appris à accéder à votre contenu en mode découplé via l’API AEM GraphQL et vous devriez maintenant :

* Connaître GraphQL dans ses grandes lignes.
* Comprendre le fonctionnement de l’API AEM GraphQL.
* Connaître quelques exemples pratiques de requêtes.

Cet article s’appuie sur ces principes de base afin que vous compreniez comment mettre à jour votre contenu découplé existant dans AEM à l’aide des API disponibles.

## Objectif {#objective}

* **Audience** : Niveau avancé
* **Objectif** : découvrez les API disponibles pour accéder au contenu de vos fragments de contenu et le mettre à jour.

## API AEM à utiliser avec des fragments de contenu {#aem-apis-for-use-with-content-fragments}

Adobe Experience Manager (AEM) as a Cloud Service propose plusieurs API pour la diffusion de contenu structuré à partir de fragments de contenu et la gestion de fragments de contenu. Voir les pages individuelles pour plus de détails sur les API spécifiques.

* OpenAPI REST AEM pour la diffusion de fragments de contenu
   * Cette API crée des réponses JSON pour diffuser du contenu structuré à partir de fragments de contenu dans AEM.
   * Il utilise un chemin d’accès vers un fragment de contenu comme point d’entrée.
   * Cette API est basée sur REST.
   * Il est optimisé pour la diffusion de contenu, y compris l’intégration du réseau CDN.
* API AEM GraphQL pour la diffusion de fragments de contenu
   * Cette API est basée sur un schéma. Les schémas d’API sont représentés par des modèles de fragment de contenu, qui définissent la structure du contenu.
   * Cette API est basée sur GraphQL.
* Fragments de contenu et modèles de fragment de contenu OpenAPI
   * Ces API sont destinées à la gestion de contenu structuré.
   * Les opérateurs GET respectifs ne sont pas optimisés pour la diffusion de contenu.
   * Cette API est basée sur REST.
* Prise en charge des fragments de contenu dans l’API HTTP AEM Assets
   * API d’origine pour la sortie JSON pour la diffusion de contenu structuré dans AEM.
      * Bien que robuste et éprouvée, cette API ne fournit pas de sortie JSON *entièrement hydratée*. Les références ne sont générées que comme chemins d’accès, ce qui nécessite des requêtes d’API secondaires pour récupérer du contenu supplémentaire.
   * L’API HTTP Assets peut également être utilisée pour gérer les fragments de contenu et les modèles de fragment de contenu (CRUD).
   * Cette API est basée sur REST.
   * La prise en charge des fragments de contenu dans l’API HTTP Assets sera abandonnée à l’avenir car elle sera remplacée par l’API REST JSON Edge Delivery Services. Le calendrier n&#39;a pas encore été fixé.

## Prochaines étapes {#whats-next}

Maintenant que vous avez terminé cette partie du parcours de développement découplé AEM, vous devriez pouvoir :

* Découvrez les API AEM disponibles.
* Comprendre comment les fragments de contenu sont pris en charge dans ces API.

Continuez votre parcours AEM découplé en consultant ensuite le document. [Tout assembler - Votre application et votre contenu dans AEM découplé](put-it-all-together.md) où vous vous familiariserez avec les principes de base de l’architecture d’AEM et les outils dont vous avez besoin pour assembler votre application.

## Ressources supplémentaires {#additional-resources}

* [API Adobe Experience Manager as a Cloud Service](https://developer.adobe.com/experience-cloud/experience-manager-apis/)
* [API AEM pour la diffusion et la gestion de contenu structuré](/help/headless/apis-headless-and-content-fragments.md)
* [OpenAPI REST AEM pour la diffusion de fragments de contenu](/help/headless/aem-rest-openapi-content-fragment-delivery.md)
* [API AEM GraphQL pour la diffusion de fragments de contenu](/help/headless/graphql-api/content-fragments.md)
* [Fragments de contenu et modèles de fragment de contenu OpenAPI](/help/headless/content-fragment-openapis.md)
* [Prise en charge des fragments de contenu dans l’API HTTP AEM Assets](/help/assets/content-fragments/assets-api-content-fragments.md)
* [Utilisation de fragments de contenu](/help/sites-cloud/administering/content-fragments/overview.md)
* [AEM Core Components](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr)
* [CORS/AEM expliqué](https://helpx.adobe.com/fr/experience-manager/kt/platform-repository/using/cors-security-article-understand.html)
* [Vidéo – Développement pour CORS et AEM](https://helpx.adobe.com/fr/experience-manager/kt/platform-repository/using/cors-security-technical-video-develop.html)
* [Présentation d’AEM en tant que CMS découplé](/help/headless/introduction.md)
* [Portail de développement d’AEM ](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=fr)
* [Tutoriels pour le découplage dans AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=fr)
