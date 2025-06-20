---
title: Lancements pour les pages
description: Découvrez comment utiliser les lancements pour les pages dans Adobe Experience Manager as a Cloud Service. Les lancements vous permettent de développer efficacement du contenu pour une version ultérieure, tout en conservant vos pages actives.
exl-id: 3e410120-d08f-4d05-932f-07bc4440af2b
solution: Experience Manager Sites
feature: Authoring, Launches
role: User
source-git-commit: 4c75904958f7faf91173cb8a37d5be5b3048cfae
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 77%

---

# Lancements pour les pages {#launches-for-pages}

Dans Adobe Experience Manager (AEM) as a Cloud Service, les lancements vous permettent de développer efficacement du contenu pour une version ultérieure.

Un *Launch* est créé pour vous permettre d’apporter des modifications en vue d’une publication ultérieure, tout en conservant votre contenu actuel. Pour les pages AEM, cela signifie que vous modifiez deux versions simultanément : les pages actuellement publiées et une version de ces pages, qui sera publiée à un moment donné dans le futur. Une fois ce délai écoulé, vous pouvez remplacer les pages d’origine et publier les nouvelles versions.

<!--
>[!NOTE]
>
>Launches are also available for Content Fragments. The basic concepts are the same, but there are differences in how to manage them in AEM. 
>
>For full details see [Launches for Content Fragments](/help/sites-cloud/administering/content-fragments/launches-for-content-fragments.md).
-->

Vous créez un *lancement*, puis, après avoir modifié et mis à jour vos pages de *lancement*, vous les *reconvertissez* en *Source*. Vous pouvez ensuite activer ces pages *Source* (de niveau supérieur). Le fait de promouvoir les pages duplique le contenu du lancement sur les pages source. Cette action peut être effectuée manuellement ou automatiquement (en fonction des champs définis lors de la création et de la modification du lancement).

Par exemple, les pages de produits saisonniers de votre boutique en ligne sont mises à jour chaque trimestre, afin que les produits présentés correspondent à la saison en cours. Pour préparer la prochaine mise à jour trimestrielle, vous pouvez créer un lancement des pages web appropriées. Tout au long du trimestre, les modifications suivantes sont cumulées dans la copie de lancement :

* Les modifications apportées aux pages source après des tâches de maintenance normales. Ces modifications sont automatiquement dupliquées dans les pages de lancement.
* Les modifications effectuées directement sur les pages de lancement en préparation du trimestre suivant.

Vous pouvez également :

* Naviguer dans le contenu de la branche de lancement pour ajoute ou supprimer des pages, si nécessaire.
* Prévisualisez comment le contenu publié se présentera à une date ultérieure spécifique.

À l’approche du trimestre suivant, vous convertissez les pages de lancement pour pouvoir modifier les pages source (contenant le contenu mis à jour). Vous pouvez convertir toutes les pages ou uniquement celles que vous avez modifiées.

Les lancements peuvent également être :

* Créés pour plusieurs branches racine. Bien que vous puissiez créer le lancement pour l’ensemble du site (et y apporter les modifications), cela peut s’avérer peu pratique, car l’ensemble du site doit être copié. Lorsque des centaines, voire des milliers de pages sont utilisées, les configurations et les performances du système dépendent de l’action de copie et ultérieurement des comparaisons nécessaires pour les tâches de conversion.
* Imbriqués (un lancement dans un lancement) pour permettre de créer un lancement à partir d’un lancement existant, de sorte que les créateurs et créatrices de contenu puissent tirer parti des changements déjà effectués plutôt que de devoir refaire les mêmes changements pour plusieurs lancements.

