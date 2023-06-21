---
title: Points importants concernant l’outil de mappage utilisateur (hérité)
description: Points importants concernant l’outil de mappage utilisateur (hérité)
exl-id: 0d39a5be-93e1-4b00-ac92-c2593c02b740
hide: true
hidefromtoc: true
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 47%

---

# Points importants concernant l’outil de mappage utilisateur (hérité) {#important-considerations}

>[!INFO]
>
>Cette documentation fait référence à une version obsolète de l’outil. Pour plus d’informations sur la dernière version, voir [Mappage des utilisateurs et migration des entités de sécurité](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md).

## Cas exceptionnels {#exceptional-cases}

Les cas spécifiques suivants sont consignés :

1. Si un utilisateur ne dispose d’aucune adresse électronique dans la variable `profile/email` de leur champ *jcr* , l’utilisateur ou le groupe en question est migré, mais n’est pas mappé.  Cette règle est appliquée même si l’adresse électronique est utilisée comme nom d’utilisateur pour la connexion.

1. Si un message électronique donné est introuvable sur le système Adobe Identity Management (IMS) pour l’ID d’organisation utilisé (ou si l’ID IMS ne peut pas être récupéré pour une autre raison), l’utilisateur ou le groupe en question est migré mais n’est pas mappé.

1. Si l’utilisateur est actuellement désactivé, il est traité de la même manière que s’il n’était pas désactivé. Il est mappé et migré normalement et reste désactivé sur l’instance cloud.

1. Si un utilisateur existe sur l’instance AEM Cloud Service cible avec le même nom d’utilisateur (rep:principalName) que l’un des utilisateurs sur l’instance AEM source, l’utilisateur ou le groupe en question n’est pas migré.

1. Si un utilisateur ou une utilisatrice est migré sans avoir au préalable été mappé via le mappage utilisateur, sur le système cloud cible, il ou elle ne pourra pas se connecter à l’aide de son identifiant IMS.  La connexion sera possible à l’aide de la méthode AEM traditionnelle, mais gardez à l’esprit que ce n’est normalement pas ce qui est recherché ou attendu.

## Considérations supplémentaires {#additional-considerations}

* Si le paramètre **Effacer le contenu existant sur l’instance cloud avant l’ingestion** est définie, les utilisateurs déjà transférés sur l’instance de Cloud Service sont supprimés avec l’ensemble du référentiel existant et un nouveau référentiel est créé pour ingérer du contenu dans . Cette opération réinitialise également tous les paramètres, y compris les autorisations sur l’instance Cloud Service cible, et est effective pour un utilisateur administrateur ajouté au groupe **administrateurs**. L’utilisateur administrateur doit être réajouté au groupe **administrateurs** pour récupérer le jeton d’accès à l’outil de transfert de contenu (CTT).

* Il est recommandé de supprimer tout utilisateur existant de l’instance d’AEM Cloud Service cible avant d’exécuter CTT avec mappage des utilisateurs. Cela permet d’éviter tout conflit entre la migration des utilisateurs de l’instance AEM source vers l’instance AEM cible. Des conflits surviendront lors de l’ingestion si un même utilisateur existe sur l’instance AEM source et l’instance AEM cible.

* Lorsque des rechargements de contenu sont effectués, si le contenu n’est pas transféré parce qu’il n’a pas été modifié depuis le transfert précédent, les utilisateurs et les groupes associés à ce contenu ne seront pas transférés non plus, même si les utilisateurs et les groupes ont changé entre-temps. En effet, les utilisateurs et les groupes font l’objet d’un migration avec le contenu auquel ils sont associés.

* Si l’instance AEM Cloud Service cible comporte un utilisateur avec un nom d’utilisateur différent mais la même adresse électronique que l’un des utilisateurs sur l’instance d’AEM source et que le mappage d’utilisateur est activé, un message d’erreur est écrit dans les journaux et l’utilisateur de l’AEM source ne sera pas transféré, car un seul utilisateur avec une adresse électronique donnée est autorisé sur le système cible.

* Si deux utilisateurs de l’instance d’AEM source ont la même adresse électronique et que le mappage des utilisateurs est activé, un message d’erreur est écrit dans les journaux et l’un des utilisateurs d’AEM source ne sera pas transféré, car un seul utilisateur disposant d’une adresse électronique donnée est autorisé sur le système cible.

### Prochaines étapes {#whats-next}

Une fois que vous aurez pris connaissance des principales considérations et des cas exceptionnels, vous serez prêt à utiliser l’outil. Pour plus d’informations, consultez [Utilisation de l’outil de mappage des utilisateurs](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/using-user-mapping-tool-legacy.md).
