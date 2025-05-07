---
title: Création de contenu avec l’éditeur universel
description: Découvrez à quel point il est facile et intuitif pour les personnes en charge de la création de créer du contenu à l’aide de l’éditeur universel.
exl-id: 15fbf5bc-2e30-4ae7-9e7f-5891442228dd
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 36a27d7fb36c9832b78c13d7544a43df2cbd0fa0
workflow-type: tm+mt
source-wordcount: '2222'
ht-degree: 9%

---


# Création de contenu avec l’éditeur universel {#authoring}

Découvrez à quel point il est facile et intuitif pour les personnes en charge de la création de créer du contenu à l’aide de l’éditeur universel.

## Présentation {#introduction}

L’éditeur universel permet de modifier n’importe quel aspect de contenu dans n’importe quelle mise en œuvre afin que vous puissiez offrir des expériences exceptionnelles et augmenter la vitesse du contenu.

Pour ce faire, l’éditeur universel fournit aux personnes en charge de la création de contenu une interface utilisateur intuitive qui nécessite une formation minimale pour se lancer et commencer à modifier le contenu. Ce document décrit l’expérience de création de l’éditeur universel.

>[!NOTE]
>
>Ce document suppose que vous connaissez déjà la procédure d’accès et de navigation dans l’éditeur universel. Si ce n’est pas le cas, consultez [Accès à l’éditeur universel et navigation dans cet éditeur](/help/sites-cloud/authoring/universal-editor/navigation.md).

>[!TIP]
>
>Pour une présentation plus détaillée de l’éditeur universel, voir [Présentation de l’éditeur universel](/help/implementing/universal-editor/introduction.md).

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

Lorsque vous sélectionnez le composant de texte, ses détails s’affichent dans le panneau [Propriétés](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail). Vous pouvez également modifier le texte dans le panneau.

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

Vous pouvez afficher les détails dans le panneau [Propriétés](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail).

![Modification de médias](assets/ue-edit-media.png)

