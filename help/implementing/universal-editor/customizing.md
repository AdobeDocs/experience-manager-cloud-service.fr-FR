---
title: Personnalisation de l’expérience de création de l’éditeur universel
description: Découvrez les différents points d’extension et autres fonctionnalités qui vous permettent de personnaliser l’interface utilisateur d’Universal Editor afin de prendre en charge les besoins de vos auteurs de contenu.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
source-git-commit: 11a244b7dd4810fbfec92b3effc362102e7322dc
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# Personnalisation de l’expérience de création de l’éditeur universel {#customizing-ue}

Découvrez les différents points d’extension et autres fonctionnalités qui vous permettent de personnaliser l’expérience de création d’Universal Editor afin de prendre en charge les besoins de vos auteurs de contenu.

## Désactivation de la publication {#disable-publish}

Certains workflows de création nécessitent que le contenu soit examiné avant d’être publié. Dans ce cas, l’option de publication ne doit être disponible pour aucun auteur.

La variable **Publier** peut donc être entièrement supprimé dans une application en ajoutant les métadonnées suivantes.

```html
<meta name="urn:adobe:aue:config:disable" content="publish"/>
```

## Filtrage des composants {#filtering-components}

Lorsque vous utilisez l’éditeur universel, vous pouvez limiter les composants autorisés par composant de conteneur. Pour ce faire, vous devez introduire une balise de script supplémentaire, qui pointe vers la définition de filtre.

```html
<script type="application/vnd.adobe.aue.filter+json" src="/static/filter-definition.json"></script>
```

Une définition de filtre peut se présenter comme suit, ce qui limite un conteneur pour qu’il n’autorise que l’ajout de texte et d’images.

```json
[
  {
    "id": "container-filter",
     "components": ["text", "image"]
   }
]
```

Vous pouvez ensuite référencer la définition de filtre à partir de votre composant de conteneur en ajoutant la propriété . `data-aue-filter`, en transmettant l’identifiant du filtre que vous avez défini précédemment.

```html
data-aue-filter="container-filter"
```

La définition de la variable `components` dans une définition de filtre à `null` autorise tous les composants, comme s’il n’existait aucun filtre.

```json
[
  {
    "id": "another-container-filter",
     "components": null
   }
]
```

## Afficher et masquer les composants de manière conditionnelle dans le rail des propriétés {#conditionally-hide}

Bien qu’un ou plusieurs composants puissent généralement être disponibles pour les auteurs, il peut arriver qu’ils n’aient pas de sens dans certains cas. Dans ce cas, vous pouvez masquer des composants dans le rail de propriétés en ajoutant une `condition` à l’attribut [des champs du modèle de composant.](/help/implementing/universal-editor/field-types.md#fields)

Les conditions peuvent être définies à l’aide de [Schéma JsonLogic.](https://jsonlogic.com/) Si la condition est vraie, le champ s’affiche. Si la condition est fausse, le champ est masqué.

### Exemple de modèle {#sample-model}

```json
 {
    "id": "conditionally-revealed-component",
    "fields": [
      {
        "component": "boolean",
        "label": "Shall the text field be revealed?",
        "name": "reveal",
        "valueType": "boolean"
      },
      {
        "component": "text-input",
        "label": "Hidden text field",
        "name": "hidden-text",
        "valueType": "string",
        "condition": { "===": [{"var" : "reveal"}, true] }
      }
    ]
 }
```

#### Condition False {#false}

![Champ de texte masqué](assets/hidden.png)

#### Condition True {#true}

![Champ de texte affiché](assets/shown.png)

