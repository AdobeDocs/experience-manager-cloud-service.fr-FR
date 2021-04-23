---
title: Facultatif - Comment créer des applications d'une seule page (SPA) avec AEM
description: Dans cette suite facultative du Parcours de développement AEM sans tête, vous découvrirez comment AEM peut combiner une diffusion sans tête avec les fonctionnalités CMS à pile complète traditionnelles et comment vous pouvez créer des SPA modifiables à l’aide de la structure de l’éditeur d’.
hide: true
hidefromtoc: true
index: false
translation-type: tm+mt
source-git-commit: 1b6dbf401ff921964537f6c79d12544789e93c92
workflow-type: tm+mt
source-wordcount: '1301'
ht-degree: 34%

---


# Comment créer des applications d&#39;une seule page (SPA) avec AEM {#create-spa}

>[!CAUTION]
>
>TRAVAUX EN COURS - La création de ce document est en cours et ne doit pas être comprise comme complète ou définitive ni être utilisée à des fins de production.

Dans cette suite facultative du [AEM Parcours de développement sans tête](overview.md), vous découvrirez comment AEM peut combiner une diffusion sans tête avec les fonctionnalités CMS à pile complète traditionnelles et comment vous pouvez créer des SPA modifiables à l&#39;aide de la structure de l&#39;éditeur d&#39;, ainsi que l&#39;intégration de  externes, ce qui vous permettra de modifier le cas échéant.

## L&#39;histoire jusqu&#39;à présent {#story-so-far}

À ce stade, vous devez avoir terminé l&#39;ensemble du [Parcours de développement AEM sans tête](overview.md) et comprendre les bases d&#39;une diffusion sans tête en AEM, y compris la compréhension des éléments suivants :

* Différence entre la diffusion de contenu sans en-tête et avec en-tête.
* AEM fonctionnalités sans tête.
* Comment organiser et AEM projet sans tête.
* Comment créer du contenu sans en-tête en AEM.
* Comment récupérer et mettre à jour du contenu sans en-tête dans AEM.
* Comment vivre avec un projet AEM sans tête.

Vous êtes donc maintenant soit parti en direct avec votre premier projet AEM sans tête, soit vous avez toutes les connaissances nécessaires pour le faire. Félicitations ! 

