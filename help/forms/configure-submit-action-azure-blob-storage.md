---
Title: How to connect AEM Adaptive Forms with Azure Blob Storage?
Description: Learn how to create an Azure Blob Storage Configuration in AEM Forms and use it within your Adaptive Forms for efficient data storage.
keywords: Intégration du stockage Azure Blob avec AEM Forms, envoi de données vers le stockage Azure, création d’une configuration de stockage Azure dans AEM Forms, utilisation du stockage Azure Blob dans l’action d’envoi Adaptive Forms
feature: Adaptive Forms, Core Components
source-git-commit: 8784c0bcd05eeae41a472faa5ecad03cbdd8a9b6
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 62%

---


# Envoyer un formulaire adaptatif au stockage Azure Blob

L’action d’envoi **[!UICONTROL Envoyer au stockage Azure Blob]** connecte un formulaire adaptatif à un portail Microsoft® Azure. Vous pouvez envoyer les données de formulaire, les fichiers, les pièces jointes ou le document d’enregistrement aux conteneurs Azure Storage connectés.

AEM as a Cloud Service propose différentes actions d’envoi prêtes à l’emploi pour gérer les envois de formulaire. Pour en savoir plus sur ces options, voir [Action d’envoi de formulaire adaptatif](/help/forms/configure-submit-actions-core-components.md) article.

## Avantages

Voici quelques-uns des avantages de l’intégration du stockage Blob Azure à AEM Forms :

* Il permet de rationaliser le processus d’envoi de données de formulaire adaptatif, de fichiers, de pièces jointes et de document d’enregistrement aux conteneurs de stockage Azure.
* Il utilise Azure Blob Storage pour le stockage centralisé et organisé des envois de formulaires adaptatifs.

## Connexion d’AEM Forms à Microsoft® Azure Blob Storage

Pour utiliser le stockage Azure Blob dans l’action d’envoi Adaptive Forms :

1. [Créer un conteneur de stockage Azure Blob](#create-a-azure-blob-storage-container-create-azure-configuration) : connecte AEM Forms aux conteneurs de stockage Azure.
2. [Utilisation de la configuration de stockage Azure dans un formulaire adaptatif](#use-azure-storage-configuration-in-an-adaptive-form-use-azure-storage-configuartion-in-af): il connecte votre formulaire adaptatif aux conteneurs de stockage Azure configurés.

### Créer un conteneur de stockage Azure Blob {#create-azure-configuration}

Pour connecter AEM Forms à vos conteneurs de stockage Azure :
1. Accédez à l’instance de **création AEM Forms** > **[!UICONTROL Outils]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Stockage Azure]**.
1. Sélectionnez **[!UICONTROL Stockage Azure]** pour accéder au **[!UICONTROL Navigateur de stockage Azure]**.
1. Sélectionnez un **conteneur de configuration**. La configuration est stockée dans le conteneur de configuration sélectionné.
1. Cliquez sur **[!UICONTROL Créer]**. L’assistant Créer une configuration de stockage Azure s’affiche.

   ![Configuration du stockage Azure](/help/forms/assets/azure-storage-configuration.png)

1. Spécifiez le **[!UICONTROL titre]**, le **[!UICONTROL compte de stockage Azure]** et la **[!UICONTROL clé d’accès Azure]**.

   * Vous pouvez récupérer le nom du `Azure Storage Account` et la `Azure Access key` à partir des comptes de stockage sur le portail Microsoft® Azure.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

Désormais, vous pouvez utiliser cette configuration de conteneur de stockage Azure pour l’action d’envoi dans un formulaire adaptatif.

### Utiliser la configuration de stockage Azure dans un formulaire adaptatif {#use-azure-storage-configuartion-in-af}

Vous pouvez utiliser la configuration de conteneur de stockage Azure créée dans un formulaire adaptatif pour enregistrer des données ou un document d’enregistrement généré dans le conteneur de stockage Azure. Suivez les étapes ci-après pour utiliser la configuration de conteneur de stockage Azure dans un formulaire adaptatif :
1. Créez un [formulaire adaptatif](/help/forms/creating-adaptive-form-core-components.md).

   >[!NOTE]
   >
   > * Sélectionnez le même [!UICONTROL conteneur de configuration] pour le formulaire adaptatif dans lequel vous avez créé votre espace de stockage OneDrive.
   > * Si aucun [!UICONTROL conteneur de configuration] n’est sélectionné, les dossiers de [!UICONTROL configuration de stockage] globaux s’affichent dans la fenêtre des propriétés de l’action d’envoi.

1. Sélectionnez l’**action Envoyer** pour **[!UICONTROL Soumettre au stockage Azure Blob]**.
   ![GIF de stockage Azure Blob](/help/forms/assets/azure-submit-video.gif)

1. Sélectionnez la **[!UICONTROL configuration de stockage]** où vous souhaitez enregistrer vos données.
1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer les paramètres d’envoi.

Lorsque vous envoyez le formulaire, les données sont enregistrées dans la configuration de conteneur de stockage Azure spécifié.
La structure du dossier pour l’enregistrement des données est `/configuration_container/form_name/year/month/date/submission_id/data`.

## Articles connexes

{{af-submit-action}}