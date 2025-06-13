---
title: Activer [!DNL Dynamic Media] Prime et Ultimate
description: Découvrez comment activer les offres  [!DNL Dynamic Media] Prime et Ultimate.
feature: Asset Management
role: User, Admin
exl-id: 0ee161f5-bf44-41f1-928e-c07574fd43cc
source-git-commit: 82a3016149645701abe829ad89c493f480956267
workflow-type: tm+mt
source-wordcount: '1075'
ht-degree: 4%

---

# Activer [!DNL Dynamic Media] Prime et Ultimate {#enable-dynamic-media-prime-and-ultimate}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime et Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Intégration d’AEM Assets à Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Extensibilité de l’IU</b></a>
        </td>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Bonnes pratiques de recherche</b></a>
        </td>
    </tr>
    <tr>
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

[!DNL Adobe Experience Manager] as a Cloud Service vous permet d’accéder [!DNL Dynamic Media] offres Prime et Ultimate afin de rationaliser vos workflows numériques et d’optimiser la gestion de contenu. Voir [Dynamic Media Prime et Ultimate](/help/assets/dynamic-media/dm-prime-ultimate.md) pour en connaître les avantages et connaître les principales différences.

Cet article fournit le workflow de bout en bout pour activer les offres [!DNL Dynamic Media] Prime et Ultimate.

## Activer [!DNL Dynamic Media] Ultimate {#enable-dynamic-media-ultimate}

Pour activer [!DNL Dynamic Media] Ultimate :

