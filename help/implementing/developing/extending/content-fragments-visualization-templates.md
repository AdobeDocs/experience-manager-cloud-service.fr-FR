---
title: Création de modèles de visualisation pour les fragments de contenu
description: Prévisualiser et publier des fragments de contenu avec des modèles de visualisation. Découvrez comment créer et personnaliser des modèles.
feature: Developing, Content Fragments
role: Admin, Developer
source-git-commit: b0a32380b028ff230ec4904a86b55b8ba0f4558f
workflow-type: tm+mt
source-wordcount: '2134'
ht-degree: 4%

---

# Fragments de contenu visuels - Modèles {#visual-content-fragments-templates}

Dans Adobe Experience Manager (AEM) as a Cloud Service, les modèles HTML peuvent être utilisés pour visualiser les fragments de contenu et les diffuser au format HTML.

Les modèles HTML vous permettent de contrôler l’affichage de vos fragments de contenu. Vous pouvez créer des modèles HTML dans l’éditeur de code de votre choix, puis les charger et les affecter aux modèles de fragment de contenu dans AEM.  Les espaces réservés de contenu utilisant Handlebars.js permettent de mapper le modèle aux types de données dans le modèle de fragment de contenu. Une fois affecté à un modèle, un modèle peut être utilisé avec n’importe quel fragment de contenu basé sur le modèle. Il permet de visualiser le fragment ou de le diffuser sous forme d’expérience modulaire au format HTML sur n’importe quel canal (web, e-mail, application mobile, etc.).

Cet article explique comment créer des modèles HTML personnalisés avec la syntaxe Handlebars pour le rendu des fragments de contenu visuel.

Après avoir créé vos modèles, vous pouvez :

