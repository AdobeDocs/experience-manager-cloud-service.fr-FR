---
title: Types de champs
description: Découvrez les différents types de champs que l’éditeur universel peut modifier dans le rail de composants avec des exemples d’utilisation de votre propre application.
source-git-commit: 44073e27ce7eb35bc0d71cb963c1bd0f14183f00
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 7%

---


# Types de champs {#field-types}

Découvrez les différents types de champs que l’éditeur universel peut modifier dans le rail de composants avec des exemples d’utilisation de votre propre application.

{{universal-editor-status}}

## Vue d’ensemble {#overview}

Lorsque vous adaptez vos propres applications pour les utiliser avec l’éditeur universel, vous devez instrumenter les composants et définir les types de données qu’ils peuvent manipuler dans le rail des composants de l’éditeur.

Ce document présente un aperçu des types de champ disponibles, ainsi que des exemples de configuration.

>[!TIP]
>
>Si vous ne savez pas comment utiliser votre application pour l’éditeur universel, consultez le document . [Présentation d’Universal Editor pour AEM Developers.](/help/implementing/universal-editor/developer-overview.md)

## Booléen {#boolean}

Un champ booléen stocke une simple valeur true/false rendue en tant que case à cocher.

### Échantillon {#sample-boolean}

```json
{
  "fields": [   
   {
      "component": "boolean",
      "valueType": "boolean",
      "name": "field1",
      "label": "Boolean Field",
      "description": "This is a boolean field.",
      "required": true,
      "placeholder": null,
      "validation": {
        "customErrorMsg": "This is an error."
      }
    }
  ]
}
```

## Groupe de cases à cocher {#checkbox-group}

Tout comme une valeur booléenne, un groupe de cases à cocher permet de sélectionner plusieurs éléments true/false.

### Échantillon {#sample-checkbox-group}

```json
{
  "fields": [   
   {
      "component": "checkbox-group",
      "valueType": "string-array",
      "name": "field1",
      "label": "Checkbox Group",
      "description": "This is a checkbox group.",
      "required": true,
      "placeholder": null,
      "options": [
        { "name": "First option", "value": "one" },
        { "name": "Second option", "value": "two" },
        { "name": "Third option", "value": "three" }
      ]
    }
  ]
}
```

## Heure de date {#date-time}

Un champ de date et d’heure permet de spécifier une date ou une heure, ou une combinaison de dates.

### Échantillon {#sample-date-time}

```json
{
  "fields": [   
      {
      "component": "date-time",
      "valueType": "date-time",
      "name": "field1",
      "label": "Date Time",
      "description": "This is a date time field that stores both date and time.",
      "required": true,
      "placeholder": "YYYY-MM-DD HH:mm:ss",
      "displayFormat": null,
      "valueFormat": null,
      "validation": {
        "customErrorMsg": "Marty! You have to come back with me!"
      }
    },
    {
      "component": "date-time",
      "valueType": "date",
      "name": "field2",
      "label": "Another Date Time",
      "description": "This is another date time field that only stores the date.",
      "required": true,
      "placeholder": "YYYY-MM-DD",
      "displayFormat": null,
      "valueFormat": null,
      "validation": {
        "customErrorMsg": "Back to the future!"
      }
    },
    {
      "component": "date-time",
      "valueType": "time",
      "name": "field3",
      "label": "Yet Another Date Time",
      "description": "This is another date time field that only stores the time.",
      "required": true,
      "placeholder": "HH:mm:ss",
      "displayFormat": null,
      "valueFormat": null,
      "validation": {
        "customErrorMsg": "Great Scott!"
      }
    }
  ]
}
```

## Nombre {#number}

Un champ de nombre permet la saisie d’un nombre.

### Échantillon {#sample-number}

```json
{
  "fields": [   
   {
      "component": "number",
      "valueType": "number",
      "name": "field1",
      "label": "Number Field",
      "description": "This is a number field.",
      "required": true,
      "placeholder": null,
      "validation": {
        "numberMin": null,
        "numberMax": null,
        "customErrorMsg": "Please don't do that."
      }
    }
  ]
}
```

## Groupe de cases d’option {#radio-group}

