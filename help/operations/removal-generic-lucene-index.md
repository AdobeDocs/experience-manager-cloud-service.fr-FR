---
title: Suppression générique de l’index Lucene
description: Découvrez la suppression prévue des index Lucene génériques et comment vous pouvez être affecté.
exl-id: 3b966d4f-6897-406d-ad6e-cd5cda020076
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '1349'
ht-degree: 5%

---

# Suppression générique de l’index Lucene {#generic-lucene-index-removal}

Adobe a l’intention de supprimer l’index &quot;Lucene générique&quot; (`/oak:index/lucene-*`) depuis Adobe Experience Manager as a Cloud Service. Cet index est obsolète depuis AEM 6.5. Dans ce document, l’impact de cette décision est décrit, ainsi que des descriptions détaillées sur la manière d’examiner si une instance AEM est affectée. Il contient également des moyens de modifier les requêtes afin qu’elles continuent à fonctionner sans l’index Lucene générique.

## Contexte {#background}

Dans AEM, les requêtes en texte intégral sont celles qui utilisent les fonctions suivantes :

* `jcr:contains()` dans JCR XPATH
* `CONTAINS` dans JCR-SQL2

Ces requêtes ne peuvent pas renvoyer de résultats sans utiliser dʼindex. Contrairement à une requête contenant uniquement des restrictions de chemin ou de propriété, une requête contenant une restriction de texte intégral pour laquelle aucun index n’est trouvé (et donc une traversée est effectuée) ne renvoie toujours aucun résultat.

Index Lucene générique (`/oak:index/lucene-*`) existe depuis AEM 6.0 / Oak 1.0 afin de fournir une recherche de texte intégral dans la plus grande partie de la hiérarchie du référentiel, bien que certains chemins, tels que `/jcr:system` et `/var` ont toujours été exclues. Cependant, cet index a été largement remplacé par des index sur des types de noeuds plus spécifiques (par exemple, `damAssetLucene-*` pour le `dam:Asset` type de noeud), qui prend en charge les recherches de texte intégral et de propriétés.

Dans AEM 6.5, l’index Lucene générique a été marqué comme obsolète, indiquant qu’il serait supprimé dans les versions ultérieures. Depuis, un avertissement a été consigné lorsque l’index a été utilisé, comme illustré par le fragment de code de journal suivant :

```text
org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'search term') and isdescendantnode(a, '/content/mysite') /* xpath: /jcr:root/content/mysite//*[jcr:contains(.,"search term")] */ fullText="search" "term", path=/content/mysite//*). Please change the query or the index definitions.
```

Dans les versions d’AEM récentes, l’index générique Lucene a été utilisé pour prendre en charge un très petit nombre de fonctionnalités. Ces dernières subissent actuellement des refontes afin dʼutiliser d’autres index ou sont modifiées afin de supprimer leur dépendance à cet index.

Par exemple, les requêtes de recherche de référence, comme dans l’exemple suivant, doivent maintenant utiliser l’index à l’adresse `/oak:index/pathreference`, qui indexe uniquement `String` valeurs de propriété correspondant à une expression régulière qui recherche des chemins JCR.

```text
//*[jcr:contains(., '"/content/dam/mysite"')]
```

