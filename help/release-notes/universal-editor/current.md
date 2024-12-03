---
title: Notes de mise à jour de l’éditeur universel version 2024.12.02
description: Il s’agit des notes de mise à jour de la version 2024.12.02 de l’éditeur universel.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 2aae8c63358680758e4f5324f38dea1bc2c47155
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 16%

---


# Notes de mise à jour de l’éditeur universel version 2024.12.02 {#release-notes}

Il s’agit des notes de mise à jour de la version du 2 décembre 2024 d’Universal Editor.

>[!TIP]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de mise à jour actuelle d’Adobe Experience Manager as a Cloud Service.

## Nouveautés {#what-is-new}

* **Navigation au clavier de l’arborescence de contenu** : [L’arborescence de contenu,](/help/sites-cloud/authoring/universal-editor/navigation.md#content-tree-mode) disponible dans le panneau latéral, est désormais entièrement accessible via le clavier.
   * Les auteurs peuvent naviguer et interagir avec les éléments d’arborescence à l’aide des commandes de clavier standard, en respectant les [instructions WCAG 2.1](/help/sites-cloud/authoring/page-editor/accessible-content.md) pour l’accessibilité.
   * Cette amélioration garantit que tous les éléments interactifs de l’arborescence sont utilisables par le clavier, ce qui améliore l’inclusion pour les utilisateurs qui dépendent de la navigation au clavier.
* **Désélection des éléments modifiables** : les auteurs peuvent désormais désélectionner les éléments modifiables précédemment sélectionnés sur la page.
   * Cela permet d’éviter les distractions lorsque les auteurs souhaitent afficher la page sans bordures de sélection actives.
* **Sélecteur de fragments** : sur les instances AEM as a Cloud Service, les références aux fragments ouvrent désormais le sélecteur de fragments en tant que sélecteur de contenu, offrant ainsi des fonctionnalités améliorées telles que l’obéissance aux modèles de fragments de contenu autorisés, la recherche de fragments de contenu et une expérience globale améliorée.
   * Cela s’aligne sur les autres interfaces utilisateur d’Adobe et améliore la cohérence.
   * [Pour les environnements AEM 6.5,](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction) le sélecteur de contenu existant reste en cours d’utilisation.
* **Description du conteneur** : [Le composant de conteneur](/help/implementing/universal-editor/field-types.md#container) utilisé dans le [panneau Propriétés,](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-panel-properties-rail) pour référencer le contenu, prend désormais en charge un attribut de description, affiché au-dessus des champs du conteneur.
   * Cet ajout renforce la clarté en fournissant aux auteurs un contexte sur les champs regroupés qu’ils modifient.

## Autres améliorations {#other-improvements}

* **Synchronisation des champs de texte enrichi** : la synchronisation du contenu brut et rendu dans les champs de texte enrichi du panneau des propriétés a été améliorée, ce qui permet de résoudre les problèmes liés aux projets Edge Delivery Services où le contenu de texte enrichi et la représentation générée peuvent différer.
* **Événements de mode d’édition** : l’éditeur universel émet désormais de manière fiable des événements de mode d’édition, y compris après le rechargement d’applications distantes.
