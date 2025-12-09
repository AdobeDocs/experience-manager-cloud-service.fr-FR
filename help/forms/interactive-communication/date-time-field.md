---
title: Champ Date/Heure dans l’éditeur de communication interactive
description: Composant de champ date/heure dans l’éditeur de communication interactive d’AEM Forms pour permettre aux auteurs d’insérer des champs dans lesquels les utilisateurs peuvent sélectionner ou saisir des valeurs de date et/ou d’heure.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: e651869132a232db577e94946c082c46eea26bb3
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 8%

---


# Composant de champ Date/heure dans l’éditeur de communication interactive

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque de prompts est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les prompts, les exemples et les bonnes pratiques peuvent changer à mesure que Forms Experience Builder continue d’évoluer dans le cadre du programme des utilisateurs et utilisatrices initiaux.

## &#x200B;1. Présentation

Le composant **Champ de date/heure** de l’éditeur de communication interactive (IC) permet aux auteurs d’insérer des champs dans lesquels les utilisateurs peuvent sélectionner ou saisir des valeurs de date et/ou d’heure. Ce composant est généralement utilisé pour capturer des informations telles que la date de naissance, les horaires de rendez-vous, les créneaux horaires de réservation ou les dates d’émission/d’expiration des documents.

Le champ prend en charge diverses options de formatage (par exemple, JJ/MM/AAAA, formats de 24 heures ou de 12 heures), des contraintes de validation et la personnalisation de l’apparence pour correspondre à la conception de la communication. Il améliore l’expérience utilisateur en réduisant les erreurs de saisie manuelle et en promouvant la cohérence de la collecte de données.

![Rechercher un document IC](/help/forms/interactive-communication/assets/datetime.png)

## &#x200B;2. Propriétés

Le composant Champ de date et d’heure comprend plusieurs propriétés configurables :

2.1. Champ De Base

- **Nom :** identifiant unique du champ. Utilisé pour le référencement dans les règles, expressions et liaisons de données.

- **Légende :** libellé affiché à côté du champ pour indiquer son objectif (par exemple, « Date de naissance »).

- **Date :** permet aux utilisateurs de sélectionner ou de saisir une date de calendrier.

- **Time :** permet la saisie ou la sélection de valeurs horaires spécifiques si elles sont configurées.

- **Réserve :** valeur de secours affichée lorsqu’aucune entrée n’est fournie, utile pour les scénarios de lecture seule ou d’impression.

- **Apparence :** sélectionnez un style visuel tel que souligné, bordé ou plat pour un rendu cohérent de l’interface utilisateur.

2.2. Typographie

Contrôle le style du texte à l’intérieur du champ date/heure :

- **Variation de police :** les options incluent Standard, Gras et Italique en fonction des exigences du thème.

- **Taille de police :** définie par défaut sur 10 pt pour maintenir la cohérence avec la disposition du formulaire.

2.3. Position

- **Description :** définit l’emplacement du champ date/heure sur la mise en page du formulaire.

- **Paramètres:**

   - Coordonnées **X et Y**

   - **Hauteur et largeur** (mesurée en mm ou pixels) pour le dimensionnement précis du champ.

2.4. Marge

Définit l’espacement autour du champ pour un alignement épuré et une meilleure flexibilité de mise en page :

- Haut (Haut)

- Bas (Bas)

- Gauche

- Droite

2.5. Apparence

Définit le style du conteneur pour maintenir la cohérence et la clarté visuelles :

- **Remplir :** couleur d’arrière-plan du champ.

- **Contour :** couleur de la bordure autour du champ.

- **Largeur :** Épaisseur de la bordure.

- **Style :** types de bordure, tels que plein, tirets ou aucun.

- **Arêtes :** effectuez votre choix parmi des angles vifs ou arrondis en fonction du thème du formulaire.

2.6. Présence

Détermine le comportement du champ au moment de l’exécution :

- **Visible :** le champ s’affiche pour les utilisateurs et occupe l’espace de disposition.

- **Caché (laisse de l’espace) :** le champ n’est pas visible, mais de l’espace lui est toujours réservé dans la mise en page.

2.7. Liaison De Données

Associe le champ à une source de données pour stocker ou récupérer des valeurs.

- **Type de liaison de données :** indique comment le champ se connecte aux données.

- **Utiliser le nom :** lie le champ à l’aide du nom de champ défini dans le schéma.

- **Utiliser les données globales :** connecte le champ aux données globales partagées dans la communication.

- **Aucune liaison de données :** champ n’est connecté à aucune donnée d’arrière-plan (utilisé pour les valeurs visuelles uniquement ou calculées).

## &#x200B;3. Utilisation

Le champ Date/Heure est idéal dans les scénarios où des données temporelles cohérentes sont requises. Cas d’utilisation courants :

- Capturer la date de naissance, la date de rendez-vous ou l’heure de l’événement

- Consignation des dates d&#39;expiration/de problème du document

- Sélection des emplacements de livraison ou de prélèvement

- Enregistrer la date et l&#39;heure des transactions

Les auteurs peuvent combiner le champ avec des conteneurs de disposition, des validations ou des règles conditionnelles pour contrôler le format, les champs obligatoires et la visibilité contextuelle.

## &#x200B;4. Bonnes Pratiques

- Utilisez des légendes claires telles que « Sélectionner une date » ou « Heure du rendez-vous » pour guider les utilisateurs.

- Activez le sélecteur date/heure pour une meilleure expérience utilisateur et moins d’erreurs de saisie.

- Appliquez des restrictions de format (par exemple, des dates futures uniquement) si nécessaire.

- Fournissez une valeur de réserve pour l’accessibilité ou l’impression de secours.

- Conservez la cohérence de la typographie et de l’aspect avec la conception de formulaire globale.

- Liez le champ à un chemin de schéma valide pour garantir une capture et un traitement corrects des données.

Le composant Champ de date et d’heure de l’éditeur de communication interactive est un composant puissant et convivial qui simplifie les entrées temporelles. Avec la configuration appropriée de style, de gestion des données et de contrôles de mise en page, il offre des expériences de formulaire claires, fiables et intuitives pour les utilisateurs et les systèmes principaux.

