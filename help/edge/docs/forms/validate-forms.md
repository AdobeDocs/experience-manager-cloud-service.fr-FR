---
title: Des feuilles de calcul aux formulaires - Maîtriser les validations des champs de bloc de formulaires adaptatifs
description: Créez plus rapidement des formulaires performants à l’aide de feuilles de calcul et de champs du bloc de formulaires adaptatifs. Ce guide vous permet de créer des validations personnalisées pour les champs de bloc de formulaires EDS.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 16e1d42a-42d0-4335-ba81-feedea7ed7d7
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 100%

---

# Ajouter des validations à des champs de formulaires

Le bloc de formulaires adaptatifs dispose de fonctionnalités de validation intégrées. Les validations sont automatiquement appliquées dans les navigateurs modernes en fonction du type de champ choisi et des propriétés supplémentaires que vous ajoutez.

## Présentation des types de champ et de la validation

Le bloc de formulaires adaptatifs prend en charge un large éventail de [types d’entrée HTML5](https://developer.mozilla.org/fr-fr/docs/Web/HTML/Element/input#input_types), y compris le texte, l’e-mail, le numéro, la date, etc. Il prend également en charge [textarea](https://developer.mozilla.org/fr-fr/docs/Web/HTML/Element/textarea), select et fieldset, ainsi que des fonctionnalités exhaustives de validation des entrées inhérentes au HTML5.

Il utilise des types de champs HTML pour définir le type de données qu’un utilisateur ou une utilisatrice peut saisir. Les différents types de champ ont des règles de validation intégrées différentes :

E-mail : ce type de champ valide automatiquement la saisie de l’utilisateur ou de l’utilisatrice par rapport à un format d’adresse e-mail commun. Un message d’erreur s’affiche pour les utilisateurs et les utilisatrices qui saisissent un e-mail non valide.
Nombre : ce type de champ autorise uniquement une saisie numérique. Les utilisateurs et les utilisatrices qui saisissent des caractères non numériques obtiendront une erreur.
Date : ce type de champ valide la saisie de l’utilisateur ou de l’utilisatrice par rapport à un format de date standard. Les dates en dehors d’une plage raisonnable peuvent également être indiquées comme non valides.
URL : ce type de champ valide la saisie de l’utilisateur ou de l’utilisatrice par rapport à un format d’URL valide. Un message d’erreur s’affiche lorsque les utilisateurs et les utilisatrices saisissent une URL non valide.
Tél : ce type de champ est spécialement conçu pour les numéros de téléphone et peut déclencher la validation en fonction des formats spécifiques des pays (la prise en charge n’est pas universelle).



