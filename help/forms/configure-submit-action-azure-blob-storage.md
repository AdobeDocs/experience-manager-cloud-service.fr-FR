---
Title: How to connect AEM Adaptive Forms with Azure Blob Storage?
Description: Learn how to create an Azure Blob Storage Configuration in AEM Forms and use it within your Adaptive Forms for efficient data storage.
keywords: Intégration du stockage Blob Azure à AEM Forms, envoi de données au stockage Azure, création d’une configuration de stockage Azure dans AEM Forms, utilisation du stockage Blob Azure dans l’action d’envoi de Forms adaptative
feature: Adaptive Forms, Foundation Components, Edge Delivery Services, Core Components
exl-id: 0c9f8f85-c4e9-4c79-bd0b-abdcac99a2d4
title: Comment configurer une action Envoyer pour un formulaire adaptatif ?
role: User, Developer
source-git-commit: c0df3c6eaf4e3530cca04157e1a5810ebf5b4055
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 47%

---

# Envoyer un formulaire adaptatif à Azure Blob Storage

L’action d’envoi **[!UICONTROL Envoyer au stockage Azure Blob]** connecte un formulaire adaptatif à un portail Microsoft® Azure. Vous pouvez envoyer les données de formulaire, les fichiers, les pièces jointes ou le document d’enregistrement aux conteneurs de stockage Azure connectés.

AEM as a Cloud Service propose différentes actions d’envoi prêtes à l’emploi pour gérer les envois de formulaires. Pour en savoir plus sur ces options, consultez l’article [Action d’envoi de formulaire adaptatif](/help/forms/aem-forms-submit-action.md).

## Avantages

Voici quelques-uns des avantages de l’intégration du stockage Blob Azure à AEM Forms :

* Il permet de rationaliser le processus d’envoi des données de formulaire adaptatif, des fichiers, des pièces jointes et du document d’enregistrement aux conteneurs de stockage Azure.
* Il utilise Azure Blob Storage pour le stockage centralisé et organisé des envois de formulaires adaptatifs.

## Connecter AEM Forms au stockage Blob Azure Microsoft®

Pour utiliser le stockage Azure Blob dans l’action d’envoi Forms adaptative :

