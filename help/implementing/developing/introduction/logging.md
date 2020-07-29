---
title: Journalisation
description: Découvrez comment configurer des paramètres globaux pour le service de journalisation centrale, des paramètres spécifiques pour les services individuels ou apprenez à demander la journalisation des données.
translation-type: tm+mt
source-git-commit: db0ea2367e8ecf645694a0f33b9f3b99010ec491
workflow-type: tm+mt
source-wordcount: '2212'
ht-degree: 7%

---


# Journalisation {#logging}

La plate-forme AEM as a Cloud Service permet aux clients d’inclure du code personnalisé destiné à créer des expériences incomparables pour leurs propres bases de clients. Dans cette optique, la journalisation est une fonction essentielle pour déboguer et comprendre l&#39;exécution du code sur le développement local, et les environnements de cloud, en particulier l&#39;AEM en tant qu&#39;environnements de développement Cloud Service.

Les niveaux de journalisation et de journalisation AEM sont gérés dans des fichiers de configuration stockés dans le cadre du projet AEM dans Git, et déployés dans le cadre du projet AEM via Cloud Manager. La connexion à AEM en tant que Cloud Service peut être divisée en deux jeux logiques :

* Journalisation des AEM, qui effectue la journalisation au niveau de l&#39;AEM application
* Journalisation du serveur Web/Dispatcher Apache HTTPD, qui effectue la journalisation du serveur Web et du Dispatcher sur le niveau Publier.

## Journalisation des AEM {#aem-loggin}

La journalisation au niveau de l’application AEM est gérée par trois journaux :

1. Journaux Java AEM, qui affichent les instructions de journalisation Java pour l’application AEM.
1. Journaux de requêtes HTTP, qui consignent les informations sur les requêtes HTTP et leurs réponses fournies par AEM
1. Journaux d’accès HTTP, qui consignent les informations résumées et les requêtes HTTP diffusées par AEM

> [!NOTE]
> 
> Les requêtes HTTP diffusées à partir du cache Dispatcher du niveau Publication ou du réseau de diffusion de contenu en amont ne sont pas reflétées dans ces journaux.

## Journalisation Java AEM {#aem-java-logging}

AEM en tant que Cloud Service donne accès aux instructions de journal Java. Les développeurs d&#39;applications pour AEM doivent suivre les meilleures pratiques de consignation Java générales, consigner les instructions pertinentes concernant l&#39;exécution du code personnalisé, aux niveaux de journal suivants :

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
Lorsque la journalisation DEBUG est active, les instructions fournissant une image claire des activités survenues ainsi que les paramètres clés qui affectent le traitement sont consignées.</td>
<td>
<ul>
<li> Développement local</li>
<li>Développement</li>
</ul></td>
</tr>
<tr>
<td>
Scène</td>
<td>
WARN</td>
<td>
Décrit les conditions susceptibles de devenir des erreurs.<br>
Lorsque la journalisation WARN est active, seules les instructions indiquant les conditions qui approchent du sous-optimisme sont consignées.</td>
<td>
<ul>
<li> Développement local</li>
<li>Développement</li>
<li>Scène</li>
</ul></td>
</tr>
<tr>
<td>
Production</td>
<td>
ERREUR</td>
<td>
Décrit les conditions qui indiquent un échec et doivent être résolues.<br>
Lorsque la journalisation ERROR est active, seules les instructions indiquant des échecs sont consignées. Les relevés de journal d'ERREUR indiquent un problème grave qui devrait être résolu le plus tôt possible.</td>
<td>
<ul>
<li> Développement local</li>
<li>Développement</li>
<li>Scène</li>
<li>Production</li>
</ul></td>
</tr>
</table>

Bien que la journalisation Java prenne en charge plusieurs autres niveaux de granularité de la journalisation, AEM en tant que Cloud Service recommande d&#39;utiliser les trois niveaux décrits ci-dessus.

