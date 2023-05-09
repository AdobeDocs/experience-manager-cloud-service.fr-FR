---
title: Comment configurer les modèles de données de formulaire prêts à l’emploi de Microsoft Dynamics 365 et Salesforce pour les formulaires adaptatifs ?
description: Découvrez comment intégrer Microsoft Dynamics 365 et Salesforce à des formulaires adaptatifs.
exl-id: 2a43b2db-2dfb-4c79-88be-ea770b44dac1
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '936'
ht-degree: 99%

---

# Configuration des services cloud [!DNL Microsoft Dynamics 365] et [!DNL Salesforce] {#configure-azure-storage}

L’[[!DNL Experience Manager Forms] intégration de données](data-integration.md) fournit des services cloud [!DNL Microsoft Dynamics 365] et [!DNL Salesforce] permettant d’intégrer des formulaires adaptatifs aux modèles de données de formulaire prêts à l’emploi. Les formulaires adaptatifs peuvent alors interagir avec les serveurs [!DNL Microsoft Dynamics 365] et [!DNL Salesforce] pour activer les workflows métier. Par exemple :

* Écrire des données dans [!DNL Microsoft Dynamics 365] et [!DNL Salesforce] lors de la soumission de formulaires adaptatifs.
* Écrire des données dans [!DNL Microsoft Dynamics 365] et [!DNL Salesforce] par le biais d’entités personnalisées définies dans un modèle de données de formulaire et inversement.
* Interroger des données sur un serveur [!DNL Microsoft Dynamics 365] et [!DNL Salesforce] pour préremplir des formulaires adaptatifs.
* Lire des données à partir de serveurs [!DNL Microsoft Dynamics 365] et [!DNL Salesforce].

