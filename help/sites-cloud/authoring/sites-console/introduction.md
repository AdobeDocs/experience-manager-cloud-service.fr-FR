---
title: Console Sites
description: Découvrez comment utiliser la console Sites pour gérer et organiser vos pages AEM.
exl-id: b666e62a-c3dc-4be3-8932-d5fe67b178d6
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1625'
ht-degree: 47%

---

# Console Sites {#sites-console}

Découvrez comment utiliser la console **Sites** pour gérer et organiser vos pages AEM.

## Orientation {#orientation}

La console **Sites** vous permet d’afficher la hiérarchie de vos pages.

![Mode Colonnes de la console Sites avec un élément sélectionné](assets/sites-console-column-view-selected.png)

Il propose différents affichages et barres d’outils pour vous aider à gérer et à organiser vos pages.

* [La barre d’outils de la console](#toolbar) est toujours présente pour vous aider à naviguer.
* [Trois vues différentes](#views) vous permettent de localiser et de sélectionner facilement votre page.
* [La barre d’outils Action](#action-toolbar) s’affiche lorsque vous avez sélectionné un élément pour exécuter une action dessus.
* Le [panneau latéral](#side-panel) comporte plusieurs options pour afficher des informations détaillées sur une page sélectionnée.

## Barre d’outils de la console {#console-toolbar}

La barre d’outils de la console est toujours présente sur la console et vous aide à vous orienter dans votre contenu et à parcourir le contenu.

![Barre d’outils de la console Sites](assets/sites-console-toolbar.png)

### Sélecteur de panneau latéral {#side-panel-selector}

Le sélecteur du panneau latéral vous permet d’afficher des informations supplémentaires sur l’élément sélectionné dans la console.

![Bouton du sélecteur du panneau latéral](assets/sites-console-side-panel-button.png)

Les options présentées dépendent de la console active. Par exemple, dans la console **Sites**, vous ne pouvez sélectionner que le contenu (valeur par défaut), la chronologie, les références ou le panneau latéral de filtrage.

![Exemple de sélecteur de panneau latéral](assets/sites-console-side-panel-selector.png)

Pour plus d’informations sur le panneau latéral, voir [Panneau latéral de la console Sites](/help/sites-cloud/authoring/sites-console/console-side-panel.md).

### Chemins de navigation {#breadcrumbs}

Le chemin de navigation est situé au milieu du rail. Il affiche toujours la description de l’élément sélectionné et vous permet de parcourir les niveaux de votre site web.

![Chemin de navigation dans la barre de navigation](assets/sites-console-breadcrumbs-navigation.png)


Appuyez ou cliquez sur le texte du chemin de navigation pour afficher une liste déroulante répertoriant les niveaux de la hiérarchie de l’élément actuellement sélectionné. Appuyez ou cliquez sur une entrée pour accéder à cet emplacement.

![Exemple de chemin de navigation développé](assets/sites-console-breadcrumbs-example.png)

### Tout sélectionner {#select-all}

Appuyez ou cliquez sur le bouton **Tout sélectionner** pour sélectionner tous les éléments de l’affichage actuel de la console.

![bouton Tout sélectionner](assets/sites-console-select-all.png)

Lorsque vous avez sélectionné tous les éléments, leur nombre s’affiche dans le coin supérieur droit de la barre d’outils où apparaît le bouton **Tout sélectionner**.

Vous pouvez annuler la sélection de tous les éléments et quitter le mode de sélection en procédant comme suit :

* Cliquez ou appuyez sur le **X** en regard du nombre.
* À l’aide de la touche **escape**.

![Tout désélectionner](assets/sites-console-deselect-all.png)

### Bouton Créer {#create-button}

Le bouton **Créer** vous permet d’ajouter de nouvelles pages à votre site et de créer des objets Sites supplémentaires tels que des Live Copies ou des lancements.

![Bouton Créer](assets/sites-console-create.png)

Une fois que vous cliquez dessus, les options affichées sont appropriées à la console/au contexte. Les plus fréquents sont :

* [Page](/help/sites-cloud/authoring/sites-console/creating-pages.md)
* [Site](/help/sites-cloud/administering/site-creation/create-site.md)
* [Live Copy](/help/sites-cloud/administering/msm/overview.md)
* [Launch](/help/sites-cloud/authoring/launches/overview.md)
* [Copie de langue](/help/sites-cloud/administering/translation/overview.md)
* [Rapport CSV](/help/sites-cloud/authoring/sites-console/csv-export.md)

Consultez les liens vers ces fonctionnalités pour plus d’informations sur leur fonctionnement.

## Vues et sélection de pages {#views}

La console **Sites** offre trois vues différentes de votre hiérarchie de contenu. Vous pouvez afficher, parcourir et sélectionner (pour effectuer d’autres actions) vos ressources dans n’importe quel mode disponible.

* [Mode Colonnes](#column-view)
* [Mode Carte](#card-view)
* [Vue Liste](#list-view)

L’icône **Affichage** située à l’extrémité droite de la barre d’outils AEM indique l’affichage sélectionné.

Appuyez ou cliquez dessus pour sélectionner une autre vue.

![Bouton Vues](assets/sites-console-views-button.png)

Vous pouvez basculer entre la vue Colonnes, Carte et Liste. Dans la vue Liste, les paramètres de vue sont également affichés.

![Vues](assets/sites-console-view.png)

>[!NOTE]
>
>L’option **Paramètres** est disponible uniquement dans la vue **Liste**.

L’affichage, la navigation et la sélection sont identiques sur le plan conceptuel dans tous les modes, mais leur manipulation comporte de légères variations en fonction du mode utilisé.

>[!NOTE]
>
>Par défaut, AEM Assets n’affiche pas les rendus originaux des ressources dans l’interface utilisateur sous forme de miniatures, quel que soit le mode. Si vous êtes administrateur ou administratrice, vous pouvez utiliser des superpositions pour configurer AEM Assets afin d’afficher les rendus originaux sous forme de miniatures.

### Sélection de ressources {#selecting-resources}

La sélection d’une ressource en particulier dépend de la combinaison du mode et de l’appareil :

| Mode | Sélectionner Tactile | Sélectionner Bureau | Désélectionner Tactile | Désélectionner Bureau |
|---|---|---|---|---|
| Colonnes | Sélectionner la miniature | Cliquer sur la miniature | Sélectionner la miniature | Cliquer sur la miniature |
| Carte | Sélectionnez et maintenez la carte enfoncée | Placer le pointeur de la souris dessus, puis utiliser l’action rapide sous forme de coche | Sélectionner la carte | Cliquer sur la carte |
| Liste | Sélectionner la miniature | Cliquer sur la miniature | Sélectionner la miniature | Cliquer sur la miniature |

#### Exemple de sélection {#selecting-example}

1. Par exemple, dans la vue Carte :

   ![Sélection du mode Carte](assets/sites-console-card-view-select.png)

1. Une fois que vous avez sélectionné une ressource, l’en-tête de premier niveau est couvert par la [barre d’outils Actions](#actions-toolbar), qui permet d’accéder aux actions actuellement applicables à la ressource sélectionnée.

1. Pour quitter le mode de sélection, sélectionnez le signe **X** affiché en haut à droite de l’écran ou utilisez la touche **Échap**.

### Mode Colonnes {#column-view}

Le mode Colonnes permet de naviguer visuellement dans une arborescence de contenu à travers une série de colonnes en cascade. Cette vue vous permet de visualiser et de parcourir l’arborescence de votre site web.

![Mode Colonnes](assets/sites-console-column-view.png)

Si vous sélectionnez une ressource dans la colonne la plus à gauche, les ressources enfants s’affichent dans une colonne à droite. Si vous sélectionnez une ressource dans la colonne de droite, les ressources enfants s’affichent dans une autre colonne à droite, etc.

* Vous pouvez naviguer de haut en bas dans l’arborescence en appuyant ou en cliquant sur le nom de la ressource ou sur le chevron situé à droite du nom de la ressource.

   * Le nom de la ressource et le chevron sont mis en surbrillance lorsque vous appuyez ou cliquez dessus.
   * Les enfants de la ressource sur laquelle vous avez cliqué/appuyé s’affichent dans la colonne située à droite de celle-ci.
   * Si vous sélectionnez un nom de ressource qui n’a pas d’enfants, ses détails s’affichent dans la dernière colonne.

* Appuyez ou cliquez sur la miniature pour sélectionner la ressource.

   * Lorsqu’elle est sélectionnée, une coche est apposée sur la miniature et le nom de la ressource est également mis en surbrillance.
   * Les détails de la ressource sélectionnée sont affichés dans la dernière colonne.
   * La barre d’outils d’action devient disponible.

* Lorsque vous sélectionnez une page en mode Colonnes, la page sélectionnée s’affiche dans la dernière colonne avec les détails suivants :

   * Titre de la page
   * Nom de la page (partie de l’URL de la page)
   * Modèle sur lequel est basée la page
   * Détails des modifications
   * Langue de la page
   * Publication et prévisualisation des détails

### Mode Carte {#card-view}

En mode Carte, chaque élément au niveau actuel de la hiérarchie s’affiche sous la forme d’une grande carte.

![Mode Carte](assets/sites-console-card-view.png)

* Les cartes fournissent des informations telles que :

   * une représentation visuelle du contenu de la page ;
   * Le titre de la page ;
   * Des dates importantes (telles que la date de la dernière modification ou publication) ;
   * Si la page est verrouillée, masquée ou fait partie d’une Live Copy.
   * Indique si vous devez agir sur l’élément dans le cadre d’un workflow.

Le mode Carte offre également des [actions rapides](#quick-actions) pour les éléments tels que la sélection et des actions courantes telles que la modification.

![Actions rapides](assets/sites-console-quick-actions.png)

Vous pouvez parcourir l’arborescence vers le bas en appuyant/cliquant sur des cartes (en veillant à éviter d’appuyer sur les actions rapides), ou vers le haut en utilisant le [chemin de navigation dans l’en-tête](#the-header).

### Vue Liste {#list-view}

La vue Liste fournit des informations pour chaque ressource au niveau actuel d’une liste.

![Vue Liste](assets/sites-console-list-view.png)

* Vous pouvez parcourir l’arborescence vers le bas en appuyant/cliquant sur le nom de la ressource, ou vers le haut en utilisant le [chemin de navigation dans l’en-tête](#the-header).
* Pour sélectionner facilement tous les éléments de la liste, utilisez la case à cocher [**Tout sélectionner** de la barre d’outils](#select-all).

* Sélectionnez les colonnes à afficher à l’aide de l’option **Afficher les paramètres** située sous le bouton Vues. Vous pouvez afficher les colonnes suivantes :

   * **Nom** : nom de la page, qui peut s’avérer utile dans un environnement de création multilingue, car il fait partie de l’URL de la page et ne change pas, quelle que soit la langue
   * **Modifié** : date de la dernière modification et dernière modification par l’utilisateur ou l’utilisatrice
   * **Publié** : statut de la publication.
   * **Prévisualisation** : prévisualisation du statut
   * **Modèle** : modèle sur lequel la page est basée.
   * **Opération**
   * **Workflow** : workflow actuellement appliqué à la page. Vous pouvez voir davantage d’informations en passant la souris sur un élément ou en ouvrant la chronologie.
   * **Traduit**
   * **Pages vues**
   * **Visiteurs uniques**
   * **Temps passé sur la page**

![Configurer les colonnes](assets/sites-console-select-columns.png)

Par défaut, la colonne **Nom** est affichée ; ce nom fait partie de l’URL de la page. Dans certains cas, il se peut que l’auteur doive accéder à des pages rédigées dans une autre langue. Aussi, le fait de voir le nom de la page (qui reste généralement identique) peut s’avérer très utile si l’auteur ne connaît pas la langue de la page.

* Modifiez l’ordre des éléments à l’aide de la barre verticale en pointillés tout à droite de chaque élément de la liste.

![Ordre des colonnes](assets/sites-console-column-order.png)

Sélectionnez la barre de sélection verticale et faites glisser l’élément vers un nouvel emplacement dans la liste.

![Liste d’ordre](assets/sites-console-order-list.png)

>[!NOTE]
>
>La modification de l’ordre fonctionne uniquement dans un dossier ordonné dont la valeur `jcr:primaryType` est `sling:OrderedFolder`.

## Barre d’outils Actions {#actions-toolbar}

Chaque fois qu’une ressource est sélectionnée, vous pouvez effectuer différentes actions sur l’élément sélectionné. Ces actions s’affichent dans la barre d’outils d’actions.

![ Barre d’outils Actions ](assets/introduction-actions-toolbar.png)

La barre d’outils des actions ne s’affiche que lorsqu’une ressource est sélectionnée dans la console. L’action disponible dans la barre d’outils d’actions change pour refléter les actions que vous pouvez effectuer sur les éléments spécifiques sélectionnés. Les actions les plus courantes sont les suivantes :

* [**Créer**](#create-action) - Créer du contenu ou des actions liées au contenu
* **Modifier** - Selon le mode de création de la page sélectionnée, l’action **Modifier** ouvre l’éditeur approprié.
   * [Éditeur de page](/help/sites-cloud/authoring/page-editor/introduction.md) - Pour les pages créées avec l’éditeur de page AEM
   * [Éditeur universel](/help/sites-cloud/authoring/universal-editor/authoring.md) - Pour les pages créées avec l’éditeur universel
* [**Propriétés**](/help/sites-cloud/authoring/sites-console/page-properties.md) : ouvre la fenêtre des propriétés de la page.
* [**Verrouiller**](/help/sites-cloud/authoring/sites-console/managing-pages.md#locking-a-page) - Verrouiller une page pour empêcher d’autres personnes de la modifier
* [**Copier**](/help/sites-cloud/authoring/sites-console/managing-pages.md#copying-and-pasting-a-page) - Copier une page
* [**Déplacer**](/help/sites-cloud/authoring/sites-console/managing-pages.md#moving-or-renaming-a-page) - Déplacer ou renommer une page
* [**Quick Publish**](/help/sites-cloud/authoring/sites-console/publishing-pages.md#quick-publish) - Publish immédiatement d’une ou de plusieurs pages
* [**Gérer la publication**](/help/sites-cloud/authoring/sites-console/publishing-pages.md#manage-publication) - Planifier la publication d’une ou de plusieurs pages
* [**Restaurer**](/help/sites-cloud/authoring/sites-console/page-versions.md#restore-version) - Restaure une version d’une page ou d’une arborescence de pages
* [**Supprimer**](/help/sites-cloud/authoring/sites-console/managing-pages.md#deleting-a-page) - Supprime une ou plusieurs pages

En raison des restrictions d’espace dans certaines fenêtres, la barre d’outils peut rapidement dépasser l’espace disponible. Lorsque cela se produit, d’autres options s’affichent. Cliquez ou appuyez sur les points de suspension (les trois petits points ou **...**) pour ouvrir un sélecteur déroulant contenant toutes les actions restantes.

![Options supplémentaires](assets/sites-console-additional-options.png)

### Créer une action {#create-action}

L’action Créer offre des options similaires au bouton de la barre d’outils [**Créer** pour créer des pages et des éléments similaires](#create-button).

En outre, il offre la possibilité de créer des actions liées à la page.

* [**Workflow**](/help/sites-cloud/authoring/workflows/overview.md) - Appliquez un workflow à une page
* [**Version**](/help/sites-cloud/authoring/sites-console/page-versions.md) - Création d’une version d’une page

## Modèles

Vous pouvez déterminer facilement le modèle sur lequel la page est basée en sélectionnant cette dernière dans la vue [**Colonnes**](/help/sites-cloud/authoring/basic-handling.md#column-view) ou [**Liste**](/help/sites-cloud/authoring/basic-handling.md#list-view).
