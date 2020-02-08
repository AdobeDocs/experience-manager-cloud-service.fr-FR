---
title: Votre boîte de réception
description: Gestion de vos tâches à l’aide de la boîte de réception
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Votre boîte de réception {#your-inbox}

Vous pouvez recevoir des notifications de différentes zones d’AEM, y compris des processus et des projets. Par exemple, vous pouvez recevoir des notifications concernant :

* Tâches :
   * These can also be created at various points within the AEM UI, for example, under **Projects**.
   * These can be the product of a workflow **Create Task** or **Create Project Task** step.
* Les workflows :
   * Éléments de travail représentant les actions que vous devez effectuer sur le contenu de la page
      * These are the product of workflow **Participant** steps.
   * Éléments d’échec, pour permettre aux administrateurs de relancer l’étape d’échec

Vous recevez ces notifications dans votre propre boîte de réception où vous pouvez les visualiser et effectuer des actions.

>[!NOTE]
>
>Pour plus d’informations sur les types d’élément, voir aussi :
>
>* [Projets](/help/sites-cloud/authoring/projects/overview.md)
>* [Projets – Utilisation des tâches](/help/sites-cloud/authoring/projects/tasks.md)
>* [Workflows](/help/sites-cloud/authoring/workflows/overview.md)


## Boîte de réception dans l’en-tête {#inbox-in-the-header}

Dans les deux consoles, le nombre actuel d’éléments présents dans votre boîte de réception est indiqué dans l’en-tête. Vous pouvez également ouvrir l’indicateur pour accéder rapidement aux pages nécessitant une ou plusieurs opérations ou pour accéder à la boîte de réception :

![Présentation de la boîte de réception dans l’en-tête](/help/sites-cloud/authoring/assets/inbox-header.png)

>[!NOTE]
>
>Certaines opérations sont également répertoriées en [mode Carte de la ressource appropriée](/help/sites-cloud/authoring/getting-started/basic-handling.md#card-view).

## Ouverture de la boîte de réception {#opening-the-inbox}

Pour ouvrir la boîte de réception des notifications AEM :

1. Cliquez/appuyez sur l’indicateur dans la barre d’outils.

1. Sélectionnez **Afficher tout**. La **boîte de réception AEM** s’ouvre. La boîte de réception affiche les éléments des workflows, des projets et des tâches.
1. Le mode par défaut est le [mode Liste](#inbox-list-view), mais vous pouvez également basculer vers le [mode Calendrier](#inbox-calendar-view). Cette opération s’effectue à l’aide du sélecteur d’affichage (barre d’outils, en haut à droite).

   For both views you can also define [View Settings](#inbox-view-settings). The options available are dependent on the current view.

   ![Paramètres de la vue Boîte de réception](/help/sites-cloud/authoring/assets/inbox-view-settings.png)

>[!NOTE]
>
>The Inbox operates as a console, so use [Global Navigation](/help/sites-cloud/authoring/getting-started/basic-handling.md#global-navigation) or [Search](/help/sites-cloud/authoring/getting-started/search.md) to navigate to another location when you are finished.

### Boîte de réception – Mode Liste {#inbox-list-view}

Cette vue répertorie tous les éléments, ainsi que les informations pertinentes :

![Affichage de la liste des boîtes de réception](/help/sites-cloud/authoring/assets/inbox-list-view.png)

### Boîte de réception – Mode Calendrier {#inbox-calendar-view}

Cet affichage présente les éléments en fonction de leur position dans le calendrier :

![Affichage du calendrier des boîtes de réception](/help/sites-cloud/authoring/assets/inbox-calendar-view.png)

Vous pouvez :

* Select a specific view: **Timeline**, **Column**, **List**
* Specify the tasks to display according to **Schedule**: **All**, **Planned**, **In Progress**, **Due Soon**, **Past Due**
* Recherche d’informations plus détaillées sur un élément
* Sélectionnez une plage de dates pour mettre la vue au point :

![Période d’affichage du calendrier de réception](/help/sites-cloud/authoring/assets/inbox-calendar-range.png)

### Boîte de réception – Paramètres d’affichage {#inbox-view-settings}

Vous pouvez définir des paramètres d’affichage pour les deux modes (Liste et Calendrier) :

* **Mode Calendrier**

   Pour le **mode Calendrier**, vous pouvez configurer les paramètres suivants :

   * **Regrouper par**
   * **Planification** ou **Aucun**
   * **Taille des cartes** 
   ![Paramètres d’affichage du calendrier de réception](/help/sites-cloud/authoring/assets/inbox-calendar-settings.png)

* **Mode Liste**

   Pour le **mode Liste**, vous pouvez configurer le mécanisme de tri :

   * **Tri par**
   * **Ordre de tri**
   ![Paramètres d’affichage de la liste des entrées](/help/sites-cloud/authoring/assets/inbox-list-settings.png)

   Vous pouvez également déléguer votre calendrier à d&#39;autres fins, demander la délégation d&#39;autres utilisateurs et gérer vos délégations.

   ![Paramètres de délégation de la vue Liste des entrées](/help/sites-cloud/authoring/assets/inbox-delegation.png)

## Action sur un élément {#taking-action-on-an-item}

1. Pour agir sur un élément, sélectionnez la miniature de l’élément souhaité. Les icônes des actions applicables à cet élément apparaissent dans la barre d’outils :

   ![Sélectionner un élément de boîte de réception](/help/sites-cloud/authoring/assets/inbox-select-item.png)

   Les actions disponibles varient selon l’élément et incluent les opérations suivantes :

   * **Terminer** l’action
   * **Déléguer** un élément
   * **Ouvrez** un élément, selon le type d’élément que cette action peut :

      * Afficher les propriétés de l’élément
      * Ouvrez un tableau de bord ou un assistant approprié pour une action ultérieure.
      * Ouvrir la documentation connexe
   * **Revenir** à une étape précédente
   * Afficher la charge utile pour un workflow
   * Créer un projet à partir de l’élément
   >[!NOTE]
   >
   >Pour plus d’informations, voir :
   >
   >* Éléments de workflow –[Participation aux workflows](/help/sites-cloud/authoring/workflows/participating.md)


1. En fonction de l’élément sélectionné, une action sera lancée, par exemple :

   * Une boîte de dialogue correspondant à l’opération s’ouvre
   * Un assistant d&#39;action va démarrer
   * Une page de documentation s’ouvre.
   For example, **Delegate** will open a dialog:

   ![Déléguer la tâche de boîte de réception](/help/sites-cloud/authoring/assets/inbox-assign-task.png)

   Selon qu’une boîte de dialogue, une page de documentation ou un assistant a été ouvert, vous pouvez :

   * Confirmez l’action appropriée, par exemple réaffecter.
   * Annuler l’action
   * Sélectionnez la flèche arrière pour revenir à la boîte de réception. Par exemple, si un assistant d’action ou une page de documentation a été ouvert, vous pouvez revenir à la boîte de réception.


## Création d’une tâche {#creating-a-task}

Vous pouvez créer des tâches directement à partir de la boîte de réception :

1. Sélectionnez **Créer**, puis **Tâche**.
1. Complete the necessary fields in the **Basic** and **Advanced** tabs (only the **Title** is mandatory, all others are optional):

   * **De base**:

      * **Titre**
      * **Projet**
      * **Cessionnaire**
      * **Contenu**, similaire à Payload, il s’agit d’une référence de la tâche à un emplacement du référentiel.
      * **Description**
      * **Priorité de la tâche**
      * **Date de début**
      * **Échéance**
   ![Tâche d’ajout de boîte de réception](/help/sites-cloud/authoring/assets/inbox-create-task.png)

   * **Avancé**

      * **Nom**: il sera utilisé pour former l’URL et, s’il est vide, il sera basé sur le **Titre**.
   ![Options avancées de la tâche d’ajout de boîte de réception](/help/sites-cloud/authoring/assets/inbox-add-task-advanced.png)

1. Sélectionnez **Envoyer**.

## Création d’un projet {#creating-a-project}

Pour certaines tâches, vous pouvez créer un [projet](/help/sites-cloud/authoring/projects/overview.md) basé sur cette tâche :

1. Sélectionnez la tâche appropriée en appuyant/cliquant sur la miniature.

   >[!NOTE]
   >
   >Only tasks created using the **Create** option of the **Inbox** can be used to create a project.
   >
   >Les tâches (issues d’un processus) ne peuvent pas être utilisées pour créer un projet.

1. Sélectionnez **Créer un projet** dans la barre d’outils pour ouvrir l’assistant.
1. Sélectionnez le modèle approprié, puis **Suivant**.
1. Spécifiez les propriétés requises :

   * **De base**

      * **Titre**
      * **Description**
      * **Date de début**
      * **Échéance**
      * **Utilisateur** et rôle
   * **Avancé**

      * **Nom**
   >[!NOTE]
   >
   >Pour plus d’informations, voir [Création d’un projet](/help/sites-cloud/authoring/projects/managing.md#creating-a-project).

1. Sélectionnez **Créer** pour confirmer l’action.

## Filtrage des éléments dans la boîte de réception AEM {#filtering-items-in-the-aem-inbox}

Vous pouvez filtrer les éléments répertoriés :

1. Ouvrez la **boîte de réception AEM**.

1. Ouvrez le sélecteur de filtre :

   ![Recherche dans les boîtes de réception](/help/sites-cloud/authoring/assets/inbox-search.png)

1. Vous pouvez filtrer les éléments répertoriés selon une plage de critères, dont beaucoup peuvent être affinés.Par exemple :

   ![Filtre de recherche de boîte de réception](/help/sites-cloud/authoring/assets/inbox-search-filter.png)

   >[!NOTE]
   >
   >En [mode Liste](#inbox-list-view), vous pouvez également configurer l’ordre de tri dans les [paramètres d’affichage](#inbox-view-settings).
