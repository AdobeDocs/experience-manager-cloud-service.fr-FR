---
title: Optimisation des images à l’aide de Dynamic Media avec les fonctionnalités OpenAPI
description: Découvrez comment optimiser les images à la volée avant leur diffusion publique à l’aide des fonctionnalités d’optimisation d’image de Dynamic Media avec les fonctionnalités OpenAPI
role: Admin
feature: Asset Management, Publishing, Collaboration, Asset Processing
source-git-commit: 74c5fbda5ee1ad46b5fcab5ba89f0fd96873e3cf
workflow-type: tm+mt
source-wordcount: '1265'
ht-degree: 0%

---


# Optimisation des images à l’aide de Dynamic Media avec les fonctionnalités OpenAPI{#Optimize-images-using-Dynamic-Media-with-OpenAPI-Capabilities}

[!DNL Dynamic Media with OpenAPI capabilities] offre des fonctionnalités d’optimisation d’image telles que [!DNL Smart Crop], [!DNL Image Presets] et [!DNL Smart Imaging]. Ces fonctionnalités permettent de fournir des images réactives de haute qualité qui se chargent rapidement sur différents appareils et réseaux.

## Recadrage intelligent{#smart-crop-using-dynamic-media-with-openapi-capabilities}

Le [recadrage intelligent](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat!in=query&path=smartcrop&t=request) est une fonctionnalité de dimensionnement dynamique d’[!DNL Dynamic Media with OpenAPI capabilities]. [!DNL Smart Crop] est une technique de traitement des images avancée qui utilise le recadrage basé sur le contenu optimisé par l’IA pour recadrer intelligemment des images pour différentes tailles d’écran tout en préservant le contexte visuel dans les versions recadrées. L’IA analyse l’image pour identifier le point focal ou le point ciblé prévu, puis recadre automatiquement l’image pour conserver le point focal dans toutes les versions recadrées. [!DNL Smart Crop], un élément clé du responsive design, offre un moyen économique et rapide de recadrer des images.

