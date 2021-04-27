---
title: Utilisation de l’outil de mappage des utilisateurs
description: Utilisation de l’outil de mappage des utilisateurs
exl-id: 88ce7ed3-46fe-4b3f-8e18-c7c8423faf24
translation-type: tm+mt
source-git-commit: 7bdf8f1e6d8ef1f37663434e7b14798aeb8883f4
workflow-type: tm+mt
source-wordcount: '1185'
ht-degree: 58%

---

# Utilisation de l’outil de mappage des utilisateurs {#user-mapping-tool}

## Présentation {#overview}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="Outil Mappage utilisateur"
>abstract="L’outil de transfert de contenu vous permet de déplacer les utilisateurs et les groupes de votre système AEM existant vers AEM en tant que Cloud Service. Les utilisateurs et les groupes existants doivent être mappés à leurs ID IMS pour éviter que des utilisateurs et des groupes de duplicata ne soient associés à l’instance d’auteur du Cloud Service."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#important-considerations" text="Considérations importantes pour l’utilisation de l’outil de mappage des utilisateurs"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#using-user-mapping-tool" text="Utilisation de l’outil de mappage des utilisateurs"


Dans le cadre du parcours de transition vers Adobe Experience Manager (AEM) as a Cloud Service, vous devez déplacer les utilisateurs et les groupes du système AEM existant vers AEM as a Cloud Service. Cette opération fait appel à l’outil de transfert de contenu.

