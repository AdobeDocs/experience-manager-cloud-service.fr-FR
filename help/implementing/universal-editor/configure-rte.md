---
title: Configuration de l’éditeur de texte enrichi pour l’éditeur universel
description: Découvrez comment configurer l’éditeur de texte enrichi dans l’éditeur universel.
feature: Developing
role: Admin, Developer
exl-id: 350eab0a-f5bc-49c0-8e4d-4a36a12030a1
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 1%

---

# Configuration de l’éditeur de texte enrichi pour l’éditeur universel {#configure-rte}

Découvrez comment configurer l’éditeur de texte enrichi dans l’éditeur universel.

>[!NOTE]
>
>Cette documentation s’applique au nouvel éditeur de texte enrichi pour l’éditeur universel, disponible en tant que fonctionnalité destinée aux utilisateurs et utilisatrices précoces. Si vous souhaitez tester cette nouvelle fonctionnalité, [consultez les notes de mise à jour pour plus d’informations.](/help/release-notes/universal-editor/current.md#new-rte)

## Vue d’ensemble {#overview}

L’éditeur universel fournit un éditeur de texte enrichi (RTE) à la fois sur place et dans le panneau des propriétés pour permettre aux créateurs et aux créatrices d’appliquer des modifications de mise en forme lorsqu’ils modifient leur texte.

Cet éditeur de texte enrichi peut être configuré à l’aide de filtres de composant [.](/help/implementing/universal-editor/filtering.md) Ce document décrit les options de configuration disponibles, ainsi que des exemples.

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

## Configuration des actions {#actions}

La configuration des actions vous permet de personnaliser le comportement et l’apparence des actions de modification individuelles. Voici les sections disponibles.

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
    },
    "components": [
      "richtext"
    ]
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

### Options de la cible du lien {#link-target}

L’option `hideTarget` pour les liens contrôle si l’attribut `target` est inclus dans les liens générés et si la boîte de dialogue de création de lien inclut un champ pour la sélection de la cible.

#### `hideTarget: false` (par défaut) {#hideTarget-false}

```html
<a href="https://example.com" target="_self">Link text</a>
<a href="https://example.com" target="_blank">External link</a>
```

### `hideTarget: true` {#hideTarget-true}

```html
<a href="https://example.com">Link text</a>
```

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
