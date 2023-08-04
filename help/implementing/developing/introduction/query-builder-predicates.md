---
title: Référence des prédicats de Query Builder
description: Référence de prédicat pour l’API Query Builder dans AEM as a Cloud Service.
exl-id: 77118ef7-4d29-470d-9c4b-20537a408940
source-git-commit: 8c73805b6ed1b7a03c65b4d21a4252c1412a5742
workflow-type: tm+mt
source-wordcount: '2252'
ht-degree: 58%

---

# Référence des prédicats de Query Builder {#query-builder-predicate-reference}

## Général {#general}

### root {#root}

Groupe de prédicats racine. Il prend en charge toutes les fonctionnalités d’un groupe et permet de définir des paramètres de requête globaux.

Le nom &quot;root&quot; n’est jamais utilisé dans une requête ; il est implicite.

#### Propriétés {#properties-18}

* **`p.offset`** - nombre indiquant le début de la page de résultat, c’est-à-dire le nombre d’éléments à ignorer.
* **`p.limit`** - Nombre indiquant la taille de la page.
* **`p.guessTotal`** - recommandé : évitez de calculer le total du résultat, ce qui peut être coûteux. Soit un nombre indiquant le total maximal à compter (par exemple 1 000, un nombre qui donne aux utilisateurs suffisamment de commentaires sur la taille brute et les nombres exacts pour obtenir des résultats plus modestes). Ou, `true` pour ne compter que le minimum nécessaire `p.offset` + `p.limit`.
* **`p.excerpt`** - si la valeur est définie sur `true`, incluez un extrait de texte intégral dans le résultat.
* **`p.hits`** - (uniquement pour le servlet JSON) sélectionnez la manière dont les accès sont écrits en tant que JSON, avec ces accès standard (extensibles par le biais du service ResultHitWriter).
   * **`simple`** - Éléments minimaux tels que `path`, `title`, `lastmodified`, `excerpt` (s’ils sont définis).
   * **`full`** - rendu Sling JSON du noeud, avec `jcr:path` indiquant le chemin de l’accès. Par défaut, répertorie uniquement les propriétés directes du noeud, incluez une arborescence plus profonde avec la propriété `p.nodedepth=N`, avec 0 signifiant la sous-arborescence entière et infinie. Ajouter `p.acls=true` pour inclure les autorisations JCR de la session en cours sur l’élément de résultat donné (mappages : `create` = `add_node`, `modify` = `set_property`, `delete` = `remove`).
   * **`selective`** - uniquement les propriétés spécifiées dans `p.properties`, qui est séparé par un espace (utilisez `+` dans les URL) liste des chemins relatifs. Si le chemin relatif a une profondeur `>1`, ces propriétés sont représentées sous la forme d’objets enfants. Le spécial `jcr:path` inclut le chemin d’accès de l’accès.

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

D&#39;un point de vue conceptuel, `(1_property` OU `2_property)`.

Voici un exemple pour les groupes imbriqués :

```text
fulltext=Management
group.p.or=true
group.1_group.path=/content/wknd/ch/de
group.1_group.type=cq:Page
group.2_group.path=/content/dam/wknd
group.2_group.type=dam:Asset
```

Recherche le terme **Gestion** dans les pages de `/content/wknd/ch/de` ou dans les ressources de `/content/dam/wknd`.

D&#39;un point de vue conceptuel, `fulltext AND ( (path AND type) OR (path AND type) )`. De telles jointures OU nécessitent de bons index pour des raisons de performances.

#### Propriétés {#properties-6}

* **`p.or`** – Si défini sur `true`, un seul prédicat du groupe doit correspondre. La valeur par défaut est `false`, ce qui signifie que toutes les doivent correspondre
* **`p.not`** – Si défini sur `true`, le groupe est annulé (la valeur par défaut est `false`).
* **`<predicate>`** – ajoute des prédicats imbriqués
* **`N_<predicate>`** – ajoute plusieurs prédicats imbriqués simultanément, comme `1_property, 2_property, ...`

### orderby {#orderby}

Ce prédicat permet de trier les résultats. Si un classement par plusieurs propriétés est requis, ce prédicat doit être ajouté plusieurs fois à l’aide du préfixe numérique, tel que `1_orderby=first`, `2_oderby=second`.

#### Propriétés {#properties-13}

