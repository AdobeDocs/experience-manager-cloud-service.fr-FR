---
title: Environnement de création
description: Découvrez l’environnement de création de Cloud Manager et comment il génère et teste votre code.
exl-id: a4e19c59-ef2c-4683-a1be-3ec6c0d2f435
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 77%

---


# Environnement de création {#build-environment}

Découvrez l’environnement de création de Cloud Manager et comment il génère et teste votre code.

## Détails de l’environnement de génération {#build-environment-details}

Cloud Manager crée et teste votre code à l’aide d’un environnement de génération spécialisé.

* L’environnement de création est basé sur Linux, dérivé de Ubuntu 22.04.
* Apache Maven 3.9.4 est installé.
   * Adobe recommande aux utilisateurs et utilisatrices de [mettre à jour leurs référentiels Maven de sorte à utiliser HTTPS au lieu de HTTP](#https-maven).
* Les versions Java installées sont Oracle JDK 11.0.22 et Oracle JDK 8u401.
* **IMPORTANT** : par défaut, la variable d’environnement `JAVA_HOME` est définie sur `/usr/lib/jvm/jdk1.8.0_401` qui contient le JDK Oracle 8u401. *_Cette valeur par défaut doit être remplacée pour que AEM Cloud Projects utilise JDK 11_*. Pour plus d’informations, voir la section [Définition de la version du JDK Maven](#alternate-maven-jdk-version) .
* D’autres packages système nécessaires sont installés.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* D’autres packages peuvent être installés au moment de la création, comme décrit dans la section [Installer des packages système supplémentaires](#installing-additional-system-packages).
* Chaque génération a lieu dans un environnement vierge ; le conteneur de génération ne conserve aucun état entre les exécutions.
* Maven est toujours exécuté avec les trois commandes suivantes.
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven est configuré au niveau du système avec un fichier `settings.xml` qui inclut automatiquement le référentiel public d’artefacts Adobe à l’aide d’un profil appelé `adobe-public`. (Pour plus d’informations, consultez le [référentiel Maven public d’Adobe](https://repo1.maven.org/)).

>[!NOTE]
>
>Bien que Cloud Manager ne définisse pas de version spécifique du `jacoco-maven-plugin`, la version utilisée doit être au moins `0.7.5.201505241946`.

## Référentiels Maven HTTPS {#https-maven}

Cloud Manager [version 2023.10.0](/help/implementing/cloud-manager/release-notes/2023/2023-10-0.md) a commencé une mise à jour continue de l’environnement de création (achevée avec la version 2023.12.0), qui incluait une mise à jour de Maven 3.8.8. L’amélioration de la sécurité visant à atténuer les vulnérabilités potentielles a constitué un changement significatif introduit dans Maven 3.8.1. Plus précisément, Maven désactive désormais par défaut tous les miroirs `http://*` non sécurisés, comme indiqué dans les [Notes de mise à jour de Maven](http://maven.apache.org/docs/3.8.1/release-notes.html#cve-2021-26291).

Suite à cette amélioration de la sécurité, certaines personnes peuvent rencontrer des problèmes lors de l’étape de création, en particulier lors du téléchargement d’artefacts à partir de référentiels Maven qui utilisent des connexions HTTP non sécurisées.

Pour garantir une expérience fluide avec la version mise à jour, Adobe recommande aux utilisateurs et utilisatrices de mettre à jour leurs référentiels Maven de sorte à utiliser HTTPS au lieu de HTTP. Cet ajustement s’aligne sur la transition croissante du secteur vers des protocoles de communication sécurisés et contribue à maintenir un processus de création sécurisé et fiable.

### Utilisation d’une version de Java spécifique {#using-java-support}

Par défaut, les projets sont créés par le processus de génération Cloud Manager à l’aide du JDK Oracle 8, mais il est vivement conseillé aux clients AEM Cloud Service de définir la version du JDK utilisée pour exécuter Maven sur `11`.

#### Définition de la version du JDK Maven {#alternate-maven-jdk-version}

Il est recommandé de définir la version du JDK pour l’exécution Maven entière sur `11` dans un fichier `.cloudmanager/java-version`.

Pour ce faire, créez un fichier nommé `.cloudmanager/java-version` dans la branche de référentiel git utilisée par le pipeline. Modifiez le fichier afin qu&#39;il ne contienne que le texte, `11`. Bien que Cloud Manager accepte également une valeur `8`, cette version n’est plus prise en charge pour les projets AEM Cloud Service. Toute autre valeur est ignorée. Lorsque `11` est spécifié, l’Oracle 11 est utilisé et la variable d’environnement `JAVA_HOME` est définie sur `/usr/lib/jvm/jdk-11.0.22`.

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

Pour plus d’informations, voir le document [Configuration des variables de pipeline](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md)

## Installation de packages système supplémentaires {#installing-additional-system-packages}

Certaines versions nécessitent d’autres packages système pour fonctionner entièrement. Par exemple, une version peut appeler un script Python ou Ruby et doit avoir un interpréteur de langue approprié installé. Pour ce faire, appelez le plug-in [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) dans votre `pom.xml` pour invoquer APT. Cette exécution doit généralement être encapsulée dans un profil Maven spécifique à Cloud Manager. Cet exemple installe Python.

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
>Pour plus d’informations sur l’environnement de création front-end, consultez [Développement de sites avec le pipeline front-end](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md).
