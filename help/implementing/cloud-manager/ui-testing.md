---
title: Tests de l’interface utilisateur
description: Le test personnalisé d’interface utilisateur est une fonctionnalité facultative qui vous permet de créer et d’exécuter automatiquement des tests d’interface utilisateur pour vos applications personnalisées.
exl-id: 3009f8cc-da12-4e55-9bce-b564621966dd
source-git-commit: 3e31b065999d36717b81253d2773e41b76949954
workflow-type: tm+mt
source-wordcount: '2141'
ht-degree: 56%

---


# Tests de l’interface utilisateur {#ui-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_uitesting"
>title="Tests de l’interface utilisateur"
>abstract="Le test d’interface utilisateur personnalisé est une fonctionnalité facultative qui vous permet de créer et d’exécuter automatiquement des tests d’interface utilisateur pour vos applications. Les tests de l’interface utilisateur sont des tests basés sur Selenium placés dans une image Docker afin de permettre un large choix de langues et de cadres (tels que Java et Maven, Node et WebDriver.io, ou tout autre cadre et technologie basés sur Selenium)."

Le test d’interface utilisateur personnalisé est une fonctionnalité facultative qui vous permet de créer et d’exécuter automatiquement des tests d’interface utilisateur pour vos applications.

## Présentation {#custom-ui-testing}

AEM fournit une suite intégrée de [points de contrôle de qualité Cloud Manager](/help/implementing/cloud-manager/custom-code-quality-rules.md) pour garantir la fluidité de la mise à jour des applications personnalisées. En particulier, les points de contrôle des tests informatiques prennent déjà en charge la création et l’automatisation de tests personnalisés à l’aide des API AEM.

Les tests de l’interface utilisateur sont des tests basés sur Selenium placés dans une image Docker afin de permettre un large choix de langues et de cadres (tels que Java et Maven, Node et WebDriver.io, ou tout autre cadre et technologie basés sur Selenium). En outre, un projet de tests d’interface utilisateur peut facilement être généré en utilisant [l’archétype de projet AEM.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr)

Les tests de l’interface utilisateur sont exécutés dans le cadre d’un point de contrôle qualité spécifique pour chaque pipeline Cloud Manager avec une étape [dédiée au **Test personnalisé de l’interface utilisateur**.](/help/implementing/cloud-manager/deploy-code.md) Tous les tests de l’interface utilisateur, y compris les régressions et les nouvelles fonctionnalités, permettent de détecter et de signaler des erreurs.

