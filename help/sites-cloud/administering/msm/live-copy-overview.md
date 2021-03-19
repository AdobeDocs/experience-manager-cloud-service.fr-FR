---
title: Console Aperçu de la Live Copy
description: Découvrez les principes de base de la console d’aperçu de Live Copy pour comprendre rapidement l’état de vos Live Copies afin de synchroniser le contenu.
feature: Gestionnaire de plusieurs sites
role: Administrator
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 20%

---


# Console Aperçu de la Live Copy {#live-copy-overview-console}

La console **Présentation de Live Copy** vous permet d&#39;effectuer les opérations suivantes :

* Vue/gestion de l’héritage sur un site.
   * Vue de l&#39;arborescence du plan directeur et de la structure Live Copy correspondante, ainsi que de leur état d&#39;héritage
   * Modifier l’état d’héritage, tel que la suspension et la reprise
   * Plan de vue et propriétés Live Copy
* Exécuter des actions de déploiement.

## Ouverture de l’aperçu de la Live Copy {#opening-the-live-copy-overview}

Vous pouvez ouvrir l’aperçu de la Live Copy via :

* [Panneau latéral de références d’une page de plan directeur (console Sites)](#opening-live-copy-overview-references-for-a-blueprint-page)
* [Propriétés d’une page de plan directeur](#opening-live-copy-overview-properties-of-a-blueprint-page)

### Références à une page de plan directeur {#references-to-a-blueprint-page}

Vous pouvez ouvrir **Live Copy Overview** à partir du panneau latéral **References** de la console **Sites** :

1. Dans la console **Sites**, [accédez à la page de plan directeur et sélectionnez-la.](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)
1. Ouvrez le rail **[Références](/help/sites-cloud/authoring/getting-started/basic-handling.md#references)** et sélectionnez **Live Copies**.

   ![Live Copy du rail de références](../assets/live-copy-references.png)

   >[!TIP]
   >
   >Vous pouvez également ouvrir d’abord les références, puis sélectionner le plan.

1. Sélectionnez **Aperçu de la Live Copy** pour afficher et utiliser l&#39;aperçu de toutes les Live Copies liées au plan directeur sélectionné.
1. Utilisez **Fermer** pour fermer l’aperçu et retourner à la console **Sites**.

### Propriétés d&#39;une page de plan directeur {#properties-of-a-blueprint-page}

L’**aperçu de la Live Copy** peut être ouvert lorsque lors de l’affichage des propriétés d’une page de plan directeur :

1. Ouvrir **Propriétés** pour la page de plan directeur appropriée.
1. Ouvrez l’onglet **Plan directeur** ; l’option **Aperçu de la Live Copy** apparaît dans la barre d’outils supérieure :

   ![Onglet Propriétés du plan directeur](../assets/live-copy-blueprint-tab.png)

1. Sélectionnez **Aperçu de la Live Copy** pour afficher et utiliser l&#39;aperçu de toutes les Live Copies liées au plan général actuel.

1. Utilisez **Fermer** pour fermer l’aperçu et retourner à la console **Sites**.

## Utilisation de l’aperçu de la Live Copy {#using-the-live-copy-overview}

La fenêtre **Aperçu de la Live Copy** fournit un aperçu de l&#39;état des Live Copies liées à la page sélectionnée.

![Fenêtre Aperçu de Live Copy](../assets/live-copy-overview.png)

Un déploiement dépend des actions de synchronisation définies dans la configuration de déploiement spécifique. Certaines actions dépendent des modifications apportées au contenu. Cependant, de nombreuses actions ne dépendent pas des modifications apportées au contenu, mais dépendent de événements tels que l’activation des pages. Ces événements ne modifient pas le contenu, mais modifient les propriétés internes liées au contenu.

Les champs d&#39;état dépendent également des actions de synchronisation définies dans la configuration de déploiement spécifique et indiquent s&#39;il y a eu de telles actions dans le plan ou dans Live Copy depuis le dernier déploiement réussi. Un champ d&#39;état ne reflète que les actions de la configuration de déploiement spécifique. Si aucun déploiement réussi n’a jamais été effectué sur une Live Copy, l’état s’affiche toujours à jour.

Par exemple, une configuration de déploiement est définie comme `targetActivate`. Par conséquent, un déploiement dépendra uniquement des événements d&#39;activation. Le champ d&#39;état indique uniquement si des événements d&#39;activation se sont produits depuis le dernier déploiement réussi.

L&#39;**Aperçu de la Live Copy** peut également être utilisé pour effectuer des actions sur la Live Copy :

1. Ouvrez l’**aperçu de la Live Copy**.
1. Sélectionnez le plan ou la page Live Copy requise et la barre d&#39;outils sera mise à jour pour afficher les actions disponibles. Les [actions](overview.md#terms-used) disponibles varient selon que vous sélectionnez une page [plan directeur](#actions-for-a-blueprint-page) ou [Live Copy](#actions-for-a-live-copy-page).

### Actions d’une page de plan directeur {#actions-for-a-blueprint-page}

Lorsque vous sélectionnez une page de plan directeur, les actions suivantes sont disponibles :

![Actions de présentation en direct d&#39;un plan](../assets/live-copy-overview-actions-blueprint.png)

* **Modifier**  : ouvrez la page du plan pour le modifier.
* **[Déploiement](overview.md#rollout-and-synchronize)**  : effectuez un déploiement pour pousser les modifications de la source vers la Live Copy.

### Actions d’une page de Live Copy {#actions-for-a-live-copy-page}

Lorsque vous sélectionnez une page Live Copy, les actions suivantes sont disponibles :

![Actions de vue d’ensemble de LiveCopy pour une Live Copy](../assets/live-copy-overview-actions.png)

* **Modifier**  : ouvrez la page Live Copy pour la modifier.
* **[Statut](#relationship-status)**  de la relation - Informations sur la Vue de l&#39;état et de l&#39;héritage.
* **[Synchroniser](overview.md#rollout-and-synchronize)**  : synchronisez une Live Copy pour extraire les modifications de la source vers la Live Copy.
* **[Réinitialiser](creating-live-copies.md#resetting-a-live-copy-page)**  : réinitialisez une page Live Copy pour supprimer toutes les annulations d&#39;héritage et rétablir la page dans le même état que la page source.
* **[Suspendre](overview.md#suspending-and-cancelling-inheritance-and-synchronization)**  : désactive temporairement la relation active entre une Live Copy et sa page de plan.
* **[Reprendre](creating-live-copies.md#resuming-inheritance-for-a-page)**  - Reprendre vous permet de rétablir une relation suspendue.
* **[Détacher](overview.md#detaching-a-live-copy)**  : supprime définitivement la relation active entre une Live Copy et sa page de plan.

## État de la relation {#relationship-status}

La console **Statut de la relation** comporte deux onglets qui offrent une gamme de fonctionnalités.

* [État de la relation](#relationship-status-tab)
* [Live Copy ](#live-copy-tab)

### État de la relation {#relationship-status-tab}

Cet onglet fournit des informations détaillées sur l&#39;état de la relation entre le plan et Live Copy.

![Onglet Statut de la relation](../assets/live-copy-relationship-status.png)

### Live Copy   {#live-copy-tab}

Cet onglet vous permet de vue et de modifier la configuration de Live Copy.

![Onglet Live Copy](../assets/live-copy-relationship-status-live-copy.png)
