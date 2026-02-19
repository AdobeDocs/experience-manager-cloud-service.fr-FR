---
title: Configuration de l’éditeur de texte enrichi pour l’éditeur universel
description: Découvrez comment configurer l’éditeur de texte enrichi dans l’éditeur universel.
feature: Developing
role: Admin, Developer
exl-id: 350eab0a-f5bc-49c0-8e4d-4a36a12030a1
source-git-commit: 39137052e9fa409f7f5494be53fa7693aaa60b17
workflow-type: tm+mt
source-wordcount: '994'
ht-degree: 1%

---

# Configuration de l’éditeur de texte enrichi pour l’éditeur universel {#configure-rte}

Découvrez comment configurer l’éditeur de texte enrichi dans l’éditeur universel.

## Vue d’ensemble {#overview}

L’éditeur universel fournit un éditeur de texte enrichi (RTE) à la fois sur place et dans le panneau des propriétés pour permettre aux créateurs et aux créatrices d’appliquer des modifications de mise en forme lorsqu’ils modifient leur texte.

Cet éditeur de texte enrichi peut être configuré à l’aide de filtres de composant [.](/help/implementing/universal-editor/filtering.md) Ce document décrit les options de configuration disponibles, ainsi que des exemples.

>[!NOTE]
>
>Lorsque vous démarrez un projet d’éditeur universel, toutes les fonctionnalités de texte enrichi prises en charge par votre serveur principal (AEM avec une implémentation Edge Delivery ou découplée) sont automatiquement actives.
>
>* Vous pouvez désactiver les options dont vous n’avez pas besoin.
>* L’activation d’options non compatibles avec votre type de projet n’est pas prise en charge.

## Structure de configuration {#structure}

La configuration de l’éditeur de texte enrichi se compose de deux parties :

