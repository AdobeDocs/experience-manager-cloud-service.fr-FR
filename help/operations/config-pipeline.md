---
title: Utilisation des pipelines de configuration
description: Découvrez comment utiliser les pipelines de configuration pour déployer différentes configurations dans AEM as a Cloud Service, telles que les paramètres de transfert de journal, les tâches de maintenance liées à la purge et diverses configurations de réseau CDN.
feature: Operations
role: Admin
exl-id: bd121d31-811f-400b-b3b8-04cdee5fe8fa
source-git-commit: 4c166193ec464bb66fe00ff648c2c449ab5b3eab
workflow-type: tm+mt
source-wordcount: '1024'
ht-degree: 2%

---

# Utilisation des pipelines de configuration {#config-pipelines}

Découvrez comment utiliser les pipelines de configuration pour déployer différentes configurations dans AEM as a Cloud Service, telles que les paramètres de transfert de journal, les tâches de maintenance liées à la purge et diverses configurations de réseau CDN.

## Vue d’ensemble {#overview}

Un pipeline de configuration Cloud Manager déploie des fichiers de configuration (créés au format YAML) dans un environnement cible. Plusieurs fonctionnalités d’AEM as a Cloud Service peuvent être configurées de cette manière, notamment le transfert de journal, les tâches de maintenance liées à la purge et plusieurs fonctionnalités de réseau CDN.

