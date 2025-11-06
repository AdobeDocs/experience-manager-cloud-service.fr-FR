---
title: Migration des groupes d’utilisateurs et utilisatrices fermés
description: Découvrez les points spéciaux à prendre en compte pour activer les groupes d’utilisateurs fermés après la migration du contenu vers Adobe Experience Manager as a Cloud Service.
hide: true
hidefromtoc: true
exl-id: f62ed751-d5e2-4a01-8910-c844afab5733
feature: Migration
role: Admin
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
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

Actuellement, les groupes d’utilisateurs fermés (CUG) nécessitent quelques étapes supplémentaires pour fonctionner dans l’environnement de destination d’une migration. Ce document explique le scénario et les étapes nécessaires pour qu’ils protègent les nœuds de la manière prévue.

## Migration de groupes d’utilisateurs fermés (CUG)

Les groupes sont automatiquement inclus dans une migration CTT/CAM vers Adobe Experience Manager as a Cloud Service s’ils sont associés au contenu migré via la liste de contrôle d’accès de ce contenu ou son nœud de politique de CUG. La vérification de l’existence du groupe et de ses membres doit être effectuée avant la mise en ligne. Les groupes référencés sur une politique de CUG sont appelés « groupes de CUG ».

Pour utiliser des CUG dans AEM as a Cloud Service, les utilisateurs doivent être présents sur l’instance de création et être membres des groupes de CUG appropriés.  Cette opération peut être effectuée à l’aide de packages, ou si les utilisateurs et utilisatrices des CUG sont des utilisateurs et utilisatrices IMS, ils ou elles peuvent déjà être présents.  Les utilisateurs et utilisatrices de CUG doivent ensuite être membres des groupes de CUG AEM.

Pour activer le comportement des CUG sur l’instance de publication :

1. Les groupes CUG doivent être activés (ce qui les reproduit ainsi que leurs membres sur l’instance de publication).
1. *Toutes* pages protégées par des politiques de CUG doivent être dépubliées (pour effacer le nombre global de CUG), et
1. Les pages protégées par des politiques de CUG doivent ensuite être publiées (ce qui permet à l’instance de publication et de suivre les politiques).
1. Une fois toutes les pages publiées, vérifiez la fonctionnalité de chaque page protégée par un CUG.

Pour plus d’informations, voir [Groupes d’utilisateurs fermés](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/closed-user-groups.html?lang=fr).
