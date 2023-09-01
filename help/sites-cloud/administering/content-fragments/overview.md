---
title: Présentation de l’utilisation des fragments de contenu
description: Découvrez comment les fragments de contenu dans Adobe Experience Manager (AEM) as a Cloud Service vous permettent de concevoir, créer, organiser et utiliser du contenu indépendant des pages, idéal pour une diffusion sans en-tête et la création de pages.
feature: Content Fragments
role: User, Developer, Architect
source-git-commit: 3d20f4bca566edcdb5f13eab581c33b7f3cf286d
workflow-type: tm+mt
source-wordcount: '1823'
ht-degree: 40%

---


# Présentation de l’utilisation des fragments de contenu {#overview-working-with-content-fragments}

Avec Adobe Experience Manager (AEM) as a Cloud Service, les fragments de contenu vous permettent de concevoir, créer, organiser et [publier du contenu indépendant des pages](/help/sites-cloud/authoring/fundamentals/content-fragments.md). Ils vous permettent de préparer du contenu prêt à être utilisé à plusieurs emplacements et sur plusieurs canaux, idéal pour une diffusion sans interface et la création de pages.

>[!IMPORTANT]
>
>Les fragments de contenu sont accessibles à partir de deux consoles : **Fragments de contenu** et **Ressources**.
>
>Deux éditeurs sont également disponibles pour les fragments de contenu. (Les deux éditeurs sont accessibles à partir des deux consoles.)
>
>Cette section traite de la **Fragments de contenu** et la console *new* Éditeur de fragment de contenu. Ils ont été développés pour la diffusion de contenu sans interface utilisateur graphique (bien qu’ils puissent être utilisés pour tous les scénarios).
>
>Pour plus d’informations, consultez :
>
>* l’utilisation de la fonction **Ressources** console pour [gestion des fragments de contenu](/help/assets/content-fragments/content-fragments-managing.md)
>* l’utilisation de la fonction [*original* Éditeur de fragment de contenu](/help/assets/content-fragments/content-fragments-variations.md),
>* using [Fragments de contenu pour la création de pages](/help/sites-cloud/authoring/fundamentals/content-fragments.md).


Les fragments de contenu contiennent du contenu structuré :

* Chaque fragment est basé sur une [Modèle de fragment de contenu](/help/sites-cloud/administering/content-fragments/content-fragment-models.md).
   * Le modèle de fragment de contenu définit la structure du fragment résultant.