Les niveaux de journalisation AEM sont définis par type d’environnement via la configuration OSGi, qui à son tour est affectée à Git, et déployés via Cloud Manager pour AEM en tant que Cloud Service. C&#39;est pourquoi il est préférable de conserver des instructions de journal cohérentes et bien connues pour les types d&#39;environnements, afin de s&#39;assurer que les journaux disponibles par l&#39;intermédiaire d&#39;AEM comme Cloud Service sont disponibles au niveau de journal optimal sans avoir à redéployer l&#39;application avec la configuration de niveau de journal mise à jour.

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
<td>AEM en tant qu’ID de noeud Cloud Service</td>
<td>[cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]</td>
</tr>
<tr>
<td>Niveau de journalisation</td>
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
<td>Aucun approbateur spécifié, par défaut [ groupe d’utilisateurs Approbateurs créatifs ]</td>
</tr>
</tbody>
</table>

### Journaux de configuration {#configuration-loggers}

AEM journaux Java sont définis en tant que configuration OSGi et, par conséquent, des AEM spécifiques à la cible en tant qu’environnements Cloud Service utilisant des dossiers en mode d’exécution.

Configurez la journalisation java pour les packages Java personnalisés via des configurations OSGi pour la fabrique Sling LogManager. Il existe deux propriétés de configuration prises en charge :

| Propriété de configuration OSGi | Description |
|---|---|
| org.apache.sling.commons.log.names | Packages Java pour lesquels collecter les instructions de journal. |
| org.apache.sling.commons.log.level | Niveau de journal auquel consigner les packages Java, spécifié par org.apache.sling.commons.log.names |

La modification d’autres propriétés de configuration de LogManager OSGi peut entraîner des problèmes de disponibilité dans AEM en tant que Cloud Service.

Vous trouverez ci-dessous des exemples des configurations de journalisation recommandées (à l’aide du package Java d’espace réservé de `com.example`) pour les trois AEM en tant que types d’environnements Cloud Service.

### Développement {#development}

/apps/my-app/config/org.apache.sling.commons.log.LogManager.factory.config-example.cfg.json

```
{
    "org.apache.sling.commons.log.names": ["com.example"],
    "org.apache.sling.commons.log.level": "debug"
}
```

### Scène {#stage}

/apps/my-app/config.stage/org.apache.sling.commons.log.LogManager.factory.config-example.cfg.json

```
{
    "org.apache.sling.commons.log.names": ["com.example"],
    "org.apache.sling.commons.log.level": "warn"
}
```

### Production {#productiomn}

/apps/my-app/config.prod/org.apache.sling.commons.log.LogManager.factory.config-example.cfg.json

```
{
    "org.apache.sling.commons.log.names": ["com.example"],
    "org.apache.sling.commons.log.level": "error"
}
```

## Journalisation des requêtes HTTP AEM {#aem-http-request-logging}

AEM en tant que Cloud Service de la journalisation des requêtes HTTP fournit des informations sur les requêtes HTTP envoyées à AEM et leurs réponses HTTP dans l’ordre du temps. Ce journal permet de comprendre les requêtes HTTP envoyées à AEM et l&#39;ordre dans lequel elles sont traitées et auxquelles elles ont répondu.

La clé pour comprendre ce journal est de mapper les paires requête et réponse HTTP selon leurs ID, identifiés par la valeur numérique entre crochets. Notez que souvent, les requêtes et leurs réponses correspondantes ont d&#39;autres requêtes HTTP et réponses interjonctées entre elles dans le journal.

**Exemple de journal**

