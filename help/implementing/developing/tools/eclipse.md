---
title: AEM Developer Tools for Eclipse
description: Outils de développement AEM pour Eclipse
translation-type: tm+mt
source-git-commit: c40d668cb6dcf5c3e2d09504b547457306a99c85
workflow-type: tm+mt
source-wordcount: '1182'
ht-degree: 28%

---


# Outils de développement AEM pour Eclipse{#aem-developer-tools-for-eclipse}

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

* Téléchargez et installez [Eclipse IDE for Enterprise Java Developers](https://www.eclipse.org/downloads/packages/).
* Configurez votre installation d&#39;éclipse pour vous assurer que vous disposez d&#39;au moins 1 gigaoctet de mémoire de tas en modifiant votre fichier de configuration `eclipse.ini` comme décrit dans la [FAQ sur l&#39;éclipse](https://wiki.eclipse.org/FAQ_How_do_I_increase_the_heap_size_available_to_Eclipse).

>[!NOTE]
>
>Sur macOS, vous devez cliquer avec le bouton droit de la souris sur **Eclipse.app**, puis sélectionner **Afficher le contenu du package** pour trouver votre `eclipse.ini`**.**

## Installation des outils de développement AEM pour Eclipse {#how-to-install-the-aem-developer-tools-for-eclipse}

Une fois que vous avez satisfait aux [exigences](#requirements) ci-dessus, vous pouvez installer le module externe comme suit :

1. Ouvrez le [site Web Outils de développement AEM.](https://eclipse.adobe.com/aem/dev-tools/)

1. Copiez le **Lien d’installation**.

   Notez que vous pouvez également télécharger un fichier d’archives au lieu d’utiliser le lien d’installation. Cela permet une installation hors ligne, mais sans recevoir les notifications de mise à jour automatique.

1. Dans Eclipse, ouvrez le menu **Help** (Aide).
1. Cliquez sur **Install New Software** (Installer un nouveau logiciel).
1. Cliquez sur **Ajouter...**.
1. Dans **Name**, saisissez `AEM Developer Tools`.
1. Dans **Location** (Emplacement), copiez l’URL d’installation.
1. Cliquez sur **Ajouter**.
1. Cochez les deux modules externes **AEM** et **Sling**.
1. Cliquez sur **Next** (Suivant).
1. Dans la fenêtre **Détails de l&#39;installation**, cliquez de nouveau sur **Suivant**.
1. Acceptez les contrats de licence et cliquez sur **Terminer**.
1. Cliquez sur **RestartNow** pour redémarrer Eclipse.

## AEM Perspective {#the-aem-perspective}

Dans Eclipse, une perspective détermine les actions et les vues disponibles dans une fenêtre et permet une interaction orientée tâche avec les ressources dans Eclipse. Pour plus d&#39;informations sur Perspective, consultez la [documentation d&#39;Eclipse.](https://help.eclipse.org)

Les outils de développement AEM pour Eclipse offrent une perspective AEM qui vous offre à contrôler vos projets et instances. Pour ouvrir la perspective AEM :

1. Dans la barre de menus Eclipse, sélectionnez **Fenêtre** -> **Perspective** -> **Ouvrir la perspective** -> **Autre**.
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

1. Sélectionnez `com.adobe.granite.archetypes : sample-project-archetype : <highest-number>` dans le menu, puis cliquez sur **Suivant**.

   ![Sélectionner la version de l&#39;archétype](assets/select-archetype.png)

1. Fournissez les champs suivants pour l’exemple de projet :

   * **Nom**
   * **ID de groupe**
   * **Id d&#39;artefact**
   * **appId**  : vous devrez peut-être développer les options  **** avancées pour définir cette valeur.
   * **appTitle**  - Vous devrez peut-être développer les options  **** avancées pour définir cette valeur.
   * **Package**  - Vous devrez peut-être développer les options  **** avancées pour définir cette valeur.

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

1. Suivez les instructions pour créer un projet [Exemple de projet multimodule](#sample-multi-module-project) et vous aurez créé les projets suivants pour vous, ce qui vous permettra de séparer les préoccupations :

   * `PROJECT.ui.apps` pour  `/apps` et  `/etc` le contenu
   * `PROJECT.ui.content` pour  `/content` ce qui est écrit
   * `PROJECT.core` pour les lots Java (ceux-ci deviennent intéressants dès que vous souhaitez ajouter du code Java)
   * `PROJECT.it.launcher` et  `PROJECT.it.tests` pour les tests d’intégration

1. Remplacez le contenu de votre projet `PROJECT.ui.apps` par les dossiers `apps` et `etc` de votre package :

   1. Dans le panneau Explorateur de projets, dépliez `PROJECT.ui.apps` > `src` > `main` > `content` > `jcr_root` > `apps`.
   1. Cliquez avec le bouton droit sur le dossier `apps` et choisissez **Afficher en** > **Explorateur système**.
   1. Supprimez les dossiers `apps` et `etc` que vous devriez maintenant voir et placez ici les dossiers `apps` et `etc` de votre package de contenu.
   1. Dans Eclipse, cliquez avec le bouton droit sur le projet `PROJECT.ui.apps` et choisissez **Actualiser**.

1. Faites ensuite de même pour le dossier `PROJECT.ui.content` et remplacez son dossier de contenu par celui de votre package :

   1. Dans le panneau Explorateur de projets, dépliez `PROJECT.ui.content` > `src` > `main` > `content` > `jcr_root` > `content`.
   1. Cliquez avec le bouton droit sur le dossier de contenu plus profond et choisissez **Afficher dans** -> **Explorateur système**.
   1. Supprimez le dossier de contenu que vous devez maintenant afficher et placez-le dans le dossier de contenu de votre package de contenu.
   1. Dans Eclipse, cliquez avec le bouton droit sur le projet `PROJECT.ui.content` et choisissez **Actualiser**.

1. Vous devez maintenant mettre à jour les fichiers `filter.xml` de ces deux projets pour qu&#39;ils correspondent au contenu de votre package de contenu. Pour cela, ouvrez le fichier `META-INF/vault/filter.xml` de votre package de contenu dans un éditeur de texte/code distinct.

   * Voici un exemple de l&#39;aspect de votre fichier `filter.xml` :

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

1. En ce qui concerne le contenu de votre paquet qui a été divisé en deux projets, vous devrez également scinder ces règles de filtrage en deux et mettre à jour en conséquence les fichiers `filter.xml` des deux projets.

   1. Dans Eclipse, ouvrez `PROJECT.ui.apps/src/main/content/META-INF/filter.xml`.
   1. Remplacez le contenu de l’élément `<workspaceFilter>` par les règles de votre package qui s’début par `/apps` et `/etc`.
      * Par exemple :

         ```xml
         <?xml version="1.0" encoding="UTF-8"?>
         <workspaceFilter version="1.0">
            <filter root="/apps/foo"/>
            <filter root="/apps/foundation/components/bar"/>
            <filter root="/etc/designs/foo"/>
         </workspaceFilter>
         ```
   1. Ouvrez ensuite `PROJECT.ui.content/src/main/content/META-INF/filter.xml`.
   1. Remplacez les règles par celles de votre package qui début par `/content`.
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
1. Cliquez sur l&#39;icône **Nettoyer et publier**.

Une fois l’opération terminée, vous devez exécuter votre package sur votre instance. Lors de l’enregistrement, toute modification est automatiquement synchronisée avec l’instance.

Si vous souhaitez recréer un package à partir de votre projet, cliquez avec le bouton droit de la souris sur `PROJECT.ui.apps` ou `PROJECT.ui.content` et choisissez **Exécuter en tant que** -> **Installation maven**.

Vous disposez désormais d’un dossier de cible créé avec votre pack (appelé par ex. `PROJECT.ui.apps-0.0.1-SNAPSHOT.zip`).

## Dépannage {#troubleshooting}

### Résolution d’une définition de projet non valide {#resolving-invalid-project-definition}

Pour résoudre des dépendances et une définition de projet non valides, procédez comme suit :

1. Sélectionnez tous les projets créés.
1. Faites un clic-droit.
1. Dans le menu contextuel, sélectionnez **Maven** -> **Mettre à jour les projets**.
1. Cochez **Force Updates of Snapshot/Releases** (Forcer les mises à jour de snaptshot/versions).
1. Cliquez sur **OK**.

Eclipse télécharge les dépendances requises. Cela peut prendre un moment.

## Informations supplémentaires {#more-information}

Le site web officiel Apache Sling IDE tooling for Eclipse fournit des informations utiles :

* Le [**Guide de l&#39;utilisateur d&#39;Apache Sling pour Eclipse** ](https://sling.apache.org/documentation/development/ide-tooling.html), cette documentation vous guidera dans l&#39;ensemble des concepts, l&#39;intégration des serveurs et les capacités de déploiement pris en charge par les outils de développement AEM.
* La section [Dépannage](https://sling.apache.org/documentation/development/ide-tooling.html#troubleshooting).
* La [liste des problèmes connus](https://sling.apache.org/documentation/development/ide-tooling.html#known-issues).

La documentation officielle [Eclipse](https://eclipse.org/) suivante peut vous aider à configurer votre environnement :

* [Getting Started with Eclipse](https://eclipse.org/users/)
* [Eclipse Luna Help System](https://help.eclipse.org/luna/index.jsp)
* [Maven Integration (m2eclipse)](https://www.eclipse.org/m2e/)
