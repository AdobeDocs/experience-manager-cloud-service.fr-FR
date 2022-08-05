---
title: Parcours du développeur AEM Headless
description: 'Commencez ici pour obtenir un parcours guidé via Adobe Experience Manager (AEM) as a Cloud Service lorsqu’il est utilisé comme système de gestion de contenu sans affichage (CMS). Découvrez les fonctionnalités puissantes et flexibles sans interface, leurs fonctionnalités et comment les exploiter dans votre premier projet de développement sans interface. Ce parcours vous fournit toutes les informations dont vous avez besoin pour développer votre première application sans interface. '
landing-page-description: 'Comprendre la diffusion et la mise en oeuvre de contenu sans interface utilisateur. En savoir plus sur le développement de votre stratégie au sein de votre entreprise. '
exl-id: d14a1e30-dd04-49a8-8cda-27c80a4bb0f5
source-git-commit: 1424c604e175cce0728f49f548d0bebec76043f4
workflow-type: tm+mt
source-wordcount: '1300'
ht-degree: 84%

---

# Parcours du développeur AEM Headless {#aem-headless-developer-journey}

Commencez ici pour un parcours guidé [!DNL Adobe Experience Manager as a Cloud Service] (AEM) lorsqu’il est utilisé comme système de gestion de contenu (CMS) sans affichage. Découvrez les fonctionnalités puissantes et flexibles sans interface, leurs fonctionnalités et comment les exploiter dans votre premier projet de développement sans interface. Ce parcours vous fournit toutes les informations dont vous avez besoin pour développer votre première application sans interface.

## Présentation {#introduction}

La mise en oeuvre sans affichage d’AEM utilise des modèles de fragments de contenu et des fragments de contenu pour se concentrer sur la création de fragments de contenu structurés, neutres et réutilisables, ainsi que sur leur diffusion cross-canal. Pour ce faire, la gestion des pages et des composants est abandonnée, comme c’est le cas dans les solutions de pile complètes. Il s’agit d’un modèle de développement moderne et dynamique pour l’implémentation d’expériences numériques.

Ce guide détaille les sujets les plus importants concernant l’implémentation du découplage dans AEM afin que vous puissiez :

* comprendre pleinement ce qu’est la diffusion de contenu découplé et ses avantages ;
* comprendre les fonctionnalités découplées AEM et comment elles s’associent pour vous offrir une expérience découplée ;
* effectuer les premières étapes de la mise en œuvre de votre premier projet AEM découplé.

## Parcours de documentation AEM {#documentation-journeys}

Un [Parcours de documentation](/help/journey-documentation/documentation-journeys.md) relie de nombreux sujets et fonctionnalités différents et parfois complexes en aidant le lecteur, parfois débutant dans AEM, à comprendre et à résoudre un problème d’activité du début à la fin, tout en présupposant un minimum de connaissances préalables concernant le sujet ou AEM.

Les parcours de documentation sont conçus autour des principes de bonne pratique, reposent sur les dernières recherches d’Adobe, sur l’expérience éprouvée de mise en œuvre des consultants Adobe, ainsi que sur les retours de projets clients.

Si vous souhaitez savoir comment Adobe recommande de résoudre des cas d’utilisation découplés avec AEM, les [Parcours découplés AEM](/help/journey-documentation/documentation-journeys.md) sont un bon endroit pour commencer.

