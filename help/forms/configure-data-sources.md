---
title: Comment configurer des sources de données ?
description: L’intégration de données Experience Manager Forms permet de configurer des sources de données disparates et de s’y connecter. Découvrez comment configurer les services web RESTful, les services web SOAP et les services OData en tant que sources de données et comment les utiliser pour créer des modèles de données de formulaire.
feature: Form Data Model
role: User, Developer
level: Beginner
exl-id: cb77a840-d705-4406-a94d-c85a6efc8f5d
source-git-commit: 983f1b815fd213863ddbcd83ac7e3f076c57d761
workflow-type: tm+mt
source-wordcount: '1716'
ht-degree: 89%

---

# Configuration des sources de données {#configure-data-sources}

![Intégration de données](do-not-localize/data-integeration.png)

L’intégration de données [!DNL Experience Manager Forms] permet de configurer des sources de données disparates et de s’y connecter. La prise en charge est assurée par défaut pour les types suivants:

<!-- * Relational databases - MySQL, [!DNL Microsoft SQL Server], [!DNL IBM DB2], and [!DNL Oracle RDBMS] 
* [!DNL Experience Manager] user profile  -->
* Services web RESTful
* Services web SOAP
* Services OData (Version 4.0)
* Microsoft Dynamics 
* SalesForce
* Stockage Microsoft Azure Blob

L’intégration de données prend en charge l’authentification OAuth2.0, de base ou par clé API par défaut, et permet de mettre en œuvre une authentification personnalisée pour accéder aux services web. Les services RESTful, SOAP et OData sont configurés dans [!DNL Experience Manager] as a Cloud Service <!--, JDBC for relational databases --> et le connecteur pour le profil utilisateur [!DNL Experience Manager] est configuré dans la console web [!DNL Experience Manager].

>[!NOTE]
>
>[!UICONTROL Experience Manager Forms] ne prend pas en charge les bases de données relationnelles.

<!-- ## Configure relational database {#configure-relational-database}

You can configure relational databases using [!DNL Experience Manager] Web Console Configuration. Do the following:

1. Go to [!DNL Experience Manager] web console at `https://server:host/system/console/configMgr`.
1. Look for **[!UICONTROL Apache Sling Connection Pooled DataSource]** configuration. Tap to open the configuration in edit mode.
1. In the configuration dialog, specify the details for the database you want to configure, such as:

    * Name of the data source
    * Data source service property that stores the data source name
    * Java class name for the JDBC driver
    * JDBC connection URI
    * Username and password to establish connection with the JDBC driver

   >[!NOTE]
   >
   >Ensure that you encrypt sensitive information like passwords before configuring the data source. To encrypt:
   >
   >    
   >    
   >    1. Go to https://'[server]:[port]'/system/console/crypto.
   >    1. In the **[!UICONTROL Plain Text]** field, specify the password or any string to encrypt and tap **[!UICONTROL Protect]**.
   >    
   >    
   >    
   >The encrypted text appears in the Protected Text field that you can specify in the configuration.

1. Enable **[!UICONTROL Test on Borrow]** or **[!UICONTROL Test on Return]** to specify that the objects are validated before being borrowed or returned from and to the pool, respectively.
1. Specify a SQL SELECT query in the **[!UICONTROL Validation Query]** field to validate connections from the pool. The query must return at least one row. Based on your database, specify one of the following:

    * SELECT 1 (MySQL and MS SQL) 
    * SELECT 1 from dual (Oracle)

1. Tap **[!UICONTROL Save]** to save the configuration. -->

<!-- ## Configure [!DNL Experience Manager] user profile {#configure-aem-user-profile}

You can configure [!DNL Experience Manager] user profile using User Profile Connector configuration in [!DNL Experience Manager] Web Console. Do the following:

1. Go to [!DNL Experience Manager] web console at `https://[server]:[port]/system/console/configMgr`.
1. Look for **[!UICONTROL AEM Forms Data Integrations - User Profile Connector Configuration]** and tap to open the configuration in edit mode.
1. In the User Profile Connector Configuration dialog, you can add, remove, or update user profile properties. The specified properties will be available for use in form data model. Use the following format to specify user profile properties:

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   Examples:

    * `name=profile/phoneNumber,type=string`
    * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >The **&#42;** in the above example denotes all nodes under the `profile/empLocation/` node in [!DNL Experience Manager] user profile in CRXDE structure. It means that the Form Data Model can access the `city` property of type `string` present in any node under the `profile/empLocation/` node. However, the nodes that contain the specified property must follow a consistent structure.

