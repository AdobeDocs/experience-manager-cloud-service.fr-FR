---
title: Filtres
description: Découvrez comment définir des filtres pour limiter les options disponibles dans l’éditeur, telles que les composants disponibles, les options de l’éditeur de texte enrichi et la sélection de ressources.
feature: Developing
role: Admin, Developer
exl-id: eeae8d7c-c563-4d9b-8c54-1098a4e98c18
source-git-commit: 8d9d162ec5bba99afb1ae86252a49a9880be4e68
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 15%

---


# Filtres {#filters}

Découvrez comment définir des filtres pour limiter les options disponibles dans l’éditeur, telles que les composants disponibles, les options de l’éditeur de texte enrichi et la sélection de ressources.

## Configuration des filtres {#configuring-filters}

Lors de l’utilisation de l’éditeur universel, vous pouvez restreindre les options autorisées pour certaines fonctionnalités en définissant un filtre. Un filtre est une liste d’éléments ou d’actions disponibles pour un contexte spécifique. Par exemple, vous pouvez filtrer les composants pouvant être insérés dans un conteneur, vous pouvez [filtrer les options disponibles dans l’éditeur de texte enrichi](/help/implementing/universal-editor/configure-rte.md) et vous pouvez [filtrer les ressources disponibles](/help/implementing/universal-editor/configure-assets-selector.md) dans le sélecteur de ressources.

Les filtres doivent tous être définis de la même manière.

1. [Ajouter une balise de script pour pointer vers la définition du filtre](#add-tag)
1. [Définition du filtre](#define-filter)
1. [Référencer le filtre](#reference-filter)

Prenons un exemple de filtrage de composants par composant de conteneur.

## Définition du filtre de référence {#add-tag}

Commencez par introduire une balise de script supplémentaire, qui pointe vers la définition du filtre.

Dans notre exemple, pour filtrer les composants autorisés par conteneur, la balise peut se présenter comme suit :

```html
<script type="application/vnd.adobe.aue.filter+json" src="/static/filter-definition.json"></script>
```

## Définition du filtre {#define-filter}

Une définition de filtre contient du code JSON avec un identifiant propre au filtre et les critères de filtre.

Dans notre exemple, pour filtrer les composants autorisés par conteneur, il peut s’agir de ce qui suit, ce qui limite un conteneur à l’autorisation d’ajouter uniquement du texte et des images.

```json
[
  {
    "id": "container-filter",
    "components": ["text", "image"]
   }
]
```

La définition de l’attribut `components` dans une définition de filtre sur `null` autorise tous les composants, comme s’il n’y avait aucun filtre.

```json
[
  {
    "id": "another-container-filter",
     "components": null
   }
]
```

## Référencer le filtre {#reference-filter}

Pour utiliser le filtre, vous devez référencer la définition du filtre. Vous pouvez le faire en procédant comme suit :

* Référencez le filtre de votre composant de conteneur en ajoutant la propriété `data-aue-filter`, en transmettant l’identifiant du filtre.

  ```html
  data-aue-filter="container-filter"
  ```

* Référençant le filtre à partir de votre définition de composant [](/help/implementing/universal-editor/component-definition.md) en transmettant l’identifiant du filtre.

  ```json
  {
     "title":"My Container",
     "id":"my-container",
     "model": "my-model",
     "filter": "container-filter",
     ...
  }
  ```

## Ressources supplémentaires {#additional-resources}

Découvrez d’autres options de personnalisation et d’extension disponibles pour l’éditeur universel dans les documents suivants :

* [Configuration de l’éditeur de texte enrichi pour l’éditeur universel](/help/implementing/universal-editor/configure-rte.md)
* [Configuration des filtres pour le sélecteur Assets](/help/implementing/universal-editor/configure-assets-selector.md)
* [Personnalisation de l’éditeur universel](/help/implementing/universal-editor/customizing.md)
* [Extension de l’éditeur universel](/help/implementing/universal-editor/extending.md)
