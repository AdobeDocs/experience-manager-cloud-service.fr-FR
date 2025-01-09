---
title: Création de contenu avec l’éditeur universel
description: Découvrez à quel point il est facile et intuitif pour les personnes en charge de la création de créer du contenu à l’aide de l’éditeur universel.
exl-id: 15fbf5bc-2e30-4ae7-9e7f-5891442228dd
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: e4db952e8284dba578c6b3ac86405e9ab640e7c0
workflow-type: tm+mt
source-wordcount: '1378'
ht-degree: 20%

---


# Création de contenu avec l’éditeur universel {#authoring}

Découvrez à quel point il est facile et intuitif pour les personnes en charge de la création de créer du contenu à l’aide de l’éditeur universel.

## Présentation {#introduction}

L’éditeur universel permet de modifier n’importe quel aspect de contenu dans n’importe quelle mise en œuvre pour que vous puissiez fournir des expériences exceptionnelles, d’augmenter la vitesse du contenu et d’offrir une expérience de développement à la pointe de la technologie.

Pour ce faire, l’éditeur universel fournit aux personnes en charge de la création de contenu une interface utilisateur intuitive qui nécessite une formation minimale pour se lancer et commencer à modifier le contenu. Ce document décrit l’expérience de création de l’éditeur universel.

>[!NOTE]
>
>Ce document suppose que vous connaissez déjà la procédure d’accès et de navigation dans l’éditeur universel. Si ce n’est pas le cas, consultez le document [Accès à l’éditeur universel et navigation dans cet éditeur.](/help/sites-cloud/authoring/universal-editor/navigation.md)

>[!TIP]
>
>Pour une présentation plus détaillée de l’éditeur universel, consultez le document [Présentation de l’éditeur universel.](/help/implementing/universal-editor/introduction.md)

## Modification du contenu {#editing-content}

La modification du contenu est simple et intuitive. Lorsque vous placez le pointeur de la souris sur le contenu de l’éditeur, le contenu modifiable se met en surbrillance dans un fin contour bleu.

![Le contenu modifiable est mis en surbrillance dans une case bleue.](assets/editable-content.png)

>[!TIP]
>
>Par défaut, appuyer ou cliquer sur du contenu le sélectionne pour le modifier. Si vous souhaitez parcourir votre contenu en suivant les liens, passez en [mode Aperçu](/help/sites-cloud/authoring/universal-editor/navigation.md#preview-mode).

Selon le contenu que vous sélectionnez, vous pouvez disposer de différentes options de modification statique et d’informations et d’options supplémentaires pour le contenu dans le panneau [propriétés](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail).

### Modification de texte brut {#edit-plain-text}

Vous pouvez modifier le texte en place en double-cliquant ou en appuyant deux fois sur le composant.

![Modification du contenu](assets/editing-content.png)

Le contour bleu fin se transforme en contour bleu foncé pour indiquer la sélection et un curseur s’affiche. Apportez vos modifications, puis appuyez sur Entrée/Retour ou sélectionnez en dehors de la zone de texte pour les enregistrer.

Lorsque vous sélectionnez le composant de texte, ses détails s’affichent dans le panneau [Propriétés).](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail) Vous pouvez également modifier le texte dans le panneau.

![Modification de texte dans le panneau des propriétés](assets/ue-editing-text-component-rail.png)

En outre, les détails de votre texte sont disponibles dans le panneau des propriétés. Les modifications sont automatiquement enregistrées une fois que le focus quitte le champ modifié dans le panneau des propriétés.

### Modification de texte enrichi {#edit-rich-text}

Vous pouvez modifier le texte en place en double-cliquant ou en appuyant deux fois sur le composant.

![Modification d’un composant de texte enrichi](assets/rich-text-editing.png)

Pour votre commodité, les options de mise en forme et les détails de votre texte sont disponibles à deux endroits.

#### Le menu contextuel {#context-menu}

Le menu contextuel s’ouvre au-dessus du bloc de texte enrichi et offre des options de mise en forme de base en contexte. En raison des limitations d’espace, certaines options peuvent être masquées derrière le bouton représentant des points de suspension.

![Menu contextuel Texte enrichi](assets/rich-text-context-menu.png)

Les modifications sont automatiquement enregistrées une fois que le focus quitte le champ modifié.

#### Le Panneau Propriétés {#properties-rail}

Le panneau [propriétés](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail) affiche un élément pour le texte sélectionné. Appuyez sur l’entrée pour ouvrir une boîte de dialogue présentant une zone de travail plus grande pour modifier le texte.

