---
title: Configuration du sélecteur Assets pour l’éditeur universel
description: Découvrez comment configurer le sélecteur de ressources à utiliser avec l’éditeur universel.
feature: Developing
role: Admin, Developer
exl-id: 0bf7b418-5ecd-454f-ac46-03792268c59c
source-git-commit: a03eb72ee1b46756f003a60709019aa3122d26f2
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Configuration du sélecteur Assets pour l’éditeur universel {#configure-assets-selector}

Découvrez comment configurer le sélecteur de ressources à utiliser avec l’éditeur universel.

## Vue d’ensemble {#overview}

L’éditeur universel utilise le sélecteur de ressources pour permettre aux auteurs de parcourir et de sélectionner des ressources à insérer dans leur contenu.

Le sélecteur de ressources peut être configuré dans l’éditeur universel à l’aide de [filtres de composant.](/help/implementing/universal-editor/filtering.md) Ce document décrit les options de configuration disponibles.

>[!NOTE]
>
>Lorsque vous démarrez un projet d’éditeur universel, aucun filtre n’est en place pour le sélecteur de ressources. Les auteurs auront accès à toutes les ressources que leurs autorisations utilisateur autorisent normalement.

## Définition du filtre {#filter-definition}

La définition du filtre du sélecteur de ressources présente une structure simple.

```json
[
  {
    "id": "assets-filter",
    "assets": {...}
   }
]
```

## Options de filtre {#filter-options}

Le filtre `assets` peut avoir les options suivantes.

* `deliveryTier?` : - définit le niveau de diffusion à utiliser parmi les suivants :
   * `dm` : Dynamic Media (préféré) avec option de secours à `publish` si nécessaire
   * `publish` : instance de publication AEM
* `repoNames?` : chaîne - liste des référentiels AEM qui peuvent être utilisés pour sélectionner des images.
   * Par défaut : tous les référentiels de diffusion
* `selectionTier?` : chaîne - niveaux AEM à partir desquels sélectionner des ressources
   * Valeur par défaut : `["author", "delivery"]`
* `disableRemote?` : booléen - Désactivation de la prise en charge du référentiel distant
* `preselectedTypes?` : chaîne - types de fichiers présélectionnés à appliquer comme filtre par défaut dans le sélecteur de ressources.
* `minMaxDimensions?` : objet : fournit des dimensions minimales et/ou maximales (en pixels) à appliquer en tant que filtre par défaut dans le sélecteur de ressources.
   * `widthMin?` : Nombre - Largeur minimale
   * `widthMax?` : Nombre - Largeur maximale
   * `heightMin?` : Nombre - Hauteur minimale
   * `heightMax?` : Nombre - Hauteur maximale
* `minMaxFileSize?` : objet - Indiquez la taille de fichier minimale et/ou maximale (en octets) à appliquer comme filtre par défaut dans le sélecteur de ressources.
   * `min?` : nombre - taille de fichier minimale
   * `max?` : nombre - Taille maximale du fichier
* `customFileTypeFilters?` : objet - fournit des filtres de type de fichier personnalisés à afficher dans le sélecteur de ressources.
   * `label` : chaîne - libellé à afficher dans l’interface utilisateur de sélection de la ressource.
   * `value` : chaîne - valeur du type de fichier à filtrer.
* `displayFilters?` : booléen - utilisé pour désactiver l’interface utilisateur des filtres dans le sélecteur de ressources ; true par défaut

## Exemple {#example}

L’exemple suivant contient la plupart des options à des fins d’illustration.

```json
[
  {
    "id": "assets-filter",
    "assets": {
      "deliveryTier": "dm",
      "repoNames": ["thisRepo", "thatRepo"],
      "selectionTier": ["author", "delivery"],
      "disableRemote": true,
      "preselectedTypes": ["png", "svg", "jpg", "gif"],
      "minMaxDimensions": {
        "widthMin": 640,
        "widthMax": 640,
        "heightMin": 480,
        "heightMax": 480
      },
      "minMaxFileSize": {
        "min": 1024,
        "max": 1024
      }
    }
   }
]
```

<!--

## Additional Resources {#additional-resources}

For details on the assets selector, please see the document [Micro-Frontend Asset Selector](/help/assets/overview-asset-selector.md#using-asset-selector) in the assets documentation.

-->
