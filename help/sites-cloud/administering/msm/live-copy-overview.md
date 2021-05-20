---
title: Console Aperçu de la Live Copy
description: Découvrez les principes de base de la console Aperçu de la Live Copy pour comprendre rapidement l’état de vos Live Copies afin de synchroniser le contenu.
feature: Multi Site Manager
role: Administrator
exl-id: 3ef7fbce-10a1-4b21-8486-d3c3706e537c
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 20%

---

# Console Aperçu de la Live Copy {#live-copy-overview-console}

La console **Aperçu de la Live Copy** vous permet d’effectuer les opérations suivantes :

* Afficher/gérer l’héritage sur un site.
   * Affichez l’arborescence du plan directeur et la structure Live Copy correspondante, ainsi que leur état d’héritage.
   * Modifier l’état d’héritage, tel que suspendre et reprendre
   * Afficher les propriétés de plan directeur et de Live Copy
* Exécuter des actions de déploiement.

## Ouverture de l’aperçu de la Live Copy {#opening-the-live-copy-overview}

Vous pouvez ouvrir l’aperçu de la Live Copy via :

* [Panneau latéral de références d’une page de plan directeur (console Sites)](#opening-live-copy-overview-references-for-a-blueprint-page)
* [Propriétés d’une page de plan directeur](#opening-live-copy-overview-properties-of-a-blueprint-page)

### Références à une page de plan directeur {#references-to-a-blueprint-page}

L’ **aperçu de la Live Copy** peut être ouvert à partir du panneau latéral **Références** de la console **Sites** :

1. Dans la console **Sites**, [accédez à la page de plan directeur et sélectionnez-la.](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)
1. Ouvrez le rail **[Références](/help/sites-cloud/authoring/getting-started/basic-handling.md#references)** et sélectionnez **Live Copies**.

   ![Live Copy depuis le rail de références](../assets/live-copy-references.png)

   >[!TIP]
   >
   >Vous pouvez également ouvrir d’abord les références, puis sélectionner le plan directeur.

1. Sélectionnez **Aperçu de la Live Copy** pour afficher et utiliser l’aperçu de toutes les Live Copies liées au plan directeur sélectionné.
1. Utilisez **Fermer** pour fermer l’aperçu et retourner à la console **Sites**.

### Propriétés d’une page de plan directeur {#properties-of-a-blueprint-page}

L’**aperçu de la Live Copy** peut être ouvert lorsque lors de l’affichage des propriétés d’une page de plan directeur :

1. Ouvrir **Propriétés** pour la page de plan directeur appropriée.
1. Ouvrez l’onglet **Plan directeur** ; l’option **Aperçu de la Live Copy** apparaît dans la barre d’outils supérieure :

   ![Onglet Propriétés du plan directeur](../assets/live-copy-blueprint-tab.png)

1. Sélectionnez **Aperçu de la Live Copy** pour afficher et utiliser l’aperçu de toutes les Live Copies liées au plan directeur actuel.

1. Utilisez **Fermer** pour fermer l’aperçu et retourner à la console **Sites**.

## Utilisation de l’aperçu de la Live Copy {#using-the-live-copy-overview}

La fenêtre **Aperçu de la Live Copy** fournit un aperçu de l’état des Live Copies associées à la page sélectionnée.

![Fenêtre Aperçu de la Live Copy](../assets/live-copy-overview.png)

Un déploiement dépend des actions de synchronisation définies dans la configuration de déploiement spécifique. Certaines actions dépendent des modifications apportées au contenu. Cependant, de nombreuses actions ne dépendent pas des modifications apportées au contenu, mais dépendent d’événements tels que l’activation de la page. Ces événements ne modifient pas le contenu, mais modifient les propriétés internes liées au contenu.

Les champs d’état dépendent également des actions de synchronisation définies dans la configuration spécifique au déploiement et indiquent s’il y a eu de telles actions dans le plan directeur ou dans la Live Copy depuis le dernier déploiement réussi. Un champ d’état ne reflète que les actions de la configuration de déploiement spécifique. Si aucun déploiement réussi n’a jamais été effectué sur une Live Copy, l’état s’affiche toujours à jour.

Par exemple, une configuration de déploiement est définie sous la forme `targetActivate`. Par conséquent, un déploiement dépend uniquement des événements d’activation. Le champ statut indique uniquement si des événements d’activation se sont produits depuis le dernier déploiement réussi.

L’ **aperçu de la Live Copy** peut également être utilisé pour exécuter des actions sur la Live Copy :

1. Ouvrez l’**aperçu de la Live Copy**.
1. Sélectionnez le plan directeur ou la page Live Copy requis et la barre d’outils sera mise à jour pour afficher les actions disponibles. Les [actions](overview.md#terms-used) disponibles dépendent si vous sélectionnez une page [Plan directeur](#actions-for-a-blueprint-page) ou [Live Copy](#actions-for-a-live-copy-page).

### Actions d’une page de plan directeur {#actions-for-a-blueprint-page}

Lorsque vous sélectionnez une page de plan directeur, les actions suivantes sont disponibles :

![Actions Aperçu de la Live Copy pour un plan directeur](../assets/live-copy-overview-actions-blueprint.png)

* **Modifier**  : ouvrez la page de plan directeur pour la modifier.
* **[Déploiement](overview.md#rollout-and-synchronize)**  : effectuez un déploiement pour transmettre les modifications de la source à la Live Copy.

### Actions d’une page de Live Copy {#actions-for-a-live-copy-page}

Lorsque vous sélectionnez une page Live Copy, les actions suivantes sont disponibles :

![Actions d’aperçu de Live Copy pour une Live Copy](../assets/live-copy-overview-actions.png)

* **Modifier**  : ouvrez la page Live Copy pour la modifier.
* **[État de la relation](#relationship-status)**  : affichez des informations sur l’état et l’héritage.
* **[Synchroniser](overview.md#rollout-and-synchronize)**  : synchronisez une Live Copy pour extraire les modifications de la source vers la Live Copy.
* **[Réinitialiser](creating-live-copies.md#resetting-a-live-copy-page)**  : réinitialisez une page Live Copy afin de supprimer toutes les annulations d’héritage et de rétablir l’état de la page source.
* **[Suspendre](overview.md#suspending-and-cancelling-inheritance-and-synchronization)**  : désactive temporairement la relation dynamique entre une Live Copy et sa page de plan directeur.
* **[Reprendre](creating-live-copies.md#resuming-inheritance-for-a-page)**  : Reprendre vous permet de rétablir une relation suspendue.
* **[Désolidariser](overview.md#detaching-a-live-copy)**  : supprime définitivement la relation dynamique entre une Live Copy et sa page de plan directeur.

## État de la relation {#relationship-status}

La console **État de la relation** comporte deux onglets qui offrent une gamme de fonctionnalités.

* [État de la relation](#relationship-status-tab)
* [Live Copy ](#live-copy-tab)

### État de la relation {#relationship-status-tab}

Cet onglet fournit des informations détaillées sur l’état de la relation entre le plan directeur et la Live Copy.

![Onglet État de la relation](../assets/live-copy-relationship-status.png)

### Live Copy   {#live-copy-tab}

Cet onglet vous permet d’afficher et de modifier la configuration de la Live Copy.

![Onglet Live Copy](../assets/live-copy-relationship-status-live-copy.png)
