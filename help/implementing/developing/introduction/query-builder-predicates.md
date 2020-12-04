---
title: Référence des prédicats de Query Builder
description: Référence d’attribut pour l’API du créateur de Requêtes.
translation-type: tm+mt
source-git-commit: 90b635cb31af910e08bdee7925cec0c7beb05318
workflow-type: tm+mt
source-wordcount: '2221'
ht-degree: 19%

---


# Référence des prédicats de Query Builder {#query-builder-predicate-reference}

## Général {#general}

### root {#root}

Il s&#39;agit du groupe de prédicats racine. Il prend en charge toutes les fonctionnalités d’un groupe et permet de définir des paramètres de requête globaux.

Le nom « root » n’est jamais utilisé dans une requête ; il est implicite.

#### Propriétés {#properties-18}

* **`p.offset`** -  Nombre indiquant le début de la page de résultats, c’est-à-dire le nombre d’éléments à ignorer
* **`p.limit`** - nombre indiquant le format de page
* **`p.guessTotal`** - recommandé : éviter de calculer le total des résultats qui peut être coûteux ; soit un nombre indiquant le total maximum à comptabiliser (par exemple 1 000, nombre qui donne aux utilisateurs suffisamment de commentaires sur la taille brute et les nombres exacts pour des résultats plus modestes), soit  `true` pour ne compter que jusqu’au minimum nécessaire  `p.offset` +  `p.limit`
* **`p.excerpt`** - s&#39;il est défini sur  `true`, inclure un extrait de texte intégral dans le résultat
* **`p.hits`** - (uniquement pour la servlet JSON) sélectionnez la manière dont les accès sont écrits en tant que JSON, avec les valeurs standard suivantes (extensible via le service ResultHitWriter) :
   * **`simple`** - éléments minimaux tels que  `path`,  `title`,  `lastmodified`,  `excerpt` (s&#39;ils sont définis)
   * **`full`** - rendu JSON sling du noeud, en  `jcr:path` indiquant le chemin de l’accès : par défaut, il suffit de liste les propriétés directes du noeud, d&#39;inclure une arborescence plus profonde avec  `p.nodedepth=N`0 signifiant la sous-arborescence entière et infinie ; ajouter  `p.acls=true` pour inclure les autorisations JCR de la session en cours sur l’élément de résultat donné (mappages :  `create` =  `add_node`,  `modify` =  `set_property`,  `delete` =  `remove`)
   * **`selective`** - seules les propriétés spécifiées dans  `p.properties`, qui est une liste de chemins relatifs séparée par des espaces (utilisée  `+` dans les URL) ; si le chemin relatif a une profondeur,  `>1` ils seront représentés sous forme d&#39;objets enfant ; la  `jcr:path` propriété spéciale inclut le chemin de l’accès.

### Groupe {#group}

Ce prédicat permet de créer des conditions imbriquées. Les groupes peuvent contenir des groupes imbriqués. Tout dans une requête du créateur de Requêtes se trouve implicitement dans un groupe racine, qui peut également avoir des paramètres `p.or` et `p.not`.

Voici un exemple de correspondance entre l’une ou l’autre des deux propriétés et une valeur :

```text
group.p.or=true
group.1_property=jcr:title
group.1_property.value=My Page
group.2_property=navTitle
group.2_property.value=My Page
```

Il s’agit de `(1_property` OU `2_property)` conceptuellement.

Voici un exemple pour les groupes imbriqués :

```text
fulltext=Management
group.p.or=true
group.1_group.path=/content/wknd/ch/de
group.1_group.type=cq:Page
group.2_group.path=/content/dam/wknd
group.2_group.type=dam:Asset
```

Cette méthode recherche le terme **Gestion** dans les pages de `/content/wknd/ch/de` ou dans les ressources de `/content/dam/wknd`.

Il s&#39;agit de `fulltext AND ( (path AND type) OR (path AND type) )` conceptuellement. Gardez à l’esprit que de telles jointures OU nécessitent de bons index pour des raisons de performances.

#### Propriétés {#properties-6}

* **`p.or`** - s&#39;il est défini sur  `true`, un seul prédicat du groupe doit correspondre. Par défaut, cette valeur est `false`, ce qui signifie que tous doivent correspondre à
* **`p.not`** - s&#39;il est défini sur  `true`, il annule le groupe (par défaut  `false`)
* **`<predicate>`** - ajoute des prédicats imbriqués
* **`N_<predicate>`** - ajoute plusieurs prédicats imbriqués simultanément, comme  `1_property, 2_property, ...`

### orderby {#orderby}

Ce prédicat permet de trier les résultats. Si l’ordre par plusieurs propriétés est requis, ce préfixe doit être ajouté plusieurs fois à l’aide du préfixe de nombre, tel que `1_orderby=first`, `2_oderby=second`.

#### Propriétés {#properties-13}

* **`orderby`** - soit le nom de la propriété JCR indiqué par un @ de début, par exemple  `@jcr:lastModified` ou  `@jcr:content/jcr:title`, soit un autre prédicat dans la requête, par exemple  `2_property`sur lequel effectuer le tri
* **`sort`** - ordre de tri, soit  `desc` pour décroissant, soit  `asc` pour croissant (par défaut)
* **`case`** - s&#39;il est défini sur  `ignore` rendra le tri insensible à la casse, le sens  `a` vient avant  `B`; s’il est vide ou omis, le tri est sensible à la casse, ce qui signifie  `B` qu’il est avant  `a`

## Prédicats {#predicates}

### boolproperty {#boolproperty}

Ce prédicat correspond à des propriétés booléennes JCR. Accepte uniquement les valeurs `true` et `false`. Dans le cas de `false`, il correspondra si la propriété a la valeur `false` ou si elle n’existe pas du tout. Cela peut s’avérer utile pour rechercher des indicateurs booléens qui sont définis uniquement lorsqu’ils sont activés.

Le paramètre `operation` hérité n&#39;a aucune signification.

Ce prédicat prend en charge l’extraction des facettes et fournit des intervalles pour chaque valeur `true` ou `false`, mais uniquement pour les propriétés existantes.

#### Propriétés {#properties}

* **`boolproperty`** - chemin relatif à la propriété, par exemple  `myFeatureEnabled` ou  `jcr:content/myFeatureEnabled`
* **`value`** - valeur pour laquelle vérifier la propriété,  `true` ou  `false`

### contentfragment {#contentfragment}

Ce prédicat limite le résultat aux fragments de contenu.

* Il ne prend pas en charge le filtrage.
* Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-1}

