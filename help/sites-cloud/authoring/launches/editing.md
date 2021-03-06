---
title: Modification de lancements
description: Après avoir créé un lancement pour votre page (ou un jeu de pages), vous pouvez modifier le contenu dans la copie de lancement de la ou des pages.
exl-id: d3cd3383-e0a0-4019-9f97-8baa3be99e6e
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 100%

---

# Modification de lancements {#editing-launches}

## Modification de pages de lancement {#editing-launch-pages}

Après avoir créé un lancement pour une page (ou un jeu de pages), vous pouvez modifier le contenu dans la copie de lancement correspondante.

1. Accédez à [Lancement à partir des références (console Sites)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console) pour afficher les actions disponibles.
1. Sélectionnez **Aller à la page** pour ouvrir la page d’édition.

Lors de la modification de la page, une indication apparaît dans la barre d’outils supérieure, ainsi que les options **Quitter** et **Naviguer** :

![Quitter et Naviguer apparaissent depuis l’éditeur de page](/help/sites-cloud/authoring/assets/launches-edit-01.png)

>[!NOTE]
>
>Vous n’êtes pas autorisé à déplacer une page au cours d’un lancement. Tenter cette action déclenchera un message d’avertissement :
>
>* Avertissement : Cette page est la source du lancement. Le déplacement de cette page n’est pas autorisé.


### Modification de l’objet des pages de lancement en Live Copy {#editing-launch-pages-subject-to-a-live-copy}

Si votre lancement est basé sur une [Live Copy](/help/sites-cloud/administering/msm/overview.md) :

* vous verrez des symboles de verrouillage (petits verrous) lors de la modification d’un composant (de son contenu ou de ses propriétés) ;
* vous verrez l’onglet **Live Copy** dans **Propriétés de la page**.

Une Live Copy est utilisée pour synchroniser le contenu *depuis* la branche source *vers* votre branche de lancement (afin que votre lancement soit à jour avec les modifications apportées à la source).

Vous pouvez apporter des modifications de la même manière que vous pouvez modifier une Live Copy standard, par exemple :

* Cliquer sur un cadenas fermé interrompt cette synchronisation et vous permet d’apporter de nouvelles mises à jour au contenu de votre lancement. Une fois le cadenas déverrouillé (ouvert), vos modifications ne seront remplacées par aucune modification effectuée au même emplacement dans la branche de source.
* **Suspendre** (et **Reprendre**) l’héritage pour une page spécifique.

Pour plus d’informations, voir [Modification du contenu d’une Live Copy](/help/sites-cloud/administering/msm/creating-live-copies.md).

## Comparaison d’une page de lancement avec sa page source {#comparing-a-launch-page-to-its-source-page}

Pour suivre les modifications que vous avez apportées, vous pouvez afficher le lancement dans **Références** et comparer la page de lancement à sa page source :

1. Dans la console **Sites**, [accédez aux pages source de votre lancement et sélectionnez-en une](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Ouvrez le panneau **[Références](/help/sites-cloud/authoring/getting-started/basic-handling.md#references)** et sélectionnez **Lancements**.
1. Sélectionnez votre lancement spécifique, puis **Comparer à la source** :

   ![Comparaison du lancement à la source](/help/sites-cloud/authoring/assets/launches-compare.png)

1. Les deux pages (de lancement et source) s’ouvrent côte à côte.

   Pour des informations complètes sur l’utilisation de cette fonction, consultez [Différence entre les pages](/help/sites-cloud/authoring/features/page-diff.md).

## Modification des pages source utilisées {#changing-the-source-pages-used}

Vous pouvez à tout moment ajouter ou supprimer des pages vers/depuis la plage de pages source pour un lancement :

1. Accédez au lancement et sélectionnez-le depuis, au choix :
   * la console [Lancements](/help/sites-cloud/authoring/launches/overview.md#the-launches-console) :
      * Sélectionnez **Modifier**.
   * [Références (console Sites)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console) pour afficher les actions disponibles :
      * Sélectionnez **Modifier le lancement**.
      * Les pages source s’affichent.
1. Effectuez les modifications requises, puis confirmez avec **Enregistrer**.

>[!NOTE]
>
>Pour ajouter des pages à un lancement, celles-ci doivent se trouver sous une racine de langue commune (c’est-à-dire, sur un seul site).

## Modification d’une configuration de lancement {#editing-a-launch-configuration}

Vous pouvez à tout moment modifier les propriétés d’un lancement :

1. Accédez au lancement et sélectionnez-le depuis, au choix :
   * la [console Lancements](/help/sites-cloud/authoring/launches/overview.md#the-launches-console) :
      * Sélectionnez **Propriétés**.
   * [Références (console Sites)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console) pour afficher les actions disponibles :
      * Sélectionnez **Modifier les propriétés**.
      * Les détails s’affichent.
1. Effectuez les modifications requises, puis confirmez avec **Enregistrer**.
   * Consultez [Lancements – Ordre des événements](/help/sites-cloud/authoring/launches/overview.md#launches-the-order-of-events) pour plus d’informations sur l’objectif et l’interaction des champs **Date de lancement** et **Prêt pour la production**.

## Identification du statut de lancement d’une page {#discovering-the-launch-status-of-a-page}

Le statut s’affiche lorsque vous sélectionnez un lancement spécifique dans l’onglet Références (voir [Lancements dans les références (console Sites)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console)).

![Découverte du statut de lancement](/help/sites-cloud/authoring/assets/launches-status.png)
