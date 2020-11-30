---
title: AEM Developer Tools for Eclipse
description: AEM Developer Tools for Eclipse
translation-type: tm+mt
source-git-commit: c40d668cb6dcf5c3e2d09504b547457306a99c85
workflow-type: tm+mt
source-wordcount: '1182'
ht-degree: 28%

---


# AEM Developer Tools for Eclipse{#aem-developer-tools-for-eclipse}

![](assets/eclipse-logo.png)

## Présentation {#overview}

AEM Developer Tools for Eclipse est un module externe Eclipse basé sur le module externe [Eclipse pour Apache Sling](https://sling.apache.org/documentation/development/ide-tooling.html) disponible avec Apache License 2.

Il offre plusieurs fonctionnalités qui facilitent le développement d’AEM :

* Intégration transparente avec les instances AEM via Eclipse Server Connector
* Synchronisation du contenu et des lots OSGi
* Prise en charge du débogage avec fonctionnalité de permutation de code
* Bootstrap simple de projets AEM avec un assistant de création de projet spécifique
* Modification facile des propriétés JCR

## Conditions requises {#requirements}

Avant d’utiliser les outils de développement AEM, vous devez :

* Download and install [Eclipse IDE for Enterprise Java Developers](https://www.eclipse.org/downloads/packages/).
* Configure your eclipse installation to ensure that you have at least 1 gigabyte of heap memory by editing your `eclipse.ini` configuration file as described in the [Eclipse FAQ](https://wiki.eclipse.org/FAQ_How_do_I_increase_the_heap_size_available_to_Eclipse).

>[!NOTE]
>
>On macOS, you need to right-click on **Eclipse.app** and then select **Show Package Contents** in order to find your `eclipse.ini`**.**

## How to Install the AEM Developer Tools for Eclipse {#how-to-install-the-aem-developer-tools-for-eclipse}

Once you have fulfilled the [requirements](#requirements) above, you can install the plugin as follows:

1. Open the [AEM Developer Tools Web Site.](https://eclipse.adobe.com/aem/dev-tools/)

1. Copiez le **Lien d’installation**.

   Notez que vous pouvez également télécharger un fichier d’archives au lieu d’utiliser le lien d’installation. Cela permet une installation hors ligne, mais sans recevoir les notifications de mise à jour automatique.

1. Dans Eclipse, ouvrez le menu **Help** (Aide).
1. Cliquez sur **Install New Software** (Installer un nouveau logiciel).
1. Cliquez sur **Ajouter...**.
1. Dans **Nom** , saisissez `AEM Developer Tools`.
1. Dans **Location** (Emplacement), copiez l’URL d’installation.
1. Cliquez sur **Ajouter**.
1. Cochez les deux modules externes **AEM** et **Sling**.
1. Cliquez sur **Next** (Suivant).
1. Dans la fenêtre Détails **de l’** installation, cliquez à nouveau sur **Suivant** .
1. Accept the license agreements and click **Finish**.
1. Click **RestartNow** in order to restart Eclipse.

## AEM Perspective {#the-aem-perspective}

Dans Eclipse, une perspective détermine les actions et les vues disponibles dans une fenêtre et permet une interaction orientée tâche avec les ressources dans Eclipse. Pour plus d&#39;informations sur Perspective, consultez la documentation [Eclipse.](https://help.eclipse.org)

Les outils de développement AEM pour Eclipse offrent une perspective AEM qui vous offre à contrôler vos projets et instances. Pour ouvrir la perspective AEM :

1. Dans la barre de menus Eclipse, sélectionnez **Fenêtre** -> **Perspective** -> **Ouvrir la perspective** -> **Autre.**
1. Sélectionnez **AEM** dans la boîte de dialogue et cliquez sur **Ouvrir**.

![La perspective AEM dans Eclipse](assets/eclipse-aem-perspective.png)

## Exemple de projet multi-module {#sample-multi-module-project}

AEM Developer Tools for Eclipse est fourni avec un exemple de projet multi-module qui vous aide à vous familiariser rapidement avec une configuration de projet dans Eclipse, et sert également de guide de bonnes pratiques pour plusieurs fonctionnalités AEM. [En savoir plus sur l’archétype du projet](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).

Suivez les étapes ci-après pour créer l’exemple de projet :

1. Dans le menu **Fichier** > **Nouveau** > **Projet**, accédez à la section **AEM** et sélectionnez **Exemple de projet multi-module AEM**.

   ![aem exemple de projet à modules multiples](assets/aem-sample-project.png)

1. Cliquez sur **Next** (Suivant).

   >[!NOTE]
   >
   >Cette étape peut prendre un certain temps car m2eclipse doit analyser les catalogues archétype.

1. Choisissez `com.adobe.granite.archetypes : sample-project-archetype : <highest-number>` dans le menu, puis cliquez sur **Suivant**.

   ![Sélectionner la version de l&#39;archétype](assets/select-archetype.png)

1. Fournissez les champs suivants pour l’exemple de projet :

   * **Nom**
   * **ID de groupe**
   * **Id d&#39;artefact**
   * **appId** - Vous devrez peut-être développer les options **avancées** pour définir cette valeur.
   * **appTitle** - Vous devrez peut-être développer les options **avancées** pour définir cette valeur.
   * **Package** : vous devrez peut-être développer les options **avancées** pour définir cette valeur.

   ![Définition des propriétés d&#39;archétype](assets/archetype-properties.png)

1. Cliquez sur **Next** (Suivant).

1. Vous configurez ensuite un serveur AEM auquel Eclipse va se connecter.

   Pour utiliser la fonctionnalité de débogage, vous devez avoir démarré AEM en mode de débogage - ce qui peut être réalisé en ajoutant ce qui suit à la ligne de commande :

   ```text
       -nofork -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=10123
   ```

   ![Se connecter au serveur AEM](assets/connect-server.png)

1. Cliquez sur **Termine**. La structure du projet est créée.

   >[!NOTE]
   >
   >Lors d&#39;une nouvelle installation (plus précisément, lorsque les dépendances maven n&#39;ont jamais été téléchargées), vous pouvez créer le projet avec des erreurs. Dans ce cas, veuillez suivre la procédure décrite dans [Résolution d’une définition de projet non valide](#resolving-invalid-project-definition).

## Importation de projets existants {#how-to-import-existing-projects}

Vous pouvez utiliser la fonction **Nouveau projet** pour créer la structure appropriée pour vous :

1. Suivez les instructions pour créer un [exemple de projet](#sample-multi-module-project) à modules multiples et vous aurez créé les projets suivants pour vous, ce qui vous permettra de séparer les préoccupations :

   * `PROJECT.ui.apps` pour `/apps` et `/etc` le contenu
   * `PROJECT.ui.content` pour `/content` ce qui est écrit
   * `PROJECT.core` pour les lots Java (ceux-ci deviennent intéressants dès que vous souhaitez ajouter du code Java)
   * `PROJECT.it.launcher` et `PROJECT.it.tests` pour les tests d’intégration

1. Remplacez le contenu de votre `PROJECT.ui.apps` projet par les dossiers `apps` et `etc` de votre package :

   1. Dans le panneau Explorateur de projets, dépliez `PROJECT.ui.apps` > `src` > `main` > `content` > `jcr_root` > `apps`.
   1. Cliquez avec le bouton droit sur le `apps` dossier et choisissez **Afficher dans** > Explorateur **** système.
   1. Supprimez les `apps` dossiers et `etc` les dossiers que vous devriez maintenant voir et placez ici les `apps` dossiers et `etc` les dossiers de votre package de contenu.
   1. Dans Eclipse, cliquez avec le bouton droit sur le `PROJECT.ui.apps` projet et choisissez **Actualiser**.

1. Faites ensuite de même pour le dossier `PROJECT.ui.content` et remplacez son dossier de contenu par celui de votre pack :

   1. Dans le panneau Explorateur de projets, dépliez `PROJECT.ui.content` > `src` > `main` > `content` > `jcr_root` > `content`.
   1. Cliquez avec le bouton droit sur le dossier de contenu plus profond et choisissez **Afficher dans** -> Explorateur **** système.
   1. Supprimez le dossier de contenu que vous devez maintenant afficher et placez-le dans le dossier de contenu de votre package de contenu.
   1. Dans Eclipse, cliquez avec le bouton droit sur le `PROJECT.ui.content` projet et choisissez **Actualiser**.

1. Vous devez maintenant mettre à jour les `filter.xml` fichiers de ces deux projets pour qu&#39;ils correspondent au contenu de votre module de contenu. Pour cela, ouvrez le `META-INF/vault/filter.xml` fichier de votre package de contenu dans un éditeur de texte/code distinct.

   * Voici un exemple de l’aspect de votre `filter.xml` fichier :

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <workspaceFilter version="1.0">
       <filter root="/apps/foo"/>
       <filter root="/apps/foundation/components/bar"/>
       <filter root="/etc/designs/foo"/>
       <filter root="/content/foo"/>
       <filter root="/content/dam/foo"/>
       <filter root="/content/usergenerated/content/foo"/>
   </workspaceFilter>
   ```

1. En ce qui concerne le contenu de votre paquet qui a été divisé en deux projets, vous devrez également scinder ces règles de filtrage en deux et mettre à jour en conséquence les `filter.xml` fichiers des deux projets.

   1. Dans Eclipse, ouvrez `PROJECT.ui.apps/src/main/content/META-INF/filter.xml`.
   1. Remplacez le contenu de l’ `<workspaceFilter>` élément par les règles de votre package qui début par `/apps` et `/etc`
      * Par exemple :

         ```xml
         <?xml version="1.0" encoding="UTF-8"?>
         <workspaceFilter version="1.0">
            <filter root="/apps/foo"/>
            <filter root="/apps/foundation/components/bar"/>
            <filter root="/etc/designs/foo"/>
         </workspaceFilter>
         ```
   1. Alors ouvrez `PROJECT.ui.content/src/main/content/META-INF/filter.xml`.
   1. Remplacez les règles par celles de votre package par `/content`.
      * Par exemple :

         ```xml
         <?xml version="1.0" encoding="UTF-8"?>
         <workspaceFilter version="1.0">
            <filter root="/content/foo"/>
            <filter root="/content/dam/foo"/>
            <filter root="/content/usergenerated/content/foo"/>
         </workspaceFilter>
         ```


1. Veillez à enregistrer toutes vos modifications. Vous pouvez désormais synchroniser ce nouveau contenu avec votre instance AEM.

1. Dans le panneau Serveurs, assurez-vous que votre connexion est démarrée et, si vous ne l’début pas.
1. Cliquez sur l’icône **Nettoyer et publier** .

Une fois l’opération terminée, vous devez exécuter votre package sur votre instance. Lors de l’enregistrement, toute modification est automatiquement synchronisée avec l’instance.

Si vous souhaitez recréer un package à partir de votre projet, cliquez avec le bouton droit de la souris sur le `PROJECT.ui.apps` ou `PROJECT.ui.content` et choisissez **Exécuter en tant que** -> Installation **** expert.

Vous disposez désormais d’un dossier de cible créé avec votre pack (appelé par ex. `PROJECT.ui.apps-0.0.1-SNAPSHOT.zip`).

## Dépannage {#troubleshooting}

### Résolution d’une définition de projet non valide {#resolving-invalid-project-definition}

Pour résoudre des dépendances et une définition de projet non valides, procédez comme suit :

1. Sélectionnez tous les projets créés.
1. Faites un clic-droit.
1. Dans le menu contextuel, sélectionnez **Maven** -> **Update Projects**.
1. Cochez **Force Updates of Snapshot/Releases** (Forcer les mises à jour de snaptshot/versions).
1. Cliquez sur **OK**.

Eclipse télécharge les dépendances requises. Cela peut prendre un moment.

## Informations supplémentaires {#more-information}

Le site web officiel Apache Sling IDE tooling for Eclipse fournit des informations utiles :

* The [**Apache Sling IDE tooling for Eclipse** User Guide](https://sling.apache.org/documentation/development/ide-tooling.html), this documentation will guide you through the overall concepts, server integration and deployment capabilities supported by the AEM Development Tools.
* La section [Dépannage](https://sling.apache.org/documentation/development/ide-tooling.html#troubleshooting).
* La [liste des problèmes connus](https://sling.apache.org/documentation/development/ide-tooling.html#known-issues).

La documentation officielle [Eclipse](https://eclipse.org/) suivante peut vous aider à configurer votre environnement :

* [Getting Started with Eclipse](https://eclipse.org/users/)
* [Eclipse Luna Help System](https://help.eclipse.org/luna/index.jsp)
* [Maven Integration (m2eclipse)](https://www.eclipse.org/m2e/)
