---
title: Activation des composants principaux de Forms adaptatif dans l’environnement de développement as a Cloud Service et local d’AEM Forms
seo-title: Step-by-Step Guide for enabling Adaptive Forms Core Components on AEM Forms as a Cloud Service and local development environment
description: Découvrez comment activer les composants principaux de Forms adaptatif sur AEM Forms as a Cloud Service avec notre guide détaillé. Notre tutoriel vous guide tout au long du processus, ce qui facilite l’activation de cette puissante fonctionnalité pour votre environnement AEM Forms.
seo-description: Learn how to enable Adaptive Forms Core Components on AEM Forms as a Cloud Service with our step-by-step guide. Our tutorial walks you through the process, making it easy to enable this powerful feature for your AEM Forms environment.
contentOwner: Khushwant Singh
docset: CloudService
role: Admin
source-git-commit: 8c125d834ebfff5601f56646d59ce00a80fcc0ba
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 11%

---


# Activation des composants principaux de Forms adaptatif dans l’environnement de développement as a Cloud Service et local d’AEM Forms {#enable-headless-adaptive-forms-on-aem-forms-cloud-service}

L’activation des composants principaux des formulaires adaptatifs sur AEM Forms as a Cloud Service vous permet de commencer à créer, à publier et à diffuser des formulaires adaptatif et des formulaires découplés basés sur les composants principaux à l’aide de vos instances Cloud Service d&#39;AEM Forms sur plusieurs canaux. Vous avez besoin de l’environnement de composants principaux de Forms adaptatif activé pour utiliser le Forms adaptatif sans affichage.

## Considérations

