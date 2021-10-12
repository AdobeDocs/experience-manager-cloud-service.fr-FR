---
title: Utilisation de l’outil de mappage des utilisateurs
description: Utilisation de l’outil de mappage des utilisateurs
source-git-commit: 6ab32a952a53eed612192ee8359373087e6cf624
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 55%

---


# Utilisation de l’outil de mappage des utilisateurs {#using-user-mapping-tool}

L’outil de mappage des utilisateurs utilise une API pour rechercher les utilisateurs du système Adobe IMS (Identity Management System) par email et renvoyer leur ID IMS. Cette API nécessite que l’utilisateur crée un ID client pour son organisation, un secret client et un jeton d’accès ou de porteur.

## Configuration de l’outil de mappage des utilisateurs {#setting-up-user-mapping}

Suivez les étapes ci-dessous pour configurer ces éléments :

1. Accédez à la [Adobe Developer Console](https://console.adobe.io) à l’aide de votre Adobe ID.
1. Créez un projet ou ouvrez un formulaire existant.
1. Ajouter une API - Cliquez sur **Ajouter au projet** et sélectionnez **API**
1. Sélectionnez l’API Gestion des utilisateurs.  Vous devrez peut-être obtenir des autorisations pour disposer de cette option.
1. Créez des informations d’identification JWT.
1. Générez une paire de clés ou chargez une clé publique (RSA ne convient pas).  There is a button, **Generate a public/private keypair**, which will do this for you.  Make sure you save both the public and private keys.
1. Accédez à l’API User Management.
1. Générez un jeton d’accès (ou jeton porteur) en collant votre contenu de clé privée dans la zone de texte et en cliquant sur **Générer un jeton**.
1. Enregistrez en lieu sûr ces informations, notamment l’**ID client**, le **secret client**, l’**ID de compte technique**, l’**adresse électronique du compte technique**, l’**ID d’organisation** et le **jeton d’accès**.

## Accessing the User Interface for User Mapping Tool {#user-interface}

L’outil de mappage des utilisateurs est intégré à l’outil de transfert de contenu. Vous pouvez télécharger l’outil de transfert de contenu depuis le [portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). Pour plus d’informations sur la dernière version, consultez les [Notes de mise à jour actuelles](/help/release-notes/release-notes-cloud/release-notes-current.md).

1. Sélectionnez Adobe Experience Manager et accédez à Outils -> **Opérations** -> **Migration de contenu**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-access1.png)

1. Click on **User Mapping** card.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-access2.png)

1. Cliquez sur **Créer une configuration de mappage des utilisateurs**.

   >[!NOTE]
   >Si vous ignorez cette étape, le mappage des utilisateurs et des groupes sera ignoré au cours de la phase d’extraction.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-access5.png)

   Renseignez les champs de **Configuration de l’API User Management**, comme décrit ci-dessous.

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

1. Une fois le mappage utilisateur terminé, cliquez sur **Résultats** pour afficher le résumé.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-landing5.png)

   >[!IMPORTANT]
   >* Une fois le mappage des utilisateurs terminé, vous pouvez revenir à la page Migration du contenu à l’aide du chemin de navigation. The User Mapping card displays the status and timestamp. Click on **Content Transfer** to create a migration Set to run extraction. Pour plus d’informations, voir [Exécution de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#running-tool) .


### Reprise du processus de mappage utilisateur {#resume-user-mapping}

Si le processus de mappage des utilisateurs est arrêté pour l’une des raisons suivantes :

* L’utilisateur a sélectionné **Arrêter le mappage des utilisateurs**
* le jeton d&#39;accès expiré pendant le processus ou,
* une autre raison.

La progression est enregistrée à partir de l’endroit où le processus s’est arrêté. Review the User Mapping log to check the saved progress. Cliquez à nouveau sur le bouton **Commencer le mappage de l’utilisateur** pour reprendre à l’endroit où il s’est arrêté. Assurez-vous, avant de redémarrer, que le jeton d’accès est toujours valide ou a été actualisé.
