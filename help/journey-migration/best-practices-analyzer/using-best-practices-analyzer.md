---
title: Utilisation de l’analyseur des bonnes pratiques
description: Utilisation de l’analyseur des bonnes pratiques
source-git-commit: a6d225943c5d23ebd960fda0b0912a81f1f80014
workflow-type: tm+mt
source-wordcount: '2470'
ht-degree: 99%

---

# Utilisation de l’analyseur des bonnes pratiques {#using-best-practices-analyzer}

>[!CONTEXTUALHELP]
>id="aemcloud_bpa_using"
>title="Utilisation de l’analyseur des bonnes pratiques"
>abstract="Consultez la documentation relative à l’utilisation de l’analyseur des bonnes pratiques (anciennement Cloud Readiness Analyzer) et du rapport généré. Le rapport de l’analyseur des bonnes pratiques permet de mieux comprendre le degré de préparation général à la mise à niveau."
>additional-url=""

## Considérations importantes concernant l’utilisation de l’analyseur des bonnes pratiques {#imp-considerations}

Consultez la section ci-dessous afin de comprendre les points importants à prendre en compte pour utiliser l’analyseur des bonnes pratiques (BPA, Best Practices Analyzer) :

* Les rapports BPA sont générés à l’aide des résultats obtenus par le [détecteur de motifs](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/pattern-detector.html?lang=fr) d’Adobe Experience Manager (AEM). La version du détecteur de motifs utilisée par BPA se trouve dans le module d’installation BPA.

* L’outil BPA ne peut être exécuté que par un utilisateur **admin** ou un utilisateur figurant dans le groupe **administrateurs**.

* L’outil BPA est pris en charge sur les instances AEM avec la version 6.1 et versions ultérieures.

   >[!NOTE]
