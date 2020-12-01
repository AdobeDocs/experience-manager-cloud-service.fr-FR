---
title: Prise en main des SPA dans AEM avec React
description: Cet article présente un exemple d'application SPA, explique comment elle est organisée et vous permet de vous familiariser avec vos propres SPA rapidement en utilisant la structure Réagir.
translation-type: tm+mt
source-git-commit: cdd92032c627740c66de7b2f3836fa1dcd2ee2ca
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 50%

---


# Prise en main des SPA dans AEM avec React {#getting-started-with-spas-in-aem-using-react}

Les applications sur une seule page (SPA) peuvent améliorer considérablement l’expérience des utilisateurs de sites web. Le souhait des développeurs est de pouvoir créer des sites avec des structures SPA. Les auteurs, pour leur part, souhaitent modifier facilement du contenu dans AEM pour un site conçu à l’aide de telles structures.

La fonction de création d’application d’une seule page constitue une solution complète pour la prise en charge de ce type d’application dans AEM. Cet article présente une application de SPA simplifiée sur le cadre React, explique comment il est assemblé, vous permettant de vous mettre rapidement en contact avec vos propres SPA.

>[!NOTE]
>
>Cet article est basé sur le cadre Réagir. Pour le document correspondant au cadre angulaire, voir [Prise en main de la SPA dans AEM - Angular](getting-started-angular.md).

## Présentation {#introduction}

Cet article résume le fonctionnement de base d’une application d’une seule page simple et ce que vous devez savoir pour que la vôtre soit opérationnelle.

Pour plus d&#39;informations sur le fonctionnement des SPA en AEM, consultez les documents suivants :

* [Introduction et présentation des SPA](introduction.md)
* [Présentation de l’éditeur de SPA](editor-overview.md)
* [Plan directeur d’applications sur une seule page (SPA)](blueprint.md)

>[!NOTE]
>
>Pour pouvoir créer du contenu au sein d’un SPA, le contenu doit être stocké dans AEM et exposé par le modèle de contenu.
>
>Un SPA développé en dehors de AEM ne sera pas autorisé s&#39;il ne respecte pas le contrat du modèle de contenu.

Ce document va parcourir la structure d&#39;un SPA simplifié créé à l&#39;aide du cadre Réagir et illustrera comment il fonctionne pour que vous puissiez appliquer cette compréhension à votre propre SPA.

## Dépendances, configuration et construction {#dependencies-configuration-and-building}

En plus de la dépendance React attendue, l’exemple d’application d’une seule page tire parti de bibliothèques supplémentaires pour optimiser la création de l’application d’une seule page.

### Dépendances {#dependencies}

Le fichier `package.json` définit les exigences du package SPA global. Les dépendances AEM minimales pour un SPA fonctionnel sont répertoriées ici.

```
  "dependencies": {
    "@adobe/aem-react-editable-components": "~1.0.4",
    "@adobe/aem-spa-component-mapping": "~1.0.5",
    "@adobe/aem-spa-page-model-manager": "~1.0.3"
  }
```

Comme cet exemple est basé sur le cadre Réagir, il existe deux dépendances spécifiques Réagir qui sont obligatoires dans le fichier `package.json` :

```
 react
 react-dom
```

L&#39;élément `aem-clientlib-generator` est utilisé pour rendre la création de bibliothèques clientes automatique dans le cadre du processus de génération.

`"aem-clientlib-generator": "^1.4.1",`

Plus de détails à ce sujet sont disponibles [sur GitHub ici](https://github.com/wcm-io-frontend/aem-clientlib-generator).

`aem-clientlib-generator` est configuré dans le fichier `clientlib.config.js` comme suit.

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

Tout projet AEM doit exploiter l’[archétype de projet AEM](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/developing/archetype/overview.html), qui prend en charge les projets SPA à l’aide de React ou d’Angular et utilise le SDK SPA.

## Structure d’application {#application-structure}

L’inclusion des dépendances et la création de votre application comme décrit précédemment vous laisseront avec un SPA de travail que vous pourrez télécharger sur votre instance AEM.

La section suivante de ce document vous permettra de découvrir comment un SPA en AEM est structuré, les fichiers importants qui pilotent l&#39;application et comment ils fonctionnent ensemble.

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

En rendant la page, `App.js` appelle `Page.js` répertorié ici dans une version simplifiée.

```
import {Page, MapTo, withComponentMappingContext } from "@adobe/aem-react-editable-components";

...

class AppPage extends Page {
...
}

MapTo('my-react-app/components/structure/page')(withComponentMappingContext(AppPage));
```

Dans cet exemple, la classe `AppPage` étend `Page`, qui contient les méthodes de contenu interne qui peuvent ensuite être utilisées.

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

Les applications d’une seule page dans AEM ont comme principale finalité de mapper les composants SPA aux composants AEM et de mettre à jour le composant lorsque le contenu est modifié (et vice versa). Consultez le document [SPA Editor Overview](editor-overview.md) pour un résumé de ce modèle de communication.

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

La fonction `MapTo` renvoie un `Component` qui est le résultat d&#39;une composition qui étend le `PageClass` fourni avec les noms de classe et les attributs qui permettent la création. Ce composant peut être exporté pour être instancié ultérieurement dans le balisage de votre application.

Lors de l&#39;exportation à l&#39;aide des fonctions `MapTo` ou `withModel`, le composant `Page` est encapsulé avec un composant `ModelProvider` qui fournit aux composants standard l&#39;accès à la dernière version du modèle de page ou à un emplacement précis dans ce modèle de page.

Pour plus d’informations, voir le document [Plan directeur de SPA](blueprint.md).

>[!NOTE]
>
>Par défaut, vous recevez le modèle complet du composant lorsque vous utilisez la fonction `withModel`.

## Partage d&#39;informations entre les composants SPA {#sharing-information-between-spa-components}

Il est régulièrement nécessaire que les composants d’une application d’une seule page partagent des informations. Il existe plusieurs méthodes recommandées pour ce faire, énumérées ci-dessous dans un ordre croissant de complexité.

* **Option 1 :** Centralisez la logique et diffusez-la aux composants nécessaires, par exemple en utilisant le contexte de réaction.
* **Option 2 :** Partage des états du composant à l’aide d’une bibliothèque d’états telle que Redux.
* **Option 3 :** tirez parti de la hiérarchie d’objets en personnalisant et en étendant le composant de conteneur.

## Étapes suivantes {#next-steps}

* [Prise en main des SPA dans AEM avec Angular](getting-started-angular.md) présente comment créer une SPA de base pour fonctionner avec l’éditeur de SPA dans AEM avec Angular.
* [Vue d’ensemble de l’éditeur de SPA](editor-overview.md) décrit de manière plus détaillée le modèle de communication entre AEM et la SPA.
* [WKND SPA Project](wknd-tutorial.md) est un tutoriel détaillé qui met en œuvre un projet de SPA simple dans AEM.
* [Mappage dynamique de modèle à composant pour SPA](model-to-component-mapping.md) explique le mappage dynamique du modèle au composant et son fonctionnement au sein de SPA dans AEM.
* [Plan directeur d’applications sur une seule page (SPA)](blueprint.md) explique en détail le fonctionnement du SDK SPA pour AEM pour la mise en œuvre de SPA dans AEM dans un autre framework que React ou Angular.
