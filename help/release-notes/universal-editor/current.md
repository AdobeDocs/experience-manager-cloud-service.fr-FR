---
title: Notes de mise à jour d’Universal Editor 2024.09.3
description: Il s’agit des notes de mise à jour de la version 2024.09.3 d’Universal Editor.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: b70acef8dc259fff3041617abe0a89f7eb73dfab
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 1%

---


# Notes de mise à jour d’Universal Editor 2024.09.3 {#release-notes}

Il s’agit des notes de mise à jour de la version du 3 septembre 2024 d’Universal Editor.

>[!TIP]
>
>Pour consulter les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service, reportez-vous à [cette page.](/help/release-notes/release-notes-cloud/release-notes-current.md)

## Nouveautés {#what-is-new}

* **`rootPath`désormais disponible pour le sélecteur de contenu** : le sélecteur de contenu peut désormais être fourni avec un `rootPath` pour présenter à l’utilisateur une sélection ciblée de contenu lors de l’utilisation des types de champs [AEM contenu,](/help/implementing/universal-editor/field-types.md#aem-content) [Fragment de contenu,](/help/implementing/universal-editor/field-types.md#content-fragment) et [Fragment d’expérience](/help/implementing/universal-editor/field-types.md#experience-fragment).
   * La sélection de contenu est ainsi limitée au contenu du chemin d’accès spécifié et aux sous-répertoires.

## Programme d’adoption précoce pour la prise en charge de la version 6.5 {#early-adoption}

Universal Editor est désormais disponible pour les cas d’utilisation sans interface lors de l’utilisation d’AEM 6.5 dans le cadre d’un programme d’adoption précoce.

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un email à votre représentant d’Adobe à partir de l’adresse électronique associée à votre Adobe ID.

## Correctifs {#bug-fixes}

* **Glisser-déposer inter-conteneurs** : [Le déplacement de composants entre différents conteneurs par glisser-déposer](/help/sites-cloud/authoring/universal-editor/authoring.md#reordering-components) respecte désormais les [filtres de composants](/help/implementing/universal-editor/customizing.md#filtering-components) dans la source et la cible.
