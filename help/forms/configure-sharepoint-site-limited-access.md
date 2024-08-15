---
Title: How to configure a SharePoint Site with limited access using authorization scope?
Description: Learn how to configure SharePoint Site with limited access using the authorization scope.
keywords: Comment configurer SharePoint Site avec accès limité ?, Configurer SharePoint avec accès limité, Utiliser la portée d’autorisation pour limiter l’accès à SharePoint Site.
feature: Adaptive Forms, Core Components
role: User, Developer
source-git-commit: 85cef99dc7a8d762d12fd6e1c9bc2aeb3f8c1312
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 23%

---


<span class="preview"> La fonctionnalité est disponible dans le cadre du programme des premiers adopteurs. Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre adresse e-mail officielle pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité. </span>

# Configurer un site SharePoint avec accès limité à l’aide du champ d’application de l’autorisation

L’objectif d’un accès limité ou restreint est d’améliorer la gestion de la sécurité en permettant aux administrateurs de contrôler l’accès des utilisateurs à un site SharePoint spécifique ou à un groupe de sites SharePoint. Le niveau d’autorisation est utile lorsque vous devez accorder à un utilisateur ou à un groupe l’accès à un site spécifique sans lui permettre d’afficher d’autres sites SharePoint non autorisés.

## Avantages de la configuration du site SharePoint avec un accès limité

Avantages d’un accès limité au site SharePoint :

* **Amélioration de la sécurité** : en limitant l’accès, vous pouvez vous assurer que seul le personnel autorisé peut afficher ou manipuler des informations sensibles, ce qui réduit le risque d’accès non autorisé.

* **Principe du moindre privilège** : il fournit aux utilisateurs les niveaux d’accès (ou les autorisations) minimaux nécessaires pour exécuter leurs fonctions de tâche. Cela permet de réduire l’exposition de chaque utilisateur à des parties sensibles du réseau, qui peuvent être protégées contre les menaces internes potentielles.

* **Protection des données** : un accès limité permet de protéger les données critiques contre l’exposition. Elle garantit que seuls les utilisateurs qui ont besoin de consulter les données peuvent y accéder, ce qui est essentiel pour se conformer aux réglementations en matière de protection des données.

* **Prévention des pertes de données accidentelles** : avec moins de personnes capables de modifier le contenu, les risques de suppression accidentelle ou de modification de données importantes sont considérablement réduits.

* **Flux de données contrôlé** : permet de contrôler le flux d’informations au sein et à l’extérieur de l’organisation, en s’assurant que les données ne tombent pas entre de mauvaises mains.

## Configuration de SharePoint avec accès limité à l’aide de la portée d’autorisation

Suivez les étapes ci-dessous pour configurer SharePoint Sites avec un accès limité à l’aide des portées d’autorisation :

