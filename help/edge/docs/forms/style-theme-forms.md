---
title: Personnalisation du thème et du style d’un formulaire de services de diffusion AEM Forms Edge
description: Personnalisation du thème et du style d’un formulaire de services de diffusion AEM Forms Edge
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: c214711c-979b-4833-9541-8e35b2aa8e09
source-git-commit: 4144f9704aaf17ea684be147395adc3aa31641f2
workflow-type: tm+mt
source-wordcount: '1821'
ht-degree: 0%

---

# Style des champs de formulaire

Forms est essentiel pour les interactions utilisateur sur les sites web, ce qui leur permet de saisir des données. Ce guide décrit les principes de base de la mise en forme de divers champs de formulaire dans le [Bloc Forms adaptatif](/help/edge/docs/forms/create-forms.md), vous aidant à créer des formulaires visuellement attrayants et conviviaux.

## Présentation des types de champ de formulaire

Avant de passer à la mise en forme, examinons les types de champs de formulaire courants pris en charge par le bloc de Forms adaptatif :

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

## Style d’un formulaire pour un bloc Forms adaptatif

Le bloc de Forms adaptatif offre une structure de HTML normalisée, ce qui simplifie le processus de sélection et de mise en forme des composants de formulaire :

* **Mettre à jour les styles par défaut**: vous pouvez modifier les styles par défaut d’un formulaire en modifiant les `/blocks/form/form.css file`. Ce fichier fournit un style complet pour un formulaire, prenant en charge les formulaires de l’assistant en plusieurs étapes. Il met l’accent sur l’utilisation de variables CSS personnalisées pour faciliter la personnalisation, la maintenance et le style uniforme dans les formulaires. Pour plus d’informations sur l’ajout du bloc Forms adaptatif à votre projet, reportez-vous à la section [création d’un formulaire](/help/edge/docs/forms/create-forms.md).

* **Personnalisation**: utilisez la valeur par défaut `forms.css` en tant que base et personnalisez-la pour modifier l’apparence de vos composants de formulaire, ce qui le rend visuellement attrayant et convivial. La structure du fichier encourage l’organisation et conserve les styles pour les formulaires, ce qui favorise la cohérence des conceptions sur votre site web.

## Répartition de la structure de forms.css

* **Variables globales :** Défini à l’adresse `:root` niveau, ces variables (`--variable-name`) stockent les valeurs utilisées dans toute la feuille de style pour assurer la cohérence et la facilité des mises à jour. Ces variables définissent les couleurs, la taille des polices, la marge intérieure et d’autres propriétés. Vous pouvez déclarer vos propres variables globales ou modifier les variables existantes pour modifier le style du formulaire.

* **Styles de sélecteur universels :** La variable `*` Le sélecteur correspond à chaque élément du formulaire, en veillant à ce que les styles soient appliqués par défaut à tous les composants, y compris la définition de la variable `box-sizing` de `border-box`.

* **Style du formulaire :** Cette section porte sur la mise en forme des composants de formulaire à l’aide de sélecteurs afin de cibler des éléments de HTML spécifiques. Il définit des styles pour les champs de saisie, les zones de texte, les cases à cocher, les boutons radio, les entrées de fichier, les libellés de formulaire et les descriptions.

* **Style de l’assistant (le cas échéant) :** Cette section est consacrée au style de la mise en page de l’assistant, un formulaire en plusieurs étapes dans lequel chaque étape est affichée une par une. Il définit les styles pour le conteneur de l’assistant, les jeux de champs, les légendes, les boutons de navigation et les mises en page réactives.

* **Requêtes de média :** Ils fournissent des styles pour différentes tailles d’écran, en ajustant la mise en page et le style en conséquence.

* **Style divers :**: cette section décrit les styles des messages de succès ou d’erreur, les zones de chargement de fichier et d’autres éléments que vous pouvez rencontrer dans un formulaire.


## Structure des composants

