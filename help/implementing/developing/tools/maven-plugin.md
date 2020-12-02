---
title: Module externe Maven du package de contenu Adobe
description: Utilisez le module externe Content Package Maven pour déployer AEM applications
translation-type: tm+mt
source-git-commit: 2cdbbe9b8f6608cbdd299889be515d421e3d9ad3
workflow-type: tm+mt
source-wordcount: '1857'
ht-degree: 46%

---


# Module externe Maven du package de contenu d&#39;Adobe {#adobe-content-package-maven-plugin}

Utilisez le module externe Adobe Content Package Maven pour intégrer des tâches de déploiement et de gestion de modules dans vos projets Maven.

Le déploiement des packages construits sur AEM est effectué par le module externe Adobe Content Package Maven et permet l’automatisation des tâches normalement exécutées à l’aide d’AEM Package Manager :

* Création de packages à partir des fichiers du système de fichiers
* Installez et désinstallez les packages sur AEM.
* Créez des packages déjà définis sur AEM.
* Procurez-vous une liste de packages installés sur AEM.
* Supprimez un package de AEM.

Ce document décrit comment utiliser l&#39;expert pour gérer ces tâches. Cependant, il est également important de comprendre [comment les projets AEM et leurs paquets sont structurés.](#aem-project-structure)

