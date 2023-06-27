---
title: Présentation de l’outil de mappage des utilisateurs et des utilisatrices (hérité)
description: Présentation de l’outil de mappage des utilisateurs et des utilisatrices (hérité)
exl-id: 17ed5721-093e-4491-b8c4-3dadcaa6598b
hide: true
hidefromtoc: true
source-git-commit: d361ddc9a50a543cd1d5f260c09920c5a9d6d675
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 28%

---

# Présentation de l’outil de mappage des utilisateurs et des utilisatrices (hérité) {#overview-user-mapping-tool}

>[!INFO]
>
>Cette documentation fait référence à une version obsolète de l’outil. Pour plus d’informations sur la dernière version, voir [Mappage des utilisateurs et migration des entités de sécurité](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md).

<!-- Alexandru: drafting this for now

NOTE: "LEGACY" for user mapping includes everything before (i.e. not including) 2.0.16 of CTT.

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="User Mapping Tool"
>abstract="The Content Transfer Tool helps you move users and groups from your existing AEM system to AEM as a Cloud Service. Existing users and groups need to be mapped to their IMS IDs to avoid duplicate users and groups on the Cloud Service author instance."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#important-considerations" text="Important Considerations for using User Mapping Tool"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#using-user-mapping-tool" text="Using User Mapping Tool"

-->

## Présentation {#introduction}

Dans le cadre du parcours de transition vers Adobe Experience Manager (AEM) as a Cloud Service, vous devez déplacer les utilisateurs et les groupes de votre système AEM existant vers l’as a Cloud Service. Cette migration est effectuée par l’outil de transfert de contenu.

L’un des changements majeurs apportés à AEM as a Cloud Service est l’utilisation entièrement intégrée des Adobe ID pour l’accès au niveau création. Cette intégration requiert l’utilisation de la fonction [Adobe Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html) pour la gestion des utilisateurs et des groupes d’utilisateurs. Les informations de profil utilisateur sont centralisées dans Adobe Identity Management System (IMS), qui permet l’authentification unique dans toutes les applications cloud d’Adobe. Pour plus d’informations, voir [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html?lang=en#identity-management). En raison de cette modification, les utilisateurs et les groupes existants doivent être mappés à leurs identifiants IMS afin d’éviter la duplication des utilisateurs et des groupes sur l’instance d’auteur du Cloud Service.

## Outil de mappage des utilisateurs {#mapping-tool}

L’outil de transfert de contenu (sans mappage utilisateur) migre les utilisateurs et les groupes associés au contenu en cours de migration. L’outil de mappage des utilisateurs fait partie de l’outil de transfert de contenu. Son seul objectif est de modifier les utilisateurs afin qu’ils soient correctement reconnus par IMS, la fonctionnalité d’authentification unique utilisée par AEM as a Cloud Service. Une fois ces modifications effectuées, l’outil de transfert de contenu migre les utilisateurs et les groupes du contenu spécifié comme d’habitude.

### Prochaines étapes {#whats-next}

Une fois que vous avez appris ce qu’est un outil de mappage des utilisateurs, vous êtes prêt à passer en revue les points importants et les cas exceptionnels à prendre en compte avant d’utiliser l’outil de mappage des utilisateurs. Consultez les [Considérations concernant l’outil de mappage des utilisateurs](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md) pour plus d’informations.
