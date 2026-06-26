---
title: Tâche de conversion de format en fragments de contenu visuels
description: Découvrez ce qu’est la tâche Brand Experience Agent Figma en fragments de contenu visuels et ce qu’elle peut vous apporter.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
source-git-commit: 19931f7cc911376f5096903a2d99d6ff11f928ac
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---


# Tâche de conversion de format en fragments de contenu visuels {#figma-to-visual-content-fragments-job}

La tâche Figma vers les fragments de contenu visuel de l’[agent de production Experience](/help/ai-in-aem/agents/brand-experience/experience-production/overview.md) automatise le processus de recréation des conceptions Figma dans Adobe Experience Manager (AEM) as a Cloud Service.

## Vue d’ensemble {#overview}

Les fragments de contenu visuel AEM permettent de prévisualiser et de diffuser des fragments de contenu à l’aide d’une disposition visuelle basée sur un [modèle HTML](/help/implementing/developing/extending/content-fragments-visualization-templates.md).

Bien que la définition des informations de style et de mise en page dans des modèles HTML codés à la main soit entièrement réalisable, il s’agit d’un processus hautement technique qui est généralement effectué par les développeurs web.

Afin de rationaliser ce processus pour les [fragments de contenu visuel](/help/sites-cloud/administering/content-fragments/visual-content-fragments.md), et puisque les conceptions visuelles pour les expériences modulaires sont souvent créées dans Figma, il est également possible d’importer directement des conceptions de Figma dans AEM.

## Conditions préalables {#prerequisites}

Avant de commencer :

* L&#39;importation depuis Figma requiert une authentification. L’utilisateur ou l’utilisatrice Figma doit créer un jeton d’accès dans Figma et le stocker dans le service AEM.

  Pour ce faire, il faut :

   * génération d&#39;un jeton personnel à Figma
   * connexion à Adobe Experience Cloud à l’adresse `https://experience.adobe.com`
   * conserver le jeton à l’emplacement `https://experience.adobe.com/#/aem/figmatocontentfragment`

## Pour charger une conception {#to-upload-a-design}

Le flux se présente comme suit :

1. Le concepteur (utilisateur de Figma) crée la conception dans Figma.
1. L&#39;utilisateur de Figma crée un lien de partage vers l&#39;objet de conception dans Figma.
1. L’utilisateur Figma envoie le lien de partage à l’utilisateur AEM.
1. À partir d’une [invite](#sample-prompts) initiale, l’utilisateur d’AEM peut ensuite utiliser l’assistant d’IA pour interagir avec la tâche Figma vers fragments de contenu visuels et recréer automatiquement la conception approuvée dans AEM. AEM crée automatiquement les modèles de fragment de contenu, les fragments de contenu et les modèles HTML requis.
   * Si nécessaire, l’agent demandera des informations supplémentaires, telles que l’environnement AEM à utiliser.
   * Le processus de création d’agent comprend également des fonctionnalités qui permettent de réutiliser des modèles de contenu ou des fragments existants lorsqu’ils sont déjà disponibles.
1. L’agent génère un fragment de contenu et un modèle de fragment de contenu pour le contenu, ainsi qu’un modèle HTML pour la mise en page et la conception.
   * L’agent fournit un lien direct vers le fragment, à partir duquel vous pouvez accéder au modèle et au modèle.

## Exemples d’invites {#sample-prompts}

Voici quelques exemples d’invites :

* Pour importer depuis Figma :
   * Importer de Figma {*Figma_share_URL*} vers AEM
* Pour sélectionner le programme AEM à partir des suggestions d’agent :
   * Importer de Figma {*Figma_share_URL*} vers {*AEMaaCS_program/environment_link*}

## Ressources supplémentaires {#additional-resources}

Les ressources suivantes peuvent s’avérer utiles lorsque vous continuez à explorer les fragments de contenu visuel :

* [Fragments de contenu visuels](/help/sites-cloud/administering/content-fragments/visual-content-fragments.md)
* [Fragments de contenu visuels - Modèles](/help/implementing/developing/extending/content-fragments-visualization-templates.md)
* [Fragments de contenu visuels - Diffuser avec l’URL de publication](/help/implementing/developing/extending/content-fragments-visualization-publish-url.md)
