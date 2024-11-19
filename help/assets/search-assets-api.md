---
title: Recherche dans l’API Assets
description: Découvrez comment utiliser l’API Search Assets.
role: User
exl-id: 0c52e793-4c33-4230-b4f2-27296dd9e4b3
source-git-commit: ed7331647ea2227e6047e42e21444b743ee5ce6d
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 4%

---

# Recherche dans l’API Assets {#search-assets-api}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [Bonnes pratiques relatives aux métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Fonctionnalités Dynamic Media avec OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation de développement pour AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

>[!AVAILABILITY]
>
>Le guide des fonctionnalités de Dynamic Media avec OpenAPI est désormais disponible au format PDF. Téléchargez l’intégralité du guide et utilisez l’assistant Adobe Acrobat AI pour répondre à vos requêtes.
>
>[!BADGE Dynamic Media avec OpenAPI Feature PDF ]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

Toutes les [ressources approuvées](approve-assets.md) disponibles dans le référentiel de ressources Experience Manager peuvent être recherchées, puis diffusées aux applications intégrées en aval à l’aide d’une URL de diffusion.

La recherche des ressources approuvées appropriées à partir du référentiel Experience Manager constitue la première étape de la diffusion des ressources à l’aide de l’URL de diffusion. La réponse à la requête de recherche comprend un tableau de documents JSON correspondant aux ressources qui répondent aux critères de recherche. Chaque document JSON est identifié à l’aide d’un champ `id`, qui est utilisé pour composer la demande de remise de ressources.

![Présentation du protocole de chargement binaire direct](assets/search-assets-api-overview.png)

Vous pouvez définir des propriétés dans la requête API Search Assets pour activer les fonctionnalités suivantes :

* **Recherche de texte intégral** : utilisez la requête `match` pour définir le texte à rechercher.  Vous pouvez également utiliser des opérateurs dans la requête `match` pour filtrer les résultats.

* **Appliquer les filtres** : utilisez la requête `term` pour filtrer davantage les résultats en définissant une `key` et une ou plusieurs valeurs. `key` identifie le champ dont la valeur doit correspondre et `value` représente ce à quoi la correspondance doit être effectuée. De même, vous pouvez utiliser la requête `range` pour définir une plage pour un champ à l’aide des propriétés Supérieur à (gt), Supérieur ou égal à (gte), Inférieur à (lt) et Inférieur ou égal à (lte).

* **Trier les résultats** : utilisez la propriété `OrderBy` pour trier les résultats de recherche en fonction d’un ou de plusieurs champs. Vous pouvez trier les résultats par ordre croissant ou décroissant.

* **Pagination** : utilisez les propriétés `limit` et `cursor` pour définir les propriétés de pagination dans une requête d’API de recherche. La propriété `limit` définit le nombre maximal d’éléments à récupérer dans une réponse API. La propriété `cursor` facilite la récupération du point de départ pour l’ensemble suivant de ressources définies dans la propriété `limit`. Par exemple, si vous définissez `50` comme limite dans la requête API, vous pouvez utiliser la propriété `cursor` pour démarrer et récupérer les 50 éléments suivants à l’aide de la requête API suivante.

## Point d’entrée de l’API de recherche de ressources {#search-assets-api-endpoint}

Le point de terminaison d’une requête de l’API Assets de recherche doit être au format suivant :
`https://delivery-pXXXX-eYYYY.adobeaemcloud.com/adobe/assets/search`

Le domaine de diffusion est similaire en termes de structure au domaine de l’environnement de création Experience Manager. La seule différence est de remplacer le terme `author` par `delivery`.

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

Pour appeler l’API de recherche, un jeton IMS est nécessaire pour définir dans les détails `Authorization`. Le jeton IMS est récupéré à partir d’un compte technique. Voir [Récupération des informations d’identification AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#fetch-the-aem-as-a-cloud-service-credentials) pour créer un compte technique. Voir [Génération du jeton d’accès](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token) pour générer le jeton IMS et l’utiliser de manière appropriée dans l’en-tête de requête de l’API de ressources de recherche.

Pour afficher des exemples de requête, des exemples de réponse et des codes de réponse, reportez-vous à la section [API Search Assets](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/search).
