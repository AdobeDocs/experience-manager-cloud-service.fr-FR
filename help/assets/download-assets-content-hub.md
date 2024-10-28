---
title: Téléchargement de ressources à partir de Content Hub
description: Découvrez comment télécharger des ressources à partir du portail Content Hub
role: User
exl-id: 96d4ffba-4e3e-4496-9da2-6eb36be8331f
source-git-commit: 96b7b7fe32aefc81a9fde15d79e9089f71cb5d31
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 4%

---

# Téléchargement de ressources à partir de Content Hub {#download-assets}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [Bonnes pratiques relatives aux métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Fonctionnalités Dynamic Media avec OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation de développement pour AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

<!-- ![Download assets](assets/download-asset.jpg) -->
![Téléchargement de ressources](assets/download-asset-genstudio.jpeg)

Content Hub vous permet de télécharger et de partager vos ressources. Ces ressources peuvent inclure des images, des vidéos ou tout autre contenu numérique. Content Hub améliore l’accessibilité et l’adaptabilité pour une distribution efficace des ressources.

Vous pouvez télécharger une ou plusieurs ressources à l’aide de Content Hub. Les versions d’origine de la ressource sont téléchargées.

## Conditions préalables {#prerequisites}

[Les utilisateurs de Content Hub](deploy-content-hub.md#onboard-content-hub-users) peuvent effectuer les actions mentionnées dans cet article.

## Télécharger une ressource {#download-single-asset}

[Approuvez la licence de la ressource](/help/assets/approve-assets-content-hub.md) avant de la télécharger.

### Téléchargement unique {#single-download-asset}

Sélectionnez une ressource et cliquez sur ![télécharger](/help/assets/assets/download-icon.svg) dans le rail supérieur. La boîte de dialogue Télécharger la ressource affiche la licence de la ressource. Acceptez les conditions et conditions de licence et cliquez sur **Télécharger**.
Vous pouvez également cliquer sur ![télécharger](/help/assets/assets/download-icon.svg) dans la carte de ressource pour télécharger la ressource.

#### Téléchargement de ressource unique à partir de la boîte de dialogue Ressource {#single-download-from-asset-dialog-box}

1. Cliquez sur la miniature de la ressource. La boîte de dialogue Ressource s’affiche.
1. Cliquez sur ![télécharger](/help/assets/assets/download-icon.svg) dans la barre d’outils la plus à droite. Le volet de téléchargement affiche les rendus de ressources et la case à cocher d’acceptation des conditions et conditions de licence.
   ![single-download-dialog-box](/help/assets/assets/asset-dialog-box-for-single-download.png)
   * Cliquez sur le lien Conditions générales pour afficher les conditions de licence dans le volet de gauche.

     >[!NOTE]
     >
     >La case à cocher Conditions générales s’affiche uniquement pour les ressources sous licence. En outre, la boîte de dialogue Ressource affiche un aperçu des conditions de licence uniquement pour les ressources avec des licences approuvées. [Approuvez la licence de la ressource](/help/assets/approve-assets-content-hub.md) avant de la télécharger pour activer l’aperçu des termes de la licence dans la boîte de dialogue de la ressource.

   * Cliquez sur la **boîte de rendu d’origine** pour revenir au rendu de ressource d’origine dans le volet de gauche.
1. Acceptez les conditions de licence (pour la ressource sous licence) et cliquez sur **Télécharger** pour télécharger la ressource.

### Téléchargement multiple {#multi-download}

1. Sélectionnez les ressources et cliquez sur ![télécharger](/help/assets/assets/download-icon.svg) dans le rail supérieur. La boîte de dialogue qui s’affiche varie selon que la liste de téléchargement inclut des ressources expirées ou uniquement des ressources non expirées. <br/>
   **Boîte de dialogue Télécharger les ressources expirées :** Cette boîte de dialogue affiche l’aperçu des ressources expirées avec leur date d’expiration dans le volet de gauche. Le nombre de ressources expirées sur le total sélectionné s’affiche dans le volet de droite. Cliquez sur **Continuer avec toutes les ressources** pour télécharger les ressources expirées avec d’autres ressources (le cas échéant). La boîte de dialogue Télécharger les ressources s’affiche. Voir la [boîte de dialogue Télécharger des ressources](#Download-asset-dialog-box) pour continuer.

   >[!NOTE]
   >
   >[Activez l’option de téléchargement pour les ressources expirées](/help/assets/configure-content-hub-ui-options.md#expired-assets-content-hub) pour les télécharger. Seules les ressources expirées ayant activé le téléchargement sont disponibles.

   <a id="Download-asset-dialog-box"></a> **Boîte de dialogue Télécharger les ressources :** Cette boîte de dialogue affiche la liste des licences associées aux ressources sélectionnées dans le volet de gauche. Sélectionnez une licence pour prévisualiser ses conditions générales (au format pdf) dans le volet central, l’aperçu des ressources associées et leur comptage dans le volet de droite. Les licences révisées sont surlignées en bleu clair.

   >[!NOTE]
   >
   > La **boîte de dialogue Télécharger les ressources** prévisualise les conditions et conditions de licence uniquement pour les licences approuvées. [Approuvez les licences des ressources](/help/assets/approve-assets-content-hub.md) avant de les télécharger afin de prévisualiser leurs conditions de licence dans la **boîte de dialogue Télécharger la ressource**.

1. Cliquez sur ![remove-icon](/help/assets/assets/remove-icon.svg) pour supprimer une licence de la boîte de dialogue de téléchargement.

1. Acceptez les conditions générales, puis cliquez sur **Télécharger** pour télécharger les ressources associées aux licences disponibles dans le volet de gauche.
   ![download-multiple-license](/help/assets/assets/download-multiple-license.png)

### Téléchargement de ressources sans licence {#download-non-licensed-assets}

Pour télécharger des ressources sans licence, sélectionnez-les et cliquez sur ![télécharger](/help/assets/assets/download-icon.svg) dans le rail supérieur.







