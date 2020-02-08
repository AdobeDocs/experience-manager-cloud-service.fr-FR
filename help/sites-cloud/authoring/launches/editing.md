---
title: Modification de lancements
description: 'Après avoir créé un lancement pour votre page (ou un jeu de pages), vous pouvez modifier le contenu dans la copie de lancement de la ou des pages. '
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Modification de lancements {#editing-launches}

## Modification de pages de lancement {#editing-launch-pages}

Après avoir créé un lancement pour une page (ou un jeu de pages), vous pouvez modifier le contenu dans la copie de lancement correspondante.

1. Accédez à [Lancement à partir des références (console Sites)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console) pour afficher les actions disponibles.
1. Sélectionnez **Aller à la page** pour ouvrir la page d’édition.

### Modification de l’objet des pages de lancement en Live Copy {#editing-launch-pages-subject-to-a-live-copy}

If your launch is based upon a live copy then you will: <!--If your launch is based upon a [live copy](/help/sites-administering/msm.md) then you will:-->

* Voir symboles de verrouillage (petits cadenas) lorsque vous modifiez un composant (contenu et/ou propriétés).
* See the **Live Copy** tab in **Page Properties**

Une Live Copy est utilisée pour synchroniser le contenu *de* la branche source *vers* votre branche de lancement (pour conserver votre lancement à jour avec les modifications apportées dans la source).

Vous pouvez apporter des modifications de la même manière que vous pouvez modifier une Live Copy standard, par exemple :

* Cliquer sur un cadenas fermé interrompt cette synchronisation et vous permet d’apporter de nouvelles mises à jour au contenu de votre lancement. Une fois le cadenas déverrouillé (ouvert), vos modifications ne seront remplacées par aucune modification effectuée au même emplacement dans la branche de source.
* **Suspendre** (et **Reprendre**) l’héritage pour une page spécifique.

Pour plus d’informations, voir Modification du contenu d’une Live Copy. <!--See [Changing Live Copy Content](/help/sites-administering/msm-livecopy.md#changing-live-copy-content) for further information.-->

## Comparaison d’une page de lancement avec sa page source {#comparing-a-launch-page-to-its-source-page}

Pour suivre les modifications que vous avez apportées, vous pouvez afficher le lancement dans **Références** et comparer la page de lancement avec sa page source :

1. Dans la console **Sites**, [accédez à la page source de votre lancement et sélectionnez-la](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Ouvrez le panneau **[Références](/help/sites-cloud/authoring/getting-started/basic-handling.md#references)**et sélectionnez **Lancements**.
1. Sélectionnez votre lancement spécifique, puis **Comparer à la source** :

   ![Comparaison du lancement à la source](/help/sites-cloud/authoring/assets/launches-compare.png)

1. Les deux pages (de lancement et source) s’ouvrent côte à côte.

   Pour des informations complètes sur l’utilisation de cette fonction, voir [Différence entre les pages](/help/sites-cloud/authoring/features/page-diff.md).

## Modification des pages source utilisées {#changing-the-source-pages-used}

Vous pouvez à tout moment ajouter ou supprimer des pages vers/depuis la plage de pages source pour un lancement : 

1. Accédez au lancement et sélectionnez-le depuis, au choix :
   * The [Launches console](/help/sites-cloud/authoring/launches/overview.md#the-launches-console):
      * Sélectionnez **Modifier**.
   * [Références (console Sites)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console) pour afficher les actions disponibles :
      * Sélectionnez **Modifier le lancement**. 
      * Les pages source s’affichent.
1. Apportez les modifications requises, puis confirmez-les avec **Enregistrer**.

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
1. Apportez les modifications requises, puis confirmez-les avec **Enregistrer**.
   * Reportez-vous à [Lancements - Ordre des événements](/help/sites-cloud/authoring/launches/overview.md#launches-the-order-of-events) pour obtenir des informations sur l’objectif et l’interaction des champs **Date de lancement** et **Prêt pour la production**.

## Identification de l’état de lancement d’une page {#discovering-the-launch-status-of-a-page}

L’état s’affiche lorsque vous sélectionnez un lancement spécifique dans l’onglet Références (voir [Lancements dans les références (console Sites)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console)).

![Découverte de l’état de lancement](/help/sites-cloud/authoring/assets/launches-status.png)
