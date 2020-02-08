---
title: Lancements
description: Lancements vous permettent de développer efficacement du contenu pour une prochaine version. Les lancements permettent de préparer les modifications pour une publication à venir, tout en conservant vos pages actuelles.
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Lancements {#launches}

La fonction Lancements permet de développer efficacement du contenu en vue d’une publication ultérieure.

Le lancement vous permet de préparer des modifications en vue d’une publication future (tout en conservant vos pages actives). Une fois vos modifications apportées aux pages de lancement, vous devez les convertir de nouveau en pages source, puis activer ces dernières (au niveau supérieur). L’opération de conversion duplique le contenu de lancement sur les pages source et peut être appliquée manuellement ou automatiquement (selon les champs définis lors de la création et de la modification du lancement).

Par exemple, les pages de produits saisonniers de votre boutique en ligne sont mises à jour tous les trimestres, de telle sorte que les offres spéciales soient en phase avec la saison. Pour préparer la prochaine mise à jour trimestrielle, vous pouvez créer un lancement des pages web en question. Pendant tout le trimestre, les modifications suivantes sont accumulées dans la copie de lancement :

* Modifications apportées aux pages source dans le cadre des tâches de maintenance normales. Ces modifications sont automatiquement dupliquées dans les pages de lancement.
* Modifications effectuées directement sur les pages de lancement en vue du prochain trimestre.

À l’approche du trimestre suivant, vous convertissez les pages de lancement pour pouvoir modifier les pages source (contenant le contenu mis à jour). Vous pouvez convertir toutes les pages ou uniquement celles que vous avez modifiées. 

Les lancements peuvent également être :

* Créés pour plusieurs branches racine. Même si vous pouvez créer un lancement pour le site dans son intégralité (et y apporter des modifications), cette méthode n’est pas pratique puisque l’ensemble du site doit être copié. Lorsque des centaines, voire des milliers, de pages sont utilisées, les configurations et les performances du système dépendent de l’action de copie et ultérieurement des comparaisons nécessaires pour les tâches de conversion.
* Imbriqués (un lancement dans un lancement). Vous pouvez ainsi créer un lancement à partir d’un lancement existant pour que les développeurs de contenu exploitent les modifications déjà apportées, au lieu de répercuter ces mêmes modifications à plusieurs reprises pour chaque lancement.

This section describes how to create, edit and promote (and if necessary [delete](/help/sites-cloud/authoring/launches/creating.md#deleting-a-launch)) launch pages from within the Sites console or [the Launches console](#the-launches-console):

* [Création de lancements](/help/sites-cloud/authoring/launches/creating.md)
* [Modification de lancements](/help/sites-cloud/authoring/launches/editing.md)
* [Conversion de lancements](/help/sites-cloud/authoring/launches/promoting.md)

## Lancements - Ordre des événements {#launches-the-order-of-events}

La fonction Lancements vous permet de développer efficacement le contenu en vue d’une publication future d’une ou de plusieurs pages web activées.

La fonction Lancements vous permet de :

* Créer une copie de vos pages source :
   * La copie correspond au lancement.
   * Les pages source de niveau supérieur s’appellent des **pages de production**.
      * Les pages source peuvent être extraites de plusieurs branches (distinctes).
   ![Ordre de fonctionnement des lancements](/help/sites-cloud/authoring/assets/launches-order.png)

* Modifier la configuration des lancements :
   * Ajoutez ou supprimez des pages et/ou des branches vers/à partir du lancement.
   * Modifiez des propriétés de lancement, comme le **titre**, la **date de lancement** et l’indicateur **Prêt pour la production**. 
* Vous pouvez convertir et modifier le contenu manuellement ou automatiquement :
   * Manuellement :
      * Convertissez votre contenu de lancement en **Cible** (pages source) lorsqu’il est prêt à être publié.
      * Modifiez le contenu des pages source (après les avoir à nouveau converties).
      * Convertissez toutes les pages ou uniquement celles qui ont été modifiées.
   * Automatiquement, ce qui implique les étapes suivantes : 
      * Le champ **Date de** **lancement** (**En direct**) : ce paramètre peut être défini lors de la création ou de la modification d’un lancement.
      * L’indicateur **Prêt pour la production** : cette option n’est sélectionnable que lors de la modification d’un lancement.
      * Si l’indicateur **Prêt pour la production** est défini, le lancement sera automatiquement converti en pages de production à la date de **lancement** (**En direct**) spécifiée ****. Une fois la conversion faite, les pages de production sont automatiquement publiées.\
         Si aucune date n’a été définie, l’indicateur n’a aucun effet.
* Mettez à jour vos pages source et de lancement en parallèle :
   * Les modifications apportées aux pages source sont automatiquement appliquées à la copie de lancement (si elle a été configurée avec un héritage, c’est-à-dire comme Live Copy). 
   * Les modifications apportées à la copie de lancement peuvent l’être sans interrompre les mises à jour automatiques ou modifier les pages source. 
   ![Actions en parallèle](/help/sites-cloud/authoring/assets/launches-parallel.png)

* [Créer un lancement imbriqué](/help/sites-cloud/authoring/launches/creating.md#creating-a-nested-launch) (lancement dans un lancement) :
   * La source est un lancement existant.
   * Vous pouvez [promouvoir un lancement imbriqué](/help/sites-cloud/authoring/launches/promoting.md#promoting-a-nested-launch) dans n’importe quelle cible. Il peut s’agir d’un lancement parent ou des pages source de niveau supérieur (production).
   ![Lancement imbriqué](/help/sites-cloud/authoring/assets/launches-nested.png)

   >[!CAUTION]
   >
   >La suppression d’un lancement supprime le lancement lui-même et tous les lancements imbriqués qui en sont des descendants.

>[!NOTE]
>
>Creating and editing launches requires access rights to `/content/launches` - as with the default group `content-authors`.
>
>Si vous rencontrez des difficultés, contactez votre administrateur système. 

### Console de lancements {#the-launches-console}

La console de lancements fournit un aperçu de vos lancements et permet d’appliquer des actions sur les lancements répertoriés. Vous pouvez accéder à la console via :

* La console **Outils** : **Outils**, **Sites**, **Lancements**.

* Ou directement avec `https://<host>:<port>/libs/launches/content/launches.html`

## Lancements dans les références (console de sites) {#launches-in-references-sites-console}

1. Dans la console **Sites**, accédez à la source des lancements.
1. Ouvrez le rail **Références** et sélectionnez la page source.
1. Sélectionnez **Lancements**. Les lancements existants seront répertoriés :

   ![Références des lancements dans la console des sites](/help/sites-cloud/authoring/assets/launches-references.png)

1. Appuyez/cliquez sur le lancement qui vous intéresse. La liste des actions possibles s’affiche :

   ![Actions à effectuer sur les lancements dans la console des sites](/help/sites-cloud/authoring/assets/launches-references-actions.png)
