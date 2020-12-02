---
title: Création de balises dans des applications AEM
description: Travailler par programmation avec des balises ou étendre des balises dans une application AEM personnalisée
translation-type: tm+mt
source-git-commit: ce55065c3ae6a2350ed06811af76477df7c11291
workflow-type: tm+mt
source-wordcount: '769'
ht-degree: 40%

---


# Création de balises dans des applications AEM {#building-tagging-into-aem-applications}

Pour travailler par programmation avec des balises ou étendre des balises dans une application d’AEM personnalisée, ce document décrit l’utilisation de la variable

* [l’API de balisage ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/package-summary.html)

qui interagit avec le

* [framework de balisage](tagging-framework.md)

Pour plus d&#39;informations sur le balisage :

* Voir [Utilisation des balises](/help/sites-cloud/authoring/features/tags.md) pour plus d’informations sur le balisage du contenu en tant qu’auteur de contenu.
* Voir Administration des balises pour en savoir plus sur la création et la gestion des balises, ainsi que sur les balises de contenu qui ont été appliquées.

## Vue d’ensemble de l’API de balisage {#overview-of-the-tagging-api}

L’implémentation du [framework de balisage](tagging-framework.md) dans AEM permet la gestion des balises et du contenu des balises à l’aide de l’API JCR. `TagManager` s’assure que les balises entrées en tant que valeurs sur la propriété du tableau de  `cq:tags` chaînes ne sont pas dupliquées, supprime  `TagID`les balises pointant vers des balises non existantes et met à jour  `TagID`les balises déplacées ou fusionnées. `TagManager` utilise un écouteur d’observation JCR qui annule les modifications incorrectes. Les principales classes sont stockées dans le modules [com.day.cq.tagging](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/tagging/package-summary.html) :

* `JcrTagManagerFactory` - renvoie une mise en oeuvre JCR d&#39;un  `TagManager`. C’est l’implémentation de référence de l’API de balisage.
* `TagManager` - permet de résoudre et de créer des balises par chemins et noms.
* `Tag` - définit l’objet tag.

### Récupération d’un TagManager basé sur JCR {#getting-a-jcr-based-tagmanager}

Pour récupérer une instance `TagManager`, vous devez disposer d’un JCR `Session` et appeler `getTagManager(Session)` :

```java
@Reference
JcrTagManagerFactory jcrTagManagerFactory;

TagManager tagManager = jcrTagManagerFactory.getTagManager(session);
```

Dans le contexte standard de Sling, vous pouvez également effectuer une adaptation à un `TagManager` à partir du `ResourceResolver` : 

```java
TagManager tagManager = resourceResolver.adaptTo(TagManager.class);
```

### Récupération d’un objet Tag {#retrieving-a-tag-object}

Vous pouvez récupérer une balise `Tag` par l&#39;intermédiaire de `TagManager`, soit en résolvant une balise existante, soit en en en créant une nouvelle :

```java
Tag tag = tagManager.resolve("my/tag"); // for existing tags

Tag tag = tagManager.createTag("my/tag"); // for new tags
```

Pour l’implémentation basée sur JCR, qui mappe `Tags` sur JCR `Nodes`, vous pouvez directement utiliser le mécanisme `adaptTo` de Sling si vous disposez de la ressource (par exemple `/content/cq:tags/default/my/tag`) :

```java
Tag tag = resource.adaptTo(Tag.class);
```

Si une balise peut seulement être convertie *à partir d’* une ressource (et non d’un nœud), une balise peut être convertie *en*&#x200B;à la fois un nœud et une ressource :

```java
Node node = tag.adaptTo(Node.class);
Resource node = tag.adaptTo(Resource.class);
```

>[!NOTE]
>
>L&#39;adaptation directe de `Node` à `Tag` n&#39;est pas possible, car `Node` n&#39;implémente pas la méthode Sling `Adaptable.adaptTo(Class)`.

### Récupération et définition des balises {#getting-and-setting-tags}

```java
// Getting the tags of a Resource:
Tag[] tags = tagManager.getTags(resource);

// Setting tags to a Resource:
tagManager.setTags(resource, tags);
```

### Recherche de balises {#searching-for-tags}

```java
// Searching for the Resource objects that are tagged with the tag object:
Iterator<Resource> it = tag.find();

// Retrieving the usage count of the tag object:
long count = tag.getCount();

// Searching for the Resource objects that are tagged with the tagID String:
 RangeIterator<Resource> it = tagManager.find(tagID);
```

