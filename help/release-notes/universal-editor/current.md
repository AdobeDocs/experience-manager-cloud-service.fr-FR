---
title: Notes de mise à jour de l’éditeur universel version 2026.02.19
description: Il s’agit des notes de mise à jour de la version 2026.02.19 de l’éditeur universel.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 39137052e9fa409f7f5494be53fa7693aaa60b17
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 28%

---


# Notes de mise à jour de l’éditeur universel version 2026.02.19 {#release-notes}

Voici les notes de mise à jour de la version du 19 février 2026 de l’éditeur universel.

>[!TIP]
>
>Si vous souhaitez tester les fonctionnalités de l’éditeur universel **à venir** avant leur publication, reportez-vous aux [Notes de mise à jour de l’aperçu de l’éditeur universel.](/help/release-notes/universal-editor/preview.md)

>[!TIP]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service.

## Nouveautés {#what-is-new}

* Des améliorations ont été apportées à l’éditeur de texte enrichi.
   * Le [masquage des éléments de barre d’outils dans l’éditeur de texte enrichi en contexte](/help/implementing/universal-editor/configure-rte.md#common-action-options) est désormais pris en charge.
   * Le [renvoi à la ligne de texte à l’intérieur de tableaux avec des paragraphes](/help/implementing/universal-editor/configure-rte.md#table-actions) est désormais pris en charge.
   * [Balises HTML non prises en charge](/help/implementing/universal-editor/configure-rte.md#unsupported-html) les balises peuvent désormais être conservées par l’éditeur de texte enrichi.
   * La logique de l’éditeur de texte enrichi est désormais diffusée à partir d’un fichier distinct.
   * [Les tableaux peuvent désormais être créés](/help/sites-cloud/authoring/universal-editor/authoring.md#formatting-options) ainsi que modifiés à l’aide de l’éditeur de texte enrichi.
* Si aucun libellé n’est défini, le titre du composant de la définition du composant est désormais utilisé.
* `setEditorMode` est désormais disponible via les extensions.

## Fonctionnalités d’adoption précoce {#early-adopter}

Si vous souhaitez tester les prochaines fonctionnalités répertoriées ci-dessous et partager vos commentaires, envoyez un e-mail à votre responsable du succès client Adobe à partir de l’adresse e-mail associée à votre Adobe ID.

* Une copie superficielle a été implémentée pour les fragments de contenu.

## Autres améliorations {#other-improvements}

* Les points d’entrée de l’éditeur de texte enrichi sont désormais servis pour l’éditeur statique.
* La modification des champs imbriqués n’entraîne plus le remplacement des entrées d’homologue de ces structures.
* Les champs obligatoires de l’éditeur de texte enrichi ne peuvent plus être enregistrés comme vides.
* La mise en forme statique n’est plus appliquée de manière incorrecte lors de l’ajout de liens après la mise en forme.
