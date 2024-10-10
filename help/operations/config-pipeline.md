---
title: Utilisation des pipelines de configuration
description: Découvrez comment utiliser les pipelines de configuration pour déployer différentes configurations dans AEM as a Cloud Service, telles que les paramètres de transfert de journal, les tâches de maintenance liées à la purge et diverses configurations du réseau de diffusion de contenu.
feature: Operations
role: Admin
exl-id: bd121d31-811f-400b-b3b8-04cdee5fe8fa
source-git-commit: 3d0abce117cf94d7bf521e78be2ec019f216aa08
workflow-type: tm+mt
source-wordcount: '973'
ht-degree: 2%

---

# Utilisation des pipelines de configuration {#config-pipelines}

Découvrez comment utiliser les pipelines de configuration pour déployer différentes configurations dans AEM as a Cloud Service, telles que les paramètres de transfert de journal, les tâches de maintenance liées à la purge et diverses configurations du réseau de diffusion de contenu.

## Vue d’ensemble {#overview}

Un pipeline de configuration Cloud Manager déploie les fichiers de configuration (créés au format YAML) dans un environnement cible. Un certain nombre de fonctionnalités d’AEM as a Cloud Service peuvent être configurées de cette manière, notamment le transfert de journal, les tâches de maintenance liées à la purge et plusieurs fonctionnalités de réseau de diffusion de contenu.

Les pipelines de configuration peuvent être déployés via Cloud Manager pour les types d’environnements de développement, d’évaluation et de production dans les programmes de production (hors environnements de test). Les RDE ne sont pas pris en charge.

Les sections suivantes de ce document donnent un aperçu d’informations importantes concernant la manière dont les pipelines de configuration peuvent être utilisés et la manière dont les configurations doivent être structurées. Il décrit les concepts généraux partagés sur l’ensemble ou un sous-ensemble des fonctionnalités prises en charge par les pipelines de configuration.

