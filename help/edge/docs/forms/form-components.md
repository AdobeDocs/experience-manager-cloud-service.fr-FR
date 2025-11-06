---
title: Composants de bloc de formulaire adaptatif et leurs propriétés
description: Ce document présente une vue d’ensemble des composants de formulaire et de leurs propriétés disponibles dans Edge Delivery Services pour AEM Forms.
feature: Edge Delivery Services
exl-id: 7d087d41-9313-482a-a905-8955b0999781
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 100%

---

# Composants de bloc de formulaire adaptatif et leurs propriétés

Edge Delivery Services pour AEM Forms vous permet de créer des formulaires interactifs et conviviaux à l’aide de divers composants. Ces composants répondent à différents types de collecte de données et peuvent être facilement personnalisés en fonction de vos besoins.


![Exemple de feuille de calcul avec quelques composants et propriétés](/help/edge/assets/sample-form-in-spreadsheet.png)

Le bloc de formulaires adaptatifs génère une [structure HTML uniforme](/help/edge/docs/forms/style-theme-forms.md) pour tous les types de champ et conteneurs (panneaux), garantissant ainsi la cohérence. Cette structure cohérente facilite la [définition du style d’un formulaire](/help/edge/docs/forms/style-theme-forms.md).

## Composants disponibles

Voici une vue d’ensemble des composants disponibles :

### Champs d’entrée

