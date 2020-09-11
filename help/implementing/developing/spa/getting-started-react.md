---
title: Prise en main des applications monopages dans AEM Utilisation de la fonction Réagir
description: Cet article présente un exemple d’application d’une seule page d’une seule page d’une seule page d’une seule page d’une seule page d’une seule page d’une seule page d’une seule page d’une seule page d’une seule page.
translation-type: tm+mt
source-git-commit: 8bdb7bbe80a4e22bb2b750c0719c6db745133392
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 36%

---


# Prise en main des applications monopages dans AEM Utilisation de la fonction Réagir {#getting-started-with-spas-in-aem-using-react}

Les applications d’une seule page (SPA) peuvent améliorer considérablement l’expérience des utilisateurs de sites web. Le souhait des développeurs est de pouvoir créer des sites avec des structures SPA. Les auteurs, pour leur part, souhaitent modifier facilement du contenu dans AEM pour un site conçu à l’aide de telles structures.

La fonction de création d’application d’une seule page constitue une solution complète pour la prise en charge de ce type d’application dans AEM. Cet article présente une application SPA simplifiée sur le cadre React, explique comment elle est mise en place, ce qui vous permet de maîtriser rapidement votre propre application SPA.

>[!NOTE]
>
>Cet article est basé sur le cadre Réagir. Pour le document correspondant à la structure angulaire, voir [Prise en main des applications monopages dans AEM - Angular](getting-started-angular.md).

## Présentation {#introduction}

Cet article résume le fonctionnement de base d’une application d’une seule page simple et ce que vous devez savoir pour que la vôtre soit opérationnelle.

Pour plus d’informations sur le fonctionnement des applications monopages en AEM, voir les documents suivants :

* [Présentation et présentation des applications monopages](introduction.md)
* [Aperçu de l’éditeur d’application d’une seule page](editor-overview.md)
* [Plan directeur d’applications sur une seule page (SPA)](blueprint.md)

>[!NOTE]
>
>Pour pouvoir créer du contenu dans une application d’une seule page, le contenu doit être stocké dans AEM et exposé par le modèle de contenu.
>
>Une ZPS développée en dehors de AEM ne sera pas autorisée si elle ne respecte pas le contrat du modèle de contenu.

Ce document va parcourir la structure d&#39;une application d&#39;une seule page d&#39;une seule page créée à l&#39;aide de la structure Réagir et illustrera son fonctionnement afin que vous puissiez appliquer cette compréhension à votre propre application d&#39;une seule page d&#39;une seule page.

## Dépendances, configuration et construction {#dependencies-configuration-and-building}

En plus de la dépendance React attendue, l’exemple d’application d’une seule page tire parti de bibliothèques supplémentaires pour optimiser la création de l’application d’une seule page.

### Dépendances {#dependencies}

Le `package.json` fichier définit les exigences du pack d’application d’une seule page. Les dépendances AEM minimales pour un SPA fonctionnel sont répertoriées ici.

```
  "dependencies": {
    "@adobe/aem-react-editable-components": "~1.0.4",
    "@adobe/aem-spa-component-mapping": "~1.0.5",
    "@adobe/aem-spa-page-model-manager": "~1.0.3"
  }
```

Because this example is based on the React framework, there are two React-specific dependencies which are obligatory in the `package.json` file:

```
 react
 react-dom
```

The `aem-clientlib-generator` is leveraged to make the creation of client libraries automatic as part of the build process.

`"aem-clientlib-generator": "^1.4.1",`

