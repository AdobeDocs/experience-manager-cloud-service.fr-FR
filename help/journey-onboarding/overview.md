---
title: Présentation du Parcours d’intégration as a Cloud Service
description: Commencez ici pour avoir un aperçu du parcours guidé tout au long du processus d’intégration pour AEM as a Cloud Service.
exl-id: 892577db-05dc-49ff-bb2c-203efdb89c8c
source-git-commit: 75c0e8cbaa409fa48750e794c27ace98eda107d0
workflow-type: tm+mt
source-wordcount: '1175'
ht-degree: 25%

---


# Parcours d’intégration {#onboarding-journey}

Félicitations d&#39;avoir choisi AEM as a Cloud Service ! Ce document constitue le point de départ d’un parcours guidé tout au long du processus d’intégration. Que vous déployiez une nouvelle application ou migriez une application existante, ce parcours d’intégration garantit que vos équipes sont configurées et ont accès à AEM as a Cloud Service.

## Présentation {#introduction}

L’intégration est le processus par lequel un administrateur système désigné configure AEM as a Cloud Service pour votre organisation. Il inclut l’approvisionnement initial des ressources cloud et l’affectation des utilisateurs à des rôles en fonction de leurs responsabilités professionnelles. Par conséquent, chaque membre peut se connecter et accéder à ses ressources AEM as a Cloud Service.

![Le parcours d’intégration](/help/journey-onboarding/assets/onboarding-journey.png)

Ce guide vous guide tout au long des rubriques d’intégration les plus importantes afin que vous puissiez :

* Une compréhension complète des différents termes, services et utilisateurs impliqués dans le processus d’intégration.
* Avoir permis à votre équipe de se mettre en route et de commencer à apprendre à créer et développer du contenu pour votre application AEM as a Cloud Service.

Par conséquent :

* Votre équipe sera configurée et aura accès aux ressources cloud.
* AEM auteurs auront accès à AEM as a Cloud Service et pourront commencer à créer du contenu.
* Les développeurs AEM et les responsables de déploiement auront accès à AEM as a Cloud Service et pourront commencer à créer et déployer des applications personnalisées.

## Concepts et objectif {#concepts}

Bien qu&#39;il semble y avoir beaucoup à apprendre à commencer avec AEM as a Cloud Service, il n&#39;y a conceptuellement que quelques éléments logiques.

* **Le contrat** - Vous devez connaître votre contrat d’Adobe, car il définit les aspects du processus d’intégration.
* **Admin Console** - C’est là que les utilisateurs sont gérés et que les rôles sont affectés.
* **Cloud Manager** - Il s’agit de l’outil permettant de configurer des ressources telles que des programmes et des environnements. C’est également là que vous accédez à git et créez des pipelines pour gérer et déployer votre code personnalisé.

Ces concepts seront présentés en détail dans ce parcours d&#39;intégration. L’objectif est qu’à la fin du parcours, vous :

* Ont accordé aux utilisateurs l’accès nécessaire à AEMaaCS
* avoir configuré les premières ressources cloud pour votre projet ;
* Découvrez comment déployer votre premier code et créer votre premier contenu.

Fondamentalement, vous allez tomber sur le terrain avec votre nouveau projet as a Cloud Service AEM !

## Public {#audience}

Le parcours d’intégration est écrit spécifiquement pour la variable **administrateur système** des nouveaux clients à AEM as a Cloud Service et à AEM en général. L’administrateur système est la personne qui est contactée pour la première fois par Adobe après la signature de votre contrat as a Cloud Service AEM. Il s’agit généralement de la première personne à accéder à vos ressources as a Cloud Service AEM et à les configurer. Si vous lisez ceci, vous êtes probablement l’administrateur système.

L’administrateur système gère tous les aspects des utilisateurs AEMaaCS de leur entreprise, de l’accès aux autorisations. Cependant, l’administrateur système doit interagir avec d’autres personnes en cours de route.

| Personne | Description | Rôle dans le Parcours |
|---|---|---|
| Administrateur système | Target de ce parcours fournit la configuration initiale des ressources cloud et l’affectation des utilisateurs aux rôles appropriés en fonction de leurs responsabilités professionnelles. | Gère tous les aspects des utilisateurs de l’accès aux autorisations |
| Auteur de contenu | Crée et révise le contenu dans AEM | Une fois les autorisations accordées par l’administrateur système, les auteurs peuvent commencer leur propre parcours à créer du contenu. |
| Développeur | Développe des applications AEM qui consomment du contenu provenant de différentes sources. | Une fois les autorisations accordées par l’administrateur système, les développeurs peuvent lancer leurs propres solutions de développement de parcours. |
| Responsable de déploiement | Ajoute ou met à jour un environnement, exécute des pipelines et déploie le code vers AEM environnement ou la qualité du code. | Une fois les autorisations accordées par l’administrateur système, les gestionnaires de déploiement peuvent lancer leur propre parcours de gestion des déploiements. |

