---
title: Connexion à AEM as a Cloud Service
description: Découvrez comment utiliser la journalisation pour AEM as a Cloud Service afin de configurer des paramètres globaux pour le service de journalisation central, des paramètres spécifiques pour les services individuels ou comment demander la journalisation des données.
exl-id: 262939cc-05a5-41c9-86ef-68718d2cd6a9
feature: Log Files, Developing
role: Admin, Architect, Developer
source-git-commit: 5c32a088cf7e334ba6497a595b5176e5389ce9ed
workflow-type: tm+mt
source-wordcount: '2556'
ht-degree: 78%

---

# Connexion à AEM as a Cloud Service {#logging-for-aem-as-a-cloud-service}

La plateforme AEM as a Cloud Service permet aux clients d’inclure du code personnalisé destiné à créer des expériences incomparables pour leurs propres bases de clients. Dans cette optique, le service de journalisation est une fonction essentielle pour déboguer et comprendre l’exécution du code sur le développement local, ainsi que les environnements cloud, en particulier les environnements de développement AEM as a Cloud Service.

Les niveaux de journal et paramètres de journalisation AEM as a Cloud Service sont gérés dans des fichiers de configuration stockés au sein du projet AEM dans Git, et déployés dans le cadre du projet AEM via Cloud Manager. La journalisation dans AEM as a Cloud Service peut être divisée en trois ensembles logiques :

* La journalisation au niveau de l’application AEM.
* La journalisation de serveur web Apache HTTPD/Dispatcher au niveau Publication.
* La journalisation sur le réseau CDN, qui, comme son nom l’indique, effectue la journalisation sur le réseau CDN.

## Journalisation AEM {#aem-logging}

La journalisation au niveau de l’application AEM est gérée par trois journaux :

1. Les journaux Java AEM, qui consignent les instructions de journalisation Java pour l’application AEM.
1. Les journaux de requêtes HTTP, qui consignent les informations sur les requêtes HTTP et les réponses fournies par AEM
1. Les journaux d’accès HTTP, qui consignent les informations résumées et les requêtes HTTP diffusées par AEM

>[!NOTE]
>
>Les requêtes HTTP diffusées à partir du cache Dispatcher du niveau Publication ou du réseau de diffusion de contenu en amont ne sont pas reflétées dans ces journaux

## Journalisation Java AEM {#aem-java-logging}

AEM as a Cloud Service donne accès aux instructions de journal Java. Les développeurs d’applications pour AEM doivent suivre les bonnes pratiques générales en matière de consignation pour Java, en consignant les instructions pertinentes concernant l’exécution du code personnalisé, aux niveaux de journal suivants :

<table>
<tr>
<td>
<b>Environnement AEM</b></td>
<td>
<b>Niveau de journal</b></td>
<td>
<b>Description</b></td>
<td>
<b>Disponibilité des instructions de journal</b></td>
</tr>
<tr>
<td>
Développement</td>
<td>
DEBUG</td>
<td>
Décrit ce qui se passe dans l’application.<br>
Lorsque la journalisation DEBUG est active, les instructions fournissant une image claire des activités survenues ainsi que les paramètres clés qui affectent le traitement sont consignés.</td>
<td>
<ul>
<li> Développement local</li>
<li>Développement</li>
</ul></td>
</tr>
<tr>
<td>
Évaluation</td>
<td>
WARN</td>
<td>
Décrit les conditions susceptibles de devenir des erreurs.<br>
Lorsque la journalisation WARN est active, seules les instructions indiquant des conditions qui s’approchent de performances sous-optimales sont consignées.</td>
<td>
<ul>
<li> Développement local</li>
<li>Développement</li>
<li>Évaluation</li>
</ul></td>
</tr>
<tr>
<td>
Production</td>
<td>
ERROR</td>
<td>
Décrit les conditions qui indiquent un échec et doivent être résolues.<br>
Lorsque la journalisation ERROR est active, seules les instructions indiquant des échecs sont consignées. Les instructions de journal ERROR indiquent un problème grave qui doit être résolu le plus tôt possible.</td>
<td>
<ul>
<li> Développement local</li>
<li>Développement</li>
<li>Évaluation</li>
<li>Production</li>
</ul></td>
</tr>
</table>

Bien que la journalisation Java prenne en charge plusieurs autres niveaux de granularité de la journalisation, nous recommandons d’utiliser les trois niveaux décrits ci-dessus pour AEM as a Cloud Service.