Contrairement aux tests fonctionnels personnalisés qui sont des tests HTTP écrits en Java, les tests de l’interface utilisateur peuvent être une image Docker avec des tests écrits dans n’importe quelle langue, à condition qu’ils respectent les conventions définies dans la section [Création de tests d’interface utilisateur.](#building-ui-tests)

>[!TIP]
>
>Adobe recommande de suivre la structure et le langage (JavaScript et WDIO) fournis dans l’[Archétype de projet AEM.](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests)
>
>Adobe fournit également un exemple de module de test d’interface utilisateur basé sur Java et WebDriver. Reportez-vous à la section [AEM Référentiel d’exemples de test](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-selenium-webdriver) pour plus d’informations.

## Prise en main des tests de l’interface utilisateur {#get-started-ui-tests}

Cette section décrit les étapes requises pour configurer des tests d’interface utilisateur pour une exécution dans Cloud Manager.

1. Déterminez le langage de programmation que vous souhaitez utiliser.

   * Pour JavaScript et WDIO, utilisez l’exemple de code généré automatiquement dans la variable `ui.tests` de votre référentiel Cloud Manager.

      >[!NOTE]
      >
      >Si votre référentiel a été créé avant la création automatique de Cloud Manager `it.tests` , vous pouvez également générer la dernière version à l’aide de la variable [AEM Archétype de projet.](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/it.tests)

   * Pour Java et WebDriver, utilisez l’exemple de code du [AEM Référentiel d’exemples de test.](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-selenium-webdriver)

   * Pour les autres langages de programmation, reportez-vous à la section [Création de tests d’interface utilisateur](#building-ui-tests) dans ce document pour configurer le projet test.

1. Assurez-vous que le test de l’interface utilisateur est activé conformément à la section . [Accord préalable client](#customer-opt-in) dans ce document.

1. Développez vos cas de test et [exécutez les tests localement.](#run-ui-tests-locally)

1. Validez votre code dans le référentiel Cloud Manager et exécutez un pipeline Cloud Manager.

## Création de tests de l’interface utilisateur {#building-ui-tests}

Un projet Maven génère un contexte de build Docker. Ce contexte de création Docker décrit comment créer une image Docker contenant les tests d’interface utilisateur, que Cloud Manager utilise pour générer une image Docker contenant les tests d’interface utilisateur réels.

Cette section décrit les étapes à suivre pour ajouter un projet de tests de l’interface utilisateur à votre référentiel.

>[!TIP]
>
>Le [AEM Archétype de projet](https://github.com/adobe/aem-project-archetype) Vous pouvez générer pour vous un projet de tests d’interface utilisateur, conforme à la description suivante, si vous n’avez pas d’exigences spéciales pour le langage de programmation.

### Générer un contexte de build Docker {#generate-docker-build-context}

Pour générer un contexte de création Docker, vous avez besoin d’un module Maven qui :

* Génère une archive contenant un `Dockerfile` et tout autre fichier nécessaire pour créer l’image Docker avec vos tests.
* Balise l’archive avec le classificateur `ui-test-docker-context`.

La méthode la plus simple pour y parvenir consiste à configurer le [plug-in Maven Assembly](https://maven.apache.org/plugins/maven-assembly-plugin/) pour créer l’archive de contexte de création Docker et lui affecter le classificateur approprié.

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

Cette exécution indique au module d’extension Maven Assembly de créer une archive basée sur les instructions contenues dans `assembly-ui-test-docker-context.xml`, nommée **descripteur d’assemblage** dans le jargon du plug-in. Le descripteur d’assemblage répertorie tous les fichiers qui doivent faire partie de l’archive.

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

Le descripteur d’assemblage demande au module d’extension de créer une archive de type `.tar.gz` et lui affecte le classificateur `ui-test-docker-context`. En outre, il répertorie les fichiers qui doivent être inclus dans l’archive, parmi lesquels les éléments suivants.

* Un `Dockerfile`, obligatoire pour la création de l’image Docker
* Le script `wait-for-grid.sh` dont les objectifs sont décrits ci-dessous
* Des tests d’interface utilisateur, implémentés par un projet Node.js dans le dossier `test-module`

Le descripteur d’assemblage exclut également certains fichiers qui pourraient être générés lors de l’exécution locale des tests de l’interface utilisateur. Cela garantit une archive plus petite et accélère la création.

L’archive contenant le contexte de création Docker est automatiquement récupérée par Cloud Manager, qui crée l’image Docker contenant vos tests pendant ses pipelines de déploiement. Cloud Manager exécute ensuite l’image Docker pour réaliser les tests de l’interface utilisateur sur votre application.

Le build doit produire zéro ou une archive. S’il ne produit aucune archive, l’étape de test est effectuée par défaut. Si le build produit plusieurs archives, celle qui est sélectionnée est non déterministe.

### Accord préalable client {#customer-opt-in}

Pour que Cloud Manager puisse créer et exécuter vos tests d’interface utilisateur, vous devez souscrire à cette fonctionnalité en ajoutant un fichier à votre référentiel.

* Le nom du fichier doit être `testing.properties`.
* Le contenu du fichier doit être `ui-tests.version=1`.
* Le fichier doit se trouver sous le sous-module Maven pour les tests de l’interface utilisateur en regard de la variable `pom.xml` du sous-module tests de l’interface utilisateur.
* Le fichier doit se trouver à la racine du fichier `tar.gz` créé.

La génération et l’exécution des tests de l’interface utilisateur seront ignorées si ce fichier n’est pas présent.

Pour inclure un fichier `testing.properties` dans l’artefact de build, ajoutez une instruction `include` dans le fichier `assembly-ui-test-docker-context.xml`.

```xml
[...]
<includes>
    <include>Dockerfile</include>
    <include>wait-for-grid.sh</include>
    <include>testing.properties</include> <!-- opt-in test module in Cloud Manager -->
</includes>
[...]
```

>[!NOTE]
>
>Si votre projet n’inclut pas cette ligne, vous devrez modifier ce fichier pour souscrire au test de l’interface utilisateur.
>
>Il se peut que ce fichier contienne une ligne vous conseillant de ne pas le modifier. Cet avertissement est dû au fait qu’il a été introduit dans votre projet avant la souscription au test de l’interface utilisateur et qu’il n’était pas prévu que le clients puissent modifier le fichier. Vous pouvez l’ignorer en toute sécurité.

Si vous utilisez les exemples fournis par Adobe :

* Pour le JavaScript `ui.tests` dossier généré à partir de [AEM Archétype de projet](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests), vous pouvez exécuter la commande ci-dessous pour ajouter la configuration requise.

   ```shell
   echo "ui-tests.version=1" > testing.properties
   
   if ! grep -q "testing.properties" "assembly-ui-test-docker-context.xml"; then
     awk -v line='                <include>testing.properties</include>' '/<include>wait-for-grid.sh<\/include>/ { printf "%s\n%s\n", $0, line; next }; 1' assembly-ui-test-docker-context.xml > assembly-ui-test-docker-context.xml.new && mv assembly-ui-test-docker-context.xml.new assembly-ui-test-docker-context.xml
   fi
   ```

* L’indicateur d’inclusion est déjà défini pour les exemples de test Java fournis.

## Rédiger des tests de l’interface utilisateur {#writing-ui-tests}

Cette section décrit les conventions que l’image Docker contenant vos tests de l’interface utilisateur doit respecter. L’image Docker est créée à partir du contexte de création Docker décrit dans la section précédente.

### Variables d’environnement {#environment-variables}

Les variables d’environnement suivantes seront transmises à votre image Docker au moment de l’exécution.

| Variable | Exemples | Description |
|---|---|---|
| `SELENIUM_BASE_URL` | `http://my-ip:4444` | URL du serveur Selenium |
| `SELENIUM_BROWSER` | `chrome` | Implémentation du navigateur utilisée par le serveur Selenium |
| `AEM_AUTHOR_URL` | `http://my-ip:4502/context-path` | URL de l’instance de création AEM |
| `AEM_AUTHOR_USERNAME` | `admin` | Nom d’utilisateur pour se connecter à l’instance d’auteur AEM |
| `AEM_AUTHOR_PASSWORD` | `admin` | Mot de passe pour se connecter à l’instance d’auteur AEM |
| `AEM_PUBLISH_URL` | `http://my-ip:4503/context-path` | URL de l’instance de publication AEM |
| `AEM_PUBLISH_USERNAME` | `admin` | Nom d’utilisateur pour se connecter à l’instance de publication AEM |
| `AEM_PUBLISH_PASSWORD` | `admin` | Mot de passe pour se connecter à l’instance de publication AEM |
| `REPORTS_PATH` | `/usr/src/app/reports` | Chemin d’accès où le rapport XML des résultats du test doit être enregistré |
| `UPLOAD_URL` | `http://upload-host:9090/upload` | URL vers laquelle le fichier doit être chargé afin de le rendre accessible à Selenium |

Les exemples de test d’Adobe fournissent des fonctions d’assistance pour accéder aux paramètres de configuration :

* JavaScript : Voir [lib/config.js](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/test-module/lib/config.js) module
* Java : Voir [Config](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/Config.java) class

### Attendre la préparation de Selenium {#waiting-for-selenium}

Avant le début des tests, l’image Docker doit garantir que le serveur Selenium est opérationnel. L’attente du service de Selenium est un processus en deux étapes.

1. Lecture de l’URL du service Selenium à partir de la variable d’environnement `SELENIUM_BASE_URL`.
1. Sondage à intervalle régulier vers le [point d’entrée de statut](https://github.com/SeleniumHQ/docker-selenium/#waiting-for-the-grid-to-be-ready) exposé par l’API Selenium.

Une fois que le point d’entrée du statut de Selenium donne une réponse positive, les tests peuvent débuter.

Les exemples de test de l’interface utilisateur de l’Adobe gèrent cela avec le script. `wait-for-grid.sh`, qui est exécuté au démarrage de Docker et ne lance l’exécution réelle du test qu’une fois la grille prête.

### Générer des rapports de test {#generate-test-reports}

L’image Docker doit générer des rapports de test au format XML JUnit et les enregistrer dans le chemin spécifié par la variable d’environnement `REPORTS_PATH`. Le format XML JUnit est un format très répandu pour les rapports de résultats de tests. Si l’image Docker utilise Java et Maven, les modules de test standard tels que le [plug-in Maven Surefire](https://maven.apache.org/surefire/maven-surefire-plugin/) et le [plug-in Maven Failsafe](https://maven.apache.org/surefire/maven-failsafe-plugin/) peuvent générer ces rapports prêts à l’emploi.

Si l’image Docker est implémentée avec d’autres langages de programmation ou des exécuteurs de tests, consultez la documentation des outils choisis pour savoir comment générer des rapports XML JUnit.

>[!NOTE]
>
>Le résultat de l’étape de test de l’interface utilisateur est évalué uniquement en fonction des rapports de test. Veillez à générer le rapport en conséquence pour votre exécution de test.
>
>Utilisez des assertions au lieu de simplement consigner une erreur dans STDERR ou de renvoyer un code de sortie non nul, sinon votre pipeline de déploiement peut continuer normalement.

### Captures d’écran et vidéos {#capture-screenshots}

L’image Docker peut générer une sortie de test supplémentaire (par exemple, des captures d’écran ou des vidéos) et les enregistrer dans le chemin spécifié par la variable d’environnement. `REPORTS_PATH`. Tout fichier situé sous la variable d’environnement `REPORTS_PATH` est inclus dans l’archive des résultats du test.

Les exemples de test fournis par Adobe créent par défaut des captures d’écran pour tout test ayant échoué.

Vous pouvez utiliser les fonctions d’assistance pour créer des captures d’écran à travers vos tests.

* JavaScript : [takeScreenshot, commande](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/test-module/lib/commons.js)
* Java : [Commandes](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/Commands.java)

Si une archive de résultats de test est créée lors de l’exécution d’un test de l’interface utilisateur, vous pouvez la télécharger à partir de Cloud Manager à l’aide de la fonction `Download Details` sous le bouton [**Tests de l’interface utilisateur personnalisée** étape .](/help/implementing/cloud-manager/deploy-code.md)

### Charger des fichiers {#upload-files}

Les tests doivent parfois charger des fichiers vers l’application en cours de test. Afin que le déploiement de Selenium puisse s’adapter à vos tests, il n’est pas possible de charger directement une ressource vers Selenium. Au lieu de cela, le chargement d’un fichier nécessite de suivre les étapes suivantes.

1. Chargez le fichier à l’URL spécifiée par la variable d’environnement `UPLOAD_URL`. 
   * Le chargement doit être effectué dans une requête POST avec un formulaire en plusieurs parties.
   * Le formulaire en plusieurs parties doit comporter un seul champ de fichier.
   * Celui-ci doit être équivalent à `curl -X POST ${UPLOAD_URL} -F "data=@file.txt"`.
   * Consultez la documentation et les bibliothèques du langage de programmation utilisé dans l’image Docker pour savoir comment exécuter une telle requête HTTP.
   * Les exemples de test d’Adobe fournissent des fonctions d’assistance pour le téléchargement de fichiers :
      * JavaScript : Voir [getFileHandleForUpload](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/test-module/lib/wdio.commands.js) .
      * Java : Voir [FileHandler](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/FileHandler.java) classe .
1. Si le chargement aboutit, la requête renvoie une réponse `200 OK` de type `text/plain`.
   * Le contenu de la réponse est une gestion de fichier opaque.
   * Vous pouvez utiliser cette gestion à la place d’un chemin de fichier dans un élément `<input>` pour tester les chargements de fichiers dans votre application.

## Exécution locale de tests de l’interface utilisateur {#run-ui-tests-locally}

Avant d’activer les tests de l’interface utilisateur dans un pipeline Cloud Manager, il est recommandé d’exécuter localement les tests de l’interface utilisateur vers l’ [AEM SDK as a Cloud Service](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) ou dans une instance as a Cloud Service d’AEM réelle.

### Prérequis {#prerequisites}

Les tests dans Cloud Manager seront exécutés à l’aide d’un utilisateur administrateur technique.

Pour exécuter les tests de l’interface utilisateur à partir de votre ordinateur local, créez un utilisateur avec des autorisations de type administrateur afin d’obtenir le même comportement.

### Exemple de test JavaScript {#javascript-sample}

1. Ouvrez un conteneur et accédez à la `ui.tests` dossier dans votre référentiel

1. Exécutez la commande ci-dessous pour lancer les tests à l’aide de Maven.

   ```shell
   mvn verify -Pui-tests-local-execution \
   -DAEM_AUTHOR_URL=https://author-<program-id>-<environment-id>.adobeaemcloud.com \
   -DAEM_AUTHOR_USERNAME=<user> \
   -DAEM_AUTHOR_PASSWORD=<password> \
   -DAEM_PUBLISH_URL=https://publish-<program-id>-<environment-id>.adobeaemcloud.com \
   -DAEM_PUBLISH_USERNAME=<user> \
   -DAEM_PUBLISH_PASSWORD=<password> \
   -DHEADLESS_BROWSER=true \
   -DSELENIUM_BROWSER=chrome
   ```

>[!NOTE]
>
>* Cela lance une instance de sélénium autonome et exécute les tests sur cette instance.
>* Les fichiers journaux sont stockés dans la variable `target/reports` dossier de votre référentiel
>* Vous devez vous assurer que vous utilisez la dernière version de Chrome alors que le test télécharge automatiquement la dernière version de ChromeDriver à des fins de test.
>
>Pour plus d’informations, reportez-vous à la section [AEM référentiel de l’archétype de projet.](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/README.md)

### Exemple de test Java {#java-sample}

1. Ouvrez un conteneur et accédez à la `ui.tests/test-module` dossier dans votre référentiel

1. Exécutez la commande ci-dessous pour lancer les tests à l’aide de Maven.

   ```shell
   # Start selenium docker image (for x64 CPUs)
   docker run --platform linux/amd64 -d -p 4444:4444 selenium/standalone-chrome-debug:latest
   
   # Start selenium docker image (for ARM CPUs)
   docker run -d -p 4444:4444 seleniarm/standalone-chromium
   
   # Run the tests using the previously started Selenium instance
   mvn verify -Pui-tests-local-execution -DSELENIUM_BASE_URL=http://<server>:<port>
   ```

>[!NOTE]
>
>* Les fichiers journaux seront stockés dans la variable `target/reports` de votre référentiel.
>
>Pour plus d’informations, reportez-vous à la section [AEM Référentiel d’exemples de test.](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/README.md)
