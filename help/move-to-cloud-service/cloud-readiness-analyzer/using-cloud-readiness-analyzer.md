---
title: Utilisation de Cloud Readiness Analyzer
description: Utilisation de Cloud Readiness Analyzer
translation-type: tm+mt
source-git-commit: 6459a3eae03ec75ed9449f27ad717b90bddf6dec
workflow-type: tm+mt
source-wordcount: '2209'
ht-degree: 71%

---


# Utilisation de Cloud Readiness Analyzer {#using-cloud-readiness-analyzer}

## Points importants concernant l’utilisation de Cloud Readiness Analyzer {#imp-considerations}

Consultez la section ci-dessous afin de comprendre les points importants à prendre en compte pour utiliser l’outil Cloud Readiness Analyzer (CRA) :

* Les rapports CRA sont générés à l’aide des résultats obtenus par le [détecteur de motifs](https://docs.adobe.com/content/help/fr-FR/experience-manager-65/deploying/upgrading/pattern-detector.html) d’Adobe Experience Manager (AEM). La version du détecteur de motifs utilisée par CRA se trouve dans le module d’installation CRA.

* L’outil CRA ne peut être exécuté que par un utilisateur **admin** ou un utilisateur figurant dans le groupe **administrateurs**.

* L’outil est pris en charge sur les instances AEM avec la version 6.1 et versions ultérieures.

   >[!NOTE]
   > Consultez [Installation sur AEM 6.1](#installing-on-aem61) pour connaître les conditions particulières d’installation de CRA sur AEM 6.1.

* Il peut s’exécuter dans n’importe quel environnement, mais il est préférable de l’exécuter dans un environnement d’*évaluation*.

   >[!NOTE]
   >Pour éviter toute incidence sur les instances critiques de l’entreprise, il est recommandé d’exécuter CRA dans un environnement de *création* aussi proche que possible de l’environnement de *production* concernant la personnalisation, la configuration, les contenus et les applications utilisateur. Vous pouvez également l’exécuter sur un clone de l’environnement de *création* de production.

* La génération du contenu des rapports CRA peut nécessiter un temps important, de plusieurs minutes à quelques heures. La durée nécessaire dépend largement de la taille et de la nature du contenu du référentiel AEM, de la version d’AEM et d’autres facteurs.

* En raison du temps éventuellement nécessaire pour générer le contenu du rapport, celui-ci est créé par un processus en arrière-plan et conservé dans un cache. L’affichage et le téléchargement du rapport doivent être relativement rapides, car il utilise le cache de contenu jusqu’à son expiration ou s’il est explicitement actualisé. Pendant la génération du contenu du rapport, vous pouvez fermer l’onglet du navigateur et revenir ultérieurement à l’affichage du rapport lorsque son contenu est disponible dans le cache.

## Disponibilité {#availability}

Il est possible de télécharger l’outil Cloud Readiness Analyzer dans un fichier zip à partir du portail de distribution de logiciels. Vous pouvez installer le module par le biais du gestionnaire de modules sur votre instance source Adobe Experience Manager (AEM).

>[!NOTE]
>Téléchargez Cloud Readiness Analyzer depuis le portail de [distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

## Affichage du rapport Cloud Readiness Analyzer au format {#viewing-report}

### Adobe Experience Manager 6.3.0 et versions ultérieures {#aem-later-versions}

Consultez cette section pour savoir comment afficher le rapport Cloud Readiness Analyzer :

1. Sélectionnez Adobe Experience Manager et accédez à Outils -> **Opérations** -> **Cloud Readiness Analyzer**.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-1.png)

1. Cliquez sur **Générer le rapport** pour exécuter Cloud Readiness Analyzer.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-tool-generate-report.png)

1. Pendant que l&#39;ARC génère le rapport, vous pouvez voir les progrès réalisés par l&#39;outil à l&#39;écran. Il affiche le nombre d&#39;éléments analysés et le nombre de résultats trouvés.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-tool-generate-report-1.png)


1. Une fois le rapport de l&#39;ARC généré, il affiche un résumé et le nombre de constatations sous forme de tableau, selon le type de conclusions et le niveau d&#39;importance. Pour obtenir plus de détails sur une recherche particulière, vous pouvez cliquer sur le numéro correspondant au type de recherche dans le tableau.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/report-cra-4.png)

   L&#39;action ci-dessus fera défiler automatiquement l&#39;écran jusqu&#39;à l&#39;emplacement de cette recherche dans le rapport.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/report-cra-5.png)

1. You have the option of downloading the report in a comma-separated values (CSV) format by clicking on **CSV**, as shown in the figure below.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/report-cra-6.png)

   >[!NOTE]
   >Vous pouvez forcer CRA à effacer son cache et à générer de nouveau le rapport en cliquant sur **Actualiser le rapport**.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/report-cra-7.png)

   >[!NOTE]
   >Le rapport est en cours de régénération, mais il affiche la progression en termes de pourcentage achevé, comme le montre l&#39;illustration ci-dessous.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-tool-refresh-1.png)


