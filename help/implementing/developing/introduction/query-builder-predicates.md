---
title: Référence des prédicats de Query Builder
description: Référence de prédicat pour l’API Query Builder dans AEM as a Cloud Service.
exl-id: 77118ef7-4d29-470d-9c4b-20537a408940
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '2270'
ht-degree: 88%

---

# Référence des prédicats de Query Builder {#query-builder-predicate-reference}

## Général {#general}

### root {#root}

Groupe de prédicats racine. Il prend en charge toutes les fonctionnalités d’un groupe et permet de définir des paramètres de requête globaux.

Le nom « root » n’est jamais utilisé dans une requête ; il est implicite.

#### Propriétés {#properties-18}

* **`p.offset`** – Nombre indiquant le début de la page de résultats, c’est-à-dire le nombre d’éléments à ignorer.
* **`p.limit`** – Nombre indiquant la taille de la page.
* **`p.guessTotal`** - recommandé : évitez de calculer le total des résultats, ce qui peut s’avérer coûteux. Soit un nombre indiquant la limite de comptage maximale (par exemple, 1 000, un nombre qui offre aux utilisateurs suffisamment d’informations sur la taille approximative et des nombres exacts pour des résultats plus petits). Ou, `true` de compter uniquement jusqu’au minimum nécessaire `p.offset` + `p.limit`.
* **`p.excerpt`** – Si la valeur est définie sur `true`, l’extrait de texte complet est inclus dans les résultats.
* **`p.indexTag`** : si cette valeur est définie, une option de balise d’index est incluse dans la requête (voir [Balise d’index de l’option de requête](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#query-option-index-tag)).
* **`p.facetStrategy`** : si cette valeur est définie sur `oak`, Query Builder délègue l’extraction de facettes à Oak (voir [Facettes](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#facets)).
* **`p.hits`** – (Uniquement pour le servlet JSON) sélectionne la manière dont les accès sont écrits au format JSON, avec ces éléments standard (extensibles via le service ResultHitWriter).
   * **`simple`** – Éléments minimaux tels que `path`, `title`, `lastmodified`, `excerpt` (s’ils sont définis).
   * **`full`** - Rendu JSON Sling du nœud, avec `jcr:path` indiquant le chemin de l’accès. Par défaut, répertorie uniquement les propriétés directes du nœud, inclut une arborescence plus profonde avec `p.nodedepth=N`, 0 signifiant l’ensemble de la sous-arborescence infinie. Ajoutez des `p.acls=true` pour inclure les autorisations JCR de la session en cours sur l’élément de résultat donné (mappages : `create` = `add_node`, `modify` = `set_property`, `delete` = `remove`).
   * **`selective`** – Uniquement les propriétés spécifiées dans `p.properties`, qui est une liste séparée par des espaces (utilisez `+` dans les URL) des chemins relatifs. Si le chemin relatif a une profondeur de `>1`, ces propriétés sont représentées sous la forme d’objets enfants. La propriété spéciale `jcr:path` inclut le chemin d’accès de l’accès.

### groupe {#group}

Ce prédicat permet de créer des conditions imbriquées. Les groupes peuvent contenir des groupes imbriqués. Tout le contenu d’une requête Query Builder se trouve implicitement dans un groupe racine qui peut également posséder des paramètres `p.or` et `p.not`.

Voici un exemple de correspondance entre l’une ou l’autre des deux propriétés et une valeur :

```text
group.p.or=true
group.1_property=jcr:title
group.1_property.value=My Page
group.2_property=navTitle
group.2_property.value=My Page
```

D’un point de vue conceptuel, `(1_property` OU `2_property)`.

Voici un exemple pour les groupes imbriqués :

```text
fulltext=Management
group.p.or=true
group.1_group.path=/content/wknd/ch/de
group.1_group.type=cq:Page
group.2_group.path=/content/dam/wknd
group.2_group.type=dam:Asset
```

Le terme **Management** est recherché dans des pages sous `/content/wknd/ch/de` ou dans des ressources sous `/content/dam/wknd`.

D’un point de vue conceptuel, il s’agit de `fulltext AND ( (path AND type) OR (path AND type) )`. De telles jointures OU nécessitent de bons index pour des raisons de performances.

#### Propriétés {#properties-6}

* **`p.or`** – Si défini sur `true`, un seul prédicat du groupe doit correspondre. La valeur par défaut est `false`, ce qui signifie que tout doit correspondre
* **`p.not`** – Si défini sur `true`, le groupe est annulé (la valeur par défaut est `false`).
* **`<predicate>`** – ajoute des prédicats imbriqués
* **`N_<predicate>`** – ajoute plusieurs prédicats imbriqués simultanément, comme `1_property, 2_property, ...`

### orderby {#orderby}

Ce prédicat permet de trier les résultats. Si un classement basé sur plusieurs propriétés est requis, ce prédicat doit être ajouté plusieurs fois à l’aide du préfixe numérique, tel que `1_orderby=first`, `2_oderby=second`.

#### Propriétés {#properties-13}

* **`orderby`** - Nom de propriété JCR indiqué par un caractère @ initial, par exemple `@jcr:lastModified` ou `@jcr:content/jcr:title`, ou un autre prédicat dans la requête, par exemple `2_property`, sur la base duquel le tri doit être effectué.
* **`sort`** – Sens du tri, soit `desc` pour décroissant, soit `asc` pour croissant (valeur par défaut).
* **`case`** – Si cette valeur est définie sur `ignore`, le tri ne respecte pas la casse, ce qui signifie que `a` vient avant `B` ; si cette valeur est vide ou ignorée, le tri respecte la casse, ce qui signifie que `B` vient avant `a`

## Prédicats {#predicates}

### boolproperty {#boolproperty}

Ce prédicat met en correspondance des propriétés booléennes JCR. Accepte uniquement les valeurs `true` et `false`. Si la valeur est `false`, elle correspond si la propriété a la valeur `false`, ou si elle n’existe pas du tout. Ce prédicat s’avère utile pour rechercher des indicateurs booléens qui sont définis uniquement lorsqu’ils sont activés.

Le paramètre `operation` hérité n’a aucune signification.

Ce prédicat prend en charge l’extraction des facettes et fournit des intervalles pour chaque valeur `true` ou `false`, mais uniquement pour les propriétés existantes.

#### Propriétés {#properties}

* **`boolproperty`** - Chemin d’accès relatif à la propriété, par exemple `myFeatureEnabled` ou `jcr:content/myFeatureEnabled`
* **`value`** – Valeur dont la propriété doit être vérifiée : `true` ou `false`

### contentfragment {#contentfragment}

Ce prédicat limite le résultat aux fragments de contenu.

* Il ne prend pas en charge le filtrage.
* Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-1}

* **`contentfragment`** – Peut être utilisé avec n’importe quelle valeur pour rechercher des fragments de contenu.

### `dateComparison` {#datecomparison}

Ce prédicat compare entre elles deux propriétés de date JCR. Il peut tester si elles sont égales, inégales, supérieures ou supérieures ou égales.

Un prédicat de filtrage uniquement et qui ne peut pas utiliser d’index de recherche.

#### Propriétés {#properties-2}

* **`property1`** – Chemin d’accès à la première propriété date
* **`property2`** – Chemin d’accès à la deuxième propriété date
* **`operation`**
   * `=` pour la correspondance exacte (par défaut)
   * `!=` pour la comparaison des inégalités
   * `>` pour `property1` supérieur à `property2`
   * `>=` pour `property1` supérieur ou égal à `property2`

### daterange {#daterange}

Ce prédicat met en correspondance les propriétés de date JCR par rapport à un intervalle de date/heure. Il utilise le format ISO8601 pour les dates et heures (`YYYY-MM-DDTHH:mm:ss.SSSZ`) et autorise les représentations partielles, comme `YYYY-MM-DD`. Vous pouvez également fournir l’horodatage au format POSIX.

Vous pouvez rechercher tout ce qui se trouve entre deux horodatages, un élément plus récent ou plus ancien qu’une date donnée, et également choisir entre des intervalles inclusifs et ouverts.

Il prend en charge l’extraction des facettes et fournit des intervalles `today`, `this week`, `this month`, `last 3 months`, `this year`, `last year` et `earlier than last year`.

Il ne prend pas en charge le filtrage.

#### Propriétés {#properties-3}

* **`property`** - Chemin d’accès relatif à une propriété `DATE`, par exemple, `jcr:lastModified`
* **`lowerBound`** - Limite de date inférieure pour laquelle la propriété doit être vérifiée, par exemple pour `2014-10-01`
* **`lowerOperation`** – `>` (plus récent) ou `>=` (à cette date ou plus récent) ; applicable à `lowerBound`. La valeur par défaut est de `>`
* **`upperBound`** - Limite supérieure pour laquelle la propriété doit être vérifiée, par exemple, pour `2014-10-01T12:15:00`
* **`upperOperation`** – `<` (antérieur) ou `<=` (à cette date ou antérieur) ; applicable à `upperBound`. La valeur par défaut est de `<`
* **`timeZone`** – ID du fuseau horaire à utiliser lorsqu’il n’est pas indiqué sous la forme d’une chaîne de date ISO-8601. La valeur par défaut est le fuseau horaire par défaut du système.

### excludepaths {#excludepaths}

Ce prédicat exclut des nœuds du résultat lorsque leur chemin d’accès correspond à une expression régulière.

Un prédicat de filtrage uniquement et qui ne peut pas utiliser d’index de recherche.

Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-4}

* **`excludepaths`** – Expression régulière comparée à des chemins de résultat, en excluant les correspondances du résultat.

### fulltext {#fulltext}

Il recherche des termes dans l’index en texte intégral.

Il ne prend pas en charge le filtrage.

Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-5}

* **`fulltext`** – Termes de recherche en texte intégral
* **`relPath`** – Chemin d’accès relatif devant faire l’objet d’une recherche dans la propriété ou le sous-nœud. Cette propriété est facultative.

### hasPermission {#haspermission}

Ce prédicat limite le résultat aux éléments où la session en cours possède les [privilèges JCR](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges) spécifiés.

Un prédicat de filtrage uniquement et qui ne peut pas utiliser d’index de recherche. Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-7}

