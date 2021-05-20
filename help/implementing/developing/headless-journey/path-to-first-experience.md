---
title: Chemin d’accès à votre première expérience à l’aide d’AEM sans affichage
description: Dans cette partie du Parcours de développement AEM sans interface utilisateur, vous comprendrez les étapes de mise en oeuvre de votre première expérience sans interface dans AEM, y compris des considérations de planification et découvrirez également les bonnes pratiques pour rendre votre chemin aussi fluide que possible.
hide: true
hidefromtoc: true
index: false
exl-id: 257fc173-6bfb-4b60-b66c-6d6bdd5cf13f
source-git-commit: 9e06419f25800199dea92b161bc393e6e9670697
workflow-type: tm+mt
source-wordcount: '2005'
ht-degree: 0%

---

# Chemin d’accès à votre première expérience à l’aide AEM sans affichage {#path-to-first-experience}

>[!CAUTION]
>
>OUTDATED - Ce contenu de brouillon a été remplacé par la nouvelle [documentation du Parcours développeur sans affichage.](/help/journey-headless/developer/overview.md)

Dans cette partie du [Parcours de développement AEM sans interface utilisateur,](overview.md) vous comprendrez les étapes de mise en oeuvre de votre première expérience sans interface dans AEM, notamment des considérations de planification et vous apprendrez également les bonnes pratiques pour rendre votre chemin aussi fluide que possible.

## L&#39;histoire jusqu&#39;à présent {#story-so-far}

Dans le document précédent du parcours sans tête d’AEM, [Prise en main d’AEM sans tête en tant que Cloud Service](getting-started.md) vous avez appris la théorie de base de ce qu’est un CMS sans tête et vous devez maintenant :

* Comprendre les principes de base des fonctionnalités AEM sans interface.
* Découvrez les conditions préalables requises pour utiliser AEM fonctionnalités sans interface.
* Ayez conscience des niveaux d’intégration AEM sans interface.
* Soyez en mesure de définir votre projet en termes de portée.

Cet article s’appuie sur ces principes de base pour que vous compreniez comment préparer votre propre projet AEM sans tête.

## Intention {#objective}

Ce document vous aide à comprendre les étapes nécessaires à la mise en oeuvre de votre premier projet. Après l’avoir lu, vous devez :

* Comprenez les points importants de la planification pour concevoir votre contenu.
* Découvrez les étapes à suivre pour implémenter sans tête dans AEM.
* Découvrez les outils et les configurations d’AEM nécessaires.
* Découvrez les bonnes pratiques pour fluidifier votre parcours sans interface, optimiser la génération du contenu et garantir une diffusion rapide du contenu.

## Conditions requises {#requirements}

Avant de poursuivre avec ce document, assurez-vous d’avoir consulté le document précédent dans le Parcours de développement AEM sans affichage, [Prise en main d’AEM sans affichage en tant que Cloud Service](getting-started.md) en vous assurant que vous :

* Renseignez les conditions requises répertoriées.
* Ont pris en compte votre propre définition de projet, y compris la portée, les rôles et les performances.

## Planification de la réussite {#planning-for-success}

Pour démarrer votre premier projet AEM sans interface utilisateur, vous devez vous assurer que vous disposez d’un modèle de contenu qui prendra en charge la personnalisation et les mises à jour que vous souhaitez effectuer sur tous vos canaux.

En dehors d’AEM, vous souhaitez également vous assurer que vous disposez d’un environnement de développement correct configuré si vous créez une application côté client afin que vous puissiez tester votre client par rapport aux appels d’API à AEM en tant que Cloud Service.

### Définition des modèles de contenu et des API {#defining-models}

Vous souhaitez générer une expérience cohérente et gérer des campagnes personnalisées sur plusieurs canaux, afin que vous puissiez considérer chaque canal et surface comme sa propre structure de contenu à diffuser. Toutefois, la gestion de chaque canal avec son propre modèle de contenu sera difficile.

