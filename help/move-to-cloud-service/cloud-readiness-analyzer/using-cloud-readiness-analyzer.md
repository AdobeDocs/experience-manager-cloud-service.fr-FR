---
title: Utilisation de Cloud Readiness Analyzer
description: Utilisation de Cloud Readiness Analyzer
translation-type: tm+mt
source-git-commit: a0e58c626f94b778017f700426e960428b657806
workflow-type: tm+mt
source-wordcount: '1871'
ht-degree: 75%

---


# Utilisation de Cloud Readiness Analyzer {#using-cloud-readiness-analyzer}

## Points importants concernant l’utilisation de Cloud Readiness Analyzer {#imp-considerations}

Suivez la section ci-dessous pour comprendre les points importants à prendre en compte pour l&#39;exécution de l&#39;outil Cloud Readiness Analyzer (CRA) :

* Les rapports CRA sont générés à l’aide des résultats obtenus par le [détecteur de motifs](https://docs.adobe.com/content/help/fr-FR/experience-manager-65/deploying/upgrading/pattern-detector.html) d’Adobe Experience Manager (AEM). La version du détecteur de motifs utilisée par CRA se trouve dans le module d’installation CRA.

* CRA may only be run by the **admin** user or a user in the **administrators** group.

* L’outil est pris en charge sur les instances AEM avec la version 6.1 et versions ultérieures.

   >[!NOTE]
   > Consultez [Installation sur AEM 6.1](#installing-on-aem61) pour connaître les conditions particulières d’installation de CRA sur AEM 6.1.

* Il peut s’exécuter dans n’importe quel environnement, mais il est préférable de l’exécuter dans un environnement d’*évaluation*.

   >[!NOTE]
   >In order to avoid an impact on business critical instances, it is recommended that you run CRA on an *Author* environment that is as close as possible to the *Production* environment in the areas of customizations, configurations, content and user applications. Vous pouvez également l’exécuter sur un clone de l’environnement de *création* de production.

* La génération du contenu des rapports CRA peut nécessiter un temps important, de plusieurs minutes à quelques heures. La durée nécessaire dépend largement de la taille et de la nature du contenu du référentiel AEM, de la version d’AEM et d’autres facteurs.

* En raison du temps éventuellement nécessaire pour générer le contenu du rapport, celui-ci est créé par un processus en arrière-plan et conservé dans un cache. L’affichage et le téléchargement du rapport doivent être relativement rapides, car il utilise le cache de contenu jusqu’à son expiration ou s’il est explicitement actualisé. Pendant la génération du contenu du rapport, vous pouvez fermer l’onglet du navigateur et revenir ultérieurement à l’affichage du rapport lorsque son contenu est disponible dans le cache.

## Disponibilité {#availability}

L&#39;analyseur de l&#39;état de préparation de Cloud peut être téléchargé sous la forme d&#39;un fichier zip depuis le portail de distribution de logiciels. Vous pouvez installer le module par le biais du gestionnaire de modules sur votre instance source Adobe Experience Manager (AEM).

>[!NOTE]
>Download the Cloud Readiness Analyzer from the [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) portal.

## Viewing the Cloud Readiness Analyzer Report {#viewing-report}

### Adobe Experience Manager 6.3.0, et versions ultérieures {#aem-later-versions}

Suivez cette section pour savoir comment vue le rapport Cloud Readiness Analyzer :

1. Sélectionnez Adobe Experience Manager et accédez à Outils -> **Opérations** -> **Cloud Readiness Analyzer**.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-1.png)

1. Une fois que vous avez cliqué sur **Cloud Readiness Analyzer**, l’outil commence à générer le rapport et l’affiche dès qu’il est disponible.

   >[!NOTE]
   >Vous devrez faire défiler la page vers le bas pour afficher le rapport complet.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-tool-1.png)

