---
title: Modélisation de contenu pour la création AEM avec des projets Edge Delivery Services
description: Découvrez comment la modélisation de contenu fonctionne pour la création AEM avec des projets Edge Delivery Services et comment modéliser votre propre contenu.
source-git-commit: e9c882926baee001170bad2265a1085e03cdbedf
workflow-type: tm+mt
source-wordcount: '2097'
ht-degree: 1%

---


# Modélisation de contenu pour la création AEM avec des projets Edge Delivery Services {#content-modeling}

Découvrez comment la modélisation de contenu fonctionne pour la création AEM avec des projets Edge Delivery Services et comment modéliser votre propre contenu.

{{aem-authoring-edge-early-access}}

## Conditions préalables {#prerequisites}

Les projets utilisant la création AEM avec des Edge Delivery Services héritent de la majorité des mécanismes de tout autre projet Edge Delivery Services, indépendamment de la source de contenu ou [méthode de création.](/help/edge/authoring.md)

Avant de commencer à modéliser le contenu de votre projet, veillez à lire la documentation suivante.

* [Prise en main – Tutoriel pour l’équipe de développement](/help/edge/developer/tutorial.md)
* [Balisage, sections, blocs et blocage automatique](/help/edge/developer/markup-sections-blocks.md)
* [Collection de blocs](/help/edge/developer/block-collection.md)

Il est essentiel de comprendre ces concepts afin de trouver un modèle de contenu convaincant qui fonctionne de manière non dépendante des sources de contenu. Ce document fournit des détails sur les mécanismes mis en oeuvre spécifiquement pour la création AEM.

## Contenu par défaut {#default-content}

**Contenu par défaut** est le contenu qu’un auteur place intuitivement sur une page sans ajouter de sémantique supplémentaire. Cela inclut du texte, des en-têtes, des liens et des images. Un tel contenu s&#39;explique d&#39;elle-même par sa fonction et son objectif.

Dans AEM, ce contenu est implémenté sous la forme de composants avec des modèles prédéfinis très simples, qui incluent tout ce qui peut être sérialisé dans Markdown et HTML.

* **Texte**: texte enrichi (y compris les éléments de liste et le texte en italique ou fort)
* **Titre**: texte, type (h1-h6)
* **Image**: source, description
* **Bouton**: texte, titre, url, type (par défaut, principal, secondaire)