* [`toolbar`](#toolbar) : la configuration de la barre d’outils contrôle les options de modification disponibles dans l’interface utilisateur et leur organisation.
* [`actions`](#actions) : la configuration des actions vous permet de personnaliser le comportement et l’aspect des actions de modification individuelles.

Ces configurations peuvent être définies dans le cadre d’un [filtre de composant](/help/implementing/universal-editor/filtering.md) avec la propriété `rte`.

```json
[
  {
    "id": "richtext",
    "rte": {
      "toolbar": {
        // Toolbar configuration
      },
      "actions": {
        // Action-specific configurations
      }
    },
    "components": [
      "richtext"
    ]
  }
]
```

## Configuration de la barre d’outils {#toolbar}

La configuration de la barre d’outils contrôle les options de modification disponibles dans l’interface utilisateur et leur organisation. Sections disponibles

```json
{
  "toolbar": {
    // Text formatting options
    "format": ["bold", "italic", "underline", "strike"],
    // Text alignment options
    "alignment": ["left", "center", "right", "justify"],
    // Text direction options, right-to-left or left-to-right
    "direction": ["rtl", "ltr"],
    // Indentation controls
    "indentation": ["indent", "outdent"],
    // Block-level elements
    "blocks": ["paragraph", "h1", "h2", "h3", "h4", "h5", "h6", "code_block"],
    // List options
    "list": ["bullet_list", "ordered_list"],
    // Content insertion
    "insert": ["link", "unlink", "image"],
    // Superscript/subscript
    "sr_script": ["superscript", "subscript"],
    // Editor utilities
    "editor": ["removeformat"],
    // Section ordering (optional)
    "sections": ["format", "alignment", "list"]
  }
}
```

## Configuration d’action {#action}

La configuration des actions vous permet de personnaliser le comportement et l’apparence des actions de modification individuelles. Voici les sections disponibles.

### Options d’action courantes {#common-action-options}

La plupart des actions prennent en charge les options courantes suivantes :

* `shortcut?` : chaîne - remplace le raccourci clavier par défaut de l’action (le cas échéant)
* `label?` : chaîne - remplace le libellé utilisé pour l’action dans l’interface utilisateur
* `hideInline?` : booléen. Lorsqu’elle est `true`, cette action est masquée dans la barre d’outils de l’éditeur de texte enrichi contextuel (intégré)

```json
{
  "actions": {
    "bold": {
      "label": "Bold",
      "shortcut": "Mod-B",
      "hideInline": true
    }
  }
}
```

### Formater les actions {#format}

Les actions de format sont utilisées pour appliquer une mise en forme et prendre en charge le changement de balise HTML pour choisir entre des variantes sémantiques. Les sections suivantes sont disponibles.

```json
{
  "actions": {
    "bold": {
      "tag": "strong",      // Use <strong> instead of <b>
      "shortcut": "Mod-B",  // Custom keyboard shortcut
      "label": "Make Bold"  // Custom button label 
    },
    "italic": {
      "tag": "em",          // Use <em> instead of <i>
      "shortcut": "Mod-I",
      "label": "Italicize"
    },
    "strike": {
      "tag": "del"          // Use <del> instead of <s>
    }
  }
}
```

### Liste des actions {#list}

Les actions de liste prennent en charge le wrapping de contenu pour contrôler la structure HTML. Les sections suivantes sont disponibles.

```json
{
  "actions": {
    "bullet_list": {
      "wrapInParagraphs": true,    // <ul><li><p>content</p></li></ul>
      "shortcut": "Mod-Shift-8",   // Custom shortcut
      "label": "Bullet List"       // Custom label
    },
    "ordered_list": {
      "wrapInParagraphs": false,   // <ol><li>content</li></ol> (default)
      "shortcut": "Mod-Shift-9"
    }
  }
}
```

### Actions du tableau {#table-actions}

Les actions de tableau prennent en charge le renvoi à la ligne du contenu pour contrôler la structure HTML dans les cellules du tableau :

```json
{
  "actions": {
    "table": {
      "wrapInParagraphs": false, // <td>content</td> (default)
      "shortcut": "Mod-Alt-T",   // Custom shortcut
      "label": "Insert Table"    // Custom label
    }
  }
}
```

#### Options de configuration du tableau {#table-configuration-options}

* `wrapInParagraphs` : `false` (par défaut) - Les cellules du tableau contiennent du contenu de texte non enveloppé
* `wrapInParagraphs` : `true` - Les cellules de tableau encapsulent le contenu dans des balises de paragraphe

Exemples :

Si `wrapInParagraphs` : `false` :

```html
<!-- Single line -->
<td>Cell content</td>

<!-- Multiple paragraphs get <br> separation -->
<td>Line 1<br />Line 2</td>
```

Si `wrapInParagraphs` : `true` :

```html
<!-- Single paragraph -->
<td><p>Cell content</p></td>

<!-- Multiple paragraphs preserved -->
<td>
  <p>Line 1</p>
  <p>Line 2</p>
</td>
```

>[!NOTE]
>
>Lorsque vous extrayez des paragraphes (`wrapInParagraphs` : `false`), le désinfectant insère automatiquement des balises `<br>` entre plusieurs paragraphes afin de conserver les sauts de ligne visuels. Cela respecte les normes HTML et les pratiques courantes des principaux éditeurs de texte enrichi.

### Actions de lien {#link}

Les actions Lien prennent en charge le contrôle des attributs de la cible pour gérer le comportement des liens. Les sections suivantes sont disponibles.

```json
{
  "actions": {
    "link": {
      "hideTarget": false,       // Show target attribute options (default)
      "shortcut": "Mod-K",       // Custom keyboard shortcut
      "label": "Insert Link"     // Custom button label
    },
    "unlink": {
      "shortcut": "Mod-Shift-K", // Custom keyboard shortcut
      "label": "Remove Link"     // Custom button label
    }
  }
}
```

#### Options de configuration du lien {#link-options}

* `hideTarget` : `false` (par défaut) - Incluez l’attribut cible dans les liens, en autorisant les `_self`, les `_blank`, etc.
* `hideTarget` : `true` - Exclure entièrement l’attribut cible des liens

L&#39;action `unlink` n&#39;apparaît que lorsque le curseur est positionné dans un lien existant. Cela supprime la mise en forme du lien tout en conservant le contenu textuel.

### Actions sur l’image {#image}

Les actions d’image prennent en charge le renvoi à la ligne des éléments d’image pour générer un balisage d’image réactif. Les sections suivantes sont disponibles.

```json
{
  "actions": {
    "image": {
      "wrapInPicture": false,     // Use <img> tag (default)
      "shortcut": "Mod-Shift-I",  // Custom keyboard shortcut
      "label": "Insert Image"     // Custom button label
    }
  }
}
```

#### Options de configuration d’image {#image-options}

* `wrapInPicture` : `false` (par défaut) - Génération d’éléments de `<img>` simples
* `wrapInPicture` : `true` - Envelopper des images dans des éléments `<picture>` pour un design réactif

### Configuration de la mise en retrait {#indentation}

La mise en retrait possède une configuration au niveau des fonctionnalités qui contrôle la portée du comportement de mise en retrait, ainsi que des configurations d’action individuelles pour les raccourcis et les libellés.

```json
{
  "actions": {
    // Feature-level configuration
    "indentation": {
      "scope": "all"  // Controls what content can be indented (default: "all")
    },

    // Individual action configurations
    "indent": {
      "shortcut": "Tab",           // Custom keyboard shortcut
      "label": "Increase Indent"   // Custom button label
    },
    "outdent": {
      "shortcut": "Shift-Tab",     // Custom keyboard shortcut
      "label": "Decrease Indent"   // Custom button label
    }
  }
}
```

#### Options d’étendue de la mise en retrait {#indentation-options}

* `scope` : `all` (par défaut) - Le retrait/retrait négatif s’applique à tout le contenu :
   * Listes : imbriquer/désimbriquer des éléments de liste
   * Paragraphes et titres : Augmenter/diminuer le niveau général de retrait
* `scope` : `lists` - Le retrait/retrait négatif s’applique uniquement aux éléments de liste :
   * Listes : imbriquer/désimbriquer des éléments de liste
   * Paragraphes et en-têtes : pas de retrait (boutons désactivés pour ces paragraphes)

>[!NOTE]
>
>L’imbrication de listes à l’aide des touches Tab/Maj+Tab fonctionne indépendamment des paramètres de mise en retrait généraux.

### Coller en tant que texte {#paste-as-text}

L’action de l’éditeur de `paste_text` active un workflow standard de collage en tant que texte brut.

* **Raccourci par défaut :** Mod-Shift-v (Cmd+Maj+V sous macOS, Ctrl+Maj+V sous Windows/Linux)
* **Comportement :** Colle à partir de texte/brut (la mise en forme source est ignorée)
   * Dans les listes, les nouvelles lignes créent des éléments de liste.

```json
{
  "toolbar": {
    "editor": ["removeformat", "paste_text"]
  },
  "actions": {
    "paste_text": {
      "shortcut": "Mod-Shift-v",
      "label": "Paste as Text"
    }
  }
}
```

### Autres actions {#other}

Toutes les autres actions prennent en charge la personnalisation de base. Les sections suivantes sont disponibles.

```json
{
  "actions": {
    "h1": {
      "shortcut": "Mod-Alt-1",
      "label": "Large Heading"
    },
    "paragraph": {
      "shortcut": "Mod-Alt-0",
      "label": "Normal Text"
    },
    "link": {
      "shortcut": "Mod-K",
      "label": "Insert Link",
      "hideTarget": false    // Show target attribute options (default: false)
    }
  }
}
```

## Exemple complet {#example}

Voici un exemple de configuration complète.

```json
[
  {
    "id": "richtext",
    "rte": {
      // Configure which tools appear in toolbar
      "toolbar": {
        "format": [
          "bold",
          "italic"
        ],
        "blocks": [
          "paragraph",
          "h1",
          "h2"
        ],
        "list": [
          "bullet_list",
          "ordered_list"
        ],
        "insert": [
          "link",
          "unlink"
        ],
        "sections": [
          "format",
          "blocks",
          "list",
          "insert"
        ]
      },
      // Customize individual action behavior
      "actions": {
        // Format actions with HTML tag choices
        "bold": {
          "tag": "strong",
          "shortcut": "Mod-B",
          "label": "Bold"
        },
        "italic": {
          "tag": "em",
          "shortcut": "Mod-I"
        },
        // List actions with content wrapping
        "bullet_list": {
          "wrapInParagraphs": true,
          "label": "Bullet List"
        },
        "ordered_list": {
          "wrapInParagraphs": false
        },
        // Link actions with target control
        "link": {
          "hideTarget": false,
          "shortcut": "Mod-K",
          "label": "Add Link"
        },
        "unlink": {
          "label": "Remove Link"
        },
        // Other actions with basic customization
        "h1": {
          "shortcut": "Mod-Alt-1",
          "label": "Main Heading"
        }
      }
    }
  }
]
```

## Détails de l’option d’action {#action-details}

Plusieurs options comportent des détails supplémentaires qu’il est important de garder à l’esprit.

### `wrapInParagraphs` {#wrapInParagraphs}

L’option `wrapInParagraphs` des listes contrôle la structure d’HTML.

#### `wrapInParagraphs: false` (par défaut) {#wrapInParagraphs-false}

```html
<ul>
  <li>Simple text content</li>
  <li>Another item</li>
</ul>
```

#### `wrapInParagraphs: true` {#wrapInParagraphs-true}

```html
<ul>
  <li><p>Text wrapped in paragraphs</p></li>
  <li><p>Supports rich formatting within items</p></li>
</ul>
```

Utilisez `wrapInParagraphs: true` lorsque vous avez besoin de :

* Formatage enrichi dans les éléments de liste
* Plusieurs paragraphes par élément de liste
* Style cohérent au niveau du bloc

### `wrapInPicture`{#wrapinpicture}

L’option `wrapInPicture` pour les images contrôle la structure HTML générée pour le contenu de l’image.

#### wrapInPicture : false (par défaut) {#wrapinpicture-false}

```html
<img src="image.jpg" alt="Description" />
```

#### wrapInPicture : true {#wrapinpicture-true}

```html
<picture>
  <img src="image.jpg" alt="Description" />
</picture>
```

Utilisez `wrapInPicture: true` lorsque vous avez besoin de :

* Prise en charge des images réactives avec des éléments `<source>`.
* Fonctionnalités de direction artistique.
* La pérennisation des fonctionnalités d’image avancées.
* Structure cohérente d’un élément image.

>[!NOTE]
>
>Lorsque `wrapInPicture: true` est activé, les images peuvent être améliorées avec des éléments `<source>` supplémentaires pour différents formats et requêtes de média, ce qui les rend plus flexibles pour le responsive design.

### Options de la cible du lien {#link-target}

L’option `hideTarget` pour les liens contrôle si l’attribut `target` est inclus dans les liens générés et si la boîte de dialogue de création de lien inclut un champ pour la sélection de la cible.

#### `hideTarget: false` (par défaut) {#hideTarget-false}

```html
<a href="https://example.com" target="_self">Link text</a>
<a href="https://example.com" target="_blank">External link</a>
```

#### `hideTarget: true` {#hideTarget-true}

```html
<a href="https://example.com">Link text</a>
```

### Désactivation des liens sur les images {#disableforimages}

L’option `disableForImages` pour les liens contrôle si les utilisateurs peuvent créer des liens sur des images et des éléments d’image. Cela s’applique à la fois aux éléments de `<img>` intégrés et aux éléments de `<picture>` au niveau du bloc.

#### `disableForImages: false` (par défaut) {#disableforimages-false}

Les utilisateurs peuvent sélectionner des images et les encapsuler dans des liens.

```html
<!-- Inline image with link -->
<a href="https://example.com">
  <img src="image.jpg" alt="Description" />
</a>

<!-- Block-level picture with link -->
<a href="https://example.com">
  <picture>
    <img src="image.jpg" alt="Description" />
  </picture>
</a>
```

#### disableForImages : true {#disableforimages-true}

Le bouton Lien est désactivé lorsqu’une image ou une image est sélectionnée. Les utilisateurs peuvent uniquement créer des liens sur du contenu texte.

```html
<!-- Images remain standalone without links -->
<img src="image.jpg" alt="Description" />

<picture>
  <img src="image.jpg" alt="Description" />
</picture>

<!-- Links work normally on text -->
<a href="https://example.com">Link text</a>
```

Utilisez `disableForImages: true` lorsque vous souhaitez :

* Maintenez la cohérence visuelle en empêchant les images liées.
* Simplifiez la structure de contenu en séparant les images de la navigation.
* Appliquez des politiques de contenu qui limitent la liaison d’images.
* Réduisez la complexité de l’accessibilité dans votre contenu.

>[!NOTE]
>
>Ce paramètre affecte uniquement la possibilité de créer des liens sur les images. Elle ne supprime pas les liens existants des images dans le contenu.

### Options de balises {#tag}

Les actions de format permettent de basculer entre les variantes d’HTML.

| Action | Balise par défaut | Balises alternatives | Cas d’utilisation |
|---|---|---|---|
| `bold` | `<strong>` | `<b>` | Emphase sémantique et visuelle |
| `italic` | `<em>` | `<i>` | Style sémantique ou visuel |
| `strike` | `<del>` | `<s>` | Suppression visuelle ou sémantique |

Choisissez des balises sémantiques (`<strong>`, `<em>`, `<del>`) pour une meilleure accessibilité et un meilleur référencement.

### Raccourcis clavier {#keyboard-shortcuts}

Les raccourcis utilisent le ou les `Mod-Key` de format où :

* `Mod` = `Cmd` sous Mac, `Ctrl` sous Windows/Linux
* Exemples : `Mod-B`, `Mod-Shift-8`, `Mod-Alt-1`

## HTML non pris en charge {#unsupported-html}

Par défaut, les balises HTML inconnues sont supprimées lorsqu’elles sont analysées par l’éditeur. Pour les conserver, vous devez activer l&#39;option de configuration `unsupportedHtml` :

```javascript
const rteConfig = {
  unsupportedHtml: true, // preserve unknown HTML tags (default: false)
};
```

| Valeur | Comportement |
|---|---|
| `false` (par défaut) | Les balises HTML inconnues sont ignorées lors de l’analyse. |
| `true` | Les balises HTML inconnues sont enveloppées dans un nœud de bloc personnalisé non pris en charge afin que le contenu puisse faire l’objet d’un aller-retour en toute sécurité. |

Lorsqu’il est activé, l’éditeur effectue le rendu des nœuds non pris en charge avec une classe `rte-unsupported-block`. Les applications clientes doivent fournir le style de cette classe (par exemple, bordure, marge intérieure, arrière-plan). Le libellé de balise à l’intérieur du bloc utilise `rte-unsupported-label`, qui peut également être personnalisé.
