---
title: Optimisation des requêtes GraphQL
description: Découvrez comment optimiser vos requêtes GraphQL lors du filtrage, de la pagination et du tri de vos fragments de contenu dans Adobe Experience Manager as a Cloud Service pour une diffusion de contenu sans interface utilisateur.
source-git-commit: e156ed7348815e02c942cb8feace70c675956752
workflow-type: tm+mt
source-wordcount: '1192'
ht-degree: 0%

---


# Optimisation des requêtes GraphQL {#optimizing-graphql-queries}

>[!NOTE]
>
>Avant d’appliquer ces recommandations d’optimisation, tenez compte des [Mise à jour des fragments de contenu pour la pagination et le tri dans le filtrage GraphQL](/help/headless/graphql-api/graphql-paging-sorting-content-update.md) pour de meilleures performances.

Sur une instance d’AEM avec un grand nombre de fragments de contenu partageant le même modèle, les requêtes de liste GraphQL peuvent devenir coûteuses (en termes de ressources).

Ceci est dû au fait que *all* les fragments qui partagent un modèle utilisé dans la requête GraphQL doivent être chargés en mémoire. Cela consomme à la fois du temps et de la mémoire. Le filtrage, qui peut réduire le nombre d’éléments dans le jeu de résultats (final), ne peut être appliqué que. **after** chargement de l’ensemble de résultats en mémoire.

Cela peut donner l’impression que même de petits ensembles de résultats (peuvent) entraîner de mauvaises performances. Toutefois, en réalité, la lenteur est due à la taille de l’ensemble de résultats initial, car il doit être géré en interne avant que le filtrage puisse être appliqué.

Pour réduire les problèmes de performances et de mémoire, ce jeu de résultats initial doit être conservé aussi petit que possible.

AEM propose deux méthodes d’optimisation des requêtes GraphQL :