Consultez l’article [Profils d’image Dynamic Media](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles) pour savoir comment [créer des rendus de recadrage intelligent](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles#creating-image-profiles) dans [!DNL Admin View], [les appliquer à des dossiers](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles#applying-an-image-profile-to-folders) ou [modifier des rendus](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles#editing-the-smart-crop-or-smart-swatch-of-a-single-image) déjà appliqués à une image ou à un dossier. Découvrez comment créer une [!DNL Smart Crop] étape par étape dans cette [vidéo](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use).

Le paramètre [!DNL Smart Crop] s’attend à ce que les profils nommés de recadrage intelligent existent et aient été appliqués à la ressource. Voir [Profils de recadrage intelligent](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat!in=query&path=smartcrop&t=request) pour en savoir plus sur le paramètre [!DNL Smart Crop] et sur la manière dont les profils [!DNL Smart Crop] nommés sont appliqués.

>[!IMPORTANT]
>
> Vous ne pouvez créer des rendus [!DNL Smart Crop] que dans la vue Administration .

## Paramètres d’image prédéfinis{#image-presets-using-dynamic-media-with-openapi-capabilities}

Transformez des images à la volée à l’aide de la fonctionnalité [Paramètres d’image prédéfinis](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat!in=query&path=preset&t=request) dans [!DNL Dynamic Media with OpenAPI capabilities]. Un [!DNL image preset] est un ensemble prédéfini de règles de dimensionnement et de formatage pour une image de sortie.

[!DNL Dynamic Media with OpenAPI capabilities] utilise des noms de paramètres prédéfinis pour transformer une image à la volée et générer son rendu instantanément. Lorsque vous demandez une image par le biais d’une URL de diffusion [!DNL Dynamic Media with OpenAPI] qui inclut un paramètre prédéfini, [!DNL DM with OpenAPI] applique les transformations du paramètre prédéfini, crée le rendu à la demande et le diffuse à l’utilisateur.

Vous pouvez appliquer un seul paramètre prédéfini à plusieurs images par le biais de leurs URL de diffusion [!DNL Dynamic Media with OpenAPI]. Cela permet d’assurer une mise en forme cohérente entre les ressources sans les modifier manuellement.

Consultez l’article [Gestion des paramètres prédéfinis d’image](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/managing-image-presets) pour savoir [comment créer des paramètres prédéfinis d’image dans la vue Administration](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/managing-image-presets#creating-image-presets) et [comment créer des paramètres prédéfinis d’image réactifs](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/managing-image-presets#creating-a-responsive-image-preset) qui adaptent automatiquement les ressources en fonction des différentes tailles d’écran.

### Avantages de l’utilisation des paramètres d’image prédéfinis{#benefits-of-image-presets}

[!DNL Image Presets] présente plusieurs avantages pour la gestion et la diffusion des images dans [!DNL Dynamic Media with OpenAPI]. Voici quelques-uns des principaux avantages :

* Les paramètres prédéfinis raccourcissent les URL de diffusion d’images. Au lieu d’ajouter plusieurs modificateurs d’image qui allongent l’URL de diffusion, utilisez un seul préréglage. Les URL plus courtes sont plus faciles à gérer et garantissent une diffusion d’images cohérente sur les sites web, les applications mobiles, les e-mails et d’autres canaux.
* Les paramètres d’image prédéfinis créent des rendus juste à temps à partir d’un fichier image source. Cette fonctionnalité de génération de rendu à la demande élimine la nécessité de créer et de stocker plusieurs rendus statiques du même fichier, ce qui permet de gagner du temps et de l’espace de stockage.
* Appliquez un seul paramètre prédéfini à un large ensemble de ressources en même temps, en évitant les modifications manuelles de chaque ressource, en garantissant une mise en forme cohérente et en permettant l’évolutivité.
* Lorsque vous mettez à jour les paramètres d’un paramètre prédéfini, toutes les images utilisant ce paramètre prédéfini sont reformatées automatiquement. Cela simplifie la modification en centralisant les mises à jour de formatage, ce qui élimine la nécessité de modifier à nouveau des ressources individuelles ou du code web.
* Améliore l’efficacité et les performances avec les rendus dynamiques mis en cache par le réseau CDN, ce qui accélère le chargement et optimise les performances sur les appareils et les réseaux.

### Utilisation des paramètres d’image prédéfinis{#use-image-presets-using-dynamic-media-with-openapi-capabilities}

Après avoir créé les [!DNL Image Presets], vous pouvez les utiliser pour les workflows suivants :
* [Utilisez des paramètres prédéfinis dans l’URL de diffusion d’images pour créer ses rendus à la volée avant de les diffuser à l’utilisateur final.](#use-presets-in-delivery-urls)
* [Utilisation de paramètres prédéfinis lors de la création dans AEM Sites](#use-presets-during-authoring-in-aem-sites)

#### Utilisation de paramètres prédéfinis dans l’URL de diffusion d’images{#use-presets-in-delivery-urls}

Les préréglages raccourcissent et facilitent l’utilisation de vos URL de diffusion.  Chaque nom de préréglage sert d’identifiant unique dans l’URL de diffusion. Au lieu d’ajouter plusieurs modificateurs à l’URL de diffusion d’une ressource, référencez le nom du préréglage pour générer instantanément son rendu. [Découvrez comment appliquer des paramètres prédéfinis d’image Dynamic Media à votre image](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-presets).
L’exemple suivant compare une URL avec un préréglage à une URL sans préréglage.

**URL sans préréglage (URL longue)** :

`https://delivery-p30902-e145436-cmstg.adobeaemcloud.com/adobe/assets/urn:aaid:aem:393d5579-5be2-49a5-ac5f-8fed72bfb614/as/AdobeStock_63266433.avif?width=400&height=300&fit=crop&qualit=85&sharpen=true`

**URL avec un préréglage (URL courte)** :

`https://delivery-p30902-e145436-cmstg.adobeaemcloud.com/adobe/assets/urn:aaid:aem:393d5579-5be2-49a5-ac5f-8fed72bfb614/as/AdobeStock_63266433.avif?preset=thumbnail`.
La miniature du paramètre prédéfini regroupe les mêmes paramètres de modificateur d’image.

#### Utilisation de paramètres prédéfinis lors de la création dans AEM Sites{#use-presets-during-authoring-in-aem-sites}

Les auteurs peuvent sélectionner [!DNL Image Presets] lors de la modification de la page dans [!DNL AEM Sites] page de création lorsque la prise en charge du [!DNL Dynamic Media] est activée.
Pour utiliser des paramètres d’image prédéfinis dans votre page de création, procédez comme suit :
1. Accédez à la page de création de Sites.
1. Exécutez les étapes de la section [Accès aux ressources distantes dans l’éditeur de page d’AEM](/help/assets/integrate-remote-approved-assets-with-sites.md#access-remote-assets-in-aem-page-editor) pour utiliser le panneau [!DNL Asset Selector] pour sélectionner une ressource.
1. Dans le panneau [!DNL asset selector], faites défiler l’écran jusqu’à **[!UICONTROL Type de paramètre prédéfini]**, puis spécifiez `Preset=Preset Name` dans le champ **[!UICONTROL Modificateurs d’image]**.
   ![préréglage](/help/assets/assets/preset-in-asset-selector-panel.png)

## Imagerie dynamique{#use-smart-imaging-using-dynamic-media-with-openapi-capabilities}

Lorsque vous utilisez [!DNL Dynamic Media with OpenAPI capabilities] pour la diffusion d’images, les images sont automatiquement optimisées via [Imagerie dynamique](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/). La diffusion optimisée garantit que les images se chargent plus rapidement, ont une qualité visuelle maximale et une taille de fichier minimale. Cela permet d’obtenir les chargements de page les plus rapides et une qualité visuelle élevée et cohérente sur les appareils et les réseaux, tout en consommant peu de bande passante, ce qui rend votre site web plus rapide et plus réactif.

[!DNL Smart Imaging] comprend les fonctionnalités suivantes :
* [Conversion automatique du format](#auto-format-conversion)
* [Optimisation de la bande passante du réseau](#network-bandwidth-optimisation)

### Conversion automatique du format{#auto-format-conversion}

[!DNL Dynamic Media with OpenAPI] [ convertit automatiquement les images en formats modernes optimisés pour le web, tels que AVIF ou WEBP](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat!in=query&path=auto-format&t=request). La conversion dépend des fonctionnalités du navigateur et de [license-rights](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dm-prime-ultimate), quel que soit le format demandé.
Les formats AVIF et WEBP offrent une meilleure compression, ce qui rend les images plus petites et plus rapides à diffuser et à charger. Le format AVIF est utilisé comme format par défaut, car il gère toutes les fonctionnalités du navigateur.
[!DNL Dynamic Media with OpenAPI] utilise le paramètre de requête `auto-format` pour contrôler le comportement du navigateur lors de la conversion d’une image en divers formats pour une diffusion optimisée. La conversion automatique de format inclut **promotion automatique** et **rétrogradation automatique**. Lorsque le système promeut un format optimisé pour le web (AVIF ou WEBP) sur JPEG ou PNG pour la diffusion, il est appelé promotion automatique.

Par défaut, le paramètre de requête `auto-format` est défini sur `true`. Lorsque `auto-format` est activé (true), le système ignore le format demandé et sélectionne automatiquement un format optimisé pour le web (AVIF ou WEBP) en fonction des caractéristiques de l’image, des fonctionnalités du navigateur et du [droit de licence](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dm-prime-ultimate).

Lorsque la `auto-format` est définie sur true, le système diffuse le format d’image dans l’ordre suivant :
* ***AVIF*** : l’AVIF est fourni si le navigateur le prend en charge et que la licence le permet. Il s’agit de la promotion automatique.
* ***WEBP*** : le WEBP est diffusé si l’AVIF n’est pas pris en charge ou sous licence. Il s’agit également de la promotion automatique.
* ***JPEG*** : JPEG n’est diffusé que lorsque les formats AVIF et WEBP ne sont pas pris en charge et que l’image n’a pas de canal alpha (transparence). Cela s’appelle la rétrogradation automatique.
* ***PNG*** : le format PNG est diffusé lorsque le navigateur ne prend pas en charge les formats modernes et que l’image comporte un canal alpha (transparence). On parle aussi de rétrogradation automatique.

Désactivez-`auto-format` en définissant le paramètre de requête sur `false`, puis spécifiez le format requis pour que l’image soit diffusée dans ce format.

### Optimisation de la bande passante du réseau{#network-bandwidth-optimisation}

Les images sont automatiquement optimisées en fonction des conditions réseau du client afin d’assurer une diffusion plus rapide et un chargement fluide. Les paramètres [Quality](#quality-parameter) et [Max-quality](#max-quality-parameter) ajustent automatiquement la qualité en contrôlant les niveaux de compression de l&#39;image, avec des valeurs comprises entre 1 et 100.

Consultez les comportements clés suivants des paramètres `quality` et `max-quality ` :

* Si [!DNL quality] et [!DNL max-quality] sont spécifiés, [!DNL quality] est prioritaire.
* Si seul [!DNL quality] est spécifié, la qualité est délivrée quel que soit le temps de chargement en fonction de la vitesse du réseau.
* Si seul [!DNL max-quality] est spécifié, la qualité d’image s’ajuste automatiquement en fonction des conditions réseau, fournissant la meilleure qualité possible jusqu’à la valeur de [!DNL max-quality] spécifiée.
* Si aucun n’est spécifié, le système applique l’optimisation dynamique avec une `max-quality` par défaut de `85`.

#### Paramètre de qualité{#quality-parameter}

Le paramètre de qualité donne la priorité à la qualité d’image sur la vitesse de chargement. Il fixe la qualité de l’image de sortie sur la valeur demandée (entre 1 et 100) et ignore les conditions réseau. En savoir plus sur le [ paramètre de qualité ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat!in=query&path=quality&t=request).

#### Paramètre de qualité max{#max-quality-parameter}

La qualité maximale équilibre la qualité de l’image et le temps de chargement en fonction de la vitesse du réseau du client. Il donne la priorité à des temps de chargement plus rapides en réduisant la qualité d’image sur des réseaux plus lents, tout en fournissant la qualité la plus élevée possible (1-100) pour les conditions réseau données. En savoir plus sur le paramètre [max-quality](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat!in=query&path=quality&t=request).



