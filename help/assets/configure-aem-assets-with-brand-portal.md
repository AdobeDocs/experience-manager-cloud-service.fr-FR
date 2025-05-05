---
title: Configuration d’AEM Assets as a [!DNL Cloud Service] avec Brand Portal
description: Découvrez comment configurer AEM Assets avec Brand Portal. La configuration vous permet de publier des ressources de marque approuvées d’une instance AEM vers Brand Portal et de les distribuer aux utilisateurs de Brand Portal.
contentOwner: AK
feature: Brand Portal, Asset Distribution, Configuration
role: Admin
exl-id: 078e522f-bcd8-4734-95db-ddc8772de785
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '1802'
ht-degree: 86%

---

# Configurer Experience Manager Assets avec Brand Portal {#configure-aem-assets-with-brand-portal}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime et Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouvelle</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Intégration d’AEM Assets à Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Extensibilité de l’interface utilisateur</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Activation de Dynamic Media Prime et Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Bonnes pratiques de recherche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Bonnes pratiques relatives aux métadonnées</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Hub de contenus</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Fonctionnalités Dynamic Media avec OpenAPI</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Documentation de développement pour AEM Assets</b></a>
        </td>
    </tr>
</table>

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/assets/brandportal/configure-aem-assets-with-brand-portal.html?lang=fr) |
| AEM as a Cloud Service | Cet article |

La configuration de Adobe Experience Manager Assets Brand Portal vous permet de publier des ressources de marque approuvées d’Adobe Experience Manager Assets as a [!DNL Cloud Service] vers Brand Portal et de les distribuer aux utilisateurs de Brand Portal.

## Activation de Brand Portal à l’aide de Cloud Manager {#activate-brand-portal}

L’utilisateur ou l’utilisatrice de Cloud Manager active Brand Portal pour une instance Experience Manager Assets as a [!DNL Cloud Service]. Le workflow d’activation crée les configurations requises (jeton d’autorisation, configuration IMS et service cloud de Brand Portal) sur le serveur principal et reflète le statut du client ou de la cliente Brand Portal dans Cloud Manager. L’activation de Brand Portal permet aux utilisateurs et utilisatrices d’Experience Manager Assets de publier des ressources sur Brand Portal et de les distribuer aux utilisateurs et utilisatrices de Brand Portal.

**Conditions préalables**

Vous avez besoin des éléments suivants pour activer Brand Portal sur votre instance Experience Manager Assets as a [!DNL Cloud Service] :

