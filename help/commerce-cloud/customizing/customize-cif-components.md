---
title: Personnalisation des composants principaux CIF
description: Personnalisation des composants principaux CIF
translation-type: tm+mt
source-git-commit: c3cf472f5e207e7ca0788dc3e42105868d9bdf00
workflow-type: tm+mt
source-wordcount: '2520'
ht-degree: 2%

---


# Personnalisation des composants principaux CIF AEM {#customize-cif-components}

[AEM CIF Core Components](https://github.com/adobe/aem-core-cif-components) fournit un ensemble standard de composants Commerce qui peuvent être utilisés pour accélérer un projet qui intègre des solutions d&#39;Adobe Experience Manager (AEM) et de Magento. Ces composants sont prêts pour la production et peuvent être [facilement mis en forme avec CSS](style-cif-component.md). De nombreuses implémentations voudront également étendre ces composants pour répondre aux besoins spécifiques de l&#39;entreprise.

Dans ce tutoriel, nous passerons en revue plusieurs points d&#39;extension fournis par AEM CIF Core Components et AEM en général. Pour ce faire, nous étendrons les fonctionnalités du composant [Product Teaser](https://github.com/adobe/aem-core-cif-components/tree/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/productteaser/v1/productteaser) afin d’inclure la possibilité de générer une bannière &quot;Nouveau&quot;. Les auteurs de contenu pourront activer la bascule de cette bannière et déterminer la durée d’affichage de la bannière. L’&quot;âge&quot; du produit sera déterminé en fonction de la date de création dans le catalogue du Magento. Une fois qu’un produit a un certain nombre de jours, la bannière &quot;Nouveau&quot; doit disparaître automatiquement.

![Nouvelle bannière étendue](/help/commerce-cloud/assets/customize-cif-components/new-banner-productteaser.png)

## Conditions préalables {#prerequisites}

Les outils et technologies suivants sont nécessaires :

* [Java 11](https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html)
* [Apache Maven](https://maven.apache.org/) (version 3.3.9 ou ultérieure)
* [AEM Cloud SKD avec module complémentaire CIF](../develop.md)
* Magento compatible avec les composants principaux CIF

Il est recommandé de consulter le contenu suivant avant de suivre ce didacticiel :

* [Présentation du cadre d&#39;intégration commerciale sur l&#39;AEM en tant que Cloud Service](/help/commerce-cloud/overview.md)
* [Style AEM CIF Core Components - Didacticiel](style-cif-component.md)

## Projet de démarrage

Nous avons fourni un projet de démarrage à utiliser avec ce tutoriel. Le projet a été généré à l&#39;aide de la version [v0.7.0](https://github.com/adobe/aem-cif-project-archetype/releases/tag/cif-project-archetype-0.7.0) de l&#39;archétype du projet CIF. Il est recommandé de toujours utiliser la [dernière version](https://github.com/adobe/aem-cif-project-archetype/releases/latest) de l&#39;archétype lors du démarrage d&#39;un nouveau projet.

1. Téléchargez le projet de démarrage [**acme-store.zip **](/help/commerce-cloud/assets/customize-cif-components/acme-store.zip)sur votre bureau.

1. Décompressez **acme-store.zip** et vous devriez voir la structure de dossiers suivante :

   ```plain
   /acme-store
      /ui.content
      /ui.apps
      /samplecontent
      /core
      /all
      + pom.xml
      + README.md
   ```

1. Ouvrez une nouvelle fenêtre de terminal et créez et déployez le projet sur une instance locale d&#39;AEM ;

   ```shell
   $ cd acme-store/
   $ mvn clean install -PautoInstallAll
   ```

1. Ajoutez les configurations OSGi nécessaires pour connecter votre instance AEM à une instance de Magento ou ajoutez les configurations au projet nouvellement créé.

1. A ce stade, vous devez disposer d&#39;une version fonctionnelle d&#39;une vitrine connectée à une instance de Magento. Accédez à la page `US` > `Home` à l’adresse suivante : [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html)

   Vous devriez voir que la vitrine utilise actuellement le thème Venia. En développant le menu principal de la vitrine, vous devriez voir différentes catégories, indiquant que le Magento de connexion fonctionne.

   ![Vitrine configurée avec le thème Venia](/help/commerce-cloud/assets/customize-cif-components/acme-store-configured.png)

## Auteur du produit Teaser {#author-product-teaser}

Nous étendrons le composant Teaser produit tout au long de ce tutoriel. Dans un premier temps, nous allons ajouter une nouvelle instance de Product Teaser à la Page d&#39;accueil afin de comprendre la fonctionnalité de base.

1. Accédez à la **Page d&#39;accueil** du site : [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html)

1. Insérez un nouveau composant **Produit Teaser** dans le conteneur de mise en page principal de la page.

   ![Insérer un produit Teaser](/help/commerce-cloud/assets/customize-cif-components/product-teaser-add-component.png)

1. Développez le panneau latéral (s’il n’est pas déjà activé) et basculez la liste déroulante de recherche de ressources sur **Produits**. Ceci devrait afficher une liste de produits disponibles à partir d’une instance de Magento connectée. Sélectionnez un produit et **faites-le glisser** sur le composant **Produit Teaser** de la page.

   ![Faire glisser + déposer le produit Teaser](/help/commerce-cloud/assets/customize-cif-components/drag-drop-product-teaser.png)

   > Remarque : vous pouvez également configurer le produit affiché en configurant le composant à l’aide de la boîte de dialogue (en cliquant sur l’icône de *clé à molette* ).

1. Vous devriez maintenant voir un produit affiché par le Teaser de produit. Le nom du produit et le prix du produit sont des attributs par défaut affichés.

   ![Produit Teaser - style par défaut](/help/commerce-cloud/assets/customize-cif-components/product-teaser-default-style.png)

## Personnalisation de l&#39;annotation du produit Teaser {#customize-markup-product-teaser}

Une extension courante des composants AEM consiste à modifier l’annotation générée par le composant. Pour ce faire, il doit remplacer le script [](https://docs.adobe.com/content/help/fr-FR/experience-manager-htl/using/overview.html) HTL utilisé par le composant pour effectuer le rendu de son balisage. HTML Template Language (HTL) est un langage de modèle léger que AEM composants utilisent pour générer dynamiquement des balises en fonction du contenu créé, ce qui permet de réutiliser les composants. Le produit Teaser, par exemple, peut être réutilisé plusieurs fois pour afficher différents produits.

Dans notre cas, nous voulons rendre une bannière sur le teaser pour indiquer que le produit est &quot;nouveau&quot; et a été récemment ajouté au catalogue. Le modèle de conception permettant de [personnaliser l’annotation](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/customizing.html#customizing-the-markup) d’un composant est en fait standard pour tous les composants AEM, et pas seulement pour les composants CIF Core AEM.

Utilisez l&#39;IDE de votre choix pour [ouvrir le projet de démarrage téléchargé](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html#set-up-an-integrated-development-environment) au début du didacticiel.

1. Recherchez et développez le module **ui.apps** et développez la hiérarchie de dossiers pour : `ui.apps/src/main/content/jcr_root/apps/acme/components/commerce/productteaser` et inspecter le `.content.xml` dossier.

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
       jcr:description="Product Teaser Component"
       jcr:primaryType="cq:Component"
       jcr:title="Product Teaser"
       sling:resourceSuperType="core/cif/components/commerce/productteaser/v1/productteaser"
       componentGroup="acme"/>
   ```

   Ci-dessus, la définition de composant pour le composant Teaser du produit dans notre projet. Notez la propriété `sling:resourceSuperType="core/cif/components/commerce/productteaser/v1/productteaser"`. Il s&#39;agit d&#39;un exemple de création d&#39;un composant [](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/get-started/using.html#create-proxy-components)Proxy. Au lieu de copier et de coller tous les scripts HTML de Product Teaser à partir des composants principaux CIF AEM, nous pouvons utiliser le `sling:resourceSuperType` pour hériter de toutes les fonctionnalités.

1. Ouvrez un nouveau navigateur et accédez à [CRXDE-Lite](http://localhost:4502/crx/de/index.jsp#/apps/core/cif/components/commerce/productteaser/v1/productteaser) dans AEM. Développez l&#39;arborescence pour vue du `productteaser` composant sous : `/apps/core/cif/components/commerce/productteaser/v1/productteaser`:

   ![CRXDE Lite Product Teaser](/help/commerce-cloud/assets/customize-cif-components/crxde-productteaser.png)

   Il s&#39;agit de la définition complète du composant Teaser de produit.

1. Revenez à votre IDE et au projet Acme Store. Créez un nouveau fichier nommé `productteaser.html` sous `ui.apps/src/main/content/jcr_root/apps/acme/components/commerce/productteaser`.

1. Copiez le contenu de `productteaser.html` CRXDE-Lite [et collez-le dans le projet Acme-Store du](http://localhost:4502/crx/de/index.jsp#/apps/core/cif/components/commerce/productteaser/v1/productteaser/productteaser.html) `productteaser.html` fichier que vous venez de créer.

   ![Remplacement du code html du produit Teaser](/help/commerce-cloud/assets/customize-cif-components/productteaser-html-overwrite.png)

1. Dans le projet Acme-Store, modifiez le `productteaser.html` fichier et insérez une nouvelle balise div qui représente un badge au-dessus de l’annotation d’image du produit :

   ```html
   ...
   <div data-sly-test.isvalid="${product.url}" class="item__root" data-cmp-is="productteaser">
       <!-- Add Badge -->
       <div class="item__badge">
           <span>New</span>
       </div>
       <!-- end add badge -->
       <a class="item__images" href=${product.url}>
           <img class="item__image" width="100%" height="100%"
                   src="${product.image}" alt="${product.image}"/>
       </a>
       <a class="item__name" href=${product.url}><span>${product.name}</span></a>
       <div class="item__price">
           <span> ${product.formattedPrice} </span>
       </div>
       <sly data-sly-call="${actionsTpl.actions @ product=product}"></sly>
   </div>
   ```

1. Déployez le code mis à jour sur l&#39;instance locale de AEM en utilisant vos compétences d&#39;expert ou [les fonctionnalités de votre IDE](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html#set-up-an-integrated-development-environment):

   ```shell
   $ cd ui.apps
   $ mvn -PautoInstallPackage clean install
   ```

1. Dans le navigateur, revenez à la [page d&#39;accueil du magasin avant](http://localhost:4502/editor.html/content/acme/us/en.html) dans AEM. Actualisez et vous devriez voir qu’une &quot;nouvelle&quot; bannière s’affiche dans le coin supérieur droit du composant.

   ![Nouvelle bannière étendue](/help/commerce-cloud/assets/customize-cif-components/new-banner-productteaser.png)

   Actuellement, il n&#39;y a aucune logique derrière le moment où la bannière sera affichée. Dans les exercices suivants, nous corrigerons cela.

   > Notez que la page CSS permettant de générer la bannière a été fournie dans le cadre du projet de démarrage et se trouve à l’adresse suivante : `ui.apps/../apps/acme/clientlibs/theme/components/productteaser/teaser.css`. Pour plus d&#39;informations, consultez le didacticiel [](style-cif-component.md)Styling CIF Core Components.

## Personnalisation de la boîte de dialogue du produit Teaser {#customize-dialog-product-teaser}

Ensuite, nous allons personnaliser la boîte de dialogue du composant Teaser de produit pour permettre à un auteur de déterminer la période pour laquelle un produit est considéré comme &quot;nouveau&quot; et si la bannière doit être affichée. Pour ce faire, nous [personnaliserons la boîte de dialogue](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/customizing.html#customizing-dialogs) du produit Teaser dans le cadre du projet Acme Store.

1. Ouvrez le projet Acme Store dans l’IDE de votre choix et accédez à `ui.apps/src/main/content/jcr_root/apps/acme/components/commerce/productteaser`.

1. Sous le `productteaser` dossier, ajoutez un nouveau dossier nommé `_cq_dialog`. Ajoutez un nouveau fichier dans le `_cq_dialog` dossier nommé `.content.xml`. Vous devez maintenant avoir la structure de fichiers suivante :

   ```plain
   ../acme
       /components
           /commerce
               /productteaser
                  /_cq_dialog
                     + .content.xml
                  /_cq_template
                  + .content.xml
                  + productteaser.html
   ```

1. Mettez à jour `_cq_dialog/.content.xml` avec le code XML suivant :

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" 
       xmlns:cq="http://www.day.com/jcr/cq/1.0" 
       xmlns:jcr="http://www.jcp.org/jcr/1.0" 
       xmlns:nt="http://www.jcp.org/jcr/nt/1.0" 
       jcr:primaryType="nt:unstructured" 
       jcr:title="My Product Teaser" 
       sling:resourceType="cq/gui/components/authoring/dialog" 
       trackingFeature="cif-core-components:productteaser:v1">
       <content jcr:primaryType="nt:unstructured" 
           sling:resourceType="granite/ui/components/coral/foundation/container">
           <items jcr:primaryType="nt:unstructured">
               <tabs jcr:primaryType="nt:unstructured" 
                   sling:resourceType="granite/ui/components/coral/foundation/tabs" 
                   maximized="{Boolean}true">
                   <items jcr:primaryType="nt:unstructured">
                       <badge jcr:primaryType="nt:unstructured" 
                           jcr:title="Badge" 
                           sling:resourceType="granite/ui/components/coral/foundation/container" 
                           margin="{Boolean}true">
                           <items jcr:primaryType="nt:unstructured">
                               <columns jcr:primaryType="nt:unstructured" 
                                   sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns" 
                                   margin="{Boolean}true">
                                   <items jcr:primaryType="nt:unstructured">
                                       <column jcr:primaryType="nt:unstructured" 
                                           sling:resourceType="granite/ui/components/coral/foundation/container">
                                           <items jcr:primaryType="nt:unstructured">
                                               <badge jcr:primaryType="nt:unstructured" 
                                                   sling:resourceType="granite/ui/components/coral/foundation/form/checkbox" 
                                                   text="Display 'New' badge" 
                                                   value="true" 
                                                   uncheckedValue="false" 
                                                   name="./badge" />
                                               <age jcr:primaryType="nt:unstructured" 
                                                   sling:resourceType="granite/ui/components/coral/foundation/form/numberfield" 
                                                   fieldDescription="The maximum age in days the 'new' badge should be shown" 
                                                   fieldLabel="Max Product Age" 
                                                   name="./age"
                                                   min="{Long}0" 
                                                   value="10" />
                                               <ageTypeHint jcr:primaryType="nt:unstructured" 
                                                   sling:resourceType="granite/ui/components/foundation/form/hidden" 
                                                   ignoreData="{Boolean}true" 
                                                   name="./age@TypeHint" 
                                                   value="Long" />
                                           </items>
                                       </column>
                                   </items>
                               </columns>
                           </items>
                       </badge>
                   </items>
               </tabs>
           </items>
       </content>
   </jcr:root>
   ```

   Au-dessus, nous avons ajouté 2 champs supplémentaires dans un nouvel onglet et un seul champ masqué.

   1. Case à cocher pour afficher le badge &quot;Nouveau&quot;
   2. Champ Numéro permettant de définir l’âge du produit max.
   3. Champ masqué pour vous assurer que l’âge maximum du produit est enregistré en tant que long (voir [@TypeHint](https://sling.apache.org/documentation/bundles/manipulating-content-the-slingpostservlet-servlets-post.html) pour plus d’informations).

   Les boîtes de dialogue définies comme faisant partie d&#39;un composant proxy héritent de tous les champs de boîte de dialogue existants avec une fonctionnalité appelée [Sling Resource Merger](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/sling-resource-merger.html). Par conséquent, nous n&#39;avons pas à redéfinir les champs existants qui font partie du produit Teaser.

1. Mettez à jour `productteaser.html` et ajoutez un `data-sly-test` à la page `<div>` pour le badge. Il s’agira d’un test simple pour décider de rendre le badge si l’utilisateur a coché &quot;true&quot;.

   ```html
       ...
       <div data-sly-test.isvalid="${product.url}" class="item__root" data-cmp-is="productteaser">
   
           <!--/* add test to see if properties.badge equals true */-->
           <div data-sly-test="${properties.badge == 'true'}" class="item__badge">
               <span>New</span>
           </div>
   ...
   ```

1. Déployez le code mis à jour sur l&#39;instance locale de AEM à l&#39;aide des fonctionnalités de votre IDE ou en utilisant vos compétences d&#39;expert :

   ```shell
   $ cd ui.apps
   $ mvn -PautoInstallPackage clean install
   ```

1. Revenez au composant Teaser produit et cliquez sur l&#39;icône de *clé à molette* pour ouvrir la boîte de dialogue. Vous devriez maintenant voir un onglet pour **Badge** avec deux champs supplémentaires. La mise à jour de ces champs conserve les valeurs à AEM. Vous devriez pouvoir activer/désactiver le badge à l’aide de la case à cocher :

   ![Basculer le badge](/help/commerce-cloud/assets/customize-cif-components/toggle-badge-checkbox.gif)

   L’auteur peut ainsi contrôler le moment où le badge apparaît. Cependant, il serait idéal que le badge disparaisse automatiquement une fois que le produit a atteint un certain âge dans la journée en fonction de l&#39;entrée pour l&#39;âge **** maxi du produit. Pour cela, nous devrons mettre en oeuvre une logique d&#39;arrière-plan.

## Mise à jour du modèle Sling pour le produit Teaser {#updating-sling-model-product-teaser}

Ensuite, nous étendrons la logique métier de Product Teaser en implémentant un modèle Sling. [Les modèles](https://sling.apache.org/documentation/bundles/models.html)Sling sont des &quot;POJO&quot; pilotés par les annotations (objets Java standard) qui implémentent toute logique métier nécessaire au composant. Les modèles Sling sont utilisés conjointement avec les scripts HTL dans le cadre du composant. Nous suivrons le modèle de [délégation pour les modèles](https://github.com/adobe/aem-core-wcm-components/wiki/Delegation-Pattern-for-Sling-Models) Sling afin que nous puissions simplement étendre certaines parties du modèle existant de Teaser produit.

Les modèles Sling sont implémentés en tant que Java et se trouvent dans le module **principal** du projet généré.

1. Ouvrez le projet Acme Store dans l’IDE de votre choix et naviguez sous le module **principal** pour : `core/src/main/java/com/acme/cif/core/models/MyProductTeaser.java`. **MyProductTeaser.java** est une interface Java que nous avons précréée qui étend l&#39;interface CIF **ProductTeaser** .

1. Ouvrez ensuite le fichier **MyProductTeaserImpl.java** situé à l’emplacement suivant : `core/src/main/java/com/acme/cif/core/models/MyProductTeaserImpl.java`. `MyProductTeaserImpl` est la classe d’implémentation de l’interface `MyProductTeaser`.

   En utilisant le modèle de [délégation pour les modèles](https://github.com/adobe/aem-core-wcm-components/wiki/Delegation-Pattern-for-Sling-Models) Sling, nous pouvons référencer la `ProductTeaser` classe via la propriété `sling:resourceSuperType` :

   ```java
   @Self
   @Via(type = ResourceSuperType.class)
   private ProductTeaser productTeaser;
   ```

   Pour toutes les méthodes que nous ne voulons pas remplacer ou modifier, nous pouvons simplement renvoyer la valeur `ProductTeaser` renvoyée :

   ```java
   @Override
   public String getImage() {
       return productTeaser.getImage();
   }
   ```

1. Un des points d&#39;extension supplémentaires fournis par AEM CIF Core Components est le `AbstractProductRetriever` qui nous permet d&#39;accéder à des attributs de produits spécifiques. Ajoutez la méthode suivante pour initialiser la `AbstractProductRetriever` méthode dans la `init()` méthode :

   ```java
   import javax.annotation.PostConstruct;
   ...
   @Model(adaptables = SlingHttpServletRequest.class, adapters = MyProductTeaser.class, resourceType = MyProductTeaserImpl.RESOURCE_TYPE)
   public class MyProductTeaserImpl implements MyProductTeaser {
       ...
       private AbstractProductRetriever productRetriever;
   
       /* add this method to intialize the proudctRetriever */
       @PostConstruct
       public void initModel() {
           productRetriever = productTeaser.getProductRetriever();
   
       }
   ...
   ```

1. Permet de tester ces modifications en modifiant le prix formaté et en remplaçant la logique dans `getFormattedPrice()`. Effectuez les mises à jour suivantes afin de formater explicitement le prix en fonction des paramètres régionaux allemands. (ou choisir un autre pays !)

   ```java
           import java.util.Locale;
           import java.text.NumberFormat;
            ...
   
               @Override
                   public String getFormattedPrice() 
                   {
                   //return productTeaser.getFormattedPrice();
                   NumberFormat germanCurrencyFormat = NumberFormat.getCurrencyInstance(Locale.GERMANY);
                   Double price =  productRetriever.fetchProduct().getPrice().getRegularPrice().getAmount().getValue();
                       if(price != null) 
                       {
                           return germanCurrencyFormat.format(price);
                       }
                   return null;
                   }
   ```

   Notez comment l&#39; `productRetriever` objet nous donne accès à l&#39; `ProductInterface` objet par le biais de la `fetchProduct()` méthode. Vous pouvez voir toutes les méthodes [disponibles ici](https://github.com/adobe/commerce-cif-magento-graphql/blob/master/src/main/java/com/adobe/cq/commerce/magento/graphql/ProductInterface.java).

   > Note* La modification de la langue en allemand est juste un exemple amusant pour voir le remplacement. En réalité, ProductTeaser utilise les paramètres régionaux de la [page pour déterminer le format](https://github.com/adobe/aem-core-cif-components/blob/master/bundles/core/src/main/java/com/adobe/cq/commerce/core/components/internal/models/v1/productteaser/ProductTeaserImpl.java#L173).

1. Ensuite, nous devons mettre à jour le fichier **productteaser.html** dans le module **ui.apps** pour référencer notre nouveau modèle Sling à l’adresse suivante : `com.acme.cif.core.models.MyProductTeaser`.

   ```diff
     <!--/* productteaser.html - change the use.product to point to MyProductTeaser */-->
     <sly data-sly-use.clientlib="/libs/granite/sightly/templates/clientlib.html"
   -  data-sly-use.product="com.adobe.cq.commerce.core.components.models.productteaser.ProductTeaser"
   +  data-sly-use.product="com.acme.cif.core.models.MyProductTeaser"
      data-sly-use.actionsTpl="actions.html">
      ...
   ```

   Enregistrez les modifications dans `productteaser.html`.

1. Déployez la base de code sur l’instance locale de AEM. Comme des modifications ont été apportées à la fois aux **ui.apps** et aux modules **principaux** , créez et déployez le projet à partir de la racine :

   ```shell
   $ cd acme-store
   $ mvn -PautoInstallPackage clean install
   ```

1. Ouvrez un navigateur et accédez à : [http://localhost:4502/system/console/status-slingmodels](http://localhost:4502/system/console/status-slingmodels). Cette console affiche tous les modèles Sling enregistrés dans le système. Vérification de Doublon pour vérifier que MyTeaserModelImpl a été déployé et est mappé correctement. Vous devriez pouvoir voir quelque chose comme :

   ```plain
   com.acme.cif.core.models.MyProductTeaserImpl - acme/components/commerce/productteaser
   ```

1. Enfin, accédez à l’emplacement où vous avez créé le composant Produit Teaser et vous devriez maintenant voir le prix au format allemand :

   ![Format de prix mis à jour](/help/commerce-cloud/assets/customize-cif-components/german-currency-update.png)

## Implémenter la logique isShowBadge {#implement-isshowbadge}

Maintenant que nous avons eu la possibilité de tester le remplacement des méthodes du modèle Sling, nous allons mettre en oeuvre la logique pour quand afficher le &quot;nouveau&quot; badge.

1. Revenez à votre IDE et ouvrez le fichier **MyProductTeaser.java** à l&#39;adresse : `core/src/main/java/com/acme/cif/core/models/MyProductTeaser.java`.

1. Ajoutez une nouvelle méthode `isShowBadge()` à l’interface :

   ```java
   @ProviderType
   public interface MyProductTeaser extends ProductTeaser {
       // Extend the existing interface with the additional properties which you
       // want to expose to the HTL template.
       public Boolean isShowBadge();
   }
   ```

   C&#39;est une nouvelle méthode que nous allons introduire pour encapsuler la logique de montrer ou non le badge.

1. Ensuite, rouvrez **MyProductTeaserImpl.java** à `core/src/main/java/com/acme/cif/core/models/MyProductTeaserImpl.java`.

1. La logique du délai d&#39;affichage du &quot;nouveau&quot; badge dépend de l&#39; `created_at` attribut du produit. Pour avoir accès à cet attribut, nous devons étendre la requête **GraphQL** exécutée par ProductTeaser. Pour ce faire, nous pouvons mettre à jour la `init()` méthode dans **MyProductTeaserImpl.java**:

   ```java
   //MyProductTeaserImpl.java
   
   @PostConstruct
   public void initModel() {
       productRetriever = productTeaser.getProductRetriever();
   
       if (productRetriever != null) {
           // Pass your custom partial query to the ProductRetriever. This class will
           // automatically take care of executing your query as soon
           // as you try to access any product property.
           productRetriever.extendProductQueryWith(p ->
               p.addCustomSimpleField("created_at")
           );
       }
   }
   ```

   Ajouter à la `extendProductQueryWith` méthode est un moyen puissant de s&#39;assurer que d&#39;autres attributs de produit sont disponibles pour le reste du modèle. Elle permet également de réduire le nombre de requêtes exécutées.

   >[!NOTE]
   >Dans le code ci-dessus, nous utilisons les`addCustomSimpleField` pour récupérer la `created_at` propriété. Ceci illustre comment vous pouvez requête pour les attributs personnalisés qui font partie du schéma du Magento.
   >
   > Cependant, la `created_at` propriété a été mise en oeuvre dans le cadre de l’interface [](https://github.com/adobe/commerce-cif-magento-graphql/blob/master/src/main/java/com/adobe/cq/commerce/magento/graphql/ProductInterface.java) du produit et il serait préférable de réutiliser la méthode comme suit : `productRetriever.extendProductQueryWith(p -> p.createdAt());`. La plupart des attributs de schéma les plus courants ont été implémentés, utilisez donc uniquement la `addCustomSimpleField` pour les attributs réellement personnalisés.

1. Ensuite, nous allons mettre en oeuvre la `isShowBadge()` méthode :

   ```java
   import java.time.format.DateTimeFormatter;
   import java.util.Locale;
   import java.time.temporal.ChronoUnit;
   
   ...
   
   @Override
   public Boolean isShowBadge() {
        final DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss");
   
        //Look at the checkbox from the dialog to see if we should even attempt to show the badge
        final boolean showBadge = properties.get("badge", false);
        if (showBadge) {
   
            //Look at the numberfield set from the dialog to determine the max "age" in days to compare too
            final int maxAgeProp = properties.get("age", 0);
   
           String createdAtString;
           try {
               //Grab the created_at property from the product
               //Here we show the example of retrieving the attribute as if it was a custom attribute
               // an alternative that would work is productRetriever.fetchProduct().getCreatedAt()
               createdAtString = productRetriever.fetchProduct().getAsString("created_at");
               log.info("***CREATED_AT**** " + createdAtString);
           } catch (SchemaViolationError e) {
               //it is possible that a schema error could be thrown if the attribute is not part of the schema
               log.error("Error determining to showBadge" , e);
               return false;
           }
   
            // Custom code to calc the date difference of the product creation
            // compared to today
           final LocalDate createdAt = LocalDate.parse(createdAtString, formatter);
            if (createdAt != null) {
   
                final long ageInDays = ChronoUnit.DAYS.between(createdAt, LocalDate.now());
                if (ageInDays < maxAgeProp) {
                    return true;
                }
            }
        }
        return false;
    }
   ```

   Dans la méthode ci-dessus, nous vérifions d&#39;abord si l&#39;auteur a activé la fonctionnalité de badge avec la case à cocher. Ensuite, nous lisons la valeur de la propriété `age` qui est définie dans le cadre de la boîte de dialogue et représente le nombre maximal de jours qu&#39;un produit doit avoir avant la disparition de la bannière. Enfin, nous calculons l&#39;âge du produit en fonction de la `created_at` date. Si, après avoir comparé les deux valeurs, nous retournons `true` pour afficher le badge, `false` dans tous les autres cas.

1. Enfin, un autre ajout doit être apporté au `productteaser.html` script pour appeler la `isShowBadge()` méthode. Ouvrez le fichier à `ui.apps/src/main/content/jcr_root/apps/acme/components/commerce/productteaser/productteaser.html`. Effectuez la mise à jour suivante :

   ```diff
   ...
   - <div data-sly-test="${properties.badge == 'true'}" class="item__badge">
   + <div data-sly-test="${product.showBadge}" class="item__badge">
        <span>New</span>
    </div>
   ...
   ```

1. Déployez la base de code sur l’instance locale de AEM. Comme des modifications ont été apportées à la fois aux **ui.apps** et aux modules **principaux** , créez et déployez le projet à partir de la racine :

   ```shell
   $ cd acme-store
   $ mvn -PautoInstallPackage clean install
   ```

1. Revenez à l&#39;AEM et au composant ProductTeaser et testez avec des nombres différents pour afficher l&#39;âge maximum du produit. Selon l&#39;âge du produit, vous devrez peut-être entrer de très grands nombres pour obtenir le badge à afficher.

   ![Âge maxi. de produit 999](/help/commerce-cloud/assets/customize-cif-components/max-age-working.png)

1. Enfin, recherchez les journaux d&#39;AEM pour voir l&#39;instruction de journal saisie à l&#39;étape 5 ci-dessus. Ceci devrait imprimer la valeur de la propriété `created_at` qui provient du Magento. Vous pouvez vue les journaux des AEM en ouvrant le `error.log` fichier. Ce fichier se trouve sous l’ `crx-quickstart/logs/error.log` emplacement où le fichier jar AEM a été installé. Vous pouvez vous attendre à voir un élément de ligne comme suit :

   ```plain
   com.acme.cif.core.models.MyProductTeaser ***CREATED_AT**** 2019-06-05 06:51:33
   ```

   Vous pouvez maintenant vérifier que la logique que nous avons implémentée est correcte !

### Congratulations {#congratulations}

Vous venez de personnaliser votre premier composant AEM CIF ! Téléchargez ici [le package de la solution](/help/commerce-cloud/assets/customize-cif-components/acme-store-solution.zip)terminée.

## Ressources supplémentaires {#additional-resources}

* [Archétype AEM](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html)
* [Composants principaux AEM CIF](https://github.com/adobe/aem-core-cif-components)
* [Personnalisation des composants principaux CIF AEM](https://github.com/adobe/aem-core-cif-components/wiki/Customizing-CIF-Core-Components)
* [Personnalisation des composants principaux](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/customizing.html)
