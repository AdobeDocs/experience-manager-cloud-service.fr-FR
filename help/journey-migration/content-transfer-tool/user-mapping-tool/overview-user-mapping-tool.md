---
title: Présentation de l’outil de mappage des utilisateurs
description: Présentation de l’outil de mappage des utilisateurs
exl-id: 17ed5721-093e-4491-b8c4-3dadcaa6598b
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 100%

---

# Présentation de l’outil de mappage des utilisateurs {#overview-user-mapping-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="Outil de mappage des utilisateurs"
>abstract="L’outil de transfert de contenu vous permet de déplacer des utilisateurs et des groupes de votre système AEM existant vers AEM as a Cloud Service. Les utilisateurs et groupes existants doivent être mappés avec leurs ID IMS pour éviter que des doublons d’utilisateurs et de groupes ne soient associés à l’instance de création Cloud Service."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=fr#important-considerations" text="Points importants concernant l’utilisation de l’outil de mappage des utilisateurs"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=fr#using-user-mapping-tool" text="Utilisation de l’outil de mappage des utilisateurs"

## Présentation {#introduction}

Dans le cadre du parcours de transition vers Adobe Experience Manager (AEM) as a Cloud Service, vous devez déplacer les utilisateurs et les groupes du système AEM existant vers AEM as a Cloud Service. Cette opération fait appel à l’outil de transfert de contenu.

L’un des changements majeurs apportés à AEM as a Cloud Service est l’utilisation entièrement intégrée des Adobe ID pour l’accès au niveau création. Pour ce faire, vous devez utiliser [Adobe Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html) afin de gérer les utilisateurs et les groupes d’utilisateurs. Les informations de profil d’utilisateur sont centralisées dans le système Adobe IMS (Identity Management System), qui permet l’authentification unique pour toutes les applications de cloud d’Adobe. Pour plus d’informations, consultez [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html?lang=fr#identity-management). En raison de cette modification, les utilisateurs et groupes existants doivent être mappés avec leurs ID IMS pour éviter que des doublons d’utilisateurs et de groupes ne soient associés à l’instance de création Cloud Service.

## Outil de mappage des utilisateurs {#mapping-tool}

L’outil de transfert de contenu (sans mappage utilisateur) migre les utilisateurs et les groupes associés au contenu en cours de migration. L’outil de mappage des utilisateurs fait partie de l’outil de transfert de contenu. Son seul objectif est de modifier les utilisateurs et les groupes afin qu’ils puissent être correctement reconnus par IMS, la fonctionnalité d’authentification unique utilisée par AEM as a Cloud Service. Une fois ces modifications effectuées, l’outil de transfert de contenu migre les utilisateurs et les groupes du contenu spécifié comme d’habitude.

### Prochaines étapes {#whats-next}

Une fois que vous avez appris ce qu’est un outil de mappage des utilisateurs, vous êtes prêt à passer en revue les points importants et les cas exceptionnels à prendre en compte avant d’utiliser l’outil de mappage des utilisateurs. Consultez les [Considérations concernant l’outil de mappage des utilisateurs](/help/journey-migration/content-transfer-tool/user-mapping-tool/considerations-user-mapping-tool.md) pour plus d’informations.
