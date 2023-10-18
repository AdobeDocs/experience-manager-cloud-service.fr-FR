---
title: Mappage des utilisateurs et utilisatrices et migration des entités principales
description: Présentation du mappage des utilisateurs et de la migration des entités de sécurité dans AEM as a Cloud Service.
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
source-git-commit: 2fdfb65543fa2942e809aa5d379f4000e40bd517
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 47%

---

# Mappage des utilisateurs et utilisatrices et migration des entités principales {#user-mapping-and-principal-migration}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="Mappage des utilisateurs et des utilisatrices"
>abstract="L’outil de transfert de contenu vous permet de déplacer des utilisateurs, des utilisatrices et des groupes de votre système Adobe Experience Manager (AEM) existant vers AEM as a Cloud Service. Les utilisateurs existantes doivent être mappés à leurs identifiants IMS pour éviter qu’ils ne soient dupliqués sur l’instance de création de Cloud Service."

>[!NOTE]
>Pour les versions précédentes de l’outil de mappage des utilisateurs, consultez la [documentation des versions antérieures](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md).

## Présentation {#introduction}

Dans le cadre du parcours de transition vers Adobe Experience Manager (AEM) as a Cloud Service, les utilisateurs et les groupes (ou &quot;entités de sécurité&quot;) doivent être migrés des systèmes AEM existants vers les systèmes as a Cloud Service. Cette tâche est effectuée par l’outil de transfert de contenu.

L’un des changements majeurs apportés à AEM as a Cloud Service est l’utilisation entièrement intégrée des Adobe ID pour l’accès au niveau création. Ce processus nécessite l’utilisation d’[Adobe Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html) pour la gestion des utilisateurs et utilisatrices, et des groupes d’utilisateurs et utilisatrices. Les informations relatives au profil utilisateur sont centralisées dans Identity Management System (IMS) d’Adobe, qui permet une authentification unique à toutes les applications cloud d’Adobe. Pour plus d’informations, voir [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html?lang=fr#identity-management). En raison de cette modification, les utilisateurs existants doivent être mappés à leurs identifiants IMS pour éviter la création d’utilisateurs en double sur l’instance de création du Cloud Service. Puisque les groupes de la plateforme AEM traditionnelle sont fondamentalement différents de ceux dans IMS, ils ne sont pas mappés, mais les deux ensembles de groupes doivent être réconciliés une fois la migration terminée.

## Détails de la migration des principaux {#principal-migration-detail}

L’outil de transfert de contenu et Cloud Acceleration Manager migreront vers le système cloud toutes les entités associées au contenu en cours de migration.  L’outil de transfert de contenu effectue cette opération en copiant toutes les entités du système d’AEM source pendant le processus d’extraction.  L’ingestion CAM sélectionne et migre ensuite uniquement les entités associées au contenu ingéré.

## Détails du mappage des utilisateurs et utilisatrices {#user-mapping-detail}

Les utilisateurs et utilisatrices AEM peuvent être mappés aux utilisateurs et utilisatrices Adobe IMS correspondants avec la même adresse e-mail.  Ce mapping peut être effectué automatiquement dans CTT (lors de l’étape d’extraction) et s’il est effectué ou non peut être contrôlé par un bouton bascule avant le démarrage de l’extraction. Le paramètre par défaut du bouton (bascule) peut être remplacé par l’utilisateur ou l’utilisatrice lors du démarrage de l’extraction.

* Si le système source est une instance de création, le choix par défaut consistant à effectuer le mappage est _activé_, puisqu’il s’agit du processus recommandé.
* Si le système source est une instance de publication, le choix par défaut d’effectuer le mappage est _off_, car les utilisateurs ne sont normalement pas migrés ou utilisés sur les instances de publication ; ou s’ils sont utilisés, un autre système d’authentification (c’est-à-dire pas IMS) est généralement utilisé à leur place.

Que les utilisateurs soient mappés ou non lors de l’extraction, ils sont migrés, avec les groupes, vers le système cloud lors de l’ingestion s’ils sont associés au contenu en cours de migration.

## Points importants lors du mappage et de la migration d’utilisateurs et d’utilisatrices {#important-considerations}

### Cas exceptionnels {#exceptional-cases}

Les cas spécifiques suivants sont consignés :

1. Si un utilisateur ou une utilisatrice n’a pas d’adresse e-mail dans le champ `profile/email` de son nœud *jcr*, l’utilisateur, l’utilisatrice ou le groupe en question peut être migré, mais pas mappé. Ce scénario est valable même si l’adresse e-mail est utilisée comme nom d’utilisateur pour la connexion.
2. Si l’utilisateur est désactivé, il est traité de la même manière que les autres utilisateurs ; il est mappé et migré normalement et reste désactivé sur l’instance cloud.
3. Si une entité porte le même nom (rep:principalName) sur l’instance d’AEM source et l’instance AEM Cloud Service cible, l’entité en question n’est pas migrée et l’entité existante précédemment sur le système cloud reste inchangée.
4. Si un utilisateur est migré sans être mappé au moyen du mappage utilisateur, l’utilisateur ne pourra pas se connecter à l’aide de son identifiant IMS sur le système cloud cible. Ou, si leur adresse électronique ne correspond pas à celle utilisée pour se connecter à IMS, sur le système cloud cible, ils ne pourront pas non plus se connecter à l’aide de leur identifiant IMS. Ils peuvent se connecter à l’aide de la méthode d’AEM traditionnelle (connexion locale), mais cette méthode n’est normalement pas ce qui est recherché ou attendu.

## Considérations supplémentaires {#additional-considerations}

* Si le paramètre **Effacer le contenu existant sur l’instance cloud avant l’ingestion** est définie, les utilisateurs déjà transférés sur l’instance de Cloud Service sont supprimés avec l’ensemble du référentiel existant ; un nouveau référentiel est créé dans lequel le contenu est ingéré. Ce processus réinitialise également tous les paramètres, y compris les autorisations, sur l’instance du service cloud cible et s’applique à une personne utilisatrice en charge de l’aministration ajoutée au groupe d’**administration**. L’utilisateur administrateur doit être rajouté au **administrateurs** groupe pour récupérer le jeton d’accès pour l’ingestion CTT/CAM.
* Lorsque des rechargements de contenu sont effectués, si le contenu n’est pas transféré parce qu’il n’a pas été modifié depuis le transfert précédent, les utilisateurs, les utilisatrices et les groupes associés à ce contenu ne seront pas transférés non plus. Cette règle est vraie même si les utilisateurs et les groupes ont changé sur le système source. Cela est dû au fait que les utilisateurs et les groupes ne sont migrés qu’avec le contenu auquel ils sont associés.
* Si l’instance AEM Cloud Service cible a un utilisateur ou une utilisatrice avec un nom d’utilisateur différent, mais la même adresse e-mail que l’un des utilisateurs ou l’une des utilisatrices de l’instance AEM source, et que le mappage des utilisateurs et utilisatrices est activé, un message d’erreur est consigné dans les journaux. En outre, l’utilisateur ou utilisatrice d’AEM source n’est pas transféré, car seul un utilisateur ou une utilisatrice disposant d’une adresse e-mail donnée est autorisé sur le système cible.
* Voir [Migration des groupes d’utilisateurs fermés](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md) pour plus d’informations sur les entités utilisées dans une stratégie de groupe d’utilisateurs fermé (CUG).

## Résumé final et rapport {#final-report}

Une fois l’extraction et l’ingestion terminées, un rapport est généré avec les détails de la migration des entités principales. Voir [Comment valider la migration des entités principales](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/validating-content-transfers.md#how-to-validate-principal-migration) pour plus de détails.
