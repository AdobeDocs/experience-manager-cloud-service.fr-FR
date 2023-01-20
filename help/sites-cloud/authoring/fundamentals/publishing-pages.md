---
title: Publication de pages
description: Publication et annulation de la publication de pages à l’aide d’AEM
exl-id: 89f2363c-7922-4ca5-92cb-cbee6a393ee3
source-git-commit: ca849bd76e5ac40bc76cf497619a82b238d898fa
workflow-type: ht
source-wordcount: '1812'
ht-degree: 100%

---

# Publication de pages {#publishing-pages}

Une fois le contenu créé et révisé dans l’environnement de création, l’objectif est de le [rendre disponible sur votre site web public](/help/sites-cloud/authoring/getting-started/concepts.md) (votre environnement de publication).

On parle alors de publication d’une page, ou d’annulation de publication lorsque vous souhaitez retirer une page de l’environnement de publication. En cas de publication et d’annulation de la publication, la page reste disponible pour d’autres modifications dans l’environnement de création jusqu’à ce que vous la supprimiez.

Vous pouvez publier/annuler la publication d’une page immédiatement ou à une date/heure prédéfinies.

>[!NOTE]
>
>La publication d’un fragment d’expérience suit globalement la même procédure que pour une page, mais à partir de la console de Fragments d’expérience ou de l’éditeur.

## Terminologie {#terminology}

Dans le cadre de votre utilisation d’Adobe Experience Manager (AEM) as a Cloud Service, vous pouvez rencontrer différents termes liés à la publication.

* **Publier/Annuler la publication**
   * Termes principalement utilisés pour évoquer les opérations qui rendent votre contenu publiquement accessible dans votre environnement de publication (ou non).
   * Il s’agit des termes utilisés dans la documentation AEM.
* **Activer/Désactiver**
   * Ces termes sont synonymes de publication/annulation de la publication.
   * Ces termes étaient utilisés dans les versions précédentes d’AEM.
* **Répliquer/Réplication**
   * Il s’agit de termes techniques décrivant le mouvement des données (contenu de page, fichiers, code et commentaires utilisateur, par exemple) d’un environnement vers un autre lorsque vous publiez une page.
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


