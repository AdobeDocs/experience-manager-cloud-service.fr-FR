---
title: Détails de la configuration du projet
description: Détails de la configuration du projet - Cloud Services
translation-type: tm+mt
source-git-commit: 207d0742e8bf46065c7e20bec7d88b0776c246b2
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 98%

---


# Configuration du projet {#project-setup-details}

## Modification des détails de configuration du projet {#modifying-project-setup-details}

Pour créer et déployer dans Cloud Manager, les projets AEM existants doivent se conformer à certaines règles de base :

* Les projets doivent être créés à l’aide d’Apache Maven.
* Un fichier *pom.xml* doit se trouver à la racine du référentiel Git. Ce fichier *pom.xml* peut faire référence à autant de sous-modules (qui, à leur tour, peuvent comporter d’autres sous-modules, etc.) que nécessaire.

* Vous pouvez ajouter des références à d’autres référentiels d’artefact Maven dans vos fichiers *pom.xml*. L’accès aux [référentiels d’artefacts protégés par mot de passe](#password-protected-maven-repositories) est pris en charge s’il est configuré. Cependant, l’accès aux référentiels d’artefacts protégés par réseau n’est pas pris en charge.
* Les packages de contenu déployables sont découverts en analysant les fichiers *zip* de package de contenu se trouvant dans un répertoire appelé *target*. Un nombre illimité de sous-modules peut produire des packages de contenu.

* Les artefacts déployables de Dispatcher sont découverts en analysant les fichiers *zip* (contenus dans un répertoire appelé *target*) dont les répertoires sont appelés *conf* et *conf.d*.

* S’il existe plusieurs packages de contenu, l’ordre des déploiements des packages n’est pas garanti. Si un ordre spécifique est nécessaire, il est possible d’utiliser les dépendances de package pour le définir. Les packages peuvent être [ignorés](#skipping-content-packages) du déploiement.


## Activation des profils Maven dans Cloud Manager {#activating-maven-profiles-in-cloud-manager}

Dans certains cas, vous devrez peut-être légèrement modifier le processus de génération lors de l’exécution dans Cloud Manager, contrairement à celui qui s’exécute sur les postes de travail des développeurs. Dans ce cas, les [profils Maven](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) peuvent être utilisés pour définir la manière dont la génération doit être différente dans différents environnements, notamment Cloud Manager.

L’activation d’un profil Maven dans l’environnement de génération Cloud Manager doit se faire en recherchant la présence de la variable d’environnement appelée CM_BUILD, décrite plus haut. Par contre, un profil destiné à être utilisé uniquement en dehors de l’environnement de création Cloud Manager doit être généré en vérifiant l’absence de cette variable.

Par exemple, si vous souhaitez générer un message de sortie simple uniquement lorsque la génération est exécutée dans Cloud Manager, procédez comme suit :

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

Si vous souhaitez générer un message de sortie simple uniquement lorsque la génération est exécutée en dehors de Cloud Manager, procédez comme suit :

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
>Les artefacts d’un référentiel Maven protégé par mot de passe ne doivent être utilisés que très prudemment, car le code déployé par ce mécanisme ne passe actuellement pas par les points de contrôle de qualité de Cloud Manager. Par conséquent, ce mécanisme ne devrait être utilisé que dans de rares cas et pour le code non lié à AEM. Il est conseillé de déployer les sources Java ainsi que l’ensemble du code source du projet avec le binaire.

Pour utiliser un référentiel Maven protégé par mot de passe dans Cloud Manager, spécifiez le mot de passe (et éventuellement le nom d’utilisateur) en tant que [Variable pipeline](#pipeline-variables) secrète, puis référencez ce secret dans un fichier nommé `.cloudmanager/maven/settings.xml` dans le référentiel git. Ce fichier suit le schéma de [fichier de paramètres Maven](https://maven.apache.org/settings.html). Au démarrage du processus de création de Cloud Manager, l’élément `<servers>` de ce fichier est fusionné dans le fichier `settings.xml` par défaut fourni par Cloud Manager. Les ID de serveur commençant par `adobe` et `cloud-manager` sont considérés comme réservés et ne doivent pas être utilisés par des serveurs personnalisés. Les ID de serveur **ne correspondant pas** à l’un de ces préfixes ou à l’ID par défaut `central` ne seront jamais mis en miroir par Cloud Manager. Une fois ce fichier en place, l’ID de serveur est référencé à l’intérieur d’un élément `<repository>` et/ou `<pluginRepository>` dans le fichier `pom.xml`. En règle générale, ces éléments `<repository>` et/ou `<pluginRepository>` sont contenus dans un [profil spécifique à Cloud Manager](#activating-maven-profiles-in-cloud-manager), bien que cela ne soit pas strictement nécessaire.

Par exemple, supposons que le référentiel se trouve à l’adresse https://repository.myco.com/maven2, que le nom d’utilisateur que Cloud Manager doit utiliser soit `cloudmanager` et que le mot de passe soit `secretword`.

Tout d’abord, définissez le mot de passe comme secret sur le pipeline :

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword`

Faites ensuite référence à ceci à partir du fichier `.cloudmanager/maven/settings.xml` :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
    <servers>
        <server>
            <id>myco-repository</id>
            <username>cloudmanager</username>
            <password>${env.CUSTOM_MYCO_REPOSITORY_PASSWORD}</password>
        </server>
    </servers>
</settings>
```

Enfin référencez l’identifiant du serveur dans le fichier `pom.xml` :

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

Configurez le module maven-source-plugin dans votre projet :

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

Configurez le module maven-assembly-plugin dans votre projet :

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

## Omission des modules de contenu{#skipping-content-packages}

Dans Cloud Manager, chaque compilation peut produire un certain nombre de modules de contenu.
Pour diverses raisons, il peut être préférable de produire un module de contenu, mais de ne pas le déployer. Cela peut s’avérer utile, par exemple, lors de la création de modules de contenu utilisés uniquement à des fins de test ou qui seront recompilés lors d’une autre étape du processus de compilation, c’est-à-dire sous la forme d’un sous-module d’un autre module.

Pour tenir compte de ces scénarios, Cloud Manager recherche une propriété nommée ***cloudManagerTarget*** dans les propriétés des modules de contenu créés. Si cette propriété est définie sur « none (aucun) », le module sera ignoré et non déployé. Le mécanisme permettant de définir cette propriété dépend de la manière dont la compilation produit le module de contenu. Par exemple, avec filevault-maven-plugin, vous devez configurer le module externe comme suit :

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

Avec content-package-maven-plugin, il est similaire :

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
