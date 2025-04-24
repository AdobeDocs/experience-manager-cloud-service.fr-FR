---
title: Utilisation des versions de page
description: Découvrez comment créer, comparer et restaurer des versions de vos pages dans AEM.
exl-id: 33d8e43c-594d-4bba-9631-b2c42a1e910f
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: b39c455c9bd4b50eb3777cd1a4bdbada48786d62
workflow-type: tm+mt
source-wordcount: '1574'
ht-degree: 93%

---

# Utilisation des versions de page {#working-with-page-versions}

Le contrôle de version permet de créer un « instantané » d’une page à un moment donné. Avec le contrôle de version, vous pouvez effectuer les opérations suivantes :

* Créez une version d’une page.
* Rétablir une version précédente d’une ou de plusieurs pages pour :
   * Annuler les modifications apportées aux pages.
   * Restaurer les pages qui ont été supprimées.
   * Restaurer une arborescence (à une date et une heure spécifiées).
* Prévisualiser une version.
* Comparer la version actuelle d’une page à une version précédente.
   * Les différences dans le texte et les images sont mises en évidence.
* La distorsion du temps utilise les versions de pages pour déterminer l’état de l’environnement de publication.

>[!NOTE]
>
>Seul le contenu est versionné dans le référentiel AEM. Les ressources dynamiques telles que le code, le CSS et le JavaScript ne sont pas versionnées.
>
>* Lors de l’affichage des versions, le contenu est affiché avec le code, le CSS et le JavaScript actuels du référentiel.
>* Lors de la restauration de versions, seul le contenu est restauré et le code, CSS et JavaScript actuels du référentiel lui sont appliqués.

## Création d’une version {#creating-a-new-version}

Vous pouvez créer une version de votre ressource depuis :

