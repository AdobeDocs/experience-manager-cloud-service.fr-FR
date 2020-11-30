---
title: Infrastructure de balisage AEM
description: Balisage de contenu et utilisation de l’infrastructure de balisage AEM afin de classer et d'organiser les données.
translation-type: tm+mt
source-git-commit: 4bf023068aa69fb6b69c6f2443703ea2bbbf7d42
workflow-type: tm+mt
source-wordcount: '1567'
ht-degree: 24%

---


# The AEM Tagging Framework {#aem-tagging-framework}

Le balisage permet de catégoriser et d’organiser le contenu. Les balises peuvent être classées par un espace de noms et par une taxonomie. Pour plus d’informations sur l’utilisation des balises :

* Voir [Utilisation des balises](/help/sites-cloud/authoring/features/tags.md) pour en savoir plus sur le balisage du contenu en tant qu’auteur de contenu.
* Voir Administration des balises pour en savoir plus sur la création et la gestion des balises, ainsi que sur les balises de contenu qui ont été appliquées.

Cet article se concentre sur le cadre sous-jacent qui prend en charge le balisage en AEM et comment l&#39;exploiter en tant que développeur.

## Présentation {#introduction}

Pour baliser le contenu et utiliser l’infrastructure de balisage AEM, procédez comme suit :