1. [Activer [!DNL Dynamic Media with OpenAPI]](#activate-dynamic-media-with-openapi)
1. [Configurer [!DNL Dynamic Media] solutions](#configure-dynamic-media-solutions)
1. [Créer et répertorier  [!DNL Dynamic Media]  entreprises](#create-and-list-dynamic-media-companies)
1. [Configurer un domaine personnalisé dans le niveau de diffusion](#configure-custom-domain-in-delivery-tier)

<!--
1. [Onboard API keys using the [!DNL AEM] [!DNL Dynamic Media] API card](#onboarding-api-keys)
-->

Si vous devez activer le [!DNL Dynamic Media Prime], consultez les liens rapides fournis dans [Activer [!DNL Dynamic Media Prime]](#enable-dynamic-media-prime).

### Activer [!DNL Dynamic Media with OpenAPI] {#activate-dynamic-media-with-openapi}

[!DNL Dynamic Media] avec les fonctionnalités OpenAPI, la gestion des ressources numériques (DAM) est au cœur d’un écosystème de chaîne d’approvisionnement de contenu agile et efficace qui garantit la gouvernance et la diffusion des ressources.

La première étape du processus d’activation d’[!DNL Dynamic Media] Ultimate consiste à activer [[!DNL Dynamic Media] avec OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) pour votre environnement Cloud Service.

#### Préparez-vous à démarrer {#prerequisites}

Assurez-vous de remplir les conditions suivantes avant de commencer le processus d’activation :

1. [Accès à Cloud Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager).
1. [Votre programme comprend  [!DNL Dynamic Media]  solutions](#configure-dynamic-media-solutions).
1. Vous disposez d’[!DNL Dynamic Media] licence Prime ou Ultimate.

#### Activation des fonctionnalités [!DNL Dynamic Media with OpenAPI] dans votre environnement Cloud Service {#enable-dynamic-media-with-openapi-capabilites-in-your-CS-environment}

Pour activer le [!DNL Dynamic Media with OpenAPI] pour votre environnement de service cloud, procédez comme suit :

1. [Accédez à l’interface utilisateur de Cloud Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager).

1. [Créez un environnement](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/onboarding/journey/create-environments) si vous n’avez pas accès à un environnement existant.

1. Sélectionnez **[!UICONTROL Cliquer pour activer]** dans la ligne **[!UICONTROL Dynamic Media]** de la section **[!UICONTROL Informations sur l’environnement]** de la page Détails de l’environnement.

   ![activer Dynamic Media avec les fonctionnalités OpenAPI](/help/assets/assets/activate-adv-capabiliites-of-dm-openAPI.png)

1. Cliquez sur **[!UICONTROL Activer]** dans la boîte de dialogue de confirmation pour lancer le processus d’activation du [!DNL Dynamic Media with OpenAPI]. Une fois l’activation réussie, le Cloud Manager affiche les mises à jour de statut suivantes :
   1. **[!UICONTROL Étape de l’environnement]** : **[!UICONTROL En cours d’exécution]**
   1. ![DM activated](/help/assets/assets/Images_icon.svg)**[!UICONTROL Dynamic Media &#x200B;]**:**[!UICONTROL &#x200B; les fonctionnalités OpenAPI sont activées &#x200B;]**

      ![ activation réussie ](/help/assets/assets/activation-successful.png){width="700" align="left"}

#### Réessayer l’activation {#retry-activation}

Si l’activation échoue, le Cloud Manager affiche les mises à jour de statut suivantes :

* **[!UICONTROL Étape de l’environnement]** : échec de **[!UICONTROL DM avec OpenAPI]**
* ![DM activated](/help/assets/assets/Images_icon.svg)**[!UICONTROL Dynamic Media &#x200B;]**: échec de l’activation des fonctionnalités&#x200B;**[!UICONTROL &#x200B; OpenAPI &#x200B;]**

  ![réessayer l’activation](/help/assets/assets/retry-dm-openapi-failed-activation.png){width="700" align="left"}

Sélectionnez **[!UICONTROL Cliquer pour réessayer]** pour redémarrer l’activation.

Vous pouvez également exécuter les étapes suivantes pour redémarrer le processus d’activation :

1. Accédez à la page qui répertorie tous les environnements.

1. Cliquez sur Plus d’options (![plus d’options](/help/assets/assets/three-dots.svg)) à la fin de la ligne de votre environnement.

1. Sélectionnez **[!UICONTROL Réessayer DM avec l’activation OpenAPI]** pour redémarrer l’activation.

   ![réessayer l’activation à partir de la page détails de l’environnement](/help/assets/assets/restart-activation-process-from-list-environment-page.png)

### Configuration des solutions [!DNL Dynamic Media] {#configure-dynamic-media-solutions}

Configurez les solutions [!UICONTROL Dynamic Media] pour utiliser les fonctionnalités de base et avancées de [Dynamic Media avec OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) sur les environnements existants ou nouveaux disponibles dans Cloud Manager.

#### Préparez-vous à démarrer {#prerequisites-to-configure-dynamic-media-solutions}

Vérifiez que vous disposez des éléments suivants pour configurer les solutions [!UICONTROL Dynamic Media] :

1. [Accès à Cloud Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager).
1. Vous disposez d’[!DNL Dynamic Media] licence Ultimate.

#### Configuration de solutions [!DNL Dynamic Media] pour la diffusion de ressources {#configure-dynamic-media-solutions-for-asset-delivery}

Procédez comme suit :

1. [Créez un programme](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/onboarding/journey/create-program) ou accédez à un programme existant et cliquez sur **[!UICONTROL Modifier]**. La page **[!UICONTROL Configurer pour la production]** affiche l’onglet **[!UICONTROL Solutions et modules complémentaires]**.

1. Sélectionnez **[!UICONTROL Assets]**, **[!UICONTROL Assets Prime]**, **[!UICONTROL Assets Ultimate]** ou **[!UICONTROL Sites]** pour ajouter la solution **[!UICONTROL Dynamic Media]** à votre programme.

1. Sélectionnez la solution **[!UICONTROL Dynamic Media]** et cliquez sur **[!UICONTROL Continuer]** pour ajouter la solution **[!UICONTROL Dynamic Media]** à votre programme. Cette action redémarre tous les environnements existants de votre programme et leur ajoute la solution [!DNL Dynamic Media]. En outre, tout nouvel environnement créé dans votre programme est automatiquement [!DNL Dynamic Media].

   ![configuration pour la production](/help/assets/assets/set-up-for-prod.png){width="500" align="left"}

Voir [Activer [!DNL Dynamic Media with OpenAPI]](#activate-dynamic-media-with-openapi) pour commencer à utiliser les fonctionnalités de [!DNL Dynamic Media] avec les fonctionnalités OpenAPI dans votre environnement.

### Créer et lister [!DNL Dynamic Media] entreprises {#create-and-list-dynamic-media-companies}

Créez et répertoriez [!DNL Dynamic Media] sociétés dans votre environnement de service cloud AEM pour gérer les configurations dans votre environnement AEM.

#### Préparez-vous à démarrer {#prerequisites-to-create-and-list-dynamic-media-companies}

Pour afficher les sociétés (comptes) existantes ou ajouter une nouvelle société (compte) [!DNL Dynamic Media] dans votre organisation IMS, vous devez disposer des éléments suivants :

1. [Accès à Cloud Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager).

1. Vous disposez d’[!DNL Dynamic Media] licence Ultimate.

#### Créer et répertorier [!DNL Dynamic Media] sociétés dans votre organisation IMS {#create-and-list-dynamic-media-companies-in-your-ims-organisation}

Pour créer et répertorier une nouvelle société [!DNL Dynamic Media] (compte) configurable dans votre environnement de [!DNL AEM], procédez comme suit :

1. Accédez à la page de licence [Cloud Manager](https://experience-stage.adobe.com/#/@ssahnichstage/cloud-manager/license).

1. Cliquez sur **[!UICONTROL Ajouter une entreprise]** et la boîte de dialogue **[!UICONTROL Créer une entreprise Dynamic Media]** s’affiche.

1. Indiquez un nom de société [!DNL Dynamic Media] unique, sélectionnez une région de société et ajoutez une liste d’ID de messagerie d’administration de société séparés par des virgules.

   ![Créer une société Dynamic Media](/help/assets/assets/create-dynamic-media-company.png){width="500" align="left"}

1. Cliquez sur **[!UICONTROL Créer]** pour commencer à créer votre entreprise. Cette action ajoute une nouvelle ligne à **[!UICONTROL [!DNL Dynamic Media]section sociétés]** et affiche **[!UICONTROL Configuration]** comme **[!UICONTROL STATUT]** de la société.

   ![création d’entreprise Dynamic Media initiée](/help/assets/assets/dm-company-creation-initiated.png)

1. **Facultatif :** cliquez sur ![icône d’informations](/help/assets/assets/info-icon-solid-black.svg) pour afficher les détails de l’entreprise. Le **[!UICONTROL STATUS]** est mis à jour sur **[!UICONTROL Ready]** lors de la création de l’entreprise.

   ![Informations sur l’entreprise Dynamic Media](/help/assets/assets/dm-company-information.png)

1. En tant qu’administrateur ou administratrice Dynamic Media, recherchez dans votre boîte aux lettres un e-mail de bienvenue contenant la liste des étapes à suivre pour [configurer [!DNL Dynamic Media]](/help/assets/dynamic-media/config-dm.md#architecture-diagram-of-dynamic-media) une société dans votre environnement Cloud Service [!DNL AEM] afin de commencer.

   ![email de bienvenue](/help/assets/assets/welcome-email.png)

#### Reprise de la création de l’entreprise {#retry-company-creation}

Si [!DNL Dynamic Media] création d’entreprise échoue, procédez comme suit en fonction du statut d’échec :

1. Si le **[!UICONTROL Statut]** est En attente, signalez le problème à l’équipe du service clientèle pour résolution.


   ![statut en attente](/help/assets/assets/company-creation-pending-status.png){width="350" align="center"}



1. Si la **[!UICONTROL Statut]** a échoué, réessayez en fonction de la raison de l’échec.

   ![statut en échec](/help/assets/assets/company-creation-failure-status.png){width="380" align="center"}

### Facultatif : configuration d’un domaine personnalisé dans le niveau de diffusion {#configure-custom-domain-in-delivery-tier}

Bien qu’AEM as a Cloud Service soit fourni avec un domaine par défaut, vous pouvez le personnaliser en fonction de vos besoins. Associez un domaine personnalisé au niveau de diffusion à l’aide de Cloud Manager.

#### Préparez-vous à démarrer {#prerequisites-to-configure-custom-domain-in-delivery-tier}

Assurez-vous de répondre aux exigences suivantes avant de démarrer le processus de configuration :

1. [Accès à Cloud Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager).
1. [Déjà activé [!DNL Dynamic Media with OpenAPI] dans votre environnement](#activate-dynamic-media-with-openapi).
1. Activation du [!DNL Dynamic Media with OpenAPI] à l’état prêt.
1. Certificat de type EV ou OV pour le domaine à utiliser pour le niveau de diffusion. Voir [Présentation des certificats SSL](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/introduction-to-ssl-certificates) pour plus d’informations.

#### Configuration d’un domaine personnalisé dans le niveau de diffusion à l’aide de Cloud Manager {#configure-custom-domain-in-delivery-tier-using-cloud-manager}

Exécutez les étapes suivantes dans Cloud Manager pour configurer un domaine personnalisé dans le niveau de diffusion :

1. [Ajoutez un certificat SSL géré par le client](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/add-ssl-certificate#add-customer-managed-ssl-cert).

1. [Ajoutez un nom de domaine personnalisé](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name#adding-cdn-settings).

1. Accédez à la page des détails de l’environnement et [ajoutez une configuration CDN](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/domain-mappings/add-domain-mapping). Lors de l’ajout de la configuration, sélectionnez **[!UICONTROL Diffusion]** dans le champ **[!UICONTROL Niveau]** de la boîte de dialogue **[!UICONTROL Configurer le réseau CDN]**.

   ![Configurer le réseau CDN](/help/assets/assets/select-delivery-tier-in-configure-cdn-form.png)

   Après avoir ajouté les configurations, le **[!UICONTROL STATUT]** de **[!UICONTROL Configurations du réseau CDN]** passe à **[!UICONTROL Appliqué]**.

   ![Configuration du statut de déploiement du réseau CDN](/help/assets/assets/cdn-configuration-deployment-status.png)

1. Cliquez sur Autres options (![Autres options](/help/assets/assets/three-dots.svg)) et sélectionnez **[!UICONTROL Préparation à la mise en production]** pour afficher la boîte de dialogue **[!UICONTROL Préparation à la mise en production]**.

   ![option de préparation en ligne](/help/assets/assets/go-live-readiness-option.png)

1. Exécutez les étapes **[!UICONTROL Configurer CNAME]** pour mapper les `cdn.adobeaemcloud.com` (enregistrement CNAME) dans l’enregistrement DNS du fournisseur de services DNS. Ce mappage garantit que les requêtes reçues au niveau du domaine personnalisé sont redirigées vers le réseau CDN d’Adobe.

   ![boîte de dialogue de préparation à la mise en production](/help/assets/assets/go-live-readiness-dialogbox.png){width="500" align="left"}

1. Cliquez sur **[!UICONTROL Ok]**, le **[!UICONTROL STATUT]** se met à jour sur **[!UICONTROL Vérifié]**. Le domaine personnalisé est prêt à être utilisé dans l’URL de diffusion.


   ![Configurer le réseau CDN](/help/assets/assets/cdn-configurations-varified.png)



<!--
### Onboard API keys {#onboarding-api-keys}

Create an API key to access [!DNL Dynamic Media] with OpenAPIs and the delivery tier backed Asset Selector.

#### Prepare yourself for API keys onboarding process {#prerequisites-for-onboarding-api-keys} 

To start the API keys onboarding process, ensure you have:

1. [Access to Cloud Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager).
1. [Activated [!DNL Dynamic Media with OpenAPI] in your environment](#activate-dynamic-media-with-openapi).
1. [Access to the Adobe Developer Console](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis#create-adobe-developer-console-adc-project).

#### Onboard the API keys using [!DNL AEM Dynamic Media] API card {#onboarding-api-keys-using-aem-dynamic-media-api-card}

Use the [Adobe Developer Console](https://developer.adobe.com/developer-console/) to onboard the API keys to:

1. [Access Dynamic Media APIs](#access-dynamic-media-apis)
1. [Access Delivery tier backed Asset Selector](#access-delivery-tier-backed-asset-selector)

#### Create an API key to access [!DNL Dynamic Media] with OpenAPIs {#access-dynamic-media-apis}

Execute the following steps to create an API key to access [!DNL Dynamic Media] with OpenAPIs:

1. Navigate to the **[!UICONTROL Admin Console]**. The Admin Console displays the **[!UICONTROL author]**, **[!UICONTROL delivery]** and **[!UICONTROL publish]** instances.
![instances on admin console](/help/assets/assets/delivery-instance-admin-console.png)
1. Select the **[!UICONTROL delivery]** instance to display the product profile with **[!UICONTROL AEM Dynamic Media enable API Services]** enabled by default. The product profile looks like this: **[!UICONTROL AEM Assets DM OpenAPI Users - delivery  - Program [ID Number] - Environment [ID Number]]**. 

   ![product profile on admin console](/help/assets/assets/admin-console-product-profile.png)

   >[!NOTE]
   >
   >This delivery instance is common for [!DNL Content Hub] and [!DNL Dynamic Media] with OpenAPI capabilities.

1. Navigate to the [Adobe Developer console](https://developer.adobe.com/console) and [create a new project](https://developer.adobe.com/dep/guides/dev-console/create-project/). See [Invoke OpenAPI-based AEM APIs for server to server authentication](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) to learn about creating a new project.
1. Select **[!UICONTROL AEM Dynamic Media API]** to access to the [!DNL Dynamic Media with OpenAPI capabilities] and click **[!UICONTROL Next]**.
![adobe developer console](/help/assets/assets/adobe-developer-console.png)
1. Select **[!UICONTROL Server-to-Server Authentication]** and click **[!UICONTROL Next]**. See [Server to Server authentication](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/) to learn more about this authentication type.
![server-to-server-authentication](/help/assets/assets/server-to-server-authentication.png)
1. Select **[!UICONTROL OAuth Server-to-Server]**, specify a unique **[!UICONTROL Credential name]** and click **[!UICONTROL Next]**.
![oauth server to server credential](/help/assets/assets/oauth-server-server-and-credential-name.png)
1. Select your product profile (mentioned in step 2) to access the APIs using the environment's delivery endpoint and click **[!UICONTROL Save configured API]**.
![select product profile](/help/assets/assets/select-product-profile.png)
1. Select **[!UICONTROL AEM Dynamic Media API]**. Use the **[!UICONTROL OAuth Server-to-Server]** to fetch the **X-API-key** and access the token for the **authorization** header. 
![oauth server to server](/help/assets/assets/oauth-server-to-server-credentials.png)
Execute the below steps to use [Dynamic Media with OpenAPIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/) using the **[!UICONTROL OAuth Server-to-Server]** credentials. 
    1. Copy the **[!UICONTROL API KEY (Client ID)]** and replace the `X-Api-Key` in the cURL.
    1. Click **[!UICONTROL Generate access token]** to generate an access token and replace `YOUR_JWT_HERE` with the token in the cURL.

The cURL looks like this:
```
headers: {
    'Content-Type': 'application/json',
      'X-Adobe-Accept-Experimental': '1',
      Authorization: 'Bearer <YOUR_JWT_HERE>',
      'X-Api-Key': 'YOUR_API_KEY_HERE'
    `},
```
See [Search Assets API](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dynamic-media-open-apis/search-assets-api#search-assets-api-header) for more information.

### Access Delivery tier backed Asset Selector {#access-delivery-tier-backed-asset-selector}

TBD: Wiki in progress..
-->

## Activer [!DNL Dynamic Media] Prime {#enable-dynamic-media-prime}

Pour activer [!DNL Dynamic Media] Prime :

1. [Activer Dynamic Media avec OpenAPI](#activate-dynamic-media-with-openapi)
1. [Facultatif : configuration d’un domaine personnalisé dans le niveau de diffusion](#configure-custom-domain-in-delivery-tier)

<!--
1. [Onboard API keys using the AEM Dynamic Media API card](#onboarding-api-keys)
-->
