---
title: Bonnes pratiques en matière de requête et d’indexation
description: Découvrez comment optimiser vos index et requêtes en fonction des bonnes pratiques d’Adobe.
topic-tags: best-practices
source-git-commit: 565ca9f29c08a741edfd325090588c4bd7ae81f3
workflow-type: tm+mt
source-wordcount: '1563'
ht-degree: 25%

---


# Bonnes pratiques en matière de requête et d’indexation {#query-and-indexing-best-practices}

Dans AEM as a Cloud Service, tous les aspects opérationnels concernant l&#39;indexation sont automatisés. Cela permet aux développeurs de se concentrer sur la création de requêtes efficaces et leurs définitions d’index correspondantes.

## Quand utiliser des requêtes {#when-to-use-queries}

Les requêtes sont un moyen d’accéder au contenu, mais elles ne sont pas la seule possibilité. Dans de nombreuses situations, l’accès au contenu du référentiel est plus efficace par d’autres moyens. Vous devez déterminer si les requêtes sont la meilleure et la plus efficace manière d’accéder au contenu pour votre cas d’utilisation.

### Conception du référentiel et de la taxonomie {#repository-and-taxonomy-design}

Lors de la conception de la taxonomie d’un référentiel, plusieurs facteurs doivent être pris en compte. Il s’agit notamment des contrôles d’accès, de la localisation, de l’héritage des propriétés de composant et de page, etc.

Lors de la conception d’une taxonomie qui tient compte de ces facteurs, il est également important de penser à la « traversabilité » de la conception de l’indexation. Dans ce contexte, la traversabilité est la capacité d’une taxonomie à permettre un accès prévisible au contenu en fonction de son chemin. Cela permet d’obtenir un système plus efficace, plus facile à gérer qu’un système nécessitant l’exécution de plusieurs requêtes.

De plus, lors de la conception d’une taxonomie, il faut considérer si l’ordre importe. Dans les cas où un ordre explicite n’est pas nécessaire et qu’un grand nombre de nœuds frères est attendu, il est préférable d’utiliser un type de nœud non ordonné tel que `sling:Folder` ou `oak:Unstructured`. Lorsque la commande est requise, `nt:unstructured` et `sling:OrderedFolder` serait plus approprié.

### Requêtes au sein de composants {#queries-in-components}

Comme les requêtes peuvent être l’une des opérations les plus intensives sur un système AEM, il est conseillé de les exclure de vos composants. L’exécution de plusieurs requêtes chaque fois qu’une page est rendue peut souvent dégrader les performances du système. Deux stratégies sont conseillées pour éviter l’exécution de requêtes lors du rendu de composants : le **[parcours transversal des nœuds](#traversing-nodes)** et la **[pré-récupération des résultats.](#prefetching-results)**

### Parcours transversal des nœuds {#traversing-nodes}

Si le référentiel est conçu de manière à permettre une connaissance préalable de l’emplacement des données requises, le code qui récupère ces données à partir des chemins nécessaires peut être déployé sans avoir à exécuter des requêtes pour les localiser.

Le rendu de contenu correspondant à une certaine catégorie en est un exemple. L’une des approches consiste à organiser le contenu avec une propriété de catégorie qui peut être interrogée pour remplir un composant présentant des éléments dans une catégorie.

Une meilleure approche consiste à structurer ce contenu dans une taxonomie par catégorie afin qu’il puisse être récupéré manuellement.

Par exemple, si le contenu est stocké dans une taxonomie similaire à :

```xml
/content/myUnstructuredContent/parentCategory/childCategory/contentPiece
```

la valeur `/content/myUnstructuredContent/parentCategory/childCategory` peut simplement être récupéré, ses enfants peuvent être analysés et utilisés pour effectuer le rendu du composant.

En outre, lorsque vous traitez un jeu de résultats de petite taille ou homogène, il est parfois plus rapide de parcourir transversalement le référentiel et de rassembler les nœuds nécessaires plutôt que de créer une requête pour renvoyer le même jeu de résultats. En règle générale, les requêtes doivent être évitées dans la mesure du possible.

### Pré-extraction des résultats {#prefetching-results}

Parfois, le contenu ou les exigences autour du composant ne permettent pas l’utilisation de la traversée de noeuds comme méthode de récupération des données requises. Dans ce cas, les requêtes requises doivent être exécutées avant le rendu du composant afin d’assurer des performances optimales.

Si les résultats requis pour le composant peuvent être calculés au moment de sa création et qu’il n’y a aucune espérance de modification du contenu, la requête peut être exécutée une fois la modification effectuée.

Si les données ou le contenu changent régulièrement, la requête peut être exécutée selon un calendrier ou via un écouteur pour les mises à jour des données sous-jacentes. Ensuite, les résultats peuvent être enregistrés dans un emplacement partagé au sein du référentiel. Tous les composants qui ont besoin de ces données peuvent ensuite extraire les valeurs de ce nœud unique sans avoir à exécuter une requête lors de l’exécution.

Une stratégie similaire peut être utilisée pour conserver le résultat dans un cache en mémoire, qui est renseigné au démarrage et mis à jour chaque fois que des modifications sont effectuées (à l’aide d’un JCR). `ObservationListener` ou Sling `ResourceChangeListener`).

