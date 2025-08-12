---
title: Transfert de journal pour AEM as a Cloud Service
description: Découvrez comment transférer des journaux à des fournisseurs de journalisation dans AEM as a Cloud Service
exl-id: 27cdf2e7-192d-4cb2-be7f-8991a72f606d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: tm+mt
source-wordcount: '2409'
ht-degree: 3%

---

# Transfert de journaux {#log-forwarding}

>[!NOTE]
>
>Le transfert de journal est désormais configuré en libre-service, différent de la méthode héritée qui nécessitait l’envoi d’un ticket d’assistance pour Adobe. Pour plus d&#39;informations, consultez la section [ Migration ](#legacy-migration) si le transfert du journal a été configuré par Adobe.

Les clients disposant d’une licence auprès d’un fournisseur de journalisation ou qui hébergent un produit de journalisation peuvent transférer les journaux AEM (y compris Apache/Dispatcher) et les journaux CDN vers la destination de journalisation associée. AEM as a Cloud Service prend en charge les destinations de journalisation suivantes :

<table>
  <tbody>
    <tr>
      <th>Technologie des journaux</th>
      <th>Private Beta*</th>
      <th>AEM</th>
      <th>Dispatcher</th>
      <th>Réseau de diffusion de contenu (CDN)</th>
    </tr>
    <tr>
      <td>Amazon S3</td>
      <td style="background-color: #ffb3b3;">Oui</td>
      <td>Oui</td>
      <td>Oui</td>
      <td style="background-color: #ffb3b3;">Non</td>
    </tr>
    <tr>
      <td>Stockage Azure Blob</td>
      <td>Non</td>
      <td>Oui</td>
      <td>Oui</td>
      <td>Oui</td>
    </tr>
    <tr>
      <td>DataDog</td>
      <td>Non</td>
      <td>Oui</td>
      <td>Oui</td>
      <td>Oui</td>
    </tr>
    <tr>
      <td>Dynatrace</td>
      <td style="background-color: #ffb3b3;">Oui</td>
      <td>Oui</td>
      <td>Oui</td>
      <td style="background-color: #ffb3b3;">Non</td>
    </tr>
    <tr>
      <td>Elasticsearch<br>OpenSearch</td>
      <td>Non</td>
      <td>Oui</td>
      <td>Oui</td>
      <td>Oui</td>
    </tr>
    <tr>
      <td>HTTPS</td>
      <td>Non</td>
      <td>Oui</td>
      <td>Oui</td>
      <td>Oui</td>
    </tr>
    <tr>
      <td>New Relic</td>
      <td style="background-color: #ffb3b3;">Oui</td>
      <td>Oui</td>
      <td>Oui</td>
      <td style="background-color: #ffb3b3;">Non</td>
    </tr>
    <tr>
      <td>Splunk</td>
      <td>Non</td>
      <td>Oui</td>
      <td>Oui</td>
      <td>Oui</td>
    </tr>
    <tr>
      <td>Logique Sumo</td>
      <td style="background-color: #ffb3b3;">Oui</td>
      <td>Oui</td>
      <td>Oui</td>
      <td style="background-color: #ffb3b3;">Non</td>
    </tr>
  </tbody>
</table>
&lt;/html>

>[!NOTE]
>
> Pour les technologies dans Private Beta, veuillez envoyer un e-mail à [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com) pour demander l’accès.

Le transfert du journal est configuré en libre-service en déclarant une configuration dans Git et peut être déployé via les pipelines de configuration de Cloud Manager vers les types d’environnements de développement, d’évaluation et de production. Le fichier de configuration peut être déployé dans des environnements de développement rapide (RDE) à l’aide de l’outil de ligne de commande.

Il existe une option pour que les journaux AEM et Apache/Dispatcher soient acheminés via l’infrastructure de réseau avancée d’AEM, telle que l’adresse IP de sortie dédiée.

