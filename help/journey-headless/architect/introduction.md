---
title: Modélisation de contenu pour AEM en tant que CMS découplé - Introduction
description: Une introduction de l’utilisation des fonctionnalités d’Adobe Experience Manager as a Cloud Service dans un CMS découplé pour modéliser du contenu pour votre projet.
exl-id: 62061d73-6fdb-440b-a7dd-b0d530d49186
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 96%

---

# Modélisation de contenu pour AEM en tant que CMS découplé - Introduction {#architect-headless-introduction}

Dans cette partie du [Parcours d’architecturisation de contenu découplé AEM](overview.md), vous pouvez découvrir les concepts et la terminologie (de base) nécessaires pour comprendre la modélisation de contenu avec Adobe Experience Manager (AEM) as a Cloud Service dans un CMS découplé.

Ce document vous aide à comprendre la diffusion de contenu découplé, comment AEM prend en charge le découplage et comment le contenu est modélisé pour le découplage. Après avoir lu ce document, vous devriez :

* comprendre les concepts de base de la diffusion de contenus en mode découplé ;
* vous être familiarisé avec la façon dont AEM prend en charge le découplage et la modélisation de contenu.

## Objectif {#objective}

* **Audience** : débutant
* **Objectif** : découvrez les concepts et la terminologie relatifs à la modélisation de contenu découplé.

## Diffusion de contenu full stack {#full-stack}

Depuis l’émergence des systèmes de gestion de contenu (CMS) à grande échelle et faciles d’utilisation, les entreprises les utilisent comme un emplacement central pour la gestion des messages, des marques et des communications. L’utilisation d’un CMS comme point central pour administrer les expériences a permis des gains d’efficacité en éliminant la nécessité de dupliquer les tâches dans des systèmes disparates.

![CMS full stack classique](/help/journey-headless/developer/assets/full-stack.png)

Dans un CMS full stack, toutes les fonctionnalités de manipulation de votre contenu se trouvent dans le système. Les fonctionnalités de ce système constituent différents composants de la pile CMS. Une solution full stack présente de nombreux avantages.

* Il n’y a qu’un seul système à maintenir.
* Le contenu est géré de manière centralisée.
* Tous les services du système sont intégrés.
* La création de contenu est transparente.

Ainsi, si un nouveau canal doit être ajouté ou si la prise en charge de nouveaux types d’expériences est requise, un ou plusieurs nouveaux composants peuvent être insérés dans la pile et les modifications ne peuvent être apportées qu’à un seul emplacement.

![Ajout d’un nouveau canal à la pile](/help/journey-headless/developer/assets/adding-channel.png)

Cependant, la complexité des dépendances au sein de la pile apparaît rapidement, car d’autres éléments nécessitent des ajustements pour tenir compte des modifications.

## La tête d’un système découplé {#the-head}

La tête de tout système est généralement constituée du moteur de rendu de sortie, généralement sous la forme d’une interface utilisateur graphique ou d’une autre sortie graphique.

Lorsque nous parlons d’un CMS découplé (ou sans tête), il s’agit d’un système de gestion de contenu qui assure la diffusion en continu vers les consommateurs. Cependant, en n’effectuant que la diffusion du **contenu** de manière standardisée, un CMS découplé omet le rendu de sortie final, laissant la **présentation** du contenu au service consommateur.

![CMS découplé](/help/journey-headless/developer/assets/headless-cms.png)

Les services consommateurs (expériences de réalité augmentée, boutiques web, expériences mobiles, applications web progressives (PWA), etc.) récupèrent le contenu du CMS découplé et fournissent leur propre rendu. Ils se chargent de fournir leurs propres têtes à votre contenu.

Omettre la tête (en mode découplé) permet de simplifier le CMS en éliminant sa complexité. Vous pouvez ainsi transférer la responsabilité de rendu du contenu vers les services qui en ont réellement besoin et qui sont souvent mieux adaptés pour cela.

## Modélisation de contenu {#content-modeling}

La modélisation de contenu (également appelée modélisation de données) est votre spécialité. Par conséquent, que doit-on prendre en compte lors de la modélisation pour le découplage ?

Pour que les applications découplées puissent accéder à votre contenu et l’utiliser, le contenu a vraiment besoin d’une structure prédéfinie. Il serait possible de donner à votre contenu une forme libre, mais cela compliquerait *grandement* les choses pour les applications.

Pour AEM, en tant qu’architecte de contenu, vous exécuterez la modélisation de contenu afin de concevoir un ensemble de **Modèles de fragments de contenu**. Ceux-ci définissent la structure utilisée lorsque les auteurs de contenu créent les **Fragments de contenu** qui contiennent le contenu.

### Accès au contenu {#access-content}

En matière de développement, il s’agit d’un détail, mais ça pourrait vous intéresser, pour vous fournir une vue globale.

Une fois que vous avez créé les modèles de fragment de contenu et que vos auteurs les ont utilisés pour générer le contenu, les applications découplées doivent accéder à ce contenu.

Grâce à Adobe Experience Manager (AEM) as a Cloud Service, vous pouvez accéder de manière sélective à vos fragments de contenu, à l’aide de l’API AEM GraphQL, pour renvoyer uniquement le contenu nécessaire. Grâce à l’API, un développeur peut formuler des requêtes qui sélectionnent un contenu spécifique. Ce processus de sélection est basé sur *vos* modèles de fragment de contenu.

Cela signifie que votre projet peut réaliser une diffusion découplée d’un contenu structuré pour l’utiliser dans vos applications.

## Prochaines étapes {#whats-next}

Maintenant que vous avez appris les concepts et la terminologie, l’étape suivante consiste à [découvrir les principes de base de la modélisation avec des modèles de fragment de contenu](basics.md).

## Ressources supplémentaires {#additional-resources}

* Parcours du développeur AEM Headless
   * [En savoir plus sur le développement CMS découplé](/help/journey-headless/developer/learn-about.md)
   * [Découvrez comment modéliser votre contenu](/help/journey-headless/developer/model-your-content.md)
