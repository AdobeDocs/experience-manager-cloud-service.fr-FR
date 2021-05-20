---
title: Facultatif - Comment créer des applications d’une seule page (SPA) avec AEM
description: Dans cette suite facultative du Parcours de développement AEM sans interface utilisateur, vous découvrirez comment AEM peut combiner une diffusion sans interface avec des fonctionnalités CMS en pile complète traditionnelles et comment créer des données modifiables à l’aide de la structure Editor.
source-git-commit: ddd320ae703225584d4a2055d0f882d238d60987
workflow-type: tm+mt
source-wordcount: '1273'
ht-degree: 35%

---


# Comment créer des applications d’une seule page (SPA) avec AEM {#create-spa}

Dans cette suite facultative du [Parcours de développement AEM sans interface utilisateur,](overview.md) vous découvrez comment AEM peut combiner la diffusion sans interface avec les fonctionnalités CMS en pile complète traditionnelles et comment créer des données modifiables à l’aide de la structure de l’éditeur d’, ainsi qu’intégrer des  externes, en activant les fonctionnalités d’édition selon les besoins.

## L&#39;histoire jusqu&#39;à présent {#story-so-far}

À ce stade, vous devez avoir terminé l’ensemble du [Parcours de développement AEM sans affichage](overview.md) et comprendre les principes de base de la diffusion sans affichage dans AEM, y compris une compréhension des éléments suivants :

* Différence entre diffusion de contenu sans interface utilisateur graphique et en mode plein écran.
* AEM fonctionnalités sans interface.
* Comment organiser et AEM un projet sans affichage.
* Comment créer du contenu sans interface dans AEM.
* Comment récupérer et mettre à jour du contenu sans affichage dans AEM.
* Mise en ligne d’un projet AEM sans affichage.

Vous avez donc soit mis en ligne avec votre premier projet AEM sans tête, soit vous disposez de toutes les connaissances nécessaires pour le faire. Félicitations ! 