Le modèle de ces composants fait partie de la [Modèle standard pour la création AEM avec des Edge Delivery Services.](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-models.json#L2-L112)

## Blocs {#blocks}

Les blocs sont utilisés pour créer un contenu plus riche avec des styles et des fonctionnalités spécifiques. Contrairement au contenu par défaut, les blocs nécessitent une sémantique supplémentaire. Les blocs peuvent être associés à [composants dans l’éditeur de page d’AEM.](/help/implementing/developing/components/overview.md)

Les blocs sont essentiellement des éléments de contenu décorés par JavaScript et stylisés avec une feuille de style.

### Définition du modèle de bloc {#model-definition}

Lors de l’utilisation de la création AEM avec des Edge Delivery Services, le contenu des blocs doit être modélisé explicitement afin de fournir à l’auteur l’interface de création de contenu. Essentiellement, vous devez créer un modèle pour que l’interface utilisateur de création sache quelles options présenter à l’auteur en fonction du bloc.

La variable [`component-models.json`](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-models.json) définit le modèle des blocs. Les champs définis dans le modèle de composant sont conservés sous forme de propriétés dans AEM et générés sous forme de cellules dans le tableau qui constitue un bloc.

```json
{
  "id": "hero",
  "fields": [
    {
      "component": "reference",
      "valueType": "string",
      "name": "image",
      "label": "Image",
      "multi": false
    },
    {
      "component": "text-input",
      "valueType": "string",
      "name": "imageAlt",
      "label": "Alt",
      "value": ""
    },
    {
      "component": "text-area",
      "name": "text",
      "value": "",
      "label": "Text",
      "valueType": "string"
    }
  ]
}
```

Notez que tous les blocs ne doivent pas avoir de modèle. Certains blocs sont simplement [conteneurs](#container) pour une liste d’enfants, où chaque enfant a son propre modèle.

Il est également nécessaire de définir les blocs existants et qui peuvent être ajoutés à une page à l’aide de l’éditeur universel. La variable [`component-definitions.json`](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-definition.json) répertorie les composants tels qu’ils sont rendus disponibles par l’éditeur universel.

```json
{
  "title": "Hero",
  "id": "hero",
  "plugins": {
    "xwalk": {
      "page": {
        "resourceType": "core/franklin/components/block/v1/block",
        "template": {
          "name": "Hero",
          "model": "hero"
        }
      }
    }
  }
}
```

Il est possible d&#39;utiliser un modèle pour de nombreux blocs. Par exemple, certains blocs peuvent partager un modèle qui définit un texte et une image.

Pour chaque bloc, le développeur :

* Doit utiliser la variable `core/franklin/components/block/v1/block` type de ressource, l’implémentation générique de la logique de bloc dans AEM.
* Doit définir le nom du bloc, qui sera rendu dans l’en-tête du tableau du bloc.
   * Le nom du bloc est utilisé pour récupérer le style et le script appropriés pour décorer le bloc.
* Peut définir une [ID de modèle.](/help/implementing/universal-editor/field-types.md#model-structure)
   * L’ID de modèle est une référence au modèle du composant, qui définit les champs disponibles pour l’auteur dans le rail des propriétés.
* Peut définir une [ID de filtre.](/help/implementing/universal-editor/customizing.md#filtering-components)
   * L’ID de filtre est une référence au filtre du composant, qui permet de modifier le comportement de création, par exemple en limitant les enfants pouvant être ajoutés au bloc ou à la section, ou les fonctionnalités d’éditeur de texte enrichi activées.

Toutes ces informations sont stockées dans AEM lorsqu’un bloc est ajouté à une page. Si le type de ressource ou le nom du bloc est manquant, le bloc ne s’affiche pas sur la page.

>[!WARNING]
>
>Bien que cela soit possible, il n’est pas nécessaire ni recommandé de mettre en oeuvre des composants d’AEM personnalisés. Les composants des Edge Delivery Services fournis par AEM sont suffisants et offrent certains rails de garde pour faciliter le développement.
>
>Les composants fournis par AEM génèrent un balisage qui peut être utilisé par [helix-html2md](https://github.com/adobe/helix-html2md) lors de la publication sur des Edge Delivery Services et en [aem.js](https://github.com/adobe/aem-boilerplate/blob/main/scripts/aem.js) lors du chargement d’une page dans Universal Editor. Les balises constituent le contrat stable entre AEM et les autres parties du système et ne permettent pas les personnalisations. Pour cette raison, les projets ne doivent pas modifier les composants et ne doivent pas utiliser de composants personnalisés.

### Structure de bloc {#block-structure}

Les propriétés des blocs sont les suivantes : [défini dans les modèles de composant](#model-definition) et ont persisté en tant que telle dans AEM. Les propriétés sont rendues sous forme de cellules dans la structure de type tableau du bloc.

#### Blocs simples {#simple}

Dans le formulaire le plus simple, un bloc effectue le rendu de chaque propriété sur une seule ligne/colonne dans l’ordre dans lequel les propriétés sont définies dans le modèle.

Dans l’exemple suivant, l’image est définie en premier dans le modèle et en second dans le texte. Ils sont ainsi rendus avec l’image en premier et le texte en second.

>[!BEGINTABS]

>[!TAB Données]

```json
{
  "name": "Hero",
  "model": "hero",
  "image": "/content/dam/image.png",
  "imageAlt": "Helix - a shape like a corkscrew",
  "text": "<h1>Welcome to AEM</h1>"
}
```

>[!TAB Balisage]

```html
<div class="hero">
  <div>
    <div>
      <picture>
        <img src="/content/dam/image.png" alt="Helix - a shape like a corkscrew">
      </picture>
    </div>
  </div>
  <div>
    <div>
      <h1>Welcome to AEM</h1>
    </div>
  </div>
</div>
```

>[!TAB Tableau]

```text
+---------------------------------------------+
| Hero                                        |
+=============================================+
| ![Helix - a shape like a corkscrew][image0] |
+---------------------------------------------+
| # Welcome to AEM                            |
+---------------------------------------------+
```

>[!ENDTABS]

Vous remarquerez peut-être que certains types de valeurs autorisent la sémantique inférente dans les balises et que les propriétés sont combinées dans des cellules uniques. Ce comportement est décrit dans la section [Type Inférence.](#type-inference)

#### Bloc clé-valeur {#key-value}

Dans de nombreux cas, il est recommandé de décorer le balisage sémantique rendu, d’ajouter des noms de classe CSS, d’ajouter de nouveaux noeuds ou de les déplacer dans le modèle DOM et d’appliquer des styles.

Dans d&#39;autres cas, cependant, le bloc est lu comme une configuration de type paire clé-valeur.

Voici un exemple : [métadonnées de section.](/help/edge/developer/markup-sections-blocks.md#sections) Dans ce cas pratique, le bloc peut être configuré pour effectuer le rendu en tant que table de paires clé-valeur. Consultez la section [Métadonnées de sections](#sections-metadata) pour plus d’informations.

>[!BEGINTABS]

>[!TAB Données]

```json
{
  "name": "Featured Articles",
  "model": "spreadsheet-input",
  "key-value": true,
  "source": "/content/site/articles.json",
  "keywords": ['Developer','Courses'],
  "limit": 4
}
```

>[!TAB Balisage]

```html
<div class="featured-articles">
  <div>
    <div>source</div>
    <div><a href="/content/site/articles.json">/content/site/articles.json</a></div>
  </div>
  <div>
    <div>keywords</div>
    <div>Developer,Courses</div>
  <div>
  <div>
    <div>limit</div>
    <div>4</div>
  </div>
</div>
```

>[!TAB Tableau]

```text
+-----------------------------------------------------------------------+
| Featured Articles                                                     |
+=======================================================================+
| source   | [/content/site/articles.json](/content/site/articles.json) |
+-----------------------------------------------------------------------+
| keywords | Developer,Courses                                          |
+-----------------------------------------------------------------------+
| limit    | 4                                                          |
+-----------------------------------------------------------------------+
```

>[!ENDTABS]

#### Blocs de conteneur {#container}

Les deux structures précédentes ont une seule dimension : la liste des propriétés. Les blocs de conteneur permettent d’ajouter des enfants (généralement du même type ou modèle) et sont donc bidimensionnels. Ces blocs prennent toujours en charge leurs propres propriétés générées sous forme de lignes avec une seule colonne en premier. Elles permettent également d’ajouter des enfants, pour lesquels chaque élément est rendu en ligne et chaque propriété en colonne dans cette ligne.

Dans l&#39;exemple suivant, un bloc accepte une liste d&#39;icônes liées en tant qu&#39;enfants, où chaque icône liée comporte une image et un lien. Remarquez que la variable [identifiant de filtre](/help/implementing/universal-editor/customizing.md#filtering-components) défini dans les données du bloc afin de référencer la configuration du filtre.

>[!BEGINTABS]

>[!TAB Données]

```json
{
  "name": "Our Partners",
  "model": "text-only",
  "filter": "our-partners",
  "text": "<p>Our community of partners is ...</p>",
  "item_0": {
    "model": "linked-icon",
    "image": "/content/dam/partners/foo.png",
    "imageAlt": "Icon of Foo",
    "link": "https://foo.com/"
  },
  "item_1": {
    "model": "linked-icon"
    "image": "/content/dam/partners/bar.png",
    "imageAlt": "Icon of Bar",
    "link": "https://bar.com"
  }
}
```

>[!TAB Balisage]

```html
<div class="our-partners">
  <div>
    <div>
        Our community of partners is ...
    </div>
  </div>
  <div>
    <div>
      <picture>
         <img src="/content/dam/partners/foo.png" alt="Icon of Foo">
      </picture>
    </div>
    <div>
      <a href="https://foo.com">https://foo.com</a>
    </div>
  </div>
  <div>
    <div>
      <picture>
         <img src="/content/dam/partners/bar.png" alt="Icon of Bar">
      </picture>
    </div>
    <div>
      <a href="https://bar.com">https://bar.com</a>
    </div>
  </div>
</div>
```

>[!TAB Tableau]

```text
+------------------------------------------------------------ +
| Our Partners                                                |
+=============================================================+
| Our community of partners is ...                            |
+-------------------------------------------------------------+
| ![Icon of Foo][image0] | [https://foo.com](https://foo.com) |
+-------------------------------------------------------------+
| ![Icon of Bar][image1] | [https://bar.com](https://bar.com) |
+-------------------------------------------------------------+
```

>[!ENDTABS]

### Création de modèles de contenu sémantique pour les blocs {#creating-content-models}

Avec la variable [la mécanique de la structure en bloc,](#block-structure) il est possible de créer un modèle de contenu qui mappe le contenu persistant AEM un à un au niveau de la diffusion.

Au début de chaque projet, un modèle de contenu doit être soigneusement pris en compte pour chaque bloc. Il doit être indépendant de la source de contenu et de l’expérience de création afin de permettre aux auteurs de les changer ou de les combiner tout en réutilisant les mises en oeuvre et les styles de bloc. Vous trouverez plus de détails et de conseils généraux dans la section [David&#39;s Model (prenez 2).](https://www.aem.live/docs/davidsmodel) Plus précisément, la [collection de blocs](/help/edge/developer/block-collection.md) contient un vaste ensemble de modèles de contenu pour des cas d’utilisation spécifiques de modèles d’interface utilisateur courants.

Pour AEM la création avec des Edge Delivery Services, cela soulève la question de savoir comment servir un modèle de contenu sémantique convaincant lorsque les informations sont créées avec des formulaires composés de plusieurs champs au lieu de modifier le balisage sémantique dans un contexte tel que du texte enrichi.

Pour résoudre ce problème, trois méthodes permettent de créer un modèle de contenu attrayant :

* [Inférence de type](#type-inference)
* [Réduire le champ](#field-collapse)
* [Regroupement d’éléments](#element-grouping)

>[!NOTE]
>
>Les implémentations de blocs peuvent déconstruire le contenu et remplacer le bloc par un DOM rendu côté client. Bien que cela soit possible et intuitif pour un développeur, ce n’est pas la bonne pratique pour les Edge Delivery Services.

#### Inférence de type {#type-inference}

Pour certaines valeurs, nous pouvons déduire la signification sémantique à partir des valeurs elles-mêmes. Ces valeurs comprennent :

* **Images** - Si une référence à une ressource dans AEM est une ressource avec un type MIME commençant par `image/`, la référence est rendue comme `<picture><img src="${reference}"></picture>`.
* **Liens** - Si une référence existe dans AEM et n’est pas une image, ou si la valeur commence par `https?://`  ou `#`, la référence est rendue comme `<a href="${reference}">${reference}</a>` .
* **Texte enrichi** - Si une valeur rognée commence par un paragraphe (`p`, `ul`, `ol`, `h1`-`h6`, etc.), la valeur est rendue en texte enrichi.
* **Noms de classe** - La variable `classes` est traitée comme des options de bloc et rendue dans l’en-tête du tableau pour [des blocs simples,](#simple) ou en tant que liste de valeurs pour les éléments d’une [bloc conteneur.](#container)
* **Listes de valeurs** - Si une valeur est une propriété à plusieurs valeurs et que la première valeur ne correspond à aucune des valeurs précédentes, toutes les valeurs sont concaténées sous la forme d’une liste séparée par des virgules.

Tout le reste est rendu en texte brut.

#### Réduire le champ {#field-collapse}

La réduction des champs est le mécanisme qui permet de combiner plusieurs valeurs de champ en un seul élément sémantique, selon une convention d’affectation de nom utilisant les suffixes. `Title`, `Type`, `Alt`, et `Text` (toutes les valeurs sensibles à la casse). Toute propriété se terminant par l’un de ces suffixes ne sera pas considérée comme une valeur, mais comme un attribut d’une autre propriété.

##### Images {#image-collapse}

>[!BEGINTABS]

>[!TAB Données]

```json
{
  "image": "/content/dam/red-car.png",
  "imageAlt: "A red card on a road"
}
```

>[!TAB Balisage]

```html
<picture>
  <img src="/content/dam/red-car.png" alt="A red car on a road">
</picture>
```

>[!TAB Tableau]

```text
![A red car on a road][image0]
```

>[!ENDTABS]

##### Liens et boutons {#links-buttons-collapse}

>[!BEGINTABS]

>[!TAB Données]

```json
{
  "link": "https://www.adobe.com",
  "linkTitle": "Navigate to adobe.com",
  "linkText": "adobe.com",
  "linkType": "primary"
}
```

>[!TAB Balisage]

Non `linkType`, ou `linkType=default`

```html
<a href="https://www.adobe.com" title="Navigate to adobe.com">adobe.com</a>
```

`linkType=primary`

```html
<strong>
  <a href="https://www.adobe.com" title="Navigate to adobe.com">adobe.com</a>
</strong>
```

`linkType=secondary`

```html
<em>
  <a href="https://www.adobe.com" title="Navigate to adobe.com">adobe.com</a>
</em>
```

>[!TAB Tableau]

```text
[adobe.com](https://www.adobe.com "Navigate to adobe.com")
**[adobe.com](https://www.adobe.com "Navigate to adobe.com")**
_[adobe.com](https://www.adobe.com "Navigate to adobe.com")_
```

>[!ENDTABS]

##### Titres {#headings-collapse}

>[!BEGINTABS]

>[!TAB Données]

```json
{
  "heading": "Getting started",
  "headingType": "h2"
}
```

>[!TAB Balisage]

```html
<h2>Getting started</h2>
```

>[!TAB Tableau]

```text
## Getting started
```

>[!ENDTABS]

#### Regroupement d’éléments {#element-grouping}

while [effondrement de champ](#field-collapse) Il s’agit de combiner plusieurs propriétés en un seul élément sémantique. Le regroupement d’éléments consiste à concaténer plusieurs éléments sémantiques en une seule cellule. Cela s’avère particulièrement utile dans les cas d’utilisation où l’auteur doit être limité dans le type et le nombre d’éléments qu’il peut créer.

Par exemple, un composant de teaser peut uniquement permettre à l’auteur de créer un sous-titre, un titre et une description de paragraphe unique, combinés avec un maximum de deux boutons d’appel à l’action. Le regroupement de ces éléments génère un balisage sémantique qui peut être stylisé sans autre action.

Le regroupement d’éléments utilise une convention d’affectation des noms, selon laquelle le nom du groupe est séparé de chaque propriété du groupe par un trait de soulignement. La réduction des champs des propriétés d’un groupe fonctionne comme décrit précédemment.

>[!BEGINTABS]

>[!TAB Données]

```json
{
  "name": "teaser",
  "model": "teaser",
  "image": "/content/dam/teaser-background.png",
  "imageAlt": "A group of people sitting on a stage",
  "teaserText_subtitle": "Adobe Experience Cloud"
  "teaserText_title": "Meet the Experts"
  "teaserText_titleType": "h2"
  "teaserText_description": "<p>Join us in this ask me everything session...</p>"
  "teaserText_cta1": "https://link.to/more-details",
  "teaserText_cta1Text": "More Details"
  "teaserText_cta2": "https://link.to/sign-up",
  "teaserText_cta2Text": "RSVP",
  "teaserText_cta2Type": "primary"
}
```

>[!TAB Balisage]

```html
<div class="teaser">
  <div>
    <div>
      <picture>
        <img src="/content/dam/teaser-background.png" alt="A group of people sitting on a stage">
      </picture>
    </div>
  </div>
  <div>
    <div>
      <p>Adobe Experience Cloud</p>
      <h2>Meet the Experts</h2>
      <p>Join us in this ask me everything session ...</p>
      <p><a href="https://link.to/more-details">More Details</a></p>
      <p><strong><a href="https://link.to/sign-up">RSVP</a></strong></p>
    </div>
  </div>
</div>
```

>[!TAB Tableau]

```text
+-------------------------------------------------+
| Teaser                                          |
+=================================================+
| ![A group of people sitting on a stage][image0] |
+-------------------------------------------------+
| Adobe Experience Cloud                          |
| ## Welcome to AEM                               |
| Join us in this ask me everything session ...   |
| [More Details](https://link.to/more-details)    |
| [RSVP](https://link.to/sign-up)                 |
+-------------------------------------------------+
```

>[!ENDTABS]

## Métadonnées de sections {#sections-metadata}

De la même manière qu’un développeur peut définir et modéliser plusieurs [blocs,](#blocks) ils peuvent définir différentes sections.

Le modèle de contenu des Edge Delivery Services autorise délibérément un seul niveau d’imbrication, qui est tout contenu ou bloc par défaut contenu par une section. Cela signifie que pour disposer de composants visuels plus complexes pouvant contenir d’autres composants, ils doivent être modélisés en tant que sections et combinés à l’aide du blocage automatique côté client. Les exemples types sont les onglets et les sections réductibles, tels que les accordéons.

Une section peut être définie de la même manière qu’un bloc, mais avec le type de ressource `core/franklin/components/section/v1/section`. Les sections peuvent avoir un nom et un [identifiant du filtre,](/help/implementing/universal-editor/customizing.md#filtering-components) qui sont utilisés par la variable [Éditeur universel](/help/implementing/universal-editor/introduction.md) uniquement, ainsi qu’un [ID de modèle,](/help/implementing/universal-editor/field-types.md#model-structure) qui est utilisé pour effectuer le rendu des métadonnées de section. Le modèle est ainsi le modèle du bloc de métadonnées de section, qui sera automatiquement ajouté à une section en tant que bloc clé-valeur s’il n’est pas vide.

La variable [ID de modèle](/help/implementing/universal-editor/field-types.md#model-structure) et [identifiant de filtre](/help/implementing/universal-editor/customizing.md#filtering-components) de la section par défaut est `section`. Il peut être utilisé pour modifier le comportement de la section par défaut. L’exemple suivant ajoute des styles et une image d’arrière-plan au modèle de métadonnées de section.

```json
{
  "id": "section",
  "fields": [
    {
      "component": "multiselect",
      "name": "style",
      "value": "",
      "label": "Style",
      "valueType": "string",
      "options": [
        {
          "name": "Fade in Background",
          "value": "fade-in"
        },
        {
          "name": "Highlight",
          "value": "highlight"
        }
      ]
    },
    {
      "component": "reference",
      "valueType": "string",
      "name": "background",
      "label": "Image",
      "multi": false
    }
  ]
}
```

L&#39;exemple suivant définit une section d&#39;onglets qui peut être utilisée pour créer un bloc d&#39;onglets en combinant des sections consécutives avec un attribut de données de titre d&#39;onglet dans un bloc d&#39;onglets lors du blocage automatique.

```json
{
  "title": "Tab",
  "id": "tab",
  "plugins": {
    "xwalk": {
      "page": {
        "resourceType": "core/franklin/components/section/v1/section",
        "template": {
          "name": "Tab",
          "model": "tab",
          "filter": "section"
        }
      }
    }
  }
}
```

## Métadonnées de page {#page-metadata}

Les documents peuvent avoir une page [bloc de métadonnées,](/help/edge/authoring.md#metadata--seo) qui est utilisé pour définir laquelle `<meta>` Les éléments sont rendus dans la variable `<head>` d’une page. Les propriétés de page des pages dans AEM mappage as a Cloud Service à celles disponibles prêtes à l’emploi pour les Edge Delivery Services, comme `title`, `description`, `keywords`, etc.

Avant d’explorer plus en détail la manière de définir vos propres métadonnées, consultez les documents suivants pour comprendre d’abord le concept de métadonnées de page.

* [Métadonnées](https://www.aem.live/developer/block-collection/metadata)
* [Métadonnées en bloc](/help/edge/docs/bulk-metadata.md)

Il est également possible de définir des métadonnées de page supplémentaires de deux manières.

### Feuilles de calcul de métadonnées {#metadata-spreadsheets}

Il est possible de définir des métadonnées par chemin ou par modèle de chemin d’accès d’une manière similaire à un tableau dans AEM as a Cloud Service. Il existe une interface utilisateur de création pour les données de type tableau, similaire à Excel ou Google Sheets.

Pour créer ce tableau, créez une page et utilisez le modèle Métadonnées dans la console Sites.

Dans les propriétés de page de la feuille de calcul, définissez les champs de métadonnées dont vous avez besoin, ainsi que l’URL. Ajoutez ensuite des métadonnées par chemin de page ou modèle de chemin de page.

Assurez-vous également que la feuille de calcul est ajoutée à votre mappage de chemin avant de la publier.

```json
{
  "mappings": [
    "/content/site/:/",
    "/content/site/metadata:/metadata.json"
  ]
}
```

### Propriétés de page {#page-properties}

Il est également possible de définir un modèle de composant pour les métadonnées de page, qui sera mis à la disposition de l’auteur sous forme d’onglet dans la boîte de dialogue Propriétés de la page AEM Sites.

Pour ce faire, créez un modèle de composant avec l’ID . `page-metadata`.

```json
{
  "id": "page-metadata",
  "fields": [
    {
      "component": "text-input",
      "name": "theme",
      "label": "Theme"
    }
  ]
}
```

Certains noms de champ ont une signification spéciale et seront ignorés lors de l’activation de l’interface utilisateur de la boîte de dialogue de création :

* **`cq:tags`** - Par défaut : `cq:tags` ne sont pas ajoutées aux métadonnées. Les ajouter au `page-metadata` ajoute les ID de balise sous la forme d’une liste séparée par des virgules sous la forme `tags` meta tag à la tête.
* **`cq:lastModified`** - `cq:lastModified` ajoute ses données sous la forme `last-modified` à la tête.
