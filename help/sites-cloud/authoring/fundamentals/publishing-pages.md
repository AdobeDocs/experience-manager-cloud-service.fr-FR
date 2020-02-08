---
title: Publication de pages
description: Publication et annulation de publication de pages à l’aide d’AEM
translation-type: tm+mt
source-git-commit: e88a814a901d7fa0da2675fa6017c66d61a73445

---


# Publication de pages {#publishing-pages}

Une fois le contenu créé et révisé dans l’environnement de création, l’objectif est de le [rendre disponible sur votre site web public](/help/sites-cloud/authoring/getting-started/concepts.md) (votre environnement de publication).

On parle alors de publication d’une page, ou d’annulation de publication lorsque vous souhaitez retirer une page de l’environnement de publication. En cas de publication et d’annulation de la publication, la page reste disponible pour d’autres modifications dans l’environnement de création jusqu’à ce que vous la supprimiez.

Vous pouvez publier/annuler la publication d’une page immédiatement ou à une date/heure prédéfinie dans le futur.

## Terminologie {#terminology}

Vous pouvez rencontrer différents termes liés à la publication lorsque vous travaillez avec AEM.

* **Publier / Annuler la publication**
   * Il s’agit des principaux termes des actions qui rendent votre contenu public dans votre environnement de publication (ou pas).
   * Il s’agit des termes utilisés dans la documentation AEM.
* **Activer / désactiver**
   * Ces termes sont synonymes de publication/annulation de publication.
   * Ces termes ont été utilisés dans les versions précédentes d’AEM.
* **Répliquer / Réplication**
   * Il s’agit des termes techniques décrivant le mouvement des données (contenu de page, fichiers, code, commentaires utilisateur, par exemple) d’un environnement à un autre lorsque vous publiez une page.
   * Ces termes sont principalement utilisés par les développeurs.

## Publication de pages {#publishing-pages-1}

Selon votre emplacement, vous pouvez effectuer la publication :