Les services cloud [!DNL Microsoft Dynamics 365] et [!DNL Salesforce] et les modèles de données de formulaire sont disponibles prêts à l’emploi sur le serveur [!DNL AEM Forms] une fois que vous avez [configuré un projet de développement de formulaires basé sur l’archétype Experience Manager](setup-local-development-environment.md##forms-cloud-service-local-development-environment).

>[!NOTE]
>
>Les services cloud Microsoft Dynamics 365 et [!DNL Salesforce] et les modèles de données de formulaire ne sont disponibles prêts à l’emploi que si vous configurez un projet [!DNL Experience Manager Forms] as a [!DNL Cloud Service] basé sur un [Archétype AEM version 30](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-30) ou supérieure.

## Configuration du service cloud [!DNL Salesforce] {#configure-salesforce-cloud-service}

Avant de configurer les services cloud [!DNL Salesforce], assurez-vous d’effectuer les tâches suivantes :

* [Créez une application connectée [!DNL Salesforce] compatible OAuth](https://help.salesforce.com/s/articleView?id=sf.connected_app_create_api_integration.htm&amp;type=5). Lorsque vous créez l’application [!DNL Salesforce] connectée, spécifiez l’URL de rappel au format suivant :

   ```
   https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html
   ```

   Le serveur et le port doivent faire référence au nom d’hôte et au numéro de port du serveur [!DNL AEM Forms].

* Lors de la création de l’application [!DNL Salesforce] connectée, spécifiez `full` et `offline_access` comme valeurs de portée OAuth.

* Notez les valeurs de l’ID client (appelé clé du client) et du secret client pour l’application connectée.

Pour configurer le service cloud [!DNL Salesforce], procédez comme suit :

1. Sur l’instance d’auteur [!DNL AEM Forms], accédez à **[!UICONTROL Outils]** ![marteau](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Sources de données]**. La liste des dossiers de wrapper disponibles inclut un dossier avec le titre `DappTitle` tout en [générant le projet d’archétype d’AEM](setup-local-development-environment.md##forms-cloud-service-local-development-environment).
1. Appuyez sur le nom du dossier, sélectionnez **[!UICONTROL Configuration cloud Salesforce]**, puis appuyez sur **[!UICONTROL Propriétés]**.
1. Dans l’onglet **[!UICONTROL Paramètres d’authentification]** :
   1. Spécifiez l’URL du domaine [!DNL Salesforce] dans le champ **[!UICONTROL Hôte]**. Par exemple, [nom-de-domaine].my.salesforce.com.
   1. Indiquez l’ID client (appelé clé du client) et le secret client pour l’application connectée.
   1. Spécifiez **full offline_access** (valeurs `full` et `offine_access` séparées par un espace) dans le champ **[!UICONTROL Champ d’application de l’autorisation]**.
   1. Appuyez sur **[!UICONTROL Se connecter à OAuth]**. Vous êtes redirigé vers la page de connexion de [!DNL Microsoft Dynamics].
   1. Connectez-vous avec vos informations d’identification [!DNL Salesforce] et autorisez la connexion de la configuration du service cloud au service [!DNL Salesforce]. Si la connexion est établie, vous êtes redirigé vers la page de configuration du service cloud [!DNL Salesforce], qui affiche un message de réussite.
1. Appuyez sur **[!UICONTROL Enregistrer et fermer]** pour terminer la configuration.

### Accès au modèle de données de formulaire [!DNL Salesforce] prêt à l’emploi

Un modèle de données de formulaire [!DNL Salesforce] prêt à l’emploi est disponible sur le serveur [!DNL AEM Forms] après que vous avez [configuré un projet de développement de formulaires basé sur l’archétype Experience Manager](setup-local-development-environment.md##forms-cloud-service-local-development-environment).

Pour accéder au modèle de données de formulaire, accédez à **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Intégrations de données]**. La liste des dossiers de disponibles inclut un dossier avec le titre `DappTitle` tout en [générant le projet d’archétype d’AEM](setup-local-development-environment.md##forms-cloud-service-local-development-environment). Appuyez sur le nom du dossier, sélectionnez le **[!UICONTROL modèle de données Salesforce]**, puis appuyez sur l’icône Modifier ![Modifier](assets/edit.png) pour afficher le modèle de données de formulaire.

Après avoir configuré le service de configuration du cloud [[!DNL Salesforce] ](#configure-salesforce-cloud-service), vous pouvez intégrer des formulaires adaptatifs avec le modèle de données [!DNL Salesforce] prêt à l’emploi.

## Configuration du service cloud [!DNL Microsoft Dynamics 365] {#configure-dynamics-cloud-service}

Avant de configurer le service cloud [!DNL Microsoft Dynamics 365], assurez-vous d’effectuer les tâches suivantes :

* [Enregistrez une application pour [!DNL Microsoft Dynamics 365] avec l’Active Directory Azure](https://docs.microsoft.com/fr-fr/powerapps/developer/data-platform/walkthrough-register-app-azure-active-directory). Lorsque vous créez l’application connectée [!DNL Microsoft Dynamics 365], spécifiez les URL de réponse au format suivant :

   ```
   https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html
   ```

   Le serveur et le port doivent faire référence au nom d’hôte et au numéro de port du serveur [!DNL AEM Forms].

* Notez les valeurs de l’ID client (également appelé « ID d’application ») et du secret du client pour l’application connectée.

Pour configurer le service cloud [!DNL Microsoft Dynamics 365], procédez comme suit :

1. Sur l’instance d’auteur [!DNL AEM Forms], accédez à **[!UICONTROL Outils]** ![marteau](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Sources de données]**. La liste des dossiers de wrapper disponibles inclut un dossier avec le titre `DappTitle` tout en [générant le projet d’archétype d’AEM](setup-local-development-environment.md##forms-cloud-service-local-development-environment).
1. Appuyez sur le nom du dossier, sélectionnez **[!UICONTROL Configuration cloud Microsoft Dynamics 365]**, puis appuyez sur **[!UICONTROL Propriétés]**.
1. Dans l’onglet **[!UICONTROL Paramètres d’authentification]** :
   1. Saisissez la valeur de la variable **[!UICONTROL Racine du service]** champ . Accédez à l’instance Dynamics et à [Ressources de développement](https://docs.microsoft.com/fr-fr/powerapps/developer/data-platform/view-download-developer-resources) pour afficher la valeur du champ Racine du service. Par exemple, `https://<tenant-name>.dynamics.com/api/data/v9.1/`
   1. Spécifiez l’ID client (appelé ID d’application) et le secret client pour l’application connectée.
   1. Remplacez `{tenant}` par un ID client dans les champs **[!UICONTROL URL OAuth]**, **[!UICONTROL URL du jeton d’actualisation]** et **[!UICONTROL URL de jeton d’accès]**.
   1. Spécifiez l’URL de l’instance dynamique dans le champ **[!UICONTROL Ressource]** pour configurer [!UICONTROL Microsoft Dynamics] avec un modèle de données de formulaire. Utilisez l’URL racine du service pour dériver l’URL de l’instance dynamique. Par exemple, `https://<tenant-name>.dynamics.com`.

   1. Spécifiez `openid` dans le champ **[!UICONTROL Champ d’application de l’autorisation]** pour la procédure d’autorisation sur [!DNL Microsoft Dynamics 365].
   1. Connectez-vous avec vos informations d’identification [!DNL Microsoft Dynamics 365] et autorisez la connexion de la configuration du service cloud au service [!DNL Microsoft Dynamics 365]. Si la connexion est établie, vous êtes redirigé vers la page de configuration du service cloud [!DNL Microsoft Dynamics 365], qui affiche un message de réussite.
1. Appuyez sur **[!UICONTROL Enregistrer et fermer]** pour terminer la configuration.

### Accès au modèle de données de formulaire [!DNL Microsoft Dynamics 365] prêt à l’emploi

Un modèle de données de formulaire [!DNL Microsoft Dynamics 365] prêt à l’emploi est disponible sur le serveur [!DNL AEM Forms] après que vous avez [configuré un projet de développement de formulaires basé sur l’archétype Experience Manager](setup-local-development-environment.md##forms-cloud-service-local-development-environment).

Pour accéder au modèle de données de formulaire, accédez à **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Intégrations de données]**. La liste des dossiers de disponibles inclut un dossier avec le titre `DappTitle` tout en [générant le projet d’archétype d’AEM](setup-local-development-environment.md##forms-cloud-service-local-development-environment). Appuyez sur le nom du dossier, sélectionnez le **[!UICONTROL modèle de données Microsoft Dynamics 365]**, puis appuyez sur l’icône Modifier ![Modifier](assets/edit.png) pour afficher le modèle de données de formulaire.

Après avoir configuré le service de configuration du cloud [[!DNL Microsoft Dynamics 365] ](#configure-dynamics-cloud-service), vous pouvez intégrer des formulaires adaptatifs avec le modèle de données [!DNL Microsoft Dynamics 365] prêt à l’emploi.
