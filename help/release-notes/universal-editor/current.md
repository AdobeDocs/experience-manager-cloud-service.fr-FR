---
title: Notes de mise à jour de l’éditeur universel version 2025.09.04
description: Il s’agit des notes de mise à jour de la version 2025.09.04 de l’éditeur universel.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 0c380e0faca1db0966d22d056dd1f824a731a7bc
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 71%

---


# Notes de mise à jour de l’éditeur universel version 2025.09.04 {#release-notes}

Voici les notes de mise à jour de la version du 4 septembre 2025 de l’éditeur universel.

>[!TIP]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service.

## Nouveautés {#what-is-new}

* Le copier-coller est disponible pour les [utilisateurs initiaux](#copy-paste)

### Annuler, rétablir {#undo-redo}

Les fonctions Annuler et Rétablir sont désormais disponibles pour les créateurs et créatrices de contenu dans l’éditeur universel.

* Cela inclut les modifications effectuées en contexte, les modifications effectuées via le panneau Propriétés, ainsi que l’ajout (ou la duplication), le déplacement et la suppression de blocs.
* Les options Annuler et Rétablir sont limitées à la session de navigateur en cours.

## Fonctionnalités d’adoption précoce {#early-adopter}

Si vous souhaitez tester ces nouvelles fonctionnalités à venir et partager vos commentaires, envoyez un e-mail à la personne responsable du succès client d’Adobe de votre équipe à partir de l’adresse e-mail associée à votre Adobe ID.

### Nouvel éditeur de texte enrichi {#new-rte}

Le nouvel éditeur de texte enrichi ProseMirror, qui présente un sélecteur de page dans la boîte de dialogue du lien, est désormais disponible dans le panneau de droite.

### Copier/Coller {#copy-paste}

La copie et le collage de composants dans la même page sont désormais disponibles pour les auteurs de contenu.

## Autres améliorations {#other-improvements}

* Mise à jour du style de la barre d’outils de l’éditeur afin de mieux s’aligner sur le nouvel éditeur de texte enrichi à venir.
* Les filtres de la boîte de dialogue du sélecteur de ressources ont été restaurés.

## Obsolescence {#deprecations}

* Les composants `text-input` et `text-area` ont été officiellement abandonnés avec la [version 2025.07.09](/help/release-notes/universal-editor/2025/2025-07-09.md).
   * Dans `model-definition.json`, utilisez le composant texte pour créer des entrées de texte pour le panneau Propriétés.
