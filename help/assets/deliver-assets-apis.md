---
title: API de diffusion
description: Découvrez comment utiliser les API de diffusion.
role: User
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# API de diffusion {#delivery-apis}

Tous [ressources approuvées](approved-assets.md) disponibles dans le référentiel de ressources de Experience Manager [searched](search-assets-api.md) et ensuite diffusé aux applications intégrées en aval à l’aide d’une URL de diffusion.

Toute modification apportée aux ressources approuvées dans la gestion des ressources numériques, y compris les mises à jour de version et les modifications de métadonnées, est automatiquement répercutée dans les URL de diffusion. Avec une valeur TTL (short Time-to-Live) de 10 minutes configurée pour la diffusion de ressources via CDN, les mises à jour deviennent visibles dans toutes les interfaces de création et de publication en moins de 10 minutes.

L’image suivante illustre les URL de diffusion disponibles :

![API de diffusion](assets/delivery-url.png)

Le tableau suivant illustre l’utilisation des différentes API de diffusion disponibles :

| API de diffusion | Description |
|---|---|
| [Représentation binaire optimisée pour le web de la ressource au format de sortie demandé](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/getAssetSeoFormat) | Renvoie la représentation binaire optimisée pour le web de la ressource dans le format de sortie demandé en fonction de l’ID de ressource envoyé dans la requête. En outre, vous pouvez définir divers modificateurs d’image, tels que la largeur, la hauteur, la rotation, le pivotement, la qualité, etc. Voir [Détails de l’API](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/getAssetSeoFormat) pour les formats et les modificateurs d’image pris en charge.<br>Adobe recommande d’utiliser cette API pour tous les types de format d’image. |
| [Représentation binaire optimisée pour le web de la ressource](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/getAsset) | API de commodité qui s’applique par défaut à la représentation binaire optimisée pour le web de la ressource renvoyée dans la réponse. Les valeurs par défaut incluent un format standard JPEG/WEBP, qualité => 65 et largeur => 1024. |
| [binaire téléchargé initial de la ressource](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/getAssetOriginal) | Renvoie les fichiers binaires chargés initialement pour la ressource. Adobe recommande d’utiliser cette API pour les types de format de document et les images de SVG. |
| [Métadonnées de ressource](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/getAssetMetadata) | Renvoie les propriétés associées à une ressource, telles que le titre, la description, CreateDate, ModifyDate, etc. |
| [Conteneur de lecteur pour la ressource vidéo](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/videoPlayerDelivery) | Renvoie le conteneur du lecteur pour la ressource vidéo. Vous pouvez incorporer le lecteur dans un élément de HTML iframe et lire la vidéo. |
| [Manifeste de lecture au format sélectionné](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/videoManifestDelivery) | Renvoie le fichier manifeste de lecture de la ressource vidéo spécifiée dans le format de sortie sélectionné. Vous devez créer un lecteur personnalisé capable de diffuser en continu adaptative via des protocoles HLS ou DASH pour pouvoir extraire le fichier manifeste de lecture et lire la vidéo. |

## Points de terminaison des API de diffusion {#delivery-apis-endpoint}

Les points de terminaison de l’API varient pour chaque API de diffusion. Par exemple, le point de terminaison API pour `Web-optimized binary representation of the asset in the requested output format` L’API est :
`https://delivery-pXXXX-eYYYY.adobeaemcloud.com/adobe/assets/{assetId}/as/{seoName}.{format}`

Le domaine de diffusion est similaire en termes de structure au domaine de l’environnement de création du Experience Manager. La seule différence est de remplacer le terme `author` avec `delivery`.

`pXXXX` fait référence à l’ID de programme

`eYYYY` fait référence à l’ID d’environnement

Voir [Détails de l’API](https://adobe-aem-assets-delivery-experimental.redoc.ly/#tag/Assets) pour plus d’informations.

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

Pour appeler les API de diffusion, un jeton IMS est requis dans la variable `Authorization` détails pour diffuser une ressource limitée. Le jeton IMS est récupéré à partir d’un compte technique. Voir [Récupération des informations d’identification as a Cloud Service AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#fetch-the-aem-as-a-cloud-service-credentials) pour créer un compte technique. Voir [Génération du jeton d’accès](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token) pour générer le jeton IMS et l’utiliser de manière appropriée dans l’en-tête de requête des API de diffusion.

Pour consulter des exemples de requête, des exemples de réponse et des codes de réponse, voir [API de diffusion](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/getAssetSeoFormat).
