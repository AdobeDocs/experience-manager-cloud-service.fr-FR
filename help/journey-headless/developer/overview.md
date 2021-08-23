---
title: Parcours de développement découplé AEM
description: Faites vos premiers pas avec cette visite guidée et découvrez les fonctionnalités découplées puissantes et flexibles d’AEM, leurs capacités et comment les exploiter dans votre premier projet de développement.
exl-id: d14a1e30-dd04-49a8-8cda-27c80a4bb0f5
source-git-commit: d7d647e2114ed808ad29ed0802d838d257a9df03
workflow-type: tm+mt
source-wordcount: '1252'
ht-degree: 55%

---

# Parcours de développement découplé AEM {#aem-headless-developer-journey}

Faites vos premiers pas avec cette visite guidée et découvrez les fonctionnalités découplées puissantes et flexibles d’AEM, leurs capacités et comment les exploiter dans votre premier projet de développement découplé.

## Présentation {#introduction}

L’implémentation découplée devient de plus en plus importante pour offrir des expériences à votre public, où qu’il se trouve et quel que soit son canal.

L’implémentation découplée renonce à la gestion des pages et des composants, comme c’est généralement le cas avec les solutions complètes, et se concentre sur la création de fragments de contenu réutilisables et neutres du point de vue du canal, ainsi que sur leur diffusion entre canaux. Il s’agit d’un modèle de développement moderne et dynamique pour l’implémentation d’expériences numériques.

Ce guide vous accompagne tout au long des sujets les plus importants afin que vous puissiez :

* comprendre pleinement ce qu’est la diffusion de contenu découplé et ses avantages ;
* comprendre les fonctionnalités découplées AEM et comment elles s’associent pour vous offrir une expérience découplée ;
* effectuer les premières étapes de la mise en œuvre de votre premier projet AEM découplé.

## AEM Parcours de documentation {#documentation-journeys}

[A Documentation ](/help/journey-documentation/home.md) Journey rassemble de nombreux sujets et fonctionnalités différents et peut-être complexes en fournissant un récit qui aide le lecteur, qui peut être nouveau à AEM, comprendre et résoudre un problème d&#39;entreprise du début à la fin, tout en assumant un minimum de connaissances préalables ou AEM.

Les Parcours de documentation sont conçus autour des principes de bonnes pratiques, reposant sur les dernières recherches d’Adobe, l’expérience de mise en oeuvre éprouvée des consultants Adobe, ainsi que les commentaires des projets clients.

Si vous souhaitez savoir comment Adobe recommande de résoudre des cas d’entreprise sans interface avec AEM, AEM Parcours sans interface sont les points de départ.

