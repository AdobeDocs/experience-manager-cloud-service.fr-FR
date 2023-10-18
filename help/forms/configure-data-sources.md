---
title: Comment configurer des sources de données ?
description: Découvrez comment configurer les services Web RESTful, les services Web SOAP et les services OData comme sources de données pour un modèle de données de formulaire.
feature: Form Data Model
role: User, Developer
level: Beginner
exl-id: cb77a840-d705-4406-a94d-c85a6efc8f5d
source-git-commit: ac7e1a1ada156734c3a487269e674e8eade7c9c3
workflow-type: tm+mt
source-wordcount: '2452'
ht-degree: 87%

---


# Configuration des sources de données {#configure-data-sources}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/configure-data-sources.html) |
| AEM as a Cloud Service | Cet article |

![Intégration de données](do-not-localize/data-integeration.png)

[!DNL Experience Manager Forms] Data Integration vous permet de configurer des sources de données disparates et de vous y connecter. La prise en charge est assurée par défaut pour les types suivants :

* Bases de données relationnelles - MySQL, [!DNL Microsoft® SQL Server], [!DNL IBM® DB2®], et [!DNL Oracle RDBMS].
* Services web RESTful
* Services web SOAP
* Services OData  (Version 4.0)
* Microsoft® Dynamics 
* SalesForce
* Stockage d’objets blob Microsoft® Azure.

