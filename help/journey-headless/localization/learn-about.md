---
title: Découvrez le contenu sans interface et comment le localiser dans AEM
description: Apprenez les concepts sans tête, comment ils correspondent à AEM, et la théorie de la localisation AEM.
source-git-commit: 22ca7c01bfddb407c119de7d9a4d105941772664
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 40%

---

# Découvrez le contenu sans interface et comment le localiser dans AEM {#learn-about}

Apprenez les concepts sans tête, comment ils correspondent à AEM, et la théorie de la localisation AEM.

## Objectif {#objective}

Ce document vous aide à comprendre la diffusion de contenu sans interface utilisateur graphique, comment AEM prend en charge l’interface utilisateur sans interface utilisateur graphique et comment ce contenu peut être localisé. Après l’avoir lu, vous devriez :

* Découvrez les concepts de base de la diffusion de contenu sans interface utilisateur.
* Familiarisez-vous avec la façon dont AEM prend en charge la localisation et les headless.

## Diffusion de contenu full stack {#full-stack}

Depuis l’émergence des systèmes de gestion de contenu (CMS) à grande échelle et faciles d’utilisation, les entreprises les utilisent comme emplacement central pour la gestion des messages, des marques et de leur communication. L’utilisation d’un CMS comme point central pour administrer les expériences a permis des gains d’efficacité en éliminant la nécessité de dupliquer les tâches dans des systèmes disparates.

![CMS full stack classique](/help/journey-headless/developer/assets/full-stack.png)

Dans un CMS en pile complète, toutes les fonctionnalités de manipulation de contenu se trouvent dans le CMS. Les fonctionnalités de ce système constituent différents composants de la pile CMS. Une solution full stack présente de nombreux avantages.

* Il y a un système à maintenir.
* Le contenu est géré de manière centralisée.
* Tous les services du système sont intégrés.
* La création de contenu est transparente.

Ainsi, si un nouveau canal doit être ajouté ou si la prise en charge de nouveaux types d’expériences est requise, un (ou plusieurs) nouveaux composants peuvent être insérés dans la pile et il n’y a qu’un seul emplacement pour apporter des modifications.

![Ajout d’un nouveau canal à la pile](/help/journey-headless/developer/assets/adding-channel.png)

La complexité des dépendances au sein de la pile devient rapidement visible, car d’autres éléments de la pile doivent être ajustés pour tenir compte des modifications.

## La tête d’un système découplé {#the-head}

La tête de tout système est généralement constituée du moteur de rendu de sortie, généralement sous la forme d’une interface utilisateur graphique ou d’une autre sortie graphique.

Lorsque nous parlons d’un CMS découplé (ou sans tête), il s’agit d’un système de gestion de contenu qui assure la diffusion en continu vers les consommateurs. Cependant, en n’effectuant que la diffusion du **contenu** de manière standardisée, un CMS découplé omet le rendu de sortie final, laissant la **présentation** du contenu au service consommateur.

![CMS découplé](/help/journey-headless/developer/assets/headless-cms.png)

Les services consommateurs (expériences de réalité augmentée, boutiques web, expériences mobiles, applications web progressives (PWA), etc.) récupèrent le contenu du CMS découplé et fournissent leur propre rendu. Ils se chargent de fournir leurs propres têtes à votre contenu.

Omettre la tête (en mode découplé) permet de simplifier le CMS en éliminant sa complexité. Vous pouvez ainsi transférer la responsabilité de rendu du contenu vers les services qui en ont réellement besoin et qui sont souvent mieux adaptés pour cela.

## Localisation du contenu sans affichage dans AEM {#localizing-in-aem}

En plus d’offrir des outils fiables pour créer, gérer et diffuser des pages web traditionnelles de manière complète, AEM offre la possibilité de créer des sélections de contenu autonomes et de les diffuser sans interface.

La puissance d’AEM lui permet de diffuser du contenu en mode sans affichage, en mode plein empilement ou dans les deux modèles en même temps. Pour le spécialiste de localisation, le même ensemble d’outils de localisation peut être appliqué aux deux types de contenu, ce qui vous permet d’avoir une approche unifiée de la traduction de votre contenu.

## Et après ? {#what-is-next}

Merci d&#39;être venu sur votre parcours de localisation AEM sans interface ! Maintenant que vous avez lu ce document, vous devriez :

* Découvrez les concepts de base de la diffusion de contenu sans interface utilisateur.
* Familiarisez-vous avec la façon dont AEM prend en charge la localisation et les headless.

Tirez parti de ces connaissances et continuez votre parcours de localisation AEM sans interface utilisateur en consultant le document [Commencez par AEM localisation sans interface](getting-started.md) où vous trouverez une vue d’ensemble de la gestion du contenu sans interface utilisateur et de la connaissance de ses outils de localisation.

## Ressources supplémentaires {#additional-resources}

Bien qu’il soit recommandé de passer à la partie suivante du parcours de localisation sans interface utilisateur en consultant le document [Prise en main de la localisation sans interface utilisateur AEM,](getting-started.md) voici quelques ressources facultatives supplémentaires qui approfondissent certains concepts mentionnés dans ce document, mais qui ne doivent pas continuer sur le parcours sans interface.

* [MSM et traduction](/help/sites-cloud/administering/msm-and-translation.md)  : détails d’AEM Multi-Site Manager et de son fonctionnement avec ses outils de traduction.
