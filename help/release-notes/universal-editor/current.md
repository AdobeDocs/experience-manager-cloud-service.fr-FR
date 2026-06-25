---
title: Notes De Mise À Jour De L’Éditeur Universel 2026.06.25
description: Voici les notes de mise à jour de la version 2026.06.25 de l’éditeur universel.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: c5aec0d045162327bad3d0d03b22386bf2effe6e
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 13%

---


# Notes De Mise À Jour De L’Éditeur Universel 2026.06.25 {#release-notes}

Voici les notes de mise à jour de la version du 25 juin 2026 de l’éditeur universel.

>[!TIP]
>
>Si vous souhaitez tester les fonctionnalités de l’éditeur universel **à venir** avant leur publication, reportez-vous aux [Notes de mise à jour de l’aperçu de l’éditeur universel.](/help/release-notes/universal-editor/preview.md)

>[!TIP]
>
>Pour consulter les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service, voir [cette page.](/help/release-notes/release-notes-cloud/release-notes-current.md)

## Nouveautés {#what-is-new}

* Un nouveau bouton **Ouvrir dans l’administrateur du site** a été ajouté à la barre d’outils pour accéder à la console AEM Sites.
   * Cela apporte les fonctionnalités de l’ancienne extension **AEM Site Admin Extension** [extension](/help/implementing/universal-editor/extending.md) de manière native à l’éditeur universel.
   * Le bouton permet d’ouvrir la page AEM active dans la console [Sites](/help/sites-cloud/authoring/universal-editor/authoring.md#sites-console) ou dans la console [Fragments d’expérience](/help/sites-cloud/authoring/fragments/experience-fragments.md) pour les chemins d’accès `/content/experience-fragments`.
   * Le bouton est masqué pour les chemins d’accès DAM (`/content/dam`) et lorsqu’aucune page AEM unique ne peut être déterminée à partir des éléments modifiables actuels.
* Les raccourcis clavier à un seul caractère fonctionnent désormais mieux avec les technologies d’accessibilité.

## Autres améliorations {#other-improvements}

* De nombreux boutons portent désormais correctement des noms accessibles.
* Correction d’un problème lié à la conservation de certains fragments de contenu après les avoir sélectionnés à l’aide d’un sélecteur.
