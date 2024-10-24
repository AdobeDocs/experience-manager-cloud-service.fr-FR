---
title: Tests de l’interface utilisateur
description: Le test personnalisé d’interface utilisateur est une fonctionnalité facultative qui vous permet de créer et d’exécuter automatiquement des tests d’interface utilisateur pour vos applications personnalisées.
exl-id: 3009f8cc-da12-4e55-9bce-b564621966dd
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 8703240a5b7b8ed751620f602470da45025f7b74
workflow-type: tm+mt
source-wordcount: '2698'
ht-degree: 74%

---


# Tests de l’interface utilisateur {#ui-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_uitesting"
>title="Tests de l’interface utilisateur"
>abstract="Le test d’interface utilisateur personnalisé est une fonctionnalité facultative qui vous permet de créer et d’exécuter automatiquement des tests d’interface utilisateur pour vos applications. Les tests de l’interface utilisateur sont des tests basés sur Selenium placés dans une image Docker pour permettre un large choix de langues et de cadres (tels que Java et Maven, Node et WebDriver.io, ou tout autre cadre et technologie basés sur Selenium)."

Le test d’interface utilisateur personnalisé est une fonctionnalité facultative qui vous permet de créer et d’exécuter automatiquement des tests d’interface utilisateur pour vos applications.

## Vue d’ensemble {#custom-ui-testing}

AEM fournit une suite intégrée de [points de contrôle de qualité Cloud Manager](/help/implementing/cloud-manager/custom-code-quality-rules.md) pour garantir la fluidité de la mise à jour des applications personnalisées. En particulier, les points de contrôle informatiques prennent déjà en charge la création et l’automatisation des tests personnalisés à l’aide des API d’AEM.

Les tests de l’interface utilisateur sont empaquetés dans une image Docker afin de permettre un large choix de langages et de structures (telles que Cypress, Selenium, Java et Maven, ou encore Javascript). En outre, un projet de tests d’interface utilisateur peut facilement être généré en utilisant [l’ archétype de projet AEM](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/developing/archetype/overview).

Adobe encourage l’utilisation de Cypress, car il propose un rechargement en temps réel et une attente automatique, ce qui permet de gagner du temps et d’améliorer la productivité pendant les tests. Cypress fournit également une syntaxe simple et intuitive, ce qui facilite l’apprentissage et l’utilisation, même pour les personnes qui n’ont pas l’habitude d’effectuer des tests.

Les tests de l’interface utilisateur sont exécutés dans le cadre d’un point de contrôle qualité spécifique pour chaque pipeline Cloud Manager avec une étape de [**Tests de l’interface utilisateur personnalisée** ](/help/implementing/cloud-manager/deploy-code.md) dans les [pipelines de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) ou dans les [pipelines hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md). Tous les tests de l’interface utilisateur, y compris les régressions et les nouvelles fonctionnalités, permettent de détecter et de signaler des erreurs.

