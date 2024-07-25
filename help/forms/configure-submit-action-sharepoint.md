---
Title: How to send data to a SharePoint storage on submission of an Adaptive Form?
Description: Learn how to send data from your Adaptive Form to a SharePoint storage like a SharePoint list or Document library when you submit the form.
keywords: Comment connecter la liste SharePoint pour un formulaire adaptatif ? Comment connecter la bibliothèque de documents SharePoint pour un formulaire adaptatif, Envoyer à SharePoint, Créer une configuration de bibliothèque de documents SharePoint, Utiliser l’action d’envoi Envoyer à SharePoint dans un formulaire adaptatif, Connecter un formulaire adaptatif à Microsoft&reg; Liste SharePoint.
feature: Adaptive Forms, Core Components
exl-id: e925a750-5fb5-4950-afd3-78551eec985d
title: "Comment configurer une action Envoyer pour un formulaire adaptatif ?"
role: User, Developer
source-git-commit: 5e1d08e82cafc3a8a715653727f42ce0048f2b1f
workflow-type: tm+mt
source-wordcount: '1117'
ht-degree: 52%

---

# Connexion d’un formulaire adaptatif à Microsoft® SharePoint

L’action d’envoi **[!UICONTROL Envoyer à SharePoint]** vous permet de connecter facilement votre formulaire adaptatif à un stockage Microsoft® SharePoint. Il envoie les données du formulaire à l’espace de stockage SharePoint de votre choix après l’envoi du formulaire.

AEM as a Cloud Service propose différentes actions d’envoi prêtes à l’emploi pour gérer les envois de formulaire. Vous pouvez en savoir plus sur ces options dans l’article [Action d’envoi de formulaire adaptatif](/help/forms/configure-submit-actions-core-components.md) .

## Avantages

Voici quelques-uns des avantages de l’envoi de données d’un formulaire adaptatif au stockage SharePoint :

* Il facilite l’envoi direct des données de formulaire à SharePoint, fournissant ainsi un emplacement centralisé pour le stockage et la gestion des informations.
* En appliquant les fonctionnalités de contrôle d’accès et d’autorisations de SharePoint, elle garantit que seules les personnes autorisées peuvent afficher ou modifier les données envoyées.

À l’aide de **[!UICONTROL Submit to SharePoint]**, vous pouvez :

