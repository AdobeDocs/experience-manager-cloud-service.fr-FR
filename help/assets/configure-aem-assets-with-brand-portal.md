---
title: Configuration du service cloud AEM Assets avec Brand Portal
description: Configurez le service cloud AEM Assets avec Brand Portal.
contentOwner: Vishabh Gupta
translation-type: tm+mt
source-git-commit: f54f5bbd5de76c3507d86b92255f1d4713e717fc
workflow-type: tm+mt
source-wordcount: '1762'
ht-degree: 99%

---


# Configuration d’AEM Assets avec Brand Portal {#configure-aem-assets-with-brand-portal}

Adobe Experience Manager (AEM) Assets est configuré avec Brand Portal via Adobe Developer Console, qui fournit un jeton IMS pour autoriser votre client Brand Portal.

**Comment fonctionne la configuration ?**

La configuration de l’instance cloud AEM Assets avec un client Brand Portal (organisation) nécessite des configurations à la fois dans l’instance cloud AEM Assets et dans Adobe Developer Console.

1. Dans l’instance cloud AEM Assets, créez un compte IMS et générez un certificat public (clé publique).
1. Dans Adobe Developer Console, créez un projet pour votre client Brand Portal (organisation).
1. Dans le projet, configurez une API à l’aide de la clé publique pour créer une connexion au compte de service (JWT).
1. Obtenez les informations d’identification du compte de service et les informations de charge utile JWT.
1. Dans l’instance cloud AEM Assets, configurez le compte IMS à l’aide des informations d’identification du compte de service et de la charge utile JWT.
1. Dans l’instance cloud AEM Assets, configurez le service cloud Brand Portal à l’aide du compte IMS et du point d’entrée Brand Portal (URL de l’organisation).
1. Testez la configuration en publiant une ressource de l’instance cloud AEM Assets sur Brand Portal.

>[!NOTE]
>
>Un client Brand Portal ne doit être configuré qu’avec une seule instance cloud AEM Assets.
>
>Ne configurez pas un client Brand Portal avec plusieurs instances cloud AEM Assets.


## Conditions préalables {#prerequisites}

Pour configurer AEM Assets avec Brand Portal, vous devez disposer des éléments suivants :

* Une instance cloud AEM Assets en cours d’exécution
* L’adresse URL du client Brand Portal
* Un utilisateur disposant de droits d’administrateur système sur l’organisation IMS du client Brand Portal

**Contactez l’assistance clientèle** pour toute autre question.

## Création d’une configuration {#create-new-configuration}

Procédez comme suit dans la séquence spécifiée pour configurer l’instance cloud AEM Assets avec Brand Portal.

