---
title: Environnement de création de Cloud Manager
description: Découvrez l’environnement de création de Cloud Manager et comment il génère et teste votre code.
exl-id: a4e19c59-ef2c-4683-a1be-3ec6c0d2f435
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 3bc9ec12de604818f6be1c0717566a5f16c6a7b9
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 58%

---


# Créer l&#39;environnement {#build-environment}

Découvrez l’environnement de création de Cloud Manager et comment il génère et teste votre code.

## Création des détails de l’environnement {#build-environment-details}

Cloud Manager crée et teste votre code à l’aide d’un environnement de génération spécialisé.

* L’environnement de création est basé sur Linux, dérivé de Ubuntu 22.04.
* Apache Maven 3.9.4 est installé.
   * Adobe recommande aux utilisateurs et utilisatrices de [mettre à jour leurs référentiels Maven de sorte à utiliser HTTPS au lieu de HTTP](#https-maven).
* <!-- OLD --> Les versions Java installées sont Oracle JDK 11.0.22 et Oracle JDK 8u401.
<!-- NEW but needed to be removed 12/5/24 * The Java versions installed are Oracle JDK 11.0.22, Oracle JDK 17.0.10, and Oracle JDK 21.0.4. -->
<!-- OLD --> * **IMPORTANT :** Par défaut, la variable d’environnement JAVA_HOME est définie sur `/usr/lib/jvm/jdk1.8.0_401`, qui contient le JDK Oracle 8u401. Cette valeur par défaut doit être remplacée pour AEM Cloud Projects d’utiliser JDK 11. Pour plus d’informations, voir la section Définition de la version du JDK Maven .
<!-- NEW but needed to be removed 12/5/24 * **IMPORTANT:** By default, the `JAVA_HOME` environment variable is set to `/usr/lib/jvm/jdk1.8.0_401`, which contains Oracle JDK 8u401. ***This default should be overridden for AEM Cloud Projects to use JDK 21 (preferred), 17, or 11***. See the [Setting the Maven JDK Version](#alternate-maven-jdk-version) section for more details. -->
* D’autres packages système nécessaires sont installés.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* D’autres packages peuvent être installés au moment de la création, comme décrit dans la section [Installer des packages système supplémentaires](#installing-additional-system-packages).
* Chaque version s’exécute dans un environnement propre, le conteneur de génération ne conservant aucun état entre les exécutions.
* Maven est toujours exécuté avec les trois commandes suivantes.
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven est configuré au niveau du système avec un fichier `settings.xml` qui inclut automatiquement le référentiel public d’artefacts Adobe à l’aide d’un profil appelé `adobe-public`. (Pour plus d’informations, consultez le [référentiel Maven public d’Adobe](https://repo1.maven.org/)).

>[!NOTE]
>
>Bien que Cloud Manager ne définisse pas de version spécifique du `jacoco-maven-plugin`, la version utilisée doit être au moins `0.7.5.201505241946`.

## Référentiels Maven HTTPS {#https-maven}

Cloud Manager [version 2023.10.0](/help/implementing/cloud-manager/release-notes/2023/2023-10-0.md) a commencé une mise à jour continue de l’environnement de création (achevée avec la version 2023.12.0), qui incluait une mise à jour de Maven 3.8.8. L’amélioration de la sécurité visant à atténuer les vulnérabilités potentielles a constitué un changement significatif introduit dans Maven 3.8.1. Plus précisément, Maven désactive désormais par défaut tous les miroirs `http://*` non sécurisés, comme indiqué dans les [Notes de mise à jour de Maven](https://maven.apache.org/docs/3.8.1/release-notes.html#cve-2021-26291).

Suite à cette amélioration de la sécurité, certaines personnes peuvent rencontrer des problèmes lors de l’étape de création, en particulier lors du téléchargement d’artefacts à partir de référentiels Maven qui utilisent des connexions HTTP non sécurisées.

Pour garantir une expérience fluide avec la version mise à jour, Adobe recommande aux utilisateurs et utilisatrices de mettre à jour leurs référentiels Maven de sorte à utiliser HTTPS au lieu de HTTP. Cet ajustement s’aligne sur la transition croissante du secteur vers des protocoles de communication sécurisés et contribue à maintenir un processus de création sécurisé et fiable.

<!-- OLD below -->

### Utilisation d’une version Java spécifique

Le processus de génération Cloud Manager utilise le JDK Oracle 8 pour créer des projets par défaut, mais les clients AEM Cloud Service doivent définir le JDK d’exécution Maven sur 11.

<!-- OLD below -->

#### Définition de la version du JDK Maven

Adobe recommande de définir la version du JDK pour l’exécution Maven entière sur `11` dans un `.cloudmanager/java-version file`.

Pour ce faire, créez un fichier nommé `.cloudmanager/java-version` dans la branche de référentiel git utilisée par le pipeline. Modifiez le fichier afin qu&#39;il ne contienne que le texte, `11`. Bien que Cloud Manager accepte également une valeur `8`, cette version n’est plus prise en charge pour les projets AEM Cloud Service. Toute autre valeur est ignorée. Lorsque `11` est spécifié, l’Oracle 11 est utilisé et la variable d’environnement `JAVA_HOME` est définie sur `/usr/lib/jvm/jdk-11.0.22`.

<!-- NEW but needed to be removed 12/5/24 ### Use a specific Java version {#using-java-support}

The Cloud Manager build process uses the Oracle 8 JDK to build projects by default, but AEM Cloud Service customers should set the Maven execution JDK version to 21 (preferred), 17, or 11.

#### Set the Maven JDK version {#alternate-maven-jdk-version}

Adobe recommends setting the Maven execution JDK version to `21` or `17` in a `.cloudmanager/java-version` file.

To do so, create a file named `.cloudmanager/java-version` in the Git repository branch used by the pipeline. Edit the file so that it contains only the text, `21` or `17`. While Cloud Manager also accepts a value of `8`, this version is no longer supported for AEM Cloud Service projects. Any other value is ignored. When `21` or `17` is specified, Oracle Java 21 or Oracle Java 17 is used and the `JAVA_HOME` environment variable is set to `/usr/lib/jvm/jdk-21` or `/usr/lib/jvm/jdk-17`.

#### Prerequisites for migrating to building with Java 21 or Java 17 {#prereq-for-building}

>[!NOTE]
>
>*When migrating your application to a new Java build version and runtime version, thoroughly test in dev and stage environments before deploying to production.
>Of special note, the following features have not yet been formally validated with Java 21 runtime: [Forms](/help/forms/home.md), [Workflows](/help/sites-cloud/authoring/workflows/overview.md), [Inbox](/help/sites-cloud/authoring/inbox.md), and [Projects](/help/sites-cloud/authoring/projects/overview.md). If your application relies on these features, ensure comprehensive testing to verify functionality.*

##### About some translation features {#translation-features}

The following features might not function correctly when building with Java 21 or Java 17, and Adobe expects to resolve them by early 2025:

* `XLIFF` (XML Localization Interchange File Format) fails when using Human Translation.  
* `I18n` (Internationalization) does not properly handle language locales Hebrew (`he`), Indonesian (`in`), and Yiddish (`yi`) due to changes in the Locale constructor in newer Java versions.

#### Runtime requirements {#runtime-requirements}

The Java 21 runtime is used for builds on Java 21, Java 17, and Java 11 starting in February 2025. To ensure compatibility, the following adjustments are necessary. 

Library updates can be applied anytime, as they remain compatible with older Java versions.

* **Minimum version of `org.objectweb.asm`:**
Update the usage of `org.objectweb.asm` to version 9.5 or higher to ensure support for newer JVM runtimes.

* **Minimum version of `org.apache.groovy`:**
Update the usage of `org.apache.groovy` to version 4.0.22 or higher to ensure support for newer JVM runtimes.

  This bundle can be indirectly included by adding third party dependencies such as the AEM Groovy Console.

* **Edit a runtime parameter:**
When running AEM locally with Java 21, the start scripts (`crx-quickstart/bin/start` or `crx-quickstart/bin/start.bat`) fail due to the `MaxPermSize` parameter. As a remedy, either remove `-XX:MaxPermSize=256M` from the script or define the environment variable `CQ_JVM_OPTS`, setting it to `-Xmx1024m -Djava.awt.headless=true`.

  Adobe plans to resolve this issue in a future release.

>[!NOTE]
>
>When `.cloudmanager/java-version` is set to `21` or `17`, the Java 21 runtime is deployed. In February or March 2025, the Java 21 runtime is planned for deployment to all customers, even if Java 11 is used to build your code. 

#### Build time requirements

The following adjustments are required to allow building the project with Java 21 and Java 17. They can be updated at any time as they are compatible with older versions of Java.

* **Minimum version of `bnd-maven-plugin`:**
Update the usage of `bnd-maven-plugin` to version 6.4.0 to ensure support for newer JVM runtimes. 

  Versions 7 or higher are not compatible with Java 11 or lower so an upgrade to that version is not recommended.

* **Minimum version of `aemanalyser-maven-plugin`:**
Update the usage of `aemanalyser-maven-plugin` to version 1.6.6 or higher to ensure support for newer JVM runtimes.

* **Minimum version of `maven-bundle-plugin`:**
Update the usage of `maven-bundle-plugin` to version 5.1.5 or higher to ensure support for newer JVM runtimes. 

  Versions 6 or higher are not compatible with Java 11 or lower so an upgrade to that version is not recommended.

* **Update dependencies in `maven-scr-plugin`:**
The `maven-scr-plugin` is not directly compatible with Java 21 or Java 17. However, descriptor files can be generated by updating the ASM dependency version in the plugin configuration, as shown in the following example:

```XML
<project>
  ...
  <build>
    ...
    <plugins>
      ...
      <plugin>
        <groupId>org.apache.felix</groupId>
        <artifactId>maven-scr-plugin</artifactId>
        <version>1.26.4</version>
        <executions>
          <execution>
            <id>generate-scr-scrdescriptor</id>
            <goals>
              <goal>scr</goal>
            </goals>
          </execution>
        </executions>
        <dependencies>
          <dependency>
            <groupId>org.ow2.asm</groupId>
            <artifactId>asm-analysis</artifactId>
            <version>9.7.1</version>
            <scope>compile</scope>
          </dependency>
        </dependencies>
      </plugin>
      ...
    </plugins>
    ...
  </build>
  ...
</project>
```
-->


## Variables d’environnement - standard {#environment-variables}

Vous pouvez juger nécessaire de modifier le processus de génération en fonction des informations sur le programme ou le pipeline.

Par exemple, si la minification JavaScript se produit au moment de la création à l’aide d’un outil comme gulp, différents niveaux de minification peuvent être recommandés pour divers environnements. Une version de développement peut utiliser un niveau de minimisation plus léger par rapport à l’évaluation et à la production.

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

## Variables d’environnement - pipeline {#pipeline-variables}

Votre processus de création peut nécessiter des variables de configuration spécifiques qui ne doivent pas être stockées dans le référentiel Git. De plus, vous devrez peut-être ajuster ces variables entre les exécutions de pipeline à l’aide de la même branche.

Pour plus d’informations, voir également [Configuration des variables de pipeline](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md) .

## Installation de packages système supplémentaires {#installing-additional-system-packages}

Certaines versions nécessitent des packages système supplémentaires pour fonctionner pleinement. Par exemple, une version peut appeler un script Python ou Ruby et doit avoir un interpréteur de langue approprié installé. Ce processus d’installation peut être géré en appelant le [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) de votre `pom.xml` pour appeler APT. Cette exécution doit généralement être encapsulée dans un profil Maven spécifique à Cloud Manager. Cet exemple installe Python.

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
