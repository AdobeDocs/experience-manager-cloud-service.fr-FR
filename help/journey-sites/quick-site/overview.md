---
title: parcours de création rapide de site
description: Commencez ici pour obtenir un parcours guidé à travers l’outil de création rapide de site AEM convivial afin de rationaliser le développement front-end de votre site AEM et de personnaliser rapidement votre site sans aucune connaissance d’arrière-plan AEM.
exl-id: b8218232-0298-4b16-9dab-fa59be592a24
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '1030'
ht-degree: 18%

---

# parcours de création rapide de site {#quick-site-creation-journey}

Commencez ici pour obtenir un parcours guidé à travers l’outil de création rapide de site AEM convivial afin de rationaliser le développement front-end de votre site AEM et de personnaliser rapidement votre site sans aucune connaissance d’arrière-plan AEM.

## Présentation {#introduction}

AEM Sites est une suite d’outils puissants pour la création et la gestion d’expériences numériques. Les auteurs de contenu peuvent facilement créer des expériences numériques à l’aide de l’éditeur de sites et organiser le contenu à l’aide de la console Sites, tout en étant en mesure de voir le contenu en direct tel qu’il sera diffusé par AEM à vos audiences sur l’ensemble des canaux.

L’outil de création rapide de site permet aux non-développeurs de créer rapidement un site à partir de zéro à l’aide de modèles de site. Une fois créé, l’outil Création rapide de site permet également une personnalisation rapide du thème et du style du site AEM (JavaScript, CSS et ressources statiques). Cela permet au développeur front-end, qui n’a besoin d’aucune connaissance de l’AEM, de travailler séparément et parallèlement aux créateurs de contenu. L’administrateur d’AEM télécharge simplement le thème du site et le fournit au développeur front-end qui le personnalise à l’aide de ses outils favoris, puis valide les modifications dans le référentiel de code AEM, qui est ensuite déployé.

En éliminant toutes les connaissances des développeurs en matière de création de site, en éliminant les exigences de connaissances AEM pour le développement front-end et en permettant au développement de thème de se poursuivre en parallèle de la création de contenu, l’outil AEM création rapide de site accélère considérablement le délai d’évaluation de votre site et accroît la personnalisation et l’agilité du déploiement de votre site.

## Présentation vidéo {#video-overview}