Ce guide d’intégration illustre l’ensemble du processus d’intégration en tant qu’administrateur système. Les rôles des utilisateurs, développeurs et gestionnaires de déploiement d’AEM sont brièvement présentés comme des parties supplémentaires et facultatives du parcours.

>[!TIP]
>
>Si vous découvrez AEM as a Cloud Service, mais que vous connaissez déjà AEM et que vous migrez depuis On-Premise ou Adobe Managed Services, assurez-vous de consulter la section [AEM Parcours de migration as a Cloud Service.](/help/journey-migration/getting-started.md)

## Présentation du Parcours d’intégration {#overview}

Les articles suivants décrivent en détail les principaux concepts d’intégration et vous donnent des connaissances fondamentales sur AEM as a Cloud Service. Bien que vous puissiez accéder directement à une partie spécifique du parcours, de nombreux concepts sont présentés dans des articles précédents. Par conséquent, si le concept d’intégration est nouveau pour vous, nous vous recommandons de commencer par le début et de progresser de manière chronologique.

| Numéro | Article | Description | Public |
|---|---|---|---|
| 0 | Parcours d’intégration | Ce document | Administrateur système |
| 1 | [Préparation à l’intégration](preparation.md) | Avant que le processus d’intégration ne commence, l’administrateur système doit comprendre un certain nombre d’étapes préparatoires avant de se connecter au système. | Administrateur système |
| 2 | [Terminologie as a Cloud Service AEM](terminology.md) | Avant de vous connecter pour la première fois à AEMaaCS, il est utile de comprendre la terminologie du système et sa structure de base. | Administrateur système |
| 3 | [Le Admin Console](admin-console.md) | Découvrez ce qu’est le Admin Console, comment vous connecter et comment vérifier votre profil en tant qu’administrateur système. | Administrateur système |
| 4 | [Attribution de profils de produit Cloud Manager](assign-profiles-cloud-manager.md) | Passez en revue les profils de produit Cloud Manager et apprenez à affecter des membres de l’équipe aux profils de produit Cloud Manager. | Administrateur système |
| 5 | [Accès à Cloud Manager](cloud-manager.md) | Découvrez comment accéder à Cloud Manager afin de pouvoir configurer les ressources de votre projet. | Administrateur système |
| 6 | [Création d’un programme](create-program.md) | Découvrez comment créer un programme à l’aide de Cloud Manager. | Administrateur système |
| 7 | [Créer des environnements](create-environments.md) | Découvrez comment créer un environnement à l’aide de Cloud Manager. | Administrateur système |
| 8 | [Attribution de profils de produit AEM](assign-profiles-aem.md) | Découvrez comment l’administrateur système assigne les membres de votre équipe à des profils de produit AEM as a Cloud Service. | Administrateur système |
| 9 | [Tâches du développeur et du responsable de déploiement](developers.md) | Facultatif - Découvrez comment en tant que développeur vous pouvez accéder à Cloud Manager Git et comment, en tant que responsable de déploiement, vous pouvez configurer des pipelines et déployer du code dans Cloud Manager. | Développeurs et responsables de déploiement |
| 10 | [Tâches utilisateur AEM](aem-users.md) | Facultatif - Découvrez comment, en tant qu’auteur AEM, vous pouvez accéder à AEM instance as a Cloud Service et vous familiariser avec la création de contenu pour l’instance as a Cloud Service. | Utilisateurs AEM |

## Prochaines étapes {#what-is-next}

Vous êtes maintenant prêt à démarrer votre parcours d’intégration as a Cloud Service AEM. Nous vous encourageons à passer à la partie suivante du parcours et à lire l’article [Préparation à l’intégration](preparation.md)

## Parcours de documentation AEM {#documentation-journeys}

Un [Parcours de documentation](/help/journey-documentation/documentation-journeys.md) relie de nombreux sujets et fonctionnalités différents et parfois complexes en aidant le lecteur, parfois débutant dans AEM, à comprendre et à résoudre un problème d’activité du début à la fin, tout en présupposant un minimum de connaissances préalables concernant le sujet ou AEM.

Les parcours de documentation sont conçus autour des principes de bonne pratique, reposent sur les dernières recherches d’Adobe, sur l’expérience éprouvée de mise en œuvre des consultants Adobe, ainsi que sur les retours de projets clients.

Si vous souhaitez savoir comment Adobe recommande d’intégrer votre équipe à votre nouvelle application as a Cloud Service AEM, voici où commencer.
