---
title: Présentation de l’utilisation des fragments de contenu
description: Découvrez comment les fragments de contenu dans Adobe Experience Manager (AEM) as a Cloud Service vous permettent de créer et d’utiliser du contenu structuré, idéal pour une diffusion découplée et la création de pages.
feature: Content Fragments
role: User, Developer, Architect
exl-id: ce9cb811-57d2-4a57-a360-f56e07df1b1a
solution: Experience Manager Sites
source-git-commit: d1e5651dcad75df430e7055f4f8162e666d91f04
workflow-type: tm+mt
source-wordcount: '2021'
ht-degree: 36%

---

# Présentation de l’utilisation des fragments de contenu {#overview-working-with-content-fragments}

Avec Adobe Experience Manager (AEM) as a Cloud Service, les fragments de contenu vous permettent de concevoir, créer, organiser et publier du contenu indépendant des pages. Ils vous permettent de préparer du contenu prêt à être utilisé à plusieurs emplacements et sur plusieurs canaux, idéal pour la [diffusion découplée](/help/headless/what-is-headless.md) et la [création de pages](/help/sites-cloud/authoring/fragments/content-fragments.md).

>[!IMPORTANT]
>
>De nombreuses fonctionnalités décrites dans cette section sont *uniquement* disponibles dans l’as a Cloud Service [&#x200B; Unified Shell](/help/overview/aem-cloud-service-on-unified-shell.md) ; *en ligne* Adobe Experience Manager (AEM), et non dans une instance locale.

>[!IMPORTANT]
>
>Les fragments de contenu sont accessibles à partir de deux consoles : **Fragments de contenu** et **Assets**.
>
>Il existe également deux éditeurs pour créer des fragments de contenu ; bien que la fonctionnalité de base soit la même, il existe quelques différences. Les deux éditeurs sont accessibles à partir des deux consoles.
>
>Cette section traite de la console **Fragments de contenu** et du *nouvel* éditeur de fragment de contenu. Ils ont été développés pour la diffusion de contenu découplé (bien qu’ils puissent être utilisés dans tous les scénarios).
>
>Pour plus d’informations, consultez ce qui suit :
>
>* utilisation de la console **Assets** pour [gérer les fragments de contenu](/help/assets/content-fragments/content-fragments-managing.md)
>* l’utilisation de l’éditeur de fragment de contenu [*original*](/help/assets/content-fragments/content-fragments-variations.md),
>* à l’aide de [Fragments de contenu pour la création de pages](/help/sites-cloud/authoring/fragments/content-fragments.md).


Les fragments de contenu contiennent du contenu structuré :

* Chaque fragment est basé sur un [&#x200B; modèle de fragment de contenu &#x200B;](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md).
   * Le [&#x200B; modèle de fragment de contenu définit la structure &#x200B;](/help/sites-cloud/administering/content-fragments/content-fragment-models.md) fragment obtenu.
* Chaque fragment comprend :
   * **[Principal](#main-and-variations)** - Partie intégrante du fragment qui contient le contenu principal ; existe toujours et ne peut pas être supprimé
   * **[Variations](#main-and-variations)** - une ou plusieurs permutations du contenu, créées par l’auteur ou l’autrice
* La structure peut varier entre :
   * De base
      * Par exemple, un champ de texte multiligne unique.
      * Peut être utilisée pour préparer du contenu simple à utiliser pour la création de pages.
      * Peut également être utilisé pour une diffusion découplée vers votre application.
   * Complexe
      * Combinaison de nombreux champs de types de données variables, notamment le texte, le nombre, la valeur booléenne, ainsi que la date et l’heure.
      * Peut être utilisé pour préparer du contenu plus structuré pour la création de pages ou pour une diffusion découplée vers votre application.
   * Imbriqué
      * Les types de données de référence disponibles vous permettent d’imbriquer votre contenu.
      * A tendance à être utilisé pour une diffusion découplée vers votre application.

Les fragments de contenu peuvent également être diffusés au format JSON, à l’aide des fonctionnalités d’exportation du modèle Sling (JSON) des composants principaux d’AEM. Cette forme de diffusion :

* permet d’utiliser le composant pour gérer les éléments d’un fragment à diffuser
* permet la diffusion en masse ; en ajoutant plusieurs [composants principaux de fragments de contenu](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html?lang=fr) sur la page utilisée pour la diffusion de l’API.

Le nombre de canaux de communication augmente tous les ans. En règle générale, les canaux font référence au mécanisme de diffusion :

* Canal physique (par exemple, bureau ou mobile).
* Forme de diffusion dans un canal physique (par exemple, la « page de détails du produit », la « page de catégorie de produit » pour le bureau, ou le « web mobile » et « l’application mobile » pour le mobile).

Cependant, vous ne souhaitez (probablement) pas utiliser le *exactement* même contenu pour tous les canaux ; vous devez optimiser votre contenu en fonction du canal spécifique.

Les fragments de contenu vous permettent de :

* Étudier comment atteindre efficacement les audiences cibles sur plusieurs canaux.
* Créer et gérer du contenu éditorial neutre pour les canaux.
* Créer des pools de contenu pour divers canaux.
* Concevoir des variations de contenu pour des canaux spécifiques.
* Ajoutez des images à votre texte en insérant des ressources.
* Créez du contenu imbriqué pour refléter la complexité de vos données.

Ces fragments de contenu peuvent ensuite être assemblés pour fournir des expériences sur divers canaux.

>[!NOTE]
>
>Les **fragments de contenu** et les **[fragments d’expérience](/help/sites-cloud/authoring/fragments/content-fragments.md)** représentent deux fonctions distinctes d’AEM :
>* Les **fragments de contenu** sont des contenus éditoriaux, avec définition et structure, mais sans conception visuelle et/ou mise en page supplémentaires. Ils permettent d’accéder aux données structurées, notamment les textes, les nombres et les dates.
>* Les **fragments d’expérience** désignent un contenu parfaitement mis en page : un fragment de page web.
>
>Les fragments d’expérience peuvent être composés de contenu sous la forme de fragments de contenu, mais pas l’inverse.
>
>Pour plus d’informations, voir [Présentation des fragments de contenu et d’expérience dans AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html?lang=fr#content-fragments).

Cette page et les suivantes portent sur les tâches de création, de configuration, de maintenance et d’utilisation de vos fragments de contenu :

* [Activation de la fonctionnalité de fragments de contenu pour votre instance](/help/sites-cloud/administering/content-fragments/setup.md)
* [Modèles de fragment de contenu](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md) : activation, création et [définition](/help/sites-cloud/administering/content-fragments/content-fragment-models.md) vos modèles.
* [Créer vos fragments de contenu](/help/sites-cloud/administering/content-fragments/managing.md#creating-a-content-fragment) (à l’aide de la console Fragments de contenu)

Une fois les fragments créés, vous pouvez :

* [Utilisez la console Fragments de contenu](/help/sites-cloud/administering/content-fragments/managing.md) - pour :
   * accès, publication (pour la prévisualisation ou la production) et référencement de vos fragments
* [Utilisez l’éditeur de fragments de contenu](/help/sites-cloud/administering/content-fragments/authoring.md) - pour :
   * modifier, publier (pour prévisualiser ou produire) et référencer vos fragments
   * collaborer avec d’autres auteurs à l’aide de Commentaires
* [Analysez](/help/sites-cloud/administering/content-fragments/analysis.md) la structure de votre fragment de contenu à l’aide de l’éditeur.
* [Accédez à vos fragments avec GraphQL, pour une diffusion découplée vers vos applications](/help/sites-cloud/administering/content-fragments/content-delivery-with-graphql.md).
* [Intégrer et utiliser vos fragments de contenu dans Adobe Journey Optimizer](/help/sites-cloud/administering/content-fragments/content-fragments-with-journey-optimizer.md)
* Créer et gérer des [lancements pour les fragments de contenu](/help/sites-cloud/administering/content-fragments/launches-for-content-fragments.md)
* [Ou utilisez vos fragments pour la création de pages](/help/sites-cloud/authoring/fragments/content-fragments.md)

>[!NOTE]
>
>Ces pages peuvent être lues conjointement avec :
>
>* [Personnalisation et extensions de fragments de contenu](/help/implementing/developing/extending/content-fragments-customizing.md)
>* [Fragments de contenu – Configuration des composants pour le rendu](/help/implementing/developing/extending/content-fragments-configuring-components-rendering.md)
>* [Prise en charge des fragments de contenu dans l’API HTTP AEM Assets](/help/assets/content-fragments/assets-api-content-fragments.md)
>* [API AEM GraphQL à utiliser avec les fragments de contenu](/help/headless/graphql-api/content-fragments.md)
>* [Création de page à partir de fragments de contenu](/help/sites-cloud/authoring/fragments/content-fragments.md).
>* Les [OpenAPI de modèle de fragment de contenu et de fragment de contenu](/help/headless/content-fragment-openapis.md) sont également disponibles.


## Principaux et variations {#main-and-variations}

Les variations sont une fonction importante des fragments de contenu AEM. Ils vous permettent de créer et de modifier des copies du contenu **Principal** à utiliser sur des canaux et scénarios spécifiques, ce qui rend la diffusion de contenu découplé et la création de pages encore plus flexibles.

* **Principal**

   * **Principal** n’est pas une variation en tant que telle, mais est la base de toutes les variations.
   * Partie intégrante du fragment

      * Chaque fragment de contenu comporte une instance de **Principal**.
      * Impossible de supprimer **Principal**.

   * **Principal** est accessible dans l’éditeur de fragments sous **[Variations](/help/sites-cloud/administering/content-fragments/authoring.md#variations)**.

  >[!NOTE]
  >
  >Dans l’éditeur disponible à partir de la console **Assets**, **Principal** est étiqueté comme **Principal**.

* **Variations**

   * Il s’agit de rendus de texte de fragment spécifiques à fin éditoriale. Les variations peuvent être associées au canal, sans que cela soit obligatoire, et elles peuvent également servir à des modifications locales ad hoc.
   * sont créées en tant que copies de **Principal**, mais peuvent ensuite être modifiées selon les besoins ; il existe souvent un chevauchement de contenu entre les variations elles-mêmes ;
   * Peut être défini lors de la création de fragments dans le panneau de gauche.
   * Stockées dans le fragment, afin d’éviter l’éparpillement des copies de contenu.
   * Les variations peuvent être [comparées et synchronisées](/help/sites-cloud/administering/content-fragments/authoring.md#compare-and-synchronize-rich-text) avec **Principal**.
  <!--
  * Can be [Summarized](/help/sites-cloud/administering/content-fragments/authoring.md#summarizing-text) to quickly truncate the text to a predefined length.
  -->

## Fragments de contenu et services de contenu {#content-fragments-and-content-services}

AEM Content Services est conçu pour généraliser la description et la diffusion de contenu dans/à partir d’AEM à des canaux autres que des pages web.

Il assure la diffusion du contenu aux canaux autres que les pages web AEM classiques, à l’aide de méthodes normalisées qui peuvent être utilisées par tous les clients. Ces canaux peuvent inclure :

* des applications sur une seule page ;
* des applications mobiles natives ;
* d’autres canaux et points de contact externes à AEM.

La diffusion est effectuée au format JSON à l’aide de l’outil d’exportation JSON.

Les fragments de contenu AEM peuvent être utilisés pour décrire et gérer du contenu structuré. Le contenu structuré est défini dans des modèles qui peuvent contenir divers types de contenu : texte, données numériques, valeur booléenne, date et heure, etc.

Associé aux fonctionnalités d’exportation JSON des composants principaux AEM, ce contenu structuré peut ensuite être utilisé pour livrer le contenu AEM à des canaux autres que les pages AEM.

>[!NOTE]
>
>Consultez [Le découplage et AEM](/help/headless/introduction.md) pour une introduction au développement découplé pour AEM Sites as a Cloud Service.

>[!NOTE]
>
>AEM prend également en charge la traduction des fragments de contenu. Consultez [Traduction des actifs](/help/assets/translate-assets.md) pour plus d’informations.

## Type de contenu {#content-type}

Les fragments de contenu sont :

* Une fonctionnalité **Sites**.

* Stockés en tant que **ressources** :

   * Les fragments de contenu (et leurs variantes) peuvent être créés et conservés à partir de la [console Fragments de contenu](#content-fragments-console).
   * Créés et modifiés dans l’[&#x200B; Éditeur de fragment de contenu &#x200B;](/help/sites-cloud/administering/content-fragments/authoring.md).

* Accessible pour la diffusion de contenu à l’aide de l’API AEM GraphQL [&#128279;](/help/headless/graphql-api/content-fragments.md).

* Disponible dans l’[éditeur de page à l’aide du composant Fragment de contenu](/help/sites-cloud/authoring/fragments/content-fragments.md) (composant référençant) :

   * Le [composant principal Fragment de contenu](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html?lang=fr) est disponible pour les auteurs de pages. Il leur permet de référencer et de diffuser le fragment de contenu requis au format HTML ou JSON.

Les fragments de contenu sont une structure de contenu qui :

* Ne comportent pas de disposition ou de conception (la mise en forme du texte est possible pour les champs de texte).
* sont indépendants du mécanisme de diffusion (tel que la page ou le canal) ;
* Contiennent une ou plusieurs [parties constituantes](#constituent-parts-of-a-content-fragment).
* Peuvent [contenir des images ou être connectés à celles-ci](#fragments-with-visual-assets).

### Fragments avec des ressources visuelles {#fragments-with-visual-assets}

Pour permettre aux créateurs et aux créatrices de mieux contrôler leur contenu, les images peuvent être ajoutées et/ou intégrées à un fragment de contenu.

Assets peut être utilisé avec un fragment de contenu de plusieurs manières, chacune ayant ses propres avantages :

* en tant que **référence de contenu**
* dans un champ **texte multiligne**

### Parties constituantes d’un fragment de contenu {#constituent-parts-of-a-content-fragment}

Les ressources Fragment de contenu sont composées des parties suivantes (directement ou indirectement) :

* **Éléments de fragment**

   * Les éléments sont corrélés aux champs de données contenant du contenu.
   * Vous utilisez un [modèle de fragment de contenu](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md) pour créer le fragment de contenu. Les éléments (champs) [spécifiés dans le modèle définissent la structure du fragment](/help/sites-cloud/administering/content-fragments/content-fragment-models.md). Ces éléments (champs) peuvent être de différents types de données.

* **Paragraphes de fragment**

   * Blocs de texte, souvent multilignes, délimités en tant qu’entités individuelles.

   * Activez le contrôle du contenu lors de la création de pages.

* **Métadonnées de fragment**

   * Utilisez les [Schémas de métadonnées de ressources](/help/assets/metadata-schemas.md).
   * Les balises peuvent être créées lorsque vous :

      * Créez et êtes l’auteur ou l’autrice du fragment
      * Ou plus tard, lorsque vous [affichez ou modifiez les propriétés](/help/sites-cloud/administering/content-fragments/authoring.md#view-properties-tags) dans l’éditeur de fragments

  >[!CAUTION]
  >
  >Les profils de traitement des métadonnées ne s’appliquent pas aux fragments de contenu.

  >[!CAUTION]
  >
  >Un modèle de fragment de contenu peut souvent définir des champs de données nommés **Titre** et **Description**. Si ces deux champs existent, il s’agit de champs définis par l’utilisateur ou l’utilisatrice et ils peuvent être mis à jour dans la zone de contenu de l’éditeur.
  >
  >Le fragment de contenu et ses variations comportent également des champs de métadonnées (propriété) appelés **Titre** et **Description**. Ces deux champs de métadonnées font partie intégrante de tout fragment de contenu et de toute variation. Ils sont initialement définis lors de la création du fragment. Elles peuvent être mises à jour dans la zone des propriétés/métadonnées de l’éditeur.

* **[Principal](#main-and-variations)**
* **[Variations](#main-and-variations)**

### Conditions requises pour utiliser des fragments {#required-by-fragments}

Pour créer des fragments de contenu, vous avez besoin des éléments suivants :

* **Modèles de contenu**

   * Sont [activés à l’aide de l’explorateur de configurations](/help/sites-cloud/administering/content-fragments/setup.md).
   * Ils sont [créés à l’aide de la console Fragments de contenu](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#creating-a-content-fragment-model).
   * Obligatoires pour [créer un fragment](/help/sites-cloud/administering/content-fragments/managing.md#creating-content-fragments).
   * Définissent la structure d’un fragment (titre, éléments de contenu et définitions de balise).
   * Les définitions de modèle de fragment de contenu nécessitent un titre et un élément de données ; tout le reste est facultatif.
   * Le modèle peut définir le contenu par défaut, le cas échéant.
   * Les auteurs ne peuvent pas modifier la structure définie lors de la création de contenu de fragment ; ils peuvent toutefois ouvrir l’éditeur de modèles à partir de l’éditeur de fragments.
   * Les modifications apportées à un modèle après la création de fragments de contenu dépendants peuvent avoir un impact sur ces fragments de contenu.

Pour utiliser vos fragments de contenu pour une diffusion de contenu découplé, vous avez également besoin des éléments suivants :

* une requête [GraphQL](/help/headless/graphql-api/content-fragments.md) pour demander le contenu requis
* ce contenu peut ensuite être utilisé pour développer vos propres SPA pour AEM. Pour plus d’informations, consultez les documents suivants :

   * [Tutoriel sur SPA WKND](/help/implementing/developing/hybrid/wknd-tutorial.md)
   * [Prise en main avec React](/help/implementing/developing/hybrid/getting-started-react.md)
   * [Prise en main avec Angular](/help/implementing/developing/hybrid/getting-started-angular.md)

Pour utiliser vos fragments de contenu pour la création de pages, vous avez également besoin des éléments suivants :

* Un **composant de fragment de contenu**

   * Utilitaire de diffusion du fragment au format HTML et/ou JSON.
   * Obligatoire pour [référencer le fragment sur une page](/help/sites-cloud/authoring/fragments/content-fragments.md).
   * Responsable de la mise en page et de la diffusion d’un fragment, par exemple les canaux.
   * Les fragments ont besoin d’un ou de plusieurs composants dédiés pour définir la mise en page, ainsi que diffuser tous les éléments/variations et le contenu associé.
   * Faire glisser un fragment sur une page en mode Création permet d’associer automatiquement le composant requis.
   * Voir le [composant principal Fragment de contenu](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html?lang=fr).

## Console Fragments de contenu {#content-fragments-console}

La console Fragments de contenu est dédiée à la gestion, à la recherche et à la création de [Fragments de contenu](/help/sites-cloud/administering/content-fragments/managing.md), [Modèles de fragment de contenu](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md) et [Assets](/help/sites-cloud/administering/content-fragments/assets-content-fragments-console.md). Optimisée pour une utilisation dans un contexte découplé, elle est également utilisée lors de la création de fragments de contenu et de modèles de fragment de contenu à utiliser dans la création de pages.

La console est directement accessible à partir du niveau supérieur de la navigation globale.

![Navigation globale - Console Fragments de contenu](assets/cf-managing-global-navigation.png)

Vous pouvez utiliser le panneau tout à gauche pour sélectionner le type de ressource à afficher, parcourir et gérer :

![Console Fragments de contenu - navigation](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-navigation.png)

Pour plus d’informations, voir :

* [Fragments de contenu](/help/sites-cloud/administering/content-fragments/managing.md)
* [Modèles de fragment de contenu](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md)
* [Assets](/help/sites-cloud/administering/content-fragments/assets-content-fragments-console.md)

* Plusieurs [raccourcis clavier](/help/sites-cloud/administering/content-fragments/keyboard-shortcuts.md) sont disponibles dans cette console

>[!CAUTION]
>
>Cette console est *uniquement* disponible dans l’as a Cloud Service Adobe Experience Manager (AEM) en ligne.

>[!NOTE]
>
>Votre équipe de projet peut personnaliser la console et l’éditeur si nécessaire. Voir [Personnalisation de la console et de l’éditeur de fragments de contenu](/help/implementing/developing/extending/content-fragments-console-and-editor.md) pour plus d’informations.

## Exemple d’utilisation {#example-usage}

Un fragment, avec ses éléments et ses variations, peut être utilisé afin de créer du contenu homogène sur plusieurs canaux. Lors de la conception de votre fragment, vous devez tenir compte de ce qui sera utilisé et où.

### Exemple WKND {#wknd-sample}

Les exemples [Site WKND et WKND Shared](/help/implementing/developing/introduction/develop-wknd-tutorial.md) sont fournis pour vous aider à en savoir plus sur AEM as a Cloud Service.

<!-- CHECK: which links can/should be used these days? -->

Le projet WKND comprend :

* les modèles de fragments de contenu disponibles sous :

   * `.../libs/dam/cfm/models/console/content/models.html/conf/wknd`

   * `.../ui#/aem/libs/dam/cfm/models/console/content/models.html/conf/wknd-shared`

* les fragments de contenu (et autres contenus) disponibles sous :

   * `.../assets.html/content/dam/wknd/en`
