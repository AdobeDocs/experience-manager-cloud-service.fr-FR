---
title: Prise en main des applications monopages dans AEM Utilisation d’Angular
description: Cet article présente un exemple d’application d’une seule page d’une seule page d’une seule page d’une seule page d’une seule page d’une seule page d’une seule page d’une seule page.
translation-type: tm+mt
source-git-commit: 8bdb7bbe80a4e22bb2b750c0719c6db745133392
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 27%

---


# Prise en main des applications monopages dans AEM Utilisation d’Angular {#getting-started-with-spas-in-aem-using-angular}

Les applications d’une seule page (SPA) peuvent améliorer considérablement l’expérience des utilisateurs de sites web. Le souhait des développeurs est de pouvoir créer des sites avec des structures SPA. Les auteurs, pour leur part, souhaitent modifier facilement du contenu dans AEM pour un site conçu à l’aide de telles structures.

La fonction de création d’application d’une seule page constitue une solution complète pour la prise en charge de ce type d’application dans AEM. Cet article présente une application SPA simplifiée sur la structure Angular, explique comment elle est mise en place, ce qui vous permet de maîtriser rapidement votre propre application SPA.

>[!NOTE]
>
>Cet article est basé sur la structure angulaire. Pour le document correspondant au cadre Réagir, voir [Prise en main des applications monopages dans AEM - Réagir](getting-started-react.md).

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

Ce document vous fera découvrir la structure d&#39;une application d&#39;une seule page d&#39;une seule page d&#39;une seule page et vous permettra d&#39;illustrer son fonctionnement afin que vous puissiez appliquer cette compréhension à votre propre application d&#39;une seule page d&#39;une seule page.

## Dépendances, configuration et construction {#dependencies-configuration-and-building}

Outre la dépendance angulaire attendue, l’exemple d’application d’une seule page peut tirer parti de bibliothèques supplémentaires pour rendre la création de l’application d’une seule page plus efficace.

### Dépendances {#dependencies}

Le `package.json` fichier définit les exigences du pack d’application d’une seule page. Les dépendances AEM minimales requises sont répertoriées ici.

```
"dependencies": {
  "@adobe/aem-angular-editable-components": "~1.0.3",
  "@adobe/aem-spa-component-mapping": "~1.0.5",
  "@adobe/aem-spa-page-model-manager": "~1.0.3"
}
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

Tout projet AEM doit tirer parti de l’archétype [de projet](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html)AEM, qui prend en charge les projets d’application d’une seule page à l’aide de React ou d’Angular et qui utilise le SDK d’application d’une seule page.

## Structure d’application {#application-structure}

L’inclusion des dépendances et la création de votre application comme décrit précédemment vous laisseront avec un pack d’applications monopages fonctionnel que vous pourrez télécharger sur votre instance AEM.

La section suivante de ce document vous permettra de découvrir comment une application SPA est structurée en AEM, les fichiers importants qui pilotent l&#39;application et comment elle fonctionne ensemble.

Un composant d’image simplifié est utilisé comme exemple, mais tous les composants de l’application sont basés sur le même concept.

### app.module.ts {#app-module-ts}

The entry point into the SPA is the `app.module.ts` file shown here simplified to focus on the important content.

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

Le `app.module.ts` fichier est le point de départ de l’application et contient la configuration initiale du projet et est utilisé `AppComponent` pour amorcer l’application.

#### Instanciation statique {#static-instantiation}

Lorsque le composant est instancié de manière statique à l’aide du modèle de composant, la valeur doit être transmise du modèle aux propriétés du composant. Les valeurs du modèle sont transmises en tant qu’attributs pour être disponibles ultérieurement en tant que propriétés de composant.

### app.component.ts {#app-component-ts}

Une fois `app.module.ts` amorcé `AppComponent`, il peut initialiser l’application, qui est présentée ici dans une version simplifiée pour se concentrer sur le contenu important.

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

En traitant la page, `app.component.ts` les appels `main-content.component.ts` sont répertoriés ici dans une version simplifiée.

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

Le `Page` est composé de composants. Une fois le fichier JSON ingéré, il `Page` peut traiter ces composants, comme `image.component.ts` illustré ici.

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

Les applications d’une seule page dans AEM ont comme principale finalité de mapper les composants SPA aux composants AEM et de mettre à jour le composant lorsque le contenu est modifié (et vice versa). See the document [SPA Editor Overview](editor-overview.md) for an summary of this communication model.

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

## Partage d’informations entre les composants de l’application d’une seule page {#sharing-information-between-spa-components}

Il est régulièrement nécessaire que les composants d’une application d’une seule page partagent des informations. Il existe plusieurs méthodes recommandées pour ce faire, énumérées ci-dessous dans un ordre croissant de complexité.

* **Option 1 :** Centralisez la logique et diffusez les éléments nécessaires, par exemple en utilisant une classe complète comme solution purement orientée objet.
* **Option 2 :** Partagez des états de composant en utilisant une bibliothèque d’états telle que NgRx.
* **Option 3 :** Tirez parti de la hiérarchie d’objets en personnalisant et en étendant le composant de conteneur.

## Étapes suivantes {#next-steps}

* [Prise en main des applications monopages dans AEM à l’aide de React](getting-started-react.md) montre comment une application monopage de base est créée pour fonctionner avec l’éditeur d’applications monopages dans AEM à l’aide de React.
* [Présentation](editor-overview.md) de l’éditeur d’applications d’une seule page approfondit le modèle de communication entre l’AEM et l’application d’une seule page.
* [WKND SPA Project](wknd-tutorial.md) est un didacticiel détaillé qui met en oeuvre un projet SPA simple en AEM.
* [Le mappage modèle dynamique/composant pour les applications monopages](model-to-component-mapping.md) explique le mappage des composants du modèle dynamique et son fonctionnement dans les applications monopages dans AEM.
* [SPA Blueprint](blueprint.md) offre une plongée profonde dans le fonctionnement du SDK SPA pour AEM au cas où vous souhaiteriez mettre en oeuvre des SPA dans AEM pour un cadre autre que React ou Angular ou simplement pour une compréhension plus approfondie.
