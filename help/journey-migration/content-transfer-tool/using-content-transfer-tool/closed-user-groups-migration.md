---
title: Migration des groupes d’utilisateurs et utilisatrices fermés
description: Découvrez les points à prendre en compte pour activer les groupes d’utilisateurs fermés après la migration de contenu vers Adobe Experience Manager as a Cloud Service.
hide: true
hidefromtoc: true
exl-id: f62ed751-d5e2-4a01-8910-c844afab5733
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 10%

---

# Migration des groupes d’utilisateurs et utilisatrices fermés {#migrating-closed-user-groups}

>[!CONTEXTUALHELP]
>id="aemcloud_cug_migration"
>title="Migration de groupes d’utilisateurs et utilisatrices fermés"
>abstract="La migration des groupes d’utilisateurs et utilisatrices fermés (CUG) nécessite actuellement quelques vérifications et étapes pour être opérationnelle après une migration."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/closed-user-groups.html?lang=fr" text="Groupes d’utilisateurs fermés dans AEM"

Actuellement, les groupes d’utilisateurs fermés (CUG) ont besoin de certaines étapes supplémentaires pour être fonctionnels dans l’environnement de destination d’une migration. Ce document explique le scénario et les étapes requises pour leur permettre de protéger les noeuds de la manière prévue.

## Migration des groupes

Les entités principales (y compris les groupes) sont automatiquement incluses dans une migration vers Adobe Experience Manager as a Cloud Service si elles sont associées au contenu migré via l’ACL de ce contenu, et elles sont également incluses si elles sont référencées dans une stratégie de CUG sur ce contenu.

## Groupes d’utilisateurs fermés dans la migration

La vérification du groupe et de ses membres doit être effectuée avant la mise en ligne. Le rapport Principal, téléchargé via la vue Tâche d’ingestion, peut être utilisé pour déterminer si le groupe en question a été inclus ou non parce qu’il ne faisait pas partie d’une liste de contrôle d’accès ou d’une stratégie de CUG.

Ensuite, les processus doivent être déclenchés et les propriétés doivent être définies pour activer les CUG. Pour ce faire, republiez toutes les pages associées à une stratégie de CUG. Cette opération calibre l’instance de publication pour effectuer le suivi des stratégies.

Cela active les stratégies de CUG lors de la publication et le contenu n’est accessible que pour les utilisateurs authentifiés qui sont membres du groupe associé aux stratégies.

## Résumé

En résumé, voici les étapes pour activer CUG après une migration :

1. Assurez-vous que chaque groupe utilisé dans les stratégies de CUG existe sur Publier après la migration.
   - Un groupe peut exister s’il est inclus dans la stratégie de CUG d’un contenu migré ou dans la liste de contrôle d’accès de ce contenu.
   - Si ce n’est pas le cas, utilisez Packages pour l’installer sur l’instance de destination (ou créez-la manuellement) et l’activer ainsi que ses membres. Vérifiez ensuite qu’il existe sur la publication.
1. Republiez toutes les pages associées à une stratégie de CUG, en vous assurant qu’elles sont publiées, par exemple en modifiant d’abord la page. Il est important de tous les republier.
   - Une fois toutes les pages republiées, vérifiez la fonctionnalité de chaque page protégée par un groupe d’utilisateurs fermé.
