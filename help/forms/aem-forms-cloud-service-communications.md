---
title: Comment utiliser Forms as a Cloud Service pour fusionner des données avec des modèles XDP et PDF ou générer une sortie aux formats PCL, ZPL et PostScript ?
description: Fusionner automatiquement les données avec des modèles XDP et PDF ou générer une sortie aux formats PCL, ZPL et PostScript
exl-id: 9fa9959e-b4f2-43ac-9015-07f57485699f
feature: Adaptive Forms,APIs & Integrations
role: Admin, Developer, User
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 86%

---


# Utilisation du traitement synchrone {#sync-processing-introduction}

Forms as a Cloud Service - Les API de communications vous permettent de créer, assembler et diffuser des communications personnalisées et orientées sur la marque, telles que des correspondances commerciales, des documents, des récapitulatifs, des lettres de traitement des demandes, des avis de prestations, des lettres de traitement des demandes, des factures mensuelles et des kits de bienvenue. Vous pouvez utiliser les API de communication pour combiner un modèle (XFA ou PDF) avec des données client afin de générer des documents aux formats PDF, PS, PCL, DPL, IPL et ZPL.

Supposons que vous ayez un ou plusieurs modèles et plusieurs enregistrements de données XML pour chaque modèle. Vous pouvez utiliser les API Communications pour générer un document d’impression pour chaque enregistrement. <!-- You can also combine the records into a single document. --> Le résultat est un document PDF non interactif. Dans ce type de document, les utilisateurs n’ont pas la possibilité de saisir des données dans les champs.

Forms as a Cloud Service - Communications fournit des API à la demande et par lots (API asynchrones) pour la génération de documents planifiés :

* Les API synchrones sont adaptées aux cas d’utilisation de génération de documents à la demande, à faible latence et pour un enregistrement unique. Ces API sont plus adaptées aux cas d’utilisation basés sur une action de l’utilisateur. Il peut s’agir, par exemple, de la génération d’un document après qu’un utilisateur a rempli un formulaire.

* Les API Batch (API asynchrones) conviennent pour la génération planifiée à débit élevé de documents multiples. Ces API génèrent des documents par lots. Il peut s’agir, par exemple, de factures de téléphone, de relevés de carte de crédit et de relevés de prestations générés tous les mois.

## Utilisation des opérations synchrones {#batch-operations}

Une opération synchrone est un processus de génération de documents de manière linéaire. Ces API sont classées comme API à client unique et API à plusieurs clients :

### API à client unique

* API de génération de documents
* API de manipulation de documents

<!-- 
### Multi-tenant APIs

* Document utility APIs -->


### Authentifier une API à client unique

Les opérations des API à client unique prennent en charge deux types d’authentification :

* **Authentification de base** : l’authentification de base est un schéma d’authentification simple intégré au protocole HTTP. Le client envoie des requêtes HTTP avec l’en-tête Autorisation qui contient le mot Base suivi d’un espace et d’une chaîne codée en base64 - nom d’utilisateur : mot de passe. Par exemple, pour autoriser en tant qu’administrateur / admin, le client envoie Base [chaîne codée en base64 - nom d’utilisateur] : [chaîne codée en base64 - mot de passe].

