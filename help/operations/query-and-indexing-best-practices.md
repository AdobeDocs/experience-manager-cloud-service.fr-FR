---
title: Bonnes pratiques en matière de requête et d’indexation
description: Découvrez comment optimiser vos index et requêtes en fonction des bonnes pratiques d’Adobe.
topic-tags: best-practices
exl-id: 37eae99d-542d-4580-b93f-f454008880b1
source-git-commit: afeff7cfb8606eb58126a4ca62ce9e6e58c44215
workflow-type: tm+mt
source-wordcount: '1563'
ht-degree: 82%

---

# Bonnes pratiques en matière de requête et d’indexation {#query-and-indexing-best-practices}

Dans AEM as a Cloud Service, tous les aspects opérationnels concernant l’indexation sont automatisés. Cela permet aux développeurs de se concentrer sur la création de requêtes efficaces et leurs définitions d’index correspondantes.

## Quand utiliser des requêtes {#when-to-use-queries}

Les requêtes sont un moyen d’accéder au contenu, mais elles ne sont pas la seule possibilité. Dans de nombreuses situations, l’accès au contenu du référentiel est plus efficace par d’autres moyens. Vous devez déterminer si les requêtes sont la meilleure manière, et la plus efficace, d’accéder au contenu pour votre cas d’utilisation.

### Référentiel et conception de taxonomie {#repository-and-taxonomy-design}

Lors de la conception de la taxonomie d’un référentiel, plusieurs facteurs doivent être pris en compte. Il s’agit entre autres des contrôles d’accès, de la localisation et de l’héritage des propriétés de composant et de page, et bien plus encore.

Lors de la conception d’une taxonomie qui tient compte de ces facteurs, il est également important de penser à la « traversabilité » de la conception de l’indexation. Dans ce contexte, la traversabilité est la capacité d’une taxonomie à permettre un accès prévisible au contenu en fonction de son chemin d’accès. Cela permet d’obtenir un système plus efficace, plus facile à gérer qu’un système nécessitant l’exécution de plusieurs requêtes.

De plus, lors de la conception d’une taxonomie, il faut considérer si l’ordre importe. Dans les cas où un ordre explicite n’est pas nécessaire et qu’un grand nombre de nœuds frères est attendu, il est préférable d’utiliser un type de nœud non ordonné tel que `sling:Folder` ou `oak:Unstructured`. Dans les cas où un ordre est obligatoire, `nt:unstructured` et `sling:OrderedFolder` serait plus approprié.

### Requêtes dans les composants {#queries-in-components}

