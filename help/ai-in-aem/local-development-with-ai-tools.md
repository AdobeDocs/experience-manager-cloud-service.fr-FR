---
title: Développement local avec les outils d’IA
description: Découvrez comment configurer des outils de codage d’IA avec le contexte du projet, les compétences des agents et les serveurs MCP pour accélérer le développement d’AEM as a Cloud Service.
feature: Developing
role: Developer
exl-id: 09d6257d-36ad-49e5-831f-c44b356f1800
source-git-commit: 6fe463cb3f350f84e3853950e667eac851f672ef
workflow-type: tm+mt
source-wordcount: '1623'
ht-degree: 0%

---

# Développement local avec les outils d’IA {#local-development-with-ai-tools}

>[!NOTE]
>
>Cet article se concentre sur le développement local avec les outils d’IA pour le développement de **pile Java**. Pour Edge Delivery Services, voir [Développement à l’aide d’outils d’IA](https://www.aem.live/developer/ai-coding-agents).

Les agents de codage d’IA (Claude Code, Cursor, GitHub Copilot et outils similaires) disposent d’une connaissance approfondie des technologies sous-jacentes d’AEM (Java, OSGi, Sling, JCR, HTL), mais ne connaissent pas nécessairement les bonnes pratiques pour générer le code et la configuration, ni comment déboguer les problèmes de développement courants d’AEM.

Quatre composantes complémentaires abordent ce problème :

| Composant | Objectif |
|---|---|
| **AGENTS.md** | Fichier de contexte spécifique au projet qui fonde l’IA dans votre projet AEM Cloud Service pour chaque session |
| **Compétences agent** | Jeux d’instructions réutilisables pour les tâches de développement récurrentes telles que la création de composants et la configuration de Dispatcher |
| **Serveur MCP local Quickstart** | Expose les données d’exécution en direct d’une instance AEM SDK locale pour prendre en charge le dépannage |
| **Serveur MCP local** | Permet la validation et le contrôle au moment de l’exécution d’une instance Dispatcher locale |

Consultez les [tutoriels de développement assisté par l’IA](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/ai/ai-assisted-development/overview) pour obtenir des instructions pratiques supplémentaires.

>[!NOTE]
>
> Les serveurs MCP distants d’AEM Cloud Service sont également utiles au développement local, mais ne sont pas abordés dans cet article. Pour en savoir plus à ce sujet, consultez l’article [ Utilisation de MCP avec Cloud Service ](/help/ai-in-aem/mcp-support/using-mcp-with-aem-as-a-cloud-service.md).

## AGENTS.md {#agentsmd}

`AGENTS.md` fichier Markdown se trouve à la racine de votre projet AEM et est chargé automatiquement par les outils de codage de l’IA au début de chaque session afin de reposer sur l’expertise essentielle du domaine Java-stack AEM Cloud Service (et non sur d’autres solutions AEM telles qu’AEM 6.5 ou Edge Delivery Services).

`AGENTS.md` n’est pas un fichier statique que vous copiez : il est généré par les compétences `ensure-agents-md` décrites dans la section suivante. Cette compétence lit votre `pom.xml` pour résoudre le nom du projet, découvrir des modules et détecter les modules complémentaires installés, afin de produire un fichier adapté à votre projet spécifique.

>[!NOTE]
>
>Une fois qu’`AGENTS.md` existe à la racine du projet, la compétence `ensure-agents-md` n’est plus exécutée. Modifiez directement le fichier si la structure de votre projet change.

## Compétences de l’agent {#agent-skills}

Les compétences sont des ensembles d’instructions qui codent des workflows de développement à plusieurs étapes. Lorsqu’elle est invoquée, l’IA suit la procédure de la compétence plutôt que de se fier uniquement aux connaissances générales, produisant des résultats cohérents et conformes à la convention.

Adobe publie les compétences AEM as a Cloud Service dans le référentiel **[adobe/skills](https://github.com/adobe/skills/tree/main/plugins/aem/cloud-service)** :

| Compétence | Objectif |
|---|---|
| `ensure-agents-md` | Bootstraps `AGENTS.md` et `CLAUDE.md` adapté à la structure réelle du module du projet |
| `create-component` | Génère un modèle automatique pour un composant AEM complet : définition de composant, code XML de boîte de dialogue, modèle HTL, modèle Sling, tests unitaires et bibliothèques clientes |
| `dispatcher` | Assistant de configuration Dispatcher et Apache HTTPD optimisés par l’IA et couvrant la création de configuration, les conseils techniques, la réponse aux incidents, l’optimisation des performances et le renforcement de la sécurité |
| `workflow` | Point d’entrée unique pour toutes les compétences de workflow AEM as a Cloud Service. Il y est question de la conception de modèle de workflow, du développement d’étapes de processus personnalisées et du programme de sélection des participants, de la configuration du lanceur, du déclenchement de workflow et de la prise en charge de la production, notamment le débogage des workflows bloqués/en échec, le tri des incidents avec les journaux Cloud Manager, l’analyse du pool de threads et les diagnostics de tâche Sling pour le moteur de workflow Granite. |

### Installation des compétences {#install-skills}

Sélectionnez la méthode qui correspond à votre outil de codage d’IA. L’installation des compétences les rend disponibles pour tous les projets sur cette machine. Voir le [tutoriel Configuration des compétences de l’agent AEM](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/ai/ai-assisted-development/setup/agent-skills) pour une présentation concrète.

#### Claude Code {#claude-code}

```bash
# Add the Adobe Skills marketplace (one-time setup)
/plugin marketplace add adobe/skills

# Install all available skills
/plugin install aem-cloud-service@adobe-skills
```

#### Compétences Npx {#npx-skills}

```bash
# Install all available skills
npx skills add https://github.com/adobe/skills/tree/main/skills/aem/cloud-service --all
```

#### Compétences supérieures (extension de ligne de commande GitHub) {#upskill-github-cli-extension}

```bash
# Install the gh-upskill extension (one-time setup)
gh extension install ai-ecoverse/gh-upskill

# Install all available skills
gh upskill adobe/skills --path skills/aem/cloud-service --all
```

### Utiliser la compétence ensure-agents-md {#use-the-ensure-agents-md-skill}

Après avoir installé la compétence, ouvrez votre assistant d’IA dans tout projet AEM Cloud Service qui n’a pas encore de `AGENTS.md`. La compétence s’exécute automatiquement avant le traitement de votre première requête, créant les deux fichiers à la racine du projet sans nécessiter d’appel explicite.

### Utilisation de la compétence create-component {#use-the-create-component-skill}

Lors de la première utilisation, la compétence détecte automatiquement les `project`, les `package` et les `group` des composants `pom.xml` et existants, vous demande de confirmer les valeurs détectées, puis crée des `.aem-skills-config.yaml` à la racine du projet. Aucune configuration manuelle n’est nécessaire avant la première utilisation.

Si vous préférez pré-créer le fichier, placez `.aem-skills-config.yaml` à la racine du projet avec la structure suivante :

```yaml
configured: true

project: "wknd"                                    # Check /apps/{project}/ or pom.xml
package: "com.adobe.aem.guides.wknd.core"          # Check core/pom.xml
group: "WKND Components"                           # Check existing component .content.xml files
```

Le fichier se trouve en dehors du répertoire des compétences et n’est jamais remplacé lorsque la compétence est mise à jour.

Décrivez le composant dans votre conversation avec l’IA :

```
Create an AEM component called "Hero Banner"

Dialog specification:
Title (title) - Textfield, mandatory
Subtitle (subtitle) - Textfield
Background Image (backgroundImage) - Fileupload
CTA Text (ctaText) - Textfield
CTA Link (ctaLink) - Pathfield
```

L’agent fait écho à la spécification du champ pour confirmation, puis génère tous les fichiers de composant. Les modèles pris en charge comprennent les champs multiples avec des éléments imbriqués composites, la logique d’affichage/masquage conditionnel, l’extension des composants principaux via Sling Resource Merger et les tests JUnit 5 à l’aide de simulations AEM. La conception peut provenir de diverses sources, y compris une description textuelle, une image ou une URL de conception Figma utilisant le serveur MCP de Figma.

Pour en savoir plus, suivez le tutoriel [ Développement de composants à l’aide des compétences de l’agent AEM ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/ai/ai-assisted-development/use-cases/component-development).

### Utilisation des compétences Dispatcher {#use-the-dispatcher-skill}

Appelez les compétences du Dispatcher pour toute tâche de configuration Dispatcher ou Apache HTTPD. Les compétences acheminent les requêtes vers l’une des six sous-compétences spécialisées selon la nature de la requête :

| Sous-compétence | Objectif |
|---|---|
| `workflow-orchestrator` | Travail de bout en bout couvrant la conception, les modifications de configuration, la validation et le suivi |
| `config-authoring` | Modifications concrètes de la configuration : filtres, règles de cache, réécritures, hôtes virtuels, en-têtes et fermes |
| `technical-advisory` | Conseils conceptuels, explication de politique et recommandations basées sur des citations |
| `incident-response` | Échecs d’exécution, anomalies du cache et régressions |
| `performance-tuning` | Efficacité du cache, latence et optimisation du débit |
| `security-hardening` | Examen de l’exposition et renforcement de la production |

Pour les requêtes générales ou de première utilisation, commencez par la sous-compétence `workflow-orchestrator`. Pour un travail ciblé, décrivez le problème spécifique et les parcours d’acquisition des compétences au spécialiste approprié.

Les compétences du Dispatcher permettent de gérer l’orchestration et les conseils. Le serveur Dispatcher MCP, décrit ci-dessous, fournit les sept outils de validation et d’exécution que la compétence utilise lorsqu’elle a besoin de preuves locales.

## Serveur MCP Quickstart AEM {#aem-quickstart-mcp-server}

Le protocole MCP (Model Context Protocol) est une norme ouverte qui permet aux outils de codage de l’IA de se connecter à des sources de données et à des services externes. Le serveur AEM Quickstart MCP est un package de contenu qui, une fois installé dans une instance AEM SDK locale, expose directement les données d’exécution aux outils d’IA connectés. Les agents peuvent ainsi récupérer les journaux, diagnostiquer les échecs OSGi et inspecter le traitement des demandes sans quitter l’IDE.

### Installation du package de contenu {#install-the-content-package}

Téléchargez le package de contenu à partir du [Portail de distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?fulltext=mcp*&1_group.propertyvalues.property=.%2Fjcr%3Acontent%2Fmetadata%2Fdc%3AsoftwareType&1_group.propertyvalues.operation=equals&1_group.propertyvalues.0_values=software-type%3Atooling&orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&orderby.sort=desc&layout=list&p.offset=0&p.limit=3) et installez-`com.adobe.aem:com.adobe.aem.mcp-server-contribs-content` dans votre démarrage rapide local à l’aide du gestionnaire de packages sur `/crx/packmgr`.

**Compatibilité :** validée avec AEM SDK `2026.2.24678.20260226T154829Z-260200` et version ultérieure.

### Outils disponibles {#available-tools}

| Outil | Description |
|---|---|
| `aem-logs` | Récupère les entrées du journal AEM et OSGi, filtrables par modèle RegEx, niveau de journal et nombre d’entrées |
| `diagnose-osgi-bundle` | Diagnostique les raisons pour lesquelles un lot ou un composant DS ne démarre pas ; signale les packages manquants, les références non satisfaites et les problèmes de configuration. |
| `recent-requests` | Renvoie les requêtes HTTP récentes avec la trace de traitement interne complète de Sling (résolution de ressource, résolution de script, chaîne de filtres), filtrable par expression régulière de chemin d’accès |

### Configuration de votre IDE {#configure-your-ide}

#### Curseur {#cursor}

Dans les paramètres du curseur, ajoutez un nouveau serveur MCP personnalisé :

```json
"aem-cs-sdk": {
  "type": "streamable-http",
  "url": "http://localhost:4502/bin/mcp",
  "headers": {
    "Authorization": "Basic YWRtaW46YWRtaW4="
  }
}
```

#### Copilote GitHub avec IntelliJ IDEA {#github-copilot-with-ihtellij-idea}

Accédez à **Outils > Copilote GitHub > Modèle de protocole contextuel (MCP)** puis cliquez sur **Configurer**. Ajouter :

```json
"aem-cs-sdk": {
  "url": "http://localhost:4502/bin/mcp",
  "requestInit": {
    "headers": {
      "Authorization": "Basic YWRtaW46YWRtaW4="
    }
  }
}
```

#### Autres IDE {#other-ides}

Tout client MCP peut se connecter en pointant vers `http://localhost:4502/bin/mcp` avec un en-tête `Authorization: Basic YWRtaW46YWRtaW4=`. Configurez des en-têtes personnalisés à l’aide des paramètres MCP de votre IDE.

>[!NOTE]
>
>La valeur `Basic YWRtaW46YWRtaW4=` est le codage Base64 de `admin:admin`, les informations d’identification par défaut pour un démarrage rapide local. Ne l’utilisez pas avec des environnements non locaux.

## Serveur MCP Dispatcher {#dispatcher-mcp-server}

>[!IMPORTANT]
>
>Cette fonctionnalité est **version bêta**. L’accès anticipé aux fonctionnalités développées par Adobe permet aux clients et aux partenaires de faire part de leurs commentaires (par e-mail [aemcs-ai-ide-tools-feedback@adobe.com](mailto:aemcs-ai-ide-tools-feedback@adobe.com)) et de façonner le développement des produits. Cela les aide également à se préparer à adopter de nouvelles fonctionnalités avant leur disponibilité générale.
>
>Les versions de Beta peuvent contenir des défauts et sont fournies « EN L’ÉTAT » sans garantie d’aucune sorte. Adobe n’a aucune obligation de tenir à jour, corriger, mettre à jour, modifier, remplacer ou prendre en charge (par le biais des services d’assistance Adobe ou d’une autre manière) les versions bêta. Adobe conseille aux clients d’être prudent et de ne pas se fier au bon fonctionnement ou aux performances des versions bêta, ni à la documentation ou aux documents d’accompagnement. Les fonctionnalités et API de la version bêta peuvent être modifiées sans préavis. Par conséquent, toute utilisation des versions bêta s’effectue entièrement aux risques et périls du client.

Le serveur Dispatcher MCP est fourni avec AEM Dispatcher SDK. Il permet aux outils d’IA de valider la configuration Dispatcher et Apache HTTPD, de suivre la gestion des requêtes et d’inspecter le comportement du cache par rapport à une instance Dispatcher s’exécutant localement dans Docker.

Contrairement aux compétences du Dispatcher, le serveur MCP Dispatcher n’expose que les outils suivants : sept outils MCP et aucune invite ni ressource.

### Conditions préalables {#prerequisites}

- Docker Desktop 4.x ou version ultérieure, installé et en cours d’exécution
- AEM Dispatcher SDK téléchargé à partir du [portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?fulltext=mcp*&1_group.propertyvalues.property=.%2Fjcr%3Acontent%2Fmetadata%2Fdc%3AsoftwareType&1_group.propertyvalues.operation=equals&1_group.propertyvalues.0_values=software-type%3Atooling&orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&orderby.sort=desc&layout=list&p.offset=0&p.limit=3)

>[!NOTE]
>
>Si vous voyez `client version 1.43 is too new`, `DOCKER_API_VERSION=1.41` dans votre shell ou dans `mcp.json`.

### Installation du SDK Dispatcher {#install-the-dispatcher-sdk}

**macOS et Linux:**

```bash
chmod +x aem-sdk-dispatcher-tools-<version>-unix.sh
./aem-sdk-dispatcher-tools-<version>-unix.sh
cd dispatcher-sdk-<version>
chmod +x ./bin/docker_run_mcp.sh
./bin/docker_run_mcp.sh test
```

**Windows:**

```powershell
Expand-Archive aem-sdk-dispatcher-tools-<version>-windows.zip
```

Exécutez `./bin/docker_run_mcp.sh help` pour récupérer la configuration de l’IDE de copier-coller et `./bin/docker_run_mcp.sh version` pour confirmer la version MCP et SDK groupées. Utilisez `./bin/docker_run_mcp.sh diagnose` pour examiner les problèmes de connectivité.

### Configurer le curseur {#configure-cursor}

Ajoutez une entrée `aem-dispatcher-mcp` à `~/.cursor/mcp.json` :

```json
{
  "mcpServers": {
    "aem-dispatcher-mcp": {
      "command": "<path_to_dispatcher_sdk>/bin/docker_run_mcp.sh",
      "env": {
        "DOCKER_API_VERSION": "1.43",
        "AEM_DEPLOYMENT_MODE": "cloud",
        "MCP_LOG_LEVEL": "trace",
        "MCP_LOG_FILE": "/tmp/dispatcher-mcp.log",
        "DISPATCHER_CONFIG_PATH": "<path_to_dispatcher_src>"
      }
    }
  }
}
```

Remplacez `<path_to_dispatcher_sdk>` par l’emplacement du SDK Dispatcher extrait et `<path_to_dispatcher_src>` par le répertoire de `src` du Dispatcher du projet. Définissez `DISPATCHER_CONFIG_PATH` sur la racine de configuration qui inclut les fichiers dans lesquels `/docroot` est défini. `MCP_LOG_LEVEL` et `MCP_LOG_FILE` sont des paramètres de débogage facultatifs. Si vous voyez `client version 1.43 is too new`, définissez `DOCKER_API_VERSION` sur `1.41`. Si d’autres serveurs MCP sont déjà configurés, ajoutez l’entrée `aem-dispatcher-mcp` sans les remplacer. Redémarrez le curseur après l&#39;enregistrement.

D’autres IDE peuvent être configurés de la même manière. Le `docs/DispatcherMCP.md` SDK comprend des exemples complets pour Claude Desktop et VS Code.

### Outils disponibles {#available-tools-dispatcher}

| Outil | Description |
|---|---|
| `validate` | Valide les configurations Dispatcher et Apache HTTPD |
| `lint` | Exécute des contrôles statiques prenant en compte le mode et des analyses de bonnes pratiques. |
| `sdk` | Exécute les workflows Dispatcher SDK : `validate`, `validate-full`, `three-phase-validate`, `docker-test`, `check-files`, `diff-baseline` |
| `trace_request` | Trace le comportement des requêtes avec les preuves d’exécution |
| `inspect_cache` | Inspecte le comportement du cache et du docroot pour une URL cible |
| `monitor_metrics` | Lit les mesures d’exécution des journaux Dispatcher et HTTPD |
| `tail_logs` | Consigne en détail les journaux d’exécution Dispatcher et HTTPD pertinents |

La surface MCP n’expose intentionnellement que ces sept outils ; les invites et les ressources restent dans la couche de compétences. La documentation de référence complète est disponible en `docs/DispatcherMCP.md` dans le SDK Dispatcher extrait.
