---
title: Objet Image dans l’éditeur de communication interactive
description: Créez des fragments de communication interactive dans AEM Forms pour permettre aux auteurs d’améliorer les dispositions de communication en insérant des images statiques.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: acad9e05288a606c54e2059c2381725ac982f7d8
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 14%

---


# Objet Image dans l’éditeur de communication interactive

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque de prompts est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les prompts, les exemples et les bonnes pratiques peuvent changer à mesure que Forms Experience Builder continue d’évoluer dans le cadre du programme des utilisateurs et utilisatrices initiaux.

## &#x200B;1. Présentation

L’objet Image dans l’éditeur de communication interactive permet aux auteurs d’améliorer les dispositions de communication en insérant des images statiques. Ce composant est essentiel pour créer des mises en page visuellement attrayantes et incorporer des éléments de marque tels que des logos ou des icônes visuelles. Les auteurs peuvent le placer dans les pages de Principal et en mode Création pour garantir une apparence cohérente dans divers formats de sortie, tels que PDF.

![Rechercher un document IC](/help/forms/interactive-communication/assets/image.png)

## 2.Properties

L’objet Image fournit plusieurs propriétés pour aider à configurer son apparence et son comportement.

2.1. Description de l’image

Nom :
Agit comme un identifiant unique pour le composant d’image, ce qui permet une référence facile dans la hiérarchie de composant ou l’éditeur de règles.

Sélectionner une image : permet à l’auteur de charger ou de référencer une image, telle qu’un logo, une icône ou tout autre élément visuel statique provenant de plusieurs sources.


2.2. Position

Description : contrôle le positionnement spatial de l’image dans la mise en page.

Paramètres :

Coordonnées X et Y

Hauteur et largeur (en mm)

2.3 Marge

Définissez l’espacement autour de la zone de texte :

- Haut (Haut)

- Bas (Bas)

- Gauche

- Droite

2.4. Apparence

Aspect : définit le style visuel du champ d’image, choisit des paramètres prédéfinis tels que bordé, aplati ou élevé et personnalise avec la couleur de remplissage, la largeur de trait et le style d’angle (arrondi ou aigu).

2.5. Présence

Description : détermine la visibilité de l’objet image au moment de l’exécution.

- Options :

   - Visible

   - Caché (conserve l’espace)

## 3.Usage

L’objet Image est idéal pour :

- Insérer des logos dans les en-têtes de documents

- Affichage des images des produits dans les factures ou les devis

- Amélioration de l’engagement visuel des communications

## 4.Bonnes pratiques

- Utilisez des images d’une bibliothèque partagée pour une réutilisation facile et plus de cohérence.

- Conservez la cohérence de la forme de l’image pour éviter l’étirement ou la pixellisation.

- Évitez d’utiliser des fichiers image très volumineux pour que le document reste rapide et réactif.

- Définissez l’image à afficher ou à masquer de manière conditionnelle si elle n’est pas toujours nécessaire.

L’objet Image dans la communication interactive AEM joue un rôle essentiel dans la création de communications de marque, personnalisées et visuellement efficaces. Grâce à ses propriétés configurables, il améliore l’expérience utilisateur tout en maintenant la cohérence de la conception sur différents formats.
