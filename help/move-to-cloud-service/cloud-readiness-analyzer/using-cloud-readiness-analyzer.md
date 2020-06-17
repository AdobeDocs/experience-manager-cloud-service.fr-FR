---
title: Utilisation de Cloud Readiness Analyzer
description: Utilisation de Cloud Readiness Analyzer
translation-type: tm+mt
source-git-commit: 0565d053b6040bc99ae79823711d56eb9aecdfb3
workflow-type: tm+mt
source-wordcount: '1709'
ht-degree: 1%

---


# Utilisation de Cloud Readiness Analyzer {#using-cloud-readiness-analyzer}

## Considérations importantes pour l’utilisation de Cloud Readiness Analyzer {#imp-considerations}

Suivez la section ci-dessous pour comprendre les points importants à prendre en compte pour l&#39;exécution de l&#39;outil Cloud Readiness Analyzer (CRA) :

* Le rapport ARC est généré à l’aide de la sortie du détecteur [de](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/upgrading/pattern-detector.html)schémas d’Adobe Experience Manager (AEM). La version du détecteur de schémas utilisée par l&#39;ARC est incluse dans la trousse d&#39;installation de l&#39;ARC.

* L&#39;ARC ne peut être exécutée que par l&#39;utilisateur **administrateur** ou un utilisateur du groupe **Administrateurs** .

* L’ARC est prise en charge sur les instances AEM avec les versions 6.1 et ultérieures.

* L&#39;ARC peut s&#39;exécuter sur n&#39;importe quel environnement, mais il est préférable de l&#39;exécuter sur un environnement *d&#39;étape* .

   >[!NOTE]
   >Afin d&#39;éviter un impact sur les instances critiques de l&#39;entreprise, il est recommandé d&#39;exécuter CRA sur un environnement *Auteur* aussi proche que possible de l&#39;environnement *Production* dans les domaines de la personnalisation, de la configuration, du contenu et des applications utilisateur. Vous pouvez également l’exécuter sur un clone de l’ *environnement d’auteur* de production.

* La production du contenu des rapports de l&#39;ARC peut prendre beaucoup de temps, de plusieurs minutes à quelques heures. La durée requise dépend largement de la taille et de la nature du contenu du référentiel AEM, de la version AEM et d’autres facteurs.

* En raison du temps important qui peut être nécessaire pour générer le contenu du rapport, ils sont générés par un processus en arrière-plan et conservés dans un cache. L&#39;affichage et le téléchargement du rapport doivent être relativement rapides, car il utilise le cache de contenu jusqu&#39;à son expiration ou parce que le rapport est explicitement actualisé. Pendant la génération du contenu du rapport, vous pouvez fermer l&#39;onglet du navigateur et revenir ultérieurement à la vue du rapport une fois son contenu disponible dans le cache.

## Disponibilité {#availability}

L&#39;analyseur de l&#39;état de préparation du cloud peut être téléchargé sous la forme d&#39;un fichier zip depuis le portail de distribution de logiciels. Vous pouvez installer le module par le biais du gestionnaire de modules sur votre instance source Adobe Experience Manager (AEM).

>[!NOTE]
>Téléchargez Cloud Readiness Analyzer sur le portail de distribution de logiciels.

## Affichage du rapport Cloud Readiness Analyzer {#viewing-report}

### Adobe Experience Manager 6.3.0 et versions ultérieures {#aem-later-versions}

Suivez cette section pour savoir comment vue le rapport Cloud Readiness Analyzer :

1. Sélectionnez Adobe Experience Manager et accédez aux outils -> **Opérations** -> **Cloud Readiness Analyzer**.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-1.png)

1. Une fois que vous avez cliqué sur **Cloud Readiness Analyzer**, l’outil début à générer le rapport et l’affiche lorsqu’il est disponible.

   >[!NOTE]
   >Vous devrez faire défiler la page vers le bas pour vue au rapport complet.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-tool-1.png)

1. Une fois le rapport ARC généré et affiché, vous avez la possibilité de télécharger le rapport au format CSV (valeurs séparées par des virgules) en cliquant sur **CSV**, comme le montre la figure ci-dessous.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-tool-2.png)

   >[!NOTE]
   >Vous pouvez forcer l&#39;ARC à effacer son cache et à régénérer le rapport en cliquant sur **Actualiser le rapport**.

### Adobe Experience Manager 6.2 et 6.1 {#aem-specific-versions}

L’outil Cloud Readiness Analyzer est limité dans l’Adobe Experience Manager 6.2 à un lien qui génère et télécharge le rapport CSV.

Pour l’Adobe Experience Manager 6.1, l’outil n’est pas fonctionnel et seule l’interface HTTP peut être utilisée.

>[!NOTE]
>Dans toutes les versions, le Détecteur de schémas inclus peut s’exécuter indépendamment.

## Interprétation du rapport Cloud Readiness Analyzer {#cra-report}

