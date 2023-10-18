---
title: Attributs et types
description: Découvrez les attributs et les types de données requis par l’éditeur universel.
exl-id: 02795a31-244a-42b4-8297-2649125d7777
source-git-commit: 79fe3133a6b0553209b14c4cf47faa9db28caacc
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 87%

---

# Attributs et types {#attributes-types}

Découvrez les attributs et les types de données requis par l’éditeur universel.

## Présentation {#introduction}

Pour que l’éditeur universel puisse modifier une application, cette dernière doit être correctement instrumentée. L’application doit inclure des métadonnées appropriées afin que l’éditeur puisse en modifier le contenu. Ce document décrit les attributs et les types de ces métadonnées.

>[!NOTE]
>
>La validation du contenu se produit côté serveur. L’éditeur universel fonctionne simplement avec les attributs de données. La validation de leur adéquation au modèle/à la structure doit être traitée au niveau de l’API.

## Propriétés des données {#data-properties}

| Propriété des données | Description |
|---|---|
| `itemid` | URN de la ressource : consultez la section [Instrumenter la page du document Prise en main de l’éditeur universel dans AEM](getting-started.md#instrument-thepage). |
| `itemprop` | Attribut de la ressource : consultez la section [Instrumenter la page du document Prise en main de l’éditeur universel dans AEM](getting-started.md#instrument-thepage). |
| `itemtype` | Type de l’élément modifiable (par exemple, texte, image et référence) |
| `data-editor-itemfilter` | Définit les références qui peuvent être utilisées |
| `data-editor-itemlabel` | Définit un libellé personnalisé pour un élément sélectionnable affiché dans l’éditeur. <br>Si `itemmodel` est défini, le libellé est récupéré via le modèle. |
| `data-editor-itemmodel` | Définit un modèle qui est utilisé pour la modification basée sur les formulaires dans le rail des propriétés |
| `data-editor-behavior` | Définit le comportement d’une instrumentation ; par exemple, un texte ou une image autonome peut également reproduire un composant pour qu’il puisse être modifié ou supprimé. |

## Types d’éléments {#item-types}

| `itemtype` | Description | `itemid` | `itemprop` | `data-editor-itemfilter` | `data-editor-itemlabel` | `data-editor-itemmodel` | `data-editor-behvior` |
|---|---|---|---|---|---|---|---|
| `text` | Le texte est modifiable dans les balises HTML, mais uniquement dans un format de texte simple, sans mise en forme de texte enrichi. Ce format est généralement utilisé sur les composants de titre. | Facultatif | Requis | n/a | Facultatif | n/a | Facultatif |
| `richtext` | Le texte est modifiable avec des fonctionnalités de texte enrichi complètes. L’éditeur de texte enrichi s’affiche dans le panneau de droite | Facultatif | Requis | n/a | Facultatif | n/a | Facultatif |
| `media` | L’élément modifiable est une ressource, par exemple une image ou une vidéo. | Facultatif | Requis | Liste<br>facultative des critères de filtre d’image ou vidéo transmise au sélecteur de ressources. | Facultatif | n/a | Facultatif |
| `container` | L’élément modifiable se comporte comme un conteneur pour les composants, c’est-à-dire le système de paragraphe. | Selon le cas <br>voir ci-dessous. | Selon le cas <br>voir ci-dessous. | Une liste<br>facultative des composants autorisés | Facultatif | n/a | n/a |
| `component` | L’élément modifiable est un composant. Il n’ajoute pas de fonctionnalités supplémentaires. Il est nécessaire d’indiquer les parties déplaçables/déplaçables du DOM et d’ouvrir le rail des propriétés et ses champs. | Requis | n/a | n/a | Facultatif | Facultatif | n/a |
| `reference` | L’élément modifiable est une référence : par exemple, un fragment de contenu, un fragment d’expérience ou un produit. | Selon le cas <br>voir ci-dessous. | Selon le cas <br>voir ci-dessous. | Une liste<br>facultative des critères de filtre des fragments de contenu, des produits ou des fragments d’expérience transmise au sélecteur de références. | Facultatif | Facultatif | n/a |

Selon le cas d’utilisation, `itemprop` ou `itemid` peuvent être requis. Par exemple :

* `itemid` est requis si vous interrogez des fragments de contenu via GraphQL et que vous souhaitez rendre la liste modifiable en contexte.
* `itemprop` est requis si un composant effectue le rendu du contenu d’un fragment de contenu référencé et que vous souhaitez mettre à jour la référence dans le composant.

## Comportements {#behaviors}

| `data-editor-behavior` | Description |
|---|---|
| `component` | Utilisé pour autoriser les composants de texte autonome, de texte enrichi et de mimique multimédia afin qu’ils puissent également être déplacés et supprimés sur la page. |
| `container` | Utilisé pour permettre aux conteneurs d’être traités comme leurs propres composants afin qu’ils soient mobiles et pouvant être supprimés sur la page. |

## Ressources supplémentaires {#additional-resources}

Pour en savoir plus sur l’éditeur universel, consultez ces documents.

* [Présentation de l’éditeur universel](introduction.md) - Découvrez comment l’éditeur universel permet de modifier n’importe quel aspect d’un contenu dans n’importe quelle implémentation afin de fournir des expériences exceptionnelles, d’augmenter la vitesse du contenu et d’offrir une expérience de développement à la pointe de la technologie.
* [Création de contenu avec l’éditeur universel](authoring.md) - Découvrez à quel point il est facile et intuitif pour les créateurs et les créatrices de contenu de créer du contenu à l’aide de l’éditeur universel.
* [Publication de contenu avec l’éditeur universel](publishing.md) - Découvrez comment l’éditeur universel publie du contenu et comment vos applications peuvent gérer le contenu publié.
* [Prise en main de l’éditeur universel dans AEM](getting-started.md) - Découvrez comment accéder à l’éditeur universel et comment commencer à instrumenter votre première application AEM pour l’utiliser.
* [Architecture de l’éditeur universel](architecture.md) – Découvrez l’architecture de l’éditeur universel et le flux de données entre ses services et calques.
* [Authentification de l’éditeur universel](authentication.md) – Découvrez comment l’éditeur universel s’authentifie.
