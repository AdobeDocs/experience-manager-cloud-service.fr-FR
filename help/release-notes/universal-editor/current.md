---
title: Notes de mise à jour de l’éditeur universel version 2025.07.09
description: Il s’agit des notes de mise à jour de la version 2025.07.09 de l’éditeur universel.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 199ee7e11f6706773bd426c3d27236d6ea791a6c
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 25%

---


# Notes de mise à jour de l’éditeur universel version 2025.07.09 {#release-notes}

Voici les notes de mise à jour de la version du 9 juillet 2025 de l’éditeur universel.

>[!TIP]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service.

## Nouveautés {#what-is-new}

* [Lorsque vous cliquez sur le bouton de la barre d’outils **Ajouter** sur des conteneurs](/help/sites-cloud/authoring/universal-editor/authoring.md#adding-components) si un seul type de composant est autorisé, il est inséré immédiatement sans qu’il soit nécessaire de le sélectionner dans le menu déroulant.
* [L’option de la barre d’outils d’en-tête d’authentification](/help/sites-cloud/authoring/universal-editor/navigation.md#autentication-settings) a été placée derrière un bouton (bascule) de fonctionnalité, car elle n’est pas utile dans la plupart des cas.
* [L’imbrication de conteneurs n’étant pas autorisée pour les champs multiples dans le panneau des propriétés](/help/implementing/universal-editor/field-types.md#fields) la routine de rendu filtre désormais les conteneurs imbriqués de la liste des champs pour éviter toute imbrication non valide.

## Fonctionnalités d’adoption précoce {#early-adopter}

Si vous souhaitez tester ces prochaines fonctionnalités et partager vos commentaires, envoyez un e-mail à votre responsable du succès client Adobe à partir de l’adresse e-mail associée à votre Adobe ID.

### Nouvel éditeur de texte enrichi {#new-rte}

Le nouvel éditeur de texte enrichi ProseMirror, avec un sélecteur de page dans la boîte de dialogue du lien, est désormais disponible dans le panneau de droite.

### Annuler/rétablir {#undo-redo}

Les fonctions Annuler et Rétablir sont désormais disponibles pour les créateurs et créatrices de contenu dans l’éditeur universel.

* Cela inclut les modifications effectuées en contexte, les modifications effectuées via le panneau Propriétés, ainsi que l’ajout (ou la duplication), le déplacement et la suppression de blocs.
* Les options Annuler et Rétablir sont limitées à la session de navigateur en cours.

## Autres améliorations {#other-improvements}

* Correction d’un problème en raison duquel la suppression de la référence d’une ressource unique n’était pas possible lors de la modification via le rail de propriété.
* Correction d’un problème en raison duquel le panneau Propriétés se chargeait indéfiniment, car les références aux ressources étaient automatiquement converties en tableaux, provoquant un chargement infini.
   * Les valeurs de référence des ressources sont désormais stockées en l’état, sans conversion automatique en tableaux.
* Correction d’un problème en raison duquel le panneau Propriétés n’affichait pas les champs lorsqu’un modèle était défini mais ne contenait aucun contenu.
   * Cela entraînait un chargement infini du panneau Propriétés pour les réponses de détails vides, comme les fragments de contenu vides.
* La configuration ESLint a été restructurée pour des raisons de compatibilité avec la version 9, y compris les règles mises à jour et la prise en charge des modules externes.

## Obsolescence {#deprecations}

* Le composant `text-input` est désormais officiellement obsolète.
   * Dans `model-definition.json`, utilisez le composant texte pour créer des entrées de texte pour le panneau Propriétés.