Vous devez plutôt examiner la manière dont le contenu sur différentes surfaces est associé en fonction de principes d’organisation tels que les hiérarchies de marques et de produits, les catégories de produits ou de surfaces, ou les étapes du parcours client. Par exemple, si vous disposez d’un ensemble de surfaces qui prennent en charge une marque spécifique de voitures que vous fabriquez, vous pouvez commencer par un modèle de contenu pour des informations générales qui seraient vraies pour l’ensemble de la voiture, puis avoir des éléments plus spécifiques au contexte, comme le contenu nécessaire lorsque la voiture commence à lorsqu’il y a des problèmes de service. Un tel modèle applique un héritage du contenu général de la marque automobile tout en permettant des modifications en fonction du contexte spécifique nécessaire. Il permet également de gérer les futures mises à jour de ce contenu, car vous pouvez appliquer un contrôle en fonction de rôles tels que le responsable marketing global ou le chef de produit pour l’ensemble de la marque de voiture, par rapport à un auteur responsable de l’expérience &quot;de départ de voiture&quot;.

Une fois que vous disposez du modèle de contenu et d’une vue claire sur les différents clients auxquels le contenu doit être affiché, vous devez vous assurer que les API GraphQL/API associées à l’accès à divers modèles de contenu sont publiées pour tous les clients qui ont besoin de ce contenu. Il existe différentes options pour accéder à un certain contenu. Vous pouvez demander un élément de contenu statique spécifique qui permet la mise en cache du contenu et des performances supérieures. Vous pouvez également demander du contenu généré dynamiquement, ce qui nécessitera davantage de traitement. Assurez-vous que les clients utilisent les API les plus efficaces pour répondre aux besoins de leur entreprise.

## Présentation de vos environnements {#understanding-environments}

Dans AEM, il existe trois types d’environnements : développement, évaluation et production.

Les environnements de développement (vous pouvez en avoir plusieurs) sont un endroit sûr pour expérimenter et essayer des idées. Pendant la phase initiale du projet, Adobe recommande d’utiliser les environnements de développement pour essayer des variantes des modèles de contenu et voir lesquels fournissent la sortie prévue pour les surfaces.

L’environnement d’évaluation pour les projets sans interface utilisateur est utilisé pour valider les nouvelles versions AEM de produits avant leur déploiement en production. Conservez une liste à jour des modèles de contenu de production et un sous-ensemble du contenu afin que les fichiers JSON soient générés pour les comparer ; ils fournissent toujours la même sortie lorsque vous effectuez des modifications ou que la version d’AEM introduit des modifications.

La production est l’endroit où les auteurs de contenu créent et gèrent leur contenu réel. Les changements de modèle dans la production doivent être effectués avec soin et avec une compatibilité descendante à l’esprit.

Au cours de l’étape de développement, il est recommandé de travailler avec un environnement de développement et d’évaluation. Au fur et à mesure que vous passez aux tests de performance, vous souhaiterez passer à l’environnement de production.

### Coopération des développeurs et des auteurs de contenu {#cooperation}

Les développeurs ont besoin d’un environnement de développement AEM configuré avec les modèles de contenu renseignés. Le développeur développe le client qui consommera du contenu d’AEM sans interface car les auteurs du contenu continuent à créer le contenu. C’est pourquoi les définitions d’API sont très importantes. En utilisant le SDK d’AEM, le développeur peut créer un point d’extension de test afin de pouvoir créer des tests client et unitaires pour s’assurer que le client est en mesure d’effectuer correctement le rendu du contenu.

Les auteurs de contenu créent du contenu en fonction des modèles de contenu définis dans l’environnement d’évaluation. À l’aide de l’outil de création de fragments de contenu, l’auteur crée un fragment de contenu ou en modifie un existant. Avant de le publier, l’auteur peut prévisualiser l’aspect qu’il aura dans le client en travaillant avec le développeur pour pousser le modèle de contenu sur le développement ou configurer un environnement de développement uniquement pour que les auteurs puissent prévisualiser l’aspect qu’il aura dans le client.

## Configuration {#setup}

