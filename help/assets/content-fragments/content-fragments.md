---
title: Utiliser des fragments de contenu (Assets - Fragments de contenu)
description: Découvrez comment les fragments de contenu dans Adobe Experience Manager (AEM) as a Cloud Service vous permettent de concevoir, créer, organiser et utiliser du contenu, idéal pour la création de pages et la diffusion découplée.
exl-id: db17eff1-4252-48d5-bb67-5e476e93ef7e
feature: Content Fragments
role: User
solution: Experience Manager Sites
source-git-commit: 2449bc380268ed42b6c8d23ae4a4fecaf1736889
workflow-type: tm+mt
source-wordcount: '2576'
ht-degree: 63%

---

# Utilisation de fragments de contenu {#working-with-content-fragments}

Avec Adobe Experience Manager (AEM) as a Cloud Service, les fragments de contenu vous permettent de concevoir, créer, organiser et [publier du contenu indépendant des pages](/help/sites-cloud/authoring/fragments/content-fragments.md). Ils vous permettent de préparer du contenu prêt à être utilisé à plusieurs emplacements ou sur plusieurs canaux, idéal pour une diffusion découplée. Ils peuvent également être utilisés avec la [gestion multisite pour vous permettre de réutiliser votre contenu](#reusing-content-fragments-with-msm).

Les fragments de contenu contiennent du contenu structuré :

* Ils sont basés sur un [modèle de fragment de contenu](/help/assets/content-fragments/content-fragments-models.md), servant à prédéfinir une structure pour le fragment résultant.
* La structure peut varier entre :
   * De base
      * Par exemple, un seul champ de texte multilignes.
      * Il peut être utilisé pour préparer du contenu simple à utiliser dans la création de pages.
   * Complexe
      * Combinaison de nombreux champs de divers types de données, y compris texte, nombre, booléen, données et temps.
      * Il peut être utilisé pour préparer du contenu plus structuré pour la création de pages ou pour le diffuser dans votre application.
   * Imbriqué
      * Les types de données de référence disponibles vous permettent d’imbriquer votre contenu.
      * Tend à être utilisé pour la diffusion à votre application.

Les fragments de contenu peuvent également être diffusés au format JSON, à l’aide des fonctionnalités d’exportation du modèle Sling (JSON) des composants principaux d’AEM. Cette forme de diffusion :

* permet d’utiliser le composant pour gérer les éléments d’un fragment à diffuser
* permet la diffusion en masse, en ajoutant plusieurs composants principaux de fragments de contenu sur la page utilisée pour la diffusion de l’API

>[!NOTE]
>
>Les fragments de contenu sont une fonctionnalité de sites, mais sont stockés sous la forme **Ressources**.
>
>Les fragments de contenu et les modèles de fragment de contenu sont désormais principalement gérés avec la console **[Fragments de contenu](/help/sites-cloud/administering/content-fragments/overview.md#content-fragments-console)**, bien que les fragments de contenu puissent toujours être gérés à partir de la console **Assets** et les modèles de fragment de contenu à partir de la console **Outils**. Cette section traite de la gestion à partir des consoles **Assets** et **Tools**.
>
>Il existe deux éditeurs pour créer des fragments de contenu ; bien que la fonctionnalité de base soit la même, il existe quelques différences. Cette section couvre l’éditeur d’origine, accessible principalement à partir de la console **Assets**. Voir la documentation Sites, [Fragments de contenu - Création](/help/sites-cloud/administering/content-fragments/authoring.md), pour plus d’informations sur le nouvel éditeur (principalement accessible à partir de la console **Fragments de contenu**). Les deux éditeurs comportent un bouton bascule dans la barre d’outils supérieure pour fournir un accès rapide à l’autre éditeur.

Cette page et les suivantes portent sur les tâches de création, de configuration, de gestion et d’utilisation de vos fragments de contenu :

* [Activation de la fonctionnalité de fragments de contenu pour votre instance](/help/assets/content-fragments/content-fragments-configuration-browser.md)
* [Modèles de fragment de contenu](/help/assets/content-fragments/content-fragments-models.md) : activation, création et définition de vos modèles.
* [Gérer les fragments de contenu](/help/assets/content-fragments/content-fragments-managing.md) - créer vos fragments de contenu ; puis modifier, publier et référencer
* [Variations – création de fragments de contenu](/help/assets/content-fragments/content-fragments-variations.md) : créez le contenu du fragment et créez des variantes du maître.
* [Texte (Markdown)](/help/assets/content-fragments/content-fragments-markdown.md) : utilisation de la syntaxe Markdown pour votre fragment.
* [Utilisation du contenu associé](/help/assets/content-fragments/content-fragments-assoc-content.md) : ajout de contenu associé.
* [Métadonnées – propriétés des fragments](/help/assets/content-fragments/content-fragments-metadata.md) : affichage et modification des propriétés des fragments.
* Utilisez [Fragments de contenu, avec GraphQL, afin de diffuser du contenu](/help/assets/content-fragments/content-fragments-graphql.md) pour l’utiliser dans vos applications. Pour vous aider, vous pouvez prévisualiser la [sortie JSON](/help/assets/content-fragments/content-fragments-json-preview.md).
* [Réutilisation de fragments de contenu à l’aide de MSM](#reusing-content-fragments-with-msm)

>[!NOTE]
>
>Ces pages peuvent être lues avec :
>
>* [Création de page à partir de fragments de contenu](/help/sites-cloud/authoring/fragments/content-fragments.md).
>* [Personnalisation et extensions de fragments de contenu](/help/implementing/developing/extending/content-fragments-customizing.md)
>* [Fragments de contenu – Configuration des composants pour le rendu](/help/implementing/developing/extending/content-fragments-configuring-components-rendering.md)
>* [Prise en charge des fragments de contenu dans l’API HTTP AEM Assets](/help/assets/content-fragments/assets-api-content-fragments.md)
>* [API AEM GraphQL à utiliser avec les fragments de contenu](/help/headless/graphql-api/content-fragments.md)
>* [API ouvertes de fragment de contenu et de modèle de fragment de contenu](/help/headless/content-fragment-openapis.md)

Le nombre de canaux de communication augmente tous les ans. En règle générale, les canaux font référence au mécanisme de diffusion :

* Canal physique (par exemple, bureau ou mobile).
* Forme de diffusion dans un canal physique (par exemple, la « page de détails du produit », la « page de catégorie de produit » pour le bureau, ou le « web mobile » et « l’application mobile » pour le mobile).

Cependant, vous ne souhaitez (probablement) pas utiliser le même contenu pour tous les canaux ; vous devez optimiser votre contenu en fonction du canal spécifique.

Les fragments de contenu vous permettent de :

* Étudier comment atteindre efficacement les audiences cibles sur plusieurs canaux.
* Créer et gérer du contenu éditorial neutre pour les canaux.
* Créer des pools de contenu pour divers canaux.
* Concevoir des variations de contenu pour des canaux spécifiques.
* Ajouter des images à votre texte en insérant des ressources (fragments de supports variés).
* Créez du contenu imbriqué pour refléter la complexité de vos données.

Ces fragments de contenu peuvent ensuite être assemblés pour offrir diverses expériences sur de multiples canaux.

>[!NOTE]
>
>Les **fragments de contenu** et les **[fragments d’expérience](/help/sites-cloud/authoring/fragments/content-fragments.md)** représentent deux fonctions distinctes d’AEM :
>
>* Les **fragments de contenu** sont des contenus éditoriaux, avec définition et structure, mais sans conception visuelle et/ou mise en page supplémentaires. Ils permettent d’accéder aux données structurées, notamment les textes, les nombres et les dates.
>* Les **fragments d’expérience** désignent un contenu parfaitement mis en page : un fragment de page web.
>
>Les fragments d’expérience peuvent être composés de contenu sous la forme de fragments de contenu, mais pas l’inverse.
>
>Pour plus d’informations, voir également [Présentation des fragments de contenu et d’expérience dans AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html?lang=fr#content-fragments).

## Fragments de contenu et Content Services {#content-fragments-and-content-services}

AEM Content Services est conçu pour généraliser la description et la diffusion de contenu dans/à partir d’AEM à des canaux autres que des pages web.

Il assure la diffusion du contenu aux canaux autres que les pages web AEM classiques, à l’aide de méthodes normalisées qui peuvent être utilisées par tous les clients. Ces canaux peuvent inclure :

* des applications sur une seule page ;
* des applications mobiles natives ;
* d’autres canaux et points de contact externes à AEM.

La diffusion est effectuée au format JSON à l’aide de l’outil d’exportation JSON.

Les fragments de contenu AEM peuvent être utilisés pour décrire et gérer du contenu structuré. Le contenu structuré est défini dans des modèles qui peuvent contenir divers types de contenu, notamment du texte, des données numériques, des valeurs booléennes, des dates et heures, etc.

Associé aux fonctionnalités d’exportation JSON des composants principaux AEM, ce contenu structuré peut ensuite être utilisé pour livrer le contenu AEM à des canaux autres que les pages AEM.

>[!NOTE]
>
>Consultez [Le découplage et AEM](/help/headless/introduction.md) pour une introduction au développement découplé pour AEM Sites as a Cloud Service.

>[!NOTE]
>
>AEM prend également en charge la traduction des fragments de contenu. Consultez [Traduction des actifs](/help/assets/translate-assets.md) pour plus d’informations.

## Type de contenu {#content-type}

Les fragments de contenu sont :

* stockés en tant que **ressources** :

   * Les fragments de contenu (et leurs variations) peuvent être créés et conservés à partir de la console **Ressources**.
   * Créés et modifiés dans l’éditeur de fragment de contenu.

* Utilisé dans l’[éditeur de page par le composant Fragment de contenu](/help/sites-cloud/authoring/fragments/content-fragments.md) (composant référençant) :

   * Le composant **Fragment de contenu** est disponible pour les créateurs de pages. Il leur permet de référencer et de livrer le fragment de contenu requis au format HTML ou JSON.

* Accessible à l’aide de l’[API AEM GraphQL](/help/headless/graphql-api/content-fragments.md).

Les fragments de contenu sont une structure de contenu qui :

* Ne comportent pas de disposition ou de conception (certaines mises en forme de texte sont possibles en mode Texte enrichi).
* Contiennent une ou plusieurs [parties constituantes](#constituent-parts-of-a-content-fragment).
* [contiennent des images ou peuvent être connectés à celles-ci](#fragments-with-visual-assets) ;
* Utilisé [contenu intermédiaire](#in-between-content-when-page-authoring-with-content-fragments) lorsqu’il est référencé sur une page.
* Ils sont indépendants du mécanisme de diffusion (c’est-à-dire de la page, du canal).

### Fragments avec des ressources visuelles {#fragments-with-visual-assets}

Pour donner aux auteurs et autrices plus de contrôle sur leur contenu, il est possible d’ajouter et/ou d’intégrer des images à un fragment de contenu.

Les ressources peuvent être utilisées avec un fragment de contenu de plusieurs façons ; chacune présentant ses propres avantages :

* **Insérer une ressource** dans un fragment (fragments de médias variés)

   * Ils font partie du fragment (voir [&#x200B; Parties constituantes d’un fragment de contenu &#x200B;](#constituent-parts-of-a-content-fragment)).
   * Définissent la position de la ressource.
   * Reportez-vous à la section [Insertion de ressources dans votre fragment](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment) dans l’éditeur de fragments pour plus d’informations.

  >[!NOTE]
  >
  >Les ressources visuelles insérées dans le fragment de contenu sont liées au paragraphe précédent. Lorsque le fragment est ajouté à une page, ces ressources sont déplacées avec le paragraphe en question quand du contenu intermédiaire est ajouté.

* **Contenu associé**

   * Connecté à un fragment ; mais pas une partie fixe du fragment (voir [&#x200B; Parties constituantes d’un fragment de contenu &#x200B;](#constituent-parts-of-a-content-fragment)).
   * Dispose d’une certaine flexibilité pour le positionnement.
   * Facilement disponible pour utilisation (comme contenu intermédiaire) lors de l’utilisation du fragment sur une page.

  Voir [Contenu associé](/help/assets/content-fragments/content-fragments-assoc-content.md) pour plus d’informations.

* Ressources disponibles dans le **navigateur Ressources** de l’éditeur de page

   * Permettent une flexibilité totale pour la sélection d’une ressource.
   * Dispose d’une certaine flexibilité pour le positionnement.
   * N’appliquent pas le concept d’approbation pour un fragment spécifique.

  Voir [Explorateur de ressources](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#assets-browser) pour plus d’informations.

### Parties constituantes d’un fragment de contenu {#constituent-parts-of-a-content-fragment}

Les ressources de fragment de contenu se composent des parties suivantes (directement ou indirectement) :

* **Éléments de fragment**

   * Les éléments sont corrélés aux champs de données contenant du contenu.
   * Vous utilisez un modèle de contenu pour créer le fragment de contenu. Les éléments (champs) spécifiés dans le modèle définissent la structure du fragment. Ces éléments (champs) peuvent être de différents types de données.

* **Paragraphes de fragment**

   * Blocs de texte, souvent multilignes, délimités en tant qu’entités individuelles.

   * Dans les modes [Texte enrichi](/help/assets/content-fragments/content-fragments-variations.md#rich-text) et [Markdown](/help/assets/content-fragments/content-fragments-variations.md#markdown), un paragraphe peut être formaté en tant qu’en-tête, auquel cas celui-ci et le paragraphe suivant sont considérés comme une unité.

   * Activez le contrôle du contenu lors de la création de pages.

* **Ressources insérées dans un fragment (fragments de supports variés)**

   * Ressources (images) insérées dans le fragment et utilisées en tant que contenu interne d’un fragment.
   * Incorporé dans le système de paragraphes du fragment.
   * Peuvent être formatées lorsque le [fragment est utilisé/référencé sur une page](/help/sites-cloud/authoring/fragments/content-fragments.md).
   * Peuvent uniquement être ajoutées, supprimées ou déplacées dans un fragment à l’aide de l’éditeur de fragment. Ces actions ne peuvent pas être effectuées dans l’éditeur de page.
   * Peuvent uniquement être ajoutées, supprimées ou déplacées dans un fragment à l’aide du [Format Texte enrichi dans l’éditeur de fragments](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment).
   * Peuvent uniquement être ajoutées aux éléments de texte multiligne (tout type de fragment).
   * Sont liées au texte précédent (paragraphe).

     >[!CAUTION]
     >
     >Des ressources peuvent être supprimées (par inadvertance) d’un fragment lors du passage au format texte brut.

     >[!NOTE]
     >
     >Assets peut également être ajouté en tant que contenu supplémentaire (intermédiaire) lors de l’utilisation d’un fragment sur une page ; à l’aide du [Contenu associé](/help/assets/content-fragments/content-fragments-assoc-content.md) ou des ressources du navigateur Assets.

* **Contenu associé**

   * Il s’agit d’un contenu externe à un fragment, mais présentant une pertinence éditoriale pour celui-ci. En règle générale, les images, vidéos ou autres fragments.
   * Les ressources individuelles de la collection peuvent être utilisées avec le fragment dans l’éditeur de page lorsqu’il est ajouté à une page. Cela signifie qu’elles sont facultatives, selon les exigences du canal spécifique.
   * Les ressources sont [associées aux fragments au moyen de collections](/help/assets/content-fragments/content-fragments-assoc-content.md) ; les collections associées permettent à l’auteur ou à l’autrice de décider quelles ressources utiliser lors de la création de la page.

      * Les collections peuvent être associées à des fragments, en tant que contenu par défaut, ou selon les auteurs lors de la création du fragment.
      * Les [Collections de ressources (DAM)](/help/assets/manage-collections.md) constituent la base du contenu associé des fragments.
   * Vous pouvez également ajouter le fragment lui-même à une collection pour faciliter le suivi.

* **Métadonnées de fragment**

   * Utilisez les [Schémas de métadonnées de ressources](/help/assets/metadata-schemas.md).
   * Les balises peuvent être créées lorsque vous :

      * Créez et êtes l’auteur ou l’autrice du fragment
      * Ou plus tard :

         * En affichant/modifiant les **Propriétés** du fragment depuis la console
         * En modifiant les **Métadonnées** dans l’éditeur de fragments

  >[!CAUTION]
  >
  >Les profils de traitement des métadonnées ne s’appliquent pas aux fragments de contenu.

* **Maître**

   * Partie du fragment

      * Chaque fragment de contenu comporte une instance de Principal.
      * Le Principal ne peut pas être supprimé.

   * L’instance maître est accessible dans l’éditeur de fragment sous **[Variations](/help/assets/content-fragments/content-fragments-variations.md)**.
   * L’instance maître n’est pas une variation en tant que telle, mais plutôt la base de toutes les variations.

* **Variations**

   * Il s’agit de rendus de texte de fragment spécifiques à une fin éditoriale. Les variations peuvent être associées au canal, sans que cela soit obligatoire, et elles peuvent également servir à des modifications locales ad hoc.
   * Ils sont créés en tant que copies de **Principal**, mais peuvent ensuite être modifiés selon les besoins. Il existe un chevauchement de contenu entre les variations elles-mêmes.
   * Peuvent être définies lors de la création de fragments.
   * Stockées dans le fragment, afin d’éviter l’éparpillement des copies de contenu.
   * Les variations peuvent être [synchronisées](/help/assets/content-fragments/content-fragments-variations.md#synchronizing-with-master) par Principal si le contenu du Principal a été mis à jour.
   * Peuvent être [résumées](/help/assets/content-fragments/content-fragments-variations.md#summarizing-text) afin de tronquer rapidement le texte sur une longueur prédéfinie.
   * Disponibles sous l’onglet [Variations](/help/assets/content-fragments/content-fragments-variations.md) de l’éditeur de fragment.

### Contenu intermédiaire lors de la création de page avec des fragments de contenu {#in-between-content-when-page-authoring-with-content-fragments}

Contenu intermédiaire :

* Disponible pour une utilisation dans l’éditeur de page lors de l’utilisation de fragments de contenu.
* [Contenu supplémentaire ajouté dans le flux d’un fragment](/help/sites-cloud/authoring/fragments/content-fragments.md#adding-in-between-content) après son utilisation ou son référencement sur une page.
* Disponible pour une utilisation dans l’[éditeur de page lors de l’utilisation de fragments de contenu](/help/sites-cloud/authoring/fragments/content-fragments.md).
* Le contenu intermédiaire peut être ajouté à n’importe quel fragment, où seul un élément est visible.
* Le contenu associé peut être utilisé, de même que les ressources et/ou les composants du navigateur approprié.

>[!CAUTION]
>
>Le contenu intermédiaire est du contenu de page. Il n’est pas stocké dans le fragment de contenu.

### Conditions requises pour utiliser des fragments {#required-by-fragments}

Pour créer des fragments de contenu, vous avez besoin des éléments suivants :

* **Modèles de contenu**

   * Sont [activés à l’aide de l’explorateur de configurations](/help/assets/content-fragments/content-fragments-configuration-browser.md).
   * Sont [créés à l’aide d’outils](/help/assets/content-fragments/content-fragments-models.md).
   * Obligatoires pour [créer un fragment](/help/assets/content-fragments/content-fragments-managing.md#creating-content-fragments).
   * Définissent la structure d’un fragment (titre, éléments de contenu et définitions de balise).
   * Les définitions de modèles de contenu requièrent un titre et un élément de données ; tous les autres attributs sont facultatifs.
   * Le modèle peut définir le contenu par défaut, le cas échéant.
   * Les auteurs ne peuvent pas modifier la structure définie lors de la création du contenu d’un fragment.
   * Les modifications apportées à un modèle après la création de fragments de contenu dépendants peuvent avoir un impact sur ces fragments de contenu.

Pour utiliser vos fragments de contenu pour la création de pages, vous avez également besoin des éléments suivants :

* **Composant Fragment de contenu**

   * Utilitaire de diffusion du fragment au format HTML ou JSON, ou les deux.
   * Obligatoire pour [référencer le fragment sur une page](/help/sites-cloud/authoring/fragments/content-fragments.md).
   * Responsable de la disposition et de la diffusion d’un fragment, c’est-à-dire des canaux.
   * Les fragments ont besoin d’un ou de plusieurs composants dédiés pour définir la disposition, ainsi que diffuser tous les éléments/variations et le contenu associé.
   * Faire glisser un fragment sur une page en mode Création permet d’associer automatiquement le composant requis.

## Réutilisation de fragments de contenu avec MSM {#reusing-content-fragments-with-msm}

Lors d’un accès via la console **Assets**, vous pouvez utiliser MSM et créer des Live Copies pour vos fragments.

Pour plus d’informations, consultez :

* [Réutilisation de fragments de contenu à l’aide de MSM](/help/assets/content-fragments/content-fragments-msm.md)
* [Réutilisation de ressources à l’aide de MSM pour Assets](/help/assets/reuse-assets-using-msm.md).

Ils activent l’[héritage](/help/assets/content-fragments/content-fragments-variations.md#inheritance) à la fois pour les variations et les champs individuels de vos fragments.

>[!CAUTION]
>
>Si vous souhaitez utiliser MSM (qui crée des copies de fragments de contenu), toute contrainte **unique** doit être supprimée de tous les types de données utilisés dans les [modèles de fragment de contenu](/help/assets/content-fragments/content-fragments-models.md) respectifs.

## Exemple d’utilisation {#example-usage}

Un fragment, avec ses éléments et ses variations, peut être utilisé afin de créer du contenu homogène sur plusieurs canaux. Lors de la conception de votre fragment, réfléchissez à ce qui est utilisé et où il est utilisé.

### Exemple WKND {#wknd-sample}

Les exemples du [site WKND](/help/implementing/developing/introduction/develop-wknd-tutorial.md) sont fournis pour vous aider à en savoir plus sur AEM as a Cloud Service.

Le projet WKND comprend :

* les modèles de fragments de contenu disponibles sous :
  `http://<hostname>:<port>/libs/dam/cfm/models/console/content/models.html/conf/wknd`

* les fragments de contenu (et autres contenus) disponibles sous :
  `http://<hostname>:<port>/assets.html/content/dam/wknd/en`

## Bonnes pratiques {#best-practices}

Les fragments de contenu peuvent être utilisés pour former des structures complexes. Adobe fournit des recommandations relatives aux bonnes pratiques à appliquer lors de la définition et de l’utilisation de modèles et de fragments.

### Restez simple {#keep-it-simple}

Lors de la modélisation de contenu structuré dans AEM, simplifiez au maximum les structures de contenu afin d’assurer des performances système solides et une gouvernance rationalisée.

### Nombre de modèles {#number-of-models}

Créez autant de modèles de contenu que nécessaire, mais pas plus.

Un nombre trop élevé de modèles complique la gouvernance et peut ralentir les requêtes GraphQL. Un petit ensemble de modèles, maximum de dizaines faibles, est généralement suffisant. Si vous approchez des dizaines élevées ou plus, reconsidérez votre stratégie de modélisation.

### Imbrication de modèles et de fragments (très important) {#nesting-models-and-fragments}

Évitez l’imbrication profonde ou excessive de fragments de contenu à l’aide des références de fragments de contenu, qui permettent aux fragments de référencer d’autres fragments, parfois sur plusieurs niveaux.

L’utilisation intensive des références de fragments de contenu peut avoir un impact significatif sur les performances du système, la réactivité de l’interface utilisateur et l’exécution des requêtes GraphQL. Visez à ne pas imbriquer plus de dix niveaux.

### Nombre de champs de données et de types par modèle {#number-of-data-fields-and-types-per-model}

Incluez uniquement les champs de données et les types dont un modèle a vraiment besoin.

Les modèles trop complexes génèrent des fragments trop complexes qui peuvent rendre la création difficile et réduire les performances de l’éditeur.

### Champs de texte enrichi {#rich-text-fields}

Utilisez les champs de texte enrichi (le **texte multiligne** type de données) avec précaution.

Limitez le nombre de champs de texte enrichi par modèle. La quantité de texte stockée dans chaque fragment et la quantité de mise en forme HTML. Un contenu de texte enrichi très volumineux peut nuire aux performances du système.

### Nombre de variations {#number-of-variations}

Créez autant de variations de fragment que nécessaire, mais pas plus.

Les variations ajoutent un temps de traitement à un fragment de contenu, dans l’environnement de création et lors de la diffusion également. Il est recommandé de maintenir le nombre de variations à un niveau minimal gérable.

Une bonne pratique consiste à ne pas dépasser dix variations par fragment de contenu.

### Test Avant Production {#test-before-production}

En cas de doute, prototypez les structures de contenu prévues avant de les déployer en production. Des preuves de concept précoces, associées à des tests adéquats, tant sur le plan technique que sur celui de l’acceptation par les utilisateurs, peuvent contribuer à éviter des problèmes ultérieurement, lorsque la production est soumise à des délais.
