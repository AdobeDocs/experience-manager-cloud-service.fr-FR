---
title: Utilisation de l’outil de mappage des utilisateurs
description: Utilisation de l’outil de mappage des utilisateurs
translation-type: tm+mt
source-git-commit: 2ceaaa4db35ab793392ae3644db9b862cbf9af2b
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 6%

---


# Utilisation de l’outil de mappage utilisateur {#user-mapping-tool}

## Présentation {#overview}

Dans le cadre du parcours de transition à Adobe Experience Manager (AEM) en tant que Cloud Service, vous devez déplacer les utilisateurs et les groupes de votre système AEM existant vers l&#39;AEM en tant que Cloud Service. Pour ce faire, utilisez l’outil de transfert de contenu.

L’un des changements majeurs apportés à AEM as a Cloud Service est l’utilisation entièrement intégrée des Adobe ID pour l’accès au niveau création.  Pour ce faire, il faut utiliser le [Adobe Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html) pour gérer les utilisateurs et les groupes d’utilisateurs. Les informations utilisateur-profil sont centralisées dans l’Adobe Identity Management System (IMS), qui permet l’authentification unique dans toutes les applications de cloud d’Adobes. Pour plus d&#39;informations, consultez [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html?lang=en#identity-management). En raison de cette modification, les utilisateurs et groupes existants doivent être mappés à leurs ID IMS pour éviter que des utilisateurs et des groupes de duplicata ne soient associés à l’instance d’auteur du Cloud Service.

## Points importants {#important-considerations}

Il y a quelques cas exceptionnels à examiner. Les cas spécifiques suivants seront consignés et l’utilisateur ou le groupe en question ne sera pas mappé :

1. Si un utilisateur n’a pas d’adresse électronique dans le champ `profile/email` de son noeud *jcr*.

1. Si un courrier électronique donné est introuvable sur le système IMS (Adobe Identity Management System) pour l&#39;ID d&#39;organisation utilisé (ou si l&#39;ID IMS ne peut pas être récupéré pour une autre raison).

1. Si l’utilisateur est actuellement désactivé, il est traité de la même manière que s’il n’était pas désactivé. Il sera mappé et migré comme normal et restera désactivé sur l’instance de cloud.

## Utilisation de l’outil de mappage des utilisateurs {#using-user-mapping-tool}

L’outil de mappage utilisateur utilise une API qui lui permet de rechercher des utilisateurs du système IMS (Adobe Identity Management System) par courrier électronique et de renvoyer leurs ID IMS. Cette API requiert que l&#39;utilisateur crée un ID de client pour son organisation, une clé secrète client et un jeton d&#39;accès ou de garde.

Suivez les étapes ci-dessous pour configurer ce paramètre :

1. Accédez à [Adobe Developer Console](https://console.adobe.io) à l&#39;aide de votre Adobe ID.
1. Créez un projet ou ouvrez un projet existant.
1. Ajoutez une API.
1. Sélectionnez User Management API.
1. Créez des informations d’identification JWT.
1. Générez une paire de clés ou Téléchargez une clé publique (rsa ne convient pas).
1. Générez un jeton d&#39;accès (ou jeton JWT ou jeton porteur).
1. Enregistrez en toute sécurité toutes ces informations, telles que **ID client**, **Secret client**, **ID de compte technique**, **Adresse électronique du compte technique**, **ID d&#39;entreprise** et **Jeton d&#39;accès**.

## Interface utilisateur {#user-interface}

L’outil de mappage utilisateur est intégré à l’outil de transfert de contenu. Vous pouvez télécharger l&#39;outil de transfert de contenu à partir de [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). Pour plus d&#39;informations sur la dernière version, consultez les [Notes de mise à jour actuelles](/help/release-notes/release-notes-cloud/release-notes-current.md).

1. Sélectionnez Sélectionner le Adobe Experience Manager et accédez aux outils -> **Opérations** -> **Transfert de contenu**.
1. Cliquez sur **Créer une configuration de mappage utilisateur**.

   >[!NOTE]
   >Si vous ignorez cette étape, le mappage des utilisateurs et des groupes sera ignoré pendant la phase d’Extraction.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-1.png)

   Renseignez les champs de la configuration de l’API User Management comme décrit ci-dessous :

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-2.png)

   * **ID** d&#39;entreprise : Saisissez l’ID d’organisation Adobe Identity Management System (IMS) pour l’organisation que les utilisateurs migrent.

      >[!NOTE]
      >Pour obtenir l’ID d’organisation, connectez-vous au [Admin Console](https://adminconsole.adobe.com/) et choisissez votre organisation (dans la zone supérieure droite) si vous appartenez à plusieurs organisations. L’ID d’organisation se trouve dans l’URL de cette page, au format `xx@AdobeOrg`, où xx correspond à l’ID d’organisation IMS.  Vous pouvez également trouver l’ID d’organisation dans la [Adobe Developer Console](https://console.adobe.io) page où vous générez le Jeton d&#39;accès.

   * **ID** client : Saisissez l’ID client que vous avez enregistré à l’étape de configuration.

   * **jeton d&#39;accès** : Entrez le Jeton d&#39;accès que vous avez enregistré à partir de l&#39;étape de configuration.

      >[!NOTE]
      >Le Jeton d&#39;accès arrive à expiration toutes les 24 heures et il faut en créer un nouveau. Pour créer un jeton, revenez dans [Adobe Developer Console](https://console.adobe.io), choisissez votre projet, cliquez sur **User Management API** et collez la même clé privée dans la zone.

1. Après avoir saisi les informations ci-dessus, cliquez sur **Enregistrer**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-3.png)


1. Créez un jeu de migration en cliquant sur **Créer un jeu de migration** et en renseignant les champs, puis en cliquant sur **Enregistrer**. Pour plus d&#39;informations, reportez-vous à la section [Exécution de l&#39;outil de transfert de contenu](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#running-tool).

   >[!NOTE]
   >Par défaut, l’option bascule pour inclure le mappage des utilisateurs à partir des utilisateurs et groupes IMS est ACTIVÉE. Avec ce paramètre, lorsque l’Extraction est effectuée sur ce jeu de migration, l’outil de mappage utilisateur s’exécute dans le cadre de la phase d’Extraction. Il s’agit de la méthode recommandée pour exécuter la phase d’Extraction de l’outil de transfert de contenu. Si cette bascule est désactivée et/ou si la configuration de mappage des utilisateurs n’est pas créée, le mappage des utilisateurs et des groupes est ignoré pendant la phase d’Extraction.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-4.png)

1. Pour exécuter la phase d&#39;Extraction, reportez-vous à la section [Exécution de l&#39;outil de transfert de contenu](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#running-tool).



