---
title: Transfert de journal pour AEM as a Cloud Service
description: En savoir plus sur le transfert des journaux vers les fournisseurs de journalisation dans AEM as a Cloud Service
exl-id: 27cdf2e7-192d-4cb2-be7f-8991a72f606d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: f6de6b6636d171b6ab08fdf432249b52c2318c45
workflow-type: tm+mt
source-wordcount: '1781'
ht-degree: 1%

---

# Transfert de journaux {#log-forwarding}

>[!NOTE]
>
>Le transfert de journal est désormais configuré en libre-service, à la différence de la méthode héritée, qui nécessitait l’envoi d’un ticket d’assistance à l’Adobe. Consultez la section [Migration](#legacy-migration) si le transfert de journal a été configuré par Adobe.

Les clients disposant d’une licence avec un fournisseur de journalisation ou hébergeant un produit de journalisation peuvent avoir AEM journaux (y compris Apache/Dispatcher) et des journaux CDN transférés vers la destination de journalisation associée. AEM as a Cloud Service prend en charge les destinations de journalisation suivantes :

* Stockage Azure Blob
* Datadog
* Elasticsearch ou OpenSearch
* HTTPS
* Splunk

Le transfert de journal est configuré en libre-service en déclarant une configuration dans Git et en la déployant via le pipeline de configuration Cloud Manager vers les types d’environnements de production (hors environnements de test), de développement, d’évaluation et de production RDE.

Il existe une option pour que les journaux d’AEM et Apache/Dispatcher soient acheminés par le biais d’AEM infrastructure de mise en réseau avancée, telle qu’une adresse IP de sortie dédiée.

Notez que la bande passante réseau associée aux journaux envoyés à la destination de journalisation est considérée comme faisant partie de l’utilisation des E/S réseau de votre entreprise.


## Organisation de cet article {#how-organized}

Cet article est organisé de la manière suivante :

* Configuration : commune à toutes les destinations de journalisation
* Configurations de destination de journalisation : chaque destination a un format légèrement différent.
* Formats de saisie de journal - informations sur les formats de saisie de journal
* Mise en réseau avancée : envoi de journaux AEM et Apache/Dispatcher via une sortie dédiée ou via un VPN
* Migration à partir du transfert de journal hérité : comment passer du transfert de journal précédemment configuré par Adobe à l’approche en libre-service


## Configuration {#setup}

1. Créez un fichier nommé `logForwarding.yaml`. Il doit contenir des métadonnées, comme décrit dans l’ [article du pipeline de configuration](/help/operations/config-pipeline.md#common-syntax) (**type** doit être défini sur `LogForwarding` et la version définie sur &quot;1&quot;), avec une configuration similaire à la suivante (nous utilisons Splunk comme exemple).

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

1. Placez le fichier quelque part sous un dossier de niveau supérieur nommé *config* ou similaire, comme décrit dans [Utilisation des pipelines de configuration](/help/operations/config-pipeline.md#folder-structure).

1. Pour les types d’environnements autres que RDE (qui utilise des outils de ligne de commande), créez un pipeline de configuration de déploiement ciblé dans Cloud Manager, comme référencé par [cette section](/help/operations/config-pipeline.md#creating-and-managing). Notez que les pipelines de pile complète et les pipelines de niveau web ne déploient pas le fichier de configuration.

1. Déployez la configuration.

Les jetons dans la configuration (tels que `${{SPLUNK_TOKEN}}`) représentent des secrets, qui ne doivent pas être stockés dans Git. À la place, déclarez-les en tant que [variables d’environnement secrètes](/help/operations/config-pipeline.md#secret-env-vars) Cloud Manager. Veillez à sélectionner **Tous** comme valeur de liste déroulante pour le champ Service appliqué, de sorte que les journaux puissent être transférés vers les niveaux d’auteur, de publication et d’aperçu.

Il est possible de définir des valeurs différentes entre les journaux CDN et les journaux d’AEM (y compris Apache/Dispatcher), en incluant un bloc supplémentaire **cdn** et/ou **aem** après le bloc **default**, où les propriétés peuvent remplacer celles définies dans le bloc **default** ; seule la propriété activée est requise. Un cas d’utilisation possible peut être l’utilisation d’un index Splunk différent pour les journaux CDN, comme l’exemple ci-dessous.

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
       cdn:
         enabled: true
         token: "${{SPLUNK_TOKEN_CDN}}"
         index: "AEMaaCS_CDN"   
```

Un autre scénario consiste à désactiver le transfert des journaux CDN ou AEM journaux (y compris Apache/Dispatcher). Par exemple, pour ne transférer que les journaux CDN, vous pouvez configurer les éléments suivants :

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
       aem:
         enabled: false
```

## Configuration de la destination de journalisation {#logging-destinations}

Les configurations pour les destinations de journalisation prises en charge sont répertoriées ci-dessous, ainsi que toute considération spécifique.

### Stockage Azure Blob {#azureblob}

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  azureBlob:
    default:
      enabled: true       
      storageAccountName: "example_acc"
      container: "aem_logs"
      sasToken: "${{AZURE_BLOB_SAS_TOKEN}}
      
```

Un jeton SAS doit être utilisé pour l’authentification. Elle doit être créée à partir de la page de signature Accès partagé, plutôt que sur la page Jeton d’accès partagé , et doit être configurée avec les paramètres suivants :

* Services autorisés : l’objet Blob doit être sélectionné.
* Ressources autorisées : l’objet doit être sélectionné.
* Autorisations autorisées : vous devez sélectionner Write, Add, Create (Écrire, Ajouter, Créer).
* Date/heure de début et d’expiration valides.

Voici une capture d’écran d’un exemple de configuration de jeton SAS :

![Configuration du jeton Azure Blob SAS](/help/implementing/developing/introduction/assets/azureblob-sas-token-config.png)

Si les logs ont cessé d’être diffusés après avoir fonctionné correctement, vérifiez si le jeton SAS que vous avez configuré est toujours valide, car il a peut-être expiré.

#### Journaux CDN Azure Blob Storage {#azureblob-cdn}

Chacun des serveurs de journalisation répartis dans le monde produira un nouveau fichier toutes les quelques secondes, sous le dossier `aemcdn`. Une fois créé, le fichier ne sera plus annexé au fichier. Le format du nom de fichier est AAAA-MM-DDThh:mm:ss.sss-uniqueid.log. Par exemple, 2024-03-04T10:00:00.000-WnFWYN9BpOUs2aOVn4ee.log.

Par exemple, à un moment donné :

```
aemcdn/
   2024-03-04T10:00:00.000-abc.log
   2024-03-04T10:00:00.000-def.log
```

Et puis 30 secondes plus tard :

```
aemcdn/
   2024-03-04T10:00:00.000-abc.log
   2024-03-04T10:00:00.000-def.log
   2024-03-04T10:00:30.000-ghi.log
   2024-03-04T10:00:30.000-jkl.log
   2024-03-04T10:00:30.000-mno.log
```

Chaque fichier contient plusieurs entrées de journal json, chacune sur une ligne distincte. Les formats d’entrée de journal sont décrits sous [Journalisation pour AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md), et chaque entrée de journal inclut également les propriétés supplémentaires mentionnées dans la section [Formats d’entrée de journal](#log-format) ci-dessous.

#### Journaux Azure Blob Storage AEM {#azureblob-aem}

Les journaux d’AEM (y compris Apache/Dispatcher) apparaissent sous un dossier avec la convention d’affectation des noms suivante :

* aemaccess
* aemerror
* aemrequest
* aemdispatcher
* aemhttpdaccess
* aemhttpderror

Sous chaque dossier, un seul fichier est créé et ajouté. Les clients sont responsables du traitement et de la gestion de ce fichier afin qu’il ne se développe pas trop.

Voir les formats d’entrée de journal sous [Journalisation pour AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md). Les entrées de journal incluent également les propriétés supplémentaires mentionnées dans la section [Formats de saisie de journal](#log-formats) ci-dessous.


### Datadog {#datadog}

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  datadog:
    default:
      enabled: true       
      host: "http-intake.logs.datadoghq.eu"
      token: "${{DATADOG_API_KEY}}"
      tags:
         tag1: value1
         tag2: value2
      
```

Considérations :

* Créez une clé API, sans intégration avec un fournisseur cloud spécifique.
* La propriété tags est facultative.
* Pour les journaux d’AEM, la balise source de données est définie sur `aemaccess`, `aemerror`, `aemrequest`, `aemdispatcher`, `aemhttpdaccess` ou `aemhttpderror`.
* Pour les journaux CDN, la balise source Datadog est définie sur `aemcdn`.
* La balise du service Datadog est définie sur `adobeaemcloud`, mais vous pouvez la remplacer dans la section des balises.
* Si votre pipeline d’ingestion utilise des balises Datadog pour déterminer l’index approprié pour les journaux de transfert, vérifiez que ces balises sont correctement configurées dans le fichier YAML de transfert de journal. Les balises manquantes peuvent empêcher l’ingestion des journaux si le pipeline en dépend.



### Elasticsearch et OpenSearch {#elastic}

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  elasticsearch:
    default:
      enabled: true
      host: "example.com"
      user: "${{ELASTICSEARCH_USER}}"
      password: "${{ELASTICSEARCH_PASSWORD}}"
      pipeline: "ingest pipeline name"
```

Considérations :

* par défaut, le port est 443. Il peut éventuellement être remplacé par une propriété nommée `port`.
* Pour les informations d’identification, veillez à utiliser les informations d’identification de déploiement plutôt que les informations d’identification de compte. Il s’agit des informations d’identification générées dans un écran qui peut ressembler à cette image :

![Informations d’identification de déploiement élastiques](/help/implementing/developing/introduction/assets/ec-creds.png)

* Pour les journaux d’AEM, `index` est défini sur l’un des `aemaccess`, `aemerror`, `aemrequest`, `aemdispatcher`, `aemhttpdaccess` ou `aemhttpderror`
* La propriété de pipeline facultative doit être définie sur le nom du pipeline d’ingestion Elasticsearch ou OpenSearch, qui peut être configuré pour acheminer l’entrée de journal vers l’index approprié. Le type de processeur du pipeline doit être défini sur *script* et le langage de script doit être défini sur *sans douleur*. Voici un exemple de fragment de script pour acheminer les entrées de journal vers un index tel que aemaccess_dev_26_06_2024 :

```
def envType = ctx.aem_env_type != null ? ctx.aem_env_type : 'unknown';
def sourceType = ctx._index;
def date = new SimpleDateFormat('dd_MM_yyyy').format(new Date());
ctx._index = sourceType + "_" + envType + "_" + date;
```

### HTTPS {#https}

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  https:
    default:
      enabled: true
      url: "https://example.com/aem_logs/aem"
      authHeaderName: "X-AEMaaCS-Log-Forwarding-Token"
      authHeaderValue: "${{HTTPS_LOG_FORWARDING_TOKEN}}"
```

Considérations :

* La chaîne d’URL doit inclure **https://** ou la validation échouera.
* L’URL peut inclure un port. Par exemple, `https://example.com:8443/aem_logs/aem`. Si aucun port n’est inclus dans la chaîne d’URL, le port 443 (port HTTPS par défaut) est utilisé.

#### Logs CDN HTTPS {#https-cdn}

Les requêtes Web (POST) seront envoyées en continu, avec une payload json qui est un tableau d’entrées de journal, avec le format d’entrée de journal décrit sous [Journalisation pour AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md#cdn-log). Des propriétés supplémentaires sont mentionnées dans la section [Formats de saisie de journal](#log-formats) ci-dessous.

Il existe également une propriété nommée `sourcetype`, qui est définie sur la valeur `aemcdn`.

>[!NOTE]
>
> Avant l’envoi de la première entrée de journal CDN, votre serveur HTTP doit réussir un défi unique : une requête envoyée au chemin ``/.well-known/fastly/logging/challenge`` doit répondre avec un astérisque ``*`` dans le corps et un code d’état 200.

#### Journaux des AEM HTTPS {#https-aem}

Pour les journaux d’AEM (y compris apache/dispatcher), les demandes web (POST) seront envoyées en continu, avec une payload json qui est un tableau d’entrées de journal, avec les différents formats d’entrée de journal comme décrit sous [Journalisation pour AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md). Des propriétés supplémentaires sont mentionnées dans la section [Formats de saisie de journal](#log-format) ci-dessous.

Il existe également une propriété nommée `Source-Type`, définie sur l’une de ces valeurs :

* aemaccess
* aemerror
* aemrequest
* aemdispatcher
* aemhttpdaccess
* aemhttpderror

### Splunk {#splunk}

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
      index: "aemaacs"
```

Considérations :

* Par défaut, le port est 443. Il peut éventuellement être remplacé par une propriété nommée `port`.
* Le champ sourcetype aura l’une des valeurs suivantes, selon le journal spécifique : *aemaccess*, *aemerror*,
  *aemrequest*, *aemdispatcher*, *aemhttpdaccess*, *aemhttpderror*, *aemcdn*
* Si les adresses IP requises ont été placées sur la liste autorisée et que les journaux ne sont toujours pas distribués, vérifiez qu’aucune règle de pare-feu n’applique la validation du jeton Splunk. Exécute rapidement une étape de validation initiale au cours de laquelle un jeton Splunk non valide est envoyé de manière intentionnelle. Si votre pare-feu est défini pour mettre fin aux connexions avec des jetons Splunk non valides, le processus de validation échoue, ce qui empêche Fastly de diffuser des journaux vers votre instance Splunk.


>[!NOTE]
>
> [Si vous migrez ](#legacy-migration) de l’ancien transfert de journal vers ce modèle en libre-service, les valeurs du champ `sourcetype` envoyées à votre index Splunk ont peut-être changé, ajustez-les en conséquence.


<!--
### Sumo Logic {#sumologic}

   ```
   kind: "LogForwarding"
   version: "1"
   metadata:
     envTypes: ["dev"]
   data:
     splunk:
       default:
         enabled: true
         host: "https://collectors.de.sumologic.com"
         uri: "/receiver/v1/http"
         privateKey: "${{SomeOtherToken}}"
   
   ```   
-->

## Formats de saisie du journal {#log-formats}

Voir [Journalisation pour AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md) pour le format de chaque type de journal respectif (journaux CDN et journaux d’AEM y compris Apache/Dispatcher).

Puisque les journaux de plusieurs programmes et environnements peuvent être transférés vers la même destination de journalisation, en plus de la sortie décrite dans l’article de journalisation, les propriétés suivantes seront incluses dans chaque entrée de journal :

* aem_env_id
* aem_env_type
* aem_program_id
* aem_tier

Par exemple, les propriétés peuvent avoir les valeurs suivantes :

```
aem_env_id: 1242
aem_env_type: dev
aem_program_id: 12314
aem_tier: author
```

## Mise en réseau avancée {#advanced-networking}

Certaines organisations choisissent de restreindre le trafic qui peut être reçu par les destinations de journalisation.

Pour le journal du réseau de diffusion de contenu, vous pouvez ajouter des adresses IP aux listes autorisées, comme décrit dans la [documentation rapide - Liste d’adresses IP publiques](https://www.fastly.com/documentation/reference/api/utils/public-ip-list/). Si cette liste d’adresses IP partagées est trop volumineuse, envisagez d’envoyer du trafic vers un serveur https ou (non Adobe) Azure Blob Store où une logique peut être écrite pour envoyer les journaux d’une adresse IP connue vers leur destination finale.

Pour les journaux d’AEM (y compris Apache/Dispatcher), si vous avez configuré la [mise en réseau avancée](/help/security/configuring-advanced-networking.md), vous pouvez utiliser la propriété advancedNetworking pour les transférer à partir d’une adresse IP de sortie dédiée ou sur un VPN.

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
      port: 443
      token: "${{SPLUNK_TOKEN}}"
      index: "aemaacs"
    aem:
      advancedNetworking: true
```

## Migration à partir du transfert de journal hérité {#legacy-migration}

Avant que la configuration du transfert du journal ne soit réalisée par le biais d’un modèle en libre-service, les clients étaient invités à ouvrir les tickets d’assistance, où l’Adobe lancerait l’intégration.

Les clients qui ont été configurés de cette manière par Adobe sont les bienvenus pour s’adapter au modèle en libre-service à leur convenance. Cette transition peut être effectuée pour plusieurs raisons :

* Un nouvel environnement (par exemple, un nouvel environnement de développement ou RDE) a été configuré.
* Modifications apportées à votre point de terminaison Splunk existant ou à vos informations d’identification.
* Adobe avait configuré le transfert des journaux avant que les journaux CDN ne soient disponibles et que vous souhaitiez recevoir les journaux CDN.
* Une décision consciente d&#39;adapter de manière proactive au modèle en libre-service afin que votre organisation ait les connaissances nécessaires avant même qu&#39;un changement sensible au temps ne soit nécessaire.

Une fois prêt à migrer, configurez le fichier YAML comme décrit dans les sections précédentes. Utilisez le pipeline de configuration Cloud Manager pour effectuer le déploiement sur chacun des environnements dans lesquels la configuration doit être appliquée.

Il est recommandé, mais non obligatoire, qu’une configuration soit déployée dans tous les environnements afin qu’ils soient tous sous contrôle en libre-service. Dans le cas contraire, vous pouvez oublier les environnements qui ont été configurés par Adobe par rapport à ceux configurés en libre-service.

>[!NOTE]
>
>Les valeurs du champ `sourcetype` envoyées à votre index Splunk peuvent avoir changé. Vous pouvez donc vous adapter en conséquence.

>[!NOTE]
>
>Lorsque le transfert des journaux est déployé dans un environnement précédemment configuré par la prise en charge d’Adobe, vous pouvez recevoir des logs en double pendant quelques heures au maximum. Cela finira par se résoudre automatiquement.

