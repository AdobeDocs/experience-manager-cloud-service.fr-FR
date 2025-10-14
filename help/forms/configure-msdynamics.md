---
title: Comment configurer des modèles de données de formulaire prêts à l’emploi Microsoft Dynamics 365 pour les Forms adaptatifs ?
description: Découvrez comment intégrer Microsoft Dynamics 365 à Adaptive Forms.
feature: Adaptive Forms, Form Data Model
role: User, Developer
exl-id: 29ee324c-cd4c-403b-bb3d-b1eda8e8ad88
source-git-commit: 76301ca614ae2256f5f8b00c41399298c761ee33
workflow-type: tm+mt
source-wordcount: '915'
ht-degree: 9%

---


# Configuration de Microsoft® Dynamics 365 for AEM Forms

L’intégration de données Adobe Experience Manager Forms fournit une configuration de service cloud pour intégrer des formulaires au serveur Microsoft Dynamics. Il permet de créer un modèle de données de formulaire (FDM) basé sur les entités, les attributs et les services définis dans le service Microsoft Dynamics. Le modèle de données de formulaire (FDM) peut être utilisé pour créer des Forms adaptatives qui interagissent avec un serveur Microsoft Dynamics pour activer les processus métier. Par exemple :
* Demander des données au serveur Microsoft Dynamics et préremplir le Forms adaptatif.
* Écrire des données dans Microsoft Dynamics lors de l’envoi de formulaires adaptatifs.
* Écrire des données dans Microsoft Dynamics par le biais d’entités personnalisées définies dans un modèle de données de formulaire (FDM)

AEM as a Cloud Service propose différentes actions d’envoi prêtes à l’emploi pour gérer les envois de formulaires. Pour en savoir plus sur ces options, consultez l’article [Action d’envoi de formulaire adaptatif](/help/forms/configure-submit-actions-core-components.md).

<!-- 
[[!DNL Experience Manager Forms] Data Integration](data-integration.md) provides [!DNL Microsoft&reg; Dynamics 365] Cloud Services to integrate Adaptive Forms with out of the box Form Data Model (FDM). The Adaptive Forms can then interact with [!DNL Microsoft&reg; Dynamics 365] servers to enable business workflows. For example:

* Write data into [!DNL Microsoft&reg; Dynamics 365] on Adaptive Form submission.
* Write data in [!DNL Microsoft&reg; Dynamics 365] through custom entities defined in Form Data Model (FDM) and conversely.
* Query [!DNL Microsoft&reg; Dynamics 365]server for data and prepopulate Adaptive Forms.
* Read data from [!DNL Microsoft&reg; Dynamics 365] server.

