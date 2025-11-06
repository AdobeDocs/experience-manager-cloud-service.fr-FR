---
title: Framework de balisage AEM
description: Balisez le contenu et utilisez l’infrastructure de balisage AEM pour le classer et l’organiser.
exl-id: 25418d44-aace-4e73-be1a-4b1902f40403
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1559'
ht-degree: 92%

---

# Le cadre de balisage AEM {#aem-tagging-framework}

Le balisage permet de catégoriser et d’organiser le contenu. Les balises peuvent être classées par un espace de noms et par une taxonomie. Pour obtenir des informations détaillées sur l’utilisation des balises :

* Voir [Utilisation des balises](/help/sites-cloud/authoring/sites-console/tags.md) pour plus d’informations sur le balisage du contenu en tant qu’auteur de contenu.
* Consultez Administration des balises pour savoir comment un administrateur ou une administratrice peut créer et gérer des balises et déterminer à quel contenu elles ont été appliquées.

Cet article se concentre sur le cadre sous-jacent qui prend en charge le balisage dans AEM et explique comment l’utiliser en tant que développeur ou développeuse.

## Présentation {#introduction}

Pour baliser le contenu et utiliser le framework de balisage AEM, procédez comme suit :

* La balise doit exister en tant que nœud du type [`cq:Tag`](#cq-tag-node-type) sous le [nœud racine de taxonomie](#taxonomy-root-node).
* Le `NodeType` du nœud de contenu balisé doit inclure le mixin [`cq:Taggable`](#taggable-content-cq-taggable-mixin).
* Le [`TagID`](#tagid) est ajouté à la propriété [`cq:tags`](#cq-tags-property) du nœud de contenu et est résolu sur un nœud de type [`cq:Tag`](#cq-tag-node-type).

## cq:Tag Type de nœud {#cq-tag-node-type}

La déclaration d’une balise est capturée dans le référentiel dans un nœud de type `cq:Tag.`

* Une balise peut être constituée d’un simple mot (`sky`, par exemple) ou représenter une taxonomie hiérarchique (`fruit/apple` par exemple, c’est-à-dire le fruit en tant que catégorie générique et la pomme en étant plus spécifique).
* Les balises sont identifiées par un `TagID` unique.
* Une balise comprend des méta-informations facultatives, telles qu’un titre, des titres localisés et une description. Le titre doit être affiché dans les interfaces utilisateur au lieu de l’`TagID`, le cas échéant.

Le framework de balisage limite également les créateurs et créatrices et les visiteurs et visiteuses du site à n’utiliser que des balises prédéfinies spécifiques.

### Caractéristiques de la balise {#tag-characteristics}

* Le type de nœud est `cq:Tag`.
* Le nom du nœud est un composant de la [`TagID`](#tagid) .
* Le [`TagID`](#tagid) comprend toujours un [espace de noms](#tag-namespace).
* La propriété `jcr:title` (le titre à afficher dans l’interface utilisateur) est facultative.
* La propriété `jcr:description` est facultative.
* Lorsque vous incluez des nœuds enfants, est appelé [balise conteneur](#container-tags).
* La balise est stockée dans le référentiel, sous un chemin d’accès de base appelé [nœud racine de taxonomie](#taxonomy-root-node).

### TagID {#tagid}

Un `TagID` identifie un chemin d’accès qui est résolu sur un nœud de balise dans le référentiel.

En règle générale, la `TagID` est un raccourci `TagID` commençant par l’espace de noms ; il peut également s’agir d’une `TagID` absolue commençant au niveau du [nœud racine de taxonomie](#taxonomy-root-node).

Lorsque le contenu est balisé, la propriété [`cq:tags`](#cq-tags-property) est ajoutée, le cas échéant, au nœud de contenu et le `TagID` est ajouté à la valeur de tableau de la propriété `String`.

Le `TagID` se compose d’un [espace de noms](#tag-namespace), suivi du `TagID` local. Les [balises conteneurs](#container-tags) contiennent des sous-balises qui représentent un ordre hiérarchique dans la taxonomie. Des sous-balises peuvent être utilisées pour référencer des balises identiques à tout `TagID` local. Par exemple, baliser du contenu avec `fruit` est autorisé, même s’il s’agit d’une balise conteneur avec des sous-balises, comme `fruit/apple` et `fruit/banana`.

### Nœud racine de taxonomie {#taxonomy-root-node}

Le nœud racine de taxonomie est le chemin d’accès de base pour toutes les balises du référentiel. Le nœud racine de taxonomie ne peut *pas* être un nœud de type `cq:Tag`.

Dans AEM, le chemin d’accès de base est `/content/cq:tags` et le nœud racine est de type `cq:Folder`.

### Espace de noms des balises {#tag-namespace}

Les espaces de noms vous permettent de regrouper des éléments. Le cas d’utilisation le plus courant consiste à disposer d’un espace de noms par site (par exemple, public ou interne) ou par grande application (par exemple, Sites ou Assets), mais les espaces de noms peuvent être utilisés pour d’autres besoins. Les espaces de noms sont utilisés dans l’interface utilisateur pour n’afficher que le sous-ensemble de balises (c’est-à-dire les balises d’un espace de noms donné) applicable au contenu actuel.

L’espace de noms de la balise est le premier niveau de la sous-arborescence de taxonomie, à savoir le nœud situé juste en dessous du [nœud racine de taxonomie](#taxonomy-root-node). Un espace de noms est un nœud de type `cq:Tag` dont le parent n’est pas de type `cq:Tag`.

Toutes les balises possèdent un espace de noms. Si aucun espace de noms n’est spécifié, la balise est affectée à l’espace de noms par défaut, qui est `TagID` `default`, c’est-à-dire `/content/cq:tags/default`. Dans ce cas, le titre est défini par défaut sur `Standard Tags`.

### Balises conteneurs {#container-tags}

Une balise conteneur est un nœud de type `cq:Tag` contenant le nombre et le type des nœuds enfants, ce qui permet d’enrichir le modèle de balise avec des métadonnées personnalisées.

En outre, les balises conteneurs (ou super-balises) d’une taxonomie servent de sous-combinaison de toutes les sous-balises. Par exemple, du contenu balisé avec `fruit/apple` est considéré comme balisé avec `fruit`, également. Autrement dit, la recherche de contenu balisé avec `fruit` trouve également le contenu balisé avec `fruit/apple`.

### Résolution d’identifiants de balise {#resolving-tagids}

Si l’ID de balise contient le signe deux-points (`:`), celui-ci sépare l’espace de noms de la balise ou de la sous-taxonomie, qui sont alors séparés par des barres obliques (`/`). En l’absence de signe deux-points dans l’ID de balise, l’espace de noms par défaut est impliqué.

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

Pour plus d’informations, voir :

* [Balises dans différentes langues](tagging-applications.md#tags-in-different-languages). Cette section décrit l’utilisation des API en tant que développeur ou développeuse.
* Gestion des balises dans différentes langues. Cette section décrit l’utilisation de la console de balisage en tant qu’administrateur ou administratrice.

### Contrôle d’accès {#access-control}

Les balises existent sous la forme de nœud dans le répertoire sous le [nœud racine de taxonomie](#taxonomy-root-node). Il est possible d’accorder ou de refuser aux auteurs et autrices et aux visiteurs et visiteuses du site le droit de créer des balises dans un espace de noms donné en définissant des listes de contrôle d’accès (ACL) appropriées dans le référentiel.

Refuser les autorisations de lecture sur certains espaces de noms et balises détermine la possibilité d’appliquer des balises à du contenu spécifique.

Une pratique habituelle est la suivante :

* Accorder au groupe/rôle `tag-administrators` l’accès en écriture à tous les espaces de noms (add/modify sous `/content/cq:tags`). Ce groupe est fourni en standard avec AEM.
* Accorder aux utilisateurs/auteurs l’accès en lecture à tous les espaces de noms qu’ils doivent être autorisés à lire (presque tous).
* Accorder aux utilisateurs/auteurs l’accès en écriture aux espaces de noms dont ils doivent être en mesure de définir librement les balises (`add_node` sous `/content/cq:tags/some_namespace`).

## Contenu pouvant être balisé : mixin cq:Taggable {#taggable-content-cq-taggable-mixin}

Pour que les développeurs et développeuses d’application associent le balisage à un type de contenu, l’enregistrement du nœud ([CND](https://jackrabbit.apache.org/jcr/node-type-notation.html)) doit inclure le mixin `cq:Taggable` ou `cq:OwnerTaggable`.

Le mixin `cq:OwnerTaggable`, qui hérite de `cq:Taggable`, sert à indiquer que le contenu peut être classé par propriétaire/auteur. Dans AEM, il s’agit uniquement d’un attribut du nœud `cq:PageContent`. Le mixin `cq:OwnerTaggable` n’est pas requis par le cadre de balisage.

>[!NOTE]
>
>Il est recommandé de n’activer les balises que sur le nœud de niveau supérieur d’un élément de contenu agrégé (ou sur son nœud `jcr:content`). Voici quelques exemples :
>
>* Pages (`cq:Page`) sur lesquelles le nœud `jcr:content` est de type `cq:PageContent`, ce qui inclut le mixin `cq:Taggable`.
>* Ressources (`cq:Asset`) dans lesquelles le nœud `jcr:content/metadata` possède toujours le mixin `cq:Taggable`.

### Notation de type de nœud (CND) {#node-type-notation-cnd}

Les définitions de type de nœud existent dans le référentiel sous la forme de fichiers CND. La notation CND est définie dans le cadre de la [documentation JCR](https://jackrabbit.apache.org/jcr/node-type-notation.html).

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

La propriété `cq:tags` est une table de chaînes `String` utilisée pour stocker un ou plusieurs `TagID` lorsque les auteurs ou les visiteurs du site les appliquent au contenu. La propriété n’a de sens que lorsqu’elle est ajoutée à un nœud qui est défini avec le mixin [`cq:Taggable`](#taggable-content-cq-taggable-mixin).

>[!NOTE]
>
>Pour utiliser la fonctionnalité de balisage d’AEM, les applications personnalisées ne doivent pas définir de propriétés de balise autres que `cq:tags`.

## Déplacer et fusionner des balises {#moving-and-merging-tags}

Vous trouverez, ci-après, la description des effets dans le référentiel lors du déplacement ou de la fusion de balises à l’aide de la console de balisage.

Lorsqu’une balise A est déplacée ou fusionnée dans une balise B sous `/content/cq:tags` :

* La balise A n’est pas supprimée et reçoit une propriété `cq:movedTo`.
   * `cq:movedTo` pointe vers la balise B.
   * Cette propriété signifie que la balise A a été déplacée ou fusionnée dans la balise B.
   * Le déplacement de la balise B met à jour cette propriété en conséquence.
   * La balise A est ainsi masquée et n’est conservée dans le référentiel que pour pouvoir résoudre les ID de balises dans les nœuds de contenu pointant vers la balise A.
   * Tag Garbage Collector supprime les balises telles que la balise A une fois que plus aucun nœud de contenu ne pointe vers elles.
   * Une valeur spéciale pour la propriété `cq:movedTo` est `nirvana` : elle est appliquée lorsque la balise est supprimée. Cependant, elle ne peut pas être supprimée du référentiel, car des sous-balises avec une propriété `cq:movedTo` doivent être conservées.

     >[!NOTE]
     >
     >La propriété `cq:movedTo` n’est ajoutée à la balise déplacée ou fusionnée que si l’une de ces conditions est remplie :
     >
     > 1. La balise est utilisée dans le contenu (ce qui signifie qu’elle comporte une référence). OU
     > 1. La balise comporte des enfants qui ont déjà été déplacés.
     >
* La balise B est créée (dans le cas d’un déplacement) et reçoit une propriété `cq:backlinks`.
   * `cq:backlinks` conserve les références dans l’autre direction. En d’autres termes, il conserve une liste de toutes les balises qui ont été déplacées ou fusionnées avec la balise B.
   * Cette fonctionnalité est surtout nécessaire pour conserver les propriétés `cq:movedTo` à jour lorsque la balise B est également déplacée/fusionnée/supprimée ou que la balise B est activée, auquel cas toutes ses balises de liens retours doivent également être activées.

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

Pour publier la modification lorsqu’une balise a été déplacée ou fusionnée, le nœud `cq:Tag` et tous ses liens retours doivent être répliqués. Cette réplication est réalisée automatiquement lorsque la balise est activée dans la console d’administration des balises.

Les mises à jour ultérieures apportées à la propriété `cq:tags` de la page nettoient automatiquement les anciennes références. Le nettoyage est déclenché, car la résolution d’une balise déplacée via l’API renvoie la balise de destination, fournissant ainsi l’ID de balise de destination.
