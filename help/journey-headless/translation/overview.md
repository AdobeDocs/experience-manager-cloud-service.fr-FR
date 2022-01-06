---
title: AEM Parcours de traduction sans affichage
description: Commencez ici pour un parcours guidé en traduisant votre contenu sans tête à l’aide AEM puissants outils de traduction.
exl-id: b677f691-5257-43c3-a4b9-c34932577b31
source-git-commit: 3f6c96da3fd563b4c8db91ab1bc08ea17914a8c1
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 8%

---

# AEM Parcours de traduction sans affichage {#aem-headless-translation-journey}

Commencez ici pour un parcours guidé en traduisant votre contenu sans tête à l’aide AEM puissants outils de traduction.

## Présentation {#introduction}

Headless implementation is increasingly becoming important for delivering experiences to your audience, wherever they are and regardless of channel, region, or locale.

L’implémentation découplée renonce à la gestion des pages et des composants, comme c’est généralement le cas avec les solutions complètes, et se concentre sur la création de fragments de contenu réutilisables et neutres du point de vue du canal, ainsi que sur leur diffusion entre canaux. En utilisant AEM puissants outils de traduction, ces fragments réutilisables peuvent être facilement traduits et diffusés à votre audience où qu’il soit.

Ce guide vous guide tout au long des rubriques de traduction sans tête les plus importantes afin que vous puissiez :

* disposer d’une vue d’ensemble de la diffusion de contenu sans interface ;
* Ayez une compréhension de base AEM les fonctions sans tête.
* Découvrez AEM fonctionnalités de traduction et comment elles sont liées au contenu sans interface.
* Vous pouvez commencer à traduire votre propre contenu sans tête.

The goal is to give you a broad understanding of headless technology, how AEM serves headless content, and how you can translate it. Si vous ne connaissez aucun de ces sujets, voici le point de départ idéal.

Si vous connaissez déjà l&#39;AEM, l&#39;absence de tête et la traduction, vous disposez peut-être déjà des connaissances fondamentales de ce parcours. Consider referring to our technical documentation linked under the [additional resources section below.](#additional-resources)

## AEM Parcours de documentation {#documentation-journeys}

[Un Parcours de documentation](/help/journey-documentation/documentation-journeys.md) Il relie de nombreux sujets et caractéristiques différents et peut-être complexes en fournissant un récit qui aide le lecteur, qui peut être nouveau pour AEM, comprendre et résoudre un problème commercial du début à la fin, tout en assumant un minimum de connaissances préalables ou AEM.

Documentation Journeys are designed around best practices principles, informed by Adobe&#39;s latest research, proven implementation experience from Adobe consultants, and feedback from customer projects.

Si vous souhaitez savoir comment Adobe recommande de résoudre des affaires sans interface avec AEM, [AEM Parcours sans affichage](/help/journey-documentation/documentation-journeys.md) où commencer.

## Public {#audience}

Ce parcours est conçu pour le personnage spécialisé en traduction, souvent appelé gestionnaire de projet de traduction ou TPM. This journey lays out the requirements, steps, and approach to translate headless content in AEM. Le parcours peut définir des personnes supplémentaires avec lesquelles le traducteur doit interagir, mais le point de vue du parcours est celui du traducteur.

This journey assumes the reader has experience translating content on a large CMS system, but assumes no knowledge of headless technology or AEM.

The following are the personas that interact in this journey.

| Personnage | Description | Rôle dans le Parcours |
|---|---|---|
| Spécialiste de traduction | Définit le contenu à traduire et gère ces workflows. | Audience of this journey |
| Auteur de contenu | Crée et gère du contenu diffusé sans interface | Les auteurs de contenu créent du contenu que le spécialiste de traduction doit traduire. |
| Administrateur | Gère la configuration et la configuration de base d’AEM | Le spécialiste des traductions travaille avec l’administrateur pour apporter les modifications de configuration nécessaires à la traduction, telles que l’installation d’un connecteur de traduction. |
| Architecte de contenu | Analyse les exigences relatives aux données qui doivent être distribuées sans interface et définit la structure de ces données | Les spécialistes de traduction travaillent avec l’architecte de contenu pour définir l’organisation du contenu afin qu’il puisse être facilement traduit. |