1. [Créer un conteneur de stockage Azure Blob](#create-a-azure-blob-storage-container-create-azure-configuration) : connecte AEM Forms aux conteneurs de stockage Azure.
2. [Utiliser la configuration de stockage Azure dans un formulaire adaptatif](#use-azure-storage-configuration-in-an-adaptive-form-use-azure-storage-configuartion-in-af) : connecte votre formulaire adaptatif aux conteneurs de stockage Azure configurés.

### Créer un conteneur de stockage Azure Blob {#create-azure-configuration}

Pour connecter AEM Forms à vos conteneurs de stockage Azure :

1. Accédez à l’instance de **création AEM Forms** > **[!UICONTROL Outils]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Stockage Azure]**.
1. Sélectionnez **[!UICONTROL Stockage Azure]** pour accéder au **[!UICONTROL Navigateur de stockage Azure]**.
1. Sélectionnez un **conteneur de configuration**. La configuration est stockée dans le conteneur de configuration sélectionné.
1. Cliquez sur **[!UICONTROL Créer]**. L’assistant Créer une configuration de stockage Azure s’affiche.

   ![Configuration du stockage Azure](/help/forms/assets/azure-storage-configuration.png)

1. Spécifiez le **[!UICONTROL titre]**, le **[!UICONTROL compte de stockage Azure]** et la **[!UICONTROL clé d’accès Azure]**.

   * Vous pouvez récupérer le nom du `Azure Storage Account` et la `Azure Access key` à partir des comptes de stockage sur le portail Microsoft® Azure.
<!--

    >[!NOTE]
    >
    > The URL for **[!UICONTROL Azure Blob Endpoint]** is automatically appended to the textbox when a value is entered for **[!UICONTROL Azure Storage Account]**. You can update the Azure Blob End Point URL with your custom domain. Steps to update URL for **[!UICONTROL Azure Blob End Point]**:
    > 1. [Enable the AEM Advance Networking VPN support](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/advanced-networking.html?lang=fr)
    > 1. [Enable dedicated egress IP link](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/advanced-networking.html?lang=fr)
    > 1. [Map custom domain to azure blob storage](https://learn.microsoft.com/en-us/azure/storage/blobs/storage-custom-domain-name?tabs=azure-portal)
-->

1. Cliquez sur **[!UICONTROL Enregistrer]**.

Désormais, vous pouvez utiliser cette configuration de conteneur de stockage Azure pour l’action d’envoi dans un formulaire adaptatif.

### Utiliser la configuration de stockage Azure dans un formulaire adaptatif {#use-azure-storage-configuartion-in-af}

Vous pouvez utiliser la configuration de conteneur de stockage Azure créée dans un formulaire adaptatif pour enregistrer des données ou un document d’enregistrement généré dans le conteneur de stockage Azure.

>[!NOTE]
>
> * Sélectionnez le même [!UICONTROL conteneur de configuration] pour le formulaire adaptatif dans lequel vous avez créé votre espace de stockage OneDrive.
> * Si aucun [!UICONTROL conteneur de configuration] n’est sélectionné, les dossiers de [!UICONTROL configuration de stockage] globaux s’affichent dans la fenêtre des propriétés de l’action d’envoi.

>[!BEGINTABS]

>[!TAB Composant de base]

Suivez les étapes suivantes pour utiliser la configuration de conteneur de stockage Azure dans un formulaire adaptatif basé sur les composants de base comme suit :

1. Ouvrez le formulaire adaptatif pour le modifier et accéder à la section **[!UICONTROL Envoi]** des propriétés du Conteneur de formulaires adaptatifs.
1. Dans la liste déroulante **[!UICONTROL Action d’envoi]**, sélectionnez **[!UICONTROL Envoyer au stockage Azure Blob]**.

   ![GIF de stockage Blob Azure](/help/forms/assets/submit-to-azure-blob-fc.png){width=50%,height=50%}

   Vous pouvez également enregistrer un document d’enregistrement (DE) dans le stockage Blob Azure.

1. Sélectionnez la **[!UICONTROL configuration de stockage]** où vous souhaitez enregistrer vos données.
1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les paramètres d’envoi.

Lorsque vous envoyez le formulaire, les données sont enregistrées dans la configuration de conteneur de stockage Azure spécifié.
La structure du dossier pour l’enregistrement des données est `/configuration_container/form_name/year/month/date/submission_id/data`.

>[!TAB Composant principal]

Pour utiliser la configuration de conteneur de stockage Azure dans un formulaire adaptatif basé sur les composants principaux en tant que :

1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La fenêtre du conteneur de formulaires adaptatifs s’ouvre.
1. Cliquez sur l’onglet **[!UICONTROL Envoi]**.
1. Dans la liste déroulante **[!UICONTROL Action d’envoi]**, sélectionnez **[!UICONTROL Envoyer au stockage Azure Blob]**.

   ![GIF de stockage Azure Blob](/help/forms/assets/azure-submit-video.gif)

   Vous pouvez également enregistrer un document d’enregistrement (DE) dans le stockage Blob Azure.

1. Sélectionnez la **[!UICONTROL configuration de stockage]** où vous souhaitez enregistrer vos données.
1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les paramètres d’envoi.

Lorsque vous envoyez le formulaire, les données sont enregistrées dans la configuration de conteneur de stockage Azure spécifié.
La structure du dossier pour l’enregistrement des données est `/configuration_container/form_name/year/month/date/submission_id/data`.

>[!TAB Éditeur universel]

Pour utiliser la configuration de conteneur de stockage Azure dans un formulaire adaptatif créé dans l’éditeur universel, procédez comme suit :

1. Ouvrez le formulaire adaptatif pour le modifier.
1. Cliquez sur l’extension **Modifier les propriétés du formulaire** dans l’éditeur.
La boîte de dialogue **Propriétés du formulaire** s’affiche.

   >[!NOTE]
   >
   > * Si l’icône **Modifier les propriétés de formulaire** ne s’affiche pas dans l’interface de l’éditeur universel, activez l’extension **Modifier les propriétés de formulaire** dans Extension Manager.
   > * Consultez l’article [Caractéristiques des fonctionnalités d’Extension Manager](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) pour savoir comment activer ou désactiver les extensions dans l’éditeur universel.

1. Cliquez sur l’onglet **Envoi** et sélectionnez l’action d’envoi **[!UICONTROL Envoyer au stockage Azure Blob]**.
   ![Stockage Blob Azure.](/help/forms/assets/azure-blob-storage-ue.png)

   Si vous sélectionnez **Enregistrer les pièces jointes avec le nom d’origine**, les pièces jointes sont stockées dans le dossier à l’aide de leurs noms de fichier d’origine. Vous pouvez également enregistrer un document d’enregistrement (DE) dans le stockage Blob Azure.

1. Sélectionnez la **[!UICONTROL configuration de stockage]** où vous souhaitez enregistrer vos données.
1. Cliquez sur **[!UICONTROL Enregistrer et fermer]** pour enregistrer les paramètres d’envoi.

Lorsque vous envoyez le formulaire, les données sont enregistrées dans la configuration de conteneur de stockage Azure spécifié.
La structure du dossier pour l’enregistrement des données est `/configuration_container/form_name/year/month/date/submission_id/data`.

>[!ENDTABS]

## Articles connexes

{{af-submit-action}}
