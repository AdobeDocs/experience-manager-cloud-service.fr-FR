---
title: 'Facultatif : comment créer des applications monopages (SPA) avec Adobe Experience Manager (AEM)'
description: Dans cette suite facultative du parcours de développement découplé AEM, vous découvrirez comment AEM peut combiner une diffusion découplée avec des fonctionnalités CMS full stack traditionnelles et comment créer des SPA modifiables à l’aide du cadre de l’éditeur de SPA d’AEM.
exl-id: d74848f2-683e-49e1-9374-32596ca5d7d7
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1250'
ht-degree: 100%

---

# Comment créer des applications monopages avec AEM {#create-spa}

Dans cette suite facultative du [Parcours de développement découplé AEM](overview.md), vous découvrirez comment AEM peut combiner une diffusion découplée avec des fonctionnalités CMS full stack traditionnelles. Vous découvrirez également comment créer des SPA modifiables à l’aide du cadre de l’éditeur de SPA d’AEM et intégrer des SPA externes, en activant les fonctionnalités d’édition selon les besoins.

## Un peu d’histoire...  {#story-so-far}

À ce stade, vous devriez avoir terminé l’ensemble du [Parcours de développement découplé AEM](overview.md) et comprendre les principes de base de la diffusion découplée dans AEM, ainsi que les éléments suivants :

* La différence entre la diffusion de contenu couplé et découplé
* Les fonctionnalités découplées AEM
* Comment organiser un projet découplé AEM
* Comment créer du contenu découplé dans AEM
* Comment récupérer et mettre à jour du contenu découplé dans AEM
* La mise en ligne d’un projet découplé AEM

Jusqu’à présent, vous avez soit lancé votre premier projet découplé AEM, soit vous avez les connaissances pour le faire. Félicitations.