Pour un aperçu rapide de cette fonctionnalité en action, [vous pouvez regarder cette introduction de cinq minutes.](https://www.youtube.com/watch?v=NQeQ1jZ7ZBw)

Ce parcours de documentation vous guide tout au long des étapes et des détails de la vidéo afin que vous compreniez le workflow et que vous puissiez recréer le processus dans votre propre environnement.

## Parcours de documentation AEM {#documentation-journeys}

Un [Parcours de documentation](/help/journey-documentation/documentation-journeys.md) relie de nombreux sujets et fonctionnalités différents et parfois complexes en aidant le lecteur, parfois débutant dans AEM, à comprendre et à résoudre un problème d’activité du début à la fin, tout en présupposant un minimum de connaissances préalables concernant le sujet ou AEM.

Les parcours de documentation sont conçus autour des principes de bonne pratique, reposent sur les dernières recherches d’Adobe, sur l’expérience éprouvée de mise en œuvre des consultants Adobe, ainsi que sur les retours de projets clients.

Si vous souhaitez savoir la manière dont Adobe recommande de résoudre des problèmes d’activité liés aux sites grâce à AEM, les parcours AEM Sites représentent un parfait point de départ.

## Public {#audience}

Ce parcours présente les exigences, les étapes et l’approche de personnalisation des thèmes AEM Sites. Son Principal public est le développeur front-end, qui n&#39;a pas besoin de connaître les AEM. Toutefois, pour illustrer l’ensemble du processus, le parcours implique les administrateurs, qui sont censés posséder des connaissances de base sur AEM Sites et Cloud Manager. En pratique, plusieurs personnes peuvent remplir plusieurs rôles et ce parcours prend en charge les perspectives des administrateurs et des développeurs front-end.

| Personne | Description | Rôle dans le Parcours |
|---|---|---|
| Développeurs front-end | Personnalise le thème du site | Prend le thème fourni par l’administrateur AEM et le personnalise afin qu’il puisse être déployé sur le site AEM. |
| Auteur de contenu | Crée et gère le contenu diffusé sous forme de sites. | Les auteurs de contenu créent du contenu sur AEM rendu avec le thème personnalisé par le développeur front-end. |
| Administrateur AEM | Crée un site AEM | L’administrateur d’AEM crée un site à partir d’un modèle, puis fournit au développeur front-end un thème à personnaliser. |
| Administrateur Cloud Manager | Création de pipelines et octroi d’accès | L’administrateur de Cloud Manager crée le pipeline frontal et accorde l’accès au développeur front-end afin de pouvoir personnaliser le référentiel git d’AEM. |

## Le Parcours de création rapide de site AEM {#the-journey}

Vous allez explorer de nombreux sujets dans ce parcours. Les articles suivants vous donnent des connaissances fondamentales sur la création et la personnalisation d’AEM sites à l’aide de l’outil de création rapide de site et vous proposent un lien vers une documentation technique détaillée.

|#|Article|Description|Rôle responsable |—|—|—|— |0|AEM Parcours de création rapide de site|Ce document|AEM et administrateurs de Cloud Manager| |1|[Présentation de Cloud Manager et du workflow de création rapide de site](cloud-manager.md)|Découvrez Cloud Manager et comment il relie le nouveau processus de création rapide de site.|AEM Administrateur| |2|[Créer un site à partir d’un modèle](create-site.md)|Découvrez comment créer rapidement un site AEM à l’aide d’un modèle de site.|AEM Administrateur| |3|[Configuration de votre pipeline](pipeline-setup.md)|Créez un pipeline frontal pour gérer la personnalisation du thème de votre site.|Administrateur Cloud Manager| |4|[Accorder l’accès au développeur front-end](grant-access.md)|Intégrez les développeurs front-end dans Cloud Manager afin qu’ils aient accès à votre référentiel git et à votre pipeline d’AEM site.|Administrateur Cloud Manager| |5|[Récupération des informations d’accès au référentiel git](retrieve-access.md)|Découvrez comment le développeur front-end utilise Cloud Manager pour accéder aux informations du référentiel git.|Développeurs front-end| |6|[Personnalisation du thème du site](customize-theme.md)|Découvrez comment un thème de site est créé, comment le personnaliser et comment le tester à l’aide du contenu d’AEM en direct.|Développeurs front-end| |7|[Déployer votre thème personnalisé](deploy-theme.md)|Découvrez comment déployer le thème du site à l’aide du pipeline.|Développeurs front-end|

## Et après ? {#what-is-next}

Vous êtes maintenant prêt à prendre en main votre parcours de création rapide de site Adobe.

* Si vous êtes un administrateur AEM ou Cloud Manager, ou si vous servez à la fois des rôles front-end de développeur et d’administrateur, ou si vous souhaitez simplement comprendre le processus de bout en bout dans AEM, veuillez commencer au début du parcours par [Présentation de Cloud Manager](cloud-manager.md) comme indiqué ci-dessous.
* Si vous n’êtes responsable que du développement frontal et que vous interagissez avec les administrateurs AEM et Cloud Manager, vous pouvez passer directement à [Récupération des informations d’accès au référentiel git](retrieve-access.md) pour accéder au référentiel git d’AEM et commencer la personnalisation.
* Si vous comprenez déjà qu’AEM Sites et Cloud Manager fonctionnent ensemble et que vous souhaitez commencer directement la configuration, vous pouvez [passez directement à la création d’un site à partir d’un modèle.](create-site.md)

## Ressources supplémentaires {#additional-resources}

Consultez ces ressources supplémentaires pour plus d’informations sur la manière dont les puissantes fonctionnalités d’AEM fonctionnent ensemble.

* [AEM documentation technique as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=fr) - Si vous maîtrisez déjà les AEM, vous pouvez consulter directement les documents techniques détaillés.
* [Documentation sur l’administration du site](/help/sites-cloud/administering/site-creation/create-site.md) - Consultez la documentation technique sur la création de site pour plus d’informations sur les fonctionnalités de l’outil de création rapide de site.
