---
title: Modélisation de contenu pour la création WYSIWYG avec des projets Edge Delivery Services
description: Découvrez comment fonctionne la modélisation de contenu pour la création WYSIWYG avec des projets Edge Delivery Services et comment modéliser votre propre contenu.
exl-id: e68b09c5-4778-4932-8c40-84693db892fd
feature: Edge Delivery Services
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: ht
source-wordcount: '2195'
ht-degree: 100%

---


# Modélisation de contenu pour la création WYSIWYG avec des projets Edge Delivery Services {#content-modeling}

Découvrez comment fonctionne la modélisation de contenu pour la création WYSIWYG avec des projets Edge Delivery Services et comment modéliser votre propre contenu.

## Conditions préalables {#prerequisites}

Les projets utilisant la création WYSIWYG avec Edge Delivery Services héritent de la majorité des mécanismes de tout autre projet Edge Delivery Services, indépendamment de la source de contenu ou de la [méthode de création](/help/edge/wysiwyg-authoring/authoring.md).

Avant de commencer à modéliser le contenu de votre projet, veillez à lire la documentation suivante.

* [Prise en main - Tutoriel pour l’équipe de développement](/help/edge/developer/tutorial.md)
* [Balisage, sections, blocs et blocage automatique](/help/edge/developer/markup-sections-blocks.md)
* [Collection de blocs](/help/edge/developer/block-collection.md)

Il est essentiel de comprendre ces concepts afin de trouver un modèle de contenu convaincant qui fonctionne indépendamment des sources de contenu. Ce document fournit des détails sur les mécanismes impliqués dans la création WYSIWYG.

## Contenu par défaut {#default-content}

Le **contenu par défaut** est le contenu qu’un auteur ou une autrice place intuitivement sur une page, sans ajouter de sémantique supplémentaire. Cela inclut du texte, des en-têtes, des liens et des images. Le fonctionnement et l’objectif de ce contenu sont simples et ne nécessitent guère d’explications.

Dans AEM, ce contenu est implémenté sous la forme de composants avec des modèles prédéfinis très simples, qui incluent tout ce qui peut être sérialisé en Markdown et HTML.

* **Texte** : texte enrichi (y compris les éléments de liste et le texte en gras ou en italique)
* **Titre** : texte, type (h1-h6)
* **Image** : source, description
* **Bouton** : texte, titre, URL, type (par défaut, principal, secondaire)

