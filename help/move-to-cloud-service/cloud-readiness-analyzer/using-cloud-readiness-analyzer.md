---
title: Utilisation de l’analyseur des meilleures pratiques
description: Utilisation de l’analyseur des meilleures pratiques
translation-type: tm+mt
source-git-commit: ca6ee9c820c67b68c7498f2b0bad8c650b00562e
workflow-type: tm+mt
source-wordcount: '2207'
ht-degree: 48%

---


# Utilisation de l’analyseur des meilleures pratiques {#using-best-practices-analyzer}

## Considérations importantes pour l’utilisation de l’analyseur des meilleures pratiques {#imp-considerations}

Suivez la section ci-dessous pour comprendre les points importants à prendre en compte pour l’exécution de l’analyseur des meilleures pratiques (BPA) :

* The BPA report is built using the output of the Adobe Experience Manager (AEM) [Pattern Detector](https://docs.adobe.com/content/help/fr-FR/experience-manager-65/deploying/upgrading/pattern-detector.html). La version du Détecteur de schémas utilisée par BPA est incluse dans le package d’installation de BPA.

* BPA may only be run by the **admin** user or a user in the **administrators** group.

* Le BPA est pris en charge sur les instances AEM avec les versions 6.1 et ultérieures.

   >[!NOTE]
   > Please see [Installing on AEM 6.1](#installing-on-aem61) for special requirements for installing BPA on AEM 6.1.

* BPA can run on any environment, but it is preferred to have it run on a *Stage* environment.

   >[!NOTE]
   >In order to avoid an impact on business critical instances, it is recommended that you run BPA on an *Author* environment that is as close as possible to the *Production* environment in the areas of customizations, configurations, content and user applications. Vous pouvez également l’exécuter sur un clone de l’environnement de *création* de production.

* La génération du contenu du rapport BPA peut prendre un temps considérable, de plusieurs minutes à quelques heures. La durée nécessaire dépend largement de la taille et de la nature du contenu du référentiel AEM, de la version d’AEM et d’autres facteurs.

* En raison du temps éventuellement nécessaire pour générer le contenu du rapport, celui-ci est créé par un processus en arrière-plan et conservé dans un cache. L’affichage et le téléchargement du rapport doivent être relativement rapides, car il utilise le cache de contenu jusqu’à son expiration ou s’il est explicitement actualisé. Pendant la génération du contenu du rapport, vous pouvez fermer l’onglet du navigateur et revenir ultérieurement à l’affichage du rapport lorsque son contenu est disponible dans le cache.

## Disponibilité {#availability}

L&#39;analyseur des meilleures pratiques peut être téléchargé sous la forme d&#39;un fichier zip à partir du portail de distribution de logiciels. Vous pouvez installer le module par le biais du gestionnaire de modules sur votre instance source Adobe Experience Manager (AEM).

>[!NOTE]
>Download the Best Practices Analyzer from the [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) portal.

## Affichage du rapport Analyseur des meilleures pratiques {#viewing-report}

### Adobe Experience Manager 6.3.0 et versions ultérieures {#aem-later-versions}

Suivez cette section pour savoir comment vue du rapport Best Practices Analyzer :

1. Select Adobe Experience Manager and navigate to tools -> **Operations** -> **Best Practices Analyzer**.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/BPA_pic1.png)

1. Cliquez sur **Générer le rapport** pour exécuter l’analyseur des meilleures pratiques.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/BPA_pic2.png)

1. Pendant que l&#39;APM génère le rapport, vous pouvez voir la progression de l&#39;outil à l&#39;écran. Il affiche le nombre d&#39;éléments analysés et le nombre de résultats trouvés.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/BPA_pic3.png)


