---
title: De feuilles de calcul à Forms - Gestion des validations des champs de bloc de formulaire
description: Créez des formulaires puissants plus rapidement à l’aide des feuilles de calcul et des champs de bloc de formulaire. Ce guide vous aide à créer des validations personnalisées pour les champs Bloc Forms d’EDS.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 78d40574e6fea8dde22414e43fd77215b9e7d2a1
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---


# Ajouter des validations à des champs de formulaire

Le bloc de formulaire comporte des fonctions de validation intégrées. Ces validations sont automatiquement appliquées dans les navigateurs modernes en fonction du type de champ choisi et des propriétés supplémentaires fournies.

## Présentation des types de champ et validation

Le bloc de formulaire prend en charge un large éventail de [Types d’entrée HTML-5](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types), y compris le texte, l’adresse électronique, le numéro, la date, etc. Il prend également en charge [textarea](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea), sélectionnez et le jeu de champs, ainsi que des fonctionnalités complètes de validation des entrées inhérentes au HTML-5.

utilise les types de champs de HTML pour définir le type de données qu’un utilisateur peut entrer. Les différents types de champ ont des règles de validation intégrées différentes :

Email : ce type de champ valide automatiquement la saisie de l’utilisateur par rapport à un format d’adresse email commun. Un message d’erreur s’affiche pour les utilisateurs qui saisissent un email non valide.
Nombre : ce type de champ autorise uniquement la saisie numérique. Les utilisateurs qui saisissent des caractères non numériques recevront une erreur.
Date : ce type de champ valide la saisie de l’utilisateur par rapport à un format de date standard. Les dates en dehors d’une plage raisonnable peuvent également être marquées comme non valides.
URL : ce type de champ valide la saisie de l’utilisateur par rapport à un format d’URL valide. Un message d’erreur s’affiche lorsque les utilisateurs saisissent une URL non valide.
Tel : ce type de champ est spécialement conçu pour les numéros de téléphone et peut déclencher une validation en fonction de formats de pays spécifiques (non pris en charge universellement).


## En savoir plus

* [Créer et prévisualiser un formulaire](/help/edge/docs/forms/create-forms.md)
* [Activer le formulaire pour envoyer des données](/help/edge/docs/forms/submit-forms.md)
* [Publier un formulaire sur la page de sites](/help/edge/docs/forms/publish-eds-forms.md)
* [Ajouter des validations à des champs de formulaire](/help/edge/docs/forms/validate-forms.md)
* [Modifier les thèmes et le style du formulaire](/help/edge/docs/forms/style-theme-forms.md)