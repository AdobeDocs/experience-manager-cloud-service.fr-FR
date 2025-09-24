---
title: Balises de balisage HTML prises en charge dans le document d’enregistrement
description: Guide de référence pour les balises de balisage HTML désormais prises en charge dans la génération de document d’enregistrement, y compris le comportement de rendu et les considérations d’accessibilité
feature: Adaptive Forms
role: Developer, User
source-git-commit: 739b2b396bf0c9042d6287bfba2e8e8792cabf70
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 8%

---



# Balises de balisage HTML prises en charge dans le document d’enregistrement

## Qu’est-ce que cette référence couvre ?

AEM Forms prend désormais en charge les balises de balisage HTML dans les champs de texte enrichi lors de la génération de PDF de document d’enregistrement (DE). Ce guide explique quelles balises de balisage HTML vous pouvez utiliser en toute sécurité dans le Forms adaptatif et comment elles s’affichent dans les documents générés.

Si vous ajoutez du contenu de texte enrichi (mise en forme en gras, listes ou liens) à vos formulaires, il est important de comprendre quelles balises sont prises en charge et quelles restrictions elles peuvent comporter. Cette référence vous aide à choisir les balises appropriées pour vous assurer que votre contenu s’affiche correctement et reste accessible dans le document d’enregistrement.

## Avant de commencer

### Conditions préalables

Vous devez connaître :

- Syntaxe de base des balises HTML
- [Principes fondamentaux des documents d’enregistrement](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
- Principes d’accessibilité et directives WCAG
- Exigences d’accessibilité de PDF
- Composants de formulaire adaptatif qui acceptent le balisage HTML

### Considérations

Le document d’enregistrement peut être un PDF balisé, ce qui permet d’assurer l’accessibilité et une structure appropriée pour les technologies d’assistance. Pour activer la sortie PDF balisée, [définissez le `config/present/pdf/tagged` de propriété XCI sur `true`](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#use-a-custom-xci-file). Après avoir généré votre PDF, il est important de vérifier que les balises d’accessibilité sont correctement appliquées. Vous pouvez utiliser [Adobe Acrobat pour vérifier les balises d’accessibilité](https://helpx.adobe.com/in/acrobat/using/create-verify-pdf-accessibility.html) et vous assurer que votre document répond aux normes d’accessibilité.

### Nouveautés

La prise en charge du texte enrichi dans les documents d’enregistrement est une amélioration récente. Auparavant, le contenu de texte enrichi s’affichait en tant que texte brut dans les documents générés. Cette nouvelle fonctionnalité permet au contenu formaté de s’afficher correctement dans les sorties PDF.

## Référence de prise en charge des balises HTML

### Balises entièrement prises en charge

Ces balises sont entièrement prises en charge avec une création de nœud d’accessibilité appropriée :

| HTML Tag | Description | Prise en charge des documents d’enregistrement | Accessibilité | Exemple |
|----------|-------------|-------------|---------------|---------|
| `<p>` | Paragraphe | Oui | Prise en charge complète - Nœud de `<P>` correct | `<p>This is a paragraph.</p>` |
| `<br/>` | Saut de ligne | Oui | Prise en charge complète - dans `<P>` nœud | `<p>Line 1<br/>Line 2</p>` |
| `<b>` | Texte en gras | Oui | Prise en charge complète - dans `<P>` nœud | `<b>bold text</b>` |
| `<i>` | Texte en italique | Oui | Prise en charge complète - dans `<P>` nœud | `<i>italic text</i>` |
| `<span>` | Conteneur intégré générique | Oui | dans les éléments de bloc | `<span>styled text</span>` |
| `<sub>` | Indice | Oui | Prise en charge complète - dans les éléments de bloc | `H<sub>2</sub>O` |
| `<sup>` | Exposant | Oui | Prise en charge complète - dans les éléments de bloc | `E=mc<sup>2</sup>` |
| `<a>` | Lien hypertexte | Oui | Prise en charge limitée : nécessite une imbrication appropriée. | `<a href="url">link text</a>` |


#### Problème d’accessibilité de la liste

Le rendu de liste actuel crée des nœuds `<P>` au lieu de la structure de liste appropriée :

```
Current: <P>1. First item
Current: <P>2. Second item

Expected: <L>
Expected:   <LI>
Expected:     <LBL>1.
Expected:     <LBody>First item
```

### Balises non prises en charge

Ces balises ne sont pas prises en charge et ne s’affichent pas correctement :

| HTML Tag | Description | Solution alternative |
|----------|-------------|---------------------|
| `<h1>` - `<h6>` | Balises d’en-tête | Utiliser des balises `<p>` stylisées ou des en-têtes de niveau conception |
| `<img>` | Images | Utiliser des champs d’image ou des modèles de conception distincts |
| `<code>` | Blocs de code | Utilisation de polices à espacement fixe avec un style `<span>` |
| `<blockquote>` | Bloquer les devis | Utilisation de balises `<p>` avec mise en retrait |
| `<table>` | Tableaux | Utilisation des composants de tableau de formulaire adaptatif |

## Exemples de code

### Mise en forme de texte de base

```html
<!--  Supported - renders correctly -->
<p>This paragraph contains <b>bold text</b> and <i>italic text</i>.</p>

<!--  Supported - combined formatting -->
<p>This text is <i><b>bold and italic</b></i>.</p>

<!--  Unsupported - headings don't work -->
<h1>This won't render as a heading</h1>
```

### Listes

```html
<!-- ⚠️ Partially supported - renders but not accessible -->
<ol>
  <li>First numbered item</li>
  <li>Second numbered item</li>
</ol>

<ul>
  <li>First bullet point</li>
  <li>Second bullet point</li>
</ul>
```

### Liens

```html
<!--  Supported - but must be within block elements -->
<p>Visit our <a href="https://example.com">website</a> for more information.</p>

<!--  Incorrect - link not properly nested -->
<a href="https://example.com">Standalone link</a>
```

### Notation scientifique

```html
<!--  Supported - but limited accessibility -->
<p>Water formula: H<sub>2</sub>O</p>
<p>Einstein's equation: E=mc<sup>2</sup></p>
```

## Informations connexes

### Documentation AEM Forms

- [Générer un document d’enregistrement pour les formulaires adaptatifs](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
- [Générer un document d’enregistrement pour les composants principaux](/help/forms/generate-document-of-record-core-components.md)
- [Personnalisation du modèle de document d’enregistrement](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#customize-the-branding-information-in-document-of-record)

### Références techniques

- [Spécification XFA - Attributs XHTML et CSS](https://www.adobe.com/devnet/acrobat/pdfs/XFA-3_3.pdf) (page 1187)
- [Normes d’accessibilité PDF](https://www.w3.org/TR/WCAG21/)
- [Mappages principaux des API d’accessibilité](https://www.w3.org/TR/core-aam-1.2/#role-map-superscript)

### Guides des bonnes pratiques

- [Création de PDF accessibles](https://www.adobe.com/accessibility/pdf.html)
- [Bonnes pratiques relatives au texte enrichi dans les formulaires](/help/forms/creating-accessible-adaptive-forms.md)
- [Structure du document pour l’accessibilité](/help/forms/creating-accessible-adaptive-forms.md)

