---
title: Collections du sélecteur de ressources
description: Utilisation des collections de sélecteurs de ressources.
role: Admin,User
exl-id: 1687e7d5-eb7e-4eb7-8747-e5dc6afacd5b
source-git-commit: 9c1104f449dc2ec625926925ef8c95976f1faf3d
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 7%

---

# Collections du sélecteur de ressources {#asset-selector-collections}

Une collection est un ensemble de ressources, de dossiers ou d’autres collections dans le sélecteur de ressources. Vous pouvez utiliser des collections pour partager des ressources entre utilisateurs. Contrairement aux dossiers, une collection peut comporter des ressources provenant de différents emplacements.

Les Collections front-end micro dans le sélecteur de ressources sont disponibles prêtes à l’emploi en mode lecture seule. Il récupère les ressources et les collections directement à partir du référentiel [!DNL Experience Manager Assets] auquel vous avez accès.

>[!NOTE]
>
>Assurez-vous de disposer des autorisations d’accès à une [!DNL Experience Manager Assets] [imsOrg](/help/assets/asset-selector-properties.md) et à des collections.

Les Collections front-end micro dans le sélecteur de ressources sont disponibles prêtes à l’emploi en mode lecture seule. Il récupère les ressources et les collections directement à partir du référentiel Experience Manager Assets auquel vous avez accès et hérite des propriétés des dossiers publics et privés de votre référentiel Experience Manager Assets. En savoir plus sur la [création d’une collection publique ou privée dans la vue Assets](/help/assets/manage-collections-assets-view.md#create-collection).

Vous pouvez afficher les collections dans le sélecteur de ressources en mode rail et en mode modal.

![Collections en mode rail](assets/collections-rail-modal-view.png)

<!--
Additionally, you can [customize](/help/assets/asset-selector-customization.md) the `featureSet` property to enable or disable collections in Asset Selector. See [enable or disable Collections tab](#enable-disable-collections-tab).-->

De plus, vous pouvez également personnaliser la sélection des ressources sous l’onglet Collections . Pour ce faire, vous pouvez le personnaliser à l’aide de `handleSelection`. Voir [Gestion de la sélection d’Assets à l’aide du schéma d’objet](/help/assets/asset-selector-customization.md#handling-selection).

## Affichage des collections {#view-collections}

Le sélecteur de ressources vous permet d’afficher les collections dans une vue ![ liste](assets/do-not-localize/list-view.png) liste ou ![ grille](assets/do-not-localize/grid-view.png) grille. Voir [types de vue dans le sélecteur de ressources](overview-asset-selector.md#types-of-view).

## Glisser-déposer des ressources dans la collection {#collection-drag-and-drop}

Vous pouvez faire glisser et déposer une ressource dans les collections directement depuis la vue [!DNL Assets as a Cloud Service] de l’environnement de création. Pour ce faire, faites glisser la ressource de l’onglet Assets vers la zone de travail Collections de l’application Sélecteur de ressources pour créer des applications enrichies.

>[!NOTE]
>
>* Le glisser-déposer d’une ressource est possible uniquement en mode rail.
>* Vous pouvez uniquement faire glisser et déposer des fichiers (ressources), et non des dossiers.

D’autre part, vous pouvez également [activer ou désactiver le glisser-déposer de ressources dans les collections](asset-selector-customization.md#enable-disable-drag-and-drop) directement.

## Désactiver la sélection de ressources dans les collections {#disable-selection-collection}

Désactiver la sélection est utilisé pour masquer ou désactiver la sélection des ressources ou des dossiers. Cela masque la case à cocher de sélection de la carte ou de la ressource, ce qui l’empêche d’être sélectionnée. Voir [désactiver la sélection](/help/assets/asset-selector-customization.md#disable-selection).

## Activer ou désactiver l’onglet Collections {#enable-disable-collections-tab}

Le sélecteur de ressources vous permet de personnaliser les composants en fonction des besoins et de la convivialité. Pour activer ou désactiver l’onglet Collections dans le sélecteur de ressources, vous pouvez utiliser `featureSet` propriété comme suit :

* **Activer l’onglet Collections :** pour activer l’onglet Collections, vous devez fournir des `collections` en tant que valeur au tableau . Par défaut, l’onglet Collections est prêt à l’emploi pour tous les utilisateurs. Par exemple, `featureSet:["collections"]`.
* **Désactiver l’onglet Collections :** pour désactiver l’onglet Collections, vous devez fournir un tableau vide comme valeur. Par exemple, `featureSet:[ ]`.

>[!MORELIKETHIS]
>
>* [Personnalisation du sélecteur de ressources](/help/assets/asset-selector-customization.md)
>* [Intégration du sélecteur de ressources à diverses applications](/help/assets/integrate-asset-selector.md)
>* [Propriétés du sélecteur de ressources](/help/assets/asset-selector-properties.md)
