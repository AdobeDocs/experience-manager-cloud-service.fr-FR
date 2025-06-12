---
title: Limites de l’éditeur de page
description: L’éditeur de page utilise des recouvrements pour interagir avec le contenu confiné dans un iframe. Cette interaction présente certaines limites pour l’utilisation de l’éditeur, mais également pour les développeurs et développeuses.
exl-id: 6a4f0e43-1076-4da9-95dc-9c5bf83e30d0
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 8b38e26b16c1fb565f122777f0577d332f62c39c
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 88%

---


# Limites de l’éditeur de page {#editor-limitations}

[L’éditeur de page](/help/sites-cloud/authoring/page-editor/introduction.md) utilise les recouvrements pour interagir avec le contenu confiné dans un iframe. Cette interaction présente certaines limites pour l’utilisation de l’éditeur, mais également pour les développeurs. Cette page résume ces limites et fournit des solutions ou des contournements lorsque cela s’avère possible.

## Limites fonctionnelles {#functional-limitations}

Un auteur peut être confronté aux limites fonctionnelles suivantes lors de l’utilisation de l’éditeur pour créer des pages.

### Liens inactifs {#links-not-active}

Lors de la [modification d’une page](/help/sites-cloud/authoring/page-editor/edit-content.md), les liens ne sont pas actifs.

* [Basculez vers le mode **Aperçu**](/help/sites-cloud/authoring/page-editor/introduction.md#preview-mode) pour naviguer à l’aide des liens de votre contenu.

### Pages de structure {#structure-pages}

Impossible de nommer les pages `structure`. Les pages nommées `structure` ne seront pas modifiables dans l’éditeur de page.

## Limitations de CSS {#css-limitations}

Un développeur peut être confronté aux limites suivantes concernant les interactions de l’éditeur avec CSS.

### Éléments à positionnement absolu {#absolutely-positioned-elements}

Les éléments positionnés de manière absolue peuvent entraîner des problèmes de position de leur recouvrement.

* Si cela se produit, assurez-vous que les dimensions de l’élément à positionnement absolu sont correctes, car l’éditeur crée un recouvrement avec les mêmes dimensions.

### Unités vh {#vh-units}

Les unités `vh` ne sont pas prises en charge, car la hauteur de l’iFrame doit être réglée automatiquement par AEM.

### Images d’arrière-plan fixes {#fixed-background-images}

Il est possible que les images d’arrière-plan fixes ne puissent pas être affichées en mode fixe lors du défilement, étant donné qu’elles sont incorporées dans un iFrame.

* Sélectionnez **Afficher la page comme publiée** dans les actions de la barre d’en-tête pour afficher correctement la page.

### Hauteur de 100 % {#height}

La hauteur de 100 % n’est pas prise en charge sur l’élément de corps d’une page.

* Il est possible d’appliquer une solution afin d’implémenter un corps plein écran en « étirant » l’élément de corps comme suit :

```xml
body {
    position: absolute;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
}
```

### Réduction de marge {#margin-collapsing}

Des problèmes de réduction de marge peuvent apparaître si le premier élément enfant de l’élément de corps comporte une marge.

* La solution consiste à ajouter un clearfix au niveau de l’élément de corps comme suit :

```xml
body:before, body:after{
    content: ' ';
    display: table;
}
```
