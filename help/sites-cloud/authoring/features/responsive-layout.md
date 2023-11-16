---
title: Mise en page réactive
description: AEM permet de créer une mise en page réactive pour vos pages.
exl-id: 87202742-5bed-4e87-a427-456a1a0e72cc
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '1734'
ht-degree: 86%

---

# Disposition réactive {#responsive-layout}

AEM permet d’avoir une mise en page réactive pour vos pages à l’aide de la fonction **Conteneur de mises en page** composant.

Vous disposez ainsi d’un système de paragraphes qui vous permet de positionner les composants dans une grille réactive. Cette grille peut réorganiser la mise en page en fonction de l’appareil/de la taille de fenêtre et du format. Le composant est utilisé conjointement avec la fonction [**Disposition** mode](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes), qui vous permet de créer et de modifier votre mise en page réactive en fonction de l’appareil.

Le conteneur de mise en page :

* Permet un alignement horizontal sur la grille, ainsi que la possibilité de placer côte à côte les composants dans la grille et de définir quand ils doivent être réduits/développés.
* Il utilise des points d’arrêt prédéfinis (par exemple, pour le téléphone, la tablette, etc.) pour vous permettre de définir le comportement requis du contenu pour l’orientation/les appareils associés.
   * Par exemple, vous pouvez personnaliser la taille du composant ou décider s’il peut être affiché sur des appareils spécifiques.
* Il peut être imbriqué pour permettre le contrôle des colonnes.

L’utilisateur ou l’utilisatrice peut ensuite afficher le rendu du contenu pour des appareils spécifiques à l’aide de l’émulateur.

AEM effectue une mise en page réactive de vos pages en combinant plusieurs mécanismes :

