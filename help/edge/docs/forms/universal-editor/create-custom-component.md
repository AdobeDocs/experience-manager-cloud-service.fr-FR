---
title: Créer des composants personnalisés pour un formulaire EDS
description: Créer des composants personnalisés pour un formulaire EDS
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 2bbe3f95-d5d0-4dc7-a983-7a20c93e2906
source-git-commit: 9ef4c5638c2275052ce69406f54dda3ea188b0ef
workflow-type: tm+mt
source-wordcount: '1804'
ht-degree: 95%

---

# Créer un composant personnalisé en création WYSIWYG

<span class="preview"> Il s’agit d’une fonctionnalité en version préliminaire disponible via notre <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=fr#new-features">canal de version préliminaire</a>. </span>


Edge Delivery Services pour AEM Forms offre des possibilités de personnalisation, ce qui permet aux développeurs et développeuses front-end de créer des composants de formulaire personnalisés. Ces composants personnalisés s’intègrent de manière transparente à l’expérience de création WYSIWYG, ce qui permet aux créateurs et créatrices de formulaires de les ajouter, de les configurer et de les gérer facilement dans l’éditeur de formulaires. Grâce aux composants personnalisés, les créateurs et créatrices peuvent améliorer leurs fonctionnalités tout en assurant un processus de création fluide et intuitif.

Ce document décrit les étapes à suivre pour créer des composants personnalisés en mettant en forme les composants de formulaire HTML natifs afin d’améliorer l’expérience client et l’attrait visuel du formulaire.

## Conditions préalables

Avant de commencer à créer votre composant personnalisé, vous devez :

* posséder des connaissances de base sur les [composants HTML natifs](/help/edge/docs/forms/form-components.md) ;
* savoir [appliquer un style aux champs de formulaire en fonction du type de champ à l’aide des sélecteurs CSS](/help/edge/docs/forms/style-theme-forms.md).

## Créer un composant personnalisé

L’ajout d’un composant personnalisé dans l’éditeur universel permet de mettre à disposition un nouveau composant pour que les créateurs et créatrices puissent l’utiliser lors de la conception de formulaires. Cela implique d’enregistrer le composant, de définir ses propriétés et de configurer les endroits où il peut être utilisé. Les étapes de création de composants personnalisés sont les suivantes :

