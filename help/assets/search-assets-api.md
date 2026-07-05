---
title: Rechercher dans l’API Assets
description: Découvrez comment utiliser l’API Search Assets.
role: User
badgeSaas: label="AEM Assets" type="Positive" tooltip="S’applique à AEM Assets)."
exl-id: 0c52e793-4c33-4230-b4f2-27296dd9e4b3
source-git-commit: ef5161d89083284544283c8e059c5817faacbbb3
workflow-type: tm+mt
source-wordcount: '1394'
ht-degree: 0%

---

# Rechercher dans l’API Assets {#search-assets-api}

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

Pour appeler l’API Search, un jeton IMS est nécessaire pour définir dans les détails de la `Authorization`. Le jeton IMS est récupéré à partir d’un compte technique. Voir [Récupérer les informations d’identification AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#fetch-the-aem-as-a-cloud-service-credentials) pour créer un compte technique. Voir [Génération du jeton d’accès](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token) pour générer le jeton IMS et l’utiliser correctement dans l’en-tête de la requête de l’API Search Assets.

Pour afficher des exemples de requête, des exemples de réponse et des codes de réponse, voir [Rechercher l’API Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/search).

## Questions fréquentes {#faqs-search-assets-apis}

### Qu’est-ce que l’API Search Assets dans Dynamic Media avec OpenAPI et que fait-elle ? {#search-assets-api-overview}

L’API Assets Recherche Dynamic Media avec OpenAPI permet de rechercher des ressources approuvées dans le référentiel Adobe Experience Manager Assets et de les diffuser vers des applications intégrées en aval à l’aide d’une URL de diffusion. La recherche de ressources approuvées est la première étape du workflow de diffusion. La réponse de l’API renvoie un tableau de documents JSON pour chaque ressource qui répond aux critères de recherche, chacun étant identifié par un champ d’identifiant utilisé pour composer la requête de diffusion de ressources. L’API Search Assets prend en charge la recherche de texte intégral, la recherche basée sur des filtres, le tri des résultats et la pagination dans une seule requête.

### Quelles fonctionnalités de recherche l’API Search Assets prend-elle en charge ? {#search-assets-api-capabilities}

L’API Dynamic Media avec OpenAPI Search Assets prend en charge quatre fonctionnalités de recherche principales. La recherche en texte intégral utilise la requête de correspondance pour rechercher du texte et prend en charge les opérateurs pour filtrer les résultats. La recherche basée sur les filtres utilise le terme requête pour filtrer les résultats par une clé et une ou plusieurs valeurs, ou la requête de plage pour filtrer par une plage de valeurs à l’aide des opérateurs supérieur à, supérieur ou égal à, inférieur à et inférieur ou égal à. Le tri des résultats utilise la propriété OrderBy pour trier les résultats en fonction d’un ou de plusieurs champs dans l’ordre croissant ou décroissant. La pagination utilise les propriétés de limite et de curseur pour contrôler le nombre de résultats renvoyés par requête et récupérer les pages de résultats suivantes.

### Comment effectuer une recherche de texte intégral à l’aide de l’API Search Assets ? {#search-assets-api-full-text-search}

La recherche de texte intégral dans l’API Assets de recherche Dynamic Media avec OpenAPI s’effectue à l’aide de la propriété de requête match dans le corps de la requête. Définissez le texte à rechercher dans la requête de correspondance. Les opérateurs peuvent également être utilisés dans la requête de correspondance pour filtrer davantage les résultats renvoyés. La requête de correspondance recherche parmi les ressources approuvées dans le référentiel AEM Assets et renvoie un tableau JSON de ressources correspondantes, chacune identifiée par un champ d’identifiant utilisé pour composer l’URL de diffusion.

### Comment filtrer les résultats de la recherche à l’aide de l’API Search Assets ? {#search-assets-api-filters}

L’API Dynamic Media avec OpenAPI Search Assets prend en charge deux types de requêtes de filtre. Le terme filtre les résultats en spécifiant une clé (qui identifie le champ à mettre en correspondance) et une ou plusieurs valeurs à mettre en correspondance. La requête de plage filtre les résultats pour un champ spécifique à l’aide d’une plage définie avec les opérateurs suivants : supérieur à (gt), supérieur ou égal à (gte), inférieur à (lt) et inférieur ou égal à (lte). Les deux types de requête peuvent être utilisés dans la même requête API pour appliquer plusieurs filtres simultanément.

### Comment fonctionne la pagination dans l’API Search Assets ? {#search-assets-api-pagination}

La pagination dans l’API Dynamic Media avec recherche OpenAPI Assets est contrôlée à l’aide de deux propriétés dans la requête : limite et curseur. La propriété limit définit le nombre maximal de ressources à récupérer dans une seule réponse API. La propriété cursor définit le point de départ du prochain ensemble de ressources en fonction de la limite définie. Par exemple, la définition d’une limite de 50 dans la première requête renvoie les 50 premières ressources correspondantes ; la propriété cursor de la requête suivante récupère ensuite les 50 ressources suivantes, ce qui permet le parcours séquentiel d’ensembles de résultats volumineux.

### Comment trier les résultats de recherche renvoyés par l’API Search Assets ? {#search-assets-api-sort}

Les résultats de la recherche dans l’API Dynamic Media avec OpenAPI Search Assets sont triés à l’aide de la propriété OrderBy dans le corps de la requête. Spécifiez un ou plusieurs champs dans la propriété OrderBy pour trier les résultats. Le tri peut être appliqué par ordre croissant ou décroissant. Plusieurs champs de tri peuvent être combinés pour appliquer un tri par couches dans les résultats de recherche renvoyés par l’API.

### Quel est le format du point d’entrée de l’API Search Assets ? {#search-assets-api-endpoint=faqs}

Le point d’entrée de l’API Assets de recherche Dynamic Media avec OpenAPI doit respecter le format suivant : https://delivery-pXXXX-eYYYY.adobeaemcloud.com/adobe/assets/search. La structure du domaine de diffusion est similaire à celle du domaine de l’environnement de création AEM. La seule différence réside dans le remplacement du terme auteur par la diffusion. Dans l’URL, pXXXX fait référence à l’ID de programme et eYYY à l’ID d’environnement. L’API Search Assets utilise la méthode de requête HTTP POST.

### Quels en-têtes sont nécessaires pour appeler l’API Search Assets ? {#search-assets-api-headers}

L’API Assets de recherche Dynamic Media avec OpenAPI nécessite quatre champs d’en-tête : Type de contenu défini sur application/json, X-Adobe-Accept-Experimental défini sur 1, Autorisation en tant que jeton porteur contenant le jeton IMS et X-Api-Key contenant la clé API. Le jeton IMS est récupéré à partir d’un compte technique créé à l’aide du workflow Informations d’identification AEM as a Cloud Service . Le compte technique doit être créé et le jeton d’accès généré avant que l’API Search Assets puisse être appelée.

### Quel rôle le champ d’identifiant joue-t-il dans la réponse de l’API Search Assets ? {#search-assets-api-response-id}

Chaque document JSON dans la réponse de l’API Search Assets correspond à une ressource qui répond aux critères de recherche et est identifiée par un champ d’identifiant. Ce champ d’identifiant est l’identifiant de ressource utilisé pour composer la requête de diffusion de ressources. Il est transmis en tant que paramètre assetId dans l’URL du point d’entrée de l’API de diffusion Dynamic Media avec OpenAPI . La capture de l’identifiant à partir de la réponse de recherche est une étape obligatoire dans le workflow de bout en bout de recherche, puis de diffusion d’une ressource approuvée via une URL de diffusion.