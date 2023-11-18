---
title: Comment gérer les formulaires, les applications et les tâches dans la boîte de réception AEM ?
description: La boîte de réception AEM vous permet de lancer des processus orientés formulaire via l’envoi d’applications et de tâches de gestion.
uuid: c6c0d8ea-743f-4852-99d1-69fd50a0994e
contentOwner: vishgupt
topic-tags: document_services, publish
discoiquuid: dd11fd83-3df1-4727-8340-8c5426812823
source-git-commit: 6bb7b2d056d501d83cf227adb239f7f40f87d0ce
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 80%

---


# Gestion des applications et des tâches Forms dans la boîte de réception AEM {#manage-forms-applications-and-tasks-in-aem-inbox}

L’une des nombreuses façons de lancer ou de déclencher un processus orienté formulaire consiste à utiliser des applications dans la boîte de réception AEM. Vous devez créer une application de workflow pour qu’un Forms Workflow soit disponible en tant qu’application dans la boîte de réception. Pour plus d’informations sur l’application de processus et d’autres façons de lancer les processus de Forms, voir [Lancement d’un processus orienté formulaire sur OSGi](aem-forms-workflow.md#launch).

En outre, la boîte de réception AEM rassemble les notifications et les tâches provenant de divers composants d’AEM, y compris les workflows de Forms. Lorsqu’un Forms Workflow contenant une étape Affecter une tâche est déclenché, l’application associée est répertoriée en tant que tâche dans la boîte de réception de la personne désignée. Si l’entité désignée est un groupe, la tâche apparaît dans la boîte de réception de toutes les personnes membres du groupe jusqu’à ce qu’une personne demande ou délègue la tâche.

L’interface utilisateur de la boîte de réception fournit la liste et les vues de calendrier pour afficher les tâches. Vous pouvez également configurer les paramètres d’affichage. Vous pouvez filtrer les tâches en fonction de divers paramètres. Pour plus d’informations sur la vue et les filtres, voir [Votre boîte de réception](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/getting-started/inbox.html?lang=fr#inbox-in-the-header).

En résumé, la boîte de réception vous permet de créer une application et de gérer les tâches affectées.

>[!NOTE]
>
>Vous devez être membre du groupe [!DNL workflow-users] pour pouvoir utiliser la boîte de réception AEM.

## Création d’une application {#create-application}

1. Accédez à la boîte de réception AEM à l’adresse https://’[serveur]:[port/]’/aem/inbox.
1. Dans l’interface utilisateur de la boîte de réception, appuyez sur **[!UICONTROL Créer > Application]**. La page Sélectionner l’application s’affiche.
1. Sélectionnez une application, puis appuyez sur **[!UICONTROL Créer]**. Le formulaire adaptatif associé à l’application s’ouvre. Renseignez les informations dans le formulaire adaptatif et appuyez sur **[!UICONTROL Soumettre]**. Cette action lance le processus associé et crée une tâche dans la boîte de réception de la personne désignée.

## Gestion des tâches {#manage-tasks}

Lorsqu’un workflow Forms se déclenche et que vous êtes une personne désignée ou faites partie du groupe désigné, une tâche s’affiche dans votre boîte de réception. Vous pouvez afficher les détails de la tâche et exécuter les actions disponibles sur la tâche depuis la boîte de réception.

### Demande ou délégation de tâches {#claim-or-delegate-tasks}

Les tâches affectées à un groupe apparaissent dans la boîte de réception de toutes les personnes membres du groupe. Toute personne membre du groupe peut demander la tâche ou la déléguer à une autre personne membre du groupe. Pour ce faire :

1. Appuyez pour sélectionner la miniature de la tâche. Les options d’ouverture ou de délégation de la tâche s’affichent en haut.

   ![select-task](assets/select-task.png)

1. Utilisez l’une des méthodes suivantes :

   * Pour déléguer la tâche, appuyez sur **[!UICONTROL Déléguer]**. La boîte de dialogue Déléguer l’élément s’affiche. Sélectionnez un utilisateur (vous pouvez également ajouter un commentaire) puis appuyez sur **[!UICONTROL OK]**.

   ![déléguer](assets/delegate.png)

   * Pour demander la tâche, appuyez sur **[!UICONTROL Ouvrir]**. La boîte de dialogue Auto-affecter s’affiche. Appuyer sur **[!UICONTROL Continuer]** pour demander la tâche. La tâche demandée apparaît dans votre boîte de réception, avec vous en tant que personne désignée.

   ![claim](assets/claim.png)

### Affichage des détails et actions sur les tâches {#view-details-and-perform-actions-on-tasks}

Lorsque vous ouvrez une tâche, vous pouvez afficher les détails de celle-ci et exécuter les actions disponibles. Les actions disponibles pour une tâche sont définies à l’étape Affecter une tâche du Forms Workflow associé.

1. Appuyez pour sélectionner la miniature de la tâche. Les options pour ouvrir ou déléguer la tâche sélectionnée s’affichent en haut.
1. Sélectionner **Ouvrir** pour afficher les détails de la tâche et les actions disponibles. La vue détaillée de la tâche s’ouvre. Dans cette vue, vous pouvez afficher les détails de la tâche et agir sur une tâche.

   >[!NOTE]
   >
   >Si une tâche est affectée à un groupe, vous devez d’abord la demander pour pouvoir l’ouvrir dans la vue détaillée.

![détails de la tâche](assets/task-details.png)

La vue détaillée de tâche comprend les sections suivantes :

* Détails de la tâche
* Formulaire
* Détails du processus
* Barre d’outils Actions

#### Détails de la tâche {#task-details}

La section Détails de la tâche affiche des informations sur la tâche. Les informations affichées dépendent des paramètres de configuration de l’[étape Affecter une tâche](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-step-ref.html?lang=fr#extending-aem) dans le processus. Dans l’exemple ci-dessus s’affichent la description, le statut, la date de début et le workflow utilisé pour la tâche. Vous pouvez également joindre un fichier à la tâche.

#### Formulaire {#form}

L’onglet Formulaire dans la zone de contenu principale affiche le formulaire envoyé et les pièces jointes du champ, le cas échéant.

#### Détails du processus {#workflow-details}

L’onglet Détails du workflow en haut affiche la progression de la tâche via différentes étapes du worflow. Il affiche les étapes terminées, en cours et en attente pour la tâche. Les étapes d’un processus sont définies à [l’étape Affecter une tâche](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-step-ref.html?lang=fr#extending-aem) du processus associé.

En outre, l’onglet affiche l’historique de la tâche pour chaque étape terminée dans le workflow. Vous pouvez appuyer sur **[!UICONTROL Afficher les détails]** d’une étape terminée afin d’en connaître les détails. Cette action permet d’afficher les détails de la tâche : les commentaires, les pièces jointes de formulaire et de tâches, le statut, les dates de début et de fin, etc.

![workflow-details](assets/workflow-details.png)

#### Barre d’outils Actions {#actions-toolbar}

La barre d’outils Actions affiche toutes les options disponibles pour la tâche. Bien que les actions Enregistrer, Réinitialiser et Déléguer soient des actions par défaut, d’autres actions disponibles sont configurées dans la variable [Étape Affecter une tâche](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-step-ref.html?lang=fr#extending-aem). Dans l’exemple ci-dessus, les options Approuver et Rejeter sont configurées dans le workflow.

Lorsque vous agissez sur la tâche, celle-ci se poursuit plus loin dans le workflow.

### Afficher les tâches terminées {#view-completed-tasks}

La boîte de réception AEM affiche uniquement les tâches actives. Les tâches terminées n’apparaissent pas dans la liste. Cependant, vous pouvez utiliser les filtres de boîte de réception pour filtrer les tâches en fonction de plusieurs paramètres, tels que le type de tâche, l’état, les dates de début et de fin. Pour afficher les tâches terminées :

1. Dans la boîte de réception AEM, appuyez sur ![toggle-side-panel1](assets/toggle-side-panel1.png) pour ouvrir le sélecteur de filtres.
1. Appuyez sur l’accordéon **[!UICONTROL Statut de la tâche]** et choisissez **[!UICONTROL Terminé]**. Toutes vos tâches terminées s’affichent.

   ![filter](assets/filter.png)

1. Appuyez pour sélectionner une tâche et appuyez sur **[!UICONTROL Ouvrir]**.

La tâche s’ouvre pour afficher le document ou le formulaire adaptatif associé à la tâche. Pour les formulaires adaptatifs, la tâche affiche le formulaire adaptatif en lecture seule ou son document d’enregistrement PDF tel que configuré dans l’onglet Formulaire/Document de l’[étape Affecter une tâche du processus](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-step-ref.html?lang=fr#extending-aem).

La section de détails de la tâche affiche des informations telles qu’une mesure prise, l’état de la tâche, la date de début et la date de fin.

![completed-task](assets/completed-task.png)

L’onglet **[!UICONTROL Détails du processus]** affiche chaque étape du processus. Appuyez sur **[!UICONTROL Afficher les détails]** d’une étape pour obtenir des informations détaillées.

![completed-task-workflow](assets/completed-task-workflow.png)

## Résolution des problèmes {#troubleshooting-workflows}

### Impossible d’afficher les éléments liés au workflow AEM dans AEM boîte de réception {#unable-to-see-aem-worklow-items}

Un propriétaire de modèle de workflow ne peut pas afficher les éléments liés à AEM workflow dans AEM boîte de réception. Pour résoudre ce problème, ajoutez les index suivants à votre référentiel AEM et recréez l’index.

1. Pour ajouter des index, utilisez l’une des méthodes suivantes :

   * Créez les nœuds suivants dans CRX DE à `/oak:index/workflowDataLucene/indexRules/granite:InboxItem/properties` avec les propriétés respectives spécifiées dans le tableau suivant :

     | Nœud | Propriété | Type |
     |---|---|---|
     | sharedWith | sharedWith | CHAÎNE |
     | verrouillé | verrouillé | BOOLÉEN |
     | renvoyé | renvoyé | BOOLÉEN |
     | allowInboxSharing | allowInboxSharing | BOOLÉEN |
     | allowExplicitSharing | allowExplicitSharing | BOOLÉEN |


   * Déployez les index au moyen d’un package AEM. Vous pouvez utiliser un projet [AEM Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) pour créer un package AEM déployable. Utilisez l’exemple de code suivant pour ajouter des index à un projet AEM Archetype :

   ```Java
      .property("sharedWith", "sharedWith").type(TYPENAME_STRING).propertyIndex()
      .property("locked", "locked").type(TYPENAME_BOOLEAN).propertyIndex()
      .property("returned", "returned").type(TYPENAME_BOOLEAN).propertyIndex()
      .property("allowInboxSharing", "allowInboxSharing").type(TYPENAME_BOOLEAN).propertyIndex()
      .property("allowExplicitSharing", "allowExplicitSharing").type(TYPENAME_BOOLEAN).propertyIndex()
   ```

1. [Créez un index de propriétés et définissez-le sur Vrai](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/queries-and-indexing.html?lang=fr#the-property-index).

1. Après avoir configuré des index dans CRX DE ou procédé au déploiement via un package, [réindexez le référentiel](https://helpx.adobe.com/fr/experience-manager/kb/HowToCheckLuceneIndex.html#Completelyrebuildtheindex).

