---
title: Structure de l’interface utilisateur d’AEM
description: 'L’interface utilisateur d’AEM s’accompagne de plusieurs principes sous-jacents et se compose d’une série d’éléments clés :'
exl-id: ac211716-d699-4fdb-a286-a0a1122c86c5
source-git-commit: d361ddc9a50a543cd1d5f260c09920c5a9d6d675
workflow-type: tm+mt
source-wordcount: '893'
ht-degree: 50%

---

# Structure de l’interface utilisateur d’AEM {#structure-of-the-aem-ui}

L’interface utilisateur d’AEM s’accompagne de plusieurs principes sous-jacents et se compose d’une série d’éléments clés :

## Consoles {#consoles}

### Redimensionnement et mise en page de base {#basic-layout-and-resizing}

L’interface utilisateur convient à la fois aux appareils mobiles et aux ordinateurs de bureau. Cependant, au lieu de créer deux styles distincts, AEM utilise un seul style qui fonctionne pour tous les écrans et terminaux.

Tous les modules utilisent la même disposition de base :

![Console AEM Sites](assets/ui-sites-console.png)

La mise en page adhère à un style de conception réactif et s’adapte à la taille de l’appareil, de la fenêtre ou des deux, que vous utilisez.

Par exemple, lorsque la résolution est inférieure à 1 024 pixels (comme sur un appareil mobile), l’affichage est ajusté en conséquence :

![Vue mobile de la console Sites](assets/ui-sites-mobile.png)

### Barre d’en-tête {#header-bar}

![Barre d’en-tête AEM](assets/ui-header-bar.png)

La barre d’en-tête affiche des éléments globaux, parmi lesquels :

* Le logo et le produit/la solution spécifique que vous utilisez actuellement. Pour AEM, cet élément forme également un lien vers la navigation globale
* Rechercher
* Icône d’accès aux ressources d’aide
* Icône d’accès à d’autres solutions
* Indicateur d’alertes ou d’éléments de boîte de réception qui vous attendent et leur accès.
* L’icône de l’utilisateur, ainsi qu’un lien vers la gestion de votre profil

### Barre d’outils {#toolbar}

Le contenu de cette barre varie en fonction de l’emplacement. La barre d’outils affiche des outils permettant de contrôler la vue ou des ressources dans la page ci-dessous. La barre d’outils est spécifique au produit, mais les éléments ont un aspect commun.

Dans n’importe quel emplacement, la barre d’outils affiche les actions actuellement disponibles :

![Barre d’outils AEM Sites](assets/ui-sites-toolbar.png)

Dépend également de la sélection ou non d’une ressource :

![Barre d’outils AEM Sites sélectionnée](assets/ui-sites-toolbar-selected.png)

### Rail de gauche {#left-rail}

Le rail de gauche peut être ouvert/masqué suivant les besoins afin d’afficher les éléments suivants :

* **Contenu uniquement**
* **Arborescence de contenu**
* **Chronologie**
* **Références**
* **Filtrer**

La valeur par défaut est **Contenu uniquement** (rail masqué).

![Rail de gauche](assets/ui-left-rail.png)

## Création de pages {#page-authoring}

Lors de la création de pages, les zones structurelles sont les suivantes.

### Cadre de contenu {#content-frame}

Le contenu de la page est rendu dans le cadre de contenu. Le cadre de contenu est indépendant de l’éditeur, afin de s’assurer qu’il n’y a aucun conflit en raison de CSS ou JavaScript.

Le cadre de contenu se situe dans la partie droite de la fenêtre, sous la barre d’outils.

![Cadre de contenu](assets/ui-content-frame.png)

### Cadre d’éditeur {#editor-frame}

Le cadre d’éditeur active les fonctions d’édition.

Le cadre d’éditeur est un conteneur pour l’ensemble des éléments de création de pages. Il se situe au-dessus du cadre de contenu et comprend les éléments suivants :

* Barre d’outils supérieure
* Panneau latéral
* Tous les recouvrements
* Tout autre élément de création de pages ; la barre d’outils des composants, par exemple

![Cadre d’éditeur](assets/ui-editor-frame.png)

### Panneau latéral {#side-panel}

Contient trois onglets par défaut. Le **Ressources** et **Composants** Les onglets vous permettent de sélectionner ces éléments, de les faire glisser du panneau et de les déposer sur la page. Le **Arborescence de contenu** vous permet d’examiner la hiérarchie du contenu de la page.