* **`orderby`** – Nom de propriété JCR indiqué par un caractère @ initial, par exemple `@jcr:lastModified` ou `@jcr:content/jcr:title`, ou un autre prédicat dans la requête, par exemple `2_property`, sur la base duquel le tri doit être effectué.
* **`sort`** – Sens du tri, soit `desc` pour décroissant, soit `asc` pour croissant (valeur par défaut).
* **`case`** - si la valeur est définie sur `ignore`, le tri n’est pas sensible à la casse, ce qui signifie `a` vient avant `B`; s’il est vide ou omis, le tri est sensible à la casse, ce qui signifie `B` vient avant `a`

## Prédicats {#predicates}

### boolproperty {#boolproperty}

Ce prédicat met en correspondance des propriétés booléennes JCR. Accepte uniquement les valeurs `true` et `false`. Si la valeur est `false`, il correspond si la propriété a la valeur . `false`ou s’il n’existe pas du tout. Ce prédicat est utile pour rechercher les indicateurs booléens qui ne sont définis que lorsqu’ils sont activés.

Le paramètre `operation` hérité n’a aucune signification.

Ce prédicat prend en charge l’extraction des facettes et fournit des intervalles pour chaque valeur `true` ou `false`, mais uniquement pour les propriétés existantes.

#### Propriétés {#properties}

* **`boolproperty`** – Chemin d’accès relatif à la propriété ; par exemple, `myFeatureEnabled` ou `jcr:content/myFeatureEnabled`
* **`value`** – Valeur dont la propriété doit être vérifiée : `true` ou `false`

### contentfragment {#contentfragment}

Ce prédicat limite le résultat aux fragments de contenu.

* Il ne prend pas en charge le filtrage.
* Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-1}

* **`contentfragment`** – Peut être utilisé avec n’importe quelle valeur pour rechercher des fragments de contenu.

### `dateComparison` {#datecomparison}

Ce prédicat compare entre elles deux propriétés de date JCR. Peuvent tester s’ils sont égaux, inégaux, supérieurs ou supérieurs ou égaux.

Prédicat de filtrage uniquement et ne peut pas utiliser d’index de recherche.

#### Propriétés {#properties-2}

* **`property1`** – Chemin d’accès à la première propriété date
* **`property2`** – Chemin d’accès à la deuxième propriété date
* **`operation`**
   * `=` pour la correspondance exacte (par défaut)
   * `!=` pour la comparaison des inégalités
   * `>` pour `property1` supérieur à `property2`
   * `>=` pour `property1` supérieur ou égal à `property2`

### daterange {#daterange}

Ce prédicat met en correspondance les propriétés de date JCR par rapport à un intervalle de date/heure. Utilise le format ISO8601 pour les dates et les heures (`YYYY-MM-DDTHH:mm:ss.SSSZ`) et permet également des représentations partielles, comme `YYYY-MM-DD`. Vous pouvez également fournir l’horodatage au format POSIX.

Vous pouvez rechercher tout ce qui se trouve entre deux horodatages, un élément plus récent ou plus ancien qu’une date donnée, et également choisir entre des intervalles inclusifs et ouverts.

Il prend en charge l’extraction des facettes et fournit des intervalles `today`, `this week`, `this month`, `last 3 months`, `this year`, `last year` et `earlier than last year`.

Il ne prend pas en charge le filtrage.

#### Propriétés {#properties-3}

* **`property`** – Chemin d’accès relatif à une propriété `DATE` ; par exemple, `jcr:lastModified`
* **`lowerBound`** – Limite de date inférieure pour laquelle la propriété doit être vérifiée ; par exemple, `2014-10-01`
* **`lowerOperation`** – `>` (plus récent) ou `>=` (à cette date ou plus récent) ; applicable à `lowerBound`. La valeur par défaut est de `>`
* **`upperBound`** – Limite supérieure pour laquelle la propriété doit être vérifiée ; par exemple, `2014-10-01T12:15:00`
* **`upperOperation`** – `<` (antérieur) ou `<=` (à cette date ou antérieur) ; applicable à `upperBound`. La valeur par défaut est de `<`
* **`timeZone`** – ID du fuseau horaire à utiliser lorsqu’il n’est pas indiqué sous la forme d’une chaîne de date ISO-8601. La valeur par défaut est le fuseau horaire par défaut du système.

### excludepaths {#excludepaths}

Ce prédicat exclut des nœuds du résultat lorsque leur chemin d’accès correspond à une expression régulière.

Prédicat de filtrage uniquement et ne peut pas utiliser d’index de recherche.

Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-4}

* **`excludepaths`** – Expression régulière comparée à des chemins de résultat, en excluant les correspondances du résultat.

