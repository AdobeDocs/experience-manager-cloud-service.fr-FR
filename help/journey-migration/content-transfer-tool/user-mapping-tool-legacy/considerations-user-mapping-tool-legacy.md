---
title: Points importants concernant l’outil de mappage des utilisateurs (hérité)
description: Points importants concernant l’outil de mappage des utilisateurs (hérité)
exl-id: 0d39a5be-93e1-4b00-ac92-c2593c02b740
hide: true
hidefromtoc: true
source-git-commit: f7be351c85b8db6d11033c7cf064529a46c2802a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Points importants concernant l’outil de mappage des utilisateurs (hérité) {#important-considerations}


## Cas exceptionnels {#exceptional-cases}

Les cas spécifiques suivants seront consignés :

1. Si un utilisateur n’a pas d’adresse électronique dans le champ `profile/email` de son nœud *jcr*, l’utilisateur ou le groupe en question sera migré, mais pas mappé.  Cela sera le cas même si l’adresse électronique est utilisée comme nom d’utilisateur pour la connexion.

1. Si un courrier électronique donné est introuvable sur le système IMS (Adobe Identity Management System) pour l’ID d’organisation utilisé (ou si l’ID IMS ne peut pas être récupéré pour une autre raison), l’utilisateur ou le groupe en question sera migré, mais pas mappé.

1. Si l’utilisateur est actuellement désactivé, il est traité de la même manière que s’il n’était pas désactivé. Il fera l’objet d’une migration et d’un mappage normaux et restera désactivé sur l’instance cloud.

1. Si un utilisateur existe sur l’instance d’AEM Cloud Service cible avec le même nom d’utilisateur (rep:principalName) que l’un des utilisateurs de l’instance d’AEM source, l’utilisateur ou le groupe en question ne fera pas l’objet d’une migration.

1. Si un utilisateur est migré sans avoir au préalable été mappé via le mappage utilisateur, il ne pourra pas se connecter à l’aide de son identifiant IMS sur le système cloud cible.  Ils peuvent se connecter à l’aide de la méthode d’AEM traditionnelle, mais gardez à l’esprit que ce n’est normalement pas ce qui est recherché ou attendu.

## Considérations supplémentaires {#additional-considerations}

* Si le paramètre **Effacer le contenu existant sur l’instance cloud avant l’ingestion** est défini, les utilisateurs déjà transférés sur l’instance de Cloud Service seront supprimés avec l’ensemble du référentiel existant, et un nouveau référentiel sera créé pour intégrer du contenu. Cette opération réinitialise également tous les paramètres, y compris les autorisations sur l’instance Cloud Service cible, et est effective pour un utilisateur administrateur ajouté au groupe **administrateurs**. L’utilisateur administrateur doit être réajouté au groupe **administrateurs** pour récupérer le jeton d’accès à l’outil de transfert de contenu (CTT).

* Il est recommandé de supprimer tout utilisateur existant de l’instance d’AEM Cloud Service cible avant d’exécuter CTT avec mappage des utilisateurs. Cela permet d’éviter tout conflit entre la migration des utilisateurs de l’instance AEM source vers l’instance AEM cible. Des conflits surviendront lors de l’ingestion si un même utilisateur existe sur l’instance AEM source et l’instance AEM cible.

* Lorsque des rechargements de contenu sont effectués, si le contenu n’est pas transféré parce qu’il n’a pas été modifié depuis le transfert précédent, les utilisateurs et les groupes associés à ce contenu ne seront pas transférés non plus, même si les utilisateurs et les groupes ont changé entre-temps. En effet, les utilisateurs et les groupes font l’objet d’un migration avec le contenu auquel ils sont associés.

* Si l’instance AEM Cloud Service cible a un utilisateur avec un nom d’utilisateur différent, mais la même adresse électronique que l’un des utilisateurs de l’instance AEM source, et que le mappage des utilisateurs est activé, un message d’erreur s’inscrit dans les journaux et l’utilisateur AEM source n’est pas transféré, car un seul utilisateur avec une adresse électronique donnée est autorisé sur le système cible.

* Si deux utilisateurs de l’instance d’AEM source ont la même adresse électronique et que le mappage des utilisateurs est activé, un message d’erreur s’inscrit dans les journaux et l’un des utilisateurs source d’AEM ne sera pas transféré, car un seul utilisateur disposant d’une adresse électronique donnée est autorisé sur le système cible.

### Prochaines étapes {#whats-next}

Une fois que vous aurez pris connaissance des principales considérations et des cas exceptionnels, vous serez prêt à utiliser l’outil. Pour plus d’informations, consultez [Utilisation de l’outil de mappage des utilisateurs](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/using-user-mapping-tool-legacy.md).
