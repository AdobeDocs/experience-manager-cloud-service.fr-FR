---
title: Learn about headless content and how to translate it in AEM
description: Apprenez les concepts sans tête, comment ils s'adaptent à AEM, et la théorie de la traduction AEM.
exl-id: 72bb6646-e573-4576-8d17-49787d8c8c7f
source-git-commit: 3f6c96da3fd563b4c8db91ab1bc08ea17914a8c1
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 32%

---

# Découvrez le contenu sans tête et comment le traduire en AEM {#learn-about}

Apprenez les concepts sans tête, comment ils s&#39;adaptent à AEM, et la théorie de la traduction AEM.

## Objectif {#objective}

This document helps you understand headless content delivery, how AEM supports headless, and how such content can be translated. Après l’avoir lu, vous devriez :

* Découvrez les concepts de base de la diffusion de contenu sans interface utilisateur.
* Familiarisez-vous avec la façon dont AEM prend en charge les traductions et les headless.

## Diffusion de contenu full stack {#full-stack}

Depuis l’émergence des systèmes de gestion de contenu (CMS) à grande échelle et faciles d’utilisation, les entreprises les utilisent comme emplacement central pour la gestion des messages, des marques et de leur communication. L’utilisation d’un CMS comme point central pour administrer les expériences a permis des gains d’efficacité en éliminant la nécessité de dupliquer les tâches dans des systèmes disparates.

![CMS full stack classique](/help/journey-headless/developer/assets/full-stack.png)

In a full-stack CMS, all of the functionality for manipulating content is in the CMS. Les fonctionnalités de ce système constituent différents composants de la pile CMS. Une solution full stack présente de nombreux avantages.

* There is one system to maintain.
* Le contenu est géré de manière centralisée.
* Tous les services du système sont intégrés.
* La création de contenu est transparente.

Ainsi, si un nouveau canal doit être ajouté ou si la prise en charge de nouveaux types d’expériences est requise, un (ou plusieurs) nouveaux composants peuvent être insérés dans la pile et il n’y a qu’un seul emplacement pour apporter des modifications.

![Ajout d’un nouveau canal à la pile](/help/journey-headless/developer/assets/adding-channel.png)

However the complexity of the dependencies within the stack quickly becomes apparent as other items in the stack need to be adjusted to accommodate the changes.

## La tête d’un système découplé {#the-head}

La tête de tout système est généralement constituée du moteur de rendu de sortie, généralement sous la forme d’une interface utilisateur graphique ou d’une autre sortie graphique.

Lorsque nous parlons d’un CMS découplé (ou sans tête), il s’agit d’un système de gestion de contenu qui assure la diffusion en continu vers les consommateurs. Cependant, en n’effectuant que la diffusion du **contenu** de manière standardisée, un CMS découplé omet le rendu de sortie final, laissant la **présentation** du contenu au service consommateur.

![CMS découplé](/help/journey-headless/developer/assets/headless-cms.png)

Les services consommateurs, qu’il s’agisse d’expériences AR, d’un magasin web, d’expériences mobiles, d’applications web progressives (PWA), etc., récupèrent du contenu du CMS sans interface et fournissent leur propre rendu. Ils se chargent de fournir leurs propres têtes à votre contenu.

Omettre la tête (en mode découplé) permet de simplifier le CMS en éliminant sa complexité. Vous pouvez ainsi transférer la responsabilité de rendu du contenu vers les services qui en ont réellement besoin et qui sont souvent mieux adaptés pour cela.

## Traduction de contenu sans affichage dans AEM {#translating-in-aem}

En plus d’offrir des outils fiables pour créer, gérer et diffuser des pages web traditionnelles de manière complète, AEM offre la possibilité de créer des sélections de contenu autonomes et de les diffuser sans interface.

The power of AEM allows it to deliver content either headlessly, full-stack, or in both models at the same time. For the translation specialist, the same set of translation tools can be applied to both types of content, giving you a unified approach for translating your content.

Plus loin dans le parcours, vous découvrirez les détails de la traduction AEM contenu, mais à un niveau général, le concept est simple :

1. Define a connection to a translation service by configuring the translation integration framework.
1. Définissez le contenu à traduire à l’aide des règles de traduction.
1. Créez un projet de traduction pour récolter le contenu, l’envoyer au service de traduction et recevoir les résultats.
1. Passez en revue et publiez le contenu traduit.

## Et après ? {#what-is-next}

Thanks for getting started on your AEM headless translation journey! Maintenant que vous avez lu ce document, vous devriez :

* Découvrez les concepts de base de la diffusion de contenu sans interface utilisateur.
* Be familiar with how AEM supports headless and translation.

Build on this knowledge and continue your AEM headless translation journey by next reviewing the document [Get started with AEM headless translation](getting-started.md) where you will have an overview of how AEM manages headless content and get to know its translation tools.

## Ressources supplémentaires {#additional-resources}

Bien qu’il soit recommandé de passer à la partie suivante du parcours de traduction sans interface utilisateur graphique en consultant le document [Prise en main de AEM traduction sans interface,](getting-started.md) vous trouverez ci-dessous des ressources facultatives supplémentaires qui approfondissent certains concepts mentionnés dans ce document, mais qui ne sont pas nécessaires pour continuer sur le parcours sans interface.

* [MSM et traduction](/help/sites-cloud/administering/msm-and-translation.md) - Détails d’AEM Multi Site Manager et son fonctionnement avec ses outils de traduction
