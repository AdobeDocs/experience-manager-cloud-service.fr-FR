---
title: Parcours de développement découplé AEM
description: Commencez ici pour un parcours guidé des fonctionnalités puissantes et flexibles d’AEM en mode découplé, leurs capacités et comment les exploiter dans votre premier projet de développement.
source-git-commit: bec1e901e19abc9ae99dbf95878e51c9b000a5ee
workflow-type: ht
source-wordcount: '736'
ht-degree: 100%

---


# Parcours de développement découplé AEM {#aem-headless-developer-journey}

Commencez ici pour un parcours guidé des fonctionnalités puissantes et flexibles d’AEM en mode découplé, leurs capacités et comment les exploiter dans votre premier projet de développement en mode découplé.

## Présentation {#introduction}

L’implémentation découplée devient de plus en plus importante pour offrir des expériences à votre public, où qu’il se trouve et quel que soit son canal.

L’implémentation découplée renonce à la gestion des pages et des composants, comme c’est généralement le cas avec les solutions complètes, et se concentre sur la création de fragments de contenu réutilisables et neutres du point de vue du canal, ainsi que sur leur diffusion entre canaux. Il s’agit d’un modèle de développement moderne et dynamique pour l’implémentation d’expériences numériques.

Ce guide vous accompagne tout au long des sujets les plus importants afin que vous puissiez :

* Comprendre pleinement ce qu’est la diffusion de contenu en mode découplé et ses avantages.
* Découvrir les fonctionnalités d’AEM en mode découplé et comment elles fonctionnent ensemble pour offrir une expérience découplée.
* Pouvoir effectuer les premières étapes de la mise en œuvre de votre premier projet AEM en mode découplé.

## Public {#audience}

Ce parcours est conçu pour le développeur. Il présente les exigences, les étapes et l’approche d’un projet AEM en mode découplé du point de vue du développeur. Le parcours définit des personnes supplémentaires avec lesquelles le développeur doit interagir pour un projet couronné de succès, mais le point de vue du parcours est celui du développeur.

Les informations présentes dans ce parcours peuvent bien sûr être utiles à d’autres personnes, mais certaines informations seront superflues pour certains rôles. Restez à l’écoute au sujet de prochains parcours concernant des rôles supplémentaires.

## Le parcours de développement découplé {#the-journey}

Vous allez explorer de nombreux sujets dans ce parcours. Les articles suivants vous apportent des connaissances fondamentales sur le mode découplé d’AEM et vous proposent un lien vers une documentation technique détaillée.

Bien que vous puissiez accéder directement à une partie spécifique du parcours, de nombreux concepts s’appuient sur ceux présentés dans des articles précédents. Si vous êtes novice concernant le mode découplé dans AEM, nous vous recommandons de commencer par le début et de progresser de manière séquentielle.

| N° | Article | Description |
|---|---|---|
| 0 | Parcours de développement découplé AEM | Ce document |
| 1 | [En savoir plus sur le développement CMS découplé ](learn-about.md) | Découvrez la technologie découplée et quand l’utiliser. |
| 2 | [Prise en main d’AEM découplé as a Cloud Service](getting-started.md) | En savoir plus sur les conditions préalables relatives à AEM découplé |
| 3 | [Accéder à votre première expérience à l’aide d’AEM découplé](path-to-first-experience.md) | Configurez votre environnement de développement et apprenez à intégrer une application simple avec AEM découplé. |
| 4 | [Comment modéliser votre contenu](model-your-content.md) | Découvrez comment modéliser votre structure de contenu. Ensuite, réalisez cette structure pour Adobe Experience Manager (AEM) à l’aide des modèles de fragment de contenu et des fragments de contenu, afin de la réutiliser sur plusieurs canaux. |
| 5 | [Accès à votre contenu à l’aide des API de diffusion AEM](access-your-content.md) | Découvrez comment utiliser des requêtes GraphQL pour accéder au contenu de vos fragments de contenu. |
| 6 | [Comment mettre à jour votre contenu à l’aide des API de ressources d’AEM](update-your-content.md) | Découvrez comment utiliser l’API REST pour accéder au contenu de vos fragments de contenu et le mettre à jour. |
| 7 | [Comment tout assembler – votre application et votre contenu dans AEM découplé](put-it-all-together.md) | Découvrez comment prendre votre projet AEM et le préparer pour la mise en ligne avec le SDK AEM découplé. |
| 8 | [Comment mettre en ligne votre application en mode découplé](go-live.md) | Découvrez comment déployer l’application en direct, placer votre code local dans le référentiel Git et le déplacer vers Cloud Manager Git pour le pipeline CI/CD. |
| 9 | [Facultatif – Comment créer des applications d’une seule page (SPA) avec AEM](create-spa.md) | Une fois que vous avez compris les fonctionnalités d’AEM en mode découplé, découvrez comment combiner une diffusion full stack et en mode découplé et comment créer des SPA modifiables à l’aide du framework de l’éditeur de SPA d’AEM. |

## Et après ?{#what-is-next}

Vous êtes maintenant prêt à prendre en main votre parcours Adobe en mode découplé. Nous vous encourageons à passer à la partie suivante du parcours et à lire l’article [En savoir plus sur le développement CMS découplé.](learn-about.md)

### Choisissez votre propre aventure {#choose-your-path}

Toutefois, Adobe souhaite que vous réussissiez à démarrer votre projet AEM découplé, quel que soit votre style d’apprentissage. Vous pouvez donc considérer ces deux options.

* Si vous préférez continuer à **découvrir les concepts du mode découplé et les technologies en mode découplé d’AEM**, vous devez continuer votre parcours avec AEM découplé comme le recommande le document [Comment modéliser votre contenu sous la forme de modèles de contenu](model-your-content.md) où vous apprendrez à modéliser votre structure de contenu dans AEM.
* Si vous préférez **apprendre en pratiquant**, vous pouvez passer au [tutoriel de prise en main d’AEM découplé](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html?lang=fr). Vous pourrez ainsi accéder directement au développement avec AEM découplé en mettant en œuvre un projet simple pour exposer un contenu découplé.