1. Une fois le rapport d&#39;APB généré, il affiche un résumé et le nombre de résultats sous forme de tableau, organisés en fonction du type de recherche et du niveau d&#39;importance. Pour obtenir plus de détails sur une recherche particulière, vous pouvez cliquer sur le numéro correspondant au type de recherche dans le tableau.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/BPA_pic4.png)

   L&#39;action ci-dessus fera défiler automatiquement l&#39;écran jusqu&#39;à l&#39;emplacement de cette recherche dans le rapport.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/BPA_pic5.png)

1. You have the option of downloading the report in a comma-separated values (CSV) format by clicking on **CSV**, as shown in the figure below.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/BPA_pic6.png)

   >[!NOTE]
   >You may force the BPA to clear its cache and regenerate the report by clicking **Refresh Report**.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/BPA_pic7.png)

   >[!NOTE]
   >Le rapport est en cours de régénération, mais il affiche la progression en termes de pourcentage achevé, comme le montre l&#39;illustration ci-dessous.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/BPA_pic8.png)


### Adobe Experience Manager 6.2 et 6.1 {#aem-specific-versions}

L’outil Best Practices Analyzer est limité dans Adobe Experience Manager 6.2 à un lien qui génère et télécharge le rapport CSV.

Pour Adobe Experience Manager 6.1, l’outil n’est pas fonctionnel et seule l’interface HTTP peut être utilisée.

>[!NOTE]
>Dans toutes les versions, le détecteur de motifs inclus peut s’exécuter de manière indépendante.

## Interprétation du rapport Analyseur des meilleures pratiques {#cra-report}

Lorsque l&#39;outil Best Practices Analyzer est exécuté dans l&#39;instance AEM, le rapport s&#39;affiche sous forme de résultats dans la fenêtre d&#39;outils.

Le format du rapport est le suivant :

* **Report Overview** : informations sur le rapport lui-même qui incluent les informations suivantes :
   * **Report Time** : heure à laquelle le contenu du rapport a été généré et rendu disponible pour la première fois.
   * **Expiration Time** : heure d’expiration du cache du contenu du rapport.
   * **Generation Time Period** : durée du processus de génération du contenu du rapport.
   * **Finding Count** : nombre total de résultats figurant dans le rapport.
* **Présentation** du système : Informations sur le système AEM sur lequel le BPA a été exécuté.
* **Finding Categories** : différentes sections traitant chacune d’un ou plusieurs résultats pour une même catégorie. Chaque section comprend les éléments suivants : nom de la catégorie, sous-types, nombre et importance des résultats, résumé, lien vers la documentation de la catégorie et informations relatives à chaque résultat.

Un niveau d’importance est attribué à chaque résultat pour indiquer une priorité absolue concernant l’action.

>[!NOTE]
>Pour en savoir plus sur chaque Catégorie de recherche, consultez Catégories [du Détecteur de](https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html)schémas.

Consultez le tableau ci-dessous pour comprendre les niveaux d’importance :

| Importance | Description |
|--- |--- |
| INFO | Ce résultat est fourni à titre d’information. |
| ADVISORY | Ce résultat peut poser un problème de mise à niveau. Il est recommandé d’approfondir les investigations. |
| MAJOR | Il est probable que ce résultat constitue un problème de mise à niveau qui doit être résolu. |
| CRITICAL | Il est très probable que ce résultat constitue un problème de mise à niveau qui doit être résolu pour éviter toute perte de fonction ou de performances. |


## Interprétation du rapport CSV de l’analyseur des meilleures pratiques {#cra-csv-report}

When you click the **CSV** option from your AEM instance, the CSV format of the Best Practices Analyzer report is built from the content cache and returned to your browser. En fonction des paramètres du navigateur, ce rapport sera automatiquement téléchargé sous la forme d’un fichier portant le nom `results.csv` par défaut.

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

Le BPA fournit une interface HTTP qui peut être utilisée comme alternative à son interface utilisateur dans AEM. L’interface prend en charge les commandes HEAD et GET. Il peut être utilisé pour générer le rapport BPA et le renvoyer dans l’un des trois formats suivants : JSON, CSV et valeurs séparées par des tabulations (TSV).