Information in this journey can of course be useful to all personas, but some information may be superfluous to certain roles. Restez à l’écoute pour [les prochains parcours couvrant des rôles supplémentaires.](/help/journey-documentation/documentation-journeys.md#journeys)

## Parcours de traduction sans affichage {#the-journey}

Vous allez explorer de nombreux sujets dans ce parcours. Les articles suivants vous donnent des connaissances fondamentales sur la traduction de contenu headless dans AEM et vous proposent des liens vers une documentation technique détaillée.

Bien que vous puissiez accéder directement à une partie spécifique du parcours, de nombreux concepts sont présentés dans des articles précédents. Therefore if you are new to headless translation in AEM, we recommend that you start at the beginning and progress sequentially.

| Numéro | Article | Description |
|---|---|---|
| 0 | AEM Parcours de traduction sans affichage | Ce document |
| 1 | [Learn about headless content and how to translate it in AEM](learn-about.md) | Learn headless concepts, how they map to AEM, and the theory of AEM translation. |
| 2 | [Prise en main de AEM traduction sans interface](getting-started.md) | Découvrez comment organiser votre contenu sans interface et comment AEM outils de traduction fonctionnent. |
| 3 | [Configuration du connecteur de traduction](configure-connector.md) | Découvrez comment connecter AEM à un service de traduction. |
| 4 | [Configuration des règles de traduction](translation-rules.md) | Découvrez comment définir des règles de traduction pour identifier le contenu à traduire. |
| 5 | [Traduire le contenu](translate-content.md) | Utilisez le connecteur et les règles de traduction pour traduire votre contenu sans interface utilisateur graphique. |
| 6 | [Publier le contenu traduit](publish-content.md) | Découvrez comment publier votre contenu traduit et mettre à jour la traduction lorsque le contenu sous-jacent est mis à jour. |

## Et après ? {#what-is-next}

You are now ready to get started on your Adobe headless translation journey. Nous vous encourageons à passer à la partie suivante du parcours et à lire l’article [Découvrez le contenu sans tête et comment le traduire en AEM](learn-about.md)

## Ressources supplémentaires {#additional-resources}

Les parcours de documentation vous montrent comment AEM résoudre un problème d’entreprise en vous fournissant une narration qui vous guide tout au long de processus et de fonctionnalités complexes et interconnectés. Un parcours illustre la façon dont plusieurs fonctionnalités fonctionnent ensemble pour répondre aux besoins d’une seule entreprise.

Ces parcours sont conçus pour être autonomes. Cependant, un certain nombre d’entre elles peuvent être liées. Consultez ces parcours supplémentaires pour plus d’informations sur la manière dont AEM puissantes fonctionnalités fonctionnent ensemble.

* [Parcours de création sans affichage](/help/journey-headless/author/overview.md) - Commencez ici pour un parcours guidé à travers les puissantes et flexibles fonctionnalités headless d’AEM, leurs fonctionnalités et comment modéliser votre contenu sur votre premier projet headless.
* [Parcours Architecte sans tête](/help/journey-headless/architect/overview.md) - Commencez ici pour découvrir les fonctionnalités puissantes, flexibles et sans interface d’Adobe Experience Manager as a Cloud Service et comment modéliser le contenu de votre projet.
* [AEM Parcours développeur sans tête](/help/journey-headless/developer/overview.md) - Commencez ici pour un parcours guidé à travers les puissantes et flexibles fonctionnalités headless d’AEM, leurs capacités et comment les exploiter dans votre premier projet de développement.
* [AEM as a Cloud Service technical documentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=fr) - If you already have a firm understanding of AEM and headless technologies, you may want to directly consult our in-depth technical docs.
* [Tutoriels AEM sans affichage](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=fr) - Si vous préférez apprendre par la pratique et êtes techniquement disposé, suivez nos tutoriels pratiques organisés par API et structure, qui explorent la création et l’utilisation d’applications reposant sur AEM Headless.
