---
title: Configuration du projet
description: Découvrez comment les projets AEM sont créés avec Maven et les normes que vous devez respecter lors de la création de votre propre projet.
exl-id: 76af0171-8ed5-4fc7-b5d5-7da5a1a06fa8
source-git-commit: 430179bf13c1fff077c515eed0676430e9e7f341
workflow-type: tm+mt
source-wordcount: '1415'
ht-degree: 100%

---

# Configuration du projet {#project-setup}

Découvrez comment les projets AEM sont créés avec Maven et les normes que vous devez respecter lors de la création de votre propre projet.

## Détails de configuration du projet {#project-setup-details}

Pour pouvoir être créés et déployés dans Cloud Manager, les projets AEM doivent se conformer à ces directives :

* Les projets doivent être créés à l’aide d’[Apache Maven](https://maven.apache.org).
* Un fichier `pom.xml` doit se trouver à la racine du référentiel Git. Ce fichier `pom.xml` peut faire référence à autant de sous-modules (qui, à leur tour, peuvent comporter d’autres sous-modules, etc.) que nécessaire.
* Vous pouvez ajouter des références à d’autres référentiels d’artefact Maven dans vos fichiers `pom.xml`. 
   * L’accès aux [référentiels d’artefacts protégés par mot de passe](#password-protected-maven-repositories) est pris en charge s’il est configuré. Cependant, l’accès aux référentiels d’artefacts protégés par réseau n’est pas pris en charge.
* Les packages de contenu déployables sont découverts en analysant les fichiers `.zip` de package de contenu se trouvant dans un répertoire appelé `target`.
   * Un nombre illimité de sous-modules peut produire des packages de contenu.
* Les artefacts de Dispatcher déployables sont découverts en analysant les fichiers `.zip` (également contenus dans le répertoire appelé `target`) dont les répertoires sont appelés `conf` et `conf.d`.
* S’il existe plusieurs packages de contenu, l’ordre des déploiements des packages n’est pas garanti.
   * Si un ordre spécifique est nécessaire, il est possible d’utiliser les dépendances de package pour le définir.
* Les packages peuvent être [ignorés](#skipping-content-packages) au cours du déploiement.

## Activation des profils Maven dans Cloud Manager {#activating-maven-profiles-in-cloud-manager}

Dans certains cas, vous devrez peut-être légèrement modifier le processus de génération lors de l’exécution dans Cloud Manager, contrairement à celui qui s’exécute sur les postes de travail des développeurs. Dans ce cas, les [profils Maven](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) peuvent être utilisés pour définir la manière dont la génération doit être différente dans différents environnements, notamment Cloud Manager.

L’activation d’un profil Maven dans l’environnement de génération Cloud Manager doit se faire en recherchant la présence de la variable d’environnement `CM_BUILD` [.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) De la même manière, un profil destiné à être utilisé uniquement en dehors de l’environnement de création Cloud Manager doit être généré en vérifiant l’absence de cette variable.

Par exemple, si vous souhaitez générer un message de sortie simple uniquement lorsque la génération est exécutée dans Cloud Manager, procédez comme suit.

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

Si vous souhaitez générer un message de sortie simple uniquement lorsque la génération est exécutée en dehors de Cloud Manager, procédez comme suit.

```xml
        <profile>
            <id>notCMBuild</id>
            <activation>
                  <property>
                        <name>!env.CM_BUILD</name>
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

## Prise en charge d’un référentiel Maven protégé par mot de passe {#password-protected-maven-repositories}

>[!NOTE]
>
>Les artefacts d’un référentiel Maven protégé par mot de passe ne doivent être utilisés que très prudemment, car le code déployé par ce mécanisme ne passe actuellement pas par les [règles de qualité de code](/help/implementing/cloud-manager/custom-code-quality-rules.md) intégrées aux points de contrôle de qualité de Cloud Manager. Par conséquent, ce mécanisme ne devrait être utilisé que dans de rares cas et pour le code non lié à AEM. Il est conseillé de déployer les sources Java ainsi que l’ensemble du code source du projet avec le binaire.

Pour utiliser un référentiel Maven protégé par mot de passe dans Cloud Manager :

1. Indiquez le mot de passe (et éventuellement le nom d’utilisateur) comme [variable de pipeline secrète.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md)
1. Référencez ensuite ce secret dans un fichier nommé `.cloudmanager/maven/settings.xml` dans le référentiel git, qui suit le schéma du [fichier des paramètres Maven](https://maven.apache.org/settings.html).

Lorsque le processus de création de Cloud Manager démarre :

* Le `<servers>` dans ce fichier sera fusionné dans le fichier `settings.xml` par défaut fourni par Cloud Manager.
   * Les ID de serveur commençant par `adobe` et `cloud-manager` sont considérés comme réservés et ne doivent pas être utilisés par des serveurs personnalisés.
   * Les ID de serveur ne correspondant pas à l’un de ces préfixes ou à l’ID par défaut `central` ne seront jamais mis en miroir par Cloud Manager.
* Une fois ce fichier en place, l’ID de serveur est référencé à l’intérieur d’un élément `<repository>` et `<pluginRepository>` dans le fichier `pom.xml`.
* En règle générale, ces éléments `<repository>` et `<pluginRepository>` sont contenus dans un [profil spécifique à Cloud Manager](#activating-maven-profiles-in-cloud-manager), bien que cela ne soit pas strictement nécessaire.

Par exemple, supposons que le référentiel se trouve à l’adresse `https://repository.myco.com/maven2`, que le nom d’utilisateur que Cloud Manager doit utiliser soit `cloudmanager` et que le mot de passe soit `secretword`. Procédez comme suit.

1. Définissez le mot de passe comme secret sur le pipeline.

   ```text
   $ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword`
   ```

1. Établissez ensuite la référence à partir du fichier `.cloudmanager/maven/settings.xml`.

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

1. Enfin, référencez l’identifiant du serveur dans le fichier `pom.xml` :

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

### Déploiement de sources {#deploying-sources}

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

### Déploiement de sources de projet {#deploying-project-sources}

Il est recommandé de déployer la source du projet dans son intégralité avec le binaire dans un référentiel Maven, ce qui permet de reconstruire l’artefact exact.

Pour ce faire, configurez le plug-in maven-assembly dans votre projet.

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

## Omission des modules de contenu {#skipping-content-packages}

Dans Cloud Manager, chaque build peut produire un certain nombre de modules de contenu. Pour diverses raisons, il peut être préférable de produire un module de contenu, mais de ne pas le déployer, par exemple, lors de la création de modules de contenu utilisés uniquement à des fins de test ou qui seront recompilés lors d’une autre étape du processus de build, c’est-à-dire sous la forme d’un sous-module d’un autre module.

Pour tenir compte de ces scénarios, Cloud Manager recherche une propriété nommée `cloudManagerTarget` dans les propriétés des modules de contenu créés. Si cette propriété est définie sur `none`, le module sera ignoré et non déployé.

Le mécanisme permettant de définir cette propriété dépend de la manière dont le build produit le module de contenu. Par exemple, avec le `filevault-maven-plugin`, vous devez configurer le plug-in de la manière suivante. 

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

## Réutilisation de l’artefact de build {#build-artifact-reuse}

Dans de nombreux cas, le même code est déployé dans plusieurs environnements AEM. Dans la mesure du possible, Cloud Manager évite de reconstruire la base du code lorsqu’il détecte que la même validation Git est utilisée dans plusieurs exécutions de pipelines de piles pleines.

Lorsqu’une exécution est lancée, la validation HEAD en cours pour le pipeline de branche est extraite. Le hachage de validation est visible dans l’interface utilisateur et via l’API. Une fois l’étape de build terminée, les artefacts obtenus sont stockés en fonction de ce hachage de validation et peuvent être réutilisés dans les exécutions ultérieures du pipeline.

Les packages sont réutilisés sur plusieurs pipelines s’ils se trouvent dans le même programme. Lorsque vous recherchez des modules qui peuvent être réutilisés, AEM ignore les branches et réutilise les artefacts entre les branches.

En cas de réutilisation, les étapes de build et de qualité du code sont effectivement remplacées par les résultats de l’exécution initiale. Le fichier journal de l’étape de build répertorie les artefacts et les informations d’exécution qui ont été utilisés pour les créer à lʼorigine.

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

1. L’exécution du pipeline 1 commence par générer les modules normalement.
1. Ensuite, l’exécution du pipeline 2 réutilisera les modules créés par le pipeline 1.

#### Exemple 2 {#example-2}

Partez du principe que votre programme comporte deux branches :

* Branche `foo`
* Branche `bar`

Les deux branches ont le même identifiant de validation.

1. Un pipeline de développement crée et exécute `foo`.
1. Par la suite, un pipeline de production crée et exécute `bar`.

Dans ce cas, l’artefact de `foo` sera réutilisé pour le pipeline de production, car le même hachage de validation a été identifié.

### Désinscription {#opting-out}

Si vous le souhaitez, le comportement de réutilisation peut être désactivé pour des pipelines spécifiques en définissant la variable de pipeline `CM_DISABLE_BUILD_REUSE` sur `true`. Si cette variable est définie, le hachage de validation est toujours extrait et les artefacts obtenus sont stockés pour une utilisation ultérieure, mais les artefacts précédemment stockés ne seront pas réutilisés. Pour comprendre ce comportement, considérez le scénario suivant.

1. Un pipeline est créé.
1. Le pipeline est exécuté (exécution #1) et la validation HEAD en cours est `becdddb`. L’exécution est réussie et les artefacts obtenus sont stockés.
1. La variable `CM_DISABLE_BUILD_REUSE` est définie.
1. Le pipeline est exécuté à nouveau sans modifier le code. Bien que des artefacts stockés soient associés à `becdddb`, ils ne sont pas réutilisés en raison de la variable `CM_DISABLE_BUILD_REUSE`.
1. Le code est modifié et le pipeline est exécuté. La validation HEAD est maintenant `f6ac5e6`. L’exécution est réussie et les artefacts obtenus sont stockés.
1. La variable `CM_DISABLE_BUILD_REUSE` est supprimée.
1. Le pipeline est exécuté à nouveau sans modifier le code. Puisque des artefacts stockés sont associés à `f6ac5e6`, ces artefacts sont réutilisés.

### Restrictions {#caveats}

* Les artefacts de build ne sont pas réutilisés dans différents programmes même si le hachage de validation est identique.
* Les artefacts de build sont réutilisés dans le même programme même si la branche et/ou le pipeline sont différents.
* La [gestion des versions Maven](/help/implementing/cloud-manager/managing-code/project-version-handling.md) remplace la version du projet uniquement dans les pipelines de production. Par conséquent, si la même validation est utilisée à la fois sur une exécution de déploiement de développement et une exécution de pipeline de production, et que le pipeline de déploiement de développement est exécuté en premier, les versions sont déployées dans les environnements dʼévaluation et de production sans être modifiées. Cependant, une balise sera toujours créée dans cette situation.
* Si la récupération des artefacts stockés échoue, l’étape de build est exécutée comme si aucun artefact n’avait été stocké.
* Les variables de pipeline autres que `CM_DISABLE_BUILD_REUSE` ne sont pas prises en compte lorsque Cloud Manager décide de réutiliser des artefacts de build créés précédemment.