The following URLs are available for HTTP access, where `<host>` is the hostname, and port if necessary, of the server on which the BPA is installed:
* `http://<host>/apps/best-practices-analyzer/analysis/report.json` pour le format JSON
* `http://<host>/apps/best-practices-analyzer/analysis/report.csv` pour le format CSV
* `http://<host>/apps/best-practices-analyzer/analysis/report.tsv` pour le format TSV

### Exécution d’une requête HTTP {#executing-http-request}

Il est possible d’utiliser l’interface HTTP de différentes manières.

Une méthode simple consiste à ouvrir un onglet dans le même navigateur que celui utilisé pour vous connecter à AEM en tant qu’administrateur. Vous pouvez renseigner l’URL dans l’onglet du navigateur et afficher ou télécharger les résultats grâce au navigateur.

Vous pouvez également utiliser un outil de ligne de commande tel que `curl` ou `wget`, mais aussi toute autre application cliente HTTP. Si vous n’utilisez pas un onglet de navigateur avec une session authentifiée, vous devez fournir un nom d’utilisateur et un mot de passe d’administration en commentaire.

À titre d’exemple, vous pouvez procéder comme suit :
`curl -u admin:admin 'http://localhost:4502/apps/best-practices-analyzer/analysis/report.csv' > report.csv`.

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
`curl -u admin:admin 'http://localhost:4502/apps/best-practices-analyzer/analysis/report.json?max-age=0&respond-async=true'`.

Lorsqu’une requête a été effectuée, le client n’a pas besoin de rester actif pour que le rapport soit généré. La génération du rapport peut être lancée avec un client à l’aide d’une demande de GET HTTP et, une fois le rapport généré, affichée à partir du cache avec un autre client ou avec l’outil BPA dans l’interface utilisateur AEM.

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

La durée de vie du cache BPA par défaut est de 24 heures. Avec l&#39;option d&#39;actualisation d&#39;un rapport et de régénération du cache, dans l&#39;instance AEM et l&#39;interface HTTP, cette valeur par défaut est susceptible d&#39;être appropriée pour la plupart des utilisations du BPA. Si le temps de génération du rapport est particulièrement long pour votre instance AEM, vous pouvez ajuster la durée de vie du cache afin de minimiser la nouvelle génération d’un rapport.

La durée de vie du cache est stockée dans la propriété `maxCacheAge` dans le nœud de référentiel suivant :
`/apps/best-practices-analyzer/content/BestPracticesReport/jcr:content`

La valeur de cette propriété est la durée de vie du cache en secondes. Un administrateur peut ajuster la durée de vie du cache à l’aide de CRX/DE Lite.

### Installation sur AEM 6.1 {#installing-on-aem61}

BPA utilizes a system service user account named `repository-reader-service` to execute the Pattern Detector. Ce compte est disponible dans AEM 6.2 et versions ultérieures. On AEM 6.1, this account must be created *prior to* installation of BPA by taking the following steps:

1. Suivez les instructions de la section [Création d’un utilisateur de service](https://docs.adobe.com/content/help/fr-FR/experience-manager-65/administering/security/security-service-users.html#creating-a-new-service-user) pour créer un utilisateur. Définissez l’ID utilisateur sur `repository-reader-service` et laissez le champ Chemin intermédiaire vide, puis cliquez sur la coche verte.

2. Suivez les instructions de la section [Gestion des utilisateurs et des groupes](https://docs.adobe.com/content/help/fr-FR/experience-manager-65/administering/security/security.html#managing-users-and-groups), en particulier les instructions d’ajout d’utilisateurs à un groupe afin d’ajouter l’utilisateur `repository-reader-service` au groupe `administrators`.

3. Installez le package BPA via Package Manager sur votre instance d’AEM source. (Cela a pour effet d’ajouter la modification de configuration nécessaire à la configuration ServiceUserMapper pour l’utilisateur du service système `repository-reader-service`.)