Le bloc de Forms adaptatif offre une structure de HTML cohérente pour divers éléments de formulaire, assurant ainsi un style et une gestion plus simples. Vous pouvez manipuler les composants à l’aide de CSS à des fins de style.

### Composants généraux (à l’exception des listes déroulantes, des groupes radio et des groupes de cases à cocher) :

Tous les champs de formulaire, à l’exception des listes déroulantes, des groupes radio et des groupes de cases à cocher, ont la structure de HTML suivante :

#### Structure du HTML

```HTML
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   <label for="{FieldId}" class="field-label">First Name</label>
   <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - First name should be minimum 3 characters and a maximum of 10 characters.
   </div>
</div>
```

* Classes : l’élément div comporte plusieurs classes pour le ciblage d’éléments et de styles spécifiques. Vous avez besoin de la fonction `{Type}-wrapper` ou `field-{Name}` classes pour développer un sélecteur CSS afin de mettre en forme un champ de formulaire :
   * {Type}: identifie le composant par type de champ. Par exemple, texte (wrapper de texte), nombre (wrapper de nombre), date (wrapper de date).
   * {Name}: identifie le composant par son nom. Le nom du champ ne peut contenir que des caractères alphanumériques, les multiples tirets consécutifs du nom sont remplacés par un seul tiret. `(-)`, et les tirets de début et de fin dans un nom de champ sont supprimés. Par exemple, prénom (champ-prénom-champ-wrapper).
   * {FieldId}: il s’agit de l’identifiant unique du champ, généré automatiquement.
   * {Required}: il s’agit d’une valeur booléenne indiquant si le champ est obligatoire.
* Libellé : `label` fournit un texte descriptif pour le champ et l’associe à l’élément de saisie à l’aide de l’élément `for` attribut.
* Input : le `input` définit le type de données à renseigner. Par exemple, texte, numéro, courrier électronique.
* Description (facultatif) : La variable `div` avec classe `field-description` fournit des informations ou des instructions supplémentaires à l’intention de l’utilisateur.

**Exemple de structure de HTML**

```HTML
<div class="text-wrapper field-first-name field-wrapper" data-required="true">
  <label for="firstName" class="field-label">First Name</label>
  <input type="text" placeholder="Enter your first name" maxlength="50" id="firstName" name="firstName" aria-describedby="firstName-description">
  <div class="field-description" aria-live="polite" id="firstName-description">
    Please enter your legal first name.
  </div>
</div>
```

**Sélecteur CSS pour les composants généraux**

```CSS
/* Target all input fields within any .{Type}-wrapper  */
.{Type}-wrapper  {
  /* Add your styles here */
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}

/* Target all input fields within any .{Type}-wrapper  */
.{Type}-wrapper input {
  /* Add your styles here */
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}

/* Target any element with the class field-{Name}  */
.field-{Name} {
  /* Add your styles here */
  /* This could be used for styles specific to all elements with field-{Name} class, not just inputs */
}
```

* `.{Type}-wrapper`: cible l’extérieur `div` en fonction du type de champ. Par exemple : `.text-wrapper` cible tous les champs de texte.
* `.field-{Name}`: sélectionne davantage l’élément en fonction du nom de champ spécifique. Par exemple : `.field-first-name` cible le champ de texte &quot;Prénom&quot;. Bien que ce sélecteur puisse être utilisé pour le ciblage des éléments avec le champ -{Name} en classe, il est important d&#39;être prudent. Dans ce cas spécifique, il ne serait pas très utile de mettre en forme les champs de saisie, car il ciblerait non seulement la saisie elle-même, mais aussi les éléments de libellé et de description. Il est généralement recommandé d’utiliser des sélecteurs plus spécifiques comme ceux que vous avez pour cibler les champs de saisie de texte (entrée .text-wrapper).



**Exemples de sélecteurs CSS pour les composants généraux**

```CSS
/*Target all text input fields */

text-wrapper input {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}

/*Target all fields with name first-name*/

first-name input {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}
```


### Composant Liste déroulante

Pour les menus déroulants, la variable `select` est utilisé à la place d’un élément `input` element:


#### Structure du HTML

```HTML
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={required}>
   <label for="{FieldId}" class="field-label">First Name</label>
   <select id="{FieldId}" name="{Name}"><option></option><option></option></select>
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - First name should be minimum 3 characters and a maximum of 10 characters.
   </div>
</div>
```

**Exemple de structure de HTML**

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

#### Exemples de sélecteurs CSS pour le composant déroulant

```CSS
/* Target the outer wrapper */
.drop-down-wrapper {
  /* Add your styles here */
  display: flex;
  flex-direction: column;
  margin-bottom: 15px;
}

/* Style the label */
.drop-down-wrapper .field-label {
  margin-bottom: 5px;
  font-weight: bold;
}

/* Style the dropdown itself */
.drop-down-wrapper select {
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
.drop-down-wrapper select::-ms-expand {
  display: none; /* Hide the default arrow for IE11 */
}

.drop-down-wrapper select::after {
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

* Ciblage du wrapper : premier sélecteur (`.drop-down-wrapper`) cible l’élément wrapper externe, en s’assurant que les styles s’appliquent à l’ensemble du composant déroulant.
* Mise en page de la boîte flexible : la boîte flexible organise le libellé, la liste déroulante et la description verticalement pour une mise en page propre.
* Style du libellé : le libellé se distingue par un poids de police plus lourd et une marge légère.
* Style de liste déroulante : l’élément sélectionné reçoit une bordure, une marge intérieure et des coins arrondis pour un aspect poli.
* Couleur de fond : une couleur de fond cohérente est définie pour l’harmonie visuelle.
* Personnalisation des flèches : les styles facultatifs masquent la flèche de liste déroulante par défaut et créent une flèche personnalisée à l’aide d’un caractère Unicode et d’un positionnement.

### Groupes radio

Tout comme les composants de liste déroulante, les groupes radio ont leur propre structure de HTML et structure CSS :

#### Structure de HTML de groupe de cases d’option

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

#### Exemple de structure de HTML

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

#### Exemples de sélecteurs CSS pour le composant déroulant

* Ciblage du jeu de champs

```CSS
  .radio-group-wrapper {
    border: 1px solid #ccc;
    padding: 10px;
  }
```

Ce sélecteur cible n’importe quel champ avec la classe radiogroup-wrapper. Cela s’avère utile pour appliquer des styles généraux à l’ensemble du groupe de cases d’option.

* Étiquettes de bouton radio de ciblage

```CSS
.radio-wrapper label {
    font-weight: normal;
    margin-right: 10px;
  }
```

* Cibler tous les libellés de bouton radio dans un jeu de champs spécifique en fonction de son nom

```CSS
.field-color .radio-wrapper label {
  /* Your styles here */
}
```

### Groupes de cases à cocher

#### Structure de HTML de groupe de cases à cocher

```HTML
<fieldset class="checkbox-group-wrapper field-{Name} field-wrapper" id="{FieldId}" name="{Name}" data-required="{Required}">
   <legend for="{FieldId}" class="field-label">....</legend>
   <% for each radio in Group %>
   <div class="radio-wrapper field-{Name}">
      <input type="checkbox" value="" id="{UniqueId}" data-field-type="checkbox-group" name="{FieldId}">
      <label for="{UniqueId}" class="field-label">...</label>
   </div>
   <% end for %>