## Optimisation des requêtes {#optimizing-queries}

La documentation d’Oak fournit une [présentation générale de l’exécution des requêtes.](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#query-processing) C’est la base de toutes les activités d’optimisation décrites dans ce document.

AEM as a Cloud Service fournit l’outil de performance des requêtes , conçu pour prendre en charge l’implémentation de requêtes efficaces.

* Il affiche les requêtes déjà exécutées avec leurs caractéristiques de performance et le plan de requête correspondants.
* Il permet d’exécuter des requêtes ad hoc à différents niveaux, en commençant par afficher le plan de requête jusqu’à l’exécution de la requête complète.

L’outil de performance de requête est accessible via le [Developer Console dans Cloud Manager.](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=fr#queries) L’outil de performance de requête d’AEM as a Cloud Service fournit plus d’informations sur les détails de l’exécution de la requête sur la version AEM 6.x.

Ce graphique illustre le flux général d’utilisation de l’outil de performance des requêtes pour optimiser les requêtes.

![Flux d’optimisation des requêtes](assets/query-optimization-flow.png)

### Utilisation d’un index {#use-an-index}

Chaque requête doit utiliser un index pour fournir des performances optimales. Dans la plupart des cas, les index prêts à l’emploi existants doivent être suffisants pour gérer les requêtes.

Il arrive que des propriétés personnalisées doivent être ajoutées à un index existant, de sorte que des contraintes supplémentaires puissent être interrogées à l’aide de l’index. Voir le document [Recherche et indexation de contenu](/help/operations/indexing.md#changing-an-index) pour plus d’informations. Le [Aide-mémoire pour les requêtes JCR](#jcr-query-cheatsheet) la section de ce document décrit l’aspect que doit prendre une définition de propriété sur un index pour prendre en charge un type de requête spécifique.

### Utilisation des critères appropriés {#use-the-right-criteria}

La contrainte Principale sur toute requête doit être une correspondance de propriété, car il s’agit du type le plus efficace. L’ajout d’autres contraintes de propriété limite davantage le résultat.

Le moteur de requête ne prend en compte qu’un seul index. Cela signifie qu’un index existant peut et doit être personnalisé en y ajoutant d’autres propriétés d’index personnalisées.

Le [Aide-mémoire pour les requêtes JCR](#jcr-query-cheatsheet) la section de ce document répertorie les contraintes disponibles et décrit également la manière dont une définition d’index doit avoir l’air pour être récupérée. Utilisez la variable [Outil Performances des requêtes](#query-performance-tool) pour tester la requête et s’assurer que l’index approprié est utilisé et que le moteur de requête n’a pas besoin d’évaluer les contraintes en dehors de l’index.

### Commande {#ordering}

Si un ordre spécifique du résultat est demandé, le moteur de requête peut effectuer deux opérations :

1. L’index peut fournir le résultat complètement et dans le bon ordre.
   * Cela fonctionne si les propriétés utilisées pour la commande sont annotées avec `ordered=true` dans la définition d’index.
1. Le moteur de requête effectue le processus de commande.
   * Cela peut se produire lorsque le moteur de requête effectue un filtrage en dehors de l’index ou que la propriété de classement n’est pas annotée avec la propriété `ordered=true` .
   * Cela nécessite que le jeu de résultats complet soit lu en mémoire pour le tri, ce qui est beaucoup plus lent que la première option.

### Limitation de la taille du résultat {#restrict-result-size}

La taille récupérée du résultat de la requête est un facteur important dans les performances de la requête. Comme le résultat est récupéré de manière paresseuse, il y a une différence dans la simple récupération des 20 premiers résultats par rapport à la récupération de 10 000 résultats, tant dans l’exécution que dans l’utilisation de la mémoire.

Cela signifie également que la taille de l’ensemble de résultats ne peut être déterminée correctement que si tous les résultats sont récupérés. Pour cette raison, le jeu de résultats récupéré doit toujours être limité, soit en augmentant la requête (voir la section [Aide-mémoire pour les requêtes JCR](#jcr-query-cheatsheet) pour plus de détails) ou en limitant la lecture des résultats.

Une telle limite empêche également le moteur de requête d’appuyer sur la variable **limite de traversée** de 100 000 noeuds, ce qui entraîne un arrêt forcé de la requête.

Voir la section [Requêtes avec de grands résultats](#queries-with-large-result-sets) de ce document si un jeu de résultats potentiellement important doit être traité complètement.

## Aide-mémoire pour les requêtes JCR {#jcr-query-cheatsheet}

Pour prendre en charge la création de requêtes JCR et de définitions d’index efficaces, la variable [Aide-mémoire pour les requêtes JCR](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/practices/best-practices-for-queries-and-indexing.html#jcrquerycheatsheet) peut être téléchargé et utilisé comme référence pendant le développement.

Il contient des exemples de requêtes pour QueryBuilder, XPath et SQL-2, couvrant plusieurs scénarios qui se comportent différemment en termes de performances des requêtes. Il fournit également des recommandations sur la création ou la personnalisation d’index Oak. Le contenu de cet aide-mémoire s’applique à AEM as a Cloud Service ainsi qu’à AEM 6.5.

## Requêtes avec jeux de résultats volumineux {#queries-with-large-result-sets}

Bien qu’il soit recommandé d’éviter les requêtes avec des jeux de résultats volumineux, il existe des cas valides où des jeux de résultats volumineux doivent être traités. Souvent la taille du résultat n&#39;est pas connue à l&#39;avance, certaines précautions doivent donc être prises pour rendre le traitement fiable.

* La requête ne doit pas être exécutée dans une requête. Au lieu de cela, la requête doit être exécutée dans le cadre d’une tâche Sling ou d’un workflow AEM. Ils ne comportent aucune limite dans leur exécution totale et sont redémarrés au cas où l’instance tomberait en panne pendant le traitement de la requête et de ses résultats.
* Pour dépasser la limite de requête de 100 000 noeuds, vous devez utiliser [Pagination du clavier](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Keyset_Pagination) et fractionner la requête en plusieurs sous-requêtes.

## Repository Traversal {#repository-traversal}

Les requêtes qui traversent le référentiel n’utilisent pas d’index et se connectent avec un message similaire à ce qui suit.

```text
28.06.2022 13:32:52.804 *WARN* [127.0.0.1 [1656415972414] POST /libs/settings/granite/operations/diagnosis/granite_queryperformance.explain.json HTTP/1.1] org.apache.jackrabbit.oak.plugins.index.Cursors$TraversingCursor Traversed 98000 nodes with filter Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a /* xpath: //* */, path=*) called by com.adobe.granite.queries.impl.explain.query.ExplainQueryServlet.getHeuristics; consider creating an index or changing the query
```

Avec ce fragment de code de journal, vous pouvez déterminer :

* La requête elle-même : `//*`
* Le code Java qui a exécuté cette requête : `com.adobe.granite.queries.impl.explain.query.ExplainQueryServlet::getHeuristics` pour aider à identifier le créateur de la requête.

Avec ces informations, il est possible d&#39;optimiser cette requête à l&#39;aide des méthodes décrites dans la section [Optimisation des requêtes](#optimizing-queries) de ce document.
