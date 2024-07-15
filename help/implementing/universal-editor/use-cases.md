---
title: Cas d’utilisation de l’éditeur universel et chemins d’apprentissage
description: Découvrez les principaux cas d’utilisation d’Universal Editor, comment en savoir plus sur son utilisation et comment l’implémenter sur vos propres projets.
exl-id: 398ad0e2-c299-4c49-9784-05c84c67bec2
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 7ad9a959592f1e8cebbcad9a67d280d5b2119866
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# Cas d’utilisation de l’éditeur universel et chemins d’apprentissage {#use-cases-learning-paths}

Découvrez les principaux cas d’utilisation d’Universal Editor et comment en savoir plus sur son utilisation et comment l’implémenter sur vos propres projets.

## Vue d’ensemble {#overview}

Universal Editor est un éditeur visuel polyvalent qui fait partie d’Adobe Experience Manager Sites. Il permet aux auteurs d’effectuer l’édition WYSIWYG (What-you-see-what-you-get) de n’importe quelle expérience sans tête ou plein de tête.

Ce document explique en détail ces deux cas d’utilisation et explique comment en savoir plus sur ces deux cas afin que vous puissiez mettre en oeuvre l’éditeur universel dans votre propre projet.

>[!TIP]
>
>Si vous ne l’avez pas déjà fait, consultez le document [Universal Editor Introduction](/help/implementing/universal-editor/introduction.md) pour obtenir un aperçu complet et une valeur pour Universal Editor.

## Cas d’utilisation {#use-cases}

L’éditeur universel offre un éditeur visuel intuitif et pratique à vos auteurs de contenu, quel que soit le type de contenu qu’ils créent. Les deux principaux cas d’utilisation sont les suivants :

* [Création WYSIWYG](#wysiwyg-authoring) - Utilisez la console AEM Sites pour gérer votre contenu et créer des pages dans AEM à l’aide de l’éditeur universel.
* [Création sans affichage](#headless-authoring) - Créez du contenu dans votre propre application personnalisée sans affichage à l’aide de l’éditeur universel.

### Création WYSIWYG {#wysiwyg-authoring}

Si vous maîtrisez déjà AEM, vous pouvez utiliser la console Sites pour créer et gérer vos pages, puis les modifier à l’aide de l’éditeur universel.

Vous pouvez ainsi bénéficier des outils disponibles dans la console Sites, tels que la gestion des pages (copier, coller, déplacer) et les workflows, mais également de l’éditeur universel moderne.

Si c’est votre cas d’utilisation, reportez-vous aux documents suivants pour une présentation complète de la prise en main d’Universal Editor dans AEM.

1. [Guide de prise en main du développeur pour la création WYSIWYG avec des Edge Delivery Services](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) - Prise en main de votre premier projet Universal Editor dans AEM
1. [Création de blocs instrumentés pour une utilisation avec l’éditeur universel](/help/edge/wysiwyg-authoring/create-block.md) - Découvrez comment instrumenter des blocs pour rendre votre contenu modifiable dans l’éditeur universel
1. [Modélisation de contenu pour la création WYSIWYG avec des projets Edge Delivery Services](/help/edge/wysiwyg-authoring/content-modeling.md) - Découvrez les détails de la structure des blocs pour modéliser efficacement votre contenu à utiliser avec l’éditeur universel.

Une fois que vous avez lu ces documents, vous pouvez revenir à cette page pour en savoir plus sur le cas d’utilisation de la création sans interface utilisateur et sur le fonctionnement général d’Universal Editor.

### Création sans affichage {#headless-authoring}

Si vous disposez déjà d’une application sans interface utilisateur graphique, vous pouvez utiliser l’éditeur universel pour créer du contenu pour l’application et conserver son contenu en tant que fragments de contenu dans AEM. La seule condition requise est que l’application soit instrumentée pour autoriser l’utilisation de l’éditeur universel.

Si c’est votre cas d’utilisation, reportez-vous immédiatement au document suivant pour obtenir un exemple d’application sans tête instrumentée pour utiliser l’éditeur universel.

* [Exemple d’application SecurBank pour l’éditeur universel](/help/implementing/universal-editor/securbank.md)

Une fois que vous avez lu ce document, vous pouvez revenir à cette page pour en savoir plus sur le cas d’utilisation de la création WYSIWYG et sur le fonctionnement général de l’éditeur universel.

## Fonctionnement d’Universal Editor {#how-ue-works}

La puissance d’Universal Editor réside dans sa capacité à créer n’importe quel contenu statique, fournissant à l’auteur de contenu une interface utilisateur entièrement intuitive et unifiée, quel que soit le contenu.

L’éditeur universel fonctionne comme suit.

1. Un développeur utilise l’application ou la page pour utiliser l’éditeur universel. Cette instrumentation indique à l’éditeur quel contenu est modifiable et comment le conserver.
   * Pour la création WYSIWYG, les pages créées à l’aide du modèle standard sont automatiquement instrumentées.
   * Pour une création sans interface utilisateur, votre application peut être facilement instrumentée.
1. L’auteur du contenu charge l’éditeur universel, qui à son tour charge votre page pour modification. Parce qu’il est instrumenté, il sait quel contenu est modifiable et comment il doit être représenté et conservé.
1. L’auteur du contenu modifie le contenu de la page dans une interface WYSIWYG intuitive, en effectuant une modification statique.
1. L’éditeur universel conserve les modifications automatiquement dans AEM.

Si vous souhaitez en savoir plus sur l’architecture d’Universal Editor, consultez le document [Universal Editor Architecture.](/help/implementing/universal-editor/architecture.md)

## Concepts de l’éditeur universel {#concepts}

Pour qu’une page ou une application puisse être modifiée par l’éditeur universel, elle doit être correctement instrumentée. Une fois instrumentée, elle peut être davantage adaptée aux besoins de votre projet.

* [Attributs et types](/help/implementing/universal-editor/attributes-types.md) - Pour qu’une application ou une page puisse être modifiée par l’éditeur universel, elle doit être correctement instrumentée. Cela inclut l’inclusion des métadonnées appropriées afin que l’éditeur puisse modifier le contenu de l’application.
* [Définition des modèles, champs et types de composants](/help/implementing/universal-editor/field-types.md) - Une fois les métadonnées présentes pour activer la modification d’un composant, vous définissez les champs et les types de composants qu’ils peuvent manipuler dans le rail des propriétés de l’éditeur. Pour ce faire, créez un modèle et liez-le à partir du composant.
* [Personnalisation de l’expérience de création Universal Editor](/help/implementing/universal-editor/customizing.md) - Une fois l’application ou la page entièrement instrumentée, l’expérience Universal Editor peut être davantage adaptée en filtrant les composants disponibles ou en étendant les fonctionnalités de l’éditeur.
* [Événements d’éditeur universel](/help/implementing/universal-editor/events.md) - Vous pouvez personnaliser davantage votre application en réagissant aux événements standard que la fonction envoie par la fonction universelle lors des modifications apportées au contenu et à l’interface utilisateur.
