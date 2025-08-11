---
title: Comment configurer une action Envoyer pour un formulaire adaptatif ?
description: Un formulaire adaptatif fournit plusieurs actions Envoyer. Une action Envoyer définit le mode de traitement d’un formulaire adaptatif après l’envoi. Vous pouvez utiliser des actions Envoyer intégrées ou créer les vôtres.
keywords: comment sélectionner une action envoyer pour un formulaire adaptatif, connecter un formulaire adaptatif à une liste sharepoint, connecter un formulaire adaptatif à une bibliothèque de documents sharepoint, connecter un formulaire adaptatif à un modèle de données de formulaire (FDM)
feature: Adaptive Forms, Edge Delivery Services
role: User, Developer
source-git-commit: cfff846e594b39aa38ffbd3ef80cce1a72749245
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 46%

---

# Action Envoyer pour formulaire adaptatif

| Version | Lien de l’article |
|---------|-----------------------------|
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/configuring-submit-actions.html) |
| AEM as a Cloud Service (composants de base) | [Cliquer ici](/help/forms/configuring-submit-actions.md) |
| AEM as a Cloud Service (composants principaux) | [Cliquer ici](/help/forms/configure-submit-actions-core-components.md) |
| AEM as a Cloud Service (Edge Delivery Services) | Cet article |


L’envoi d’un formulaire est la dernière étape essentielle du parcours de l’utilisateur ou de l’utilisatrice. C’est à ce moment-là que les données collectées sont traitées et que des actions sont lancées. Ce document contient un guide complet pour la configuration et la gestion des actions d’envoi pour les formulaires adaptatifs dans l’éditeur universel.

### Ce que vous apprendrez :

À la fin de ce document, vous aurez appris à :

- Configurer différents types d’actions d’envoi pour vos formulaires
- Configurer des envois de point d’entrée REST pour l’intégration à des systèmes externes
- Configurer les envois d’e-mails pour les réponses de formulaire
- Implémenter des actions d’envoi personnalisées pour des besoins professionnels spécifiques
- Gérer la validation du formulaire et les scénarios d’erreur lors de l’envoi

### Audience cible

Ce guide est conçu pour les publics suivants :

- **Développeurs et développeuses de formulaires** qui implémentent la logique d’envoi
- **Intégrateurs et intégratrices système** qui connectent des formulaires aux systèmes principaux
- **Analystes métier** qui définissent des workflows de formulaire
- **Architectes techniques** qui conçoivent des processus d’envoi de formulaire

## Actions Envoyer pour Forms créées dans l’éditeur universel

Les actions d’envoi suivantes sont prises en charge par [Forms adaptatif créé dans l’éditeur universel](/help/edge/docs/forms/universal-editor/create-forms.md) :

- [Envoyer un e-mail](/help/forms/configure-submit-action-send-email.md)
- [Appeler un flux Power Automate](/help/forms/forms-microsoft-power-automate-integration.md)
- [Envoyer à SharePoint](/help/forms/configure-submit-action-sharepoint.md)
- [Appeler Workfront Fusion](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
- [Envoyer à l’aide du modèle de données de formulaire (FDM)](/help/forms/integrate-adaptive-form-with-fdm.md)
- [Envoyer au stockage Blob Azure](/help/forms/configure-submit-action-azure-blob-storage.md)
- [Envoyer vers le point d’entrée REST](/help/forms/configure-submit-action-restpoint.md)
- [Envoyer à OneDrive](/help/forms/configure-submit-action-onedrive.md)
- [Appeler un workflow AEM](/help/forms/configure-submit-action-workflow.md)
- [Envoyer à Marketo Engage](/help/forms/submit-adaptive-form-to-marketo-engage.md)
- [Envoyer à Adobe Experience Platform (AEP)](/help/forms/aem-forms-aep-connector.md)
- [Envoyer à la feuille de calcul](/help/forms/forms-submission-service.md)

<!--You can also submit an Adaptive Form in the Universal Editor to other storage or CRM integrations:

* [Connect Adaptive Form to Salesforce](/help/forms/aem-forms-salesforce-integration.md)
* [Connect an Adaptive Form to Microsoft&reg; Dynamics OData](/help/forms/ms-dynamics-odata-configuration.md)-->

Vous pouvez configurer l’action d’envoi pour les formulaires créés dans l’éditeur universel à l’aide de l’onglet **Envoi** de l’extension **Modifier les propriétés du formulaire**.

**Comment configurer l’action Envoyer pour Forms créé dans l’éditeur universel ?**
Vous pouvez configurer l’action d’envoi pour les formulaires créés dans l’éditeur universel à l’aide de l’onglet **Envoi** de l’extension **Modifier les propriétés du formulaire**.

![Icône Propriétés du formulaire](/help/forms/assets/ue-form-properties-icon.png)

![Propriétés de formulaire de l’éditeur universel](/help/forms/assets/ue-form-properties.png)

>[!NOTE]
>
> - Si l’icône **Modifier les propriétés de formulaire** ne s’affiche pas dans l’interface de l’éditeur universel, activez l’extension **Modifier les propriétés de formulaire** dans Extension Manager.
> - Consultez l’article [Caractéristiques des fonctionnalités d’Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) pour savoir comment activer ou désactiver les extensions dans l’éditeur universel.



