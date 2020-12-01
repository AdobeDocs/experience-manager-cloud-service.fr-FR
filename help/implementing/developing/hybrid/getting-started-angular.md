---
title: Prise en main des SPA dans AEM avec Angular
description: Cet article présente un exemple d'application SPA, explique comment elle est organisée et vous permet de vous familiariser avec votre propre SPA rapidement en utilisant la structure Angular.
translation-type: tm+mt
source-git-commit: cdd92032c627740c66de7b2f3836fa1dcd2ee2ca
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 43%

---


# Prise en main des SPA dans AEM avec Angular {#getting-started-with-spas-in-aem-using-angular}

Les applications sur une seule page (SPA) peuvent améliorer considérablement l’expérience des utilisateurs de sites web. Le souhait des développeurs est de pouvoir créer des sites avec des structures SPA. Les auteurs, pour leur part, souhaitent modifier facilement du contenu dans AEM pour un site conçu à l’aide de telles structures.

La fonction de création d’application d’une seule page constitue une solution complète pour la prise en charge de ce type d’application dans AEM. Cet article présente une application SPA simplifiée sur le cadre Angular, explique comment il est assemblé, vous permettant de vous mettre en contact avec vos propres SPA rapidement.

>[!NOTE]
>
>Cet article est basé sur la structure angulaire. Pour le document correspondant au cadre Réagir, voir [Prise en main de SPA dans AEM - Réagir](getting-started-react.md).

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

Ce document vous permettra de parcourir la structure d&#39;un SPA simplifié et d&#39;illustrer comment il fonctionne pour que vous puissiez appliquer cette compréhension à votre propre SPA.

## Dépendances, configuration et construction {#dependencies-configuration-and-building}

Outre la dépendance angulaire attendue, l’exemple de SPA peut exploiter d’autres bibliothèques pour rendre la création du SPA plus efficace.

### Dépendances {#dependencies}

Le fichier `package.json` définit les exigences du package SPA global. Les dépendances AEM minimales requises sont répertoriées ici.