Lorsque l’outil Cloud Readiness Analyzer est exécuté dans l’instance AEM, le rapport s’affiche en tant que résultats dans la fenêtre de l’outil.

Le format du rapport est le suivant :

* **Aperçu** du rapport : Informations sur le rapport lui-même qui incluent les informations suivantes :
   * **Heure** du rapport : Lorsque le contenu du rapport a été généré et rendu disponible pour la première fois.
   * **Heure** d&#39;expiration : Date d&#39;expiration du cache du contenu du rapport.
   * **Période** de génération : Temps passé par le processus de génération du contenu du rapport.
   * **Recherche du décompte**: Nombre total de constatations figurant dans le rapport.
* **Présentation** du système : Informations sur le système AEM sur lequel l&#39;ARC a été exécutée.
* **Recherche de Catégories**: Plusieurs sections qui traitent chacune d’une ou de plusieurs constatations de la même catégorie. Chaque section comprend les éléments suivants : Nom de la Catégorie, sous-types, nombre et importance de la recherche, résumé, lien vers la documentation de la catégorie et informations de recherche individuelles.

Un niveau d&#39;importance est attribué à chaque découverte pour indiquer une priorité absolue de l&#39;action.

Suivez le tableau ci-dessous pour comprendre les niveaux d&#39;importance :

| Importance | Description |
|--- |--- |
| INFO | Cette conclusion est fournie à titre d&#39;information. |
| CONSEILLER | Cette recherche peut poser un problème de mise à niveau. Il est recommandé d&#39;approfondir l&#39;enquête. |
| MAJOR | Il est probable que cette découverte soit un problème de mise à niveau qui devrait être résolu. |
| CRITIQUE | Il est très probable que cette découverte soit un problème de mise à niveau qui doit être résolu pour éviter toute perte de fonction ou de performances. |


## Interprétation du rapport CSV de l’analyseur de l’état de préparation du cloud {#cra-csv-report}

Lorsque vous cliquez sur l’option **CSV** de votre instance AEM, le format CSV du rapport Cloud Readiness Analyzer est créé à partir du cache de contenu et renvoyé à votre navigateur. Selon les paramètres du navigateur, ce rapport sera automatiquement téléchargé sous la forme d&#39;un fichier portant le nom `results.csv`par défaut.

Si le cache a expiré, le rapport est régénéré avant la création et le téléchargement du fichier CSV.

Le format CSV du rapport comprend des informations générées à partir de la sortie du détecteur de schémas, triées et organisées par type de catégorie, sous-type et niveau d’importance. Son format est adapté à l’affichage et à la modification dans une application telle que Microsoft Excel. Il vise à fournir toutes les informations de recherche sous une forme répétable qui peut s&#39;avérer utile lors de la comparaison des rapports au fil du temps pour mesurer les progrès.

Les colonnes du rapport au format CSV sont les suivantes :

* **code**: le code de catégorie
* **type**: nom de la catégorie
* **sous-type**: le sous-type catégorie
* **importance**: niveau d&#39;importance
* **identificateur**: l&#39;identifiant principal de la recherche
* **autre**: informations supplémentaires sur la recherche
* **message**: le message fourni pour la recherche
* **moreInfo**: un lien qui peut être utilisé pour accéder à l&#39;aide en ligne sur la catégorie
* **contexte**: une chaîne JSON de recherche de données ;

La valeur &quot;\N&quot; dans une colonne pour une recherche individuelle indique qu&#39;aucune donnée n&#39;a été fournie.

## Interface HTTP {#http-interface}

L’ARC fournit une interface HTTP qui peut être utilisée comme alternative à son interface utilisateur dans AEM. L’interface prend en charge les commandes HEAD et GET. Il peut être utilisé pour générer le rapport de l&#39;ARC et le renvoyer dans l&#39;un des trois formats suivants : JSON, CSV et valeurs séparées par des tabulations (TSV).

Les URL suivantes sont disponibles pour l&#39;accès HTTP, où `<host>` est le nom d&#39;hôte et le port si nécessaire du serveur sur lequel l&#39;ARC est installé :
* `http://<host>/apps/readiness-analyzer/analysis/result.json` pour le format JSON
* `http://<host>/apps/readiness-analyzer/analysis/result.csv` pour le format CSV
* `http://<host>/apps/readiness-analyzer/analysis/result.tsv` pour le format TSV

### Exécution d’une requête HTTP {#executing-http-request}

L&#39;interface HTTP peut être utilisée de différentes manières.

Une méthode simple consiste à ouvrir un onglet de navigateur dans le même navigateur dans lequel vous vous êtes déjà connecté à AEM en tant qu’administrateur. Vous pouvez entrer l’URL dans l’onglet du navigateur et afficher ou télécharger les résultats par le navigateur.

Vous pouvez également utiliser un outil de ligne de commande tel que `curl` ou `wget` ainsi que toute application cliente HTTP. Lorsque vous n’utilisez pas l’onglet du navigateur avec une session authentifiée, vous devez fournir un nom d’utilisateur et un mot de passe administratifs dans le cadre du commentaire.

