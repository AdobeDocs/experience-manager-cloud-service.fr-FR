---
Title: How to configure submit action to Marketo Engage for forms?
Description: Learn how to configure the submit action of Adaptive Form to send data to Marketo Engage.
Keywords: Submit data to Marketo engage, Configure submit action as Submit to Marketo Engage
Feature: Adaptive Forms, Form Data Model
Role: User, Developer
exl-id: 0683564b-1ac4-42b4-bc08-101c4fdef286
source-git-commit: ce4646d8db1870f8ec85faddeb4e0a6a04f4c46e
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 13%

---

# Configurer l’action d’envoi vers Marketo Engage pour les formulaires existants

<span class="preview"> Cette fonctionnalité est disponible par le biais d’un programme d’adoption précoce. Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre identifiant e-mail officiel pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité. </span>

![Workflow](/help/forms/assets/workflow-marketo-3.png)

L’éditeur de Forms adaptatif fournit l’action d’envoi **Envoyer à Marketo Engage** pour envoyer des données de Forms adaptatif à Adobe Marketo Engage en vue de leur traitement. Vous pouvez configurer un formulaire adaptatif existant pour envoyer des données à [Adobe Marketo Engage](https://experienceleague.adobe.com/en/docs/marketo/using/home) lors de l’envoi.

Diverses actions d’envoi prêtes à l’emploi sont disponibles pour gérer les envois de formulaire. Pour en savoir plus sur ces options, consultez l’article [Action d’envoi de formulaire adaptatif](/help/forms/configure-submit-actions-core-components.md).

## Remarque lors de la configuration de l’action d’envoi au Marketo Engage pour le formulaire

* Assurez-vous que le formulaire adaptatif est configuré avec la source de données Marketo Engage pour envoyer des données à Marketo Engage lors de l’envoi du formulaire. Cependant, vous pouvez remplacer l’action d’envoi par d’autres, par exemple **Envoyer à OneDrive** ou **Envoyer à SharePoint**, même si le formulaire est configuré avec le schéma de données Marketo Engage.

## Condition préalable requise pour configurer l’action d’envoi vers Marketo Engage pour le formulaire existant

Prérequis pour configurer l’action d’envoi vers Marketo Engage :

* Configurez la source de données [Marketo Engage pour le formulaire adaptatif](/help/forms/use-marketo-engage-data-source-in-form.md) et liez les éléments de formulaire aux champs Marketo Engage.

## Comment configurer une action d’envoi vers Marketo Engage pour les formulaires existants ?

>[!VIDEO](https://video.tv.adobe.com/v/3442866/submit-action-marketo-engage-marketo-aem-aem-forms-engage)

>[!BEGINTABS]

>[!TAB Composant de base]

Vous pouvez configurer l’action d’envoi d’un formulaire adaptatif en fonction des composants de base pour envoyer des données à Adobe Marketo Engage. Pour configurer l’action d’envoi vers Marketo Engage, procédez comme suit :

1. Connectez-vous à votre instance de création [!DNL Experience Manager Forms].
1. Ouvrez le formulaire adaptatif pour le modifier et accédez à la section **[!UICONTROL Envoi]** des propriétés du conteneur de formulaires adaptatifs et sélectionnez une action d’envoi comme **Envoyer à Marketo Engage**.
1. Cliquez sur **[!UICONTROL Terminé]**.

![Action Envoyer Marketo](/help/forms/assets/marketo-engage-submit-action-af.png){width=50%, height=50%}

Après avoir configuré l’action d’envoi pour le formulaire adaptatif en tant que **Envoyer à Marketo Engage**, vous pouvez envoyer des données à Adobe Marketo Engage pour traitement. Les données peuvent être utilisées pour analyser et optimiser les campagnes marketing, automatiser les e-mails de relance et déclencher des workflows en fonction des envois de formulaire.

>[!TAB Composant principal]

Vous pouvez configurer l’action d’envoi d’un formulaire adaptatif en fonction des composants principaux pour envoyer des données à Adobe Marketo Engage. Pour configurer l’action d’envoi vers Marketo Engage, procédez comme suit :

1. Ouvrez le formulaire adaptatif pour le modifier.
1. Ouvrez l’arborescence de contenu et sélectionnez le **[!UICONTROL conteneur de guide]**.
1. Cliquez sur l’icône des propriétés de conteneur de formulaires adaptatifs ![propriétés de conteneur de formulaires adaptatifs](/help/forms/assets/configure-icon.svg). Le conteneur de formulaires adaptatifs pour configurer l’action d’envoi s’ouvre.
1. Ouvrez l’onglet **[!UICONTROL Envoi]** et sélectionnez une action d’envoi comme **Envoyer à Marketo Engage**.
1. Cliquez sur **[!UICONTROL Terminé]**.

![Action Envoyer Marketo](/help/forms/assets/marketo-engage-submit-action.png){width=50%, height=50%}

Après avoir configuré l’action d’envoi pour le formulaire adaptatif en tant que **Envoyer à Marketo Engage**, vous pouvez envoyer des données à Adobe Marketo Engage pour traitement. Les données peuvent être utilisées pour analyser et optimiser les campagnes marketing, automatiser les e-mails de relance et déclencher des workflows en fonction des envois de formulaire.

>[!TAB Éditeur universel]

Vous pouvez configurer l’action d’envoi d’un formulaire adaptatif créé dans l’éditeur universel pour envoyer des données à Adobe Marketo Engage. Pour configurer l’action d’envoi vers Marketo Engage, procédez comme suit :

1. Ouvrez le formulaire adaptatif pour le modifier.
1. Cliquez sur l’extension **Modifier les propriétés du formulaire** dans l’éditeur.
La boîte de dialogue **Propriétés du formulaire** s’affiche.

   >[!NOTE]
   >
   > * Si l’icône **Modifier les propriétés de formulaire** ne s’affiche pas dans l’interface de l’éditeur universel, activez l’extension **Modifier les propriétés de formulaire** dans Extension Manager.
   > * Consultez l’article [Caractéristiques des fonctionnalités d’Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) pour savoir comment activer ou désactiver les extensions dans l’éditeur universel.

1. Cliquez sur l’onglet **Envoi** et sélectionnez **[!UICONTROL Envoyer à Marketo Engage]** action d’envoi.

   ![Action Envoyer Marketo](/help/forms/assets/marketo-engage-submit-action-ue.png)

1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**.

Après avoir configuré l’action d’envoi pour le formulaire adaptatif en tant que **Envoyer à Marketo Engage**, vous pouvez envoyer des données à Adobe Marketo Engage pour traitement. Les données peuvent être utilisées pour analyser et optimiser les campagnes marketing, automatiser les e-mails de relance et déclencher des workflows en fonction des envois de formulaire.

>[!ENDTABS]

## Questions fréquentes

**Q : Pouvez-vous modifier l’action d’envoi pour les formulaires configurés pour se connecter au schéma Marketo Engage ?**
**A :** par défaut, l’action **Envoyer à Marketo** est sélectionnée lorsqu’un formulaire est configuré pour se connecter au schéma Marketo Engage. Cependant, vous pouvez modifier l’action d’envoi des formulaires si nécessaire.

## Étape suivante

Vous pouvez également connecter un formulaire adaptatif à la bibliothèque Munchkin [](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/setup/munchkin) pour suivre le nombre de visites, de clics et d’envois de formulaire.

## Articles connexes

{{af-submit-action}}

## Voir également

{{marketo-engage-see-also}}