### fulltext {#fulltext}

Recherche des termes dans l’index de texte intégral.

Il ne prend pas en charge le filtrage.

Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-5}

* **`fulltext`** : termes de recherche en texte intégral
* **`relPath`** – Chemin d’accès relatif devant faire l’objet d’une recherche dans la propriété ou le sous-nœud. Cette propriété est facultative.

### hasPermission {#haspermission}

Ce prédicat limite les résultats aux éléments dont la session en cours possède les [privilèges JCR](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges) spécifiés.

Prédicat de filtrage uniquement et ne peut pas utiliser d’index de recherche. Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-7}

* **`hasPermission`** : tous les privilèges JCR séparés par des virgules que la session utilisateur actuelle doit posséder pour le noeud en question. Par exemple, `jcr:write`, `jcr:modifyAccessControl`

### language {#language}

Ce prédicat identifie des pages AEM dans une langue spécifique. Il examine à la fois la propriété de langue de la page et le chemin d’accès à la page qui inclut souvent la langue ou les paramètres régionaux dans une structure de site de niveau supérieur.

Prédicat de filtrage uniquement et ne peut pas utiliser d’index de recherche.

Il prend en charge l’extraction des facettes et fournit des intervalles pour chaque code de langue unique.

#### Propriétés {#properties-8}

* **`language`** – Code de langue ISO ; par exemple, `de`

### mainasset {#mainasset}

Ce prédicat vérifie si un nœud est une ressource DAM principale et non une sous-ressource. Il s’agit essentiellement de tous les noeuds qui ne se trouvent pas dans un noeud de sous-ressources. Il ne vérifie pas la variable `dam:Asset` type de noeud. Pour utiliser ce prédicat, définissez `mainasset=true` ou `mainasset=false`. Il n’y a pas d’autres propriétés.

Prédicat de filtrage uniquement et ne peut pas utiliser d’index de recherche.

Il prend en charge l’extraction des facettes et fournit deux intervalles pour les ressources principales et secondaires.

#### Propriétés {#properties-9}

* **`mainasset`** – Booléen, `true` pour les ressources principales, `false` pour les sous-ressources

### memberOf {#memberof}

Ce prédicat recherche les éléments membres d’une [collection de ressources Sling](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/resource/collection/ResourceCollection.html) spécifique.

Prédicat de filtrage uniquement et ne peut pas utiliser d’index de recherche.

Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-10}

* **`memberOf`** – Chemin d’accès à la collection de ressources Sling

### nodename {#nodename}

Ce prédicat met en correspondance des noms de nœud JCR.

Il prend en charge l’extraction des facettes et fournit des intervalles pour chaque nom de nœud unique (nom de fichier).

#### Propriétés {#properties-11}

* **`nodename`** – Modèle de nom de nœud qui autorise les caractères génériques : `*` = n’importe quel caractère, ou aucun, `?` = n’importe quel caractère, `[abc]` = uniquement les caractères entre crochets

### notexpired {#notexpired}

Ce prédicat met en correspondance des éléments en vérifiant si une propriété de date JCR est supérieure ou égale à l’heure actuelle du serveur. Il peut être utilisé pour vérifier un `expiresAt` et limite les résultats aux seules valeurs qui n’ont pas encore expiré (`notexpired=true`) ou qui ont déjà expiré (`notexpired=false`).

Il ne prend pas en charge le filtrage.

Il prend en charge l’extraction de facettes de la même manière que le prédicat [`daterange`](#daterange).

#### Propriétés {#properties-12}

* **`notexpired`** – Booléen, `true` pour les propriétés qui n’ont pas encore atteint le délai d’expiration (date future ou égale à celle indiquée), `false` pour les propriétés qui ont atteint le délai d’expiration (date dans le passé) (obligatoire)
* **`property`** – Chemin d’accès relatif à la propriété `DATE` à vérifier (obligatoire)

### path {#path}

Ce prédicat effectue une recherche dans un chemin donné.

Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-14}

* **`path`** - Définit le modèle de chemin.
   * Selon le `exact` , soit la sous-arborescence entière correspond (comme l’ajout de `//*` dans xpath, mais notez qu’il n’inclut pas le chemin de base), ou qu’un seul chemin exact correspond, qui peut inclure des caractères génériques (`*`).
      * La valeur par défaut est `true`.
