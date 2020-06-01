---
title: Configuration du service cloud AEM Assets avec Brand Portal
description: Configurez le service cloud AEM Assets avec Brand Portal.
contentOwner: Vishabh Gupta
translation-type: tm+mt
source-git-commit: f54f5bbd5de76c3507d86b92255f1d4713e717fc
workflow-type: tm+mt
source-wordcount: '1762'
ht-degree: 37%

---


# Configuration d’AEM Assets avec Brand Portal {#configure-aem-assets-with-brand-portal}

Les ressources Adobe Experience Manager (AEM) sont configurées avec le portail de marque via Adobe Developer Console, qui fournit un jeton IMS pour l’autorisation de votre client du portail de marque.

**Comment fonctionne la configuration ?**

La configuration de l’instance de cloud AEM Assets avec un client (organisation) du portail de marque nécessite des configurations à la fois dans l’instance de cloud AEM Assets et dans Adobe Developer Console.

1. Dans l’instance cloud AEM Assets, créez un compte IMS et générez un certificat public (clé publique).
1. Dans Adobe Developer Console, créez un projet pour votre client (organisation) du portail de marque.
1. Sous le projet, configurez une API à l’aide de la clé publique pour créer une connexion au compte de service (JWT).
1. Obtenez les informations d’identification du compte de service et les informations de charge JWT.
1. Dans l’instance cloud AEM Assets, configurez le compte IMS à l’aide des informations d’identification du compte de service et de la charge utile JWT.
1. Dans l’instance cloud AEM Assets, configurez le service cloud du portail des marques à l’aide du compte IMS et du point de terminaison du portail des marques (URL de l’organisation).
1. Testez la configuration en publiant une ressource de l’instance cloud AEM Assets sur Brand Portal.

>[!NOTE]
>
>Un client du portail de marques doit uniquement être configuré avec une seule instance de cloud AEM Assets.
>
>Ne configurez pas un client du portail de marques avec plusieurs instances de cloud AEM Assets.


## Conditions préalables {#prerequisites}

Pour configurer AEM Assets avec Brand Portal, vous devez disposer des éléments suivants :

* Une instance cloud AEM Assets en cours d’exécution.
* URL du client Brand Portal
* Un utilisateur disposant de droits d’administrateur système sur l’organisation IMS du client Brand Portal

**Contactez le service à la clientèle** pour obtenir d’autres requêtes.

## Création d’une configuration {#create-new-configuration}

Effectuez les étapes suivantes dans la séquence spécifiée pour configurer l’instance cloud AEM Assets avec Brand Portal.