```
29/Apr/2020:19:14:21 +0000 [137] -> POST /conf/global/settings/dam/adminui-extension/metadataprofile/ HTTP/1.1 [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
...
29/Apr/2020:19:14:22 +0000 [139] -> GET /mnt/overlay/dam/gui/content/processingprofilepage/metadataprofiles/editor.html/conf/global/settings/dam/adminui-extension/metadataprofile/main HTTP/1.1 [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
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
<td>29/avr/2020:19:14:21 +000</td>
</tr>
<tr>
<td>ID de paire de requêtes/réponses</td>
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
<td>AEM en tant qu’ID de noeud Cloud Service</td>
<td>[cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]</td>
</tr>
</tbody>
</table>

### Configuration du journal {#configuring-the-log}

Le journal des requêtes HTTP AEM n&#39;est pas configurable dans AEM en tant que Cloud Service.

## Journalisation des accès HTTP AEM {#aem-http-access-logging}

AEM en tant que journalisation d’accès HTTP Cloud Service affiche les requêtes HTTP dans l’ordre du temps. Chaque entrée de journal représente la requête HTTP qui accède à AEM.

Ce journal est utile pour comprendre rapidement quelles requêtes HTTP sont envoyées à AEM, si elles réussissent en examinant le code d’état de la réponse HTTP qui l’accompagne et combien de temps la requête HTTP a duré. Ce journal peut également être utile pour déboguer une activité d’utilisateur spécifique en filtrant les entrées du journal par utilisateurs.

**Exemple de sortie de journal**

```
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/granite/ui/references/clientlibs/references.lc-5188e85840c529149e6cd29d94e74ad5-lc.min.css HTTP/1.1" 200 1141 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/dam/gui/coral/components/admin/customthumb/clientlibs.lc-60e4443805c37afa0c74b674b141f1df-lc.min.css HTTP/1.1" 200 809 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/dam/gui/coral/components/admin/metadataeditor/clientlibs/metadataeditor.lc-4a2226d8232f8b7ab27d24820b9ddd64-lc.min.js HTTP/1.1" 200 7965 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
```

**Format du journal**

<table>
<tbody>
<tr>
<td>AEM en tant qu’ID de noeud Cloud Service</td>
<td>cm-p1235-e2644-aem-author-59555cb5b8-8kgr2</td>
</tr>
<tr>
<td>Adresse IP du client</td>
<td>-</td>
</tr>
<tr>
<td>User</td>
<td>myuser@adobe.com</td>
</tr>
<tr>
<td>Date et heure</td>
<td>30/avr/2020:17:37:14 +000</td>
</tr>
<tr>
<td>Méthode HTTP</td>
<td>GET</td>
</tr>
<tr>
<td>URL</td>
<td>/libs/granite/ui/references/clientlibs/references.lc-5188e85840c529149e6cd29d94e74ad5-lc.min.css</td>
</tr>
<tr>
<td>Protocole</td>
<td>HTTP/1.1</td>
</tr>
<tr>
<td>État de la réponse HTTP</td>
<td>200</td>
</tr>
<tr>
<td>Temps de requête HTTP en millisecondes</td>
<td>1141</td>
</tr>
<tr>
<td>Référent</td>
<td><code>"https://author-p1234-e4444.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/wknd/en/adventures/surf-camp-in-costa-rica/adobestock_266405335.jpeg&_charset_=utf8"</code></td>
</tr>
<tr>
<td>Agent utilisateur</td>
<td>"Mozilla/5.0 (Macintosh ; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, comme Gecko) Chrome/81.0.4044.122 Safari/537.36"</td>
</tr>
</tbody>
</table>

### Configuration du journal d&#39;accès HTTP {#configuring-the-http-access-log}

Le journal d&#39;accès HTTP n&#39;est pas configurable dans AEM en tant que Cloud Service.

## Apache Web Server and Dispatcher Logging {#apache-web-server-and-dispatcher-logging}

AEM en tant que Cloud Service fournit trois journaux pour les serveurs Web Apache et la couche de répartiteur sur la publication :

* Journal d&#39;accès au serveur Web Apache HTTPD
* Journal des erreurs du serveur Web Apache HTTPD
* Journal des Dispatchers

Notez que ces journaux ne sont disponibles que pour le niveau Publication.

Cet ensemble de journaux fournit des informations sur les requêtes HTTP à l’AEM en tant que niveau de publication Cloud Service avant que ces requêtes n’atteignent l’application AEM. Il est important de le comprendre, car, idéalement, la plupart des requêtes HTTP envoyées aux serveurs de niveau Publication sont servies par du contenu mis en cache par le serveur Web Apache HTTPD et l’Dispatcher AEM, et n’atteignent jamais l’application AEM elle-même. Il n’existe donc aucune instruction de journal pour ces requêtes dans AEM journaux Java, Request ou Access.

### Journal d&#39;accès du serveur Web Apache HTTPD {#apache-httpd-web-server-access-log}

Le journal d&#39;accès Apache HTTP Web Server fournit des instructions pour chaque requête HTTP qui atteint le serveur Web/Dispatcher du niveau Publication. Notez que les requêtes diffusées à partir d’un CDN en amont ne sont pas reflétées dans ces journaux.

Consultez les informations sur le format du journal des erreurs dans la documentation [](https://httpd.apache.org/docs/2.4/logs.html#accesslog)officielle d’Apache.

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
<td>AEM en tant qu’ID de noeud de service cloud</td>
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
<td>01/mai/2020:00:09:46 +000</td>
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
<td>État de la réponse HTTP</td>
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
<td>"Mozilla/5.0 (Macintosh ; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, comme Gecko) Chrome/81.0.4044.122 Safari/537.36"</td>
</tr>
</tbody>
</table>

### Configuration du journal d&#39;accès au serveur Web Apache HTTPD {#configuring-the-apache-httpd-webs-server-access-log}

Ce journal n&#39;est pas configurable dans AEM en tant que Cloud Service.

## Journal d’erreurs du serveur Web Apache HTTPD {#apache-httpd-web-server-error-log}

Le journal des erreurs du serveur Web HTTP Apache fournit des instructions pour chaque erreur dans le serveur Web/Dispatcher du niveau Publication.

Consultez les informations sur le format du journal des erreurs dans la documentation [](https://httpd.apache.org/docs/2.4/logs.html#errorlog)officielle d’Apache.

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
<td>Vendredi 17 Juil 02:16:42.608913 2020</td>
</tr>
<tr>
<td>Niveau de Événement</td>
<td>[mpm_worker:notice]</td>
</tr>
<tr>
<td>ID de processus</td>
<td>[pid 1:tid 140715149343624]</td>
</tr>
<tr>
<td>Nom de la capsule</td>
<td>[cm-p1234-e56789-aem-publish-b86c6b466-qpfvp]</td>
</tr>
<tr>
<td>Message</td>
<td>AH00094 : Ligne de commande : 'httpd -d /etc/httpd -f /etc/httpd/conf/httpd.conf -D FOREGROUE -D </td>
</tr>
</tbody>
</table>

### Configuration du journal des erreurs du serveur Web Apache HTTPD {#configuring-the-apache-httpd-web-server-error-log}

Les niveaux de journal mod_rewrite sont définis par la variable REWRITE_LOG_LEVEL dans le fichier `conf.d/variables/global.var`.

Il peut être défini sur Error, Warn, Info, Debug et Trace1 - Trace8, avec la valeur par défaut Warn. Pour déboguer votre RewriteRules, il est recommandé de passer au niveau du journal Trace2.

Pour plus d&#39;informations, consultez la documentation [du module](https://httpd.apache.org/docs/current/mod/mod_rewrite.html#logging) mod_rewrite.

Pour définir le niveau de journal par environnement, utilisez la branche conditionnelle appropriée dans le fichier global.var, comme décrit ci-dessous :

```
Define REWRITE_LOG_LEVEL Debug
  