[!DNL Microsoft&reg; Dynamics 365] cloud services and Form Data Model (FDM) are available out of the box on the [!DNL AEM Forms] Server after you [set up a development project for Forms based on Experience Manager archetype](setup-local-development-environment.md#forms-cloud-service-local-development-environment).

>[!NOTE]
>
>Microsoft&reg; Dynamics 365 cloud services and Form Data Model (FDM) are available out of the box only if you set up an [!DNL Experience Manager Forms] as a [!DNL Cloud Service] project based on [AEM Archetype 30](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-30) or later.-->

## Prérequis

Avant d’intégrer [!DNL Microsoft® Dynamics 365] à AEM Forms as a Cloud Service, vérifiez que vous avez effectué les étapes suivantes :


1. **Configuration du compte dans Microsoft Dynamics 365**

   Suivez les étapes décrites dans la vidéo pour configurer un compte Microsoft Dynamics 365. Dans cette vidéo, un compte d’évaluation est créé à des fins de démonstration.

   >[!VIDEO](https://video.tv.adobe.com/v/3444389/)

1. **Créer un compte dans le Centre d’administration Power Platform**
Créez un compte dans le **Centre d’administration Power Platform** pour :
   * Ajouter Dataverse
   * Activation des applications Microsoft Dynamics 365

   Suivez les étapes de la vidéo pour créer un compte dans le Centre d’administration Power Platform. Dans cette vidéo, un compte d’évaluation a été créé à des fins de démonstration.

   >[!VIDEO](https://video.tv.adobe.com/v/3444388)

1. **Enregistrer une application pour [!DNL Microsoft® Dynamics 365] dans Azure Active Directory**

   Suivez les étapes de la vidéo pour enregistrer une application à [!DNL Microsoft® Dynamics 365] dans Azure Active Directory.

   >[!VIDEO](https://video.tv.adobe.com/v/3444369/dynamics365integration-microsoftdynamics-apiaccess-azuread-appregistration)

   >[!NOTE]
   >
   > * Pour créer l’application [!DNL Microsoft® Dynamics 365] connectée, sélectionnez **Web** comme plateforme et indiquez l’**URI de redirection** au format suivant : `https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/fdm.html`.
   > * Veillez à enregistrer l’ID client (également appelé ID d’application) et le secret client pour une référence ultérieure.

## Connexion de Forms à Microsoft® Dynamics 365

Une fois que vous avez configuré les conditions préalables ci-dessus, vous pouvez poursuivre l’intégration de Forms adaptatif à Microsoft® Dynamics 365. Pour envoyer des données à Microsoft® Dynamics 365 lors de l’envoi du formulaire, procédez comme suit :

[1. Configuration du service cloud pour Microsoft Dynamics](#1-configure-cloud-service-configuration-for-microsoft-dynamics)

[2. Créer un modèle de données de formulaire (FDM)](#2-create-form-data-model-fdm)

### 1. Configuration du service cloud pour Microsoft Dynamics

>[!VIDEO](https://video.tv.adobe.com/v/3444370/cloudconfiguration-dataintegration-adobeexperiencemanager-aemforms-microsoftdynamics)

Pour configurer la configuration du service cloud [!DNL Microsoft® Dynamics 365], procédez comme suit :

1. Accédez à **[!UICONTROL Outils]** ![marteau](assets/hammer.png) > **[!UICONTROL Services cloud]** > **[!UICONTROL Sources de données]** sur [!DNL AEM Forms] instance de création,.

   ![Sélectionnez Cloud Data Source](/help/forms/assets/dynamics-data-source.png)
1. Sélectionnez un conteneur de configuration. La configuration est stockée dans le conteneur de configuration sélectionné.
1. Cliquez sur **[!UICONTROL Créer]**.

   ![Créer une configuration cloud](/help/forms/assets/dynamics-select-configuration.png)

   L’assistant de configuration **Créer une configuration de Source de données** s’affiche.

   ![Assistant Créer une configuration de Source de données](/help/forms/assets/dynamics-create-data-configuration.png)

1. Spécifiez les **[!UICONTROL Titre]** et **[!UICONTROL Nom]**, puis sélectionnez **[!UICONTROL Type de service]** en tant que **Service OData**.
1. Cliquez sur **[!UICONTROL Suivant]**. L’onglet **Authentification** s’affiche.

   ![Onglet Authentification](/help/forms/assets/dynamics-authentication-tab.png)

1. Spécifiez la valeur du champ **[!UICONTROL Racine du service]**.

   Accédez à votre instance Dynamics dans le **Centre d’administration Power Platform** et accédez à [Ressources de développement](https://docs.microsoft.com/fr-fr/powerapps/developer/data-platform/view-download-developer-resources) pour afficher la valeur de la racine du **service**. Le point d’entrée **API Web** représente la valeur **racine du service** de l’instance Dynamics que vous souhaitez intégrer au Forms adaptatif. L’URL **Racine du service** est au format suivant : `https://<tenant-name>.dynamics.com/api/data/v9.1/`

   ![&#x200B; Champ racine du service &#x200B;](/help/forms/assets/dynamics-service-root.png)

1. Sélectionnez le **[!UICONTROL Type d’authentification]** comme **OAuth2.0**.
1. Spécifiez les valeurs **ID client** (appelé ID d’application) et **Secret client** pour l’application connectée.
Vous pouvez récupérer l’**ID client** et le **Secret client** à partir de l’application Azure Active Directory.

   ![ID client et secret client](/help/forms/assets/dynamics-azure-app-resgistration.png)

1. Spécifiez les éléments suivants dans les champs **[!UICONTROL URL OAuth]**, **[!UICONTROL URL du jeton d’actualisation]** et **[!UICONTROL URL du jeton d’accès]**.
Vous pouvez récupérer les **[!UICONTROL URL OAuth]**, **[!UICONTROL URL du jeton d’actualisation]** et **[!UICONTROL URL du jeton d’accès]** dans la section **Points d’entrée** de votre application Azure Active Directory.

   ![Points d’entrée de l’application Azure](/help/forms/assets/dynamics-azure-app-endpoints.png)

1. Spécifiez `openid` dans le champ **[!UICONTROL Champ d’application de l’autorisation]** pour la procédure d’autorisation sur [!DNL Microsoft® Dynamics 365].
1. Spécifiez l’URL de l’instance dynamique dans le champ **[!UICONTROL Ressource]** pour configurer des [!DNL Microsoft® Dynamics 365] avec un modèle de données de formulaire (FDM).
Vous pouvez copier l’**URL de l’environnement** à partir du **Centre d’administration Power Platform** ou dériver l’URL de l’instance Dynamics à l’aide de l’URL **Racine du service**. L’URL de la ressource est au format suivant : `https://<tenant-name>.dynamics.com`.

   ![Champ de ressource de l’application Power](/help/forms/assets/dynamics-resource-field.png)

1. Connectez-vous avec vos informations d’identification [!DNL Microsoft® Dynamics 365] et autorisez la connexion de la configuration du service cloud au service [!DNL Microsoft® Dynamics 365]. Si la connexion est établie, vous êtes redirigé vers la page de configuration du service cloud [!DNL Microsoft® Dynamics 365], qui affiche un message de réussite.
1. Sélectionnez **[!UICONTROL Créer]** pour enregistrer la configuration.

### 2. Créer un modèle de données de formulaire (FDM)

>[!VIDEO](https://video.tv.adobe.com/v/3444367/aemforms-adobeexperiencemanager-formdatamodel--dataintegration-digitalforms)

Vous pouvez utiliser l’outil Créer le modèle de données de formulaire (FDM) à l’aide de la configuration cloud [!DNL Microsoft® Dynamics 365] créée. Pour créer un modèle de données de formulaire, procédez comme suit :

1. Accédez à **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Intégrations de données]**.
   ![Création d’un modèle de données de formulaire](/help/forms/assets/dynamics-create-fdm.png)

1. Cliquez sur **[!UICONTROL Créer]** et sélectionnez **[!UICONTROL Modèle de données de formulaire]**.
   ![Sélectionner le modèle de données de formulaire](/help/forms/assets/dynamics-select-fdm.png)

   L’assistant **Créer un modèle de données de formulaire** s’affiche.
1. Cliquez sur **[!UICONTROL Suivant]**.
1. Sélectionnez la configuration cloud créée dans l’onglet **Sélectionner la source de données**.
   ![Sélectionner la configuration du cloud](/help/forms/assets/dynamics-select-cloud-config.png)

1. Cliquez sur l’icône Modifier ![Modifier](assets/edit.png) pour afficher et configurer le modèle de données de formulaire (FDM).

Ensuite, vous pouvez [configurer le modèle de données de formulaire (FDM)](/help/forms/work-with-form-data-model.md#configure-services) et l’utiliser dans divers cas de formulaires adaptatifs, tels que :

* Remplir le formulaire adaptatif en obtenant des informations des entités et des services [!DNL Microsoft Dynamics]
* Appeler [!DNL Microsoft Dynamics] opérations du serveur définies dans un modèle de données de formulaire (FDM) à l’aide de règles de formulaire adaptatif
* Écrire les données de formulaire envoyées dans les entités [!DNL Microsoft Dynamics]
* Vous pouvez configurer l’action d’envoi de modèle de données de formulaire pour un formulaire adaptatif afin d’envoyer des données à [!DNL Microsoft Dynamics].

Vous pouvez ensuite utiliser l’option [Envoyer à l’aide du modèle de données de formulaire (FDM)](/help/forms/using-form-data-model.md) dans un **formulaire adaptatif** pour transférer les données de votre formulaire vers le [!DNL Microsoft® Dynamics 365] configuré.


>[!MORELIKETHIS]
>
>* [Configurer les sources de données pour AEM Forms](/help/forms/configure-data-sources.md)
>* [Configurer le stockage Azure pour AEM Forms](/help/forms/configure-azure-storage.md)
>  [Ajoutez Forms Portal à une page AEM Sites](/help/forms/configure-forms-portal.md)
