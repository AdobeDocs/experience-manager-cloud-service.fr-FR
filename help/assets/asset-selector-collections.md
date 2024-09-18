---
title: Sélecteur de ressources pour [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]
description: Utilisez le sélecteur de ressources pour rechercher, trouver et récupérer les métadonnées et les rendus des ressources dans votre application.
role: Admin,User
source-git-commit: 63174176c944195ed21e481264e0a50062fd34f3
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 8%

---


# Collections de sélecteurs de ressources {#asset-selector-collections}

Une collection est un ensemble de ressources, de dossiers ou d’autres collections dans le sélecteur de ressources. Vous pouvez utiliser des collections pour partager des ressources entre utilisateurs. Contrairement aux dossiers, une collection peut comporter des ressources provenant de différents emplacements.

Les mini-collections front-end dans le sélecteur de ressources sont disponibles en lecture seule, prêtes à l’emploi. Il récupère les ressources et les collections directement à partir du référentiel [!DNL Experience Manager Assets] auquel vous avez accès.

>[!NOTE]
>
>Assurez-vous que vous disposez des autorisations nécessaires pour accéder à [!DNL Experience Manager Assets] [imsOrg](/help/assets/asset-selector-properties.md) et à des collections.

Les mini-collections front-end dans le sélecteur de ressources sont disponibles en lecture seule, prêtes à l’emploi. Il récupère les ressources et les collections directement à partir du référentiel Experience Manager Assets auquel vous avez accès et hérite des propriétés des dossiers publics et privés de votre référentiel Experience Manager Assets. Pour en savoir plus sur la [création d’une collection publique ou privée dans la vue Assets](/help/assets/manage-collections-assets-view.md#create-collection).

Vous pouvez afficher les collections dans le sélecteur de ressources en mode rail et en mode modal.

![Collections dans la vue de rail](assets/collections-rail-modal-view.png)

<!--
Additionally, you can [customize](/help/assets/asset-selector-customization.md) the `featureSet` property to enable or disable collections in Asset Selector. See [enable or disable Collections tab](#enable-disable-collections-tab).-->

De plus, vous pouvez personnaliser la sélection des ressources sous l’onglet Collections . Pour ce faire, vous pouvez le personnaliser à l’aide de `handleSelection`. Voir [gestion de la sélection d’Assets à l’aide du schéma d’objet](/help/assets/asset-selector-customization.md#handling-selection).

## Affichage des collections {#view-collections}

Le sélecteur de ressources vous permet d’afficher les collections dans une vue de liste ![list view](assets/do-not-localize/list-view.png) ou dans une vue de grille ![grid view](assets/do-not-localize/grid-view.png). Voir [types d’affichage dans le sélecteur de ressources](overview-asset-selector.md#types-of-view).

## Glisser-déposer des ressources dans la collection {#collection-drag-and-drop}

Vous pouvez faire glisser et déposer une ressource vers Collections directement depuis la vue [!DNL Assets as a Cloud Service] dans l’environnement de création. Pour ce faire, faites glisser la ressource de l’onglet Assets vers la zone de travail Collections de l’application Sélecteur de ressources afin de créer des applications enrichies.

>[!NOTE]
>
>* Le déplacement d’une ressource n’est possible que dans la vue rail.
>* Vous ne pouvez faire glisser et déposer des fichiers que (ressources) et non les dossiers.

D’un autre côté, vous pouvez également [activer ou désactiver le glisser-déposer des ressources dans les collections](asset-selector-customization.md#enable-disable-drag-and-drop) directement.

## Désactivation de la sélection de ressources dans les collections {#disable-selection-collection}

L’option Désactiver la sélection permet de masquer ou de désactiver la sélection des ressources ou des dossiers. Elle masque la case à cocher de la carte ou de la ressource qui l’empêche d’être sélectionnée. Voir [désactiver la sélection](/help/assets/asset-selector-customization.md#disable-selection).

## Activation ou désactivation de l’onglet Collections {#enable-disable-collections-tab}

Le sélecteur de ressources vous permet de personnaliser les composants en fonction des besoins et de la convivialité. Pour activer ou désactiver l’onglet Collections dans le sélecteur de ressources, vous pouvez utiliser la propriété `featureSet` de la manière suivante :

* **Activer l’onglet Collections :** Pour activer l’onglet Collections, vous devez fournir `collections` comme valeur au tableau. Par défaut, l’onglet Collections est activé par défaut pour tous les utilisateurs. Par exemple, `featureSet:["collections"]`.
* **Désactiver l’onglet Collections :** Pour désactiver l’onglet Collections, vous devez fournir un tableau vide comme valeur. Par exemple, `featureSet:[ ]`.

>[!MORELIKETHIS]
>
>* [Personnalisation du sélecteur de ressources](/help/assets/asset-selector-customization.md)
>* [Intégrer le sélecteur de ressources à diverses applications](/help/assets/integrate-asset-selector.md)
>* [Propriétés du sélecteur de ressources](/help/assets/asset-selector-properties.md)

