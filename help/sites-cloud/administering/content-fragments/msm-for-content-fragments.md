---
title: Réutilisation de fragments de contenu à l’aide de MSM et de Live Copies
description: Découvrez comment utiliser la fonctionnalité Live Copy de MSM pour utiliser le même contenu de fragment de contenu ou un contenu similaire à plusieurs emplacements, tout en se synchronisant avec le contenu source.
badgeSaas: label="AEM Sites" type="Positive" tooltip="S’applique à AEM Sites)."
feature: Content Fragments
role: User
solution: Experience Manager Sites
hide: true
hidefromtoc: true
index: false
source-git-commit: 85b72909597a95531aea51719c841bc5db9c1a21
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 4%

---

# Réutilisation de fragments de contenu à l’aide de MSM {#reuse-content-fragments-using-msm}

Multi Site Manager (MSM) et la fonctionnalité Live Copy vous permettent d’utiliser le même contenu à plusieurs emplacements, tout en se synchronisant avec le contenu source.

<!-- CQDOC-23473 - feature is currently beta so page is hidden, see metadata -->
<!-- CQDOC-23473 - screenshots -->
<!-- CQDOC-23473 - only mentioned once in ToC, add entries -->
<!-- CQDOC-23473 - will work on folders -->

<!-- CQDOC-23473 - feature is currently beta remove Caution for GA -->

>[!CAUTION]
>
>MSM à partir de la console Fragments de contenu est actuellement une fonctionnalité de Beta disponible uniquement pour des clients spécifiques.
>
>MSM pour les fragments de contenu est également disponible lors de l’utilisation de fragments de contenu via la console **&#x200B;**.

* Avec les Live Copies MSM, vous pouvez :
   * Créer du contenu une fois
   * Réutilisez ce contenu dans d’autres zones du même site, d’autres sites ou dans des applications.
* MSM conserve alors les relations en direct entre votre contenu source et ses Live Copies afin que :
   * Lorsque vous modifiez le contenu source, la source et les Live Copies sont synchronisées.
   * Vous pouvez apporter des ajustements uniquement au contenu des Live Copies en déconnectant les relations en direct pour des sous-fragments et/ou composants individuels.

<!-- CQDOC-23473 - feature is currently beta remove Caution for GA -->

Pour une présentation détaillée des concepts de MSM, voir Réutilisation de contenu : Multi Site Manager et Live Copy.

<!--
For a detailed overview of MSM concepts see [Reusing Content: Multi Site Manager and Live Copy](/help/sites-cloud/administering/msm/overview.md).
-->

<!-- CQDOC-23473 - feature is currently beta remove Caution for GA -->

>[!NOTE]
>
>La fonctionnalité Multi Site Manager (MSM) dans Adobe Experience Manager permet aux utilisateurs de réutiliser du contenu créé une fois, puis de le réutiliser à plusieurs emplacements sur le web.

<!--
>[!NOTE]
>
>[Multi Site Manager (MSM)](/help/sites-cloud/administering/msm/overview.md) functionality in Adobe Experience Manager enables users to reuse content that is authored once and then reused across multiple web-locations. 
-->

Avec MSM pour les fragments de contenu, vous pouvez :

* Créez des fragments de contenu une fois, puis effectuez des copies (liées) de ces fragments pour les réutiliser dans d’autres zones du site ou de l’application.
* Conservez la synchronisation de plusieurs copies en mettant à jour la copie source une seule fois, puis en transmettant les modifications aux copies (actives).
* Apportez des modifications locales en suspendant temporairement ou définitivement la liaison entre les fragments parents et enfants, soit complètement, soit pour leurs variantes ou champs.

MSM pour les fragments de contenu, associé à des fonctionnalités dans l’éditeur de fragment de contenu, vous permet de rompre et de rétablir l’héritage au niveau du champ.

<!-- CQDOC-23473 - feature is currently beta remove Caution for GA -->

>[!NOTE]
>
>Cette page traite de la fonctionnalité MSM lors de l’utilisation de la console **Fragments de contenu**.
>
>MSM pour les fragments de contenu est également disponible lors de l’utilisation de fragments de contenu via la console **&#x200B;**.

<!--
>[!NOTE]
>
>This page covers MSM functionality when using the **Content Fragments** console.
>
>MSM for Content Fragments is also available when using [Content Fragments via the **Assets** console](/help/assets/content-fragments/content-fragments-msm.md). 
-->

## Créer une Live Copy {#create-a-live-copy}

<!-- CQDOC-23473 - exclude children or referenced content fragments? -->

Pour créer une Live Copy de votre fragment de contenu :

1. Dans la console Fragment de contenu , naviguez jusqu’à l’emplacement de votre fragment.
1. Sélectionnez votre fragment.
1. Sélectionnez **Créer une Live Copy** dans la barre d’outils supérieure.
1. Dans la boîte de dialogue qui s’ouvre, spécifiez la destination et continuez avec **Suivant**.
1. Spécifiez les propriétés. Vous pouvez spécifier le titre, le nom et si la Live Copy doit exclure les enfants (fragments imbriqués).
1. Continuez avec **Suivant**.
1. Choisissez si vous souhaitez que la Live Copy soit créée immédiatement (**Maintenant**) ou à une date et une heure **Ultérieurement**.
1. Confirmez avec **Créer une Live Copy**.

   <!-- CQDOC-23473 - feature is currently beta remove Caution for GA -->

   >[!CAUTION]
   >
   >Si vous souhaitez utiliser MSM pour créer des copies de fragments de contenu), toutes les contraintes **uniques** doivent être supprimées de tous les types de données utilisés dans les modèles de fragment de contenu respectifs.

   <!--
   >[!CAUTION]
   >
   >If you want to use MSM to create copies of Content Fragments), then any **Unique** constraints should be removed from any Data Types used in the respective [Content Fragment Models](/help/assets/content-fragments/content-fragments-models.md).
   -->