* **`contentfragment`** - Peut être utilisé avec n’importe quelle valeur pour rechercher des fragments de contenu.

### `dateComparison` {#datecomparison}

Ce prédicat compare deux propriétés de date JCR. Permet d’établir des comparaisons de type « est égale à », « est différente de », « est supérieure à » ou encore « est supérieure ou égale à ».

Il s’agit d’un prédicat de type filtrage seul qui ne peut pas exploiter d’index de recherche.

#### Propriétés {#properties-2}

* **`property1`** - chemin d’accès à la propriété de la première date
* **`property2`** - chemin d&#39;accès à la propriété de deuxième date
* **`operation`**
   * `=` pour la correspondance exacte (par défaut)
   * `!=` comparaison des inégalités
   * `>` pour  `property1` supérieur à  `property2`
   * `>=` pour  `property1` supérieur ou égal à  `property2`

### daterange {#daterange}

Ce prédicat correspond aux propriétés de date JCR par rapport à un intervalle de date/heure. Cette méthode utilise la norme ISO8601.
format pour les dates et les heures (`YYYY-MM-DDTHH:mm:ss.SSSZ`) et permet également des représentations partielles, comme `YYYY-MM-DD`. Vous pouvez également fournir l’horodatage sous forme d’heure POSIX.

Vous pouvez rechercher tout ce qui se trouve entre deux horodatages, un élément plus récent ou plus ancien qu’une date donnée, et également choisir entre des intervalles inclusifs et ouverts.