* **`hasPermission`** – Tous les privilèges JCR séparés par des virgules qui doivent être associés à la session d’utilisation en cours pour le nœud en question. Par exemple, `jcr:write`, `jcr:modifyAccessControl`.

### language {#language}

Ce prédicat identifie des pages AEM dans une langue spécifique. Il examine à la fois la propriété de langue de la page et le chemin d’accès à la page qui inclut souvent la langue ou les paramètres régionaux dans une structure de site de niveau supérieur.

Un prédicat de filtrage uniquement et qui ne peut pas utiliser d’index de recherche.

Il prend en charge l’extraction des facettes et fournit des intervalles pour chaque code de langue unique.

#### Propriétés {#properties-8}

* **`language`** - Code de langue ISO ; `de`, par exemple

### mainasset {#mainasset}

Ce prédicat vérifie si un nœud est une ressource DAM principale et non une sous-ressource. Il s’agit, en fait, de tout nœud qui ne se trouve pas à l’intérieur d’un nœud de sous-ressources. Il ne vérifie pas letype de nœud `dam:Asset`. Pour utiliser ce prédicat, définissez `mainasset=true` ou `mainasset=false`. Il n’y a pas d’autres propriétés.

Un prédicat de filtrage uniquement et qui ne peut pas utiliser d’index de recherche.