Avant de commencer à utiliser headless dans AEM, vous devez vous assurer que toutes les fonctionnalités requises sont activées. Cette section décrit les exigences. Les étapes réelles pour réaliser ces étapes sont détaillées plus loin dans le [Parcours de développement AEM sans affichage.](#overview.md)

Vous pouvez également vous reporter éventuellement aux [ressources supplémentaires](#additional-resources) pour plus d’informations sur les sujets individuels.

### Configuration {#configuration}

1. Activation des fragments de contenu
1. Activation de GraphQL
1. Configuration du SDK sans affichage

## Mise en oeuvre de votre première application AEM sans affichage

Il s’agit d’un aperçu de ce qui est nécessaire pour mettre en oeuvre votre première application sans tête à l’aide d’AEM pour diffuser votre contenu. La procédure à suivre pour effectuer ces étapes sera décrite en détail dans les parties ultérieures du Parcours de développement sans affichage.

1. Création de modèles de fragment de contenu
1. Création de fragments de contenu
1. Requête de contenu avec GraphQL

## Bonnes pratiques {#best-practices}

Un projet sans tête est non seulement un succès grâce à la technologie mise en oeuvre, mais aussi grâce à une bonne planification et à la bonne gouvernance du projet. Vous trouverez ci-dessous un certain nombre de bonnes pratiques que les auteurs et les développeurs de contenu doivent garder à l’esprit au fur et à mesure que vous planifiez votre projet.

### Organisation de votre contenu {#organizing-content}

* Rendez votre structure aussi complexe que nécessaire, mais restez aussi simple que possible. Des structures de contenu plus simples permettent de rationaliser la gouvernance du contenu et d’améliorer les performances du système.
* Définir la priorité de la réutilisation du contenu dans votre stratégie. Créez des sous-modèles et des références de contenu qui peuvent être réutilisés sur plusieurs canaux et modèles de niveau supérieur.
* Rendre les structures de contenu aussi explicites que possible afin que les auteurs de contenu puissent apprendre et s’adapter rapidement aux tâches de création.
* Si vous avez des restrictions d’accès, essayez d’aligner votre modèle de contenu avec les exigences d’accès.
* Lorsque vous avez des exigences d’accès, il doit diriger votre hiérarchie de contenu. Regroupez le contenu qui est édité par le même groupe de personnes.
* Regroupez du contenu similaire dans un dossier.
   * Il est plus probable qu’un auteur de contenu copiera et collera du contenu existant pour créer du contenu. Par conséquent, le fait de le faire dans le même dossier le rend plus efficace.
   * AEM permet de définir les modèles autorisés par dossier. De ce fait, le bouton **Créer** n’affiche que les modèles pris en charge à cet emplacement.
* La création de fragments de contenu en ligne par l’éditeur de fragments de contenu peut être simplifiée si le dossier racine est défini dans le modèle. Ensuite, le praticien n’a pas à choisir un emplacement, mais doit simplement fournir un nom et peut commencer à modifier la nouvelle référence.

### Création de contenu {#authoring}

* Pour les versions spécifiques à un canal de votre contenu, pensez à utiliser des variations de fragment de contenu. Les variations sont synchronisées avec le gabarit de contenu afin de rationaliser la gestion des changements de contenu.
* Invitez d’autres producteurs de contenu à passer en revue le contenu et à faire part de commentaires avec des annotations et des commentaires, disponibles dans l’éditeur de fragments de contenu et globalement dans les fragments de la console d’administration des fragments de contenu.
* Faites en sorte que les choses se déplacent avec le moins d’éléments obligatoires possible. Les éléments obligatoires peuvent bloquer le workflow.

### Création de contenu global {#localization}

* Définissez des règles et une gouvernance pour la traduction de contenu. Pour réduire la charge du système, définissez la traduction comme un processus asynchrone qui peut être exécuté à des intervalles plus longs. Laissez du temps pour le contrôle de la qualité de la localisation et la correction de bogues.
* Tirez parti de toutes les fonctionnalités de votre système de technologie de traduction que vous pouvez intégrer à AEM telles que la mémoire de traduction.
* Déterminez si le contenu multimédia, tel que les images et les vidéos, doit être localisé.

## Suite {#what-is-next}

Maintenant que vous avez terminé cette partie du Parcours de développement AEM sans affichage, vous devez :

* Comprenez les points importants de la planification pour concevoir votre contenu.
* Découvrez les étapes à suivre pour implémenter sans tête dans AEM.
* Découvrez les outils et les configurations d’AEM nécessaires.
* Découvrez les bonnes pratiques pour fluidifier votre parcours sans interface, optimiser la génération du contenu et garantir une diffusion rapide du contenu.

Nous voulons que vous puissiez tirer parti de ces connaissances fondamentales pour comprendre pleinement la puissance et la flexibilité d&#39;AEM sans tête afin que vous puissiez en profiter pour vos propres projets. Pour ce faire, vous disposez d’options.

### Choisissez votre propre aventure {#choose-your-path}

Quel que soit votre style d&#39;apprentissage, l&#39;Adobe veut que vous réussissiez à commencer votre projet AEM sans tête.

* Si vous préférez continuer à **découvrir les concepts sans interface et AEM les technologies sans interface**, vous devez continuer votre parcours sans interface en consultant le document [Comment modéliser votre contenu en tant que modèles de contenu ](model-your-content.md) où vous apprendrez à modéliser votre structure de contenu dans.
* Si vous préférez **apprendre en faisant**, vous pouvez passer au [didacticiel Prise en main d’AEM non-affichage](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html) où vous allez directement dans AEM développement sans affichage en mettant en oeuvre un projet simple pour exposer un contenu sans affichage.

## Ressources supplémentaires {#additional-resources}

Bien qu’il soit recommandé de passer à la partie suivante du parcours de développement sans interface utilisateur en consultant le document [Comment modéliser votre contenu en tant que modèles de contenu AEM,](model-your-content.md) les ressources facultatives suivantes approfondissent certains concepts mentionnés dans ce document, mais elles ne doivent pas continuer sur le parcours sans interface.

* [Développement sans affichage pour AEM Sites as a Cloud Service](/help/implementing/developing/headless/introduction.md)  - Cette présentation rapide pour orienter le développeur sans affichage AEM avec les fonctionnalités nécessaires.
* [AEM Tutorials sans affichage](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=fr)  : utilisez ces tutoriels pratiques pour découvrir comment utiliser les différentes options de diffusion de contenu vers des points de terminaison sans interface avec AEM et choisissez ce qui vous convient.
* [Gestion de contenu sans affichage à l’aide des API GraphQL](https://experienceleague.adobe.com/?Solution=Experience+Manager&amp;Solution=Experience+Manager+Sites&amp;Solution=Experience+Manager+Forms&amp;Solution=Experience+Manager+Screens&amp;launch=ExperienceManager-D-1-2020.1.headless#courses)  : suivez ce cours pour une présentation de l’API GraphQL implémentée dans AEM. L’authentification via Adobe ID est requise.
* [AEM Guides WKND - GraphQL](https://github.com/adobe/aem-guides-wknd-graphql)  - Ce projet GitHub comprend des exemples d’applications qui mettent en évidence AEM API GraphQL.
* [Présentation de l’architecture d’Adobe Experience Manager as a Cloud Service](/help/core-concepts/architecture.md)  - Aperçu complet de l’architecture AEM
* [Guide de prise en main sans tête](/help/implementing/developing/headless/introduction.md#getting-started)  : présentation rapide des fonctionnalités AEM sans tête pour les utilisateurs qui connaissent déjà AEM.
* [Créer des modèles de fragment de contenu](/help/assets/content-fragments/content-fragments-models.md)  - Documentation technique sur les modèles de fragment de contenu
* [Créer des fragments de contenu](/help/assets/content-fragments/content-fragments.md)  - Documentation technique sur les fragments de contenu
* [Contenu des requêtes avec GraphQL](/help/assets/content-fragments/graphql-api-content-fragments.md)  - Documentation technique sur l’API GraphQL
