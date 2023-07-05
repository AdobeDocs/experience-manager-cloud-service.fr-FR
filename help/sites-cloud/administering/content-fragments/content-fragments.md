---
title: Utiliser des fragments de contenu
description: Découvrez comment les fragments de contenu dans Adobe Experience Manager (AEM) as a Cloud Service vous permettent de concevoir, créer, organiser et utiliser du contenu indépendant des pages de façon idéale pour la création de pages et la diffusion découplée.
feature: Content Fragments
role: User
exl-id: d12b1dda-85ce-4665-b8b1-915b74231bb8
source-git-commit: a01583483fa89f89b60277c2ce4e1c440590e96c
workflow-type: tm+mt
source-wordcount: '2122'
ht-degree: 94%

---

# Utiliser des fragments de contenu {#working-with-content-fragments}

Avec Adobe Experience Manager (AEM) as a Cloud Service, les fragments de contenu vous permettent de concevoir, de créer, d’organiser et de [publier du contenu indépendant des pages](/help/sites-cloud/authoring/fundamentals/content-fragments.md). Ils vous permettent de préparer du contenu prêt à être utilisé à plusieurs emplacements ou sur plusieurs canaux, ce qui est idéal pour la création de pages et la diffusion découplée.

Les fragments de contenu contiennent du contenu structuré :

* Ils sont basés sur un [modèle de fragment de contenu](/help/sites-cloud/administering/content-fragments/content-fragments-models.md), servant à prédéfinir une structure pour le fragment résultant.
* La structure peut varier entre :
   * De base
      * Par exemple, un seul champ de texte multilignes.
      * Peut être utilisée pour préparer du contenu simple à utiliser pour la création de pages.
   * Complexe
      * Combinaison de nombreux champs de divers types de données, y compris texte, nombre, booléen, données et temps.
      * Peut être utilisée soit pour la préparation de contenu plus structuré pour la création de pages, soit pour la diffusion à votre application.
   * Imbriqué
      * Les types de données de référence disponibles vous permettent d’imbriquer votre contenu.
      * Tend à être utilisé pour la diffusion à votre application.

Les fragments de contenu peuvent également être diffusés au format JSON, à l’aide des fonctionnalités d’exportation du modèle Sling (JSON) des composants principaux d’AEM. Cette forme de diffusion :

* permet d’utiliser le composant pour gérer les éléments d’un fragment à diffuser
* permet la diffusion en masse, en ajoutant plusieurs composants principaux de fragments de contenu sur la page utilisée pour la diffusion de l’API

Cette page et les suivantes portent sur les tâches de création, de configuration, de gestion et d’utilisation de vos fragments de contenu :

* [Activation de la fonctionnalité de fragments de contenu pour votre instance](/help/sites-cloud/administering/content-fragments/content-fragments-configuration-browser.md)
* [Modèles de fragment de contenu](/help/sites-cloud/administering/content-fragments/content-fragments-models.md) : activation, création et définition de vos modèles.
* [Utiliser la console Fragments de contenu](/help/sites-cloud/administering/content-fragments/content-fragments-console.md) - pour accéder, créer, modifier, publier et référencer vos fragments
* [Gérer les fragments de contenu](/help/sites-cloud/administering/content-fragments/content-fragments-managing.md) - créer vos fragments de contenu ; puis modifier, publier et référencer
* [Variations – création de fragments de contenu](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md) : créez le contenu du fragment et créez des variantes du maître.
* [Texte (Markdown)](/help/sites-cloud/administering/content-fragments/content-fragments-markdown.md) : utilisation de la syntaxe Markdown pour votre fragment.
* [Utilisation du contenu associé](/help/sites-cloud/administering/content-fragments/content-fragments-assoc-content.md) : ajout de contenu associé.
* [Métadonnées – propriétés des fragments](/help/sites-cloud/administering/content-fragments/content-fragments-metadata.md) : affichage et modification des propriétés des fragments.
* Utilisez vos fragments de contenu :

   * [pour la création de pages](/help/sites-cloud/authoring/fundamentals/content-fragments.md)
   * [avec GraphQL, pour une diffusion découplée vers vos applications](/help/sites-cloud/administering/content-fragments/content-fragments-graphql.md).
Pour vous aider à faire cela, vous pouvez prévisualiser l’[Arborescence de structure](/help/sites-cloud/administering/content-fragments/content-fragments-structure-tree.md) et la [sortie JSON](/help/sites-cloud/administering/content-fragments/content-fragments-json-preview.md).

