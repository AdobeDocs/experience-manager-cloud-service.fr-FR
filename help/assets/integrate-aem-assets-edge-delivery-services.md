---
title: Intégration lors  [!DNL AEM Assets]  la création de contenu pour  [!DNL Edge Delivery Services]
description: Découvrez comment intégrer le [!DNL AEM Assets] avec [!DNL Edge Delivery Services]. This integration enables you to integrate [!DNL AEM Assets]  [!DNL Microsoft Word]  et [!DNL Google Docs], integrate [!DNL AEM Assets] avec [!DNL Universal Editor], integrate [!DNL Dynamic Media with OpenAPI capabilities] avec [!DNL Universal Editor] et l’intégrer [!DNL Dynamic Media with OpenAPI capabilities] avec [!DNL Microsoft Word] et [!DNL Google Docs].
exl-id: e58db2ce-a55a-49b3-ae8e-709b5ea8d095
source-git-commit: 2de6352363959f4258c0786910eaef7babe68f15
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 3%

---

# Intégration de [!DNL AEM Assets] lors de la création de contenu pour [!DNL Edge Delivery Services] {#integrate-aem-assets-while-authoring-for-edge-delivery-services}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime et Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Extensibilité de l’interface utilisateur</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Activation de Dynamic Media Prime et Ultimate</b></a>
        </td>
         <td>
            <a href="/help/assets/search-best-practices.md"><b>Bonnes pratiques de recherche</b></a>
        </td>
    </tr>
    <tr>
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

![Ressources AEM avec UE](/help/assets/assets/EDS2.png)

[[!DNL Edge Delivery Services]](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/edge-delivery/overview) est un ensemble composable de services qui permet un haut degré de flexibilité dans la manière dont vous créez et diffusez du contenu sur votre site web. Vous pouvez utiliser à la fois la [gestion de contenu AEM](/help/sites-cloud/authoring/author-publish.md) et la [création WYSIWYG à l’aide de l [!DNL Universal Editor] outil , ainsi que la création basée sur des documents](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/authoring).

Vous pouvez modifier le contenu dans :