Alors pourquoi lisez-vous cette suite supplémentaire et facultative du parcours ? Vous vous souvenez sans doute que dans la section [Prise en main](getting-started.md#integration-levels), nous avons brièvement expliqué comment l’AEM ne prend pas seulement en charge la livraison sans interface et les modèles de pile complète traditionnels, mais peut également prendre en charge des modèles hybrides qui combinent les avantages des deux. Bien qu&#39;il ne s&#39;agisse pas du modèle classique sans tête, de tels modèles hybrides peuvent offrir une flexibilité sans précédent à certains projets.

Cet article s’appuie sur vos connaissances d’AEM sans tête en explorant en profondeur la manière dont vous pouvez créer vos propres applications d’une seule page (SPA) qui sont en fait modifiables dans l’ensemble d’Adobe. Ainsi, vous pouvez créer du contenu et le diffuser intégralement vers un SPA, mais ce SPA reste modifiable dans l’.

## Intention {#objective}

Ce document vous aide à comprendre comment les applications d’une seule page sont développées à l’aide de la structure AEM SPA Editor. Après avoir lu ce document, vous devez :

* Comprendre la fonction de base de l’éditeur SPA.
* Découvrez les exigences relatives à la création d’un SPA entièrement modifiable pour AEM.
* Découvrez comment les SPA externes peuvent être intégrées à AEM.
* Comprenez comment le rendu côté serveur doit ou ne doit pas être implémenté.

## Conditions requises et conditions préalables {#requirements-prerequisites}

Avant de commencer à travailler avec SPA dans AEM, plusieurs conditions sont requises.

### Connaissances {#knowledge}

* Expérience de développement créant des SPA avec des structures React ou Angular
* Compétences de base AEM la création de fragments de contenu et l’utilisation de l’éditeur
* Veillez à consulter le document [En-tête et sans en-tête dans AEM](/help/implementing/developing/headful-headless.md) afin de comprendre les différents niveaux d’intégration SPA possibles.

### Outils {#tools}

* Accès aux environnements de test pour tester le déploiement de votre projet
* Instance de développement locale pour la modélisation et le test des données
* SPA externe existante (facultatif, selon le modèle d’intégration choisi)
* Archétype de projet AEM

## Qu’est-ce qu’une SPA ? {#what-is-a-spa}

Une application sur une seule page (SPA) diffère d’une page conventionnelle en cela qu’elle est rendue côté client et qu’elle est principalement pilotée par JavaScript, en utilisant les appels Ajax pour charger les données et mettre la page à jour dynamiquement. La plupart ou la totalité du contenu est récupérée une fois au chargement d’une seule page avec des ressources supplémentaires chargées de manière asynchrone, selon les besoins, en fonction de l’interaction de l’utilisateur avec la page.

Cela limite la nécessité d’actualiser la page et offre à l’utilisateur une expérience harmonieuse, rapide et rappelant davantage l’expérience d’une application native.

L’éditeur de SPA AEM permet aux développeurs front-end de créer des SPA qui peuvent être intégrées à un site AEM, ce qui permet aux créateurs de contenu de modifier le contenu SPA aussi facilement qu’un autre contenu AEM.

## Pourquoi une SPA ? {#why-spa}

Plus rapide, fluide et ressemblant davantage à une application native, une SPA, de par son fonctionnement, offre une expérience très attrayante, non seulement pour le visiteur de la page web, mais aussi pour les spécialistes du marketing et les développeurs.

Pour obtenir une description complète des SPA et des raisons de leur utilisation, reportez-vous à la section [Ressources supplémentaires](#additional-resources) pour obtenir des liens vers une documentation plus détaillée.

## Comment AEM gère SPA

Le développement d’applications sur une seule page sur AEM suppose que le développeur front-end respecte les bonnes pratiques standard lors de la création d’une SPA. Si le développeur front-end respecte ces bonnes pratiques générales, ainsi que certains principes spécifiques à AEM, sa SPA sera fonctionnelle avec AEM et ses fonctionnalités de création de contenu.

* **Portabilité**  : comme pour tout composant, les composants SPA doivent être conçus pour être aussi portables que possible. La SPA doit être créée avec des composants portables et réutilisables.
* **AEM détermine la structure du site** : le développeur front-end crée des composants et possède leur structure interne, mais il dépend d’AEM pour définir la structure de contenu du site.
* **Rendu dynamique** : tout le rendu doit être dynamique.
* **Routage dynamique** : la SPA assure le routage, et AEM l’écoute et s’appuie dessus pour l’extraction. Tout routage devrait également être dynamique.

Pour une description complète de la façon dont AEM gère SPA, consultez la section [Ressources supplémentaires](#additional-resources) pour obtenir des liens vers une documentation plus détaillée.

## Éditeur de SPA d’AEM {#aem-spa-editor}

Les sites créés à l’aide de structures SPA courantes, telles que React et AngularJS, chargent leur contenu via le format JSON dynamique et ne fournissent pas la structure HTML dont l’éditeur de page AEM a besoin pour passer des commandes de modification.

Pour activer la modification d’applications sur une seule page dans AEM, il faut qu’il y ait une correspondance entre la sortie JSON de l’application et le modèle de contenu dans le répertoire AEM afin d’enregistrer les modifications apportées au contenu.

La prise en charge des applications sur une seule page dans AEM s’accompagne d’une fine couche JS qui interagit avec le code JS de l’application lorsqu’elle est chargée dans l’éditeur de pages avec lequel des événements peuvent être envoyés. L’emplacement des commandes d’édition peut être activé pour permettre une modification en contexte. Cette fonction repose sur le concept de point de terminaison de l’API Content Services, étant donné que le contenu de l’application sur une seule page doit être chargé par le biais de Content Services.

Pour obtenir une description complète de l’éditeur SPA d’AEM, reportez-vous à la section [Ressources supplémentaires](#additional-resources) pour obtenir des liens vers une documentation plus détaillée.

## Hébergement des SPA existantes {#existing-spas}

Si vous disposez d’un SPA existant, AEM prend en charge son intégration dans afin qu’il soit visible par les auteurs de contenu dans l’éditeur d’. Cela peut s’avérer très utile pour afficher le contenu qu’ils créent via des fragments de contenu dans le contexte de l’application finale où il sera utilisé.

En outre, avec seulement de petites modifications, vous pouvez activer certaines fonctionnalités d’édition pour les SPA externes dans l’éditeur AEM.

Le composant RemotePage permet le rendu d’un SPA externe dans AEM.

Pour une description complète de la manière de rendre un SPA externe modifiable dans AEM, consultez la section [ressources supplémentaires](#additional-resources) pour obtenir des liens vers une documentation plus détaillée.

## Suite {#what-is-next}

Pour commencer à développer votre propre SPA pour AEM, consultez les documents suivants :

* [Tutoriel sur SPA WKND](/help/implementing/developing/hybrid/wknd-tutorial.md)
* [Prise en main avec React](/help/implementing/developing/hybrid/getting-started-react.md)
* [Prise en main de Angular](/help/implementing/developing/hybrid/getting-started-angular.md)

Si vous devez adapter un SPA existant pour l’utiliser dans AEM, consultez les documents suivants :

* [Composant RemotePage](/help/implementing/developing/hybrid/remote-page.md)
* [Modification d’une SPA externe dans AEM](/help/implementing/developing/hybrid/editing-external-spa.md)

Voir ci-dessous les [ressources supplémentaires](#additional-resources) qui peuvent vous aider à approfondir SPA sujets dans AEM.

## Ressources supplémentaires {#additional-resources}

Vous trouverez ci-dessous quelques ressources supplémentaires qui approfondissent certains concepts mentionnés dans ce document.

* [Headful and Headless dans AEM](/help/implementing/developing/headful-headless.md)  - Description des différents modèles de diffusion disponibles dans AEM
* [Introduction et présentation des SPA.](/help/implementing/developing/hybrid/introduction.md) - Une bonne introduction à SPA en AEM
* [Développement de SPA pour AEM](/help/implementing/developing/hybrid/developing.md)  - Consignes sur la manière de développer des SPA pour
* [SPA Aperçu](/help/implementing/developing/hybrid/editor-overview.md)  de l’éditeur : détails du fonctionnement de l’éditeur de SPA
* [Rendu côté serveur](/help/implementing/developing/hybrid/ssr.md)  - Comment configurer le rendu côté serveur pour AEM SPA
* [SPA Documents de référence](/help/implementing/developing/hybrid/reference-materials.md)  : références d’API JavaScript et liens vers les AEM open source SPA projets GitHub
* [Fragments de contenu](/help/assets/content-fragments/content-fragments.md)  - Comment créer des fragments de contenu
* [AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr)  : modèle Maven qui crée un projet Adobe Experience Manager (AEM) minimal basé sur les bonnes pratiques comme point de départ de votre site web.
