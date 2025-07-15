---
title: Personnaliser le thème et le style d’un Edge Delivery Services pour AEM Forms
description: Personnalisez efficacement le thème et le style des formulaires AEM Forms diffusés via Edge Delivery Services, afin d’offrir une expérience client cohérente et conforme à la marque.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: ac780399-34fe-457d-aaf4-b675656c024d
source-git-commit: 9ef4c5638c2275052ce69406f54dda3ea188b0ef
workflow-type: tm+mt
source-wordcount: '1833'
ht-degree: 94%

---

# Personnaliser l’apparence de vos formulaires

<span class="preview"> Il s’agit d’une fonctionnalité en version préliminaire disponible via notre <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=fr#new-features">canal de version préliminaire</a>. </span>


Les formulaires sont essentiels pour les interactions des utilisateurs et des utilisatrices sur les sites web, car cela leur permet de saisir des données. Vous pouvez utiliser des feuilles de style en cascade (CSS) pour mettre en forme les champs d’un formulaire, améliorer la présentation visuelle de vos formulaires et améliorer l’expérience client.

Le bloc de formulaires adaptatifs crée une structure cohérente pour tous les champs de formulaire. La structure cohérente facilite le développement de sélecteurs CSS pour sélectionner et mettre en forme les champs de formulaire en fonction du type de champ et des noms des champs.

Ce document décrit la structure du HTML pour divers composants de formulaire. Il vous aide à mieux comprendre comment créer des sélecteurs CSS pour divers champs de formulaire afin de mettre en forme les champs de formulaire d’un bloc de formulaires adaptatifs.

À la fin de l’article :

* Vous comprenez la structure du fichier CSS par défaut inclus dans le bloc de formulaires adaptatifs.
* Vous comprendrez la structure HTML des composants de formulaire fournis par le bloc de formulaires adaptatifs, notamment les composants généraux et des composants spécifiques tels que les listes déroulantes, les groupes de boutons radio et les groupes de cases à cocher.
* Vous apprenez à définir le style de champs de formulaire en fonction du type de champ et des noms de champ à l’aide de sélecteurs CSS, ce qui permet d’obtenir un style cohérent ou unique en fonction des besoins.

## Présentation des types de champs de formulaire

