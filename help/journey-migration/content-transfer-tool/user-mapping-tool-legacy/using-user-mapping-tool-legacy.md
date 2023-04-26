---
title: Utilisation de l’outil de mappage des utilisateurs (hérité)
description: Utilisation de l’outil de mappage des utilisateurs (hérité)
exl-id: dcb750c4-0f81-4d11-ac6c-0592162b683d
hide: true
hidefromtoc: true
source-git-commit: 8a258c2c929f9af84a1cde99072291a3e7f6cfc3
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 87%

---

# Utilisation de l’outil de mappage des utilisateurs (hérité) {#using-user-mapping-tool}

>[!INFO]
>
>Cette documentation fait référence à une version obsolète de l’outil. Pour plus d’informations sur la dernière version, voir [Mappage des utilisateurs et migration des entités de sécurité](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md).

L’outil de mappage des utilisateurs utilise une API pour rechercher les utilisateurs du système Adobe IMS (Identity Management System) par email et renvoyer leur ID IMS. Cette API nécessite que l’utilisateur crée un ID client pour son organisation, un secret client et un jeton d’accès ou de porteur.

## Configuration de l’outil de mappage des utilisateurs {#setting-up-user-mapping}

**Condition requise :** Le mappage des utilisateurs requiert que chaque utilisateur soit mappé à son identifiant IMS avec une adresse email dans son profil dans AEM et dans IMS.  Notez que même si l’utilisateur utilise une adresse électronique comme ID utilisateur pour se connecter, le mappage ne fonctionne pas pour cet utilisateur, sauf si l’adresse électronique figure également dans le profil, ainsi que dans IMS.

Suivez les étapes ci-dessous pour configurer ces éléments :

1. Accédez à la [Adobe Developer Console](https://console.adobe.io) à l’aide de votre Adobe ID.
1. Créez un projet ou ouvrez un formulaire existant.
1. Ajout d’une API – Cliquez sur **Ajouter au projet** et sélectionnez **API**.
1. Sélectionnez l’API User Management. Pour que cette option soit disponible, vous devez disposer des autorisations d’administrateur système.
1. Créez des informations d’identification JWT.
1. Générez une paire de clés ou chargez une clé publique (RSA ne convient pas). Un bouton intitulé **Générer une paire de clés publique/privée** le fera pour vous. Veillez à enregistrer les deux clés, publique et privée.
1. Accédez à l’API User Management.
1. Générez un jeton d’accès (ou un jeton au porteur) en collant le contenu de votre clé privée dans la zone de texte, puis en cliquant sur **Générer un jeton**.
1. Enregistrez en lieu sûr ces informations, notamment l’**ID client**, le **secret client**, l’**ID de compte technique**, l’**adresse électronique du compte technique**, l’**ID d’organisation** et le **jeton d’accès**.

## Accès à l’interface utilisateur de l’outil de mappage des utilisateurs {#user-interface}

L’outil de mappage des utilisateurs est intégré à l’outil de transfert de contenu. Vous pouvez télécharger l’outil de transfert de contenu depuis le [portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). Pour plus d’informations sur la dernière version, consultez les [Notes de mise à jour actuelles](/help/release-notes/release-notes-cloud/release-notes-current.md).

1. Sélectionnez Adobe Experience Manager et accédez à Outils -> **Opérations** -> **Migration de contenu**.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access1.png)

1. Cliquez sur la carte **Mappage des utilisateurs**.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access2.png)

1. Cliquez sur **Créer une configuration de mappage des utilisateurs**.

   >[!NOTE]
   >Si vous ignorez cette étape, le mappage des utilisateurs et des groupes sera ignoré au cours de la phase d’extraction.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access5.png)

   Renseignez les champs dans **Configuration de l’API User Management** comme décrit ci-dessous. 

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access3.png)


   * **ID d’organisation** : saisissez l’ID d’organisation Adobe IMS (Identity Management System) pour l’organisation depuis laquelle migrent les utilisateurs.

      >[!NOTE]
      >Pour obtenir l’ID d’organisation, connectez-vous à l’[Admin Console](https://adminconsole.adobe.com/) et choisissez votre organisation (dans la zone supérieure droite) si vous appartenez à plusieurs. L’ID d’organisation se trouve dans l’URL de cette page, au format `xx@AdobeOrg`, où xx correspond à l’ID d’organisation IMS. Vous pouvez également trouver l’ID d’organisation sur la page [Adobe Developer Console](https://console.adobe.io) où vous générez le jeton d’accès.

   * **ID client** : saisissez l’ID client enregistré à l’étape de configuration.

   * **Jeton d’accès** : saisissez le jeton d’accès enregistré lors de l’étape de configuration.

      >[!NOTE]
      >Le jeton d’accès arrive à expiration toutes les 24 heures et il faut en créer un nouveau. Pour créer un jeton, revenez dans [Adobe Developer Console](https://console.adobe.io), choisissez votre projet, cliquez sur **User Management API** (API User Management) et collez la même clé privée dans la zone.

1. Une fois les champs renseignés, cliquez sur **Configuration du test** pour tester la connexion au service de l’API User Management. Si la connexion est établie, vous pourrez cliquer sur **Enregistrer** pour sauvegarder la configuration.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access4.png)

1. Après avoir enregistré la configuration, sélectionnez-la et cliquez sur **Démarrer le mappage des utilisateurs**.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-landing4.png)

1. Cliquez sur **Démarrer** dans la boîte de dialogue pour lancer le processus de mappage des utilisateurs.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   Elle affiche le **Statut** comme étant **EN COURS**.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-start1.png)


1. Une fois le mappage des utilisateurs terminé, cliquez sur **Résultats** pour afficher le résumé.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-landing5.png)

   >[!IMPORTANT]
   >* Une fois le mappage des utilisateurs terminé, vous pouvez revenir à la page de Migration du contenu à l’aide du chemin de navigation. La carte Mappage des utilisateurs affiche le statut et l’horodatage. Cliquez sur **Transfert de contenu** pour créer un jeu de migration pour exécuter l’extraction. Pour plus d’informations, consultez [Exécution de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=fr#running-tool).


### Reprise du processus de mappage des utilisateurs {#resume-user-mapping-process}

Si le processus de mappage des utilisateurs est arrêté pour l’une des raisons suivantes :

* L’utilisateur a sélectionné **Arrêter le mappage des utilisateurs**
* le jeton d’accès a expiré pendant le processus ou
* une autre raison

   >[!NOTE]
   >La progression est enregistrée à partir de l’endroit où le processus s’est arrêté.

Pour reprendre le processus de mappage des utilisateurs, procédez comme suit :

1. Cliquez sur **Afficher le journal** pour consulter le journal de mappage des utilisateurs afin de vérifier la progression enregistrée.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping1.png)

1. Cliquez sur le bouton **Démarrer le mappage des utilisateurs** pour reprendre à l’endroit où il s’est arrêté.

   >[!NOTE]
   >Assurez-vous, avant de redémarrer, que le jeton d’accès est toujours valide ou qu’il a été actualisé.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping2.png)

1. Cliquez sur **Démarrer** dans la boîte de dialogue pour reprendre le processus de mappage des utilisateurs.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   Une fois le processus de mappage des utilisateurs terminé, vous verrez le **Statut** comme étant **TERMINÉ** pour cette configuration spécifique.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping4.png)
