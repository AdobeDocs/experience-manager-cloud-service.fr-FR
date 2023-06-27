---
title: Développement de SPA pour AEM
description: Cet article présente des questions importantes à prendre en compte lorsqu’un développeur front-end doit développer un SPA pour AEM. Il donne également un aperçu de l’architecture de l’AEM concernant SPA à garder à l’esprit lors du déploiement d’un projet développé sur l’.
exl-id: f6c6f31a-69ad-48f6-b995-e6d0930074df
source-git-commit: d361ddc9a50a543cd1d5f260c09920c5a9d6d675
workflow-type: tm+mt
source-wordcount: '2034'
ht-degree: 49%

---

# Développement de SPA pour AEM {#developing-spas-for-aem}

Les applications monopage (SPA) peuvent améliorer considérablement votre expérience des sites web. Les développeurs souhaitent pouvoir créer des sites à l’aide de structures SPA et les auteurs souhaitent modifier facilement du contenu dans AEM pour un site créé à l’aide de ces structures.

Cet article présente des questions importantes à prendre en compte lorsqu’un développeur front-end doit développer un SPA pour AEM et donne un aperçu de l’architecture d’AEM concernant le déploiement sur.

## Principes de développement de SPA pour AEM {#spa-development-principles-for-aem}

Le développement d’applications sur une seule page sur AEM suppose que le développeur front-end respecte les bonnes pratiques standard lors de la création d’une SPA. Si, en tant que développeur front-end, vous suivez ces bonnes pratiques générales et quelques principes spécifiques à AEM, votre SPA est fonctionnel avec [AEM et ses fonctionnalités de création de contenu](introduction.md#content-editing-experience-with-spa).

* **[Portabilité](#portability)** : comme pour tout composant, les composants créés doivent être aussi portables que possible. La SPA doit être créée avec des composants portables et réutilisables.
* **[AEM détermine la structure du site](#aem-drives-site-structure)** - Le développeur front-end crée des composants et possède leur structure interne, mais s’appuie sur AEM pour définir la structure de contenu du site.
* **[Rendu dynamique](#dynamic-rendering)** : tout le rendu doit être dynamique.
* **[Routage dynamique](#dynamic-routing)** : la SPA assure le routage, et AEM l’écoute et s’appuie dessus pour l’extraction. Tout routage devrait également être dynamique.

Si vous gardez ces principes à l’esprit au fur et à mesure que vous développez votre SPA, ils deviennent aussi flexibles et futurs que possible tout en activant toutes les fonctionnalités de création d’AEM prises en charge.

Si vous n’avez pas besoin de prendre en charge AEM fonctionnalités de création, envisagez un [Modèle de conception SPA](#spa-design-models).

### Portabilité {#portability}

Comme lors du développement de tout composant, vous devez créer vos composants de manière à optimiser leur portabilité. Il convient d’éviter tout modèle qui va à l’encontre de la portabilité ou de la capacité de réutilisation des composants afin de garantir la compatibilité, la flexibilité et la maintenabilité à l’avenir.

Les SPA doivent être créées avec des composants hautement portables et réutilisables.

### AEM détermine la structure du site {#aem-drives-site-structure}

Le développeur front-end doit se considérer comme responsable de la création d’une bibliothèque de composants SPA utilisés pour créer l’application. Le développeur front-end contrôle entièrement la structure interne des composants. [Cependant, AEM possède toujours la structure du site.](editor-overview.md).

Ce contrôle signifie que le développeur front-end peut ajouter du contenu client avant ou après le point d’entrée des composants et peut également effectuer un appel tiers dans le composant. Cependant, le développeur front-end ne contrôle pas entièrement la manière dont les composants sont imbriqués, par exemple.

### Rendu dynamique {#dynamic-rendering}

La SPA ne devrait reposer que sur le rendu dynamique de contenu. Cette attente est la valeur par défaut où AEM récupère et effectue le rendu de tous les enfants de la structure de contenu.

Tout rendu explicite pointant vers un contenu spécifique est considéré comme un rendu statique et, bien qu’il soit pris en charge, est compatible avec les fonctions de création de contenu AEM. Elle va aussi à l&#39;encontre du principe de [portabilité](#portability).

### Routage dynamique {#dynamic-routing}

Comme pour le rendu, l’ensemble du routage devrait également être dynamique. Dans AEM, [la SPA devrait toujours être responsable du routage](routing.md). AEM l’écoute et s’appuie dessus pour l’extraction de contenu.

Tout routage statique va à l’encontre du [principe de portabilité](#portability) et limite l’auteur en n’étant pas compatible avec les fonctionnalités de création de contenu d’AEM. Par exemple, avec le routage statique, si l’auteur du contenu souhaite modifier un itinéraire ou une page, il doit demander au développeur front-end de le faire.

## Archétype de projet AEM {#aem-project-archetype}

Tout projet AEM doit utiliser la variable [AEM Archétype de projet](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr), qui prend en charge SPA projets à l’aide de React ou d’Angular et utilise le SDK SPA.

## Modèles de conception de SPA {#spa-design-models}

Si la variable [principes de développement des SPA en AEM](#spa-development-principles-for-aem) sont suivis, puis votre SPA est fonctionnel avec toutes les fonctionnalités de création de contenu AEM prises en charge.

Il peut toutefois arriver que cette fonctionnalité ne soit pas entièrement nécessaire. Le tableau suivant présente un aperçu des différents modèles de conception, leurs avantages et leurs inconvénients.

<table>
 <tbody>
  <tr>
   <th><strong>Modèle de conception<br /> </strong></th>
   <th><strong>Avantages</strong></th>
   <th><strong>Inconvénients</strong></th>
  </tr>
  <tr>
   <td>AEM est utilisé comme CMS sans affichage sans utiliser le <a href="/help/implementing/developing/hybrid/reference-materials.md">framework du SDK de l’éditeur de SPA.</a></td>
   <td>Le développeur front-end contrôle entièrement l’application.</td>
   <td><p>Les auteurs de contenu ne peuvent pas utiliser AEM expérience de création de contenu.</p> <p>Le code n’est ni portable ni réutilisable s’il contient des références statiques ou un routage.</p> <p>N’autorise pas l’utilisation de l’éditeur de modèles ; le développeur front-end doit donc conserver les modèles modifiables via le JCR.</p> </td>
  </tr>
  <tr>
   <td>Le développeur front-end utilise la structure du SDK de l’éditeur de SPA, mais n’ouvre que certaines zones à l’auteur du contenu.</td>
   <td>Le développeur garde le contrôle de l’application en n’autorisant la création que dans des zones restreintes de l’application.</td>
   <td><p>Les auteurs de contenu sont limités à un ensemble limité d’expérience de création de contenu d’AEM.</p> <p>Le code risque de ne pas être portable ou réutilisable s’il contient des références statiques ou un routage.</p> <p>N’autorise pas l’utilisation de l’éditeur de modèles ; le développeur front-end doit donc conserver les modèles modifiables via le JCR.</p> </td>
  </tr>
  <tr>
   <td>Le projet utilise entièrement le SDK de SPA Editor et les composants front-end sont développés en tant que bibliothèque et la structure de contenu de l’application est déléguée à AEM.</td>
   <td><p>L’application est réutilisable et portable.</p> <p>L’auteur de contenu peut modifier l’application à l’aide de l’expérience de création de contenu d’AEM.<br /> </p> <p>La SPA est compatible avec l’éditeur de modèles.</p> </td>
   <td><p>Le développeur ne contrôle pas la structure de l’application et la partie du contenu déléguée à AEM.</p> <p>Le développeur peut toutefois réserver des zones de l’application au contenu qui ne doit pas être créé à l’aide d’AEM.</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Bien que tous les modèles soient pris en charge dans AEM, uniquement en implémentant le troisième (et en suivant les recommandations) [Principes de développement SPA](#spa-development-principles-for-aem)) sont les auteurs de contenu qui peuvent interagir avec le contenu du SPA dans AEM et le modifier.

## Migration de SPA existantes vers AEM {#migrating-existing-spas-to-aem}

Si votre SPA suit [Principes de développement SPA pour l&#39;AEM](#spa-development-principles-for-aem), votre SPA fonctionne dans AEM et est modifiable à l’aide de l’éditeur d’.

Suivez ces étapes pour préparer votre SPA existant à travailler avec AEM.

1. **Rendez vos composants JS modulaires.** - Permettez leur rendu dans n’importe quel ordre, position et taille.
1. **Utilisez les conteneurs fournis par le SDK pour placer vos composants à l’écran.** – AEM fournit un composant de système de paragraphe et de page que vous pouvez utiliser.
1. **Créez un composant AEM pour chaque composant JS.** - Les composants AEM définissent la boîte de dialogue et la sortie JSON.

## Instructions destinées aux développeurs front-end {#instructions-for-front-end-developers}

Pour demander à un développeur front-end de créer une SPA pour AEM, la principale tâche consiste à convenir des composants et de leurs modèles JSON.

Voici un aperçu des étapes que doit suivre un développeur front-end lors du développement d’un SPA pour AEM.

1. **Convenir des composants et de leur modèle JSON**

   Les développeurs front-end et les développeurs d’AEM back-end doivent s’entendre sur les composants nécessaires et sur un modèle afin qu’il existe une correspondance individualisée entre les composants SPA et les composants back-end.

   Les composants d’AEM sont toujours nécessaires, notamment pour fournir des boîtes de dialogue d’édition et exporter le modèle de composant.

1. **Dans les composants React, accéder au modèle via`this.props.cqModel`**

   Une fois les composants définis et le modèle JSON en place, le développeur front-end est libre de développer la SPA et peut accéder simplement au modèle JSON via `this.props.cqModel`.

1. **Implémentation du composant `render()` method**

   Le développeur front-end met en œuvre la méthode `render()` à sa convenance et peut utiliser les champs de la propriété `cqModel`. Cette méthode génère le DOM et les fragments de HTML insérés dans la page. Cette méthode constitue également la méthode standard de création d’une application dans React.

1. **Faire correspondre le composant au type de ressource AEM via`MapTo()`**

   Le mappage stocke les classes de composants et est utilisé en interne par le composant `Container` fourni pour récupérer et instancier dynamiquement les composants en fonction du type de ressource donné.

   Cette map sert de &quot;colle&quot; entre le front-end et le back-end afin que l’éditeur sache à quels composants correspondent les composants de réaction.

   `Page` et `ResponsiveGrid` sont de bons exemples de classes qui étendent le `Container` de base.

1. **Définissez les `EditConfig` comme paramètre à`MapTo()`**

   Ce paramètre est nécessaire pour indiquer à l’éditeur comment le composant doit être nommé tant qu’il n’a pas encore effectué de rendu ou qu’il n’a aucun rendu à effectuer.

1. **Étendre la classe `Container` fournie pour les pages et les conteneurs**

   Les pages et les systèmes de paragraphes doivent étendre cette classe afin que la délégation aux composants internes fonctionne comme prévu.

1. **Mettre en œuvre une solution de routage qui utilise l’API HTML5 `History`**

   Lorsque la variable `ModelRouter` est activé, en appelant la fonction `pushState` et `replaceState` déclenche une requête à la fonction `PageModelManager` pour récupérer un fragment manquant du modèle.

   La version actuelle de `ModelRouter` ne prend en charge que l’utilisation d’URL pointant vers le chemin de ressource réel des points d’entrée du modèle Sling. Elle ne prend pas en charge l’utilisation de vanity URL ni d’alias.

   `ModelRouter` peut être désactivé ou configuré pour ignorer une liste d’expressions régulières.

## Indépendance par rapport à AEM {#aem-agnostic}

Ces blocs de code illustrent le fait que vos composants React et Angular n’ont besoin de rien qui soit spécifique à Adobe ou AEM.

* Tout ce qui se trouve à l’intérieur du composant JavaScript est indépendant d’AEM.
* Ce qui est spécifique à AEM, cependant, c’est que le composant JS doit être mappé à un composant AEM avec l’assistant MapTo.

![Approche indépendante d’AEM](assets/aem-agnostic.png)

L’assistant `MapTo` est la « colle » qui permet de faire correspondre les composants back-end et front-end :

* Il indique au conteneur JS (ou système de paragraphes JS) quel composant JS est responsable du rendu de chacun des composants présents dans le fichier JSON.
* Il ajoute un attribut de données HTML au code HTML généré par le composant JS, de sorte que l’éditeur de SPA sache quelle boîte de dialogue afficher pour l’auteur lors de la modification du composant.

Pour plus d’informations sur l’utilisation de `MapTo` et la création de SPA pour AEM en général, consultez le Guide de prise en main du framework choisi.

* [Prise en main des SPA dans AEM avec React](getting-started-react.md)
* [Prise en main des SPA dans AEM avec Angular](getting-started-angular.md)

## Architecture d’AEM et SPA {#aem-architecture-and-spas}

L’architecture générale d’AEM, y compris les environnements de développement, de création et de publication, ne change pas lors de l’utilisation de SPA. Il est toutefois utile de comprendre comment le développement de SPA s’inscrit dans cette architecture.

![Architecture d’AEM et SPA](assets/aem-architecture.png)

* **Environnement de création**

  Dans cet environnement, la source de l’application SPA et la source du composant sont extraites.

   * Le générateur clientlib NPM crée une bibliothèque cliente à partir du projet de SPA.
   * Cette bibliothèque est utilisée par Maven et déployée par le module externe Maven Build avec le composant sur l’auteur AEM.

* **Auteur AEM**

  Le contenu est créé sur l’auteur AEM, y compris les SPA de création.

  Lorsqu’une SPA est modifiée à l’aide de l’éditeur de SPA sur l’environnement de création :

   1. La SPA demande le code HTML externe.
   1. Le fichier CSS est chargé.
   1. Le code JavaScript de l’application SPA est chargé.
   1. Lorsque la SPA est exécutée, le fichier JSON est demandé, ce qui permet à l’application de créer le DOM de la page, y compris les attributs `cq-data`.
   1. Le `cq-data` Les attributs permettent à l’éditeur de charger des informations de page supplémentaires afin qu’il connaisse les configurations d’édition disponibles pour les composants.

* **Publication AEM**

  Où le contenu créé et les bibliothèques compilées, y compris les artefacts d’application SPA, les bibliothèques clientes et les composants, sont publiés pour une utilisation publique.

* **Dispatcher/réseau CDN**

  Dispatcher sert de couche d’AEM de mise en cache pour les visiteurs du site.
   * Les requêtes sont traitées de la même manière que sur l’auteur AEM. Toutefois, les informations de page ne sont pas demandées, car l’éditeur n’en a besoin que.
   * JavaScript, CSS, JSON et HTML sont mis en cache, ce qui optimise la page pour une diffusion rapide.

>[!NOTE]
>
>Dans AEM, il n’est pas nécessaire d’exécuter les mécanismes de création JavaScript ni d’exécuter le code JavaScript lui-même. AEM héberge uniquement les artefacts compilés de la SPA.

## Étapes suivantes {#next-steps}

* [Prise en main des SPA dans AEM avec React](getting-started-react.md) présente comment créer une SPA de base pour fonctionner avec l’éditeur de SPA dans AEM avec React.
* La section [Prise en main des SPA dans AEM avec Angular](getting-started-angular.md) montre comment une SPA de base est créée pour fonctionner avec l’éditeur de SPA dans AEM avec Angular.
* La section [Présentation de l’éditeur de SPA](editor-overview.md) examine de plus près le modèle de communication entre AEM et la SPA.
* Le tutoriel [Projet SPA WKND](wknd-tutorial.md) est un tutoriel détaillé qui met en œuvre un projet SPA simple dans AEM.
* La section [Mappage d’un modèle dynamique sur un composant pour les SPA](model-to-component-mapping.md) explique le mappage d’un modèle dynamique sur un composant et présente son fonctionnement au sein des SPA dans AEM.
* [Blueprint SPA](blueprint.md) offre un aperçu détaillé du fonctionnement du SDK SPA pour AEM si vous souhaitez mettre en oeuvre le SDK dans pour un framework autre que React ou Angular. Ou vous voulez simplement une compréhension plus approfondie.
