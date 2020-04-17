---
title: Extension de l’Éditeur de ressources
description: Découvrez comment étendre les fonctionnalités de l’Éditeur de ressources avec des composants personnalisés.
contentOwner: AG
translation-type: ht
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Extension de l’Éditeur de ressources {#extending-asset-editor}

L’Éditeur de ressources est la page qui s’ouvre lorsque l’utilisateur clique sur une ressource trouvée par le biais du partage de ressources, ce qui lui permet de modifier certains aspects de la ressource, tels que les métadonnées, la miniature, le titre et les balises.

La configuration de l’éditeur à l’aide des composants de modification prédéfinis est traitée dans [Création et configuration d’une page Éditeur de ressources](https://helpx.adobe.com/experience-manager/6-5/assets/using/assets-finder-editor.html).

En plus d’utiliser les composants d’éditeur préexistants, les développeurs d’Adobe Experience Manager (AEM) peuvent créer leurs propres composants.

## Création d’un modèle Éditeur de ressources   {#creating-an-asset-editor-template}

Les exemples de pages suivants sont inclus dans Geometrixx :

* Exemple de page Geometrixx : `/content/geometrixx/en/press/asseteditor.html`
* Exemple de modèle : `/apps/geometrixx/templates/asseteditor`
* Exemple de composant de page : `/apps/geometrixx/components/asseteditor`

### Configuration de clientlib {#configuring-clientlib}

Les composants d’AEM Assets utilisent une extension du clientlib de modification de la gestion du contenu web. Les clientlibs sont généralement chargés dans `init.jsp`.

Par rapport au chargement du clientlib par défaut (au cœur d’`init.jsp`), un modèle AEM Assets doit répondre aux exigences suivantes :

* Le modèle doit inclure le clientlib `cq.dam.edit` (au lieu de `cq.wcm.edit`).

* Le clientlib doit également être inclus lorsque le mode de gestion du contenu web est désactivé (par exemple, transféré lors de la **publication**) pour être en mesure d’effectuer le rendu des prédicats, des actions et des loupes.

Dans la plupart des cas, la copie de l’exemple existant de `init.jsp` (`/apps/geometrixx/components/asseteditor/init.jsp`) doit répondre à ces besoins.

### Configuration des actions JS {#configuring-js-actions}

Certains composants d’AEM Assets nécessitent des fonctions JS définies dans le fichier `component.js`. Copiez ce fichier dans votre répertoire de composants et liez-le.

```xml
<script type="text/javascript" src="<%= component.getPath() %>/component.js"></script>
```

Cet exemple charge cette source JavaScript dans `head.jsp` (`/apps/geometrixx/components/asseteditor/head.jsp`).

### Feuilles de style supplémentaires {#additional-style-sheets}

Certains composants d’AEM Assets utilisent la bibliothèque de widgets d’AEM. Pour que le rendu soit effectué correctement dans le contexte du contenu, une feuille de style supplémentaire doit être chargée. Le composant d’action de balise nécessite une feuille de style supplémentaire.

```xml
<link href="/etc/designs/geometrixx/ui.widgets.css" rel="stylesheet" type="text/css">
```

### Feuille de style Geometrixx   {#geometrixx-style-sheet}

Les exemples de composants de page nécessitent que tous les sélecteurs commencent par `.asseteditor` dans `static.css` (`/etc/designs/geometrixx/static.css`). Bonne pratique : copiez tous les sélecteurs `.asseteditor` dans votre feuille de style et ajustez les règles en fonction de vos besoins.

### FormChooser : réglages pour les ressources chargées par la suite.{#formchooser-adjustments-for-eventually-loaded-resources}

L’Éditeur de ressources utilise le sélecteur de formulaire, qui permet de modifier les ressources sur la même page de formulaire. Pour cela, il suffit d’ajouter un sélecteur de formulaire et le chemin du formulaire vers l’URL de la ressource.

Par exemple :

* Page de formulaire simple : [http://localhost:4502/content/geometrixx/en/press/asseteditor.html](http://localhost:4502/content/geometrixx/en/press/asseteditor.html)
* Ressource chargée dans la page de formulaire : [http://localhost:4502/content/dam/geometrixx/icons/diamond.png.form.html/content/geometrixx/en/press/asseteditor.html](http://localhost:4502/content/dam/geometrixx/icons/diamond.png.form.html/content/geometrixx/en/press/asseteditor.html)

Les exemples de gestionnaires dans `head.jsp` (`/apps/geometrixx/components/asseteditor/head.jsp`) procèdent ainsi :

* Ils détectent si une ressource est chargée ou si le formulaire simple doit être affiché.
* Si une ressource est chargée, ils désactivent le mode de gestion du contenu web, car le parsys ne peut être modifié que sur une page de formulaire simple.
* Si une ressource est chargée, ils utilisent son titre au lieu de celui sur la page de formulaire.

```java
 List<Resource> resources = FormsHelper.getFormEditResources(slingRequest);
    if (resources != null) {
        if (resources.size() == 1) {
            // single resource
            FormsHelper.setFormLoadResource(slingRequest, resources.get(0));
        } else if (resources.size() > 1) {
            // multiple resources
            // not supported by CQ 5.3
        }
    }
    Resource loadResource = (Resource) request.getAttribute("cq.form.loadresource");
    String title;
    if (loadResource != null) {
        // an asset is loaded: disable WCM
        WCMMode.DISABLED.toRequest(request);

        String path = loadResource.getPath();
        Asset asset = loadResource.adaptTo(Asset.class);
        try {
            // it might happen that the adobe xmp lib creates an array
            Object titleObj = asset.getMetadata("dc:title");
            if (titleObj instanceof Object[]) {
                Object[] titleArray = (Object[]) titleObj;
                title = (titleArray.length > 0) ? titleArray[0].toString() : "";
            } else {
                title = titleObj.toString();
            }
        }
        catch (NullPointerException e) {
            title = path.substring(path.lastIndexOf("/") + 1);
        }
    }
    else {
        title = currentPage.getTitle() == null ? currentPage.getName() : currentPage.getTitle();
    }
```

Dans la partie HTML, utilisez l’ensemble de titre précédent (titre de la ressource ou de la page) :

```xml
<title><%= title %></title>
```

## Création d’un composant de champ de formulaire simple   {#creating-a-simple-form-field-component}

Cet exemple illustre comment créer un composant qui affiche les métadonnées d’une ressource chargée.

1. Créez un dossier de composant dans votre répertoire de projets, par exemple, `/apps/geometrixx/components/samplemeta`.
1. Ajoutez `content.xml` avec le fragment de code suivant :

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Image Dimension"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Asset Editor"/>
   ```

1. Ajoutez `samplemeta.jsp` avec le fragment de code suivant :

   ```xml
   <%--
   
     Sample metadata field comopnent
   
   --%><%@ page import="com.day.cq.dam.api.Asset,
                    java.security.AccessControlException" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       String value = "";
       String name = "dam:sampleMetadata";
       boolean readOnly = false;
   
       // If the form page is requested for an asset loadResource will be the asset.
       Resource loadResource = (Resource) request.getAttribute("cq.form.loadresource");
   
       if (loadResource != null) {
   
           // Determine if the loaded asset is read only.
           Session session = slingRequest.getResourceResolver().adaptTo(Session.class);
           try {
               session.checkPermission(loadResource.getPath(), "set_property");
               readOnly = false;
           }
           catch (AccessControlException ace) {
               // checkPermission throws exception if asset is read only
               readOnly = true;
           }
           catch (RepositoryException re) {}
   
           // Get the value of the metadata.
           Asset asset = loadResource.adaptTo(Asset.class);
           try {
               value = asset.getMetadata(name).toString();
           }
           catch (NullPointerException npe) {
               // no metadata dc:description available
           }
       }
   %>
   <div class="form_row">
       <div class="form_leftcol">
           <div class="form_leftcollabel">Sample Metadata</div>
       </div>
       <div class="form_rightcol">
           <%
           if (readOnly) {
               %><c:out value="<%= value %>"/><%
           }
           else {
               %><input class="text" type="text" name="./jcr:content/metadata/<%= name %>" value="<c:out value="<%= value %>" />"><%
           }%>
       </div>
   </div>
   ```

1. Pour rendre le composant accessible, vous devez être en mesure de le modifier. Pour permettre la modification d’un composant, ajoutez un nœud `cq:editConfig` de type principal `cq:EditConfig` dans CRXDE Lite. Afin de pouvoir supprimer des paragraphes, ajoutez une propriété à valeurs multiples `cq:actions` avec une valeur unique de `DELETE`.

1. Accédez à votre navigateur puis, sur votre exemple de page (par exemple, `asseteditor.html`), basculez en mode de conception et activez votre nouveau composant pour le système de paragraphes.

1. En mode d’**édition**, le nouveau composant (par exemple, **Exemple de métadonnées**) est désormais disponible dans le sidekick (qui se trouve dans le groupe **Éditeur de ressources**). Insérez le composant. Pour pouvoir stocker les métadonnées, il doit être ajouté au formulaire de métadonnées.

## Modification des options de métadonnées   {#modifying-metadata-options}

Vous pouvez modifier les espaces de noms disponibles [sous forme de métadonnées](https://helpx.adobe.com/experience-manager/6-5/assets/using/assets-finder-editor.html).

Les métadonnées actuellement disponibles sont définies dans`/libs/dam/options/metadata` :

* Le premier niveau à l’intérieur de ce répertoire contient des espaces de noms.
* Les éléments à l’intérieur de chaque espace de noms représentent une métadonnée, par exemple les résultats dans un élément local.
* Les métadonnées contiennent des informations sur le type et les options à valeurs multiples.

Les options peuvent être remplacées dans`/apps/dam/options/metadata` :

1. Copiez le répertoire de `/libs` vers `/apps`.

1. Supprimez, modifiez ou ajoutez des éléments.

>[!NOTE]
>
>Si vous ajoutez de nouveaux espaces de noms, ils doivent être enregistrés dans votre référentiel/CRX. Sinon, l’envoi du formulaire de métadonnées provoquera une erreur.