* Composant [**Conteneur de mise en page**](#adding-a-layout-container-and-its-content-edit-mode)

  Ce composant, qui est disponible dans l’[explorateur de composants](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser), fournit un système de paragraphes/grille qui permet d’ajouter et de positionner des composants dans une grille réactive. Il peut également être défini comme le système de paragraphes par défaut de votre page.

* [**Mode Mise en page**](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes)

  Une fois que le conteneur de mises en page est positionné sur la page, vous pouvez utiliser le mode **Mise en page** pour placer le contenu dans la grille réactive.

* [**Émulateur**](#selecting-a-device-to-emulate)
Vous pouvez ainsi créer et modifier des sites web réactifs qui réorganisent la mise en page en fonction de la taille de l’appareil ou de la fenêtre en redimensionnant les composants de manière interactive. L’utilisateur ou l’utilisatrice peut alors voir comment le contenu est rendu à l’aide de l’émulateur.

Grâce à ces mécanismes de grille réactive, vous pouvez :

* utiliser des points d’arrêt pour définir différentes mises en page de contenu en fonction de la largeur de l’appareil (selon le type et l’orientation de l’appareil) ;
* utiliser ces points d’arrêt et les mises en page de contenu pour veiller à ce que le contenu s’ajuste à la taille de la fenêtre du navigateur sur le poste de travail ;
* utiliser l’alignement horizontal sur la grille, ce qui permet de placer les composants dans la grille, de les redimensionner selon les besoins et de définir quand ils doivent être réduits ou développés pour être côte à côte ou l’un au-dessus de l’autre ;
* masquer des composants pour des mises en page spécifiques à certains appareils ;
* contrôler les colonnes.

En fonction de votre projet, le conteneur de mise en page peut être utilisé en tant que système de paragraphes par défaut pour vos pages ou en tant que composant pouvant être ajouté à votre page via l’explorateur de composants (ou les deux).

>[!TIP]
>
>Adobe propose une [documentation GitHub](https://adobe-marketing-cloud.github.io/aem-responsivegrid/) sur la mise en page réactive. Celle-ci peut servir de référence et être distribuée aux équipes de développement d’applications front-end pour leur permettre d’utiliser la grille AEM en dehors d’AEM, par exemple lors de la création de maquettes HTML statiques pour un site AEM en préparation.

>[!NOTE]
>
>L’utilisation des mécanismes ci-dessus est activée par une configuration du modèle. Pour plus d’informations, voir Configuration d’une mise en page réactive. <!-- Use of the above mechanisms is enabled by configuration on the template. See [Configuring Responsive Layout](/help/sites-administering/configuring-responsive-layout.md) for further information.-->

## Définitions de mise en page, émulation d’appareil et points d’arrêt {#layout-definitions-device-emulation-and-breakpoints}

Lorsque vous créez le contenu de votre site web, vous voulez être certain que celui-ci sera affiché correctement sur l’appareil utilisé pour le consulter :

AEM permet de définir des mises en page en fonction de la largeur de l’appareil :

* L’émulateur vous permet d’émuler ces mises en page sur divers appareils. Tout comme le type d’appareil, l’orientation, qui est sélectionnée à l’aide de l’option **Rotation du périphérique**, peut avoir une incidence sur le point d’arrêt sélectionné lors du changement de largeur.
* Les points d’arrêt sont des points qui séparent les définitions de mise en page.
   * Ils définissent la largeur maximale (en pixels) de n’importe quel appareil à l’aide d’une mise en page spécifique.
   * Les points d’arrêt sont généralement valides pour plusieurs appareils en fonction de la largeur de leur écran.
   * La plage d’un point d’arrêt s’étend sur la gauche, jusqu’au point d’arrêt suivant.
   * Vous ne pouvez pas sélectionner le point d’arrêt. La sélection de l’appareil et de l’orientation permet de sélectionner automatiquement le point d’arrêt adéquat.

L’appareil **Bureau**, qui ne possède pas de largeur spécifique, est associé au point d’arrêt par défaut (c’est-à-dire tout ce qui se trouve au-dessus du dernier point d’arrêt configuré).

>[!NOTE]
>
>Il est possible de définir des points d’arrêt pour chaque appareil, mais cela augmenterait la charge de travail requise pour la définition des mises en page et la maintenance.

Lors de l’utilisation de l’émulateur, vous sélectionnez un appareil spécifique pour l’émulation et la définition de disposition. Le point d’arrêt associé est également mis en surbrillance. Toutes les modifications apportées à la disposition s’appliquent à d’autres appareils auxquels s’applique le point d’arrêt. En d’autres termes, tous les appareils placés à gauche du marqueur de point d’arrêt actif, mais avant le marqueur de point d’arrêt suivant.

Par exemple, lorsque vous sélectionnez l’appareil **iPhone 6 Plus** (défini avec une largeur de 540 pixels) pour l’émulation et la disposition, le point d’arrêt **Téléphone** (défini sur 768 pixels) est également activé. Toutes les modifications apportées à la mise en page pour l’**iPhone 6** s’appliquent aux autres appareils sous le point d’arrêt **Téléphone**, tel que l’**iPhone 5** (défini sur 320 pixels).

![Émulateurs](/help/sites-cloud/authoring/assets/responsive-layout-emulators.png)

## Sélection d’un appareil à émuler {#selecting-a-device-to-emulate}

1. Ouvrez la page requise en vue de la modifier. Par exemple :

   `http://<host>:<port>/editor.html/content/wknd/en/sports/la-skateparks.html`

1. Sélectionnez l’icône **Émulateur** dans la barre d’outils supérieure :

   ![Bouton Émulateur](/help/sites-cloud/authoring/assets/emulator.png)

1. La barre d’outils de l’émulateur s’ouvre.

   ![Barre d’outils de l’émulateur](/help/sites-cloud/authoring/assets/responsive-layout-emulator-toolbar.png)

   La barre d’outils de l’émulateur affiche des options de mise en page supplémentaires :

   * **Rotation du périphérique** - Permet de faire pivoter un appareil de l’orientation verticale (portrait) à l’orientation horizontale (paysage), et inversement.

   ![Bouton Rotation de l’appareil - Paysage](/help/sites-cloud/authoring/assets/responsive-layout-rotate-device-landscape-button.png)
   ![Bouton Rotation de l’appareil - Portrait](/help/sites-cloud/authoring/assets/responsive-layout-rotate-device-portrait-button.png)

   * **Sélectionner un périphérique** : permet de sélectionner un appareil spécifique à émuler dans une liste (pour plus d’informations, voir l’étape suivante).

   ![Bouton Sélectionner un appareil](/help/sites-cloud/authoring/assets/responsive-layout-select-device-button.png)

1. Pour sélectionner un appareil spécifique à émuler, vous pouvez effectuer l’une des opérations suivantes :

   * utiliser l’icône Sélectionner un périphérique et sélectionner l’appareil dans la liste déroulante ;
   * Appuyez/cliquez sur l’indicateur de l’appareil dans la barre d’outils de l’émulateur.

   ![Menu déroulant Sélectionner un appareil](/help/sites-cloud/authoring/assets/responsive-layout-select-device-dropdown.png)

1. Une fois un appareil spécifique sélectionné, vous pouvez visualiser les éléments suivants :

   * Marqueurs actifs de l’appareil sélectionné (**iPad**, par exemple).
   * Marqueurs actifs du [point d’arrêt](#layout-definitions-device-emulation-and-breakpoints) approprié (**Tablette**, par exemple).
   * La ligne pointillée bleue représente le *pli* pour l’appareil sélectionné (ici, **iPhone 6 Plus** en mode Paysage).

   ![Le pli](/help/sites-cloud/authoring/assets/responsive-layout-fold.png)

   * Le pli peut également être considéré comme un saut de ligne de page (à ne pas confondre avec les [points d’arrêt](#layout-definitions-device-emulation-and-breakpoints)) pour le contenu. Il est affiché à des fins pratiques pour indiquer la partie du contenu que l’utilisateur voit sur l’appareil avant de faire défiler l’écran.
   * La ligne du pli ne s’affiche pas si la hauteur de l’appareil émulé est supérieure à la taille de l’écran.
   * Le pli est affiché pour faciliter le travail de l’auteur et n’apparaît pas sur la page publiée.

## Ajout d’un conteneur de mise en page et de son contenu (mode d’édition) {#adding-a-layout-container-and-its-content-edit-mode}

Un **conteneur de mise en page** est un système de paragraphes qui présente les caractéristiques suivantes :

* Il contient d’autres composants.
* Il définit la mise en page.
* Il répond aux modifications.

>[!NOTE]
>
>S’il n’est pas encore disponible, le **conteneur de mise en page** doit être explicitement activé pour un système de paragraphes ou une page. <!-- If not already available, the **Layout Container** must be explicitly [activated for a paragraph system/page](/help/sites-administering/configuring-responsive-layout.md).-->

1. Le **conteneur de mise en page** est disponible en tant que composant standard dans l’[explorateur de composants](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser). À partir de là, vous pouvez le faire glisser vers l’emplacement requis sur la page, après lequel vous pouvez voir la variable **Faites glisser les composants ici** espace réservé.
1. Vous pouvez ensuite ajouter des composants au conteneur de mise en page, qui contiendront le contenu proprement dit :

   ![Conteneur de mise en page](/help/sites-cloud/authoring/assets/responsive-layout-add-to-layout-container.png)

## Sélection et exécution d’une action sur un conteneur de mise en page (mode d’édition) {#selecting-and-taking-action-on-a-layout-container-edit-mode}

À l’instar des autres composants, vous pouvez sélectionner un conteneur de mise en page, puis effectuer une opération (couper, copier, supprimer) sur ce dernier (en mode d’**édition**) :

>[!CAUTION]
>
>Un conteneur de mise en page étant un système de paragraphes, la suppression du composant entraîne la suppression de la grille de mise en page et de tous les composants (ainsi que de leur contenu) qu’il contient.

1. Si vous pointez ou appuyez sur l’espace réservé de la grille, le menu d’actions s’affiche.

   ![Ajout au conteneur de mise en page](/help/sites-cloud/authoring/assets/responsive-layout-container.png)

   Vous devez sélectionner l’option **Parent**.

   ![Bouton Parent](/help/sites-cloud/authoring/assets/responsive-layout-parent-button.png)

1. Si le composant de mise en page est imbriqué, la sélection de l’option **Parent** présente une sélection déroulante, ce qui vous permet de sélectionner le conteneur de mise en page imbriqué ou ses parents.

   Lorsque vous placez le pointeur de la souris sur les noms de conteneurs dans la liste déroulante, leurs contours s’affichent sur la page.

   * Les contours du conteneur de mises en page imbriqué du plus bas niveau s’affichent en bleu.
   * Les contours de chaque conteneur successif s’affichent dans une nuance plus claire de bleu.

   ![Conteneurs imbriqués](/help/sites-cloud/authoring/assets/responsive-layout-nested.png)

1. La grille entière est mise en surbrillance avec son contenu. La barre d’outils s’affiche. Vous pouvez alors sélectionner une action comme **Supprimer**.

## Définition des mises en page (mode Mise en page) {#defining-layouts-layout-mode}

>[!NOTE]
>
>Vous pouvez définir une mise en page distincte pour chaque [point d’arrêt](#layout-definitions-device-emulation-and-breakpoints) (déterminée par l’orientation et le type d’appareil émulé).

Pour configurer la mise en page d’une grille réactive mise en œuvre avec le conteneur de mise en page, vous devez utiliser le mode **Mise en page**.

Le mode **Mise en page** peut être activé de deux façons.

* À l’aide du [menu de mode de la barre d’outils](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes), en sélectionnant le mode **Mise en page**.
   * Sélectionnez le mode **Mise en page** de la même façon que vous passeriez en mode **Édition** ou en mode **Ciblage**.
   * Le mode **Mise en page** est un **mode** persistant, ce qui signifie qu’il reste sélectionné jusqu’à ce que vous choisissiez un autre mode à l’aide du sélecteur de mode.
* Lors de la [modification d’un composant individuel](/help/sites-cloud/authoring/fundamentals/editing-content.md#edit-component-layout).
   * En utilisant l’option **Mise en page** dans le menu d’action rapide du composant, vous pouvez passer au mode **Mise en page**.
   * Le mode **Mise en page** persiste pendant la modification du composant et bascule vers le mode **Édition** lorsqu’un autre composant est sélectionné.

Une fois le mode Mise en page sélectionné, vous pouvez effectuer diverses actions sur une grille :

* Redimensionnez les composants de contenu à l’aide des points bleus. Le redimensionnement s’accroche toujours à la grille. Lors du redimensionnement, la grille d’arrière-plan s’affiche pour faciliter l’alignement :

  ![Redimensionnement des composants](/help/sites-cloud/authoring/assets/responsive-layout-resizing.png)

  >[!NOTE]
  >
  >Les proportions et les rapports sont conservés lorsque des composants, tels que des **images**, sont redimensionnés.

* Cliquez/appuyez sur un composant de contenu. La barre d’outils vous permet d’effectuer les opérations suivantes :
   * **Parent** - Permet de sélectionner l’intégralité du composant Conteneur de mises en page pour effectuer une action.
   * **Flotter sur une nouvelle ligne** : le composant est déplacé vers une nouvelle ligne selon l’espace disponible dans la grille.
   * **Masquer le composant** : le composant devient invisible (il peut être restauré à partir de la barre d’outils du conteneur de mises en page).

  ![Masquer le composant](/help/sites-cloud/authoring/assets/responsive-layout-hide.png)

* Dans **Disposition** vous pouvez appuyer/cliquer sur le mode **Faire glisser des composants ici** pour sélectionner le composant entier. La barre d’outils s’affiche pour ce mode.

  La barre d’outils propose différentes options en fonction de l’état du composant de mise en page et des composants qui lui sont associés. Par exemple :

   * **Parent** : permet de sélectionner le composant parent.

     ![Bouton Parent](/help/sites-cloud/authoring/assets/responsive-layout-parent-button.png)

   * **Afficher les composants masqués** : affiche tous les composants ou des composants individuels. Le chiffre indique le nombre actuel de composants masqués. Le compteur indique le nombre de composants masqués.

     ![Bouton Afficher les composants masqués](/help/sites-cloud/authoring/assets/responsive-layout-show-button.png)

   * **Rétablir la disposition du point d’arrêt** : rétablit la mise en page par défaut. Aucune mise en page personnalisée n’est imposée.

     ![Bouton Rétablir la disposition du point d’arrêt](/help/sites-cloud/authoring/assets/responsive-layout-revert-button.png)

   * **Flotter sur une nouvelle ligne** : déplace le composant d’une position vers le haut si l’espace est suffisant.

     ![Bouton Flotter sur une nouvelle ligne](/help/sites-cloud/authoring/assets/responsive-layout-float-button.png)

   * **Masquer le composant** : masque le composant actif.

     ![Bouton Masquer le composant](/help/sites-cloud/authoring/assets/responsive-layout-hide-button.png)

  >[!NOTE]
  >
  >Dans l’exemple ci-dessus, les actions de flottement et de masquage sont disponibles, car ce conteneur de mise en page est imbriqué dans un conteneur de mise en page parent.

   * **Afficher les composants**
Sélectionnez les composants parents pour afficher la barre d’outils comportant l’option **Afficher les composants masqués**. Dans cet exemple, deux composants sont masqués.

     ![Afficher les composants](/help/sites-cloud/authoring/assets/responsive-layout-unhide.png)

  Si vous sélectionnez l’option **Afficher les composants masqués**, les composants actuellement masqués s’affichent en bleu à leur position initiale.

  ![Bouton Restaurer tout](/help/sites-cloud/authoring/assets/responsive-layout-restore-all.png)

  Sélectionnez **Restaurer tout** pour afficher tous les composants masqués.
