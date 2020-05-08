---
title: Conseils de développement pour AEM as a Cloud Service
description: À terminer
translation-type: ht
source-git-commit: 114bc678fc1c6e3570d6d2a29bc034feb68aa56d

---


# Conseils de développement pour AEM as a Cloud Service {#aem-as-a-cloud-service-development-guidelines}

Le code s’exécutant dans AEM as a Cloud Service doit savoir qu’il s’exécute toujours dans une grappe. Cela signifie qu’il y a toujours plusieurs instances en cours d’exécution. Le code doit être résilient, d’autant plus qu’une instance peut être arrêtée à tout moment.

Lors de la mise à jour d’AEM as a Cloud Service, il y aura des instances où l’ancien et le nouveau code s’exécuteront en parallèle. Par conséquent, l’ancien code ne doit pas rompre avec le contenu créé par le nouveau code et le nouveau code doit pouvoir traiter l’ancien contenu.
<!--

>[!NOTE]
> All of the best practices mentioned here hold true for on-premise deployments of AEM, if not stated otherwise. An instance can always stop due to various reasons. However, with Skyline it is more likely to happen therefore an instance stopping is the rule not an exception.

-->

S’il est nécessaire d’identifier le maître dans la grappe, l’API Apache Sling Discovery peut être utilisée pour le détecter.

## État en mémoire {#state-in-memory}

L’état ne doit pas être conservé dans la mémoire, mais conservé dans le référentiel, sans quoi il peut se perdre si une instance est arrêtée.

## État sur le système de fichiers {#state-on-the-filesystem}

Le système de fichiers de l’instance ne doit pas être utilisé dans AEM as a Cloud Service. Le disque est éphémère et sera effacé lorsque les instances sont recyclées. L’utilisation limitée du système de fichiers pour le stockage temporaire lié au traitement des demandes uniques est possible, mais ne doit pas être excessive dans le cas des fichiers volumineux. En effet, elle peut avoir un impact négatif sur le quota d’utilisation des ressources et rencontrer des limitations de disque.

Par exemple, si l’utilisation du système de fichiers n’est pas prise en charge, le niveau de publication doit s’assurer que toutes les données qui doivent être conservées sont transférées vers un service externe pour un stockage à plus long terme.

## Observation {#observation}

De même, compte tenu de tout ce qui se passe de manière asynchrone, comme les actions sur des événements d’observation, il n’est pas garanti que le système de fichiers soit exécuté localement et il doit donc être utilisé avec soin. Cela est vrai pour les événements JCR comme pour les événements de ressources Sling. Au moment d’un changement, l’instance peut être supprimée et remplacée par une autre instance. D’autres instances de la topologie actives à ce moment-là pourront réagir à cet événement. Dans ce cas, cependant, il ne s’agira pas d’un événement local et il se pourrait même qu’il n’y ait pas de leader actif dans le cas d’une élection de leader en cours au moment de l’émission de l’événement.

## Tâches en arrière-plan et tâches à long terme {#background-tasks-and-long-running-jobs}

Le code exécuté en tant que tâches en arrière-plan doit prendre en compte le fait que l’instance dans laquelle il est exécuté peut être supprimée à tout moment. Par conséquent, le code doit être résilient et la plupart des importations doivent pouvoir être reproduites. Cela signifie que si le code est réexécuté, il ne doit pas recommencer à partir du début, mais plutôt à partir de l’endroit où il a été abandonné. Bien que cette exigence ne soit pas nouvelle pour ce type de code, il est plus probable qu’une suppression d’instance se produise dans AEM as a Cloud Service.

