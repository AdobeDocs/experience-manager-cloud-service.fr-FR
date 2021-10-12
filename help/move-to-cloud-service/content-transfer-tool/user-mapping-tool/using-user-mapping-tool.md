---
title: Utilisation de l’outil de mappage des utilisateurs
description: Utilisation de l’outil de mappage des utilisateurs
source-git-commit: 32220016fbe8c0ac0f906e62098398d4508af4cd
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 51%

---


# Utilisation de l’outil de mappage des utilisateurs {#using-user-mapping-tool}

L’outil de mappage des utilisateurs utilise une API pour rechercher les utilisateurs du système Adobe IMS (Identity Management System) par email et renvoyer leur ID IMS. Cette API nécessite que l’utilisateur crée un ID client pour son organisation, un secret client et un jeton d’accès ou de porteur.

## Configuration de l’outil de mappage des utilisateurs {#setting-up-user-mapping}

Suivez les étapes ci-dessous pour configurer ces éléments :

1. Accédez à la [Adobe Developer Console](https://console.adobe.io) à l’aide de votre Adobe ID.
1. Créez un projet ou ouvrez un formulaire existant.
1. Add an API - Click **Add to Project** and select **API**
1. Sélectionnez l’API Gestion des utilisateurs.  Vous devrez peut-être obtenir des autorisations pour disposer de cette option.
1. Créez des informations d’identification JWT.
1. Générez une paire de clés ou chargez une clé publique (RSA ne convient pas).  Il existe un bouton, **Générer une paire de clés publique/privée**, qui vous permet de le faire.  Veillez à enregistrer les clés publique et privée.
1. Navigate to the User Management API.
1. Générez un jeton d’accès (ou jeton porteur) en collant votre contenu de clé privée dans la zone de texte et en cliquant sur **Générer un jeton**.
1. Enregistrez en lieu sûr ces informations, notamment l’**ID client**, le **secret client**, l’**ID de compte technique**, l’**adresse électronique du compte technique**, l’**ID d’organisation** et le **jeton d’accès**.

## Accès à l’interface utilisateur de l’outil de mappage utilisateur {#user-interface}

L’outil de mappage des utilisateurs est intégré à l’outil de transfert de contenu. Vous pouvez télécharger l’outil de transfert de contenu depuis le [portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). Pour plus d’informations sur la dernière version, consultez les [Notes de mise à jour actuelles](/help/release-notes/release-notes-cloud/release-notes-current.md).

1. Sélectionnez Adobe Experience Manager et accédez à Outils -> **Opérations** -> **Migration de contenu**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-access1.png)

1. Cliquez sur la carte **Mappage de l’utilisateur** .

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-access2.png)

1. Cliquez sur **Créer une configuration de mappage des utilisateurs**.

   >[!NOTE]
   >Si vous ignorez cette étape, le mappage des utilisateurs et des groupes sera ignoré au cours de la phase d’extraction.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-access5.png)

   Populate the fields in **User Management API Configuration**, as described below.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-access3.png)


   * **ID d’organisation** : saisissez l’ID d’organisation Adobe IMS (Identity Management System) pour l’organisation depuis laquelle migrent les utilisateurs.

      >[!NOTE]
      >Pour obtenir l’ID d’organisation, connectez-vous à l’[Admin Console](https://adminconsole.adobe.com/) et choisissez votre organisation (dans la zone supérieure droite) si vous appartenez à plusieurs. L’ID d’organisation se trouve dans l’URL de cette page, au format `xx@AdobeOrg`, où xx correspond à l’ID d’organisation IMS.  Vous pouvez également trouver l’ID d’organisation sur la page [Adobe Developer Console](https://console.adobe.io) où vous générez le jeton d’accès.

   * **ID client** : saisissez l’ID client enregistré à l’étape de configuration.

   * **Jeton d’accès** : saisissez le jeton d’accès enregistré lors de l’étape de configuration.

      >[!NOTE]
      >Le jeton d’accès arrive à expiration toutes les 24 heures et il faut en créer un nouveau. Pour créer un jeton, revenez dans [Adobe Developer Console](https://console.adobe.io), choisissez votre projet, cliquez sur **User Management API** (API Gestion des utilisateurs) et collez la même clé privée dans la zone.

1. After populating the fields, click on **Test Configuration** to test the connection to the User Management API service. Si la connexion est établie, vous pourrez cliquer sur **Enregistrer** pour enregistrer la configuration.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-access4.png)

1. Après avoir enregistré la configuration, sélectionnez-la et cliquez sur **Démarrer le mapping utilisateur**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-landing4.png)

1. Cliquez sur **Démarrer** dans la boîte de dialogue pour lancer le processus de mappage utilisateur.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   It displays the **Status** as **RUNNING**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-start1.png)


1. Once User Mapping is complete, click on **Results** to view the summary.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-landing5.png)

   >[!IMPORTANT]
   >* Une fois le mappage des utilisateurs terminé, vous pouvez revenir à la page Migration du contenu à l’aide du chemin de navigation. The User Mapping card displays the status and timestamp. Cliquez sur **Transfert de contenu** pour créer un jeu de migration pour exécuter l’extraction. Refer to [Running the Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#running-tool) for more details.


### Reprise du processus de mappage utilisateur {#resume-user-mapping-process}

If the User Mapping process is stopped due to any of the following reasons:

* L’utilisateur a sélectionné **Arrêter le mappage des utilisateurs**
* the access token expired during the process or,
* une autre raison

   >[!NOTE]
   >The progress is saved from where the process stopped.

Follow the steps below to resume the User mapping process:

1. Cliquez sur **Afficher le journal** pour consulter le journal de mappage des utilisateurs afin de vérifier la progression enregistrée.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/resume-user-mapping1.png)

1. Cliquez à nouveau sur le bouton **Commencer le mappage de l’utilisateur** pour reprendre à l’endroit où il s’est arrêté.

   >[!NOTE]
   >Ensure before restarting that the access token is still valid or has been refreshed.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/resume-user-mapping2.png)

1. Click on **Start** from the the dialog box to resume the User Mapping process.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)