Un groupe de cases d’option permet une sélection mutuellement exclusive à partir de plusieurs options rendues sous la forme d’un groupe semblable à un groupe de cases à cocher.

### Échantillon {#sample-radio-group}

```json
{
  "fields": [   
   {
      "component": "radio-group",
      "valueType": "string",
      "name": "field1",
      "label": "Radio Group",
      "description": "This is a radio group.",
      "required": true,
      "placeholder": null,
      "options": [
        { "name": "Option One", "value": "one" },
        { "name": "Option Two", "value": "two" },
        { "name": "Option Three", "value": "three" }
      ]
    }
  ]
}
```

## Référence {#reference}

Une référence permet de spécifier un autre objet de données comme référence à partir de l’objet actif.

## Sélectionner {#select}

Une sélection permet de sélectionner une ou plusieurs options prédéfinies dans un menu déroulant.

### Échantillon {#sample-select}

```json
{
  "fields": [   
   {
      "component": "select",
      "valueType": "string",
      "name": "field1",
      "label": "Select",
      "description": "This is a select.",
      "required": true,
      "placeholder": null,
      "options": [
        { "name": "Option One", "value": "one" },
        { "name": "Option Two", "value": "two" },
        { "name": "Option Three", "value": "three" }
      ],
      "emptyOption": true
    }
  ]
}
```

## Zone de texte {#text-area}

Une zone de texte permet la saisie de texte multiligne.

### Échantillon {#sample-text-area}

```json
{
  "fields": [   
   {
      "component": "text-area",
      "valueType": "string",
      "name": "field1",
      "label": "Text Area",
      "description": "This is a text area.",
      "required": true,
      "multi": true,
      "placeholder": null,
      "mimeType": "text/x-markdown"
    }
  ]
}
```

## Entrée de texte {#text-input}

Une saisie de texte permet de saisir une seule ligne de texte.

### Échantillon {#sample-text-input}

```json
{
  "fields": [   
   {
      "component": "text-input",
      "valueType": "string",
      "name": "field1",
      "label": "Text Input",
      "description": "This is a text input.",
      "required": true,
      "multi": true,
      "placeholder": null
    },
    {
      "component": "text-input",
      "valueType": "string",
      "name": "field2",
      "label": "Another Text Input",
      "description": "This is a text input with validation.",
      "required": true,
      "multi": true,
      "placeholder": null,
      "validation": {
        "minLength": 5,
        "maxLength": 10,
        "regExp": "^foo:.*",
        "customErrorMsg": "I'm sorry, Dave. I can't do that."
      }
    }
  ]
}
```

## Tabulation {#tab}

Un onglet vous permet de regrouper d’autres champs de saisie sur plusieurs onglets afin d’améliorer l’organisation de la mise en page pour les auteurs.

A `tab` peut être considérée comme un séparateur dans le tableau de `fields`. Tout ce qui vient après une `tab` sera placé sur cet onglet jusqu’à ce qu’un nouveau `tab` se produit, où les éléments suivants seront placés sur le nouvel onglet.

Si vous souhaitez que les éléments apparaissent au-dessus de tous les onglets, ils doivent être définis avant les onglets.

### Échantillon {#sample-tab}

```json
{
  "id": "title",
  "fields": [
    {
      "component": "tab",
      "label": "Tab",
      "name": "tab1"
    },
    {
      "component": "text-input",
      "name": "tab-response",
      "value": "",
      "placeholder": "Tab? I can't give you a tab unless you order something.",
      "label": "Lou",
      "valueType": "string"
    },
    {
      "component": "tab",
      "label": "Pepsi Free",
      "name": "tab2"
    },
    {
      "component": "text-input",
      "name": "pepsi-free-response",
      "value": "",
      "placeholder": "You want a Pepsi, pal, you're gonna pay for it.",
      "label": "Mr. Carruthers",
      "valueType": "string"
    },
    {
      "component": "select",
      "name": "without-sugar",
      "value": "coffee",
      "label": "Something without sugar",
      "valueType": "string",
      "options": [
        { "name": "Coffee", "value": "coffee" },
        { "name": "Hot Coffee", "value": "hot-coffee" },
        { "name": "Hotter Coffee", "value": "hotter-coffee" }
      ]
    }
  ]
}
```
