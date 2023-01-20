---
title: Environnement de création
description: Découvrez l’environnement de création de Cloud Manager et comment il génère et teste votre code.
exl-id: a4e19c59-ef2c-4683-a1be-3ec6c0d2f435
source-git-commit: 3348662e3da4dad75b851d7af7251d456321a3ec
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 98%

---


# Environnement de création {#build-environment}

Découvrez l’environnement de création de Cloud Manager et comment il génère et teste votre code.

## Détails de l’environnement de génération {#build-environment-details}

Cloud Manager crée et teste votre code à l’aide d’un environnement de génération spécialisé.

* L’environnement de génération est basé sur Linux, dérivé de Ubuntu 18.04.
* Apache Maven 3.6.0 est installé.
* Les versions Java installées sont Oracle JDK 8u202 et Oracle JDK 11.0.2.
* Par défaut, la variable d’environnement `JAVA_HOME` est définie sur `/usr/lib/jvm/jdk1.8.0_202` qui contient le JDK Oracle 8u202. Consultez la section [Autre version du JDK d’exécution Maven](#alternate-maven-jdk-version) pour plus d’informations.
* D’autres packages système nécessaires sont installés.

   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`

* D’autres packages peuvent être installés au moment de la génération, comme décrit dans la section [Installation de packages système supplémentaires.](#installing-additional-system-packages)
* Chaque génération a lieu dans un environnement vierge ; le conteneur de génération ne conserve aucun état entre les exécutions.
* Maven est toujours exécuté avec les trois commandes suivantes.

* `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
* `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
* `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven est configuré au niveau du système avec un fichier `settings.xml` qui inclut automatiquement le référentiel public d’artefacts Adobe à l’aide d’un profil appelé `adobe-public`. (Pour plus d’informations, consultez le [référentiel Maven public d’Adobe](https://repo1.maven.org/)).

>[!NOTE]
>
>Bien que Cloud Manager ne définisse pas de version spécifique du `jacoco-maven-plugin`, la version utilisée doit être au moins `0.7.5.201505241946`.

### Utilisation d’une version de Java spécifique {#using-java-support}

Par défaut, les projets sont créés par le processus de génération Cloud Manager à l’aide du JDK Oracle 8. Les clients qui souhaitent utiliser un autre JDK disposent de deux options.

* [Utiliser Maven Toolchains.](#maven-toolchains)
* [Sélectionner une autre version du JDK pour l’ensemble du processus d’exécution de Maven.](#alternate-maven-jdk-version)

#### Maven Toolchains {#maven-toolchains}

Le [plug-in Maven Toolchains](https://maven.apache.org/plugins/maven-toolchains-plugin/) permet aux projets de sélectionner un JDK spécifique (dit toolchain) pour l’utiliser dans le contexte des plug-ins Maven compatibles avec les chaînes d’outils. Cette opération est effectuée dans le fichier `pom.xml` du projet en spécifiant un fournisseur et une valeur de version.

```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-toolchains-plugin</artifactId>
    <version>1.1</version>
    <executions>
        <execution>
            <goals>
                <goal>toolchain</goal>
            </goals>
        </execution>
    </executions>
    <configuration>
        <toolchains>
            <jdk>
                <version>11</version>
                <vendor>oracle</vendor>
            </jdk>
        </toolchains>
    </configuration>
</plugin>
```

Elle entraîne l’utilisation du JDK Oracle, version 11 dans tous les plug-ins Maven compatibles avec les chaînes d’outils.

Lors de l’utilisation de cette méthode, Maven s’exécute toujours en utilisant le JDK par défaut (Oracle 8) et la variable d’environnement `JAVA_HOME` n’est pas modifiée. Par conséquent, la vérification ou l’application de la version Java par le biais de plug-ins tels que le plug-in Apache Maven Enforcer ne fonctionne pas et ces plug-ins ne doivent pas être utilisés.

Les combinaisons fournisseur/version actuellement disponibles sont les suivantes :

| Fournisseur | Version |
|---|---|
| `oracle` | `8` |
| `oracle` | `11` |
| `sun` | `8` |
| `sun` | `11` |

Ce tableau fait référence aux numéros de version des produits. Les numéros de version Java ou les chemins d’installation peuvent refléter les anciennes conventions de version Java, comme 1.8 pour Java 8.

>[!NOTE]
>
>À compter d’avril 2022, le JDK Oracle sera le JDK par défaut pour le développement et le fonctionnement des applications AEM. Le processus de génération de Cloud Manager passe automatiquement à l’utilisation du JDK Oracle, même si une autre option est explicitement sélectionnée dans le toolchain Maven. Pour plus d’informations, reportez-vous aux notes de mise à jour d’avril une fois publiées.

#### Autre version du JDK d’exécution Maven {#alternate-maven-jdk-version}

Il est également possible de sélectionner Java 8 ou Java 11 en tant que JDK pour l’ensemble de l’exécution Maven. Contrairement aux options de toolchains, un autre JDK sera utilisé pour tous les plug-ins, sauf si la configuration de toolchains est également définie, auquel cas la configuration de toolchains est toujours appliquée pour les plug-ins Maven compatibles avec les toolchains. Par conséquent, la vérification et l’application de la version Java à l’aide du [plug-in Apache Maven Enforcer](https://maven.apache.org/enforcer/maven-enforcer-plugin/) fonctionneront.

Pour ce faire, créez un fichier nommé `.cloudmanager/java-version` dans la branche de référentiel git utilisée par le pipeline. Ce fichier peut contenir « 11 » ou « 8 ». Toute autre valeur est ignorée. Si 11 est spécifié, Oracle 11 est utilisé et la variable d’environnement `JAVA_HOME` est définie sur `/usr/lib/jvm/jdk-11.0.2`. Si 8 est spécifié, Oracle 8 est utilisé et la variable d’environnement `JAVA_HOME` est définie sur `/usr/lib/jvm/jdk1.8.0_202`.

## Variables d’environnement {#environment-variables}

### Variables d’environnement standard {#standard-environ-variables}

Vous pouvez juger nécessaire de modifier le processus de génération en fonction des informations sur le programme ou le pipeline.

Par exemple, si la minification JavaScript au moment de la génération est effectuée via un outil comme gulp, il peut être nécessaire d’utiliser un autre niveau de minification lors de la génération pour un environnement de développement et pour des environnements d’évaluation et de production.

Pour la prise en charge, Cloud Manager ajoute ces variables d’environnement standard au conteneur de build pour chaque exécution.

| Nom de variable | Définition |
|---|---|
| `CM_BUILD` | Toujours définie sur `true` |
| `BRANCH` | Branche configurée pour l’exécution |
| `CM_PIPELINE_ID` | Identifiant numérique de pipeline |
| `CM_PIPELINE_NAME` | Nom du pipeline |
| `CM_PROGRAM_ID` | Identifiant numérique de programme |
| `CM_PROGRAM_NAME` | Nom du programme |
| `ARTIFACTS_VERSION` | Pour un pipeline intermédiaire ou de production, version synthétique générée par Cloud Manager |
| `CM_AEM_PRODUCT_VERSION` | Version de la mise à jour |

### Variables de pipeline {#pipeline-variables}

Votre processus de génération peut dépendre de variables de configuration spécifiques qui ne seraient pas appropriées pour le référentiel Git ou vous devrez peut-être les faire varier entre les exécutions de pipeline utilisant la même branche.

Cloud Manager permet de configurer ces variables par le biais de l’API Cloud Manager ou de l’interface de ligne de commande de Cloud Manager pour chaque pipeline. Les variables peuvent être stockées en texte brut ou chiffrées au repos. Dans les deux cas, les variables sont disponibles dans l’environnement de génération en tant que variable d’environnement qui peut ensuite être référencée à partir du fichier `pom.xml` ou d’autres scripts de génération.

Cette commande d’interface de ligne de commande définit une variable.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

Cette commande répertorie les variables.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

Les noms de variables doivent respecter les conventions suivantes.

* Les variables ne peuvent contenir que des caractères alphanumériques et un trait de soulignement (`_`).
* Les noms doivent être en majuscules.
* Il existe une limite de 200 variables par pipeline.
* Chaque nom doit comporter moins de 100 caractères.
* La valeur `string` de chaque variable doit comporter moins de 2 048 caractères.
* La valeur `secretString` de chaque variable type doit comporter moins de 500 caractères.

En cas d’utilisation dans un fichier `pom.xml` Maven, il est généralement utile de mapper ces variables aux propriétés Maven en utilisant une syntaxe similaire à celle-ci.

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
            </activation>
            <properties>
                <my.custom.property>${env.MY_CUSTOM_VARIABLE}</my.custom.property> 
            </properties>
        </profile>
```

## Installation de packages système supplémentaires {#installing-additional-system-packages}

Certaines versions nécessitent d’autres packages système pour fonctionner entièrement. Par exemple, une génération peut appeler un script Python ou Ruby et doit se voir installer un interprète de langue approprié. Pour ce faire, appelez le plug-in [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) dans votre `pom.xml` pour invoquer APT. Cette exécution doit généralement être encapsulée dans un profil Maven spécifique à Cloud Manager. Cet exemple installe Python.

```xml
        <profile>
            <id>install-python</id>
            <activation>
                <property>
                        <name>env.CM_BUILD</name>
                </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <groupId>org.codehaus.mojo</groupId>
                        <artifactId>exec-maven-plugin</artifactId>
                        <version>1.6.0</version>
                        <executions>
                            <execution>
                                <id>apt-get-update</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>update</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                            <execution>
                                <id>install-python</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>install</argument>
                                        <argument>-y</argument>
                                        <argument>--no-install-recommends</argument>
                                        <argument>python</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

Cette même technique peut être utilisée pour installer des packages spécifiques à la langue, par exemple utiliser `gem` pour les packages RubyGems ou `pip` pour les packages Python.

>[!NOTE]
>
>Installer un package système de cette manière ne l’installe pas dans l’environnement d’exécution utilisé pour Adobe Experience Manager. Si vous avez besoin d’installer un package système dans l’environnement AEM, contactez votre représentant Adobe.

>[!TIP]
>
>Pour plus d’informations sur l’environnement de génération front-end, consultez le document . [Développement de sites avec le pipeline front-end.](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md)