Les pipelines de configuration peuvent être déployés via Cloud Manager vers les types d’environnements de développement, d’évaluation et de production. Les fichiers de configuration peuvent être déployés dans des environnements de développement rapide (RDE) à l’aide de [outil de ligne de commande](/help/implementing/developing/introduction/rapid-development-environments.md#deploy-config-pipeline).

Les sections suivantes de ce document donnent un aperçu des informations importantes concernant la manière dont les pipelines de configuration peuvent être utilisés et la manière dont les configurations pour ces pipelines doivent être structurées. Il décrit les concepts généraux partagés entre toutes les fonctionnalités ou un sous-ensemble des fonctionnalités prises en charge par les pipelines de configuration.

* [Configurations prises en charge](#configurations) - Liste des configurations qui peuvent être déployées avec les pipelines de configuration
* [Création et gestion des pipelines de configuration](#creating-and-managing) - Comment créer un pipeline de configuration.
* [Syntaxe commune](#common-syntax) - Syntaxe partagée entre les configurations
* [Structure de dossiers](#folder-structure) - Décrit la structure que les pipelines de configuration attendent pour les configurations
* [Variables d’environnement secrètes](#secret-env-vars) - Exemples d’utilisation de variables d’environnement pour ne pas divulguer de secrets dans vos configurations

## Configurations prises en charge {#configurations}

Le tableau suivant propose une liste complète de ces configurations avec des liens vers la documentation dédiée décrivant sa syntaxe de configuration distincte et d’autres informations.

| Type | Valeur `kind` YAML | Description |
|---|---|---|
| [Règles de filtrage du trafic, y compris WAF](/help/security/traffic-filter-rules-including-waf.md) | `CDN` | Déclarer les règles pour bloquer le trafic malveillant |
| [Transformations de requête](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations) | `CDN` | Déclaration des règles pour transformer la forme de la demande de trafic |
| [ Transformations de réponse ](/help/implementing/dispatcher/cdn-configuring-traffic.md#response-transformations) | `CDN` | Déclaration de règles pour transformer la forme de la réponse pour une requête donnée |
| [Redirections côté serveur](/help/implementing/dispatcher/cdn-configuring-traffic.md#server-side-redirectors) | `CDN` | Déclarez les redirections côté serveur de type 301/302 |
| [Sélecteurs d’origine](/help/implementing/dispatcher/cdn-configuring-traffic.md#origin-selectors) | `CDN` | Déclarez des règles pour acheminer le trafic vers différents serveurs principaux, y compris les applications non Adobe |
| [Pages d’erreur du réseau CDN](/help/implementing/dispatcher/cdn-error-pages.md) | `CDN` | Remplacer la page d’erreur par défaut si l’origine AEM ne peut pas être atteinte, en référençant l’emplacement du contenu statique auto-hébergé dans le fichier de configuration |
| [Purge CDN](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token) | `CDN` | Déclarez les clés API de purge utilisées pour purger le réseau CDN. |
| [Jeton HTTP CDN géré par le client](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token#CDN-HTTP-value) | `CDN` | Déclarez la valeur de X-AEM-Edge-Key nécessaire pour appeler le réseau CDN Adobe à partir d’un réseau CDN client |
| [Authentification de base](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token#basic-auth) | `CDN` | Déclarez les noms d’utilisateur et mots de passe d’une boîte de dialogue d’authentification de base protégeant certaines URL. |
| [ Tâche de maintenance de purge de version ](/help/operations/maintenance.md#purge-tasks) | `MaintenanceTasks` | Optimisez le référentiel AEM en déclarant des règles relatives au moment où les versions de contenu doivent être purgées. |
| [ Tâche de maintenance de purge du journal d’audit ](/help/operations/maintenance.md#purge-tasks) | `MaintenanceTasks` | Optimisez le journal d’audit AEM pour améliorer les performances en déclarant des règles concernant le moment où les journaux doivent être purgés. |
| [Transfert de journal](/help/implementing/developing/introduction/log-forwarding.md) | `LogForwarding` | Configurez les points d’entrée et les informations d’identification pour le transfert des journaux vers diverses destinations, y compris Azure Blob Storage, Datadog, HTTPS, Elasticsearch, Splunk |
| [Enregistrement d’un ID client](/help/implementing/developing/open-api-based-apis.md) | `API` | Étendue des projets d’API Adobe Developer Console à des environnements AEM spécifiques en enregistrant l’identifiant client. Cela est nécessaire pour l’utilisation des API basées sur OpenAPI qui nécessitent une authentification |

## Création et gestion des pipelines de configuration {#creating-and-managing}

Pour plus d’informations sur la création et la configuration des pipelines, voir [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline).

Lors de la création d’un pipeline de configuration dans Cloud Manager, veillez à sélectionner un **Déploiement ciblé** plutôt qu’un **Code de pile complète** lors de la configuration du pipeline.

Comme indiqué précédemment, la configuration des RDE est déployée à l’aide de [outils de ligne de commande](/help/implementing/developing/introduction/rapid-development-environments.md#deploy-config-pipeline) plutôt que d’un pipeline.


## Syntaxe courante {#common-syntax}

Chaque fichier de configuration commence par des propriétés ressemblant à l’exemple de fragment de code suivant :

```yaml
  kind: "LogForwarding"
  version: "1"
  metadata:
    envTypes: ["dev"]
```

| Propriété | Description | Valeur par défaut |
|---|---|---|
| `kind` | Chaîne qui détermine le type de configuration, tel que le transfert de journal, les règles de filtrage du trafic ou les transformations de requête | Obligatoire, pas de valeur par défaut |
| `version` | Chaîne représentant la version du schéma | Obligatoire, pas de valeur par défaut |
| `envTypes` | Ce tableau de chaînes est une propriété enfant du nœud `metadata`. Les valeurs possibles sont dev, stage, prod ou toute combinaison de ces éléments. Elle détermine pour quels types d’environnement la configuration sera traitée. Par exemple, si le tableau contient uniquement des `dev`, la configuration n’est pas chargée dans les environnements d’évaluation ou de production, même si elle y est déployée. | Tous les types d’environnements (développement, évaluation, production) |

Vous pouvez utiliser l’utilitaire `yq` pour valider localement la mise en forme YAML de votre fichier de configuration (par exemple, `yq cdn.yaml`).

## Structure de dossiers {#folder-structure}

Un dossier nommé `/config` ou similaire doit se trouver en haut de l’arborescence, avec un ou plusieurs fichiers YAML quelque part dans une arborescence sous celui-ci.

Par exemple :

```text
/config
  cdn.yaml
```

ou

```text
/config
  /dev
    cdn.yaml
```

Les noms de dossier et de fichier sous `/config` sont arbitraires. Le fichier YAML doit toutefois inclure une valeur de propriété [`kind` valide](#configurations).

En règle générale, les configurations sont déployées dans tous les environnements. Si toutes les valeurs de propriété sont identiques pour chaque environnement, un seul fichier YAML suffira. Cependant, il est courant que les valeurs de propriété diffèrent d’un environnement à l’autre, par exemple lors du test d’un environnement inférieur.

Les sections suivantes illustrent quelques stratégies pour structurer vos fichiers.

### Un seul fichier de configuration pour tous les environnements {#single-file}

La structure du fichier ressemblera à ce qui suit :

```text
/config
  cdn.yaml
  logForwarding.yaml
```

Utilisez cette structure lorsque la même configuration est suffisante pour tous les environnements et pour tous les types de configuration (réseau CDN, transfert de journal, etc.). Dans ce scénario, la propriété de tableau `envTypes` inclut tous les types d’environnement.

```yaml
   kind: "cdn"
   version: "1"
   metadata:
     envTypes: ["dev", "stage", "prod"]
```

En utilisant des variables d’environnement de type secret, il est possible que les [propriétés secrètes](#secret-env-vars) varient selon l’environnement, comme illustré par la référence `${{SPLUNK_TOKEN}}`

```yaml
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  splunk:
    default:
      enabled: true
      host: "splunk-host.example.com"
      token: "${{SPLUNK_TOKEN}}"
      index: "AEMaaCS"
```

### Un Fichier Distinct Par Type D’Environnement {#file-per-env}

La structure du fichier ressemblera à ce qui suit :

```text
/config
  cdn-dev.yaml
  cdn-stage.yaml
  cdn-prod.yaml
  logForwarding-dev.yaml
  logForwarding-stage.yaml
  logForwarding-prod.yaml
```

Utilisez cette structure en cas de différences dans les valeurs de propriété. Dans les fichiers , on s’attend à ce que la valeur du tableau `envTypes` corresponde au suffixe , par exemple
`cdn-dev.yaml` et `logForwarding-dev.yaml` avec une valeur de `["dev"]`, `cdn-stage.yaml` et `logForwarding-stage.yaml` avec une valeur de `["stage"]`, etc.

### Un Dossier Par Environnement {#folder-per-env}

Dans cette stratégie, il existe un dossier `config` distinct par environnement, avec un pipeline distinct déclaré dans Cloud Manager pour chacun.

Cette approche est particulièrement utile si vous disposez de plusieurs environnements de développement, où chacun possède des valeurs de propriété uniques.

La structure du fichier ressemblera à ce qui suit :

```text
/config/dev1
  cdn.yaml
  logForwarding.yaml
/config/dev2
  cdn.yaml
  logForwarding.yaml
/config/prod  
  cdn.yaml
  logForwarding.yaml
```

Une variante de cette approche consiste à conserver une branche distincte par environnement.

## Variables d’environnement secrètes {#secret-env-vars}

Pour que le stockage des informations sensibles dans le contrôle de code source ne soit pas nécessaire, les fichiers de configuration prennent en charge les variables d’environnement Cloud Manager de type **secret**. Pour certaines configurations, y compris le transfert de journal, les variables d’environnement secrètes sont obligatoires pour certaines propriétés.

Le fragment de code ci-dessous est un exemple de la manière dont la variable d’environnement secrète `${{SPLUNK_TOKEN}}` est utilisée dans la configuration.

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  splunk:
    default:
      enabled: true
      host: "splunk-host.example.com"
      token: "${{SPLUNK_TOKEN}}"
      index: "AEMaaCS"
```

Consultez le document [Variables d’environnement Cloud Manager](/help/implementing/cloud-manager/environment-variables.md) pour plus d’informations sur l’utilisation des variables d’environnement.
