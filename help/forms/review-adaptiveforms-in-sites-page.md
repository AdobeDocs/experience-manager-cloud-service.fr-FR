---
title: Comment envoyer un formulaire adaptatif pour révision ? Comment gérer les révisions d’un formulaire adaptatif aem ?
description: La révision est un mécanisme qui permet aux réviseurs d’effectuer différentes tâches pour les formulaires adaptatifs à l’aide de l’étape Affecter une tâche .
feature: Adaptive Forms
hide: true
hidefromtoc: true
role: User
source-git-commit: 937bd4653e454beea3111cfc7ef7b4bbc1ace193
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 83%

---


# Création et gestion de révisions pour un formulaire adaptatif {#review-step-forms-aem-sites-page}

En suivant l’[Étape Attribuer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference.html#assign-task-step?lang=fr) dans le workflow AEM, le réviseur ou la réviseuse passe en revue le formulaire envoyé et effectue une action sur celui-ci. Pour passer en revue le formulaire envoyé à l’aide de l’étape Affecter une tâche, procédez comme suit :

1. [Créer un workflow AEM](#create-an-aem-workflow)
1. [Configurer l’action Envoyer du conteneur de formulaires adaptatifs](#configure-submit-action)
1. [Envoyer un formulaire adaptatif après révision](#submit-af-after-review)

## Créer un workflow AEM {#create-an-aem-workflow}

1. Ouvrez votre instance de création en mode d’édition.
1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modèles]** > **[!UICONTROL Créer]** > **[!UICONTROL Créer un modèle]**.
1. Indiquez le titre du workflow et ajoutez l’étape **[Affecter une tâche]**.
1. Sélectionnez ![settings_icon](assets/settings_icon.png) dans la barre d’actions. La boîte de dialogue **[!UICONTROL Affecter une tâche]** s’ouvre.
1. Ouvrez l’onglet [!UICONTROL Formulaire et document], ouvrez le menu déroulant [!UICONTROL Pré-renseigné] et indiquez :

   * Sélectionner le fichier de données d’entrée en utilisant
   * Sélectionner les pièces jointes d’entrée en utilisant

   ![Étape de révision](/help/forms/assets/assigntask-review1.gif)

1. Ouvrez l’onglet **[!UICONTROL Personne désignée]**, ouvrez le menu déroulant [!UICONTROL Pré-renseigné] et indiquez **[!UICONTROL Options d’affectation]** :

   ![Étape de révision](/help/forms/assets/review-assignstep.png)

1. Cliquez sur **[!UICONTROL Terminé]** pour enregistrer les modifications.

## Configuration de l’action d’envoi {#configure-submit-action}

Maintenant, configurez l’action Envoyer d’un composant Conteneur de formulaires adaptatifs sur la page Sites :

1. Accédez à la page Sites.
1. Sélectionnez ![settings_icon](assets/settings_icon.png) d’un conteneur de formulaires adaptatifs. Le **[!UICONTROL conteneur de formulaires adaptatifs]** s’ouvre.
1. Ouvrez l’onglet **[!UICONTROL Envoi]** et indiquez l’**[!UICONTROL Action Envoyer]** pour [Appeler un wokflow AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions.html?lang=en#invoke-an-aem-workflow?lang=fr).

1. Pour enregistrer les paramètres, cliquez sur [Terminé].

![submissiontab-reviewstep](/help/forms/assets/submissiontab-reviewstep.gif)

## Envoyer un formulaire adaptatif après révision {#submit-af-after-review}

Pour réviser et confirmer le formulaire adaptatif envoyé :

1. Accédez à [!UICONTROL Outils] > [!UICONTROL Workflow] > [!UICONTROL Instances].
1. Dans la boîte de réception, vous pouvez constater qu’une instance est en cours de création.
1. Sélectionnez l’instance et cliquez sur [!UICONTROL Ouvrir].
1. Maintenant, vous pouvez voir le formulaire envoyé.

Le réviseur ou la réviseuse effectue différentes actions, comme suit :

* **Envoyer** : le réviseur ou la réviseuse remplit le formulaire et l’envoie pour un traitement ultérieur.
* **Enregistrer** : le réviseur ou la réviseuse enregistre le formulaire dans son état actuel sans l’envoyer.
* **Réinitialiser** : le réviseur ou la réviseuse efface toutes les modifications apportées au formulaire et le restaure à son état d’origine.
* **Déléguer** : le réviseur ou la réviseuse transfère la propriété du formulaire à une autre personne pour une autre action ou révision.
