---
title: API de diffusion
description: Découvrez comment utiliser les API de diffusion.
role: User
exl-id: 806ca38f-2323-4335-bfd8-a6c79f6f15fb
source-git-commit: 7727aa87693cc96e3497dcda71190866b198975d
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 7%

---

# API de diffusion {#delivery-apis}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [Bonnes pratiques relatives aux métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Fonctionnalités Dynamic Media avec OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation de développement pour AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

>[!AVAILABILITY]
>
>Le guide des fonctionnalités de Dynamic Media avec OpenAPI est désormais disponible au format PDF. Téléchargez l’intégralité du guide et utilisez l’assistant Adobe Acrobat AI pour répondre à vos requêtes.
>
>[!BADGE Dynamic Media avec OpenAPI Feature PDF ]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

Toutes les [ressources approuvées](approve-assets.md) disponibles dans le référentiel de ressources Experience Manager peuvent être [recherchées](search-assets-api.md) et ensuite diffusées aux applications intégrées en aval à l’aide d’une URL de diffusion.

Toute modification apportée aux ressources approuvées dans la gestion des ressources numériques, y compris les mises à jour de version et les modifications de métadonnées, est automatiquement répercutée dans les URL de diffusion. Avec une valeur TTL (short Time-to-Live) de 10 minutes configurée pour la diffusion de ressources via CDN, les mises à jour deviennent visibles dans toutes les interfaces de création et de publication en moins de 10 minutes.

L’image suivante illustre les URL de diffusion disponibles :

![API de diffusion](assets/delivery-url.png)

Le tableau suivant illustre l’utilisation des différentes API de diffusion disponibles :

| API de diffusion | Description |
|---|---|
| [Représentation binaire optimisée pour le web de la ressource au format de sortie demandé](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetSeoFormat) | Renvoie la représentation binaire optimisée pour le web de la ressource dans le format de sortie demandé en fonction de l’ID de ressource envoyé dans la requête. En outre, vous pouvez définir divers modificateurs d’image tels que la largeur, la hauteur, la rotation, la rotation, la qualité, le recadrage, le format et le [recadrage intelligent](/help/assets/dynamic-media/image-profiles.md). Voir les [détails de l’API](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetSeoFormat) pour connaître les formats et les modificateurs d’image pris en charge.<br>Adobe recommande d&#39;utiliser cette API pour tous les types de format d&#39;image. |
| [Représentation binaire optimisée pour le web de la ressource](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAsset) | API de commodité qui s’applique par défaut à la représentation binaire optimisée pour le web de la ressource renvoyée dans la réponse. Les valeurs par défaut incluent un format standard JPEG/WEBP, qualité => 65 et largeur => 1024. |
| [binaire téléchargé original de la ressource](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetOriginal) | Renvoie les fichiers binaires chargés initialement pour la ressource. Adobe recommande d’utiliser cette API pour les types de format de document et les images de SVG. |
| [Rendu pré-généré de la ressource disponible dans l’environnement de création AEM Assets](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetRendition) | Renvoie le flux binaire du rendu de ressource disponible dans l’environnement de création AEM Assets en fonction de l’ID de ressource et du nom du rendu envoyé dans la requête. |
| [Métadonnées de ressource](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetMetadata) | Renvoie les propriétés associées à une ressource, telles que le titre, la description, CreateDate, ModifyDate, etc. |
| [Conteneur du lecteur pour la ressource vidéo](https://adobe-aem-assets-delivery.redoc.ly/#operation/videoPlayerDelivery) | Renvoie le conteneur du lecteur pour la ressource vidéo. Vous pouvez incorporer le lecteur dans un élément d’HTML iframe et lire la vidéo. |
| [Manifeste de lecture au format de sortie sélectionné](https://adobe-aem-assets-delivery.redoc.ly/#operation/videoManifestDelivery) | Renvoie le fichier manifeste de lecture de la ressource vidéo spécifiée dans le format de sortie sélectionné. Vous devez créer un lecteur personnalisé capable de diffuser en continu adaptative via des protocoles HLS ou DASH pour pouvoir extraire le fichier manifeste de lecture et lire la vidéo. |


>[!NOTE]
>
[Les paramètres d’image prédéfinis, l’imagerie dynamique et d’autres modificateurs d’image ](https://adobe-aem-assets-delivery-advancemodifiers.redoc.ly/) sont disponibles en tant que fonctionnalité de disponibilité limitée. Pour y accéder, [créez et envoyez un cas d’assistance clientèle Adobe](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html).

## Points de terminaison des API de diffusion {#delivery-apis-endpoint}

Les points de terminaison de l’API varient pour chaque API de diffusion. Par exemple, le point d’entrée de l’API `Web-optimized binary representation of the asset in the requested output format` est le suivant :
`https://delivery-pXXXX-eYYYY.adobeaemcloud.com/adobe/assets/{assetId}/as/{seoName}.{format}`

Le domaine de diffusion est similaire en termes de structure au domaine de l’environnement de création Experience Manager. La seule différence est de remplacer le terme `author` par `delivery`.

`pXXXX` fait référence à l’ID de programme

`eYYYY` fait référence à l’ID d’environnement

Pour plus d’informations, voir [Détails de l’API](https://adobe-aem-assets-delivery.redoc.ly/#tag/Assets) .

## Méthode de requête des API de diffusion {#delivery-api-request-method}

GET

## En-tête des API de diffusion {#deliver-assets-api-header}

Vous devez fournir les détails suivants lors de la définition d’un en-tête dans l’en-tête des API de diffusion :

```java
headers: {
      'If-None-Match': 'string',
      Authorization: 'Bearer <YOUR_JWT_HERE>'
    }
```

Pour appeler les API de diffusion, un jeton IMS est requis dans les détails `Authorization` pour diffuser une ressource limitée. Le jeton IMS est récupéré à partir d’un compte technique. Voir [Récupération des informations d’identification AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#fetch-the-aem-as-a-cloud-service-credentials) pour créer un compte technique. Voir [Génération du jeton d’accès](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token) pour générer le jeton IMS et l’utiliser de manière appropriée dans l’en-tête de requête des API de diffusion.


Pour afficher des exemples de requête, des exemples de réponse et des codes de réponse, voir [API de diffusion](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetSeoFormat).