>[!TIP]
>
> Si vous préférez **apprendre par la pratique** et préférez la technique à la théorie, consultez les tutoriels sur le découplage dans AEM, organisés par API et par structure et disponibles dans la [Section Ressources supplémentaires](#additional-resources) à la fin de ce document.

## Public {#audience}

Ce parcours est conçu à l’intention des développeurs et présente les exigences, les étapes et l’approche d’un projet AEM découplé du point de vue du développeur. Ce parcours définit les personnes supplémentaires avec lesquelles le développeur doit interagir pour réussir son projet, mais le point de vue du parcours est celui du développeur.

Voici les personnes qui interagissent dans ce parcours.

| Personne | Description | Rôle dans ce parcours |
|---|---|---|
| Développeur (audience cible) | Dispose de l’expérience nécessaire pour développer des applications découplées qui consomment du contenu provenant de différentes sources | Audience cible de ce parcours |
| Auteur de contenu | Crée et gère le contenu diffusé de façon découplée | Les auteurs de contenu créent du contenu que le développeur diffuse de façon découplée. |
| Administrateur | Gère les paramètres et la configuration de base d’AEM | Le développeur travaille avec l’administrateur pour apporter les modifications de configuration nécessaires au développement. |
| Architecte de contenu | Analyse les exigences relatives aux données qui doivent être diffusées en mode découplé et définit la structure de ces données | Les développeurs travaillent avec l’architecte de contenu pour comprendre la structure des données et les exigences nécessaires pour les diffuser en toute sécurité. |

Les informations contenues dans ce parcours peuvent être utiles à tous les acteurs, mais certaines informations ne sont pas nécessairement nécessaires pour certains rôles. Tenez-vous informés des [prochains parcours couvrant les spécificités des rôles supplémentaires.](/help/journey-documentation/documentation-journeys.md#journeys)

## Le parcours de développement découplé {#the-journey}

Vous découvrirez de nombreux sujets dans ce parcours. Les articles suivants vous donnent une connaissance fondamentale sur les projets découplés dans AEM et vous proposent des liens vers une documentation technique détaillée.

Bien que vous puissiez accéder directement à une partie spécifique du parcours, de nombreux concepts sont présentés dans des articles précédents. Par conséquent, si le concept de découplage dans AEM est nouveau pour vous, nous vous recommandons de commencer par le début et de progresser de manière chronologique.

| Numéro | Article | Description |
|---|---|---|
| 0 | Parcours du développeur AEM Headless | Ce document |
| 1 | [En savoir plus sur le développement CMS découplé](learn-about.md) | Découvrez la technologie découplée et quand l’utiliser. |
| 2 | [Prise en main d’AEM as a Cloud Service découplé](getting-started.md) | En savoir plus sur les prérequis d’AEM découplé |
| 3 | [Chemin d’accès à votre première expérience à l’aide d’AEM découplé](path-to-first-experience.md) | Configurez votre environnement de développement et apprenez à intégrer une application simple avec AEM découplé. |
| 4 | [Comment modéliser votre contenu](model-your-content.md) | Découvrez comment modéliser votre structure de contenu. Créez ensuite cette structure pour Adobe Experience Manager (AEM) à l’aide des modèles de fragments de contenu et des fragments de contenu, en vue de la réutiliser sur plusieurs canaux. |
| 5 | [Accès à votre contenu grâce aux API de diffusion AEM](access-your-content.md) | Découvrez comment utiliser des requêtes GraphQL pour accéder au contenu de vos fragments de contenu. |
| 6 | [Comment mettre à jour votre contenu grâce aux API d’AEM Assets](update-your-content.md) | Découvrez comment utiliser l’API REST pour accéder au contenu de vos fragments de contenu et le mettre à jour. |
| 7 | [Comment tout assembler – votre application et votre contenu dans AEM découplé](put-it-all-together.md) | Découvrez comment prendre votre projet AEM et le préparer pour la mise en ligne avec le SDK AEM découplé. |
| 8 | [Comment mettre en ligne votre application découplée](go-live.md) | Découvrez comment déployer l’application en direct et comment récupérer votre code local dans Git et le déplacer vers Cloud Manager Git pour le pipeline CI/CD. |
| 9 | [Facultatif – Comment créer des applications d’une seule page (SPA) avec AEM](create-spa.md) | Une fois que vous avez compris comment fonctionnent les fonctionnalités découplées AEM, découvrez comment combiner une diffusion utilisateur couplée et découplée et comment créer des SPA modifiables à l’aide de la structure de l’éditeur d’AEM. |

## Prochaines étapes {#what-is-next}

Vous êtes maintenant prêt à prendre en main votre parcours découplé Adobe. Nous vous encourageons à passer à la section suivante du parcours et à lire l’article [Découvrez le développement CMS découplé](learn-about.md).

### Choisissez votre propre parcours {#choose-your-path}

Toutefois, Adobe souhaite que vous réussissiez à démarrer votre projet AEM découplé, quel que soit votre style d’apprentissage. Considérez alors ces deux options.

* Si vous préférez continuer à **découvrir les concepts du mode découplé et les technologies en mode découplé d’AEM**, vous devez continuer votre parcours avec AEM découplé comme le recommande le document [Comment modéliser votre contenu sous la forme de modèles de contenu](model-your-content.md) où vous apprendrez à modéliser votre structure de contenu dans AEM.
* Si vous préférez **apprendre en pratiquant**, vous pouvez passer au [tutoriel de prise en main d’AEM découplé](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html?lang=fr). Vous pourrez ainsi accéder directement au développement avec AEM découplé en mettant en œuvre un projet simple pour exposer un contenu découplé.

## Ressources supplémentaires {#additional-resources}

Les parcours de documentation vous montrent comment AEM permet de résoudre un problème d’activité en vous fournissant une narration qui vous guide tout au long de processus et de fonctionnalités complexes et interconnectés. Un parcours illustre la façon dont plusieurs fonctionnalités fonctionnent ensemble pour répondre à un unique besoin d’activité.

Ces parcours sont conçus pour être autonomes. Cependant, un certain nombre d’entre eux sont connectés. Consultez ces parcours supplémentaires pour plus d’informations sur la manière dont les puissantes fonctionnalités d’AEM fonctionnent ensemble.

* [Tutoriels découplés AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=fr) : si vous préférez apprendre par la pratique et préférez la technique à la théorie, suivez nos tutoriels pratiques organisés par API et par structure, qui explorent la création et l’utilisation d’applications reposant sur le découplage AEM.
* [Parcours de traduction découplé AEM](/help/journey-headless/translation/overview.md) – Ce parcours de documentation vous donne une compréhension globale de la technologie découplée, de la manière dont AEM diffuse du contenu découplé et de la manière dont vous pouvez le traduire.
* [Parcours de création découplée](/help/journey-headless/author/overview.md) – Faites vos premiers pas avec cette visite guidée et découvrez les fonctionnalités découplées puissantes et flexibles d’AEM, leurs capacités et comment les modéliser votre contenu dans votre premier projet découplé.
* [Parcours d’architecture découplée](/help/journey-headless/architect/overview.md) –  Faites vos premiers pas avec cette introduction sur les fonctionnalités puissantes, flexibles et découplées d’Adobe Experience Manager as a Cloud Service et comment modéliser le contenu de votre projet.
* [Documentation technique d’AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=fr) – Si vous connaissez déjà bien les technologies AEM et découplées, vous pouvez consulter directement notre documentation technique détaillée.
