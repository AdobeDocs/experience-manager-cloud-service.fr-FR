---
title: Comment activer les composants principaux de Forms adaptatif sur AEM Forms as a Cloud Service et l’environnement de développement local ?
description: Découvrez comment activer les composants principaux de Forms adaptatif sur AEM Forms as a Cloud Service.
contentOwner: Khushwant Singh
docset: CloudService
role: Admin, Developer, User
feature: Adaptive Forms, Core Components
exl-id: 32a574e2-faa9-4724-a833-1e4c584582cf
hide: true
hidefromtoc: true
source-git-commit: 0845447c1c4f47b77debd179f24eac95a0d2c2db
workflow-type: tm+mt
source-wordcount: '1113'
ht-degree: 81%

---

# Activer les composants principaux des formulaires adaptatifs {#enable-headless-adaptive-forms-on-aem-forms-cloud-service}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-core-components/enable-adaptive-forms-core-components.html?lang=fr) |
| AEM as a Cloud Service | Cet article |

L’activation des composants principaux de Forms adaptatif sur AEM Forms as a Cloud Service Forms vous permet de commencer à créer, publier et diffuser des Forms adaptatifs et découplés basés sur les composants principaux à l’aide de vos instances AEM Forms Cloud Service sur plusieurs canaux. L’environnement des composants principaux des formulaires adaptatifs doit être activé pour utiliser les formulaires adaptatifs découplés.

## Considérations

