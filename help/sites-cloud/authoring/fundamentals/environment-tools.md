---
title: Environnement et outils de création
description: L’environnement de création d’AEM comprend divers mécanismes permettant d’organiser et de modifier votre contenu.
translation-type: ht
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Environnement et outils de création {#authoring-the-environment-and-tools}

L’environnement de création d’AEM comprend divers mécanismes permettant d’organiser et de modifier votre contenu. Les outils proposés sont accessibles dans les divers éditeurs de pages et consoles.

## Gestion de votre site {#managing-your-site}

Dans la console **Sites**, vous pouvez parcourir et gérer votre site web en utilisant la barre d’en-tête, la barre d’outils, les icônes d’action (applicables à la ressource sélectionnée), les chemins de navigation et, s’ils sont sélectionnés, les rails secondaires (par exemple référence et chronologie).

Par exemple, le mode Colonnes :

![Mode Colonnes](/help/sites-cloud/authoring/assets/column-view.png)

## Modification du contenu de la page {#editing-page-content}

Vous pouvez modifier une page dans l’éditeur de page. Par exemple :

`http://<host>:<port>/editor.html/content/wknd/en/sports/la-skateparks.html`

![Éditeur de page](/help/sites-cloud/authoring/assets/page-editor.png)

>[!NOTE]
>
>La première fois que vous ouvrez une page pour la modifier, les différentes fonctions vous sont présentées dans une série de diapositives.
>
>Vous pouvez ignorer cette présentation ou la revoir à tout moment en la sélectionnant dans le menu **Informations sur la page**.

## Accès à l’Aide    {#accessing-help}

Lorsque vous modifiez une page, l’**Aide** est accessible depuis :

* le sélecteur [**d’informations sur la page **](/help/sites-cloud/authoring/fundamentals/page-properties.md#page-properties)avec les diapositives de présentation qui s’affichent (comme lors de votre premier accès à l’éditeur) ;
* la boîte de dialogue [Configuration](/help/sites-cloud/authoring/fundamentals/editing-content.md#component-toolbar) pour des composants spécifiques (au moyen de l’icône ? dans la barre d’outils de la boîte de dialogue), qui affiche l’aide contextuelle.

D’autres [ressources d’aide sont accessibles depuis les consoles](/help/sites-cloud/authoring/getting-started/basic-handling.md#accessing-help).

## Explorateur de composants    {#components-browser}

Les composants sont les blocs de création du contenu AEM. Vous placez plusieurs composants sur une page et configurez leurs options afin de créer votre page de contenu avec AEM.

L’explorateur de composants présente tous les composants que vous pouvez utiliser sur la page active. Faites-les glisser à l’emplacement de votre choix, puis modifiez-les pour ajouter du contenu.

L’explorateur de composants est un onglet du panneau latéral (de même que l’[explorateur de ressources](#assets-browser) et l’[arborescence de contenu](#content-tree)). Pour ouvrir (ou fermer) le panneau latéral, utilisez l’icône en haut à gauche de la barre d’outils :

![Bascule du panneau latéral](/help/sites-cloud/authoring/assets/side-panel-toggle.png)

Lorsque vous ouvrez le panneau latéral, il s’ouvre en glissant depuis le côté gauche (sélectionnez l’onglet **Composants** si nécessaire). De là, vous pouvez parcourir tous les composants disponibles pour votre page.

L’aspect et la gestion de l’explorateur dépendent du type d’appareil utilisé :

* **Appareils mobiles (p. ex. iPad)**

   L’explorateur de composants couvre entièrement la page en cours de modification.

   Pour ajouter un composant à votre page, maintenez appuyé le composant requis et déplacez-le vers la droite (l’explorateur de composants se ferme pour afficher de nouveau la page) jusqu’à l’emplacement où vous souhaitez le placer.

   ![Explorateur de composants sur mobile](/help/sites-cloud/authoring/assets/component-browser-mobile.png)

* **Poste de travail**

   L’explorateur de composants s’ouvre sur le côté gauche de la fenêtre.

   Pour ajouter un composant à votre page, cliquez sur le composant souhaité et faites-le glisser vers l’emplacement requis.

   ![Explorateur de composants sur bureau](/help/sites-cloud/authoring/assets/component-browser-desktop.png)

   Les composants sont représentés par

   * Nom du composant
   * Groupe de composants (en gris)
   * Icône ou abréviation
      * Les icônes de composants standard sont monochromes.
      * Les abréviations correspondent toujours aux deux premiers caractères du nom du composant.
   Dans la barre d’outils supérieure de l’explorateur de **composants**, vous pouvez effectuer les opérations suivantes :

   * Filtrer les composants par nom
   * Restreindre l’affichage à un groupe spécifique à l’aide de la liste déroulante
   Pour une description plus détaillée du composant, vous pouvez cliquer ou appuyer sur l’icône d’informations affichée en regard du composant dans l’Explorateur de **composants** (si disponible). Par exemple, pour le **fragment de contenu** :

   ![Informations de l’explorateur de composants](/help/sites-cloud/authoring/assets/component-browser-information.png)

   Pour plus d’informations sur les composants disponibles, voir [Console Composants](/help/sites-cloud/authoring/features/components-console.md).

>[!NOTE]
>
>Un appareil mobile est détecté si sa largeur est inférieure à 1 024 px. C’est également le cas pour les petites fenêtres sur les ordinateurs de bureau.

## Explorateur de ressources {#assets-browser}

L’explorateur de ressources présente toutes les ressources que vous pouvez utiliser directement sur la page active. <!--The assets browser shows all [assets](/help/assets/home.md) that are available for direct use on your current page.-->

L’explorateur de ressources est un onglet du panneau latéral (de même que l’[explorateur de composants](#components-browser) et l’[arborescence de contenu](#content-tree)). Pour ouvrir ou fermer le panneau latéral, utilisez l’icône en haut à gauche de la barre d’outils :

![Bascule du panneau latéral](/help/sites-cloud/authoring/assets/side-panel-toggle.png)

Lorsque vous ouvrez le panneau latéral, il s’ouvre en glissant depuis le côté gauche. Sélectionnez l’onglet **Ressources** si nécessaire.

![Bouton de l’explorateur de ressources](/help/sites-cloud/authoring/assets/assets-browser-button.png)

Une fois l’explorateur de ressources ouvert, vous pouvez parcourir toutes les ressources disponibles pour votre page. Le défilement infini permet de développer la liste quand cela s’avère nécessaire.

![Explorateur de ressources](/help/sites-cloud/authoring/assets/assets-browser.png)

Pour ajouter une ressource à votre page, sélectionnez-la et faites-la glisser jusqu’à l’emplacement requis. Il peut s’agir :

* d’un composant existant du type approprié.
   * Par exemple, vous pouvez faire glisser une ressource de type image sur un composant Image ;
* d’un [emplacement réservé](/help/sites-cloud/authoring/fundamentals/editing-content.md#component-placeholder) dans le système de paragraphes où créer un composant du type approprié.
   * Par exemple, vous pouvez faire glisser une ressource de type image sur le système de paragraphes afin de créer un composant Image.

>[!NOTE]
>
>Vous pouvez agir ainsi pour des ressources et des types de composants spécifiques. Voir [Insertion d’un composant à l’aide de l’explorateur de ressources](/help/sites-cloud/authoring/fundamentals/editing-content.md#inserting-a-component-using-the-assets-browser) pour en savoir plus.

Dans la barre d’outils supérieure de l’explorateur de ressources, vous pouvez filtrer les ressources par :

* Nom
* Chemin
* Type de ressource tel que les images, les vidéos, les documents, les paragraphes, les fragments de contenu et les fragments d’expérience
* Caractéristiques des ressources, telles que l’orientation et le style
   * Disponible uniquement pour certains types de ressources

L’aspect et la gestion de l’explorateur dépendent du type d’appareil utilisé :

* **Appareil mobile**

   L’explorateur de ressources couvre entièrement la page en cours de modification.

   Pour ajouter une ressource à votre page, maintenez appuyée la ressource requise et déplacez-la vers la droite (l’explorateur de ressources se ferme pour afficher de nouveau la page) pour l’ajouter au composant requis.

   ![Explorateur de ressources sur mobile](/help/sites-cloud/authoring/assets/assets-browser-mobile.png)

* **Poste de travail**

   L’explorateur de ressources s’ouvre sur le côté gauche de la fenêtre.

   Pour ajouter une ressource à votre page, cliquez dessus et faites-la glisser sur le composant ou l’emplacement requis.

   ![Explorateur de ressources sur bureau](/help/sites-cloud/authoring/assets/assets-browser-desktop.png)

>[!NOTE]
>
>Un appareil mobile est détecté si la largeur est inférieure à 1 024 px. C’est également le cas pour les petites fenêtres sur les ordinateurs de bureau.

Si vous devez modifier rapidement une ressource, vous pouvez lancer l’éditeur de ressources directement depuis l’explorateur de ressources en cliquant sur l’icône Modifier affichée en regard du nom de la ressource. <!--If you need to quickly make a change to an asset, you can start the [asset editor](/help/assets/manage-digital-assets.md) directly from the asset browser by clicking the edit icon shown next to the asset's name.-->

![Bouton Modifier la ressource](/help/sites-cloud/authoring/assets/asset-edit-button.png)

## Arborescence de contenu    {#content-tree}

L’**arborescence de contenu** présente une vue d’ensemble des composants sur la page sous forme de structure hiérarchique pour que vous puissiez visualiser la composition de la page en un seul coup d’œil.

L’arborescence de contenu est un onglet du panneau latéral (de même que l’explorateur de composants et l’explorateur de ressources). Pour ouvrir (ou fermer) le panneau latéral, utilisez l’icône en haut à gauche de la barre d’outils :

![Bouton Arborescence de contenu](/help/sites-cloud/authoring/assets/content-tree-button.png)

Lorsque vous ouvrez le panneau latéral, il s’ouvre en glissant depuis le côté gauche. Sélectionnez l’onglet **Arborescence de contenu** si nécessaire. Vous pouvez alors voir une représentation de votre page ou modèle sous forme d’arborescence, qui vous permet de comprendre plus facilement la structure hiérarchique de son contenu. Sur une page complexe, elle vous permet en outre de passer plus facilement d’un composant à l’autre.

![Arborescence de contenu](/help/sites-cloud/authoring/assets/content-tree-editor.png)

Étant donné qu’une page est souvent composée de nombreux composants du même type, l’arborescence des composants affiche un texte descriptif (en gris) après le nom du type de composant (en noir). Le texte descriptif provient des propriétés communes du composant, telles que le titre ou le texte.

Les types de composants sont affichés dans la langue de l’utilisateur, tandis que le texte descriptif du composant dépend de la langue de la page.

Cliquez sur le chevron en regard d’un composant pour réduire ou développer ce niveau.

![Extension du chevron de l’arborescence de contenu](/help/sites-cloud/authoring/assets/content-tree-chevron.png)

Cliquez sur le composant pour mettre en surbrillance le composant dans l’éditeur de page. Les actions disponibles dépendent de l’état de la page :

* Par exemple, une page de base :

   ![Arborescence de contenu mise en surbrillance](/help/sites-cloud/authoring/assets/content-tree-highlighted.png)

   Les composants d’une page de base auront les options habituelles.

   Si le composant sur lequel vous cliquez dans l’arborescence est modifiable, une icône de clé s’affiche à droite du nom. Cliquez sur cette icône pour ouvrir directement la boîte de dialogue de modification de ce composant.

   ![Bouton Modifier l’arborescence de contenu](/help/sites-cloud/authoring/assets/content-tree-edit.png)

* Une page faisant partie d’une Live Copy, où les composants sont hérités d’une autre page, présente une sélection réduite d’options, y compris les options d’héritage. <!--A page that is part of a [livecopy](/help/sites-administering/msm.md), where components are inherited from another page:-->

>[!NOTE]
>
>L’arborescence de contenu n’est pas disponible si vous modifiez une page sur un appareil mobile (si la largeur de l’explorateur est inférieure à 1 024 px).

## Fragments – Explorateur de contenu associé {#fragments-associated-content-browser}

Si votre page contient des fragments de contenu, vous aurez dans ce cas également accès à l’[explorateur de contenu associé](/help/sites-cloud/authoring/fundamentals/content-fragments.md#using-associated-content).

## Références {#references}

**Références** signale toutes les connexions avec la page sélectionnée :

* Plans directeurs
* Lancements
* Live copies
* Copies de langue
* Liens entrants
* Utilisation du composant de référence : contenu emprunté et prêté

Ouvrez la console appropriée, puis accédez à la ressource requise et ouvrez **Références** à l’aide de :

![Option Références](/help/sites-cloud/authoring/assets/references.png)

[Sélectionnez la ressource qui vous intéresse](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) pour afficher la liste des types de références correspondant à cette ressource :

![Détails des références](/help/sites-cloud/authoring/assets/references-detail.png)

Sélectionnez le type de référence approprié pour en savoir plus. Dans certains cas, d’autres actions sont disponibles lorsque vous sélectionnez une référence particulière, notamment :

* **Liens entrants**, fournit la liste de pages qui font référence à cette page, ainsi qu’un lien direct vers l’option **Modifier** pour l’une de ces deux pages lorsque vous sélectionnez un lien spécifique.
* Les instances du contenu emprunté et prêté à l’aide du composant **Référence** vous permettent de naviguer jusqu’à la page de référence.
* [Lancements](/help/sites-cloud/authoring/launches/overview.md) donne accès aux lancements associés.
* Live Copies affiche les chemins d’accès à toutes les Live Copies basées sur la ressource sélectionnée. <!--[Live Copies](/help/sites-administering/msm.md) displays the paths of all live copies that are based on the selected resource.-->
* Plan directeur fournit des détails et diverses actions. <!--[Blueprint](/help/sites-administering/msm-best-practices.md), provides details and various actions-->
* Copies de langue fournit des détails et diverses actions. <!--[Languages Copies](/help/sites-administering/tc-manage.md#creating-translation-projects-using-the-references-panel), provides details and various actions-->

## Événements – Chronologie {#events-timeline}

Pour accéder aux ressources appropriées (par ex. des pages de la console **Sites** ou des ressources de la console **Ressources**), utilisez la [chronologie afin d’afficher l’activité récente d’un élément sélectionné](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline).

Ouvrez la console appropriée, puis accédez à la ressource requise et ouvrez la **Chronologie** à l’aide de :

![Option Chronologie](/help/sites-cloud/authoring/assets/timeline.png)

[Sélectionnez la ressource requise](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources), puis **Tout afficher** ou **Activités** afin de répertorier les activités récentes pour les ressources sélectionnées :

![Détails de la chronologie](/help/sites-cloud/authoring/assets/timeline-detail.png)

## Informations sur la page {#page-information}

L’icône Informations sur la page (icône d’égaliseur) ouvre un menu qui fournit également des détails sur la dernière modification et la dernière publication. Selon les caractéristiques de la page, de son site et de votre instance, d’autres options peuvent être disponibles :

![Option Informations sur la page](/help/sites-cloud/authoring/assets/page-information.png)

* [Ouvrir les propriétés](/help/sites-cloud/authoring/fundamentals/page-properties.md)
* Déployer la page <!--[Rollout Page](/help/sites-administering/msm.md#msm-from-the-ui)-->
* [Démarrer le workflow](/help/sites-cloud/authoring/workflows/applying.md#starting-a-workflow-from-the-page-editor)
* [Verrouiller la page](/help/sites-cloud/authoring/fundamentals/editing-content.md#locking-a-page)
* [Publier la page](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#publishing-pages-1)
* [Annuler la publication de la page](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#unpublishing-pages)
* [Modifier le modèle](/help/sites-cloud/authoring/features/templates.md)
* [Afficher comme publié(e)](/help/sites-cloud/authoring/fundamentals/editing-content.md#view-as-published)
* [Afficher en administrateur](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)
* [Aide](/help/sites-cloud/authoring/getting-started/basic-handling.md#accessing-help)
* [Convertir le lancement](/help/sites-cloud/authoring/launches/promoting.md) (uniquement si la page correspond à un lancement)

Le menu **Informations sur la page** peut en outre donner accès à des analyses et recommandations, le cas échéant.

## Modes de page    {#page-modes}

Lors de la modification d’une page, plusieurs modes permettent d’effectuer différentes actions :

* [Modifier](/help/sites-cloud/authoring/fundamentals/editing-content.md) : mode à utiliser lors de la modification du contenu de la page.
* [Mise en page](/help/sites-cloud/authoring/features/responsive-layout.md) : permet de créer et de modifier une mise en page réactive en fonction du type d’appareil utilisé (si la page est basée sur un conteneur de mises en page).
* [Ciblage](/help/sites-cloud/authoring/personalization/targeted-content.md) : optimise la pertinence du contenu grâce au ciblage et aux mesures à l’échelle de tous les canaux.
* [Timewarp](/help/sites-cloud/authoring/features/page-versions.md#timewarp) : permet d’afficher l’état d’une page à un moment donné.
* [État de Live Copy](/help/sites-cloud/authoring/fundamentals/editing-content.md#live-copy-status) : donne un aperçu rapide de l’état de la live copy et des composants qui sont ou non hérités.
* [Aperçu](/help/sites-cloud/authoring/fundamentals/editing-content.md#previewing-pages) : permet d’afficher la page comme elle sera présentée dans l’environnement de publication ou de naviguer au moyen des liens figurant dans le contenu.
* [Annoter](/help/sites-cloud/authoring/fundamentals/annotations.md) : permet d’ajouter ou d’afficher des annotations sur la page.

Vous pouvez accéder à ces modes en cliquant sur les icônes dans le coin supérieur droit ; l’icône active se changera alors pour refléter le mode sélectionné :

![Modes de page](/help/sites-cloud/authoring/assets/page-modes.png)

>[!NOTE]
>
>* Certains modes peuvent ne pas être disponibles en fonction des caractéristiques de la page.
>* L’accès à certains modes implique que vous disposiez des droits ou autorisations appropriés.
>* Le mode Développeur n’est pas accessible sur les appareils mobiles en raison de restrictions d’espace.
>* Utilisez le [raccourci clavier](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) (`Ctrl-Shift-M`) pour permuter entre l’**Aperçu** et le mode actuellement sélectionné (par ex. **Modifier**, **Mise en page**, etc.).
>



## Sélection du chemin d’accès {#path-selection}

Lors de la création, il est souvent nécessaire de sélectionner une autre ressource, par exemple pour définir un lien vers une autre page ou ressource ou sélectionner une image. Pour faciliter la sélection d’un chemin d’accès, les [champs de chemin d’accès](#path-fields) proposent la saisie automatique et [l’explorateur de chemins d’accès](#path-browser) permet une sélection plus efficace.

### Champs de chemin d’accès {#path-fields}

L’exemple utilisé ici à titre d’illustration est le composant Image. Pour plus d’informations sur l’utilisation et la modification des composants, voir [Composants de création de pages](/help/sites-cloud/authoring/fundamentals/components.md).

Les champs de chemin d’accès intègrent désormais une fonctionnalité de saisie automatique et d’anticipation pour faciliter la localisation des ressources.

Si vous cliquez sur le bouton **Ouvrir la boîte de dialogue de sélection** dans le champ de chemin d’accès, la boîte de dialogue [Explorateur de chemins d’accès](#path-browser) s’ouvre pour vous permettre d’accéder à des options de sélection plus détaillées.

![Bouton Ouvrir la boîte de dialogue de sélection](/help/sites-cloud/authoring/assets/open-selection-dialog-button.png)

Vous pouvez également effectuer une saisie dans le champ de chemin d’accès. AEM vous proposera alors les chemins d’accès correspondants au fil de la saisie.

![Bouton Ouvrir la boîte de dialogue de sélection](/help/sites-cloud/authoring/assets/path-selection-completion.png)

### Explorateur de chemins d’accès {#path-browser}

L’explorateur de chemins d’accès est organisé de la même façon que le [mode Colonnes](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view) de la console Sites afin de permettre une sélection plus détaillée des ressources.

![Explorateur de chemins d’accès](/help/sites-cloud/authoring/assets/path-browser.png)

* Lorsqu’une ressource est sélectionnée, le bouton **Sélectionner** situé en haut à droit de la boîte de dialogue devient actif. Cliquez ou appuyez dessus pour confirmer la sélection, ou sur **Annuler** pour annuler.
* Si le contexte permet la sélection de plusieurs ressources, la sélection d’une ressource active également le bouton **Sélectionner**, mais ajoute également le nombre de ressources sélectionnées en haut à droite de la fenêtre. Cliquez sur **X** à côté du nombre pour annuler la sélection de toutes les ressources sélectionnées.
* Lorsque vous parcourez l’arborescence, votre emplacement est reflété dans le chemin de navigation de la boîte de dialogue. Ces chemins de navigation peuvent être utilisés pour passer rapidement d’une ressource à une autre dans la hiérarchie des ressources.
* Vous pouvez à tout moment utiliser le champ de recherche situé en haut de la boîte de dialogue. Cliquez sur **X** dans le champ de recherche pour effacer la recherche.
* Pour affiner votre recherche, vous pouvez afficher les options de filtre et filtrer vos résultats en fonction du chemin d’accès.

   ![Option Filtres](/help/sites-cloud/authoring/assets/filters-option.png)

## Raccourcis clavier {#keyboard-shortcuts}

Divers [raccourcis clavier](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) sont disponibles.
