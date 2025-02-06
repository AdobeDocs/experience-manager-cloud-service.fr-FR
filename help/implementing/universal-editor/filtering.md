---
title: Filtrage des composants
description: Découvrez comment restreindre les composants autorisés par conteneur dans l’éditeur universel à l’aide de filtres de composant.
feature: Developing
role: Admin, Architect, Developer
exl-id: eeae8d7c-c563-4d9b-8c54-1098a4e98c18
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 3%

---

# Filtrage des composants {#filtering-components}

Découvrez comment restreindre les composants autorisés par conteneur dans l’éditeur universel à l’aide de filtres de composant.

## Filtres {#filters}

Lors de l’utilisation de l’éditeur universel, vous pouvez restreindre les composants autorisés par composant de conteneur. Pour ce faire, vous devez introduire une balise de script supplémentaire, qui pointe vers la définition du filtre.

```html
<script type="application/vnd.adobe.aue.filter+json" src="/static/filter-definition.json"></script>
```

Une définition de filtre peut ressembler à ce qui suit, ce qui limiterait un conteneur pour autoriser uniquement l’ajout de texte et d’images.

```json
[
  {
    "id": "container-filter",
     "components": ["text", "image"]
   }
]
```

Vous pouvez ensuite référencer la définition du filtre de votre composant de conteneur en ajoutant la propriété `data-aue-filter`, en transmettant l’identifiant du filtre que vous avez défini précédemment.

```html
data-aue-filter="container-filter"
```

La définition de l’attribut `components` dans une définition de filtre sur `null` autorise tous les composants, comme s’il n’existait aucun filtre.

```json
[
  {
    "id": "another-container-filter",
     "components": null
   }
]
```

>[!TIP]
>
>Découvrez d’autres options de personnalisation et d’extension disponibles pour l’éditeur universel dans le document [Personnalisation et extension de l’éditeur universel](/help/implementing/universal-editor/customizing.md).