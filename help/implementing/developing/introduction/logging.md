---
title: Journalisation
description: Découvrez comment configurer des paramètres globaux pour le service de journalisation centrale, des paramètres spécifiques pour les services individuels ou apprenez à demander la journalisation des données.
translation-type: tm+mt
source-git-commit: c7100f53ce38cb8120074ec4eb9677fb7303d007
workflow-type: tm+mt
source-wordcount: '873'
ht-degree: 10%

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

Notez que les requêtes HTTP diffusées à partir du cache du Dispatcher du niveau Publication ou du réseau de diffusion de contenu en amont ne sont pas reflétées dans ces journaux.

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

### Format du journal {#log-format}

| Date et heure | AEM en tant qu&#39;ID de dot Cloud Service | Niveau de journal | Thread | Classe Java | Message du journal |
|---|---|---|---|---|---|
| 29.04.2020 21:50:13.398 | `[cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]` | `*DEBUG*` | qtp2130572036-1472 | com.example.approval.workflow.impl.CustomApprovalWorkflow | Aucun approbateur spécifié, groupe d’utilisateurs Approbateurs [ créatifs par défaut ] |

**Exemple de sortie de journal**

`22.06.2020 18:33:30.120 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *ERROR* [qtp501076283-1809] io.prometheus.client.dropwizard.DropwizardExports Failed to get value from Gauge`
`22.06.2020 18:33:30.229 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [qtp501076283-1805] org.apache.sling.auth.core.impl.SlingAuthenticator getAnonymousResolver: Anonymous access not allowed by configuration - requesting credentials`
`22.06.2020 18:33:30.370 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [73.91.59.34 [1592850810364] GET /libs/granite/core/content/login.html HTTP/1.1] org.apache.sling.i18n.impl.JcrResourceBundle Finished loading 0 entries for 'en_US' (basename: <none>) in 4ms`
`22.06.2020 18:33:30.372 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [FelixLogListener] org.apache.sling.i18n Service [5126, [java.util.ResourceBundle]] ServiceEvent REGISTERED`
`22.06.2020 18:33:30.372 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *WARN* [73.91.59.34 [1592850810364] GET /libs/granite/core/content/login.html HTTP/1.1] libs.granite.core.components.login.login$jsp j_reason param value 'unknown' cannot be mapped to a valid reason message: ignoring`

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

### Format du journal {#http-request-logging-format}

| Date et heure | ID de paire de requêtes/réponses |  | Méthode HTTP | URL | Protocole | AEM en tant qu’ID de noeud Cloud Service |
|---|---|---|---|---|---|---|
| 29/avr/2020:19:14:21 +000 | `[137]` | -> | POST | /conf/global/settings/dam/adminui-extension/metadataprofile/ | HTTP/1.1 | `[cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]` |

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

### Configuration du journal {#configuring-the-log}

Le journal des requêtes HTTP AEM n&#39;est pas configurable dans AEM en tant que Cloud Service.

## Journalisation des accès HTTP AEM {#aem-http-access-logging}

AEM en tant que journalisation d’accès HTTP Cloud Service affiche les requêtes HTTP dans l’ordre du temps. Chaque entrée de journal représente la requête HTTP qui accède à AEM.

Ce journal est utile pour comprendre rapidement quelles requêtes HTTP sont envoyées à AEM, si elles réussissent en examinant le code d’état de la réponse HTTP qui l’accompagne et combien de temps la requête HTTP a duré. Ce journal peut également être utile pour déboguer une activité d’utilisateur spécifique en filtrant les entrées du journal par utilisateurs.

### Format du journal {#access-log-format}