Afin de limiter les problèmes, il est nécessaire d’éviter les tâches à long terme autant que possible, et de faire en sorte qu’elles puissent autant que possible être reprises après avoir été interrompues. Pour exécuter de telles tâches, utilisez les tâches Sling qui offrent la garantie qu’elles redémarreront au moins une fois si elles sont interrompues, et qu’elles seront donc réexécutées dès que possible. Elles ne doivent cependant probablement pas recommencer depuis le début. Pour planifier de telles tâches, il est préférable d’utiliser le planificateur de [tâches Sling](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#jobs-guarantee-of-processing), car il permet également l’exécution au moins une fois.

Le planificateur Sling Commons ne doit pas être utilisé pour la planification, car l’exécution ne peut pas être garantie. Il permet simplement d’augmenter la probabilité de la programmation.

De même, avec tout ce qui se passe de manière asynchrone, comme les actions sur des événements d’observation (c’est-à-dire des événements JCR ou des événements de ressources Sling), il n’est pas garanti qu’ils soient exécutés et doivent donc être utilisés avec soin. C’est déjà le cas actuellement pour les déploiements d’AEM.

## Connexions HTTP sortantes {#outgoing-http-connections}

Il est vivement recommandé que toute connexion HTTP sortante définisse des délais d’attente raisonnables pour la connexion et la lecture. Pour le code qui n’applique pas ces délais d’expiration, les instances AEM s’exécutant sur AEM as a Cloud Service appliqueront un délai d’expiration global. Ces valeurs de délai d’expiration sont de 10 secondes pour les appels de connexion et de 60 secondes pour les appels de lecture pour les connexions utilisées par les principales bibliothèques Java suivantes :

Adobe recommande l’utilisation de la bibliothèque [Apache HttpComponents Client 4.x](https://hc.apache.org/httpcomponents-client-ga/) fournie pour établir les connexions HTTP.

Les alternatives connues et qui fonctionnent, mais qui peuvent nécessiter de fournir la dépendance vous-même, sont les suivantes :

* [java.net.URL](https://docs.oracle.com/javase/7/docs/api/java/net/URL.html) ou [java.net.URLConnection](https://docs.oracle.com/javase/7/docs/api/java/net/URLConnection.html) (fournies par AEM)
* [Apache Commons HttpClient 3.x](https://hc.apache.org/httpclient-3.x/) (non recommandées, car obsolètes et remplacées par la version 4.x)
* [OK Http](https://square.github.io/okhttp/) (non fourni par AEM)

## Aucune personnalisation classique de l’interface utilisateur {#no-classic-ui-customizations}

AEM as a Cloud Service ne prend en charge que l’interface utilisateur tactile pour le code client tiers. L’interface utilisateur classique n’est pas disponible pour la personnalisation.

## Éviter les fichiers binaires natifs {#avoid-native-binaries}

Le code ne pourra pas télécharger de fichiers binaires au moment de l’exécution ni les modifier. Par exemple, il ne sera pas en mesure de décompresser les fichiers `jar` ou `tar`.

## Pas de fichiers binaires de diffusion via AEM as a Cloud Service {#no-streaming-binaries}

Les fichiers binaires doivent être accessibles via le réseau CDN, qui diffusera des fichiers binaires en dehors des services AEM principaux.

Par exemple, n’utilisez pas `asset.getOriginal().getStream()`, qui déclenche le téléchargement d’un fichier binaire sur le disque éphémère du service AEM.

## Aucun agent de réplication inverse {#no-reverse-replication-agents}

La réplication inverse de l’instance de publication vers l’instance d’auteur n’est pas prise en charge dans AEM as a Cloud Service. Si une telle stratégie est nécessaire, vous pouvez utiliser un espace de stockage persistant externe qui est partagé entre la ferme d’instances de publication et potentiellement la grappe d’auteur.

## Les agents de réplication de transfert peuvent nécessiter un portage {#forward-replication-agents}

Le contenu est répliqué de l’instance d’auteur vers l’instance de publication au moyen d’un mécanisme pub-sub. Les agents de réplication personnalisés ne sont pas pris en charge.

## Surveillance et débogage {#monitoring-and-debugging}

### Journaux {#logs}

Pour le développement en local, les entrées de journaux sont écrites dans des fichiers locaux  dans le dossier `/crx-quickstart/logs`.

Dans les environnements cloud, les développeurs peuvent télécharger les journaux via Cloud Manager ou utiliser un outil de ligne de commande pour en afficher les dernières lignes. <!-- See the [Cloud Manager documentation](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) for more details. Note that custom logs are not supported and so all logs should be output to the error log. -->

**Définition du niveau de journalisation**

Pour modifier les niveaux de journal des environnements Cloud, il est nécessaire de modifier la configuration d’enregistreur OSGI Sling, suivi d’un redéploiement complet. Comme il ne s’agit pas d’une opération instantanée, soyez prudent lorsque vous activez les journaux en détail sur les environnements de production qui reçoivent beaucoup de trafic. Dans le futur, il est possible que des mécanismes soient ajoutés pour pouvoir modifier plus rapidement le niveau du journal.

>[!NOTE]
>
>Pour effectuer les modifications de configuration répertoriées ci-dessous, vous devez les créer dans un environnement de développement local, puis les transmettre à une instance AEM as a Cloud Service. Pour plus d’informations sur la procédure à suivre, voir [Déploiement sur AEM as a Cloud Service](/help/implementing/deploying/overview.md).

**Activation du niveau de journalisation DEBUG**

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

### Images mémoire de threads {#thread-dumps}

Les images mémoire de threads dans les environnements Cloud sont collectés en permanence, mais ne peuvent pas être téléchargées en libre-service pour le moment. En attendant, contactez l’assistance AEM si des images mémoire de threads sont nécessaires pour déboguer un problème, en spécifiant la fenêtre de temps exacte.

## Consoles CRX/DE Lite et système {#crxde-lite-and-system-console}

### Développement local {#local-development}

Pour le développement local, les développeurs ont un accès complet à CRXDE Lite (`/crx/de`) et à la console web AEM (`/system/console`).

Notez qu’en cas de développement local (à l’aide du démarrage rapide disponible pour le cloud), les `/apps` et `/libs` peuvent être modifiés directement, ce qui diffère des environnements Cloud dans lesquels ces dossiers de niveau supérieur sont immuables.

### Outils de développement AEM as a Cloud Service {#aem-as-a-cloud-service-development-tools}

Les clients peuvent accéder à CRXDE Lite sur l’environnement de développement, mais pas sur l’étape ou la production. Le référentiel immuable (`/libs`, `/apps`) ne peut pas être modifié au moment de l’exécution. Toute tentative de ce type entraînera des erreurs.

Un ensemble d’outils pour le débogage des environnements de développeur d’AEM as a Cloud Service est disponible dans la Console de développement pour les environnements de développement, d’évaluation et de production. L’URL peut être déterminée en ajustant les URL du service d’auteur ou de publication comme suit :

`https://dev-console/-<namespace>.<cluster>.dev.adobeaemcloud.com`

Vous pouvez utiliser comme raccourci la commande d’interface de ligne de commande Cloud Manager suivante pour lancer la console de développement, en fonction du paramètre d’environnement décrit ci-dessous :

`aio cloudmanager:open-developer-console <ENVIRONMENTID> --programId <PROGRAMID>`

Pour plus d’informations, consultez [cette page](/help/release-notes/home.md).

Les développeurs peuvent générer des informations d’état et résoudre diverses ressources.

Comme illustré ci-dessous, les informations d’état disponibles incluent l’état des lots, des composants, des configurations OSGI, des index Oak, des services OSGI et des tâches Sling.

![Console de développement 1](/help/implementing/developing/introduction/assets/devconsole1.png)

Comme illustré ci-dessous, les développeurs peuvent résoudre les dépendances des packages et les servlets :

![Console de développement 2](/help/implementing/developing/introduction/assets/devconsole2.png)

![Console de développement 3](/help/implementing/developing/introduction/assets/devconsole3.png)

Également utile pour le débogage, la console de développement comprend un lien vers l’outil Requête d’explication :

![Console de développement 4](/help/implementing/developing/introduction/assets/devconsole4.png)

### Service de test et de production AEM {#aem-staging-and-production-service}

Les clients n’auront pas accès aux outils de développement pour les environnements de test et de production.

### Surveillance des performances {#performance-monitoring}

Adobe surveille les performances de l’application et prend des mesures pour remédier à cette détérioration. Actuellement, il n’est pas possible d’observer les mesures d’application.