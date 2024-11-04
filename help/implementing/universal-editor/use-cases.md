---
title: Cas d’utilisation de l’éditeur universel et chemins d’apprentissage
description: Découvrez les principaux cas d’utilisation d’Universal Editor, comment en savoir plus sur son utilisation et comment l’implémenter sur vos propres projets.
exl-id: 398ad0e2-c299-4c49-9784-05c84c67bec2
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 2db4428065b3611a43137514864573947d32fff7
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 0%

---

# Cas d’utilisation de l’éditeur universel et chemins d’apprentissage {#use-cases-learning-paths}

Découvrez les principaux cas d’utilisation d’Universal Editor et comment en savoir plus sur son utilisation et comment l’implémenter sur vos propres projets.

## Vue d’ensemble {#overview}

Universal Editor est un éditeur visuel polyvalent qui fait partie d’Adobe Experience Manager Sites. Il permet aux auteurs d’effectuer la modification WYSIWYG de n’importe quelle expérience sans tête ou avec des entêtes.

Ce document explique en détail ces deux cas d’utilisation et explique comment en savoir plus sur ces deux cas afin que vous puissiez mettre en oeuvre l’éditeur universel dans votre propre projet.

>[!TIP]
>
>Si vous ne l’avez pas déjà fait, consultez le document [Universal Editor Introduction](/help/implementing/universal-editor/introduction.md) pour obtenir un aperçu complet et une valeur pour Universal Editor.

## Cas d’utilisation {#use-cases}

L’éditeur universel offre un éditeur visuel intuitif et pratique à vos auteurs de contenu, quel que soit le type de contenu qu’ils créent. Les deux principaux cas d’utilisation sont les suivants :

* [Création WYSIWYG](#wysiwyg-authoring) - Utilisez la console AEM Sites pour gérer le contenu et créer des pages dans AEM à l’aide de l’éditeur universel.
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

Une fois que vous avez lu ce document, vous pouvez revenir à cette page pour en savoir plus sur le cas d’utilisation de la création WYSIWYG et sur le fonctionnement général d’Universal Editor.

## Fonctionnement d’Universal Editor {#how-ue-works}

La puissance d’Universal Editor réside dans sa capacité à créer n’importe quel contenu statique, fournissant à l’auteur de contenu une interface utilisateur entièrement intuitive et unifiée, quel que soit le contenu.

L’éditeur universel fonctionne comme suit.

1. Un développeur utilise l’application ou la page pour utiliser l’éditeur universel. Cette instrumentation indique à l’éditeur quel contenu est modifiable et comment le conserver.
   * Si vous suivez la documentation [Guide de prise en main du développeur pour la création WYSIWYG avec des Edge Delivery Services](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md), vos pages sont automatiquement instrumentées.
   * Pour une création sans interface utilisateur, votre application peut être facilement instrumentée.
1. L’auteur du contenu charge l’éditeur universel, qui à son tour charge votre page pour modification. Parce qu’il est instrumenté, il sait quel contenu est modifiable et comment il doit être représenté et conservé.
1. L’auteur du contenu modifie le contenu de la page dans une interface WYSIWYG intuitive, en effectuant une modification statique.
1. L’éditeur universel conserve les modifications automatiquement dans la source de données.

Si vous souhaitez en savoir plus sur l’architecture d’Universal Editor, consultez le document [Universal Editor Architecture.](/help/implementing/universal-editor/architecture.md)

## Concepts de l’éditeur universel {#concepts}

Pour qu’une page ou une application puisse être modifiée par l’éditeur universel, elle doit être correctement instrumentée.

* [Attributs et types](/help/implementing/universal-editor/attributes-types.md) - Pour qu’une application ou une page puisse être modifiée par l’éditeur universel, elle doit être correctement instrumentée. Cela inclut l’inclusion des métadonnées appropriées afin que l’éditeur puisse modifier le contenu de l’application.
* [Définition des modèles, champs et types de composants](/help/implementing/universal-editor/field-types.md) - Une fois les métadonnées présentes pour activer la modification d’un composant, vous définissez les champs et les types de composants qu’ils peuvent manipuler dans le rail des propriétés de l’éditeur.
* [Événements d’éditeur universel](/help/implementing/universal-editor/events.md) - Vous pouvez personnaliser davantage votre application en améliorant l’expérience de modification dans votre application en utilisant des événements émis par l’éditeur universel sur le contenu ou les interactions de l’interface utilisateur.

L’éditeur universel peut également être adapté aux besoins de votre projet.

* [Personnalisation de l’expérience de création de l’éditeur universel](/help/implementing/universal-editor/customizing.md) - L’expérience de l’éditeur universel peut être adaptée en filtrant divers aspects de l’éditeur ou en étendant les fonctionnalités de l’éditeur.
