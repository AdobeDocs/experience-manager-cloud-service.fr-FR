---
title: Personnalisation et extension de l’éditeur universel
description: Découvrez les différents points d’extension et autres fonctionnalités qui vous permettent de personnaliser l’interface utilisateur d’Universal Editor afin de prendre en charge les besoins de vos auteurs de contenu.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 732b0648e7114594cb8d35df03f83b842d62736e
workflow-type: tm+mt
source-wordcount: '646'
ht-degree: 1%

---


# Personnalisation et extension de l’éditeur universel {#customizing-extending}

Découvrez les différents points d’extension et autres fonctionnalités qui vous permettent de personnaliser l’expérience de création d’Universal Editor afin de prendre en charge les besoins de vos auteurs de contenu.

## Vue d’ensemble {#overview}

L’éditeur universel permet deux types d’adaptation aux besoins de votre projet.

* [Personnalisation de l’éditeur universel](#customizing) - Les fonctionnalités standard de l’éditeur universel peuvent être adaptées via plusieurs configurations de personnalisation.
* [Extension de l’interface utilisateur de l’éditeur universel](#extending) - L’interface utilisateur de l’éditeur universel peut également être étendue à l’aide d’App Builder pour répondre aux besoins de vos projets.

Les deux types sont présentés dans les sections suivantes.

## Personnaliser l’éditeur universel {#customizing}

Universal Editor propose plusieurs options intégrées pour personnaliser ses fonctionnalités.

### Désactivation de la publication {#disable-publish}

Certains workflows de création nécessitent que le contenu soit examiné avant d’être publié. Dans ce cas, l’option de publication ne doit être disponible pour aucun auteur.

Le bouton **Publish** peut donc être entièrement supprimé dans une application en ajoutant les métadonnées suivantes.

```html
<meta name="urn:adobe:aue:config:disable" content="publish"/>
```

### Filtrage des composants {#filtering-components}

Lors de l’utilisation d’Universal Editor, vous pouvez limiter les composants autorisés par composant de conteneur. Pour ce faire, vous devez introduire une balise de script supplémentaire, qui pointe vers la définition de filtre.

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

Vous pouvez ensuite référencer la définition de filtre à partir de votre composant de conteneur en ajoutant la propriété `data-aue-filter`, en transmettant l’identifiant du filtre que vous avez défini précédemment.

```html
data-aue-filter="container-filter"
```

La définition de l’attribut `components` dans une définition de filtre sur `null` autorise tous les composants, comme s’il n’y avait aucun filtre.

```json
[
  {
    "id": "another-container-filter",
     "components": null
   }
]
```

### Afficher et masquer les composants de manière conditionnelle dans le panneau Propriétés {#conditionally-hide}

Bien qu’un ou plusieurs composants puissent généralement être disponibles pour les auteurs, il peut arriver qu’ils n’aient pas de sens dans certains cas. Dans ce cas, vous pouvez masquer des composants dans le panneau des propriétés en ajoutant un attribut `condition` aux [ champs du modèle de composant.](/help/implementing/universal-editor/field-types.md#fields)

Les conditions peuvent être définies à l’aide du schéma [JsonLogic.](https://jsonlogic.com/) Si la condition est vraie, le champ s’affiche. Si la condition est fausse, le champ est masqué.

>[!BEGINTABS]

>[!TAB Exemple de modèle]

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

![Champ de texte masqué](assets/hidden.png)

>[!TAB Condition True]

![Champ de texte affiché](assets/shown.png)

>[!ENDTABS]

### URL d’aperçu personnalisées {#custom-preview-urls}

Vous pouvez spécifier une URL d’aperçu personnalisée via une configuration de métadonnées `urn:adobe:aue:config:preview` qui s’ouvre lorsque vous cliquez sur le bouton **Ouvrir la page** dans la barre d’outils [ supérieure droite de l’éditeur.](/help/sites-cloud/authoring/universal-editor/navigation.md#universal-editor-toolbar)

Ceci est particulièrement utile pour les applications avec des exigences d’aperçu spécifiques, telles que celles [ utilisant des Edge Delivery Services avec la création WYSIWYG.](/help/edge/wysiwyg-authoring/authoring.md)

Pour ce faire, incluez simplement l’URL d’aperçu souhaitée dans une balise meta de l’application instrumentée comme dans l’exemple suivant.

```html
<meta name="urn:adobe:aue:config:preview" content="https://wknd.site"/>
```

## Extension de l’interface utilisateur de l’éditeur universel {#extending}

En tant que service Adobe Experience Cloud, l’interface utilisateur d’Universal Editor peut être étendue à l’aide d’App Builder et d’Experience Manager.

Les extensions d’IU sont des applications JavaScript créées avec Adobe App Builder qui peuvent être incorporées dans des applications d’IU qui s’exécutent sous le shell unifié Adobe Experience Cloud, comme Universal Editor. Vous pouvez ajouter vos propres boutons et actions au menu d’en-tête et au panneau des propriétés, ainsi que créer vos propres événements pour l’éditeur universel.

Si vous souhaitez explorer ces possibilités, consultez les ressources suivantes :

1. [Extensibilité de l’interface utilisateur](https://developer.adobe.com/uix/docs/) - Il s’agit de la documentation destinée aux développeurs concernant l’extension de l’interface utilisateur.
1. [Guides d’extensibilité de l’interface utilisateur](https://developer.adobe.com/uix/docs/guides/) - Instructions détaillées sur la manière de développer votre propre extension
1. [Points d’extension Universal Editor](https://developer.adobe.com/uix/docs/services/aem-universal-editor/) - Documentation de point d’extension universelle spécifique à l’éditeur

>[!TIP]
>
>Si vous préférez apprendre par exemple, consultez le tutoriel sur l’extensibilité de l’interface utilisateur [AEM.](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/extensibility/ui/overview) Bien qu’il se concentre sur l’extension de la console Fragment de contenu, les concepts de mise en oeuvre d’une extension d’interface utilisateur dans l’éditeur universel sont les mêmes.

[À l’aide d’Extension Manager dans AEM Sites, ](https://developer.adobe.com/uix/docs/extension-manager/) vous pouvez activer ou désactiver vos extensions au niveau de chaque instance, accéder aux extensions propriétaires de l’Adobe, y compris celles pour l’éditeur universel, et bien plus encore.
