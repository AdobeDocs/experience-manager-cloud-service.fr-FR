---
title: Infrastructure de balisage AEM
description: Balisage de contenu et utilisation de l’infrastructure de balisage AEM afin de classer et d'organiser les données.
translation-type: tm+mt
source-git-commit: 4bf023068aa69fb6b69c6f2443703ea2bbbf7d42
workflow-type: tm+mt
source-wordcount: '1567'
ht-degree: 24%

---


# Cadre de balisage AEM {#aem-tagging-framework}

Le balisage permet de catégoriser et d’organiser le contenu. Les balises peuvent être classées par un espace de noms et par une taxonomie. Pour plus d’informations sur l’utilisation des balises :

* Voir [Utilisation des balises](/help/sites-cloud/authoring/features/tags.md) pour plus d’informations sur le balisage du contenu en tant qu’auteur de contenu.
* Voir Administration des balises pour en savoir plus sur la création et la gestion des balises, ainsi que sur les balises de contenu qui ont été appliquées.

Cet article se concentre sur le cadre sous-jacent qui prend en charge le balisage en AEM et comment l&#39;exploiter en tant que développeur.

## Présentation {#introduction}

Pour baliser le contenu et utiliser l’infrastructure de balisage AEM, procédez comme suit :

* La balise doit exister en tant que noeud de type [`cq:Tag`](#cq-tag-node-type) sous le [noeud racine de taxonomie.](#taxonomy-root-node)
* `NodeType` du noeud de contenu balisé doit inclure le mixin [`cq:Taggable`](#taggable-content-cq-taggable-mixin).
* [`TagID`](#tagid) est ajouté à la propriété [`cq:tags`](#cq-tags-property) du noeud de contenu et est résolu en un noeud de type [`cq:Tag`.](#cq-tag-node-type)

## cq:Type de noeud de balise {#cq-tag-node-type}

La déclaration d’une balise est capturée dans le référentiel dans un noeud de type `cq:Tag.`.

* Une balise peut être un mot simple (ex. `sky`) ou représentent une taxonomie hiérarchique (p. ex. `fruit/apple`, ce qui signifie à la fois le fruit générique et la pomme plus spécifique).
* Les balises sont identifiées par un `TagID` unique.
* Une balise comprend des méta-informations facultatives, telles qu’un titre, des titres localisés et une description. Le titre doit s’afficher dans les interfaces utilisateur au lieu de `TagID`, le cas échéant.

La structure de balisage offre également la possibilité de contraindre les auteurs et les visiteurs du site à n’utiliser que des balises prédéfinies spécifiques.

### Caractéristiques de la balise {#tag-characteristics}

* Le type de noeud est `cq:Tag`.
* Le nom du noeud est un composant de [`TagID`.](#tagid)
* Le [`TagID`](#tagid) contient toujours un espace de nommage [.](#tag-namespace)
* La propriété `jcr:title` (le titre à afficher dans l’interface utilisateur) est facultative.
* La propriété `jcr:description` est facultative.
* Lorsqu’il contient des noeuds enfants, est appelé balise [conteneur.](#container-tags)
* La balise est stockée dans le référentiel sous un chemin d&#39;accès de base appelé [noeud racine de taxonomie.](#taxonomy-root-node)

### ID de balise {#tagid}

Un `TagID` identifie un chemin d’accès qui se résout en un noeud de balise dans le référentiel.

En règle générale, `TagID` est un raccourci `TagID` commençant par l&#39;espace de nommage ou il peut s&#39;agir d&#39;un absolu `TagID` commençant par le noeud racine de la taxonomie [.](#taxonomy-root-node)

Lorsque le contenu est balisé, s’il n’existe pas encore, la propriété [`cq:tags`](#cq-tags-property) est ajoutée au noeud de contenu et `TagID` est ajoutée à la valeur de tableau `String` de la propriété.

Le `TagID` se compose d&#39;un [espace de nommage](#tag-namespace) suivi du `TagID` local. Les [balises conteneurs](#container-tags) contiennent des sous-balises qui représentent un ordre hiérarchique dans la taxonomie. Les sous-balises peuvent être utilisées pour référencer des balises comme n&#39;importe quelle balise locale `TagID`. Par exemple, le balisage du contenu avec `fruit` est autorisé, même s’il s’agit d’une balise conteneur avec des sous-balises, telles que `fruit/apple` et `fruit/banana`.

### Nœud racine de taxonomie {#taxonomy-root-node}

Le nœud racine de taxonomie est le chemin d’accès de base pour toutes les balises du référentiel. Le nœud racine de taxonomie ne peut *pas* être un nœud de type `cq:Tag`.

En AEM, le chemin d’accès de base est `/content/cq:tags` et le noeud racine est de type `cq:Folder`.

### Espace de noms des balises {#tag-namespace}

Les espaces de noms permettent de regrouper des éléments. Le cas d’utilisation le plus courant consiste à disposer d’un espace de nommage par site (par exemple, public par rapport à interne) ou par application plus large (par exemple, Sites ou Ressources), mais les espaces de nommage peuvent être utilisés pour divers autres besoins. Les Espaces de nommage sont utilisés dans l’interface utilisateur pour afficher uniquement le sous-ensemble de balises (balises d’un certain espace de nommage, par exemple) qui s’applique au contenu actuel.

L’espace de noms de la balise est le premier niveau de la sous-arborescence de taxonomie, à savoir le nœud situé juste en dessous du [nœud racine de taxonomie.](#taxonomy-root-node) Un espace de nommage est un noeud de type  `cq:Tag` dont le parent n’est pas un type de  `cq:Tag` noeud.

Toutes les balises possèdent un espace de noms. Si aucun espace de nommage n’est spécifié, la balise est affectée à l’espace de nommage par défaut, qui est `TagID` `default`, c’est-à-dire. `/content/cq:tags/default`.  Dans ce cas, le titre est défini par défaut sur `Standard Tags`.

### Balises conteneurs {#container-tags}

Une balise conteneur est un nœud de type `cq:Tag` contenant le nombre et le type des nœuds enfants, ce qui permet d’enrichir le modèle de balise avec des métadonnées personnalisées.

En outre, les balises de conteneur (ou super-balises) dans une taxonomie servent de sous-somme de toutes les sous-balises : par exemple, le contenu balisé avec `fruit/apple` est également considéré comme balisé avec `fruit`, c’est-à-dire que la recherche de contenu simplement balisé avec `fruit` trouvera également le contenu balisé avec `fruit/apple`.

### Résolution d’ID de balise {#resolving-tagids}

Si l’ID de balise contient un deux-points (`:`), le deux-points sépare l’espace de nommage de la balise ou de la sous-taxonomie, qui sont ensuite séparés par des barres obliques normales (`/`). En l’absence de signe deux-points dans l’ID de balise, l’espace de noms par défaut est impliqué.

L&#39;emplacement standard et unique des balises est inférieur à `/content/cq:tags`.

Les balises référençant des chemins ou chemins non existants qui ne pointent pas vers un noeud `cq:Tag` sont considérées comme non valides et sont ignorées.

Le tableau suivant présente quelques exemples de `TagID`s, leurs éléments et la façon dont `TagID` se résout en chemin absolu dans le référentiel :

| `TagID` | Espace de noms | ID local | Balise(s) de conteneur | Balise Feuille | Chemin d’accès absolu aux balises du référentiel |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`,`apple` | `braeburn` | `content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | (aucune) | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | (aucune) | (aucune) | (aucune) | `/content/cq:tags/dam` |
| `content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `content/cq:tags/category/car` |

### Localisation du titre de balise {#localization-of-tag-title}

Lorsque la balise contient la chaîne de titre facultative `jcr:title`, il est possible de localiser le titre pour l’affichage en ajoutant la propriété `jcr:title.<locale>`.

Pour plus d’informations, voir :

* [Balises dans différentes langues,](tagging-applications.md#tags-in-different-languages) qui décrit l’utilisation des API en tant que développeur
* Gestion des balises dans différentes langues, qui décrit l’utilisation de la console de balisage en tant qu’administrateur

### Contrôle d’accès {#access-control}

Les balises existent sous la forme de nœud dans le répertoire sous le [nœud racine de taxonomie.](#taxonomy-root-node) Il est possible d’autoriser ou de refuser aux auteurs et aux visiteurs du site de créer des balises dans un espace de nommage donné en définissant des listes de contrôle d’accès appropriées dans le référentiel.

Le refus d’autorisations de lecture pour certaines balises ou certains espaces de nommage permet de contrôler la possibilité d’appliquer des balises à un contenu spécifique.

Une pratique habituelle est la suivante :

* Autorisation de l&#39;accès en écriture de groupe/rôle `tag-administrators` à tous les espaces de nommage (ajouter/modifier sous `/content/cq:tags`). Ce groupe est fourni en standard avec AEM.
* Accorder aux utilisateurs/auteurs l’accès en lecture à tous les espaces de noms qu’ils doivent être autorisés à lire (presque tous).
* Autoriser les utilisateurs/auteurs à écrire l’accès aux espaces de nommage où les balises doivent être définies librement par les utilisateurs/auteurs (`add_node` sous `/content/cq:tags/some_namespace`)

## Contenu pouvant être balisé : cq:Taggable Mixin {#taggable-content-cq-taggable-mixin}

Pour que les développeurs d’applications puissent associer un balisage à un type de contenu, l’enregistrement du noeud ([CND](https://jackrabbit.apache.org/node-type-notation.html)) doit inclure le mixin `cq:Taggable` ou le mixin `cq:OwnerTaggable`.

Le mixin `cq:OwnerTaggable`, qui hérite de `cq:Taggable`, sert à indiquer que le contenu peut être classé par propriétaire/auteur. En AEM, il ne s’agit que d’un attribut du noeud `cq:PageContent`. Le mixin `cq:OwnerTaggable` n&#39;est pas requis par la structure de balisage.

>[!NOTE]
>
>Il est recommandé d’activer uniquement les balises sur le noeud de niveau supérieur d’un élément de contenu agrégé (ou sur son `jcr:content` noeud). Voici quelques exemples :
>
>* Pages (`cq:Page`) où le noeud `jcr:content`est de type `cq:PageContent`, qui inclut le mixin `cq:Taggable`.
>* Actifs (`cq:Asset`) où le noeud `jcr:content/metadata` a toujours le mixin `cq:Taggable`.


### Notation de type de nœud (CND) {#node-type-notation-cnd}

Les définitions de type de nœud existent dans le référentiel sous la forme de fichiers CND. La notation CND est définie dans la documentation [JCR.](https://jackrabbit.apache.org/node-type-notation.html).

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

La propriété `cq:tags` est un tableau `String` utilisé pour stocker un ou plusieurs `TagID`s lorsqu&#39;ils sont appliqués au contenu par les auteurs ou les visiteurs du site. La propriété n&#39;a de signification que lorsqu&#39;elle est ajoutée à un noeud défini avec le mixin [`cq:Taggable`](#taggable-content-cq-taggable-mixin).

>[!NOTE]
>
>Pour tirer parti de la fonctionnalité de balisage d’AEM, les applications personnalisées ne doivent pas définir de propriétés de balise autres que `cq:tags`.

## Déplacement et fusion de balises {#moving-and-merging-tags}

Voici une description des effets dans le référentiel lors du déplacement ou de la fusion de balises à l’aide de la console Balisage.

Lorsque la balise A est déplacée ou fusionnée dans la balise B sous `/content/cq:tags` :

* La balise A n’est pas supprimée et reçoit une propriété `cq:movedTo`.
   * `cq:movedTo` pointe vers la balise B.
   * Cette propriété signifie que la balise A a été déplacée ou fusionnée dans la balise B.
   * Le déplacement de la balise B mettra cette propriété à jour en conséquence.
   * La balise A est donc masquée et conservée uniquement dans le référentiel pour résoudre les ID de balise dans les noeuds de contenu pointant vers la balise A.
   * Le collecteur de balises supprime les balises telles que la balise A une fois que plus aucun noeud de contenu ne les pointe.
   * Une valeur spéciale pour la propriété `cq:movedTo` est `nirvana`, qui est appliquée lorsque la balise est supprimée mais ne peut pas être supprimée du référentiel car il existe des sous-balises avec `cq:movedTo` qui doivent être conservées.

      >[!NOTE]
      >
      >La propriété `cq:movedTo` n&#39;est ajoutée à la balise déplacée ou fusionnée que si l&#39;une de ces conditions est remplie :
      >
      > 1. La balise est utilisée dans le contenu (ce qui signifie qu’elle comporte une référence). OU
      > 1. La balise contient des enfants qui ont déjà été déplacés.


* La balise B est créée (en cas de déplacement) et reçoit une propriété `cq:backlinks`.
   * `cq:backlinks` conserve les références dans l’autre direction, c’est-à-dire qu’elle conserve une liste de toutes les balises qui ont été déplacées ou fusionnées avec la balise B.
   * Cela est surtout nécessaire pour tenir les propriétés `cq:movedTo` à jour lorsque la balise B est également déplacée/fusionnée/supprimée ou lorsque la balise B est activée, auquel cas toutes ses balises de liens arrière doivent également être activées.

      >[!NOTE]
      >
      >La propriété `cq:backlinks` n&#39;est ajoutée à la balise déplacée ou fusionnée que si l&#39;une de ces conditions est remplie :
      >
      > 1. La balise est utilisée dans le contenu (ce qui signifie qu’elle comporte une référence). OU
      > 1. La balise contient des enfants qui ont déjà été déplacés.


La lecture d&#39;une propriété `cq:tags` d&#39;un noeud de contenu implique la résolution suivante :

1. Si aucune correspondance n’est trouvée sous `/content/cq:tags`, aucune balise n’est renvoyée.
1. Si la propriété `cq:movedTo` est définie pour la balise, l’ID de balise référencé est suivi.
   *  Cette étape est répétée aussi longtemps que la balise suivie contient la propriété `cq:movedTo`.
1. Si la balise suivie n’est pas associée à une propriété `cq:movedTo`, elle est lue.

Pour publier la modification lorsqu’une balise a été déplacée ou fusionnée, le noeud `cq:Tag` et tous ses liens d’arrière-plan doivent être répliqués. Cette opération est automatiquement effectuée lorsque la balise est activée dans la console d’administration des balises.

Des mises à jour ultérieures de la propriété `cq:tags` de la page nettoient automatiquement les anciennes références. Cette opération est déclenchée, car la résolution d’une balise déplacée via l’API renvoie la balise de destination, fournissant ainsi l’ID de balise de destination.
