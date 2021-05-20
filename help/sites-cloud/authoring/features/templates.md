---
title: Création de modèles de page
description: Le modèle définit la structure de la page créée et, à l’aide de l’éditeur de modèles, les tâches de création et de gestion des modèles ne sont plus réservées aux développeurs.
exl-id: 4c9dbf26-5852-45ab-b521-9f051c153b2e
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '4600'
ht-degree: 100%

---

# Création de modèles de page {#creating-page-templates}

Lors de la création d’une page, vous devez sélectionner un modèle. C’est la base pour la création de la page. Le modèle définit la structure de la page créée, le contenu initial et les composants pouvant être utilisés.

Grâce à **Éditeur de modèles**, la création et la maintenance de modèles ne sont plus des tâches réservées aux développeurs. Un type d’utilisateur avancé, appelé **auteur de modèles**, peut également être impliqué. Les développeurs doivent encore configurer l’environnement, créer des bibliothèques clientes et créer les composants à utiliser. Cependant, une fois ces bases en place, l’**auteur de modèles** peut créer et configurer des modèles sans projet de développement.

La **console de modèles** permet aux créateurs de modèles :

* de créer ou de copier un modèle ;
* de gérer le cycle de vie du modèle.

L’**éditeur de modèles** permet aux créateurs de modèles :

* d’ajouter des composants au modèle et de les positionner sur une grille réactive.
* de préconfigurer les composants ;
* de définir les composants qui peuvent être publiés dans les pages créées à partir du modèle.

Ce document explique comment un **créateur de modèles** peut utiliser la console et l’éditeur de modèles pour créer et gérer des modèles modifiables.

Pour obtenir des informations détaillées sur le fonctionnement des modèles modifiables à un niveau technique, voir le document destiné aux développeurs [Modèles de page](/help/implementing/developing/components/templates.md).

>[!NOTE]
>
>L’**éditeur de modèles** ne prend pas en charge le ciblage directement au niveau du modèle. Les pages créées à partir d’un modèle modifiable peuvent être ciblées, mais pas les modèles eux-mêmes.

## Avant de commencer {#before-you-start}

>[!NOTE]
>
>Un administrateur doit configurer un dossier de modèles dans le **navigateur des configurations** et appliquer les autorisations appropriées permettant au créateur de modèles de créer un modèle dans ce dossier.

