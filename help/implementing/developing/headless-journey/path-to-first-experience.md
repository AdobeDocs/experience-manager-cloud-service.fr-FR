---
title: Chemin vers votre première expérience à l’aide de AEM sans en-tête
description: Dans cette partie du Parcours de développement AEM sans tête, vous comprendrez les étapes de la mise en oeuvre de votre première expérience sans tête en AEM, y compris les considérations de planification et vous apprendrez également les meilleures pratiques pour rendre votre chemin aussi fluide que possible.
hide: true
hidefromtoc: true
index: false
translation-type: tm+mt
source-git-commit: 3fd695cbe77873fa57373d91249b71d8c4be8a08
workflow-type: tm+mt
source-wordcount: '1899'
ht-degree: 0%

---


# Chemin vers votre première expérience à l’aide de AEM sans en-tête {#path-to-first-experience}

>[!CAUTION]
>
>TRAVAUX EN COURS - La création de ce document est en cours et ne doit pas être comprise comme complète ou définitive ni être utilisée à des fins de production.

Dans cette partie du [AEM Parcours de développement sans tête,](#overview.md) vous comprendrez les étapes de mise en oeuvre de votre première expérience sans tête en AEM, y compris les considérations de planification, et vous apprendrez également les meilleures pratiques pour rendre votre chemin aussi fluide que possible.

## L&#39;histoire jusqu&#39;à présent {#story-so-far}

Dans le document précédent de l&#39;parcours AEM sans tête, [Pour commencer avec AEM sans tête en tant que Cloud Service](getting-started.md) vous avez appris la théorie de base de ce qu&#39;est un CMS sans tête et vous devez maintenant :

* Comprenez les principes de base des AEM fonctionnalités sans tête.
* Connaissez les conditions préalables à l&#39;utilisation de AEM fonctions sans tête.
* Gardez à l’esprit AEM niveaux d’intégration sans tête.
* Être capable de définir votre projet en termes de portée.

Cet article s&#39;appuie sur ces principes de base pour vous permettre de comprendre comment préparer votre propre projet AEM sans tête.

## Intention {#objective}

Ce document vous aide à comprendre les étapes nécessaires à la mise en oeuvre de votre premier projet. Après l&#39;avoir lu, vous devez :

* Découvrez les points importants de la planification pour concevoir votre contenu.
* Comprenez les étapes à suivre pour implémenter sans tête en AEM.
* connaître les outils et les configurations AEM nécessaires.
* Découvrez les meilleures pratiques pour simplifier votre parcours sans tête, optimiser la génération de contenu et garantir la diffusion rapide du contenu.

## Conditions préalables {#requirements}

Avant de poursuivre avec ce document, vérifiez que vous avez passé en revue le document précédent dans le Parcours de développement AEM sans affichage, [Prise en main de AEM sans affichage en tant que Cloud Service](getting-started.md) en vous assurant que vous :

* Répondez aux exigences répertoriées.
* Vous avez pris en compte votre propre définition de projet, y compris la portée, les rôles et les performances.

## Planification du succès {#planning-for-success}

Pour début de votre premier projet AEM sans tête, vous devez vous assurer que vous disposez d’un modèle de contenu qui prend en charge la personnalisation et les mises à jour que vous souhaitez effectuer sur tous vos canaux.

Vous souhaitez également vous assurer que vous disposez d’un environnement de développement approprié si vous créez une application côté client afin de pouvoir tester votre client par rapport aux appels d’API à AEM en tant que Cloud Service.

### Définition de modèles de contenu et d&#39;API {#defining-models}

Vous souhaitez générer une expérience cohérente et gérer des campagnes personnalisées d’un canal à l’autre, afin que vous puissiez considérer chaque canal et surface comme sa propre structure de contenu à diffuser. Toutefois, il sera difficile de maintenir chaque canal à son propre modèle de contenu.

Il est préférable d’examiner la manière dont le contenu sur différentes surfaces est lié en fonction de principes d’organisation tels que les hiérarchies de marques et de produits, les catégories de marchandises ou de surfaces ou les étapes du parcours client. Par exemple, si vous disposez d&#39;un ensemble de surfaces qui prennent en charge une marque spécifique de voitures que vous fabriquez, vous pouvez début avec un modèle de contenu pour des informations générales qui seraient vraies pour la voiture entière, puis avoir des éléments plus contextuels spécifiques comme le contenu nécessaire au démarrage de la voiture lorsqu&#39;il y a des problèmes de service. Un tel modèle fera respecter l&#39;héritage du contenu général de la marque automobile tout en permettant des changements en fonction du contexte spécifique nécessaire. Il permet également de gérer les mises à jour de ce contenu à l’avenir, car vous pouvez imposer un contrôle en fonction de rôles tels que le spécialiste du marketing ou le responsable de produit global pour l’ensemble de la marque de voiture, par rapport à un auteur responsable de l’expérience de &quot;démarrage de voiture&quot;.

Une fois que vous disposez du modèle de contenu et que vous avez une vue claire sur les différents clients auxquels le contenu doit être affiché, vous devez vous assurer que les API GraphQL/API associées à l&#39;accès à divers modèles de contenu sont publiées à tous les clients qui ont besoin de ce contenu. Il existe différentes options pour accéder à certains contenus. Vous pouvez demander un élément de contenu statique spécifique qui permet la mise en cache du contenu et des performances supérieures. Vous pouvez également demander du contenu généré de manière dynamique et qui nécessitera davantage de traitement. Assurez-vous que les clients tirent parti des API les plus efficaces pour répondre à leurs besoins professionnels.

## Présentation de vos Environnements {#understanding-environments}

Il existe trois types d&#39;environnements dans AEM : développement, évaluation et production.

Les environnements de développement (vous pouvez en avoir plusieurs) sont un endroit sûr pour expérimenter et essayer des idées. Au cours de la phase initiale du projet, l&#39;Adobe recommande d&#39;utiliser les environnements de développement pour essayer des variantes des modèles de contenu et voir lesquels fournissent la sortie prévue pour les surfaces.

L’environnement d’évaluation pour les projets sans en-tête est utilisé pour valider les nouvelles versions AEM des produits avant leur déploiement en production. Conservez une liste à jour des modèles de contenu de production et un sous-ensemble du contenu. Vous pouvez ainsi obtenir des fichiers JSON générés pour comparer les éléments qui fournissent toujours la même sortie lorsque vous effectuez des modifications ou que la version AEM introduit des modifications.

La production est l’endroit où les auteurs de contenu créent et gèrent leur contenu réel. Les changements de modèle dans la production doivent être effectués avec soin et en gardant à l&#39;esprit la compatibilité ascendante.

Au cours de l’étape de développement, il est recommandé de travailler avec un environnement de développement et d’évaluation. Au fur et à mesure que vous passez aux tests de performances, vous voudrez passer à l’environnement de production.

### Coopération des développeurs et des auteurs de contenu {#cooperation}

Les développeurs ont besoin d’un environnement de développement AEM configuré avec les modèles de contenu renseignés. Le développeur développe le client qui consommera du contenu AEM sans en-tête alors que les auteurs du contenu continuent à créer le contenu. C&#39;est pourquoi les définitions d&#39;API sont très importantes. En exploitant le SDK AEM, le développeur peut créer un hook de test afin de pouvoir créer des tests client et unité pour s’assurer que le client est en mesure de générer correctement le contenu.

Les auteurs de contenu créent du contenu en fonction des modèles de contenu définis sur l’environnement d’évaluation. A l’aide de l’outil de création de fragments de contenu, l’auteur crée un fragment de contenu ou modifie un fragment de contenu existant. Avant de le publier, l’auteur peut prévisualisation l’aspect qu’il aura dans le client en collaborant avec le développeur pour pousser le modèle de contenu sur le développement ou en configurant un environnement de développeur uniquement pour les auteurs afin de prévisualisation de son aspect dans le client.

## Configuration {#setup}

Avant de commencer à utiliser AEM sans en-tête, vous devez vous assurer que toutes les fonctionnalités requises sont activées. Cette section décrit les exigences. Les étapes réelles permettant de réaliser ces étapes sont détaillées plus loin dans le [Parcours de développement AEM sans en-tête.](#overview.md)

Vous pouvez également consulter les [ressources supplémentaires](#additional-resources) pour plus d&#39;informations sur les différentes rubriques.

### Configuration {#configuration}

1. Activer les fragments de contenu
1. Activer GraphQL
1. Configuration du SDK sans en-tête

## Mise en oeuvre de votre première application AEM sans affichage

Il s’agit d’un aperçu de ce qui est nécessaire pour mettre en oeuvre votre première application sans tête à l’aide d’AEM pour diffuser votre contenu. La manière d’effectuer ces étapes sera décrite en détail dans les parties ultérieures du Parcours de développement sans affichage.

1. Création de modèles de fragments de contenu
1. Création de fragments de contenu
1. Requête de contenu avec GraphQL

## Bonnes pratiques {#best-practices}

Un projet sans but lucratif est non seulement un succès grâce à la technologie mise en oeuvre, mais aussi grâce à une bonne planification et à une bonne gouvernance du projet. Vous trouverez ci-dessous un certain nombre de bonnes pratiques que les auteurs et les développeurs doivent garder à l’esprit lorsque vous planifiez votre projet.

### Organisation de votre contenu {#organizing-content}

* Rendre votre structure aussi complexe que nécessaire mais la garder aussi simple que possible. Des structures de contenu plus simples permettent de rationaliser la gestion du contenu et d&#39;améliorer les performances du système.
* Attribuez la priorité à la réutilisation du contenu dans votre stratégie. Créez des sous-modèles et des références de contenu qui peuvent être réutilisés sur plusieurs modèles et canaux de niveau supérieur.
* Rendre les structures de contenu aussi explicites que possible afin que les auteurs puissent apprendre et s’adapter rapidement aux tâches de création.
* Si vous avez des restrictions d’accès, essayez d’aligner votre modèle de contenu avec les exigences d’accès.
* Lorsque vous avez des besoins en matière d’accès, ils doivent diriger la hiérarchie du contenu. Regroupez le contenu qui est modifié par le même groupe de personnes.
* Regroupez du contenu similaire dans un dossier.
   * Il est plus probable qu’un auteur de contenu copiera et collera du contenu sortant pour créer un nouveau contenu. Par conséquent, le fait de faire cela dans le même dossier le rend plus efficace.
   * AEM permet de définir des modèles autorisés par dossier, de sorte que le bouton **Créer** n&#39;affiche que les modèles pris en charge à cet emplacement.
* La création de nouveaux fragments de contenu dans l’éditeur de fragments de contenu en ligne peut être simplifiée si le dossier racine est défini dans le modèle. Ensuite, le praticien n&#39;a pas à choisir un emplacement, mais doit juste fournir un nom et peut début modifier la nouvelle référence.

### Création de contenu {#authoring}

* Pour les versions spécifiques à un canal de votre contenu, pensez à utiliser des variantes de fragments de contenu. Les variations sont synchronisées avec le contenu maître afin de rationaliser la gestion des modifications de contenu.
* Invitez d’autres producteurs de contenu à revoir le contenu et à fournir des commentaires avec annotations et commentaires, disponibles dans l’éditeur de fragments de contenu et globalement dans les fragments de contenu dans la console d’administration des fragments de contenu.
* Maintenez les choses en mouvement avec le moins d&#39;éléments obligatoires possible. Les éléments obligatoires peuvent bloquer le processus.

### Création de contenu global {#localization}

* Établir des règles et une gouvernance pour la traduction de contenu. Pour réduire la charge du système, établissez la traduction comme un processus asynchrone qui peut être exécuté à des intervalles plus longs. Prévoyez du temps pour le contrôle de la qualité des localisations et la correction de bogues.
* Tirez parti de toutes les fonctionnalités fournies par votre système de technologie de traduction que vous pouvez intégrer à des AEM telles que la mémoire de traduction.
* Déterminer si le contenu multimédia enrichi, tel que les images et les vidéos, a besoin d’être localisation.

## Eléments suivants {#what-is-next}

Maintenant que vous avez terminé cette partie du Parcours de développement AEM sans tête, vous devez :

* Découvrez les points importants de la planification pour concevoir votre contenu.
* Comprenez les étapes à suivre pour implémenter sans tête en AEM.
* connaître les outils et les configurations AEM nécessaires.
* Découvrez les meilleures pratiques pour simplifier votre parcours sans tête, optimiser la génération de contenu et garantir la diffusion rapide du contenu.

Vous devez poursuivre votre parcours sans tête AEM en examinant ensuite le document [Comment modéliser votre contenu en tant que AEM Content Models](model-your-content.md) où vous apprendrez à modéliser votre structure de contenu en AEM.

## Ressources supplémentaires {#additional-resources}

Bien qu&#39;il soit recommandé de passer à la partie suivante du parcours de développement sans tête en examinant le document [Comment modéliser votre contenu en tant que modèles de contenu AEM,](model-your-content.md), voici quelques ressources supplémentaires facultatives qui approfondissent certains concepts mentionnés dans ce document, mais qui ne sont pas nécessaires pour continuer sur le parcours sans tête.

* [Un développement sans tête pour AEM Sites en tant que Cloud Service](/help/implementing/developing/headless/introduction.md)  - Une introduction rapide pour orienter AEM développeur sans tête avec les fonctionnalités nécessaires
* [AEM Tutorials](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=fr)  sans en-tête - Utilisez ces didacticiels pratiques pour découvrir comment utiliser les différentes options de diffusion de contenu vers des points de terminaison sans en-tête avec AEM et choisissez ce qui vous convient.
* [Gestion de contenu sans en-tête utilisant les API](https://experienceleague.adobe.com/?Solution=Experience+Manager&amp;Solution=Experience+Manager+Sites&amp;Solution=Experience+Manager+Forms&amp;Solution=Experience+Manager+Screens&amp;launch=ExperienceManager-D-1-2020.1.headless#courses)  GraphQL - Suivez ce cours pour une présentation de l&#39;API GraphQL implémentée dans AEM. L’authentification via AdobeID est requise.
* [AEM Guides WKND - GraphQL](https://github.com/adobe/aem-guides-wknd-graphql)  - Ce projet GitHub comprend des exemples d&#39;applications qui mettent en évidence les API AEM GraphQL.
* [Introduction à l&#39;architecture de Adobe Experience Manager en tant que Cloud Service](/help/core-concepts/architecture.md)  - Un aperçu complet de l&#39;architecture AEM
* [Guide](/help/implementing/developing/headless/introduction.md#getting-started)  de prise en main sans en-tête - Une introduction rapide à AEM fonctions sans en-tête pour les utilisateurs déjà familiarisés avec l&#39;AEM.
* [Création de modèles](/help/assets/content-fragments/content-fragments-models.md)  de fragments de contenu - Documentation technique sur les modèles de fragments de contenu
* [Création de fragments](/help/assets/content-fragments/content-fragments.md)  de contenu - Documentation technique sur les fragments de contenu
* [Contenu de la requête avec GraphQL](/help/assets/content-fragments/graphql-api-content-fragments.md)  - Documentation technique sur l’API GraphQL
