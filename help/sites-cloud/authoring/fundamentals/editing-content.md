---
title: Modification du contenu de la page
description: Une fois votre page créée, vous pouvez en modifier le contenu pour effectuer les mises à jour nécessaires
exl-id: 8af0f621-14e8-4605-a51a-a3be21f19092
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '2974'
ht-degree: 94%

---


# Modification du contenu de la page{#editing-page-content}

Une fois la page créée (une nouvelle page ou dans le cadre d’un lancement ou d’une Live Copy), vous pouvez modifier le contenu pour effectuer toute mise à jour dont vous avez besoin.

Le contenu est ajouté à l’aide des [composants](/help/sites-cloud/authoring/features/components-console.md) (appropriés au type de contenu) qui peuvent être glissés sur la page. Ils peuvent ensuite être modifiés sur place, déplacés ou supprimés.

>[!NOTE]
>
>Vous devez disposer des droits d’accès et des autorisations appropriés sur votre compte pour modifier les pages.
>
>En cas de problème, contactez votre administrateur système.
<!--
>Your account needs the [appropriate access rights](/help/sites-administering/security.md) and [permissions](/help/sites-administering/security.md#permissions) to edit pages.
-->

>[!NOTE]
>
>Si votre page et/ou modèle ont été configurés correctement, vous pouvez utiliser la [mise en page réactive](/help/sites-cloud/authoring/features/responsive-layout.md) lors de la modification.

>[!TIP]
>
>En mode **Édition**, les liens dans votre contenu sont visibles, mais ils ne sont **pas accessibles**. Utilisez le [mode Aperçu](#previewing-pages) pour naviguer en suivant les liens.

{{edge-delivery-authoring}}

## Barre d’outils Page {#page-toolbar}

La barre d’outils Page permet d’accéder à la fonctionnalité appropriée, en fonction de la configuration de la page.

![Barre d’outils Page](/help/sites-cloud/authoring/assets/editing-page-toolbar.png)

La barre d’outils permet d’accéder à de nombreuses options. Selon votre contexte et votre configuration actuels, certaines options peuvent ne pas être disponibles.

* **Activer/désactiver le panneau latéral**

  Cette action ouvre/ferme le panneau latéral, qui contient l’[explorateur de ressources](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser), l’[explorateur de composants](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser) et l’[arborescence de contenu](/help/sites-cloud/authoring/fundamentals/environment-tools.md#content-tree).

  ![Bascule du panneau latéral](/help/sites-cloud/authoring/assets/side-panel-toggle.png)

* **Informations sur la page**

  Permet d’accéder au menu [Informations sur la page](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information) comprenant les détails de la page et les actions qui peuvent être entreprises sur la page, notamment l’affichage et la modification des informations de la page, l’affichage des propriétés de la page et la publication/annulation de la publication de la page.

  ![Bouton Informations sur la page](/help/sites-cloud/authoring/assets/page-information-icon.png)

* **Émulateur**

  Fait basculer la [barre d’outils de l’émulateur](/help/sites-cloud/authoring/features/responsive-layout.md#selecting-a-device-to-emulate) utilisée pour émuler l’aspect de la page sur un autre appareil. Cette option est automatiquement basculée en mode de mise en page.

  ![Bouton Émulateur](/help/sites-cloud/authoring/assets/emulator.png)

* **ContextHub**

  Ouvre [ContextHub](/help/sites-cloud/authoring/personalization/contexthub.md). Uniquement disponible en mode Aperçu.

  ![Bouton ContextHub](/help/sites-cloud/authoring/assets/context-hub.png)

* **Titre de la page**

  Ceci est à titre purement informatif.

  ![Titre de la page](/help/sites-cloud/authoring/assets/page-title.png)

* **Sélecteur de mode**

  Affiche le [mode](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) actuel et vous permet de sélectionner un autre mode, tel que l’édition, la mise en page, la temporisation ou le ciblage.

  ![Bouton Sélecteur de mode](/help/sites-cloud/authoring/assets/mode-selector.png)

* **Aperçu**

  Permet d’activer le [mode Aperçu](#preview-mode). Cette option affiche la page telle qu’elle apparaîtra une fois publiée.

  ![Bouton Aperçu](/help/sites-cloud/authoring/assets/preview.png)

* **Annoter**

  Permet d’ajouter [des annotations](/help/sites-cloud/authoring/fundamentals/annotations.md) à la page lors de la révision d’une page. Après la première annotation, l’icône prend la forme d’un nombre indiquant le nombre d’annotations sur la page.

  ![Bouton Annotation](/help/sites-cloud/authoring/assets/annotations.png)

### Notification de statut {#status-notification}

Si la page fait partie d’un ou de plusieurs [workflows](/help/sites-cloud/authoring/workflows/overview.md), ces informations s’affichent dans une barre de notification située en haut de l’écran lorsque vous la modifiez.

![Notification de workflow](/help/sites-cloud/authoring/assets/editing-workflow-notification.png)

>[!NOTE]
>
>La barre de statut n’est visible que pour les comptes d’utilisateur ou d’utilisatrice disposant des privilèges appropriés.

La notification répertorie le workflow qui s’exécute sur la page. Si la personne utilisatrice est impliquée dans l’étape de workflow en cours, les options pour [affecter le statut du workflow](/help/sites-cloud/authoring/workflows/participating.md) et obtenir plus d’informations sur le workflow sont également disponibles, par exemple :

* **Terminé** : ouvre la boîte de dialogue **Terminer l’élément de travail**
* **Déléguer** : ouvre la boîte de dialogue **Terminer l’élément de travail**
* **Afficher les détails** : ouvre la fenêtre **Détails** du workflow

L’utilisation de la barre de notification pour terminer et déléguer des étapes de workflow fonctionne de la même manière que la [participation à des workflows](/help/sites-cloud/authoring/workflows/participating.md) depuis la boîte de réception de notifications.

Si la page est soumise à plusieurs workflows, leur nombre est indiqué à droite de la notification, avec des chevrons, pour vous permettre de les parcourir.

![Notifications de workflows multiples](/help/sites-cloud/authoring/assets/editing-workflow-notification-multiple.png)

## Espace réservé au composant {#component-placeholder}

L’espace réservé indique le positionnement du composant que vous déposez. Pour l’afficher, survolez le composant.

* Lors de l’ajout d’un nouveau composant à la page (en le faisant glisser depuis l’explorateur de composants) :

  ![Espace réservé lors de l’ajout d’un nouveau composant à une page](/help/sites-cloud/authoring/assets/editing-component-placeholder.png)

* Lors du déplacement d’un composant existant :

  ![Espace réservé lors du déplacement d’un composant existant sur une page](/help/sites-cloud/authoring/assets/editing-component-placeholder-existing.png)

## Insertion d’un composant {#inserting-a-component}

### Insertion d’un composant depuis l’explorateur de composants {#inserting-a-component-from-the-components-browser}

Vous pouvez ajouter un nouveau composant à l’aide de l’[explorateur de composants](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser). L’[espace réservé du composant](#component-placeholder) vous indique où sera positionné le composant.

1. Assurez-vous que votre page est en mode [**Modifier**](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes).
1. Ouvrez l’[explorateur de composants](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser).
1. Faites glisser le composant jusqu’à la [position requise](#component-placeholder).
1. [Modifiez](#edit-content) le composant.

>[!NOTE]
>
>Sur un appareil mobile, l’explorateur de composants remplit tout l’écran. Quand vous faites glisser un composant, l’explorateur se ferme pour afficher à nouveau la page afin que vous puissiez placer le composant.

### Insertion d’un composant à partir du système de paragraphes {#inserting-a-component-from-the-paragraph-system}

Vous pouvez ajouter un nouveau composant à l’aide de la case **Faire glisser les composants ici** du système de paragraphes :

1. Assurez-vous que votre page est en mode [**Modifier**](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes).
1. Il existe deux façons de sélectionner et d’ajouter un nouveau composant à partir du système de paragraphes :

   * Sélectionnez l’option **Insérer le composant** (+) depuis la barre d’outils d’un composant existant ou dans la zone **Faire glisser les composants ici**.

     ![Insertion d’un composant](/help/sites-cloud/authoring/assets/editing-insert-component.png)

   * Si vous utilisez un ordinateur de bureau, vous pouvez double-cliquer sur la zone **Faire glisser les composants ici** .

   * La boîte de dialogue **Insérer un nouveau composant** s’ouvre pour vous permettre de sélectionner le composant requis :

     ![Boîte de dialogue Insérer un nouveau composant](/help/sites-cloud/authoring/assets/editing-insert-component-selection.png)

1. Le composant sélectionné est ajouté au bas de la page. [Modifiez](#edit-content) le composant si nécessaire.

### Insertion d’un composant à partir de l’explorateur de ressources {#inserting-a-component-using-the-assets-browser}

Vous pouvez également ajouter un nouveau composant à la page en faisant glisser une ressource depuis le [navigateur de ressources](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser). Cela crée automatiquement un composant du type approprié contenant la ressource.

Ce comportement peut être configuré pour votre installation. Pour plus d’informations, voir Configuration d’un système de paragraphes de manière à faire glisser une ressource pour créer une instance de composant. <!--This behavior can be configured for your installation. See [Configuring a Paragraph System so that Dragging an Asset Creates a Component Instance](/help/sites-developing/developing-components.md#configuring-a-paragraph-system-so-that-dragging-an-asset-creates-a-component-instance) for further details.-->

Pour créer un composant en faisant glisser l’un des types de ressources ci-dessus, suivez ces étapes :

1. Assurez-vous que votre page est en mode [**Modifier**](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes).
1. Ouvrez l’[explorateur de ressources](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser).
1. Faites glisser le composant jusqu’à la position requise. L’[espace réservé du composant](#component-placeholder) vous indique où le composant est positionné.

   Un composant, adapté au type de ressource, est créé à l’emplacement requis. Il contient la ressource sélectionnée.

1. [Modifiez](#edit-content) le composant si nécessaire.

>[!NOTE]
>
>Sur un appareil mobile, l’explorateur de ressources remplit tout l’écran. Quand vous faites glisser une ressource, l’explorateur se ferme pour afficher à nouveau la page. Vous pouvez alors placer la ressource.

Si, lors de l’exploration des ressources, vous estimez qu’il est nécessaire d’apporter une modification rapide à l’une d’elles, vous pouvez lancer directement l’[éditeur de ressources](/help/assets/manage-digital-assets.md) à partir de l’explorateur en cliquant sur l’icône d’édition située en regard de son nom.

![Bouton Modifier la ressource](/help/sites-cloud/authoring/assets/asset-edit-button.png)

## Barre d’outils des composants {#component-toolbar}

Sélectionner un composant ouvre la barre d’outils. Cela permet d’accéder à diverses actions pouvant être réalisées sur le composant.

Les actions disponibles sont affichées comme il convient ; ces actions ne peuvent pas toutes être décrites ici.

![Barre d’outils des composants](/help/sites-cloud/authoring/assets/editing-component-toolbar.png)

* **Modifier**

  [En fonction du type de composant](/help/sites-cloud/authoring/fundamentals/components.md), vous pouvez [en modifier le contenu](#edit-content). Souvent, une barre d’outils est fournie.

  ![Bouton Modifier](/help/sites-cloud/authoring/assets/editing-component-toolbar-edit.png)

* **Configurer**

  [En fonction du type de composant](/help/sites-cloud/authoring/fundamentals/components.md), vous pouvez modifier et configurer ses propriétés. Souvent, une boîte de dialogue s’ouvre.

  ![Bouton Configurer](/help/sites-cloud/authoring/assets/editing-component-toolbar-configure.png)

* **Copier**

  Le composant est copié dans le presse-papiers. Après l’action de collage, le composant d’origine reste.

  ![Bouton Copier](/help/sites-cloud/authoring/assets/editing-component-toolbar-copy.png)

* **Couper**

  Le composant est copié dans le presse-papiers. Après l’action de collage, le composant d’origine est supprimé.

  ![Bouton Couper](/help/sites-cloud/authoring/assets/editing-component-toolbar-cut.png)

* **Supprimer**

  Après confirmation de votre part, le composant de la page est supprimé.

  ![Bouton Supprimer](/help/sites-cloud/authoring/assets/editing-component-toolbar-delete.png)

* **Insérer le composant**

  La boîte de dialogue s’ouvre, permettant d’[ajouter un nouveau composant](/help/sites-cloud/authoring/fundamentals/editing-content.md#inserting-a-component-from-the-paragraph-system).

  ![Bouton Insérer](/help/sites-cloud/authoring/assets/editing-component-toolbar-insert.png)

* **Coller**

  Le composant est collé du presse-papiers dans la page. L’original est conservé ou non, selon la fonction que vous avez utilisée (Couper ou Coller).

   * Vous pouvez coller les composants sur la même page ou sur une autre.
   * L’élément collé est collé au-dessus de l’élément pour lequel vous avez sélectionné l’action de collage.
   * L’action de collage ne s’affiche que si du contenu se trouve dans le presse-papiers.

  ![Bouton Coller](/help/sites-cloud/authoring/assets/editing-component-toolbar-paste.png)

  >[!NOTE]
  >
  >Si vous effectuez un collage sur une autre page qui était déjà ouverte avant l’opération de couper/copier, vous devez actualiser la page pour afficher le contenu collé.

* **Groupe**

  Cette option permet de sélectionner plusieurs composants à la fois. Vous pouvez obtenir le même résultat sur un poste de travail à l’aide des commandes **Ctrl-clic** ou **Commande-clic**.

  ![Bouton Groupe](/help/sites-cloud/authoring/assets/editing-component-toolbar-group.png)

* **Parent**

  Permet de sélectionner le composant parent du composant sélectionné.

  ![Bouton Parent](/help/sites-cloud/authoring/assets/editing-component-toolbar-parent.png)

* **Disposition**

  Cette option permet de modifier la [disposition](/help/sites-cloud/authoring/fundamentals/editing-content.md#edit-component-layout) du composant sélectionné. Cela s’applique uniquement au composant sélectionné et n’active pas le [mode de disposition](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) pour la page entière.

  ![Bouton Mise en page](/help/sites-cloud/authoring/assets/editing-component-toolbar-layout.png)

* **Convertir en variation de fragment d’expérience**

  Vous pouvez ainsi créer un [fragment d’expérience](/help/sites-cloud/authoring/fundamentals/experience-fragments.md) à partir du composant sélectionné ou l’ajouter à un fragment d’expérience existant.

  ![Bouton Convertir en variation de fragment d’expérience](/help/sites-cloud/authoring/assets/editing-component-toolbar-xf.png)

## Modifier le contenu {#edit-content}

Deux méthodes permettent d’ajouter et/ou de modifier le contenu dans les composants :

* Ouvrez la [boîte de dialogue du composant pour la modification](#component-edit-dialog).
* [Faites glisser et déposez un élément](#drag-and-drop-assets-into-component) depuis l’explorateur de ressources pour ajouter directement du contenu.

### Boîte de dialogue de modification du composant {#component-edit-dialog}

Vous pouvez ouvrir un composant pour modifier le contenu à l’aide de l’icône [Modifier (crayon) de la barre d’outils du composant](#component-toolbar).

Les options de modification exactes dépendent du composant. Pour certains composants, [toutes les actions ne sont disponibles qu’en mode plein écran](#edit-content-full-screen-mode). Par exemple :

* Composant textuel

  ![Barre d’outils du composant textuel](/help/sites-cloud/authoring/assets/editing-text-component-toolbar.png)

* Composant d’image

  ![Barre d’outils du composant d’image](/help/sites-cloud/authoring/assets/editing-image-component-toolbar.png)

  >[!NOTE]
  >
  >L’édition ne fonctionne pas sur un composant d’image vide.
  >
  >Vous devez faire glisser ou charger une image (à l’aide de l’option Configurer) avant de commencer à la modifier.

* Composant d’image - Plein écran

  [Le passage en mode plein écran](#edit-content-full-screen-mode) pour le composant d’image permet de libérer de l’espace pour modifier l’image et d’afficher des options de modification supplémentaires, telles que **Carte de lancement** et **Réinitialiser le zoom**. En outre, le mode plein écran permet de sélectionner les paramètres prédéfinis de recadrage.

  ![Mode Plein écran du composant d’image](/help/sites-cloud/authoring/assets/editing-image-component-full-screen.png)

* Les composants construits à partir de plusieurs composants de base vous demandent tout d’abord de confirmer à quel jeu d’options de modification vous souhaitez accéder :

### Faire glisser et déposez des éléments dans des composants {#drag-and-drop-assets-into-component}

Pour certains types de composants (comme les images), vous pouvez faire glisser et déposer des éléments depuis l’explorateur de ressources directement dans le composant pour mettre à jour le contenu.

## Modifier le contenu en mode Plein écran {#edit-content-full-screen-mode}

Pour tous les composants, vous pouvez accéder au mode Plein écran (ou le quitter) avec :

![Bouton Plein écran](/help/sites-cloud/authoring/assets/editing-full-screen.png)

Par exemple, le composant **textuel** :

![Composant textuel en plein écran](/help/sites-cloud/authoring/assets/editing-text-full-screen.png)

>[!NOTE]
>
>Pour certains composants, le mode Plein écran dispose d’un plus grand nombre d’options disponibles que l’éditeur en place de base.

## Déplacement d’un composant {#moving-a-component}

Pour déplacer un composant de paragraphe :

1. Sélectionnez le paragraphe à déplacer en sélectionnant ou en cliquant longuement.
1. Faites glisser le paragraphe vers son nouvel emplacement. AEM indique où le paragraphe peut être déposé. Déposez-le à l’emplacement de votre choix.

   ![Déplacement d’un composant](/help/sites-cloud/authoring/assets/editing-moving-component.png)

1. Votre paragraphe est déplacé.

>[!TIP]
>
>Vous pouvez également utiliser la technique du [couper/coller](#component-toolbar) pour déplacer un composant.

## Modification de la disposition du composant {#edit-component-layout}

Au lieu de basculer à plusieurs reprises entre les modes Modifier et de [Disposition](/help/sites-cloud/authoring/features/responsive-layout.md) pour ajuster un composant, vous pouvez sélectionner l’action **Disposition** pour un composant afin d’en modifier la mise en page. Cela vous évite de devoir quitter le mode Modifier, ce qui se traduit par un gain de temps.

1. Lorsque le mode **Modifier** de la console Sites est actif, la sélection d’un composant déclenche l’affichage de sa barre d’outils.

   ![Barre d’outils d’un composant de page](/help/sites-cloud/authoring/assets/editing-layout-toolbar.png)

   Sélectionnez l’action **Disposition** pour ajuster la disposition du composant.

   ![Bouton Disposition de la barre d’outils d’un composant](/help/sites-cloud/authoring/assets/editing-component-toolbar-layout.png)

1. Une fois l’action de mise en page sélectionnée :

   * Les poignées de redimensionnement du composant s’affichent.
   * La barre d’outils de l’émulateur s’affiche en haut de l’écran.
   * Les actions de mise en page au lieu des actions de modification standard s’affichent dans la barre d’outils du composant.

   ![Un composant en mode Mise en page](/help/sites-cloud/authoring/assets/editing-layout-mode.png)

   Vous pouvez à présent modifier la mise en page du composant, comme vous le feriez dans le [mode de mise en page](/help/sites-cloud/authoring/features/responsive-layout.md#defining-layouts-layout-mode).

1. Après avoir effectué les modifications nécessaires au niveau de la mise en page, cliquez sur le bouton **Fermer** dans le menu des actions du composant pour arrêter la session de modification. La barre d’outils du composant revient à son état d’édition normal.

   ![Barre d’outils d’un composant de page](/help/sites-cloud/authoring/assets/editing-layout-exit.png)

>[!TIP]
>
>L’action de mise en page est limitée au composant sélectionné. Par exemple, si vous modifiez la mise en page d’un composant, puis cliquez sur un autre composant, la barre d’outils d’édition standard (et non la barre d’outils de mise en page) s’affiche pour le nouveau composant sélectionné, les poignées de redimensionnement et la barre d’outils de l’émulateur disparaissent.
>
>Si vous devez modifier la disposition globale de la page et affecter ainsi plusieurs composants, basculez vers le [mode Disposition](/help/sites-cloud/authoring/features/responsive-layout.md).

## Composants hérités {#inherited-components}

L’héritage est le mécanisme par lequel le contenu peut être automatiquement envoyé d’un composant vers un autre. Les composants hérités peuvent être le produit de divers scénarios :

* [Gestion de plusieurs sites](/help/sites-cloud/administering/msm/overview.md)
* [Lancements](/help/sites-cloud/authoring/launches/overview.md) (quand basés sur une Live Copy)

Vous pouvez annuler (puis réactiver) l’héritage. Selon le composant, cette option peut être disponible à partir de la barre d’outils du composant, s’il se trouve sur une page faisant partie d’une Live Copy ou d’un lancement (en fonction d’une Live Copy).

![Barre d’outils de composant montrant la relation d’héritage](/help/sites-cloud/authoring/assets/editing-component-toolbar-inheritance.png)

Par exemple :

* Annuler l’héritage

  ![Bouton Annuler l’héritage](/help/sites-cloud/authoring/assets/editing-cancel-inheritance.png)

* Réactiver l’héritage (si l’héritage est déjà annulé)

  ![Bouton Réactiver l’héritage](/help/sites-cloud/authoring/assets/editing-reenable-inheritance.png)

* L’action de déploiement est également disponible dans le plan directeur ou la source Live Copy.

  ![Bouton Déployer](/help/sites-cloud/authoring/assets/editing-rollout.png)

## Modification du modèle de page {#editing-the-page-template}

Vous pouvez facilement passer à l’[éditeur de modèles](/help/sites-cloud/authoring/features/templates.md#editing-templates-template-authors) en sélectionnant **Modifier le modèle** dans le menu [Informations sur la page](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information).

Vous pouvez déterminer facilement le modèle sur lequel la page est basée en sélectionnant cette dernière dans la vue [Colonnes](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view) ou [Liste](/help/sites-cloud/authoring/getting-started/basic-handling.md#list-view).

## Statut de la Live Copy {#live-copy-status}

Le [mode de la page du statut de la Live Copy](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) vous donne une vue d’ensemble rapide du statut de la Live Copy et des composants qui sont ou non hérités :

* Bordure verte : hérité
* Bordure rose : héritage annulé

Par exemple :

![Exemple d’affichage de l’état de Live Copy](/help/sites-cloud/authoring/assets/editing-live-copy-status.png)

## Ajout d’annotations {#adding-annotations}

Les [Annotations](/help/sites-cloud/authoring/fundamentals/annotations.md) permettent aux réviseurs et aux autres créateurs de fournir des commentaires sur votre contenu. Elles sont souvent utilisées à des fins de révision et de validation.

## Aperçu des pages {#previewing-pages}

Deux options sont disponibles pour prévisualiser une page :

* [Mode Aperçu](#preview-mode) : aperçu rapide et statique
* [Afficher comme publié](#view-as-published) : aperçu complet qui ouvre la page dans un nouvel onglet

>[!TIP]
>
>* Les liens dans le contenu sont visibles, mais ne sont pas accessibles en mode d’édition.
>* Si vous souhaitez naviguer à l’aide des liens, utilisez l’une des options d’aperçu.
>* Utilisez le [raccourci clavier](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) `Ctrl-Shift-M` pour basculer entre le mode Aperçu et le dernier mode sélectionné.

>[!NOTE]
>
>Le cookie de mode WCM est défini pour les deux options d’aperçu.

### Mode Aperçu {#preview-mode}

Lorsque vous modifiez du contenu, vous pouvez prévisualiser la page à l’aide du [mode](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) Aperçu. Ce mode :

* Masque les différents mécanismes de modification pour vous donner un aperçu rapide de l’apparence de la page publiée.
* Permet d’utiliser des liens pour naviguer.
* **N’actualise pas** le contenu de la page.

Lors de la création, le mode Aperçu est disponible à l’aide de l’icône située en haut à droite de l’éditeur de page :

![Bouton Aperçu](/help/sites-cloud/authoring/assets/preview.png)

### Afficher comme publié(e) {#view-as-published}

L’option **Afficher comme publié(e)** est disponible à partir du menu [Informations sur la page](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information). La page s’ouvre alors dans un nouvel onglet, actualise le contenu et affiche la page telle qu’elle apparaîtra dans l’environnement de publication.

## Verrouillage d’une page  {#locking-a-page}

AEM vous permet de verrouiller une page, de sorte que personne d’autre ne puisse en modifier le contenu. Cette option est pratique lorsque vous souhaitez réaliser un nombre important de modifications sur une page unique ou que vous souhaitez geler le contenu d’une page pendant un certain temps.

Une page peut être verrouillée à partir de :

* La console **Sites**

   1. Sélectionnez la page en [mode de sélection](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
   1. Sélectionnez l’icône de verrou.

      ![Bouton Verrouiller](/help/sites-cloud/authoring/assets/lock.png)

* **Éditeur de page**

   1. Sélectionnez l’icône **Informations sur la page** pour ouvrir le menu.
   1. Sélectionnez l’option **Verrouiller la page**.

Une fois la page verrouillée, les informations d’affichage de la console sont mises à jour et, lors de la modification, le symbole d’un verrou s’affiche dans la barre d’outils.

![Exemple de page verrouillée](/help/sites-cloud/authoring/assets/editing-locked-page.png)

>[!CAUTION]
>
>Le verrouillage d’une page peut être réalisé lorsque vous empruntez l’identité d’un utilisateur. Cependant, une page verrouillée de cette manière peut uniquement être déverrouillée (par les clients) avec l’utilisateur ou l’utilisatrice dont l’identité a été empruntée.
>
>Les pages ne peuvent pas être déverrouillées en empruntant l’identité de l’utilisateur ou de l’utilisatrice qui les a verrouillées.
>
>Si l’utilisateur ou l’utilisatrice qui a verrouillé la page n’est pas disponible pour la déverrouiller, contactez le service clientèle afin d’évaluer les options de suppression du verrouillage.

## Déverrouillage d’une page {#unlocking-a-page}

Le déverrouillage d’une page est une procédure très similaire au [verrouillage de la page](#locking-a-page) : une fois la page verrouillée, les options de verrouillage sont remplacées par des actions de déverrouillage.

Dans le menu Informations sur la page, **Déverrouiller** est répertorié comme une option et l’icône Verrouiller dans la console Sites est remplacée par l’icône **Déverrouiller**.

![Bouton Déverrouiller](/help/sites-cloud/authoring/assets/unlock.png)

>[!CAUTION]
>
>Le verrouillage d’une page peut être réalisé lorsque vous empruntez l’identité d’un utilisateur. Cependant, une page verrouillée de cette manière peut ensuite uniquement être déverrouillée (par les clients) avec l’utilisateur ou l’utilisatrice dont l’identité a été empruntée.
>
>Les pages ne peuvent pas être déverrouillées en empruntant l’identité de l’utilisateur ou de l’utilisatrice qui les a verrouillées.
>
>Si l’utilisateur ou l’utilisatrice qui a verrouillé la page n’est pas disponible pour la déverrouiller, contactez le service clientèle afin d’évaluer les options de suppression du verrouillage.

<!--
>[!CAUTION]
>
>Locking a page can be performed when impersonating a user. However a page locked in this way can only then be unlocked by the user who was impersonated, or by a user with admin rights (a member of AEM Administrator IMS profile).
>
>Pages cannot be unlocked by impersonating the user who locked the page.
-->

<!--
>Locking a page can be performed when [impersonating a user](/help/sites-administering/security.md#impersonating-another-user). However a page locked in this way can only then be unlocked by the user who was impersonated or by the admin user.
-->

## Annulation et rétablissement des modifications de page {#undoing-and-redoing-page-edits}

Les icônes suivantes permettent d’annuler ou de rétablir une opération. Celles-ci s’affichent dans la barre d’outils le cas échéant :

![Boutons Annuler et Rétablir](/help/sites-cloud/authoring/assets/redo.png)

>[!TIP]
>
>* Le [raccourci clavier](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) `Ctrl-Z` est également disponible pour annuler les actions d’édition de la page.
>* Le raccourci clavier `Ctrl-Y` est également disponible pour annuler les actions d’édition de la page.

>[!NOTE]
>
>Consultez [Annulation et rétablissement des modifications de page : la théorie](#undoing-and-redoing-page-edits-the-theory) pour en savoir plus sur ce qu’il est possible de faire lorsque vous annulez ou rétablissez des modifications de page.

## Annulation et rétablissement des modifications de page : la théorie {#undoing-and-redoing-page-edits-the-theory}

AEM stocke un historique des actions que vous réalisez, ainsi que la séquence selon laquelle vous les réalisez, de sorte que vous puissiez annuler plusieurs actions dans l’ordre dans lequel vous les avez réalisées. Vous pouvez également les rétablir pour appliquer à nouveau une ou plusieurs de ces actions.

Si un élément de la page de contenu est sélectionné (un composant de texte, par exemple), les commandes Annuler et Rétablir s’appliquent à celui-ci.

Le comportement des commandes Annuler et Rétablir est similaire à celui des autres logiciels. Utilisez ces commandes pour restaurer l’état récent de votre page web lorsque vous prenez des décisions sur le contenu. Par exemple, si vous repositionnez un paragraphe de texte sur la page, vous pouvez utiliser la commande Annuler pour le remettre à son emplacement initial. Si vous décidez alors que la position précédente était meilleure, utilisez la commande Rétablir pour « annuler l’annulation ».

Par exemple, vous pouvez effectuer les actions suivantes :

* Rétablir les actions tant que vous n’avez pas effectué de modification de page depuis que vous avez utilisé l’option Annuler.
* Annuler un maximum de 20 actions de modification (paramètre par défaut).
* Utilisez également les [raccourcis clavier](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) pour annuler et rétablir.

Vous pouvez utiliser les options Annuler et Rétablir pour les types de modifications de page suivants :

* Ajout, modification, suppression et déplacement de paragraphes
* Modification sur place du contenu des paragraphes
* Copie, découpe et collage d’éléments dans une page

>[!NOTE]
>
>* Des autorisations spéciales sont nécessaires pour annuler et rétablir des modifications affectant des fichiers et des images.
>* L’historique des modifications apportées aux fichiers et aux images dure au moins dix heures. Au-delà de cette période, l’annulation des modifications n’est toutefois pas garantie. Votre administrateur ou administratrice peut modifier la durée par défaut de dix heures.
>* L’administrateur système peut configurer différents aspects des fonctions Annuler/Rétablir en fonction des exigences de votre instance.
<!--* Your system administrator can [configure various aspects of the Undo/Redo features](/help/sites-administering/config-undo.md) according to the requirements for your instance.-->
