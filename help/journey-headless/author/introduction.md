---
title: Création pour AEM en tant que CMS sans affichage - Introduction
description: Cette section présente l’utilisation des fonctionnalités d’Adobe Experience Manager as a Cloud Service as a Headless CMS pour créer du contenu pour votre projet.
exl-id: 065b00cb-a82d-4bcb-b2c9-44542cee6303
source-git-commit: 00ec09f327bc2f382d263970e690ed067aaa1355
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 86%

---

# Création pour AEM en tant que CMS sans affichage - Introduction {#author-headless-introduction}

Dans cette partie du [AEM Parcours de création de contenu sans affichage](overview.md), vous pouvez découvrir les concepts (de base) et la terminologie nécessaires pour comprendre la création de contenu lors de l’utilisation d’Adobe Experience Manager (AEM) as a Cloud Service en tant que CMS sans affichage. Cela implique de structurer et de créer votre contenu pour une diffusion de contenu sans interface utilisateur.

## Objectif {#objective}

* **Audience** : débutant
* **Objectif** : découvrez les concepts et la terminologie relatifs à la création découplée.

## Système de gestion de contenu (CMS) {#content-management-system}

Qu’est-ce qu’un système de gestion de contenu ?

Le nom de système de gestion de contenu (CMS) est parfaitement parlant : il s’agit d’un système informatique utilisé pour gérer le contenu. Ce concept un peu général, donc, pour être plus précis, il est (généralement) utilisé pour gérer le contenu que vous souhaitez rendre disponible sur votre ou vos sites web.

## CMS découplé {#headless-cms}

Le découplage est un terme utilisé pour décrire les systèmes qui dissocient efficacement le contenu de la manière d’afficher ce contenu sur le web.

Traditionnellement, vous gérez le contenu dans un CMS qui est responsable du rendu de ce contenu sur vos pages web.

Ainsi, le découplage signifie que votre jeu de contenu peut être géré dans le CMS, puis accessible par le biais d’une ou de plusieurs applications (indépendantes).

Cela signifie que votre contenu peut être diffusé sur n’importe quel appareil, dans de nombreux formats. Cela rend l’ensemble du processus beaucoup plus flexible et signifie également que vous n’avez pas à vous soucier de la mise en page et de la mise en forme.

>[!NOTE]
>
>Si vous souhaitez en savoir plus sur les détails techniques d’un CMS découplé, consultez la section En savoir plus sur le développement CMS découplé.

## Adobe Experience Manager as a Cloud Service {#aem-cloud-service}

Qu’est-ce qu’AEM ?

Tout d’abord, AEM est un système de gestion de contenu qui propose un large éventail de fonctionnalités qui peuvent également être personnalisées pour répondre à vos besoins.

Cela signifie qu’il peut être utilisé en tant que :

* CMS découplé
   * Votre contenu découplé peut être créé en tant que **Fragments de contenu**.
Il s’agit d’éléments de contenu autonomes accessibles directement par le biais de nombreuses applications, car ils disposent d’une structure prédéfinie basée sur les **Modèles de fragment de contenu**.
Cela signifie que votre contenu peut atteindre de nombreux appareils différents, dans de nombreux formats et avec de une variété de fonctionnalités.
De plus, ces fragments peuvent également être utilisés lors de la construction de pages web AEM, si vous le souhaitez.

* CMS « traditionnel »
   * Le contenu est créé pour les pages web à l’aide de divers composants qui définissent la manière dont le contenu sera rendu sur votre site web. AEM fait également preuve dans ce cas d’une extrême flexibilité, car votre équipe de projet peut développer des composants personnalisés.

## Modélisation de contenu {#content-modeling}

La modélisation de contenu (également appelée modélisation de données) est donc un autre terme technique. Pourquoi devrait-il vous intéresser en tant qu’auteur ?

Pour que les applications découplées puissent accéder à votre contenu et en faire quelque chose, votre contenu a vraiment besoin d’une structure prédéfinie. Il serait possible de donner à votre contenu une forme libre, mais cela rendrait la vie *vraiment* compliquée aux applications.

Fondamentalement, le processus de définition de la structure à laquelle votre contenu doit se conformer implique la conception d’un modèle, processus appelé « modélisation des données ».

Pour AEM, le rôle d’architecte de contenu (souvent une autre personne) effectue la modélisation des données afin de concevoir un éventail de **Modèles de fragment de contenu** que vous utilisez ensuite comme base pour votre contenu en utilisant les **Fragments de contenu**.

>[!NOTE]
>
>Si vous souhaitez en savoir plus sur la modélisation des données, consultez le parcours d’architecture de contenu découplé AEM.

## Prochaines étapes {#whats-next}

Maintenant que vous avez découvert les concepts et la terminologie, l’étape suivante consiste à [découvrir les principes de base de la création de fragments de contenu](basics.md). Cela permettra d’introduire la manipulation de base d’AEM ainsi que la création de fragments de contenu.

## Ressources supplémentaires {#additional-resources}

* Parcours du développeur AEM Headless
   * [En savoir plus sur le développement CMS découplé](/help/journey-headless/developer/learn-about.md)
   * [Découvrez comment modéliser votre contenu](/help/journey-headless/developer/model-your-content.md)

* Parcours d’architecture de contenu découplé AEM

* Parcours de traduction de contenu découplé AEM
