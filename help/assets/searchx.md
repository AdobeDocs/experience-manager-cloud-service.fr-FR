---
title: Étendre les options et fonctionnalités de recherche dans Adobe Experience Manager Assets
description: Étendre les fonctionnalités de recherche d’Assets.
contentOwner: AG
translation-type: ht
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Étendre la recherche de ressources{#extend-assets-search}

Vous pouvez étendre la recherche dans Adobe Experience Manager (AEM) Assets. AEM Assets propose des recherches prêtes à l’emploi de ressources par chaînes.

La recherche est effectuée par le biais de l’interface QueryBuilder, de sorte qu’elle puisse être personnalisée avec plusieurs prédicats. Vous pouvez remplacer l’ensemble des prédicats par défaut dans le répertoire suivant : `/apps/dam/content/search/searchpanel/facets`.

Vous pouvez également ajouter des onglets supplémentaires au panneau d’administration d’AEM Assets.

## Incrustation {#overlay}

Pour remplacer les prédicats préconfigurés, copiez le nœud `facets` du répertoire `/libs/dam/content/search/searchpanel` dans le répertoire `/apps/dam/content/search/searchpanel/` ou spécifiez une autre propriété `facetURL` dans la configuration du panneau de recherche (la valeur par défaut est `/libs/dam/content/search/searchpanel/facets.overlay.infinity.json`).

>[!NOTE]
>
>Par défaut, la structure de répertoire sous `/apps` n’existe pas et doit être créée. Assurez-vous que les types de nœuds correspondent à ceux existant sous `/libs`.

### Ajouter des onglets {#add-tabs}

Vous pouvez ajouter des onglets de recherche supplémentaires en les configurant dans le panneau d’administration d’AEM Assets. Pour créer des onglets supplémentaires, procédez comme suit :

1. Créez la structure de dossiers `/apps/wcm/core/content/damadmin/tabs,`si elle n’existe pas encore, puis copiez le nœud `tabs` dans le répertoire `/libs/wcm/core/content/damadmin` et collez-le.
1. Créez et configurez le second onglet, le cas échéant.

   >[!NOTE]
   >
   >Lorsque vous créez un second nœud `siteadminsearchpanel`, assurez-vous de définir une propriété `id` afin d’éviter tout conflit de formulaire.

### Création de prédicats personnalisés {#create-custom-predicates}

AEM Assets est fourni avec un ensemble de prédicats prédéfinis qui peuvent être utilisés pour personnaliser une page de partage de ressources.
<!-- In addition to using pre-existing predicates, AEM developers can also create their own predicates using the [Query Builder API](/help/sites-developing/querybuilder-api.md). -->

La création de prédicats personnalisés nécessite des connaissances de base sur la [structure des widgets](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html).

La pratique recommandée consiste à copier un prédicat existant, puis à le modifier. Des exemples de prédicats sont disponibles dans le répertoire **/libs/cq/search/components/predicates**.

#### Exemple : création d’un prédicat de propriété simple   {#example-build-a-simple-property-predicate}

Pour créer un prédicat de propriété, procédez comme suit :

1. Créez un dossier de composant dans votre répertoire de projets, par exemple **/apps/geometrixx/components/titlepredicate**.
1. Ajoutez **content.xml** :

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Title Predicate"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Search"/>
   ```

1. Ajoutez `titlepredicate.jsp`.

   ```xml
   <%--
   
     Sample title predicate component
   
   --%><%@ page import="java.util.Calendar" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       // A unique id is necessary in case this predicate is inserted multiple times on the same page
       String elemId = "cq-predicate-" +  Long.toString(Calendar.getInstance().getTimeInMillis());
   
   %><div class="predicatebox">
   
       <div class="title">Title</div>
   
       <%-- The wrapper for the form elements. All items will be append to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:title";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // createId adds a counter to the predicate name - useful in case this predicate
           // is inserted multiple times on the same page.
           var id = qb.createId(predicateName);
   
           // Hidden field that defines the property to search for; in our case this
           // is the "dc:title" metadata. The name "property" (or "1_property", "2_property" etc.)
           // indicates the server to use the property predicate
           // (com.day.cq.search.eval.JcrPropertyPredicateEvaluator).
           qb.addField({
               "xtype": "hidden",
               "renderTo": elemId,
               "name": id,
               "value": propertyName
           });
   
           // The visible text field. The name has to be like the one of the hidden field above
           // plus the ".value" suffix.
           qb.addField({
               "xtype": "textfield",
               "renderTo": elemId,
               "name": id + ".value"
           });
   
           // Depending on the predicate additional parameters allow to configure the
           // predicate. Here we add an operation parameter to create a "like" query.
           // Again note the name set to the id and a suffix.
           qb.addField({
               "xtype": "hidden",
               "renderTo": elemId,
               "name": id + ".operation",
               "value": "like"
           });
       });
   </script>
   ```

1. Pour rendre le composant accessible, vous devez être en mesure de le modifier. Pour rendre un composant modifiable, dans CRXDE, ajoutez un nœud **cq:editConfig** du type principal **cq:EditConfig**. Afin de pouvoir supprimer des paragraphes, ajoutez une propriété à valeurs multiples **cq:actions** avec une valeur unique de **DELETE**.
1. Accédez à votre navigateur puis, sur votre exemple de page (par exemple **press.html**), basculez en mode de conception et activez votre nouveau composant pour le système de paragraphes de prédicats (par exemple **left**).

1. En mode d’**édition**, le nouveau composant est désormais disponible dans le sidekick (accessible dans le groupe **Recherche**). Insérez le composant dans la colonne **Prédicats** et saisissez un mot de recherche, par exemple **Diamant**, puis cliquez sur la loupe pour lancer la recherche.

   >[!NOTE]
   >
   >Lors de la recherche, assurez-vous de saisir le terme exact en respectant la casse.

#### Exemple : création d’un prédicat de groupe simple {#example-build-a-simple-group-predicate}

Pour créer un prédicat de groupe, procédez comme suit :

1. Créez un dossier de composant dans votre répertoire de projets, par exemple **/apps/geometrixx/components/picspredicate**.
1. Ajoutez **content.xml** :

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Image Formats"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Search"/>
   ```

