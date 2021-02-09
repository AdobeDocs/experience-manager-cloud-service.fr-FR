---
title: Tests de l’interface utilisateur – Cloud Services
description: Tests de l’interface utilisateur – Cloud Services
translation-type: tm+mt
source-git-commit: ea0c9675ca03b1d247c7e5fd13e03072fb4a13ae
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 96%

---


# Tests de l’interface utilisateur {#ui-testing}

Les tests de l’interface utilisateur sont des tests basés sur Selenium placés dans une image Docker afin de permettre un large choix de langues et de cadres (tels que Java et Maven, Node et WebDriver.io, ou tout autre cadre et technologie basé sur Selenium). L’image Docker peut être créée avec des outils standard, mais elle doit respecter certaines conventions lors de son exécution. Lors de l’exécution de l’image Docker, un serveur Selenium est automatiquement mis en service. Les conventions d’exécution décrites ci-dessous permettent à votre code de test d’accéder à la fois au serveur Selenium et aux instances AEM testées.

>[!NOTE]
> Les gazoducs d’étape et de production créés avant le 10 février 2021 doivent être mis à jour afin d’utiliser les tests d’interface utilisateur décrits sur cette page.
> Voir [Configuration de votre pipeline CI-CD](/help/implementing/cloud-manager/configure-pipeline.md) pour plus d&#39;informations sur la configuration du pipeline.

## Création de tests de l’interface utilisateur {#building-ui-tests}

Les tests de l’interface utilisateur sont élaborés à partir d’un contexte de création Docker généré par un projet Maven. Cloud Manager utilise le contexte de création de Docker afin de générer une image Docker contenant les tests de l’interface utilisateur. En résumé, un projet Maven génère un contexte de création Docker décrivant comment créer une image Docker contenant les tests de l’interface utilisateur.