* [Configurations prises en charge](#configurations) - Liste des configurations qui peuvent être déployées avec les pipelines de configuration
* [Création et gestion des pipelines de configuration](#creating-and-managing) - Comment créer un pipeline de configuration.
* [Syntaxe commune](#common-syntax) - Syntaxe partagée entre les configurations
* [Structure de dossiers](#folder-structure) - Décrit la structure attendue des pipelines de configuration pour les configurations
* [Variables d’environnement secrètes](#secret-env-vars) - Exemples d’utilisation de variables d’environnement pour ne pas divulguer de secrets dans vos configurations

## Configurations prises en charge {#configurations}

Le tableau suivant propose une liste complète de ces configurations avec des liens vers une documentation dédiée décrivant sa syntaxe de configuration distincte et d’autres informations.

| Type | Valeur `kind` YAML | Description |
|---|---|---|
| [Règles de filtre de trafic, y compris WAF](/help/security/traffic-filter-rules-including-waf.md) | `CDN` | Déclarer des règles pour bloquer le trafic malveillant |
| [Transformations de requête](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations) | `CDN` | Déclarer des règles pour transformer la forme de la requête de trafic |
| [Transformations de réponse](/help/implementing/dispatcher/cdn-configuring-traffic.md#response-transformations) | `CDN` | Déclarer des règles pour transformer la forme de la réponse pour une requête donnée |
| [Redirections côté client](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors) | `CDN` | Déclarer les redirections côté client de type 301/302 |
| [Sélecteurs d’origine](/help/implementing/dispatcher/cdn-configuring-traffic.md#origin-selectors) | `CDN` | Déclarez des règles pour acheminer le trafic vers différents serveurs principaux, y compris les applications non Adobes. |
| [Pages d’erreur CDN](/help/implementing/dispatcher/cdn-error-pages.md) | `CDN` | Remplacez la page d’erreur par défaut si AEM’origine ne peut pas être atteinte, en référençant l’emplacement du contenu statique auto-hébergé dans le fichier de configuration. |
| [Purge CDN](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token) | `CDN` | Déclarez les clés d’API de purge utilisées pour purger le réseau CDN |
| [Jeton HTTP CDN géré par le client](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token#CDN-HTTP-value) | `CDN` | Déclarez la valeur de X-AEM-Edge-Key nécessaire pour appeler le CDN Adobe à partir d’un CDN client |
| [Authentification de base](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token#basic-auth) | `CDN` | Déclarez les noms d’utilisateur et les mots de passe pour une boîte de dialogue d’authentification de base protégeant certaines URL [ (disponible uniquement pour les utilisateurs adopteurs précoces)](/help/release-notes/release-notes-cloud/release-notes-current.md#foundation-early-adopter) |
| [Tâche de maintenance de purge de version](/help/operations/maintenance.md#purge-tasks) | `MaintenanceTasks` | Optimisez le référentiel AEM en déclarant les règles autour du moment où les versions de contenu doivent être purgées. |
| [ Tâche de maintenance de purge du journal d’audit ](/help/operations/maintenance.md#purge-tasks) | `MaintenanceTasks` | Optimiser le journal d’audit AEM pour des performances accrues en déclarant des règles sur le moment où les journaux doivent être purgés |
| [Transfert de journal](/help/implementing/developing/introduction/log-forwarding.md) | `LogForwarding` | Pas encore disponible : configurez les points de terminaison et les informations d’identification pour le transfert des journaux vers diverses destinations (par exemple, Splunk, Datadog, HTTPS). |

## Création et gestion des pipelines de configuration {#creating-and-managing}

Pour plus d’informations sur la création et la configuration des pipelines, voir le document [Pipelines CI/CD.](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline)

Lors de la création d’un pipeline de configuration dans Cloud Manager, veillez à sélectionner un **déploiement ciblé** plutôt que le **code de pile complet** lors de la configuration du pipeline.

## Syntaxe commune {#common-syntax}

Chaque fichier de configuration commence par des propriétés qui ressemblent à l’exemple de fragment de code suivant :

```yaml
  kind: "LogForwarding"
  version: "1"
  metadata:
    envTypes: ["dev"]
```

| Propriété | Description | Valeur par défaut |
|---|---|---|
| `kind` | Chaîne qui détermine le type de configuration, par exemple le transfert de journal, les règles de filtrage du trafic ou les transformations de requêtes. | Obligatoire, pas de valeur par défaut |
| `version` | Chaîne représentant la version du schéma | Obligatoire, pas de valeur par défaut |
| `envTypes` | Ce tableau de chaînes est une propriété enfant du noeud `metadata`. Les valeurs possibles sont dev, stage, prod ou toute combinaison. Il détermine les types d’environnement pour lesquels la configuration sera traitée. Par exemple, si le tableau comprend uniquement `dev`, la configuration ne sera pas chargée dans les environnements intermédiaire ou prod, même si la configuration y est déployée. | Tous les types d’environnement (développement, évaluation, production) |

Vous pouvez utiliser l’utilitaire `yq` pour valider localement la mise en forme YAML de votre fichier de configuration (par exemple, `yq cdn.yaml`).

## Structure de dossiers {#folder-structure}

Un dossier nommé `/config` ou similaire doit se trouver en haut de l’arborescence, avec un fichier YAML supplémentaire quelque part dans une arborescence en dessous.

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

Les noms de dossiers et de fichiers sous `/config` sont arbitraires. Cependant, le fichier YAML doit inclure une valeur de propriété [`kind` valide.](#configurations)

En règle générale, les configurations sont déployées dans tous les environnements. Si toutes les valeurs de propriété sont identiques pour chaque environnement, un seul fichier YAML suffit. Cependant, il est courant que les valeurs de propriété diffèrent d’un environnement à l’autre, par exemple lors du test d’un environnement plus faible.

Les sections suivantes illustrent certaines stratégies de structuration des fichiers.

### Un seul fichier de configuration pour tous les environnements {#single-file}

La structure du fichier ressemblera à ce qui suit :

```text
/config
  cdn.yaml
  logForwarding.yaml
```

Utilisez cette structure lorsque la même configuration est suffisante pour tous les environnements et pour tous les types de configuration (CDN, transfert de logs, etc.). Dans ce scénario, la propriété de tableau `envTypes` inclurait tous les types d’environnements.

```yaml
   kind: "cdn"
   version: "1"
   metadata:
     envTypes: ["dev", "stage", "prod"]
```

À l’aide de variables d’environnement de type secret, il est possible que [propriétés secrètes](#secret-env-vars) varie par environnement, comme illustré par la référence `${{SPLUNK_TOKEN}}`

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

### Un fichier distinct par type d’environnement {#file-per-env}

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

Utilisez cette structure lorsqu’il peut y avoir des différences dans les valeurs de propriété. Dans les fichiers, on s’attend à ce que la valeur du tableau `envTypes` corresponde au suffixe, par exemple
`cdn-dev.yaml` et `logForwarding-dev.yaml` avec une valeur de `["dev"]`, `cdn-stage.yaml` et `logForwarding-stage.yaml` avec une valeur de `["stage"]`, etc.

### Un dossier par environnement {#folder-per-env}

Dans cette stratégie, il existe un dossier `config` distinct par environnement, avec un pipeline distinct déclaré dans Cloud Manager pour chacun d’eux.

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

Pour que les informations sensibles n’aient pas besoin d’être stockées dans le contrôle de code source, les fichiers de configuration prennent en charge les variables d’environnement Cloud Manager de type **secret**. Pour certaines configurations, y compris le transfert des logs, les variables d’environnement secrètes sont obligatoires pour certaines propriétés.

Le fragment de code ci-dessous est un exemple d’utilisation de la variable d’environnement secrète `${{SPLUNK_TOKEN}}` dans la configuration.

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

Pour plus d’informations sur l’utilisation des variables d’environnement, voir le document [Variables d’environnement Cloud Manager](/help/implementing/cloud-manager/environment-variables.md) .
