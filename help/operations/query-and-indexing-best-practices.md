---
title: Bonnes pratiques en matière de requête et d’indexation
description: Découvrez comment optimiser vos index et requêtes en fonction des bonnes pratiques d’Adobe.
topic-tags: best-practices
exl-id: 37eae99d-542d-4580-b93f-f454008880b1
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '3133'
ht-degree: 49%

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

Comme les requêtes peuvent être l’une des opérations les plus contraignantes effectuées sur un système AEM, il est préférable de les éviter dans vos composants. L’exécution de plusieurs requêtes à chaque rendu de page peut souvent dégrader les performances du système. Deux stratégies sont conseillées pour éviter l’exécution de requêtes lors du rendu de composants : le **[parcours transversal des nœuds](#traversing-nodes)** et la **[pré-récupération des résultats.](#prefetching-results)**

### Parcours transversal des nœuds {#traversing-nodes}

Si le référentiel est conçu de manière à permettre une connaissance préalable de l’emplacement des données requises, le code qui récupère ces données dans les chemins nécessaires peut être déployé sans avoir à exécuter de requêtes pour le trouver.

Par exemple, le rendu de contenu correspondant à une certaine catégorie. Une méthode consiste à organiser le contenu avec une propriété de catégorie qui peut être interrogée pour renseigner un composant qui affiche des éléments dans une catégorie.

Une meilleure approche serait de structurer ce contenu dans une taxonomie par catégorie afin qu’il puisse être récupéré manuellement.

Par exemple, si le contenu est stocké dans une taxonomie similaire à :

```xml
/content/myUnstructuredContent/parentCategory/childCategory/contentPiece
```

Le nœud `/content/myUnstructuredContent/parentCategory/childCategory` peut simplement être récupéré ; ses tâches enfants peuvent être analysées et utilisées pour le rendu du composant.

En outre, lorsque vous traitez un ensemble de résultats petit ou homogène, il peut être plus rapide de parcourir le référentiel et de rassembler les nœuds requis, plutôt que de concevoir une requête pour renvoyer le même ensemble de résultats. En règle générale, les requêtes doivent être évitées lorsque cela est possible.

### Prérécupération des résultats {#prefetching-results}

Parfois, le contenu ou les exigences liées à un composant ne permettent pas d’utiliser le parcours transversal des nœuds comme méthode de récupération des données requises. Dans ce cas, les requêtes requises doivent être exécutées avant le rendu du composant afin que des performances optimales soient garanties.

Si les résultats requis pour le composant peuvent être calculés au moment de sa création et qu’aucun changement de contenu n’est attendu, la requête peut être exécutée après que des modifications soient effectuées.

Si les données ou le contenu changent régulièrement, la requête peut être exécutée selon un planning ou via un listener pour la mise à jour des données sous-jacentes. Ensuite, les résultats peuvent être écrits à un emplacement partagé dans le référentiel. Tous les composants qui ont besoin de ces données peuvent ensuite extraire les valeurs de ce nœud unique sans avoir à exécuter une requête lors de l’exécution.

Une stratégie similaire peut être utilisée pour conserver le résultat dans un cache en mémoire, qui est renseigné au démarrage et mis à jour chaque fois que des modifications sont effectuées (à l’aide d’un JCR `ObservationListener`ou d’un Sling`ResourceChangeListener`).

## Optimiser les requêtes {#optimizing-queries}

La documentation d’Oak fournit une [présentation générale de l’exécution des requêtes.](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#query-processing) C’est la base de toutes les activités d’optimisation décrites dans ce document.

AEM as a Cloud Service fournit la variable [Outil Performances des requêtes](#query-performance-tool), conçu pour prendre en charge l’implémentation de requêtes efficaces.

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

Voir la section [Requêtes avec des jeux de résultats volumineux](#queries-with-large-result-sets) de ce document si un jeu de résultats potentiellement important doit être traité complètement.

## Outil Performances des requêtes {#query-performance-tool}

L’outil de performance de requête (situé à l’adresse `/libs/granite/operations/content/diagnosistools/queryPerformance.html` et disponible via le [Developer Console dans Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=fr#queries)) fournit -
* Liste de toutes les &quot;requêtes lentes&quot; ; actuellement définies comme étant celles qui lisent/analysent plus de 5 000 lignes.
* Une liste de &quot;Requêtes populaires&quot;
* L’outil &quot;Expliquer la requête&quot; pour comprendre comment une requête particulière sera exécutée par Oak.

![Outil Performances des requêtes](assets/query-performance-tool.png)

Les tables &quot;Requêtes lentes&quot; et &quot;Requêtes populaires&quot; incluent -
* L’instruction de requête elle-même.
* Détails du dernier thread qui a exécuté la requête, permettant d’identifier la fonction de page ou d’application exécutant la requête.
* Score &quot;Lecture d’optimisation&quot; pour la requête.
   * Il s’agit du ratio entre le nombre de lignes/noeuds analysés pour exécuter la requête et le nombre de résultats correspondants lus.
   * Une requête pour laquelle chaque restriction (et tout ordre) peut être traité à l’index aura généralement un score supérieur ou égal à 90 %.
* Détails du nombre maximal de lignes -
   * Lecture : indiquant qu’une ligne a été incluse dans un jeu de résultats.
   * Analysé : indiquant qu’une ligne a été incluse dans les résultats de la requête d’index sous-jacente (dans le cas d’une requête indexée) ou lue à partir du magasin de noeuds (dans le cas d’une traversée du référentiel).

Ces tables permettent d’identifier les requêtes qui ne sont pas entièrement indexées (voir [Utilisation d’un index](#use-an-index) ou lisent trop de noeuds (voir également [Traverse du référentiel](#repository-traversal) et [Traverse d’index](#index-traversal)). De telles requêtes seront mises en évidence, avec les zones de préoccupation appropriées indiquées en rouge.

La variable `Reset Statistics` est fournie pour supprimer toutes les statistiques existantes collectées dans les tables. Cela permet l&#39;exécution d&#39;une requête particulière (soit via l&#39;application elle-même, soit via l&#39;outil Explain Query ) et l&#39;analyse des statistiques d&#39;exécution.

### Expliquer la requête

L’outil Expliquer la requête permet aux développeurs de comprendre le plan d’exécution de la requête (voir [Lecture du plan d’exécution de la requête](#reading-query-execution-plan)), y compris les détails des index utilisés lors de l’exécution de la requête. Vous pouvez l’utiliser pour comprendre l’efficacité avec laquelle une requête est indexée pour prédire ou pour analyser rétrospectivement ses performances.

#### Expliquer une requête

Pour expliquer une requête, procédez comme suit :

* Sélectionnez la langue de requête appropriée à l’aide du `Language` menu déroulant.
* Saisissez l’instruction de requête dans le champ `Query` champ .
* Si nécessaire, sélectionnez le mode d’exécution de la requête à l’aide des cases à cocher fournies.
   * Par défaut, les requêtes JCR n’ont pas besoin d’être exécutées pour identifier le plan d’exécution de la requête (ce n’est pas le cas pour les requêtes QueryBuilder).
   * Trois options sont proposées pour exécuter la requête :
      * `Include Execution Time` - exécutez la requête, mais ne tentez pas de lire les résultats.
      * `Read first page of results` - exécuter la requête et lire la première &quot;page&quot; de 20 résultats (réplication des bonnes pratiques d’exécution des requêtes).
      * `Include Node Count` - exécuter la requête et lire l&#39;ensemble des résultats (ce qui n&#39;est généralement pas conseillé - voir [Traverse d’index](#index-traversal)).

#### Fenêtre contextuelle Explication de la requête {#query-explanation-popup}

![Fenêtre contextuelle Explication de la requête](./assets/query-explanation-popup.png)

Après avoir sélectionné `Explain`, une fenêtre contextuelle s’affiche pour l’utilisateur décrivant le résultat de l’explication de la requête (et l’exécution, si sélectionnée).
Cette fenêtre contextuelle contient des détails sur -
* Index utilisés lors de l’exécution de la requête (ou aucun index si la requête est exécutée à l’aide de [Traverse du référentiel](#repository-traversal)).
* Le temps d’exécution (si `Include Execution Time` case à cocher cochée) et le nombre de résultats lus (si `Read first page of results` ou `Include Node Count` cochez les cases ).
* Le plan d’exécution, permettant une analyse détaillée de l’exécution de la requête - voir [Lecture du plan d’exécution de la requête](#reading-query-execution-plan) pour savoir comment interpréter cela.
* Chemins des 20 premiers résultats de la requête (si `Read first page of results` case à cocher cochée)
* Les logs complets de la planification des requêtes, indiquant les coûts relatifs des index pris en compte pour l&#39;exécution de cette requête (l&#39;index avec le coût le plus bas sera celui choisi).

#### Lecture du plan d’exécution de la requête {#reading-query-execution-plan}

Le plan d’exécution de la requête contient tout ce qui est nécessaire pour prédire (ou expliquer) les performances d’une requête particulière. Comprenez l’efficacité de l’exécution de la requête en comparant les restrictions et l’ordre de la requête JCR (ou Query Builder) d’origine à la requête exécutée dans l’index sous-jacent (Lucene, Elastic ou Property).

Examinez la requête suivante :

```
/jcr:root/content/dam//element(*, dam:Asset) [jcr:content/metadata/dc:title = "My Title"] order by jcr:created
```

...qui contient -
* 3 restrictions
   * Type de nœud (`dam:Asset`)
   * Chemin (descendants) `/content/dam`)
   * Propriété (`jcr:content/metadata/dc:title = "My Title"`)
* Classement par `jcr:created` property

L’explication de cette requête entraîne le plan suivant :

```
[dam:Asset] as [a] /* lucene:damAssetLucene-9(/oak:index/damAssetLucene-9) +:ancestors:/content/dam +jcr:content/metadata/dc:title:My Title ordering:[{ propertyName : jcr:created, propertyType : UNDEFINED, order : ASCENDING }] where ([a].[jcr:content/metadata/dc:title] = 'My Title') and (isdescendantnode([a], [/content/dam])) */
```

Dans ce plan, la section décrivant la requête exécutée dans l’index sous-jacent est -

```
lucene:damAssetLucene-9(/oak:index/damAssetLucene-9) +:ancestors:/content/dam +jcr:content/metadata/dc:title:My Title ordering:[{ propertyName : jcr:created, propertyType : UNDEFINED, order : ASCENDING }]
```

Cette section du plan stipule que :
* Un index est utilisé pour exécuter cette requête.
   * Dans ce cas, l’index Lucene `/oak:index/damAssetLucene-9` est utilisé. Les informations restantes sont donc indiquées dans la syntaxe de requête Lucene.
* Les 3 restrictions sont gérées par l’index :
   * Restriction du type de noeud
      * implicite, car `damAssetLucene-9` répertorie uniquement les noeuds de type dam:Asset.
   * Restriction de chemin
      * car `+:ancestors:/content/dam` apparaît dans la requête Lucene.
   * Restriction des propriétés
      * car `+jcr:content/metadata/dc:title:My Title` apparaît dans la requête Lucene.
* L’ordre est géré par l’index.
   * car `ordering:[{ propertyName : jcr:created, propertyType : UNDEFINED, order : ASCENDING }]`  apparaît dans la requête Lucene.

Une telle requête est susceptible de fonctionner correctement, puisque les résultats renvoyés par la requête d’index ne seront pas filtrés davantage dans le moteur de requête (mis à part le filtrage du contrôle d’accès). Cependant, il est toujours possible qu’une telle requête s’exécute lentement si les bonnes pratiques ne sont pas suivies. Voir [Traverse d’index](#index-traversal) ci-dessous

Considérer une requête différente -

```
/jcr:root/content/dam//element(*, dam:Asset) [jcr:content/metadata/myProperty = "My Property Value"] order by jcr:created
```

...qui contient -
* 3 restrictions
   * Type de nœud (`dam:Asset`)
   * Chemin (descendants) `/content/dam`)
   * Propriété (`jcr:content/metadata/myProperty = "My Property Value"`)
* Classement par `jcr:created` property**

L’explication de cette requête entraîne le plan suivant :

```
[dam:Asset] as [a] /* lucene:damAssetLucene-9-custom-1(/oak:index/damAssetLucene-9-custom-1) :ancestors:/content/dam ordering:[{ propertyName : jcr:created, propertyType : UNDEFINED, order : ASCENDING }] where ([a].[jcr:content/metadata/myProperty] = 'My Property Value') and (isdescendantnode([a], [/content/dam])) */
```

Dans ce plan, la section décrivant la requête exécutée dans l’index sous-jacent est -

```
lucene:damAssetLucene-9(/oak:index/damAssetLucene-9) :ancestors:/content/dam ordering:[{ propertyName : jcr:created, propertyType : UNDEFINED, order : ASCENDING }]
```

Cette section du plan stipule que :
* Seules 2 (sur 3) restrictions sont traitées par l’index :
   * Restriction du type de noeud
      * implicite, car `damAssetLucene-9` répertorie uniquement les noeuds de type dam:Asset.
   * Restriction de chemin
      * car `+:ancestors:/content/dam` apparaît dans la requête Lucene.
* Restriction des propriétés `jcr:content/metadata/myProperty = "My Property Value"` n’est pas exécuté à l’index, mais sera appliqué en tant que moteur de requête filtrant sur les résultats de la requête Lucene sous-jacente.
   * Ceci est dû au fait que `+jcr:content/metadata/myProperty:My Property Value` n’apparaît pas dans la requête Lucene, car cette propriété n’est pas indexée dans la variable `damAssetLucene-9` index utilisé pour cette requête.

Ce plan d’exécution de requête génère chaque ressource sous `/content/dam` à partir de l’index, puis filtré davantage par le moteur de requête (qui inclura uniquement ceux correspondant à la restriction de propriété non indexée dans le jeu de résultats).

Même si seulement un faible pourcentage de ressources correspond à la restriction `jcr:content/metadata/myProperty = "My Property Value"`, la requête doit lire un grand nombre de noeuds pour (tenter) remplir la &quot;page&quot; de résultats demandée. Cela peut entraîner une requête peu performante, qui s’affichera comme ayant une faible valeur `Read Optimization` score dans l’outil de performances des requêtes) et peut entraîner des messages AVERTISSEMENT indiquant que de grands nombres de noeuds sont parcourus (voir [Traverse d’index](#index-traversal)).

Pour optimiser les performances de cette seconde requête, créez une version personnalisée du `damAssetLucene-9` index (`damAssetLucene-9-custom-1`) et ajoutez la définition de propriété suivante :

```
"myProperty": {
  "jcr:primaryType": "nt:unstructured",
  "propertyIndex": true,
  "name": "jcr:content/metadata/myProperty"
}
```

## Aide-mémoire pour les requêtes JCR {#jcr-query-cheatsheet}

Pour prendre en charge la création de requêtes JCR et de définitions d’index efficaces, la section [Aide-mémoire pour les requêtes JCR](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/practices/best-practices-for-queries-and-indexing.html?lang=fr#jcrquerycheatsheet) peut être téléchargée et utilisée comme référence pendant le développement.

Il contient des exemples de requêtes pour QueryBuilder, XPath et SQL-2, couvrant plusieurs scénarios qui se comportent différemment en termes de performances des requêtes. Il fournit également des recommandations sur la version ou la personnalisation d’index Oak. Le contenu de cet aide-mémoire s’applique à AEM as a Cloud Service ainsi qu’à la version 6.5 d’AEM.

## Bonnes pratiques relatives à la définition d’index {#index-definition-best-practices}

Vous trouverez ci-dessous quelques bonnes pratiques à prendre en compte lors de la définition ou de l’extension d’index.

* Pour les types de noeuds qui comportent des index existants (tels que `dam:Asset` ou `cq:Page`) préfèrent l’extension des index prêts à l’emploi à l’ajout de nouveaux index.
   * L’ajout de nouveaux index, notamment des index de texte intégral, sur le `dam:Asset` Le type de noeud est fortement déconseillé (voir [cette note](/help/operations/indexing.md##index-names-index-names)).
* Lors de l’ajout de nouveaux index
   * Définissez toujours des index de type &quot;lucene&quot;.
   * Utilisez une balise d’index dans la définition d’index (et la requête associée) et `selectionPolicy = tag` pour s’assurer que l’index n’est utilisé que pour les requêtes prévues.
   * Assurez-vous que `queryPaths` et `includedPaths` sont fournies (généralement avec les mêmes valeurs).
   * Utilisation `excludedPaths` pour exclure les chemins qui ne contiendront pas de résultats utiles.
   * Utilisation `analyzed` propriétés uniquement lorsque cela est nécessaire, par exemple lorsque vous devez utiliser une restriction de requête en texte intégral uniquement pour cette propriété.
   * Toujours spécifier `async = [ async, nrt ] `, `compatVersion = 2` et `evaluatePathRestrictions = true`.
   * Spécification uniquement `nodeScopeIndex = true` si vous avez besoin d’un index de texte intégral nodescope.

>[!NOTE]
>
>Pour plus d’informations, voir [Documentation de l’index Lucene Oak](https://jackrabbit.apache.org/oak/docs/query/lucene.html).

Les vérifications de pipeline d’Automated Cloud Manager appliqueront certaines des bonnes pratiques décrites ci-dessus.

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

### Traverse d’index {#index-traversal}

Les requêtes qui utilisent un index, mais qui lisent toujours un grand nombre de noeuds, sont enregistrées avec un message similaire à ce qui suit (notez le terme `Index-Traversed` plutôt que `Traversed`).

```text
05.10.2023 10:56:10.498 *WARN* [127.0.0.1 [1696502982443] POST /libs/settings/granite/operations/diagnosis/granite_queryperformance.explain.json HTTP/1.1] org.apache.jackrabbit.oak.plugins.index.search.spi.query.FulltextIndex$FulltextPathCursor Index-Traversed 60000 nodes with filter Filter(query=select [jcr:path], [jcr:score], * from [dam:Asset] as a where isdescendantnode(a, '/content/dam') order by [jcr:content/metadata/unindexedProperty] /* xpath: /jcr:root/content/dam//element(*, dam:Asset) order by jcr:content/metadata/unindexedProperty */, path=/content/dam//*)
```

Cela peut se produire pour plusieurs raisons :
1. Toutes les restrictions de la requête ne peuvent pas être traitées à l’index.
   * Dans ce cas, un sur-ensemble du jeu de résultats final est lu à partir de l’index et ensuite filtré dans le moteur de requête.
   * Cette opération est beaucoup plus lente que l’application de restrictions dans la requête d’index sous-jacente.
1. La requête est triée par une propriété qui n’est pas marquée comme &quot;classée&quot; dans l’index.
   * Dans ce cas, tous les résultats renvoyés par l’index doivent être lus par le moteur de requête et triés en mémoire.
   * Cette opération est beaucoup plus lente que l’application d’un tri dans la requête d’index sous-jacente.
1. L’exécuteur de la requête tente d’itérer un jeu de résultats volumineux.
   * Cette situation peut se produire pour plusieurs raisons, comme indiqué ci-dessous :

| Cause  | Atténuation |
|----------|--------------|
| La Commission de `p.guessTotal` (ou l’utilisation d’un paramètre guessTotal très volumineux) provoquant l’itération de QueryBuilder sur un grand nombre de résultats comptant les résultats. | Fournir `p.guessTotal` avec une valeur appropriée |
| Utilisation d’une limite importante ou illimitée dans Query Builder (c’est-à-dire `p.limit=-1`) | Utilisez la valeur appropriée pour `p.limit` (idéalement, 1 000 ou moins) |
| Utilisation d’un prédicat de filtrage dans Query Builder qui filtre un grand nombre de résultats de la requête JCR sous-jacente | Remplacer les prédicats de filtrage par des restrictions qui peuvent être appliquées dans la requête JCR sous-jacente |
| Utilisation d’un tri basé sur un comparateur dans QueryBuilder | Remplacez par un ordre basé sur les propriétés dans la requête JCR sous-jacente (à l’aide de propriétés indexées selon l’ordre). |
| Filtrage d’un grand nombre de résultats en raison du contrôle d’accès | Appliquez une propriété indexée supplémentaire ou une restriction de chemin à la requête pour refléter le contrôle d’accès. |
| Utilisation de la &quot;pagination décalée&quot; avec un décalage important | Envisager d’utiliser [Pagination du clavier](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Keyset_Pagination) |
| Itération d’un nombre de résultats important ou illimité | Envisager d’utiliser [Pagination du clavier](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Keyset_Pagination) |
| Index incorrect sélectionné | Utilisez des balises dans la définition de requête et d’index pour vous assurer que l’index attendu est utilisé. |
