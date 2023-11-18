---
title: Migration des groupes d’utilisateurs et utilisatrices fermés
description: Découvrez les points à prendre en compte pour activer les groupes d’utilisateurs fermés après la migration de contenu vers Adobe Experience Manager as a Cloud Service.
hide: true
hidefromtoc: true
exl-id: f62ed751-d5e2-4a01-8910-c844afab5733
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 9%

---

# Migration des groupes d’utilisateurs et utilisatrices fermés {#migrating-closed-user-groups}

>[!CONTEXTUALHELP]
>id="aemcloud_cug_migration"
>title="Migration de groupes d’utilisateurs et utilisatrices fermés"
>abstract="La migration des groupes d’utilisateurs et utilisatrices fermés (CUG) nécessite actuellement quelques vérifications et étapes pour être opérationnelle après une migration."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/closed-user-groups.html?lang=fr" text="Groupes d’utilisateurs fermés dans AEM"

Actuellement, les groupes d’utilisateurs fermés (CUG) ont besoin de certaines étapes supplémentaires pour être fonctionnels dans l’environnement de destination d’une migration. Ce document explique le scénario et les étapes requises pour leur permettre de protéger les noeuds de la manière prévue.

## Migration des groupes

Les entités principales (y compris les groupes) sont automatiquement incluses dans une migration vers Adobe Experience Manager as a Cloud Service si elles sont associées au contenu migré via l’ACL de ce contenu.

## Groupes d’utilisateurs fermés dans la migration

Actuellement, groupes associés *only* avec une stratégie Groupe d’utilisateurs fermé (CUG) : *not* automatiquement inclus dans l’ingestion. Comme indiqué ci-dessus, ils sont migrés s’ils sont associés à un contenu par le biais d’une liste de contrôle d’accès. La vérification du groupe et de ses membres doit être effectuée avant la mise en ligne. Le rapport Principal, téléchargé via la vue Tâche d’ingestion, peut être utilisé pour déterminer si le groupe en question a été inclus ou non parce qu’il ne se trouvait pas dans une liste de contrôle d’accès. Si le groupe n’existe pas, il doit être créé dans l’instance d’auteur, y compris en ajoutant les membres appropriés, et activé pour qu’il existe sur l’instance de publication. Vous pouvez le faire à l’aide de packages créés sur la source.

Enfin, les processus doivent être déclenchés et les propriétés doivent être définies pour activer les CUG. Pour ce faire, republiez toutes les pages associées à une stratégie de CUG. Cette opération calibre l’instance de publication pour effectuer le suivi des stratégies.

Cela active les stratégies de CUG lors de la publication et le contenu n’est accessible que pour les utilisateurs authentifiés qui sont membres du groupe associé aux stratégies.

## Développement actif

L’équipe de migration s’efforce de faire migrer et fonctionner automatiquement les stratégies de CUG, sans aucune étape supplémentaire après l’ingestion du contenu.
Incluez la fonctionnalité CUG dans tout processus de test avant de tenter de passer en ligne.

## Résumé

En résumé, voici les étapes pour activer CUG après une migration :

1. Assurez-vous que chaque groupe utilisé dans les stratégies de CUG existe sur Publier après la migration.
   - Un groupe peut exister s’il est inclus dans l’ACL d’un contenu migré.
   - Si ce n’est pas le cas, utilisez Packages pour l’installer sur l’instance de destination (ou créez-la manuellement) et l’activer ainsi que ses membres. Vérifiez ensuite qu’il existe sur la publication.
1. Republiez toutes les pages associées à une stratégie de CUG, en vous assurant qu’elles sont publiées, par exemple en modifiant d’abord la page. Il est important de tous les republier.
   - Une fois toutes les pages republiées, vérifiez la fonctionnalité de chaque page protégée par un groupe d’utilisateurs fermé.
