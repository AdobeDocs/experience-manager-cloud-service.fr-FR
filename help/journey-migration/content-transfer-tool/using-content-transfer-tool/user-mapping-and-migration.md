---
title: Mappage des utilisateurs et utilisatrices et migration des entités principales
description: Présentation du mappage des utilisateurs et de la migration des entités de sécurité dans AEM as a Cloud Service.
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
source-git-commit: bf1260f9a49012bbcb4138e0a5498d8dda451b6a
workflow-type: tm+mt
source-wordcount: '1060'
ht-degree: 24%

---

# Mappage des utilisateurs et utilisatrices et migration des entités principales {#user-mapping-and-principal-migration}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="Migration des utilisateurs"
>abstract="L’outil de transfert de contenu vous permet de déplacer des utilisateurs, des utilisatrices et des groupes de votre système Adobe Experience Manager (AEM) existant vers AEM as a Cloud Service. Les utilisateurs existants doivent être mappés afin de pouvoir se connecter via leurs identifiants IMS."

>[!NOTE]
>Pour les versions précédentes de l’outil de mappage des utilisateurs, consultez la [documentation des versions antérieures](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md).

## Présentation {#introduction}

Dans le cadre du parcours de transition vers Adobe Experience Manager (AEM) as a Cloud Service, les utilisateurs et les groupes (ou &quot;entités de sécurité&quot;) doivent être migrés des systèmes AEM existants vers les systèmes as a Cloud Service. Cette tâche est effectuée par l’outil de transfert de contenu.

