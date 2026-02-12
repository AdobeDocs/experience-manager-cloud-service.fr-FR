---
title: Diffusion de fragments de contenu AEM avec OpenAPI
description: En savoir plus sur la diffusion de fragments de contenu AEM avec OpenAPI
feature: Headless, Content Fragments, Edge Delivery Services
role: Admin, Developer
exl-id: b298db37-1033-4849-bc12-7db29fb77777
source-git-commit: 73bfeb19eebe104a772d1c420fe6471fea3e1225
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 2%

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

>[!IMPORTANT]
>
>Pour activer la diffusion de fragments de contenu avec OpenAPI sur AEM as a Cloud Service, vérifiez qu’elle n’est pas déjà activée, puis envoyez un ticket de support Adobe avec le titre **Activer la diffusion de fragments de contenu avec OpenAPI** et en spécifiant :
>
>* le programme Cloud Service et les identifiants d’environnement ;
>* détails du cas d’utilisation que vous souhaitez résoudre avec l’OpenAPI de diffusion de fragments de contenu.
>* détails de tous les contacts auxquels Adobe doit répondre et qui doivent être tenus informés de la demande et du projet (si nécessaire)

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

La diffusion de fragments de contenu avec OpenAPI prend en charge l’invalidation active du cache CDN. Cela signifie que chaque fois que le contenu est mis à jour ou publié, les réponses OpenAPI JSON correspondantes sont automatiquement invalidées, par le biais d’une requête de purge réversible envoyée à Fastly. Cela vous permet de voir les modifications répercutées dans la sortie JSON avant que l’âge réel du cache du réseau CDN (`s-maxage`) ne soit atteint.

## Disponibilité {#availability}

La diffusion de fragments de contenu avec OpenAPI est disponible sur les niveaux Aperçu et Publication. L’API OpenAPI diffuse des fragments de contenu au format JSON pour la prévisualisation et la diffusion en direct.

Pour obtenir un aperçu, la diffusion de fragments de contenu avec OpenAPI peut :

* Publier dans l’aperçu
* Activer l’accès à l’aperçu avec la liste autorisée IP
* obtenir l’URL d’aperçu

## CORS {#cors}

[Origines autorisées CORS](/help/headless/deployment/cross-origin-resource-sharing.md) définissez les origines qui peuvent appeler l’API.

Les origines autorisées CORS définies du côté de la configuration du Dispatcher, spécifiquement pour GraphQL, ne sont pas prises en compte par cette API.

## Limites de taux d’API {#api-rate-limits}

L’API autorise de nouvelles requêtes à raison de 200 requêtes maximum par seconde et par environnement.

Une fois cette limite dépassée, l’API commence à envoyer des réponses d’erreur [429](https://www.rfc-editor.org/rfc/rfc6585#section-4). Ces erreurs doivent être gérées par toutes les applications clientes et les requêtes ayant échoué doivent être relancées à la suite d’une reprise exponentielle. La réponse HTTP s’accompagne d’un en-tête spécifique, `Retry-After`, qui indique au client combien de temps il doit attendre avant de renvoyer la requête.

## Requêtes authentifiées {#authenticated-requests}

La prise en charge des requêtes authentifiées peut être mise en œuvre avec la clé Edge [CDN AEM](/help/implementing/dispatcher/cdn-credentials-authentication.md). L’utilisation de la clé Edge du réseau CDN AEM vous permet de vous fier au réseau CDN AEM et de vous assurer que seules des requêtes spécifiques peuvent accéder à l’API, en fonction de l’en-tête de clé Edge fourni.

>[!NOTE]
>
>L’autorisation basée sur les listes ACL spécifiques au référentiel n’est actuellement pas prise en charge.

<!-- 
## Limitations {#limitations}
-->
