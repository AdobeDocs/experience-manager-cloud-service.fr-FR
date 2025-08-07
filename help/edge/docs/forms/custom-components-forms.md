---
title: Créer des composants personnalisés pour un formulaire EDS
description: Créer des composants personnalisés pour un formulaire EDS
feature: Edge Delivery Services
hide: true
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: 77e90657-38db-4a49-9aac-3f3774b62624
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 100%

---

# Création de composants personnalisés

Edge Delivery Services pour AEM Forms vous permet de personnaliser les [composants de formulaire HTML natifs](/help/edge/docs/forms/form-components.md) et de créer des formulaires interactifs et conviviaux. Il vous permet de modifier les composants de formulaire avec des balises prédéfinies, comme expliqué dans la section [Style des champs de formulaire](/help/edge/docs/forms/style-theme-forms.md) à l’aide de CSS personnalisés (feuilles de style en cascade) et du code personnalisé pour la décoration du composant, améliorant ainsi l’aspect des champs de formulaire dans un bloc de formulaires adaptatifs.

![Composant personnalisé](/help/edge/assets/custom-component-image.png)

Ce document décrit les étapes à suivre pour créer des composants personnalisés en mettant en forme les composants de formulaire HTML natifs afin d’améliorer l’expérience client et l’attrait visuel du formulaire.

Prenons l’exemple d’un composant `range` qui affiche le `Estimated trip cost` sur un formulaire. Le composant `range` s’affiche en ligne droite, sans afficher de valeurs telles que les valeurs minimale, maximale ou sélectionnée.

![Composant de plage natif](/help/edge/assets/native-range-component.png)

Commençons à personnaliser le champ `range` pour afficher esa valeurs minimale, maximale et sélectionnée sur la ligne en ajoutant un style à l’aide de CSS et en ajoutant une fonction personnalisée pour décorer un composant.

![Composant de plage personnalisé](/help/edge/assets/custom-range-component.png)

À la fin de cet article, vous saurez créer des composants personnalisés en ajoutant des styles au fichier CSS et la fonction personnalisée.

## Prérequis

Avant de commencer à créer votre composant personnalisé, vous devez :

- posséder des connaissances de base sur les [composants HTML natifs](/help/edge/docs/forms/form-components.md) ;
- savoir [appliquer un style aux champs de formulaire en fonction du type de champ à l’aide des sélecteurs CSS](/help/edge/docs/forms/style-theme-forms.md).


## Créer un composant personnalisé


![Étapes pour créer un composant personnalisé](/help/edge/docs/forms/assets/steps-to-create-custom-component.png)

Comprenons maintenant chaque étape en détail.

<!--Refer to the [enquiry spreadsheet](/help/edge/docs/forms/assets/enquiry.xlsx) to customize the `range` component, by following the steps as explained below.-->

### Ajouter une fonction personnalisée pour décorer le composant

La fonction personnalisée ajoutée dans `[../Form Block/components]` se compose des éléments suivants :

- **Déclaration de fonction** : définissez le nom de la fonction et ses paramètres.
- **Implémentation logique** : écrivez la logique pour ajouter le comportement personnalisé du composant.
- **Export de la fonction** : rendez la fonction accessible dans `[Form Block]`.

Pour ajouter une fonction personnalisée :