Comme les requêtes peuvent être l’une des opérations les plus taxatrices effectuées sur un système AEM, il est préférable de les éviter dans vos composants. L’exécution de plusieurs requêtes à chaque rendu d’une page peut souvent dégrader les performances du système. Deux stratégies sont conseillées pour éviter l’exécution de requêtes lors du rendu de composants : le **[parcours transversal des nœuds](#traversing-nodes)** et la **[pré-récupération des résultats.](#prefetching-results)**

### Parcours des noeuds {#traversing-nodes}

Si le référentiel est conçu de manière à permettre une connaissance préalable de l’emplacement des données requises, le code qui récupère ces données des chemins nécessaires peut être déployé sans avoir à exécuter de requêtes pour les trouver.

Par exemple, le rendu du contenu correspondant à une certaine catégorie. Une méthode consiste à organiser le contenu avec une propriété de catégorie qui peut être interrogée pour renseigner un composant qui affiche des éléments dans une catégorie.

Une meilleure approche serait de structurer ce contenu dans une taxonomie par catégorie afin qu’il puisse être récupéré manuellement.

Par exemple, si le contenu est stocké dans une taxonomie similaire à :

```xml
/content/myUnstructuredContent/parentCategory/childCategory/contentPiece
```

Le nœud `/content/myUnstructuredContent/parentCategory/childCategory` peut simplement être récupéré ; ses tâches enfants peuvent être analysées et utilisées pour le rendu du composant.

En outre, lorsque vous traitez un jeu de résultats petit ou homogène, il peut être plus rapide de parcourir le référentiel et de rassembler les noeuds requis, plutôt que de concevoir une requête pour renvoyer le même jeu de résultats. En règle générale, les requêtes doivent être évitées lorsque cela est possible.

### Prérécupération des résultats {#prefetching-results}

Parfois, le contenu ou les exigences liées à un composant ne permettent pas d’utiliser le parcours transversal des nœuds comme méthode de récupération des données requises. Dans ce cas, les requêtes requises doivent être exécutées avant le rendu du composant afin que des performances optimales soient garanties.

Si les résultats requis pour le composant peuvent être calculés au moment de sa création et qu’aucun changement de contenu n’est attendu, la requête peut être exécutée après que des modifications soient effectuées.

Si les données ou le contenu changent régulièrement, la requête peut être exécutée selon un planning ou via un écouteur pour la mise à jour des données sous-jacentes. Ensuite, les résultats peuvent être écrits à un emplacement partagé dans le référentiel. Tous les composants qui ont besoin de ces données peuvent ensuite extraire les valeurs de ce nœud unique sans avoir à exécuter une requête lors de l’exécution.

Une stratégie similaire peut être utilisée pour conserver le résultat dans un cache en mémoire, qui est renseigné au démarrage et mis à jour chaque fois que des modifications sont effectuées (à l’aide d’un JCR `ObservationListener`ou d’un Sling`ResourceChangeListener`).

## Optimiser les requêtes {#optimizing-queries}

La documentation d’Oak fournit une [présentation générale de l’exécution des requêtes.](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#query-processing) C’est la base de toutes les activités d’optimisation décrites dans ce document.

AEM as a Cloud Service fournit l’outil de performance des requêtes, conçu pour prendre en charge l’implémentation de requêtes efficaces.

* Il affiche les requêtes déjà exécutées avec leurs caractéristiques de performance appropriées et leur plan de requête.
* Il permet d’exécuter des requêtes ad hoc à différents niveaux, en commençant par afficher le plan de requête jusqu’à l’exécution de la requête complète.

L’outil de performance de requête est accessible via [Developer Console dans Cloud Manager.](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=fr#queries) L’outil de performance de requête d’AEM as a Cloud Service fournit plus d’informations sur les détails de l’exécution de la requête à partir des versions 6.x. d’AEM.

Ce graphique illustre le flux général d’utilisation de l’outil de performance des requêtes pour optimiser les requêtes.

![Flux d’optimisation des requêtes](assets/query-optimization-flow.png)

### Utiliser un index {#use-an-index}

Chaque requête doit utiliser un index pour fournir des performances optimales. Dans la plupart des cas, les index prêts à l’emploi existants doivent être suffisants pour gérer les requêtes.

Il arrive que des propriétés personnalisées doivent être ajoutées à un index existant, de sorte que des contraintes supplémentaires puissent être interrogées à l’aide de l’index. Consultez le document [Recherche et indexation de contenu](/help/operations/indexing.md#changing-an-index) pour en savoir plus. La section [Aide-mémoire pour les requêtes JCR](#jcr-query-cheatsheet) de ce document décrit l’aspect que doit prendre une définition de propriété sur un index pour prendre en charge un type de requête spécifique.

### Utiliser les critères appropriés {#use-the-right-criteria}

La contrainte principale sur toute requête doit être une correspondance de propriété, car il s’agit du type le plus efficace. L’ajout d’autres contraintes de propriété limite davantage le résultat.

Le moteur de requête ne prend en compte qu’un seul index. Cela signifie qu’un index existant peut et doit être personnalisé en y ajoutant d’autres propriétés d’index personnalisées.

La section [Aide-mémoire pour les requêtes JCR](#jcr-query-cheatsheet) de ce document répertorie les contraintes disponibles et décrit également ce à quoi une définition d’index doit ressembler pour être récupérée. Utilisez l’[outil Performances des requêtes](#query-performance-tool) pour tester la requête et vous assurer que l’index approprié est utilisé et que le moteur de requête n’a pas besoin d’évaluer les contraintes en dehors de l’index.

### Commande {#ordering}

Si une commande spécifique du résultat est demandée, le moteur de requête peut effectuer deux opérations :

1. L’index peut fournir le résultat complet et dans l’ordre appropriée.
   * Cela fonctionne si les propriétés utilisées pour la mise en ordre sont annotées avec `ordered=true` dans la définition d’index.
1. Le moteur de requête effectue le processus de commande.
   * Cela peut se produire lorsque le moteur de requête effectue un filtrage en dehors de l’index ou que la propriété de commande n’est pas annotée avec la propriété `ordered=true`.
   * Cela nécessite que le jeu de résultats complet soit lu en mémoire pour le tri, ce qui est beaucoup plus lent que la première option.

### Limiter la taille du résultat {#restrict-result-size}

La taille récupérée du résultat de la requête est un facteur important dans les performances de la requête. Comme la récupération du résultat est différée, il y a une différence dans la simple récupération des 20 premiers résultats par rapport à la récupération de 10 000 résultats, tant dans l’exécution que dans l’utilisation de la mémoire.

Cela signifie également que la taille du jeu de résultats ne peut être déterminée correctement que si tous les résultats sont récupérés. Pour cette raison, l’ensemble des résultats récupérés doit toujours être limité, soit en augmentant la requête (voir la section [Aide-mémoire pour les requêtes JCR](#jcr-query-cheatsheet) pour plus de détails) ou en limitant la lecture des résultats.

Une telle limite empêche également le moteur de requête de consulter la **limite de traversée** de 100 000 nœuds, ce qui entraîne un arrêt forcé de la requête.

Reportez-vous à la section [Requêtes avec des résultats volumineux](#queries-with-large-result-sets) de ce document si un jeu de résultats potentiellement volumineux doit être complètement traité.

## Aide-mémoire pour les requêtes JCR {#jcr-query-cheatsheet}

Pour prendre en charge la création de requêtes JCR et de définitions d’index efficaces, la section [Aide-mémoire pour les requêtes JCR](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/practices/best-practices-for-queries-and-indexing.html?lang=fr#jcrquerycheatsheet) peut être téléchargée et utilisée comme référence pendant le développement.

Il contient des exemples de requêtes pour QueryBuilder, XPath et SQL-2, couvrant plusieurs scénarios qui se comportent différemment en termes de performances des requêtes. Il fournit également des recommandations sur la version ou la personnalisation d’index Oak. Le contenu de cet aide-mémoire s’applique à AEM as a Cloud Service ainsi qu’à la version 6.5 d’AEM.

## Requêtes avec jeux de résultats volumineux {#queries-with-large-result-sets}

Bien qu’il soit recommandé d’éviter les requêtes avec des jeux de résultats volumineux, il existe des cas valides où des jeux de résultats volumineux doivent être traités. Souvent la taille du résultat n’est pas connue à l’avance, certaines précautions doivent donc être prises pour rendre le traitement fiable.

* La requête ne doit pas être exécutée dans une demande. Au lieu de cela, la requête doit être exécutée dans le cadre d’une tâche Sling ou d’un workflow AEM. Ces derniers ne comportent aucune limite dans leur exécution totale et sont redémarrés au cas où l’instance tomberait en panne pendant le traitement de la requête et de ses résultats.
* Pour dépasser la limite de requête de 100 000 nœuds, vous devez utiliser [Pagination de jeu de clés](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Keyset_Pagination) et diviser la requête en plusieurs sous-requêtes.

## Traversée de référentiel {#repository-traversal}

Les requêtes qui traversent le référentiel n’utilisent pas d’index et se connectent avec un message similaire à ce qui suit.

```text
28.06.2022 13:32:52.804 *WARN* [127.0.0.1 [1656415972414] POST /libs/settings/granite/operations/diagnosis/granite_queryperformance.explain.json HTTP/1.1] org.apache.jackrabbit.oak.plugins.index.Cursors$TraversingCursor Traversed 98000 nodes with filter Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a /* xpath: //* */, path=*) called by com.adobe.granite.queries.impl.explain.query.ExplainQueryServlet.getHeuristics; consider creating an index or changing the query
```

Grâce à ce fragment de code de journal, vous pouvez déterminer :

* La requête elle-même : `//*`
* Le code Java qui a exécuté cette requête : `com.adobe.granite.queries.impl.explain.query.ExplainQueryServlet::getHeuristics` pour aider à identifier le créateur de la requête.

Grâce à ces informations, il est possible d’optimiser cette requête à l’aide des méthodes décrites dans la section [Optimisation des requêtes](#optimizing-queries) de ce document.
