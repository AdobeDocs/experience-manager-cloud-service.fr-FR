---
title: Recherche et indexation de contenu
description: Recherche et indexation de contenu
translation-type: tm+mt
source-git-commit: 610615534cb5a798e37d34fadb9a3bf341565526
workflow-type: tm+mt
source-wordcount: '1521'
ht-degree: 2%

---


# Recherche et indexation de contenu {#indexing}

## Changements de l’AEM en tant que Cloud Service {#changes-in-aem-as-a-cloud-service}

Avec l’AEM en tant que Cloud Service, l’Adobe s’éloigne d’un modèle centré sur les instances AEM pour passer à une vue basée sur les services avec des Conteneurs n-x, pilotés par des pipelines CI/CD dans Cloud Manager. Au lieu de configurer et de gérer les index sur des instances d&#39;AEM uniques, la configuration d&#39;index doit être spécifiée avant un déploiement. Les changements de configuration dans la production enfreignent clairement les politiques de CI/CD. Il en va de même pour les changements d&#39;index, car ils peuvent avoir un impact sur la stabilité et les performances du système si elles ne sont pas spécifiées et réindexées avant leur mise en production.

Voici une liste des principaux changements par rapport à AEM version 6.5 et antérieure :

1. Les utilisateurs n’auront plus accès au Gestionnaire d’index d’une seule instance AEM pour déboguer, configurer ou gérer l’indexation. Il n&#39;est utilisé que pour le développement local et les déploiements sur site.

1. Les utilisateurs ne changeront pas d’index sur une seule instance AEM et n’auront plus à s’inquiéter des vérifications de cohérence ou de la réindexation.

1. En général, les changements d’index sont amorcés avant d’être mis en production afin de ne pas contourner les passerelles de qualité dans les pipelines CI/CD de Cloud Manager et de ne pas avoir d’incidence sur les IPC métier en production.

1. Toutes les mesures connexes, y compris les performances de recherche en production, seront disponibles pour les clients au moment de l’exécution afin de fournir une vue holistique sur les sujets de recherche et d’indexation.

1. Les clients pourront configurer des alertes en fonction de leurs besoins.

1. Les SRE surveillent la santé du système 24 heures sur 24, 7 jours sur 7 et prendront les mesures nécessaires et le plus tôt possible.

1. La configuration de l’index est modifiée par le biais de déploiements. Les modifications apportées à la définition de l’index sont configurées comme les autres modifications apportées au contenu.

1. À un niveau élevé, AEM Cloud Service, avec l&#39;introduction du modèle [de déploiement](#index-management-using-blue-green-deployments) Blue-Green, deux ensembles d&#39;index existeront : l&#39;un pour l&#39;ancienne version (bleu), l&#39;autre pour la nouvelle version (vert).

1. Les clients peuvent déterminer si la tâche d’indexation est terminée sur la page de création de Cloud Manager et ils recevront une notification lorsque la nouvelle version sera prête à recevoir du trafic.

1. Limites : actuellement, la gestion des index sur AEM en tant que Cloud Service n&#39;est prise en charge que pour les index de type lucene.

<!-- ## Sizing Considerations {#sizing-considerations}

AEM as a Cloud Service comes with a default capacity model to provide sufficient performance for average web applications. This "average" measure relates to the repository size and even more relevant to the indexing size. If we have reasons to believe that we need extended capacity for a specific customer project, an evaluation with SREs and Engineering will take place to determine the required capacity settings.

AS NOTE: the above is internal for now.

-->

## Utilisation {#how-to-use}

La définition d&#39;index peut comprendre les trois cas d&#39;utilisation suivants :

1. ajouter une nouvelle définition d&#39;index client
1. Mise à jour d’une définition d’index existante. Cela signifie en effet l’ajout d’une nouvelle version d’une définition d’index existante.
1. Suppression d’un index existant redondant ou obsolète.

Pour les points 1 et 2 ci-dessus, vous devez créer une nouvelle définition d’index dans le cadre de votre base de code personnalisé dans le calendrier de publication de Cloud Manager correspondant. Pour plus d’informations, voir la documentation [](/help/implementing/deploying/overview.md)Déploiement sur AEM en tant que Cloud Service.

### Préparation de la nouvelle définition d&#39;index {#preparing-the-new-index-definition}

Vous devez préparer un nouveau package de définition d&#39;index qui contient la définition d&#39;index réelle, en suivant ce modèle de dénomination :

`<indexName>[-<productVersion>]-custom-<customVersion>`

qui doit ensuite passer sous `ui.apps/src/main/content/jcr_root`la barre. Les dossiers de sous-racine ne sont pas pris en charge pour l&#39;instant.

<!-- need to review and link info on naming convention from https://wiki.corp.adobe.com/display/WEM/Merging+Customer+and+OOTB+Index+Changes?focusedCommentId=1784917629#comment-1784917629 -->