* Lorsque vous créez un programme AEM Forms as a Cloud Service, [Les composants principaux de Forms adaptatif et Forms adaptatif sans affichage sont déjà activés pour votre environnement.](#are-adaptive-forms-core-components-enabled-for-my-environment).

* Si vous disposez d’un programme Forms as a Cloud Service plus ancien où les composants principaux sont [not enabled](#enable-components), vous pouvez [ajout de dépendances des composants principaux Forms adaptatifs](#enable-headless-adaptive-forms-for-an-aem-forms-as-a-cloud-service-environment) dans votre référentiel as a Cloud Service AEM et déployez le référentiel dans vos environnements de Cloud Service pour activer le Forms adaptatif sans affichage.

* Si votre environnement de Cloud Service existant propose une option pour [Création d’un Forms adaptatif basé sur les composants principaux](creating-adaptive-form-core-components.md), les composants principaux de Forms adaptatif et les Forms adaptatifs sans affichage sont déjà activés pour votre environnement et vous pouvez utiliser les Forms adaptatifs basés sur les composants principaux en tant que formulaires sans interface pour les canaux tels que les canaux mobiles, web, les applications natives et les services qui nécessitent une représentation sans interface de Forms adaptatif.


## Activation des composants principaux de Forms adaptatif et de Forms adaptatif sans affichage {#enable-headless-forms}

Effectuez les étapes suivantes, dans l’ordre indiqué, pour activer les composants principaux de Forms adaptatif et le Forms adaptatif sans affichage pour un environnement as a Cloud Service AEM Forms


![Activation des composants principaux et des formulaires adaptatifs sans en-tête](/help/forms/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service.png)


## 1. Cloner votre référentiel Git as a Cloud Service AEM Forms {#clone-git-repository}

1. Connectez-vous à [Cloud Manager](https://my.cloudmanager.adobe.com/) et sélectionnez votre organisation et votre programme.

1. Accédez au **Pipelines** de votre **Aperçu du programme** , cliquez sur la page **Accès aux informations sur le référentiel** pour accéder à votre référentiel Git et le gérer. La page comprend les informations suivantes :

   * URL du référentiel Git de Cloud Manager.
   * Informations d’identification du nom d’utilisateur Git Repository (nom d’utilisateur et mot de passe).

   Cliquez sur **Générer un mot de passe** pour afficher ou générer le mot de passe.

1. Ouvrez le terminal ou l’invite de commande sur votre ordinateur local et exécutez la commande suivante :

   ```Shell
   git clone [Git Repository URL]
   ```

   Lorsque vous y êtes invité, saisissez les informations d’identification. Le référentiel est cloné sur votre ordinateur local.


## 2. Ajout de dépendances des composants principaux Forms adaptatifs à votre référentiel Git {#add-adaptive-forms-core-components-dependencies}

1. Ouvrez votre dossier Git Repository dans un éditeur de code de texte brut. Par exemple, VS Code.
1. Ouvrez le fichier `[AEM Repository Folder]\pom.xml` en mode d’édition.
1. Remplacer les versions de la fonction `core.forms.components.version`, `core.forms.components.af.version` et `core.wcm.components.version` composants avec les versions spécifiées dans [documentation des composants principaux](https://github.com/adobe/aem-core-forms-components). Si le composant n’existe pas, ajoutez ces composants.

   ```XML
   <!-- Replace the version with the latest released version at https://github.com/adobe/aem-core-forms-components/tags -->
   
   <properties>
       <core.wcm.components.version>2.22.10</core.wcm.components.version>
       <core.forms.components.version>2.0.18</core.forms.components.version>
       <core.forms.components.af.version>2.0.18</core.forms.components.af.version>
   </properties>
   ```

   ![Mentionner la dernière version des composants principaux Forms](/help/forms/assets/latest-forms-component-version.png)

1. Dans la section dependencies de la variable `[AEM Repository Folder]\pom.xml` , ajoutez les dépendances suivantes, puis enregistrez le fichier.

   ```XML
       <!-- WCM Core Component Examples Dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <version>${core.wcm.components.version}</version>
               <type>zip</type>
           </dependency>    
           <!-- End of WCM Core Component Examples Dependencies -->
           <!-- Forms Core Component Dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
   <!-- End of AEM Forms Core Component Dependencies -->
   ```

1. Ouvrez le fichier `[AEM Repository Folder]/all/pom.xml` pour le modifier. Ajoutez les dépendances suivantes dans la variable `<embeddeds>` et enregistrez le fichier.

   ```XML
   <!-- WCM Core Component Examples Dependencies -->
   
   <!-- inside plugin config of filevault-package-maven-plugin -->  
   <!-- embed wcm core components examples artifacts -->
   
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.config</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <!-- embed forms core components artifacts -->
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   ```

   >[!NOTE]
   >
   >
   >  Remplacer `${appId}` avec votre appId.
   >
   >  Pour rechercher votre `${appId}`, dans la variable `[AEM Repository Folder]/all/pom.xml` , recherchez les `-packages/application/install` terme. Le texte situé avant la balise `-packages/application/install` est votre terme `${appId}`. Par exemple, le code suivant : `myheadlessform` is `${appId}`.
   >
   >   ```
   >             <embedded>
   >                     <groupId>com.myheadlessform</groupId>
   >                     <artifactId>myheadlessform.ui.apps<artifactId>
   >                     <type>zip</type>
   >                   <target>/apps/myheadlessform-packages/application install</target>
   >             </embedded>
   >   ```

1. Dans le `<dependencies>` de la section `[AEM Repository Folder]/all/pom.xml` , ajoutez les dépendances suivantes, puis enregistrez le fichier :

   ```XML
           <!-- Other existing dependencies -->
           <!-- wcm core components examples dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <type>zip</type>
               </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
           </dependency>
               <!-- forms core components dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
           </dependency>
               <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
           </dependency>
   ```

1. Ouvrez le `[AEM Repository Folder]/ui.apps/pom.xml` pour édition. Ajoutez la variable `af-core bundle` et enregistrez le fichier.

   ```XML
       <dependency>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       </dependency>
   ```

   >[!NOTE]
   >
   >Assurez-vous que les artefacts de composants principaux des formulaires adaptatifs suivants ne sont pas inclus dans votre projet.
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-apps</artifactId>`
   >
   > `</dependency>`
   >
   > et
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-core</artifactId>`
   >
   > `</dependency>`


1. Enregistrez et fermez le fichier.

## 3. Créez et déployez le code mis à jour

Déployez le code mis à jour dans vos environnements de développement et de Cloud Service locaux afin d’activer les composants principaux sur les deux environnements :

* [Créer et déployer du code mis à jour dans un environnement de développement local (AEM SDK as a Cloud Service)](#core-components-on-aem-forms-local-sdk)

* [Créer et déployer du code mis à jour dans un environnement AEM Forms as a Cloud Service](#core-components-on-aem-forms-cs)

### Créer et déployer du code mis à jour dans un environnement de développement local {#core-components-on-aem-forms-local-sdk}

1. Ouvrez l’invite de commande ou le terminal.

1. Accédez au répertoire racine de votre projet Git Repository.

1. Exécutez la commande suivante pour créer le module pour votre environnement :

   ```Shell
       mvn clean install
   ```



   Une fois le module créé, vous pouvez le trouver à l’adresse [Dossier Du Référentiel Git]\all\target\[appid].all-[version].zip

1. Utilisez la variable [Gestionnaire de modules](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=fr) pour déployer le [AEM archetype Project Folder]\all\target\[appid].all-[version]Package .zip sur l’environnement de développement local.


### Créer et déployer du code mis à jour dans un environnement AEM Forms as a Cloud Service {#core-components-on-aem-forms-cs}

1. Ouvrez le terminal ou l’invite de commande.
1. Accédez à `[AEM Repository Folder]` et exécutez les commandes suivantes dans l’ordre indiqué.

   ```Shell
    git add pom.xml
    git add all/pom.xml
    git add ui.apps/pom.xml
    git commit -m "Added dependencies for Adaptive Forms Core Components"
    git push origin
   ```

1. Une fois les fichiers validés dans le référentiel Git, [Exécution du pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=fr).

   Une fois l’exécution du pipeline terminée, les composants principaux de Forms adaptatif sont activés pour l’environnement correspondant. En outre, un modèle Forms adaptatif (composants principaux) et un thème Canevas 3.0 sont ajoutés à votre environnement Forms as a Cloud Service, ce qui vous permet de personnaliser et de créer des composants principaux basés sur Forms adaptatif.


## Foire aux questions {#faq}

### Que sont les composants principaux ? {#core-components}

Le [Composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr) sont un ensemble de composants WCM (Web Content Management, gestion de contenu web) normalisés permettant d’AEM accélérer le temps de développement et de réduire les coûts de maintenance de vos sites web.

### Quelles sont toutes les fonctionnalités ajoutées lors de l’activation des composants principaux ? {#core-components-capabilities}

Lorsque les composants principaux de Forms adaptatif sont activés pour votre environnement, un modèle de formulaire adaptatif basé sur les composants principaux vierge et le thème Canevas 3.0 sont ajoutés à votre environnement. Après avoir activé les composants principaux de Forms adaptatif pour votre environnement, vous pouvez :

* [Création d’un Forms adaptatif basé sur des composants principaux](/help/forms/creating-adaptive-form-core-components.md).
* [Création de modèles de formulaires adaptatifs basés sur des composants principaux](/help/forms/template-editor.md).
* [Création de thèmes personnalisés pour les modèles de formulaires adaptatifs basés sur les composants principaux](/help/forms/using-themes-in-core-components.md).
* [Diffuser les représentations JSON du formulaire adaptatif basé sur les composants principaux aux canaux tels que les applications mobiles, web, natives et les services qui nécessitent une représentation sans tête d’un formulaire](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=fr).

### Les composants principaux de Forms adaptatif sont-ils activés pour mon environnement ? {#enable-components}

Pour vérifier que les composants principaux de Forms adaptatif sont activés pour votre environnement :

1. [Clonage de votre référentiel as a Cloud Service AEM Forms](#1-clone-your-aem-forms-as-a-cloud-service-git-repository).

1. Ouvrez le `[AEM Repository Folder]/all/pom.xml` du référentiel Git de votre Cloud Service AEM Forms.

1. Recherchez les dépendances suivantes :

   * core-forms-components-af-core
   * core-forms-components-core
   * core-forms-components-apps
   * core-forms-components-af-apps
   * core-forms-components-examples-apps
   * core-forms-components-examples-content

   ![localisez l’artefact core-forms-components-af-core dans all/pom.xml](/help/forms/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service-locate-core-af-artifact.png)

   Si les dépendances existent, les composants principaux de Forms adaptatif sont activés pour votre environnement.

