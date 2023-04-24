---
title: Création et gestion de révisions d’Adaptive Forms incorporées ou créées dans la page Sites
seo-title: Review is a mechanism that allows reviewer to perform different tasks for adaptive forms using Assign Task step
description: La révision est un mécanisme qui permet aux réviseurs d’effectuer différentes tâches pour les formulaires adaptatifs à l’aide de l’étape Affecter une tâche
feature: Adaptive Forms
hide: true
hidefromtoc: true
source-git-commit: 2a487654c3af2d2ec3aa43481caed5e1d4fc77a2
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 6%

---


# Étape de révision de Forms dans la page du site {#review-step-forms-aem-sites-page}

En utilisant la variable [Étape Attribuer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference.html#assign-task-step) Dans le workflow AEM, le validant passe en revue le formulaire envoyé et effectue une action sur celui-ci. Pour passer en revue le formulaire envoyé à l’aide de l’étape Affecter une tâche, procédez comme suit :

1. [Création d’un workflow d’AEM](#create-an-aem-workflow)
1. [Configuration de l’action d’envoi du conteneur de formulaires adaptatifs](#configure-submit-action)
1. [Envoyer un formulaire adaptatif après révision](#submit-af-after-review)

## Création d’un workflow d’AEM {#create-an-aem-workflow}

1. Ouvrez votre instance de création en mode d’édition.
1. Accédez à **[!UICONTROL Outils]** >  **[!UICONTROL Workflow]** >  **[!UICONTROL Modèles]** > **[!UICONTROL Créer]** > **[!UICONTROL Créer un modèle]**
1. Indiquez le Titre du workflow et ajoutez le **[Affecter une tâche]** step
1. Appuyer ![settings_icon](assets/settings_icon.png) dans la barre d’actions. Le **[!UICONTROL Assign Task]** s’ouvre.
1. Ouvrir [!UICONTROL Formulaire et document] et ouvrez [!UICONTROL Pré-renseigné] et indiquez :

* Sélectionner le fichier de données d’entrée en utilisant
* Sélectionner les pièces jointes d’entrée en utilisant

   ![Étape de révision](/help/forms/assets/assigntask-review1.gif)

1. Ouvrir **[!UICONTROL Cessionnaire]** et ouvrez [!UICONTROL Pré-renseigné] et indiquez **[!UICONTROL Options d’affectation]**:

   ![Étape de révision](/help/forms/assets/review-assignstep.png)

1. Cliquez sur **[!UICONTROL Terminé]** pour enregistrer les modifications.

## Configuration de l’action d’envoi {#configure-submit-action}

Maintenant, configurez l’action Envoyer d’un composant Conteneur de formulaires adaptatifs sur la page du site :

1. Accédez à la page du site.
1. Appuyer ![settings_icon](assets/settings_icon.png) d’un conteneur de formulaires adaptatifs. Le **[!UICONTROL Conteneur de formulaires adaptatifs]** s’ouvre.
1. Ouvrez le **[!UICONTROL Envoi]** et indiquez **[!UICONTROL Action Envoyer]** to [Appeler un workflow d’AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions.html?lang=en#invoke-an-aem-workflow)

1. Pour enregistrer les paramètres, cliquez sur [Terminé].

![submissiontab-reviewstep](/help/forms/assets/submissiontab-reviewstep.gif)

## Envoyer un formulaire adaptatif après révision {#submit-af-after-review}

Pour vérifier et confirmer le formulaire adaptatif envoyé :

1. Accédez à [!UICONTROL Outils] >  [!UICONTROL Workflow] >  [!UICONTROL Instances]
1. Dans la boîte de réception, vous pouvez constater qu’une instance est en cours de création.
1. Sélectionnez l’instance et cliquez sur [!UICONTROL Ouvrir].
1. Maintenant, vous pouvez voir le formulaire envoyé.

Le réviseur effectue différentes actions, comme suit :

* **Envoyer**: Le réviseur remplit le formulaire et l’envoie pour un traitement ultérieur.
* **Enregistrer**: Le validant enregistre le formulaire dans son état actuel sans l’envoyer.
* **Réinitialiser**: Le réviseur efface toutes les modifications apportées au formulaire et le restaure à son état d’origine.
* **Déléguer**: Le réviseur transfère la propriété du formulaire à une autre personne pour une autre action ou révision.
