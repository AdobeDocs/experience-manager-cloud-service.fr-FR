---
title: Tests de l'interface utilisateur - Cloud Services
description: Tests de l'interface utilisateur - Cloud Services
translation-type: tm+mt
source-git-commit: bf3fb5178bc2ae72e19ecc1de82b08fac5089ecf
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 0%

---


# Test de l&#39;interface utilisateur {#ui-testing}

>[!CAUTION]
>
>Cette fonction n’est pas encore disponible pour l’ensemble de la population.


Les tests d&#39;interface utilisateur sont des tests basés sur le sélénium conditionnés dans une image Docker afin de permettre un large choix de langue et de cadres (tels que Java et Maven, Node et WebDriver.io, ou toute autre structure et technologie construite sur le sélénium). L&#39;image Docker peut être créée avec un outillage standard, mais elle doit respecter certaines conventions lors de son exécution. Lors de l&#39;exécution de l&#39;image Docker, un serveur Selenium est automatiquement mis en service. Les conventions d&#39;exécution décrites ci-dessous permettent à votre code de test d&#39;accéder à la fois au serveur Selenium et aux instances AEM sous test.

## Création de tests d&#39;interface utilisateur {#building-ui-tests}

Les tests d&#39;interface utilisateur sont élaborés à partir d&#39;un contexte de création Docker généré par un projet Maven. Cloud Manager utilise le contexte de création Docker pour générer une image Docker qui contient les tests d’interface utilisateur réels. En résumé, un projet Maven génère un contexte de création Docker et le contexte de création Docker décrit comment créer une image Docker contenant les tests d&#39;interface utilisateur.

Cette section décrit les étapes nécessaires à l&#39;ajout d&#39;un projet de tests d&#39;interface utilisateur à votre référentiel. Si vous êtes pressé ou si vous n&#39;avez pas de besoins spéciaux pour le langage de programmation, l&#39;[archétype de projet ](https://github.com/adobe/aem-project-archetype) AEM peut générer un projet de tests d&#39;interface utilisateur pour vous.

### Générer un contexte de création Docker {#generate-docker-build-context}

Pour générer un contexte de création Docker, vous avez besoin d&#39;un module Maven qui :

- Génère une archive contenant `Dockerfile` et tout autre fichier nécessaire pour créer l&#39;image Docker avec vos tests.
- Balise l&#39;archive avec le classificateur `ui-test-docker-context`.

