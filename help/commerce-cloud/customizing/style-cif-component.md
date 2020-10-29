---
title: Composants principaux de style AEM CIF
description: Découvrez comment mettre en forme AEM composants principaux CIF. Ce didacticiel explique comment les bibliothèques ou clientlibs côté client sont utilisés pour déployer et gérer des fichiers CSS et Javascript pour une implémentation commerciale Adobe Experience Manager (AEM). Ce didacticiel explique également comment le module ui.frontend et un projet webpack sont intégrés dans le processus de génération de bout en bout.
sub-product: Commerce
topics: Development
version: cloud-service
doc-type: tutorial
activity: develop
audience: developer
feature: Commerce Integration Framework
kt: 3456
thumbnail: 3456-style-cif.jpg
translation-type: tm+mt
source-git-commit: 72d98c21a3c02b98bd2474843b36f499e8d75a03
workflow-type: tm+mt
source-wordcount: '2592'
ht-degree: 4%

---


# Composants principaux de style AEM CIF {#style-aem-cif-core-components}

Le projet [](https://github.com/adobe/aem-cif-guides-venia) CIF Venia est une base de code de référence pour l&#39;utilisation des composants [principaux](https://github.com/adobe/aem-core-cif-components)CIF. Dans ce tutoriel, vous allez examiner le projet de référence de Venia et comprendre comment les composants principaux de AEM CIF sont organisés en CSS et JavaScript. Vous allez également créer un style à l’aide de CSS pour mettre à jour le style par défaut du composant **Product Teaser** .

>[!TIP]
>
> Utilisez l&#39;archétype [du projet](https://github.com/adobe/aem-project-archetype) AEM lors du démarrage de votre propre implémentation commerciale.

## Ce que vous allez construire

Dans ce didacticiel, un nouveau style sera mis en oeuvre pour le composant Produit Teaser qui ressemble à une carte. Les leçons apprises dans le tutoriel peuvent être appliquées à d&#39;autres composantes essentielles du FIC.

![Ce que vous allez construire](../assets/style-cif-component/what-you-will-build.png)

## Conditions préalables {#prerequisites}

Un environnement de développement local est nécessaire pour compléter ce tutoriel. Cela inclut une instance en cours d’exécution d’AEM qui est configurée et connectée à une instance de Magento. Examinez les exigences et les étapes de la [configuration d’un développement local avec AEM comme SDK](../develop.md)Cloud Service.

## Cloner le projet Venia {#clone-venia-project}

Nous clonerons le projet [](https://github.com/adobe/aem-cif-guides-venia) Venia, puis nous remplacerons les styles par défaut.

>[!NOTE]
>
> **N&#39;hésitez pas à utiliser un projet** existant (basé sur l&#39;archétype de projet AEM avec CIF inclus) et ignorez cette section.

1. Exécutez la commande git suivante pour cloner le projet :

   ```shell
   $ git clone git@github.com:adobe/aem-cif-guides-venia.git
   ```

1. Créez et déployez le projet sur une instance locale d’AEM :

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

1. Ajoutez les configurations OSGi nécessaires pour connecter votre instance AEM à une instance de Magento ou ajoutez les configurations au projet nouvellement créé.

1. A ce stade, vous devez disposer d&#39;une version fonctionnelle d&#39;une vitrine connectée à une instance de Magento. Accédez à la page `US` > `Home` à l’adresse suivante : [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

   Vous devriez voir que la vitrine utilise actuellement le thème Venia. En développant le menu principal de la vitrine, vous devriez voir différentes catégories, indiquant que le Magento de connexion fonctionne.

   ![Vitrine configurée avec le thème Venia](../assets/style-cif-component/venia-store-configured.png)

## Bibliothèques client et module ui.frontend {#introduction-to-client-libraries}

La page CSS et le code JavaScript responsable du rendu du thème/des styles de la vitrine sont gérés AEM par une bibliothèque [](/help/implementing/developing/introduction/clientlibs.md) cliente ou des clientlibs pour un court laps de temps. Les bibliothèques clientes offrent un mécanisme permettant d’organiser CSS et Javascript dans le code d’un projet, puis de diffuser sur la page.

Des styles spécifiques à la marque peuvent être appliqués aux composants principaux AEM CIF en ajoutant et en remplaçant la page CSS gérée par ces bibliothèques clientes. Il est essentiel de comprendre comment les bibliothèques client sont structurées et incluses dans la page.

Le [ui.frontend](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/uifrontend.html) est un projet [webpack](https://webpack.js.org/) dédié à la gestion de toutes les ressources frontales d’un projet. Cela permet aux développeurs frontaux d&#39;utiliser un grand nombre de langages et de technologies tels que [TypeScript](https://www.typescriptlang.org/), [Sass](https://sass-lang.com/) et bien plus encore.

Le `ui.frontend` module est également un module Maven et intégré au projet plus vaste grâce à l&#39;utilisation d&#39;un module NPM le générateur [](https://github.com/wcm-io-frontend/aem-clientlib-generator)aem-clientlib. Au cours d’une génération, le `aem-clientlib-generator` copie les fichiers CSS et JavaScript compilés dans une bibliothèque cliente du `ui.apps` module.

![ui.frontend vers l’architecture ui.apps](../assets/style-cif-component/ui-frontend-architecture.png)

*Les fichiers CSS et Javascript compilés sont copiés du `ui.frontend` module dans le `ui.apps` module en tant que bibliothèque client lors d’une génération Maven.*

## Mettre à jour le style du teaser {#ui-frontend-module}

Ensuite, apportez une petite modification au style Teaser pour voir comment fonctionnent le `ui.frontend` module et les bibliothèques clientes. Utilisez [l&#39;IDE de votre choix](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html#set-up-the-development-ide) pour importer le projet Venia. Les captures d&#39;écran utilisées proviennent de l&#39;IDE [](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html#microsoft-visual-studio-code)Visual Studio Code.

1. Recherchez et développez le module **ui.frontend** et développez la hiérarchie de dossiers pour : `ui.frontend/src/main/styles/commerce`:

   ![ui.frontend, dossier de commerce](../assets/style-cif-component/ui-frontend-commerce-folder.png)

   Notez qu’il existe plusieurs fichiers Sass (`.scss`) sous le dossier. Il s’agit des styles propres au Commerce pour chacun des composants Commerce.

1. Open the file `_productteaser.scss`.

1. Mettez à jour la `.item__image` règle et modifiez la règle de bordure :

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

   La règle ci-dessus doit ajouter une bordure rose très audacieuse au composant Teaser du produit.

1. Ouvrez une nouvelle fenêtre de terminal et accédez au `ui.frontend` dossier :

   ```shell
   $ cd <project-location>/aem-cif-guides-venia/ui.frontend
   ```

1. Exécutez la commande expert suivante :

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

   Inspect la sortie du terminal. Vous verrez que la commande Maven a exécuté plusieurs scripts NPM, y compris `npm run build`. La `npm run build` commande est définie dans le `package.json` fichier et a pour effet de compiler le projet webpack et de déclencher la génération de la bibliothèque cliente.

1. Inspect le fichier `ui.frontend/dist/clientlib-site/site.css`:

   ![CSS du site compilé](../assets/style-cif-component/comiled-site-css.png)

   Le fichier est la version comilée et minifiée de tous les fichiers Sass du projet.

   >[!NOTE]
   >
   > Les fichiers de ce type sont ignorés du contrôle de code source, puisqu’ils doivent être générés pendant la génération.

1. Inspect le fichier `ui.frontend/clientlib.config.js`.

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

   Il s’agit du fichier de configuration pour [aem-clientlib-generator](https://github.com/wcm-io-frontend/aem-clientlib-generator) et détermine où et comment le CSS compilé et JavaScript se transformeront en une bibliothèque cliente AEM.

1. Dans le `ui.apps` module, inspectez le fichier : `ui.apps/src/main/content/jcr_root/apps/venia/clientlibs/clientlib-site/css/site.css`:

   ![CSS du site compilé dans ui.apps](../assets/style-cif-component/comiled-css-ui-apps.png)

   Il s&#39;agit du `site.css` fichier copié dans le `ui.apps` projet. Il fait désormais partie d’une bibliothèque cliente nommée `clientlib-site` avec une catégorie de `venia.site`données. Une fois que le fichier fait partie du `ui.apps` module, il peut être déployé sur AEM.

   >[!NOTE]
   >
   > Les fichiers de ce type sont également ignorés du contrôle de code source puisqu’ils doivent être générés pendant la génération.

1. Examinez ensuite les autres bibliothèques clientes générées par le projet :

   ![Autres bibliothèques clientes](../assets/style-cif-component/other-clientlibs.png)

   Ces bibliothèques clientes ne sont pas gérées par le `ui.frontend` module. Au lieu de cela, ces bibliothèques clientes incluent les dépendances CSS et JavaScript fournies par l’Adobe. La définition de ces bibliothèques clientes se trouve dans le `.content.xml` fichier sous chaque dossier.

   **clientlib-base** - Il s&#39;agit d&#39;une bibliothèque cliente vide qui incorpore simplement les dépendances nécessaires des composants [](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/introduction.html)principaux de l&#39;AEM. La catégorie est `venia.base`.

   **clientlib-cif** - Il s&#39;agit également d&#39;une bibliothèque cliente vide qui intègre simplement les dépendances nécessaires des composants [principaux](https://github.com/adobe/aem-core-cif-components)AEM CIF. La catégorie est `venia.cif`.

   **clientlib-grid** : inclut la page CSS nécessaire pour activer la fonction de grille réactive AEM. L’utilisation de la grille AEM active le mode [de](https://docs.adobe.com/content/help/en/experience-manager-65/administering/operations/configuring-responsive-layout.html#include-the-responsive-css) mise en page dans l’éditeur AEM et permet aux auteurs de contenu de redimensionner les composants. La catégorie est `venia.grid` et est incorporée dans la `venia.base` bibliothèque.

1. Inspect les fichiers `customheaderlibs.html` et `customfooterlibs.html` sous `ui.apps/src/main/content/jcr_root/apps/venia/components/page`:

   ![Scripts d’en-tête et de pied de page personnalisés](../assets/style-cif-component/custom-header-footer-script.png)

   Ces scripts incluent les bibliothèques **venia.base** et **venia.cif** dans toutes les pages.

   >[!NOTE]
   >
   > Seules les bibliothèques de base sont &quot;codées en dur&quot; dans le cadre des scripts de page. `venia.site` n’est pas incluse dans ces fichiers et est incluse dans le modèle de page pour une plus grande flexibilité. Cette inspection sera effectuée ultérieurement.

1. Depuis le terminal, créez et déployez l&#39;ensemble du projet sur une instance locale d&#39;AEM :

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

## Création d’un testeur de produit {#author-product-teaser}

Maintenant que les mises à jour du code ont été déployées, ajoutez une nouvelle instance du composant Product Teaser à la page d&#39;accueil du site à l’aide des outils de création AEM. Cela nous permettra de vue les styles mis à jour.

1. Ouvrez un nouvel onglet de navigateur et accédez à la **Page d&#39;accueil** du site : [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

1. Développez l’outil de recherche de ressources (le rail latéral) en mode **Edition** . Basculez le filtre Ressources sur **Produits**.

   ![Développez l’outil de recherche de ressources et filtrez par produits.](../assets/style-cif-component/drag-drop-product-page.png)

1. Faites glisser un nouveau produit sur la page d&#39;accueil du Conteneur de mise en page principal :

   ![Teaser produit avec bordure rose](../assets/style-cif-component/pink-border-product-teaser.png)

   Vous devriez voir que le produit Teaser a désormais une bordure rose vif basée sur la modification de règle CSS créée précédemment.

## Vérification des bibliothèques client sur la page {#verify-client-libraries}

Ensuite, vérifiez l’inclusion des bibliothèques clientes dans la page.

1. Accédez à la **Page d&#39;accueil** du site : [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

1. Sélectionnez le menu Informations **sur la** page, puis cliquez sur **Vue comme Publié**:

   ![Afficher comme publié(e) ](../assets/style-cif-component/view-as-published.png)

   La page s’ouvre alors sans que l’AEM javascript de l’auteur soit chargé, comme il apparaît sur le site publié. Notez que le paramètre de requête est `?wcmmode=disabled` annexé à l’URL. Lors du développement de CSS et de JavaScript, il est recommandé d’utiliser ce paramètre pour simplifier la page sans intervention de l’auteur AEM.

1. Vue de la source de la page et vous devriez être en mesure d’identifier plusieurs bibliothèques clientes sont incluses :

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

   Les bibliothèques clientes lorsqu’elles sont diffusées sur la page sont précédées d’un préfixe `/etc.clientlibs` et sont diffusées par le biais d’un [proxy](/help/implementing/developing/introduction/clientlibs.md) afin d’éviter d’exposer quelque chose de sensible dans `/apps` ou `/libs`.

   Remarquez `venia/clientlibs/clientlib-site.min.css` et `venia/clientlibs/clientlib-site.min.js`. Il s’agit des fichiers CSS et Javascript compilés dérivés du `ui.frontend` module.

## Inclusion de la bibliothèque cliente avec des modèles de page {#client-library-inclusion-pagetemplates}

Il existe plusieurs options pour inclure une bibliothèque côté client. Examinez ensuite comment le projet généré inclut les `clientlib-site` bibliothèques par le biais de modèles de [page](https://docs.adobe.com/content/help/en/experience-manager-65/developing/platform/templates/page-templates-editable.html).

1. Accédez à la **Page d&#39;accueil** du site dans l’éditeur AEM : [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

1. Sélectionnez le menu Informations **sur la** page, puis cliquez sur **Modifier le modèle**:

   ![Modifier le modèle](../assets/style-cif-component/edit-template.png)

   Cela ouvrira le modèle de **Landing page** sur lequel repose la page d’ **accueil** .

   >[!NOTE]
   >
   > Pour vue à tous les modèles disponibles à partir de l’écran Début AEM, accédez à **Outils** > **Général** > **Modèles**.

1. Dans le coin supérieur gauche, sélectionnez l’icône Informations **sur la** page, puis cliquez sur Stratégie **de** page.

   ![Option de menu Stratégie de page](../assets/style-cif-component/page-policy-menu.png)

1. La stratégie de page pour le modèle de Landing page s&#39;ouvre alors :

   ![Stratégie de page - landing page](../assets/style-cif-component/page-policy-properties.png)

   Sur le côté droit, vous pouvez voir la liste des **catégories** de bibliothèques clientes qui seront incluses sur toutes les pages qui utilisent ce modèle.

   * `venia.dependencies` - Fournit toutes les bibliothèques de fournisseurs qui `venia.site` dépendent.
   * `venia.site` - Il s&#39;agit de la catégorie pour `clientlib-site` laquelle le `ui.frontend` module génère.

   Notez que les autres modèles utilisent la même stratégie, la même page **de** contenu, le même **Landing page**, etc... En réutilisant la même stratégie, nous pouvons nous assurer que les mêmes bibliothèques clientes sont incluses sur toutes les pages.

   L’avantage de l’utilisation des stratégies Modèles et Pages pour gérer l’inclusion des bibliothèques clientes est que vous pouvez modifier la stratégie par modèle. Par exemple, vous gérez peut-être deux marques différentes au sein de la même instance AEM. Chaque marque aura son propre style ou *thème* unique, mais les bibliothèques de base et le code seront les mêmes. Autre exemple : si vous disposez d’une bibliothèque cliente plus grande que vous ne souhaitez afficher que sur certaines pages, vous pouvez créer une stratégie de page unique uniquement pour ce modèle.

## Développement de webpack local {#local-webpack-development}

Lors de l’exercice précédent, une mise à jour a été effectuée sur un fichier Sass dans le `ui.frontend` module, puis après avoir exécuté une création Maven, les modifications sont déployées sur AEM. Nous allons maintenant nous pencher sur l&#39;utilisation d&#39;un serveur webpack-dev-server pour développer rapidement les styles frontaux.

Le webpack-dev-server proxie des images et une partie du CSS/JavaScript provenant de l’instance locale de l’AEM, mais permet au développeur de modifier les styles et le code JavaScript dans le `ui.frontend` module.

1. Dans le navigateur, accédez à la page d’ **accueil** et à la **Vue Publiée**: [http://localhost:4502/content/venia/us/en.html?wcmmode=disabled](http://localhost:4502/content/venia/us/en.html?wcmmode=disabled).

1. Vue de la source de la page et de la **copie** du code HTML brut de la page.

1. Revenez à l&#39;IDE de votre choix sous le `ui.frontend` module ouvrez le fichier : `ui.frontend/src/main/static/index.html`

   ![Fichier HTML statique](../assets/style-cif-component/static-index-html.png)

1. Remplacez le contenu de `index.html` et **collez** le code HTML copié à l’étape précédente.

1. Recherchez les inclusions `clientlib-site.min.css`, `clientlib-site.min.js` puis **supprimez** -les.

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

   Elles sont supprimées car elles représentent la version compilée du CSS et du code JavaScript générés par le `ui.frontend` module. Laissez les autres bibliothèques clientes telles qu’elles seront traitées par proxy à partir de l’instance AEM en cours d’exécution.

1. Ouvrez une nouvelle fenêtre de terminal et accédez au `ui.frontend` dossier. Exécutez la commande `npm start`:

   ```shell
   $ cd ui.frontend
   $ npm start
   ```

   Cela début le serveur webpack-dev-dev sur [http://localhost:8080/](http://localhost:8080/)

   >[!CAUTION]
   >
   > Si vous obtenez une erreur liée à Sass, arrêtez le serveur, exécutez la commande `npm rebuild node-sass` et répétez les étapes ci-dessus. Cela peut se produire si vous disposez d’une autre version de `npm` et `node` que vous avez ensuite spécifiée dans le projet `aem-cif-guides-venia/pom.xml`.

1. Accédez au dossier [http://localhost:8080/](http://localhost:8080/) dans un nouvel onglet avec le même navigateur qu’une instance d’AEM connectée. Vous devriez voir la page d&#39;accueil Venia via webpack-dev-server :

   ![Serveur Webpack dev sur le port 80](../assets/style-cif-component/webpack-dev-server-port80.png)

   Laissez le webpack-dev-server en cours d’exécution. Il sera utilisé dans le prochain exercice.

## Mise en oeuvre du style de carte pour Product Teaser {#update-css-product-teaser}

Modifiez ensuite les fichiers Sass dans le `ui.frontend` module pour mettre en oeuvre un style de type carte pour le produit Teaser. Le webpack-dev-server sera utilisé pour voir rapidement les changements.

Revenez à l&#39;IDE et au projet généré.

1. Dans le module **ui.frontend** , rouvrez le fichier `_productteaser.scss` à `ui.frontend/src/main/styles/commerce/_productteaser.scss`.

1. Apportez les modifications suivantes à la bordure du produit Teaser :

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

   Enregistrez les modifications et le webpack-dev-server devrait automatiquement actualiser avec les nouveaux styles.

1. Ajoutez une ombre portée et ajoutez des coins arrondis au produit Teaser.

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

1. Mettez à jour le nom du produit pour qu’il s’affiche au bas du teaser et modifiez la couleur du texte.

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

1. Mettez à jour le prix du produit pour qu&#39;il apparaisse également au bas du teaser et modifiez la couleur du texte.

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

1. Mettez à jour la requête multimédia en bas pour empiler le nom et le prix dans les écrans inférieurs à **992px**.

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

   Vous devriez maintenant voir le style de carte reflété dans le webpack-dev-server :

   ![Modifications du teaser Webpack Dev Server](../assets/style-cif-component/webpack-dev-server-teaser-changes.png)

   Toutefois, les modifications n&#39;ont pas encore été déployées en AEM. Vous pouvez télécharger le fichier de la [solution ici](../assets/style-cif-component/_productteaser.scss).

1. Déployez les mises à jour pour AEM à l&#39;aide de vos compétences Maven, à partir d&#39;un terminal de ligne de commande :

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

   >[!NOTE]
   >Il existe d&#39;autres outils [et programmes d&#39;installation](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html#set-up-an-integrated-development-environment) IDE qui peuvent synchroniser les fichiers de projet directement vers une instance d&#39;AEM locale sans avoir à effectuer une compilation Maven complète.

## Vue Mise à jour du produit Teaser {#view-updated-product-teaser}

Une fois que le code du projet a été déployé sur AEM, nous devons maintenant être en mesure de voir les modifications apportées au produit Teaser.

1. Revenez à votre navigateur et actualisez la Page d&#39;accueil : [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html). Vous devriez voir les styles de teaser de produit mis à jour appliqués.

   ![Mise à jour du style de produit Teaser](../assets/style-cif-component/product-teaser-new-style.png)

1. Testez en ajoutant d&#39;autres produits. Utilisez le mode Mise en page pour modifier la largeur et le décalage des composants afin d’afficher plusieurs teasers sur une même ligne.

   ![Teasers de produits multiples](../assets/style-cif-component/multiple-teasers-final.png)

## Résolution des incidents {#troubleshooting}

Vous pouvez vérifier dans [CRXDE-Lite](http://localhost:4502/crx/de/index.jsp) que le fichier CSS mis à jour a été déployé : [http://localhost:4502/crx/de/index.jsp#/apps/venia/clientlibs/clientlib-site/css/site.css](http://localhost:4502/crx/de/index.jsp#/apps/venia/clientlibs/clientlib-site/css/site.css)

Lors du déploiement de nouveaux fichiers CSS et/ou JavaScript, il est également important de s’assurer que le navigateur ne diffuse pas les fichiers obsolètes. Vous pouvez éliminer ce problème en vidant le cache du navigateur ou en lançant une nouvelle session du navigateur.

aem tente également de mettre en cache les bibliothèques clientes pour des raisons de performances. Il arrive parfois qu’à la suite d’un déploiement du code, les fichiers plus anciens soient diffusés. Vous pouvez invalider manuellement AEM cache de bibliothèque cliente à l’aide de l’outil [](http://localhost:4502/libs/granite/ui/content/dumplibs.rebuild.html)Reconstruire les bibliothèques clientes. *La méthode d’invalidation des caches est conseillée si vous pensez que AEM a mis en cache une ancienne version d’une bibliothèque cliente. La reconstruction des bibliothèques est inefficace et prend du temps.*

## Congratulations {#congratulations}

Vous venez de mettre en forme votre premier composant AEM CIF Core et vous avez utilisé un serveur de développement webpack !

## Bonus Challenge {#bonus-challenge}

Utilisez le système [Style](https://docs.adobe.com/content/help/fr-FR/experience-manager-65/developing/components/style-system.html) AEM pour créer deux styles qui peuvent être activés/désactivés par un auteur de contenu. [Le développement avec le système](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/style-system.html) de style comprend des étapes détaillées et des informations sur la façon d&#39;y parvenir.

![Bonus Challenge - Système de style](../assets/style-cif-component/bonus-challenge.png)

## Ressources supplémentaires {#additional-resources}

* [Archétype de projet AEM](https://github.com/adobe/aem-project-archetype)
* [Composants principaux AEM CIF](https://github.com/adobe/aem-core-cif-components)
* [Configuration d’un Environnement de développement AEM local](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html)
* [Bibliothèques côté client](/help/implementing/developing/introduction/clientlibs.md)
* [Prise en main de AEM Sites](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)
* [Développer avec le système de style](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/style-system.html)
