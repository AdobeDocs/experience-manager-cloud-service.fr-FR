---
title: Utiliser les pipelines de configuration
description: Découvrez comment utiliser les pipelines de configuration pour déployer différentes configurations dans AEM as a Cloud Service, telles que les paramètres de transfert de journal, les tâches de maintenance liées à la purge et diverses configurations de réseau CDN.
feature: Operations
role: Admin
exl-id: bd121d31-811f-400b-b3b8-04cdee5fe8fa
source-git-commit: 5e0626c57f233ac3814355d7efe7db010897d72b
workflow-type: tm+mt
source-wordcount: '1378'
ht-degree: 3%

---

# Utilisation des pipelines de configuration {#config-pipelines}

Découvrez comment utiliser les pipelines de configuration pour déployer différentes configurations dans AEM as a Cloud Service, telles que les paramètres de transfert de journal, les tâches de maintenance liées à la purge et diverses configurations de réseau CDN.

## Vue d’ensemble {#overview}

Un pipeline de configuration Cloud Manager déploie des fichiers de configuration (créés au format YAML) dans un environnement cible. Plusieurs fonctionnalités d’AEM as a Cloud Service peuvent être configurées de cette manière, notamment le transfert de journal, les tâches de maintenance liées à la purge et plusieurs fonctionnalités de réseau CDN.