* [À partir de l’éditeur de page](#publishing-from-the-editor)
* [À partir de la console Sites](#publishing-from-the-console)

>[!NOTE]
>
>Si vous ne possédez pas les privilèges requis pour publier une page spécifique :
>
>* Un workflow est déclenché afin d’aviser la personne concernée de votre demande de publication.
>* Ce workflow a peut-être été personnalisé par votre équipe de développement.
>* Un message s’affiche brièvement pour vous informer que le workflow a été déclenché.

<!--
>* This [workflow may have been customized](/help/sites-developing/workflows-models.md#main-pars-procedure-6fe6) by your development team.
>* A message will be displayed briefly to notify you that the workflow was triggered.
-->

### Publication à partir de l’éditeur {#publishing-from-the-editor}

Si vous modifiez une page, vous pouvez la publier directement à partir de l’éditeur.

1. Select the **Page Information** icon to open the menu and then the **Publish Page** option.

   ![Publication d’une page via les options de page](/help/sites-cloud/authoring/assets/publishing-page-options.png)

1. Selon que la page comporte des références qui doivent être publiées :

   * La page sera publiée directement, s’il n’y a aucune référence à publier.
   * Si la page comporte des références à publier, celles-ci seront répertoriées dans l’assistant **Publier**, où vous pourrez accomplir ce qui suit :
      * Specify which of the assets/tags/etc. you want to publish together with the page, then use **Publish** to complete the process.
      * Sélectionner **Annuler** pour abandonner l’opération.
   ![Publication de références avec la page](/help/sites-cloud/authoring/assets/publishing-references.png)

1. Selecting **Publish** will replicate the page to the publish environment. Une bannière d’informations est affichée dans l’éditeur de page pour confirmer l’opération de publication.

   ![Publier la bannière d’informations d’état](/help/sites-cloud/authoring/assets/publishing-info.png)

   Lorsque vous affichez la même page dans la console, l’état de publication mis à jour est visible.

   ![Statut de publication de page en mode Colonne dans la console des sites](/help/sites-cloud/authoring/assets/publishing-status-console-column.png)

>[!NOTE]
>
>La publication à partir de l’éditeur est une publication superficielle, c’est-à-dire que seule la ou les pages sélectionnées sont publiées et que les pages enfants ne le sont pas.

### Publication à partir de la console {#publishing-from-the-console}

La console Sites propose deux options de publication :

* [Publication rapide](#quick-publish)
* [Gérer la publication](#manage-publication)

#### Publication rapide {#quick-publish}

**La publication** rapide est destinée aux cas simples et publie immédiatement la ou les pages sélectionnées sans autre interaction. De ce fait, toute autre référence non publiée l’est aussi automatiquement.

Pour publier une page avec l’option Publication rapide :

1. Select the page or pages in the sites console and click on the **Quick Publish** button.

   ![Sélection de pages pour publication](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. In the Quick Publish dialog, confirm the publication by clicking on **Publish** or cancel by clicking on **Cancel**. Pour rappel, toute référence non publiée sera également publiée automatiquement.

   ![Confirmation de publication rapide](/help/sites-cloud/authoring/assets/publishing-quick-publish.png)

1. Lorsque la page est publiée, une alerte est affichée pour confirmer la publication.

>[!NOTE]
>
>L’option de publication rapide est dite superficielle ; en d’autres termes, seules la ou les pages sélectionnées sont publiées (les éventuelles pages enfants ne le sont pas).

#### Gérer la publication {#manage-publication}

**Gérer la publication** offre plus d’options que la publication rapide, ce qui permet d’inclure des pages enfants, de personnaliser les références et de démarrer les processus applicables, tout en offrant la possibilité de publier ultérieurement.

Pour modifier ou annuler la publication d’une page à l’aide de l’option Gérer la publication :

1. Select the page or pages in the sites console and click on the **Manage Publication** button.

   ![Sélection de pages pour publication](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. The **Manage Publication** wizard starts. The first step, **Options**, allows you to:

   * Publier ou annuler la publication des pages sélectionnées.
   * Effectuer une action maintenant ou ultérieurement.
   La publication différée lance un workflow pour modifier la ou les pages sélectionnées à l’heure indiquée. Si vous optez pour une annulation différée de la publication, un workflow est lancé pour annuler la publication de la ou des pages sélectionnées à une heure déterminée.

   Pour annuler une publication/annulation de publication ultérieure, rendez-vous dans la console Processus pour mettre un terme au processus correspondant. <!--If you want to cancel a publish/unpublish later, go to the [Workflow Console](/help/sites-administering/workflows.md) to terminate the corresponding workflow.-->

   ![Gérer les options de publication](/help/sites-cloud/authoring/assets/publishing-manage-publication-options.png)

   Cliquez sur **Suivant** pour continuer.

1. In the next step of the Manage Publication wizard, **Scope**, you can define the scope of the publication/un-publication such as including to include child pages and/or including references.

   ![Gérer l’étendue de la publication](/help/sites-cloud/authoring/assets/publishing-manage-publication-scope.png)

   You can use the **Add Content** button to add additional pages to the list of pages to be published in case you neglected to select one before starting the Manage Publication wizard.

   Le bouton Ajouter du contenu lance l’[explorateur de chemins d’accès](/help/sites-cloud/authoring/fundamentals/environment-tools.md#path-browser), qui vous permet de sélectionner du contenu.

   Select the required pages and then click **Select** to add the content to the wizard or **Cancel **to cancel the selection and return to the wizard.

   De retour dans l’assistant, vous pouvez sélectionner un élément dans la liste afin de configurer d’autres options :

   * Inclure ses enfants.
   * Le supprimer de la sélection.
   * Gérer ses références publiées.
   ![Gestion des pages de sélection des publications](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

   Clicking **Include Children** opens a dialogue allowing you to:

   * Inclure seulement les enfants immédiats.
   * Inclure seulement les pages modifiées.
   * Inclure seulement les pages déjà publiées.
   Click **Add** to add the children pages to the list of pages to be published or unpublished based on the selection options. Click **Cancel** to cancel the selection and return to the wizard.

   ![Gérer la publication, y compris les enfants](/help/sites-cloud/authoring/assets/publishing-include-children.png)

   De retour dans l’assistant, les pages ajoutées sont affichées en fonction des options que vous avez sélectionnées dans la boîte de dialogue Inclure les enfants.

   You can view and modify the references to be published or unpublished for a page by selecting it and then clicking the **Published References** button.

   ![Gérer les options de publication](/help/sites-cloud/authoring/assets/publishing-manage-publication-references.png)

   The **Published References** dialog displays the references for the selected content. Par défaut, elles sont toutes sélectionnées et seront publiées/non publiées, mais vous pouvez les désélectionner pour qu’elles ne soient pas incluses dans l’action.

   Click **Done** to save your changes or **Cancel** to cancel the selection and return to the wizard.

   De retour dans l’assistant, la colonne **Références** est mise à jour afin de tenir compte des références que vous avez choisi de publier ou dont la publication doit être annulée.

   ![Gestion des pages de sélection des publications](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

1. Click **Publish** to complete.

   De retour dans la console Sites, un message de notification s’affiche pour confirmer la publication.

1. If the published pages are associated with workflows, they may be shown in a final **Workflows** step of the publication wizard.

   >[!NOTE]
   >
   >The **Workflows** step will be shown based on what rights your user may or may not have. See the previous note on this page regarding publishing privileges as well as Managing Access to Workflows and [Applying Workflows to Pages](/help/sites-cloud/authoring/workflows/applying.md) for details.
   <!--
   >The **Workflows** step will be shown based on what rights your user may or may not have. See the previous note on this page regarding publishing privileges as well as [Managing Access to Workflows](/help/sites-administering/workflows-managing.md) and [Applying Workflows to Pages](/help/sites-cloud/authoring/workflows/applying.md) for details.
   -->

   Les ressources sont regroupées en fonction des workflows déclenchés et de chaque option proposée pour :

   * définir le titre du workflow ;
   * Keep the workflow package, provided that the workflow has multi-resource support. <!--Keep the workflow package, provided that the workflow has [multi-resource support](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support).-->
   * définir le titre du workflow, si l’option de conservation du module de workflow a été sélectionnée.
   Click **Publish** or **Publish Later** to complete the publication.

## Annulation de la publication des pages {#unpublishing-pages}

L’annulation de la publication d’une page supprime cette page de votre environnement de publication, de sorte que vos lecteurs ne puissent plus y accéder.

In a [manner similar to publishing](#publishing-pages), one or more pages can be unpublished:

* [À partir de l’éditeur de page](#unpublishing-from-the-editor)
* [À partir de la console Sites](#unpublishing-from-the-console)

### Annulation de la publication à partir de l’éditeur {#unpublishing-from-the-editor}

Lors de la modification d’une page, si vous souhaitez annuler sa publication, sélectionnez **Annuler la publication de la page** dans le menu **Informations sur la page**, comme vous le feriez pour [publier la page](#publishing-from-the-editor).

### Annulation de la publication à partir de la console {#unpublishing-from-the-console}

De la même façon que vous [utilisez l’option Gérer la publication pour publier une page](#manage-publication), vous pouvez l’utiliser pour annuler la publication.

1. Select the page or pages in the sites console and click on the **Manage Publication** button.
1. The **Manage Publication** wizard starts. In the first step, **Options**, select to **Unpublish** instead of the default option of **Publish**.

   ![Annulation de la publication](/help/sites-cloud/authoring/assets/publishing-unpublish.png)

   À l’instar de l’option de publication différée, qui lance un workflow permettant de publier cette version de la page à l’heure indiquée, la désactivation différée lance un workflow pour annuler la publication de la ou des pages sélectionnées à une heure spécifique.

   Pour annuler une publication/annulation de publication ultérieure, rendez-vous dans la console Processus pour mettre un terme au processus correspondant. <!--If you want to cancel a publish/unpublish later, go to the [Workflow Console](/help/sites-administering/workflows.md) to terminate the corresponding workflow.-->

1. To complete the un-publication, continue through the wizard as you would to [publish the page](#manage-publication).

## Publication et annulation de la publication d’une arborescence {#publishing-and-unpublishing-a-tree}

Après avoir saisi, ou mis à jour, un nombre élevé de pages de contenu (toutes résidant sous la même page racine), il peut s’avérer plus simple de publier toute l’arborescence en une seule opération.

Pour ce faire, vous pouvez utiliser l’option [Gérer la publication](#manage-publication) de la console Sites.

1. Dans la console Sites, sélectionnez la page racine de l’arborescence que vous souhaitez publier ou dont vous souhaitez annuler la publication, puis sélectionnez **Gérer la publication**.
1. The **Manage Publication** wizard starts. Choisissez de publier ou d’annuler la publication, indiquez à quel moment cette opération doit être effectuée, puis sélectionnez **Suivant** pour continuer.
1. À l’étape **Portée**, sélectionnez la page racine, puis **Inclure les enfants**.

   ![Gestion des pages de sélection des publications](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

1. In the **Include Children** dialogue, un-check the options:

   * Inclure seulement les enfants immédiats
   * Inclure seulement les pages déjà publiées
   Ces options sont sélectionnées par défaut. Vous devez donc penser à les désélectionner. Click **Add** to confirm and add the content to the publication/un-publication.

   ![Inclusion des enfants lors de la dépublication](/help/sites-cloud/authoring/assets/publishing-tree-children.png)

1. L’assistant **Gérer la publication** répertorie le contenu de l’arborescence à des fins de révision. Vous pouvez personnaliser davantage la sélection en ajoutant d’autres pages ou en supprimant celles qui sont sélectionnées.

   ![Options de gestion des publications](/help/sites-cloud/authoring/assets/publishing-tree-select.png)

   Remember that you can also review the references to be published via the **Published References** option.

1. [Continuez l’assistant de gestion de la publication normalement](#manage-publication) pour terminer la publication ou la dépublication de l’arborescence.

## Définition de l’état de publication {#determining-publication-status}

Vous pouvez déterminer l’état de publication d’une page :

* Dans les [informations d’aperçu des ressources de la console Sites](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)

   ![Etat de publication dans la vue Carte](/help/sites-cloud/authoring/assets/publishing-status-console-card.png)

   L’état de publication est indiqué dans les modes d’affichage [Carte](/help/sites-cloud/authoring/getting-started/basic-handling.md#card-view), [Colonnes](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view) et [Liste](/help/sites-cloud/authoring/getting-started/basic-handling.md#list-view) de la console Sites.

* In the [timeline](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline)

   ![Etat de publication dans la vue Chronologie](/help/sites-cloud/authoring/assets/publishing-status-timeline.png)

* In the [Page Information menu](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information) when editing a page

   ![Etat de publication dans le menu Informations sur la page](/help/sites-cloud/authoring/assets/publishing-status-page-information.png)
