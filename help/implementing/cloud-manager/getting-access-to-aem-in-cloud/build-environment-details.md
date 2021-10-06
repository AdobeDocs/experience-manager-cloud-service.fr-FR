---
title: Détails de l’environnement de génération
description: Détails de l’environnement de génération – Cloud Services
exl-id: a4e19c59-ef2c-4683-a1be-3ec6c0d2f435
source-git-commit: 9ae940fb0149a76277aba49a75abfb8b83305788
workflow-type: tm+mt
source-wordcount: '957'
ht-degree: 98%

---

# Présentation de l’environnement de génération {#understanding-build-environment}

## Détails de l’environnement de génération {#build-environment-details}

Cloud Manager crée et teste votre code à l’aide d’un environnement de génération spécialisé. Cet environnement comporte les attributs suivants :

* L’environnement de génération est basé sur Linux, dérivé de Ubuntu 18.04.
* Apache Maven 3.6.0 est installé.
* Les versions de Java installées sont les suivantes : Oracle JDK 8u202, Azul Zulu 8u292, Oracle JDK 11.0.2 et Azul Zulu 11.0.11.
* D’autres packages système nécessaires sont installés :

   * bzip2
   * unzip
   * libpng
   * imagemagick
   * graphicsmagick

* D’autres packages peuvent être installés au moment de la génération, comme décrit [ci-dessous](#installing-additional-system-packages).
* Chaque génération a lieu dans un environnement vierge ; le conteneur de génération ne conserve aucun état entre les exécutions.
* Maven est toujours exécuté avec les trois commandes suivantes :

   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent packageco-maven-plugin:prepare-agent package`
* Maven est configuré au niveau du système avec un fichier settings.xml qui inclut automatiquement le référentiel public Adobe **Artifact** à l’aide d’un profil appelé `adobe-public`. (Pour plus d’informations, consultez le [référentiel Maven public d’Adobe](https://repo1.maven.org/)).

>[!NOTE]
>Bien que Cloud Manager ne définisse pas de version spécifique du `jacoco-maven-plugin`, la version utilisée doit être au moins `0.7.5.201505241946`.

### Utilisation d’une version de Java spécifique {#using-java-support}

Par défaut, les projets sont créés par le processus de génération Cloud Manager à l’aide du JDK Oracle 8. Les clients qui souhaitent utiliser un autre JDK disposent de deux options : en utilisant Maven Toolchains et en sélectionnant une autre version du JDK pour l’ensemble du processus d’exécution Maven.

#### Maven Toolchains {#maven-toolchains}

Le [plug-in Maven Toolchains](https://maven.apache.org/plugins/maven-toolchains-plugin/) permet aux projets de sélectionner un JDK spécifique (dit *toolchain*) pour l’utiliser dans le contexte des plug-ins Maven compatibles avec les chaînes d’outils. Cette opération est effectuée dans le fichier `pom.xml` du projet en spécifiant un fournisseur et une valeur de version. Voici un exemple de section dans le fichier `pom.xml` :

```
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

Dans cette méthode, Maven s’exécute toujours en utilisant le JDK par défaut (Oracle 8). Par conséquent, la vérification ou l’application de la version Java par le biais de plug-ins tels que le plug-in Apache Maven Enforcer ne fonctionne pas et ces plug-ins ne doivent pas être utilisés.

Les combinaisons fournisseur/version actuellement disponibles sont les suivantes :

* oracle 1.8
* oracle 1.11
* oracle 11
* sun 1.8
* sun 1.11
* sun 11
* azul 1.8
* azul 1.11
* azul 8

#### Autre version du JDK d’exécution Maven {#alternate-maven-jdk-version}

Il est également possible de sélectionner Azul 8 ou Azul 11 en tant que JDK pour l’ensemble de l’exécution Maven. Contrairement aux options de toolchains, un autre JDK sera utilisé pour tous les plug-ins, sauf si la configuration de toolchains est également définie, auquel cas la configuration de toolchains est toujours appliquée pour les plug-ins Maven compatibles avec les toolchains. Par conséquent, la vérification et l’application de la version Java à l’aide du [plug-in Apache Maven Enforcer](https://maven.apache.org/enforcer/maven-enforcer-plugin/) fonctionneront.

Pour ce faire, créez un fichier nommé `.cloudmanager/java-version` dans la branche de référentiel Git utilisée par le pipeline. Ce fichier peut contenir « 11 » ou « 8 ». Toute autre valeur est ignorée. S’il contient « 11 », Azul 11 sera utilisé. S’il contient « 8 », Azul 8 sera utilisé.

>[!NOTE]
>Dans une prochaine version de Cloud Manager, estimée actuellement pour octobre 2021, le JDK par défaut sera modifié et la valeur par défaut sera Azul 11. Pour les projets non compatibles avec Java 11, vous devrez créer dès que possible un fichier contenant le chiffre « 8 » afin de vous assurer qu’ils ne sont pas impactés par ce changement.


## Variables d’environnement {#environment-variables}

### Variables d’environnement standard {#standard-environ-variables}

Dans certains cas, les clients jugent nécessaire de modifier le processus de génération en fonction des informations sur le programme ou le pipeline.

Par exemple, si la minification JavaScript au moment de la génération est effectuée par le biais d’un outil comme gulp, il peut être nécessaire d’utiliser un niveau de minification différent lors de la génération pour un environnement de développement et pour des environnements intermédiaire et de production.

Pour la prise en charge, Cloud Manager ajoute ces variables d’environnement standard au conteneur de build pour chaque exécution.

| **Nom de variable** | **Définition** |
|---|---|
| CM_BUILD | Toujours définie sur &quot;true&quot; |
| BRANCHE | Branche configurée pour l’exécution |
| CM_PIPELINE_ID | Identifiant numérique de pipeline |
| CM_PIPELINE_NAME | Nom du pipeline |
| CM_PROGRAM_ID | Identifiant numérique de programme |
| CM_PROGRAM_NAME | Nom du programme |
| ARTIFACTS_VERSION | Pour un pipeline intermédiaire ou de production, version synthétique générée par Cloud Manager |
| CM_AEM_PRODUCT_VERSION | Nom de la version |

### Variables de pipeline {#pipeline-variables}

Dans certains cas, le processus de génération d’un client peut dépendre de variables de configuration spécifiques qui ne seraient pas appropriées pour le référentiel Git ou qui doivent varier entre les exécutions de pipeline utilisant la même branche.

Cloud Manager permet de configurer ces variables par le biais de l’API Cloud Manager ou de l’interface de ligne de commande de Cloud Manager pour chaque pipeline. Les variables peuvent être stockées en texte brut ou chiffrées au repos. Dans les deux cas, les variables sont disponibles dans l’environnement de génération en tant que variable d’environnement qui peut ensuite être référencée à partir du fichier `pom.xml` ou d’autres scripts de génération.

Pour définir une variable à l’aide de l’interface de ligne de commande, exécutez une commande du type :

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test`

Les variables actives peuvent être répertoriées :

`$ aio cloudmanager:list-pipeline-variables PIPELINEID`

Les noms des variables ne peuvent contenir que des caractères alphanumériques et des caractères de soulignement (_). Par convention, les noms doivent être entièrement en majuscules. Chaque pipeline présente une limite de 200 variables, chaque nom doit comporter moins de 100 caractères et chaque valeur doit comporter moins de 2 048 caractères dans le cas des variables de type chaîne et 500 caractères dans le cas des variables de type secretString.

En cas d’utilisation dans un fichier `Maven pom.xml`, il est généralement utile de mapper ces variables aux propriétés Maven en suivant une syntaxe similaire à celle-ci :

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

Certaines versions nécessitent d’autres packages système pour fonctionner entièrement. Par exemple, une version peut appeler un script Python ou ruby et, par conséquent, doit se voir installer un interprète de langue approprié. Pour ce faire, appelez le plug-in [exec-maven-plugin](https://www.mojohaus.org/exec-maven-plugin/) pour invoquer APT. Cette exécution doit généralement être encapsulée dans un profil Maven spécifique à Cloud Manager. Par exemple, pour installer Python :

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

Cette même technique peut être utilisée pour installer des packages spécifiques à la langue, c’est-à-dire utilisée `gem` pour les packages RubyGems ou `pip` pour les packages Python.

>[!NOTE]
>Installer un package système de cette manière ne l’installe **pas** dans l’environnement d’exécution utilisé pour Adobe Experience Manager. Si vous avez besoin d’installer un package système dans l’environnement AEM, contactez votre représentant Adobe.
