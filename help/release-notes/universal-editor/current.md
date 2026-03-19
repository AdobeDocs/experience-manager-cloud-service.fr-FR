---
title: Notes de mise à jour de l’éditeur universel version 2026.03.19
description: Il s’agit des notes de mise à jour de la version 2026.03.19 de l’éditeur universel.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 8d9d162ec5bba99afb1ae86252a49a9880be4e68
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 34%

---


# Notes de mise à jour de l’éditeur universel version 2026.03.19 {#release-notes}

Voici les notes de mise à jour de la version du 19 mars 2026 de l’éditeur universel.

>[!TIP]
>
>Si vous souhaitez tester les fonctionnalités de l’éditeur universel **à venir** avant leur publication, reportez-vous aux [Notes de mise à jour de l’aperçu de l’éditeur universel.](/help/release-notes/universal-editor/preview.md)

>[!TIP]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service.

## Nouveautés {#what-is-new}

* Les éléments dans les propriétés sont maintenant réduits lors du retour à [l’écran d’accueil.](/help/sites-cloud/authoring/universal-editor/navigation.md#home-button)
* [Le sélecteur de ressources](/help/implementing/universal-editor/configure-assets-selector.md) prend désormais en charge les [définitions de filtre.](/help/implementing/universal-editor/filtering.md)
* Si aucune action n’est disponible pour l’élément sélectionné, [le menu contextuel](/help/sites-cloud/authoring/universal-editor/authoring.md#context-menu) n’affiche plus de chevron permettant d’accéder aux actions.

## Autres améliorations {#other-improvements}

* S’il existe une définition de modèle/filtre/composant, elle est récupérée lors du passage d’une application à une autre dans l’éditeur.
* La suppression d’une image ne laisse plus de balises d’image vides lors de l’utilisation de DA comme serveur principal.
* Les classes dans les blocs sont désormais correctement gérées lors de l’utilisation de DA comme serveur principal.
* L’API Open enregistre désormais correctement les ressources distantes en tant qu’objets .

## Rupture du changement {#breaking-change}

* Toutes les extensions doivent être mises à jour sur `@adobe/uix-guest` >= `1.1.7` pour améliorer la stabilité.