1. [Obtention d’un certificat public](#public-certificate)
1. [Création d’une connexion au compte de service (JWT)](#createnewintegration)
1. [Configuration du compte IMS](#create-ims-account-configuration)
1. [Configuration du service cloud](#configure-the-cloud-service)
1. [Test de la configuration](#test-configuration)

### Création de la configuration IMS {#create-ims-configuration}

La configuration IMS authentifie votre locataire du portail de marque avec l’instance de cloud AEM Assets.

La configuration IMS comprend deux étapes :

* [Obtention d’un certificat public](#public-certificate)
* [Configuration du compte IMS](#create-ims-account-configuration)

### Obtention d’un certificat public {#public-certificate}

Un certificat public permet d’authentifier votre profil sur Adobe Developer Console.

1. Connectez-vous à votre instance cloud AEM Assets.

1. Dans le panneau **Outils** ![Outils](assets/tools.png), accédez à **[!UICONTROL Sécurité]** > **[!UICONTROL Configurations d’Adobe IMS]**.

   ![Interface utilisateur de configuration du compte Adobe IMS](assets/ims-configuration1.png)

1. Dans la page Configurations d’Adobe IMS, cliquez sur **[!UICONTROL Créer]**.

1. Vous êtes redirigé vers la page **[!UICONTROL Configuration du compte technique Adobe IMS]**. Par défaut, l’onglet **Certificat** s’ouvre.

   Sélectionnez la solution cloud **[!UICONTROL Adobe Brand Portal]**.

1. Cochez la case **[!UICONTROL Créer un certificat]** et spécifiez un **alias** pour le certificat. L’alias sert de nom à la boîte de dialogue.

1. Cliquez sur **[!UICONTROL Créer un certificat]**. Cliquez ensuite sur **[!UICONTROL OK]** dans la boîte de dialogue pour générer le certificat public.

   ![Création d’un certificat](assets/ims-config2.png)

1. Cliquez sur **[!UICONTROL Télécharger la clé publique]** et enregistrez le fichier de certificat (.crt) sur votre ordinateur.

   Le fichier de certificat sera utilisé à d’autres étapes pour configurer l’API de votre client Brand Portal et générer les informations d’identification de compte de service dans Adobe Developer Console.

   ![Téléchargement du certificat](assets/ims-config3.png)

1. Cliquez sur **[!UICONTROL Suivant]**.

   Dans l’onglet **Compte**, vous créez le compte Adobe IMS. Pour ce faire, vous aurez besoin des informations d’identification du compte de service générées dans Adobe Developer Console. Gardez cette page ouverte pour l’instant.

   Ouvrez un nouvel onglet et [créez une connexion au compte de service (JWT) dans Adobe Developer Console](#createnewintegration) pour obtenir les informations d’identification et la charge utile JWT qui servent à configurer le compte IMS.

### Création d’une connexion au compte de service (JWT) {#createnewintegration}

Dans Adobe Developer Console, les projets et les API sont configurés au niveau de l’organisation (client Brand Portal). La configuration d’une API crée une connexion au compte de service (JWT) dans Adobe Developer Console. Il existe deux méthodes pour configurer l’API : générer une paire de clés (clés privée et publique) ou télécharger une clé publique. Pour configurer l’instance cloud AEM Assets avec Brand Portal, vous devez générer un certificat public (clé publique) dans l’instance cloud AEM Assets et créer des informations d’identification dans Adobe Developer Console en chargeant la clé publique. Cette clé publique permet de configurer l’API pour l’organisation Brand Portal sélectionnée et de générer les informations d’identification ainsi que la charge utile JWT pour le compte de service. Ces informations d’identification sont également utilisées pour configurer le compte IMS dans l’instance cloud AEM Assets. Une fois le compte IMS configuré, vous pouvez configurer le service cloud Brand Portal dans l’instance cloud AEM Assets.

Procédez comme suit pour générer les informations d’identification du compte de service et la charge utile JWT :

1. Connectez-vous à Adobe Developer Console avec les privilèges d’administrateur système sur l’organisation IMS (client Brand Portal). L’URL par défaut est

   [https://www.adobe.com/go/devs_console_ui_fr](https://www.adobe.com/go/devs_console_ui_fr)


   >[!NOTE]
   >
   >Assurez-vous d’avoir sélectionné l’organisation IMS appropriée (client Brand Portal) dans la liste déroulante (liste d’organisations) située dans l’angle supérieur droit.

1. Cliquez sur **[!UICONTROL Créer un projet]**. Un projet vierge est créé pour votre organisation.

   Cliquez sur **[!UICONTROL Modifier le projet]** pour mettre à jour le **[!UICONTROL Titre du projet]** et la **[!UICONTROL Description]**, puis cliquez sur **[!UICONTROL Enregistrer]**.

   ![Créer un projet](assets/service-account1.png)

1. Dans l’onglet Aperçu du projet, cliquez sur **[!UICONTROL Ajouter une API]**.

   ![Ajouter une API](assets/service-account2.png)

1. Dans la fenêtre Ajouter une API, sélectionnez **[!UICONTROL AEM Brand Portal]**, puis cliquez sur **[!UICONTROL Suivant]**.

   Assurez-vous d’avoir accès au service AEM Brand Portal.

1. Dans la fenêtre Configurer l’API, cliquez sur **[!UICONTROL Charger votre clé publique]**. Cliquez ensuite sur **[!UICONTROL Sélectionner un fichier]** et chargez le certificat public (fichier .crt) que vous avez téléchargé comme indiqué à la section [Obtention d’un certificat public](#public-certificate).

   Cliquez sur **[!UICONTROL Suivant]**.

   ![Charger la clé publique](assets/service-account3.png)

1. Vérifiez le certificat public et cliquez sur **[!UICONTROL Suivant]**.

1. Sélectionnez le profil de produit par défaut **[!UICONTROL Assets Brand Portal]**, puis cliquez sur **[!UICONTROL Enregistrer la configuration]**.

   <!-- 
   In Brand Portal, a default profile is created for each organization. The Product Profiles are created in admin console for assigning users to groups (based on the roles and permissions). For configuration with Brand Portal, the OAuth token is created at organization level. Therefore, you must configure the default Product Profile for your organization. 
   -->

   ![Sélectionner le profil de produit](assets/service-account4.png)

1. Une fois l’API configurée, vous êtes redirigé vers l’aperçu de l’API. Dans le volet de navigation de gauche, sous **[!UICONTROL Informations d’identification]**, cliquez sur **[!UICONTROL Compte de service (JWT)]**.

   >[!NOTE]
   >
   >Vous pouvez voir les informations d’identification et effectuer d’autres actions (générer des jetons JWT, copier les informations d’identification, récupérer le secret client, etc.), si nécessaire.

1. Dans l’onglet **[!UICONTROL Informations d’identification client]**, copiez l’**[!UICONTROL ID client]**.

   Cliquez sur **[!UICONTROL Récupérer le secret client]** et copiez le **[!UICONTROL secret client]**.

   ![Informations d’identification du compte de service](assets/service-account5.png)

1. Accédez à l’onglet **[!UICONTROL Générer le jeton JWT]** et copiez la **[!UICONTROL Charge utile JWT]**.

Vous pouvez maintenant utiliser l’ID client (clé d’API), le secret client et la charge utile JWT pour [configurer le compte IMS](#create-ims-account-configuration) dans l’instance cloud AEM Assets.

<!--
1. Click **[!UICONTROL Create Integration]**.

1. Select **[!UICONTROL Access an API]**, and click **[!UICONTROL Continue]**.

   ![Create New Integration](assets/create-new-integration1.png)

1. Create a new integration page opens. 
   
   Select your organization from the drop-down list.

   In **[!UICONTROL Experience Cloud]**, Select **[!UICONTROL AEM Brand Portal]** and click **[!UICONTROL Continue]**. 

   If the Brand Portal option is disabled for you, ensure that you have selected correct organization from the drop-down box above the **[!UICONTROL Adobe Services]** option. If you do not know your organization, contact your administrator.

   ![Create Integration](assets/create-new-integration2.png)

1. Specify a name and description for the integration. Click **[!UICONTROL Select a File from your computer]** and upload the `AEM-Adobe-IMS.crt` file downloaded in the [obtain public certificates](#public-certificate) section.

1. Select the profile of your organization. 

   Or, select the default profile **[!UICONTROL Assets Brand Portal]** and click **[!UICONTROL Create Integration]**. The integration is created.

1. Click **[!UICONTROL Continue to integration details]** to view the integration information. 

   Copy the **[!UICONTROL API Key]** 
   
   Click **[!UICONTROL Retrieve Client Secret]** and copy the Client Secret key.

   ![API Key, Client Secret, and payload information of an integration](assets/create-new-integration3.png)

1. Navigate to **[!UICONTROL JWT]** tab, and copy the **[!UICONTROL JWT payload]**.

   The API Key, Client Secret key, and JWT payload information will be used to create IMS account configuration.

-->

### Configuration du compte IMS {#create-ims-account-configuration}

Vérifiez que vous avez effectué les étapes suivantes :

* [Obtention d’un certificat public](#public-certificate)
* [Création d’une connexion au compte de service (JWT)](#createnewintegration)

Procédez comme suit pour configurer le compte IMS créé selon la section [Obtention d’un certificat public](#public-certificate).

1. Ouvrez la configuration IMS et accédez à l’onglet **[!UICONTROL Comptes]**. Vous avez gardé la page ouverte lors de l’[obtention du certificat public](#public-certificate).

1. Spécifiez un **[!UICONTROL titre]** pour le compte IMS.

   Dans **[!UICONTROL Serveur d’autorisation]**, entrez l’adresse URL : [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)

   Collez l’ID client dans la clé d’API, le secret client et la charge utile JWT que vous avez copiés lors de la [création d’une connexion au compte de service (JWT)](#createnewintegration).

   Cliquez sur **[!UICONTROL Créer]**.

   Le compte IMS est configuré.

   ![Configuration du compte IMS](assets/create-new-integration6.png)


1. Sélectionnez la configuration de compte IMS et cliquez sur **[!UICONTROL Contrôle de l’intégrité]**.

   Cliquez sur **[!UICONTROL Vérifier]** dans la boîte de dialogue. Une fois la configuration réussie, un message s’affiche avec la mention *Jeton récupéré avec succès*.

   ![](assets/create-new-integration5.png)

>[!CAUTION]
>
>Vous ne devez avoir qu’une seule configuration IMS. N’en créez pas plusieurs.
>
>Assurez-vous que la configuration IMS réussit le contrôle d’intégrité. Si tel n’est pas le cas, elle n’est pas valide. Vous devez la supprimer et créer une configuration valide.



### Configuration du service cloud {#configure-the-cloud-service}

Pour configurer le service cloud Brand Portal, procédez comme suit :

1. Connectez-vous à votre instance cloud AEM Assets.

1. Dans le panneau **Outils** ![Outils](assets/tools.png), accédez à **[!UICONTROL Cloud Services]** > **[!UICONTROL AEM Brand Portal]**.

1. Dans la page Configurations Brand Portal, cliquez sur **[!UICONTROL Créer]**.

1. Saisissez un **[!UICONTROL titre]** pour la configuration.

   Sélectionnez la configuration IMS créée lors de la [configuration du compte IMS](#create-ims-account-configuration).

   Dans **[!UICONTROL URL du service]**, entrez votre client Brand Portal (URL de l’organisation).

   ![](assets/create-cloud-service.png)

1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**. La configuration cloud est alors créée. Votre instance cloud AEM Assets est maintenant configurée avec le client Brand Portal.

### Test de la configuration {#test-configuration}

Pour valider la configuration, procédez comme suit :

1. Connectez-vous à votre instance cloud AEM Assets.

1. Dans le panneau **Outils** ![Outils](assets/tools.png), accédez à **[!UICONTROL Déploiement]** > **[!UICONTROL Distribution]**.

   ![](assets/test-bpconfig1.png)

1. Dans la page Distribution, vous pouvez voir qu’un agent de distribution Brand Portal `bpdistributionagent0` est créé pour **[!UICONTROL Publier sur Brand Portal]**.

   Cliquez sur **[!UICONTROL Publier sur Brand Portal]**.

   ![](assets/test-bpconfig2.png)

   >[!NOTE]
   >
   >Par défaut, un agent de distribution est créé pour un client Brand Portal.

1. Dans la page de l’agent de distribution, vous pouvez voir les files d’attente de distribution sous l’onglet **[!UICONTROL État]**.

   Un agent de distribution contient deux files d’attente :
   * **processing-queue** : pour la distribution des ressources de Brand Portal.

   * **error-queue** : pour les ressources dont la distribution a échoué.
   >[!NOTE]
   >
   >Il est recommandé d’examiner les erreurs et d’effacer régulièrement la file d’attente **error-queue**.

   ![](assets/test-bpconfig3.png)

1. Pour vérifier la connexion entre AEM Assets et Brand Portal, cliquez sur **[!UICONTROL Tester la connexion]**.

   ![](assets/test-bpconfig4.png)

   Un message s’affiche en bas de la page pour indiquer que votre package de test a été livré.

   >[!NOTE]
   >
   >Évitez de désactiver l’agent de distribution, car cela peut entraîner l’échec de la distribution des ressources (running-in-queue).


Votre instance cloud AEM Assets est correctement configurée avec Brand Portal, et vous pouvez à présent effectuer les actions suivantes :

* [Publication de ressources à partir d’AEM Assets sur Brand Portal](publish-to-brand-portal.md)
* [Publication de dossiers à partir d’AEM Assets sur Brand Portal](publish-to-brand-portal.md#publish-folders-to-brand-portal)
* [Publication de collections à partir d’AEM Assets sur Brand Portal](publish-to-brand-portal.md#publish-collections-to-brand-portal)

Outre ce qui précède, vous pouvez également publier des schémas de métadonnées, des paramètres d’image prédéfinis, des facettes de recherche et des balises d’AEM Assets sur Brand Portal.

* [Publication de paramètres prédéfinis, de schémas et de facettes sur Brand Portal](https://docs.adobe.com/content/help/fr-FR/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html)
* [Publication de balises sur Brand Portal](https://docs.adobe.com/content/help/fr-FR/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html)


Pour plus d’informations, voir [Publication de balises sur Brand Portal](https://docs.adobe.com/content/help/fr-FR/experience-manager-brand-portal/using/home.html).


## Journaux de distribution {#distribution-logs}

Vous pouvez consulter les journaux pour obtenir des informations détaillées sur les actions effectuées par l’agent de distribution.

Par exemple, nous avons publié une ressource d’AEM Assets sur Brand Portal pour valider la configuration.

1. Suivez les étapes (1 à 4), comme indiqué dans la section [Test de la connexion](#test-configuration), puis accédez à la page de l’agent de distribution.

1. Cliquez sur **[!UICONTROL Journaux]** pour afficher les journaux de distribution. Vous pouvez afficher les journaux de traitement et d’erreur ici.

   ![](assets/test-bpconfig5.png)

L’agent de distribution génère les journaux suivants :

* INFO : Il s’agit d’un journal généré par le système qui se déclenche lors d’une configuration réussie activant l’agent de distribution.
* DSTRQ1 (requête 1) : Déclencheurs lors du test de la connexion.

Lors de la publication de la ressource, les journaux de requête et de réponse suivants sont générés :

**Requête de l’agent de distribution** :
* DSTRQ2 (requête 2) : La requête de publication de ressource est déclenchée.
* DSTRQ3 (requête 3) : Le système déclenche une autre requête pour publier le dossier dans lequel se trouve la ressource et réplique le dossier dans Brand Portal.

**Réponse de l’agent de distribution** :
* queue-bpdistributionagent0 (DSTRQ2) : La ressource est publiée sur Brand Portal.
* queue-bpdistributionagent0 (DSTRQ3) : Le système réplique le dossier contenant la ressource dans Brand Portal.

Dans l’exemple ci-dessus, une requête et une réponse supplémentaires sont déclenchées. Le système n’a pas trouvé le dossier parent (alias Ajouter chemin d’accès) dans Brand Portal, car la ressource a été publiée pour la première fois. Par conséquent, il déclenche une requête supplémentaire pour créer un dossier parent portant le même nom dans Brand Portal à l’emplacement où la ressource est publiée.

>[!NOTE]
>
>Une requête supplémentaire est générée au cas où le dossier parent n’existerait pas dans Brand Portal (dans l’exemple ci-dessus) ou si le dossier parent a été modifié dans AEM Assets.



<!--

## Additional information {#additional-information}

Go to `/system/console/slingmetrics` for statistics related to the distributed content:

1. **Counter metrics**
   * sling: `mac_sync_request_failure`
   * sling: `mac_sync_request_received`
   * sling: `mac_sync_request_success`

1. **Time metrics**
   * sling: `mac_sync_distribution_duration`
   * sling: `mac_sync_enqueue_package_duration`
   * sling: `mac_sync_setup_request_duration`

-->

<!--
   Comment Type: draft

   <li> </li>
   -->

<!--
   Comment Type: draft

   <li>Step text</li>
   -->
