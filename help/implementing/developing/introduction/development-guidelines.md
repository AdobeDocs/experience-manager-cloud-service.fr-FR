---
title: Conseils de développement sur AEM as a Cloud Service
description: Découvrez les conseils de développement sur AEM as a Cloud Service et les différences importantes avec AEM On-premise et AEM dans AMS.
exl-id: 94cfdafb-5795-4e6a-8fd6-f36517b27364
feature: Developing
role: Admin, Architect, Developer
source-git-commit: c7ba218faac76c9f43d8adaf5b854676001344cd
workflow-type: tm+mt
source-wordcount: '2768'
ht-degree: 58%

---

# Conseils de développement pour AEM as a Cloud Service {#aem-as-a-cloud-service-development-guidelines}

>[!CONTEXTUALHELP]
>id="development_guidelines"
>title="Conseils de développement sur AEM as a Cloud Service"
>abstract="Découvrez les conseils de développement sur AEM as a Cloud Service et les différences importantes avec AEM On-premise et AEM dans AMS."
>additional-url="https://video.tv.adobe.com/v/330555/?captions=fre_fr" text="Démonstration de la structure du package"

Ce document présente les conseils de développement sur AEM as a Cloud Service et les différences importantes avec AEM On-premise et AEM dans AMS.

## Le code doit être adapté aux clusters {#cluster-aware}

Le code s’exécutant dans AEM as a Cloud Service doit savoir qu’il s’exécute toujours dans une grappe. Cela signifie qu’il y a toujours plusieurs instances en cours d’exécution. Le code doit être résilient, d’autant plus qu’une instance peut être arrêtée à tout moment.

Lors de la mise à jour d’AEM as a Cloud Service, il existe des instances dans lesquelles l’ancien et le nouveau code s’exécuteront en parallèle. Par conséquent, l’ancien code ne doit pas rompre avec le contenu créé par le nouveau code et le nouveau code doit être en mesure de traiter l’ancien contenu.

S’il est nécessaire d’identifier le principal dans le cluster, l’API Discovery Apache Sling peut être utilisée pour le détecter.

## Statut en mémoire {#state-in-memory}

Le statut ne doit pas être conservé dans la mémoire, mais conservé dans le référentiel, sans quoi il peut se perdre si une instance est arrêtée.

## Statut sur le système de fichiers {#state-on-the-filesystem}

N’utilisez pas le système de fichiers de l’instance dans AEM as a Cloud Service. Le disque est éphémère et est éliminé lors du recyclage des instances. L’utilisation limitée du système de fichiers pour le stockage temporaire lié au traitement des demandes uniques est possible, mais ne doit pas être excessive dans le cas des fichiers volumineux. En effet, elle peut avoir un impact négatif sur le quota d’utilisation des ressources et rencontrer des limitations de disque.

À titre d’exemple, lorsque l’utilisation du système de fichiers n’est pas prise en charge, le niveau Publication doit s’assurer que toutes les données qui doivent être conservées sont envoyées à un service externe pour un stockage à plus long terme.

## Observation {#observation}

De même, avec tout ce qui se produit de manière asynchrone, comme une action sur des événements d’observation, il ne peut pas être garanti qu’il sera exécuté localement et doit donc être utilisé avec précaution. Cela est vrai pour les événements JCR comme pour les événements de ressources Sling. Au moment où une modification se produit, l’instance peut être arrêtée et remplacée par une autre instance. D’autres instances de la topologie actives à ce moment-là peuvent réagir à cet événement. Dans ce cas, cependant, il ne s&#39;agira pas d&#39;un événement local et il se peut même qu&#39;il n&#39;y ait pas de chef actif dans le cas d&#39;une élection à la direction en cours lorsque l&#39;événement sera publié.

## Tâches en arrière-plan et tâches à long terme {#background-tasks-and-long-running-jobs}

Le code exécuté en tant que tâche en arrière-plan doit supposer que l’instance dans laquelle il est exécuté peut être supprimée à tout moment. Par conséquent, le code doit être résilient et, surtout, peut être repris. Cela signifie que si le code est réexécuté, il ne doit pas repartir du début, mais plutôt proche de l’endroit où il s’est arrêté. Bien qu’il ne s’agisse pas d’une nouvelle exigence pour ce type de code, dans AEM as a Cloud Service, il est plus probable qu’une suppression d’instance se produise.