Le modèle de ces composants fait partie du [modèle standard pour la création WYSIWYG avec Edge Delivery Services](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-models.json#L2-L112).

## Blocs {#blocks}

Les blocs sont utilisés pour créer un contenu plus riche avec des styles et des fonctionnalités spécifiques. Contrairement au contenu par défaut, les blocs nécessitent bien une sémantique supplémentaire.

Les blocs sont fondamentalement des éléments de contenu décorés par JavaScript et mis en forme avec une feuille de style.

### Définition du modèle de bloc {#model-definition}

Lors de l’utilisation de la création WYSIWYG avec Edge Delivery Services, le contenu des blocs doit être explicitement modélisé afin de fournir au créateur ou à la créatrice l’interface pour la création de contenu. Pour l’essentiel, vous devez créer un modèle permettant à l’interface utilisateur de création de connaître les options à présenter à l’auteur ou l’autrice en fonction du bloc.

Le fichier [`component-models.json`](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-models.json) définit le modèle des blocs. Les champs définis dans le modèle de composant sont conservés sous forme de propriétés dans AEM et rendus sous forme de cellules dans le tableau qui constitue un bloc.

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

Notez que tous les blocs n’ont pas nécessairement un modèle. Certains sont simplement des [conteneurs](#container) pour une liste d’enfants, où chaque enfant a son propre modèle.

Il est également nécessaire de définir les blocs qui existent et qui peuvent être ajoutés à une page à l’aide de l’éditeur universel. Le fichier [`component-definitions.json`](/help/implementing/universal-editor/component-definition.md) répertorie les composants à mesure qu’ils sont rendus disponibles par l’éditeur universel.

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

Il est possible d’utiliser un même modèle pour de nombreux blocs. Par exemple, certains blocs peuvent partager un modèle qui définit un texte et une image.

Pour chaque bloc, l’équipe de développement :

* doit utiliser le type de ressource `core/franklin/components/block/v1/block`, l’implémentation générique de la logique de bloc dans AEM ;
* doit définir le nom du bloc, qui sera rendu dans l’en-tête de tableau du bloc ;
   * Le nom du bloc est utilisé pour récupérer le style et le script appropriés pour décorer le bloc.
* peut définir un [ID de modèle](/help/implementing/universal-editor/field-types.md#model-structure) ;
   * L’ID de modèle est une référence au modèle du composant, qui définit les champs disponibles pour la personne chargée de la création dans le panneau des propriétés.
* peut définir un [ID de filtre](/help/implementing/universal-editor/filtering.md).
   * L’ID de filtre est une référence au filtre du composant, qui permet de modifier le comportement de création, par exemple en limitant les enfants pouvant être ajoutés au bloc ou à la section, ou les fonctionnalités d’éditeur de texte enrichi qui sont activées.

Toutes ces informations sont stockées dans AEM lorsqu’un bloc est ajouté à une page. Si le type de ressource ou le nom du bloc est manquant, le bloc ne s’affiche pas sur la page.

>[!WARNING]
>
>Bien que cela soit possible, il n’est pas nécessaire ni recommandé d’implémenter des composants AEM personnalisés. Les composants pour Edge Delivery Services fournis par AEM sont suffisants et offrent certains rails de protection pour faciliter le développement.
>
>Les composants fournis par AEM sont accompagnés d’un balisage qui peut être utilisé par [helix-html2md](https://github.com/adobe/helix-html2md) lors de la publication sur Edge Delivery Services et par [aem.js](https://github.com/adobe/aem-boilerplate/blob/main/scripts/aem.js) lors du chargement d’une page dans l’éditeur universel. Le balisage constitue le contrat stable entre AEM et les autres parties du système et n’autorise pas les personnalisations. Pour cette raison, les projets ne doivent pas modifier les composants et ne doivent pas utiliser de composants personnalisés.

### Structure de bloc {#block-structure}

Les propriétés des blocs sont [définies dans les modèles de composant](#model-definition) et conservées en tant que telles dans AEM. Les propriétés sont rendues sous forme de cellules dans la structure de bloc sous forme de tableau.

#### Blocs simples {#simple}

Dans le formulaire le plus simple, un bloc effectue le rendu de chaque propriété sur une seule ligne/colonne dans l’ordre dans lequel les propriétés sont définies dans le modèle.

Dans l’exemple suivant, l’image est d’abord définie dans le modèle, puis le texte est défini. Le rendu contient ainsi l’image en premier et le texte en second.

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

Vous remarquerez peut-être que certains types de valeurs autorisent la déduction de la sémantique dans les balises et que les propriétés sont combinées dans des cellules uniques. Ce comportement est décrit dans la section [Déduction du type](#type-inference).

#### Bloc clé-valeur {#key-value}

Dans de nombreux cas, il est recommandé de décorer le balisage sémantique rendu, d’ajouter des noms de classe CSS, d’ajouter de nouveaux nœuds ou de les déplacer dans le modèle DOM et d’appliquer des styles.

Dans d’autres cas, cependant, le bloc est lu comme une configuration de type paire clé-valeur.

En voici un exemple : [métadonnées de section](/help/edge/developer/markup-sections-blocks.md#sections). Dans ce cas d’utilisation, le bloc peut être configuré pour effectuer le rendu en tant que table de paires clé-valeur. Pour en savoir plus, consultez la rubrique [Sections et métadonnées de sections](#sections-metadata).

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

Les deux structures précédentes ont une seule dimension : la liste des propriétés. Les blocs de conteneur permettent d’ajouter des enfants (généralement du même type ou modèle) et sont donc bidimensionnels. Ces blocs continuent de prendre en charge leurs propres propriétés rendues sous forme de lignes, avec une seule colonne au départ. Ils permettent également d’ajouter des enfants, pour lesquels chaque élément est rendu sous forme de ligne et chaque propriété est rendue sous forme de colonne dans cette ligne.

Dans l’exemple suivant, un bloc accepte une liste d’icônes liées en tant qu’enfants, chaque icône liée comportant une image et un lien. Remarquez l’[identifiant de filtre](/help/implementing/universal-editor/filtering.md) défini dans les données du bloc afin de référencer la configuration du filtre.

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

### Créer des modèles de contenu sémantique pour les blocs {#creating-content-models}

Une fois la [mécanique de la structure de bloc expliquée](#block-structure), il est possible de créer un modèle de contenu qui mappe le contenu conservé dans AEM avec le niveau de diffusion, de manière biunivoque.

Au début de chaque projet, il convient d’envisager attentivement le modèle de contenu de chaque bloc. Ceux-ci doivent être indépendants de la source de contenu et de l’expérience de création afin de permettre aux auteurs et autrices de les changer ou de les combiner, tout en réutilisant les implémentations et les styles de bloc. Vous trouverez plus de détails et de conseils généraux dans la section [Modèle de David (version 2)](https://www.aem.live/docs/davidsmodel). Plus précisément, la [collection de blocs](/help/edge/developer/block-collection.md) contient un vaste ensemble de modèles de contenu pour des cas d’utilisation spécifiques de modèles d’interface d’utilisation courants.

Pour la création WYSIWYG avec Edge Delivery Services, cela soulève la question de savoir comment diffuser un modèle de contenu sémantique convaincant lorsque les informations sont créées avec des formulaires composés de plusieurs champs au lieu de modifier le balisage sémantique dans un contexte tel que du texte enrichi.

Pour résoudre ce problème, trois méthodes permettent de créer un modèle de contenu convaincant :

* [Déduction de type](#type-inference)
* [Réduction du champ](#field-collapse)
* [Regroupement d’éléments](#element-grouping)

>[!NOTE]
>
>Les implémentations de blocs peuvent déconstruire le contenu et remplacer le bloc par un DOM rendu côté client. Bien que cela soit possible et intuitif pour un développeur ou une développeuse, il ne s’agit pas d’une bonne pratique pour Edge Delivery Services.

#### Déduction de type {#type-inference}

Pour certaines valeurs, la signification sémantique peut être déduite des valeurs elles-mêmes. Ces valeurs incluent les suivantes :

* **Images** : si une référence à une ressource dans AEM est une ressource avec un type MIME commençant par `image/`, la référence est rendue sous la forme `<picture><img src="${reference}"></picture>`.
* **Liens** : si une référence existe dans AEM et n’est pas une image, ou si la valeur commence par `https?://` ou `#`, la référence est rendue sous la forme `<a href="${reference}">${reference}</a>`.
* **Texte enrichi** : si une valeur rognée commence par un paragraphe (`p`, `ul`, `ol`, `h1`-`h6`, etc.), la valeur est rendue sous forme de texte enrichi.
* **Noms de classe** : la propriété `classes` est traitée sous forme d’[options de bloc](/help/edge/developer/markup-sections-blocks.md#block-options) et rendue dans l’en-tête du tableau pour des [blocs simples](#simple), ou en tant que liste de valeurs pour les éléments d’un [bloc conteneur](#container). Elle est utile si vous souhaitez [appliquer un style différent à un bloc](/help/edge/wysiwyg-authoring/create-block.md#block-options), mais que vous n’avez pas besoin de créer un bloc entièrement nouveau.
* **Listes de valeurs** : si une valeur est une propriété à plusieurs valeurs et que la première valeur ne correspond à aucune des valeurs précédentes, toutes les valeurs sont concaténées sous la forme d’une liste séparée par des virgules.

Tout le reste est rendu en texte brut.

#### Réduction du champ {#field-collapse}

La réduction des champs est le mécanisme qui permet de combiner plusieurs valeurs de champ en un seul élément sémantique, selon une convention de nommage utilisant les suffixes `Title`, `Type`, `MimeType`, `Alt` et `Text` (toutes les valeurs étant sensibles à la casse). Toute propriété se terminant par l’un de ces suffixes ne sera pas considérée comme une valeur, mais comme un attribut d’une autre propriété.

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

Pas de `linkType` ni de `linkType=default`

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

La [réduction des champs](#field-collapse) a pour but de combiner plusieurs propriétés en un seul élément sémantique. Quant au regroupement d’éléments, il consiste à concaténer plusieurs éléments sémantiques en une seule cellule. Cela se révèle particulièrement utile dans les cas d’utilisation où la personne chargée de la création doit être limitée en termes de type et de nombre d’éléments qu’il est possible de créer.

Par exemple, un composant Teaser peut autoriser la personne chargée de la création à ne créer qu’un sous-titre, un titre et une description contenant un seul paragraphe, le tout combiné avec un maximum de deux boutons d’appel à l’action. Le regroupement de ces éléments génère un balisage sémantique qui peut être mis en forme sans aucune autre action.

Le regroupement d’éléments utilise une convention de nommage selon laquelle le nom du groupe est séparé de chaque propriété du groupe par un trait de soulignement. La réduction des propriétés d’un groupe fonctionne comme décrit précédemment.

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
| ## Meet the Experts                             |
| Join us in this ask me everything session ...   |
| [More Details](https://link.to/more-details)    |
| [RSVP](https://link.to/sign-up)                 |
+-------------------------------------------------+
```

>[!ENDTABS]

## Sections et métadonnées de sections {#sections-metadata}

De la même manière qu’une équipe de développement peut définir et modéliser plusieurs [blocs](#blocks), elle peut définir différentes sections.

Le modèle de contenu de Edge Delivery Services n’autorise, à dessein, qu’un seul niveau d’imbrication, c’est-à-dire un contenu ou un bloc par défaut figurant dans une section. Cela signifie que, pour disposer de composants visuels plus complexes pouvant contenir d’autres composants, il convient de les modéliser sous forme de sections et de les combiner à l’aide du blocage automatique côté client. Les exemples types sont les onglets et les sections réductibles, comme les accordéons.

Une section peut être définie de la même manière qu’un bloc, mais avec le type de ressource `core/franklin/components/section/v1/section`. Les sections peuvent avoir un nom et un [ID de filtre](/help/implementing/universal-editor/filtering.md), qui sont utilisés par l’[éditeur universel](/help/implementing/universal-editor/introduction.md) uniquement, ainsi qu’un [ID de modèle](/help/implementing/universal-editor/field-types.md#model-structure), qui est utilisé pour effectuer le rendu des métadonnées de section. Dans ce cas, le modèle est le modèle du bloc de métadonnées de section, qui sera automatiquement ajouté à une section en tant que bloc clé-valeur s’il n’est pas vide.

L’[identifiant de modèle](/help/implementing/universal-editor/field-types.md#model-structure) et l’[identifiant de filtre](/help/implementing/universal-editor/filtering.md) de la section par défaut sont `section`. Ils peuvent être utilisés pour modifier le comportement de la section par défaut. L’exemple suivant ajoute des styles et une image d’arrière-plan au modèle de métadonnées de section.

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

L’exemple suivant définit une section d’onglets qui peut être utilisée pour créer un bloc d’onglets en combinant des sections consécutives avec un attribut de données de titre d’onglet dans un bloc d’onglets lors du blocage automatique.

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

Les documents peuvent avoir un [bloc de métadonnées](https://www.aem.live/developer/block-collection/metadata) de page, qui est utilisé pour définir les éléments `<meta>` qui sont rendus en `<head>` d’une page. Les propriétés de page des pages dans AEM as a Cloud Service sont mappées à celles disponibles et prêtes à l’emploi pour Edge Delivery Services, comme `title`, `description`, `keywords`, etc.

Avant d’explorer plus en détail la manière de définir vos propres métadonnées, consultez les documents suivants pour comprendre au préalable le concept de métadonnées de page.

* [Métadonnées](https://www.aem.live/developer/block-collection/metadata)
* [Métadonnées en bloc](/help/edge/docs/bulk-metadata.md)

Il est également possible de définir des métadonnées de page supplémentaires de deux manières.

### Feuilles de calcul de métadonnées {#metadata-spreadsheets}

Il est possible de définir des métadonnées pour chaque chemin ou pour chaque modèle de chemin de manière similaire à un tableau dans AEM as a Cloud Service. Il existe une interface utilisateur de création pour les données de type tableau, similaire aux feuilles de calcul Excel ou Google.

Pour plus d’informations, consultez le document [Utilisation de feuilles de calcul pour gérer les données tabulaires](/help/edge/wysiwyg-authoring/tabular-data.md).

### Propriétés de page {#page-properties}

La plupart des propriétés de page par défaut disponibles dans AEM sont mappées aux métadonnées de page respectives dans un document. Cela inclut par exemple `title`, `description`, `robots`, `canonical url` ou `keywords`. Certaines propriétés spécifiques à AEM sont également disponibles :

* `cq:lastModified` en tant que `modified-time` au format ISO8601.
* Heure de la dernière publication du document en tant que `published-time` au format ISO8601.
* `cq:tags` en tant que `cq-tags` comme liste séparée par des virgules des identifiants de balises.

Il est également possible de définir un modèle de composant pour les métadonnées de page personnalisées, qui sera mis à la disposition de l’auteur ou de l’autrice dans l’éditeur universel.

Pour ce faire, créez un modèle de composant avec l’identifiant `page-metadata`.

```json
{
  "id": "page-metadata",
  "fields": [
    {
      "component": "text",
      "name": "theme",
      "label": "Theme"
    }
  ]
}
```

## Étapes suivantes {#next-steps}

Maintenant que vous savez comment modéliser du contenu, vous pouvez créer des blocs pour votre propre projet de création WYSIWYG avec Edge Delivery Services.

Consultez le document [Création de blocs instrumentés pour une utilisation avec l’éditeur universel](/help/edge/wysiwyg-authoring/create-block.md) pour découvrir comment créer des blocs instrumentés pour une utilisation avec l’éditeur universel dans des projets de création WYSIWYG avec Edge Delivery Services.

Si vous savez déjà comment créer des blocs, consultez le document [Guide de prise en main du développement pour la création WYSIWYG avec Edge Delivery Services](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) pour vous familiariser avec un nouveau site Adobe Experience Manager en utilisant Edge Delivery Services et l’éditeur universel pour la création de contenu.

>[!TIP]
>
>Pour une présentation détaillée du processus de création d’un projet Edge Delivery Services activé pour la création WYSIWYG avec AEM as a Cloud Service comme source de contenu, consultez [ce webinaire AEM Gems](https://experienceleague.adobe.com/fr/docs/events/experience-manager-gems-recordings/gems2024/wysiwyg-authoring-and-edge-delivery).