* Une instance Experience Manager Assets as a [!DNL Cloud Service] opérationnelle.
* Utilisateur ayant accès à Cloud Manager, affecté aux Profils du produit Cloud Manager. Consultez [Accès à Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=fr#accessing-cloud-manager) pour plus d’informations.

>[!NOTE]
>
>Un environnement de production configuré est requis pour qu’une instance Experience Manager Assets as a [!DNL Cloud Service] puisse se connecter au client Brand Portal.

**Étapes d’activation de Brand Portal**

Vous pouvez activer Brand Portal au moment de la création des environnements de production pour votre instance Experience Manager Assets as a [!DNL Cloud Service] ou à un autre moment. Supposons que l’environnement a déjà été créé et que vous devez maintenant activer Brand Portal.

1. Connectez-vous à Adobe Cloud Manager et accédez à **[!UICONTROL Environnements]**.

   La page **[!UICONTROL Environnements]** affiche la liste de tous les environnements existants.

1. Sélectionnez les environnements (un par un) de la liste pour afficher les détails de l’environnement.

   Brand Portal a alloué à l’un des environnements disponibles et apparaît dans les **[!UICONTROL Informations sur l’environnement]**.

   Une fois que vous avez trouvé l’environnement associé à Brand Portal, cliquez sur le bouton **[!UICONTROL Activer Brand Portal]** pour lancer le workflow d’activation.

   ![Activer Brand Portal](assets/create-environment4.png)

1. L’activation du client Brand Portal prend quelques minutes car le processus d’activation crée les configurations requises sur le serveur principal. Une fois que le client Brand Portal est activé, son statut passe sur Activé.

   ![Afficher l’état](assets/create-environment5.png)


>[!NOTE]
>
>Brand Portal doit être activé sur la même organisation IMS que l’instance Experience Manager Assets as a [!DNL Cloud Service].
>
>Si vous disposez déjà d’une configuration cloud de Brand Portal ([configurée manuellement à l’aide d’Adobe Developer Console](#manual-configuration)) pour une organisation IMS (org1-existing) et que votre instance Experience Manager Assets as a [!DNL Cloud Service] est configurée pour une autre organisation IMS (org2-new), l’activation de Brand Portal à partir de Cloud Manager réinitialise l’organisation IMS de Brand Portal sur `org2-new`. Bien que la configuration manuelle du cloud sur `org1-existing` soit visible dans l’instance de création Experience Manager Assets, elle n’est plus utilisée une fois Brand Portal activé à partir de Cloud Manager.
>
>Si la configuration cloud existante de Brand Portal et de l’instance Experience Manager Assets as a [!DNL Cloud Service] utilisent la même organisation IMS (org1), il vous suffit d’activer Brand Portal à partir de Cloud Manager.
>
>Ne modifiez aucun paramètre généré automatiquement.

**Voir aussi** :

* [Ajouter des utilisateurs et des rôles dans Experience Manager Assets as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=fr)

* [Gérer les environnements dans Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=fr#adding-environments)


**Connexion à votre client Brand Portal** :

Après l’activation de votre client Brand Portal dans Cloud Manager, vous pouvez vous connecter à Brand Portal à partir de l’Admin Console ou directement à l’aide de l’URL du client.

L’URL par défaut de votre client Brand Portal est : `https://<tenant-id>.brand-portal.adobe.com/`.

dans lequel l’identifiant client est l’organisation IMS.


Suivez les étapes suivantes si vous n’êtes pas sûr de l’URL de Brand Portal :

1. Connectez-vous à l’[Admin Console](https://adminconsole.adobe.com/) et accédez à **[!UICONTROL Produits]**.
1. Dans le panneau de gauche, sélectionnez **[!UICONTROL Adobe Experience Manager Brand Portal - Brand Portal]**.
1. Cliquez sur **[!UICONTROL Accéder à Brand Portal]** pour ouvrir directement Brand Portal dans le navigateur.

   Vous pouvez également copier l’URL du client Brand Portal à partir du lien **[!UICONTROL Accéder à Brand Portal]** et la coller dans votre navigateur pour ouvrir l’interface de Brand Portal.

   ![Accéder à Brand Portal](assets/access-bp-on-cloud.png)


**Test de la connexion**

Suivez les étapes suivantes pour valider la connexion entre votre instance Experience Manager Assets as a [!DNL Cloud Service] et votre client Brand Portal :

1. Connectez-vous à Experience Manager Assets.

1. Dans le panneau **Outils**, accédez à **[!UICONTROL Déploiement]** > **[!UICONTROL Distribution]**.

   ![Accès à l’option de distribution](assets/test-bpconfig1.png)

   Un agent de distribution Brand Portal (**[!UICONTROL bpdistributionagent0]**) est créé sous **[!UICONTROL Publier sur Brand Portal]**.

   ![Création d’un agent de distribution](assets/test-bpconfig2.png)

1. Cliquez sur **[!UICONTROL Publier sur Brand Portal]** pour ouvrir l’agent de distribution.

   Les files d’attente de distribution apparaissent dans l’onglet **[!UICONTROL État]**.

   Un agent de distribution contient deux files d’attente :
   * **processing-queue** : pour la distribution des ressources de Brand Portal.

   * **error-queue** : pour les ressources dont la distribution a échoué.

   >[!NOTE]
   >
   >Il est recommandé d’examiner les erreurs et d’effacer régulièrement la file d’attente **error-queue**.

   ![File d’attente de traitement pour la distribution des ressources](assets/test-bpconfig3.png)

1. Pour vérifier la connexion entre Experience Manager Assets as a [!DNL Cloud Service] et Brand Portal, cliquez sur l’icône **[!UICONTROL Tester la connexion]**.

   ![Vérification de la connexion entre AEM et Brand Portal](assets/test-bpconfig4.png)

   Un message s’affiche indiquant que votre *package de test a bien été livré*.

   >[!NOTE]
   >
   >Évitez de désactiver l’agent de distribution, car cela peut entraîner l’échec de la distribution des ressources (running-in-queue).

Pour vérifier la connexion entre votre instance Experience Manager Assets as a [!DNL Cloud Service] et le client Brand Portal, publiez une ressource d’Experience Manager Assets vers Brand Portal. Si la connexion est établie, la ressource publiée est visible dans l’interface de Brand Portal.


Vous pouvez maintenant effectuer les tâches suivantes :

* [Publier des ressources d’Experience Manager Assets vers Brand Portal.](publish-to-brand-portal.md)
* [Publier des dossiers d’Experience Manager Assets vers Brand Portal.](publish-to-brand-portal.md#publish-folders-to-brand-portal)
* [Publier des collections d’Experience Manager Assets vers Brand Portal.](publish-to-brand-portal.md#publish-collections-to-brand-portal)
* [Publication de ressources de Brand Portal vers Experience Manager Assets](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html?lang=fr) - Approvisionnement de ressources dans Brand Portal
* [Publication de paramètres prédéfinis, de schémas et de facettes sur Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html?lang=fr)
* [Publication de balises sur Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html?lang=fr)

Pour plus d’informations, voir [Publication de balises sur Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html?lang=fr).

**Journaux de distribution**

Vous pouvez surveiller les journaux de l’agent de distribution correspondant au workflow de publication de ressources.

Publions maintenant une ressource d’Experience Manager Assets vers Brand Portal et examinons les journaux.

1. Suivez les étapes (1 à 4), comme indiqué dans la section **Test de la connexion**, puis accédez à la page de l’agent de distribution.
1. Cliquez sur **[!UICONTROL Journaux]** pour afficher les journaux de traitement et d’erreurs.

   ![Journaux de traitement et d’erreurs](assets/test-bpconfig5.png)

L’agent de distribution génère les journaux suivants :

* INFO : il s’agit d’un journal généré par le système qui se déclenche lors d’une configuration réussie de l’agent de distribution.
* DSTRQ1 (requête 1) : Déclencheurs lors du test de la connexion.

Lors de la publication de la ressource, les journaux de requête et de réponse suivants sont générés :

**Requête de l’agent de distribution** :

* DSTRQ2 (requête 2) : La requête de publication de ressource est déclenchée.
* DSTRQ3 (requête 3) : le système déclenche une autre requête pour publier le dossier Experience Manager Assets (dans lequel se trouve la ressource) et réplique le dossier dans Brand Portal.

**Réponse de l’agent de distribution** :

* queue-bpdistributionagent0 (DSTRQ2) : La ressource est publiée sur Brand Portal.
* queue-bpdistributionagent0 (DSTRQ3) : le système réplique le dossier Experience Manager Assets (contenant la ressource) dans Brand Portal.

Dans l’exemple ci-dessus, une requête et une réponse supplémentaires sont déclenchées. Le système n’a pas trouvé le dossier parent (Ajouter chemin d’accès) dans Brand Portal, car la ressource a été publiée pour la première fois. Par conséquent, il a déclenché une requête supplémentaire pour créer un dossier parent portant le même nom dans Brand Portal à l’emplacement où la ressource est publiée.

>[!NOTE]
>
>Une requête supplémentaire est générée au cas où le dossier parent n’existe pas dans Brand Portal ou a été modifié dans Experience Manager Assets.

Outre le workflow d’automatisation de l’activation de Brand Portal sur Experience Manager Assets as a [!DNL Cloud Service], il existe une autre méthode permettant de configurer manuellement Experience Manager Assets as a [!DNL Cloud Service] avec Brand Portal à l’aide d’Adobe Developer Console, mais elle n’est plus recommandée.

>[!NOTE]
>
>Contactez le service clientèle si vous rencontrez un problème lors de l’activation de votre client Brand Portal.

## Configuration manuelle à l’aide d’Adobe Developer Console {#manual-configuration}

>[!NOTE]
>
> Vous ne pourrez plus créer de nouvelles informations d’identification JWT à partir de juin 2024. Désormais, seules les informations d’identification OAuth sont créées.
> En savoir plus [création d’une configuration OAuth](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/security/setting-up-ims-integrations-for-aem-as-a-cloud-service#creating-oauth-configuration:~:text=For%20example%3A-,Creating%20an%20OAuth%20configuration,-To%20create%20a).

La section suivante décrit comment configurer manuellement Experience Manager Assets as a [!DNL Cloud Service] avec Brand Portal à l’aide d’Adobe Developer Console.

Auparavant, Experience Manager Assets as a [!DNL Cloud Service] était configuré manuellement avec Brand Portal par le biais d’Adobe Developer Console, qui fournissait un jeton de compte Identity Management Services (IMS) Adobe pour l’autorisation du client Brand Portal. Cela nécessite des configurations à la fois dans Experience Manager Assets et dans l’Adobe Developer Console.

<!--1. In Experience Manager Assets, create an IMS account and generate a public key (certificate).-->
<!--1. Under the project, configure an API using the public key to create a service account connection.
1. Get the service account credentials and JSON Web Token (JWT) payload information.
1. In Experience Manager Assets, configure the IMS account using the service account credentials and JWT payload.-->
1. Dans Adobe Developer Console, créez un projet pour votre client Brand Portal (organisation).
1. Dans Experience Manager Assets, configurez le service cloud Brand Portal à l’aide du compte IMS et du point d’entrée Brand Portal (URL de l’organisation).
1. Testez votre configuration en publiant une ressource d’Experience Manager Assets sur Brand Portal.

>[!NOTE]
>
>Une instance Experience Manager Assets as a [!DNL Cloud Service] ne doit être configurée qu’avec un seul client Brand Portal.

**Conditions préalables**

Pour configurer Experience Manager Assets avec Brand Portal, vous devez disposer des éléments suivants :

* Une instance Experience Manager Assets as a [!DNL Cloud Service] opérationnelle.
* Une adresse URL du client Brand Portal
* Un utilisateur disposant de droits d’administrateur système sur l’organisation IMS du client Brand Portal

## Créer une configuration {#create-new-configuration}

Procédez comme suit dans la séquence spécifiée pour configurer Experience Manager Assets avec Brand Portal.

1. [Configurer les informations d’identification OAuth dans Adobe Developer Console](#config-oauth)
1. [Créer une intégration Adobe IMS à l’aide d’OAuth](#create-ims-account-configuration)
1. [Configuration du service cloud](#configure-cloud-service)
   <!--1. [Obtain public certificate](#public-certificate)-->
<!--1. [Create service account (JWT) connection](#createnewintegration) 
1. [Configure IMS account](#create-ims-account-configuration)-->

<!--
### Create IMS configuration {#create-ims-configuration}

The IMS configuration authenticates your Experience Manager Assets as a [!DNL Cloud Service] instance with the Brand Portal tenant. 

IMS configuration includes two steps:

* [Obtain public certificate](#public-certificate) 
* [Configure IMS account](#create-ims-account-configuration)
-->
<!--

### Obtain public certificate {#public-certificate}

The public key (certificate) authenticates your profile on Adobe Developer Console.

1. Login to Experience Manager Assets.
1. From the **Tools** panel, navigate to **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**.
1. In Adobe IMS Configurations page, click **[!UICONTROL Create]**. It will redirect to the **[!UICONTROL Adobe IMS Technical Account Configuration]** page. By default, the **Certificate** tab opens.
1. Select **[!UICONTROL Adobe Brand Portal]** in the **[!UICONTROL Cloud Solution]** drop-down list.  
1. Select the **[!UICONTROL Create new certificate]** check box and specify an **alias** for the public key. The alias serves as name of the public key. 
1. Click **[!UICONTROL Create certificate]**. Then, click **[!UICONTROL OK]** to generate the public key.

   ![Create Certificate](assets/ims-config2.png)

1. Click the **[!UICONTROL Download Public Key]** icon and save the public key (CRT) file on your machine.

   The public key is used later to configure API for your Brand Portal tenant and generate service account credentials in Adobe Developer Console.  

   ![Download Certificate](assets/ims-config3.png)

1. Click **[!UICONTROL Next]**.

    In the **Account** tab, Adobe IMS account is created which requires the service account credentials that are generated in Adobe Developer Console. Keep this page open for now.

    Open a new tab and [create a service account (JWT) connection in Adobe Developer Console](#createnewintegration) to get the credentials and JWT payload for configuring the IMS account. 
-->
<!--

### Create service account (JWT) connection {#createnewintegration}

In Adobe Developer Console, projects and APIs are configured at Brand Portal tenant (organization) level. Configuring an API creates a service account (JWT) connection. There are two methods to configure API, by generating a key pair (private and public keys) or by uploading a public key. To configure Experience Manager Assets with Brand Portal, you must generate a public key (certificate) in Experience Manager Assets and create credentials in Adobe Developer Console by uploading the public key. These credentials are required to configure the IMS account in Experience Manager Assets. Once the IMS account is configured, you can configure the Brand Portal cloud service in Experience Manager Assets.

Perform the following steps to generate the service account credentials and JWT payload:

1. Login to Adobe Developer Console with system administrator privileges on the IMS organization (Brand Portal tenant). The default URL is [https://www.adobe.com/go/devs_console_ui](https://www.adobe.com/go/devs_console_ui).


   >[!NOTE]
   >
   >Ensure that you have selected the correct IMS organization (Brand Portal tenant) from the drop-down (organization) list located at the upper-right corner.

1. Click **[!UICONTROL Create new project]**. A blank project with a system-generated name is created for your organization. 

   Click **[!UICONTROL Edit project]** to update the **[!UICONTROL Project Title]** and **[!UICONTROL Description]**, and click **[!UICONTROL Save]**.
   
1. In the **[!UICONTROL Project overview]** tab, click **[!UICONTROL Add API]**.

1. In the **[!UICONTROL Add an API window]**, select **[!UICONTROL AEM Brand Portal]** and click **[!UICONTROL Next]**. 

   Ensure that you have access to the Experience Manager Brand Portal service.

1. In the **[!UICONTROL Configure API]** window, click **[!UICONTROL Upload your public key]**. Then, click **[!UICONTROL Select a File]** and upload the public key (.crt file) that you have downloaded in the [obtain public certificate](#public-certificate) section. 

   Click **[!UICONTROL Next]**.

   ![Upload Public Key](assets/service-account3.png)

1. Verify the public key and click **[!UICONTROL Next]**.

1. Select **[!UICONTROL Assets Brand Portal]** as the default product profile and click **[!UICONTROL Save configured API]**. 

   ![Select Product Profile](assets/service-account4.png)

1. Once the API is configured, you are redirected to the API overview page. From the left navigation under **[!UICONTROL Credentials]**, click the **[!UICONTROL Service Account (JWT)]** option.

   >[!NOTE] 
   >
   >* You can view the credentials and perform actions such as generate JWT tokens, copy credential details, retrieve client secret, and so on.
   >* Currently, only the Adobe's Developer Console Service Account (JWT) credential type is supported. Do not use the `OAuth Server-to-Server` credential type until it is supported in mid-April. Read more at [JWT Credentials Deprecation in Adobe Developer Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/jwt-credentials-deprecation-in-adobe-developer-console.html?lang=fr).

1. From the **[!UICONTROL Client Credentials]** tab, copy the **[!UICONTROL client ID]**. 

   Click **[!UICONTROL Retrieve Client Secret]** and copy the **[!UICONTROL client secret]**.

   ![Service Account Credentials](assets/service-account5.png)

1. Navigate to the **[!UICONTROL Generate JWT]** tab and copy the **[!UICONTROL JWT Payload]** information. 

You can now use the client ID (API key), client secret, and JWT payload to [configure the IMS account](#create-ims-account-configuration) in Experience Manager Assets.
-->
<!--
1. Click **[!UICONTROL Create Integration]**.

1. Select **[!UICONTROL Access an API]**, and click **[!UICONTROL Continue]**.

   ![Create New Integration](assets/create-new-integration1.png)

1. Create an integration page. 
   
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

   The API Key, Client Secret key, and JWT payload information is used to create IMS account configuration.

-->

### Configurer les informations d’identification OAuth dans Adobe Developer Console {#config-oauth}

[Configurez les informations d’identification OAuth dans Adobe Developer Console](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/security/setting-up-ims-integrations-for-aem-as-a-cloud-service#credentials-in-the-developer-console) puis sélectionnez API Brand Portal.

### Créer une nouvelle intégration Adobe IMS à l’aide d’OAuth {#create-ims-account-configuration}

[Créez une intégration Adobe IMS à l’aide d’OAuth](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/security/setting-up-ims-integrations-for-aem-as-a-cloud-service#creating-oauth-configuration) et sélectionnez Brand Portal dans la liste déroulante sous Solution cloud.

<!--
Ensure that you have performed the following steps:

* [Obtain public certificate](#public-certificate)
* [Create service account (JWT) connection](#createnewintegration)
-->

<!--1. Open the IMS Configuration and navigate to the **[!UICONTROL Account]** tab. Keep the page open while [obtaining the public certificate](#public-certificate).

1. Specify a **[!UICONTROL Title]** for the IMS account.

   In the **[!UICONTROL Authorization Server]** field, specify the URL: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)  
-->
<!--
1. Complete the configuration based on details from the [Developer Console](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/). Click **[!UICONTROL Create]**.
-->
<!--Specify client ID in the **[!UICONTROL API key]** field, **[!UICONTROL Client Secret]**, and **[!UICONTROL Payload]** (JWT payload) that you have copied while [creating the service account (JWT) connection](#createnewintegration).

   The IMS account is configured. 

   ![IMS Account configuration](assets/create-new-integration6.png)

 <!--  
1. Select the IMS account configuration and click **[!UICONTROL Check Health]**.

   Click **[!UICONTROL Check]** in the dialog box. On successful configuration, a message appears that the *Token is retrieved successfully*.

   ![Adobe IMS Configurations Check Health.](assets/create-new-integration5.png)
-->
<!--
>[!CAUTION]
>
>You must have only one IMS configuration.
>
>Ensure that the IMS configuration passes the health check. If the configuration does not pass the health check, it is invalid. You must delete it and create another valid configuration.
-->

### Configuration du service cloud {#configure-cloud-service}

Pour configurer le service cloud Brand Portal, procédez comme suit :

1. Connectez-vous à Experience Manager Assets.

1. Dans le panneau **Outils**, accédez à **[!UICONTROL Cloud Services]** > **[!UICONTROL AEM Brand Portal]**.

1. Dans la page Configurations Brand Portal, cliquez sur **[!UICONTROL Créer]**.

1. Saisissez un **[!UICONTROL titre]** pour la configuration.

   Sélectionnez la configuration IMS que vous avez créée lors de la [configuration du compte IMS](#create-ims-account-configuration).

   Dans le champ **[!UICONTROL URL du service]**, entrez l’adresse URL de votre client Brand Portal (organisation).

   Boîte de dialogue de configuration de Brand Portal ![](assets/create-cloud-service.png).

1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**. La configuration cloud est alors créée.

   Votre instance Experience Manager Assets as a [!DNL Cloud Service] est maintenant configurée avec le client Brand Portal.

Vous pouvez maintenant tester la configuration en vérifiant l’agent de distribution et en publiant les ressources sur Brand Portal.

**Placer sur la liste autorisée les adresses IP sortantes dans SPS si l&#39;aperçu sécurisé est activé**
Si vous utilisez Dynamic Media en mode Scene7 avec l’option [aperçu sécurisé activé](#https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/testing-assets-making-them-public.html?lang=fr) pour une entreprise, il est conseillé à l’administrateur de l’entreprise Scene7 [de placer sur la liste autorisée les adresses IP sortantes publiques](#https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/testing-assets-making-them-public.html?lang=fr#testing-the-secure-testing-service) pour les régions respectives à l’aide de l’interface utilisateur Flash de SPS (Scene7 Publishing System).
Les adresses IP sortantes sont les suivantes :

| **Zone géographique** | **Adresse IP de sortie** |
|--- |--- |
| N/A | 130.248.160.68, 20.94.203.130 |
| EMEA | 51.132.146.75, 130.248.244.202, 130.248.244.203, 130.248.244.204, 130.248.244.210, 130.248.244.211, 130.248.244.212 |
| APAC | 63.140.44.54 |

<!--
### Test configuration {#test-configuration}

Perform the following steps to validate the configuration:

1. Login to AEM Assets.

1. From the **Tools** panel, navigate to **[!UICONTROL Deployment]** > **[!UICONTROL Distribution]**.

    ![test-bpconfig1](assets/test-bpconfig1.png)

   A Brand Portal distribution agent (**[!UICONTROL bpdistributionagent0]**) is created under **[!UICONTROL Publish to Brand Portal]**.

   ![test-bpconfig2](assets/test-bpconfig2.png)


1. Click **[!UICONTROL Publish to Brand Portal]** to open the distribution agent. 

   You can see the distribution queues under the **[!UICONTROL Status]** tab. 
   
   A distribution agent contains two queues: 
   * **processing-queue**: for the distribution of assets to Brand Portal. 

   * **error-queue**: for the assets where distribution has failed. 
   
   >[!NOTE]
   >
   >It is recommended to review the failures and  clear the **error-queue** periodically.  

   ![test-bpconfig3](assets/test-bpconfig3.png)

1. To verify the connection between AEM Assets as a [!DNL Cloud Service] and Brand Portal, click the **[!UICONTROL Test Connection]** icon.

   ![test-bpconfig4](assets/test-bpconfig4.png)

   A message appears that your *test package is successfully delivered*.

   >[!NOTE]
   >
   >Avoid disabling the distribution agent, as it can cause the distribution of the assets (running-in-queue) to fail.

You can now:

* [Publish assets from AEM Assets to Brand Portal](publish-to-brand-portal.md)
* [Publish folders from AEM Assets to Brand Portal](publish-to-brand-portal.md#publish-folders-to-brand-portal)
* [Publish collections from AEM Assets to Brand Portal](publish-to-brand-portal.md#publish-collections-to-brand-portal)
* [Publish assets from Brand Portal to AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html?lang=fr) - Asset Sourcing in Brand Portal
* [Publish presets, schemas, and facets to Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html?lang=fr)
* [Publish tags to Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html?lang=fr)

See [Brand Portal documentation](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html?lang=fr) for more information.

## Distribution logs {#distribution-logs}

You can monitor the distribution agent logs for the asset publishing workflow. 

For example, we have published an asset from AEM Assets to Brand Portal to validate the configuration. 

1. Follow the steps (from 1 to 4) as shown in the [Test Configuration](#test-configuration) section and navigate to the distribution agent page.
1. Click **[!UICONTROL Logs]** to view the processing and error logs.

   ![ctest-bpconfig4](assets/ctest-bpconfig4.png)

The distribution agent has generated the following logs:

* INFO: This is a system-generated log that triggers on successful configuration of the distribution agent. 
* DSTRQ1 (Request 1): Triggers on test connection.

On publishing the asset, the following request and response logs are generated:

**Distribution agent request**:

* DSTRQ2 (Request 2): The asset publishing request is triggered.
* DSTRQ3 (Request 3): The system triggers another request to publish the AEM Assets folder (in which the asset exists) and replicates the folder in Brand Portal.

**Distribution agent response**:

* queue-bpdistributionagent0 (DSTRQ2): The asset is published to Brand Portal.
* queue-bpdistributionagent0 (DSTRQ3): The system replicates the AEM Assets folder (containing the asset) in Brand Portal.

In the above example, an additional request and response is triggered. The system could not find the parent folder (Add Path) in Brand Portal because the asset was published for the first time, therefore, it triggered an additional request to create a parent folder with the same name in Brand Portal where the asset is published.  

>[!NOTE]
>
>Additional request is generated in case the parent folder does not exist in Brand Portal or has been modified in AEM Assets. 
-->

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

**Voir également**

* [Traduire les ressources](translate-assets.md)
* [API HTTP Assets](mac-api-assets.md)
* [Formats de fichiers pris en charge par Assets](file-format-support.md)
* [Rechercher des ressources](search-assets.md)
* [Ressources connectées](use-assets-across-connected-assets-instances.md)
* [Rapports de ressources](asset-reports.md)
* [Schémas de métadonnées](metadata-schemas.md)
* [Télécharger des ressources](download-assets-from-aem.md)
* [Gestion des métadonnées](manage-metadata.md)
* [Facettes de recherche](search-facets.md)
* [Gérer les collections](manage-collections.md)
* [Import des métadonnées en bloc](metadata-import-export.md)
* [Publier des ressources sur AEM et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
