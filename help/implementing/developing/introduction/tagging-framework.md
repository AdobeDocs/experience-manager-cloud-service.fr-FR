---
title: Framework de balisage AEM
description: Balisez le contenu et utilisez l’infrastructure de balisage AEM pour le classer et l’organiser.
exl-id: 25418d44-aace-4e73-be1a-4b1902f40403
source-git-commit: a01583483fa89f89b60277c2ce4e1c440590e96c
workflow-type: tm+mt
source-wordcount: '1569'
ht-degree: 66%

---

# Le cadre de balisage AEM {#aem-tagging-framework}

Le balisage permet de catégoriser et d’organiser le contenu. Les balises peuvent être classées par un espace de noms et par une taxonomie. Pour obtenir des informations détaillées sur l’utilisation des balises :

* Voir [Utilisation des balises](/help/sites-cloud/authoring/features/tags.md) pour plus d’informations sur le balisage du contenu en tant qu’auteur de contenu.
* Pour en savoir plus sur la création et la gestion des balises, ainsi que sur les balises de contenu qui ont été appliquées, voir Administration des balises pour un administrateur.

Cet article se concentre sur la structure sous-jacente qui prend en charge le balisage dans AEM et sur la manière de l’utiliser en tant que développeur.

## Présentation {#introduction}

Pour baliser le contenu et utiliser l’infrastructure de balisage AEM :

