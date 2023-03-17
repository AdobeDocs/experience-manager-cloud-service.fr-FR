---
title: Attributs et types
description: Découvrez les attributs et les types de données requis par Universal Editor.
source-git-commit: f454475b65da8f410812bbbe30ca5fc393be410a
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 7%

---


# Attributs et types {#attributes-types}

Découvrez les attributs et les types de données requis par Universal Editor.

## Présentation {#introduction}

Pour qu’une application puisse être modifiée par l’éditeur universel, elle doit être correctement instrumentée. Cela inclut l’inclusion des métadonnées appropriées afin que l’éditeur puisse modifier le contenu de l’application. Ce document décrit les attributs et les types de ces métadonnées.

>[!NOTE]
>
>La validation du contenu est effectuée côté serveur. L’éditeur universel fonctionne simplement avec les attributs de données. La validation qu’elles correspondent au modèle/à la structure doit être traitée au niveau de l’API.

## Propriétés des données {#data-properties}

| Propriété des données | Description |
|---|---|
| `itemid` | URL de la ressource, voir la section [Instrument de la page du document Prise en main de l’éditeur universel dans AEM](getting-started.md#instrument-thepage) |
| `itemprop` | Attribut de la ressource, voir la section [Instrument de la page du document Prise en main de l’éditeur universel dans AEM](getting-started.md#instrument-thepage) |
| `itemtype` | Type de l’élément modifiable (par exemple, texte, image, référence, etc.) |
| `data-editor-itemfilter` | Définit les références qui peuvent être utilisées. |
| `data-editor-itemlabel` | Définit un libellé personnalisé pour un élément sélectionnable affiché dans l’éditeur. <br>Dans le cas `itemmodel` est définie, le libellé sera récupéré via le modèle. |
| `data-editor-itemmodel` | Définit un modèle qui sera utilisé pour la modification d’après les formulaires dans le rail des propriétés. |
| `data-editor-behavior` | Définit le comportement d’une instrumentation ; par exemple, un texte ou une image autonome peut également imiter un composant pour le rendre modifiable ou pouvant être supprimé. |

## Types d’éléments {#item-types}

| `itemtype` | Description | `itemid` | `itemprop` | `data-editor-itemfilter` | `data-editor-itemlabel` | `data-editor-itemmodel` | `data-editor-behvior` |
|---|---|---|---|---|---|---|---|
| `text` | Le texte est modifiable dans les balises de HTML, mais uniquement dans un format de texte simple, sans mise en forme de texte enrichi, ce format est généralement utilisé sur les composants de titre, par exemple. | Facultative | Requise | n/a | Facultative | n/a | Facultative |
| `richtext` | Le texte est modifiable avec des fonctionnalités de texte enrichi complètes. L’éditeur de texte enrichi s’affiche dans le panneau de droite. | Facultative | Requise | n/a | Facultative | n/a | Facultative |
| `media` | Le modifiable est une ressource, par exemple une image ou une vidéo. | Facultative | Requise | Facultatif<br>liste des critères de filtre d’image ou vidéo transmis au sélecteur de ressources | Facultative | n/a | Facultative |
| `container` | Le composant modifiable se comporte comme un conteneur pour les composants, c’est-à-dire le système de paragraphes. | Dépend <br>voir ci-dessous | Dépend <br>voir ci-dessous | Facultatif<br>une liste des composants autorisés ; | Facultative | n/a | n/a |
| `component` | Le modifiable est un composant. N’ajoute pas de fonctionnalités supplémentaires. Cela sera nécessaire pour indiquer les parties déplaçables/déplaçables du DOM et pour ouvrir le rail de propriétés et ses champs. | Requise | n/a | n/a | Facultative | Facultative | n/a |
| `reference` | Le modifiable est une référence, par exemple, Fragment de contenu, Fragment d’expérience ou Produit. | Dépend <br>voir ci-dessous | Dépend <br>voir ci-dessous | Facultatif<br>liste des critères de filtre Fragment de contenu, Produit ou Fragment d’expérience transmis au sélecteur de référence | Facultative | Facultative | n/a |

Selon le cas d’utilisation `itemprop` ou `itemid` peut être nécessaire ou non. Par exemple :

* `itemid` est requis si vous interrogez des fragments de contenu via GraphQL et souhaitez rendre la liste modifiable en contexte.
* `itemprop` est requis si un composant effectue le rendu du contenu d’un fragment de contenu référencé et que vous souhaitez mettre à jour la référence dans le composant.

## Comportements {#behaviors}

| `data-editor-behavior` | Description |
|---|---|
| `component` | Peut être utilisé pour laisser le texte autonome, le texte enrichi et les composants de mimique multimédia être déplacés et pouvant être supprimés sur la page. |

## Ressources supplémentaires {#additional-resources}

Pour en savoir plus sur Universal Editor, consultez ces documents.

* [Présentation de l’éditeur universel](introduction.md) - Découvrez comment Universal Editor permet de modifier n’importe quel aspect de contenu dans n’importe quelle mise en oeuvre afin de fournir des expériences exceptionnelles, d’augmenter la vitesse du contenu et de fournir une expérience de développement à la pointe de la technologie.
* [Création de contenu avec l’éditeur universel](authoring.md) - Découvrez à quel point il est facile et intuitif pour les auteurs de contenu de créer du contenu à l’aide de l’éditeur universel.
* [Prise en main d’Universal Editor dans AEM](getting-started.md) - Découvrez comment accéder à l’éditeur universel et comment commencer à instrumenter votre première application AEM pour l’utiliser.
* [Architecture d’éditeur universelle](architecture.md) - Découvrez l’architecture d’Universal Editor et le flux de données entre ses services et calques.
* [Authentification de l’éditeur universel](authentication.md) - Découvrez comment l’éditeur universel s’authentifie.
