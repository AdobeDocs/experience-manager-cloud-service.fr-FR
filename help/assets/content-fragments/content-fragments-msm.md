---
title: Réutilisation de fragments de contenu à l’aide de MSM et de Live Copies
description: Découvrez comment utiliser la fonctionnalité Live Copy de MSM pour utiliser le même contenu de fragment de contenu, ou similaire, à plusieurs emplacements, lors de la synchronisation avec le contenu source.
exl-id: f050b2d1-856c-4cdb-ac74-bc78016f144a
feature: Content Fragments
role: User
solution: Experience Manager Sites
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 17%

---

# Réutilisation de fragments de contenu à l’aide de MSM {#reuse-content-fragments-using-msm}

Multi Site Manager (MSM) et la fonctionnalité Live Copy vous permet d’utiliser le même contenu à plusieurs emplacements, lors de la synchronisation avec le contenu source.

* Avec les Live Copies MSM, vous pouvez :
   * créer une fois un contenu ;
   * Réutiliser ce contenu dans d’autres zones du même site ou d’autres sites ou applications.
* MSM conserve alors les relations en direct entre votre contenu source et ses Live Copies afin que :
   * Lorsque vous modifiez le contenu source, la source et les Live Copies sont synchronisées.
   * vous puissiez apporter des ajustements uniquement au contenu des Live Copies en déconnectant les relations en direct pour des sous-pages et composants spécifiques.

Pour une présentation détaillée des concepts MSM, voir [Réutilisation de contenu : Multi Site Manager et Live Copy](/help/sites-cloud/administering/msm/overview.md).

>[!NOTE]
>
>La fonctionnalité [Multi Site Manager (MSM)](/help/sites-cloud/administering/msm/overview.md) de Adobe Experience Manager permet aux utilisateurs de réutiliser du contenu créé une fois, puis réutilisé sur plusieurs emplacements web.

Grâce à MSM pour les fragments de contenu, vous pouvez :

* Créez des fragments de contenu une seule fois, puis effectuez des copies (liées) de ces fragments pour les réutiliser dans d’autres zones du site ou de l’application.
* Faites en sorte que plusieurs copies soient synchronisées en mettant à jour la copie source une seule fois, puis en envoyant les modifications aux copies (en direct).
* Effectuez des modifications locales en suspendant temporairement ou définitivement le lien entre les fragments parents et enfants ; complètement, ou pour leurs variations ou champs.

MSM pour les fragments de contenu, associé à la fonctionnalité de l’éditeur de fragments de contenu, vous permet de rompre et de rétablir l’héritage au niveau du champ.

>[!CAUTION]
>
>MSM pour les fragments de contenu n’est disponible que lors de l’utilisation de fragments de contenu via la console **Ressources**.
>
>La fonctionnalité MSM *n’est pas* disponible lors de l’utilisation de la console **Fragments de contenu**.

## Comment {#how-to}

Pour plus d’informations sur l’utilisation de MSM pour les fragments de contenu (également applicable à Assets), consultez la documentation suivante :

* Utilisation de [MSM pour les fragments de contenu (et Assets)](/help/assets/reuse-assets-using-msm.md)

* [Créer une Live Copy](/help/assets/reuse-assets-using-msm.md)

  >[!CAUTION]
  >
  >Si vous souhaitez utiliser MSM pour créer des copies de fragments de contenu), toutes les contraintes **Unique** doivent être supprimées de tous les types de données utilisés dans les [&#x200B; modèles de fragments de contenu &#x200B;](/help/assets/content-fragments/content-fragments-models.md) respectifs.

* [Afficher les propriétés et l’état de la source et de la Live Copy](/help/assets/reuse-assets-using-msm.md#properties)
* [Propager les modifications de la source à la Live Copy](/help/assets/reuse-assets-using-msm.md#rollout-sync)
* Annuler et rétablir l’héritage pour :
   * champs et variations dans l’ [&#x200B; éditeur de fragment de contenu &#x200B;](/help/assets/content-fragments/content-fragments-variations.md#inheritance)
   * [métadonnées des ressources associées](/help/assets/content-fragments/content-fragments-variations.md#canceling-reenabling-inheritance-individual-items)
* [Suspension et reprise de la relation](/help/assets/reuse-assets-using-msm.md#suspend-resume)
* [Suppression de la relation dynamique](/help/assets/reuse-assets-using-msm.md#detach)
* [Comparaison de MSM pour les fragments de contenu (et Assets) avec MSM pour les sites](/help/assets/reuse-assets-using-msm.md#comparison)

## Limites {#limitations}

* Les déclencheurs à la modification et la configuration de déploiement associée n’existent pas pour les fragments de contenu.
