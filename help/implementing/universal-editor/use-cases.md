---
title: Cas d’utilisation de l’éditeur universel et parcours d’apprentissage
description: Découvrez les principaux cas d’utilisation de l’éditeur universel et la meilleure façon d’en savoir plus sur son utilisation et sur la manière de l’implémenter dans vos propres projets.
exl-id: 398ad0e2-c299-4c49-9784-05c84c67bec2
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '882'
ht-degree: 100%

---

# Cas d’utilisation de l’éditeur universel et parcours d’apprentissage {#use-cases-learning-paths}

Découvrez les principaux cas d’utilisation de l’éditeur universel et comment en savoir plus sur son utilisation et sur la manière de l’implémenter dans vos propres projets.

## Vue d’ensemble {#overview}

L’éditeur universel est un éditeur visuel polyvalent qui fait partie d’Adobe Experience Manager Sites. Il permet aux créateurs et créatrices d’effectuer une modification de type « ce que vous voyez est ce que vous obtiendrez » (what-you-see-is-what-you-get, WYSIWYG) de n’importe quelle expérience couplée ou découplée.

Ce document explique ces deux cas d’utilisation en détail et vous montre comment en savoir plus afin que vous puissiez implémenter l’éditeur universel dans votre propre projet.

>[!TIP]
>
>Si vous ne l’avez pas déjà fait, consultez le document [Présentation de l’éditeur universel](/help/implementing/universal-editor/introduction.md) pour une vue d’ensemble complète et compréhension de la valeur de l’éditeur universel.

## Cas d’utilisation {#use-cases}

L’éditeur universel présente un éditeur visuel pratique et intuitif aux auteurs et autrices de contenu, quel que soit le type de contenu qu’ils ou elles créent. Les deux cas d’utilisation principaux sont les suivants :

* [Création WYSIWYG](#wysiwyg-authoring) : utilisez la console AEM Sites pour gérer votre contenu et créer des pages dans AEM à l’aide de l’éditeur universel.
* [Création (en mode) découplé](#headless-authoring) : créez du contenu dans votre propre application (en mode) découplé personnalisée à l’aide de l’éditeur universel.

### Création WYSIWYG {#wysiwyg-authoring}

Si vous connaissez déjà AEM, vous pouvez utiliser la console Sites pour créer et gérer vos pages, puis les modifier à l’aide de l’éditeur universel.

Ainsi, vous pouvez bénéficier des outils disponibles dans la console Sites tels que la gestion des pages (copier, coller, déplacer) et les workflows, mais aussi bénéficier de l’éditeur universel moderne.

Si c’est votre cas d’utilisation, la prochaine étape immédiate consiste à consulter les documents suivants pour obtenir une vue d’ensemble complète de la mise en service de l’éditeur universel dans AEM.

1. [Guide de prise en main des développeurs et développeuses pour la création dans WYSIWYG avec Edge Delivery Services](https://www.aem.live/developer/ue-tutorial) : commencez avec votre premier projet d’éditeur universel dans AEM
1. [Création de blocs paramétrés pour une utilisation avec l’éditeur universel](https://www.aem.live/developer/universal-editor-blocks) : découvrez comment paramétrer les blocs pour rendre votre contenu modifiable dans l’éditeur universel
1. [Modélisation de contenu pour la création dans WYSIWYG avec des projets Edge Delivery Services](https://www.aem.live/developer/component-model-definitions) : découvrez les détails de la structure des blocs pour modéliser efficacement votre contenu à utiliser avec l’éditeur universel.

Une fois que vous avez lu ces documents, vous pouvez revenir à cette page pour en savoir plus sur le cas d’utilisation de la création (en mode) découplé et sur le fonctionnement de l’éditeur universel en général.

### Création (en mode) découplé {#headless-authoring}

Si vous disposez déjà d’une application (en mode) découplé, vous pouvez utiliser l’éditeur universel pour créer du contenu pour l’application et conserver son contenu en tant que fragments de contenu dans AEM. La seule exigence est que l’application soit instrumentée pour permettre l’utilisation de l’éditeur universel.

Si c’est votre cas d’utilisation, l’étape suivante immédiate consiste à consulter le document suivant pour obtenir un exemple d’application (en mode) découplé instrumentée pour utiliser l’éditeur universel.

* [Exemple d’application SecurBank pour l’éditeur universel](/help/implementing/universal-editor/securbank.md)

Une fois que vous avez lu ce document, vous pouvez revenir à cette page pour en savoir plus sur le cas d’utilisation de la création WYSIWYG et sur le fonctionnement de l’éditeur universel en général.

{{ue-headless-auth}}

## Fonctionnement de l’éditeur universel {#how-ue-works}

La puissance de l’éditeur universel est sa capacité à créer n’importe quel contenu statique, fournissant à la personne en charge de la création de contenu une interface utilisateur entièrement intuitive et unifiée, quel que soit le contenu.

L’éditeur universel fonctionne de la manière suivante.

1. Un développeur ou une développeuse instrumente l’application ou la page pour utiliser l’éditeur universel. Cette instrumentation indique à la personne en charge des modifications, quel contenu est modifiable et comment le conserver.
   * Si vous suivez la documentation [Guide de prise en main pour les développeurs et développeuses pour la création WYSIWYG avec Edge Delivery Services](https://www.aem.live/developer/ue-tutorial), vos pages sont automatiquement instrumentées.
   * Pour la création (en mode) découplé, votre application peut être facilement instrumentée.
1. La personne en charge de la création de contenu charge l’éditeur universel, qui à son tour charge votre page à modifier. Parcequ’il est instrumenté, cette personne sait quel contenu est modifiable et comment le représenter et conserver.
1. La personne en charge de la création de contenu modifie de façon statique le contenu de la page dans une interface WYSIWYG intuitive.
1. L’éditeur universel conserve automatiquement les modifications dans la source de données.

Si vous souhaitez en savoir plus sur l’architecture de l’éditeur universel, consultez le document [Architecture de l’éditeur universel](/help/implementing/universal-editor/architecture.md).

## Concepts de l’éditeur universel {#concepts}

Pour que l’éditeur universel puisse modifier une page ou une application, cette dernière doit être correctement instrumentée.

* [Attributs et types](/help/implementing/universal-editor/attributes-types.md) : pour que l’éditeur universel puisse modifier une page ou une application, cette dernière doit être correctement instrumentée. Cela inclut des métadonnées appropriées afin que l’éditeur puisse modifier le contenu de l’application.
* [Définitions de modèle, champs et types de composants](/help/implementing/universal-editor/field-types.md) : une fois que les métadonnées sont présentes pour permettre la modification d’un composant, vous définissez les champs et les types de composants qu’ils peuvent manipuler dans le panneau Propriétés de l’éditeur.
* [Événements de l’éditeur universel](/help/implementing/universal-editor/events.md) : vous pouvez personnaliser davantage votre application en améliorant l’expérience de modification dans votre application en utilisant des événements que l’éditeur universel émet sur le contenu ou les interactions de l’interface utilisateur.

L’éditeur universel peut également être adapté aux besoins de votre projet.

* [Personnalisation de l’éditeur universel](/help/implementing/universal-editor/customizing.md) : l’expérience de l’éditeur universel peut être adaptée en filtrant divers aspects de l’éditeur ou en étendant les fonctionnalités de l’éditeur.
* [Extension de l’éditeur universel](/help/implementing/universal-editor/extending.md) : l’interface utilisateur de l’éditeur universel peut être étendue pour développer ses fonctionnalités afin de répondre aux besoins de votre projet.