- Tous les [types d’entrées](https://developer.mozilla.org/fr-fr/docs/Web/HTML/Element/input#input_types) HTML5 valides et [textarea](https://developer.mozilla.org/fr-fr/docs/Web/HTML/Element/textarea). Par exemple : bouton, case à cocher, couleur, date, heure locale, e-mail, fichier, contenu masqué, image, mois, nombre, mot de passe, bouton radio, plage, réinitialisation, envoi, numéro de téléphone, texte, heure, URL et semaine.

### Contrôles de sélection

- [Groupes de cases à cocher](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox) : pour sélectionner plusieurs options.
- [Groupes de boutons radio](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/radio) : pour sélectionner une seule option dans un groupe.
- [Menus déroulants](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select) : pour afficher un menu d’options. Par exemple, une zone de liste déroulante.

### Conteneurs

- Panneaux/Conteneurs : pour regrouper les éléments de formulaire associés en vue d’une meilleure organisation. Il s’agit d’une combinaison de [fieldset](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset) et de [légende](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/legend).


## Propriétés des composants

Chaque composant de formulaire est accompagné de différentes propriétés qui vous permettent de contrôler son comportement et son apparence. Les propriétés prises en charge par les composants du bloc de formulaires adaptatifs sont présentées ici :


| Propriété | Composants applicables | Détails |
|--------------|------------------------------|----------------------------------------------------------------------|
| Type | Tous | Indique le type du composant. Cette propriété détermine le comportement et l’apparence du champ d’entrée. Par exemple, pour les entrées de texte, le type peut être « texte », « e-mail » pour les entrées d’e-mail, et « mot de passe » pour les entrées de mot de passe. Le bloc de formulaires adaptatifs prend en charge <a href="https://developer.mozilla.org/fr-fr/docs/Web/HTML/Element/input#input_types">tous les types d’entrée HTML5 valides</a>, <a href="https://developer.mozilla.org/fr-fr/docs/Web/HTML/Element/textarea">textarea</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">select</a> et <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset</a> comme type. |
| Nom | Tous | Identifie le composant pour l’envoi du formulaire. L’attribut name est utilisé lors de l’envoi des données de formulaire au serveur, en associant l’entrée de l’utilisateur ou de l’utilisatrice à un champ spécifique. |
| Libellé | Tous | Fournit des informations contextuelles aux utilisateurs et utilisatrices. Le libellé est le texte affiché en regard du composant, qui fournit aux utilisateurs et utilisatrices des conseils sur les informations à saisir. |
| Valeur | Texte, Mot de passe, E-mail, Nombre, Plage, Date et ses variantes (heure locale, mois, semaine, heure), Case à cocher, Bouton radio, Contenu masqué, Envoyer, Bouton | Indique la valeur initiale du composant. Pour les éléments d’entrées de texte, textarea et de sélection, il s’agit du texte ou de l’option par défaut qui s’affiche. Pour les composants de bouton radio et de case à cocher, il s’agit de la valeur/des données envoyées lorsqu’ils sont sélectionnés. L’attribut value est facultatif, mais doit être considéré comme obligatoire pour les entrées de case à cocher et de bouton radio. |
| Espace réservé | Texte, Téléphone, E-mail, Mot de passe, Date (et ses variantes telles que mois, semaine, heure, heure locale), Nombre, Plage | Fournit des conseils sur l’entrée attendue. L’attribut placeholder fournit un bref indice qui décrit la valeur attendue du champ d’entrée. Il disparaît lorsque l’utilisateur ou l’utilisatrice commence à saisir. |
| Description | Tous | Fournit des informations supplémentaires sur le composant et sert de texte d’aide. Le champ de description permet d’obtenir des explications supplémentaires sur l’objectif ou des instructions de remplissage du composant. Cela aide les utilisateurs et utilisatrices à comprendre le contexte du champ d’entrée. |
| Visible | Tous | Contrôle la visibilité initiale. L’attribut visible est une propriété booléenne qui détermine si le composant est visible initialement ou masqué lors du chargement du formulaire. S’il est défini sur true, le champ s’affiche ; dans le cas contraire, il est masqué. |
| Obligatoire | Texte, Téléphone, E-mail, Mot de passe, Date et ses variantes (heure locale, mois, semaine, heure), Nombre, Case à cocher, Bouton radio, Fichier, Sélectionner (liste déroulante), Textarea | Indique si le champ doit être renseigné avant l’envoi. L’attribut mandatory est une propriété booléenne utilisée pour spécifier si l’utilisateur ou l’utilisatrice doit fournir une entrée pour le champ avant d’envoyer le formulaire. |
| Min | Date (et ses variantes telles que mois, semaine, heure, la date, heure locale), Nombre, Plage | Indique la valeur minimale autorisée. L’attribut min définit la valeur minimale que l’utilisateur ou l’utilisatrice peut saisir dans le champ. Par exemple, pour les entrées de nombres, il définit le nombre le plus faible acceptable. |
| Max | Date (et ses variantes telles que mois, semaine, heure, la date, heure locale), Nombre, Plage | Indique la valeur maximale autorisée. L’attribut max définit la valeur maximale que l’utilisateur ou l’utilisatrice peut saisir dans le champ. Par exemple, pour les entrées de dates, il définit la date la plus élevée acceptable. |
| Accepter | Fichier | Définit les types de fichiers autorisés. L’attribut accept est une liste séparée par des virgules de spécificateurs de type de fichier uniques qui limite les types de fichiers que les utilisateurs et les utilisatrices peuvent sélectionner dans un champ d’entrée de fichier. |
| Multiple | Fichier | Autorise plusieurs sélections. L’attribut multiple est une propriété booléenne utilisée avec les champs d’entrée de fichier. Lorsqu’il est défini sur true, il permet aux utilisateurs et utilisatrices de sélectionner plusieurs fichiers. |
| Options | Liste déroulante | Spécifie les options des menus déroulants. La propriété options est une liste séparée par des virgules d’options pour les menus déroulants, qui définit les options sélectionnables présentées à l’utilisateur ou à l’utilisatrice. |
| Cochée | Case à cocher, Bouton radio | Détermine si le champ est sélectionné par défaut. L’attribut checked est une propriété booléenne utilisée avec les entrées de case à cocher et de bouton radio. Lorsqu’il est défini sur true, il indique que le champ est sélectionné par défaut lors du chargement du formulaire. |
| Fieldset | Tous | Regroupe des champs pour créer des sections visuellement distinctes dans un formulaire. L’élément fieldset regroupe les champs associés dans un formulaire, les séparant visuellement afin d’améliorer l’organisation et l’expérience client. </br> Pour organiser un ensemble de champs dans un fieldset, utilisez simplement la propriété `fieldset` et spécifiez son attribut name. Dans l’exemple ci-dessous, nous montrons comment les boutons radio sont encapsulés dans un seul fieldset pour une meilleure organisation. ![Exemple de fieldset](/help/edge/assets/fieldset-example.png) |
| Répétable | Tous | Propriété booléenne pour `fieldset` indiquant qu’un jeu de champs particulier peut être répété selon le nombre de fois `Min` et `Max` spécifié. La propriété `Min` doit être définie sur 1 ou plus. Ne définissez pas la propriété `Min` sur 0. |
| Expression visible | Tous | Une expression visible fait référence à une formule de feuille de calcul, indiquée par la balise « = », utilisée pour contrôler la visibilité d’un champ. Dans cette formule, seule la propriété value d’autres champs peut être utilisée, ce qui permet de gérer facilement la visibilité des champs dans le système. |
| Expression de valeur | Tous | Une expression de valeur fait référence à une formule de feuille de calcul, indiquée par la balise « = », utilisée pour contrôler la valeur d’un champ. Dans cette formule, seule la propriété value d’autres champs peut être utilisée, ce qui permet de gérer facilement la valeur des champs dans le système. |
