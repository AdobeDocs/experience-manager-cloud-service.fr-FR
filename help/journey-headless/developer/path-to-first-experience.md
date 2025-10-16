---
title: Premiers pas vers votre première expérience d’utilisation d’AEM découplé
description: Dans cette partie du parcours de développement découplé AEM, vous découvrirez les étapes de mise en œuvre de votre première expérience découplée dans AEM, notamment des considérations concernant sa planification, et découvrirez également les bonnes pratiques pour rendre votre parcours aussi fluide que possible.
exl-id: 172ad8d8-5067-4452-bf91-1eea9a39a7bc
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Architect, Developer
source-git-commit: 2ccca86a0e611b93c273e37abb6e0fd7870421d4
workflow-type: tm+mt
source-wordcount: '1881'
ht-degree: 96%

---

# Premiers pas vers votre première expérience d’utilisation d’AEM découplé {#path-to-first-experience}

Dans cette partie du [Parcours de développement AEM Headless](overview.md), vous découvrirez les étapes de mise en œuvre de votre première expérience découplée dans AEM, notamment des considérations concernant sa planification, et découvrirez également les bonnes pratiques pour rendre votre parcours aussi fluide que possible.

## Un peu d’histoire... {#story-so-far}

Dans le document précédent traitant du parcours AEM découplé, intitulé [Prise en main d’AEM as a Cloud Service découplé](getting-started.md), vous avez appris la théorie sur ce qu’est un CMS découplé, et vous devriez maintenant :

* comprendre les principes de base des fonctionnalités d’AEM découplé ;
* connaître les conditions préalables requises pour utiliser les fonctionnalités AEM découplées ;
* avoir conscience des niveaux d’intégration AEM découplé ;
* être en mesure de définir votre projet et sa portée.

Cet article s’appuie sur ces principes de base pour que vous compreniez comment préparer votre propre projet AEM découplé.

## Objectif {#objective}

Ce document vous aide à comprendre les étapes nécessaires à la mise en œuvre de votre premier projet. Après l’avoir lu, vous devriez :

* comprendre les points importants de sa planification pour concevoir votre contenu ;
* découvrir les étapes à suivre pour implémenter du contenu découplé dans AEM ;
* découvrir les outils et les configurations AEM nécessaires ;
* connaître les bonnes pratiques vous permettant de fluidifier votre parcours découplé, d’optimiser la génération du contenu et de garantir une diffusion rapide du contenu.

## Conditions requises {#requirements}

Avant de poursuivre avec ce document, assurez-vous d’avoir consulté le document précédent dans le parcours de développement découplé AEM, [Prise en main d’AEM as a Cloud Service découplé](getting-started.md), en vous assurant que vous :

* remplissez les conditions requises répertoriées ;
* avez pris en compte votre propre définition de projet, y compris sa portée, les rôles en jeu et les performances attendues.

## Planifier pour réussir {#planning-for-success}

Pour lancer votre premier projet découplé AEM, vous devez vous assurer que vous disposez d’un modèle de contenu qui prendra en charge la personnalisation et les mises à jour que vous souhaitez effectuer sur tous vos canaux.

En dehors d’AEM, nous vous recommandons également de vous assurer que vous disposez d’un environnement de développement correctement configuré si vous créez une application côté client afin de pouvoir tester votre client par rapport aux appels des API à AEM as a Cloud Service.

### Définition des modèles de contenu et des API {#defining-models}

Votre objectif est de générer une expérience cohérente et de gérer des campagnes personnalisées sur plusieurs canaux, afin de pouvoir considérer chaque canal et chaque surface comme sa propre structure de contenu à diffuser. Toutefois, il est difficile de gérer chaque canal doté de son propre modèle de contenu.

