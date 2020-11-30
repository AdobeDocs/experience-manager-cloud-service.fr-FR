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

* Voir [Utilisation des balises](/help/sites-cloud/authoring/features/tags.md) pour en savoir plus sur le balisage du contenu en tant qu’auteur de contenu.
* Voir Administration des balises pour en savoir plus sur la création et la gestion des balises, ainsi que sur les balises de contenu qui ont été appliquées.

## Vue d’ensemble de l’API de balisage {#overview-of-the-tagging-api}

L’implémentation du [framework de balisage](tagging-framework.md) dans AEM permet la gestion des balises et du contenu des balises à l’aide de l’API JCR. `TagManager` s’assure que les balises entrées en tant que valeurs sur la propriété du tableau de `cq:tags` chaînes ne sont pas dupliquées, supprime `TagID`les balises pointant vers des balises non existantes et met à jour `TagID`les balises déplacées ou fusionnées. `TagManager` utilise un écouteur d’observation JCR qui annule les modifications incorrectes. Les principales classes sont stockées dans le modules [com.day.cq.tagging](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/tagging/package-summary.html) :

* `JcrTagManagerFactory` - renvoie une mise en oeuvre JCR d&#39;un `TagManager`. C’est l’implémentation de référence de l’API de balisage.
* `TagManager` - permet de résoudre et de créer des balises par chemins et noms.
* `Tag` - définit l’objet tag.

### Récupération d’un TagManager basé sur JCR {#getting-a-jcr-based-tagmanager}

To retrieve a `TagManager` instance, you need to have a JCR `Session` and to call `getTagManager(Session)`:

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

A `Tag` can be retrieved through the `TagManager`, by either resolving an existing tag or creating a new one:

```java
Tag tag = tagManager.resolve("my/tag"); // for existing tags

Tag tag = tagManager.createTag("my/tag"); // for new tags
```

For the JCR-based implementation, which maps `Tags` onto JCR `Nodes`, you can directly use Sling&#39;s `adaptTo` mechanism if you have the resource (e.g. such as `/content/cq:tags/default/my/tag`):

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
>Directly adapting from `Node` to `Tag` is not possible, because `Node` does not implement the Sling `Adaptable.adaptTo(Class)` method.

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

Le récupérateur de balises est un service d’arrière-plan qui nettoie les balises qui sont masquées et inutilisées. Les balises masquées et inutilisées sont des balises ci-dessous `/content/cq:tags` qui possèdent une `cq:movedTo` propriété et ne sont pas utilisées sur un noeud de contenu. Ils ont un décompte de zéro. Avec ce processus de suppression à l’arrière-plan, le nœud de contenu (c’est-à-dire la propriété `cq:tags`) n’a pas besoin d’être mis à jour lors du déplacement ou de la fusion. Les références de la propriété `cq:tags` sont automatiquement mises à jour lorsque la propriété `cq:tags` est mise à jour, par ex. via la boîte de dialogue des propriétés de la page.

Le Tag Garbage Collector s’exécute par défaut une fois par jour. Cette fréquence peut être configurée sur : 

`http://<host>:<port>/system/console/configMgr/com.day.cq.tagging.impl.TagGarbageCollector`

## Recherche de balises et listing des balises {#tag-search-and-tag-listing}

La recherche de balises et le listing des balises fonctionnent comme suit :

* The search for `TagID` searches for the tags that have the property `cq:movedTo` set to `TagID` and follows through the `cq:movedTo` `TagID`s.
* The search for tag title only searches the tags that do not have a `cq:movedTo` property.

## Balises dans différentes langues {#tags-in-different-languages}

Une balise `title` peut être définie dans différentes langues. Une propriété sensible à la langue est ensuite ajoutée au nœud de la balise. Cette propriété a le format `jcr:title.<locale>`, par exemple `jcr:title.fr` pour la traduction française. `<locale>` doit être une chaîne de paramètres régionaux ISO en minuscules et utiliser un trait de soulignement (`_`) au lieu d’un tiret/tiret (`-`), par exemple : `de_ch`.

Par exemple, lorsque la balise **Animals** est ajoutée à la page **Produits** , la valeur `stockphotography:animals` est ajoutée à la propriété `cq:tags` du noeud `/content/wknd/en/products/jcr:content`. La traduction est référencée à partir du nœud de balise.

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

The following procedure describes how to add a new language (e.g. Finnish) to the **Tag Edit** dialog:

1. In **CRXDE**, edit the multi-value property `languages` of the node `/content/cq:tags`.
1. Add `fi_fi`, which represents the Finnish locale, and save the changes.

Finnish is now available in the tag dialog of the page properties and in the **Edit Tag** dialog when editing a tag in the **Tagging** console.

>[!NOTE]
>
>La nouvelle langue doit faire partie de celles reconnues par AEM, c’est-à-dire qu’elle doit être disponible sous `/libs/wcm/core/resources/languages`.
