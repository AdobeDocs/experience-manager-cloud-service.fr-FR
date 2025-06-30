---
title: Parcours de création rapide de site AEM
description: Commencez ici votre parcours guidé à travers l’outil convivial de création rapide de site AEM, qui vous permet de rationaliser le développement front-end de votre site AEM et de personnaliser rapidement ce site sans aucune connaissance du back-end AEM.
exl-id: b8218232-0298-4b16-9dab-fa59be592a24
solution: Experience Manager Sites
feature: Developing
role: Admin, Developer
source-git-commit: 34c2604c7dcc2a1b27f617fe2d88eeb7496b3456
workflow-type: ht
source-wordcount: '1020'
ht-degree: 100%

---

# Parcours de création rapide de site AEM {#quick-site-creation-journey}

{{traditional-aem}}

Commencez ici votre parcours guidé à travers l’outil convivial de création rapide de site AEM, qui vous permet de rationaliser le développement front-end de votre site AEM et de personnaliser rapidement ce site sans aucune connaissance du back-end AEM.

## Présentation {#introduction}

AEM Sites est une suite d’outils puissants pour la création et la gestion d’expériences digitales. Les auteurs et autrices de contenu peuvent facilement créer des expériences numériques à l’aide de l’éditeur de sites et organiser le contenu à l’aide de la console Sites, tout en étant en mesure de voir le contenu en direct tel qu’il est diffusé par AEM à vos audiences sur l’ensemble des canaux.

L’outil de création rapide de site AEM permet aux non-développeurs de créer rapidement un site à partir de zéro à l’aide de modèles de sites. Une fois créé, l’outil de création rapide de site permet également une personnalisation rapide du thème et du style du site AEM (JavaScript, CSS et ressources statiques). Cela permet au développeur front-end, qui n’a besoin d’aucune connaissance d’AEM, de travailler séparément et parallèlement aux créateurs de contenu. L’administrateur d’AEM télécharge simplement le thème du site et le fournit au développeur front-end, qui le personnalise à l’aide de ses outils favoris, puis valide les modifications dans le référentiel de code AEM, qui est ensuite déployé.

En éliminant le besoin de connaissance du développement en matière de création de sites, en éliminant les exigences de connaissance d’AEM pour le développement front-end et en permettant au développement de thèmes de se poursuivre parallèlement à la création de contenu, l’outil de création rapide de site AEM accélère de manière considérable le temps nécessaire à la valorisation de votre site et accroît la personnalisation et l’agilité du déploiement de votre site.

## Présentation vidéo {#video-overview}

