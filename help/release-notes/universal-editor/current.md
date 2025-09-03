---
title: Notes de mise à jour de l’éditeur universel version 2025.08.22
description: Il s’agit des notes de mise à jour de la version 2025.08.22 de l’éditeur universel.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: cd717eac1e4eb6eda3b2a60fc28ad63d92e858ec
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 71%

---


# Notes de mise à jour de l’éditeur universel version 2025.08.22 {#release-notes}

Voici les notes de mise à jour de la version du 22 août 2025 de l’éditeur universel.

>[!TIP]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service.

## Nouveautés {#what-is-new}

* Nouvelles fonctionnalités pour les [utilisateurs précoces de l’éditeur de texte enrichi](#new-rte)
   * Le titre du lien est désormais disponible dans la boîte de dialogue du lien.
   * La dissociation est désormais disponible.
   * Les éléments de liste prennent désormais en charge le formatage en ligne et les liens.
   * La zone défilable a été corrigée.

## Fonctionnalités d’adoption précoce {#early-adopter}

Si vous souhaitez tester ces nouvelles fonctionnalités à venir et partager vos commentaires, envoyez un e-mail à la personne responsable du succès client d’Adobe de votre équipe à partir de l’adresse e-mail associée à votre Adobe ID.

### Nouvel éditeur de texte enrichi {#new-rte}

Le nouvel éditeur de texte enrichi ProseMirror, qui présente un sélecteur de page dans la boîte de dialogue du lien, est désormais disponible dans le panneau de droite.

### Annuler, rétablir {#undo-redo}

Les fonctions Annuler et Rétablir sont désormais disponibles pour les créateurs et créatrices de contenu dans l’éditeur universel.

* Cela inclut les modifications effectuées en contexte, les modifications effectuées via le panneau Propriétés, ainsi que l’ajout (ou la duplication), le déplacement et la suppression de blocs.
* Les options Annuler et Rétablir sont limitées à la session de navigateur en cours.

## Autres améliorations {#other-improvements}

* [La fonction Annuler/Rétablir pour les utilisateurs et utilisatrices précoces](#undo-redo) ne déclenche plus le rechargement d’une page lorsqu’un composant est ajouté par le biais d’une opération d’annulation ou de restauration.

## Obsolescence {#deprecations}

* Les composants `text-input` et `text-area` ont été officiellement abandonnés avec la [version 2025.07.09](/help/release-notes/universal-editor/2025/2025-07-09.md).
   * Dans `model-definition.json`, utilisez le composant texte pour créer des entrées de texte pour le panneau Propriétés.
