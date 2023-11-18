---
title: Votre boîte de réception
description: Découvrez comment utiliser les notifications qui arrivent dans votre boîte de réception pour gérer vos tâches.
exl-id: 37d0cf43-192f-4a50-b174-42d7dced3b63
source-git-commit: 6bb7b2d056d501d83cf227adb239f7f40f87d0ce
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 94%

---

# Votre boîte de réception {#your-inbox}

Vous pouvez recevoir des notifications de diverses sections d’AEM, y compris des workflows et des projets. Ces notifications peuvent par exemple concerner les éléments suivants :

* Tâches :
   * Elles peuvent également être créées à différents endroits de l’interface utilisateur d’AEM (par exemple, sous **Projets**).
   * Elles peuvent être générées par l’étape **Créer une tâche** ou **Créer une tâche de projet** d’un workflow.
* Workflows :
   * Éléments de travail correspondant à des opérations que vous devez exécuter sur le contenu de la page.
      * Ils sont générés par l’étape **Participant** du workflow.
   * Éléments d’échec, pour permettre aux administrateurs de relancer l’étape qui a échoué.

Vous recevez ces notifications dans votre propre boîte de réception, où vous pouvez les afficher et agir sur la base de celles-ci.

>[!NOTE]
>
>Pour plus d’informations sur les types d’éléments, consultez les sections suivantes :
>
>* [Projets](/help/sites-cloud/authoring/projects/overview.md)
>* [Projets – Utilisation des Tâches](/help/sites-cloud/authoring/projects/tasks.md)
>* [Workflows](/help/sites-cloud/authoring/workflows/overview.md)

## Boîte de réception dans l’en-tête {#inbox-in-the-header}

Dans les deux consoles, le nombre actuel d’éléments présents dans votre boîte de réception est indiqué dans l’en-tête. L’indicateur peut également être ouvert pour permettre un accès rapide aux pages nécessitant des actions ou un accès à la boîte de réception :

![Aperçu de la boîte de réception dans l’en-tête](/help/sites-cloud/authoring/assets/inbox-header.png)

