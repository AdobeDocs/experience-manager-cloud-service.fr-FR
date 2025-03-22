---
title: Utilisation de sélecteurs
description: Découvrez les méthodes que vous pouvez utiliser pour sélectionner des ressources sous forme d’images interactives, de vidéos interactives et de bannières de carrousel dans Dynamic Media.
contentOwner: Rick Brough
feature: Selectors,Interactive Images,Interactive Videos,Carousel Banners
role: User
exl-id: a6f366ab-41b8-4909-b815-e6c4b938bf77
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 96%

---

# Utilisation de sélecteurs dans Dynamic Media {#working-with-selectors}

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

Lorsque vous utilisez une image interactive, une vidéo interactive ou une bannière de carrousel, vous sélectionnez des ressources, ainsi que des sites et des produits auxquels relier les zones réactives et les zones cliquables. Lorsque vous travaillez avec des visionneuses d’images, des visionneuses à 360° et de contenu multimédia, vous devez également sélectionner les ressources à l’aide du sélecteur de ressources.

Cette rubrique décrit comment utiliser les sélecteurs de produits, de sites et de ressources, y compris comment naviguer, filtrer et trier dans les sélecteurs.

Vous accédez aux sélecteurs lorsque vous créez des ensembles de carrousels, vous ajoutez des zones réactives et des zones cliquables et vous créez des vidéos et des images interactives.

Par exemple, dans cette bannière de carrousel, vous utilisez le sélecteur de produits si vous liez une zone réactive ou une zone cliquable à une page d’aperçu rapide. Utilisez le sélecteur de sites si vous liez une zone réactive ou une zone cliquable à un lien hypertexte ; utilisez le sélecteur de ressources lorsque vous créez une diapositive.

![chlimage_1-520](assets/chlimage_1-520.png)

Lorsque vous sélectionnez (au lieu de saisir manuellement) l’emplacement des zones réactives ou des zones cliquables, vous utilisez le sélecteur. Le sélecteur de sites ne fonctionne que si vous êtes client [!DNL Adobe Experience Manager Sites]. Le sélecteur de produits nécessite également [!DNL Experience Manager Commerce].

## Sélection de produits dans Dynamic Media {#selecting-products}

Utilisez le sélecteur de produits pour choisir un produit lorsque vous souhaitez une zone réactive ou une zone cliquable pour proposer l’aperçu rapide d’un produit de votre catalogue de produits.

1. Accédez à l’ensemble de carrousels, à l’image interactive ou à la vidéo interactive, puis sélectionnez l’onglet **[!UICONTROL Actions]** (disponible uniquement si vous avez défini une zone réactive ou une zone cliquable).

   Le sélecteur de produits se trouve dans la zone **[!UICONTROL Type d’action]**.

   ![chlimage_1-521](assets/chlimage_1-521.png)

1. Sélectionnez l’icône du **[!UICONTROL sélecteur de produits]** (loupe) et accédez à un produit dans le catalogue.

   ![chlimage_1-522](assets/chlimage_1-522.png)

   Vous pouvez également filtrer par mot-clé ou balise en appuyant sur **[!UICONTROL Filtrer]** et en entrant des mots-clés ou en sélectionnant des balises, ou les deux à la fois.

   ![chlimage_1-523](assets/chlimage_1-523.png)

   Vous pouvez modifier l’emplacement dans lequel [!DNL Experience Manager] recherche les données de produit en appuyant sur **[!UICONTROL Parcourir]** et en accédant à un autre dossier.

   ![chlimage_1-524](assets/chlimage_1-524.png)

   Sélectionnez **[!UICONTROL Trier par]** pour indiquer si trie du plus récent au plus ancien ou du plus ancien au plus récent.[!DNL Experience Manager]

   ![chlimage_1-525](assets/chlimage_1-525.png)

   Sélectionnez **[!UICONTROL Afficher sous]** pour changer l’affichage des produits (**[!UICONTROL Vue Liste]** ou **[!UICONTROL Vue Carte]**).

   ![chlimage_1-526](assets/chlimage_1-526.png)

1. Une fois le produit sélectionné, le champ reçoit la miniature et le nom du produit.

   ![chlimage_1-527](assets/chlimage_1-527.png)