1. Tap **[!UICONTROL Save]** to save the configuration. -->

## Configurer le dossier pour les configurations de service cloud {#cloud-folder}

La configuration du dossier de services cloud est requise pour la configuration des services cloud pour les services RESTful, SOAP et OData.

Toutes les configurations de services cloud dans [!DNL Experience Manager] sont consolidées dans le dossier `/conf` du référentiel [!DNL Experience Manager]. Par défaut, le dossier `conf` contient le dossier `global` dans lequel vous pouvez créer des configurations de service cloud. Toutefois, vous devez l’activer manuellement pour les configurations cloud. Vous pouvez également créer des dossiers supplémentaires dans `conf` pour créer et organiser des configurations de service cloud.

Pour configurer le dossier pour les configurations de service cloud :

1. Accédez à **[!UICONTROL Outils > Général > Navigateur de configuration]**.
   * Pour plus d’informations, consultez la documentation relative au [Navigateur de configuration](https://experienceleague.adobe.com/docs/experience-manager-65/administering/introduction/configurations.html?lang=fr).
1. Procédez comme suit pour activer le dossier global pour les configurations cloud ou ignorez cette étape pour créer et configurer un autre dossier pour les configurations de service cloud.

   1. Dans le **[!UICONTROL navigateur de configuration]**, sélectionnez le dossier `global` et appuyez sur **[!UICONTROL Propriétés]**.

   1. Dans la boîte de dialogue **[!UICONTROL Propriétés de configuration]**, activez **[!UICONTROL Configurations cloud]**.

   1. Appuyez sur **[!UICONTROL Enregistrer et fermer]** pour enregistrer la configuration et fermer la boîte de dialogue.

1. Dans le **[!UICONTROL navigateur de configuration]**, appuyez sur **[!UICONTROL Créer]**.
1. Dans la boîte de dialogue **[!UICONTROL Créer une configuration]**, indiquez un titre pour le dossier et activez **[!UICONTROL Configurations cloud]**.
1. Appuyez sur **[!UICONTROL Créer]** pour créer le dossier activé pour les configurations de service cloud.

## Configuration des services web RESTful {#configure-restful-web-services}

Le service web RESTful peut être décrit en utilisant les [spécifications Swagger](https://swagger.io/specification/v2/) au format JSON ou YAML dans un fichier de définition [!DNL Swagger]. Pour configurer le service Web RESTful dans [!DNL Experience Manager] as a Cloud Service, assurez-vous que la variable [!DNL Swagger] fichier ([Swagger version 2.0](https://swagger.io/specification/v2/)) sur votre système de fichiers ou l’URL d’hébergement du fichier.

Procédez comme suit pour configurer les services RESTful :

1. Accédez à **[!UICONTROL Outils > Cloud Services > Sources de données]**. Appuyez pour sélectionner le dossier dans lequel vous souhaitez créer une configuration cloud.

   Pour plus d’informations sur la création et la configuration d’un dossier pour les configurations de service cloud, voir [Configurer le dossier pour les configurations de service cloud](configure-data-sources.md#cloud-folder).

1. Appuyez sur **[!UICONTROL Créer]** pour ouvrir l’**[!UICONTROL assistant Créer une configuration de source de données]**. Indiquez un nom et éventuellement un titre pour la configuration, sélectionnez **[!UICONTROL Service RESTful]** dans la liste déroulante **[!UICONTROL Type de service]**, recherchez et sélectionnez éventuellement une image miniature pour la configuration, puis appuyez sur **[!UICONTROL Suivant]**.
1. Spécifiez les informations suivantes pour le service RESTful :

   * Sélectionnez l’URL ou le fichier dans la liste déroulante [!UICONTROL Source Swagger] et spécifiez l’[!DNL Swagger URL] vers le fichier de définition du [!DNL  Swagger] ou chargez le fichier [!DNL Swagger] à partir de votre système de fichiers local.
   * En fonction de l’entrée de la source[!DNL  Swagger], les champs suivants sont prérenseignés avec des valeurs :

      * Schéma : protocoles de transfert utilisés par l’API REST. Le nombre de types de schémas qui s’affichent dans la liste déroulante dépend des schémas définis dans la source [!DNL Swagger].
      * Hôte : nom de domaine ou adresse IP de l’hôte qui sert l’API REST. Ce champ est obligatoire.
      * Chemin d’accès de base : le préfixe d’URL de tous les chemins d’API. Ce champ est facultatif.\
         Si nécessaire, modifiez les valeurs prérenseignées pour ces champs.
   * Sélectionnez le type d’authentification (Aucun, OAuth2.0, Authentification de base, Clé API ou Authentification personnalisée) pour accéder au service RESTful et spécifiez les détails de l’authentification.

   Si vous sélectionnez **[!UICONTROL Clé API]** comme type d’authentification, spécifiez la valeur de la clé API. La clé API peut être envoyée en tant qu’en-tête de requête ou en tant que paramètre de requête. Sélectionnez l’une de ces options dans la liste déroulante **[!UICONTROL Emplacement]** et indiquez le nom de l’en-tête ou du paramètre de requête dans le champ **[!UICONTROL Nom du paramètre]**.

   <!--If you select **[!UICONTROL Mutual Authentication]** as the authentication type, see [Certificate-based mutual authentication for RESTful and SOAP web services](#mutual-authentication).-->

1. Appuyez sur **[!UICONTROL Créer]** pour créer la configuration cloud pour le service RESTful.

### Configurer le client HTTP du modèle de données de formulaire pour optimiser les performances {#fdm-http-client-configuration}

Le modèle de données de formulaire d’[!DNL Experience Manager Forms] lors de l’intégration des services web RESTful comme source de données comprend des configurations de client HTTP pour l’optimisation des performances.


Définissez les propriétés suivantes de la variable **[!UICONTROL Configuration du client HTTP du modèle de données de formulaire pour la source de données REST]** configuration pour spécifier l’expression régulière :

* Utilisez la variable `http.connection.max.per.route` pour définir le nombre maximal de connexions autorisées entre le modèle de données de formulaire et les services Web RESTful. La valeur par défaut est de 20 connexions.

* Utilisez la variable `http.connection.max` pour spécifier le nombre maximal de connexions autorisées pour chaque itinéraire. La valeur par défaut est de 40 connexions.

* Utilisez la variable `http.connection.keep.alive.duration` pour spécifier la durée pour laquelle une connexion HTTP persistante est maintenue active. La valeur par défaut est de 15 secondes.

* Utilisez la variable `http.connection.timeout` pour spécifier la durée pour laquelle la propriété [!DNL Experience Manager Forms] attend qu’une connexion soit établie. La valeur par défaut est de 10 secondes.

* Utilisez la variable `http.socket.timeout` pour spécifier la période maximale d’inactivité entre deux paquets de données. La valeur par défaut est de 30 secondes.

Le fichier JSON suivant affiche un exemple :

```json
{   
   "http.connection.keep.alive.duration":"15",   
   "http.connection.max.per.route":"20",   
   "http.connection.timeout":"10",   
   "http.socket.timeout":"30",   
   "http.connection.idle.connection.timeout":"15",   
   "http.connection.max":"40" 
} 
```

Pour définir les valeurs d’une configuration, [générez des configurations OSGi à l’aide du SDK AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=fr#generating-osgi-configurations-using-the-aem-sdk-quickstart) et [déployez la configuration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=fr#deployment-process) sur votre instance de Cloud Service.


Effectuez les étapes suivantes pour configurer le client HTTP du modèle de données de formulaire :

1. Connectez-vous à l’instance d’auteur [!DNL Experience Manager Forms] en tant qu’administrateur et accédez aux lots de la console web d’[!DNL Experience Manager]. L’URL par défaut est [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).

1. Appuyer **[!UICONTROL Configuration du client HTTP du modèle de données de formulaire pour la source de données REST]**.

1. Dans le [!UICONTROL Configuration du client HTTP du modèle de données de formulaire pour la source de données REST] dialog :

   * Spécifiez le nombre maximal de connexions autorisées entre le modèle de données de formulaire et les services Web RESTful dans le champ **[!UICONTROL Limite de connexion au total]**. La valeur par défaut est de 20 connexions.

   * Spécifiez le nombre maximal de connexions autorisées pour chaque itinéraire dans le champ **[!UICONTROL Limite de connexion par itinéraire]**. La valeur par défaut est de 2 connexions.

   * Indiquez la durée pendant laquelle une connexion HTTP persistante est maintenue en vie, dans le champ **[!UICONTROL Maintenir en vie]**. La valeur par défaut est de 15 secondes.

   * Indiquez la durée pendant laquelle le serveur [!DNL Experience Manager Forms] attend qu’une connexion soit établie, dans le champ **[!UICONTROL Délai d’attente de connexion]**. La valeur par défaut est de 10 secondes.

   * Spécifiez la période maximale d’inactivité entre deux paquets de données dans le champ **[!UICONTROL Délai d’attente du socket]**. La valeur par défaut est de 30 secondes.

## Configuration des services web SOAP {#configure-soap-web-services}

Les services web SOAP sont décrits à l’aide des [spécifications WSDL (Web Services Description Language)](https://www.w3.org/TR/wsdl). [!DNL Experience Manager Forms] ne prend pas en charge le modèle WSDL de style RPC.

Pour configurer le service Web SOAP dans [!DNL Experience Manager] as a Cloud Service, vérifiez que vous disposez de l’URL WSDL pour le service web et procédez comme suit :

1. Accédez à **[!UICONTROL Outils > Cloud Services > Sources de données]**. Appuyez pour sélectionner le dossier dans lequel vous souhaitez créer une configuration cloud.

   Pour plus d’informations sur la création et la configuration d’un dossier pour les configurations de service cloud, voir [Configurer le dossier pour les configurations de service cloud](configure-data-sources.md#cloud-folder).

1. Appuyez sur **[!UICONTROL Créer]** pour ouvrir l’**[!UICONTROL assistant Créer une configuration de source de données]**. Indiquez un nom et éventuellement un titre pour la configuration, sélectionnez **[!UICONTROL Service Web SOAP]** dans la liste déroulante **[!UICONTROL Type de service]**, sélectionnez et sélectionnez une image miniature pour la configuration, puis appuyez sur **[!UICONTROL Suivant]**.
1. Spécifiez les éléments suivants pour le service Web SOAP :

   * URL WSDL pour le service Web.
   * Point d’entrée du service. Spécifiez une valeur dans ce champ pour remplacer le point d’entrée du service mentionné dans WSDL.
   * Sélectionnez le type d’authentification - Aucun, OAuth2.0, Authentification de base ou Authentification personnalisée - pour accéder au service SOAP et fournir en conséquence les détails de l’authentification.

      <!--If you select **[!UICONTROL X509 Token]** as the Authentication type, configure the X509 certificate. For more information, see [Set up certificates](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service).-->
      <!--Specify the KeyStore alias for the X509 certificate in the **[!UICONTROL Key Alias]** field. Specify the time, in seconds, until the authentication request remains valid, in the **[!UICONTROL Time To Live]** field. Optionally, select to sign the message body or timestamp header or both.-->

      <!--If you select **[!UICONTROL Mutual Authentication]** as the authentication type, see [Certificate-based mutual authentication for RESTful and SOAP web services](#mutual-authentication).-->

1. Appuyez sur **[!UICONTROL Créer]** pour créer la configuration cloud pour le service web SOAP.

### Activez l’utilisation des instructions d’importation dans le WSDL des services web SOAP {#enable-import-statements}

Vous pouvez spécifier une expression régulière qui sert de filtre pour les URL absolues autorisées comme instructions d’importation dans le WSDL des services web SOAP. Par défaut, ce champ ne contient aucune valeur. Par conséquent, [!DNL Experience Manager] bloque toutes les instructions d’importation disponibles dans le WSDL. Si vous spécifiez `.*` comme valeur dans ce champ, [!DNL Experience Manager] autorise toutes les instructions d’importation.

Définissez la propriété `importAllowlistPattern` de la configuration de la **[!UICONTROL Liste autorisée d’importation des services Web SOAP du Modèle de données de formulaire]** pour spécifier l’expression régulière. Le fichier JSON suivant affiche un exemple :

```json
{
  "importAllowlistPattern": ".*"
}
```

Pour définir les valeurs d’une configuration, [générez des configurations OSGi à l’aide du SDK AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart) et [déployez la configuration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) sur votre instance de Cloud Service.

## Configuration des services OData {#config-odata}

Un service OData est identifié par son URL racine de service. Pour configurer un service OData dans [!DNL Experience Manager] as a Cloud Service, vérifiez que vous disposez de l’URL racine du service et procédez comme suit :

>[!NOTE]
>
> Le modèle de données de formulaire prend en charge [OData version 4](https://www.odata.org/documentation/).
>Pour obtenir un guide pas à pas sur la configuration de [!DNL Microsoft Dynamics 365], en ligne ou sur site, voir [[!DNL Microsoft Dynamics] Configuration OData](ms-dynamics-odata-configuration.md).

1. Accédez à **[!UICONTROL Outils > Cloud Services > Sources de données]**. Appuyez pour sélectionner le dossier dans lequel vous souhaitez créer une configuration cloud.

   Pour plus d’informations sur la création et la configuration d’un dossier pour les configurations de service cloud, voir [Configurer le dossier pour les configurations de service cloud](#cloud-folder).

1. Appuyez sur **[!UICONTROL Créer]** pour ouvrir l’**[!UICONTROL assistant Créer une configuration de source de données]**. Indiquez un nom et éventuellement un titre pour la configuration, sélectionnez **[!UICONTROL Service OData]** dans la liste déroulante **[!UICONTROL Type de service]**, cherchez et sélectionnez éventuellement une vignette pour la configuration, puis appuyez sur **[!UICONTROL Suivant]**.
1. Spécifiez les informations suivantes pour le service OData :

   * URL racine du service pour le service OData à configurer.
   * Sélectionnez le type d’authentification - Aucun, OAuth2.0, Authentification de base, Clé API ou Authentification personnalisée - pour accéder au service OData et fournir en conséquence les détails de l’authentification.

   Si vous sélectionnez **[!UICONTROL Clé API]** comme type d’authentification, spécifiez la valeur de la clé API. La clé API peut être envoyée en tant qu’en-tête de requête ou en tant que paramètre de requête. Sélectionnez l’une de ces options dans la liste déroulante **[!UICONTROL Emplacement]** et indiquez le nom de l’en-tête ou du paramètre de requête dans le champ **[!UICONTROL Nom du paramètre]**.

   >[!NOTE]
   >
   >Vous devez sélectionner le type d’authentification OAuth 2.0 pour vous connecter aux services [!DNL Microsoft Dynamics] à l’aide du point d’entrée OData en tant que racine du service.

1. Appuyez sur **[!UICONTROL Créer]** pour créer la configuration de cloud pour le service OData.

<!--## Certificate-based mutual authentication for RESTful and SOAP web services {#mutual-authentication}

When you enable mutual authentication for form data model, both the data source and [!DNL Experience Manager] Server running Form Data Model authenticate each other’s identity before sharing any data. You can use mutual authentication for REST and SOAP-based connections (data sources). To configure mutual authentication for a Form Data Model on your [!DNL Experience Manager Forms] environment:

1. Upload the private key (certificate) to [!DNL Experience Manager Forms] server. To upload the private key:
   1. Log in to your [!DNL Experience Manager Forms] server as an administrator.
   1. Navigate to **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**. Select the `fd-cloudservice` user and tap **[!UICONTROL Properties]**.
   1. Open the **[!UICONTROL Keystore]** tab, expand the **[!UICONTROL Add Private Key from KeyStore file]** option, upload the KeyStore File, specify the aliases, passwords, and tap **[!UICONTROL Submit]**. The Certificate is uploaded.  The private key alias is mentioned in the certificate and set while creating the certificate.
1. Upload trust certificate to Global Trust Store. To upload the certificate:
   1. Navigate to **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Trust Store]**.
   1. Expand the **[!UICONTROL Add Certificate from CER file]** option, tap **[!UICONTROL Select Certificate File]**, upload the certificate, and tap **[!UICONTROL Submit]**.
1. Configure [SOAP](#configure-soap-web-services) or [RESTful](#configure-restful-web-services) web services as the data source and select **[!UICONTROL Mutual authentication]** as the authentication type. If you configure multiple self-signed certificates for `fd-cloudservice` user, specify the Key Alias name for the certificate.-->

## Étapes suivantes {#next-steps}

Vous avez configuré la source de données. Vous pouvez ensuite créer un modèle de données de formulaire ou, si vous en avez déjà créé un sans source de données, vous pouvez l’associer aux sources de données que vous venez de configurer. Voir [Création d’un modèle de données de formulaire](create-form-data-models.md) pour plus de détails.
