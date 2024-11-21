---
Title: How to integrate Marketo Engage with AEM Forms using Form wizard?
Description: Learn how to integrate your Marketo Engage instance with AEM Forms using form wizard.
Keywords: How to connect a Marketo instance with form? , Connect a form to Marketo, Integrate a form with Marketo Engage, Integrate an Adaptive Form with a Marketo instance.
Feature: Adaptive Forms, Form Data Model
Role: User, Developer
source-git-commit: 681c194f997ab66f93beedad4eea273614e6797d
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 6%

---


# Configurer un nouveau formulaire à intégrer à Marketo Engage

<span class="preview"> La fonctionnalité est disponible dans le cadre du programme d’adoption précoce. Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre adresse e-mail officielle pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité. </span>

![Workflow](/help/forms/assets/workflow-marketo-4.png)

Après avoir créé la configuration du service cloud pour intégrer Marketo Engage à AEM Forms, vous pouvez configurer un formulaire adaptatif à intégrer à [Adobe Marketo Engage](https://experienceleague.adobe.com/en/docs/marketo/using/home).

Vous pouvez connecter un Marketo Engage à un formulaire adaptatif à l’aide de l’assistant de formulaire, ce qui simplifie le processus de configuration en vous guidant à chaque étape. Il comprend la sélection de modèles, de styles et de champs de données, ainsi que la configuration du mappage de données pour vous assurer que votre formulaire est prêt à communiquer avec Marketo Engage une fois créé. L’assistant de formulaire vous permet également de configurer le formulaire adaptatif pour envoyer directement des données à Adobe Marketo Engage lors de l’envoi.

## Remarque concernant la configuration de la source de données Marketo Engage pour les formulaires

Lors de la configuration de la source de données Marketo Engage pour les formulaires, les points à prendre en compte sont les suivants :

* Il n’est pas possible de connecter Edge Delivery Services Forms à Marketo Engage.

## Condition préalable requise pour connecter le Marketo Engage à des formulaires

Condition préalable requise pour connecter le Marketo Engage aux formulaires :

* Créez la configuration de service cloud [ pour intégrer Marketo Engage à forms](/help/forms/integrate-form-to-marketo-engage.md).

## Comment configurer un nouveau formulaire adaptatif pour l’intégrer à Marketo Engage ?

Pour configurer un nouveau formulaire adaptatif à intégrer à Marketo Engage, procédez comme suit :

1. Sélectionnez **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.

   ![Sélectionner Forms et documents](/help/forms/assets/select-forms.png)

1. Sélectionnez **[!UICONTROL Créer]** > **[!UICONTROL Forms adaptatif]**. L’assistant de création de formulaire s’ouvre.

   ![Sélectionner AF](/help/forms/assets/select-create-forms.png)

1. Dans l’onglet **[!UICONTROL Source]** , sélectionnez un modèle.

   ![Sélectionner des modèles](/help/forms/assets/select-template.png)

1. Dans le **[!UICONTROL Style]**, sélectionnez le thème.

   ![Sélectionner un thème](/help/forms/assets/select-form-theme.png)


1. Dans l&#39;onglet **[!UICONTROL Data]**, sélectionnez un modèle de données comme **Marketo Engage**.

1. Sélectionnez la **[!UICONTROL configuration cloud]** dans la liste déroulante qui s’affiche dans le volet droit de l’écran.
Par défaut, tous les champs de la configuration associée s’affichent. L’assistant vous permet de choisir de manière sélective les champs à inclure dans le formulaire adaptatif à l’aide de cases à cocher.

   ![Sélectionner un modèle de données](/help/forms/assets/select-marketo-data.png)

1. Dans l’onglet **[!UICONTROL Submission]** (Envoi), sélectionnez l’action d’envoi **[!UICONTROL Submit to Marketo]** (Envoyer à).

   Lorsque vous sélectionnez le modèle de données **Marketo Engage**, l’action d’envoi **Envoyer à Marketo** est automatiquement sélectionnée. Vous pouvez sélectionner une autre action d’envoi à partir de l’onglet **[!UICONTROL Submission]** (Envoi). L’onglet **[!UICONTROL Submission]** affiche toutes les actions d’envoi disponibles.

   ![Submit to Marketo engage](/help/forms/assets/select-marketo-engage.png)

1. Sélectionnez **[!UICONTROL Créer]**. Indiquez le titre, le nom et l’emplacement d’enregistrement du formulaire adaptatif.

   ![Créer un formulaire](/help/forms/assets/create-marketo-form.png)

1. Sélectionnez **[!UICONTROL Créer]**.

Le formulaire adaptatif est maintenant configuré pour se connecter à l’instance de Marketo Engage. Vous pouvez également modifier les propriétés du formulaire adaptatif pour modifier la configuration qui lui est associée.

## Questions fréquentes

**Q : Pouvez-vous modifier l’action d’envoi des formulaires configurés pour se connecter au schéma du Marketo Engage ?**
**A :** Par défaut, l’action **Envoyer à Marketo** est sélectionnée lorsqu’un formulaire est configuré pour se connecter au schéma du Marketo Engage. Cependant, vous pouvez modifier l’action d’envoi des formulaires si nécessaire.


**Q : Que se passe-t-il lorsque vous modifiez le connecteur du formulaire ?**\
**A :** Si vous modifiez le connecteur du formulaire, les liaisons existantes ne sont plus valides.

**Q : Quelles sont les trois opérations disponibles dans le service Invoke de l’éditeur de règles pour les formulaires intégrés à Marketo Engage ?**\
**A :** Les trois opérations d’usine disponibles dans le **service d’appel** pour les formulaires intégrés à Marketo Engage sont les suivantes :
* piste de synchronisation
* Obtention d’une piste avec ID
* Obtention d’une piste par type de filtre

## Étape suivante

Vous pouvez également connecter un formulaire adaptatif à la [bibliothèque Munchkin](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/setup/munchkin) pour effectuer le suivi du nombre de visites, de clics et d’envois de formulaire.

## Articles connexes

{{af-submit-action}}

## Voir également

{{marketo-engage-see-also}}
