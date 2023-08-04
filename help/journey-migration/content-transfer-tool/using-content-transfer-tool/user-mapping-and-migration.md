---
title: Mappage des utilisateurs et utilisatrices et migration des entités principales
description: Présentation du mappage des utilisateurs et de la migration des entités de sécurité dans AEM as a Cloud Service.
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
source-git-commit: 8c73805b6ed1b7a03c65b4d21a4252c1412a5742
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 22%

---

# Mappage des utilisateurs et utilisatrices et migration des entités principales {#user-mapping-and-principal-migration}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="Mappage des utilisateurs"
>abstract="L’outil de transfert de contenu vous permet de déplacer des utilisateurs, des utilisatrices et des groupes de votre système Adobe Experience Manager (AEM) existant vers AEM as a Cloud Service. Les utilisateurs existantes doivent être mappés à leurs identifiants IMS pour éviter qu’ils ne soient dupliqués sur l’instance de création de Cloud Service."

>[!NOTE]
>Pour les versions précédentes de l’outil de mappage des utilisateurs, consultez la [documentation des versions antérieures](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md).

## Présentation {#introduction}

Dans le cadre du parcours de transition vers Adobe Experience Manager (AEM) as a Cloud Service, vous devez déplacer les utilisateurs et les groupes de votre système AEM existant vers l’as a Cloud Service. Cette tâche est effectuée par l’outil de transfert de contenu.

L’un des changements majeurs apportés à AEM as a Cloud Service est l’utilisation entièrement intégrée des Adobe ID pour l’accès au niveau création. Ce processus nécessite l’utilisation de la fonction [Adobe Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html) pour la gestion des utilisateurs et des groupes d’utilisateurs. Les informations de profil utilisateur sont centralisées dans Adobe Identity Management System (IMS), qui permet l’authentification unique dans toutes les applications cloud d’Adobe. Pour plus d’informations, voir [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html#identity-management). En raison de cette modification, les utilisateurs existants doivent être mappés à leurs identifiants IMS afin d’éviter les doublons d’utilisateurs sur l’instance d’auteur du Cloud Service. Puisque les groupes de la plateforme AEM traditionnelle sont fondamentalement différents de ceux dans IMS, ils ne sont pas mappés, mais les deux ensembles de groupes doivent être réconciliés une fois la migration terminée.

## Détails de la migration des utilisateurs {#user-migration-detail}

L’outil de transfert de contenu et Cloud Acceleration Manager migreront vers le système cloud tous les utilisateurs associés au contenu en cours de migration.

## Détails du mappage des utilisateurs {#user-mapping-detail}

Les utilisateurs AEM peuvent être mappés aux utilisateurs Adobe IMS correspondants avec la même adresse électronique.  Ce mappage peut être effectué automatiquement dans le CTT et son exécution peut être contrôlée par un bouton bascule avant le démarrage de l’extraction. Le paramètre par défaut du bouton (bascule) peut être remplacé par l’utilisateur ou l’utilisatrice lors du démarrage de l’extraction.

* Si le système source est une instance d’auteur, le choix par défaut d’effectuer le mappage est _on_, car il s’agit du processus recommandé.
* Si le système source est une instance de publication, le choix par défaut d’effectuer le mappage est _off_, car les utilisateurs ne sont normalement pas migrés ou utilisés sur les instances de publication.

## Points importants lors du mappage et de la migration d’utilisateurs et d’utilisatrices {#important-considerations}


### Cas exceptionnels {#exceptional-cases}

Les cas spécifiques suivants sont consignés :

1. Si un utilisateur ne dispose d’aucune adresse électronique dans la variable `profile/email` de leur champ *jcr* , l’utilisateur ou le groupe en question peut être migré, mais n’est pas mappé. Ce scénario est le cas même si l’adresse électronique est utilisée comme nom d’utilisateur pour la connexion.

1. Si l’utilisateur ou l’utilisatrice est désactivé, le traitement est le même que s’il ou elle ne l’était pas. Il ou elle fera l’objet d’une migration et d’un mappage normaux et restera désactivé(e) sur l’instance cloud.

1. Si un utilisateur existe sur l’instance AEM Cloud Service cible avec le même nom d’utilisateur (rep:principalName) que l’un des utilisateurs sur l’instance d’AEM source, l’utilisateur en question n’est pas migré.

1. Si un utilisateur est migré sans être mappé au moyen du mappage utilisateur, il ne peut pas se connecter à l’aide de son identifiant IMS sur le système cloud cible. Ou, si leur adresse électronique ne correspond pas à celle utilisée pour se connecter à IMS, sur le système cloud cible, ils ne peuvent pas non plus se connecter à l’aide de leur identifiant IMS. Il est possible qu’ils puissent se connecter à l’aide de la méthode d’AEM traditionnelle, mais cette méthode n’est normalement pas ce qui est recherché ou attendu.


## Considérations supplémentaires {#additional-considerations}

* Si le paramètre **Effacer le contenu existant sur l’instance cloud avant l’ingestion** est définie, les utilisateurs déjà transférés sur l’instance de Cloud Service sont supprimés avec l’ensemble du référentiel existant. De plus, un nouveau référentiel est créé dans lequel le contenu est ingéré. Ce processus réinitialise également tous les paramètres, y compris les autorisations sur l’instance de Cloud Service cible. Il est vrai pour un utilisateur administrateur ajouté à la variable **administrateurs** groupe. L’utilisateur administrateur doit être lu dans la variable **administrateurs** pour récupérer le jeton d’accès pour CTT.
* Lorsque des compléments de contenu sont effectués, si le contenu n’est pas transféré car il n’a pas été modifié depuis le transfert précédent, les utilisateurs et les groupes associés à ce contenu ne sont pas transférés non plus. Cette règle est vraie même si les utilisateurs et les groupes ont changé entre-temps. Cela est dû au fait que les utilisateurs et les groupes sont migrés avec le contenu auquel ils sont associés.
* Si l’instance AEM Cloud Service cible comporte un utilisateur avec un nom d’utilisateur différent mais la même adresse électronique que l’un des utilisateurs sur l’instance d’AEM source et que le mappage utilisateur est activé, les journaux enregistrent un message d’erreur. En outre, l’utilisateur de l’AEM source n’est pas transféré, car un seul utilisateur disposant d’une adresse électronique donnée est autorisé sur le système cible.

## Résumé final et rapport {#final-report}

Une fois l’extraction et l’ingestion terminées, un rapport est généré avec les principaux détails de migration. Voir [Validation de la migration des entités de sécurité](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/validating-content-transfers.md#how-to-validate-principal-migration) pour plus de détails.
