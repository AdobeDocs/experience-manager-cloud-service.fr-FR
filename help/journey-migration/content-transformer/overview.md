---
title: Présentation de Content Transformer
description: Découvrez comment détecter et corriger les problèmes liés au contenu signalés par la BPA à l’aide de Content Transformer.
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 4%

---

# Vue d’ensemble {#overview-ct}

Le Transformateur de contenu (CT) est un outil développé par Adobe qui peut être utilisé pour détecter et corriger automatiquement les problèmes liés au contenu signalés par . [Analyseur des bonnes pratiques (BPA)](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md) avant de migrer le contenu de votre mise en oeuvre AEM actuelle (On-premise ou Managed Services) vers AEM as a Cloud Service.

Le transformateur de contenu peut vous aider à résoudre les problèmes qui tombent sous les conditions suivantes : [Catégories de modèle BPA](https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html?lang=fr) (dans le tableau ci-dessous) en permettant aux utilisateurs d’effectuer des actions en bloc, telles que déplacer ou supprimer. Cela peut réduire considérablement le temps et la complexité associée à un projet de migration.

## Catégories de modèles couvertes par Content Transformer et solutions suggérées {#pattern-categories-and-benefits}

| Code de motif | Type de méfiance/sous-type | Correctif potentiel avant de migrer le contenu vers AEM as a Cloud Service |
|--------------|--------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|
| ACV | missing.jcrcontent <br> missing.original.rendition <br> metadata.descendants.violation | Déplacez ces ressources vers un autre emplacement ou supprimez-les pour vous assurer qu’elles ne sont pas migrées vers AEM as a Cloud Service. |
| CAV | content.area.violation | Déplacer temporairement les chemins vers `/etc/packages/content-transformation/paths` pour s’assurer qu’ils ne sont pas migrés vers AEM as a Cloud Service. |
| DOPI | deprecated.ordered.index | Supprimez les index obsolètes. |
| OAUI | non.migrated.oauth.users | Supprimez ces utilisateurs pour vous assurer qu’ils ne sont pas migrés vers AEM as a Cloud Service. |
| PCX | page.complexité.medium <br> page.complexité.high | Supprimez les pages/enfants ou déplacez-les vers un autre emplacement pour vous assurer qu’ils ne sont pas migrés vers AEM as a Cloud Service. |
| REP | forward.replication <br> reverse.replication <br> standard.replication.agent.modification <br> custom.replication.agent.détection | Supprimez les agents de réplication nouvellement créés. <br> OU <br> Supprimez les propriétés modifiées/ajoutées. |
| URS | clientlibs.location <br> file.location <br> node.location <br> workflow.location | Accédez à l’emplacement approprié pour éviter des problèmes lors de la migration. |
| URS | node.size | Déplacer temporairement les noeuds vers`/etc/packages/content-transformation/paths` pour s’assurer qu’ils ne sont pas migrés vers AEM as a Cloud Service. |

## Avantages du transformateur de contenu {#benefits}

Content Transformer offre les avantages suivants :

* Fail-safe : un package est créé par Content Transformer chaque fois qu’il apporte une modification au référentiel pour résoudre les problèmes. Si nécessaire, vous pouvez revenir à l’état précédent en installant le package.
* Facile à utiliser : le transformateur de contenu a été intégré à l’outil de transfert de contenu et s’accompagne d’une interface utilisateur simple et intuitive.
* Gagnez du temps : lorsque vous rencontrez un grand nombre de problèmes de contenu qui relèvent d’une catégorie de modèle, vous pouvez tous les résoudre en quelques clics seulement à l’aide du transformateur de contenu.