Il prend en charge l’extraction des facettes et fournit deux intervalles pour les ressources principales et secondaires.

#### Propriétés {#properties-9}

* **`mainasset`** – Booléen, `true` pour les ressources principales, `false` pour les sous-ressources

### memberOf {#memberof}

Ce prédicat recherche les éléments membres d’une [collection de ressources Sling](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/resource/collection/ResourceCollection.html) spécifique.

Un prédicat de filtrage uniquement et qui ne peut pas utiliser d’index de recherche.

Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-10}

* **`memberOf`** – Chemin d’accès à la collection de ressources Sling

### nodename {#nodename}

Ce prédicat met en correspondance des noms de nœud JCR.

Il prend en charge l’extraction des facettes et fournit des intervalles pour chaque nom de nœud unique (nom de fichier).

#### Propriétés {#properties-11}

* **`nodename`** – Modèle de nom de nœud qui autorise les caractères génériques : `*` = n’importe quel caractère, ou aucun, `?` = n’importe quel caractère, `[abc]` = uniquement les caractères entre crochets

### notexpired {#notexpired}

Ce prédicat met en correspondance des éléments en vérifiant si une propriété de date JCR est supérieure ou égale à l’heure actuelle du serveur. Vous pouvez l’utiliser pour vérifier une valeur `expiresAt` et limiter les résultats à celles qui n’ont pas encore atteint le délai d’expiration (`notexpired=true`) ou qui ont déjà atteint le délai d’expiration (`notexpired=false`).