L’un des changements majeurs apportés à AEM as a Cloud Service est l’utilisation entièrement intégrée des Adobe ID pour l’accès au niveau création.  Pour ce faire, vous devez utiliser [Adobe Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html) afin de gérer les utilisateurs et les groupes d’utilisateurs. Les informations de profil d’utilisateur sont centralisées dans le système Adobe IMS (Identity Management System), qui permet l’authentification unique pour toutes les applications de cloud d’Adobe. Pour plus d’informations, consultez [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html?lang=fr#identity-management). En raison de cette modification, les utilisateurs et groupes existants doivent être mappés avec leurs ID IMS pour éviter que des doublons d’utilisateurs et de groupes ne soient associés à l’instance de création Cloud Service.

## Points importants {#important-considerations}

### Cas exceptionnels {#exceptional-cases}

Les cas spécifiques suivants seront consignés :

1. Si un utilisateur n’a pas d’adresse électronique dans le champ `profile/email` de son noeud *jcr*, l’utilisateur ou le groupe en question sera migré, mais pas mappé.

1. Si un courrier électronique donné est introuvable sur le système IMS (Adobe Identity Management System) pour l&#39;ID d&#39;organisation utilisé (ou si l&#39;ID IMS ne peut pas être récupéré pour une autre raison), l&#39;utilisateur ou le groupe en question sera migré, mais pas mappé.

1. Si l’utilisateur est actuellement désactivé, il est traité de la même manière que s’il n’était pas désactivé. Il fera l’objet d’une migration et d’un mappage normaux et restera désactivé sur l’instance cloud.

1. Si un utilisateur existe sur l’instance de l’Cloud Service de l’cible AEM avec le même nom d’utilisateur (rep:principalName) que l’un des utilisateurs de l’instance d’AEM source, l’utilisateur ou le groupe en question ne sera pas migré.

### Remarques complémentaires {#additional-considerations}

* Si le paramètre **Effacer le contenu existant sur l’instance Cloud avant l’assimilation** est défini, les utilisateurs déjà transférés sur l’instance de Cloud Service seront supprimés avec l’ensemble du référentiel existant et un nouveau référentiel sera créé pour intégrer du contenu. Ceci réinitialise également tous les paramètres, y compris les autorisations sur l’instance de Cloud Service de cible, et est vrai pour un utilisateur administrateur ajouté au groupe **administrateurs**. L’utilisateur administrateur doit être réajouté au groupe **administrateurs** pour récupérer le jeton d&#39;accès pour CTT.

* Il est recommandé de supprimer tout utilisateur existant de l’instance d’AEM Cloud Service de cible avant d’exécuter CTT avec Mappage d’utilisateur. Cela permet d’éviter tout conflit entre la migration des utilisateurs de l’instance d’AEM source vers l’instance d’AEM de cible. Des conflits surviendront lors de l’assimilation si un même utilisateur existe sur l’instance d’AEM source et l’instance d’AEM de cible.

* Lorsque des rechargements de contenu sont effectués, si le contenu n’est pas transféré parce qu’il n’a pas été modifié depuis le transfert précédent, les utilisateurs et les groupes associés à ce contenu ne seront pas transférés non plus, même si les utilisateurs et les groupes ont changé entre-temps. En effet, les utilisateurs et les groupes sont migrés avec le contenu auquel ils sont associés.

* L&#39;importation échoue dans les cas suivants :

1. Si l’instance de l’Cloud Service de cible a un utilisateur avec un nom d’utilisateur différent mais la même adresse électronique que l’un des utilisateurs de l’instance d’AEM source.

1. S’il y a deux utilisateurs sur l’instance d’AEM source avec des noms d’utilisateur différents mais la même adresse électronique. AEM en tant que Cloud Service ne permet pas à deux utilisateurs d’avoir la même adresse électronique.

## Utilisation de l’outil de mappage des utilisateurs {#using-user-mapping-tool}

L’outil de mappage utilisateur utilise une API qui lui permet de rechercher des utilisateurs du système de Identity Management Adobe (IMS) par courrier électronique et de renvoyer leurs ID IMS. Cette API nécessite que l’utilisateur crée un ID client pour son organisation, un secret client et un jeton d’accès ou de porteur.

Suivez les étapes ci-dessous pour configurer ces éléments :

1. Accédez à la [Adobe Developer Console](https://console.adobe.io) à l’aide de votre Adobe ID.
1. Créez un projet ou ouvrez un formulaire existant.
1. Ajoutez une API.
1. Sélectionnez l’API Gestion des utilisateurs.
1. Créez des informations d’identification JWT.
1. Générez une paire de clés ou chargez une clé publique (RSA ne convient pas).
1. Générez un jeton d’accès (ou jeton JWT ou jeton au porteur).
1. Enregistrez en lieu sûr ces informations, notamment l’**ID client**, le **secret client**, l’**ID de compte technique**, l’**adresse électronique du compte technique**, l’**ID d’organisation** et le **jeton d’accès**.

## Interface utilisateur {#user-interface}

L’outil de mappage des utilisateurs est intégré à l’outil de transfert de contenu. Vous pouvez télécharger l’outil de transfert de contenu depuis le [portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). Pour plus d’informations sur la dernière version, consultez les [Notes de mise à jour actuelles](/help/release-notes/release-notes-cloud/release-notes-current.md).

1. Sélectionnez Adobe Experience Manager et accédez à Outils -> **Opérations** -> **Transfert de contenu**.
1. Cliquez sur **Créer une configuration de mappage des utilisateurs**.

   >[!NOTE]
   >Si vous ignorez cette étape, le mappage des utilisateurs et des groupes sera ignoré au cours de la phase d’extraction.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-1.png)

   Renseignez les champs de la configuration de l’API Gestion des utilisateurs comme décrit ci-dessous :

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-2.png)

   * **ID d’organisation** : saisissez l’ID d’organisation Adobe IMS (Identity Management System) pour l’organisation depuis laquelle migrent les utilisateurs.

      >[!NOTE]
      >Pour obtenir l’ID d’organisation, connectez-vous à l’[Admin Console](https://adminconsole.adobe.com/) et choisissez votre organisation (dans la zone supérieure droite) si vous appartenez à plusieurs. L’ID d’organisation se trouve dans l’URL de cette page, au format `xx@AdobeOrg`, où xx correspond à l’ID d’organisation IMS.  Vous pouvez également trouver l’ID d’organisation sur la page [Adobe Developer Console](https://console.adobe.io) où vous générez le jeton d’accès.

   * **ID client** : saisissez l’ID client enregistré à l’étape de configuration.

   * **Jeton d’accès** : saisissez le jeton d’accès enregistré lors de l’étape de configuration.

      >[!NOTE]
      >Le jeton d’accès arrive à expiration toutes les 24 heures et il faut en créer un nouveau. Pour créer un jeton, revenez dans [Adobe Developer Console](https://console.adobe.io), choisissez votre projet, cliquez sur **User Management API** (API Gestion des utilisateurs) et collez la même clé privée dans la zone.

1. Après avoir saisi les informations ci-dessus, cliquez sur **Save** (Enregistrer).

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-3.png)


1. Créez un jeu de migration en cliquant sur **Create Migration Set** (Créer un jeu de migration) et en renseignant les champs, puis cliquez sur **Save** (Enregistrer). Pour plus d’informations, reportez-vous à la section [Exécution de l’outil de transfert de contenu](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#running-tool).

   >[!NOTE]
   >Par défaut, l’option de bascule destinée à inclure le mappage des utilisateurs à partir des utilisateurs et groupes IMS est activée. Avec ce paramètre, lorsque l’extraction est appliquée à ce jeu de migration, l’outil de mappage des utilisateurs s’exécute dans le cadre de la phase d’extraction. C’est la méthode recommandée pour exécuter la phase d’extraction de l’outil de transfert de contenu. Si ce paramètre est désactivé et/ou si la configuration du mappage des utilisateurs n’est pas créée, le mappage des utilisateurs et des groupes est ignoré pendant la phase d’extraction.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-4.png)

1. Pour exécuter la phase d’extraction, reportez-vous à la section [Exécution de l’outil de transfert de contenu](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#running-tool).
