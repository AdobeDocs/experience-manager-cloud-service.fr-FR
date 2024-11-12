---
title: Notes de mise à jour d’Universal Editor 2024.11.12
description: Il s’agit des notes de mise à jour de la version 2024.11.12 d’Universal Editor.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 03ccad00e689052ada8cca976d6c385be01d3cc9
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 5%

---


# Notes de mise à jour d’Universal Editor 2024.11.12 {#release-notes}

Il s’agit des notes de mise à jour de la version d’Universal Editor du 12 novembre 2024.

>[!TIP]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de mise à jour actuelle d’Adobe Experience Manager as a Cloud Service.

## Nouveautés {#what-is-new}

* **Option de reprise sur délai d’expiration CORS :** Avec la [version 2024.09.26,](/help/release-notes/universal-editor/2024/2024-09-26.md), un panneau d’erreur a été introduit lorsque l’éditeur n’a pas pu établir de connexion à la page chargée, ce qui a empêché des états de chargement interminables.
   * Avec cette version, l’éditeur continue automatiquement de réessayer et une fois la connexion établie, l’édition peut reprendre.
   * Cela s’avère particulièrement utile pour les pages dont l’initialisation peut prendre plus d’une minute.
* **Améliorations de l’extensibilité pour les développeurs :** Universal Editor prend désormais en charge la diffusion d’événements vers des extensions, ce qui permet aux développeurs d’extensions de s’abonner à [events.](/help/implementing/universal-editor/events.md)
   * Cela permet aux développeurs de [réagir aux événements de l’éditeur dans leurs extensions personnalisées.](/help/implementing/universal-editor/customizing.md#extending)
* **Sélection de composants persistants :** Les composants sélectionnés dans l’éditeur persisteront désormais même après l’actualisation du navigateur.
   * Cela permet aux utilisateurs de continuer à travailler sans perdre leur contexte lors du rechargement de la page.
* **Liens rapides localisés :** La section **Liens rapides** de l’écran d’accueil fournit désormais des liens localisés vers la documentation, ce qui permet aux utilisateurs d’accéder facilement aux guides pertinents en fonction de leurs préférences linguistiques.
* **ID de demande pour le débogage avancé :** Les notifications d’erreur incluent désormais un **ID de demande** dans la section des détails, qui est en corrélation avec `x-request-id header`.
   * Cela facilite le suivi et le diagnostic des problèmes par les équipes d’ingénierie d’Adobe en faisant correspondre ces erreurs aux logs internes.

## Autres améliorations {#other-improvements}

* **Étiquettes d’arborescence de contenu longue fixe :** Correction d’un problème en raison duquel les libellés longs du panneau **Arborescence de contenu** étaient coupés.
   * Ainsi, les poignées de glisser-déposer sont toujours visibles pour la réorganisation du contenu.
* **Correction des libellés de propriétés longues :** Correction d’un bogue en raison duquel les libellés de champs longs dans le panneau **Propriétés** se chevauchaient avec les informations de validation de champ.
* **Défilement horizontal dans le panneau Propriétés :** Correction d’un problème en raison duquel des éléments larges dans le panneau **Propriétés** provoquaient un défilement horizontal
* **Barre d’outils inactive fixe pendant les notifications :** La barre d’outils **Adobe Experience Cloud** supérieure est désormais entièrement fonctionnelle lorsque des notifications [toast](https://spectrum.adobe.com/page/toast/) sont affichées.
* **Stabilité améliorée :** Ajout de limites d’erreur pour gérer les valeurs inattendues, empêchant l’ensemble de l’interface utilisateur de se bloquer lorsqu’un seul moteur de rendu ou validateur échoue, ce qui améliore la robustesse
