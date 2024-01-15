---
title: Comment intégrer Salesforce à l’aide du flux d’informations d’identification client OAuth 2.0 avec AEM Forms ?
description: Découvrez comment intégrer Salesforce à AEM Forms à l’aide du flux d’informations d’identification client OAuth 2.0.
Keywords: Integration of Salesforce using OAuth 2.0 client credential flow, salesforce integration with oauth2 using client credential flow, salesforce and client credential integration
feature: Adaptive Forms, Form Data Model
role: User, Developer
exl-id: 2c2029ab-6fb4-41a6-846c-175c3a79d921
source-git-commit: 527c9944929c28a0ef7f3e617ef6185bfed0d536
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 74%

---

# Connexion d’un formulaire adaptatif à Salesforce à l’aide du flux d’informations d’identification client OAuth 2.0 {#configure-salesforce-with-ouath-2.0-client-credential}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/oauth2-client-credentials-flow-for-server-to-server-integration.html) |
| AEM as a Cloud Service | Cet article |

Vous pouvez utiliser les informations d’identification du client OAuth 2.0 pour intégrer AEM Forms à l’application Salesforce. Les informations d’identification du client OAuth 2.0 consistent en une méthode standard et sécurisée de communication directe sans intervention utilisateur.

![Workflow lors de la définition de la communication entre AEM Forms et l’application Salesforce](/help/forms/assets/salesforce-workflow.png).

AEM Forms échange les informations d’identification du client (consumer key et secret du client), définies dans l’application connectée Salesforce, pour obtenir un jeton d’accès.

L’utilisation des informations d’identification du client OAuth 2.0 présente plusieurs avantages par rapport à l’authentification à l’aide du flux de code d’autorisation :

* L’authentification des informations d’identification du client OAuth 2.0 permet plus de cinq connexions par utilisateur ou utilisatrice.
* La configuration de la source de données AEM continue à fonctionner lors de la désactivation, des modifications d’accès et de la mise à jour du mot de passe pour un utilisateur ou une utilisatrice AEM.

## Conditions préalables requises {#prerequisites}

Avant de définir la communication entre une application Salesforce et un environnement AEM, assurez-vous de disposer des éléments suivants :

* Créez une [application connectée à Salesforce avec le flux d’informations d’identification client OAuth 2.0](https://help.salesforce.com/s/articleView?id=sf.connected_app_client_credentials_setup.htm&amp;type=5) et un utilisateur ou une utilisatrice API uniquement pour votre entreprise et obtenez la consumer key et le secret client pour l’application.

* Assurez-vous que votre fichier Swagger est correctement configuré pour correspondre aux API de votre entreprise. Vous pouvez également choisir de [créer un fichier Swagger](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/forms/integrate-with-salesforce/describe-rest-api.html?lang=fr) à partir de zéro, adapté à l’utilisation dans votre environnement AEM.


## Configuration de l’application Salesforce à l’aide du flux d’informations d’identification client OAuth 2.0 {#steps-to-create-aem-datasource-configuration}

Pour connecter le formulaire adaptatif à l’application Salesforce à l’aide des paramètres d’authentification des informations d’identification client OAuth 2.0, procédez comme suit :

1. Connectez-vous à votre instance de création.
1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Services cloud]** > **[!UICONTROL Sources de données]**.
1. Sélectionnez le dossier de configuration.
1. Cliquez sur **[!UICONTROL Créer]**. **[!UICONTROL Créer une configuration de source de données]** apparaît.
1. Spécifiez le **[!UICONTROL Titre]** et sélectionnez le **[!UICONTROL Type de service]** comme **[!UICONTROL Service RESTful]**.
1. Cliquez sur **[!UICONTROL Suivant]**.
1. Sélectionnez la **[!UICONTROL Source Swagger]** comme **[!UICONTROL Fichier].**

   >[!NOTE]
   >
   > Lorsque le fichier swagger est sélectionné, le schéma, le nom de l’hôte et le chemin d’accès de base sont automatiquement renseignés.

1. Chargez le fichier Swagger créé à partir de votre ordinateur local en cliquant sur **[!UICONTROL Parcourir]**.
1. Sélectionnez le **[!UICONTROL Type d’authentification]** comme **[!UICONTROL OAuth 2.0]**. Le panneau **[!UICONTROL Paramètres d’authentification]** s’affiche.
1. Sélectionnez la variable **[!UICONTROL Type d’octroi]** as **[!UICONTROL Informations d’identification client]**.
1. Spécifiez l’**[!UICONTROL ID client]** et le **[!UICONTROL Secret du client]** obtenus à partir de l’application connectée à Salesforce.
1. Spécifiez l’**[!UICONTROL URL du jeton d’accès]** au format
   `https://[MyDomainName].my.salesforce.com/services/oauth2/token`.

   >[!NOTE]
   >
   > Chaque organisation possède son propre nom de domaine spécifique.

1. Cliquez sur **[!UICONTROL Tester la connexion]**.
1. Si la connexion est établie, cliquez sur le bouton **[!UICONTROL Créer]**.

Maintenant, vous pouvez [création du modèle de données de formulaire](/help/forms/create-form-data-models.md) pour envoyer le formulaire adaptatif à l’application Salesforce.