Consultez [Installation sur AEM 6.1](#installing-on-aem61) pour connaître les conditions particulières d’installation de BPA sur AEM 6.1.

* Il peut s’exécuter dans n’importe quel environnement, mais il est préférable de l’exécuter dans un environnement d’*évaluation*.

   >[!NOTE]
Pour éviter toute incidence sur les instances critiques de l’entreprise, il est recommandé d’exécuter BPA dans un environnement de *création* aussi proche que possible de l’environnement de *production* concernant la personnalisation, la configuration, les contenus et les applications utilisateur. Vous pouvez également l’exécuter sur un clone de l’environnement de *création* de production.

* La génération du contenu des rapports BPA peut nécessiter un temps important, de plusieurs minutes à quelques heures. La durée nécessaire dépend largement de la taille et de la nature du contenu du référentiel AEM, de la version d’AEM et d’autres facteurs.

* En raison du temps éventuellement nécessaire pour générer le contenu du rapport, celui-ci est créé par un processus en arrière-plan et conservé dans un cache. L’affichage et le téléchargement du rapport doivent être relativement rapides, car il utilise le cache de contenu jusqu’à son expiration ou s’il est explicitement actualisé. Pendant la génération du contenu du rapport, vous pouvez fermer l’onglet du navigateur et revenir ultérieurement à l’affichage du rapport lorsque son contenu est disponible dans le cache.

## Disponibilité {#availability}

[!CONTEXTUALHELP]
id="aemcloud_bpa_download"
title="Téléchargement de l’analyseur des bonnes pratiques"
abstract="Il est possible de télécharger l’analyseur des bonnes pratiques dans un fichier zip à partir du portail de distribution de logiciels. Vous pouvez installer le module par le biais du gestionnaire de modules sur votre instance source Adobe Experience Manager (AEM)."

Il est possible de télécharger l’analyseur des bonnes pratiques dans un fichier zip à partir du portail de distribution de logiciels. Vous pouvez installer le package via [Gestionnaire de modules](/help/implementing/developing/tools/package-manager.md) sur votre instance source Adobe Experience Manager (AEM).

>[!NOTE]
Téléchargez l’analyseur des bonnes pratiques depuis le portail de [distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

## Affichage du rapport de l’analyseur des bonnes pratiques {#viewing-report}

### Adobe Experience Manager 6.3.0 et versions ultérieures {#aem-later-versions}

Consultez cette section pour savoir comment afficher le rapport de l’analyseur des bonnes pratiques :

1. Sélectionnez Adobe Experience Manager et accédez à Outils > **Opérations** > **Best Practices Analyzer**.

   ![image](/help/journey-migration/best-practices-analyzer/assets/BPA_pic1.png)

1. Cliquez sur **Generate Report** (Générer le rapport) pour exécuter l’analyseur des bonnes pratiques.

   ![image](/help/journey-migration/best-practices-analyzer/assets/BPA_pic2.png)

1. Pendant que BPA génère le rapport, vous pouvez afficher l’avancée de l’outil à l’écran. Il affiche le nombre d’éléments analysés et le nombre de résultats trouvés.

   ![image](/help/journey-migration/best-practices-analyzer/assets/BPA_pic3.png)


1. Une fois son rapport généré, l’analyseur des bonnes pratiques affiche un résumé et le nombre de résultats sous forme de tableau organisé selon le type de résultat et le niveau d’importance. Pour obtenir plus de détails sur un résultat spécifique, vous pouvez cliquer sur le numéro correspondant au type de résultat dans le tableau.

   ![image](/help/journey-migration/best-practices-analyzer/assets/BPA_pic4.png)

   L’action ci-dessus fait automatiquement défiler l’écran jusqu’à l’emplacement de ce résultat dans le rapport.

   ![image](/help/journey-migration/best-practices-analyzer/assets/BPA_pic5.png)

1. Vous avez la possibilité de télécharger le rapport au format CSV (valeurs séparées par une virgule) en cliquant sur **Exporter au format CSV**, comme le montre l’illustration ci-dessous.

   ![image](/help/journey-migration/best-practices-analyzer/assets/BPA_pic6.png)

   >[!NOTE]
Vous pouvez forcer l’analyseur des bonnes pratiques à effacer son cache et à générer de nouveau le rapport en cliquant sur **Refresh Report** (Actualiser le rapport).

   ![image](/help/journey-migration/best-practices-analyzer/assets/BPA_pic7.png)

   >[!NOTE]
Pendant sa régénération, le rapport affiche la progression en termes de pourcentage achevé, comme le montre l’illustration ci-dessous.

   ![image](/help/journey-migration/best-practices-analyzer/assets/BPA_pic8.png)



#### Utilisation de filtres dans le rapport Analyseur des bonnes pratiques (BPA)  {#bpa-filters}

Pour filtrer les résultats liés à [ACS Commons](https://adobe-consulting-services.github.io/acs-aem-commons/), procédez comme suit :

1. Cliquez sur l’icône du rail de gauche sur le côté gauche de la page. Cela affichera le **filtre ACS Commons**. Cliquez sur le **filtre ACS Commons** pour afficher la case à cocher interactive comme illustré dans l’image ci-dessous.

   ![image](/help/journey-migration/best-practices-analyzer/assets/report_filter_1.png)

   >[!NOTE]
L’icône du rail de gauche n’apparaîtra que si le BPA détecte l’utilisation d’ACS Commons.

1. Désélectionnez la case pour filtrer tous les résultats liés à ACS Commons. Un **nombre de résultats filtrés** devrait s’afficher sur le rapport, comme illustré dans l’image ci-dessous. Le filtre est également appliqué au rapport lorsqu’il est exporté au format CSV (valeurs séparées par des virgules).

   ![image](/help/journey-migration/best-practices-analyzer/assets/report_filter_2.png)

   >[!NOTE]
Les résultats d’ACS Commons ne doivent pas être ignorés. Consultez la [documentation](https://adobe-consulting-services.github.io/acs-aem-commons/pages/compatibility.html#aem-as-a-cloud-service-feature-incompatibility) pour déterminer le niveau de compatibilité avec AEM as a Cloud Service.


<!--
### Adobe Experience Manager 6.2 and 6.1 {#aem-specific-versions}
 
The Best Practices Analyzer tool is limited in Adobe Experience Manager 6.2 to a link that generates and downloads the CSV report.

For Adobe Experience Manager 6.1, the tool is not functional and only the HTTP interface may be used.

>[!NOTE]
>In all versions, the included Pattern Detector may run independently.
-->

## Interprétation du rapport de l’analyseur des bonnes pratiques {#cra-report}

[!CONTEXTUALHELP]
id="aemcloud_bpa_interpreting"
title="Interprétation du rapport de l’analyseur des bonnes pratiques"
abstract="Il existe deux options pour afficher les sorties de rapport de l’analyseur des bonnes pratiques : IU et CSV. Lorsque l’analyseur des bonnes pratiques est exécuté dans l’instance AEM, le rapport de l’IU s’affiche sous la forme de résultats dans la fenêtre des outils. Le format CSV du rapport contient des informations générées à partir de la sortie du détecteur de motifs, triées et organisées par types de catégories, sous-types et niveaux d’importance."
additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=fr#analysis-report" text="Rapport d’analyse des bonnes pratiques"
additional-url="https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html?lang=fr" text="Présentation des catégories de rapports de l’analyseur des bonnes pratiques"

Lorsque l’analyseur des bonnes pratiques est exécuté dans l’instance AEM, le rapport s’affiche sous la forme de résultats dans la fenêtre des outils.

Le format du rapport est le suivant :

* **Report Overview** : informations sur le rapport lui-même qui incluent les informations suivantes :
   * **Report Time** : heure à laquelle le contenu du rapport a été généré et rendu disponible pour la première fois.
   * **Expiration Time** : heure d’expiration du cache du contenu du rapport.
   * **Generation Time Period** : durée du processus de génération du contenu du rapport.
   * **Finding Count** : nombre total de résultats figurant dans le rapport.
* **System Overview** : informations concernant le système AEM sur lequel l’analyseur des bonnes pratiques a été exécuté.
* **Finding Categories** : différentes sections traitant chacune d’un ou plusieurs résultats pour une même catégorie. Chaque section comprend les éléments suivants : nom de la catégorie, sous-types, nombre et importance des résultats, résumé, lien vers la documentation de la catégorie et informations relatives à chaque résultat.

Un niveau d’importance est attribué à chaque résultat pour indiquer une priorité absolue concernant l’action.

>[!NOTE]
Pour en savoir plus sur chaque catégorie de résultat, consultez [Catégories du détecteur de motifs](https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html?lang=fr).

Consultez le tableau ci-dessous pour comprendre les niveaux d’importance :

| Importance | Description |
|--- |--- |
| INFO | Ce résultat est fourni à titre d’information. |
| ADVISORY | Ce résultat peut poser un problème de mise à niveau. Il est recommandé d’approfondir les investigations. |
| MAJOR | Il est probable que ce résultat constitue un problème de mise à niveau qui doit être résolu. |
| CRITICAL | Il est très probable que ce résultat constitue un problème de mise à niveau qui doit être résolu pour éviter toute perte de fonction ou de performances. |


## Interprétation du rapport CSV de l’analyseur des bonnes pratiques {#cra-csv-report}

Lorsque vous cliquez sur l’option **CSV** de votre instance AEM, le format CSV du rapport de l’analyseur des bonnes pratiques est créé à partir du cache de contenu et renvoyé à votre navigateur. En fonction des paramètres du navigateur, ce rapport sera automatiquement téléchargé sous la forme d’un fichier portant le nom `results.csv` par défaut.

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

L’analyseur des bonnes pratiques fournit une interface HTTP, utilisable comme alternative à son interface utilisateur dans AEM. L’interface prend en charge les commandes HEAD et GET. Il peut être utilisé pour générer le rapport BPA et le renvoyer dans l’un des trois formats suivants : JSON, CSV et TSV (valeurs séparées par des tabulations).

Les URL suivantes sont disponibles pour l’accès HTTP, où `<host>` est le nom d’hôte et, si nécessaire, le port du serveur sur lequel l’analyseur des bonnes pratiques est installé :
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

Lorsqu’une requête a été effectuée, le client n’a pas besoin de rester actif pour que le rapport soit généré. La génération du rapport peut être lancée avec un client à l’aide d’une requête GET HTTP. Une fois le rapport généré, il peut être affiché à l’aide du cache d’un autre client ou de l’outil BPA de l’interface utilisateur AEM.

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

La durée de vie par défaut du cache l’analyseur des bonnes pratiques est de 24 heures. Avec l’option destinée à actualiser un rapport et à régénérer le cache, aussi bien dans l’instance AEM que dans l’interface HTTP, cette valeur par défaut sera probablement appropriée pour la plupart des utilisations du BPA. Si le temps de génération du rapport est particulièrement long pour votre instance AEM, vous pouvez ajuster la durée de vie du cache afin de minimiser la nouvelle génération d’un rapport.

La durée de vie du cache est stockée dans la propriété `maxCacheAge` dans le nœud de référentiel suivant :
`/apps/best-practices-analyzer/content/BestPracticesReport/jcr:content`

La valeur de cette propriété est la durée de vie du cache en secondes. Un administrateur peut ajuster la durée de vie du cache à l’aide de CRX/DE Lite.

### Installation sur AEM 6.1 {#installing-on-aem61}

BPA utilise un compte d’utilisateur de service système nommé `repository-reader-service` pour exécuter le détecteur de motifs. Ce compte est disponible dans AEM 6.2 et versions ultérieures. Dans AEM 6.1, ce compte doit être créé *avant* l’installation de BPA en procédant comme suit :

1. Suivez les instructions de la section [Création d’un utilisateur de service](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-service-users.html?lang=fr#creating-a-new-service-user) pour créer un utilisateur. Définissez l’ID utilisateur sur `repository-reader-service` et laissez le champ Chemin intermédiaire vide, puis cliquez sur la coche verte.

2. Suivez les instructions de la section [Gestion des utilisateurs et des groupes](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html?lang=fr#managing-users-and-groups), en particulier les instructions d’ajout d’utilisateurs à un groupe afin d’ajouter l’utilisateur `repository-reader-service` au groupe `administrators`.

3. Installez le package BPA via le gestionnaire de modules sur votre instance AEM source. (Cela a pour effet d’ajouter la modification de configuration nécessaire à la configuration ServiceUserMapper pour l’utilisateur du service système `repository-reader-service`.)