1. Appuyez ou cliquez sur l’aperçu de l’image sélectionnée dans le panneau Propriétés.
1. La fenêtre [sélecteur de ressources](/help/assets/overview-asset-selector.md#using-asset-selector) s’ouvre pour vous permettre de sélectionner une ressource.
1. Sélectionnez pour sélectionner une nouvelle ressource.
1. Sélectionnez **Sélectionner** pour revenir au panneau des propriétés où la ressource a été remplacée.

Les modifications sont automatiquement enregistrées dans votre contenu.

### Modification de fragments de contenu {#edit-content-fragment}

Si vous sélectionnez un [fragment de contenu](/help/sites-cloud/administering/content-fragments/overview.md), vous pouvez modifier ses détails dans le panneau [propriétés](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail).

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

### Réorganisation des composants {#reordering-components}

1. S’il n’est pas déjà en [mode arborescence de contenu](/help/sites-cloud/authoring/universal-editor/navigation.md#content-tree-mode), basculez-le.
1. Sélectionnez un composant de conteneur dans l’arborescence de contenu ou dans l’éditeur.
1. Sélectionnez l’icône chevron du conteneur pour développer son contenu dans l’arborescence de contenu.
1. Faites glisser les icônes des poignées en regard des composants du conteneur pour les réorganiser. Faites glisser les composants pour les réorganiser dans le conteneur.

   ![Réorganisation des composants](assets/ue-reordering-components.png)

1. Le composant déplacé devient gris dans l’arborescence de contenu, tandis que le point d’insertion est représenté par une ligne bleue. Libérez le composant pour le placer à son nouvel emplacement.

Les composants sont réorganisés dans l’arborescence de contenu et dans l’éditeur.

>[!NOTE]
>
>Les composants ne peuvent être déplacés entre des conteneurs que si les conteneurs cibles [filtre de composant](/help/implementing/universal-editor/filtering.md) autorisent le composant sélectionné.

## Prévisualisation du contenu {#previewing-content}

Une fois le contenu modifié, vous aimez généralement le parcourir pour voir à quoi il ressemble dans le contenu d’autres pages. En [mode Aperçu](/help/sites-cloud/authoring/universal-editor/navigation.md#preview-mode), vous pouvez cliquer sur les liens pour parcourir votre contenu comme le ferait un lecteur ou une lectrice. Le contenu est rendu dans l’éditeur tel qu’il serait publié.

En mode Aperçu, le fait d’appuyer ou de cliquer sur le contenu fait réagir ce dernier comme il le ferait avec un lecteur ou une lectrice du contenu. Si vous souhaitez sélectionner le contenu à modifier, basculez en dehors du [mode d’aperçu](/help/sites-cloud/authoring/universal-editor/navigation.md#preview-mode).

## Modification de l’héritage des composants {#inheritance}

L’héritage est le mécanisme par lequel le contenu peut être lié, de sorte que la modification de l’un modifie automatiquement l’autre.

À l’aide de l’éditeur universel, vous pouvez annuler l’héritage pour le contenu en mettant simplement à jour le contenu. L’éditeur désactive automatiquement l’héritage pour toutes les modifications apportées par les auteurs sur cette page, en s’assurant que le contenu modifié est conservé lorsque les mises à jour sont synchronisées à partir du plan directeur.

Si l’extension **AEM Multi-Site-Management (MSM)** est activée pour votre programme, vous disposez d’[options de barre d’outils supplémentaires](#inheritance-extension) pour afficher et modifier le statut d’héritage d’un composant individuel dans l’éditeur universel.

Pour plus d’informations sur le fonctionnement de l’héritage à l’aide de l’éditeur universel, consultez [Héritage de contenu dans l’éditeur universel](/help/sites-cloud/authoring/universal-editor/inheritance.md).

## Fonctionnalités facultatives de la barre d’outils {#toolbar-options}

D’autres fonctionnalités sont disponibles sous forme d’extensions de l’éditeur universel pour vous aider à gérer vos pages et votre contenu. [Ces extensions doivent être activées dans votre programme par un administrateur](/help/implementing/universal-editor/extending.md) avant d’être visibles par vous en tant qu’auteur de contenu dans [la barre d’outils de l’éditeur universel.](/help/sites-cloud/authoring/universal-editor/navigation.md#universal-editor-toolbar)

### Héritage {#inheritance-extension}

L’extension **AEM Multi-Site-Management (MSM)** affiche le statut d’héritage actuel du composant sélectionné et vous permet de [interrompre ou rétablir l’héritage.](/help/sites-cloud/authoring/universal-editor/inheritance.md)

L’icône **Héritage installé** de la barre d’outils de l’éditeur universel indique que l’héritage est toujours actif pour le composant sélectionné.

![Icône Hériter installé](assets/inheritance-installed-icon.png)

Appuyez ou cliquez sur l’icône pour rompre l’héritage du composant sélectionné. L’héritage est automatiquement rompu si vous modifiez le composant.

L’icône **Héritage rompu** indique que l’héritage a été rompu pour le composant sélectionné.

![Icône d’héritage rompu](assets/inheritance-broken-icon.png)

Appuyez ou cliquez sur l’icône pour rétablir l’héritage pour le composant sélectionné. Vous devez recharger la page pour actualiser le contenu afin d’afficher le contenu hérité.

Pour plus d’informations sur la manière d’activer cette extension, [consultez la documentation d’Extension Manager.](https://developer.adobe.com/uix/docs/extension-manager/)

>[!NOTE]
>
>Les icônes **Héritage installé** et **Héritage rompu** ne s’affichent que lorsqu’un composant a été sélectionné et que la page est basée sur un plan directeur.

>[!NOTE]
>
>L’extension **AEM Multi-Site-Management (MSM)** fonctionne uniquement pour les pages, et non pour les fragments de contenu.

### Accès aux propriétés de page {#page-properties}

L’extension **Propriétés de page AEM** permet un accès rapide à la fenêtre [Propriétés de page](/help/sites-cloud/authoring/sites-console/page-properties.md) de la page en cours de modification.

![Icône Propriétés de la page](assets/page-properties-icon.png)

Appuyez ou cliquez sur l’icône **Propriétés de page** dans la barre d’outils de l’éditeur universel pour ouvrir les propriétés de page de la page dans un nouvel onglet du navigateur.

Pour plus d’informations sur la manière d’activer cette extension, [consultez la documentation d’Extension Manager.](https://developer.adobe.com/uix/docs/extension-manager/)

>[!NOTE]
>
>L’extension **Propriétés de page AEM** fonctionne uniquement pour les pages, et non pour les fragments de contenu.

### Accès à la console Sites {#sites-console}

L’extension **AEM Site Admin Extension** permet un accès rapide à la page en cours de modification dans la console [Sites d’AEM](/help/sites-cloud/authoring/sites-console/introduction.md), ce qui vous permet de parcourir l’arborescence du site ou d’effectuer des actions au niveau de la page dans la console.

![Icône Ouvrir dans l’administration de sites](assets/open-in-site-admin-icon.png)

Appuyez ou cliquez sur l’icône pour ouvrir la console Sites dans un nouvel onglet du navigateur, et accédez à la page qui se trouve actuellement dans l’éditeur.

Pour plus d’informations sur la manière d’activer cette extension, [consultez la documentation d’Extension Manager.](https://developer.adobe.com/uix/docs/extension-manager/)

### Verrouillage et déverrouillage de pages {#locking-pages}

L’extension de verrouillage de page **AEM** affiche le statut de verrouillage actuel de la page dans l’éditeur et vous permet de [verrouiller ou déverrouiller la page](/help/sites-cloud/authoring/sites-console/managing-pages.md#locking-a-page).

L’icône **Déverrouillé** de la barre d’outils de l’éditeur universel indique que la page qui se trouve actuellement dans l’éditeur n’est pas verrouillée.

![Icône déverrouillée](assets/unlocked-icon.png)

Appuyez ou cliquez sur l’icône pour verrouiller la page.

L’icône **Verrouillé** de la barre d’outils de l’éditeur universel indique que la page qui se trouve actuellement dans l’éditeur est verrouillée. Pointez votre souris sur l’icône d’info-bulle pour indiquer l’utilisateur qui a verrouillé la page.

![Icône verrouillée](assets/locked-icon.png)

Appuyez ou cliquez sur l’icône pour déverrouiller la page si vous êtes l’utilisateur ou l’utilisatrice qui l’a verrouillée.

Pour plus d’informations sur la manière d’activer cette extension, [consultez la documentation d’Extension Manager.](https://developer.adobe.com/uix/docs/extension-manager/)

>[!NOTE]
>
>L’extension de verrouillage de page **AEM** fonctionne uniquement pour les pages, et non pour les fragments de contenu.

### Workflows {#workflows}

L’extension **AEM Workflows** vous permet de [démarrer un workflow](/help/sites-cloud/authoring/workflows/overview.md) sur la page qui se trouve actuellement dans l’éditeur.

![ Icône Workflows ](assets/workflows-icon.png)

Appuyez ou cliquez sur l’icône **Workflows** dans la barre d’outils de l’éditeur universel pour ouvrir la fenêtre modale **Démarrer un workflow**. La fenêtre répertorie le contenu possible auquel vous pouvez appliquer un workflow.

![Boîte de dialogue modale Démarrer un workflow](assets/start-a-workflow.png)

1. Dans la liste déroulante **Modèle de workflow**, sélectionnez le workflow à appliquer.
1. Fournissez une description du workflow dans le champ **Nom**.
1. Dans la liste **Contenu à inclure dans le workflow**, utilisez les cases à cocher pour définir le contenu à inclure dans le workflow.
1. Appuyez ou cliquez sur **Démarrer le workflow** pour démarrer le workflow ou sur **Fermer** pour abandonner.

Pour plus d’informations sur la manière d’activer cette extension, [consultez la documentation d’Extension Manager.](https://developer.adobe.com/uix/docs/extension-manager/)

### Connexion du développeur {#developer-login}

L’extension de connexion au développement **AEM Universal Editor** est utile pour les développeurs et développeuses qui développent localement, ce qui permet de s’authentifier de manière pratique auprès d’un SDK AEM local à des fins de test.

![Icône de connexion au développeur](assets/developer-login-icon.png)

Appuyez ou cliquez sur l’icône **Ouverture de session du développeur** dans la barre d’outils de l’éditeur universel pour fournir vos informations de connexion locales afin de vous connecter à votre SDK AEM local.

![Boîte de dialogue modale de connexion du développeur](assets/developer-login.png)

Pour plus d’informations sur la manière d’activer cette extension, [consultez la documentation d’Extension Manager.](https://developer.adobe.com/uix/docs/extension-manager/)

## Fonctionnalités du panneau Propriétés facultatives {#properties-panel-options}

D’autres fonctionnalités sont disponibles sous forme d’extensions de l’éditeur universel pour vous aider à gérer davantage le contenu de votre page. [Ces extensions doivent être activées dans votre programme par un administrateur](/help/implementing/universal-editor/extending.md) avant d’être visibles par vous en tant qu’auteur de contenu dans [le panneau des propriétés de l’éditeur universel.](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-rail)

### Générer des variations {#generate-variations}

L’extension **Generate Variations** vous permet d’utiliser l’intelligence artificielle (IA) générative pour créer des variations pour votre contenu directement dans le panneau des propriétés.

![Icône Générer des variations](assets/generate-variations-icon.png)

Appuyez ou cliquez sur l’icône **Générer des variations** dans le panneau des propriétés de l’éditeur universel pour recevoir des recommandations et créer des variations. Consultez le document [Générer des variations - Intégré aux éditeurs AEM](/help/generative-ai/generate-variations-integrated-editor.md) pour plus d’informations sur le fonctionnement de la génération de variations.

Pour plus d’informations sur la manière d’activer cette extension, [consultez la documentation d’Extension Manager.](https://developer.adobe.com/uix/docs/extension-manager/)

## Ressources supplémentaires {#additional-resources}

Pour savoir comment publier du contenu avec l’éditeur universel, consultez ce document.

* [Publication de contenu avec l’éditeur universel](publishing.md) - Découvrez comment l’éditeur universel publie du contenu et comment vos applications peuvent gérer le contenu publié.

Pour en savoir plus sur les détails techniques de l’éditeur universel, consultez ces documents de développement.

* [Présentation de l’éditeur universel](/help/implementing/universal-editor/introduction.md) - Découvrez comment l’éditeur universel permet de modifier n’importe quel aspect de contenu dans n’importe quelle mise en œuvre afin que vous puissiez offrir des expériences exceptionnelles et augmenter la vitesse du contenu.
* [Prise en main de l’éditeur universel dans AEM](/help/implementing/universal-editor/getting-started.md) - Découvrez comment accéder à l’éditeur universel et comment commencer à instrumenter votre première application AEM pour l’utiliser.
* [Architecture de l’éditeur universel](/help/implementing/universal-editor/architecture.md) - Découvrez l’architecture de l’éditeur universel et le flux de données entre ses services et calques.
* [Attributs et types](/help/implementing/universal-editor/attributes-types.md) - Découvrez les attributs et les types de données requis par l’éditeur universel.
* [Authentification de l’éditeur universel](/help/implementing/universal-editor/authentication.md) - Découvrez comment l’éditeur universel s’authentifie.
