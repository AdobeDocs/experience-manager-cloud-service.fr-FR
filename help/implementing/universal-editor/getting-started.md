---
title: Prise en main de l’éditeur universel dans AEM
description: Découvrez comment accéder à l’éditeur universel et comment commencer à instrumenter votre première application AEM pour l’utiliser.
exl-id: 9091a29e-2deb-4de7-97ea-53ad29c7c44d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: c4dcb1cecb756f746ecb856fcfd65d73833a5ee0
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 37%

---


# Prise en main de l’éditeur universel dans AEM {#getting-started}

Découvrez comment accéder à l’éditeur universel et comment commencer à instrumenter votre première application AEM pour l’utiliser.

>[!TIP]
>
>Si vous préférez plonger directement dans un exemple, vous pouvez consulter la section [ Exemple d’application de l’éditeur universel sur GitHub ](https://github.com/adobe/universal-editor-sample-editable-app).

Bien que l’éditeur universel puisse modifier du contenu à partir de n’importe quelle source, ce document utilise une application AEM comme exemple. Ce document vous guidera tout au fil de ces étapes.

## Instrumenter la page {#instrument-page}

L’éditeur universel requiert une bibliothèque JavaScript pour effectuer le rendu et la modification de la page dans l’éditeur.

En outre, le service d’éditeur universel requiert un [nom de ressource uniforme (URN)](https://fr.wikipedia.org/wiki/Uniform_Resource_Name) pour identifier et utiliser le système principal approprié pour le contenu de l’application en cours de modification. Par conséquent, un schéma URN est nécessaire pour mapper le contenu aux ressources de contenu.

### Inclure la bibliothèque CORS de l’éditeur universel {#cors-library}

Pour que l’éditeur universel puisse se connecter à votre application, votre application doit inclure la bibliothèque CORS de l’éditeur universel. Ajoutez le script suivant à votre application .

```html
 <script src="https://universal-editor-service.adobe.io/cors.js" async></script>
```

### Création de connexions {#connections}

Les connexions utilisées dans l’application sont stockées sous la forme de balises `<meta>` dans la page `<head>`.

```html
<meta name="urn:adobe:aue:<category>:<referenceName>" content="<protocol>:<url>">
```

* `<category>` - Il s’agit d’une classification de la connexion avec deux options.
   * `system` - Pour les points d’entrée de connexion
   * `config` - Pour [définition des paramètres de configuration facultatifs](#configuration-settings)
* `<referenceName>` : il s’agit d’un nom court réutilisé dans le document pour identifier la connexion. Par exemple, `aemconnection`
* `<protocol>` : indique le plug-in de persistance du service de persistance de l’éditeur universel à utiliser. Par ex. `aem`
* `<url>` : il s’agit de l’URL vers le système où les modifications doivent être conservées. Par ex. `http://localhost:4502`

L’identifiant `urn:adobe:aue:system` représente la connexion à l’éditeur universel d’Adobe.

Les `data-aue-resource` utilisent le préfixe `urn` pour raccourcir l’identifiant.

```html
data-aue-resource="urn:<referenceName>:<resource>"
```

* `<referenceName>` : il s’agit de la référence nommée mentionnée dans la balise `<meta>`. Par ex. `aemconnection`
* `<resource>` : il s’agit d’un pointeur vers la ressource du système cible. Par ex., un chemin de contenu AEM tel que `/content/page/jcr:content`

>[!TIP]
>
>Consultez le document [Attributs et types](attributes-types.md) pour plus d’informations sur les attributs et les types de données requis par l’éditeur universel.

### Exemple de connexion {#example}

```html
<meta name="urn:adobe:aue:system:<referenceName>" content="<protocol>:<url>">

<html>
<head>
    <meta name="urn:adobe:aue:system:aemconnection" content="aem:https://localhost:4502">
    <meta name="urn:adobe:aue:system:fcsconnection" content="fcs:https://example.franklin.adobe.com/345fcdd">
</head>
<body>
        <aside>
          <ul data-aue-resource="urn:aemconnection:/content/example/list" data-aue-type="container">
            <li data-aue-resource="urn:aemconnection:/content/example/listitem" data-aue-type="component">
              <p data-aue-prop="name" data-aue-type="text">Jane Doe</p>
              <p data-aue-prop="title" data-aue-type="text">Journalist</p>
              <img data-aue-prop="avatar" src="https://www.adobe.com/content/dam/cc/icons/Adobe_Corporate_Horizontal_Red_HEX.svg" data-aue-type="image" alt="avatar"/>
            </li>

...

            <li data-aue-resource="urn:fcsconnection:/documents/mytext" data-aue-type="component">
              <p data-aue-prop="name" data-aue-type="text">John Smith</p>
              <p data-aue-resource="urn:aemconnection:/content/example/another-source" data-aue-prop="title" data-aue-type="text">Photographer</p>
              <img data-aue-prop="avatar" src="https://www.adobe.com/content/dam/cc/icons/Adobe_Corporate_Horizontal_Red_HEX.svg" data-aue-type="image" alt="avatar"/>
            </li>
          </ul>
        </aside>
</body>
</html>
```

### Paramètres de configuration {#configuration-settings}

Vous pouvez utiliser le préfixe `config` dans votre URN de connexion pour définir le service et les points d’entrée d’extension, si nécessaire.

Si vous souhaitez ne pas utiliser le service d’éditeur universel, qui est hébergé par Adobe, mais votre propre version hébergée, vous pouvez le définir dans une balise meta . Pour remplacer le point d’entrée de service par défaut fourni par l’éditeur universel, définissez votre propre point d’entrée de service :

* Nom du méta-élément - `urn:adobe:aue:config:service`
* Méta-contenu - `content="https://adobe.com"` (exemple)

```html
<meta name="urn:adobe:aue:config:service" content="<url>">
```

Si vous souhaitez uniquement activer certaines extensions pour une page, vous pouvez le définir dans une balise meta. Pour récupérer des extensions, définissez les points d’entrée d’extension :

* Méta-nom : `urn:adobe:aue:config:extensions`
* Métcontenu : `content="https://adobe.com,https://anotherone.com,https://onemore.com"` (exemple)

```html
<meta name="urn:adobe:aue:config:extensions" content="<url>,<url>,<url>">
```

## Définissez pour quels chemins d’accès au contenu ou `sling:resourceType` l’éditeur universel doit être ouvert. (Facultatif) {#content-paths}

Si vous disposez déjà d’un projet AEM utilisant [l’éditeur de page](/help/sites-cloud/authoring/page-editor/introduction.md), lorsque les auteurs de contenu modifient des pages, les pages s’ouvrent automatiquement avec l’éditeur de page. Vous pouvez définir l’éditeur qu’AEM doit ouvrir en fonction des chemins d’accès au contenu ou du `sling:resourceType`, ce qui rend l’expérience transparente pour vos auteurs, quel que soit l’éditeur requis pour le contenu sélectionné.

1. Ouvrez Configuration Manager.

   `http://<host>:<port>/system/console/configMgr`

1. Recherchez **Service d’URL de l’éditeur universel** dans la liste, puis cliquez sur **Modifier les valeurs de configuration**.

1. Définissez pour quels chemins d’accès au contenu ou `sling:resourceType` l’éditeur universel doit être ouvert.

   * Dans le champ **Mappage d’ouverture de l’éditeur universel** indiquez les chemins d’accès pour lesquels l’éditeur universel est ouvert.
   * Dans le champ **Sling:resourceTypes qui doit être ouvert par l’éditeur universel**, fournissez une liste de ressources ouvertes directement par l’éditeur universel.

1. Cliquez sur **Enregistrer**.

1. Vérifiez votre [configuration de l’externaliseur](/help/implementing/developing/tools/externalizer.md) et assurez-vous au minimum que les environnements local, de création et de publication sont définis comme dans l’exemple suivant.

   ```text
   "local $[env:AEM_EXTERNALIZER_LOCAL;default=http://localhost:4502]",
   "author $[env:AEM_EXTERNALIZER_AUTHOR;default=http://localhost:4502]",
   "publish $[env:AEM_EXTERNALIZER_PUBLISH;default=http://localhost:4503]"
   ```

Une fois ces étapes de configuration terminées, AEM ouvre l’éditeur universel pour les pages dans l’ordre suivant.

1. AEM vérifie les mappages sous `Universal Editor Opening Mapping` et si le contenu se trouve sous l’un des chemins définis à cet endroit, l’éditeur universel s’ouvre pour lui.
1. Pour le contenu ne se trouvant pas sous les chemins définis dans `Universal Editor Opening Mapping`, AEM vérifie si le `resourceType` du contenu correspond à ceux définis dans **Sling:resourceTypes qui doivent être ouverts par l’éditeur universel** et si le contenu correspond à l’un de ces types, l’éditeur universel est ouvert pour lui à l’`${author}${path}.html`.
1. Sinon, AEM ouvre l’éditeur de page.

Les variables suivantes sont disponibles pour définir vos mappages dans le champ **Universal Editor Opening Mapping**.

* `path` : chemin d’accès au contenu de la ressource à ouvrir
* `localhost` : entrée du service Externalizer pour les `localhost` sans schéma, par exemple `localhost:4502`
* `author` : entrée du service Externalizer pour l’auteur sans schéma, par exemple `localhost:4502`
* `publish` : entrée du service Externalizer pour la publication sans schéma, par exemple `localhost:4503`
* `preview` : entrée du service Externalizer pour la prévisualisation sans schéma, par exemple `localhost:4504`
* `env` : `prod`, `stage`, `dev` en fonction des modes d’exécution Sling définis
* `token` : jeton de requête requis pour le `QueryTokenAuthenticationHandler`

### Exemples de mappages {#example-mappings}

* Ouvrez toutes les pages sous `/content/foo` dans l’auteur AEM :

   * `/content/foo:${author}${path}.html?login-token=${token}`
   * Cela entraîne l’ouverture de `https://localhost:4502/content/foo/x.html?login-token=<token>`

* Ouvrez toutes les pages sous `/content/bar` sur un serveur NextJS distant, en fournissant toutes les variables comme informations :

   * `/content/bar:nextjs.server${path}?env=${env}&author=https://${author}&publish=https://${publish}&login-token=${token}`
   * Cela entraîne l’ouverture de `https://nextjs.server/content/bar/x?env=prod&author=https://localhost:4502&publish=https://localhost:4503&login-token=<token>`

## Vous pouvez désormais utiliser l’éditeur universel. {#youre-ready}

Votre application est désormais instrumentée pour utiliser l’éditeur universel

Reportez-vous à [Création de contenu avec l’éditeur universel](/help/sites-cloud/authoring/universal-editor/authoring.md) et découvrez à quel point il est facile et intuitif pour les auteurs et autrices de créer du contenu à l’aide de l’éditeur universel.

{{ue-headless-auth}}

## Ressources supplémentaires {#additional-resources}

Pour en savoir plus sur l’éditeur universel, consultez ces documents.

* [Présentation de l’éditeur universel](introduction.md) - Découvrez comment l’éditeur universel permet de modifier n’importe quel aspect d’un contenu dans n’importe quelle implémentation afin de fournir des expériences exceptionnelles, d’augmenter la vitesse du contenu et d’offrir une expérience de développement à la pointe de la technologie.
* [Création de contenu avec l’éditeur universel](/help/sites-cloud/authoring/universal-editor/authoring.md) - Découvrez à quel point il est facile et intuitif pour les créateurs et les créatrices de contenu de créer du contenu à l’aide de l’éditeur universel.
* [Publication de contenu avec l’éditeur universel](/help/implementing/universal-editor/publishing.md) - Découvrez comment l’éditeur universel publie du contenu et comment vos applications peuvent gérer le contenu publié.
* [Architecture de l’éditeur universel](architecture.md) - Découvrez l’architecture de l’éditeur universel et le flux de données entre ses services et calques.
* [Attributs et types](attributes-types.md) - Découvrez les attributs et les types de données requis par l’éditeur universel.
* [Authentification de l’éditeur universel](authentication.md) - Découvrez comment l’éditeur universel s’authentifie.