* The tag must exist as a node of type [`cq:Tag`](#cq-tag-node-type) under the [taxonomy root node.](#taxonomy-root-node)
* The tagged content node&#39;s `NodeType` must include the [`cq:Taggable`](#taggable-content-cq-taggable-mixin) mixin.
* The [`TagID`](#tagid) is added to the content node&#39;s [`cq:tags`](#cq-tags-property) property and resolves to a node of type [`cq:Tag`.](#cq-tag-node-type)

## cq:Tag Node Type {#cq-tag-node-type}

The declaration of a tag is captured in the repository in a node of type `cq:Tag.`

* A tag can be a simple word (e.g. `sky`) or represent a hierarchical taxonomy (e.g. `fruit/apple`, meaning both the generic fruit and the more specific apple).
* Tags are identified by a unique `TagID`.
* Une balise comprend des méta-informations facultatives, telles qu’un titre, des titres localisés et une description. The title should be displayed in user interfaces instead of the `TagID`, when present.

La structure de balisage offre également la possibilité de contraindre les auteurs et les visiteurs du site à n’utiliser que des balises prédéfinies spécifiques.

### Caractéristiques de la balise {#tag-characteristics}

* Le type de noeud est `cq:Tag`.
* The node name is a component of the [`TagID`.](#tagid)
* The [`TagID`](#tagid) always includes a [namespace.](#tag-namespace)
* La `jcr:title` propriété (Titre à afficher dans l’interface utilisateur) est facultative.
* The `jcr:description` property is optional.
* When containing child nodes, is referred to as a [container tag.](#container-tags)
* The tag is stored in the repository below a base path called the [taxonomy root node.](#taxonomy-root-node)

### ID de balise {#tagid}

A `TagID` identifies a path which resolves to a tag node in the repository.

Typically, the `TagID` is a shorthand `TagID` starting with the namespace or it can be an absolute `TagID` starting from the [taxonomy root node.](#taxonomy-root-node)

When content is tagged, if it does not yet exist, the [`cq:tags`](#cq-tags-property) property is added to the content node and the `TagID` is added to the property&#39;s `String` array value.

The `TagID` consists of a [namespace](#tag-namespace) followed by the local `TagID`. Les [balises conteneurs](#container-tags) contiennent des sous-balises qui représentent un ordre hiérarchique dans la taxonomie. Sub-tags can be used to reference tags same as any local `TagID`. For example tagging content with `fruit` is allowed, even if it is a container tag with sub-tags, such as `fruit/apple` and `fruit/banana`.

### Nœud racine de taxonomie {#taxonomy-root-node}

Le nœud racine de taxonomie est le chemin d’accès de base pour toutes les balises du référentiel. Le nœud racine de taxonomie ne peut *pas* être un nœud de type `cq:Tag`.

In AEM, the base path is `/content/cq:tags` and the root node is of type `cq:Folder`.

### Espace de noms des balises {#tag-namespace}

Les espaces de noms permettent de regrouper des éléments. Le cas d’utilisation le plus courant consiste à disposer d’un espace de nommage par site (par exemple, public par rapport à interne) ou par application plus large (par exemple, Sites ou Ressources), mais les espaces de nommage peuvent être utilisés pour divers autres besoins. Les Espaces de nommage sont utilisés dans l’interface utilisateur pour afficher uniquement le sous-ensemble de balises (balises d’un certain espace de nommage, par exemple) qui s’applique au contenu actuel.

L’espace de noms de la balise est le premier niveau de la sous-arborescence de taxonomie, à savoir le nœud situé juste en dessous du [nœud racine de taxonomie.](#taxonomy-root-node) Un espace de nommage est un noeud de type `cq:Tag` dont le parent n’est pas un type de `cq:Tag` noeud.

Toutes les balises possèdent un espace de noms. Si aucun espace de nommage n’est spécifié, la balise est affectée à l’espace de nommage par défaut, c’est-à-dire `TagID``default`, `/content/cq:tags/default`.  Le titre est défini par défaut `Standard Tags`dans ces cas.

### Balises conteneurs {#container-tags}

Une balise conteneur est un nœud de type `cq:Tag` contenant le nombre et le type des nœuds enfants, ce qui permet d’enrichir le modèle de balise avec des métadonnées personnalisées.

Furthermore, container tags (or super-tags) in a taxonomy serve as the sub-summation of all sub-tags: for example content tagged with `fruit/apple` is considered to be tagged with `fruit` as well, i.e. searching for content just tagged with `fruit` would also find the content tagged with `fruit/apple`.

### Résolution d’ID de balise {#resolving-tagids}

If the tag ID contains a colon (`:`), the colon separates the namespace from the tag or sub-taxonomy, which are then separated with normal slashes (`/`). En l’absence de signe deux-points dans l’ID de balise, l’espace de noms par défaut est impliqué.

The standard and only location of tags is below `/content/cq:tags`.

Tags referencing non-existing paths or paths that do not point to a `cq:Tag` node are considered invalid and are ignored.

The following table shows some sample `TagID`s, their elements, and how the `TagID` resolves to an absolute path in the repository:

| `TagID` | Espace de noms | ID local | Balise(s) de conteneur | Balise Feuille | Chemin d’accès absolu aux balises du référentiel |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`,`apple` | `braeburn` | `content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | (aucune) | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | (aucune) | (aucune) | (aucune) | `/content/cq:tags/dam` |
| `content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `content/cq:tags/category/car` |

### Localisation du titre de balise {#localization-of-tag-title}

When the tag includes the optional title string `jcr:title`, it is possible to localize the title for display by adding the property `jcr:title.<locale>`.

Pour plus d’informations, voir :

* [Balises dans différentes langues,](tagging-applications.md#tags-in-different-languages) qui décrit l’utilisation des API en tant que développeur
* Gestion des balises dans différentes langues, qui décrit l’utilisation de la console de balisage en tant qu’administrateur

### Contrôle d’accès {#access-control}

Les balises existent sous la forme de nœud dans le répertoire sous le [nœud racine de taxonomie.](#taxonomy-root-node) Il est possible d’autoriser ou de refuser aux auteurs et aux visiteurs du site de créer des balises dans un espace de nommage donné en définissant des listes de contrôle d’accès appropriées dans le référentiel.

Le refus d’autorisations de lecture pour certaines balises ou certains espaces de nommage permet de contrôler la possibilité d’appliquer des balises à un contenu spécifique.

Une pratique habituelle est la suivante :

* Allowing the `tag-administrators` group/role write access to all namespaces (add/modify under `/content/cq:tags`). Ce groupe est fourni en standard avec AEM.
* Accorder aux utilisateurs/auteurs l’accès en lecture à tous les espaces de noms qu’ils doivent être autorisés à lire (presque tous).
* Allowing users/authors write access to those namespaces where tags should be freely definable by users/authors (`add_node` under `/content/cq:tags/some_namespace`)

## Contenu pouvant être balisé : cq:Taggable Mixin {#taggable-content-cq-taggable-mixin}

In order for application developers to attach tagging to a content type, the node&#39;s registration ([CND](https://jackrabbit.apache.org/node-type-notation.html)) must include the `cq:Taggable` mixin or the `cq:OwnerTaggable` mixin.

Le mixin `cq:OwnerTaggable`, qui hérite de `cq:Taggable`, sert à indiquer que le contenu peut être classé par propriétaire/auteur. In AEM, it is only an attribute of the `cq:PageContent` node. The `cq:OwnerTaggable` mixin is not required by the tagging framework.

>[!NOTE]
>
>It is recommended to only enable tags on the top-level node of an aggregated content item (or on its `jcr:content` node). Voici quelques exemples :
>
>* Pages (`cq:Page`) where the `jcr:content`node is of type `cq:PageContent`, which includes the `cq:Taggable` mixin.
>* Assets (`cq:Asset`) where the `jcr:content/metadata` node always has the `cq:Taggable` mixin.


### Notation de type de nœud (CND) {#node-type-notation-cnd}

Les définitions de type de nœud existent dans le référentiel sous la forme de fichiers CND. The CND notation is defined as part of the [JCR documentation.](https://jackrabbit.apache.org/node-type-notation.html).

Les définitions essentielles relatives aux types de nœud inclus dans AEM sont les suivantes :

```xml
[cq:Tag] > mix:title, nt:base
    orderable
    - * (undefined) multiple
    - * (undefined)
    + * (nt:base) = cq:Tag version

[cq:Taggable]
    mixin
    - cq:tags (string) multiple

[cq:OwnerTaggable] > cq:Taggable
    mixin
```

## cq:tags, propriété {#cq-tags-property}

The `cq:tags` property is a `String` array used to store one or more `TagID`s when they are applied to content by authors or site visitors. The property only has meaning when added to a node which is defined with the [`cq:Taggable`](#taggable-content-cq-taggable-mixin) mixin.

>[!NOTE]
>
>Pour tirer parti de la fonctionnalité de balisage d’AEM, les applications personnalisées ne doivent pas définir de propriétés de balise autres que `cq:tags`.

## Déplacement et fusion de balises {#moving-and-merging-tags}

Voici une description des effets dans le référentiel lors du déplacement ou de la fusion de balises à l’aide de la console Balisage.

When tag A is moved or merged into tag B under `/content/cq:tags`:

* Tag A is not deleted and receives a `cq:movedTo` property.
   * `cq:movedTo` pointe vers la balise B.
   * Cette propriété signifie que la balise A a été déplacée ou fusionnée dans la balise B.
   * Le déplacement de la balise B mettra cette propriété à jour en conséquence.
   * La balise A est donc masquée et conservée uniquement dans le référentiel pour résoudre les ID de balise dans les noeuds de contenu pointant vers la balise A.
   * Le collecteur de balises supprime les balises telles que la balise A une fois que plus aucun noeud de contenu ne les pointe.
   * A special value for the `cq:movedTo` property is `nirvana`, which is applied when the tag is deleted but cannot be removed from the repository because there are subtags with a `cq:movedTo` that must be kept.

      >[!NOTE]
      >
      >La `cq:movedTo` propriété n’est ajoutée à la balise déplacée ou fusionnée que si l’une de ces conditions est remplie :
      >
      > 1. La balise est utilisée dans le contenu (ce qui signifie qu’elle comporte une référence). OU
      > 1. La balise contient des enfants qui ont déjà été déplacés.


* Tag B is created (in case of a move) and receives a `cq:backlinks` property.
   * `cq:backlinks` conserve les références dans l’autre direction, c’est-à-dire qu’elle conserve une liste de toutes les balises qui ont été déplacées ou fusionnées avec la balise B.
   * Cela est principalement nécessaire pour tenir `cq:movedTo` les propriétés à jour lorsque la balise B est également déplacée/fusionnée/supprimée ou lorsque la balise B est activée, auquel cas toutes ses balises de liens arrière doivent également être activées.

      >[!NOTE]
      >
      >La `cq:backlinks` propriété n’est ajoutée à la balise déplacée ou fusionnée que si l’une de ces conditions est remplie :
      >
      > 1. La balise est utilisée dans le contenu (ce qui signifie qu’elle comporte une référence). OU
      > 1. La balise contient des enfants qui ont déjà été déplacés.


Reading a `cq:tags` property of a content node involves the following resolution:

1. If there is no match under `/content/cq:tags`, no tag is returned.
1. Si la propriété `cq:movedTo` est définie pour la balise, l’ID de balise référencé est suivi.
   *  Cette étape est répétée aussi longtemps que la balise suivie contient la propriété `cq:movedTo`.
1. Si la balise suivie n’est pas associée à une propriété `cq:movedTo`, elle est lue.

Pour publier la modification lorsqu’une balise a été déplacée ou fusionnée, le noeud `cq:Tag` et tous ses liens d’arrière-plan doivent être répliqués. Cette opération est automatiquement effectuée lorsque la balise est activée dans la console d’administration des balises.

Later updates to the page&#39;s `cq:tags` property automatically clean up the old references. Cette opération est déclenchée, car la résolution d’une balise déplacée via l’API renvoie la balise de destination, fournissant ainsi l’ID de balise de destination.