### Adobe Experience Manager 6.2 et 6.1 {#aem-specific-versions}

Dans l’outil Adobe Experience Manager 6.2, Cloud Readiness Analyzer est limité à un lien qui génère et télécharge le rapport CSV.

Pour Adobe Experience Manager 6.1, l’outil n’est pas fonctionnel et seule l’interface HTTP peut être utilisée.

>[!NOTE]
>Dans toutes les versions, le détecteur de motifs inclus peut s’exécuter de manière indépendante.

## Interprétation des rapports Cloud Readiness Analyzer {#cra-report}

Lorsque l’outil Cloud Readiness Analyzer est exécuté dans l’instance AEM, le rapport s’affiche sous la forme de résultats dans la fenêtre des outils.

Le format du rapport est le suivant :

* **Report Overview** : informations sur le rapport lui-même qui incluent les informations suivantes :
   * **Report Time** : heure à laquelle le contenu du rapport a été généré et rendu disponible pour la première fois.
   * **Expiration Time** : heure d’expiration du cache du contenu du rapport.
   * **Generation Time Period** : durée du processus de génération du contenu du rapport.
   * **Finding Count** : nombre total de résultats figurant dans le rapport.
* **System Overview** : informations sur le système AEM sur lequel CRA a été exécuté.
* **Finding Categories** : différentes sections traitant chacune d’un ou plusieurs résultats pour une même catégorie. Chaque section comprend les éléments suivants : nom de la catégorie, sous-types, nombre et importance des résultats, résumé, lien vers la documentation de la catégorie et informations relatives à chaque résultat.

