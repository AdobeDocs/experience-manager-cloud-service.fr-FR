---
title: Mappage des utilisateurs et utilisatrices et migration des entités principales
description: Présentation du mappage des utilisateurs et des utilisatrices et de la migration des entités principales
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
source-git-commit: 9cff6e94b38016f008fd8177be2e071a530d80b6
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 100%

---

# Mappage des utilisateurs et utilisatrices et migration des entités principales {#user-mapping-and-principal-migration}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="Mappage des utilisateurs"
>abstract="L’outil de transfert de contenu vous permet de déplacer des utilisateurs et des utilisatrices et des groupes de votre système AEM existant vers AEM as a Cloud Service. Les utilisateurs existantes doivent être mappés à leurs identifiants IMS pour éviter qu’ils ne soient dupliqués sur l’instance de création de Cloud Service."

>[!NOTE]
>Pour les versions précédentes de l’outil de mappage des utilisateurs, consultez la [documentation des versions antérieures](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md).

## Présentation {#introduction}

Dans le cadre du parcours de transition vers Adobe Experience Manager (AEM) as a Cloud Service, vous devez déplacer les utilisateurs et les groupes du système AEM existant vers AEM as a Cloud Service. Cette opération fait appel à l’outil de transfert de contenu.

L’un des changements majeurs apportés à AEM as a Cloud Service est l’utilisation entièrement intégrée des Adobe ID pour l’accès au niveau création. Pour ce faire, vous devez utiliser [Adobe Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html) afin de gérer les utilisateurs et les groupes d’utilisateurs. Les informations de profil d’utilisateur sont centralisées dans le système Adobe IMS (Identity Management System), qui permet l’authentification unique pour toutes les applications de cloud d’Adobe. Pour plus d’informations, consultez [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html?lang=fr#identity-management). En raison de cette modification, les utilisateurs et utilisatrices existants doivent être mappés avec leurs identifiants IMS pour éviter qu’ils ne soient dupliqués sur l’instance de création Cloud Service. Puisque les groupes de la plateforme AEM traditionnelle sont fondamentalement différents de ceux dans IMS, ils ne sont pas mappés, mais les deux ensembles de groupes doivent être réconciliés une fois la migration terminée.

## Mappage des utilisateurs et des utilisatrices et détails de migration {#user-mapping-detail}

L’outil de transfert de contenu et Cloud Acceleration Manager migrent tous les utilisateurs et utilisatrices associés au contenu en cours de migration. Ce mappage est effectué automatiquement et son exécution peut être contrôlée par un bouton (bascule) avant le démarrage de l’extraction. Le paramètre par défaut du bouton (bascule) peut être remplacé par l’utilisateur ou l’utilisatrice lors du démarrage de l’extraction.

* Si le système source est une instance de création, le choix par défaut consistant à effectuer le mappage est _activé_, puisqu’il s’agit du processus recommandé.
* Si le système source est une instance de publication, le choix par défaut consistant à procéder au mappage est _désactivé_, car les utilisateurs et utilisatrices ne sont normalement pas migrés ni utilisés sur les instances de publication.

## Points importants lors du mappage et de la migration d’utilisateurs et d’utilisatrices {#important-considerations}


### Cas exceptionnels {#exceptional-cases}

Les cas spécifiques suivants sont consignés :

1. Si un utilisateur ou une utilisatrice n’a pas d’adresse e-mail dans le champ `profile/email` de son nœud *jcr*, l’utilisateur, l’utilisatrice ou le groupe en question sera migré, mais pas mappé. C’est le cas même si l’adresse e-mail est utilisée comme nom d’utilisateur pour la connexion.

1. Si l’utilisateur ou l’utilisatrice est désactivé, le traitement est le même que s’il ou elle ne l’était pas. Il ou elle fera l’objet d’une migration et d’un mappage normaux et restera désactivé(e) sur l’instance cloud.

1. Si un utilisateur ou une utilisatrice existe sur l’instance d’AEM Cloud Service cible avec le même nom d’utilisateur (rep:principalName) que l’un des utilisateurs ou une des utilisatrices de l’instance d’AEM source, l’utilisateur, l’utilisatrice ou le groupe en question ne sera pas migré(e).

1. Si un utilisateur ou une utilisatrice est migré sans avoir au préalable été mappé via le mappage utilisateur ou si son adresse e-mail ne correspond pas à celle utilisée pour se connecter à IMS sur le système cloud cible, il ou elle ne pourra pas se connecter à l’aide de son identifiant IMS. La connexion sera possible à l’aide de la méthode AEM traditionnelle, mais gardez à l’esprit que ce n’est normalement pas ce qui est recherché ou attendu.


## Considérations supplémentaires {#additional-considerations}

* Si le paramètre **Effacer le contenu existant sur l’instance cloud avant l’ingestion** est défini, les utilisateurs déjà transférés sur l’instance de Cloud Service seront supprimés avec l’ensemble du référentiel existant, et un nouveau référentiel sera créé pour intégrer du contenu. Cette opération réinitialise également tous les paramètres, y compris les autorisations sur l’instance Cloud Service cible, et est effective pour un utilisateur administrateur ajouté au groupe **administrateurs**. La personne en charge de l’administration doit être réajoutée au groupe **administrateurs** pour récupérer le jeton d’accès à l’outil de transfert de contenu.
* Lorsque des rechargements de contenu sont effectués, si le contenu n’est pas transféré parce qu’il n’a pas été modifié depuis le transfert précédent, les utilisateurs, les utilisatrices et les groupes associés à ce contenu ne seront pas transférés non plus, même s’ils ont changé entre-temps. En effet, les utilisateurs, les utilisatrices et les groupes font l’objet d’une migration avec le contenu auquel ils sont associés.
* Si l’instance AEM Cloud Service cible a un utilisateur ou une utilisatrice avec un nom d’utilisateur différent, mais la même adresse e-mail que l’un des utilisateurs ou l’une des utilisatrices de l’instance AEM source, et que le mappage des utilisateurs est activé, un message d’erreur est consigné dans les journaux et l’utilisateur ou l’utilisatrice AEM source n’est pas transféré(e), car un seul utilisateur ou une seule utilisatrice avec une adresse e-mail donnée est autorisé(e) sur le système cible.