* **Authentification basée sur les jetons :** l’authentification basée sur les jetons utilise un jeton d’accès (jeton d’authentification du porteur) pour envoyer des requêtes à Experience Manager as a Cloud Service. AEM Forms as a Cloud Service fournit des API pour récupérer en toute sécurité le jeton d’accès. Pour récupérer et utiliser le jeton afin d’authentifier une requête :

   1. [Récupérer les informations d’identification Experience Manager as a Cloud Service à partir de Developer Console](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=fr).
   1. [Installer les informations d’identification Experience Manager as a Cloud Service dans votre environnement](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=fr). (Serveur d’applications, serveur web ou autres serveurs non AEM) configurés pour envoyer des requêtes au service cloud (passer des appels).
   1. [Générez un jeton JWT et échangez-le avec les API Adobe IMS pour un jeton d’accès](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=fr).
   1. Exécutez l’API Experience Manager avec le jeton d’accès servant de jeton d’authentification du porteur.
   1. [Définissez les autorisations appropriées pour l’utilisateur du compte technique dans l’environnement Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=fr#configurer-l’accès-dans-aem).

  >[!NOTE]
  >
  >Adobe recommande d’utiliser l’authentification basée sur les jetons sur un environnement de production.

<!-- 

### Authenticate a multi-tenant API

#### Authentication Headers

Every inbound HTTP API call to the multi-tenant API must contain these three headers:


* `x-api-key`
* `x-gw-ims-org-id`
* `Authorization`

The values which should be sent in the `x-api-key` and `x-gw-ims-org-id` headers are provided in the Credentials details screen in the [Adobe Developer Console](https://developer.adobe.com/console). The value of the `x-api-key` header is the Client ID and the value for the `x-gw-ims-org-id` header is the Organization ID.

#### Configure Adobe Developer console to generate an access token

To set up authentication APIs, create a project in Adobe Developer Console and add Communication APIs to the project on Adobe Developer Console. The integration generates API Key, Client Secret, Payload (JWT):

1. Contact you Adobe Developer Console administrator. Ask the administrator to add as a developer.
1. Log in to `https://developer.adobe.com/console/`. Use your developer account that your administrator has provisioned to log in to Adobe Developer Console.
1. Select your organization from the top-right corner. If you do not know your organization, contact your administrator.
1. Select **[!UICONTROL Create new project]**. A screen to get started with your new project appears. Select **[!UICONTROL Add API]**. A screen with list of all the APIs enabled for your account appears.
1. Select **[!UICONTROL AEM Forms - Communications]** and select **[!UICONTROL Next]**. A screen to configure the API appears.
1. Select **[!UICONTROL OPTION 1 Generate a key pair]** and select **[!UICONTROL Generate keypair]**. It creates and downloads the configuration file. The downloaded configuration file contains all your app settings, along with the only copy of your private key. Adobe does not record your private key, make sure to securely store the downloaded file. Select **[!UICONTROL Next]**.
1. Select **[!UICONTROL Integrations - Cloud Service]** and select **[!UICONTROL Save configured API]**. Select **[!UICONTROL Service Account (JWT)]** to view the API Key, Client Secret, and other information required to access the APIs. You set to use the token to access the APIs.

#### Programmatically generate and use an access token

To programmatically generate an access token, generate a JSON Web Token (JWT) and exchange it with the Adobe Identity Management Service (IMS) for an access token.

Use the following keys, referred to as claims, to construct JWT JSON object:


* `exp`- the requested expiration of the access token, expressed as several seconds since January 1, 1970 GMT. For most use cases, this is a relatively small value. For example, 5 minutes, for five minutes from now, this value should be 1670923791.
* `iss` - the Organization ID from the Adobe Developer Console project, in the format org_ident@AdobeOrg.
* `sub` - the Technical Account ID from the Adobe Developer Console integration, in the format: id@techacct.adobe.com.
* `aud` - the Client ID from the Adobe Developer Console integration prepended with `https://ims-na1.adobelogin.com/c/`.
* `https://ims-na1-stg1.adobelogin.com/s/ent_aemforms_docprocessing` - set to the literal value `true`

This JSON object must be then base64 encoded and signed using the private key for the project. Finally, the encoded value is sent in the body of a POST request to `https://ims-na1.adobelogin.com/ims/exchange/jwt` along with the Client ID and Client Secret for the project.

##### Example

```JSON

    ========================= REQUEST ==========================
    POST https://ims-na1.adobelogin.com/ims/exchange/jwt
    -------------------------- body ----------------------------
    client_id={myClientId}&client_secret={myClientSecret}&jwt_token={myJSONWebToken}
    ------------------------- headers --------------------------
    Content-Type: application/x-www-form-urlencoded
    Cache-Control: no-cache

```

#### Language Support for JWT

While it is possible to do the entire JWT generation and exchange process in custom code, it is more common to use a higher-level library to do so. A number of such libraries are listed on the [Adobe I/O JWT Documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/).

-->

### (Uniquement pour les API de génération de documents) Configuration des ressources et des autorisations

Pour utiliser les API synchrones, les éléments suivants sont requis :

* Utilisateurs ou utilisatrices disposant des privilèges d’administration Experience Manager
* Chargez les modèles et d’autres ressources vers votre instance Experience Manager Forms Cloud Service.

### (Uniquement pour les API de génération de documents) Chargez des modèles et d’autres ressources vers votre instance Experience Manager.

Une entreprise possède généralement différents modèles. Par exemple, un modèle pour les relevés de carte de crédit, les relevés de prestations et les réclamations. Chargez tous ces modèles XDP et PDF vers votre instance Experience Manager. Pour charger un modèle :

1. Ouvrez votre instance Experience Manager.
1. Accédez à Formulaires > Formulaires et documents
1. Cliquez sur Créer > Dossier et créez un dossier. Ouvrez le dossier.
1. Cliquez sur Créer > Téléchargement de fichier et chargez les modèles.

### Appel d’une API

La [documentation de référence sur les API](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/) fournit des informations détaillées sur tous les paramètres, les méthodes d’authentification et les différents services fournis par les API. La documentation de référence sur les API fournit également un fichier de définition de l’API au format .yaml. Vous pouvez télécharger le fichier .yaml et le télécharger dans [Postman](https://www.postman.com/) pour vérifier les fonctionnalités des API.

>[!VIDEO](https://video.tv.adobe.com/v/335771)

>[!NOTE]
>
>Seuls les membres du groupe des utilisateurs et utilisatrices de formulaires peuvent accéder aux API de communication.

>[!MORELIKETHIS]
>
>* [Présentation des communications as a Cloud Service AEM Forms](/help/forms/aem-forms-cloud-service-communications-introduction.md)
>* [&#x200B; Architecture as a Cloud Service AEM Forms pour les API de communication et de Forms adaptatifs](/help/forms/aem-forms-cloud-service-architecture.md)
>* [Traitement des communications - API synchrones](/help/forms/aem-forms-cloud-service-communications.md)
>* [Traitement des communications - API de lot](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)