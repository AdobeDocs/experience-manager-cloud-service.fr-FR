---
title: Personnaliser le thème et le style d’un Edge Delivery Services pour AEM Forms
description: Personnalisez efficacement le thème et le style des formulaires AEM Forms diffusés via Edge Delivery Services, afin d’offrir une expérience client cohérente et conforme à la marque.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: ac780399-34fe-457d-aaf4-b675656c024d
source-git-commit: 44a8d5d5fdd2919d6d170638c7b5819c898dcefe
workflow-type: tm+mt
source-wordcount: '2493'
ht-degree: 55%

---

# Personnaliser l’apparence de vos formulaires

Le style des formulaires Edge Delivery Services pour AEM Forms nécessite une compréhension approfondie des propriétés personnalisées CSS, de l’architecture par blocs et des stratégies de ciblage spécifiques aux composants. Contrairement aux approches de style de formulaire traditionnelles, le bloc de Forms adaptatif implémente un système de jetons de conception systématique qui permet d’obtenir un thème cohérent tout en conservant les avantages en termes de performances et d’accessibilité de Edge Delivery Services.

L’architecture en blocs de Forms adaptative génère des structures HTML normalisées sur tous les composants de formulaire, ce qui crée des modèles prévisibles pour le ciblage et la personnalisation CSS. Cette cohérence permet aux développeurs de mettre en œuvre des systèmes de style complets qui s’adaptent à toutes les implémentations de formulaires complexes, tout en préservant les optimisations de performances par bloc qui rendent Edge Delivery Services exceptionnellement rapide.

Ce guide complet couvre les bases techniques du style de formulaire dans l’écosystème Edge Delivery Services, y compris les systèmes de propriétés personnalisées CSS, les modèles de structure HTML de composant et les techniques de style avancées. La documentation fournit à la fois une compréhension théorique et des conseils pratiques d’implémentation pour créer des expériences de formulaire de marque sophistiquées.

## Ce que vous allez Principal

**Maîtrise des propriétés personnalisées CSS** : comprenez le système de variables complet qui contrôle l’aspect du formulaire, y compris les modèles de couleurs, les échelles de typographie, les systèmes d’espacement et les paramètres de disposition. Découvrez comment remplacer et étendre ces propriétés pour implémenter des thèmes de marque complets.

**Compréhension de l’architecture des composants** : approfondissez vos connaissances des modèles de structure HTML utilisés par chaque type de composant de formulaire, ce qui permet un ciblage et une personnalisation CSS précis sans rompre avec les fonctionnalités ou les fonctionnalités d’accessibilité sous-jacentes.

**Techniques de style avancées** : implémentez des modèles de style sophistiqués, notamment un style basé sur l’état, une intégration de conception réactive et des stratégies de personnalisation optimisées pour les performances, qui conservent les caractéristiques de chargement rapide de Edge Delivery Services.

**Stratégies d’implémentation professionnelles** : découvrez les approches standard du secteur en matière de style de formulaire, y compris l’intégration du système de conception, l’architecture CSS maintenable et les techniques de dépannage pour les scénarios de style complexes.

## Présentation des types de champs de formulaire

