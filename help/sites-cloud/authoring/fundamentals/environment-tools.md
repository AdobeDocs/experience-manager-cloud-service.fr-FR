---
title: Environnement et outils de création
description: L’environnement de création d’AEM comprend divers mécanismes permettant d’organiser et de modifier votre contenu.
exl-id: cc3bd4cf-93bd-429d-9a2a-4a02a7b42f7c
source-git-commit: 1a49bcd5b76e6a3b0d5a3168cef445101dc8d149
workflow-type: tm+mt
source-wordcount: '2161'
ht-degree: 86%

---


# Environnement et outils de création {#authoring-the-environment-and-tools}

L’environnement de création d’AEM comprend divers mécanismes permettant d’organiser et de modifier votre contenu. Les outils fournis sont accessibles dans plusieurs consoles et éditeurs de page.

{{edge-delivery-authoring}}

## Gestion de votre site {#managing-your-site}

La variable **Sites** La console vous permet de parcourir et de gérer votre site web à l’aide de la barre d’en-tête, de la barre d’outils, des icônes d’action (applicables à la ressource sélectionnée), des chemins de navigation et, lorsqu’ils sont sélectionnés, des rails secondaires (par exemple, la chronologie et les références).

Par exemple, le mode Colonnes :

![Mode Colonnes](/help/sites-cloud/authoring/assets/column-view.png)

## Modification du contenu de la page {#editing-page-content}

Vous pouvez modifier une page à l’aide de l’éditeur de page. Par exemple :

`http://<host>:<port>/editor.html/content/wknd/en/sports/la-skateparks.html`

![Éditeur de page](/help/sites-cloud/authoring/assets/page-editor.png)

>[!NOTE]
>
>La première fois que vous ouvrez une page en vue de la modifier, une série de diapositives vous offre une présentation des fonctionnalités.
>
>Vous pouvez ignorer cette présentation ou la revoir à tout moment en la sélectionnant dans le menu **Informations sur la page**.

## Accès à l’Aide   {#accessing-help}

Lorsque vous modifiez une page, l’**Aide** est accessible depuis :