Il vous faut plutôt examiner la manière dont les contenus des différentes surfaces sont associés les uns aux autres en fonction de principes d’organisation tels que les hiérarchies de marques et de produits, les catégories de produits ou de surfaces, ou les étapes du parcours client. Par exemple, si vous disposez d’un ensemble de surfaces qui prennent en charge une marque spécifique de voitures que vous fabriquez, vous pouvez commencer par un modèle de contenu pour des informations générales qui seraient vraies pour l’ensemble de la voiture, puis avoir des éléments plus spécifiques, comme le contenu nécessaire pour le démarrage de la voiture, ou lorsqu’il y a des problèmes de service. Un tel modèle va appliquer un héritage pour le contenu général de la marque automobile tout en permettant des modifications en fonction du contexte spécifique nécessaire. Il permet également de gérer les futures mises à jour de ce contenu, car vous pouvez appliquer un contrôle en fonction de rôles tels que celui de responsable marketing global ou de chef de produit pour l’ensemble de la marque de voiture, par rapport à un auteur responsable de l’expérience « démarrage de la voiture ».

Une fois que vous disposez du modèle de contenu et d’une vue claire sur les différents clients pour lesquels le contenu doit être affiché, vous devez vous assurer que les API GraphQL/API associées à l’accès à divers modèles de contenu sont publiées pour tous les clients qui ont besoin de ce contenu. Il existe différentes options pour accéder à un contenu particulier. Vous pouvez demander un élément de contenu statique spécifique qui permet la mise en cache du contenu et des performances supérieures. Vous pouvez également demander de générer dynamiquement du contenu, ce qui nécessitera davantage de traitement. Assurez-vous que les clientes et les clients utilisent les API les plus efficaces pour répondre aux besoins de leur entreprise.

## Présentation de vos environnements {#understanding-environments}

Dans AEM, il existe trois types d’environnements : développement, évaluation et exploitation.

Les environnements de développement (vous pouvez en avoir plusieurs) sont un endroit sûr pour expérimenter et essayer de nouvelles idées. Pendant la phase initiale du projet, Adobe recommande d’utiliser les environnements de développement pour tester les variantes des modèles de contenu et voir lesquels fournissent le résultat prévu pour les surfaces.

L’environnement d’évaluation pour les projets découplés est utilisé pour valider les nouvelles versions de produits AEM avant leur déploiement en exploitation. Conservez la liste actualisée des modèles de contenu d’exploitation et un sous-ensemble du contenu afin de générer des fichiers JSON à des fins de comparaison ; ces derniers fournissent toujours le même résultat lorsque vous effectuez des modifications ou lorsque la mise à jour AEM introduit des modifications.

L’environnement d’exploitation est l’endroit où les auteurs de contenu créent et gèrent leur contenu réel. Les changements de modèle dans l’exploitation doivent être effectués avec soin et en gardant à l’esprit une compatibilité descendante.

Au cours de l’étape de développement, il est recommandé de travailler avec un environnement de développement et d’évaluation. Au fur et à mesure que vous passez aux tests de performance, il est recommandé de passer à l’environnement de production.

### Coopération entre équipe de développement et auteurs de contenu {#cooperation}

L’équipe de développement a besoin d’un environnement de développement AEM configuré avec les modèles de contenu renseignés. Le développeur développe le client qui consommera du contenu découplé AEM, car les auteurs du contenu continuent à créer du contenu. C’est pourquoi les définitions d’API sont très importantes. Grâce au SDK AEM, le développeur ou la développeuse peut créer un hook de test afin d’effectuer des tests client et unitaires et de s’assurer que le client ou la cliente est en mesure d’effectuer correctement le rendu du contenu.

Les auteurs et autrices de contenu créent du contenu en fonction des modèles de contenu définis dans l’environnement d’évaluation. À l’aide de l’outil de création de fragments de contenu, l’auteur ou l’autrice crée un fragment de contenu ou modifie un fragment existant. Avant de le publier, l’auteur peut prévisualiser l’aspect qu’il aura dans le client en travaillant avec le développeur pour pousser le modèle de contenu en développement ou configurer un environnement de développement uniquement pour que les auteurs puissent prévisualiser l’aspect que le fragment de contenu aura dans le client.

