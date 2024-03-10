---
title: Composants et propriétés de formulaire
description: Ce document présente les composants de formulaire et leurs propriétés disponibles dans le service de diffusion Edge AEM Forms.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 7d087d41-9313-482a-a905-8955b0999781
source-git-commit: 2aa70e78764616f41fe64e324c017873cfba1d5b
workflow-type: tm+mt
source-wordcount: '964'
ht-degree: 2%

---

# Composants et propriétés de formulaire : service de diffusion AEM Forms Edge

AEM Forms Edge Delivery Services vous permet de créer des formulaires interactifs et conviviaux à l’aide de divers composants. Ces composants répondent à différents types de collecte de données et peuvent être facilement personnalisés en fonction de vos besoins.


![Un exemple de feuille de calcul avec quelques composants et propriétés](/help/edge/assets/sample-form-in-spreadsheet.png)

Le bloc Forms adaptatif génère une [structure de HTML uniforme](/help/edge/docs/forms/style-theme-forms.md) pour tous les types de champ et conteneurs (panneaux), en assurant la cohérence. Cette structure cohérente facilite la [style d’un formulaire](/help/edge/docs/forms/style-theme-forms.md).

## Composants disponibles

Voici un aperçu des composants disponibles :

### Champs d’entrée

- Tout le HTML valide5 [types d’entrée](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types) et [textarea](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea). Par exemple, un bouton, une case à cocher, une couleur, une date, une heure-locale, un email, un fichier, masqué, une image, un mois, un numéro, un mot de passe, une radio, une plage, une réinitialisation, un envoi, un tel, un texte, une heure, une URL et une semaine.

### Contrôles de sélection