<IfDefine ENVIRONMENT_STAGE>
  ...
  Define REWRITE_LOG_LEVEL Warn
  ...
</IfDefine>
<IfDefine ENVIRONMENT_PROD>
  ...
  Define REWRITE_LOG_LEVEL Error
  ...
</IfDefine>
```

## Journal des Dispatchers {#dispatcher-log}

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
<td>[17/juil/2020:23:48:16 +000]</td>
</tr>
<tr>
<td>Nom de la capsule</td>
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
<td>Code d’état de réponse du Dispatcher</td>
<td>/content/experience-fragments/wknd/language-masters/en/contributors/sofia-sjoeberg/master/_jcr_content/root/responsivegrid/image.coreimg.100.500.jpeg/1572236359031/ayo-ogunseinde-237739.jpeg</td>
</tr>
<tr>
<td>Durée</td>
<td>1949ms</td>
</tr>
<tr>
<td>Ferme</td>
<td>[publishbatterie/0]</td>
</tr>
<tr>
<td>État du cache</td>
<td>[action manquée]</td>
</tr>
<tr>
<td>Hôte</td>
<td>"publish-p12904-e25628.adobeaemcloud.com"</td>
</tr>
</tbody>
</table>

### Configuration du journal des erreurs du Dispatcher {#configuring-the-dispatcher-error-log}

Les niveaux de journal du répartiteur sont définis par la variable DISP_LOG_LEVEL dans le fichier `conf.d/variables/global.var`.

Il peut être défini sur Error, Warn, Info, Debug et Trace1, avec la valeur par défaut Warn.

Bien que la journalisation des Dispatchers prenne en charge plusieurs autres niveaux de granularité de la journalisation, l’AEM en tant que Cloud Service recommande d’utiliser les niveaux décrits ci-dessous.

Pour définir le niveau de journal par environnement, utilisez la branche conditionnelle appropriée dans le `global.var` fichier, comme décrit ci-dessous :

```
Define DISP_LOG_LEVEL Debug
  
