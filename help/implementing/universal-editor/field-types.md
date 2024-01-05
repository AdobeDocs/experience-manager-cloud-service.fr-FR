---
title: Types de champs
description: Découvrez les différents types de champs que l’éditeur universel peut modifier dans le rail de composants avec des exemples d’utilisation de votre propre application.
source-git-commit: b1a188d01371665b4375087847625d89e47d8927
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 8%

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

