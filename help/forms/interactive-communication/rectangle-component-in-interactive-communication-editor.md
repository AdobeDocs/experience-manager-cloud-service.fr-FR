---
title: Composant Rectangle dans l’éditeur de communication interactive
description: Le composant Rectangle de l’éditeur de communication interactive d’AEM Forms permet aux créateurs et créatrices d’ajouter des éléments graphiques mis en forme qui servent de séparateurs de disposition, d’accents visuels ou de conteneurs de contenu.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: bd8992792afddb2243736578acd24bc47efad842
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 12%

---


# Composant Rectangle dans l’éditeur de communication interactive

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque de prompts est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les prompts, les exemples et les bonnes pratiques peuvent changer à mesure que Forms Experience Builder continue d’évoluer dans le cadre du programme des utilisateurs et utilisatrices initiaux.

## &#x200B;1. Présentation

Le composant Rectangle de l’éditeur de communication interactive (IC) permet aux auteurs d’ajouter des éléments graphiques mis en forme qui servent de séparateurs de disposition, d’accents visuels ou de conteneurs de contenu. Les rectangles améliorent la hiérarchie visuelle et guident l’attention des utilisateurs dans les mises en page de communication structurée.
Ce composant n’est pas lié aux données, mais contribue à améliorer la clarté de la conception, le regroupement des champs associés et l’amélioration de la présentation globale.

![Rechercher un document IC](/help/forms/interactive-communication/assets/rectangle.png)

## &#x200B;2. Propriétés

Le composant Rectangle comprend plusieurs propriétés personnalisables :

2.1. Nom

Nom : identifiant unique du rectangle. Principalement utilisé pour référencer dans les hiérarchies de mises en page ou appliquer des styles de manière cohérente.

2.2. Position

- **Description :** détermine l’emplacement où le rectangle apparaît dans la mise en page du document.

- **Paramètres:**

   - Coordonnées **X et Y :** permet de définir le positionnement horizontal et vertical.

   - **Hauteur et largeur (en mm) :** permet de contrôler la taille du rectangle.

2.3. Marge

Définit l’espacement autour du composant de rectangle pour le séparer des autres éléments de l’interface utilisateur :

- Haut (Haut)

- Bas (Bas)

- Gauche

- Droite

2.4. Apparence

- **Description :** régit le style visuel du rectangle.

- **Options de personnalisation :**

   - **Remplissage :** couleur interne du rectangle.

   - **Contour :** la couleur de contour du rectangle.

   - **Largeur du trait :** épaisseur de la bordure du rectangle.

   - **Style :** styles prédéfinis, tels que plat, bordé ou élevé.

   - **Arêtes :** contrôle l’aspect des coins (par exemple, les arêtes arrondies ou tranchantes).

2.5. Présence

- **Description :** indique si le rectangle s’affiche lorsque la communication est rendue.

- **Options:**

   - **Visible :** affiche le rectangle au moment de l’exécution.

   - **Caché :** conserve l’espace de disposition sans afficher le rectangle.

## &#x200B;3. Utilisation

Le composant Rectangle est généralement utilisé à des fins de mise en page et de style plutôt que pour la saisie de contenu. Cas d’utilisation courants :

- Créer une séparation visuelle entre les sections

- Mise en surbrillance des éléments groupés

- Amélioration de la lisibilité et de l’équilibre visuel

- En-têtes, pieds de page ou sections de légende de cadrage

Les rectangles peuvent être combinés à d’autres éléments de disposition tels que des sous-formulaires ou des conteneurs pour des structures de conception visuelle complexes.

## &#x200B;4. Bonnes Pratiques

- Utilisez un style cohérent pour les rectangles de votre disposition afin d’assurer une harmonie visuelle.

- Appliquez des marges et un espacement adéquats pour éviter d&#39;encombrer les champs adjacents.

- Choisissez des couleurs de fond et de contour alignées sur votre marque ou votre thème de document.

- Utilisez des bords arrondis de manière subtile pour améliorer l’esthétique des mises en page modernes de l’interface utilisateur.

- Masquez les rectangles s’ils ne sont nécessaires qu’à des fins de conception lors de la modification et non dans la sortie finale.

Le composant Rectangle est un outil non interactif, mais puissant dans l’éditeur IC. Lorsqu’elles sont stylisées et positionnées efficacement, elles améliorent la précision de la mise en page, le flux visuel et l’expérience utilisateur sans ajouter de complexité à la liaison ou à l’interactivité des données.