* [Filtrage hybride](#hybrid-filtering)
* [Pagination](#paging) (ou pagination)

   * [Tri](#sorting) n’est pas directement lié à l’optimisation, mais est lié à la pagination.

Chaque approche comporte ses propres cas d’utilisation et ses propres limites. Ce document fournit des informations sur le filtrage hybride et la pagination, avec quelques [bonnes pratiques](#best-practices) pour optimiser les requêtes GraphQL.

## Filtrage hybride {#hybrid-filtering}

Le filtrage hybride combine le filtrage JCR avec le filtrage AEM.

Il applique un filtre JCR (sous la forme d’une contrainte de requête) avant de charger le jeu de résultats en mémoire pour le filtrage AEM. Cela permet de réduire le jeu de résultats chargé en mémoire, car le filtre JCR supprime les résultats superflus avant.

>[!NOTE]
>
>Pour des raisons techniques (par exemple flexibilité, imbrication de fragments), AEM ne peut pas déléguer l’intégralité du filtrage à JCR.

Cette technique permet de conserver la flexibilité que les filtres GraphQL offrent, tout en déléguant autant de filtrage que possible à JCR.

## Pagination {#paging}

GraphQL dans AEM prend en charge deux types de pagination :

* [pagination basée sur les limites/décalages](/help/headless/graphql-api/content-fragments.md#list-offset-limit)
Il est utilisé pour les requêtes de liste ; qui se terminent par 
`List`; par exemple, `articleList`.
Pour l’utiliser, vous devez indiquer la position du premier élément à renvoyer (le `offset`) et le nombre d’éléments à renvoyer (la variable `limit`, ou taille de page).

* [pagination basée sur le curseur](/help/headless/graphql-api/content-fragments.md#paginated-first-after) (représenté par `first`et `after`) fournit un identifiant unique pour chaque élément ; également appelé curseur.
Dans la requête, vous spécifiez le curseur du dernier élément de la page précédente, plus la taille de la page (le nombre maximal d’éléments à renvoyer).

   Comme la pagination basée sur le curseur ne s’intègre pas dans les structures de données des requêtes basées sur des listes, AEM a introduit `Paginated` type de requête ; par exemple, `articlePaginated`. Les structures et paramètres de données utilisés suivent le [Spécification de connexion du curseur GraphQL](https://relay.dev/graphql/connections.htm).

   >[!NOTE]
   >
   >AEM prend actuellement en charge la pagination (à l’aide de `after`/`first` ).
   >
   >Pagination arrière (à l’aide de `before`/`last` ) n’est pas pris en charge.

## Tri {#sorting}

Le tri ne peut être efficace que si tous les critères de tri sont liés à des fragments de niveau supérieur.

Si l’ordre de tri inclut un ou plusieurs champs situés sur un fragment imbriqué, tous les fragments partageant le modèle de niveau supérieur doivent être chargés en mémoire. Cela a un impact négatif sur les performances.

>[!NOTE]
>
>Le tri sur les champs de niveau supérieur a également un impact (quoique faible) sur les performances.

## Bonnes pratiques {#best-practices}

L’objectif principal de toutes les optimisations est de réduire le jeu de résultats initial. Les bonnes pratiques répertoriées ici fournissent des moyens de le faire. Ils peuvent (et doivent) être combinés.

### Filtrage sur les propriétés de niveau supérieur uniquement {#filter-top-level-properties-only}

Actuellement, le filtrage au niveau JCR ne fonctionne que pour les fragments de niveau supérieur.

Si un filtre s’adresse aux champs d’un fragment imbriqué, AEM doit recharger (en mémoire) tous les fragments qui partagent le modèle sous-jacent.

Vous pouvez toujours optimiser ces requêtes GraphQL en combinant des expressions de filtre sur les champs de fragments de niveau supérieur et ceux des champs de fragments imbriqués avec la propriété [Opérateur ET](#logical-operations-in-filter-expressions).

### Utiliser la structure de contenu {#use-content-structure}

Dans AEM, il est généralement considéré comme une bonne pratique d’utiliser la structure de référentiel pour réduire la portée du contenu à traiter.

Cette approche doit également être appliquée aux requêtes GraphQL.

Pour ce faire, appliquez un filtre sur la variable `_path` champ du fragment de niveau supérieur :

```graphql
{
  someList(filter: {
    _path: {
      _expressions: [ 
        {
          value: "/content/dam/some/sub/path/",
          _operator: STARTS_WITH
        }
      ]
    }
  }) {
    items {
      # ...
    }
  }
}
```

>[!NOTE]
>
>La fin `/` on `value` est requis pour obtenir les meilleures performances.

### Utilisation de la pagination {#use-paging}

Vous pouvez également utiliser la pagination pour réduire le jeu de résultats initial ; en particulier si vos requêtes n’utilisent aucun filtrage et tri.

Si vous filtrez ou triez les fragments imbriqués, les requêtes paginées peuvent être lentes, car AEM peut encore devoir charger de plus grandes quantités de fragments dans la mémoire. Par conséquent, si vous combinez filtrage et pagination, tenez compte des règles de filtrage (comme mentionné ci-dessus).

Pour la pagination, le tri est tout aussi important, car les résultats paginés sont toujours triés, de manière explicite ou implicite.

Si vous souhaitez principalement récupérer uniquement les premières pages, il n’y a aucune différence significative entre l’utilisation de la variable `...List` ou `...Paginated` requêtes. Cependant, si votre application souhaite lire plus d’une ou deux pages, vous devez tenir compte de la variable `...Paginated` , car il fonctionne nettement mieux avec les pages ultérieures.

### Opérations logiques dans les expressions de filtre {#logical-operations-in-filter-expressions}

Si vous filtrez des fragments imbriqués, vous pouvez tout de même utiliser le filtrage JCR en fournissant un filtre d’accompagnement sur un champ de niveau supérieur combiné à l’aide de la variable `AND` de l’opérateur.

Un cas d’utilisation type consiste à restreindre la portée de la requête à l’aide d’un filtre sur la variable `_path` du fragment de niveau supérieur, puis filtrez les champs supplémentaires pouvant se trouver au niveau supérieur ou sur un fragment imbriqué.

Dans ce cas, les différentes expressions de filtre sont combinées avec `AND`. Par conséquent, le filtre sur `_path` peut limiter efficacement l’ensemble de résultats initial. Tous les autres filtres sur les champs de niveau supérieur peuvent également contribuer à réduire le jeu de résultats initial, à condition qu’ils soient combinés avec `AND`.

Expressions de filtre combinées avec `OR` ne peut pas être optimisé si des fragments imbriqués sont impliqués. `OR` les expressions ne peuvent être optimisées que si *non* les fragments imbriqués sont impliqués.

### Éviter le filtrage sur les champs de texte multiligne {#avoid-filtering-multiline-textfields}

Les champs d&#39;un champ de texte multiligne (html, markdown, plaintext, json) ne peuvent pas être filtrés via une requête JCR, car le contenu de ces champs doit être calculé à la volée.

Si vous devez toujours filtrer sur un champ de texte multiligne, pensez à limiter la taille de l’ensemble de résultats initial en ajoutant des expressions de filtre supplémentaires et en les combinant avec `AND`. Limiter la portée en filtrant sur la variable `_path` est également une bonne approche.

### Éviter le filtrage sur les champs virtuels {#avoid-filtering-virtual-fields}

Champs virtuels (la plupart des champs commençant par `_`) sont calculées lors de l’exécution d’une requête GraphQL et ne sont donc pas concernées par le filtrage basé sur JCR.

Une exception importante est la suivante : `_path` qui peut être utilisé efficacement pour réduire la taille du jeu de résultats initial, si le contenu est structuré en conséquence (voir [Utiliser la structure de contenu](#use-content-structure)).

### Filtrage : Exclusions {#filtering-exclusions}

Il existe plusieurs autres situations dans lesquelles une expression de filtre ne peut pas être évaluée au niveau JCR (et doit donc être évitée pour obtenir les meilleures performances) :

* Filtrage des expressions sur un `Float` qui utilisent la variable `_sensitiveness` option de filtre, et où `_sensitiveness` est défini sur toute autre valeur que `0.0` .

* Filtrage des expressions sur un `String` à l’aide de la variable `_ignoreCase` option de filtrage.

* Filtrage sur `null` valeurs.

* Filtres sur des tableaux avec `_apply: ALL_OR_EMPTY`.

* Filtres sur des tableaux avec `_apply: INSTANCES`, `_instances: 0`.

* Filtrage des expressions à l’aide de `CONTAINS_NOT` de l’opérateur.

* Filtrage des expressions sur un `Calendar`, `Date` ou `Time` qui utilisent la variable `NOT_AT` de l’opérateur.