Pour minimiser les problèmes, les tâches de longue durée doivent être évitées si possible, et elles doivent pouvoir être reprises au minimum. Pour exécuter de telles tâches, utilisez les tâches Sling qui offrent la garantie qu’elles redémarreront au moins une fois si elles sont interrompues, et qu’elles seront donc réexécutées dès que possible. Elles ne doivent cependant probablement pas recommencer depuis le début. Pour planifier de telles tâches, il est préférable d’utiliser le planificateur de [tâches Sling](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#jobs-guarantee-of-processing), car il permet également l’exécution au moins une fois.

N’utilisez pas le planificateur Sling Commons pour la planification, car l’exécution ne peut pas être garantie. Il permet simplement d’augmenter la probabilité de la programmation.

De même, avec tout ce qui se produit de manière asynchrone, comme une action sur des événements d’observation (qu’il s’agisse d’événements JCR ou d’événements de ressource Sling), l’exécution ne peut pas être garantie et doit donc être utilisée avec précaution. C’est déjà le cas actuellement pour les déploiements d’AEM.

## Connexions HTTP sortantes {#outgoing-http-connections}

Il est vivement recommandé que toutes les connexions HTTP sortantes définissent des délais de connexion et de lecture raisonnables ; les valeurs suggérées sont de 1 seconde pour le délai de connexion et de 5 secondes pour le délai de lecture. Les nombres exacts doivent être déterminés en fonction des performances du système principal qui gère ces requêtes.

Pour le code qui n’applique pas ces délais d’expiration, les instances AEM s’exécutant sur AEM as a Cloud Service appliqueront un délai d’expiration global. Ces valeurs de délai sont de 10 secondes pour les appels de connexion et de 60 secondes pour les appels de lecture pour les connexions.

Adobe recommande l’utilisation de la bibliothèque [Apache HttpComponents Client 4.x](https://hc.apache.org/httpcomponents-client-ga/) fournie pour établir les connexions HTTP.

Les alternatives connues et qui fonctionnent, mais qui peuvent nécessiter de fournir la dépendance vous-même, sont les suivantes :

* [java.net.URL](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/net/URL.html) ou [java.net.URLConnection](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/net/URLConnection.html) (fournies par AEM)
* [Apache Commons HttpClient 3.x](https://hc.apache.org/httpclient-3.x/) (non recommandées, car obsolètes et remplacées par la version 4.x)
* [OK Http](https://square.github.io/okhttp/) (non fourni par AEM)

En plus de fournir des délais d’expiration, une gestion appropriée de ces délais et des codes de statut HTTP inattendus doivent être implémentés.

## Gérer les limites de taux de requête {#rate-limit-handling}

Lorsque le taux de requêtes entrantes vers AEM dépasse les niveaux sains, AEM répond aux nouvelles requêtes avec le code d’erreur HTTP 429. Les applications qui effectuent des appels programmatiques vers AEM peuvent envisager un codage défensif, en réessayant après quelques secondes avec une stratégie d’interruption exponentielle. Avant la mi-août 2023, AEM répondait à la même condition avec le code d’erreur HTTP 503.

## Aucune personnalisation classique de l’interface utilisateur {#no-classic-ui-customizations}

AEM as a Cloud Service ne prend en charge que l’interface utilisateur tactile pour le code client tiers. L’interface utilisateur classique n’est pas disponible pour la personnalisation.

## Pas de fichiers binaires natifs ni de bibliothèques natives {#avoid-native-binaries}

Les fichiers binaires et bibliothèques natifs ne doivent pas être déployés sur ou installés dans des environnements cloud.

En outre, le code ne doit pas tenter de télécharger des fichiers binaires natifs ou des extensions Java natives (par exemple, JNI) au moment de l’exécution.

## Pas de fichiers binaires de diffusion via AEM as a Cloud Service {#no-streaming-binaries}

Les fichiers binaires doivent être accessibles via le réseau de diffusion de contenu, qui diffusera des fichiers binaires en dehors des services AEM principaux.

Par exemple, n’utilisez pas `asset.getOriginal().getStream()`, qui déclenche le téléchargement d’un fichier binaire sur le disque éphémère du service AEM.

## Aucun agent de réplication inverse {#no-reverse-replication-agents}

La réplication inverse de l’instance de publication vers l’instance d’auteur n’est pas prise en charge dans AEM as a Cloud Service. Si une telle stratégie est nécessaire, vous pouvez utiliser un espace de stockage persistant externe qui est partagé entre la ferme d’instances de publication et potentiellement la grappe d’auteur.

## Les agents de réplication en avant peuvent nécessiter un portage {#forward-replication-agents}

Le contenu est répliqué de l’instance d’auteur vers l’instance de publication au moyen d’un mécanisme pub-sub. Les agents de réplication personnalisés ne sont pas pris en charge.

## Ne Pas Surcharger Les Environnements De Développement {#overloading-dev-envs}

Les environnements de production sont dimensionnés de manière à garantir un fonctionnement stable, tandis que les environnements intermédiaires sont dimensionnés de la même manière que les environnements de production afin de garantir des tests réalistes dans des conditions de production.

Les environnements de développement et de développement rapide doivent se limiter au développement, à l’analyse des erreurs et aux tests fonctionnels. Ils ne sont pas conçus pour traiter des charges de travail élevées ou de grandes quantités de contenu.

Par exemple, la modification d’une définition d’index sur un référentiel de contenu volumineux dans un environnement de développement peut entraîner une réindexation et un traitement excessif. Les tests qui nécessitent du contenu important doivent être exécutés sur des environnements intermédiaires.

## Surveillance et débogage {#monitoring-and-debugging}

### Journaux {#logs}

Pour le développement en local, les entrées de journal sont écrites dans des fichiers locaux dans le dossier `/crx-quickstart/logs`.

Dans les environnements cloud, les développeurs peuvent télécharger les journaux via Cloud Manager ou utiliser un outil de ligne de commande pour les consulter. <!-- See the [Cloud Manager documentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html?lang=fr) for more details. Custom logs are not supported and so all logs should be output to the error log. -->

**Définition du niveau de journalisation**

Pour modifier les niveaux de journal des environnements Cloud, il est nécessaire de modifier la configuration d’enregistreur OSGi Sling, suivi d’un redéploiement complet. Comme cette opération n’est pas instantanée, veillez à activer les journaux détaillés sur les environnements de production qui reçoivent beaucoup de trafic. Dans le futur, il est possible que des mécanismes soient ajoutés pour pouvoir modifier plus rapidement le niveau du journal.

>[!NOTE]
>
>Pour effectuer les modifications de configuration répertoriées ci-dessous, créez-les dans un environnement de développement local, puis transmettez-les à une instance AEM as a Cloud Service. Pour plus d’informations sur la procédure à suivre, voir [Déploiement sur AEM as a Cloud Service](/help/implementing/deploying/overview.md).

**Activation du niveau de journalisation DEBUG**

Le niveau de journalisation par défaut est INFO, ce qui signifie que les messages DEBUG ne sont pas consignés. Pour activer le niveau de journalisation DEBUG, mettez à jour la propriété suivante vers le mode Déboguer.

`/libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level`

Par exemple, définissez `/apps/<example>/config/org.apache.sling.commons.log.LogManager.factory.config~<example>.cfg.json` avec la valeur suivante.

```json
{
   "org.apache.sling.commons.log.names": [
      "com.example"
   ],
   "org.apache.sling.commons.log.level": "DEBUG",
   "org.apache.sling.commons.log.file": "logs/error.log",
   "org.apache.sling.commons.log.additiv": "false"
}
```

Ne laissez pas le journal au niveau de débogage DEBUG plus longtemps que nécessaire, car cela génère un grand nombre d’entrées.

Des niveaux de journal distincts peuvent être définis pour les différents environnements AEM à l’aide du ciblage de la configuration OSGi basée sur le mode d’exécution s’il est souhaitable de toujours se connecter à `DEBUG` pendant le développement. Par exemple :

| Environnement | Emplacement de configuration OSGi par mode d’exécution | Valeur de propriété `org.apache.sling.commons.log.level` |
| - | - | - |
| Développement | /apps/example/config/org.apache.sling.commons.log.LogManager.factory.config~example.cfg.json | DEBUG |
| Évaluation | /apps/example/config.stage/org.apache.sling.commons.log.LogManager.factory.config~example.cfg.json | WARN |
| Production | /apps/example/config.prod/org.apache.sling.commons.log.LogManager.factory.config~example.cfg.json | ERROR |

Une ligne dans le fichier de débogage commence généralement par DEBUG, puis fournit le niveau de journalisation, l’action du programme d’installation et le message du journal. Par exemple :

```text
DEBUG 3 WebApp Panel: WebApp successfully deployed
```

Les niveaux de journal sont les suivants :

| 0 | Erreur fatale | L’action a échoué et le programme d’installation ne peut pas continuer. |
|---|---|---|
| 1 | Erreur | L’action a échoué. L’installation se poursuit, mais une partie de CRX n’a pas été installée correctement et ne fonctionnera pas. |
| 2 | Avertissement | L’action a réussi, mais a rencontré des problèmes. CRX risque de ne pas fonctionner correctement. |
| 3 | Informations | L’action a réussi. |

### Images mémoire de threads {#thread-dumps}

Les images mémoire de threads dans les environnements Cloud sont collectés en permanence, mais ne peuvent pas être téléchargées en libre-service pour le moment. En attendant, contactez l’assistance AEM si des images mémoire de threads sont nécessaires pour déboguer un problème, en spécifiant la fenêtre temporelle exacte.

## CRX/DE Lite et AEM as a Cloud Service Developer Console {#crxde-lite-and-developer-console}

### Développement local {#local-development}

Pour le développement local, les développeurs ont un accès complet à CRXDE Lite (`/crx/de`) et à la console web AEM (`/system/console`).

Lors du développement local (à l’aide du SDK), les `/apps` et les `/libs` peuvent être modifiés directement, ce qui diffère des environnements Cloud, où ces dossiers de niveau supérieur sont immuables.

### Outils de développement AEM as a Cloud Service {#aem-as-a-cloud-service-development-tools}

>[!NOTE]
>Le Developer Console AEM as a Cloud Service ne doit pas être confondu avec le Adobe Developer Console [*&#128279;*](https://developer.adobe.com/developer-console/).
>

>[!NOTE]
>Certains clients auront la possibilité de tester une expérience repensée pour le Developer Console AEM Cloud Service. Voir [cet article](/help/implementing/developing/introduction/aem-developer-console.md) pour plus d’informations.

Les clients peuvent accéder à CRXDE lite dans l’environnement de développement du niveau création, mais pas dans les environnements d’évaluation ni de production. Le référentiel immuable (`/libs`, `/apps`) ne peut pas être modifié au moment de l’exécution. Toute tentative de ce type entraînera des erreurs.

Au lieu de cela, vous pouvez lancer l’explorateur de référentiels à partir d’AEM as a Cloud Service Developer Console, ce qui vous permet d’accéder au référentiel en lecture seule pour tous les environnements sur les niveaux de création, de publication et de prévisualisation. Pour plus d’informations, voir [Navigateur de référentiels](/help/implementing/developing/tools/repository-browser.md).

Un ensemble d’outils pour le débogage des environnements de développement AEM as a Cloud Service est disponible dans AEM as a Cloud Service Developer Console pour les environnements de RDE, de développement, d’évaluation et de production. L’URL peut être déterminée en ajustant les URL du service de création ou de publication comme suit :

`https://dev-console-<namespace>.<cluster>.dev.adobeaemcloud.com`

Pour raccourcir ce processus, utilisez la commande d’interface de ligne de commande Cloud Manager suivante pour lancer AEM as a Cloud Service Developer Console en fonction d’un paramètre d’environnement décrit ci-dessous :

`aio cloudmanager:open-developer-console <ENVIRONMENTID> --programId <PROGRAMID>`

Voir [Informations de mise à jour](/help/release-notes/home.md) pour plus d’informations.

Les développeurs peuvent générer des informations de statut et résoudre diverses ressources.

Comme illustré ci-dessous, les informations de statut disponibles incluent l’état des lots, des composants, des configurations OSGi, des index Oak, des services OSGi et des tâches Sling.

![Console de développement 1](/help/implementing/developing/introduction/assets/devconsole1.png)

Comme illustré ci-dessous, les développeurs peuvent résoudre les dépendances des packages et les servlets :

![Console de développement 2](/help/implementing/developing/introduction/assets/devconsole2.png)

![Console de développement 3](/help/implementing/developing/introduction/assets/devconsole3.png)

Également utile pour le débogage, le Developer Console AEM as a Cloud Service comporte un lien vers l’outil Expliquer la requête :

![Console de développement 4](/help/implementing/developing/introduction/assets/devconsole4.png)

Pour les programmes de production, l’accès à AEM as a Cloud Service Developer Console est défini par la mention « Cloud Manager - Rôle de développeur » dans Adobe Admin Console, tandis que pour les programmes Sandbox, AEM as a Cloud Service Developer Console est disponible pour tout utilisateur disposant d’un profil de produit qui lui donne accès à AEM as a Cloud Service. Pour tous les programmes, « Cloud Manager – Rôle de développement » est nécessaire pour les vidages de statut et le navigateur de référentiels. Les utilisateurs et les utilisatrices doivent également être définis dans le profil de produit Utilisateurs et utilisatrices d’AEM ou Administrateurs et administratrices d’AEM sur les services de création et de publication pour afficher les données des deux services. Pour plus d’informations sur la configuration des autorisations des utilisateurs, voir [Documentation de Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=fr).

### Surveillance des performances {#performance-monitoring}

Adobe surveille les performances des applications et prend des mesures pour remédier à toute détérioration si elle est observée. Actuellement, les mesures de l’application ne peuvent pas être observées.

## Envoi d’un e-mail {#sending-email}

Les sections ci-dessous décrivent comment demander, configurer et envoyer des e-mails.

>[!NOTE]
>
>Le service de messagerie peut être configuré avec la prise en charge d’OAuth2. Pour plus d’informations, voir [Prise en charge d’OAuth2 pour le service de messagerie](/help/security/oauth2-support-for-mail-service.md).

### Activation de l’e-mail sortant {#enabling-outbound-email}

Par défaut, les ports utilisés pour envoyer des e-mails sont désactivés. Pour activer un port, configurez la [mise en réseau avancée](/help/security/configuring-advanced-networking.md) en veillant à définir pour chaque environnement nécessaire les règles de transfert du port de point d’entrée `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking`, ce qui mappe le port prévu (par exemple, 465 ou 587) à un port proxy.

Il est recommandé de configurer une mise en réseau avancée avec un paramètre de `kind` défini sur `flexiblePortEgress`, car Adobe peut optimiser les performances du trafic de sortie de port flexible. Si une adresse IP sortante unique est nécessaire, choisissez un paramètre `kind` de `dedicatedEgressIp`. Si vous avez déjà configuré un VPN pour d’autres raisons, vous pouvez également utiliser l’adresse IP unique fournie par cette variante de mise en réseau avancée.

Vous devez envoyer un e-mail par l’intermédiaire d’un serveur de messagerie plutôt que directement aux clients de messagerie. Sans cela, les e-mails pourraient être bloqués.

### Envoi d’e-mails {#sending-emails}

Le service de messagerie [Day CQ OSGI](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/notification.html?lang=fr#configuring-the-mail-service) doit être utilisé et les e-mails doivent être envoyés au serveur de messagerie indiqué dans la demande d’assistance, et non directement aux destinataires.

### Configuration {#email-configuration}

Dans AEM, les emails doivent être envoyés à l’aide du [service de messagerie Day CQ OSGi](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/notification.html?lang=fr#configuring-the-mail-service).

Voir la [documentation d’AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/notification.html?lang=fr) pour plus d’informations sur la configuration des paramètres des e-mails. Pour AEM as a Cloud Service, notez les modifications nécessaires suivantes pour le service `com.day.cq.mailer.DefaultMailService OSGI` :

* Le nom d’hôte du serveur SMTP doit être défini sur $[env:AEM_PROXY_HOST;default=proxy.tunnel]
* Le port du serveur SMTP doit être défini sur la valeur du port proxy d’origine défini dans le paramètre portForwards utilisé dans l’appel de l’API lors de la configuration de la mise en réseau avancée. Par exemple, 30465 (plutôt que 465).

Le port du serveur SMTP doit être défini comme valeur `portDest` définie dans le paramètre portForwards utilisé dans l’appel API lors de la configuration d’une mise en réseau avancée, et la valeur `portOrig` doit être une valeur significative comprise dans la plage requise entre 30000 et 30999. Par exemple, si le port du serveur SMTP est 465, le port 30465 doit être utilisé en tant que valeur `portOrig`.

Dans ce cas, et en supposant que le SSL doive être activé, dans la configuration du service de messagerie **Day CQ OSGI** :

* Définissez `smtp.port` sur `30465`.
* Définissez `smtp.ssl` sur `true`.

Autrement, si le port de destination est le 587, une valeur `portOrig` de 30587 doit être utilisée. En supposant que le SSL doive être désactivé, la configuration du service de messagerie Day CQ OSGI :

* Définissez `smtp.port` sur `30587`.
* Définissez `smtp.ssl` sur `false`.

La propriété `smtp.starttls` sera automatiquement définie par AEM as a Cloud Service au moment de son exécution sur une valeur appropriée. Par conséquent, si `smtp.ssl` est défini sur true, `smtp.startls` est ignoré. Si `smtp.ssl` est défini sur false, `smtp.starttls` est défini sur true. Cette règle s’applique indépendamment des valeurs de `smtp.starttls` définies dans votre configuration OSGI.


Le service de messagerie peut également être configuré avec la prise en charge d’OAuth2. Pour plus d’informations, voir [Prise en charge d’OAuth2 pour le service de messagerie](/help/security/oauth2-support-for-mail-service.md).

### Configuration d’e-mail héritée {#legacy-email-configuration}

Avant la version 2021.9.0, l’e-mail était configuré par le biais d’une demande du service clientèle. Notez les modifications nécessaires suivantes pour le service `com.day.cq.mailer.DefaultMailService OSGI` :

AEM as a Cloud Service nécessite que l’e-mail soit envoyé via le port 465. Si un serveur de messagerie ne prend pas en charge le port 465, il est possible d’utiliser le port 587 tant que l’option TLS est activée.

Si le port 465 a été demandé :

* Définissez `smtp.port` sur `465`.
* Définissez `smtp.ssl` sur `true`.

Si le port 587 a été demandé :

* Définissez `smtp.port` sur `587`.
* Définissez `smtp.ssl` sur `false`.

La propriété `smtp.starttls` sera automatiquement définie par AEM as a Cloud Service au moment de son exécution sur une valeur appropriée. Par conséquent, si `smtp.ssl` est défini sur true, `smtp.startls` est ignoré. Si `smtp.ssl` est défini sur false, `smtp.starttls` est défini sur true. Cette règle s’applique indépendamment des valeurs de `smtp.starttls` définies dans votre configuration OSGI.

L’hôte du serveur SMTP doit être défini sur celui de votre serveur de messagerie.

## Éviter les nombreuses propriétés à plusieurs valeurs {#avoid-large-mvps}

Le référentiel de contenu Oak sous-jacent à AEM as a Cloud Service n’est pas destiné à être utilisé avec un nombre excessif de propriétés à plusieurs valeurs (MVP, multi-value properties). Une règle de base consiste à maintenir les MVP en dessous de 1 000. Toutefois, les performances réelles dépendent de nombreux facteurs.

Les avertissements sont consignés par défaut après avoir dépassé 1 000. Ils se présentent comme suit.

```text
org.apache.jackrabbit.oak.jcr.session.NodeImpl Large multi valued property [/path/to/property] detected (1029 values). 
```

En raison du document MongoDB dépassant 16 Mo, les MVP trop nombreuses peuvent entraîner des erreurs similaires à celles-ci.

```text
Caused by: com.mongodb.MongoWriteException: Resulting document after update is larger than 16777216
```

Pour plus d’informations, consultez la [documentation d’Apache Oak](https://jackrabbit.apache.org/oak/docs/dos_and_donts.html#Large_Multi_Value_Property).

## Directives de développement et cas pratiques concernant [!DNL Assets] {#use-cases-assets}

Pour découvrir les cas d’utilisation de développement, les recommandations et les documents de référence pour Assets as a Cloud Service, consultez les [références de développement pour Assets](/help/assets/developer-reference-material-apis.md#assets-cloud-service-apis).
