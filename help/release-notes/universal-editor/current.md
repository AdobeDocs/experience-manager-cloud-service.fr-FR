---
title: Notes De Mise À Jour De L’Éditeur Universel 2026.05.07
description: Voici les notes de mise à jour de la version 2026.05.07 de l’éditeur universel.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 4f66cd6048d7a78bea33c0f9c21017983b9032d5
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 12%

---


# Notes De Mise À Jour De L’Éditeur Universel 2026.05.07 {#release-notes}

Voici les notes de mise à jour de la version du 7 mai 2026 de l’éditeur universel.

>[!TIP]
>
>Si vous souhaitez tester les fonctionnalités de l’éditeur universel **à venir** avant leur publication, reportez-vous aux [Notes de mise à jour de l’aperçu de l’éditeur universel.](/help/release-notes/universal-editor/preview.md)

>[!TIP]
>
>Pour consulter les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service, voir [cette page.](/help/release-notes/release-notes-cloud/release-notes-current.md)

## Nouveautés {#what-is-new}

* Vous pouvez désormais [glisser-déposer des composants dans l’éditeur pour les déplacer.](/help/sites-cloud/authoring/universal-editor/authoring.md#drag-and-drop-move)
* Un service worker a été introduit pour réduire la latence entre l’interface utilisateur de l’éditeur universel et les systèmes principaux.
* Tous les adaptateurs pour les fragments de contenu (AEM 6.5, OpenAPI et GraphQL) incluent désormais les filtres pour le sélecteur de ressources afin d’assurer la cohérence et de permettre aux utilisateurs de sélectionner uniquement les ressources autorisées.
* `content:patch`’intention est maintenant fournie.
* Pour faciliter l’accessibilité, le flux de création et les repères ont été définis.

## Autres Améliorations À Venir {#other-improvements}

* Les assertions de type inutiles dans `assignImageDimensionFields` ont été supprimées.
* Correction d’un problème en raison duquel la gestion côté serveur de l’opération `add` itérait la valeur de chaîne, en la traitant comme un objet au lieu d’un correctif.
