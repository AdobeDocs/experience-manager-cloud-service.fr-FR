---
title: Notes de mise à jour de l’éditeur universel version 2025.03.10
description: Il s’agit des notes de mise à jour de la version 2025.03.10 de l’éditeur universel.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: b3c98f5e41dbc5e1714d0ed418a317199c735b73
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 23%

---


# Notes de mise à jour de l’éditeur universel version 2025.03.10 {#release-notes}

Voici les notes de mise à jour de la version du 10 mars 2025 de l’éditeur universel.

>[!TIP]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service.

## Nouveautés {#what-is-new}

* **Déplacement de composants :** [le déplacement de composants entre des conteneurs](/help/sites-cloud/authoring/universal-editor/authoring.md#reordering-components) observe désormais le filtre de composant du conteneur cible.
   * Il n’est plus nécessaire de mettre en place la même [définition de filtre](/help/implementing/universal-editor/filtering.md) pour les conteneurs cible et de destination afin de déplacer le composant entre les conteneurs.
* **Pages verrouillées :** le service d’éditeur universel observe le [statut de verrouillage d’une page](/help/sites-cloud/authoring/sites-console/managing-pages.md#locking-a-page) et écrit uniquement sur les pages qui ne sont pas verrouillées ou qui sont verrouillées par l’utilisateur ou l’utilisatrice.

## Autres améliorations {#other-improvements}

* Des correctifs ont été apportés pour corriger la validation de la zone de travail découplée.

## Obsolescence {#deprecation}

* La bibliothèque `universal-editor-cors` fournie via npm ou `https://unviersal-editor-service.experiencecloud.live/corslib/*` ne doit plus être utilisée.
   * Une balise de script pointant vers `https://universal-editor-service.adobe.io/cors.js` doit être utilisée à la place.
   * Consultez la [Présentation de l’éditeur universel pour les développeurs AEM](/help/implementing/universal-editor/developer-overview.md) pour plus d’informations sur la manière d’instrumenter correctement votre page pour l’utiliser avec l’éditeur universel.
   * Un message d’obsolescence s’affiche une fois par jour si la mauvaise méthode est utilisée.
