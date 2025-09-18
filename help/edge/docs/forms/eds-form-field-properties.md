---
title: Maîtriser les propriétés de champ de bloc de Forms adaptatif
description: Créez des formulaires puissants plus rapidement à l’aide des feuilles de calcul et des propriétés de champ de bloc Forms adaptatif ! Ce guide répertorie toutes les propriétés prises en charge par le bloc Forms EDS.
feature: Edge Delivery Services
source-git-commit: ccc6439f68d8199154d4cd664b9cdb6428460a64
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 4%

---


# Propriétés de champ de bloc de Forms adaptatif

Ce document résume la manière dont le schéma JSON est mappé à HTML rendu dans `blocks/form/form.js`, en se concentrant sur la manière dont les champs sont identifiés et rendus, les modèles courants et les différences spécifiques aux champs.

## Comment Les Champs (`fieldType`) Sont-Ils Identifiés ?

Chaque champ du schéma JSON possède une propriété `fieldType` qui détermine son rendu. Le `fieldType` peut être :

- **Un type spécial**\
  Exemples : `drop-down`, `radio-group`, `checkbox-group`, `panel`, `plain-text`, `image`, `heading`, etc.
- **Type d’entrée HTML valide**\
  Exemples : `text`, `number`, `email`, `date`, `password`, `tel`, `range`, `file`, etc.
- **Type avec un suffixe `-input`**\
  Exemples : `text-input`, `number-input`, etc. (normalisé sur le type de base tel que `text`, `number`).

Si le `fieldType` correspond à un type spécial, un **moteur de rendu personnalisé** est utilisé. Dans le cas contraire, il est traité comme un **type d’entrée par défaut**.

