---
title: Notes de mise à jour de l’éditeur universel version 2054.01.16
description: Il s’agit des notes de mise à jour de la version 2025.01.16 de l’éditeur universel.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 77%

---


# Notes de mise à jour de l’éditeur universel version 2025.01.16 {#release-notes}

Il s’agit des notes de mise à jour de la version du 16 janvier 2025 de l’éditeur universel.

>[!TIP]
>
>Pour consulter les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service, consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Nouveautés {#what-is-new}

* **Obsolescence de la bibliothèque CORS &lt; 3.0.0** - Pour assurer la compatibilité future et améliorer la sécurité, l’éditeur universel prend désormais exclusivement en charge la version 3.0.0 ou ultérieure de la
  bibliothèque `@Adobe Express/universal-editor-cors`.
   * La bibliothèque est désormais uniquement diffusée via [`universal-editor-service.adobe.io/cors.js`](http://universal-editor-service.adobe.io/cors.js).
   * Une notification d’obsolescence s’affiche lors de l’ouverture d’une page qui utilise des versions plus anciennes de la bibliothèque CORS, invitant ainsi à effectuer la mise à jour.
* **Point d’extension de la page de destination** - [Un nouveau point d’extension](/help/implementing/universal-editor/customizing.md#extending) a été introduit pour que les extensions s’affichent dans le rail latéral de la page de destination de l’éditeur universel.
   * L’équipe de développement peut désormais spécifier si les extensions s’appliquent à l’éditeur, à la page de destination ou aux deux, offrant ainsi une plus grande personnalisation et davantage de convivialité.

## Autres améliorations {#other-improvements}

* **Correction d’URL non valides dans les éléments récents de la page de destination** - Un problème était résolu où les URL affichées dans la liste « Récents » de la page de destination de l’éditeur universel étaient rompues.
* **Synchronisation des thèmes dans Unified Shell** - L’éditeur universel synchronise désormais dynamiquement le thème avec les paramètres Unified Shell du système et ajuste automatiquement les modes clair et sombre.
   * Cela garantit une apparence visuelle cohérente sur les micro-frontends, y compris les sélecteurs de fragments et de ressources.
