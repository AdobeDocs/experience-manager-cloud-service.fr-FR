---
title: Attributs et types d’éléments
description: Découvrez les attributs de données et les types d’éléments requis par l’éditeur universel.
exl-id: 02795a31-244a-42b4-8297-2649125d7777
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 100%

---


# Attributs et types {#attributes-types}

Découvrez les attributs de données et les types d’éléments requis par l’éditeur universel.

## Présentation {#introduction}

Pour que l’éditeur universel puisse modifier une application, cette dernière doit être correctement instrumentée. L’application doit inclure des métadonnées appropriées afin que l’éditeur puisse en modifier le contenu. Ce document décrit les attributs et les types d’éléments de ces métadonnées.

>[!NOTE]
>
>La validation du contenu se produit côté serveur. L’éditeur universel fonctionne simplement avec les attributs de données. La validation de leur adéquation au modèle/à la structure doit être traitée au niveau de l’API.

## Propriétés des données {#data-properties}

| Propriété des données | Description |
|---|---|
| `data-aue-resource` | URN de la ressource : consultez la section [Instrumenter la page du document Prise en main de l’éditeur universel dans AEM](getting-started.md#instrument-thepage). |
| `data-aue-prop` | Attribut de la ressource : consultez la section [Instrumenter la page du document Prise en main de l’éditeur universel dans AEM](getting-started.md#instrument-thepage). |
| `data-aue-type` | [Type de l’élément modifiable](#item-types) (par exemple, texte, image et référence). |
| `data-aue-filter` | Définit :<br>- Quelles fonctionnalités d’éditeur de texte enrichi sont activées.<br>- Quels composants peuvent être ajoutés à un conteneur.<br>- Quelles ressources peuvent être ajoutées à un type de média. |
| `data-aue-label` | Définit un libellé personnalisé pour un élément sélectionnable affiché dans l’éditeur. |
| `data-aue-model` | Définit un modèle qui est utilisé pour la modification basée sur les formulaires dans le panneau des propriétés. |
| `data-aue-behavior` | Obsolète. Définit le comportement d’une instrumentation pour permettre à un texte, un texte enrichi et un média autonomes d’imiter les composants afin qu’ils puissent également être déplacés et supprimés sur la page, offrant ainsi une valeur potentielle unique de `component`. Cette propriété est maintenant ignorée et lorsqu’un élément avec `data-aue-resource` est un enfant direct d’un conteneur, elle est automatiquement considérée comme un composant. |

## Types d’éléments {#item-types}

| `data-aue-type` | Description | `data-aue-resource` | `data-aue-prop` | `data-aue-filter` | `data-aue-label` | `data-aue-model` |
|---|---|---|---|---|---|---|
| `text` | Le texte est modifiable dans les balises HTML, mais uniquement dans un format de texte simple, sans mise en forme de texte enrichi. Ce format est généralement utilisé sur les composants de titre. | Facultatif | Nécessaires | n/a | Facultatif | n/a |
| `richtext` | Le texte est modifiable avec des fonctionnalités de texte enrichi complètes. L’éditeur de texte enrichi s’affiche dans le panneau de droite | Facultatif | Nécessaires | n/a | Facultatif | n/a |
| `media` | L’élément modifiable est une ressource, par exemple une image ou une vidéo. | Facultatif | Nécessaires | Liste<br>facultative des critères de filtre d’image ou vidéo transmise au sélecteur de ressources. | Facultatif | n/a |
| `container` | L’élément modifiable se comporte comme un conteneur pour les composants, c’est-à-dire le système de paragraphe. | Selon le cas <br>voir ci-dessous. | Selon le cas <br>voir ci-dessous. | Une liste<br>facultative des composants autorisés | Facultatif | n/a |
| `component` | L’élément modifiable est un composant. Cela n’ajoute pas de fonctionnalité supplémentaire. Cela est nécessaire pour indiquer les parties qui peuvent être déplacées/supprimées du DOM et pour ouvrir le panneau de propriétés et ses champs. | Nécessaires | n/a | n/a | Facultatif | Facultatif |
| `reference` | L’élément modifiable est une référence, par exemple, un fragment de contenu, un fragment d’expérience ou un produit. | Selon le cas <br>voir ci-dessous. | Selon le cas <br>voir ci-dessous. | Une liste<br>facultative des critères de filtre des fragments de contenu, des produits ou des fragments d’expérience transmise au sélecteur de références. | Facultatif | Facultatif |

`data-aue-resource` est toujours nécessaire, car il s’agit de la clé primaire qui indique où les modifications de contenu sont écrites.

* Il n’est pas nécessaire directement sur la balise où `data-aue-type` est défini.
* S’il n’est pas défini, l’attribut `data-aue-resource` d’un parent le plus proche est utilisé.

`data-aue-prop` est nécessaire chaque fois que vous souhaitez effectuer une modification en contexte, à l’exception d’un conteneur où il est facultatif (si le conteneur est défini, il s’agit d’un fragment de contenu et la propriété pointe vers un champ à références multiples).

* `data-aue-prop` est l’attribut à mettre à jour pour la clé primaire de `data-aue-resource`.