* La balise doit exister en tant que nœud du type [`cq:Tag`](#cq-tag-node-type) sous le [nœud racine de taxonomie.](#taxonomy-root-node)
* Le `NodeType` du nœud de contenu balisé doit inclure le mixin [`cq:Taggable`](#taggable-content-cq-taggable-mixin).
* Le [`TagID`](#tagid) est ajouté à la propriété [`cq:tags`](#cq-tags-property) du nœud de contenu et est résolu sur un nœud de type [`cq:Tag`.](#cq-tag-node-type)

## cq : balisage du type de nœud {#cq-tag-node-type}

La déclaration d’une balise est capturée dans le référentiel dans un nœud de type `cq:Tag.`

* Une balise peut être constituée d’un simple mot (`sky`, par exemple) ou représenter une taxonomie hiérarchique (`fruit/apple` par exemple, c’est-à-dire le fruit en tant que catégorie générique et la pomme en étant plus spécifique).
* Les balises sont identifiées par un `TagID` unique.
* Une balise contient des métadonnées facultatives telles qu’un titre, des titres localisés et une description. Le titre doit être affiché dans les interfaces utilisateur au lieu du `TagID`, le cas échéant.

La structure de balisage limite également les auteurs et les visiteurs du site à n’utiliser que des balises prédéfinies spécifiques.

### Caractéristiques de la balise {#tag-characteristics}

* Le type de noeud est `cq:Tag`.
* Le nom du nœud est un composant de [`TagID`.](#tagid)
* Le [`TagID`](#tagid) contient toujours un [espace de noms.](#tag-namespace)
* La propriété `jcr:title` (le titre à afficher dans l’interface utilisateur) est facultative.
* La propriété `jcr:description` est facultative.
* Lorsqu’elle contient des nœuds enfants, la balise est qualifiée de [balise conteneur.](#container-tags)
* La balise est stockée dans le référentiel, sous un chemin de base appelé [nœud racine de taxonomie.](#taxonomy-root-node)

### TagID {#tagid}

Un `TagID` identifie un chemin d’accès qui est résolu sur un nœud de balise dans le référentiel.

En règle générale, le `TagID` est un `TagID` abrégé commençant par l’espace de noms ; il peut également s’agir d’un `TagID` absolu commençant au niveau du [nœud racine de taxonomie.](#taxonomy-root-node)

Lorsque le contenu est balisé, la propriété [`cq:tags`](#cq-tags-property) est ajoutée, le cas échéant, au nœud de contenu et le `TagID` est ajouté à la valeur de tableau de la propriété `String`.

Le `TagID` se compose d’un [espace de noms](#tag-namespace), suivi du `TagID` local. [Balises de conteneur](#container-tags) comportent des sous-balises qui représentent un ordre hiérarchique dans la taxonomie. Les sous-balises peuvent être utilisées pour référencer des balises de la même manière que n’importe quelle balise locale. `TagID`. Par exemple, pour baliser le contenu avec `fruit` est autorisé, même s’il s’agit d’une balise conteneur comportant des sous-balises, telles que `fruit/apple` et `fruit/banana`.

### Nœud racine de taxonomie {#taxonomy-root-node}

Le nœud racine de taxonomie est le chemin d’accès de base pour toutes les balises du référentiel. Le nœud racine de taxonomie ne peut *pas* être un nœud de type `cq:Tag`.

Dans AEM, le chemin d’accès de base est `/content/cq:tags` et le nœud racine est de type `cq:Folder`.

### Espace de noms des balises {#tag-namespace}

Les espaces de noms vous permettent de regrouper des éléments. Le cas d’utilisation le plus courant consiste à disposer d’un espace de noms par site (par exemple, public ou interne) ou par grande application (par exemple, Sites ou Ressources), mais les espaces de noms peuvent être utilisés pour d’autres besoins. Les espaces de noms sont utilisés dans l’interface utilisateur pour afficher uniquement le sous-ensemble de balises (c’est-à-dire les balises d’un certain espace de noms) applicable au contenu actuel.

L’espace de noms de la balise est le premier niveau de la sous-arborescence de taxonomie, à savoir le nœud situé juste en dessous du [nœud racine de taxonomie.](#taxonomy-root-node) Un espace de noms est un nœud de type `cq:Tag` dont le parent n’est pas de type `cq:Tag`.

Toutes les balises possèdent un espace de noms. Si aucun espace de noms n’est spécifié, la balise est affectée à l’espace de noms par défaut, qui est `TagID` `default`, c’est-à-dire : `/content/cq:tags/default`. Dans ce cas, le titre est défini par défaut sur `Standard Tags`.

### Balises conteneurs {#container-tags}

Une balise conteneur est un nœud de type `cq:Tag` contenant le nombre et le type des nœuds enfants, ce qui permet d’enrichir le modèle de balise avec des métadonnées personnalisées.

En outre, les balises conteneur (ou super-balises) d’une taxonomie servent de sous-balises à la sous-combinaison de toutes les sous-balises. Par exemple, du contenu balisé avec `fruit/apple` est considéré comme balisé avec `fruit`, également . Autrement dit, la recherche de contenu balisé avec `fruit` trouverait également le contenu balisé avec `fruit/apple`.

### Résolution d’identifiant de balise {#resolving-tagids}

Si l’ID de balise contient deux points (`:`), le deux-points sépare l’espace de noms de la balise ou de la sous-taxonomie, qui sont ensuite séparés par des barres obliques normales (`/`). En l’absence de signe deux-points dans l’ID de balise, l’espace de noms par défaut est impliqué.

`/content/cq:tags` constitue l’emplacement standard des balises, mais aussi le seul.

Les balises qui référencent des chemins d’accès inexistants ou qui ne pointent pas vers un nœud `cq:Tag` sont considérés comme non valides et sont ignorés.

Le tableau ci-dessous présente quelques exemples de `TagID`, les éléments associés et la manière dont le `TagID` est résolu sur un chemin d’accès absolu dans le référentiel :

| `TagID` | Espace de noms | ID local | Balises conteneurs | Balise feuille | Chemin d’accès absolu aux balises du référentiel |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`,`apple` | `braeburn` | `content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | (aucune) | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | (aucune) | (aucune) | (aucune) | `/content/cq:tags/dam` |
| `content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `content/cq:tags/category/car` |

### Localisation du titre de balise {#localization-of-tag-title}

Lorsque la balise comprend une chaîne de titre facultative `jcr:title`, il est possible de localiser le titre à afficher en ajoutant la propriété `jcr:title.<locale>`.

Pour plus d’informations, voir :

* [Balises dans différentes langues](tagging-applications.md#tags-in-different-languages) décrire l’utilisation des API en tant que développeur ;
* Gestion des balises dans différentes langues, qui décrit l’utilisation de la console Balisage en tant qu’administrateur

### Contrôle d’accès {#access-control}

Les balises existent sous la forme de nœud dans le répertoire sous le [nœud racine de taxonomie.](#taxonomy-root-node) Il est possible d’accorder ou de refuser aux auteurs et aux visiteurs du site le droit de créer des balises dans un espace de noms donné en définissant des listes de contrôle d’accès (ACL) appropriées dans le référentiel.

Le refus d’autorisations de lecture pour certaines balises ou espaces de noms contrôle la possibilité d’appliquer des balises à un contenu spécifique.

Une pratique habituelle est la suivante :

* Accorder au groupe/rôle `tag-administrators` l’accès en écriture à tous les espaces de noms (add/modify sous `/content/cq:tags`). Ce groupe est fourni en standard avec AEM.
* Accorder aux utilisateurs/auteurs l’accès en lecture à tous les espaces de noms qu’ils doivent être autorisés à lire (presque tous).
* Accorder aux utilisateurs/auteurs l’accès en écriture aux espaces de noms dont ils doivent être en mesure de définir librement les balises (`add_node` sous `/content/cq:tags/some_namespace`).

## Contenu pouvant être balisé : mixin cq:Taggable {#taggable-content-cq-taggable-mixin}

Pour que les développeurs d’applications joignent un balisage à un type de contenu, l’enregistrement du noeud ([CND](https://jackrabbit.apache.org/jcr/node-type-notation.html)) doit inclure la variable `cq:Taggable` mixin ou le `cq:OwnerTaggable` mixin.

Le mixin `cq:OwnerTaggable`, qui hérite de `cq:Taggable`, sert à indiquer que le contenu peut être classé par propriétaire/auteur. Dans AEM, il s’agit uniquement d’un attribut du nœud `cq:PageContent`. Le mixin `cq:OwnerTaggable` n’est pas requis par le cadre de balisage.

>[!NOTE]
>
>Il est recommandé de n’activer les balises que sur le nœud de niveau supérieur d’un élément de contenu agrégé (ou sur son nœud `jcr:content`). Voici quelques exemples :
>
>* Pages (`cq:Page`) sur lesquelles le nœud `jcr:content` est de type `cq:PageContent`, ce qui inclut le mixin `cq:Taggable`.
>* Ressources (`cq:Asset`) dans lesquelles le nœud `jcr:content/metadata` possède toujours le mixin `cq:Taggable`.

### Notation de type de nœud (CND) {#node-type-notation-cnd}

Les définitions de type de nœud existent dans le référentiel sous la forme de fichiers CND. La notation CND est définie comme faisant partie de la [Documentation JCR](https://jackrabbit.apache.org/jcr/node-type-notation.html).

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

## cq : propriété des balises {#cq-tags-property}

La propriété `cq:tags` est une table de chaînes `String` utilisée pour stocker un ou plusieurs `TagID` lorsque les auteurs ou les visiteurs du site les appliquent au contenu. La propriété n’a de sens que lorsqu’elle est ajoutée à un nœud qui est défini avec le mixin [`cq:Taggable`](#taggable-content-cq-taggable-mixin).

>[!NOTE]
>
>Pour utiliser AEM fonctionnalité de balisage, les applications développées personnalisées ne doivent pas définir de propriétés de balise autres que `cq:tags`.

## Déplacement et fusion de balises {#moving-and-merging-tags}

Vous trouverez, ci-après, la description des effets dans le référentiel lors du déplacement ou de la fusion de balises à l’aide de la console de balisage.

Lorsqu’une balise A est déplacée ou fusionnée dans une balise B sous `/content/cq:tags` :

* La balise A n’est pas supprimée et reçoit une propriété `cq:movedTo`.
   * `cq:movedTo` pointe vers la balise B.
   * Cette propriété signifie que la balise A a été déplacée ou fusionnée dans la balise B.
   * Le déplacement de la balise B met à jour cette propriété en conséquence.
   * La balise A est donc masquée et conservée uniquement dans le référentiel afin de pouvoir résoudre les ID de balise dans les noeuds de contenu pointant vers la balise A.
   * Tag Garbage Collector supprime les balises telles que la balise A une fois que plus aucun nœud de contenu ne pointe vers elles.
   * Une valeur spéciale pour la propriété `cq:movedTo` est `nirvana` : elle est appliquée lorsque la balise est supprimée. Cependant, elle ne peut pas être supprimée du référentiel, car des sous-balises avec une propriété `cq:movedTo` doivent être conservées.

     >[!NOTE]
     >
     >La propriété `cq:movedTo` n’est ajoutée à la balise déplacée ou fusionnée que si l’une de ces conditions est remplie :
     >
     > 1. La balise est utilisée dans le contenu (ce qui signifie qu’elle comporte une référence). OU
     > 1. La balise comporte des enfants qui ont déjà été déplacés.
     >
* La balise B est créée (en cas de déplacement) et reçoit une `cq:backlinks` .
   * `cq:backlinks` conserve les références dans l’autre direction. En d’autres termes, il conserve une liste de toutes les balises qui ont été déplacées ou fusionnées avec la balise B.
   * Cette fonctionnalité est principalement nécessaire pour conserver `cq:movedTo` propriétés mises à jour lorsque la balise B est également déplacée/fusionnée/supprimée ou lorsque la balise B est activée, auquel cas toutes ses balises de lien arrière doivent être activées.

     >[!NOTE]
     >
     >La propriété `cq:backlinks` n’est ajoutée à la balise déplacée ou fusionnée que si l’une de ces conditions est remplie :
     >
     > 1. La balise est utilisée dans le contenu (ce qui signifie qu’elle comporte une référence), ou
     > 1. La balise comporte des enfants qui ont déjà été déplacés.

La lecture d’une propriété `cq:tags` d’un nœud de contenu implique la résolution suivante :

1. S’il n’existe aucune correspondance sous `/content/cq:tags`, aucune balise n’est renvoyée.
1. Si la propriété `cq:movedTo` est définie pour la balise, l’ID de balise référencé est suivi.
   * Cette étape est répétée aussi longtemps que la balise suivie contient la propriété `cq:movedTo`.
1. Si la balise suivie n’est pas associée à une propriété `cq:movedTo`, elle est lue.

Pour publier la modification lorsqu’une balise a été déplacée ou fusionnée, le nœud `cq:Tag` et tous ses liens retours doivent être répliqués. Cette réplication est automatiquement effectuée lorsque la balise est activée dans la console d’administration des balises.

Les mises à jour ultérieures apportées à la propriété `cq:tags` de la page nettoient automatiquement les anciennes références. Le nettoyage est déclenché car la résolution d’une balise déplacée via l’API renvoie la balise de destination, fournissant ainsi l’identifiant de balise de destination.