Un niveau d’importance est attribué à chaque résultat pour indiquer une priorité absolue concernant l’action. Pour en savoir plus sur chaque Catégorie de recherche, reportez-vous à la section Catégories du détecteur de [schémas.](https://docs.adobe.com/content/help/en/experience-manager-pattern-detection/table-of-contents/aso.html)

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

Vous pouvez également utiliser un outil de ligne de commande tel que `curl` ou `wget`, mais aussi toute autre application cliente HTTP. Si vous n’utilisez pas un onglet de navigateur avec une session authentifiée, vous devez fournir un nom d’utilisateur et un mot de passe d’administration en commentaire.

À titre d’exemple, vous pouvez procéder comme suit :
`curl -u admin:admin 'http://localhost:4502/apps/readiness-analyzer/analysis/result.csv' > result.csv`.

### En-têtes et paramètres {#http-headers-and-parameters}

Les en-têtes HTTP suivants sont utilisés par cette interface :

* `Cache-Control: max-age=<seconds>`: Spécifie la durée de vie de fraîcheur du cache en secondes. (Voir [RFC 7234](https://tools.ietf.org/html/rfc7234#section-5.2.2.8).)
* `Prefer: respond-async`: Indique que le serveur doit répondre de manière asynchrone. (Voir [RFC 7240](https://tools.ietf.org/html/rfc7240#section-4.1).)
* `Prefer: return=minimal`: Indique que le serveur doit renvoyer une réponse minimale. (Voir [RFC 7240](https://tools.ietf.org/html/rfc7240#section-4.2).)

Les paramètres de requête HTTP suivants sont disponibles à titre de commodité lorsque l’utilisation des en-têtes HTTP risque de ne pas être facile :

* `max-age` (nombre, facultatif) : Spécifie la durée de vie de fraîcheur du cache en secondes. Ce nombre doit être égal ou supérieur à 0. La durée de vie de fraîcheur par défaut est de 8 6400 secondes. Sans ce paramètre ou l&#39;en-tête correspondant, un nouveau cache sera utilisé pour répondre aux demandes pendant 24 heures, et le cache devra alors être régénéré. L&#39;utilisation `max-age=0` forcera le cache à être effacé et déclenchera une régénération du rapport, en utilisant la durée de vie de fraîcheur non nulle précédente pour le cache nouvellement généré.
* `respond-async` (booléen, facultatif) : Indique que la réponse doit être fournie de manière asynchrone. Using `respond-async=true` when the cache is stale will cause the server to return a response of `202 Accepted` without waiting for the cache to be refreshed and for the report to be generated. Si le cache est actualisé, ce paramètre n’a aucun effet. The default value is `false`. Without this parameter or the corresponding header the server will respond synchronously, which may require a significant amount of time and require an adjustment to the maximum response time for the HTTP client.
* `may-refresh-cache` (booléen, facultatif) : Indique que le serveur peut actualiser le cache en réponse à une demande si le cache actuel est vide, obsolète ou bientôt obsolète. Si `may-refresh-cache=true`ou si elle n’est pas spécifiée, le serveur peut lancer une tâche d’arrière-plan qui appelle le Détecteur de schémas et actualise le cache. Si `may-refresh-cache=false` le serveur ne lance aucune tâche d&#39;actualisation qui aurait été effectuée autrement si le cache est vide ou obsolète, auquel cas le rapport est vide. Toute tâche d&#39;actualisation déjà en cours de traitement ne sera pas affectée par ce paramètre.
* `return-minimal` (booléen, facultatif) : Indique que la réponse du serveur doit uniquement inclure l’état contenant l’indication de progression et l’état du cache au format JSON. Si `return-minimal=true`vous le souhaitez, le corps de la réponse sera limité à l’objet status. Si `return-minimal=false`ou si elle n&#39;est pas spécifiée, une réponse complète sera fournie.
* `log-findings` (booléen, facultatif) : Indique que le serveur doit enregistrer le contenu du cache lors de sa création ou de son actualisation initiale. Chaque recherche du cache sera consignée sous la forme d’une chaîne JSON. Cette journalisation ne se produit que si `log-findings=true` la demande génère un nouveau cache.

Si un en-tête HTTP et son paramètre de requête correspondant sont présents simultanément, le paramètre de requête est prioritaire.

La commande suivante est une méthode simple pour lancer la génération du rapport via l’interface HTTP :
`curl -u admin:admin 'http://localhost:4502/apps/readiness-analyzer/analysis/result.json?max-age=0&respond-async=true'`.

Lorsqu’une requête a été effectuée, le client n’a pas besoin de rester actif pour que le rapport soit généré. La génération du rapport peut être lancée avec un client à l&#39;aide d&#39;une demande de GET HTTP et, une fois le rapport généré, affichée à partir du cache avec un autre client ou avec l&#39;outil ARC dans l&#39;interface utilisateur de l&#39;AEM.

### Réponses {#http-responses}

Les valeurs de réponses possibles sont les suivantes :

* `200 OK`: Indique que la réponse contient les résultats du détecteur de schémas qui ont été générés pendant la durée de vie de la mémoire cache.
* `202 Accepted`: Utilisé pour indiquer que le cache est obsolète. Lorsque `respond-async=true` et `may-refresh-cache=true` cette réponse indique qu’une tâche d’actualisation est en cours. Lorsque `may-refresh-cache=false` cette réponse indique simplement que le cache est obsolète.
* `400 Bad Request` : indique qu’une erreur s’est produite lors de la requête. Un message au format Détails du problème (voir [RFC 7807](https://tools.ietf.org/html/rfc7807)) donne des détails supplémentaires.
* `401 Unauthorized`: Indique que la demande n’a pas été autorisée.
* `500 Internal Server Error` : indique qu’une erreur de serveur interne s’est produite. Un message au format Détails du problème donne des détails supplémentaires.
* `503 Service Unavailable` : indique que le serveur est occupé par une autre réponse et qu’il ne peut pas traiter cette requête dans les délais impartis. Cela ne se produit probablement que pour les requêtes synchrones. Un message au format Détails du problème donne des détails supplémentaires.

## Informations sur l’administrateur

### Ajustement de la durée de vie du cache {#cache-adjustment}

La durée de vie par défaut du cache CRA est de 24 heures. Avec l’option destinée à actualiser un rapport et à régénérer le cache, aussi bien dans l’instance AEM que dans l’interface HTTP, cette valeur par défaut sera probablement appropriée pour la plupart des utilisations du CRA. Si le temps de génération du rapport est particulièrement long pour votre instance AEM, vous pouvez ajuster la durée de vie du cache afin de minimiser la nouvelle génération d’un rapport.

La durée de vie du cache est stockée dans la propriété `maxCacheAge` dans le nœud de référentiel suivant :
`/apps/readiness-analyzer/content/CloudReadinessReport/jcr:content`

La valeur de cette propriété est la durée de vie du cache en secondes. Un administrateur peut ajuster la durée de vie du cache à l’aide de CRX/DE Lite.

### Installation sur AEM 6.1 {#installing-on-aem61}

CRA utilise un compte d’utilisateur de service système nommé `repository-reader-service` pour exécuter le détecteur de motifs. Ce compte est disponible dans AEM 6.2 et versions ultérieures. Dans AEM 6.1, ce compte doit être créé *avant* l’installation de CRA en procédant comme suit :

1. Suivez les instructions de la section [Création d’un utilisateur de service](https://docs.adobe.com/content/help/fr-FR/experience-manager-65/administering/security/security-service-users.html#creating-a-new-service-user) pour créer un utilisateur. Définissez l’ID utilisateur sur `repository-reader-service` et laissez le champ Chemin intermédiaire vide, puis cliquez sur la coche verte.

2. Suivez les instructions de la section [Gestion des utilisateurs et des groupes](https://docs.adobe.com/content/help/fr-FR/experience-manager-65/administering/security/security.html#managing-users-and-groups), en particulier les instructions d’ajout d’utilisateurs à un groupe afin d’ajouter l’utilisateur `repository-reader-service` au groupe `administrators`.

3. Installez le package CRA via Package Manager sur votre instance AEM source. (Cela a pour effet d’ajouter la modification de configuration nécessaire à la configuration ServiceUserMapper pour l’utilisateur du service système `repository-reader-service`.)
