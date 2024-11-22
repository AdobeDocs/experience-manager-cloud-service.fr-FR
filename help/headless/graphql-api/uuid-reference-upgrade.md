---
title: Mise à niveau des fragments de contenu pour les références UID
description: Découvrez comment mettre à niveau vos fragments de contenu pour obtenir des références UUID optimisées dans Adobe Experience Manager as a Cloud Service pour une diffusion de contenu sans interface utilisateur.
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: 5aa04f3b042f8e9f9af97148ceab0288ff210238
workflow-type: tm+mt
source-wordcount: '1157'
ht-degree: 2%

---

# Mise à niveau des fragments de contenu pour les références UID {#upgrade-content-fragments-for-UUID-references}

>[!IMPORTANT]
>
>Diverses fonctionnalités de l’API GraphQL à utiliser avec les fragments de contenu sont disponibles via le programme Adopteur anticipé.
>
>Pour connaître l’état et savoir comment vous appliquer si vous le souhaitez, consultez les [notes de mise à jour](/help/release-notes/release-notes-cloud/release-notes-current.md).

Pour optimiser la stabilité de vos filtres GraphQL, vous pouvez mettre à niveau le contenu et les références aux fragments dans vos fragments de contenu afin qu’ils utilisent des identifiants universellement uniques (UUID).

À l’origine, les modèles de fragment de contenu fournissaient les types de données **Référence du contenu** et **Référence du fragment**. Ces deux références utilisent un chemin d’accès pour pointer vers la ressource référencée, et ce chemin peut devenir obsolète si la ressource est déplacée. Bien que ces références soient plus que suffisantes dans la plupart des scénarios, les modèles de fragment de contenu ont été étendus afin de fournir également des références basées sur un UUID :

* **Référence du contenu (UUID)**
* **Référence de fragment (UUID)**.

Ces nouveaux types de référence peuvent être utilisés à la fois dans les nouveaux modèles de fragment de contenu et dans les fragments, et pour étendre les instances existantes.

Pour mettre à niveau des fragments et des modèles de contenu existants, vous pouvez exécuter la procédure décrite ici.

>[!CAUTION]
>
>Avant d&#39;exécuter la procédure de mise à niveau, vous devez toujours [Exécuter une exécution d&#39;essai](#execute-a-dry-run) pour mettre en évidence les problèmes potentiels liés à votre contenu.

## Éléments mis à niveau {#what-is-upgraded}

Les mises à jour suivantes sont effectuées :

* Champs des types de données :
   * **Référence du contenu** sont convertis en **Référence du contenu (UUID)**
   * **Référence du fragment** sont convertis en **Référence du fragment (UUID)**
* Les valeurs des références basées sur un chemin contenues dans ces champs sont remplacées par les UUID correspondants.

>[!NOTE]
>
>Après la mise à niveau, les deux types de données sont toujours disponibles dans l’éditeur de modèle de fragment de contenu. Vous pouvez créer des champs basés sur les deux types (bien qu’il soit prévu que vous utilisiez les types basés sur l’UUID) et relancer la mise à niveau si nécessaire.

## Éléments NON mis à niveau {#what-is-not-upgraded}

Les références suivantes ne sont pas mises à niveau :

