---
title: Utilisation de l’outil de mappage des utilisateurs (hérité)
description: Utilisation de l’outil de mappage des utilisateurs (hérité)
exl-id: dcb750c4-0f81-4d11-ac6c-0592162b683d
hide: true
hidefromtoc: true
feature: Migration
role: Admin
source-git-commit: e5fd1b351047213adbb83ef1d1722352958ce823
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 97%

---


# Utilisation de l’outil de mappage des utilisateurs et utilisatrices (hérité) {#using-user-mapping-tool}

>[!INFO]
>
>Cette documentation fait référence à une version obsolète de l’outil. Pour plus d’informations sur la dernière version, voir [Migration de groupe](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md).

L’outil de mappage des utilisateurs utilise une API pour rechercher les utilisateurs du système Adobe IMS (Identity Management System) par email et renvoyer leur ID IMS. Cette API nécessite que l’utilisateur crée un ID client pour son organisation, un secret client et un jeton d’accès ou de porteur.

## Configuration de l’outil de mappage des utilisateurs {#setting-up-user-mapping}

**Condition requise :** le mappage des utilisateurs et utilisatrices requiert que chaque utilisateur ou utilisatrice à mapper à son identifiant IMS dispose d’une adresse e-mail dans son profil dans AEM et dans IMS. Même si l’utilisateur ou l’utilisatrice utilise une adresse e-mail comme ID pour se connecter, le mappage ne fonctionne pas pour cette personne, sauf si l’adresse e-mail figure également dans le profil, ainsi que dans IMS.

Suivez les étapes ci-dessous pour configurer ces éléments :

1. Accédez à la [Adobe Developer Console](https://developer.adobe.com/console/) à l’aide de votre Adobe ID.
1. Créez un projet ou ouvrez un projet existant.
1. Ajout d’une API – Cliquez sur **Ajouter au projet** et sélectionnez **API**
1. Sélectionnez l’API User Management. Pour que cette option soit disponible, vous devez disposer des autorisations d’administrateur système.
1. Créez des informations d’identification JWT.
1. Générez une paire de clés ou chargez une clé publique (RSA ne convient pas). Un bouton intitulé **Générer une paire de clés publique/privée** vous permettra de créer cette paire de clés. Veillez à enregistrer les deux clés, publique et privée.
1. Accédez à l’API User Management.
1. Générez un jeton d’accès (ou un jeton porteur) en collant le contenu de votre clé privée dans la zone de texte, puis en cliquant sur **Générer un jeton**.
1. Enregistrez en lieu sûr ces informations, notamment l’**ID client**, le **secret client**, l’**ID de compte technique**, l’**adresse électronique du compte technique**, l’**ID d’organisation** et le **jeton d’accès**.

## Accès à l’interface utilisateur de l’outil de mappage des utilisateurs {#user-interface}

L’outil de mappage des utilisateurs est intégré à l’outil de transfert de contenu. Vous pouvez télécharger l’outil de transfert de contenu depuis le [portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). Pour plus d’informations sur la dernière version, consultez les [Notes de mise à jour de la version actuelle](/help/release-notes/release-notes-cloud/release-notes-current.md).

1. Sélectionnez Adobe Experience Manager et accédez à Outils > **Opérations** > **Migration de contenu**.

   ![Image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access1.png)

1. Cliquez sur la carte **Mappage des utilisateurs**.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access2.png)

1. Cliquez sur **Créer une configuration de mappage des utilisateurs**.

   >[!NOTE]
   >Si vous ignorez cette étape, le mappage des utilisateurs, des utilisatrices et des groupes est ignoré au cours de la phase d’extraction.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access5.png)

   Renseignez les champs dans **Configuration de l’API User Management** comme décrit ci-dessous.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access3.png)


   * **ID d’organisation** : saisissez l’ID d’organisation Adobe IMS (Identity Management System) pour l’organisation depuis laquelle migrent les utilisateurs et utilisatrices.

     >[!NOTE]
     >Pour obtenir l’ID d’organisation, connectez-vous à [Admin Console](https://adminconsole.adobe.com/) et choisissez votre organisation (dans la zone supérieure droite) si vous appartenez à plusieurs organisations. L’ID d’organisation se trouve dans l’URL de cette page, au format `xx@AdobeOrg`, où xx correspond à l’ID d’organisation IMS. Vous pouvez également trouver l’ID d’organisation sur la page [Adobe Developer Console](https://developer.adobe.com/console/) où vous générez le jeton d’accès.

   * **ID client** : saisissez l’ID client enregistré à l’étape de configuration.

   * **Jeton d’accès** : saisissez le jeton d’accès enregistré lors de l’étape de configuration.

     >[!NOTE]
     >Le jeton d’accès arrive à expiration toutes les 24 heures et il faut en créer un nouveau. Pour créer un jeton, revenez dans [Adobe Developer Console](https://developer.adobe.com/console/), choisissez votre projet, cliquez sur **API User Management** et collez la même clé privée dans la zone.

1. Une fois les champs renseignés, cliquez sur **Tester la configuration** pour tester la connexion au service de l’API User Management. Si la connexion est établie, vous pouvez cliquer sur **Enregistrer** pour enregistrer la configuration.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access4.png)

1. Après avoir enregistré la configuration, sélectionnez-la et cliquez sur **Démarrer le mappage des utilisateurs**.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-landing4.png)

1. Cliquez sur **Démarrer** dans la boîte de dialogue pour lancer le processus de mappage utilisateur.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   Elle affiche le **Statut** comme étant **EN COURS**.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-start1.png)


1. Une fois le mappage des utilisateurs et utilisatrices terminé, cliquez sur **Résultats** pour afficher le résumé.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-landing5.png)

   >[!IMPORTANT]
   >
   >* Une fois le mappage des utilisateurs et utilisatrices terminé, vous pouvez revenir à la page de Migration du contenu à l’aide du chemin de navigation. La carte Mappage des utilisateurs affiche le statut et l’horodatage. Cliquez sur **Transfert de contenu** afin de pouvoir créer un jeu de migration pour exécuter l’extraction. Pour plus d’informations, consultez [Exécution de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=fr#running-tool).

### Reprise du processus de mappage des utilisateurs {#resume-user-mapping-process}

Si le processus de mappage des utilisateurs est arrêté pour l’une des raisons suivantes :

* L’option **Arrêt du mappage des utilisateurs** a été sélectionnée par l’utilisateur ou utilisatrice.
* Le jeton d’accès a expiré pendant le processus.
* Ou, pour une autre raison.

  >[!NOTE]
  >La progression est enregistrée à partir de l’endroit où le processus s’est arrêté.

Pour reprendre le processus de mappage des utilisateurs, procédez comme suit :

1. Cliquez sur **Afficher le journal** pour consulter le journal de mappage des utilisateurs et utilisatrices afin de vérifier la progression enregistrée.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping1.png)

1. Cliquez sur le bouton **Démarrer le mappage des utilisateurs** pour reprendre à l’endroit où il s’est arrêté.

   >[!NOTE]
   >Assurez-vous, avant de redémarrer, que le jeton d’accès est toujours valide ou qu’il a été actualisé.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping2.png)

1. Cliquez sur **Démarrer** dans la boîte de dialogue pour reprendre le processus de mappage des utilisateurs et utilisatrices.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   Une fois le processus de mappage des utilisateurs et utilisateurs terminé, vous pouvez voir le **Statut** comme étant **TERMINÉ** pour cette configuration spécifique.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping4.png)
