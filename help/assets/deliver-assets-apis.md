---
title: API de diffusion
description: Découvrez comment utiliser les API de diffusion.
role: User
exl-id: 806ca38f-2323-4335-bfd8-a6c79f6f15fb
source-git-commit: c36938e80d0b159c5f89d450aaa228c37c4f5276
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 16%

---

# API de diffusion {#delivery-apis}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime et Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Intégration d’AEM Assets à Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Extensibilité de l’IU</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Activer Dynamic Media Prime et Ultimate</b></a>
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

Toutes les [ressources approuvées](approve-assets.md) disponibles dans le référentiel de ressources d’Experience Manager peuvent être [recherchées](search-assets-api.md) puis diffusées vers les applications intégrées en aval à l’aide d’une URL de diffusion.

Toute modification apportée aux ressources approuvées dans la gestion des ressources numériques, y compris les mises à jour de version et les modifications de métadonnées, est automatiquement répercutée dans les URL de diffusion. Avec une courte valeur de durée de vie (TTL) de 10 minutes configurée pour la diffusion des ressources via le réseau CDN, les mises à jour sont visibles sur toutes les interfaces de création et de publication en moins de 10 minutes.

L’image suivante illustre les URL de diffusion disponibles :

![ API de diffusion ](assets/delivery-url.png)

Le tableau suivant illustre l’utilisation des différentes API de diffusion disponibles :

| API de diffusion | Description |
|---|---|
| [Représentation binaire optimisée pour le web de la ressource au format de sortie demandé](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetSeoFormat) | Renvoie la représentation binaire optimisée pour le web de la ressource au format de sortie demandé en fonction de l’identifiant de ressource envoyé dans la requête. Vous pouvez également définir différents modificateurs d’image tels que la largeur, la hauteur, la rotation, le retournement, la qualité, le recadrage, le format et le [recadrage intelligent](/help/assets/dynamic-media/image-profiles.md). Voir [Détails de l’API](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetSeoFormat) pour connaître les formats et les modificateurs d’image pris en charge.<br>Adobe recommande d’utiliser cette API pour tous les types de format d’image. |
| [Représentation binaire optimisée pour le web de la ressource](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAsset) | API pratique qui applique les valeurs par défaut à la représentation binaire optimisée pour le web de la ressource renvoyée dans la réponse. Les valeurs par défaut comprennent un format JPEG/WEBP standard, une qualité => 65 et une largeur => 1024. |
| [Fichier binaire original chargé de la ressource](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetOriginal) | Renvoie les fichiers binaires chargés initialement pour la ressource. Adobe recommande d’utiliser cette API pour les types de format de document et les images SVG. |
| [Rendu prégénéré de la ressource disponible dans l’environnement de création AEM Assets](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetRendition) | Renvoie le flux binaire du rendu de la ressource disponible dans l’environnement de création AEM Assets en fonction de l’identifiant de la ressource et du nom du rendu envoyés dans la requête. |
| [Métadonnées de ressource](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetMetadata) | Renvoie les propriétés associées à une ressource, telles que le titre, la description, CreateDate, ModifyDate, etc. |
| [Conteneur du lecteur pour la ressource vidéo](https://adobe-aem-assets-delivery.redoc.ly/#operation/videoPlayerDelivery) | Renvoie le conteneur du lecteur pour la ressource vidéo. Vous pouvez incorporer le lecteur dans un élément HTML iframe et lire la vidéo. |
| [Manifestes de lecture au format de sortie sélectionné](https://adobe-aem-assets-delivery.redoc.ly/#operation/videoManifestDelivery) | Renvoie le fichier de manifeste de lecture pour la ressource vidéo spécifiée au format de sortie sélectionné. Vous devez créer un lecteur personnalisé capable de diffuser en continu adaptative par le biais des protocoles HLS ou DASH pour pouvoir extraire le fichier de manifeste de lecture et lire la vidéo. |

Dynamic Media avec les fonctionnalités OpenAPI prend également en charge les vidéos de forme longue. Les vidéos peuvent prendre en charge jusqu’à 50 Go et 2 heures.

Pour plus d’informations sur les offres Dynamic Media disponibles et leurs fonctionnalités, consultez [Dynamic Media Prime et Ultimate](/help/assets/dynamic-media/dm-prime-ultimate.md).

## Points d’entrée des API de diffusion {#delivery-apis-endpoint}

Les points d’entrée de l’API varient pour chaque API de diffusion. Par exemple, le point d’entrée de l’API pour `Web-optimized binary representation of the asset in the requested output format`’API est :
`https://delivery-pXXXX-eYYYY.adobeaemcloud.com/adobe/assets/{assetId}/as/{seoName}.{format}`

Le domaine de diffusion est similaire, par sa structure, au domaine de l’environnement de création Experience Manager. La seule différence est de remplacer le terme `author` par `delivery`.

`pXXXX` fait référence à l’ID de programme

`eYYYY` fait référence à l’identifiant d’environnement

Voir [Détails de l’API](https://adobe-aem-assets-delivery.redoc.ly/#tag/Assets) pour plus d’informations.

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

Pour appeler les API de diffusion, un jeton IMS est requis dans les détails de la `Authorization` pour diffuser une ressource restreinte. Le jeton IMS est récupéré à partir d’un compte technique. Voir [Récupérer les informations d’identification AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#fetch-the-aem-as-a-cloud-service-credentials) pour créer un compte technique. Voir [Génération du jeton d’accès](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token) pour générer le jeton IMS et l’utiliser de manière appropriée dans l’en-tête de la requête des API de diffusion.


Pour afficher des exemples de requêtes, des exemples de réponses et des codes de réponse, voir [API de diffusion](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetSeoFormat).
