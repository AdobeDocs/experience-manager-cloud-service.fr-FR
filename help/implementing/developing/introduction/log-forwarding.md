---
title: Transfert de journal pour AEM as a Cloud Service
description: En savoir plus sur le transfert des journaux vers Splunk et d’autres fournisseurs de journalisation dans AEM as a Cloud Service
source-git-commit: 13696ffde99114e5265e5c2818cb3257dd09ee8c
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 3%

---


# Transfert de journal {#log-forwarding}

>[!NOTE]
>
>Cette fonctionnalité n’est pas encore publiée et certaines destinations de journalisation peuvent ne pas être disponibles au moment de la publication. En attendant, vous pouvez ouvrir un ticket d’assistance pour transférer les journaux vers **Splunk**, comme décrit dans la section [article de connexion](/help/implementing/developing/introduction/logging.md).

Les clients qui disposent d’une licence pour un fournisseur de journalisation ou qui hébergent un produit de journalisation peuvent avoir AEM, Apache/Dispatcher et des journaux CDN transférés vers les destinations de journalisation associées. AEM as a Cloud Service prend en charge les destinations de journalisation suivantes :

* Stockage Azure Blob
* DataDog
* Elasticsearch ou OpenSearch
* HTTPS
* Splunk

Le transfert de journal est configuré en libre-service en déclarant une configuration dans Git et en la déployant via le pipeline de configuration de Cloud Manager vers les types d’environnements de développement, d’évaluation et de production dans les programmes de production (hors environnements de test).

Notez que la bande passante réseau associée aux journaux envoyés à la destination de journalisation est considérée comme faisant partie de l’utilisation des E/S réseau de votre entreprise.


## Organisation de cet article {#how-organized}

Cet article est organisé de la manière suivante :

* Configuration : commune à toutes les destinations de journalisation
* Configurations de destination de journalisation : chaque destination a un format légèrement différent.
* Mise en réseau avancée : envoi de journaux d’AEM et Apache/Dispatcher via une sortie dédiée ou via un VPN


## Configuration {#setup}

1. Créez la structure de dossiers et de fichiers suivante dans le dossier de niveau supérieur de votre projet dans Git :

   ```
   config/
        logForwarding.yaml
   ```

1. logForwarding.yaml doit contenir des métadonnées et une configuration similaire au format suivant (nous utilisons Splunk comme exemple).

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

   La variable **kind** doit être défini sur LogForwarding , la version doit être définie sur la version du schéma, qui est 1.

   Jetons dans la configuration (tels que `${{SPLUNK_TOKEN}}`) représentent des secrets, qui ne doivent pas être stockés dans Git. À la place, déclarez-les comme Cloud Manager  [Variables d’environnement](/help/implementing/cloud-manager/environment-variables.md) de type **secret**. Veillez à sélectionner **Tous** comme valeur de liste déroulante pour le champ Service appliqué , afin que les journaux puissent être transférés vers les niveaux d’auteur, de publication et d’aperçu.

   Il est possible de définir des valeurs différentes entre les journaux cdn et tout le reste (journaux AEM et apache), en incluant une **cdn** et/ou **aem** après la balise **default** block, où les propriétés peuvent remplacer celles définies dans la variable **default** block ; seule la propriété enabled est requise. Un cas d’utilisation possible peut être l’utilisation d’un index Splunk différent pour les journaux CDN, comme l’exemple ci-dessous.

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

   Un autre scénario consiste à désactiver le transfert des journaux CDN ou de tout le reste (journaux AEM et apache). Par exemple, pour ne transférer que les journaux CDN, vous pouvez configurer les éléments suivants :

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

1. Pour les types d’environnements autres que RDE (qui n’est actuellement pas pris en charge), créez un pipeline de configuration de déploiement ciblé dans Cloud Manager.

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
* Autorisations autorisées : l’écriture, l’ajout et la création doivent être sélectionnés.
* Date/heure de début et d’expiration valides.

Voici une capture d’écran d’un exemple de configuration de jeton SAS :

![Configuration du jeton Azure Blob SAS](/help/implementing/developing/introduction/assets/azureblob-sas-token-config.png)


### Datadog {#datadog}

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  dataDog:
    default:
      enabled: true       
      host: "http-intake.logs.datadoghq.eu"
      token: "${{DATADOG_API_KEY}}"
      
```

Considérations :

* Créez une clé API, sans intégration avec un fournisseur cloud spécifique.


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
```

Considérations :

* Pour les informations d’identification, veillez à utiliser les informations d’identification de déploiement plutôt que les informations d’identification de compte. Il s’agit des informations d’identification générées dans un écran qui peut ressembler à cette image :

![Informations d’identification de déploiement Elastic](/help/implementing/developing/introduction/assets/ec-creds.png)

### HTTPS {#https}

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  https:
    default:
      url: "https://example.com/aem_logs/aem"
      authHeaderName: "X-AEMaaCS-Log-Forwarding-Token"
      authHeaderValue: "${{HTTPS_LOG_FORWARDING_TOKEN}}"
```

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

## Mise en réseau avancée {#advanced-networking}

Si vous avez des exigences organisationnelles pour verrouiller le trafic vers votre destination de journalisation, vous pouvez configurer le transfert des journaux pour qu’il [mise en réseau avancée](/help/security/configuring-advanced-networking.md). Découvrez les modèles des trois types de mise en réseau avancés ci-dessous, qui utilisent une `port` , ainsi que la variable `host` .

### Sortie de port flexible {#flex-port}

Si le trafic du journal va vers un port autre que 443 (par exemple, 8443 ci-dessous), configurez la mise en réseau avancée comme suit :

```
{
    "portForwards": [
        {
            "name": "mylogging.service.logger.com",
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
      host: "proxy.tunnel"
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
            "name": "mylogging.service.com",
            "portDest": 443, # something other than 443
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
      host: "proxy.tunnel"
      token: "${{SomeToken}}"
      port: 30443
      index: "index_name"
```

### VPN {#vpn}

Si le trafic du journal doit passer par un VPN, configurez la mise en réseau avancée comme suit :

```
{
    "portForwards": [
        {
            "name": "mylogging.service.com",
            "portDest": 443, # something other than 443
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
      host: "mylogging.service.com"
      token: "${{SomeToken}}"
      port: 30443
      index: "index_name"
```