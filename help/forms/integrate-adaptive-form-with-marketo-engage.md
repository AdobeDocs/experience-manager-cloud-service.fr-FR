---
title: Comment intégrer Marketo Engage à AEM Forms à l’aide de l’assistant de formulaire ?
description: Découvrez comment intégrer votre instance Marketo Engage à AEM Forms à l’aide de l’assistant de formulaires.
keywords: Comment connecter une instance Marketo à un formulaire ? , Connecter un formulaire à Marketo, Intégrer un formulaire à Marketo Engage, Intégrer un formulaire adaptatif à une instance Marketo.
feature: Adaptive Forms, Form Data Model
role: User, Developer
exl-id: 1fcba628-ffd8-416a-a8b5-76b35d4aabd4
source-git-commit: 4bb63932a658cf01cc493b9e5e68b96984cce49c
workflow-type: tm+mt
source-wordcount: '1048'
ht-degree: 21%

---

# Intégration d’un formulaire adaptatif à Marketo Engage

<span class="preview"> Cette fonctionnalité est disponible par le biais d’un programme d’adoption précoce. Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre identifiant e-mail officiel pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité. </span>

![Workflow](/help/forms/assets/workflow-marketo-4.png)

Après avoir créé la configuration de service cloud pour intégrer Marketo Engage à AEM Forms, vous pouvez configurer un formulaire adaptatif à intégrer à [Adobe Marketo Engage](https://experienceleague.adobe.com/en/docs/marketo/using/home).

Vous pouvez connecter Marketo Engage à un formulaire adaptatif à l’aide de l’assistant de formulaire, ce qui simplifie le processus de configuration en vous guidant à travers chaque étape. Cela inclut la sélection de modèles, de styles et de champs de données, ainsi que la configuration du mappage de données pour vous assurer que votre formulaire est prêt à communiquer avec Marketo Engage une fois créé. À l’aide de l’assistant de formulaire, vous pouvez également configurer le formulaire adaptatif pour envoyer directement les données à Adobe Marketo Engage lors de l’envoi.

## Condition préalable requise pour connecter Marketo Engage aux formulaires

Prérequis pour connecter Marketo Engage aux formulaires :

* Créez la [configuration du service cloud pour intégrer Marketo Engage aux formulaires](/help/forms/integrate-form-to-marketo-engage.md).

## Comment configurer un nouveau formulaire adaptatif pour l’intégrer à Marketo Engage ?

>[!VIDEO](https://video.tv.adobe.com/v/3442867/marketo-aem-marketo-engage-engage-aem-forms)

<span> Cette vidéo s’applique uniquement aux composants principaux. Pour les composants éditeur universel/de base, reportez-vous à l’article </span>.

>[!BEGINTABS]

>[!TAB Composant de base]

Pour configurer un nouveau formulaire adaptatif basé sur les composants de base à intégrer à Marketo Engage, procédez comme suit :

1. Sélectionnez **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.

   ![Sélectionner le Forms et les documents](/help/forms/assets/select-forms.png)

1. Sélectionnez **[!UICONTROL Créer]** > **[!UICONTROL Formulaires adaptatifs]**. L’assistant de création de formulaire s’ouvre.

   ![Sélectionner AF](/help/forms/assets/select-create-forms.png)

1. Dans l&#39;onglet **[!UICONTROL Source]**, sélectionnez un modèle

   ![Sélectionner modèles](/help/forms/assets/select-template-af1.png)

1. Sélectionnez le thème dans **[!UICONTROL Style]**.

   ![Sélectionner un thème](/help/forms/assets/select-form-theme-af1.png)
1. Dans l’onglet **[!UICONTROL Données]**, sélectionnez un modèle de données en tant que **Marketo Engage**.
1. Sélectionnez la **[!UICONTROL Configuration du cloud]** dans la liste déroulante qui s’affiche dans le volet de droite de l’écran.
Par défaut, tous les champs de la configuration associée s’affichent. L’assistant vous permet de choisir les champs à inclure dans le formulaire adaptatif au moyen de cases à cocher.

   ![Sélectionner le modèle de données](/help/forms/assets/select-marketo-data-af1.png)

1. Dans l’onglet **[!UICONTROL Envoi]**, sélectionnez l’action d’envoi **[!UICONTROL Envoyer à Marketo]**.

   Lorsque vous sélectionnez le modèle de données en tant que **Marketo Engage**, l’action d’envoi **Envoyer à Marketo** est sélectionnée automatiquement. Vous pouvez sélectionner une autre action d’envoi dans l’onglet **[!UICONTROL Envoi]**. L’onglet **[!UICONTROL Envoi]** affiche toutes les actions d’envoi disponibles.

   ![Envoyer à Marketo engage](/help/forms/assets/select-marketo-engage.png)

1. Sélectionnez **[!UICONTROL Créer]**. Indiquez le titre, le nom et l’emplacement d’enregistrement du formulaire adaptatif.

   ![Créer un formulaire](/help/forms/assets/create-marketo-form.png)

1. Sélectionnez **[!UICONTROL Créer]**.

Le formulaire adaptatif est maintenant configuré pour se connecter à l’instance Marketo Engage. Vous pouvez également modifier les propriétés du formulaire adaptatif pour modifier sa configuration associée

>[!TAB Composant principal]

Pour configurer un nouveau formulaire adaptatif basé sur les composants principaux à intégrer à Marketo Engage, procédez comme suit :

1. Sélectionnez **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.

   ![Sélectionner le Forms et les documents](/help/forms/assets/select-forms.png)

1. Sélectionnez **[!UICONTROL Créer]** > **[!UICONTROL Formulaires adaptatifs]**. L’assistant de création de formulaire s’ouvre.

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

Le formulaire adaptatif est maintenant configuré pour se connecter à l’instance Marketo Engage. Vous pouvez également modifier les propriétés du formulaire adaptatif pour modifier sa configuration associée.

>[!TAB Éditeur universel]

Pour configurer un nouveau formulaire adaptatif créé dans l’éditeur universel afin de l’intégrer à Marketo Engage, procédez comme suit :

1. Sélectionnez **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.

   ![Sélectionner le Forms et les documents](/help/forms/assets/select-forms.png)

1. Sélectionnez **[!UICONTROL Créer]** > **[!UICONTROL Formulaires adaptatifs]**. L’assistant de création de formulaire s’ouvre.

   ![Sélectionner AF](/help/forms/assets/select-create-forms.png)

1. Dans l&#39;onglet **[!UICONTROL Source]**, sélectionnez un modèle

   ![Sélectionner modèles](/help/forms/assets/select-template-ue.png)

1. Dans l’onglet **[!UICONTROL Données]**, sélectionnez un modèle de données en tant que **Marketo Engage**.

1. Sélectionnez la **[!UICONTROL Configuration du cloud]** dans la liste déroulante qui s’affiche dans le volet de droite de l’écran.
Par défaut, tous les champs de la configuration associée s’affichent. L’assistant vous permet de choisir les champs à inclure dans le formulaire adaptatif au moyen de cases à cocher.

   ![Sélectionner le modèle de données](/help/forms/assets/select-marketo-data-ue.png)

1. Dans l’onglet **[!UICONTROL Envoi]**, sélectionnez l’action d’envoi **[!UICONTROL Envoyer à Marketo]**.

   Lorsque vous sélectionnez le modèle de données en tant que **Marketo Engage**, l’action d’envoi **Envoyer à Marketo** est sélectionnée automatiquement. Vous pouvez sélectionner une autre action d’envoi dans l’onglet **[!UICONTROL Envoi]**. L’onglet **[!UICONTROL Envoi]** affiche toutes les actions d’envoi disponibles.

   ![Envoyer à Marketo engage](/help/forms/assets/select-marketo-engage-ue.png)

1. Sélectionnez **[!UICONTROL Créer]**. Indiquez le titre, le nom et l’emplacement d’enregistrement du formulaire adaptatif.

   ![Créer un formulaire](/help/forms/assets/create-marketo-form.png)

1. Sélectionnez **[!UICONTROL Créer]**.

Le formulaire adaptatif est maintenant configuré pour se connecter à l’instance Marketo Engage. Vous pouvez également modifier les propriétés du formulaire adaptatif pour modifier sa configuration associée.

>[!ENDTABS]

## Questions fréquentes

**Q : Pouvez-vous modifier l’action d’envoi pour les formulaires configurés pour se connecter au schéma Marketo Engage ?**
**A :** par défaut, l’action **Envoyer à Marketo** est sélectionnée lorsqu’un formulaire est configuré pour se connecter au schéma Marketo Engage. Cependant, vous pouvez modifier l’action d’envoi des formulaires si nécessaire.


**Q : que se passe-t-il lors de la modification du connecteur du formulaire ?**\
**R :** si vous modifiez le connecteur du formulaire, les liaisons existantes ne sont plus valides.

**Q : quelles sont les trois opérations disponibles dans le service d’appel de l’éditeur de règles pour les formulaires intégrés à Marketo Engage ?**\
**R :** les trois opérations prêtes à l’emploi disponibles dans le **service d’appel** pour les formulaires intégrés à Marketo Engage sont les suivantes :

* Synchroniser le lead
* Obtenir le lead par ID
* Obtenir le lead par type de filtre

## Étape suivante

Vous pouvez également connecter un formulaire adaptatif à la bibliothèque Munchkin [&#128279;](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/setup/munchkin) pour suivre le nombre de visites, de clics et d’envois de formulaire.

## Articles connexes

{{af-submit-action}}

## Voir également

{{marketo-engage-see-also}}
