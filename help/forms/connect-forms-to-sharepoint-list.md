---
Title: How to send data to a SharePoint List storage on submission of an Adaptive Form?
Description: Learn how to send data from your Adaptive Form to a SharePoint storage like a SharePoint list when you submit the form.
keywords: Comment connecter la liste SharePoint d’un formulaire adaptatif ?, Envoyer à SharePoint, Créer une configuration de liste SharePoint, Utiliser l’action d’envoi Envoyer à SharePoint dans un formulaire adaptatif, Connecter un formulaire adaptatif à Microsoft&reg; liste SharePoint.
feature: Adaptive Forms, Core Components
title: Comment configurer une action Envoyer pour un formulaire adaptatif ?
role: User, Developer
source-git-commit: 55e8f142e242f5f4010653a155a241ffcf801470
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 65%

---


# Connecter un formulaire adaptatif à une liste Microsoft® SharePoint {#connect-af-sharepoint-list}

>[!VIDEO](https://video.tv.adobe.com/v/3424820/connect-aem-adaptive-form-to-sharepointlist/?quality=12&learn=on)

Pour utiliser l’action de soumission [!UICONTROL Soumettre à la liste SharePoint] dans un formulaire adaptatif :

1. [Créer une configuration de liste SharePoint](#1-create-a-sharepoint-list-configuration) : connecte AEM Forms à votre stockage de listes Microsoft® SharePoint.
1. [Utiliser l’envoi à l’aide du modèle de données de formulaire (FDM) dans un formulaire adaptatif](#2-use-the-submit-using-form-data-model-fdm-in-an-adaptive-form-use-submit-using-fdm) : connecte votre formulaire adaptatif au SharePoint Microsoft® configuré.

## 1. Création d’une configuration de liste SharePoint

Pour connecter AEM Forms à votre liste Microsoft® SharePoint :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Services cloud]** > **[!UICONTROL Microsoft® SharePoint]**.
1. Sélectionnez un **conteneur de configuration**. La configuration est stockée dans le conteneur de configuration sélectionné.
1. Cliquez sur **[!UICONTROL Créer]** > **[!UICONTROL Liste SharePoint]** dans la liste déroulante. L’assistant de configuration SharePoint s’affiche.
1. Spécifiez le **[!UICONTROL titre]**, l’**[!UICONTROL ID client]**, le **[!UICONTROL secret client]** et l’**[!UICONTROL URL OAuth]**. Pour savoir comment récupérer l’ID client et le secret client pour l’URL OAuth, consultez la [documentation Microsoft®](https://learn.microsoft.com/fr-fr/graph/auth-register-app-v2).
   * Vous pouvez récupérer l’`Client ID` et le `Client Secret` de votre application sur le portail Microsoft® Azure.
   * Sur le portail Microsoft® Azure, ajoutez l’URI de redirection en tant que `https://[author-instance]/libs/cq/sharepointlist/content/configurations/wizard.html`. Remplacez `[author-instance]` par l’URL de votre instance de création.
   * Ajoutez les autorisations d’API `offline_access` et `Sites.Manage.All` dans l’onglet **Graphique Microsoft®** pour fournir des autorisations de lecture/écriture. Ajoutez `AllSites.Manage` autorisation sous l’onglet **Sharepoint** pour interagir à distance avec les données SharePoint.
   * Utilisez l’URL OAuth `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Remplacez `<tenant-id>` par le `tenant-id` de votre application depuis le portail Microsoft® Azure.

     >[!NOTE]
     >
     > Le champ du **secret client** est obligatoire ou facultatif selon la configuration de votre application Azure Active Directory. Si votre application est configurée pour utiliser un secret client, vous devez l’indiquer.

1. Cliquez sur **[!UICONTROL Connecter]**. Lors d’une connexion réussie, le message `Connection Successful` s’affiche.
1. Sélectionnez **[!UICONTROL Site SharePoint]** et **[!UICONTROL Liste SharePoint]** dans la liste déroulante.
1. Sélectionnez **[!UICONTROL Créer]** pour créer la configuration cloud pour Microsoft® SharePointList.


## 2. Utiliser Envoyer à l’aide du modèle de données de formulaire (FDM) dans un formulaire adaptatif {#use-submit-using-fdm}

Vous pouvez utiliser la configuration de liste SharePoint créée dans un formulaire adaptatif pour enregistrer des données ou un document d’enregistrement généré dans une liste SharePoint. Pour utiliser une liste SharePoint dans un formulaire adaptatif, procédez comme suit :

1. [Création d’un modèle de données de formulaire (FDM) à l’aide de Microsoft](/help/forms/create-form-data-models.md)
1. [Configurer le modèle de données de formulaire (FDM) pour récupérer et envoyer des données](/help/forms/work-with-form-data-model.md#configure-services)
1. [Créer un formulaire adaptatif](/help/forms/creating-adaptive-form-core-components.md)
1. [Configuration d’une action Envoyer à l’aide d’un modèle de données de formulaire (FDM)](/help/forms/using-form-data-model.md)

Lorsque vous soumettez le formulaire, les données sont enregistrées dans le stockage de listes Microsoft® SharePoint que vous avez spécifié.

>[!NOTE]
>
> Dans la liste Microsoft® SharePoint, les types de colonnes suivants ne sont pas pris en charge :
> * Colonne image
> * Colonne métadonnées
> * Colonne personne
> * Colonne données externes

## Articles connexes

{{af-submit-action}}