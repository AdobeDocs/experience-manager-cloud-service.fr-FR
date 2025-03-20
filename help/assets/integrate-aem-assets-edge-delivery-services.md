---
title: Intégrer AEM Assets lors de la création de contenu pour Edge Delivery Services
description: Découvrez comment intégrer AEM Assets à Edge Delivery Services. Cette intégration vous permet d’intégrer AEM Assets à Microsoft Word et Google Docs, d’intégrer AEM Assets à l’éditeur universel, d’intégrer Dynamic Media aux fonctionnalités OpenAPI à l’éditeur universel et d’intégrer Dynamic Media aux fonctionnalités OpenAPI à Microsoft Word et Google Docs.
exl-id: e58db2ce-a55a-49b3-ae8e-709b5ea8d095
source-git-commit: 38d4ad078233fcb22422b8c771e7e553cc082c41
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 3%

---

# Intégrer AEM Assets lors de la création de contenu pour Edge Delivery Services {#integrate-aem-assets-while-authoring-for-edge-delivery-services}

![Ressources AEM avec UE](/help/assets/assets/EDS2.png)

[Edge Delivery Services](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/edge-delivery/overview) est un ensemble de services composables qui permet un haut degré de flexibilité dans la manière dont vous créez et diffusez du contenu sur votre site web. Vous pouvez utiliser la [gestion de contenu AEM](/help/sites-cloud/authoring/author-publish.md) et la [création WYSIWYG à l’aide de l’éditeur universel ainsi que la création basée sur des documents](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/authoring).

Vous pouvez modifier le contenu dans :