>[!NOTE]
>
> Pour les autres possibilités, reportez-vous à **Heure d’activation** et **Heure de désactivation** dans l’[onglet De base des propriétés de page](/help/sites-cloud/authoring/fundamentals/page-properties.md#basic)

### Publication à partir de l’éditeur {#publishing-from-the-editor}

Si vous modifiez une page, vous pouvez la publier directement à partir de l’éditeur.

1. Sélectionnez l’icône **Informations sur la page** pour ouvrir le menu, puis sélectionnez l’option **Publier la page**.

   ![Publication d’une page via les options de page](/help/sites-cloud/authoring/assets/publishing-page-options.png)

1. Selon que la page comporte des références qui doivent être publiées :

   * La page sera publiée directement, s’il n’y a aucune référence à publier.
   * Si la page comporte des références à publier, celles-ci seront répertoriées dans l’assistant **Publier**, où vous pourrez accomplir ce qui suit :
      * Spécifier les ressources, balises et autres éléments à publier conjointement avec la page, puis cliquer sur **Publier** pour terminer l’opération.
      * Sélectionner **Annuler** pour abandonner l’opération.

   ![Publication de références avec la page](/help/sites-cloud/authoring/assets/publishing-references.png)

1. L’option **Publier** réplique la page dans l’environnement de publication. Une bannière d’informations est affichée dans l’éditeur de page pour confirmer l’opération de publication.

   ![Bannière d’informations sur l’état de publication](/help/sites-cloud/authoring/assets/publishing-info.png)

   Lorsque vous affichez la même page dans la console, l’état de publication mis à jour est visible.

   ![État de publication de la page dans le mode d’affichage Colonnes de la console Sites](/help/sites-cloud/authoring/assets/publishing-status-console-column.png)

>[!NOTE]
>
>Une publication à partir de l’éditeur est dite superficielle ; en d’autres termes, seules la ou les pages sélectionnées sont publiées (les éventuelles pages enfants ne le sont pas).

>[!NOTE]
>
>Les pages accessibles par [alias](/help/sites-cloud/authoring/fundamentals/page-properties.md#advanced) dans l’éditeur ne peuvent pas être publiées. Les options de publication dans l’éditeur ne sont disponibles que pour les pages auxquelles vous pouvez accéder à partir de leur chemin d’accès réel.

### Publication à partir de la console {#publishing-from-the-console}

La console Sites propose deux options de publication :

* [Publication rapide](#quick-publish)
* [Gérer la publication](#manage-publication)

#### Publication rapide {#quick-publish}

L’option **Publication rapide** concerne les cas simples. Elle publie immédiatement la ou les pages sélectionnées sans aucune autre interaction. De ce fait, toute autre référence non publiée l’est aussi automatiquement.

Pour publier une page avec l’option Publication rapide :

1. Sélectionnez la ou les pages dans la console Sites et cliquez ensuite sur le bouton **Publication rapide**.

   ![Sélection de pages en vue de la publication](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. Dans la boîte de dialogue Publication rapide, confirmez la publication en cliquant sur **Publier** ou annulez-la en cliquant sur **Annuler**. Pour rappel, toute référence non publiée sera également publiée automatiquement.

   ![Confirmation de publication rapide](/help/sites-cloud/authoring/assets/publishing-quick-publish.png)

1. Lorsque la page est publiée, une alerte est affichée pour confirmer la publication.

>[!NOTE]
>
>L’option de publication rapide est dite superficielle ; en d’autres termes, seules la ou les pages sélectionnées sont publiées (les éventuelles pages enfants ne le sont pas).

#### Gérer la publication {#manage-publication}

La méthode **Gérer la publication** propose plus d’options que **Publication rapide**, dont la possibilité d’inclure des pages enfants, de personnaliser les références ou encore de lancer n’importe quel workflow applicable. Elle offre également la possibilité de publier la page à une date ultérieure.

Pour modifier ou annuler la publication d’une page à l’aide de l’option Gérer la publication :

1. Sélectionnez la ou les pages dans la console Sites et cliquez ensuite sur le bouton **Gérer la publication**.

   ![Sélection de pages en vue de la publication](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. L’assistant **Gérer la publication** démarre. La première étape, **Options**, vous permet d’effectuer les opérations suivantes :

   * **Action**

      Publier ou annuler la publication des pages sélectionnées.

   * **Planification**

      Effectuer une action maintenant ou ultérieurement.

      La publication différée lance un workflow pour modifier la ou les pages sélectionnées à l’heure indiquée. Si vous optez pour une annulation différée de la publication, un workflow est lancé pour annuler la publication de la ou des pages sélectionnées à une heure déterminée.

      >[!NOTE]
      >
      >Pour annuler une publication/annulation de publication ultérieure, rendez-vous dans la [console Processus](/help/sites-cloud/administering/workflows-administering.md#suspending-resuming-and-terminating-a-workflow-instance) pour mettre un terme au processus correspondant.
   ![Options de gestion de la publication](/help/sites-cloud/authoring/assets/publishing-manage-publication-options.png)

1. Cliquez sur **Suivant** pour continuer.

1. Au cours de l’étape suivante de l’assistant Gérer la publication, **Portée**, vous pouvez définir la portée de la publication ou de l’annulation de la publication ; par exemple, inclure des pages enfants et/ou des références.

   ![Gérer la portée de la publication](/help/sites-cloud/authoring/assets/publishing-manage-publication-scope.png)

   **Ajouter du contenu**

   Vous pouvez sélectionner le bouton **Ajouter du contenu** pour ajouter des pages à la liste des pages à publier, au cas où vous auriez omis d’en sélectionner une avant de lancer l’assistant Gérer la publication.

   Le fait de sélectionner le bouton **Ajouter du contenu** lance l’[explorateur de chemins d’accès](/help/sites-cloud/authoring/fundamentals/environment-tools.md#path-browser), qui permet de sélectionner du contenu.

   Sélectionnez les pages souhaitées, puis cliquez sur **Sélectionner** pour ajouter le contenu à l’assistant ou sur **Annuler** pour annuler la sélection et revenir à l’assistant.

   **Supprimer la sélection**

   De retour dans l’assistant, vous pouvez sélectionner un élément de la liste pour le supprimer de la sélection.

   ![Sélection de pages dans la boîte de dialogue Gérer la publication](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

   **Références publiées**

   Vous pouvez afficher et modifier les références à publier ou dont la publication doit être annulée pour une page. Pour ce faire, sélectionnez la page, puis cliquez sur le bouton **Références publiées**.

   ![Options de gestion de la publication](/help/sites-cloud/authoring/assets/publishing-manage-publication-references.png)

   La boîte de dialogue **Références publiées** affiche alors les références du contenu sélectionné. Par défaut, elles sont toutes sélectionnées. Dès lors, elles seront toutes publiées ou leur publication sera annulée. Vous pouvez toutefois les désélectionner pour qu’elles ne soient pas incluses dans l’opération.

   Cliquez sur **Terminé** pour enregistrer vos modifications ou sur **Annuler** pour annuler la sélection et revenir à l’assistant.

   De retour dans l’assistant, la colonne **Références** est mise à jour afin de tenir compte des références que vous avez choisi de publier ou dont la publication doit être annulée.

   ![Sélection de pages dans la boîte de dialogue Gérer la publication](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

   **Inclure les enfants**

   >[!NOTE]
   >
   >Voir [Publication et annulation de la publication d’une arborescence](#publishing-and-unpublishing-a-tree)

   Le fait de cliquer sur **Inclure les enfants** ouvre une boîte de dialogue qui permet d’effectuer les opérations suivantes :

   * **Inclure les enfants**
   * **Inclure seulement les enfants immédiats**
   * **Inclure seulement les pages modifiées**
   * **Inclure seulement les pages déjà publiées**

   Activez les options requises et confirmez avec **OK** l’ajout des pages enfants à la liste des pages à publier ou dont la publication doit être annulée en fonction des options de sélection. Cliquez sur **Annuler** pour annuler la sélection et revenir à l’assistant.

   ![Gérer la publication : option Inclure les enfants](/help/sites-cloud/authoring/assets/publishing-include-children.png)

1. Pour terminer, cliquez sur **Publier**.

   De retour dans la console Sites, un message de notification s’affiche pour confirmer la publication.

1. Si les pages publiées sont associées à des workflows, elles peuvent être affichées dans une dernière étape de l’assistant de publication intitulée **Workflows**.

   ![Sélection de pages dans la boîte de dialogue Gérer la publication](/help/sites-cloud/authoring/assets/publishing-manage-publication-workflow.png)

   >[!NOTE]
   >
   >L’étape **Workflows** est affichée en fonction des droits dont dispose ou non votre utilisateur. Pour plus d’informations, reportez-vous à la remarque précédente sur cette page concernant les privilèges de publication, ainsi qu’aux sections Gestion de l’accès aux workflows et [Application de workflows aux pages](/help/sites-cloud/authoring/workflows/applying.md).

   Les ressources sont regroupées en fonction des workflows déclenchés et de chaque option proposée pour :

   * définir le titre du workflow ;
   * conserver le module de workflow, à condition que le workflow dispose d’une prise en charge multi-ressource ;
   * définir le titre du module de workflow, si l’option de conservation du module de workflow a été sélectionnée.

1. Cliquez sur **Publier** ou **Publier ultérieurement** pour terminer la publication.

## Annulation de la publication des pages {#unpublishing-pages}

L’annulation de la publication d’une page supprime cette page de votre environnement de publication ou de [prévisualisation](/help/sites-cloud/authoring/fundamentals/previewing-content.md), de sorte que vos lecteurs et lectrices ne puissent plus y accéder.

Vous pouvez annuler la publication d’une ou de plusieurs pages de la destination souhaitée en procédant de la [même manière que pour leur publication](#publishing-pages) :

* [À partir de l’éditeur de page](#unpublishing-from-the-editor)
* [À partir de la console Sites](#unpublishing-from-the-console)

### Annulation de la publication à partir de l’éditeur {#unpublishing-from-the-editor}

Lors de la modification d’une page, si vous souhaitez annuler sa publication, sélectionnez **Annuler la publication de la page** dans le menu **Informations sur la page**, comme vous le feriez pour [publier la page](#publishing-from-the-editor).

>[!NOTE]
>
>Les pages accessibles par [alias](/help/sites-cloud/authoring/fundamentals/page-properties.md#advanced) dans l’éditeur ne peuvent pas être publiées. Les options de publication dans l’éditeur ne sont disponibles que pour les pages auxquelles vous pouvez accéder à partir de leur chemin d’accès réel.

### Annulation de la publication à partir de la console {#unpublishing-from-the-console}

De la même façon que vous [utilisez l’option Gérer la publication pour publier une page](#manage-publication), vous pouvez l’utiliser pour annuler la publication.

1. Sélectionnez la ou les pages dans la console Sites et cliquez ensuite sur le bouton **Gérer la publication**.
1. L’assistant **Gérer la publication** démarre. Dans la première étape, **Options**, sélectionnez **Annuler la publication** au lieu de l’option par défaut, à savoir **Publier**.

   ![Annulation de la publication - Options](/help/sites-cloud/authoring/assets/publishing-unpublish.png)

   À l’instar de l’option de publication différée, qui lance un workflow permettant de publier cette version de la page à l’heure indiquée, la désactivation différée lance un workflow pour annuler la publication de la ou des pages sélectionnées à une heure spécifique.

   >[!NOTE]
   >
   >Pour annuler une publication/annulation de publication ultérieure, rendez-vous dans la [console Processus](/help/sites-cloud/administering/workflows-administering.md#suspending-resuming-and-terminating-a-workflow-instance) pour mettre un terme au processus correspondant.

   >[!NOTE]
   >Si vous disposez d’un environnement de [prévisualisation](/help/sites-cloud/authoring/fundamentals/previewing-content.md), vous pouvez sélectionner la **destination** pendant la gestion de la publication.

1. Pour finaliser l’annulation de la publication, complétez les différentes étapes de l’assistant, comme vous le feriez pour [publier la page](#manage-publication).

   ![Annulation de la publication - Portée](/help/sites-cloud/authoring/assets/publishing-unpublish-scope.png)

## Publication et annulation de la publication d’une arborescence {#publishing-and-unpublishing-a-tree}

Après avoir saisi, ou mis à jour, un nombre élevé de pages de contenu (toutes résidant sous la même page racine), il peut s’avérer plus simple de publier toute l’arborescence en une seule opération.

Pour ce faire, vous pouvez utiliser l’option [Gérer la publication](#manage-publication) de la console Sites.

1. Dans la console Sites, sélectionnez la page racine de l’arborescence que vous souhaitez publier ou dont vous souhaitez annuler la publication, puis sélectionnez **Gérer la publication**.
1. L’assistant **Gérer la publication** démarre. Choisissez de publier ou d’annuler la publication, indiquez à quel moment cette opération doit être effectuée, puis sélectionnez **Suivant** pour continuer.
1. À l’étape **Portée**, sélectionnez la page racine, puis **Inclure les enfants**.

   ![Sélection de pages dans la boîte de dialogue Gérer la publication](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

1. Dans la boîte de dialogue **Inclure les enfants** :

   * sélectionnez **Inclure les enfants**
   * désélectionnez **Inclure seulement les enfants immédiats**
   * désélectionnez **Inclure seulement les pages déjà publiées**
   * configurez **Inclure uniquement les pages modifiées** selon les besoins

   Ces options sont sélectionnées par défaut. Vous devez donc penser à les configurer. Confirmez la sélection avec **OK** pour ajouter le contenu à la publication/annulation de la publication.

   ![Inclusion d’enfants pour la publication d’arborescence](/help/sites-cloud/authoring/assets/publishing-include-children-tree.png)

1. Dans l’assistant **Gérer la publication**, vous pouvez personnaliser davantage la sélection en ajoutant des pages supplémentaires ou en supprimant celles sélectionnées.

   N’oubliez pas que vous pouvez également passer en revue les références à publier au moyen de l’option **Références publiées**.

1. [Poursuivez normalement les étapes de l’assistant Gérer la publication](#manage-publication) pour terminer la publication ou l’annulation de la publication de l’arborescence.

## Définition de l’état de publication {#determining-publication-status}

Vous pouvez déterminer l’état de publication d’une page :

* Dans les [informations d’aperçu des ressources de la console Sites](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)

   ![État de la publication en mode Carte](/help/sites-cloud/authoring/assets/publishing-status-console-card.png)

   L’état de publication est indiqué dans les modes d’affichage [Carte](/help/sites-cloud/authoring/getting-started/basic-handling.md#card-view), [Colonnes](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view) et [Liste](/help/sites-cloud/authoring/getting-started/basic-handling.md#list-view) de la console Sites.

* Dans la [chronologie](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline)

   ![État de publication en mode Chronologie](/help/sites-cloud/authoring/assets/publishing-status-timeline.png)

* Dans le menu [Informations sur la page](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information) lors de la modification d’une page

   ![État de publication dans le menu Informations sur la page](/help/sites-cloud/authoring/assets/publishing-status-page-information.png)