1. [Créez une application avec la fonction ](#create-an-application-with-the-limited-permission-in-the-azure-portal)
1. [Définition de la portée d’autorisation sur l’instance AEM](#set-the-authorization-scope-at-aem-instance)

### Création d’une application avec les autorisations limitées sur le portail Azure

Créez une application sur le [portail Microsoft Azure](https://portal.azure.com/#home) avec la portée d’autorisation `Sites.Selected` dans l’API Graph de Microsoft.

![Site sélectionné SharePoint](/help/forms/assets/sharepoint-selected-site.png)

Pour plus d&#39;informations sur la façon de récupérer `Client ID`, `Client Secret` et `Tenant ID` pour `OAuth URL`, consultez la [documentation Microsoft®](https://learn.microsoft.com/fr-fr/graph/auth-register-app-v2).
* Sur le portail Microsoft® Azure, ajoutez l’URI de redirection en tant que `https://[author-instance]/libs/cq/sharepoint/content/configurations/wizard.html`. Remplacez `[author-instance]` par l’URL de votre instance de création.
* Ajoutez l’étendue des autorisations `offline_access` et `Sites.Selected` dans l’API Microsoft Graph afin de fournir un accès restreint à Sites.
* Pour l’URL OAuth : `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Remplacez `<tenant-id>` par le `tenant-id` de votre application depuis le portail Microsoft® Azure.

Pour utiliser l’autorisation d’API `Sites.Selected`, une application doit être enregistrée sur le portail Azure avec les autorisations appropriées définies pour SharePoint Online Sites. Cette configuration garantit que l’application dispose de l’autorisation nécessaire pour interagir avec le site SharePoint dans la portée définie, fournissant ainsi l’accès limité requis.

Reportez-vous à l’ [article de blog - Developing Applications that use Sites.Selected permissions for SPO sites](https://techcommunity.microsoft.com/t5/microsoft-sharepoint-blog/develop-applications-that-use-sites-selected-permissions-for-spo/ba-p/3790476) pour obtenir des instructions sur le développement d’applications qui utilisent des autorisations `Sites.Selected` pour SharePoint Online Sites.

### Définition de la portée d’autorisation sur l’instance AEM

Pour fournir un accès limité à un site SharePoint Microsoft, il est essentiel de définir correctement la portée de l’autorisation. Pour définir la portée d’autorisation et connecter AEM Forms à votre stockage Microsoft® SharePoint :

1. Accédez à votre instance de **création AEM Forms** > **[!UICONTROL Outils]** > **[!UICONTROL Services cloud]** > **[!UICONTROL Microsoft® SharePoint]**.
1. Une fois que vous avez sélectionné le stockage **[!UICONTROL Microsoft® SharePoint]**, l’interface vous redirige vers le **[!UICONTROL navigateur SharePoint]**.
1. Sélectionnez un **conteneur de configuration**. La configuration est stockée dans le conteneur de configuration sélectionné.
1. Cliquez sur **[!UICONTROL Créer]** > **[!UICONTROL Bibliothèque de documents SharePoint]** dans la liste déroulante. L’assistant de configuration SharePoint s’affiche.

   ![SharePoint Site Limited Site Access](/help/forms/assets/sharepoint-doc-library-limited-scopes.png)

1. Spécifiez le **[!UICONTROL Titre]**, l&#39;**[!UICONTROL ID client]** et le **[!UICONTROL Secret client]**. Pour plus d&#39;informations sur la récupération de l&#39;ID client et du secret client, consultez la [documentation Microsoft®](https://learn.microsoft.com/fr-fr/graph/auth-register-app-v2).

1. Utilisez l’URL OAuth comme `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Remplacez `<tenant-id>` par le `tenant-id` de votre application depuis le portail Microsoft® Azure.

   >[!NOTE]
   >
   > Le champ du **secret client** est obligatoire ou facultatif selon la configuration de votre application Azure Active Directory. Si votre application est configurée pour utiliser un secret client, vous devez l’indiquer.

1. Ajoutez le `offline_access Sites.Selected` dans le champ `Authorization Scope` . Lorsque vous ajoutez la portée `offline_access Sites.Selected` dans le champ `Authorization Scope` textbox , la zone de texte `SharePoint Site ID` devient visible à l’écran.

1. Spécifiez l’identifiant de site SharePoint. Pour savoir comment récupérer l’identifiant de site SharePoint, reportez-vous à la section [Octets supplémentaires](#extra-bytes) .

1. Cliquez sur **[!UICONTROL Vérifier la connexion au site]**. Lors d’une connexion réussie, le message `Connection Successful` s’affiche.

1. Maintenant, sélectionnez **Site SharePoint** > **Bibliothèque de documents** > **Dossier SharePoint**, pour enregistrer les données.

   >[!NOTE]
   >
   >* Par défaut, `forms-ootb-storage-adaptive-forms-submission` est présent sur le site SharePoint sélectionné.
   >* Créez un dossier sous la forme `forms-ootb-storage-adaptive-forms-submission`, s’il n’est pas déjà présent dans la bibliothèque `Documents` du site SharePoint sélectionné en cliquant sur **Créer un dossier**.

Désormais, vous pouvez utiliser cette [configuration de sites SharePoint pour l’action d’envoi dans un formulaire adaptatif](/help/forms/configure-submit-action-sharepoint.md#use-sharepoint-document-library-configuration-in-an-adaptive-form-use-sharepoint-configuartion-in-af).

## Octets supplémentaires

Pour récupérer la valeur de `SharePoint Site ID` :
1. Accédez aux [API Microsoft Graph Explorer](https://developer.microsoft.com/en-us/graph/graph-explorer).
1. Dans le volet de gauche, sous les API `SharePoint Sites`, cliquez sur `Search for a SharePoint site by keyword`.
1. Remplacez l’espace réservé `contoso` par le nom réel de votre site SharePoint pour récupérer l’identifiant de site correspondant.

   ![SharePoint Document Library ID](/help/forms/assets/sharepoint-site-id.png)

Lorsque vous cliquez sur le bouton `Run Query`, l’ID de site s’affiche à l’écran.