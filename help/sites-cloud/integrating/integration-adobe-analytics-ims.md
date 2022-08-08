---
title: Configuration IMS à utiliser lors de l’intégration à Adobe Analytics
description: En savoir plus sur la configuration IMS à utiliser lors de l’intégration à Adobe Analytics
exl-id: 12bd1573-373a-4001-be71-c8f155ef6896
source-git-commit: 0030b0f6f17dd66229f681e9c513786de4fe10a2
workflow-type: tm+mt
source-wordcount: '893'
ht-degree: 100%

---

# Configuration IMS à utiliser lors de l’intégration à Adobe Analytics {#ims-configuration-for-integration-with-adobe-analytics}

L’intégration d’Adobe Experience Manager as a Cloud Service (AEMaaCS) avec Adobe Analytics via l’API Analytics Standard nécessite la configuration d’Adobe IMS (système d’Identity Management). La configuration est réalisée avec la Developer Console Adobe.

>[!NOTE]
>
>La prise en charge de l’API Adobe Analytics Standard 2.0 a été nouvellement intégrée à AEMaaCS 2022.2.0. Cette version de l’API prend en charge l’authentification IMS.
>
>La sélection de l’API repose sur la méthode d’authentification utilisée pour l’intégration AEM/Analytics.
>
>Des informations supplémentaires sont également disponibles sous [Migration vers les API 2.0](https://developer.adobe.com/analytics-apis/docs/2.0/guides/migration/).

## Conditions préalables {#prerequisites}

Avant de commencer cette procédure :

* L’[assistance Adobe](https://helpx.adobe.com/fr/contact/enterprise-support.ec.html) doit configurer votre compte avec les éléments suivants :

   * Adobe Console
   * Developer Console Adobe
   * Adobe Analytics
   * Adobe IMS (système d’Identity Management)

* L’administrateur système de votre entreprise doit utiliser l’Admin Console pour donner aux développeurs de votre entreprise l’accès aux profils de produit appropriés.

   * Les développeurs spécifiques disposent ainsi des autorisations nécessaires pour activer les intégrations à l’aide de la Developer Console Adobe.
   * Pour plus d’informations, consultez le document [Gestion des développeurs](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html).


## Configuration d’une configuration IMS - Génération d’une clé publique {#configuring-ims-generating-a-public-key}

La première étape de la configuration consiste à créer une configuration IMS dans AEM et à générer la clé publique.

1. Dans AEM, ouvrez le menu **Outils**.
1. Dans la section **Sécurité**, sélectionnez **Configurations Adobe IMS**.
1. Sélectionnez **Créer** pour ouvrir la **Configuration du compte technique Adobe IMS**.
1. À l’aide de la liste déroulante sous **Configuration du cloud**, sélectionnez **Adobe Analytics**.
1. Activez **Créer un certificat** et saisissez un nouvel alias.
1. Confirmez avec **Créer un certificat**.

   ![Créer un certificat](assets/integrate-analytics-ims-01.png)

1. Sélectionnez **Télécharger** (ou **Télécharger la clé publique**) pour télécharger le fichier sur votre lecteur local afin qu’il soit prêt à être utilisé lors de la [configuration d’IMS pour l’intégration d’Adobe Analytics avec AEM](#configuring-ims-adobe-analytics-integration-with-aem).

   >[!CAUTION]
   >
   >Gardez cette configuration ouverte. Elle sera de nouveau nécessaire pour la [Réalisation de la configuration IMS dans AEM](#completing-the-ims-configuration-in-aem).

   ![Téléchargement du certificat](assets/integrate-analytics-ims-02.png)

## Configuration IMS pour l’intégration d’Adobe Analytics avec AEM {#configuring-ims-adobe-analytics-integration-with-aem}

À l’aide de la Developer Console Adobe, vous devez créer un projet (d’intégration) avec Adobe Analytics (pour AEM à utiliser), puis attribuer les privilèges requis.

### Création du projet {#creating-the-project}

Ouvrez la Developer Console Adobe pour créer un projet avec Adobe Analytics qui sera utilisé par AEM :

1. Ouvrez la Developer Console Adobe pour les projets :

   [https://developer.adobe.com/console/projects](https://developer.adobe.com/console/projects)

1. Tous les projets que vous avez s’affichent. Sélectionnez **Créer un projet** - L’emplacement et l’utilisation dépendent des éléments suivants :

   * Si vous n’avez pas encore de projet, **Créer un projet** sera au centre, en bas.
      ![Créer un projet - Premier projet](assets/integration-analytics-ims-02.png)
   * Si vous avez déjà des projets existants, ils seront répertoriés dans cette liste et **Créer un projet** apparaîtra en haut à droite.
      ![Créer un projet - Projets multiples](assets/integration-analytics-ims-03.png)


1. Sélectionnez **Ajouter au projet**, puis **API** :

   ![Prise en main de votre nouveau projet](assets/integration-analytics-ims-10.png)

1. Sélectionnez **Adobe Analytics**, puis **Suivant** :

   >[!NOTE]
   >
   >Si vous êtes abonné à Adobe Analytics mais que vous ne le voyez pas répertorié, cochez la case [Conditions préalables](#prerequisites).

   ![Ajoutez une API](assets/integration-analytics-ims-12.png)

1. Sélectionnez **Compte de service (JWT)** comme type d’authentification, puis continuez avec **Suivant** :

   ![Sélectionnez le type d’authentification](assets/integration-analytics-ims-12a.png)

1. **Chargement de votre clé publique**, puis, une fois l’opération terminée, passez à **Suivant** :

   ![Chargez votre clé publique](assets/integration-analytics-ims-13.png)

1. Vérifiez les informations d’identification et continuez avec **Suivant** :

   ![Vérification des informations d’identification](assets/integration-analytics-ims-15.png)

1. Sélectionnez les profils de produit requis et continuez en sélectionnant **Enregistrer l’API configurée** :

   ![Sélectionner les profils de produit requis](assets/integration-analytics-ims-16.png)

1. La configuration sera confirmée.

### Attribution de privilèges à l’intégration {#assigning-privileges-to-the-integration}

Vous devez maintenant attribuer les privilèges requis à l’intégration :

1. Ouvrez l’**Admin Console** Adobe :

   * [https://adminconsole.adobe.com](https://adminconsole.adobe.com/)

1. Accédez à **Products** (Produits) (barre d’outils supérieure), puis sélectionnez **Adobe Analytics - &lt;*your-tenant-id*>** (dans le panneau de gauche).
1. Sélectionnez **Product Profiles** (Profils de produit), puis l’espace de travail que vous souhaitez dans la liste présentée. Par exemple, l’espace de travail par défaut.
1. Sélectionnez **API Credentials** (Informations d’identification de l’API), puis la configuration d’intégration requise.
1. Sélectionnez **Editor** (Éditeur) en tant que propriété de **Product Role** (Rôle de produit) au lieu d’**Observer** (Observateur).

## Informations stockées pour le projet d’intégration de la Developer Console Adobe {#details-stored-for-the-ims-integration-project}

Dans la Developer Console Adobe - Projets, vous pouvez voir la liste de tous vos projets d’intégration :

* [https://developer.adobe.com/console/projects](https://developer.adobe.com/console/projects)

Sélectionnez une entrée de projet spécifique pour afficher plus d’informations sur la configuration. Celles-ci comprennent les éléments suivants :

* Présentation du projet
* Statistiques
* Informations d’identification
   * Compte de service (JWT)
      * Informations d’identification
      * Génération de JWT
* API
   * Par exemple, Adobe Analytics

Pour certains d’entre eux, vous devrez terminer l’intégration d’Adobe Analytics à AEM basée sur l’IMS.

## Réalisation de la configuration IMS dans AEM {#completing-the-ims-configuration-in-aem}

En retournant sur AEM, vous pouvez terminer la configuration IMS en ajoutant les valeurs requises pour l’intégration IMS pour Analytics :

1. Retournez dans l’instance de [Configuration IMS ouverte dans AEM](#configuring-ims-generating-a-public-key).
1. Sélectionnez **Suivant**.

1. Vous pouvez alors utiliser les [informations de configuration du projet dans la Developer Console Adobe](#details-stored-for-the-ims-integration-project) :

   * **Titre** : votre texte.
   * **Serveur d’autorisation** : copiez/collez ceci à partir de la ligne `aud` de la section **Payload** ci-dessous, par exemple `https://ims-na1.adobelogin.com` dans l’exemple ci-dessous.
   * **Clé d’API** : copiez-la à partir de la section **Informations d’identification** de la [Présentation du projet](#details-stored-for-the-ims-integration-project)
   * **Secret du client** : générez-le dans l’[Onglet Secret client de la section Compte de service (JWT)](#details-stored-for-the-ims-integration-project) et copiez-la.
   * **Payload** : copiez-le depuis l’[onglet Générer le JWT de la section Compte de service (JWT)](#details-stored-for-the-ims-integration-project).

   ![Informations de configuration IMS AEM](assets/integrate-analytics-ims-10.png)

1. Confirmez avec **Créer**.

1. Votre configuration Adobe Analytics s’affichera dans la console AEM.

   ![Configuration IMS](assets/integrate-analytics-ims-11.png)

## Confirmation de la configuration IMS {#confirming-the-ims-configuration}

Pour confirmer que la configuration fonctionne comme prévu :

1. Ouvrez :

   * `https://localhost<port>/libs/cq/adobeims-configuration/content/configurations.html`

   Par exemple :

   * `https://localhost:4502/libs/cq/adobeims-configuration/content/configurations.html`


1. Sélectionnez votre configuration.
1. Sélectionnez **Contrôle de l’intégrité** dans la barre d’outils, puis **Vérifier**.

   ![Configuration IMS - Contrôle de l’intégrité](assets/integrate-analytics-ims-12.png)

1. En cas de réussite, un message de confirmation s’affiche.

## Fin de l’intégration avec Adobe Analytics {#complete-the-integration-with-adobe-analytics}

Vous pouvez maintenant utiliser cette configuration IMS pour terminer l’[intégration avec Adobe Analytics](/help/sites-cloud/integrating/integrating-adobe-analytics.md).

<!--
## Configuring the Adobe Analytics Cloud Service {#configuring-the-adobe-analytics-cloud-service}

The configuration can now be referenced for a Cloud Service to use the Analytics Standard API:

1. Open the **Tools** menu. Then, within the **Cloud Services** section, select **Legacy Cloud Services**.
1. Scroll down to **Adobe Analytics** and select **Configure now**.

   The **Create Configuration** dialog will open.

1. Enter a **Title** and, if you want, a **Name** (if left blank this will be generated from the title).

   You can also select the required template (if more than one is available).

1. Confirm with **Create**.

   The **Edit Component** dialog will open.

1. Enter the details in the **Analytics Settings** tab:

    * **Authentication**: IMS

    * **IMS Configuration**: select the name of the IMS Configuration

1. Click **Connect to Analytics** to initialize the connection with Adobe Analytics.

   If the connection is successful, the message **Connection successful** is displayed.

1. Select **OK** on the message.

1. Complete other parameters as required, followed by **OK** on the dialog to confirm the configuration.

1. You can now proceed to [Adding an Analytics Framework](/help/sites-administering/adobeanalytics-connect.md) to configure parameters that will be sent to Adobe Analytics. 
-->