Pour une vue d’ensemble rapide de cette fonctionnalité en action, [vous pouvez regarder cette présentation de cinq minutes](https://www.youtube.com/watch?v=NQeQ1jZ7ZBw).

Ce parcours de documentation vous guide à travers les fonctionnalités en vidéo, vous permettant de les découvrir étape par étape et en détail. Cela vous permet de comprendre le workflow et de recréer le processus dans votre propre environnement.

## Parcours de documentation AEM {#documentation-journeys}

[Un parcours de documentation](/help/journey-documentation/documentation-journeys.md) relie de nombreux sujets et fonctionnalités différents et compliqués en aidant le lecteur ou la lectrice, qui débute parfois dans AEM, à comprendre et à résoudre un problème d’activité du début à la fin, tout en présupposant un minimum de connaissances préalables concernant le sujet ou AEM.

Les parcours de documentation sont conçus autour des principes de bonne pratique, reposent sur les dernières recherches d’Adobe, sur l’expérience éprouvée de mise en œuvre des consultants Adobe, ainsi que sur les retours de projets clients.

Si vous souhaitez savoir la manière dont Adobe recommande de résoudre des problèmes d’activité liés aux sites grâce à AEM, les parcours AEM Sites représentent un parfait point de départ.

## Public {#audience}

Ce parcours présente les exigences, les étapes et les méthodes de personnalisation des thèmes AEM Sites. Son principal public est le développeur front-end, qui n’a pas besoin de connaître AEM. Toutefois, pour illustrer l’ensemble du processus, le parcours implique l’administration, qui est censée posséder des connaissances de base sur AEM Sites et Cloud Manager. En pratique, de nombreuses personnes peuvent remplir plusieurs fonctions et ce parcours prend en charge les perspectives des administrateurs et des développeurs front-end.

| Personne | Description | Rôle dans le Parcours |
|---|---|---|
| Développeur front-end | Personnalise le thème du site | Prend le thème fourni par l’administrateur AEM et le personnalise afin qu’il puisse être déployé sur le site AEM. |
| Auteur de contenu | Crée et gère le contenu diffusé sur des sites. | Les auteurs de contenus créent du contenu sur AEM rendu avec le thème personnalisé par le développeur front-end. |
| Administrateur AEM | Crée un nouveau site AEM | L’administrateur d’AEM crée un site à partir d’un modèle, puis fournit au développeur front-end un thème à personnaliser. |
| Administrateur Cloud Manager | Crée des pipelines et octroie des accès | L’administrateur Cloud Manager crée le pipeline front-end et accorde l’accès au développeur front-end afin de pouvoir valider les personnalisations dans le référentiel Git d’AEM. |

## Le parcours de création rapide de site AEM {#the-journey}

Vous découvrirez de nombreux sujets dans ce parcours. Les articles suivants vous donnent des connaissances fondamentales sur la création et la personnalisation d’AEM Sites à l’aide de l’outil de création rapide de site et vous proposent un lien vers une documentation technique détaillée.

| Numéro | Article | Description | Rôle responsable |
|---|---|---|--|
| 0 | Parcours de création rapide de site AEM | Ce document | Administration d’AEM et de Cloud Manager |
| 1 | [Présentation de Cloud Manager et du workflow de création rapide de site](cloud-manager.md) | Découvrez Cloud Manager et comment il relie le nouveau processus de création rapide de site. | Administration AEM |
| 2 | [Créer un site à partir d’un modèle](create-site.md) | Découvrez comment créer rapidement un site AEM à l’aide d’un modèle de site. | Administration AEM |
| 3 | [Configurer le pipeline](pipeline-setup.md) | Créez un pipeline front-end pour gérer la personnalisation du thème de votre site. | Administration Cloud Manager |
| 4 | [Accorder l’accès au développeur ou à la développeuse front-end](grant-access.md) | Intégrez les développeurs et développeuses front-end à Cloud Manager afin qu’ils aient accès au référentiel Git et au pipeline de votre site AEM. | Administration Cloud Manager |
| 5 | [Récupérer des informations d’accès au référentiel Git](retrieve-access.md) | Découvrez comment le développeur ou la développeuse front-end utilise Cloud Manager pour accéder aux informations du référentiel Git. | Développement front-end |
| 6 | [Personnaliser le thème du site](customize-theme.md) | Découvrez comment un thème de site est créé, comment le personnaliser et comment le tester à l’aide du contenu réel d’AEM. | Développement front-end |
| 7 | [Déployer votre thème personnalisé](deploy-theme.md) | Découvrez comment déployer le thème du site à l’aide du pipeline. | Développement front-end |

## Prochaines étapes {#what-is-next}

Vous êtes maintenant prêt à commencer votre parcours de création rapide de site Adobe.

* Si vous faites partie de l’administration d’AEM ou de Cloud Manager, ou si vous jouez à la fois les rôles de développement front-end et d’administration, ou encore si vous souhaitez simplement comprendre le processus de bout en bout dans AEM, commencez au début du parcours par [Comprendre Cloud Manager](cloud-manager.md) comme indiqué ci-dessous.
* Si vous n’êtes responsable que du développement front-end et que vous interagissez avec les administrateurs et les administratrices d’AEM et de Cloud Manager, vous pouvez passer directement à [Récupération des informations d’accès au référentiel Git](retrieve-access.md) pour accéder au référentiel Git d’AEM et commencer la personnalisation.
* Si vous comprenez déjà qu’AEM Sites et Cloud Manager fonctionnent ensemble et que vous souhaitez commencer directement la configuration, vous pouvez [passer directement à la création d’un site à partir d’un modèle](create-site.md).

## Ressources supplémentaires {#additional-resources}

Consultez ces ressources supplémentaires pour plus d’informations sur la manière dont les puissantes fonctionnalités d’AEM fonctionnent ensemble.

* [Documentation technique d’AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=fr) : si vous connaissez déjà bien AEM, vous pouvez directement consulter notre documentation technique détaillée.
* [Documentation sur l’administration du site](/help/sites-cloud/administering/site-creation/create-site.md) : consultez la documentation technique relative à la création de site pour plus d’informations sur les fonctionnalités de l’outil de création rapide de site.