>[!TIP]
>
> Si vous préférez **apprendre en faisant** et que vous êtes féru de technologie, consultez les tutoriels AEM sans affichage, qui sont organisés par API et structure et sont disponibles dans la [section Ressources supplémentaires](#additional-resources) à la fin de ce document.

## Public {#audience}

Ce parcours est conçu à l’intention des développeurs et présente les exigences, les étapes et l’approche d’un projet AEM découplé du point de vue du développeur. Le parcours définit des personnes supplémentaires avec lesquelles le développeur doit interagir pour un projet réussi, mais le point de vue du parcours est celui du développeur.

Voici les personnages qui interagissent dans ce parcours.

| Personnage | Description | Rôle dans le Parcours |
|---|---|---|
| Développeur | Expérience dans le développement d’applications sans interface utilisateur graphique qui consomment du contenu provenant de différentes sources | Public cible de ce parcours |
| Auteur de contenu | Crée et gère le contenu diffusé sans interface | Les auteurs de contenu créent du contenu que le développeur diffuse sans interface. |
| Administrateur | Gère la configuration et la configuration de base d’AEM | Le développeur travaille avec l’administrateur pour apporter les modifications de configuration nécessaires au développement. |
| Architecte de contenu | Analyse les exigences relatives aux données qui doivent être distribuées sans interface et définit la structure de ces données | Les développeurs travaillent avec l’architecte de contenu pour comprendre la structure des données et les exigences nécessaires pour les diffuser en toute sécurité. |
| Spécialiste de traduction | Définit le contenu à traduire et gère ces workflows. | Le spécialiste de traduction travaille avec l’architecte de contenu pour définir l’organisation initiale du contenu et peut avoir besoin de travailler avec le développeur pour toute exigence spécifique à la traduction. |

L&#39;information dans ce parcours peut bien sûr être utile à tous les acteurs, mais certaines informations peuvent être superflues à certains rôles. Restez en ligne pour les [prochains parcours couvrant des rôles supplémentaires.](/help/journey-documentation/home.md#journeys)

## Le parcours de développement découplé {#the-journey}

Vous allez explorer de nombreux sujets dans ce parcours. Les articles suivants vous donnent une connaissance fondamentale sur les projets découplés dans AEM et vous proposent des liens vers une documentation technique détaillée.

Bien que vous puissiez accéder directement à une partie spécifique du parcours, de nombreux concepts sont présentés dans des articles précédents. Par conséquent, si le concept de découplage dans AEM est nouveau pour vous, nous vous recommandons de commencer par le début et de progresser de manière chronologique.

| Numéro | Article | Description |
|---|---|---|
| 0 | Parcours de développement découplé AEM | Ce document |
| 1 | [En savoir plus sur le développement CMS découplé](learn-about.md) | Découvrez la technologie découplée et quand l’utiliser. |
| 2 | [Prise en main d’AEM as a Cloud Service découplé](getting-started.md) | En savoir plus sur les conditions préalables d’AEM découplé |
| 3 | [Chemin d’accès à votre première expérience à l’aide d’AEM découplé](path-to-first-experience.md) | Configurez votre environnement de développement et apprenez à intégrer une application simple avec AEM découplé. |
| 4 | [Comment modéliser votre contenu](model-your-content.md) | Découvrez comment modéliser votre structure de contenu. Créez ensuite cette structure pour Adobe Experience Manager (AEM) à l’aide des modèles de fragments de contenu et des fragments de contenu, en vue de la réutiliser sur plusieurs canaux. |
| 5 | [Comment accéder à votre contenu grâce aux API de diffusion AEM](access-your-content.md) | Découvrez comment utiliser des requêtes GraphQL pour accéder au contenu de vos fragments de contenu. |
| 6 | [Comment mettre à jour votre contenu via les API AEM Assets](update-your-content.md) | Découvrez comment utiliser l’API REST pour accéder au contenu de vos fragments de contenu et le mettre à jour. |
| 7 | [Comment tout assembler – votre application et votre contenu dans AEM découplé](put-it-all-together.md) | Découvrez comment prendre votre projet AEM et le préparer pour la mise en ligne avec le SDK AEM découplé. |
| 8 | [Comment mettre en ligne votre application découplée](go-live.md) | Découvrez comment déployer l’application en direct et comment récupérer votre code local dans Git et le déplacer vers Cloud Manager Git pour le pipeline CI/CD. |
| 9 | [Facultatif – Comment créer des applications d’une seule page (SPA) avec AEM](create-spa.md) | Une fois que vous avez compris comment fonctionnent les fonctionnalités découplées AEM, découvrez comment combiner une diffusion utilisateur couplée et découplée et comment créer des SPA modifiables à l’aide de la structure de l’éditeur d’AEM. |

## Et après ? {#what-is-next}

Vous êtes maintenant prêt à prendre en main votre parcours découplé Adobe. Nous vous encourageons à passer à la section suivante du parcours et à lire l’article [Découvrez le développement CMS découplé](learn-about.md).

### Choisissez votre propre parcours {#choose-your-path}

Toutefois, Adobe souhaite que vous réussissiez à démarrer votre projet AEM découplé, quel que soit votre style d’apprentissage. Considérez alors ces deux options.

* Si vous préférez continuer à **découvrir les concepts du mode découplé et les technologies en mode découplé d’AEM**, vous devez continuer votre parcours avec AEM découplé comme le recommande le document [Comment modéliser votre contenu sous la forme de modèles de contenu](model-your-content.md) où vous apprendrez à modéliser votre structure de contenu dans AEM.
* Si vous préférez **apprendre en pratiquant**, vous pouvez passer au [tutoriel de prise en main d’AEM découplé](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html?lang=fr). Vous pourrez ainsi accéder directement au développement avec AEM découplé en mettant en œuvre un projet simple pour exposer un contenu découplé.

## Ressources supplémentaires {#additional-resources}

Les parcours de documentation vous montrent comment AEM résoudre un problème d’entreprise en vous fournissant une narration qui vous guide tout au long de processus et de fonctionnalités complexes et interconnectés. Un parcours illustre la façon dont plusieurs fonctionnalités fonctionnent ensemble pour répondre aux besoins d’une seule entreprise.

Ces parcours sont conçus pour être autonomes. Cependant, un certain nombre d’entre elles peuvent être liées. Consultez ces parcours supplémentaires pour plus d’informations sur la manière dont AEM puissantes fonctionnalités fonctionnent ensemble.

* [AEM tutoriels sans affichage](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=fr)  - Si vous préférez apprendre par le travail et êtes plus intéressé par les questions techniques, suivez nos tutoriels pratiques organisés par API et structure, qui explorent la création et l’utilisation d’applications basées sur AEM sans affichage.
* [AEM Parcours](/help/journey-headless/translation/overview.md)  de traduction sans interface - Ce parcours de documentation vous donne une large compréhension de la technologie sans interface, de la manière dont AEM diffuse du contenu sans interface et de la manière dont vous pouvez le traduire.
* [Parcours](/help/journey-headless/author/overview.md)  de création sans tête : commencez ici pour un parcours guidé à travers les puissantes fonctionnalités et flexibles d’AEM sans tête, leurs fonctionnalités et comment modéliser votre contenu sur votre premier projet sans tête.
* [Parcours](/help/journey-headless/architect/overview.md)  Architecte sans tête : commencez ici pour découvrir les fonctionnalités puissantes, flexibles et sans tête d’Adobe Experience Manager en tant que Cloud Service, ainsi que comment modéliser du contenu pour votre projet.
* [AEM en tant que documentation technique](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=fr)  de Cloud Service : si vous maîtrisez déjà les technologies AEM et sans interface, vous pouvez consulter directement nos documents techniques détaillés.