[1. Ajouter une structure pour un nouveau composant personnalisé](#1-adding-structure-for-new-custom-component)
[2. Définir les propriétés de votre composant personnalisé pour la création](#2-defining-the-properties-of-your-custom-component-for-authoring)
3 [.  Rendre votre composant personnalisé visible dans la liste des composants WYSIWYG](#3-making-your-custom-component-visible-in-the-wysiwyg-component-list)
4 [. Enregistrer votre composant personnalisé](#4-registering-your-custom-component)
5 [. Ajouter le comportement d’exécution de votre composant personnalisé](#5-adding-the-runtime-behaviour-for-your-custom-component)

Prenons pour exemple la création d’un composant personnalisé appelé **range (plage)**. Le composant « range » (plage) apparaît sous la forme d’une ligne droite et affiche des valeurs telles que les valeurs minimale, maximale ou sélectionnée.

![Représentation visuelle d’un composant de plage présentant un curseur avec des valeurs minimales et maximales, ainsi qu’un indicateur de valeur sélectionné](/help/edge/docs/forms/universal-editor/assets/custom-component-range-style.png)

À la fin de cet article, vous saurez créer entièrement des composants personnalisés.

### 1. Ajouter une structure pour un nouveau composant personnalisé

Avant de pouvoir être utilisé, un composant personnalisé doit être enregistré afin que l’éditeur universel le reconnaisse comme une option disponible. Pour ce faire, utilisez une définition de composant qui inclut un identifiant unique, des propriétés par défaut et la structure du composant. Pour rendre le composant personnalisé disponible pour la création de formulaires, procédez comme suit :

1. **Ajouter un dossier et des fichiers**
Ajoutez un dossier et des fichiers pour votre nouveau composant personnalisé dans votre projet AEM.
   1. Ouvrez votre projet AEM et accédez à `../blocks/form/components/`.
   1. Ajoutez un dossier pour votre composant personnalisé sur `../blocks/form/components/<component_name>`. Dans cet exemple, nous allons créer un dossier nommé `range`.
   1. Accédez au dossier nouvellement créé sur `../blocks/form/components/<component_name>`. Par exemple, accédez à `../blocks/form/components/range` et ajoutez les fichiers suivants :
      * `/blocks/form/components/range/_range.json` : contient la définition du composant personnalisé.
      * `../blocks/form/components/range/range.css` : définit le style du composant personnalisé.
      * `../blocks/form/components/range/range.js` : personnalise le composant personnalisé au moment de l’exécution.

        ![Ajouter le composant personnalisé pour la création](/help/edge/docs/forms/universal-editor/assets/adding-custom-component.png)

        >[!NOTE]
        >
        > Vérifiez que le fichier json comprend un trait de soulignement (_) comme préfixe dans son nom de fichier.

1. Accédez au fichier `/blocks/form/components/range/_range.json` et ajoutez la définition du composant personnalisé.

1. **Ajouter la définition du composant**

   Pour ajouter la définition, les champs à ajouter dans le fichier `_range.json` sont les suivants :

   * **title** : titre du composant qui s’affiche dans l’éditeur universel.
   * **id** : identifiant unique du composant.
   * **fieldType** : Forms prend en charge différents **fieldType** pour capturer des types spécifiques d’entrée utilisateur. Le [fieldType pris en charge se trouve dans la section Octet supplémentaire](#supported-fieldtypes).
   * **resourceType** : chaque composant personnalisé est associé à un type de ressource en fonction de son fieldType. Le [resourceType pris en charge se trouve dans la section Octet supplémentaire](#supported-resourcetype).
   * **jcr:title** : similaire à un titre, mais il est stocké dans la structure du composant.
   * **fd:viewType** : représente le nom du composant personnalisé. Il s’agit de l’identifiant unique du composant. Vous devez créer une vue personnalisée pour le composant.

Le fichier `_range.json`, après avoir ajouté la définition du composant, est le suivant :

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
> Tous les composants liés aux formulaires suivent la même approche que Sites lors de l’ajout de blocs à l’éditeur universel. Pour plus d’informations, consultez l’article [Création de blocs instrumentés pour une utilisation avec l’éditeur universel](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/create-block).

### &#x200B;2. Définir les propriétés de votre composant personnalisé pour la création

Le composant personnalisé comprend un modèle de composant qui spécifie les propriétés configurables par la personne à l’origine du formulaire. Ces propriétés apparaissent dans la boîte de dialogue **Propriétés** de l’éditeur universel, ce qui permet aux créateurs et aux créatrices d’ajuster les paramètres tels que les libellés, les règles de validation, les styles et d’autres attributs. Pour définir les propriétés :

1. Accédez au fichier `/blocks/form/components/range/_range.json` et ajoutez le modèle de composant pour le composant personnalisé.

1. **Ajouter le modèle de composant**

   Pour définir le modèle de composant de votre composant personnalisé, vous devez ajouter les champs appropriés au fichier `_range.json`.

   1. **Créer un modèle**

      * Dans le tableau de modèles, ajoutez un objet et définissez l’`id` du modèle de composant pour qu’il corresponde à la propriété `fd:viewType` configurée précédemment dans la définition du composant.
      * Incluez un tableau de champs dans cet objet.

   2. **Définir des champs pour la boîte de dialogue Propriété**

      * Chaque objet du tableau des champs doit être un composant de type conteneur, ce qui lui permet d’apparaître sous la forme d’un onglet dans la boîte de dialogue **Propriété**.
      * Certains champs peuvent faire référence à des propriétés réutilisables disponibles dans `models/form-common`.

   3. **Utiliser un modèle de composant existant comme référence**

      * Vous pouvez copier le contenu d’un modèle de composant existant correspondant au `fieldType` de votre choix et le modifier si nécessaire. Par exemple, le composant `number-input` est étendu pour créer un composant **range (plage)** afin que nous puissions utiliser le tableau de modèles de `models/form-components/_number-input.json` comme référence.

   Après l’ajout du composant, le fichier `_range.json` ressemble à celui-ci :

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
   > Pour ajouter un champ à la boîte de dialogue **Propriété** d’un composant personnalisé, respectez le [schéma défini](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/field-types#loading-model).

   Vous pouvez également [ajouter des propriétés personnalisées](#adding-custom-properties-for-your-custom-component) à un composant personnalisé pour étendre ses fonctionnalités.

#### Ajouter des propriétés personnalisées pour votre composant personnalisé

Les propriétés personnalisées vous permettent de définir des comportements spécifiques en fonction des valeurs définies dans la boîte de dialogue Propriété d’un composant. Vous pouvez ainsi étendre les options de fonctionnalité et de personnalisation du composant.

Dans cet exemple, nous ajoutons la propriété personnalisée Step Value (Valeur d’étape) au composant Range (Plage).

![Propriété personnalisée de valeur d’étape](/help/edge/docs/forms/universal-editor/assets/customcomponent-stepvalue.png)

Pour ajouter la propriété personnalisée Step Value (Valeur d’étape), ajoutez le modèle de composant avec les lignes de code suivantes dans le fichier ` _<component>.json` :

```javascript
      {
      "component": "number",
      "name": "stepValue",
      "label": "Step Value",
      "valueType": "number"
      }
```

Le fragment de code JSON définit une propriété personnalisée appelée **Step Value** (Valeur d’étape) pour un composant **Range** (Plage). Vous trouverez ci-dessous une répartition de chaque champ :

* **component** : indique le type de champ de saisie utilisé dans la boîte de dialogue Propriété. Dans ce cas, `number` indique que le champ accepte des valeurs numériques.
* **name** : identifiant de la propriété, utilisé pour la référencer dans la logique du composant. Ici, la `stepValue` représente le paramètre de valeur d’étape de la plage.
* **label** : nom d’affichage de la propriété tel qu’il apparaît dans la boîte de dialogue Propriété.
* **valueType** : définit le type de données attendu pour la propriété. La valeur `number` garantit que seules les entrées numériques sont autorisées.

Vous pouvez désormais utiliser `stepValue` comme propriété personnalisée dans les propriétés JSON de `range.js` et implémenter un comportement dynamique en fonction de sa valeur au moment de l’exécution.

Par conséquent, après l’ajout de la définition du composant, du modèle de composant et des propriétés personnalisées, le fichier `_range.json` final ressemble à celui-ci :

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


### &#x200B;3. Rendre votre composant personnalisé visible dans la liste des composants WYSIWYG

Un filtre définit la section dans laquelle le composant personnalisé peut être utilisé dans l’éditeur universel. Cela permet de s’assurer que le composant ne peut être utilisé que dans les sections appropriées, en conservant sa structure et sa convivialité.

Pour vous assurer que le composant personnalisé apparaît dans la liste des composants disponibles lors de la création de formulaires dans WYSIWYG :

1. Accédez au fichier `/blocks/form/_form.json`.
1. Recherchez le tableau de composants dans l’objet qui contient `id="form"`.
1. Ajoutez la valeur `fd:viewType` de `definitions[]` au tableau de composants de l’objet avec `id="form"`.

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

![filtre du composant](/help/edge/docs/forms/universal-editor/assets/custom-component-form-file.png)

### &#x200B;4. Enregistrer votre composant personnalisé

Pour permettre au bloc de formulaire de reconnaître le composant personnalisé et de charger ses propriétés définies dans le modèle de composant lors de la création de formulaire, ajoutez la valeur `fd:viewType` de la définition de composant au fichier `mappings.js`.
Pour enregistrer un composant :
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

Lorsque les étapes ci-dessus ont été réalisées, le composant personnalisé apparaît dans la liste des composants du formulaire, dans l’éditeur universel. Vous pouvez ensuite le faire glisser et le déposer dans la section de votre formulaire.

![Copie d’écran de la palette du composant Éditeur universel présentant le composant de plage personnalisée disponible par glisser-déposer dans des formulaires](/help/edge/docs/forms/universal-editor/assets/custom-component-range.png)

La copie d’écran ci-dessous montre les propriétés du composant `range` ajouté au modèle de composant, lequel spécifie les propriétés que le créateur ou la créatrice du formulaire peut configurer :

![Copie d’écran du panneau Propriétés de l’éditeur universel affichant les paramètres configurables pour le composant de plage, y compris les propriétés de base, les règles de validation et les options de style](/help/edge/docs/forms/universal-editor/assets/range-properties.png)

Vous pouvez maintenant définir le comportement d’exécution de votre composant personnalisé en ajoutant des styles et des fonctionnalités.

### &#x200B;5. Ajouter le comportement d’exécution de votre composant personnalisé

Vous pouvez modifier des composants personnalisés à l’aide d’annotations prédéfinies, comme expliqué dans la section [Style des champs de formulaire](/help/edge/docs/forms/style-theme-forms.md). Pour ce faire, utilisez des feuilles de style en cascade (CSS) et du code personnalisés afin d’améliorer l’aspect du composant. Pour ajouter le comportement d’exécution de votre composant :

1. Pour ajouter les styles, accédez au fichier `/blocks/form/components/range/range.css` et ajoutez la ligne de code suivante :

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

   Le code vous permet de définir le style et l’aspect visuel du composant personnalisé.

1. Pour ajouter les fonctionnalités, accédez au fichier `/blocks/form/components/range/range.js` et ajoutez la ligne de code suivante :

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

   Elles contrôlent la manière dont le composant personnalisé interagit avec les entrées des utilisateurs et utilisatrices, traite les données et s’intègre au bloc de formulaire dans l’éditeur universel.

   Lorsque le style et les fonctionnalités personnalisés ont été intégrés, l’aspect et le comportement du composant « range » (plage) sont améliorés. La conception mise à jour reflète les styles appliqués, tandis que les fonctionnalités ajoutées garantissent une expérience client plus dynamique et interactive.
La copie d’écran ci-dessous illustre le composant « range » (plage) mis à jour.

![Le composant de plage finale en action présentant un curseur stylisé avec un affichage à bulles de valeurs et une fonctionnalité interactive dans l’éditeur universel](/help/edge/docs/forms/universal-editor/assets/custom-component-range-1.png)

## Questions fréquentes

* **Si j’ajoute des styles à la fois dans component.css et dans forms.css, lesquels sont prioritaires ?**
Lorsque des styles sont définis à la fois dans `component.css` et dans **forms.css**, `component.css` est prioritaire. En effet, les styles au niveau du composant sont plus spécifiques et remplacent les styles globaux de `forms.css`.

* **Mon composant personnalisé n’est pas visible dans la liste des composants disponibles dans l’éditeur universel. Comment puis-je résoudre ce problème ?**
Si votre composant personnalisé n’apparaît pas, vérifiez les fichiers suivants pour vous assurer que le composant est correctement enregistré :
   * **component-definition.json** : vérifiez que le composant est correctement défini.
   * **component-filters.json** : assurez-vous que le composant est autorisé dans les sections appropriées.
   * **component-models.json** : vérifiez que le modèle de composant est correctement configuré.

## Bonnes pratiques

* Vous pouvez [configurer un environnement de développement AEM local](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#set-up-local-aem-development-environment) pour développer localement des styles et composants personnalisés.


## Octet supplémentaire

### resourceType pris en charge

| Type de champ | Type de ressource |
|--------------|------------------------------------------------------------------|
| text-input | core/fd/components/form/textinput/v1/textinput |
| number-input | core/fd/components/form/numberinput/v1/numberinput |
| date-input | core/fd/components/form/datepicker/v1/datepicker |
| panel | core/fd/components/form/panelcontainer/v1/panelcontainer |
| checkbox | core/fd/components/form/checkbox/v1/checkbox |
| drop-down | core/fd/components/form/dropdown/v1/dropdown |
| radio-group | core/fd/components/form/radiobutton/v1/radiobutton |
| plain-text | core/fd/components/form/text/v1/text |
| file-input | core/fd/components/form/fileinput/v2/fileinput |
| email | core/fd/components/form/emailinput/v1/emailinput |
| image | core/fd/components/form/image/v1/image |
| button | core/fd/components/form/button/v1/button |

### fieldTypes pris en charge

Les fieldTypes pris en charge pour les formulaires sont les suivants :
* text-input
* number-input
* date-input
* panel
* checkbox
* drop-down
* radio-group
* plain-text
* file-input
* email
* image
* button

## Voir également

{{universal-editor-see-also}}
