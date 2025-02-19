---
title: Environnement de création de Cloud Manager
description: Découvrez l’environnement de création de Cloud Manager et comment il génère et teste votre code.
exl-id: a4e19c59-ef2c-4683-a1be-3ec6c0d2f435
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f37795b99f7c79aa73615748a0a7df61f9afbdb7
workflow-type: tm+mt
source-wordcount: '1551'
ht-degree: 30%

---


# Environnement de création {#build-environment}

Découvrez l’environnement de création de Cloud Manager et comment il génère et teste votre code.

>[!TIP]
>
>Ce document couvre l’environnement de création Cloud Manager pour le développement de votre projet AEM as a Cloud Service. Pour plus d’informations sur les plateformes clientes prises en charge par AEM as a Cloud Service pour la création de contenu, consultez le document [Plateformes clientes prises en charge.](/help/overview/supported-platforms.md)

## Détails de l’environnement de création {#build-environment-details}

Cloud Manager crée et teste votre code à l’aide d’un environnement de génération spécialisé.

* L’environnement de création est basé sur Linux, dérivé de Ubuntu 22.04.
* Apache Maven 3.9.4 est installé.
   * Adobe recommande aux utilisateurs et utilisatrices de [mettre à jour leurs référentiels Maven de sorte à utiliser HTTPS au lieu de HTTP](#https-maven).
<!-- OLD Removed 1/16/25 * The Java versions installed are Oracle JDK 11.0.22 and Oracle JDK 8u401. -->
* Les versions de Java installées sont les suivantes : Oracle JDK 11.0.22, Oracle JDK 17.0.10 et Oracle JDK 21.0.4.

<!-- OLD Removed 1/16/25 * **IMPORTANT:** By default, the JAVA_HOME environment variable is set to `/usr/lib/jvm/jdk1.8.0_401`, which contains Oracle JDK 8u401. This default should be overridden for AEM Cloud Projects to use JDK 11. See the Setting the Maven JDK Version section for more details. -->
* **IMPORTANT :** par défaut, la variable d’environnement `JAVA_HOME` est définie sur `/usr/lib/jvm/jdk1.8.0_401`, qui contient le JDK Oracle 8u401. ***Cette valeur par défaut doit être remplacée pour que les projets cloud AEM utilisent le JDK 21 (recommandé), 17 ou 11***. Consultez la section [Définition de la version du JDK Maven](#alternate-maven-jdk-version) pour plus d’informations.
* D’autres packages système nécessaires sont installés.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* D’autres packages peuvent être installés au moment de la création, comme décrit dans la section [Installer des packages système supplémentaires](#installing-additional-system-packages).
* Chaque version s’exécute dans un environnement propre, le conteneur de version ne conservant aucun état entre les exécutions.
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

<!-- OLD below Removed 1/16/25

### Use a specific Java version

The Cloud Manager build process uses the Oracle 8 JDK to build projects by default, but AEM Cloud Service customers should set the Maven execution JDK version to 11. -->

<!-- OLD below Removed 1/16/25

#### Set the Maven JDK version

Adobe recommends that you set the JDK version for the entire Maven execution to `11` in a `.cloudmanager/java-version file`.

To do so, create a file named `.cloudmanager/java-version` in the git repository branch used by the pipeline. Edit the file so that it contains only the text, `11`. While Cloud Manager also accepts a value of `8`, this version is no longer supported for AEM Cloud Service projects. Any other value is ignored. When `11` is specified, Oracle 11 is used and the `JAVA_HOME` environment variable is set to `/usr/lib/jvm/jdk-11.0.22`. -->

### Utiliser une version Java spécifique {#using-java-support}

Le processus de création Cloud Manager utilise le JDK Oracle 8 pour créer des projets par défaut, mais les clients AEM Cloud Service doivent définir la version du JDK d’exécution Maven sur 21 (recommandé), 17 ou 11.

#### Définition de la version du JDK Maven {#alternate-maven-jdk-version}

Pour définir le JDK d’exécution Maven, créez un fichier nommé `.cloudmanager/java-version` dans la branche de référentiel Git utilisée par le pipeline. Modifiez le fichier afin qu’il contienne uniquement le texte, le `21` ou le `17`. Bien que Cloud Manager accepte également une valeur de `8`, cette version n’est plus prise en charge pour les projets AEM Cloud Service. Toute autre valeur est ignorée. Lorsque `21` ou `17` est spécifié, Oracle Java 21 ou Oracle Java 17 est utilisé.


#### Conditions préalables à la migration vers la création avec Java 21 ou Java 17 {#prereq-for-building}

Pour migrer vers la création avec Java 21 ou Java 17, vous devez d’abord effectuer une mise à niveau vers la dernière version de SonarQube. Pour plus d’informations, consultez les [notes de mise à jour de Cloud Manager 2025.1.0](/help/implementing/cloud-manager/release-notes/current.md#what-is-new).

Lors de la migration de votre application vers une nouvelle version de build Java et une nouvelle version d’exécution, testez minutieusement dans les environnements de développement et d’évaluation avant de procéder au déploiement en production.

Nous recommandons la stratégie de déploiement suivante :

1. Exécutez votre SDK locale avec Java 21, que vous pouvez télécharger à partir de https://experience.adobe.com/#/downloads, et déployez votre application sur celle-ci et validez ses fonctionnalités. Vérifiez dans les journaux qu&#39;il n&#39;y a pas d&#39;erreurs, ce qui indique des problèmes de chargement de classe ou de tissage de code octet.
1. Configurez une branche dans votre référentiel Cloud Manager pour utiliser Java 21 en tant que version Java au moment de la création, configurez un pipeline de développement pour utiliser cette branche et exécutez le pipeline. Exécutez vos tests de validation.
1. Si tout semble correct, configurez votre pipeline d’évaluation/de production pour utiliser Java 21 en tant que version Java au moment de la création et exécutez le pipeline.

##### À propos de certaines fonctionnalités de traduction {#translation-features}

Les fonctionnalités suivantes peuvent ne pas fonctionner correctement lorsqu’elles sont déployées sur l’exécution Java 21 et Adobe prévoit de les résoudre d’ici le début de l’année 2025 :

* Le format `XLIFF` (XML Localization Interchange File Format) échoue lors de l’utilisation de la traduction humaine.
* `I18n` (Internationalisation) ne gère pas correctement les paramètres régionaux hébreu (`he`), indonésien (`in`) et yiddish (`yi`) en raison de modifications apportées au constructeur de paramètres régionaux dans les versions Java les plus récentes.

#### Exigences d’exécution {#runtime-requirements}

Le runtime Java 21 est utilisé pour les versions avec Java 21 et Java 17, et il sera progressivement appliqué aux versions Java 11 également (voir la note ci-dessous). Un environnement doit se trouver dans une version d’AEM 17098 ou plus récente pour recevoir la mise à jour Java 21. Pour garantir la compatibilité, les ajustements suivants sont nécessaires.

Les mises à jour des bibliothèques peuvent être appliquées à tout moment, car elles restent compatibles avec les versions Java plus anciennes.

* **Version minimale d’ASM:**
Mettez à jour l’utilisation du package Java`org.objectweb.asm` souvent regroupé dans des artefacts `org.ow2.asm.*`, vers la version 9.5 ou ultérieure pour garantir la prise en charge des exécutions JVM plus récentes.

* **Version minimale de Groovy:**
Mettez à jour l’utilisation des packages Java `org.apache.groovy` ou `org.codehaus.groovy` vers la version 4.0.22 ou ultérieure pour garantir la prise en charge des exécutions JVM plus récentes.

  Ce lot peut être inclus indirectement en ajoutant des dépendances tierces telles que la console AEM Groovy.

* **Version minimale de Aries SPIFly:**
Mettez à jour l’utilisation du package Java `org.apache.aries.spifly.dynamic.bundle` vers la version 1.3.6 ou ultérieure pour garantir la prise en charge des exécutions JVM plus récentes.

Le SDK AEM Cloud Service est compatible avec Java 21 et peut être utilisé pour valider la compatibilité de votre projet avec Java 21 avant d’exécuter un pipeline Cloud Manager.

* **Modifier un paramètre d’exécution :**
Lors de l’exécution locale d’AEM avec Java 21, les scripts de démarrage (`crx-quickstart/bin/start` ou `crx-quickstart/bin/start.bat`) échouent en raison du paramètre `MaxPermSize` . Pour remédier à ce problème, supprimez `-XX:MaxPermSize=256M` du script ou définissez la variable d’environnement `CQ_JVM_OPTS`, en la définissant sur `-Xmx1024m -Djava.awt.headless=true`.

  Ce problème est résolu dans la version 19149 et ultérieure du SDK AEM Cloud Service.

>[!IMPORTANT]
>
>Lorsque `.cloudmanager/java-version` est défini sur `21` ou `17`, l’exécution Java 21 est déployée. L’exécution de Java 21 est planifiée pour un déploiement progressif vers tous les environnements (et pas seulement ceux dont le code est créé avec Java 11) à partir du mardi 4 février 2025. Le déploiement commencera par les sandbox et les environnements de développement, puis sera déployé dans tous les environnements de production en avril 2025. Les clients qui souhaitent adopter l’exécution Java 21 *auparavant* peuvent contacter Adobe à l’adresse [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com).


#### Exigences de temps de création {#build-time-reqs}

Les ajustements suivants sont nécessaires pour permettre la création du projet avec Java 21 et Java 17. Elles peuvent être mises à jour avant même l’exécution de Java 21 et Java 17, car elles sont compatibles avec les versions Java plus anciennes.

Il est recommandé aux clients AEM Cloud Service de créer leurs projets avec Java 21 dès que possible afin de tirer parti des nouvelles fonctionnalités de langue.

* **Version minimale de `bnd-maven-plugin`:**
Mettez à jour l’utilisation de `bnd-maven-plugin` vers la version 6.4.0 pour garantir la prise en charge des exécutions JVM plus récentes.

  Les versions 7 ou ultérieures ne sont pas compatibles avec Java 11 ou version antérieure, une mise à niveau vers cette version n’est donc pas recommandée.

* **Version minimale de `aemanalyser-maven-plugin`:**
Mettez à jour l’utilisation de `aemanalyser-maven-plugin` vers la version 1.6.6 ou ultérieure pour garantir la prise en charge des exécutions JVM plus récentes.

* **Version minimale de `maven-bundle-plugin`:**
Mettez à jour l’utilisation de `maven-bundle-plugin` vers la version 5.1.5 ou une version ultérieure pour garantir la prise en charge des exécutions JVM plus récentes.

  Les versions 6 ou ultérieures ne sont pas compatibles avec Java 11 ou version antérieure, une mise à niveau vers cette version n’est donc pas recommandée.

* **Mise à jour des dépendances dans `maven-scr-plugin`:**
Le `maven-scr-plugin` n’est pas directement compatible avec Java 21 ou Java 17. Cependant, les fichiers descripteurs peuvent être générés en mettant à jour la version des dépendances AEM dans la configuration du plug-in, comme illustré dans l’exemple suivant :

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

Par exemple, si la minimisation de JavaScript se produit au moment de la création à l’aide d’un outil tel que gulp, différents niveaux de minimisation peuvent être préférés pour divers environnements. Une version de développement peut utiliser un niveau de minimisation plus léger par rapport à l’évaluation et à la production.

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

Votre processus de génération peut nécessiter des variables de configuration spécifiques qui ne doivent pas être stockées dans le référentiel Git. En outre, vous devrez peut-être ajuster ces variables entre les exécutions de pipeline à l’aide de la même branche.

Voir aussi [Configurer des variables de pipeline](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md) pour plus d’informations.

## Installation de packages système supplémentaires {#installing-additional-system-packages}

Certaines versions nécessitent des packages système supplémentaires pour fonctionner entièrement. Par exemple, une version peut appeler un script Python ou Ruby et doit disposer d’un interprète de langue approprié installé. Ce processus d’installation peut être géré en appelant la [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) de votre `pom.xml` pour appeler APT. Cette exécution doit généralement être encapsulée dans un profil Maven spécifique à Cloud Manager. Cet exemple installe Python.

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
