---
title: Environnement de création de Cloud Manager
description: Découvrez l’environnement de création de Cloud Manager et comment il génère et teste votre code.
exl-id: a4e19c59-ef2c-4683-a1be-3ec6c0d2f435
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 7b9b9f3b957b27812c4a7e8f2dbcf96d8786b73e
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Créer l&#39;environnement {#build-environment}

Découvrez l’environnement de création de Cloud Manager et comment il génère et teste votre code.

## Création des détails de l’environnement {#build-environment-details}

Cloud Manager crée et teste votre code à l’aide d’un environnement de génération spécialisé.

* L’environnement de création est basé sur Linux, dérivé de Ubuntu 22.04.
* Apache Maven 3.9.4 est installé.
   * Adobe recommande aux utilisateurs et utilisatrices de [mettre à jour leurs référentiels Maven de sorte à utiliser HTTPS au lieu de HTTP](#https-maven).
* Les versions Java installées sont les suivantes : JDK Oracle 11.0.22, JDK Oracle 17.0.10 et JDK Oracle 21.0.4.
* **IMPORTANT :** Par défaut, la variable d’environnement `JAVA_HOME` est définie sur `/usr/lib/jvm/jdk1.8.0_401`, qui contient le JDK Oracle 8u401. ***Cette valeur par défaut doit être remplacée pour que AEM Cloud Projects utilise JDK 21 (recommandé), 17 ou 11***. Pour plus d’informations, voir la section [Définition de la version du JDK Maven](#alternate-maven-jdk-version) .
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

### Utilisation d’une version Java spécifique {#using-java-support}

Le processus de génération Cloud Manager utilise le JDK Oracle 8 pour créer des projets par défaut, mais les clients AEM Cloud Service doivent définir le JDK d’exécution Maven sur 21 (recommandé), 17 ou 11.

#### Définition de la version du JDK Maven {#alternate-maven-jdk-version}

Adobe recommande de définir la version du JDK d’exécution Maven sur `21` ou `17` dans un fichier `.cloudmanager/java-version`.

Pour ce faire, créez un fichier nommé `.cloudmanager/java-version` dans la branche de référentiel Git utilisée par le pipeline. Modifiez le fichier afin qu&#39;il ne contienne que le texte, `21` ou `17`. Bien que Cloud Manager accepte également une valeur `8`, cette version n’est plus prise en charge pour les projets AEM Cloud Service. Toute autre valeur est ignorée. Lorsque `21` ou `17` est spécifié, Oracle Java 21 ou Oracle Java 17 est utilisé et la variable d&#39;environnement `JAVA_HOME` est définie sur `/usr/lib/jvm/jdk-21` ou `/usr/lib/jvm/jdk-17`.

#### Conditions préalables pour la migration vers la création avec Java 21 ou Java 17 {#prereq-for-building}

>[!NOTE]
>
>*Lors de la migration de votre application vers une nouvelle version de build et une nouvelle version d’exécution Java, testez minutieusement les environnements de développement et d’évaluation avant de procéder au déploiement en production.
>Notez que les fonctionnalités suivantes n’ont pas encore été validées officiellement avec l’exécution Java 21 : [Forms](/help/forms/home.md), [Workflows](/help/sites-cloud/authoring/workflows/overview.md), [Boîte de réception](/help/sites-cloud/authoring/inbox.md) et [Projets](/help/sites-cloud/authoring/projects/overview.md). Si votre application repose sur ces fonctionnalités, effectuez des tests complets pour en vérifier les fonctionnalités.*

##### A propos de certaines fonctionnalités de traduction {#translation-features}

Les fonctionnalités suivantes peuvent ne pas fonctionner correctement lors de la création avec Java 21 ou Java 17 et Adobe prévoit de les résoudre d’ici au début de 2025 :

* `XLIFF` (XML Localization Interchange File Format) échoue lors de l’utilisation de la traduction humaine.
* `I18n` (Internationalisation) ne prend pas correctement en charge les paramètres régionaux de langue hébreu (`he`), indonésien (`in`) et yiddish (`yi`) en raison de modifications apportées au constructeur Locale dans des versions Java plus récentes.

#### Exigences d’exécution {#runtime-requirements}

L’exécution Java 21 est utilisée pour les versions sur Java 21, Java 17 et Java 11 à compter de février 2025. Pour garantir la compatibilité, les réglages suivants sont nécessaires.

Les mises à jour de bibliothèque peuvent être appliquées à tout moment, car elles restent compatibles avec les anciennes versions de Java.

* **Version minimale de `org.objectweb.asm` :**
Mettez à jour l’utilisation de `org.objectweb.asm` vers la version 9.5 ou ultérieure pour garantir la prise en charge des nouveaux environnements d’exécution JVM.

* **Version minimale de `org.apache.groovy` :**
Mettez à jour `org.apache.groovy` vers la version 4.0.22 ou ultérieure pour assurer la prise en charge des nouveaux environnements d’exécution JVM.

  Ce lot peut être inclus indirectement en ajoutant des dépendances tierces telles que la console AEM Groovy.

* **Modifier un paramètre d’exécution :**
Lors de l’exécution locale d’AEM avec Java 21, les scripts de démarrage (`crx-quickstart/bin/start` ou `crx-quickstart/bin/start.bat`) échouent en raison du paramètre `MaxPermSize` . Pour remédier à ce problème, supprimez `-XX:MaxPermSize=256M` du script ou définissez la variable d’environnement `CQ_JVM_OPTS`, en la définissant sur `-Xmx1024m -Djava.awt.headless=true`.

  Adobe prévoit de résoudre ce problème dans une version ultérieure.

>[!NOTE]
>
>Lorsque `.cloudmanager/java-version` est défini sur `21` ou `17`, le runtime Java 21 est déployé. En février ou mars 2025, l’exécution Java 21 est prévue pour le déploiement sur tous les clients, même si Java 11 est utilisé pour créer votre code.

#### Configuration requise

Les ajustements suivants sont nécessaires pour permettre la création du projet avec Java 21 et Java 17. Ils peuvent être mis à jour à tout moment, car ils sont compatibles avec les anciennes versions de Java.

* **Version minimale de `bnd-maven-plugin` :**
Mettez à jour l’utilisation de `bnd-maven-plugin` vers la version 6.4.0 pour garantir la prise en charge des nouveaux environnements d’exécution JVM.

  Les versions 7 ou ultérieures ne sont pas compatibles avec Java 11 ou version inférieure. Il n’est donc pas recommandé d’effectuer une mise à niveau vers cette version.

* **Version minimale de `aemanalyser-maven-plugin` :**
Mettez à jour l’utilisation de `aemanalyser-maven-plugin` vers la version 1.6.6 ou ultérieure pour garantir la prise en charge des nouveaux environnements d’exécution JVM.

* **Version minimale de `maven-bundle-plugin` :**
Mettez à jour `maven-bundle-plugin` vers la version 5.1.5 ou ultérieure pour garantir la prise en charge des nouveaux environnements d’exécution JVM.

  Les versions 6 ou ultérieures ne sont pas compatibles avec Java 11 ou version inférieure. Il n’est donc pas recommandé d’effectuer une mise à niveau vers cette version.

* **Mettre à jour les dépendances dans `maven-scr-plugin` :**
`maven-scr-plugin` n’est pas directement compatible avec Java 21 ou Java 17. Cependant, les fichiers descripteurs peuvent être générés en mettant à jour la version de dépendance ASM dans la configuration du module externe, comme illustré dans l’exemple suivant :

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
