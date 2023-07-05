---
title: Manipulation de base
description: Familiarisez-vous avec la navigation dans AEM et l’utilisation des fonctionnalités de base.
exl-id: ae87a63a-c6d3-4220-ab3d-07a20b21b93b
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '2978'
ht-degree: 92%

---

# Manipulation de base {#basic-handling}

Ce document donne un aperçu des opérations de gestion de base dans l’environnement de création d’AEM. Il utilise la console **Sites** comme base.

>[!NOTE]
>
>* Certaines fonctionnalités ne sont pas disponibles dans toutes les consoles et d’autres peuvent être disponibles dans certaines consoles uniquement. Des informations spécifiques sur les consoles individuelles et leurs fonctionnalités associées sont traitées plus en détail sur d’autres pages.
>* Des raccourcis clavier sont disponibles dans toute l’application AEM, notamment lors de l’[utilisation des consoles](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) et de la [modification de pages](/help/sites-cloud/authoring/fundamentals/keyboard-shortcuts.md).

## Interface utilisateur pour écrans tactiles {#a-touch-enabled-ui}

L’interface utilisateur d’AEM est adaptée aux écrans tactiles. Les interfaces de ce type permettent d’interagir de manière tactile avec le logiciel en appuyant sur l’écran, en maintenant la pression du doigt ou en le faisant glisser. L’interface utilisateur d’AEM étant tactile, vous pouvez utiliser les mouvements des doigts sur vos appareils tactiles, tels que votre téléphone mobile ou votre tablette. Cependant, les actions de la souris sur un poste de travail traditionnel sont également disponibles, ce qui vous offre davantage de flexibilité pour créer votre contenu.

## Premiers pas {#first-steps}

