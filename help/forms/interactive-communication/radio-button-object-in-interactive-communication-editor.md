---
title: Objet Bouton radio dans l’éditeur de communication interactive
description: L’objet Bouton radio dans l’éditeur de communication interactive d’AEM Forms permet aux auteurs de présenter un ensemble de choix mutuellement exclusifs aux utilisateurs et utilisatrices, ce qui signifie qu’une seule option peut être sélectionnée à la fois.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: acad9e05288a606c54e2059c2381725ac982f7d8
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 9%

---


# Objet Bouton radio dans l’éditeur de communication interactive

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque de prompts est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les prompts, les exemples et les bonnes pratiques peuvent changer à mesure que Forms Experience Builder continue d’évoluer dans le cadre du programme des utilisateurs et utilisatrices initiaux.

## &#x200B;1. Présentation

Le composant **Bouton radio** de l’éditeur de communication interactive (IC) permet aux auteurs de présenter un ensemble de choix mutuellement exclusifs aux utilisateurs et utilisatrices, ce qui signifie qu’une seule option peut être sélectionnée à la fois. Cela le rend idéal pour les cas d’utilisation tels que les questions Oui/Non, la sélection du genre, les niveaux d’évaluation ou les réponses catégorielles prédéfinies.
Les boutons radio sont intuitifs, faciles à configurer et peuvent être liés à des modèles de données d’arrière-plan pour une capture et une intégration transparentes des données.

![Rechercher un document IC](/help/forms/interactive-communication/assets/radio.png)

## &#x200B;2. Propriétés

L’objet Bouton radio comprend plusieurs propriétés configurables :

2.1. Champ De Base

- **Nom :** identifiant unique du champ. Il est utilisé pour le référencement dans les modèles de données, les règles et la logique commerciale.

- **Basculer :** permet de définir chaque choix sélectionnable dans le groupe de boutons. Chaque bouton (bascule) représente une valeur possible.

- **Légende :** libellé associé au groupe de boutons radio pour guider l’utilisateur.

- **Réserve :** valeur de secours facultative si aucune sélection n’est effectuée ou si la liaison de données est vide.

2.2. Position

Description : contrôle le positionnement spatial du groupe de boutons radio dans la disposition.

**Paramètres:**

- Coordonnées **X et Y**

- **Hauteur et largeur** (définie en mm ou en % pour le design de mise en page réactive)

2.3. Marge

Définissez l’espacement autour de la zone de texte :

- Haut (Haut)

- Bas (Bas)

- Gauche

- Droite

2.4. Présence

- **Description :** détermine la visibilité de l’objet de bouton radio au moment de l’exécution.

- **Options:**

   - **Visible :** affiché aux utilisateurs et occupe de l’espace.

   - **Masqué (laisse de l’espace) :** non visible, mais conserve l’espacement de la disposition.



2.5. Liaison De Données

- **Description :** connecte le groupe de boutons radio à un modèle de données pour capturer l’option sélectionnée.

- **Types de liaison :**

   - **Utiliser le nom :** utilise le nom du champ affecté comme référence pour la liaison.

   - **Utiliser des données globales :** lie le champ à un modèle de données global ou à un élément de schéma.

   - **Aucune liaison de données :** la sélection du bouton radio n’est liée à aucune source de données ; utilisée pour le comportement de l’interface utilisateur uniquement.

## &#x200B;3. Utilisation

Le composant Bouton radio est adapté aux scénarios où les utilisateurs et utilisatrices ne doivent choisir qu’une seule valeur dans une liste. Les cas d’utilisation standard incluent :

- Choisir une méthode de communication préférée (E-mail / Téléphone / SMS)

- Confirmation des décisions binaires (Oui / Non)

- Choisir parmi des options limitées (par exemple, le sexe, la situation de famille)

- Indiquer les niveaux de satisfaction ou les échelles d&#39;entente (p. ex. Pas d&#39;accord / Neutre / D&#39;accord)

Les créateurs et créatrices peuvent regrouper les boutons radio associés et les positionner dans des conteneurs de disposition pour un alignement cohérent. Les libellés peuvent être placés sur la ligne ou au-dessus des boutons, selon les exigences de conception visuelle.

## &#x200B;4. Bonnes Pratiques

- Limitez le nombre d’options à 5 ou moins pour éviter de surcharger l’utilisateur ou l’utilisatrice.

- Utilisez des légendes claires et concises pour décrire ce que l’utilisateur sélectionne.

- Présélectionnez le choix le plus courant ou le plus sûr, le cas échéant.

- Évitez d’utiliser des boutons radio lorsque les utilisateurs doivent être autorisés à choisir plusieurs options. Utilisez plutôt des cases à cocher.

- Liez directement les boutons radio aux nœuds de schéma lors de l’intégration aux modèles de données d’arrière-plan.

- Appliquez un espacement et un alignement cohérents pour une meilleure clarté visuelle, en particulier dans les dispositions compatibles avec les appareils mobiles.

L’objet Bouton radio dans l’éditeur de communication interactive est un composant d’entrée fondamental qui offre une prise de décision propre et structurée aux utilisateurs finaux. Lorsqu’elle est configurée avec des libellés clairs, un espacement réfléchi et une liaison de données, elle garantit une collecte de données fiable et une expérience utilisateur fluide pour les formulaires, les questionnaires et les workflows d’intégration.


