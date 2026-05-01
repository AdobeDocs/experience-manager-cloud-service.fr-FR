---
title: Comment envoyer des données à un stockage de liste SharePoint lors de l’envoi d’un formulaire adaptatif ?
Description: Learn how to send data from your Adaptive Form to a SharePoint storage like a SharePoint list when you submit the form.
keywords: Comment connecter la liste SharePoint d’un formulaire adaptatif ?, Envoyer à SharePoint, Créer une configuration de liste SharePoint, Utiliser l’action d’envoi Envoyer à SharePoint dans un formulaire adaptatif, Connecter un formulaire adaptatif à la liste SharePoint Microsoft&reg ;.
feature: Adaptive Forms, Core Components, Foundation Components, Edge Delivery Services
role: User, Developer
badgeSaas: label="AEM Forms" type="Positive" tooltip="S’applique à AEM Forms)."
exl-id: 9ac3e7be-c6fa-4dbc-9aba-b81741ba6c55
source-git-commit: 0e5045b87719781301d91874c7355eda9426beef
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 45%

---

# Connecter un formulaire adaptatif à une liste Microsoft® SharePoint {#connect-af-sharepoint-list}

>[!VIDEO](https://video.tv.adobe.com/v/3424820/connect-aem-adaptive-form-to-sharepointlist/?quality=12&learn=on)

<span> Cette vidéo s’applique uniquement aux composants principaux. Pour les composants éditeur universel/de base, reportez-vous à l’article </span>.

Pour utiliser l’action de soumission [!UICONTROL Soumettre à la liste SharePoint] dans un formulaire adaptatif :

1. [Créer une configuration de liste SharePoint](#1-create-a-sharepoint-list-configuration) : connecte AEM Forms à votre stockage de listes Microsoft® SharePoint.
1. [Utiliser l’envoi à l’aide du modèle de données de formulaire (FDM) dans un formulaire adaptatif](#2-use-the-submit-using-form-data-model-fdm-in-an-adaptive-form-use-submit-using-fdm) : connecte votre formulaire adaptatif au SharePoint Microsoft® configuré.

## &#x200B;1. Créer une configuration de liste SharePoint

Pour connecter AEM Forms à votre liste Microsoft® SharePoint :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Services cloud]** > **[!UICONTROL Microsoft® SharePoint]**.
1. Sélectionnez un **conteneur de configuration**. La configuration est stockée dans le conteneur de configuration sélectionné.
1. Cliquez sur **[!UICONTROL Créer]** > **[!UICONTROL Liste SharePoint]** dans la liste déroulante. L’assistant de configuration SharePoint s’affiche.
1. Spécifiez le **[!UICONTROL titre]**, l’**[!UICONTROL ID client]**, le **[!UICONTROL secret client]** et l’**[!UICONTROL URL OAuth]**. Pour savoir comment récupérer l’ID client et le secret client pour l’URL OAuth, consultez la [documentation Microsoft®](https://learn.microsoft.com/fr-fr/graph/auth-register-app-v2).
   * Vous pouvez récupérer l’`Client ID` et le `Client Secret` de votre application sur le portail Microsoft® Azure.
   * Sur le portail Microsoft® Azure, ajoutez l’URI de redirection en tant que `https://[author-instance]/libs/cq/sharepointlist/content/configurations/wizard.html`. Remplacez `[author-instance]` par l’URL de votre instance de création.
   * Ajoutez les autorisations d’API `offline_access` et `Sites.Manage.All` dans l’onglet **Graphique Microsoft®** pour fournir des autorisations de lecture/écriture. Ajoutez `AllSites.Manage` autorisation sous l’onglet **Sharepoint** pour interagir à distance avec les données SharePoint.
   * Utilisez l’URL OAuth `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Remplacez `<tenant-id>` par le `tenant-id` de votre application depuis le portail Microsoft® Azure.

     >[!NOTE]
     >
     > Le champ du **secret client** est obligatoire ou facultatif selon la configuration de votre application Azure Active Directory. Si votre application est configurée pour utiliser un secret client, vous devez l’indiquer.

1. Cliquez sur **[!UICONTROL Connecter]**. Lors d’une connexion réussie, le message `Connection Successful` s’affiche.
1. Sélectionnez **[!UICONTROL Site SharePoint]** et **[!UICONTROL Liste SharePoint]** dans la liste déroulante.
1. Sélectionnez **[!UICONTROL Créer]** pour créer la configuration cloud pour Microsoft® SharePointList.

### Authentification basée sur les certificats {#certificate-based-authentication}

<span class="preview">’authentification basée sur les certificats pour la configuration de la liste SharePoint se trouve sous le programme des utilisateurs et utilisatrices précoces . Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre identifiant e-mail officiel pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité. </span>

Dans l’assistant de configuration Liste SharePoint :

1. Définissez **[!UICONTROL Type d’authentification]** sur **Authentification basée sur certificat**.
1. Spécifiez **[!UICONTROL Titre]**, **[!UICONTROL ID client]**, **[!UICONTROL Alias de certificat]**, **[!UICONTROL ID client]** et **[!UICONTROL Nom du client]**.
1. Saisissez l’URL du site **&#x200B;**, vérifiez la connexion au site si nécessaire, puis sélectionnez la liste **[!UICONTROL SharePoint]**.
1. Cliquez sur **[!UICONTROL Connexion]** pour vérifier la connexion, puis sur **[!UICONTROL Enregistrer et fermer]** pour enregistrer la configuration.

La capture d’écran ci-dessous affiche la configuration de la liste SharePoint avec l’**authentification basée sur un certificat** :

![Configuration de la liste SharePoint avec authentification par certificat](/help/forms/assets/sharepoint-list-certificate-auth-configuration.png){width=50%, height=50%, align=center}

Pour préparer le certificat pour AEM et Microsoft Azure, procédez comme suit dans AEM, puis enregistrez le certificat public dans Microsoft Azure.

**Dans AEM**

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Sécurité]** > **[!UICONTROL Utilisateurs]**.
1. Recherchez **[!UICONTROL fd-cloudservice]**, sélectionnez l’utilisateur et cliquez sur **[!UICONTROL Propriétés]**.
1. Ouvrez l’onglet **[!UICONTROL Keystore]**. Si un fichier de stockage des clés n’est pas encore créé, cliquez sur **[!UICONTROL Créer un fichier de stockage des clés]** et renseignez les invites pour définir le mot de passe du fichier de stockage des clés.
1. Ajoutez la clé privée au fichier de stockage des clés : développez **[!UICONTROL Ajouter la clé privée à partir du fichier de stockage des clés]** et chargez votre fichier **.jks**.
1. Saisissez un **[!UICONTROL Alias]** qui correspond à l’**[!UICONTROL Alias de certificat]** dans la configuration de la liste SharePoint, envoyez le matériel de clé, puis cliquez sur **[!UICONTROL Enregistrer et fermer]**.

La capture d’écran affiche le fichier de stockage des clés une fois le certificat ajouté. Le **[!UICONTROL Alias]** doit correspondre au **[!UICONTROL Alias du certificat]** dans la configuration cloud de la liste SharePoint :

![Keystore de l’utilisateur fd-cloudservice avec alias de certificat](/help/forms/assets/fd-cloudservice-keystore-certificate.png){width=50%, height=50%, align=center}

**Dans Microsoft Azure**

1. Ouvrez l’enregistrement de votre application et accédez à **Certificats et secrets** > **Certificats**.
1. Sélectionnez **Télécharger le certificat** et téléchargez le fichier de certificat (clé publique) auquel Azure doit faire confiance pour l’application.

La capture d’écran affiche l’onglet **Certificats** sur le portail Azure, où vous téléchargez le certificat pour l’enregistrement de l’application :

![Certificats et secrets d’enregistrement de l’application &#x200B;](/help/forms/assets/azure-app-registration-sharepoint-certificates.png){width=50%, height=50%, align=center}

## &#x200B;2. Utiliser l’envoi à l’aide du modèle de données de formulaire (FDM) dans un formulaire adaptatif {#use-submit-using-fdm}

Vous pouvez utiliser la configuration de liste SharePoint créée dans un formulaire adaptatif pour enregistrer des données ou un document d’enregistrement généré dans une liste SharePoint. Pour utiliser une liste SharePoint dans un formulaire adaptatif, procédez comme suit :

1. [Créer un modèle de données de formulaire (FDM) à l’aide de la configuration de liste SharePoint Microsoft®](/help/forms/create-form-data-models.md)
1. [Configurer le modèle de données de formulaire (FDM) pour récupérer et envoyer des données](/help/forms/work-with-form-data-model.md#configure-services)
1. [Créer un formulaire adaptatif](/help/forms/creating-adaptive-form-core-components.md)
1. [Configuration d’une action Envoyer à l’aide d’un modèle de données de formulaire (FDM)](/help/forms/using-form-data-model.md)

Lorsque vous soumettez le formulaire, les données sont enregistrées dans le stockage de listes Microsoft® SharePoint que vous avez spécifié.

>[!NOTE]
>
> Dans la liste Microsoft® SharePoint, les types de colonnes suivants ne sont pas pris en charge :
>
> * Colonne image
> * Colonne métadonnées
> * Colonne personne
> * Colonne données externes

## Articles connexes

{{af-submit-action}}
