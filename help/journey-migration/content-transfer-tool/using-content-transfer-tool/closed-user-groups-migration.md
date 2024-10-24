---
title: Migration des groupes d’utilisateurs et utilisatrices fermés
description: Découvrez les points à prendre en compte pour activer les groupes d’utilisateurs fermés après la migration de contenu vers Adobe Experience Manager as a Cloud Service.
hide: true
hidefromtoc: true
exl-id: f62ed751-d5e2-4a01-8910-c844afab5733
feature: Migration
role: Admin
source-git-commit: c721a8db801602389822222b08ca4ea1fd2293e4
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 13%

---


# Migration des groupes d’utilisateurs et utilisatrices fermés {#migrating-closed-user-groups}

>[!CONTEXTUALHELP]
>id="aemcloud_cug_migration"
>title="Migrer des groupes d’utilisateurs et utilisatrices fermés"
>abstract="La migration des groupes d’utilisateurs et utilisatrices fermés (CUG) nécessite actuellement quelques vérifications et étapes pour être opérationnelle après une migration."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/closed-user-groups.html?lang=fr" text="Groupes d’utilisateurs fermés dans AEM"

Actuellement, les groupes d’utilisateurs fermés (CUG) ont besoin de certaines étapes supplémentaires pour être fonctionnels dans l’environnement de destination d’une migration. Ce document explique le scénario et les étapes requises pour leur permettre de protéger les noeuds de la manière prévue.

## Migration des groupes d’utilisateurs fermés (CUG)

Les groupes sont automatiquement inclus dans une migration CTT/CAM vers Adobe Experience Manager as a Cloud Service s’ils sont associés au contenu migré via l’ACL de ce contenu ou son noeud de stratégie de CUG. Vérifier que le groupe et ses membres existent doit être fait avant la mise en ligne. Les groupes référencés sur une stratégie de CUG sont appelés &quot;groupes de CUG&quot;.

Pour utiliser des groupes d’utilisateurs fermés dans AEM as a Cloud Service, les utilisateurs doivent être présents sur l’instance d’auteur et faire partie des groupes de groupes d’utilisateurs fermés appropriés.  Cela peut être réalisé à l’aide de packages, ou si les utilisateurs de CUG sont des utilisateurs IMS, ils sont peut-être déjà présents.  Les utilisateurs de CUG doivent alors être membres des groupes de CUG AEM.

Pour activer le comportement des CUG sur l’instance Publish,
1. Les groupes de CUG doivent être activés (qui les répliquent, ainsi que leurs membres, sur l’instance Publish),
1. *Toutes les* pages protégées par des stratégies de CUG doivent être dépubliées (pour effacer le nombre de CUG globaux) et
1. Les pages protégées par des stratégies de CUG doivent ensuite être publiées (ce qui permet à l’instance Publish et de suivre les stratégies).
1. Une fois toutes les pages publiées, vérifiez la fonctionnalité de chaque page protégée par un groupe d’utilisateurs fermé.

Pour plus d’informations, voir [Groupes d’utilisateurs fermés](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/closed-user-groups.html?lang=fr).