![Boîte de dialogue d’édition de texte enrichi](assets/rich-text-canvas.png)

Appuyez ou cliquez sur **Annuler** ou **Terminé** pour ignorer ou enregistrer les modifications, respectivement.

### Modification de médias {#edit-media}

Vous pouvez en afficher les détails dans le panneau [propriétés](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail).

![Modification de médias](assets/ue-edit-media.png)

1. Appuyez ou cliquez sur l’aperçu de l’image sélectionnée dans le panneau Propriétés.
1. La fenêtre [sélecteur de ressources](/help/assets/overview-asset-selector.md#using-asset-selector) s’ouvre pour vous permettre de sélectionner une ressource.
1. Sélectionnez pour sélectionner une nouvelle ressource.
1. Sélectionnez **Sélectionner** pour revenir au panneau des propriétés où la ressource a été remplacée.

Les modifications sont automatiquement enregistrées dans votre contenu.

### Modification de fragments de contenu {#edit-content-fragment}

Si vous sélectionnez un [fragment de contenu](/help/sites-cloud/administering/content-fragments/overview.md) vous pouvez modifier ses détails dans le panneau [propriétés.](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail)

![Modification d’un fragment de contenu](assets/ue-edit-cf.png)

Les champs définis dans le modèle de contenu du fragment de contenu sélectionné sont affichés et modifiables dans le panneau des propriétés.

Si vous sélectionnez un champ associé à un fragment de contenu, le fragment de contenu se charge dans le panneau Composants et le champ est automatiquement défilé vers .

Les modifications sont automatiquement enregistrées une fois que le focus quitte le champ modifié dans le panneau des propriétés.

Si vous souhaitez plutôt modifier votre fragment de contenu dans l’[éditeur de fragment de contenu](/help/sites-cloud/administering/content-fragments/authoring.md), appuyez ou cliquez sur le bouton [**Ouvrir dans l’éditeur de fragment de contenu** ](/help/sites-cloud/authoring/universal-editor/navigation.md#edit) dans le panneau des propriétés.

>[!TIP]
>
>Utilisez les touches de raccourci `e` modifier le fragment de contenu sélectionné dans l’éditeur de fragment de contenu.

Selon les besoins de votre workflow, vous pouvez modifier le fragment de contenu dans l’éditeur universel ou directement dans l’éditeur de fragment de contenu.

>[!NOTE]
>
>L’éditeur universel [valide les champs de fragment de contenu en fonction de leurs modèles](/help/assets/content-fragments/content-fragments-models.md#validation) ce qui vous permet d’appliquer des règles d’intégrité des données telles que des modèles d’expression régulière et des contraintes d’unicité.
>
>Cela garantit que votre contenu répond aux besoins spécifiques de l’entreprise avant d’être publié.

### Ajout de composants aux conteneurs {#adding-components}

1. Sélectionnez un composant de conteneur dans l’[arborescence de contenu](/help/sites-cloud/authoring/universal-editor/navigation.md#content-tree-mode) ou dans l’éditeur.

   ![Sélection d’un composant à ajouter à un conteneur](assets/ue-add-component.png)

1. Sélectionnez ensuite l’icône d’ajout dans le panneau des propriétés.

   ![Sélectionner l’icône d’ajout](assets/add-icon.png)

Le composant est inséré dans le conteneur et peut être modifié dans l’éditeur.

>[!TIP]
>
>Utilisez la touche de raccourci `a` ajouter un composant au conteneur sélectionné.

### Duplication de composants dans des conteneurs {#duplicating-components}

1. Sélectionnez un composant dans un conteneur à l’aide de l’[arborescence de contenu](/help/sites-cloud/authoring/universal-editor/navigation.md#content-tree-mode) ou de l’éditeur.
1. Sélectionnez ensuite l’icône **Dupliquer** dans le panneau des propriétés.

   ![Sélection d’un composant à ajouter à un conteneur](assets/ue-duplicate-component.png)
1. Le composant est dupliqué et inséré sous le composant sélectionné.

Le composant est inséré dans le conteneur et peut être modifié dans l’éditeur.

### Suppression de composants de conteneurs {#deleting-components}

1. Sélectionnez un composant de conteneur dans l’[arborescence de contenu](/help/sites-cloud/authoring/universal-editor/navigation.md#content-tree-mode) ou dans l’éditeur.
1. Sélectionnez l’icône chevron du conteneur pour développer son contenu dans l’arborescence de contenu.
1. Ensuite, dans l’arborescence de contenu, sélectionnez un composant dans le conteneur .
1. Sélectionnez l’icône de suppression dans le panneau des propriétés.

   ![Supprimer un composant](assets/ue-delete-component.png)

Composant sélectionné supprimé.

>[!TIP]
>
>Utilisez la touche de raccourci `Shift+Backspace` supprimer le composant sélectionné de son conteneur.

### Réorganisation des composants dans les conteneurs {#reordering-components}

1. S’il n’est pas déjà en mode [arborescence de contenu](/help/sites-cloud/authoring/universal-editor/navigation.md#content-tree-mode) basculez-le.
1. Sélectionnez un composant de conteneur dans l’arborescence de contenu ou dans l’éditeur.
1. Sélectionnez l’icône chevron du conteneur pour développer son contenu dans l’arborescence de contenu.
1. Faites glisser les icônes des poignées en regard des composants du conteneur pour les réorganiser. Faites glisser les composants pour les réorganiser dans le conteneur.

   ![Réorganisation des composants](assets/ue-reordering-components.png)

1. Le composant déplacé devient gris dans l’arborescence de contenu, tandis que le point d’insertion est représenté par une ligne bleue. Libérez le composant pour le placer à son nouvel emplacement.

Les composants sont réorganisés dans l’arborescence de contenu et dans l’éditeur.

>[!NOTE]
>
>Les composants ne peuvent pas être déplacés entre les conteneurs si un [filtre de composant](/help/implementing/universal-editor/customizing.md#filtering-components) différent est défini entre les conteneurs source et cible.

## Prévisualisation du contenu {#previewing-content}

Une fois le contenu modifié, vous aimez généralement le parcourir pour voir à quoi il ressemble dans le contenu d’autres pages. En [mode Aperçu](/help/sites-cloud/authoring/universal-editor/navigation.md#preview-mode), vous pouvez cliquer sur les liens pour parcourir votre contenu comme le ferait un lecteur ou une lectrice. Le contenu est rendu dans l’éditeur tel qu’il serait publié.

En mode Aperçu, le fait d’appuyer ou de cliquer sur le contenu fait réagir ce dernier comme il le ferait avec un lecteur ou une lectrice du contenu. Si vous souhaitez sélectionner le contenu à modifier, basculez en dehors du [mode d’aperçu](/help/sites-cloud/authoring/universal-editor/navigation.md#preview-mode).

## Ressources supplémentaires {#additional-resources}

Pour savoir comment publier du contenu avec l’éditeur universel, consultez ce document.

* [Publication de contenu avec l’éditeur universel](publishing.md) - Découvrez comment l’éditeur universel publie du contenu et comment vos applications peuvent gérer le contenu publié.

Pour en savoir plus sur les détails techniques de l’éditeur universel, consultez ces documents de développement.

* [Présentation de l’éditeur universel](/help/implementing/universal-editor/introduction.md) - Découvrez comment l’éditeur universel permet de modifier n’importe quel aspect d’un contenu dans n’importe quelle implémentation afin de fournir des expériences exceptionnelles, d’augmenter la vitesse du contenu et d’offrir une expérience de développement à la pointe de la technologie.
* [Prise en main de l’éditeur universel dans AEM](/help/implementing/universal-editor/getting-started.md) - Découvrez comment accéder à l’éditeur universel et comment commencer à instrumenter votre première application AEM pour l’utiliser.
* [Architecture de l’éditeur universel](/help/implementing/universal-editor/architecture.md) - Découvrez l’architecture de l’éditeur universel et le flux de données entre ses services et calques.
* [Attributs et types](/help/implementing/universal-editor/attributes-types.md) - Découvrez les attributs et les types de données requis par l’éditeur universel.
* [Authentification de l’éditeur universel](/help/implementing/universal-editor/authentication.md) - Découvrez comment l’éditeur universel s’authentifie.

## Modification de l’héritage des composants {#inheritance}

L’héritage est le mécanisme par lequel le contenu peut être lié, de sorte que la modification de l’un modifie automatiquement l’autre.

À l’aide de l’éditeur universel, vous pouvez annuler l’héritage pour le contenu en mettant simplement à jour le contenu. L’éditeur désactive automatiquement l’héritage pour toutes les modifications apportées par les auteurs sur cette page, en s’assurant que le contenu modifié est conservé lorsque les mises à jour sont synchronisées à partir du plan directeur.

Pour plus d’informations sur le fonctionnement de l’héritage à l’aide de l’éditeur universel, consultez le document [Héritage de contenu dans l’éditeur universel](/help/sites-cloud/authoring/universal-editor/inheritance.md).