* le sélecteur [**Informations sur la page**](/help/sites-cloud/authoring/fundamentals/page-properties.md#page-properties) avec les diapositives de présentation qui s’affichent (comme lors de votre premier accès à l’éditeur) ;
* la boîte de dialogue [Configuration](/help/sites-cloud/authoring/fundamentals/editing-content.md#component-toolbar) pour des composants spécifiques (au moyen de l’icône ? dans la barre d’outils de la boîte de dialogue), qui affiche l’aide contextuelle.

D’autres [ressources d’aide sont accessibles depuis les consoles](/help/sites-cloud/authoring/getting-started/basic-handling.md#accessing-help).

## Explorateur de composants {#components-browser}

Les composants sont les blocs de création du contenu AEM. Vous placez plusieurs composants sur une page et configurez leurs options pour créer votre page de contenu avec AEM.

L’explorateur de composants présente tous les composants que vous pouvez utiliser sur la page active. Vous pouvez les faire glisser à l’emplacement approprié, puis les modifier pour ajouter votre contenu.

L’explorateur de composants est un onglet du panneau latéral (de même que l’[explorateur de ressources](#assets-browser) et l’[arborescence de contenu](#content-tree)). Pour ouvrir (ou fermer) le panneau latéral, utilisez l’icône en haut à gauche de la barre d’outils :

![Bascule du panneau latéral](/help/sites-cloud/authoring/assets/side-panel-toggle.png)

Lorsque vous ouvrez le panneau latéral, ce dernier glisse depuis le côté gauche (sélectionnez l’onglet **Ressources** si nécessaire). Une fois ouvert, vous pouvez parcourir tous les composants disponibles pour votre page.

L’aspect et la gestion de l’explorateur dépendent du type d’appareil utilisé :

* **Appareil mobile (par exemple, iPad)**

  L’explorateur de composants couvre entièrement la page en cours de modification.

  Pour ajouter un composant à votre page, maintenez appuyé le composant requis et déplacez-le vers la droite (l’explorateur de composants se ferme pour afficher à nouveau la page) où vous pouvez positionner le composant.

  ![Explorateur de composants sur mobile](/help/sites-cloud/authoring/assets/component-browser-mobile.png)

* **Poste de travail**

  L’explorateur de composants s’ouvre sur le côté gauche de la fenêtre.

  Pour ajouter un composant à votre page, cliquez sur le composant requis et faites-le glisser vers l’emplacement requis.

  ![Explorateur de composants sur bureau](/help/sites-cloud/authoring/assets/component-browser-desktop.png)

  Les composants sont représentés par les éléments suivants :

   * Nom du composant
   * Groupe de composants (en gris)
   * Icône ou abréviation
      * Les icônes des composants standard sont monochromes.
      * Les abréviations correspondent toujours aux deux premiers caractères du nom du composant.

  Dans la barre d’outils supérieure de l’explorateur de **composants**, vous pouvez effectuer les opérations suivantes :

   * Filtrer les composants par nom
   * Restreindre l’affichage à un groupe spécifique à l’aide de la liste déroulante.

  Pour obtenir une description plus détaillée du composant, vous pouvez sélectionner l’icône d’informations en regard du composant dans la variable **Composants** navigateur (le cas échéant). Par exemple, pour le **fragment de contenu** :

  ![Informations de l’explorateur de composants](/help/sites-cloud/authoring/assets/component-browser-information.png)

  Pour plus d’informations sur les composants disponibles, voir [Console Composants](/help/sites-cloud/authoring/features/components-console.md).

>[!NOTE]
>
>Un appareil mobile est détecté lorsque la largeur est inférieure à 1 024 px. Cela peut également être le cas pour une petite fenêtre de bureau.

## Explorateur de ressources {#assets-browser}

L’explorateur de ressources présente toutes les [ressources](/help/assets/overview.md) que vous pouvez utiliser directement sur la page active.

L’explorateur de ressources est un onglet du panneau latéral (de même que l’[explorateur de composants](#components-browser) et l’[arborescence de contenu](#content-tree)). Pour ouvrir ou fermer le panneau latéral, utilisez l’icône en haut à gauche de la barre d’outils :

![Bascule du panneau latéral](/help/sites-cloud/authoring/assets/side-panel-toggle.png)

Lorsque vous ouvrez le panneau latéral, il s’ouvre en glissant depuis le côté gauche. Sélectionnez l’onglet **Ressources** si nécessaire.

![Bouton de l’explorateur de ressources](/help/sites-cloud/authoring/assets/assets-browser-button.png)

Lorsque l’explorateur de ressources est ouvert, vous pouvez parcourir toutes les ressources disponibles pour votre page. Le défilement infini permet de développer la liste si nécessaire.

![Explorateur de ressources](/help/sites-cloud/authoring/assets/assets-browser.png)

Pour ajouter une ressource à votre page, sélectionnez-la et faites-la glisser jusqu’à l’emplacement souhaité. Il peut s’agir des éléments suivants :

* d’un composant existant du type approprié.
   * Par exemple, vous pouvez faire glisser une ressource de type image sur un composant Image ;
* d’un [espace réservé](/help/sites-cloud/authoring/fundamentals/editing-content.md#component-placeholder) dans le système de paragraphes où créer un composant du type approprié :
   * Par exemple, vous pouvez faire glisser une ressource de type image sur le système de paragraphes afin de créer un composant Image.

>[!NOTE]
>
>Cette option est disponible pour des ressources et des types de composants spécifiques. Voir [Insertion d’un composant à l’aide de l’explorateur de ressources](/help/sites-cloud/authoring/fundamentals/editing-content.md#inserting-a-component-using-the-assets-browser) pour plus d’informations.

Dans la barre d’outils supérieure de l’explorateur de ressources, vous pouvez filtrer les ressources en procédant comme suit :

* Nom
* Chemin
* Type de ressource tel que les images, les vidéos, les documents, les paragraphes, les fragments de contenu et les fragments d’expérience
* Caractéristiques des ressources, telles que l’orientation et le style
   * Disponible uniquement pour certains types de ressources

L’aspect et la gestion de l’explorateur dépendent du type d’appareil utilisé :

* **Appareil mobile**

  L’explorateur de ressources couvre entièrement la page en cours de modification.

  Pour ajouter une ressource à votre page, maintenez appuyée la ressource requise, puis déplacez-la vers la droite : l’explorateur de ressources se ferme pour afficher à nouveau la page, où vous pouvez ajouter la ressource au composant requis.

  ![Explorateur de ressources sur mobile](/help/sites-cloud/authoring/assets/assets-browser-mobile.png)

* **Poste de travail**

  L’explorateur de ressources s’ouvre sur le côté gauche de la fenêtre.

  Pour ajouter une ressource à votre page, cliquez sur la ressource requise et faites-la glisser vers le composant ou l’emplacement requis.

  ![Explorateur de ressources sur bureau](/help/sites-cloud/authoring/assets/assets-browser-desktop.png)

>[!NOTE]
>
>Un appareil mobile est détecté si la largeur est inférieure à 1 024 px. C’est également le cas pour les petites fenêtres sur les ordinateurs de bureau.

Si vous devez modifier rapidement une ressource, vous pouvez lancer [l’éditeur de ressources](/help/assets/manage-digital-assets.md) directement depuis l’explorateur de ressources en cliquant sur l’icône Modifier affichée en regard du nom de la ressource.

![Bouton Modifier la ressource](/help/sites-cloud/authoring/assets/asset-edit-button.png)

## Arborescence de contenu {#content-tree}

La variable **Arborescence de contenu** donne un aperçu de tous les composants de la page dans une hiérarchie afin que vous puissiez voir en un coup d’oeil comment la page est composée.

L’arborescence de contenu est un onglet du panneau latéral (ainsi que l’explorateur de composants et de ressources). Pour ouvrir (ou fermer) le panneau latéral, utilisez l’icône en haut à gauche de la barre d’outils :

![Bouton Arborescence de contenu](/help/sites-cloud/authoring/assets/content-tree-button.png)

Lorsque vous ouvrez le panneau latéral, il s’ouvre en glissant depuis le côté gauche. Sélectionnez l’onglet **Arborescence de contenu** si nécessaire. Une fois ouvert, vous pouvez voir une représentation en arborescence de votre page ou modèle. Il est ainsi plus simple de comprendre comment son contenu est structuré de manière hiérarchique. En outre, sur une page complexe, il est plus facile de passer d’un composant à l’autre de la page.

![Arborescence de contenu](/help/sites-cloud/authoring/assets/content-tree-editor.png)

Étant donné qu’une page est souvent composée de nombreux composants du même type, l’arborescence des composants affiche un texte descriptif (en gris) après le nom du type de composant (en noir). Le texte descriptif provient des propriétés courantes du composant, telles que le titre ou le texte.

Les types de composants sont affichés dans la langue de l’utilisateur ou de l’utilisatrice, tandis que le texte descriptif du composant dépend de la langue de la page.

Cliquez sur le chevron en regard d’un composant pour réduire ou développer ce niveau.

![Extension du chevron de l’arborescence de contenu](/help/sites-cloud/authoring/assets/content-tree-chevron.png)

Cliquez sur le composant pour le mettre en surbrillance dans l’éditeur de page. Les actions disponibles dépendent du statut de la page :

* Par exemple, une page de base :

  ![Arborescence de contenu mise en surbrillance](/help/sites-cloud/authoring/assets/content-tree-highlighted.png)

  Les composants d’une page de base auront les options habituelles.

  Si le composant sur lequel vous cliquez est éditable, une icône de clé à molette s’affiche à droite du nom. Cliquez sur cette icône pour ouvrir la boîte de dialogue de modification du composant.

  ![Bouton Modifier l’arborescence de contenu](/help/sites-cloud/authoring/assets/content-tree-edit.png)

* Une page faisant partie d’une page [Live Copy](/help/sites-cloud/administering/msm/overview.md), où les composants sont hérités d’une autre page.

>[!NOTE]
>
>L’arborescence de contenu n’est pas disponible si vous modifiez une page sur un appareil mobile (si la largeur de l’explorateur est inférieure à 1 024 px).

## Fragments – Explorateur de contenu associé {#fragments-associated-content-browser}

Si votre page contient des fragments de contenu, vous aurez dans ce cas également accès à l’[explorateur de contenu associé](/help/sites-cloud/authoring/fundamentals/content-fragments.md#using-associated-content).

## Références {#references}

Les **références** affichent toutes les connexions avec la page sélectionnée :

* Plans directeurs
* Lancements
* Live Copies
* Copies de langue
* Liens entrants
* Utilisation du composant de référence : contenu emprunté et prêté

Ouvrez la console appropriée, puis accédez à la ressource requise et ouvrez **Références** à l’aide de :

![Option Références](/help/sites-cloud/authoring/assets/references.png)

[Sélectionnez la ressource qui vous intéresse](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) pour afficher la liste des types de références correspondant à cette ressource :

![Détails des références](/help/sites-cloud/authoring/assets/references-detail.png)

Sélectionnez le type de référence approprié pour en savoir plus. Dans certains cas, d’autres actions sont disponibles lorsque vous sélectionnez une référence particulière, notamment :

* **Liens entrants**, fournit une liste des pages qui font référence à la page, ainsi qu’un accès direct à **Modifier** l’une de ces pages lorsque vous sélectionnez un lien spécifique.

   * Cela peut uniquement afficher des liens statiques, et non des liens générés dynamiquement, par exemple, à partir du composant Liste .

* Les instances du contenu emprunté et prêté à l’aide du composant **Référence** vous permettent de naviguer jusqu’à la page de référence.
* [Lancements](/help/sites-cloud/authoring/launches/overview.md) donne accès aux lancements associés.
* [Live Copies](/help/sites-cloud/administering/msm/overview.md) affiche les chemins d’accès à toutes les Live Copies basées sur la ressource sélectionnée.
* Le [plan directeur](/help/sites-cloud/administering/msm/best-practices.md) fournit des détails et la possibilité de diverses actions.
* [Copies de langue](/help/sites-cloud/administering/translation/managing-projects.md#creating-translation-projects-using-the-references-panel), fournit des détails et diverses actions

## Événements – Chronologie {#events-timeline}

Pour les ressources appropriées (par exemple, des pages de la console **Sites** ou des ressources de la console **Ressources**), utilisez la [chronologie afin d’afficher l’activité récente d’un élément sélectionné](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline).

Ouvrez la console appropriée, puis accédez à la ressource requise et ouvrez la **Chronologie** à l’aide de :

![Option Chronologie](/help/sites-cloud/authoring/assets/timeline.png)

[Sélectionnez la ressource requise](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources), puis **Afficher tout** ou **Activités** afin de répertorier les activités récentes pour les ressources sélectionnées :

![Détails de la chronologie](/help/sites-cloud/authoring/assets/timeline-detail.png)

## Informations sur la page {#page-information}

L’icône Informations sur la page (icône d’égaliseur) ouvre un menu qui fournit également des détails sur la dernière modification et la dernière publication. Selon les caractéristiques de la page, de son site et de votre instance, d’autres options peuvent être disponibles :

![Option Informations sur la page](/help/sites-cloud/authoring/assets/page-information.png)

* [Ouvrir les propriétés](/help/sites-cloud/authoring/fundamentals/page-properties.md)
* [Déployer la page](/help/sites-cloud/administering/msm/overview.md#msm-from-the-ui)
* [Démarrer le processus](/help/sites-cloud/authoring/workflows/applying.md#starting-a-workflow-from-the-page-editor)
* [Verrouillage de la page](/help/sites-cloud/authoring/fundamentals/editing-content.md#locking-a-page)
* [Publier la page](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#publishing-pages-1)
* [Dépublication de la page](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#unpublishing-pages)
* [Modifier le modèle](/help/sites-cloud/authoring/features/templates.md)
* [Afficher comme publié(e)](/help/sites-cloud/authoring/fundamentals/editing-content.md#view-as-published)
* [Afficher en administrateur](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)
* [Aide](/help/sites-cloud/authoring/getting-started/basic-handling.md#accessing-help)
* [Convertir le lancement](/help/sites-cloud/authoring/launches/promoting.md) (uniquement si la page correspond à un lancement)

Le menu **Informations sur la page** peut en outre donner accès à des analyses et recommandations, le cas échéant.

## Modes de page {#page-modes}

Plusieurs modes sont possibles lors de la modification d’une page, ce qui permet d’effectuer différentes actions :

* [Modifier](/help/sites-cloud/authoring/fundamentals/editing-content.md) : mode à utiliser lors de la modification du contenu de la page.
* [Disposition](/help/sites-cloud/authoring/features/responsive-layout.md) - vous permet de créer et de modifier votre mise en page réactive en fonction de l’appareil (si la page est basée sur un conteneur de mises en page).
* [Ciblage](/help/sites-cloud/authoring/personalization/targeted-content.md) : accroît la pertinence du contenu grâce au ciblage et à la mesure sur tous les canaux.
* [Distorsion du temps](/help/sites-cloud/authoring/features/page-versions.md#timewarp) : permet d’afficher le statut d’une page à un moment donné.
* [Statut de la Live Copy](/help/sites-cloud/authoring/fundamentals/editing-content.md#live-copy-status) : donne un aperçu rapide du statut de la Live Copy et des composants qui sont ou non hérités.
* [Mode Développeur](/help/implementing/developing/tools/developer-mode.md)
* [Aperçu](/help/sites-cloud/authoring/fundamentals/editing-content.md#previewing-pages) : permet d’afficher la page comme elle est présentée dans l’environnement de publication ou de naviguer au moyen des liens figurant dans le contenu.
* [Annoter](/help/sites-cloud/authoring/fundamentals/annotations.md) : permet d’ajouter ou d’afficher des annotations sur la page.

Vous pouvez accéder à ces modes en cliquant sur les icônes dans le coin supérieur droit ; l’icône active se changera alors pour refléter le mode sélectionné :

![Modes de page](/help/sites-cloud/authoring/assets/page-modes.png)

>[!NOTE]
>
>* Selon les caractéristiques de la page, certains modes peuvent ne pas être disponibles.
>* L’accès à certains modes nécessite les autorisations/privilèges appropriés.
>* Le mode de développement n’est pas disponible sur les appareils mobiles en raison de restrictions d’espace.
>* Il existe une [raccourci clavier](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) ( `Ctrl-Shift-M`) pour basculer entre les **Aperçu** et le mode actuellement sélectionné (par exemple : **Modifier**, **Disposition**, etc.).
>

## Sélection du chemin d’accès {#path-selection}

Lors de la création, il est souvent nécessaire de sélectionner une autre ressource, par exemple lors de la définition d’un lien vers une autre page ou ressource ou de la sélection d’une image. Pour sélectionner facilement un chemin d’accès, les [Champs de chemin d’accès](#path-fields) permettent la saisie automatique et l’[explorateur de chemins d’accès](#path-browser) permet une sélection plus robuste.

### Champs de chemin d’accès {#path-fields}

L’exemple utilisé ici pour illustrer est le composant d’image. Pour plus d’informations sur l’utilisation et la modification des composants, voir [Composants pour la création de pages](/help/sites-cloud/authoring/fundamentals/components.md).

Les champs de chemin d’accès intègrent désormais une fonctionnalité de saisie automatique et d’anticipation pour faciliter la localisation des ressources.

Si vous cliquez sur le bouton **Ouvrir la boîte de dialogue de sélection** dans le champ de chemin d’accès, la boîte de dialogue [Explorateur de chemins d’accès](#path-browser) s’ouvre pour vous permettre d’accéder à des options de sélection plus détaillées.

![Bouton Ouvrir la boîte de dialogue de sélection](/help/sites-cloud/authoring/assets/open-selection-dialog-button.png)

Vous pouvez également effectuer une saisie dans le champ de chemin d’accès. AEM vous proposera alors les chemins d’accès correspondants au fil de la saisie.

![Bouton Ouvrir la boîte de dialogue de sélection](/help/sites-cloud/authoring/assets/path-selection-completion.png)

### Explorateur de chemins d’accès {#path-browser}

L’explorateur de chemins d’accès est organisé de la même façon que le [mode Colonnes](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view) de la console Sites afin de permettre une sélection plus détaillée des ressources.

![Explorateur de chemins d’accès](/help/sites-cloud/authoring/assets/path-browser.png)

* Une fois une ressource sélectionnée, la variable **Sélectionner** dans l’angle supérieur droit de la boîte de dialogue devient actif. Sélectionnez cette option pour confirmer la sélection ou **Annuler** pour abandonner.
* Si le contexte permet la sélection de plusieurs ressources, la sélection d’une ressource active également le bouton **Sélectionner**, mais ajoute également le nombre de ressources sélectionnées en haut à droite de la fenêtre. Cliquez sur le **X** en regard du nombre pour tout désélectionner.
* Lorsque vous parcourez l’arborescence, votre emplacement est reflété dans le chemin de navigation de la boîte de dialogue. Ces chemins de navigation peuvent également être utilisés pour accéder rapidement à la hiérarchie des ressources.
* Vous pouvez à tout moment utiliser le champ de recherche situé en haut de la boîte de dialogue. Cliquez sur le **X** dans le champ de recherche pour effacer la recherche.
* Pour affiner votre recherche, vous pouvez afficher les options de filtre et filtrer vos résultats en fonction du chemin d’accès.

  ![Option Filtres](/help/sites-cloud/authoring/assets/filters-option.png)

## Raccourcis clavier {#keyboard-shortcuts}

Divers [raccourcis clavier](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) sont disponibles.
