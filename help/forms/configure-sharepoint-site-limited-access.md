---
title: Comment configurer un site SharePoint avec un accès limité à l’aide de la portée d’autorisation ?
description: Découvrez comment configurer le site SharePoint avec un accès limité à l’aide de la portée d’autorisation.
keywords: Comment configurer le site SharePoint avec un accès limité ?, Configuration de SharePoint avec un accès limité, Utilisation de la portée d’autorisation pour limiter l’accès au site SharePoint.
feature: Adaptive Forms, Core Components
role: User, Developer
exl-id: 3230bab2-c1aa-409d-9f01-c42cf88b1135
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 23%

---

# Configurer un site SharePoint avec accès limité à l’aide du champ d’application de l’autorisation

<span class="preview"> Cette fonctionnalité est disponible dans le cadre du programme des utilisateurs et utilisatrices précoces. Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre identifiant e-mail officiel pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité. </span>

L’accès limité ou restreint a pour but d’améliorer la gestion de la sécurité en permettant aux administrateurs de contrôler l’accès des utilisateurs à un site SharePoint particulier ou à un groupe de sites SharePoint. Le niveau d’autorisation est utile lorsque vous devez accorder à un utilisateur ou à un groupe l’accès à un site spécifique sans lui permettre d’afficher d’autres sites SharePoint non autorisés.

## Avantages de la configuration de SharePoint Site avec un accès limité

Avantages pour fournir un accès limité au site SharePoint :

* **Sécurité renforcée** : en limitant l’accès, vous pouvez vous assurer que seul le personnel autorisé a la possibilité d’afficher ou de manipuler des informations sensibles, ce qui réduit le risque d’accès non autorisé.

* **Principe de moindre privilège** : il fournit aux utilisateurs les niveaux minimaux d’accès, ou autorisations, nécessaires à l’exécution de leurs fonctions. Cela réduit l’exposition de chaque utilisateur aux parties sensibles du réseau, ce qui peut protéger contre les menaces internes potentielles.

* **Protection des données** : l’accès restreint permet de protéger les données critiques contre l’exposition. Cela permet de s’assurer que seuls les utilisateurs et utilisatrices qui ont besoin de voir les données peuvent y accéder, ce qui est essentiel pour se conformer aux réglementations sur la protection des données.

* **Prévention des pertes de données accidentelles** : avec moins de personnes capables de modifier le contenu, les risques de suppression ou de modification accidentelle de données importantes sont considérablement réduits.

* **Flux de données contrôlé** : permet de contrôler le flux d’informations au sein et en dehors de l’organisation, en veillant à ce que les données ne se retrouvent pas entre de mauvaises mains.

## Configuration de SharePoint avec un accès limité à l’aide de la portée d’autorisation

Suivez les étapes ci-dessous pour configurer les sites SharePoint avec un accès limité à l’aide des portées d’autorisation :