Il prend en charge l’extraction des facettes et fournit des intervalles `today`, `this week`, `this month`, `last 3 months`, `this year`, `last year` et `earlier than last year`.

Il ne prend pas en charge le filtrage.

#### Propriétés {#properties-3}

* **`property`** - chemin relatif à une  `DATE` propriété, par exemple  `jcr:lastModified`
* **`lowerBound`** - date inférieure liée pour la vérification de la propriété, par exemple  `2014-10-01`
* **`lowerOperation`** -  `>` (plus récent) ou  `>=` (plus récent), s&#39;applique au  `lowerBound`. La valeur par défaut est de `>`
* **`upperBound`** - limite supérieure pour laquelle vérifier la propriété, par exemple  `2014-10-01T12:15:00`
* **`upperOperation`** -  `<` (plus ancien) ou  `<=` (plus ancien), s&#39;applique au  `upperBound`. La valeur par défaut est de `<`
* **`timeZone`** - ID du fuseau horaire à utiliser lorsqu’il n’est pas indiqué sous la forme d’une chaîne de date ISO-8601. La valeur par défaut est le fuseau horaire par défaut du système.

### excludepaths  {#excludepaths}

Ce prédicat exclut les noeuds du résultat où leur chemin correspond à une expression régulière.

Il s’agit d’un prédicat de type filtrage seul qui ne peut pas exploiter d’index de recherche.

Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-4}

* **`excludepaths`** - Expression régulière comparée à des chemins de résultat, en excluant les correspondances du résultat.

### fulltext {#fulltext}

Ce prédicat recherche des termes dans l’index de texte intégral.

Il ne prend pas en charge le filtrage.

Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-5}

* **`fulltext`** - le ou les termes de recherche en texte intégral
* **`relPath`** - Chemin d’accès relatif devant faire l’objet d’une recherche dans la propriété ou le sous-nœud. Cette propriété est facultative.

### hasPermission {#haspermission}

Ce prédicat limite le résultat aux éléments pour lesquels la session en cours dispose des privilèges [JCR spécifiés.](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges)

Il s’agit d’un prédicat de type filtrage seul qui ne peut pas exploiter d’index de recherche. Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-7}

* **`hasPermission`** - les privilèges JCR séparés par des virgules que la session utilisateur actuelle doit avoir TOUS pour le noeud en question ; par exemple  `jcr:write`:  `jcr:modifyAccessControl`

### language {#language}

Ce prédicat recherche AEM pages dans une langue spécifique. Ce prédicat examine la propriété language de la page et le chemin d’accès de la page qui inclut souvent la langue ou le paramètre régional dans une structure de site de niveau supérieur.

Il s’agit d’un prédicat de type filtrage seul qui ne peut pas exploiter d’index de recherche.

Il prend en charge l’extraction des facettes et fournit des intervalles pour chaque code de langue unique.

#### Propriétés {#properties-8}

* **`language`** - code de langue ISO, par exemple  `de`

### mainasset {#mainasset}

Ce prédicat vérifie si un noeud est un actif principal DAM et non un sous-actif. Il s’agit essentiellement de chaque noeud qui ne se trouve pas dans un noeud de sous-ressources. Notez que ce prédicat ne recherche pas le type de nœud `dam:Asset`. Pour utiliser ce prédicat, définissez simplement `mainasset=true` ou `mainasset=false`. Il n&#39;y a pas d&#39;autres propriétés.

Il s’agit d’un prédicat de type filtrage seul qui ne peut pas exploiter d’index de recherche.

Il prend en charge l’extraction des facettes et fournit deux intervalles pour les ressources principales et secondaires.

#### Propriétés {#properties-9}

* **`mainasset`** - booléen,  `true` pour les ressources principales,  `false` pour les sous-ressources

### memberOf {#memberof}

