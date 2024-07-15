---
Title: How to submit data from an Adaptive Form to Microsoft® OneDrive?
Description: Explore the streamlined process of connecting AEM Forms with Microsoft® OneDrive using the Submit to OneDrive Submit Action. Learn the step-by-step guide to configure OneDrive and set up submission actions for efficient data storage and retrieval
keywords: Intégration d’AEM Forms OneDrive, connexion à Microsoft OneDrive, configuration de OneDrive avec AEM forms
feature: Adaptive Forms, Core Components
exl-id: dbfa4094-1b92-4a7c-a799-f66973d27054
title: "Comment configurer une action Envoyer pour un formulaire adaptatif ?"
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 67%

---

# Envoyer un formulaire adaptatif à Microsoft® OneDrive

L’action d’envoi **[!UICONTROL Soumettre à OneDrive]** connecte un formulaire adaptatif à un stockage Microsoft® OneDrive. Vous pouvez envoyer les données de formulaire, les fichiers, les pièces jointes ou le document d’enregistrement au Microsoft® OneDrive Storage connecté.

AEM as a Cloud Service propose différentes actions d’envoi prêtes à l’emploi pour gérer les envois de formulaire. Vous pouvez en savoir plus sur ces options dans l’article [Action d’envoi de formulaire adaptatif](/help/forms/configure-submit-actions-core-components.md) .

## Avantages

Voici quelques-uns des avantages de l’intégration transparente d’AEM Forms et de Microsoft® OneDrive :

* L’accessibilité entre appareils de OneDrive garantit que les données de formulaire stockées sont facilement disponibles sur différentes plateformes. Les utilisateurs peuvent accéder aux données, pièces jointes et documents envoyés depuis des ordinateurs de bureau, des ordinateurs portables, des tablettes et des appareils mobiles, ce qui optimise l’accessibilité et la flexibilité.
* L’intégration de OneDrive à AEM forms offre une solution fiable et évolutive pour un stockage de données efficace. Tous les envois de formulaire adaptatif, tels que les fichiers, les pièces jointes et les documents d’enregistrement, peuvent être facilement enregistrés dans OneDrive, ce qui garantit des données organisées et accessibles.

## Connexion de OneDrive à un formulaire adaptatif

>[!VIDEO](https://video.tv.adobe.com/v/3424864/connect-aem-adaptive-form-to-onedrive/?quality=12&learn=on)

Pour configurer OneDrive pour l’envoi par AEM Forms, procédez comme suit :

1. [Créer une configuration OneDrive](#create-a-onedrive-configuration-create-onedrive-configuration) : connecte AEM Forms à votre stockage Microsoft® OneDrive.
2. [Utilisez l’action d’envoi Envoyer à OneDrive dans un formulaire adaptatif](#use-onedrive-configuration-in-an-adaptive-form-use-onedrive-configuartion-in-af) : cela connecte votre formulaire adaptatif à Microsoft® OneDrive configuré.

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

Vous pouvez utiliser la configuration de stockage OneDrive créée dans un formulaire adaptatif pour enregistrer des données ou un document d’enregistrement généré dans un dossier OneDrive. Suivez les étapes ci-après pour utiliser la configuration de stockage OneDrive dans un formulaire adaptatif :
1. Créez un [formulaire adaptatif](/help/forms/creating-adaptive-form.md).

   >[!NOTE]
   >
   > * Sélectionnez le même [!UICONTROL conteneur de configuration] pour le formulaire adaptatif dans lequel vous avez créé votre espace de stockage OneDrive.
   > * Si aucun [!UICONTROL conteneur de configuration] n’est sélectionné, les dossiers de [!UICONTROL configuration de stockage] globaux s’affichent dans la fenêtre des propriétés de l’action d’envoi.

1. Sélectionnez l’**action Envoyer** pour **[!UICONTROL Envoyer à OneDrive]**.
   ![GIF OneDrive](/help/forms/assets/onedrive-video.gif)
1. Sélectionnez la **[!UICONTROL configuration de stockage]** dans laquelle enregistrer vos données.
1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les paramètres d’envoi.

Lorsque vous soumettez le formulaire, les données sont enregistrées dans le stockage Microsoft® OneDrive que vous avez spécifié.
La structure du dossier pour l’enregistrement des données est `/folder_name/form_name/year/month/date/submission_id/data`.

## Articles connexes

{{af-submit-action}}
