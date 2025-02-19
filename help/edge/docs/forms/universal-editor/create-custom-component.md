---
title: Créer des composants personnalisés pour un formulaire EDS
description: Créer des composants personnalisés pour un formulaire EDS
feature: Edge Delivery Services
hide: true
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: 2bbe3f95-d5d0-4dc7-a983-7a20c93e2906
source-git-commit: 76301ca614ae2256f5f8b00c41399298c761ee33
workflow-type: tm+mt
source-wordcount: '1725'
ht-degree: 5%

---

# Création d’un composant personnalisé dans la création WYSIWYG

Edge Delivery Services Forms offre une personnalisation qui permet aux développeurs front-end de créer des composants de formulaire personnalisés. Ces composants personnalisés s’intègrent de manière transparente à l’expérience de création WYSIWYG, ce qui permet aux auteurs de formulaires de les ajouter, de les configurer et de les gérer facilement dans l’éditeur de formulaires. Grâce aux composants personnalisés, les créateurs et créatrices peuvent améliorer leurs fonctionnalités tout en assurant un processus de création fluide et intuitif.

Ce document décrit les étapes à suivre pour créer des composants personnalisés en mettant en forme les composants de formulaire HTML natifs afin d’améliorer l’expérience client et l’attrait visuel du formulaire.

## Prérequis

Avant de commencer à créer votre composant personnalisé, vous devez :

* posséder des connaissances de base sur les [composants HTML natifs](/help/edge/docs/forms/form-components.md) ;
* savoir [appliquer un style aux champs de formulaire en fonction du type de champ à l’aide des sélecteurs CSS](/help/edge/docs/forms/style-theme-forms.md).

## Créer un composant personnalisé

L’ajout d’un composant personnalisé dans l’éditeur universel signifie la mise à disposition d’un nouveau composant pour que les auteurs puissent l’utiliser lors de la conception de formulaires. Cela implique d’enregistrer le composant, de définir ses propriétés et de configurer où il peut être utilisé. Les étapes de création de composants personnalisés sont les suivantes :