>[!NOTE]
>
>Ces pages peuvent être lues en lien avec :
>
>* [Création de page à partir de fragments de contenu](/help/sites-cloud/authoring/fundamentals/content-fragments.md).
>* [Personnalisation et extensions de fragments de contenu](/help/implementing/developing/extending/content-fragments-customizing.md)
>* [Fragments de contenu – Configuration des composants pour le rendu](/help/implementing/developing/extending/content-fragments-configuring-components-rendering.md)
>* [Prise en charge des fragments de contenu dans l’API HTTP AEM Assets](/help/assets/content-fragments/assets-api-content-fragments.md)
>* [API AEM GraphQL à utiliser avec les fragments de contenu](/help/headless/graphql-api/content-fragments.md)
>* [Réutilisation de fragments de contenu à l’aide de MSM pour Assets](/help/assets/reuse-assets-using-msm.md) (disponible uniquement via le **Ressources** console)

Le nombre de canaux de communication augmente tous les ans. En règle générale, les canaux font référence au mécanisme de diffusion :

* Canal physique (par exemple, bureau ou mobile).
* Forme de diffusion dans un canal physique (par exemple, la « page de détails du produit », la « page de catégorie de produit » pour le bureau, ou le « web mobile » et « l’application mobile » pour le mobile).

Cependant, vous ne souhaitez (probablement) pas utiliser exactement le même contenu pour tous les canaux ; vous devez optimiser votre contenu en fonction du canal spécifique.

Les fragments de contenu permettent :

* Étudier comment atteindre efficacement les audiences cibles sur plusieurs canaux.
* Créer et gérer du contenu éditorial neutre pour les canaux.
* Créer des pools de contenu pour divers canaux.
* Concevoir des variations de contenu pour des canaux spécifiques.
* Ajouter des images à votre texte en insérant des ressources (fragments de supports variés).
* Créez du contenu imbriqué pour refléter la complexité de vos données.

Ces fragments de contenu peuvent ensuite être assemblés pour offrir diverses expériences sur de multiples canaux.

