---
title: Tests de l’interface utilisateur
description: Les tests d’interface utilisateur personnalisés sont une fonctionnalité facultative qui vous permet de créer et d’exécuter automatiquement des tests d’interface utilisateur pour vos applications personnalisées.
exl-id: 3009f8cc-da12-4e55-9bce-b564621966dd
source-git-commit: 05f9e9de0d5dbcc332466dc964e2d01569d16110
workflow-type: tm+mt
source-wordcount: '1338'
ht-degree: 46%

---


# Tests de l’interface utilisateur {#ui-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_uitesting"
>title="Tests de l’interface utilisateur"
>abstract="Les tests d’interface utilisateur personnalisés sont une fonctionnalité facultative qui vous permet de créer et d’exécuter automatiquement des tests d’interface utilisateur pour vos applications. Les tests de l’interface utilisateur sont des tests basés sur Selenium placés dans une image Docker afin de permettre un large choix de langues et de cadres (tels que Java et Maven, Node et WebDriver.io, ou tout autre cadre et technologie basé sur Selenium)."

Les tests d’interface utilisateur personnalisés sont une fonctionnalité facultative qui vous permet de créer et d’exécuter automatiquement des tests d’interface utilisateur pour vos applications.

## Présentation {#custom-ui-testing}

AEM fournit une suite intégrée de [Points de contrôle de qualité Cloud Manager](/help/implementing/cloud-manager/custom-code-quality-rules.md) pour garantir des mises à jour régulières des applications personnalisées. En particulier, les points de contrôle informatiques sont déjà créés et automatisés dans les tests personnalisés à l’aide des API AEM.

Les tests de l’interface utilisateur sont des tests basés sur Selenium placés dans une image Docker afin de permettre un large choix de langues et de cadres (tels que Java et Maven, Node et WebDriver.io, ou tout autre cadre et technologie basé sur Selenium). En outre, un projet de tests d’interface utilisateur peut facilement être généré en utilisant [l’archétype de projet AEM.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr)

Les tests de l’interface utilisateur sont exécutés dans le cadre d’un point de contrôle qualité spécifique pour chaque pipeline Cloud Manager avec une [dédié **Tests de l’interface utilisateur personnalisée** étape .](/help/implementing/cloud-manager/deploy-code.md) Tous les tests de l’interface utilisateur, y compris les régressions et les nouvelles fonctionnalités, permettent de détecter et de signaler des erreurs.

