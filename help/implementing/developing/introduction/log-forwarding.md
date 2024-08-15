---
title: Transfert de journal pour AEM as a Cloud Service
description: En savoir plus sur le transfert des journaux vers Splunk et d’autres fournisseurs de journalisation dans AEM as a Cloud Service
exl-id: 27cdf2e7-192d-4cb2-be7f-8991a72f606d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 85cef99dc7a8d762d12fd6e1c9bc2aeb3f8c1312
workflow-type: tm+mt
source-wordcount: '1375'
ht-degree: 1%

---

# Transfert de journaux {#log-forwarding}

>[!NOTE]
>
>Cette fonctionnalité n’est pas encore disponible et certaines destinations de journalisation peuvent ne pas être disponibles au moment de la publication. En attendant, vous pouvez ouvrir un ticket d’assistance pour transférer les journaux vers **Splunk**, comme décrit sous [Journalisation pour AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md).

Les clients qui disposent d’une licence pour un fournisseur de journalisation ou qui hébergent un produit de journalisation peuvent avoir AEM journaux (y compris Apache/Dispatcher) et des journaux CDN transférés vers les destinations de journalisation associées. AEM as a Cloud Service prend en charge les destinations de journalisation suivantes :

* Stockage Azure Blob
* DataDog
* Elasticsearch ou OpenSearch
* HTTPS
* Splunk

Le transfert de journal est configuré en libre-service en déclarant une configuration dans Git et en la déployant via le pipeline de configuration de Cloud Manager vers les types d’environnements de développement, d’évaluation et de production dans les programmes de production (hors environnements de test).

Il existe une option pour que les journaux d’AEM et Apache/Dispatcher soient acheminés par le biais d’AEM infrastructure de mise en réseau avancée, telle qu’une adresse IP de sortie dédiée.

Notez que la bande passante réseau associée aux journaux envoyés à la destination de journalisation est considérée comme faisant partie de l’utilisation des E/S réseau de votre entreprise.


## Organisation de cet article {#how-organized}

Cet article est organisé de la manière suivante :

* Configuration : commune à toutes les destinations de journalisation
* Configurations de destination de journalisation : chaque destination a un format légèrement différent.
* Formats de saisie de journal - informations sur les formats de saisie de journal
* Mise en réseau avancée : envoi de journaux AEM et Apache/Dispatcher via une sortie dédiée ou via un VPN


## Configuration {#setup}

1. Créez la structure de dossiers et de fichiers suivante dans le dossier de niveau supérieur de votre projet dans Git :

   ```
   config/
        logForwarding.yaml
   ```

1. `logForwarding.yaml` doit contenir des métadonnées et une configuration similaire au format suivant (nous utilisons Splunk comme exemple).

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

   Le paramètre **kind** doit être défini sur `LogForwarding`, la version doit être définie sur la version du schéma, qui est 1.

   Les jetons dans la configuration (tels que `${{SPLUNK_TOKEN}}`) représentent des secrets, qui ne doivent pas être stockés dans Git. À la place, déclarez-les comme Cloud Manager [Variables d’environnement](/help/implementing/cloud-manager/environment-variables.md) de type **secret**. Veillez à sélectionner **Tous** comme valeur de liste déroulante pour le champ Service appliqué, de sorte que les journaux puissent être transférés vers les niveaux d’auteur, de publication et d’aperçu.

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

1. Pour les types d’environnements autres que RDE (qui n’est actuellement pas pris en charge), créez un pipeline de configuration de déploiement ciblé dans Cloud Manager. Notez que les pipelines de pile complète et les pipelines de niveau web ne déploient pas le fichier de configuration.

   * [Voir Configuration des pipelines de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md).
   * [Voir Configuration des pipelines hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).

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
* aemdispatcher
* httpdaccess
* httpderror

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
* la propriété tags est facultative.


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

* Pour les informations d’identification, veillez à utiliser les informations d’identification de déploiement plutôt que les informations d’identification de compte. Il s’agit des informations d’identification générées dans un écran qui peut ressembler à cette image :

![Informations d’identification de déploiement élastiques](/help/implementing/developing/introduction/assets/ec-creds.png)

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
      url: "https://example.com:8443/aem_logs/aem"
      authHeaderName: "X-AEMaaCS-Log-Forwarding-Token"
      authHeaderValue: "${{HTTPS_LOG_FORWARDING_TOKEN}}"
