---
title: Notes De Mise À Jour De L’Éditeur Universel 2026.05.28
description: Voici les notes de mise à jour de la version 2026.05.28 de l’éditeur universel.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 63c3a7e2ca28890370701fd388f6cc9f068c6dc5
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 14%

---


# Notes De Mise À Jour De L’Éditeur Universel 2026.05.28 {#release-notes}

Voici les notes de mise à jour de la version du 28 mai 2026 de l’éditeur universel.

>[!TIP]
>
>Si vous souhaitez tester les fonctionnalités de l’éditeur universel **à venir** avant leur publication, reportez-vous aux [Notes de mise à jour de l’aperçu de l’éditeur universel.](/help/release-notes/universal-editor/preview.md)

>[!TIP]
>
>Pour consulter les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service, voir [cette page.](/help/release-notes/release-notes-cloud/release-notes-current.md)

## Nouveautés {#what-is-new}

* Un nouveau bouton a été ajouté à la barre d’outils [pour accéder aux propriétés de la page AEM](/help/sites-cloud/authoring/universal-editor/authoring.md#page-properties).
   * Cela apporte la fonctionnalité de l’ancienne `aem-page-properties` [extension](/help/implementing/universal-editor/extending.md) de manière native à l’éditeur universel.
   * Le bouton s’affiche uniquement lorsque la page distante possède une [connexion avec le protocole](/help/implementing/universal-editor/component-definition.md#plugins) le `aem` ou le `xwalk` et qu’un chemin de page unique peut être résolu à partir de l’élément modifiable actuel.

## Autres améliorations {#other-improvements}

* La couleur d’arrière-plan par défaut de la zone de travail de modification est désormais blanche (#FFFFFF) lorsque l’application ne définit aucune couleur d’arrière-plan.
* Correction d’un problème en raison duquel la copie et le collage sur plusieurs pages ne fonctionnaient pas.