>[!NOTE]
>
>Les **fragments de contenu** et les **[fragments d’expérience](/help/sites-cloud/authoring/fundamentals/experience-fragments.md)** représentent deux fonctions distinctes d’AEM :
>* Les **fragments de contenu** sont des contenus éditoriaux, avec définition et structure, mais sans conception visuelle et/ou mise en page supplémentaires. Ils permettent d’accéder aux données structurées telles que les textes, les nombres et les dates, entre autres.
>* Les **fragments d’expérience** désignent un contenu parfaitement mis en page : un fragment de page web.
>
>Les fragments d’expérience peuvent être composés de contenu sous la forme de fragments de contenu, mais pas l’inverse.
>
>Pour plus d’informations, voir [Présentation des fragments de contenu et des fragments d’expérience dans AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html?lang=fr#content-fragments).

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

## Publication et aperçu {#publish-and-preview}

Comme pour tout le contenu, vous voudrez éventuellement publier vos fragments de contenu dans le **[Service de publication](/help/overview/architecture.md#runtime-architecture)**.

Avant cela, vous pouvez également prévisualiser une expérience diffusée à l’aide de fragments de contenu en [publication de fragments de contenu](/help/sites-cloud/administering/content-fragments/content-fragments-managing.md##publishing-and-previewing-a-fragment) à l’AEM **[Service de prévisualisation](/help/overview/architecture.md#runtime-architecture)**.

>[!CAUTION]
>
>Publication sur le **Service de prévisualisation** n’est disponible que depuis le **Fragments de contenu** console.

## Type de contenu {#content-type}

Les fragments de contenu sont :

* Une fonctionnalité **Sites**.

* Stockés en tant que **ressources** :

   * Les fragments de contenu (et leurs variantes) peuvent être créés et conservés à partir des consoles **Fragments de contenu** et **Ressources**.
   * Créés et modifiés dans l’éditeur de fragment de contenu.

* Utilisés dans l’[éditeur de page au moyen du composant Fragment de contenu](/help/sites-cloud/authoring/fundamentals/content-fragments.md) (qui fait référence au composant) :

   * Le composant **Fragment de contenu** est disponible pour les créateurs de pages. Il leur permet de référencer et de livrer le fragment de contenu requis au format HTML ou JSON.

* Accessible à l’aide de l’[API AEM GraphQL](/help/headless/graphql-api/content-fragments.md).

Les fragments de contenu sont une structure de contenu qui :

* Ne comportent pas de mise en page ou de conception (certaines mises en forme de texte sont possibles en mode Texte enrichi).
* Contiennent une ou plusieurs [parties constituantes](#constituent-parts-of-a-content-fragment).
* Peuvent [contenir des images ou être connectés à celles-ci](#fragments-with-visual-assets).
* peut utiliser du [contenu intermédiaire](#in-between-content-when-page-authoring-with-content-fragments) en cas de référencement sur une page ;

* sont indépendants du mécanisme de diffusion (c’est-à-dire de la page, du canal) ;

### Fragments avec des ressources visuelles {#fragments-with-visual-assets}

Pour donner aux auteurs plus de contrôle sur leur contenu, il est possible d’ajouter et/ou d’intégrer des images à un fragment de contenu.

Les ressources peuvent être utilisées avec un fragment de contenu de plusieurs façons ; chacune présentant ses propres avantages :

* **Insérer une ressource** dans un fragment (fragments de supports variés)

   * Font partie intégrante du fragment (voir [Parties constituantes d’un fragment de contenu](#constituent-parts-of-a-content-fragment)).
   * Définissent la position de la ressource.
   * Reportez-vous à la section [Insertion de ressources dans votre fragment](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment) dans l’éditeur de fragments pour plus d’informations.

  >[!NOTE]
  >
  >Les ressources visuelles insérées dans le fragment de contenu sont liées au paragraphe précédent. Lorsque le fragment est ajouté à une page, ces ressources sont déplacées avec le paragraphe en question lorsque du contenu intermédiaire est ajouté.

* **Contenu associé**

   * Sont connectés à un fragment ; mais pas une partie fixe du fragment (voir [Parties constituantes d’un fragment de contenu](#constituent-parts-of-a-content-fragment)).
   * Permettent une certaine souplesse de positionnement.
   * Sont facilement disponibles pour utilisation (comme contenu intermédiaire) lors de l’utilisation du fragment sur une page.
   * Voir [Contenu associé](/help/sites-cloud/administering/content-fragments/content-fragments-assoc-content.md) pour plus d’informations.

* Ressources disponibles dans le **navigateur Ressources** de l’éditeur de page

   * Permettent une flexibilité totale pour la sélection d’une ressource.
   * Permettent une certaine souplesse de positionnement.
   * N’appliquent pas le concept d’approbation pour un fragment spécifique.
   * Voir [Explorateur de ressources](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser) pour plus d’informations.

### Parties constituantes d’un fragment de contenu {#constituent-parts-of-a-content-fragment}

Les ressources de fragment de contenu se composent des parties suivantes (directement ou indirectement) :

* **Éléments de fragment**

   * Les éléments sont corrélés aux champs de données contenant du contenu.
   * Vous utilisez un modèle de contenu pour créer le fragment de contenu. Les éléments (champs) spécifiés dans le modèle définissent la structure du fragment. Ces éléments (champs) peuvent être de différents types de données.

* **Paragraphes de fragment**

   * Blocs de texte, souvent multilignes, délimités comme des entités individuelles.

   * Dans les modes [Texte enrichi](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md#rich-text) et [Markdown](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md#markdown), un paragraphe peut être formaté en tant qu’en-tête, auquel cas celui-ci et le paragraphe suivant sont considérés comme une unité.

   * Activez le contrôle du contenu lors de la création de pages.

* **Ressources insérées dans un fragment (fragments de supports variés)**

   * Ressources (images) insérées dans le fragment et utilisées en tant que contenu interne d’un fragment.
   * Sont intégrées dans le système de paragraphe du fragment.
   * Peuvent être formatées lorsque le [fragment est utilisé/référencé sur une page](/help/sites-cloud/authoring/fundamentals/content-fragments.md).
   * Peuvent uniquement être ajoutées, supprimées ou déplacées dans un fragment à l’aide de l’éditeur de fragment. Ces actions ne peuvent pas être effectuées dans l’éditeur de page.
   * Peuvent uniquement être ajoutées, supprimées ou déplacées dans un fragment à l’aide du [Format Texte enrichi dans l’éditeur de fragments](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment).
   * Peuvent uniquement être ajoutées aux éléments de texte multiligne (tout type de fragment).
   * Sont liées au texte précédent (paragraphe).

     >[!CAUTION]
     >
     >Des ressources peuvent être supprimées (par inadvertance) d’un fragment lors du passage au format texte brut.

     >[!NOTE]
     >
     >Les ressources peuvent également être ajoutées en tant que [contenu supplémentaire (intermédiaire)](/help/sites-cloud/authoring/fundamentals/content-fragments.md#using-associated-content) lors de l’utilisation d’un fragment sur une page ; à l’aide du contenu associé ou des ressources de l’explorateur de ressources.

* **Contenu associé**

   * Il s’agit d’un contenu externe à un fragment, mais présentant une pertinence éditoriale pour celui-ci. En règle générale, les images, vidéos ou autres fragments.
   * Les ressources individuelles de la collection peuvent être utilisées avec le fragment dans l’éditeur de page lorsqu’il est ajouté à une page. Cela signifie qu’elles sont facultatives, selon les exigences du canal spécifique.
   * Les ressources sont [associées aux fragments via des collections](/help/sites-cloud/administering/content-fragments/content-fragments-assoc-content.md) ; les collections associées permettent à l’auteur de déterminer les ressources à utiliser lors de la création d’une page.

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

   * Partie intégrante du fragment

      * Chaque fragment de contenu comporte une instance de Principal.
      * Le Principal ne peut pas être supprimé.

   * L’instance maître est accessible dans l’éditeur de fragment sous **[Variations](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md)**.
   * L’instance maître n’est pas une variation en tant que telle, mais plutôt la base de toutes les variations.

* **Variations**

   * Il s’agit de rendus de texte de fragment spécifiques à fin éditoriale. Les variations peuvent être associées au canal, sans que cela soit obligatoire, et elles peuvent également servir à des modifications locales ad hoc.
   * Sont créées en tant que copies de l’instance **maître**, mais peuvent ensuite être modifiées si besoin. Il existe généralement un chevauchement de contenu entre les différentes variations.
   * Peuvent être définies lors de la création de fragments.
   * Stockées dans le fragment, afin d’éviter l’éparpillement des copies de contenu.
   * Les variations peuvent être [synchronisées](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md#synchronizing-with-master) par Principal si le contenu du Principal a été mis à jour.
   * Peuvent être [résumées](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md#summarizing-text) afin de tronquer rapidement le texte sur une longueur prédéfinie.
   * Disponibles sous l’onglet [Variations](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md) de l’éditeur de fragment.

### Contenu intermédiaire lors de la création de page avec des fragments de contenu {#in-between-content-when-page-authoring-with-content-fragments}

Contenu intermédiaire :

* Il est disponible dans l’éditeur de page lorsque vous utilisez des fragments de contenu.
* Il s’agit de [contenu supplémentaire ajouté dans le flux d’un fragment](/help/sites-cloud/authoring/fundamentals/content-fragments.md#adding-in-between-content) une fois qu’il a été utilisé ou référencé sur une page.
* Il est disponible dans l’[éditeur de page lorsque vous utilisez des fragments de contenu](/help/sites-cloud/authoring/fundamentals/content-fragments.md).
* Le contenu intermédiaire peut être ajouté à n’importe quel fragment, où seul un élément est visible.
* Le contenu associé peut être utilisé, de même que les ressources et/ou les composants du navigateur approprié.

>[!CAUTION]
>
>Le contenu intermédiaire est du contenu de page. Il n’est pas stocké dans le fragment de contenu.

### Conditions requises pour utiliser des fragments {#required-by-fragments}

Pour créer des fragments de contenu, vous devez disposer des éléments suivants :

* **Modèles de contenu**

   * Sont [activés à l’aide de l’explorateur de configurations](/help/sites-cloud/administering/content-fragments/content-fragments-configuration-browser.md).
   * Sont [créés à l’aide d’outils](/help/sites-cloud/administering/content-fragments/content-fragments-models.md).
   * Obligatoires pour [créer un fragment](/help/sites-cloud/administering/content-fragments/content-fragments-managing.md#creating-content-fragments).
   * Définissent la structure d’un fragment (titre, éléments de contenu et définitions de balise).
   * Les définitions de modèles de contenu requièrent un titre et un élément de données ; tous les autres attributs sont facultatifs.
   * Le modèle peut définir le contenu par défaut, le cas échéant.
   * Les auteurs ne peuvent pas modifier la structure définie lors de la création du contenu d’un fragment.
   * Les modifications apportées à un modèle après la création de fragments de contenu dépendants peuvent avoir un impact sur ces fragments de contenu.

Pour utiliser vos fragments de contenu pour la création de pages, vous avez également besoin des éléments suivants :

* **Composant de fragment de contenu**

   * Utilitaire de diffusion du fragment au format HTML et/ou JSON.
   * Obligatoire pour [référencer le fragment sur une page](/help/sites-cloud/authoring/fundamentals/content-fragments.md).
   * responsable de la mise en page et de la diffusion d’un fragment ; c&#39;est-à-dire les canaux.
   * Les fragments ont besoin d’un ou de plusieurs composants dédiés pour définir la mise en page, ainsi que diffuser tous les éléments/variations et le contenu associé.
   * Faire glisser un fragment sur une page en mode Création permet d’associer automatiquement le composant requis.

## Exemple d’utilisation {#example-usage}

Un fragment, avec ses éléments et ses variations, peut être utilisé afin de créer du contenu homogène sur plusieurs canaux. Lors de la conception de votre fragment, tenez compte de l’emplacement utilisé.

### Exemple WKND {#wknd-sample}

Les exemples du [site WKND](/help/implementing/developing/introduction/develop-wknd-tutorial.md) sont fournis pour vous aider à en savoir plus sur AEM as a Cloud Service.

Le projet WKND comprend :

* les modèles de fragments de contenu disponibles sous :
  `http://<hostname>:<port>/libs/dam/cfm/models/console/content/models.html/conf/wknd`

* les fragments de contenu (et autres contenus) disponibles sous :
  `http://<hostname>:<port>/assets.html/content/dam/wknd/en`