1. [Obtention d’un certificat public](#public-certificate)
1. [Créer une connexion au compte de service (JWT)](#createnewintegration)
1. [Configuration du compte IMS](#create-ims-account-configuration)
1. [Configuration du service cloud](#configure-the-cloud-service)
1. [Test de la configuration](#test-configuration)

### Création de la configuration IMS {#create-ims-configuration}

La configuration IMS authentifie votre locataire du portail de marque avec l’instance cloud AEM Assets.

La configuration IMS comprend deux étapes :

* [Obtention d’un certificat public](#public-certificate)
* [Configuration du compte IMS](#create-ims-account-configuration)

### Obtention d’un certificat public {#public-certificate}

Le certificat public vous permet d’authentifier votre profil sur Adobe Developer Console.

1. Connectez-vous à votre instance cloud AEM Assets.

1. From the **Tools** ![Tools](assets/tools.png) panel, navigate to **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**.

   ![Interface utilisateur de configuration du compte Adobe IMS](assets/ims-configuration1.png)

1. Dans la page Adobe IMS Configurations, cliquez sur **[!UICONTROL Créer]**.

1. Vous êtes redirigé vers la page Configuration **[!UICONTROL du compte technique]** Adobe IMS. By default, the **Certificate** tab opens.

   Sélectionnez la solution cloud **[!UICONTROL Adobe Brand Portal]**.

1. Cochez la case **[!UICONTROL Créer un certificat]** et spécifiez un **alias** pour le certificat. L’alias sert de nom à la boîte de dialogue.

1. Cliquez sur **[!UICONTROL Créer un certificat]**. Cliquez ensuite sur **[!UICONTROL OK]** dans la boîte de dialogue pour générer le certificat public.

   ![Création d’un certificat](assets/ims-config2.png)

1. Click **[!UICONTROL Download Public Key]** and save the certificate (.crt) file on your machine.

   Le fichier de certificat sera utilisé dans d’autres étapes pour configurer l’API de votre client du portail de marque et générer des informations d’identification de compte de service dans Adobe Developer Console.

   ![Téléchargement du certificat](assets/ims-config3.png)

1. Cliquez sur **[!UICONTROL Suivant]**.

   Dans l’onglet **Compte** , vous créez le compte IMS Adobe, mais pour ce faire, vous aurez besoin des informations d’identification du compte de service générées dans Adobe Developer Console. Gardez cette page ouverte pour l’instant.

   Ouvrez un nouvel onglet et [créez une connexion au compte de service (JWT) dans Adobe Developer Console](#createnewintegration) pour obtenir les informations d’identification et la charge utile JWT pour configurer le compte IMS.

### Créer une connexion au compte de service (JWT) {#createnewintegration}

Dans Adobe Developer Console, les projets et les API sont configurés au niveau de l’entreprise (client du portail de marque). La configuration d’une API crée une connexion de compte de service (JWT) dans Adobe Developer Console. Il existe deux méthodes pour configurer l&#39;API, en générant une paire de clés (clés privée et publique) ou en téléchargeant une clé publique. Pour configurer l’instance de cloud AEM Assets avec Brand Portal, vous devez générer un certificat public (clé publique) dans l’instance de cloud AEM Assets et créer des informations d’identification dans Adobe Developer Console en téléchargeant la clé publique. Cette clé publique permet de configurer l’API pour l’organisation du portail de marques sélectionnée et de générer les informations d’identification et la charge utile JWT pour le compte de service. Ces informations d’identification sont également utilisées pour configurer le compte IMS dans l’instance cloud AEM Assets. Une fois le compte IMS configuré, vous pouvez configurer le service cloud du portail de marque dans l’instance cloud AEM Assets.

Effectuez les étapes suivantes pour générer les informations d’identification du compte de service et la charge utile JWT :

1. Connectez-vous à Adobe Developer Console avec les droits d’administrateur système sur l’organisation IMS (locataire du portail de marque). L’URL par défaut est

   [https://www.adobe.com/go/devs_console_ui](https://www.adobe.com/go/devs_console_ui)


   >[!NOTE]
   >
   >Assurez-vous d’avoir sélectionné l’organisation IMS appropriée (locataire du portail de marque) dans la liste déroulante (liste d’organisation) située dans l’angle supérieur droit.

1. Click **[!UICONTROL Create new project]**. Un projet vierge est créé pour votre organisation.

   Cliquez sur **[!UICONTROL Modifier le projet]** pour mettre à jour le titre **[!UICONTROL et la]** description **[!UICONTROL du]** projet, puis cliquez sur **[!UICONTROL Enregistrer.]**

   ![Créer un projet](assets/service-account1.png)

1. Dans l’onglet Aperçu du projet, cliquez sur **[!UICONTROL Ajouter l’API]**.

   ![API Ajoute](assets/service-account2.png)

1. Dans la fenêtre Ajouter une API, sélectionnez Portail **[!UICONTROL de marque]** AEM et cliquez sur **[!UICONTROL Suivant]**.

   Assurez-vous d’avoir accès au service AEM Brand Portal.

1. Dans la fenêtre Configurer l’API, cliquez sur **[!UICONTROL Télécharger votre clé]** publique. Cliquez ensuite sur **[!UICONTROL Sélectionner un fichier]** et téléchargez le certificat public (fichier .crt) que vous avez téléchargé dans la section [Obtenir un certificat](#public-certificate) public.

   Cliquez sur **[!UICONTROL Suivant]**.

   ![Télécharger la clé publique](assets/service-account3.png)

1. Vérifiez le certificat public et cliquez sur **[!UICONTROL Suivant]**.

1. Sélectionnez le portail **[!UICONTROL des]** ressources du profil de produits par défaut **[!UICONTROL et cliquez sur]** Enregistrer la configuration.

   <!-- 
   In Brand Portal, a default profile is created for each organization. The Product Profiles are created in admin console for assigning users to groups (based on the roles and permissions). For configuration with Brand Portal, the OAuth token is created at organization level. Therefore, you must configure the default Product Profile for your organization. 
   -->

   ![Sélectionner le Profil de produit](assets/service-account4.png)

1. Une fois l’API configurée, vous êtes redirigé vers l’aperçu de l’API. Dans le volet de navigation de gauche sous **[!UICONTROL Informations d’identification]**, cliquez sur Compte de **[!UICONTROL service (JWT)]**.

   >[!NOTE]
   >
   >Vous pouvez vue les informations d’identification et effectuer d’autres actions (générer des jetons JWT, copier les informations d’identification, récupérer le secret client, etc.) si nécessaire.

1. Dans l’onglet Informations d’identification **[!UICONTROL du]** client, copiez l’ID **[!UICONTROL du]** client.

   Click **[!UICONTROL Retrieve Client Secret]** and copy the **[!UICONTROL client secret]**.

   ![Identifiants de compte de service](assets/service-account5.png)

1. Navigate to the **[!UICONTROL Generate JWT]** tab and copy the **[!UICONTROL JWT Payload]**.

Vous pouvez désormais utiliser l’ID client (clé d’API), le secret client et la charge utile JWT pour [configurer le compte](#create-ims-account-configuration) IMS dans l’instance cloud AEM Assets.

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
* [Créer une connexion au compte de service (JWT)](#createnewintegration)

Effectuez les étapes suivantes pour configurer le compte IMS que vous avez créé dans [l’obtention d’un certificat](#public-certificate)public.

1. Ouvrez la configuration IMS et accédez à l’onglet **[!UICONTROL Comptes]** . Vous avez gardé la page ouverte lors de l’ [obtention du certificat](#public-certificate)public.

1. Spécifiez un **[!UICONTROL titre]** pour le compte IMS.

   Dans **[!UICONTROL Serveur d’autorisation]**, entrez l’adresse URL : [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)

   Collez l’ID client dans la clé d’API, le secret client et la charge utile JWT que vous avez copiés lors de la [création de la connexion](#createnewintegration)au compte de service (JWT).

   Cliquez sur **[!UICONTROL Créer]**.

   Le compte IMS est configuré.

   ![Configuration du compte IMS](assets/create-new-integration6.png)


1. Select the IMS account configuration and click **[!UICONTROL Check Health]**.

   Cliquez sur **[!UICONTROL Vérifier]** dans la boîte de dialogue. Une fois la configuration réussie, un message s&#39;affiche indiquant que le *jeton est récupéré avec succès*.

   ![](assets/create-new-integration5.png)

>[!CAUTION]
>
>Vous ne devez avoir qu’une seule configuration IMS. N’en créez pas plusieurs.
>
>Assurez-vous que la configuration IMS réussit le contrôle d’intégrité. Si tel n’est pas le cas, elle n’est pas valide. Vous devez la supprimer et créer une configuration valide.



### Configuration du service cloud {#configure-the-cloud-service}

Effectuez les étapes suivantes pour configurer le service cloud de Brand Portal :

1. Connectez-vous à votre instance cloud AEM Assets.

1. From the **Tools** ![Tools](assets/tools.png) panel, navigate to **[!UICONTROL Cloud Services]** > **[!UICONTROL AEM Brand Portal]**.

1. Dans la page Configurations du portail de marque, cliquez sur **[!UICONTROL Créer]**.

1. Saisissez un **[!UICONTROL titre]** pour la configuration.

   Sélectionnez la configuration IMS que vous avez créée lors de la [configuration du compte](#create-ims-account-configuration)IMS.

   In the **[!UICONTROL Service URL]**, enter your Brand Portal tenant (organization URL).

   ![](assets/create-cloud-service.png)

1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**. La configuration cloud est alors créée. Votre instance cloud AEM Assets est maintenant configurée avec le client Brand Portal.

### Test de la configuration {#test-configuration}

Effectuez les étapes suivantes pour valider la configuration :

1. Connectez-vous à votre instance cloud AEM Assets.

1. From the **Tools** ![Tools](assets/tools.png) panel, navigate to **[!UICONTROL Deployment]** > **[!UICONTROL Distribution]**.

   ![](assets/test-bpconfig1.png)

1. Dans la page Distribution, vous pouvez voir qu’un agent de distribution du portail de marques `bpdistributionagent0` est créé pour **[!UICONTROL Publier sur le portail]** de marques.

   Cliquez sur **[!UICONTROL Publier sur Brand Portal]**.

   ![](assets/test-bpconfig2.png)

   >[!NOTE]
   >
   >Par défaut, un agent de distribution est créé pour un client Brand Portal.

1. Dans la page de l&#39;agent de distribution, vous pouvez voir les files d&#39;attente de distribution sous l&#39;onglet **[!UICONTROL État]** .

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

Vous pouvez consulter les journaux pour obtenir des informations détaillées sur les actions effectuées par l&#39;agent de distribution.

Par exemple, nous avons publié un actif d’AEM Assets sur le portail de marque pour valider la configuration.

1. Follow the steps (from 1 to 4) as shown in the [test connection](#test-configuration) section and navigate to the distribution agent page.

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
