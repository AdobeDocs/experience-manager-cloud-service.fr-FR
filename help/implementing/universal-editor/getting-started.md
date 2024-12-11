---
title: Prise en main de l’éditeur universel dans AEM
description: Découvrez comment accéder à l’éditeur universel et comment commencer à instrumenter votre première application AEM pour l’utiliser.
exl-id: 9091a29e-2deb-4de7-97ea-53ad29c7c44d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 8357caf2b0d396f6a1bd7b6160d6b48d8d6c026c
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 62%

---


# Prise en main de l’éditeur universel dans AEM {#getting-started}

Découvrez comment accéder à l’éditeur universel et comment commencer à instrumenter votre première application AEM pour l’utiliser.

>[!TIP]
>
>Si vous préférez plonger directement dans un exemple, vous pouvez consulter la section [Exemple d’application de l’éditeur universel sur GitHub.](https://github.com/adobe/universal-editor-sample-editable-app)

Bien qu’Universal Editor puisse modifier du contenu à partir de n’importe quelle source, ce document utilise une application AEM comme exemple. Ce document vous guidera tout au fil de ces étapes.

## Instrumenter la page {#instrument-page}

Universal Editor a besoin d’une bibliothèque JavaScript pour effectuer le rendu et modifier la page dans l’éditeur.

En outre, le service Universal Editor requiert un [ nom de ressource uniforme (URN)](https://fr.wikipedia.org/wiki/Uniform_Resource_Name) pour identifier et utiliser le système principal approprié pour le contenu de l’application en cours de modification. Par conséquent, un schéma URN est nécessaire pour mapper le contenu aux ressources de contenu.

### Inclusion de la bibliothèque CORS de l’éditeur universel {#cors-library}

Pour que l’éditeur universel puisse se connecter à votre application, celle-ci doit inclure la bibliothèque CORS de l’éditeur universel. Ajoutez le script suivant à votre application.

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
   * `config` - Pour [ la définition des paramètres de configuration facultatifs](#configuration-settings)
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

Vous pouvez utiliser le préfixe `config` dans l’URL de votre connexion pour définir les points d’entrée de service et d’extension si nécessaire.

Si vous ne souhaitez pas utiliser le service Universal Editor, qui est hébergé par Adobe, mais votre propre version hébergée, vous pouvez le définir dans une balise META. Pour remplacer le point d’entrée de service par défaut fourni par Universal Editor, définissez votre propre point d’entrée de service :

* Nom de métadonnées - `urn:adobe:aue:config:service`
* Métadonnées - `content="https://adobe.com"` (exemple)

```html
<meta name="urn:adobe:aue:config:service" content="<url>">
```

Si vous souhaitez uniquement que certaines extensions soient activées pour une page, vous pouvez le définir dans une balise meta . Pour récupérer les extensions, définissez les points de fin d’extension :

* Nom méta : `urn:adobe:aue:config:extensions`
* Métadonnées : `content="https://adobe.com,https://anotherone.com,https://onemore.com"` (exemple)

```html
<meta name="urn:adobe:aue:config:extensions" content="<url>,<url>,<url>">
```

## Vous pouvez désormais utiliser l’éditeur universel. {#youre-ready}

Votre application est désormais instrumentée pour utiliser l’éditeur universel

Reportez-vous à [Création de contenu avec l’éditeur universel](/help/sites-cloud/authoring/universal-editor/authoring.md) et découvrez à quel point il est facile et intuitif pour les auteurs et autrices de créer du contenu à l’aide de l’éditeur universel.

## Ressources supplémentaires {#additional-resources}

Pour en savoir plus sur l’éditeur universel, consultez ces documents.

* [Présentation de l’éditeur universel](introduction.md) - Découvrez comment l’éditeur universel permet de modifier n’importe quel aspect d’un contenu dans n’importe quelle implémentation afin de fournir des expériences exceptionnelles, d’augmenter la vitesse du contenu et d’offrir une expérience de développement à la pointe de la technologie.
* [Création de contenu avec l’éditeur universel](/help/sites-cloud/authoring/universal-editor/authoring.md) - Découvrez à quel point il est facile et intuitif pour les créateurs et les créatrices de contenu de créer du contenu à l’aide de l’éditeur universel.
* [Publication de contenu avec l’éditeur universel](/help/sites-cloud/authoring/universal-editor/publishing.md) - Découvrez comment l’éditeur universel publie du contenu et comment vos applications peuvent gérer le contenu publié.
* [Architecture de l’éditeur universel](architecture.md) - Découvrez l’architecture de l’éditeur universel et le flux de données entre ses services et calques.
* [Attributs et types](attributes-types.md) - Découvrez les attributs et les types de données requis par l’éditeur universel.
* [Authentification de l’éditeur universel](authentication.md) - Découvrez comment l’éditeur universel s’authentifie.