Pour les projets **Publication de diffusion**, les pipelines de configuration peuvent être déployés via Cloud Manager vers les types d’environnements de développement, d’évaluation et de production. Les fichiers de configuration peuvent être déployés dans des environnements de développement rapide (RDE) à l’aide de [outil de ligne de commande](/help/implementing/developing/introduction/rapid-development-environments.md#deploy-config-pipeline).

Les pipelines de configuration peuvent également être déployés via Cloud Manager pour les projets **Edge Delivery**.

Les sections suivantes de ce document donnent un aperçu des informations importantes concernant la manière dont les pipelines de configuration peuvent être utilisés et la manière dont les configurations pour ces pipelines doivent être structurées. Il décrit les concepts généraux partagés entre toutes les fonctionnalités ou un sous-ensemble des fonctionnalités prises en charge par les pipelines de configuration.

* [Configurations prises en charge](#configurations) - Liste des configurations qui peuvent être déployées avec les pipelines de configuration.
* [Créer et gérer des pipelines de configuration](#creating-and-managing) - Comment créer un pipeline de configuration
* [Syntaxe commune](#common-syntax) - Syntaxe partagée entre les configurations.
* [Structure de dossiers](#folder-structure) - Décrit la structure que les pipelines de configuration attendent pour les configurations.
* [Variables d’environnement secrètes](#secret-env-vars) - Exemples d’utilisation de variables d’environnement pour ne pas divulguer de secrets dans vos configurations.
* [Variables de pipeline secrètes](#secret-pipeline-vars) - Exemples d’utilisation de variables d’environnement pour ne pas divulguer de secrets dans vos configurations pour les projets Edge Delivery Services.

## Configurations prises en charge {#configurations}

Le tableau suivant propose une liste complète de ces configurations avec des liens vers la documentation dédiée décrivant sa syntaxe de configuration distincte et d’autres informations.

| Type | Valeur `kind` YAML | Description | Diffusion à la publication | Edge Delivery |
|---|---|---|---|---|
| [Règles de filtrage du trafic, y compris WAF](/help/security/traffic-filter-rules-including-waf.md) | `CDN` | Déclarer les règles pour bloquer le trafic malveillant | X | X |
| [Transformations de requête](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations) | `CDN` | Déclaration des règles pour transformer la forme de la demande de trafic | X | X |
| [ Transformations de réponse ](/help/implementing/dispatcher/cdn-configuring-traffic.md#response-transformations) | `CDN` | Déclaration de règles pour transformer la forme de la réponse pour une requête donnée | X | X |
| [Redirections côté serveur](/help/implementing/dispatcher/cdn-configuring-traffic.md#server-side-redirectors) | `CDN` | Déclarez les redirections côté serveur de type 301/302 | X | X |
| [Sélecteurs d’origine](/help/implementing/dispatcher/cdn-configuring-traffic.md#origin-selectors) | `CDN` | Déclarez des règles pour acheminer le trafic vers différents serveurs principaux, y compris les applications non Adobe | X | X |
| [Pages d’erreur du réseau CDN](/help/implementing/dispatcher/cdn-error-pages.md) | `CDN` | Remplacer la page d’erreur par défaut si l’origine AEM ne peut pas être atteinte, en référençant l’emplacement du contenu statique auto-hébergé dans le fichier de configuration | X |  |
| [Purge CDN](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token) | `CDN` | Déclarez les clés API de purge utilisées pour purger le réseau CDN. | X |  |
| [Jeton HTTP CDN géré par le client](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token#CDN-HTTP-value) | `CDN` | Déclarez la valeur de X-AEM-Edge-Key nécessaire pour appeler le réseau CDN Adobe à partir d’un réseau CDN client | X |  |
| [Authentification de base](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token#basic-auth) | `CDN` | Déclarez les noms d’utilisateur et mots de passe d’une boîte de dialogue d’authentification de base protégeant certaines URL. | X | X |
| [ Tâche de maintenance de purge de version ](/help/operations/maintenance.md#purge-tasks) | `MaintenanceTasks` | Optimisez le référentiel AEM en déclarant des règles relatives au moment où les versions de contenu doivent être purgées. | X |  |
| [ Tâche de maintenance de purge du journal d’audit ](/help/operations/maintenance.md#purge-tasks) | `MaintenanceTasks` | Optimisez le journal d’audit AEM pour améliorer les performances en déclarant des règles concernant le moment où les journaux doivent être purgés. | X |  |
| [Transfert de journal](/help/implementing/developing/introduction/log-forwarding.md) | `LogForwarding` | Configurez les points d’entrée et les informations d’identification pour le transfert des journaux vers diverses destinations, y compris Azure Blob Storage, Datadog, HTTPS, Elasticsearch, Splunk | X | X |
| [Enregistrement d’un ID client](/help/implementing/developing/open-api-based-apis.md) | `API` | Définissez la portée des projets d’API Adobe Developer Console sur un environnement AEM spécifique en enregistrant l’identifiant client. Nécessaire pour l’utilisation des API basées sur OpenAPI qui nécessitent une authentification | X |  |

## Créer et gérer des pipelines de configuration {#creating-and-managing}

Pour plus d’informations sur la création et la configuration des pipelines de configuration de **Publication de diffusion**, voir [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline). Lors de la création d’un pipeline de configuration dans Cloud Manager, veillez à sélectionner un **Déploiement ciblé** plutôt qu’un **Code de pile complète** lors de la configuration du pipeline. Comme indiqué précédemment, la configuration des RDE est déployée à l’aide de [outils de ligne de commande](/help/implementing/developing/introduction/rapid-development-environments.md#deploy-config-pipeline) plutôt que d’un pipeline.

Pour plus d’informations sur la création et la configuration des pipelines de configuration **Edge Delivery**, consultez l’article [Ajouter un pipeline Edge Delivery](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md).

## Syntaxe courante {#common-syntax}

Chaque fichier de configuration commence par des propriétés ressemblant à l’exemple de fragment de code suivant :

```yaml
   kind: "CDN"
   version: "1"
   metadata: ...
   data: ...
```

| Propriété | Description | Valeur par défaut |
|---|---|---|
| `kind` | Chaîne qui détermine le type de configuration, tel que le transfert de journal, les règles de filtrage du trafic ou les transformations de requête | Obligatoire, pas de valeur par défaut |
| `version` | Chaîne représentant la version du schéma | Obligatoire, pas de valeur par défaut |
| `metadata` | (Facultatif) Contient un tableau de chaînes `envTypes` qui détermine pour quels types d’environnement la configuration est traitée. Pour **Publier la diffusion** les valeurs possibles sont `dev`, `stage` et `prod`. Pour **Edge Delivery**, seule une valeur de `prod` doit être utilisée. Par exemple, si le tableau contient uniquement des `dev`, la configuration n’est pas chargée dans les environnements d’évaluation ou de production, même si elle y est déployée. | Tous les types d’environnements, c’est-à-dire (développement, évaluation, production) pour la diffusion de publication ou simplement la production pour Edge Delivery. |

Vous pouvez utiliser l’utilitaire `yq` pour valider localement la mise en forme YAML de votre fichier de configuration (par exemple, `yq cdn.yaml`).

## Diffusion à la publication {#yamls-for-aem}

Les configurations **Publier la diffusion** seront déployées dans un environnement cible. Lorsque vous ciblez plusieurs environnements, vous pouvez organiser les différents fichiers de différentes manières. Par exemple, si le tableau contient uniquement des `dev`, la configuration n’est pas chargée dans les environnements d’évaluation ou de production, même si elle y est déployée.

```yaml
   kind: "CDN"
   version: "1"
   metadata:
    envType: ["dev"]
```

### Structure des dossiers {#folder-structure}

Un dossier nommé `/config` ou similaire doit se trouver en haut de l’arborescence, avec un ou plusieurs fichiers YAML quelque part dans une arborescence sous celui-ci.

Par exemple :

```text
/config
  cdn.yaml
```

Ou

```text
/config
  /dev
    cdn.yaml
```

Les noms de dossier et de fichier sous `/config` sont arbitraires. Le fichier YAML doit toutefois inclure une valeur de propriété [`kind` valide](#configurations).

En règle générale, les configurations sont déployées dans tous les environnements. Si toutes les valeurs de propriété sont identiques pour chaque environnement, un seul fichier YAML est suffisant. Cependant, il est courant que les valeurs de propriété diffèrent d’un environnement à l’autre, par exemple lors du test d’un environnement inférieur.

Les sections suivantes illustrent quelques stratégies pour structurer vos fichiers.

### Un seul fichier de configuration pour tous les environnements {#single-file}

La structure du fichier ressemble à ce qui suit :

```text
/config
  cdn.yaml
  logForwarding.yaml
```

Utilisez cette structure lorsque la même configuration est suffisante pour tous les environnements et pour tous les types de configuration (réseau CDN, transfert de journal, etc.). Dans ce scénario, la propriété de tableau `envTypes` inclut tous les types d’environnement.

```yaml
   kind: "CDN"
   version: "1"
   metadata:
     envTypes: ["dev", "stage", "prod"]
```

En utilisant des variables d’environnement de type secret (ou pipeline), il est possible que les [propriétés secrètes](#secret-env-vars) varient selon l’environnement, comme illustré par la référence de `${{SPLUNK_TOKEN}}` suivante.

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

La structure du fichier ressemble à ce qui suit :

```text
/config
  cdn-dev.yaml
  cdn-stage.yaml
  cdn-prod.yaml
  logForwarding-dev.yaml
  logForwarding-stage.yaml
  logForwarding-prod.yaml
```

Utilisez cette structure en cas de différences dans les valeurs de propriété. Dans les fichiers , on s’attend à ce que la valeur du tableau `envTypes` corresponde au suffixe . Par exemple,`cdn-dev.yaml` et `logForwarding-dev.yaml` avec une valeur de `["dev"]`, `cdn-stage.yaml` et `logForwarding-stage.yaml` avec une valeur de `["stage"]`, etc.

### Un dossier par environnement {#folder-per-env}

Dans cette stratégie, il existe un dossier `config` distinct par environnement, avec un pipeline distinct déclaré dans Cloud Manager pour chacun.

Cette approche est particulièrement utile si vous disposez de plusieurs environnements de développement, où chacun possède des valeurs de propriété uniques.

La structure du fichier ressemble à ce qui suit :

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

## Edge Delivery Services {#yamls-for-eds}

Les pipelines de configuration d’Edge Delivery ne disposent pas d’environnements de développement, d’évaluation et de production distincts. Dans les environnements de diffusion de publication, les modifications progressent sur les niveaux de développement, d’évaluation et de production. En revanche, un pipeline de configuration Edge Delivery applique directement la configuration à tous les mappages de domaine enregistrés dans Cloud Manager pour un site Edge Delivery.


Ainsi, déployez une structure de fichiers simple telle que :

```text
/config
  cdn.yaml
  logForwarding.yaml
```

Si une règle doit être différente pour chaque site Edge Delivery, utilisez la syntaxe *quand* pour distinguer les règles les unes des autres. Par exemple, notez que le domaine correspond à dev.example.com dans le fragment de code ci-dessous, qui peut être distingué du domaine `www.example.com`.

```
kind: "CDN"
version: "1"
data:
  trafficFilters:
    rules:
    # Block simple path
    - name: block-path
      when:
        allOf:
          - reqProperty: domain
            equals: "dev.example.com"
          - reqProperty: path
            equals: '/block/me'
      action: block
```

Si vous incluez le champ de métadonnées *envTypes*, seule la valeur **prod** doit être utilisée (l’omission du champ de métadonnées envTypes est également acceptable). Pour la propriété *tier* reqProperty, seule la valeur **publish** doit être utilisée.

## Variables d’environnement secrètes {#secret-env-vars}

Pour que le stockage des informations sensibles dans le contrôle de code source ne soit pas nécessaire, les fichiers de configuration prennent en charge les variables d’environnement Cloud Manager de type **secret**. Pour certaines configurations, y compris le transfert de journal, les variables d’environnement secrètes sont obligatoires pour certaines propriétés.

Notez que les variables d’environnement secrètes sont utilisées pour les projets de diffusion de publication ; consultez la section Variables de pipeline secrètes pour les projets Edge Delivery Services.

Le fragment de code suivant illustre la manière dont la variable d’environnement secrète `${{SPLUNK_TOKEN}}` est utilisée dans la configuration.

```
kind: "LogForwarding"
version: "1"
data:
  splunk:
    default:
      enabled: true
      host: "splunk-host.example.com"
      token: "${{SPLUNK_TOKEN}}"
      index: "AEMaaCS"
```

Pour plus d’informations sur l’utilisation des variables d’environnement, voir [Variables d’environnement Cloud Manager](/help/implementing/cloud-manager/environment-variables.md).

## Variables de pipeline secrètes {#secret-pipeline-vars}

Pour les projets Edge Delivery Services, utilisez des variables de pipeline Cloud Manager de type **secret** afin que les informations sensibles ne soient pas stockées dans le contrôle de code source. La zone de sélection *Étape appliquée* doit utiliser l’option **déployer**.

La syntaxe est identique au fragment de code illustré dans la section précédente.

Pour plus d’informations sur l’utilisation des variables de pipeline, voir [Variables de pipeline dans Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md).