>[!NOTE]
>
>La création de package est désormais détenue par le [module externe Apache Jackrabbit FileVault Package Maven](https://jackrabbit.apache.org/filevault-package-maven-plugin/). Le déploiement des packages construits sur AEM est effectué par le module externe Adobe Content Package Maven, comme décrit ici.

## Packages et structure de projet AEM {#aem-project-structure}

aem 6.5 respecte les meilleures pratiques en matière de gestion des paquets et de structure des projets, telles qu&#39;elles sont mises en oeuvre par le dernier AEM Project Archetype pour les mises en oeuvre sur site et AMS.

>[!TIP]
>
>Pour plus d&#39;informations, consultez l&#39;article [AEM Project Structure](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) de l&#39;AEM sous la forme d&#39;une documentation Cloud Service ainsi que la documentation [AEM Project Archetype](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/developing/archetype/overview.html). Les deux sont entièrement pris en charge pour AEM 6.5.

## Obtention du module externe Content Package Maven {#obtaining-the-content-package-maven-plugin}

Le plug-in est disponible à partir du [référentiel Maven Central.](https://mvnrepository.com/artifact/com.day.jcr.vault/content-package-maven-plugin?repo=adobe-public)

## Objectifs et paramètres du module externe Content Package Maven

Pour utiliser le module externe Content Package Maven, ajoutez l’élément plugin suivant dans l’élément build du fichier POM :

```xml
<plugin>
 <groupId>com.day.jcr.vault</groupId>
 <artifactId>content-package-maven-plugin</artifactId>
 <version>0.0.24</version>
 <configuration>
       <!-- parameters and values common to all goals, as required -->
 </configuration>
</plugin>
```

Pour que Maven puisse télécharger le module externe, utilisez le profil fourni dans la section [Obtention du module externe Content Package Maven](#obtaining-the-content-package-maven-plugin) de cette page.

## Version du module externe Content Package Maven :  {#goals-of-the-content-package-maven-plugin}

Les goals et les paramètres de goal fournis par le module externe Content Package sont décrits dans les sections qui suivent. Les paramètres qui sont décrits dans la section Paramètres communs peuvent être utilisés pour la plupart des goals. Les paramètres qui s’appliquent à un goal sont décrits dans la section consacrée au goal en question.

### Préfixe du module externe {#plugin-prefix}

Le préfixe du module externe est `content-package`. Utilisez ce préfixe pour exécuter un goal à partir de la ligne de commande, comme illustré ci-après.

```shell
mvn content-package:build
```

### Préfixe des paramètres {#parameter-prefix}

Sauf indication contraire, les objectifs et paramètres du module externe utilisent le préfixe `vault`, comme dans l’exemple suivant :

```shell
mvn content-package:install -Dvault.targetURL="https://192.168.1.100:4502/crx/packmgr/service.jsp"
```

### Proxys {#proxies}

Les objectifs qui utilisent des proxies pour AEM utilisent la première configuration de proxy valide trouvée dans les paramètres Maven. Si aucune configuration de proxy n’est trouvée, aucun proxy n’est utilisé. Voir le paramètre `useProxy` dans la section [Paramètres communs](#common-parameters).

### Paramètres communs {#common-parameters}

Les paramètres du tableau suivant sont communs à tous les objectifs, sauf lorsqu&#39;ils sont indiqués dans la colonne **Objectifs**.

| Nom | Type | Requis | Valeur par défaut | Description | Goals |
|---|---|---|---|---|---|
| `failOnError` | `boolean` | Non | `false` | La valeur `true` entraîne l’échec de la création lorsqu’une erreur se produit. La valeur `false` entraîne la création à ignorer l’erreur. | Tous les objectifs sauf `package` |
| `name` | `String` | `build`: Oui,  `install`: Non,  `rm`: Oui | `build`: Pas de valeur par défaut,  `install`: Valeur de la  `artifactId` propriété du projet Maven | Nom du package sur lequel exécuter une action | Tous les objectifs sauf `ls` |
| `password` | `String` | Oui | `admin` | Mot de passe utilisé pour l&#39;authentification avec AEM | Tous les objectifs sauf `package` |
| `serverId` | `String` | Non | ID du serveur à partir duquel récupérer le nom d’utilisateur et le mot de passe pour l’authentification | Tous les objectifs sauf `package` |
| `targetURL` | `String` | Oui | `http://localhost:4502/crx/packmgr/service.jsp` | URL de l’API du service HTTP du gestionnaire de packages AEM | Tous les objectifs sauf `package` |
| `timeout` | `int` | Non | `5` | Délai de connexion, exprimé en secondes, pour communiquer avec le service du gestionnaire de packages | Tous les objectifs sauf `package` |
| `useProxy` | `boolean` | Non | `true` | Si la valeur `true` est définie, Maven utilise la première configuration de proxy principale trouvée pour envoyer des demandes de proxy à Package Manager. | Tous les objectifs sauf `package` |
| `userId` | `String` | Oui | `admin` | Nom d’utilisateur à authentifier avec AEM | Tous les objectifs sauf `package` |
| `verbose` | `boolean` | Non | `false` | Active ou désactive la journalisation documentée | Tous les objectifs sauf `package` |

### build {#build}

Crée un package de contenu qui est déjà défini sur une instance AEM.

>[!NOTE]
>
>Il n’est pas nécessaire que le goal soit exécuté dans un projet Maven.

#### Paramètres {#parameters}

Tous les paramètres de l&#39;objectif de génération sont décrits dans la section [Paramètres communs](#common-parameters).

### install {#install}

Installe un package dans le référentiel. L’exécution de ce goal ne nécessite pas de projet Maven. L&#39;objectif est lié à la phase `install` du cycle de vie de la génération Maven.

#### Paramètres {#parameters-1}

Outre les paramètres suivants, consultez les descriptions de la section [Paramètres communs](#common-parameters).

| Nom | Type | Requis | Valeur par défaut | Description |
|---|---|---|---|---|---|
| `artifact` | `String` | Non | Valeur de la propriété `artifactId` du projet Maven | Chaîne du formulaire `groupId:artifactId:version[:packaging]` |
| `artifactId` | `String` | Non | Aucune | ID de l’artifact à installer. |
| `groupId` | `String` | Non | Aucune | `groupId` de l&#39;artefact à installer |
| `install` | `boolean` | Non | `true` | Détermine si le package doit être décompressé automatiquement lorsqu’il est téléchargé |
| `localRepository` | `org.apache.maven.artifact.repository.ArtifactRepository` | Non | Valeur de la variable système `localRepository` | Le référentiel Maven local qui ne peut pas être configuré à l&#39;aide de la configuration du module car la propriété système est toujours utilisée |
| `packageFile` | `java.io.File` | Non | artifact principal défini pour le projet Maven | Nom du fichier de package à installer |
| `packaging` | `String` | Non | `zip` | Type de package de l’artifact à installer. |
| `pomRemoteRepositories` | `java.util.List` | Oui | Valeur de la propriété `remoteArtifactRepositories` définie pour le projet Maven | Cette valeur ne peut pas être configurée à l&#39;aide de la configuration du module externe et doit être spécifiée dans le projet. |
| `project` | `org.apache.maven.project.MavenProject` | Oui | Projet pour lequel le plugin est configuré | Projet Maven implicite car le projet contient la configuration du module externe |
| `repositoryId` (POM),  `repoID` (ligne de commande) | `String` | Non | `temp` | ID du référentiel duquel est récupéré l’artifact |
| `repositoryUrl` (POM),  `repoURL` (ligne de commande) | `String` | Non | Aucune | URL du référentiel duquel est récupéré l’artifact |
| version | Chaîne | Non | Aucune | Version de l’artifact à installer |

### ls {#ls}

Répertorie les packages qui sont déployés dans Package Manager.

#### Paramètres {#parameters-2}

Tous les paramètres de l&#39;objectif ls sont décrits dans la section [Paramètres communs](#common-parameters).

### rm {#rm}

Supprime un package de Package Manager.

#### Paramètres {#parameters-3}

Tous les paramètres de l&#39;objectif rm sont décrits dans la section [Paramètres communs](#common-parameters).

### uninstall {#uninstall}

Désinstalle un package. Le package reste sur le serveur avec l’état désinstallé.

#### Paramètres {#parameters-4}

Tous les paramètres de l&#39;objectif de désinstallation sont décrits dans la section [Paramètres communs](#common-parameters).

### package {#package}

Crée un package de contenu. La configuration par défaut du goal du package comprend le contenu du répertoire dans lequel les fichiers compilés sont enregistrés. L’exécution du goal du package requiert que la phase de création de la compilation soit terminée. Le goal est lié à la phase de package du cycle de vie de création Maven.

#### Paramètres {#parameters-5}

Outre les paramètres suivants, voir la description du paramètre `name` dans la section [Paramètres communs](#common-parameters).

| Nom | Type | Requis | Valeur par défaut | Description |
|---|---|---|---|---|
| `archive` | `org.apache.maven.archiver.MavenArchiveConfiguration` | Non | Aucune | Configuration d’archive à utiliser |
| `builtContentDirectory` | `java.io.File` | Oui | Valeur du répertoire de sortie de la build Maven | Répertoire qui comporte le contenu à inclure dans le package |
| `dependencies` | `java.util.List` | Non | Aucune |  |
| `embeddedTarget` | `java.lang.String` | Non | Aucune |  |
| `embeddeds` | `java.util.List` | Non | Aucune |  |
| `failOnMissingEmbed` | `boolean` | Oui | `false` | Une valeur `true` provoque l’échec de la build lorsqu’un artefact incorporé est introuvable dans les dépendances du projet. Si la valeur `false` est définie, la build ignore ces erreurs. |
| `filterSource` | `java.io.File` | Non | Aucune | Ce paramètre définit un fichier qui spécifie la source du filtre de l&#39;espace de travail. Les filtres spécifiés dans le fichier de configuration et injectés via les incorporations ou les sous-packages sont fusionnés avec le contenu du fichier. |
| `filters` | `com.day.jcr.vault.maven.pack.impl.DefaultWorkspaceFilter` | Non | Aucune | Ce paramètre contient des éléments de filtre qui définissent le contenu du package. Une fois exécutés, les filtres sont inclus dans le fichier `filter.xml`. Voir la section [Utilisation de Filtres](#using-filters) ci-dessous. |
| `finalName` | `java.lang.String` | Oui | `finalName` défini dans le projet Maven (phase de création) | Nom du fichier ZIP du package généré, sans l&#39;extension de fichier `.zip` |
| `group` | `java.lang.String` | Oui | Le `groupID` défini dans le projet Maven | `groupId` du package de contenu généré qui fait partie du chemin d’installation de la cible pour le package de contenu |
| `outputDirectory` | `java.io.File` | Oui | Répertoire build défini dans le projet Maven | Répertoire local dans lequel est enregistré le package de contenu |
| `prefix` | `java.lang.String` | Non | Aucune |  |
| `project` | `org.apache.maven.project.MavenProject` | Oui | Aucune | Projet Maven |
| `properties` | `java.util.Map` | Non | Aucune | Ces paramètres définissent des propriétés supplémentaires que vous pouvez définir dans le fichier `properties.xml`. Ces propriétés ne peuvent pas remplacer les propriétés prédéfinies suivantes : `group` (utiliser le paramètre `group` pour définir), `name` (utiliser le paramètre `name` pour définir), `version` (utiliser le paramètre `version` pour définir), `description` (défini à partir de la description du projet), `groupId` (`groupId` du descripteur de projet Maven), `artifactId` (`artifactId`) descripteur de projet Maven), `dependencies` (utilisez le paramètre `dependencies` pour définir), `createdBy` (valeur de la propriété système `user.name`), `created` (heure système actuelle), `requiresRoot` (utilisez le paramètre `requiresRoot` pour définir), `packagePath` (généré automatiquement à partir du nom du groupe et du package) |
| `requiresRoot` | `boolean` | Oui | false | Définit si le package requiert ou non root. Cela deviendra la propriété `requiresRoot` du fichier `properties.xml`. |
| `subPackages` | `java.util.List` | Non | Aucune |  |
| `version` | `java.lang.String` | Oui | Version définie dans le projet Maven. | version du package de contenu |
| `workDirectory` | `java.io.File` | Oui | Répertoire défini dans le projet Maven (phase build) | Répertoire qui comporte le contenu à inclure dans le package |

#### Utilisation de l’élément filters {#using-filters}

Utilisez l’élément filters pour définir le contenu du package. Les filtres sont ajoutés à l&#39;élément `workspaceFilter` dans le fichier `META-INF/vault/filter.xml` du package.

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
* **Replace:** Le contenu du package qui ne se trouve pas dans le référentiel est ajouté au référentiel. Le contenu du référentiel est remplacé par le contenu correspondant du package. Le contenu est supprimé du référentiel lorsqu’il n’existe pas dans le package.
* **Mettre à jour** : le contenu du package ne se trouvant pas dans le référentiel y est ajouté. Le contenu du référentiel est remplacé par le contenu correspondant du package. Le contenu existant est supprimé du référentiel.

Lorsque le filtre ne contient pas d’élément `mode`, la valeur `replace` par défaut est utilisée.

### help {#help}

#### Paramètres {#parameters-6}

| Nom | Type | Requis | Valeur par défaut | Description |
|---|---|---|---|---|
| `detail` | `boolean` | Non | `false` | Détermine si toutes les propriétés définissables doivent être affichées ou non pour chaque goal |
| `goal` | `String` | Non | Aucune | Ces paramètres définissent le nom de l’objectif pour lequel afficher l’aide. Si aucune valeur n’est spécifiée, l’aide est affichée pour tous les goals. |
| `indentSize` | `int` | Non | `2` | Nombre d’espaces à utiliser pour le retrait de chaque niveau (doit être positif s’il est défini) |
| `lineLength` | `int` | Non | `80` | Longueur maximale d’une ligne d’affichage (doit être positive si elle est définie) |

## Inclusion d’une image de miniature ou d’un fichier de propriétés dans le package {#including-a-thumbnail-image-or-properties-file-in-the-package}

Remplacez les fichiers de configuration du package par défaut afin de personnaliser les propriétés du package. Incluez, par exemple, une image miniature pour différencier le package dans Package Manager et Package Share.

Les fichiers sources peuvent se trouver n’importe où dans le système de fichiers. Dans le fichier POM, définissez les ressources de génération pour copier les fichiers source dans `target/vault-work/META-INF` en vue de les inclure dans le package.

Le code POM suivant ajoute les fichiers du dossier `META-INF` de la source du projet au package :

```xml
<build>
    <resources>
        <!-- vault META-INF resources (thumbnail etc.) -->
        <resource>
            <directory>${basedir}/src/main/content/META-INF</directory>
            <targetPath>../vault-work/META-INF</targetPath>
        </resource>
    </resources>
</build>
```

Le code POM ci-après ajoute uniquement une image miniature au package. L’image miniature doit porter le nom `thumbnail.png` et se trouver dans le dossier `META-INF/vault/definition` du package. Dans cet exemple, le fichier source se trouve dans le dossier `/src/main/content/META-INF/vault/definition` du projet :

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

## Utilisation de l&#39;archétype de projet AEM pour générer des projets AEM {#using-archetypes}

Le dernier archétype de projet AEM met en oeuvre la structure d&#39;ensemble des meilleures pratiques pour les implémentations sur site et sur site et est recommandé pour tous les projets AEM.

>[!TIP]
>
>Pour plus d&#39;informations, consultez l&#39;article [AEM Project Structure](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) de l&#39;AEM sous la forme d&#39;une documentation Cloud Service ainsi que la documentation [AEM Project Archetype](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html). Les deux sont entièrement pris en charge pour AEM 6.5.