* [Microsoft Word ou Google Docs](#integrate-aem-assets-with-document-based-authoring-tools)
* [Éditeur universel](#integrate-aem-assets-with-universal-editor)

Après avoir modifié le contenu, vous pouvez le publier dans Edge Delivery Services.

## Intégration d’AEM Assets aux flux de création basés sur des documents pour Edge Delivery Services {#integrate-aem-assets-with-document-based-authoring-tools}

L’intégration d’AEM Assets aux outils de création basés sur des documents, tels que Microsoft Word ou Google Docs, fournit un sélecteur de ressources directement dans votre éditeur. Utilisez ce sélecteur de ressources pour accéder à AEM Assets et insérer des ressources approuvées dans votre document.

Si vous disposez déjà d’un site web Edge Delivery Services, consultez [Plug-in AEM Assets](https://github.com/adobe-rnd/aem-assets-plugin/blob/main/README.md) pour intégrer AEM Assets à votre projet AEM existant. Si vous ne disposez pas d’un site web Edge Delivery Services, consultez les sections [Conditions préalables](#integrate-aem-assets-with-microsoft-word-and-google-docs) et [Intégration d’AEM Assets à un environnement de création basé sur les documents](#integrate-aem-assets-with-microsoft-word-or-google-docs-to-use-aem-assets-with-microsoft-word-or-google-docs) ci-dessous.

### Prérequis{#integrate-aem-assets-with-microsoft-word-and-google-docs}

Avant de commencer, assurez-vous que votre environnement de création basé sur les documents est prêt :

* Intégrez AEM à un outil de création basé sur les documents pour configurer l’environnement de création. Voir [Prise en main - Tutoriel pour les développeurs](https://www.aem.live/developer/tutorial) pour configurer l’environnement de création.

### Intégration d’AEM Assets à l’environnement de création basé sur les documents{#integrate-aem-assets-with-microsoft-word-or-google-docs-to-use-aem-assets-with-microsoft-word-or-google-docs}

Configurez le plug-in AEM Assets Sidekick pour utiliser les ressources lors de la création de contenu dans Microsoft Word ou Google Docs.

* Consultez [Plug-in Adobe Experience Manager Assets Sidekick](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-experience-manager-assets-for-website-authors) pour savoir comment accéder à AEM Assets et l’utiliser dans Microsoft Word ou Google Docs.
* Voir [Configuration du plug-in Adobe Experience Manager Assets Sidekick](https://www.aem.live/developer/configuring-aem-assets-sidekick-plugin) pour plus d’informations sur la configuration.
  ![utilisez dynamic media avec les fonctionnalités openAPI dans ms word et google docs](/help/assets/assets/my-assets-sidebar.png)

## Diffusion de ressources à l’aide de Dynamic Media avec des fonctionnalités OpenAPI {#integrate-Dynamic-Media-with-OpenAPI-capabilities-with-Microsoft-Word-Google-Docs-and-universal-editor}

Vous pouvez également utiliser les ressources diffusées à l’aide de DM avec les fonctionnalités OpenAPI . Il offre de nombreux avantages, notamment :

* Accès aux ressources approuvées par la marque uniquement (images, vidéos, PDF et autres types de ressources) à partir des services cloud AEM Assets.
* La gouvernance (références ou copies de la ressource), qui permet la propagation automatique d’événements du cycle de vie des ressources tels que l’expiration, la suppression et les mises à jour.
* Rendus d’images dynamiques et recadrage intelligent.
* Optimisation et diffusion des médias riches, telles que la diffusion vidéo adaptative par flux prêt à l’emploi et la diffusion de ressources d’origine pour les PDF.
* Rapport Impressions au niveau des ressources ([disponibilité limitée](/help/assets/manage-reports-assets-view.md#dynamic-media-delivery-reports)).

Pour plus d’informations sur ces fonctionnalités, consultez la documentation [Dynamic Media avec les fonctionnalités OpenAPI](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dynamic-media-open-apis/dynamic-media-open-apis-overview).

### Prérequis {#prerequisites-for-dm-with-openapi-capabilities-to-use-aem-assets}

Pour utiliser la référence de ressource, vous devez disposer des éléments suivants :

* Droit à un environnement Assets Cloud Service dans lequel Dynamic Media avec les fonctionnalités Open API est activé.
* Une licence Dynamic Media.
* Le plug-in AEM Assets sidekick activé avec la référence de copie pour les ressources d’image activée. Pour plus d’informations, consultez les sections [ceci](https://www.aem.live/developer/configuring-aem-assets-sidekick-plugin#copymode) pour la création basée sur des documents et [ceci](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#extension-overview) pour la création basée sur l’éditeur universel.
* Assets approuvées. Les ressources approuvées sont `dam:status=Approved` via le serveur principal Assets Cloud Services ou les actions de l’interface utilisateur.

### Utilisation des ressources diffusées à l’aide de Dynamic Media avec les fonctionnalités OpenAPI{#how-to-use-Dynamic-Media-with-OpenAPI-assets}

Pour utiliser les ressources diffusées à l’aide de Dynamic Media avec des fonctionnalités OpenAPI lors de la création de contenu, consultez :

* [Utilisation des références d’image](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-image-references-when-authoring-content)
* [Utilisation de références vidéo](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-video-references-when-authoring-content)
* [Utilisation des références de ressources pour les ressources vidéo et non-images telles que les PDF, les fichiers Zip, etc](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-asset-references-for-pdf-zip-etc-when-authoring-content)

Regardez cette vidéo pour découvrir comment diffuser des ressources à l’aide de Dynamic Media avec les fonctionnalités OpenAPI.

>[!VIDEO](https://video.tv.adobe.com/v/3441155)

## Exemple de site Edge Delivery Services{#example-of-an-Edge-Delivery-Services-site}

Voir [Voyage WKND](http://bit.ly/3DExLnf). Ce site est créé à l’aide des fonctionnalités de création documentaire de Edge Delivery Services. Le contenu du site est créé dans [Google Docs](https://drive.google.com/drive/folders/1HCCHRWp4HJIXW_cUv5cRDQ5DzzqiZsXT) à l’aide de Dynamic Media avec des fonctionnalités OpenAPI pour la diffusion de ressources. Une fois créé, le contenu est publié directement à partir du document. Pour cette configuration de création basée sur des documents, tous les fichiers, dossiers, configurations, codes de style et de fonctionnalité essentiels du site web sont stockés dans ce [référentiel Git](https://github.com/hlxsites/franklin-assets-selector/tree/aem-dynamicmedia-demo/blocks).

## Intégration d’AEM Assets aux flux de création basés sur l’éditeur universel pour Edge Delivery Services {#integrate-aem-assets-with-universal-editor}

Configurez l’éditeur universel pour l’intégration à AEM Assets. Cette intégration vous permet d’utiliser Dynamic Media avec des fonctionnalités OpenAPI pour diffuser des ressources.

* Voir [Configuration dans Edge Delivery Site](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#configuration-in-edge-delivery-site) pour ajouter une fonction de sélecteur de ressources personnalisée dans l’éditeur universel. Le sélecteur de ressources personnalisé vous permet d’insérer directement des ressources dans votre contenu de l’éditeur universel.
* Voir [Présentation de l’extension](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#extension-overview) pour savoir comment accéder à AEM Assets et insérer les ressources lors de la création dans l’éditeur universel.
