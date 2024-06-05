---
title: Plug-in Maven Content Package d’Adobe
description: Utilisation du plug-in Maven Content Package pour déployer des applications AEM
exl-id: d631d6df-7507-4752-862b-9094af9759a0
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1802'
ht-degree: 97%

---

# Plug-in Maven Content Package d’Adobe {#adobe-content-package-maven-plugin}

Le plug-in Maven Content Package d’Adobe permet d’intégrer les tâches de déploiement et de gestion de modules dans vos projets Maven.

Le déploiement des modules construits sur AEM est effectué par le plug-in Maven Content Package d’Adobe et permet l’automatisation des tâches normalement exécutées à l’aide du [Gestionnaire de modules](/help/implementing/developing/tools/package-manager.md) d’AEM :

* Création de packages à partir des fichiers du système de fichiers.
* Installation et désinstallation de packages sur AEM.
* Création de packages déjà définis sur AEM.
* Obtention de la liste des packages installés sur AEM.
* Suppression d’un package d’AEM.

Ce document décrit comment utiliser Maven pour gérer ces tâches. Cependant, il est également important de comprendre [comment les projets AEM et leurs packages sont structurés.](#aem-project-structure)

>[!NOTE]
>
>La **création** de packages incombe désormais au [plug-in Maven Apache Jackrabbit FileVault.](https://jackrabbit.apache.org/filevault-package-maven-plugin/)
>
>* Le `content-package-maven-plugin` ne prend plus en charge les packages à partir de la version 1.0.2.
>* Cet article décrit comment le **déploiement** des packages construits dans AEM est effectué par le plug-in Maven Content Package d’Adobe.

## Packages et structure de projet AEM {#aem-project-structure}

AEM as a Cloud Service adhère aux bonnes pratiques les plus récentes en matière de gestion de packages et de structure de projet, telles qu’elles sont implémentées par le dernier archétype de projet AEM.

>[!TIP]
>
>Voir [AEM structure de projet](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=fr) de la documentation as a Cloud Service AEM et de la [AEM Archétype de projet](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) la documentation. Les deux implémentations sont entièrement prises en charge pour AEM 6.5.

## Obtention du plug-in Maven Content Package {#obtaining-the-content-package-maven-plugin}

Le plug-in est disponible à partir du [référentiel Maven central.](https://mvnrepository.com/artifact/com.day.jcr.vault/content-package-maven-plugin?repo=adobe-public)

## Objectifs et paramètres du plug-in Maven Content Package

Pour utiliser le plug-in Content Package Maven, ajoutez l’élément de plug-in suivant à l’élément build de votre fichier POM :

```xml
<plugin>
 <groupId>com.day.jcr.vault</groupId>
 <artifactId>content-package-maven-plugin</artifactId>
 <version>1.0.4</version>
 <configuration>
       <!-- parameters and values common to all goals, as required -->
 </configuration>
</plugin>
```

Pour permettre à Maven de télécharger le plug-in, utilisez le profil fourni dans la section [Obtention du plug-in Content Package Maven](#obtaining-the-content-package-maven-plugin) sur cette page.

## Version du plug-in Content Package Maven : {#goals-of-the-content-package-maven-plugin}

Les objectifs et les paramètres d’objectif fournis par le plug-in Content Package sont décrits dans les sections qui suivent. Les paramètres qui sont décrits dans la section Paramètres communs peuvent être utilisés pour la plupart des objectifs. Les paramètres qui s’appliquent à un objectif sont décrits dans la section consacrée à l’objectif en question.

### Préfixe du plug-in {#plugin-prefix}

Le préfixe du plug-in est `content-package`. Utilisez ce préfixe pour exécuter un objectif à partir de la ligne de commande, comme illustré ci-après.

```shell
mvn content-package:build
```

### Préfixe des paramètres {#parameter-prefix}

Sauf indication contraire, les objectifs et les paramètres du plug-in utilisent le préfixe `vault`, comme illustré ci-après.

```shell
mvn content-package:install -Dvault.targetURL="https://192.168.1.100:4502/crx/packmgr/service.jsp"
```

### Proxys {#proxies}

Les objectifs qui utilisent des proxys pour AEM ont recours à la première configuration de proxy valide dans les paramètres Maven. Si aucune configuration de proxy n’est trouvée, aucun proxy n’est utilisé. Reportez-vous au paramètre `useProxy` dans la section [Paramètres communs](#common-parameters).

### Paramètres communs {#common-parameters}

Les paramètres contenus dans le tableau ci-après sont communs à tous les objectifs, sauf si une note indique le contraire dans la colonne **Objectifs**.

| Nom | Type | Requis | Valeur par défaut | Description | Objectifs |
|---|---|---|---|---|---|
| `failOnError` | `boolean` | Non | `false` | La valeur `true` entraîne l’échec de la compilation lorsqu’une erreur se produit. La valeur `false` entraîne la création à ignorer l’erreur. | Tous les objectifs, à l’exception de `package` |
| `name` | `String` | `build` : Oui, `install` : Non, `rm` : Oui | `build` : Pas de valeur par défaut, `install` : Valeur de la propriété `artifactId` du projet Maven | Nom du package sur lequel exécuter une action | Tous les objectifs, à l’exception de `ls` |
| `password` | `String` | Oui | `admin` | Mot de passe utilisé pour l’authentification avec AEM | Tous les objectifs, à l’exception de `package` |
| `serverId` | `String` | Non | ID du serveur à partir duquel récupérer le nom d’utilisateur et le mot de passe pour l’authentification | Tous les objectifs, à l’exception de `package` |
| `targetURL` | `String` | Oui | `http://localhost:4502/crx/packmgr/service.jsp` | URL de l’API du service HTTP du gestionnaire de packages AEM | Tous les objectifs, à l’exception de `package` |
| `timeout` | `int` | Non | `5` | Délai de connexion, exprimé en secondes, pour communiquer avec le service du gestionnaire de packages | Tous les objectifs, à l’exception de `package` |
| `useProxy` | `boolean` | Non | `true` | La valeur `true` entraîne l’utilisation par Maven de la première configuration de proxy active trouvée en réponse aux requêtes de proxy au gestionnaire de packages. | Tous les objectifs, à l’exception de `package` |
| `userId` | `String` | Oui | `admin` | Nom d’utilisateur à authentifier avec AEM | Tous les objectifs, à l’exception de `package` |
| `verbose` | `boolean` | Non | `false` | Active ou désactive la journalisation documentée | Tous les objectifs, à l’exception de `package` |

### build {#build}

Crée un package de contenu déjà défini sur une instance AEM.

>[!NOTE]
>
>Il n’est pas nécessaire que l’objectif soit exécuté dans un projet Maven.

#### Paramètres {#parameters}

Tous les paramètres de l’objectif de build sont décrits dans la section [Paramètres communs](#common-parameters).

### install {#install}

Installe un package dans le référentiel. L’exécution de cet objectif ne nécessite pas de projet Maven. L’objectif est lié à la phase `install` du cycle de vie de compilation Maven.

#### Paramètres {#parameters-1}

En plus des paramètres suivants, consultez les descriptions de la section [Paramètres communs](#common-parameters).

| Nom | Type | Requis | Valeur par défaut | Description |
|---|---|---|---|---|
| `artifact` | `String` | Non | Valeur de la propriété `artifactId` du projet Maven | Chaîne au format `groupId:artifactId:version[:packaging]` |
| `artifactId` | `String` | Non | Aucune | ID de l’artefact à installer. |
| `groupId` | `String` | Non | Aucune | `groupId` de l’artefact à installer |
| `install` | `boolean` | Non | `true` | Détermine si le package doit être décompressé automatiquement lorsqu’il est chargé |
| `localRepository` | `org.apache.maven.artifact.repository.ArtifactRepository` | Non | Valeur de la variable système `localRepository` | Référentiel Maven local qui ne peut pas appliquer la configuration du plug-in car la propriété système est toujours utilisée |
| `packageFile` | `java.io.File` | Non | artefact principal défini pour le projet Maven | Nom du fichier de package à installer |
| `packaging` | `String` | Non | `zip` | Type de groupement de l’artefact à installer. |
| `pomRemoteRepositories` | `java.util.List` | Oui | Valeur de la propriété `remoteArtifactRepositories` définie pour le projet Maven | Cette valeur ne peut pas appliquer la configuration du plug-in et doit être spécifiée dans le projet. |
| `project` | `org.apache.maven.project.MavenProject` | Oui | Projet pour lequel le plug-in est configuré | Le projet Maven implicite, car il contient la configuration du plug-in |
| `repositoryId` (POM), `repoID` (ligne de commande) | `String` | Non | `temp` | ID du référentiel duquel est récupéré l’artefact |
| `repositoryUrl` (POM), `repoURL` (ligne de commande) | `String` | Non | Aucune | URL du référentiel duquel est récupéré l’artefact |
| version | Chaîne | Non | Aucune | Version de l’artefact à installer |

### ls {#ls}

Répertorie les packages déployés dans le [Gestionnaire de packages](/help/implementing/developing/tools/package-manager.md).

#### Paramètres {#parameters-2}

Tous les paramètres de l’objectif sont décrits dans la section [Paramètres communs](#common-parameters).

### rm {#rm}

Supprime un package du [Gestionnaire de packages](/help/implementing/developing/tools/package-manager.md).

#### Paramètres {#parameters-3}

Tous les paramètres de l’objectif rm sont décrits dans la section [Paramètres communs](#common-parameters).

### uninstall {#uninstall}

Désinstalle un package. Le package reste sur le serveur avec l’état désinstallé.

#### Paramètres {#parameters-4}

Tous les paramètres de l’objectif uninstall sont décrits dans la section [Paramètres communs](#common-parameters).

### package {#package}

Crée un package de contenu. La configuration par défaut de l’objectif du package comprend le contenu du répertoire dans lequel les fichiers compilés sont enregistrés. L’exécution de l’objectif du package requiert que la phase de création de la compilation soit terminée. L’objectif est lié à la phase de package du cycle de vie de compilation Maven.

#### Paramètres {#parameters-5}

Outre les paramètres suivants, consultez la description du paramètre `name` dans la section [Paramètres communs](#common-parameters).

| Nom | Type | Requis | Valeur par défaut | Description |
|---|---|---|---|---|
| `archive` | `org.apache.maven.archiver.MavenArchiveConfiguration` | Non | Aucune | Configuration d’archive à utiliser |
| `builtContentDirectory` | `java.io.File` | Oui | Valeur du répertoire de sortie de la compilation Maven | Répertoire qui comporte le contenu à inclure dans le package |
| `dependencies` | `java.util.List` | Non | Aucune |  |
| `embeddedTarget` | `java.lang.String` | Non | Aucune |  |
| `embeddeds` | `java.util.List` | Non | Aucune |  |
| `failOnMissingEmbed` | `boolean` | Oui | `false` | La valeur `true` entraîne l’échec de la compilation lorsqu’un artefact incorporé n’est pas trouvé dans les dépendances du projet. La valeur `false` entraîne l’absence de prise en compte de l’erreur par la création. |
| `filterSource` | `java.io.File` | Non | Aucune | Ce paramètre définit un fichier qui spécifie la source du filtre de l’espace de travail. Les filtres spécifiés dans le fichier de configuration et injectés via les incorporations ou les sous-packages sont fusionnés avec le contenu du fichier. |
| `filters` | `com.day.jcr.vault.maven.pack.impl.DefaultWorkspaceFilter` | Non | Aucune | Ce paramètre contient les éléments de filtre qui définissent le contenu du package. Lorsqu’ils sont exécutés, les filtres sont inclus dans le fichier `filter.xml`. Voir la section [Utilisation des filtres](#using-filters) ci-dessous. |
| `finalName` | `java.lang.String` | Oui | Paramètre `finalName` défini dans le projet Maven (phase de compilation) | Nom du fichier zip du package généré sans extension `.zip` |
| `group` | `java.lang.String` | Oui | `groupID` défini dans le projet Maven. | `groupId` du package de contenu généré, qui fait partie du chemin d’installation cible pour le package de contenu |
| `outputDirectory` | `java.io.File` | Oui | Répertoire build défini dans le projet Maven | Répertoire local dans lequel est enregistré le package de contenu |
| `prefix` | `java.lang.String` | Non | Aucune |  |
| `project` | `org.apache.maven.project.MavenProject` | Oui | Aucune | Projet Maven |
| `properties` | `java.util.Map` | Non | Aucune | Ces paramètres définissent des propriétés supplémentaires que vous pouvez définir dans le fichier `properties.xml`. Ces propriétés ne peuvent pas remplacer les propriétés prédéfinies suivantes : `group` (utiliser le paramètre `group` à définir), `name` (utiliser le paramètre `name` à définir), `version` (utiliser le paramètre `version` à définir), `description` (fixé à partir de la description du projet), `groupId` (`groupId` du descripteur de projet Maven), `artifactId` (`artifactId` du descripteur de projet Maven), `dependencies` (utiliser le paramètre `dependencies` à définir), `createdBy` (valeur de la propriété système `user.name`), `created` (temps système actuel), `requiresRoot` (utiliser le paramètre `requiresRoot` à définir), `packagePath` (généré automatiquement à partir du groupe et du nom du package) |
| `requiresRoot` | `boolean` | Oui | false | Définit si le package requiert ou non root. Devient la propriété `requiresRoot` du fichier `properties.xml`. |
| `subPackages` | `java.util.List` | Non | Aucune |  |
| `version` | `java.lang.String` | Oui | Version définie dans le projet Maven. | Version du package de contenu |
| `workDirectory` | `java.io.File` | Oui | Répertoire défini dans le projet Maven (phase de compilation) | Répertoire qui comporte le contenu à inclure dans le package |

#### Utilisation de l’élément filters {#using-filters}

Utilisez l’élément filters pour définir le contenu du package. Les filtres sont ajoutés à l’élément `workspaceFilter` du fichier `META-INF/vault/filter.xml` du package.

L’exemple de filtre suivant montre la structure XML à utiliser :

```xml
<filter>
   <root>/apps/myapp</root>
   <mode>merge</mode>
       <includes>
              <include>/apps/myapp/install/</include>
              <include>/apps/myapp/components</include>
       </includes>
       <excludes>
              <exclude>/apps/myapp/config/*</exclude>
       </excludes>
</filter>
```

##### Mode d’importation {#import-mode}

L’élément `mode` définit l’impact de l’importation du package sur le contenu du référentiel. Les valeurs suivantes peuvent être utilisées :

* **Fusionner** : le contenu du package ne se trouvant pas encore dans le référentiel est ajouté. Le contenu se trouvant dans le package et le référentiel reste inchangé. Aucun contenu n’est supprimé du référentiel.
* **Remplacer** : le contenu du package absent du référentiel y est ajouté. Le contenu du référentiel est remplacé par le contenu correspondant du package. Le contenu est supprimé du référentiel lorsqu’il n’existe pas dans le package.
* **Mettre à jour** : le contenu du package ne se trouvant pas dans le référentiel y est ajouté. Le contenu du référentiel est remplacé par le contenu correspondant du package.

Lorsque le filtre ne contient pas d’élément `mode`, la valeur `replace` par défaut est utilisée.

### help {#help}

#### Paramètres {#parameters-6}

| Nom | Type | Requis | Valeur par défaut | Description |
|---|---|---|---|---|
| `detail` | `boolean` | Non | `false` | Détermine si toutes les propriétés définissables doivent être affichées ou non pour chaque objectif |
| `goal` | `String` | Non | Aucune | Ce paramètre définit le nom de l’objectif pour lequel afficher l’aide. Si aucune valeur n’est spécifiée, l’aide est affichée pour tous les objectifs. |
| `indentSize` | `int` | Non | `2` | Nombre d’espaces à utiliser pour le retrait de chaque niveau (doit être positif s’il est défini) |
| `lineLength` | `int` | Non | `80` | Longueur maximale d’une ligne d’affichage (doit être positive si elle est définie) |

## Inclusion d’une image de miniature ou d’un fichier de propriétés dans le package {#including-a-thumbnail-image-or-properties-file-in-the-package}

Remplacez les fichiers de configuration du package par défaut afin de personnaliser les propriétés du package. Incluez, par exemple, une image miniature pour différencier le package dans le [Gestionnaire de packages](/help/implementing/developing/tools/package-manager.md).

Les fichiers sources peuvent se trouver n’importe où dans le système de fichiers. Dans le fichier POM, définissez les ressources de création pour copier les fichiers sources dans `target/vault-work/META-INF` à des fins d’inclusion dans le package.

Le code POM suivant ajoute au package les fichiers du dossier `META-INF` de la source du projet :

```xml
<build>
    <resources>
        <!-- vault META-INF resources (thumbnail and so on) -->
        <resource>
            <directory>${basedir}/src/main/content/META-INF</directory>
            <targetPath>../vault-work/META-INF</targetPath>
        </resource>
    </resources>
</build>
```

Le code POM ci-après ajoute uniquement une image miniature au package. L’image miniature doit être appelée `thumbnail.png` et figurer dans le dossier `META-INF/vault/definition` du package. Dans cet exemple, le fichier source se trouve dans le dossier `/src/main/content/META-INF/vault/definition` du projet :

```xml
<build>
    <resources>
        <!-- thumbnail only -->
        <resource>
            <directory>${basedir}/src/main/content/META-INF/vault/definition</directory>
            <targetPath>../vault-work/META-INF/vault/definition</targetPath>
        </resource>
    </resources>
</build>
```

## Utilisation de l’archétype de projet AEM pour générer des projets AEM {#using-archetypes}

Le dernier archétype de projet AEM met en œuvre la structure de package des bonnes pratiques pour les implémentations On-Premise et AMS et est recommandé pour tous les projets AEM.

>[!TIP]
>
>Voir [AEM structure de projet](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=fr) de la documentation as a Cloud Service AEM et de la [AEM Archétype de projet](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) la documentation. Les deux implémentations sont entièrement prises en charge pour AEM 6.5.