>[!NOTE]
>
>`RangeIterator` valide à utiliser :
>
>`com.day.cq.commons.RangeIterator`

### Suppression des balises {#deleting-tags}

```java
tagManager.deleteTag(tag);
```

### Réplication de balises {#replicating-tags}

Il est possible d’utiliser le service de réplication (`Replicator`) avec des balises dans la mesure où elles sont de type `nt:hierarchyNode` : 

```java
replicator.replicate(session, replicationActionType, tagPath);
```

## Le Tag Garbage Collector {#the-tag-garbage-collector}

Le récupérateur de balises est un service d’arrière-plan qui nettoie les balises qui sont masquées et inutilisées. Les balises masquées et inutilisées sont des balises inférieures à `/content/cq:tags` qui possèdent une propriété `cq:movedTo` et ne sont pas utilisées sur un noeud de contenu. Ils ont un décompte de zéro. Avec ce processus de suppression à l’arrière-plan, le nœud de contenu (c’est-à-dire la propriété `cq:tags`) n’a pas besoin d’être mis à jour lors du déplacement ou de la fusion. Les références de la propriété `cq:tags` sont automatiquement mises à jour lorsque la propriété `cq:tags` est mise à jour, par ex. via la boîte de dialogue des propriétés de la page.

Le Tag Garbage Collector s’exécute par défaut une fois par jour. Cette fréquence peut être configurée sur : 

`http://<host>:<port>/system/console/configMgr/com.day.cq.tagging.impl.TagGarbageCollector`

## Recherche de balises et listing des balises {#tag-search-and-tag-listing}

La recherche de balises et le listing des balises fonctionnent comme suit :

* La recherche de `TagID` recherche les balises pour lesquelles la propriété `cq:movedTo` est définie sur `TagID` et suit les `cq:movedTo` `TagID`s.
* La recherche du titre de la balise ne porte que sur les balises qui ne possèdent pas de propriété `cq:movedTo`.

## Balises dans différentes langues {#tags-in-different-languages}

Une balise `title` peut être définie dans différentes langues. Une propriété sensible à la langue est ensuite ajoutée au nœud de la balise. Cette propriété a le format `jcr:title.<locale>`, par ex. `jcr:title.fr` pour la traduction française. `<locale>` doit être une chaîne de paramètres régionaux ISO en minuscules et utiliser un trait de soulignement (`_`) au lieu d’un tiret/tiret (`-`), par exemple :  `de_ch`.

Par exemple, lorsque la balise **Animaux** est ajoutée à la page **Produits**, la valeur `stockphotography:animals` est ajoutée à la propriété `cq:tags` du noeud `/content/wknd/en/products/jcr:content`. La traduction est référencée à partir du nœud de balise.

L’API côté serveur a localisé des méthodes liées à `title` :

* [`com.day.cq.tagging.Tag`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/tagging/Tag.html)
   * `getLocalizedTitle(Locale locale)`
   * `getLocalizedTitlePaths()`
   * `getLocalizedTitles()`
   * `getTitle(Locale locale)`
   * `getTitlePath(Locale locale)`
* [`com.day.cq.tagging.TagManager`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/tagging/TagManager.html)
   * `canCreateTagByTitle(String tagTitlePath, Locale locale)`
   * `createTagByTitle(String tagTitlePath, Locale locale)`
   * `resolveByTitle(String tagTitlePath, Locale locale)`

En AEM, la langue peut être obtenue à partir de la langue de la page ou de la langue de l’utilisateur.

Pour le balisage, la localisation dépend du contexte, car la balise `titles` peut être affichée dans la langue de la page, dans la langue de l’utilisateur ou dans toute autre langue.

### Ajout d’une langue à la boîte de dialogue Modifier la balise {#adding-a-new-language-to-the-edit-tag-dialog}

La procédure suivante décrit comment ajouter une nouvelle langue (par exemple le finnois) à la boîte de dialogue **Modifier la balise** :

1. Dans **CRXDE**, modifiez la propriété à plusieurs valeurs `languages` du noeud `/content/cq:tags`.
1. Ajoutez `fi_fi`, qui représente le paramètre régional finlandais, et enregistrez les modifications.

Le finnois est désormais disponible dans la boîte de dialogue des balises des propriétés de la page et dans la boîte de dialogue **Modifier la balise** lors de la modification d’une balise dans la console **Balisage**.

>[!NOTE]
>
>La nouvelle langue doit faire partie de celles reconnues par AEM, c’est-à-dire qu’elle doit être disponible sous `/libs/wcm/core/resources/languages`.
