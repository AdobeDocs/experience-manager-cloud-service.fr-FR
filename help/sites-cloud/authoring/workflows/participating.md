---
title: Participation aux workflows
description: Les workflows incluent généralement les étapes qu’une personne doit suivre pour réaliser une activité sur une page ou sur une ressource.
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Participation aux workflows {#participating-in-workflows}

Les workflows incluent généralement les étapes qu’une personne doit suivre pour réaliser une activité sur une page ou sur une ressource. Le workflow sélectionne un utilisateur ou un groupe pour qu’il mette en œuvre l’activité en question et attribue un élément de travail à cette personne ou à ce groupe. L’utilisateur reçoit la notification et peut alors réaliser l’action appropriée :

* [Affichage des notifications](#notifications-of-available-workflow-actions)
* [Finalisation d’une étape de participant](#completing-a-participant-step)
* [Délégation d’une étape de participant](#delegating-a-participant-step)
* [Revenir d’une étape de participant en arrière](#performing-step-back-on-a-participant-step)
* [Ouverture d’un élément de workflow pour afficher les détails (et réaliser des actions)](#opening-a-workflow-item-to-view-details-and-take-actions)
* [Affichage de la charge utile de workflow (plusieurs ressources)](#viewing-the-workflow-payload-multiple-resources)

## Notifications d’actions de workflow disponibles {#notifications-of-available-workflow-actions}

Lorsqu’un élément de travail vous est attribué (par exemple, **Approuver le contenu**), différentes alertes et/ou notifications s’affichent :

* Votre indicateur de [notification](/help/sites-cloud/authoring/getting-started/inbox.md) (barre d’outils) sera incrémenté :

   ![Barre d’outils Notification](/help/sites-cloud/authoring/assets/workflows-notifications.png)

* L’élément est répertorié dans votre [boîte de réception](/help/sites-cloud/authoring/getting-started/inbox.md) de notifications :

   ![Notifications dans la boîte de réception](/help/sites-cloud/authoring/assets/workflows-inbox.png)

* Lorsque vous utilisez l’éditeur de page, la barre d’état affiche :
   * Le nom du ou des workflows appliqués à la page ; par exemple, Demander l’activation.
   * Les actions auxquelles l’utilisateur actuel a accès pour l’étape actuelle du workflow ; par exemple, Compléter, Déléguer et Afficher les détails.
   * Le nombre de workflows auxquels la page est soumise. Vous pouvez :
      * utiliser les flèches gauche/droite pour parcourir les informations d’état des différents workflows.
      * cliquer/appuyer sur le nombre pour ouvrir la liste déroulante de tous les workflows applicables, puis sélectionner le worfklow que vous souhaitez afficher dans la barre d’état.
   ![Page avec plusieurs processus](/help/sites-cloud/authoring/assets/workflows-multiple.png)

   >[!NOTE]
   >
   >La barre d’état est uniquement visible pour les utilisateurs disposant de droits de workflow ; par exemple, les membres du groupe `workflow-users`.
   >
   >
   >Les actions s’affichent lorsque l’utilisateur actuel est directement impliqué dans l’étape actuelle du workflow.

* Lorsque la **chronologie** est ouverte pour la ressource, l’étape du workflow s’affiche. Lorsque vous cliquez/appuyez sur la bannière d’avertissement, les actions disponibles sont également affichées :

   ![Flux de travaux dans la chronologie](/help/sites-cloud/authoring/assets/workflows-timeline.png)

### Réalisation d’une étape de participant {#completing-a-participant-step}

Vous pouvez terminer un élément pour permettre au workflow de passer à l’étape suivante.

Pour cette action, vous pouvez indiquer :

* **Étape suivante** : la prochaine étape à suivre ; vous pouvez la sélectionner dans la liste fournie.
* **Commentaire** : si nécessaire

Vous pouvez terminer une étape de participant à partir de :

* [La boîte de réception](#completing-a-participant-step-inbox)
* [Editeur de page](#completing-a-participant-step-page-editor)
* [Chronologie](#completing-a-participant-step-timeline)
* When [opening a workflow item to view details](#opening-a-workflow-item-to-view-details-and-take-actions).

#### Réalisation d’une étape de participant - Boîte de réception {#completing-a-participant-step-inbox}

Utilisez la procédure suivante pour terminer l’élément de tâche :

1. Ouvrez la **[boîte de réception AEM](/help/sites-cloud/authoring/getting-started/inbox.md)**.
1. Sélectionnez l’élément de workflow sur lequel que vous souhaitez agir (appuyez/cliquez sur la miniature).
1. Select **Complete** from the toolbar.
1. La boîte de dialogue **Terminer l’élément de travail** s’ouvre. Select the **Next Step** from the drop down selector and add a **Comment** if required.
1. Use **OK** to complete the step (or the **Cancel** to abort the action).

#### Réalisation d’une étape de participant - Éditeur de page {#completing-a-participant-step-page-editor}

Utilisez la procédure suivante pour terminer l’élément de tâche :

1. Ouvrez la [page à modifier](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#opening-a-page-for-editing).
1. Select **Complete** from the status bar at the top.
1. La boîte de dialogue **Terminer l’élément de travail** s’ouvre. Select the **Next Step** from the drop down selector and add a **Comment** if required.
1. Use **OK** to complete the step (or the **Cancel** to abort the action).

#### Réalisation d’une étape de participant - Chronologie {#completing-a-participant-step-timeline}

Vous pouvez également utiliser la chronologie pour terminer et avancer d’une étape :

1. Select the required page and open **Timeline** (or open **Timeline** and select the page):

   ![Exécution d’une étape](/help/sites-cloud/authoring/assets/workflows-timeline-completing.png)

1. Cliquez/appuyez sur la bannière d’alerte pour afficher les actions disponibles. Sélectionnez l’option **Avancer** :

   ![Avancement de l’étape](/help/sites-cloud/authoring/assets/workflows-timeline-advance.png)

1. Selon le workflow, vous pouvez choisir l’étape suivante :

   ![Sélection de l’étape suivante](/help/sites-cloud/authoring/assets/workflows-next-step.png)

1. Sélectionnez l’option **Avancer** pour confirmer l’action.

### Délégation d’une étape de participant {#delegating-a-participant-step}

Si une étape vous a été affectée, mais que pour une raison quelconque, vous ne pouvez pas vous en charger, vous pouvez la déléguer à un autre utilisateur ou groupe.

Les utilisateurs à qui vous pouvez déléguer une étape dépendent de la personne à qui l’élément de travail a été attribué :

* Si l’élément de travail a été attribué à un groupe, les membres du groupe sont disponibles.
* Si l’élément de travail a été attribué à un groupe puis délégué à un utilisateur, les membres du groupe et le groupe sont disponibles.
* Si l’élément de travail a été attribué à un utilisateur unique, l’élément de travail ne peut pas être délégué.

Pour cette action, vous pouvez indiquer :

* **Utilisateur** : l’utilisateur auquel déléguer ; vous pouvez le sélectionner dans la liste fournie.
* **Commentaire** : si nécessaire

Vous pouvez déléguer une étape de participant à partir de :

* [La boîte de réception](#delegating-a-participant-step-inbox)
* [Editeur de page](#delegating-a-participant-step-page-editor)
* [Chronologie](#delegating-a-participant-step-timeline)
* When [opening a workflow item to view details](#opening-a-workflow-item-to-view-details-and-take-actions).

#### Délégation d’une étape de participant - Boîte de réception {#delegating-a-participant-step-inbox}

Utilisez la procédure suivante pour déléguer un élément de tâche :

1. Ouvrez la **[boîte de réception AEM](/help/sites-cloud/authoring/getting-started/inbox.md)**.
1. Sélectionnez l’élément de workflow sur lequel que vous souhaitez agir (appuyez/cliquez sur la miniature).
1. Select **Delegate** from the toolbar.
1. Une boîte de dialogue s’ouvre. Specify the **User** from the drop down selector (this can also be a group) and add a **Comment** if required.
1. Use **OK** to complete the step (or the **Cancel** to abort the action).

#### Délégation d’une étape de participant - Éditeur de page {#delegating-a-participant-step-page-editor}

Utilisez la procédure suivante pour déléguer un élément de tâche :

1. Ouvrez la [page à modifier](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#opening-a-page-for-editing).
1. Select **Delegate** from the status bar at the top.
1. Une boîte de dialogue s’ouvre. Specify the **User** from the drop down selector (this can also be a group) and add a **Comment** if required.
1. Use **OK** to complete the step (or the **Cancel** to abort the action).

#### Délégation d’une étape de participant - Chronologie {#delegating-a-participant-step-timeline}

Vous pouvez également utiliser la chronologie pour déléguer et/ou attribuer une étape :

1. Select the required page and open **Timeline** (or open **Timeline** and select the page).
1. Cliquez/appuyez sur la bannière d’alerte pour afficher les actions disponibles. Sélectionnez **Changer le cessionnaire** :

   ![Déléguer l’étape](/help/sites-cloud/authoring/assets/workflows-delegate.png)

1. Spécifiez un nouveau cessionnaire :

   ![Modifier le responsable](/help/sites-cloud/authoring/assets/workflows-assignee.png)

1. Select **Assign** to confirm the action.

### Revenir d’une étape de participant en arrière {#performing-step-back-on-a-participant-step}

Si vous vous rendez compte qu’une étape ou qu’une série d’étapes doit être répétée, vous pouvez revenir en arrière. Cela vous permet de sélectionner une étape qui s’est produite plus tôt dans le workflow pour la traiter à nouveau. Le workflow retourne à l’étape spécifiée et poursuit à partir de là.

Pour cette action, vous pouvez indiquer :

* **Étape précédente** : l’étape vers laquelle revenir ; vous pouvez la sélectionner dans la liste fournie.
* **Commentaire** : si nécessaire

Vous pouvez revenir d’une étape de participant en arrière à partir de :

* [La boîte de réception](#performing-step-back-on-a-participant-step-inbox)
* [Editeur de page](#performing-step-back-on-a-participant-step-page-editor)
* [Chronologie](#performing-step-back-on-a-participant-step-timeline)
* When [opening a workflow item to view details](#opening-a-workflow-item-to-view-details-and-take-actions).

#### Revenir d’une étape de participant en arrière - Boîte de réception {#performing-step-back-on-a-participant-step-inbox}

Utilisez la procédure suivante pour revenir en arrière :

1. Ouvrez la **[boîte de réception AEM](/help/sites-cloud/authoring/getting-started/inbox.md)**.
1. Sélectionnez l’élément de workflow sur lequel que vous souhaitez agir (appuyez/cliquez sur la miniature).
1. Select **Step Back** to open the dialog.
1. Définissez l’**étape précédente** et ajoutez un **commentaire** si nécessaire.
1. Use **OK** to complete the step (or the **Cancel** to abort the action).

#### Revenir d’une étape de participant en arrière - Éditeur de page {#performing-step-back-on-a-participant-step-page-editor}

Utilisez la procédure suivante pour revenir en arrière :

1. Ouvrez la [page à modifier](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#opening-a-page-for-editing).
1. Select **Step Back** from the status bar at the top.
1. Définissez l’**étape précédente** et ajoutez un **commentaire** si nécessaire.
1. Use **OK** to complete the step (or the **Cancel** to abort the action).

#### Revenir d’une étape de participant en arrière - Chronologie {#performing-step-back-on-a-participant-step-timeline}

Vous pouvez également utiliser la chronologie pour revenir à une étape précédente et la restaurer :

1. Select the required page and open **Timeline** (or open **Timeline** and select the page).
1. Cliquez/appuyez sur la bannière d’alerte pour afficher les actions disponibles. Sélectionnez **Restaurer** :

   ![Restaurer une étape](/help/sites-cloud/authoring/assets/workflows-roll-back.png)

1. Spécifiez l’étape à laquelle le workflow doit revenir :

   ![Spécifier l’étape](/help/sites-cloud/authoring/assets/workflows-roll-back-step.png)

1. Select **Roll back** to confirm the action.

### Ouverture d’un élément de workflow pour afficher les détails (et réaliser des actions) {#opening-a-workflow-item-to-view-details-and-take-actions}

Affichez les détails de l’élément de travail du workflow et réalisez les actions appropriées.

Les détails de workflow s’affichent dans des onglets, et les actions appropriées sont disponibles dans la barre d’outils :

* **WORKITEM** , onglet :

   ![WORKITEM, onglet](/help/sites-cloud/authoring/assets/workflows-work-item.png)

* **INFO** DE PROCESSUS :

   ![WORKFLOW, panneau](/help/sites-cloud/authoring/assets/workflows-workflow-info.png)

   If Workflow Stages have been configured for the model, you can view the progress according to these: <!--If [Workflow Stages](/help/sites-developing/workflows.md#workflow-stages) have been configured for the model, you can view the progress according to these:-->

   ![Étapes de processus](/help/sites-cloud/authoring/assets/workflows-workflow-stages.png)

* **COMMENTAIRES** , onglet :

   ![COMMENTAIRES, panneau](/help/sites-cloud/authoring/assets/workflows-comments.png)

Vous pouvez ouvrir les détails de l’élément de travail à partir de :

* [La boîte de réception](#performing-step-back-on-a-participant-step-inbox)
* [Editeur de page](#performing-step-back-on-a-participant-step-page-editor)

#### Ouverture des détails de workflow - Boîte de réception {#opening-workflow-details-inbox}

Pour ouvrir un élément de workflow et en afficher les détails :

1. Ouvrez la **[boîte de réception AEM](/help/sites-cloud/authoring/getting-started/inbox.md)**.
1. Sélectionnez l’élément de workflow sur lequel que vous souhaitez agir (appuyez/cliquez sur la miniature).
1. Select **Open** to open the information tabs.
1. Si nécessaire, choisissez l’action appropriée, saisissez les informations et confirmez avec **OK** (ou **Annuler**).
1. Use **Save** or **Cancel** to exit.

#### Ouverture des détails de workflow - Éditeur de page {#opening-workflow-details-page-editor}

Pour ouvrir un élément de workflow et en afficher les détails :

1. Ouvrez la [page à modifier](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#opening-a-page-for-editing).
1. Select **View Details** from the status bar to open the information tabs.
1. Si nécessaire, choisissez l’action appropriée, saisissez les informations et confirmez avec **OK** (ou **Annuler**).
1. Use **Save** or **Cancel** to exit.

### Affichage de la charge utile de workflow (plusieurs ressources) {#viewing-the-workflow-payload-multiple-resources}

Vous pouvez afficher les détails de la charge utile associée à l’instance de workflow. Au départ, les ressources du module sont affichées, puis vous pouvez faire un zoom avant pour afficher les pages individuelles.

Pour afficher la charge utile et les ressources de l’instance de workflow :

1. Ouvrez la **[boîte de réception AEM](/help/sites-cloud/authoring/getting-started/inbox.md)**.
1. Sélectionnez l’élément de workflow sur lequel que vous souhaitez agir (appuyez/cliquez sur la miniature).
1. Select **View Payload** from the toolbar to open the dialog.
   * Un module de workflow étant simplement un ensemble de pointeurs vers les chemins d’accès au sein du référentiel, vous pouvez y ajouter, supprimer ou modifier les entrées pour définir ce qu’il référence. Utilisez le composant **Définition de la ressource** pour ajouter de nouvelles entrées.
1. Les liens peuvent être utilisés pour ouvrir les pages individuelles.