Alors pourquoi lire cette section supplémentaire et facultative du parcours ? Vous vous souvenez que dans la section [Prise en main](getting-started.md#integration-levels), nous avons expliqué comment AEM prend non seulement en charge la diffusion découplée et les modèles full stack traditionnels, mais peut également prendre en charge des modèles hybrides qui combinent les avantages des deux. Bien qu’il ne s’agisse pas de modèles découplés classiques, de tels modèles hybrides peuvent offrir une flexibilité sans précédent à certains projets.

Cet article s’appuie sur vos connaissances du découplage AEM en explorant en profondeur la manière dont vous pouvez créer vos propres applications monopages (SPA) qui sont modifiables dans Adobe. Vous pouvez ainsi créer du contenu et le diffuser intégralement vers une SPA, mais cette SPA reste modifiable dans AEM.

## Objectif {#objective}

Ce document vous aide à comprendre comment les applications monopages sont développées à l’aide du cadre de l’éditeur d’application monopage AEM. Après avoir lu ce document, vous devriez :

* comprendre la fonction de base de l’éditeur de SPA ;
* connaître les exigences relatives à la création d’une SPA entièrement modifiable pour AEM ;
* comprendre comment les SPA externes peuvent être intégrées à AEM ;
* comprendre comment le rendu côté serveur peut ou non être implémenté.

## Exigences et conditions préalables {#requirements-prerequisites}

Avant de commencer à travailler avec des SPA dans AEM, plusieurs conditions sont requises.

### Connaissances {#knowledge}

* Expérience de développement de création de SPA avec des frameworks React ou Angular
* Compétences AEM de base pour la création de fragments de contenu et l’utilisation de l’éditeur
* Veillez à consulter le document [Couplage et découplage dans AEM](/help/implementing/developing/headful-headless.md) afin de comprendre les différents niveaux d’intégration de SPA possibles.

### Outils {#tools}

* Accès aux sandbox pour tester le déploiement de votre projet
* Instance de développement locale pour la modélisation et le test des données
* SPA externe existante (facultatif, selon le modèle d’intégration choisi)
* Archétype de projet AEM

## Qu’est-ce qu’une SPA ? {#what-is-a-spa}

Une application monopage (SPA) diffère d’une page conventionnelle en cela qu’elle est rendue côté client et qu’elle est principalement pilotée par JavaScript, en utilisant les appels Ajax pour charger les données et mettre la page à jour dynamiquement. La plupart ou la totalité du contenu est récupérée une fois au chargement d’une seule page avec des ressources supplémentaires chargées de manière asynchrone, selon les besoins, en fonction de l’interaction de l’utilisateur ou de l’utilisatrice avec la page.

Cette fonctionnalité limite la nécessité d’actualiser la page et offre à l’utilisateur ou à l’utilisatrice une expérience harmonieuse, rapide et rappelant davantage l’expérience d’une application native.

L’éditeur de SPA d’AEM permet aux développeurs et aux développeuses front-end de créer des SPA qui peuvent être intégrées à un site AEM, ce qui permet aux créateurs et créatrices de contenu de modifier le contenu de SPA aussi facilement qu’un autre contenu AEM.

## Pourquoi une SPA ?  {#why-spa}

En étant plus rapide, plus fluide et plus proche d’une application native, une SPA devient une expérience attrayante. C’est une bonne chose non seulement pour le visiteur de personne qui visite la page web, mais aussi pour les personnes spécialisées dans le marketing et le développement en raison de la nature du fonctionnement des SPA.

Pour obtenir une description complète des SPA et des raisons de leur utilisation, reportez-vous à la section [Ressources supplémentaires](#additional-resources) pour obtenir des liens vers une documentation plus détaillée.

## Comment AEM gère les SPA

Le développement d’applications monopages sur AEM suppose que l’équipe de développement front-end respecte les bonnes pratiques standard lors de la création d’une application monopage. En tant que personne chargée du développement front-end, si vous suivez ces bonnes pratiques générales et quelques principes spécifiques à AEM, votre SPA devient fonctionnelle avec AEM et ses fonctionnalités de création de contenu.

* **Portabilité** : comme pour tout composant, les composants de SPA créés doivent être aussi portables que possible. La SPA doit être créée avec des composants portables et réutilisables.
* **AEM détermine la structure du site** : la personne chargée du développement front-end crée des composants et contrôle leur structure interne, mais elle dépend d’AEM pour définir la structure de contenu du site.
* **Rendu dynamique** : tout le rendu doit être dynamique.
* **Routage dynamique** : la SPA assure le routage, et AEM l’écoute et s’appuie dessus pour l’extraction. Tout routage devrait également être dynamique.

Pour une description complète de la façon dont AEM gère les SPA, consultez la section [Ressources supplémentaires](#additional-resources) pour obtenir des liens vers une documentation plus détaillée.

## Éditeur de SPA AEM {#aem-spa-editor}

Les sites créés à l’aide de structures SPA courantes, telles que React et Angular, chargent leur contenu au moyen d’un code JSON dynamique. Ils ne fournissent pas la structure de HTML nécessaire pour que l’éditeur de page d’AEM puisse placer des contrôles de modification.

Pour activer la modification d’applications monopages dans AEM, il faut qu’il y ait une correspondance entre la sortie JSON de l’application et le modèle de contenu dans le répertoire AEM afin d’enregistrer les modifications apportées au contenu.

La prise en charge des SPA dans AEM introduit une fine couche JavaScript qui interagit avec le code JavaScript de la SPA lorsqu’elle est chargée dans l’éditeur de page, qui permet l’envoi d’événements. L’emplacement des commandes d’édition peut être activé pour permettre la modification en contexte. Cette fonctionnalité repose sur le concept de point d’entrée de l’API Content Services, car le contenu de la SPA doit être chargé au moyen de Content Services.

Pour une description complète de la façon dont AEM gère l’éditeur de SPA, consultez la section [Ressources supplémentaires](#additional-resources) pour obtenir des liens vers une documentation plus détaillée.

## Hébergement des SPA existantes {#existing-spas}

Si vous disposez d’une SPA existante, AEM prend en charge son intégration afin qu’elle soit visible par les auteurs et les autrices de contenu dans l’éditeur AEM. Cette capacité peut s’avérer très utile pour afficher le contenu créé à l’aide de fragments de contenu dans le contexte de l’application finale où il sera utilisé.

En outre, avec seulement quelques petites modifications, vous pouvez activer certaines fonctionnalités d’édition pour les SPA externes dans l’éditeur AEM.

Le composant RemotePage permet le rendu d’une SPA externe dans AEM.

Pour une description complète de la manière de rendre les SPA externes modifiables dans AEM, consultez la section [Ressources supplémentaires](#additional-resources) pour obtenir des liens vers une documentation plus détaillée.

## Et après ? {#what-is-next}

Pour commencer à développer votre propre SPA pour AEM, consultez les documents suivants :

* [Tutoriel sur SPA WKND](/help/implementing/developing/hybrid/wknd-tutorial.md)
* [Prise en main avec React](/help/implementing/developing/hybrid/getting-started-react.md)
* [Prise en main avec Angular](/help/implementing/developing/hybrid/getting-started-angular.md)

Si vous devez adapter une SPA existante pour l’utiliser dans AEM, consultez les documents suivants :

* [Composant RemotePage](/help/implementing/developing/hybrid/remote-page.md)
* [Modification d’une SPA externe dans AEM](/help/implementing/developing/hybrid/editing-external-spa.md)

Consultez ci-dessous les [ressources supplémentaires](#additional-resources) qui peuvent vous aider à approfondir les sujets relatifs aux SPA dans AEM.

## Ressources supplémentaires {#additional-resources}

Vous trouverez ci-dessous quelques ressources supplémentaires qui approfondissent certains concepts mentionnés dans ce document.

* [Couplage et découplage dans AEM](/help/implementing/developing/headful-headless.md) : description des différents modèles de diffusion disponibles dans AEM
* [Introduction à la SPA et présentation](/help/implementing/developing/hybrid/introduction.md) - Une bonne introduction aux SPA dans AEM.
* [Développement de SPA pour AEM](/help/implementing/developing/hybrid/developing.md) : consignes sur la manière de développer des SPA pour AEM
* [Aperçu sur l’éditeur de SPA](/help/implementing/developing/hybrid/editor-overview.md) : informations détaillées sur le fonctionnement de l’éditeur de SPA
* [Documents de référence pour les SPA](/help/implementing/developing/hybrid/reference-materials.md) : références et liens de l’API JavaScript vers les projets GitHub de SPA AEM open source
* [Fragments de contenu](/help/sites-cloud/administering/content-fragments/managing.md#creating-content-fragments) : comment créer des fragments de contenu
* [Archétype de projet AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) : modèle Maven qui crée un projet Adobe Experience Manager (AEM) minimal qui s’appuie sur des bonnes pratiques pour démarrer votre site web
