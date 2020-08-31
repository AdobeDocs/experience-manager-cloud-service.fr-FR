---
title: Développement d’applications monopages pour AEM
description: Cet article présente des questions importantes à prendre en compte lorsqu'un développeur frontal développe un SPA pour AEM et donne un aperçu de l'architecture des AEM par rapport aux SPA à garder à l'esprit lors du déploiement d'un SPA développé sur les .
translation-type: tm+mt
source-git-commit: d0685af8b05d5491debf7bad99b5c8f111808f26
workflow-type: tm+mt
source-wordcount: '2088'
ht-degree: 2%

---


# Développement d’applications monopages pour AEM {#developing-spas-for-aem}

Les applications d’une seule page (SPA) peuvent améliorer considérablement l’expérience des utilisateurs de sites web. Le souhait des développeurs est de pouvoir créer des sites avec des structures SPA. Les auteurs, pour leur part, souhaitent modifier facilement du contenu dans AEM pour un site conçu à l’aide de telles structures.

Cet article présente des questions importantes à prendre en compte lorsqu’un développeur frontal est invité à développer une application d’une seule page pour l’AEM et donne un aperçu de l’architecture de l’AEM en ce qui concerne le déploiement d’applications d’une seule page sur l’AEM.

## Principes de développement des ZPS pour les AEM {#spa-development-principles-for-aem}