Cette section décrit les étapes nécessaires à l’ajout d’un projet de tests de l’interface utilisateur à votre référentiel. Si vous êtes pressé ou si vous n’avez pas de besoins spéciaux en matière de langage de programmation, l’[archétype de projet AEM](https://github.com/adobe/aem-project-archetype) peut générer pour vous un projet de tests de l’interface utilisateur.

### Génération d’un contexte de création Docker {#generate-docker-build-context}

Pour générer un contexte de création Docker, vous avez besoin d’un module Maven qui :

- Génère une archive contenant un `Dockerfile` et tout autre fichier nécessaire pour créer l’image Docker avec vos tests.
- Balise l’archive avec le classificateur `ui-test-docker-context`.

La méthode la plus simple pour y parvenir consiste à configurer le [plug-in Maven Assembly](http://maven.apache.org/plugins/maven-assembly-plugin/) pour créer l’archive de contexte de création Docker et lui affecter le classificateur approprié.

Vous pouvez créer des tests de l’interface utilisateur avec différentes technologies et structures, mais cette section suppose que votre projet est présenté de la même manière que le suivant.

```
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

Cette exécution indique au module d’extension Maven Assembly de créer une archive basée sur les instructions contenues dans `assembly-ui-test-docker-context.xml`, nommée « descripteur d’assemblage » dans le jargon du plug-in. Le descripteur d’assemblage répertorie tous les fichiers qui doivent faire partie de l’archive.

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

Le descripteur d’assemblage demande au module d’extension de créer une archive de type `.tar.gz` et lui affecte le classificateur `ui-test-docker-context`. En outre, il répertorie les fichiers qui doivent être inclus dans l’archive :

- Un `Dockerfile`, obligatoire pour la création de l’image Docker.
- Le script `wait-for-grid.sh` dont les objectifs sont décrits ci-dessous.
- Tests d’interface utilisateur, implémentés par un projet Node.js dans le dossier `test-module`.

Le descripteur d’assemblage exclut également certains fichiers qui pourraient être générés lors de l’exécution locale des tests de l’interface utilisateur. Cela garantit une archive plus petite et accélère la création.

L’archive contenant le contexte de création Docker est automatiquement récupérée par Cloud Manager, qui crée l’image Docker contenant vos tests pendant ses pipelines de déploiement. Cloud Manager exécute ensuite l’image Docker pour réaliser les tests de l’interface utilisateur sur votre application.

## Rédaction de tests de l’interface utilisateur {#writing-ui-tests}

Cette section décrit les conventions que l’image Docker contenant vos tests de l’interface utilisateur doit respecter. L’image Docker est créée à partir du contexte de création Docker décrit dans la section précédente.

### Variables d’environnement {#environment-variables}

Les variables d’environnement suivantes seront transmises à votre image Docker au moment de l’exécution.

| Variable | Exemples | Description |
|---|---|---|
| `SELENIUM_BASE_URL` | `http://my-ip:4444` | URL du serveur Selenium |
| `SELENIUM_BROWSER` | `chrome`, `firefox` | Implémentation du navigateur utilisée par le serveur Selenium |
| `AEM_AUTHOR_URL` | `http://my-ip:4502/context-path` | URL de l’instance de création AEM |
| `AEM_AUTHOR_USERNAME` | `admin` | Nom d’utilisateur pour la connexion à l’instance de création AEM |
| `AEM_AUTHOR_PASSWORD` | `admin` | Mot de passe de connexion à l’instance de création AEM |
| `AEM_PUBLISH_URL` | `http://my-ip:4503/context-path` | URL de l’instance de publication AEM |
| `AEM_PUBLISH_USERNAME` | `admin` | Nom d’utilisateur pour la connexion à l’instance de publication AEM |
| `AEM_PUBLISH_PASSWORD` | `admin` | Mot de passe de connexion à l’instance de publication AEM |
| `REPORTS_PATH` | `/usr/src/app/reports` | Chemin d’accès où le rapport XML des résultats du test doit être enregistré |
| `UPLOAD_URL` | `http://upload-host:9090/upload` | URL vers laquelle le fichier doit être chargé afin de le rendre accessible à Selenium |

### Attente de la préparation de Selenium {#waiting-for-selenium}

Avant le début des tests, l’image Docker doit garantir que le serveur Selenium est opérationnel. L’attente du service de Selenium est un processus en deux étapes :

1. Lecture de l’URL du service Selenium à partir de la variable d’environnement `SELENIUM_BASE_URL`.
2. Sondage à intervalle régulier vers le [point d’entrée d’état](https://github.com/SeleniumHQ/docker-selenium/#waiting-for-the-grid-to-be-ready) exposé par l’API Selenium.

Une fois que le point d’entrée d’état de Selenium donne une réponse positive, les tests peuvent débuter.

### Génération de rapports de test {#generate-test-reports}

L’image Docker doit générer des rapports de test au format XML JUnit et les enregistrer dans le chemin spécifié par la variable d’environnement `REPORTS_PATH`. Le format XML JUnit est un format très répandu pour le rapports de résultats de tests. Si l’image Docker utilise Java et Maven, le [plug-in Maven Surefire](https://maven.apache.org/surefire/maven-surefire-plugin/) et le [plug-in Maven Failsafe](https://maven.apache.org/surefire/maven-failsafe-plugin/) sont tous deux utilisés. Si l’image Docker est implémentée avec d’autres langages de programmation ou des exécuteurs de tests, consultez la documentation des outils choisis pour savoir comment générer des rapports XML JUnit.

### Chargement de fichiers (#upload-files)

Les tests doivent parfois charger des fichiers vers l’application testée. Afin que le déploiement de Selenium reste flexible par rapport à vos tests, il n’est pas possible de charger directement une ressource vers Selenium. Au lieu de cela, le chargement d’un fichier passe par quelques étapes intermédiaires :

1. Chargement du fichier à l’URL spécifiée par la variable d’environnement `UPLOAD_URL`. Le chargement doit être effectué dans une requête POST avec un formulaire en plusieurs parties. Le formulaire en plusieurs parties doit comporter un seul champ de fichier. Cela équivaut à `curl -X POST ${UPLOAD_URL} -F "data=@file.txt"`. Consultez la documentation et les bibliothèques du langage de programmation utilisé dans l’image Docker pour savoir comment exécuter une telle requête HTTP.
2. Si le chargement aboutit, la requête renvoie une réponse `200 OK` de type `text/plain`. Le contenu de la réponse est une gestion de fichier opaque. Vous pouvez utiliser cette gestion à la place d’un chemin de fichier dans un élément `<input>` pour tester les chargements de fichiers dans votre application.
