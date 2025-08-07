---
Title: How to submit data from an Adaptive Form to Microsoft&reg; OneDrive?
Description: Explore the streamlined process of connecting AEM Forms with Microsoft&reg; OneDrive using the Submit to OneDrive Submit Action. Learn the step-by-step guide to configure OneDrive and set up submission actions for efficient data storage and retrieval
keywords: Intégration d’AEM Forms OneDrive, Connexion à Microsoft OneDrive, Configuration OneDrive avec AEM Forms
feature: Adaptive Forms, Core Components, Foundation Components, Edge Delivery Services
exl-id: dbfa4094-1b92-4a7c-a799-f66973d27054
title: Comment configurer une action Envoyer pour un formulaire adaptatif ?
role: User, Developer
source-git-commit: dabf8029577c5fb6bb5eebdbf10d77f3d4d95a5d
workflow-type: tm+mt
source-wordcount: '882'
ht-degree: 50%

---

# Envoyer un formulaire adaptatif à Microsoft® OneDrive

L’action d’envoi **[!UICONTROL Soumettre à OneDrive]** connecte un formulaire adaptatif à un stockage Microsoft® OneDrive. Vous pouvez envoyer les données de formulaire, les fichiers, les pièces jointes ou le document d’enregistrement au stockage OneDrive Microsoft® connecté.

AEM as a Cloud Service propose différentes actions d’envoi prêtes à l’emploi pour gérer les envois de formulaires. Pour en savoir plus sur ces options, consultez l’article [Action d’envoi de formulaire adaptatif](/help/forms/aem-forms-submit-action.md).

## Avantages

Voici quelques-uns des avantages de l’intégration transparente d’AEM Forms et de Microsoft® OneDrive :

* L’accessibilité de OneDrive sur plusieurs appareils garantit que les données de formulaire stockées sont facilement disponibles sur différentes plateformes. Les utilisateurs peuvent accéder aux données, aux pièces jointes et aux documents envoyés à partir d’ordinateurs de bureau, d’ordinateurs portables, de tablettes et d’appareils mobiles, ce qui améliore l’accessibilité et la flexibilité.
* L’intégration de OneDrive à AEM forms offre une solution fiable et évolutive pour un stockage de données efficace. Tous les envois de formulaires adaptatifs, tels que les fichiers, les pièces jointes et le document d’enregistrement, peuvent être enregistrés facilement dans OneDrive, ce qui garantit l’organisation et l’accessibilité des données.

## Connecter OneDrive à un formulaire adaptatif