1. Ajoutez **titlepredicate.jsp** :

   ```xml
   <%--
   
     Sample group predicate component
   
   --%><%@ page import="java.util.Calendar" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       // A unique id is necessary in case this predicate is inserted multiple times on the same page.
       String elemId = "cq-predicate-" +  Long.toString(Calendar.getInstance().getTimeInMillis());
   
   %><div class="predicatebox">
   
       <div class="title">Image Formats</div>
   
       <%-- The wrapper for the form elements. All items will be append to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:format";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // Create a unique group ID; will return e.g. "1_group".
           var groupId = qb.createGroupId();
   
           // Hidden field that defines the property to search for  - in our case "dc:format" -
           // and declares the group of predicates. "property" in the name ("1_group.property")
           // indicates to the server to use the "property predicate"
           // (com.day.cq.search.eval.JcrPropertyPredicateEvaluator).
           qb.addField({
               "xtype": "hidden",
               "renderTo": "<%= elemId %>",
               "name": groupId + "." + predicateName, // 1_group.property
               "value": propertyName
           });
   
           // Declare to combine the multiple values using OR.
           qb.add(new CQ.Ext.form.Hidden({
               "name": groupId + ".p.or",  // 1_group.p.or
               "value": "true"
           }));
   
           // The options
           var options = [
               { "label":"JPEG", "value":"image/jpeg"},
               { "label":"PNG",  "value":"image/png" },
               { "label":"GIF",  "value":"image/gif" }
           ];
   
           // Build a checkbox for each option.
           for (var i = 0; i < options.length; i++) {
               qb.addField({
                   "xtype": "checkbox",
                   "renderTo": "<%= elemId %>",
                   // 1_group.property.0_value, 1_group.property.1_value etc.
                   "name": groupId + "." +  predicateName + "." + i + "_value",
                   "inputValue": options[i].value,
                   "boxLabel": options[i].label,
                   "listeners": {
                       "check": function() {
                           // Submit the search form when checking/unchecking a checkbox.
                           qb.submit();
                       }
                   }
               });
           }
       });
   ```

1. Pour rendre le composant accessible, vous devez être en mesure de le modifier. Pour rendre un composant modifiable, dans CRXDE, ajoutez un nœud **cq:editConfig** du type principal **cq:EditConfig**. Afin de pouvoir supprimer des paragraphes, ajoutez une propriété à valeurs multiples **cq:actions** avec une valeur unique de **DELETE**.
1. Accédez à votre navigateur puis, sur votre exemple de page (par exemple **press.html**), basculez en mode de conception et activez votre nouveau composant pour le système de paragraphes de prédicats (par exemple **left**).
1. En mode d’**édition**, le nouveau composant est désormais disponible dans le sidekick (accessible dans le groupe **Recherche**). Insérez le composant dans la colonne **Prédicats**.

### Widgets de prédicats installés {#installed-predicate-widgets}

