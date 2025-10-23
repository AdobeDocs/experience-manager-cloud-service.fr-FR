---
title: Présentation du Parcours d’intégration d’AEM as a Cloud Service
description: Commencez ici pour avoir un aperçu du parcours guidé tout au long du processus d’intégration pour AEM as a Cloud Service.
exl-id: 892577db-05dc-49ff-bb2c-203efdb89c8c
recommendations: noDisplay
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 858a9c4b61fd3a80a257313e48816b067ca77175
workflow-type: tm+mt
source-wordcount: '1362'
ht-degree: 93%

---


# Parcours d’intégration {#onboarding-journey}

Félicitations pour avoir choisi AEM as a Cloud Service. Ce document constitue le point de départ d’un parcours guidé tout au long du processus d’intégration. Qu’il s’agisse de déployer une nouvelle application ou de migrer une application déjà existante, ce parcours d’intégration permet de configurer vos équipes. Il garantit qu’elles ont accès à AEM as a Cloud Service.

## Présentation {#introduction}

Adobe Experience Manager (AEM) offre une certaine flexibilité sur les approches de diffusion et de création de contenu, ce qui permet aux équipes de choisir le modèle le mieux adapté à leurs besoins.

Utilisez [Edge Delivery Services](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/edge-delivery/overview) pour une création rapide et itérative et une vitesse de contenu élevée, ou utilisez le service de diffusion de Publication traditionnel pour un modèle de publication d’entreprise robuste. Les deux approches permettent aux entreprises de fournir des expériences digitales exceptionnelles de la manière qui leur convient le mieux. Pour commencer à utiliser Edge Delivery Services, consultez la [Présentation de Edge Delivery Services](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/edge-delivery/overview) et pour en savoir plus sur les options de création modernes, consultez le [Guide de création](https://www.aem.live/docs/authoring-guide).

L’intégration est le processus au cours duquel un la personne chargée de l’administration système désignée configure AEM as a Cloud Service pour votre organisation. Ce processus inclut l’approvisionnement initial des ressources cloud et l’affectation des utilisateurs et utilisatrices à des rôles en fonction de leurs responsabilités professionnelles. Par conséquent, chaque membre peut se connecter et accéder à ses ressources sur AEM as a Cloud Service.

![Parcours d’intégration](/help/journey-onboarding/assets/onboarding-journey.png).

Ce guide vous conduit à travers les sujets les plus importants de l’intégration de sorte qu’à la fin, vous aurez :

* Une compréhension complète des différents termes, services et utilisateurs impliqués dans le processus d’intégration.
* Permis à votre équipe de se mettre en route et de commencer à apprendre à créer et développer du contenu pour votre application AEM as a Cloud Service.

Par conséquent :

* Votre équipe est prête et a accès aux ressources cloud.
* Les auteurs et autrices AEM auront accès à AEM as a Cloud Service et pourront commencer à créer du contenu.
* Les responsables de déploiement et les développeurs ou développeuses AEM auront accès à AEM as a Cloud Service et pourront commencer à créer et déployer des applications personnalisées.

## Concepts et objectif {#concepts}

<!-- Although there may appear to be a lot to learn when getting started with AEM as a Cloud Service, conceptually there are only a few, logical pieces.-->

Le parcours d’intégration d’AEM as a Cloud Service est axé sur les éléments principaux suivants :

* **Contrat** : consultez votre contrat Adobe pour connaître les détails essentiels du processus d’intégration.
* **Experience Hub** : utilisez [experience.adobe.com](https://experience.adobe.com/) comme point d’entrée central pour les fonctionnalités d’AEM. Experience Hub s’adapte à votre persona et à vos droits afin que vous puissiez travailler efficacement. À partir de là, accédez à :
   * **Admin Console** : gérez les utilisateurs et utilisatrices, et attribuez des rôles.
   * **Cloud Manager** : configurez des programmes et des environnements, accédez à Git et créez des pipelines pour gérer et déployer du code personnalisé.
   * **Sites** : créez, gérez et diffusez des expériences digitales. (Droit basé sur une licence)
   * **Assets** : organisez, stockez et distribuez vos ressources numériques. (Droit basé sur une licence)
   * **Forms** : créez et gérez des formulaires adaptatifs et réactifs. (Droit basé sur une licence)

Ces concepts seront présentés en détail dans ce parcours d’intégration. L’objectif est qu’à la fin du parcours, vous puissiez effectuer les opérations suivantes :

* Accorder l’accès nécessaire à AEM as a Cloud Service à l’utilisateur ou à l’utilisatrice.
* Configurer les premières ressources cloud pour votre projet.
* Découvriez comment déployer votre premier code et créer votre premier contenu.

En gros, vous allez pouvoir commencer directement avec votre nouveau projet AEM as a Cloud Service !

## Audience {#audience}

Le parcours d’intégration est écrit spécifiquement pour l’**administrateur ou administratrice système** de la clientèle qui découvre AEM as a Cloud Service et d’AEM en général. L’administrateur ou administratrice système est la personne qu’Adobe contacte en premier lieu après la signature de votre contrat AEM as a Cloud Service. Il s’agit généralement de la première personne à accéder à vos ressources et à les configurer sur AEM as a Cloud Service. Si vous lisez cette rubrique, il est probable que vous soyez l’administrateur ou l’administratrice système.

L’administrateur ou administratrice système gère tous les aspects des utilisateurs et utilisatrices AEMaaCS de son entreprise, de l’accès aux autorisations. Cependant, l’administrateur ou administratrice système doit interagir avec d’autres personnes tout au long de son parcours.

| Personne | Description | Rôle dans le Parcours |
| --- | --- | --- |
| Administrateur système | L’objectif de ce parcours est de veiller au déploiement initial des ressources cloud et à l’assignation des utilisateurs et des utilisatrices aux rôles appropriés selon leurs responsabilités professionnelles. | Le rôle vous permet de gérer tous les aspects liés aux utilisateurs et utilisatrices, depuis l’accès jusqu’aux autorisations. |
| Créateur ou créatrice de contenu | Crée et révise le contenu dans AEM. | Une fois les autorisations accordées par l’administrateur ou administratrice système, les personnes chargées de la création de contenu peuvent commencer leur propre parcours. |
| Développeur ou développeuse | Développe des applications AEM qui consomment du contenu provenant de différentes sources. | Une fois les autorisations accordées par l’administrateur ou administratrice système, les personnes chargées du développement peuvent commencer leur propre parcours. |
| Responsable de déploiement | Ajoute ou met à jour un environnement, exécute un pipeline et déploie du code dans l’environnement AEM ou teste les performances du code. | Une fois les autorisations accordées par l’administrateur ou administratrice système, les responsables de déploiement peuvent lancer leur propre parcours de gestion des déploiements. |

Ce guide d’intégration illustre l’ensemble du processus d’intégration en tant qu’administrateur système. Les rôles des utilisateurs, des développeurs et des responsables de déploiement AEM sont brièvement présentés comme des parties supplémentaires et facultatives du parcours.

>[!TIP]
>
>Si vous découvrez AEM as a Cloud Service mais que vous connaissez déjà AEM et que vous migrez depuis On-Premise ou Adobe Managed Services, consultez le [Parcours de migration d’AEM as a Cloud Service](/help/journey-migration/getting-started.md).

## Vue d’ensemble du parcours d’intégration {#overview}

Les articles suivants décrivent en détail les principaux concepts d’intégration et vous donnent des connaissances fondamentales sur AEM as a Cloud Service. Bien que vous puissiez accéder directement à une partie spécifique du parcours, de nombreux concepts sont présentés dans des articles précédents. Par conséquent, si le concept d’intégration est nouveau pour vous, nous vous recommandons de commencer par le début et de continuer de manière chronologique.

| | Article | Description | Audience |
| --- | --- | --- | --- |
| 0 | Parcours d’intégration | Ce document | Administrateur et administratrice système |
| 1 | [Préparation à l’intégration](preparation.md) | Avant que le processus d’intégration ne commence, l’administrateur système doit comprendre un certain nombre d’étapes préparatoires avant de se connecter au système. | Administrateur et administratrice système |
| 2 | [Terminologie d’AEM as a Cloud Service](terminology.md) | Avant de vous connecter pour la première fois à AEMaaCS, il est utile de comprendre une partie de la terminologie du système et sa structure de base. | Administrateur et administratrice système |
| 3 | [Admin Console](admin-console.md) | Découvrez ce qu’est Admin Console, comment vous y connecter et comment vérifier votre profil en tant qu’administrateur système. | Administrateur et administratrice système |
| 4 | [Attribuer des profils de produits Cloud Manager](assign-profiles-cloud-manager.md) | Passez en revue les profils de produit Cloud Manager et apprenez à attribuer des membres de l’équipe aux profils de produit Cloud Manager. | Administrateur et administratrice système |
| 5 | [Accéder à Experience Hub](/help/experience-hub.md) | Utilisez Experience Hub qui sert de point d’entrée unifié et personnalisé pour l’écosystème AEM. | Utilisateurs et utilisatrices AEM |
| 6 | [Accéder à Cloud Manager](cloud-manager.md) | Découvrez comment accéder à Cloud Manager afin de pouvoir configurer les ressources de votre projet. | Administrateur et administratrice système |
| 7 | [Créer un programme](create-program.md) | Découvrez comment créer un programme à l’aide de Cloud Manager. | Administrateur et administratrice système |
| 8 | [Créer des environnements](create-environments.md) | Découvrez comment créer un environnement à l’aide de Cloud Manager. | Administrateur et administratrice système |
| 9 | [Attribuer des profils de produit AEM](assign-profiles-aem.md) | Découvrez comment l’administrateur ou l’administratrice système attribue les membres de votre équipe à des profils de produit dans AEM as a Cloud Service. | Administrateur et administratrice système |
| 10 | [Tâches du développeur ou de la développeuse et du responsable ou de la responsable de déploiement](developers.md) | Facultatif : découvrez comment accéder au Git Cloud Manager et le gérer en tant que développeur ou développeuse. En tant que responsable de déploiement, découvrez comment configurer des pipelines et déployer votre code dans Cloud Manager. | Développeurs ou développeuses et responsables de déploiement |
| 11 | [Tâches utilisateur d’AEM](aem-users.md) | Facultatif - Découvrez comment, en tant qu’auteur ou autrice AEM, vous pouvez accéder à l’instance AEM as a Cloud Service et vous familiariser avec la création de contenu pour AEM as a Cloud Service. | Utilisateurs et utilisatrices AEM |

## Prochaines étapes {#what-is-next}

Vous êtes maintenant en mesure de démarrer votre parcours d’intégration AEM as a Cloud Service. Nous vous encourageons à passer à la partie suivante du parcours et à lire l’article [Préparation à l’intégration](preparation.md)

## Parcours de documentation AEM {#documentation-journeys}

[Un parcours de documentation](/help/journey-documentation/documentation-journeys.md) associe de nombreux sujets et fonctionnalités différents et complexes. Il fournit un récit qui aide un lecteur ou une lectrice découvrant AEM à comprendre et résoudre un problème d’entreprise du début à la fin, tout en supposant un minimum de sujets antérieurs ou de connaissances AEM.

Les parcours de documentation sont conçus autour des principes des bonnes pratiques. Ils sont élaborés à partir des recherches les plus récentes d’Adobe, de l’expertise avérée des consultantes et consultants Adobe en matière de mise en œuvre, et des retours d’expérience des projets clients.

Si vous souhaitez savoir comment Adobe recommande d’intégrer votre équipe à une nouvelle application AEM as a Cloud Service, voici par où commencer.

## Ressources supplémentaires {#additional-resources}

Vous trouverez ci-dessous des ressources facultatives supplémentaires si vous souhaitez aller au delà du contenu du parcours d’intégration.

* [Intégration dans AEM as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/migration/moving-to-aem-as-a-cloud-service/onboarding) : cette courte vidéo propose une vue d’ensemble du processus d’intégration du service cloud pour AEM.
