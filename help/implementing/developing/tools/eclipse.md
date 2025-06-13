---
title: AEM Developer Tools for Eclipse
description: Découvrez comment utiliser les outils de développement AEM pour Eclipse, un plug-in Eclipse basé sur le plug-in Eclipse pour Apache Sling.
exl-id: 7f9c0f99-e230-440a-8bc9-a0ab7465e3bf
feature: Developing
role: Admin, Architect, Developer
source-git-commit: fecbebde808c545a84889da5610a79c088f2f459
workflow-type: tm+mt
source-wordcount: '1138'
ht-degree: 83%

---

# Outils de développement AEM pour Eclipse{#aem-developer-tools-for-eclipse}

![Logo Outils de développement Experience Manager pour Eclipse](assets/eclipse-logo.png)

## Vue d’ensemble {#overview}

Les _outils de développement Experience Manager pour Eclipse_ sont un plug-in Eclipse basé sur le [plug-in Eclipse pour Apache Sling](https://sling.apache.org/documentation/development/ide-tooling.html) disponible avec Apache License 2.

Il offre plusieurs fonctionnalités qui facilitent le développement d’AEM :

* Intégration transparente avec les instances AEM via Eclipse Server Connector
* Synchronisation pour les bundles de contenu et d’OSGi
* Prise en charge du débogage avec fonctionnalité de remplacement de code à chaud
* Démarrage simple de projets AEM par l’intermédiaire d’un assistant de création de projet spécifique
* Modification facile des propriétés JCR

## Conditions requises {#requirements}

Avant d’utiliser AEM Developer Tools, vous devez :

* Téléchargez et installez l’[IDE Eclipse pour les développeurs Enterprise Java™](https://www.eclipse.org/downloads/packages/).
* Configurez l’installation d’Eclipse pour vous assurer de disposer d’au moins 1 Go de mémoire de tas en modifiant votre fichier de configuration `eclipse.ini` comme décrit dans la [FAQ Eclipse.](https://wiki.eclipse.org/FAQ_How_do_I_increase_the_heap_size_available_to_Eclipse%3F)

>[!NOTE]
>
>Sur macOS, vous devez cliquer avec le bouton droit de la souris sur **Eclipse.app**, puis sélectionner **Afficher le contenu du package** pour rechercher votre `eclipse.ini`**.**

## Comment installer AEM Developer Tools pour Eclipse {#how-to-install-the-aem-developer-tools-for-eclipse}

Une fois les [conditions préalables](#requirements) ci-dessus réunies, vous pouvez installer le plug-in comme suit :

1. Ouvrez le site web [AEM Developer Tools](https://eclipse.adobe.com/com.adobe.granite.ide.p2update-1.3.0.zip). <!-- RB: OLD URL was (https://eclipse.adobe.com/aem/dev-tools/) This URL is generating a 404 error in the experience-manager-cloud-service.en LinkCheckExl report . The website appears to be dead; no redirects at all. Clicking "Installation Link" does not do anything. Only the link "Download archive" works. The "Online Documentation" link just takes you to the AEM Docs home page. Not sure if this topic is still needed?? -->

1. Copiez le **lien d’installation**.

   Notez que vous pouvez également télécharger une archive au lieu d’utiliser le lien d’installation. Cela permet une installation hors ligne, mais sans recevoir les notifications de mise à jour automatique.

1. Dans Eclipse, ouvrez le menu **Aide**.
1. Cliquez sur **Installer un nouveau logiciel**.
1. Cliquez sur **Add...** (Ajouter).
1. Dans le champ **Nom**, saisissez `AEM Developer Tools`.
1. Dans le champ **Emplacement**, copiez l’URL d’installation.
1. Cliquez sur **Add** (Ajouter).
1. Cochez les plug-ins **AEM** et **Sling**.
1. Cliquez sur **Next** (Suivant).
1. Dans la fenêtre **Install Details** (Détails de l’installation), cliquez de nouveau sur **Next** (Suivant).
1. Acceptez les contrats de licence et cliquez sur **Finish** (Terminer).
1. Cliquez sur **Redémarrer maintenant** pour redémarrer Eclipse.

## La perspective d’AEM {#the-aem-perspective}

Dans Eclipse, une perspective détermine les actions et les vues disponibles dans une fenêtre et permet une interaction axée sur les tâches avec les ressources. Pour plus d’informations sur les perspectives, consultez la [ documentation d’Eclipse ](https://help.eclipse.org/latest/index.jsp).

Les _outils de développement Experience Manager pour Eclipse_ offrent une perspective AEM qui vous permet de contrôler intégralement vos projets et instances AEM. Pour ouvrir la perspective AEM :

1. Dans la barre de menus Eclipse, sélectionnez **Fenêtre** > **Perspective** > **Ouvrir la perspective** > **Autre**.
1. Sélectionnez **AEM** dans la boîte de dialogue et cliquez sur **Ouvrir**.

![La perspective AEM dans Eclipse](assets/eclipse-aem-perspective.png)

## Exemple de projet multi-module {#sample-multi-module-project}

Les _outils de développement Experience Manager pour Eclipse_ s’accompagnent d’un exemple de projet multi-module qui vous permet de vous familiariser rapidement avec la configuration d’un projet dans Eclipse. Ils servent également de guide des bonnes pratiques pour plusieurs fonctionnalités AEM. [En savoir plus sur l’archétype du projet](https://github.com/adobe/aem-project-archetype).

Pour créer l’exemple de projet, procédez comme suit :

1. Dans le menu **Fichier** > **Nouveau** > **Projet**, accédez à la section **AEM** et sélectionnez **Exemple de projet multi-module AEM**.

   ![Exemple de projet multi-module AEM](assets/aem-sample-project.png)

1. Cliquez sur **Next** (Suivant).

   >[!NOTE]
   >
   >Cette étape peut prendre un certain temps, car m2eclipse doit analyser les catalogues d’archétypes.

1. Sélectionnez `com.adobe.granite.archetypes : sample-project-archetype : <highest-number>` dans le menu, puis cliquez sur **Next** (Suivant).

   ![Sélectionnez la version de l’archétype](assets/select-archetype.png)

1. Fournissez les champs suivants pour l’exemple de projet :

   * **Name** (Nom)
   * **Group Id** (ID de groupe)
   * **Artifact Id** (ID d’artefact)
   * **appId** : vous devrez peut-être développer les options **Advanced** (Avancé) pour définir cette valeur.
   * **appTitle** : vous devrez peut-être développer les options **Advanced** pour définir cette valeur.
   * **Package** : vous devrez peut-être développer les options **Advanced** pour définir cette valeur.

   ![Définition des propriétés d’archétype](assets/archetype-properties.png)

1. Cliquez sur **Next** (Suivant).

1. Vous devez ensuite configurer un serveur AEM auquel Eclipse se connectera.

   Pour utiliser la fonctionnalité de débogage, vous devez avoir démarré AEM en mode de débogage, ce qui peut être réalisé en ajoutant ce qui suit à la ligne de commande :

   ```text
       -nofork -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=10123
   ```

   ![Connexion au serveur AEM](assets/connect-server.png)

1. Cliquez sur **Finish** (Terminer). La structure du projet est créée.

   >[!NOTE]
   >
   >Sur une nouvelle installation (plus précisément, si les dépendances Maven n’ont jamais été téléchargées), vous risquez de créer le projet avec des erreurs. Dans ce cas, suivez la procédure décrite dans la section [Résoudre une définition de projet non valide](#resolving-invalid-project-definition).

## Comment importer des projets existants {#how-to-import-existing-projects}

Vous pouvez utiliser la fonction **Nouveau projet** pour créer la structure qui vous convient :

1. Suivez les instructions afin de créer un [exemple de projet multi-module](#sample-multi-module-project) et les projets suivants seront créés pour vous, ce qui permettra de séparer efficacement les préoccupations :

   * `PROJECT.ui.apps` pour le contenu `/apps` et `/etc`
   * `PROJECT.ui.content` pour le `/content` qui est créé
   * `PROJECT.core` pour les bundles Java™ (ils deviennent intéressants dès que vous voulez ajouter du code Java™)
   * `PROJECT.it.launcher` et `PROJECT.it.tests` pour les tests d’intégration

1. Remplacez le contenu de votre projet `PROJECT.ui.apps` par les dossiers `apps` et `etc` de votre package :

   1. Dans le panneau Project Explorer (Explorateur de projets), développez `PROJECT.ui.apps` > `src` > `main` > `content` > `jcr_root` > `apps`.
   1. Cliquez avec le bouton droit sur le dossier `apps` et choisissez **Afficher dans** > **Explorateur système**.
   1. Supprimez les dossiers `apps` et `etc` que vous devriez voir maintenant et placez ici les dossiers `apps` et `etc` de votre package de contenu.
   1. Dans Eclipse, cliquez avec le bouton droit sur le projet `PROJECT.ui.apps` et sélectionnez **Actualiser**.

1. Faites ensuite de même pour `PROJECT.ui.content` et remplacez son dossier de contenu par celui de vos packages :

   1. Dans le panneau Project Explorer (Explorateur de projets), développez `PROJECT.ui.content` > `src` > `main` > `content` > `jcr_root` > `content`.
   1. Cliquez avec le bouton droit sur le dossier de contenu le plus profond et sélectionnez **Afficher dans** > **Explorateur système**.
   1. Supprimez le dossier de contenu que vous devriez voir maintenant et placez ici le dossier de contenu de votre package de contenu.
   1. Dans Eclipse, cliquez avec le bouton droit sur le projet `PROJECT.ui.content` et sélectionnez **Actualiser**.

1. Vous devez maintenant mettre à jour les fichiers `filter.xml` de ces deux projets pour qu’ils correspondent au contenu de votre package de contenu. Pour cela, ouvrez le fichier `META-INF/vault/filter.xml` de votre package de contenu dans un éditeur de texte/code distinct.

   * Voici un exemple de l’aspect que peut avoir votre fichier `filter.xml` :

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

1. Concernant le contenu de votre package qui a été divisé en deux projets, vous devrez également diviser ces règles de filtrage en deux et mettre à jour les fichiers `filter.xml` de ces deux projets en conséquence.

   1. Dans Eclipse, ouvrez `PROJECT.ui.apps/src/main/content/META-INF/filter.xml`.
   1. Remplacez le contenu de l’élément `<workspaceFilter>` par les règles de votre package qui commencent par `/apps` et `/etc`.
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
   1. Remplacez les règles par celles de votre package qui commencent par `/content`.
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

1. Dans le panneau Servers (Serveurs), assurez-vous que votre connexion est démarrée. Si ce n’est pas le cas, démarrez-la.
1. Cliquez sur l’icône **Nettoyer et publier**.

Une fois cette opération terminée, votre package devrait être exécuté sur votre instance. Lors de l’enregistrement, toute modification est automatiquement synchronisée avec l’instance.

Si vous souhaitez recréer un package à partir de votre projet, cliquez avec le bouton droit de la souris sur le `PROJECT.ui.apps` ou le `PROJECT.ui.content`, puis sélectionnez **Exécuter en tant que** > **Installation Maven**.

Vous disposez désormais d’un dossier cible contenant votre package (nommé par exemple `PROJECT.ui.apps-0.0.1-SNAPSHOT.zip`).

## Résolution des problèmes {#troubleshooting}

### Résolution d’une définition de projet non valide {#resolving-invalid-project-definition}

Pour résoudre des dépendances et une définition de projet non valides, procédez comme suit :

1. Sélectionnez tous les projets créés.
1. Faites un clic-droit.
1. Dans le menu contextuel, sélectionnez **Maven** > **Mettre à jour les projets**.
1. Cochez **Force Updates of Snapshot/Releases** (Forcer les mises à jour d’instantané/de versions).
1. Cliquez sur **OK**.

Eclipse télécharge les dépendances requises. Cela peut prendre un moment.

## Informations supplémentaires {#more-information}

Le site Web officiel Apache Sling IDE tooling for Eclipse fournit des informations utiles :

* Le [**guide d’utilisation Apache Sling IDE tooling for Eclipse**](https://sling.apache.org/documentation/development/ide-tooling.html) vous guide parmi les concepts généraux, l’intégration des serveurs et les fonctionnalités de déploiement pris en charge par AEM Development Tools.
* La section [Dépannage](https://sling.apache.org/documentation/development/ide-tooling.html#troubleshooting).
* La [liste des problèmes connus](https://sling.apache.org/documentation/development/ide-tooling.html#known-issues).

La documentation officielle [Eclipse](https://www.eclipse.org/) suivante peut vous aider à configurer votre environnement :

* [Prise en main d’Eclipse](https://eclipseide.org/getting-started/)
* [Système d’aide d’Eclipse Luna](https://help.eclipse.org/latest/index.jsp)
* [Intégration Maven (m2eclipse)](https://www.eclipse.org/m2e/)