* le [rail de la frise chronologique](#creating-a-new-version-timeline),
* l’option [Créer](#creating-a-new-version-create-with-a-selected-resource) (lorsqu’une ressource est sélectionnée)

### Créer une version - Frise chronologique {#creating-a-new-version-timeline}

1. Accédez à la page pour laquelle créer une version.
1. Sélectionnez la page en [mode de sélection](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources).
1. Ouvrez le rail **Frise chronologique**.
1. Sélectionnez les points de suspension en regard du champ de commentaire pour afficher les options :

   ![Versions dans le rail de la frise chronologique](/help/sites-cloud/authoring/assets/versions-timeline-rail.png)

1. Sélectionnez **Enregistrer comme version**.
1. Saisissez un **Libellé** et un **Commentaire** si nécessaire.

   ![Ajout d’un libellé pour une version](/help/sites-cloud/authoring/assets/versions-add-label.png)

1. Confirmez la nouvelle version avec l’option **Créer**.

   Les informations dans la frise chronologique sont mises à jour pour indiquer la nouvelle version.

### Création d’une version – Création avec une ressource sélectionnée {#creating-a-new-version-create-with-a-selected-resource}

1. Accédez à la page pour laquelle créer une version.
1. Sélectionnez la page en [mode de sélection](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources).
1. Sélectionnez l’option **Créer** dans la barre d’outils.
1. La même boîte de dialogue s’ouvre. Vous pouvez saisir un **libellé** et un **commentaire** si nécessaire.
1. Confirmez la nouvelle version avec l’option **Créer**.

La frise chronologique s’ouvre avec les informations mises à jour afin d’indiquer la nouvelle version.

## Rétablissement de versions {#reinstating-versions}

Une fois que vous avez créé une version de votre page, différentes méthodes permettent de rétablir une version antérieure :

* l’option **Revenir à cette version** depuis le rail [Chronologie](/help/sites-cloud/authoring/basic-handling.md#timeline)

  Rétablissez une version antérieure d’une page sélectionnée.

* les options **Restaurer** de la [barre d’outils d’actions](/help/sites-cloud/authoring/basic-handling.md#actions-toolbar) en haut de la page

   * **Restaurer la version**

     Rétablissez des versions de pages spécifiées dans le dossier actuellement sélectionné. Elle peut également inclure la restauration de pages qui ont été supprimées précédemment.

   * **Restaurer l’arborescence**

     Rétablissez une version d’une arborescence entière à une date et une heure spécifiées. Elle peut également inclure des pages qui ont été supprimées précédemment.

>[!NOTE]
>
>Lors du rétablissement d’une page, la version créée fait partie d’une nouvelle branche.
>
>Illustration :
>
>1. Créez des versions d’une page.
>1. Les libellés et les noms de nœud de version initiaux sont 1.0, 1.1, 1.2, etc.
>1. Rétablissez la première version, c&#39;est-à-dire 1.0.
>1. Créez à nouveau de nouvelles versions.
>1. Les libellés et noms de nœud générés sont désormais 1.0.0, 1.0.1, 1.0.2, etc.

### Rétablissement d’une version {#revert-to-a-version}

Pour **rétablir** la version précédente d’une page sélectionnée :

1. Naviguez pour afficher la page pour laquelle restaurer une ancienne version.
1. Sélectionnez la page en [mode de sélection](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources).
1. Ouvrez la colonne **Chronologie**, puis sélectionnez **Afficher tout** ou **Versions**. Les versions de la page sélectionnée sont répertoriées.
1. Sélectionnez la version à restaurer. Les options possibles s’affichent :

   ![Revenir à cette version](/help/sites-cloud/authoring/assets/versions-revert.png)

1. Sélectionnez **Revenir à cette version**. La version sélectionnée est restaurée et les informations de la chronologie sont mises à jour.

### Restaurer la version {#restore-version}

Cette méthode peut être utilisée pour restaurer des versions de pages spécifiées dans le dossier actif. Elle peut également être appliquée à la restauration de pages qui ont été supprimées précédemment :

1. Recherchez et [sélectionnez](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources) le dossier souhaité.

1. Sélectionnez **Restaurer**, puis **Restaurer la version** dans la [barre d’outils d’actions](/help/sites-cloud/authoring/basic-handling.md#actions-toolbar) en haut de la page.

   >[!NOTE]
   >
   >Si vous avez :
   >
   >* sélectionné une seule page, qui n’a jamais eu de page enfant,
   >* ou aucune des pages du dossier ne comporte de version,
   >
   >L’affichage devient vide car il n’existe aucune version applicable.

1. Les versions disponibles sont répertoriées :

   ![Restaurer la version : liste de toutes les pages dans le dossier](/help/sites-cloud/authoring/assets/versions-restore-version-01.png)

1. Pour une page spécifique, utilisez le sélecteur déroulant sous **RESTAURER VERS LA VERSION** pour sélectionner la version requise pour cette page.

   ![Restaurer la version – Sélectionner la version](/help/sites-cloud/authoring/assets/versions-restore-version-02.png)

1. Dans l’affichage principal, sélectionnez la page à restaurer :

   ![Restaurer la version – Sélectionner la page](/help/sites-cloud/authoring/assets/versions-restore-version-03.png)

1. Sélectionnez **Restaurer** pour la version sélectionnée de la page sélectionnée à restaurer en tant que version actuelle.

>[!NOTE]
>
>L’ordre dans lequel vous sélectionnez une page requise et la version associée est interchangeable.

### Restaurer l’arborescence {#restore-tree}

Cette méthode peut être utilisée pour restaurer une version d’une arborescence à une date et une heure spécifiées. Elle peut être appliquée à des pages qui ont été supprimées précédemment :

1. Recherchez et [sélectionnez](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources) le dossier souhaité.

1. Sélectionnez **Restaurer**, puis **Restaurer l’arborescence** dans la [barre d’outils d’actions](/help/sites-cloud/authoring/basic-handling.md#actions-toolbar) en haut de la page. La dernière version de l’arborescence apparaît :

   ![Restaurer l’arborescence](/help/sites-cloud/authoring/assets/versions-restore-tree-01.png)

1. Utilisez le sélecteur de date et d’heure dans **Dernières versions en date** pour sélectionner une autre version de l’arborescence : celle qui doit être restaurée.

1. Définissez l’indicateur **Pages non versionnées préservées** selon les besoins :

   * Si cette option est active (sélectionnée), toute page non versionnée est conservée et n’est pas affectée par la restauration.

   * Si elle est inactive (non sélectionnée), toute page non versionnée est supprimée, car elle n’existait pas dans l’arborescence versionnée.

1. Sélectionnez **Restaurer** pour la version sélectionnée de l’arborescence à restaurer comme version *actuelle*.

## Aperçu d’une version {#previewing-a-version}

Vous pouvez prévisualiser une version spécifique :

1. Accédez à la page que vous souhaitez comparer.
1. Sélectionnez la page en [mode de sélection](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources).
1. Ouvrez la colonne **Chronologie**, puis sélectionnez **Afficher tout** ou **Versions**.
1. Les versions de page sont répertoriées. Sélectionnez la version que vous souhaitez prévisualiser :

   ![Aperçu de la version](/help/sites-cloud/authoring/assets/versions-revert.png)

1. Sélectionnez **Aperçu**. La page s’affiche dans un nouvel onglet.

   >[!CAUTION]
   >
   >Si une page a été déplacée, vous ne pouvez plus afficher l’aperçu des versions antérieures au déplacement.
   >
   >Si vous rencontrez des problèmes avec un aperçu, vérifiez la variable [Frise chronologique](/help/sites-cloud/authoring/basic-handling.md#timeline) de la page afin de voir si la page a été déplacée.

## Comparaison d’une ancienne version avec la page actuelle {#comparing-a-version-with-current-page}

Pour comparer une version précédente à la page actuelle :

1. Accédez à la page que vous souhaitez comparer.
1. Sélectionnez la page en [mode de sélection](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources).
1. Ouvrez la colonne **Chronologie**, puis sélectionnez **Afficher tout** ou **Versions**.
1. Les versions de page sont répertoriées. Sélectionnez la version que vous souhaitez comparer :

   ![Comparaison des versions](/help/sites-cloud/authoring/assets/versions-revert.png)

1. Sélectionner **Comparer avec la version actuelle**. La [comparaison des pages](/help/sites-cloud/authoring/sites-console/page-diff.md) s’ouvre et affiche les différences.

## Distorsion du temps Timewarp {#timewarp}

La fonction de distorsion du temps Timewarp permet de simuler l’état *publié* d’une page à des moments spécifiques dans le passé.

>[!TIP]
>
>[Il est également possible d’utiliser la fonction Timewarp avec les lancements pour obtenir un aperçu du futur](/help/sites-cloud/authoring/launches/preview.md).

La création de contenu étant un processus continu et collaboratif, l’objectif de Timewarp est de permettre aux auteurs et autrices d’effectuer le suivi d’un site web publié au fil du temps afin qu’ils comprennent l’évolution du contenu. Cette fonctionnalité utilise les versions de page pour déterminer l’état de l’environnement de publication.

Pour utiliser cette fonctionnalité :

* Le système recherche la version de page qui était active à l’heure sélectionnée.
* Cela signifie que la version affichée a été créée/activée *avant* l’heure sélectionnée dans Timewarp.
* Si vous accédez à une page qui a été supprimée, celle-ci sera également affichée, à condition toutefois que les anciennes versions de la page soient toujours disponibles dans le référentiel.
* Si aucune version publiée n’a été trouvée, la fonction Timewarp revient à l’état actuel de la page dans l’environnement de création (et ce, afin d’éviter une erreur/page 404, ce qui rendrait impossible toute poursuite de la navigation).

### Utilisation de Timewarp {#using-timewarp}

Timewarp est un [mode](/help/sites-cloud/authoring/page-editor/introduction.md#page-modes) de l’éditeur de page. Pour le démarrer, il vous suffit de l’activer comme vous le feriez pour tout autre mode.

1. Démarrez l’éditeur de la page sur laquelle vous souhaitez démarrer Timewarp, puis sélectionnez **Timewarp** dans la sélection de mode.

   ![Mode Timewarp](/help/sites-cloud/authoring/assets/versions-timewarp-mode.png)

1. Dans la boîte de dialogue, définissez une date et une heure cibles, puis cliquez ou appuyez sur **Définir la date**. Si vous ne sélectionnez pas d’heure, l’heure actuelle est utilisée par défaut.

   ![Date cible du mode Timewarp](/help/sites-cloud/authoring/assets/versions-timewarp-target.png)

1. La page s’affiche en fonction de la date définie. Le mode Timewarp est indiqué à partir de la barre d’état bleue située en haut de la fenêtre. Utilisez les liens de la barre d’état pour sélectionner une nouvelle date cible ou quitter le mode Timewarp.

   ![En mode Timewarp](/help/sites-cloud/authoring/assets/versions-timewarp.png)

### Limites de la distorsion du temps {#timewarp-limitations}

Timewarp s’efforce de reproduire au mieux une page à un moment donné. Toutefois, en raison de la complexité de la création continue de contenu dans AEM, cela n’est pas toujours possible. Tenez compte de ces limites lorsque vous utilisez Timewarp.

* **Timewarp fonctionne sur la base de pages publiées** : toutes les fonctionnalités de Timewarp ne sont disponibles que si vous avez publié la page précédemment. Dans le cas contraire, Timewarp affiche la page actuelle dans l’environnement de création.
* **Timewarp utilise des versions de page** : si vous accédez à une page qui a été supprimée du référentiel, elle s’affiche correctement si d’anciennes versions sont toujours disponibles dans le référentiel.
* **Les versions supprimées affectent Timewarp** : si des versions sont supprimées du référentiel, Timewarp n’est pas en mesure d’afficher la vue correcte.
* **Timewarp est en lecture seule** : vous ne pouvez pas modifier l’ancienne version de la page. Elle est disponible uniquement à des fins d’affichage. Si vous souhaitez restaurer l’ancienne version, vous devrez procéder manuellement à l’aide de la fonction [Restaurer](#revert-to-a-version).
* **Timewarp est basé sur le contenu de la page :** si des éléments pour le rendu du site web ont été modifiés (code, css et ressources, par exemple), la vue diffère de celle d’origine. Ces éléments ne sont pas versionnés dans le référentiel.

>[!CAUTION]
>
>Timewarp est un outil conçu pour aider les auteurs à comprendre et à créer du contenu. Il ne s’agit pas d’un journal d’audit et il n’est pas destiné à des fins juridiques.
