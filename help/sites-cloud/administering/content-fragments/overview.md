---
title: Présentation de l’utilisation des fragments de contenu
description: Découvrez comment les fragments de contenu de Adobe Experience Manager (AEM) vous permettent de créer et d’utiliser du contenu structuré idéal pour la diffusion sans interface utilisateur et la création de pages.
feature: Content Fragments
role: User, Developer, Architect
exl-id: ce9cb811-57d2-4a57-a360-f56e07df1b1a
solution: Experience Manager Sites
source-git-commit: 86a2c5f35d82010c84b74b6b5f0da09fd87c2b7a
workflow-type: tm+mt
source-wordcount: '1818'
ht-degree: 41%

---

# Présentation de l’utilisation des fragments de contenu {#overview-working-with-content-fragments}

As a Cloud Service Adobe Experience Manager (AEM), les fragments de contenu vous permettent de concevoir, créer, organiser et publier du contenu indépendant des pages. Ils vous permettent de préparer du contenu prêt à être utilisé à plusieurs emplacements et sur plusieurs canaux, idéal pour [la diffusion sans interface](/help/headless/what-is-headless.md) et la [création de pages](/help/sites-cloud/authoring/fragments/content-fragments.md).

>[!IMPORTANT]
>
>Les fragments de contenu sont accessibles à partir de deux consoles : **Fragments de contenu** et **Assets**.
>
>Il existe également deux éditeurs pour la création de fragments de contenu. Bien que la fonctionnalité de base soit la même, il existe des différences. Les deux éditeurs sont accessibles à partir des deux consoles.
>
>Cette section traite de la console **Fragments de contenu** et de l’ *nouvel* éditeur de fragments de contenu. Ils ont été développés pour la diffusion de contenu sans interface utilisateur graphique (bien qu’ils puissent être utilisés pour tous les scénarios).
>
>Pour plus d’informations, consultez ce qui suit :
>
>* utilisation de la console **Assets** pour [gérer les fragments de contenu](/help/assets/content-fragments/content-fragments-managing.md)
>* l’utilisation de l’ [*éditeur de fragment de contenu* d’origine](/help/assets/content-fragments/content-fragments-variations.md),
>* utilisation de [fragments de contenu pour la création de page](/help/sites-cloud/authoring/fragments/content-fragments.md).


Les fragments de contenu contiennent du contenu structuré :

* Chaque fragment est basé sur un [modèle de fragment de contenu](/help/sites-cloud/administering/content-fragments/content-fragment-models.md).
   * Le modèle de fragment de contenu définit la structure du fragment résultant.
