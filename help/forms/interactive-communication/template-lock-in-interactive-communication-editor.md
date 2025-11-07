---
title: Verrouillage de modèle dans l’éditeur de communication interactive
description: Le verrouillage de modèle dans l’éditeur de communication interactive permet aux auteurs de modèles de verrouiller la disposition ou le contenu pour les auteurs de documents.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: 957944da363b506c34c2630aeedbe984442f34b8
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 10%

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

![Rechercher document IC](/help/forms/interactive-communication/assets/template-lock.png)

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

## &#x200B;3. Utilisation du verrouillage de modèle dans l’éditeur de communication interactive

Pour appliquer des verrous de contenu ou de disposition à votre modèle de communication interactive (IC), procédez comme suit :

1. Ouvrez Votre Modèle
Ouvrez ou créez un modèle, suivez le guide [Créer un modèle de communication interactive](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/interactive-communication/overview/create-interactive-communication-template)

1. Sélection du composant
Cliquez sur le composant (zone de texte, image ou sous-formulaire) que vous souhaitez restreindre.

1. Options de verrouillage d&#39;accès
Dans le panneau Propriétés, accédez à la section Verrouillage .

1. Appliquer les verrous

   1. Verrouillage de contenu : empêche les modifications de texte, de style et de données.

   1. Verrouillage de la disposition : limite le mouvement et le redimensionnement.

   1. Vous pouvez activer les deux pour une protection complète.

1. Enregistrer et vérifier
Enregistrez le modèle et créez un code interactif basé sur celui-ci pour confirmer que les éléments verrouillés ne peuvent pas être modifiés.

## &#x200B;4. Bonnes Pratiques

- **Verrouiller rapidement les composants critiques :** verrouiller les en-têtes, les pieds de page, les clauses de non-responsabilité et les logos pour garantir la conformité et l’identité de la marque.

- **Utilisation de verrous de contenu pour plus de précision :** protégez les champs liés aux modèles de données principaux ou au texte réglementaire.

- **Utilisez des verrous de mise en page par souci de cohérence :** prévenez les désalignements ou les distorsions visuelles dans les modèles fréquemment réutilisés.

- **Communication de l’utilisation du verrou :** assurez-vous que les utilisateurs en aval savent quelles sections sont intentionnellement restreintes afin d’éviter toute confusion.
