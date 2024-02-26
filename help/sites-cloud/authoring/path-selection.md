---
title: Sélection du chemin avec l’Explorateur de chemins d’accès
description: Découvrez comment utiliser l’explorateur de chemins d’accès pour sélectionner des ressources dans AEM.
source-git-commit: bbd845079cb688dc3e62e2cf6b1a63c49a92f6b4
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 43%

---


# Sélection du chemin d’accès {#path-selection}

Lors de la création, il est souvent nécessaire de sélectionner une autre ressource, par exemple lors de la définition d&#39;un lien vers une autre page ou de la sélection d&#39;une image. Pour sélectionner facilement un chemin d’accès, les [Champs de chemin d’accès](#path-fields) permettent la saisie automatique et l’[explorateur de chemins d’accès](#path-browser) permet une sélection plus robuste.

## Champs de chemin d’accès {#path-fields}

L’exemple utilisé ici pour illustrer est le composant d’image. Pour plus d’informations sur l’utilisation et la modification des composants, voir [Composants pour la création de pages.](/help/sites-cloud/authoring/page-editor/components.md)

Les champs de chemin d’accès disposent d’une fonctionnalité de saisie automatique et d’anticipation pour faciliter la localisation d’une ressource.

Si vous cliquez sur le bouton **Ouvrir la boîte de dialogue de sélection** dans le champ de chemin d’accès, la boîte de dialogue [Explorateur de chemins d’accès](#path-browser) s’ouvre pour vous permettre d’accéder à des options de sélection plus détaillées.

![Bouton Ouvrir la boîte de dialogue de sélection](assets/path-selection-open-selection-dialog.png)

Vous pouvez également effectuer une saisie dans le champ de chemin d’accès. AEM vous proposera alors les chemins d’accès correspondants au fil de la saisie.

![Bouton Ouvrir la boîte de dialogue de sélection](assets/path-selection-open-selection-dialog.png)

## Explorateur de chemins d’accès {#path-browser}

L’explorateur de chemins d’accès est organisé de la manière suivante : [mode colonne](/help/sites-cloud/authoring/basic-handling.md#column-view) de [**Sites** console,](/help/sites-cloud/authoring/sites-console/introduction.md) permettant une sélection plus détaillée des ressources.

![Explorateur de chemins d’accès](/help/sites-cloud/authoring/assets/path-browser.png)

* Une fois une ressource sélectionnée, la variable **Sélectionner** dans l’angle supérieur droit de la boîte de dialogue devient actif.
   * Sélectionnez cette option pour confirmer la sélection ou **Annuler** pour abandonner.
* Si le contexte permet la sélection de plusieurs ressources, la sélection d’une ressource active également la fonction **Sélectionner** , mais ajoute également le nombre de ressources sélectionnées en haut à droite de la fenêtre.
   * Cliquez sur le **X** en regard du nombre pour tout désélectionner.
* Lorsque vous naviguez dans l’arborescence, votre emplacement est reflété dans le chemin de navigation en haut de la boîte de dialogue.
   * Ces chemins de navigation peuvent également être utilisés pour accéder rapidement à la hiérarchie des ressources.
* Vous pouvez à tout moment utiliser le champ de recherche situé en haut de la boîte de dialogue.
   * Cliquez sur le **X** dans le champ de recherche pour effacer la recherche.
* Pour affiner votre recherche, vous pouvez afficher les options de filtre et filtrer vos résultats en fonction du chemin d’accès.

![Option Filtres](assets/path-selection-filters.png)
