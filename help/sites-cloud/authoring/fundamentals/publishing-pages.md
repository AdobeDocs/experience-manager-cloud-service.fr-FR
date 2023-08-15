---
title: Publication de pages
description: Découvrez comment publier et annuler la publication de vos pages à l’aide de divers mécanismes dans AEM.
exl-id: 89f2363c-7922-4ca5-92cb-cbee6a393ee3
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '1804'
ht-degree: 83%

---

# Publication de pages {#publishing-pages}

Une fois que vous avez créé et révisé votre contenu dans l’environnement de création, l’objectif est de [le rendre disponible sur votre site web public ;](/help/sites-cloud/authoring/getting-started/concepts.md) (votre environnement de publication).

On parle alors de publication d’une page. Lorsque vous souhaitez supprimer une page de l’environnement de publication, on parle de dépublication. Lorsque vous publiez et dépubliez, la page reste disponible dans l’environnement de création pour d’autres modifications jusqu’à ce que vous la supprimiez.

Vous pouvez publier/dépublier une page immédiatement ou à une date/heure prédéfinies.

>[!NOTE]
>
>La publication d’un fragment d’expérience suit globalement la même procédure que pour une page, mais à partir de la console de Fragments d’expérience ou de l’éditeur.

## Terminologie {#terminology}

Dans le cadre de votre utilisation d’Adobe Experience Manager (AEM) as a Cloud Service, vous pouvez rencontrer différents termes liés à la publication.

* **Publier/dépublier**
   * Termes principalement utilisés pour évoquer les opérations qui rendent votre contenu publiquement accessible dans votre environnement de publication (ou non).
   * Il s’agit des termes utilisés dans la documentation AEM.
* **Activer/Désactiver**
   * Ces termes sont synonymes de publication/dépublication.
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
>Si vous ne disposez pas des privilèges requis pour publier une page spécifique :
>
>* Un workflow est déclenché pour informer la personne appropriée de votre demande de publication.
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

   * La page est publiée directement s’il n’y a aucune référence à publier.
   * Si la page comporte des références à publier, celles-ci sont répertoriées dans la variable **Publier** , où vous pouvez effectuer l’une des opérations suivantes :
      * Spécifier les ressources, balises et autres éléments à publier conjointement avec la page, puis cliquer sur **Publier** pour terminer l’opération.
      * Sélectionner **Annuler** pour abandonner l’opération.

   ![Publication de références avec la page](/help/sites-cloud/authoring/assets/publishing-references.png)

1. L’option **Publier** réplique la page dans l’environnement de publication. Dans l’éditeur de page, une bannière d’informations s’affiche pour confirmer l’action de publication.

   ![Bannière d’informations sur l’état de publication](/help/sites-cloud/authoring/assets/publishing-info.png)

   Lorsque vous affichez la même page dans la console, l’état de publication mis à jour est visible.

   ![État de publication de la page dans le mode d’affichage Colonnes de la console Sites](/help/sites-cloud/authoring/assets/publishing-status-console-column.png)

>[!NOTE]
>
>La publication à partir de l’éditeur est une publication superficielle, c’est-à-dire que seule la ou les pages sélectionnées sont publiées et que les pages enfants ne le sont pas.