Avant de passer à la définition du style, examinons les [types de champs](/help/edge/docs/forms/universal-editor/create-custom-component.md#supported-fieldtypes) de formulaire communs pris en charge par le bloc de formulaires adaptatifs :

* Champs d’entrée : ces champs incluent des entrées de texte, des entrées d’e-mail, des entrées de mot de passe, et bien plus encore.
* Groupes de cases à cocher : utilisés pour sélectionner plusieurs options.
* Groupes de boutons radio : utilisés pour sélectionner une seule option dans un groupe.
* Listes déroulantes : également appelées zones de sélection, utilisées pour sélectionner une option dans une liste.
* Panneaux/Conteneurs : utilisés pour regrouper les éléments de formulaire associés.

## Principes de base de la définition du style

Il est essentiel de comprendre les [concepts de base de CSS](https://www.w3schools.com/css/css_intro.asp) avant de définir le style de champs de formulaire spécifiques :

* [Sélecteurs](https://www.w3schools.com/css/css_selectors.asp) : les sélecteurs CSS vous permettent de cibler des éléments HTML spécifiques pour la définition du style. Vous pouvez utiliser des sélecteurs d’éléments, des sélecteurs de classe ou des sélecteurs d’ID.
* [Propriétés](https://www.w3schools.com/css/css_syntax.asp) : les propriétés CSS définissent l’apparence visuelle des éléments. Les propriétés courantes de définition du style des champs de formulaire incluent les suivantes : couleur, couleur d’arrière-plan, bordure, remplissage, marge, et bien plus encore.
* [Modèle de zone](https://www.w3schools.com/css/css_boxmodel.asp) : le modèle de zone CSS décrit la structure des éléments HTML sous la forme d’une zone de contenu entourée d’un remplissage, de bordures et de marges.
* Flexbox/Grille : les dispositions de [Flexbox](https://www.w3schools.com/css/css3_flexbox.asp) et de [grille](https://www.w3schools.com/css/css_grid.asp) CSS sont des outils puissants pour créer des conceptions réactives et flexibles.


## Définir le style d’un formulaire pour un bloc de formulaires adaptatifs

Le bloc de formulaires adaptatifs offre une structure HTML normalisée, ce qui simplifie le processus de sélection et de définition du style des composants de formulaire :

* **Mettre à jour les styles par défaut** : vous pouvez modifier les styles par défaut d’un formulaire en modifiant les `/blocks/form/form.css file`. Ce fichier fournit une définition de style de formulaire complet, qui prend en charge les formulaires de l’assistant en plusieurs étapes. Il met l’accent sur l’utilisation de variables CSS personnalisées pour faciliter la personnalisation, la maintenance et la définition d’un style uniforme entre les formulaires.

* **Style CSS pour les formulaires** : pour vous assurer que vos styles sont appliqués correctement, enveloppez le fichier CSS spécifique au formulaire dans le sélecteur de `main .form form`. Cela garantit que vos styles ciblent uniquement les éléments de formulaire dans la zone de contenu principale, évitant les conflits avec d’autres parties du site web.

  Exemple :

  ```css
  main .form form .{Type}-wrapper input {
      /* Add styles specific to input fields inside the form */
  }
  
  main .form form .{Type}-wrapper button {
      /* Add styles specific to buttons inside the form */
  }
  
  main .form form .{Type}-wrapper label {
      /* Add styles specific to labels inside the form */
  }
  ```

## Structure des composants

Le bloc Formulaires adaptatifs offre une structure HTML cohérente pour divers éléments de formulaire, simplifiant ainsi la définition de style et la gestion. Vous pouvez manipuler les composants à l’aide de CSS à des fins de définition de style.

### Composants généraux (à l’exception des listes déroulantes, des groupes de boutons radio et des groupes de cases à cocher) :

Tous les champs de formulaire, à l’exception des listes déroulantes, des groupes de boutons radio et des groupes de cases à cocher, présentent la structure HTML suivante :

+++ Structure HTML des composants généraux

```HTML
  <div class="{Type}-wrapper field-{Name}   field-wrapper" data-required={Required}>
     <label for="{FieldId}" class="field-label">First   Name</label>
     <input type="{Type}" placeholder="{Placeholder}"   maxlength="{Max}" id={FieldId}" name="{Name}"   aria-describedby="{FieldId}-description">
     <div class="field-description" aria-live="polite"  id="{FieldId}-description">
      Hint - First name should be minimum 3 characters  and a maximum of 10 characters.
     </div>
  </div>
```

* Classes : l’élément div comporte plusieurs classes pour le ciblage d’éléments et de définitions de styles spécifiques. Vous avez besoin des classes `{Type}-wrapper` ou `field-{Name}` pour développer un sélecteur CSS afin de définir le style d’un champ de formulaire :
* {Type} : identifie le composant par type de champ. Par exemple, texte (text-wrapper), nombre (number-wrapper), date (date-wrapper).
* {Name} : identifie le composant par son nom. Le nom du champ ne peut contenir que des caractères alphanumériques, les tirets consécutifs multiples dans le nom sont remplacés par un seul tiret `(-)`, et les tirets de début et de fin dans le nom d’un champ sont supprimés. Par exemple, first-name (field-first-name field-wrapper).
* {FieldId} : il s’agit d’un identifiant unique pour le champ, généré automatiquement.
* {Required} : valeur booléenne indiquant si le champ est obligatoire.
* Libellé : l’élément `label` fournit un texte descriptif pour le champ et l’associe à l’élément d’entrée à l’aide de l’attribut `for`.
* Entrée : l’élément `input` définit le type de données à renseigner. Par exemple : texte, nombre, e-mail.
* Description (facultatif) : `div` avec la classe `field-description` fournit des informations ou des instructions supplémentaires à l’intention de l’utilisateur ou de l’utilisatrice.

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

+++

+++ Sélecteur CSS pour les composants généraux

```CSS
  
  /* Target all input fields within any .{Type}-wrapper  */
  main .form form .{Type}-wrapper  {
    /* Add your styles here */
    border: 1px solid #ccc;
    padding: 8px;
    border-radius: 4px;
  }
  
  /* Target all input fields within any .{Type}-wrapper  */
  main .form form .{Type}-wrapper input {
    /* Add your styles here */
    border: 1px solid #ccc;
    padding: 8px;
    border-radius: 4px;
  }
  
  /* Target any element with the class field-{Name}  */
  main .form form .field-{Name} {
    /* Add your styles here */
    /* This could be used for styles specific to all elements with   field-{Name} class, not just inputs */
  }
  
```
* `.{Type}-wrapper` : cible l’élément `div` externe en fonction du type de champ. Par exemple : `.text-wrapper` cible tous les champs de texte.
* `.field-{Name}` : affine la sélection de l’élément en fonction du nom de champ spécifique. Par exemple, `.field-first-name` cible le champ de texte « Prénom ». Bien que ce sélecteur puisse être utilisé pour cibler les éléments avec la classe field-{Name} , il est important d’être prudent. Dans ce cas spécifique, il ne serait pas utile de définir le style de champs d’entrée, car cela ciblerait non seulement l’entrée elle-même, mais également les éléments de libellé et de description. Il est recommandé d’utiliser des sélecteurs plus spécifiques comme ceux dont vous disposez pour cibler les champs d’entrée de texte (entrée .text-wrapper).

**Exemples de sélecteurs CSS pour les composants généraux**

```CSS
/*Target all text input fields */
main .form form .text-wrapper input {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
  color: red;
}

/*Target all fields with name first-name*/
main .form form .field-first-name input {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}
```

+++

### Composant de liste déroulante

Pour les menus déroulants, l’élément `select` est utilisé à la place d’un élément `input` :

+++ Structure HTML du composant de liste déroulante

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

+++

+++ Sélecteurs CSS pour le composant de liste déroulante

Le CSS suivant répertorie des exemples de sélecteurs CSS pour les composants de liste déroulante.

```CSS
/* Target the outer wrapper */
main .form form .drop-down-wrapper {
  /* Add your styles here */
  display: flex;
  flex-direction: column;
  margin-bottom: 15px;
}

/* Style the label */
main .form form .drop-down-wrapper .field-label {
  margin-bottom: 5px;
  font-weight: bold;
}
```
* Cibler le wrapper : le premier sélecteur (`.drop-down-wrapper`) cible l’élément wrapper externe, assurant ainsi l’application des styles à l’ensemble du composant de liste déroulante.
* Disposition Flexbox : Flexbox organise le libellé, la liste déroulante et la description verticalement pour une disposition claire.
* Définition du style de libellé : le libellé se distingue par une police plus épaisse et une légère marge.
* Définition du style de liste déroulante : l’élément `select` comprend une bordure, un remplissage et des coins arrondis pour un aspect lisse.
* Couleur d’arrière-plan : une couleur d’arrière-plan cohérente est définie à des fins d’harmonie visuelle.
* Personnalisation des flèches : des styles facultatifs masquent la flèche de liste déroulante par défaut et créent une flèche personnalisée à l’aide d’un caractère Unicode et d’un positionnement.

+++

---

### Groupes de boutons radio

Tout comme les composants de liste déroulante, les groupes de boutons radio présentent une structure HTML et une structure CSS qui leur sont propres :

+++ Structure HTML du groupe de boutons radio

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

+++

+++ Sélecteurs CSS pour les groupes de boutons radio

* Ciblage de filedset

```CSS
  main .form form .radio-group-wrapper {
    border: 1px solid #ccc;
    padding: 10px;
  }
```
Ce sélecteur cible n’importe quel fieldset avec la classe radio-group-wrapper. Cela s’avère utile pour appliquer des styles généraux à l’ensemble du groupe de boutons radio.

* Ciblage des libellés de boutons radio

```CSS
main .form form .radio-wrapper label {
    font-weight: normal;
    margin-right: 10px;
  }
```

* Cibler tous les libellés de bouton radio dans un fieldset spécifique en fonction de son nom

```CSS
main .form form .field-color .radio-wrapper label {
  /* Your styles here */
}
```

+++

### Groupes de cases à cocher

+++ Structure HTML du groupe de cases à cocher

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

+++

+++ Sélecteurs CSS pour les groupes de cases à cocher

* Ciblage du wrapper externe : ces sélecteurs ciblent les conteneurs les plus éloignés des groupes de boutons radio et de cases à cocher, vous permettant ainsi d’appliquer des styles généraux à l’ensemble de la structure du groupe. Cela s’avère utile pour définir l’espacement, l’alignement ou d’autres propriétés liées à la disposition.

```CSS
  
  /* Targets radio group wrappers */
  main .form form .radio-group-wrapper {
    margin-bottom: 20px; /* Adds space between radio groups */  
  }

  /* Targets checkbox group wrappers */
  main .form form .checkbox-group-wrapper {
    margin-bottom: 20px; /* Adds space between checkbox groups */
  }
```

* Ciblage des libellés de groupes : ce sélecteur cible l’élément `.field-label` dans les wrappers de groupes de boutons radio et de cases à cocher. Cela vous permet de définir le style des libellés propres à ces groupes, ce qui peut les rendre plus remarquables.

```CSS
main .form form .radio-group-wrapper legend,
main .form form .checkbox-group-wrapper legend {
  font-weight: bold; /* Makes the group label bold */
}
```

* Ciblage d’entrées et de libellés individuels : ces sélecteurs offrent un contrôle plus précis sur les boutons radio et cases à cocher individuels et les libellés qui leur sont associés. Vous pouvez les utiliser pour ajuster le dimensionnement, l’espacement ou appliquer des styles visuels plus distincts.

```CSS
/* Styling radio buttons */
main .form form .radio-group-wrapper input[type="radio"] {
  margin-right: 5px; /* Adds space between the input and its label */
}

/* Styling radio button labels */
main .form form .radio-group-wrapper label {
  font-size: 15px; /* Changes the label font size */
}

/* Styling checkboxes */
main .form form .checkbox-group-wrapper input[type="checkbox"] {
  margin-right: 5px; /* Adds space between the input and its label */
}

/* Styling checkbox labels */
main .form form .checkbox-group-wrapper label {
  font-size: 15px; /* Changes the label font size */
}
```

* Personnalisation de l’apparence des boutons radio et des cases à cocher : cette technique masque l’entrée par défaut et utilise les pseudo-éléments `:before` et `:after` pour créer des visuels personnalisés qui modifient l’apparence en fonction de l’état « coché ».

```CSS
/* Hide the default radio button or checkbox */
main .form form .radio-group-wrapper input[type="radio"],
main .form form .checkbox-group-wrapper input[type="checkbox"] {
  opacity: 0;
  position: absolute;
}

/* Create a custom radio button */
main .form form .radio-group-wrapper input[type="radio"] + label::before {
  /* ... styles for custom radio button ... */
}

main .form form .radio-group-wrapper input[type="radio"]:checked + label::before {
  /* ... styles for checked radio button ... */
}

/* Create a custom checkbox */
main .form form .checkbox-group-wrapper input[type="checkbox"] + label::before {
  /* ... styles for custom checkbox ... */
}

main .form form .checkbox-group-wrapper input[type="checkbox"]:checked + label::before {
  /* ... styles for checked checkbox ... */
}
```

+++

### Composants de panneau/conteneur

+++ Structure HTML des composants de panneau/conteneur

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

* L’élément fieldset fait office de conteneur de panneau avec la classe panel-wrapper et des classes supplémentaires pour définir le style en fonction du nom du panneau (field-login).
* L’élément de légende (<legend>) sert de titre de panneau avec le texte « Informations de connexion » et la classe field-label. L’attribut data-visible=&quot;false&quot; peut être utilisé avec JavaScript pour contrôler la visibilité du titre.
* Dans le fieldset, plusieurs éléments.Les éléments {Type}-wrapper (.text-wrapper et .password-wrapper dans ce cas) représentent des champs de formulaire individuels dans le panneau.
* Chaque wrapper contient un libellé, un champ d’entrée et une description, comme dans les exemples précédents.

+++

+++ Exemples de sélecteurs CSS pour les composants de panneau/conteneur

1. Ciblage du panneau :

```CSS
  /* Target the entire panel container */
  main .form form .panel-wrapper {
    /* Add your styles here (e.g., border, padding, background color) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
 }
```

* le sélecteur `.panel-wrapper` définit le style de tous les éléments avec la classe panel-wrapper, créant ainsi un aspect cohérent pour tous les panneaux.

1. Ciblage du titre du panneau :

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

* le sélecteur `.panel-wrapper legend` définit le style de l’élément de légende dans le panneau, ce qui permet de distinguer visuellement le titre.


1. Ciblage de champs individuels dans le panneau :

```CSS
/* Target all form field wrappers within a panel */
main .form form .panel-wrapper .{Type}-wrapper {
  /* Add your styles here (e.g., margin) */
  margin-bottom: 10px;
}
```

* le sélecteur `.panel-wrapper .{Type}-wrapper` cible tous les wrappers avec la classe `.{Type}-wrapper` dans le panneau, ce qui vous permet de définir le style de l’espacement entre les champs de formulaire.

1. Ciblage de champs spécifiques (facultatif) :

```CSS
  /* Target the username field wrapper */
  main .form form .panel-wrapper .text-wrapper.field-username {
    /* Add your styles here (specific to username field) */
  }

  /* Target the password field wrapper */
  main .form form .panel-wrapper .password-wrapper.field-password {
    /* Add your styles here (specific to password field) */
  }
```

* ces sélecteurs facultatifs vous permettent de cibler des wrappers de champ spécifiques dans le panneau pour une définition de style unique, comme la mise en surbrillance du champ du nom d’utilisateur ou d’utilisatrice.

+++

### Panneau répétable

+++ Structure HTML d’un panneau répétable

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

* data-repeatable=&quot;true&quot; : cet attribut indique que le panneau peut être répété de manière dynamique à l’aide de JavaScript ou d’un framework.

* Identifiants et noms uniques : chaque élément du panneau comprend un identifiant unique (par exemple, name-1, email-1) et un attribut name basé sur l’index du panneau (par exemple, name=&quot;contacts[0].name&quot;). Cela permet une collecte de données correcte lorsque plusieurs panneaux sont envoyés.

+++

+++ Sélecteurs CSS pour un panneau répétable

* Ciblage de tous les panneaux répétables :

```CSS
  /* Target all panels with the repeatable attribute */
 main .form form .panel-wrapper[data-repeatable="true"] {
    /* Add your styles here (e.g., border, margin) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
  }
```

le sélecteur définit le style de tous les panneaux qui peuvent être répétés, assurant ainsi un aspect cohérent.


* Ciblage de champs individuels dans un panneau :

```CSS
/* Target all form field wrappers within a repeatable panel */
main .form form .panel-wrapper[data-repeatable="true"] .{Type}-wrapper {
  /* Add your styles here (e.g., margin) */
  margin-bottom: 10px;
}
```
ce sélecteur définit le style de tous les wrappers de champ dans un panneau répétable, en assurant un espacement cohérent entre les champs.

* Ciblage de champs spécifiques (dans un panneau) :

```CSS
/* Target the name field wrapper within the first panel */
main .form form .panel-wrapper[data-repeatable="true"][data-index="0"] .text-wrapper.field-name {
  /* Add your styles here (specific to first name field) */
}

/* Target all
```

+++

### Pièce jointe

+++ Structure HTML pour une pièce jointe

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

* L’attribut class utilise le nom fourni pour le fichier joint (claim_form).
* Les attributs id et name de l’élément d’entrée correspondent au nom du fichier joint (claim_form).
* La section files-list est initialement vide. Elle est renseignée de manière dynamique avec JavaScript lorsque des fichiers sont chargés.

+++

+++ Sélecteurs CSS pour le composant de fichier joint

* Ciblage de l’ensemble du composant de fichier joint :

```CSS
/* Target the entire file attachment component */
main .form form .file-wrapper {
  /* Add your styles here (e.g., border, padding) */
  border: 1px solid #ccc;
  padding: 15px;
  border-radius: 4px;
  margin-bottom: 20px;
}
```

ce sélecteur définit le style de l’ensemble du composant de fichier joint, y compris la légende, la zone de déplacement, le champ d’entrée et la liste.

* Ciblage d’éléments spécifiques :

```CSS
/* Target the drag and drop area */
main .form form .file-wrapper .file-drag-area {
  /* Add your styles here (e.g., background color, border) */
  background-color: #f0f0f0;
  border: 1px dashed #ddd;
  padding: 10px;
  text-align: center;
}

/* Target the file input element */
main .form form .file-wrapper input[type="file"] {
  /* Add your styles here (e.g., hide the default input) */
  display: none;
}

/* Target individual file descriptions within the list (populated dynamically) */
main .form form .file-wrapper .files-list .file-description {
  /* Add your styles here (e.g., margin, display) */
  display: flex;
  justify-content: space-between;
  margin-bottom: 5px;
}

/* Target the file name within the description */
main .form form .file-wrapper .files-list .file-description .file-description-name {
  /* Add your styles here (e.g., font-weight) */
  font-weight: bold;
}
```

ces sélecteurs vous permettent de définir le style individuellement de divers éléments du composant de fichier joint. Vous pouvez ajuster les styles en fonction de vos préférences de conception.

+++


## Définir le style des composants

Vous pouvez définir le style des champs de formulaire en fonction de leur type spécifique (`{Type}-wrapper`) ou des noms individuels (`field-{Name}`). Cela permet un contrôle et une personnalisation plus précis de l’apparence de votre formulaire.

### Définition de style basée sur le type de champ

Vous pouvez utiliser des sélecteurs CSS pour cibler des types de champ spécifiques et appliquer les styles de manière cohérente.

+++ Structure HTML

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

* Chaque champ est encapsulé dans un élément `div` avec plusieurs classes :
   * `{Type}-wrapper` : identifie le type de champ. Par exemple : `form-text-wrapper`, `form-number-wrapper`, `form-email-wrapper`.
   * `field-{Name}` : identifie le champ par son nom. Par exemple : `form-name`, `form-age`, `form-email`.
   * `field-wrapper` : classe générique pour tous les wrappers de champ.
* L’attribut `data-required` indique si le champ est obligatoire ou facultatif.
* Chaque champ comporte un libellé, un élément d’entrée et d’éventuels éléments supplémentaires correspondants, tels que des espaces réservés et des descriptions.


+++


+++ Exemple de sélecteurs CSS

```CSS
/* Target all text input fields */
main .form form .text-wrapper input {
  /* Add your styles here */
}

/* Target all number input fields */
main .form form .number-wrapper input {
  /* Add your styles here */
  letter-spacing: 2px; /* Example for adding letter spacing to all number fields */
}
```

+++

### Définition de style basée sur le nom du champ

Vous pouvez également cibler des champs individuels par nom pour appliquer des styles uniques.

+++ Structure HTML

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

+++

+++ Exemple de sélecteur CSS

```CSS
main .form form .field-otp input {
   letter-spacing: 2px
}
```

Ce CSS cible tous les éléments d’entrée situés dans un élément qui possède la classe `field-otp`. La structure HTML de votre formulaire suit les conventions du bloc de formulaires adaptatifs, ce qui implique qu’un conteneur marqué avec la classe &quot;field-otp&quot; contient le champ nommé &quot;otp&quot;.

+++




## Voir également

{{universal-editor-see-also}}