Ce prédicat recherche les éléments qui sont membres d&#39;une [collecte de ressources sling](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/resource/collection/ResourceCollection.html) spécifique.

Il s’agit d’un prédicat de type filtrage seul qui ne peut pas exploiter d’index de recherche.

Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-10}

* **`memberOf`** - chemin de collecte des ressources Sling

### nodename {#nodename}

Ce prédicat correspond aux noms de noeud JCR.

Il prend en charge l’extraction des facettes et fournit des intervalles pour chaque nom de noeud unique (nom de fichier).

#### Propriétés {#properties-11}

* **`nodename`** - modèle de nom de noeud qui autorise les caractères génériques :  `*` = n’importe quel ou pas de caractère,  `?` = n’importe quel caractère,  `[abc]` = uniquement les caractères entre crochets

### notexpired {#notexpired}

Ce prédicat correspond aux éléments en vérifiant si une propriété de date JCR est supérieure ou égale à l’heure actuelle du serveur. Vous pouvez l’utiliser pour vérifier une valeur `expiresAt` et limiter les résultats à ceux qui n’ont pas encore expiré (`notexpired=true`) ou qui ont déjà expiré (`notexpired=false`).

Il ne prend pas en charge le filtrage.

Il prend en charge l’extraction des facettes de la même manière que le prédicat [`daterange`](#daterange).

#### Propriétés {#properties-12}

* **`notexpired`** - booléen,  `true` pour non encore expiré (date ultérieure ou égale),  `false` pour expirée (date antérieure) (obligatoire)
* **`property`** - chemin relatif à la  `DATE` propriété à vérifier (obligatoire)

### path {#path}

Ce prédicat recherche dans un chemin donné.

Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-14}