Une fois connecté, vous accédez au [panneau de navigation](#navigation-panel). Sélectionnez l’une des options pour ouvrir la console correspondante.

![Panneau de navigation](/help/sites-cloud/authoring/assets/navigation.png)

La console **Sites** est utilisée dans ce document pour garantir une bonne compréhension de l’utilisation de base d’AEM. Cliquez ou appuyez sur **Sites** pour commencer.

## Navigation dans le produit {#product-navigation}

Lorsqu’une personne utilisatrice accède à une console pour la première fois, un tutoriel sur la navigation dans le produit en question s’affiche. Cliquez ou appuyez pour obtenir une vue d’ensemble de la gestion de base d’AEM.

![Tutoriel de navigation](/help/sites-cloud/authoring/assets/tutorial.png)

Cliquez ou appuyez sur **Suivant** pour accéder à la page suivante de l’aperçu. Cliquez ou appuyez sur **Fermer** ou à l’extérieur de la boîte de dialogue de l’aperçu pour la fermer.

Si vous ne désactivez pas l’option **Ne plus afficher ce message**, l’aperçu redémarrera la prochaine fois que vous accéderez à la console.

## Navigation globale {#global-navigation}

Pour passer d’une console à une autre, utilisez le panneau de navigation globale. Cela se déclenche sous la forme d’une liste déroulante plein écran lorsque vous cliquez ou appuyez sur le lien Adobe Experience Manager dans le coin supérieur gauche de l’écran.

Vous pouvez fermer le panneau de navigation globale en cliquant ou en appuyant sur **Fermer** pour revenir à votre position précédente.

![Barre supérieure du panneau de navigation](/help/sites-cloud/authoring/assets/navigation-bar.png)

La navigation globale se compose de deux panneaux, représentés par des icônes dans la marge gauche de l’écran :

* **[Navigation](#navigation-panel)** : représenté par une boussole  et le panneau par défaut lorsque vous vous connectez à AEM
* **[Outils](#tools-panel)** : représenté par un marteau

Consultez les options disponibles dans ces panneaux ci-dessous.

### Panneau de navigation {#navigation-panel}

Panneau de navigation :

![Panneau de navigation](/help/sites-cloud/authoring/assets/navigation.png)

Le titre de l’onglet du navigateur est mis à jour pour refléter votre emplacement lorsque vous naviguez dans les consoles et le contenu.

Les consoles suivantes sont disponibles à partir du panneau de navigation :

| Console | Objectif |
|---|---|
| Projets | La console Projets vous donne un accès direct à vos projets. [Les projets sont des tableaux de bord virtuels](/help/sites-cloud/authoring/projects/overview.md) qui peuvent être utilisés pour créer une équipe. Vous pouvez ensuite donner à cette équipe un accès aux ressources, aux workflows et aux tâches, ce qui permet aux utilisateurs de travailler vers un objectif commun. |
| Sites | Les consoles Sites permettent de [créer, d’afficher et de gérer des sites](/help/sites-cloud/authoring/fundamentals/organizing-pages.md) exécutés sur votre instance AEM. Grâce à ces consoles, vous pouvez créer, modifier, copier, déplacer et supprimer des pages, démarrer des workflows et publier des pages. |
| Fragments d’expérience | Un [fragment d’expérience](/help/sites-cloud/authoring/fundamentals/experience-fragments.md) est une expérience autonome qui peut être réutilisée sur l’ensemble des canaux et qui présente des variations, ce qui vous évite de devoir copier et coller à plusieurs reprises des expériences ou des parties d’expériences. |
| Assets | La console Ressources vous permet d’importer et de gérer des [ressources numériques telles que des images, des vidéos, des documents et des fichiers audio](/help/assets/overview.md). Ces ressources peuvent ensuite être utilisées par n’importe quel site s’exécutant sur la même instance AEM. Vous pouvez également créer et gérer des [fragments de contenu](/help/assets/content-fragments/content-fragments.md) à partir de la console Ressources. |
| Personnalisation  | Cette console propose un ensemble d’outils de [création de contenu ciblé et de présentation d’expériences personnalisées](/help/sites-cloud/authoring/personalization/overview.md). |
| Fragments de contenu | Les [Fragments de contenu](/help/sites-cloud/administering/content-fragments/content-fragments.md) vous permettent de concevoir, créer, organiser et publier du contenu indépendant des pages. Ils vous permettent de préparer du contenu structuré prêt à être utilisé à plusieurs emplacements/sur plusieurs canaux, idéal pour la création de pages et la diffusion headless. |

## Panneau Outils {#tools-panel}

Dans le panneau Outils se trouve un panneau latéral contenant un éventail de catégories, qui regroupe des consoles Outils similaires. Les consoles Outils vous donnent accès à un certain nombre d’outils et de consoles spécialisés pour la gestion des sites web, des ressources numériques et d’autres aspects du référentiel de contenu. <!--The [Tools consoles](/help/sites-administering/tools-consoles.md) provide access to a number of specialized tools and consoles that help you administer your websites, digital assets, and other aspects of your content repository.-->

![Panneau Outils](/help/sites-cloud/authoring/assets/tools-panel.png)

## En-tête {#the-header}

L’en-tête est toujours affiché en haut de l’écran. Bien que la plupart des options de l’en-tête restent les mêmes, quel que soit l’endroit où vous vous trouvez dans le système, certaines dépendent du contexte.

![En-tête de navigation](/help/sites-cloud/authoring/assets/navigation-bar.png)

* [Navigation globale](#global-navigation)

  Sélectionnez le lien **Adobe Experience Manager** pour naviguer entre les consoles.

  ![Navigation globale](/help/sites-cloud/authoring/assets/global-navigation.png)

* [Rechercher](/help/sites-cloud/authoring/getting-started/search.md)

  ![Icône Rechercher](/help/sites-cloud/authoring/assets/search-icon.png)

  Vous pouvez également utiliser la [touche de raccourci](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) `/` (barre oblique) pour appeler la recherche à partir de n’importe quelle console.

* [Solutions](https://www.adobe.com/fr/experience-cloud.html)

  ![Bouton Solutions](/help/sites-cloud/authoring/assets/solutions.png)

* [Aide](#accessing-help)

  ![Bouton Aide](/help/sites-cloud/authoring/assets/help.png)

* [Notifications](/help/sites-cloud/authoring/getting-started/inbox.md)

  ![Bouton Notifications](/help/sites-cloud/authoring/assets/notifications.png)

  Cette icône comporte un badge indiquant le nombre de notifications incomplètes actuellement attribuées.

* [Propriétés de l’utilisateur](/help/sites-cloud/authoring/getting-started/account-environment.md)

  ![Bouton Propriétés de l’utilisateur](/help/sites-cloud/authoring/assets/user-properties.png)

* [Sélecteur de rail](#rail-selector)

  ![Bouton Sélecteur de rail](/help/sites-cloud/authoring/assets/rail-selector.png)

  Les options présentées dépendent de la console active. Par exemple, dans la console **Sites**, vous ne pouvez sélectionner que le contenu (valeur par défaut), la chronologie, les références ou le panneau latéral de filtrage.

  ![Exemple de sélecteur de rail](/help/sites-cloud/authoring/assets/rail-selector-example.png)

* Chemin de navigation

  ![Chemin de navigation dans la barre de navigation](/help/sites-cloud/authoring/assets/breadcrumbs-navigation.png)

  Le chemin de navigation est situé au milieu du rail. Il affiche toujours la description de l’élément sélectionné et vous permet de naviguer au sein d’une console spécifique. Dans la console **Sites**, vous pouvez parcourir les différents niveaux de votre site web.

  Il vous suffit de cliquer sur le texte du chemin de navigation pour afficher une liste déroulante des niveaux de la hiérarchie de l’élément sélectionné. Cliquez sur une entrée pour accéder à cet emplacement.

  ![Exemple de chemin de navigation développé](/help/sites-cloud/authoring/assets/breadcrumbs-example.png)

* Bouton **Créer**

  ![Bouton Créer](/help/sites-cloud/authoring/assets/create.png)

  Une fois que vous cliquez dessus, les options affichées sont adaptées à la console ou au contexte.

* [Vues](#viewing-and-selecting-resources)

  L’icône Vues se trouve à l’extrémité droite de la barre d’outils AEM. Comme elle indique également la vue actuelle, elle change. Par exemple, la vue par défaut, **Mode Colonnes** affiche :

  ![Bouton Vues](/help/sites-cloud/authoring/assets/views-button.png)

  Vous pouvez basculer entre la vue Colonnes, Carte et Liste. Dans la vue Liste, les paramètres de vue sont également affichés.

  ![Vues](/help/sites-cloud/authoring/assets/view.png)

  >[!NOTE]
  >
  >L’option **Paramètres** est disponible uniquement dans la vue **Liste**.

* Navigation au clavier

  Vous pouvez naviguer sur un site web en utilisant exclusivement le clavier. Ce processus s’appuie sur la fonctionnalité de la touche **TAB** (tabulation) dans un navigateur standard (ou **OPT+TAB**) pour vous déplacer entre les éléments de la page pouvant recevoir le focus.

  Dans la console **Sites**, vous pouvez ajouter l’option **Passer au contenu principal**. Cette option apparaît lorsque vous passez d’une option d’en-tête à une autre. Elle permet d’accélérer la navigation en ignorant les éléments standard de la barre d’outils (produit) et en accédant directement au contenu principal.

  ![Passer au contenu principal](/help/sites-cloud/authoring/assets/skip-to-main-content.png)

## Accès à l’Aide    {#accessing-help}

Plusieurs ressources d’aide sont disponibles :

* **Barre d’outils de la console**

  Selon votre emplacement, l’icône **Aide** ouvre les ressources appropriées :

  ![Icône d’aide](/help/sites-cloud/authoring/assets/help-console.png)

* **Navigation**

  La première fois que vous naviguez dans le système, [une série de diapositives présente la navigation au sein d’AEM](#product-navigation).

  ![Tutoriel](/help/sites-cloud/authoring/assets/tutorial.png)

* **Éditeur de page**

  La première fois que vous modifiez une page, une série de diapositives présente l’éditeur de page.

  ![Tutoriel de l’éditeur](/help/sites-cloud/authoring/assets/editor-tutorial.png)

  Parcourez cet aperçu comme vous le feriez avec l’[aperçu de navigation du produit](#product-navigation) la première fois que vous accédez à une console.

  Dans le menu [**Informations sur la page**, sélectionnez l’option **Aide**](/help/sites-cloud/authoring/fundamentals/environment-tools.md#accessing-help) pour afficher de nouveau cette présentation à tout moment.

* **Console Outils**

  Dans la console **Outils**, vous pouvez également accéder aux **ressources** externes :

   * **Documentation** : affichez la documentation de Web Experience Management.
   * **Ressources pour les développeurs** : ressources et téléchargements pour les développeurs.

  >[!NOTE]
  >
  >Vous pouvez accéder à un aperçu des raccourcis clavier disponibles à tout moment à l’aide de la touche `?` (point d’interrogation) lorsque vous vous trouvez dans une console.
  >
  >Pour une présentation de tous les raccourcis clavier, reportez-vous à la documentation suivante :
  >
  >* [Raccourcis clavier lors de la modification de pages](/help/sites-cloud/authoring/fundamentals/keyboard-shortcuts.md)
  >* [Raccourcis clavier pour les consoles](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md)

## Barre d’outils Actions {#actions-toolbar}

Lorsque vous sélectionnez une ressource (une page ou un actif, par exemple), diverses actions sont indiquées par des icônes, avec un texte explicatif dans la barre d’outils. Ces actions dépendent de différents éléments :

* La console active
* Le contexte actuel
* Si vous êtes en [mode de sélection](#viewing-and-selecting-resources)

L’action disponible dans la barre d’outils change pour tenir compte des actions que vous pouvez effectuer sur les éléments sélectionnés.

La manière dont vous [sélectionnez une ressource](#viewing-and-selecting-resources) dépend du mode.

En raison des restrictions d’espace dans certaines fenêtres, la barre d’outils peut rapidement dépasser l’espace disponible. Lorsque cela se produit, d’autres options s’affichent. Cliquez ou appuyez sur les points de suspension (les trois points ou **...**) ouvre un sélecteur de liste déroulante contenant toutes les actions restantes. Par exemple, après avoir sélectionné une page dans la console **Sites** :

![Options supplémentaires](/help/sites-cloud/authoring/assets/additional-options.png)

>[!NOTE]
>
>Les icônes individuelles disponibles sont documentées par rapport à la console, à la fonction ou au scénario approprié.

## Actions rapides {#quick-actions}

Dans [Mode Carte](#card-view) certaines actions sont disponibles sous forme d’icônes d’action rapide et se trouvent sur la barre d’outils. Les icônes d’action rapide sont disponibles pour un seul élément à la fois, ce qui évite d’avoir à présélectionner.

Les actions rapides sont visibles lorsque vous pointez (ordinateur de bureau) sur une carte de ressource avec la souris. Les actions rapides disponibles dépendent de la console et du contexte. Voici, par exemple, les actions rapides d’une page dans la console **Sites** :

![Options supplémentaires](/help/sites-cloud/authoring/assets/quick-actions.png)

## Affichage et sélection de ressources {#viewing-and-selecting-resources}

L’affichage, la navigation et la sélection sont identiques sur le plan conceptuel dans tous les modes, mais leur manipulation comporte de légères variations en fonction du mode utilisé.

Vous pouvez afficher, parcourir et sélectionner (pour effectuer d’autres opérations) vos ressources dans n’importe quel mode disponible. Chaque mode peut être sélectionné par le biais d’une icône située en haut à droite :

* [Mode Colonnes](#column-view)
* [Mode Carte](#card-view)
* [Vue Liste](#list-view)

>[!NOTE]
>
>Par défaut, AEM Assets n’affiche pas les rendus originaux des ressources dans l’interface utilisateur sous forme de miniatures, quel que soit le mode. Si vous êtes administrateur ou administratrice, vous pouvez utiliser des superpositions pour configurer AEM Assets afin d’afficher les rendus originaux sous forme de miniatures.

### Sélection de ressources {#selecting-resources}

La sélection d’une ressource en particulier dépend de la combinaison du mode et de l’appareil :

| Mode | Sélectionner Tactile | Sélectionner Bureau | Désélectionner Tactile | Désélectionner Bureau |
|---|---|---|---|---|
| Colonnes | Appuyer sur la miniature | Cliquer sur la miniature | Appuyer sur la miniature | Cliquer sur la miniature |
| Carte | Appuyer sur la carte et maintenir la pression | Placer le pointeur de la souris dessus, puis utiliser l’action rapide sous forme de coche | Appuyer sur la carte | Cliquer sur la carte |
| Liste | Appuyer sur la miniature | Cliquer sur la miniature | Appuyer sur la miniature | Cliquer sur la miniature |

#### Tout sélectionner {#select-all}

Vous pouvez sélectionner tous les éléments d’un mode en cliquant sur le bouton **Tout sélectionner** dans le coin supérieur droit de la console.

* En **mode Carte**, toutes les cartes sont sélectionnées.
* Dans la vue **Liste**, tous les éléments de la liste sont sélectionnés.
* En **mode Colonnes**, tous les éléments de la colonne la plus à gauche sont sélectionnés.

![Tout sélectionner](/help/sites-cloud/authoring/assets/select-all.png)

#### Tout désélectionner {#deselecting-all}

Dans tous les cas, lorsque vous sélectionnez des éléments, leur nombre est affiché dans le coin supérieur droit de la barre d’outils.

Vous pouvez annuler la sélection de tous les éléments et quitter le mode de sélection en procédant comme suit :

* Cliquez ou appuyez sur **X** à côté du nombre.
* Utilisez la touche **Échap**.

![Tout désélectionner](/help/sites-cloud/authoring/assets/deselect-all.png)

Quel que soit le mode, vous pouvez désélectionner tous les éléments en appuyant sur la touche Échap du clavier (si vous utilisez un ordinateur de bureau).

#### Exemple de sélection {#selecting-example}

1. Par exemple, en mode Carte :

   ![Sélection du mode Carte](/help/sites-cloud/authoring/assets/card-view-select.png)

1. Une fois que vous avez sélectionné une ressource, l’en-tête de premier niveau est couvert par la [barre d’outils Actions](#actions-toolbar), qui permet d’accéder aux actions actuellement applicables à la ressource sélectionnée.

   Pour quitter le mode de sélection, sélectionnez le signe **X** affiché en haut à droite de l’écran ou utilisez la touche **Échap**.

### Mode Colonnes {#column-view}

![Mode Colonnes](/help/sites-cloud/authoring/assets/column-view.png)

Le mode Colonnes permet de naviguer visuellement dans une arborescence de contenu à travers une série de colonnes en cascade. Ce mode vous permet de visualiser et de parcourir l’arborescence de votre site web.

Si vous sélectionnez une ressource dans la colonne la plus à gauche, les ressources enfants s’affichent dans une colonne à droite. Si vous sélectionnez une ressource dans la colonne de droite, les ressources enfants s’affichent dans une autre colonne à droite, etc.

* Vous pouvez naviguer de haut en bas dans l’arborescence en appuyant ou en cliquant sur le nom de la ressource ou sur le chevron situé à droite du nom de la ressource.

   * Le nom de la ressource et le chevron sont mis en surbrillance lorsque vous appuyez ou cliquez dessus.
   * Les enfants de la ressource sur laquelle vous avez cliqué/appuyé s’affichent dans la colonne située à droite de cette ressource.
   * Si vous appuyez ou cliquez sur un nom de ressource sans enfant, ses détails s’affichent dans la colonne finale.

* Appuyez ou cliquez sur la miniature pour sélectionner la ressource.

   * Lorsqu’elle est sélectionnée, une coche est superposée sur la miniature et le nom de la ressource est également mis en surbrillance.
   * Les détails de la ressource sélectionnée sont affichés dans la dernière colonne.
   * La barre d’outils d’action devient disponible.

  Lorsque vous sélectionnez une page en mode Colonnes, la page sélectionnée s’affiche dans la dernière colonne avec les détails suivants :

   * Titre de la page
   * Nom de la page (partie de l’URL de la page)
   * Modèle sur lequel est basée la page
   * Détails des modifications
   * Langue de la page
   * Publication et prévisualisation des détails

### Mode Carte {#card-view}

![Mode Carte](/help/sites-cloud/authoring/assets/card-view.png)

* Le mode Carte affiche des cartes d’informations pour chaque élément au niveau actuel. Elles fournissent des informations telles que :

   * une représentation visuelle du contenu de la page ;
   * le titre de la page ;
   * des dates importantes (telles que la date de la dernière modification ou publication) ;
   * si la page est verrouillée, masquée ou fait partie d’une Live Copy ;
   * le cas échéant, le moment auquel vous devez effectuer une action dans le cadre d’un workflow.
      * Les marques qui indiquent les actions requises peuvent être liées aux entrées de votre [boîte de réception](/help/sites-cloud/authoring/getting-started/inbox.md).

* Les [actions rapides](#quick-actions) sont également disponibles dans ce mode, comme la sélection et les actions courantes, telles que la modification.

  ![Actions rapides](/help/sites-cloud/authoring/assets/quick-actions.png)

* Vous pouvez parcourir l’arborescence vers le bas en appuyant/cliquant sur des cartes (en veillant à éviter les actions rapides), ou vers le haut en utilisant le [chemin de navigation dans l’en-tête](#the-header).

### Vue Liste {#list-view}

![Vue Liste](/help/sites-cloud/authoring/assets/list-view.png)

* La vue Liste répertorie les informations pour chaque ressource au niveau actuel.
* Vous pouvez parcourir l’arborescence vers le bas en appuyant/cliquant sur le nom de la ressource, ou vers le haut en utilisant le [chemin de navigation dans l’en-tête](#the-header).
* Pour sélectionner facilement tous les éléments de la liste, utilisez la case à cocher située dans le coin supérieur gauche de la liste.

  ![Tout sélectionner dans la vue Liste](/help/sites-cloud/authoring/assets/list-view-select-all.png)

   * Cette case apparaît cochée lorsque tous les éléments de la liste sont sélectionnés.

      * Cliquez ou appuyez sur la case à cocher pour tout désélectionner.

   * Lorsque seuls certains éléments sont sélectionnés, le signe moins apparaît.

      * Cliquez ou appuyez sur la case à cocher pour tout sélectionner.
      * Cliquez ou appuyez à nouveau sur la case à cocher pour tout désélectionner.

* Sélectionnez les colonnes à afficher à l’aide de l’option **Afficher les paramètres** située sous le bouton Vues. Vous pouvez afficher les colonnes suivantes :

   * **Nom** : nom de la page, qui peut s’avérer utile dans un environnement de création multilingue, car il fait partie de l’URL de la page et ne change pas, quelle que soit la langue.
   * **Modifié** : date de la dernière modification et dernière modification par l’utilisateur ou l’utilisatrice.
   * **Publié** : statut de la publication.
   * **Prévisualisation** : prévisualisation du statut
   * **Modèle** : modèle sur lequel la page est basée.
   * **Workflow** : workflow actuellement appliqué à la page. D’autres informations sont disponibles lorsque vous déplacez la souris ou lorsque vous ouvrez la chronologie.
   * **Analyse de la page**
   * **Visiteurs uniques**
   * **Temps passé sur la page**

     ![Sélectionner des colonnes](/help/sites-cloud/authoring/assets/select-columns.png)

  Par défaut, la colonne **Nom** est affichée ; ce nom fait partie de l’URL de la page. Dans certains cas, il se peut que l’auteur doive accéder à des pages rédigées dans une autre langue. Aussi, le fait de voir le nom de la page (qui reste généralement identique) peut s’avérer très utile si l’auteur ne connaît pas la langue de la page.

* Modifiez l’ordre des éléments à l’aide de la barre verticale en pointillés tout à droite de chaque élément de la liste.

  >[!NOTE]
  >
  >La modification de l’ordre fonctionne uniquement dans un dossier ordonné dont la valeur `jcr:primaryType` est `sling:OrderedFolder`.

  ![Ordre des colonnes](/help/sites-cloud/authoring/assets/column-order.png)

  Cliquez ou appuyez sur la barre de sélection verticale, puis faites glisser l’élément vers un nouvel emplacement dans la liste.

  ![Liste d’ordre](/help/sites-cloud/authoring/assets/order-list.png)

## Sélecteur de rail {#rail-selector}

Le **sélecteur de rail** est disponible dans le coin supérieur gauche de la fenêtre et affiche des options en fonction des consoles actives.

![Sélecteur de rail développé](/help/sites-cloud/authoring/assets/rail-selector-expanded.png)

Par exemple, dans la console **Sites**, vous pouvez sélectionner le contenu uniquement (valeur par défaut), l’arborescence de contenu, la chronologie, les références, les détails du site ou le panneau latéral de filtrage.

Si Contenu uniquement est sélectionné, alors seule l’icône de rail s’affiche. Si n’importe quelle autre option est sélectionnée, le nom des options apparaît en regard de l’icône de rail.

>[!NOTE]
>
>Des [raccourcis clavier](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) sont disponibles pour basculer rapidement entre les options d’affichage du rail.

### Arborescence de contenu {#content-tree}

L’arborescence de contenu peut être utilisée pour parcourir rapidement la hiérarchie du site dans le panneau latéral et afficher de nombreuses informations sur les pages du dossier actif.

Grâce au panneau latéral de l’arborescence de contenu associé à un mode Liste ou Carte, les utilisateurs peuvent facilement voir la structure hiérarchique du projet, naviguer facilement dans la structure de contenu à l’aide du panneau latéral de l’arborescence de contenu et afficher des informations détaillées sur la page en mode Liste.

![Arborescence de contenu](/help/sites-cloud/authoring/assets/content-tree.png)

>[!NOTE]
>
>Après avoir sélectionné une entrée dans la hiérarchie, vous pouvez naviguer rapidement dans la hiérarchie à l’aide des touches directionnelles.
>
>Voir [raccourcis clavier](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) pour plus d’informations.

### Chronologie {#timeline}

La chronologie peut être utilisée pour afficher et/ou lancer des événements qui se sont produits sur la ressource sélectionnée. Pour ouvrir la colonne Chronologie, utilisez le sélecteur de rail :

![Arborescence de la chronologie](/help/sites-cloud/authoring/assets/timeline.png)

La colonne Chronologie permet d’effectuer les actions suivantes :

* Afficher divers événements liés à un élément sélectionné.

   * Les types d’événements peuvent être sélectionnés dans la liste déroulante :

      * Commentaires
      * [Annotations](/help/sites-cloud/authoring/fundamentals/annotations.md)
      * [Activités](/help/sites-cloud/authoring/personalization/activities.md)
      * [Lancements](/help/sites-cloud/authoring/launches/overview.md)
      * [Versions](/help/sites-cloud/authoring/features/page-versions.md)
      * [Workflows](/help/sites-cloud/authoring/workflows/overview.md)
         * À l’exception des workflows transitoires, car aucune information historique n’est enregistrée pour ceux-ci <!--With the exception of [transient workflows](/help/sites-developing/workflows.md#transient-workflows) as no history information is saved for these-->
      * Tout afficher

* Ajouter/afficher des commentaires sur l’élément sélectionné. La zone **Commentaire** s’affiche dans la partie inférieure de la liste des événements. Saisissez un commentaire, puis appuyez sur Entrée pour l’enregistrer. Il s’affiche si vous sélectionnez l’option **Commentaires** ou **Tout afficher**.

* Certaines consoles possèdent des fonctionnalités supplémentaires. Par exemple, dans la console Sites, vous pouvez :

   * [enregistrer une version ;](/help/sites-cloud/authoring/features/page-versions.md)
   * [démarrer un workflow.](/help/sites-cloud/authoring/workflows/applying.md)

Ces fonctionnalités sont accessibles par le biais du chevron en regard du champ **Commentaires**.

![Champ de commentaire](/help/sites-cloud/authoring/assets/comments.png)

### Références {#references}

Les **références** affichent toutes les connexions avec la ressource sélectionnée. Par exemple, dans la console **Sites**, les [références](/help/sites-cloud/authoring/fundamentals/environment-tools.md#references) des pages affichent :

* [Lancements](/help/sites-cloud/authoring/launches/overview.md#launches-in-references-sites-console)
* [Live Copies](/help/sites-cloud/administering/msm/overview.md#openingthelivecopyoverviewfromreferences)
* [Copies de langue](/help/sites-cloud/administering/translation/preparation.md#seeing-the-status-of-language-roots)
* Références du contenu :

   * Liens d’autres pages vers la page sélectionnée
   * Contenu emprunté et/ou prêté à la page sélectionnée par le composant Référence

![Exemples de références](/help/sites-cloud/authoring/assets/references-example.png)

### Site {#site}

**Site** affiche les détails des sites [créés à l’aide d’un modèle de site](/help/sites-cloud/administering/site-creation/create-site.md).

![Rail Site](../assets/site-rail.png)

Consultez le document [Utilisation du rail Site pour gérer le thème de votre site](/help/sites-cloud/administering/site-creation/site-rail.md) pour plus d’informations sur l’utilisation du rail pour gérer le [thème de votre site](/help/sites-cloud/administering/site-creation/site-themes.md).

>[!TIP]
>
>Vous trouverez une description de bout en bout du processus de création d’un nouveau site à partir d’un modèle et de personnalisation de son thème dans le [Parcours de création rapide de site](/help/journey-sites/quick-site/overview.md).

### Filtrer {#filter}

Cette action ouvre un panneau similaire à [Rechercher](/help/sites-cloud/authoring/getting-started/search.md) avec les filtres d’emplacement correspondants déjà définis, ce qui permet de filtrer davantage le contenu que vous souhaitez afficher.

![Exemple de filtre](/help/sites-cloud/authoring/assets/filter.png)
