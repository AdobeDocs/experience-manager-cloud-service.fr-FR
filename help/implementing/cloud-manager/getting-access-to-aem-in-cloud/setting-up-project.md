---
title: Configuration du projet
description: Découvrez comment les projets AEM sont créés avec Maven et les normes que vous devez respecter lors de la création de votre propre projet.
exl-id: 76af0171-8ed5-4fc7-b5d5-7da5a1a06fa8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: e7e12d78ace75ade7a2f3168191c410eecadf9d0
workflow-type: tm+mt
source-wordcount: '1348'
ht-degree: 49%

---

# Configuration du projet {#project-setup}

Découvrez comment les projets AEM sont créés avec Maven et les normes que vous devez respecter lors de la création de votre propre projet.

## Détails de configuration du projet {#project-setup-details}

Pour créer et déployer avec succès avec Cloud Manager, les projets AEM doivent respecter les instructions suivantes :

* Les projets doivent être créés à l’aide d’[ Apache Maven ](https://maven.apache.org).
* Un fichier `pom.xml` doit se trouver à la racine du référentiel Git. Ce fichier `pom.xml` référence autant de sous-modules (qui à leur tour comportent d’autres sous-modules, etc.) que nécessaire.
* Vous pouvez ajouter des références à d’autres référentiels d’artefact Maven dans vos fichiers `pom.xml`. L’accès aux [référentiels d’artefacts protégés par mot de passe](#password-protected-maven-repositories) est pris en charge s’il est configuré. Cependant, l’accès aux référentiels d’artefacts protégés par réseau n’est pas pris en charge.
* Cloud Manager détecte les packages de contenu déployables en analysant les fichiers `.zip` de packages de contenu se trouvant dans un répertoire appelé `target`. Un nombre illimité de sous-modules produit des packages de contenu.
* Cloud Manager détecte les artefacts Dispatcher déployables en analysant les fichiers `.zip` (également contenus dans le répertoire nommé `target`) dont les répertoires sont nommés `conf` et `conf.d`.
* S’il existe plusieurs modules de contenu, l’ordre des déploiements des modules n’est pas garanti. Si un ordre spécifique est nécessaire, il est possible d’utiliser les dépendances de module de contenu pour le définir.
* Les packages sont [ignorés](#skipping-content-packages) lors du déploiement.

## Activer des profils Maven dans Cloud Manager {#activating-maven-profiles-in-cloud-manager}

Dans certains cas, vous pouvez légèrement modifier votre processus de génération lors de l’exécution dans Cloud Manager par opposition à celui exécuté sur les postes de travail des développeurs. Pour ces cas, les [profils Maven](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) définissent la manière dont la version diffère selon les environnements, y compris Cloud Manager.

L’activation d’un profil Maven dans l’environnement de génération Cloud Manager doit se faire en recherchant la présence de la [variable d’environnement](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) `CM_BUILD`. De même, un profil destiné à être utilisé uniquement en dehors de l’environnement de création Cloud Manager est configuré en vérifiant l’absence de cette variable.

Par exemple, si vous souhaitez générer un message simple uniquement lorsque la version est exécutée dans Cloud Manager, procédez comme suit :

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running inside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

>[!NOTE]
>
>Pour tester ce profil sur un poste de travail de développeur, vous pouvez l’activer sur la ligne de commande (avec `-PcmBuild`) ou dans l’environnement de développement intégré (IDE).

Et si vous souhaitez générer un message simple uniquement lorsque la version est exécutée en dehors de Cloud Manager, procédez comme suit :

```xml
        <profile>
            <id>notCMBuild</id>
            <activation>
                  <property>
                        <name>[!NOTE]nv.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running outside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

## Utiliser un référentiel Maven protégé par mot de passe dans Cloud Manager {#password-protected-maven-repositories}

>[!NOTE]
>
>Déployez les artefacts des référentiels Maven protégés par mot de passe avec précaution, car Cloud Manager n’évalue pas ce code avec ses [règles de qualité du code](/help/implementing/cloud-manager/custom-code-quality-rules.md). Cette méthode ne doit être utilisée que dans des situations spécifiques et s’applique uniquement au code non lié à AEM. Adobe recommande d’inclure les sources Java et l’intégralité du code source du projet avec le binaire. Cela garantit une plus grande transparence et maintenabilité tout au long du processus de déploiement.

**Pour utiliser un référentiel Maven protégé par mot de passe dans Cloud Manager :**

1. Indiquez le mot de passe (et éventuellement le nom d’utilisateur) comme [variable de pipeline](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) secrète.
1. Référencez ensuite ce secret dans un fichier nommé `.cloudmanager/maven/settings.xml` dans le référentiel git, qui suit le schéma du [fichier des paramètres Maven](https://maven.apache.org/settings.html).

Lorsque le processus de création de Cloud Manager démarre :

* L’élément `<servers>` dans ce fichier est fusionné dans le fichier `settings.xml` par défaut fourni par Cloud Manager.
   * Les ID de serveur commençant par `adobe` et `cloud-manager` sont considérés comme réservés. Ne les utilisez pas sur des serveurs personnalisés.
   * Cloud Manager met en miroir uniquement les ID de serveur qui correspondent à des préfixes spécifiques ou à l’ID par défaut `central` ; tous les autres ID de serveur sont exclus de la mise en miroir.
* Une fois ce fichier en place, référencez l’ID de serveur à l’intérieur d’un élément `<repository>` et/ou `<pluginRepository>` dans le fichier `pom.xml`.
* Ces éléments `<repository>` et `<pluginRepository>` sont inclus dans un profil spécifique à [Cloud Manager](#activating-maven-profiles-in-cloud-manager) mais leur inclusion n’est pas strictement requise.

Supposons, par exemple, que le référentiel se trouve à l’adresse `https://repository.myco.com/maven2`, que le nom d’utilisateur utilisé par Cloud Manager soit `cloudmanager` et que le mot de passe soit `secretword`. Procédez comme suit :

1. Définissez le mot de passe comme secret sur le pipeline.

   ```text
   $ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword`
   ```

1. Référencez ce secret à partir du fichier `.cloudmanager/maven/settings.xml` dans ce qui suit :

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <settings xmlns="https://maven.apache.org/SETTINGS/1.0.0" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
           xsi:schemaLocation="https://maven.apache.org/SETTINGS/1.0.0 https://maven.apache.org/xsd/settings-1.0.0.xsd">
       <servers>
           <server>
               <id>myco-repository</id>
               <username>cloudmanager</username>
              <password>${env.CUSTOM_MYCO_REPOSITORY_PASSWORD}</password>
           </server>
       </servers>
   </settings>
   ```

1. Enfin, référencez l’identifiant du serveur dans le fichier `pom.xml` :

   ```xml
   <profiles>
       <profile>
           <id>cmBuild</id>
           <activation>
                   <property>
                       <name>env.CM_BUILD</name>
                   </property>
           </activation>
           <repositories>
                <repository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </repository>
            </repositories>
            <pluginRepositories>
                <pluginRepository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </pluginRepository>
            </pluginRepositories>
       </profile>
   </profiles>
   ```

### Déployer des sources {#deploying-sources}

Il est recommandé de déployer les sources Java avec le binaire dans un référentiel Maven.

Pour ce faire, configurez le plug-in maven-source-plugin dans votre projet.

```xml
         <plugin>
             <groupId>org.apache.maven.plugins</groupId>
             <artifactId>maven-source-plugin</artifactId>
             <executions>
                 <execution>
                     <id>attach-sources</id>
                     <goals>
                         <goal>jar-no-fork</goal>
                     </goals>
                 </execution>
             </executions>
         </plugin>
```

### Déployer des sources de projet {#deploying-project-sources}

Il est recommandé de déployer l’ensemble de la source du projet avec le binaire dans un référentiel Maven. Vous pouvez ainsi reconstruire l’artefact exact.

Configurez le plug-in maven-assembly dans votre projet comme suit :

```xml
         <plugin>
             <groupId>org.apache.maven.plugins</groupId>
             <artifactId>maven-assembly-plugin</artifactId>
             <executions>
                 <execution>
                     <id>project-assembly</id>
                     <phase>package</phase>
                     <goals>
                         <goal>single</goal>
                     </goals>
                     <configuration>
                         <descriptorRefs>
                             <descriptorRef>project</descriptorRef>
                         </descriptorRefs>
                     </configuration>
                 </execution>
             </executions>
         </plugin>
```

## Ignorer les modules de contenu {#skipping-content-packages}

Dans Cloud Manager, les versions produisent un nombre illimité de packages de contenu. Pour diverses raisons, il est préférable de produire un package de contenu, mais de ne pas le déployer. Un exemple se produit lorsque les packages de contenu sont créés uniquement à des fins de test ou lorsqu’une autre étape du processus de création les recompresse. C&#39;est-à-dire un sous-package d&#39;un autre package.

Pour tenir compte de ces scénarios, Cloud Manager recherche une propriété nommée `cloudManagerTarget` dans les propriétés des modules de contenu créés. Si cette propriété est définie sur `none`, le package est ignoré et n’est pas déployé.

Le mécanisme permettant de définir cette propriété dépend de la manière dont le build produit le module de contenu. Par exemple, avec le `filevault-maven-plugin` , vous configurez le plug-in comme suit.

```xml
        <plugin>
            <groupId>org.apache.jackrabbit</groupId>
            <artifactId>filevault-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

Le `content-package-maven-plugin` a une configuration similaire.

```xml
        <plugin>
            <groupId>com.day.jcr.vault</groupId>
            <artifactId>content-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

## Réutilisation des artefacts de build {#build-artifact-reuse}

Dans de nombreux cas, le même code est déployé dans plusieurs environnements AEM. Dans la mesure du possible, Cloud Manager évite de reconstruire la base du code lorsqu’il détecte que la même validation Git est utilisée dans plusieurs exécutions de pipelines de piles pleines.

Lorsqu’une exécution est lancée, la validation HEAD en cours pour le pipeline de branche est extraite. Le hachage de validation est visible dans l’interface utilisateur et via l’API. Une fois l’étape de build terminée, les artefacts obtenus sont stockés en fonction de ce hachage de validation et sont réutilisés dans les exécutions ultérieures du pipeline.

Les packages sont réutilisés sur plusieurs pipelines s’ils se trouvent dans le même programme. Lorsque vous recherchez des packages qui peuvent être réutilisés, AEM ignore les branches et réutilise les artefacts entre les branches.

En cas de réutilisation, les étapes de build et de qualité du code sont effectivement remplacées par les résultats de l’exécution initiale. Le fichier journal de l’étape de création répertorie les artefacts et les informations d’exécution qui ont été utilisées pour les créer à l’origine.

Voici un exemple dʼune telle sortie de journal.

```shell
The following build artifacts were reused from the prior execution 4 of pipeline 1 which used commit f6ac5e6943ba8bce8804086241ba28bd94909aef:
build/aem-guides-wknd.all-2021.1216.1101633.0000884042.zip (content-package)
build/aem-guides-wknd.dispatcher.cloud-2021.1216.1101633.0000884042.zip (dispatcher-configuration)
```

Le journal de l’étape de qualité du code contient des informations similaires.

### Exemples {#example-reuse}

#### Exemple 1 {#example-1}

Partez du principe que votre programme comporte deux pipelines de développement :

* Le pipeline 1 sur la branche `foo`
* Le pipeline 2 sur la branche `bar`

Les deux branches utilisent le même identifiant de validation.

1. L’exécution du pipeline 1 crée d’abord les packages normalement.
1. Ensuite, l’exécution du pipeline 2 réutilise les packages créés par le pipeline 1.

#### Exemple 2 {#example-2}

Partez du principe que votre programme comporte deux branches :

* Branche `foo`
* Branche `bar`

Les deux branches ont le même identifiant de validation.

1. Un pipeline de développement crée et exécute `foo`.
1. Par la suite, un pipeline de production crée et exécute `bar`.

Dans ce cas, l’artefact de `foo` est réutilisé pour le pipeline de production, car le même hachage de validation a été identifié.

### Opt-out {#opting-out}

Si vous le souhaitez, le comportement de réutilisation peut être désactivé pour des pipelines spécifiques en définissant la variable de pipeline `CM_DISABLE_BUILD_REUSE` sur `true`. Si cette variable est définie, le système extrait le hachage de validation et stocke les artefacts obtenus pour une utilisation ultérieure, mais ignore la réutilisation des artefacts précédemment stockés. Pour comprendre ce comportement, considérez le scénario suivant :

1. Un pipeline est créé.
1. Le pipeline est exécuté (exécution #1) et la validation HEAD en cours est `becdddb`. L’exécution est réussie et les artefacts obtenus sont stockés.
1. La variable `CM_DISABLE_BUILD_REUSE` est définie.
1. Le pipeline est exécuté à nouveau sans modifier le code. Bien que des artefacts stockés soient associés à `becdddb`, ils ne sont pas réutilisés en raison de la variable `CM_DISABLE_BUILD_REUSE`.
1. Le code est modifié et le pipeline est exécuté. La validation HEAD est maintenant `f6ac5e6`. L’exécution est réussie et les artefacts obtenus sont stockés.
1. La variable `CM_DISABLE_BUILD_REUSE` est supprimée.
1. Le pipeline est exécuté à nouveau sans modifier le code. Puisque des artefacts stockés sont associés à `f6ac5e6`, ces artefacts sont réutilisés.

### Avertissements {#caveats}

* Les artefacts de build ne sont pas réutilisés dans différents programmes, que le hachage de validation soit identique ou non.
* Les artefacts de build sont réutilisés dans le même programme même si la branche et/ou le pipeline sont différents.
* [Gestion des versions Maven](/help/implementing/cloud-manager/managing-code/project-version-handling.md) remplace la version du projet uniquement dans les pipelines de production.
Si la même validation est utilisée à la fois pour un déploiement de développement et un pipeline de production, et que le déploiement de développement s’exécute en premier, les versions sont déployées en évaluation et en production sans changer. Cependant, une balise est toujours créée dans ce cas.
* Si la récupération des artefacts stockés échoue, l’étape de build est exécutée comme si aucun artefact n’était stocké.
* Les variables de pipeline autres que `CM_DISABLE_BUILD_REUSE` ne sont pas prises en compte lorsque Cloud Manager décide de réutiliser des artefacts de version créés précédemment.
