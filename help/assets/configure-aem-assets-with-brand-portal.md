---
title: Configuration d’AEM Assets en tant que Cloud Service avec le portail de marque
description: Configuration d’AEM Assets avec Brand Portal.
contentOwner: Vishabh Gupta
translation-type: tm+mt
source-git-commit: ad1f1e8c0ba5409cd645489263f349b29f080d27
workflow-type: tm+mt
source-wordcount: '1647'
ht-degree: 37%

---


# Configure AEM Assets as a Cloud Service with Brand Portal {#configure-aem-assets-with-brand-portal}

La configuration de Adobe Experience Manager Assets Brand Portal permet de publier des fichiers de marque approuvés à partir de Adobe Experience Manager Assets en tant qu’instance de Cloud Service sur Brand Portal et de les distribuer aux utilisateurs du portail de marque.

**Processus de configuration**

aem assets en tant que Cloud Service est configuré avec Brand Portal via Adobe Developer Console, qui fournit un jeton de compte Adobe Identity Management Services (IMS) pour l’autorisation du locataire du portail Marque. Il nécessite des configurations à la fois dans AEM Assets et dans Adobe Developer Console.

1. En AEM Assets, créez un compte IMS et générez une clé publique (certificat).
1. Dans Adobe Developer Console, créez un projet pour votre client Brand Portal (organisation).
1. Sous le projet, configurez une API à l’aide de la clé publique pour créer une connexion au compte de service.
1. Obtenez les informations d’identification du compte de service et les informations de charge utile JSON Web Token (JWT).
1. En AEM Assets, configurez le compte IMS à l’aide des informations d’identification du compte de service et de la charge utile JWT.
1. Dans AEM Assets, configurez le service cloud du portail des marques à l’aide du compte IMS et du point de terminaison du portail des marques (URL de l’organisation).
1. Testez votre configuration en publiant un fichier d’AEM Assets vers Brand Portal.

>[!NOTE]
>
>Une AEM Assets en tant qu’instance Cloud Service ne doit être configurée qu’avec un seul client du portail de marques.


## Conditions préalables {#prerequisites}

Pour configurer AEM Assets avec Brand Portal, vous devez disposer des éléments suivants :

* Une AEM Assets en cours d’exécution en tant qu’instance Cloud Service
* URL du client du portail de marques
* Utilisateur disposant de droits d’administrateur système sur l’organisation IMS du locataire du portail de marque

## Création d’une configuration {#create-new-configuration}

Effectuez les étapes suivantes dans la séquence spécifiée pour configurer AEM Assets avec Brand Portal.