* Références de page : les UUID ne sont pas encore pris en charge
* Toute référence non valide, par exemple, où la cible du chemin de fragment de contenu ou du chemin d’accès à la ressource n’existe pas

   * Les références non valides ne sont pas mises à niveau, comme si le chemin du fragment de contenu ou le chemin d’accès à la ressource n’était pas valide, il n’y a pas d’UUID correspondant à affecter. La référence d&#39;origine reste intacte.

   * Utilisez un [dry run](#execute-a-dry-run) pour supprimer les références non valides.

  >[!NOTE]
  >
  >Invalides, elles ne sont pas utilisables, quelle que soit la mise à niveau.

## Lorsque vous ne devez pas effectuer la mise à niveau {#when-you-should-not-upgrade}

Ne pas mettre à niveau :

* Lorsque l’un de vos fragments de contenu utilise des références de page ; car les UUID ne sont pas encore pris en charge pour les références de page.

## Limites des références UUID {#limitations-of-uuid-references}

Actuellement, les restrictions suivantes s’appliquent lors de l’utilisation de références basées sur un UUID :

* Modèles

   * Les nouveaux modèles de fragment de contenu avec l’UUID de fragment de contenu ou les champs UUID de référence du contenu ne peuvent pas être créés via OpenAPI.
   * Le champ `id` des modèles n’a pas été modifié pour être basé sur l’UUID. Il utilise le chemin décodé base64 du modèle. Les modèles ne peuvent pas être déplacés. Par conséquent, cette valeur est toujours stable.

* Ressources

   * Lors de la création d’un fragment de contenu via OpenAPI, les types de champ `fragment-reference` ou `content-reference` doivent être utilisés pour spécifier respectivement des références à un fragment ou à une ressource, même lors de la définition de la valeur d’un champ de référence basé sur l’UUID.

## Planification de la mise à niveau {#upgrade-planning}

Il existe quelques étapes de préparation avant d’exécuter la mise à niveau.

### Exécution d’une exécution d’essai {#execute-a-dry-run}

Il est recommandé que *chaque* fois que vous mettez à niveau votre contenu, vous réalisiez une exécution d’essai. Cela crée des fichiers journaux avec des entrées qui mettent en évidence tout problème potentiel :

* Références non valides
* Références de page

Exécutez la mise à niveau du contenu en mode `dryRun` pour :

* identifier les références non valides ; en les répertoriant dans les fichiers journaux ;
Vous pouvez ensuite corriger ces références avant d’exécuter la mise à niveau réelle du contenu.
* identifier les références de page, en les répertoriant dans les fichiers journaux ;
Lorsque des références de page sont détectées, [ ne doit pas exécuter la mise à niveau de contenu](#when-you-should-not-upgrade).


### Application d’un gel du contenu {#enforce-a-content-freeze}

L&#39;exécution de l&#39;upgrade de contenu doit être planifiée pendant une période de gel du contenu.

La durée du gel du contenu dépend du volume des fragments de contenu mis à niveau. Par conséquent, la mise à niveau peut aller de quelques minutes à quelques heures et dépend également des paramètres utilisés lors du démarrage de la mise à niveau du contenu.

## Exécution de la mise à niveau du contenu {#running-the-content-upgrade}

La mise à niveau du contenu peut être gérée à l&#39;aide du point de terminaison : `/libs/dam/cfm/maintenance.json`

>[!NOTE]
>
>Votre compte a besoin du rôle `Administrator` pour accéder au point de terminaison .

### Commencer une mise à niveau de contenu {#start-a-content-upgrade}

| Point d’entrée | Type de requête HTTP | Commentaire |
|--- |--- |--- |
| `/libs/dam/cfm/maintenance.json` | `POST` | |
| **Paramètres de requête** | **Valeur**. | |
| action | `start` | |
| serviceTypeId | `uuidUpgradeService` | ID de type de service (prédéfini, valeur fixe). |
|  segmentSize | `1000` | Nombre de fragments de contenu ou de modèles qui seront mis à niveau dans un segment (lot). |
| basePath | `/conf` | Spécifiez l’une des options suivantes :<ul><li>la racine `/conf` pour mettre à niveau toutes les configurations AEM</li><li>un chemin de configuration d’AEM sélectionné. pour lequel la mise à niveau du contenu est exécutée<br>Par exemple : `/conf/wknd-shared` met uniquement à niveau le client unique `wknd-shared`</li></ul> |
| interval | `10` | Intervalle en secondes, après lequel le segment suivant de fragments de contenu ou de modèles est mis à niveau. |
| mode | `replicate`, `noReplicate` | <ul><li>`replicate` : réplique la même tâche sur toutes les instances Publish AEM</li><li>`noReplicate` : exécute uniquement la tâche sur les instances d’auteur AEM</li></ul> |
| dryRun |  `true`, `false` | <ul><li>`false` : simuler la mise à niveau du contenu, sans enregistrer les modifications du contenu</li><li>`true` : effectuez la mise à niveau du contenu et enregistrez les modifications du contenu</li></ul> |
| **Détails de la réponse** | **Valeur**. | |
| jobId | `UUID` |  L’identifiant de la tâche qui exécute la mise à niveau du contenu.<ul><li>Cet identifiant est requis dans tous les appels suivants liés à cette exécution.</li><li>Si la valeur `mode` est définie sur `replicate`, l’exécution sur les instances Publish AEM doit également se trouver sous le même `jobId`.</li></ul> |
| Paramètres | Paramètres de mise à niveau du contenu | Il s’agit notamment des paramètres initiaux fournis pour lancer la mise à niveau du contenu, ainsi que de certains paramètres internes. |


### Exemple de demande de mise à niveau de contenu {#example-content-upgrade-request}

+++Request

```http
POST http://localhost:4502/libs/dam/cfm/maintenance.json
Content-Type: application/json
Authorization: _REPLACE_WITH_VALID_AUTH_
Accept: application/json
 
{
    "action": "start",
    "serviceTypeId": "uuidUpgradeService",
    "segmentSize": 1000,
    "basePath": "/conf/wknd-shared",
    "interval": 10,
    "mode": "replicate",
    "dryRun": true
}
```

+++

+++Response

```http
HTTP/1.1 200 OK
Date: Wed, 16 Oct 2024 14:34:37 GMT
X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
Content-Type: application/json
Content-Length: 386
 
{
  "jobId": "91af43a6-63ff-45e5-ac7b-06ccf565bdfa",
  "jcr:created": 1729089277309,
  "parameters": {
    "mode": "replicate",
    "dryRun": true,
    "segmentSize": 1000,
    "serviceTypeId": "uuidUpgradeService",
    "action": "start",
    "basePath": "/conf/wknd-shared",
    "topic": "cfm/maintenance",
    "interval": 10,
    "cronSchedule": "*/10 * * * * ?"
  }
}
```

+++

### Obtention de l&#39;état d&#39;un upgrade de contenu {#get-the-status-of-a-content-upgrade}

| Point d’entrée | Type de requête HTTP | Commentaire |
|--- |--- |--- |
| `/libs/dam/cfm/maintenance.json` | `GET` | |
| **Paramètres de requête** | **Valeur**. | |
| action | status | |
| jobId | `<UUID>` | `jobId` renvoyé par l’appel pour démarrer la mise à niveau du contenu. |
| **Détails de la réponse** | **Valeur**. | |
| status | Valeurs JSON | Contient l&#39;état détaillé de la mise à niveau du contenu :<ul><li>Mise à jour après chaque intervalle (secondes).</li><li>L’exécution de `uuidUpgradeService` comporte deux phases :<ol><li>phase-0 pour mettre à niveau les modèles de fragments de contenu</li><li>phase-1 pour mettre à niveau les fragments de contenu</li></ol></li><li>Dans chaque phase, les statistiques sont mises à jour après chaque intervalle.</li><li>&quot;jobStatus&quot; : &quot;COMPLETED&quot; marque la fin de la mise à niveau.</li><li>Les autres valeurs d’état sont explicites.</li></ul> |

### Exemple de demande d’état de mise à niveau de contenu {#example-content-upgrade-status-request}

+++Request

```http
GET http://localhost:4502/libs/dam/cfm/maintenance.json?action=status&jobId=91af43a6-63ff-45e5-ac7b-06ccf565bdfa
Authorization: _REPLACE_WITH_VALID_AUTH_
Accept: application/json
```

+++

+++Response

```http
HTTP/1.1 200 OK
Date: Wed, 16 Oct 2024 14:35:51 GMT
X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
Content-Type: application/json
Content-Length: 1116
 
{
  "jobId": "91af43a6-63ff-45e5-ac7b-06ccf565bdfa",
  "jcr:created": 1729089277309,
  "eventProcessed": 1,
  "parameters": {
    "mode": "replicate",
    "dryRun": true,
    "segmentSize": 1000,
    "serviceTypeId": "uuidUpgradeService",
    "action": "start",
    "confPath": "/conf/wknd-shared",
    "topic": "cfm/uuid-migration",
    "interval": 10,
    "cronSchedule": "*/10 * * * * ?"
  },
  "status": {
    "jobStatus": "COMPLETED",
    "lastModified": 1729089310301,
    "currentPhaseIndex": 1,
    "phases": {
      "phase-0": {
        "bookmark": 1727183332520,
        "stats": {
          "successCount": 2,
          "skippedCount": 1,
          "errorCount": 0
        },
        "name": "modelUpgrade",
        "lastModified": 1729089290040,
        "isCompleted": true
      },
      "phase-1": {
        "bookmark": 1727183347990,
        "stats": {
          "successCount": 29,
          "skippedCount": 0,
          "errorCount": 1
        },
        "name": "cfUpgrade",
        "lastModified": 1729089310298,
        "isCompleted": true
      }
    }
  }
}
```

+++

+++Exemples de fichiers journaux

Outre l’état d’une mise à niveau de contenu en cours d’exécution obtenue à partir du point de terminaison HTTP, les journaux d’AEM fournissent des informations détaillées sur la progression au niveau du contenu. Par exemple :

```xml
#Successful model upgrade
com.adobe.cq.dam.cfm.impl.servicing.uuid.* Phase phase-0: resource: /conf/wknd-shared/settings/dam/cfm/models/article , status: SUCCESS, skips: [], errors: []
 
#Successful content fragment upgrade
com.adobe.cq.dam.cfm.impl.servicing.uuid.* Phase phase-1: resource: /content/dam/wknd-shared/en/magazine/san-diego-surf-spots/san-diego-surfspots , status: SUCCESS, skips: [], errors: []
 
#Unsuccessful/Skipped model upgrade
com.adobe.cq.dam.cfm.impl.servicing.uuid.* Phase phase-0: resource: /conf/wknd-shared/settings/dam/cfm/models/adventure , status: SKIPPED, skips: [Model: '/conf/wknd-shared/settings/dam/cfm/models/adventure', no upgradeable fields found], errors: []
 
#Unsuccessful content fragment upgrade
com.adobe.cq.dam.cfm.impl.servicing.uuid.* Phase phase-1: resource: /content/dam/wknd-shared/en/magazine/western-australia/western-australia-by-camper-van , status: FAILED, skips: [], errors: [Path '/content/dam/wknd-shared/en/magazine/western-australia/western-australia-by-camper-van', Variation: 'master' Field 'featuredImage', Value '/content/dam/wknd-shared/en/magazine/western-australia/adobestock_156407519.jpeg' is invalid; will not upgrade this field.] 
```

En outre, après le traitement de chaque segment (lot) de fragments de contenu et de modèles, un état cumulé est consigné, résumant la progression jusqu’à présent. Par exemple :

```xml
com.adobe.cq.dam.cfm.impl.servicing.PhaseChainProcessor Phase phase-x, processed a segment, stats: {successCount=29, skippedCount=0, errorCount=1}
```

+++

### Abandon d&#39;une mise à niveau de contenu {#abort-a-content-upgrade}

>[!CAUTION]
>
>Abandon d&#39;une mise à niveau de contenu (il ne s&#39;agit pas d&#39;une mise à niveau différée) :
>
>* ne rétablit pas les modifications déjà effectuées
>* peut laisser votre contenu dans un état mixte.
>
>Utilisez cette action avec précaution.

| Point d’entrée | Type de requête HTTP | Commentaire |
|--- |--- |--- |
| `/libs/dam/cfm/maintenance.json` | `POST` | |
| **Paramètres de requête** | **Valeur**. | |
| action | abort | |
| jobId | `<UUID>` | `jobId` renvoyé par l’appel pour démarrer la mise à niveau du contenu. |
| **Détails de la réponse** | **Valeur**. | |
| status | Valeurs JSON | Contient l&#39;état détaillé de la mise à niveau du contenu :<ul><li>Le statut à noter est &quot;jobStatus&quot;: &quot;ABORTED&quot;.<br>Après une action d’abandon, les segments de données en attente ne seront pas traités.</li><li>Si jobStatus est &quot;COMPLETED&quot; avant un abandon, l’appel n’a aucun effet.</li></ul> |

### Exemple d’abandon d’une demande de mise à niveau de contenu {#example-abort-content-upgrade-request}

+++Request

```http
POST http://localhost:4502/libs/dam/cfm/maintenance.json
Content-Type: application/json
Authorization: Basic YWRtaW46YWRtaW4=
Accept: application/json
 
{
    "action": "abort",
    "jobId": "b1dbf6f9-5f59-4007-b631-01b63cd17807"
    "mode": "replicate",
}
```

+++

+++Response

```http
HTTP/1.1 200 OK
Date: Wed, 16 Oct 2024 14:39:03 GMT
 
{
  "jobId": "b1dbf6f9-5f59-4007-b631-01b63cd17807",
   ...
  "eventProcessed": 2,
  "parameters": {
    ...
    "abort": true,
    ...
  },
  "status": {
     "jobStatus": "ABORTED",
    ...
  }
}
```

+++
