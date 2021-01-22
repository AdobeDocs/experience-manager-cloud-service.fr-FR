---
title: Utilisation de l’analyseur des meilleures pratiques
description: Utilisation de l’analyseur des meilleures pratiques
translation-type: tm+mt
source-git-commit: dc2d529c6bbdb4e0fd963021e40bc333b321c95c
workflow-type: tm+mt
source-wordcount: '2362'
ht-degree: 69%

---


# Utilisation de l’analyseur des meilleures pratiques {#using-best-practices-analyzer}

>[!CONTEXTUALHELP]
>id="aemcloud_bpa_using"
>title="Utilisation de l’analyseur des meilleures pratiques"
>abstract="Consultez la documentation relative à l’utilisation de Best Practices Analyzer (anciennement Cloud Readiness Analyzer) et du rapport généré. Le rapport Best Practices Analyzer permet de mieux comprendre l’état de préparation à la mise à niveau générale."
>additional-url=""

## Considérations importantes concernant l’utilisation de l’analyseur des meilleures pratiques {#imp-considerations}

Suivez la section ci-dessous pour comprendre les points importants à prendre en compte pour l’exécution de l’analyseur des meilleures pratiques (BPA) :

* Le rapport BPA est créé à l’aide de la sortie de Adobe Experience Manager (AEM) [Détecteur de schémas](https://docs.adobe.com/content/help/fr-FR/experience-manager-65/deploying/upgrading/pattern-detector.html). La version du Détecteur de schémas utilisée par BPA est incluse dans le package d’installation de BPA.

* Le BPA ne peut être exécuté que par l&#39;utilisateur **admin** ou un utilisateur du groupe **administrateurs**.

* Le BPA est pris en charge sur les instances AEM avec les versions 6.1 et ultérieures.

   >[!NOTE]
Veuillez consulter  [Installation sur AEM 6.1](#installing-on-aem61) pour connaître les conditions particulières d&#39;installation de BPA sur AEM 6.1.

* BPA peut s’exécuter sur n’importe quel environnement, mais il est préférable de l’exécuter sur un environnement *Stage*.

   >[!NOTE]
Afin d’éviter tout impact sur les instances critiques de l’entreprise, il est recommandé d’exécuter BPA sur un environnement  ** Autorisation le plus proche possible de l’environnement  ** Productionenvironment dans les domaines des personnalisations, des configurations, du contenu et des applications utilisateur. Vous pouvez également l’exécuter sur un clone de l’environnement de *création* de production.

* La génération du contenu du rapport BPA peut prendre un temps considérable, de plusieurs minutes à quelques heures. La durée nécessaire dépend largement de la taille et de la nature du contenu du référentiel AEM, de la version d’AEM et d’autres facteurs.

* En raison du temps éventuellement nécessaire pour générer le contenu du rapport, celui-ci est créé par un processus en arrière-plan et conservé dans un cache. L’affichage et le téléchargement du rapport doivent être relativement rapides, car il utilise le cache de contenu jusqu’à son expiration ou s’il est explicitement actualisé. Pendant la génération du contenu du rapport, vous pouvez fermer l’onglet du navigateur et revenir ultérieurement à l’affichage du rapport lorsque son contenu est disponible dans le cache.

## Disponibilité {#availability}

[!CONTEXTUALHELP]
id="aemcloud_bpa_download"
title="Téléchargement de l’analyseur des meilleures pratiques"
abstract="L&#39;analyseur des meilleures pratiques peut être téléchargé sous la forme d&#39;un fichier zip à partir du portail de distribution de logiciels. Vous pouvez installer le module par le biais du gestionnaire de modules sur votre instance source Adobe Experience Manager (AEM)."

L&#39;analyseur des meilleures pratiques peut être téléchargé sous la forme d&#39;un fichier zip à partir du portail de distribution de logiciels. Vous pouvez installer le module par le biais du gestionnaire de modules sur votre instance source Adobe Experience Manager (AEM).

>[!NOTE]
Téléchargez Best Practices Analyzer sur le  [portail ](https://experience.adobe.com/#/downloads/content/software-distribution/fr-FR/aemcloud.html) de distribution de logiciels.

## Affichage du rapport Analyseur des meilleures pratiques {#viewing-report}

### Adobe Experience Manager 6.3.0 et versions ultérieures {#aem-later-versions}

Suivez cette section pour savoir comment vue du rapport Best Practices Analyzer :

1. Sélectionnez Adobe Experience Manager et accédez aux outils -> **Opérations** -> **Analyseur des meilleures pratiques**.

   ![image](/help/move-to-cloud-service/best-practices-analyzer/assets/BPA_pic1.png)

1. Cliquez sur **Générer le rapport** pour exécuter l’analyseur des meilleures pratiques.

   ![image](/help/move-to-cloud-service/best-practices-analyzer/assets/BPA_pic2.png)

1. Pendant que l&#39;APM génère le rapport, vous pouvez voir la progression de l&#39;outil à l&#39;écran. Il affiche le nombre d’éléments analysés et le nombre de résultats trouvés.

   ![image](/help/move-to-cloud-service/best-practices-analyzer/assets/BPA_pic3.png)


1. Une fois le rapport d&#39;APB généré, il affiche un résumé et le nombre de résultats sous forme de tableau, organisés en fonction du type de recherche et du niveau d&#39;importance. Pour obtenir plus de détails sur un résultat spécifique, vous pouvez cliquer sur le numéro correspondant au type de résultat dans le tableau.

   ![image](/help/move-to-cloud-service/best-practices-analyzer/assets/BPA_pic4.png)

   L’action ci-dessus fait automatiquement défiler l’écran jusqu’à l’emplacement de ce résultat dans le rapport.

   ![image](/help/move-to-cloud-service/best-practices-analyzer/assets/BPA_pic5.png)

1. Vous avez la possibilité de télécharger le rapport au format CSV (valeurs séparées par une virgule) en cliquant sur **CSV**, comme le montre la figure ci-dessous.

   ![image](/help/move-to-cloud-service/best-practices-analyzer/assets/BPA_pic6.png)

   >[!NOTE]
Vous pouvez forcer l’application d’une seule page à effacer son cache et à régénérer le rapport en cliquant sur  **Actualiser le rapport**.

   ![image](/help/move-to-cloud-service/best-practices-analyzer/assets/BPA_pic7.png)

   >[!NOTE]
Pendant sa régénération, le rapport affiche la progression en termes de pourcentage achevé, comme le montre l’illustration ci-dessous.

   ![image](/help/move-to-cloud-service/best-practices-analyzer/assets/BPA_pic8.png)


### Adobe Experience Manager 6.2 et 6.1 {#aem-specific-versions}

L’outil Best Practices Analyzer est limité dans Adobe Experience Manager 6.2 à un lien qui génère et télécharge le rapport CSV.

Pour Adobe Experience Manager 6.1, l’outil n’est pas fonctionnel et seule l’interface HTTP peut être utilisée.

>[!NOTE]
Dans toutes les versions, le détecteur de motifs inclus peut s’exécuter de manière indépendante.

## Interprétation du rapport Analyseur des meilleures pratiques {#cra-report}

[!CONTEXTUALHELP]
id="aemcloud_bpa_interpreting"
title="Interprétation du rapport Analyseur des meilleures pratiques"
abstract="Il existe deux options pour afficher les sorties de rapport BPA : IU et CSV. Lorsque l’outil Best Practices Analyzer est exécuté dans l’instance AEM, le rapport IU s’affiche sous forme de résultats dans la fenêtre d’outils. Le format CSV du rapport contient des informations générées à partir de la sortie du détecteur de motifs, triées et organisées par types de catégories, sous-types et niveaux d’importance."
additional-url="https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html?lang=en" text="Présentation des catégories de rapports de l’analyseur des meilleures pratiques"

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
Pour en savoir plus sur chaque catégorie de résultat, consultez [Catégories du détecteur de motifs](https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html).

Consultez le tableau ci-dessous pour comprendre les niveaux d’importance :

| Importance | Description |
|--- |--- |
| INFO | Ce résultat est fourni à titre d’information. |
| ADVISORY | Ce résultat peut poser un problème de mise à niveau. Il est recommandé d’approfondir les investigations. |
| MAJOR | Il est probable que ce résultat constitue un problème de mise à niveau qui doit être résolu. |
| CRITICAL | Il est très probable que ce résultat constitue un problème de mise à niveau qui doit être résolu pour éviter toute perte de fonction ou de performances. |


## Interprétation du rapport CSV de l’analyseur des meilleures pratiques {#cra-csv-report}

Lorsque vous cliquez sur l’option **CSV** de votre instance d’AEM, le format CSV du rapport Best Practices Analyzer est créé à partir du cache de contenu et renvoyé à votre navigateur. En fonction des paramètres du navigateur, ce rapport sera automatiquement téléchargé sous la forme d’un fichier portant le nom `results.csv` par défaut.

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

Les URL suivantes sont disponibles pour l’accès HTTP, où `<host>` correspond au nom d’hôte et au port, si nécessaire, du serveur sur lequel le BPA est installé :
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

* `Cache-Control: max-age=<seconds>` : indique l’intervalle d’actualisation du cache en secondes. (Voir [RFC 7234](https://tools.ietf.org/html/rfc7234#section-5.2.2.8).)
* `Prefer: respond-async` : indique que le serveur doit répondre de manière asynchrone. (Voir [RFC 7240](https://tools.ietf.org/html/rfc7240#section-4.1).)
* `Prefer: return=minimal` : indique que le serveur doit renvoyer une réponse minimale. (Voir [RFC 7240](https://tools.ietf.org/html/rfc7240#section-4.2).)

Les paramètres de requête HTTP suivants sont disponibles à titre de commodité lorsque l’utilisation des en-têtes HTTP risque de ne pas être facile :

* `max-age` (nombre, facultatif) : indique l’intervalle d’actualisation du cache en secondes. Ce nombre doit être égal ou supérieur à 0. L’intervalle d’actualisation par défaut est de 86 400 secondes. Sans ce paramètre ou l’en-tête correspondant, un nouveau cache est utilisé pour répondre aux requêtes pendant 24 heures, auquel stade le cache doit être régénéré. L’utilisation de `max-age=0` force l’effacement du cache et déclenche une régénération du rapport, en utilisant l’intervalle d’actualisation non nul précédent du cache nouvellement généré.
* `respond-async` (booléen, facultatif) : indique que la réponse doit être fournie de manière asynchrone. L’utilisation de `respond-async=true`, si le cache est obsolète, entraîne l’envoi par le serveur d’une réponse `202 Accepted` sans attendre que le cache soit actualisé et le rapport généré. Si le cache est actualisé, ce paramètre n’a aucun effet. La valeur par défaut est `false`. Sans ce paramètre ou l’en-tête correspondant, le serveur répondra de manière synchrone. Dans ce cas, la réponse peut nécessiter un temps important et un ajustement du temps de réponse maximal pour le client HTTP.
* `may-refresh-cache` (booléen, facultatif) : indique que le serveur peut actualiser le cache en réponse à une demande si le cache actuel est vide, obsolète ou sur le point d’être obsolète. Si `may-refresh-cache=true`, ou s’il n’est pas spécifié, le serveur peut lancer une tâche en arrière-plan qui appelle le détecteur de motifs et actualise le cache. Si `may-refresh-cache=false`, le serveur ne lance aucune tâche d’actualisation qui aurait sinon été effectuée si le cache est vide ou obsolète, auquel cas le rapport est vide. Une tâche d’actualisation déjà en cours de traitement n’est pas affectée par ce paramètre.
* `return-minimal` (booléen, facultatif) : indique que la réponse du serveur doit uniquement inclure le statut contenant l’indication de progression et le statut du cache au format JSON. Si `return-minimal=true`, le corps de la réponse est limité à l’objet de statut. Si `return-minimal=false`, ou s’il n’est pas spécifié, une réponse complète est fournie.
* `log-findings` (booléen, facultatif) : indique que le serveur doit consigner le contenu du cache lors de sa création ou de son actualisation initiale. Chaque résultat du cache est consigné sous la forme d’une chaîne JSON. Cette consignation ne se produit que si `log-findings=true` et la requête génèrent un nouveau cache.

Si un en-tête HTTP et son paramètre de requête correspondant sont présents simultanément, le paramètre de requête est prioritaire.

La commande suivante est une méthode simple pour lancer la génération du rapport via l’interface HTTP :
`curl -u admin:admin 'http://localhost:4502/apps/best-practices-analyzer/analysis/report.json?max-age=0&respond-async=true'`.

Lorsqu’une requête a été effectuée, le client n’a pas besoin de rester actif pour que le rapport soit généré. La génération du rapport peut être lancée avec un client à l’aide d’une demande de GET HTTP et, une fois le rapport généré, affichée à partir du cache avec un autre client ou avec l’outil BPA dans l’interface utilisateur AEM.

### Réponses {#http-responses}

Les valeurs de réponses possibles sont les suivantes :

* `200 OK` : indique que la réponse contient les résultats du détecteur de motifs, générés pendant l’intervalle d’actualisation de la mémoire cache.
* `202 Accepted` : utilisé pour indiquer que le cache est obsolète. Si `respond-async=true` et `may-refresh-cache=true`, cette réponse indique qu’une tâche d’actualisation est en cours. Si `may-refresh-cache=false`, cette réponse indique simplement que le cache est obsolète.
* `400 Bad Request` : indique qu’une erreur s’est produite lors de la requête. Un message au format Détails du problème (voir [RFC 7807](https://tools.ietf.org/html/rfc7807)) donne des détails supplémentaires.
* `401 Unauthorized` : indique que la requête n’a pas été autorisée.
* `500 Internal Server Error` : indique qu’une erreur de serveur interne s’est produite. Un message au format Détails du problème donne des détails supplémentaires.
* `503 Service Unavailable` : indique que le serveur est occupé par une autre réponse et qu’il ne peut pas traiter cette requête dans les délais impartis. Cela ne se produit probablement que pour les requêtes synchrones. Un message au format Détails du problème donne des détails supplémentaires.

## Informations sur l’administrateur

### Ajustement de la durée de vie du cache {#cache-adjustment}

La durée de vie du cache BPA par défaut est de 24 heures. Avec l&#39;option d&#39;actualisation d&#39;un rapport et de régénération du cache, dans l&#39;instance AEM et l&#39;interface HTTP, cette valeur par défaut est susceptible d&#39;être appropriée pour la plupart des utilisations du BPA. Si le temps de génération du rapport est particulièrement long pour votre instance AEM, vous pouvez ajuster la durée de vie du cache afin de minimiser la nouvelle génération d’un rapport.

La durée de vie du cache est stockée dans la propriété `maxCacheAge` dans le nœud de référentiel suivant :
`/apps/best-practices-analyzer/content/BestPracticesReport/jcr:content`

La valeur de cette propriété est la durée de vie du cache en secondes. Un administrateur peut ajuster la durée de vie du cache à l’aide de CRX/DE Lite.

### Installation sur AEM 6.1 {#installing-on-aem61}

BPA utilise un compte utilisateur de service système nommé `repository-reader-service` pour exécuter le Détecteur de schémas. Ce compte est disponible dans AEM 6.2 et versions ultérieures. À l&#39;AEM 6.1, ce compte doit être créé *avant* l&#39;installation de BPA en procédant comme suit :

1. Suivez les instructions de la section [Création d’un utilisateur de service](https://docs.adobe.com/content/help/fr-FR/experience-manager-65/administering/security/security-service-users.html#creating-a-new-service-user) pour créer un utilisateur. Définissez l’ID utilisateur sur `repository-reader-service` et laissez le champ Chemin intermédiaire vide, puis cliquez sur la coche verte.

2. Suivez les instructions de la section [Gestion des utilisateurs et des groupes](https://docs.adobe.com/content/help/fr-FR/experience-manager-65/administering/security/security.html#managing-users-and-groups), en particulier les instructions d’ajout d’utilisateurs à un groupe afin d’ajouter l’utilisateur `repository-reader-service` au groupe `administrators`.

3. Installez le package BPA via Package Manager sur votre instance d’AEM source. (Cela a pour effet d’ajouter la modification de configuration nécessaire à la configuration ServiceUserMapper pour l’utilisateur du service système `repository-reader-service`.)
