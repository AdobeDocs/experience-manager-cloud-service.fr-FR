---
title: Personnalisation du thème et du style d’un formulaire de service de diffusion Edge AEM Forms
description: Personnalisation du thème et du style d’un formulaire de service de diffusion Edge AEM Forms
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 59ed012f10a20939c846c8fff088534c5638f3db
workflow-type: tm+mt
source-wordcount: '1268'
ht-degree: 0%

---


# Style des champs de formulaire

Forms est essentiel pour les interactions utilisateur sur les sites web, ce qui leur permet de saisir des données. Ce guide décrit les principes de base de la mise en forme de divers champs de formulaire dans le [Bloc de formulaire](/help/edge/docs/forms/create-forms.md), vous aidant à créer des formulaires visuellement attrayants et conviviaux.

## Présentation des types de champ de formulaire

Avant de passer à la mise en forme, examinons les types de champ de formulaire courants pris en charge par le bloc de formulaire :

* Input Fields : ces champs incluent des entrées de texte, des entrées d’e-mail, des entrées de mot de passe, etc.
* Groupes de cases à cocher : utilisés pour sélectionner plusieurs options.
* Groupes de cases d’option : utilisées pour sélectionner une seule option d’un groupe.
* Listes déroulantes : également appelées zones de sélection, utilisées pour sélectionner une option dans une liste.
* Panneaux/Conteneurs : utilisés pour regrouper les éléments de formulaire associés.

## Principes de style de base

Il est essentiel de comprendre les concepts CSS fondamentaux avant de mettre en forme des champs de formulaire spécifiques :

* Sélecteurs : les sélecteurs CSS vous permettent de cibler des éléments de HTML spécifiques pour la mise en forme. Vous pouvez utiliser des sélecteurs d’éléments, des sélecteurs de classe ou des sélecteurs d’ID.
* Propriétés : les propriétés CSS définissent l’aspect visuel des éléments. Les propriétés courantes de mise en forme des champs de formulaire sont les suivantes : couleur, couleur d’arrière-plan, bordure, remplissage, marge, etc.
* Modèle de zone : le modèle de zone CSS décrit la structure des éléments de HTML sous la forme d’une zone de contenu entourée de marge intérieure, de bordures et de marges.
* Flexbox/Grid : les mises en page Flexbox et Grille CSS sont des outils puissants pour créer des conceptions réactives et flexibles.

## Style d’un formulaire pour un bloc de formulaire

Le bloc de formulaire offre une structure de HTML normalisée, ce qui simplifie le processus de sélection et de mise en forme des composants de formulaire :

* **Mettre à jour les styles par défaut**: vous pouvez modifier les styles par défaut d’un formulaire en modifiant les `/blocks/form/form.css file`. Ce fichier fournit un style complet pour un formulaire, prenant en charge les formulaires de l’assistant en plusieurs étapes. Il met l’accent sur l’utilisation de variables CSS personnalisées pour faciliter la personnalisation, la maintenance et le style uniforme dans les formulaires. Pour plus d’informations sur l’ajout du bloc de formulaire à votre projet, reportez-vous à la section [création d’un formulaire](/help/edge/docs/forms/create-forms.md).

* **Personnalisation**: utilisez la valeur par défaut `forms.css` en tant que base et personnalisez-la pour modifier l’apparence de vos composants de formulaire, ce qui le rend visuellement attrayant et convivial. La structure du fichier encourage l’organisation et conserve les styles pour les formulaires, ce qui favorise la cohérence des conceptions sur votre site web.

## Répartition de la structure de forms.css

* **Variables globales :** Défini à l’adresse `:root` niveau, ces variables (`--variable-name`) stockent les valeurs utilisées dans toute la feuille de style pour assurer la cohérence et la facilité des mises à jour. Ces variables définissent les couleurs, la taille des polices, la marge intérieure et d’autres propriétés. Vous pouvez déclarer vos propres variables globales ou modifier les variables existantes pour modifier le style du formulaire.

* **Styles de sélecteur universels :** La variable `*` Le sélecteur correspond à chaque élément du formulaire, en veillant à ce que les styles soient appliqués par défaut à tous les composants, y compris la définition de la variable `box-sizing` de `border-box`.

* **Style du formulaire :** Cette section porte sur la mise en forme des composants de formulaire à l’aide de sélecteurs afin de cibler des éléments de HTML spécifiques. Il définit des styles pour les champs de saisie, les zones de texte, les cases à cocher, les boutons radio, les entrées de fichier, les libellés de formulaire et les descriptions.

* **Style de l’assistant (le cas échéant) :** Cette section est consacrée au style de la mise en page de l’assistant, un formulaire en plusieurs étapes dans lequel chaque étape est affichée une par une. Il définit les styles pour le conteneur de l’assistant, les jeux de champs, les légendes, les boutons de navigation et les mises en page réactives.

