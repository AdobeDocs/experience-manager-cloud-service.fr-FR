---
title: Composant Sous-formulaire dans l’éditeur de communication interactive
description: Le composant Sous-formulaire de l’éditeur de communication interactive d’AEM Forms vous permet d’organiser plusieurs éléments de formulaire de manière flexible et structurée.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: e651869132a232db577e94946c082c46eea26bb3
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 10%

---


# Composant Sous-formulaire dans l’éditeur de communication interactive

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque de prompts est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les prompts, les exemples et les bonnes pratiques peuvent changer à mesure que Forms Experience Builder continue d’évoluer dans le cadre du programme des utilisateurs et utilisatrices initiaux.

## &#x200B;1. Présentation

Le composant **Sous-formulaire** de l’éditeur de communication interactive (IC) agit comme un conteneur de disposition dynamique qui vous permet d’organiser plusieurs éléments de formulaire de manière flexible et structurée. Il est généralement utilisé pour regrouper des champs associés, créer des sections extensibles ou définir des structures de données imbriquées pour améliorer l’expérience utilisateur et la liaison de données.

Les sous-formulaires peuvent être configurés pour s’afficher dans différentes dispositions, de haut en bas ou de gauche à droite, ce qui les rend idéaux pour les conceptions de formulaire complexes et les sections réutilisables.

![Rechercher un document IC](/help/forms/interactive-communication/assets/subform.png)

## &#x200B;2. Propriétés

2.1 Propriétés de base

- **Nom :** identifiant unique du sous-formulaire utilisé pour le référencement, les modèles de données et les règles métier.

- **Contenu :** définit la disposition des éléments à l’intérieur du sous-formulaire.

   - **Positionné :** placement absolu des éléments enfants en utilisant les coordonnées X et Y.

   - **Distribué (de haut en bas) :** organise les éléments verticalement.

   - **Distribué (de gauche à droite) :** organise les éléments horizontalement.

2.2 Position

- **Description :** détermine le placement du sous-formulaire dans la disposition Communication.

- **Paramètres:**

   - Coordonnées X et Y (en mm)

   - Largeur et Hauteur (en mm)

2.3 Apparence

- **Remplir :** indique la couleur d’arrière-plan de la zone de sous-formulaire.

- **Contour :** définit la couleur de la bordure.

- **Largeur :** permet de définir l’épaisseur de la bordure.

- **Style :** sélectionnez l’un des paramètres visuels prédéfinis, tels que plat, bordé ou élevé.

- **Arêtes :** détermine le style des angles (arrondis ou nets).

2.4 Présence

- **Description :** contrôle la visibilité du sous-formulaire lors de l’exécution.

- **Options:**

   - **Visible :** toujours affiché.

   - **Caché :** non affiché, mais l’espace est conservé dans la disposition.

2.5 Liaison de données

- **Type de liaison de données :** lie le sous-formulaire à une structure de données (généralement XML ou JSON).

- **Utiliser le nom :** lie les données à l’aide du nom attribué au sous-formulaire.

- **Utiliser les données globales :** connecte le sous-formulaire à un chemin de schéma global pour l’utilisation des données partagées.

- **Aucune liaison de données :** sous-formulaire ne stocke ni n’interagit avec aucun modèle de données externe.

## &#x200B;3. Utilisation

Les sous-formulaires sont essentiels dans les scénarios nécessitant le regroupement, l’imbrication ou la répétition de jeux de champs. Les applications typiques incluent :

- Organisation des blocs d’adresse (par exemple, rue, ville, code postal)

- Sections répétées pour éléments de ligne ou entrées multiples

- Structurer la logique de formulaire conditionnel à l’aide de la visibilité et des règles
Les sous-formulaires peuvent également être utilisés comme conteneurs pour l’alignement de la conception par glisser-déposer dans des dispositions statiques et dynamiques.

## &#x200B;4. Bonnes Pratiques

- Choisissez la disposition appropriée (fluide ou positionné) en fonction de la conception et des besoins en matière de données.

- Utilisez des noms significatifs pour faciliter l’intégration des données et le référencement des règles.

- Mettre en forme des sous-formulaires pour distinguer visuellement les sections groupées

- Lors de l’utilisation de sous-formulaires qui se répètent, assurez-vous que les données sont correctement liées aux structures tableaux.

- Appliquez des règles de visibilité conditionnelle pour optimiser l’expérience utilisateur dans les formulaires complexes.

Le composant **Sous-formulaire** de l’éditeur de communication interactive offre un moyen puissant de structurer et de contrôler des dispositions de formulaires complexes. Qu’il s’agisse d’organiser des champs de saisie, de gérer du contenu dynamique ou d’activer la conception modulaire, les sous-formulaires améliorent la convivialité et la maintenance des modèles de document.