* Lorsque vous créez un programme AEM Forms as a Cloud Service, [les composants principaux des formulaires adaptatifs et les formulaires adaptatifs découplés sont déjà activés pour votre environnement](#are-adaptive-forms-core-components-enabled-for-my-environment).

* Si vous disposez d’un programme Forms as a Cloud Service plus ancien où les composants principaux [ne sont pas activés](#enable-components), vous pouvez [ajouter des dépendances de composants principaux de formulaires adaptatifs](#enable-headless-adaptive-forms-for-an-aem-forms-as-a-cloud-service-environment) dans votre référentiel AEM as a Cloud Service, puis déployer le référentiel dans vos environnements de service cloud pour activer les formulaires adaptatifs découplés.

* Si votre environnement de service cloud existant propose une option permettant de [créer des formulaires adaptatifs basés sur les composants principaux](creating-adaptive-form-core-components.md), les composants principaux des formulaires adaptatifs et les formulaires adaptatifs découplés sont déjà activés pour votre environnement. Vous pouvez utiliser les formulaires adaptatifs basés sur les composants principaux en tant que formulaires découplés pour les canaux mobiles et web, les applications natives et les services qui nécessitent une représentation découplée de formulaires adaptatifs.

## Activer les composants principaux des formulaires adaptatifs et les formulaires adaptatifs découplés {#enable-headless-forms}

Effectuez les étapes suivantes, dans l’ordre indiqué, pour activer les composants principaux des formulaires adaptatifs et les formulaires adaptatifs découplés pour un environnement AEM Forms as a Cloud Service


![Activer les composants principaux et les formulaires adaptatifs découplés](/help/forms/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service.png)


## &#x200B;1. Cloner votre référentiel Git AEM Forms as a Cloud Service {#clone-git-repository}

1. Connectez-vous à [Cloud Manager](https://my.cloudmanager.adobe.com/) et sélectionnez votre organisation et votre programme.

1. Accédez à la vignette **Pipelines** à partir de votre page **Aperçu du programme** et cliquez sur le bouton **Accéder aux informations sur le référentiel** pour accéder à votre référentiel Git et le gérer. La page contient les informations suivantes :

   * URL vers le référentiel Git de Cloud Manager.
   * Informations d’identification du nom d’utilisateur du référentiel Git (nom d’utilisateur et mot de passe).

   Cliquez sur **Générer un mot de passe** pour afficher ou générer le mot de passe.

1. Ouvrez le terminal ou l’invite de commande sur votre ordinateur local et exécutez la commande suivante :

   ```Shell
   git clone [Git Repository URL]
   ```

   Lorsque l’on vous y invite, saisissez les informations d’identification. Le référentiel est cloné sur votre ordinateur local.


## &#x200B;2. Ajouter les dépendances des composants principaux des formulaires adaptatifs à votre référentiel Git {#add-adaptive-forms-core-components-dependencies}

1. Ouvrez votre dossier du référentiel Git dans un éditeur de code de texte brut. Par exemple, VS Code.
1. Ouvrez le fichier `[AEM Repository Folder]\pom.xml` en mode d’édition.
1. Remplacez les versions des composants `core.forms.components.version`, `core.forms.components.af.version` et `core.wcm.components.version` par les versions spécifiées dans la [documentation des composants principaux](https://github.com/adobe/aem-core-forms-components). Si le composant n’existe pas, ajoutez ces composants.

   ```XML
   <!-- Replace the version with the latest released version at https://github.com/adobe/aem-core-forms-components/tags -->
   
   <properties>
       <core.wcm.components.version>2.22.10</core.wcm.components.version>
       <core.forms.components.version>2.0.18</core.forms.components.version>
       <core.forms.components.af.version>2.0.18</core.forms.components.af.version>
   </properties>
   ```

   ![Mention de la dernière version des composants principaux de Forms](/help/forms/assets/latest-forms-component-version.png)

1. Dans la section des dépendances du fichier `[AEM Repository Folder]\pom.xml`, ajoutez les dépendances suivantes, puis enregistrez le fichier.

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

1. Ouvrez le fichier `[AEM Repository Folder]/all/pom.xml` en mode d’édition. Ajoutez les dépendances suivantes dans la section `<embeddeds>` et enregistrez le fichier.

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
   >  Remplacez `${appId}` par votre appId.
   >
   >  Pour rechercher votre `${appId}`, dans le fichier `[AEM Repository Folder]/all/pom.xml`, recherchez le terme `-packages/application/install`. Le texte situé avant le terme `-packages/application/install` est votre `${appId}`. Par exemple, le code suivant, `myheadlessform` est `${appId}`.
   >
   >   ```
   >             <embedded>
   >                     <groupId>com.myheadlessform</groupId>
   >                     <artifactId>myheadlessform.ui.apps<artifactId>
   >                     <type>zip</type>
   >                   <target>/apps/myheadlessform-packages/application install</target>
   >             </embedded>
   >   ```

1. Dans la section `<dependencies>` du fichier `[AEM Repository Folder]/all/pom.xml`, ajoutez les dépendances suivantes, puis enregistrez le fichier :

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

1. Ouvrez le `[AEM Repository Folder]/ui.apps/pom.xml` pour édition. Ajoutez la dépendance `af-core bundle` et enregistrez le fichier.

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

## &#x200B;3. Créer et déployer le code mis à jour

Déployez le code mis à jour dans vos environnements de développement local et de service cloud afin d’activer les composants principaux sur les deux environnements :

* [Créer et déployer du code mis à jour dans un environnement de développement local (SDK AEM as a Cloud Service)](#core-components-on-aem-forms-local-sdk)

* [Créer et déployer du code mis à jour dans un environnement AEM Forms as a Cloud Service](#core-components-on-aem-forms-cs)

### Créer et déployer du code mis à jour dans un environnement de développement local {#core-components-on-aem-forms-local-sdk}

1. Ouvrez l’invite de commande ou le terminal.

1. Accédez au répertoire racine de votre projet de référentiel Git.

1. Exécutez la commande suivante pour créer le package de votre environnement :

   ```Shell
       mvn clean install
   ```



   Une fois le package créé, vous pouvez le trouver à l’adresse [Dossier du Référentiel Git]\all\target\[appid].all-[version].zip.

1. Utilisez le [gestionnaire de packages](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=fr) pour déployer le package accessible à [dossier de l’archétype de projet AEM]\all\target\[appid].all-[version].zip sur l’environnement de développement local.


### Créer et déployer du code mis à jour dans un environnement AEM Forms as a Cloud Service {#core-components-on-aem-forms-cs}

1. Ouvrez le terminal ou l’invite de commande.
1. Accédez à `[AEM Repository Folder]` et exécutez les commandes suivantes dans l’ordre indiqué

   ```Shell
    git add pom.xml
    git add all/pom.xml
    git add ui.apps/pom.xml
    git commit -m "Added dependencies for Adaptive Forms Core Components"
    git push origin
   ```

1. Une fois les fichiers validés dans le référentiel Git, [exécutez le pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=fr).

   Une fois l’exécution du pipeline terminée, les composants principaux des formulaires adaptatifs sont activés pour l’environnement correspondant. En outre, un modèle de formulaire adaptatif (composants principaux) et un thème Canvas 3.0 sont ajoutés à votre environnement Forms as a Cloud Service, ce qui vous permet de personnaliser et de créer des composants principaux basés sur les formulaires adaptatifs.


## Questions fréquentes {#faq}

### Que sont les composants principaux ? {#core-components}

Les [composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr) sont un ensemble de composants WCM (Web Content Management, ou gestion de contenu web) normalisés pour AEM, dont l’objectif est d’accélérer le développement et de réduire les coûts de maintenance de vos sites web.

### Quelles sont toutes les fonctionnalités ajoutées lors de l’activation des composants principaux ? {#core-components-capabilities}

Lorsque les composants principaux des formulaires adaptatifs sont activés pour votre environnement, un modèle de formulaire adaptatif basé sur les composants principaux vierge et le thème Canvas 3.0 sont ajoutés à votre environnement. Après avoir activé les composants principaux des formulaires adaptatifs pour votre environnement, vous pouvez :

* [Créer des formulaires adaptatifs basés sur des composants principaux](/help/forms/creating-adaptive-form-core-components.md).
* [Créer des modèles de formulaires adaptatifs basés sur des composants principaux](/help/forms/template-editor.md).
* [Créer des thèmes personnalisés pour les modèles de formulaires adaptatifs basés sur les composants principaux](/help/forms/using-themes-in-core-components.md).
* [Diffuser les représentations JSON des formulaires adaptatifs basés sur les composants principaux à divers canaux tels que les applications mobiles, web et natives, ainsi que les services qui nécessitent une représentation découplée d’un formulaire](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=fr).

### Les composants principaux des formulaires adaptatifs sont-ils activés pour mon environnement ? {#enable-components}

Pour vérifier que les composants principaux des formulaires adaptatifs sont activés pour votre environnement :

1. [Clonez votre référentiel AEM Forms as a Cloud Service](#1-clone-your-aem-forms-as-a-cloud-service-git-repository).

1. Ouvrez le fichier `[AEM Repository Folder]/all/pom.xml` du référentiel Git AEM Forms Cloud Service.

1. Recherchez les dépendances suivantes :

   * core-forms-components-af-core
   * core-forms-components-core
   * core-forms-components-apps
   * core-forms-components-af-apps
   * core-forms-components-examples-apps
   * core-forms-components-examples-content

   ![Localisez l’artefact core-forms-components-af-core dans all/pom.xml](/help/forms/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service-locate-core-af-artifact.png).

   Si les dépendances existent, les composants principaux des formulaires adaptatifs sont activés pour votre environnement.

### Pourquoi le rendu des formulaires basés sur les composants principaux échoue-t-il dans le projet ?

Le rendu des formulaires basés sur les composants principaux peut échouer en raison d’une incohérence de version entre le package de composants principaux Forms et la version incluse dans l’archétype de projet. Ce problème se produit généralement lorsque la version spécifiée dans l’archétype du projet est égale ou supérieure à la version fournie avec le package des composants principaux Forms. Pour résoudre ce problème, effectuez l’une des opérations suivantes :

* Utilisez une version inférieure du package Composants principaux Forms dans l’archétype du projet.
* Supprimez la dépendance Composants principaux Forms de l’archétype du projet, car la version requise est déjà incluse dans AEM as a Cloud Service. Le package Composants principaux Forms est fourni avec AEM as a Cloud SDK à partir de la version 20133, par exemple `AEM SDK v2025.3.20133.20250325T063357Z-250300`.

>[!MORELIKETHIS]
>
>* [Créer un formulaire adaptatif](/help/forms/creating-adaptive-form-core-components.md)
