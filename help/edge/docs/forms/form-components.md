---
title: Composants de bloc de formulaire adaptatif et leurs propriétés
description: Ce document présente les composants de formulaire et leurs propriétés disponibles dans le service de diffusion Edge AEM Forms.
feature: Edge Delivery Services
exl-id: 7d087d41-9313-482a-a905-8955b0999781
source-git-commit: 703a48903c44678f6fe311de740b7c767c886ba5
workflow-type: tm+mt
source-wordcount: '1006'
ht-degree: 3%

---

# Composants de bloc de formulaire adaptatif et leurs propriétés

AEM Forms Edge Delivery Services vous permet de créer des formulaires interactifs et conviviaux à l’aide de divers composants. Ces composants répondent à différents types de collecte de données et peuvent être facilement personnalisés en fonction de vos besoins.


![Un exemple de feuille de calcul avec quelques composants et propriétés](/help/edge/assets/sample-form-in-spreadsheet.png)

Le bloc Forms adaptatif génère une [structure de HTML uniforme](/help/edge/docs/forms/style-theme-forms.md) pour tous les types de champ et conteneurs (panneaux), en assurant la cohérence. Cette structure cohérente facilite la [style d’un formulaire](/help/edge/docs/forms/style-theme-forms.md).

## Composants disponibles

Voici un aperçu des composants disponibles :

### Champs d’entrée

* Tout le HTML valide5 [types d’entrée](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types) et [textarea](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea). Par exemple, un bouton, une case à cocher, une couleur, une date, une heure-locale, un email, un fichier, masqué, une image, un mois, un numéro, un mot de passe, une radio, une plage, une réinitialisation, un envoi, un tel, un texte, une heure, une URL et une semaine.

### Contrôles de sélection

* [Groupes de cases à cocher](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox): pour sélectionner plusieurs options.
* [Groupes de cases d&#39;option](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/radio): pour sélectionner une seule option dans un groupe.
* [Menus déroulants](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select): pour afficher un menu d’options. Par exemple, une liste déroulante.

### Conteneurs

* Panneaux/Conteneurs : pour regrouper les éléments de formulaire associés pour une meilleure organisation. Il s’agit d’une combinaison de [fieldset](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset) et [légende](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/legend).


## Propriétés des composants

Chaque composant de formulaire est fourni avec différentes propriétés qui vous permettent de contrôler son comportement et son aspect. Ici, les propriétés prises en charge par les composants Bloc de Forms adaptatif :


| Propriété | Composants applicables | Détails |
|--------------|------------------------------|----------------------------------------------------------------------|
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
| Répétable | Tous | Une propriété booléenne pour `fieldset` indiquant qu’un jeu de champs particulier peut être répété pour spécifié `Min` et `Max` nombre de fois. La variable `Min` doit être définie sur 1 ou supérieur, ne définissez pas la variable `Min` à 0. |
| Expression visible | Tous | Une expression visible fait référence à une formule de feuille de calcul, indiquée par la balise &#39;=&#39;, utilisée pour contrôler la visibilité d’un champ. Dans cette formule, seule la propriété value des autres champs peut être utilisée, ce qui permet de gérer facilement la visibilité des champs dans le système. |
| Expression de valeur | Tous | Une expression de valeur fait référence à une formule de feuille de calcul, indiquée par la balise &#39;=&#39;, utilisée pour contrôler la valeur d’un champ. Dans cette formule, seule la propriété value des autres champs peut être utilisée, ce qui permet une gestion simple de la valeur des champs dans le système. |


## Voir également

{{see-more-forms-eds}}