Avant de passer à la définition du style, examinons les [types de champs](/help/edge/docs/forms/universal-editor/create-custom-component.md#supported-fieldtypes) de formulaire communs pris en charge par le bloc de formulaires adaptatifs :

- Champs d’entrée : ces champs incluent des entrées de texte, des entrées d’e-mail, des entrées de mot de passe, et bien plus encore.
- Groupes de cases à cocher : utilisés pour sélectionner plusieurs options.
- Groupes de boutons radio : utilisés pour sélectionner une seule option dans un groupe.
- Listes déroulantes : également appelées zones de sélection, utilisées pour sélectionner une option dans une liste.
- Panneaux/Conteneurs : utilisés pour regrouper les éléments de formulaire associés.

## Principes de base de la définition du style

Il est essentiel de comprendre les [concepts de base de CSS](https://www.w3schools.com/css/css_intro.asp) avant de définir le style de champs de formulaire spécifiques :

- [Sélecteurs](https://www.w3schools.com/css/css_selectors.asp) : les sélecteurs CSS vous permettent de cibler des éléments HTML spécifiques pour la définition du style. Vous pouvez utiliser des sélecteurs d’éléments, des sélecteurs de classe ou des sélecteurs d’ID.
- [Propriétés](https://www.w3schools.com/css/css_syntax.asp) : les propriétés CSS définissent l’apparence visuelle des éléments. Les propriétés courantes de définition du style des champs de formulaire incluent les suivantes : couleur, couleur d’arrière-plan, bordure, remplissage, marge, et bien plus encore.
- [Modèle de zone](https://www.w3schools.com/css/css_boxmodel.asp) : le modèle de zone CSS décrit la structure des éléments HTML sous la forme d’une zone de contenu entourée d’un remplissage, de bordures et de marges.
- Flexbox/Grille : les dispositions de [Flexbox](https://www.w3schools.com/css/css3_flexbox.asp) et de [grille](https://www.w3schools.com/css/css_grid.asp) CSS sont des outils puissants pour créer des conceptions réactives et flexibles.




## Style de formulaire complet avec propriétés personnalisées CSS

Le bloc de Forms adaptatif utilise une architecture CSS sophistiquée basée sur des propriétés personnalisées (variables CSS) qui permettent un thème systématique et un style cohérent sur tous les composants de formulaire. La compréhension de cette structure est essentielle pour une personnalisation et une valorisation de marque efficaces des formulaires.

### Présentation de l’architecture de forms.css

Les styles de formulaire par défaut se trouvent dans le référentiel de votre projet à l’adresse `/blocks/form/form.css` et suivent une approche structurée qui donne la priorité à la maintenabilité, la cohérence et la flexibilité de personnalisation. L’architecture se compose de plusieurs composants clés :

**Custom Properties Foundation CSS** : le système de style est basé sur les propriétés personnalisées CSS définies au niveau du `:root`, fournissant un système de thème centralisé qui se répercute en cascade sur tous les composants de formulaire. Ces variables établissent des jetons de conception pour les couleurs, la typographie, l’espacement et les propriétés de disposition.

**Structure CSS basée sur les blocs** : Edge Delivery Services utilise une architecture basée sur les blocs, où la classe `.form` sert d’espace de noms principal pour tous les styles liés au formulaire, ce qui garantit une isolation de portée appropriée et empêche les conflits CSS avec d’autres composants de page.

**Style spécifique aux composants** : les composants de formulaire individuels sont stylisés à l’aide de modèles d’enveloppe cohérents (`.{Type}-wrapper`) qui fournissent un ciblage prévisible pour différents types de champs tout en préservant l’intégrité globale du système de conception.

### Référence et personnalisation des propriétés personnalisées CSS

Le système de style de formulaire comprend plus de 50 propriétés personnalisées CSS qui contrôlent tous les aspects de l’aspect et du comportement du formulaire. La compréhension de ces propriétés permet une personnalisation complète tout en maintenant la cohérence de la conception.

+++ Variables de couleur et de thème

Le système de couleurs établit une base visuelle complète pour les formulaires grâce à des propriétés personnalisées soigneusement organisées :

```css
:root {
    /* Primary color system */
    --background-color-primary: #fff;
    --label-color: #666;
    --border-color: #818a91;
    --form-error-color: #ff5f3f;
    
    /* Button color system */
    --button-primary-color: #5F8DDA;
    --button-secondary-color: #666;
    --button-primary-hover-color: #035fe6;
    
    /* Form-specific color applications */
    --form-background-color: var(--background-color-primary);
    --form-input-border-color: var(--border-color);
    --form-invalid-border-color: #ff5f3f;
    --form-label-color: var(--label-color);
}
```

**Exemple de personnalisation pratique** : pour implémenter un thème sombre pour vos formulaires, remplacez les variables de couleur de base :

```css
:root {
    --background-color-primary: #1a1a1a;
    --label-color: #e0e0e0;
    --border-color: #404040;
    --form-error-color: #ff6b6b;
    --button-primary-color: #4a9eff;
}
```

Cette modification unique se propage à tous les composants de formulaire, car le système utilise des références de variable plutôt que des valeurs codées en dur.

+++

+++ Typographie et variables d’espacement

Les variables de typographie et d’espacement permettent de contrôler entièrement la présentation du texte et l’espacement des mises en page :

```css
:root {
    /* Font size system */
    --form-font-size-m: 22px;
    --form-font-size-s: 18px;
    --form-font-size-xs: 16px;
    
    /* Component-specific typography */
    --form-label-font-size: var(--form-font-size-s);
    --form-label-font-weight: 400;
    --form-title-font-weight: 600;
    --form-input-font-size: 1rem;
    
    /* Spacing system */
    --form-field-horz-gap: 40px;
    --form-field-vert-gap: 20px;
    --form-input-padding: 0.75rem 0.6rem;
    --form-padding: 0 10px;
}
```

**Exemple de personnalisation pratique** : pour créer une disposition de formulaire plus compacte avec une typographie plus petite :

```css
:root {
    --form-font-size-m: 18px;
    --form-font-size-s: 14px;
    --form-font-size-xs: 12px;
    --form-field-horz-gap: 20px;
    --form-field-vert-gap: 15px;
    --form-input-padding: 0.5rem 0.4rem;
}
```

+++

+++ Variables de disposition et de structure

Les variables de disposition contrôlent les dimensions du formulaire, le comportement de la grille et la disposition des composants :

```css
:root {
    /* Form layout */
    --form-width: 100%;
    --form-columns: 12;
    --form-submit-width: 100%;
    
    /* Card-based components */
    --form-card-border-radius: 4px;
    --form-card-padding: 0.6rem 0.8rem;
    --form-card-shadow: 0 1px 2px rgb(0 0 0 / 3%);
    --form-card-hover-shadow: 0 2px 4px rgb(0 0 0 / 6%);
    
    /* Wizard-specific layout */
    --form-wizard-padding: 0px;
    --form-wizard-padding-bottom: 160px;
    --form-wizard-step-legend-padding: 10px;
}
```

**Exemple de personnalisation pratique** : pour créer un formulaire de style carte avec une profondeur visuelle améliorée :

```css
:root {
    --form-card-border-radius: 12px;
    --form-card-padding: 1.5rem 2rem;
    --form-card-shadow: 0 4px 12px rgb(0 0 0 / 8%);
    --form-card-hover-shadow: 0 8px 24px rgb(0 0 0 / 12%);
    --form-background-color: #f8f9fa;
}

.form {
    background: var(--form-background-color);
    border-radius: var(--form-card-border-radius);
    box-shadow: var(--form-card-shadow);
    padding: var(--form-card-padding);
    max-width: 600px;
    margin: 2rem auto;
}
```

+++

### Modèles de style CSS et bonnes pratiques

Le bloc de Forms adaptatif suit des modèles CSS spécifiques qui assurent un style maintenable, performant et cohérent à tous les composants.

+++ Modèles de style de Principal

**Conteneur de formulaires au niveau du bloc** : ciblez le conteneur de formulaires principal pour la mise en page globale et le style d’arrière-plan :

```css
.form {
    /* Form-wide styles */
    max-width: 800px;
    margin: 0 auto;
    background-color: var(--form-background-color);
    padding: var(--form-padding);
    border-radius: var(--form-card-border-radius);
}
```

**Modèles de wrapper de composants** : ciblez des types de champs spécifiques à l’aide de classes de wrapper cohérentes :

```css
/* Text input fields */
.form .text-wrapper input {
    padding: var(--form-input-padding);
    border: var(--form-input-border-size) solid var(--form-input-border-color);
    font-size: var(--form-input-font-size);
    border-radius: 4px;
    width: 100%;
}

/* Email input fields */
.form .email-wrapper input {
    padding: var(--form-input-padding);
    border: var(--form-input-border-size) solid var(--form-input-border-color);
    font-size: var(--form-input-font-size);
}

/* Button styling */
.form .button-wrapper button {
    background-color: var(--form-button-background-color);
    color: var(--form-button-color);
    padding: var(--form-button-padding);
    border: var(--form-button-border);
    font-size: var(--form-button-font-size);
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.2s ease;
}

.form .button-wrapper button:hover {
    background-color: var(--form-button-background-hover-color);
}
```

+++

+++ Modèles de personnalisation avancés

**Ciblage spécifique au champ** : ciblez des champs individuels par nom pour des exigences de style uniques :

```css
/* Style specific fields */
.form .field-email input {
    background-image: url('data:image/svg+xml;...'); /* Email icon */
    background-repeat: no-repeat;
    background-position: right 12px center;
    padding-right: 40px;
}

.form .field-phone input {
    text-align: center;
    letter-spacing: 1px;
    font-family: monospace;
}
```

**Style basé sur l’état** : implémentez la validation et les états d’interaction :

```css
/* Validation states */
.form .field-wrapper[data-valid="false"] input {
    border-color: var(--form-error-color);
    box-shadow: 0 0 0 2px rgba(255, 95, 63, 0.1);
}

.form .field-wrapper[data-valid="true"] input {
    border-color: #28a745;
    box-shadow: 0 0 0 2px rgba(40, 167, 69, 0.1);
}

/* Focus states */
.form .text-wrapper input:focus,
.form .email-wrapper input:focus {
    outline: none;
    border-color: var(--button-primary-color);
    box-shadow: 0 0 0 2px rgba(95, 141, 218, 0.2);
}
```

+++


## Structure des composants

Le bloc Formulaires adaptatifs offre une structure HTML cohérente pour divers éléments de formulaire, simplifiant ainsi la définition de style et la gestion. Vous pouvez manipuler les composants à l’aide de CSS à des fins de définition de style.

+++ Composants généraux (à l’exception des listes déroulantes, des groupes de boutons radio et des groupes de cases à cocher) :

Tous les champs de formulaire, à l’exception des listes déroulantes, des groupes de boutons radio et des groupes de cases à cocher, présentent la structure HTML suivante :

#### Structure HTML des composants généraux

```HTML
  <div class="{Type}-wrapper field-{Name}   field-wrapper" data-required={Required}>
     <label for="{FieldId}" class="field-label">First   Name</label>
     <input type="{Type}" placeholder="{Placeholder}"   maxlength="{Max}" id={FieldId}" name="{Name}"   aria-describedby="{FieldId}-description">
     <div class="field-description" aria-live="polite"  id="{FieldId}-description">
      Hint - First name should be minimum 3 characters  and a maximum of 10 characters.
     </div>
  </div>
```

- Classes : l’élément div comporte plusieurs classes pour le ciblage d’éléments et de définitions de styles spécifiques. Vous avez besoin des classes `{Type}-wrapper` ou `field-{Name}` pour développer un sélecteur CSS afin de définir le style d’un champ de formulaire :
- {Type} : identifie le composant par type de champ. Par exemple, texte (text-wrapper), nombre (number-wrapper), date (date-wrapper).
- {Name} : identifie le composant par son nom. Le nom du champ ne peut contenir que des caractères alphanumériques, les tirets consécutifs multiples dans le nom sont remplacés par un seul tiret `(-)`, et les tirets de début et de fin dans le nom d’un champ sont supprimés. Par exemple, first-name (field-first-name field-wrapper).
- {FieldId} : il s’agit de l’identifiant unique du champ, généré automatiquement.
- {Required} : il s’agit d’une valeur booléenne indiquant si le champ est obligatoire.
- Libellé : l’élément `label` fournit un texte descriptif pour le champ et l’associe à l’élément d’entrée à l’aide de l’attribut `for`.
- Entrée : l’élément `input` définit le type de données à renseigner. Par exemple : texte, nombre, e-mail.
- Description (facultatif) : `div` avec la classe `field-description` fournit des informations ou des instructions supplémentaires à l’intention de l’utilisateur ou de l’utilisatrice.

**Exemple de structure HTML**

```HTML
<div class="text-wrapper field-first-name field-wrapper" data-required="true">
  <label for="firstName" class="field-label">First Name</label>
  <input type="text" placeholder="Enter your first name" maxlength="50" id="firstName" name="firstName" aria-describedby="firstName-description">
  <div class="field-description" aria-live="polite" id="firstName-description">
    Please enter your legal first name.
  </div>
</div>
```

#### Sélecteur CSS pour les composants généraux

```css
/* Primary Pattern: Target field wrapper by type */
.form .{Type}-wrapper {
    /* Container styling for specific field types */
    margin-bottom: 1rem;
    border-radius: 4px;
}

/* Primary Pattern: Target input fields within wrapper */
.form .{Type}-wrapper input {
    /* Input field styling using CSS custom properties */
    border: var(--form-input-border-size) solid var(--form-input-border-color);
    padding: var(--form-input-padding);
    border-radius: 4px;
    width: 100%;
    font-size: var(--form-input-font-size);
}

/* Context-specific: Target element by field name when higher specificity needed */
.form .field-{Name} input {
    /* Field-specific customizations */
    /* Use this pattern for unique styling requirements */
}
```

- `.form .{Type}-wrapper` : cible l’élément wrapper du champ en fonction du type de champ. Par exemple, `.form .text-wrapper` cible tous les conteneurs de champs de texte.
- `.form .{Type}-wrapper input` : cible les éléments d’entrée réels dans le wrapper. Il s’agit du modèle recommandé pour la mise en forme des entrées de formulaire.
- `.form .field-{Name}` : cible les éléments en fonction du nom de champ spécifique. Par exemple, `.form .field-first-name` cible le conteneur de champs « Prénom ». Utilisez `.form .field-{Name} input` pour cibler spécifiquement l’élément d’entrée.
- **Éviter** : `main .form form .{Type}-wrapper` - Cela crée une spécificité CSS inutile et est plus difficile à gérer.

**Exemples de sélecteurs CSS pour les composants généraux**

```css
/* Primary Pattern: Target all text input fields */
.form .text-wrapper input {
    border: var(--form-input-border-size) solid var(--form-input-border-color);
    padding: var(--form-input-padding);
    border-radius: 4px;
    width: 100%;
    font-size: var(--form-input-font-size);
    background-color: var(--form-input-background-color);
}

/* Context-specific: Target field by name when higher specificity needed */
.form .field-first-name input {
    text-transform: capitalize;
    border-color: var(--button-primary-color);
}

/* Alternative with main context if needed */
main .form .text-wrapper input {
    /* Use only when you need higher specificity */
    color: var(--form-label-color);
}
```

+++

+++ Composant de liste déroulante

Pour les menus déroulants, l’élément `select` est utilisé à la place d’un élément `input` :

#### Structure HTML du composant de liste déroulante

```HTML
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   <label for="{FieldId}" class="field-label">First Name</label>
   <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - First name should be minimum 3 characters and a maximum of 10 characters.
   </div>
</div>
```

**Exemple de structure HTML**

```HTML
<div class="drop-down-wrapper field-country field-wrapper" data-required="true">
  <label for="country" class="field-label">Country</label>
  <select id="country" name="country">
    <option value="">Select Country</option>
    <option value="US">United States</option>
    <option value="CA">Canada</option>
  </select>
  <div class="field-description" aria-live="polite" id="country-description">
    Please select your country of residence.
  </div>
</div>
```

#### Sélecteurs CSS pour le composant de liste déroulante

Le CSS suivant répertorie des exemples de sélecteurs CSS pour les composants de liste déroulante.

```css
/* Primary Pattern: Target the dropdown wrapper */
.form .drop-down-wrapper {
    /* Container layout using flexbox */
    display: flex;
    flex-direction: column;
    margin-bottom: var(--form-field-vert-gap);
}

/* Target the select element */
.form .drop-down-wrapper select {
    border: var(--form-input-border-size) solid var(--form-input-border-color);
    padding: var(--form-input-padding);
    border-radius: 4px;
    background-color: var(--form-input-background-color);
    font-size: var(--form-input-font-size);
    color: var(--form-label-color);
}

/* Style the label */
.form .drop-down-wrapper .field-label {
    margin-bottom: 5px;
    font-weight: var(--form-label-font-weight);
    color: var(--form-label-color);
    font-size: var(--form-label-font-size);
}
```

- Cibler le wrapper : le premier sélecteur (`.drop-down-wrapper`) cible l’élément wrapper externe, assurant ainsi l’application des styles à l’ensemble du composant de liste déroulante.
- Disposition Flexbox : Flexbox organise le libellé, la liste déroulante et la description verticalement pour une disposition claire.
- Définition du style de libellé : le libellé se distingue par une police plus épaisse et une légère marge.
- Définition du style de liste déroulante : l’élément `select` comprend une bordure, un remplissage et des coins arrondis pour un aspect lisse.
- Couleur d’arrière-plan : une couleur d’arrière-plan cohérente est définie à des fins d’harmonie visuelle.
- Personnalisation des flèches : des styles facultatifs masquent la flèche de liste déroulante par défaut et créent une flèche personnalisée à l’aide d’un caractère Unicode et d’un positionnement.

+++

+++ Groupes de boutons radio

Tout comme les composants de liste déroulante, les groupes de boutons radio présentent une structure HTML et une structure CSS qui leur sont propres :

#### Structure HTML du groupe de boutons radio

```HTML
<fieldset class="radio-group-wrapper field-{Name} field-wrapper" id="{FieldId}" name="{Name}" data-required="{Required}">
   <legend for="{FieldId}" class="field-label">....</legend>
   <% for each radio in Group %>
   <div class="radio-wrapper field-{Name}">
      <input type="radio" value="" id="{UniqueId}" data-field-type="radio-group" name="{FieldId}">
      <label for="{UniqueId}" class="field-label">...</label>
   </div>
   <% end for %>
</fieldset>
```

**Exemple de structure HTML**

```HTML
<fieldset class="radio-group-wrapper field-color field-wrapper" id="color_preference" name="color_preference" data-required="true">
  <legend for="color_preference" class="field-label">Favorite Color:</legend>
  <% for each radio in Group %>
    <div class="radio-wrapper field-color">
      <input type="radio" value="red" id="color_red" data-field-type="radio-group" name="color_preference">
      <label for="color_red" class="field-label">Red</label>
    </div>
    <div class="radio-wrapper field-color">
      <input type="radio" value="green" id="color_green" data-field-type="radio-group" name="color_preference">
      <label for="color_green" class="field-label">Green</label>
    </div>
    <div class="radio-wrapper field-color">
      <input type="radio" value="blue" id="color_blue" data-field-type="radio-group" name="color_preference">
      <label for="color_blue" class="field-label">Blue</label>
    </div>
  <% end for %>
</fieldset>
```

#### Sélecteurs CSS pour les groupes de boutons radio

- Ciblage de filedset

```css
/* Target radio group container */
.form .radio-group-wrapper {
    border: var(--form-input-border-size) solid var(--form-input-border-color);
    padding: var(--form-input-padding);
    border-radius: 4px;
    margin-bottom: var(--form-field-vert-gap);
}
```

Ce sélecteur cible n’importe quel fieldset avec la classe radio-group-wrapper. Cela s’avère utile pour appliquer des styles généraux à l’ensemble du groupe de boutons radio.

- Ciblage des libellés de boutons radio

```css
/* Target radio button labels */
.form .radio-wrapper label {
    font-weight: var(--form-label-font-weight);
    margin-right: 10px;
    color: var(--form-label-color);
    font-size: var(--form-label-font-size);
    cursor: pointer;
}
```

- Cibler tous les libellés de bouton radio dans un fieldset spécifique en fonction de son nom

```css
/* Target all radio button labels within a specific fieldset based on its name */
.form .field-color .radio-wrapper label {
    /* Field-specific radio label customizations */
    /* Add your custom styles here */
}
```

+++

+++ Groupes de cases à cocher

#### Structure HTML du groupe de cases à cocher

```HTML
<fieldset class="checkbox-group-wrapper field-{Name} field-wrapper" id="{FieldId}" name="{Name}" data-required="{Required}">
   <legend for="{FieldId}" class="field-label">....</legend>
   <% for each radio in Group %>
   <div class="checkbox-wrapper field-{Name}">
      <input type="checkbox" value="" id="{UniqueId}" data-field-type="checkbox-group" name="{FieldId}">
      <label for="{UniqueId}" class="field-label">...</label>
   </div>
   <% end for %>
</fieldset>
```

**Exemple de structure HTML**

```HTML
<fieldset class="checkbox-group-wrapper field-topping field-wrapper" id="topping_preference" name="topping_preference" data-required="false">
  <legend for="topping_preference" class="field-label">Pizza Toppings:</legend>
  <div class="checkbox-wrapper field-topping">
    <input type="checkbox" value="pepperoni" id="topping_pepperoni" data-field-type="checkbox-group" name="topping_preference">
    <label for="topping_pepperoni" class="field-label">Pepperoni</label>
  </div>
  <div class="checkbox-wrapper field-topping">
    <input type="checkbox" value="mushrooms" id="topping_mushrooms" data-field-type="checkbox-group" name="topping_preference">
    <label for="topping_mushrooms" class="field-label">Mushrooms</label>
  </div>
  <div class="checkbox-wrapper field-topping">
    <input type="checkbox" value="onions" id="topping_onions" data-field-type="checkbox-group" name="topping_preference">
    <label for="topping_onions" class="field-label">Onions</label>
  </div>
</fieldset>
```

#### Sélecteurs CSS pour les groupes de cases à cocher

- Ciblage du wrapper externe : ces sélecteurs ciblent les conteneurs les plus éloignés des groupes de boutons radio et de cases à cocher, vous permettant ainsi d’appliquer des styles généraux à l’ensemble de la structure du groupe. Cela s’avère utile pour définir l’espacement, l’alignement ou d’autres propriétés liées à la disposition.

```css
/* Primary Pattern: Targets radio group wrappers */
.form .radio-group-wrapper {
    margin-bottom: var(--form-field-vert-gap); /* Adds space between radio groups */
    display: flex;
    flex-direction: column;
    border: var(--form-fieldset-border);
    padding: var(--form-input-padding);
}

/* Primary Pattern: Targets checkbox group wrappers */
.form .checkbox-group-wrapper {
    margin-bottom: var(--form-field-vert-gap); /* Adds space between checkbox groups */
    display: flex;
    flex-direction: column;
    border: var(--form-fieldset-border);
    padding: var(--form-input-padding);
}
```

- Ciblage des libellés de groupes : ce sélecteur cible l’élément `.field-label` dans les wrappers de groupes de boutons radio et de cases à cocher. Cela vous permet de définir le style des libellés propres à ces groupes, ce qui peut les rendre plus remarquables.

```css
/* Primary Pattern: Target group labels */
.form .radio-group-wrapper legend,
.form .checkbox-group-wrapper legend {
    font-weight: var(--form-title-font-weight); /* Makes the group label bold */
    margin-bottom: 0.5rem;
    font-size: var(--form-fieldset-legend-font-size);
    color: var(--form-fieldset-legend-color);
    padding: var(--form-fieldset-legend-padding);
    border: var(--form-fieldset-legend-border);
}
```

- Ciblage d’entrées et de libellés individuels : ces sélecteurs offrent un contrôle plus précis sur les boutons radio et cases à cocher individuels et les libellés qui leur sont associés. Vous pouvez les utiliser pour ajuster le dimensionnement, l’espacement ou appliquer des styles visuels plus distincts.

```css
/* Primary Pattern: Styling radio buttons */
.form .radio-group-wrapper input[type="radio"] {
    margin-right: 8px; /* Adds space between the input and its label */
    margin-bottom: 4px;
    cursor: pointer;
}

/* Primary Pattern: Styling radio button labels */
.form .radio-group-wrapper label {
    font-size: var(--form-label-font-size); /* Changes the label font size */
    color: var(--form-label-color);
    font-weight: var(--form-label-font-weight);
    display: flex;
    align-items: center;
    cursor: pointer;
}

/* Primary Pattern: Styling checkboxes */
.form .checkbox-group-wrapper input[type="checkbox"] {
    margin-right: 8px; /* Adds space between the input and its label */
    margin-bottom: 4px;
    cursor: pointer;
}

/* Primary Pattern: Styling checkbox labels */
.form .checkbox-group-wrapper label {
    font-size: var(--form-label-font-size); /* Changes the label font size */
    color: var(--form-label-color);
    font-weight: var(--form-label-font-weight);
    display: flex;
    align-items: center;
    cursor: pointer;
}
```

- Personnalisation de l’apparence des boutons radio et des cases à cocher : cette technique masque l’entrée par défaut et utilise les pseudo-éléments `:before` et `:after` pour créer des visuels personnalisés qui modifient l’apparence en fonction de l’état « coché ».

```css
/* Hide the default radio button or checkbox */
.form .radio-group-wrapper input[type="radio"],
.form .checkbox-group-wrapper input[type="checkbox"] {
    opacity: 0;
    position: absolute;
    width: 1px;
    height: 1px;
}

/* Create a custom radio button */
.form .radio-group-wrapper input[type="radio"] + label::before {
    content: '';
    display: inline-block;
    width: 16px;
    height: 16px;
    border: 2px solid var(--form-input-border-color);
    border-radius: 50%;
    margin-right: 8px;
    background-color: var(--form-input-background-color);
    transition: all 0.2s ease;
}

.form .radio-group-wrapper input[type="radio"]:checked + label::before {
    background-color: var(--button-primary-color);
    border-color: var(--button-primary-color);
    box-shadow: inset 0 0 0 3px var(--form-input-background-color);
}

/* Create a custom checkbox */
.form .checkbox-group-wrapper input[type="checkbox"] + label::before {
    content: '';
    display: inline-block;
    width: 16px;
    height: 16px;
    border: 2px solid var(--form-input-border-color);
    border-radius: 2px;
    margin-right: 8px;
    background-color: var(--form-input-background-color);
    transition: all 0.2s ease;
}

.form .checkbox-group-wrapper input[type="checkbox"]:checked + label::before {
    background-color: var(--button-primary-color);
    border-color: var(--button-primary-color);
    background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16"><path fill="white" d="M13.854 3.646a.5.5 0 0 1 0 .708l-7 7a.5.5 0 0 1-.708 0l-3.5-3.5a.5.5 0 1 1 .708-.708L6.5 10.293l6.646-6.647a.5.5 0 0 1 .708 0z"/></svg>');
    background-repeat: no-repeat;
    background-position: center;
}
```

+++

+++ Composants de panneau/conteneur

#### Structure HTML des composants de panneau/conteneur

```HTML
<fieldset class="panel-wrapper field-{PanelName} field-wrapper">
  <legend for="{id}" class="field-label" data-visible="false">bannerComponent</legend>
  <div class="{Type}-wrapper field-{Name} field-wrapper">
    <label for="{FieldId}" class="field-label">First Name</label>
    <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}">
    <div class="field-description" aria-live="polite" id="{FieldId}-description">
      Hint - First name should be minimum 3 characters and a maximum of 10 characters.
    </div>
  </div>
</fieldset>
```

**Exemple de structure HTML**

```HTML
<fieldset class="panel-wrapper field-login field-wrapper">
  <legend for="login" class="field-label" data-visible="false">Login Information</legend>
  <div class="text-wrapper field-username field-wrapper">
    <label for="username" class="field-label">Username</label>
    <input type="text" placeholder="Enter your username" maxlength="50" id="username" name="username">
    <div class="field-description" aria-live="polite" id="username-description">
      Please enter your username or email address.
    </div>
  </div>
  <div class="password-wrapper field-password field-wrapper">
    <label for="password" class="field-label">Password</label>
    <input type="password" placeholder="Enter your password" maxlength="20" id="password" name="password">
    <div class="field-description" aria-live="polite" id="password-description">
      Your password must be at least 8 characters long.
    </div>
  </div>
</fieldset>
```

- L’élément fieldset fait office de conteneur de panneau avec la classe panel-wrapper et des classes supplémentaires pour définir le style en fonction du nom du panneau (field-login).
- L’élément de légende (`<legend>`) sert de titre au panneau avec le texte « Informations de connexion » et le libellé du champ de la classe. L’attribut data-visible=&quot;false&quot; peut être utilisé avec JavaScript pour contrôler la visibilité du titre.
- Dans le fieldset, plusieurs éléments.Les éléments {Type}-wrapper (.text-wrapper et .password-wrapper dans cet exemple) représentent des champs de formulaire individuels dans le panneau.
- Chaque wrapper contient un libellé, un champ d’entrée et une description, comme dans les exemples précédents.


#### Exemples de sélecteurs CSS pour les composants de panneau/conteneur

1. Ciblage du panneau :

```CSS
  /- Target the entire panel container */
  main .form form .panel-wrapper {
    /- Add your styles here (e.g., border, padding, background color) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
 }
```

- le sélecteur `.panel-wrapper` définit le style de tous les éléments avec la classe panel-wrapper, créant ainsi un aspect cohérent pour tous les panneaux.

1. Ciblage du titre du panneau :

```CSS
  /- Target the legend element (panel title) */
  .panel-wrapper legend {
    /- Add your styles here (e.g., font-weight, font-size) */
    font-weight: bold;
    font-size: 16px;
    padding-bottom: 5px;
    margin-bottom: 10px;
    border-bottom: 1px solid #ddd; /- Optional: create a separation line */
  }
```

- le sélecteur `.panel-wrapper legend` définit le style de l’élément de légende dans le panneau, ce qui permet de distinguer visuellement le titre.


1. Ciblage de champs individuels dans le panneau :

```CSS
/- Target all form field wrappers within a panel */
main .form form .panel-wrapper .{Type}-wrapper {
  /- Add your styles here (e.g., margin) */
  margin-bottom: 10px;
}
```

- le sélecteur `.panel-wrapper .{Type}-wrapper` cible tous les wrappers avec la classe `.{Type}-wrapper` dans le panneau, ce qui vous permet de définir le style de l’espacement entre les champs de formulaire.

1. Ciblage de champs spécifiques (facultatif) :

```CSS
  /- Target the username field wrapper */
  main .form form .panel-wrapper .text-wrapper.field-username {
    /- Add your styles here (specific to username field) */
  }

  /- Target the password field wrapper */
  main .form form .panel-wrapper .password-wrapper.field-password {
    /- Add your styles here (specific to password field) */
  }
```

- ces sélecteurs facultatifs vous permettent de cibler des wrappers de champ spécifiques dans le panneau pour une définition de style unique, comme la mise en surbrillance du champ du nom d’utilisateur ou d’utilisatrice.


+++

+++ Panneau répétable

#### Structure HTML d’un panneau répétable

```HTML
<fieldset class="panel-wrapper field-{PanelName} field-wrapper">
  <legend for="{id}" class="field-label" data-visible="false">bannerComponent</legend>
  <div class="{Type}-wrapper field-{Name} field-wrapper">
    <label for="{FieldId}" class="field-label">First Name</label>
    <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}">
    <div class="field-description" aria-live="polite" id="{FieldId}-description">
      Hint - First name should be minimum 3 characters and a maximum of 10 characters.
    </div>
</fieldset>
```

**Exemple de structure HTML**

```HTML
<fieldset class="panel-wrapper field-contact field-wrapper" data-repeatable="true">
  <legend for="contact-1" class="field-label" data-visible="false">Contact Information</legend>
  <div class="text-wrapper field-name field-wrapper">
    <label for="name-1" class="field-label">Name</label>
    <input type="text" placeholder="Enter your name" maxlength="50" id="name-1" name="contacts[0].name">
    <div class="field-description" aria-live="polite" id="name-1-description">
      Please enter your full name.
    </div>
  </div>
  <div class="email-wrapper field-email field-wrapper">
    <label for="email-1" class="field-label">Email</label>
    <input type="email" placeholder="Enter your email address" maxlength="100" id="email-1" name="contacts[0].email">
    <div class="field-description" aria-live="polite" id="email-1-description">
      Please enter a valid email address.
    </div>
  </div>
</fieldset>

<fieldset class="panel-wrapper field-contact field-wrapper" data-repeatable="true">
  <legend for="contact-2" class="field-label" data-visible="false">Contact Information</legend>
  <div class="text-wrapper field-name field-wrapper">
    <label for="name-2" class="field-label">Name</label>
    <input type="text" placeholder="Enter your name" maxlength="50" id="name-2" name="contacts[1].name">
    <div class="field-description" aria-live="polite" id="name-2-description">
      Please enter your full name.
    </div>
  </div>
  <div class="email-wrapper field-email field-wrapper">
    <label for="email-2" class="field-label">Email</label>
    <input type="email" placeholder="Enter your email address" maxlength="100" id="email-2" name="contacts[1].email">
    <div class="field-description" aria-live="polite" id="email-2-description">
      Please enter a valid email address.
    </div>
  </div>
</fieldset>
```

Chaque panneau présente la même structure que l’exemple de panneau unique, avec des attributs supplémentaires :

- data-repeatable=&quot;true&quot; : cet attribut indique que le panneau peut être répété de manière dynamique à l’aide de JavaScript ou d’un framework.

- Identifiants et noms uniques : chaque élément du panneau comprend un identifiant unique (par exemple, name-1, email-1) et un attribut name basé sur l’index du panneau (par exemple, name=&quot;contacts[0].name&quot;). Cela permet une collecte de données correcte lorsque plusieurs panneaux sont envoyés.


#### Sélecteurs CSS pour un panneau répétable

- Ciblage de tous les panneaux répétables :

```CSS
  /- Target all panels with the repeatable attribute */
 main .form form .panel-wrapper[data-repeatable="true"] {
    /- Add your styles here (e.g., border, margin) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
  }
```

le sélecteur définit le style de tous les panneaux qui peuvent être répétés, assurant ainsi un aspect cohérent.


- Ciblage de champs individuels dans un panneau :

```CSS
/- Target all form field wrappers within a repeatable panel */
main .form form .panel-wrapper[data-repeatable="true"] .{Type}-wrapper {
  /- Add your styles here (e.g., margin) */
  margin-bottom: 10px;
}
```

ce sélecteur définit le style de tous les wrappers de champ dans un panneau répétable, en assurant un espacement cohérent entre les champs.

- Ciblage de champs spécifiques (dans un panneau) :

```CSS
/- Target the name field wrapper within the first panel */
main .form form .panel-wrapper[data-repeatable="true"][data-index="0"] .text-wrapper.field-name {
  /- Add your styles here (specific to first name field) */
}

/- Target all
```


+++


+++ Pièce jointe

#### Structure HTML pour une pièce jointe

```HTML
<div class="file-wrapper field-{FileName} field-wrapper">
  <legend for="{id}" class="field-label" data-visible="false"> File Attachment </legend>
  <div class="file-drag-area">
    <div class="file-dragIcon"></div>
    <div class="file-dragText">Drag and Drop To Upload</div>
    <button class="file-attachButton" type="button">Attach</button>
    <input type="file" accept="audio/*, video/*, image/*, text/*, application/pdf" id="{id}" name="{FileName}" autocomplete="off" multiple="" required="required">
  </div>
  <div class="files-list">
    <div data-index="0" class="file-description">
      <span class="file-description-name">ClaimForm.pdf</span>
      <span class="file-description-size">26 kb</span>
      <button class="file-description-remove" type="button"></button>
    </div>
  </div>
</div>
```

**Exemple de structure HTML**


```HTML
<div class="file-wrapper field-claim_form field-wrapper">
  <legend for="claim_form" class="field-label" data-visible="false">File Attachment</legend>
  <div class="file-drag-area">
    <div class="file-dragIcon"></div>
    <div class="file-dragText">Drag and Drop To Upload</div>
    <button class="file-attachButton" type="button">Attach</button>
  </div>
  <input type="file" accept="audio/*, video/*, image/*, text/*, application/pdf" id="claim_form"
         name="claim_form" autocomplete="off" multiple="" required="required" data-max-file-size="2MB">
  <div class="files-list">
    </div>
</div>
```

- L’attribut class utilise le nom fourni pour le fichier joint (claim_form).
- Les attributs id et name de l’élément d’entrée correspondent au nom du fichier joint (claim_form).
- La section files-list est initialement vide. Elle est renseignée de manière dynamique avec JavaScript lorsque des fichiers sont chargés.


#### Sélecteurs CSS pour le composant de fichier joint

- Ciblage de l’ensemble du composant de fichier joint :

```CSS
/- Target the entire file attachment component */
main .form form .file-wrapper {
  /- Add your styles here (e.g., border, padding) */
  border: 1px solid #ccc;
  padding: 15px;
  border-radius: 4px;
  margin-bottom: 20px;
}
```

ce sélecteur définit le style de l’ensemble du composant de fichier joint, y compris la légende, la zone de déplacement, le champ d’entrée et la liste.

- Ciblage d’éléments spécifiques :

```CSS
/- Target the drag and drop area */
main .form form .file-wrapper .file-drag-area {
  /- Add your styles here (e.g., background color, border) */
  background-color: #f0f0f0;
  border: 1px dashed #ddd;
  padding: 10px;
  text-align: center;
}

/- Target the file input element */
main .form form .file-wrapper input[type="file"] {
  /- Add your styles here (e.g., hide the default input) */
  display: none;
}

/- Target individual file descriptions within the list (populated dynamically) */
main .form form .file-wrapper .files-list .file-description {
  /- Add your styles here (e.g., margin, display) */
  display: flex;
  justify-content: space-between;
  margin-bottom: 5px;
}

/- Target the file name within the description */
main .form form .file-wrapper .files-list .file-description .file-description-name {
  /- Add your styles here (e.g., font-weight) */
  font-weight: bold;
}
```

ces sélecteurs vous permettent de définir le style individuellement de divers éléments du composant de fichier joint. Vous pouvez ajuster les styles en fonction de vos préférences de conception.

+++



## Définir le style des composants

Vous pouvez définir le style des champs de formulaire en fonction de leur type spécifique (`{Type}-wrapper`) ou des noms individuels (`field-{Name}`). Cela permet un contrôle et une personnalisation plus précis de l’apparence de votre formulaire.

+++ Définition de style basée sur le type de champ

Vous pouvez utiliser des sélecteurs CSS pour cibler des types de champ spécifiques et appliquer les styles de manière cohérente.

#### Structure HTML

```HTML
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   <label for="{FieldId}" class="field-label">First Name</label>
   <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - First name should be minimum 3 characters and a maximum of 10 characters.
   </div>
</div>
```

**Exemple de structure HTML**

```HTML
<div class="text-wrapper field-name field-wrapper" data-required="true">
  <label for="name" class="field-label">Name</label>
  <input type="text" placeholder="Enter your name" maxlength="50" id="name" name="name">
</div>

<div class="number-wrapper field-age field-wrapper" data-required="true">
  <label for="age" class="field-label">Age</label>
  <input type="number" placeholder="Enter your age" id="age" name="age">
</div>

<div class="email-wrapper field-email field-wrapper" data-required="true">
  <label for="email" class="field-label">Email Address</label>
  <input type="email" placeholder="Enter your email" id="email" name="email">
</div>
```

- Chaque champ est encapsulé dans un élément `div` avec plusieurs classes :
   - `{Type}-wrapper` : identifie le type de champ. Par exemple : `form-text-wrapper`, `form-number-wrapper`, `form-email-wrapper`.
   - `field-{Name}` : identifie le champ par son nom. Par exemple : `form-name`, `form-age`, `form-email`.
   - `field-wrapper` : classe générique pour tous les wrappers de champ.
- L’attribut `data-required` indique si le champ est obligatoire ou facultatif.
- Chaque champ comporte un libellé, un élément d’entrée et d’éventuels éléments supplémentaires correspondants, tels que des espaces réservés et des descriptions.




#### Exemple de sélecteurs CSS

```CSS
/- Primary Pattern: Target all text input fields */
.form .text-wrapper input {
  /- Add your styles here */
  width: 100%;
  padding: var(--form-input-padding);
}

/- Primary Pattern: Target all number input fields */
.form .number-wrapper input {
  /- Add your styles here */
  letter-spacing: 2px; /- Example for adding letter spacing to all number fields */
  text-align: center;
}
```

+++

+++ Définition de style basée sur le nom du champ

Vous pouvez également cibler des champs individuels par nom pour appliquer des styles uniques.

#### Structure HTML

```HTML
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   <label for="{FieldId}" class="field-label">First Name</label>
   <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id="{FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - Enter the 6 digit number sent to your mobile number.
   </div>
</div>
```

**Exemple de structure HTML**

```HTML
<div class="number-wrapper field-otp field-wrapper" data-required="true">
  <label for="otp" class="field-label">OTP</label>
  <input type="number" placeholder="Enter your OTP" maxlength="6" id="otp" name="otp" aria-describedby="otp-description">
  <div class="field-description" aria-live="polite" id="otp-description">
    Hint - Enter the 6 digit number sent to your mobile number.
   </div>
</div>
```


#### Exemple de sélecteur CSS

```CSS
/- Primary Pattern: Target specific field by name */
.form .field-otp input {
   letter-spacing: 2px;
   text-align: center;
   font-family: monospace;
}

/- Context-specific: Use higher specificity when needed */
main .form .field-otp input {
   /- Use only when you need to override other styles */
   font-weight: bold;
}
```

Ce CSS cible tous les éléments d’entrée situés dans un élément qui possède la classe `field-otp`. La structure de formulaire Edge Delivery Services suit les conventions de blocs de Forms adaptatif, où les conteneurs sont marqués de classes spécifiques au champ comme « field-otp » pour les champs portant le nom « otp ».


## Structure et implémentation des fichiers CSS

### **Implémentation de référence**

La référence complète du style de formulaire est disponible dans le référentiel standard d’AEM Forms :

```
https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/blocks/form/form.css
```

Ce fichier sert d’implémentation canonique du système de propriétés personnalisées CSS et fournit la base de tous les styles de formulaire. Il comprend des définitions complètes de toutes les variables CSS, les modèles de style de composant et les implémentations de Responsive Design.

+++

+++ Intégration de projet

Dans votre projet Edge Delivery Services, implémentez le style de formulaire au moyen de cette approche structurée :

```
/blocks/form/form.css          // Core form block styles (copied from boilerplate)
/styles/styles.css             // Global site styles and CSS variable overrides
/styles/lazy-styles.css        // Additional component enhancements
```

+++

+++ Stratégie de mise en œuvre

**Remplacements de propriétés personnalisées CSS** : remplacez les variables de formulaire dans vos styles globaux pour implémenter un thème spécifique à la marque :

```css
/* In /styles/styles.css */
:root {
    /* Brand-specific overrides */
    --button-primary-color: #your-brand-color;
    --form-background-color: #your-background;
    --label-color: #your-text-color;
}
```

**Personnalisations spécifiques aux composants** :
Ajoutez un style spécifique au composant tout en conservant le système de variables CSS :

```css
/* Enhanced component styling */
.form .text-wrapper input {
    border-radius: var(--form-card-border-radius);
    transition: all 0.2s ease;
}

.form .text-wrapper input:focus {
    transform: translateY(-1px);
    box-shadow: 0 0 0 3px rgba(var(--button-primary-color), 0.1);
}
```

**Responsive Design Integration** : utilisez des propriétés personnalisées CSS dans les requêtes de média pour obtenir un comportement réactif cohérent :

```css
@media (max-width: 768px) {
    :root {
        --form-input-padding: 0.875rem;
        --form-field-vert-gap: 1rem;
        --form-padding: 1rem;
    }
}
```

+++

### Exemple d’implémentation de style complète

Cette section explique comment créer un formulaire moderne, avec marque, à l’aide des propriétés personnalisées CSS. La mise en œuvre est divisée en sous-sections claires pour une compréhension et une navigation plus faciles.



+++ &#x200B;1. Variables de thème de marque

Définissez la palette de couleurs, l’espacement et la typographie de votre marque à l’aide des propriétés personnalisées CSS.

```css
/* Custom brand theme */
:root {
  /* Brand color system */
  --brand-primary: #2563eb;
  --brand-secondary: #64748b;
  --brand-success: #059669;
  --brand-error: #dc2626;
  --brand-background: #f8fafc;
  
  /* Override form variables */
  --background-color-primary: #ffffff;
  --button-primary-color: var(--brand-primary);
  --button-primary-hover-color: #1d4ed8;
  --form-error-color: var(--brand-error);
  --form-background-color: var(--brand-background);
  --label-color: var(--brand-secondary);
  --border-color: #d1d5db;
  
  /* Enhanced spacing */
  --form-input-padding: 1rem;
  --form-field-vert-gap: 1.5rem;
  --form-padding: 2rem;
  
  /* Modern typography */
  --form-font-size-s: 16px;
  --form-label-font-weight: 500;
}
```


+++

+++ &#x200B;2. Style du conteneur de formulaires

Appliquez un arrière-plan moderne, un rayon de bordure et une ombre au conteneur de formulaire pour une disposition visuellement attrayante.


```css
/* Enhanced form container */
.form {
    background: linear-gradient(135deg, #f8fafc 0%, #f1f5f9 100%);
    border-radius: 12px;
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.05);
    max-width: 600px;
    margin: 2rem auto;
    overflow: hidden;
}
```




+++

+++ &#x200B;3. Style des champs de saisie

Appliquez un style au texte, à l’e-mail et aux champs d’entrée numériques pour un aspect épuré et moderne.


```css
/* Modern input styling */
.form .text-wrapper input,
.form .email-wrapper input,
.form .number-wrapper input {
    background: white;
    border: 2px solid var(--border-color);
    border-radius: 8px;
    padding: var(--form-input-padding);
    font-size: 16px;
    transition: all 0.2s ease;
    width: 100%;
}
```


+++

+++ &#x200B;4. Personnalisation supplémentaire

Vous pouvez étendre davantage la mise en forme du formulaire en ciblant des champs, des états ou des composants spécifiques, si nécessaire. Reportez-vous aux sections précédentes pour obtenir des modèles avancés.

```css
/* Custom brand theme */
:root {
    /* Brand color system */
    --brand-primary: #2563eb;
    --brand-secondary: #64748b;
    --brand-success: #059669;
    --brand-error: #dc2626;
    --brand-background: #f8fafc;
    
    /* Override form variables */
    --background-color-primary: #ffffff;
    --button-primary-color: var(--brand-primary);
    --button-primary-hover-color: #1d4ed8;
    --form-error-color: var(--brand-error);
    --form-background-color: var(--brand-background);
    --label-color: var(--brand-secondary);
    --border-color: #d1d5db;
    
    /* Enhanced spacing */
    --form-input-padding: 1rem;
    --form-field-vert-gap: 1.5rem;
    --form-padding: 2rem;
    
    /* Modern typography */
    --form-font-size-s: 16px;
    --form-label-font-weight: 500;
}

/* Enhanced form container */
.form {
    background: linear-gradient(135deg, #f8fafc 0%, #f1f5f9 100%);
    border-radius: 12px;
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.05);
    max-width: 600px;
    margin: 2rem auto;
    overflow: hidden;
}

/* Modern input styling */
.form .text-wrapper input,
.form .email-wrapper input,
.form .number-wrapper input {
    background: white;
    border: 2px solid var(--border-color);
    border-radius: 8px;
    padding: var(--form-input-padding);
    font-size: 16px;
    transition: all 0.2s ease;
    width: 100%;
}

.form .text-wrapper input:focus,
.form .email-wrapper input:focus,
.form .number-wrapper input:focus {
    border-color: var(--brand-primary);
    box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
    transform: translateY(-1px);
}

/* Enhanced button styling */
.form .button-wrapper button[type="submit"] {
    background: linear-gradient(135deg, var(--brand-primary) 0%, #1d4ed8 100%);
    color: white;
    border: none;
    border-radius: 8px;
    padding: 1rem 2rem;
    font-size: 16px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.2s ease;
    width: 100%;
    box-shadow: 0 4px 12px rgba(37, 99, 235, 0.3);
}

.form .button-wrapper button[type="submit"]:hover {
    transform: translateY(-2px);
    box-shadow: 0 6px 20px rgba(37, 99, 235, 0.4);
}
```

Cette approche complète montre comment les propriétés personnalisées CSS permettent un thème sophistiqué tout en conservant l’intégrité structurelle et les fonctionnalités d’accessibilité du système de blocs de Forms adaptatif.

+++

## Résolution des problèmes CSS

+++ Problèmes de spécificité CSS

```css
/- ❌ Problem: Styles not applying */
.text-wrapper input {
  color: red;
}

/- ✅ Solution: Match or exceed existing specificity */
.form .text-wrapper input {
  color: red;
}

/- ✅ Alternative: Use higher specificity when needed */
main .form .text-wrapper input {
  color: red;
}
```

+++

+++ Problèmes de remplacement de variable CSS

```css
/- ❌ Problem: Variables not working */
.form {
  --form-border-color: blue; /- Local scope only */
}

/- ✅ Solution: Define in root scope */
:root {
  --form-border-color: blue; /- Global scope */
}
```

+++

+++ Erreurs de sélecteur courantes

```css
/- ❌ Incorrect: Assumes direct nesting */
.form form input {
  /- This might miss inputs in wrappers */
}

/- ✅ Correct: Target actual structure */
.form .text-wrapper input {
  /- Targets actual HTML structure */
}

/- ❌ Avoid: Unnecessary specificity */
main .form form .text-wrapper input {
  /- Too specific, harder to override */
}

/- ✅ Preferred: Balanced specificity */
.form .text-wrapper input {
  /- Easier to maintain and override */
}
```

+++

+++ Style de l’état du formulaire

```css
/- Validation states */
.form .field-wrapper.error input {
  border-color: var(--form-error-color);
}

.form .field-wrapper.success input {
  border-color: var(--form-success-color);
}

/- Loading state */
.form[data-submitting="true"] {
  opacity: 0.7;
  pointer-events: none;
}

/- Disabled state */
.form input:disabled {
  background-color: var(--form-input-disabled-background);
  cursor: not-allowed;
}
```

+++

### **Bonnes pratiques spécifiques aux composants**


+++ Style des boutons

```css
/- Primary buttons */
.form .button-wrapper button[type="submit"] {
  background-color: var(--form-focus-color);
  color: white;
  border: none;
  padding: var(--form-input-padding);
  border-radius: var(--form-border-radius);
}

/- Secondary buttons */
.form .button-wrapper button[type="reset"] {
  background-color: transparent;
  color: var(--form-text-color);
  border: 1px solid var(--form-border-color);
}
```

+++

+++ Conception de formulaire réactif

```css
/- Mobile-first approach */
.form {
  width: 100%;
  padding: 1rem;
}

/- Tablet and up */
@media (min-width: 768px) {
  .form {
    max-width: var(--form-max-width);
    padding: var(--form-padding);
  }
}
```

+++

## Résumé des bonnes pratiques

1. **Utiliser des propriétés personnalisées CSS** : utilisez des variables pour obtenir un thème cohérent
2. **Suivre l’architecture basée sur les blocs** : utilisez `.form` comme sélecteur de blocs principal
3. **Évitez la sur-spécificité** : n’utilisez pas `main .form form` sauf si nécessaire
4. **Wrappers Target** : utilisez des modèles de `.{Type}-wrapper` pour le ciblage des composants
5. **Maintenir la cohérence** : utilisez les mêmes modèles de sélecteur tout au long du projet
6. **Test sur tous les appareils** : assurez-vous que les formulaires fonctionnent correctement sur les appareils mobiles, les tablettes et les ordinateurs de bureau
7. **Valider l’accessibilité** : assurez-vous que les styles n’interfèrent pas avec les lecteurs d’écran ou la navigation au clavier


