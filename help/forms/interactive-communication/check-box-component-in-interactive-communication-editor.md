---
title: Composant de case à cocher dans l’éditeur de communication interactive
description: Le composant de case à cocher dans l’éditeur de communication interactive d’AEM Forms permet aux utilisateurs d’effectuer des sélections binaires uniques ou multiples (oui/non, true/false).
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: bd8992792afddb2243736578acd24bc47efad842
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 8%

---


# Composant de case à cocher dans l’éditeur de communication interactive

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque de prompts est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les prompts, les exemples et les bonnes pratiques peuvent changer à mesure que Forms Experience Builder continue d’évoluer dans le cadre du programme des utilisateurs et utilisatrices initiaux.

## &#x200B;1. Introduction

Le composant Case à cocher de l’éditeur de communication interactive (IC) permet aux utilisateurs d’effectuer des sélections binaires uniques ou multiples (oui/non, true/false). Généralement utilisé pour les conditions générales, les préférences, les champs de consentement et les opt-ins, il fournit un moyen rapide de capturer une entrée booléenne dans un formulaire de communication.

La case à cocher prend en charge un style flexible, des options de liaison de données et des règles de visibilité, ce qui en fait un outil léger mais puissant dans la conception de formulaires interactifs et conviviaux.

![Rechercher un document IC](/help/forms/interactive-communication/assets/checkbox.png)

## &#x200B;2. Propriétés

2.1 Champ de base

- **Nom :** identifiant unique utilisé pour référencer la case à cocher dans les modèles de données, les règles ou les scripts.

- **Basculer :** permet d’activer/désactiver la case à cocher lorsque l’utilisateur clique dessus. Vous pouvez l’utiliser en mode unique ou groupé.

- **Légende :** libellé descriptif affiché à côté de la case à cocher, guidant les utilisateurs et les utilisatrices sur ce qu’ils acceptent ou sélectionnent.

- **Réserve :** texte ou symbole d’espace réservé facultatif affiché en lecture seule ou en mode de secours lorsqu’aucune interaction n’est effectuée.

2.2 Position

Définit l&#39;emplacement de la case à cocher dans la mise en page :

- Coordonnées **X et Y :** définissez l’emplacement de la case à cocher dans la grille de disposition.

- **Hauteur et largeur :** définit les dimensions de la case à cocher (en mm ou px), ce qui est particulièrement important lors de l’utilisation de styles visuels ou d’icônes personnalisés.

2.3 Marge

Permet un espacement autour de la case à cocher pour les réglages de disposition :

- Haut (Haut)

- Bas (Bas)

- Gauche

- Droite

2.4 Apparence

Contrôle le style visuel de la case à cocher et de son cadre :

- **Remplissage :** couleur d’arrière-plan de la case à cocher (lorsqu’elle est sélectionnée ou non).

- **Contour :** couleur de contour de la bordure de la case à cocher.

- **Largeur du trait :** épaisseur de la ligne de bordure.

- **Style :** motif de contour uni, en tirets ou personnalisé.

- **Arêtes :** définit le style d’angle de la case à cocher : arêtes arrondies ou vives selon les préférences de conception.

2.5 Présence

Détermine comment et quand la case à cocher s’affiche au moment de l’exécution :

- **Visible :** s’affiche normalement et occupe de l’espace.

- **Masqué (conserve l’espace) :** masqué de l’interface utilisateur, mais l’espace de disposition est conservé. Utile pour une visibilité conditionnelle sans rupture de mise en page.

2.6 Liaison de données

Permet à la case à cocher d’interagir avec des sources de données externes ou internes :

**Type de liaison de données :**

**Utiliser le nom :** lie la valeur à l’aide du nom de champ du composant.

**Utiliser des données globales :** se connecte à un modèle de données global partagé dans la communication.

**Aucune liaison de données :** la case à cocher reste autonome et n’est pas stockée dans le modèle de données.

&#x200B;3. Utilisation

Les cases à cocher sont généralement utilisées dans des scénarios tels que :

- **Champs de consentement :** exemple, « J’accepte les conditions générales »

- **Préférences utilisateur :** par exemple, « S’abonner à la newsletter »

- **Sélections à choix multiples :** exemple, « Sélectionner toutes les options applicables »

- **Accusés de réception de formulaire :** ex. « Je confirme que les détails ci-dessus sont corrects »

Les cases à cocher peuvent être placées dans des grilles ou des panneaux de disposition et regroupées pour une meilleure organisation dans les formulaires.

&#x200B;4. Bonnes Pratiques

- Utilisez des légendes claires et concises pour aider les utilisateurs et les utilisatrices à comprendre ce qu’ils ou elles sélectionnent.

- Évitez de surcharger en utilisant des cases à cocher uniquement pour les entrées binaires ; utilisez des boutons radio pour les options exclusives.

- Assurez-vous que l’espacement est correct en utilisant les paramètres de marge et de disposition pour une interface utilisateur épurée.

- Liez les cases à cocher à une référence de modèle de données significative lorsque le choix capturé doit être stocké ou traité.

- Utilisez des règles de visibilité lorsque les cases à cocher dépendent d’entrées ou de conditions antérieures.

Le composant Case à cocher dans l’éditeur de communication interactive est un composant simple mais essentiel pour les entrées binaires. Avec la prise en charge du style, de la présence conditionnelle et de la liaison de données flexible, il joue un rôle clé dans l’amélioration de l’interactivité et du contrôle utilisateur dans les formulaires numériques intelligents. Lorsqu’elles sont mises en œuvre avec des libellés réfléchis, un style cohérent et une intégration significative des données, les cases à cocher contribuent de manière significative à une expérience de formulaire fluide et intuitive.