</fieldset>
```

#### Exemple de structure de HTML

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

**Exemples de sélecteurs CSS pour les groupes de cases d’option et de cases à cocher**

* Ciblage du wrapper externe : ces sélecteurs ciblent les conteneurs les plus éloignés des groupes de cases d’option et de cases à cocher, ce qui vous permet d’appliquer des styles généraux à l’ensemble de la structure du groupe. Cela s’avère utile pour définir l’espacement, l’alignement ou d’autres propriétés liées à la mise en page.


  ```CSS
     /* Targets radio group wrappers */
       .radio-group-wrapper {
       margin-bottom: 20px; /* Adds space between radio groups */  
     }
  
     /* Targets checkbox group wrappers */
     .checkbox-group-wrapper {
     margin-bottom: 20px; /* Adds space between checkbox groups */
     }
  ```


* Étiquettes de groupe de ciblage : ce sélecteur cible la variable `.field-label` élément dans les wrappers de groupes de cases d’option et de cases à cocher. Cela vous permet de mettre en forme les étiquettes spécifiquement pour ces groupes, ce qui peut les rendre plus remarquables.

  ```CSS
   .radio-group-wrapper legend,
   .checkbox-group-wrapper legend {
     font-weight: bold; /* Makes the group label bold */
   }
  ```



* Ciblage d’entrées et de libellés individuels : ces sélecteurs offrent un contrôle plus précis sur les boutons radio, cases à cocher et leurs libellés associés. Vous pouvez les utiliser pour ajuster le dimensionnement, l’espacement ou appliquer des styles visuels plus distincts.

  ```CSS
  /* Styling radio buttons */
   .radio-group-wrapper input[type="radio"] {
     margin-right: 5px; /* Adds space between the input and its label */
   }
  
   /* Styling radio button labels */
   .radio-group-wrapper label {
     font-size: 15px; /* Changes the label font size */
   }
  
  /* Styling checkboxes */
   .checkbox-group-wrapper input[type="checkbox"] {
     margin-right: 5px; /* Adds space between the input and its label */
   }
  
   /* Styling checkbox labels */
   .checkbox-group-wrapper label {
     font-size: 15px; /* Changes the label font size */
   }
  ```




* Personnalisation de l’aspect des boutons radio et des cases à cocher : cette technique masque l’entrée par défaut et utilise les pseudo-éléments :before et :after pour créer des visuels personnalisés qui modifient l’aspect en fonction de l’état &quot;coché&quot;.

  ```CSS
  /* Hide the default radio button or checkbox */
     .radio-group-wrapper input[type="radio"],
     .checkbox-group-wrapper input[type="checkbox"] {
       opacity: 0;
       position: absolute;
     }
  
     /* Create a custom radio button */
     .radio-group-wrapper input[type="radio"] + label::before {
       /* ... styles for custom radio button ... */
     }
  
     .radio-group-wrapper input[type="radio"]:checked + label::before {
       /* ... styles for checked radio button ... */
     }
  
     /* Create a custom checkbox */
     /* Similar styling as above, with adjustments for a square shape  */
     .checkbox-group-wrapper input[type="checkbox"] + label::before {
       /* ... styles for custom checkbox ... */
     }
  
     .checkbox-group-wrapper input[type="checkbox"]:checked + label::before {
       /* ... styles for checked checkbox ... */
     }
  ```

### Composants de panneau/conteneur

#### Structure du HTML

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

**Exemple de structure de HTML**

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

* L’élément fieldset fait office de conteneur de panneau avec la classe panel-wrapper et des classes supplémentaires pour le style en fonction du nom du panneau (field-login).
* L’élément de légende (<legend>) sert de titre de panneau avec le texte &quot;Informations de connexion&quot; et le libellé du champ de classe. L&#39;attribut data-visible=&quot;false&quot; peut être utilisé avec JavaScript pour contrôler la visibilité du titre.
* Dans le jeu de champs, plusieurs .{Type}Les éléments -wrapper (.text-wrapper et .password-wrapper, dans ce cas) représentent des champs de formulaire individuels dans le panneau.
* Chaque wrapper contient un libellé, un champ de saisie et une description, comme dans les exemples précédents.

#### Sélecteurs CSS et exemples

1. Ciblage du panneau :

```CSS
  /* Target the entire panel container */
  .panel-wrapper {
    /* Add your styles here (e.g., border, padding, background color) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
 }
```

* La variable `.panel-wrapper` le sélecteur met en forme tous les éléments à l’aide de la classe panel-wrapper, créant ainsi une apparence cohérente pour tous les panneaux.

1. Ciblage du titre du panneau :

```CSS
  /* Target the legend element (panel title) */
  .panel-wrapper legend {
    /* Add your styles here (e.g., font-weight, font-size) */
    font-weight: bold;
    font-size: 16px;
    padding-bottom: 5px;
    margin-bottom: 10px;
    border-bottom: 1px solid #ddd; /* Optional: create a separation line */
  }
```

* La variable `.panel-wrapper legend` Le sélecteur met en forme l’élément de légende dans le panneau, ce qui permet de distinguer visuellement le titre.


1. Ciblage de champs individuels dans le panneau :

```CSS
/* Target all form field wrappers within a panel */
.panel-wrapper .{Type}-wrapper {
  /* Add your styles here (e.g., margin) */
  margin-bottom: 10px;
}
```

* La variable `.panel-wrapper .{Type}-wrapper` le sélecteur cible tous les wrappers avec la propriété `.{Type}-wrapper` dans le panneau , ce qui vous permet de mettre en forme l’espacement entre les champs de formulaire.

1. Ciblage de champs spécifiques (facultatif) :

```CSS
  /* Target the username field wrapper */
  .panel-wrapper .text-wrapper.field-username {
    /* Add your styles here (specific to username field) */
  }

  /* Target the password field wrapper */
  .panel-wrapper .password-wrapper.field-password {
    /* Add your styles here (specific to password field) */
  }
```

* Ces sélecteurs facultatifs vous permettent de cibler des wrappers de champ spécifiques dans le panneau pour un style unique, comme la mise en surbrillance du champ nom d’utilisateur.

### Panneau répétable

#### Structure du HTML

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

**Exemple de structure de HTML**

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

Chaque panneau possède la même structure que l’exemple de panneau unique, avec des attributs supplémentaires :

* data-repeatable=&quot;true&quot; : cet attribut indique que le panneau peut être répété dynamiquement à l’aide de JavaScript ou d’une structure.

* Identifiants et noms uniques : chaque élément du panneau possède un identifiant unique (par exemple, nom-1, email-1) et un attribut name basé sur l’index du panneau (par exemple, nom=&quot;contacts&quot;[0].name&quot;). Cela permet une collecte de données correcte lorsque plusieurs panneaux sont envoyés.



#### Sélecteurs CSS et exemples

* Ciblage de tous les panneaux répétables :

```CSS
  /* Target all panels with the repeatable attribute */
  .panel-wrapper[data-repeatable="true"] {
    /* Add your styles here (e.g., border, margin) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
  }
```

Le sélecteur met en forme tous les panneaux qui peuvent être répétés, assurant ainsi un aspect cohérent.


* Ciblage de champs individuels dans un panneau :

```CSS
/* Target all form field wrappers within a repeatable panel */
.panel-wrapper[data-repeatable="true"] .{Type}-wrapper {
  /* Add your styles here (e.g., margin) */
  margin-bottom: 10px;
}
```
Ce sélecteur met en forme tous les wrappers de champ dans un panneau répétable, en maintenant un espacement cohérent entre les champs.

* Ciblage de champs spécifiques (dans un panneau) :

```CSS
/* Target the name field wrapper within the first panel */
.panel-wrapper[data-repeatable="true"][data-index="0"] .text-wrapper.field-name {
  /* Add your styles here (specific to first name field) */
}

/* Target all
```

### Pièce jointe


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

**Exemple de structure de HTML**


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

* L’attribut class utilise le nom fourni pour la pièce jointe (request_form).
* Les attributs id et name de l’élément d’entrée correspondent au nom de la pièce jointe du fichier (request_form).
* La section liste de fichiers est initialement vide. Il est renseigné dynamiquement avec JavaScript lors du chargement des fichiers.


**Sélecteurs CSS et exemples :**

* Ciblage de l’intégralité du composant Pièce jointe :

```CSS
/* Target the entire file attachment component */
.file-wrapper {
  /* Add your styles here (e.g., border, padding) */
  border: 1px solid #ccc;
  padding: 15px;
  border-radius: 4px;
  margin-bottom: 20px;
}
```

Ce sélecteur met en forme l’ensemble du composant de pièce jointe du fichier, y compris la légende, la zone de glisser, le champ d’entrée et la liste.

* Ciblage d’éléments spécifiques :

```CSS
/* Target the drag and drop area */
.file-wrapper .file-drag-area {
  /* Add your styles here (e.g., background color, border) */
  background-color: #f0f0f0;
  border: 1px dashed #ddd;
  padding: 10px;
  text-align: center;
}

/* Target the file input element */
.file-wrapper input[type="file"] {
  /* Add your styles here (e.g., hide the default input) */
  display: none;
}

/* Target individual file descriptions within the list (populated dynamically) */
.file-wrapper .files-list .file-description {
  /* Add your styles here (e.g., margin, display) */
  display: flex;
  justify-content: space-between;
  margin-bottom: 5px;
}

/* Target the file name within the description */
.file-wrapper .files-list .file-description .file-description-name {
  /* Add your styles here (e.g., font-weight) */
  font-weight: bold;
}

/* Target the file size within the description */
.file-wrapper .files-list .file-description .file-description-size {
  /* Add your styles here (e.g., font-size) */
  font-size: 0.8em;
}

/* Target the remove button within the description */
.file-wrapper .files-list .file-description .file-description-remove {
  /* Add your styles here (e.g., background color, hover effect) */
  background-color: transparent;
  border: none;
  cursor: pointer;
}
```

Ces sélecteurs vous permettent de mettre en forme individuellement différentes parties du composant de pièce jointe au fichier. Vous pouvez ajuster les styles en fonction de vos préférences de conception.


## Mise en forme des composants

Vous pouvez également mettre en forme les champs de formulaire en fonction de leur type spécifique ou de leurs noms individuels. Cela permet un contrôle et une personnalisation plus granulaires de l’apparence de votre formulaire.

### Style basé sur le type de champ

Vous pouvez utiliser des sélecteurs CSS pour cibler des types de champ spécifiques et appliquer les styles de manière cohérente.

**Exemple de structure de HTML**

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

* Chaque champ est encapsulé dans une balise `div` élément avec plusieurs classes :
   * `{Type}-wrapper`: identifie le type de champ. Par exemple : `form-text-wrapper`, `form-number-wrapper`, `form-email-wrapper`.
   * `field-{Name}`: identifie le champ par son nom. Par exemple `form-name`, `form-age`, `form-email`.
   * `field-wrapper`: classe générique pour tous les wrappers de champ.
* La variable `data-required` indique si le champ est obligatoire ou facultatif.
* Chaque champ comporte un libellé, un élément d’entrée et des éléments supplémentaires potentiels, tels que des espaces réservés et des descriptions.

**Exemple de sélecteurs CSS**

```CSS
/* Target all text input fields */
.text-wrapper input {
  /* Add your styles here */
}

/* Target all number input fields */
.number-wrapper input {
  /* Add your styles here */
  letter-spacing: 2px; /* Example for adding letter spacing to all number fields */
}
```

### Style basé sur le nom du champ

Vous pouvez également cibler des champs individuels par nom pour appliquer des styles uniques.

**Exemple de structure de HTML**

```HTML
<div class="number-wrapper field-otp field-wrapper" data-required="true">
  <label for="otp" class="field-label">OTP</label>
  <input type="number" placeholder="Enter your OTP" maxlength="6" id="otp" name="otp">
</div>
```

**Exemple de sélecteur CSS**

```CSS
.field-otp input {
   letter-spacing: 2px
}
```

Ce CSS cible tous les éléments d’entrée situés dans un élément qui possède la classe . `field-otp`. La structure de HTML de votre formulaire suit les conventions du bloc Forms adaptatif, ce qui implique qu’il existe un conteneur marqué avec la classe &quot;field-top&quot; qui contient le champ nommé &quot;top&quot;.

## Voir également

{{see-more-forms-eds}}