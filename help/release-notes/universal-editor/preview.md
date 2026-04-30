---
title: Notes de mise à jour de l’aperçu de l’éditeur universel
description: Voici les notes de mise à jour de la version préliminaire de l’éditeur universel.
feature: Release Information
role: Admin
exl-id: e8d031aa-4676-4e45-977b-e5dffcc404c4
source-git-commit: f3ba70f276ab534e0becea47390fe58bf8a825d2
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---


# Notes de mise à jour de l’aperçu de l’éditeur universel {#preview}

Voici les notes de mise à jour de la **version d’aperçu** de l’éditeur universel. Ces fonctionnalités sont actuellement disponibles dans l’environnement d’aperçu **de votre éditeur universel**. La mise à disposition de ces fonctionnalités est prévue pour le 7 mai 2026.

Ces notes de mise à jour **aperçu** sont fournies à titre indicatif pour que vous sachiez quelles modifications seront apportées à l’éditeur universel et que vous puissiez les tester en [passant à votre version d’aperçu.](/help/sites-cloud/authoring/universal-editor/navigation.md#user-properties)

>[!TIP]
>
>Pour les **notes de mise à jour actuelles** de l’éditeur universel, consultez le document [Notes de mise à jour de l’éditeur universel.](/help/release-notes/universal-editor/current.md)

>[!NOTE]
>
>Le contenu de la version actuelle ainsi que la date de publication peuvent changer.

## Fonctionnalités à venir {#upcoming-features}

* Un service worker a été introduit pour réduire la latence entre l’interface utilisateur de l’éditeur universel et les systèmes principaux.
* Tous les adaptateurs pour les fragments de contenu (AEM 6.5, OpenAPI et GraphQL) incluent désormais les filtres pour le sélecteur de ressources afin d’assurer la cohérence et de permettre aux utilisateurs de sélectionner uniquement les ressources autorisées.
* `content:patch`’intention est maintenant fournie.
* Pour faciliter l’accessibilité, le flux de création et les repères ont été définis.

## Autres Améliorations À Venir {#other-improvements}

* Les assertions de type inutiles dans `assignImageDimensionFields` ont été supprimées.
* Correction d’un problème en raison duquel la gestion côté serveur de l’opération `add` itérait la valeur de chaîne, en la traitant comme un objet au lieu d’un correctif.