1. En mode **[!UICONTROL Aperçu]**, vous pouvez sélectionner la zone réactive ou la zone cliquable et voir l’aspect de l’aperçu rapide.

   ![chlimage_1-528](assets/chlimage_1-528.png)

## Sélection de sites dans Dynamic Media {#selecting-sites}

Utilisez le sélecteur de sites pour choisir une page web lorsque vous souhaitez qu’une zone réactive ou une zone cliquable pointe vers une page web gérée dans les sites [!DNL Experience Manager].

1. Accédez à l’ensemble de carrousels, à l’image interactive ou à la vidéo interactive, puis sélectionnez l’onglet **[!UICONTROL Actions]** (disponible uniquement si vous avez défini une zone réactive ou une zone cliquable).

   Le sélecteur de sites se trouve dans la zone **[!UICONTROL Type d’action]**.

   ![chlimage_1-529](assets/chlimage_1-529.png)

1. Sélectionnez l’icône **[!UICONTROL Sélecteur de sites]** (dossier avec loupe) et accédez à une page de vos sites à laquelle vous voulez relier la zone réactive ou la zone cliquable.[!DNL Experience Manager]

   ![chlimage_1-530](assets/chlimage_1-530.png)

1. Une fois le site sélectionné, le champ reçoit le chemin d’accès.

   ![chlimage_1-531](assets/chlimage_1-531.png)

1. En mode **[!UICONTROL Aperçu]**, si vous sélectionnez la zone réactive ou la zone cliquable, vous accédez à la page de site que vous avez spécifiée.[!DNL Experience Manager]

## Sélection de ressources dans Dynamic Media {#selecting-assets}

Utilisez ce sélecteur pour sélectionner les images à utiliser dans une bannière de carrousel, une vidéo interactive, des visionneuses d’images, de contenus multimédia variés et à 360°. Dans la vidéo interactive, le sélecteur de ressources est disponible lorsque vous sélectionnez **[!UICONTROL Sélectionner des ressources]** dans l’onglet **[!UICONTROL Contenu]**. Dans les ensembles de carrousels, le sélecteur de ressources est disponible lorsque vous créez une diapositive. Dans les visionneuses d’images, de contenus multimédia variés et à 360°, le sélecteur de ressources est disponible lorsque vous créez respectivement une visionneuse d’images, de contenus multimédia variés ou à 360°.

Reportez-vous également à la section [Sélecteur de ressources](/help/assets/search-assets.md#asset-selector) pour plus d’informations.

1. Accédez à l’ensemble de carrousels et créez une diapositive. Ou accédez à la vidéo interactive, puis à l’onglet **[!UICONTROL Contenu]**, et sélectionnez des ressources. Vous pouvez également créer des visionneuses de contenu multimédia varié, d’images ou à 360°.
1. Sélectionnez l’icône **[!UICONTROL Sélecteur de ressources]** (dossier avec loupe) et accédez à une ressource.

   ![chlimage_1-532](assets/chlimage_1-532.png)

   Filtrez par mot-clé ou balise en appuyant sur **[!UICONTROL Filtrer]** et en entrant des mots-clés ou en ajoutant des critères, ou les deux à la fois.

   ![chlimage_1-533](assets/chlimage_1-533.png)

   Vous pouvez modifier l’emplacement où [!DNL Experience Manager] recherche les ressources en accédant à un autre dossier dans le champ **[!UICONTROL Chemin]**.

   Sélectionnez **[!UICONTROL Collection]** pour rechercher uniquement des ressources dans les collections.

   ![chlimage_1-534](assets/chlimage_1-534.png)

   Sélectionnez **[!UICONTROL Afficher sous]** pour changer l’affichage des produits (**[!UICONTROL Vue Liste]**, **[!UICONTROL Vue Colonne]** ou **[!UICONTROL Vue Carte]**).

   ![chlimage_1-535](assets/chlimage_1-535.png)

1. Pour sélectionner la ressource, sélectionnez la coche. La ressource s’affiche.

   ![chlimage_1-536](assets/chlimage_1-536.png)
-->