Par défaut, le panneau latéral est masqué. Lorsqu’elle est sélectionnée, elle s’affiche sur le côté gauche ou lorsque la largeur de la fenêtre est inférieure à 1 024 pixels, elle s’étend sur toute la fenêtre comme, par exemple, sur un appareil mobile.

![Panneau latéral](assets/ui-side-panel.png)

### Panneau latéral – Ressources {#side-panel-assets}

Dans l’onglet Ressources, vous pouvez effectuer une sélection parmi la plage de ressources. Vous pouvez également filtrer selon un terme spécifique ou sélectionner un groupe.

![Onglet Ressources](assets/ui-side-panel-assets.png)

### Panneau latéral - Groupes de ressources {#side-panel-asset-groups}

Dans l’onglet Ressources, vous pouvez utiliser une liste déroulante pour sélectionner les groupes de ressources spécifiques.

![Groupes de ressources](assets/ui-side-panel-asset-groups.png)

### Panneau latéral – Composants {#side-panel-components}

Dans l’onglet Composants , vous pouvez effectuer une sélection dans la plage de composants. Vous pouvez également filtrer selon un terme spécifique ou sélectionner un groupe.

![Onglet Composants](assets/ui-side-panel-components.png)

### Panneau latéral - Arborescence de contenu {#side-panel-content-tree}

Dans l’onglet Arborescence de contenu, vous pouvez afficher la hiérarchie du contenu de la page. Cliquer sur une entrée dans l’onglet permet d’accéder à l’élément et de le sélectionner sur la page dans l’éditeur.

![Arborescence de contenu](assets/ui-side-panel-content-tree.png)

### Recouvrements {#overlays}

Recouvre le cadre de contenu et est utilisé par la fonction [calques](#layer) pour réaliser le mécanisme d’interaction transparente avec les composants et leur contenu.

Les recouvrements résident dans le cadre d’éditeur (avec tous les autres éléments de création de pages) même si, en fait, ils recouvrent les composants appropriés dans le cadre de contenu.

![Recouvrements](assets/ui-overlays.png)

### Calque {#layer}

Un calque est un groupe indépendant de fonctionnalités pouvant être activées pour :

* fournir une vue différente de la page ;
* vous permettre de manipuler une page et/ou d’interagir avec celle-ci.

Les calques fournissent des fonctionnalités sophistiquées pour toute la page, par opposition aux actions spécifiques sur un composant individuel.

AEM s’accompagne de plusieurs calques qui sont déjà implémentés pour la création de pages. Il s’agit notamment des calques d’édition, de prévisualisation et d’annotation.

>[!NOTE]
>
>Les calques sont un concept puissant qui affecte la vue de l’utilisateur et son interaction avec le contenu de la page. Lorsque vous développez vos propres calques, assurez-vous qu’ils sont nettoyés à la sortie.

### Sélecteur de calques {#layer-switcher}

Le sélecteur de calques vous permet de choisir le calque à utiliser. Lorsqu’il est fermé, il indique le calque en cours d’utilisation.

Le sélecteur de calques est disponible sous forme de liste déroulante dans la barre d’outils (dans la partie supérieure de la fenêtre, dans le cadre de l’éditeur).

![Sélecteur de calques](assets/ui-layer-switcher.png)

### Barre d’outils des composants {#component-toolbar}

Chaque instance d’un composant affiche sa barre d’outils en cas de clic (une fois ou avec un double-clic lent). La barre d’outils contient les actions spécifiques (par exemple, copier, coller, ouvrir l’éditeur) qui sont disponibles pour l’instance du composant sur la page.

En fonction de l’espace disponible, les barres d’outils de composant sont placées dans le coin supérieur, ou inférieur, droit du composant approprié.

![Barre d’outils de composants](assets/ui-component-toolbar.png)

## Informations supplémentaires {#further-information}

<!--For more details about the concepts around the touch-enabled UI, continue to the article [Concepts of the AEM Touch-Enabled UI](/help/sites-developing/touch-ui-concepts.md).-->

Pour plus d’informations techniques, voir [Jeu de documentation JS](https://developer.adobe.com/experience-manager/reference-materials/6-5/jsdoc/ui-touch/editor-core/index.html) pour l’éditeur de page.
