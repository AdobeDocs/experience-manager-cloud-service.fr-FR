---
title: Panneau latéral de l’éditeur de page
description: Découvrez comment utiliser le panneau latéral dans l’éditeur d’AEM Sites pour ajouter des composants et des ressources à votre page.
exl-id: 5f025828-f2ca-4cbb-9cdf-a199e9e90cc7
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1122'
ht-degree: 41%

---

# Panneau latéral de l’éditeur de page {#side-panel}

Découvrez comment utiliser le panneau latéral dans l’éditeur d’AEM Sites pour ajouter des composants et des ressources à votre page.

## Modes du panneau latéral {#modes}

Le panneau latéral est toujours accessible dans l’éditeur de page en appuyant ou en cliquant sur l’icône **Activer/désactiver le panneau latéral** dans la barre d’outils de l’éditeur de page.

![Bascule du panneau latéral](assets/editor-side-panel-side-panel-toggle.png)

Lorsque vous ouvrez le panneau latéral, il s’ouvre en glissant depuis le côté gauche et vous pouvez ensuite choisir parmi trois onglets importants :

* [Explorateur de composants](#components-browser) pour ajouter du nouveau contenu à votre page
* [L’explorateur de ressources](#assets-browser) pour ajouter de nouvelles ressources à votre page
* [Arborescence de contenu](#content-tree) pour parcourir la structure de votre page.

## Explorateur de composants {#components-browser}

Les [composants](/help/implementing/developing/components/overview.md) sont les blocs de création utilisés pour créer du contenu avec l’éditeur de page d’AEM. Vous placez plusieurs composants sur une page et configurez leurs options pour créer votre page de contenu.

L’explorateur de composants présente tous les composants que vous pouvez utiliser sur la page active. Vous pouvez les faire glisser à l’emplacement approprié, puis les modifier pour ajouter votre contenu.

Appuyez ou cliquez sur l’onglet **Composants** dans le panneau latéral pour accéder au navigateur **Composants**.

![Icône du navigateur de composants dans le panneau latéral](assets/editor-side-panel-components-browser.png)

L’aspect et la gestion de l’interface utilisateur dépendent du type d’appareil utilisé.

### Appareil Mobile {#mobile-device-components-browser}

Lors de l’ouverture de l’explorateur de composants sur un appareil mobile, la page en cours de modification est entièrement recouverte.

Pour ajouter un composant à votre page, sélectionnez-le, faites-le glisser et déplacez-le vers la droite. L’explorateur de composants se ferme pour afficher à nouveau la page, où vous pouvez positionner le composant.

![Explorateur de composants sur mobile](assets/editor-side-panel-mobile-device.png)

>[!NOTE]
>
>Un appareil mobile est détecté lorsque la largeur est inférieure à 1 024 px.

### Poste de travail {#desktop-device-components-browser}

Lors de l’ouverture de l’explorateur de composants sur un ordinateur de bureau, il s’affiche sur le côté gauche de la fenêtre.

Pour ajouter un composant à votre page, cliquez sur le composant requis et faites-le glisser vers l’emplacement requis.

![Explorateur de composants sur bureau](/help/sites-cloud/authoring/assets/component-browser-desktop.png)

### Utilisation de l’explorateur de composants {#using-component-browser}

Dans le navigateur **Composants** les composants sont représentés par les éléments suivants :

* Nom du composant
* Groupe de composants (en gris)
* Icône ou abréviation
   * Les icônes des composants standard sont monochromes.
   * Les abréviations correspondent toujours aux deux premiers caractères du nom du composant.

Dans la barre d’outils supérieure de l’explorateur de **composants**, vous pouvez effectuer les opérations suivantes :

* Filtrer les composants par nom
* Restreindre l’affichage à un groupe spécifique à l’aide de la liste déroulante.

Pour obtenir une description plus détaillée du composant, vous pouvez sélectionner l’icône d’information en regard du composant dans le navigateur **Composants** (le cas échéant). Par exemple, pour le **fragment de contenu** :

![Informations de l’explorateur de composants](assets/editor-side-panel-component-description.png)

Pour plus d’informations sur les composants disponibles, voir [Console Composants](/help/sites-cloud/authoring/components-console.md)

## Explorateur de ressources {#assets-browser}

Le navigateur **Assets** affiche toutes les ressources [assets](/help/assets/overview.md) qui peuvent être utilisées sur la page active.

Appuyez ou cliquez sur l’onglet **Assets** dans le panneau latéral pour parcourir les ressources.

![Bouton de l’explorateur de ressources](assets/editor-side-panel-assets-browser-tab.png)

Le défilement infini permet de développer la liste des ressources selon les besoins.

![Explorateur de ressources](assets/editor-side-panel-assets-browser.png)

L’aspect et la gestion de l’explorateur dépendent du type d’appareil utilisé :

### Appareil Mobile {#mobile-device-assets-browser}

Lors de l’ouverture de l’explorateur de ressources sur un appareil mobile, la page en cours de modification est entièrement recouverte.

Pour ajouter une ressource à votre page, sélectionnez-la et faites-la glisser, puis déplacez-la vers la droite. L’explorateur de ressources se ferme pour afficher à nouveau la page, où vous pouvez ajouter la ressource au composant requis.

![Explorateur de ressources sur mobile](assets/editor-side-panel-assets-browser-mobile.png)

>[!NOTE]
>
>Un appareil mobile est détecté lorsque la largeur est inférieure à 1 024 px.

### Poste de travail {#desktop-device-assets-browser}

Lors de l’ouverture de l’explorateur de ressources sur un ordinateur de bureau, il s’ouvre sur le côté gauche de la fenêtre.

Pour ajouter une ressource à votre page, sélectionnez la ressource requise et faites-la glisser vers le composant ou l’emplacement requis.

![Explorateur de ressources sur bureau](assets/editor-side-panel-assets-browser-desktop.png)

### Utiliser le navigateur Assets {#using-assets-browser}

Pour ajouter une ressource à votre page, sélectionnez-la et faites-la glisser jusqu’à l’emplacement souhaité. Il peut s’agir des éléments suivants :

* d’un composant existant du type approprié.
   * Par exemple, vous pouvez faire glisser une ressource de type image sur un composant Image ;
* d’un [espace réservé](/help/sites-cloud/authoring/page-editor/edit-content.md#component-placeholder) dans le système de paragraphes où créer un composant du type approprié :
   * Par exemple, vous pouvez faire glisser une ressource de type image sur le système de paragraphes afin de créer un composant Image.

>[!NOTE]
>
>Le glisser-déposer de ressources est disponible pour des ressources et des types de composants spécifiques. Reportez-vous à [Insertion d’un composant à l’aide de l’explorateur de ressources](/help/sites-cloud/authoring/page-editor/edit-content.md#adding-a-component-from) pour plus d’informations.

Dans la barre d’outils supérieure de l’explorateur de ressources, vous pouvez filtrer les ressources en procédant comme suit :

* Nom
* Chemin
* Type de ressource tel que les images, les vidéos, les documents, les paragraphes, les fragments de contenu et les fragments d’expérience
* Caractéristiques des ressources, telles que l’orientation et le style
   * Disponible uniquement pour certains types de ressources

Si vous devez modifier rapidement une ressource, vous pouvez lancer [l’éditeur de ressources](/help/assets/manage-digital-assets.md) directement depuis l’explorateur de ressources en cliquant sur l’icône Modifier affichée en regard du nom de la ressource.

![Bouton Modifier la ressource](assets/editor-side-panel-asset-edit-button.png)

## Arborescence de contenu {#content-tree}

L’**Arborescence de contenu** donne une vue d’ensemble de tous les composants de la page dans une hiérarchie, afin que vous puissiez voir en un coup d’œil comment la page est composée.

>[!NOTE]
>
>L’arborescence de contenu n’est pas disponible si vous modifiez une page sur un appareil mobile (si la largeur de l’explorateur est inférieure à 1 024 px).

Appuyez ou cliquez sur l’onglet **Arborescence de contenu** pour accéder à l’arborescence de contenu.

![Bouton Arborescence de contenu](assets/editor-side-panel-content-tree-tab.png)

Une fois ouvert, vous pouvez voir une représentation en arborescence de votre page ou modèle. Il est ainsi plus simple de comprendre comment son contenu est structuré de manière hiérarchique. En outre, sur une page complexe, il est plus facile de passer d’un composant à l’autre de la page.

![Arborescence de contenu](assets/editor-side-panel-content-tree.png)

Une page pouvant facilement être composée de nombreux composants du même type, l’arborescence de contenu affiche un texte descriptif (en gris) après le nom du type de composant (en noir). Le texte descriptif provient des propriétés courantes du composant, telles que le titre ou le texte.

Les types de composants sont affichés dans la langue de l’utilisateur ou de l’utilisatrice, tandis que le texte descriptif du composant dépend de la langue de la page.

Cliquez sur le chevron en regard d’un composant pour réduire ou développer ce niveau.

![Extension du chevron de l’arborescence de contenu](assets/editor-side-panel-content-tree-chevron.png)

Cliquez sur le composant pour le mettre en surbrillance dans l’éditeur de page. Les actions disponibles dépendent du statut de la page. Par exemple :

## Une page de base {#basic-page}

Les composants d’une page de base auront les options habituelles.

![Arborescence de contenu mise en surbrillance](assets/editor-side-panel-content-tree-highlighted.png)

Si le composant sur lequel vous cliquez est éditable, une icône de clé à molette s’affiche à droite du nom. Cliquez sur cette icône pour lancer la boîte de dialogue de modification du composant.

![Bouton Modifier l’arborescence de contenu](assets/editor-side-panel-content-tree-edit.png)

### Une Live Copy {#live-copy}

Une page qui fait partie d’une [Live Copy](/help/sites-cloud/administering/msm/overview.md), où les composants sont hérités d’une autre page, possède différentes options.

## Explorateur de contenu associé {#associated-content-browser}

Si votre page contient des fragments de contenu, vous avez également accès au [navigateur de contenu associé](/help/sites-cloud/authoring/fragments/content-fragments.md#using-associated-content).