La méthode la plus simple pour y parvenir consiste à configurer le [module externe Maven Assembly](http://maven.apache.org/plugins/maven-assembly-plugin/) pour créer l&#39;archive contextuelle de build Docker et lui affecter le classificateur approprié.

Vous pouvez créer des tests d’interface utilisateur avec différentes technologies et structures, mais cette section suppose que votre projet est présenté de la même manière que le suivant.

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

Le fichier `pom.xml` prend en charge la version Maven. Ajoutez une exécution au module externe Maven Assembly semblable à celle qui suit.

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

Cette exécution indique au module externe Maven Assembly de créer une archive basée sur les instructions contenues dans `assembly-ui-test-docker-context.xml`, appelée &quot;descripteur d&#39;assembly&quot; dans le jargon du module externe. Le descripteur d&#39;assembly liste tous les fichiers qui doivent faire partie de l&#39;archive.

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

Le descripteur d&#39;assembly demande au module externe de créer une archive de type `.tar.gz` et lui affecte le classificateur `ui-test-docker-context`. En outre, il liste les fichiers qui doivent être inclus dans l&#39;archive :

- Un `Dockerfile`, obligatoire pour la création de l&#39;image Docker.
- Script `wait-for-grid.sh` dont les objectifs sont décrits ci-dessous.
- Tests d’interface utilisateur réels, implémentés par un projet Node.js dans le dossier `test-module`.

Le descripteur d&#39;assembly exclut également certains fichiers qui pourraient être générés lors de l&#39;exécution locale des tests d&#39;interface utilisateur. Ceci garantit une archive plus petite et des compilations plus rapides.

L&#39;archive contenant le contexte de création du Docker est automatiquement récupérée par Cloud Manager, qui crée l&#39;image du Docker contenant vos tests pendant ses pipelines de déploiement. Ultérieurement, Cloud Manager exécutera l’image Docker pour exécuter les tests d’interface utilisateur sur votre application.

## Ecriture de tests d&#39;interface utilisateur {#writing-ui-tests}

Cette section décrit les conventions que l&#39;image Docker contenant vos tests d&#39;interface utilisateur doit respecter. L&#39;image du Docker est créée à partir du contexte de création du Docker décrit dans la section précédente.

### Variables d’environnement {#environment-variables}

Les variables d&#39;environnement suivantes seront transmises à votre image Docker au moment de l&#39;exécution.

| Variable | Exemples | Description |
|---|---|---|
| `SELENIUM_BASE_URL` | `http://my-ip:4444` | URL du serveur Selenium |
| `SELENIUM_BROWSER` | `chrome`, `firefox` | Implémentation du navigateur utilisée par le serveur Selenium |
| `AEM_AUTHOR_URL` | `http://my-ip:4502/context-path` | URL de l’instance d’auteur AEM |
| `AEM_AUTHOR_USERNAME` | `admin` | Nom d’utilisateur pour la connexion à l’instance d’auteur AEM |
| `AEM_AUTHOR_PASSWORD` | `admin` | Mot de passe de connexion à l’instance d’auteur AEM |
| `AEM_PUBLISH_URL` | `http://my-ip:4503/context-path` | URL de l’instance de publication AEM |
| `AEM_PUBLISH_USERNAME` | `admin` | Nom d’utilisateur pour la connexion à l’instance de publication AEM |
| `AEM_PUBLISH_PASSWORD` | `admin` | Mot de passe de connexion à l’instance de publication AEM |
| `REPORTS_PATH` | `/usr/src/app/reports` | Chemin d&#39;accès où le rapport XML des résultats du test doit être enregistré |
| `UPLOAD_URL` | `http://upload-host:9090/upload` | L&#39;URL vers laquelle le fichier doit être téléchargé afin de le rendre accessible au sélénium |

### Attente de la préparation du sélénium {#waiting-for-selenium}

Avant le début des tests, il est de la responsabilité de l&#39;image Docker de s&#39;assurer que le serveur Selenium est opérationnel. L&#39;attente du service du Sélénium est un processus en deux étapes :

1. Lisez l&#39;URL du service Selenium à partir de la variable d&#39;environnement `SELENIUM_BASE_URL`.
2. Sondage à intervalle régulier jusqu&#39;au [point de terminaison d&#39;état](https://github.com/SeleniumHQ/docker-selenium/#waiting-for-the-grid-to-be-ready) exposé par l&#39;API de sélénium.

Une fois que le point de terminaison du statut du Sélénium répond avec une réponse positive, les tests peuvent enfin début.

### Générer les rapports de test {#generate-test-reports}

L&#39;image Docker doit générer des rapports de test au format XML JUnit et les enregistrer dans le chemin spécifié par la variable d&#39;environnement `REPORTS_PATH`. Le format XML JUnit est un format très répandu pour le rapports des résultats des tests. Si l&#39;image du Docker utilise Java et Maven, le [Maven Surefire Plugin](https://maven.apache.org/surefire/maven-surefire-plugin/) et le [Maven Failsafe Plugin](https://maven.apache.org/surefire/maven-failsafe-plugin/) sont tous deux utilisés. Si l&#39;image Docker est implémentée avec d&#39;autres langages de programmation ou des exécutants de test, consultez la documentation pour connaître les outils choisis pour savoir comment générer des rapports XML JUnit.

### Télécharger des fichiers (#upload-files)

Les tests doivent parfois télécharger des fichiers vers l’application sous test. Afin de maintenir le déploiement du sélénium par rapport à vos tests flexibles, il n&#39;est pas possible de télécharger directement un actif vers le sélénium. Au lieu de cela, le téléchargement d’un fichier passe par quelques étapes intermédiaires :

1. Téléchargez le fichier à l’URL spécifiée par la variable d’environnement `UPLOAD_URL`. Le transfert doit être effectué dans une demande de POST avec un formulaire en plusieurs parties. Le formulaire multipartie doit comporter un seul champ de fichier. Cela équivaut à `curl -X POST ${UPLOAD_URL} -F "data=@file.txt"`. Consultez la documentation et les bibliothèques du langage de programmation utilisé dans l&#39;image Docker pour savoir comment exécuter une telle requête HTTP.
2. Si le transfert aboutit, la requête renvoie une réponse `200 OK` de type `text/plain`. Le contenu de la réponse est un descripteur de fichier opaque. Vous pouvez utiliser cette poignée à la place d’un chemin de fichier dans un élément `<input>` pour tester les téléchargements de fichiers dans votre application.
