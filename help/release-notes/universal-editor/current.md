---
title: Notes de mise à jour du 13 novembre 2024 de l’éditeur universel
description: Voici les notes de mise à jour de la version du 13 novembre 2024 de l’éditeur universel.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 98795cab471470442cf5c424a67ce2846cfe85dc
workflow-type: ht
source-wordcount: '370'
ht-degree: 100%

---


# Notes de mise à jour du 13 novembre 2024 de l’éditeur universel {#release-notes}

Voici les notes de mise à jour de la version du 13 novembre 2024 de l’éditeur universel.

>[!TIP]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de mise à jour actuelle d’Adobe Experience Manager as a Cloud Service.

## Nouveautés {#what-is-new}

* **Option de nouvel essai en cas de délai d’expiration CORS :** avec la [version 2024.09.26,](/help/release-notes/universal-editor/2024/2024-09-26.md) un panneau d’erreur a été introduit lorsque l’éditeur ne parvient pas à établir de connexion avec la page chargée, évitant ainsi les états de chargement interminables.
   * Dans cette version, l’éditeur réessaye automatiquement, et une fois la connexion établie, la modification peut reprendre.
   * Cela est particulièrement utile pour les pages dont l’initialisation peut prendre plus d’une minute, ce qui correspond au délai d’expiration.
* **Améliorations de l’extensibilité pour les équipes de développement :** l’éditeur universel prend désormais en charge la diffusion d’événements vers les extensions, permettant aux personnes chargées du développement de s’abonner aux [événements.](/help/implementing/universal-editor/events.md)
   * Elles peuvent ainsi [réagir aux événements de l’éditeur dans leurs extensions personnalisées.](/help/implementing/universal-editor/customizing.md#extending)
* **Sélection de composants persistants :** les composants sélectionnés dans l’éditeur resteront désormais actifs même après l’actualisation du navigateur.
   * Les utilisateurs et les utilisatrices peuvent ainsi poursuivre leur travail sans interruption de contexte lors du rechargement de la page.
* **Liens rapides localisés :** la section **Liens rapides** de l’écran d’accueil propose désormais des liens localisés vers la documentation, permettant aux utilisateurs et aux utilisatrices d’accéder facilement aux guides pertinents selon leurs préférences linguistiques.
* **ID de la demande pour le débogage avancé :** les notifications d’erreur incluent désormais un **ID de la demande** dans la section des détails, qui est en corrélation avec l’élément `x-request-id header`.
   * Cette fonctionnalité facilite le suivi et le diagnostic des problèmes par les équipes d’ingénierie d’Adobe, en permettant de faire correspondre ces erreurs aux journaux internes.

## Autres améliorations {#other-improvements}

* **Correction de la longueur des libellés de l’arborescence de contenu :** résolution du problème de coupure des libellés trop longs dans le panneau **Arborescence de contenu.**
   * Ainsi, les poignées de glisser-déposer sont toujours visibles pour la réorganisation du contenu.
* **Correction des longs libellés de propriétés :** résolution d’un bug qui faisait que les longs libellés de champs dans le panneau **Propriétés** empiétaient sur les informations de validation des champs.
* **Défilement horizontal dans le panneau des propriétés :** correction d’un problème causant un défilement horizontal pour les éléments larges dans le panneau **Propriétés**.
* **Correction de la barre d’outils inactive lors des notifications :** la barre d’outils supérieure d’**Adobe Experience Cloud** est désormais pleinement fonctionnelle lors de l’affichage des notifications [toast](https://spectrum.adobe.com/page/toast/).
* **Amélioration de la stabilité :** ajout de seuils d’erreur pour gérer les valeurs inattendues, évitant le blocage de l’interface d’utilisation en cas de défaillance d’un programme de rendu ou de validation unique, et renforçant ainsi sa robustesse.
