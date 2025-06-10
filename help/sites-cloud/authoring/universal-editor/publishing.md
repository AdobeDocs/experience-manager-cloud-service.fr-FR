---
title: Publication de contenu avec l’éditeur universel
description: Découvrez comment l’éditeur universel publie du contenu et comment vos applications peuvent gérer le contenu publié.
exl-id: aee34469-37c2-4571-806b-06c439a7524a
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 3288edacba909335f8109eee7e1e793abe5a8343
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 31%

---


# Publication de contenu avec l’éditeur universel {#publishing}

Découvrez comment l’éditeur universel publie du contenu et comment vos applications peuvent gérer le contenu publié.

>[!TIP]
>
>Le processus de publication décrit ici est la fonctionnalité standard prête à l’emploi de l’éditeur universel.
>
>L’éditeur universel prend également en charge les [extensions et extensibilité de l’interface utilisateur](/help/implementing/universal-editor/extending.md) pour permettre aux workflows de prendre en charge votre processus de publication, de sorte que votre flux de publication puisse varier.

## Publication de contenu à partir de l’éditeur universel {#publishing-content}

Lorsque vous, en tant qu’auteur de contenu, êtes prêt à publier votre contenu, il vous suffit d’appuyer ou de cliquer sur l’icône **Publier** dans la barre d’outils de l’éditeur universel.

![Publication de pages](assets/publish-menu.png)

1. Dans l’éditeur universel, appuyez ou cliquez sur [l’icône **Publier** dans la barre d’outils de l’éditeur universel.](/help/sites-cloud/authoring/universal-editor/navigation.md#publish)
1. Si un [service d’aperçu](/help/sites-cloud/authoring/sites-console/previewing-content.md) est disponible, vous pouvez choisir l’endroit où vous publiez votre contenu, soit dans **[Aperçu](/help/sites-cloud/authoring/sites-console/previewing-content.md)** (le cas échéant) ou **Publication**.
1. La section **Éléments** répertorie le contenu inclus dans la publication, notamment :
   * **Nouveaux** éléments qui n’ont pas encore été publiés.
   * **Modifié** contenu qui a été publié, mais modifié depuis la dernière publication.
   * **Publié** contenu qui a été publié et qui n’a pas été modifié depuis cette publication.

   Appuyez ou cliquez sur les cases à cocher en regard de ces éléments pour les inclure ou les exclure de la publication, si nécessaire. Appuyez ou cliquez sur **Étendre** pour afficher les éléments individuels inclus dans les totaux pour les trois catégories et pouvoir les inclure/exclure individuellement.

   ![Publier les éléments](assets/publish-items.png)

   Appuyez ou cliquez sur la flèche vers l’arrière en regard de l’en-tête **Éléments** pour revenir à l’aperçu.

1. Appuyez ou cliquez sur **Publier** pour publier ou **Annuler** pour abandonner.

>[!NOTE]
>
>L’option de publication dans la prévisualisation [peut être désactivée](/help/implementing/universal-editor/customizing.md#publish-preview) et peut donc ne pas apparaître dans votre éditeur.

## Dépublication de contenu à partir de l’éditeur universel {#unpublishing-content}

La dépublication de contenu fonctionne de la même manière que la publication de contenu. Lorsque vous êtes en tant que créateur de contenu et que vous êtes prêt à supprimer du contenu de la publication, appuyez ou cliquez sur l’icône représentant des points de suspension dans la barre d’outils de l’éditeur universel, puis sur **Dépublier**.

Vous disposez alors des mêmes options de dépublication du contenu que lors de la [ publication du contenu.](#publishing-content) d’inclure la dépublication à partir d’une instance d’aperçu si disponible et les éléments à inclure dans la dépublication.

## Publication et dépublication à partir de la console Sites {#publishing-sites-console}

Vous pouvez également publier [à partir de la console Sites](/help/sites-cloud/authoring/sites-console/publishing-pages.md) ce qui peut s’avérer utile lorsque vous souhaitez publier plusieurs pages de contenu ou planifier la publication ou la dépublication.

## Ressources supplémentaires {#additional-resources}

Pour savoir comment créer du contenu avec l’éditeur universel, consultez ce document.

* [Création de contenu avec l’éditeur universel](authoring.md) - Découvrez à quel point il est facile et intuitif pour les créateurs et les créatrices de contenu de créer du contenu à l’aide de l’éditeur universel.

Pour en savoir plus sur les détails techniques de l’éditeur universel, consultez ces documents de développement.

* [Présentation de l’éditeur universel](/help/implementing/universal-editor/introduction.md) - Découvrez comment l’éditeur universel permet de modifier n’importe quel aspect d’un contenu dans n’importe quelle implémentation afin de fournir des expériences exceptionnelles, d’augmenter la vitesse du contenu et d’offrir une expérience de développement à la pointe de la technologie.
* [Prise en main de l’éditeur universel dans AEM](/help/implementing/universal-editor/getting-started.md) - Découvrez comment accéder à l’éditeur universel et comment commencer à instrumenter votre première application AEM pour l’utiliser.
* [Architecture de l’éditeur universel](/help/implementing/universal-editor/architecture.md) - Découvrez l’architecture de l’éditeur universel et le flux de données entre ses services et calques.
* [Attributs et types](/help/implementing/universal-editor/attributes-types.md) - Découvrez les attributs et les types de données requis par l’éditeur universel.
* [Authentification de l’éditeur universel](/help/implementing/universal-editor/authentication.md) - Découvrez comment l’éditeur universel s’authentifie.
