---
title: Utilisation de l’outil de mappage des utilisateurs
description: Utilisation de l’outil de mappage des utilisateurs
source-git-commit: bcbf4e4ba1330bef9f2c8c473419903e40ac0e58
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 50%

---


# Utilisation de l’outil de mappage des utilisateurs {#using-user-mapping-tool}

L’outil de mappage des utilisateurs utilise une API pour rechercher les utilisateurs du système Adobe IMS (Identity Management System) par email et renvoyer leur ID IMS. Cette API nécessite que l’utilisateur crée un ID client pour son organisation, un secret client et un jeton d’accès ou de porteur.

## Configuration de l’outil de mappage des utilisateurs {#setting-up-user-mapping}

Suivez les étapes ci-dessous pour configurer ces éléments :

1. Accédez à la [Adobe Developer Console](https://console.adobe.io) à l’aide de votre Adobe ID.
1. Créez un projet ou ouvrez un formulaire existant.
1. Ajout d’une API - Cliquez sur **Ajouter au projet** et sélectionnez **API**
1. Sélectionnez l’API Gestion des utilisateurs.  Vous devrez peut-être obtenir des autorisations pour disposer de cette option.
1. Créez des informations d’identification JWT.
1. Générez une paire de clés ou chargez une clé publique (RSA ne convient pas).  Il y a un bouton, **Génération d’une paire de clés publique/privée**, qui le fera pour vous.  Veillez à enregistrer les clés publique et privée.
1. Accédez à l’API User Management.
1. Générez un jeton d’accès (ou un jeton porteur) en collant le contenu de votre clé privée dans la zone de texte, puis en cliquant sur **Générer un jeton**.
1. Enregistrez en lieu sûr ces informations, notamment l’**ID client**, le **secret client**, l’**ID de compte technique**, l’**adresse électronique du compte technique**, l’**ID d’organisation** et le **jeton d’accès**.

## Accès à l’interface utilisateur de l’outil de mappage utilisateur {#user-interface}

L’outil de mappage des utilisateurs est intégré à l’outil de transfert de contenu. Vous pouvez télécharger l’outil de transfert de contenu depuis le [portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). Pour plus d’informations sur la dernière version, consultez les [Notes de mise à jour actuelles](/help/release-notes/release-notes-cloud/release-notes-current.md).

1. Sélectionnez Adobe Experience Manager et accédez à Outils -> **Opérations** -> **Migration de contenu**.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access1.png)

1. Cliquez sur **Mappage utilisateur** carte.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access2.png)

1. Cliquez sur **Créer une configuration de mappage des utilisateurs**.

   >[!NOTE]
   >Si vous ignorez cette étape, le mappage des utilisateurs et des groupes sera ignoré au cours de la phase d’extraction.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access5.png)

   Renseignez les champs de la section **Configuration de l’API User Management**, comme décrit ci-dessous.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access3.png)


   * **ID d’organisation** : saisissez l’ID d’organisation Adobe IMS (Identity Management System) pour l’organisation depuis laquelle migrent les utilisateurs.

      >[!NOTE]
      >Pour obtenir l’ID d’organisation, connectez-vous à l’[Admin Console](https://adminconsole.adobe.com/) et choisissez votre organisation (dans la zone supérieure droite) si vous appartenez à plusieurs. L’ID d’organisation se trouve dans l’URL de cette page, au format `xx@AdobeOrg`, où xx correspond à l’ID d’organisation IMS.  Vous pouvez également trouver l’ID d’organisation sur la page [Adobe Developer Console](https://console.adobe.io) où vous générez le jeton d’accès.

   * **ID client** : saisissez l’ID client enregistré à l’étape de configuration.

   * **Jeton d’accès** : saisissez le jeton d’accès enregistré lors de l’étape de configuration.

      >[!NOTE]
      >Le jeton d’accès arrive à expiration toutes les 24 heures et il faut en créer un nouveau. Pour créer un jeton, revenez dans [Adobe Developer Console](https://console.adobe.io), choisissez votre projet, cliquez sur **User Management API** (API Gestion des utilisateurs) et collez la même clé privée dans la zone.

1. Une fois les champs renseignés, cliquez sur **Test Configuration** pour tester la connexion au service d’API User Management. Si la connexion est établie, vous pouvez cliquer sur **Enregistrer** pour enregistrer la configuration.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access4.png)

1. Après avoir enregistré la configuration, sélectionnez-la et cliquez sur **Mappage de l’utilisateur de démarrage**.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-landing4.png)

1. Cliquez sur **Début** dans la boîte de dialogue pour lancer le processus de mappage utilisateur.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   Il affiche la variable **État** as **EN COURS**.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-start1.png)


1. Une fois le mappage des utilisateurs terminé, cliquez sur **Résultats** pour afficher le résumé.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-landing5.png)

   >[!IMPORTANT]
   >* Une fois le mappage des utilisateurs terminé, vous pouvez revenir à la page Migration du contenu à l’aide du chemin de navigation. La carte Mappage de l’utilisateur affiche l’état et l’horodatage. Cliquez sur **Transfert de contenu** pour créer un jeu de migration pour exécuter l’extraction. Voir [Exécution de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#running-tool) pour plus d’informations.


### Reprise du processus de mappage utilisateur {#resume-user-mapping-process}

Si le processus de mappage des utilisateurs est arrêté pour l’une des raisons suivantes :

* L’utilisateur sélectionné **Arrêt du mappage des utilisateurs**
* le jeton d&#39;accès expiré pendant le processus ou,
* une autre raison

   >[!NOTE]
   >La progression est enregistrée à partir de l’endroit où le processus s’est arrêté.

Pour reprendre le processus de mappage des utilisateurs, procédez comme suit :

1. Cliquez sur **Afficher le journal** pour consulter le journal de mappage des utilisateurs afin de vérifier la progression enregistrée.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping1.png)

1. Cliquez sur le bouton **Mappage de l’utilisateur de démarrage** pour reprendre à l’endroit où il s’est arrêté.

   >[!NOTE]
   >Assurez-vous, avant de redémarrer, que le jeton d’accès est toujours valide ou a été actualisé.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping2.png)

1. Cliquez sur **Début** dans la boîte de dialogue pour reprendre le processus de mappage utilisateur.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   Une fois le processus de mappage des utilisateurs terminé, vous verrez le **État** as **FINISHED** pour cette configuration spécifique.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping4.png)
