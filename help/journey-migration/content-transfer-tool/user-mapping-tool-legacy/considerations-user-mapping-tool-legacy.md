---
title: Points importants concernant l’outil de mappage utilisateur (hérité)
description: Points importants concernant l’outil de mappage utilisateur (hérité)
exl-id: 0d39a5be-93e1-4b00-ac92-c2593c02b740
hide: true
hidefromtoc: true
source-git-commit: 7260649eaab303ba5bab55ccbe02395dc8159949
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 12%

---

# Points importants concernant l’outil de mappage utilisateur (hérité) {#important-considerations}

>[!INFO]
>
>Cette documentation fait référence à une version obsolète de l’outil. Pour plus d’informations sur la dernière version, voir [Mappage des utilisateurs et migration des entités de sécurité](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md).

## Cas exceptionnels {#exceptional-cases}

Les cas spécifiques suivants sont consignés :

1. Si un utilisateur ne dispose d’aucune adresse électronique dans la variable `profile/email` de leur champ *jcr* , l’utilisateur ou le groupe en question est migré, mais n’est pas mappé. Cette règle est appliquée même si l’adresse électronique est utilisée comme nom d’utilisateur pour la connexion.

1. Si un courrier électronique est introuvable sur le système Adobe Identity Management (IMS) pour l’ID d’organisation utilisé (ou, si l’ID IMS ne peut pas être récupéré), l’utilisateur ou le groupe est migré, mais pas mappé.

1. Si l’utilisateur ou l’utilisatrice est désactivé, le traitement est le même que s’il ou elle ne l’était pas. Il est mappé et migré normalement et reste désactivé sur l’instance cloud.

1. Si un utilisateur existe sur l’instance AEM Cloud Service cible avec le même nom d’utilisateur (rep:principalName) que l’un des utilisateurs sur l’instance d’AEM source, l’utilisateur ou le groupe n’est pas migré.

1. Si un utilisateur est migré sans avoir au préalable été mappé au moyen du mappage de l’utilisateur, il ne peut pas se connecter sur le système cloud cible à l’aide de son identifiant IMS. Ils peuvent se connecter à l’aide de la méthode d’AEM traditionnelle, mais ce workflow n’est normalement pas ce qui est attendu ou voulu.

## Considérations supplémentaires {#additional-considerations}

* Si le paramètre **Effacer le contenu existant sur l’instance cloud avant l’ingestion** est définie, les utilisateurs déjà transférés sur l’instance de Cloud Service sont supprimés. L’intégralité du référentiel existant est également supprimée et un nouveau référentiel est créé dans lequel le contenu est ingéré. Cette action réinitialise également tous les paramètres, y compris les autorisations sur l’instance de Cloud Service cible. Elle est vraie pour un utilisateur administrateur ajouté à la variable **administrateurs** groupe. L’utilisateur administrateur doit être lu dans la variable **administrateurs** pour récupérer le jeton d’accès pour CTT.

* Adobe recommande de supprimer tout utilisateur existant de l’instance AEM Cloud Service cible avant d’exécuter CTT avec le mappage utilisateur. Cette action est nécessaire pour éviter tout conflit entre les utilisateurs migrés de l’instance d’AEM source vers l’instance AEM cible. Des conflits peuvent se produire lors de l’ingestion si le même utilisateur existe sur l’instance d’AEM source et l’instance AEM cible.

* Lorsque des compléments de contenu sont effectués, si le contenu n’est pas transféré car il n’a pas été modifié depuis le transfert précédent, les utilisateurs et les groupes associés à ce contenu ne sont pas transférés non plus. Cette règle est vraie même si les utilisateurs et les groupes ont changé entre-temps. Cela est dû au fait que les utilisateurs et les groupes sont migrés avec le contenu auquel ils sont associés.

* Si AEM Cloud Service comporte un utilisateur portant un nom d’utilisateur différent, mais ayant la même adresse électronique qu’un utilisateur sur l’instance d’AEM source, et si le mappage d’utilisateur est activé, un message d’erreur est consigné. En outre, l’utilisateur de l’AEM source n’est pas transféré, car un seul utilisateur disposant d’une adresse électronique donnée est autorisé sur le système cible.

* Si deux utilisateurs de l’instance d’AEM source ont la même adresse électronique et que le mappage utilisateur est activé, un message d’erreur est consigné. En outre, l’un des utilisateurs de l’AEM source est transféré, car un seul utilisateur disposant d’une adresse électronique donnée est autorisé sur le système cible.

### Prochaines étapes {#whats-next}

Une fois que vous aurez pris connaissance des principales considérations et des cas exceptionnels, vous serez prêt à utiliser l’outil. Pour plus d’informations, consultez [Utilisation de l’outil de mappage des utilisateurs](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/using-user-mapping-tool-legacy.md).
