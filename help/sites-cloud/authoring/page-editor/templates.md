---
title: Modèles pour créer des pages modifiables avec l’éditeur de page
description: Vous pouvez utiliser l’éditeur de modèles pour créer des modèles que les auteurs de contenu peuvent utiliser pour créer des pages modifiables avec l’éditeur de page.
exl-id: 4c9dbf26-5852-45ab-b521-9f051c153b2e
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '4415'
ht-degree: 80%

---


# Modèles pour créer des pages modifiables avec l’éditeur de page {#creating-page-templates}

Vous pouvez utiliser l’éditeur de modèles pour créer des modèles que les auteurs de contenu peuvent utiliser pour créer des pages modifiables avec l’éditeur de page.

## Vue d’ensemble {#overview}

Lorsqu’un auteur crée une page, il doit sélectionner un modèle, qui est utilisé comme base de la nouvelle page. Le modèle définit la structure de la page créée, le contenu initial et les composants qui peuvent être utilisés lors de la modification de la page dans l’éditeur de page.

>[!NOTE]
>
>[Des modèles sont également disponibles pour créer des pages modifiables avec l’éditeur universel](/help/sites-cloud/authoring/universal-editor/templates.md).

Avec l’**Éditeur de modèles**, la création et la maintenance des modèles ne sont pas des tâches réservées aux développeurs. Un type d’utilisateur avancé, appelé **créateur de modèles**, peut créer des modèles. L’équipe de développement doit configurer l’environnement, créer des bibliothèques clientes et créer les composants à utiliser. Cependant, une fois ces bases en place, l’**créateur de modèles** peut créer et configurer des modèles sans impliquer de développeur.

L’**Éditeur de modèles** permet aux auteurs et autrices de modèles de :

* Ajouter des composants au modèle et les positionner sur une grille réactive.
* de préconfigurer les composants ;
* Définir les composants qui peuvent être modifiés sur les pages créées avec le modèle.

Ce document explique comment un **créateur de modèles** peut utiliser l’**éditeur de modèles** pour créer et gérer des modèles modifiables.

Pour plus d’informations sur le fonctionnement des modèles modifiables au niveau technique, consultez le document de développement [Modèles modifiables](/help/implementing/developing/components/templates.md).

>[!NOTE]
>
>L’**éditeur de modèles** ne prend pas en charge le ciblage directement au niveau du modèle. Les pages créées à partir d’un modèle modifiable peuvent être ciblées, mais pas les modèles eux-mêmes.

## Avant de commencer {#before-you-start}

