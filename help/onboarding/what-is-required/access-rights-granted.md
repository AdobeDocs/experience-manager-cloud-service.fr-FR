---
title: Droits d'accès accordés - Ce qui est requis
description: Droits d'accès accordés - Ce qui est requis
translation-type: tm+mt
source-git-commit: 8259bf4e7f2004d76fd985ec7ad7c416b6f8d491
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 50%

---


# Droits d’accès accordés {#access-rights-granted}

L&#39;Adobe va créer un **identifiant d&#39;organisation** pour votre société dans le système IMS (Adobe Identity Management System), où tous vos utilisateurs et leurs autorisations peuvent être gérés. Chaque utilisateur, qui doit être membre de cette organisation et qui aura accès à l&#39;un des services [!UICONTROL Experience Cloud], devra disposer de son propre **Adobe ID**.

## Types d’identités de l’utilisateur {#user-identity-types}

Pour commencer à utiliser un Adobe ID, consultez la page [Gérer les types d’identités Adobe](https://helpx.adobe.com/fr/enterprise/using/identity.html), afin d’obtenir des instructions détaillées sur la manière d’obtenir un Adobe ID à l’aide de l’un des types d’identités disponibles.

## Utilisateurs et rôles {#users-and-roles}

Une fois qu’Adobe a créé une organisation pour votre entreprise, l’administrateur désigné sera ajouté en tant que premier membre à cette organisation. Par défaut, l’administrateur se verra octroyer les autorisations d’administrateur et attribuer le [!UICONTROL produit] **AEM Managed Services** et un ou plusieurs [!UICONTROL profils de produits] **Cloud Manager**.

1. Une fois que votre administrateur système vous a accordé l’accès à Cloud Manager, vous recevrez un courrier électronique vous conduisant à la page de connexion de Cloud Manager, également accessible via [Adobe Experience Cloud](https://my.cloudmanager.adobe.com/).

1. Dans le landing page de Cloud Manager, cliquez sur **Gérer l’accès**.

   ![](/help/onboarding/getting-access-to-aem-in-cloud/assets/sys-admin5.png)

1. Une fois que vous avez cliqué sur **Gérer l’accès**, vous accédez à **Admin Console** à partir duquel vous pouvez gérer les rôles utilisateur ou les autorisations de Cloud Manager.

   ![](/help/onboarding/getting-access-to-aem-in-cloud/assets/sys-admin1.png)

   Depuis le Admin Console, vous pouvez exécuter des tâches SysAdmin telles que :
   * [Gestion des rôles](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html?lang=en#manage-roles)
   * [Gestion de l’accès à l’instance d’auteur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html?lang=en#manage-access-aem)

      >[!NOTE]
      >Consultez la section [Utilisateurs et rôles](#users-roles) pour en savoir plus sur les utilisateurs et les définitions de rôles dans Cloud Manager.

Avec ces droits, votre administrateur dispose maintenant d’une authentification unique (à l’aide de l’Adobe ID) pour accéder aux services [!UICONTROL Experience Cloud], se connecter à vos environnements cloud AEM et utiliser [!UICONTROL Cloud Manager].

La plupart des fonctionnalités de [!UICONTROL Cloud Manager] nécessitent des autorisations spécifiques.

[!UICONTROL Cloud Manager] définit actuellement quatre rôles pour les utilisateurs qui régissent la disponibilité de fonctionnalités spécifiques :

* Propriétaire de l’entreprise
* Responsable de programme
* Responsable de déploiement
* Développeur

>[!CAUTION]
>Pour utiliser [!UICONTROL Cloud Manager], vous devez disposer d’une Adobe ID et du Adobe Experience Manager en tant que contexte de produit Cloud Service.

### Définitions de rôle {#role-definitions}

>[!NOTE]
>
>Dans Admin Console, le développeur n’est pas lié au rôle Développeur dans [!UICONTROL Cloud Manager].

Le tableau suivant résume les rôles :

| Rôles de [!UICONTROL Cloud Manager] | Description |
|--- |--- |
| Propriétaire de l’entreprise | Est responsable de la définition des ICP, approuve les déploiements en production et contourne les échecs de trois niveaux. |
| Responsable de programme | Utilise [!UICONTROL Cloud Manager] pour configurer les équipes et passer en revue les statuts et les IPC. Peut approuver des échecs importants de 3 niveaux. |
| Responsable de déploiement | Gère les opérations de déploiement. Utilise [!UICONTROL Cloud Manager] pour exécuter les déploiements dans les environnements intermédiaires/de production. Peut modifier les pipelines CI/CD. Peut approuver des échecs importants de 3 niveaux. Peut accéder au référentiel Git. |
| Développeur | Développe et teste du code d’application personnalisé. Utilise principalement [!UICONTROL Cloud Manager] pour consulter les statuts. Peut accéder au référentiel Git pour la validation du code. |
| Auteur de contenu | N’interagit généralement pas avec [!UICONTROL Cloud Manager]. Peut utiliser le commutateur de programmes de [!UICONTROL Cloud Manager] (depuis [!UICONTROL Experience Cloud]) pour accéder à AEM. |

### Profil du produit d&#39;intégration {#integration-product-profile}

Outre ce qui précède, Cloud Manager crée automatiquement un profil de produits nommé &quot;Intégrations - Cloud Service&quot;. Ce profil de produits est utilisé pour les intégrations entre Adobe Experience Manager et d&#39;autres produits d&#39;Adobe. Ce profil de produit **ne doit pas** être supprimé. Si vous supprimez accidentellement ce profil, il doit être recréé manuellement. Le nom d&#39;affichage de ce profil **doit** être `CM_CS_DEFAULT`.

