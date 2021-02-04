---
title: En tête et sans tête en AEM
description: aem projets peuvent être mis en oeuvre dans un modèle plein d'esprit et sans tête, mais le choix n'est pas binaire. aem offre la flexibilité d'exploiter les avantages des deux modèles dans un seul projet.
translation-type: tm+mt
source-git-commit: 772717b7ad3baa17a58e251c128663035eb89931
workflow-type: tm+mt
source-wordcount: '1009'
ht-degree: 0%

---


# En-tête et sans en-tête en AEM {#headful-headless}

Les projets Adobe Experience Manager peuvent être mis en oeuvre à la fois dans des modèles sans tête et en tête, mais le choix n&#39;est pas binaire. aem offre la flexibilité d&#39;exploiter les avantages des deux modèles dans un seul projet. Ce document fournit un aperçu des différents modèles et décrit les niveaux d&#39;intégration SPA.

## Présentation {#overview}

aem offre de puissants outils pour gérer à la fois la création de contenu et sa diffusion sur une seule plate-forme. Il s&#39;agit d&#39;un modèle traditionnel de gestion de contenu &quot;dynamique&quot;, où les auteurs et les développeurs de contenu travaillent sur la même plate-forme pour fournir les expériences aux consommateurs de contenu.

Les AEM peuvent également être utilisés pour gérer simplement le contenu, ce qui permet de gérer la présentation et la diffusion du contenu par une autre plateforme. Il s&#39;agit du modèle de gestion de contenu &quot;sans tête&quot;, où les auteurs et les développeurs de contenu travaillent sur différentes plateformes pour fournir une expérience aux consommateurs de contenu.

Mais ce n&#39;est pas nécessairement un choix binaire. aem offres une flexibilité sans précédent, vous permettant d&#39;exploiter les avantages des deux modèles pour votre projet.

![Modèles d’implémentation AEM](headless/assets/aem-implementation-models.png)

Dans un modèle avec ou sans pile, le contenu est géré dans le référentiel AEM et les composants AEM basés sur Java, HTL, etc. sont utilisées pour effectuer le rendu du contenu pour l’expérience utilisateur. Dans ce modèle, la création du contenu, sa mise en forme, sa présentation et sa diffusion se produisent en AEM.

Dans un modèle sans en-tête, le contenu est géré dans le référentiel AEM, mais diffusé via des API telles que REST et GraphQL sur un autre système afin de générer le contenu pour l’expérience utilisateur. Dans ce modèle, le contenu est créé dans AEM, mais il est mis en forme, présenté et diffusé sur une autre plateforme.

Les applications d’une seule page (SPA) sont souvent la destination du contenu diffusé sans encombre par AEM. Cependant, ces SPA ne doivent pas nécessairement être entièrement externes à l&#39;AEM. aem vous permet de décider dans quelle mesure votre SPA est intégrée à l&#39;AEM. Prenons un exemple.

## Exemple de boutique Web {#web-shop-example}

Supposons que vous ayez un site Web pour votre société en tant que SPA. Vous y trouverez tous les détails et images de votre produit. Vous présentez ensuite AEM afin de renforcer vos efforts marketing, tels que les sites promotionnels, les blogs et le contenu des campagnes. Comment intégrer les deux ? aem permet un éventail d’options :

* **Permettre aux systèmes de fonctionner indépendamment.**
* **Fournissez le site Web avec un contenu limité provenant d&#39;AEM via GraphQL.** Le contenu peut être créé par des auteurs en AEM, mais uniquement visible via la boutique web SPA.
* **Incorporez le magasin SPA Web dans AEM.** Le contenu peut être créé par des auteurs en AEM, et affiché en AEM dans le contexte de la boutique Web, mais pas manipulé.
* **Incorporez la boutique Web SPA dans AEM et activez les points modifiables.** Le contenu peut être créé par des auteurs en AEM, et affiché en AEM dans le contexte de la boutique en ligne, et les auteurs ont une capacité limitée de manipuler le contenu de la boutique en ligne de l’SPA dans l’.
* **Incorporez les pages Web SPA dans AEM et activez des zones entières pour modification.** Le contenu peut être créé par des auteurs en AEM, et affiché en AEM dans le contexte de la boutique en ligne, et les auteurs ont une capacité limitée de manipuler le contenu de la boutique en ligne de l’SPA dans l’.

