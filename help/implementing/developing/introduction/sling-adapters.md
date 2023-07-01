---
title: Utilisation des adaptateurs Sling
description: Sling propose un modèle Adaptateur permettant de convertir facilement les objets qui mettent en œuvre l’interface Adaptable
exl-id: 8ffe3bbd-01fe-44c2-bf60-7a4d25a6ba2b
source-git-commit: a01583483fa89f89b60277c2ce4e1c440590e96c
workflow-type: tm+mt
source-wordcount: '2214'
ht-degree: 28%

---

# Utilisation des adaptateurs Sling {#using-sling-adapters}

[Sling](https://sling.apache.org) propose un [modèle Adaptateur](https://sling.apache.org/documentation/the-sling-engine/adapters.html) permettant de convertir facilement les objets qui mettent en œuvre l’interface [Adaptable](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29). Cette interface fournit une variable générique [adaptTo()](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) qui convertit l’objet au type de classe transmis en tant qu’argument.

Par exemple, pour convertir un objet Resource en objet Node correspondant, vous pouvez simplement :

```java
Node node = resource.adaptTo(Node.class);
```

## Cas d’utilisation {#use-cases}

Il existe plusieurs scénarios d’utilisation :

* Obtenir des objets spécifiques à l’implémentation.

  Par exemple, une implémentation basée sur JCR de l’interface [`Resource`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/Resource.html) permet d’accéder à l’objet [`Node`](https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) JCR sous-jacent.

* Création de raccourcis d’objets qui nécessitent la transmission d’objets de contexte internes.

  Par exemple, la variable basée sur JCR [`ResourceResolver`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ResourceResolver.html) contient une référence à la variable [`JCR Session`](https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html), qui, à son tour, est nécessaire pour de nombreux objets qui fonctionnent sur la base de cette session de requête, tels que [`PageManager`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/PageManager.html) ou [`UserManager`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/security/UserManager.html).

* Raccourci vers les services.

  Cas peu fréquent : `sling.getService()` s’avère également simple.

### Valeur renvoyée nulle {#null-return-value}

`adaptTo()` Peut renvoyer une valeur nulle.

Il existe plusieurs raisons pour le retour nul, notamment :

* l’implémentation ne prend pas en charge le type de cible.
* une fabrique d’adaptateur qui gère ce cas n’est pas principale (par exemple, en raison de références de service manquantes).
* la condition interne a échoué
* Le service n’est pas disponible.

Il est important que vous gériez le cas &quot;null&quot; avec élégance. Pour les rendus jsp, il peut être acceptable que le jsp échoue si cela entraîne un élément de contenu vide.

### Mise en cache {#caching}

Pour améliorer les performances, les implémentations peuvent mettre en cache l’objet renvoyé par un appel `obj.adaptTo()`. Si `obj` est identique, l’objet renvoyé l’est également.

Cette mise en cache est exécutée pour tous les scénarios basés sur `AdapterFactory`.

Cependant, il n’existe aucune règle générale : l’objet peut être soit une nouvelle instance, soit une instance existante. En tant que tel, cela signifie que vous ne pouvez pas vous fier à aucun des comportements. Par conséquent, il est important, notamment dans `AdapterFactory`, que les objets soient réutilisables dans ce scénario.

### Fonctionnement {#how-it-works}

`Adaptable.adaptTo()` peut être implémenté de différentes façons :

* Par l’objet proprement dit ; implémentation de la méthode et mappage sur certains objets.
* Par une [`AdapterFactory`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/AdapterFactory.html), qui peut mapper des objets arbitraires.

  Les objets doivent cependant implémenter l’interface `Adaptable` et étendre [`SlingAdaptable`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/adapter/SlingAdaptable.html) (qui transmet l’appel `adaptTo` à un gestionnaire d’adaptateur central).

  Cette méthode permet d’ajouter des hooks dans la variable `adaptTo` pour les classes existantes, par exemple `Resource`.

* Une combinaison des deux.

Pour le premier cas, les documents Java™ peuvent indiquer ce qui suit : `adaptTo-targets` sont possibles. Cependant, pour des sous-classes spécifiques telles que la ressource basée sur JCR, cette instruction est souvent impossible. Dans ce dernier cas, les implémentations de `AdapterFactory` font généralement partie des classes privées d’un lot et ne sont donc pas exposées dans une API client, ni répertoriées dans la documentation Java™. En théorie, il est possible d’accéder à tous les `AdapterFactory` les mises en oeuvre de [OSGi](/help/implementing/deploying/configuring-osgi.md) Exécution du service et observez leurs configurations &quot;adaptables&quot; (sources et cibles), mais pas pour les mapper les unes aux autres. En fin de compte, cela dépend de la logique interne, qui doit être documentée. D’où cette référence.

## Référence {#reference}

### Sling {#sling}

[**Resource**](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html) s’adapte à :

<table>
 <tbody>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Nœud</a></td>
   <td>S’il s’agit d’une ressource basée sur un noeud JCR ou d’une propriété JCR, en référençant un noeud</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Property.html">Propriété</a></td>
   <td>S’il s’agit d’une ressource basée sur une propriété JCR</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Item.html">Élément</a></td>
   <td>S’il s’agit d’une ressource basée sur JCR (noeud ou propriété)</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/util/Map.html">Map</a></td>
   <td>Renvoie un mappage des propriétés, s’il s’agit d’une ressource basée sur un noeud JCR (ou une autre ressource prenant en charge les mappages de valeurs)</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a></td>
   <td>Renvoie un mappage convivial des propriétés, s’il s’agit d’une ressource basée sur un noeud JCR (ou une autre ressource prenant en charge les mappages de valeurs). Peut également être réalisé (plus simplement) en utilisant<br /> <code><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/ResourceUtil.html">ResourceUtil.getValueMap(Resource)</a></code> (gère la casse nulle, etc.)</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/inherit/InheritanceValueMap.html">InheritanceValueMap</a></td>
   <td>Extension de <a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a> qui permet de prendre en compte la hiérarchie des ressources lors de la recherche de propriétés.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/ModifiableValueMap.html">ModifiableValueMap</a></td>
   <td>Extension de <a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a> qui vous permet de modifier les propriétés sur ce nœud</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/io/InputStream.html">InputStream</a></td>
   <td>Renvoie le contenu binaire d’une ressource de fichier (s’il s’agit d’une ressource basée sur un noeud JCR et que le type de noeud est <code>nt:file</code> ou <code>nt:resource</code>; s’il s’agit d’une ressource de lot ; contenu du fichier, s’il s’agit d’une ressource de système de fichiers). Ou renvoie les données d’une ressource de propriété JCR binaire.</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/net/URL.html">URL</a></td>
   <td>Renvoie une URL vers la ressource (URL du référentiel de ce noeud s’il s’agit d’une ressource basée sur un noeud JCR ; URL du lot jar s’il s’agit d’une ressource de lot ; URL du fichier s’il s’agit d’une ressource de système de fichiers)</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/io/File.html">File</a></td>
   <td>S’il s’agit d’une ressource de système de fichiers</td>
  </tr>
  <tr>
   <td><a href="https://sling.apache.org/apidocs/sling5/org/apache/sling/api/scripting/SlingScript.html">SlingScript</a></td>
   <td>Si la ressource est un script (par exemple, un fichier jsp) pour lequel un moteur de script est enregistré avec sling</td>
  </tr>
  <tr>
   <td><a href="https://www.oracle.com/java/technologies/servlet-technology.html">Servlet</a></td>
   <td>Si la ressource est un script (un fichier jsp, par exemple) pour lequel un moteur de script est enregistré avec sling ou s’il s’agit d’une ressource de servlet</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/String.html">String</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Boolean.html">Boolean</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Long.html">Long</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Double.html">Double</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/util/Calendar.html">Calendar</a><br /> <a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Value.html">Value</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/String.html">String[]</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Boolean.html">Boolean[]</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Long.html">Long[]</a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/util/Calendar.html">Calendar[]</a><br /> <a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Value.html">Value[]</a></td>
   <td>Renvoie les valeurs s’il s’agit d’une ressource basée sur une propriété JCR (et que la valeur convient)</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>S’il s’agit d’une ressource basée sur un noeud JCR</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/Page.html">Page</a></td>
   <td>S’il s’agit d’une ressource basée sur un noeud JCR et que le noeud est une <code>cq:Page</code> (ou <code>cq:PseudoPage</code>)</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/components/Component.html">Composant</a></td>
   <td>S’il s’agit d’une <code>cq:Component</code> ressource de noeud</td>
  </tr>  
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/designer/Design.html">Conception</a></td>
   <td>S’il s’agit d’un noeud de conception (<code>cq:Page</code>)</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/Template.html">Modèle </a></td>
   <td>S’il s’agit d’une <code>cq:Template</code> ressource de noeud</td>
  </tr>  
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/msm/api/Blueprint.html">Plan directeur</a></td>
   <td>S’il s’agit d’une <code>cq:Template</code> ressource de noeud</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/dam/api/Asset.html">Asset</a></td>
   <td>S’il s’agit d’une ressource de noeud dam:Asset</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/dam/api/Rendition.html">Rendition</a></td>
   <td>S’il s’agit d’un rendu dam:Asset (nt:file sous le dossier de rendu d’un noeud dam:Asset)</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/tagging/Tag.html">Balise</a></td>
   <td>S’il s’agit d’une <code>cq:Tag</code> ressource de noeud</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/security/UserManager.html">UserManager</a></td>
   <td>Basé sur la session JCR s’il s’agit d’une ressource basée sur JCR et que l’utilisateur est autorisé à accéder à UserManager.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">Authorizable</a></td>
   <td>Authorizable est la base commune de User et Group</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/jackrabbit/api/security/user/User.html">Utilisateur</a></td>
   <td>User est un objet Authorizable spécial qui peut être authentifié et dont il est possible d’emprunter l’identité</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/SimpleSearch.html">SimpleSearch</a></td>
   <td>Recherche sous la ressource (ou utilisez setSearchIn()) s’il s’agit d’une ressource basée sur JCR.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/workflow/status/WorkflowStatus.html">WorkflowStatus</a></td>
   <td>État du workflow pour le nœud de charge utile de la page/du workflow donné</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/replication/ReplicationStatus.html">ReplicationStatus</a></td>
   <td>État de réplication de la ressource donnée ou de son sous-nœud jcr:content (vérifié en premier)</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/connector/ConnectorResource.html">ConnectorResource</a></td>
   <td>Renvoie une ressource de connecteur adaptée pour certains types, s’il s’agit d’une ressource basée sur un noeud JCR</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/contentsync/config/package-summary.html">Config</a></td>
   <td>S’il s’agit d’une <code>cq:ContentSyncConfig</code> ressource de noeud</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/contentsync/config/package-summary.html">ConfigEntry</a></td>
   <td>S’il se trouve sous un <code>cq:ContentSyncConfig</code> ressource de noeud</td>
  </tr>
 </tbody>
</table>

[**ResourceResolver**](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/ResourceResolver.html) s’adapte à :

<table>
 <tbody>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html">Session</a></td>
   <td>Session JCR de la requête, s’il s’agit d’un résolveur de ressources basé sur JCR (par défaut).</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/PageManager.html">PageManager</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/components/ComponentManager.html">ComponentManager</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/designer/Designer.html">Designer</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/dam/api/AssetManager.html">AssetManager</a></td>
   <td>Selon la session JCR, s’il s’agit d’un résolveur de ressources basé sur JCR</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/tagging/TagManager.html">TagManager</a></td>
   <td>Selon la session JCR, s’il s’agit d’un résolveur de ressources basé sur JCR</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/jackrabbit/api/security/user/UserManager.html">UserManager</a></td>
   <td>UserManager permet d’accéder aux objets autorisables et de les gérer, c’est-à-dire les utilisateurs et les groupes. UserManager est lié à une session particulière
   </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">Authorizable</a> </td>
   <td>Utilisateur actuel</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/jackrabbit/api/security/user/User.html">Utilisateur</a><br /> </td>
   <td>Utilisateur actuel</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/QueryBuilder.html">QueryBuilder</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/Externalizer.html">Externalizer</a></td>
   <td>Pour externaliser des URL absolues, même sans l’objet de requête<br /> </td>
  </tr>
 </tbody>
</table>

[**SlingHttpServletRequest**](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/SlingHttpServletRequest.html) s’adapte à :

Pas encore de cible, mais implémente l’interface Adaptable et peut être utilisé comme source dans une AdapterFactory personnalisée.

[**SlingHttpServletResponse**](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/SlingHttpServletResponse.html) s’adapte à :

<table>
 <tbody>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/org/xml/sax/ContentHandler.html">ContentHandler</a><br /> (XML)</td>
   <td>S’il s’agit d’une réponse de réécriture sling</td>
  </tr>
 </tbody>
</table>

#### WCM {#wcm}

**[Page](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/Page.html)** s’adapte à :

<table>
 <tbody>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html">Resource</a><br /> </td>
   <td>Ressource de la page</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>Ressource étiquetée (== this).</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Node</a></td>
   <td>Nœud de la page.</td>
  </tr>
  <tr>
   <td>…</td>
   <td>Tous les éléments auxquels la ressource de la page peut être adaptée.</td>
  </tr>
 </tbody>
</table>

**[Component](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/components/Component.html)** s’adapte à :

| [Resource](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html) | Ressource du composant. |
|---|---|
| [LabeledResource](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/LabeledResource.html) | Ressource étiquetée (== this). |
| [Node](https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Nœud du composant. |
| … | Tous les éléments auxquels la ressource du composant peut être adaptée. |

**[Template](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/Template.html)** s’adapte à :

<table>
 <tbody>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html">Resource</a><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html"><br /> </a></td>
   <td>Ressource du modèle.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>Ressource étiquetée (== this).</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Node</a></td>
   <td>Nœud de ce modèle.</td>
  </tr>
  <tr>
   <td>…</td>
   <td>Tous les éléments auxquels la ressource du modèle peut être adaptée.</td>
  </tr>
 </tbody>
</table>

#### Sécurité {#security}

**Authorizable**, **Utilisateur**, et **Groupe** adapter à :

| [Node](https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Renvoie le nœud racine utilisateur/groupe. |
|---|---|
| [ReplicationStatus](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/replication/ReplicationStatus.html) | Renvoie le statut de réplication pour le nœud racine utilisateur/groupe. |

#### Gestion des ressources numériques (DAM) {#dam}

**Asset** s’adapte à :

| [Resource](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html) | Ressource de l’actif. |
|---|---|
| [Node](https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Nœud de la ressource. |
| … | Tous les éléments auxquels la ressource de l’actif peut être adaptée. |

#### Balisage {#tagging}

**Tag** s’adapte à :

| [Resource](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html) | Ressource de la balise. |
|---|---|
| [Node](https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Nœud de la balise. |
| … | Tous les éléments auxquels la ressource de la balise peut être adaptée. |

#### Autres {#other}

Sling/JCR/OCM fournit, en outre, un [`AdapterFactory`](https://sling.apache.org/documentation/the-sling-engine/adapters.html) pour les objets OCM ([Object Content Mapping](https://jackrabbit.apache.org/jcr/object-content-mapping.html)) personnalisés.
