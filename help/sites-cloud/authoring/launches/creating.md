---
title: Création de lancements
description: Vous pouvez créer un lancement afin de permettre la mise à jour d’une nouvelle version des pages web existantes en vue d’une activation future.
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Création de lancements {#creating-launches}

Créez un lancement pour permettre la mise à jour d’une nouvelle version des pages web existantes en vue d’une activation future. Lors de la création d’un lancement, vous devez spécifier un titre et la page source:

* The title appears in the [References](/help/sites-cloud/authoring/fundamentals/environment-tools.md#references) rail, from where authors can access them to work on them.
* Les pages enfants de la page source sont incluses, par défaut, dans le lancement. Si vous le souhaitez, vous pouvez n’utiliser que la page source
* Par défaut, Live Copy met automatiquement à jour les pages de lancement à mesure que les pages source changent. Vous pouvez spécifier qu’une copie statique est créée afin d’empêcher les modifications automatiques. <!--By default, [Live Copy](/help/sites-administering/msm.md) automatically updates the launch pages as the source pages change. You can specify that a static copy is created to prevent automatic changes.-->

Vous pouvez éventuellement indiquer la **date de lancement** (et l’heure) pour définir le moment auquel les pages de lancement doivent être converties et activées. However the **Launch Date** only operates in combination with the **Production Ready** flag (see [Editing a Launch Configuration](/help/sites-cloud/authoring/launches/editing.md#editing-a-launch-configuration)); for the actions to actually occur automatically, both must be set.

## Création d’un lancement {#creating-a-launch}

Vous pouvez créer un lancement à partir de la console Sites ou Lancements :

1. Ouvrez la console **Sites** ou **Lancements**. 

   >[!NOTE]
   >
   >Lorsque vous utilisez la console **Sites**, il est normal de naviguer jusqu’à l’emplacement de la page source, mais ce n’est pas obligatoire puisque vous pouvez naviguer en sélectionnant **Source de lancement** dans l’assistant.

1. Selon la console que vous utilisez :
   * **Lancements**:
      1. Sélectionnez **Créer un lancement** dans la barre d’outils pour ouvrir l’assistant.
   * **Sites**:
      1. Sélectionnez **Créer** dans la barre d’outils pour ouvrir la zone de sélection. 
      1. Dans cette zone, sélectionnez **Créer un lancement** pour ouvrir l’assistant.
   >[!NOTE]
   >
   >Dans la console **Sites**, vous pouvez également utiliser le [mode de sélection](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) pour sélectionner une page avant de sélectionner **Créer**.
   >
   >La page sélectionnée sera alors utilisée comme page source initiale.

1. À l’étape **Sélectionner la source**, vous devez **Ajouter des pages**. Vous pouvez sélectionner plusieurs pages en spécifiant un chemin pour chacune d’elles : 
   * Naviguez jusqu’à l’emplacement qui vous intéresse.
   * Sélectionnez les pages source et confirmez (cochez).
   Recommencez l’étape selon vos besoins.

   ![Sélectionner la source de lancement](/help/sites-cloud/authoring/assets/launches-select-source.png)

   >[!NOTE]
   >
   >Pour ajouter des pages et/ou des branches à un lancement, elles doivent exister dans un site, c’est-à-dire sous la racine du niveau supérieur commun.
   >
   >Si le site contient des racines de langage en dessous du niveau supérieur, les pages et les branches d’un lancement doivent se trouver sous une racine de langage commun.

1. Pour chaque entrée vous pouvez indiquer s’il faut ou non :

   * **Inclure les sous-pages**:

      * Indiquez si vous souhaitez créer le lancement avec ou sans les pages enfants.  Par défaut, ces sous-pages sont intégrées.
   Poursuivez en cliquant sur **Suivant**. 

   ![Sélectionner la source de lancement](/help/sites-cloud/authoring/assets/launches-select-source-2.png)

1. À l’étape **Propriétés** de l’assistant, vous pouvez définir les paramètres suivants : 

   * **Titre du lancement **: nom du lancement. Ce nom doit être explicite pour les auteurs.
   * **avec le contenu existant** : le contenu d’origine sera utilisé pour créer le lancement. 
   * **Utiliser un nouveau modèle pour remplacer la page** : voir [Création d’un lancement avec un nouveau modèle](#create-launch-with-new-template) pour plus de détails. 
   * **Hériter des données actives de la page source** : sélectionnez cette option pour mettre automatiquement à jour le contenu des pages de lancement lors de la modification des pages source. Cette option permet d’effectuer cette opération en faisant du lancement une copie en direct. Par défaut, cette option est sélectionnée. <!--Select this option to automatically update the content of launch pages when the source pages change. This option achieves this by making the launch a [live copy](/help/sites-administering/msm.md). By default, this option is selected.-->
   * **Date de lancement** : date et heure d’activation de la copie de lancement (selon l’indicateur **Prêt pour la production**. Voir [Lancements - Ordre des événements](/help/sites-cloud/authoring/launches/overview.md#launches-the-order-of-events)).
   ![Propriétés de lancement](/help/sites-cloud/authoring/assets/launches-properties.png)

1. Cliquez sur **Créer** pour terminer le processus et créer le lancement. La boîte de dialogue de confirmation vous invite à ouvrir le lancement immédiatement :

   Si vous revenez à la console (en cliquant sur **Terminé**) vous pouvez afficher (et accéder à) votre lancement à partir de :

   * The [**Launches **console](/help/sites-cloud/authoring/launches/overview.md#the-launches-console)
   * The [**References **in the** Sites **console](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console)

### Create Launch with New Template {#create-launch-with-new-template}

Lors de la création d’un lancement, vous pouvez utiliser un nouveau modèle :

>[!NOTE]
>
>Cette option est uniquement disponible lors de la création d’un lancement à partir de **Sites**. Elle n’est pas disponible lors de la création d’un lancement depuis la console **Lancements**.

![Création d’un lancement avec un nouveau modèle](/help/sites-cloud/authoring/assets/launches-create-new-template.png)

La sélection de cette option va :

* Mettez à jour les autres options disponibles,
* Insérez une nouvelle étape où vous pouvez sélectionner le modèle requis.

![Sélection d’un nouveau modèle](/help/sites-cloud/authoring/assets/launches-select-template.png)

>[!CAUTION]
>
>Si un autre modèle est utilisé, la nouvelle page est vide. Du fait de la structure de page différente, aucun contenu n’est copié.
>
>Ce mécanisme peut être utilisé pour modifier le modèle d’une [page existante](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page), bien que la perte du contenu doit être envisagée.

### Création d’un lancement imbriqué {#creating-a-nested-launch}

La création d’un lancement imbriqué (lancement dans un lancement) vous permet de créer un lancement à partir d’un lancement existant pour que les développeurs de contenu exploitent les modifications déjà apportées, au lieu de répercuter ces mêmes modifications à plusieurs reprises pour chaque lancement.

>[!NOTE]
>
>Voir aussi [Promotion d’un lancement imbriqué](/help/sites-cloud/authoring/launches/promoting.md#promoting-a-nested-launch).

#### Création d’un lancement imbriqué - Console de lancements {#creating-a-nested-launch-launches-console}

Creating a nested launch from the **Launches** console is basically the same as creating any other form of launch, with the exception that you need to navigate to the launches branch `/content/launches`:

1. Dans la console **Lancements**, sélectionnez **Créer**.
1. Select **Add Pages**, then navigate to the launches branch by specifying `/content/launches` in the filter. Sélectionnez la branche requise et confirmez avec **Sélectionner** :

   ![Création d’un lancement imbriqué](/help/sites-cloud/authoring/assets/launches-create-nested.png)

1. Continuez avec **Suivant** et indiquez les **propriétés**, comme pour tout autre lancement.

   ![Sélectionner la source du lancement imbriqué](/help/sites-cloud/authoring/assets/launches-create-nested-select.png)

#### Création d’un lancement imbriqué - Console de sites {#creating-a-nested-launch-sites-console}

Pour créer un lancement imbriqué à partir de la console de **sites**, sur la base d’un lancement existant : 

1. Accédez à [Lancement à partir des références (console Sites)](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console) pour afficher les actions disponibles.
1. Sélectionnez **Créer un lancement** pour ouvrir l’assistant (puisque la source a déjà été sélectionnée, l’assistant ignore l’étape **Sélectionner la source**). 
1. Entrez le **titre du lancement** et tous les autres détails demandés (comme s’il s’agissait d’un lancement normal). 
1. Cliquez sur **Créer** pour terminer le processus et créer le lancement. La boîte de dialogue de confirmation vous invite à ouvrir le lancement immédiatement :

If you select **Done**, you are returned to the **References** rail of the **Sites** console, if you select the appropriate page your new launch is shown.

### Suppression d’un lancement {#deleting-a-launch}

Vous pouvez supprimer un lancement à partir de la console [Lancements](/help/sites-cloud/authoring/launches/overview.md#the-launches-console) :

* Sélectionnez le lancement en appuyant/cliquant sur la miniature.
* La barre d’outils s’affiche. Sélectionnez supprimer.
* Confirmez l’action.

>[!CAUTION]
>
>La suppression d’un lancement supprime le lancement lui-même et tous les lancements imbriqués qui en sont des descendants.