Il ne prend pas en charge le filtrage.

Il prend en charge l’extraction de facettes de la même manière que le prédicat [`daterange`](#daterange).

#### Propriétés {#properties-12}

* **`notexpired`** – Booléen, `true` pour les propriétés qui n’ont pas encore atteint le délai d’expiration (date future ou égale à celle indiquée), `false` pour les propriétés qui ont atteint le délai d’expiration (date dans le passé) (obligatoire)
* **`property`** – Chemin d’accès relatif à la propriété `DATE` à vérifier (obligatoire)

### path {#path}

Ce prédicat effectue une recherche dans un chemin donné.

Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-14}

* **`path`** – Définit le modèle de chemin.
   * Selon la propriété `exact`, il existe une correspondance avec l’ensemble de la sous-arborescence (comme l’ajout de `//*` dans xpath, mais sans englober le chemin de base), ou seulement une correspondance avec le chemin exact, avec la possibilité d’inclure des caractères génériques (`*`).
      * La valeur par défaut est `true`.
&lt;!--- * Si la propriété `self` est définie, une recherche est appliquée à l’ensemble de la sous-arborescence, y compris le nœud de base.--->
* **`exact`** : si la propriété `exact` est définie sur `true`, le chemin d’accès exact doit correspondre, mais il peut contenir des caractères génériques simples (`*`), qui correspondent aux noms, mais pas `/` ; si elle est définie sur `false` (par défaut) tous les descendants sont inclus (facultatif).
* **`flat`** – Effectue uniquement des recherches dans les enfants directs (ce qui revient à ajouter `/*` dans xpath) (utilisé uniquement si `exact` n’est pas défini sur « true », facultatif).
* **`self`** : effectue une recherche dans la sous-arborescence, mais inclut le nœud de base indiqué comme chemin d’accès (aucun caractère générique).
   * *Remarque importante* : un problème a été identifié avec la propriété `self` dans l’implémentation actuelle de Query Builder et son utilisation dans les requêtes peut ne pas retourner des résultats de recherche corrects. Il n’est pas non plus possible de modifier l’implémentation actuelle de la propriété `self`, car cela pourrait interrompre l’exécution des applications existantes qui reposent dessus. En raison de cette fonctionnalité, la propriété `self` a été abandonnée et il est recommandé d’éviter de l’utiliser.

### property {#property}

Ce prédicat met en correspondance des propriétés JCR et leurs valeurs.

Il prend en charge l’extraction des facettes et fournit des intervalles pour chaque valeur de propriété unique dans les résultats.

#### Propriétés {#properties-15}

* **`property`** - Chemin d’accès relatif à la propriété, par exemple, `jcr:title`.
* **`value`** – Valeur dont la propriété doit être vérifiée ; suit le type de propriété JCR pour les conversions de chaînes.
* **`N_value`** – Utilisez `1_value`, `2_value`, etc. pour vérifier plusieurs valeurs (combinées avec `OR` par défaut, avec `AND` si `and=true`).
* **`and`** – défini sur `true` pour la combinaison de plusieurs valeurs (`N_value`) avec `AND`
* **`operation`**
   * `equals` pour une correspondance exacte (par défaut).
   * `unequals` pour la comparaison des inégalités.
   * `like` pour utiliser la fonction xpath `jcr:like` (facultatif).
   * `not` pour l’absence de correspondance (par exemple, `not(@prop)` dans xpath, le paramètre de valeur est ignoré).
   * `exists` pour une vérification d’existence.
      * `true` la propriété doit exister.
      * `false` est identique à `not` et est la valeur par défaut.
