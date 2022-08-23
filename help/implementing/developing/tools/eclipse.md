---
title: AEM Developer Tools for Eclipse
description: AEM Outils de développement pour Eclipse
exl-id: 7f9c0f99-e230-440a-8bc9-a0ab7465e3bf
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '1182'
ht-degree: 100%

---

# AEM Outils de développement pour Eclipse{#aem-developer-tools-for-eclipse}

![](assets/eclipse-logo.png)

## Présentation {#overview}

AEM Developer Tools for Eclipse est un plug-in Eclipse basé sur le [plug-in Eclipse pour Apache Sling](https://sling.apache.org/documentation/development/ide-tooling.html) disponible avec Apache License 2.

Il offre plusieurs fonctionnalités qui facilitent le développement d’AEM :

* Intégration transparente avec les instances AEM via Eclipse Server Connector
* Synchronisation pour les bundles de contenu et d’OSGi
* Prise en charge du débogage avec fonctionnalité de remplacement de code à chaud
* Amorçage simple de projets AEM avec un assistant de création de projet spécifique
* Modification facile des propriétés JCR

## Conditions requises {#requirements}

Avant d’utiliser AEM Developer Tools, vous devez :

* télécharger et installer [Eclipse IDE pour les développeurs Java EE](https://www.eclipse.org/downloads/packages/) ;
* configurer votre installation Eclipse pour vous assurer de disposer d’au moins 1 Go de mémoire de segment en modifiant votre fichier de configuration `eclipse.ini` de la manière décrite dans la [FAQ Eclipse](https://wiki.eclipse.org/FAQ_How_do_I_increase_the_heap_size_available_to_Eclipse).

>[!NOTE]
>
>Sous macOS, vous devez cliquer avec le bouton droit de la souris sur **Eclipse.app**, puis sélectionner **Voir le contenu du paquet** pour trouver le fichier `eclipse.ini`**.**

## Installation d’AEM Developer Tools for Eclipse {#how-to-install-the-aem-developer-tools-for-eclipse}

Une fois les [conditions préalables](#requirements) ci-dessus réunies, vous pouvez installer le plug-in comme suit :

1. Ouvrez le [site web AEM Developer Tools.](https://eclipse.adobe.com/aem/dev-tools/)

1. Copiez le **Lien d’installation**.

   Notez que vous pouvez également télécharger un fichier d’archives au lieu d’utiliser le lien d’installation. Cela permet une installation hors ligne, mais sans recevoir les notifications de mise à jour automatique.

1. Dans Eclipse, ouvrez le menu **Help** (Aide).
1. Cliquez sur **Install New Software** (Installer un nouveau logiciel).
1. Cliquez sur **Add...** (Ajouter).
1. Dans **Name** (Nom), saisissez `AEM Developer Tools`.
1. Dans **Location** (Emplacement), copiez l’URL d’installation.
1. Cliquez sur **Add** (Ajouter).
1. Cochez les deux modules externes **AEM** et **Sling**.
1. Cliquez sur **Next** (Suivant).
1. Dans la fenêtre **Install Details** (Détails de l’installation), cliquez de nouveau sur **Next** (Suivant).
1. Acceptez les contrats de licence et cliquez sur **Finish** (Terminer).
1. Cliquez sur **Restart Now** (Redémarrer maintenant) pour redémarrer Eclipse.

## La perspective AEM {#the-aem-perspective}

Dans Eclipse, une perspective détermine les actions et les vues disponibles dans une fenêtre et permet une interaction axée sur les tâches avec les ressources dans Eclipse. Pour plus d’informations sur les perspectives, consultez la [documentation d’Eclipse.](https://help.eclipse.org)

AEM Development Tools for Eclipse propose une perspective offrant un contrôle total sur vos projets et instances AEM. Pour ouvrir la perspective AEM :

1. Dans la barre de menus Eclipse, sélectionnez **Window** > **Perspective** > **Open Perspective** > **Other**.
1. Sélectionnez **AEM** dans la boîte de dialogue et cliquez sur **Ouvrir**.

![La perspective AEM dans Eclipse](assets/eclipse-aem-perspective.png)

## Exemple de projet multi-module {#sample-multi-module-project}

AEM Developer Tools for Eclipse est fourni avec un exemple de projet multi-module qui vous aide à vous familiariser rapidement avec une configuration de projet dans Eclipse, et sert également de guide de bonnes pratiques pour plusieurs fonctionnalités AEM. [En savoir plus sur l’archétype du projet](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).

Suivez les étapes ci-après pour créer l’exemple de projet :

1. Dans le menu **Fichier** > **Nouveau** > **Projet**, accédez à la section **AEM** et sélectionnez **Exemple de projet multi-module AEM**.

   ![Exemple de projet multi-module AEM](assets/aem-sample-project.png)

1. Cliquez sur **Next** (Suivant).

   >[!NOTE]
   >
   >Cette étape peut prendre un certain temps, car m2eclipse doit analyser les catalogues d’archétype.

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

   Pour utiliser la fonctionnalité de débogage, vous devez avoir démarré AEM en mode débogage, ce qui peut être réalisé, par exemple, en ajoutant ce qui suit à la ligne de commande :

   ```text
       -nofork -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=10123
   ```

   ![Connexion au serveur AEM](assets/connect-server.png)

1. Cliquez sur **Finish** (Terminer). La structure du projet est créée.

   >[!NOTE]
   >
   >Sur une nouvelle installation (plus précisément, si les dépendances Maven n’ont jamais été téléchargées), vous risquez de créer le projet avec des erreurs. Dans ce cas, veuillez suivre la procédure décrite dans [Résolution d’une définition de projet non valide](#resolving-invalid-project-definition).

## Importation de projets existants {#how-to-import-existing-projects}

Vous pouvez utiliser la fonction **New Project** (Nouveau projet) pour créer la structure qui vous convient :

1. Suivez les instructions afin de créer un [exemple de projet multi-module](#sample-multi-module-project) et les projets suivants seront créés pour vous, ce qui permettra de séparer efficacement les préoccupations :

   * `PROJECT.ui.apps` pour le contenu `/apps` et `/etc`
   * `PROJECT.ui.content` pour le `/content` qui est créé
   * `PROJECT.core` pour les lots Java (ils deviennent intéressants dès que vous voulez ajouter du code Java)
   * `PROJECT.it.launcher` et `PROJECT.it.tests` pour les tests d’intégration

1. Remplacez le contenu de votre projet `PROJECT.ui.apps` par les dossiers `apps` et `etc` de votre package :

   1. Dans le panneau Project Explorer (Explorateur de projets), développez `PROJECT.ui.apps` > `src` > `main` > `content` > `jcr_root` > `apps`.
   1. Cliquez avec le bouton droit sur le dossier `apps` et choisissez **Show In** (Afficher dans) > **System Explorer** (Explorateur système).
   1. Supprimez les dossiers `apps` et `etc` que vous devriez voir maintenant et placez ici les dossiers `apps` et `etc` de votre package de contenu.
   1. Dans Eclipse, cliquez avec le bouton droit sur le projet `PROJECT.ui.apps` et choisissez **Refresh** (Actualiser).

1. Faites ensuite de même pour `PROJECT.ui.content` et remplacez son dossier de contenu par celui de votre package :

   1. Dans le panneau Project Explorer (Explorateur de projets), développez `PROJECT.ui.content` > `src` > `main` > `content` > `jcr_root` > `content`.
   1. Cliquez avec le bouton droit sur le dossier de contenu plus profond et choisissez **Show In** (Afficher dans) > **System Explorer** (Explorateur système).
   1. Supprimez le dossier de contenu que vous devriez voir maintenant et placez ici le dossier de contenu de votre package de contenu.
   1. Dans Eclipse, cliquez avec le bouton droit sur le projet `PROJECT.ui.content` et choisissez **Refresh** (Actualiser).

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

1. Concernant le contenu de votre package qui a été divisé en deux projets, vous devrez également scinder ces règles de filtrage en deux et mettre à jour les fichiers `filter.xml` de ces deux projets en conséquence.

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
1. Cliquez sur l’icône **Clean and Publish** (Nettoyer et publier).

Une fois cette opération terminée, votre package devrait être exécuté sur votre instance. Lors de l’enregistrement, toute modification est automatiquement synchronisée avec l’instance.

Si vous souhaitez recréer un package à partir de votre projet, cliquez avec le bouton droit de la souris sur `PROJECT.ui.apps` ou `PROJECT.ui.content` et choisissez **Run As** (Exécuter en tant que) > **Maven Install** (Installation Maven).

Vous disposez désormais d’un dossier cible créé avec votre package (nommé par ex. `PROJECT.ui.apps-0.0.1-SNAPSHOT.zip`).

## Résolution des problèmes {#troubleshooting}

### Résolution d’une définition de projet non valide {#resolving-invalid-project-definition}

Pour résoudre des dépendances et une définition de projet non valides, procédez comme suit :

1. Sélectionnez tous les projets créés.
1. Faites un clic-droit.
1. Dans le menu contextuel, sélectionnez **Maven** > **Update Projects** (Mettre à jour les projets).
1. Cochez **Force Updates of Snapshot/Releases** (Forcer les mises à jour d’instantané/de versions).
1. Cliquez sur **OK**.

Eclipse télécharge les dépendances requises. Cela peut prendre un moment.

## Informations complémentaires {#more-information}

Le site web officiel Apache Sling IDE tooling for Eclipse fournit des informations utiles :

* Le [**Guide de l’utilisateur** Apache Sling IDE tooling for Eclipse](https://sling.apache.org/documentation/development/ide-tooling.html) vous guide parmi les concepts généraux, l’intégration des serveurs et les fonctionnalités de déploiement pris en charge par AEM Development Tools.
* La section [Dépannage](https://sling.apache.org/documentation/development/ide-tooling.html#troubleshooting).
* La [liste des problèmes connus](https://sling.apache.org/documentation/development/ide-tooling.html#known-issues).

La documentation officielle [Eclipse](https://eclipse.org/) suivante peut vous aider à configurer votre environnement :

* [Prise en main d’Eclipse](https://eclipse.org/users/)
* [Système d’aide d’Eclipse Luna](https://help.eclipse.org/luna/index.jsp)
* [Intégration Maven (m2eclipse)](https://www.eclipse.org/m2e/)