>[!NOTE]
>
>Pages accessibles par [alias](/help/sites-cloud/authoring/fundamentals/page-properties.md#advanced) dans l’éditeur ne peut pas être publié. Les options de publication dans l’éditeur ne sont disponibles que pour les pages auxquelles vous pouvez accéder à partir de leur chemin d’accès réel.

### Publication à partir de la console {#publishing-from-the-console}

La console Sites propose deux options de publication :

* [Publication rapide](#quick-publish)
* [Gérer la publication](#manage-publication)

#### Publication rapide {#quick-publish}

L’option **Publication rapide** concerne les cas simples. Elle publie immédiatement la ou les pages sélectionnées sans aucune autre interaction. Pour cette raison, toutes les références non publiées seront également publiées automatiquement.

Pour publier une page avec publication rapide :

1. Sélectionnez la ou les pages dans la console Sites et cliquez ensuite sur le bouton **Publication rapide**.

   ![Sélection de pages en vue de la publication](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. Dans la boîte de dialogue Publication rapide, confirmez la publication en cliquant sur **Publier** ou annulez-la en cliquant sur **Annuler**. Pour rappel, toute référence dépubliée sera également publiée automatiquement.

   ![Confirmation de publication rapide](/help/sites-cloud/authoring/assets/publishing-quick-publish.png)

1. Une fois la page publiée, une alerte s’affiche pour confirmer la publication.

>[!NOTE]
>
>La publication rapide est une publication superficielle, c’est-à-dire que seule la ou les pages sélectionnées sont publiées et que les pages enfants ne le sont pas.

#### Gérer la publication {#manage-publication}

**Gérer la publication** offre plus d’options que **Publication rapide**, permettant l’inclusion de pages enfants, la personnalisation des références et le démarrage de tous les workflows applicables, et offrant la possibilité de publier à une date ultérieure.

Pour publier ou dépublier une page à l’aide de l’option Gérer la publication :

1. Sélectionnez la ou les pages dans la console Sites et cliquez ensuite sur le bouton **Gérer la publication**.

   ![Sélection de pages en vue de la publication](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. L’assistant **Gérer la publication** démarre. la première étape, **Options**, vous permet :

   * **Action**

     Publier ou dépublier des pages sélectionnées.

   * **Planification**

     Vous pouvez choisir d’effectuer cette action maintenant ou ultérieurement.

     La publication différée lance un workflow pour publier la ou les pages sélectionnées à un moment précis. A l’inverse, la dépublication différée lance un workflow pour dépublier la ou les pages sélectionnées à un moment précis.

     >[!NOTE]
     >
     >Pour annuler une publication/dépublier ultérieurement, rendez-vous dans la [console Workflow](/help/sites-cloud/administering/workflows-administering.md#suspending-resuming-and-terminating-a-workflow-instance) pour mettre un terme au workflow correspondant.

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

   Vous pouvez afficher et modifier les références à publier ou dépublier pour une page. Pour ce faire, sélectionnez la page, puis cliquez sur le bouton **Références publiées**.

   ![Options de gestion de la publication](/help/sites-cloud/authoring/assets/publishing-manage-publication-references.png)

   La boîte de dialogue **Références publiées** affiche alors les références du contenu sélectionné. Par défaut, ils sont tous sélectionnés et publiés/non publiés, mais vous pouvez décocher la case pour les désélectionner afin qu’ils ne soient pas inclus dans l’action.

   Cliquez sur **Terminé** pour enregistrer vos modifications ou sur **Annuler** pour annuler la sélection et revenir à l’assistant.

   De retour dans l’assistant, le **Références** est mise à jour afin de prendre en compte votre sélection de références à publier ou dont la publication doit être annulée.

   ![Sélection de pages dans la boîte de dialogue Gérer la publication](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

   **Inclure les enfants**

   >[!NOTE]
   >
   >Voir [Publication et dépublication d’une arborescence](#publishing-and-unpublishing-a-tree)

   Le fait de cliquer sur **Inclure les enfants** ouvre une boîte de dialogue qui permet d’effectuer les opérations suivantes :

   * **Inclure les enfants**
   * **Inclure seulement les enfants immédiats**
   * **Inclure seulement les pages modifiées**
   * **Inclure seulement les pages déjà publiées**

   Activez les options requises et confirmez avec **OK** l’ajout des pages enfants à la liste des pages à publier ou dépublier en fonction des options de sélection. Cliquez sur **Annuler** pour annuler la sélection et revenir à l’assistant.

   ![Gérer la publication : option Inclure les enfants](/help/sites-cloud/authoring/assets/publishing-include-children.png)

1. Pour terminer, cliquez sur **Publier**.

   De retour dans la console Sites, un message de notification s’affiche pour confirmer la publication.

1. Si les pages publiées sont associées à des workflows, elles peuvent être affichées dans une dernière étape de l’assistant de publication intitulée **Workflows**.

   ![Sélection de pages dans la boîte de dialogue Gérer la publication](/help/sites-cloud/authoring/assets/publishing-manage-publication-workflow.png)

   >[!NOTE]
   >
   >La variable **Workflows** s’affiche en fonction des droits dont dispose ou non votre utilisateur. Consultez la remarque précédente sur cette page concernant les privilèges de publication et la gestion de l’accès aux workflows et [Application de workflows aux pages](/help/sites-cloud/authoring/workflows/applying.md) pour plus d’informations.

   Les ressources sont regroupées selon les workflows déclenchés et chaque option donnée pour :

   * Définissez le titre du workflow.
   * conserver le package de workflow, à condition que le workflow dispose d’une prise en charge multi-ressource ;
   * définir le titre du package de workflow, si l’option de conservation du package de workflow a été sélectionnée.

1. Cliquez sur **Publier** ou **Publier ultérieurement** pour terminer la publication.

## Dépublication de pages {#unpublishing-pages}

La dépublication d’une page supprime cette page de votre environnement de publication ou de [prévisualisation](/help/sites-cloud/authoring/fundamentals/previewing-content.md), de sorte que vos lecteurs et lectrices ne puissent plus y accéder.

Vous pouvez dépublier une ou plusieurs pages de la destination souhaitée en procédant de la [même manière que pour leur publication](#publishing-pages) :

* [À partir de l’éditeur de page](#unpublishing-from-the-editor)
* [À partir de la console Sites](#unpublishing-from-the-console)

### Dépublication à partir de l’éditeur {#unpublishing-from-the-editor}

Lors de la modification d’une page, si vous la dépubliez, sélectionnez **Dépublier la page** dans le menu **Informations sur la page**, comme vous le feriez pour [publier la page](#publishing-from-the-editor).

>[!NOTE]
>
>Pages accessibles par [alias](/help/sites-cloud/authoring/fundamentals/page-properties.md#advanced) dans l’éditeur ne peut pas être dépublié. Les options de publication dans l’éditeur ne sont disponibles que pour les pages auxquelles vous pouvez accéder à partir de leur chemin d’accès réel.

### Dépublication à partir de la console {#unpublishing-from-the-console}

De la même façon que vous [utilisez l’option Gérer la publication pour publier une page](#manage-publication), vous pouvez l’utiliser pour la dépublication.

1. Sélectionnez la ou les pages dans la console Sites et cliquez ensuite sur le bouton **Gérer la publication**.
1. L’assistant **Gérer la publication** démarre. Dans la première étape, **Options**, sélectionnez **Dépublier** au lieu de l’option par défaut, à savoir **Publier**.

   ![Dépublication - Options](/help/sites-cloud/authoring/assets/publishing-unpublish.png)

   À l’instar de l’option de publication différée, qui lance un workflow permettant de publier cette version de la page à l’heure indiquée, la désactivation différée lance un workflow pour dépublier la ou les pages sélectionnées à une heure spécifique.

   >[!NOTE]
   >
   >Pour annuler une publication/dépublier ultérieurement, rendez-vous dans la [console Workflow](/help/sites-cloud/administering/workflows-administering.md#suspending-resuming-and-terminating-a-workflow-instance) pour mettre un terme au workflow correspondant.

   >[!NOTE]
   >Si vous disposez d’un environnement de [prévisualisation](/help/sites-cloud/authoring/fundamentals/previewing-content.md), vous pouvez sélectionner la **destination** pendant la gestion de la publication.

1. Pour finaliser l’annulation de la publication, complétez les différentes étapes de l’assistant, comme vous le feriez pour [publier la page](#manage-publication).

   ![Dépublication - Portée](/help/sites-cloud/authoring/assets/publishing-unpublish-scope.png)

## Publication et dépublication d’une arborescence {#publishing-and-unpublishing-a-tree}

Lorsque vous avez saisi ou mis à jour un nombre considérable de pages de contenu (toutes résidant sous la même page racine), il peut s’avérer plus facile de publier l’arborescence entière en une seule action.

Vous pouvez utiliser l’option [Gérer la publication](#manage-publication) sur la console des sites.

1. Dans la console Sites, sélectionnez la page racine de l’arborescence que vous souhaitez publier ou dépublier, puis sélectionnez **Gérer la publication**.
1. L’assistant **Gérer la publication** démarre. Choisissez la publication ou la dépublication, puis sélectionnez **Suivant** pour continuer.
1. À l’étape **Portée**, sélectionnez la page racine et sélectionnez **Inclure les enfants**.

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