* [Utilisation de modèles dans AEM](#using-a-content-fragment-html-template-in-aem)

* Utiliser l’[URL de publication de vos fragments de contenu visuel](#using-the-visual-content-fragment-publish-url)

>[!NOTE]
>
>Voir [Fragments de contenu visuel](/help/sites-cloud/administering/content-fragments/visual-content-fragments.md) pour charger, affecter et utiliser votre modèle dans AEM.

>[!NOTE]
>
>Utilisez la tâche [Figma vers fragments de contenu visuels](/help/ai-in-aem/agents/brand-experience/experience-production/figma-to-visual-content-fragments.md) pour automatiser le chargement d’une conception HTML.

## Ce que vous apprendrez {#what-you-will-learn}

Après avoir présenté (très rapidement) :

* Utilisation des modèles dans AEM
* Utilisation de l’URL de publication

Cette page aborde (plus en détail) les points suivants :

* Handlebars : principes de base de la syntaxe
* Accès aux données de fragment de contenu
* Utilisation de fragments de contenu imbriqués
* Gestion des champs à plusieurs valeurs
* Créer des boucles et une logique conditionnelle
* Bonnes pratiques de conception de modèles pour les fragments de contenu

## Conditions préalables {#prerequisites}

Pour comprendre et utiliser les technologies décrites ici, vous devez disposer des éléments suivants :

* Compréhension de base d’HTML
* Connaissance des fragments de contenu et des modèles de fragment de contenu AEM
* Compréhension de vos modèles de fragment de contenu

## Utilisation d’un modèle HTML de fragment de contenu {#using-a-content-fragment-html-template}

### Utilisation d’un modèle HTML de fragment de contenu dans AEM {#using-a-content-fragment-html-template-in-aem}

Pour plus d’informations sur l’utilisation de votre modèle dans AEM, voir :

* [Fragments de contenu visuels - Chargement et affectation de vos modèles](/help/sites-cloud/administering/content-fragments/visual-content-fragments.md)
* [Action de prévisualisation pour un fragment sélectionné, à partir de la console](/help/sites-cloud/administering/content-fragments/managing.md#actions-selected-content-fragment)
* [Prévisualiser votre fragment à partir de l’éditeur de fragments](/help/sites-cloud/administering/content-fragments/authoring.md#preview-content-fragment)

### Utilisation de l’URL de publication de fragment de contenu visuel {#using-the-visual-content-fragment-publish-url}

Une fois que vous avez créé des fragments de contenu visuel à l’aide du modèle, vous pouvez utiliser l’URL [ Publication de vos fragments de contenu visuel](/help/implementing/developing/extending/content-fragments-visualization-publish-url.md).

## Handlebars : principes de base (très) {#handlebars-the-very-basics}

Handlebars est un langage de modèle simple qui utilise des accolades doubles (crochets) `{{ }}` pour insérer du contenu dynamique dans HTML.

### Syntaxe de base {#basic-syntax}

Exemple de syntaxe Handlebars de base :

```handlebars
<!-- Output a variable (HTML-escaped) -->
{{variableName}}

<!-- Output raw HTML (unescaped) -->
{{{htmlContent}}}

<!-- Comment (not rendered) -->
{{! This is a comment }}
```

### Concepts clés {#key-concepts}

Les concepts clés de Handlebars :

| Syntaxe | Description | Quand l’utiliser |
|--- |--- |--- |
| `{{ }}` | Ignore les caractères spéciaux HTML | Métadonnées, libellés, booléens |
| `{{{ }}}` | Génère l’HTML brute (sans échappement). | Sortie de texte enrichi et de ressource |
| `{{! }}` | Commentaire Handlebars uniquement | Documentation sur les modèles |

>[!IMPORTANT]
>
> Utilisez des accolades triples (`{{{ }}}`) pour les valeurs de champ, car les valeurs sont pré-rendues dans HTML.

## Référence du contexte du modèle {#template-context-reference}

Lorsque votre modèle est rendu, il reçoit un objet de contexte contenant toutes les données sur votre fragment de contenu. Cela couvrira :

* le fragment que vous avez sélectionné
* tous les autres fragments référencés à partir de ce fragment sélectionné

  >[!NOTE]
  >
  >Les fragments peuvent être référencés :
  >
  >* dans l’interface utilisateur : jusqu’à la profondeur maximale de 5
  >* Lors de l’utilisation de l’API : la profondeur est configurable, jusqu’à la profondeur maximale de 10

### Fragment de contenu {#content-fragment}

Structure de l’objet contextuel pour le fragment de contenu (sélectionné) :

| Variable | Type | Description |
|--- |--- |--- |
| `properties` | Map | Métadonnées du fragment (voir [Structure des propriétés](#properties-structure-main-and-referenced-fragments)) |
| `fields` | Map | Accès direct aux valeurs des champs par nom |
| `allFields` | Liste | Tableau de `{name, value}` pour l’itération |
| `hasFields` | Booléen | `true` si le fragment contient des champs |

### Structure des propriétés {#properties-structure}

L’objet `properties` présente la même structure pour le fragment sélectionné et pour chaque fragment référencé.

| Propriété | Type | Description | Exemple |
|--- |--- |--- |--- |
| `id` | Chaîne | UUID du fragment | |
| `title` | Chaîne | Titre du fragment | Vélo dans le sud de l&#39;Utah |
| `description` | Chaîne | Description du fragment | Une aventure... |
| `path` | Chaîne | Chemin JCR vers le fragment | `/content/dam/...` |
| `hasDescription` | Booléen | True si la description n&#39;est pas vide | `true` |
| `createdDate` | Chaîne | Date de création ISO-8601 | |
| `modifiedDate` | Chaîne | Date de modification ISO-8601 | |
| `publishedDate` | Chaîne | Date de publication ISO-8601 | |
| `status` | Chaîne | Statut de réplication pour le niveau de publication | `DRAFT` |
| `model` | Map | Contient : `id`, `path`, `name`, `technicalName`, `description` | |
| `validationStatus` | Liste | Entrées comme `{property, message}` | |
| `previewReplicationStatus` | Chaîne | Statut de réplication pour le niveau Aperçu | |
| `tags` | Liste | Balises au niveau du fragment. Chaque élément : `id`, `title`, `titlePath`, `name`, `path`, `description` | |
| `fieldTags` | Liste | Balises au niveau du champ. Même structure que `tags`. | |

Exemples : accès aux modèles

Pour le fragment de contenu (sélectionné) :

```handlebars
{{properties.title}}, {{properties.description}}, {{{fields.field_name}}} 
```

### Fragments de contenu référencés {#referenced-content-fragments}

Structure de l’objet de contexte pour tous les fragments référencés :

| Variable | Type | Description |
|--- |--- |--- |
| `hasReferencedFragments` | Booléen | `true` lorsque des références existent |
| `referencedFragments` | Liste | Tableau d’objets de fragment référencés |
| `referencesError` | Booléen | `true` si une erreur s’est produite lors du chargement des références |
| `referencesErrorMessage` | Chaîne | Message d’erreur à l’`true` de la `referencesError` |

### Structure de fragment référencé {#referenced-fragment-structure}

Chaque élément de `referencedFragments` contient :

| Propriété | Type | Description |
|--- |--- |--- |
| `anchorId` | Chaîne | Identifiant d’ancrage sécurisé par HTML (au niveau du fragment ; il ne s’agit pas d’une propriété de fragment de contenu) |
| `properties` | Map | Métadonnées du fragment (même structure que ci-dessus) |
| `hasFields` | Booléen | Vrai si le fragment contient des champs |
| `fields` | Map | Accès direct aux champs de ce fragment |
| `allFields` | Liste | Tableau de `{name, value}` pour l’itération |

Exemples : accès au modèle pour le premier fragment de contenu référencé (premier élément de la liste indexée sur 0) :

```handlebars
{{referencedFragments.[0].anchorId}}, {{referencedFragments.[0].properties.title}}, {{referencedFragments.[0].properties.description}}
```

Ou à partir du mappage des champs :

```handlebars
{{{ fields.referenced_cf_field_name.properties.description }}}
```

## Accès aux champs de base {#basic-field-access}

L’accès direct aux champs est recommandé. Si nécessaire, vous pouvez effectuer une itération sur tous les champs.

### Accès direct aux champs (recommandé) {#direct-field-access-recommended}

Accédez directement aux champs par nom à l’aide du mappage des champs :

```handlebars
<!DOCTYPE html>
<html>
<head>
  <title>{{properties.title}}</title>
</head>
<body>
  <article>
    <h1>{{{fields.title}}}</h1>
    <p class="subtitle">{{{fields.subtitle}}}</p>
    <div class="content">
      {{{fields.description}}}
    </div>
    <div class="image">
      {{{fields.primaryImage}}}
    </div>
  </article>
</body>
</html>
```

Souvenez-vous :

* Utilisez des accolades triples `{{{ }}}` pour les valeurs de champ si elles contiennent du code HTML prérendu (texte enrichi).
* Les noms de champ (titre, sous-titre, description, primaryImage) **doivent** correspondre exactement à votre modèle de fragment de contenu **exactement**
* Les champs manquants ne sont pas rendus : aucune erreur n’est générée et la syntaxe Handlebars reste présente (et visible) dans le fragment HTML rendu

### Itérer dans tous les champs {#iterate-through-all-fields}

Utilisez `allFields` lorsque vous ne connaissez pas les noms des champs à l’avance :

```handlebars
<table>
  <thead>
    <tr>
      <th>Field Name</th>
      <th>Field Value</th>
    </tr>
  </thead>
  <tbody>
    {{#each allFields}}
    <tr>
      <td>{{name}}</td>
      <td>{{{value}}}</td>
    </tr>
    {{/each}}
  </tbody>
</table>
```

Souvenez-vous :

* `{{name}}` utilise des accolades doubles (libellé en texte brut)
* `{{{value}}}` utilise des accolades triples (valeur HTML prérendue)

## Fragments de contenu imbriqués {#nested-content-fragments}

Lorsqu’un champ de fragment de contenu fait référence à un autre fragment de contenu, vous pouvez utiliser la notation par points pour accéder directement aux champs du fragment référencé.

### Imbrication à un seul niveau {#single-level-nesting}

Exemple d’imbrication à un seul niveau :

```handlebars
<article>
  <h1>{{{fields.title}}}</h1>

  <!-- Access author (a referenced Content Fragment) -->
  <div class="author-info">
    <h3>Author</h3>
    <p>Name: {{{fields.author.name}}}</p>
    <p>Email: {{{fields.author.email}}}</p>
    <p>Bio: {{{fields.author.bio}}}</p>
  </div>

  <div class="content">
    {{{fields.content}}}
  </div>
</article>
```

Modèle : `fields.referenceFieldName.nestedFieldName`

### Imbrication à plusieurs niveaux {#multi-level-nesting}

Le système prend en charge une profondeur d’imbrication illimitée :

```handlebars
<article>
  <h1>{{{fields.title}}}</h1>

  <div class="author-details">
    <!-- Level 1: Author -->
    <p>Author: {{{fields.author.name}}}</p>

    <!-- Level 2: Author's Organization -->
    <p>Organization: {{{fields.author.organization.name}}}</p>
    <p>Website: {{{fields.author.organization.website}}}</p>

    <!-- Level 3: Organization's Address -->
    <p>Located in: {{{fields.author.organization.address.city}}},
    {{{fields.author.organization.address.country}}}</p>
  </div>

  <div class="content">
    {{{fields.content}}}
  </div>
</article>
```

Modèle : `fields.level1.level2.level3.fieldName` (profondeur limitée ; la valeur par défaut est 5, peut être étendue à 10 lors de l’utilisation de l’API)

### Paramètre d’API requis : hydratation {#api-parameter-requirements}

Pour activer l’accès aux fragments de contenu imbriqués, vous devez inclure le paramètre de requête `hydration` dans votre appel API :

Pour activer l&#39;hydratation :

```http
# Enable hydration with depth=2 for 2 levels of nesting
GET /adobe/sites/cf/fragments/{id}/preview?hydration=%7B%22enabled%22%3Atrue%2C%22maxDepth%22%3A2%7D
```

| `maxDepth` | Contenu chargé |
|--- |--- |
| `1` | Fragment principal + références directes |
| `2` | Fragment principal + références directes + leurs références |
| `3+` | Continuer jusqu&#39;à 10 niveaux |

## Champs à plusieurs valeurs {#multi-valued-fields}

Il existe plusieurs types de champs à valeurs multiples.

### Champs de texte à valeurs multiples {#multi-valued-text-fields}

Le texte, le [nombre](#multi-valued-number-fields) la date et d’autres champs simples deviennent des tableaux lorsqu’ils comportent plusieurs valeurs :

```handlebars
<article>
  <h1>{{{fields.title}}}</h1>

  <!-- Access individual items by index (use dot before bracket) -->
  <div class="tags">
    <span class="tag">{{{fields.tags.[0]}}}</span>
    <span class="tag">{{{fields.tags.[1]}}}</span>
  </div>

  <!-- Better: Iterate through all tags -->
  <div class="tags">
    {{#each fields.tags}}
    <span class="tag">{{{this}}}</span>
    {{/each}}
  </div>
</article>
```

N’oubliez pas, lors de l’accès aux éléments de tableau par index dans Handlebars :

* Utilisez :
   * `.[0]` (point avant crochet)
* Pas :
   * `[0]`

### Champs numériques à plusieurs valeurs {#multi-valued-number-fields}

Les nombres sont convertis en [chaînes](#multi-valued-text-fields) pour le rendu :

```handlebars
<div class="pricing">
  <h3>Available Prices:</h3>
  {{#each fields.prices}}
  <span class="price">${{{this}}}</span>
  {{/each}}
</div>
```

### Références à des fragments de contenu à plusieurs valeurs {#multi-valued-content-fragment-references}

Lorsqu’un champ fait référence à plusieurs fragments de contenu :

```handlebars
<div class="authors">
  <h3>Authors:</h3>
  {{#each fields.authors}}
  <div class="author">
    <h4>{{{this.name}}}</h4>
    <p>Email: {{{this.email}}}</p>
    {{#if this.bio}}
    <p class="bio">{{{this.bio}}}</p>
    {{/if}}
  </div>
  {{/each}}
</div>
```

### Références de ressources à valeurs multiples {#multi-valued-asset-references}

Les champs [Référence de contenu](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#content-reference) configurés pour les types de contenu qui sont des ressources (par exemple, des images et des documents) sont prérendus sous la forme d’HTML. Les ressources à valeurs multiples deviennent des tableaux :

```handlebars
<!-- Single asset -->
<div class="hero-image">
  {{{fields.heroImage}}}
</div>

<!-- Multi-valued: iterate through all images -->
<div class="gallery">
  {{#each fields.gallery}}
  <div class="image">{{{this}}}</div>
  {{/each}}
</div>
```

### Références à plusieurs valeurs imbriquées {#nested-multi-valued-references}

Les références à plusieurs valeurs peuvent contenir des références à plusieurs valeurs à n’importe quelle profondeur :

```handlebars
{{#each fields.chapters}}
<div class="chapter">
  <h3>Chapter: {{{this.title}}}</h3>

  {{#each this.authors}}
  <p>Author: {{{this.name}}}</p>

  {{#each this.publications}}
  <p>Publication: {{{this.title}}}</p>
  {{/each}}
  {{/each}}
</div>
{{/each}}
```

## Boucles et itération {#loops-and-iteration}

Handlebars fournit l’assistant `{{#each}}` pour effectuer une itération sur des tableaux et des objets.

### Itération sur des tableaux {#iterating-over-arrays}

Exemple d’itération sur des tableaux :

```handlebars
<!-- Simple array iteration -->
{{#each fields.tags}}
<span class="tag">{{{this}}}</span>
{{/each}}

<!-- Array of objects -->
{{#each fields.authors}}
<div class="author">
  <h4>{{{this.name}}}</h4>
  <p>{{{this.email}}}</p>
</div>
{{/each}}

<!-- With empty-state fallback -->
{{#each fields.tags}}
<span class="tag">{{{this}}}</span>
{{else}}
<p>No tags available.</p>
{{/each}}
```

### Variables spéciales dans les boucles {#special-variables-in-loops}

Dans les blocs `{{#each}}`, Handlebars fournit des variables spéciales :

```handlebars
{{#each fields.items}}
<div class="item">
  <p>Index: {{@index}}</p>     <!-- 0-based index -->
  <p>Number: {{@number}}</p>   <!-- 1-based index -->
  <p>First: {{@first}}</p>     <!-- true for first item -->
  <p>Last: {{@last}}</p>       <!-- true for last item -->
  <p>Value: {{{this}}}</p>     <!-- current item -->
</div>
{{/each}}

<!-- Example: numbered steps with first/last CSS classes -->
<ul>
  {{#each fields.steps}}
  <li class="{{#if @first}}first{{/if}} {{#if @last}}last{{/if}}">
    Step {{@number}}: {{{this}}}
  </li>
  {{/each}}
</ul>
```

### Itération sur des fragments référencés {#iterating-over-referenced-fragments}

Exemple d’itération sur des fragments référencés :

```handlebars
{{#if hasReferencedFragments}}
<section class="references">
  <h2>Related Content</h2>
  {{#each referencedFragments}}
  <article id="{{anchorId}}">
    <h3>{{title}}</h3>
    {{#if hasDescription}}
    <p>{{description}}</p>
    {{/if}}
    {{#if hasFields}}
    <ul>
      {{#each allFields}}
      <li><strong>{{name}}:</strong> {{{value}}}</li>
      {{/each}}
    </ul>
    {{/if}}
  </article>
  {{/each}}
</section>
{{/if}}
```

### Boucles imbriquées {#nested-loops}

Exemple de boucles imbriquées :

```handlebars
{{#each fields.categories}}
<section class="category">
  <h2>{{{this.name}}}</h2>

  {{#each this.products}}
  <article class="product">
    <h3>{{{this.name}}}</h3>
    <p>{{{this.description}}}</p>
  </article>
  {{/each}}
</section>
{{/each}}
```

## Rendu conditionnel {#conditional-rendering}

Utilisez des conditions pour afficher ou masquer le contenu en fonction de la disponibilité des données.

### If/Else De Base {#basic-if-else}

Exemple de concept if-else de base :

```handlebars
{{#if hasMainDescription}}
<p class="description">{{properties.description}}</p>
{{else}}
<p class="no-description">No description available.</p>
{{/if}}

<!-- Check field existence before rendering -->
{{#if fields.author}}
<div class="author">
  <p>By {{{fields.author.name}}}</p>
</div>
{{/if}}

{{#if fields.publishDate}}
<time>{{{fields.publishDate}}}</time>
{{/if}}
```

### Sauf (condition négative) {#unless-negative-conditional}

Un assistant `unless` :

```handlebars
<!-- Show author unless explicitly hidden -->
{{#unless fields.hideAuthor}}
<div class="author">{{{fields.author.name}}}</div>
{{/unless}}
```

### Conditions imbriquées {#nested-conditials}

Exemple de condition imbriquée :

```handlebars
{{#if fields.author}}
<div class="author">
  <h3>{{{fields.author.name}}}</h3>

  {{#if fields.author.bio}}
  <p class="bio">{{{fields.author.bio}}}</p>
  {{/if}}

  {{#if fields.author.website}}
  <a href="{{{fields.author.website}}}">Visit Website</a>
  {{/if}}
</div>
{{/if}}
```

## Assistants Handlebars intégrés {#built-in-handlebars-helpers}

Handlebars comprend plusieurs assistants intégrés, au-delà des `{{#if}}` et des `{{#each}}`.

| Helper | Description |
|--- |--- |
| `{{#if condition}}` | Rend le contenu si la condition est vraie. Valeurs Falsy : `false`, `undefined`, `null`, `0`, `""`, `[]` |
| `{{#unless condition}}` | Rend le contenu si la condition est fausse (inverse de `#if`) |
| `{{#each array}}` | Répète le contenu pour chaque élément ; prend en charge les `{{else}}` pour les tableaux vides. |
| `{{#with object}}` | Crée une portée pour un objet imbriqué, ce qui réduit la répétition du chemin d’accès |
| `{{lookup this "key"}}` | Recherche dynamique d’une propriété par nom |

### Avec le helper {#with-helper}

Crée une portée pour les objets imbriqués afin de réduire les préfixes de chemin répétitifs :

```handlebars
{{#with fields.author}}
<div class="author">
  <h3>{{{name}}}</h3>     <!-- same as fields.author.name -->
  <p>{{{email}}}</p>      <!-- same as fields.author.email -->
  <p>{{{bio}}}</p>        <!-- same as fields.author.bio -->
</div>
{{/with}}

<!-- Useful for deeply nested objects -->
{{#with fields.author.organization}}
<div class="organization">
  <h4>{{{name}}}</h4>
  <p>{{{website}}}</p>
  {{#with address}}
  <address>
    {{{street}}}<br/>
    {{{city}}}, {{{country}}}
  </address>
  {{/with}}
</div>
{{/with}}
```

## Modèles avancés {#advanced-patterns}

Voici quelques exemples de modèles avancés.

### Accès au contexte parent dans les boucles imbriquées {#accessing-parent-context-in-nested-loops}

Utilisez `../` pour accéder à la portée parente à partir d’une boucle imbriquée :

```handlebars
<h1>{{{fields.title}}}</h1>

{{#each fields.chapters}}
<section class="chapter">
  <h2>Chapter {{@number}}: {{{this.title}}}</h2>

  {{#each this.sections}}
  <article>
    <!-- Access parent chapter via ../ -->
    <p>Chapter: {{{../title}}}</p>

    <!-- Access root context via ../../ -->
    <p>Book: {{{../../fields.title}}}</p>

    <h3>{{{this.title}}}</h3>
    <div>{{{this.content}}}</div>
  </article>
  {{/each}}
</section>
{{/each}}
```

### Classes CSS dynamiques {#dynamic-css-classes}

Exemple de classes CSS dynamiques :

```handlebars
<article class="content-fragment {{#if hasMainDescription}}with-description{{/if}} {{#if hasReferencedFragments}}has-refs{{/if}}">
  <h1>{{properties.title}}</h1>
</article>

<ul class="tag-list">
  {{#each fields.tags}}
  <li class="tag {{#if @first}}first{{/if}} {{#if @last}}last{{/if}}">
    {{{this}}}
  </li>
  {{/each}}
</ul>
```

## Exemples complets {#complete-examples}

Plusieurs exemples complets sont fournis à titre de référence.

### Billet de blog avec l’auteur

Un article de blog contenant des informations sur l’auteur :

```handlebars
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>{{properties.title}}</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 40px; }
    .author-card { background: #f5f5f5; padding: 20px; border-radius: 8px; }
    .tags { display: flex; gap: 10px; }
    .tag { background: #007bff; color: white; padding: 5px 10px; border-radius: 4px; }
  </style>
</head>
<body>
  <article>
    <header>
      <h1>{{{fields.title}}}</h1>
      {{#if fields.publishDate}}
      <time datetime="{{{fields.publishDate}}}">{{{fields.publishDate}}}</time>
      {{/if}}
      {{#if fields.tags}}
      <div class="tags">
        {{#each fields.tags}}
        <span class="tag">{{{this}}}</span>
        {{/each}}
      </div>
      {{/if}}
    </header>

    {{#if fields.heroImage}}
    <figure>
      {{{fields.heroImage}}}
      {{#if fields.imageCaption}}
      <figcaption>{{{fields.imageCaption}}}</figcaption>
      {{/if}}
    </figure>
    {{/if}}

    <div class="content">
      {{{fields.content}}}
    </div>

    {{#if fields.author}}
    <aside class="author-card">
      <h3>About the Author</h3>
      <h4>{{{fields.author.name}}}</h4>
      {{#if fields.author.profilePicture}}
      <div class="author-image">{{{fields.author.profilePicture}}}</div>
      {{/if}}
      {{#if fields.author.bio}}
      <p>{{{fields.author.bio}}}</p>
      {{/if}}
      {{#if fields.author.email}}
      <p>Contact: <a href="mailto:{{{fields.author.email}}}">{{{fields.author.email}}}</a></p>
      {{/if}}
    </aside>
    {{/if}}
  </article>
</body>
</html>
```

Appel API requis :

```http
GET /adobe/sites/cf/fragments/{id}/preview?hydration=%7B%22enabled%22%3Atrue%2C%22maxDepth%22%3A1%7D
```

### Vue de tableau générique (aucune connaissance préalable des champs) {#generic-table-view-no-prior-knowledge-of-fields}

Une vue de tableau générique, sans connaissance inhérente des champs. Le est similaire au modèle **générique** :

```handlebars
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>{{properties.title}}</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 40px; }
    table { width: 100%; border-collapse: collapse; margin: 20px 0; }
    th, td { border: 1px solid #ddd; padding: 12px; text-align: left; }
    th { background-color: #f4f4f4; font-weight: bold; }
    .ref-section { background: #f9f9f9; padding: 20px; margin: 20px 0; border-radius: 8px; }
  </style>
</head>
<body>
  <header>
    <h1>{{properties.title}}</h1>
    {{#if properties.description}}<p>{{properties.description}}</p>{{/if}}
    <p><small>Path: {{properties.path}}</small></p>
  </header>

  {{#if hasFields}}
  <section>
    <h2>Fields</h2>
    <table>
      <thead>
        <tr><th>Field Name</th><th>Field Value</th></tr>
      </thead>
      <tbody>
        {{#each allFields}}
        <tr>
          <td><strong>{{name}}</strong></td>
          <td>{{{value}}}</td>
        </tr>
        {{/each}}
      </tbody>
    </table>
  </section>
  {{/if}}

  {{#if hasReferencedFragments}}
  <section class="ref-section">
    <h2>Referenced Content Fragments</h2>
    {{#each referencedFragments}}
    <article id="{{anchorId}}" style="margin-bottom: 30px;">
      <h3>{{title}}</h3>
      {{#if hasDescription}}<p>{{description}}</p>{{/if}}
      <p><small>Path: {{path}}</small></p>
      {{#if hasFields}}
      <table>
        <thead>
          <tr><th>Field Name</th><th>Field Value</th></tr>
        </thead>
        <tbody>
          {{#each allFields}}
          <tr>
            <td><strong>{{name}}</strong></td>
            <td>{{{value}}}</td>
          </tr>
          {{/each}}
        </tbody>
      </table>
      {{/if}}
    </article>
    {{/each}}
  </section>
  {{/if}}
</body>
</html>
```

## Bonnes pratiques {#best-practices}

Les bonnes pratiques incluent :

1. Utilisez toujours des accolades triples pour les valeurs de champ qui contiennent du contenu de balisage HTML.

   * Les valeurs des champs sont des HTML pré-rendues.

     >[!NOTE]
     >
     >Les accolades doubles affichent les balises HTML brutes sous forme de texte brut.

   ```handlebars
   <!-- CORRECT -->
   {{{fields.description}}}
   
   <!-- WRONG - displays HTML tags as text -->
   {{fields.description}}
   ```

1. Vérifier l’existence avant d’accéder aux champs imbriqués.

   ```handlebars
   <!-- GOOD: check before accessing nested fields -->
   {{#if fields.author}}
   <p>By {{{fields.author.name}}}</p>
   {{/if}}
   
   <!-- RISKY: may render empty if author is not set -->
   <p>By {{{fields.author.name}}}</p>
   ```

1. Utilisez un accès direct aux champs lorsque cela est possible.

   * Elle est plus lisible et gérable que l’itération de `allFields` et la correspondance par nom.

1. Structurer les modèles avec des commentaires de section.

   ```handlebars
   {{! ===== HEADER SECTION ===== }}
   <header>
     <h1>{{properties.title}}</h1>
   </header>
   
   {{! ===== MAIN CONTENT ===== }}
   <main>
     {{#if hasFields}}
     <!-- fields rendering -->
     {{/if}}
   </main>
   
   {{! ===== REFERENCES ===== }}
   {{#if hasReferencedFragments}}
   <!-- references rendering -->
   {{/if}}
   ```

1. Gérez les données manquantes avec élégance et avec des solutions de secours.

   ```handlebars
   {{#if fields.title}}
   <h1>{{{fields.title}}}</h1>
   {{else}}
   <h1>Untitled</h1>
   {{/if}}
   ```

1. Utilisez toujours une structure de document HTML appropriée.

   ```handlebars
   <!DOCTYPE html>
   <html lang="en">
   <head>
     <meta charset="UTF-8">
     <meta name="viewport" content="width=device-width, initial-scale=1">
     <title>{{properties.title}}</title>
   </head>
   <body>
     <!-- your content here -->
   </body>
   </html>
   ```

1. Testez avec divers scénarios de contenu :

   * Tous les champs sont entièrement renseignés
   * Champs facultatifs manquants
   * Champs à plusieurs valeurs vides
   * Imbrication profonde (plusieurs niveaux)
   * Références dont le chargement échoue

1. Utiliser des éléments sémantiques d’HTML :

   * Pour une meilleure accessibilité, utilisez `<article>`, `<header>`, `<main>`, `<footer>`, `<time>`, `<address>` ou toute autre méthode similaire.

1. Conserver les styles dans CSS.

   * Utilisez des balises `<style>` ou des feuilles de style externes.
   * Évitez autant que possible les styles intégrés.

1. Logique complexe du document :

   * Utilisez les commentaires Handlebars `({{! }})`.
   * N’utilisez pas les commentaires HTML qui apparaissent dans la sortie rendue.

## Résolution des problèmes {#troubleshooting}

Voici quelques conseils de dépannage :

| Problème | Symptôme | Solution |
|--- |--- |--- |
| Le champ affiche les balises HTML sous forme de texte. | `<p>Hello World</p>` affiché littéralement | Utiliser des accolades triples : `{{{fields.description}}}` |
| Les champs de fragment de contenu imbriqués sont vides ou affichent [ Objet ] | `{{{fields.author.name}}}` est vide | Activer l’hydratation dans l’appel API ; vérifier l’orthographe du nom du champ ; vérifier que la `maxDepth` est suffisamment profonde |
| Le champ à valeurs multiples affiche uniquement le premier élément | Un tableau comportant cinq éléments n’en affiche qu’un seul | Utiliser `{{#each fields.tags}}` pour itérer tous les éléments |
| L’accès à l’index de tableau ne fonctionne pas. | `{{{fields.tags[0]}}}` rend vide | Utilisez une syntaxe entre points : `{{{fields.tags.[0]}}}` |
| Les fragments référencés n’apparaissent pas | `hasReferencedFragments` est toujours faux | Activer l&#39;hydratation : `?hydration=%7B%22enabled%22%3Atrue%7D;` également vérifier `{{#if referencesError}}` |
| Le modèle ne renvoie rien. | Page vide ou sortie vide | Rechercher les blocs `{{#if}}` ou `{{#each}}` non fermés ; ajouter une sortie de diagnostic : `<pre>hasFields: {{hasFields}} \| title: {{properties.title}}</pre>` |
| Les commentaires s’affichent dans la page rendue | Texte de commentaire HTML visible par les utilisateurs finaux | Utiliser des commentaires Handlebars `{{! comment }}` lieu de `<!-- comment -->` HTML |
| Conditionnel est toujours évalué sur vrai | `{{#if fields.enabled}}` est toujours vrai | Remarque : la chaîne `"false"` est vraie dans Handlebars. Seuls les `false`, `null`, `undefined`, `0`, `""` et `[]` réels sont faux. |
| Caractères spéciaux rendus en tant qu’entités | `&lt;`, `&amp;` affiché au lieu de `<`, `&` | Utilisez des accolades triples pour le contenu HTML prérendu : `{{{fields.content}}}` |
| Impossible d&#39;accéder à la variable de boucle externe depuis la boucle interne | La variable du `#each` parent est indéfinie | Utiliser `../` pour la portée parente : `{{{../name}}}` ; utiliser `../../` pour les grands-parents |
| Liste vide n’affichant pas le message de secours | Un champ à plusieurs valeurs contenant zéro élément n’affiche rien | Utiliser `{{else}}` à l’intérieur des `{{#each}}` : `{{#each fields.tags}}...{{else}}<p>No tags</p>{{/each}}` |

### Utilisation des ressources {#working-with-assets}

Assets référencé à partir des fragments de contenu est prérendu en tant qu’HTML par AEM. Par conséquent, les accolades triples sont obligatoires pour toutes les références de ressources.

| Type de ressource | Rendu en tant que |
|--- |--- |
| Images | `<img src="..." alt="...">` |
| Vidéos | élément `<video>` |
| Documents | `<a href="...">` le lien |

Souvenez-vous :

* Utilisez toujours des accolades triples pour les champs de ressource.L’utilisation de doubles accolades permet d’échapper la balise HTML générée et de l’afficher en tant que texte brut plutôt que d’effectuer le rendu de l’image, de la vidéo ou du lien.

### Utilisation des champs des ressources {#asset-field-usage}

Exemple d’utilisation des champs de ressource :

```handlebars
<!-- CORRECT - triple braces render the image -->
{{{fields.heroImage}}}
<!-- Output: <img src="path/to/image.jpg" alt="Hero"> -->

<!-- WRONG - double braces escape the tag, showing it as text -->
{{fields.heroImage}}
<!-- Output: &lt;img src="path/to/image.jpg" alt="Hero"&gt; -->
```

## Assistants de modèles personnalisés {#customer-template-helpers}

Le système fournit des assistants Handlebars personnalisés pour générer des éléments HTML avec des attributs HTML personnalisés. Ces assistants vous permettent de contrôler les balises générées, tout en gérant la complexité de l’extraction des URL sources du contenu prérendu.

Assistants disponibles :

1. `asset` - Génère des balises `<img>` avec des attributs personnalisés
1. `text` - Génère des balises `<span>` qui encapsulent le contenu textuel avec des attributs personnalisés

### assistant `asset` {#asset-helper}

Syntaxe :

```handlebars
{{{asset fieldValue attribute1="value1" attribute2="value2"}}}
```

Souvenez-vous :

* Utilisez des accolades triples `{{{ }}}` avec l’assistant de ressources, et non des accolades doubles !

#### Quatre exemples de base {#four-basic-examples}

Voici quatre exemples de base :

```handlebars
<!-- Add a CSS class to an image -->
{{{asset fields.heroImage class="hero-image"}}}
<!-- Output: <img src="..." alt="..." class="hero-image"> -->

<!-- Add multiple CSS classes -->
{{{asset fields.productImage class="product-img responsive shadow"}}}

<!-- Add id and class -->
{{{asset fields.logo class="brand-logo" id="main-logo"}}}

<!-- Add data attributes -->
{{{asset fields.thumbnail class="thumb" data-category="product" data-id="123"}}}
```

#### Attributs pris en charge {#supported-attributes}

Vous pouvez ajouter n’importe quel attribut HTML valide :

| Attribut |  Exemple |
|--- |--- |
| `class` | `class="my-class another-class"` |
| `id` | `id="unique-id"` |
| `alt` | `alt="Custom alt text" (overrides existing alt)` |
| `data-*` | `data-index="1" data-type="hero"` |
| `aria-*` | `aria-label="Description" aria-hidden="true"` |
| `width` | `width="300"` |
| `height` | `height="200"` |
| `loading` | `loading="lazy"` |
| `style` | `style="border-radius: 8px;"` |

#### Remplacer le texte de remplacement {#override-alt-text}

L’attribut `alt` de l’image d’origine peut être remplacé :

```handlebars
{{{asset fields.photo alt="Custom description for accessibility"}}}
```

#### Exemple complexe {#complex-example}

Voici un exemple complexe :

```handlebars
<article class="blog-post">
<header>
{{{asset fields.featuredImage 
class="featured-image responsive" 
id="post-hero"
loading="lazy"
data-post-id="12345"}}}
</header>
</article>
```

#### Utilisation des boucles with {#using-with-loops}

Asset helper dans les boucles :

```handlebars
{{#each fields.galleryImages}}
{{{asset this class="gallery-item" data-index=@index}}}
{{/each}}
```

### assistant `text` {#text-helper}

L’assistant de texte génère une balise `<span>` enveloppant le contenu textuel avec des classes CSS et des attributs HTML personnalisés. Utile pour mettre en forme des champs de texte individuels.

Syntaxe :

```handlebars
{{{text fieldValue attribute1="value1" attribute2="value2"}}}
```

Souvenez-vous :

* Utilisez des accolades triples `{{{ }}}` avec l’assistant de texte, et non des accolades doubles !

#### Trois exemples de base {#three-basic-examples}

Voici trois exemples de base :

```handlebars
<!-- Add a CSS class to text -->
{{{text fields.title class="article-title"}}}
<!-- Output: <span class="article-title">The Title Text</span> -->

<!-- Add multiple attributes -->
{{{text fields.price class="price-tag" id="product-price" data-currency="USD"}}}

<!-- Style inline text -->
{{{text fields.highlightedText class="highlighted" style="background: yellow;"}}}
```

#### Cas d’utilisation courants {#common-use-cases}

Voici quelques cas d’utilisation courants :

```handlebars
<!-- Styling article metadata -->
<article>
<header>
{{{text fields.category class="category-badge"}}}
<h1>{{{fields.title}}}</h1>
{{{text fields.author class="byline"}}}
{{{text fields.publishDate class="date"}}}
</header>
</article>

<!-- Creating styled labels -->
<div class="product-card">
{{{text fields.productName class="product-name"}}}
{{{text fields.brand class="brand-label" data-brand-id="abc"}}}
{{{text fields.price class="price" id="main-price"}}}
</div>

<!-- Accessibility enhancements -->
{{{text fields.importantNote class="alert" role="alert" aria-live="polite"}}}
```

#### Avec des boucles {#with-loops}

Un cas d’utilisation courant avec des boucles comprend :

```handlebars
{{#each fields.tags}}
{{{text this class="tag-badge"}}}
{{/each}}
```

### Helpers - Validation des attributs {#helpers-attribute-validation}

Les deux assistants valident les noms d’attribut avant de les inclure dans la sortie.

Noms d’attributs valides :

* Doit commencer par une lettre (a-z, A-Z)
* Ne peut contenir que des lettres, des chiffres, des tirets et des traits de soulignement. Consultez la section [Conventions de dénomination](/help/implementing/developing/introduction/naming-conventions.md)
* Insensible à la casse
* Par exemple :
   * Valide :
      * `class`, `id`, `data-value`, `aria-label`, `my_attr`, `dataIndex1`
   * Non valide :
      * `123-attr`, `-class`, `@special`, `$money`

Les noms d’attribut non valides sont silencieusement ignorés avec un avertissement dans les journaux :

```handlebars
{{{asset fields.image class="valid" 123-invalid="skipped" id="also-valid"}}}
<!-- Output: <img src="..." alt="..." class="valid" id="also-valid"> -->
<!-- 123-invalid is skipped because it starts with a number -->
```

Souvenez-vous :

* Recherchez dans les journaux du serveur les avertissements « Format de nom d’attribut non valide bloqué ».

## Comparaison de la sortie directe aux assistants {#comparing-direct-output-to-helpers}

Quand utiliser les `{{{fields.xxx}}}` de sortie directe :

* Vous n’avez pas besoin de définir de style personnalisé
* Vous souhaitez obtenir la sortie par défaut en l’état
* Le champ contient des HTML complexes que vous ne souhaitez pas modifier

Quand utiliser les assistants :

* Vous devez ajouter des classes CSS pour le style
* Vous devez ajouter des attributs HTML personnalisés (`data-*`, `aria-*` et autres)
* Vous souhaitez une structure HTML cohérente et contrôlée

Comparaison :

```handlebars
<!-- Direct output - uses whatever HTML the system generates -->
{{{fields.heroImage}}}
<!-- Output: <img src="/path/image.jpg" alt="Hero Image"> -->

<!-- With asset helper - full control over attributes -->
{{{asset fields.heroImage class="hero responsive" id="main-hero" loading="lazy"}}}
<!-- Output: <img src="/path/image.jpg" alt="Hero Image" class="hero responsive" id="main-hero" loading="lazy"> -->
```

## Référence rapide {#quick-reference}

Certaines informations de référence rapide sont fournies à titre de référence.

### Variables contextuelles {#context-variables}

Les variables contextuelles :

```handlebars
{{properties}}                <!-- Main fragment metadata -->
{{fields}}                    <!-- Map keyed by field name to rendered values (such as strings, lists, nested maps for Content Fragment references, commerce maps, HTML, and others) -->
{{allFields}}                 <!-- List of { name, value } maps (uniform iteration) -->
{{hasFields}}.                <!-- Boolean -->
{{hasReferencedFragments}}.   <!-- Boolean -->
{{referencedFragments}}       <!-- List of referenced-fragment maps -->
```

### Accès aux champs {#field-access}

Accès aux champs :

```handlebars
{{{fields.fieldName}}}                    <!-- Direct field -->
{{{fields.author.name}}}                  <!-- Nested Content Fragment field -->
{{{fields.author.org.address.city}}}      <!-- Multi-level nesting -->
{{{fields.tags.[0]}}}                     <!-- Array by index -->
{{#each fields.tags}}...{{/each}}         <!-- Array iteration -->
{{{fields.authors.[0].name}}}             <!-- Multi-valued Content Fragment reference -->
```

### Flux de contrôle {#control-flow}

Le flux de contrôle :

```handlebars
{{#if condition}}...{{/if}}               <!-- Conditional -->
{{#if condition}}...{{else}}...{{/if}}    <!-- If/else -->
{{#unless condition}}...{{/unless}}       <!-- Negative conditional -->
{{#each array}}...{{/each}}               <!-- Iteration -->
{{#each array}}...{{else}}...{{/each}}    <!-- Iteration with fallback -->
{{#with object}}...{{/with}}              <!-- Change scope -->
```

### Variables en boucle {#loop-variables}

Les variables de boucle :

```handlebars
{{@index}}        <!-- 0-based index -->
{{@number}}       <!-- 1-based index -->
{{@first}}        <!-- true for first item -->
{{@last}}         <!-- true for last item -->
{{@key}}          <!-- Object property name -->
{{this}}          <!-- Current item -->
{{../parent}}     <!-- Access parent scope -->
```

### Assistants de modèles personnalisés {#custom-template-helpers}

Les assistants de modèle personnalisé :

```handlebars
{{{asset fields.image class="css-class"}}}                <!-- Image with class -->
{{{asset fields.image class="c1" id="my-id"}}}            <!-- Image with multiple attrs -->
{{{asset fields.image alt="Custom alt text"}}}            <!-- Override alt text -->
{{{asset fields.image loading="lazy" data-x="val"}}}      <!-- Custom attributes -->

{{{text fields.title class="title-class"}}}               <!-- Span with class -->
{{{text fields.price class="price" id="p1"}}}             <!-- Span with multiple attrs -->
{{{text this class="item" data-index=@index}}}            <!-- In loops -->
```

## Ressources supplémentaires {#additional-resources}

Des ressources supplémentaires sont disponibles :

* [Documentation Handlebars](https://handlebarsjs.com/)
* [Assistants intégrés Handlebars](https://handlebarsjs.com/guide/builtin-helpers.html)
* [Documentation sur les fragments de contenu AEM](/help/sites-cloud/administering/content-fragments/overview.md)
* [API de modèles de visualisation de fragments de contenu](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/cvt/)