* **`depth`** – Nombre de niveaux de caractères génériques sous lesquels le chemin d’accès relatif/la propriété peut exister (par exemple, `property=size depth=2` vérifie `node/size`, `node/*/size` et `node/*/*/size`).

### rangeproperty {#rangeproperty}

Ce prédicat met en correspondance une propriété JCR par rapport à un intervalle. Il s’applique à des propriétés de type linéaire telles que `LONG`, `DOUBLE` et `DECIMAL`. Pour `DATE`, reportez-vous au prédicat [`daterange`](#daterange) qui présente une entrée de format de date optimisée.

Vous pouvez définir une limite inférieure, une limite supérieure ou les deux. L’opération (par exemple, inférieure, ou inférieure à ou égale à) peut également être spécifiée individuellement pour les limites inférieure et supérieure.

Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-16}

* **`property`** – Chemin d’accès relatif à la propriété
* **`lowerBound`** – Limite inférieure pour laquelle la propriété doit être vérifiée
* **`lowerOperation`** – `>` (par défaut) ou `>=`, s’applique à `lowerValue`
* **`upperBound`** – Limite supérieure pour laquelle la propriété doit être vérifiée
* **`upperOperation`** – `<` (par défaut) ou `<=`, s’applique à `lowerValue`
* **`decimal`** – `true` si la propriété vérifiée est de type Décimal

### relativedaterange {#relativedaterange}

Ce prédicat met en correspondance les propriétés `JCR DATE` par rapport à un intervalle de date/heure à l’aide de décalages temporels relatifs à l’heure actuelle du serveur. Vous pouvez spécifier `lowerBound` et `upperBound` en utilisant une valeur en millisecondes ou la syntaxe Bugzilla `1s 2m 3h 4d 5w 6M 7y` (une seconde, deux minutes, trois heures, quatre jours, cinq semaines, six mois, sept ans). Préfixe avec `-` pour indiquer un décalage négatif avant l’heure actuelle. Si vous spécifiez uniquement `lowerBound` ou `upperBound`, l’autre propriété est définie par défaut sur `0`, ce qui signifie l’heure actuelle.

Par exemple :

* `upperBound=1h` (et pas de `lowerBound`) sélectionne n’importe quel horaire dans l’heure suivante.
* `lowerBound=-1d` (et pas de `upperBound`) sélectionne n’importe quel horaire dans les dernières 24 heures.
* `lowerBound=-6M` et `upperBound=-3M` sélectionne n’importe quelle date au cours des 3 à 6 derniers mois
* `lowerBound=-1500` Et `upperBound=5500` sélectionne tout moment se trouvant entre 1 500 millisecondes et 5 500 millisecondes dans le futur.
* `lowerBound=1d` et `upperBound=2d` sélectionne tout moment postérieur au lendemain

Il ne tient pas compte des années bissextiles et tous les mois comptent 30 jours.

Il ne prend pas en charge le filtrage.