Avant de commencer, il est important de tenir compte du fait que la création d’un modèle nécessite une collaboration. Pour cette raison, le [rôle](#roles) est indiqué pour chaque tâche. Cela n’a pas d’incidence sur la façon dont vous utilisez le modèle pour créer une page, mais cela affecte la façon dont la page fait référence à son modèle.

>[!NOTE]
>
>Un administrateur doit configurer un dossier de modèles dans le **navigateur des configurations** et appliquer les autorisations appropriées permettant au créateur de modèles de créer un modèle dans ce dossier.

### Rôles {#roles}

La création d’un modèle nécessite la collaboration entre les rôles suivants :

* **Administrateur** :
   * La création d’un dossier pour les modèles nécessite des droits `admin`.
   * Ces tâches peuvent souvent être aussi effectuées par un développeur ou une développeuse.
* **Développeur** :
   * Se concentre sur les détails techniques/internes
   * Requiert une expérience de l’environnement de développement.
   * Fournit au créateur de modèles les informations nécessaires.
* **Créateur de modèles** :
   * Il s’agit d’un créateur particulier qui est membre du groupe `template-authors`
      * Ce groupe affecte les privilèges et les autorisations nécessaires.
   * Peut configurer l’utilisation de composants et d’autres détails de haut niveau qui nécessitent les éléments suivants :
      * Quelques connaissances techniques
         * Par exemple, l’utilisation de modèles lors de la définition de chemins.
      * Des informations techniques provenant du développeur.

En raison de la nature de certaines tâches, telles que la création d’un dossier, un environnement de développement est nécessaire, lequel nécessite des connaissances/de l’expérience.

Les tâches présentées dans ce document sont répertoriées avec le rôle responsable de leur exécution.

## Création et gestion des modèles {#creating-and-managing-templates}

Lors de la création d’un modèle modifiable :

* [Créez un modèle](#creating-a-new-template-template-author), qui est initialement vide.
* [Définissez des propriétés supplémentaires](#defining-template-properties-template-author) pour le modèle, le cas échéant.
* [Modifiez le modèle](#editing-templates-template-authors) pour définir :
   * [Structure](#editing-a-template-structure-template-author) : contenu prédéfini ne pouvant pas être modifié dans les pages créées avec le modèle.
   * [Contenu initial](#editing-a-template-initial-content-author) : contenu prédéfini pouvant être modifié dans les pages créées avec le modèle.
   * [Mise en page](#editing-a-template-layout-template-author) : pour de nombreux appareils.
   * [Styles](/help/sites-cloud/authoring/page-editor/style-system.md) : définissez les styles à utiliser avec le modèle et ses composants.
* [Activer le modèle](#enabling-a-template-template-author) à utiliser lors de la création d’une page
* [Autoriser le modèle](#allowing-a-template-author) pour la page ou la branche requise de votre site web
* [Publier le modèle](#publishing-a-template-template-author) pour le rendre disponible dans l’environnement de publication

>[!NOTE]
>
>Les **modèles autorisés** sont souvent prédéfinis lors de la configuration initiale de votre site web.

>[!TIP]
>
>Ne saisissez jamais d’informations qui doivent être [internationalisées](/help/implementing/developing/extending/i18n/dev.md) dans un modèle.
>
>Pour les éléments de modèle tels que les en-têtes et pieds de page qui doivent être localisés, utilisez les fonctions de localisation [ des composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/localization.html?lang=fr).

### Création d’un dossier de modèles - Administrateur {#creating-a-template-folder-admin}

Vous devez créer un dossier de modèles pour votre projet afin de contenir les modèles spécifiques au projet. Il s’agit d’une tâche d’administration décrite dans le document [Modèles de page](/help/implementing/developing/components/templates.md#template-folders).

### Création d’un modèle - Créateur ou créatrice de modèles {#creating-a-new-template-template-author}

1. Ouvrez la **[console Modèles](/help/sites-cloud/administering/templates-console.md)** puis accédez au dossier requis.

   >[!NOTE]
   >
   >Dans une instance AEM standard, le dossier **Global** existe déjà dans la console de modèles. Il contient les modèles par défaut et fait office de dossier de rechange si le dossier actif ne contient pas de politiques et/ou de types de modèles.
   >
   >Il est recommandé d’utiliser un [dossier de modèles créé pour votre projet](/help/implementing/developing/components/templates.md#template-folders).

1. Pour ouvrir l’Assistant, sélectionnez **Créer**, puis **Créer un modèle**.

1. Sélectionnez un **Type de modèle**, puis choisissez **Suivant**.

   >[!NOTE]
   >
   >Les types de modèle sont des mises en page de modèle prédéfinies qui peuvent être considérées comme des modèles pour un modèle. Ils sont prédéfinis par les développeurs/développeuses ou l’administrateur/administratrice système. Vous trouverez plus d’informations à ce sujet dans le document [Modèles de page](/help/implementing/developing/components/templates.md#template-type).-->

1. Complétez les **Détails du modèle** :

   * **Nom du modèle**
   * **Description**

1. Sélectionnez **Créer**. Un message de confirmation s’affiche. Sélectionnez **Ouvrir** pour commencer à modifier le modèle ou **Terminé** pour revenir à la console de modèles.

   >[!NOTE]
   >
   >Lorsque vous créez un modèle, il est marqué comme **Brouillon** dans la console pour indiquer qu’il n’est pas encore actif.

>[!TIP]
>
>Les modèles sont des outils puissants pour rationaliser votre processus de création de page. Cependant, un nombre excessif de modèles peut submerger les auteurs et semer la confusion dans la création de pages. Une bonne règle d’or consiste à maintenir le nombre de modèles au-dessous de 100.
>
>Adobe ne recommande pas d’avoir plus de 1 000 modèles en raison des impacts potentiels sur le rendement.

### Définition des propriétés des modèles – Créateur de modèles {#defining-template-properties-template-author}

Un modèle peut avoir les propriétés suivantes :

* Image
   * Image à utiliser comme [miniature du modèle](#template-thumbnail-image) pour faciliter la sélection, par exemple dans l’assistant Créer une page.
      * Peut être chargé
      * Peut être générée en fonction du contenu du modèle
* Titre
   * Titre utilisé pour identifier le modèle, comme dans l’assistant **Créer une page**.
* Description
   * Description facultative permettant de fournir des informations supplémentaires sur le modèle et son utilisation. Elle peut s’afficher, par exemple, dans l’assistant **Créer une page**.

Une fois le modèle créé, utilisez la **[console de modèles](/help/sites-cloud/administering/templates-console.md)** pour afficher ou modifier ses propriétés.

#### Miniature du modèle {#template-thumbnail-image}

Pour définir la miniature du modèle :

1. Modifiez les propriétés du modèle.
1. Choisissez si vous souhaitez charger une miniature ou la faire générer à partir du contenu du modèle.
   * Si vous souhaitez charger une miniature, sélectionnez **Charger l’image**
   * Si vous souhaitez générer une miniature, sélectionnez **Générer l’aperçu**
1. Pour les deux méthodes, un aperçu de la miniature s’affiche.
   * Si elle n’est pas satisfaisante, sélectionnez **Effacer** pour charger une autre image ou générer à nouveau la miniature.
1. Lorsque la miniature vous convient, sélectionnez **Enregistrer et fermer**.

### Activation et autorisation d’un modèle - Créateur ou créatrice de modèles {#enabling-and-allowing-a-template-template-author}

Pour utiliser un modèle lors de la création d’une page, vous devez effectuer les deux tâches suivantes :

* [Activer le modèle](#enabling-a-template-template-author) : permet de le rendre disponible lors de la création de pages.
* [Autoriser le modèle](#allowing-a-template-author) : permet de spécifier les branches de contenu dans lesquelles le modèle peut être utilisé.

#### Activation d’un modèle - Créateur de modèles {#enabling-a-template-template-author}

Un modèle peut être activé ou désactivé afin de le rendre disponible ou indisponible dans l’assistant **Créer une page**.

Utilisez la **[console de modèles](/help/sites-cloud/administering/templates-console.md)** pour activer ou désactiver un modèle.

>[!CAUTION]
>
>Une fois qu’un modèle est activé, un avertissement s’affiche lorsqu’un auteur ou une autrice de modèles commence à le mettre à jour. Cela permet d’informer la personne utilisatrice que le modèle peut être référencé. Toute modification peut donc avoir une incidence sur les pages qui le référencent.

#### Autorisation d’un modèle - Créateur {#allowing-a-template-author}

Un modèle peut être rendu disponible ou indisponible pour certaines branches de la page.

1. Ouvrez [Propriétés de la page](/help/sites-cloud/authoring/sites-console/page-properties.md) pour la page principale de la branche dans laquelle vous souhaitez que le modèle soit disponible.
1. Ouvrez l’onglet **Avancé**.
1. Sous **Paramètres du modèle**, utilisez **Ajouter un champ** pour spécifier le ou les chemins d’accès de vos modèles.

   Le chemin d’accès peut être explicite ou utiliser des modèles. Par exemple :

   `/conf/<your-folder>/settings/wcm/templates/.*`

   L’ordre des chemins n’a aucune importance. Tous les chemins sont analysés et tous les modèles sont récupérés.

   >[!NOTE]
   >
   >Si la liste **Modèles autorisés** est laissée vide, alors l’arborescence est remontée jusqu’à ce qu’une valeur/liste soit trouvée.
   >
   >Voir [Disponibilité des modèles](/help/implementing/developing/components/templates.md#template-availability) : les principes des modèles autorisés restent identiques.

1. Cliquez sur **Enregistrer** pour enregistrer les modifications apportées aux propriétés de la page.

>[!NOTE]
>
>Souvent, les modèles autorisés sont prédéfinis pour le site entier lorsqu’il est configuré.

### Publication d’un modèle - Créateur de modèles {#publishing-a-template-template-author}

Comme le modèle est référencé lors du rendu d’une page, le modèle entièrement configuré doit être publié afin d’être disponible dans l’environnement de publication.

les modèles Publish à l’aide de la **[console de modèles](/help/sites-cloud/administering/templates-console.md)**.

## Modification de modèles - Créateurs et créatrices de modèles {#editing-templates-template-authors}

Lors de la création ou de la modification d’un modèle, vous pouvez définir différents aspects. La modification de modèles est similaire à la création de pages.

Le sélecteur **Mode** de la barre d’outils permet de sélectionner et de modifier l’aspect approprié du modèle :

* [Structure](#editing-a-template-structure-template-author)
* [Contenu initial](#editing-a-template-initial-content-author)
* [Mise en page](#editing-a-template-layout-template-author)

![Sélecteur de mode de l’éditeur de modèles](/help/sites-cloud/authoring/assets/templates-mode.png)

Tandis que l’option **Politique de page** du menu **Informations sur la page** vous permet de [sélectionner les politiques de page requises](#page-policies) :

![Informations sur la page de l’éditeur de modèles](/help/sites-cloud/authoring/assets/templates-page-information.png)

>[!CAUTION]
>
>Si un auteur ou une autrice modifie un modèle qui a déjà été activé, un avertissement s’affiche. Cela permet d’informer la personne utilisatrice que le modèle peut être référencé. Toute modification peut donc avoir une incidence sur les pages qui le référencent.

### Attributs de modèle {#template-attributes}

Les attributs suivants d’un modèle peuvent être modifiés :

#### Structure {#template-structure}

Les composants ajoutés à la [structure](#editing-a-template-structure-template-author) ne peuvent pas être déplacés/supprimés dans les pages créées par les créateurs de pages. Si vous souhaitez que les créateurs de pages puissent ajouter et supprimer des composants aux pages créées, vous devez ajouter un système de paragraphes dans le modèle.

Lorsque les composants sont verrouillés, vous pouvez ajouter du contenu qui ne peut pas être modifié par les auteurs et autrices de pages. Vous pouvez déverrouiller des composants pour définir le [contenu initial](#editing-a-template-initial-content-author).

>[!NOTE]
>
>En mode Structure, les composants qui sont le parent d’un composant déverrouillé ne peuvent pas être déplacés, coupés ou supprimés.

#### Contenu initial {#template-initial-content}

Lorsqu’un composant a été déverrouillé, vous pouvez définir le [contenu initial](#editing-a-template-initial-content-author) copié dans les pages créées à partir du modèle. Ces composants déverrouillés peuvent être modifiés dans les pages créées.

>[!NOTE]
>
>En mode **Contenu initial** (et dans les pages créées), les composants déverrouillés qui possèdent un parent accessible (c’est-à-dire, les composants dans un conteneur de mises en page) peuvent être supprimés.

#### Disposition {#template-layout}

Vous pouvez prédéfinir la [disposition](#editing-a-template-layout-template-author) du modèle pour les formats d’appareil de votre choix. Le mode **Disposition** pour la création de modèles comporte la même fonctionnalité que le mode [**Disposition** pour la création de pages](/help/sites-cloud/authoring/page-editor/responsive-layout.md#defining-layouts-layout-mode).

#### Politiques de page {#template-page-policies}

Dans le cadre des [politiques de page](#page-policies), vous pouvez attribuer des politiques de page prédéfinies à la page. Ces politiques de page définissent les différentes configurations de conception.

#### Styles {#template-styles}

Le système de style permet à un auteur de modèles de définir des classes de style dans la politique de contenu d’un composant, de façon à pouvoir sélectionner ces classes lors de la modification du composant sur une page. Ces styles peuvent être des variantes visuelles d’un composant, le rendant ainsi plus flexible.

Pour plus d’informations, consultez la [documentation du système de style](/help/sites-cloud/authoring/page-editor/style-system.md).

### Modification d’un modèle - Structure - Créateur de modèles {#editing-a-template-structure-template-author}

En mode **Structure**, vous définissez les composants et le contenu de votre modèle, ainsi qu’une politique pour le modèle et ses composants.

* Les composants définis dans la structure du modèle ne peuvent pas être déplacés sur une page créée ni supprimés des pages créées.
* Si vous souhaitez que les personnes créant les pages puissent ajouter et supprimer des composants, ajoutez un système de paragraphes au modèle.
* Les composants peuvent être déverrouillés (et reverrouillés) pour que vous puissiez définir le [contenu initial](#editing-a-template-initial-content-author).
* Les politiques de conception des composants et de la page sont définies.

![Structure de page de l’éditeur de modèles](/help/sites-cloud/authoring/assets/templates-page-structure.png)

Plusieurs actions peuvent être entreprises dans le mode **Structure** de l’éditeur de modèles, ainsi que plusieurs fonctionnalités pour vous aider :

#### Ajout de composants {#add-components}

Plusieurs mécanismes permettent d’ajouter des composants au modèle :

* Depuis le navigateur **Composants** dans le panneau latéral.
* Avec l’option **Insérer le composant** disponible dans la barre d’outils des composants figurant déjà dans le modèle ou la zone **Faire glisser les composants ici**.
* En faisant glisser une ressource (à partir de la fonction **Ressources** dans le panneau latéral) directement sur le modèle pour générer le composant approprié in situ.

Une fois ajouté, chaque composant est marqué par :

* Une bordure
* Une marque pour afficher le type de composant
* Une marque indiquant le moment où le composant a été déverrouillé

>[!NOTE]
>
>Lorsque vous ajoutez un composant **Titre** prêt à l’emploi au modèle, il contient le texte **structure** par défaut.
>
>Si vous le modifiez et que vous ajoutez votre propre texte, le texte mis à jour est utilisé pour les pages créées à partir du modèle.
>
>Si vous laissez le texte par défaut (structure), le titre propose par défaut le nom de la page suivante.

>[!NOTE]
>
>Même si l’ajout de composants et de ressources à un modèle n’est pas identique à des actions comparables lors de la [création de pages](/help/sites-cloud/authoring/page-editor/edit-content.md), il présente de nombreuses similitudes avec ces actions.

#### Actions des composants {#component-actions}

Agissez sur les composants une fois qu’ils ont été ajoutés au modèle. Chaque instance individuelle dispose d’une barre d’outils qui permet d’accéder aux actions disponibles. La barre d’outils dépend du type de composant.

![Barre d’outils d’actions d’un composant de modèle](/help/sites-cloud/authoring/assets/templates-component-actions.png)

Elle peut également dépendre des actions exécutées. Par exemple, lorsqu’une politique a été associée au composant, l’icône de configuration de la conception est disponible.

#### Modification et configuration {#edit-and-configure}

Avec ces deux actions, vous pouvez ajouter du contenu aux composants.

#### Bordure indiquant la structure {#border-to-indicate-structure}

Lorsque vous travaillez en mode **Structure**, une bordure orange indique le composant actuellement sélectionné. Une ligne pointillée indique également le composant parent.

#### Politique et propriétés (générales) {#policy-and-properties-general}

Les politiques de contenu (ou de conception) définissent les propriétés de conception d’un composant. Par exemple, les composants disponibles ou les dimensions minimales/maximales. Ces politiques s’appliquent au modèle (et aux pages créées avec le modèle).

Créez une politique de contenu ou sélectionnez-en une existante pour un composant.

![Bouton Politique de contenu](/help/sites-cloud/authoring/assets/templates-content-policy-button.png)

Cela permet de définir les détails de la conception.

![Politique de contenu](/help/sites-cloud/authoring/assets/template-content-policy.png)

La fenêtre de configuration est divisée en deux.

* Dans la partie gauche de la boîte de dialogue, sous **Politique**, vous pouvez sélectionner une politique existante ou en sélectionner une existante.
* Dans la partie droite de la boîte de dialogue, sous **Propriétés**, vous pouvez définir les propriétés spécifiques au type de composant.

Les propriétés disponibles dépendent du composant sélectionné. Par exemple, pour un composant de texte, les propriétés définissent les options de copier-coller, de mise en forme et de style de paragraphe, entre autres options.

##### Politique {#policy}

Les politiques de contenu (ou de conception) définissent les propriétés de conception d’un composant. Par exemple, les composants disponibles ou les dimensions minimales/maximales. Elles s’appliquent au modèle (et aux pages créées avec le modèle).

Sous **Politique** vous pouvez sélectionner une politique existante à appliquer au composant au moyen de la liste déroulante.

![Sélectionner une politique](/help/sites-cloud/authoring/assets/templates-policy-selector.png)

Vous pouvez ajouter une nouvelle politique en cliquant sur le bouton d’ajout en regard de la liste déroulante **Sélectionner une politique**. Donnez un nouveau titre dans le champ **Titre de la politique**.

![Bouton Ajouter une politique](/help/sites-cloud/authoring/assets/templates-add-policy-button.png)

La politique existante sélectionnée dans la liste déroulante **Sélectionner une politique** peut être copiée en tant que nouvelle politique à l’aide du bouton Copier en regard de la liste déroulante. Donnez un nouveau titre dans le champ **Titre de la politique**. Par défaut, la politique copiée est intitulée **Copie de X**, X étant le titre de la politique copiée.

![Bouton Copier la politique](/help/sites-cloud/authoring/assets/templates-copy-policy-button.png)

Vous pouvez saisir la description de la politique dans le champ **Description de la politique** (facultatif).

Dans la section **Autres modèles utilisant également la politique sélectionnée** vous pouvez facilement voir quels autres modèles utilisent la politique sélectionnée dans la liste déroulante **Sélectionner une politique**.

![Utilisation d’une politique existante](/help/sites-cloud/authoring/assets/templates-policy-use.png)

>[!NOTE]
>
>Si plusieurs composants du même type sont ajoutés comme contenu initial, la même politique s’applique à tous les composants.

##### Propriétés {#properties}

Sous l’en-tête **Propriétés**, vous pouvez définir les paramètres du composant. Le titre comporte deux onglets :

* Principal
* Fonctions

###### Principal {#main}

Sur l’onglet **Principal**, les paramètres les plus importants du composant sont définis.

Par exemple, pour un composant d’image, les largeurs autorisées peuvent être définies, ainsi que l’activation du chargement différé.

Si un paramètre permet plusieurs configurations, sélectionnez le bouton **Ajouter** pour ajouter une autre configuration.

![Bouton Ajouter.](/help/sites-cloud/authoring/assets/templates-add-button.png)

Pour supprimer une configuration, cliquez sur le bouton **Supprimer** situé à droite de la configuration.

Pour supprimer une configuration, sélectionnez le bouton **Supprimer**.

![Bouton Supprimer](/help/sites-cloud/authoring/assets/templates-delete-button.png)

###### Fonctions {#features}

L’onglet **Fonctions** permet d’activer ou de désactiver des fonctions supplémentaires du composant.

Par exemple, pour un composant d’image, vous pouvez définir les proportions de recadrage et les orientations d’image autorisées, puis indiquer si les chargements sont autorisés.

![Onglet Fonctions](/help/sites-cloud/authoring/assets/templates-features-tab.png)

>[!CAUTION]
>
>Dans AEM, les rapports de recadrage sont définis comme **hauteur/largeur**. Cela diffère de la définition conventionnelle de la largeur/hauteur, à des fins de compatibilité avec les versions héritées. Les utilisateurs de la création de pages ne percevront aucune différence à condition que vous définissiez clairement le **Nom**, car c’est ce dernier qui s’affiche dans l’interface utilisateur.

>[!NOTE]
>
>[Les politiques de contenu pour les composants impliquant la mise en œuvre de l’éditeur de texte enrichi](/help/implementing/developing/extending/rich-text-editor.md) peuvent uniquement être définies pour les options accessibles par les paramètres de l’interface utilisateur, via ses propres paramètres d’interface utilisateur. 

#### Stratégie et propriétés (conteneur de mise en page) {#policy-and-properties-layout-container}

Les paramètres de politique et de propriétés d’un conteneur de mises en page sont similaires à l’utilisation générale, à quelques différences près.

>[!NOTE]
>
>La configuration d’une politique est obligatoire pour les composants de conteneur, car elle vous permet de définir les composants disponibles dans le conteneur.

La fenêtre de configuration est divisée en deux, comme pour l’utilisation générale de la fenêtre.

##### Politique {#policy-layout}

Les politiques de contenu (ou de conception) définissent les propriétés de conception d’un composant. Par exemple, les composants disponibles ou les dimensions minimales/maximales. Elles s’appliquent au modèle (et aux pages créées avec le modèle).

Sous **Politique**, vous pouvez sélectionner, dans le menu déroulant, une politique à appliquer au composant. Cela fonctionne exactement comme dans l’utilisation générale de la fenêtre.

##### Propriétés {#properties-layout}

Sous l’en-tête **Propriétés**, vous pouvez choisir les composants disponibles pour le conteneur de mises en page et définir leurs paramètres. Le titre se compose de trois onglets :

* Composants autorisés
* Composants par défaut
* Paramètres réactifs

###### Composants autorisés {#allowed-components}

Dans l’onglet **Composants autorisés**, vous définissez les composants disponibles pour le conteneur de mises en page.

* Les composants sont regroupés par groupes de composants, qui peuvent être développés et réduits.
* Vous pouvez sélectionner un groupe entier en cochant le nom du groupe et tout peut être désélectionné en décochant la case.
* Un signe moins représente au moins un élément, mais tous les éléments d’un groupe ne sont pas sélectionnés.
* Une recherche est disponible pour filtrer un composant par nom.
* Les nombres répertoriés à droite du nom du groupe de composants représentent le nombre total de composants sélectionnés dans ces groupes, quel que soit le filtre.

![Onglet Composants autorisés](/help/sites-cloud/authoring/assets/templates-allowed-components-tab.png)

###### Composants par défaut {#default-components}

Dans l’onglet **Composants par défaut**, vous définissez les composants qui sont automatiquement associés à des types de médias donnés. Ainsi, lorsqu’un créateur fait glisser une ressource depuis le navigateur des ressources, AEM sait avec quel composant l’associer. Seuls les composants avec des zones de dépôt sont disponibles pour une telle configuration.

Sélectionnez **Ajouter un mappage** pour ajouter un composant entièrement nouveau et un mappage de type MIME.

Sélectionnez un composant dans la liste, puis sélectionnez **Ajouter un type** pour ajouter un type MIME supplémentaire à un composant déjà mappé. Cliquez sur l’icône **Supprimer** pour supprimer un type MIME.

![Onglet Composants par défaut](/help/sites-cloud/authoring/assets/templates-default-components-tab.png)

###### Paramètres réactifs {#responsive-settings}

Dans l’onglet **Paramètres réactifs**, vous pouvez configurer le nombre de colonnes de la grille résultante du conteneur de mise en page.

#### Déverrouillage et verrouillage des composants {#unlock-and-lock-components}

Vous déverrouillez/verrouillez des composants pour définir si le contenu peut être modifié en mode **Contenu initial**.

Lorsqu’un composant a été déverrouillé :

* Un indicateur de cadenas ouvert s’affiche dans la bordure.
* La barre d’outils du composant est ajustée en conséquence.
* Le contenu déjà saisi ne s’affichera plus en mode **Structure**.
   * Le contenu déjà saisi est considéré comme du contenu initial et n’est visible qu’en mode **Contenu initial**.
* Les parents du composant déverrouillé ne peuvent être ni déplacés, ni coupés, ni supprimés.

![Bouton Verrouiller le composant](/help/sites-cloud/authoring/assets/templates-unlock-component.png)

Cela comprend le déverrouillage des composants de conteneur afin que d’autres composants puissent être ajoutés, soit en mode **Contenu initial**, soit sur les pages résultantes. Si vous avez déjà ajouté des composants/du contenu au conteneur avant de le déverrouiller, ceux-ci ne s’affichent plus en mode **Structure**, mais en mode **Contenu initial**. En mode **Structure**, seul le composant de conteneur est affiché avec sa liste de **Composants autorisés**.

![Composants autorisés](/help/sites-cloud/authoring/assets/templates-allowed-components.png)

Pour économiser de l’espace, le conteneur de mise en page ne se développe pas pour s’adapter à la liste des composants autorisés. En revanche, le conteneur se transforme en liste déroulante.

Les composants configurables s’affichent avec une icône **Politique**, sur laquelle vous pouvez appuyer ou cliquer pour modifier la politique et les propriétés de ce composant.

![Icône de composant configurable](/help/sites-cloud/authoring/assets/templates-configurable-component.png)

#### Relation avec les pages existantes {#relationship-to-existing-pages}

Si la structure est mise à jour après la création de pages en fonction du modèle, ces pages répercutent les modifications apportées au modèle. Un avertissement, ainsi que des boîtes de dialogue de confirmation, s’affichent dans la barre d’outils pour vous rappeler cette répercussion.

![Bannière d’avertissement indiquant que le modèle est en cours d’utilisation](/help/sites-cloud/authoring/assets/templates-in-use-banner.png)

### Modification d’un modèle - Contenu initial - Créateur {#editing-a-template-initial-content-author}

Le mode **Contenu initial** est utilisé pour définir le contenu qui s’affichera lors de la première création d’une page en fonction du modèle. Le contenu initial peut ensuite être modifié par les auteurs et autrices de pages.

Même si l’ensemble du contenu créé en mode **Structure** est visible en mode **Contenu initial**, seuls les composants déverrouillés peuvent être sélectionnés et modifiés.

>[!NOTE]
>
>Le mode **Contenu initial** peut être envisagé comme mode d’édition pour les pages créées avec ce modèle. Par conséquent, les politiques ne sont pas définies en mode **Contenu initial**, mais plutôt en mode [**Structure**](#editing-a-template-structure-template-author).

* Les composants déverrouillés pouvant être modifiés sont marqués. Lorsqu’ils sont sélectionnés, ils ont une bordure bleue :

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
>Le contenu initial est destiné à préparer les composants et la mise en page, point de départ de la création du contenu. Il n’est pas destiné à constituer un contenu réel laissé tel quel. De ce fait, le contenu initial ne peut pas être traduit.
>
>Si vous devez inclure du texte traduisible dans votre modèle, par exemple dans les en-têtes ou les pieds de page, vous pouvez utiliser les [fonctions de localisation des composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/localization.html?lang=fr).

### Modification d’un modèle - Disposition - Créateur de modèles {#editing-a-template-layout-template-author}

Vous pouvez définir la disposition du modèle pour différents appareils. La [mise en page réactive](/help/sites-cloud/authoring/page-editor/responsive-layout.md) pour les modèles fonctionne de la même manière que pour la création de pages.

>[!NOTE]
>
>Les modifications apportées à la mise en page se répercutent en mode **Contenu initial**, mais aucune modification n’est visible en mode **Structure**.

![Modifier la mise en page d’un modèle](/help/sites-cloud/authoring/assets/templates-edit-layout.png)

### Modification d’un modèle – Politique de page – Créateur/développeur de modèles {#editing-a-template-page-policy-template-author-developer}

La politique de page, y compris les bibliothèques clientes requises, est conservée sous l’option **Politique de page** du menu **Informations sur la page**.

Pour accéder à la boîte de dialogue **Politique de page** :

1. Dans l’**Éditeur de modèles**, sélectionnez **Informations sur la page** dans la barre d’outils, puis **Politique de page** pour ouvrir la boîte de dialogue.
1. La boîte de dialogue **Politique de page** s’ouvre. Elle est divisée en deux sections :

   * La moitié gauche définit les [politiques de page](#page-policies)
   * La moitié droite définit les [propriétés de page](#page-properties)

   ![Conception de page](/help/sites-cloud/authoring/assets/templates-page-design.png)

#### Politiques de page {#page-policies}

Vous pouvez appliquer une politique de contenu au modèle ou aux pages créées. Cette opération définit la politique de contenu pour le système de paragraphes principal dans la page.

![Politique de page](/help/sites-cloud/authoring/assets/templates-page-policy.png)

* Vous pouvez sélectionner une politique existante pour la page dans le menu déroulant **Sélectionner une politique**.

  ![Sélecteur de politique](/help/sites-cloud/authoring/assets/templates-policy-selector.png)

  Vous pouvez ajouter une nouvelle politique en cliquant sur le bouton d’ajout en regard de la liste déroulante **Sélectionner une politique**. Donnez un nouveau titre dans le champ **Titre de la politique**.

  ![Bouton Ajouter une politique](/help/sites-cloud/authoring/assets/templates-add-policy-button.png)

  La politique existante sélectionnée dans la liste déroulante **Sélectionner une politique** peut être copiée en tant que nouvelle politique à l’aide du bouton Copier en regard de la liste déroulante. Donnez un nouveau titre dans le champ **Titre de la politique**. Par défaut, la politique copiée est intitulée **Copie de X**, X étant le titre de la politique copiée.

  ![Bouton Copier la politique](/help/sites-cloud/authoring/assets/templates-copy-policy-button.png)

* Définissez le titre de la politique dans le champ **Titre de la politique**. Une politique doit comporter un titre afin de pouvoir être facilement sélectionnée dans la liste déroulante **Sélectionner une politique**.

  ![Titre de la politique](/help/sites-cloud/authoring/assets/templates-policy-title.png)

* Vous pouvez saisir la description de la politique dans le champ **Description de la politique** (facultatif).
* Dans la section **Autres modèles utilisant également la politique sélectionnée** vous pouvez facilement voir quels autres modèles utilisent la politique sélectionnée dans la liste déroulante **Sélectionner une politique**.

  ![Utilisation des politiques](/help/sites-cloud/authoring/assets/templates-policy-use.png)

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
>Bien que l’auteur du modèle puisse spécifier la politique de page sur le modèle, il doit obtenir les détails des bibliothèques côté client appropriées auprès du développeur.

### Modification d’un modèle - Propriétés de page initiales - Créateur {#editing-a-template-initial-page-properties-author}

À l’aide de l’option **Propriétés de page initiales**, vous pouvez définir les [propriétés initiales de la page](/help/sites-cloud/authoring/sites-console/page-properties.md) à utiliser lors de la création des pages.

1. Dans l’éditeur de modèles, sélectionnez **Informations sur la page** dans la barre d’outils, puis **Propriétés de page initiales** pour ouvrir la boîte de dialogue.

1. Dans la boîte de dialogue, vous pouvez définir les propriétés à appliquer aux pages créées avec ce modèle.

   ![Propriétés de page initiales des modèles](/help/sites-cloud/authoring/assets/templates-initial-properties.png)

1. Confirmez vos définitions en cliquant/appuyant sur **Terminé**.

## Bonnes pratiques {#best-practices}

Lors de la création de modèles, tenez compte des points suivants :

1. L’impact des modifications apportées au modèle une fois que les pages ont été créées à partir de ce modèle.

   Vous trouverez ci-dessous la liste des différentes opérations possibles sur les modèles, ainsi que leur répercussion sur les pages créées à partir de ces derniers :

   * Modifications apportées à la structure :

      * Elles sont immédiatement appliquées aux pages concernées.
      * La publication du modèle modifié est toujours nécessaire pour que les visiteurs et visiteuses puissent voir les modifications.

   * Modifications apportées aux politiques de contenu et aux configurations de conception :

      * Elles s’appliquent immédiatement aux pages concernées.
      * La publication des modifications est nécessaire pour que les visiteurs et visiteuses puissent voir les modifications.

   * Modifications apportées au contenu initial :

      * Elles s’appliquent uniquement aux pages créées après les modifications apportées au modèle.

   * Les modifications apportées à la mise en page dépendent du fait que le composant modifié appartient ou non aux éléments suivants :

      * Structure seule : appliquée immédiatement
      * Contenir le contenu initial : uniquement sur les pages créées après la modification

   Procédez avec prudence lors des opérations suivantes :

   * Verrouillage ou déverrouillage de composants sur des modèles activés.
   * Cela peut avoir des effets indésirables, car les pages existantes risquent de déjà l’utiliser. En règle générale :

      * Les composants déverrouillés (qui étaient verrouillés) sont manquants sur les pages existantes.
      * Les composants verrouillés (modifiables) empêchent l’affichage de ce contenu sur les pages.

   >[!NOTE]
   >
   >AEM affiche des avertissements explicites lorsque vous modifiez le statut de verrouillage des composants sur les modèles qui ne sont plus des brouillons.

1. [Créer vos propres dossiers](#creating-a-template-folder-admin) pour les modèles spécifiques à votre site.
1. [Publish vos modèles](#publishing-a-template-template-author) à partir de la console **[Modèles]**(/help/sites-cloud/administering/templates-console.md).
