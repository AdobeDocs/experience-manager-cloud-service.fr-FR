---
title: Composant Champ de texte dans l’éditeur de communication interactive
description: Composant Champ de texte dans l’éditeur de communication interactive d’AEM Forms pour permettre aux auteurs d’afficher des informations telles que des noms, des adresses, des commentaires ou des identifiants numériques.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: bd8992792afddb2243736578acd24bc47efad842
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 7%

---


# Composant Champ de texte dans l’éditeur de communication interactive

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque de prompts est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les prompts, les exemples et les bonnes pratiques peuvent changer à mesure que Forms Experience Builder continue d’évoluer dans le cadre du programme des utilisateurs et utilisatrices initiaux.

## &#x200B;1. Introduction

Le composant Champ de texte de l’éditeur de communication interactive (IC) permet aux auteurs d’afficher des informations telles que des noms, des adresses, des commentaires ou des identifiants numériques. La valeur affichée dans le champ de texte est prédéfinie (statique) ou remplie dynamiquement à l’aide de la liaison de données. Il prend en charge les entrées sur une seule ligne, les règles de validation et une mise en forme flexible, ce qui en fait l’un des éléments les plus utilisés et polyvalents dans les communications personnalisées.

![Rechercher document IC](/help/forms/interactive-communication/assets/textfield.png)

## &#x200B;2. Propriétés

2.1 Champ de base

- **Nom :** permet de définir un identifiant unique pour le champ, utilisé dans les modèles de données, les règles et les scripts.

- **Légende :** permet d’afficher le libellé à l’écran présenté aux utilisateurs (par exemple, « Prénom »).

- **Valeur :** afficher du texte tel que des noms, des adresses, des remarques ou d’autres détails. La valeur est statique ou dérivée de la liaison de données.

- **Réserver :** définissez l’alignement de la valeur, à gauche, à droite, en haut ou en bas, ou spécifiez une position personnalisée à l’aide d’unités telles que les millimètres (20 mm, par exemple).

- **Apparence :** définissez l’apparence de la zone de valeur sur Aucune, Zone pleine ou Soulignement selon la disposition visuelle souhaitée.

2.2 Typographie

Contrôle le style visuel des caractères saisis :

- **Validation des polices :** appliquez des contraintes facultatives pour valider le format de la valeur affichée, par exemple en n’autorisant que les lettres, les nombres ou des modèles personnalisés spécifiques.

- **Taille de police :** ajustez la taille du texte dans le champ à l’aide de valeurs de point telles que 10 pt, 12 pt, 20 pt, etc. pour garantir la lisibilité et l’alignement avec les normes de conception.

2.3 Position

Définit l’emplacement du champ dans la mise en page :

- Coordonnées **X/Y**

- **Largeur et Hauteur** (mm, px ou %)

2.4 Marge

Indique l’espacement autour du conteneur de champs :

- Haut (Haut)

- Bas (Bas)

- Gauche

- Droite

2.5 Apparence

Applique un style au conteneur de champs lui-même :

- **Remplissage :** définit la couleur d’arrière-plan de la zone de texte. Cela permet de distinguer les zones de saisie ou de les aligner sur les couleurs de la marque.

- **Contour :** ajoutez des bordures autour de la zone de texte avec les propriétés personnalisables suivantes :

- **Largeur :** permet de définir l’épaisseur de la bordure.

- **Style :** vous permet d’effectuer un choix parmi les styles de bordure pleins, en tirets ou en pointillés.

- **Edge :** sélectionnez la forme des coins, arrondie ou nette.

- **Rayon :** permet d’ajuster la courbure des angles à l’aide de valeurs de rayon (4 px, 10 px, par exemple) pour un aspect plus souple ou plus angulaire.

2.6 Présence

Détermine la visibilité au moment de l’exécution :

- **Visible :** affiché et occupe de l&#39;espace

- **Caché (conserve l’espace) :** invisible, mais l’espace de disposition est réservé

2.7 Liaison de données

Associe le champ de texte à une source de données pour afficher les valeurs de manière dynamique ou statique dans la communication.

- **Type de liaison de données :** indique comment le champ se connecte à une source de données ou à un schéma.

- **Utiliser le nom :** lie le champ de texte à l’aide du nom de champ défini dans le modèle de données ou le schéma, ce qui permet l’affichage de texte dynamique en fonction de données externes.

- **Utiliser les données globales :** connecte le champ aux données globales partagées dans l’ensemble de la communication pour garantir la cohérence de l’affichage des informations.

- **Aucune liaison de données :** permet de ne lier le champ d’aucune source du serveur principal. Il est utilisé pour afficher des valeurs statiques ou du texte destiné uniquement au contexte visuel.

## &#x200B;3. Utilisation

Voici quelques exemples de scénarios courants :

- Capturer des informations personnelles (noms, adresses, numéros de téléphone)

- Acceptation de commentaires ou de commentaires (multiligne)

- Saisir des numéros de stratégie ou des identifiants de compte

- Collecter des valeurs numériques courtes telles que des codes PIN ou des OTP

Les auteurs peuvent placer le champ dans des sous-formulaires ou des grilles de disposition pour l’alignement et joindre des règles de validation (limites de longueur, modèles d’expression régulière) pour garantir une entrée épurée.

## &#x200B;4. Bonnes Pratiques

- Appliquez une validation (indicateurs obligatoires, contrôles de motifs) pour un retour d’informations immédiat.

- Fournissez un texte de réserve significatif pour les vues imprimées ou en lecture seule.

- Conservez la cohérence de la typographie avec les directives de la marque.

- Réduisez la largeur de champ sur les dispositions pour appareils mobiles pour l’adapter aux écrans plus petits.

- Liez directement au modèle de données chaque fois que cela est possible pour une maintenance plus simple.

Le composant Champ de texte de l’éditeur IC est un bloc de création polyvalent qui simplifie la capture de données. Lorsqu’elle est configurée de manière réfléchie, avec une typographie bien choisie, des libellés clairs, une validation appropriée et une liaison de données solide, elle offre une expérience transparente et conviviale, ainsi que des données fiables pour le traitement en aval.