* Chaque fragment se compose des éléments suivants :
   * **[Main](#main-and-variations)** : partie intégrante du fragment qui contient le contenu principal ; existe toujours, ne peut pas être supprimé.
   * **[Variations](#main-and-variations)** : une ou plusieurs permutations du contenu, créées par l’auteur
* La structure peut varier entre :
   * De base
      * Par exemple, un champ de texte simple à plusieurs lignes.
      * Peut être utilisée pour préparer du contenu simple à utiliser pour la création de pages.
      * Peut également être utilisé pour la diffusion sans interface vers votre application.
   * Complexe
      * Combinaison de nombreux champs de différents types de données, notamment de texte, de nombre, de valeur booléenne, de date et d’heure.
      * Peut être utilisé pour préparer du contenu plus structuré en vue de la création de pages ou pour la diffusion sans interface dans votre application.
   * Imbriqué
      * Les types de données de référence disponibles vous permettent d’imbriquer votre contenu.
      * Tend à être utilisé pour la diffusion sans en-tête vers votre application.

Les fragments de contenu peuvent également être diffusés au format JSON, à l’aide des fonctionnalités d’exportation du modèle Sling (JSON) des composants principaux d’AEM. Cette forme de diffusion :

* permet d’utiliser le composant pour gérer les éléments d’un fragment à diffuser
* permet la diffusion en masse ; en ajoutant plusieurs [composants principaux de fragment de contenu](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html?lang=fr) sur la page utilisée pour la diffusion d’API ;

Le nombre de canaux de communication augmente tous les ans. En règle générale, les canaux font référence au mécanisme de diffusion :

* Canal physique (par exemple, bureau ou mobile).
* Forme de diffusion dans un canal physique (par exemple, la « page de détails du produit », la « page de catégorie de produit » pour le bureau, ou le « web mobile » et « l’application mobile » pour le mobile).

Cependant, vous ne souhaitez (probablement) pas utiliser le même contenu *exact* pour tous les canaux ; vous devez optimiser votre contenu en fonction du canal spécifique.

Les fragments de contenu vous permettent de :

* Étudier comment atteindre efficacement les audiences cibles sur plusieurs canaux.
* Créer et gérer du contenu éditorial neutre pour les canaux.
* Créer des pools de contenu pour divers canaux.
* Concevoir des variations de contenu pour des canaux spécifiques.
* Ajoutez des images à votre texte en insérant des ressources.
* Créez du contenu imbriqué pour refléter la complexité de vos données.

Ces fragments de contenu peuvent ensuite être assemblés afin de fournir des expériences sur divers canaux.

>[!NOTE]
>
>Les **fragments de contenu** et les **[fragments d’expérience](/help/sites-cloud/authoring/fragments/content-fragments.md)** représentent deux fonctions distinctes d’AEM :
>* Les **fragments de contenu** sont des contenus éditoriaux, avec définition et structure, mais sans conception visuelle et/ou mise en page supplémentaires. Ils peuvent être utilisés pour accéder à des données structurées, notamment du texte, des nombres et des dates.
>* Les **fragments d’expérience** désignent un contenu parfaitement mis en page : un fragment de page web.
>
>Les fragments d’expérience peuvent être composés de contenu sous la forme de fragments de contenu, mais pas l’inverse.
>
>Pour plus d’informations, voir [Présentation des fragments de contenu et d’expérience dans AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html?lang=fr#content-fragments).

Cette page et les suivantes portent sur les tâches de création, de configuration, de maintenance et d’utilisation de vos fragments de contenu :

* [Activation de la fonctionnalité de fragments de contenu pour votre instance](/help/sites-cloud/administering/content-fragments/setup.md)
* [Modèles de fragment de contenu](/help/sites-cloud/administering/content-fragments/content-fragment-models.md) : activation, création et définition de vos modèles.
* [Créez vos fragments de contenu](/help/sites-cloud/administering/content-fragments/managing.md#creating-a-content-fragment) (à l’aide de la console Fragment de contenu)

Une fois les fragments créés, vous pouvez :

* [Utilisez la console Fragments de contenu](/help/sites-cloud/administering/content-fragments/managing.md) pour accéder à vos fragments, les publier (pour les prévisualiser ou les produire) et les référencer.
* [Utilisez l’éditeur de fragments de contenu](/help/sites-cloud/administering/content-fragments/authoring.md) pour modifier, publier (pour prévisualiser ou produire) et référencer vos fragments.
* [Analyser](/help/sites-cloud/administering/content-fragments/analysis.md) la structure de votre fragment de contenu à l’aide de l’éditeur
* [Accédez à vos fragments avec GraphQL pour une diffusion sans en-tête vers vos applications](/help/sites-cloud/administering/content-fragments/content-delivery-with-graphql.md).
* [Ou utilisez vos fragments pour la création de pages](/help/sites-cloud/authoring/fragments/content-fragments.md)

>[!NOTE]
>
>Ces pages peuvent être lues avec :
>
>* [Personnalisation et extensions de fragments de contenu](/help/implementing/developing/extending/content-fragments-customizing.md)
>* [Fragments de contenu – Configuration des composants pour le rendu](/help/implementing/developing/extending/content-fragments-configuring-components-rendering.md)
>* [Prise en charge des fragments de contenu dans l’API HTTP AEM Assets](/help/assets/content-fragments/assets-api-content-fragments.md)
>* [API AEM GraphQL à utiliser avec les fragments de contenu](/help/headless/graphql-api/content-fragments.md)
>* [Création de page à partir de fragments de contenu](/help/sites-cloud/authoring/fragments/content-fragments.md).
>* Les [OpenAPI de modèle de fragment de contenu et de fragment de contenu](/help/headless/content-fragment-openapis.md) sont également disponibles.


## Principales et variations {#main-and-variations}

Les variations sont une fonctionnalité importante de l’AEM des fragments de contenu. Ils vous permettent de créer et de modifier des copies du contenu **Main** pour une utilisation sur des canaux spécifiques, ainsi que des scénarios, ce qui rend la diffusion de contenu sans interface utilisateur graphique et la création de pages encore plus flexible.

* **Principal**

   * **Main** n’est pas une variation en tant que telle, mais est la base de toutes les variations.
   * Partie intégrante du fragment

      * Chaque fragment de contenu possède une instance de **Main**.
      * **Main** ne peut pas être supprimé.

   * **Main** est accessible dans l’éditeur de fragments sous **[Variations](/help/sites-cloud/administering/content-fragments/authoring.md#variations)**.

  >[!NOTE]
  >
  >Dans l’éditeur disponible à partir de la console **Assets**, **Main** est étiqueté **Principal**.

* **Variations**

   * Il s’agit de rendus de texte de fragment spécifiques à fin éditoriale. Les variations peuvent être associées au canal, sans que cela soit obligatoire, et elles peuvent également servir à des modifications locales ad hoc.
   * Sont créées en tant que copies de **Main**, mais peuvent ensuite être modifiées si nécessaire ; il existe souvent un chevauchement de contenu entre les variations elles-mêmes.
   * Peuvent être définies lors de la création de fragments ; dans le panneau de gauche.
   * Stockées dans le fragment, afin d’éviter l’éparpillement des copies de contenu.
   * Les variations peuvent être [comparées et synchronisées](/help/sites-cloud/administering/content-fragments/authoring.md#compare-and-synchronize-rich-text) avec **Main**.
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

Associé aux fonctionnalités d’exportation JSON des composants de base AEM, ce contenu structuré peut ensuite être utilisé pour livrer le contenu AEM à des canaux autres que les pages AEM.

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

   * Les fragments de contenu (et leurs variations) peuvent être créés et conservés à partir de la [console Fragments de contenu](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console).
   * Créé et modifié dans l’ [ éditeur de fragments de contenu ](/help/sites-cloud/administering/content-fragments/authoring.md).

* Accessible pour la diffusion de contenu à l’aide de l’ [API GraphQL ](/help/headless/graphql-api/content-fragments.md) AEM.

* Disponible dans l’ [ éditeur de page à l’aide du composant Fragment de contenu](/help/sites-cloud/authoring/fragments/content-fragments.md) (référençant le composant) :

   * Le [composant principal de fragment de contenu](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html?lang=fr) est disponible pour les auteurs de pages. Il leur permet de référencer et de diffuser le fragment de contenu requis au format HTML ou JSON.

Les fragments de contenu sont une structure de contenu qui :

* Ne sont pas constitués d’une mise en page ou d’une conception (la mise en forme de texte est possible pour les champs de texte).
* sont indépendants du mécanisme de diffusion (par exemple, la page ou le canal) ;
* Contiennent une ou plusieurs [parties constituantes](#constituent-parts-of-a-content-fragment).
* Peuvent [contenir des images ou être connectés à celles-ci](#fragments-with-visual-assets).

### Fragments avec des ressources visuelles {#fragments-with-visual-assets}

Pour permettre aux auteurs de mieux contrôler leur contenu, les images peuvent être ajoutées et/ou intégrées à un fragment de contenu.

Assets peut être utilisé avec un fragment de contenu de plusieurs façons, chacune présentant ses propres avantages :

* en tant que **référence de contenu**
* dans un champ **texte multiligne**

### Parties constituantes d’un fragment de contenu {#constituent-parts-of-a-content-fragment}

Les ressources de fragment de contenu sont constituées des parties suivantes (directement ou indirectement) :

* **Éléments de fragment**

   * Les éléments sont corrélés aux champs de données contenant du contenu.
   * Vous utilisez un [modèle de fragment de contenu](/help/sites-cloud/administering/content-fragments/content-fragment-models.md) pour créer le fragment de contenu. Les éléments (champs) spécifiés dans le modèle définissent la structure du fragment. Ces éléments (champs) peuvent être de différents types de données.

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
  >Un modèle de fragment de contenu peut souvent définir des champs de données nommés **Title** et **Description**. Si ces deux champs existent, il s’agit de champs définis par l’utilisateur et ils peuvent être mis à jour dans la zone de contenu de l’éditeur.
  >
  >Le fragment de contenu, et ses variations, contient également des champs de métadonnées (propriété) appelés **Titre** et **Description**. Ces deux champs de métadonnées font partie intégrante d’un fragment de contenu et d’une variation, et sont initialement définis lors de la création du fragment. Ils peuvent être mis à jour dans la zone des propriétés/métadonnées de l’éditeur.

* **[Principal](#main-and-variations)**
* **[Variations](#main-and-variations)**

### Conditions requises pour utiliser des fragments {#required-by-fragments}

Pour créer des fragments de contenu, vous devez :

* **Modèles de contenu**

   * Sont [activés à l’aide de l’explorateur de configurations](/help/sites-cloud/administering/content-fragments/setup.md).
   * Sont [créés à l’aide d’outils](/help/sites-cloud/administering/content-fragments/content-fragment-models.md).
   * Obligatoires pour [créer un fragment](/help/sites-cloud/administering/content-fragments/managing.md#creating-content-fragments).
   * Définissent la structure d’un fragment (titre, éléments de contenu et définitions de balise).
   * Les définitions de modèle de fragment de contenu requièrent un titre et un élément de données ; tout le reste est facultatif.
   * Le modèle peut définir le contenu par défaut, le cas échéant.
   * Les auteurs ne peuvent pas modifier la structure définie lors de la création de contenu de fragment, bien qu’ils puissent ouvrir l’éditeur de modèles à partir de l’éditeur de fragments.
   * Les modifications apportées à un modèle après la création de fragments de contenu dépendants peuvent avoir une incidence sur ces fragments de contenu.

Pour utiliser vos fragments de contenu pour une diffusion de contenu sans interface utilisateur graphique, vous devez également :

* une [requête GraphQL](/help/headless/graphql-api/content-fragments.md) pour demander le contenu requis ;
* ce contenu peut ensuite être utilisé pour développer votre propre SPA pour AEM. pour plus d’informations, consultez les documents suivants :

   * [Tutoriel sur SPA WKND](/help/implementing/developing/hybrid/wknd-tutorial.md)
   * [Prise en main avec React](/help/implementing/developing/hybrid/getting-started-react.md)
   * [Prise en main avec Angular](/help/implementing/developing/hybrid/getting-started-angular.md)

Pour utiliser vos fragments de contenu pour la création de pages, vous avez également besoin des éléments suivants :

* Un **composant de fragment de contenu**

   * Utilitaire de diffusion du fragment au format HTML et/ou JSON.
   * Obligatoire pour [référencer le fragment sur une page](/help/sites-cloud/authoring/fragments/content-fragments.md).
   * Responsable de la mise en page et de la diffusion d’un fragment ; canaux, par exemple.
   * Les fragments ont besoin d’un ou de plusieurs composants dédiés pour définir la mise en page, ainsi que diffuser tous les éléments/variations et le contenu associé.
   * Faire glisser un fragment sur une page en mode Création permet d’associer automatiquement le composant requis.
   * Voir le [composant principal de fragment de contenu](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html?lang=fr).

## Exemple d’utilisation {#example-usage}

Un fragment, avec ses éléments et ses variations, peut être utilisé afin de créer du contenu homogène sur plusieurs canaux. Lors de la conception de votre fragment, vous devez tenir compte de ce qui sera utilisé et où.

### Exemple WKND {#wknd-sample}

Les exemples [WKND Site et WKND Shared](/help/implementing/developing/introduction/develop-wknd-tutorial.md) sont fournis pour vous aider à en savoir plus sur AEM as a Cloud Service.

<!-- CHECK: which links can/should be used these days? -->

Le projet WKND comprend :

* les modèles de fragments de contenu disponibles sous :

   * `.../libs/dam/cfm/models/console/content/models.html/conf/wknd`

   * `.../ui#/aem/libs/dam/cfm/models/console/content/models.html/conf/wknd-shared`

* les fragments de contenu (et autres contenus) disponibles sous :

   * `.../assets.html/content/dam/wknd/en`
