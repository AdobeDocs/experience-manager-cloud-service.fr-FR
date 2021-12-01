---
title: Tests de l’interface utilisateur – Cloud Services
description: Tests de l’interface utilisateur – Cloud Services
exl-id: 3009f8cc-da12-4e55-9bce-b564621966dd
source-git-commit: 778fa187df675eada645c73911e6f02e8a112753
workflow-type: tm+mt
source-wordcount: '1582'
ht-degree: 95%

---

# Tests de l’interface utilisateur {#ui-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_uitesting"
>title="Tests de l’interface utilisateur"
>abstract="Les tests de l’interface utilisateur sont des tests basés sur Selenium placés dans une image Docker afin de permettre un large choix de langues et de cadres (tels que Java et Maven, Node et WebDriver.io, ou tout autre cadre et technologie basé sur Selenium). L’image Docker peut être créée avec des outils standard, mais elle doit respecter certaines conventions lors de son exécution. Lors de l’exécution de l’image Docker, un serveur Selenium est automatiquement mis en service. Les conventions d’exécution décrites ci-dessous permettent à votre code de test d’accéder à la fois au serveur Selenium et aux instances AEM testées."

Les tests de l’interface utilisateur sont des tests basés sur Selenium placés dans une image Docker afin de permettre un large choix de langues et de cadres (tels que Java et Maven, Node et WebDriver.io, ou tout autre cadre et technologie basé sur Selenium). L’image Docker peut être créée avec des outils standard, mais elle doit respecter certaines conventions lors de son exécution. Lors de l’exécution de l’image Docker, un serveur Selenium est automatiquement mis en service. Les conventions d’exécution décrites ci-dessous permettent à votre code de test d’accéder à la fois au serveur Selenium et aux instances AEM testées.

>[!NOTE]
> Les pipelines d’évaluation et de production créés avant le 10 février 2021 doivent être mis à jour pour pouvoir utiliser les tests d’interface utilisateur décrits sur cette page.
> Voir [Pipelines CI-CD dans Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) pour plus d’informations sur la configuration du pipeline.

## Test d’interface utilisateur personnalisé {#custom-ui-testing}

AEM fournit à ses clients une suite intégrée de murs qualité Cloud Manager qui leur permettent d’assurer la mise à jour régulière de leurs applications. Les passerelles de test informatique permettent en particulier déjà aux clients de créer et d’automatiser leurs propres tests qui utilisent des API AEM.