1. Une fois le rapport ARC généré et affiché, vous avez la possibilité de télécharger le rapport au format CSV (valeurs séparées par des virgules) en cliquant sur **CSV**, comme le montre la figure ci-dessous.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-tool-2.png)

   >[!NOTE]
   >Vous pouvez forcer CRA à effacer son cache et à générer de nouveau le rapport en cliquant sur **Actualiser le rapport**.

### Adobe Experience Manager 6.2 et 6.1 {#aem-specific-versions}

L’outil Cloud Readiness Analyzer est limité dans l’Adobe Experience Manager 6.2 à un lien qui génère et télécharge le rapport CSV.

Pour Adobe Experience Manager 6.1, l’outil n’est pas fonctionnel et seule l’interface HTTP peut être utilisée.

>[!NOTE]
>Dans toutes les versions, le détecteur de motifs inclus peut s’exécuter de manière indépendante.

## Interprétation des rapports Cloud Readiness Analyzer {#cra-report}

Lorsque l’outil Cloud Readiness Analyzer est exécuté dans l’instance AEM, le rapport s’affiche en tant que résultats dans la fenêtre de l’outil.

Le format du rapport est le suivant :

* **Aperçu** du rapport : Informations sur le rapport lui-même qui incluent les informations suivantes :
   * **Heure** du rapport : Lorsque le contenu du rapport a été généré et rendu disponible pour la première fois.
   * **Heure** d&#39;expiration : Date d&#39;expiration du cache du contenu du rapport.
   * **Période** de génération : Temps passé par le processus de génération du contenu du rapport.
   * **Recherche du décompte**: Nombre total de constatations figurant dans le rapport.
* **System Overview** : informations sur le système AEM sur lequel CRA a été exécuté.
* **Finding Categories** : différentes sections traitant chacune d’un ou plusieurs résultats pour une même catégorie. Chaque section comprend les éléments suivants : nom de la catégorie, sous-types, nombre et importance des résultats, résumé, lien vers la documentation de la catégorie et informations relatives à chaque résultat.

Un niveau d’importance est attribué à chaque résultat pour indiquer une priorité absolue concernant l’action.

Consultez le tableau ci-dessous pour comprendre les niveaux d’importance :

| Importance | Description |
|--- |--- |
| INFO | Ce résultat est fourni à titre d’information. |
| ADVISORY | Ce résultat peut poser un problème de mise à niveau. Il est recommandé d’approfondir les investigations. |
| MAJOR | Il est probable que ce résultat constitue un problème de mise à niveau qui doit être résolu. |
| CRITICAL | Il est très probable que ce résultat constitue un problème de mise à niveau qui doit être résolu pour éviter toute perte de fonction ou de performances. |


## Interprétation du rapport Cloud Readiness Analyzer au format CSV {#cra-csv-report}

Lorsque vous cliquez sur l’option **CSV** de votre instance AEM, le format CSV du rapport Cloud Readiness Analyzer est créé à partir du cache de contenu et renvoyé à votre navigateur. En fonction des paramètres du navigateur, ce rapport sera automatiquement téléchargé sous la forme d’un fichier portant le nom `results.csv` par défaut.

Si le cache a atteint son délai d’expiration, le rapport sera de nouveau généré avant la création et le téléchargement du fichier CSV.

Le format CSV du rapport contient des informations générées à partir de la sortie du détecteur de motifs, triées et organisées par types de catégories, sous-types et niveaux d’importance. Son format est adapté pour permettre l’affichage et la modification dans une application comme Microsoft Excel. La finalité du rapport est de donner toutes les informations relatives aux résultats sous une forme reproductible. Cette démarche peut s’avérer utile lors de la comparaison des rapports au fil du temps pour mesurer les progrès réalisés.

Les colonnes du rapport au format CSV sont les suivantes :

* **code** : code de catégorie
* **type** : nom de la catégorie
* **subtype** : sous-type de catégorie
* **importance** : niveau d’importance
* **identifier** : identifiant principal du résultat
* **other** : informations supplémentaires sur le résultat
* **message** : message fourni pour le résultat
* **moreInfo** : lien utilisable pour accéder à l’aide en ligne à propose de la catégorie
* **context** : chaîne JSON concernant les données du résultat.