Le package de l&#39;exemple ci-dessus est créé comme `com.adobe.granite:new-index-content:zip:1.0.0-SNAPSHOT`.

### Déploiement des définitions d’index {#deploying-index-definitions}

>[!NOTE]
>
>Il existe un problème connu avec Jackrabbit Filevault Maven Package Plugin version **1.1.0** qui ne vous permet pas d&#39;ajouter `oak:index` aux modules de `<packageType>application</packageType>`. Pour contourner ce problème, utilisez la version **1.0.4**.

Les définitions d’index sont désormais marquées comme personnalisées et avec version :

* La définition d’index elle-même (par exemple `/oak:index/ntBaseLucene-custom-1`)

Par conséquent, pour déployer un index, la définition de l’index (`/oak:index/definitionname`) doit être fournie via `ui.apps` Git et le processus de déploiement de Cloud Manager.

Une fois la nouvelle définition d’index ajoutée, la nouvelle application doit être déployée via Cloud Manager. Au moment du déploiement, deux tâches sont démarrées, chargées d&#39;ajouter (et de fusionner si nécessaire) les définitions d&#39;index à MongoDB et Azure Segment Store pour l&#39;auteur et la publication, respectivement. Les référentiels sous-jacents sont réindexés avec les nouvelles définitions d&#39;index, avant que le commutateur Blue-Green n&#39;ait lieu.

>[!TIP]
>
>Pour plus de détails sur la structure de package requise pour AEM en tant que Cloud Service, voir la structure de projet de l&#39; [AEM document.](/help/implementing/developing/introduction/aem-project-content-package-structure.md)

## Gestion des index à l’aide de déploiements Blue-Green {#index-management-using-blue-green-deployments}

### Présentation de la gestion des index {#what-is-index-management}

La gestion des index consiste à ajouter, supprimer et modifier des index. La modification de la *définition* d&#39;un index est rapide, mais l&#39;application de la modification (souvent appelée &quot;création d&#39;un index&quot;, ou, pour les index existants, &quot;réindexation&quot;) nécessite du temps. Elle n&#39;est pas instantanée : le référentiel doit être analysé pour que les données soient indexées.

### Qu&#39;est-ce que le déploiement bleu-vert {#what-is-blue-green-deployment}

Le déploiement Blue-Green peut réduire les temps d’inactivité. Il permet également des mises à niveau sans interruption de service et permet des remises en service rapides. L’ancienne version de l’application (bleue) s’exécute en même temps que la nouvelle version de l’application (verte).

### Zones en lecture seule et en lecture-écriture {#read-only-and-read-write-areas}

Certaines zones du référentiel (parties en lecture seule du référentiel) peuvent être différentes dans l&#39;ancienne (bleue) et dans la nouvelle version (verte) de l&#39;application. Les zones en lecture seule du référentiel sont généralement &quot;`/app`&quot; et &quot;`/libs`&quot;. Dans l’exemple suivant, l’italique est utilisé pour marquer les zones en lecture seule, tandis que l’gras est utilisé pour les zones en lecture-écriture.

* **/**
* */apps (lecture seule)*
* **/content**
* */libs (lecture seule)*
* **/oak:index**
* **/oak:index/acme.**
* **/jcr:system**
* **/system**
* **/var**

Les zones de lecture-écriture du référentiel sont partagées entre toutes les versions de l&#39;application, tandis que pour chaque version de l&#39;application, il existe un ensemble spécifique de `/apps` et `/libs`.

### Gestion des index sans déploiement bleu-vert {#index-management-without-blue-green-deployment}

Lors du développement ou de l’utilisation sur site d’installations, les index peuvent être ajoutés, supprimés ou modifiés au moment de l’exécution. Les index sont utilisés dès qu&#39;ils sont disponibles. Si un index n&#39;est pas censé être utilisé dans l&#39;ancienne version de l&#39;application, il est généralement créé lors d&#39;un arrêt planifié. Il en va de même lors de la suppression d&#39;un index ou de la modification d&#39;un index existant. Lors de la suppression d’un index, il devient indisponible dès sa suppression.

### Gestion des index avec déploiement bleu-vert {#index-management-with-blue-green-deployment}

Avec des déploiements bleu-vert, il n&#39;y a pas de temps d&#39;arrêt. Toutefois, pour la gestion des index, cela nécessite que les index ne soient utilisés que par certaines versions de l’application. Par exemple, lorsque vous ajoutez un index dans la version 2 de l’application, vous ne souhaitez pas qu’il soit encore utilisé par la version 1 de l’application. L’inverse est le cas lorsqu’un index est supprimé : un index supprimé dans la version 2 est toujours nécessaire dans la version 1. Lors de la modification d&#39;une définition d&#39;index, nous voulons que l&#39;ancienne version de l&#39;index soit utilisée uniquement pour la version 1 et la nouvelle version de l&#39;index uniquement pour la version 2.

