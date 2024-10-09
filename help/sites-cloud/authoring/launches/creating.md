---
title: Création de lancements
description: Vous pouvez créer un lancement pour permettre la mise à jour d’une nouvelle version des pages web existantes en vue d’une activation future.
exl-id: 216ccb7a-1409-4f55-8be2-2b088f91a430
solution: Experience Manager Sites
feature: Authoring, Launches
role: User
source-git-commit: b5ded40d1cb8b8fab28583467b68c4586eecf1a0
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 96%

---

# Création de lancements {#creating-launches}

Créez un lancement pour permettre la mise à jour d’une nouvelle version des pages web existantes en vue d’une activation future. Lors de la création d’un lancement, vous devez spécifier un titre et la page source :

* Le titre apparaît dans le rail [Références](/help/sites-cloud/authoring/sites-console/console-side-panel.md#references), à partir duquel les auteurs peuvent accéder aux références afin de les modifier.
* Les pages enfants de la page source sont incluses par défaut dans le lancement. Si vous le souhaitez, vous pouvez n’utiliser que la page source.
* Par défaut, [Live Copy](/help/sites-cloud/administering/msm/overview.md) met automatiquement à jour les pages de lancement au fur et à mesure des modifications des pages source. Vous pouvez spécifier qu’une copie statique soit créée afin d’empêcher les modifications automatiques.

Vous pouvez éventuellement indiquer la **date de lancement** (et l’heure) pour définir le moment auquel les pages de lancement doivent être promues et activées. Toutefois, la **date de lancement** fonctionne uniquement en conjonction avec l’indicateur **Prêt pour la production** (voir [Modification d’une configuration de lancement](/help/sites-cloud/authoring/launches/editing.md#editing-a-launch-configuration)). Pour que les actions se produisent automatiquement, les deux doivent être définis.

>[!NOTE]
>
>Lorsque vous créez un lancement, les pages situées plus haut dans la hiérarchie ne sont pas des copies des pages source. Il s’agit d’espaces réservés, créés avec le modèle :
>
>* `/libs/launches/templates/outofscope`
>
>Ces pages ne peuvent pas être modifiées. Le message s’affiche :
>
>* **Cette page ne fait pas partie du lancement. Accéder à la page de production**

## Création d’un lancement {#creating-a-launch}

Vous pouvez créer un lancement à partir de la console Sites ou Lancements :

1. Ouvrez la console **Sites** ou **Lancements**.

   >[!NOTE]
   >
   >Lors de l’utilisation de la console **Sites**, il est courant de naviguer jusqu’à l’emplacement de la page source, mais cela n’est pas obligatoire, car vous pouvez y accéder lorsque vous sélectionnez l’option **Source de lancement** dans l’assistant.

1. Selon la console que vous utilisez :
   * **Lancements** :
      1. Sélectionnez **Créer un lancement** depuis la barre d’outils pour ouvrir l’assistant.
   * **Sites** :
      1. Sélectionnez **Créer** dans la barre d’outils pour ouvrir la zone de sélection.
      1. Dans cette zone, sélectionnez **Créer un lancement** pour ouvrir l’assistant.

   >[!NOTE]
   >
   >Dans la console **Sites**, vous pouvez également utiliser le [mode de sélection](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources) pour choisir une page avant de sélectionner **Créer**.
   >
   >La page sélectionnée sera alors utilisée comme page source initiale.

1. À l’étape **Sélectionner la source**, vous devez **Ajouter des pages**. Vous pouvez sélectionner plusieurs pages en spécifiant un chemin pour chacune d’elles :
   * Accédez à l’emplacement qui vous intéresse.
   * Sélectionnez la ou les pages sources et confirmez (coche).

   Recommencez l’étape selon vos besoins.

   ![Sélection de la source de lancement](/help/sites-cloud/authoring/assets/launches-select-source.png)

   >[!NOTE]
   >
   >Pour ajouter des pages et/ou des branches à un lancement, elles doivent se trouver dans un site ; c’est-à-dire sous une racine de niveau supérieur commune.
   >
   >Si un site contient des racines de langue sous le niveau supérieur, les pages et les branches d’un lancement doivent se trouver sous une racine de langue commune.

1. Pour chaque entrée, vous pouvez indiquer si :

   * **Inclure les sous-pages** :

      * Indiquez si vous souhaitez créer le lancement avec ou sans les pages enfants.  Par défaut, ces sous-pages sont intégrées.

   Poursuivez en cliquant sur **Suivant**.

   ![Sélection de la source de lancement](/help/sites-cloud/authoring/assets/launches-select-source-2.png)

1. À l’étape **Propriétés** de l’assistant, vous pouvez définir les paramètres suivants :

   * **Titre du lancement** : nom du lancement. Le nom doit avoir un sens pour les personnes chargées de la création.
   * **avec le contenu existant** : le contenu d’origine sera utilisé pour créer le lancement.
   * **en utilisant un nouveau modèle pour remplacer la page** : voir [Création d’un lancement avec un nouveau modèle](#create-launch-with-new-template) pour plus de détails.
   * **Hériter des données actives de la page source** : sélectionnez cette option pour mettre automatiquement à jour le contenu des pages de lancement lors de la modification des pages source. Cette option transforme le lancement en [Live Copy](/help/sites-cloud/administering/msm/overview.md). Par défaut, cette option est sélectionnée.-->
   * **Date de lancement** : date et heure d’activation de la copie de lancement (selon l’indicateur **Prêt pour la production**. Voir [Lancements – Ordre des événements](/help/sites-cloud/authoring/launches/overview.md#launches-the-order-of-events)).

   ![Propriétés de lancement](/help/sites-cloud/authoring/assets/launches-properties.png)

1. Cliquez ou appuyez sur **Créer** pour terminer le processus et créer votre lancement. La boîte de dialogue de confirmation vous demandera si vous souhaitez ouvrir le lancement immédiatement.

   Si vous renvoyez la console (avec **Terminé**), vous pouvez afficher (et accéder à) votre lancement à partir de :

   * la [**console Lancements**](/help/sites-cloud/authoring/launches/overview.md#the-launches-console) ;
   * les [**références** de la **console Sites**](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console).

### Créer un lancement avec un nouveau modèle {#create-launch-with-new-template}

Lors de la création d’un lancement, vous pouvez utiliser un nouveau modèle :

>[!NOTE]
>
>Cette option est uniquement disponible lors de la création d’un lancement à partir de la console **Sites**. Elle n’est pas disponible lors de la création d’un lancement depuis la console **Lancements**.

![Création d’un lancement avec un nouveau modèle](/help/sites-cloud/authoring/assets/launches-create-new-template.png)

La sélection de cette option va :

* mettre à jour les autres options disponibles ;
* inclure une nouvelle étape dans laquelle vous pouvez sélectionner le modèle requis.

![Sélection d’un nouveau modèle](/help/sites-cloud/authoring/assets/launches-select-template.png)

>[!CAUTION]
>
>Étant donné qu’un modèle différent est utilisé, la nouvelle page est vide. En raison de la différence de structure de page, aucun contenu n’est copié.
>
>Ce mécanisme peut être utilisé pour modifier le modèle d’une [page existante](/help/sites-cloud/authoring/sites-console/creating-pages.md#creating-a-new-page), bien que la perte du contenu doit être envisagée.

### Création d’un lancement imbriqué {#creating-a-nested-launch}

La création d’un lancement imbriqué (lancement dans un lancement) vous permet de créer un lancement à partir d’un lancement existant pour que les développeurs de contenu exploitent les modifications déjà apportées, au lieu de répercuter ces mêmes modifications à plusieurs reprises pour chaque lancement.

>[!NOTE]
>
>Voir aussi [Promotion d’un lancement imbriqué](/help/sites-cloud/authoring/launches/promoting.md#promoting-a-nested-launch).

#### Création d’un lancement imbriqué – Console Lancements {#creating-a-nested-launch-launches-console}

La création d’un lancement imbriqué à partir de la console **Lancements** est similaire à la création de tout autre type de lancement, si ce n’est que vous devez accéder à la branche de lancements `/content/launches` :

1. Dans la console **Lancements**, sélectionnez **Créer**.
1. Sélectionnez **Ajouter des pages**, puis accédez à la branche de lancements en spécifiant `/content/launches` dans le rail **Filtres**. Sélectionnez la branche requise et confirmez avec **Sélectionner** :

   ![Création d’un lancement imbriqué](/help/sites-cloud/authoring/assets/launches-create-nested.png)

1. Poursuivez en cliquant sur **Suivant**.

1. Remplissez les **Propriétés** comme pour tout autre lancement.

1. Terminez avec **Créer**.

#### Création d’un lancement imbriqué – Console Sites {#creating-a-nested-launch-sites-console}

Pour créer un lancement imbriqué à partir de la console **Sites**, sur la base d’un lancement existant :

1. Accédez à [Lancement à partir des références (console Sites)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console) pour afficher les actions disponibles.
1. Sélectionnez **Créer un lancement** pour ouvrir l’assistant (puisque la source a déjà été sélectionnée, l’assistant ignore l’étape **Sélectionner la source**).
1. Entrez le **titre du lancement** et tous les autres détails demandés (comme s’il s’agissait d’un lancement normal).
1. Cliquez ou appuyez sur **Créer** pour terminer le processus et créer votre lancement. La boîte de dialogue de confirmation vous demandera si vous souhaitez ouvrir le lancement immédiatement.

Si vous sélectionnez **Terminé**, vous revenez au rail **Références** de la console **Sites**. Si vous sélectionnez la page appropriée, votre nouveau lancement est affiché.

### Clonage d’un lancement {#cloning-a-launch}

Vous pouvez cloner un lancement à partir de la [console de lancements](/help/sites-cloud/authoring/launches/overview.md#the-launches-console) :

* Sélectionnez le lancement en appuyant/cliquant sur la miniature.
* La barre d’outils s’affiche. Sélectionnez Cloner.
   * Le clone s’affiche dans la console.

## Suppression d’un lancement {#deleting-a-launch}

Vous pouvez supprimer un lancement à partir de la [console des lancements](/help/sites-cloud/authoring/launches/overview.md#the-launches-console) :

* Sélectionnez le lancement en appuyant/cliquant sur la miniature.
* La barre d’outils s’affiche. Sélectionnez Supprimer.
* Confirmez l’action.

>[!CAUTION]
>
>La suppression d’un lancement supprime le lancement lui-même et tous les lancements imbriqués qui en sont des descendants.
