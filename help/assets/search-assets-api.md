---
title: Recherche dans l’API Assets
description: Découvrez comment utiliser l’API Search Assets.
role: User
source-git-commit: 3e2fe458460fe8ec4c1dd12152c1134bfb9ca62b
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 1%

---

# Recherche dans l’API Assets {#search-assets-api}

Tous [ressources approuvées](approve-assets.md) disponibles dans le référentiel de ressources Experience Manager peuvent être recherchées, puis diffusées aux applications intégrées en aval à l’aide d’une URL de diffusion.

La recherche des ressources approuvées appropriées à partir du référentiel Experience Manager constitue la première étape de la diffusion des ressources à l’aide de l’URL de diffusion. La réponse à la requête de recherche comprend un tableau de documents JSON correspondant aux ressources qui répondent aux critères de recherche. Chaque document JSON est identifié à l’aide d’une `id` qui sert à composer la demande de diffusion de la ressource.

![Présentation du protocole de chargement binaire direct](assets/search-assets-api-overview.png)

Vous pouvez définir des propriétés dans la requête API Search Assets pour activer les fonctionnalités suivantes :

* **Recherche de texte intégral**: utilisez la variable `match` requête pour définir le texte à rechercher.  Vous pouvez également utiliser des opérateurs dans la variable `match` pour filtrer les résultats.

* **Appliquer les filtres**: utilisez la variable `term` requête pour filtrer davantage les résultats en définissant une `key` et une ou plusieurs valeurs. `key` identifie le champ dont la valeur doit correspondre et `value` représente ce à quoi faire correspondre. De même, vous pouvez utiliser la variable `range` pour définir une plage pour un champ à l’aide des propriétés Supérieur à (gt), Supérieur ou égal à (gte), Inférieur à (lt) et Inférieur ou égal à (lte).

* **Tri des résultats**: utilisez la variable `OrderBy` pour trier les résultats de la recherche en fonction d’un ou de plusieurs champs. Vous pouvez trier les résultats par ordre croissant ou décroissant.

* **Pagination**: utilisez la variable `limit` et `cursor` propriétés pour définir les propriétés de pagination dans une requête d’API de recherche. `limit` définit le nombre maximal d’éléments à récupérer dans une réponse API. `cursor` facilite la récupération du point de départ pour l’ensemble suivant de ressources défini dans la propriété `limit` . Par exemple, si vous définissez `50` comme limite dans la requête API, vous pouvez utiliser la variable `cursor` pour démarrer et récupérer les 50 éléments suivants à l’aide de la requête API suivante.

## Point d’entrée de l’API de recherche de ressources {#search-assets-api-endpoint}

Le point de terminaison d’une requête de l’API Assets de recherche doit être au format suivant :
`https://delivery-pXXXX-eYYYY.adobeaemcloud.com/adobe/assets/search`

Le domaine de diffusion est similaire en termes de structure au domaine de l’environnement de création Experience Manager. La seule différence est de remplacer le terme `author` avec `delivery`.

`pXXXX` fait référence à l’ID de programme

`eYYYY` fait référence à l’ID d’environnement

## Méthode de requête de l’API de recherche de ressources {#search-assets-api-request-method}

POST

## En-tête de l’API de recherche Assets {#search-assets-api-header}

Vous devez fournir les détails suivants lors de la définition d’un en-tête dans l’API de recherche de ressources :

```java
headers: {
      'Content-Type': 'application/json',
      'X-Adobe-Accept-Experimental': '1',
      Authorization: 'Bearer <YOUR_JWT_HERE>',
      'X-Api-Key': 'YOUR_API_KEY_HERE'
    },
```

Pour appeler l’API de recherche, un jeton IMS doit être défini dans la variable `Authorization` détails. Le jeton IMS est récupéré à partir d’un compte technique. Voir [Récupération des informations d’identification AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#fetch-the-aem-as-a-cloud-service-credentials) pour créer un compte technique. Voir [Génération du jeton d’accès](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token) pour générer le jeton IMS et l’utiliser de manière appropriée dans l’en-tête de requête de l’API de recherche de ressources.

Pour consulter des exemples de requête, des exemples de réponse et des codes de réponse, voir [Recherche dans l’API Assets](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/search).
