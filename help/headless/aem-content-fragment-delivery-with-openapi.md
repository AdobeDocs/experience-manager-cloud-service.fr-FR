---
title: Diffusion de fragments de contenu AEM avec OpenAPI
description: En savoir plus sur la diffusion de fragments de contenu AEM avec OpenAPI
feature: Headless, Content Fragments, Edge Delivery Services
role: Admin, Developer
exl-id: b298db37-1033-4849-bc12-7db29fb77777
source-git-commit: 7f7ed3adcbd01f688f48f3ba4a0c25293b8b1551
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 4%

---

# Diffusion de fragments de contenu AEM avec OpenAPI {#aem-content-fragment-delivery-with-openapi}

Dans Adobe Experience Manager (AEM) as a Cloud Service, l’OpenAPI AEM pour la diffusion de fragments de contenu :

* est une OpenAPI optimisée pour la diffusion en direct de fragments de contenu AEM au format JSON
* offre une intégration CDN moderne qui permet d’invalider le contenu actif
* se concentre sur la diffusion de contenu (performances, évolutivité, intégration CDN, contrôle et sortie JSON optimisés)
* inclut la possibilité d’hydrater du code JSON pour les fragments et les ressources référencés

Cette API :

* est le successeur de [ Prise en charge des fragments de contenu dans l’API HTTP AEM Assets ](/help/assets/content-fragments/assets-api-content-fragments.md)

* complète les [API ouvertes de fragments de contenu et de modèles de fragments de contenu](/help/headless/content-fragment-openapis.md), qui vous permettent de gérer les fragments de contenu et les modèles de fragment de contenu (CRUD)

* est une alternative HTTP REST à l’API AEM GraphQL [à utiliser avec des fragments de contenu](/help/headless/graphql-api/content-fragments.md)

Pour consulter la documentation complète, voir [Diffusion de fragments de contenu AEM avec OpenAPI](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/contentfragments/delivery/).

>[!NOTE]
>
>Consultez [API AEM pour la diffusion et la gestion de contenu structuré](/help/headless/apis-headless-and-content-fragments.md) pour un aperçu des différentes API disponibles et une comparaison de certains des concepts impliqués.

## Mise en cache {#caching}

AEM s’intègre au réseau CDN d’AEM rapidement. Cela signifie que les réponses JSON diffusées au niveau de publication sont mises en cache au niveau Fastly .

Les réponses sont ensuite mises en cache, en fonction des en-têtes de mise en cache prédéfinis (ne peuvent pas être configurés) :

* Les réponses sont mises en cache pendant 5 minutes dans le cache du navigateur/client
   * `max-age`=`300`
* Les réponses sont mises en cache pendant 1 heure sur le cache CDN.
   * `s-maxage`=`3600`
* Le contenu obsolète peut être diffusé lors de la revalidation des nouvelles requêtes pendant une heure maximum
   * `stale-while-revalidate`=`3600`
* Le contenu obsolète peut être diffusé, par erreur, pendant 1 jour au maximum
   * `stale-on-error`=`86400`

AEM est également fourni avec l’invalidation active du cache du réseau CDN. Cela signifie que chaque fois que le contenu est mis à jour ou publié, les réponses OpenAPI JSON correspondantes sont automatiquement invalidées, par le biais d’une requête de purge réversible envoyée à Fastly. Cela vous permet de voir les modifications répercutées dans la sortie JSON avant que l’âge réel du cache du réseau CDN (`s-maxage`) ne soit atteint.