* [Connexion d’un formulaire adaptatif à la bibliothèque de documents SharePoint](#connect-af-sharepoint-doc-library)
* [Connexion d’un formulaire adaptatif à une liste SharePoint](#connect-af-sharepoint-list)

## Connexion d’un formulaire adaptatif à la bibliothèque de documents SharePoint {#connect-af-sharepoint-doc-library}

Pour utiliser l’action d’envoi **[!UICONTROL Submit to SharePoint Document Library]** dans un formulaire adaptatif :

1. [Créer une configuration de bibliothèque de documents SharePoint](#create-a-sharepoint-configuration-create-sharepoint-configuration) : elle connecte AEM Forms à votre stockage Microsoft® SharePoint.
2. [Utiliser l’action d’envoi Soumettre à SharePoint dans un formulaire adaptatif](#use-sharepoint-configuartion-in-af) : connecte votre formulaire adaptatif au stockage Microsoft® SharePoint configuré.

### Création d’une configuration Bibliothèque de documents SharePoint {#create-sharepoint-configuration}

Pour connecter AEM Forms à votre stockage de bibliothèque de documents Microsoft® SharePoint, procédez comme suit :

1. Accédez à votre instance de **création AEM Forms** > **[!UICONTROL Outils]** > **[!UICONTROL Services cloud]** > **[!UICONTROL Microsoft® SharePoint]**.
1. Une fois que vous avez sélectionné le stockage **[!UICONTROL Microsoft® SharePoint]**, l’interface vous redirige vers le **[!UICONTROL navigateur SharePoint]**.
1. Sélectionnez un **conteneur de configuration**. La configuration est stockée dans le conteneur de configuration sélectionné.
1. Cliquez sur **[!UICONTROL Créer]** > **[!UICONTROL Bibliothèque de documents SharePoint]** dans la liste déroulante. L’assistant de configuration SharePoint s’affiche.

   ![Configuration de SharePoint](/help/forms/assets/sharepoint_configuration.png)
1. Spécifiez le **[!UICONTROL titre]**, l’**[!UICONTROL ID client]**, le **[!UICONTROL secret client]** et l’**[!UICONTROL URL OAuth]**. Pour savoir comment récupérer l’ID client et le secret client pour l’URL OAuth, consultez la [documentation Microsoft®](https://learn.microsoft.com/fr-fr/graph/auth-register-app-v2).
   * Vous pouvez récupérer l’`Client ID` et le `Client Secret` de votre application sur le portail Microsoft® Azure.
   * Sur le portail Microsoft® Azure, ajoutez l’URI de redirection en tant que `https://[author-instance]/libs/cq/sharepoint/content/configurations/wizard.html`. Remplacez `[author-instance]` par l’URL de votre instance de création.
   * Ajoutez les autorisations d’API `offline_access` et `Sites.Manage.All` pour fournir des autorisations de lecture/écriture. `Sites.Manage.All` est une portée d’autorisation dans l’API Graph de Microsoft qui permet à une application de gérer tous les aspects des sites SharePoint, comme la suppression ou la modification de sites.

     >[!NOTE]
     >
     > Vous pouvez également [configurer SharePoint Sites avec un accès limité](/help/forms/configure-sharepoint-site-limited-access.md) à l’aide de la portée d’autorisation `Sites.Selected` dans l’API Graph de Microsoft. `Sites.Selected` est une portée d’autorisation dans l’API Microsoft Graph qui permet un accès plus granulaire et restreint aux sites SharePoint.

   * Utilisez l’URL OAuth `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Remplacez `<tenant-id>` par le `tenant-id` de votre application depuis le portail Microsoft® Azure.

   >[!NOTE]
   >
   > Le champ du **secret client** est obligatoire ou facultatif selon la configuration de votre application Azure Active Directory. Si votre application est configurée pour utiliser un secret client, vous devez l’indiquer.

1. Cliquez sur **[!UICONTROL Connecter]**. Lors d’une connexion réussie, le message `Connection Successful` s’affiche.

1. Maintenant, sélectionnez **Site SharePoint** > **Bibliothèque de documents** > **Dossier SharePoint**, pour enregistrer les données.

   >[!NOTE]
   >
   >* Par défaut, `forms-ootb-storage-adaptive-forms-submission` est présent sur le site SharePoint sélectionné.
   >* Créez un dossier sous la forme `forms-ootb-storage-adaptive-forms-submission`, s’il n’est pas déjà présent dans la bibliothèque `Documents` du site SharePoint sélectionné en cliquant sur **Créer un dossier**.

Vous pouvez désormais utiliser cette configuration de sites SharePoint pour l’action d’envoi dans un formulaire adaptatif.

### Utilisation de la configuration de la bibliothèque de documents SharePoint dans un formulaire adaptatif {#use-sharepoint-configuartion-in-af}

Vous pouvez utiliser la configuration de la bibliothèque de documents SharePoint créée dans un formulaire adaptatif pour enregistrer des données ou générer un document d’enregistrement dans un dossier SharePoint. Pour utiliser une configuration de stockage de la bibliothèque de documents SharePoint dans un formulaire adaptatif, procédez comme suit :

1. Créez un [formulaire adaptatif](/help/forms/creating-adaptive-form-core-components.md).

   >[!NOTE]
   >
   > * Sélectionnez le même [!UICONTROL Conteneur de configuration] pour un formulaire adaptatif, où vous avez créé votre stockage dans la bibliothèque de documents SharePoint.
   > * Si aucun [!UICONTROL conteneur de configuration] n’est sélectionné, les dossiers de [!UICONTROL configuration de stockage] globaux s’affichent dans la fenêtre des propriétés de l’action d’envoi.

1. Sélectionnez l’**action d’envoi** **[!UICONTROL Soumettre à SharePoint]**.
   ![GIF SharePoint](/help/forms/assets/sharedrive-video.gif)
1. Sélectionnez la **[!UICONTROL configuration de stockage]** où vous souhaitez enregistrer vos données.
1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les paramètres d’envoi.

Lorsque vous envoyez le formulaire, les données sont enregistrées dans le stockage de la bibliothèque de documents Microsoft® SharePoint spécifié.
La structure du dossier pour l’enregistrement des données est `/folder_name/form_name/year/month/date/submission_id/data`.

## Connecter un formulaire adaptatif à une liste Microsoft® SharePoint {#connect-af-sharepoint-list}

>[!VIDEO](https://video.tv.adobe.com/v/3424820/connect-aem-adaptive-form-to-sharepointlist/?quality=12&learn=on)

Pour utiliser l’action de soumission [!UICONTROL Soumettre à la liste SharePoint] dans un formulaire adaptatif :

1. [Créer une configuration de liste SharePoint](#create-sharepoint-list-configuration) : connecte AEM Forms à votre stockage de listes Microsoft® SharePoint.
1. [Utilisez Submit using Form Data Model (FDM) dans un formulaire adaptatif](#use-submit-using-fdm) : il connecte votre formulaire adaptatif à Microsoft® SharePoint configuré.

### Créer une configuration de liste SharePoint {#create-sharepoint-list-configuration}

Pour connecter AEM Forms à votre liste Microsoft® SharePoint :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Services cloud]** > **[!UICONTROL Microsoft® SharePoint]**.
1. Sélectionnez un **conteneur de configuration**. La configuration est stockée dans le conteneur de configuration sélectionné.
1. Cliquez sur **[!UICONTROL Créer]** > **[!UICONTROL Liste SharePoint]** dans la liste déroulante. L’assistant de configuration SharePoint s’affiche.
1. Spécifiez le **[!UICONTROL titre]**, l’**[!UICONTROL ID client]**, le **[!UICONTROL secret client]** et l’**[!UICONTROL URL OAuth]**. Pour savoir comment récupérer l’ID client et le secret client pour l’URL OAuth, consultez la [documentation Microsoft®](https://learn.microsoft.com/fr-fr/graph/auth-register-app-v2).
   * Vous pouvez récupérer l’`Client ID` et le `Client Secret` de votre application sur le portail Microsoft® Azure.
   * Sur le portail Microsoft® Azure, ajoutez l’URI de redirection en tant que `https://[author-instance]/libs/cq/sharepointlist/content/configurations/wizard.html`. Remplacez `[author-instance]` par l’URL de votre instance de création.
   * Ajoutez les autorisations d’API `offline_access` et `Sites.Manage.All` dans l’onglet **Graphique Microsoft®** pour fournir des autorisations de lecture/écriture. Ajoutez l’autorisation `AllSites.Manage` dans l’onglet **Sharepoint** pour interagir à distance avec les données SharePoint.
   * Utilisez l’URL OAuth `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Remplacez `<tenant-id>` par le `tenant-id` de votre application depuis le portail Microsoft® Azure.

     >[!NOTE]
     >
     > Le champ du **secret client** est obligatoire ou facultatif selon la configuration de votre application Azure Active Directory. Si votre application est configurée pour utiliser un secret client, vous devez l’indiquer.

1. Cliquez sur **[!UICONTROL Connecter]**. Lors d’une connexion réussie, le message `Connection Successful` s’affiche.
1. Sélectionnez **[!UICONTROL Site SharePoint]** et **[!UICONTROL Liste SharePoint]** dans la liste déroulante.
1. Sélectionnez **[!UICONTROL Créer]** pour créer la configuration de cloud pour Microsoft® SharePointList.


### Utilisation de l’option Submit using Form Data Model (FDM) dans un formulaire adaptatif {#use-submit-using-fdm}

Vous pouvez utiliser la configuration de liste SharePoint créée dans un formulaire adaptatif pour enregistrer des données ou un document d’enregistrement généré dans une liste SharePoint. Pour utiliser une liste SharePoint dans un formulaire adaptatif, procédez comme suit :

1. [Création d’un modèle de données de formulaire (FDM) à l’aide de Microsoft](/help/forms/create-form-data-models.md)
1. [Configuration du modèle de données de formulaire (FDM) pour récupérer et envoyer des données](/help/forms/work-with-form-data-model.md#configure-services)
1. [Créer un formulaire adaptatif](/help/forms/creating-adaptive-form-core-components.md)
1. [Configuration de l’action Envoyer à l’aide d’un modèle de données de formulaire (FDM)](/help/forms/using-form-data-model.md)

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
