---
title: Notes de mise à jour de l’aperçu de l’éditeur universel
description: Voici les notes de mise à jour de la version préliminaire de l’éditeur universel.
feature: Release Information
role: Admin
exl-id: e8d031aa-4676-4e45-977b-e5dffcc404c4
source-git-commit: 374c8045043f67f06d4ae68aef499bb594f1c08c
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Notes de mise à jour de l’aperçu de l’éditeur universel {#preview}

Voici les notes de mise à jour de la **version d’aperçu** de l’éditeur universel. Ces fonctionnalités sont actuellement disponibles dans l’environnement d’aperçu **de votre éditeur universel**. La mise à disposition de ces fonctionnalités est prévue pour le 19 février 2026.

Ces notes de mise à jour **aperçu** sont fournies à titre indicatif pour que vous sachiez quelles modifications seront apportées à l’éditeur universel et que vous puissiez les tester en [passant à votre version d’aperçu.](/help/sites-cloud/authoring/universal-editor/navigation.md#user-properties)

>[!TIP]
>
>Pour les **notes de mise à jour actuelles** de l’éditeur universel, consultez le document [Notes de mise à jour de l’éditeur universel.](/help/release-notes/universal-editor/current.md)

>[!NOTE]
>
>Le contenu de la version actuelle ainsi que la date de publication peuvent changer.

## Nouvelles fonctionnalités à venir {#what-is-new}

* Des améliorations ont été apportées à l’éditeur de texte enrichi.
   * Le masquage des éléments de barre d’outils dans l’éditeur de texte enrichi en contexte est désormais pris en charge.
   * L’encapsulation de texte dans des tableaux avec des paragraphes est désormais prise en charge.
   * Les balises d’éditeur de texte enrichi non prises en charge sont désormais conservées.
   * La logique de l’éditeur de texte enrichi est désormais diffusée à partir d’un fichier distinct.
   * Les tableaux peuvent désormais être créés et modifiés à l’aide de l’éditeur de texte enrichi.
* Si aucun libellé n’est défini, le titre du composant de la définition du composant est désormais utilisé.
* `setEditorMode` est désormais disponible via les extensions.

## Améliorations à venir {#other-improvements}

* La fonctionnalité de copier-coller entre les pages a été corrigée.
* `universal-editor-extensibility` a été déplacé vers `universal-editor`.
* Le nombre de requêtes au point d’entrée des extensions a été réduit.
* Le nombre de démontages RemoteApp est passé de trois à un.
* Les points d’entrée de l’éditeur de texte enrichi sont désormais servis pour l’éditeur statique.
* La modification des champs imbriqués n’entraîne plus le remplacement des entrées d’homologue de ces structures.
* Les champs obligatoires de l’éditeur de texte enrichi ne peuvent plus être enregistrés comme vides.
* La mise en forme statique n’est plus appliquée de manière incorrecte lors de l’ajout de liens après la mise en forme.
