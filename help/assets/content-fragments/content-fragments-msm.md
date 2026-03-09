---
title: Réutilisation de fragments de contenu à l’aide de MSM et de Live Copies
description: Découvrez comment utiliser la fonctionnalité Live Copy de MSM pour utiliser le même contenu de fragment de contenu ou un contenu similaire à plusieurs emplacements, tout en se synchronisant avec le contenu source.
badgeSaas: label="AEM Assets" type="Positive" tooltip="S’applique à AEM Assets)."
exl-id: f050b2d1-856c-4cdb-ac74-bc78016f144a
feature: Content Fragments
role: User
solution: Experience Manager Sites
source-git-commit: a641933d1049cd07ee8935672c8ef357a5bbf18c
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 18%

---

# Réutilisation de fragments de contenu à l’aide de MSM {#reuse-content-fragments-using-msm}

Multi Site Manager (MSM) et la fonctionnalité Live Copy vous permettent d’utiliser le même contenu à plusieurs emplacements, tout en se synchronisant avec le contenu source.

* Avec les Live Copies MSM, vous pouvez :
   * créer une fois un contenu ;
   * Réutilisez ce contenu dans d’autres zones du même site ou d’autres applications.
* MSM conserve alors les relations en direct entre votre contenu source et ses Live Copies afin que :
   * Lorsque vous modifiez le contenu source, la source et les Live Copies sont synchronisées.
   * vous puissiez apporter des ajustements uniquement au contenu des Live Copies en déconnectant les relations en direct pour des sous-pages et composants spécifiques.

Pour une présentation détaillée des concepts de MSM, voir [Réutilisation de contenu : Multi Site Manager et Live Copy](/help/sites-cloud/administering/msm/overview.md).

>[!NOTE]
>
>La fonctionnalité [Multi Site Manager (MSM)](/help/sites-cloud/administering/msm/overview.md) de Adobe Experience Manager permet aux utilisateurs de réutiliser du contenu créé une fois, puis de le réutiliser à plusieurs emplacements sur le web.

Avec MSM pour les fragments de contenu, vous pouvez :

* Créez des fragments de contenu une fois, puis effectuez des copies (liées) de ces fragments pour les réutiliser dans d’autres zones du site ou de l’application.
* Conservez la synchronisation de plusieurs copies en mettant à jour la copie source une seule fois, puis en transmettant les modifications aux copies (actives).
* Apportez des modifications locales en suspendant temporairement ou définitivement la liaison entre les fragments parents et enfants, soit complètement, soit pour leurs variantes ou champs.

MSM pour les fragments de contenu, associé à des fonctionnalités dans l’éditeur de fragment de contenu, vous permet de rompre et de rétablir l’héritage au niveau du champ.

>[!CAUTION]
>
>MSM pour les fragments de contenu n’est disponible que lors de l’utilisation de fragments de contenu via la console **Ressources**.
>
>La fonctionnalité MSM *n’est pas* disponible lors de l’utilisation de la console **Fragments de contenu**.

## Procédures {#how-to}

Consultez la documentation suivante pour plus d’informations sur l’utilisation de MSM pour les fragments de contenu (également applicable à Assets) :

* Utilisation de [MSM pour les fragments de contenu (et Assets)](/help/assets/reuse-assets-using-msm.md)

* [Créer une Live Copy](/help/assets/reuse-assets-using-msm.md)

  >[!CAUTION]
  >
  >Si vous souhaitez utiliser MSM pour créer des copies de fragments de contenu), toutes les contraintes **uniques** doivent être supprimées de tous les types de données utilisés dans les [modèles de fragment de contenu](/help/assets/content-fragments/content-fragments-models.md) respectifs.

* [Affichage des propriétés et du statut de la source et de la Live Copy](/help/assets/reuse-assets-using-msm.md#properties)
* [Propagation des modifications de la source vers la Live Copy](/help/assets/reuse-assets-using-msm.md#rollout-sync)
* Annuler et rétablir l’héritage pour :
   * champs et variations dans l’[éditeur de fragment de contenu](/help/assets/content-fragments/content-fragments-variations.md#inheritance)
   * [métadonnées des ressources associées](/help/assets/content-fragments/content-fragments-variations.md#canceling-reenabling-inheritance-individual-items)
* [Suspendre et reprendre la relation](/help/assets/reuse-assets-using-msm.md#suspend-resume)
* [Suppression de la relation dynamique](/help/assets/reuse-assets-using-msm.md#detach)
* [Comparaison de MSM pour les fragments de contenu (et Assets) avec MSM pour Sites](/help/assets/reuse-assets-using-msm.md#comparison)

## Limites {#limitations}

* Les déclencheurs Lors de la modification et la configuration de déploiement associée n’existent pas pour les fragments de contenu.