&lt;!— * Si la variable `self`est définie, la sous-arborescence entière, y compris le noeud de base, est recherchée.—>
* **`exact`** - if `exact` is `true`, le chemin exact doit correspondre, mais il peut contenir des caractères génériques simples (`*`), qui correspondent aux noms, mais pas aux `/`; s’il s’agit de `false` (par défaut) tous les descendants sont inclus (facultatif).
* **`flat`** - recherche uniquement les enfants directs (comme l’ajout de `/*` dans xpath (utilisé uniquement si) `exact` n’est pas vrai, facultatif).
* **`self`** – Effectue des recherches dans la sous-arborescence, mais inclut le nœud de base indiqué comme chemin d’accès (pas de caractères génériques).
   * *Remarque importante*: un problème a été identifié avec `self` dans l’implémentation actuelle de query builder et son utilisation dans les requêtes peut ne pas produire les résultats de recherche corrects. Modification de l’implémentation actuelle de `self` n’est pas non plus faisable, car elle peut interrompre les applications existantes qui s’y fient. En raison de cette fonctionnalité, `self` est désormais obsolète ; il est conseillé d’éviter de l’utiliser.

### property {#property}

Ce prédicat met en correspondance des propriétés JCR et leurs valeurs.

Il prend en charge l’extraction des facettes et fournit des intervalles pour chaque valeur de propriété unique dans les résultats.

#### Propriétés {#properties-15}

* **`property`** - chemin relatif à la propriété, par exemple `jcr:title`.
* **`value`** - valeur pour laquelle vérifier la propriété ; suit le type de propriété JCR en conversions de chaîne.
* **`N_value`** - use `1_value`, `2_value`, etc. pour vérifier plusieurs valeurs (combinées avec `OR` par défaut, avec `AND` if `and=true`).
* **`and`** – défini sur `true` pour la combinaison de plusieurs valeurs (`N_value`) avec `AND`
* **`operation`**
   * `equals` pour la correspondance exacte (par défaut).
   * `unequals` pour la comparaison des inégalités.
   * `like` pour utiliser la fonction xpath `jcr:like` (facultatif).
   * `not` pour aucune correspondance (par exemple, `not(@prop)` dans xpath, le paramètre value est ignoré).
   * `exists` pour une vérification d’existence.
      * `true` la propriété doit exister.
      * `false` est identique à `not` et est la valeur par défaut.
* **`depth`** : nombre de niveaux de caractères génériques sous lesquels le chemin de propriété/relatif peut exister (par exemple, `property=size depth=2` vérifications `node/size`, `node/*/size`, et `node/*/*/size`).

### rangeproperty {#rangeproperty}

