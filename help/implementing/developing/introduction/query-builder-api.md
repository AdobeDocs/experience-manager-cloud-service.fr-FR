---
title: API Query Builder
description: La fonctionnalité du Query Builder Asset Share est exposée via une API Java et une API REST.
translation-type: tm+mt
source-git-commit: cfd54f0cd84cef72b6f2fad1a85132c312a19348
workflow-type: tm+mt
source-wordcount: '2069'
ht-degree: 43%

---


# API Query Builder  {#query-builder-api}

Les offres du créateur de Requêtes constituent un moyen facile d’interroger le référentiel de contenu de l’AEM. La fonctionnalité est exposée par le biais d’une API Java et d’une API REST. Ce document décrit ces API.

Le générateur de requêtes côté serveur ([`QueryBuilder`](https://helpx.adobe.com/fr/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/QueryBuilder.html)) accepte une description de requête, crée et exécute une requête XPath, filtre éventuellement le jeu de résultats et, si vous le souhaitez, extrait également des facettes.

La description de requête correspond simplement à un ensemble de prédicats ([`Predicate`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/Predicate.html)). Par exemple, un prédicat de texte intégral correspond à la fonction `jcr:contains()` dans XPath.

Pour chaque type de prédicat, il existe un composant Évaluateur ([`PredicateEvaluator`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/eval/PredicateEvaluator.html)) qui sait comment en effectuer la gestion pour XPath, pour le filtrage et pour l’extraction de facettes. Il est très facile de créer des évaluateurs personnalisés, qui sont activés via l’exécutable du composant OSGi.

L’API REST permet d’accéder exactement aux mêmes fonctionnalités via HTTP, les réponses étant envoyées au format JSON.

>[!NOTE]
>
>L’API QueryBuilder est créée à l’aide de l’API JCR. Vous pouvez également requête le JCR AEM en utilisant l’API JCR depuis un lot OSGi. Pour plus d’informations, voir [Interrogation des données Adobe Experience Manager à l’aide de l’API JCR](https://helpx.adobe.com/experience-manager/using/querying-experience-manager-data-using1.html).

## Session Gem  {#gem-session}

[AEM Gems](https://helpx.adobe.com/fr/experience-manager/kt/eseminars/gems/aem-index.html) est une série de sessions techniques approfondies sur Adobe Experience Manager dispensées par des experts Adobe.

Vous pouvez [examiner la session dédiée au créateur de requêtes](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-search-forms-using-querybuilder.html) pour obtenir un aperçu et utiliser l’outil.

## Exemples de requêtes {#sample-queries}

Ces exemples sont fournis dans la notation de style des propriétés Java. Pour les utiliser avec l’API Java, utilisez un `HashMap` Java comme dans l’exemple d’API suivant.

Pour le servlet JSON `QueryBuilder`, chaque exemple comprend un exemple de lien vers une installation AEM (à l’emplacement par défaut, `http://<host>:<port>`). Notez que vous devez vous connecter à votre instance AEM avant d’utiliser ces liens.

>[!CAUTION]
>
>Par défaut, la servlet JSON du créateur de requêtes affiche un maximum de 10 accès.
>
>L’ajout du paramètre suivant permet au servlet d’afficher tous les résultats de la requête :
>
>`p.limit=-1`

>[!NOTE]
>
>Pour afficher les données JSON renvoyées dans votre navigateur, vous pouvez utiliser un module externe tel que JSONView for Firefox.

### Renvoi de tous les résultats {#returning-all-results}

La requête suivante **renvoie dix résultats** (ou, pour être précis, un maximum de dix), mais vous informe du **Nombre d’accès** réellement disponibles :

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&orderby=path`

```xml
path=/content
1_property=sling:resourceType
1_property.value=wknd/components/structure/page
1_property.operation=like
orderby=path
```

La même requête (avec le paramètre `p.limit=-1`) **renvoie tous les résultats** (il peut s’agir d’un nombre élevé en fonction de votre instance) :

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&orderby=path&p.limit=-1`

```xml
path=/content
1_property=sling:resourceType
1_property.value=wknd/components/structure/page
1_property.operation=like
p.limit=-1
orderby=path
```

### Utilisation de p.devisTotal pour renvoyer les résultats {#using-p-guesstotal-to-return-the-results}

Le paramètre `p.guessTotal` a pour but de renvoyer le nombre approprié de résultats qui peuvent être affichés en combinant les valeurs minimales viables `p.offset` et `p.limit`. Utilisé avec des jeux de résultats de grande taille, ce paramètre offre des performances accrues. Cela évite de calculer le total complet (par exemple, appeler `result.getSize()`) et de lire l&#39;ensemble des résultats, optimisé jusqu&#39;au moteur et à l&#39;index OAK. Il peut s’agir d’une différence significative lorsqu’il y a des centaines de milliers de résultats, à la fois en termes de temps d’exécution et d’utilisation de la mémoire.

L’inconvénient de ce paramètre est que les utilisateurs ne voient pas le total exact. Mais vous pouvez définir un nombre minimum tel que `p.guessTotal=1000` pour qu’il soit toujours lu jusqu’à 1000, de sorte que vous obtenez les totaux exacts pour les jeux de résultats plus petits, mais si c’est plus que cela, vous pouvez uniquement afficher &quot;et plus&quot;.

Ajoutez `p.guessTotal=true` à la requête ci-dessous pour voir comment cela fonctionne :

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&p.guessTotal=true&orderby=path`

```xml
path=/content
1_property=sling:resourceType
1_property.value=wknd/components/structure/page
1_property.operation=like
p.guessTotal=true
orderby=path
```

La requête renvoie la valeur `p.limit` par défaut de `10` résultats avec un décalage `0` :

```xml
"success": true,
"results": 10,
"total": 10,
"more": true,
"offset": 0,
```

Vous pouvez également utiliser une valeur numérique pour comptabiliser jusqu’à un nombre personnalisé de résultats maximum. Utilisez la même requête que ci-dessus, mais définissez la valeur de `p.guessTotal` sur `50` :

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&p.guessTotal=50&orderby=path`

Elle renvoie un nombre dont la limite par défaut est de 10 résultats avec un décalage de 0, mais n’affiche qu’un maximum de 50 résultats :

```xml
"success": true,
"results": 10,
"total": 50,
"more": true,
"offset": 0,
```

### Implémentation de la pagination {#implementing-pagination}

Par défaut, Query Builder fournit également le nombre d’accès. Suivant la taille du résultat, cette opération peut prendre un certain temps, étant donné qu’il est nécessaire de vérifier le contrôle d’accès pour chaque résultat afin de déterminer le nombre exact. Le total est essentiellement utilisé pour implémenter la pagination pour l’IU de l’utilisateur final. Déterminer le nombre exact peut s’avérer particulièrement lent. Aussi, est-il conseillé d’utiliser la fonctionnalité guessTotal pour implémenter la pagination.

L’interface utilisateur peut, par exemple, adapter la méthode suivante :

* Obtenez et affichez le nombre exact du nombre total d’accès ([SearchResult.getTotalMatches()](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/result/SearchResult.html#gettotalmatches) ou total dans la réponse `querybuilder.json`) inférieur ou égal à 100 ;
* Définissez `guessTotal` sur 100 tout en effectuant l’appel vers Query Builder.

* La réponse peut générer le résultat suivant :

   * `total=43`,  `more=false` - Indique que le nombre total d’accès est de 43. L’interface utilisateur peut afficher jusqu’à dix résultats dans le cadre de la première page et fournir la pagination pour les trois pages suivantes. Vous pouvez également utiliser cette implémentation pour afficher un texte descriptif tel que **« 43 résultats trouvés »**.
   * `total=100`,  `more=true` - Indique que le nombre total d’accès est supérieur à 100 et que le nombre exact n’est pas connu. L’interface utilisateur peut afficher jusqu’à dix résultats dans le cadre de la première page et fournir la pagination pour les dix pages suivantes. Vous pouvez également utiliser cette implémentation pour afficher un texte tel que **« plus de 100 résultats trouvés »**. Lorsque l’utilisateur accède aux pages suivantes, les appels effectués vers Query Builder augmentent la limite de `guessTotal`, ainsi que celle des paramètres `offset` et `limit`.

Il est également conseillé d’utiliser `guessTotal` lorsque l’IU doit appliquer un défilement infini, afin d’empêcher Query Builder de déterminer le nombre exact d’accès.

### Rechercher des fichiers jar et les classer, le plus récent en premier {#find-jar-files-and-order-them-newest-first}

`http://<host>:<port>/bin/querybuilder.json?type=nt:file&nodename=*.jar&orderby=@jcr:content/jcr:lastModified&orderby.sort=desc`

```xml
type=nt:file
nodename=*.jar
orderby=@jcr:content/jcr:lastModified
orderby.sort=desc
```

### Rechercher toutes les pages et les classer par dernière modification {#find-all-pages-and-order-them-by-last-modified}

`http://<host>:<port>/bin/querybuilder.json?type=cq:Page&orderby=@jcr:content/cq:lastModified`

```xml
type=cq:Page
orderby=@jcr:content/cq:lastModified
```

### Rechercher toutes les pages et les classer par Dernière modification, Descendant {#find-all-pages-and-order-them-by-last-modified-but-descending}

`http://<host>:<port>/bin/querybuilder.json?type=cq:Page&orderby=@jcr:content/cq:lastModified&orderby.sort=desc`

```xml
type=cq:Page
orderby=@jcr:content/cq:lastModified
orderby.sort=desc
```

### Recherche de texte intégral, triée par score {#fulltext-search-ordered-by-score}

`http://<host>:<port>/bin/querybuilder.json?fulltext=Management&orderby=@jcr:score&orderby.sort=desc`

```xml
fulltext=Management
orderby=@jcr:score
orderby.sort=desc
```

### Rechercher des pages avec une balise spécifique {#search-for-pages-tagged-with-a-certain-tag}

`http://<host>:<port>/bin/querybuilder.json?type=cq:Page&tagid=wknd:activity/cycling&tagid.property=jcr:content/cq:tags`

```xml
type=cq:Page
tagid=wknd:activity/cycling
tagid.property=jcr:content/cq:tags
```

Utilisez le prédicat `tagid` comme dans l&#39;exemple si vous connaissez l&#39;ID de balise explicite.

Utilisez le prédicat `tag` pour le chemin d’accès au titre de la balise (sans espaces).

Dans l&#39;exemple précédent, vous recherchez des pages (`cq:Page` noeuds), vous devez utiliser le chemin relatif de ce noeud pour le prédicat `tagid.property`, qui est `jcr:content/cq:tags`. Par défaut, `tagid.property` serait simplement `cq:tags`.

### Rechercher plusieurs chemins (à l’aide de groupes) {#search-under-multiple-paths-using-groups}

`http://<host>:<port>/bin/querybuilder.json?fulltext=Experience&group.1_path=/content/wknd/us/en/magazine&group.2_path=/content/wknd/us/en/adventures&group.p.or=true`

```xml
fulltext=Experience
group.p.or=true
group.1_path=/content/wknd/us/en/magazine
group.2_path=/content/wknd/us/en/adventures
```

Cette requête utilise un *groupe* (nommé `group`), qui agit pour délimiter les sous-expressions au sein d’une requête, comme le font les parenthèses dans les notations plus standard. Par exemple, la requête précédente peut être exprimée dans un style plus familier comme suit :

`"Experience" and ("/content/wknd/us/en/magazine" or "/content/wknd/us/en/adventures")`

Le prédicat `path` est utilisé à plusieurs reprises dans le groupe de l’exemple précédent. Pour différencier et classer les deux instances du prédicat (l&#39;ordre est requis pour certains prédicats), vous devez préfixer les prédicats avec `N_` où `N` est l&#39;index d&#39;ordonnancement. Dans l&#39;exemple précédent, les prédicats résultants sont `1_path` et `2_path`.

`p` dans `p.or` est un délimiteur spécial qui indique que ce qui suit (dans ce cas un `or`) est un *paramètre* du groupe, par opposition à un sous-prédicat du groupe, tel que `1_path`.

Si aucun `p.or` n&#39;est donné, tous les prédicats sont ETés ensemble, c&#39;est-à-dire que chaque résultat doit satisfaire tous les prédicats.

>[!NOTE]
>
>Vous ne pouvez pas utiliser le même préfixe numérique dans une seule requête, même pour des prédicats différents.

### Rechercher des propriétés {#search-for-properties}

Dans ce cas, vous recherchez toutes les pages d’un modèle donné, à l’aide de la propriété `cq:template` :

`http://<host>:<port>/bin/querybuilder.json?property=cq%3atemplate&property.value=%2fconf%2fwknd%2fsettings%2fwcm%2ftemplates%2fadventure-page-template&type=cq%3aPageContent`

```xml
type=cq:PageContent
property=cq:template
property.value=/conf/wknd/settings/wcm/templates/adventure-page-template
```

L’inconvénient est que les nœuds `jcr:content` des pages sont renvoyés, et non les pages proprement dites. Pour remédier à ce problème, vous pouvez effectuer une recherche par chemin d’accès relatif :

`http://<host>:<port>/bin/querybuilder.json?property=jcr%3acontent%2fcq%3atemplate&property.value=%2fconf%2fwknd%2fsettings%2fwcm%2ftemplates%2fadventure-page-template&type=cq%3aPage`

```xml
type=cq:Page
property=jcr:content/cq:template
property.value=/conf/wknd/settings/wcm/templates/adventure-page-template
```

### Rechercher plusieurs propriétés {#search-for-multiple-properties}

Lorsque vous utilisez plusieurs fois le prédicat property, vous devez ajouter à nouveau les préfixes numériques :

`http://<host>:<port>/bin/querybuilder.json?1_property=jcr%3acontent%2fcq%3atemplate&1_property.value=%2fconf%2fwknd%2fsettings%2fwcm%2ftemplates%2fadventure-page-template&2_property=jcr%3acontent%2fjcr%3atitle&2_property.value=Cycling%20Tuscany&type=cq%3aPage`

```xml
type=cq:Page
1_property=jcr:content/cq:template
1_property.value=/conf/wknd/settings/wcm/templates/adventure-page-template
2_property=jcr:content/jcr:title
2_property.value=Cycling Tuscany
```

### Rechercher plusieurs valeurs de propriété {#search-for-multiple-property-values}

Pour éviter les grands groupes lorsque vous souhaitez rechercher plusieurs valeurs d&#39;une propriété (`"A" or "B" or "C"`), vous pouvez fournir plusieurs valeurs au prédicat `property` :

`http://<host>:<port>/bin/querybuilder.json?property=jcr%3atitle&property.1_value=Cycling%20Tuscany&property.2_value=Ski%20Touring&property.3_value=Whistler%20Mountain%20Biking`

```xml
property=jcr:title
property.1_value=Cycling Tuscany
property.2_value=Ski Touring
property.3_value=Whistler Mountain Biking
```

Pour les propriétés à plusieurs valeurs, vous pouvez également exiger que plusieurs valeurs correspondent (`"A" and "B" and "C"`) :

`http://<host>:<port>/bin/querybuilder.json?property=jcr%3atitle&property.and=true&property.1_value=Cycling%20Tuscany&property.2_value=Ski%20Touring&property.3_value=Whistler%20Mountain%20Biking`

```xml
property=jcr:title
property.and=true
property.1_value=Cycling Tuscany
property.2_value=Ski Touring
property.3_value=Whistler Mountain Biking
```

## Affinage de ce qui est renvoyé {#refining-what-is-returned}

Par défaut, le servlet JSON QueryBuilder renvoie un jeu de propriétés par défaut pour chaque nœud dans les résultats de recherche (par exemple : chemin d’accès, nom, titre, etc.). Pour contrôler les propriétés renvoyées, vous pouvez effectuer l’une des opérations suivantes :

Spécifier

```xml
p.hits=full
```

dans quel cas toutes les propriétés seront incluses pour chaque noeud :

`http://<host>:<port>/bin/querybuilder.json?p.hits=full&property=jcr%3atitle&property.value=Cycling%20Tuscany`

```xml
property=jcr:title
property.value=Cycling Tuscany
p.hits=full
```

Utilisation

```xml
p.hits=selective
```

et spécifiez les propriétés à intégrer

```xml
p.properties
```

séparé par un espace :

`http://<host>:<port>/bin/querybuilder.json?p.hits=selective&p.properties=sling%3aresourceType%20jcr%3aprimaryType&property=jcr%3atitle&property.value=Cycling%20Tuscany`

```xml
property=jcr:title
property.value=Cycling Tuscany
p.hits=selective
p.properties=sling:resourceType jcr:primaryType
```

Vous pouvez également inclure des noeuds enfants dans la réponse du créateur de Requêtes. Pour ce faire, vous devez spécifier

```xml
p.nodedepth=n
```

où `n` correspond au nombre de niveaux que la requête doit renvoyer. Notez que pour qu’un noeud enfant soit renvoyé, il doit être spécifié par le sélecteur de propriétés.

```xml
p.hits=full
```

Exemple :

`http://<host>:<port>/bin/querybuilder.json?p.hits=full&p.nodedepth=5&property=jcr%3atitle&property.value=Cycling%20Tuscany`

```xml
property=jcr:title
property.value=Cycling Tuscany
p.hits=full
p.nodedepth=5
```

## Plus de prédicats {#morepredicates}

Pour plus de prédicats, consultez la [page de référence des prédicats de Query Builder](query-builder-predicates.md).

Vous pouvez également vérifier le code Javadoc [pour les classes `PredicateEvaluator`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/eval/PredicateEvaluator.html). Ce JavaDoc contient la liste des propriétés que vous pouvez utiliser.

Le préfixe du nom de classe (par exemple, `similar` dans [`SimilarityPredicateEvaluator`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/eval/SimilarityPredicateEvaluator.html)) est la *propriété principale* de la classe. Cette propriété est également le nom du prédicat à utiliser dans la requête (en minuscules).

Pour ces propriétés principales, vous pouvez raccourcir la requête et utiliser `similar=/content/en` au lieu de la variante complète `similar.similar=/content/en`. La forme complète doit être utilisée pour toutes les propriétés non principales d’une classe.

## Exemple d’utilisation de l’API Query Builder  {#example-query-builder-api-usage}

```java
   String fulltextSearchTerm = "WKND";

    // create query description as hash map (simplest way, same as form post)
    Map<String, String> map = new HashMap<String, String>();

// create query description as hash map (simplest way, same as form post)
    map.put("path", "/content");
    map.put("type", "cq:Page");
    map.put("group.p.or", "true"); // combine this group with OR
    map.put("group.1_fulltext", fulltextSearchTerm);
    map.put("group.1_fulltext.relPath", "jcr:content");
    map.put("group.2_fulltext", fulltextSearchTerm);
    map.put("group.2_fulltext.relPath", "jcr:content/@cq:tags");

    // can be done in map or with Query methods
    map.put("p.offset", "0"); // same as query.setStart(0) below
    map.put("p.limit", "20"); // same as query.setHitsPerPage(20) below

    Query query = builder.createQuery(PredicateGroup.create(map), session);
    query.setStart(0);
    query.setHitsPerPage(20);

    SearchResult result = query.getResult();

    // paging metadata
    int hitsPerPage = result.getHits().size(); // 20 (set above) or lower
    long totalMatches = result.getTotalMatches();
    long offset = result.getStartIndex();
    long numberOfPages = totalMatches / 20;

    //Place the results in XML to return to client
    DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance();
    DocumentBuilder builder = factory.newDocumentBuilder();
    Document doc = builder.newDocument();

    //Start building the XML to pass back to the AEM client
    Element root = doc.createElement( "results" );
    doc.appendChild( root );

    // iterating over the results
    for (Hit hit : result.getHits()) {
       String path = hit.getPath();

      //Create a result element
      Element resultel = doc.createElement( "result" );
      root.appendChild( resultel );

      Element pathel = doc.createElement( "path" );
      pathel.appendChild( doc.createTextNode(path ) );
      resultel.appendChild( pathel );
    }
```

La même requête exécutée sur HTTP à l’aide du servlet Query Builder (JSON) :

`http://<host>:<port>/bin/querybuilder.json?path=/content&type=cq:Page&group.p.or=true&group.1_fulltext=WKND&group.1_fulltext.relPath=jcr:content&group.2_fulltext=WKND&group.2_fulltext.relPath=jcr:content/@cq:tags&p.offset=0&p.limit=20`

## Stockage et chargement de Requêtes {#storing-and-loading-queries}

Les requêtes peuvent être stockées dans le référentiel de manière à pouvoir les utiliser ultérieurement. La méthode `QueryBuilder` fournit la méthode `storeQuery` avec la signature suivante :

```java
void storeQuery(Query query, String path, boolean createFile, Session session) throws RepositoryException, IOException;
```

Lors de l&#39;utilisation de la méthode [`QueryBuilder#storeQuery`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/QueryBuilder.html#storequerycomdaycqsearchqueryjavalangstringbooleanjavaxjcrsession), le `Query` donné est stocké dans le référentiel sous la forme d&#39;un fichier ou d&#39;une propriété, conformément à la valeur de l&#39;argument `createFile`. L&#39;exemple suivant montre comment enregistrer un `Query` dans le chemin d&#39;accès `/mypath/getfiles` en tant que fichier :

```java
builder.storeQuery(query, "/mypath/getfiles", true, session);
```

Toutes les requêtes stockées précédemment peuvent être chargées à partir du référentiel en utilisant la méthode [`QueryBuilder#loadQuery`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/QueryBuilder.html#loadqueryjavalangstringjavaxjcrsession) :

```java
Query loadQuery(String path, Session session) throws RepositoryException, IOException
```

Par exemple, un `Query` stocké dans le chemin `/mypath/getfiles` peut être chargé par le fragment de code suivant :

```java
Query loadedQuery = builder.loadQuery("/mypath/getfiles", session);
```

## Tests et débogage {#testing-and-debugging}

Pour lire et déboguer les requêtes du créateur de Requêtes, vous pouvez utiliser la console de débogage du créateur de Requêtes à l’adresse

`http://<host>:<port>/libs/cq/search/content/querydebug.html`

ou la servlet JSON du créateur de Requêtes à

`http://<host>:<port>/bin/querybuilder.json?path=/tmp`

`path=/tmp` n’est qu’un exemple.

### Recommandations générales en matière de débogage {#general-debugging-recommendations}

### Obtenir XPath explicable via la journalisation {#obtain-explain-able-xpath-via-logging}

Expliquez **toutes** les requêtes pendant le cycle de développement par rapport au jeu d’index cible.

1. Autorisation des journaux DEBUG pour Query Builder afin d’obtenir la requête XPath explicable sous-jacente
   * Accédez à `https://<host>:<port>/system/console/slinglog`. Créez un nouveau journal pour `com.day.cq.search.impl.builder.QueryImpl` à **DEBUG**.
1. Une fois que DEBUG a été activé pour la classe ci-dessus, les journaux affichent la requête XPath générée par Query Builder.
1. Copiez la requête XPath de l&#39;entrée de journal de la requête du créateur de Requêtes associée, par exemple :
   * `com.day.cq.search.impl.builder.QueryImpl XPath query: /jcr:root/content//element(*, cq:Page)[(jcr:contains(jcr:content, "WKND") or jcr:contains(jcr:content/@cq:tags, "WKND"))]`
1. Collez la requête XPath dans la Requête d&#39;explication comme XPath pour obtenir le plan de requête.

### Obtenez XPath explicable via le débogueur du créateur de Requêtes {#obtain-explain-able-xpath-via-the-query-builder-debugger}

Utilisez le débogueur AEM Requête Builder pour générer une requête XPath explicable.

![Débogueur du créateur de requêtes](assets/query-builder-debugger.png)

1. Fourniture de la requête du créateur de Requêtes dans le débogueur du créateur de Requêtes
1. Exécutez la recherche.
1. Récupérez la requête XPath générée.
1. Collez la requête XPath dans la Requête d&#39;explication comme XPath pour obtenir le plan de requête

>[!NOTE]
>
>Les requêtes autres que Requête Builder (XPath, JCR-SQL2) peuvent être fournies directement à la Requête d&#39;explication.

## Débogage de requêtes à l’aide de la journalisation {#debugging-queries-with-logging}

>[!NOTE]
>
>La configuration des journaux est décrite dans le document [Logging](/help/implementing/developing/introduction/logging.md).

Sortie du journal (niveau INFO) de l’implémentation du créateur de requêtes lors de l’exécution de la requête décrite dans la section précédente [Test et débogage:](#testing-and-debugging)

```xml
com.day.cq.search.impl.builder.QueryImpl executing query (predicate tree):
null=group: limit=20, offset=0[
    {group=group: or=true[
        {1_fulltext=fulltext: fulltext=WKND, relPath=jcr:content}
        {2_fulltext=fulltext: fulltext=WKND, relPath=jcr:content/@cq:tags}
    ]}
    {path=path: path=/content}
    {type=type: type=cq:Page}
]
com.day.cq.search.impl.builder.QueryImpl XPath query: /jcr:root/content//element(*, cq:Page)[(jcr:contains(jcr:content, "WKND") or jcr:contains(jcr:content/@cq:tags, "WKND"))]
com.day.cq.search.impl.builder.QueryImpl no filtering predicates
com.day.cq.search.impl.builder.QueryImpl query execution took 69 ms
```

Dans le cas d’une requête qui utilise des évaluateurs de prédicats qui filtrent ou appliquent un ordre personnalisé par comparateur, cela est également indiqué dans la requête :

```xml
com.day.cq.search.impl.builder.QueryImpl executing query (predicate tree):
null=group: [
    {nodename=nodename: nodename=*.jar}
    {orderby=orderby: orderby=@jcr:content/jcr:lastModified}
    {type=type: type=nt:file}
]
com.day.cq.search.impl.builder.QueryImpl custom order by comparator: jcr:content/jcr:lastModified
com.day.cq.search.impl.builder.QueryImpl XPath query: //element(*, nt:file)
com.day.cq.search.impl.builder.QueryImpl filtering predicates: {nodename=nodename: nodename=*.jar}
com.day.cq.search.impl.builder.QueryImpl query execution took 272 ms
```

## Liens JavaDoc  {#javadoc-links}

| **Javadoc** | **Description** |
|---|---|
| [com.day.cq.search](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/package-summary.html) | Créateur de Requêtes de base et API de Requête |
| [com.day.cq.search.result](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/result/package-summary.html) | API de résultat |
| [com.day.cq.search.facets](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/facets/package-summary.html) | Facettes |
| [com.day.cq.search.facets.buckets](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/facets/buckets/package-summary.html) | Intervalles (contenus dans les facettes) |
| [com.day.cq.search.eval](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/eval/package-summary.html) | Évaluateurs d’attributs |
| [com.day.cq.search.facets.extracteurs](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/facets/extractors/package-summary.html) | Extracteurs de facettes (pour les évaluateurs) |
| [com.day.cq.search.writer](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/writer/package-summary.html) | JavaScript JSON Result Hit Writer pour servlet du créateur de Requêtes (`/bin/querybuilder.json`) |