Voici un exemple de la façon de procéder :
`curl -u admin:admin 'http://localhost:4502/apps/readiness-analyzer/analysis/result.csv' > result.csv`.

### En-têtes et paramètres {#http-headers-and-parameters}

Les en-têtes HTTP suivants sont utilisés par cette interface :

* `Cache-Control: max-age=<seconds>`: Spécifiez la durée de vie de fraîcheur du cache en secondes. (Voir [RFC 7234](https://tools.ietf.org/html/rfc7234#section-5.2.2.8).)
* `Prefer: respond-async`: Indique que le serveur doit répondre de manière asynchrone. (Voir [RFC 7240](https://tools.ietf.org/html/rfc7240#section-4.1).)

Les paramètres de requête HTTP suivants sont disponibles à titre de commodité lorsque des en-têtes HTTP peuvent ne pas être facilement utilisés :

* `max-age` (nombre, facultatif) : Spécifiez la durée de vie de fraîcheur du cache en secondes. Ce nombre doit être égal ou supérieur à 0. La durée de vie par défaut de la fraîcheur est de 86 400 secondes, ce qui signifie que sans ce paramètre ou l’en-tête correspondant, un nouveau cache sera utilisé pour répondre aux demandes pendant 24 heures avant que le rapport ne soit régénéré. L&#39;utilisation `max-age=0` forcera le cache à être effacé et déclenchera une régénération du rapport. Immédiatement après cette demande, la durée de vie de la fraîcheur sera réinitialisée à la valeur antérieure non nulle.
* `respond-async` (booléen, facultatif) : Spécifiez que la réponse doit être fournie de manière asynchrone. Si `respond-async=true` le cache est obsolète, le serveur renvoie une réponse de `202 Accepted, processing cache` sans attendre que le rapport soit généré et que le cache soit actualisé. Si le cache est neuf, ce paramètre n’a aucun effet. La valeur par défaut est `false`, ce qui signifie que sans ce paramètre ou l’en-tête correspondant, le serveur répondra de manière synchrone, ce qui peut nécessiter un temps important et un ajustement du temps de réponse maximal pour le client HTTP.

Si un en-tête HTTP et le paramètre de requête correspondant sont présents, le paramètre de requête est prioritaire.

La commande suivante permet simplement de lancer la génération du rapport via l’interface HTTP :
`curl -u admin:admin 'http://localhost:4502/apps/readiness-analyzer/analysis/result.json?max-age=0&respond-async=true'`.

Une fois qu&#39;une requête a été effectuée, le client n&#39;a pas besoin de rester actif pour que le rapport soit généré. La génération du rapport peut être lancée avec un client à l’aide d’une requête HTTP GET et, une fois le rapport généré, affiché à partir du cache d’un autre client ou de l’outil CSV dans l’interface utilisateur d’AEM.

### Réponses (#http-response)

Les valeurs de réponse suivantes sont possibles :

* `200 OK`: La réponse contient les résultats du détecteur de schémas qui ont été générés pendant la durée de vie de la mémoire cache.
* `202 Accepted, processing cache`: Fourni pour les réponses asynchrones afin d’indiquer que le cache était obsolète et qu’une actualisation est en cours.
* `400 Bad Request`: Indique qu’une erreur s’est produite lors de la demande. Un message au format Détails du problème (voir [RFC 7807](https://tools.ietf.org/html/rfc7807)) fournit plus de détails.
* `401 Unauthorized`: La demande n&#39;a pas été autorisée.
* `500 Internal Server Error`: Indique qu’une erreur de serveur interne s’est produite. Un message au format Détails du problème fournit plus de détails.
* `503 Service Unavailable`: Indique que le serveur est occupé par une autre réponse et qu’il ne peut pas traiter cette demande en temps opportun. Cela ne se produit que lorsque des requêtes synchrones sont effectuées. Un message au format Détails du problème fournit plus de détails.

## Réglage de la durée de vie du cache {#cache-adjustment}

La durée de vie par défaut du cache de l&#39;ARC est de 24 heures. Avec l’option permettant d’actualiser un rapport et de régénérer le cache, tant dans l’instance AEM que dans l’interface HTTP, cette valeur par défaut est susceptible d’être appropriée pour la plupart des utilisations de l’ARC. Si le temps de génération du rapport est particulièrement long pour votre instance AEM, vous pouvez ajuster la durée de vie du cache afin de minimiser la régénération du rapport.

La valeur de durée de vie du cache est stockée en tant que `maxCacheAge` propriété sur le noeud de référentiel suivant :
`/apps/readiness-analyzer/content/CloudReadinessReport/jcr:content`

La valeur de cette propriété est la durée de vie du cache en secondes. Un administrateur peut ajuster la durée de vie du cache à l’aide de CRX/DE Lite.