* **Requêtes de média :** Ils fournissent des styles pour différentes tailles d’écran, en ajustant la mise en page et le style en conséquence.

* **Style divers :**: cette section décrit les styles des messages de succès ou d’erreur, les zones de chargement de fichier et d’autres éléments que vous pouvez rencontrer dans un formulaire.


## Structure des composants

Le bloc de formulaire offre une structure de HTML cohérente pour divers éléments de formulaire, ce qui facilite la mise en forme et la gestion. Vous pouvez manipuler les composants à l’aide de CSS à des fins de style.

### Composants généraux (à l’exception des listes déroulantes, des groupes radio et des groupes de cases à cocher) :

Tous les champs de formulaire, à l’exception des listes déroulantes, des groupes radio et des groupes de cases à cocher, ont la structure de HTML suivante :

#### Structure du HTML

```HTML
<div class="form-{Type}-wrapper form-{Name} field-wrapper" data-required={Required}>
  <label for="{FieldId}" class="field-label">Field Label</label>
  <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id="{FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
  <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - Description of the field.
  </div>
</div>
```

* Classes : l’élément div comporte plusieurs classes pour le ciblage d’éléments et de styles spécifiques. Vous avez besoin de la fonction `form-{Type}-wrapper` ou `form-{Name}` classes pour développer un sélecteur CSS afin de mettre en forme un champ de formulaire :
   * {Type}: identifie le composant par type de champ. Par exemple, texte (form-text-wrapper), nombre (form-number-wrapper), date (form-date-wrapper).
   * {Name}: identifie le composant par son nom. Le nom du champ ne peut contenir que des caractères alphanumériques, les multiples tirets consécutifs du nom sont remplacés par un seul tiret. `(-)`, et les tirets de début et de fin dans un nom de champ sont supprimés. Par exemple, prénom (form-first-name field-wrapper).
   * {FieldId}: il s’agit de l’identifiant unique du champ, généré automatiquement.
   * {Required}: il s’agit d’une valeur booléenne indiquant si le champ est obligatoire.
* Libellé : `label` fournit un texte descriptif pour le champ et l’associe à l’élément de saisie à l’aide de l’élément `for` attribut.
* Input : le `input` définit le type de données à renseigner. Par exemple, texte, numéro, courrier électronique.
* Description (facultatif) : La variable `div` avec classe `field-description` fournit des informations ou des instructions supplémentaires à l’intention de l’utilisateur.

**Exemple de structure de HTML**

```HTML
<div class="form-text-wrapper form-first-name field-wrapper" data-required="true">
  <label for="firstName" class="field-label">First Name</label>
  <input type="text" placeholder="Enter your first name" maxlength="50" id="firstName" name="firstName" aria-describedby="firstName-description">
  <div class="field-description" aria-live="polite" id="firstName-description">
    Please enter your legal first name.
  </div>
</div>
```

**Sélecteur CSS pour les composants généraux**

```CSS
.form-{Type}-wrapper input {
  /* Add your styles here */
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}


.form-{Name} input {
  /* Add your styles here */
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}
```

* `.form-{Type}-wrapper`: cible l’extérieur `div` en fonction du type de champ. Par exemple : `.form-text-wrapper` cible tous les champs de saisie de texte.
* `.form-{Name}`: sélectionne davantage l’élément en fonction du nom de champ spécifique. Par exemple : `.form-first-name` cible le champ de texte &quot;Prénom&quot;.

**Exemples de sélecteurs CSS pour les composants généraux**

```CSS
/*Target all text input fields */

.form-text-wrapper input {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}

/*Target all fields with name first-name*/

.form-first-name input {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}
```


### Composant Liste déroulante

Pour les menus déroulants, la variable `select` est utilisé à la place d’un élément `input` element:


#### Structure du HTML

```HTML
<div class="form-drop-down-wrapper form-{Name} field-wrapper" data-required={required}>
  <label for="{FieldId}" class="field-label">First Name</label>
  <select id="{FieldId}" name="{Name}"><option></option><option></option></select>
  <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - First name should be minimum 3 characters and a maximum of 10 characters.
  </div>
</div>
```

**Exemple de structure de HTML**

```HTML
    <div class="form-drop-down-wrapper form-country field-wrapper" data-required="true">
      <label for="country" class="field-label">Country</label>
      <select id="country" name="country">
         <option value="">Select Country</option>
         <option value="US">United States</option>
         <option value="CA">Canada</option>
    </select>
   <div class="field-description" aria-live="polite" id="country-description">Please select your country of residence.</div>
   </div>
```

