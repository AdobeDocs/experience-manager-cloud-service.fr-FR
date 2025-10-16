---
title: Parcours du développeur CMS AEM Headless
description: Découvrez le développement découplé à l’aide d’Adobe Experience Manager (AEM) en tant que CMS découplé. Découvrez comment utiliser des fonctionnalités telles que les modèles de contenu, les fragments de contenu et l’API GraphQL afin d’optimiser la diffusion de contenu découplé.
landing-page-description: Découvrez la diffusion et la mise en œuvre du contenu découplé. Apprenez-en plus sur le développement de votre stratégie au sein de votre entreprise.
exl-id: d14a1e30-dd04-49a8-8cda-27c80a4bb0f5
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Architect, Developer
source-git-commit: 2ccca86a0e611b93c273e37abb6e0fd7870421d4
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 95%

---

# Parcours du développeur CMS AEM Headless {#aem-headless-developer-journey}

Bienvenue dans la documentation destinée aux développeurs et développeuses qui découvrent Adobe Experience Manager en tant que CMS découplé !

Découvrez tout un ensemble de fonctionnalités de découplage puissantes et flexibles, leurs capacités, ainsi que la façon de les utiliser dans votre premier projet de développement découplé. Ce parcours vous fournit toute les informations dont vous avez besoin pour développer votre première application découplée.

>[!CONTEXTUALHELP]
>id="aemcloud_headless_developer_resources"
>title="Ressources et documentation avancée pour le développement sur AEM Headless"
>abstract="Tout ce dont vous avez besoin pour en savoir plus sur le CMS d’AEM Headless et créer et diffuser de meilleures applications et offrir des expériences plus rapides."
>additional-url="https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=fr" text="Ressources de développement AEM Headless"


## Présentation {#introduction}

La mise en œuvre découplée d’AEM utilise des modèles de fragments de contenu et des fragments de contenu pour se concentrer sur la création de fragments de contenu structurés, neutres et réutilisables, ainsi que sur leur diffusion cross-canal. Pour cela, il faut abandonner la gestion de page et de composant telle qu’elle était traditionnellement réalisée dans les solutions de pile complètes. Il s’agit d’un modèle de développement moderne et dynamique pour l’implémentation d’expériences digitales.

Ce guide aborde les différents aspects de l’implémentation découplée dans AEM. À l’issue de celui-ci, vous pourrez effectuer les opérations suivantes :

* comprendre pleinement ce qu’est la diffusion de contenu découplé et ses avantages ;
* comprendre les fonctionnalités découplées AEM et comment elles s’associent pour vous offrir une expérience découplée ;
* effectuer les premières étapes de l’implémentation de votre premier projet AEM découplé.

## Audience {#audience}

Ce parcours est conçu à l’intention des développeurs et présente les exigences, les étapes et l’approche d’un projet AEM découplé du point de vue du développeur. Ce parcours définit les personnes supplémentaires avec lesquelles le développeur doit interagir pour réussir son projet, mais le point de vue du parcours est celui du développeur.

Voici les personnes qui interagissent dans ce parcours.

| Personne | Description | Rôle dans ce parcours |
|---|---|---|
| Développeur (audience cible) | Dispose de l’expérience nécessaire pour développer des applications découplées qui consomment du contenu provenant de différentes sources | Audience cible de ce parcours |
| Auteur de contenu | Crée et gère le contenu diffusé de façon découplée | Les auteurs de contenu créent du contenu que le développeur diffuse de façon découplée. |
| Administrateur | Gère les paramètres et la configuration de base d’AEM | Le développeur travaille avec l’administrateur pour apporter les modifications de configuration nécessaires au développement. |
| Architecte de contenu | Analyse les exigences relatives aux données qui doivent être diffusées en mode découplé et définit la structure de ces données | Les développeurs travaillent avec l’architecte de contenu pour comprendre la structure des données et les exigences nécessaires pour les diffuser en toute sécurité. |

## Le parcours de développement découplé {#the-journey}

De nombreux sujets seront abordés dans ce parcours, qui vous permettra d’acquérir les connaissances fondamentales du découplage dans AEM.

