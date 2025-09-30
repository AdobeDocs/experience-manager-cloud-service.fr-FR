---
title: Objet Zone de texte dans l’éditeur de communication interactive
description: L’objet Zone de texte dans l’éditeur de communication interactive d’AEM Forms permet aux auteurs de saisir et d’afficher du contenu textuel dans une communication.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: acad9e05288a606c54e2059c2381725ac982f7d8
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 11%

---


# Objet Zone de texte dans l’éditeur de communication interactive

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque de prompts est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les prompts, les exemples et les bonnes pratiques peuvent changer à mesure que Forms Experience Builder continue d’évoluer dans le cadre du programme des utilisateurs et utilisatrices initiaux.

## &#x200B;1. Présentation

L’objet **Zone de texte** dans l’éditeur de communication interactive permet aux auteurs de saisir et d’afficher du contenu textuel dans une communication. Il s’agit de l’un des composants les plus fondamentaux et les plus utilisés, généralement utilisé pour collecter des noms, des commentaires, des commentaires ou des données personnalisées lors de la conception de communications interactives ou de fragments de communication.

La zone de texte prend en charge la **liaison de données**, ce qui permet aux auteurs de combiner facilement du contenu statique et dynamique, par exemple : ***« Nom de l’utilisateur : @name »***, où @name est un champ de données lié qui est renseigné dynamiquement lorsque le document est enregistré en tant que PDF. En outre, il prend en charge la mise en forme de texte enrichi et un positionnement flexible pour un contrôle de disposition précis.

![Rechercher document IC](/help/forms/interactive-communication/assets/textbox.png)

## &#x200B;2. Propriétés

L’objet de zone de texte fournit un large ensemble de propriétés pour aider à configurer son aspect, son toucher et son comportement.

2.1 Typographie

**Famille de polices :** permet de sélectionner des styles de polices tels qu’Arial, Helvetica, Times New Roman, etc.

**Validation des polices :** des contraintes d’entrée facultatives peuvent être appliquées pour vous assurer que seuls les formats texte, numérique ou spéciaux sont acceptés.

**Alignement du texte :** les options comprennent l’alignement à gauche, à droite, centré ou justifié.

**Style de texte :** activez la mise en forme du texte avec les fonctions gras, italique, barré et souligné.

**Listes :** prend en charge l’insertion de listes triées (numérotées) et non triées (à puces).

2.2 Position

**Largeur et Hauteur :** permet de définir les dimensions de la zone de texte en pixels ou en pourcentage par rapport au conteneur.

2.3 Marge

Définissez l’espacement autour de la zone de texte :

- Haut (Haut)

- Bas (Bas)

- Gauche

- Droite

2.4 Apparence

- **Remplissage du texte :** personnalisez la couleur et la transparence du texte.

- **Remplissage :** définit la couleur d’arrière-plan de la zone de texte.

- **Contour :** Ajouter des bordures avec personnalisable :

   - Largeur (épaisseur)

   - Style (trait plein, tirets, pointillés)

   - Edge (coins arrondis ou nets)

2.5 Présence

**Visible :** paramètre par défaut ; la zone de texte est affichée pour l’utilisateur.

**Masqué :** la zone de texte est incluse dans le formulaire, mais n’est pas affichée.



## &#x200B;3. Utilisation

La zone de texte est utilisée pour :

- Collecter des informations client telles que des noms, des commentaires ou des commentaires.

- Saisir des valeurs alphanumériques.

- Intégration de messages personnalisés à l’aide de modèles de données liés.

- Incorporation dans des fragments pour une utilisation répétée dans des documents.

Les auteurs peuvent faire glisser la zone de texte de la bibliothèque d&#39;objets vers le mode Création ou le mode Maître et configurer son comportement à l&#39;aide du panneau Propriétés.

## &#x200B;4. Bonnes Pratiques

- Associez toujours les zones de texte à des libellés de champ significatifs pour améliorer l’accessibilité.

- Utilisez des validations d’entrée appropriées pour éviter les erreurs de saisie de données.

- Garantissez une disposition réactive en définissant des marges et des largeurs relatives aux conteneurs parents.

- Évitez les styles de police excessifs qui pourraient nuire à la lisibilité.

En configurant les propriétés de la zone de texte de manière approfondie, les auteurs peuvent créer des expériences de communication interactives, réactives et conviviales dans l’éditeur de communication interactive d’AEM.
