---
title: Migration des groupes d’utilisateurs fermés
description: Cette page contient les considérations spéciales nécessaires pour activer les groupes d’utilisateurs fermés après la migration de contenu vers Adobe Experience Manager as a Cloud Service.
hide: true
hidefromtoc: true
source-git-commit: ca3c4bae2e652d75190d68c76b1dd4e09239f16c
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 7%

---

# Migration des groupes d’utilisateurs fermés {#migrating-closed-user-groups}

>[!CONTEXTUALHELP]
>id="aemcloud_cug_migration"
>title="Migration des groupes d’utilisateurs et utilisatrices fermés"
>abstract="La migration des groupes d’utilisateurs et utilisatrices fermés (CUG) nécessite actuellement quelques vérifications et étapes pour être opérationnelle après une migration."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/closed-user-groups.html?lang=fr" text="Groupes d’utilisateurs fermés dans AEM"

Actuellement, les groupes d’utilisateurs fermés (CUG) ont besoin de certaines étapes supplémentaires pour être fonctionnels dans l’environnement de destination d’une migration.  Ce document explique le scénario et les étapes requises pour leur permettre de protéger les noeuds de la manière prévue.

## Migration des groupes

Les entités principales (y compris les groupes) sont automatiquement incluses dans une migration vers Adobe Experience Manager as a Cloud Service si elles sont associées au contenu migré via l’ACL de ce contenu.

## Groupes d’utilisateurs fermés dans la migration

Actuellement, groupes associés *only* avec une stratégie Groupe d’utilisateurs fermé (CUG) : *not* automatiquement inclus dans l’ingestion. S’ils sont associés à un contenu via une liste de contrôle d’accès, comme indiqué ci-dessus, ils seront migrés. La vérification de l&#39;existence du groupe doit être faite avant la mise en ligne. Le rapport Principal, téléchargé via la vue Tâche d’ingestion, peut être utilisé pour déterminer si le groupe en question a été inclus ou non parce qu’il ne se trouvait pas dans une liste de contrôle d’accès. Si le groupe n’existe pas, il doit être créé dans l’instance d’auteur, y compris en ajoutant les membres appropriés, et activé afin qu’il existe sur l’instance de publication.

Enfin, les processus doivent être déclenchés pour activer le CUG. Pour ce faire, republiez tout le contenu qui contient la stratégie de CUG. Par conséquent, dans vos processus de test normaux, s’il s’avère que le CUG ne fonctionne pas, republiez ce contenu (en veillant à ce qu’il soit publié même s’il n’est pas modifié).

Cela devrait activer les stratégies de CUG lors de la publication, et le contenu ne sera accessible qu’aux utilisateurs authentifiés qui sont membres du groupe associé aux stratégies.

## Développement actif

L’équipe de migration s’efforce de faire migrer et fonctionner automatiquement les stratégies de CUG, sans aucune étape supplémentaire après l’ingestion du contenu.
Il est conseillé d’inclure la fonctionnalité CUG dans tout processus de test avant de tenter de passer en ligne.

## Résumé

En résumé, voici les étapes pour activer CUG après une migration :

1. Assurez-vous que chaque groupe utilisé dans les stratégies de CUG existe sur Publier après la migration.
   - Un groupe peut déjà exister s’il est inclus dans l’ACL d’un contenu migré.
   - Si ce n’est pas le cas, utilisez les packages pour l’installer sur l’instance de destination (ou créez-la manuellement) et l’activer ainsi que ses membres. Vérifiez ensuite qu’il existe sur la publication.
1. Si la stratégie de CUG ne protège pas encore le noeud, republiez la page (en veillant à ce qu’elle soit publiée même si aucune modification n’a été apportée à cette page).
   - Vérifiez pour chaque noeud protégé par CUG.