1. [Obtention d’un certificat public](#public-certificate)
1. [Création d’une connexion au compte de service (JWT)](#createnewintegration)
1. [Configuration du compte IMS](#create-ims-account-configuration)
1. [Configuration du service cloud](#configure-the-cloud-service)
1. [Test de la configuration](#test-configuration)

### Création de la configuration IMS {#create-ims-configuration}

La configuration IMS authentifie votre AEM Assets en tant qu’instance de Cloud Service auprès du locataire du portail de marques.

La configuration IMS comprend deux étapes :

* [Obtention d’un certificat public](#public-certificate)
* [Configuration du compte IMS](#create-ims-account-configuration)

### Obtention d’un certificat public {#public-certificate}

La clé publique (certificat) authentifie votre profil sur Adobe Developer Console.

1. Connectez-vous à AEM Assets.

1. From the **Tools** panel, navigate to **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**.


1. Dans la page Configurations d’Adobe IMS, cliquez sur **[!UICONTROL Créer]**. It will redirect to the **[!UICONTROL Adobe IMS Technical Account Configuration]** page. Par défaut, l’onglet **Certificat** s’ouvre.

1. Sélectionnez Portail **[!UICONTROL de marque]** d’Adobe dans la liste déroulante Solution **** Cloud.

1. Cochez la case **[!UICONTROL Créer un nouveau certificat]** et spécifiez un **alias** pour la clé publique. L’alias sert de nom à la clé publique.

1. Cliquez sur **[!UICONTROL Créer un certificat]**. Then, click **[!UICONTROL OK]** to generate the public key.

   ![Création d’un certificat](assets/ims-config2.png)

1. Click the **[!UICONTROL Download Public Key]** icon and save the public key (.crt) file on your machine.

   La clé publique sera utilisée ultérieurement pour configurer l’API de votre client du portail de marque et générer les informations d’identification du compte de service dans la console de développement des Adobes.

   ![Téléchargement du certificat](assets/ims-config3.png)

1. Cliquez sur **[!UICONTROL Suivant]**.

   Dans l&#39;onglet **Compte** , un compte IMS Adobe est créé, ce qui nécessite les informations d&#39;identification du compte de service qui sont générées dans Adobe Developer Console. Gardez cette page ouverte pour l’instant.

   Ouvrez un nouvel onglet et [créez une connexion au compte de service (JWT) dans Adobe Developer Console](#createnewintegration) pour obtenir les informations d’identification et la charge utile JWT qui servent à configurer le compte IMS.

### Création d’une connexion au compte de service (JWT) {#createnewintegration}

Dans Adobe Developer Console, les projets et les API sont configurés au niveau du client (organisation) du portail de la marque. La configuration d’une API crée une connexion au compte de service (JWT). Il existe deux méthodes pour configurer l’API : générer une paire de clés (clés privée et publique) ou télécharger une clé publique. Pour configurer AEM Assets avec Brand Portal, vous devez générer une clé publique (certificat) dans AEM Assets et créer des informations d’identification dans Adobe Developer Console en téléchargeant la clé publique. Ces informations d’identification sont requises pour configurer le compte IMS en AEM Assets. Une fois le compte IMS configuré, vous pouvez configurer le service cloud du portail de marque en AEM Assets.

Procédez comme suit pour générer les informations d’identification du compte de service et la charge utile JWT :

1. Connectez-vous à Adobe Developer Console avec les privilèges d’administrateur système sur l’organisation IMS (client Brand Portal). L’URL par défaut est [https://www.adobe.com/go/devs_console_ui_fr](https://www.adobe.com/go/devs_console_ui_fr).


   >[!NOTE]
   >
   >Assurez-vous d’avoir sélectionné l’organisation IMS appropriée (locataire du portail de marque) dans la liste de liste déroulante (organisation) située dans l’angle supérieur droit.

1. Cliquez sur **[!UICONTROL Créer un projet]**. Un projet vierge portant un nom généré par le système est créé pour votre entreprise.

   Cliquez sur **[!UICONTROL Modifier le projet]** pour mettre à jour le **[!UICONTROL Titre du projet]** et la **[!UICONTROL Description]**, puis cliquez sur **[!UICONTROL Enregistrer]**.

1. In the **[!UICONTROL Project overview]** tab, click **[!UICONTROL Add API]**.

1. In the **[!UICONTROL Add an API window]**, select **[!UICONTROL AEM Brand Portal]** and click **[!UICONTROL Next]**.

   Assurez-vous d’avoir accès au service AEM Brand Portal.

1. In the **[!UICONTROL Configure API]** window, click **[!UICONTROL Upload your public key]**. Then, click **[!UICONTROL Select a File]** and upload the public key (.crt file) that you have downloaded in the [obtain public certificate](#public-certificate) section.

   Cliquez sur **[!UICONTROL Suivant]**.

   ![Charger la clé publique](assets/service-account3.png)

1. Verify the public key and click **[!UICONTROL Next]**.

1. Sélectionnez **[!UICONTROL Assets Brand Portal]** comme profil de produit par défaut et cliquez sur **[!UICONTROL Enregistrer l’API]** configurée.

   <!-- 
   In Brand Portal, a default profile is created for each organization. The Product Profiles are created in admin console for assigning users to groups (based on the roles and permissions). For configuration with Brand Portal, the OAuth token is created at organization level. Therefore, you must configure the default Product Profile for your organization. 
   -->

   ![Sélectionner le profil de produit](assets/service-account4.png)

1. Une fois l’API configurée, vous êtes redirigé vers la page d’aperçu de l’API. From the left navigation under **[!UICONTROL Credentials]**, click on the **[!UICONTROL Service Account (JWT)]** option.

   >[!NOTE]
   >
   >Vous pouvez vue les informations d’identification et effectuer des actions telles que générer des jetons JWT, copier les informations d’identification, récupérer le secret client, etc.

1. Dans l’onglet **[!UICONTROL Informations d’identification client]**, copiez l’**[!UICONTROL ID client]**.

   Cliquez sur **[!UICONTROL Récupérer le secret client]** et copiez le **[!UICONTROL secret client]**.

   ![Informations d’identification du compte de service](assets/service-account5.png)

1. Navigate to the **[!UICONTROL Generate JWT]** tab and copy the **[!UICONTROL JWT Payload]** information.

You can now use the client ID (API key), client secret, and JWT payload to [configure the IMS account](#create-ims-account-configuration) in AEM Assets.

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

Effectuez les étapes suivantes pour configurer le compte IMS.

1. Open the IMS Configuration and navigate to the **[!UICONTROL Account]** tab. You kept the page open while [obtaining the public certificate](#public-certificate).

1. Spécifiez un **[!UICONTROL titre]** pour le compte IMS.

   In the **[!UICONTROL Authorization Server]** field, specify the URL: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)

   Specify client ID in the **[!UICONTROL API key]** field, **[!UICONTROL Client Secret]**, and **[!UICONTROL Payload]** (JWT payload) that you have copied while [creating the service account (JWT) connection](#createnewintegration).

   Cliquez sur **[!UICONTROL Créer]**.

   Le compte IMS est configuré.

   ![Configuration du compte IMS](assets/create-new-integration6.png)


1. Sélectionnez la configuration de compte IMS et cliquez sur **[!UICONTROL Contrôle de l’intégrité]**.

   Cliquez sur **[!UICONTROL Vérifier]** dans la boîte de dialogue. Une fois la configuration réussie, un message s’affiche avec la mention *Jeton récupéré avec succès*.

   ![](assets/create-new-integration5.png)

>[!CAUTION]
>
>Vous ne devez avoir qu’une seule configuration IMS.
>
>Assurez-vous que la configuration IMS réussit le contrôle d’intégrité. Si tel n’est pas le cas, elle n’est pas valide. Vous devez la supprimer et créer une configuration valide.



### Configuration du service cloud {#configure-the-cloud-service}

Pour configurer le service cloud Brand Portal, procédez comme suit :

1. Connectez-vous à AEM Assets.

1. From the **Tools** panel, navigate to **[!UICONTROL Cloud Services]** > **[!UICONTROL AEM Brand Portal]**.

1. Dans la page Configurations Brand Portal, cliquez sur **[!UICONTROL Créer]**.

1. Saisissez un **[!UICONTROL titre]** pour la configuration.

   Select the IMS configuration that you created while [configuring the IMS account](#create-ims-account-configuration).

   In the **[!UICONTROL Service URL]** field, specify your Brand Portal tenant (organization) URL.

   ![](assets/create-cloud-service.png)

1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**. La configuration cloud est alors créée.

   Votre AEM Assets en tant qu’instance de Cloud Service est maintenant configurée avec le client du portail de marques.

### Test de la configuration {#test-configuration}

Pour valider la configuration, procédez comme suit :

1. Connectez-vous à AEM Assets.

1. From the **Tools** panel, navigate to **[!UICONTROL Deployment]** > **[!UICONTROL Distribution]**.

   ![](assets/test-bpconfig1.png)

   A Brand Portal distribution agent (**[!UICONTROL bpdistributionagent0]**) is created under **[!UICONTROL Publish to Brand Portal]**.

   ![](assets/test-bpconfig2.png)


1. Cliquez sur **[!UICONTROL Publier sur le portail]** des marques pour ouvrir l&#39;agent de distribution.

   Vous pouvez voir les files d&#39;attente de distribution sous l&#39;onglet **[!UICONTROL Etat]** .

   Un agent de distribution contient deux files d’attente :
   * **processing-queue** : pour la distribution des ressources de Brand Portal.

   * **error-queue** : pour les ressources dont la distribution a échoué.
   >[!NOTE]
   >
   >Il est recommandé d’examiner les erreurs et d’effacer régulièrement la file d’attente **error-queue**.

   ![](assets/test-bpconfig3.png)

1. Pour vérifier la connexion entre AEM Assets en tant que Cloud Service et le portail de marque, cliquez sur l’icône **[!UICONTROL Tester la connexion]** .

   ![](assets/test-bpconfig4.png)

   Un message s’affiche indiquant que votre package de *test est livré* avec succès.

   >[!NOTE]
   >
   >Évitez de désactiver l’agent de distribution, car cela peut entraîner l’échec de la distribution des ressources (running-in-queue).


Vous pouvez maintenant :

* [Publication de ressources à partir d’AEM Assets sur Brand Portal](publish-to-brand-portal.md)
* [Publication de dossiers à partir d’AEM Assets sur Brand Portal](publish-to-brand-portal.md#publish-folders-to-brand-portal)
* [Publication de collections à partir d’AEM Assets sur Brand Portal](publish-to-brand-portal.md#publish-collections-to-brand-portal)

* [Publication de paramètres prédéfinis, de schémas et de facettes sur Brand Portal](https://docs.adobe.com/content/help/fr-FR/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html)
* [Publication de balises sur Brand Portal](https://docs.adobe.com/content/help/fr-FR/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html)


See [Brand Portal documentation](https://docs.adobe.com/content/help/fr-FR/experience-manager-brand-portal/using/home.html) for more information.


## Journaux de distribution {#distribution-logs}

Vous pouvez surveiller les journaux de l’agent de distribution pour le processus de publication des ressources.

Par exemple, nous avons publié une ressource d’AEM Assets sur Brand Portal pour valider la configuration.

1. Suivez les étapes (1 à 4), comme indiqué dans la section [Test de la configuration](#test-configuration), puis accédez à la page de l’agent de distribution.

1. Cliquez sur **[!UICONTROL Journaux]** pour vue des journaux de traitement et d’erreurs.

   ![](assets/test-bpconfig5.png)

L&#39;agent de distribution a généré les journaux suivants :

* INFO : Il s&#39;agit d&#39;un journal généré par le système qui se déclenche lors d&#39;une configuration réussie de l&#39;agent de distribution.
* DSTRQ1 (requête 1) : Déclencheurs lors du test de la connexion.

Lors de la publication de la ressource, les journaux de requête et de réponse suivants sont générés :

**Requête de l’agent de distribution** :
* DSTRQ2 (requête 2) : La requête de publication de ressource est déclenchée.
* DSTRQ3 (Demande 3) : Le système déclenche une autre demande de publication du dossier AEM Assets (dans lequel la ressource existe) et répliquera le dossier dans le portail de marques.

**Réponse de l’agent de distribution** :
* queue-bpdistributionagent0 (DSTRQ2) : La ressource est publiée sur Brand Portal.
* queue-bpdistributionagent0 (DSTRQ3) : Le système répliquera le dossier AEM Assets (contenant le fichier) dans Brand Portal.

Dans l’exemple ci-dessus, une requête et une réponse supplémentaires sont déclenchées. Le système n’a pas pu trouver le dossier parent (chemin d’accès à l’Ajoute) dans Brand Portal car la ressource a été publiée pour la première fois. Par conséquent, il a déclenché une demande supplémentaire pour créer un dossier parent portant le même nom dans Brand Portal où la ressource est publiée.

>[!NOTE]
>
>Une requête supplémentaire est générée au cas où le dossier parent n’existerait pas dans le portail de la marque ou aurait été modifié en AEM Assets.



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
