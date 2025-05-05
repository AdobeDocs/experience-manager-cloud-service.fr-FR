---
Title: How to configure submit action to Marketo Engage for forms?
Description: Learn how to configure the submit action of Adaptive Form to send data to Marketo Engage.
Keywords: Submit data to Marketo engage, Configure submit action as Submit to Marketo Engage
Feature: Adaptive Forms, Form Data Model
Role: User, Developer
exl-id: 0683564b-1ac4-42b4-bc08-101c4fdef286
source-git-commit: e46c5afac945620cc44e9064956848acecc786bf
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 15%

---

# Configurer l’action d’envoi vers Marketo Engage pour les formulaires existants

<span class="preview"> Cette fonctionnalité est disponible dans le programme des utilisateurs et utilisatrices précoces. Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre identifiant e-mail officiel pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité. </span>

![Workflow](/help/forms/assets/workflow-marketo-3.png)

L’éditeur de Forms adaptatif fournit l’action d’envoi **Envoyer au Marketo Engage** pour envoyer des données de Forms adaptatif à Adobe Marketo Engage en vue de leur traitement. Vous pouvez configurer un formulaire adaptatif existant pour envoyer des données à [Adobe Marketo Engage](https://experienceleague.adobe.com/en/docs/marketo/using/home) lors de l’envoi.

Diverses actions d’envoi prêtes à l’emploi sont disponibles pour gérer les envois de formulaire. Pour en savoir plus sur ces options, consultez l’article [Action d’envoi de formulaire adaptatif](/help/forms/configure-submit-actions-core-components.md).

## Remarque lors de la configuration de l’action d’envoi dans Marketo Engage pour le formulaire

* Assurez-vous que le formulaire adaptatif est configuré avec la source de données du Marketo Engage pour envoyer des données au Marketo Engage lors de l’envoi du formulaire. Cependant, vous pouvez remplacer l’action d’envoi par d’autres, par exemple **Envoyer à OneDrive** ou **Envoyer à SharePoint**, même si le formulaire est configuré avec le schéma de données du Marketo Engage.

## Condition préalable requise pour configurer l’action d’envoi dans Marketo Engage pour le formulaire existant

Condition préalable requise pour configurer l’action d’envoi dans Marketo Engage :

* Configurez la source de données [Marketo Engage pour le formulaire adaptatif](/help/forms/use-marketo-engage-data-source-in-form.md) et liez les éléments de formulaire aux champs du Marketo Engage.

## Comment configurer l’action d’envoi dans Marketo Engage pour les formulaires existants ?

>[!VIDEO](https://video.tv.adobe.com/v/3442866/submit-action-marketo-engage-marketo-aem-aem-forms-engage)

Vous pouvez configurer l’action d’envoi d’un formulaire adaptatif pour envoyer des données à Adobe Marketo Engage. Pour configurer l’action d’envoi dans Marketo Engage, procédez comme suit :

1. Ouvrez le formulaire adaptatif pour le modifier.
2. Ouvrez l’arborescence de contenu et sélectionnez le **[!UICONTROL conteneur de guide]**.
3. Cliquez sur l’icône des propriétés de conteneur de formulaires adaptatifs ![propriétés de conteneur de formulaires adaptatifs](/help/forms/assets/configure-icon.svg). Le conteneur de formulaires adaptatifs pour configurer l’action d’envoi s’ouvre.
4. Ouvrez l’onglet **[!UICONTROL Envoi]** et sélectionnez une action d’envoi comme **Envoyer au Marketo Engage**.
5. Cliquez sur **[!UICONTROL Terminé]**.

![Action d’envoi Marketo](/help/forms/assets/marketo-engage-submit-action.png){width=50%, height=50%}


Après avoir configuré l’action d’envoi pour le formulaire adaptatif en tant que **Envoyer au Marketo Engage**, vous pouvez envoyer des données à Adobe Marketo Engage pour traitement. Les données peuvent être utilisées pour analyser et optimiser les campagnes marketing, automatiser les e-mails de relance et déclencher des workflows en fonction des envois de formulaire.

## Questions fréquentes

**Q : Pouvez-vous modifier l’action d’envoi pour les formulaires configurés pour se connecter au schéma du Marketo Engage ?**
**A :** par défaut, l’action **Envoyer vers Marketo** est sélectionnée lorsqu’un formulaire est configuré pour se connecter au schéma du Marketo Engage. Cependant, vous pouvez modifier l’action d’envoi des formulaires si nécessaire.

## Étape suivante

Vous pouvez également connecter un formulaire adaptatif à la bibliothèque Munchkin [&#128279;](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/setup/munchkin) pour suivre le nombre de visites, de clics et d’envois de formulaire.

## Articles connexes

{{af-submit-action}}

## Voir également

{{marketo-engage-see-also}}