L’un des changements majeurs apportés à AEM as a Cloud Service est l’utilisation entièrement intégrée des Adobe ID pour l’accès au niveau création. Ce processus nécessite l’utilisation d’[Adobe Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html) pour la gestion des utilisateurs et utilisatrices, et des groupes d’utilisateurs et utilisatrices. Les informations de profil utilisateur sont centralisées dans Adobe Identity Management System (IMS), qui permet l’authentification unique dans toutes les applications cloud d’Adobe. Pour plus d’informations, voir [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html?lang=fr#identity-management). En raison de cette modification, les utilisateurs existants doivent être mappés à leurs identifiants IMS afin de pouvoir accéder à AEMaaCS à l’aide de leurs profils IMS. Puisque les groupes de la plateforme AEM traditionnelle sont fondamentalement différents de ceux dans IMS, ils ne sont pas mappés, mais les deux ensembles de groupes doivent être réconciliés une fois la migration terminée.

## Détails de la migration des principaux {#principal-migration-detail}

L’outil de transfert de contenu et Cloud Acceleration Manager migreront vers le système cloud toutes les entités associées au contenu en cours de migration. L’outil de transfert de contenu effectue cette opération en copiant toutes les entités du système d’AEM source pendant le processus d’extraction. L’ingestion CAM sélectionne et migre ensuite uniquement les entités associées au contenu ingéré. Si une entité de sécurité se trouve sur une règle ACL ou CUG du contenu migré, cette entité de sécurité et tous les groupes dans lesquels elle se trouve et leurs groupes parents (ancêtres) seront migrés. De plus, si une entité de sécurité sur le contenu est un groupe, tous ses groupes et utilisateurs descendants (enfants) seront également migrés.

## Détails du mappage des utilisateurs et utilisatrices {#user-mapping-detail}

Les utilisateurs AEM peuvent être mappés aux utilisateurs Adobe IMS correspondants avec la même adresse électronique. Ce mapping peut être effectué automatiquement dans CTT (lors de l’étape d’extraction) et s’il est effectué ou non peut être contrôlé par un bouton bascule avant le démarrage de l’extraction. Le paramètre par défaut du bouton (bascule) peut être remplacé par l’utilisateur ou l’utilisatrice lors du démarrage de l’extraction.

* Si le système source est une instance de création, le choix par défaut consistant à effectuer le mappage est _activé_, puisqu’il s’agit du processus recommandé.
* Si le système source est une instance de publication, le choix par défaut d’effectuer le mappage est _off_, car les utilisateurs ne sont normalement pas migrés ou utilisés sur les instances de publication ; ou s’ils sont utilisés, un autre système d’authentification (c’est-à-dire pas IMS) est généralement utilisé pour eux.

Que les utilisateurs soient mappés ou non lors de l’extraction, ils sont migrés, avec les groupes, vers le système cloud lors de l’ingestion s’ils sont associés au contenu en cours de migration.

## Points importants lors du mappage et de la migration d’utilisateurs et d’utilisatrices {#important-considerations}

### Cas exceptionnels {#exceptional-cases}

Les cas spécifiques suivants sont consignés :

1. Si un utilisateur ne dispose d’aucune adresse électronique dans la variable `profile/email` de leur champ *jcr* , l’utilisateur en question peut être migré, mais n’est pas mappé. Ce scénario est valable même si l’adresse e-mail est utilisée comme nom d’utilisateur pour la connexion.
2. Si l’utilisateur est désactivé, il est traité de la même manière que les autres utilisateurs ; il est mappé et migré normalement et reste désactivé sur l’instance cloud.
3. Si une entité existe avec les mêmes données contraintes d’unicité (rep:principalName, rep:authorizableId, jcr:uuid ou rep:externalId) sur l’instance d’AEM source et l’instance AEM Cloud Service cible, l’entité en question n’est pas migrée et l’entité existante précédemment sur le système cloud reste inchangée. Il est consigné dans le rapport Migration de l’entité principale.
4. Si un utilisateur n’est pas mappé à IMS via un mappage utilisateur, le profil utilisateur sur le système d’AEM cloud ne sera pas reconnu par IMS ; dans ce cas, s’il se connecte via IMS, un nouveau profil (en double) sera créé sur AEM, mais il ne contiendra pas les informations de son profil précédent. Le profil utilisateur d’origine existe sur le système d’AEM cloud, mais il ne pourra pas s’y connecter via IMS, en utilisant uniquement la méthode AEM traditionnelle (connexion locale). Pour cette raison, il est vivement recommandé de mapper tous les utilisateurs pour toutes les migrations de création.

## Considérations supplémentaires {#additional-considerations}

* Si le paramètre **Effacer le contenu existant sur l’instance cloud avant l’ingestion** est définie, les entités précédemment transférées vers l’instance de Cloud Service sont supprimées avec l’ensemble du référentiel existant ; un nouveau référentiel est créé dans lequel le contenu est ingéré. Ce processus réinitialise également tous les paramètres, y compris les autorisations, sur l’instance du service cloud cible et s’applique à une personne utilisatrice en charge de l’aministration ajoutée au groupe d’**administration**. L’utilisateur administrateur doit être rajouté au **administrateurs** groupe pour récupérer le jeton d’accès pour l’ingestion CTT/CAM.
* Lorsque des assimilations non effacées sont effectuées (**Effacer le contenu existant** n’est pas définie), si le contenu n’est pas transféré car il n’a pas été modifié depuis le transfert précédent, les utilisateurs et les groupes associés à ce contenu ne sont pas transférés non plus. Cette règle est vraie même si les utilisateurs et les groupes ont changé sur le système source. En effet, les utilisateurs et les groupes ne sont migrés qu’avec le contenu auquel ils sont associés. Pour cette raison, les entités qui ne viennent pas d’entrer dans un groupe sur le système source ne seront pas migrées à moins qu’elles ne fassent partie d’un groupe différent qui est en cours de migration ou dans l’ACL de contenu différent en cours de migration. Pour migrer ensuite ces entités, envisagez d’utiliser des packages ou de supprimer des entités de la cible et de rémigrer le contenu approprié (Extraire avec remplacement et Ingérer avec effacement).
* Les adresses email en double ne sont pas autorisées dans IMS, mais elles sont autorisées dans AEM (à la fois sur site et dans le cloud). Un utilisateur peut se connecter à AEM via IMS à l’aide de son adresse électronique et il sera connecté au profil utilisateur référencé par IMS.
* Voir [Migration des groupes d’utilisateurs fermés](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md) pour plus d’informations sur les entités utilisées dans une stratégie de groupe d’utilisateurs fermé (CUG).

## Résumé final et rapport {#final-report}

Une fois l’extraction et l’ingestion terminées, un rapport est généré avec les détails de la migration des entités principales. Voir [Comment valider la migration des entités principales](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/validating-content-transfers.md#how-to-validate-principal-migration) pour plus de détails.
