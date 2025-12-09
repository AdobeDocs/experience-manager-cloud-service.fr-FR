---
title: Composant de champ numérique dans l’éditeur de communication interactive
description: Composant de champ numérique dans l’éditeur de communication interactive d’AEM Forms pour permettre aux auteurs de collecter des entrées numériques des utilisateurs dans un format contrôlé.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: e651869132a232db577e94946c082c46eea26bb3
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 7%

---


# Composant de champ numérique dans l’éditeur de communication interactive

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque de prompts est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les prompts, les exemples et les bonnes pratiques peuvent changer à mesure que Forms Experience Builder continue d’évoluer dans le cadre du programme des utilisateurs et utilisatrices initiaux.

## &#x200B;1. Présentation

Le composant Champ numérique de l’éditeur de communication interactive (IC) permet aux auteurs de collecter des entrées numériques des utilisateurs dans un format contrôlé. Qu’il s’agisse de capturer des numéros de téléphone, des codes PIN, des ID de politique ou des chiffres financiers, ce champ garantit que seules les valeurs numériques sont acceptées. Le composant prend également en charge le style, la mise en forme, la validation et la liaison de données, ce qui le rend essentiel pour les communications structurées.

![Rechercher document IC](/help/forms/interactive-communication/assets/numericfield.png)

## &#x200B;2. Propriétés

2.1 Champ de base

- **Nom :** permet de définir un identifiant unique pour le champ, utilisé dans les modèles de données, les règles et les scripts.

- **Légende :** afficher le libellé à l’écran présenté aux utilisateurs (par exemple, « Numéro de téléphone » ou « ID d’employé »).

- **Valeur :** permet aux utilisateurs de saisir des données numériques telles que des numéros de téléphone, des identifiants, des quantités ou des valeurs monétaires.

- **Réserver :** définissez l’alignement de la valeur numérique (gauche, droite, haut ou bas) ou spécifiez une position personnalisée à l’aide d’unités telles que les millimètres (20 mm, par exemple).

- **Apparence :** définissez l’apparence de la zone de valeur sur Aucune, Zone pleine ou Soulignement selon la disposition visuelle souhaitée.

2.2 Typographie

Contrôle le style visuel des caractères numériques saisis par l&#39;utilisateur :

- **Validation des polices :** appliquez des contraintes pour vous assurer que seule une entrée numérique valide est acceptée, telle que des entiers, des décimales ou des plages de nombres, en fonction du type de données prévu.

- **Taille de police :** ajustez la taille du texte numérique à l’aide de valeurs de point telles que 10 pt, 12 pt ou 20 pt pour maintenir la cohérence et la lisibilité dans l’ensemble du formulaire.

2.3 Position

Contrôle le placement spatial du champ numérique sur la zone de travail.

- Coordonnées **X et Y :** définissez l’emplacement exact du champ.

- **Largeur et Hauteur (en mm) :** détermine la taille de la zone de saisie.

2.4 Marge

Définit l’espacement autour de la limite du champ numérique pour un alignement propre.

- Haut (Haut)

- Bas (Bas)

- Gauche

- Droite

2.5 Apparence

Met en forme le conteneur de champs d’entrée numériques pour qu’il corresponde à la disposition visuelle souhaitée :

- **Remplir :** permet de définir la couleur d’arrière-plan du champ numérique. Cela permet de le séparer visuellement des autres éléments ou de le faire correspondre au thème global.

- **Contour :** ajoutez des bordures autour du champ numérique avec les options personnalisables suivantes :

- **Largeur :** permet de définir l’épaisseur de la bordure en fonction de l’accentuation visuelle.

- **Style :** sélectionnez un motif de bordure uni, en tirets ou en pointillés.

- **Edge:** Sélectionnez entre les coins arrondis ou nets pour la bordure.

- **Rayon :** permet d’ajuster l’arrondi du coin à l’aide de valeurs de rayon spécifiques (par exemple, 4 px ou 10 px) pour adoucir ou accentuer l’aspect du champ.

2.6 Présence

Contrôle la visibilité du champ numérique pendant l’exécution.

- **Visible :** état par défaut ; le champ s’affiche normalement.

- **Caché (conserve l’espace) :** le champ est invisible, mais l’espace est conservé dans la disposition.

2.7 Liaison de données

**Type de liaison de données :** connecte le champ numérique à une source de données (XML ou JSON) pour une intégration en temps réel.

**Utiliser le nom :** lie le champ à son nom unique pour la capture simple de valeurs.

**Utiliser des données globales :** associe le champ à un nœud de données partagé entre les formulaires ou les fragments.

**Aucune liaison de données :** maintient le champ statique pour une utilisation visuelle uniquement ou une entrée temporaire.

## &#x200B;3. Utilisation

Les champs numériques sont idéaux dans les scénarios où seuls les chiffres sont des entrées valides. Cas d’utilisation courants :

- Capture des **numéros de téléphone mobile, OTP et NIP**

- Saisie de **numéros de police ou ID d’employé**

- Collecte **quantités numériques ou valeurs monétaires**

- Activation **champs numériques basés sur des étapes** (compteurs ou entrées de score, par exemple)

Les auteurs peuvent placer des champs numériques dans des conteneurs de disposition ou des sous-formulaires et appliquer une validation (comme des contraintes de longueur, de valeur minimale ou maximale) pour améliorer la qualité des données.

## &#x200B;4. Bonnes Pratiques

- Étiqueter clairement les champs numériques avec des unités si nécessaire (par exemple, « Montant en ₹ »).

- Appliquez la validation du format (comme la limite de 10 chiffres pour les numéros de téléphone) pour une meilleure précision.

- Utilisez des valeurs de réserve lorsque les champs sont obligatoires, mais que les données dynamiques peuvent être manquantes.

- Liez les champs numériques de manière réfléchie aux chemins de schéma pour prendre en charge le traitement principal.

- Conservez une apparence et une typographie cohérentes pour correspondre aux directives de la marque.

Le composant **Champ numérique** de l’éditeur de communication interactive est un outil précis et fiable pour la collecte de données numériques. Grâce à une mise en forme robuste, des contrôles de visibilité et des options de liaison de données, il garantit que les entrées numériques sont capturées de manière claire et intégrées de manière transparente dans les formulaires numériques. Lorsqu’elle est stylisée et configurée correctement, elle améliore considérablement la convivialité des formulaires et la précision globale des données.


