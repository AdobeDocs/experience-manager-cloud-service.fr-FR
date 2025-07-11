---
title: Personnaliser l’éditeur universel
description: Découvrez les différentes options de personnalisation de l’éditeur universel pour prendre en charge les besoins des auteurs de contenu.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 32b3a125d6370dd591252fde342843d5f9e33cf1
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 2%

---


# Personnaliser l’éditeur universel {#customizing}

Découvrez les différentes options de personnalisation de l’éditeur universel pour prendre en charge les besoins des auteurs de contenu.

>[!TIP]
>
>L’éditeur universel offre également de nombreux points d’extension [&#128279;](/help/implementing/universal-editor/extending.md) qui vous permettent d’étendre ses fonctionnalités pour répondre aux besoins de votre projet.

## Désactivation de la publication {#disable-publish}

Certains workflows de création nécessitent que le contenu soit révisé avant d’être publié. Dans ce cas, l’option de publication ne doit être accessible à aucun auteur.

Le bouton **Publier** peut donc être entièrement supprimé dans une application en ajoutant les métadonnées suivantes.

```html
<meta name="urn:adobe:aue:config:disable" content="publish"/>
```

## Désactivation de la publication à prévisualiser {#publish-preview}

Certains workflows de création peuvent empêcher la publication sur le [service d’aperçu](/help/sites-cloud/authoring/sites-console/previewing-content.md) (le cas échéant).

L’option **Aperçu** dans la fenêtre de publication peut donc être supprimée entièrement dans une application en ajoutant les métadonnées suivantes.

```html
<meta name="urn:adobe:aue:config:disable" content="publish-preview"/>
```

## Désactivation de l’ouverture de la page {#open-page}

Le bouton **Ouvrir la page** peut être entièrement supprimé dans une application en ajoutant les métadonnées suivantes.

```html
<meta name="urn:adobe:aue:config:disable" content="header-open-page" />
```

## Bouton Désactiver les doublons {#duplicate-button}

Certains workflows de création peuvent être amenés à limiter la possibilité pour le créateur ou la créatrice de contenu de dupliquer des composants. Vous pouvez désactiver l’icône [dupliquer](/help/sites-cloud/authoring/universal-editor/navigation.md#duplicate) en ajoutant les métadonnées suivantes.

```html
<meta name="urn:adobe:aue:config:disable" content="duplicate"/>
```

## Modification de votre point d’entrée {#custom-endpoint}

Si vous souhaitez ne pas utiliser le service d’éditeur universel, qui est hébergé par Adobe, mais votre propre version hébergée, vous pouvez le définir dans une balise meta . Consultez le document [Prise en main de l’éditeur universel dans AEM](/help/implementing/universal-editor/getting-started.md##configuration-settings) pour plus d’informations.

## Filtrage des composants {#filtering-components}

Vous pouvez restreindre les composants autorisés par conteneur dans l’éditeur universel à l’aide de filtres de composant. Consultez le document [Filtrage des composants](/help/implementing/universal-editor/filtering.md) pour plus d’informations.

## Affichage et masquage conditionnel des composants dans le panneau Propriétés {#conditionally-hide}

Bien qu’un ou plusieurs composants puissent généralement être disponibles pour les auteurs, il peut y avoir certaines situations où ils ne sont pas pertinents. Dans ce cas, vous pouvez masquer des composants dans le panneau des propriétés en ajoutant un attribut `condition` aux [champs du modèle de composant](/help/implementing/universal-editor/field-types.md#fields).

Les conditions peuvent être définies à l’aide du schéma [JsonLogic](https://jsonlogic.com/). Si la condition est vraie, alors le champ s&#39;affiche. Si la condition est false, le champ est masqué.

>[!BEGINTABS]

>[!TAB Modèle type]

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

>[!TAB Condition False]

![ Champ de texte masqué ](assets/hidden.png)

>[!TAB Condition True]

![Champ de texte affiché](assets/shown.png)

>[!ENDTABS]

## URL d&#39;aperçu personnalisées {#custom-preview-urls}

Vous pouvez spécifier une URL d’aperçu personnalisée par le biais d’une méta configuration `urn:adobe:aue:config:preview`, qui s’ouvre en cliquant sur le bouton **Ouvrir la page** dans la barre d’outils supérieure droite de l’éditeur de [&#128279;](/help/sites-cloud/authoring/universal-editor/navigation.md#universal-editor-toolbar).

Pour ce faire, il vous suffit d’inclure l’URL d’aperçu souhaitée dans une balise meta de l’application instrumentée, comme dans l’exemple suivant.

```html
<meta name="urn:adobe:aue:config:preview" content="https://wknd.site"/>
```