* [[!DNL Microsoft Word] ou  [!DNL Google Docs]](#integrate-aem-assets-with-document-based-authoring-tools)
* [[!DNL Universal Editor]](#integrate-aem-assets-with-UE-universal-editor)

Après avoir modifié le contenu, vous pouvez le publier dans Edge Delivery Services.

## Intégration de [!DNL AEM Assets] aux flux de création basés sur des documents pour [!DNL Edge Delivery Services] {#integrate-aem-assets-with-document-based-authoring-tools}

Lorsque [!DNL AEM Assets] s’intègre à vos outils de création basés sur des documents, tels que [!DNL Microsoft Word] ou [!DNL Google Docs], il fournit un sélecteur de ressources dans votre outil de création. Utilisez ce sélecteur de ressources pour accéder aux [!DNL AEM Assets] et insérer des ressources approuvées dans votre contenu.
Si vous disposez déjà d’un site web [!DNL Edge Delivery Services], consultez la documentation du [[!DNL AEM Assets] plug-in](https://github.com/adobe-rnd/aem-assets-plugin/blob/main/README.md) pour savoir comment l’intégrer [!DNL AEM Assets] votre projet [!DNL AEM] existant.
Suivez les sections [Conditions préalables](#integrate-aem-assets-with-microsoft-word-and-google-docs) et [Intégration [!DNL AEM Assets] à l’environnement de création basé sur les documents](#integrate-aem-assets-with-microsoft-word-or-google-docs-to-use-aem-assets-with-microsoft-word-or-google-docs) ci-après si vous ne disposez pas d’un site web [!DNL Edge Delivery Services] pour publier votre [!DNL AEM Assets] contenu inclusif créé dans des outils de création basés sur les documents.

### Prérequis{#integrate-aem-assets-with-microsoft-word-and-google-docs}

Avant de commencer, assurez-vous que votre environnement de création basé sur les documents est prêt :

* Intégrez [!DNL AEM] à un outil de création basé sur des documents pour configurer l’environnement de création. Voir [Prise en main - Tutoriel pour les développeurs](https://www.aem.live/developer/tutorial) pour savoir comment configurer l’environnement de création.

### Intégration de [!DNL AEM Assets] à un environnement de création basé sur des documents{#integrate-aem-assets-with-microsoft-word-or-google-docs-to-use-aem-assets-with-microsoft-word-or-google-docs}

Configurez le plug-in [!DNL AEM Assets] Sidekick pour utiliser les ressources lors de la création de contenu dans [!DNL Microsoft Word] ou [!DNL Google Docs].

* Consultez [[!DNL Adobe Experience Manager Assets Sidekick Plugin]](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-experience-manager-assets-for-website-authors) pour savoir comment accéder à AEM Assets et l’utiliser dans Microsoft Word ou Google Docs.
* Voir [Configuration [!DNL Adobe Experience Manager Assets Sidekick Plugin]](https://www.aem.live/developer/configuring-aem-assets-sidekick-plugin) pour les détails de la configuration.
  ![utilisez dynamic media avec les fonctionnalités openAPI dans ms word et google docs](/help/assets/assets/my-assets-sidebar.png)

## Diffusion de ressources à l’aide de [!DNL Dynamic Media with OpenAPI capabilities] {#integrate-Dynamic-Media-with-OpenAPI-capabilities-with-Microsoft-Word-Google-Docs-and-universal-editor}

Vous pouvez également utiliser les ressources diffusées à l’aide de [!DNL Dynamic Media with OpenAPI capabilities]. Il offre de nombreux avantages, notamment :

* Accès aux ressources approuvées par la marque uniquement (images, vidéos, PDF et autres types de ressources) à partir de [!DNL AEM Assets Cloud Services].
* La gouvernance (références ou copies de la ressource), qui permet la propagation automatique d’événements du cycle de vie des ressources tels que l’expiration, la suppression et les mises à jour.
* Rendus d’images dynamiques et recadrage intelligent.
* Optimisation et diffusion des médias riches, telles que la diffusion vidéo adaptative par flux prêt à l’emploi et la diffusion de ressources d’origine pour les PDF.
* Rapport Impressions au niveau des ressources ([disponibilité limitée](/help/assets/manage-reports-assets-view.md#dynamic-media-delivery-reports)).

Pour plus d’informations sur ces fonctionnalités, consultez la documentation [[!DNL Dynamic Media with OpenAPI capabilities]](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dynamic-media-open-apis/dynamic-media-open-apis-overview).

### Prérequis {#prerequisites-for-dm-with-openapi-capabilities-to-use-aem-assets}

Pour utiliser la référence de ressource, vous devez disposer des éléments suivants :

* Droit à un environnement Assets Cloud Service où [!DNL Dynamic Media with Open API capabilities] est activé.
* Une licence [!DNL Dynamic Media].
* [!DNL AEM Assets sidekick plugin] activé avec la référence de copie pour les ressources d’image activée. Pour plus d’informations, consultez [cette documentation](https://www.aem.live/developer/configuring-aem-assets-sidekick-plugin#copymode) pour la création basée sur des documents et [cette documentation](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#extension-overview) pour la création basée sur l’éditeur universel.
* Assets approuvées. Les ressources approuvées sont `dam:status=Approved` via le serveur principal Assets Cloud Services ou les actions de l’interface utilisateur.

### Utilisation des ressources diffusées à l’aide d’[!DNL Dynamic Media with OpenAPI capabilities]{#how-to-use-Dynamic-Media-with-OpenAPI-assets}

Sélectionnez les liens suivants pour savoir comment utiliser [!DNL Dynamic Media with OpenAPI capabilities] pour diffuser des images, des vidéos et d’autres types de ressources dans votre contenu :

* [Ajouter des images à votre contenu](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-image-references-when-authoring-content)
* [Ajouter des vidéos à votre contenu](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-video-references-when-authoring-content)
* [Ajoutez à votre contenu des ressources vidéo et autres que des images, telles que des fichiers PDF et Zip](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-asset-references-for-pdf-zip-etc-when-authoring-content)

Regardez cette vidéo pour découvrir comment diffuser des ressources dans votre contenu à l’aide de Dynamic Media avec les fonctionnalités OpenAPI.

>[!VIDEO](https://video.tv.adobe.com/v/3441155)

## Exemple de site [!DNL Edge Delivery Services]{#example-of-an-Edge-Delivery-Services-site}

Consultez la section [Voyage WKND](http://bit.ly/3DExLnf), un site créé à l’aide des fonctionnalités de création de documents d’[!DNL Edge Delivery Services]. Le contenu du site est créé dans [Google Docs](https://drive.google.com/drive/folders/1HCCHRWp4HJIXW_cUv5cRDQ5DzzqiZsXT) et [!DNL Dynamic Media with OpenAPI capabilities] est utilisé pour diffuser des ressources dans le contenu. Après la création, le contenu est directement publié à partir du document. Explorez ce [référentiel Git](https://github.com/hlxsites/franklin-assets-selector/tree/aem-dynamicmedia-demo/blocks) pour en savoir plus sur tous les fichiers, dossiers, configurations, codes de style et de fonctionnalité essentiels utilisés pour créer la configuration de création basée sur des documents pour ce site [!DNL Edge Delivery Services (EDS)].

## Intégration de [!DNL AEM Assets] aux flux de création basés sur [!DNL Universal Editor] pour [!DNL Edge Delivery Services] {#integrate-aem-assets-with-UE-universal-editor}

Configurez le [!DNL Universal Editor] à intégrer à [!DNL AEM Assets]. Cette intégration vous permet d’utiliser [!DNL Dynamic Media with OpenAPI capabilities] pour diffuser des ressources.

* Voir [Configuration dans le site [!DNL Edge Delivery]  ](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#configuration-in-edge-delivery-site) pour savoir comment ajouter une fonction de sélecteur de ressources personnalisée dans [!DNL Universal Editor]. Le sélecteur de ressources personnalisé vous permet d’insérer directement des ressources dans votre contenu [!DNL Universal Editor].
* Consultez [ Présentation de l’extension ](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#extension-overview) pour savoir comment accéder à [!DNL AEM Assets] et insérer les ressources lors de la création dans [!DNL Universal Editor].