Les prédicats suivants sont disponibles en tant que widgets ExtJS préconfigurés.

#### FulltextPredicate   {#fulltextpredicate}

<table>
 <tbody>
  <tr>
   <td><strong>Propriétés<br /> </strong></td>
   <td><strong>Type</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
   <td>predicateName</td>
   <td>Chaîne</td>
   <td>Nom du prédicat. Par défaut : « fulltext »</td>
  </tr>
  <tr>
   <td>searchCallback</td>
   <td>Fonction</td>
   <td>Rappel pour déclencher une recherche sur l’événement « keyup ». Par défaut : « CQ.wcm.SiteAdmin.doSearch »</td>
  </tr>
 </tbody>
</table>

#### PropertyPredicate {#propertypredicate}

<table>
 <tbody>
  <tr>
   <td><strong>Propriétés<br /> </strong></td>
   <td><strong>Type</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
   <td>predicateName</td>
   <td>Chaîne</td>
   <td>Nom du prédicat. La valeur par défaut est 'propriété'</td>
  </tr>
  <tr>
   <td>propertyName</td>
   <td>Chaîne </td>
   <td>Nom de la propriété JCR. Par défaut : « jcr:title »</td>
  </tr>
  <tr>
   <td>defaultValue<br /> </td>
   <td>Chaîne<br /> </td>
   <td>Valeur par défaut préremplie.<br /> </td>
  </tr>
 </tbody>
</table>

#### PathPredicate {#pathpredicate}

<table>
 <tbody>
  <tr>
   <td><strong>Propriétés<br /> </strong></td>
   <td><strong>Type</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
   <td>predicateName</td>
   <td>Chaîne</td>
   <td>Nom du prédicat. Par défaut : « path »</td>
  </tr>
  <tr>
   <td>rootPath</td>
   <td>Chaîne </td>
   <td>Chemin racine du prédicat. Par défaut : « /content/dam »</td>
  </tr>
  <tr>
   <td>pathFieldPredicateName</td>
   <td>Chaîne</td>
   <td>Par défaut : « folder »</td>
  </tr>
  <tr>
   <td>showFlatOption</td>
   <td>Booléen</td>
   <td>Indicateur permettant d’afficher la case à cocher « Rechercher dans les sous-dossiers ». La valeur par défaut est « true ».</td>
  </tr>
 </tbody>
</table>

#### DatePredicate {#datepredicate}

<table>
 <tbody>
  <tr>
   <td><strong>Propriétés<br /> </strong></td>
   <td><strong>Type</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
   <td>predicateName</td>
   <td>Chaîne</td>
   <td>Nom du prédicat. Par défaut : « daterange »</td>
  </tr>
  <tr>
   <td>propertyName</td>
   <td>Chaîne</td>
   <td>Nom de la propriété JCR. Par défaut : « jcr:content/jcr:lastModified »</td>
  </tr>
  <tr>
   <td>defaultValue </td>
   <td>Chaîne </td>
   <td>Valeur par défaut préremplie </td>
  </tr>
 </tbody>
</table>

#### OptionsPredicate {#optionspredicate}

<table>
 <tbody>
  <tr>
   <td><strong>Propriétés<br /> </strong></td>
   <td><strong>Type</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
   <td>titre </td>
   <td>Chaîne </td>
   <td>Ajoute un titre supérieur supplémentaire </td>
  </tr>
  <tr>
   <td>predicateName</td>
   <td>Chaîne</td>
   <td>Nom du prédicat. Par défaut : « daterange »</td>
  </tr>
  <tr>
   <td>propertyName</td>
   <td>Chaîne</td>
   <td>Nom de la propriété JCR. Par défaut : « jcr:content/metadata/cq:tags »</td>
  </tr>
  <tr>
   <td>collapse</td>
   <td>Chaîne</td>
   <td>Réduire par niveau. Par défaut : « level1 »</td>
  </tr>
  <tr>
   <td>triggerSearch</td>
   <td>Booléen </td>
   <td>Indicateur de déclenchement de la recherche lors de la vérification. Par défaut : « false »</td>
  </tr>
  <tr>
   <td>searchCallback</td>
   <td>Fonction</td>
   <td>Rappel pour déclencher la recherche. Par défaut : « CQ.wcm.SiteAdmin.doSearch »</td>
  </tr>
  <tr>
   <td>searchTimeoutTime</td>
   <td>Nombre</td>
   <td>Délai d’expiration avant le déclenchement de searchCallback. Valeur par défaut : 800 ms</td>
  </tr>
 </tbody>
</table>