La section suivante examine ces niveaux d’intégration de manière plus détaillée.

>[!NOTE]
>
>Bien sûr, vous pouvez également réimplémenter le site web SPA comme un AEM pleinement opérationnel [à l&#39;aide de la structure de l&#39;éditeur d&#39;.](/help/implementing/developing/hybrid/introduction.md) Si vous avez déjà AEM et souhaitez créer un nouveau site Web ou un autre SPA, il s&#39;agit de la méthode recommandée, mais elle n&#39;entre pas dans le cadre de ce document.

## Niveaux d&#39;intégration SPA {#integration-levels}

SPA intégration se fait sur un spectre de quatre niveaux en AEM.

* **Niveau 0 : Aucune intégration**
   * Le SPA et l&#39;AEM existent séparément et n&#39;échangent aucune information.
   * Le contenu est créé, géré et distribué indépendamment sur deux systèmes distincts.
* **Niveau 1 : Intégration de fragments de contenu**
   * [Les ](/help/assets/content-fragments/content-fragments.md) fragments de contenu sont utilisés dans AEM pour créer et gérer du contenu limité pour le SPA.
   * Le SPA récupère ce contenu par l&#39;intermédiaire de l&#39;API [GraphQL.](/help/assets/content-fragments/graphql-api-content-fragments.md)
   * Certains contenus sont gérés en AEM et d&#39;autres dans un système externe.
   * Le contenu ne peut être affiché que dans le SPA.
* **Niveau 2 : Incorporer le SPA dans AEM**
   * [Les ](/help/assets/content-fragments/content-fragments.md) fragments de contenu sont utilisés dans AEM pour créer et gérer le contenu pour le SPA.
   * Le SPA récupère ce contenu par l&#39;intermédiaire de l&#39;API [GraphQL.](/help/assets/content-fragments/graphql-api-content-fragments.md)
   * Certains contenus sont gérés en AEM et d&#39;autres dans un système externe.
   * Le contenu peut être visualisé en contexte dans AEM.
   * Le contenu limité peut être modifié dans AEM.
* **Niveau 3 : Incorporer et activer entièrement les SPA dans AEM**
   * [Les ](/help/assets/content-fragments/content-fragments.md) fragments de contenu sont utilisés dans AEM pour créer et gérer le contenu pour le SPA.
   * Le SPA récupère ce contenu par l&#39;intermédiaire de l&#39;API [GraphQL.](/help/assets/content-fragments/graphql-api-content-fragments.md)
   * Le contenu peut être visualisé en contexte dans AEM.
   * La plupart du contenu peut être modifié dans AEM.

Le niveau 1 est un exemple typique d’une mise en oeuvre sans tête. Cependant, les auteurs de contenu ne peuvent vue leur contenu qu’en contexte au sein du SPA. aem n&#39;est qu&#39;un outil de création.

L&#39;avantage et la souplesse de l&#39;AEM deviennent évidents avec les niveaux 2 et 3 tout en conservant les avantages de SPA. Les auteurs de contenu peuvent créer leur contenu dans AEM, mais ils peuvent également le voir dans son contexte dans AEM. Le SPA gagne la capacité d&#39;être écrit en AEM, mais toujours être livré comme un SPA.

## Mise en oeuvre des niveaux d&#39;intégration {#implementing}

Il existe différents outils en AEM disponibles en fonction du niveau d’intégration choisi. Chaque niveau s’appuie sur les outils utilisés précédemment. La liste suivante établit un lien vers les ressources pertinentes.

* **Niveau 1 :** Les fragments de contenu et le  [cadre sans en-tête ](/help/implementing/developing/headless/introduction.md) AEM peuvent être utilisés pour diffuser du contenu AEM aux SPA.
* **Niveau 2 :** En plus du niveau 1 :
   * [Le ](/help/implementing/developing/hybrid/remote-page.md) composant RemotePage peut être utilisé pour incorporer le SPA externe dans AEM où le contenu AEM peut être affiché en contexte.
   * Certains points de la SPA peuvent également être activés pour [autoriser une modification limitée dans AEM.](/help/implementing/developing/hybrid/editing-external-spa.md)
* **Niveau 3 :** En plus du niveau 2 :
   * Des zones entières du SPA peuvent être activées pour permettre une modification complète dans AEM.