Avant de commencer, il est important de tenir compte du fait que la création d’un modèle nécessite une collaboration. Pour cette raison, le [rôle](#roles) est indiqué pour chaque tâche. Cela n’a pas d’incidence sur la façon dont vous utilisez le modèle pour créer une page, mais cela affecte la façon dont la page fait référence à son modèle.

### Rôles {#roles}

La création d’un modèle à l’aide de la **console Modèles** et de l’**éditeur de modèles** exige une collaboration entre les rôles suivants :

* **Administrateur** :
   * La création d’un dossier pour les modèles nécessite des droits `admin`.
   * Souvent, ces tâches peuvent également être effectuées par un développeur.
* **Développeur** :
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
   * Ou directement à l’adresse : `https://<host>:<port>/libs/wcm/core/content/sites/templates.html/conf`
* Si besoin, vous pouvez [créer un dossier pour les modèles](#creating-a-template-folder-admin).
* [Créez un modèle](#creating-a-new-template-template-author), qui est initialement vide.
* Si besoin, [définissez des propriétés supplémentaires](#defining-template-properties-template-author) pour le modèle.
* [Modifiez le modèle](#editing-templates-template-authors) pour définir ce qui suit :
   * [Structure](#editing-a-template-structure-template-author) : contenu prédéfini ne pouvant pas être modifié dans les pages créées avec le modèle.
   * [Contenu initial](#editing-a-template-initial-content-author) : contenu prédéfini pouvant être modifié dans les pages créées avec le modèle.
   * [Mise en page](#editing-a-template-layout-template-author) : pour de nombreux appareils.
   * [Styles](/help/sites-cloud/authoring/features/style-system.md) : définissez les styles à utiliser avec le modèle et ses composants.
* [Activez le modèle](#enabling-a-template-template-author) à utiliser lors de la création d’une page.
* [Autorisez le modèle](#allowing-a-template-author) de la page ou de la branche souhaitée du site web.
* [Publiez le modèle](#publishing-a-template-template-author) pour le rendre disponible dans l’environnement de publication.

>[!NOTE]
>
>Les **modèles autorisés** sont souvent prédéfinis lors de la configuration initiale de votre site web.

>[!TIP]
>
>Ne saisissez jamais d’informations qui doivent être internationalisées dans un modèle. <!-- Never enter any information that needs to be [internationalized](/help/sites-developing/i18n.md) into a template.-->
>
>Pour les éléments de modèle tels que les en-têtes et les pieds de page qui doivent être localisés, utilisez les [fonctionnalités de localisation des composants principaux.](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/get-started/localization.html)

### Création d’un dossier de modèles - Administrateur {#creating-a-template-folder-admin}

Vous devez créer un dossier de modèles pour votre projet afin de contenir les modèles spécifiques au projet. Il s’agit d’une tâche de l’administrateur qui est décrite dans le document [Modèles de page](/help/implementing/developing/components/templates.md#template-folders).

### Création d’un modèle - Créateur de modèles {#creating-a-new-template-template-author}

1. Ouvrez la **console de modèles** (en sélectionnant **Outils ->** **Général**), puis accédez au dossier souhaité.

   >[!NOTE]
   >
   >Dans une instance AEM standard, le dossier **Global** existe déjà dans la console de modèles. Il contient les modèles par défaut et fait office de dossier de rechange si le dossier actif ne contient pas de stratégies et/ou de types de modèles.
   >
   >Il est recommandé d’utiliser un [dossier de modèles créé pour le projet](/help/implementing/developing/components/templates.md#template-folders).

1. Pour ouvrir l’Assistant, sélectionnez **Créer**, puis **Créer un modèle**.

1. Sélectionnez un **type de modèle**, puis cliquez sur **Suivant**.

   >[!NOTE]
   >
   >Les types de modèles sont des mises en page de modèles prédéfinies et peuvent être considérés comme les modèles d’un modèle. Ils sont prédéfinis par les développeurs ou l’administrateur système. Vous trouverez plus d’informations à ce sujet dans le document [Modèles de page](/help/implementing/developing/components/templates.md#template-type).-->

1. Renseignez les **détails du modèle** :

   * **Nom du modèle**
   * **Description**

1. Sélectionnez **Créer**. Un message de confirmation s’affiche. Sélectionnez **Ouvrir** pour commencer à modifier le modèle ou **Terminé** pour revenir à la console de modèles.

   >[!NOTE]
   >
   >Lorsque vous créez un modèle, il est marqué comme **Brouillon** dans la console pour indiquer qu’il n’est pas encore actif.

>[!NOTE]
>
>Les modèles sont des outils puissants pour rationaliser votre processus de création de page. Cependant, un nombre excessif de modèles peut submerger les auteurs et semer la confusion dans la création de pages. Une bonne règle d’or consiste à maintenir le nombre de modèles au-dessous de 100.
>
>Adobe ne recommande pas d’avoir plus de 1 000 modèles en raison des impacts potentiels sur le rendement.

### Définition des propriétés des modèles - Créateur de modèles  {#defining-template-properties-template-author}

Un modèle peut posséder les propriétés suivantes :

* Image
   * Image à utiliser comme [miniature du modèle](#template-thumbnail-image) pour faciliter la sélection, par exemple dans l’assistant Créer une page.
      * Peut être téléchargée
      * Peut être générée en fonction du contenu du modèle
* Titre
   * Titre servant à identifier le modèle, par exemple dans l’assistant **Créer une page**.
* Description
   * Description facultative permettant de fournir des informations supplémentaires sur le modèle et son utilisation. Elle peut s’afficher, par exemple, dans l’assistant **Créer une page**.

Pour afficher et/ou modifier les propriétés :

1. Dans la **console de modèles**, sélectionnez le modèle.
1. Sélectionnez **Afficher les propriétés** dans la barre d’outils ou les options rapides pour ouvrir la boîte de dialogue.
1. Vous pouvez maintenant afficher ou modifier les propriétés du modèle.

>[!NOTE]
>
>L’état du modèle (brouillon, activé ou désactivé) est indiqué dans la console.

#### Miniature du modèle {#template-thumbnail-image}

Pour définir la miniature du modèle :

1. Modifiez les propriétés du modèle.
1. Choisissez si vous souhaitez télécharger une miniature ou la générer à partir du contenu du modèle.
   * Si vous souhaitez télécharger une miniature, cliquez ou appuyez sur **Télécharger l’image**
   * Si vous souhaitez générer une miniature, cliquez ou appuyez sur **Générer l’aperçu**
1. Pour les deux méthodes, un aperçu de la miniature s’affiche.
   * Si l’aperçu ne vous satisfait pas, cliquez ou appuyez sur **Effacer** pour télécharger une autre image ou pour générer à nouveau la miniature.
1. Lorsque vous êtes satisfait de la miniature, cliquez ou appuyez sur **Enregistrer et Fermer**.

### Activation et autorisation d’un modèle - Créateur de modèles  {#enabling-and-allowing-a-template-template-author}

Pour utiliser un modèle lors de la création d’une page, vous devez effectuer les deux tâches suivantes :

* [Activer le modèle](#enabling-a-template-template-author) : permet de le rendre disponible lors de la création de pages.
* [Autoriser le modèle](#allowing-a-template-author) : permet de spécifier les branches de contenu dans lesquelles le modèle peut être utilisé.

#### Activation d’un modèle - Créateur de modèles {#enabling-a-template-template-author}

Un modèle peut être activé ou désactivé pour être mis à disposition (ou non) dans l’assistant **Créer une page**.

>[!CAUTION]
>
>Une fois qu’un modèle est activé, un avertissement s’affiche lorsqu’un créateur de modèles commence à le mettre à jour. Cela permet d’avertir l’utilisateur que le modèle peut être référencé et que donc des modifications sont susceptibles d’affecter les pages faisant référence à ce modèle.

1. Dans la **console de modèles**, sélectionnez le modèle.
1. Sélectionnez **Activer** ou **Désactiver** dans la barre d’outils, puis de nouveau dans la boîte de dialogue de confirmation.
1. Vous pouvez maintenant utiliser le modèle lors de la [création d’une page](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page). Cependant, vous souhaiterez sans doute [modifier le modèle](#editing-templates-template-authors) en fonction de vos besoins.

>[!NOTE]
>
>L’état du modèle (brouillon, activé ou désactivé) est indiqué dans la console.

#### Autorisation d’un modèle - Créateur {#allowing-a-template-author}

Un modèle peut être rendu disponible ou indisponible pour certaines branches de la page.

1. Ouvrez [Propriétés de la page](/help/sites-cloud/authoring/fundamentals/page-properties.md) pour la page principale de la branche dans laquelle vous souhaitez que le modèle soit disponible.
1. Ouvrez l’onglet **Avancé**.
1. Sous **Paramètres du modèle**, utilisez **Ajouter un champ** pour spécifier le ou les chemins d’accès de vos modèles.

   Le chemin d’accès peut être explicite ou utiliser des modèles. Par exemple :

   `/conf/<your-folder>/settings/wcm/templates/.*`

   L’ordre des chemins d’accès n’a pas d’importance. La recherche porte sur tous les chemins d’accès, et tous les modèles sont extraits.

   >[!NOTE]
   >
   >Si la liste **Modèles autorisés** reste vide, l’arborescence est remontée jusqu’à ce qu’une valeur/liste soit détectée.
   >
   >
   >Voir [Disponibilité des modèles](/help/implementing/developing/components/templates.md#template-availability) : les principes des modèles autorisés restent identiques.

1. Cliquez sur **Enregistrer** pour enregistrer les modifications apportées aux propriétés de la page.

>[!NOTE]
>
>Souvent, les modèles autorisés sont prédéfinis pour le site entier lorsqu’il est configuré.

### Publication d’un modèle - Créateur de modèles {#publishing-a-template-template-author}

Dans la mesure où il est référencé lors du rendu d’une page, le modèle (totalement configuré) doit être publié afin d’être disponible dans l’environnement de publication.

1. Dans la **console de modèles**, sélectionnez le modèle.
1. Sélectionnez **Publier** dans la barre d’outils pour ouvrir l’Assistant.
1. Sélectionnez les **Politiques de contenu** à publier en tandem.
1. Sélectionnez **Publier** dans la barre d’outils pour terminer l’action.

## Modification des modèles - Créateurs de modèles  {#editing-templates-template-authors}

Lors de la création ou de la modification d’un modèle, vous pouvez définir différents aspects. La modification de modèles est similaire à la création de pages.

Le sélecteur **Mode** de la barre d’outils permet de sélectionner et de modifier l’aspect approprié du modèle :

* [Structure](#editing-a-template-structure-template-author)
* [Contenu initial](#editing-a-template-initial-content-author)
* [Mise en page](#editing-a-template-layout-template-author)

![Sélecteur de mode de l’éditeur de modèles](/help/sites-cloud/authoring/assets/templates-mode.png)

Tandis que l’option **Stratégie de page** du menu **Informations sur la page**, vous permet de [sélectionner les stratégies de page désirées](#page-policies) :

![Informations sur la page de l’éditeur de modèles](/help/sites-cloud/authoring/assets/templates-page-information.png)

>[!CAUTION]
>
>Si un créateur commence à modifier un modèle qui a déjà été activé, un avertissement s’affiche. Cela permet d’avertir l’utilisateur que le modèle peut être référencé et que donc des modifications sont susceptibles d’affecter les pages faisant référence à ce modèle.

### Attributs de modèle {#template-attributes}

Les attributs suivants d’un modèle peuvent être modifiés :

#### Structure {#template-structure}

Les composants ajoutés à la [structure](#editing-a-template-structure-template-author) ne peuvent pas être déplacés/supprimés dans les pages créées par les créateurs de pages. Si vous souhaitez que les créateurs de pages puissent ajouter et supprimer des composants aux pages créées, vous devez ajouter un système de paragraphes dans le modèle.

Lorsque les composants sont verrouillés, vous pouvez ajouter du contenu, que les créateurs de pages ne peuvent pas modifier. Vous pouvez déverrouiller des composants pour pouvoir définir le [contenu initial](#editing-a-template-initial-content-author).

>[!NOTE]
>
>En mode Structure, les composants parents d’un composant déverrouillé ne peuvent être ni déplacés, ni coupés, ni supprimés.

#### Contenu initial {#template-initial-content}

Lorsqu’un composant a été déverrouillé, vous pouvez définir le [contenu initial](#editing-a-template-initial-content-author) qui sera copié dans les pages créées à partir du modèle. Ces composants déverrouillés peuvent être modifiés dans les pages créées.

>[!NOTE]
>
>En mode **Contenu initial** (et dans les pages créées), les composants déverrouillés qui possèdent un parent accessible (c’est-à-dire, les composants dans un conteneur de mises en page) peuvent être supprimés.

#### Disposition {#template-layout}

Vous pouvez prédéfinir la [disposition](#editing-a-template-layout-template-author) du modèle pour les formats d’appareil de votre choix. Le mode **Disposition** pour la création de modèles comporte la même fonctionnalité que le mode [**Disposition** pour la création de pages](/help/sites-cloud/authoring/features/responsive-layout.md#defining-layouts-layout-mode).

#### Stratégies de page {#template-page-policies}

Dans le cadre des [stratégies de page](#page-policies), vous pouvez attribuer des stratégies de page prédéfinies à la page. Ces stratégies de page définissent les différentes configurations de conception.

#### Styles {#template-styles}

Le [système de style](/help/sites-cloud/authoring/features/style-system.md) permet à un auteur de modèles de définir des classes de style dans la stratégie de contenu d’un composant, de façon à pouvoir sélectionner ces classes lors de la modification du composant sur une page. Ces styles peuvent être des variantes visuelles d’un composant, le rendant ainsi plus flexible.

Pour plus d’informations, voir la [documentation sur le système de style](/help/sites-cloud/authoring/features/style-system.md).

### Modification d’un modèle - Structure - Créateur de modèles {#editing-a-template-structure-template-author}

En mode **Structure**, vous définissez les composants et le contenu de votre modèle, ainsi qu’une stratégie pour le modèle et ses composants.

* Les composants définis dans la structure du modèle ne peuvent être ni déplacés ni supprimés dans les pages créées.
* Si vous souhaitez que les créateurs de pages puissent ajouter et supprimer des composants, ajoutez un système de paragraphes au modèle.
* Les composants peuvent être déverrouillés (et reverrouillés) pour que vous puissiez définir le [contenu initial](#editing-a-template-initial-content-author).
* Les stratégies de conception des composants et de la page sont définies.

![Structure de page de l’éditeur de modèles](/help/sites-cloud/authoring/assets/templates-page-structure.png)

Vous pouvez exécuter un certain nombre d’actions en mode **Structure** de l’éditeur de modèles, ainsi que plusieurs fonctions pour vous aider :

#### Ajout de composants {#add-components}

Différents mécanismes permettent d’ajouter des composants au modèle :

* Dans l’Explorateur de **composants** du panneau latéral.
* Avec l’option **Insérer le composant** disponible dans la barre d’outils des composants figurant déjà dans le modèle ou la zone **Faire glisser les composants ici**.
* En faisant glisser une ressource (de l’Explorateur de **ressources** dans le panneau latéral) directement dans le modèle pour générer le composant approprié in situ.

Une fois ajouté, chaque composant est identifié par :

* Une bordure
* Un marqueur indiquant le type de composant
* Un marqueur indiquant quand le composant a été déverrouillé

>[!NOTE]
>
>Lorsque vous ajoutez un composant **Titre** prêt à l’emploi au modèle, il contient le texte **structure** par défaut.
>
>Si vous le modifiez et que vous ajoutez votre propre texte, le texte mis à jour sera utilisé pour les pages créées à partir du modèle.
>
>Si vous laissez le texte par défaut (structure), le titre propose par défaut le nom de la page suivante.

>[!NOTE]
>
>Même si l’ajout de composants et de ressources à un modèle n’est pas identique à des actions comparables lors de la [création de pages](/help/sites-cloud/authoring/fundamentals/editing-content.md), il présente de nombreuses similitudes avec ces actions.

#### Actions des composants {#component-actions}

Intervenez sur les composants une fois qu’ils ont été ajoutés au modèle. Chaque instance individuelle comporte une barre d’outils qui permet d’accéder aux actions disponibles. La barre d’outils dépend du type de composant.

![Barre d’outils d’actions d’un composant de modèle](/help/sites-cloud/authoring/assets/templates-component-actions.png)

Elle peut également dépendre des actions exécutées. Par exemple, lorsqu’une stratégie a été associée au composant, l’icône de configuration de la conception est disponible.

#### Modification et configuration {#edit-and-configure}

Avec ces deux actions, vous pouvez ajouter du contenu aux composants.

#### Bordure indiquant la structure {#border-to-indicate-structure}

Lorsque vous travaillez en mode **Structure**, une bordure orange indique le composant actuellement sélectionné. Une ligne pointillée indique le composant parent.

#### Stratégie et propriétés (générales) {#policy-and-properties-general}

Les stratégies de contenu (ou de conception) définissent les propriétés de conception d’un composant. Par exemple, les composants disponibles ou les dimensions minimales/maximales. Elles s’appliquent au modèle (et aux pages créées avec le modèle).

Créez une stratégie de contenu ou sélectionnez-en une existante pour un composant.

![Bouton Stratégie de contenu](/help/sites-cloud/authoring/assets/templates-content-policy-button.png)

Cela permet de définir les détails de la conception.

![Stratégie de contenu](/help/sites-cloud/authoring/assets/template-content-policy.png)

La fenêtre de configuration est divisée en deux.

* Dans la partie gauche de la boîte de dialogue, sous **Stratégie**, vous avez la possibilité de sélectionner une stratégie existante.
* Dans la partie droite de la boîte de dialogue, sous **Propriétés**, vous pouvez définir les propriétés spécifiques au type de composant.

Les propriétés disponibles dépendent du composant sélectionné. Par exemple, pour un composant de texte, les propriétés définissent entre autres les options de copie et de collage, de mise en forme, et le style des paragraphes.

##### Stratégie {#policy}

Les stratégies de contenu (ou de conception) définissent les propriétés de conception d’un composant. Par exemple, les composants disponibles ou les dimensions minimales/maximales. Elles s’appliquent au modèle (et aux pages créées avec le modèle).

Sous **Stratégie**, vous pouvez sélectionner, dans le menu déroulant, une stratégie à appliquer au composant.

![Sélectionner une stratégie](/help/sites-cloud/authoring/assets/templates-policy-selector.png)

Vous pouvez ajouter une nouvelle stratégie en sélectionnant le bouton d’ajout en regard du menu déroulant **Sélectionner une stratégie**. Vous devez ensuite attribuer un nouveau titre dans le champ **Titre de la stratégie**.

![Bouton Ajouter une stratégie](/help/sites-cloud/authoring/assets/templates-add-policy-button.png)

La stratégie existante sélectionnée dans le menu déroulant **Sélectionner une stratégie** peut être copiée comme nouvelle stratégie à l’aide du bouton de copie en regard du menu déroulant. Vous devez ensuite attribuer un nouveau titre dans le champ **Titre de la stratégie**. Par défaut, la stratégie copiée sera intitulée **Copie de X**, X étant le titre de la stratégie copiée.

![Bouton Copier la stratégie](/help/sites-cloud/authoring/assets/templates-copy-policy-button.png)

Vous pouvez saisir la description de la stratégie dans le champ **Description de la stratégie** (facultatif).

Dans la section **D’autres modèles utilisent également la stratégie sélectionnée**, vous pouvez facilement voir les autres modèles qui utilisent la stratégie sélectionnée dans le menu déroulant **Sélectionner une stratégie**.

![Utilisation d’une stratégie existante](/help/sites-cloud/authoring/assets/templates-policy-use.png)

>[!NOTE]
>
>Si plusieurs composants du même type sont ajoutés comme contenu initial, la même stratégie s’applique à tous les composants.

##### Propriétés {#properties}

Sous l’en-tête **Propriétés**, vous pouvez définir les paramètres du composant. L’en-tête comporte deux onglets :

* Principal
* Fonctions

###### Principal {#main}

Dans l’onglet **Principal**, les paramètres les plus importants du composant sont définis.

Par exemple, pour un composant d’image, les largeurs autorisées peuvent être définies en même temps que l’activation du chargement différé.

Si un paramètre permet plusieurs configurations, cliquez ou appuyez sur le bouton **Ajouter** pour ajouter une autre configuration.

![Bouton Ajouter](/help/sites-cloud/authoring/assets/templates-add-button.png)

Pour supprimer une configuration, cliquez ou appuyez sur le bouton **Supprimer** situé à droite de la configuration.

Pour supprimer une configuration, cliquez ou appuyez sur le bouton **Supprimer**.

![Bouton Supprimer](/help/sites-cloud/authoring/assets/templates-delete-button.png)

###### Fonctions {#features}

L’onglet **Fonctions** permet d’activer ou de désactiver des fonctions supplémentaires du composant.

Par exemple, pour un composant d’image, vous pouvez définir les proportions de recadrage, les orientations d’image autorisées et indiquer si les chargements sont autorisés.

![Onglet Fonctions](/help/sites-cloud/authoring/assets/templates-features-tab.png)

>[!CAUTION]
>
>Remarque : Dans AEM, les rapports de recadrage sont définis sous forme de **hauteur/largeur**. Cela diffère de la définition conventionnelle de la largeur/hauteur, à des fins de compatibilité avec les versions héritées. Les utilisateurs de la création de pages ne percevront aucune différence à condition que vous définissiez clairement le **Nom**, car c’est ce dernier qui s’affiche dans l’interface utilisateur.

>[!NOTE]
>
>[Les stratégies de contenu pour les composants impliquant la mise en œuvre de l’éditeur de texte enrichi](/help/implementing/developing/extending/rich-text-editor.md) peuvent uniquement être définies pour les options accessibles par les paramètres de l’interface utilisateur, via ses propres paramètres d’interface utilisateur.

#### Stratégie et propriétés (conteneur de mises en page) {#policy-and-properties-layout-container}

Les paramètres de stratégie et de propriétés d’un conteneur de mises en page sont similaires à l’utilisation générale, mais avec quelques différences.

>[!NOTE]
>
>La configuration d’une stratégie est obligatoire pour les composants de conteneur, car elle permet de définir les composants qui seront disponibles dans le conteneur.

La fenêtre de configuration est divisée en deux, tout comme dans l’utilisation générale de la fenêtre.

##### Stratégie {#policy-layout}

Les stratégies de contenu (ou de conception) définissent les propriétés de conception d’un composant. Par exemple, les composants disponibles ou les dimensions minimales/maximales. Elles s’appliquent au modèle (et aux pages créées avec le modèle).

Sous **Stratégie**, vous pouvez sélectionner, dans le menu déroulant, une stratégie à appliquer au composant. Cela fonctionne exactement comme dans l’utilisation générale de la fenêtre.

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

Dans l’onglet **Composants par défaut**, vous définissez les composants qui sont automatiquement associés à des types de médias donnés. Ainsi, lorsqu’un créateur fait glisser une ressource depuis le navigateur des ressources, AEM sait avec quel composant l’associer. Notez que seuls les composants dotés de zones de dépôt sont disponibles pour cette configuration.

Cliquez ou appuyez sur **Ajouter le mappage** pour ajouter un nouveau composant et un mappage de type MIME.

Sélectionnez un composant dans la liste, puis cliquez ou appuyez sur **Ajouter un type** pour ajouter un type MIME à un composant déjà mappé. Cliquez sur l’icône **Supprimer** pour supprimer un type MIME.

![Onglet Composants par défaut](/help/sites-cloud/authoring/assets/templates-default-components-tab.png)

###### Paramètres réactifs {#responsive-settings}

Dans l’onglet **Paramètres réactifs**, vous pouvez configurer le nombre de colonnes de la grille résultante du conteneur de mises en page.

#### Déverrouillage et verrouillage des composants {#unlock-and-lock-components}

Vous verrouillez/déverrouiller des composants pour définir si le contenu est disponible pour être modifié en mode **Contenu initial**.

Lorsqu’un composant a été déverrouillé :

* Un indicateur de cadenas ouvert s’affiche sur la bordure.
* La barre d’outils Composants est ajustée en conséquence.
* Tout contenu déjà saisi ne sera plus affiché en mode **Structure**.
   * Le contenu déjà saisi est considéré comme du contenu initial et n’est visible qu’en mode **Contenu initial**.
* Les parents du composant déverrouillé ne peuvent être ni déplacés, ni coupés, ni supprimés.

![Bouton Verrouiller le composant](/help/sites-cloud/authoring/assets/templates-unlock-component.png)

Cela comprend le déverrouillage des composants de conteneur afin que d’autres composants puissent être ajoutés, soit en mode **Contenu initial**, soit sur les pages résultantes. Si vous avez déjà ajouté des composants/du contenu au conteneur avant de le déverrouiller, ceux-ci ne s’afficheront plus en mode **Structure**, mais en mode **Contenu initial**. En mode **Structure**, seul le composant de conteneur est affiché avec sa liste de **Composants autorisés**.

![Composants autorisés](/help/sites-cloud/authoring/assets/templates-allowed-components.png)

Pour économiser de l’espace, le conteneur de mises en page ne se développe pas pour s’adapter à la liste des composants autorisés. À la place, le conteneur devient une liste déroulante.

Les composants configurables s’affichent avec une icône **Règle**, sur laquelle vous pouvez appuyer ou cliquer pour modifier la règle et les propriétés de ce composant.

![Icône de composant configurable](/help/sites-cloud/authoring/assets/templates-configurable-component.png)

#### Relation avec les pages existantes {#relationship-to-existing-pages}

Si la structure est mise à jour après la création de pages en fonction du modèle, ces pages répercutent les modifications apportées au modèle. Un avertissement, ainsi que des boîtes de dialogue de confirmation, s’affichent dans la barre d’outils pour vous rappeler cette répercussion.

![Bannière d’avertissement indiquant que le modèle est en cours d’utilisation](/help/sites-cloud/authoring/assets/templates-in-use-banner.png)

### Modification d’un modèle - Contenu initial - Créateur {#editing-a-template-initial-content-author}

Le mode **Contenu initial** est utilisé pour définir le contenu qui s’affiche lors de la première création d’une page en fonction du modèle. Le contenu initial peut ensuite être modifié par les créateurs de la page.

Même si l’ensemble du contenu créé en mode **Structure** est visible en mode **Contenu initial**, seuls les composants déverrouillés peuvent être sélectionnés et modifiés.

>[!NOTE]
>
>Le mode **Contenu initial** peut être envisagé comme mode d’édition pour les pages créées avec ce modèle. Par conséquent, les stratégies ne sont pas définies en mode **Contenu initial**, mais plutôt en mode [**Structure**](#editing-a-template-structure-template-author).

* Les composants déverrouillés modifiables sont marqués. Une fois sélectionnés, ils comportent une bordure bleue :

   ![Mode Contenu initial](/help/sites-cloud/authoring/assets/templates-initial-content-mode.png)

* Les composants déverrouillés comportent une barre d’outils permettant de modifier et de configurer le contenu :

   ![Composant déverrouillé](/help/sites-cloud/authoring/assets/templates-unlocked-components.png)

* Si un composant de conteneur a été déverrouillé (en mode **Structure**), vous pouvez ajouter de nouveaux composants au conteneur (en mode **Contenu initial**). Les composants ajoutés en mode **Contenu initial** peuvent être déplacés ou supprimés dans les pages créées.

   Vous pouvez ajouter le composant à l’aide de la zone **Faire glisser les composants ici** ou de l’option **Insérer un nouveau composant** de la barre d’outils du conteneur approprié.

   ![Ajouter un composant](/help/sites-cloud/authoring/assets/templates-add-component.png)
   ![Ajouter un composant](/help/sites-cloud/authoring/assets/templates-add-component-dialog.png)

* Si le contenu initial du modèle est mis à jour après la création des pages en fonction du modèle, ces pages ne seront pas affectées par les modifications apportées au contenu initial du modèle.

>[!NOTE]
>
>Le contenu initial est destiné à préparer les composants et la mise en page, point de départ de la création du contenu. Il n’est pas destiné à constituer un contenu réel laissé tel quel. C’est pour cette raison que le contenu initial ne peut pas être traduit.
>
>Si vous devez inclure du texte traduisible dans votre modèle, par exemple dans les en-têtes ou les pieds de page, vous pouvez utiliser les [fonctions de localisation des composants principaux](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/get-started/localization.html).

### Modification d’un modèle - Disposition - Créateur de modèles {#editing-a-template-layout-template-author}

Vous pouvez définir la disposition du modèle pour différents appareils. La [mise en page réactive](/help/sites-cloud/authoring/features/responsive-layout.md) pour les modèles fonctionne de la même manière que pour la création de pages.

>[!NOTE]
>
>Les modifications apportées à la mise en page se répercutent en mode **Contenu initial**, mais aucune modification n’est visible en mode **Structure**.

![Modifier la mise en page d’un modèle](/help/sites-cloud/authoring/assets/templates-edit-layout.png)

### Modification d’un modèle - Conception de page - Créateur/développeur de modèles {#editing-a-template-page-policy-template-author-developer}

La stratégie de page, y compris les bibliothèques clientes requises, est conservée sous l’option **Stratégie de page** du menu **Informations sur la page**.

Pour accéder à la boîte de dialogue **Stratégie de page** :

1. Dans l’**Éditeur de modèles**, sélectionnez **Informations sur la page** dans la barre d’outils, puis **Stratégie de page** pour ouvrir la boîte de dialogue.
1. La boîte de dialogue **Stratégie de page** s’ouvre. Elle est divisée en deux sections :

   * La moitié gauche définit les [stratégies de page](#page-policies).
   * La moitié droite définit les [propriétés de page](#page-properties).

   ![Conception de page](/help/sites-cloud/authoring/assets/templates-page-design.png)

#### Stratégies de page {#page-policies}

Vous pouvez appliquer une stratégie de contenu au modèle ou aux pages créées. Cette opération définit la stratégie de contenu pour le système de paragraphes principal dans la page.

![Stratégie de page](/help/sites-cloud/authoring/assets/templates-page-policy.png)

* Vous pouvez sélectionner une stratégie existante pour la page dans le menu déroulant **Sélectionner une stratégie**.

   ![Sélecteur de stratégie](/help/sites-cloud/authoring/assets/templates-policy-selector.png)

   Vous pouvez ajouter une nouvelle stratégie en sélectionnant le bouton d’ajout en regard du menu déroulant **Sélectionner une stratégie**. Vous devez ensuite attribuer un nouveau titre dans le champ **Titre de la stratégie**.

   ![Bouton Ajouter une stratégie](/help/sites-cloud/authoring/assets/templates-add-policy-button.png)

   La stratégie existante sélectionnée dans le menu déroulant **Sélectionner une stratégie** peut être copiée comme nouvelle stratégie à l’aide du bouton de copie en regard du menu déroulant. Vous devez ensuite attribuer un nouveau titre dans le champ **Titre de la stratégie**. Par défaut, la stratégie copiée sera intitulée **Copie de X**, X étant le titre de la stratégie copiée.

   ![Bouton Copier la stratégie](/help/sites-cloud/authoring/assets/templates-copy-policy-button.png)

* Définissez le titre de la stratégie dans le champ **Titre de la stratégie**. Une stratégie doit comporter un titre pour faciliter sa sélection dans le menu déroulant **Sélectionner une stratégie**.

   ![Titre de la stratégie](/help/sites-cloud/authoring/assets/templates-policy-title.png)

* Vous pouvez saisir la description de la stratégie dans le champ **Description de la stratégie** (facultatif).
* Dans la section **D’autres modèles utilisent également la stratégie sélectionnée**, vous pouvez facilement voir les autres modèles qui utilisent la stratégie sélectionnée dans le menu déroulant **Sélectionner une stratégie**.

   ![Utilisation des stratégies](/help/sites-cloud/authoring/assets/templates-policy-use.png)

#### Propriétés de page {#page-properties}

À l’aide des propriétés de page, vous pouvez définir les bibliothèques clientes requises avec la boîte de dialogue **Conception de page**. Ces bibliothèques clientes incluent des feuilles de style et du code JavaScript à charger avec le modèle et les pages créées avec ce modèle.

![Propriétés de page](/help/sites-cloud/authoring/assets/templates-page-properties.png)

* Spécifiez les bibliothèques clientes à appliquer aux pages créées avec ce modèle. Saisissez le nom d’une bibliothèque dans le champ de la section **Bibliothèques clientes**.

   ![Bibliothèques clientes](/help/sites-cloud/authoring/assets/templates-client-side-libraries.png)

* Si plusieurs bibliothèques s’avèrent nécessaires, cliquez sur le bouton Ajouter pour ajouter un champ supplémentaire pour le nom de la bibliothèque.

   ![Bouton Ajouter](/help/sites-cloud/authoring/assets/templates-add-button.png)

   Ajoutez autant de champs que nécessaire pour les bibliothèques clientes.

* Définissez la position relative des bibliothèques, en fonction de vos besoins, en faisant glisser les champs à l’aide de la poignée.

   ![Poignée de glissement](/help/sites-cloud/authoring/assets/templates-drag-handle.png)

>[!NOTE]
>
>Bien que le créateur de modèles puisse indiquer la stratégie de page dans le modèle, il doit se procurer les détails relatifs aux bibliothèques clientes concernées auprès du développeur.

### Modification d’un modèle - Propriétés de page initiales - Créateur {#editing-a-template-initial-page-properties-author}

À l’aide de l’option **Propriétés de page initiales**, vous pouvez définir les [propriétés initiales de la page](/help/sites-cloud/authoring/fundamentals/page-properties.md) à utiliser lors de la création des pages.

1. Dans l’éditeur de modèles, sélectionnez **Informations sur la page** dans la barre d’outils, puis **Propriétés de page initiales** pour ouvrir la boîte de dialogue.

1. Dans la boîte de dialogue, vous pouvez définir les propriétés à appliquer aux pages créées avec ce modèle.

   ![Propriétés de page initiales des modèles](/help/sites-cloud/authoring/assets/templates-initial-properties.png)

1. Confirmez vos définitions en cliquant/appuyant sur **Terminé**.

## Bonnes pratiques {#best-practices}

Lors de la création de modèles, vous devez prendre en compte :

1. L’impact des modifications apportées au modèle une fois que les pages ont été créées à partir de ce modèle.

   Vous trouverez ci-dessous la liste des différentes opérations possibles sur les modèles, ainsi que leur répercussion sur les pages créées à partir de ces derniers :

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
