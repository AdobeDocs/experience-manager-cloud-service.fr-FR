---
title: Journalisation
description: Découvrez comment configurer des paramètres globaux pour le service de journalisation centrale, des paramètres spécifiques pour les services individuels ou apprenez à demander la journalisation des données.
translation-type: tm+mt
source-git-commit: 0e4de19f4ae53414d90f6979980f3ce79f49394d

---


# Journalisation{#logging}

AEM en tant que service Cloud  vous  la possibilité de configurer :

* les paramètres généraux du service de journalisation central ;
* la journalisation des données de requête (une configuration de journalisation spécialisée pour les informations de requête) :
* des paramètres spécifiques pour les services individuels (par exemple, un fichier journal individuel et un format pour les messages de journaux).

For local development, logs entries are written to local files in the `/crx-quickstart/logs` folder.

Dans les environnements Cloud, les développeurs peuvent télécharger les journaux via Cloud Manager ou utiliser un outil de ligne de commande pour les retailler.

>[!NOTE]
>
>La connexion à AEM en tant que service Cloud repose sur les principes Sling. Pour plus d’informations, voir [Journalisation Sling](https://sling.apache.org/site/logging.html).

## Journalisation globale {#global-logging}

La [configuration de la journalisation d’Apache Sling](https://sling.apache.org/documentation/development/logging.html#user-configuration---osgi-based) sert à configurer l’enregistreur racine. Ceci définit les paramètres globaux pour la connexion à AEM en tant que service Cloud :

* le niveau de journalisation
* l’emplacement du fichier journal central
* le nombre de versions à conserver
* la rotation de version (soit une taille maximale, soit un intervalle de temps)
* le format à utiliser lors de l’écriture des messages du journal

## Enregistreurs et rédacteurs pour les services individuels {#loggers-and-writers-for-individual-services}

Outre les paramètres de journalisation globaux, AEM en tant que service Cloud vous permet de configurer des paramètres spécifiques pour un service individuel :

* le niveau de journalisation spécifique
* l’emplacement du fichier journal individuel
* le nombre de versions à conserver
* la rotation de version (soit une taille maximale, soit un intervalle de temps) 
* le format à utiliser lors de l’écriture des messages du journal
* l’enregistreur (le service OSGi fournissant les messages de journal)

Cela vous permet de canaliser les messages de journal pour un seul service dans un fichier distinct. Cela peut être particulièrement utile pendant le développement ou les tests, par exemple, si vous avez besoin d’un niveau de journalisation accru pour un service spécifique.

AEM as a Cloud Service utilise les éléments suivants pour écrire des messages de journal dans un fichier :

1. Un **service OSGi**(enregistreur) écrit un message de journal.
1. Un **enregistreur de journalisation** met en forme ce message selon vos spécifications.
1. Un **rédacteur de journalisation** rédige tous ces messages dans le fichier physique que vous avez défini.

Ces éléments sont liés par les paramètres suivants pour les éléments appropriés :

* **Journalisation (Journalisation)**

   Définissez le ou les services qui génèrent les messages.

* **Fichier journal (Journalisation)**

   Définissez le fichier physique pour le stockage des messages du journal.

   Ceci est utilisé pour lier un enregistreur de journalisation à un rédacteur de journalisation. La valeur doit être identique au même paramètre de la configuration du rédacteur de journalisation pour que la connexion s’effectue.

* **Fichier journal (enregistreur de journal)**

   Définissez le fichier physique dans lequel les messages du journal seront écrits.

   La valeur doit être identique au même paramètre de la configuration du rédacteur de journalisation, sinon la correspondance ne s’effectue pas. En l’absence de correspondance, un rédacteur implicite est créé avec la configuration par défaut (rotation quotidienne du journal).

### Enregistreurs et rédacteurs standard {#standard-loggers-and-writers}

Certains journaux et écrivains sont inclus dans une installation standard d’AEM en tant que service Cloud.

Le premier est un cas particulier car il contrôle à la fois les fichiers `request.log`et `access.log` :

* L’enregistreur :

   * Enregistreur de données de demandes personnalisables Apache Sling

      (org.apache.sling.engine.impl.log.RequestLoggerService)

   * Écrit les messages relatifs au contenu des demandes dans `request.log`.

* Est lié à :

   * Enregistreur de demandes Apache Sling

      (org.apache.sling.engine.impl.log.RequestLogger)

   * Writes the messages to either `request.log` or `access.log`.

Ceux-ci peuvent être personnalisés si nécessaire, bien que la configuration standard convienne à la plupart des installations.

Les autres paires suivent la configuration standard :

* L’enregistreur :

   * Apache Sling Logging Logger Configuration

      (org.apache.sling.commons.log.LogManager.factory.config)

   * Écrit `Information` des messages à `logs/error.log`.

* Est lié au rédacteur :

   * Apache Sling Logging Writer Configuration

      (org.apache.sling.commons.log.LogManager.factory.writer)

* L’enregistreur :

   * Apache Sling Logging Logger Configuration (org.apache.sling.commons.log.LogManager.factory.config.649d51b7-6425-45c9-81e6-2697a03d6be7)

   * Écrit `Warning` des messages à `../logs/error.log` pour le service `org.apache.pdfbox`.

* N’est pas lié à un rédacteur spécifique, et crée et utilise donc un rédacteur implicite avec une configuration par défaut (rotation quotidienne du journal).

## Définition du niveau de journal {#setting-the-log-level}

Pour modifier les niveaux de journal des environnements Cloud, il est nécessaire de modifier la configuration d’enregistreur OSGI Sling, suivi d’un redéploiement complet. Comme il ne s’agit pas d’une opération instantanée, soyez prudent lorsque vous activez les journaux en détail sur les environnements de production qui reçoivent beaucoup de trafic. Dans le futur, il est possible que des mécanismes soient ajoutés pour pouvoir modifier plus rapidement le niveau du journal.

> [!NOTE]
> 
> Pour effectuer les modifications de configuration répertoriées ci-dessous, vous devez les créer sur un de développement local  puis les transmettre à AEM en tant qu’instance de service Cloud. Pour plus d’informations sur la procédure à suivre, voir [Déploiement sur AEM en tant que service](/help/implementing/deploying/overview.md)Cloud.

### Activation du niveau de journalisation DEBUG {#activating-the-debug-log-level}

> [!WARNING]
>
> L&#39;activation globale du niveau du journal DEBUG génère une grande quantité d&#39;informations qui seront difficiles à analyser. Il est recommandé de ne l’activer que pour les services nécessitant un débogage. Pour plus d’informations, voir [Journaux et Ecrivains pour les services](logging.md#loggers-and-writers-for-individual-services)individuels.

Le niveau de journalisation par défaut est INFO, ce qui signifie que les messages DEBUG ne sont pas consignés.
Pour activer le niveau du journal DEBUG, définissez la variable

``` /libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level ```

la propriété à corriger. Ne laissez pas le journal au niveau de débogage DEBUG plus longtemps que nécessaire, car cela génère un grand nombre de journaux.
Une ligne dans le fichier de débogage commence généralement par DEBUG, puis fournit le niveau de journalisation, l’action d’installation et le message du journal. Par exemple :

``` DEBUG 3 WebApp Panel: WebApp successfully deployed ```

Les niveaux de journalisation sont les suivants :

| 0 | Erreur fatale | L&#39;action a échoué et le programme d&#39;installation ne peut pas continuer. |
|---|---|---|
| 1 | Erreur | L&#39;action a échoué. L’installation se poursuit, mais une partie de CRX n’a pas été installée correctement et ne fonctionnera pas. |
| 2 | Avertissement | L&#39;action a réussi mais a rencontré des problèmes. CRX risque de ne pas fonctionner correctement. |
| 3 | Informations | L&#39;action a réussi. |

### Création de vos propres enregistreurs et rédacteurs {#creating-your-own-loggers-and-writers}

Vous pouvez définir votre propre paire Enregistrer/Rédacteur :

1. Créez une nouvelle instance de la configuration d’usine [Apache Sling Logging Logger Configuration](https://sling.apache.org/documentation/development/logging.html#user-configuration---osgi-based).

   1. Définissez le fichier journal.
   1. Définissez l’enregistreur.
   1. Configurez les autres paramètres en fonction de vos besoins.

1. Créez une nouvelle instance de la configuration d’usine [Apache Sling Logging Writer Configuration](https://sling.apache.org/documentation/development/logging.html#user-configuration---osgi-based).

   1. Spécifiez le fichier journal (il doit correspondre à celui spécifié pour l’enregistreur).
   1. Configurez les autres paramètres en fonction de vos besoins.

### Création d’un fichier journal personnalisé {#create-a-custom-log-file}

>[!NOTE]
>
>Lorsque vous travaillez avec Adobe Experience Manager, il existe plusieurs méthodes pour gérer les paramètres de configuration de ces services.

Dans certains cas, vous pouvez créer un fichier journal personnalisé avec un niveau de journalisation différent. Vous pouvez le faire depuis le référentiel en procédant comme suit :

1. If not already existing, create a new configuration folder ( `sling:Folder`) for your project `/apps/<*project-name*>/config`.
1. Under `/apps/<*project-name*>/config`, create a node for the new Apache Sling Logging Logger Configuration:

   * Nom : `org.apache.sling.commons.log.LogManager.factory.config-<*identifier*>` (comme il s’agit d’un journal)

      Where `<*identifier*>` is replaced by free text that you (must) enter to identify the instance (you cannot omit this information).

      Par exemple, `org.apache.sling.commons.log.LogManager.factory.config-MINE`

   * Type: `sling:OsgiConfig`
   >[!NOTE]
   >
   >Although not a technical requirement, it is advisable to make `<*identifier*>` unique.

1. Définissez les propriétés suivantes sur ce nœud :

   * Nom: `org.apache.sling.commons.log.file`

      Type : Chaîne

      Valeur : spécifiez le fichier journal; par exemple, `logs/myLogFile.log`

   * Nom: `org.apache.sling.commons.log.names`

      Type : Chaîne[] (Chaîne + Multi)

      Valeur : spécifiez les services OSGi pour lesquels le journal doit enregistrer les messages ; par exemple, tous les éléments suivants :

      * `org.apache.sling`
      * `org.apache.felix`
      * `com.day`
   * Nom: `org.apache.sling.commons.log.level`

      Type : Chaîne

      Valeur : spécifier le niveau de journal requis ( `debug`, `info`, `warn` ou `error`); par exemple `debug`

   * Configurez les autres paramètres en fonction de vos besoins :

      * Nom: `org.apache.sling.commons.log.pattern`

         Type: `String`

         Valeur : préciser le modèle du message du journal, le cas échéant; par exemple,

         `{0,date,dd.MM.yyyy HH:mm:ss.SSS} *{4}* [{2}] {3} {5}`
   >[!NOTE]
   >
   >`org.apache.sling.commons.log.pattern` prend en charge jusqu’à six arguments.

   >{0} Horodatage de type `java.util.Date`
   >
   >{1} le marqueur de journal{2} le nom du thread actuel{3} le nom du journal{4} le niveau de journal{5} le message de journal

   >Si l’appel de journal comprend un `Throwable`, la trace de pile est ajoutée au message. 

   >[!CAUTION]
   org.apache.sling.commons.log.names doit avoir une valeur.

   >[!NOTE]
   Log writer paths are relative to the `crx-quickstart` location.
   Par conséquent, un fichier journal spécifié en tant que :
   `logs/thelog.log`

   >écrit à :
   `` ` ` `<*cq-installation-dir*>/``crx-quickstart/logs/thelog.log`.
   Et un fichier journal spécifié en tant que :
   `../logs/thelog.log`

   >écrit à un répertoire :
   ` <*cq-installation-dir*>/logs/`
&quot;(c’est-à-dire en regard de ` `&lt;*cq-installation-dir*>/`crx-quickstart/`)

1. Cette étape est nécessaire uniquement lorsqu’un nouvel auteur est nécessaire (c’est-à-dire avec une configuration différente de l’auteur par défaut).

   >[!CAUTION]
   Une nouvelle configuration d’auteur de journalisation est uniquement nécessaire lorsque celle par défaut n’est pas appropriée. 

   >Si aucun auteur explicite n’est configuré, le système génère automatiquement un auteur implicite par défaut.

   Sous `/apps/<*project-name*>/config`, créez un noeud pour la nouvelle `Apache Sling Logging Writer` configuration :

   * Nom : `org.apache.sling.commons.log.LogManager.factory.writer-<*identifier*>` (comme il s’agit d’un auteur)

      Comme pour le Logger, `<*identifier*>` est remplacé par du texte libre que vous (devez) entrez pour identifier l&#39;instance (vous ne pouvez pas omettre ces informations). Par exemple, `org.apache.sling.commons.log.LogManager.factory.writer-MINE`

   * Type: `sling:OsgiConfig`
   >[!NOTE]
   Although not a technical requirement, it is advisable to make `<*identifier*>` unique.

   Définissez les propriétés suivantes sur ce nœud :

   * Nom: `org.apache.sling.commons.log.file`

      Type: `String`

      Valeur : spécifiez le fichier journal de sorte qu&#39;il corresponde au fichier spécifié dans le journal ;

      pour cet exemple, `../logs/myLogFile.log`.

   * Configurez les autres paramètres en fonction de vos besoins :

      * Nom: `org.apache.sling.commons.log.file.number`

         Type: `Long`

         Value: specify the number of log files you want kept; for example, `5`

      * Nom: `org.apache.sling.commons.log.file.size`

         Type: `String`

         Value: specify as required to control file rotation by size/date; for example, `'.'yyyy-MM-dd`
   >[!NOTE]
   `org.apache.sling.commons.log.file.size` contrôle la rotation du fichier journal en fonction du paramètre suivant :
   * une taille maximale de fichier
   * une planification heure/date
   pour indiquer quand un nouveau fichier sera créé (et le fichier existant renommé selon le modèle de nom). 
   * Une taille maximale peut être spécifiée par un nombre. If no size indicator is given, then this is taken as the number of bytes, or you can add one of the size indicators - `KB`, `MB`, or `GB` (case is ignored).
   * Une planification heure/date peut être spécifiée sous la forme d’un modèle `java.util.SimpleDateFormat`. Cela définit le délai au bout duquel le fichier subit une rotation ; de même que le suffixe ajouté au fichier pivoté (pour identification). 
   La valeur par défaut est &#39;.&#39;yyyy-MM-dd (pour la rotation quotidienne du journal).
   Par exemple, à minuit le 20 janvier 2010 (ou pour être précis, lorsque le premier message de journal après cette heure est envoyé), ../logs/error.log sera renommé ../logs/error.log.2010-01-20. La journalisation du 21 janvier sera générée vers ../logs/error.log (nouveau et vide) jusqu’à ce qu’elle soit remplacée lors de la prochaine modification quotidienne.
       | `&#39;.&#39;yyyy-MM` |Rotation at the beginning of each month |
       |---|---|
       | `&#39;.&#39;aaaa-ww`|Rotation au premier jour de chaque semaine (dépend du paramètre régional). |
       | `&#39;.&#39;aaaa-MM-jj`|Rotation à minuit tous les jours. |
       | `&#39;.&#39;aaaa-MM-jj-a`|Rotation à minuit et midi de chaque jour. |
       | `&#39;.&#39;aaaa-MM-jj-HH`|Rotation en haut de chaque heure. |
       | `&#39;.&#39;aaaa-MM-jj-HH-mm`|Rotation au début de chaque minute. |
       
       Note: When specifying a time/date:
       1. You should &quot;escape&quot; literal text within a pair of single quotes (&#39; &#39;);
       this is to avoid certain characters being interpreted as pattern letters.
       1. Utilisez uniquement les caractères autorisés pour un nom de fichier valide n’importe où dans l’option.
   

1. Lisez votre nouveau fichier journal avec l’outil sélectionné.

   The log file created by this example will be `../crx-quickstart/logs/myLogFile.log`.

The Felix Console also provides information about Sling Log Support at `../system/console/slinglog`; for example `https://localhost:4502/system/console/slinglog`.