* Chaque fragment se compose des éléments suivants :
   * **[Principal](#main-and-variations)** : partie intégrante du fragment qui contient le contenu principal ; existe toujours, ne peut pas être supprimé
   * **[Variations](#main-and-variations)** - une ou plusieurs permutations du contenu, créées par l’auteur
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
* permet la diffusion en masse ; en ajoutant plusieurs [Composants principaux des fragments de contenu](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html?lang=fr) sur la page utilisée pour la diffusion de l’API

Le nombre de canaux de communication augmente tous les ans. En règle générale, les canaux font référence au mécanisme de diffusion :

* Canal physique (par exemple, bureau ou mobile).
* Forme de diffusion dans un canal physique (par exemple, la « page de détails du produit », la « page de catégorie de produit » pour le bureau, ou le « web mobile » et « l’application mobile » pour le mobile).

Cependant, vous ne souhaitez (probablement) pas utiliser la variable *exact* même contenu pour tous les canaux ; vous devez optimiser votre contenu en fonction du canal spécifique.

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
>Les **fragments de contenu** et les **[fragments d’expérience](/help/sites-cloud/authoring/fundamentals/experience-fragments.md)** représentent deux fonctions distinctes d’AEM :
>* Les **fragments de contenu** sont des contenus éditoriaux, avec définition et structure, mais sans conception visuelle et/ou mise en page supplémentaires. Ils peuvent être utilisés pour accéder à des données structurées, notamment du texte, des nombres et des dates.
>* Les **fragments d’expérience** désignent un contenu parfaitement mis en page : un fragment de page web.
>
>Les fragments d’expérience peuvent être composés de contenu sous la forme de fragments de contenu, mais pas l’inverse.
>
>Pour plus d’informations, voir [Présentation des fragments de contenu et des fragments d’expérience dans AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html?lang=fr#content-fragments).

Cette page et les suivantes portent sur les tâches de création, de configuration, de maintenance et d’utilisation de vos fragments de contenu :

* [Activation de la fonctionnalité de fragments de contenu pour votre instance](/help/sites-cloud/administering/content-fragments/setup.md)
* [Modèles de fragment de contenu](/help/sites-cloud/administering/content-fragments/content-fragment-models.md) - activation, création et définition de vos modèles
* [Création de fragments de contenu](/help/sites-cloud/administering/content-fragments/managing.md#creating-a-content-fragment) (à l’aide de la console de fragments de contenu)

Une fois les fragments créés, vous pouvez :

* [Utilisation de la console Fragments de contenu](/help/sites-cloud/administering/content-fragments/managing.md) - pour accéder à vos fragments, les publier (pour les prévisualiser ou les produire) et les référencer
* [Utilisation de l’éditeur de fragments de contenu](/help/sites-cloud/administering/content-fragments/authoring.md) - pour modifier, publier (pour prévisualiser ou produire) et référencer vos fragments
* [Analyser](/help/sites-cloud/administering/content-fragments/analysis.md)  la structure de votre fragment de contenu, à l’aide de l’éditeur ;
* [Accédez à vos fragments avec GraphQL pour une diffusion sans en-tête vers vos applications.](/help/sites-cloud/administering/content-fragments/content-delivery-with-graphql.md).
* [Ou utilisez vos fragments pour la création de pages](/help/sites-cloud/authoring/fundamentals/content-fragments.md)

>[!NOTE]
>
>Ces pages peuvent être lues avec :
>
>* [Personnalisation et extensions de fragments de contenu](/help/implementing/developing/extending/content-fragments-customizing.md)
>* [Fragments de contenu – Configuration des composants pour le rendu](/help/implementing/developing/extending/content-fragments-configuring-components-rendering.md)
>* [Prise en charge des fragments de contenu dans l’API HTTP AEM Assets](/help/assets/content-fragments/assets-api-content-fragments.md)
>* [API AEM GraphQL à utiliser avec les fragments de contenu](/help/headless/graphql-api/content-fragments.md)
>* [Création de page à partir de fragments de contenu](/help/sites-cloud/authoring/fundamentals/content-fragments.md).

## Principales et variations {#main-and-variations}

Les variations sont une caractéristique importante des fragments de contenu AEM. Ils vous permettent de créer et de modifier des copies de la **Principal** contenu à utiliser sur des canaux et des scénarios spécifiques, ce qui rend la diffusion de contenu sans interface utilisateur et la création de pages encore plus flexible.

* **Principal**

   * **Principal** n’est pas une variation en tant que telle, mais est la base de toutes les variations.
   * Partie intégrante du fragment

      * Chaque fragment de contenu comporte une instance de **Principal**.
      * **Principal** ne peut pas être supprimé.

   * **Principal** est accessible dans l’éditeur de fragments sous **[Variations](/help/sites-cloud/administering/content-fragments/authoring.md#variations)**.

  >[!NOTE]
  >
  >Dans l’éditeur disponible à partir du **Ressources** console, **Principal** est étiqueté comme **Principal**.

* **Variations**

   * Il s’agit de rendus de texte de fragment spécifiques à fin éditoriale. Les variations peuvent être associées au canal, sans que cela soit obligatoire, et elles peuvent également servir à des modifications locales ad hoc.
   * sont créés en tant que copies de **Principal**, mais peuvent ensuite être modifiées si nécessaire ; il existe souvent un chevauchement de contenu entre les variations elles-mêmes.
   * Peuvent être définies lors de la création de fragments ; dans le panneau de gauche.
   * Stockées dans le fragment, afin d’éviter l’éparpillement des copies de contenu.
   * Les variations peuvent être [comparé et synchronisé](/help/sites-cloud/administering/content-fragments/authoring.md#compare-and-synchronize-rich-text) avec **Principal**.
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

   * Les fragments de contenu (et leurs variations) peuvent être créés et conservés à partir de la fonction [Console Fragments de contenu](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console).
   * Créé et modifié dans [Éditeur de fragment de contenu](/help/sites-cloud/administering/content-fragments/authoring.md).

* Accessible pour la diffusion de contenu à l’aide du [API GRAPHQL AEM](/help/headless/graphql-api/content-fragments.md).

* Disponible dans le [éditeur de page à l’aide du composant Fragment de contenu](/help/sites-cloud/authoring/fundamentals/content-fragments.md) (composant de référencement) :

   * La variable [Composant principal de fragment de contenu](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html?lang=fr) est disponible pour les auteurs de pages. Il leur permet de référencer et de diffuser le fragment de contenu requis au format HTML ou JSON.

Les fragments de contenu sont une structure de contenu qui :

* Ne sont pas constitués d’une mise en page ou d’une conception (la mise en forme de texte est possible pour les champs de texte).
* sont indépendants du mécanisme de diffusion (par exemple, la page ou le canal) ;
* Contiennent une ou plusieurs [parties constituantes](#constituent-parts-of-a-content-fragment).
* Peuvent [contenir des images ou être connectés à celles-ci](#fragments-with-visual-assets).

### Fragments avec des ressources visuelles {#fragments-with-visual-assets}

Pour permettre aux auteurs de mieux contrôler leur contenu, les images peuvent être ajoutées et/ou intégrées à un fragment de contenu.

Les ressources peuvent être utilisées avec un fragment de contenu de plusieurs façons, chacune présentant ses propres avantages :

* as a **Référence de contenu**
* dans **Texte multi-lignes** field

### Parties constituantes d’un fragment de contenu {#constituent-parts-of-a-content-fragment}

Les ressources de fragment de contenu sont constituées des parties suivantes (directement ou indirectement) :

* **Éléments de fragment**

   * Les éléments sont corrélés aux champs de données contenant du contenu.
   * Vous utilisez une [Modèle de fragment de contenu](/help/sites-cloud/administering/content-fragments/content-fragment-models.md) pour créer le fragment de contenu. Les éléments (champs) spécifiés dans le modèle définissent la structure du fragment. Ces éléments (champs) peuvent être de différents types de données.

* **Paragraphes de fragment**

   * Blocs de texte, souvent multilignes, délimités en tant qu’entités individuelles.

   * Activez le contrôle du contenu lors de la création de pages.

* **Métadonnées de fragment**

   * Utilisez les [Schémas de métadonnées de ressources](/help/assets/metadata-schemas.md).
   * Les balises peuvent être créées lorsque vous :

      * Créez et êtes l’auteur ou l’autrice du fragment
      * Ou plus tard, lorsque vous [afficher ou modifier les propriétés ;](/help/sites-cloud/administering/content-fragments/authoring.md#view-properties-tags) dans l’éditeur de fragments

  >[!CAUTION]
  >
  >Les profils de traitement des métadonnées ne s’appliquent pas aux fragments de contenu.

  >[!CAUTION]
  >
  >Un modèle de fragment de contenu peut souvent définir des champs de données nommés **Titre** et **Description**. Si ces deux champs existent, il s’agit de champs définis par l’utilisateur et ils peuvent être mis à jour dans la zone de contenu de l’éditeur.
  >
  >Le fragment de contenu et ses variations comportent également des champs de métadonnées (propriété) appelés **Titre** et **Description**. Ces deux champs de métadonnées font partie intégrante d’un fragment de contenu et d’une variation, et sont initialement définis lors de la création du fragment. Ils peuvent être mis à jour dans la zone des propriétés/métadonnées de l’éditeur.

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

* a [Requête GraphQL](/help/headless/graphql-api/content-fragments.md) pour demander le contenu requis
* ce contenu peut ensuite être utilisé pour développer votre propre SPA pour AEM. pour plus d’informations, consultez les documents suivants :

   * [Tutoriel sur SPA WKND](/help/implementing/developing/hybrid/wknd-tutorial.md)
   * [Prise en main avec React](/help/implementing/developing/hybrid/getting-started-react.md)
   * [Prise en main avec Angular](/help/implementing/developing/hybrid/getting-started-angular.md)

Pour utiliser vos fragments de contenu pour la création de pages, vous avez également besoin des éléments suivants :

* A **Composant de fragment de contenu**

   * Utilitaire de diffusion du fragment au format HTML et/ou JSON.
   * Obligatoire pour [référencer le fragment sur une page](/help/sites-cloud/authoring/fundamentals/content-fragments.md).
   * Responsable de la mise en page et de la diffusion d’un fragment ; canaux, par exemple.
   * Les fragments ont besoin d’un ou de plusieurs composants dédiés pour définir la mise en page, ainsi que diffuser tous les éléments/variations et le contenu associé.
   * Le fait de faire glisser un fragment sur une page dans la création associe automatiquement le composant requis.
   * Voir [Composant principal de fragment de contenu](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html?lang=fr).

## Exemple d’utilisation {#example-usage}

Un fragment, avec ses éléments et ses variations, peut être utilisé afin de créer du contenu homogène sur plusieurs canaux. Lors de la conception de votre fragment, vous devez tenir compte de ce qui sera utilisé et où.

### Exemple WKND {#wknd-sample}

La variable [Site WKND et WKND partagé](/help/implementing/developing/introduction/develop-wknd-tutorial.md) des exemples sont fournis pour vous aider à en savoir plus sur AEM as a Cloud Service.

<!-- CHECK: which links can/should be used these days? -->

Le projet WKND comprend :

* les modèles de fragments de contenu disponibles sous :

   * `.../libs/dam/cfm/models/console/content/models.html/conf/wknd`

   * `.../ui#/aem/libs/dam/cfm/models/console/content/models.html/conf/wknd-shared`

* les fragments de contenu (et autres contenus) disponibles sous :

   * `.../assets.html/content/dam/wknd/en`
