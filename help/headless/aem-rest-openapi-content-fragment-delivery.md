---
title: AEM API REST Open pour la diffusion de fragments de contenu
description: En savoir plus sur l’AEM REST OpenAPI pour la diffusion de fragments de contenu
feature: Headless, Content Fragments, Edge Delivery Services
role: Admin, Developer
source-git-commit: d98aa9d206486022d465ca19c8888088562d56c3
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---


# AEM API REST Open pour la diffusion de fragments de contenu {#aem-rest-openapi-for-content-fragment-delivery}

>[!IMPORTANT]
>
>Cette API est disponible dans le cadre du Programme des Adopteurs Anticipés.
>
>Pour connaître l’état et savoir comment vous appliquer si vous le souhaitez, consultez les [notes de mise à jour](/help/release-notes/release-notes-cloud/release-notes-current.md).

As a Cloud Service Adobe Experience Manager (AEM), l’API REST OpenAPI AEM pour la diffusion de fragments de contenu :

* est une API HTTP REST sur [AEM Edge Delivery Services](/help/edge/overview.md), conçue pour diffuser du contenu structuré à partir de fragments de contenu au format JSON.
* offre une intégration CDN moderne qui permet l’invalidation du contenu actif.
* se concentre sur la diffusion de contenu (performances, évolutivité, intégration CDN, contrôle JSON et sortie optimisés).
* inclut la possibilité d’hydrater JSON pour les fragments et les ressources référencés ;

Cette API :

* succède à la [prise en charge des fragments de contenu dans l’API HTTP AEM Assets](/help/assets/content-fragments/assets-api-content-fragments.md)

* complète les [ API OpenFragments de contenu et modèles de fragment de contenu ](/help/headless/content-fragment-openapis.md), qui vous permettent de gérer les fragments de contenu et les modèles de fragment de contenu (CRUD).

* est une alternative HTTP REST à l’API GraphQL [AEM à utiliser avec des fragments de contenu](/help/headless/graphql-api/content-fragments.md)

Pour obtenir une documentation complète, reportez-vous à la section [AEM Sites API Schemas - Content Fragments Delivery API (2024.07-expérimental)](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/sites/delivery/).

>[!NOTE]
>
>Voir [AEM API pour la diffusion et la gestion de contenu structurées](/help/headless/apis-headless-and-content-fragments.md) pour un aperçu des différentes API disponibles et une comparaison de certains des concepts impliqués.

## Mise en cache {#caching}

AEM s’intègre rapidement au réseau de diffusion de contenu AEM. Cela signifie que les réponses JSON diffusées sur le niveau Publication sont mises en cache au niveau Fastly.

Les réponses sont ensuite mises en cache, en fonction des en-têtes de mise en cache prédéfinis (impossible à configurer) :

* Les réponses sont mises en cache pendant 5 minutes dans le cache du navigateur/client.
   * `max-age`=`300`
* Les réponses sont mises en cache pendant 1 heure sur le cache CDN
   * `s-maxage`=`3600`
* Le contenu obsolète peut être diffusé lors de la revalidation de nouvelles requêtes pendant une durée maximale d’une heure
   * `stale-while-revalidate`=`3600`
* Le contenu obsolète peut être diffusé, par erreur, pendant une journée au maximum.
   * `stale-on-error`=`86400`

AEM est également fourni avec l’invalidation active du cache CDN. Cela signifie que chaque fois que du contenu est mis à jour ou publié, les réponses OpenAPI JSON correspondantes sont automatiquement invalidées, via une requête de purge douce à Fastly. Cela vous permet de voir les modifications reflétées dans la sortie JSON, avant que l’âge réel du cache CDN (`s-maxage`) ne soit atteint.