Bien que vous puissiez accéder directement à une partie spécifique du parcours, de nombreux concepts s’appuient sur ceux présentés dans des articles précédents. Adobe vous recommande de commencer par le début et d’avancer étape par étape.

| Numéro | Article | Description |
|---|---|---|
| 0 | Parcours du développeur AEM Headless | Ce document |
| 1 | [En savoir plus sur le développement CMS découplé](learn-about.md) | Découvrez la technologie découplée et quand l’utiliser. |
| 2 | [Prise en main d’AEM as a Cloud Service découplé](getting-started.md) | En savoir plus sur les prérequis d’AEM découplé |
| 3 | [Chemin d’accès à votre première expérience à l’aide d’AEM découplé](path-to-first-experience.md) | Configurez votre environnement de développement et apprenez à intégrer une application simple avec AEM découplé. |
| 4 | [Comment modéliser votre contenu](model-your-content.md) | Découvrez comment modéliser votre structure de contenu. |
| 5 | [Accès à votre contenu grâce aux API de diffusion AEM](access-your-content.md) | Découvrez comment utiliser des requêtes GraphQL pour accéder au contenu de vos fragments de contenu. |
| 6 | [Comment mettre à jour votre contenu grâce aux API d’AEM Assets](update-your-content.md) | Découvrez comment utiliser l’API REST pour accéder au contenu de vos fragments de contenu et le mettre à jour. |
| 7 | [Comment tout assembler – votre application et votre contenu dans AEM découplé](put-it-all-together.md) | Découvrez comment prendre votre projet AEM et le préparer pour la mise en ligne avec le SDK AEM découplé. |
| 8 | [Comment mettre en ligne votre application découplée](go-live.md) | Découvrez comment déployer l’application en direct et comment récupérer votre code local dans Git et le déplacer vers Cloud Manager Git pour le pipeline CI/CD. |
| 9 | [Facultatif – Comment créer des applications monopages avec AEM](create-spa.md) | Découvrez comment combiner une diffusion couplée et découplée et comment créer des SPA modifiables à l’aide du framework de l’éditeur SPA d’AEM. |

{style="table-layout:auto"}

## Prochaines étapes {#what-is-next}

Commencez par lire l’article suivant : [En savoir plus sur le développement découplé CMS](learn-about.md).

## Ressources supplémentaires {#additional-resources}

Les parcours de documentation vous montrent comment AEM permet de résoudre un problème professionnel en vous fournissant une narration qui vous guide tout au long des processus et des fonctionnalités. Un parcours illustre la façon dont plusieurs fonctionnalités fonctionnent ensemble pour répondre à un unique besoin professionnel.

Si vous préférez apprendre par la pratique et disposez d’une connaissance préalable d’AEM, suivez nos tutoriels pratiques organisés par API et par structure, qui explorent la création et l’utilisation d’applications reposant sur le découplage AEM. Voir [Tutoriels pour le découplage dans AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=fr).

Consultez ces parcours supplémentaires pour plus d’informations sur la manière dont les puissantes fonctionnalités d’AEM fonctionnent ensemble.

* [Portail de développement AEM](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=fr)
* [Parcours de traduction découplé AEM](/help/journey-headless/translation/overview.md) – Ce parcours de documentation vous donne une compréhension globale de la technologie découplée, de la manière dont AEM diffuse du contenu découplé et de la manière dont vous pouvez le traduire.
* [Parcours de création découplée](/help/journey-headless/author/overview.md) – Faites vos premiers pas avec cette visite guidée et découvrez les fonctionnalités découplées puissantes et flexibles d’AEM, leurs capacités et comment les modéliser votre contenu dans votre premier projet découplé.
* [Parcours d’architecture découplée](/help/journey-headless/architect/overview.md) – Faites vos premiers pas avec cette introduction sur les fonctionnalités puissantes, flexibles et découplées d’Adobe Experience Manager as a Cloud Service et comment modéliser le contenu de votre projet.
* [Documentation technique d’AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=fr) - Si vous avez déjà des connaissances solides sur AEM et les technologies de découplage, vous pouvez consulter directement notre documentation technique détaillée.
   * [Présentation d’AEM en tant que CMS découplé](/help/headless/introduction.md)
