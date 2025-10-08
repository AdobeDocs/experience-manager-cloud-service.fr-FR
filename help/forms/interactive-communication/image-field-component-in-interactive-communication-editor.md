---
title: Composant Champ d’image dans l’éditeur de communication interactive
description: Composant Champ d’image dans l’éditeur de communication interactive d’AEM Forms pour permettre aux auteurs d’insérer des images dans une disposition de communication.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: bd8992792afddb2243736578acd24bc47efad842
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 10%

---


# Composant Champ d’image dans l’éditeur de communication interactive

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque de prompts est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les prompts, les exemples et les bonnes pratiques peuvent changer à mesure que Forms Experience Builder continue d’évoluer dans le cadre du programme des utilisateurs et utilisatrices initiaux.

## &#x200B;1. Présentation

Le composant Champ d’image de l’éditeur de communication interactive permet aux auteurs d’insérer des images dans une disposition de communication. Elle est idéale pour les cas d’utilisation tels que l’identification par photo, la vérification de documents ou la validation visuelle, où l’affichage d’une image est essentiel pour l’utilisateur final.

Prenant en charge des formats courants tels que **JPEG** et **PNG**, ce composant offre des options de configuration flexibles pour définir l’affichage, le stockage et le style de l’image. Les auteurs peuvent également **attribuer un nom ou un libellé** au champ d’image, ce qui améliore la clarté et l’organisation de la disposition.

![Rechercher un document IC](/help/forms/interactive-communication/assets/imagefield.png)

## &#x200B;2. Propriétés

Le composant Champ d’image comprend plusieurs propriétés configurables :

2.1. Champ De Base

- **Nom :** permet de définir un identifiant unique pour le champ, utilisé pour référencer les modèles de données et les règles.

- **Légende :** permet d’afficher le libellé présenté aux utilisateurs dans l’interface.

- **Sélectionner une image :** permet à l’auteur de charger une image à l’aide de cette propriété, généralement utilisée pour les logos, les identifiants ou d’autres éléments visuels.

- **Réserver l’image :** définissez l’alignement de l’image, à gauche, à droite, en haut ou en bas, ou spécifiez une **position personnalisée** en utilisant des unités telles que les millimètres (par exemple, 20 mm).

2.2. Position

Contrôle le positionnement spatial de l’image dans la mise en page.

- Coordonnées X et Y

- Hauteur et largeur (en mm)

2.3. Marge

Définissez l’espacement autour de la zone de texte :

- Haut (Haut)

- Bas (Bas)

- Gauche

- Droite

2.4. Apparence

Aspect : définit le style visuel du champ d’image, choisit des paramètres prédéfinis tels que bordé, aplati ou élevé et personnalise avec la couleur de remplissage, la largeur de trait et le style d’angle (arrondi ou aigu).

2.5. Présence

Détermine la visibilité du composant image au moment de l’exécution.

- Visible

- Caché (conserve l’espace)

2.6. Liaison De Données

Liez le champ d’image à une source de données pour récupérer et afficher le contenu de l’image dynamique dans la communication.

**Type de liaison de données :** définit la manière dont le champ d’image se connecte à la structure de données ou au schéma sous-jacent.

**Utiliser le nom :** lie le champ d’image à l’aide du nom de champ spécifié dans le modèle de données ou le schéma, ce qui permet de remplir l’image dynamiquement au moment de l’exécution.

**Utiliser les données globales :** connecte le champ d’image aux données globales partagées dans l’ensemble de la communication, en garantissant la cohérence du contenu visuel.

**Aucune liaison de données :** permet de déconnecter le champ de toutes les données principales, ce qui est idéal dans les cas où une image statique est affichée ou lorsque l’image est contrôlée uniquement par le biais des paramètres de l’interface utilisateur.

## &#x200B;3. Utilisation

Le champ d’image est utile dans les contextes où l’envoi d’un contenu visuel est requis. Cas d’utilisation courants :

- Chargement de l&#39;épreuve d&#39;identifiant (passeport, licence)

- Envoi de photos de profil ou personnelles

- Joindre visuellement des documents justificatifs

Les auteurs peuvent placer le champ dans des sous-formulaires ou des conteneurs de mises en page pour l’alignement et utiliser des règles de validation personnalisées pour contrôler les types et tailles de fichiers acceptés.

## &#x200B;4. Bonnes Pratiques

- Utilisez des libellés ou des instructions clairs lorsque vous demandez des chargements d’images.

- Limitez la taille et les formats de fichier par la validation des performances.

- Assurez-vous que les images de secours (réservées) sont accessibles.

- Lier le champ à un chemin d’accès au schéma significatif en cas d’intégration au serveur principal

Le composant Champ d’image de l’éditeur de communication interactive est un composant polyvalent qui améliore l’interactivité du formulaire en activant les chargements de contenu visuel. Lorsqu’elle est conçue avec un style, une validation et une liaison de données, elle prend en charge une expérience utilisateur transparente et une capture de données efficace pour les envois d’images.




