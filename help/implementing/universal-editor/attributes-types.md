---
title: Attributs et types d’élément
description: Découvrez les attributs de données et les types d’éléments requis par Universal Editor.
exl-id: 02795a31-244a-42b4-8297-2649125d7777
feature: Developing
role: Admin, Architect, Developer
source-git-commit: edef86c67becf3b8094196d39baa9e69d6c81777
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 45%

---


# Attributs et types {#attributes-types}

Découvrez les attributs de données et les types d’éléments requis par Universal Editor.

## Présentation {#introduction}

Pour que l’éditeur universel puisse modifier une application, cette dernière doit être correctement instrumentée. L’application doit inclure des métadonnées appropriées afin que l’éditeur puisse en modifier le contenu. Ce document décrit les attributs et les types d’éléments de ces métadonnées.

>[!NOTE]
>
>La validation du contenu se produit côté serveur. L’éditeur universel fonctionne simplement avec les attributs de données. La validation qu’elles correspondent au modèle/à la structure doit être traitée au niveau de l’API.

## Propriétés des données {#data-properties}

| Propriété des données | Description |
|---|---|
| `data-aue-resource` | URN de la ressource : consultez la section [Instrumenter la page du document Prise en main de l’éditeur universel dans AEM](getting-started.md#instrument-thepage). |
| `data-aue-prop` | Attribut de la ressource : consultez la section [Instrumenter la page du document Prise en main de l’éditeur universel dans AEM](getting-started.md#instrument-thepage). |
| `data-aue-type` | [Type de l’élément modifiable](#item-types) (par exemple, texte, image et référence) |
| `data-aue-filter` | Définit :<br> - Quelles fonctionnalités d’éditeur de texte enrichi sont activées<br> - Quels composants peuvent être ajoutés à un conteneur<br> - Quelles ressources peuvent être ajoutées à un type de média ? |
| `data-aue-label` | Définit un libellé personnalisé pour un élément sélectionnable affiché dans l’éditeur. |
| `data-aue-model` | Définit un modèle utilisé pour la modification d’après les formulaires dans le panneau des propriétés. |
| `data-aue-behavior` | Définit le [comportement d’une instrumentation](#behaviors) ; par exemple, un texte ou une image autonome peut également imiter un composant pour le rendre modifiable ou pouvant être supprimé. |

## Types d’éléments {#item-types}

| `data-aue-type` | Description | `data-aue-resource` | `data-aue-prop` | `data-aue-filter` | `data-aue-label` | `data-aue-model` | `data-aue-behavior` |
|---|---|---|---|---|---|---|---|
| `text` | Le texte est modifiable dans les balises HTML, mais uniquement dans un format de texte simple, sans mise en forme de texte enrichi. Ce format est généralement utilisé sur les composants de titre. | Facultatif | Requis | n/a | Facultatif | n/a | Facultatif |
| `richtext` | Le texte est modifiable avec des fonctionnalités de texte enrichi complètes. L’éditeur de texte enrichi s’affiche dans le panneau de droite | Facultatif | Requis | n/a | Facultatif | n/a | Facultatif |
| `media` | Le modifiable est une ressource, par exemple une image ou une vidéo. | Facultatif | Requis | Liste<br>facultative des critères de filtre d’image ou vidéo transmise au sélecteur de ressources. | Facultatif | n/a | Facultatif |
| `container` | L’élément modifiable se comporte comme un conteneur pour les composants, c’est-à-dire le système de paragraphe. | Selon le cas <br>voir ci-dessous. | Selon le cas <br>voir ci-dessous. | Une liste<br>facultative des composants autorisés | Facultatif | n/a | n/a |
| `component` | L’élément modifiable est un composant. Il n’ajoute pas de fonctionnalités supplémentaires. Il est nécessaire d’indiquer les parties déplaçables/déplaçables du DOM et d’ouvrir le panneau des propriétés et ses champs. | Requis | n/a | n/a | Facultatif | Facultatif | n/a |
| `reference` | Le modifiable est une référence, par exemple, Fragment de contenu, Fragment d’expérience ou Produit | Selon le cas <br>voir ci-dessous. | Selon le cas <br>voir ci-dessous. | Une liste<br>facultative des critères de filtre des fragments de contenu, des produits ou des fragments d’expérience transmise au sélecteur de références. | Facultatif | Facultatif | n/a |

`data-aue-resource` est toujours requis, car il s’agit de la clé primaire indiquant où les modifications de contenu sont écrites.

* Elle n’est pas requise directement sur la balise dans laquelle le `data-aue-type` est défini.
* Si elle n’est pas définie, l’attribut `data-aue-resource` d’un parent le plus proche sera utilisé.

`data-aue-prop` est requis lorsque vous souhaitez effectuer une modification en contexte, à l’exception d’un conteneur où il est facultatif (si la définition du conteneur est un fragment de contenu et que la prop pointe vers un champ de référence multiple).

* `data-aue-prop` est l’attribut à mettre à jour pour la clé primaire de `data-aue-resource`.

## Comportements {#behaviors}

| `data-aue-behavior` | Description |
|---|---|
| `component` | Utilisé pour autoriser les composants de texte autonome, de texte enrichi et de mimique multimédia afin qu’ils puissent également être déplacés et supprimés sur la page. |
| `container` | Utilisé pour permettre aux conteneurs d’être traités comme leurs propres composants afin qu’ils soient mobiles et pouvant être supprimés sur la page. |
