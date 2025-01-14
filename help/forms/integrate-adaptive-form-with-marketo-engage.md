---
Title: How to integrate Marketo Engage with AEM Forms using Form wizard?
Description: Learn how to integrate your Marketo Engage instance with AEM Forms using form wizard.
Keywords: How to connect a Marketo instance with form? , Connect a form to Marketo, Integrate a form with Marketo Engage, Integrate an Adaptive Form with a Marketo instance.
Feature: Adaptive Forms, Form Data Model
Role: User, Developer
exl-id: 1fcba628-ffd8-416a-a8b5-76b35d4aabd4
source-git-commit: e46c5afac945620cc44e9064956848acecc786bf
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 6%

---

# Configurer un nouveau formulaire à intégrer avec Marketo Engage

<span class="preview"> Cette fonctionnalité est disponible dans le programme des utilisateurs et utilisatrices précoces. Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre identifiant e-mail officiel pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité. </span>

![Workflow](/help/forms/assets/workflow-marketo-4.png)

Après avoir créé la configuration de service cloud pour intégrer Marketo Engage à AEM Forms, vous pouvez configurer un formulaire adaptatif à intégrer à [Adobe Marketo Engage](https://experienceleague.adobe.com/en/docs/marketo/using/home).

Vous pouvez connecter Marketo Engage à un formulaire adaptatif à l’aide de l’assistant de formulaire, ce qui simplifie le processus de configuration en vous guidant à travers chaque étape. Cela inclut la sélection de modèles, de styles et de champs de données, ainsi que la configuration du mappage de données pour vous assurer que votre formulaire est prêt à communiquer avec Marketo Engage une fois créé. À l’aide de l’assistant de formulaire, vous pouvez également configurer le formulaire adaptatif pour envoyer directement les données à Adobe Marketo Engage lors de l’envoi.

## Remarque concernant la configuration de la source de données du Marketo Engage pour les formulaires

Lors de la configuration de la source de données Marketo Engage pour les formulaires, tenez compte des points suivants :

* Il n’est pas possible de connecter Edge Delivery Services Forms à Marketo Engage.

## Condition préalable requise pour connecter Marketo Engage aux formulaires

Condition préalable requise pour connecter Marketo Engage aux formulaires :

* Créez la configuration de service cloud [ pour intégrer Marketo Engage aux formulaires](/help/forms/integrate-form-to-marketo-engage.md).

## Comment configurer un nouveau formulaire adaptatif à intégrer à Marketo Engage ?

>[!VIDEO](https://video.tv.adobe.com/v/3442867/marketo-aem-marketo-engage-engage-aem-forms)

Pour configurer un nouveau formulaire adaptatif à intégrer à Marketo Engage, procédez comme suit :

1. Sélectionnez **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.

   ![Sélectionner le Forms et les documents](/help/forms/assets/select-forms.png)

1. Sélectionnez **[!UICONTROL Créer]** > **[!UICONTROL Forms adaptatif]**. L’assistant de création de formulaire s’ouvre.

   ![Sélectionner AF](/help/forms/assets/select-create-forms.png)

1. Dans l&#39;onglet **[!UICONTROL Source]**, sélectionnez un modèle

   ![Sélectionner modèles](/help/forms/assets/select-template.png)

1. Sélectionnez le thème dans **[!UICONTROL Style]**.

   ![Sélectionner un thème](/help/forms/assets/select-form-theme.png)


1. Dans l’onglet **[!UICONTROL Données]**, sélectionnez un modèle de données en tant que **Marketo Engage**.

1. Sélectionnez la **[!UICONTROL Configuration du cloud]** dans la liste déroulante qui s’affiche dans le volet de droite de l’écran.
Par défaut, tous les champs de la configuration associée s’affichent. L’assistant vous permet de choisir les champs à inclure dans le formulaire adaptatif au moyen de cases à cocher.

   ![Sélectionner le modèle de données](/help/forms/assets/select-marketo-data.png)

1. Dans l’onglet **[!UICONTROL Envoi]**, sélectionnez l’action d’envoi **[!UICONTROL Envoyer à Marketo]**.

   Lorsque vous sélectionnez le modèle de données en tant que **Marketo Engage**, l’action d’envoi **Envoyer à Marketo** est sélectionnée automatiquement. Vous pouvez sélectionner une autre action d’envoi dans l’onglet **[!UICONTROL Envoi]**. L’onglet **[!UICONTROL Envoi]** affiche toutes les actions d’envoi disponibles.

   ![Envoyer à Marketo engage](/help/forms/assets/select-marketo-engage.png)

1. Sélectionnez **[!UICONTROL Créer]**. Indiquez le titre, le nom et l’emplacement d’enregistrement du formulaire adaptatif.

   ![Créer un formulaire](/help/forms/assets/create-marketo-form.png)

1. Sélectionnez **[!UICONTROL Créer]**.

Le formulaire adaptatif est maintenant configuré pour se connecter à l’instance du Marketo Engage. Vous pouvez également modifier les propriétés du formulaire adaptatif pour modifier sa configuration associée.

## Questions fréquentes

**Q : Pouvez-vous modifier l’action d’envoi pour les formulaires configurés pour se connecter au schéma du Marketo Engage ?**
**A :** par défaut, l’action **Envoyer vers Marketo** est sélectionnée lorsqu’un formulaire est configuré pour se connecter au schéma du Marketo Engage. Cependant, vous pouvez modifier l’action d’envoi des formulaires si nécessaire.


**Q : Que se passe-t-il lorsque vous modifiez le connecteur du formulaire ?**\
**A :** si vous modifiez le connecteur du formulaire, les liaisons existantes ne sont plus valides.

**Q : Quelles sont les trois opérations disponibles dans le service Invoke de l’éditeur de règles pour les formulaires intégrés à Marketo Engage ?**\
**A :** les trois opérations prêtes à l’emploi disponibles dans le **service Invoke** pour les formulaires intégrés à Marketo Engage sont les suivantes :
* Synchroniser le lead
* Obtenir le lead par ID
* Obtenir le lead par type de filtre

## Étape suivante

Vous pouvez également connecter un formulaire adaptatif à la bibliothèque Munchkin [](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/setup/munchkin) pour suivre le nombre de visites, de clics et d’envois de formulaire.

## Articles connexes

{{af-submit-action}}

## Voir également

{{marketo-engage-see-also}}
