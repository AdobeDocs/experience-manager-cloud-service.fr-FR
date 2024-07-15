---
title: Comment configurer Microsoft Dynamics 365 et Salesforce des modèles de données de formulaire prêts à l’emploi pour Forms adaptatif ?
description: Découvrez comment intégrer Microsoft Dynamics 365 et Salesforce à Adaptive Forms.
feature: Adaptive Forms, Form Data Model
role: User, Developer
exl-id: 2a43b2db-2dfb-4c79-88be-ea770b44dac1
source-git-commit: 7b31a2ea016567979288c7a8e55ed5bf8dfc181d
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 58%

---

# Configuration de Microsoft® Dynamics 365 ou Salesforce pour AEM Forms {#configure-azure-storage}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/oauth2-client-credentials-flow-for-server-to-server-integration.html) |
| AEM as a Cloud Service | Cet article |

[[!DNL Experience Manager Forms] Data Integration](data-integration.md) fournit des services cloud [!DNL Microsoft® Dynamics 365] et [!DNL Salesforce] pour intégrer des formulaires adaptatifs à un modèle de données de formulaire prêt à l’emploi (FDM). Les formulaires adaptatifs peuvent alors interagir avec les serveurs [!DNL Microsoft® Dynamics 365] et [!DNL Salesforce] pour activer les workflows métier. Par exemple :

* Écrire des données dans [!DNL Microsoft® Dynamics 365] et [!DNL Salesforce] lors de la soumission de formulaires adaptatifs.
* Écrivez des données dans [!DNL Microsoft® Dynamics 365] et [!DNL Salesforce] par le biais d’entités personnalisées définies dans le modèle de données de formulaire (FDM) et inversement.
* Interroger des données sur un serveur [!DNL Microsoft® Dynamics 365] et [!DNL Salesforce] pour préremplir des formulaires adaptatifs.
* Lire des données à partir de serveurs [!DNL Microsoft® Dynamics 365] et [!DNL Salesforce].

