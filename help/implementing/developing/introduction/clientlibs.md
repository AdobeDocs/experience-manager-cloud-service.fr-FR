---
title: Utilisation des bibliothèques côté client sur AEM en tant que Cloud Service
description: aem fournit des dossiers de bibliothèque côté client, qui vous permettent de stocker votre code côté client (clientlibs) dans le référentiel, de l'organiser en catégories et de définir quand et comment chaque catégorie de code doit être diffusée au client.
translation-type: tm+mt
source-git-commit: d4c031e17c0c83e44b687474502252c89ed37922
workflow-type: tm+mt
source-wordcount: '2571'
ht-degree: 36%

---


# Utilisation des bibliothèques côté client sur AEM en tant que Cloud Service {#using-client-side-libraries}

Les expériences numériques reposent en grande partie sur un traitement côté client piloté par du code JavaScript et CSS complexe. aem bibliothèques côté client (clientlibs) vous permettent d’organiser et de stocker centralement ces bibliothèques côté client dans le référentiel. Associé au processus de génération [frontale dans l&#39;archétype de projet AEM,](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/uifrontend.html) la gestion de votre code frontal pour votre projet AEM devient simple.

Les avantages de l’utilisation de clientlibs dans AEM sont les suivants :

* Le code client est stocké dans le référentiel comme tout autre code et contenu d’application.
* Les bibliothèques clientes dans AEM peuvent agrégat toutes les feuilles CSS et JS dans un seul fichier.
* Exposer les clientlibs via un chemin accessible via le [répartiteur](/help/implementing/dispatcher/disp-overview.md)
* Permet la réécriture des chemins d’accès pour les fichiers ou images référencés

Les bibliothèques clientes sont la solution intégrée pour la diffusion de CSS et de JavaScript à partir d’AEM.

>[!TIP]
>
>Les développeurs de premier plan qui créent des feuilles de style CSS et Javascript pour AEM projets devraient également se familiariser avec l&#39;archétype de projet [AEM et son processus de création frontale automatisé.](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/uifrontend.html)

## Que sont les bibliothèques côté client {#what-are-clientlibs}

Les sites requièrent du code JavaScript et CSS, ainsi que des ressources statiques telles que des icônes et des polices Web, pour être traités côté client. Une bibliothèque cliente est un mécanisme AEM de référence (par catégorie si nécessaire) et d&#39;affectation de ces ressources.

aem collecte les fichiers CSS et Javascript du site dans un seul fichier, à un emplacement central, afin de s’assurer qu’une seule copie de toute ressource est incluse dans la sortie HTML. Cela optimise l&#39;efficacité de la diffusion et permet à ces ressources d&#39;être conservées de façon centralisée dans le référentiel par le biais d&#39;un proxy, en gardant l&#39;accès sécurisé.

## Développement frontal pour l&#39;AEM en tant que Cloud Service {#fed-for-aemaacs}

Tous les actifs JavaScript, CSS et autres actifs frontaux doivent être conservés dans le module [ui.frontend de l’archétype de projet AEM.](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/uifrontend.html) La flexibilité de l&#39;archétype vous permet d&#39;utiliser vos outils Web modernes de choix pour créer et gérer ces ressources.

L’archétype peut ensuite compiler les ressources dans des fichiers CSS et JS uniques, en les incorporant automatiquement dans un `cq:clientLibraryFolder` référentiel.

## Structure du dossier de bibliothèque côté client {#clientlib-folders}

Un dossier de bibliothèques côté client est un nœud de référentiel de type `cq:ClientLibraryFolder`. Its definition in [CND notation](https://jackrabbit.apache.org/node-type-notation.html) is

```text
[cq:ClientLibraryFolder] > sling:Folder
  - dependencies (string) multiple
  - categories (string) multiple
  - embed (string) multiple
  - channels (string) multiple
```

* `cq:ClientLibraryFolder` peuvent être placés n’importe où dans la `/apps` sous-arborescence du référentiel.
* Utilisez la propriété `categories` du nœud pour identifier les catégories de bibliothèque auxquelles il appartient.

Each `cq:ClientLibraryFolder` is populated with a set of JS and/or CSS files, along with a few supporting files (see below). Important properties of the `cq:ClientLibraryFolder` are configured as follows:

* `allowProxy`: Étant donné que tous les clientlibs doivent être stockés sous `apps`, cette propriété permet d’accéder aux bibliothèques clientes par le biais d’une servlet proxy. See [Locating a Client Library Folder and Using the Proxy Client Libraries Servlet](#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet) below.
* `categories`: Identifie les catégories dans lesquelles le jeu de fichiers JS et/ou CSS se trouve au cours de cet `cq:ClientLibraryFolder` automne. La propriété `categories` comportant plusieurs valeurs, elle permet à un dossier de bibliothèques d’appartenir à plusieurs catégories (voir ci-dessous pour savoir en quoi cela peut se révéler utile).

Si le dossier de bibliothèque client contient un ou plusieurs fichiers source qui, au moment de l’exécution, sont fusionnés en un seul fichier JS et/ou CSS. The name of the generated file is the node name with either the `.js` or `.css` file name extension. For example, the library node named `cq.jquery` results in the generated file named `cq.jquery.js` or `cq.jquery.css`.

Les dossiers de bibliothèques clientes contiennent les éléments suivants :

* Fichiers source JS et/ou CSS
* Ressources statiques prenant en charge les styles CSS, telles que les icônes, les polices Web, etc.
* One `js.txt` file and/or one `css.txt` file which identify the source files to merge in the generated JS and/or CSS files

![Architecture de la bibliothèque cliente](assets/clientlib-architecture.drawio.png)

## Création de dossiers de bibliothèque côté client {#creating-clientlib-folders}

Les bibliothèques clientes doivent être situées sous `/apps`. Ceci afin de mieux isoler le code du contenu et de la configuration.

In order for the client libraries under `/apps` to be accessible, a proxy servelt is used. The ACLs are still enforced on the client library folder, but the servlet allows for the content to be read via `/etc.clientlibs/` if the `allowProxy` property is set to `true`.

1. Open CRXDE Lite in a web browser (`https://<host>:<port>/crx/de`).
1. Select the `/apps` folder and click **Create > Create Node**.
1. Enter a name for the library folder, and in the **Type** list select `cq:ClientLibraryFolder`. Cliquez sur **OK**, puis sur **Enregistrer tout**.
1. Pour spécifier la ou les catégories auxquelles appartient la bibliothèque, sélectionnez le nœud `cq:ClientLibraryFolder`, ajoutez la propriété suivante, puis cliquez sur **Enregistrer tout** :
   * Nom (name) : `categories`
   * Type : String
   * Valeur : nom de la catégorie
   * Multi : Sélectionné
1. Pour que les bibliothèques clientes soient accessibles par proxy sous `/etc.clientlibs`, sélectionnez le `cq:ClientLibraryFolder` noeud, ajoutez la propriété suivante, puis cliquez sur **Enregistrer tout**:
   * Nom (name) : `allowProxy`
   * Type : booléen
   * Valeur : `true`
1. Si vous devez gérer des ressources statiques, créez un sous-dossier nommé `resources` sous le dossier de bibliothèque client.
   * Si vous stockez des ressources statiques sous le dossier `resources`, elles ne peuvent pas être référencées sur une instance de publication.
1. Ajoutez les fichiers source dans le dossier de bibliothèque.
   * Cela est généralement effectué par le processus de création frontale de l&#39;archétype de projet [AEM.](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/uifrontend.html)
   * Si vous le souhaitez, vous pouvez organiser les fichiers source dans des sous-dossiers.
1. Sélectionnez le dossier de bibliothèques clientes et cliquez ensuite sur **Créer > Créer un fichier**.
1. Dans la zone du nom de fichier, saisissez l’un des noms suivants et cliquez ensuite sur OK :
   * **`js.txt`:** Utilisez ce nom de fichier pour générer un fichier JavaScript.
   * **`css.txt`:** Utilisez ce nom de fichier pour générer une feuille de style en cascade.
1. Ouvrez le fichier et saisissez le texte suivant pour identifier la racine du chemin d’accès des fichiers sources :
   * `#base=*[root]*`
   * Replace `[root]` with the path to the folder that contains the source files, relative to the TXT file. Utilisez, par exemple, le texte suivant lorsque les fichiers sources se trouvent dans le même dossier que le fichier TXT :
      * `#base=.`
   * Le code suivant définit la racine en tant que dossier nommé mobile sous le nœud `cq:ClientLibraryFolder` :
      * `#base=mobile`
1. On the lines below `#base=[root]`, type the paths of the source files relative to the root. Placez chaque nom de fichier sur une ligne distincte.
1. Cliquez sur **Enregistrer tout**.

## Gestion des bibliothèques côté client {#serving-clientlibs}

Une fois le dossier de bibliothèque client [configuré comme requis,](#creating-clientlib-folders) vos bibliothèques clientes peuvent être demandées par proxy. Par exemple :

* You have a clientlib in `/apps/myproject/clientlibs/foo`
* You have a static image in `/apps/myprojects/clientlibs/foo/resources/icon.png`

La `allowProxy` propriété vous permet de demander :

* clientlib via j`/etc.clientlibs/myprojects/clientlibs/foo.js`
* L’image statique via `/etc.clientlibs/myprojects/clientlibs/foo/resources/icon.png`

### Chargement des bibliothèques clientes via HTL {#loading-via-htl}

Une fois que vos bibliothèques clientes sont stockées et gérées dans leur dossier de bibliothèque cliente, elles peuvent être accessibles via HTL.

Client libraries are loaded through a helper template provided by AEM, which can be accessed through `data-sly-use`. Helper templates are available in this file, which can be called through `data-sly-call`.

Chaque modèle d’assistance exige une option `categories` pour référencer les bibliothèques client souhaitées. Cette option peut être un tableau de valeurs de chaîne ou une chaîne contenant une liste de valeurs séparées par des virgules.

[Pour plus d’informations sur le chargement de clientlibs via HTL, consultez la documentation](https://docs.adobe.com/content/help/en/experience-manager-htl/using/getting-started/getting-started.html#loading-client-libraries) HTML.

<!--
### Setting Cache Timestamps {#setting-cache-timestamps}

This is possible. Still need detail.
-->

## Bibliothèques clientes sur l’auteur par rapport à la publication {#clientlibs-author-publish}

La plupart des clientlibs seront requis sur l’instance de publication AEM. En d&#39;autres termes, la plupart des clientlibs ont pour objectif de produire l&#39;expérience de l&#39;utilisateur final du contenu. Pour les bibliothèques clientes sur les instances de publication, les outils [de création](#fed-for-aemaacs) frontaux peuvent être utilisés et déployés via des dossiers de bibliothèque [client, comme décrit ci-dessus.](#creating-clientlib-folders)

Cependant, il peut arriver que des bibliothèques clientes soient nécessaires pour personnaliser l’expérience de création. Par exemple, la personnalisation d’une boîte de dialogue peut nécessiter le déploiement de petits fragments de CSS ou de JS sur l’instance de création AEM.

### Gestion des bibliothèques clientes sur l’auteur {#clientlibs-on-author}

Si vous devez utiliser les bibliothèques clientes sur l’auteur, vous pouvez créer vos bibliothèques clientes en utilisant `/apps` les mêmes méthodes que pour la publication, mais vous pouvez les écrire directement sous `/apps/.../clientlibs/foo` la page au lieu de créer un projet entier pour le gérer.

Vous pouvez ensuite &quot;relier&quot; les fichiers JS de création en ajoutant vos bibliothèques clientes à une catégorie de bibliothèque cliente prête à l’emploi.

## Outils de débogage {#debugging-tools}

AEM s’accompagne de plusieurs outils pour déboguer et tester des dossiers de bibliothèques clientes.

### Détection de bibliothèques clientes {#discover-client-libraries}

The `/libs/cq/granite/components/dumplibs/dumplibs` component generates a page of information about all client library folders on the system. The `/libs/granite/ui/content/dumplibs` node has the component as a resource type. Pour ouvrir la page, utilisez l’URL suivante (en modifiant l’hôte et le port selon les besoins) :

`https://<host>:<port>/libs/granite/ui/content/dumplibs.test.html`

Les informations affichées sont le chemin d’accès à la bibliothèque et son type (CSS ou JS), ainsi que les valeurs des attributs de bibliothèque, tels que categories et dependencies. Les tableaux suivants présentent les bibliothèques dans chaque catégorie et canal.

### Affichage de la sortie générée {#see-generated-output}

The `dumplibs` component includes a test selector that displays the source code that is generated for `ui:includeClientLib` tags. La page comprend du code pour différentes combinaisons d’attributs js, css et thématiques.

1. Appliquez l’une des méthodes suivantes pour ouvrir la page de sortie de test :
   * From the `dumplibs.html` page, click the link in the **Click here for output testing** text.
   * Ouvrez l’URL suivante dans votre navigateur Web (utilisez un hôte et un port différents selon les besoins) :
      * `http://<host>:<port>/libs/granite/ui/content/dumplibs.html`
   * La page par défaut affiche le résultat pour les balises ne comportant aucune valeur pour l’attribut categories.
1. To see the output for a category, type the value of the client library&#39;s `categories` property and click **Submit Query**.

## Autres fonctionnalités du dossier de bibliothèque cliente {#additional-features}

Un certain nombre d’autres fonctionnalités sont prises en charge par les dossiers de bibliothèque client dans AEM. Toutefois, ces mesures ne sont pas requises à l&#39;AEM en tant que Cloud Service et, par conséquent, leur utilisation est découragée. Ils sont répertoriés ici pour être complets.

>[!WARNING]
>
>Ces fonctionnalités supplémentaires des dossiers de bibliothèque client ne sont pas requises en tant que Cloud Service et leur utilisation est donc déconseillée. Ils sont répertoriés ici pour être complets.

### Adobe Granite HTML LIbrary Manager {#html-library-manager}

D’autres paramètres de bibliothèque client peuvent être contrôlés par le biais du panneau Gestionnaire **de bibliothèque HTML Granite** Adobe de la console système (à `https://<host>:<port>/system/console/configMgr`).

### Propriétés supplémentaires du dossier {#additional-folder-properties}

Les autres propriétés de dossiers permettent de contrôler les dépendances et les incorporations, mais ne sont généralement plus nécessaires et leur utilisation est déconseillée :

* `dependencies` : il s’agit d’une liste d’autres catégories de bibliothèques clientes dont dépend ce dossier de catégories. For example, given two `cq:ClientLibraryFolder` nodes `F` and `G`, if a file in `F` requires another file in `G` in order to function properly, then at least one of the `categories` of `G` should be among the `dependencies` of `F`.
* `embed`: Utilisé pour incorporer du code provenant d’autres bibliothèques. If node `F` embeds nodes `G` and `H`, the resulting HTML will be a concatenation of content from nodes `G` and `H`.

### Liaison vers des dépendances {#linking-to-dependencies}

Lorsque le code de votre dossier de bibliothèques clientes fait référence à d’autres bibliothèques, identifiez ces dernières en tant que dépendances. The `ui:includeClientLib` tag that references your client library folder causes the HTML code to include a link to your generated library file as well as the dependencies.

The dependencies must be another `cq:ClientLibraryFolder`. To identify dependencies, add a property to your `cq:ClientLibraryFolder` node with the following attributes:

* **Nom** : dependencies
* **Type :** Chaîne[]
* **Valeurs** : la valeur de la propriété categories du nœud cq:ClientLibraryFolder dont dépend le dossier de bibliothèques en cours.

For example, the `/etc/clientlibs/myclientlibs/publicmain` has a dependency on the `cq.jquery` library. La page qui référence la bibliothèque cliente principale génère du code HTML qui inclut le code suivant :

```xml
<script src="/etc/clientlibs/foundation/cq.jquery.js" type="text/javascript">
<script src="/etc/clientlibs/mylibs/publicmain.js" type="text/javascript">
```

### Incorporation de code d’autres bibliothèques {#embedding-code-from-other-libraries}

Vous pouvez incorporer du code d’une bibliothèque cliente dans une autre bibliothèque cliente. Lors de l’exécution, les fichiers JS et CSS générés de la bibliothèque d’intégration contiennent le code de la bibliothèque incorporée.

Incorporer du code s’avère utile pour fournir l’accès aux bibliothèques qui sont stockées dans des zones sécurisées du référentiel.

#### Dossiers de bibliothèques clientes spécifiques à une application {#app-specific-client-library-folders}

Il est conseillé de conserver tous les fichiers associés à une application dans leur dossier d’application sous `/app`. It is also a best practice to deny access for web site visitors to the `/app` folder. To satisfy both best practices, create a client library folder below the `/etc` folder that embeds the client library that is below `/app`.

Utilisez la propriété catégories pour identifier le dossier de bibliothèque client à incorporer. Pour incorporer la bibliothèque, ajoutez une propriété au nœud `cq:ClientLibraryFolder` d’intégration à l’aide des attributs de propriété suivants :

* **Nom :** embed
* **Type :** Chaîne[]
* **Valeur :** Valeur de la propriété catégories du `cq:ClientLibraryFolder` noeud à incorporer.

#### Utilisation de l’incorporation pour réduire les requêtes {#using-embedding-to-minimize-requests}

Dans certains cas, il se peut que le code HTML final généré pour une page standard par votre instance de publication comporte un nombre relativement important d’ `<script>` éléments.

Dans ce cas, il peut être utile de combiner tout le code de bibliothèque cliente requis dans un seul fichier afin de réduire le nombre de requêtes aller-retour lors du chargement de la page. Pour ce faire, vous pouvez `embed`incorporer les bibliothèques requises dans la bibliothèque cliente spécifique à l’application à l’aide de la propriété du nœud `cq:ClientLibraryFolder`.

#### Chemins d’accès dans les fichiers CSS {#paths-in-css-files}

Lorsque vous incorporez des fichiers CSS, le code CSS généré utilise des chemins d’accès aux ressources qui sont relatifs à la bibliothèque d’intégration. For example, the publicly-accessible library `/etc/client/libraries/myclientlibs/publicmain` embeds the `/apps/myapp/clientlib` client library:

Le fichier `main.css` contient le style suivant :

```javascript
body {
  padding: 0;
  margin: 0;
  background: url(images/bg-full.jpg) no-repeat center top;
  width: 100%;
}
```

Le fichier CSS généré par le nœud `publicmain` contient le style suivant, en utilisant l’URL de l’image d’origine :

```javascript
body {
  padding: 0;
  margin: 0;
  background: url(../../../apps/myapp/clientlib/styles/images/bg-full.jpg) no-repeat center top;
  width: 100%;
}
```

#### Voir Fichiers incorporés dans une sortie HTML {#see-embedded-files}

Pour remonter à l’origine du code incorporé, ou vous assurer que les bibliothèques clientes incorporées produisent les résultats escomptés, vous pouvez afficher les noms des fichiers incorporés au moment de l’exécution. Pour afficher les noms de fichiers, ajoutez le paramètre `debugClientLibs=true` à l’URL de votre page web. The library that is generated contains `@import` statements instead of the embedded code.

In the example in the previous [Embedding Code From Other Libraries](#embedding-code-from-other-libraries) section, the `/etc/client/libraries/myclientlibs/publicmain` client library folder embeds the `/apps/myapp/clientlib` client library folder. L’ajout du paramètre à la page web génère le lien suivant dans le code source de la page web :

```xml
<link rel="stylesheet" href="/etc/clientlibs/mycientlibs/publicmain.css">
```

L’ouverture du fichier `publicmain.css` fait apparaître le code suivant :

```javascript
@import url("/apps/myapp/clientlib/styles/main.css");
```

1. Dans la barre d’adresse de votre navigateur web, ajoutez le texte suivant à l’URL de votre code HTML :
   * `?debugClientLibs=true`
1. Au chargement de la page, affichez sa source.
1. Cliquez sur le lien fourni comme href de l’élément link pour ouvrir le fichier et afficher le code source.

### Utilisation de préprocesseurs {#using-preprocessors}

AEM allows for pluggable preprocessors and ships with support for [YUI Compressor](https://github.com/yui/yuicompressor#yui-compressor---the-yahoo-javascript-and-css-compressor) for CSS and JavaScript and [Google Closure Compiler (GCC)](https://developers.google.com/closure/compiler/) for JavaScript with YUI set as AEM&#39;s default preprocessor.

Les préprocesseurs enfichables garantissent une certaine souplesse d’utilisation :

* Définition de ScriptProcessors pouvant traiter des sources de script
* Processeurs configurables avec des options
* Processeurs pouvant être utilisés pour la minification, mais aussi pour des cas de figure des non minifiés
* Bibliothèque cliente (clientlib) pouvant définir le processeur à utiliser

>[!NOTE]
>
>Par défaut, AEM utilise YUI Compressor. Pour connaître la liste des problèmes connus, consultez la [documentation GitHub de YUI Compressor](https://github.com/yui/yuicompressor/issues). Basculer vers le compresseur GCC pour des bibliothèques clientes spécifiques permet de résoudre certains problèmes observés lors de l’utilisation de YUI.

>[!CAUTION]
>
>Ne placez pas de bibliothèque ayant fait l’objet d’une minification dans une bibliothèque cliente. Fournissez plutôt la bibliothèque brute et, si une minification est requise, utilisez les options des préprocesseurs.

#### Utilisation {#usage}

Vous pouvez choisir de configurer les préprocesseurs par bibliothèque cliente ou à l’échelle du système.

* Add the multivalue properties `cssProcessor` and `jsProcessor` on the clientlibrary node
* Vous pouvez également définir la configuration par défaut du système par le biais de la configuration OSGi du **Gestionnaire de bibliothèques HTML**.

Une configuration de préprocesseur sur le noeud clientlib prévaut sur la configuration OSGI.

#### Format et exemples {#format-and-examples}

##### Format {#format}

```javascript
config:= mode ":" processorName options*;
mode:= "default" | "min";
processorName := "none" | <name>;
options := ";" option;
option := name "=" value;
```

##### YUI Compressor pour la minification CSS et GCC pour JS {#yui-compressor-for-css-minification-and-gcc-for-js}

```javascript
cssProcessor: ["default:none", "min:yui"]
jsProcessor: ["default:none", "min:gcc;compilationLevel=advanced"]
```

##### Typescript pour le prétraitement, puis GCC pour la minification et l’obfuscation {#typescript-to-preprocess-and-then-gcc-to-minify-and-obfuscate}

```javascript
jsProcessor: [
   "default:typescript",
   "min:typescript",
   "min:gcc;obfuscate=true"
]
```

##### Options GCC supplémentaires {#additional-gcc-options}

```javascript
failOnWarning (defaults to "false")
languageIn (defaults to "ECMASCRIPT5")
languageOut (defaults to "ECMASCRIPT5")
compilationLevel (defaults to "simple") (can be "whitespace", "simple", "advanced")
```

Pour plus d’informations sur les options GCC, consultez la [documentation de GCC](https://developers.google.com/closure/compiler/docs/compilation_levels).

#### Définition de l’outil de minification par défaut du système {#set-system-default-minifier}

YUI est défini comme outil de minification par défaut dans AEM. Pour le définir sur GCC, procédez comme suit.

1. Go to Apache Felix Config Manager at (`http://<host>:<portY/system/console/configMgr`)
1. Find and edit the **Adobe Granite HTML Library Manager**.
1. Activez l’option **Minifier** (le cas échéant).
1. Set the value **JS Processor Default Configs** to `min:gcc`.
   * Options can be passed if separated with a semicolon e.g. `min:gcc;obfuscate=true`.
1. Cliquez sur **Enregistrer** pour enregistrer les modifications.