```
"dependencies": {
  "@adobe/aem-angular-editable-components": "~1.0.3",
  "@adobe/aem-spa-component-mapping": "~1.0.5",
  "@adobe/aem-spa-page-model-manager": "~1.0.3"
}
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
    clientLibRoot: "./../content/jcr_root/apps/my-angular-app/clientlibs",

    libs: {
        name: "my-angular-app",
        allowProxy: true,
        categories: ["my-angular-app"],
        embed: ["my-angular-app.responsivegrid"],
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

`"build": "ng build --build-optimizer=false && clientlib",`

Une fois construit, le module peut être téléchargé dans une instance AEM.

### Archétype de projet AEM {#aem-project-archetype}

Tout projet AEM doit exploiter l’[archétype de projet AEM](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/developing/archetype/overview.html), qui prend en charge les projets SPA à l’aide de React ou d’Angular et utilise le SDK SPA.

## Structure d’application {#application-structure}

L’inclusion des dépendances et la création de votre application comme décrit précédemment vous laisseront avec un SPA de travail que vous pourrez télécharger sur votre instance AEM.

La section suivante de ce document vous permettra de découvrir comment une SPA en AEM est structurée, les fichiers importants qui pilotent l&#39;application et comment ils fonctionnent ensemble.

Un composant d’image simplifié est utilisé comme exemple, mais tous les composants de l’application sont basés sur le même concept.

### app.module.ts {#app-module-ts}

Le point d&#39;entrée dans la SPA est le fichier `app.module.ts` présenté ici simplifié pour se concentrer sur le contenu important.

```
// app.module.ts
import { BrowserModule, BrowserTransferStateModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { AppComponent } from './app.component';
import { SpaAngularEditableComponentsModule } from '@adobe/aem-angular-editable-components';
import { AppRoutingModule } from './app-routing.module';

@NgModule({
  imports: [ BrowserModule.withServerTransition({ appId: 'my-angular-app' }),
    SpaAngularEditableComponentsModule,
    AppRoutingModule,
    BrowserTransferStateModule ],
  providers: ...,
  declarations: [ ... ],
  entryComponents: [ ... ],
  bootstrap: [ AppComponent ]
})
export class AppModule {}
```

Le fichier `app.module.ts` est le point de départ de l’application et contient la configuration initiale du projet et utilise `AppComponent` pour amorcer l’application.

#### Instanciation statique {#static-instantiation}

Lorsque le composant est instancié de manière statique à l’aide du modèle de composant, la valeur doit être transmise du modèle aux propriétés du composant. Les valeurs du modèle sont transmises en tant qu’attributs pour être disponibles ultérieurement en tant que propriétés de composant.

### app.component.ts {#app-component-ts}

Une fois `app.module.ts` amorçage `AppComponent` effectué, il peut initialiser l&#39;application, qui est présentée ici dans une version simplifiée pour se concentrer sur le contenu important.

```
// app.component.ts
import { Component } from '@angular/core';
import { ModelManager } from '@adobe/aem-spa-page-model-manager';
import { Constants } from "@adobe/aem-angular-editable-components";

@Component({
  selector: 'app-root',
  template: `
    <router-outlet></router-outlet>
  `
})

export class AppComponent {
  items;
  itemsOrder;
  path;

  constructor() {
    ModelManager.initialize().then(this.updateData.bind(this));
  }

  private updateData(model) {
    this.path = model[Constants.PATH_PROP];
    this.items = model[Constants.ITEMS_PROP];
    this.itemsOrder = model[Constants.ITEMS_ORDER_PROP];
  }
}
```

### main-content.component.ts {#main-content-component-ts}

En traitant la page, `app.component.ts` appelle `main-content.component.ts` répertorié ici dans une version simplifiée.

```
import { Component } from '@angular/core';
import { ModelManagerService }     from '../model-manager.service';
import { ActivatedRoute } from '@angular/router';
import { Constants } from "@adobe/aem-angular-editable-components";

@Component({
  selector: 'app-main',
  template: `
    <aem-page class="structure-page" [attr.data-cq-page-path]="path" [cqPath]="path" [cqItems]="items" [cqItemsOrder]="itemsOrder" ></aem-page>
  `
})

export class MainContentComponent {
  items;
  itemsOrder;
  path;

  constructor( private route: ActivatedRoute,
    private modelManagerService: ModelManagerService) {
    this.modelManagerService.getData({ path: this.route.snapshot.data.path }).then((data) => {
      this.path = data[Constants.PATH_PROP];
      this.items = data[Constants.ITEMS_PROP];
      this.itemsOrder = data[Constants.ITEMS_ORDER_PROP];
    });
  }
}
```

`MainComponent` accède à la représentation JSON du modèle de page et traite le contenu pour encapsuler/décorer chaque élément de la page. De plus amples détails sur `Page` sont disponibles dans le document [Plan directeur de SPA](blueprint.md).

### image.component.ts {#image-component-ts}

Le `Page` est composé de composants. Une fois le fichier JSON ingéré, `Page` peut traiter les composants tels que `image.component.ts`, comme indiqué ici.

```
/// image.component.ts
import { Component, Input } from '@angular/core';

const ImageEditConfig = {

    emptyLabel: 'Image',

    isEmpty: function(cqModel) {
        return !cqModel || !cqModel.src || cqModel.src.trim().length < 1;
    }
};

@Component({
  selector: 'app-image',
  templateUrl: './image.component.html',
})

export class ImageComponent {
  @Input() src: string;
  @Input() alt: string;
  @Input() title: string;
}

MapTo('my-angular-app/components/image')(ImageComponent, ImageEditConfig);
```

Les applications d’une seule page dans AEM ont comme principale finalité de mapper les composants SPA aux composants AEM et de mettre à jour le composant lorsque le contenu est modifié (et vice versa). Consultez le document [SPA Editor Overview](editor-overview.md) pour un résumé de ce modèle de communication.

`MapTo('my-angular-app/components/image')(Image, ImageEditConfig);`

La méthode `MapTo` mappe le composant SPA au composant AEM. Elle prend en charge l’utilisation d’une seule chaîne ou d’une table de chaînes.

`ImageEditConfig` est un objet de configuration qui contribue à activer les fonctionnalités de création d’un composant en fournissant les métadonnées nécessaires à l’éditeur pour générer des espaces réservés.

S’il n’y a pas de contenu, des libellés sont fournis sous forme d’espaces réservés pour représenter le contenu vide.

#### Propriétés transmises dynamiquement {#dynamically-passed-properties}

Les données provenant du modèle sont transmises dynamiquement en tant que propriétés du composant.

### image.component.html {#image-component-html}

Enfin, l’image peut être rendue dans `image.component.html`.

```
// image.component.html
<img [src]="src" [alt]="alt" [title]="title"/>
```

## Partage d&#39;informations entre les composants SPA {#sharing-information-between-spa-components}

Il est régulièrement nécessaire que les composants d’une application d’une seule page partagent des informations. Il existe plusieurs méthodes recommandées pour ce faire, énumérées ci-dessous dans un ordre croissant de complexité.

* **Option 1 :** Centralisez la logique et diffusez-la aux composants nécessaires, par exemple en utilisant une classe util comme solution purement orientée objet.
* **Option 2 :** Partage des états du composant à l&#39;aide d&#39;une bibliothèque d&#39;états telle que NgRx.
* **Option 3 :** tirez parti de la hiérarchie d’objets en personnalisant et en étendant le composant de conteneur.

## Étapes suivantes {#next-steps}

* [Prise en main des SPA dans AEM avec React](getting-started-react.md) présente comment créer une SPA de base pour fonctionner avec l’éditeur de SPA dans AEM avec React.
* [Vue d’ensemble de l’éditeur de SPA](editor-overview.md) décrit de manière plus détaillée le modèle de communication entre AEM et la SPA.
* [WKND SPA Project](wknd-tutorial.md) est un tutoriel détaillé qui met en œuvre un projet de SPA simple dans AEM.
* [Mappage dynamique de modèle à composant pour SPA](model-to-component-mapping.md) explique le mappage dynamique du modèle au composant et son fonctionnement au sein de SPA dans AEM.
* [Plan directeur d’applications sur une seule page (SPA)](blueprint.md) explique en détail le fonctionnement du SDK SPA pour AEM pour la mise en œuvre de SPA dans AEM dans un autre framework que React ou Angular.