1. Accédez à `[../Form Block/components]`.
1. Localisez un fichier nommé `range.js`. s’il n’est pas présent, créez-le.
1. Ajoutez la ligne de code suivante :

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
   '--total-steps': Math.ceil((max - min) /    step),
   '--current-steps': Math.ceil((value - min) / step),
   };
   const style = Object.entries(steps).map(([varName, varValue]) => `${varName}:${varValue}`).join(';');
   bubble.style.left = `calc(${left})`;
   element.setAttribute('style', style);
   }
   // eslint-disable-next-line no-unused-vars
   export default function decorateRange(fieldDiv, field) {
   loadCSS('/blocks/form/components/range/range.css');
   const input = fieldDiv.querySelector('input');
   // modify the type in case it is not range.
   input.type = 'range';
   input.min = input.min || 1;
   // create a wrapper div to provide the min/max and current value
   const div = document.createElement('div');
   div.className = 'range-widget-wrapper';
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
   // as a best practice add a custom css class to apply custom styling
   fieldDiv.classList.add('decorated');
   return fieldDiv;    
   }
   ```

1. Enregistrez les modifications.

### Insérer le décorateur dans le bloc de formulaire

Le `[Form Block]` utilise l’HTML sémantique pour générer les champs de formulaire, y compris les champs de saisie, les libellés et le texte d’aide, avec des attributs standard pour l’accessibilité. Pour que `[Form Block]` utilise un décorateur personnalisé pour un composant spécifié, définissez-le dans le fichier `mappings.js`. Le fichier `mappings.js` importe une fonction qui renvoie le module responsable de la décoration d’un composant particulier. La fonction prend les propriétés du champ et renvoie une fonction de décorateur pour le champ de formulaire.

Dans notre cas, la fonction consulte la propriété `fieldType` du champ et renvoie le décorateur de plage personnalisé à partir du fichier `range.js` présent dans `[../Form Block/components]`.

Pour insérer le décorateur dans le bloc de formulaire :

1. Accédez à `[../Form Block/]` et ouvrez `mapping.js`.
1. Ajoutez la ligne de code suivante :

   ```javascript
   export default async function componentDecorator(fd) {
   const { ':type': type = '', fieldType } = fd;
   .... existing code ....
   if (fieldType === 'range') {
   const module = await import('./components/range.js');
   return module.default(element,fd);
   }
    return null; // null should be returned to use the original markup
   }
   ```

1. Enregistrez les modifications.

### Ajouter un style au composant dans le fichier CSS

Vous pouvez modifier l’apparence des champs de formulaire en fonction du type de champ et des noms de champ à l’aide de sélecteurs CSS, ce qui permet d’obtenir un style cohérent ou unique en fonction des besoins. Pour appliquer un style au composant, ajoutez du code dans le fichier `form.css` afin de modifier l’aspect du composant du formulaire.

Pour personnaliser le style du composant `range`, incluez un extrait de code CSS qui met en forme un élément d’entrée `range` et ses composants associés dans un formulaire. Cela suppose une mise en page HTML structurée avec des classes telles que `.form` et `.range-wrapper`.

Pour ajouter un style à un composant dans le fichier CSS :

1. Accédez à `[../Form Block/]` et ouvrez `form.css`.
1. Ajoutez la ligne de code suivante :

   ```javascript
       /** styling for range */
   main .form .range-wrapper.decorated input[type="range"] {
   margin: unset;
   padding: unset;
   appearance: none;
   height: 5px;
   border-radius: 5px;
   border: none;
   background-image: linear-gradient(to right, var(--button-primary-color) calc(100% * var(--current-steps)/var(--total-steps)), #C5C5C5 calc(100% * var(--current-steps)/var(--total-steps)));
   }
   
   main .form .range-wrapper.decorated input[type="range"]:focus {
   outline: none;
   }
   
   .range-wrapper.decorated input[type="range"]::-webkit-slider-thumb {
   appearance: none;
   width: 25px;
   height: 25px;
   border-radius: 50%;
   background: #fff;
   border: 3px solid var(--button-primary-color);
   cursor: pointer;
   outline: 3px solid #fff;
   }
   
   .range-wrapper.decorated input[type="range"]:focus::-webkit-slider-thumb {
   border-color: var(--button-primary-color);
   }
   
   .range-wrapper.decorated .range-bubble {
   color: #17252e;
   font-size: 20px;
   line-height: 28px;
   position: relative;
   display: inline-block;
   padding-bottom: 12px;
   }
   
   .range-wrapper.decorated .range-min,
   .range-wrapper.decorated .range-max {
   font-size: 14px;
   line-height: 22px;
   color: #494f50;
   margin-top: 16px;
   display: inline-block;
   }
   
   .range-wrapper.decorated .range-max {
   float: right;
   }
   ```

1. Enregistrez les modifications.

### Déployer les fichiers et créer le projet

Déployez les fichiers `range.js`, `mapping.js` et `form.css` mis à jour dans votre projet GitHub et vérifiez la création.

### Prévisualiser le formulaire à l’aide du sidekick AEM

Prévisualisez votre formulaire avec la fonction nouvellement mise en œuvre qui met en forme le composant `range`.

![Formulaire de composant personnalisé](/help/edge/assets/custom-componet-form.png)

Le nouveau style du composant `range` affiche la valeur minimale, maximale et sélectionnée sur la ligne en ajoutant des styles à l’aide de CSS et d’une fonction personnalisée qui inclut un décorateur pour le composant.