L’intégration de données prend en charge l’authentification OAuth2.0, ([Code d’autorisation](https://oauth.net/2/grant-types/authorization-code/), [Informations d’identification client](https://oauth.net/2/grant-types/client-credentials/)), l’authentification de base ou l’authentification par clé API (prêtes à l’emploi). Elle permet de mettre en œuvre une authentification personnalisée pour accéder aux services web. Alors que les services RESTful, SOAP et OData sont configurés dans [!DNL Experience Manager] as a Cloud Service, JDBC pour les bases de données relationnelles et le connecteur pour le profil utilisateur [!DNL Experience Manager] sont configurés dans la console web [!DNL Experience Manager].

## Configurer la base de données relationnelle {#configure-relational-database}

### Prérequis

Avant de configurer des bases de données relationnelles à l’aide de la Configuration de la console web [!DNL Experience Manager], il est obligatoire d’effectuer les actions suivantes :
* [Activation de la mise en réseau avancée via l’API de gestion du cloud](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/advanced-networking.html), car les ports sont désactivés par défaut.
* [Ajouter des dépendances de pilote JDBC dans Maven](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/examples/sql-datasourcepool.html?lang=fr#mysql-driver-dependencies).


### Etapes de configuration d&#39;une base de données relationnelle

Vous pouvez configurer des bases de données relationnelles à l’aide de la configuration de la console Web [!DNL Experience Manager]. Procédez comme suit :

1. Accédez à la console web [!DNL Experience Manager] à l’adresse `https://server:host/system/console/configMgr`.
1. Localisez la configuration des **[!UICONTROL Pools de connexions JDBC Day Commons]**. Appuyez pour ouvrir la configuration en mode édition.

   ![Pool de connecteurs JDBC](/help/forms/assets/jdbc_connector.png).

1. Dans la boîte de dialogue de configuration, spécifiez les détails de la base de données que vous souhaitez configurer, tels que :

   * Nom de classe Java™ pour le pilote JDBC.
   * URI de connexion JDBC
   * Nom d’utilisateur et mot de passe pour établir la connexion au pilote JDBC
   * Spécifiez une requête SQL SELECT dans le champ **[!UICONTROL Requête de validation]** pour valider les connexions du pool. La requête doit renvoyer au moins une ligne. En fonction de votre base de données, définissez l’une des options suivantes :
      * SELECT 1 (MySQL et MS® SQL)
      * SELECT 1 from dual (Oracle)
   * Nom de la source de données

   Exemples de chaînes pour configurer une base de données relationnelle :

   ```text
      "datasource.name": "sqldatasourcename-mysql",
      "jdbc.driver.class": "com.mysql.jdbc.Driver",
      "jdbc.connection.uri": "jdbc:mysql://$[env:AEM_PROXY_HOST;default=proxy.tunnel]:30001/sqldatasourcename"
   ```

   >[!NOTE]
   >
   > Consultez [Connexions SQL à l’aide de JDBC DataSourcePool](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/examples/sql-datasourcepool.html) pour plus d’informations.

1. Appuyez sur **[!UICONTROL Enregistrer]** pour enregistrer la configuration.

Vous pouvez désormais utiliser la base de données relationnelle configurée avec votre modèle de données de formulaire.

<!-- ## Configure [!DNL Experience Manager] user profile {#configure-aem-user-profile}

You can configure [!DNL Experience Manager] user profile using User Profile Connector configuration in [!DNL Experience Manager] Web Console. Do the following:

1. Go to [!DNL Experience Manager] web console at `https://[server]:[port]/system/console/configMgr`.
1. Look for **[!UICONTROL AEM Forms Data Integrations - User Profile Connector Configuration]** and tap to open the configuration in edit mode.
1. In the User Profile Connector Configuration dialog, you can add, remove, or update user profile properties. The specified properties are available for use in form data model. Use the following format to specify user profile properties:

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
1. Dans la boîte de dialogue **[!UICONTROL Créer une configuration]**, indiquez un titre pour le dossier et activez les **[!UICONTROL Configurations cloud]**.
1. Appuyez sur **[!UICONTROL Créer]** pour créer le dossier activé pour les configurations de service cloud.

## Configuration des services web RESTful {#configure-restful-web-services}

Les services web RESTful peuvent être décrits à l’aide de [Spécifications Swagger](https://swagger.io/specification/v2/) au format JSON ou YAML dans un objet [!DNL Swagger] fichier de définition. Pour configurer le service web RESTful dans [!DNL Experience Manager] as a Cloud Service, vérifiez que le fichier [!DNL Swagger] ([Swagger Version 2.0](https://swagger.io/specification/v2/)) ou le fichier [!DNL Swagger] ([Swagger Version 3.0](https://swagger.io/specification/v3/)) est présent dans votre système de fichiers ou l’URL où le fichier est hébergé.

### Configurez les services RESTful pour la version 2.0 de la spécification Open API {#configure-restful-services-open-api-2.0}.

1. Accédez à **[!UICONTROL Outils > Cloud Services > Sources de données]**. Appuyez pour sélectionner le dossier dans lequel vous souhaitez créer une configuration cloud.

   Pour plus d’informations sur la création et la configuration d’un dossier pour les configurations de service cloud, voir [Configurer le dossier pour les configurations de service cloud](configure-data-sources.md#cloud-folder).

1. Appuyez sur **[!UICONTROL Créer]** pour ouvrir l’**[!UICONTROL assistant Créer une configuration de source de données]**. Indiquez un nom et éventuellement un titre pour la configuration, sélectionnez **[!UICONTROL Service RESTful]** dans la liste déroulante **[!UICONTROL Type de service]**, cherchez et sélectionnez éventuellement une image miniature pour la configuration, puis appuyez sur **[!UICONTROL Suivant]**.
1. Spécifiez les informations suivantes pour le service RESTful :

   * Sélectionnez une URL ou un fichier dans le [!UICONTROL Source Swagger] et, en conséquence, spécifiez la variable [!DNL Swagger URL] à la fonction[!DNL  Swagger] fichier de définition ou téléchargez le fichier [!DNL Swagger] à partir de votre système de fichiers local.
   * En fonction de l’entrée source [!DNL  Swagger], les champs suivants sont préremplis avec des valeurs :

      * Schéma : protocoles de transfert utilisés par l’API REST. Le nombre de types de schémas qui s’affichent dans la liste déroulante dépend des schémas définis dans la source [!DNL Swagger].
      * Hôte : nom de domaine ou adresse IP de l’hôte qui sert l’API REST. Ce champ est obligatoire.
      * Chemin d’accès de base : le préfixe d’URL de tous les chemins d’API. Ce champ est facultatif.\
        Si nécessaire, modifiez les valeurs prérenseignées pour ces champs.

   * Sélectionnez le type d’authentification : aucune, OAuth2.0 ([code d’authentification](https://oauth.net/2/grant-types/authorization-code/), [informations d’identification client](https://oauth.net/2/grant-types/client-credentials/)), authentification de base, clé API ou authentification personnalisée pour accéder au service RESTful et spécifiez les détails de l’authentification.

   Si vous sélectionnez **[!UICONTROL Clé API]** comme type d’authentification, spécifiez la valeur de la clé API. La clé API peut être envoyée en tant qu’en-tête de requête ou en tant que paramètre de requête. Sélectionnez l’une de ces options dans la liste déroulante **[!UICONTROL Emplacement]** et indiquez le nom de l’en-tête ou du paramètre de requête dans le champ **[!UICONTROL Nom du paramètre]**.

   <!--If you select **[!UICONTROL Mutual Authentication]** as the authentication type, see [Certificate-based mutual authentication for RESTful and SOAP web services](#mutual-authentication).-->

1. Appuyez sur **[!UICONTROL Créer]** pour créer la configuration cloud pour le service RESTful.

### Configurez les services RESTful pour la version 3.0 de la spécification Open API {#configure-restful-services-open-api-3.0}.

1. Accédez à **[!UICONTROL Outils > Cloud Services > Sources de données]**. Appuyez pour sélectionner le dossier dans lequel vous souhaitez créer une configuration cloud.

   Pour plus d’informations sur la création et la configuration d’un dossier pour les configurations de service cloud, voir [Configurer le dossier pour les configurations de service cloud](configure-data-sources.md#cloud-folder).

1. Appuyez sur **[!UICONTROL Créer]** pour ouvrir l’**[!UICONTROL assistant Créer une configuration de source de données]**. Indiquez un nom et éventuellement un titre pour la configuration, sélectionnez **[!UICONTROL Service RESTful]** dans la liste déroulante **[!UICONTROL Type de service]**, cherchez et sélectionnez éventuellement une image miniature pour la configuration, puis appuyez sur **[!UICONTROL Suivant]**.
1. Spécifiez les informations suivantes pour le service RESTful :

   * Sélectionnez une URL ou un fichier dans le [!UICONTROL Source Swagger] et, en conséquence, spécifiez la variable [!DNL Swagger 3.0 URL] à la fonction[!DNL  Swagger] fichier de définition ou téléchargez le fichier [!DNL Swagger] à partir de votre système de fichiers local.
   * En fonction de l’entrée source [!DNL  Swagger], les informations de connexion au serveur cible s’affichent.
   * Sélectionnez le type d’authentification : aucune, OAuth2.0 ([code d’authentification](https://oauth.net/2/grant-types/authorization-code/), [informations d’identification client](https://oauth.net/2/grant-types/client-credentials/)), authentification de base, clé API ou authentification personnalisée pour accéder au service RESTful et spécifiez les détails de l’authentification.

   Si vous sélectionnez **[!UICONTROL Clé API]** comme type d’authentification, spécifiez la valeur de la clé API. La clé API peut être envoyée en tant qu’en-tête de requête ou en tant que paramètre de requête. Sélectionnez l’une de ces options dans la liste déroulante **[!UICONTROL Emplacement]** et indiquez le nom de l’en-tête ou du paramètre de requête dans le champ **[!UICONTROL Nom du paramètre]**.

   <!--If you select **[!UICONTROL Mutual Authentication]** as the authentication type, see [Certificate-based mutual authentication for RESTful and SOAP web services](#mutual-authentication).-->

1. Appuyez sur **[!UICONTROL Créer]** pour créer la configuration cloud pour le service RESTful.

Voici quelques-unes des opérations non prises en charge par la version 3.0 de la spécification Open API des services RESTful :
* Les rappels.
* l’un de/l’un des.
* Référence à distance.
* Liens
* Différents corps de requête pour différents types MIME pour une seule opération.

Consultez [Spécification OpenAPI 3.0](https://swagger.io/specification/v3/) pour plus d’informations.

### Configuration du client HTTP du modèle de données de formulaire pour optimiser les performances {#fdm-http-client-configuration}

[!DNL Experience Manager Forms] formez un modèle de données lors de l’intégration aux services web RESTful en tant que source de données ; il comprend des configurations de client HTTP pour l’optimisation des performances.

Définissez les propriétés suivantes de la **[!UICONTROL Configuration du client HTTP du modèle de données de formulaire pour la source de données REST]** pour spécifier l’expression régulière :

* Utilisez la propriété `http.connection.max.per.route` pour définir le nombre maximal de connexions autorisées entre le modèle de données de formulaire et les services Web RESTful. La valeur par défaut est de 20 connexions.

* Utilisez la propriété `http.connection.max` pour spécifier le nombre maximal de connexions autorisées pour chaque itinéraire. La valeur par défaut est de 40 connexions.

* Utilisez la propriété `http.connection.keep.alive.duration` pour spécifier la durée pour laquelle une connexion HTTP persistante est maintenue active. La valeur par défaut est de 15 secondes.

* Utilisez la propriété `http.connection.timeout` pour spécifier la durée pendant laquelle la propriété [!DNL Experience Manager Forms] attend qu’une connexion soit établie. La valeur par défaut est de 10 secondes.

* Utilisez la propriété `http.socket.timeout` pour spécifier la période maximale d’inactivité entre deux paquets de données. La valeur par défaut est de 30 secondes.

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

1. Appuyez sur **[!UICONTROL Configuration du client HTTP du modèle de données de formulaire pour la source de données REST]**.

1. Dans la boîte de dialogue [!UICONTROL Configuration du client HTTP du modèle de données de formulaire pour la source de données REST] :

   * Spécifiez le nombre maximal de connexions autorisées entre le modèle de données de formulaire et les services Web RESTful dans le champ **[!UICONTROL Limite de connexion au total]**. La valeur par défaut est de 20 connexions.

   * Spécifiez le nombre maximal de connexions autorisées pour chaque itinéraire dans le champ **[!UICONTROL Limite de connexion par itinéraire]**. La valeur par défaut est « deux connexions ».

   * Indiquez la durée pendant laquelle une connexion HTTP persistante est maintenue en vie, dans le champ **[!UICONTROL Maintenir en vie]**. La valeur par défaut est de 15 secondes.

   * Indiquez la durée pendant laquelle le serveur [!DNL Experience Manager Forms] attend qu’une connexion soit établie, dans le champ **[!UICONTROL Délai d’attente de connexion]**. La valeur par défaut est de 10 secondes.

   * Spécifiez la période maximale d’inactivité entre deux paquets de données dans le champ **[!UICONTROL Délai d’attente du socket]**. La valeur par défaut est de 30 secondes.

## Configuration des services web SOAP {#configure-soap-web-services}

Les services web SOAP sont décrits à l’aide des [spécifications WSDL (Web Services Description Language)](https://www.w3.org/TR/wsdl). [!DNL Experience Manager Forms] ne prennent pas en charge le modèle WSDL de style RPC.

Pour configurer le service Web SOAP dans [!DNL Experience Manager] as a Cloud Service, vérifiez que vous disposez de l’URL WSDL pour le service web et procédez comme suit :

1. Accédez à **[!UICONTROL Outils > Cloud Services > Sources de données]**. Appuyez pour sélectionner le dossier dans lequel vous souhaitez créer une configuration cloud.

   Pour plus d’informations sur la création et la configuration d’un dossier pour les configurations de service cloud, voir [Configurer le dossier pour les configurations de service cloud](configure-data-sources.md#cloud-folder).

1. Appuyez sur **[!UICONTROL Créer]** pour ouvrir l’**[!UICONTROL assistant Créer une configuration de source de données]**. Indiquez un nom et éventuellement un titre pour la configuration, sélectionnez **[!UICONTROL Service Web SOAP]** dans la liste déroulante **[!UICONTROL Type de service]**, recherchez et sélectionnez une image miniature pour la configuration, puis appuyez sur **[!UICONTROL Suivant]**.
1. Spécifiez les éléments suivants pour le service web SOAP :

   * URL WSDL du service web.
   * Point d’entrée du service. Spécifiez une valeur dans ce champ pour remplacer le point d’entrée du service mentionné dans WSDL.
   * Sélectionnez le type d’authentification : aucune, OAuth2.0 ([code d’autorisation](https://oauth.net/2/grant-types/authorization-code/), [informations d’identification client](https://oauth.net/2/grant-types/client-credentials/)), authentification de base ou authentification personnalisée pour accéder au service SOAP et fournissez en conséquence les détails de l’authentification.

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


Pour définir les valeurs d’une configuration, [générez des configurations OSGi à l’aide du SDK AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=fr#generating-osgi-configurations-using-the-aem-sdk-quickstart) et [déployez la configuration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=fr#deployment-process) sur votre instance de Cloud Service.

## Configuration des services OData {#config-odata}

Un service OData est identifié par son URL racine de service. Pour configurer un service OData dans [!DNL Experience Manager] as a Cloud Service, vérifiez que vous disposez de l’URL racine du service et procédez comme suit :

>[!NOTE]
>
> Le modèle de données de formulaire prend en charge [OData version 4](https://www.odata.org/documentation/).
>Pour un guide détaillé de configuration [!DNL Microsoft®® Dynamics 365], en ligne ou sur site, voir [[!DNL Microsoft® Dynamics] Configuration OData](ms-dynamics-odata-configuration.md).

1. Accédez à **[!UICONTROL Outils > Cloud Services > Sources de données]**. Appuyez pour sélectionner le dossier dans lequel vous souhaitez créer une configuration cloud.

   Pour plus d’informations sur la création et la configuration d’un dossier pour les configurations de service cloud, voir [Configurer le dossier pour les configurations de service cloud](#cloud-folder).

1. Appuyez sur **[!UICONTROL Créer]** pour ouvrir l’**[!UICONTROL assistant Créer une configuration de source de données]**. Indiquez un nom et éventuellement un titre pour la configuration, sélectionnez **[!UICONTROL Service OData]** dans la liste déroulante **[!UICONTROL Type de service]**, cherchez et sélectionnez éventuellement une vignette pour la configuration, puis appuyez sur **[!UICONTROL Suivant]**.
1. Spécifiez les informations suivantes pour le service OData :

   * URL racine du service pour le service OData à configurer.
   * Sélectionnez le type d’authentification : aucune, OAuth2.0 ([code d’autorisation](https://oauth.net/2/grant-types/authorization-code/), [informations d’identification client](https://oauth.net/2/grant-types/client-credentials/)), authentification de base, clé API ou authentification personnalisée pour accéder au service OData et fournissez en conséquence les détails de l’authentification.

   Si vous sélectionnez **[!UICONTROL Clé API]** comme type d’authentification, spécifiez la valeur de la clé API. La clé API peut être envoyée en tant qu’en-tête de requête ou en tant que paramètre de requête. Sélectionnez l’une de ces options dans la liste déroulante **[!UICONTROL Emplacement]** et indiquez le nom de l’en-tête ou du paramètre de requête dans le champ **[!UICONTROL Nom du paramètre]**.

   >[!NOTE]
   >
   Vous devez sélectionner le type d’authentification OAuth 2.0 avec lequel vous connecter. [!DNL Microsoft®® Dynamics] services utilisant le point d’entrée OData comme racine de service.

1. Appuyez sur **[!UICONTROL Créer]** pour créer la configuration de cloud pour le service OData.

## Configuration de la liste SharePoint Microsoft® {#config-sharepoint-list}

<span class="preview"> Il s’agit d’une fonctionnalité de préversion accessible via notre [canal de version préliminaire](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features). </span>

Pour enregistrer les données dans un formulaire tabulaire, utilisez Microsoft® SharePoint List. Pour configurer une liste SharePoint Microsoft dans [!DNL Experience Manager] as a Cloud Service, procédez comme suit :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Cloud Service]** >  **[!UICONTROL Microsoft®® SharePoint]**.
1. Sélectionnez un **conteneur de configuration**. La configuration est stockée dans le conteneur de configuration sélectionné.
1. Cliquez sur **[!UICONTROL Créer]** > **[!UICONTROL Liste SharePoint]** dans la liste déroulante. L’assistant de configuration SharePoint s’affiche.
1. Spécifiez le **[!UICONTROL titre]**, l’**[!UICONTROL ID client]**, le **[!UICONTROL secret client]** et l’**[!UICONTROL URL OAuth]**. Pour savoir comment récupérer l’ID client et le secret client pour l’URL OAuth, consultez la [documentation Microsoft®](https://learn.microsoft.com/fr-fr/graph/auth-register-app-v2).
   * Vous pouvez récupérer l’`Client ID` et le `Client Secret` de votre application sur le portail Microsoft® Azure.
   * Sur le portail Microsoft® Azure, ajoutez l’URI de redirection en tant que `https://[author-instance]/libs/cq/sharepointlist/content/configurations/wizard.html`. Remplacez `[author-instance]` par l’URL de votre instance de création.
   * Ajout des autorisations d’API `offline_access` et `Sites.Manage.All` dans le **Graphique Microsoft®** pour fournir des autorisations de lecture/écriture. Ajouter `AllSites.Manage` dans la fonction **Sharepoint** pour interagir à distance avec les données SharePoint.
   * Utilisez l’URL OAuth `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Remplacez `<tenant-id>` par le `tenant-id` de votre application depuis le portail Microsoft® Azure.

     >[!NOTE]
     >
     Le champ du **secret client** est obligatoire ou facultatif selon la configuration de votre application Azure Active Directory. Si votre application est configurée pour utiliser un secret client, vous devez l’indiquer.

1. Cliquez sur **[!UICONTROL Connecter]**. Lors d’une connexion réussie, le message `Connection Successful` s’affiche.
1. Sélectionner **[!UICONTROL Site SharePoint]** et **[!UICONTROL Liste SharePoint]** dans la liste déroulante.
1. Appuyer **[!UICONTROL Créer]** pour créer la configuration cloud pour Microsoft® SharePointList.

<!--## Certificate-based mutual authentication for RESTful and SOAP web services {#mutual-authentication}

When you enable mutual authentication for form data model, both the data source and [!DNL Experience Manager] Server running Form Data Model authenticate each other's identity before sharing any data. You can use mutual authentication for REST and SOAP-based connections (data sources). To configure mutual authentication for a Form Data Model on your [!DNL Experience Manager Forms] environment:

1. Upload the private key (certificate) to [!DNL Experience Manager Forms] server. To upload the private key:
   1. Log in to your [!DNL Experience Manager Forms] server as an administrator.
   1. Navigate to **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**. Select the `fd-cloudservice` user and tap **[!UICONTROL Properties]**.
   1. Open the **[!UICONTROL Keystore]** tab, expand the **[!UICONTROL Add Private Key from KeyStore file]** option, upload the KeyStore File, specify the aliases, passwords, and tap **[!UICONTROL Submit]**. The Certificate is uploaded.  The private key alias is mentioned in the certificate and set while creating the certificate.
1. Upload trust certificate to Global Trust Store. To upload the certificate:
   1. Navigate to **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Trust Store]**.
   1. Expand the **[!UICONTROL Add Certificate from CER file]** option, tap **[!UICONTROL Select Certificate File]**, upload the certificate, and tap **[!UICONTROL Submit]**.
1. Configure [SOAP](#configure-soap-web-services) or [RESTful](#configure-restful-web-services) web services as the data source and select **[!UICONTROL Mutual authentication]** as the authentication type. If you configure multiple self-signed certificates for `fd-cloudservice` user, specify the Key Alias name for the certificate.-->

## Étapes suivantes {#next-steps}

Vous avez configuré la source de données. Vous pouvez ensuite créer un modèle de données de formulaire ou, si vous avez déjà créé un modèle de données de formulaire sans source de données, vous pouvez l’associer aux sources de données que vous venez de configurer. Voir [Créer un modèle de données de formulaire](create-form-data-models.md) pour plus de détails.