Afin de prendre en charge des volumes de données client plus importants, Adobe ne créera plus l’index Lucene générique sur de nouveaux environnements as a Cloud Service AEM. De plus, Adobe commencera à supprimer l’index des référentiels existants. [Voir la chronologie](#timeline) à la fin de ce document pour plus de détails.

Adobe a déjà ajusté les paramètres d&#39;index via le `costPerEntry` et `costPerExecution` pour vous assurer que d’autres index tels que `/oak:index/pathreference` sont préférées dans la mesure du possible.

Les applications client qui utilisent des requêtes qui dépendent toujours de cet index doivent être mises à jour immédiatement afin d’exploiter d’autres index existants, qui peuvent être personnalisés si nécessaire. Vous pouvez également ajouter de nouveaux index personnalisés à l’application cliente. Vous trouverez des instructions complètes sur la gestion des index dans AEM as a Cloud Service dans la section [documentation sur l’indexation.](/help/operations/indexing.md)

## Êtes-Vous Affectée ? {#are-you-affected}

L’index Lucene générique est actuellement utilisé comme secours si aucun autre index de texte intégral ne peut traiter une requête. En cas dʼutilisation de cet index obsolète, un message comme celui-ci sera enregistré au niveau WARN :

```text
org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') /* xpath: //*[jcr:contains(.,"test")] */ fullText="test", path=*). Please change the query or the index definitions.
```

Dans certains cas, Oak peut tenter d’utiliser un autre index de texte intégral (tel que `/oak:index/pathreference`) pour prendre en charge la requête de texte intégral, mais si la chaîne de requête ne correspond pas à l’expression régulière sur la définition d’index, un message est consigné au niveau WARN et la requête ne renvoie probablement pas de résultats.

```text
org.apache.jackrabbit.oak.query.QueryImpl Potentially improper use of index /oak:index/pathReference with queryFilterRegex (["']|^)/ to search for value "test"
```

Une fois l’index Lucene générique supprimé, un message comme illustré ci-dessous est consigné au niveau de l’avertissement si une requête de texte intégral n’est pas en mesure de localiser une définition d’index appropriée :

```text
org.apache.jackrabbit.oak.query.QueryImpl Fulltext query without index for filter Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') /* xpath: //*[jcr:contains(.,"test")] */ fullText="test", path=*); no results will be returned
```

>[!IMPORTANT]
>
>**Action du client requise**
>
> Si l’un des messages d’avertissement ci-dessus est enregistré, vous devrez peut-être retravailler la requête pour utiliser un autre index de texte intégral ou fournir un nouvel index pour prendre en charge la requête.
>
>Vous trouverez des informations détaillées sur les types de dépendances que vous pouvez voir et sur la manière de les traiter dans les sections suivantes.

## Dépendances potentielles des index Lucene génériques {#potential-dependencies}

Il existe un certain nombre de domaines dans lesquels vos applications et installations d’AEM peuvent dépendre d’index Lucene génériques, à la fois sur les instances de création et de publication.

### Instance de publication {#publish-instance}

#### Requêtes d’application personnalisées {#custom-application-queries}

La source la plus courante de requêtes utilisant l’index Lucene générique sur une instance de publication est les requêtes d’application personnalisées.

Dans les cas les plus simples, il peut s’agir de requêtes sans type de noeud spécifié, ce qui implique que `nt:base` ou `nt:base` spécifié explicitement, par exemple :

```text
/jcr:root/content/mysite//*[jcr:contains(., 'search term')]
/jcr:root/content/mysite//element(*, nt:base)[jcr:contains(., 'search term')]
```

>[!IMPORTANT]
>
>**Action du client requise**
>
>Les requêtes mentionnées ci-dessus doivent être modifiées afin d’utiliser un type de noeud approprié, comme décrit dans la section suivante.

Par exemple, les requêtes peuvent être modifiées pour renvoyer les résultats correspondant aux pages ou à l’un des agrégats situés sous la propriété `cq:Page node`. La requête pouvait ainsi devenir :

```text
/jcr:root/content/mysite//element(*, cq:Page)[jcr:contains(., 'search term')]
```

Dans d’autres cas, une requête peut spécifier un type de noeud, mais contenir une restriction de texte intégral qui ne peut pas être gérée par un autre index de texte intégral, tel que :

```text
/jcr:root/content/dam//element(*, dam:Asset)[jcr:contains(jcr:content/metadata/@cq:tags, 'NewsTopics:cateogries/domestic'))]
```

Dans ce cas, la requête contient la valeur `dam:Asset` type de noeud, mais contient une restriction de texte intégral sur le `jcr:content/metadata/@cq:tags` .

Cette propriété n’est pas marquée comme analysée dans la variable `damAssetLucene` index, qui est l’index de texte intégral le plus souvent utilisé pour les requêtes sur la variable `dam:Asset` type de noeud. Par conséquent, cet index ne peut pas être utilisé pour cette requête.

Ainsi, la requête repose sur l’index de texte intégral générique où toutes les propriétés incluses sont marquées comme analysées par la correspondance du caractère générique à l’adresse `/oak:index/lucene-2/indexRules/nt:base/properties/prop`.

>[!IMPORTANT]
>
>**Action du client requise**
>
>Marquage de la variable `jcr:content/metadata/@cq:tags` comme analysé dans une version personnalisée de `damAssetLucene` Cette requête sera traitée par cet index et aucun avertissement ne sera consigné.

### Instance d’auteur {#author-instance}

Outre les requêtes dans les servlets d’application client, les composants OSGi et les scripts de rendu, il peut y avoir plusieurs utilisations spécifiques à l’auteur de l’index Lucene générique.

#### Recherche de référence {#reference-search}

Historiquement, l’index Lucene générique a été utilisé pour prendre en charge la recherche de références ou la recherche de contenu qui contient des références à un autre chemin d’accès au contenu. Ces requêtes doivent déjà avoir été mises à jour pour utiliser la nouvelle `/oak:index/pathreference` index.

#### Recherche du sélecteur de champ de chemin {#picker-search}

AEM comprend un composant de boîte de dialogue personnalisé avec le type de ressource Sling `granite/ui/components/coral/foundation/form/pathfield`, qui fournit un navigateur/sélecteur pour sélectionner un autre chemin d’AEM. Sélecteur de champ de chemin par défaut, utilisé lorsqu’il n’est pas personnalisé `pickerSrc` est définie dans la structure de contenu et affiche une barre de recherche dans la boîte de dialogue contextuelle.

Les types de noeuds sur lesquels effectuer une recherche peuvent être spécifiés à l’aide de la propriété `nodeTypes` .

À l’heure actuelle, si non `nodeTypes` est présente, la requête de recherche sous-jacente utilisera la propriété `nt:base` type de noeud et est donc susceptible d’utiliser l’index Lucene générique, consignant généralement des messages WARN similaires à ce qui suit.

```text
20.01.2022 18:56:06.412 *WARN* [127.0.0.1 [1642704966377] POST /mnt/overlay/granite/ui/content/coral/foundation/form/pathfield/picker.result.single.html HTTP/1.1] org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') and isdescendantnode(a, '/content') /* xpath: /jcr:root/content//element(*, nt:base)[(jcr:contains(., 'test'))] order by @jcr:score descending */ fullText="test", path=/content//*). Please change the query or the index definitions.
```

Avant la suppression de l’index Lucene générique, la variable `pathfield` Le composant est mis à jour afin que la zone de recherche soit masquée pour les composants qui utilisent le sélecteur par défaut, qui ne fournissent pas de `nodeTypes` .

| Sélecteur de champ de chemin avec recherche | Sélecteur de champ de chemin sans recherche |
|---|---|
| ![Sélecteur de champ de chemin avec recherche](assets/index-pathfield-picker-with-search.png) | ![Sélecteur de champ de chemin sans recherche](assets/index-pathfield-picker-without-search.png) |

>[!IMPORTANT]
>
>**Action du client requise**
>
>Si le client souhaite conserver la fonctionnalité de recherche dans le sélecteur de champ de chemin d’accès, une `nodeTypes` doit être fournie en répertoriant les types de noeuds sur lesquels ils souhaitent effectuer des requêtes. Ils peuvent être spécifiés sous la forme d’une liste de types de noeuds séparés par des virgules dans une `String` . Si aucune recherche n’est requise, aucune action du client n’est requise.

>[!NOTE]
>
>L’éditeur de modèle de fragment de contenu utilise des champs de chemin spécialisés avec le type de ressource Sling. `dam/cfm/models/editor/components/contentreference`.
> * Actuellement, ces derniers exécutent des requêtes sans types de noeud spécifiés, ce qui entraîne l’enregistrement d’un AVERTISSEMENT en raison de l’utilisation de l’index Lucene générique.
> * Les instances de ces composants seront bientôt automatiquement utilisées par défaut pour `cq:Page` et `dam:Asset` types de noeuds sans autre action du client.
> * Le `nodeTypes` peut être ajoutée pour remplacer ces types de noeuds par défaut.


## Chronologie du retrait Lucene générique {#timeline}

Adobe adoptera une approche en deux phases pour supprimer l’index générique Lucene.

* **Phase 1** (prévu à partir du 31 janvier 2022) : Ne plus créer `/oak:index/lucene-*` sur les nouveaux environnements as a Cloud Service AEM.
* **Phase 2** (début prévu le 31 mars 2022) : Supprimer `/oak:index/lucene-*` à partir d’environnements AEM as a Cloud Service existants.

Adobe va surveiller les messages de log mentionnés ci-dessus et va tenter de contacter les clients qui restent dépendants de l&#39;index générique Lucene.

Dans le cadre d’une atténuation à court terme, Adobe ajoute directement des définitions d’index personnalisées aux systèmes clients afin d’éviter des problèmes de performance ou fonctionnels suite à la suppression de l’index Lucene générique, si nécessaire.

Le client recevra alors la définition dʼindex mise à jour et sera invité à lʼinclure dans les versions ultérieures de son application via Cloud Manager.