Ce prédicat met en correspondance une propriété JCR par rapport à un intervalle. Il s’applique aux propriétés avec des types linéaires tels que `LONG`, `DOUBLE`, et `DECIMAL`. Pour `DATE`, voir [`daterange`](#daterange) prédicat avec une entrée de format de date optimisée.

Vous pouvez définir une limite inférieure, une limite supérieure ou les deux. L’opération (par exemple, inférieure ou inférieure ou égale à) peut également être spécifiée individuellement pour les limites inférieure et supérieure.

Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#properties-16}

* **`property`** – Chemin d’accès relatif à la propriété
* **`lowerBound`** – Limite inférieure pour laquelle la propriété doit être vérifiée
* **`lowerOperation`** – `>` (par défaut) ou `>=`, s’applique à `lowerValue`
* **`upperBound`** – Limite supérieure pour laquelle la propriété doit être vérifiée
* **`upperOperation`** – `<` (par défaut) ou `<=`, s’applique à `lowerValue`
* **`decimal`** – `true` si la propriété vérifiée est de type Décimal

### relativedaterange {#relativedaterange}

Ce prédicat met en correspondance les propriétés `JCR DATE` par rapport à un intervalle de date/heure à l’aide de décalages temporels relatifs à l’heure actuelle du serveur. Vous pouvez spécifier `lowerBound` et `upperBound` en utilisant une valeur en millisecondes ou la syntaxe Bugzilla `1s 2m 3h 4d 5w 6M 7y` (une seconde, deux minutes, trois heures, quatre jours, cinq semaines, six mois, sept ans). Préfixe avec `-` pour indiquer un décalage négatif avant l’heure actuelle. Si vous indiquez uniquement `lowerBound` ou `upperBound`, l’autre prend par défaut la valeur `0`, représentant l’heure actuelle.

Par exemple :

* `upperBound=1h` (et pas de `lowerBound`) sélectionne n’importe quel horaire dans l’heure suivante.
* `lowerBound=-1d` (et pas de `upperBound`) sélectionne n’importe quel horaire dans les dernières 24 heures.
* `lowerBound=-6M` et `upperBound=-3M` sélectionne n’importe quelle date au cours des 3 à 6 derniers mois
* `lowerBound=-1500` Et `upperBound=5500` sélectionne tout moment se trouvant entre 1 500 millisecondes et 5 500 millisecondes dans le futur.
* `lowerBound=1d` et `upperBound=2d` sélectionne tout moment postérieur au lendemain

Il ne faut pas tenir compte des années bissextiles et tous les mois sont 30 jours.

Il ne prend pas en charge le filtrage.

Il prend en charge l’extraction de facettes de la même manière que le prédicat [`daterange`](#daterange).

#### Propriétés {#properties-17}

* **`upperBound`** – Limite de date supérieure en millisecondes ou `1s 2m 3h 4d 5w 6M 7y` (une seconde, deux minutes, trois heures, quatre jours, cinq semaines, six mois, sept ans) par rapport à l’heure actuelle du serveur ; utilisez `-` pour un décalage négatif
* **`lowerBound`** – Limite de date inférieure en millisecondes ou `1s 2m 3h 4d 5w 6M 7y` (une seconde, deux minutes, trois heures, quatre jours, cinq semaines, six mois, sept ans) par rapport à l’heure actuelle du serveur ; utilisez `-` pour un décalage négatif

### savedquery {#savedquery}

Ce prédicat inclut tous les prédicats d’une requête Query Builder persistante dans la requête actuelle sous la forme d’un prédicat de sous-groupe.

Il n’exécute pas de requête supplémentaire, mais étend la requête actuelle.

Les requêtes peuvent être conservées par programmation à l’aide de `QueryBuilder#storeQuery()`. Le format peut être multiligne. `String` ou une propriété `nt:file` qui contient la requête sous la forme d’un fichier texte au format des propriétés Java™.

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

* **`tag`** – Chemin d’accès au titre de la balise à rechercher, par exemple `properties:orientation/landscape`
* **`N_value`** – Utilisez `1_value`, `2_value`, ... pour vérifier plusieurs balises (combinées avec `OR` par défaut, avec `AND` si `and=true`)
* **`property`** – Propriété (ou chemin d’accès relatif à la propriété) à examiner (par défaut : `cq:tags`)

### tagid {#tagid}

Ce prédicat recherche du contenu identifié avec une ou plusieurs balises, en spécifiant les chemins d’accès aux titres des balises.

Il prend en charge l’extraction des facettes et fournit des intervalles pour chaque balise unique, en utilisant l’identifiant de balise actuel.

#### Propriétés {#properties-22}

* **`tagid`** – ID de balise à rechercher ; par exemple `properties:orientation/landscape`
* **`N_value`** – Utilisez `1_value`, `2_value`, ... pour vérifier plusieurs identifiants de balises (combinées avec `OR` par défaut, avec `AND` si `and=true`)
* **`property`** – Propriété (ou chemin d’accès relatif à la propriété) à examiner (par défaut : `cq:tags`)

### tagsearch {#tagsearch}

Ce prédicat recherche du contenu identifié avec une ou plusieurs balises, en spécifiant des mots-clés. Elle recherche d’abord les balises contenant ces mots-clés dans leur titre, puis limite le résultat aux seuls éléments balisés avec ces mots-clés.

Il ne prend pas en charge l’extraction de facettes.

#### Propriétés {#Properties-1}

* **`tagsearch`** – Mot-clé à rechercher dans les titres de balise
* **`property`** – Propriété (ou chemin relatif à la propriété) à prendre en compte (valeur par défaut `cq:tags`)
* **`lang`** – Pour rechercher uniquement dans un titre de balise localisé donné (par exemple, `de`)
* **`all`** - valeur booléenne pour rechercher le texte intégral d’une balise, c’est-à-dire tous les titres, descriptions, etc. (a la priorité sur `lang`)

### type {#type}

Ce prédicat limite les résultats à un type de noeud JCR spécifique, à la fois à des types de noeuds Principaux ou `mixin` types. Il trouve également des sous-types de ce type de noeud. Les index de recherche de référentiel doivent couvrir les types de noeuds pour une exécution efficace.

Ce prédicat prend en charge l’extraction des facettes et fournit des intervalles pour chaque type unique dans les résultats.

#### Propriétés {#Properties-2}

* **`type`**`mixin` – Type de nœud ou nom de objet des recherches ; par exemple, `cq:Page`
