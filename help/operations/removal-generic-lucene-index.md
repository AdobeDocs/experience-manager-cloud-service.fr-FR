---
title: Suppression de l’index Lucene générique
description: Suppression de l’index Lucene générique
exl-id: fe0e00ac-f9c8-43cf-83c2-5a353f5eaeab
source-git-commit: bc7ef6567ad5baa4becd28a7e7d96bd6b579e1ad
workflow-type: tm+mt
source-wordcount: '1305'
ht-degree: 0%

---

# Suppression de l’index &#39;générique Lucene&#39;

Adobe a l’intention de supprimer l’index &quot;générique Lucene&quot; (`/oak:index/lucene-*`) depuis Adobe Experience Manager as a Cloud Service. Cet index est obsolète depuis AEM 6.5. Dans cette documentation, l’impact de cette décision est décrit, ainsi que des descriptions détaillées sur la manière d’examiner si une instance AEM est affectée. Enfin, il contient des moyens de modifier les requêtes afin qu’elles fonctionnent sans que cet index soit présent.

## Arrière-plan

Dans AEM, les requêtes &quot;fulltext&quot; sont les requêtes utilisant les fonctions suivantes :

* `jcr:contains()` dans JCR XPATH
* `CONTAINS` dans JCR-SQL2

Ces requêtes ne peuvent pas renvoyer de résultats sans utiliser d’index. Contrairement à une requête contenant uniquement des restrictions de chemin ou de propriété, une requête contenant une restriction de texte intégral pour laquelle aucun index n’est trouvé (et donc une traversée est effectuée) renvoie toujours 0 résultat.

Index &#39;générique Lucene&#39; (`/oak:index/lucene-*`) existe depuis AEM 6.0 / Oak 1.0 afin de fournir une recherche de texte intégral dans la plupart des hiérarchies de référentiel (certains chemins, tels que `/jcr:system` et `/var` ont toujours été exclus de cette fonctionnalité), mais cet index a été largement remplacé par des index sur des types de noeuds plus spécifiques (par exemple : `damAssetLucene-*` pour le type de noeud &quot;dam:Asset&quot;) qui prend en charge les recherches de texte intégral et de propriétés.

Dans AEM 6.5, l’index &quot;générique Lucene&quot; a été marqué comme obsolète (indiquant qu’il serait supprimé dans les versions ultérieures), et depuis lors, un AVERTISSEMENT a été consigné lorsque l’index a été utilisé :

```
org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'search term') and isdescendantnode(a, '/content/mysite') /* xpath: /jcr:root/content/mysite//*[jcr:contains(.,"search term")] */ fullText="search" "term", path=/content/mysite//*). Please change the query or the index definitions.
```

Dans les versions d&#39;AEM récentes, l&#39;index &quot;générique Lucene&quot; a été utilisé pour prendre en charge un très petit nombre de fonctionnalités. Ils sont en cours de retraitement afin d’utiliser d’autres index ou modifiés d’une autre manière pour supprimer la dépendance à cet index.
Par exemple, les requêtes de &quot;recherche de référence&quot; du formulaire ci-dessous doivent maintenant utiliser l’index à l’emplacement &#39;/oak:index/pathreference&#39; (qui indexe uniquement les valeurs de propriété de chaîne correspondant à une expression régulière qui recherche les chemins JCR). 

```
//*[jcr:contains(., '"/content/dam/mysite"')]
```