Alors pourquoi lisez-vous cette suite supplémentaire facultative du parcours ? Vous vous souvenez probablement que dans le document [Getting Started](getting-started.md#integration-levels), nous avons discuté brièvement comment AEM non seulement prend en charge la diffusion sans tête et les modèles traditionnels à pile complète, mais peut également prendre en charge des modèles hybrides qui combinent les avantages des deux. Bien qu&#39;ils ne soient pas le modèle traditionnel sans tête, ces modèles hybrides peuvent offre une flexibilité sans précédent à certains projets.

Cet article s&#39;appuie sur vos connaissances de AEM sans en-tête en explorant en profondeur comment vous pouvez créer vos propres applications d&#39;une seule page (SPA) qui sont en fait modifiables dans les AEM. Ainsi, vous pouvez créer du contenu et le diffusion sans encombre à un SPA, mais ce SPA reste modifiable en AEM.

## Intention {#objective}

Ce document vous aide à comprendre comment les applications d’une seule page sont développées à l’aide de la structure AEM SPA Editor. Après avoir lu ce document, vous devez :

* Comprendre la fonction de base de l’éditeur SPA.
* Connaissez les exigences de création d’un SPA entièrement modifiable pour l’AEM.
* Comprendre comment les SPA externes peuvent être intégrées aux AEM.
* Comprenez comment le rendu côté serveur doit ou non être implémenté.

## Exigences et conditions préalables {#requirements-prerequisites}

Un certain nombre de conditions sont requises avant de commencer à travailler avec SPA dans AEM.

### Connaissances {#knowledge}

* Expérience de développement création de SPA avec des cadres de réaction ou d&#39;Angular
* Compétences de base en AEM création de fragments de contenu et utilisation de l’éditeur
* Veillez à consulter le document [En-tête et sans en-tête en AEM](/help/implementing/developing/headful-headless.md) afin de comprendre les différents niveaux d&#39;intégration SPA possible.

### Outils {#tools}

* Accès Sandbox pour tester le déploiement de votre projet
* Instance de développement local pour la modélisation et le test des données
* SPA externe existante (facultatif, selon le modèle d’intégration choisi)
* Archétype de projet AEM

## Qu’est-ce qu’une SPA ? {#what-is-a-spa}

Une application sur une seule page (SPA) diffère d’une page conventionnelle en cela qu’elle est rendue côté client et qu’elle est principalement pilotée par JavaScript, en utilisant les appels Ajax pour charger les données et mettre la page à jour dynamiquement. La plupart ou la totalité du contenu est récupérée une fois au chargement d’une seule page avec des ressources supplémentaires chargées de manière asynchrone, selon les besoins, en fonction de l’interaction de l’utilisateur avec la page.

Cela limite la nécessité d’actualiser la page et offre à l’utilisateur une expérience harmonieuse, rapide et rappelant davantage l’expérience d’une application native.

L’éditeur de SPA AEM permet aux développeurs front-end de créer des SPA qui peuvent être intégrées à un site AEM, ce qui permet aux créateurs de contenu de modifier le contenu SPA aussi facilement qu’un autre contenu AEM.

## Pourquoi une SPA ? {#why-spa}

Plus rapide, fluide et ressemblant davantage à une application native, une SPA, de par son fonctionnement, offre une expérience très attrayante, non seulement pour le visiteur de la page web, mais aussi pour les spécialistes du marketing et les développeurs.

Pour obtenir une description complète des SPA et des raisons de leur utilisation, consultez la section [ressources supplémentaires](#additional-resources) pour obtenir des liens vers une documentation plus détaillée.

## AEM gère SPA

Le développement d’applications sur une seule page sur AEM suppose que le développeur front-end respecte les bonnes pratiques standard lors de la création d’une SPA. Si le développeur front-end respecte ces bonnes pratiques générales, ainsi que certains principes spécifiques à AEM, sa SPA sera fonctionnelle avec AEM et ses fonctionnalités de création de contenu.

* **Portabilité**  - Comme pour tout composant, les composants SPA doivent être construits pour être aussi portables que possible. La SPA doit être créée avec des composants portables et réutilisables.
* **AEM détermine la structure du site** : le développeur front-end crée des composants et possède leur structure interne, mais il dépend d’AEM pour définir la structure de contenu du site.
* **Rendu dynamique** : tout le rendu doit être dynamique.
* **Routage dynamique** : la SPA assure le routage, et AEM l’écoute et s’appuie dessus pour l’extraction. Tout routage devrait également être dynamique.

Pour une description complète de la façon dont AEM traite SPA, consultez la section [ressources supplémentaires](#additional-resources) pour obtenir des liens vers une documentation plus détaillée.

## Éditeur SPA de l&#39;AEM {#aem-spa-editor}

Les sites créés à l’aide de structures SPA courantes, telles que React et AngularJS, chargent leur contenu via le format JSON dynamique et ne fournissent pas la structure HTML dont l’éditeur de page AEM a besoin pour passer des commandes de modification.

Pour activer la modification d’applications sur une seule page dans AEM, il faut qu’il y ait une correspondance entre la sortie JSON de l’application et le modèle de contenu dans le répertoire AEM afin d’enregistrer les modifications apportées au contenu.

La prise en charge des applications sur une seule page dans AEM s’accompagne d’une fine couche JS qui interagit avec le code JS de l’application lorsqu’elle est chargée dans l’éditeur de pages avec lequel des événements peuvent être envoyés. L’emplacement des commandes d’édition peut être activé pour permettre une modification en contexte. Cette fonction repose sur le concept de point de terminaison de l’API Content Services, étant donné que le contenu de l’application sur une seule page doit être chargé par le biais de Content Services.

Pour une description complète de l&#39;AEM SPA Editor, consultez la section [ressources supplémentaires](#additional-resources) pour obtenir des liens vers une documentation plus détaillée.

## Hébergement des SPA existantes {#existing-spas}

Si vous disposez d’un SPA existant, AEM prend en charge l’intégration de celui-ci dans l’AEM afin qu’il soit visible pour les auteurs de contenu dans l’éditeur d’. Cela peut s’avérer très utile pour vue du contenu qu’ils créent par l’intermédiaire de Fragments de contenu dans le contexte de l’application finale dans laquelle il sera utilisé.

De plus, avec de petites modifications seulement, vous pouvez activer certaines capacités d&#39;édition pour les SPA externes dans l&#39;éditeur AEM.

Le composant RemotePage permet le rendu d’un SPA externe dans AEM.

Pour obtenir une description complète de la façon de rendre un SPA externe modifiable en AEM, consultez la section [ressources supplémentaires](#additional-resources) pour obtenir des liens vers une documentation plus détaillée.

## Eléments suivants {#what-is-next}

Pour commencer à développer votre propre SPA pour AEM, consultez les documents suivants :

* [Tutoriel sur SPA WKND](/help/implementing/developing/hybrid/wknd-tutorial.md)
* [Prise en main de la réaction](/help/implementing/developing/hybrid/getting-started-react.md)
* [Prise en main de l’Angular](/help/implementing/developing/hybrid/getting-started-angular.md)

Si vous devez adapter un SPA existant pour l’utiliser dans AEM, passez en revue les documents suivants :

* [Composant RemotePage](/help/implementing/developing/hybrid/remote-page.md)
* [Modification d’une SPA externe dans AEM](/help/implementing/developing/hybrid/editing-external-spa.md)

Voir ci-dessous [des ressources supplémentaires](#additional-resources) qui peuvent vous aider à approfondir SPA sujets dans AEM.

## Ressources supplémentaires {#additional-resources}

Voici quelques autres ressources qui approfondissent certains concepts mentionnés dans ce document.

* [En-tête et sans en-tête en AEM](/help/implementing/developing/headful-headless.md) - Description des différents modèles de diffusion disponibles en AEM
* [Introduction et présentation des SPA.](/help/implementing/developing/hybrid/introduction.md) - Une bonne introduction aux SPA en AEM
* [Développement de SPA pour l&#39;AEM](/help/implementing/developing/hybrid/developing.md)  - Lignes directrices sur la façon de développer des SPA pour l&#39;
* [Aperçu](/help/implementing/developing/hybrid/editor-overview.md)  de SPA Editeur - Détails du fonctionnement de SPA Editeur
* [Rendu](/help/implementing/developing/hybrid/ssr.md)  côté serveur - Comment configurer SSR pour AEM SPA
* [documents](/help/implementing/developing/hybrid/reference-materials.md)  de référence SPA : références à l&#39;API JavaScript et liens vers les projets AEM GitHub Open Source
* [Fragments](/help/assets/content-fragments/content-fragments.md)  de contenu - Comment créer des fragments de contenu
* [AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr)  - Maven template qui crée un projet Adobe Experience Manager (AEM) minimal basé sur les meilleures pratiques comme point de départ pour votre site Web