## Affichage des propriétés et du statut {#view-properties-and-status}

Pour afficher les propriétés et le statut de la source et de votre Live Copy :

1. Dans la console Fragment de contenu , naviguez jusqu’à l’emplacement de votre fragment.
1. Sélectionnez votre fragment.
1. Sélectionnez l’icône Informations (i) dans la colonne **Titre** de votre fragment.
Le panneau d’informations approprié s’ouvre.
1. Sélectionnez l’onglet **Détails de la Live Copy**.

   ![Informations sur une Live Copy](/help/sites-cloud/administering/content-fragments/assets/cf-msm-information.png)

## Propager les modifications {#propagate-modifications}

Pour propager les modifications entre la source et votre Live Copy

### Synchroniser {#synchronize}

Pour déclencher une synchronisation qui extrait les mises à jour de contenu de votre Live Copy vers la source :

1. Dans la console Fragments de contenu , naviguez jusqu’à l’emplacement de votre source de fragment.
1. Sélectionnez votre fragment.
1. Sélectionnez **Synchroniser** dans la barre d’outils.
1. Confirmez **Synchroniser** dans la boîte de dialogue.

### Déploiement {#rollout}

Pour déclencher un déploiement qui envoie les mises à jour sources à votre Live Copy :

1. Dans la console Fragments de contenu , naviguez jusqu’à l’emplacement de la Live Copy de votre fragment.
1. Sélectionnez votre fragment.
1. Sélectionnez **Déploiement** dans la barre d’outils. L’assistant s’ouvre pour vous guider tout au long du processus.
1. Sélectionnez les Live Copies à inclure dans le déploiement et **Continuer**.
1. Planifiez le déploiement pour immédiatement (**Maintenant**) ou **Ultérieurement**.
1. **Continuer** selon les besoins.

<!-- CQDOC-23473 - feature is beta, is in authoring so remove here when GA -->

## Annuler et rétablir l’héritage dans l’éditeur {#cancel-and-revert-to-inheritance-in-the-editor}

L’héritage est le mécanisme par lequel le contenu peut être automatiquement transmis d’un fragment à un autre. Les champs hérités et les variations peuvent être le produit de la gestion multisite.

Vous pouvez annuler (puis rétablir) l’héritage dans l’éditeur de fragment de contenu. Selon le contexte, cette option peut être disponible pour une variation ou un champ individuel, si le fragment fait partie d’une Live Copy.

Par exemple :

* Annuler l’héritage

  ![Icône d’annulation de l’héritage](/help/sites-cloud/administering/content-fragments/assets/cf-authoring-cancel-inheritance.png)

* Rétablir l’héritage (si l’héritage est déjà annulé)

  ![Icône Rétablir l’héritage](/help/sites-cloud/administering/content-fragments/assets/cf-authoring-revert-to-inheritance.png)

<!-- CQDOC-23473 - feature is currently beta reinstate Note for GA -->

<!--
## Cancel, and revert to, inheritance {#cancel-and-reinstate-inheritance}

Inheritance is the mechanism where content can be automatically pushed from one fragment to another. Inherited fields, and variations, can be the product of Multi-Site Management.

You can cancel (then revert) the inheritance. Depending on the context, this can be available for a variation, or an individual field, if the fragment is part of a live copy.
-->

<!--
>[!NOTE]
>
>For more details see [Cancel, and revert to, inheritance in the editor](/help/sites-cloud/administering/content-fragments/authoring.md#cancel-and-revert-to-inheritance).
-->

## Comparaison de MSM pour les fragments de contenu et les pages de sites {#compare-msm-for-content-fragments-and-sites-pages}

<!-- CQDOC-23473 - needs a detailed review -->

Dans la plupart des scénarios, MSM pour les fragments de contenu correspond au comportement de la fonctionnalité MSM pour les pages de sites. Voici quelques différences importantes à noter :

* Le plan directeur dans MSM pour les pages Sites est appelé Source Live Copy dans MSM pour les fragments de contenu.
* Pour les pages de sites, vous pouvez comparer un plan directeur et sa Live Copy, mais les fragments de contenu ne peuvent pas comparer une source à sa Live Copy.
* Vous ne pouvez pas modifier une Live Copy dans la console Fragments de contenu.
* Les pages de sites ont généralement des enfants, mais pas les fragments de contenu, même s’ils peuvent avoir des fragments référencés. L’option permettant d’inclure ou d’exclure des enfants fait référence à ces fragments référencés.
* La suppression de l’étape des chapitres dans l’assistant de création de site n’est pas prise en charge dans MSM pour les fragments de contenu.
* La configuration des verrous MSM sur les propriétés de page n’est pas prise en charge dans MSM pour les fragments de contenu.
* Pour MSM pour les fragments de contenu, utilisez uniquement la **configuration de déploiement standard**. Les autres configurations de déploiement ne sont pas disponibles pour MSM pour les fragments de contenu.

>[!NOTE]
>
>N’oubliez pas que MSM pour les fragments de contenu accessibles via la console Fragments de contenu est basé sur la fonctionnalité Assets. En effet, ils sont stockés en tant qu’Assets (bien que considéré comme une fonctionnalité Sites).

## Limites {#limitations}

* Les déclencheurs Lors de la modification et la configuration de déploiement associée n’existent pas pour les fragments de contenu.
