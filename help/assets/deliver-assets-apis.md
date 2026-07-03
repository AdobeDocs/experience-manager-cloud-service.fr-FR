---
title: API de diffusion
description: Découvrez comment utiliser les API de diffusion.
role: User
badgeSaas: label="AEM Assets" type="Positive" tooltip="S’applique à AEM Assets)."
exl-id: 806ca38f-2323-4335-bfd8-a6c79f6f15fb
source-git-commit: fa93e2079ad5a2840b5e58c5b83cb288606bda97
workflow-type: tm+mt
source-wordcount: '1879'
ht-degree: 6%

---

# API de diffusion {#delivery-apis}

Toutes les [ressources approuvées](approve-assets.md) disponibles dans le référentiel de ressources d’Experience Manager peuvent être [recherchées](search-assets-api.md) puis diffusées vers les applications intégrées en aval à l’aide d’une URL de diffusion.

Toute modification apportée aux ressources approuvées dans la gestion des ressources numériques, y compris les mises à jour de version et les modifications de métadonnées, est automatiquement répercutée dans les URL de diffusion. Avec une courte valeur de durée de vie (TTL) de 10 minutes configurée pour la diffusion des ressources via le réseau CDN, les mises à jour sont visibles sur toutes les interfaces de création et de publication en moins de 10 minutes.

L’image suivante illustre les URL de diffusion disponibles :

![ API de diffusion ](assets/delivery-url.png)

Le tableau suivant illustre l’utilisation des différentes API de diffusion disponibles :

| API de diffusion | Description |
|---|---|
| [Représentation binaire optimisée pour le web de la ressource au format de sortie demandé](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat) | Renvoie la représentation binaire optimisée pour le web de la ressource au format de sortie demandé en fonction de l’identifiant de ressource envoyé dans la requête. Vous pouvez également définir différents modificateurs d’image, tels que la largeur, la hauteur, la rotation, le retournement, la qualité, le recadrage, le format et le [recadrage intelligent](/help/assets/dynamic-media/image-profiles.md). Voir [Détails de l’API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat) pour connaître les formats et les modificateurs d’image pris en charge.<br>Adobe recommande d’utiliser cette API pour tous les types de format d’image. |
| [Représentation binaire optimisée pour le web de la ressource](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAsset) | L’API conviviale qui applique la valeur par défaut est une représentation binaire optimisée pour le web de la ressource renvoyée dans la réponse. Les valeurs par défaut comprennent un format JPEG/WEBP standard, une qualité => 65 et une largeur => 1024. |
| [Fichier binaire original chargé de la ressource](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetOriginal) | Renvoie les fichiers binaires chargés initialement pour la ressource. Adobe recommande d’utiliser cette API pour les types de format de document et les images SVG. |
| [Rendu prégénéré de la ressource disponible dans l’environnement de création AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetRendition) | Renvoie le flux binaire du rendu de la ressource disponible dans l’environnement de création AEM Assets en fonction de l’identifiant de la ressource et du nom du rendu envoyés dans la requête. |
| [Métadonnées de ressource](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetMetadata) | Renvoie les propriétés associées à une ressource, telles que le titre, la description, CreateDate, ModifyDate, etc. |
| [Conteneur du lecteur pour la ressource vidéo](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/videoPlayerDelivery) | Renvoie le conteneur du lecteur pour la ressource vidéo. Vous pouvez incorporer le lecteur dans un élément HTML iframe et lire la vidéo. |
| [Manifestes de lecture au format de sortie sélectionné](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/videoManifestDelivery) | Renvoie le fichier de manifeste de lecture pour la ressource vidéo spécifiée au format de sortie sélectionné. Vous devez créer un lecteur personnalisé capable de diffuser en continu adaptative par le biais des protocoles HLS ou DASH pour pouvoir extraire le fichier de manifeste de lecture et lire la vidéo. |