Consultez les sections ci-dessous pour connaître la [structure et propriétés HTML complètes](#common-html-structure) pour chaque type de champ.

## Propriétés courantes utilisées par les champs

Vous trouverez ci-dessous les propriétés utilisées par la plupart des champs :

- `id` : spécifie l’ID de l’élément et prend en charge l’accessibilité.
- `name` : définit l’attribut `name` pour les éléments d’entrée, de sélection ou d’ensemble de champs.
- `label.value`, `label.richText`, `label.visible` : indique le texte du libellé/de la légende, le contenu HTML et la visibilité.
- `value` : représente la valeur actuelle du champ.
- `required` : ajoute l’attribut `required` ou les données de validation.
- `readOnly`, `enabled` : contrôle si le champ est modifiable ou désactivé.
- `description` : affiche le texte d’aide sous le champ.
- `tooltip` : définit l’attribut `title` pour les entrées.
- `constraintMessages` : fournit des messages d’erreur personnalisés en tant qu’attributs de données.

## Structure commune d’HTML

La plupart des champs sont rendus dans un wrapper qui comprend un libellé et un texte d’aide facultatif. Le fragment de code suivant illustre la structure :

```html
<div class="<fieldType>-wrapper field-wrapper field-<name>" data-id="<id>">
<label for="<id>" class="field-label">Label</label>
<!-- Field-specific input/element here -->
<div class="field-description" id="<id>-description">Description or error
message</div>
</div>
```

Pour les groupes (case d’option/case à cocher) et les panneaux, un `<fieldset>` avec un `<legend>` est utilisé au lieu d’un `<div>/<label>`. Texte d’aide <div> n’est présent que si la description est définie.

## Affichage du message d’erreur

Les messages d’erreur s’affichent dans le même élément de `.field-description` que celui utilisé pour le texte d’aide, qui est mis à jour dynamiquement.

**Lorsqu’un champ n’est pas valide** :

- Le wrapper (par exemple, `.field-wrapper`) se voit attribuer la classe `.field-invalid`.
- Le contenu `.field-description` est remplacé par le message d’erreur correspondant.

**Lorsque le champ devient valide** :

- La classe `.field-invalid` est supprimée.
- Le `.field-description` est restauré au texte d’aide d’origine (le cas échéant) ou supprimé s’il n’en existe aucun.

Les messages d’erreur personnalisés peuvent être définis à l’aide de la propriété `constraintMessages` dans le fichier JSON.\
Ils sont ajoutés en tant qu’attributs `data-<constraint>ErrorMessage` sur le wrapper (par exemple, `data-requiredErrorMessage`).

## Types d’entrée par défaut (entrée HTML ou `*-input`)

Si `fieldType` n’est pas un type spécial, il est traité comme un type d’entrée HTML standard ou comme `<type>-input`, par exemple `text`, `number`, `email`, `date`, `text-input`, `number-input`.

- Le suffixe `-input` est supprimé et le type de base est utilisé comme attribut de `type` de l’entrée.
- Ces types sont gérés par défaut dans `renderField()`.
Les types d’entrée par défaut courants sont `text`, `number`, `email`, `date`, `password`, `tel`, `range`, `file`, etc.  Ils acceptent également les `text-input`, `number-input`, etc., qui sont normalisés au type de base.

## Contraintes pour les types d’entrée par défaut

Les contraintes sont ajoutées en tant qu’attributs sur l’élément d’entrée en fonction des propriétés JSON.

| Propriété JSON | Attribut HTML | Application |
|--------------|---------------|------------|
| maxLength | maxlength | texte, e-mail, mot de passe, tél |
| minLength | minlength | texte, e-mail, mot de passe, tél |
| pattern | pattern | texte, e-mail, mot de passe, tél |
| maximum | max. | nombre, période, date |
| minimum | min. | nombre, période, date |
| étape | étape | nombre, période, date |
| accept | accept | Fichier |
| multiple | multiple | Fichier |
| maxOccur | data-max | panel |
| minOccur | data-min | panel |

>[!NOTE]
>
> `multiple` est une propriété booléenne. Si la valeur est true, l’attribut `multiple` est ajouté.

Ces attributs sont définis automatiquement par le moteur de rendu de formulaire en fonction de la définition JSON du champ.

## Exemple : structure HTML avec contraintes

L’exemple suivant illustre la manière dont un champ numérique est rendu avec des contraintes de validation et des attributs de gestion des erreurs.

```html
<div class="number-wrapper field-wrapper field-age" data-id="age"
data-required="true"
data-minimumErrorMessage="Too small" data-maximumErrorMessage="Too large">
<label for="age" class="field-label">Age</label>
<input type="number"
id="age" name="age"
value="30" required min="18"
max="99" step="1"
placeholder="Enter your age" />
<div class="field-description" id="age-description"> Description or error message
</div>
</div>
```

Chaque partie de la structure d’HTML joue un rôle dans la liaison des données, la validation et l’affichage des messages d’aide ou d’erreur.

## Propriétés spécifiques au champ et leurs structures HTML

### Liste déroulante

**Propriétés supplémentaires :**

- `enum`/`enumNames` : définissez les valeurs des options et leurs libellés d’affichage pour la liste déroulante.
- `type` : permet la sélection multiple si elle est définie sur `array`.
- `placeholder` : ajoute une option d’espace réservé désactivée pour guider les utilisateurs avant la sélection.

Exemple :

```html
<div class="drop-down-wrapper field-wrapper field-<name>" data-id="<id>"
data-required="true"
data-requiredErrorMessage="This field is required">
<label for="<id>" class="field-label">Label</label>
<select id="<id>" name="<name>" required title="Tooltip" multiple>
<option disabled selected value="">Placeholder</option>
<option value="opt1">Option 1</option>
<option value="opt2">Option 2</option>
</select>
<div class="field-description" id="<id>-description"> Description or error message
</div>
</div>
```

### Texte brut

**Propriétés supplémentaires** :

- `richText` : si la valeur est true, effectue le rendu d’HTML dans le paragraphe.

Exemple :

```html
<div class="plain-text-wrapper field-wrapper field-<name>" data-id="<id>">
<label for="<id>" class="field-label">Label</label>
<p>Text or <a href="..." target="_blank">link</a></p>
</div>
```

### Case à cocher

**Propriétés supplémentaires** :

- `enum` : définit les valeurs des états cochés et non cochés de la case à cocher.
- `properties.variant / properties.alignment` : spécifie le style visuel et l’alignement des cases à cocher de style différent.

Exemple :

```html
<div class="checkbox-wrapper field-wrapper field-<name>" data-id="<id>"
data-required="true"
data-requiredErrorMessage="Please check this box">
<label for="<id>" class="field-label">Label</label>
<input type="checkbox"
id="<id>"
name="<name>" value="on"
required
data-unchecked-value="off" />
<div class="field-description" id="<id>-description"> Description or error message
</div>
</div>
```

### Bouton

**Propriétés supplémentaires** :

- `buttonType` : indique le comportement du bouton en définissant son type (bouton, envoyer ou réinitialiser).

Exemple :

```html
<div class="button-wrapper field-wrapper field-<name>" data-id="<id>">
<button id="<id>" name="<name>" type="submit" class="button"> Label
</button>
</div>
```

### Entrée Multiligne

**Propriétés supplémentaires** :

- `minLength` : spécifie le nombre minimum de caractères autorisés dans une entrée de texte ou de zone de texte.
- `maxLength` : indique le nombre maximal de caractères autorisés dans une entrée de texte ou de zone de texte.
- `pattern` : définit une expression régulière avec laquelle la valeur d’entrée doit correspondre pour être considérée comme valide.
- `placeholder` : affiche le texte d’espace réservé dans la zone de saisie ou de texte jusqu’à la saisie d’une valeur.

Exemple :

```html
<div class="multiline-wrapper field-wrapper field-<name>" data-id="<id>"
data-minLengthErrorMessage="Too short" data-maxLengthErrorMessage="Too long">
<label for="<id>" class="field-label">Label</label>
<textarea id="<id>"
name="<name>" required
minlength="2"
maxlength="100"
pattern="[A-Za-z]+"
placeholder="Type here..."></textarea>
<div class="field-description" id="<id>-description"> Description or error message
</div>
</div>
```

### Panneau

**Propriétés supplémentaires** :

- `repeatable` : indique si le panneau peut être répété dynamiquement.
- `minOccur` : permet de définir le nombre minimal d’instances de panneau requises.   maxOcr : définit le nombre maximal d’instances de panneau autorisées.
- `properties.variant` : définit le style visuel ou la variante du panneau.
- `properties.colspan` : indique le nombre de colonnes sur lesquelles s’étend le panneau dans une disposition en grille.
- `index` : indique la position du panneau dans son conteneur parent.
- `fieldset` : regroupe les champs associés sous un élément `<fieldset>` avec une légende ou un libellé.

Exemple :

```html
<fieldset class="panel-wrapper field-wrapper field-<name>" data-id="<id>"
name="<name>"
data-repeatable="true" data-index="0">
<legend class="field-label">Label</legend>
<!-- Nested fields here -->
<button type="button" class="add">Add</button>
<button type="button" class="remove">Remove</button>
<div class="field-description" id="<id>-description"> Description or error message
</div>
</fieldset>
```

### Case d’option

**Propriétés supplémentaires** :

- `enum` : définit l’ensemble des valeurs autorisées pour le champ radio, utilisé comme attribut de valeur pour chaque option de bouton radio.

Exemple :

```html
<div class="radio-wrapper field-wrapper field-<name>" data-id="<id>"
data-required="true">
<label for="<id>" class="field-label">Label</label>
<input type="radio" id="<id>" name="<name>" value="opt1" required />
<div class="field-description" id="<id>-description"> Description or error message
</div>
</div>
```

### Groupe de cases d’option

**Propriétés supplémentaires** :

- `enum` : définit la liste des valeurs d’option pour le groupe de cases d’option, utilisée comme valeur de chaque bouton radio.
- `enumNames` : fournit des libellés d’affichage pour les boutons radio, dans l’ordre de l’énumération.

Exemple :

```html
<fieldset class="radio-group-wrapper field-wrapper field-<name>" data-id="<id>"
data-required="true">
<legend class="field-label">Label</legend>
<div>
<input type="radio" id="<id>-0" name="<name>" value="opt1" required />
<label for="<id>-0">Option 1</label>
</div>
<div>
<input type="radio" id="<id>-1" name="<name>" value="opt2" />
<label for="<id>-1">Option 2</label>
</div>
<div class="field-description" id="<id>-description"> Description or error message
</div>
</fieldset>
```

### **Groupe de cases à cocher**

**Propriétés supplémentaires** :

- `enum` : définit la liste des valeurs d’option pour le groupe de cases à cocher, utilisée comme valeur de chaque case à cocher.
- `enumNames` : fournit des libellés d’affichage pour les cases à cocher, correspondant à l’ordre d’énumération.
- `minItems` : permet de définir le nombre minimal de cases à cocher qui doivent être sélectionnées pour la validité.
- `maxItems` : permet de définir le nombre maximal de cases à cocher pouvant être sélectionnées avant de déclencher une erreur.

Exemple :

```html
<fieldset class="checkbox-group-wrapper field-wrapper field-<name>" data-id="<id>"
data-required="true" data-minItems="1"
data-maxItems="3">
<legend class="field-label">Label</legend>
<div>
<input type="checkbox" id="<id>-0" name="<name>" value="opt1" required />
<label for="<id>-0">Option 1</label>
</div>
<div>
<input type="checkbox" id="<id>-1" name="<name>" value="opt2" />
<label for="<id>-1">Option 2</label>
</div>
<div class="field-description" id="<id>-description"> Description or error message
</div>
</fieldset>
```

### Image

**Propriétés supplémentaires** :

- `value / properties['fd:repoPath']` : définit le chemin d’accès source de l’image ou le chemin du référentiel pour le rendu de l’image.
- `altText` : fournit un texte secondaire pour l’image (attribut alt) afin d’en améliorer l’accessibilité.

Exemple :

```html
<div class="image-wrapper field-wrapper field-<name>" data-id="<id>">
<picture>
<img src="..." alt="..." />
<!-- Optimized sources -->
</picture>
</div>
```

### En-tête

**Propriétés supplémentaires** :

- `value` : indique le contenu texte à afficher dans l’élément d’en-tête (par exemple, `<h2>`).

Exemple :

```html
<div class="heading-wrapper field-wrapper field-<name>" data-id="<id>">
<h2 id="<id>">Heading Text</h2>
</div>
```

Pour plus d’informations, consultez la mise en œuvre dans `blocks/form/form.js` et `blocks/form/util.js`.


<!--Each form field is represented as a dedicated row in the spreadsheet, analogous to fields in a database table. The column headers act as labels for the various properties supported by the form field block.

Think of your form as a table in a spreadsheet, where each line represents a different question or piece of information you want to collect. The table headings tell you what kind of answers you can expect for each section.

The below table lists all the properties that are supported by the Adaptive Forms Block.

**Master Your Forms with These Adaptive Forms Block Field Properties:**

This table details all the properties you can use to customize your Adaptive Forms Block fields:

| Property | Description | Example |
|---|---|---|
| **Type** | [HTML input type](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types) (text, email, number, etc.), [textarea](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea), [select](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select), [fieldset](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset) | `text`, `email`, `radio`, `select` |
| **Name** | This defines the unique identifier for submitted data (e.g., 'email' for an email address field).  Choose a clear and unique name for each field, as the name serves as internal field identifier used for data mapping during submission. | `user_name`, `email_address` |
| **Label** | User-friendly field label | `"Full Name"`, `"Choose your country"` |
| **Value** | Default value displayed | `"John Doe"`, `"United States"` |
| **Placeholder** | Hint text within the field | `"Enter your email address"` |
| **Description** | Help text for users | `"Please enter a valid email address"` |
| **Visible** | Show/hide the field initially | `true`, `false` |
| **Mandatory** | Require a value from the user | `true`, `false` |
| **Min/Max** | Set minimum/maximum values (number, date, text length) | `18` (age), `2025-12-31` (date) |
| **Accept** | Allowed file types for file upload | `"image/jpeg,image/png"` |
| **Multiple** | Allow multiple file selections | `true`, `false` |
| **Options** | Comma-separated list for dropdown menus | `"Option 1, Option 2, Option 3"` |
| **Checked** | Default-selected radio button/checkbox | `true`, `false` |
| **Fieldset** | Group fields together | Fieldset name (e.g., `"Personal Information"`) |-->

