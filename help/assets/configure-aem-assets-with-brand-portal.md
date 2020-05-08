---
title: Configuration du service cloud AEM Assets avec Brand Portal
description: Configurez le service cloud AEM Assets avec Brand Portal.
contentOwner: Vishabh Gupta
translation-type: ht
source-git-commit: bbb3327d4bc7cef8eede3169bc14a1d247ee2bdc

---


# Configuration d’AEM Assets avec Brand Portal {#configure-aem-assets-with-brand-portal}

Adobe Experience Manager (AEM) Assets est configuré avec Brand Portal via Adobe I/O, qui fournit un jeton IMS pour autoriser votre client Brand Portal.

## Conditions préalables {#prerequisites}

Pour configurer AEM Assets avec Brand Portal, vous devez disposer des éléments suivants :

* Une instance cloud AEM Assets en cours d’exécution.
* URL du client Brand Portal
* Un utilisateur disposant de droits d’administrateur système sur l’organisation IMS du client Brand Portal

**Contactez l’assistance** si vous avez d’autres questions.

## Création d’une configuration {#create-new-configuration}

Vous pouvez créer une configuration sur Adobe I/O pour configurer votre instance cloud AEM Assets avec Brand Portal.

Effectuez les étapes suivantes dans leur ordre d’apparition :
1. [Obtention d’un certificat public](#public-certificate)
1. [Création de l’intégration Adobe I/O](#createnewintegration)
1. [Création d’une configuration de compte IMS](#create-ims-account-configuration)
1. [Configuration du service cloud](#configure-the-cloud-service)
1. [Test de la configuration](#test-configuration)

### Création de la configuration IMS {#create-ims-configuration}

La configuration IMS authentifie votre client Brand Portal avec l’instance d’auteur AEM Assets.

La configuration IMS comprend deux étapes :

* [Obtention d’un certificat public](#public-certificate)
* [Création d’une configuration de compte IMS](#create-ims-account-configuration)

### Obtention d’un certificat public {#public-certificate}

Un certificat public permet d’authentifier votre profil sur Adobe I/O.

1. Connectez-vous à votre instance cloud AEM Assets.

1. Dans le panneau **outil** ![Outils](assets/tools.png), accédez à **[!UICONTROL Sécurité]** > **[!UICONTROL Configurations d’Adobe IMS]**.

   ![Interface utilisateur de configuration du compte Adobe IMS](assets/ims-configuration1.png)

1. La page Configurations d’Adobe IMS s’ouvre.

   Cliquez sur **[!UICONTROL Créer]**.

   Vous accédez alors à la page **[!UICONTROL Configuration du compte technique Adobe IMS]**.

1. Par défaut, l’onglet **Certificat** s’ouvre.

   Dans **Solution cloud**, sélectionnez **[!UICONTROL Adobe Brand Portal]**.

1. Cochez la case **[!UICONTROL Créer un certificat]** et spécifiez un **alias** pour le certificat. L’alias sert de nom à la boîte de dialogue.

1. Cliquez sur **[!UICONTROL Créer un certificat]**. Une boîte de dialogue s’affiche. Cliquez sur **[!UICONTROL OK]** pour générer le certificat public.

   ![Création d’un certificat](assets/ims-config2.png)

1. Cliquez sur **[!UICONTROL Télécharger la clé publique]** et enregistrez le fichier de certificat *AEM-Adobe-IMS.crt* sur votre ordinateur. Le fichier de certificat est utilisé pour [créer une intégration Adobe I/O](#createnewintegration).

   ![Téléchargement du certificat](assets/ims-config3.png)

1. Cliquez sur **[!UICONTROL Suivant]**.

   Dans l’onglet **Compte**, vous créez le compte Adobe IMS, mais vous avez pour cela besoin des détails d’intégration. Gardez cette page ouverte pour l’instant.

   Ouvrez un nouvel onglet et [créez une intégration Adobe I/O](#createnewintegration) pour obtenir les détails d’intégration des configurations de compte IMS.

### Création de l’intégration Adobe I/O {#createnewintegration}

L’intégration Adobe I/O génère une clé API, un secret client et une charge utile (JWT), dont vous avez besoin pour configurer les configurations de compte IMS.

1. Connectez-vous à la console Adobe I/O avec les droits d’administrateur système sur l’organisation IMS du client Brand Portal.

   URL par défaut : [https://console.adobe.io/](https://console.adobe.io/)

1. Cliquez sur **[!UICONTROL Créer une intégration]**.

1. Sélectionnez **[!UICONTROL Accéder à une API]**, puis cliquez sur **[!UICONTROL Continuer]**.

   ![Création d’une intégration](assets/create-new-integration1.png)

1. La page Créer une intégration s’affiche.

   Sélectionnez votre entreprise dans la liste déroulante.

   Dans **[!UICONTROL Experience Cloud]**, sélectionnez **[!UICONTROL AEM Brand Portal]** et cliquez sur **[!UICONTROL Continuer]**.

   Si l’option Brand Portal est désactivée, assurez-vous d’avoir sélectionné la bonne entreprise dans la liste déroulante au-dessus de l’option **[!UICONTROL Adobe Services]** (Services Adobe). Si vous ne connaissez pas le nom de votre entreprise, contactez votre administrateur.

   ![Création d’une intégration](assets/create-new-integration2.png)

1. Spécifiez le nom et la description de l’intégration. Cliquez sur **[!UICONTROL Select a File from your computer]** (Sélectionner un fichier sur votre ordinateur) et téléchargez le fichier `AEM-Adobe-IMS.crt` téléchargé dans la section [obtenir des certificats publics](#public-certificate).

1. Sélectionnez le profil de votre entreprise.

   Ou sélectionnez le profil **[!UICONTROL Assets Brand Portal]** par défaut et cliquez sur **[!UICONTROL Créer une intégration]**. L’intégration est créée.

1. Appuyez sur **[!UICONTROL Continue to integration details]** (Continuer vers les détails d’intégration) pour afficher les informations d’intégration.

   Copiez la **[!UICONTROL clé API]**.

   Cliquez sur **[!UICONTROL Retrieve Client Secret]** (Récupérer le secret client) et copiez la clé secrète client.

   ![Clé API, secret client et informations de charge utile d’une intégration](assets/create-new-integration3.png)

1. Accédez à l’onglet **[!UICONTROL JWT]** et copiez la **[!UICONTROL charge JWT]**.

   Les informations de clé API, de clé secrète client et de charge utile JWT seront utilisées pour créer la configuration du compte IMS.

### Création d’une configuration de compte IMS {#create-ims-account-configuration}

Vérifiez que vous avez effectué les étapes suivantes :

* [Obtention d’un certificat public](#public-certificate)
* [Création de l’intégration Adobe I/O](#createnewintegration)

**Procédure de création de la configuration du compte IMS :**

1. Ouvrez la page Configuration IMS de l’onglet **[!UICONTROL Comptes]**. Vous avez gardé la page ouverte à la fin de la section [Obtention d’un certificat public](#public-certificate).

1. Spécifiez un **[!UICONTROL titre]** pour le compte IMS.

   Dans **[!UICONTROL Serveur d’autorisation]**, entrez l’adresse URL : [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)

   Collez la clé API, le secret client et la charge utile JWT que vous avez copiés à la fin de [Création de l’intégration Adobe I/O](#createnewintegration).

   Cliquez sur **[!UICONTROL Créer]**.

   L’intégration est créée.

   ![Configuration du compte IMS](assets/create-new-integration6.png)


1. Sélectionnez la configuration IMS et cliquez sur **[!UICONTROL Contrôle de l’intégrité]**. Une boîte de dialogue s’affiche.

   Cliquez sur **[!UICONTROL Vérifier]**. Une fois la connexion établie, le message *Jeton récupéré avec succès* s’affiche.

   ![](assets/create-new-integration5.png)

>[!CAUTION]
>
>Vous ne devez avoir qu’une seule configuration IMS. N’en créez pas plusieurs.
>
>Assurez-vous que la configuration IMS réussit le contrôle d’intégrité. Si tel n’est pas le cas, elle n’est pas valide. Vous devez la supprimer et créer une configuration valide.



### Configuration du service cloud {#configure-the-cloud-service}

Pour créer une configuration de service cloud Brand Portal, procédez comme suit :

1. Connectez-vous à votre instance cloud AEM Assets.

1. Dans le panneau **outil** ![Outils](assets/tools.png), accédez à **[!UICONTROL Services cloud]** > **[!UICONTROL AEM Brand Portal]**.

   La page Configurations de Brand Portal s’affiche.

1. Cliquez sur **[!UICONTROL Créer]**.

1. Saisissez un **[!UICONTROL titre]** pour la configuration.

   Sélectionnez la configuration IMS que vous avez créée à l’étape [Création d’une configuration de compte IMS](#create-ims-account-configuration).

   Dans **[!UICONTROL URL du service]**, entrez votre URL du client Brand Portal.

   ![](assets/create-cloud-service.png)

1. Cliquez sur **[!UICONTROL Enregistrer et fermer]**. La configuration cloud est alors créée. Votre instance cloud AEM Assets est maintenant configurée avec le client Brand Portal.

### Test de la configuration {#test-configuration}

1. Connectez-vous à votre instance cloud AEM Assets.

1. Dans le panneau **outil** ![Outils](assets/tools.png), accédez à **[!UICONTROL Déploiement]** > **[!UICONTROL Distribution]**.

   ![](assets/test-bpconfig1.png)

1. La page Distribution s’ouvre.

   Un agent de distribution Brand Portal `bpdistributionagent0` est créé sous **[!UICONTROL Publier sur Brand Portal]**.

   Cliquez sur **[!UICONTROL Publier sur Brand Portal]**.

   ![](assets/test-bpconfig2.png)

   >[!NOTE]
   >
   >Par défaut, un agent de distribution est créé pour un client Brand Portal.

1. La page de l’agent de distribution s’ouvre. Par défaut, l’onglet **[!UICONTROL État]** s’ouvre, et les files d’attente de distribution sont alors renseignées.

   Un agent de distribution contient deux files d’attente :
   * **processing-queue** : pour la distribution des ressources de Brand Portal.

   * **error-queue** : pour les ressources dont la distribution a échoué.
   >[!NOTE]
   >
   >Il est recommandé d’examiner les erreurs et d’effacer régulièrement la file d’attente **error-queue**.

   ![](assets/test-bpconfig3.png)

1. Pour vérifier la connexion entre AEM Assets et Brand Portal, cliquez sur **[!UICONTROL Tester la connexion]**.

   ![](assets/test-bpconfig4.png)

   Un message s’affiche en bas de la page pour indiquer que votre package de test a été livré.

   >[!NOTE]
   >
   >Évitez de désactiver l’agent de distribution, car cela peut entraîner l’échec de la distribution des ressources (running-in-queue).


Votre instance cloud AEM Assets est correctement configurée avec Brand Portal, et vous pouvez à présent effectuer les actions suivantes :

* [Publication de ressources à partir d’AEM Assets sur Brand Portal](publish-to-brand-portal.md)
* [Publication de dossiers à partir d’AEM Assets sur Brand Portal](publish-to-brand-portal.md#publish-folders-to-brand-portal)
* [Publication de collections à partir d’AEM Assets sur Brand Portal](publish-to-brand-portal.md#publish-collections-to-brand-portal)

Outre ce qui précède, vous pouvez également publier des schémas de métadonnées, des paramètres d’image prédéfinis, des facettes de recherche et des balises d’AEM Assets sur Brand Portal.

* [Publication de paramètres prédéfinis, de schémas et de facettes sur Brand Portal](https://docs.adobe.com/content/help/fr-FR/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html)
* [Publication de balises sur Brand Portal](https://docs.adobe.com/content/help/fr-FR/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html)


Pour plus d’informations, voir [Publication de balises sur Brand Portal](https://docs.adobe.com/content/help/fr-FR/experience-manager-brand-portal/using/home.html).


## Journaux de distribution {#distribution-logs}

Vous pouvez consulter les journaux pour obtenir des informations détaillées sur les actions effectuées sur l’agent de distribution.

Par exemple, nous avons publié une ressource d’AEM Assets sur Brand Portal pour vérifier la configuration.

1. Suivez les étapes (1 à 4), comme indiqué dans **[!UICONTROL Test de la connexion]**, puis accédez à la page de l’agent de distribution.

1. Cliquez sur **[!UICONTROL Journaux]** pour afficher les journaux de distribution. Vous pouvez afficher les journaux de traitement et d’erreur ici.

   ![](assets/test-bpconfig5.png)

L’agent de distribution génère les journaux suivants :

* INFO : Il s’agit d’un journal généré par le système qui se déclenche lors d’une configuration réussie activant l’agent de distribution.
* DSTRQ1 (requête 1) : Déclencheurs lors du test de la connexion.

Lors de la publication de la ressource, les journaux de requête et de réponse suivants sont générés :

**Requête de l’agent de distribution** :
* DSTRQ2 (requête 2) : La requête de publication de ressource est déclenchée.
* DSTRQ3 (requête 3) : Le système déclenche une autre requête pour publier le dossier dans lequel se trouve la ressource et réplique le dossier dans Brand Portal.

**Réponse de l’agent de distribution** :
* queue-bpdistributionagent0 (DSTRQ2) : La ressource est publiée sur Brand Portal.
* queue-bpdistributionagent0 (DSTRQ3) : Le système réplique le dossier contenant la ressource dans Brand Portal.

Dans l’exemple ci-dessus, une requête et une réponse supplémentaires sont déclenchées. Le système n’a pas trouvé le dossier parent (alias Ajouter chemin d’accès) dans Brand Portal, car la ressource a été publiée pour la première fois. Par conséquent, il déclenche une requête supplémentaire pour créer un dossier parent portant le même nom dans Brand Portal à l’emplacement où la ressource est publiée.

>[!NOTE]
>
>Une requête supplémentaire est générée au cas où le dossier parent n’existerait pas dans Brand Portal (dans l’exemple ci-dessus) ou si le dossier parent a été modifié dans AEM Assets.



<!--

## Additional information {#additional-information}

Go to `/system/console/slingmetrics` for statistics related to the distributed content:

1. **Counter metrics**
   * sling: `mac_sync_request_failure`
   * sling: `mac_sync_request_received`
   * sling: `mac_sync_request_success`

1. **Time metrics**
   * sling: `mac_sync_distribution_duration`
   * sling: `mac_sync_enqueue_package_duration`
   * sling: `mac_sync_setup_request_duration`

-->

<!--
   Comment Type: draft

   <li> </li>
   -->

<!--
   Comment Type: draft

   <li>Step text</li>
   -->