Le développement d’applications d’une seule page sur AEM suppose que le développeur principal respecte les meilleures pratiques standard lors de la création d’une application d’une seule page. Si en tant que développeur frontal vous suivez ces bonnes pratiques générales ainsi que quelques principes AEM spécifiques, votre application d’une seule page sera fonctionnelle avec [AEM et ses capacités](introduction.md#content-editing-experience-with-spa)de création de contenu.

* **[Portabilité](#portability)** - Comme pour tout composant, les composants doivent être construits pour être aussi portables que possible. L’application d’une seule page doit être construite avec des composants portatifs et réutilisables.
* **[aem pilote la structure](#aem-drives-site-structure)** du site : le développeur principal crée des composants et possède leur structure interne, mais compte sur AEM pour définir la structure du contenu du site.
* **[Rendu](#dynamic-rendering)** dynamique : tous les rendus doivent être dynamiques.
* **[Routage](#dynamic-routing)** dynamique - L&#39;APM est responsable du routage et AEM l&#39;écoute et les récupère en fonction. Tout routage devrait également être dynamique.

Si vous gardez ces principes à l’esprit lorsque vous développez votre application d’une seule page, elle sera aussi flexible et aussi future que possible, tout en activant toutes les fonctionnalités de création d’AEM prises en charge.

Si vous n’avez pas besoin de prendre en charge AEM fonctions de création, vous devrez peut-être envisager un modèle [de conception](#spa-design-models)d’application d’une seule page.

### Portabilité {#portability}

Comme lors du développement de n&#39;importe quel composant, vos composants doivent être conçus de manière à optimiser leur portabilité. Tout modèle qui va à l&#39;encontre de la portabilité ou de la réutilisation des composants doit être évité pour assurer la compatibilité, la flexibilité et la maintenabilité à l&#39;avenir.

L&#39;application d&#39;une seule page doit être construite avec des composants hautement portables et réutilisables.

### aem lecteurs Structure du site {#aem-drives-site-structure}

Le développeur principal doit se considérer comme responsable de la création d’une bibliothèque de composants SPA utilisés pour créer l’application. Le développeur frontal a un contrôle total de la structure interne des composants. [Cependant, AEM possède toujours la structure du site.](editor-overview.md)

Cela signifie que le développeur principal peut ajouter du contenu client avant ou après le point d’entrée des composants et peut également effectuer des appels tiers à l’intérieur du composant. Cependant, le développeur frontal ne contrôle pas entièrement la manière dont les composants sont imbriqués, par exemple.

### Rendu dynamique {#dynamic-rendering}

L’application d’une seule page doit reposer sur le rendu dynamique du contenu. Il s’agit de l’attente par défaut où AEM récupère et rend tous les enfants de la structure de contenu.

Tout rendu explicite pointant vers un contenu spécifique est considéré comme un rendu statique et bien que pris en charge ne sera pas compatible avec AEM fonctionnalités de création de contenu. Cela va aussi à l&#39;encontre du principe de [portabilité](#portability).

### Routage dynamique {#dynamic-routing}

Comme pour le rendu, tous les routages doivent également être dynamiques. En AEM, [l’application d’une seule page doit toujours être propriétaire du routage](routing.md) et AEM l’écoute et récupère le contenu en fonction de celui-ci.

Tout routage statique va à l&#39;encontre du [principe de portabilité](#portability) et limite l&#39;auteur en n&#39;étant pas compatible avec les fonctionnalités de création de contenu de l&#39;AEM. Par exemple, avec un routage statique, si l’auteur du contenu souhaite modifier un itinéraire ou une page, il doit demander au développeur principal de le faire.

## Archétype de projet AEM {#aem-project-archetype}

Tout projet AEM doit tirer parti de l’archétype [de projet](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html)AEM, qui prend en charge les projets d’application d’une seule page à l’aide de React ou d’Angular et qui utilise le SDK d’application d’une seule page.

## Modèles de conception SPA {#spa-design-models}

Si les [principes de développement des applications monopages en AEM](#spa-development-principles-for-aem) sont respectés, votre application d’application d’une seule page sera fonctionnelle avec toutes les fonctionnalités de création de contenu AEM prises en charge.

Il peut toutefois y avoir des cas où cela n&#39;est pas tout à fait nécessaire. Le tableau suivant présente un aperçu des différents modèles de conception, leurs avantages et leurs inconvénients.

<table>
 <tbody>
  <tr>
   <th><strong>Modèle de conception<br /> </strong></th>
   <th><strong>Avantages</strong></th>
   <th><strong>Inconvénients</strong></th>
  </tr>
  <tr>
   <td>aem est utilisé en tant que CMS sans en-tête sans utiliser la structure <a href="https://docs.adobe.com/content/help/en/experience-manager-65/developing/headless/spas/spa-reference-materials.html">SPA Editor SDK.</a></td>
   <td>Le développeur frontal a un contrôle total sur l’application.</td>
   <td><p>Les auteurs de contenu ne peuvent pas exploiter AEM expérience de création de contenu.</p> <p>Le code n'est ni portable ni réutilisable s'il contient des références statiques ou un routage.</p> <p>N’autorise pas l’utilisation de l’éditeur de modèles ; le développeur principal doit donc gérer les modèles modifiables via le JCR.</p> </td>
  </tr>
  <tr>
   <td>Le développeur frontal utilise la structure du SDK de l’éditeur d’applications monopages, mais n’ouvre que certaines zones à l’auteur du contenu.</td>
   <td>Le développeur garde le contrôle de l’application en activant uniquement la création dans des zones restreintes de l’application.</td>
   <td><p>Les auteurs de contenu sont limités à un ensemble limité d’AEM expérience de création de contenu.</p> <p>Le code risque de ne pas être portable ni réutilisable s'il contient des références statiques ou un routage.</p> <p>N’autorise pas l’utilisation de l’éditeur de modèles ; le développeur principal doit donc gérer les modèles modifiables via le JCR.</p> </td>
  </tr>
  <tr>
   <td>Le projet tire pleinement parti du SDK de l’éditeur d’applications monopages et les composants frontaux sont développés en tant que bibliothèque et la structure de contenu de l’application est déléguée à AEM.</td>
   <td><p>L'application est réutilisable et portable.</p> <p>L’auteur du contenu peut modifier l’application à l’aide de AEM expérience de création de contenu.<br /> </p> <p>L’application d’une seule page est compatible avec l’éditeur de modèles.</p> </td>
   <td><p>Le développeur ne contrôle pas la structure de l’application et la partie du contenu déléguée à AEM.</p> <p>Le développeur peut toujours réserver des zones de l’application pour le contenu qui ne doit pas être créé à l’aide d’AEM.</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Bien que tous les modèles soient pris en charge en AEM, ce n&#39;est qu&#39;en mettant en oeuvre le troisième (et en respectant ainsi les principes de développement [des ZPS recommandés dans AEM](#spa-development-principles-for-aem)) que les auteurs de contenu pourront interagir et modifier le contenu de l&#39;ZPS dans l&#39;, comme ils s&#39;y habituent.

## Migration des applications monopages existantes vers AEM {#migrating-existing-spas-to-aem}

En règle générale, si votre application d’une seule page respecte les Principes de développement de l’ [application d’une seule page pour AEM](#spa-development-principles-for-aem), elle fonctionne en AEM et peut être modifiée à l’aide de l’éditeur d’une seule page d’une seule page.

Suivez ces étapes pour préparer votre application d’une seule page à travailler avec AEM.

1. **Rendez vos composants JS modulaires.** - Les rendre capables d&#39;être rendus dans n&#39;importe quel ordre, position et taille.
1. **Utilisez les conteneurs fournis par notre SDK pour placer vos composants à l’écran.** - AEM fournit un composant de système de paragraphe et de page que vous pouvez utiliser.
1. **Créez un composant AEM pour chaque composant JS.** - Les composants AEM définissent la boîte de dialogue et la sortie JSON.

## Instructions destinées aux développeurs de premier plan {#instructions-for-front-end-developers}

La principale tâche pour inciter un développeur frontal à créer une application d’une seule page pour AEM est de s’entendre sur les composants et leurs modèles JSON.

Vous trouverez ci-dessous un aperçu des étapes que doit suivre un développeur frontal lors du développement d’une application d’une seule page pour AEM.

1. **Accepter les composants et leur modèle JSON**

   Les développeurs frontaux et les développeurs d&#39;AEM dorsaux doivent s&#39;entendre sur les composants nécessaires et sur un modèle pour qu&#39;il y ait une correspondance individuelle entre les composants d&#39;une application d&#39;une seule page et les composants d&#39;arrière-plan.

   aem composants sont toujours nécessaires principalement pour fournir des boîtes de dialogue de modification et pour exporter le modèle de composant.

1. **Dans les composants Réagir, accédez au modèle via`this.props.cqModel`**

   Une fois les composants acceptés et le modèle JSON en place, le développeur frontal est libre de développer l&#39;application d&#39;une seule page et peut simplement accéder au modèle JSON via `this.props.cqModel`.

1. **Mise en oeuvre de la`render()`méthode du composant**

   Le développeur frontal met en oeuvre la `render()` méthode à sa convenance et peut utiliser les champs de la `cqModel` propriété. Cette opération génère le DOM et les fragments HTML qui seront insérés dans la page. Il s’agit de la méthode standard de création d’une application dans React.

1. **Faites correspondre le composant au type de ressource AEM via`MapTo()`**

   Le mappage stocke les classes de composants et est utilisé en interne par le `Container` composant fourni pour récupérer et instancier dynamiquement les composants en fonction du type de ressource donné.

   Il sert de &quot;colle&quot; entre l&#39;avant et l&#39;arrière-plan afin que l&#39;éditeur sache quels composants correspondent les composants réactifs.

   Les `Page` et `ResponsiveGrid` sont de bons exemples de classes qui étendent la base `Container`.

1. **Définissez le composant comme`EditConfig`paramètre pour`MapTo()`**

   Ce paramètre est nécessaire pour indiquer à l’éditeur comment le composant doit être nommé aussi longtemps qu’il n’est pas encore rendu ou n’a aucun contenu à rendre.

1. **Étendre la`Container`classe fournie pour les pages et les conteneurs**

   Les systèmes de pages et de paragraphes doivent étendre cette classe afin que la délégation aux composants internes fonctionne comme prévu.

1. **Implémentez une solution de routage qui utilise l’`History`API HTML5.**

   Lorsque la fonction `ModelRouter` est activée, l’appel des `pushState` fonctions et `replaceState` déclenche une demande à la `PageModelManager` fonction pour récupérer un fragment manquant du modèle.

   La version actuelle du modèle `ModelRouter` ne prend en charge que l&#39;utilisation d&#39;URL pointant vers le chemin de ressource réel des points d&#39;entrée du modèle Sling. Il ne prend pas en charge l’utilisation d’URL ou de alias mineurs.

   Il `ModelRouter` peut être désactivé ou configuré pour ignorer une liste d&#39;expressions régulières.

## aem-Agnostique {#aem-agnostic}

Ces blocs de code illustrent comment vos composants Réagir et Angular n&#39;ont besoin de rien qui soit spécifique à l&#39;Adobe ou à l&#39;AEM.

* Tout ce qui se trouve à l’intérieur du composant JavaScript est indifférent aux AEM.
* Ce qui est toutefois spécifique à AEM est que le composant JS doit être mappé à un composant AEM avec l&#39;aide MapTo.

![aem Approche agnostique](assets/aem-agnostic.png)

L&#39; `MapTo` aide est la &quot;colle&quot; qui permet de faire correspondre les composants back-end et front-end :

* Il indique au conteneur JS (ou système de paragraphes JS) quel composant JS est responsable du rendu de chacun des composants présents dans le fichier JSON.
* Il ajoute un attribut de données HTML au code HTML généré par le composant JS, de sorte que l’éditeur d’applications monopages sache quelle boîte de dialogue afficher à l’auteur lors de la modification du composant.

Pour plus d’informations sur l’utilisation `MapTo` et la création d’applications monopages pour AEM en général, consultez le guide de prise en main de votre structure choisie.

* [Prise en main des applications monopages dans AEM Utilisation de la fonction Réagir](getting-started-react.md)
* [Prise en main des applications monopages dans AEM Utilisation d’Angular](getting-started-angular.md)

## Architecture AEM et applications monopages {#aem-architecture-and-spas}

L’architecture générale des AEM, y compris les environnements de développement, de création et de publication, ne change pas lors de l’utilisation d’applications monopages. Cependant, il est utile de comprendre comment le développement des applications SPA s&#39;intègre dans cette architecture.

![Architecture AEM et SPA](assets/aem-architecture.png)

* **Créer un Environnement**

   C’est ici que la source de l’application SPA et la source du composant sont extraites.

   * Le générateur NPM clientlib crée une bibliothèque cliente à partir du projet SPA.
   * Cette bibliothèque sera prise par Maven et déployée par le module externe Maven Build avec le composant dans AEM Author.

* **Auteur AEM**

   Le contenu est créé sur l’AEM auteur, y compris la création d’applications monopages.

   Lorsqu’une application d’une seule page est modifiée à l’aide de l’éditeur d’applications d’une seule page sur l’environnement de création :

   1. L’application d’une seule page demande le code HTML externe.
   1. Le fichier CSS est chargé.
   1. Le script JavaScript de l’application SPA est chargé.
   1. Lorsque l’application d’une seule page est exécutée, le fichier JSON est demandé, ce qui permet à l’application de créer le DOM de la page, y compris les `cq-data` attributs.
   1. Ces `cq-data` attributs permettent à l’éditeur de charger des informations de page supplémentaires afin de connaître les configurations de modification disponibles pour les composants.

* **Publication AEM**

   C’est ici que le contenu créé et les bibliothèques compilées, y compris les artefacts d’application SPA, les clientlibs et les composants, sont publiés pour la consommation publique.

* **Répartiteur / CDN**

   Le répartiteur sert de couche de mise en cache des AEM pour les visiteurs sur le site.
   * Les requêtes sont traitées de la même manière que sur l’auteur AEM. Toutefois, aucune requête d’informations de page n’est envoyée, car cette requête n’est requise que par l’éditeur.
   * Javascript, CSS, JSON et HTML sont mis en cache, ce qui optimise la page pour une diffusion rapide.

>[!NOTE]
>
>Dans AEM il n&#39;est pas nécessaire d&#39;exécuter les mécanismes de création Javascript ni d&#39;exécuter le JavaScript lui-même. aem héberge uniquement les artefacts compilés de l’application SPA.

## Étapes suivantes {#next-steps}

* [Prise en main des applications monopages dans AEM à l’aide de React](getting-started-react.md) montre comment une application monopage de base est créée pour fonctionner avec l’éditeur d’applications monopages dans AEM à l’aide de React.
* [Prise en main des applications monopages en AEM à l’aide d’Angular](getting-started-angular.md) montre comment une application monopage de base est créée pour fonctionner avec l’éditeur d’applications monopages en AEM à l’aide d’Angular.
* [Présentation](editor-overview.md) de l’éditeur d’applications d’une seule page approfondit le modèle de communication entre l’AEM et l’application d’une seule page.
* [WKND SPA Project](wknd-tutorial.md) est un didacticiel détaillé qui met en oeuvre un projet SPA simple en AEM.
* [Le mappage modèle dynamique/composant pour les applications monopages](model-to-component-mapping.md) explique le mappage des composants du modèle dynamique et son fonctionnement dans les applications monopages dans AEM.
* [SPA Blueprint](blueprint.md) offre une plongée profonde dans le fonctionnement du SDK SPA pour AEM au cas où vous souhaiteriez mettre en oeuvre des SPA dans AEM pour un cadre autre que React ou Angular ou simplement pour une compréhension plus approfondie.
