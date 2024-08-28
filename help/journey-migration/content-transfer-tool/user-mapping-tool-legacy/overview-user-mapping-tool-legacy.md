---
title: Présentation de l’outil de mappage des utilisateurs et des utilisatrices (hérité)
description: Présentation de l’outil de mappage des utilisateurs et des utilisatrices (hérité)
exl-id: 17ed5721-093e-4491-b8c4-3dadcaa6598b
hide: true
hidefromtoc: true
feature: Migration
role: Admin
source-git-commit: e5fd1b351047213adbb83ef1d1722352958ce823
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 96%

---


# Présentation de l’outil de mappage des utilisateurs et des utilisatrices (hérité) {#overview-user-mapping-tool}

>[!INFO]
>
>Cette documentation fait référence à une version obsolète de l’outil. Pour plus d’informations sur la dernière version, voir [Migration de groupe](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md).

<!-- Alexandru: drafting this for now

NOTE: "LEGACY" for user mapping includes everything before (that is, not including) 2.0.16 of CTT.

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="User Mapping Tool"
>abstract="The Content Transfer Tool helps you move users and groups from your existing AEM system to AEM as a Cloud Service. Existing users and groups need to be mapped to their IMS IDs to avoid duplicate users and groups on the Cloud Service author instance."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html#important-considerations" text="Important Considerations for using User Mapping Tool"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html#using-user-mapping-tool" text="Using User Mapping Tool"

-->

## Présentation {#introduction}

Dans le cadre de la transition vers Adobe Experience Manager (AEM) as a Cloud Service, vous devez transférer les utilisateurs et utilisatrices, et les groupes de votre système AEM existant vers AEM as a Cloud Service. Cette migration est effectuée par l’outil de transfert de contenu.

L’un des changements majeurs apportés à AEM as a Cloud Service est l’utilisation entièrement intégrée des Adobe ID pour l’accès au niveau création. Cette intégration nécessite l’utilisation d’[Adobe Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html) afin de gérer les utilisateurs et utilisatrices, et les groupes d’utilisateurs et d’utilisatrices. Les informations relatives au profil utilisateur sont centralisées dans Identity Management System (IMS) d’Adobe, qui permet une authentification unique à toutes les applications cloud d’Adobe. Pour plus d’informations, voir [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html?lang=fr#identity-management). En raison de cette modification, les utilisateurs et utilisatrices, et les groupes existants doivent être mappés avec leurs ID IMS pour éviter d’être dupliqués sur l’instance de création Cloud Service.

## Outil de mappage des utilisateurs et utilisatrices {#mapping-tool}

L’outil de transfert de contenu (sans mappage utilisateur) migre les utilisateurs et utilisatrices, et les groupes associés au contenu en cours de migration. L’outil de mappage des utilisateurs et utilisatrices fait partie de l’outil de transfert de contenu. Son seul objectif est de modifier les utilisateurs et utilisatrices afin qu’ils soient reconnus par IMS, la fonctionnalité d’authentification unique utilisée par AEM as a Cloud Service. Une fois ces modifications effectuées, l’outil de transfert de contenu migre les utilisateurs, les utilisatrices et les groupes du contenu spécifié comme d’habitude.

### Prochaines étapes {#whats-next}

Une fois que vous avez appris ce qu’est un outil de mappage des utilisateurs, vous êtes prêt à passer en revue les points importants et les cas exceptionnels à prendre en compte avant d’utiliser l’outil de mappage des utilisateurs. Consultez les [Considérations concernant l’outil de mappage des utilisateurs](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md) pour plus d’informations.