1. [Créez une application avec ](#create-an-application-with-the-limited-permission-in-the-azure-portal)
1. [Définissez la portée de l’autorisation sur l’instance AEM](#set-the-authorization-scope-at-aem-instance)

### Créez une application avec l’autorisation limitée dans le portail Azure

Créez une application sur le portail Azure [Microsoft](https://portal.azure.com/#home) avec la portée d’autorisation `Sites.Selected` dans l’API Graph Microsoft.

![Site SharePoint Sélectionné](/help/forms/assets/sharepoint-selected-site.png)

Pour plus d’informations sur la manière de récupérer `Client ID`, `Client Secret` et `Tenant ID` pour `OAuth URL`, consultez la documentation de [Microsoft®](https://learn.microsoft.com/fr-fr/graph/auth-register-app-v2).
* Sur le portail Microsoft® Azure, ajoutez l’URI de redirection en tant que `https://[author-instance]/libs/cq/sharepoint/content/configurations/wizard.html`. Remplacez `[author-instance]` par l’URL de votre instance de création.
* Ajoutez la portée des autorisations `offline_access` et `Sites.Selected` dans l’API Graph Microsoft pour fournir un accès restreint à Sites.
* Pour l’URL OAuth : `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Remplacez `<tenant-id>` par le `tenant-id` de votre application depuis le portail Microsoft® Azure.

L’utilisation de l’autorisation API `Sites.Selected` nécessite une application enregistrée sur le portail Azure avec les autorisations appropriées définies pour SharePoint Online Sites. Cette configuration garantit que l’application dispose de l’autorisation nécessaire pour interagir avec le site SharePoint dans la portée définie, fournissant ainsi l’accès limité requis.

Reportez-vous à l’article de blog [ - Développement d’applications qui utilisent Sites.Autorisations sélectionnées pour les sites SPO](https://techcommunity.microsoft.com/t5/microsoft-sharepoint-blog/develop-applications-that-use-sites-selected-permissions-for-spo/ba-p/3790476) pour obtenir des instructions sur le développement d’applications qui utilisent des autorisations `Sites.Selected` pour les sites SharePoint Online.

### Définissez la portée de l’autorisation sur l’instance AEM

Pour fournir un accès limité à un site Microsoft SharePoint, il est essentiel de définir correctement la portée de l’autorisation. Pour définir la portée de l’autorisation et connecter AEM Forms à votre stockage Microsoft® SharePoint :

1. Accédez à votre instance de **création AEM Forms** > **[!UICONTROL Outils]** > **[!UICONTROL Services cloud]** > **[!UICONTROL Microsoft® SharePoint]**.
1. Une fois que vous avez sélectionné le stockage **[!UICONTROL Microsoft® SharePoint]**, l’interface vous redirige vers le **[!UICONTROL navigateur SharePoint]**.
1. Sélectionnez un **conteneur de configuration**. La configuration est stockée dans le conteneur de configuration sélectionné.
1. Cliquez sur **[!UICONTROL Créer]** > **[!UICONTROL Bibliothèque de documents SharePoint]** dans la liste déroulante. L’assistant de configuration SharePoint s’affiche.

   ![Accès limité au site SharePoint](/help/forms/assets/sharepoint-doc-library-limited-scopes.png)

1. Spécifiez les **[!UICONTROL Titre]**, **[!UICONTROL Identifiant client]** et **[!UICONTROL Secret client]**. Pour plus d’informations sur la manière de récupérer l’ID client et le secret client, voir la documentation de [Microsoft®](https://learn.microsoft.com/fr-fr/graph/auth-register-app-v2).

1. Utilisez l’URL OAuth comme `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Remplacez `<tenant-id>` par le `tenant-id` de votre application depuis le portail Microsoft® Azure.

   >[!NOTE]
   >
   > Le champ du **secret client** est obligatoire ou facultatif selon la configuration de votre application Azure Active Directory. Si votre application est configurée pour utiliser un secret client, vous devez l’indiquer.

1. Ajoutez le `offline_access Sites.Selected` dans le champ `Authorization Scope` . Lorsque vous ajoutez la portée de `offline_access Sites.Selected` dans le champ de zone de texte `Authorization Scope`, la zone de texte `SharePoint Site ID` devient visible à l’écran.

1. Spécifiez l’ID de site SharePoint. Pour savoir comment récupérer l’ID de site SharePoint, reportez-vous à la section [Octets supplémentaires](#extra-bytes).

1. Cliquez sur **[!UICONTROL Vérifier la connexion au site]**. Lors d’une connexion réussie, le message `Connection Successful` s’affiche.

1. Maintenant, sélectionnez **Site SharePoint** > **Bibliothèque de documents** > **Dossier SharePoint**, pour enregistrer les données.

   >[!NOTE]
   >
   >* Par défaut, `forms-ootb-storage-adaptive-forms-submission` est présent sur le site SharePoint sélectionné.
   >* Créez un dossier sous la forme `forms-ootb-storage-adaptive-forms-submission`, s’il n’est pas déjà présent dans la bibliothèque `Documents` du site SharePoint sélectionné en cliquant sur **Créer un dossier**.

Vous pouvez désormais utiliser cette configuration de [SharePoint Sites pour l’action d’envoi dans un formulaire adaptatif](/help/forms/configure-submit-action-sharepoint.md#use-sharepoint-document-library-configuration-in-an-adaptive-form-use-sharepoint-configuartion-in-af).

## Octets supplémentaires

Pour récupérer la valeur du `SharePoint Site ID` :
1. Accédez aux [API Microsoft Graph Explorer](https://developer.microsoft.com/en-us/graph/graph-explorer).
1. Dans le volet de gauche, sous les API `SharePoint Sites`, cliquez sur `Search for a SharePoint site by keyword`.
1. Remplacez l’espace réservé `contoso` par le nom réel de votre site SharePoint pour récupérer l’ID de site correspondant.

   ![ID de bibliothèque de documents SharePoint](/help/forms/assets/sharepoint-site-id.png)

Lorsque vous cliquez sur le bouton `Run Query` , l’identifiant du site s’affiche à l’écran.
