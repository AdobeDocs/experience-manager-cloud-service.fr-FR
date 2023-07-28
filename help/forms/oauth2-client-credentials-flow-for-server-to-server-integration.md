---
title: Comment intégrer l’intégration de Salesforce à AEM Forms à l’aide du flux d’informations d’identification client OAuth 2.0 ?
seo-title: Salesforce integration with AEM Forms using OAuth 2.0 client credential flow
description: Procédure d’intégration de Salesforce à AEM Forms à l’aide du flux d’informations d’identification client OAuth 2.0
seo-description: Steps to integrate Salesforce integration with AEM Forms using OAuth 2.0 client credential flow
Keywords: Integration of Salesforce using OAuth 2.0 client credential flow, salesforce integration with oauth2 using client credential flow, salesforce and client credential integration
source-git-commit: 2c0a816b61cfc17a83b24b28be1f317e9681c6c5
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 3%

---


# Intégration de l’application Salesforce à l’aide du flux d’informations d’identification client OAuth 2.0 {#configure-salesforce-with-ouath-2.0-client-credential}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/oauth2-client-credentials-flow-for-server-to-server-integration.html) |
| AEM as a Cloud Service | Cet article |

Vous pouvez utiliser les informations d’identification du client OAuth 2.0 pour intégrer AEM Forms à l’application Salesforce. Les informations d’identification du client OAuth 2.0 sont une méthode standard et sécurisée de communication directe sans intervention de l’utilisateur.

![Workflow lors de la définition de la communication entre AEM Forms et l’application Salesforce](/help/forms/assets/salesforce-workflow.png)
AEM Forms échange les informations d’identification du client (clé client et secret client), définies dans l’application connectée Salesforce, pour obtenir un jeton d’accès.

L’utilisation des informations d’identification du client OAuth 2.0 présente plusieurs avantages pour l’authentification par rapport à l’authentification Flux de code d’autorisation :

* L’authentification des informations d’identification du client OAuth 2.0 permet plus de cinq connexions par utilisateur.
* AEM configuration de la source de données continue à fonctionner sur la désactivation, les modifications d’accès et la mise à jour du mot de passe pour un utilisateur AEM.

## Conditions préalables {#prerequisites}

Avant de définir la communication entre une application Salesforce et un environnement AEM :

* Créez un [Application connectée à Salesforce avec flux d’informations d’identification client OAuth 2.0](https://help.salesforce.com/s/articleView?id=sf.connected_app_client_credentials_setup.htm&amp;type=5) et un utilisateur API uniquement pour votre organisation et obtenez la clé client et le secret client pour l’application.

* Assurez-vous que votre fichier Swagger est correctement configuré pour correspondre aux API de votre entreprise. Vous pouvez également choisir de [créer un fichier Swagger ;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/forms/integrate-with-salesforce/describe-rest-api.html) à partir de zéro, adapté à l’utilisation dans votre environnement AEM.


## Configuration de l’application Salesforce à l’aide du flux d’informations d’identification client OAuth 2.0 {#steps-to-create-aem-datasource-configuration}

Pour intégrer l’application Salesforce à un formulaire adaptatif à l’aide des paramètres d’authentification des informations d’identification client OAuth 2.0, procédez comme suit :

1. Connectez-vous à votre instance d’auteur .
1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Sources de données]**.
1. Sélectionnez le dossier de configuration.
1. Cliquez sur **[!UICONTROL Créer]** et la variable **[!UICONTROL Création d’une configuration de source de données]** apparaît.
1. Spécifiez la variable **[!UICONTROL Titre]** et sélectionnez la variable **[!UICONTROL Type de service]** as **[!UICONTROL Service RESTful]**.
1. Cliquez sur **[!UICONTROL Suivant]**.
1. Sélectionnez la variable **[!UICONTROL Source Swagger]** as **[!UICONTROL Fichier].**

   >[!NOTE]
   >
   > Lorsque le fichier swagger est sélectionné, le schéma, le nom de l’hôte et le chemin d’accès de base sont automatiquement renseignés.

1. Chargez le fichier swagger créé à partir de votre ordinateur local en cliquant sur **[!UICONTROL Parcourir]**.
1. Sélectionnez la variable **[!UICONTROL Type d’authentification]** as **[!UICONTROL OAuth 2.0]** et la variable **[!UICONTROL Paramètres d’authentification]** s’affiche.
1. Sélectionnez la variable **[!UICONTROL Type d’octroi]** as **[!UICONTROL Informations d’identification client]**.
1. Spécifiez la variable **[!UICONTROL ID client]** et **[!UICONTROL Secret du client]** obtenu à partir de l’application connectée Salesforce.
1. Spécifiez la variable **[!UICONTROL URL du jeton d’accès]** au format
   `https://[MyDomainName].my.salesforce.com/services/oauth2/token`.

   >[!NOTE]
   >
   > Chaque organisation possède son propre nom de domaine spécifique.

1. Cliquez sur **[!UICONTROL Tester la connexion]**.
1. Si la connexion réussit, cliquez sur le bouton **[!UICONTROL Créer]** bouton .

Maintenant, vous pouvez [création du modèle de données de formulaire](/help/forms/create-form-data-models.md) pour intégrer la source de données configurée à votre formulaire adaptatif.
