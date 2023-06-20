---
title: Style des composants principaux Adobe Experience Manager CIF
description: Découvrez comment mettre en forme les composants principaux Adobe Experience Manager (AEM) CIF. Le tutoriel explique comment les bibliothèques côté client (clientlibs) sont utilisées pour déployer et gérer des fichiers CSS et JavaScript pour une mise en oeuvre d’AEM Commerce. Ce tutoriel explique également comment le module ui.frontend et un projet webpack sont intégrés au processus de génération de bout en bout.
sub-product: Commerce
topics: Development
version: Cloud Service
doc-type: tutorial
activity: develop
audience: developer
feature: Commerce Integration Framework
kt: 3456
thumbnail: 3456-style-cif.jpg
exl-id: 521c1bb8-7326-4ee8-aba3-f386727e2b34
source-git-commit: 5311ba7f001201fc94c73fa52bc7033716c1ba78
workflow-type: tm+mt
source-wordcount: '2536'
ht-degree: 61%

---

# Donner un style aux composants principaux AEM CIF {#style-aem-cif-core-components}

Le [projet CIF Venia](https://github.com/adobe/aem-cif-guides-venia) est une base de code de référence pour l’utilisation des [composants principaux CIF](https://github.com/adobe/aem-core-cif-components). Dans ce tutoriel, vous examinez le projet de référence Venia et comprenez comment les composants principaux CSS et JavaScript utilisés par AEM CIF sont organisés. Vous pouvez également créer un style à l’aide de CSS pour mettre à jour le style par défaut de la variable **Teaser de produit** composant.

>[!TIP]
>
> Utilisez l’[archétype de projet AEM](https://github.com/adobe/aem-project-archetype) pour démarrer votre propre implémentation commerciale.

## Ce que vous allez créer

Dans ce tutoriel, un nouveau style qui ressemble à une carte est mis en oeuvre pour le composant Teaser de produit. Ce que vous apprenez dans le tutoriel peut être appliqué à d’autres composants principaux CIF.

![Ce que vous allez créer](../assets/style-cif-component/what-you-will-build.png)

## Prérequis {#prerequisites}

Un environnement de développement local est nécessaire pour suivre ce tutoriel. Cet environnement comprend une instance d’AEM en cours d’exécution configurée et connectée à une instance Adobe Commerce. Examinez les exigences et les étapes de la [configuration d’un développement local avec le SDK AEM as a Cloud Service](../develop.md).

## Clonage du projet Venia {#clone-venia-project}

Vous allez cloner le [Projet Venia](https://github.com/adobe/aem-cif-guides-venia), puis remplacez les styles par défaut.

>[!NOTE]
>
> **N’hésitez pas à utiliser un projet existant** (basé sur l’archétype de projet AEM avec CIF inclus) et à ignorer cette section.

1. Exécutez la commande git suivante afin de pouvoir cloner le projet :

   ```shell
   $ git clone git@github.com:adobe/aem-cif-guides-venia.git
   ```

1. Créez et déployez le projet sur une instance locale d’AEM :

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

1. Ajoutez les configurations OSGi nécessaires pour connecter votre instance AEM à une instance Adobe Commerce ou ajoutez les configurations au projet nouvellement créé.

1. À ce stade, vous devriez disposer d’une version fonctionnelle d’un storefront connecté à une instance Adobe Commerce. Accédez à la page `US` > `Home` à l’adresse suivante : [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

   Vous devriez voir que le storefront utilise actuellement le thème Venia. En développant le menu principal du storefront, vous devriez voir différentes catégories indiquant que la connexion à Adobe Commerce fonctionne.

   ![Storefont configuré avec le thème Venia](../assets/style-cif-component/venia-store-configured.png)

## Bibliothèques client et module ui.frontend {#introduction-to-client-libraries}

Le code CSS et JavaScript responsable du rendu du thème/des styles du storefront est géré en AEM par un [bibliothèque cliente](/help/implementing/developing/introduction/clientlibs.md) ou &quot;clientlibs&quot; en court. Les bibliothèques clientes offrent un mécanisme permettant d’organiser le code CSS et JavaScript dans le code d’un projet, puis de le diffuser sur la page.

Des styles spécifiques à la marque peuvent être appliqués aux composants principaux CIF AEM en ajoutant et en remplaçant le CSS géré par ces bibliothèques clientes. Il est essentiel de comprendre comment les bibliothèques clientes sont structurées et incluses dans la page.

Le [ui.frontend](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uifrontend.html?lang=fr) est un [webpack](https://webpack.js.org/) pour gérer toutes les ressources front-end d’un projet. Ce webpack permet aux développeurs front-end d’utiliser un grand nombre de langues et de technologies, telles que [TypeScript](https://www.typescriptlang.org/), [Sass](https://sass-lang.com/), et bien plus encore.

Le `ui.frontend` module est également un module Maven et intégré au projet plus vaste à l’aide d’un module NPM le [aem-clientlib-generator](https://github.com/wcm-io-frontend/aem-clientlib-generator). Au cours d’une génération, `aem-clientlib-generator` copie les fichiers CSS et JavaScript compilés dans une bibliothèque cliente du module`ui.apps`.

![ui.frontend dans l’architecture ui.apps](../assets/style-cif-component/ui-frontend-architecture.png)

*Les fichiers CSS et JavaScript compilés sont copiés à partir du `ui.frontend` dans le module `ui.apps` module en tant que bibliothèque cliente lors d’une génération Maven*

## Mettre le style du teaser à jour {#ui-frontend-module}

Apportez ensuite une légère modification au style du teaser pour voir comment fonctionnent le module `ui.frontend` et les bibliothèques clientes. Utilisez l’[IDE de votre choix](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=fr#set-up-the-development-ide) pour importer le projet Venia. Les captures d’écran utilisées proviennent de l’[IDE Visual Studio Code](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=fr#microsoft-visual-studio-code).

1. Accédez au module **ui.frontend** et développez-le, puis développez la hiérarchie de dossiers comme suit : `ui.frontend/src/main/styles/commerce` :

   ![dossier du composant Commerce ui.frontend](../assets/style-cif-component/ui-frontend-commerce-folder.png)

   Notez qu’il existe plusieurs fichiers Sass (`.scss`) sous le dossier. Ces fichiers sont des styles spécifiques à Commerce pour chacun des composants Commerce.

1. Ouvrez le fichier `_productteaser.scss`.

1. Mettez la règle `.item__image` à jour et modifiez la règle de bordure :

   ```scss
   .item__image {
       border: #ea00ff 8px solid; /* <-- modify this rule */
       display: block;
       grid-area: main;
       height: auto;
       opacity: 1;
       transition-duration: 512ms;
       transition-property: opacity, visibility;
       transition-timing-function: ease-out;
       visibility: visible;
       width: 100%;
   }
   ```

   La règle ci-dessus doit ajouter une bordure rose en gras au composant Teaser de produit.

1. Ouvrez une nouvelle fenêtre de terminal et accédez au dossier `ui.frontend` :

   ```shell
   $ cd <project-location>/aem-cif-guides-venia/ui.frontend
   ```

1. Exécutez la commande Maven suivante :

   ```shell
   $ mvn clean install
   ...
   [INFO] ------------------------------------------------------------------------
   [INFO] BUILD SUCCESS
   [INFO] ------------------------------------------------------------------------
   [INFO] Total time:  29.497 s
   [INFO] Finished at: 2020-08-25T14:30:44-07:00
   [INFO] ------------------------------------------------------------------------
   ```

   Inspectez la sortie du terminal. Notez que la commande Maven a exécuté plusieurs scripts NPM, y compris `npm run build`. Le `npm run build` est définie dans la fonction `package.json` et compile le projet webpack et déclenche la génération de la bibliothèque cliente.

1. Inspectez le fichier `ui.frontend/dist/clientlib-site/site.css` :

   ![Fichier CSS du site compilé](../assets/style-cif-component/comiled-site-css.png)

   Le fichier constitue la version compilée et minimisée de tous les fichiers Sass du projet.

   >[!NOTE]
   >
   > Les fichiers de ce type sont ignorés du contrôle source, puisqu’ils doivent être générés pendant la création.

1. Inspectez le fichier `ui.frontend/clientlib.config.js`.

   ```js
   /* clientlib.config.js*/
   ...
   // Config for `aem-clientlib-generator`
   module.exports = {
       context: BUILD_DIR,
       clientLibRoot: CLIENTLIB_DIR,
       libs: [
           {
               ...libsBaseConfig,
               name: 'clientlib-site',
               categories: ['venia.site'],
               dependencies: ['venia.dependencies', 'aem-core-cif-react-components'],
               assets: {
   ...
   ```

   Ce fichier de configuration est destiné à [aem-clientlib-generator](https://github.com/wcm-io-frontend/aem-clientlib-generator) et détermine où et comment les fichiers CSS et JavaScript compilés sont transformés en bibliothèque cliente AEM.

1. Dans le `ui.apps` , inspectez le fichier : `ui.apps/src/main/content/jcr_root/apps/venia/clientlibs/clientlib-site/css/site.css`:

   ![Fichier CSS du site compilé dans ui.apps](../assets/style-cif-component/comiled-css-ui-apps.png)

   Ce fichier est `site.css` copié dans le `ui.apps` projet. Il fait désormais partie d’une bibliothèque cliente nommée `clientlib-site` avec une catégorie de `venia.site`. Une fois que le fichier fait partie du module `ui.apps`, il peut être déployé dans AEM.

   >[!NOTE]
   >
   > Les fichiers de ce type sont également ignorés du contrôle source, puisqu’ils doivent être générés pendant la création.

1. Examinez ensuite les autres bibliothèques clientes générées par le projet :

   ![Autres bibliothèques clientes](../assets/style-cif-component/other-clientlibs.png)

   Ces bibliothèques clientes ne sont pas gérées par le module `ui.frontend`. À la place, elles incluent les dépendances CSS et JavaScript fournies par Adobe. La définition de ces bibliothèques clientes figure dans le fichier `.content.xml` sous chaque dossier.

   **clientlib-base** - Une bibliothèque cliente vide qui incorpore simplement les dépendances nécessaires de [Composants principaux AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr). La catégorie est `venia.base`.

   **clientlib-cif** - Une bibliothèque cliente vide qui incorpore simplement les dépendances nécessaires de [AEM Composants principaux CIF](https://github.com/adobe/aem-core-cif-components). La catégorie est `venia.cif`.

   **clientlib-grid** - Inclut le CSS pour activer la fonction de grille réactive AEM. L’utilisation de la grille AEM active [Mode Mise en page](/help/sites-cloud/authoring/features/responsive-layout.md) dans l’éditeur d’AEM et permet aux auteurs de contenu de redimensionner les composants. La catégorie est `venia.grid` et est incorporée dans la bibliothèque `venia.base`.

1. Inspectez les fichiers `customheaderlibs.html` et `customfooterlibs.html` sous `ui.apps/src/main/content/jcr_root/apps/venia/components/page` :

   ![Scripts d’en-tête et de pied de page personnalisés](../assets/style-cif-component/custom-header-footer-script.png)

   Ces scripts incluent les bibliothèques **venia.base** et **venia.cif** comme partie de toutes les pages.

   >[!NOTE]
   >
   > Seules les bibliothèques de base sont « codées en dur » dans le cadre des scripts de page. La bibliothèque `venia.site` n’est pas incluse dans ces fichiers ; elle est à la place incluse dans le modèle de page pour une plus grande flexibilité. Ce processus est inspecté ultérieurement.

1. Depuis le terminal, créez et déployez tout le projet sur une instance locale d’AEM :

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

## Créer un teaser de produit {#author-product-teaser}

Maintenant que les mises à jour du code ont été déployées, ajoutez une instance du composant Teaser de produit à la page d’accueil du site à l’aide des outils de création AEM. Cela nous permet de visualiser les styles mis à jour.

1. Ouvrez un nouvel onglet de navigateur et accédez à la **page d’accueil** du site : [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

1. Développez l’outil de recherche de ressources (rail latéral) en mode **Modifier**. Faites basculer le filtre Ressources sur **Produits**.

   ![Développer l’outil de recherche de ressources et filtrer par Produits](../assets/style-cif-component/drag-drop-product-page.png)

1. Faites glisser et déposez un nouveau produit sur la page d’accueil du conteneur de mise en page principal :

   ![Teaser de produit avec bordure rose](../assets/style-cif-component/pink-border-product-teaser.png)

   Vous devriez constater que le teaser de produit a désormais une bordure rose vif basée sur la modification de règle CSS créée précédemment.

## Vérifier les bibliothèques clientes sur la page {#verify-client-libraries}

Vérifiez ensuite l’inclusion des bibliothèques clientes sur la page.

1. Accédez à la **page d’accueil** du site : [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html)

1. Sélectionnez le menu **Informations sur la page**, puis cliquez sur **Afficher comme publié(e)** :

   ![Afficher comme publié(e) ](../assets/style-cif-component/view-as-published.png)

   Cette page s’ouvre sans aucun code JavaScript de l’auteur AEM chargé, tel qu’il apparaîtrait sur le site publié. Notez que le paramètre de requête `?wcmmode=disabled` est annexé à l’URL. Lors du développement de code CSS et JavaScript, il est recommandé d’utiliser ce paramètre pour simplifier la page sans intervention de l’auteur AEM.

1. Affichez la source de la page ; vous devriez pouvoir constater que plusieurs bibliothèques clientes sont incluses :

   ```html
   <!DOCTYPE html>
   <html lang="en-US">
   <head>
       ...
       <link rel="stylesheet" href="/etc.clientlibs/venia/clientlibs/clientlib-base.min.css" type="text/css">
       <link rel="stylesheet" href="/etc.clientlibs/venia/clientlibs/clientlib-site.min.css" type="text/css">
   </head>
   ...
       <script type="text/javascript" src="/etc.clientlibs/venia/clientlibs/clientlib-site.min.js"></script>
       <script type="text/javascript" src="/etc.clientlibs/core/wcm/components/commons/site/clientlibs/container.min.js"></script>
       <script type="text/javascript" src="/etc.clientlibs/venia/clientlibs/clientlib-base.min.js"></script>
   <script type="text/javascript" src="/etc.clientlibs/core/cif/clientlibs/common.min.js"></script>
   <script type="text/javascript" src="/etc.clientlibs/venia/clientlibs/clientlib-cif.min.js"></script>
   </body>
   </html>
   ```

   Diffusées sur la page, les bibliothèques clientes sont précédées de `/etc.clientlibs` et sont diffusées par le biais d’un [proxy](/help/implementing/developing/introduction/clientlibs.md) afin d’éviter d’exposer un contenu sensible dans `/apps` ou `/libs`.

   Remarquez `venia/clientlibs/clientlib-site.min.css` et `venia/clientlibs/clientlib-site.min.js`. Ces fichiers sont les fichiers CSS et JavaScript compilés dérivés de la variable `ui.frontend` module .

## Inclusion de la bibliothèque cliente avec des modèles de page {#client-library-inclusion-pagetemplates}

Il existe plusieurs options pour inclure une bibliothèque côté client. Examinez ensuite comment le projet généré inclut les bibliothèques `clientlib-site` par le biais de [modèles de page](/help/implementing/developing/components/templates.md).

1. Accédez à la **page d’accueil** du site dans l’éditeur AEM : [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

1. Sélectionnez le menu **Informations sur la page**, puis cliquez sur **Éditer le modèle** :

   ![Éditer le modèle](../assets/style-cif-component/edit-template.png)

   Le **Page d’entrée** le modèle ouvert qui **Accueil** est basée sur .

   >[!NOTE]
   >
   > Pour afficher tous les modèles disponibles à partir de l’écran AEM démarrage, accédez à **Outils** > **Général** > **Modèles**.

1. Dans le coin supérieur gauche, sélectionnez l’icône **Informations sur la page**, puis cliquez sur **Politique de page**.

   ![Élément de menu Politique de page](../assets/style-cif-component/page-policy-menu.png)

1. La stratégie de page s’ouvre pour le modèle Landing Page :

   ![Politique de page – Landing Page](../assets/style-cif-component/page-policy-properties.png)

   Sur le côté droit, vous pouvez voir la liste des bibliothèques clientes. **categories** qui sont inclus sur toutes les pages qui utilisent ce modèle.

   * `venia.dependencies` – Fournit les bibliothèques de fournisseurs dont `venia.site` dépend.
   * `venia.site` - La catégorie pour `clientlib-site` que la variable `ui.frontend` génère.

   Notez que d’autres modèles utilisent la même politique, la **Page de contenu**, la **Page d’entrée**, etc. En réutilisant la même stratégie, elle garantit que les mêmes bibliothèques clientes sont incluses sur toutes les pages.

   Utiliser des politiques de modèle et de page pour gérer l’inclusion des bibliothèques clientes présente l’avantage de permettre de changer la politique par modèle. Par exemple, il se peut que vous gériez deux marques différentes au sein de la même instance AEM. Chaque marque possède son propre style ou *thème* mais les bibliothèques et le code de base sont les mêmes. Autre exemple : si vous disposez d’une bibliothèque cliente plus grande que vous ne souhaitez afficher que sur certaines pages, vous pouvez créer une politique de page unique réservée à ce modèle.

## Développement de webpack local {#local-webpack-development}

Dans l’exercice précédent, nous avons apporté une mise à jour à un fichier Sass dans le module `ui.frontend`, puis, après avoir créé Maven, nous avons déployé les modifications dans AEM. Ensuite, vous envisagez d’utiliser un serveur webpack-dev-server pour développer rapidement les styles front-end.

Le serveur webpack-dev-server crée des proxys des images et d’une partie du code CSS/JavaScript provenant de l’instance locale d’AEM, mais permet au développeur de modifier les styles et le code JavaScript dans le module `ui.frontend`.

1. Dans le navigateur, accédez à la **page d’accueil** et à **Afficher comme publié(e)** : [http://localhost:4502/content/venia/us/en.html?wcmmode=disabled](http://localhost:4502/content/venia/us/en.html?wcmmode=disabled).

1. Affichez la source de la page et la **copie** du code HTML brut de la page.

1. Revenez à l’IDE de votre choix sous le module `ui.frontend` et ouvrez le fichier : `ui.frontend/src/main/static/index.html`

   ![Fichier HTML statique](../assets/style-cif-component/static-index-html.png)

1. Remplacez le contenu de `index.html` et **collez** le code HTML copié à l’étape précédente.

1. Recherchez &quot;inclusions&quot; pour `clientlib-site.min.css`, `clientlib-site.min.js`, et **remove** eux.

   ```html
   <head>
       <!-- remove this link -->
       <link rel="stylesheet" href="/etc.clientlibs/venia/clientlibs/clientlib-base.min.css" type="text/css">
       ...
   </head>
   <body>
       ...
        <!-- remove this link -->
       <script type="text/javascript" src="/etc.clientlibs/venia/clientlibs/clientlib-site.min.js"></script>
   </body>
   ```

   Ces &quot;inclusions&quot; sont supprimées, car elles représentent la version compilée du code CSS et JavaScript généré par la variable `ui.frontend` module . Laissez les autres bibliothèques clientes telles qu’elles seront traitées par proxy à partir de l’instance AEM en cours d’exécution.

1. Ouvrez une nouvelle fenêtre de terminal et accédez au dossier `ui.frontend`. Exécutez la commande `npm start` :

   ```shell
   $ cd ui.frontend
   $ npm start
   ```

   Cette commande lance le serveur webpack-dev-server sur [http://localhost:8080/](http://localhost:8080/)

   >[!CAUTION]
   >
   > Si vous obtenez une erreur liée à Sass, arrêtez le serveur, exécutez la commande `npm rebuild node-sass` et répétez les étapes ci-dessus. Cette erreur peut se produire si vous disposez d’une version différente de `npm` et `node` spécifié dans le projet `aem-cif-guides-venia/pom.xml`.

1. Accédez au dossier [http://localhost:8080/](http://localhost:8080/) dans un nouvel onglet avec le même navigateur qu’une instance d’AEM connectée. Vous devriez voir la page d’accueil Venia via le serveur webpack-dev-server :

   ![Serveur de développement webpack sur le port 80](../assets/style-cif-component/webpack-dev-server-port80.png)

   Laissez le serveur webpack-dev-server en cours d’exécution. Il est utilisé dans l’exercice suivant.

## Mettre en œuvre le style de carte pour le teaser de produit {#update-css-product-teaser}

Modifiez ensuite les fichiers Sass dans le module `ui.frontend` afin de mettre en œuvre un style de type carte pour le teaser de produit. Le serveur webpack-dev-server est utilisé pour afficher rapidement les modifications.

Revenez à l’IDE et au projet généré.

1. Dans le **ui.frontend** module, rouvrez le fichier `_productteaser.scss` at `ui.frontend/src/main/styles/commerce/_productteaser.scss`.

1. Apportez les modifications suivantes à la bordure du teaser de produit :

   ```diff
       .item__image {
   -       border: #ea00ff 8px solid;
   +       border-bottom: 1px solid #c0c0c0;
           display: block;
           grid-area: main;
           height: auto;
           opacity: 1;
           transition-duration: 512ms;
           transition-property: opacity, visibility;
           transition-timing-function: ease-out;
           visibility: visible;
           width: 100%;
       }
   ```

   Enregistrez les modifications ; le serveur webpack-dev-server devrait automatiquement s’actualiser avec les nouveaux styles.

1. Ajoutez une ombre portée et ajoutez des coins arrondis au teaser de produit.

   ```scss
    .item__root {
        position: relative;
        box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
        transition: 0.3s;
        border-radius: 5px;
        float: left;
        margin-left: 12px;
        margin-right: 12px;
   }
   
   .item__root:hover {
      box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
   }
   ```

1. Mettez à jour le nom du produit devant s’afficher au bas du teaser et modifiez la couleur du texte.

   ```css
   .item__name {
       color: #000;
       display: block;
       float: left;
       font-size: 22px;
       font-weight: 900;
       line-height: 1em;
       padding: 0.75em;
       text-transform: uppercase;
       width: 75%;
   }
   ```

1. Mettez à jour le prix du produit devant également s’afficher au bas du teaser et modifiez la couleur du texte.

   ```css
   .price {
       color: #000;
       display: block;
       float: left;
       font-size: 18px;
       font-weight: 900;
       padding: 0.75em;
       padding-bottom: 2em;
       width: 25%;
   
       ...
   ```

1. Mettez à jour la requête multimédia en bas afin de pouvoir empiler le nom et le prix dans des écrans plus petits que **992 px**.

   ```css
   @media (max-width: 992px) {
       .productteaser .item__name {
           font-size: 18px;
           width: 100%;
       }
       .productteaser .item__price {
           font-size: 14px;
           width: 100%;
       }
   }
   ```

   Le style de carte devrait maintenant se refléter sur le serveur webpack-dev-server :

   ![Modifications du teaser du serveur de développement webpack](../assets/style-cif-component/webpack-dev-server-teaser-changes.png)

   Toutefois, les modifications n’ont pas encore été déployées dans AEM. Vous pouvez télécharger le [fichier de solution ici](../assets/style-cif-component/_productteaser.scss).

1. Déployez les mises à jour pour AEM à l’aide de vos compétences Maven, à partir d’un terminal de ligne de commande :

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

   >[!NOTE]
   >Il existe d’autres [outils et programmes d’installation IDE](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html?lang=fr#set-up-an-integrated-development-environment) pouvant synchroniser les fichiers de projet directement dans une instance d’AEM locale sans avoir à créer une version Maven entière.

## Afficher le teaser de produit mis à jour {#view-updated-product-teaser}

Une fois que le code du projet a été déployé sur AEM, vous devriez maintenant pouvoir voir les modifications apportées au teaser de produit.

1. Revenez à votre navigateur et actualisez la page d’accueil : [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html). Vous devriez constater que les styles de teaser de produit mis à jour ont été appliqués.

   ![Style de teaser de produit mis à jour](../assets/style-cif-component/product-teaser-new-style.png)

1. Expérimentez en ajoutant d’autres teasers de produit. Utilisez le mode Mise en page pour modifier la largeur et le décalage des composants afin d’afficher plusieurs teasers sur une même ligne.

   ![Plusieurs teasers de produits](../assets/style-cif-component/multiple-teasers-final.png)

## Résolution des problèmes {#troubleshooting}

Vous pouvez vérifier dans [CRXDE-Lite](http://localhost:4502/crx/de/index.jsp) que le fichier CSS mis à jour a été déployé : [http://localhost:4502/crx/de/index.jsp#/apps/venia/clientlibs/clientlib-site/css/site.css](http://localhost:4502/crx/de/index.jsp#/apps/venia/clientlibs/clientlib-site/css/site.css)

Lors du déploiement de nouveaux fichiers CSS ou JavaScript, ou les deux, il est également important de s’assurer que le navigateur ne diffuse pas de fichiers obsolètes. Vous pouvez éliminer ce problème potentiel en vidant le cache du navigateur ou en lançant une nouvelle session du navigateur.

AEM tente également de mettre en cache les bibliothèques clientes pour des raisons de performances. Il arrive qu’à la suite d’un déploiement de code les fichiers plus anciens soient diffusés. Vous pouvez invalider manuellement le cache de la bibliothèque cliente d’AEM à l’aide de l’outil [Reconstruire les bibliothèques clientes](http://localhost:4502/libs/granite/ui/content/dumplibs.rebuild.html). *La méthode d’invalidation du cache est conseillée si vous pensez qu’AEM a mis en cache une ancienne version d’une bibliothèque cliente. La reconstruction des bibliothèques est inefficace et prend du temps.*

## Félicitations {#congratulations}

Vous avez terminé de mettre en forme votre premier composant principal CIF AEM et vous avez utilisé un serveur de développement webpack !

## Défi bonus {#bonus-challenge}

Utilisez la variable [Système de style AEM](/help/sites-cloud/authoring/features/style-system.md) pour créer deux styles pouvant être activés ou désactivés par un auteur de contenu. [Développement avec le système de style](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/style-system.html?lang=fr) comprend des étapes détaillées et des informations sur la manière d’accomplir cette tâche.

![Défi bonus – Système de style](../assets/style-cif-component/bonus-challenge.png)

## Ressources supplémentaires {#additional-resources}

* [Archétype de projet AEM](https://github.com/adobe/aem-project-archetype)
* [Composants principaux AEM CIF](https://github.com/adobe/aem-core-cif-components)
* [Configuration d’un environnement de développement AEM local](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=fr)
* [Bibliothèques côté client](/help/implementing/developing/introduction/clientlibs.md)
* [Prise en main d’AEM Sites](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=fr)
* [Développement avec le système de style](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/style-system.html?lang=fr)
