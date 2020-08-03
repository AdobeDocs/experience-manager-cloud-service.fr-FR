---
title: Composants principaux de style AEM CIF
description: Composants principaux de style AEM CIF
translation-type: tm+mt
source-git-commit: 48805b21500ff3f2629efd6aecb40bb1cdc38cd6
workflow-type: tm+mt
source-wordcount: '2568'
ht-degree: 4%

---


# Composants principaux de style AEM CIF {#style-aem-cif-core-components}

L&#39;archétype [du projet](https://github.com/adobe/aem-cif-project-archetype) CIF crée un projet CIF d&#39;Adobe Experience Manager minimal (AEM) comme point de départ pour les projets clients en utilisant les composants [de base](https://github.com/adobe/aem-core-cif-components)AEM CIF. Un style par défaut, connu sous le nom de marque Venia, est initialement appliqué au site. Dans ce didacticiel, vous allez examiner un nouveau projet AEM CIF, généré par l&#39;archétype et comprendre comment CSS et JavaScript utilisés par AEM composants CIF Core sont organisés. Vous allez également créer un style à l’aide de CSS pour remplacer le style par défaut du composant Produit Teaser.

![Ce que vous allez construire](/help/commerce-cloud/assets/style-cif-component/what-you-will-build.png)

>[!NOTE]
> Un nouveau style sera mis en oeuvre pour le composant Produit Teaser qui ressemble à une carte.

## Conditions préalables {#prerequisites}

Les outils et technologies suivants sont nécessaires :

