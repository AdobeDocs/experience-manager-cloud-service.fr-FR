---
title: AEM en tant que directives de développement de service Cloud
description: 'À terminer '
translation-type: tm+mt
source-git-commit: cedc14b0d71431988238d6cb4256936a5ceb759b

---


# AEM en tant que directives de développement de service Cloud {#aem-as-a-cloud-service-development-guidelines}

## Tâches en arrière-plan et tâches à long terme {#background-tasks-and-long-running-jobs}

Le code exécuté en tant que tâches en arrière-plan doit supposer que l’instance dans laquelle il est exécuté peut être supprimée à tout moment. Par conséquent, le code doit être résilient et la plupart des importations doivent pouvoir être reproduites. Cela signifie que si le code est réexécuté, il ne doit pas recommencer à partir du début mais plutôt à partir de l’endroit où il a été abandonné. Bien qu’il ne s’agisse pas d’une nouvelle exigence pour ce type de code, dans AEM en tant que service Cloud, il est plus probable qu’une suppression d’instance se produise.

Afin de minimiser les problèmes, il est nécessaire d’éviter les emplois à long terme si possible, et de pouvoir les reprendre au minimum. Pour exécuter de telles tâches, utilisez Sling Jobs, qui dispose d’une garantie au moins une fois ; par conséquent, si elles sont interrompues, elles seront réexécutées dès que possible. Mais ils ne devraient probablement pas recommencer depuis le début. Pour planifier de telles tâches, il est préférable d’utiliser le planificateur des tâches [](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#jobs-guarantee-of-processing) Sling, car il s’agit à nouveau de l’exécution au moins une fois.

Le planificateur Sling Commons ne doit pas être utilisé pour la planification, car l’exécution ne peut pas être garantie. Il est tout simplement plus probable qu&#39;elle soit programmée.

De même, avec tout ce qui se passe de manière asynchrone, comme agir sur des événements d’observation (c’est-à-dire des événements JCR ou des événements de ressources Sling), il n’est pas garanti qu’ils soient exécutés et doivent donc être utilisés avec soin. C’est déjà le cas pour les déploiements d’AEM dans le présent.

## Connexions HTTP sortantes {#outgoing-http-connections}

Il est vivement recommandé que toute connexion HTTP sortante définisse des délais d’attente raisonnables pour la connexion et la lecture. Pour le code qui n’applique pas ces délais d’expiration, les instances AEM s’exécutant sur AEM en tant que service Cloud appliqueront un délai d’expiration global. Ces valeurs de délai d’expiration sont de 10 secondes pour les appels de connexion et de 60 secondes pour les appels de lecture pour les connexions utilisés par les bibliothèques Java populaires suivantes :

Adobe recommande l’utilisation de la bibliothèque [](https://hc.apache.org/httpcomponents-client-ga/) Apache HttpComponents Client 4.x fournie pour établir des connexions HTTP.

Les alternatives connues pour fonctionner, mais qui peuvent nécessiter de fournir la dépendance vous-même sont les suivantes :

* [java.net.URL](https://docs.oracle.com/javase/7/docs/api/java/net/URL.html) et/ou [java.net.URLConnection](https://docs.oracle.com/javase/7/docs/api/java/net/URLConnection.html) (fournie par AEM)
* [Apache Commons HttpClient 3.x](https://hc.apache.org/httpclient-3.x/) (non recommandé car obsolète et remplacé par la version 4.x)
* [OK Http](OK Http (non fourni par AEM)) (non fourni par AEM)

## Surveillance et débogage {#monitoring-and-debugging}

### Journaux {#logs}

* Pour le développement local, les entrées de journaux sont écrites dans des fichiers locaux.
   * `./crx-quickstart/logs`
* Dans les environnements Cloud, les développeurs peuvent télécharger les journaux via Cloud Manager ou utiliser un outil de ligne de commande pour les faire disparaître. <!-- See the [Cloud Manager documentation](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) for more details. Note that custom logs are not supported and so all logs should be output to the error log. -->
* Pour modifier les niveaux de journal des environnements Cloud, il est nécessaire de modifier la configuration OSGI Sling Logging, suivie d’un redéploiement complet. Comme il ne s’agit pas d’une opération instantanée, soyez prudent lorsque vous activez les journaux en détail sur les environnements de production qui reçoivent beaucoup de trafic. Dans le futur, il est possible qu&#39;il y ait des mécanismes pour changer plus rapidement le niveau du journal.

### Thread Dumps {#thread-dumps}

Les vidages de threads dans les environnements Cloud sont collectés en permanence, mais ne peuvent pas être téléchargés en libre-service pour le moment. Dans l’intervalle, contactez le support AEM si des virements de threads sont nécessaires pour déboguer un problème, en spécifiant la fenêtre de temps exacte.

### CRX/DE Lite et console système {#crxde-lite-and-system-console}

## Développement local {#local-development}

Pour le développement local, les développeurs ont un accès complet à CRXDE Lite (`/crx/de`) et à la console Web AEM (`/system/console`).

Notez qu’en cas de développement local (à l’aide du démarrage rapide prêt pour le cloud), `/apps` et `/libs` peuvent être écrits directement, ce qui est différent des environnements Cloud dans lesquels ces dossiers de niveau supérieur sont immuables.

## AEM en tant qu’outils de développement de service cloud {#aem-as-a-cloud-service-development-tools}

Les clients peuvent accéder à CRXDE Lite sur l’environnement de développement, mais pas sur l’étape ou la production. Le référentiel immuable (`/libs`, `/apps`) ne peut pas être écrit au moment de l’exécution. Toute tentative de ce type entraînera des erreurs.

Un ensemble d’outils pour le débogage d’AEM en tant qu’environnements de développement de services Cloud est disponible dans la Console de développement pour les environnements de développement, d’évaluation et de production. L’URL peut être déterminée en ajustant les URL du service d’auteur ou de publication comme suit :

`https://dev-console>-<namespace>.<cluster>.dev.adobeaemcloud.com`

Vous pouvez, à titre de raccourci, utiliser la commande d’interface de ligne de commande Cloud Manager suivante pour lancer la console de développement en fonction d’un paramètre d’environnement décrit ci-dessous :

`aio cloudmanager:open-developer-console <ENVIRONMENTID> --programId <PROGRAMID>`

See [this page](/help/release-notes/home.md) for more information.

Les développeurs peuvent générer des informations d’état et résoudre diverses ressources.

Comme illustré ci-dessous, les informations d’état disponibles incluent l’état des lots, des composants, des configurations OSGI, des index de chêne, des services OSGI et des tâches Sling.

![Console de développement 1](/help/implementing/developing/introduction/assets/devconsole1.png)

Comme illustré ci-dessous, les développeurs peuvent résoudre les dépendances des packages et les servlets :

![Console de développement 2](/help/implementing/developing/introduction/assets/devconsole2.png)

![Console de développement 3](/help/implementing/developing/introduction/assets/devconsole3.png)

Également utile pour le débogage, la console de développement comporte un lien vers l’outil Requête d’explication :

![Dev Console 4](/help/implementing/developing/introduction/assets/devconsole4.png)

**Service de test et de production AEM**

Les clients n’auront pas accès aux outils de développement pour les environnements de test et de production.

### Diagnostics {#diagnostics}

La console système est disponible pour les environnements de développement. Toutefois, les vidages de diagnostic pour l’évaluation et la production ne sont pas disponibles.