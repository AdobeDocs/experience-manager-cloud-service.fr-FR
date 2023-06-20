---
title: Utilisation des versions de page
description: Création, comparaison et restauration de versions d’une page
exl-id: 33d8e43c-594d-4bba-9631-b2c42a1e910f
source-git-commit: 635f4c990c27a7646d97ebd08b453c71133f01b3
workflow-type: tm+mt
source-wordcount: '1502'
ht-degree: 68%

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

## Création d’une version {#creating-a-new-version}

Vous pouvez créer une version de votre ressource depuis :

* le [rail de la frise chronologique](#creating-a-new-version-timeline),
* l’option [Créer](#creating-a-new-version-create-with-a-selected-resource) (lorsqu’une ressource est sélectionnée)

### Créer une version - Frise chronologique {#creating-a-new-version-timeline}

1. Accédez à la page pour laquelle créer une version.
1. Sélectionnez la page en [mode de sélection](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Ouvrez le rail **Frise chronologique**.
1. Cliquez ou appuyez sur les points de suspension près du champ de commentaire pour afficher les options :

   ![Versions dans le rail de la frise chronologique](/help/sites-cloud/authoring/assets/versions-timeline-rail.png)

1. Sélectionner **Enregistrer comme version**.
1. Saisissez un **Libellé** et **Commentaire** si nécessaire.

   ![Ajout d’un libellé pour une version](/help/sites-cloud/authoring/assets/versions-add-label.png)

1. Confirmez la nouvelle version avec l’option **Créer**.

   Les informations de la chronologie sont mises à jour afin d’indiquer la nouvelle version.

### Création d’une version – Création avec une ressource sélectionnée {#creating-a-new-version-create-with-a-selected-resource}

1. Accédez à la page pour laquelle créer une version.
1. Sélectionnez la page en [mode de sélection](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Sélectionnez la **Créer** dans la barre d’outils.
1. La même boîte de dialogue s’ouvre. Vous pouvez saisir un **libellé** et un **commentaire** si nécessaire.
1. Confirmez la nouvelle version avec l’option **Créer**.

La chronologie s’ouvre avec les informations mises à jour pour indiquer la nouvelle version.

## Rétablissement de versions {#reinstating-versions}

Une fois que vous avez créé une version de votre page, différentes méthodes permettent de rétablir une version antérieure :

* l’option **Revenir à cette version** depuis le rail [Chronologie](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline)

  Rétablissez une version antérieure d’une page sélectionnée.

* les options **Restaurer** de la [barre d’outils d’actions](/help/sites-cloud/authoring/getting-started/basic-handling.md#actions-toolbar) en haut de la page

   * **Restaurer la version**

     Rétablissez des versions de pages spécifiées dans le dossier actuellement sélectionné ; cela peut également inclure la restauration de pages qui ont été supprimées précédemment.

   * **Restaurer l’arborescence**

     Rétablissez une version d’une arborescence complète à une date et une heure spécifiées ; cela peut inclure des pages qui ont été supprimées précédemment.

>[!NOTE]
>
>Lors du rétablissement d’une page, la version créée fait partie d’une nouvelle branche.
>
>Illustration :
>
>1. Créez des versions d’une page.
>1. Les libellés et les noms de noeud de version initiaux sont 1.0, 1.1, 1.2, etc.
>1. Rétablissez la première version, soit 1.0.
>1. Créez à nouveau de nouvelles versions.
>1. Les libellés et noms de noeud générés sont désormais 1.0.0, 1.0.1, 1.0.2, etc.

### Rétablissement d’une version {#revert-to-a-version}

Pour **rétablir** la version précédente d’une page sélectionnée :

1. Naviguez pour afficher la page pour laquelle restaurer une ancienne version.
1. Sélectionnez la page en [mode de sélection](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Ouvrez la colonne **Chronologie**, puis sélectionnez **Afficher tout** ou **Versions**. Les versions de la page sélectionnée sont répertoriées.
1. Sélectionnez la version à restaurer. Les options possibles s’affichent :

   ![Revenir à cette version](/help/sites-cloud/authoring/assets/versions-revert.png)

1. Sélectionnez **Revenir à cette version**. La version sélectionnée est restaurée et les informations de la chronologie sont mises à jour.

### Restaurer la version {#restore-version}

Cette méthode permet de rétablir des versions de pages spécifiées dans le dossier actuel ; cela peut également inclure la restauration de pages qui ont été supprimées précédemment :

1. Recherchez et [sélectionnez](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) le dossier souhaité.

1. Sélectionnez **Restaurer**, puis **Restaurer la version** dans la [barre d’outils d’actions](/help/sites-cloud/authoring/getting-started/basic-handling.md#actions-toolbar) en haut de la page.

   >[!NOTE]
   >
   >Si :
   >
   >* vous avez sélectionné une seule page, qui n’a jamais eu de page enfant,
   >* ou aucune des pages du dossier ne comporte de version,
   >
   >L’affichage devient vide car il n’existe aucune version applicable.

1. Les versions disponibles sont répertoriées :

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

Cette méthode permet de restaurer une version d’une arborescence à une date et une heure spécifiées ; cela peut inclure des pages qui ont été supprimées précédemment :

1. Recherchez et [sélectionnez](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) le dossier souhaité.

1. Sélectionnez **Restaurer**, puis **Restaurer l’arborescence** dans la [barre d’outils d’actions](/help/sites-cloud/authoring/getting-started/basic-handling.md#actions-toolbar) en haut de la page. La dernière version de l’arborescence s’affiche :

   ![Restaurer l’arborescence](/help/sites-cloud/authoring/assets/versions-restore-tree-01.png)

1. Utilisez le sélecteur de date et d’heure dans **Dernières versions en date** pour sélectionner une autre version de l’arborescence : celle qui doit être restaurée.

1. Définissez l’indicateur **Pages non versionnées préservées** selon les besoins :

   * Si cette option est principale (sélectionnée), les pages non versionnées sont conservées et ne sont pas affectées par la restauration.

   * Si cette option est inactive (non sélectionnée), les pages non versionnées sont supprimées, car elles n’existaient pas dans l’arborescence versionnée.

1. Sélectionnez **Restaurer** pour la version sélectionnée de l’arborescence à restaurer comme version *actuelle*.

## Aperçu d’une version {#previewing-a-version}

Vous pouvez prévisualiser une version spécifique :

1. Accédez à la page à comparer.
1. Sélectionnez la page en [mode de sélection](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Ouvrez la colonne **Chronologie**, puis sélectionnez **Afficher tout** ou **Versions**.
1. Les versions de page sont répertoriées. Sélectionnez la version à prévisualiser :

   ![Aperçu de la version](/help/sites-cloud/authoring/assets/versions-revert.png)

1. Sélectionnez **Aperçu**. La page s’affiche dans un nouvel onglet.

   >[!CAUTION]
   >
   >Si une page a été déplacée, vous ne pouvez plus effectuer d’aperçu sur les versions antérieures au déplacement.
   >
   >Si vous rencontrez des problèmes avec un aperçu, vérifiez la variable [Chronologie](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline) pour la page afin de voir si la page a été déplacée.

## Comparaison d’une ancienne version avec la page actuelle {#comparing-a-version-with-current-page}

Pour comparer une version précédente à la page active :

1. Accédez à la page à comparer.
1. Sélectionnez la page en [mode de sélection](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Ouvrez la colonne **Chronologie**, puis sélectionnez **Afficher tout** ou **Versions**.
1. Les versions de page sont répertoriées. Sélectionnez la version à comparer :

   ![Comparaison des versions](/help/sites-cloud/authoring/assets/versions-revert.png)

1. Sélectionner **Comparer à actuel**. Le [comparaison des pages](/help/sites-cloud/authoring/features/page-diff.md) s’ouvre et affiche les différences.

## Distorsion du temps Timewarp {#timewarp}

La fonction de distorsion du temps Timewarp permet de simuler l’état *publié* d’une page à des moments spécifiques dans le passé.

>[!TIP]
>
>[Il est également possible d’utiliser la distorsion du temps avec les lancements pour obtenir un aperçu du futur.](/help/sites-cloud/authoring/launches/preview.md)

Comme la création de contenu est un processus continu et collaboratif, l’objectif de Timewarp est de permettre aux auteurs de suivre au fil du temps le site web publié afin qu’ils puissent comprendre comment le contenu a changé. Cette fonction utilise les versions de page pour déterminer l’état de l’environnement de publication.

Pour ce faire :

* Le système recherche la version de page principale à l’heure sélectionnée.
* Cela signifie que la version affichée a été créée/activée. *before* point dans le temps sélectionné dans Timewarp.
* Si vous accédez à une page qui a été supprimée, celle-ci est également affichée, à condition toutefois que les anciennes versions de la page soient toujours disponibles dans le référentiel.
* Si aucune version publiée n’a été trouvée, la fonction Timewarp revient à l’état actuel de la page dans l’environnement de création (et ce, afin d’éviter une erreur/page 404, ce qui rendrait impossible toute poursuite de la navigation).

### Utilisation de Timewarp {#using-timewarp}

Timewarp est une [mode](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) de l’éditeur de page. Pour le démarrer, il vous suffit de le basculer comme vous le feriez pour tout autre mode.

1. Démarrez l’éditeur de la page sur laquelle vous souhaitez démarrer Timewarp, puis sélectionnez **Timewarp** dans la sélection de mode.

   ![Mode Timewarp](/help/sites-cloud/authoring/assets/versions-timewarp-mode.png)

1. Dans la boîte de dialogue, définissez une date et une heure cibles, puis cliquez ou appuyez sur **Définir la date**. Si vous ne sélectionnez pas d’heure, l’heure actuelle est utilisée par défaut.

   ![Date cible du mode Timewarp](/help/sites-cloud/authoring/assets/versions-timewarp-target.png)

1. La page s’affiche en fonction du jeu de dates. Le mode Timewarp est indiqué à partir de la barre d’état bleue située en haut de la fenêtre. Utilisez les liens de la barre d’état pour sélectionner une nouvelle date cible ou quitter le mode Timewarp.

   ![En mode Timewarp](/help/sites-cloud/authoring/assets/versions-timewarp.png)

### Limites de la distorsion du temps {#timewarp-limitations}

Timewarp s’efforce de reproduire au mieux une page à un moment donné. Toutefois, en raison de la complexité de la création continue de contenu dans AEM, cela n’est pas toujours possible. Ces restrictions doivent être prises en compte lors de l’utilisation de Timewarp.

* **Timewarp fonctionne sur la base de pages publiées** : toutes les fonctionnalités de Timewarp ne sont disponibles que si vous avez publié la page précédemment. Dans le cas contraire, Timewarp affiche la page en cours dans l’environnement de création.
* **Timewarp utilise des versions de page** - Si vous accédez à une page qui a été supprimée du référentiel, elle est correctement rendue si d’anciennes versions de la page sont toujours disponibles dans le référentiel.
* **Les versions supprimées affectent Timewarp** : si des versions sont supprimées du référentiel, Timewarp n’est pas en mesure d’afficher la vue correcte.
* **Timewarp est en lecture seule** : vous ne pouvez pas modifier l’ancienne version de la page. Elle est disponible uniquement à des fins d’affichage. Si vous souhaitez restaurer l’ancienne version, vous devrez procéder manuellement à l’aide de la fonction [Restaurer](#revert-to-a-version).
* **Timewarp est basé uniquement sur le contenu de page** : si des éléments destinés au rendu du site web (tels que du code, des feuilles css, des ressources/images, etc.) ont été modifiés, la vue sera différente de ce qu’elle était initialement, étant donné que ces éléments n’ont pas de suivi de version dans le référentiel.

>[!CAUTION]
>
>Timewarp est un outil conçu pour aider les auteurs à comprendre et à créer du contenu. Il ne s’agit pas d’un journal d’audit et il n’est pas destiné à des fins juridiques.
