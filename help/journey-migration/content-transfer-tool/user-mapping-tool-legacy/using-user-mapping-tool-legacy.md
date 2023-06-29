---
title: Utilisation de l’outil de mappage des utilisateurs (hérité)
description: Utilisation de l’outil de mappage des utilisateurs (hérité)
exl-id: dcb750c4-0f81-4d11-ac6c-0592162b683d
hide: true
hidefromtoc: true
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 46%

---

# Utilisation de l’outil de mappage des utilisateurs (hérité) {#using-user-mapping-tool}

>[!INFO]
>
>Cette documentation fait référence à une version obsolète de l’outil. Pour plus d’informations sur la dernière version, voir [Mappage des utilisateurs et migration des entités de sécurité](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md).

L’outil de mappage des utilisateurs utilise une API pour rechercher les utilisateurs du système Adobe IMS (Identity Management System) par email et renvoyer leur ID IMS. Cette API nécessite que l’utilisateur crée un ID client pour son organisation, un secret client et un jeton d’accès ou de porteur.

## Configuration de l’outil de mappage des utilisateurs {#setting-up-user-mapping}

**Condition requise :** le mappage des utilisateurs et utilisatrices requiert que chaque utilisateur ou utilisatrice à mapper à son identifiant IMS dispose d’une adresse e-mail dans son profil dans AEM et dans IMS. Même si l’utilisateur utilise une adresse électronique comme ID utilisateur pour se connecter, le mappage ne fonctionne pas pour cet utilisateur, sauf si l’adresse électronique figure également dans le profil et également dans IMS.

Suivez les étapes ci-dessous pour configurer ces éléments :

1. Accédez à la [Adobe Developer Console](https://developer.adobe.com/console/) à l’aide de votre Adobe ID.
1. Créez un projet ou ouvrez un projet existant.
1. Ajout d’une API – Cliquez sur **Ajouter au projet** et sélectionnez **API**.
1. Sélectionnez l’API User Management. Pour que cette option soit disponible, vous devez disposer des autorisations d’administrateur système.
1. Créez des informations d’identification JWT.
1. Générez une paire de clés ou chargez une clé publique (RSA ne convient pas). Il y a un bouton, **Génération d’une paire de clés publique/privée** qui crée cette paire de clés pour vous. Veillez à enregistrer les deux clés, publique et privée.
1. Accédez à l’API User Management.
1. Générez un jeton d’accès (ou jeton porteur) en collant le contenu de votre clé privée dans la zone de texte, puis en cliquant sur **Générer un jeton**.
1. Enregistrez en lieu sûr ces informations, notamment l’**ID client**, le **secret client**, l’**ID de compte technique**, l’**adresse électronique du compte technique**, l’**ID d’organisation** et le **jeton d’accès**.

## Accès à l’interface utilisateur de l’outil de mappage des utilisateurs {#user-interface}

L’outil de mappage des utilisateurs est intégré à l’outil de transfert de contenu. Vous pouvez télécharger l’outil de transfert de contenu depuis le [portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). Pour plus d’informations sur la dernière version, voir [Notes de mise à jour actuelles](/help/release-notes/release-notes-cloud/release-notes-current.md).

1. Sélectionnez Adobe Experience Manager et accédez à Outils -> **Opérations** -> **Migration de contenu**.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access1.png)

1. Cliquez sur le bouton **Mappage utilisateur** carte.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access2.png)

1. Cliquez sur **Création d’une configuration de mappage utilisateur**.

   >[!NOTE]
   >Si vous ignorez cette étape, le mappage des utilisateurs et des groupes est ignoré pendant la phase d’extraction.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access5.png)

   Renseignez les champs dans **Configuration de l’API User Management** comme décrit ci-dessous.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access3.png)


   * **ID d’organisation**: Saisissez l’identifiant de l’organisation Adobe Identity Management System (IMS) pour l’organisation pour laquelle les utilisateurs sont migrés.

     >[!NOTE]
     >Pour obtenir l’ID d’organisation, connectez-vous au [Admin Console](https://adminconsole.adobe.com/) et sélectionnez votre organisation (dans la zone supérieure droite) si vous appartenez à plusieurs organisations. L’ID d’organisation se trouve dans l’URL de cette page, au format suivant : `xx@AdobeOrg`, où xx est l’identifiant de l’organisation IMS. Vous pouvez également trouver l’ID d’organisation sur la page [Adobe Developer Console](https://developer.adobe.com/console/) où vous générez le jeton d’accès.

   * **ID client** : saisissez l’ID client enregistré à l’étape de configuration.

   * **Jeton d’accès** : saisissez le jeton d’accès enregistré lors de l’étape de configuration.

     >[!NOTE]
     >Le jeton d’accès expire toutes les 24 heures et un nouveau doit être créé. Pour créer un jeton, revenez à la section [Console Adobe Developer](https://developer.adobe.com/console/), choisissez votre projet, cliquez sur **API de gestion des utilisateurs**, puis collez la même clé privée dans la zone.

1. Une fois les champs renseignés, cliquez sur **Test Configuration** pour tester la connexion au service d’API User Management. Si la connexion est établie, vous pouvez cliquer sur **Enregistrer** pour enregistrer la configuration.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access4.png)

1. Après avoir enregistré la configuration, sélectionnez-la et cliquez sur **Mappage de l’utilisateur de démarrage**.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-landing4.png)

1. Cliquez sur **Début** dans la boîte de dialogue pour lancer le processus de mappage utilisateur.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   Elle affiche le **Statut** comme étant **EN COURS**.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-start1.png)


1. Une fois le mappage utilisateur terminé, cliquez sur **Résultats** pour afficher le résumé.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-landing5.png)

   >[!IMPORTANT]
   >
   >* Une fois le mappage utilisateur terminé, vous pouvez revenir à la page Migration du contenu à l’aide du chemin de navigation. La carte Mappage des utilisateurs affiche le statut et l’horodatage. Cliquez sur **Transfert de contenu** vous pouvez ainsi créer un jeu de migration pour exécuter l’extraction. Voir [Exécution de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=fr#running-tool) pour plus d’informations.

### Reprise du processus de mappage des utilisateurs {#resume-user-mapping-process}

Si le processus de mappage des utilisateurs est arrêté pour l’une des raisons suivantes :

* L’option **Arrêt du mappage des utilisateurs** a été sélectionné par l’utilisateur.
* Le jeton d’accès a expiré pendant le processus.
* Ou, pour une autre raison.

  >[!NOTE]
  >La progression est enregistrée à partir de l’endroit où le processus s’est arrêté.

Pour reprendre le processus de mappage des utilisateurs, procédez comme suit :

1. Cliquez sur **Afficher le journal** pour consulter le journal de mappage des utilisateurs afin de vérifier la progression enregistrée.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping1.png)

1. Cliquez sur **Mappage de l’utilisateur de démarrage** pour reprendre à l’endroit où il s’est arrêté.

   >[!NOTE]
   >Assurez-vous, avant de redémarrer, que le jeton d’accès est toujours valide ou qu’il a été actualisé.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping2.png)

1. Cliquez sur **Début** dans la boîte de dialogue pour reprendre le processus de mappage utilisateur.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   Une fois le processus de mappage des utilisateurs terminé, vous pouvez afficher la variable **État** as **FINISHED** pour cette configuration spécifique.

   ![image](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping4.png)
