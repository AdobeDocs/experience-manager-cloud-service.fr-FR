---
title: Mappage des utilisateurs et migration des entités de sécurité
description: Présentation du mappage des utilisateurs et de la migration des entités principales
source-git-commit: 5475f9995513d09e61bd8f52242b3e74b8d4694c
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 32%

---

# Mappage des utilisateurs et migration des entités de sécurité {#user-mapping-and-principal-migration}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="Mappage des utilisateurs"
>abstract="L’outil de transfert de contenu vous permet de déplacer des utilisateurs et des groupes de votre système AEM existant vers AEM as a Cloud Service. Les utilisateurs existantes doivent être mappés à leurs identifiants IMS pour éviter qu&#39;ils ne soient dupliqués sur l&#39;instance de création de Cloud Service."

>[!NOTE]
>Pour connaître les versions précédentes de l’outil de mappage des utilisateurs, reportez-vous à la section [documentation héritée](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md).

## Présentation {#introduction}

Dans le cadre du parcours de transition vers Adobe Experience Manager (AEM) as a Cloud Service, vous devez déplacer les utilisateurs et les groupes du système AEM existant vers AEM as a Cloud Service. Cette opération fait appel à l’outil de transfert de contenu.

L’un des changements majeurs apportés à AEM as a Cloud Service est l’utilisation entièrement intégrée des Adobe ID pour l’accès au niveau création. Pour ce faire, vous devez utiliser [Adobe Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html) afin de gérer les utilisateurs et les groupes d’utilisateurs. Les informations de profil d’utilisateur sont centralisées dans le système Adobe IMS (Identity Management System), qui permet l’authentification unique pour toutes les applications de cloud d’Adobe. Pour plus d’informations, consultez [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html#identity-management). En raison de cette modification, les utilisateurs existants doivent être mappés à leurs identifiants IMS pour éviter les doublons d’utilisateurs sur l’instance d’auteur du Cloud Service. Puisque les groupes des AEM traditionnels sont fondamentalement différents des groupes dans IMS, les groupes ne sont pas mappés, mais les deux ensembles de groupes doivent être réconciliés une fois la migration terminée.

## Mappage des utilisateurs et détails de migration {#user-mapping-detail}

L’outil de transfert de contenu et le Cloud Acceleration Manager migrent tous les utilisateurs associés au contenu en cours de migration. Ce mappage est effectué automatiquement et le fait qu’il soit effectué peut être contrôlé par un bouton bascule avant le démarrage de l’extraction. Le paramètre par défaut du bouton peut être remplacé par l’utilisateur lors du démarrage de l’extraction.

* Si le système source est une instance d’auteur, le choix par défaut d’effectuer le mappage est _on_, puisqu’il s’agit du processus recommandé.
* Si le système source est une instance de publication, le choix par défaut de procéder au mappage est _off_, car les utilisateurs ne sont normalement pas migrés ni utilisés sur les instances de publication.

## Points importants lors du mappage et de la migration d&#39;utilisateurs {#important-considerations}


### Cas exceptionnels {#exceptional-cases}

Les cas spécifiques suivants sont consignés :

1. Si un utilisateur ne dispose d’aucune adresse électronique dans la variable `profile/email` de leur champ *jcr* noeud de l’utilisateur ou du groupe en question peut être migré, mais ne sera pas mappé. C’est le cas même si l’adresse électronique est utilisée comme nom d’utilisateur pour la connexion.

1. Si l’utilisateur est désactivé, il est traité de la même manière que s’il n’était pas désactivé. Il est mappé et migré normalement et reste désactivé sur l’instance cloud.

1. Si un utilisateur existe sur l’instance AEM Cloud Service cible avec le même nom d’utilisateur (rep:principalName) que l’un des utilisateurs sur l’instance d’AEM source, l’utilisateur ou le groupe en question ne sera pas migré.

1. Si un utilisateur est migré sans avoir au préalable été mappé via le mappage utilisateur ou si son adresse électronique ne correspond pas à l’adresse électronique utilisée pour se connecter à IMS, sur le système cloud cible, il ne pourra pas se connecter à l’aide de son identifiant IMS. Ils peuvent se connecter à l’aide de la méthode d’AEM traditionnelle, mais gardez à l’esprit que ce n’est normalement pas ce qui est recherché ou attendu.


## Considérations supplémentaires {#additional-considerations}

* Si le paramètre **Effacer le contenu existant sur l’instance cloud avant l’ingestion** est défini, les utilisateurs déjà transférés sur l’instance de Cloud Service seront supprimés avec l’ensemble du référentiel existant, et un nouveau référentiel sera créé pour intégrer du contenu. Cette opération réinitialise également tous les paramètres, y compris les autorisations sur l’instance Cloud Service cible, et est effective pour un utilisateur administrateur ajouté au groupe **administrateurs**. L’utilisateur administrateur doit être rajouté au **administrateurs** pour récupérer le jeton d’accès pour CTT.
* Lorsque des compléments de contenu sont effectués, si le contenu n’est pas transféré car il n’a pas été modifié depuis le transfert précédent, les utilisateurs et les groupes associés à ce contenu ne sont pas transférés non plus, même si les utilisateurs et les groupes ont changé entre-temps. En effet, les utilisateurs et les groupes font l’objet d’un migration avec le contenu auquel ils sont associés.
* Si l’instance AEM Cloud Service cible comporte un utilisateur avec un nom d’utilisateur différent mais la même adresse électronique que l’un des utilisateurs sur l’instance d’AEM source et que le mappage d’utilisateur est activé, un message d’erreur est écrit dans les journaux et l’utilisateur de l’AEM source n’est pas transféré, car un seul utilisateur avec une adresse électronique donnée est autorisé sur le système cible.