## Configuration {#setup}

Avant de commencer à utiliser du contenu découplé dans AEM, vous devez vous assurer que toutes les fonctionnalités requises sont activées. Cette section décrit ces différentes exigences. Les étapes réelles pour réaliser ces étapes sont détaillées plus loin dans le [Parcours de développement AEM Headless](#overview.md).

Vous pouvez également consulter les [ressources supplémentaires](#additional-resources) pour plus d’informations sur chaque sujet.

### Configuration {#configuration}

1. Activation des fragments de contenu
1. Activation de GraphQL
1. Configuration du SDK découplé

## Mise en œuvre de votre première application découplée AEM

Voici un aperçu de ce qui est nécessaire pour mettre en œuvre votre première application découplée pour diffuser votre contenu à l’aide d’AEM. La procédure à suivre pour effectuer ces étapes est décrite en détail dans les parties suivantes du parcours de développement découplé.

1. Créer des modèles de fragment de contenu
1. Créer des fragments de contenu
1. Demander du contenu avec GraphQL

## Bonnes pratiques {#best-practices}

Un projet découplé doit son succès non seulement à la technologie mise en œuvre, mais aussi à sa bonne planification et à sa bonne gouvernance. Vous trouverez ci-dessous des bonnes pratiques que les auteurs et les autrices ainsi que les développeurs et les développeuses de contenu doivent garder à l’esprit tout au long de la planification du projet.

### Organisation de votre contenu {#organizing-content}

* Concevez votre structure de manière aussi complexe que nécessaire, mais restez au plus simple. Des structures de contenu plus simples permettent de rationaliser la gouvernance et d’améliorer les performances du système.
* La réutilisation du contenu doit être une priorité dans votre stratégie. Créez des sous-modèles et des références de contenu qui peuvent être réutilisés sur plusieurs canaux et sur des modèles de niveau supérieur.
* Concevez les structures de contenu de façon aussi explicite que possible afin que les auteurs de contenu puissent apprendre et s’adapter rapidement aux tâches de création.
* En cas de restrictions d’accès, essayez d’aligner votre modèle de contenu avec ces exigences.
* Votre hiérarchie de contenu doit se calquer sur ces exigences d’accès. Regroupez les contenus édités par le même groupe de personnes.
* Regroupez les contenus similaires dans un dossier.
   * Un auteur de contenu utilisera probablement un contenu existant pour le copier et le coller et créer du contenu. C’est pourquoi il sera plus efficace de le faire dans le même dossier.
   * AEM permet de définir des modèles autorisés par dossier afin que le bouton **Créer** n’affiche que les modèles pris en charge à cet emplacement.
* La création de fragments de contenu en ligne par l’éditeur de fragments de contenu peut être simplifiée si le dossier racine est défini dans le modèle. Le professionnel ou la professionnelle n’a alors pas à choisir un emplacement, mais doit simplement fournir un nom et peut commencer à modifier la nouvelle référence.

### Création de contenu {#authoring}

* Pour les versions spécifiques à un canal de votre contenu, pensez à utiliser des variations de fragment de contenu. Les variations sont synchronisées avec le gabarit de contenu afin de rationaliser la gestion des changements de contenu.
* Invitez d’autres producteurs de contenu à passer en revue le contenu et à faire part de leurs commentaires.
* Créez un système efficace qui nécessite le moins d’éléments obligatoires possible. Des éléments obligatoires peuvent bloquer le workflow.

### Création de contenu global {#localization}

* Définissez des règles et une gouvernance pour la traduction de contenu. Pour réduire la charge du système, définissez la traduction comme un processus asynchrone qui peut être exécuté à des intervalles plus longs. Accordez le temps nécessaire au contrôle de la qualité de la localisation et à la correction des bogues.
* Tirez parti de toutes les fonctionnalités de votre système de technologie de traduction que vous pouvez intégrer à AEM, parmi lesquelles la mémoire de traduction.
* Déterminez si le contenu multimédia, tel que les images et les vidéos, doit être localisé.

## Prochaines étapes {#what-is-next}

Maintenant que vous avez terminé cette partie du parcours de développement découplé AEM, vous devriez pouvoir :

* comprendre les points importants de sa planification pour concevoir votre contenu ;
* découvrir les étapes à suivre pour implémenter du contenu découplé dans AEM ;
* découvrir les outils et les configurations AEM nécessaires ;
* connaître les bonnes pratiques vous permettant de fluidifier votre parcours découplé, d’optimiser la génération du contenu et de garantir une diffusion rapide du contenu.

Nous voulons que vous puissiez tirer parti de ces connaissances fondamentales pour comprendre pleinement la puissance et la flexibilité d’AEM découplé afin que vous puissiez en tirer parti pour vos propres projets.

Pour ce faire, continuez votre parcours découplé AEM avec [Comment modéliser votre contenu en tant que modèles de contenu AEM](/help/journey-headless/developer/model-your-content.md) où vous apprendrez à modéliser votre structure de contenu dans AEM.

## Ressources supplémentaires {#additional-resources}

Bien qu’il soit recommandé de passer à la partie suivante du parcours de développement découplé en consultant le document [Comment modéliser votre contenu en tant que modèles de contenu AEM](model-your-content.md), les documents facultatifs suivants approfondissent certains concepts mentionnés dans ce document, mais ils ne sont pas obligatoires pour poursuivre le parcours découplé.

Si vous préférez **apprendre en pratiquant**, vous pouvez passer au [tutoriel de prise en main d’AEM découplé](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html?lang=fr). Vous pourrez ainsi accéder directement au développement avec AEM découplé en mettant en œuvre un projet simple pour exposer un contenu découplé.

Autres ressources :

* [Parcours de traduction découplée AEM](/help/journey-headless/translation/overview.md) : ce parcours d’information vous aide à comprendre les principes de la technologie découplée, la manière dont AEM diffuse du contenu découplé et de la manière dont vous pouvez le traduire.
* [Développement découplé pour AEM Sites as a Cloud Service](/help/headless/introduction.md) : une présentation rapide pour orienter le développeur AEM découplé vers les fonctionnalités qui lui seront utiles.
* [Portail de développement d’AEM &#x200B;](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=fr)
* [Gestion de contenu en mode découplé à l’aide des API GraphQL](https://experienceleague.adobe.com/fr?Solution=Experience+Manager&Solution=Experience+Manager+Sites&Solution=Experience+Manager+Forms&Solution=Experience+Manager+Screens&launch=ExperienceManager-D-1-2020.1.headless#courses) : suivez ce cours pour bénéficier d’un aperçu de l’API GraphQL implémentée dans AEM. L’authentification à l’aide de l’Adobe ID est requise.
* [Guides AEM WKND – GraphQL](https://github.com/adobe/aem-guides-wknd-graphql) : ce projet GitHub comprend des exemples d’applications qui mettent en évidence l’API AEM GraphQL.
* [Présentation de l’architecture d’Adobe Experience Manager as a Cloud Service](/help/overview/architecture.md) : un aperçu complet de l’architecture AEM.
* [Configuration découplée](/help/headless/introduction.md#getting-started) : une présentation rapide des fonctionnalités découplées AEM pour les utilisateurs qui connaissent déjà AEM.
* [Créer des modèles de fragment de contenu](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md) : documentation technique sur les modèles de fragment de contenu.
* [Créer des fragments de contenu](/help/sites-cloud/administering/content-fragments/managing.md#creating-content-fragments) : documentation technique sur les fragments de contenu.
* [Demander du contenu avec GraphQL](/help/headless/graphql-api/content-fragments.md) : documentation technique sur l’API GraphQL.
