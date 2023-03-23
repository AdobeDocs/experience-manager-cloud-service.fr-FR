---
title: Prise en main d’Universal Editor dans AEM
description: Découvrez comment accéder à l’éditeur universel et comment commencer à instrumenter votre première application AEM pour l’utiliser.
source-git-commit: 0e66c379e10d275610d85a699da272dc0c32a9a8
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 0%

---


# Prise en main d’Universal Editor dans AEM {#getting-started}

Découvrez comment accéder à l’éditeur universel et comment commencer à instrumenter votre première application AEM pour l’utiliser.

>[!TIP]
>
>Si vous préférez plonger directement dans un exemple, vous pouvez consulter la section [Exemple d’application Universal Editor sur GitHub.](https://github.com/adobe/universal-editor-sample-editable-app)

## Étapes d’intégration {#onboarding}

Bien qu’Universal Editor puisse modifier du contenu à partir de n’importe quelle source, ce document utilise une application AEM comme exemple.

Il existe plusieurs étapes pour intégrer votre application AEM et l’instrumenter pour utiliser l’éditeur universel.

1. [Demandez l’accès à l’éditeur universel.](#request-access)
1. [Incluez la bibliothèque principale Universal Editor.](#core-library)
1. [Ajoutez la configuration OSGi nécessaire.](#osgi-configurations)
1. [Instrument de la page.](#instrument-page)

Ce document vous guidera tout au long de ces étapes.

## Demande d’accès à l’éditeur universel {#request-access}

Vous devez d’abord demander l’accès à l’éditeur universel. Accédez à [https://experience.adobe.com/#/aem/editor](https://experience.adobe.com/#/aem/editor) et validez si vous avez accès à l’éditeur universel.

Si vous n&#39;avez pas accès, vous pouvez le demander via un formulaire lié à la même page.

## Inclure la bibliothèque Core d’Universal Editor {#core-library}

Avant de pouvoir être instrumentée pour une utilisation avec l’éditeur universel, votre application doit inclure la dépendance suivante.

```javascript
@adobe/universal-editor-cors
```

Pour activer l’instrumentation, l’importation suivante doit être ajoutée à votre `index.js`.

```javascript
import "@adobe/universal-editor-cors";
```

### Alternative pour les applications non React {#alternative}

Si vous ne mettez pas en oeuvre d’application React et/ou avez besoin d’un rendu côté serveur, une autre méthode consiste à inclure les éléments suivants dans le corps du document.

```html
<script src="https://cdn.jsdelivr.net/gh/adobe/universal-editor-cors/dist/universal-editor-embedded.js" async></script>
```

## Ajout des configurations OSGi nécessaires {#osgi-configurations}

Pour pouvoir modifier AEM contenu avec votre application à l’aide de l’éditeur universel, les paramètres CORS et de cookie doivent être définis dans AEM.

Les éléments suivants [Les configurations OSGi doivent être définies sur l’instance de création AEM.](/help/implementing/deploying/configuring-osgi.md)

* `SameSite Cookies = None` in `com.day.crx.security.token.impl.impl.TokenAuthenticationHandler`
* Supprimez les OPTIONS X-FRAME : En-tête SAMEORIGIN dans `org.apache.sling.engine.impl.SlingMainServlet`

### com.day.crx.security.token.impl.impl.TokenAuthenticationHandler {#samesite-cookies}

Le cookie de jeton de connexion doit être envoyé à AEM en tant que domaine tiers. Par conséquent, le cookie du même site doit être défini explicitement sur `None`.

Cette propriété doit être définie dans la variable `com.day.crx.security.token.impl.impl.TokenAuthenticationHandler` Configuration OSGi.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
          xmlns:jcr="http://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig"
          token.samesite.cookie.attr="None" />
```

### org.apache.sling.engine.impl.SlingMainServlet {#sameorigin}

X-Frame-Options: SAMEORIGIN empêche le rendu AEM pages dans un iframe. La suppression de l’en-tête permet de charger les pages.

Cette propriété doit être définie dans la variable `org.apache.sling.engine.impl.SlingMainServlet` Configuration OSGi.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
          xmlns:jcr="http://www.jcp.org/jcr/1.0"
          jcr:primaryType="sling:OsgiConfig"
          sling.additional.response.headers="[X-Content-Type-Options=nosniff]"/>
```

## Instrument de la page {#instrument-page}

Le service Universal Editor requiert une [nom de ressource uniforme (URN)](https://en.wikipedia.org/wiki/Uniform_Resource_Name) pour identifier et utiliser le système principal approprié pour le contenu de l’application en cours de modification. Par conséquent, un schéma d’URL est nécessaire pour mapper le contenu aux ressources de contenu.

Les attributs d’instrumentation ajoutés à la page se composent principalement de [Microdonnées de HTML,](https://developer.mozilla.org/en-US/docs/Web/HTML/Microdata) une norme du secteur qui peut également être utilisée pour rendre le HTML plus sémantique, rendre les documents de HTML indexables, etc.

### Création de connexions {#connections}

Les connexions utilisées dans l’application sont stockées sous la forme `<meta>` balises de la page `<head>`.

```html
<meta name="urn:auecon:<referenceName>" content="<protocol>:<url>">
```

* `<referenceName>` - Il s’agit d’un nom court réutilisé dans le document pour identifier la connexion. Par exemple : `aemconnection`
* `<protocol>` - Indique le module externe de persistance du service de persistance de l’éditeur universel à utiliser. Par exemple : `aem`
* `<url>` - Il s’agit de l’URL vers le système où les modifications doivent être conservées. Par exemple : `http://localhost:4502`

Identifiant court `auecon` signifie Adobe Universal Editor Connection.

`itemid`s utilisera la variable `urn` pour raccourcir l’identifiant.

```html
itemid="urn:<referenceName>:<resource>"
```

* `<referenceName>` - Il s’agit de la référence nommée mentionnée dans la variable `<meta>` balise . Par exemple : `aemconnection`
* `<resource>` - Il s’agit d’un pointeur vers la ressource du système cible. Par exemple, un chemin de contenu AEM tel que `/content/page/jcr:content`

>[!TIP]
>
>Voir le document [Attributs et types](attributes-types.md) pour plus d’informations sur les attributs et les types de données requis par Universal Editor.

### Exemple de connexion {#example}

```html
<html>
<head>
    <meta name="urn:auecon:aemconnection" content="aem:https://localhost:4502">
    <meta name="urn:auecon:fcsconnection" content="fcs:https://example.franklin.adobe.com/345fcdd">
</head>
<body>
        <aside>
          <ul itemscope itemid="urn:aemconnection:/content/example/list" itemtype="container">
            <li itemscope itemid="urn:aemconnection/content/example/listitem" itemtype="component">
              <p itemprop="name" itemtype="text">Jane Doe</p>
              <p itemprop="title" itemtype="text">Journalist</p>
              <img itemprop="avatar" src="https://www.adobe.com/content/dam/cc/icons/Adobe_Corporate_Horizontal_Red_HEX.svg" itemtype="image" alt="avatar"/>
            </li>
 
...
 
            <li itemscope itemid="urn:fcsconnection:/documents/mytext" itemtype="component">
              <p itemprop="name" itemtype="text">John Smith</p>
              <p itemid="urn:aemconnection/content/example/another-source" itemprop="title" itemtype="text">Photographer</p>
              <img itemprop="avatar" src="https://www.adobe.com/content/dam/cc/icons/Adobe_Corporate_Horizontal_Red_HEX.svg" itemtype="image" alt="avatar"/>
            </li>
          </ul>
        </aside>
</body>
</html>
```

## Vous êtes prêt à utiliser l’éditeur universel {#youre-ready}

Votre application est désormais instrumentée pour utiliser l’éditeur universel.

Reportez-vous au document [Création de contenu avec l’éditeur universel](authoring.md) pour savoir à quel point il est facile et intuitif pour les auteurs de contenu de créer du contenu à l’aide de l’éditeur universel.

## Ressources supplémentaires {#additional-resources}

Pour en savoir plus sur Universal Editor, consultez ces documents.

* [Présentation de l’éditeur universel](introduction.md) - Découvrez comment Universal Editor permet de modifier n’importe quel aspect de contenu dans n’importe quelle mise en oeuvre afin de fournir des expériences exceptionnelles, d’augmenter la vitesse du contenu et de fournir une expérience de développement à la pointe de la technologie.
* [Création de contenu avec l’éditeur universel](authoring.md) - Découvrez à quel point il est facile et intuitif pour les auteurs de contenu de créer du contenu à l’aide de l’éditeur universel.
* [Publication de contenu avec l’éditeur universel](publishing.md) - Découvrez comment l’éditeur visuel universel publie du contenu et comment vos applications peuvent gérer le contenu publié.
* [Architecture d’éditeur universelle](architecture.md) - Découvrez l’architecture d’Universal Editor et le flux de données entre ses services et calques.
* [Attributs et types](attributes-types.md) - Découvrez les attributs et les types de données requis par Universal Editor.
* [Authentification de l’éditeur universel](authentication.md) - Découvrez comment l’éditeur universel s’authentifie.
