---
title: Comment configurer des modèles de données de formulaires prêts à l’emploi Salesforce pour les Forms adaptatifs ?
description: Découvrez comment intégrer Salesforce à Adaptive Forms.
feature: Adaptive Forms, Form Data Model
role: User, Developer
exl-id: 184db05b-7237-4dce-8059-03c39b93d7d7
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 44%

---

# Configuration de Salesforce pour AEM Forms {#configure-azure-storage}

L’intégration de données [[!DNL Experience Manager Forms] Data Integration](data-integration.md) fournit [!DNL Salesforce] Cloud Services pour intégrer le Forms adaptatif au modèle de données de formulaire (FDM) prêt à l’emploi. Le Forms adaptatif peut ensuite interagir avec les serveurs [!DNL Salesforce] pour activer les workflows métier. Par exemple :

* Écrire des données dans [!DNL Salesforce] sur un envoi de formulaires adaptatifs.
* Écrivez des données dans [!DNL Salesforce] par le biais d’entités personnalisées définies dans le modèle de données de formulaire (FDM) et inversement.
* Demander des données à un serveur [!DNL Salesforce] et préremplir des formulaires adaptatifs.
* Lire des données à partir du serveur [!DNL Salesforce].

[!DNL Salesforce] services cloud et le modèle de données de formulaire (FDM) sont disponibles prêts à l’emploi sur le serveur [!DNL AEM Forms] après que vous avez [configuré un projet de développement pour Forms basé sur l’archétype Experience Manager](setup-local-development-environment.md#forms-cloud-service-local-development-environment).

>[!NOTE]
>
>[!DNL Salesforce] services cloud et le modèle de données de formulaire (FDM) ne sont disponibles prêts à l’emploi que si vous configurez un projet [!DNL Experience Manager Forms] as a [!DNL Cloud Service] basé sur [l’archétype AEM version 30](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-30) ou ultérieure.

## Configuration du service cloud [!DNL Salesforce] {#configure-salesforce-cloud-service}

Avant de configurer les services cloud [!DNL Salesforce], assurez-vous d’effectuer les tâches suivantes :

* [Créez une application connectée [!DNL Salesforce] compatible OAuth](https://help.salesforce.com/s/articleView?id=sf.connected_app_create_api_integration.htm&type=5). Lorsque vous créez l’application [!DNL Salesforce] connectée, spécifiez l’URL de rappel au format suivant :

  ```
  https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html
  ```

  Où serveur et port font référence au nom d’hôte et au numéro de port du serveur [!DNL AEM Forms].

* Lors de la création de l’application [!DNL Salesforce] connectée, spécifiez `full` et `offline_access` comme valeurs de portée OAuth.

* Notez les valeurs de l’ID client (appelé clé du client) et du secret client pour l’application connectée.

Pour configurer le service cloud [!DNL Salesforce], procédez comme suit :

1. Sur [!DNL AEM Forms] instance d’auteur, accédez à **[!UICONTROL Outils]** ![marteau](assets/hammer.png) > **[!UICONTROL Services cloud]** > **[!UICONTROL Sources de données]**.
2. Sélectionnez le nom du dossier, sélectionnez **[!UICONTROL Configuration cloud Salesforce]** puis **[!UICONTROL Propriétés]**.
3. Dans l’onglet **[!UICONTROL Paramètres d’authentification]** :
   1. Spécifiez l’URL du domaine [!DNL Salesforce] dans le champ **[!UICONTROL Hôte]**. Par exemple, [nom-de-domaine].my.salesforce.com.
   2. Indiquez l’ID client (appelé clé du client) et le secret client pour l’application connectée.
   3. Spécifiez **full offline_access** (valeurs `full` et `offine_access` séparées par un espace) dans le champ **[!UICONTROL Champ d’application de l’autorisation]**.
   4. Sélectionnez **[!UICONTROL Se connecter à OAuth]**. Vous êtes redirigé vers la page de connexion de [!DNL Salesforce].
   5. Connectez-vous avec vos informations d’identification [!DNL Salesforce] et autorisez la connexion de la configuration du service cloud au service [!DNL Salesforce]. Si la connexion est établie, vous êtes redirigé vers la page de configuration du service cloud [!DNL Salesforce], qui affiche un message de réussite.
4. Sélectionnez **[!UICONTROL Enregistrer et fermer]** pour terminer la configuration.

### Accès prêt à l’emploi [!DNL Salesforce] modèle de données de formulaire (FDM)

Un modèle de données de formulaire [!DNL Salesforce] (FDM) prêt à l’emploi est disponible sur le serveur [!DNL AEM Forms] après que vous avez [configuré un projet de développement pour Forms basé sur l’archétype Experience Manager](setup-local-development-environment.md#forms-cloud-service-local-development-environment).

Pour accéder au modèle de données de formulaire (FDM) :

1. Accédez à **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Intégrations de données]**.
1. Sélectionnez le nom du dossier, sélectionnez le **[!UICONTROL modèle de données de Salesforce]**, puis sélectionnez l’icône Modifier ![Modifier](assets/edit.png) pour afficher le modèle de données de formulaire (FDM).

Après avoir configuré le service de configuration du cloud [[!DNL Salesforce] &#x200B;](#configure-salesforce-cloud-service), vous pouvez intégrer des formulaires adaptatifs avec le modèle de données [!DNL Salesforce] prêt à l’emploi.

>[!MORELIKETHIS]
>
>* [Configurer les sources de données pour AEM Forms](/help/forms/configure-data-sources.md)
>* [Configurer le stockage Azure pour AEM Forms](/help/forms/configure-azure-storage.md)
>  [Ajoutez Forms Portal à une page AEM Sites](/help/forms/configure-forms-portal.md)