Contrairement aux tests fonctionnels personnalisés, qui sont des tests HTTP écrits en Java, les tests de l’interface utilisateur peuvent être une image Docker avec des tests écrits dans n’importe quelle langue, à condition qu’ils respectent les conventions définies dans la section . [Création de tests d’interface utilisateur.](#building-ui-tests)

>[!TIP]
>
>Adobe recommande de suivre la structure et le langage (JavaScript et WDIO) fournis dans la variable [AEM Archétype de projet.](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests)

### Accord préalable client {#customer-opt-in}

Pour que Cloud Manager puisse créer et exécuter vos tests d’interface utilisateur, vous devez souscrire à cette fonctionnalité en ajoutant un fichier à votre référentiel.

* Le nom du fichier doit être `testing.properties`.
* Le contenu du fichier doit être `ui-tests.version=1`.
* Le fichier doit se trouver sous le sous-module Maven pour les tests de l’interface utilisateur en regard de la variable `pom.xml` du sous-module tests de l’interface utilisateur.
* Le fichier doit se trouver à la racine de la création `tar.gz` fichier .

La génération et les exécutions des tests de l’interface utilisateur seront ignorées si ce fichier n’est pas présent.

Pour inclure un `testing.properties` dans l’artefact de création, ajoutez une `include` dans la variable `assembly-ui-test-docker-context.xml` fichier .

```xml
[...]
<includes>
    <include>Dockerfile</include>
    <include>wait-for-grid.sh</include>
    <include>testing.properties</include> <!- opt-in test module in Cloud Manager -->
</includes>
[...]
```

>[!NOTE]
>
>Si votre projet n’inclut pas cette ligne, vous devrez modifier le fichier pour activer le test de l’interface utilisateur.
>
>Le fichier peut contenir une ligne vous conseillant de ne pas le modifier. Cela est dû au fait qu’il a été introduit dans votre projet avant l’introduction du test de l’interface utilisateur d’opt-in et que les clients n’étaient pas prévus pour modifier le fichier. Cela peut être ignoré en toute sécurité.

## Créer des tests de l’interface utilisateur {#building-ui-tests}

Un projet Maven génère un contexte de création Docker. Ce contexte de création Docker décrit comment créer une image Docker contenant les tests de l’interface utilisateur, que les utilisateurs de Cloud Manager doivent générer pour une image Docker contenant les tests de l’interface utilisateur réels.

Cette section décrit les étapes nécessaires à l’ajout d’un projet de tests d’interface utilisateur à votre référentiel.

>[!TIP]
>
>Le [AEM Archétype de projet](https://github.com/adobe/aem-project-archetype) peut générer un projet de tests d’interface utilisateur pour lequel vous n’avez pas d’exigences spéciales pour le langage de programmation.

### Génération d’un contexte Docker Build {#generate-docker-build-context}

Pour générer un contexte de création Docker, vous avez besoin d’un module Maven qui :

* Génère une archive contenant un `Dockerfile` et tout autre fichier nécessaire pour créer l’image Docker avec vos tests.
* Balise l’archive avec le classificateur `ui-test-docker-context`.

Pour ce faire, la méthode la plus simple consiste à configurer la variable [Module externe d’assemblage Maven](http://maven.apache.org/plugins/maven-assembly-plugin/) pour créer l’archive contextuelle de génération Docker et lui attribuer le classificateur approprié.

Vous pouvez créer des tests de l’interface utilisateur avec différentes technologies et structures, mais cette section suppose que votre projet est présenté de la même manière que le suivant.

```text
├── Dockerfile
├── assembly-ui-test-docker-context.xml
├── pom.xml
├── test-module
│   ├── package.json
│   ├── index.js
│   └── wdio.conf.js
└── wait-for-grid.sh
```

Le fichier `pom.xml` prend en charge la création Maven. Ajoutez une exécution au module d’extension Maven Assembly semblable à celle qui suit.

```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-assembly-plugin</artifactId>
    <configuration>
        <descriptors>
            <descriptor>${project.basedir}/assembly-ui-test-docker-context.xml</descriptor>
        </descriptors>
        <tarLongFileMode>gnu</tarLongFileMode>
    </configuration>
    <executions>
        <execution>
            <id>make-assembly</id>
            <phase>package</phase>
            <goals>
                <goal>single</goal>
            </goals>
        </execution>
    </executions>
</plugin>
```

Cette exécution demande au module externe d’assemblage Maven de créer une archive basée sur les instructions contenues dans `assembly-ui-test-docker-context.xml`, appelé **descripteur d’assemblage** dans le jargon du module externe. Le descripteur d’assemblage répertorie tous les fichiers qui doivent faire partie de l’archive.

```xml
<assembly>
    <id>ui-test-docker-context</id>
    <includeBaseDirectory>false</includeBaseDirectory>
    <formats>
        <format>tar.gz</format>
    </formats>
    <fileSets>
        <fileSet>
            <directory>${basedir}</directory>
            <includes>
                <include>Dockerfile</include>
                <include>wait-for-grid.sh</include>
            </includes>
        </fileSet>
        <fileSet>
            <directory>${basedir}/test-module</directory>
            <excludes>
                <exclude>node/**</exclude>
                <exclude>node_modules/**</exclude>
                <exclude>reports/**</exclude>
            </excludes>
        </fileSet>
    </fileSets>
</assembly>
```

Le descripteur d’assemblage demande au module d’extension de créer une archive de type `.tar.gz` et lui affecte le classificateur `ui-test-docker-context`. De plus, il répertorie les fichiers qui doivent être inclus dans l’archive, notamment les suivants.

* Un `Dockerfile`, obligatoire pour la création de l’image Docker
* Le script `wait-for-grid.sh` dont les objectifs sont décrits ci-dessous
* Les tests de l’interface utilisateur réels, implémentés par un projet Node.js dans la variable `test-module` folder

Le descripteur d’assemblage exclut également certains fichiers qui pourraient être générés lors de l’exécution locale des tests de l’interface utilisateur. Cela garantit une archive plus petite et accélère la création.

L’archive contenant le contexte de création Docker est automatiquement récupérée par Cloud Manager, qui crée l’image Docker contenant vos tests pendant ses pipelines de déploiement. Cloud Manager exécute ensuite l’image Docker pour réaliser les tests de l’interface utilisateur sur votre application.

Le build doit produire zéro ou une archive. S’il ne produit aucune archive, l’étape de test est effectuée par défaut. Si le build produit plusieurs archives, celle qui est sélectionnée est non déterministe.

## Rédiger des tests de l’interface utilisateur {#writing-ui-tests}

Cette section décrit les conventions que l’image Docker contenant vos tests de l’interface utilisateur doit respecter. L’image Docker est créée à partir du contexte de création Docker décrit dans la section précédente.

### Variables d’environnement {#environment-variables}

Les variables d’environnement suivantes seront transmises à votre image Docker au moment de l’exécution.

| Variable | Exemples | Description |
|---|---|---|
| `SELENIUM_BASE_URL` | `http://my-ip:4444` | URL du serveur Selenium |
| `SELENIUM_BROWSER` | `chrome` | Implémentation du navigateur utilisée par le serveur Selenium |
| `AEM_AUTHOR_URL` | `http://my-ip:4502/context-path` | URL de l’instance de création AEM |
| `AEM_AUTHOR_USERNAME` | `admin` | Nom d’utilisateur pour la connexion à l’instance d’auteur AEM |
| `AEM_AUTHOR_PASSWORD` | `admin` | Mot de passe de connexion à l’instance de création AEM |
| `AEM_PUBLISH_URL` | `http://my-ip:4503/context-path` | URL de l’instance de publication AEM |
| `AEM_PUBLISH_USERNAME` | `admin` | Nom d’utilisateur pour la connexion à l’instance de publication AEM |
| `AEM_PUBLISH_PASSWORD` | `admin` | Mot de passe de connexion à l’instance de publication AEM |
| `REPORTS_PATH` | `/usr/src/app/reports` | Chemin d’accès où le rapport XML des résultats du test doit être enregistré |
| `UPLOAD_URL` | `http://upload-host:9090/upload` | URL vers laquelle le fichier doit être chargé afin de le rendre accessible à Selenium |

### En attendant que Selenium soit prêt {#waiting-for-selenium}

Avant le début des tests, l’image Docker doit garantir que le serveur Selenium est opérationnel. L&#39;attente du service Selenium est un processus en deux étapes.

1. Lecture de l’URL du service Selenium à partir de la variable d’environnement `SELENIUM_BASE_URL`.
1. Sondage à intervalle régulier vers le [point d’entrée de statut](https://github.com/SeleniumHQ/docker-selenium/#waiting-for-the-grid-to-be-ready) exposé par l’API Selenium.

Une fois que le point de terminaison d’état du Selenium a répondu par une réponse positive, les tests peuvent commencer.

### Génération de rapports de test {#generate-test-reports}

L’image Docker doit générer des rapports de test au format XML JUnit et les enregistrer dans le chemin spécifié par la variable d’environnement `REPORTS_PATH`. Le format XML JUnit est un format largement utilisé pour rapporter les résultats des tests. Si l’image Docker utilise Java et Maven, les modules de test standard tels que [Module externe Maven Surefire](https://maven.apache.org/surefire/maven-surefire-plugin/) et [Module externe Maven Failed-safe](https://maven.apache.org/surefire/maven-failsafe-plugin/) peut générer de tels rapports prêts à l’emploi.

Si l’image Docker est implémentée avec d’autres langages de programmation ou des exécuteurs de test, consultez la documentation des outils sélectionnés pour la génération de rapports XML JUnit.

### Chargement de fichiers {#upload-files}

Les tests doivent parfois charger des fichiers dans l’application en cours de test. Pour que le déploiement de Selenium reste flexible par rapport à vos tests, il n’est pas possible de télécharger directement une ressource vers Selenium. Au lieu de cela, le téléchargement d’un fichier nécessite les étapes suivantes.

1. Chargement du fichier à l’URL spécifiée par la variable d’environnement `UPLOAD_URL`. 
   * Le chargement doit être effectué dans une requête POST avec un formulaire en plusieurs parties.
   * Le formulaire en plusieurs parties doit comporter un seul champ de fichier.
   * Cela équivaut à `curl -X POST ${UPLOAD_URL} -F "data=@file.txt"`.
   * Consultez la documentation et les bibliothèques du langage de programmation utilisé dans l’image Docker pour savoir comment exécuter une telle requête HTTP.
1. Si le chargement aboutit, la requête renvoie une réponse `200 OK` de type `text/plain`.
   * Le contenu de la réponse est une gestion de fichier opaque.
   * Vous pouvez utiliser cette gestion à la place d’un chemin de fichier dans un élément `<input>` pour tester les chargements de fichiers dans votre application.
