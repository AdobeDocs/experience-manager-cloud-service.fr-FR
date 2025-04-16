---
title: Diffusion de fragments de contenu AEM avec OpenAPI
description: En savoir plus sur la diffusion de fragments de contenu AEM avec OpenAPI
feature: Headless, Content Fragments, Edge Delivery Services
role: Admin, Developer
source-git-commit: d9db32110e1e0aaa5bdc20bd6b4bff6da6a3a3a3
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# Diffusion de fragments de contenu AEM avec OpenAPI {#aem-content-fragment-delivery-with-openapi}

>[!IMPORTANT]
>
>Cette API est disponible via le programme des utilisateurs et utilisatrices précoces.
>
>Pour consulter le statut et savoir comment appliquer la version si vous êtes intéressé, consultez les [Notes de mise à jour](/help/release-notes/release-notes-cloud/release-notes-current.md).

Dans Adobe Experience Manager (AEM) as a Cloud Service, l’OpenAPI AEM pour la diffusion de fragments de contenu :

* est une API HTTP REST sur [AEM Edge Delivery Services](/help/edge/overview.md), conçue pour diffuser du contenu structuré à partir de fragments de contenu au format JSON
* offre une intégration CDN moderne qui permet d’invalider le contenu actif
* se concentre sur la diffusion de contenu (performances, évolutivité, intégration CDN, contrôle et sortie JSON optimisés)
* inclut la possibilité d’hydrater du code JSON pour les fragments et les ressources référencés

Cette API :

* est le successeur de [ Prise en charge des fragments de contenu dans l’API HTTP AEM Assets ](/help/assets/content-fragments/assets-api-content-fragments.md)

* complète les [API ouvertes de fragments de contenu et de modèles de fragments de contenu](/help/headless/content-fragment-openapis.md), qui vous permettent de gérer les fragments de contenu et les modèles de fragment de contenu (CRUD)

* est une alternative HTTP REST à l’API AEM GraphQL [à utiliser avec des fragments de contenu](/help/headless/graphql-api/content-fragments.md)

Pour consulter la documentation complète, voir [Schémas d’API AEM Sites - API de diffusion de fragments de contenu (2024.07-stade expérimental)](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/sites/delivery/).

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
