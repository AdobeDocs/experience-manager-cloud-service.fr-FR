---
title: Utilisation du sélecteur de produits et de catégories CIF
description: Découvrez comment utiliser le sélecteur de produits et de catégories CIF dans vos composants de commerce client pour aider les auteurs et les spécialistes marketing à travailler efficacement avec les données de catalogue et de produits commerciaux.
sub-product: Commerce
topics: Development
version: Cloud Service
activity: develop
audience: developer
feature: Commerce Integration Framework
exl-id: 30f1f263-1b78-46ae-99ed-61861c488b2a
source-git-commit: f5e465d90477f1b49e4ff1c5ca9dd47cc5d539bb
workflow-type: ht
source-wordcount: '623'
ht-degree: 100%

---

# Sélecteurs de création dans Content &amp; Commerce AEM {#cif-pickers}

La création dans Content &amp; Commerce AEM fournit un ensemble d’outils de création pour aider les auteurs et spécialistes marketing AEM à travailler efficacement avec les données et les catalogues de produits commerciaux. Le sélecteur de produits et le sélecteur de catégories font partie du module complémentaire CIF et sont utilisés par les composants principaux CIF. Les projets peuvent utiliser ces sélecteurs dans n’importe quelle boîte de dialogue de composant pour sélectionner des produits ou des catégories.

## Sélecteur de produits {#product-picker}

Pour utiliser le sélecteur de produits dans un composant de projet, un développeur doit ajouter `commerce/gui/components/common/cifproductfield` à une boîte de dialogue de composant. Par exemple, utilisez ce qui suit pour cq:dialog:

```xml
<product jcr:primaryType="nt:unstructured"
    sling:resourceType="commerce/gui/components/common/cifproductfield"
    fieldDescription="The product or product variant displayed by the teaser"
    fieldLabel="Select Product"
    filter="folderOrProductOrVariant"
    name="./selection"
    selectionId="sku"/>
```

Le champ de produit permet de naviguer jusqu’au produit qu’un utilisateur souhaite sélectionner dans les différentes vues. Par défaut, le champ product renvoie l’identifiant du produit, mais il peut être configuré à l’aide de l’attribut `selectionId`.

Le champ de sélecteur de produits prend en charge les propriétés facultatives suivantes :

- selectionId (id, uid, sku, slg, combinedSlug, combinedSku) : permet de choisir l’attribut de produit à renvoyer par le sélecteur (par défaut = id). L’utilisation du sku renvoie le SKU du produit sélectionné, tandis que l’utilisation de combinedSku renvoie une chaîne du type base#variant avec le SKU du produit de base et la variante sélectionnée, ou un seul SKU si un produit de base est sélectionné.
- filter (folderOrProduct, folderOrProductOrVariant) : filtre le contenu que le sélecteur soit rendre lors de la navigation dans l’arborescence du produit. folderOrProduct : effectue le rendu des dossiers et des produits. folderOrProductOrVariant : effectue le rendu des dossiers, des produits et des variantes de produits. Si un produit ou une variante de produit est rendu, il ou elle devient également sélectionnable dans le sélecteur. (par défaut = folderOrProduct)
- multiple (true, false) : permet de sélectionner un ou plusieurs produits (par défaut = false).
- emptyText : pour configurer la valeur de texte vide du champ de sélecteur.

En outre, les propriétés de champ de boîte de dialogue standard telles que `name`, `fieldLabel` ou `fieldDescription` sont également prises en charge.

>[!CAUTION]
>
>Le composant `cifproductfield` nécessite la bibliothèque cliente `cif.shell.picker` Pour ajouter une bibliothèque cliente à une boîte de dialogue, vous pouvez utiliser la propriété extraClientlibs.
>[!CAUTION]
>
>À compter de la version 2.0.0 des composants principaux CIF, la prise en charge de `id` a été supprimée et remplacée par `uid`. Nous vous recommandons vivement d’utiliser `sku` ou `slug` comme identifiant de produit. Nous continuons à prendre en charge `id` uniquement pour les projets utilisant les composants principaux CIF version 1.x.

Vous trouverez un exemple complet de `cifproductfield` dans le projet [Composants principaux CIF](https://github.com/adobe/aem-core-cif-components/blob/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/productteaser/v1/productteaser/_cq_dialog/.content.xml). Consultez également [Personnalisation des boîtes de dialogue](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html?lang=fr#customizing-dialogs) dans la documentation sur les composants principaux AEM.

## Sélecteur de catégories {#category-picker}

Le sélecteur de catégories peut également être utilisé dans une boîte de dialogue de composant de la même manière que le sélecteur de produits.

Le fragment de code suivant peut être utilisé dans une configuration cq:dialog :

```xml
<category jcr:primaryType="nt:unstructured" 
    sling:resourceType="commerce/gui/components/common/cifcategoryfield" 
    fieldLabel="Category" 
    name="./categoryId" 
    selectionId="uid" />
```

Le champ de sélecteur de catégories prend en charge les propriétés facultatives suivantes :

- selectionId(id, uid, slug, urlPath, idAndUrlPath _(obsolète)_, uidAndUrlPath _(obsolète)_) permet de choisir l’attribut de catégorie à renvoyer par le sélecteur (par défaut = id).
- multiple (true, false) : permet de sélectionner une ou plusieurs catégories (par défaut = false).

En outre, les propriétés de champ de boîte de dialogue standard telles que `name`, `fieldLabel` ou `fieldDescription` sont également prises en charge.

>[!CAUTION]
>
>Comme le composant `cifproductfield`, le composant `cifcategoryfield` nécessite également la bibliothèque clif `cif.shell.picker` Pour ajouter une bibliothèque cliente à une boîte de dialogue, vous pouvez utiliser la propriété `extraClientlibs`. Consultez [Personnalisation des boîtes de dialogue](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html?lang=fr#customizing-dialogs) dans la documentation sur les composants principaux AEM.
>[!CAUTION]
>
>À compter de la version 2.0.0 des composants principaux CIF, la prise en charge de `id` a été supprimée et remplacée par `uid`. Nous vous recommandons vivement d’utiliser `uid` ou `urlPath` comme identifiant de catégorie. Nous continuons à prendre en charge `id` et `idAndUrlPath` uniquement pour les projets utilisant les composants principaux CIF version 1.x.

Vous trouverez un exemple complet de `cifcategoryfield` dans le projet [Composants principaux CIF](https://github.com/adobe/aem-core-cif-components/blob/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/featuredcategorylist/v1/featuredcategorylist/_cq_dialog/.content.xml).
