---
title: Notes de mise à jour de l’éditeur universel version 2025.06.19
description: Il s’agit des notes de mise à jour de la version 2025.06.19 de l’éditeur universel.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 5ffae9e548ca952975b3ea805808e227102ec99f
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 26%

---


# Notes de mise à jour de l’éditeur universel version 2025.06.19 {#release-notes}

Voici les notes de mise à jour de la version du 19 juin 2025 de l’éditeur universel.

>[!TIP]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service.

## Nouveautés {#what-is-new}

* **Prise en charge de plusieurs champs dans le rail Propriétés** -
  Le [composant de conteneur](/help/implementing/universal-editor/field-types.md#container) peut désormais être utilisé pour créer des propriétés à champs multiples.
* **Prise en charge des propriétés imbriquées** - Le champ [`name` ](/help/implementing/universal-editor/field-types.md#nesting) prend désormais en charge les chemins d’accès pour activer l’imbrication des propriétés.
* **Panneau droit redimensionnable** - Le panneau latéral peut désormais être redimensionné pour mieux prendre en compte le contenu plus long affiché dans ce dernier.

## Fonctionnalités d’adoption précoce {#early-adopter}

Pour avoir la possibilité de tester certaines des fonctionnalités à venir, faites partie du programme des utilisateurs et utilisatrices précoces d’Adobe.

### **Annuler/rétablir** {#undo-redo}

Les fonctions Annuler et Rétablir sont désormais disponibles pour les créateurs et créatrices de contenu dans l’éditeur universel.

* Cela inclut les modifications effectuées dans le contexte, les modifications effectuées via le panneau Propriétés, ainsi que l’ajout (ou la duplication), le déplacement et la suppression de blocs.
* Les options Annuler et Rétablir sont limitées à la session du navigateur en cours.

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail à la personne responsable de votre équipe du succès client Adobe à partir de l’adresse e-mail associée à votre Adobe ID.

## Autres améliorations {#other-improvements}

* Des erreurs de collision de clés de ressource lors du déplacement de blocs entre des conteneurs ont été corrigées.
* Correction d’un problème en raison duquel la duplication du dernier bloc d’un conteneur échouait.
* La liste déroulante Ajouter une action répertorie désormais uniquement les composants dotés d’un module externe approprié défini dans le fichier `component-definition.json`.
* La date de modification utilisée par la boîte de dialogue de publication a été corrigée car, dans certains cas, les pages n’étaient pas reconnues comme modifiées et n’étaient pas republiées.
* Correction du comportement d’héritage du MSM où la modification d’un conteneur annulait l’héritage pour les nœuds enfants.
* `fetchUrl` a été corrigé, restaurant les blocs mobiles d&#39;un conteneur à un autre.