- [Groupes de cases à cocher](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox): pour sélectionner plusieurs options.
- [Groupes de cases d&#39;option](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/radio): pour sélectionner une seule option dans un groupe.
- [Menus déroulants](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select): pour afficher un menu d’options. Par exemple, une liste déroulante.

### Conteneurs

- Panneaux/Conteneurs : pour regrouper les éléments de formulaire associés pour une meilleure organisation. Il s’agit d’une combinaison de [fieldset](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset) et [légende](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/legend).






## Propriétés des composants

Chaque composant de formulaire est fourni avec différentes propriétés qui vous permettent de contrôler son comportement et son aspect. Ici, les propriétés prises en charge par les composants Bloc de Forms adaptatif :


| Propriété | Composants applicables | Détails |
|--------------|------------------------------|----------------------------------------------------------------------|
| Type | Tous | Indique le type du composant. Cette propriété détermine le comportement et l’aspect du champ de saisie. Par exemple, pour les entrées de texte, le type peut être &quot;texte&quot;, &quot;email&quot; pour les entrées d’email, &quot;mot de passe&quot; pour les entrées de mot de passe. Prise en charge des blocs Forms adaptatifs  <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types">tous les types d’entrée HTML5 valides</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea">textarea</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">select</a>, et <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset</a> comme type. |
| Type | Tous | Indique le type du composant. Cette propriété détermine le comportement et l’aspect du champ de saisie. Par exemple, pour les entrées de texte, le type peut être &quot;texte&quot;, &quot;email&quot; pour les entrées d’email, &quot;mot de passe&quot; pour les entrées de mot de passe. Prise en charge des blocs Forms adaptatifs  <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types">tous les types d’entrée HTML5 valides</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea">textarea</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">select</a>, et <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset</a> comme type. |
| Nom | Tous | Identifie le composant pour l’envoi du formulaire. L’attribut name est utilisé lors de l’envoi des données de formulaire au serveur, associant la saisie de l’utilisateur à un champ spécifique. |
| Libellé | Tous | Fournit des informations contextuelles aux utilisateurs. Le libellé est le texte affiché en regard du composant, qui fournit aux utilisateurs des conseils sur les informations à saisir. |
| Valeur | Texte, Mot de passe, Email, Numéro, Plage, Date et ses variantes (datetime-local, mois, semaine, heure), Case à cocher, Radio, Masqué, Envoyer, Bouton | Indique la valeur initiale du composant. Pour les entrées de texte, la zone de texte et les éléments de sélection, il s’agit du texte ou de l’option par défaut qui s’affiche. Pour les composants radio et case à cocher, il s’agit de la valeur/des données envoyées lorsqu’elles sont sélectionnées. L’attribut value est facultatif, mais doit être considéré comme obligatoire pour les entrées de case à cocher et de radio. |
| Espace réservé | Texte, Tel, Email, Mot de passe, Date (et ses variantes telles que mois, semaine, heure, datetime-local), Nombre, Plage | Offre des conseils pour une entrée attendue. L’attribut d’espace réservé fournit un bref indice qui décrit la valeur attendue du champ de saisie. Il disparaît lorsque l’utilisateur commence à saisir du texte. |
| Description | Tous | Fournit des informations supplémentaires sur le composant et sert de texte d’aide. Le champ de description permet d’obtenir des explications supplémentaires sur l’objectif ou les instructions de remplissage du composant. Cela aide les utilisateurs à comprendre le contexte du champ de saisie. |
| Visible | Tous | Contrôle la visibilité initiale. L’attribut visible est une propriété booléenne qui détermine si le composant est initialement visible ou masqué au chargement du formulaire. S’il est défini sur true, le champ s’affiche ; dans le cas contraire, il est masqué. |
| Obligatoire | Texte, Tel, Email, Mot de passe, Date et ses variantes (datetime-local, mois, semaine, heure), Nombre, Case à cocher, Radio, Fichier, Sélectionner (liste déroulante), Zone de texte | Indique si le champ doit être renseigné avant envoi. L’attribut mandatory est une propriété booléenne utilisée pour spécifier si l’utilisateur doit fournir une entrée pour le champ avant d’envoyer le formulaire. |
| Min. | Date (et ses variantes telles que le mois, la semaine, l’heure, la date, l’heure-locale), nombre, plage | Indique la valeur minimale autorisée. L’attribut min définit la valeur minimale que l’utilisateur peut entrer dans le champ. Par exemple, pour les entrées de nombre, il définit le nombre acceptable le plus petit. |
| Max | Date (et ses variantes telles que le mois, la semaine, l’heure, la date, l’heure-locale), nombre, plage | Indique la valeur maximale autorisée. L’attribut max définit la valeur maximale que l’utilisateur peut entrer dans le champ. Par exemple, pour les entrées de date, il définit la date acceptable la plus élevée. |
| Accepter | Fichier | Définit les types de fichiers autorisés. L’attribut accept est une liste séparée par des virgules de caractères de type de fichier uniques qui limite les types de fichiers que les utilisateurs peuvent sélectionner dans un champ de saisie de fichier. |
| Multiple | Fichier | Permet plusieurs sélections. L’attribut multiple est une propriété booléenne utilisée avec les champs d’entrée de fichier. Lorsqu’elle est définie sur true, elle permet aux utilisateurs de sélectionner plusieurs fichiers. |
| Options | Liste déroulante | Spécifie les options des menus déroulants. La propriété options est une liste de choix séparés par des virgules pour les menus déroulants, qui définit les options sélectionnables affichées pour l’utilisateur. |
| Cochée | Case à cocher, Radio | Détermine si le champ est sélectionné par défaut. L’attribut coché est une propriété booléenne utilisée avec les entrées de case à cocher et de radio. Lorsque la valeur est définie sur true, elle indique que le champ est sélectionné par défaut au chargement du formulaire. |
| FileSet | Tous | Regroupe les champs pour créer des sections visuellement distinctes dans un formulaire. L’élément fieldset regroupe les champs associés dans un formulaire, les séparant visuellement afin d’améliorer l’organisation et l’expérience utilisateur. </br> Pour organiser un ensemble de champs dans un jeu de champs, utilisez simplement la variable `fieldset` et indiquez son attribut name . Dans l’exemple ci-dessous, nous montrons comment les boutons radio sont encapsulés dans un seul jeu de champs pour une meilleure organisation. ![Exemple de champ](/help/edge/assets/fieldset-example.png) |



<!--

## Supported HTML 5 input types in Adaptive Forms Block

The Adaptive Forms Block supports a range of HTML 5 input types, and it also seamlessly renders forms created with AEM core components.
Here is the table which outlines how core components correspond to their HTML-5 input types in Edge Delivery:
<table>
 <tbody>
  <tr>
   <td><b>Core Components</b> </td>
   <td><b>HTML 5 input type</b> </td>
   <td><b>Details</b></td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/form-container.html">Form Container</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#form">form </td>
   <td> Create a form to capture user inputs.
   </td>
  </tr>
  <tr>
   <td><a herf="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/text-input.html">Text Input</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/text">text</a></td>
   <td> Defines a single-line text input field. </td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/number-input.html">Number Input</a></td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/number">number</a></td>
   <td>Lets user  enter a number input. You can also add built-in validation to reject non-numerical inputs. Lets user  enter a number input. You can also add built-in validation to reject non-numerical inputs. Initially, the input field is displayed as a number input. If a user applies a display pattern, it changes to text to allow the author to apply number formatting, since HTML 5 lacks support for display patterns. However, when the user clicks it, it returns to typing numbers.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/date-picker.html">Date Picker</a></td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/date">date </a></td>
   <td> Create an input field for entering a date. You have the option to input the date either through a text box, which validates the entry, or through a dedicated date picker interface. Initially, the native date input field is displayed. If a user applies a display pattern, it changes to text to allow the user to apply formatting, since HTML 5 lacks support for display patterns. However, when the user clicks it, it returns to typing a date.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/file-attachment.html">File Attachment</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/file">file</a></td>
   <td> Allows user to choose one or more files from the device storage. It supports enhanced file input validations, such as accepted file types, file size restrictions, and minimum/maximum file selection limits. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/drop-down.html"> Dropdown List</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">select</a></td>
   <td> Allows users to select one or more options from a list of predefined options. The options can be of type String, Number, or Boolean.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox-group.html">Checkbox Group</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox">multiple checkbox</a></td>
   <td> Allow users to select one or more options from a list. Multiple checkboxes are generated with identical names, each corresponding to an item in the enum. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/radio-button.html">Radio Button Group</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/radio">multiple radio</a></td>
   <td> Allows a user to select one option from a group of related options. Multiple radio buttons are generated with identical names, each corresponding to an item in the enum.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/button.html">Button</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/button">button</a></td>
   <td>A UI element that allows users to trigger an action when clicked. </td>
  </tr>
  <tr>
   <td><a href =""https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html">Panel</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset with legend</a></td>
   <td> Group sections within a form, where a nested *legend* element adds a caption for the form.</td>
  </tr>
   <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html">Wizard</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset</a></td>
   <td>Groups related sections within a form. It also controls the arrangement, supporting display options for positioning them at the top or at the left side. </td>
  </tr>
    <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/text.html">Text</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/p">p</a></td>
   <td>A p tag marks a paragraph. In visual content, paragraphs are chunks of text separated by blank lines or an indented first line</td>
  </tr>
     <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/submit-button.html">Submit button</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/submit">submit</a></td>
   <td> A UI element that enables users to submit a form to the server upon clicking. If a user adds a submit rule to a button, it functions as the submit button. </td>
  </tr>
     <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/reset-button.html">Reset button</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/reset">reset</a></td>
   <td>A UI element that resets a form upon clicking. If a user adds a reset rule to a button, it functions as the reset button. </td>
  </tr>
    <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/email-input.html">Email Input</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/email">email</a></td>
   <td> Allows the user to enter and edit an email address. If the user adds the multiple attributes, a list of email addresses can be added or edited.</td>
  </tr>
   <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/telephone-input.html">Telephone Input</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/tel">tel</a></td>
   <td>Allows user to enter and edit a telephone number.</td>
  </tr>
   <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/header.html">Header</td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/header"> header</a></td>
   <td>It includes introductory content, typically a group of introductory or navigational aids. It is supported outside Form container. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/footer.html">Footer</td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/footer">footer</a></td>
   <td> Contains information such as copyright data or links to related documents. It is supported outside Form container.</td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html">Accordion<a></td>
   <td><i>Not yet supported in Adaptive Forms Block</i></td>
   <td> Allows user to create expandable and collapsible sections in a form. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html">Horizontal tabs</a></td>
   <td><i>Not yet supported in Adaptive Forms Block</i></td>
   <td>Organizes multiple sections of a form into separate tabs which are displayed horizontally.</td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/image.html">Image</a></td>
   <td><i>Not yet supported in Adaptive Forms Block</i></td>
   <td> Allows user to include images in a form.</td>
  </tr><tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/title.html">Title</a></td>
   <td><i>Not yet supported in Adaptive Forms Block</i></td>
   <td> Refers to the text that appears at the top of the form. </td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/submit-button.html">Switch</td>
   <td><i>Not yet supported in Adaptive Forms Block</i></td>
   <td> A two-state toggle that allows user to select between two states such as enabling or disabling a feature, setting, or functionality.</td>
  </tr>
 </tbody>
</table> -->

## En savoir plus

- [Créer et prévisualiser un formulaire](/help/edge/docs/forms/create-forms.md)
- [Activer le formulaire pour envoyer des données](/help/edge/docs/forms/submit-forms.md)
- [Publier un formulaire sur la page de sites](/help/edge/docs/forms/publish-forms.md)
- [Ajouter des validations à des champs de formulaire](/help/edge/docs/forms/validate-forms.md)
- [Modifier les thèmes et le style du formulaire](/help/edge/docs/forms/style-theme-forms.md)
