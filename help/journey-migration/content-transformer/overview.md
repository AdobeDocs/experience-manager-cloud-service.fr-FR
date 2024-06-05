---
title: Présentation du Transformateur de contenu
description: Découvrez comment détecter et corriger les problèmes liés au contenu signalés par la BPA à l’aide de Content Transformer.
exl-id: aa3397ff-3dd6-4c67-9064-cb9b19bf1c73
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 86%

---

# Vue d’ensemble {#overview-ct}

Le Transformateur de contenu (CT) est un outil développé par Adobe qui peut être utilisé pour détecter et corriger automatiquement les problèmes liés au contenu tels que signalés par l’[Analyseur des bonnes pratiques (BPA)](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md) avant de migrer le contenu de votre mise en œuvre AEM actuelle (On-premise ou Managed Services) vers AEM as a Cloud Service.

Le Transformateur de contenu peut vous aider à résoudre les problèmes qui relèvent des [catégories de modèle BPA](https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html?lang=fr) suivantes (présentées dans le tableau ci-dessous) en permettant d’effectuer des actions en bloc, telles que déplacer ou supprimer. Cela peut réduire considérablement le temps nécessaire et la complexité associée à un projet de migration.

## Catégories de modèles couvertes par le Transformateur de contenu et solutions suggérées {#pattern-categories-and-benefits}

| Code de motif | Type/Sous-type de suspicion | Correctif potentiel avant de migrer le contenu vers AEM as a Cloud Service |
|--------------|--------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|
| ACV | missing.jcrcontent <br> missing.original.rendition <br> metadata.descendants.violation | Déplacez ces ressources vers un autre emplacement ou supprimez-les pour vous assurer qu’elles ne sont pas migrées vers AEM as a Cloud Service. |
| CAV | content.area.violation | Déplacez temporairement les chemins vers `/etc/packages/content-transformation/paths` pour vous assurer qu’ils ne sont pas migrés vers AEM as a Cloud Service. |
| DOPI | deprecated.ordered.index | Supprimez les index obsolètes. |
| OAUI | non.migrated.oauth.users | Supprimez ces personnes utilisatrices pour vous assurer qu’elles ne sont pas migrées vers AEM as a Cloud Service. |
| PCX | page.complexity.medium <br> page.complexity.high | Supprimez les pages/enfants ou déplacez-les vers un autre emplacement pour vous assurer qu’ils ne sont pas migrés vers AEM as a Cloud Service. |
| REP | forward.replication <br> reverse.replication <br> standard.replication.agent.modification <br> custom.replication.agent.detection | Supprimez les agents de réplication créés. <br> OU <br> Supprimez les propriétés modifiées/ajoutées. |
| URS | clientlibs.location <br> file.location <br> node.location <br> workflow.location | Accédez à l’emplacement approprié pour éviter les problèmes lors de la migration. |
| URS | node.size | Déplacez temporairement les nœuds vers `/etc/packages/content-transformation/paths` pour vous assurer qu’ils ne sont pas migrés vers AEM as a Cloud Service. |

## Avantages du Transformateur de contenu {#benefits}

Le Transformateur de contenu offre les avantages suivants :

* Sûr : un package est créé par le Transformateur de contenu chaque fois qu’il apporte une modification au référentiel pour résoudre les problèmes. Si nécessaire, vous pouvez revenir à l’état précédent en installant le package.
* Facile à utiliser : le Transformateur de contenu a été intégré à l’outil de transfert de contenu et s’accompagne d’une interface utilisateur simple et intuitive.
* Gagne du temps : lorsque vous rencontrez un grand nombre de problèmes de contenu qui relèvent d’une catégorie de modèle, vous pouvez tous les résoudre en plusieurs clics à l’aide du transformateur de contenu.