La valeur « \N » dans une colonne concernant un résultat individuel indique qu’aucune donnée n’a été fournie.

## Interface HTTP {#http-interface}

CRA fournit une interface HTTP, utilisable comme alternative à son interface utilisateur dans AEM. L’interface prend en charge les commandes HEAD et GET. Il peut être utilisé pour générer le rapport CRA et le renvoyer dans l’un des trois formats suivants : JSON, CSV et TSV (valeurs séparées par des tabulations).

Les URL suivantes sont disponibles pour l’accès HTTP, où `<host>` est le nom d’hôte et, si nécessaire, le port du serveur sur lequel CRA est installé :
* `http://<host>/apps/readiness-analyzer/analysis/result.json` pour le format JSON
* `http://<host>/apps/readiness-analyzer/analysis/result.csv` pour le format CSV
* `http://<host>/apps/readiness-analyzer/analysis/result.tsv` pour le format TSV

### Exécution d’une requête HTTP {#executing-http-request}

Il est possible d’utiliser l’interface HTTP de différentes manières.

Une méthode simple consiste à ouvrir un onglet dans le même navigateur que celui utilisé pour vous connecter à AEM en tant qu’administrateur. Vous pouvez renseigner l’URL dans l’onglet du navigateur et afficher ou télécharger les résultats grâce au navigateur.

Vous pouvez également utiliser un outil de ligne de commande tel que `curl` ou `wget`, mais aussi toute autre application cliente HTTP. Lorsque vous n’utilisez pas l’onglet du navigateur avec une session authentifiée, vous devez fournir un nom d’utilisateur et un mot de passe administratifs dans le cadre du commentaire.

À titre d’exemple, vous pouvez procéder comme suit :
`curl -u admin:admin 'http://localhost:4502/apps/readiness-analyzer/analysis/result.csv' > result.csv`.

### En-têtes et paramètres {#http-headers-and-parameters}

Les en-têtes HTTP suivants sont utilisés par cette interface :