Contrairement aux tests fonctionnels personnalisés qui sont des tests HTTP écrits en Java, les tests de l’interface utilisateur peuvent être une image Docker avec des tests écrits dans n’importe quelle langue, à condition qu’ils respectent les conventions définies dans la section [Création de tests d’interface utilisateur](#building-ui-tests).

>[!TIP]
>
>Adobe recommande d’utiliser Cypress pour le test de l’interface utilisateur, en respectant le code fourni dans la section [Référentiel d’exemples de test AEM](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-cypress).
> 
>Adobe fournit également des exemples de module de test d’interface utilisateur basés sur JavaScript avec WebdriverIO (voir [Archétype de projet AEM](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests)) et Java avec WebDriver (voir [Référentiel d’exemples de test AEM](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-selenium-webdriver)).

## Prise en main des tests d’interface utilisateur {#get-started-ui-tests}

Cette section décrit les étapes requises pour configurer des tests d’interface utilisateur pour une exécution dans Cloud Manager.

1. Déterminez la structure de test que vous souhaitez utiliser.

   * Pour Cypress (par défaut), utilisez l’exemple de code du [référentiel d’exemples de test d’AEM](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-cypress) ou utilisez l’exemple de code généré automatiquement dans le dossier `ui.tests` de votre référentiel Cloud Manager.

   * Pour Playwright, utilisez l’exemple de code du [référentiel d’exemples de test d’AEM](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-playwright).

   * Pour Webdriver.IO, utilisez l’exemple de code du référentiel [AEM Test Samples repository](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-wdio).

   * Pour Selenium WebDriver, utilisez l’exemple de code du [référentiel d’exemples de test d’AEM](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-selenium-webdriver).

   * Pour les autres langages de programmation, reportez-vous à la section [Création de tests d’interface utilisateur](#building-ui-tests) dans ce document pour configurer le projet test.

1. Assurez-vous que le test de l’interface utilisateur est activé conformément à la section [Accord préalable client](#customer-opt-in) de ce document.

1. Développez vos cas de test et [exécutez les tests localement](#run-ui-tests-locally).

1. Validez votre code dans le référentiel Cloud Manager et exécutez un pipeline Cloud Manager.

## Création de tests de l’interface utilisateur {#building-ui-tests}

Un projet Maven génère un contexte de build Docker. Ce contexte de build Docker décrit comment créer une image Docker contenant les tests de l’interface utilisateur que les utilisateurs et utilisatrices de Cloud Manager utilisent pour générer une image Docker contenant les tests de l’interface utilisateur réels.

Cette section décrit les étapes à suivre pour ajouter un projet de tests de l’interface utilisateur à votre référentiel.

>[!TIP]
>
>L’[archétype de projet AEM](https://github.com/adobe/aem-project-archetype) peut générer pour vous un projet de tests de l’interface utilisateur, conforme à la description suivante, si vous n’avez pas d’exigences spéciales pour le langage de programmation.

### Générer un contexte Docker Build {#generate-docker-build-context}

Pour générer un contexte Docker Build, vous avez besoin d’un module Maven qui :

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

Le descripteur d’assemblage demande au module d’extension de créer une archive de type `.tar.gz` et lui affecte le classificateur `ui-test-docker-context`. De plus, il répertorie les fichiers qui doivent être inclus dans l’archive, notamment :

* Un `Dockerfile`, obligatoire pour la création de l’image Docker
* Le script `wait-for-grid.sh` dont les objectifs sont décrits ci-dessous
* Des tests d’interface utilisateur, implémentés par un projet Node.js dans le dossier `test-module`

Le descripteur d’assemblage exclut également certains fichiers qui pourraient être générés lors de l’exécution locale des tests de l’interface utilisateur. Cela garantit une archive plus petite et accélère la création.

L’archive contenant le contexte de création Docker est automatiquement récupérée par Cloud Manager, qui crée l’image Docker contenant vos tests pendant ses pipelines de déploiement. Cloud Manager exécute ensuite l’image Docker pour réaliser les tests de l’interface utilisateur sur votre application.

Le build doit produire zéro ou une archive. S’il ne produit aucune archive, l’étape de test est effectuée par défaut. Si le build produit plusieurs archives, celle qui est sélectionnée est non déterministe.

### Accord préalable client {#customer-opt-in}

Pour que Cloud Manager puisse créer et exécuter vos tests d’interface utilisateur, vous devez souscrire à cette fonctionnalité en ajoutant un fichier à votre référentiel.

* Le nom du fichier doit être `testing.properties`.
* Le contenu du fichier doit être `ui-tests.version=1`.
* Le fichier doit se trouver sous le sous-module Maven pour les tests de l’interface utilisateur, à côté du fichier `pom.xml` du sous-module de tests de l’interface utilisateur.
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
>Si votre projet n’inclut pas cette ligne, modifiez le fichier pour activer le test de l’interface utilisateur.
>
>Il se peut que ce fichier contienne une ligne vous conseillant de ne pas le modifier. Cela est dû au fait qu’il a été introduit dans votre projet avant la souscription au test de l’interface utilisateur et qu’il n’était pas prévu que le clients et clientes puissent modifier le fichier. Vous pouvez l’ignorer en toute sécurité.

Si vous utilisez les exemples fournis par Adobe :

* Pour le dossier `ui.tests` JavaScript généré à partir de l’[archétype de projet AEM](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests), vous pouvez exécuter la commande ci-dessous pour ajouter la configuration requise.

  ```shell
  echo "ui-tests.version=1" > testing.properties
  
  if ! grep -q "testing.properties" "assembly-ui-test-docker-context.xml"; then
    awk -v line='                <include>testing.properties</include>' '/<include>wait-for-grid.sh<\/include>/ { printf "%s\n%s\n", $0, line; next }; 1' assembly-ui-test-docker-context.xml > assembly-ui-test-docker-context.xml.new && mv assembly-ui-test-docker-context.xml.new assembly-ui-test-docker-context.xml
  fi
  ```

* Les exemples de test Cypress et Java Selenium fournis par Adobe disposent déjà de l’indicateur d’inclusion défini.

## Rédiger des tests de l’interface utilisateur {#writing-ui-tests}

Cette section décrit les conventions que l’image Docker contenant vos tests de l’interface utilisateur doit respecter. L’image Docker est créée à partir du contexte de création Docker décrit dans la section précédente.

### Variables d’environnement {#environment-variables}

Les variables d’environnement suivantes seront transmises à votre image Docker au moment de l’exécution, en fonction de votre framework.

>[!NOTE]
>
> Ces valeurs seront définies automatiquement lors de l’exécution du pipeline. Il n’est pas nécessaire de les définir manuellement en tant que variables de pipeline.

| Variable | Exemples | Description | Cadre de test |
|----------------------------|----------------------------------|----------------------------------------------------------------------------------------------------|---------------------|
| `SELENIUM_BASE_URL` | `http://my-ip:4444` | URL du serveur Selenium | Selenium uniquement |
| `SELENIUM_BROWSER` | `chrome` | Implémentation du navigateur utilisée par le serveur Selenium | Selenium uniquement |
| `AEM_AUTHOR_URL` | `http://my-ip:4502/context-path` | URL de l’instance de création AEM | Tous |
| `AEM_AUTHOR_USERNAME` | `admin` | Nom d’utilisateur pour la connexion à l’instance de création AEM | Tous |
| `AEM_AUTHOR_PASSWORD` | `admin` | Mot de passe de connexion à l’instance de création AEM | Tous |
| `AEM_PUBLISH_URL` | `http://my-ip:4503/context-path` | URL de l’instance de publication AEM | Tous * |
| `AEM_PUBLISH_USERNAME` | `admin` | Nom d’utilisateur pour la connexion à l’instance de publication AEM | Tous * |
| `AEM_PUBLISH_PASSWORD` | `admin` | Mot de passe pour se connecter à l’instance de publication AEM | Tous * |
| `REPORTS_PATH` | `/usr/src/app/reports` | Chemin d’accès où le rapport XML des résultats du test doit être enregistré. | Tous |
| `UPLOAD_URL` | `http://upload-host:9090/upload` | URL vers laquelle le fichier doit être chargé afin de le rendre accessible au framework de test | Tous |
| `PROXY_HOST` | `proxy-host` | Nom d’hôte du proxy HTTP interne à utiliser par la structure de test. | Tous sauf Selenium |
| `PROXY_HTTPS_PORT` | `8071` | Le port d’écoute du serveur proxy pour les connexions HTTPS (peut être vide) | Tous sauf Selenium |
| `PROXY_HTTP_PORT` | `8070` | Le port d’écoute du serveur proxy pour les connexions HTTP (peut être vide) | Tous sauf Selenium |
| `PROXY_CA_PATH` | `/path/to/root_ca.pem` | Le chemin d’accès au certificat de l’autorité de certification à utiliser par la structure de test | Tous sauf Selenium |
| `PROXY_OBSERVABILITY_PORT` | `8081` | Port HTTP healthcheck du serveur proxy | Tous sauf Selenium |
| `PROXY_RETRY_ATTEMPTS` | `12` | Nombre suggéré de tentatives de reprise en attendant la préparation du serveur proxy | Tous sauf Selenium |
| `PROXY_RETRY_DELAY` | `5` | Délai suggéré entre les tentatives de reprise en attendant la préparation du serveur proxy | Tous sauf Selenium |

`* these values will be empty if there is no publish instance`

Les exemples de test d’Adobe fournissent des fonctions d’assistance pour accéder aux paramètres de configuration :

* Cypress : utiliser la fonction standard `Cypress.env('VARIABLE_NAME')`
* JavaScript : voir le module [`lib/config.js`](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests.wdio/test-module/lib/config.js)
* Java : Voir la classe [`Config`](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/Config.java)

### Générer des rapports de test {#generate-test-reports}

L’image Docker doit générer des rapports de test au format XML JUnit et les enregistrer dans le chemin spécifié par la variable d’environnement `REPORTS_PATH`. Le format XML JUnit est un format très répandu pour les rapports de résultats de tests. Si l’image Docker utilise Java et Maven, les modules de test standard tels que le [plug-in Maven Surefire](https://maven.apache.org/surefire/maven-surefire-plugin/) et le [plug-in Maven Failsafe](https://maven.apache.org/surefire/maven-failsafe-plugin/) peuvent générer ces rapports prêts à l’emploi.

Si l’image Docker est implémentée avec d’autres langages de programmation ou des exécuteurs de tests, consultez la documentation des outils choisis pour savoir comment générer des rapports XML JUnit.

>[!NOTE]
>
>Le résultat de l’étape de test de l’interface utilisateur est évalué uniquement en fonction des rapports de test. Veillez à générer le rapport en conséquence pour votre exécution de test.
>
>Utilisez des assertions au lieu de simplement consigner une erreur dans STDERR ou de renvoyer un code de sortie non nul. Autrement, votre pipeline de déploiement pourra continuer normalement.
>
>Si un proxy HTTP a été utilisé pendant l’exécution des tests, les résultats incluront un fichier `request.log`.

### Prérequis {#prerequisites}

* Les tests dans Cloud Manager sont exécutés par une personne administratrice technique.

>[!NOTE]
>
>Pour exécuter les tests fonctionnels à partir de votre ordinateur local, créez un utilisateur ou une utilisatrice avec des autorisations de type administration afin d’obtenir le même comportement.

* L’infrastructure en conteneur qui est prévue pour les tests fonctionnels est restreinte par les limites suivantes :

| Type | Valeur | Description |
|----------------------|-------|-----------------------------------------------------------------------|
| Processeur | 2.0 | Laps de temps CPU réservé par exécution de test. |
| Mémoire | 1Gi | Quantité de mémoire allouée au test, valeur en gibioctets. |
| Expiration | 30m | Durée au bout de laquelle le test est terminé. |
| Durée recommandée | 15m | Adobe recommande d’écrire les tests pour qu’ils ne prennent pas plus de temps que la durée indiquée. |

>[!NOTE]
>
> Si vous avez besoin de davantage de ressources, veuillez créer un cas d’assistance clientèle et décrire votre cas d’utilisation ; Adobe examinera votre demande et vous fournira l’aide appropriée.

## Détails spécifiques à Selenium

>[!NOTE]
>
>Cette section s’applique uniquement lorsque Selenium est l’infrastructure de test choisie.

### Attendre la préparation de Selenium {#waiting-for-selenium}

Avant le début des tests, l’image Docker doit garantir que le serveur Selenium est opérationnel. L’attente du service de Selenium est un processus en deux étapes.

1. Lecture de l’URL du service Selenium à partir de la variable d’environnement `SELENIUM_BASE_URL`.
1. Sondage à intervalles réguliers au [point d’entrée de statut](https://github.com/SeleniumHQ/docker-selenium/#waiting-for-the-grid-to-be-ready) exposé par l’API Selenium.

Une fois que le point d’entrée du statut de Selenium donne une réponse positive, les tests peuvent débuter.

Les exemples de test de l’interface utilisateur Adobe s’en occupent avec le script `wait-for-grid.sh`, qui est exécuté au démarrage de Docker et ne lance l’exécution réelle du test qu’une fois la grille prête.

### Captures d’écran et vidéos {#capture-screenshots}

L’image Docker peut générer une sortie de test supplémentaire (par exemple, des captures d’écran ou des vidéos) et les enregistrer dans le chemin spécifié par la variable d’environnement `REPORTS_PATH`. Tout fichier situé sous la variable d’environnement `REPORTS_PATH` est inclus dans l’archive des résultats du test.

Les exemples de test fournis par Adobe créent par défaut des captures d’écran pour tout test ayant échoué.

Vous pouvez utiliser les fonctions d’assistance pour créer des captures d’écran durant vos tests.

* JavaScript : [commande takeScreenshot](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/test-module/lib/commons.js)
* Java : [commandes](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/Commands.java)

Si une archive de résultats de test est créée lors de l’exécution d’un test de l’interface utilisateur, vous pouvez la télécharger à partir de Cloud Manager. Pour cela, cliquez sur le bouton `Download Details` sous l’étape [**Tests de l’interface utilisateur personnalisée**.](/help/implementing/cloud-manager/deploy-code.md)

### Charger des fichiers {#upload-files}

Les tests doivent parfois charger des fichiers vers l’application en cours de test. Afin que le déploiement de Selenium puisse s’adapter à vos tests, il n’est pas possible de charger directement une ressource vers Selenium. Au lieu de cela, le chargement d’un fichier nécessite de suivre les étapes suivantes.

1. Chargez le fichier à l’URL spécifiée par la variable d’environnement `UPLOAD_URL`.
   * Le chargement doit être effectué dans une requête POST avec un formulaire en plusieurs parties.
   * Le formulaire en plusieurs parties doit comporter un seul champ de fichier.
   * Celui-ci doit être équivalent à `curl -X POST ${UPLOAD_URL} -F "data=@file.txt"`.
   * Consultez la documentation et les bibliothèques du langage de programmation utilisé dans l’image Docker pour savoir comment exécuter une telle requête HTTP.
   * Les exemples de test d’Adobe fournissent des fonctions d’assistance pour le téléchargement de fichiers :
      * JavaScript : voir la commande [getFileHandleForUpload](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/test-module/lib/wdio.commands.js).
      * Java : voir la classe [FileHandler](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/FileHandler.java).
1. Si le chargement aboutit, la requête renvoie une réponse `200 OK` de type `text/plain`.
   * Le contenu de la réponse est une gestion de fichier opaque.
   * Vous pouvez utiliser cette gestion à la place d’un chemin de fichier dans un élément `<input>` pour tester les chargements de fichiers dans votre application.

## Détails spécifiques à la synthèse

>[!NOTE]
>
>Cette section s’applique uniquement lorsque Cypress est l’infrastructure de test choisie.

### Configuration d’un proxy HTTP

Le point d’entrée du conteneur Docker doit vérifier la valeur de la variable d’environnement `PROXY_HOST`.

Si cette valeur est vide, aucune étape supplémentaire n’est requise et les tests doivent être exécutés sans utiliser de proxy HTTP.

S’il n’est pas vide, le script entrypoint doit :

1. Configurez une connexion proxy HTTP pour exécuter les tests de l’interface utilisateur. Pour ce faire, exportez la variable d’environnement `HTTP_PROXY` créée à l’aide des valeurs suivantes :
   * Hôte proxy fourni par la variable `PROXY_HOST`
   * Port proxy, fourni par la variable `PROXY_HTTPS_PORT` ou `PROXY_HTTP_PORT` (la variable avec une valeur non vide sera utilisée)
2. Définissez le certificat d’autorité de certification qui sera utilisé lors de la connexion au proxy HTTP. Son emplacement est fourni par la variable `PROXY_CA_PATH`.
   * Pour ce faire, exportez la variable d’environnement `NODE_EXTRA_CA_CERTS`.
3. Attendez que le proxy HTTP soit prêt.
   * Pour vérifier la préparation, les variables d&#39;environnement `PROXY_HOST`, `PROXY_OBSERVABILITY_PORT`, `PROXY_RETRY_ATTEMPTS` et `PROXY_RETRY_DELAY` peuvent être utilisées.
   * Vous pouvez vérifier à l’aide d’une requête cURL, en veillant à installer cURL dans votre `Dockerfile`.

Vous trouverez un exemple de mise en oeuvre dans Entrypoint du module de test d’exemple Cypress sur [GitHub](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-cypress/test-module/run.sh).

## Détails spécifiques à un lecteur

>[!NOTE]
>
> Cette section s’applique uniquement lorsque Playwright est l’infrastructure de test choisie.

### Configuration d’un proxy HTTP

>[!NOTE]
>
> Dans les exemples présentés, nous supposons que Chrome est utilisé comme navigateur de projet.

Comme pour Cypress, les tests doivent utiliser le proxy HTTP si une variable d&#39;environnement `PROXY_HOST` non vide est fournie.

Pour ce faire, les modifications suivantes doivent être apportées.

#### Dockerfile

Installez cURL et `libnss3-tools`, qui fournit `certutil.`

```dockerfile
RUN apt -y update \
    && apt -y --no-install-recommends install curl libnss3-tools \
    && rm -rf /var/lib/apt/lists/*
```

#### Script Entrypoint

Insérez un script bash qui, si la variable d&#39;environnement `PROXY_HOST` est fournie, effectue les opérations suivantes :

1. Exporter les variables liées au proxy telles que `HTTP_PROXY` et `NODE_EXTRA_CA_CERTS`
2. Utilisation de `certutil` pour installer le certificat d’autorité de certification proxy pour le chrome
3. Patientez jusqu’à ce que le proxy HTTP soit prêt (ou quittez en cas d’échec).

Exemple de mise en oeuvre :

```bash
# setup proxy environment variables and CA certificate
if [ -n "${PROXY_HOST:-}" ]; then
  if [ -n "${PROXY_HTTPS_PORT:-}" ]; then
    export HTTP_PROXY="https://${PROXY_HOST}:${PROXY_HTTPS_PORT}"
  elif [ -n "${PROXY_HTTP_PORT:-}" ]; then
    export HTTP_PROXY="http://${PROXY_HOST}:${PROXY_HTTP_PORT}"
  fi
  if [ -n "${PROXY_CA_PATH:-}" ]; then
    echo "installing certificate"
    mkdir -p $HOME/.pki/nssdb
    certutil -d sql:$HOME/.pki/nssdb -A -t "CT,c,c" -n "EaaS Client Proxy Root" -i $PROXY_CA_PATH
    export NODE_EXTRA_CA_CERTS=${PROXY_CA_PATH}
  fi
  if [ -n "${PROXY_OBSERVABILITY_PORT:-}" ] && [ -n "${HTTP_PROXY:-}" ]; then
    echo "waiting for proxy"
    curl --silent  --retry ${PROXY_RETRY_ATTEMPTS:-3} --retry-connrefused --retry-delay ${PROXY_RETRY_DELAY:-10} \
      --proxy ${HTTP_PROXY} --proxy-cacert ${PROXY_CA_PATH:-""} \
      ${PROXY_HOST}:${PROXY_OBSERVABILITY_PORT}
    if [ $? -ne 0 ]; then
      echo "proxy is not ready"
      exit 1
    fi
  fi
fi
```

#### Configuration du droit de lecture

Modifiez la configuration du droit de lecture (par exemple dans `playwright.config.js`) pour utiliser un proxy si la variable d’environnement `HTTP_PROXY` est définie.

Exemple de mise en oeuvre :

```javascript
const proxyServer = process.env.HTTP_PROXY || ''
```

```javascript
// enable proxy if set
if (proxyServer !== '') {
 cfg.use.proxy = {
  server: proxyServer,
 }
}
```

>[!NOTE]
>
> Vous trouverez un exemple de mise en oeuvre dans l’exemple de module de test de lecture sur [GitHub](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-playwright/).


## Exécuter les tests de l’interface utilisateur localement {#run-ui-tests-locally}

Avant d’activer les tests de l’interface utilisateur dans un pipeline Cloud Manager, il est recommandé d’exécuter localement les tests de l’interface utilisateur vers le [SDK AEM as a Cloud Service](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) ou dans une instance AEM as a Cloud Service réelle.

### Exemple de test Cypress {#cypress-sample}

1. Ouvrez une interface shell et accédez au dossier `ui.tests/test-module` dans votre référentiel

1. Installez Cypress et autres prérequis

   ```shell
   npm install
   ```

1. Définissez des variables d’environnement requises pour l’exécution du test

   ```shell
   export AEM_AUTHOR_URL=https://author-<program-id>-<environment-id>.adobeaemcloud.com
   export AEM_AUTHOR_USERNAME=<user>
   export AEM_AUTHOR_PASSWORD=<password>
   export AEM_PUBLISH_URL=https://publish-<program-id>-<environment-id>.adobeaemcloud.com
   export AEM_PUBLISH_USERNAME=<user>
   export AEM_PUBLISH_PASSWORD=<password>
   export REPORTS_PATH=target/
   ```

1. Exécutez des tests avec l’une des commandes suivantes :

   ```shell
   npm test              # Using default Cypress browser
   npm run test-chrome   # Using Google Chrome browser
   npm run test-firefox  # Using Firefox browser
   ```

>[!NOTE]
>
>Les fichiers journaux sont stockés dans le dossier `target/` de votre référentiel.
>
>Pour plus d’informations, reportez-vous au [Référentiel d’exemples de test AEM](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-cypress/test-module/README.md).

### Exemple de test JavaScript WebdriverIO {#javascript-sample}

1. Ouvrez une interface shell et accédez au dossier `ui.tests` dans votre référentiel

1. Exécutez la commande ci-dessous pour lancer les tests à l’aide de Maven.

   ```shell
   mvn verify -Pui-tests-local-execution \
    -DAEM_AUTHOR_URL=https://author-<program-id>-<environment-id>.adobeaemcloud.com \
    -DAEM_AUTHOR_USERNAME=<user> \
    -DAEM_AUTHOR_PASSWORD=<password> \
    -DAEM_PUBLISH_URL=https://publish-<program-id>-<environment-id>.adobeaemcloud.com \
    -DAEM_PUBLISH_USERNAME=<user> \
    -DAEM_PUBLISH_PASSWORD=<password>
   ```

>[!NOTE]
>
>* Vous lancez ainsi une instance autonome de Selenium et exécutez les tests sur cette instance.
>* Les fichiers journaux sont stockés dans le dossier `target/reports` de votre référentiel
>* Votre machine doit utiliser la dernière version de Chrome, car le test télécharge automatiquement la dernière version de ChromeDriver à des fins de test.
>
>Pour plus d’informations, reportez-vous au [Référentiel d’exemples de test AEM](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-wdio).

### Exemple de test de lecture {#playwright-sample}

1. Ouvrez une interface shell et accédez au dossier `ui.tests` dans votre référentiel

1. Exécutez la commande ci-dessous pour créer une image Docker à l’aide de Maven

   ```shell
   mvn clean package -Pui-tests-docker-build
   ```

1. Exécutez la commande ci-dessous pour lancer les tests à l’aide de Maven.

   ```shell
   mvn verify -Pui-tests-docker-execution \
    -DAEM_AUTHOR_URL=https://author-<program-id>-<environment-id>.adobeaemcloud.com \
    -DAEM_AUTHOR_USERNAME=<user> \
    -DAEM_AUTHOR_PASSWORD=<password> \
    -DAEM_PUBLISH_URL=https://publish-<program-id>-<environment-id>.adobeaemcloud.com \
    -DAEM_PUBLISH_USERNAME=<user> \
    -DAEM_PUBLISH_PASSWORD=<password>
   ```

>[!NOTE]
>
>Les fichiers journaux sont stockés dans le dossier `target/` de votre référentiel.
>
>Pour plus d’informations, reportez-vous au [Référentiel d’exemples de test AEM](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-playwright).


### Exemple de test Java Selenium WebDriver {#java-sample}

1. Ouvrez une interface shell et accédez au dossier `ui.tests/test-module` dans votre référentiel

1. Exécutez les commandes ci-dessous pour lancer les tests à l’aide de Maven

   ```shell
   # Start selenium docker image
   # we mount /tmp/shared as a shared volume that will be used between selenium and the test module for uploads
   docker run -d -p 4444:4444 -v /tmp/shared:/tmp/shared selenium/standalone-chromium:latest
   
   # Run the tests using the previously started Selenium instance
   mvn verify -Pui-tests-local-execution -DSELENIUM_BASE_URL=http://<server>:4444
   ```

>[!NOTE]
>
>Les fichiers journaux sont stockés dans le dossier `target/reports` de votre référentiel.
>
>Pour plus d’informations, reportez-vous au [Référentiel d’exemples de test AEM](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/README.md).