* **`path`** - Ceci définit le modèle de chemin.
   * Selon la propriété `exact`, soit la sous-arborescence entière correspond (comme l&#39;ajout de `//*` dans xpath, mais notez que cela n&#39;inclut pas le chemin de base), soit qu&#39;un chemin exact correspond, qui peut inclure des caractères génériques (`*`).
      * La valeur par défaut est `true`
   * Si la propriété `self`est définie, la sous-arborescence entière, y compris le noeud de base, est recherchée.
* **`exact`** - si  `exact` est  `true`, le chemin exact doit correspondre, mais il peut contenir de simples caractères génériques (`*`), des noms de correspondance, mais pas  `/`; s’il s’agit  `false` (valeur par défaut), tous les descendants sont inclus (facultatif).
* **`flat`** - recherche uniquement les enfants directs (comme l’ajout  `/*` dans xpath) (utilisé uniquement si  `exact` la valeur est fausse, facultatif)
* **`self`** - recherche la sous-arborescence mais inclut le noeud de base indiqué comme chemin d’accès (sans caractère générique).

### property {#property}

Ce prédicat correspond aux propriétés JCR et à leurs valeurs.

Il prend en charge l’extraction des facettes et fournit des intervalles pour chaque valeur de propriété unique dans les résultats.

#### Propriétés {#properties-15}

* **`property`** - chemin relatif à la propriété, par exemple  `jcr:title`
* **`value`** - valeur à vérifier pour la propriété ; suit le type de propriété JCR en conversions de chaînes
* **`N_value`** - utilisez  `1_value`,  `2_value`, ... pour rechercher plusieurs valeurs (combinées avec  `OR` par défaut, avec  `AND` si  `and=true`)
* **`and`** - défini sur  `true` pour la combinaison de plusieurs valeurs (`N_value`avec  `AND`
* **`operation`**
   * `equals` pour la correspondance exacte (par défaut)
   * `unequals` comparaison des inégalités
   * `like` pour utiliser la fonction  `jcr:like` xpath (facultatif)
   * `not` pour aucune correspondance (par exemple,  `not(@prop)` dans xpath, le paramètre value sera ignoré)
   * `exists` vérification de l&#39;existence
      * `true` la propriété doit exister
      * `false` est identique à  `not` et est la valeur par défaut
* **`depth`** - nombre de niveaux de caractères génériques sous lesquels la propriété/le chemin relatif peut exister (par exemple,  `property=size depth=2` vérifiera  `node/size`et  `node/*/size`  `node/*/*/size`)

### rangeproperty {#rangeproperty}

Ce prédicat correspond à une propriété JCR par rapport à un intervalle. Cela s’applique aux propriétés de types linéaires tels que `LONG`, `DOUBLE` et `DECIMAL`. Pour `DATE`[`daterange`](#daterange), reportez-vous au prédicat qui présente une entrée de format de date optimisée.

Vous pouvez définir une limite inférieure, une limite supérieure ou les deux. L&#39;opération (par exemple inférieure ou inférieure à ou égale à) peut également être spécifiée pour les limites inférieure et supérieure individuellement.

Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-16}

* **`property`** - chemin relatif à la propriété
* **`lowerBound`** - limite inférieure pour la propriété de contrôle
* **`lowerOperation`** -  `>` (valeur par défaut) ou  `>=`, s’applique à la variable  `lowerValue`
* **`upperBound`** - limite supérieure pour vérifier la propriété
* **`upperOperation`** -  `<` (valeur par défaut) ou  `<=`, s’applique à la variable  `lowerValue`
* **`decimal`** -  `true` si la propriété cochée est de type Décimal

### relativedaterange {#relativedaterange}

Ce prédicat correspond aux propriétés `JCR DATE` par rapport à un intervalle de date/heure en utilisant des décalages temporels par rapport à l’heure actuelle du serveur. Vous pouvez spécifier `lowerBound` et `upperBound` en utilisant soit une valeur de milliseconde, soit la syntaxe de bugzilla `1s 2m 3h 4d 5w 6M 7y` (une seconde, deux minutes, trois heures, quatre jours, cinq semaines, six mois, sept ans). Ajoutez un préfixe `-` pour indiquer un décalage négatif avant l’heure actuelle. Si vous spécifiez uniquement `lowerBound` ou `upperBound`, l’autre valeur par défaut est `0`, ce qui représente l’heure actuelle.

Par exemple :

* `upperBound=1h` (et non  `lowerBound`) sélectionne n’importe quoi dans l’heure suivante.
* `lowerBound=-1d` (et non  `upperBound`) sélectionne n’importe quoi au cours des dernières 24 heures.
* `lowerBound=-6M` et  `upperBound=-3M` sélectionne tout ce qui se trouve au cours des 3 à 6 derniers mois
* `lowerBound=-1500` et  `upperBound=5500` sélectionne tout ce qui a entre 1 500 millisecondes et 5 500 millisecondes dans le futur.
* `lowerBound=1d` et  `upperBound=2d` sélectionne tout ce qui suit le lendemain

Notez que ce prédicat ne tient pas compte des années bissextiles et que tous les mois comptent 30 jours.

Il ne prend pas en charge le filtrage.

Il prend en charge l’extraction des facettes de la même manière que le prédicat [`daterange`](#daterange).

#### Propriétés {#properties-17}

* **`upperBound`** - date supérieure liée en millisecondes ou  `1s 2m 3h 4d 5w 6M 7y` (une seconde, deux minutes, trois heures, quatre jours, cinq semaines, six mois, sept ans) par rapport à l&#39;heure actuelle du serveur, à utiliser  `-` pour un décalage négatif
* **`lowerBound`** - date inférieure liée en millisecondes ou  `1s 2m 3h 4d 5w 6M 7y` (une seconde, deux minutes, trois heures, quatre jours, cinq semaines, six mois, sept ans) par rapport à l&#39;heure actuelle du serveur, à utiliser  `-` pour un décalage négatif

### savedquery {#savedquery}

Ce prédicat inclut tous les prédicats d&#39;une requête persistante du créateur de Requêtes dans la requête active en tant que prédicat de sous-groupe.

Notez que ce prédicat n’exécute pas une requête supplémentaire, mais étend la requête en cours.

Les requêtes peuvent être conservées par programmation à l&#39;aide de `QueryBuilder#storeQuery()`. Le format peut être soit une propriété `String` multiligne, soit un noeud `nt:file` contenant la requête sous la forme d’un fichier texte au format de propriétés Java.

Il ne prend pas en charge l’extraction des facettes pour les prédicats de la requête enregistrée.

#### Propriétés {#properties-19}

* **`savedquery`** - chemin d&#39;accès à la requête enregistrée (`String` propriété ou  `nt:file` noeud)

### similar {#similar}

Ce prédicat est une recherche de similarité utilisant le XPath JCR `rep:similar()` de JCR.

Il ne prend pas en charge le filtrage et ne prend pas en charge l’extraction des facettes.

#### Propriétés {#properties-20}

* **`similar`** - Chemin d’accès absolu au nœud pour lequel des nœuds similaires sont recherchés
* **`local`** - un chemin relatif vers un noeud descendant ou  `.` pour le noeud actif (facultatif, la valeur par défaut est  `.`)

### tag {#tag}

Ce prédicat recherche le contenu balisé avec une ou plusieurs balises, en spécifiant les chemins d’accès au titre de la balise.

Il prend en charge l’extraction des facettes et fournit des intervalles pour chaque balise unique, en utilisant leur chemin d’accès actuel au titre de balise.

#### Propriétés {#properties-21}

* **`tag`** - chemin d’accès au titre de la balise à rechercher, par exemple  `properties:orientation/landscape`
* **`N_value`** - utilisez  `1_value`,  `2_value`, ... pour rechercher plusieurs balises (combinées avec  `OR` par défaut, avec  `AND` si  `and=true`)
* **`property`** - propriété (ou chemin relatif à la propriété) à examiner (par défaut  `cq:tags`)

### tagid {#tagid}

Ce prédicat recherche le contenu balisé avec une ou plusieurs balises, en spécifiant les ID de balise.

Il prend en charge l’extraction des facettes et fournit des intervalles pour chaque balise unique, à l’aide de leur identifiant de balise actuel.

#### Propriétés {#properties-22}

* **`tagid`** - ID de balise à rechercher, par exemple  `properties:orientation/landscape`
* **`N_value`** - utilisez  `1_value`,  `2_value`, ... pour rechercher plusieurs ID de balise (combinés  `OR` par défaut, avec  `AND` si  `and=true`)
* **`property`** - propriété (ou chemin relatif à la propriété) à examiner (par défaut  `cq:tags`)

### tagsearch {#tagsearch}

Ce prédicat recherche le contenu balisé avec une ou plusieurs balises, en spécifiant des mots-clés. Cela va d&#39;abord rechercher des balises contenant ces mots-clés dans leurs titres, puis limiter le résultat aux seuls éléments balisés avec ces mots-clés.

Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#Properties-1}

* **`tagsearch`** - Mot-clé à rechercher dans les titres de nœud
* **`property`** - propriété (ou chemin relatif à la propriété) à prendre en compte (valeur par défaut  `cq:tags`)
* **`lang`** - pour effectuer une recherche dans un certain titre de balise localisé uniquement (par ex.  `de`)
* **`all`** - valeur booléenne permettant de rechercher tout le texte intégral de la balise, c&#39;est-à-dire tous les titres, la description, etc. (est prioritaire sur `lang`)

### type {#type}

Ce prédicat limite les résultats à un type de noeud JCR spécifique, à la fois des types de noeud Principaux ou des types de mixin. Vous trouverez également des sous-types de ce type de noeud. Pour une exécution efficace, notez que les index de recherche de référentiel doivent couvrir les types de nœud.

Il prend en charge l’extraction des facettes et fournit des intervalles pour chaque type unique dans les résultats.

#### Propriétés {#Properties-2}

* **`type`** - type de noeud ou nom de mixage à rechercher, par exemple  `cq:Page`