```

Considérations :

* La chaîne d’URL doit inclure **https://** ou la validation échouera. Si aucun port n’est inclus dans la chaîne d’URL, le port 443 (port HTTPS par défaut) est utilisé.
* Si vous souhaitez utiliser un port différent du port 443, veuillez le fournir dans le cadre de l’URL.

#### Logs CDN HTTPS {#https-cdn}

Les requêtes Web (POST) seront envoyées en continu, avec une payload json qui est un tableau d’entrées de journal, avec le format d’entrée de journal décrit sous [Journalisation pour AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md#cdn-log). Des propriétés supplémentaires sont mentionnées dans la section [Formats de saisie de journal](#log-formats) ci-dessous.

Il existe également une propriété nommée `sourcetype`, qui est définie sur la valeur `aemcdn`.

>[!NOTE]
>
> Avant l’envoi de la première entrée de journal CDN, votre serveur HTTP doit réussir un défi unique : une requête envoyée au chemin ``/.well-known/fastly/logging/challenge`` doit répondre avec un astérisque ``*`` dans le corps et un code d’état 200.

#### Journaux des AEM HTTPS {#https-aem}

Pour les journaux d’AEM (y compris apache/dispatcher), les demandes web (POST) seront envoyées en continu, avec une payload json qui est un tableau d’entrées de journal, avec les différents formats d’entrée de journal comme décrit sous [Journalisation pour AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md). Des propriétés supplémentaires sont mentionnées dans la section [Formats de saisie de journal](#log-format) ci-dessous.

Il existe également une propriété nommée `sourcetype`, définie sur l’une de ces valeurs :

* aemaccess
* aemerror
* aemdispatcher
* httpdaccess
* httpderror

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
      index: "AEMaaCS"
```

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

>[!NOTE]
>
>Cette fonctionnalité n’est pas encore prête pour les utilisateurs plus précoces.


Certaines organisations choisissent de restreindre le trafic qui peut être reçu par les destinations de journalisation.

Pour le journal du réseau de diffusion de contenu, vous pouvez ajouter des adresses IP aux listes autorisées, comme décrit dans la [documentation rapide - Liste d’adresses IP publiques](https://www.fastly.com/documentation/reference/api/utils/public-ip-list/). Si cette liste d’adresses IP partagées est trop volumineuse, envisagez d’envoyer du trafic vers un Azure Blob Store (non Adobe) où une logique peut être écrite pour envoyer les journaux d’une adresse IP dédiée vers leur destination finale.

Pour les journaux d’AEM (y compris Apache/Dispatcher), vous pouvez configurer le transfert des journaux pour passer par la [mise en réseau avancée](/help/security/configuring-advanced-networking.md). Consultez les modèles pour les trois types de réseau avancés ci-dessous, qui utilisent un paramètre facultatif `port` , ainsi que le paramètre `host` .

### Sortie de port flexible {#flex-port}

Si le trafic du journal va vers un port autre que 443 (par exemple, 8443 ci-dessous), configurez la mise en réseau avancée comme suit :

```
{
    "portForwards": [
        {
            "name": "splunk-host.example.com",
            "portDest": 8443, # something other than 443
            "portOrig": 30443
        }    
    ]
}
```

et configurez le fichier yaml comme suit :

```
kind: "LogForwarding"
version: "1"
data:
  splunk:
    default:
      host: "${{AEM_PROXY_HOST}}"
      token: "${{SomeToken}}"
      port: 30443
      index: "index_name"
```

### Adresse IP Egress dédiée {#dedicated-egress}


Si le trafic du journal doit sortir d’une adresse IP de sortie dédiée, configurez la mise en réseau avancée comme suit :

```
{
    "portForwards": [
        {
            "name": "splunk-host.example.com",
            "portDest": 443, 
            "portOrig": 30443
        }    
    ]
}
```

et configurez le fichier yaml comme suit :

```
      
kind: "LogForwarding"
version: "1"
   metadata:
     envTypes: ["dev"]
data:
  splunk:
     default:
       enabled: true
       index: "index_name" 
       token: "${{SPLUNK_TOKEN}}"  
     aem:
       enabled: true
       host: "${{AEM_PROXY_HOST}}"
       port: 30443       
     cdn:
       enabled: true
       host: "splunk-host.example.com"
       port: 443    
```

### VPN {#vpn}

Si le trafic du journal doit passer par un VPN, configurez la mise en réseau avancée comme suit :

```
{
    "portForwards": [
        {
            "name": "splunk-host.example.com",
            "portDest": 443,
            "portOrig": 30443
        }    
    ]
}

kind: "LogForwarding"
version: "1"
   metadata:
     envTypes: ["dev"]
data:
  splunk:
     default:
       enabled: true
       index: "index_name" 
       token: "${{SPLUNK_TOKEN}}"  
     aem:
       enabled: true
       host: "${{AEM_PROXY_HOST}}"
       port: 30443       
     cdn:
       enabled: true
       host: "splunk-host.example.com"
       port: 443     
```