<IfDefine ENVIRONMENT_STAGE>
  ...
  Define DISP_LOG_LEVEL Warn
  ...
</IfDefine>
<IfDefine ENVIRONMENT_PROD>
  ...
  Define DISP_LOG_LEVEL Error
  ...
</IfDefine>
```

## Comment accéder aux journaux {#how-to-access-logs}

### Environnements du cloud {#cloud-environments}

AEM en tant que journaux Cloud Service pour les services cloud sont accessibles soit en téléchargeant via l’interface de Cloud Manager, soit en conservant les journaux sur la ligne de commande à l’aide de l’interface de ligne de commande E/S d’Adobe. Pour plus d’informations, voir la documentation [sur la journalisation de](/help/implementing/cloud-manager/manage-logs.md)Cloud Manager.

### SDK local {#local-sdk}

AEM en tant que SDK Cloud Service fournit des fichiers journaux pour la prise en charge du développement local.

AEM journaux se trouvent dans le dossier `crx-quickstart/logs`, où vous pouvez afficher les journaux suivants :

* Journal Java AEM : `error.log`
* Journal des requêtes HTTP AEM : `request.log`
* Journal d&#39;accès HTTP AEM : `access.log`

Les journaux de couche Apache, y compris le répartiteur, se trouvent dans le conteneur Docker qui contient le Dispatcher. Consultez la documentation [du](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html) Dispatcher pour savoir comment début du Dispatcher.

Pour récupérer les journaux :

1. Sur la ligne de commande, tapez `docker ps` pour liste vos conteneurs.
1. Pour vous connecter au conteneur, tapez &quot;`docker exec -it <container> /bin/sh`&quot;, où `<container>` est l&#39;identifiant de conteneur du répartiteur de l&#39;étape précédente.
1. Accédez à la racine du cache sous `/mnt/var/www/html`
1. Les journaux sont sous `/etc/httpd/logs`
1. Inspect the logs : ils sont accessibles sous le dossier XYZ, où vous pouvez afficher les journaux suivants :
   * Journal d&#39;accès du serveur Web Apache HTTPD - `httpd_access.log`
   * Journaux d&#39;erreur du serveur Web Apache HTTPD - `httpd_error.log`
   * Journaux des Dispatchers - `dispatcher.log`

Les journaux sont également directement imprimés sur le terminal. La plupart du temps, ces journaux doivent être DEBUG, ce qui peut être accompli en transmettant le niveau de débogage en tant que paramètre lors de l&#39;exécution de Docker. Par exemple :

`DISP_LOG_LEVEL=Debug ./bin/docker_run.sh out docker.for.mac.localhost:4503 8080`

## Débogage de la production et de la phase {#debugging-production-and-stage}

Dans des circonstances exceptionnelles, il est nécessaire de modifier les niveaux de journalisation pour qu’ils soient plus précis dans les environnements d’étape ou de production.

Bien que cela soit possible, il nécessite des modifications des niveaux de journal dans les fichiers de configuration dans Git from Warn et Error to Debug, et l&#39;exécution d&#39;un déploiement sur AEM en tant que Cloud Service pour enregistrer ces modifications de configuration avec les environnements.

Selon le trafic et la quantité de consignes écrites par Debug, cela peut avoir un impact négatif sur les performances de l&#39;environnement. Il est donc recommandé que les modifications apportées aux niveaux de débogage Stage et Production soient les suivantes :

* Fait judicieusement, et uniquement lorsque cela est absolument nécessaire
* Revenir aux niveaux appropriés et procéder au redéploiement le plus tôt possible

## Journaux de bogue {#splunk-logs}

Les clients disposant d&#39;un compte Splunk peuvent demander, via un ticket d&#39;assistance à la clientèle, que leurs journaux d&#39;Cloud Service d&#39;AEM soient transférés vers l&#39;index approprié. Les données de journalisation sont équivalentes à ce qui est disponible par le biais des téléchargements de journaux de Cloud Manager, mais les clients peuvent trouver pratique de tirer parti des fonctionnalités de requête disponibles dans le produit Splunk.

La bande passante réseau associée aux journaux envoyés à Splunk est considérée comme faisant partie de l&#39;utilisation des E/S réseau du client.

### Activation du transfert de blocs {#enabling-splunk-forwarding}

Dans la demande d&#39;assistance, les clients doivent indiquer :

* Hôte Splunk
* Index Splunk
* Le port Splunk
* Jeton Splunk HEC. Pour plus d’informations, consultez [cette page](https://docs.splunk.com/Documentation/Splunk/8.0.4/Data/HECExamples).

Les propriétés ci-dessus doivent être spécifiées pour chaque combinaison de type programme/environnement appropriée.  Par exemple, si un client souhaite des environnements de développement, d’évaluation et de production, il doit fournir trois ensembles d’informations, comme indiqué ci-dessous.

> [!NOTE]
>
> La redirection des blocs pour les environnements de programme sandbox n&#39;est pas prise en charge.

Vous trouverez ci-dessous un exemple de demande d’assistance à la clientèle :

Programme 123, Production Env

* Hôte de socle : `splunk-hec-ext.acme.com`
* Indice Splunk : acme_123prod (le client peut choisir la convention d’affectation de nom qu’il souhaite)
* Port Splunk : 443
* Jeton Splunk HEC : ABC123

Programme 123, Stage Env

* Hôte de socle : `splunk-hec-ext.acme.com`
* Indice Splunk : acme_123stage
* Port Splunk : 443
* Jeton Splunk HEC : ABC123

Programme 123, Dev Envs

* Hôte de socle : `splunk-hec-ext.acme.com`
* Indice Splunk : acme_123dev
* Port Splunk : 443
* Jeton Splunk HEC : ABC123

Il peut suffire que le même index Splunk soit utilisé pour chaque environnement, auquel cas le champ peut être utilisé pour différencier les valeurs en fonction de l’évolution, de l’étape et de la prod. `aem_env_type` S’il existe plusieurs environnements de développement, le `aem_env_id` champ peut également être utilisé. Certaines organisations peuvent choisir un index distinct pour les journaux de l&#39;environnement de production si l&#39;index associé limite l&#39;accès à un ensemble réduit d&#39;utilisateurs Splunk.

Voici un exemple d&#39;entrée de journal :

```
aem_env_id: 1242
aem_env_type: dev
aem_program_id: 12314
aem_tier: author
file_path: /var/log/aem/error.log
host: 172.34.200.12 
level: INFO
msg: [FelixLogListener] com.adobe.granite.repository Service [5091, [org.apache.jackrabbit.oak.api.jmx.SessionMBean]] ServiceEvent REGISTERED
orig_time: 16.07.2020 08:35:32.346
pod_name: aemloggingall-aem-author-77797d55d4-74zvt
splunk_customer: true
```
