---
title: Sous-formulaire dans l’éditeur de communication interactive
description: Dans l’éditeur de communication interactive, les sous-formulaires gèrent les dispositions, contrôlent le positionnement des objets et définissent la manière dont le contenu circule sur les pages.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
hide: true
index: false
hidefromtoc: true
source-git-commit: 0c84fa812b74368184d7085fecbb11a1ce4dbfd9
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 10%

---


# Sous-formulaire dans l’éditeur de communication interactive

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque de prompts est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les prompts, les exemples et les bonnes pratiques peuvent changer à mesure que Forms Experience Builder continue d’évoluer dans le cadre du programme des utilisateurs et utilisatrices initiaux.

## &#x200B;1. Présentation

Un sous-formulaire dans l’éditeur de communication interactive est un objet conteneur utilisé pour regrouper des champs, des objets et des composants dans une section logique. Il permet de gérer les mises en page, de contrôler le positionnement des objets et de définir le flux de contenu entre les pages. Les sous-formulaires sont essentiels à la création de communications structurées, réutilisables et réactives, en particulier lorsqu’il s’agit de contenu dynamique ou répété.

Grâce aux sous-formulaires, les créateurs et créatrices peuvent maintenir la cohérence, gérer la pagination et lier des sections entières à des sources de données structurées.

## &#x200B;2. Propriétés

2.1 Dispositions de conception de formulaire

- **Disposition fixe :** objets conservent une position exacte sur la page. Idéal pour les conceptions statiques où un placement précis est requis (par exemple, factures ou lettres officielles).

- **Disposition fluide : les objets** s’ajustent dynamiquement en fonction de la longueur du contenu et de la taille de l’écran. Convient aux communications qui nécessitent une conception réactive ou des longueurs de données variables.

2.2 Positionnement du sous-formulaire

- **Pagination :** contrôle de la répartition des sous-formulaires entre les pages. Les options incluent de conserver les sous-formulaires ensemble ou d’y autoriser les sauts de page.

- **Position :** permet de spécifier si le sous-formulaire doit être placé par rapport à son conteneur parent ou s’il doit s’écouler naturellement dans la mise en page.

- **Apparence :** définissez l’arrière-plan, les bordures et le style du sous-formulaire pour séparer visuellement le contenu.

- **Présence :** permet de configurer les paramètres de visibilité (Visible, Masqué ou Conditionnel) en fonction des règles métier ou des valeurs de données.

2.3 Liaison de données

- Les sous-formulaires peuvent être directement liés aux nœuds ou aux tableaux **Modèle de données de formulaire (FDM)**.

- La liaison permet au sous-formulaire de se répéter dynamiquement pour chaque enregistrement d’une collection (par exemple, plusieurs politiques, transactions ou adresses).

- Prend en charge le remplissage statique et dynamique du contenu en fonction de la structure des données.

## &#x200B;3. Utilisation

Les sous-formulaires sont couramment utilisés pour :

- Structurer des documents en sections comme l’en-tête, le corps et le pied de page.

- Répétition du contenu tel que des tableaux, des énumérations ou des listes de politiques.

- Gestion de la pagination pour que le contenu groupé reste uni

- Affichage conditionnel des sections en fonction de règles ou de valeurs de données.

- Application d’un contrôle de mise en page (fixe ou souple) en fonction du type de communication.

Les auteurs peuvent faire glisser un sous-formulaire de la bibliothèque d’objets vers la zone de travail et ajuster sa disposition, son positionnement et sa liaison à partir du panneau Propriétés.

## &#x200B;4. Bonnes Pratiques

- **Choisissez judicieusement la disposition :** utilisez une disposition fixe pour les formulaires nécessitant un emplacement exact et une disposition fluide pour les communications dynamiques axées sur les données.

- **Lier soigneusement les collections :** pour les listes ou les tableaux, liez directement les sous-formulaires aux collections FDM avec les lignes du modèle.

- **Optimiser la pagination :** empêcher les pauses gênantes en regroupant les objets associés dans un sous-formulaire.

- **Utiliser la présence conditionnelle :** masque ou affiche les sous-formulaires de manière dynamique en fonction des valeurs de données.

- **Conserver la hiérarchie :** imbriquez les sous-formulaires de manière logique pour faciliter la gestion des dispositions complexes.

- **Tester avec des données variées :** prévisualisez avec des jeux de données courts, longs et vides pour vous assurer que la conception s’adapte correctement.

En utilisant efficacement les sous-formulaires, les créateurs et les créatrices peuvent obtenir des dispositions plus épurées, un meilleur contrôle du contenu dynamique et s’assurer que les communications s’adaptent de manière transparente aux scénarios statiques et pilotés par les données.
