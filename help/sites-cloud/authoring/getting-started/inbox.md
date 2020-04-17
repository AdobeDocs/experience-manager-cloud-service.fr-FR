---
title: Votre boîte de réception
description: Gestion de vos tâches à l’aide de la boîte de réception
translation-type: ht
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Votre boîte de réception   {#your-inbox}

Vous pouvez recevoir des notifications de diverses sections d’AEM, y compris des workflows et des projets. Ces notifications peuvent par exemple concerner les éléments suivants :

* Tâches :
   * Elles peuvent également être créées à différents endroits de l’interface utilisateur d’AEM (par exemple, sous **Projets**).
   * Elles peuvent être générées par l’étape **Créer une tâche** ou **Créer une tâche de projet** d’un workflow.
* Workflows :
   * Éléments de travail correspondant à des opérations que vous devez exécuter sur le contenu de la page.
      * Ils sont générés par l’étape **Participant** du workflow.
   * Éléments d’échec, pour permettre aux administrateurs de relancer l’étape qui a échoué.

Vous recevez ces notifications dans votre propre boîte de réception où vous pouvez les visualiser et effectuer des actions.

>[!NOTE]
>
>Pour plus d’informations sur les types d’éléments, voir aussi :
>
>* [Projets](/help/sites-cloud/authoring/projects/overview.md)
>* [Projets – Utilisation des tâches](/help/sites-cloud/authoring/projects/tasks.md)
>* [Workflows](/help/sites-cloud/authoring/workflows/overview.md)


## Boîte de réception dans l’en-tête {#inbox-in-the-header}

Dans les deux consoles, le nombre actuel d’éléments présents dans votre boîte de réception est indiqué dans l’en-tête. Vous pouvez également ouvrir l’indicateur pour accéder rapidement aux pages nécessitant une ou plusieurs opérations ou pour accéder à la boîte de réception :

![Aperçu de la boîte de réception dans l’en-tête](/help/sites-cloud/authoring/assets/inbox-header.png)

>[!NOTE]
>
>Certaines opérations sont également répertoriées en [mode Carte de la ressource appropriée](/help/sites-cloud/authoring/getting-started/basic-handling.md#card-view).

## Ouverture de la boîte de réception   {#opening-the-inbox}

Pour ouvrir la boîte de réception des notifications AEM :

1. Cliquez/appuyez sur l’indicateur dans la barre d’outils.

1. Sélectionnez **Afficher tout**. La **boîte de réception AEM** s’ouvre. La boîte de réception affiche les éléments des workflows, des projets et des tâches.
1. Le mode par défaut est le [mode Liste](#inbox-list-view), mais vous pouvez également basculer vers le [mode Calendrier](#inbox-calendar-view). Cette opération s’effectue à l’aide du sélecteur d’affichage (barre d’outils, en haut à droite).

   Vous pouvez également définir les [paramètres d’affichage](#inbox-view-settings) pour ces deux modes ; les options disponibles dépendent du mode actif.

   ![Paramètres d’affichage de la boîte de réception](/help/sites-cloud/authoring/assets/inbox-view-settings.png)

>[!NOTE]
>
>La boîte de réception fonctionne comme une console. Vous pouvez ainsi utiliser la [navigation globale](/help/sites-cloud/authoring/getting-started/basic-handling.md#global-navigation) ou la fonction de [recherche](/help/sites-cloud/authoring/getting-started/search.md) pour accéder à un autre emplacement lorsque vous avez terminé.

### Boîte de réception – Mode Liste {#inbox-list-view}

Ce mode affiche tous les éléments, ainsi que des informations importantes :

![Boîte de réception – Mode Liste](/help/sites-cloud/authoring/assets/inbox-list-view.png)

### Boîte de réception – Mode Calendrier {#inbox-calendar-view}

Ce mode affiche les éléments en fonction de leur position dans le calendrier :

![Boîte de réception – Mode Calendrier](/help/sites-cloud/authoring/assets/inbox-calendar-view.png)

Vous pouvez :

* sélectionner un mode d’affichage spécifique (**Chronologie**, **Colonnes**, **Liste**) ;
* spécifier les tâches selon **Planification** : **Tous**, **Planifiés**, **En cours**, **Échéance proche** et **Échéance dépassée** ;
* descendre dans la hiérarchie pour obtenir plus d’informations sur un élément ;
* sélectionner une période sur laquelle cibler la vue :

![Boîte de réception – Période d’affichage du calendrier](/help/sites-cloud/authoring/assets/inbox-calendar-range.png)

### Boîte de réception – Paramètres d’affichage {#inbox-view-settings}

Vous pouvez définir des paramètres d’affichage pour les deux modes (Liste et Calendrier) :

* **Mode Calendrier**

   Pour le **mode Calendrier**, vous pouvez configurer les paramètres suivants :

   * **Regrouper par**
   * **Planification** ou **Aucun**
   * **Taille des cartes**
   ![Boîte de réception – Paramètres d’affichage du calendrier](/help/sites-cloud/authoring/assets/inbox-calendar-settings.png)

* **Mode Liste**

   Pour le **mode Liste**, vous pouvez configurer le mécanisme de tri :

   * **Tri par**
   * **Ordre de tri**
   ![Boîte de réception – Paramètres du mode Liste](/help/sites-cloud/authoring/assets/inbox-list-settings.png)

   Vous pouvez également déléguer votre calendrier à d’autres fins, demander la délégation à d’autres utilisateurs ou encore gérer vos délégations.

   ![Boîte de réception – Paramètres de délégation du mode Liste](/help/sites-cloud/authoring/assets/inbox-delegation.png)

## Action sur un élément {#taking-action-on-an-item}

1. Pour agir sur un élément, sélectionnez la miniature de l’élément souhaité. Les icônes des actions applicables à cet élément apparaissent dans la barre d’outils :

   ![Sélection d’un élément de la boîte de réception](/help/sites-cloud/authoring/assets/inbox-select-item.png)

   Les actions disponibles varient selon l’élément et incluent les opérations suivantes :

   * **Terminer** l’action
   * **Déléguer** un élément
   * **Ouvrir** un élément ; selon le type d’élément, cette action permet d’effectuer les opérations suivantes :

      * Afficher les propriétés de l’élément
      * Ouvrir un tableau de bord ou un assistant pour effectuer d’autres actions
      * Ouvrir la documentation associée
   * **Revenir** à une étape précédente
   * Afficher la charge utile pour un workflow
   * Créer un projet à partir de l’élément
   >[!NOTE]
   >
   >Pour plus d’informations, voir :
   >
   >* Éléments de workflow – [Participation aux workflows](/help/sites-cloud/authoring/workflows/participating.md)


1. Une action démarre en fonction de l’élément sélectionné, par exemple :

   * Une boîte de dialogue correspondant à l’opération s’ouvre.
   * Un assistant d’action démarre.
   * Une page de documentation s’ouvre.
   Par exemple, **Déléguer** ouvre une boîte de dialogue :

   ![Déléguer la tâche de boîte de réception](/help/sites-cloud/authoring/assets/inbox-assign-task.png)

   Selon qu’une boîte de dialogue, une page de documentation ou un assistant a été ouvert, vous pouvez :

   * Confirmer l’action appropriée, par exemple Réaffecter.
   * Annuler l’action
   * Sélectionner la flèche vers l’arrière pour revenir à la boîte de réception ; par exemple, si une page de documentation ou un assistant d’action a été ouvert, vous pouvez revenir à la boîte de réception.


## Création d’une tâche {#creating-a-task}

Vous pouvez créer des tâches directement à partir de la boîte de réception :

1. Sélectionnez **Créer**, puis **Tâche**.
1. Renseignez les champs nécessaires dans les onglets **De base** et **Avancé** (seul le champ **Titre** est obligatoire, tous les autres sont facultatifs) :

   * **De base** :

      * **Titre**
      * **Projet**
      * **Cessionnaire**
      * **Contenu** : similaire à Charge utile ; il s’agit d’une référence de la tâche à un emplacement dans le référentiel
      * **Description**
      * **Priorité de la tâche**
      * **Date de début**
      * **Échéance**
   ![Tâche d’ajout de la boîte de réception](/help/sites-cloud/authoring/assets/inbox-create-task.png)

   * **Avancé**

      * **Nom** : ce champ est utilisé pour former l’URL ; s’il est vide, le nom est basé sur le champ **Titre**.
   ![Options avancées de la tâche d’ajout de boîte de réception](/help/sites-cloud/authoring/assets/inbox-add-task-advanced.png)

1. Sélectionnez **Envoyer**.

## Création d’un projet {#creating-a-project}

Pour certaines tâches, vous pouvez créer un [projet](/help/sites-cloud/authoring/projects/overview.md) basé sur cette tâche :

1. Sélectionnez la tâche appropriée en appuyant/cliquant sur la miniature.

   >[!NOTE]
   >
   >Seules les tâches créées à l’aide de l’option **Créer** de la **boîte de réception** peuvent être utilisées pour créer un projet.
   >
   >Les éléments de travail (d’un workflow) ne peuvent pas être utilisés pour créer un projet.

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

1. Vous pouvez filtrer les éléments répertoriés en fonction d’une série de critères, pouvant pour la plupart être affinés. Par exemple :

   ![Filtre de recherche dans les boîtes de réception](/help/sites-cloud/authoring/assets/inbox-search-filter.png)

   >[!NOTE]
   >
   >En [mode Liste](#inbox-view-settings), vous pouvez également configurer l’ordre de tri dans les [paramètres d’affichage](#inbox-list-view).