[!DNL Microsoft® Dynamics 365] et [!DNL Salesforce] les services cloud et le modèle de données de formulaire (FDM) sont disponibles prêts à l’emploi sur le serveur [!DNL AEM Forms] après avoir [ configuré un projet de développement pour Forms sur la base de l’archétype Experience Manager ](setup-local-development-environment.md#forms-cloud-service-local-development-environment).

>[!NOTE]
>
>Les services cloud Microsoft® Dynamics 365 et [!DNL Salesforce] et le modèle de données de formulaire (FDM) ne sont disponibles prêt à l’emploi que si vous configurez un projet [!DNL Experience Manager Forms] en tant que [!DNL Cloud Service] basé sur [AEM Archetype 30](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-30) ou une version ultérieure.

## Configuration du service cloud [!DNL Salesforce] {#configure-salesforce-cloud-service}

Avant de configurer les services cloud [!DNL Salesforce], assurez-vous d’effectuer les tâches suivantes :

* [Créez une application connectée [!DNL Salesforce] compatible OAuth](https://help.salesforce.com/s/articleView?id=sf.connected_app_create_api_integration.htm&amp;type=5). Lorsque vous créez l’application [!DNL Salesforce] connectée, spécifiez l’URL de rappel au format suivant :

  ```
  https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html
  ```

  Où le serveur et le port se rapportent au nom d’hôte et au numéro de port du serveur [!DNL AEM Forms].

* Lors de la création de l’application [!DNL Salesforce] connectée, spécifiez `full` et `offline_access` comme valeurs de portée OAuth.

* Notez les valeurs de l’ID client (appelé clé du client) et du secret client pour l’application connectée.

Pour configurer le service cloud [!DNL Salesforce], procédez comme suit :

1. Sur l’instance d’auteur [!DNL AEM Forms], accédez à **[!UICONTROL Outils]** ![marteau](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Sources de données]**. La liste des dossiers de wrapper disponibles inclut un dossier avec le titre `DappTitle` tout en [générant le projet d’archétype d’AEM](setup-local-development-environment.md#forms-cloud-service-local-development-environment).
1. Sélectionnez le nom du dossier, sélectionnez **[!UICONTROL Salesforce Cloud Config]**, puis **[!UICONTROL Propriétés]**.
1. Dans l’onglet **[!UICONTROL Paramètres d’authentification]** :
   1. Spécifiez l’URL du domaine [!DNL Salesforce] dans le champ **[!UICONTROL Hôte]**. Par exemple, [nom-de-domaine].my.salesforce.com.
   1. Indiquez l’ID client (appelé clé du client) et le secret client pour l’application connectée.
   1. Spécifiez **full offline_access** (valeurs `full` et `offine_access` séparées par un espace) dans le champ **[!UICONTROL Champ d’application de l’autorisation]**.
   1. Sélectionnez **[!UICONTROL Se connecter à OAuth]**. Vous êtes redirigé vers la page de connexion de [!DNL Microsoft® Dynamics].
   1. Connectez-vous avec vos informations d’identification [!DNL Salesforce] et autorisez la connexion de la configuration du service cloud au service [!DNL Salesforce]. Si la connexion est établie, vous êtes redirigé vers la page de configuration du service cloud [!DNL Salesforce], qui affiche un message de réussite.
1. Sélectionnez **[!UICONTROL Enregistrer et fermer]** pour terminer la configuration.

### Accès au modèle de données de formulaire (FDM) prêt à l’emploi [!DNL Salesforce]

Un modèle de données de formulaire (FDM) [!DNL Salesforce] est disponible prêt à l’emploi sur le serveur [!DNL AEM Forms] après avoir [ configuré un projet de développement pour Forms en fonction de l’archétype Experience Manager ](setup-local-development-environment.md#forms-cloud-service-local-development-environment).

Pour accéder au modèle de données de formulaire (FDM), accédez à **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Intégrations de données]**. La liste des dossiers de disponibles inclut un dossier avec le titre `DappTitle` tout en [générant le projet d’archétype d’AEM](setup-local-development-environment.md#forms-cloud-service-local-development-environment). Sélectionnez le nom du dossier, le **[!UICONTROL modèle de données Salesforce]** et l’icône Edit ![Edit](assets/edit.png) pour afficher le modèle de données de formulaire (FDM).

Après avoir configuré le service de configuration du cloud [[!DNL Salesforce] ](#configure-salesforce-cloud-service), vous pouvez intégrer des formulaires adaptatifs avec le modèle de données [!DNL Salesforce] prêt à l’emploi.

## Configuration du service cloud [!DNL Microsoft® Dynamics 365] {#configure-dynamics-cloud-service}

Avant de configurer le service cloud [!DNL Microsoft® Dynamics 365], assurez-vous d’effectuer les tâches suivantes :

* [Enregistrez une application pour [!DNL Microsoft® Dynamics 365] avec l’Active Directory Azure](https://docs.microsoft.com/fr-fr/powerapps/developer/data-platform/walkthrough-register-app-azure-active-directory). Lorsque vous créez l’application connectée [!DNL Microsoft® Dynamics 365], spécifiez les URL de réponse au format suivant :

  ```
  https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html
  ```

  Où le serveur et le port se rapportent au nom d’hôte et au numéro de port du serveur [!DNL AEM Forms].

* Notez les valeurs de l’ID client (également appelé « ID d’application ») et du secret du client pour l’application connectée.

Pour configurer le service cloud [!DNL Microsoft® Dynamics 365], procédez comme suit :

1. Sur l’instance d’auteur [!DNL AEM Forms], accédez à **[!UICONTROL Outils]** ![marteau](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Sources de données]**. La liste des dossiers de wrapper disponibles inclut un dossier avec le titre `DappTitle` tout en [générant le projet d’archétype d’AEM](setup-local-development-environment.md#forms-cloud-service-local-development-environment).
1. Sélectionnez le nom du dossier, sélectionnez **[!UICONTROL Microsoft® Dynamics 365 Cloud Config]**, puis **[!UICONTROL Propriétés]**.
1. Dans l’onglet **[!UICONTROL Paramètres d’authentification]** :
   1. Saisissez la valeur du champ **[!UICONTROL Racine du service]**. Accédez à l’instance Dynamics et à [Ressources de développement](https://docs.microsoft.com/fr-fr/powerapps/developer/data-platform/view-download-developer-resources) pour afficher la valeur du champ Racine du service. Par exemple, `https://<tenant-name>.dynamics.com/api/data/v9.1/`
   1. Spécifiez l’ID client (appelé ID d’application) et le secret client pour l’application connectée.
   1. Remplacez `{tenant}` par un ID client dans les champs **[!UICONTROL URL OAuth]**, **[!UICONTROL URL du jeton d’actualisation]** et **[!UICONTROL URL de jeton d’accès]**.
   1. Spécifiez l’URL de l’instance de dynamique dans le champ **[!UICONTROL Resource]** pour configurer [!UICONTROL Microsoft® Dynamics] avec un modèle de données de formulaire (FDM). Utilisez l’URL racine du service pour dériver l’URL de l’instance dynamique. Par exemple, `https://<tenant-name>.dynamics.com`.

   1. Spécifiez `openid` dans le champ **[!UICONTROL Champ d’application de l’autorisation]** pour la procédure d’autorisation sur [!DNL Microsoft® Dynamics 365].
   1. Connectez-vous avec vos informations d’identification [!DNL Microsoft® Dynamics 365] et autorisez la connexion de la configuration du service cloud au service [!DNL Microsoft® Dynamics 365]. Si la connexion est établie, vous êtes redirigé vers la page de configuration du service cloud [!DNL Microsoft® Dynamics 365], qui affiche un message de réussite.
1. Sélectionnez **[!UICONTROL Enregistrer et fermer]** pour terminer la configuration.

### Accès au modèle de données de formulaire (FDM) prêt à l’emploi [!DNL Microsoft® Dynamics 365]

Un modèle de données de formulaire (FDM) [!DNL Microsoft® Dynamics 365] est disponible prêt à l’emploi sur le serveur [!DNL AEM Forms] après avoir [ configuré un projet de développement pour Forms en fonction de l’archétype Experience Manager ](setup-local-development-environment.md##forms-cloud-service-local-development-environment).

Pour accéder au modèle de données de formulaire (FDM), accédez à **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Intégrations de données]**. La liste des dossiers de disponibles inclut un dossier avec le titre `DappTitle` tout en [générant le projet d’archétype d’AEM](setup-local-development-environment.md#forms-cloud-service-local-development-environment). Sélectionnez le nom du dossier, sélectionnez le **[!UICONTROL Microsoft® Dynamics 365 Data Model]**, puis l’icône Edit ![Edit](assets/edit.png) pour afficher le modèle de données de formulaire (FDM).

Après avoir configuré le service de configuration du cloud [[!DNL Microsoft® Dynamics 365] ](#configure-dynamics-cloud-service), vous pouvez intégrer des formulaires adaptatifs avec le modèle de données [!DNL Microsoft® Dynamics 365] prêt à l’emploi.

>[!MORELIKETHIS]
>
>* [Configuration de sources de données pour AEM Forms](/help/forms/configure-data-sources.md)
>* [Configuration du stockage Azure pour AEM Forms](/help/forms/configure-azure-storage.md)
>  [Ajout du portail Forms à une page AEM Sites](/help/forms/configure-forms-portal.md)
