---
title: Rechercher dans l’API Assets
description: Découvrez comment utiliser l’API Search Assets.
role: User
exl-id: 0c52e793-4c33-4230-b4f2-27296dd9e4b3
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 11%

---

# Rechercher dans l’API Assets {#search-assets-api}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime et Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouvelle</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Intégration d’AEM Assets à Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Extensibilité de l’interface utilisateur</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Activation de Dynamic Media Prime et Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Bonnes pratiques de recherche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Bonnes pratiques relatives aux métadonnées</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Hub de contenus</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Fonctionnalités Dynamic Media avec OpenAPI</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Documentation de développement pour AEM Assets</b></a>
        </td>
    </tr>
</table>

>[!AVAILABILITY]
>
>Le guide de Dynamic Media avec fonctionnalités OpenAPI est désormais disponible au format PDF. Téléchargez l’intégralité du guide et utilisez l’assistant IA Adobe Acrobat pour répondre à vos requêtes.
>
>[!BADGE Guide PDF de Dynamic Media avec fonctionnalités OpenAPI]{type=Informative url="https://helpx.adobe.com/content/dam/help/fr/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

Toutes les [ressources approuvées](approve-assets.md) disponibles dans le référentiel de ressources d’Experience Manager peuvent être recherchées, puis diffusées vers les applications intégrées en aval à l’aide d’une URL de diffusion.

La recherche des ressources approuvées appropriées dans le référentiel Experience Manager est la première étape de la diffusion des ressources à l’aide de l’URL de diffusion. La réponse à la requête de recherche comprend un tableau de documents JSON correspondant aux ressources qui répondaient aux critères de recherche. Chaque document JSON est identifié à l’aide d’un champ `id`, qui est utilisé pour composer la demande de diffusion de ressources.

![Présentation du protocole de chargement binaire direct](assets/search-assets-api-overview.png)

Vous pouvez définir des propriétés dans la requête de l’API Search Assets pour activer les fonctionnalités suivantes :

* **Recherche en texte intégral** : utilisez la requête `match` pour définir le texte à rechercher.  Vous pouvez également utiliser des opérateurs dans la requête `match` pour filtrer les résultats.

* **Appliquer des filtres** : utilisez la requête `term` pour filtrer davantage les résultats en définissant un `key` et une ou plusieurs valeurs. `key` identifie le champ dont la valeur doit être mise en correspondance et `value` représente ce en quoi il faut mettre en correspondance. De même, vous pouvez utiliser la requête `range` pour définir une plage pour un champ à l’aide des propriétés Supérieur à (gt), Supérieur ou égal à (gte), Inférieur à (lt) et Inférieur ou égal à (lte).

* **Trier les résultats** : utilisez la propriété `OrderBy` pour trier les résultats de recherche en fonction d’un ou de plusieurs champs. Vous pouvez trier les résultats par ordre croissant ou décroissant.

* **Pagination** : utilisez les propriétés `limit` et `cursor` pour définir les propriétés de pagination dans une requête de l’API de recherche. `limit` propriété définit le nombre maximal d’éléments à récupérer dans une réponse API. `cursor` propriété facilite la récupération du point de départ pour l’ensemble suivant de ressources définies dans la propriété `limit` . Par exemple, si vous définissez `50` comme limite dans la requête API, vous pouvez utiliser la propriété `cursor` pour démarrer et récupérer les 50 éléments suivants à l’aide de la requête API suivante.

## Rechercher le point d’entrée de l’API Assets {#search-assets-api-endpoint}

Le point d’entrée d’une requête d’API de ressources de recherche doit être au format suivant :
`https://delivery-pXXXX-eYYYY.adobeaemcloud.com/adobe/assets/search`

Le domaine de diffusion est similaire, par sa structure, au domaine de l’environnement de création Experience Manager. La seule différence est de remplacer le terme `author` par `delivery`.

`pXXXX` fait référence à l’ID de programme

`eYYYY` fait référence à l’identifiant d’environnement

## Méthode de requête de l’API Rechercher des ressources {#search-assets-api-request-method}

POST

## Rechercher l’en-tête de l’API Assets {#search-assets-api-header}

Vous devez fournir les détails suivants lors de la définition d’un en-tête dans l’API Rechercher des ressources :

```java
headers: {
      'Content-Type': 'application/json',
      'X-Adobe-Accept-Experimental': '1',
      Authorization: 'Bearer <YOUR_JWT_HERE>',
      'X-Api-Key': 'YOUR_API_KEY_HERE'
    },
```

Pour appeler l’API Search, un jeton IMS est nécessaire pour définir dans les détails de la `Authorization`. Le jeton IMS est récupéré à partir d’un compte technique. Voir [Récupérer les informations d’identification AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=fr#fetch-the-aem-as-a-cloud-service-credentials) pour créer un compte technique. Voir [Génération du jeton d’accès](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=fr#generating-the-access-token) pour générer le jeton IMS et l’utiliser correctement dans l’en-tête de la requête de l’API Search Assets.

Pour afficher des exemples de requête, des exemples de réponse et des codes de réponse, voir [Rechercher l’API Assets](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/search).