>[!VIDEO](https://video.tv.adobe.com/v/3424864/connect-aem-adaptive-form-to-onedrive/?quality=12&learn=on)

<span> Cette vidéo s’applique uniquement aux composants principaux. Pour les composants UE/Foundation, reportez-vous à l’article </span>.

Configurer OneDrive pour l’envoi AEM Forms, procédez comme suit :

1. [Créer une configuration OneDrive](#create-a-onedrive-configuration-create-onedrive-configuration) : connecte AEM Forms à votre stockage Microsoft® OneDrive.
2. [Utiliser l’action d’envoi Soumettre à OneDrive dans un formulaire adaptatif](#use-onedrive-configuration-in-an-adaptive-form-use-onedrive-configuartion-in-af) : connecte votre formulaire adaptatif au stockage Microsoft® OneDrive configuré.

### Créer une configuration OneDrive {#create-onedrice-configuration}

Pour connecter AEM Forms à votre stockage Microsoft® OneDrive :

1. Accédez à votre instance de **création AEM Forms** > **[!UICONTROL Outils]** > **[!UICONTROL Services cloud]** > **[!UICONTROL Microsoft® OneDrive]**.
1. Une fois que vous avez sélectionné le stockage **[!UICONTROL Microsoft® OneDrive]**, l’interface vous redirige vers le **[!UICONTROL navigateur OneDrive]**.
1. Sélectionnez un **conteneur de configuration**. La configuration est stockée dans le conteneur de configuration sélectionné.
1. Cliquez sur **[!UICONTROL Créer]**. L’assistant de configuration OneDrive s’affiche.

   ![Écran de configuration OneDrive](/help/forms/assets/onedrive-configuration.png)

1. Spécifiez le **[!UICONTROL titre]**, l’**[!UICONTROL ID client]**, le **[!UICONTROL secret client]** et l’**[!UICONTROL URL OAuth]**. Pour savoir comment récupérer l’ID client et le secret client pour l’URL OAuth, consultez la [documentation Microsoft®](https://learn.microsoft.com/fr-fr/graph/auth-register-app-v2).
   * Vous pouvez récupérer l’`Client ID` et le `Client Secret` de votre application sur le portail Microsoft® Azure.
   * Sur le portail Microsoft® Azure, ajoutez l’URI de redirection en tant que `https://[author-instance]/libs/cq/onedrive/content/configurations/wizard.html`. Remplacez `[author-instance]` par l’URL de votre instance de création.
   * Ajoutez les autorisations d’API `offline_access` et `Files.ReadWrite.All` pour fournir les autorisations de lecture/écriture.
   * Utilisez l’URL OAuth `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Remplacez `<tenant-id>` par le `tenant-id` de votre application depuis le portail Microsoft® Azure.

   >[!NOTE]
   >
   > Le champ du **secret client** est obligatoire ou facultatif selon la configuration de votre application Azure Active Directory. Si votre application est configurée pour utiliser un secret client, vous devez l’indiquer.

1. Cliquez sur **[!UICONTROL Connecter]**. Lors d’une connexion réussie, le message `Connection Successful` s’affiche.

1. Sélectionnez à présent **[!UICONTROL Conteneur OneDrive]** > **[Dossier OneDrive]** pour enregistrer les données.

   >[!NOTE]
   >
   >* Par défaut, `forms-ootb-storage-adaptive-forms-submission` se trouve dans le conteneur OneDrive.
   > * Créez un dossier tel que `forms-ootb-storage-adaptive-forms-submission`, le cas échéant, en cliquant sur **Créer un dossier**.

Vous pouvez désormais utiliser cette configuration de stockage OneDrive pour l’action d’envoi dans un formulaire adaptatif.

### Utiliser la configuration OneDrive dans un formulaire adaptatif {#use-onedrive-configuartion-in-af}

Vous pouvez utiliser la configuration de stockage OneDrive créée dans un formulaire adaptatif pour enregistrer des données ou un document d’enregistrement généré dans un dossier OneDrive.

>[!NOTE]
>
> * Sélectionnez le même [!UICONTROL conteneur de configuration] pour le formulaire adaptatif dans lequel vous avez créé votre espace de stockage OneDrive.
> * Si aucun [!UICONTROL conteneur de configuration] n’est sélectionné, les dossiers de [!UICONTROL configuration de stockage] globaux s’affichent dans la fenêtre des propriétés de l’action d’envoi.

>[!BEGINTABS]

>[!TAB Composant de base]

Pour utiliser la configuration de stockage OneDrive dans un formulaire adaptatif basé sur un composant de base comme suit :

1. Ouvrez le formulaire adaptatif pour le modifier et accéder à la section **[!UICONTROL Envoi]** des propriétés du Conteneur de formulaires adaptatifs.
1. Dans la liste déroulante **[!UICONTROL Action Envoyer]**, sélectionnez **[!UICONTROL Envoyer à OneDrive]**.
   ![OneDrive GIF](/help/forms/assets/wubmit-to-onedrive-fc.png){width=50%,height=50%}
Vous pouvez également enregistrer un document d’enregistrement dans OneDrive.
1. Sélectionnez la **[!UICONTROL configuration de stockage]** où vous souhaitez enregistrer vos données.
1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les paramètres d’envoi.

Lorsque vous soumettez le formulaire, les données sont enregistrées dans le stockage Microsoft® OneDrive que vous avez spécifié.
La structure du dossier pour l’enregistrement des données est `/folder_name/form_name/year/month/date/submission_id/data`.

>[!TAB Composant principal]

Pour utiliser la configuration de stockage OneDrive dans un formulaire adaptatif basé sur le composant principal comme suit :

1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La fenêtre du conteneur de formulaires adaptatifs s’ouvre.
1. Cliquez sur l’onglet **[!UICONTROL Envoi]**.
1. Dans la liste déroulante **[!UICONTROL Action Envoyer]**, sélectionnez **[!UICONTROL Envoyer à OneDrive]**.
   ![OneDrive GIF](/help/forms/assets/onedrive-video.gif)
Vous pouvez également enregistrer un document d’enregistrement dans OneDrive.
1. Sélectionnez la **[!UICONTROL configuration de stockage]** où vous souhaitez enregistrer vos données.
1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les paramètres d’envoi.

>[!TAB Éditeur universel]

Pour utiliser la configuration de stockage OneDrive dans un formulaire adaptatif créé dans l’éditeur universel, procédez comme suit :

1. Ouvrez le formulaire adaptatif pour le modifier.
1. Cliquez sur l’extension **Modifier les propriétés du formulaire** dans l’éditeur.
La boîte de dialogue **Propriétés du formulaire** s’affiche.

   >[!NOTE]
   >
   > * Si l’icône **Modifier les propriétés de formulaire** ne s’affiche pas dans l’interface de l’éditeur universel, activez l’extension **Modifier les propriétés de formulaire** dans Extension Manager.
   > * Consultez l’article [Caractéristiques des fonctionnalités d’Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) pour savoir comment activer ou désactiver les extensions dans l’éditeur universel.
1. Cliquez sur l’onglet **Envoi** et sélectionnez **[!UICONTROL Envoyer à OneDrive]**.
   ![OneDrive GIF](/help/forms/assets/submit-to-onedrive-ue.png)
Si vous sélectionnez **Enregistrer les pièces jointes avec le nom d’origine**, les pièces jointes sont stockées dans le dossier à l’aide de leurs noms de fichier d’origine. Vous pouvez également enregistrer un document d’enregistrement (DE) dans le stockage Blob Azure.
1. Sélectionnez la **[!UICONTROL configuration de stockage]** où vous souhaitez enregistrer vos données.
1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**

>[!ENDTABS]

## Articles connexes

{{af-submit-action}}
