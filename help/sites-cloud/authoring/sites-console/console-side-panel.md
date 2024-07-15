---
title: Panneau latéral de la console Sites
description: Découvrez comment utiliser le panneau latéral dans la console Sites AEM pour mieux comprendre et parcourir votre contenu.
exl-id: 7f2571d6-b847-4cce-8e94-94ba0d2e04a5
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '827'
ht-degree: 23%

---

# Panneau latéral de la console Sites {#side-panel}

Découvrez comment utiliser le panneau latéral dans la console AEM **Sites** pour mieux comprendre et parcourir votre contenu.

## Orientation {#orientation}

Le panneau latéral est fermé par défaut lorsque vous entrez dans la console **Sites**. Ainsi, l’écran est entièrement dédié à votre contenu.

Appuyez ou cliquez sur l’icône **Panneau latéral** dans la barre d’outils de la console **Sites** pour activer le panneau latéral et choisir votre vue du contenu.

* [Contenu uniquement](#content-only)
* [Arborescence de contenu](#content-tree)
* [Chronologie](#timeline)
* [Références](#references)
* [Site](#site)
* [Filtrer](#filter)
* [Configurer Analytics](#setup-analytics)

![Vues du panneau latéral de la console Sites](assets/sites-console-side-panel-views.png)

La vue actuelle sélectionnée est indiquée par une coche bleue dans la liste déroulante et l’icône du panneau latéral dans la barre d’outils est mise à jour avec le nom de la vue sélectionnée.

## Contenu uniquement {#content-only}

Cette vue du panneau latéral la désactive, c’est-à-dire qu’elle n’affiche que le contenu de votre site.

>[!TIP]
>
>Utilisez le raccourci clavier accent/coche arrière grave `´` pour passer à la vue Contenu uniquement du panneau latéral.

## Arborescence de contenu {#content-tree}

Cette vue du panneau latéral affiche votre contenu dans une hiérarchie d’arborescence. L’arborescence de contenu peut être utilisée pour parcourir rapidement la hiérarchie du site dans le panneau latéral et afficher de nombreuses informations sur les pages du dossier actif.

![L’arborescence de contenu du panneau latéral](assets/console-side-panel-content-tree.png)

Un chevron pointant vers la droite en regard d’un élément de l’arborescence indique un noeud qui peut être développé pour afficher ses enfants. Appuyez ou cliquez sur le chevron pour afficher les enfants.

La console affiche le contenu de l’élément actuellement sélectionné dans l’arborescence de contenu.

À l’aide du panneau latéral de l’arborescence de contenu associé à un mode Liste ou Carte, vous pouvez facilement voir la structure hiérarchique du projet, naviguer facilement dans la structure de contenu à l’aide du panneau latéral de l’arborescence de contenu et afficher des informations détaillées sur la page en mode Liste.

>[!TIP]
>
>* Utilisez le raccourci clavier `Alt+1` pour passer à l’arborescence de contenu du panneau latéral.
>* Après avoir sélectionné une entrée dans la hiérarchie, vous pouvez naviguer rapidement dans la hiérarchie à l’aide des touches directionnelles.
>* Reportez-vous à la section [Raccourcis clavier](/help/sites-cloud/authoring/sites-console/keyboard-shortcuts.md) pour plus d’informations.

## La chronologie {#timeline}

La chronologie peut être utilisée pour afficher les événements qui ont affecté la ressource sélectionnée. Vous pouvez également l’utiliser pour démarrer certains événements tels que des workflows ou des versions.

![Détails de la chronologie](/help/sites-cloud/authoring/assets/timeline-detail.png)

Le panneau latéral **Chronologie** vous permet d’afficher divers événements liés à un élément sélectionné comme types dans une liste déroulante :

* Commentaires
* [Annotations](/help/sites-cloud/authoring/page-editor/annotations.md)
* [Activités](/help/sites-cloud/authoring/personalization/activities.md)
* [Lancements](/help/sites-cloud/authoring/launches/overview.md)
* [Versions](/help/sites-cloud/authoring/sites-console/page-versions.md)
* [Workflows](/help/sites-cloud/authoring/workflows/overview.md)
   * Notez qu’aucune information ne sera affichée pour les workflows transitoires, car aucune information historique n’est enregistrée pour ceux-ci.<!--With the exception of [transient workflows](/help/sites-developing/workflows.md#transient-workflows) as no history information is saved for these-->
* Tout afficher

De plus, vous pouvez ajouter/afficher des commentaires sur l’élément sélectionné à l’aide de la zone **Commentaire** affichée en bas de la liste des événements. Saisissez un commentaire suivi de `Return` pour enregistrer le commentaire. Vous pouvez l’afficher en sélectionnant **Commentaires** ou **Tout afficher**.

Dans la console **Sites** , vous pouvez également accéder à des fonctionnalités supplémentaires par le biais du bouton représentant des points de suspension en regard du champ **Commentaire** .

* [enregistrer une version ;](/help/sites-cloud/authoring/sites-console/page-versions.md)
* [démarrer un workflow.](/help/sites-cloud/authoring/workflows/applying.md)

![Champ de commentaire de la console Sites](assets/sites-console-comment-ellipsis.png)

>[!TIP]
>
>* Utilisez le raccourci clavier `Alt+2` pour basculer vers la vue de chronologie du panneau latéral.
>* Reportez-vous à la section [Raccourcis clavier](/help/sites-cloud/authoring/sites-console/keyboard-shortcuts.md) pour plus d’informations.

## Références {#references}

La vue **Références** affiche une liste des types de références de ou depuis vers la ressource sélectionnée dans la console.

![Détails des références](assets/console-side-panel-references-detail.png)

Sélectionnez le type de référence approprié pour en savoir plus. Dans certains cas, d’autres actions sont disponibles lorsque vous sélectionnez une référence particulière, notamment :

* **Liens entrants**, fournit une liste de pages qui référencent la page, ainsi qu’un accès direct à **Modifier** l’une de ces pages lorsque vous sélectionnez un lien spécifique.
   * Cela peut uniquement afficher les liens statiques, et non les liens générés dynamiquement, tels que depuis le composant Liste .
* [Lancements](/help/sites-cloud/authoring/launches/overview.md) donne accès aux lancements associés.
* [Live Copies](/help/sites-cloud/administering/msm/overview.md) affiche les chemins d’accès à toutes les Live Copies basées sur la ressource sélectionnée.
* Le [plan directeur](/help/sites-cloud/administering/msm/best-practices.md) fournit des détails et la possibilité de diverses actions.
* [Copies de langue](/help/sites-cloud/administering/translation/managing-projects.md#creating-translation-projects-using-the-references-panel), fournit des détails et diverses actions

## Site {#site}

La vue **Site** du panneau latéral affiche les détails des sites [ créés à l’aide d’un modèle de site.](/help/sites-cloud/administering/site-creation/create-site.md)

![Panneau du site](assets/console-side-panel-site-paenl.png)

Consultez le document [Utilisation du panneau du site pour gérer le thème de votre site](/help/sites-cloud/administering/site-creation/site-rail.md) pour plus d’informations sur la manière dont vous pouvez utiliser le panneau pour gérer le [thème de votre site.](/help/sites-cloud/administering/site-creation/site-themes.md).

Si vous n’avez pas encore configuré le pipeline frontal pour activer la création de site basée sur un thème, le panneau latéral offre cette option.

![Option pour activer le pipeline front-end dans le panneau latéral](assets/sites-console-side-panel-site.png)

>[!TIP]
>
>Vous trouverez une description de bout en bout du processus de création d’un site à partir d’un modèle et de personnalisation de son thème dans le [Parcours de création rapide de site.](/help/journey-sites/quick-site/overview.md)

## Filtrer {#filter}

Le panneau **Filtre** est similaire à la [ fonction de recherche](/help/sites-cloud/authoring/search.md) avec les filtres d’emplacement appropriés déjà définis, ce qui vous permet de filtrer davantage le contenu que vous souhaitez afficher.

![Exemple de filtre](assets/console-side-panel-filter.png)

Contrairement aux autres vues du panneau latéral, pour passer à une autre vue, appuyez ou cliquez sur le `X` dans le champ de recherche.

## Configurer Analytics {#setup-analytics}

Cette vue vous permet de configurer rapidement Adobe Analytics pour un site sélectionné.

![Configuration d’Analytics](assets/sites-console-side-panel-setup-analytics.png)
