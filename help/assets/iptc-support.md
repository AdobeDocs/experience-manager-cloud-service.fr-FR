---
title: Prise en charge des métadonnées IPTC
description: Découvrez comment Adobe Experience Manager (AEM) Assets prend en charge les métadonnées IPTC, les évaluations des créations et les mots-clés ajoutés aux ressources par Adobe Bridge et d’autres applications de création.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Prise en charge des métadonnées IPTC {#support-for-iptc-metadata}

Découvrez comment Adobe Experience Manager (AEM) Assets prend en charge les métadonnées IPTC, les évaluations des créations et les mots-clés ajoutés aux ressources par Adobe Bridge et d’autres applications de création.

Les ressources Adobe Experience Manager (AEM) prennent en charge la norme de métadonnées IPTC largement utilisée pour décrire les ressources. Cela permet à AEM Assets de bénéficier d’une plus large acceptation de ses images auprès des différents intervenants, y compris les photographes, les agences de création, les bibliothèques, les musées, etc.

Le schéma de métadonnées utilisé pour les ressources intègre désormais IPTC Core et IPTC Extension, deux schémas permettant de définir des propriétés de métadonnées complètes, grâce auxquels les utilisateurs peuvent ajouter des données fiables et précises sur les personnes, les lieux et les produits illustrés dans une image. Il prend également en charge les dates, noms et identifiants relatifs à la création de l’image, ainsi qu’une méthode permettant d’exprimer les informations sur les droits avec une certaine souplesse.

La page des propriétés des ressources comprend maintenant des onglets distincts pour afficher les métadonnées IPTC Core et IPTC Extension dans des champs modifiables.

1. Sélectionnez une image dans l’interface utilisateur Assets.
1. Dans la barre d’outils, cliquez ou appuyez sur l’icône **[!UICONTROL Propriétés]**.
1. In the Properties page, click/tap the **[!UICONTROL IPTC]** tab to view IPTC metadata for the asset.
1. Modifiez les propriétés de métadonnées IPTC, selon les besoins.

   ![iptc_tab](assets/iptc_tab.png)

1. Click/tap the **[!UICONTROL IPTC Extension]** tab to view IPTC Extension metadata for the asset.
1. Modifiez les propriétés de métadonnées d’extension IPTC, selon les besoins.
1. Tap/click **[!UICONTROL Save &amp; Close]** to save the changes.

## Prise en charge de l’évaluation de la création {#creative-rating-support}

Outre les évaluations individuelles et cumulées, la page Propriétés affiche désormais les évaluations affectées à des ressources par le biais d’Adobe Bridge et d’autres applications Creative.

These ratings are available under **[!UICONTROL Creative Rating]** section within the **[!UICONTROL Advanced]** tab.

Cette évaluation est une propriété en lecture seule dont la valeur est comprise entre 1 et 5. Vous pouvez rechercher des ressources en fonction de leur évaluation de création dans le panneau Rechercher.

Notez toutefois que cette propriété n’est pas indexée pour l’instant et ce, afin d’éviter tout conflit avec les modifications personnalisées apportées par les utilisateurs.

## Prise en charge des mots-clés {#keyword-support}

L’onglet **[!UICONTROL IPTC]** de la page Propriétés affiche également les mots-clés ajoutés aux ressources au moyen d’Adobe Bridge et d’autres applications Creative. Vous pouvez aussi modifier ces mots-clés et en ajouter d’autres à partir de l’onglet **[!UICONTROL IPTC]**.

![keywords](assets/keywords.png)

