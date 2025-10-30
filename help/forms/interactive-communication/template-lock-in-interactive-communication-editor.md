---
title: Verrouillage de modèle dans l’éditeur de communication interactive
description: Le verrouillage de modèle dans l’éditeur de communication interactive permet aux auteurs de modèles de verrouiller la disposition ou le contenu pour les auteurs de documents.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
hide: true
index: false
hidefromtoc: true
source-git-commit: dae482e1f57a3504bf08926b57b89ca9266bd36a
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 11%

---


# Verrouillage de modèle dans l’éditeur de communication interactive

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque de prompts est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les prompts, les exemples et les bonnes pratiques peuvent changer à mesure que Forms Experience Builder continue d’évoluer dans le cadre du programme des utilisateurs et utilisatrices initiaux.

## &#x200B;1. Présentation

La fonction Verrouillage de modèle de l’éditeur de communication interactive (IC) permet aux personnes créant des modèles de restreindre les modifications à des éléments spécifiques d’un modèle de communication. Cela permet d’assurer la cohérence de la conception, de protéger le contenu critique et d’appliquer la gouvernance entre les équipes qui réutilisent des modèles pour créer des communications personnalisées.

Lorsqu’ils sont appliqués, les composants verrouillés apparaissent visuellement distincts et ne peuvent pas être modifiés par les auteurs ou les contributeurs en aval, selon le jeu de type de verrouillage. Cette fonctionnalité permet de maintenir les normes de marque, l’intégrité des données et l’uniformité de la mise en page sur toutes les communications dérivées.

## &#x200B;2. Types de verrous

Les auteurs de modèles peuvent appliquer des verrous de contenu et de disposition, individuellement ou ensemble, pour contrôler les changements de contenu et de disposition dans les modèles de communication interactive :

### 2.1 Verrouillage de contenu

Un verrouillage de contenu limite toute modification du contenu ou des propriétés de l’élément sélectionné. Ce type de verrouillage garantit que les propriétés essentielles de données, de texte ou de conception restent inchangées, même lorsqu’elles sont réutilisées dans plusieurs communications.

Lorsqu’elles sont appliquées, les auteurs ne peuvent pas modifier :

- Contenu texte ou légendes

- Paramètres d’aspect (police, couleur, arrière-plan, bordures, etc.)

- Configurations de liaison de données

- Éléments constitutifs d’un composant de conteneur (tels que des sous-formulaires)

### 2.2 Verrouillage de la disposition

Un verrou de mise en page limite les modifications liées à la position et à la taille d’un élément. Cela garantit que l’alignement visuel et la hiérarchie de conception restent conformes aux normes de la marque ou du document.

Lorsqu’elles sont appliquées, les auteurs ne peuvent pas :

- Déplacer l’élément vers un nouvel emplacement sur la page

- Redimensionner la largeur ou la hauteur de l’élément

## &#x200B;3. Comportement dans les communications dérivées

- Lorsqu’une communication est créée à partir d’un modèle verrouillé, les éléments verrouillés apparaissent en lecture seule dans l’éditeur IC pour les auteurs de communications.

- Les propriétés internes ou les liaisons des composants avec verrouillage de contenu ne peuvent pas être modifiées.

- Les composants avec verrouillage de disposition ne peuvent pas être déplacés ou redimensionnés.

Cela permet aux créateurs de modèles de garder le contrôle sur la conception et la structure tout en permettant aux autres utilisateurs de se concentrer sur le contenu variable et la personnalisation pilotée par les données.

## &#x200B;4. Bonnes Pratiques

- **Verrouiller rapidement les composants critiques :** verrouiller les en-têtes, les pieds de page, les clauses de non-responsabilité et les logos pour garantir la conformité et l’identité de la marque.

- **Utilisation de verrous de contenu pour plus de précision :** protégez les champs liés aux modèles de données principaux ou au texte réglementaire.

- **Utilisez des verrous de mise en page par souci de cohérence :** prévenez les désalignements ou les distorsions visuelles dans les modèles fréquemment réutilisés.

- **Communication de l’utilisation du verrou :** assurez-vous que les utilisateurs en aval savent quelles sections sont intentionnellement restreintes afin d’éviter toute confusion.
