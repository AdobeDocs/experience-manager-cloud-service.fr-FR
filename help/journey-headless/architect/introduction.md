---
title: AEM Headless Content Architect Journey
description: An introduction to the powerful, and flexible, headless features of Adobe Experience Manager as a Cloud Service, and how to model content for your project.
exl-id: 62061d73-6fdb-440b-a7dd-b0d530d49186
source-git-commit: 3f6c96da3fd563b4c8db91ab1bc08ea17914a8c1
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 37%

---

# Content Modeling for Headless with AEM - An Introduction {#architect-headless-introduction}

[](overview.md)

This document helps you understand headless content delivery, how AEM supports headless, and how content is modeled for headless. Après l’avoir lu, vous devriez :

* Understand the basic concepts of headless content delivery.
* Be familiar with how AEM supports headless and content modeling.

## Objectif {#objective}

* **Audience** : débutant
* ****

## Diffusion de contenu full stack {#full-stack}

Depuis l’émergence des systèmes de gestion de contenu (CMS) à grande échelle et faciles d’utilisation, les entreprises les utilisent comme emplacement central pour la gestion des messages, des marques et de leur communication. L’utilisation d’un CMS comme point central pour administrer les expériences a permis des gains d’efficacité en éliminant la nécessité de dupliquer les tâches dans des systèmes disparates.

![CMS full stack classique](/help/journey-headless/developer/assets/full-stack.png)

In a full-stack CMS, all of the functionality for manipulating content is in the CMS. Les fonctionnalités de ce système constituent différents composants de la pile CMS. Une solution full stack présente de nombreux avantages.

* There is one system to maintain.
* Le contenu est géré de manière centralisée.
* Tous les services du système sont intégrés.
* La création de contenu est transparente.

So if new channel needs to be added or support for new types of experiences is required, one (or more) new components can be inserted into the stack and there is only one place to make changes.

![Ajout d’un nouveau canal à la pile](/help/journey-headless/developer/assets/adding-channel.png)

However the complexity of the dependencies within the stack quickly become apparent as other items in the stack need to be adjusted to accommodate the changes.

## La tête d’un système découplé {#the-head}

La tête de tout système est généralement constituée du moteur de rendu de sortie, généralement sous la forme d’une interface utilisateur graphique ou d’une autre sortie graphique.

Lorsque nous parlons d’un CMS découplé (ou sans tête), il s’agit d’un système de gestion de contenu qui assure la diffusion en continu vers les consommateurs. Cependant, en n’effectuant que la diffusion du **contenu** de manière standardisée, un CMS découplé omet le rendu de sortie final, laissant la **présentation** du contenu au service consommateur.

![CMS découplé](/help/journey-headless/developer/assets/headless-cms.png)

Les services consommateurs (expériences de réalité augmentée, boutiques web, expériences mobiles, applications web progressives (PWA), etc.) récupèrent le contenu du CMS découplé et fournissent leur propre rendu. Ils se chargent de fournir leurs propres têtes à votre contenu.

Omettre la tête (en mode découplé) permet de simplifier le CMS en éliminant sa complexité. Vous pouvez ainsi transférer la responsabilité de rendu du contenu vers les services qui en ont réellement besoin et qui sont souvent mieux adaptés pour cela.

## Modélisation de contenu {#content-modeling}

Content Modeling (also known as data modeling) is your specialty, so what needs to be considered when modeling for headless?

For the headless applications to be able to access your content, and do something with it, the content really needs to have a predefined structure. **

**** ****

### Accessing the Content {#access-content}

This is more of a development detail - but it might interest you, just to complete the story.

Once you&#39;ve created the Content Fragment Models, and your authors have used them to generate the content, the headless applications will need to access this content.

Adobe Experience Manager (AEM) as a Cloud Service, can selectively access your Content Fragments using the AEM GraphQL API, to return only the content that is needed. **

This means your project can realize headless delivery of structured content for use in your applications.

## Et après ? {#whats-next}

[](basics.md)

## Ressources supplémentaires {#additional-resources}

* Parcours de développement découplé AEM
   * [En savoir plus sur le développement CMS découplé](/help/journey-headless/developer/learn-about.md)
   * [Learn how to Model Your Content](/help/journey-headless/developer/model-your-content.md)