Les niveaux de journalisation AEM sont définis par type d’environnement via la configuration OSGi, qui à leur tour sont validés dans Git, et déployés sur AEM as a Cloud Service via Cloud Manager. C’est pourquoi il est préférable de conserver des instructions de journal cohérentes et bien connues pour les types d’environnements, afin de s’assurer que les journaux disponibles par l’intermédiaire d’AEM as a Cloud Service sont disponibles au niveau de journal optimal sans avoir à redéployer l’application avec la configuration de niveau de journal mise à jour.

>[!NOTE]
>
>Pour garantir une surveillance efficace des environnements client, ne modifiez pas le niveau de journalisation par défaut. En outre, ne modifiez pas le format de journalisation par défaut. La sortie du journal doit rester redirigée vers les fichiers par défaut. Voir [la section ci-dessous](#configuration-loggers) pour obtenir des instructions spécifiques.

**Exemple de sortie de journal**

```
22.06.2020 18:33:30.120 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *ERROR* [qtp501076283-1809] io.prometheus.client.dropwizard.DropwizardExports Failed to get value from Gauge
22.06.2020 18:33:30.229 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [qtp501076283-1805] org.apache.sling.auth.core.impl.SlingAuthenticator getAnonymousResolver: Anonymous access not allowed by configuration - requesting credentials
22.06.2020 18:33:30.370 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [73.91.59.34 [1592850810364] GET /libs/granite/core/content/login.html HTTP/1.1] org.apache.sling.i18n.impl.JcrResourceBundle Finished loading 0 entries for 'en_US' (basename: <none>) in 4ms
22.06.2020 18:33:30.372 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [FelixLogListener] org.apache.sling.i18n Service [5126, [java.util.ResourceBundle]] ServiceEvent REGISTERED
22.06.2020 18:33:30.372 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *WARN* [73.91.59.34 [1592850810364] GET /libs/granite/core/content/login.html HTTP/1.1] libs.granite.core.components.login.login$jsp j_reason param value 'unknown' cannot be mapped to a valid reason message: ignoring
```

**Format du journal**

<table>
<tbody>
<tr>
<td>Date et heure</td>
<td>29.04.2020 21:50:13.398</td>
</tr>
<tr>
<td>ID du nœud AEM as a Cloud Service</td>
<td>[cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]</td>
</tr>
<tr>
<td>Niveau de journal</td>
<td>DEBUG</td>
</tr>
<tr>
<td>Thread</td>
<td>qtp2130572036-1472</td>
</tr>
<tr>
<td>Classe Java</td>
<td>com.example.approval.workflow.impl.CustomApprovalWorkflow</td>
</tr>
<tr>
<td>Message du journal</td>
<td>Aucun approbateur spécifié, utilisation par défaut de [groupe d’utilisateurs Approbateurs du contenu créatif]</td>
</tr>
</tbody>
</table>

### Enregistreurs de configuration {#configuration-loggers}

Les journaux Java AEM sont définis en tant que configuration OSGi et ciblent par conséquent des environnements AEM as a Cloud Service spécifiques en utilisant des dossiers en mode d’exécution.

Configurez la journalisation Java pour des packages Java personnalisés via des configurations OSGi pour Sling LogManager Factory. Trois propriétés de configuration sont prises en charge :

| Propriété de configuration OSGi | Description |
|---|---|
| `org.apache.sling.commons.log.names` | Packages Java pour lesquels collecter les instructions de journal. |
| `org.apache.sling.commons.log.level` | Niveau de journalisation auquel consigner les packages Java, spécifié par `org.apache.sling.commons.log.names` |

La modification d’autres propriétés de configuration OSGi LogManager peut entraîner des problèmes de disponibilité dans AEM as a Cloud Service.

Comme indiqué dans une section précédente, pour garantir une surveillance efficace des environnements client :
* Le niveau de journal de la configuration de journal par défaut d’AEM (configuration de journalisation Apache Sling) ne doit pas être modifié à partir de sa valeur par défaut « INFO ».
* Il est acceptable de définir les niveaux de journal sur DEBUG pour des packages individuels de code de produit (à l’aide d’instances de la configuration OSGi « Configuration de l’enregistreur de journalisation Apache Sling »), mais utilisez-le avec parcimonie afin d’éviter une dégradation des performances et de restaurer les informations INFO lorsqu’elles ne sont plus nécessaires.
* Il est acceptable d’ajuster les niveaux de journal pour le code développé par le client.
* Tous les journaux (tant pour le code de produit AEM que pour le code développé par le client) doivent conserver le format de journalisation par défaut.
* La sortie du journal doit rester redirigée vers le fichier par défaut « logs/error.log ».

À cette fin, aucune modification ne doit être apportée aux propriétés OSGi suivantes :
* **Configuration du journal Apache Sling** (PID : `org.apache.sling.commons.log.LogManager`) - *toutes les propriétés*
* **Configuration de l’enregistreur de journaux Apache Sling** (PID d’usine : `org.apache.sling.commons.log.LogManager.factory.config`)
   * `org.apache.sling.commons.log.file`
   * `org.apache.sling.commons.log.pattern`

Vous trouverez ci-dessous des exemples de configurations de journalisation recommandées (à l’aide de l’espace réservé de package Java `com.example`) pour les trois types d’environnements AEM as a Cloud Service.

### Développement {#development}

/apps/my-app/config/org.apache.sling.commons.log.LogManager.factory.config-example.cfg.json

```
{
    "org.apache.sling.commons.log.names": ["com.example"],
    "org.apache.sling.commons.log.level": "debug"
    "org.apache.sling.commons.log.file": "logs/error.log"
}
```

### Évaluation {#stage}

/apps/my-app/config.stage/org.apache.sling.commons.log.LogManager.factory.config-example.cfg.json

```
{
    "org.apache.sling.commons.log.names": ["com.example"],
    "org.apache.sling.commons.log.level": "warn"
    "org.apache.sling.commons.log.file": "logs/error.log"
}
```

### Production {#productiomn}

/apps/my-app/config.prod/org.apache.sling.commons.log.LogManager.factory.config-example.cfg.json

```
{
    "org.apache.sling.commons.log.names": ["com.example"],
    "org.apache.sling.commons.log.level": "error"
    "org.apache.sling.commons.log.file": "logs/error.log"
}
```

## Journalisation des requêtes HTTP AEM {#aem-http-request-logging}

La journalisation des requêtes HTTP dans AEM as a Cloud Service fournit des informations sur les requêtes HTTP envoyées à AEM et leurs réponses HTTP par ordre d’arrivée. Ce journal permet de comprendre les requêtes HTTP envoyées à AEM ainsi que l’ordre dans lequel elles sont traitées et reçoivent une réponse.

La clé pour comprendre ce journal est de mapper les paires de requête HTTP et réponse selon leur ID, identifié par la valeur numérique entre crochets. Souvent, d’autres requêtes HTTP et réponses correspondantes sont intercalées entre elles dans le journal.

**Exemple de journal**

```
29/Apr/2020:19:14:21 +0000 [137] > POST /conf/global/settings/dam/adminui-extension/metadataprofile/ HTTP/1.1 [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
...
29/Apr/2020:19:14:22 +0000 [139] > GET /mnt/overlay/dam/gui/content/processingprofilepage/metadataprofiles/editor.html/conf/global/settings/dam/adminui-extension/metadataprofile/main HTTP/1.1 [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
...
29/Apr/2020:19:14:21 +0000 [137] <- 201 text/html 111ms [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
...
29/Apr/2020:19:14:22 +0000 [139] <- 200 text/html;charset=utf-8 637ms [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
```

**Format du journal**

<table>
<tbody>
<tr>
<td>Date et heure</td>
<td>29/Apr/2020:19:14:21 +0000</td>
</tr>
<tr>
<td>ID de paire de requête/réponse</td>
<td><code>[137]</code></td>
</tr>
<tr>
<td>Méthode HTTP</td>
<td>POST</td>
</tr>
<tr>
<td>URL</td>
<td>/conf/global/settings/dam/adminui-extension/metadataprofile/</td>
</tr>
<tr>
<td>Protocole</td>
<td>HTTP/1.1
</td>
</tr>
<tr>
<td>ID du nœud AEM as a Cloud Service</td>
<td>[cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]</td>
</tr>
</tbody>
</table>

### Configuration du journal {#configuring-the-log}

Le journal des requêtes HTTP AEM n’est pas configurable dans AEM as a Cloud Service.

## Journalisation des accès HTTP AEM {#aem-http-access-logging}

La journalisation des accès HTTP dans AEM as a Cloud Service affiche les requêtes HTTP par ordre d’arrivée. Chaque entrée de journal représente la requête HTTP qui accède à AEM.

Ce journal est utile pour comprendre rapidement quelles requêtes HTTP sont envoyées à AEM, si elles réussissent (en examinant le code de statut de la réponse HTTP qui l’accompagne) et combien de temps la requête HTTP a duré. Ce journal peut également servir à déboguer une activité d’utilisateur spécifique en filtrant les entrées du journal par utilisateurs.

**Exemple de sortie de journal**

```
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/granite/ui/references/clientlibs/references.lc-5188e85840c529149e6cd29d94e74ad5-lc.min.css HTTP/1.1" 200 1141 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/dam/gui/coral/components/admin/customthumb/clientlibs.lc-60e4443805c37afa0c74b674b141f1df-lc.min.css HTTP/1.1" 200 809 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/dam/gui/coral/components/admin/metadataeditor/clientlibs/metadataeditor.lc-4a2226d8232f8b7ab27d24820b9ddd64-lc.min.js HTTP/1.1" 200 7965 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
```

| ID du nœud AEM as a Cloud Service | cm-p1235-e2644-aem-author-59555cb5b8-8kgr2 |
|---|---|
| Adresse IP du client | - |
| User | myuser@adobe.com |
| Date et heure | 30/Apr/2020:17:37:14 +0000 |
| Méthode HTTP | GET |
| URL | `/libs/granite/ui/references/clientlibs/references.lc-5188e85840c529149e6cd29d94e74ad5-lc.min.css` |
| Protocole | HTTP/1.1 |
| Statut de réponse HTTP | 200 |
| Taille du corps de réponse en octets | 1141 |
| Référent | `"https://author-p1234-e4444.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/wknd/en/adventures/surf-camp-in-costa-rica/adobestock_266405335.jpeg&_charset_=utf8"` |
| Agent utilisateur | `"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"` |

### Configuration du journal d’accès HTTP {#configuring-the-http-access-log}

Le journal des accès HTTP n’est pas configurable dans AEM as a Cloud Service.

## Journalisation de serveur web Apache et de Dispatcher {#apache-web-server-and-dispatcher-logging}

AEM as a Cloud Service fournit trois journaux pour les serveurs web Apache et la couche Dispatcher au niveau Publication :

* Journal des accès au serveur web Apache HTTPD
* Journal des erreurs du serveur web Apache HTTPD
* Journal de Dispatcher

Ces journaux ne sont disponibles que pour le niveau Publication.

Cet ensemble de journaux fournit des informations sur les requêtes HTTP envoyées au niveau Publication d’AEM as a Cloud Service avant que celles-ci n’atteignent l’application AEM. Il est important de comprendre cela, car, dans l’idéal, la plupart des requêtes HTTP envoyées aux serveurs de niveau Publication sont servies par du contenu mis en cache par le serveur web Apache HTTPD et le Dispatcher AEM, et n’atteignent jamais l’application AEM elle-même. Il n’existe donc aucune instruction de journal pour ces requêtes dans les journaux Java, de requêtes ou des accès d’AEM.

### Journal des accès au serveur web Apache HTTPD {#apache-httpd-web-server-access-log}

Le journal des accès au serveur web Apache HTTPD fournit des instructions pour chaque requête HTTP qui atteint le serveur web/Dispatcher du niveau Publication. Les requêtes diffusées à partir d’un réseau CDN en amont ne sont pas reflétées dans ces journaux.

Consultez les informations sur le format du journal des erreurs dans la [documentation officielle d’Apache](https://httpd.apache.org/docs/2.4/logs.html#accesslog).

**Exemple de sortie de journal**

```
cm-p1234-e5678-aem-publish-b86c6b466-qpfvp - - 17/Jul/2020:09:14:41 +0000  "GET /etc.clientlibs/wknd/clientlibs/clientlib-site/resources/images/favicons/favicon-32.png HTTP/1.1" 200 715 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:78.0) Gecko/20100101 Firefox/78.0"
cm-p1234-e5678-aem-publish-b86c6b466-qpfvp - - 17/Jul/2020:09:14:41 +0000  "GET /etc.clientlibs/wknd/clientlibs/clientlib-site/resources/images/favicons/favicon-512.png HTTP/1.1" 200 9631 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:78.0) Gecko/20100101 Firefox/78.0"
cm-p1234-e5678-aem-publish-b86c6b466-qpfvp - - 17/Jul/2020:09:14:42 +0000  "GET /etc.clientlibs/wknd/clientlibs/clientlib-site/resources/images/country-flags/US.svg HTTP/1.1" 200 810 "https://publish-p6902-e30226.adobeaemcloud.com/content/wknd/us/en.html" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:78.0) Gecko/20100101 Firefox/78.0"
```

**Format du journal**

<table>
<tbody>
<tr>
<td>ID du nœud AEM as a Cloud Service</td>
<td>cm-p1234-e26813-aem-publish-5c787687c-lqlxr</td>
</tr>
<tr>
<td>Adresse IP du client</td>
<td>-</td>
</tr>
<tr>
<td>User</td>
<td>-</td>
</tr>
<tr>
<td>Date et heure</td>
<td>01/May/2020:00:09:46 +0000</td>
</tr>
<tr>
<td>Méthode HTTP</td>
<td>GET</td>
</tr>
<tr>
<td>URL</td>
<td>/content/example.html</td>
</tr>
<tr>
<td>Protocole</td>
<td>HTTP/1.1</td>
</tr>
<tr>
<td>Statut de réponse HTTP</td>
<td>200</td>
</tr>
<tr>
<td>Taille</td>
<td>310</td>
</tr>
<tr>
<td>Référent</td>
<td>-</td>
</tr>
<tr>
<td>Agent utilisateur</td>
<td>"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"</td>
</tr>
</tbody>
</table>

### Configuration du journal des accès au serveur web Apache HTTPD {#configuring-the-apache-httpd-webs-server-access-log}

Ce journal n’est pas configurable dans AEM as a Cloud Service.

## Journal des erreurs du serveur web Apache HTTPD {#apache-httpd-web-server-error-log}

Le journal des erreurs du serveur web Apache HTTPD fournit des instructions pour chaque erreur dans le serveur web/Dispatcher du niveau Publication.

Consultez les informations sur le format du journal des erreurs dans la [documentation officielle d’Apache](https://httpd.apache.org/docs/2.4/logs.html#errorlog).

**Exemple de sortie de journal**

```
Fri Jul 17 02:19:48.093820 2020 [mpm_worker:notice] [pid 1:tid 140272153361288] [cm-p1234-e30226-aem-publish-b86c6b466-b9427] AH00292: Apache/2.4.43 (Unix) Communique/4.3.4-20200424 mod_qos/11.63 configured -- resuming normal operations
Fri Jul 17 02:19:48.093874 2020 [core:notice] [pid 1:tid 140272153361288] [cm-p1234-e30226-aem-publish-b86c6b466-b9427] AH00094: Command line: 'httpd -d /etc/httpd -f /etc/httpd/conf/httpd.conf -D FOREGROUND -D ENVIRONMENT_PROD'
Fri Jul 17 02:29:34.517189 2020 [mpm_worker:notice] [pid 1:tid 140293638175624] [cm-p1234-e30226-aem-publish-b496f64bf-5vckp] AH00295: caught SIGTERM, shutting down
```

**Format du journal**

<table>
<tbody>
<tr>
<td>Date et heure</td>
<td>Fri Jul 17 02:16:42.608913 2020</td>
</tr>
<tr>
<td>Niveau d’événement</td>
<td>[mpm_worker:notice]</td>
</tr>
<tr>
<td>ID du processus</td>
<td>[pid 1:tid 140715149343624]</td>
</tr>
<tr>
<td>Nom du pod</td>
<td>[cm-p1234-e56789-aem-publish-b86c6b466-qpfvp]</td>
</tr>
<tr>
<td>Message</td>
<td>AH00094: Command line: ’httpd -d /etc/httpd -f /etc/httpd/conf/httpd.conf -D FOREGROUND -D </td>
</tr>
</tbody>
</table>

### Configuration du journal des erreurs du serveur web Apache HTTPD {#configuring-the-apache-httpd-web-server-error-log}

Les niveaux de journal mod_rewrite sont définis par la variable REWRITE_LOG_LEVEL dans le fichier `conf.d/variables/global.var`.

Il peut être défini sur Error, Warn, Info, Debug et Trace1 à Trace8, avec la valeur par défaut Warn. Pour déboguer vos règles de réécriture, il est recommandé de passer au niveau de journal trace2. Il est recommandé de déboguer les règles de réécriture à l’aide de [Dispatcher SDK](../../dispatcher/validation-debug.md). Le niveau maximal de journalisation pour AEM as a Cloud Service est `debug`. Il n’est donc actuellement pas possible de déboguer efficacement les règles de réécriture dans le cloud.

Pour plus d’informations, consultez la [documentation du module mod_rewrite](https://httpd.apache.org/docs/current/mod/mod_rewrite.html#logging).

Pour définir le niveau de journal par environnement, utilisez la branche conditionnelle appropriée dans le fichier global.var, comme décrit ci-dessous :

```
Define REWRITE_LOG_LEVEL debug

<IfDefine ENVIRONMENT_STAGE>
  ...
  Define REWRITE_LOG_LEVEL warn
  ...
</IfDefine>
<IfDefine ENVIRONMENT_PROD>
  ...
  Define REWRITE_LOG_LEVEL error
  ...
</IfDefine>
```

## Journal de Dispatcher {#dispatcher-log}

**Exemple**

```
[17/Jul/2020:23:48:06 +0000] [I] [cm-p12904-e25628-aem-publish-6c5f7c9dbd-mzcvr] "GET /content/wknd/us/en/adventures.html" - 475ms [publishfarm/0] [action miss] "publish-p12904-e25628.adobeaemcloud.com"
[17/Jul/2020:23:48:07 +0000] [I] [cm-p12904-e25628-aem-publish-6c5f7c9dbd-mzcvr] "GET /content/wknd/us/en/adventures/climbing-new-zealand/_jcr_content/root/responsivegrid/carousel/item_1571266094599.coreimg.jpeg/1473680817282/sport-climbing.jpeg" 302 10ms [publishfarm/0] [action none] "publish-p12904-e25628.adobeaemcloud.com"
[17/Jul/2020:23:48:07 +0000] [I] [cm-p12904-e25628-aem-publish-6c5f7c9dbd-mzcvr] "GET /content/wknd/us/en/adventures/ski-touring-mont-blanc/_jcr_content/root/responsivegrid/carousel/item_1571168419252.coreimg.jpeg/1572047288089/adobestock-238230356.jpeg" 302 11ms [publishfarm/0] [action none] "publish-p12904-e25628.adobeaemcloud.com"
```

**Format du journal**

<table>
<tbody>
<tr>
<td>Date et heure</td>
<td>[17/Jul/2020:23:48:16 +0000]</td>
</tr>
<tr>
<td>Nom du pod</td>
<td>[cm-p12904-e25628-aem-publish-6c5f7c9dbd-mzcvr]</td>
</tr>
<tr>
<td>Protocole</td>
<td>GET</td>
</tr>
<tr>
<td>URL</td>
<td>/content/experience-fragments/wknd/language-masters/en/contributors/sofia-sjoeberg/master/_jcr_content/root/responsivegrid/image.coreimg.100.500.jpeg/1572236359031/ayo-ogunseinde-237739.jpeg</td>
</tr>
<tr>
<td>Code de statut de réponse de Dispatcher</td>
<td>/content/experience-fragments/wknd/language-masters/en/contributors/sofia-sjoeberg/master/_jcr_content/root/responsivegrid/image.coreimg.100.500.jpeg/1572236359031/ayo-ogunseinde-237739.jpeg</td>
</tr>
<tr>
<td>Durée</td>
<td>1949ms</td>
</tr>
<tr>
<td>Ferme</td>
<td>[publishfarm/0]</td>
</tr>
<tr>
<td>Statut du cache</td>
<td>[action miss]</td>
</tr>
<tr>
<td>Hôte</td>
<td>"publish-p12904-e25628.adobeaemcloud.com"</td>
</tr>
</tbody>
</table>

### Configuration du journal des erreurs de Dispatcher {#configuring-the-dispatcher-error-log}

Les niveaux de journal de Dispatcher sont définis par la variable DISP_LOG_LEVEL dans le fichier `conf.d/variables/global.var`.

Il peut être défini sur Error, Warn, Info, Debug et Trace1, avec la valeur par défaut Warn.

Bien que la journalisation de Dispatcher prenne en charge plusieurs autres niveaux de granularité de la journalisation, nous recommandons d’utiliser les niveaux décrits ci-dessous pour AEM as a Cloud Service.

Pour définir le niveau de journal par environnement, utilisez la branche conditionnelle appropriée dans le fichier `global.var`, comme décrit ci-dessous :

```
Define DISP_LOG_LEVEL debug

<IfDefine ENVIRONMENT_STAGE>
  ...
  Define DISP_LOG_LEVEL warn
  ...
</IfDefine>
<IfDefine ENVIRONMENT_PROD>
  ...
  Define DISP_LOG_LEVEL error
  ...
</IfDefine>
```

>[!NOTE]
>
>Pour les environnements AEM as a Cloud Service, le débogage est le niveau maximal de verbosité. Le niveau de journalisation de trace n’étant pas pris en charge, évitez de le définir lorsque vous travaillez dans des environnements cloud.

## Journal CDN {#cdn-log}

AEM as a Cloud Service permet d’accéder aux journaux du réseau CDN, qui sont utiles pour les cas d’utilisation, y compris l’optimisation du taux d’accès au cache. Le format de journal du réseau CDN ne peut pas être personnalisé et il n’existe aucun concept de définition sur différents modes tels que info, warn ou error.

**Exemple**

```
{
"timestamp": "2023-05-26T09:20:01+0000",
"ttfb": 19,
"cli_ip": "147.160.230.112",
"cli_country": "CH",
"rid": "974e67f6",
"req_ua": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/14.0.3 Safari/605.1.15",
"host": "example.com",
"url": "/content/hello.png",
"method": "GET",
"res_ctype": "image/png",
"cache": "PASS",
"status": 200,
"res_age": 0,
"pop": "PAR",
"rules": "match=Enable-SQL-Injection-and-XSS-waf-rules-globally,waf=SQLI,action=blocked"
}
```

**Format du journal**

Les journaux du réseau CDN sont distincts des autres journaux en ce qu’ils respectent un format json.

| **Nom du champ** | **Description** |
|---|---|
| *timestamp* | Heure à laquelle la requête a démarré, après l’arrêt du TLS |
| *ttfb* | Abréviation de *Time To First Byte*. Intervalle entre le démarrage de la requête et le début de la diffusion du corps de la réponse. |
| *cli_ip* | Adresse IP du client ou de la cliente. |
| *cli_country* | Code de pays alpha-2 à deux lettres [ISO 3166-1](https://fr.wikipedia.org/wiki/ISO_3166-1) pour le pays du client ou de la cliente. |
| *rid* | Valeur de l’en-tête de requête utilisé pour identifier la requête de manière unique. |
| *req_ua* | Agent utilisateur responsable de l’exécution d’une requête HTTP donnée. |
| *host* | Autorité à laquelle la requête est destinée. |
| *url* | Chemin d’accès complet, y compris les paramètres de requête. |
| *method* | Méthode HTTP envoyée par le client ou la cliente, telle que GET ou POST. |
| *res_ctype* | Type de contenu utilisé pour indiquer le type de média d’origine de la ressource. |
| *cache* | État du cache. Les valeurs possibles sont HIT, MISS ou PASS |
| *status* | Code d’état HTTP sous la forme d’une valeur d’entier. |
| *res_age* | Durée (en secondes) pendant laquelle une réponse a été mise en cache (dans tous les nœuds). |
| *pop* | Centre de données du serveur de cache de réseau CDN. |
| *rules* | Les noms des [règles de filtrage du trafic](/help/security/traffic-filter-rules-including-waf.md) et indicateurs WAF correspondants, indiquant également si la correspondance a entraîné un blocage. Vide si aucune règle ne correspond. |

Les journaux du réseau CDN peuvent être étendus avec vos propres propriétés à l’aide de [transformations requête/réponse](/help/implementing/dispatcher/cdn-configuring-traffic.md#logproperty).

## Comment accéder aux journaux {#how-to-access-logs}

### Environnements cloud {#cloud-environments}

Les journaux AEM as a Cloud Service pour les services cloud sont accessibles par téléchargement via l’interface de Cloud Manager ou en affichant leurs dernières lignes à l’aide de l’interface de ligne de commande Adobe I/O. Pour plus d’informations, voir la [documentation sur la journalisation de Cloud Manager](/help/implementing/cloud-manager/manage-logs.md).

### Journaux pour les régions de publication supplémentaires {#logs-for-additional-publish-regions}

Si d’autres régions de publication sont activées pour un environnement particulier, les journaux de chaque région peuvent être téléchargés à partir de Cloud Manager, comme mentionné ci-dessus.

Les journaux AEM et les journaux du Dispatcher pour les régions de publication supplémentaires spécifient la région dans les 3 premières lettres après l’identifiant d’environnement, comme illustré par **nld2** dans l’exemple ci-dessous, qui fait référence à une instance de publication AEM supplémentaire située aux Pays-Bas :

```
cm-p7613-e12700-nld2-aem-publish-bcbb77549-5qmmt 127.0.0.1 - 07/Nov/2023:23:57:11 +0000 "HEAD /libs/granite/security/currentuser.json HTTP/1.1" 200 - "-" "Java/11.0.19"
```

### SDK local {#local-sdk}

Le SDK AEM as a Cloud Service fournit des fichiers journaux pour la prise en charge du développement local.

Les journaux AEM se trouvent dans le dossier `crx-quickstart/logs`, où vous pouvez afficher les journaux suivants :

* Journal Java AEM : `error.log`
* Journal des requêtes HTTP AEM : `request.log`
* Journal des accès HTTP AEM : `access.log`

Les journaux de couche Apache, y compris de Dispatcher, se trouvent dans le conteneur Docker qui contient Dispatcher. Consultez la [documentation de Dispatcher](/help/implementing/dispatcher/disp-overview.md) pour savoir comment le démarrer.

Pour récupérer les journaux :

1. Sur la ligne de commande, tapez `docker ps` afin de répertorier vos conteneurs.
1. Pour vous connecter au conteneur, tapez « `docker exec -it <container> /bin/sh` », où `<container>` est l’identifiant de conteneur Dispatcher de l’étape précédente.
1. Accédez à la racine du cache sous `/mnt/var/www/html`.
1. Les journaux se trouvent sous `/etc/httpd/logs`.
1. Inspectez les journaux : ils sont accessibles sous le dossier XYZ, où vous pouvez afficher les journaux suivants :
   * Journal des accès au serveur web Apache HTTPD – `httpd_access.log`
   * Journaux des erreur du serveur web Apache HTTPD – `httpd_error.log`
   * Journaux de Dispatcher – `dispatcher.log`

Les journaux sont également directement imprimés dans la sortie du terminal. La plupart du temps, ces journaux doivent être en mode DEBUG, ce qui peut être effectué en transmettant le niveau Debug comme paramètre lors de l’exécution de Docker. Par exemple :

`DISP_LOG_LEVEL=Debug ./bin/docker_run.sh out docker.for.mac.localhost:4503 8080`

## Débogage dans les environnements de production et d’évaluation {#debugging-production-and-stage}

Dans des circonstances exceptionnelles, il est nécessaire de modifier les niveaux de journalisation pour qu’ils soient plus précis dans les environnements d’évaluation ou de production.

Bien que cela soit possible, cela requiert des modifications des niveaux de journal dans les fichiers de configuration dans Git (en passant de Warn et Error à Debug), et l’exécution d’un déploiement sur AEM as a Cloud Service pour enregistrer ces modifications de configuration auprès des environnements.

Selon le trafic et la quantité d’instructions de journal écrites par Debug, cela peut avoir un impact négatif sur les performances de l’environnement. Il est donc recommandé que les modifications apportées aux niveaux de débogage Stage (pour l’environnement d’évaluation) et Production soient :

* effectuées judicieusement, et uniquement lorsque cela est absolument nécessaire ;
* annulées le plus tôt possible pour redéployer les niveaux appropriés.

## Transfert de journaux {#log-forwarding}

Bien que les journaux puissent être téléchargés à partir de Cloud Manager, certaines organisations estiment qu’il est bénéfique de les transférer vers une destination de journalisation préférée. AEM prend en charge les logs de streaming vers les destinations suivantes :

* Stockage Azure Blob
* Datadog
* HTTPD
* Elasticsearch (et OpenSearch)
* Splunk

Consultez l’article [&#x200B; Transfert de journal &#x200B;](/help/implementing/developing/introduction/log-forwarding.md) pour plus d’informations sur la configuration de cette fonctionnalité.

>[!NOTE]
>
>Le transfert de journal pour les environnements de programme Sandbox n’est pas pris en charge.
