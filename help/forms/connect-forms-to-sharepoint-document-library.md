---
Title: How to integrate Adaptive Form to a SharePoint Document Library?
Description: This article explains how to send data from your Adaptive Form to a SharePoint  Document library when you submit the form.
keywords: Comment connecter la bibliothèque de documents SharePoint à un formulaire adaptatif, l’envoyer à SharePoint, créer une configuration de bibliothèque de documents SharePoint, utiliser l’action d’envoi Envoyer à SharePoint dans un formulaire adaptatif, utiliser la bibliothèque de documents SharePoint du modèle de données AEM Forms, la bibliothèque de documents SharePoint du modèle de données Forms, intégrer le modèle de données Forms à la bibliothèque de documents SharePoint
feature: Adaptive Forms, Core Components, Foundation Components, Edge Delivery Services
role: User, Developer
exl-id: a00b4a93-2324-4c2a-824f-49146dc057b0
source-git-commit: dabf8029577c5fb6bb5eebdbf10d77f3d4d95a5d
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 39%

---

# Connexion d’un formulaire adaptatif à la bibliothèque de documents Microsoft® SharePoint {#connect-af-sharepoint-doc-library}

>[!VIDEO](https://video.tv.adobe.com/v/3444368/formautomation-productivitytools-adaptiveforms--sharepointintegration-documentlibrary/?quality=12&learn=on)

<span> Cette vidéo s’applique uniquement aux composants principaux. Pour les composants UE/Foundation, reportez-vous à l’article </span>.


Pour utiliser l’action d’envoi **[!UICONTROL Envoyer à la bibliothèque de documents SharePoint]** dans un formulaire adaptatif :

1. [Création d’une configuration de bibliothèque de documents SharePoint](#1-create-a-sharepoint-document-library-configuration) : connecte AEM Forms à votre stockage Microsoft® SharePoint.
2. [Utiliser l’action d’envoi Soumettre à SharePoint dans un formulaire adaptatif](#2-use-sharepoint-document-library-configuration-in-an-adaptive-form) : connecte votre formulaire adaptatif au stockage Microsoft® SharePoint configuré.

## &#x200B;1. Création d’une configuration de bibliothèque de documents SharePoint

Pour connecter AEM Forms au stockage de votre bibliothèque de documents Microsoft® SharePoint :

1. Accédez à votre instance de **création AEM Forms** > **[!UICONTROL Outils]** > **[!UICONTROL Services cloud]** > **[!UICONTROL Microsoft® SharePoint]**.
1. Une fois que vous avez sélectionné le stockage **[!UICONTROL Microsoft® SharePoint]**, l’interface vous redirige vers le **[!UICONTROL navigateur SharePoint]**.
1. Sélectionnez un **conteneur de configuration**. La configuration est stockée dans le conteneur de configuration sélectionné.
1. Cliquez sur **[!UICONTROL Créer]** > **[!UICONTROL Bibliothèque de documents SharePoint]** dans la liste déroulante. L’assistant de configuration SharePoint s’affiche.

   ![Configuration de SharePoint](/help/forms/assets/sharepoint_configuration.png)

1. Spécifiez le **[!UICONTROL titre]**, l’**[!UICONTROL ID client]**, le **[!UICONTROL secret client]** et l’**[!UICONTROL URL OAuth]**. Pour savoir comment récupérer l’ID client et le secret client pour l’URL OAuth, consultez la [documentation Microsoft®](https://learn.microsoft.com/fr-fr/graph/auth-register-app-v2).
   * Vous pouvez récupérer l’`Client ID` et le `Client Secret` de votre application sur le portail Microsoft® Azure.
   * Sur le portail Microsoft® Azure, ajoutez l’URI de redirection en tant que `https://[author-instance]/libs/cq/sharepoint/content/configurations/wizard.html`. Remplacez `[author-instance]` par l’URL de votre instance de création.
   * Ajoutez les autorisations d’API `offline_access` et `Sites.Manage.All` pour fournir des autorisations de lecture/écriture. L’`Sites.Manage.All` est une portée d’autorisation dans l’API Graph de Microsoft qui permet à une application de gérer tous les aspects de SharePoint Sites, tels que la suppression ou la modification de Sites.

     >[!NOTE]
     >
     > Vous pouvez également [configurer les sites SharePoint avec un accès limité](/help/forms/configure-sharepoint-site-limited-access.md) en utilisant la portée d’autorisation `Sites.Selected` dans l’API Graph Microsoft. La `Sites.Selected` est une portée d’autorisation dans l’API Graph de Microsoft qui permet un accès plus granulaire et restreint aux sites SharePoint.

   * Utilisez l’URL OAuth `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Remplacez `<tenant-id>` par le `tenant-id` de votre application depuis le portail Microsoft® Azure.

     >[!NOTE]
     >
     > Le champ du **secret client** est obligatoire ou facultatif selon la configuration de votre application Azure Active Directory. Si votre application est configurée pour utiliser un secret client, vous devez l’indiquer.

1. La portée d’autorisation `offline_access Sites.Selected` dans l’API Graph Microsoft qui permet un accès plus granulaire et restreint aux sites SharePoint. La portée d’autorisation `offline_access Sites.Manage.All` dans l’API Graph Microsoft qui permet un accès complet aux sites SharePoint.
1. Cliquez sur **[!UICONTROL Connecter]**. Lors d’une connexion réussie, le message `Connection Successful` s’affiche.

1. Maintenant, sélectionnez **Site SharePoint** > **Bibliothèque de documents** > **Dossier SharePoint**, pour enregistrer les données.

   >[!NOTE]
   >
   >* Par défaut, `forms-ootb-storage-adaptive-forms-submission` est présent sur le site SharePoint sélectionné.
   >* Créez un dossier sous la forme `forms-ootb-storage-adaptive-forms-submission`, s’il n’est pas déjà présent dans la bibliothèque `Documents` du site SharePoint sélectionné en cliquant sur **Créer un dossier**.

Vous pouvez désormais utiliser cette configuration de sites SharePoint pour l’action d’envoi dans un formulaire adaptatif.

### &#x200B;2. Utilisation de la configuration de la bibliothèque de documents SharePoint dans un formulaire adaptatif

Vous pouvez utiliser la configuration de bibliothèque de documents SharePoint créée dans un formulaire adaptatif pour enregistrer des données ou un document d’enregistrement généré dans un dossier SharePoint.

>[!NOTE]
>
> * Sélectionnez le même [!UICONTROL Conteneur de configurations] pour le formulaire adaptatif dans lequel vous avez créé le stockage de votre bibliothèque de documents SharePoint.
> * Si aucun [!UICONTROL conteneur de configuration] n’est sélectionné, les dossiers de [!UICONTROL configuration de stockage] globaux s’affichent dans la fenêtre des propriétés de l’action d’envoi.

>[!BEGINTABS]

>[!TAB Composant de base]

Pour utiliser une configuration de stockage de bibliothèque de documents SharePoint dans un formulaire adaptatif basé sur un composant de base comme suit :

1. Ouvrez le formulaire adaptatif pour le modifier et accéder à la section **[!UICONTROL Envoi]** des propriétés du Conteneur de formulaires adaptatifs.
1. Dans la liste déroulante **[!UICONTROL Action d’envoi]**, sélectionnez **Action d’envoi** comme **[!UICONTROL Envoyer à SharePoint]**.
   ![GIF SharePoint](/help/forms/assets/submit-to-sharepoint-fc.png){width=50%}
1. Sélectionnez la **[!UICONTROL configuration de stockage]** où vous souhaitez enregistrer vos données.
1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les paramètres d’envoi.

>[!NOTE]
>
> * Lorsque vous envoyez le formulaire, les données sont enregistrées dans le stockage de bibliothèque de documents Microsoft® SharePoint spécifié. La structure du dossier pour l’enregistrement des données est `/folder_name/form_name/year/month/date/submission_id/data`.
> * Les pièces jointes sont également stockées dans le répertoire `/folder_name/form_name/year/month/date/submission_id/data`. Cependant, si vous sélectionnez **Enregistrer les pièces jointes avec le nom d’origine**, les pièces jointes sont stockées dans le dossier à l’aide de leurs noms de fichier d’origine.

>[!TAB Composant principal]

Pour utiliser une configuration de stockage de bibliothèque de documents SharePoint dans un formulaire adaptatif basé sur un composant principal comme suit :

1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La fenêtre du conteneur de formulaires adaptatifs s’ouvre.
1. Cliquez sur l’onglet **[!UICONTROL Envoi]**.
1. Dans la liste déroulante **[!UICONTROL Action d’envoi]**, sélectionnez **Action d’envoi** comme **[!UICONTROL Envoyer à SharePoint]**.
   ![GIF SharePoint](/help/forms/assets/sharedrive-video.gif)
1. Sélectionnez la **[!UICONTROL configuration de stockage]** où vous souhaitez enregistrer vos données.
1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les paramètres d’envoi.

>[!NOTE]
>
> * Lorsque vous envoyez le formulaire, les données sont enregistrées dans le stockage de bibliothèque de documents Microsoft® SharePoint spécifié. La structure du dossier pour l’enregistrement des données est `/folder_name/form_name/year/month/date/submission_id/data`.
> * Les pièces jointes sont également stockées dans le répertoire `/folder_name/form_name/year/month/date/submission_id/data`. Cependant, si vous sélectionnez **Enregistrer les pièces jointes avec le nom d’origine**, les pièces jointes sont stockées dans le dossier à l’aide de leurs noms de fichier d’origine.

>[!TAB Éditeur universel]

Pour utiliser une configuration de stockage de bibliothèque de documents SharePoint dans un formulaire adaptatif créé dans l’éditeur universel, procédez comme suit :

1. Ouvrez le formulaire adaptatif pour le modifier.
1. Cliquez sur l’extension **Modifier les propriétés du formulaire** dans l’éditeur.
La boîte de dialogue **Propriétés du formulaire** s’affiche.

   >[!NOTE]
   >
   > * Si l’icône **Modifier les propriétés de formulaire** ne s’affiche pas dans l’interface de l’éditeur universel, activez l’extension **Modifier les propriétés de formulaire** dans Extension Manager.
   > * Consultez l’article [Caractéristiques des fonctionnalités d’Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) pour savoir comment activer ou désactiver les extensions dans l’éditeur universel.

1. Cliquez sur l’onglet **Envoi** et sélectionnez **[!UICONTROL Envoyer à SharePoint]** action d’envoi.
   ![GIF SharePoint](/help/forms/assets/submit-to-sharepoint-ue.png)
1. Sélectionnez la **[!UICONTROL configuration de stockage]** où vous souhaitez enregistrer vos données.
1. Cliquez sur **[!UICONTROL Enregistrer et fermer]** pour enregistrer les paramètres d’envoi.

>[!NOTE]
>
> * Lorsque vous envoyez le formulaire, les données sont enregistrées dans le stockage de bibliothèque de documents Microsoft® SharePoint spécifié. La structure du dossier pour l’enregistrement des données est `/folder_name/form_name/year/month/date/submission_id/data`.
> * Les pièces jointes sont également stockées dans le répertoire `/folder_name/form_name/year/month/date/submission_id/data`. Cependant, si vous sélectionnez **Enregistrer les pièces jointes avec le nom d’origine**, les pièces jointes sont stockées dans le dossier à l’aide de leurs noms de fichier d’origine.

>[!ENDTABS]

## Articles connexes

{{af-submit-action}}