>[!IMPORTANT]
>
>Vous pouvez tester n’importe quel modificateur, qui n’est généralement pas disponible via les API expérimentales. Par exemple : Cliquez ici pour en savoir plus sur l’utilisation des [API expérimentales](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/how-to/#experimental-apis) et la [ liste complète des modificateurs](https://developer.adobe.com/experience-cloud/experience-manager-apis/).

Dynamic Media avec les fonctionnalités OpenAPI prend également en charge les vidéos de forme longue. Les vidéos de forme longue peuvent prendre en charge jusqu’à 50 Go et 2 heures.

Pour plus d’informations sur les offres Dynamic Media disponibles et leurs fonctionnalités, consultez [Dynamic Media Prime et Ultimate](/help/assets/dynamic-media/dm-prime-ultimate.md).

>[!NOTE]
>
>Les clientes et clients DM Prime peuvent utiliser des modificateurs d’image de base, notamment la rotation, le recadrage, la symétrie, la hauteur, la largeur et la qualité. L’imagerie dynamique ne prend pas en charge AVIF pour les clientes et clients DM Prime.

## Points d’entrée des API de diffusion {#delivery-apis-endpoint}

Les points d’entrée de l’API varient pour chaque API de diffusion. Par exemple, le point d’entrée de l’API pour `Web-optimized binary representation of the asset in the requested output format`’API est :

Le domaine de diffusion est similaire, par sa structure, au domaine de l’environnement de création Experience Manager. La seule différence est de remplacer le terme `author` par `delivery`.

`pXXXX` fait référence à l’ID de programme

`eYYYY` fait référence à l’identifiant d’environnement

Voir [Détails de l’API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#tag/Assets) pour plus d’informations.

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

Pour appeler les API de diffusion, un jeton IMS est requis dans les détails de la `Authorization` pour diffuser une ressource restreinte. Le jeton IMS est récupéré à partir d’un compte technique. Voir [Récupérer les informations d’identification AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis) pour créer un compte technique. Voir [Génération du jeton d’accès](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis) pour générer le jeton IMS et l’utiliser de manière appropriée dans l’en-tête de la requête des API de diffusion.


Pour afficher des exemples de requêtes, des exemples de réponses et des codes de réponse, voir [API de diffusion](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat).

## Questions fréquentes {#delivery-apis-faqs}

### Que sont les API de diffusion Dynamic Media avec OpenAPI et qu’activent-elles ? {#delivery-apis-overview}

Les API de diffusion Dynamic Media avec OpenAPI permettent de diffuser des ressources approuvées stockées dans Adobe Experience Manager Assets vers des applications intégrées en aval via une URL de diffusion. Sept API distinctes sont disponibles, couvrant la diffusion d’images, la diffusion binaire d’origine, la diffusion de rendu prégénéré, la récupération des métadonnées de ressource, l’incorporation du lecteur vidéo et la diffusion du manifeste de lecture vidéo. Toutes les modifications apportées aux ressources approuvées dans la gestion des ressources numériques (DAM), y compris les mises à jour de version et les modifications de métadonnées, sont automatiquement répercutées dans les URL de diffusion sans nécessiter de republication ou d’intervention manuelle.

### À quelle vitesse les mises à jour des ressources apparaissent-elles dans les URL des API de diffusion après les modifications dans AEM Assets ? {#delivery-api-ttl-updates}

Les mises à jour des ressources approuvées dans AEM Assets sont visibles dans toutes les interfaces de création et de publication en moins de 10 minutes. Dynamic Media avec les API de diffusion OpenAPI utilisent une courte durée de vie de 10 minutes configurée pour la diffusion de ressources via le réseau CDN. Cela signifie que les mises à jour de version, les modifications de métadonnées et les autres modifications apportées aux ressources approuvées dans la gestion des ressources numériques se propagent automatiquement aux URL de diffusion dans les 10 minutes sans nécessiter d’invalidation manuelle du cache.

### Quelle API de diffusion dois-je utiliser pour diffuser des ressources d’images ? {#delivery-api-image-recommendation}

La représentation binaire optimisée pour le web de la ressource dans l’API du format de sortie demandée est l’API recommandée pour tous les types de format d’image. Cette API renvoie la représentation binaire optimisée pour le web de la ressource au format de sortie demandé en fonction de l’identifiant de ressource envoyé dans la requête. Il prend en charge divers modificateurs d’image, notamment la largeur, la hauteur, la rotation, le retournement, la qualité, le recadrage, le format et le recadrage intelligent. Pour les types de format de document et les images SVG, le fichier binaire original chargé de l’API de ressource est recommandé à la place.

### Quels modificateurs d’image sont pris en charge par l’API de diffusion de représentation binaire optimisée pour le web ? {#delivery-api-image-modifiers}

La représentation binaire optimisée pour le web de la ressource dans l’API de format de sortie demandée prend en charge les modificateurs d’image, notamment la largeur, la hauteur, la rotation, le retournement, la qualité, le recadrage, le format et le recadrage intelligent. Ces modificateurs peuvent être définis en tant que paramètres dans la requête d’URL de diffusion pour transformer la ressource au moment de la diffusion sans modifier la ressource d’origine stockée dans AEM Assets.

### Que renvoie par défaut l’API de diffusion de représentation binaire optimisée pour le web ? {#delivery-api-defaults}

La représentation binaire optimisée pour le web et pratique de l’API de ressource s’applique par défaut à la ressource renvoyée dans la réponse. Les valeurs par défaut sont le format JPEG ou WEBP, une qualité de 65 et une largeur de 1 024 pixels. Cette API est appropriée lorsque aucun format de sortie spécifique ou contrôle de modificateur n’est nécessaire et qu’un rendu standard optimisé pour le web est suffisant pour l’application en aval.

### Quelle API de diffusion dois-je utiliser pour les documents et les images SVG ? {#delivery-api-documents-svg}

Le fichier binaire original chargé de l’API de ressource est l’API recommandée pour les types de format de document et les images SVG. Cette API renvoie le fichier binaire chargé à l’origine pour la ressource sans appliquer de transformations d’optimisation web. Pour tous les autres types de format d’image, il est recommandé d’utiliser l’API de représentation binaire optimisée pour le web au format de sortie demandé.

### Comment récupérer les rendus prégénérés d’une ressource à l’aide des API de diffusion ? {#delivery-api-pre-generated-renditions}

Le rendu prégénéré de la ressource disponible dans l’API de l’environnement de création AEM Assets renvoie le flux de bits d’un rendu spécifique en fonction de l’identifiant de la ressource et du nom du rendu envoyés dans la requête. Le rendu doit déjà exister dans l’environnement de création AEM Assets avant de pouvoir être récupéré à l’aide de cette API. Cette API est distincte de l’API binaire optimisée pour le web, qui génère la sortie à la demande à l’aide de modificateurs d’image.

### Comment incorporer et lire une ressource vidéo à l’aide des API de diffusion ? {#delivery-api-video-player}

Le conteneur Lecteur de l’API de ressource vidéo renvoie un conteneur de lecteur pour une ressource vidéo qui peut être incorporée dans un élément HTML iframe pour activer la lecture vidéo sur la page. Dans les scénarios nécessitant des implémentations de lecteur personnalisées avec diffusion en continu adaptative, les manifestes de lecture dans l’API de format de sortie sélectionnée renvoient le fichier de manifeste de lecture pour la ressource vidéo spécifiée au format HLS ou DASH. Un lecteur personnalisé capable de diffuser en continu adaptative via les protocoles HLS ou DASH doit être créé pour utiliser le fichier manifeste et lire la vidéo.

### Quelle est la taille et la durée maximales du fichier vidéo prises en charge par Dynamic Media avec les API de diffusion OpenAPI ? {#delivery-api-video-limits}

Dynamic Media avec les API de diffusion OpenAPI prennent en charge les vidéos de forme longue d’une taille de fichier allant jusqu’à 50 Go et d’une durée allant jusqu’à 2 heures. Ces limites s’appliquent aux ressources vidéo diffusées via le conteneur du lecteur et les API de diffusion des manifestes de lecture.

### Comment l’URL du point d’entrée de l’API de diffusion est-elle structurée ? {#delivery-api-endpoint-structure}

L’URL du point d’entrée de l’API de diffusion pour la représentation binaire optimisée pour le web dans le format de sortie demandé suit cette structure : {assetId}/as/{seoName}.{format}. La structure du domaine de diffusion est similaire à celle du domaine de l’environnement de création AEM. La seule différence réside dans le remplacement du terme auteur par la diffusion. Dans l’URL, pXXXX fait référence à l’ID de programme et eYYY à l’ID d’environnement. Toutes les API de diffusion utilisent la méthode de requête HTTP GET.

### Quelle authentification est requise pour appeler Dynamic Media avec les API de diffusion OpenAPI ? {#delivery-api-authentication}

L’appel de Dynamic Media avec les API de diffusion OpenAPI nécessite un jeton IMS dans l’en-tête d’autorisation pour diffuser des ressources limitées. L’en-tête doit inclure deux champs : If-None-Match comme valeur de chaîne, et Authorization comme jeton porteur contenant le jeton IMS. Le jeton IMS est récupéré à partir d’un compte technique créé à l’aide du workflow Informations d’identification AEM as a Cloud Service . Le compte technique doit être configuré et le jeton d’accès généré avant d’appeler une API de diffusion.

### Que sont les API de diffusion expérimentales et comment y accéder ? {#delivery-api-experimental}

Les API de diffusion expérimentales permettent de tester des modificateurs d’image qui ne sont pas encore généralement disponibles. Pour accéder aux API expérimentales, utilisez un format de chemin d’URL qui inclut le modificateur et une date d’expiration, par exemple : /adobe/experiment/advancemodifiers-expires-YYYMMDD/assets. La liste complète des modificateurs expérimentaux disponibles est documentée sur Adobe Developer Console. Les API expérimentales sont destinées à des fins de test et peuvent être modifiées avant leur disponibilité générale.

### Quelles fonctionnalités de modificateur d’image sont disponibles pour les clients Dynamic Media Prime par rapport à Dynamic Media Ultimate ? {#delivery-api-prime-vs-ultimate-modifiers}

Les clients de Dynamic Media Prime peuvent utiliser des modificateurs d’image de base, notamment la rotation, le recadrage, le retournement, la hauteur, la largeur et la qualité via les API de diffusion. L’imagerie dynamique est disponible pour les clients Dynamic Media Prime, à l’exception que le format AVIF n’est pas pris en charge pour l’imagerie dynamique sur Dynamic Media Prime. Les clients Dynamic Media Ultimate ont accès à l’ensemble des modificateurs d’image et des fonctionnalités d’imagerie dynamique, y compris la prise en charge du format AVIF.