[1. Ajout d’une structure pour un nouveau composant personnalisé](#1-adding-structure-for-new-custom-component)
[2. La définition des propriétés de votre composant personnalisé pour la création](#2-defining-the-properties-of-your-custom-component-for-authoring)
3 [.  Rendre votre composant personnalisé visible dans la liste des composants WYSIWYG](#3-making-your-custom-component-visible-in-the-wysiwyg-component-list)
4 [. Enregistrement de votre composant personnalisé](#4-registering-your-custom-component)
5 [. Ajout du comportement d’exécution de votre composant personnalisé](#5-adding-the-runtime-behaviour-for-your-custom-component)

Prenons un exemple de création d’un composant personnalisé appelé **plage**. Le composant de plage s’affiche sous la forme d’une ligne droite et affiche des valeurs telles que la valeur minimale, maximale ou sélectionnée.

![Style du composant de plage](/help/edge/docs/forms/universal-editor/assets/custom-component-range-style.png)

À la fin de cet article, vous apprendrez à créer des composants personnalisés en partant de zéro.

### 1. Ajout d’une structure pour un nouveau composant personnalisé

Avant de pouvoir être utilisé, un composant personnalisé doit être enregistré afin que l’éditeur universel le reconnaisse comme une option disponible. Pour ce faire, utilisez une définition de composant qui inclut un identifiant unique, des propriétés par défaut et la structure du composant. Pour rendre le composant personnalisé disponible pour la création de formulaires, procédez comme suit :

1. **Ajouter un nouveau dossier et de nouveaux fichiers**
Ajoutez de nouveaux dossiers et fichiers pour votre nouveau composant personnalisé dans votre projet AEM.
   1. Ouvrez votre projet AEM et accédez à `../blocks/form/components/`.
   1. Ajoutez un nouveau dossier pour votre composant personnalisé à l’adresse `../blocks/form/components/<component_name>`. Dans cet exemple, nous allons créer un dossier nommé `range`.
   1. Accédez au dossier nouvellement créé à l’adresse `../blocks/form/components/<component_name>`. Par exemple, accédez à `../blocks/form/components/range` et ajoutez les fichiers suivants :
      * `/blocks/form/components/range/_range.json` : contient la définition du composant personnalisé.
      * `../blocks/form/components/range/range.css` : définit le style du composant personnalisé.
      * `../blocks/form/components/range/range.js` : personnalise le composant personnalisé au moment de l’exécution.

        ![Ajout du composant personnalisé pour la création](/help/edge/docs/forms/universal-editor/assets/adding-custom-component.png)

        >[!NOTE]
        >
        > Assurez-vous que le fichier json inclut un trait de soulignement (_) comme préfixe dans son nom de fichier.

1. Accédez au fichier `/blocks/form/components/range/_range.json` et ajoutez la définition du composant personnalisé.

1. **Ajoutez la définition du composant**

   Pour ajouter la définition , les champs à ajouter dans le fichier `_range.json` sont les suivants :

   * **title** : titre du composant qui s’affiche dans l’éditeur universel.
   * **id** : identifiant unique du composant.
   * **fieldType** : Forms prend en charge différents **fieldType** pour capturer des types spécifiques d’entrée utilisateur. Le [fieldType pris en charge) se trouve dans la section Octet supplémentaire ](#supported-fieldtypes).
   * **resourceType** : chaque composant personnalisé est associé à un type de ressource basé sur son fieldType. Le [resourceType pris en charge) se trouve dans la section Octet supplémentaire ](#supported-resourcetype).
   * **jcr:title** : similaire à un titre, mais il est stocké dans la structure du composant.
   * **fd:viewType** : représente le nom du composant personnalisé. Il s’agit de l’identifiant unique du composant. Il est nécessaire de créer une vue personnalisée pour le composant.

Le fichier `_range.json`, après avoir ajouté la définition du composant, est le suivant :

```javascript
{
  "definitions": [
    {
      "title": "Range",
      "id": "range",
      "plugins": {
        "xwalk": {
          "page": {
            "resourceType": "core/fd/components/form/numberinput/v1/numberinput",
            "template": {
              "jcr:title": "Range",
              "fieldType": "number-input",
              "fd:viewType": "range",
              "enabled": true,
              "visible": true
            }
          }
        }
      }
    }
  ]
}
```

>[!NOTE]
>
> Tous les composants liés aux formulaires suivent la même approche que Sites lors de l’ajout de blocs à l’éditeur universel. Reportez-vous à l’article [Création de blocs instrumentés à utiliser avec l’éditeur universel](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/create-block) pour plus d’informations.

### 2. Définition des propriétés de votre composant personnalisé pour la création

Le composant personnalisé comprend un modèle de composant qui spécifie les propriétés configurables par l’auteur du formulaire. Ces propriétés apparaissent dans la boîte de dialogue **Propriétés** de l’éditeur universel, ce qui permet aux créateurs et aux créatrices d’ajuster les paramètres tels que les libellés, les règles de validation, les styles et d’autres attributs. Pour définir les propriétés :

1. Accédez au fichier `/blocks/form/components/range/_range.json` et ajoutez le modèle de composant pour le composant personnalisé.

1. **Ajouter le modèle de composant**

   Pour définir le modèle de composant de votre composant personnalisé, vous devez ajouter les champs appropriés au fichier `_range.json`.

   1. **Créer un modèle**

      * Dans le tableau models (Modèles), ajoutez un nouvel objet et définissez la `id` du modèle de composant pour qu’elle corresponde à la propriété `fd:viewType` configurée précédemment dans la définition du composant.
      * Incluez un tableau de champs dans cet objet.

   2. **Définir des champs pour la boîte de dialogue Propriété**

      * Chaque objet dans le tableau des champs doit être un composant de type conteneur, ce qui lui permet d’apparaître sous la forme d’un onglet dans la boîte de dialogue **Propriété**.
      * Certains champs peuvent faire référence à des propriétés réutilisables disponibles dans `models/form-common`.

   3. **Utiliser un modèle de composant existant comme référence**

      * Vous pouvez copier le contenu d’un modèle de composant existant correspondant à l’`fieldType` de votre choix et le modifier si nécessaire. Par exemple, le composant `number-input` est étendu pour créer un composant **plage** afin que nous puissions utiliser le tableau de modèles de `models/form-components/_number-input.json` comme référence.

   Le fichier `_range.json`, après avoir ajouté le modèle de composant, est le suivant :

   ```javascript
   "models": [
   {
     "id": "range",
     "fields": [
       {
         "component": "container",
         "name": "basic",
         "label": "Basic",
         "collapsible": false,
         "...": "../../../../models/form-common/_basic-input-fields.json"
       },
       {
         "...": "../../../../models/form-common/_help-container.json"
       },
       {
         "component": "container",
         "name": "validation",
         "label": "Validation",
         "collapsible": true,
         "...": "../../../../models/form-common/_number-validation-fields.json"
       }
     ]
   }
   ]
   ```

   >[!NOTE]
   >
   > Pour ajouter un nouveau champ à la boîte de dialogue **Propriété** d’un composant personnalisé, respectez le [schéma défini](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/field-types#loading-model).

   Vous pouvez également [ajouter des propriétés personnalisées](#adding-custom-properties-for-your-custom-component) à un composant personnalisé pour étendre ses fonctionnalités.

#### Ajout de propriétés personnalisées pour votre composant personnalisé

Les propriétés personnalisées vous permettent de définir des comportements spécifiques en fonction des valeurs définies dans la boîte de dialogue Propriété d’un composant. Cela permet d’étendre les options de fonctionnalité et de personnalisation du composant.

Dans cet exemple, nous ajoutons Valeur de l’étape en tant que propriété personnalisée au composant Plage .

![Propriété personnalisée de valeur d’étape](/help/edge/docs/forms/universal-editor/assets/customcomponent-stepvalue.png)

Pour ajouter la propriété personnalisée Valeur d’étape , ajoutez le modèle de composant avec les lignes de code suivantes dans le fichier ` _<component>.json` :

```javascript
      {
      "component": "number",
      "name": "stepValue",
      "label": "Step Value",
      "valueType": "number"
      }
```

Le fragment de code JSON définit une propriété personnalisée appelée **Valeur d’étape** pour un composant **Plage**. Vous trouverez ci-dessous une répartition de chaque champ :

* **component** : indique le type de champ de saisie utilisé dans la boîte de dialogue Propriété. Dans ce cas, `number` indique que le champ accepte des valeurs numériques.
* **name** : identifiant de la propriété, utilisé pour la référencer dans la logique du composant. Ici, le `stepValue` représente le paramètre de valeur d’étape de la plage.
* **label** : nom d’affichage de la propriété tel qu’il apparaît dans la boîte de dialogue Propriété.
* **valueType** : définit le type de données attendu pour la propriété. Le `number` garantit que seules les entrées numériques sont autorisées.

Vous pouvez désormais utiliser `stepValue` comme propriété personnalisée dans les propriétés JSON de `range.js` et implémenter un comportement dynamique en fonction de sa valeur au moment de l’exécution.

Par conséquent, le fichier `_range.json` final, après avoir ajouté la définition du composant, le modèle de composant et les propriétés personnalisées, est le suivant :

```javascript
 {
  "definitions": [
    {
      "title": "Range",
      "id": "range",
      "plugins": {
        "xwalk": {
          "page": {
            "resourceType": "core/fd/components/form/numberinput/v1/numberinput",
            "template": {
              "jcr:title": "Range",
              "fieldType": "number-input",
              "fd:viewType": "range",
              "enabled": true,
              "visible": true
            }
          }
        }
      }
    }
  ],
  "models": [
    {
      "id": "range",
      "fields": [
        {
          "component": "container",
          "name": "basic",
          "label": "Basic",
          "collapsible": false,
          "...": "../../../../models/form-common/_basic-input-fields.json"
         {
           "component": "number",
           "name": "stepValue",
            "label": "Step Value",
             "valueType": "number"
}
        },
        {
          "...": "../../../../models/form-common/_help-container.json"
        },
        {
          "component": "container",
          "name": "validation",
          "label": "Validation",
          "collapsible": true,
          "...": "../../../../models/form-common/_number-validation-fields.json"
        }
      ]
    }
  ]
}
```

![définition et modèle de composant](/help/edge/docs/forms/universal-editor/assets/custom-component-json-file.png)


### 3. Rendre votre composant personnalisé visible dans la liste des composants WYSIWYG

Un filtre définit la section dans laquelle le composant personnalisé peut être utilisé dans l’éditeur universel. Cela permet de s’assurer que le composant ne peut être utilisé que dans les sections appropriées, en conservant sa structure et sa convivialité.

Pour vous assurer que le composant personnalisé apparaît dans la liste des composants disponibles lors de la création de formulaires dans WYSIWYG :

1. Accédez au fichier `/blocks/form/_form.json`.
1. Recherchez le tableau de composants dans l’objet qui a `id="form"`.
1. Ajoutez la valeur `fd:viewType` de l’`definitions[]` au tableau de composants de l’objet avec `id="form"`.

```javascript
 "filters": [
    {
      "id": "form",
      "components": [
        "captcha",
        "checkbox",
        "checkbox-group",
        "date-input",
        "drop-down",
        "email",
        "file-input",
        "form-accordion",
        "form-button",
        "form-fragment",
        "form-image",
        "form-modal",
        "form-reset-button",
        "form-submit-button",
        "number-input",
        "panel",
        "plain-text",
        "radio-group",
        "rating",
        "telephone-input",
        "text-input",
        "tnc",
        "wizard",
        "range"
      ]
    }
  ]
```

![filtre de composant](/help/edge/docs/forms/universal-editor/assets/custom-component-form-file.png)

### 4. Enregistrement de votre composant personnalisé

Pour permettre au bloc de formulaire de reconnaître le composant personnalisé et de charger ses propriétés définies dans le modèle de composant lors de la création de formulaire, ajoutez la valeur de `fd:viewType` de la définition de composant au fichier `mappings.js`.
Pour enregistrer un composant :
1. Accédez au fichier `/blocks/form/mappings.js`.
1. Recherchez le tableau `customComponents[]`.
1. Ajoutez la valeur `fd:viewType` du tableau `definitions[]` au tableau `customComponents[]`.

```javascript
let customComponents = ["range"];
const OOTBComponentDecorators = ['file-input',
                                 'wizard', 
                                 'modal', 'tnc',
                                'toggleable-link',
                                'rating',
                                'datetime',
                                'list',
                                'location',
                                'accordion'];
```

![mappage de composant](/help/edge/docs/forms/universal-editor/assets/custom-component-mapping-file.png)

Après avoir suivi les étapes ci-dessus, le composant personnalisé apparaît dans la liste des composants du formulaire dans l’éditeur universel. Vous pouvez ensuite la faire glisser et la déposer dans la section de votre formulaire.

![composant de plage](/help/edge/docs/forms/universal-editor/assets/custom-component-range.png)

La capture d’écran ci-dessous montre les propriétés du composant `range` ajouté au modèle de composant, qui spécifie les propriétés que l’auteur du formulaire peut configurer :

![Propriétés du composant de plage](/help/edge/docs/forms/universal-editor/assets/range-properties.png)

Vous pouvez maintenant définir le comportement d’exécution de votre composant personnalisé en ajoutant la mise en forme et la fonctionnalité.

### 5. Ajout du comportement d’exécution de votre composant personnalisé

Vous pouvez modifier des composants personnalisés à l’aide de balises prédéfinies, comme expliqué dans la section [Style des champs de formulaire](/help/edge/docs/forms/style-theme-forms.md). Pour ce faire, utilisez des feuilles de style en cascade (CSS) et du code personnalisé afin d’améliorer l’aspect du composant. Pour ajouter le comportement d’exécution de votre composant :

1. Pour ajouter le style, accédez au fichier `/blocks/form/components/range/range.css` et ajoutez la ligne de code suivante :

   ```javascript
   /** Styling for range */
   main .form .range-widget-wrapper.decorated input[type="range"] {
   margin: unset;
   padding: unset;
   appearance: none;
   height: 5px;
   border-radius: 5px;
   border: none;
   background-image: linear-gradient(to right, #ADD8E6 calc(100% * var(--current-steps)/var(--total-steps)), #C5C5C5 calc(100% * var(--current-steps)/var(--total-steps)));
   }
   
   main .form .range-widget-wrapper.decorated input[type="range"]:focus {
   outline: none;
   }
   
   .range-widget-wrapper.decorated input[type="range"]::-webkit-slider-thumb {
   appearance: none;
   width: 25px;
   height: 25px;
   border-radius: 50%;
   background: #00008B; /* Dark Blue */
   border: 3px solid #00008B; /* Dark Blue */
   cursor: pointer;
   outline: 3px solid #fff;
   }
   
   .range-widget-wrapper.decorated input[type="range"]:focus::-webkit-slider-thumb {
   border-color: #00008B; /* Dark Blue */
   }
   
   .range-widget-wrapper.decorated .range-bubble {
   color: #00008B; /* Dark Blue */
   font-size: 20px;
   line-height: 28px;
   position: relative;
   display: inline-block;
   padding-bottom: 12px;
   font-weight: bold;
   }
   
   .range-widget-wrapper.decorated .range-min,
   .range-widget-wrapper.decorated .range-max {
   font-size: 14px;
   line-height: 22px;
   color: #494f50;
   margin-top: 16px;
   display: inline-block;
   }
   
   .range-widget-wrapper.decorated .range-max {
   float: right;
   }
   ```
   Le code vous permet de définir la mise en forme et l’aspect visuel du composant personnalisé.

1. Pour ajouter la fonctionnalité, accédez au fichier `/blocks/form/components/range/range.js` et ajoutez la ligne de code suivante :

   ```javascript
   function updateBubble(input, element) {
   const step = input.step || 1;
   const max = input.max || 0;
   const min = input.min || 1;
   const value = input.value || 1;
   const current = Math.ceil((value - min) / step);
   const total = Math.ceil((max - min) / step);
   const bubble = element.querySelector('.range-bubble');
   // during initial render the width is 0. Hence using a default here.
   const bubbleWidth = bubble.getBoundingClientRect().width || 31;
   const left = `${(current / total) * 100}% - ${(current / total) * bubbleWidth}px`;
   bubble.innerText = `${value}`;
   const steps = {
       '--total-steps': Math.ceil((max - min) / step),
       '--current-steps': Math.ceil((value - min) / step),
   };
   const style = Object.entries(steps).map(([varName, varValue]) => `${varName}:${varValue}`).join(';');
   bubble.style.left = `calc(${left})`;
   element.setAttribute('style', style);
   }
   
   export default async function decorate(fieldDiv, fieldJson) {
   console.log('RANGE DIV: ', fieldDiv);
   console.log('RANGE JSON: fieldJson', fieldJson);
    const input = fieldDiv.querySelector('input');
   // modify the type in case it is not range.
   input.type = 'range';
   input.min = input.min || 10;
   input.max = input.max || 1000;
   // create a wrapper div to provide the min/max and current value
   const div = document.createElement('div');
   div.className = 'range-widget-wrapper decorated';
   input.after(div);
   const hover = document.createElement('span');
   hover.className = 'range-bubble';
   const rangeMinEl = document.createElement('span');
   rangeMinEl.className = 'range-min';
   const rangeMaxEl = document.createElement('span');
   rangeMaxEl.className = 'range-max';
   rangeMinEl.innerText = `${input.min || 1}`;
   rangeMaxEl.innerText = `${input.max}`;
   div.appendChild(hover);
   // move the input element within the wrapper div
   div.appendChild(input);
   div.appendChild(rangeMinEl);
   div.appendChild(rangeMaxEl);
   input.addEventListener('input', (e) => {
   updateBubble(e.target, div);
   });
   updateBubble(input, div);
   return fieldDiv;
   }
   ```

   Il contrôle la manière dont le composant personnalisé interagit avec les entrées utilisateur, traite les données et s’intègre au bloc de formulaire dans l’éditeur universel.

   Après avoir intégré un style et des fonctionnalités personnalisés, l’apparence et le comportement du composant de plage sont améliorés. La conception mise à jour reflète les styles appliqués, tandis que la fonctionnalité ajoutée garantit une expérience utilisateur plus dynamique et interactive.
La capture d’écran ci-dessous illustre le composant de plage mis à jour.

![Style du composant de plage](/help/edge/docs/forms/universal-editor/assets/custom-component-range-1.png)

## Questions fréquentes

* **Si j’ajoute un style à la fois dans component.css et forms.css, lequel est prioritaire ?**
Lorsque des styles sont définis à la fois dans `component.css` et **forms.css**, `component.css` est prioritaire. En effet, les styles au niveau du composant sont plus spécifiques et remplacent les styles globaux de `forms.css`.

* **Mon composant personnalisé n’est pas visible dans la liste des composants disponibles dans l’éditeur universel. Comment puis-je réparer ceci ?**
Si votre composant personnalisé n’apparaît pas, vérifiez les fichiers suivants pour vous assurer que le composant est correctement enregistré :
   * **component-definition.json** : vérifiez que le composant est correctement défini.
   * **component-filters.json** : assurez-vous que le composant est autorisé dans les sections appropriées.
   * **component-models.json** : vérifiez que le modèle de composant est correctement configuré.

## Bonnes pratiques

* Il est recommandé de [configurer un environnement de développement AEM local](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#set-up-local-aem-development-environment) pour développer localement des styles et des composants personnalisés.


## Octet supplémentaire

### Type de ressource pris en charge

| Type de champ | Type de ressource |
|--------------|------------------------------------------------------------------|
| text-input | core/fd/components/form/textinput/v1/textinput |
| number-input | core/fd/components/form/numberinput/v1/numberinput |
| date-input | core/fd/components/form/datepicker/v1/datepicker |
| panel | core/fd/components/form/panelcontainer/v1/panelcontainer |
| checkbox | core/fd/components/form/checkbox/v1/checkbox |
| liste déroulante | core/fd/components/form/dropdown/v1/dropdown |
| groupe radio | core/fd/components/form/radiobutton/v1/radiobutton |
| plain-text | core/fd/components/form/text/v1/text |
| file-input | core/fd/components/form/fileinput/v2/fileinput |
| email | core/fd/components/form/emailinput/v1/emailinput |
| image | core/fd/components/form/image/v1/image |
| button | core/fd/components/form/button/v1/button |

### Types de champ pris en charge

Les types de champs pris en charge pour les formulaires sont les suivants :
* text-input
* number-input
* date-input
* panel
* checkbox
* liste déroulante
* groupe radio
* plain-text
* file-input
* email
* image
* button

## Voir également

{{see-more-forms-eds}}
