---
title: Personnalisation et extension de l’éditeur universel
description: Découvrez les différents points d’extension et d’autres fonctionnalités qui vous permettent de personnaliser l’interface utilisateur de l’éditeur universel pour prendre en charge les besoins des auteurs de contenu.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 1%

---


# Personnalisation et extension de l’éditeur universel {#customizing-extending}

Découvrez les différents points d’extension et d’autres fonctionnalités qui vous permettent de personnaliser l’expérience de création de l’éditeur universel pour prendre en charge les besoins des auteurs de contenu.

## Vue d’ensemble {#overview}

L’éditeur universel permet deux types d’adaptation aux besoins de votre projet.

* [Personnalisation de l’éditeur universel](#customizing) - La fonctionnalité standard de l’éditeur universel peut être adaptée via plusieurs configurations de personnalisation.
* [Extension de l’interface utilisateur de l’éditeur universel](#extending) - L’interface utilisateur de l’éditeur universel peut également être étendue à l’aide d’App Builder pour répondre aux besoins de vos projets.

Les deux types sont présentés dans les sections suivantes.

## Personnaliser l’éditeur universel {#customizing}

L’éditeur universel offre plusieurs options intégrées pour personnaliser ses fonctionnalités.

### Désactivation de la publication {#disable-publish}

Certains workflows de création nécessitent que le contenu soit révisé avant d’être publié. Dans ce cas, l’option de publication ne doit être accessible à aucun auteur.

Le bouton **Publish** peut donc être entièrement supprimé dans une application en ajoutant les métadonnées suivantes.

```html
<meta name="urn:adobe:aue:config:disable" content="publish"/>
```

### Filtrage des composants {#filtering-components}

Vous pouvez restreindre les composants autorisés par conteneur dans l’éditeur universel à l’aide de filtres de composant. Consultez le document [Filtrage des composants](/help/implementing/universal-editor/filtering.md) pour plus d’informations.

### Affichage et masquage conditionnel des composants dans le panneau Propriétés {#conditionally-hide}

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

### URL d&#39;aperçu personnalisées {#custom-preview-urls}

Vous pouvez spécifier une URL d’aperçu personnalisée par le biais d’une méta configuration `urn:adobe:aue:config:preview`, qui s’ouvre en cliquant sur le bouton **Ouvrir la page** dans la barre d’outils supérieure droite de l’éditeur de [](/help/sites-cloud/authoring/universal-editor/navigation.md#universal-editor-toolbar).

Cela s’avère particulièrement utile pour les applications ayant des exigences d’aperçu spécifiques, telles que celles [utilisant des Edge Delivery Services avec la création WYSIWYG](/help/edge/wysiwyg-authoring/authoring.md).

Pour ce faire, il vous suffit d’inclure l’URL d’aperçu souhaitée dans une balise meta de l’application instrumentée, comme dans l’exemple suivant.

```html
<meta name="urn:adobe:aue:config:preview" content="https://wknd.site"/>
```

## Extension de l’interface utilisateur de l’éditeur universel {#extending}

En tant que service Adobe Experience Cloud, l’interface utilisateur de l’éditeur universel peut être étendue à l’aide d’App Builder et d’Experience Manager.

Les extensions d’interface utilisateur sont des applications JavaScript créées avec Adobe App Builder qui peuvent être intégrées à des applications d’interface utilisateur qui s’exécutent sous Adobe Experience Cloud Unified Shell, comme l’éditeur universel. Vous pouvez ajouter vos propres boutons et actions au menu d’en-tête et au panneau des propriétés, ainsi que créer vos propres événements pour l’éditeur universel.

Si vous souhaitez explorer ces possibilités, consultez les ressources suivantes :

1. [Extensibilité de l’interface utilisateur](https://developer.adobe.com/uix/docs/) - Il s’agit de la documentation du développeur pour l’extension d’interface utilisateur.
1. [Guides d’extensibilité de l’interface utilisateur](https://developer.adobe.com/uix/docs/guides/) - Instructions détaillées sur la manière de développer votre propre extension
1. [ Points d’extension de l’éditeur universel ](https://developer.adobe.com/uix/docs/services/aem-universal-editor/) - Documentation sur les points d’extension spécifiques à l’éditeur universel

>[!TIP]
>
>Si vous préférez apprendre par l’exemple, consultez le [tutoriel sur l’extensibilité de l’interface utilisateur AEM](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/extensibility/ui/overview). Bien qu’il se concentre sur l’extension de la console Fragments de contenu, les concepts d’implémentation d’une extension d’interface utilisateur dans l’éditeur universel sont les mêmes.

[Grâce à l’Extension Manager dans AEM Sites](https://developer.adobe.com/uix/docs/extension-manager/), vous pouvez activer ou désactiver vos extensions par instance, accéder aux extensions propriétaires d’Adobe, y compris celles de l’éditeur universel, et bien plus encore.