* `Cache-Control: max-age=<seconds>` : spécifie l’intervalle d’actualisation du cache en secondes. (Voir [RFC 7234](https://tools.ietf.org/html/rfc7234#section-5.2.2.8).)
* `Prefer: respond-async` : indique que le serveur doit répondre de manière asynchrone. (Voir [RFC 7240](https://tools.ietf.org/html/rfc7240#section-4.1).)

Les paramètres de requête HTTP suivants sont disponibles à titre de commodité lorsque l’utilisation des en-têtes HTTP risque de ne pas être facile :

* `max-age` (nombre, facultatif) : spécifie l’intervalle d’actualisation du cache en secondes. Ce nombre doit être égal ou supérieur à 0. L’intervalle d’actualisation par défaut est de 86 400 secondes, ce qui signifie que sans ce paramètre ou l’en-tête correspondant, un nouveau cache sera utilisé pour répondre aux demandes pendant 24 heures avant que le rapport ne soit de nouveau généré. L’utilisation de `max-age=0` forcera l’effacement du cache et déclenchera une nouvelle génération du rapport. Immédiatement après cette demande, l’intervalle d’actualisation sera réinitialisé à la valeur antérieure non nulle.
* `respond-async` (booléen, facultatif) : spécifie que la réponse doit être fournie de manière asynchrone. L’utilisation de `respond-async=true`, si le cache est obsolète, entraînera l’envoi par le serveur d’une réponse `202 Accepted, processing cache` sans attendre que le rapport soit généré et que le cache soit actualisé. Si le cache est actualisé, ce paramètre n’a aucun effet. La valeur par défaut est `false`, ce qui signifie que sans ce paramètre ou l’en-tête correspondant, le serveur répondra de manière synchrone. Dans ce cas, la réponse peut nécessiter un temps important et un ajustement du temps de réponse maximal pour le client HTTP.

Si un en-tête HTTP et son paramètre de requête correspondant sont présents simultanément, le paramètre de requête est prioritaire.

La commande suivante est une méthode simple pour lancer la génération du rapport via l’interface HTTP :
`curl -u admin:admin 'http://localhost:4502/apps/readiness-analyzer/analysis/result.json?max-age=0&respond-async=true'`.

Lorsqu’une requête a été effectuée, le client n’a pas besoin de rester actif pour que le rapport soit généré. La génération du rapport peut être lancée avec un client à l’aide d’une requête HTTP GET. Une fois le rapport généré, il peut être affiché à l’aide du cache d’un autre client ou de l’outil CSV de l’interface utilisateur AEM.

### Réponses {#http-responses}

Les valeurs de réponses possibles sont les suivantes :

* `200 OK` : la réponse contient les résultats du détecteur de motifs, générés pendant l’intervalle d’actualisation de la mémoire cache.
* `202 Accepted, processing cache` : fourni pour les réponses asynchrones indiquant que le cache était obsolète et qu’une actualisation est en cours.
* `400 Bad Request` : indique qu’une erreur s’est produite lors de la requête. A message in Problem Details format (see [RFC 7807](https://tools.ietf.org/html/rfc7807)) for more details.
* `401 Unauthorized` : la requête n’a pas été autorisée.
* `500 Internal Server Error` : indique qu’une erreur de serveur interne s’est produite. Un message au format Détails du problème donne des détails supplémentaires.
* `503 Service Unavailable` : indique que le serveur est occupé par une autre réponse et qu’il ne peut pas traiter cette requête dans les délais impartis. Cela n’est probable que lorsque des requêtes synchrones sont effectuées. Un message au format Détails du problème donne des détails supplémentaires.

## Informations sur l’administrateur

### Ajustement de la durée de vie du cache {#cache-adjustment}

La durée de vie par défaut du cache CRA est de 24 heures. Avec l’option destinée à actualiser un rapport et à régénérer le cache, aussi bien dans l’instance AEM que dans l’interface HTTP, cette valeur par défaut sera probablement appropriée pour la plupart des utilisations du CRA. Si le temps de génération du rapport est particulièrement long pour votre instance AEM, vous pouvez ajuster la durée de vie du cache afin de minimiser la nouvelle génération d’un rapport.

La durée de vie du cache est stockée dans la propriété `maxCacheAge` dans le nœud de référentiel suivant :
`/apps/readiness-analyzer/content/CloudReadinessReport/jcr:content`

La valeur de cette propriété est la durée de vie du cache en secondes. Un administrateur peut ajuster la durée de vie du cache à l’aide de CRX/DE Lite.

### Installation sur AEM 6.1 {#installing-on-aem61}

L&#39;ARC utilise un compte utilisateur de service système nommé `repository-reader-service` pour exécuter le Détecteur de schémas. Ce compte est disponible sur AEM 6.2 et versions ultérieures. Dans AEM 6.1, ce compte doit être créé *avant* l’installation de CRA en procédant comme suit :

1. Suivez les instructions de la section [Création d’un utilisateur](https://docs.adobe.com/content/help/en/experience-manager-65/administering/security/security-service-users.html#creating-a-new-service-user) de service pour créer un utilisateur. Définissez l’ID utilisateur sur `repository-reader-service` et laissez le chemin intermédiaire vide, puis cliquez sur la coche verte.

2. Suivez les instructions de la section [Gestion des utilisateurs et des groupes](https://docs.adobe.com/content/help/en/experience-manager-65/administering/security/security.html#managing-users-and-groups), en particulier les instructions pour Ajouter des utilisateurs à un groupe afin d’ajouter l’ `repository-reader-service` utilisateur au `administrators` groupe.

3. Installez le package CRA via Package Manager sur votre instance AEM source. (Ceci ajoutera la modification de configuration nécessaire à la configuration ServiceUserMapper pour l&#39;utilisateur du service `repository-reader-service` système.)
