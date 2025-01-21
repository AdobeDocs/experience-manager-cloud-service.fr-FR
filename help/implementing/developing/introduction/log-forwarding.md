---
title: Transfert de journal pour AEM as a Cloud Service
description: Découvrez comment transférer des journaux à des fournisseurs de journalisation dans AEM as a Cloud Service
exl-id: 27cdf2e7-192d-4cb2-be7f-8991a72f606d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 6e91ad839de6094d7f6abd47881dabc6357a80ff
workflow-type: tm+mt
source-wordcount: '1975'
ht-degree: 1%

---

# Transfert de journaux {#log-forwarding}

>[!NOTE]
>
>Le transfert de journal est désormais configuré en libre-service, différent de la méthode héritée qui nécessitait l’envoi d’un ticket d’assistance pour l’Adobe. Pour plus d&#39;informations, consultez la section [Migration](#legacy-migration) si votre transfert de journal a été configuré par Adobe.

Les clients disposant d’une licence auprès d’un fournisseur de journalisation ou qui hébergent un produit de journalisation peuvent faire transférer les journaux AEM (y compris Apache/Dispatcher) et les journaux CDN vers la destination de journalisation associée. AEM as a Cloud Service prend en charge les destinations de journalisation suivantes :

* Stockage Azure Blob
* Datadog
* Elasticsearch ou OpenSearch
* HTTPS
* Splunk

Le transfert de journal est configuré en libre-service en déclarant une configuration dans Git, puis en la déployant via le pipeline de configuration Cloud Manager vers les types d’environnements de RDE, de développement, d’évaluation et de production dans les programmes de production (hors sandbox).

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