Plus de détails à ce sujet sont disponibles [sur GitHub ici](https://github.com/wcm-io-frontend/aem-clientlib-generator).

The `aem-clientlib-generator` is configured in the `clientlib.config.js` file as follows.

```
module.exports = {
    // default working directory (can be changed per 'cwd' in every asset option)
    context: __dirname,

    // path to the clientlib root folder (output)
    clientLibRoot: "./../content/jcr_root/apps/my-react-app/clientlibs",

    libs: {
        name: "my-react-app",
        allowProxy: true,
        categories: ["my-react-app"],
        embed: ["my-react-app.responsivegrid"],
        jsProcessor: ["min:gcc"],
        serializationFormat: "xml",
        assets: {
            js: [
                "dist/**/*.js"
            ],
            css: [
                "dist/**/*.css"
            ]
        }
    }
};
```

### Construction {#building}

En réalité, la construction de l’application utilise [Webpack](https://webpack.js.org/) pour la transpilation, en plus du aem-clientlib-generator pour la création automatique de la bibliothèque cliente. Par conséquent, la commande de construction est similaire à :

`"build": "webpack && clientlib --verbose"`

Une fois construit, le module peut être téléchargé dans une instance AEM.

### Archétype de projet AEM {#aem-project-archetype}

Tout projet AEM doit tirer parti de l’archétype [de projet](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html)AEM, qui prend en charge les projets d’application d’une seule page à l’aide de React ou d’Angular et qui utilise le SDK d’application d’une seule page.

## Structure d’application {#application-structure}

L’inclusion des dépendances et la création de votre application comme décrit précédemment vous laisseront avec un pack d’applications monopages fonctionnel que vous pourrez télécharger sur votre instance AEM.

La section suivante de ce document vous permettra de découvrir comment une application SPA est structurée en AEM, les fichiers importants qui pilotent l&#39;application et comment elle fonctionne ensemble.

Un composant d’image simplifié est utilisé comme exemple, mais tous les composants de l’application sont basés sur le même concept.

### index.js {#index-js}

Le point d’entrée dans l’application d’une seule page est bien entendu le fichier `index.js` présenté ici de manière simplifiée pour que l’on se concentre sur le contenu important.

```
import ReactDOM from 'react-dom';
import App from './App';
import { ModelManager, Constants } from "@adobe/aem-spa-page-model-manager";

...

ModelManager.initialize().then((pageModel) => {
ReactDOM.render(
    <App cqChildren={pageModel[Constants.CHILDREN_PROP]} cqItems={pageModel[Constants.ITEMS_PROP]} cqItemsOrder={pageModel[Constants.ITEMS_ORDER_PROP]} cqPath={ModelManager.rootPath} locationPathname={ window.location.pathname }/>
, document.getElementById('page'));

});
```

La principale finalité de `index.js` est de tirer parti de la fonction `ReactDOM.render` pour déterminer où, dans le DOM, injecter l’application.

Il s’agit d’une utilisation standard de cette fonction, qui n’est pas propre à cet exemple d’application.

#### Instanciation statique {#static-instantiation}

Lorsque le composant est instancié de manière statique à l’aide du modèle de composant (par exemple, JSX), la valeur doit être transmise du modèle aux propriétés du composant.

### App.js {#app-js}

En effectuant le rendu de l’application, `index.js` appelle `App.js`, présenté ici dans une version simplifiée pour que l’on se concentre sur le contenu important.

```
import {Page, withModel } from '@adobe/aem-react-editable-components';

...

class App extends Page {
...
}

export default withModel(App);
```

`App.js` sert principalement à encapsuler les composants racine qui composent l’application. Le point d’entrée de toute application est la page.

### Page.js {#page-js}

En rendant la page, `App.js` les appels `Page.js` sont répertoriés ici dans une version simplifiée.

```
import {Page, MapTo, withComponentMappingContext } from "@adobe/aem-react-editable-components";

...

class AppPage extends Page {
...
}

MapTo('my-react-app/components/structure/page')(withComponentMappingContext(AppPage));
```

In this example the `AppPage` class extends `Page`, which contains the inner-content methods that can then be used.

`Page` accède à la représentation JSON du modèle de page et traite le contenu pour encapsuler/décorer chaque élément de la page. De plus amples détails sur `Page` sont disponibles dans le document [Plan directeur de SPA.](blueprint.md)

### Image.js {#image-js}

Avec la page rendue, les composants tels que `Image.js` présentés ici peuvent être rendus.

```
import React, {Component} from 'react';
import {MapTo} from '@adobe/aem-react-editable-components';

require('./Image.css');

const ImageEditConfig = {

    emptyLabel: 'Image',

    isEmpty: function() {
        return !this.props || !this.props.src || this.props.src.trim().length < 1;
    }
};

class Image extends Component {

    render() {
        return (<img src={this.props.src}>);
    }
}

MapTo('my-react-app/components/content/image')(Image, ImageEditConfig);
```

Les applications d’une seule page dans AEM ont comme principale finalité de mapper les composants SPA aux composants AEM et de mettre à jour le composant lorsque le contenu est modifié (et vice versa). Pour obtenir un résumé de ce modèle de communication, consultez la Présentation [de l’éditeur](editor-overview.md) d’applications monopages de document.

`MapTo('my-react-app/components/content/image')(Image, ImageEditConfig);`

La méthode `MapTo` mappe le composant SPA au composant AEM. Elle prend en charge l’utilisation d’une seule chaîne ou d’une table de chaînes.

`ImageEditConfig` est un objet de configuration qui contribue à activer les fonctionnalités de création d’un composant en fournissant les métadonnées nécessaires à l’éditeur pour générer des espaces réservés.

S’il n’y a pas de contenu, des libellés sont fournis sous forme d’espaces réservés pour représenter le contenu vide.

#### Propriétés transmises dynamiquement {#dynamically-passed-properties}

Les données provenant du modèle sont transmises dynamiquement en tant que propriétés du composant.

## Exportation de contenu modifiable {#exporting-editable-content}

Vous pouvez exporter un composant et le laisser modifiable.

```
import React, { Component } from 'react';
import { MapTo } from '@adobe/aem-react-editable-components';

...

const EditConfig = {...}

class PageClass extends Component {...};

...

export default MapTo('my-react-app/react/components/structure/page')(PageClass, EditConfig);
```

The `MapTo` function returns a `Component` which is the result of a composition that extends the provided `PageClass` with the class names and attributes that enable the authoring. Ce composant peut être exporté pour être instancié ultérieurement dans le balisage de votre application.

When exported using the `MapTo` or `withModel` functions, the `Page` component, is wrapped with a `ModelProvider` component which provides standard components access to the latest version of the page model or a precise location in that page model.

Pour plus d’informations, voir le document [Plan directeur de SPA](blueprint.md).

>[!NOTE]
>
>Par défaut, vous recevez le modèle complet du composant lorsque vous utilisez la fonction `withModel`.

## Partage d’informations entre les composants de l’application d’une seule page {#sharing-information-between-spa-components}

Il est régulièrement nécessaire que les composants d’une application d’une seule page partagent des informations. Il existe plusieurs méthodes recommandées pour ce faire, énumérées ci-dessous dans un ordre croissant de complexité.

* **Option 1 :** Centralisez la logique et diffusez-la aux composants nécessaires, par exemple en utilisant React Context.
* **Option 2 :** Partagez des états de composant à l’aide d’une bibliothèque d’états telle que Redux.
* **Option 3 :** Tirez parti de la hiérarchie d’objets en personnalisant et en étendant le composant de conteneur.

## Étapes suivantes {#next-steps}

* [Prise en main des applications monopages en AEM à l’aide d’Angular](getting-started-angular.md) montre comment une application monopage de base est créée pour fonctionner avec l’éditeur d’applications monopages en AEM à l’aide d’Angular.
* [Présentation](editor-overview.md) de l’éditeur d’applications d’une seule page approfondit le modèle de communication entre l’AEM et l’application d’une seule page.
* [WKND SPA Project](wknd-tutorial.md) est un didacticiel détaillé qui met en oeuvre un projet SPA simple en AEM.
* [Le mappage modèle dynamique/composant pour les applications monopages](model-to-component-mapping.md) explique le mappage des composants du modèle dynamique et son fonctionnement dans les applications monopages dans AEM.
* [SPA Blueprint](blueprint.md) offre une plongée profonde dans le fonctionnement du SDK SPA pour AEM au cas où vous souhaiteriez mettre en oeuvre des SPA dans AEM pour un cadre autre que React ou Angular ou simplement pour une compréhension plus approfondie.