Le tableau suivant présente 5 définitions d’index : index `cqPageLucene` est utilisé dans les deux versions alors que index `damAssetLucene-custom-1` est utilisé uniquement dans la version 2.

>[!NOTE]
>
>`<indexName>-custom-<customerVersionNumber>` est nécessaire pour que AEM, en tant que Cloud Service, puisse marquer cela comme un remplacement pour un index existant.

| Index | Index prêt à l&#39;emploi | Utilisation dans la version 1 | Utilisation dans la version 2 |
|---|---|---|---|
| /oak:index/damAssetLucene | Oui | Oui | Non |
| /oak:index/damAssetLucene-custom-1 | Oui (personnalisé) | Non | Oui |
| /oak:index/acme.product-custom-1 | Non | Oui | Non |
| /oak:index/acme.product-custom-2 | Non | Non | Oui |
| /oak:index/cqPageLucene | Oui | Oui | Oui |

Le numéro de version est incrémenté chaque fois que l&#39;index est modifié. Pour éviter que des noms d&#39;index personnalisés ne entrent en collision avec des noms d&#39;index du produit lui-même, les index personnalisés, ainsi que les modifications apportées aux index prêts à l&#39;emploi, doivent se terminer par `-custom-<number>`.

### Modifications apportées aux index prêts à l’emploi {#changes-to-out-of-the-box-indexes}

Une fois que l’Adobe a modifié un index prêt à l’emploi tel que &quot;damAssetLucene&quot; ou &quot;cqPageLucene&quot;, un nouvel index nommé `damAssetLucene-2` ou `cqPageLucene-2` est créé ou, si l’index a déjà été personnalisé, la définition d’index personnalisé est fusionnée avec les modifications de l’index prêt à l’emploi, comme illustré ci-dessous. La fusion des modifications se produit automatiquement. Cela signifie que vous n&#39;avez rien à faire si un index prêt à l&#39;emploi change. Cependant, il est possible de personnaliser à nouveau l’index ultérieurement.

| Index | Index prêt à l&#39;emploi | Utilisation dans la version 2 | Utilisation dans la version 3 |
|---|---|---|---|
| /oak:index/damAssetLucene-custom-1 | Oui (personnalisé) | Oui | Non |
| /oak:index/damAssetLucene-2-custom-1 | Oui (automatiquement fusionné à partir de damAssetLucene-custom-1 et damAssetLucene-2) | Non | Oui |
| /oak:index/cqPageLucene | Oui | Oui | Non |
| /oak:index/cqPageLucene-2 | Oui | Non | Oui |

### Restrictions {#limitations}

Actuellement, la gestion des index n&#39;est prise en charge que pour les index de type `lucene`.

### Suppression d&#39;un index {#removing-an-index}

Si un index doit être supprimé dans une version ultérieure de l’application, vous pouvez définir un index vide (un index sans données à indexer), avec un nouveau nom. Par exemple, vous pouvez lui donner un nom `/oak:index/acme.product-custom-3`. Cette opération remplace l’index `/oak:index/acme.product-custom-2`. Une fois `/oak:index/acme.product-custom-2` supprimé par le système, l&#39;index vide `/oak:index/acme.product-custom-3` peut également être supprimé.

### ajouter un index {#adding-an-index}

Pour ajouter un index nommé &quot;/oak:index/acme.product-custom-1&quot; à utiliser dans une nouvelle version de l’application et ultérieure, l’index doit être configuré comme suit :

`acme.product-1-custom-1`

Cette opération consiste à ajouter un identifiant personnalisé au nom de l’index, suivi d’un point (**`.`**). L’identifiant doit comporter entre 2 et 5 caractères.

Comme ci-dessus, cela permet de s’assurer que l’index n’est utilisé que par la nouvelle version de l’application.

### Modification d’un index {#changing-an-index}

Lorsqu’un index existant est modifié, un nouvel index doit être ajouté avec la définition d’index modifiée. Par exemple, considérez que l’index existant &quot;/oak:index/acme.product-custom-1&quot; a été modifié. L&#39;ancien index est stocké sous `/oak:index/acme.product-custom-1`et le nouvel index sous `/oak:index/acme.product-custom-2`.

L’ancienne version de l’application utilise la configuration suivante :

`/oak:index/acme.product-custom-1`

La nouvelle version de l’application utilise la configuration suivante (modifiée) :

`/oak:index/acme.product-custom-2`

### Disponibilité de l&#39;index/Tolérance aux pannes {#index-availability}

Il est recommandé de créer des index de duplicata pour les fonctions extrêmement importantes (en gardant à l&#39;esprit la convention d&#39;attribution de noms pour les index mentionnés ci-dessus), de sorte que dans le cas de corruption d&#39;index ou de tout événement imprévu de ce type, un index de secours est disponible pour répondre aux requêtes.