* [Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/index.html) ou [Java 11](https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html) (AEM 6.5+ uniquement)
* [Apache Maven](https://maven.apache.org/) (version 3.3.9 ou ultérieure)
* Adobe Experience Manager (instance locale)
   * [AEM 6.5](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/introduction/technical-requirements.html)
   * [AEM 6.4.4+](https://docs.adobe.com/content/help/en/experience-manager-64/release-notes/sp-release-notes.html)
* Magento exécutant une [version compatible avec l&#39;archétype](https://github.com/adobe/aem-cif-project-archetype#requirements)

## Générer un projet {#generate-project}

Nous allons générer un nouveau projet AEM CIF à l&#39;aide de l&#39;archétype [du projet](https://github.com/adobe/aem-cif-project-archetype) CIF, puis remplacer les styles par défaut.

**N&#39;hésitez pas à utiliser un projet** existant (basé sur l&#39;archétype du projet CIF) et ignorez cette section.

1. Déterminez la dernière version de l&#39;archétype de projet CIF en affichant [la dernière version sur GitHub](https://github.com/adobe/aem-cif-project-archetype/releases/latest). Dans l’étape suivante, remplacez `x.y.z` par la version de la dernière version.

1. Exécutez la commande expert suivante pour générer un nouveau projet en mode [](https://maven.apache.org/archetype/maven-archetype-plugin/examples/generate-batch.html)batch.

   ```terminal
   mvn archetype:generate -B \
       -DarchetypeGroupId="com.adobe.commerce.cif" \
       -DarchetypeArtifactId="cif-project-archetype" \
       -DarchetypeVersion=x.y.z \
       -DgroupId="com.acme.cif" \
       -DartifactId="acme-store" \
       -Dversion=0.0.1-SNAPSHOT \
       -Dpackage="com.acme.cif" \
       -DappsFolderName="acme" \
       -DartifactName="Acme Store" \
       -DcontentFolderName="acme" \
       -DpackageGroup="acme" \
       -DsiteName="Acme Store" \
       -DoptionAemVersion=6.5.0 \
       -DoptionIncludeExamples=y \
       -DoptionEmbedConnector=y
   ```

1. Créez et déployez le projet sur une instance locale d’AEM :

   ```shell
   $ cd acme-store/
   $ mvn clean install -PautoInstallAll
   ```

1. Ajoutez les configurations OSGi nécessaires pour connecter votre instance AEM à une instance de Magento ou ajoutez les configurations au projet nouvellement créé.

1. A ce stade, vous devez disposer d&#39;une version fonctionnelle d&#39;une vitrine connectée à une instance de Magento. Accédez à la page `US` > `Home` à l’adresse suivante : [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html)

   Vous devriez voir que la vitrine utilise actuellement le thème Venia. En développant le menu principal de la vitrine, vous devriez voir différentes catégories, indiquant que le Magento de connexion fonctionne.

   ![Vitrine configurée avec le thème Venia](/help/commerce-cloud/assets/style-cif-component/acme-store-configured.png)

## Présentation des bibliothèques clientes {#introduction-to-client-libraries}

La page CSS et le code JavaScript responsable du rendu du thème/des styles de la vitrine sont gérés AEM par une bibliothèque [](https://docs.adobe.com/content/help/en/experience-manager-65/developing/introduction/clientlibs.html) cliente ou des clientlibs pour un court laps de temps. Les bibliothèques clientes offrent un mécanisme permettant d’organiser CSS et Javascript dans le code d’un projet, puis de diffuser sur la page.

Pour appliquer des styles spécifiques à la marque à AEM composants principaux de CIF, nous pouvons ajouter et remplacer le fichier CSS géré par ces bibliothèques clientes. Il est essentiel de comprendre comment les bibliothèques client sont structurées et incluses dans la page.

### Bibliothèques clientes de projet {#project-client-libraries}

Ensuite, nous allons examiner les bibliothèques clientes générées automatiquement par l&#39;archétype. Utilisez l&#39;IDE de votre choix pour [importer le projet généré lors de l&#39;exercice](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html#set-up-an-integrated-development-environment)précédent.

1. Recherchez et développez le module **ui.apps** et développez la hiérarchie de dossiers pour : `ui.apps/src/main/content/jcr_root/apps/acme/clientlibs`:

   ![ui.apps clientlibs](/help/commerce-cloud/assets/style-cif-component/ui-apps-clientli-folder.png)

   Il y a deux dossiers sous, **clientlib-base** et **thème**.

1. **clientlib-base** - Il s&#39;agit d&#39;une bibliothèque cliente vide qui incorpore simplement les dépendances nécessaires des composants [](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/introduction.html)principaux de l&#39;AEM.

   ![Clientlib-base](/help/commerce-cloud/assets/style-cif-component/clientlib-base-folderhierarchy.png)

   Voici la définition XML de **clientlib-base** (le `.content.xml` fichier) :

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:ClientLibraryFolder"
       allowProxy="{Boolean}true"
       categories="[acme.wcm.base]"
       embed="[core.wcm.components.accordion.v1,core.wcm.components.tabs.v1,core.wcm.components.carousel.v1,core.wcm.components.image.v2,core.wcm.components.breadcrumb.v2,core.wcm.components.search.v1,core.wcm.components.form.text.v2]"/>
   ```

   `acme.wcm.base` est la catégorie de cette bibliothèque cliente. Imaginez une catégorie comme une étiquette. Elle sera utilisée pour inclure ou incorporer la bibliothèque sur la page.

   Notez la `embed` propriété et le tableau des autres catégories clientlib. Chacune de ces catégories représente une bibliothèque cliente. Par exemple, `core.wcm.components.accordion.v1` inclut le javascript nécessaire au fonctionnement du composant [](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/accordion.html) Accordéon.

   En utilisant les propriétés `embed` et `categories` les propriétés, vous pouvez gérer et inclure des bibliothèques clientes de différents projets.

   `allowProxy=true` garantit que la bibliothèque cliente CSS et JavaScript sera diffusée à partir d’un chemin précédé du préfixe suivant : `/etc.clientlibs`. Cela garantit que le code de l’application sous `/apps` reste protégé contre les utilisateurs finaux, mais que les fichiers CSS et JavaScript nécessaires au fonctionnement du site Web peuvent être diffusés de manière anonyme. More details about the [allowProxy property can be found here](https://docs.adobe.com/content/help/en/experience-manager-65/developing/introduction/clientlibs.html#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet).

1. **thème** : bibliothèque cliente qui contient le thème de départ et le CSS pour le projet CIF. Cette bibliothèque cliente est conçue pour être personnalisée par chaque implémentation et il est utile de la début avec certains styles existants afin que les composants soient fonctionnels pour le début.

   ![bibliothèque cliente thème](/help/commerce-cloud/assets/style-cif-component/clientlib-theme-folder-hierarchy.png)

   Voici la définition XML du **thème**:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:ClientLibraryFolder"
       allowProxy="{Boolean}true"
       categories="[acme.theme]"/>
   ```

   `acme.theme` est la catégorie de cette bibliothèque cliente et c’est ainsi que la bibliothèque cliente sera incluse dans la page.

1. Sous la bibliothèque cliente **de thème** , vous devriez voir un fichier nommé **css.txt** situé à l’emplacement suivant : `ui.apps/src/main/content/jcr_root/apps/acme/clientlibs/theme/css.txt`:

   ```plain
   #base=.
   common/common.css
   
   components/button/button.css
   
   components/featuredcategorylist/categorylist.css
   
   ...
   ```

   Le **css.txt** (et **js.txt**) se comportent comme des manifestes qui déterminent l’ordre dans lequel les fichiers individuels sont inclus dans le fichier CSS final. L&#39;ordre est important pour CSS et JavaScript et il est agréable de pouvoir créer plusieurs fichiers afin de mieux gérer le code. En parcourant le fichier **css.txt** , vous pouvez constater que les fichiers sont organisés en fonction des composants auxquels les styles sont appliqués.

1. Inspect les fichiers CSS sous le **thème/les composants** pour avoir une idée des styles de composants d’barre d’outils. Nous mettrons à jour certains de ces fichiers plus tard dans le didacticiel.

### Inclusion de la bibliothèque cliente avec le composant de page de base

Ensuite, nous allons examiner comment les bibliothèques clientes sont incluses sur une page à l&#39;aide du [code HTML](https://docs.adobe.com/content/help/en/experience-manager-65/developing/introduction/clientlibs.html#using-htl) et du composant Page.

1. Dans le module **ui.apps** , accédez à la définition du `page` composant sous : `ui.apps/src/main/content/jcr_root/apps/acme/components/structure/page`. Ce composant de **page** , généré par l&#39;archétype, est le point d&#39;entrée utilisé pour effectuer le rendu de toutes les pages du projet.

1. Si vous examinez la définition ( **) du composant de** page`page/.content.xml`, vous remarquerez qu’une propriété `sling:resourceSuperType` pointe vers `core/cif/components/structure/page/v1/page`. Cela signifie que le composant de **page** de notre projet (Acme) héritera de toutes les fonctionnalités du composant de page [principale du](https://github.com/adobe/aem-core-cif-components/tree/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/structure/page/v1/page) FIC et nous permettra de gérer moins de code.

1. Deux fichiers se trouvent sous le composant **de page** : **customheaderlibs.html** et **customfooterlibs.html**.

   ```html
   <!--/* customheaderlibs.html */-->
   <sly data-sly-use.clientLib="/libs/granite/sightly/templates/clientlib.html"
    data-sly-call="${clientlib.css @ categories='acme.wcm.base'}"/>
   ```

   **customheaderlibs.html** est un script HTL qui sera rendu au début de la page. Il s’agit d’un script courant qui remplace et ajoute une logique spécifique au projet. Dans ce cas, nous l&#39;utilisons pour inclure la bibliothèque cliente avec une catégorie de `acme.wcm.base`données. En suivant les meilleures pratiques de développement Web, nous incluons uniquement le CSS dans l’en-tête de la page.

   ```html
   <!--/* customfooterlibs.html */-->
   <sly data-sly-use.clientlib="/libs/granite/sightly/templates/clientlib.html">
       <sly data-sly-call="${clientlib.js @ categories='acme.wcm.base'}"/>
   </sly>
   ```

   **customfooterlibs.html** est un script HTML qui sera rendu au bas de la page, juste avant la balise `</body>` de fermeture. Là encore, la catégorie de `acme.wcm.base` est utilisée mais cette fois, seul le code JavaScript de la bibliothèque cliente sera chargé.

La modification des scripts HTML du composant de **page** correspond à la manière dont `acme.wcm.base` est incluse sur toutes les pages. Mais qu&#39;en est-il `acme.theme`? Au cours du prochain exercice, nous examinerons une autre option pour inclure les bibliothèques clientes.

### Inclusion de la bibliothèque cliente avec des modèles de page {#client-library-inclusion-pagetemplates}

Il existe plusieurs options pour inclure une bibliothèque côté client. Ensuite, nous allons examiner comment le projet généré inclut les bibliothèques côté client du thème par le biais de modèles de [page](https://docs.adobe.com/content/help/en/experience-manager-65/developing/platform/templates/page-templates-editable.html).

Ouvrez un nouveau navigateur et connectez-vous à l’instance AEM dans laquelle vous avez déployé le projet au début de ce didacticiel.

1. Dans l’écran Début AEM, accédez à **Outils** > **Général** > **Modèles**.

   ![Navigation dans les modèles](/help/commerce-cloud/assets/style-cif-component/template-location.png)

1. Accédez au dossier Configuration **de la** boutique Acme Store. Ouvrez le modèle **de page de** Catégorie en sélectionnant l’icône *représentant un crayon* .

   ![Carte de modèle de page de catégorie](/help/commerce-cloud/assets/style-cif-component/category-page-template.png)

1. Dans le coin supérieur gauche, sélectionnez l’icône Informations **sur la** page, puis cliquez sur Stratégie **de** page.

   ![Option de menu Stratégie de page](/help/commerce-cloud/assets/style-cif-component/page-policy-menu.png)

1. La stratégie de page pour le modèle Page du catalogue s’ouvre alors :

   ![Stratégie de page - Page de catalogue](/help/commerce-cloud/assets/style-cif-component/page-policy-properties.png)

   Sur le côté droit, vous pouvez voir la liste des **catégories** de bibliothèques clientes qui seront incluses sur toutes les pages qui utilisent ce modèle.

   * **wcm.foundation.components.page.response** - Fournit le fichier CSS nécessaire pour activer les contrôles de mise en page [](https://docs.adobe.com/content/help/fr-FR/experience-manager-65/authoring/siteandpage/responsive-layout.html) réactifs par les auteurs.
   * **acme.theme** - Il s&#39;agit du thème de départ que l&#39;archétype génère automatiquement. Par défaut, ce style s’apparente à celui de l’exemple de boutique de démonstration Venia. Cependant, comme vous pouvez le voir à partir du nom, il est destiné à être personnalisé par l&#39;implémentation du projet. *C&#39;est ce que nous allons modifier dans la prochaine section !*
   * **core.cif.components.response** - Il s’agit d’une bibliothèque cliente compilée de plusieurs composants React utilisés pour des fonctionnalités dynamiques telles que le panier. More [information can be found here](https://github.com/adobe/aem-core-cif-components/tree/master/react-components).

   Notez que les autres modèles utilisent la même stratégie, la même page **de** contenu, le même **Landing page**, etc... En réutilisant la même stratégie, nous pouvons nous assurer que les mêmes bibliothèques clientes sont incluses sur toutes les pages.

   L’avantage de l’utilisation des stratégies Modèles et Pages pour gérer l’inclusion des bibliothèques clientes est que vous pouvez modifier la stratégie par modèle. Par exemple, vous gérez peut-être deux marques différentes au sein de la même instance AEM. Chaque marque aura son propre style ou *thème* unique, mais les bibliothèques de base et le code seront les mêmes. Autre exemple : si vous disposez d’une bibliothèque cliente plus grande que vous ne souhaitez afficher que sur certaines pages, vous pouvez créer une stratégie de page unique uniquement pour ce modèle. L&#39;autre avantage

### Vérification des bibliothèques client sur la page {#verify-client-libraries}

A ce stade, nous avons examiné comment inclure les bibliothèques clientes utilisant HTL avec les scripts **customheaderlibs.html** et **customfooterlibs.html** et comment la stratégie de page d&#39;un modèle peut être utilisée pour inclure d&#39;autres bibliothèques clientes. Ensuite, nous vérifierons l&#39;inclusion des bibliothèques clientes sur le site.

1. Dans l’écran Début de l’AEM, accédez à **Sites** > **Acme Store** > États-Unis **>** **Anglais et ouvrez la page pour modification :** http://localhost:4502/editor.html/content/acme/us/en.html[.](http://localhost:4502/editor.html/content/acme/us/en.html)

1. Sélectionnez le menu Informations **sur la** page, puis cliquez sur **Vue comme Publié**:

   ![Afficher comme publié(e) ](/help/commerce-cloud/assets/style-cif-component/view-as-published.png)

   La page s’ouvre alors sans que l’AEM javascript de l’auteur soit chargé, comme il apparaît sur le site publié. Notez que le paramètre de requête est `?wcmmode=disabled` annexé à l’URL. Lors du développement de CSS et de JavaScript, il est recommandé d’utiliser ce paramètre pour simplifier la page sans intervention de l’auteur AEM.

1. Vue de la source de la page et vous devriez être en mesure d&#39;identifier les bibliothèques clientes suivantes sont incluses : **acme.wcm.base**, **wcm.foundation.components.page.réactif**, **acme.theme**, **core.cif.components.response**

   ```html
   <!DOCTYPE html>
   <html lang="en-US">
   <head>
       ...
       <link rel="stylesheet" href="/etc.clientlibs/acme/clientlibs/clientlib-base.css" type="text/css">
       <link rel="stylesheet" href="/libs/wcm/foundation/components/page/responsive.css" type="text/css">
       <link rel="stylesheet" href="/etc.clientlibs/acme/clientlibs/theme.css" type="text/css">
   </head>
   ...
   
       <script type="text/javascript" src="/etc.clientlibs/core/cif/clientlibs/react-components.js"></script>
       <script type="text/javascript" src="/etc.clientlibs/acme/clientlibs/clientlib-base.js"></script>
   </body>
   </html>
   ```

## Style du produit Teaser {#style-product-teaser}

Maintenant que nous comprenons la structure de la bibliothèque cliente générée par l’archétype, nous pouvons commencer à personnaliser les composants principaux AEM CIF. Nous modifierons les styles du composant Teaser de produit afin qu’il ressemble davantage à une &quot;carte&quot;.

### Auteur du produit Teaser {#author-product-teaser}

Dans un premier temps, nous allons ajouter une nouvelle instance du composant Produit Teaser à la page d&#39;accueil de notre site à l&#39;aide des outils de création AEM.

1. Ouvrez un nouvel onglet de navigateur et accédez à la **Page d&#39;accueil** du site : [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html).

1. Insérez un nouveau composant **Produit Teaser** dans le conteneur de mise en page principal de la page.

   ![Insérer un produit Teaser](/help/commerce-cloud/assets/style-cif-component/product-teaser-add-component.png)

1. Développez le panneau latéral (s’il n’est pas déjà activé) et basculez la liste déroulante de recherche de ressources sur **Produits**. Ceci devrait afficher une liste de produits disponibles à partir d’une instance de Magento connectée. Sélectionnez un produit et **faites-le glisser** sur le composant **Produit Teaser** de la page.

   ![Faire glisser + déposer le produit Teaser](/help/commerce-cloud/assets/style-cif-component/drag-drop-product-teaser.png)

   > Remarque : vous pouvez également configurer le produit affiché en configurant le composant à l’aide de la boîte de dialogue (en cliquant sur l’icône de *clé à molette* ).

1. Vous devriez maintenant voir un produit affiché par le Teaser de produit. Le nom du produit et le prix du produit sont des attributs par défaut affichés.

   ![Produit Teaser - style par défaut](/help/commerce-cloud/assets/style-cif-component/product-teaser-default-style.png)

### Mise à jour du fichier CSS du produit Teaser {#update-css-product-teaser}

Ensuite, nous allons modifier la page CSS dans la bibliothèque cliente **de thème** afin de mettre en oeuvre un style de carte pour le produit Teaser.

Revenez à l&#39;IDE et au projet généré.

1. Dans le module **ui.apps** , accédez au dossier : `ui.apps/src/main/content/jcr_root/apps/acme/clientlibs/theme/components/productteaser`. C&#39;est là que sont définis tous les styles du produit Teaser.

1. Ouvrez le fichier **teaser.css** et mettez à jour les règles CSS correspondantes (ou téléchargez le fichier [teaser.css de la](/help/commerce-cloud/assets/style-cif-component/solution-teaser.css) solution et remplacez-le).

   Ajoutez une ombre portée et ajoutez des coins arrondis au produit Teaser.

   ```css
    .productteaser .item__root {
        position: relative;
        box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
        transition: 0.3s;
        border-radius: 5px;
        float: left;
        margin-left: 12px;
        margin-right: 12px;
   }
   
   .productteaser .item__root:hover {
      box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
   }
   ```

   Modifiez la bordure de l’image dans le produit Teaser.

   ```css
   .productteaser .item__image {
       border-bottom: 1px solid #c0c0c0;
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

   Mettez à jour le nom du produit pour qu’il s’affiche au bas du teaser et modifiez la couleur du texte.

   ```css
   .productteaser .item__name {
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

   Mettez à jour le prix du produit pour qu&#39;il apparaisse également au bas du teaser et modifiez la couleur du texte.

   ```css
   .productteaser .item__price {
       color: #000;
       display: block;
       float: left;
       font-size: 18px;
       font-weight: 900;
       padding: 0.75em;
       padding-bottom: 2em;
       width: 25%;
   }
   ```

   Mettez à jour la requête multimédia en bas pour empiler le nom et le prix dans les écrans de moins de 992 px.

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

   Enregistrez les modifications dans **teaser.css**. Vous pouvez télécharger le fichier teaser.css de la [solution ici](/help/commerce-cloud/assets/style-cif-component/solution-teaser.css).

1. Déployez les mises à jour du module **ui.apps** pour AEM à l’aide de vos compétences Maven, à partir d’un terminal de ligne de commande :

   ```shell
           $ cd acme-store/ui.apps/
           $ mvn -PautoInstallPackage clean install
           ...
           saving approx 0 nodes...
           Package imported.
           Package installed in 61ms.
           [INFO] ------------------------------------------------------------------------
           [INFO] BUILD SUCCESS
           [INFO] ------------------------------------------------------------------------
           [INFO] Total time:  6.903 s
           [INFO] Finished at: 2020-02-06T13:21:36-08:00
            [INFO] ------------------------------------------------------------------------
   ```

   >[!NOTE]
   >Il existe d&#39;autres outils [et programmes d&#39;installation](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html#set-up-an-integrated-development-environment) IDE qui peuvent synchroniser les fichiers de projet directement vers une instance d&#39;AEM locale sans avoir à effectuer une compilation Maven complète.

### Vue Mise à jour du produit Teaser {#view-updated-product-teaser}

Une fois que le code du projet a été déployé sur AEM, nous devons maintenant être en mesure de voir les modifications apportées au produit Teaser.

1. Revenez à votre navigateur et actualisez la Page d&#39;accueil : [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html). Vous devriez voir les styles de teaser de produit mis à jour appliqués.

   ![Mise à jour du style de produit Teaser](/help/commerce-cloud/assets/style-cif-component/product-teaser-new-style.png)

1. Testez en ajoutant d&#39;autres produits. Utilisez le mode Mise en page pour modifier la largeur et le décalage des composants afin d’afficher plusieurs teasers sur une même ligne.

   ![Teasers de produits multiples](/help/commerce-cloud/assets/style-cif-component/multiple-teasers-final.png)

   >[!NOTE]
   >Chaque teaser de produit contient le même style.

### Résolution des incidents {#troubleshooting}

Vous pouvez vérifier dans [CRXDE-Lite](http://localhost:4502/crx/de/index.jsp) que le fichier CSS mis à jour a été déployé : [http://localhost:4502/crx/de/index.jsp#/apps/acme/clientlibs/theme/components/productteaser/teaser.css](http://localhost:4502/crx/de/index.jsp#/apps/acme/clientlibs/theme/components/productteaser/teaser.css)

Lors du déploiement de nouveaux fichiers CSS et/ou JavaScript, il est également important de s’assurer que le navigateur ne diffuse pas les fichiers obsolètes. Vous pouvez éliminer ce problème en vidant le cache du navigateur ou en lançant une nouvelle session du navigateur.

AEM tente également de mettre en cache les bibliothèques clientes pour des raisons de performances. Il arrive parfois qu’à la suite d’un déploiement du code, les fichiers plus anciens soient diffusés. Vous pouvez invalider manuellement AEM cache de bibliothèque cliente à l’aide de l’outil [](http://localhost:4502/libs/granite/ui/content/dumplibs.rebuild.html)Reconstruire les bibliothèques clientes. *La méthode d’invalidation des caches est conseillée si vous pensez que AEM a mis en cache une ancienne version d’une bibliothèque cliente. La reconstruction des bibliothèques est inefficace et prend du temps.*

### Congratulations {#congratulations}

Vous venez de mettre en forme votre premier composant AEM CIF Core !

### Bonus Challenge {#bonus-challenge}

Utilisez le système [Style](https://docs.adobe.com/content/help/fr-FR/experience-manager-65/developing/components/style-system.html) AEM pour créer deux styles qui peuvent être activés/désactivés par un auteur de contenu. [Le développement avec le système](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/style-system.html) de style comprend des étapes détaillées et des informations sur la façon d&#39;y parvenir.

![Bonus Challenge - Système de style](/help/commerce-cloud/assets/style-cif-component/bonus-challenge.png)

## Ressources supplémentaires {#additional-resources}

* [Archétype CIF AEM](https://github.com/adobe/aem-cif-project-archetype)

* [Composants principaux AEM CIF](https://github.com/adobe/aem-core-cif-components)

* [Configuration d’un Environnement de développement AEM local](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html)

* [Bibliothèques côté client](https://docs.adobe.com/content/help/en/experience-manager-65/developing/introduction/clientlibs.html)
* [Prise en main du AEM Sites](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)

* [Développer avec le système de style](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/style-system.html)