Cette section explique comment créer, modifier et convertir (et, le cas échéant, [supprimer](/help/sites-cloud/authoring/launches/creating.md#deleting-a-launch)) les pages de lancement de la console Sites ou de la console [Lancements](#the-launches-console) :

* [Création de lancements](/help/sites-cloud/authoring/launches/creating.md)
* [Modification de lancements](/help/sites-cloud/authoring/launches/editing.md)
* [Gestion des pages lors des lancements](/help/sites-cloud/authoring/launches/managing-pages.md)
* [Utilisation de Timewarp pour obtenir un aperçu du contenu en fonction des lancements](/help/sites-cloud/authoring/launches/preview.md)
* [Conversion de lancements](/help/sites-cloud/authoring/launches/promoting.md)

## Lancements – Ordre des événements {#launches-the-order-of-events}

Les lancements vous permettent de développer efficacement du contenu pour une prochaine publication d’une ou de plusieurs pages web activées.

Les lancements vous permettent d’effectuer les opérations suivantes :

* Créez une copie de vos pages source :
   * La copie est votre lancement.
   * Les pages source de niveau supérieur sont connues sous le nom de **Production**.
      * Les pages source peuvent provenir de plusieurs branches (distinctes).

  ![Ordre de fonctionnement des lancements](/help/sites-cloud/authoring/assets/launches-order.png)

* Modifier la configuration de lancement :
   * Ajoutez ou supprimez des pages et/ou des branches au/du lancement.
   * Modifiez des propriétés de lancement, comme le **titre**, la **date de lancement** et l’indicateur **Prêt pour la production**.
* Vous pouvez convertir et publier le contenu manuellement ou automatiquement :
   * Manuellement :
      * Effectuez la promotion de votre contenu de lancement dans la **cible** (pages source) lorsqu’elles sont prêtes à être publiées.
      * Publiez le contenu à partir des pages source (après leur promotion).
      * Effectuez la promotion de toutes les pages ou uniquement des pages modifiées.
   * Automatiquement, ce qui implique les étapes suivantes :
      * Le champ **Date de** **lancement** (**En direct**) : ce paramètre peut être défini lors de la création ou de la modification du lancement.
      * L’indicateur **Prêt pour la production** : cette option ne peut être définie que lors de la modification d’un lancement.
      * Si l’indicateur **Prêt pour la production** est défini, le lancement est automatiquement converti en pages de production à la **date** de **lancement** (**En direct**) spécifiée. Après la promotion, les pages de production sont automatiquement publiées.\
        Si aucune date n’a été définie, l’indicateur n’a aucun effet.
* Mettez à jour vos pages source et de lancement en parallèle :
   * Les modifications apportées aux pages source sont automatiquement appliquées à la copie de lancement (si elle a été configurée avec un héritage, c’est-à-dire comme Live Copy).
   * Les modifications apportées à la copie de lancement peuvent l’être sans interrompre les mises à jour automatiques ou modifier les pages source.

  ![Actions en parallèle](/help/sites-cloud/authoring/assets/launches-parallel.png)

* [Créer un lancement imbriqué](/help/sites-cloud/authoring/launches/creating.md#creating-a-nested-launch) (un lancement dans un autre lancement) :
   * La source est un lancement existant.
   * Vous pouvez [promouvoir un lancement imbriqué](/help/sites-cloud/authoring/launches/promoting.md#promoting-a-nested-launch) à toute cible ; il peut s’agir d’un lancement parent ou des pages source de niveau supérieur (production).

  ![Lancement imbriqué](/help/sites-cloud/authoring/assets/launches-nested.png)

  >[!CAUTION]
  >
  >La suppression d’un lancement supprime le lancement lui-même et tous les lancements imbriqués qui en sont des descendants.

>[!NOTE]
>
>La création et la modification de lancements exigent des droits d’accès à `/content/launches`, comme avec le groupe par défaut `content-authors`.
>
>Si vous rencontrez des problèmes, contactez votre administration système.

## Lancements dans les références (console Sites) {#launches-in-references-sites-console}

1. Dans la console **Sites**, accédez à la source du/des lancement(s).
1. Ouvrez le rail **Références** et sélectionnez la page source.
1. Sélectionnez **Lancements**. Les lancements existants sont répertoriés, ainsi que l’accès à la **Console Lancements** :

   ![Références des lancements dans la console Sites](/help/sites-cloud/authoring/assets/launches-references.png)

1. Sélectionnez le lancement approprié, puis la liste des actions possibles s’affiche :

   ![Actions à effectuer sur les lancements dans la console Sites](/help/sites-cloud/authoring/assets/launches-references-actions.png)

## Console Lancements {#the-launches-console}

>[!NOTE]
>
>Cette console est réservée aux lancements de pages.
>
>Pour gérer vos fragments de contenu, voir [Lancements pour les fragments de contenu](/help/sites-cloud/administering/content-fragments/launches-for-content-fragments.md).

La console Lancements donne un aperçu de vos lancements et vous permet d’agir sur ceux répertoriés.

![Console Lancements – Gestion du contenu](/help/sites-cloud/authoring/assets/launches-navigate-launches-console.png)

Vous pouvez accéder à la console via :

* La Console **Outils** : **Outils**, **Général**, **Lancements**.

* La **Console Lancements** dans la partie inférieure de la section **Lancements** du rail **Références** lors du parcours du contenu source dans la console Sites.

  ![Lance la console dans les références des lancements de la console Sites](/help/sites-cloud/authoring/assets/launches-references.png)

* Le bouton **Lancements** en haut à droite lors du parcours du contenu du lancement dans la console Sites :

  ![Option Lancements dans la console Sites](/help/sites-cloud/authoring/assets/launches-console-navigate-launch-content.png)