Notez que la bande passante réseau associée aux journaux envoyés à la destination de journalisation est considérée comme faisant partie de l’utilisation des E/S réseau de votre entreprise.

## Organisation de cet article {#how-organized}

L’organisation de cet article est la suivante :

* Configuration : commune à toutes les destinations de journalisation.
* Transport et mise en réseau avancée : la configuration réseau doit être prise en compte avant la création de la configuration de journalisation
* Configurations des destinations de journalisation - Chaque destination a un format légèrement différent
* Formats d’entrée du journal : informations sur les formats d’entrée du journal
* Migration du transfert de journal hérité : comment passer du transfert de journal précédemment configuré par Adobe à l’approche en libre-service.

## Configuration {#setup}

1. Créez un fichier nommé `logForwarding.yaml`. Il doit contenir des métadonnées, comme décrit dans l’article [Pipeline de configuration](/help/operations/config-pipeline.md#common-syntax) (**kind** doit être défini sur `LogForwarding` et la version doit être définie sur « 1 »), avec une configuration similaire à la suivante (nous utilisons Splunk comme exemple).

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

1. Placez le fichier quelque part sous un dossier de niveau supérieur nommé *config* ou similaire, comme décrit dans la section [ Utilisation des pipelines de configuration](/help/operations/config-pipeline.md#folder-structure).

1. Pour les types d’environnement autres que le RDE (qui utilise l’outil de ligne de commande), créez un pipeline de configuration de déploiement ciblé dans Cloud Manager, comme indiqué dans [cette section](/help/operations/config-pipeline.md#creating-and-managing) ; notez que les pipelines de pile complète et de niveau web ne déploient pas le fichier de configuration.

1. Déployez la configuration.

Les jetons de la configuration (tels que `${{SPLUNK_TOKEN}}`) représentent des secrets, qui ne doivent pas être stockés dans Git. Au lieu de cela, déclarez-les comme Cloud Manager [Variables d’environnement secrètes](/help/operations/config-pipeline.md#secret-env-vars). Veillez à sélectionner **Tous** comme valeur de liste déroulante pour le champ Service appliqué afin que les journaux puissent être transférés aux niveaux de création, de publication et de prévisualisation.

Il est possible de définir des valeurs différentes entre les journaux CDN et les journaux AEM (y compris Apache/Dispatcher), en incluant un bloc **cdn** et/ou **aem** supplémentaire après le bloc **default**, où les propriétés peuvent remplacer celles définies dans le bloc **default** ; seule la propriété enabled est requise. Un cas d’utilisation possible pourrait consister à utiliser un index Splunk différent pour les journaux CDN, comme illustré dans l’exemple ci-dessous.

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
       cdn:
         enabled: true
         token: "${{SPLUNK_TOKEN_CDN}}"
         index: "AEMaaCS_CDN"   
```

Un autre scénario consiste à désactiver le transfert des journaux CDN ou des journaux AEM (y compris Apache/Dispatcher). Par exemple, pour transférer uniquement les journaux du réseau CDN, vous pouvez configurer les éléments suivants :

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
       aem:
         enabled: false
```

## Transport et mise en réseau avancée {#transport-advancednetworking}

Certaines organisations choisissent de limiter le trafic pouvant être reçu par les destinations de journalisation, d’autres peuvent nécessiter d’utiliser des ports autres que HTTPS (443).  Si tel est le cas, [Mise en réseau avancée](/help/security/configuring-advanced-networking.md) doit être configuré avant le déploiement de la configuration de transfert de journal.

Utilisez le tableau ci-dessous pour connaître les exigences relatives à la configuration avancée de la mise en réseau et de la journalisation selon que vous utilisez le port 443 ou non et que vous avez besoin ou non que vos journaux apparaissent à partir d’une adresse IP fixe.

<table>
  <tbody>
    <tr>
      <th>Port de destination</th>
      <th>Exigence d’affichage des journaux à partir d’une adresse IP fixe ?</th>
      <th>Mise en réseau avancée nécessaire</th>
      <th>Définition de port LogForwarding.yaml nécessaire</th>
    </tr>
    <tr>
      <td rowspan="2" ro>HTTPS (443)</td>
      <td>Non</td>
      <td>Non</td>
      <td>Non</td>
    </tr>
    <tr>
      <td>Oui</td>
      <td>Oui, <a href="/help/security/configuring-advanced-networking.md#dedicated-egress-ip-address-dedicated-egress-ip-address"> Sortie Dédiée </a></td>
      <td>Non</td>
    <tr>
    <tr>
      <td rowspan="2">Port non standard (par exemple, 8088)</td>
      <td>Non</td>
      <td>Oui, <a href="/help/security/configuring-advanced-networking.md#flexible-port-egress-flexible-port-egress">sortie flexible</a></td>
      <td>Oui</td>
    </tr>
    <tr>
      <td>Oui</td>
      <td>Oui, <a href="/help/security/configuring-advanced-networking.md#dedicated-egress-ip-address-dedicated-egress-ip-address"> Sortie Dédiée </a></td>
      <td>Oui</td>
  </tbody>
</table>
&lt;/html>

>[!NOTE]
>Le fait que vos journaux s’affichent à partir d’une seule adresse IP dépend de la configuration de mise en réseau avancée que vous avez choisie.  Une sortie dédiée doit être utilisée pour faciliter cette opération.
>
> La configuration réseau avancée est un [ processus en deux étapes](/help/security/configuring-advanced-networking.md#configuring-and-enabling-advanced-networking-configuring-enabling) qui nécessite une activation au niveau du programme et de l’environnement.

Pour les journaux AEM (y compris Apache/Dispatcher), si vous avez configuré [Mise en réseau avancée](/help/security/configuring-advanced-networking.md), vous pouvez utiliser la propriété `aem.advancedNetworking` pour les transférer à partir d’une adresse IP sortante dédiée ou via un VPN.

L’exemple ci-dessous montre comment configurer la journalisation sur un port HTTPS standard avec la mise en réseau avancée.

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
      port: 443
      token: "${{SPLUNK_TOKEN}}"
      index: "aemaacs"
    aem:
      advancedNetworking: true
```

Pour les journaux CDN, vous pouvez placer les adresses IP sur la liste autorisée, comme décrit dans la section [Documentation Fastly - Liste publique d’adresses IP](https://www.fastly.com/documentation/reference/api/utils/public-ip-list/). Si cette liste d’adresses IP partagées est trop volumineuse, pensez à envoyer le trafic vers un serveur https ou un Azure Blob Store (autre qu’Adobe) où une logique peut être écrite pour envoyer les journaux d’une adresse IP connue vers leur destination finale.

>[!NOTE]
>
>Il n’est pas possible que les journaux du réseau CDN apparaissent à partir de la même adresse IP que celle à partir de laquelle vos journaux AEM apparaissent. En effet, les journaux sont envoyés directement depuis Fastly et non depuis AEM Cloud Service.

## Consignation de la configuration de destination {#logging-destinations}

Les configurations des destinations de journalisation prises en charge sont répertoriées ci-dessous, avec des considérations spécifiques.

### Amazon S3 {#amazons3}

Le transfert de journal vers Amazon S3 prend en charge les journaux AEM et Dispatcher. Les journaux CDN ne sont pas encore pris en charge.

>[!NOTE]
>
>Journaux écrits périodiquement dans S3, toutes les 10 minutes pour chaque type de fichier journal.  Cela peut entraîner un délai initial pour l’écriture des journaux dans S3 une fois la fonctionnalité basculée.  [Informations supplémentaires sur ce comportement](https://docs.fluentbit.io/manual/pipeline/outputs/s3#differences-between-s3-and-other-fluent-bit-outputs).

```yaml
kind: "LogForwarding"
version: "1.0"
metadata:
  envTypes: ["dev"]
data:
  awsS3:
    default:
      enabled: true
      region: "your-bucket-region"
      bucket: "your_bucket_name"
      accessKey: "${{AWS_S3_ACCESS_KEY}}"
      secretAccessKey: "${{AWS_S3_SECRET_ACCESS_KEY}}"
```

Pour utiliser le redirecteur de journal S3, vous devez préconfigurer un utilisateur AWS IAM avec la politique appropriée pour accéder à votre compartiment S3.  Consultez la [Documentation de l’utilisateur AWS IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html) pour savoir comment créer des informations d’identification d’utilisateur IAM.

La politique IAM doit permettre à l’utilisateur d’utiliser `s3:putObject`.  Par exemple :

```json
 {
    "Version": "2012-10-17",
    "Statement": [{
        "Effect": "Allow",
        "Action": [
            "s3:PutObject"
        ],
        "Resource": "arn:aws:s3:::your_bucket_name/*"
    }]
}
```

Consultez la [documentation de la politique de compartiment AWS](https://docs.aws.amazon.com/AmazonS3/latest/userguide/bucket-policies.html) pour plus d’informations sur la mise en œuvre.

### Stockage Azure Blob {#azureblob}

```yaml
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

Un jeton SAS doit être utilisé pour l’authentification. Il doit être créé à partir de la page de signature d’accès partagé, plutôt que sur la page Jeton d’accès partagé , et doit être configuré avec les paramètres suivants :

* Services autorisés : l’objet Blob doit être sélectionné.
* Ressources autorisées : l’objet doit être sélectionné.
* Autorisations autorisées : écriture, ajout, création doivent être sélectionnés.
* Une date/heure de début et d’expiration valide.

Voici une capture d’écran d’un exemple de configuration de jeton SAS :

![ Configuration du jeton SAS Azure Blob ](/help/implementing/developing/introduction/assets/azureblob-sas-token-config.png)

Si la diffusion des journaux a cessé après un fonctionnement correct, vérifiez si le jeton SAS que vous avez configuré est toujours valide, car il a peut-être expiré.

#### Journaux du réseau CDN de stockage Blob Azure {#azureblob-cdn}

Chacun des serveurs de journalisation distribués globalement produira un nouveau fichier toutes les quelques secondes, sous le dossier `aemcdn`. Une fois créé, le fichier n’est plus ajouté à . Le format du nom de fichier est AAAA-MM-JJThh:mm:ss.sss-uniqueid.log. Par ex., 2024-03-04T10:00:00.000-WnFWYN9BpOUs2aOVn4ee.log.

Par exemple, à un moment donné :

```text
aemcdn/
   2024-03-04T10:00:00.000-abc.log
   2024-03-04T10:00:00.000-def.log
```

Et puis 30 secondes plus tard :

```text
aemcdn/
   2024-03-04T10:00:00.000-abc.log
   2024-03-04T10:00:00.000-def.log
   2024-03-04T10:00:30.000-ghi.log
   2024-03-04T10:00:30.000-jkl.log
   2024-03-04T10:00:30.000-mno.log
```

Chaque fichier contient plusieurs entrées de journal json, chacune sur une ligne distincte. Les formats d’entrée de journal sont décrits à la section [Journalisation pour AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md) et chaque entrée de journal inclut également les propriétés supplémentaires mentionnées dans la section [Formats d’entrée de journal](#log-formats) ci-dessous.

#### Journaux AEM du stockage Blob Azure {#azureblob-aem}

Les journaux AEM (y compris Apache/Dispatcher) s’affichent sous un dossier avec la convention de nommage suivante :

* aemaccess
* aemerror
* aemrequest
* aemdispatcher
* aemhttpdaccess
* aemhttpderror

Sous chaque dossier, un seul fichier est créé et ajouté. Les clients sont chargés de traiter et de gérer ce fichier afin qu’il ne s’étende pas trop.

Consultez les formats d’entrée de journal sous [ Journalisation pour AEM as a Cloud Service ](/help/implementing/developing/introduction/logging.md). Les entrées de journal incluent également les propriétés supplémentaires mentionnées dans la section [Formats d’entrée de journal](#log-formats) ci-dessous.

### Datadog {#datadog}

```yaml
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

#### Considérations

* Créez une clé API, sans intégration à un fournisseur de cloud spécifique.
* La propriété des balises est facultative
* Pour les journaux AEM, la balise source Datadog est définie sur `aemaccess`, `aemerror`, `aemrequest`, `aemdispatcher`, `aemhttpdaccess` ou `aemhttpderror`
* Pour les journaux CDN, la balise source Datadog est définie sur `aemcdn`
* La balise de service Datadog est définie sur `adobeaemcloud`, mais vous pouvez la remplacer dans la section des balises
* Si votre pipeline d’ingestion utilise des balises Datadog pour déterminer l’index approprié pour les journaux de transfert, vérifiez que ces balises sont correctement configurées dans le fichier YAML de transfert de journal. Les balises manquantes peuvent empêcher l’ingestion réussie du journal si le pipeline en dépend.

### Elasticsearch et OpenSearch {#elastic}

```yaml
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

#### Considérations

* par défaut, le port est 443. Il peut éventuellement être remplacé par une propriété nommée `port`
* Pour les informations d’identification, veillez à utiliser les informations d’identification de déploiement plutôt que les informations d’identification de compte. Voici les informations d’identification générées dans un écran qui peut ressembler à cette image :

![Informations d’identification de déploiement élastiques](/help/implementing/developing/introduction/assets/ec-creds.png)

* Pour les journaux AEM, `index` est défini sur `aemaccess`, `aemerror`, `aemrequest`, `aemdispatcher`, `aemhttpdaccess` ou `aemhttpderror`
* La propriété de pipeline facultative doit être définie sur le nom du pipeline d’ingestion Elasticsearch ou OpenSearch, qui peut être configuré pour acheminer l’entrée du journal vers l’index approprié. Le type de processeur du pipeline doit être défini sur *script* et le langage de script doit être défini sur *sans douleur*. Voici un exemple de fragment de script permettant d’acheminer les entrées de journal vers un index tel que aemaccess_dev_26_06_2024 :

```text
def envType = ctx.aem_env_type != null ? ctx.aem_env_type : 'unknown';
def sourceType = ctx._index;
def date = new SimpleDateFormat('dd_MM_yyyy').format(new Date());
ctx._index = sourceType + "_" + envType + "_" + date;
```

### HTTPS {#https}

```yaml
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

#### Considérations

* La chaîne d&#39;URL doit inclure **https://** sinon la validation échouera.
* L’URL peut inclure un port. Par exemple, `https://example.com:8443/aem_logs/aem`. Si aucun port n’est inclus dans la chaîne d’URL, le port 443 (port HTTPS par défaut) est supposé.

#### Journaux de réseau CDN HTTPS {#https-cdn}

Les requêtes web (POST) seront envoyées en continu, avec une payload json qui est un tableau d’entrées de journal, avec le format d’entrée de journal décrit sous [Journalisation pour AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md#cdn-log). Des propriétés supplémentaires sont mentionnées dans la section [Formats d’entrée de journal](#log-formats) ci-dessous.

Il existe également une propriété nommée `sourcetype`, qui est définie sur la valeur `aemcdn`.

>[!NOTE]
>
> Avant l’envoi de la première entrée du journal CDN, votre serveur HTTP doit réussir un défi unique : une requête envoyée au chemin d’accès ``/.well-known/fastly/logging/challenge`` doit répondre avec un astérisque ``*`` dans le corps et le code d’état 200.

#### Journaux HTTPS AEM {#https-aem}

Pour les journaux AEM (y compris Apache/Dispatcher), les requêtes web (POST) sont envoyées en continu, avec une payload json qui est un tableau d’entrées de journal, avec les différents formats d’entrée de journal comme décrit dans [Journalisation pour AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md). Des propriétés supplémentaires sont mentionnées dans la section [Formats d’entrée de journal](#log-formats) ci-dessous.

Il existe également une propriété nommée `Source-Type`, qui est définie sur l’une des valeurs suivantes :

* aemaccess
* aemerror
* aemrequest
* aemdispatcher
* aemhttpdaccess
* aemhttpderror

### API du journal New Relic {#newrelic-https}

Le transfert du journal vers New Relic utilise l’API HTTPS New Relic pour l’ingestion.  Actuellement, il ne prend en charge que les journaux d’AEM et de Dispatcher ; les journaux CDN ne sont pas encore pris en charge.

```yaml
  kind: "LogForwarding"
  version: "1"
  metadata:
    envTypes: ["dev"]
  data:
    newRelic:
      default:
        enabled: true
        uri: "https://log-api.newrelic.com/log/v1"
        apiKey: "${{NR_API_KEY}}"
```

>[!NOTE]
>
>Le transfert du journal vers New Relic n’est disponible que pour les comptes New Relic détenus par le client.
>
>Envoyer un courrier électronique à [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com) pour demander l’accès.
>
>New Relic fournit des points d’entrée spécifiques à une région en fonction de l’emplacement où votre compte New Relic est configuré.  Pour plus d’informations, consultez la documentation de New Relic [&#128279;](https://docs.newrelic.com/docs/logs/log-api/introduction-log-api/#endpoint).

### API du journal Dynatrace {#dynatrace-https}

Le transfert du journal vers Dynatrace utilise l’API HTTPS Dynatrace pour l’ingestion.  Actuellement, il ne prend en charge que les journaux d’AEM et de Dispatcher ; les journaux CDN ne sont pas encore pris en charge.

L’attribut de portée « Ingérer des journaux » est obligatoire pour le jeton.

```yaml
  kind: "LogForwarding"
  version: "1"
  metadata:
    envTypes: ["dev"]
  data:
    dynatrace:
      default:
        enabled: true
        environmentId: "${{DYNATRACE_ENVID}}"
        token: "${{DYNATRACE_TOKEN}}"  
```

>[!NOTE]
>
> Envoyer un courrier électronique à [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com) pour demander l’accès.

### Splunk {#splunk}

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
      index: "aemaacs"
```

#### Considérations

* Par défaut, le port est 443. Il peut éventuellement être remplacé par une propriété nommée `port`.
* Le champ sourcetype possède l’une des valeurs suivantes, en fonction du journal spécifique : *aemaccess*, *aemerror*,
  *aemrequest*, *aemdispatcher*, *aemhttpdaccess*, *aemhttpderror*, *aemcdn*
* Placer sur la liste autorisée Si les adresses IP requises ont été réduites et que les journaux ne sont toujours pas diffusés, vérifiez qu’il n’existe aucune règle de pare-feu appliquant la validation du jeton Splunk. Fastly effectue une étape de validation initiale dans laquelle un jeton Splunk non valide est délibérément envoyé. Si votre pare-feu est défini pour arrêter les connexions avec des jetons Splunk non valides, le processus de validation échoue, empêchant Fastly de diffuser des journaux vers votre instance Splunk.

>[!NOTE]
>
> [En cas de migration](#legacy-migration) du transfert de journal hérité vers ce modèle en libre-service, les valeurs du champ `sourcetype` envoyées à votre index Splunk peuvent avoir changé. Ajustez-les en conséquence.

### Logique Sumo {#sumologic}

Le transfert de journal vers Sumo Logic prend en charge les journaux AEM et Dispatcher ; les journaux CDN ne sont pas encore pris en charge.

Lors de la configuration de la logique Sumo pour l’ingestion de données, une « adresse HTTP Source » s’affiche, qui fournit l’hôte, l’URI du destinataire et la clé privée dans une seule chaîne.  Par exemple :

`https://collectors.de.sumologic.com/receiver/v1/http/ZaVnC...`

Vous devez copier la dernière section de l’URL (sans la `/` précédente) et l’ajouter en tant que [Variable d’environnement secrète Cloud Manager](/help/operations/config-pipeline.md#secret-env-vars) comme décrit dans la section [Configuration](#setup) ci-dessus, puis référencer cette variable dans votre configuration.  Un exemple est fourni ci-dessous.

```yaml
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  sumologic:
    default:
      enabled: true
      collectorURL: "https://collectors.de.sumologic.com/receiver/v1/http"
      privateKey: "${{SUMOLOGIC_PRIVATE_KEY}}"
      index: "aem-logs"
```

>[!NOTE]
> Vous aurez besoin d&#39;un abonnement Sumo Logic Enterprise pour profiter de la fonctionnalité de champ « index ».  Les journaux des abonnements qui ne sont pas des abonnements d’entreprise seront acheminés vers la partition `sumologic_default` en standard.  Voir la [Documentation sur le partitionnement de la logique Sumo](https://help.sumologic.com/docs/search/optimize-search-partitions/) pour plus d’informations.

## Formats d&#39;entrée de journal {#log-formats}

Voir [Journalisation pour AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md) pour le format de chaque type de journal respectif (journaux CDN et journaux AEM, y compris Apache/Dispatcher).

Étant donné que les journaux de plusieurs programmes et environnements peuvent être transférés vers la même destination de journalisation, en plus de la sortie décrite dans l’article de journalisation, les propriétés suivantes seront incluses dans chaque entrée de journal :

* aem_env_id
* aem_env_type
* aem_program_id
* aem_tier

Par exemple, les propriétés peuvent avoir les valeurs suivantes :

```text
aem_env_id: 1242
aem_env_type: dev
aem_program_id: 12314
aem_tier: author
```

## Migration à partir du transfert de journal hérité {#legacy-migration}

Avant que la configuration du transfert du journal ne soit réalisée via un modèle en libre-service, il était demandé aux clients d’ouvrir des tickets d’assistance, où Adobe lancerait l’intégration.

Les clients qui ont été configurés de cette manière par Adobe sont invités à s’adapter au modèle en libre-service à leur convenance. Il existe plusieurs raisons d’effectuer cette transition :

* Un nouvel environnement (par exemple, un nouvel environnement de développement ou un nouvel outil RDE) a été configuré.
* Modifications de votre point d’entrée Splunk existant ou de vos informations d’identification.
* Adobe avait configuré le transfert de vos journaux avant que les journaux CDN ne soient disponibles et que vous souhaitiez recevoir les journaux CDN.
* Une décision consciente de s’adapter de manière proactive au modèle en libre-service afin que votre entreprise dispose des connaissances nécessaires avant même qu’un changement sensible au facteur temps ne soit nécessaire.

Une fois prêt à migrer, configurez simplement le fichier YAML comme décrit dans les sections précédentes. Utilisez le pipeline de configuration Cloud Manager pour effectuer un déploiement dans chacun des environnements où la configuration doit être appliquée.

Il est recommandé, mais pas obligatoire, de déployer une configuration sur tous les environnements afin qu’ils soient tous en libre-service. Dans le cas contraire, vous pouvez oublier les environnements qui ont été configurés par Adobe par rapport à ceux qui ont été configurés en libre-service.

>[!NOTE]
>
>Les valeurs du champ `sourcetype` envoyées à votre index Splunk peuvent avoir changé, ajustez-les en conséquence.
>
>Lorsque le transfert de journal est déployé dans un environnement précédemment configuré par le support Adobe, vous pouvez recevoir des journaux en double pendant quelques heures au maximum. Cela finira par se résoudre automatiquement.