Afin de prendre en charge des volumes de données client plus importants, Adobe ne créera plus l’index &quot;générique Lucene&quot; sur de nouveaux environnements as a Cloud Service AEM et, par la suite, commencera à supprimer l’index des référentiels existants. Nous avons déjà ajusté les paramètres d’index (via les propriétés &#39;costPerEntry&#39; et &#39;costPerExecution&#39;) pour nous assurer que d’autres index (tels que `/oak:index/pathreference`) sont utilisés de préférence pour `/oak:index/lucene-*` dans la mesure du possible. 

Les applications client qui utilisent des requêtes qui dépendent toujours de cet index doivent être mises à jour immédiatement afin d’exploiter d’autres index existants (qui peuvent être personnalisés si nécessaire) ou de nouveaux index personnalisés doivent être ajoutés à l’application client. Vous trouverez des instructions complètes sur la gestion des index dans AEM as a Cloud Service à l’adresse [documentation d’indexation](/help/operations/indexing.md).

## Comment déterminer si votre application dépend de l’index générique Lucene ?

L’index &quot;lucene générique&quot; est actuellement utilisé comme &quot;secours&quot; si aucun autre index de texte intégral ne peut traiter une requête. Lorsque cet index obsolète est utilisé, un message comme celui-ci est consigné au niveau de l’avertissement :

```
org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') /* xpath: //*[jcr:contains(.,"test")] */ fullText="test", path=*). Please change the query or the index definitions.
```

Dans certains cas, Oak peut tenter d’utiliser un autre index de texte intégral (comme `/oak:index/pathreference`) pour prendre en charge la requête en texte intégral, mais si la chaîne de requête ne correspond pas à l’expression régulière sur la définition d’index, un message est consigné au niveau WARN et la requête ne renvoie probablement pas de résultats.

```
org.apache.jackrabbit.oak.query.QueryImpl Potentially improper use of index /oak:index/pathReference with queryFilterRegex (["']|^)/ to search for value "test"
```

Une fois l’index &quot;générique Lucene&quot; supprimé, un message comme illustré ci-dessous est consigné au niveau AVERTISSEMENT si une requête de texte intégral n’est pas en mesure de localiser une définition d’index appropriée :

```
org.apache.jackrabbit.oak.query.QueryImpl Fulltext query without index for filter Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') /* xpath: //*[jcr:contains(.,"test")] */ fullText="test", path=*); no results will be returned
```

Si l’un d’eux est consigné, vous devrez peut-être retravailler la requête pour utiliser un autre index de texte intégral ou fournir un nouvel index pour prendre en charge la requête. Vous trouverez ci-dessous des informations détaillées sur les types de dépendances que vous pouvez voir et sur la manière de les traiter.

## Dépendances potentielles sur l’index &quot;lucene générique&quot;

### Publication

#### Requêtes d’application personnalisées

La source de requêtes la plus courante utilisant l’index générique Lucene sur Publish sera les requêtes d’application personnalisées.

Dans les cas les plus simples, il peut s’agir de requêtes sans type de noeud spécifié (impliquant &#39;nt:base&#39;) ou nt:base spécifié explicitement, par exemple :

```
/jcr:root/content/mysite//*[jcr:contains(., 'search term')]
/jcr:root/content/mysite//element(*, nt:base)[jcr:contains(., 'search term')]
```

Action requise : Ces requêtes peuvent être modifiées pour utiliser un type de noeud approprié, par exemple pour renvoyer les résultats correspondant aux pages (ou n’importe lequel des &quot;agrégats&quot; sous le noeud cq:Page), la requête peut devenir :

```
/jcr:root/content/mysite//element(*, cq:Page)[jcr:contains(., 'search term')]
```

Dans d’autres cas, une requête peut spécifier un type de noeud, mais contenir une restriction de texte intégral qui ne peut pas être gérée par un autre index de texte intégral, tel que :

```
/jcr:root/content/dam//element(*, dam:Asset)[jcr:contains(jcr:content/metadata/@cq:tags, 'NewsTopics:cateogries/domestic'))]
```

Dans ce cas, la requête possède le type de noeud &quot;dam:Asset&quot;, mais contient une restriction de texte intégral sur la propriété relative `jcr:content/metadata/@cq:tags` .

Cette propriété n’est pas marquée comme &quot;analysé&quot; dans l’index damAssetLucene (l’index de texte intégral le plus souvent utilisé pour les requêtes sur le type de noeud &quot;dam:Asset&quot;). Par conséquent, cet index ne peut pas être utilisé pour cette requête.

Ainsi, la requête repose sur l’index &quot;texte intégral générique&quot; où toutes les propriétés incluses sont marquées comme analysées par la correspondance du caractère générique à l’adresse `/oak:index/lucene-2/indexRules/nt:base/properties/prop`.

Action client requise : marquer la variable `jcr:content/metadata/@cq:tags` comme &quot;analysé&quot; dans une version personnalisée de l’index damAssetLucene, cette requête sera traitée par cet index et aucun WARN ne sera consigné.

### Création 

Outre les requêtes dans les servlets d’application client, les composants OSGI et les scripts de rendu, il peut y avoir un certain nombre d’utilisations spécifiques à l’auteur de l’index &quot;lucene générique&quot;. 

#### Recherche de référence

Historiquement, l’index &quot;lucene générique&quot; a été utilisé pour prendre en charge la &quot;recherche de référence&quot; (recherche de contenu contenant des références à un autre chemin d’accès au contenu). Ces requêtes doivent déjà avoir été déplacées pour utiliser le nouvel index &#39;/oak:index/pathreference&#39;.
Action client requise : aucune action du client n’est requise.


#### Recherche du sélecteur de champ de chemin

AEM comprend un composant de boîte de dialogue personnalisé (type de ressource Sling &quot;granite/ui/components/coral/foundation/form/pathfield&quot;) qui fournit un navigateur (sélecteur) pour sélectionner un autre chemin AEM.  Le sélecteur de champ de chemin par défaut (utilisé lorsqu’aucune propriété personnalisée &#39;pickerSrc&#39; n’est définie dans la structure de contenu) affiche une barre de recherche dans la boîte de dialogue contextuelle.
Les types de noeud sur lesquels effectuer une recherche peuvent être spécifiés à l’aide de la propriété &#39;nodeTypes&#39;.

Actuellement, si aucune propriété &#39;nodeTypes&#39; n’est présente, la requête de recherche sous-jacente utilisera le type de noeud &#39;nt:base&#39; et sera donc susceptible d’utiliser l’index &#39;générique lucene&#39; (normalement en enregistrant les messages WARN affichés ci-dessous).

```
20.01.2022 18:56:06.412 *WARN* [127.0.0.1 [1642704966377] POST /mnt/overlay/granite/ui/content/coral/foundation/form/pathfield/picker.result.single.html HTTP/1.1] org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') and isdescendantnode(a, '/content') /* xpath: /jcr:root/content//element(*, nt:base)[(jcr:contains(., 'test'))] order by @jcr:score descending */ fullText="test", path=/content//*). Please change the query or the index definitions.
```

Avant la suppression de &quot;lucene générique&quot;, le composant pathfield est mis à jour afin que la zone de recherche soit masquée pour les composants qui utilisent le sélecteur par défaut, qui ne fournit pas de propriété &quot;nodeTypes&quot;.

| Sélecteur de champ de chemin avec recherche | Sélecteur de champ de chemin sans recherche |
|---|---|
| ![Sélecteur de champ de chemin avec recherche](assets/index-pathfield-picker-with-search.png) | ![Sélecteur de champ de chemin sans recherche](assets/index-pathfield-picker-without-search.png) |


Action client requise : Si aucune recherche n’est requise, aucune action du client n’est requise.

Si le client souhaite conserver la fonctionnalité de recherche dans le sélecteur de champ de chemin, une propriété &quot;nodeTypes&quot; doit être fournie répertoriant les types de noeud sur lesquels il souhaite effectuer des requêtes. Ils peuvent être spécifiés sous la forme d’une liste de types de noeuds séparés par des virgules dans une propriété String .


>[!NOTE]
>L’éditeur de modèle de fragment de contenu utilise des champs de chemin d’accès spécifiques avec le type de ressource Sling &quot;dam/cfm/models/editor/components/contentreference&quot;.
> * Actuellement, ces derniers exécutent des requêtes sans types de noeud spécifiés, ce qui entraîne l’enregistrement d’un avertissement en raison de l’utilisation de l’index &quot;lucene générique&quot;.
> * Les instances de ces composants utiliseront bientôt automatiquement par défaut les types de noeuds &quot;cq:Page&quot; et &quot;dam:Asset&quot; sans autre action du client.
> * La propriété &#39;nodeTypes&#39; peut être ajoutée pour remplacer ces types de noeuds par défaut. 





## Chronologie de la suppression de &quot;lucene générique&quot;

Adobe adoptera une approche en 2 phases pour supprimer l&#39;index &quot;générique lucene&quot;.

**Phase 1** (début prévu le 31 janvier 2022) : Ne créez plus &#39;/oak:index/lucene-*&#39; sur les nouveaux environnements as a Cloud Service AEM.

**Phase 2** (début prévu le 31 mars 2022) : Supprimez l’index &#39;/oak:index/lucene-*&#39; des nouveaux environnements as a Cloud Service AEM.

Adobe va surveiller les messages de logs mentionnés ci-dessus et va tenter de contacter les clients qui restent dépendants de l&#39;index générique Lucene.

À titre de limitation à court terme, si nécessaire, un Adobe ajoute directement des définitions d’index personnalisées aux systèmes clients afin d’éviter des problèmes de performance ou fonctionnels suite à la suppression de l’index &quot;lucene générique&quot;.

Dans ce cas, le client reçoit la définition d’index mise à jour et est invité à l’inclure dans les prochaines versions de son application via Cloud Manager.
