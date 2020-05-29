---
title: Journalisation
description: Découvrez comment configurer des paramètres globaux pour le service de journalisation centrale, des paramètres spécifiques pour les services individuels ou apprenez à demander la journalisation des données.
translation-type: ht
source-git-commit: ae04553b17fcb7b9660f709565faed791a0c930e
workflow-type: ht
source-wordcount: '1097'
ht-degree: 100%

---


# Journalisation{#logging}

La plate-forme AEM as a Cloud Service permet aux clients d’inclure du code personnalisé destiné à créer des expériences incomparables pour leurs propres bases de clients. Dans ce contexte, la journalisation est une fonction essentielle pour déboguer le code personnalisé dans les environnements de cloud, et plus particulièrement, pour les environnements de développement locaux.


<!-- ## Global Logging {#global-logging}

[Apache Sling Logging Configuration](https://sling.apache.org/documentation/development/logging.html#user-configuration---osgi-based) is used to configure the root logger. This defines the global settings for logging in AEM as a Cloud Service:

* the logging level
* the location of the central log file
* the number of versions to be kept
* version rotation; either maximum size or a time interval
* the format to be used when writing the log messages
-->

## Journalisation d’AEM as a Cloud Service {#aem-as-a-cloud-service-logging}

AEM as a Cloud Service vous offre la possibilité de configurer :

* les paramètres généraux du service de journalisation central ;
* la journalisation des données de requête (une configuration de journalisation spécialisée pour les informations de requête) :
* les paramètres spécifiques des services individuels

Pour le développement en local, les entrées de journaux sont écrites dans des fichiers locaux dans le dossier `/crx-quickstart/logs`.

Dans les environnements cloud, les développeurs peuvent télécharger les journaux via Cloud Manager ou utiliser un outil de ligne de commande pour en afficher les dernières lignes.

>[!NOTE]
>
>La connexion à AEM as a Cloud Service repose sur les principes Sling. Pour plus d’informations, voir [Journalisation Sling](https://sling.apache.org/site/logging.html).

## Journalisation Java d’AEM as a Cloud Service {#aem-as-a-cloud-service-java-logging}

### Enregistreurs et rédacteurs standard {#standard-loggers-and-writers}

> [!IMPORTANT]
> Ceux-ci peuvent être personnalisés si nécessaire, bien que la configuration standard convienne à la plupart des installations. Si, toutefois, vous devez personnaliser les configurations de journalisation standard, veillez à ne le faire que sur les environnements `dev`.

Certains enregistreurs et rédacteurs sont inclus dans une installation standard d’AEM as a Cloud Service.

Le premier est un cas particulier, car il contrôle à la fois les journaux `request` et `access` :

* L’enregistreur :

   * Enregistreur de données de demandes personnalisables Apache Sling

      (org.apache.sling.engine.impl.log.RequestLoggerService)

   * Écrit les messages relatifs au contenu des demandes dans `request.log`.

* Est lié à :

   * Enregistreur de demandes Apache Sling

      (org.apache.sling.engine.impl.log.RequestLogger)

   * Écrit les messages dans `request.log` ou `access.log`.

Les autres paires suivent la configuration standard :

* L’enregistreur :

   * Apache Sling Logging Logger Configuration

      (org.apache.sling.commons.log.LogManager.factory.config)

   * Écrit des messages `Information` sur `logs/error.log`.

* Est lié au rédacteur :

   * Apache Sling Logging Writer Configuration

      (org.apache.sling.commons.log.LogManager.factory.writer)

* L’enregistreur :

   * Apache Sling Logging Logger Configuration (org.apache.sling.commons.log.LogManager.factory.config.649d51b7-6425-45c9-81e6-2697a03d6be7)

   * Écrit des messages `Warning` sur `../logs/error.log` pour le service `org.apache.pdfbox`.

* N’est pas lié à un rédacteur spécifique, et crée et utilise donc un rédacteur implicite avec une configuration par défaut.

**Journalisation des requêtes HTTP d’AEM as a Cloud Service**

Toutes les demandes d’accès à la gestion du contenu web d’AEM et au référentiel sont enregistrées ici.

Exemple de sortie :

**AEM as a Cloud Service : journalisation des requêtes HTTP/des accès aux réponses**

Chaque demande d’accès est enregistrée ici en même temps que la réponse.

Exemple de sortie :

**Serveur web Apache/Journalisation de Dispatcher**

Il s’agit d’un journal utilisé pour le débogage des problèmes de Dispatcher. Pour plus d’informations, voir [Débogage de la configuration Apache et Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/).

<!-- Besides the three types of logs present on an AEM as a Cloud Service instance (`request`, `access` and `error` logs) there is another dispatcher/overview.html#debugging-apache-and-dispatcher-configuration.

leftover text from the last breakaway chunk (re dispatcher) -->

En termes de bonnes pratiques, il est recommandé de s’aligner sur les configurations existantes dans l’archétype Maven AEM as a Cloud Service. Ces configurations définissent différents paramètres et niveaux de journal pour des types d’environnements spécifiques :

* pour les environnements `local dev` et `dev`, définissez l’enregistreur sur le niveau **DEBUG** sur le journal `error.log`
* pour `stage`, définissez l’enregistreur sur le niveau **WARN** au niveau du journal `error.log`
* pour `prod`, définissez l’enregistreur sur le niveau **ERROR** au niveau du journal `error.log`

Voici des exemples pour chaque configuration :

* Environnements `dev` :

```
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
    xmlns:jcr="http://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig"
    org.apache.sling.commons.log.level="debug"
    org.apache.sling.commons.log.names="[com.mycompany.myapp]" />
```


* Environnements `stage` :

```
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
    xmlns:jcr="http://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig"
    org.apache.sling.commons.log.level="warn"
    org.apache.sling.commons.log.names="[com.mycompany.myapp]" />
```

* Environnements `prod` :

```
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
    xmlns:jcr="http://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig"
    org.apache.sling.commons.log.level="error"
    org.apache.sling.commons.log.names="[com.mycompany.myapp]" />
```

### Enregistreurs et rédacteurs pour les services individuels {#loggers-and-writers-for-individual-services}

En plus des paramètres de journalisation globale, AEM as a Cloud Service permet de configurer des paramètres spécifiques pour un service individuel :

* le niveau de journalisation spécifique
* l’enregistreur (le service OSGi fournissant les messages de journal)

Cela vous permet de canaliser les messages de journal pour un seul service dans un fichier distinct. Cela peut être particulièrement utile pendant le développement ou les tests, par exemple, si vous avez besoin d’un niveau de journalisation accru pour un service spécifique.

AEM as a Cloud Service utilise les éléments suivants pour écrire des messages de journal dans un fichier :

1. Un **service OSGi**(enregistreur) écrit un message de journal.
1. Un **enregistreur de journalisation** met en forme ce message selon vos spécifications.
1. Un **rédacteur de journalisation** rédige tous ces messages dans le fichier physique que vous avez défini.

Ces éléments sont liés par les paramètres suivants pour les éléments appropriés :

* **Enregistreur (enregistreur de journalisation)**

   Définissez le ou les services qui génèrent les messages.

<!-- * **Log File (Logging Logger)**

  Define the physical file for storing the log messages.

  This is used to link a Logging Logger with a Logging Writer. The value must be identical to the same parameter in the Logging Writer configuration for the connection to be made.

* **Log File (Logging Writer)**

  Define the physical file that the log messages will be written to.

  This must be identical to the same parameter in the Logging Writer configuration, or the match will not be made. If there is no match then an implicit Writer will be created with default configuration (daily log rotation).
-->

### Définition du niveau de journalisation {#setting-the-log-level}

Pour modifier les niveaux de journal des environnements Cloud, il est nécessaire de modifier la configuration d’enregistreur OSGI Sling, suivi d’un redéploiement complet. Comme il ne s’agit pas d’une opération instantanée, soyez prudent lorsque vous activez les journaux en détail sur les environnements de production qui reçoivent beaucoup de trafic. Dans le futur, il est possible que des mécanismes soient ajoutés pour pouvoir modifier plus rapidement le niveau du journal.

>[!NOTE]
>
> Pour effectuer les modifications de configuration répertoriées ci-dessous, vous devez les créer dans un environnement de développement local, puis les transmettre à une instance AEM as a Cloud Service. Pour plus d’informations sur la procédure à suivre, voir [Déploiement sur AEM as a Cloud Service](/help/implementing/deploying/overview.md).

**Activation du niveau de journalisation DEBUG**

>[!WARNING]
>
> L’activation globale du niveau de journalisation DEBUG génère une grande quantité d’informations qui seront difficiles à analyser. Il est recommandé de n’activer ce niveau que pour les services nécessitant un débogage. Pour plus d’informations, voir [Enregistreurs et rédacteurs pour les services individuels](logging.md#loggers-and-writers-for-individual-services).

Le niveau de journalisation par défaut est INFO, ce qui signifie que les messages DEBUG ne sont pas consignés.
Pour activer le niveau de journalisation DEBUG, définissez

``` /libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level ```

la propriété à corriger. Ne laissez pas le journal au niveau de débogage DEBUG plus longtemps que nécessaire, car cela génère un grand nombre de journaux.
Une ligne dans le fichier de débogage commence généralement par DEBUG, puis fournit le niveau de journalisation, l’action d’installation et le message du journal. Par exemple :

``` DEBUG 3 WebApp Panel: WebApp successfully deployed ```

Les niveaux de journalisation sont les suivants :

| 0 | Erreur fatale | L’action a échoué et le programme d’installation ne peut pas continuer. |
|---|---|---|
| 1 | Erreur | L’action a échoué. L’installation se poursuit, mais une partie de CRX n’a pas été installée correctement et ne fonctionnera pas. |
| 2 | Avertissement | L’action a réussi, mais a rencontré des problèmes. CRX risque de ne pas fonctionner correctement. |
| 3 | Informations | L’action a réussi. |

### Création de vos propres enregistreurs et rédacteurs {#creating-your-own-loggers-and-writers}

Vous pouvez définir votre propre paire Enregistrer/Rédacteur :

1. Créez une nouvelle instance de la configuration d’usine [Apache Sling Logging Logger Configuration](https://sling.apache.org/documentation/development/logging.html#user-configuration---osgi-based).

   1. Définissez l’enregistreur.

<!-- 1. Create a new instance of the Factory Configuration [Apache Sling Logging Writer Configuration](https://sling.apache.org/documentation/development/logging.html#user-configuration---osgi-based).

    1. Specify the Log File - this must match that specified for the Logger.
    1. Configure the other parameters as required. -->

### Configuration de la journalisation {#configure-logging}

>[!NOTE]
>
>Lorsque vous utilisez Adobe Experience Manager, plusieurs méthodes permettent de gérer les paramètres de configuration pour ces services.

Dans certains cas, vous pouvez créer un fichier journal personnalisé avec un niveau de journalisation différent. Vous pouvez le faire depuis le référentiel en procédant comme suit :

1. S’il n’existe pas déjà, créez un dossier de configuration (`sling:Folder`) pour votre projet `/apps/<*project-name*>/config`.
1. Sous `/apps/<*project-name*>/config`, créez un nœud pour la nouvelle configuration de l’enregistreur de journaux Apache Sling :

   * Nom : `org.apache.sling.commons.log.LogManager.factory.config-<*identifier*>` (s’agissant d’un enregistreur)

      Où `<*identifier*>` est remplacé par du texte libre que vous devez entrer pour l’instance (vous ne pouvez pas omettre cette information).

      Par exemple, `org.apache.sling.commons.log.LogManager.factory.config-MINE`

   * Type : `sling:OsgiConfig`
   >[!NOTE]
   >
   >Bien que cela ne constitue pas une exigence technique, il est recommandé de rendre `<*identifier*>` unique.

<!-- 1. Set the following properties on this node:

    * Name: `org.apache.sling.commons.log.file`

      Type: String

      Value: specify the Log File; for example, `logs/myLogFile.log`

    * Name: `org.apache.sling.commons.log.names`

      Type: String[] (String + Multi)

      Value: specify the OSGi services for which the Logger is to log messages; for example, all of the following:

        * `org.apache.sling`
        * `org.apache.felix`
        * `com.day`

    * Name: `org.apache.sling.commons.log.level`

      Type: String

      Value: specify the log level required ( `debug`, `info`, `warn` or `error`); for example `debug`

    * Configure the other parameters as required:

        * Name: `org.apache.sling.commons.log.pattern`

          Type: `String`

          Value: specify the pattern of the log message as required; for example,

          `{0,date,dd.MM.yyyy HH:mm:ss.SSS} *{4}* [{2}] {3} {5}`

   >[!NOTE]
   >
   >`org.apache.sling.commons.log.pattern` supports up to six arguments.

   >
   >
   >{0} The timestamp of type `java.util.Date`
   >{1} the log marker
   >{2} the name of the current thread
   >{3} the name of the logger
   >{4} the log level
   >{5} the log message

   >
   >
   >If the log call includes a `Throwable` the stacktrace is appended to the message.

   >[!CAUTION]
   >
   >org.apache.sling.commons.log.names must have a value.

   >[!NOTE]
   >
   >Log writer paths are relative to the `crx-quickstart` location.
   >
   >
   >Therefore, a log file specified as:
   >
   >
   >`logs/thelog.log`

   >
   >
   >writes to:
   >
   >
   >`` ` ` `<*cq-installation-dir*>/``crx-quickstart/logs/thelog.log`.
   >
   >
   >And a log file specified as:
   >
   >
   >`../logs/thelog.log`

   >
   >
   >writes to a directory:
   >
   >
   >` <*cq-installation-dir*>/logs/`
   >``(i.e. next to ` `<*cq-installation-dir*>/`crx-quickstart/`)
 -->

<!-- open question: see if we need to leave the above warning note in place, but adjust it so that it doesn't mention filenames -->

<!-- 1. This step is only necessary when a new Writer is required (i.e. with a configuration that is different to the default Writer).

   >[!CAUTION]
   >
   >A new Logging Writer Configuration is only required when the existing default is not suitable.

   >
   >
   >If no explicit Writer is configured the system will automatically generate an implicit Writer based on the default.

   Under `/apps/<*project-name*>/config`, create a node for the new `Apache Sling Logging Writer` Configuration:

    * Name: `org.apache.sling.commons.log.LogManager.factory.writer-<*identifier*>` (as this is a Writer)

      As with the Logger, `<*identifier*>` is replaced by free text that you (must) enter to identify the instance (you cannot omit this information). For example, `org.apache.sling.commons.log.LogManager.factory.writer-MINE`

    * Type: `sling:OsgiConfig`

   >[!NOTE]
   >
   >Although not a technical requirement, it is advisable to make `<*identifier*>` unique.

   Set the following properties on this node:

    * Name: `org.apache.sling.commons.log.file`

      Type: `String`

      Value: specify the Log File so that it matches the file specified in the Logger;

      for this example, `../logs/myLogFile.log`.

    * Configure the other parameters as required:

        * Name: `org.apache.sling.commons.log.file.number`

          Type: `Long`

          Value: specify the number of log files you want kept; for example, `5`

        * Name: `org.apache.sling.commons.log.file.size`

          Type: `String`

          Value: specify as required to control file rotation by size/date; for example, `'.'yyyy-MM-dd`

   >[!NOTE]
   >
   >`org.apache.sling.commons.log.file.size` controls the rotation of the log file by setting either:
   >
   >* a maximum file size
   >* a time/date schedule
   >
   >to indicate when a new file will be created (and the existing file renamed according to the name pattern).
   >
   >* A size limit can be specified with a number. If no size indicator is given, then this is taken as the number of bytes, or you can add one of the size indicators - `KB`, `MB`, or `GB` (case is ignored).
   >* A time/date schedule can be specified as a `java.util.SimpleDateFormat` pattern. This defines the time period after which the file will be rotated; also the suffix appended to the rotated file (for identification).
   >
   >The default is '.'yyyy-MM-dd (for daily log rotation).
   >
   >So for example, at midnight of January 20th 2010 (or when the first log message after this occurs to be precise), ../logs/error.log will be renamed to ../logs/error.log.2010-01-20. Logging for the 21st of January will be output to (a new and empty) ../logs/error.log until it is rolled over at the next change of day.
   >
   >      | `'.'yyyy-MM` |Rotation at the beginning of each month |
   >      |---|---|
   >      | `'.'yyyy-ww` |Rotation at the first day of each week (depends on the locale). |
   >      | `'.'yyyy-MM-dd` |Rotation at midnight each day. |
   >      | `'.'yyyy-MM-dd-a` |Rotation at midnight and midday of each day. |
   >      | `'.'yyyy-MM-dd-HH` |Rotation at the top of every hour. |
   >      | `'.'yyyy-MM-dd-HH-mm` |Rotation at the beginning of every minute. |
   >
   >      Note: When specifying a time/date:
   >      1. You should "escape" literal text within a pair of single quotes (' ');
   >      this is to avoid certain characters being interpreted as pattern letters.
   >      1. Only use characters allowed for a valid file name anywhere in the option.

1. Read your new log file with your chosen tool.

   The log file created by this example will be `../crx-quickstart/logs/myLogFile.log`. -->

La console Felix fournit également des informations sur la prise en charge du journal Sling à l’adresse `../system/console/slinglog` ; par exemple, `https://localhost:4502/system/console/slinglog`.draft.

## Accès aux journaux et leur gestion {#manage-logs}

Pour plus d’informations sur l’accès aux journaux et leur gestion, voir la [documentation de Cloud Manager](/help/implementing/cloud-manager/manage-logs.md).