#### Exemples de sélecteurs CSS pour le composant déroulant

```CSS
/* Target the outer wrapper */
.form-drop-down-wrapper {
  /* Add your styles here */
  display: flex;
  flex-direction: column;
  margin-bottom: 15px;
}

/* Style the label */
.form-drop-down-wrapper .field-label {
  margin-bottom: 5px;
  font-weight: bold;
}

/* Style the dropdown itself */
.form-drop-down-wrapper select {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
  background-color: white; /* Ensure a consistent background */
  /* Adjust arrow appearance as needed */
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
}

/* Optional: Style the dropdown arrow */
.form-drop-down-wrapper select::-ms-expand {
  display: none; /* Hide the default arrow for IE11 */
}

.form-drop-down-wrapper select::after {
  content: "\25BC";
  font-size: 12px;
  color: #ccc;
  /* Adjust positioning as needed */
  position: absolute;
  right: 10px;
  top: 50%;
  transform: translateY(-50%);
}
```

* Ciblage du wrapper : premier sélecteur (`.form-drop-down-wrapper`) cible l’élément wrapper externe, en s’assurant que les styles s’appliquent à l’ensemble du composant déroulant.
* Mise en page de la boîte flexible : la boîte flexible organise le libellé, la liste déroulante et la description verticalement pour une mise en page propre.
* Style du libellé : le libellé se distingue par un poids de police plus lourd et une marge légère.
* Style de liste déroulante : l’élément sélectionné reçoit une bordure, une marge intérieure et des coins arrondis pour un aspect poli.
* Couleur de fond : une couleur de fond cohérente est définie pour l’harmonie visuelle.
* Personnalisation des flèches : les styles facultatifs masquent la flèche de liste déroulante par défaut et créent une flèche personnalisée à l’aide d’un caractère Unicode et d’un positionnement.

### Groupes de cases à cocher et de cases d’option

Tout comme les composants de liste déroulante, les groupes de cases d’option et de cases à cocher ont leur propre structure de HTML et des considérations CSS :

#### Structure de HTML de groupe de cases d’option

```HTML
<div class="form-checkbox-group-wrapper form-{Name} field-wrapper" data-required={required}>
  <label class="field-label">{Label Text}</label>
  <div class="checkbox-group">
    <input type="checkbox" id="{FieldId}-1" name="{Name}" value="{Value1}">
    <label for="{FieldId}-1">{Option 1 Text}</label>
    <input type="checkbox" id="{FieldId}-2" name="{Name}" value="{Value2}">
    <label for="{FieldId}-2">{Option 2 Text}</label>
    </div>
  <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - Select multiple options (if applicable).
  </div>
</div>
```


#### Structure de HTML de groupe de cases d’option

```HTML
<div class="form-checkbox-group-wrapper form-{Name} field-wrapper" data-required={required}>
  <label class="field-label">{Label Text}</label>
  <div class="checkbox-group">
    <input type="checkbox" id="{FieldId}-1" name="{Name}" value="{Value1}">
    <label for="{FieldId}-1">{Option 1 Text}</label>
    <input type="checkbox" id="{FieldId}-2" name="{Name}" value="{Value2}">
    <label for="{FieldId}-2">{Option 2 Text}</label>
    </div>
  <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - Select multiple options (if applicable).
  </div>
</div>
```

**Exemples de sélecteurs CSS pour les groupes de cases d’option et de cases à cocher**

* Ciblage du wrapper externe : ces sélecteurs ciblent les conteneurs les plus éloignés des groupes de cases d’option et de cases à cocher, ce qui vous permet d’appliquer des styles généraux à l’ensemble de la structure du groupe. Cela s’avère utile pour définir l’espacement, l’alignement ou d’autres propriétés liées à la mise en page.


  ```CSS
     /* Targets all radio group wrappers */
  .form-radio-group-wrapper {
    margin-bottom: 20px; /* Adds space between radio groups */
  }
  
  /* Targets all checkbox group wrappers */
  .form-checkbox-group-wrapper {
    margin-bottom: 20px; /* Adds space between checkbox groups */
  }
  ```


* Étiquettes de groupe de ciblage : ce sélecteur cible la variable `.field-label` élément dans les wrappers de groupes de cases d’option et de cases à cocher. Cela vous permet de mettre en forme les étiquettes spécifiquement pour ces groupes, ce qui peut les rendre plus remarquables.

  ```CSS
  .form-radio-group-wrapper .field-label,
  .form-checkbox-group-wrapper .field-label {
   font-weight: bold; /* Makes the group label bold */
  }
  ```