La fonction de test de l’interface utilisateur personnalisée est une [fonctionnalité facultative](#customer-opt-in) qui permet à nos clients de créer et d’exécuter automatiquement des tests d’interface utilisateur pour leurs applications. Les tests de l’interface utilisateur sont des tests basés sur Selenium placés dans une image Docker afin de permettre un large choix de langues et de cadres (tels que Java et Maven, Node et WebDriver.io, ou tout autre cadre et technologie basé sur Selenium). Cette section vous permet d’en savoir plus sur la création de l’interface utilisateur et la création de tests d’interface utilisateur. En outre, un projet de tests d’interface utilisateur peut être facilement généré à l’aide de l’archétype de projet AEM.

Les clients peuvent créer (via GIT) des tests personnalisés et des suites de tests pour l’interface utilisateur. Le test de l’interface utilisateur sera exécuté dans le cadre d’un mur qualité spécifique à chaque pipeline Cloud Manager, doté d’étapes et d’informations de feedback spécifiques. Les tests d’interface utilisateur, y compris les tests de régression et de nouvelles fonctionnalités, permettront de détecter les erreurs et de les signaler dans le contexte du client.

Les tests de l’interface utilisateur client s’exécutent automatiquement sur le canal Production, dans l’étape « Tests personnalisés de l’interface utilisateur ».

Contrairement aux tests fonctionnels personnalisés qui sont des tests HTTP écrits en java, les tests de l’interface utilisateur peuvent être une image docker avec des tests écrits dans n’importe quelle langue, à condition qu’ils respectent les conventions définies dans [Création de tests d’interface utilisateur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/ui-testing.html?lang=fr#using-cloud-manager).

>[!NOTE]
>Il est recommandé de suivre la structure et le langage *(js et wdio)* qui sont fournis comme base pratique dans l’[Archétype de projet AEM](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests).

### Souscription client {#customer-opt-in}

Pour que leurs tests d’interface utilisateur soient créés et exécutés, les clients doivent « souscrire » en ajoutant un fichier à leur référentiel de code, dans le sous-module maven pour les tests d’interface utilisateur (en regard du fichier pom.xml du sous-module de test d’interface utilisateur) et s’assurer que ce fichier est à la racine du fichier `tar.gz` créé.

*Nom du fichier* : `testing.properties`

*Contenu* : `ui-tests.version=1`

S’il ne se trouve pas dans le fichier `tar.gz` créé, les tests de l’interface utilisateur vont s’accumuler et leur exécution va être ignorée.

Pour ajouter un fichier `testing.properties` dans l’artefact créé, ajoutez une instruction `include` dans le fichier `assembly-ui-test-docker-context.xml` (dans le sous-module de tests de l’interface utilisateur) :

    ```
    [...]
    &lt;includes>
    &lt;include>Dockerfile&lt;/include>
    &lt;include>wait-for-grid.sh&lt;/include>
    &lt;include>testing.properties&lt;/include> &lt;!- module de test d’opt-in dans Cloud Manager -->
    &lt;/includes>
    [...]
    ```

>[!NOTE]
>Les pipelines de production créés avant le 10 février 2021 devront être mis à jour afin d’utiliser les tests d’interface utilisateur décrits dans cette section. Cela signifie essentiellement que l’utilisateur doit modifier le pipeline de production et cliquer sur **Enregistrer** dans l’interface utilisateur, et ce, même si aucune modification n’a été apportée.
>Consultez [Configuration de votre pipeline CI-CD](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=fr#using-cloud-manager) pour en savoir plus sur la configuration du pipeline.

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

La version doit produire zéro ou une archive. S’il ne produit aucune archive, l’étape de test est effectuée par défaut. Si la version produit plusieurs archives, celle qui est sélectionnée n’est pas déterministe.

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
2. Sondage à intervalle régulier vers le [point d’entrée de statut](https://github.com/SeleniumHQ/docker-selenium/#waiting-for-the-grid-to-be-ready) exposé par l’API Selenium.

Une fois que le point d’entrée de statut de Selenium donne une réponse positive, les tests peuvent débuter.

### Génération de rapports de test {#generate-test-reports}

L’image Docker doit générer des rapports de test au format XML JUnit et les enregistrer dans le chemin spécifié par la variable d’environnement `REPORTS_PATH`. Le format XML JUnit est un format très répandu pour le rapports de résultats de tests. Si l’image Docker utilise Java et Maven, le [plug-in Maven Surefire](https://maven.apache.org/surefire/maven-surefire-plugin/) et le [plug-in Maven Failsafe](https://maven.apache.org/surefire/maven-failsafe-plugin/) sont tous deux utilisés. Si l’image Docker est implémentée avec d’autres langages de programmation ou des exécuteurs de tests, consultez la documentation des outils choisis pour savoir comment générer des rapports XML JUnit.

### Chargement de fichiers {#upload-files}

Les tests doivent parfois charger des fichiers vers l’application testée. Afin que le déploiement de Selenium reste flexible par rapport à vos tests, il n’est pas possible de charger directement une ressource vers Selenium. Au lieu de cela, le chargement d’un fichier passe par quelques étapes intermédiaires :

1. Chargement du fichier à l’URL spécifiée par la variable d’environnement `UPLOAD_URL`. Le chargement doit être effectué dans une requête POST avec un formulaire en plusieurs parties. Le formulaire en plusieurs parties doit comporter un seul champ de fichier. Cela équivaut à `curl -X POST ${UPLOAD_URL} -F "data=@file.txt"`. Consultez la documentation et les bibliothèques du langage de programmation utilisé dans l’image Docker pour savoir comment exécuter une telle requête HTTP.
2. Si le chargement aboutit, la requête renvoie une réponse `200 OK` de type `text/plain`. Le contenu de la réponse est une gestion de fichier opaque. Vous pouvez utiliser cette gestion à la place d’un chemin de fichier dans un élément `<input>` pour tester les chargements de fichiers dans votre application.
