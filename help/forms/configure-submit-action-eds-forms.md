---
title: Comment configurer une action Envoyer pour un formulaire adaptatif ?
description: Un formulaire adaptatif fournit plusieurs actions Envoyer. Une action Envoyer définit le mode de traitement d’un formulaire adaptatif après l’envoi. Vous pouvez utiliser des actions Envoyer intégrées ou créer les vôtres.
keywords: comment sélectionner une action envoyer pour un formulaire adaptatif, connecter un formulaire adaptatif à une liste sharepoint, connecter un formulaire adaptatif à une bibliothèque de documents sharepoint, connecter un formulaire adaptatif à un modèle de données de formulaire (FDM)
feature: Adaptive Forms, Edge Delivery Services
role: User, Developer
exl-id: 3f8950c3-9022-4e9f-b3ed-723245201e45
source-git-commit: 2c3e8f6f8dab1004a6fbd9be8f5604b1570a1808
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 18%

---

# Actions Envoyer pour Edge Delivery Services Forms

| Version | Lien de l’article |
|---------|-----------------------------|
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/configuring-submit-actions.html?lang=fr) |
| AEM as a Cloud Service (composants de base) | [Cliquer ici](/help/forms/configuring-submit-actions.md) |
| AEM as a Cloud Service (composants principaux) | [Cliquer ici](/help/forms/configure-submit-actions-core-components.md) |
| AEM as a Cloud Service (Edge Delivery Services) | Cet article |

Les actions Envoyer définissent ce qui se produit lorsqu’un utilisateur envoie un formulaire, comme le stockage des données, le déclenchement de workflows ou l’intégration à des systèmes tiers. Le type d’actions d’envoi que vous pouvez configurer dépend de la méthode de création utilisée pour créer Edge Delivery Services Forms.

Vous pouvez créer Edge Delivery Services Forms à l’aide de l’éditeur [ universel ](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) ou à l’aide de la création [Forms basé sur les documents](/help/edge/docs/forms/overview.md) et configurer les formulaires avec différentes actions d’envoi en conséquence.

## Actions Envoyer pour Forms créées dans l’éditeur universel

Les actions d’envoi suivantes sont prises en charge par [Forms adaptatif créé dans l’éditeur universel](/help/edge/docs/forms/universal-editor/create-forms.md) :

* [Envoyer un e-mail](/help/forms/configure-submit-action-send-email.md)
* [Appeler un flux Power Automate](/help/forms/forms-microsoft-power-automate-integration.md)
* [Envoyer à SharePoint](/help/forms/configure-submit-action-sharepoint.md)
* [Appeler Workfront Fusion](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
* [Envoyer à l’aide du modèle de données de formulaire (FDM)](/help/forms/integrate-adaptive-form-with-fdm.md)
* [Envoyer au stockage Blob Azure](/help/forms/configure-submit-action-azure-blob-storage.md)
* [Envoyer vers le point d’entrée REST](/help/forms/configure-submit-action-restpoint.md)
* [Envoyer à OneDrive](/help/forms/configure-submit-action-onedrive.md)
* [Appeler un workflow AEM](/help/forms/configure-submit-action-workflow.md)
* [Envoyer à Marketo Engage](/help/forms/submit-adaptive-form-to-marketo-engage.md)
* [Envoyer à Adobe Experience Platform (AEP)](/help/forms/aem-forms-aep-connector.md)
* [Envoyer à la feuille de calcul](/help/forms/forms-submission-service.md)

<!--You can also submit an Adaptive Form in the Universal Editor to other storage or CRM integrations:

* [Connect Adaptive Form to Salesforce](/help/forms/aem-forms-salesforce-integration.md)
* [Connect an Adaptive Form to Microsoft&reg; Dynamics OData](/help/forms/ms-dynamics-odata-configuration.md)-->

Vous pouvez configurer l’action d’envoi pour les formulaires créés dans l’éditeur universel à l’aide de l’onglet **Envoi** de l’extension **Modifier les propriétés du formulaire**.

<!--**How to Configure Submit Action for Forms authored in Universal Editor?**
You can configure the submit action for forms created in the Universal Editor using the **Submission** tab of the **Edit Form Properties** extension.

![Form properties icon](/help/forms/assets/ue-form-properties-icon.png)

![Universal Editor Form Properties](/help/forms/assets/ue-form-properties.png)-->

>[!NOTE]
>
> * Si l’icône **Modifier les propriétés de formulaire** ne s’affiche pas dans l’interface de l’éditeur universel, activez l’extension **Modifier les propriétés de formulaire** dans Extension Manager.
> * Consultez l’article [Caractéristiques des fonctionnalités d’Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) pour savoir comment activer ou désactiver les extensions dans l’éditeur universel.

## Actions Envoyer pour le Forms basé sur les documents

Le Forms basé sur les documents prend en charge l’envoi uniquement aux feuilles de calcul. Pour savoir comment configurer votre feuille de calcul pour recevoir les données envoyées, reportez-vous aux instructions de l’article [ Configurer vos feuilles de calcul Google ou fichiers Microsoft Excel pour commencer à accepter les données ](/help/edge/docs/forms/submit-forms.md).

## Voir également {#see-also}

{{af-submit-action}}
