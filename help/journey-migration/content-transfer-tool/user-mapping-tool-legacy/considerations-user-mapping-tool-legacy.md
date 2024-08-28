---
title: Points importants concernant l’outil de mappage utilisateur (hérité)
description: Points importants concernant l’outil de mappage utilisateur (hérité)
exl-id: 0d39a5be-93e1-4b00-ac92-c2593c02b740
hide: true
hidefromtoc: true
feature: Migration
role: Admin
source-git-commit: 13a2386c099624a46e84126a939a9470e9b3a5f2
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 98%

---

# Points importants concernant l’outil de mappage utilisateur (hérité) {#important-considerations}

>[!INFO]
>
>Cette documentation fait référence à une version obsolète de l’outil. Pour plus d’informations sur la dernière version, voir [Migration de groupe](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md).

## Cas exceptionnels {#exceptional-cases}

Les cas spécifiques suivants sont consignés :

1. Si un utilisateur ou une utilisatrice n’a pas d’adresse e-mail dans le champ `profile/email` de son nœud *jcr*, l’utilisateur, l’utilisatrice ou le groupe en question est migré, mais pas mappé. Cette règle s’applique même si l’adresse e-mail est utilisée comme nom d’utilisateur pour la connexion.

1. Si une adresse e-mail est introuvable sur le système IMS (Adobe Identity Management System) pour l’ID d’organisation utilisé (ou si l’ID IMS ne peut pas être récupéré), l’utilisateur, l’utilisatrice ou le groupe en question est migré, mais pas mappé.

1. Si l’utilisateur ou l’utilisatrice est désactivé, le traitement est le même que s’il ou elle ne l’était pas. Il ou elle fera l’objet d’une migration et d’un mappage normaux et restera désactivé sur l’instance cloud.

1. Si un utilisateur ou une utilisatrice existe sur l’instance d’AEM Cloud Service cible avec le même nom d’utilisateur (rep:principalName) que l’un des utilisateurs ou l’une des utilisatrices de l’instance d’AEM source, l’utilisateur, l’utilisatrice ou le groupe n’est pas migré.

1. Si un utilisateur ou une utilisatrice est migré sans avoir au préalable été mappé via le mappage utilisateur, sur le système cloud cible, il ou elle ne pourra pas se connecter à l’aide de son identifiant IMS. La connexion sera possible à l’aide de la méthode AEM traditionnelle, mais ce n’est pas ce workflow qui est normalement recherché ou attendu.

## Considérations supplémentaires {#additional-considerations}

* Si le paramètre **Effacer le contenu existant sur l’instance Cloud avant l’ingestion** est défini, les utilisateurs et utilisatrices déjà transférés sur l’instance Cloud Service sont supprimés. L’intégralité du référentiel existant est également supprimée et un nouveau référentiel est créé dans lequel le contenu est ingéré. Cette action réinitialise également tous les paramètres, y compris les autorisations sur l’instance Cloud Service cible, et est effective pour une personne en charge de l’administration ajoutée au groupe d’**administration**. La personne en charge de l’administration doit être rajoutée au groupe d’**administration** pour récupérer le jeton d’accès pour l’outil de transfert de contenu.

* Adobe recommande de supprimer tout utilisateur ou utilisatrice existant de l’instance Cloud Service cible d’AEM avant d’exécuter le CTT avec le mappage utilisateur. Cette action est nécessaire pour éviter tout conflit entre la migration des utilisateurs et utilisatrices de l’instance AEM source vers l’instance AEM cible. Des conflits peuvent survenir lors de l’ingestion si un même utilisateur ou une même utilisatrice existe sur l’instance AEM source et l’instance AEM cible.

* Lorsque des rechargements de contenu sont effectués, si le contenu n’est pas transféré parce qu’il n’a pas été modifié depuis le transfert précédent, les utilisateurs, les utilisatrices et les groupes associés à ce contenu ne seront pas transférés non plus. Cette règle est vraie même si les utilisateurs et utilisatrices, et les groupes ont changé entre-temps. En effet, les utilisateurs, les utilisatrices et les groupes font l’objet d’une migration avec le contenu auquel ils ou elles sont associés.

* Si AEM Cloud Service comporte un utilisateur ou une utilisatrice portant un nom d’utilisateur différent, mais ayant la même adresse e-mail qu’un utilisateur ou une utilisatrice sur l’instance d’AEM source, et si le mappage utilisateur est activé, un message d’erreur est consigné. En outre, l’utilisateur ou utilisatrice d’AEM source n’est pas transféré, car seul un utilisateur ou une utilisatrice disposant d’une adresse e-mail donnée est autorisé sur le système cible.

* Si deux utilisateurs ou utilisatrices de l’instance d’AEM source ont la même adresse e-mail et que le mappage utilisateur est activé, un message d’erreur est consigné. En outre, l’un des utilisateurs ou l’une des utilisatrices d’AEM source est transféré(e), car un seul utilisateur ou une seule utilisatrice disposant d’une adresse e-mail donnée est autorisé(e) sur le système cible.

### Prochaines étapes {#whats-next}

Une fois que vous aurez pris connaissance des principales considérations et des cas exceptionnels, vous serez prêt à utiliser l’outil. Pour plus d’informations, consultez [Utilisation de l’outil de mappage des utilisateurs](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/using-user-mapping-tool-legacy.md).