>[!NOTE]
>
>Certaines opérations sont également répertoriées en [mode Carte de la ressource appropriée](/help/sites-cloud/authoring/getting-started/basic-handling.md#card-view).

## Ouverture de la boîte de réception {#opening-the-inbox}

Pour ouvrir la boîte de réception des notifications AEM :

1. Sélectionnez l’indicateur dans la barre d’outils.

1. Sélectionnez **Afficher tout**. La variable **Boîte de réception AEM** s’ouvre. La boîte de réception affiche les éléments des workflows, des projets et des tâches.
1. La vue par défaut est [Liste](#inbox-list-view), mais vous pouvez également passer à la vue [Calendrier](#inbox-calendar-view). Pour ce faire, utilisez le sélecteur de vue (barre d’outils, en haut à droite).

   Vous pouvez également définir les [paramètres d’affichage](#inbox-view-settings) pour ces deux modes ; les options disponibles dépendent du mode actif.

   ![Paramètres d’affichage de la boîte de réception](/help/sites-cloud/authoring/assets/inbox-view-settings.png)

>[!NOTE]
>
>La boîte de réception fonctionne comme une console. Vous pouvez ainsi utiliser la [navigation globale](/help/sites-cloud/authoring/getting-started/basic-handling.md#global-navigation) ou la fonction de [recherche](/help/sites-cloud/authoring/getting-started/search.md) pour accéder à un autre emplacement lorsque vous avez terminé.

### Boîte de réception – Vue Liste {#inbox-list-view}

Ce mode affiche tous les éléments, ainsi que des informations importantes :

![Boîte de réception – Vue Liste](/help/sites-cloud/authoring/assets/inbox-list-view.png)

### Boîte de réception – Vue Calendrier {#inbox-calendar-view}

Ce mode affiche les éléments en fonction de leur position dans le calendrier :

![Boîte de réception – Mode Calendrier](/help/sites-cloud/authoring/assets/inbox-calendar-view.png)

Vous pouvez effectuer les actions suivantes :

* sélectionner un mode d’affichage spécifique (**Chronologie**, **Colonnes**, **Liste**) ;
* spécifier les tâches selon **Planification** : **Tous**, **Planifiés**, **En cours**, **Échéance proche** et **Échéance dépassée** ;
* descendre dans la hiérarchie pour obtenir plus d’informations sur un élément ;
* sélectionner une période sur laquelle cibler la vue :

![Boîte de réception – Période d’affichage du calendrier](/help/sites-cloud/authoring/assets/inbox-calendar-range.png)

### Boîte de réception – Paramètres d’affichage {#inbox-view-settings}

Pour les deux vues (Liste et Calendrier), vous pouvez définir des paramètres :

* **Vue Calendrier**

  Pour la **vue Calendrier**, vous pouvez configurer les éléments suivants :

   * **Regrouper par**
   * **Planification** ou **Aucun**
   * **Taille des cartes**

  ![Boîte de réception – Paramètres d’affichage du calendrier](/help/sites-cloud/authoring/assets/inbox-calendar-settings.png)

* **Vue Liste**

  Pour la **vue Liste**, vous pouvez configurer le mécanisme de tri :

   * **Tri à**
   * **Ordre de tri**

  ![Boîte de réception – Paramètres de la vue Liste](/help/sites-cloud/authoring/assets/inbox-list-settings.png)

  Vous pouvez également déléguer votre calendrier à d’autres utilisateurs et utilisatrices, demander la délégation à d’autres utilisateurs et utilisatrices ou encore gérer vos délégations.

  ![Boîte de réception – Paramètres de délégation de la vue Liste](/help/sites-cloud/authoring/assets/inbox-delegation.png)

## Action sur un élément {#taking-action-on-an-item}

>[!NOTE]
>
>Bien qu’il soit possible de sélectionner plusieurs éléments, des actions ne peuvent être entreprises que sur un seul élément à la fois.

1. Pour agir sur un élément, sélectionnez la miniature de l’élément approprié. Les icônes des actions applicables à cet élément s’affichent dans la barre d’outils :

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
   >Pour plus d’informations, consultez les sections suivantes :
   >
   >* Éléments de workflow – [Participation aux workflows](/help/sites-cloud/authoring/workflows/participating.md)

2. Une action démarre en fonction de l’élément sélectionné, par exemple :

   * Une boîte de dialogue correspondant à l’action s’ouvre ;
   * Un assistant d&#39;action démarre ;
   * Une page de documentation s’ouvre

   Par exemple : **Déléguer** ouvre une boîte de dialogue :

   ![Déléguer la tâche de boîte de réception](/help/sites-cloud/authoring/assets/inbox-assign-task.png)

   Selon qu’une boîte de dialogue, une page de documentation ou un assistant a été ouvert, vous pouvez :

   * Confirmez l’action appropriée, par exemple en la réaffectant.
   * Annuler l’action
   * Sélectionner la flèche vers l’arrière pour revenir à la boîte de réception ; par exemple, si une page de documentation ou un assistant d’action a été ouvert, vous pouvez revenir à la boîte de réception.

## Création d’une tâche {#creating-a-task}

Vous pouvez créer des tâches à partir de la boîte de réception :

1. Sélectionner **Créer**, puis **Tâche**.
1. Renseignez les champs nécessaires dans les onglets **De base** et **Avancé** (seul le champ **Titre** est obligatoire, tous les autres sont facultatifs) :

   * **De base** :

      * **Titre**
      * **Projet**
      * **Cessionnaire**
      * **Contenu** : similaire à Charge utile ; il s’agit d’une référence de la tâche à un emplacement dans le référentiel
      * **Description**
      * **Priorité de la tâche**
      * **Date de début**
      * **Date d’échéance**

   ![Tâche d’ajout de la boîte de réception](/help/sites-cloud/authoring/assets/inbox-create-task.png)

   * **Avancé**

      * **Nom** : utilisé pour former l’URL, et s’il est vide, le nom est basé sur le champ **titre**.

   ![Options avancées de la tâche d’ajout de boîte de réception](/help/sites-cloud/authoring/assets/inbox-add-task-advanced.png)

1. Sélectionnez **Envoyer**.

## Création d’un projet {#creating-a-project}

Pour certaines tâches, vous pouvez créer un [projet](/help/sites-cloud/authoring/projects/overview.md) en fonction de cette tâche :

1. Sélectionnez la tâche appropriée en appuyant/cliquant sur la miniature.

   >[!NOTE]
   >
   >Seules les tâches créées à l’aide de l’option **Créer** de la **boîte de réception** peuvent être utilisées pour créer un projet.
   >
   >Les éléments de travail (d’un workflow) ne peuvent pas être utilisés pour créer un projet.

1. Sélectionnez **Créer un projet** depuis la barre d’outils pour ouvrir l’assistant.
1. Sélectionnez le modèle requis, puis **Suivant** :
1. Spécifiez les propriétés requises :

   * **De base**

      * **Titre**
      * **Description**
      * **Date de début**
      * **Date d’échéance**
      * **Utilisateur** et rôle

   * **Avancé**

      * **Nom**

   >[!NOTE]
   >
   >Voir [Création d’un projet](/help/sites-cloud/authoring/projects/managing.md#creating-a-project) pour obtenir des informations complètes.

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
   >Dans la vue [Liste](#inbox-list-view), vous pouvez également configurer l’ordre de tri dans les [paramètres d’affichage](#inbox-view-settings).