Il prend en charge l’extraction de facettes de la même manière que le prédicat [`daterange`](#daterange).

#### Propriétés {#properties-17}

* **`upperBound`** – Limite de date supérieure en millisecondes ou `1s 2m 3h 4d 5w 6M 7y` (une seconde, deux minutes, trois heures, quatre jours, cinq semaines, six mois, sept ans) par rapport à l’heure actuelle du serveur ; utilisez `-` pour un décalage négatif
* **`lowerBound`** – Limite de date inférieure en millisecondes ou `1s 2m 3h 4d 5w 6M 7y` (une seconde, deux minutes, trois heures, quatre jours, cinq semaines, six mois, sept ans) par rapport à l’heure actuelle du serveur ; utilisez `-` pour un décalage négatif

### savedquery {#savedquery}

Ce prédicat inclut tous les prédicats d’une requête Query Builder persistante dans la requête actuelle sous la forme d’un prédicat de sous-groupe.

Il n’exécute pas de requête supplémentaire, mais étend la requête actuelle.

Les requêtes peuvent être conservées par programmation à l’aide de `QueryBuilder#storeQuery()`. Ce format peut être soit une propriété `String` multiligne, soit un nœud `nt:file` contenant la requête en tant que fichier texte au format des propriétés Java™.

Il ne prend pas en charge l’extraction de facettes pour les prédicats de la requête enregistrée.

#### Propriétés {#properties-19}

* **`savedquery`** – Chemin d’accès à la requête enregistrée (propriété `String` ou nœud `nt:file`)

### similar {#similar}

Ce prédicat est une recherche de similarité effectuée à l’aide de `rep:similar()` en langage XPath JCR.

Il ne prend en charge ni le filtrage ni l’extraction des facettes.

#### Propriétés {#properties-20}

* **`similar`** – Chemin d’accès absolu au nœud pour lequel des nœuds similaires sont recherchés
* **`local`** – Un chemin relatif vers un nœud descendant ou `.` pour le nœud actif (facultatif, la valeur par défaut est `.`)

### tag {#tag}

Le prédicat recherche du contenu identifié avec une ou plusieurs balises, en spécifiant les chemins d’accès aux titres des balises.

Il prend en charge l’extraction des facettes et fournit des intervalles pour chaque balise unique, en utilisant leur chemin d’accès actuel au titre de la balise.

#### Propriétés {#properties-21}

* **`tag`** - Chemin d’accès au titre de la balise à rechercher ; par exemple, `properties:orientation/landscape`
* **`N_value`** – Utilisez `1_value`, `2_value`, ... pour vérifier plusieurs balises (combinées avec `OR` par défaut, avec `AND` si `and=true`)
* **`property`** – Propriété (ou chemin d’accès relatif à la propriété) à examiner (par défaut : `cq:tags`)

### tagid {#tagid}

Ce prédicat recherche du contenu identifié avec une ou plusieurs balises, en spécifiant les chemins d’accès aux titres des balises.

Il prend en charge l’extraction des facettes et fournit des intervalles pour chaque balise unique, en utilisant l’identifiant de balise actuel.

#### Propriétés {#properties-22}

* **`tagid`** - ID de balise à rechercher ; par exemple, `properties:orientation/landscape`
* **`N_value`** – Utilisez `1_value`, `2_value`, ... pour vérifier plusieurs identifiants de balises (combinées avec `OR` par défaut, avec `AND` si `and=true`)
* **`property`** – Propriété (ou chemin d’accès relatif à la propriété) à examiner (par défaut : `cq:tags`)

### tagsearch {#tagsearch}

Ce prédicat recherche du contenu identifié avec une ou plusieurs balises, en spécifiant des mots-clés. Il recherche d’abord les balises dont les titres contiennent ces mots-clés, puis limite les résultats aux seuls éléments balisés avec ces mots-clés.

Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#Properties-1}

* **`tagsearch`** – Mot-clé à rechercher dans les titres de balise
* **`property`** – Propriété (ou chemin relatif à la propriété) à prendre en compte (valeur par défaut `cq:tags`)
* **`lang`** – Pour rechercher uniquement dans un titre de balise localisé donné (par exemple, `de`)
* **`all`** – Valeur booléenne pour rechercher le texte intégral d’une balise, c’est-à-dire tous les titres, descriptions, etc. (est prioritaire sur `lang`)

### Type {#type}

Ce prédicat limite les résultats à un type de nœud JCR spécifique, aussi bien pour les types de nœud primaire que de. `mixin` Il trouve également des sous-types de ce type de nœud. Les index de recherche de référentiel doivent couvrir les types de nœuds pour une exécution efficace.

Ce prédicat prend en charge l’extraction des facettes et fournit des intervalles pour chaque type unique dans les résultats.

#### Propriétés {#Properties-2}

* **`type`** - Type de nœud ou nom de `mixin` à rechercher ; par exemple, `cq:Page`
