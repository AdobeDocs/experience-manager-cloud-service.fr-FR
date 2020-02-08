---
title: Création de modèles de page
description: Le modèle définit la structure de la page créée et, à l’aide de l’éditeur de modèles, les tâches de création et de gestion des modèles ne sont plus réservées aux développeurs.
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Création de modèles de page {#creating-page-templates}

Lors de la création d’une page, vous devez sélectionner un modèle. C’est la base pour la création de la page. Le modèle définit la structure de la page créée, le contenu initial et les composants pouvant être utilisés.

Grâce à l’**éditeur de modèles**, les tâches de création et de gestion des modèles ne sont plus réservées aux développeurs. Un type d’utilisateur expérimenté, appelé **créateur de modèles**, peut également être impliqué. Les développeurs doivent continuer à configurer l’environnement, créer les bibliothèques clientes ainsi que les composants à utiliser, mais une fois ces éléments fondamentaux en place, le **créateur de modèles** a la possibilité de créer et de configurer des modèles sans projet de développement.

La **console de modèles** permet aux créateurs de modèles :

* de créer ou de copier un modèle.
* Gérez le cycle de vie du modèle.

L’**éditeur de modèles** permet aux créateurs de modèles :

* d’ajouter des composants au modèle et de les positionner sur une grille réactive.
* De préconfigurer les composants ;
* de définir les composants qui peuvent être publiés dans les pages créées à partir du modèle.

Ce document explique comment un **créateur de modèles** peut utiliser la console et l’éditeur de modèles pour créer et gérer des modèles modifiables.

Pour obtenir des informations détaillées sur le fonctionnement des modèles modifiables à un niveau technique, voir le document destiné aux développeurs Modèles de page - Modifiables. <!-- For detailed information about how editable templates work at a technical level, please see the developer document [Page Templates - Editable](/help/sites-developing/page-templates-editable.md) for more information.-->

>[!NOTE]
>
>L’**éditeur de modèles** ne prend pas en charge le ciblage directement au niveau du modèle. Les pages créées à partir d’un modèle modifiable peuvent être ciblées, mais les modèles eux-mêmes ne le peuvent pas.

## Avant de commencer {#before-you-start}

>[!NOTE]
>
>Un administrateur doit configurer un dossier de modèles dans le **navigateur des configurations** et appliquer les autorisations appropriées permettant à un créateur de modèles de créer un modèle dans ce dossier.

Avant de commencer, il est important de tenir compte du fait que la création d’un nouveau modèle nécessite une collaboration. Pour cette raison, le [rôle](#roles) est indiqué pour chaque tâche. Cela n’a aucune incidence sur la manière dont vous utilisez un modèle pour créer une page, mais sur la manière dont une page se rapporte à son modèle.

### Rôles {#roles}

La création d’un modèle à l’aide de la **console de modèles** et de l’**éditeur de modèles** requiert une collaboration entre les rôles suivants :

* **Administrateur** :
   * Creates a new folder for templates requires `admin` rights.
   * Souvent, ces tâches peuvent également être effectuées par un développeur.
* **Développeur**:
   * Se concentre sur les détails techniques/internes.
   * Requiert une expérience de l’environnement de développement.
   * Fournit au créateur de modèles les informations nécessaires.
* **Créateur de modèles** :
   * Il s’agit d’un créateur particulier qui est membre du groupe `template-authors`
      * Ce groupe affecte les privilèges et les autorisations nécessaires.
   * Peut configurer l’utilisation des composants et d’autres détails importants nécessitant :
      * Quelques connaissances techniques
         * Par exemple, l’utilisation de modèles lors de la définition des tracés.
      * Des informations techniques provenant du développeur.

En raison de la nature de certaines tâches (comme la création d’un dossier), un environnement de développement est nécessaire et implique des connaissances et de l’expérience.

Les tâches détaillées dans ce document sont répertoriées avec le rôle responsable de leur exécution.

## Création et gestion des modèles {#creating-and-managing-templates}

Lors de la création d’un modèle modifiable :

* Utilisez la **console de modèles**. Elle est accessible dans la section **Général** de la console **Outils**. 
   * Ou directement à : `https://<host>:<port>/libs/wcm/core/content/sites/templates.html/conf`
* Can [create a folder for the templates](#creating-a-template-folder-admin) if necessary
* [Créez un modèle](#creating-a-new-template-template-author), qui est initialement vide.
* Si besoin, [définissez des propriétés supplémentaires](#defining-template-properties-template-author) pour le modèle.
* [Modifiez le modèle](#editing-templates-template-authors) pour définir ce qui suit :
   * [Structure](#editing-a-template-structure-template-author) : contenu prédéfini qui ne peut pas être modifié sur les pages créées avec le modèle.
   * [Contenu](#editing-a-template-initial-content-author) initial : contenu prédéfini pouvant être modifié sur les pages créées avec le modèle.
   * [Disposition](#editing-a-template-layout-template-author) - Pour une gamme de périphériques.
   * [Styles](/help/sites-cloud/authoring/features/style-system.md) : définissez les styles à utiliser avec le modèle et ses composants.
* [Activez le modèle](#enabling-a-template-template-author) à utiliser lors de la création d’une page.
* [Autorisez le modèle](#allowing-a-template-author) de la page ou de la branche souhaitée du site web.
* [Publiez le modèle](#publishing-a-template-template-author) pour le rendre disponible dans l’environnement de publication.

>[!NOTE]
>
>Les **modèles autorisés** sont souvent prédéfinis lors de la configuration initiale de votre site web.

>[!CAUTION]
>
>Ne saisissez jamais d’informations qui doivent être internationalisées dans un modèle. <!-- Never enter any information that needs to be [internationalized](/help/sites-developing/i18n.md) into a template.-->
>
>Pour les éléments de modèle tels que les en-têtes et les pieds de page qui doivent être localisés, tirez parti des fonctionnalités de [localisation des composants principaux.](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/get-started/localization.html)

### Création d’un dossier de modèles - Administrateur {#creating-a-template-folder-admin}

Vous devez créer un dossier de modèles pour votre projet afin de contenir les modèles spécifiques au projet. Il s’agit d’une tâche de l’administrateur qui est décrite dans le document Modèles de page - Modifiables. <!-- A template folder should be created for your project to hold your project-specific templates. This is an admin task and is described in the document [Page Templates - Editable](/help/sites-developing/page-templates-editable.md#template-folders).-->

### Création d’un modèle - Créateur de modèles {#creating-a-new-template-template-author}

1. Open the **Templates Console** (via **Tools ->** **General**) then navigate to the required folder.

   >[!NOTE]
   >
   >Dans une instance AEM standard, le dossier **Global** existe déjà dans la console Modèles. Il contient les modèles par défaut et fait office de dossier de rechange si le dossier actif ne contient pas de stratégies et/ou de types de modèles.
   >
   >Il est recommandé d’utiliser un dossier de modèles créé pour le projet. <!-- It is recommended best practice to use a [template folder created for your project](/help/sites-developing/page-templates-editable.md#template-folders).-->

1. Pour ouvrir l’Assistant, sélectionnez **Créer**, puis **Créer un modèle**.

1. Sélectionnez un **type de modèle**, puis cliquez sur **Suivant**.

   >[!NOTE]
   >
   >Les types de modèles sont des mises en page de modèles prédéfinies et peuvent être considérés comme les modèles d’un modèle. Ils sont prédéfinis par les développeurs ou l’administrateur système. Vous trouverez plus d’informations à ce sujet dans le document Modèles de page - Modifiables. <!-- More information can be found in the developer document [Page Templates - Editable](/help/sites-developing/page-templates-editable.md#template-type).-->

1. Renseignez les **détails du modèle** :

   * **Nom du modèle**
   * **Description**

1. Sélectionnez **Créer**. Un message de confirmation s’affiche. Sélectionnez **Ouvrir** pour commencer à modifier le modèle ou **Terminé** pour revenir à la console Modèles.

   >[!NOTE]
   >
   >Lorsque vous créez un modèle, il est marqué comme **Brouillon** dans la console pour indiquer qu’il n’est pas encore actif.

### Définition des propriétés des modèles - Créateur de modèles {#defining-template-properties-template-author}

Un modèle peut posséder les propriétés suivantes :

* Image
   * Image à utiliser comme [miniature du modèle](#template-thumbnail-image) pour faciliter la sélection, par exemple dans l’assistant Créer une page.
      * Peut être téléchargée
      * Peut être générée en fonction du contenu du modèle
* Titre
   * Titre servant à identifier le modèle, par exemple dans l’assistant **Créer une page**.
* Description
   * An optional description to provide more information about the template and its use, which can be seen for example in the **Create Page** wizard.

Pour afficher et/ou modifier les propriétés :

1. In the **Templates Console**, select the template.
1. Sélectionnez **Afficher les propriétés** dans la barre d’outils ou les options rapides pour ouvrir la boîte de dialogue.
1. Vous pouvez maintenant afficher ou modifier les propriétés du modèle.

>[!NOTE]
>
>L’état d’un modèle (brouillon, activé ou désactivé) est indiqué dans la console.

#### Miniature du modèle {#template-thumbnail-image}

Pour définir la miniature du modèle :

1. Modifiez les propriétés du modèle.
1. Choisissez si vous souhaitez télécharger une miniature ou la générer à partir du contenu du modèle.
   * Si vous souhaitez télécharger une miniature, cliquez ou appuyez sur **Télécharger l’image**
   * Si vous souhaitez générer une miniature, cliquez ou appuyez sur **Générer l’aperçu**
1. Pour les deux méthodes, un aperçu de la miniature s’affiche.
   * Si l’aperçu ne vous satisfait pas, cliquez ou appuyez sur **Effacer** pour télécharger une autre image ou pour générer à nouveau la miniature.
1. Lorsque vous êtes satisfait de la miniature, cliquez ou appuyez sur **Enregistrer et Fermer**.

### Activation et autorisation d’un modèle - Créateur de modèles {#enabling-and-allowing-a-template-template-author}

Pour utiliser un modèle lors de la création d’une page, vous devez effectuer les deux tâches suivantes :

* [Activez le modèle](#enabling-a-template-template-author) pour le rendre disponible lors de la création de pages.
* [Permet au modèle](#allowing-a-template-author) de spécifier les branches de contenu dans lesquelles le modèle peut être utilisé.

#### Activation d’un modèle - Créateur de modèles {#enabling-a-template-template-author}

Un modèle peut être activé ou désactivé pour être mis à disposition (ou non) dans l’assistant **Créer une page**.

>[!CAUTION]
>
>Une fois qu’un modèle est activé, un avertissement s’affiche lorsqu’un créateur de modèles commence à le mettre à jour. Cela permet d’avertir l’utilisateur que le modèle peut être référencé et que donc des modifications sont susceptibles d’affecter les pages faisant référence à ce modèle.

1. In the **Templates Console**, select the template.
1. Select **Enable** or **Disable** from the toolbar, and again in the confirmation dialog.
1. Vous pouvez maintenant utiliser le modèle lors de la [création d’une page](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page). Cependant, vous souhaiterez sans doute [modifier le modèle](#editing-templates-template-authors) en fonction de vos besoins.

>[!NOTE]
>
>L’état d’un modèle (brouillon, activé ou désactivé) est indiqué dans la console.

#### Autorisation d’un modèle - Créateur {#allowing-a-template-author}

Un modèle peut être rendu disponible ou indisponible pour certaines branches de la page.

1. Ouvrez [Propriétés de la page](/help/sites-cloud/authoring/fundamentals/page-properties.md) pour la page principale de la branche dans laquelle vous souhaitez que le modèle soit disponible.
1. Ouvrez l’onglet **Avancé**.
1. Under **Template Settings** use **Add field** to specify the path(s) to your template(s).

   Le chemin d’accès peut être explicite ou utiliser des modèles. Par exemple :

   `/conf/<your-folder>/settings/wcm/templates/.*`

   L’ordre des chemins d’accès n’a pas d’importance. La recherche porte sur tous les chemins d’accès, et tous les modèles sont extraits.

   >[!NOTE]
   >
   >Si la liste **Modèles autorisés** reste vide, l’arborescence est remontée jusqu’à ce qu’une valeur/liste soit détectée.
   >
   >
   >See Template Availability - the principles for allowed templates remain the same. <!--See [Template Availability](/help/sites-developing/templates.md#template-availability) - the principles for allowed templates remain the same.-->

1. Cliquez sur **Enregistrer** pour enregistrer les modifications apportées aux propriétés de la page.

>[!NOTE]
>
>Souvent, les modèles autorisés sont prédéfinis pour le site entier lorsqu’il est configuré.

### Publication d’un modèle - Créateur de modèles {#publishing-a-template-template-author}

Dans la mesure où il est référencé lors du rendu d’une page, le modèle (totalement configuré) doit être publié afin d’être disponible dans l’environnement de publication.

1. In the **Templates Console**, select the template.
1. Sélectionnez **Publier** dans la barre d’outils pour ouvrir l’Assistant.
1. Sélectionnez les **Politiques de contenu** à publier en tandem.
1. Sélectionnez **Publier** dans la barre d’outils pour terminer l’action.

## Modification des modèles  - Créateurs de modèles {#editing-templates-template-authors}

Lors de la création ou de la modification d’un modèle, vous pouvez définir différents aspects. La modification de modèles est similaire à la création de pages.

Le sélecteur **Mode** de la barre d’outils permet de sélectionner et de modifier l’aspect approprié du modèle :

* [Structure](#editing-a-template-structure-template-author)
* [Contenu initial](#editing-a-template-initial-content-author)
* [Mise en page](#editing-a-template-layout-template-author)

![Sélecteur de mode d’éditeur de modèles](/help/sites-cloud/authoring/assets/templates-mode.png)

Lorsque l’option **Stratégie de page** du menu **Informations sur la page**, vous pouvez [sélectionner les stratégies de page de votre choix](#page-policies) :

![Informations sur la page de l’éditeur de modèles](/help/sites-cloud/authoring/assets/templates-page-information.png)

>[!CAUTION]
>
>Si un créateur commence à modifier un modèle qui a déjà été activé, un avertissement s’affiche. Cela permet d’avertir l’utilisateur que le modèle peut être référencé et que donc des modifications sont susceptibles d’affecter les pages faisant référence à ce modèle.

### Attributs de modèle {#template-attributes}

Les attributs suivants d’un modèle peuvent être modifiés :

#### Structure {#template-structure}

Components added to the [structure](#editing-a-template-structure-template-author) cannot be moved/removed from resultant pages by the page authors. Si vous souhaitez que les créateurs de pages puissent ajouter et supprimer des composants aux pages créées, vous devez ajouter un système de paragraphes dans le modèle.

Lorsque les composants sont verrouillés, vous pouvez ajouter du contenu, que les créateurs de pages ne peuvent pas modifier. Vous pouvez déverrouiller des composants pour pouvoir définir le [contenu initial](#editing-a-template-initial-content-author).

>[!NOTE]
>
>En mode Structure, les composants parents d’un composant déverrouillé ne peuvent être ni déplacés, ni coupés, ni supprimés.

#### Contenu initial {#template-initial-content}

When a component has been unlocked you can define the [initial content](#editing-a-template-initial-content-author) that will be copied to the resultant page(s), created from the template. Ces composants déverrouillés peuvent être modifiés dans les pages créées.

>[!NOTE]
>
>En mode **Contenu initial** (et dans les pages créées), les composants déverrouillés qui possèdent un parent accessible (c’est-à-dire, les composants dans un conteneur de mise en page) peuvent être supprimés.

#### Mise en page {#template-layout}

With the [layout](#editing-a-template-layout-template-author) you can predefine the template layout for the required device formats. Le mode **Mise en page** pour la création de modèles comporte la même fonctionnalité que le mode [**Mise en page **pour la création de pages](/help/sites-cloud/authoring/features/responsive-layout.md#defining-layouts-layout-mode).

#### Stratégies de page {#template-page-policies}

[Les stratégies](#page-policies) de page peuvent lier des stratégies de page prédéfinies à la page. Ces stratégies de page définissent les différentes configurations de conception.

#### Styles {#template-styles}

The [Style System](/help/sites-cloud/authoring/features/style-system.md) allows a template author to define style classes in the content policy of a component so that a content author is able to select them when editing the component on a page. Ces styles peuvent être des variantes visuelles d’un composant, le rendant ainsi plus flexible.

Pour plus d’informations, voir la [documentation sur le système de style](/help/sites-cloud/authoring/features/style-system.md).

### Modification d’un modèle - Structure - Créateur de modèles {#editing-a-template-structure-template-author}

In **Structure** mode you define components and content for your template and define policy for the template and its components.

* Les composants définis dans la structure du modèle ne peuvent être ni déplacés ni supprimés dans les pages créées.
* Si vous souhaitez que les créateurs de pages puissent ajouter et supprimer des composants, ajoutez un système de paragraphes au modèle.
* Les composants peuvent être déverrouillés (et reverrouillés) pour que vous puissiez définir le [contenu initial](#editing-a-template-initial-content-author).
* Les stratégies de conception des composants et de la page sont définies.

![Structure de la page Editeur de modèle](/help/sites-cloud/authoring/assets/templates-page-structure.png)

Vous pouvez exécuter un certain nombre d’actions en mode **Structure** de l’éditeur de modèles, ainsi que plusieurs fonctions pour vous aider :

#### Add Components {#add-components}

Différents mécanismes permettent d’ajouter des composants au modèle :

* Dans l’Explorateur de **composants** du panneau latéral.
* By using the **Insert Component** option available on the toolbar of components already on the template or the **Drag components here** box.
* En faisant glisser une ressource (de l’Explorateur de **ressources** dans le panneau latéral) directement dans le modèle pour générer le composant approprié in situ.

Une fois ajouté, chaque composant est identifié par :

* Une bordure
* Un marqueur indiquant le type de composant
* Un marqueur indiquant quand le composant a été déverrouillé

>[!NOTE]
>
>When you add an out-of-the-box **Title** component to the template it will contain the default text **structure**.
>
>Si vous le modifiez et que vous ajoutez votre propre texte, le texte mis à jour sera utilisé pour les pages créées à partir du modèle.
>
>Si vous laissez le texte par défaut (structure), le titre propose par défaut le nom de la page suivante.

>[!NOTE]
>
>Although not identical, adding components and assets to a template has many similarities to similar actions when [page authoring](/help/sites-cloud/authoring/fundamentals/editing-content.md).

#### Actions des composants {#component-actions}

Intervenez sur les composants une fois qu’ils ont été ajoutés au modèle. Chaque instance individuelle comporte une barre d’outils qui permet d’accéder aux actions disponibles. La barre d’outils dépend du type de composant.

![Barre d’outils d’action d’un composant de modèle](/help/sites-cloud/authoring/assets/templates-component-actions.png)

Elle peut également dépendre des actions exécutées. Par exemple, lorsqu’une stratégie a été associée au composant, l’icône de configuration de la conception est disponible.

#### Modification et configuration {#edit-and-configure}

Avec ces deux actions, vous pouvez ajouter du contenu aux composants.

#### Border to Indicate Structure {#border-to-indicate-structure}

Lorsque vous travaillez en mode **Structure**, une bordure orange indique le composant actuellement sélectionné. Une ligne pointillée indique le composant parent.

#### Stratégie et propriétés (Général) {#policy-and-properties-general}

Les stratégies de contenu (ou de conception) définissent les propriétés de conception d’un composant. Par exemple, les composants disponibles ou les dimensions minimales/maximales. Elles s’appliquent au modèle (et aux pages créées avec le modèle).

Créez une stratégie de contenu ou sélectionnez-en une existante pour un composant.

![Stratégie de contenu, bouton](/help/sites-cloud/authoring/assets/templates-content-policy-button.png)

Cela permet de définir les détails de la conception.

![Stratégie de contenu](/help/sites-cloud/authoring/assets/template-content-policy.png)

La fenêtre de configuration est divisée en deux.

* In the left side of the dialogue under **Policy**, you have the ability to select an existing policy or select an existing one.
* In the right side of the dialogue under **Properties**, you can set the properties specific to the component type.

Les propriétés disponibles dépendent du composant sélectionné. Par exemple, pour un composant de texte, les propriétés définissent entre autres les options de copie et de collage, de mise en forme, et le style des paragraphes.

##### Stratégie {#policy}

Les stratégies de contenu (ou de conception) définissent les propriétés de conception d’un composant. Par exemple, les composants disponibles ou les dimensions minimales/maximales. Elles s’appliquent au modèle (et aux pages créées avec le modèle).

Under **Policy** you can select an existing policy to apply to the component via the drop-down.

![Sélectionner une stratégie](/help/sites-cloud/authoring/assets/templates-policy-selector.png)

Vous pouvez ajouter une nouvelle stratégie en sélectionnant le bouton d’ajout en regard du menu déroulant **Sélectionner une stratégie.** A new title should then be given in the **Policy Title** field.

![Ajouter une stratégie, bouton](/help/sites-cloud/authoring/assets/templates-add-policy-button.png)

La stratégie existante sélectionnée dans le menu déroulant **Sélectionner une stratégie** peut être copiée comme nouvelle stratégie à l’aide du bouton de copie en regard du menu déroulant. A new title should then be given in the **Policy Title** field. By default the copied policy will be titled **Copy of X**, where X is the title of the copied policy.

![Copier la stratégie, bouton](/help/sites-cloud/authoring/assets/templates-copy-policy-button.png)

Vous pouvez saisir la description de la stratégie dans le champ **Description de la stratégie** (facultatif).

In the **Other templates also using the selected policy** section, you can easily see which other templates use the policy selected in the **Select policy** dropdown.

![Utilisation de la stratégie existante](/help/sites-cloud/authoring/assets/templates-policy-use.png)

>[!NOTE]
>
>Si plusieurs composants du même type sont ajoutés comme contenu initial, la même stratégie s’applique à tous les composants.

##### Propriétés {#properties}

Sous l’en-tête **Propriétés**, vous pouvez définir les paramètres du composant. L’en-tête comporte deux onglets :

* Principal
* Fonctionnalités

###### Principal {#main}

Dans l’onglet **Principal**, les paramètres les plus importants du composant sont définis.

Par exemple, pour un composant d’image, les largeurs autorisées peuvent être définies en même temps que l’activation du chargement différé.

Si un paramètre permet plusieurs configurations, cliquez ou appuyez sur le bouton **Ajouter** pour ajouter une autre configuration.

![Ajouter un bouton](/help/sites-cloud/authoring/assets/templates-add-button.png)

Pour supprimer une configuration, cliquez ou appuyez sur le bouton **Supprimer** situé à droite de la configuration.

Pour supprimer une configuration, cliquez ou appuyez sur le bouton **Supprimer**.

![Bouton de suppression](/help/sites-cloud/authoring/assets/templates-delete-button.png)

###### Fonctionnalités {#features}

L’onglet **Fonctionnalités** permet d’activer ou de désactiver des fonctionnalités supplémentaires du composant.

Par exemple, pour un composant d’image, vous pouvez définir les proportions de recadrage, les orientations d’image autorisées et indiquer si les téléchargements sont autorisés.

![Onglet Fonctionnalités](/help/sites-cloud/authoring/assets/templates-features-tab.png)

>[!CAUTION]
>
>Note that in AEM crop ratios are defined as **height/width**. Cela diffère de la définition conventionnelle de la largeur/hauteur. Cela a été créée pour des raisons de compatibilité héritée. Les utilisateurs de la création de pages ne percevront aucune différence à condition que vous définissiez clairement le **Nom**, car c’est ce dernier qui s’affiche dans l’interface utilisateur.

>[!NOTE]
>
>Les stratégies de contenu pour les composants impliquant la mise en œuvre de l’Éditeur de texte enrichi  peuvent uniquement être définies pour les options accessibles par les paramètres de l’interface utilisateur, via ses propres paramètres d’interface utilisateur. <!--[Content policies for components implementing the rich text editor](/help/sites-administering/rich-text-editor.md#main-pars-header-206036638) can only be defined for options made available by the RTE through its UI settings.-->

#### Policy and Properties (Layout Container) {#policy-and-properties-layout-container}

Les paramètres de stratégie et de propriétés d’un conteneur de mises en page sont similaires à l’utilisation générale, mais avec quelques différences.

>[!NOTE]
>
>La configuration d’une stratégie est obligatoire pour les composants de conteneur, car elle permet de définir les composants qui seront disponibles dans le conteneur.

La fenêtre de configuration est divisée en deux, tout comme dans l’utilisation générale de la fenêtre.

##### Stratégie {#policy-layout}

Les stratégies de contenu (ou de conception) définissent les propriétés de conception d’un composant. Par exemple, les composants disponibles ou les dimensions minimales/maximales. Elles s’appliquent au modèle (et aux pages créées avec le modèle).

Under **Policy** you can select an existing policy to apply to the component via the drop-down. Cela fonctionne exactement comme dans l’utilisation générale de la fenêtre.

##### Propriétés {#properties-layout}

Sous l’en-tête **Propriétés**, vous pouvez choisir les composants disponibles pour le conteneur de mises en page et définir leurs paramètres. L’en-tête comporte trois onglets :

* Composants autorisés
* Composants par défaut
* Paramètres réactifs

###### Composants autorisés {#allowed-components}

Dans l’onglet **Composants autorisés**, vous définissez les composants disponibles pour le conteneur de mises en page.

* Les composants sont regroupés en groupes de composants, qui peuvent être développés et réduits.
* Un groupe entier peut être sélectionné en cochant le nom du groupe, et tous peuvent être désélectionnés en décochant la case.
* Le signe moins indique qu’au moins un élément du groupe est sélectionné, mais pas tous.
* Un champ de recherche est disponible pour filtrer un composant en fonction de son nom.
* Les chiffres à droite du nom du groupe de composants représentent le nombre total de composants sélectionnés dans ce groupe, quel que soit le filtre.

![Onglet Composants autorisés](/help/sites-cloud/authoring/assets/templates-allowed-components-tab.png)

###### Composants par défaut {#default-components}

Dans l’onglet **Composants par défaut**, vous définissez les composants qui sont automatiquement associés à des types de média donnés. Ainsi, lorsqu’un créateur fait glisser une ressource depuis le navigateur des ressources, AEM sait avec quel composant l’associer. Notez que seuls les composants dotés de zones de dépôt sont disponibles pour cette configuration.

Cliquez ou appuyez sur **Ajouter le mappage** pour ajouter un nouveau composant et un mappage de type MIME.

Sélectionnez un composant dans la liste, puis cliquez ou appuyez sur **Ajouter un type** pour ajouter un type MIME supplémentaire à un composant déjà mappé. Click the **Delete** icon to remove a MIME type.

![Panneau Composants par défaut](/help/sites-cloud/authoring/assets/templates-default-components-tab.png)

###### Paramètres réactifs {#responsive-settings}

Dans l’onglet **Paramètres réactifs**, vous pouvez configurer le nombre de colonnes de la grille résultante du conteneur de mises en page.

#### Déverrouiller et verrouiller les composants {#unlock-and-lock-components}

Vous verrouillez/déverrouiller des composants pour définir si le contenu est disponible pour être modifié en mode **Contenu initial**.

Lorsqu’un composant a été déverrouillé :

* Un indicateur de cadenas ouvert s’affiche sur la bordure.
* La barre d’outils Composants est ajustée en conséquence.
* Tout contenu déjà saisi ne sera plus affiché en mode **Structure**.
   * Already entered content is considered initial content and is only visible in **Initial Content** mode.
* Les parents du composant déverrouillé ne peuvent être ni déplacés, ni coupés, ni supprimés.

![Bouton Verrouiller le composant](/help/sites-cloud/authoring/assets/templates-unlock-component.png)

Cela inclut le déverrouillage des composants de conteneur, afin de pouvoir ajouter d’autres composants en mode **Contenu initial** ou dans des pages créées. Si vous avez déjà ajouté des composants/du contenu au conteneur avant de le déverrouiller, ceux-ci n’apparaîtront plus en mode **Structure**, mais s’afficheront en mode **Contenu initial**. En mode **Structure**, seul le composant de conteneur est affiché avec sa liste de **Composants autorisés**.

![Composants autorisés](/help/sites-cloud/authoring/assets/templates-allowed-components.png)

Pour économiser de l’espace, le conteneur de mise en page ne s’agrandit pas pour s’adapter à la liste des composants autorisés. À la place, le conteneur devient une liste déroulante.

Les composants configurables sont affichés avec une icône **Stratégie** sur laquelle vous pouvez appuyer ou cliquer pour modifier la stratégie et les propriétés de ce composant.

![Icône de composant configurable](/help/sites-cloud/authoring/assets/templates-configurable-component.png)

#### Relation avec les pages existantes {#relationship-to-existing-pages}

Si la structure est mise à jour après la création de pages en fonction du modèle, ces pages répercutent les modifications apportées au modèle. Un avertissement, ainsi que des boîtes de dialogue de confirmation, s’affichent dans la barre d’outils pour vous rappeler cette répercussion.

![Avertissement de bannière indiquant que le modèle est en cours d’utilisation](/help/sites-cloud/authoring/assets/templates-in-use-banner.png)

### Modification d’un modèle - Contenu initial - Créateur {#editing-a-template-initial-content-author}

Le mode **Contenu initial** est utilisé pour définir le contenu qui s’affiche lors de la première création d’une page en fonction du modèle. Le contenu initial peut ensuite être modifié par les créateurs de la page.

Même si l’ensemble du contenu créé en mode **Structure** est visible en mode **Contenu initial**, seuls les composants déverrouillés peuvent être sélectionnés et modifiés.

>[!NOTE]
>
>Le mode **Contenu initial** peut être envisagé comme mode de modification pour les pages créées avec ce modèle. Par conséquent, les stratégies ne sont pas définies en mode **Contenu initial**, mais plutôt en mode [**Structure **](#editing-a-template-structure-template-author).

* Les composants déverrouillés modifiables sont marqués. Une fois sélectionnés, ils comportent une bordure bleue :

   ![Mode Contenu initial](/help/sites-cloud/authoring/assets/templates-initial-content-mode.png)

* Les composants déverrouillés comportent une barre d’outils permettant de modifier et de configurer le contenu :

   ![Composant déverrouillé](/help/sites-cloud/authoring/assets/templates-unlocked-components.png)

* Si un composant de conteneur a été déverrouillé (en mode **Structure**), vous pouvez ajouter de nouveaux composants au conteneur (en mode **Contenu initial).** Les composants ajoutés en mode **Contenu initial** peuvent être déplacés ou supprimés dans les pages créées.

   Vous pouvez ajouter le composant à l’aide de la zone **Faire glisser les composants ici** ou de l’option **Insérer un nouveau composant** de la barre d’outils du conteneur approprié.

   ![Ajouter un composant](/help/sites-cloud/authoring/assets/templates-add-component.png)
   ![Ajouter un composant](/help/sites-cloud/authoring/assets/templates-add-component-dialog.png)

* Si le contenu initial du modèle est mis à jour après la création des pages en fonction du modèle, ces pages ne seront pas affectées par les modifications apportées au contenu initial du modèle.

>[!NOTE]
>
>Le contenu initial est destiné à préparer les composants et la mise en page, point de départ de la création du contenu. Il n’est pas destiné à constituer un contenu réel laissé tel quel. C’est pour cette raison que le contenu initial ne peut pas être traduit.
>
>Si vous devez inclure du texte convertible dans votre modèle, par exemple dans les en-têtes ou les pieds de page, vous pouvez utiliser les fonctions de [localisation des composants](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/get-started/localization.html)principaux.

### Modification d’un modèle - Mise en page - Créateur de modèles {#editing-a-template-layout-template-author}

Vous pouvez définir la mise en page du modèle pour différents dispositifs. [La mise en page réactive pour les modèles fonctionne de la même manière que pour la création de pages.](/help/sites-cloud/authoring/features/responsive-layout.md)

>[!NOTE]
>
>Les modifications apportées à la mise en page se répercutent en mode **Contenu initial**, mais aucune modification n’est visible en mode **Structure**.

![Modifier la disposition du modèle](/help/sites-cloud/authoring/assets/templates-edit-layout.png)

### Editing a Template - Page Policy - Template Author/Developer {#editing-a-template-page-policy-template-author-developer}

La stratégie de page, y compris les bibliothèques côté client requises, est conservée sous l’option Stratégie **de** page du menu Informations **sur la** page.

To access the **Page Policy** dialog:

1. From the **Template Editor**, select **Page Information** from the toolbar, then **Page Policy** to open the dialog.
1. The **Page Policy** dialog opens and is divided into two sections:

   * La moitié gauche définit les [stratégies de page](#page-policies).
   * La moitié droite définit les [propriétés de page](#page-properties).
   ![Conception de page](/help/sites-cloud/authoring/assets/templates-page-design.png)

#### Stratégies de page {#page-policies}

Vous pouvez appliquer une stratégie de contenu au modèle ou aux pages créées. Cette opération définit la stratégie de contenu pour le système de paragraphes principal dans la page.

![Stratégie de page](/help/sites-cloud/authoring/assets/templates-page-policy.png)

* Vous pouvez sélectionner une stratégie existante pour la page dans le menu déroulant **Sélectionner une stratégie**.

   ![Sélecteur de stratégie](/help/sites-cloud/authoring/assets/templates-policy-selector.png)

   Vous pouvez ajouter une nouvelle stratégie en sélectionnant le bouton d’ajout en regard du menu déroulant **Sélectionner une stratégie.** A new title should then be given in the **Policy Title** field.

   ![Ajouter une stratégie, bouton](/help/sites-cloud/authoring/assets/templates-add-policy-button.png)

   La stratégie existante sélectionnée dans le menu déroulant **Sélectionner une stratégie** peut être copiée comme nouvelle stratégie à l’aide du bouton de copie en regard du menu déroulant. A new title should then be given in the **Policy Title** field. By default the copied policy will be titled **Copy of X**, where X is the title of the copied policy.

   ![Copier la stratégie, bouton](/help/sites-cloud/authoring/assets/templates-copy-policy-button.png)

* Définissez le titre de la stratégie dans le champ **Titre de la stratégie**. Une stratégie doit comporter un titre pour faciliter sa sélection dans le menu déroulant **Sélectionner une stratégie**.

   ![Titre de la stratégie](/help/sites-cloud/authoring/assets/templates-policy-title.png)

* Vous pouvez saisir la description de la stratégie dans le champ **Description de la stratégie** (facultatif).
* In the **Other templates also using the selected policy** section, you can easily see which other templates use the policy selected in the **Select policy** dropdown.

   ![Utilisation des stratégies](/help/sites-cloud/authoring/assets/templates-policy-use.png)

#### Propriétés de page {#page-properties}

Using page properties, you can define the required client-side libraries by using the **Page Design** dialog. Ces bibliothèques côté client incluent des feuilles de style et du code JavaScript à charger avec le modèle et les pages créées avec ce modèle.

![Propriétés de page](/help/sites-cloud/authoring/assets/templates-page-properties.png)

* Spécifiez les bibliothèques côté client à appliquer aux pages créées avec ce modèle. Saisissez le nom d’une bibliothèque dans le champ de la section **Bibliothèques côté client**.

   ![Bibliothèques côté client](/help/sites-cloud/authoring/assets/templates-client-side-libraries.png)

* Si plusieurs bibliothèques s’avèrent nécessaires, cliquez sur le bouton Ajouter pour ajouter un champ supplémentaire pour le nom de la bibliothèque.

   ![Ajouter un bouton](/help/sites-cloud/authoring/assets/templates-add-button.png)

   Ajoutez autant de champs que nécessaire pour les bibliothèques côté client.

* Définissez la position relative des bibliothèques, en fonction de vos besoins, en faisant glisser les champs à l’aide de la poignée.

   ![Glisser la poignée](/help/sites-cloud/authoring/assets/templates-drag-handle.png)

>[!NOTE]
>
>Bien que le créateur de modèles puisse indiquer la stratégie de page dans le modèle, il doit se procurer les détails relatifs aux bibliothèques concernées côté client auprès du développeur.

### Modification d’un modèle - Propriétés de page initiales - Créateur {#editing-a-template-initial-page-properties-author}

À l’aide de l’option **Propriétés de page initiales**, vous pouvez définir les [propriétés initiales de la page](/help/sites-cloud/authoring/fundamentals/page-properties.md) à utiliser lors de la création des pages.

1. Dans l’éditeur de modèles, sélectionnez **Informations sur la page** dans la barre d’outils, puis **Propriétés de page initiales** pour ouvrir la boîte de dialogue.

1. Dans la boîte de dialogue, vous pouvez définir les propriétés à appliquer aux pages créées avec ce modèle.

   ![Modèles des propriétés de la page initiale](/help/sites-cloud/authoring/assets/templates-initial-properties.png)

1. Confirmez vos définitions en cliquant/appuyant sur **Terminé**.

## Meilleures pratiques {#best-practices}

Lors de la création de modèles, vous devez prendre en compte :

1. l’impact des modifications apportées au modèle une fois que les pages ont été créées à partir de ce modèle.

   Vous trouverez ci-dessous une liste des différentes opérations possibles sur les modèles, ainsi que leur répercussion sur les pages créées à partir de ces derniers :

   * Modifications apportées à la structure :

      * Elles sont immédiatement appliquées aux pages créées.
      * La publication du modèle modifié est toujours nécessaire pour que les visiteurs puissent voir les modifications.
   * Modifications apportées aux stratégies de contenu et aux configurations de conception :

      * Elles s’appliquent immédiatement aux pages créées.
      * La publication des modifications est nécessaire pour que les visiteurs voient les modifications.
   * Modifications apportées au contenu initial :

      * Elles s’appliquent uniquement aux pages créées après les modifications apportées au modèle.
   * Modifications apportées à la mise en page : selon si le composant modifié :

      * est réservé à la structure, auquel cas elles sont appliquées immédiatement.
      * contient le contenu initial, auquel cas elles ne sont appliquées qu’aux pages créées après les modifications.
   Soyez particulièrement prudent lors du :

   * verrouillage ou déverrouillage des composants sur des modèles activés.
   * Cela peut avoir des effets secondaires, car les pages existantes peuvent déjà utiliser ce contenu. En général :

      * Le déverrouillage des composants (qui ont été verrouillés) est manquant dans les pages existantes.
      * Le verrouillage des composants (modifiables) empêche l’affichage de ce contenu dans les pages.
   >[!NOTE]
   >
   >AEM génère des avertissements explicites lors de la modification du statut de verrouillage des composants dans les modèles qui ne sont plus des brouillons.

1. [Création de vos propres dossiers](#creating-a-template-folder-admin) pour les modèles spécifiques à un site.
1. [Publiez vos modèles](#publishing-a-template-template-author) à partir de la **console des modèles**.