* Ciblage d’entrées et de libellés individuels : ces sélecteurs offrent un contrôle plus précis sur les boutons radio, cases à cocher et leurs libellés associés. Vous pouvez les utiliser pour ajuster le dimensionnement, l’espacement ou appliquer des styles visuels plus distincts.

  ```CSS
  /* Styling radio buttons */
  .form-radio-group-wrapper input[type="radio"] {
    margin-right: 5px; /* Adds space between the input and its   label */
  } 
  
  /* Styling radio button labels */
  .form-radio-group-wrapper label {
    font-size: 15px; /* Changes the label font size */
  }
  
  /* Styling checkboxes */
  .form-checkbox-group-wrapper input[type="checkbox"] {
    margin-right: 5px;  /* Adds space between the input and its  label */ 
  }
  
  /* Styling checkbox labels */
  .form-checkbox-group-wrapper label {
    font-size: 15px; /* Changes the label font size */
  }
  ```




* Personnalisation de l’aspect des boutons radio et des cases à cocher : cette technique masque l’entrée par défaut et utilise les pseudo-éléments :before et :after pour créer des visuels personnalisés qui modifient l’aspect en fonction de l’état &quot;coché&quot;.

  ```CSS
  /* Hide the default radio button or checkbox */
  .form-radio-group-wrapper input[type="radio"],
  .form-checkbox-group-wrapper input[type="checkbox"] {
    opacity: 0; 
    position: absolute; 
  }
  
  /* Create a custom radio button */
  .form-radio-group-wrapper input[type="radio"] + label::before { 
    content: "";
    display: inline-block;
    width: 16px; 
    height: 16px; 
    border: 2px solid #ccc; 
    border-radius: 50%;
    margin-right: 5px;
  }
  
  .form-radio-group-wrapper input[type="radio"]:checked +  label::before {
    background-color: #007bff; 
  }
  
  /* Create a custom checkbox */
  /* Similar styling as above, with adjustments for a square shape  */
  ```


## Mise en forme des composants

Vous pouvez également mettre en forme les champs de formulaire en fonction de leur type spécifique ou de leurs noms individuels. Cela permet un contrôle et une personnalisation plus granulaires de l’apparence de votre formulaire.

### Style basé sur le type de champ

Vous pouvez utiliser des sélecteurs CSS pour cibler des types de champ spécifiques et appliquer les styles de manière cohérente.

**Exemple de structure de HTML**

```HTML
<div class="form-text-wrapper form-name field-wrapper" data-required="true">
  <label for="name" class="field-label">Name</label>
  <input type="text" placeholder="Enter your name" maxlength="50" id="name" name="name">
</div>

<div class="form-number-wrapper form-age field-wrapper" data-required="true">
  <label for="age" class="field-label">Age</label>
  <input type="number" placeholder="Enter your age" id="age" name="age">
</div>

<div class="form-email-wrapper form-email field-wrapper" data-required="true">
  <label for="email" class="field-label">Email Address</label>
  <input type="email" placeholder="Enter your email" id="email" name="email">
</div>
```

* Chaque champ est encapsulé dans une balise `div` élément avec plusieurs classes :
   * `form-{Type}-wrapper`: identifie le type de champ. Par exemple : `form-text-wrapper`, `form-number-wrapper`, `form-email-wrapper`.
   * `form-{Name}`: identifie le champ par son nom. Par exemple `form-name`, `form-age`, `form-email`.
   * `field-wrapper`: classe générique pour tous les wrappers de champ.
* La variable `data-required` indique si le champ est obligatoire ou facultatif.
* Chaque champ comporte un libellé, un élément d’entrée et des éléments supplémentaires potentiels, tels que des espaces réservés et des descriptions.

**Exemple de sélecteurs CSS**

```CSS
/* Target all text input fields */
.form-text-wrapper input {
  /* Add your styles here */
}

/* Target all number input fields */
.form-number-wrapper input {
  /* Add your styles here */
  letter-spacing: 2px; /* Example for adding letter spacing to all number fields */
}
```

### Style basé sur le nom du champ

Vous pouvez également cibler des champs individuels par nom pour appliquer des styles uniques.

**Exemple de structure de HTML**

```HTML
<div class="form-number-wrapper form-otp field-wrapper" data-required="true">
  <label for="otp" class="field-label">OTP</label>
  <input type="number" placeholder="Enter your OTP" maxlength="6" id="otp" name="otp">
</div>
```

**Exemple de sélecteur CSS**

```CSS
.form-otp input {
   letter-spacing: 2px
}
```

Ce CSS cible tous les éléments d’entrée situés dans un élément qui possède la classe . `form-otp`. La structure de HTML de votre formulaire suit les conventions du bloc de formulaire, ce qui implique qu’il existe un conteneur marqué avec la classe &quot;form-top&quot; qui contient le champ nommé &quot;top&quot;.