1. Créez un fichier nommé `logForwarding.yaml`. Il doit contenir des métadonnées, comme décrit dans l’article [configuration du pipeline](/help/operations/config-pipeline.md#common-syntax) (**kind** doit être défini sur `LogForwarding` et la version doit être définie sur « 1 »), avec une configuration similaire à la suivante (nous utilisons Splunk comme exemple).

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
<html>
<style>
table, th, td {
  border: 1px solid black;
  border-collapse: collapse;
  text-align: center;
}
</style>
<table>
  <tbody>
    <tr>
      <th>Port de destination</th>
      <th>Exigence d’affichage des journaux à partir d’une adresse IP fixe ?</th>
      <th>Mise en réseau avancée nécessaire</th>
      <th>Définition de port LogForwarding.yaml nécessaire</th>
    </tr>
    <tr>
      <td rowspan="2">HTTPS (443)</td>
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
</html>

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

Pour les journaux CDN, vous pouvez placer les adresses IP sur la liste autorisée, comme décrit dans la section [Documentation Fastly - Liste publique d’adresses IP](https://www.fastly.com/documentation/reference/api/utils/public-ip-list/). Si cette liste d’adresses IP partagées est trop volumineuse, pensez à envoyer du trafic vers un serveur https ou un Azure Blob Store (non Adobe) où une logique peut être écrite pour envoyer les journaux d’une adresse IP connue vers leur destination finale.

>[!NOTE]
>Il n’est pas possible que les journaux CDN s’affichent à partir de la même adresse IP que celle à partir de laquelle vos journaux AEM apparaissent. En effet, les journaux sont envoyés directement depuis Fastly et non AEM Cloud Service.

## Consignation de la configuration de destination {#logging-destinations}

Les configurations des destinations de journalisation prises en charge sont répertoriées ci-dessous, avec des considérations spécifiques.

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

#### Journaux AEM de stockage Blob Azure {#azureblob-aem}

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

Considérations :

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

Considérations :

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

Considérations :

* La chaîne d&#39;URL doit inclure **https://** sinon la validation échouera.
* L’URL peut inclure un port. Par exemple, `https://example.com:8443/aem_logs/aem`. Si aucun port n’est inclus dans la chaîne d’URL, le port 443 (port HTTPS par défaut) est supposé.

#### Journaux de réseau CDN HTTPS {#https-cdn}

Les requêtes web (POST) seront envoyées en continu, avec une payload json qui est un tableau d’entrées de journal, avec le format d’entrée de journal décrit sous [Journalisation pour AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md#cdn-log). Des propriétés supplémentaires sont mentionnées dans la section [Formats d’entrée de journal](#log-formats) ci-dessous.

Il existe également une propriété nommée `sourcetype`, qui est définie sur la valeur `aemcdn`.

>[!NOTE]
>
> Avant l’envoi de la première entrée du journal CDN, votre serveur HTTP doit réussir un défi unique : une requête envoyée au chemin d’accès ``/.well-known/fastly/logging/challenge`` doit répondre avec un astérisque ``*`` dans le corps et le code d’état 200.

#### Journaux AEM HTTPS {#https-aem}

Pour les journaux AEM (y compris Apache/Dispatcher), les requêtes web (POST) sont envoyées en continu, avec une payload json qui est un tableau d’entrées de journal, avec les différents formats d’entrée de journal comme décrit dans [Journalisation pour AEM as a Cloud Service](/help/implementing/developing/introduction/logging.md). Des propriétés supplémentaires sont mentionnées dans la section [Formats d’entrée de journal](#log-formats) ci-dessous.

Il existe également une propriété nommée `Source-Type`, qui est définie sur l’une des valeurs suivantes :

* aemaccess
* aemerror
* aemrequest
* aemdispatcher
* aemhttpdaccess
* aemhttpderror

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

Considérations :

* Par défaut, le port est 443. Il peut éventuellement être remplacé par une propriété nommée `port`.
* Le champ sourcetype possède l’une des valeurs suivantes, en fonction du journal spécifique : *aemaccess*, *aemerror*,
  *aemrequest*, *aemdispatcher*, *aemhttpdaccess*, *aemhttpderror*, *aemcdn*
* Placer sur la liste autorisée Si les adresses IP requises ont été réduites et que les journaux ne sont toujours pas diffusés, vérifiez qu’il n’existe aucune règle de pare-feu appliquant la validation du jeton Splunk. Fastly effectue une étape de validation initiale dans laquelle un jeton Splunk non valide est délibérément envoyé. Si votre pare-feu est défini pour arrêter les connexions avec des jetons Splunk non valides, le processus de validation échoue, empêchant Fastly de diffuser des journaux vers votre instance Splunk.

>[!NOTE]
>
> [En cas de migration](#legacy-migration) du transfert de journal hérité vers ce modèle en libre-service, les valeurs du champ `sourcetype` envoyées à votre index Splunk peuvent avoir changé. Ajustez-les en conséquence.

<!--
### Sumo Logic {#sumologic}

   ```yaml
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

Avant que la configuration du transfert du journal ne soit réalisée via un modèle en libre-service, les clients étaient invités à ouvrir des tickets d’assistance, où l’Adobe lancerait l’intégration.

Les clients qui ont été configurés de cette manière par Adobe sont invités à s’adapter au modèle de libre-service à leur convenance. Il existe plusieurs raisons d’effectuer cette transition :

* Un nouvel environnement (par exemple, un nouvel environnement de développement ou un nouvel outil RDE) a été configuré.
* Modifications de votre point d’entrée Splunk existant ou de vos informations d’identification.
* L’Adobe avait configuré votre transfert de journal avant que les journaux CDN ne soient disponibles et que vous souhaitiez recevoir les journaux CDN.
* Une décision consciente de s’adapter de manière proactive au modèle en libre-service afin que votre entreprise dispose des connaissances nécessaires avant même qu’un changement sensible au facteur temps ne soit nécessaire.

Une fois prêt à migrer, configurez simplement le fichier YAML comme décrit dans les sections précédentes. Utilisez le pipeline de configuration Cloud Manager pour effectuer un déploiement dans chacun des environnements où la configuration doit être appliquée.

Il est recommandé, mais pas obligatoire, de déployer une configuration sur tous les environnements afin qu’ils soient tous en libre-service. Dans le cas contraire, vous risquez d’oublier les environnements configurés par Adobe par rapport à ceux configurés en libre-service.

>[!NOTE]
>Les valeurs du champ `sourcetype` envoyées à votre index Splunk peuvent avoir changé, ajustez-les en conséquence.
>
>Lorsque le transfert de journal est déployé dans un environnement précédemment configuré par le support d’Adobe, vous pouvez recevoir des journaux en double pendant quelques heures au maximum. Cela finira par se résoudre automatiquement.
