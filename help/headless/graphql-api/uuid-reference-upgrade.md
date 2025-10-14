---
title: Mettre à niveau vos fragments de contenu pour les références UUID
description: Découvrez comment mettre à niveau vos fragments de contenu pour optimiser les références UUID dans Adobe Experience Manager as a Cloud Service pour la diffusion de contenu découplé.
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
exl-id: 004d1340-8e3a-4e9a-82dc-fa013cea45a7
source-git-commit: fdfe0291ca190cfddf3bed363a8c2271a65593a1
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 2%

---

# Mettre à niveau vos fragments de contenu pour les références UUID {#upgrade-content-fragments-for-UUID-references}

Pour optimiser la stabilité de vos filtres GraphQL, vous pouvez mettre à niveau le contenu et les références aux fragments dans vos fragments de contenu afin qu’ils utilisent des identifiants universels uniques (UUID).

À l’origine, les modèles de fragment de contenu fournissaient les types de données **Référence de contenu** et **Référence de fragment**. Ces deux références utilisent un chemin pour pointer vers la ressource référencée. Ce chemin peut devenir obsolète si la ressource est déplacée. Bien que de telles références soient plus que suffisantes dans la plupart des scénarios, les modèles de fragment de contenu ont été étendus pour fournir également des références basées sur un UUID :

* **Référence de contenu (UUID)**
* **Référence de fragment (UUID)**.

Ces nouveaux types de référence peuvent être utilisés dans les nouveaux modèles de fragment de contenu et fragments, ainsi que pour étendre les instances existantes.

Pour mettre à niveau des fragments de contenu et des modèles existants, vous pouvez exécuter la procédure décrite ici.

>[!CAUTION]
>
>Avant d’exécuter la procédure de mise à niveau, vous devez toujours [exécuter une exécution d’essai](#execute-a-dry-run) pour mettre en évidence les problèmes potentiels liés à votre contenu.

## Éléments mis à niveau {#what-is-upgraded}

Les mises à jour suivantes ont été effectuées :

* Champs des types de données :
   * Les **Référence de contenu** sont converties en **Référence de contenu (UUID)**
   * Les **Référence de fragment** sont converties en **Référence de fragment (UUID)**
* Les valeurs des références basées sur le chemin contenues dans ces champs sont remplacées par les UUID correspondants

>[!NOTE]
>
>Après la mise à niveau, les deux types de données sont toujours disponibles dans l’éditeur de modèle de fragment de contenu. Vous pouvez créer des champs basés sur les deux types (bien qu’il soit prévu que vous utilisiez les types basés sur l’UUID) et relancer la mise à niveau si nécessaire.

## Éléments NON mis à niveau {#what-is-not-upgraded}

Les références suivantes ne sont pas mises à niveau :

* Références de page - Les UUID ne sont pas encore pris en charge
* Toute référence non valide ; par exemple, où la cible du chemin d’accès au fragment de contenu ou à la ressource n’existe pas

   * Les références non valides ne sont pas mises à niveau, comme si le chemin d’accès au fragment de contenu ou à la ressource n’était pas valide. Il n’existe donc pas d’UUID correspondant à attribuer. La référence d’origine reste inchangée.

   * Utilisez une [exécution d’essai](#execute-a-dry-run) pour détecter toute référence non valide.

  >[!NOTE]
  >
  >Étant non valides, ils ne sont pas utilisables, quelle que soit la mise à niveau.

## Quand ne pas mettre à niveau {#when-you-should-not-upgrade}

Ne pas mettre à niveau :

* Lorsque l’un de vos fragments de contenu utilise des références de page, car les UUID ne sont pas encore pris en charge pour les références de page.

## Limites des références UUID {#limitations-of-uuid-references}

Actuellement, les restrictions suivantes s’appliquent lors de l’utilisation de références basées sur un UUID :

* Modèles

   * Les nouveaux modèles de fragment de contenu avec les champs UUID de fragment de contenu ou UUID de référence de contenu ne peuvent pas être créés via OpenAPI.
   * Le champ `id` des modèles n’a pas été remplacé par basé sur l’UUID. Il utilise le chemin décodé base64 du modèle. Les modèles ne peuvent pas être déplacés. Par conséquent, cette valeur est toujours stable.

* Ressources

   * Lors de la création d’un fragment de contenu par le biais d’OpenAPI, les types de champ `fragment-reference` ou `content-reference` doivent être utilisés pour spécifier respectivement les références à un fragment ou à une ressource, même lors de la définition de la valeur d’un champ de référence basé sur UUID.

## Planification de la mise à niveau {#upgrade-planning}

Avant d’exécuter la mise à niveau, effectuez quelques étapes de préparation.

### Exécution d’un essai {#execute-a-dry-run}

Il est recommandé *chaque fois que vous mettez à niveau votre contenu* d’effectuer d’abord une exécution d’essai. Vous créez ainsi des fichiers journaux avec des entrées qui mettent en évidence les problèmes potentiels :

* Références non valides
* Références de page

Exécutez la mise à niveau du contenu en mode `dryRun` pour :

* identifiez les références non valides en les répertoriant dans les fichiers journaux
Vous pouvez ensuite corriger ces références avant d’exécuter la mise à niveau réelle du contenu.
* identifiez les références de page, en les répertoriant dans les fichiers journaux
Lorsque des références de page sont détectées, vous [&#x200B; devez pas exécuter la mise à niveau du contenu](#when-you-should-not-upgrade).


### Application d’un gel du contenu {#enforce-a-content-freeze}

L’exécution de la mise à niveau du contenu doit être planifiée pendant une période de gel du contenu.

La durée du gel du contenu dépend du volume de fragments de contenu mis à niveau. Par conséquent, la mise à niveau peut prendre de quelques minutes à quelques heures, et dépend également des paramètres utilisés lors du démarrage de la mise à niveau du contenu.

## Exécution de la mise à niveau du contenu {#running-the-content-upgrade}

La mise à niveau du contenu peut être gérée à l’aide du point d’entrée : `/libs/dam/cfm/maintenance.json`

>[!NOTE]
>
>Votre compte a besoin du rôle `Administrator` pour accéder au point d’entrée.

### Démarrer une mise à niveau du contenu {#start-a-content-upgrade}

| Point d’entrée | Type de requête HTTP | Commentaire |
|--- |--- |--- |
| `/libs/dam/cfm/maintenance.json` | `POST` | |
| **Paramètres de requête** | **Valeur**. | |
| action | `start` | |
| serviceTypeId | `uuidUpgradeService` | L’identifiant du type de service (prédéfini, valeur fixe). |
|  segmentSize | `1000` | Nombre de fragments de contenu ou de modèles qui seront mis à niveau dans un segment (lot). |
| basePath | `/conf` | Spécifiez l’une des options suivantes :<ul><li>`/conf` racine pour mettre à niveau toutes les configurations AEM</li><li>un chemin de configuration AEM sélectionné. pour lequel la mise à niveau du contenu est exécutée<br>Par exemple : `/conf/wknd-shared` ne met à niveau que l’`wknd-shared` à client unique</li></ul> |
| intervalle | `10` | Intervalle en secondes, au delà duquel le segment suivant de fragments de contenu ou de modèles est mis à niveau. |
| mode | `replicate`, `noReplicate` | <ul><li>`replicate` : reproduit le même traitement sur toutes les instances de publication AEM.</li><li>`noReplicate` : exécute le traitement uniquement sur les instances d’auteur AEM.</li></ul> |
| dryRun |  `true`, `false` | <ul><li>`false` : simulez la mise à niveau du contenu, sans enregistrer les modifications du contenu</li><li>`true` : effectuez la mise à niveau du contenu et enregistrez les modifications du contenu</li></ul> |
| **Détails de la réponse** | **Valeur**. | |
| jobId | `UUID` |  Identifiant de la tâche qui exécute la mise à niveau du contenu.<ul><li>Cet identifiant est requis dans tous les appels suivants liés à cette exécution.</li><li>Si la valeur `mode` est définie sur `replicate`, l’exécution sur les instances de publication AEM doit également se faire sous la même `jobId`.</li></ul> |
| Paramètres | Paramètres de mise à niveau du contenu | Il s’agit notamment des paramètres initiaux fournis pour démarrer la mise à niveau du contenu, et de certaines valeurs par défaut internes. |


### Exemple de demande de mise à niveau de contenu {#example-content-upgrade-request}

+++Demande

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

+++Réponse

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

### Obtention du statut d’une mise à niveau de contenu {#get-the-status-of-a-content-upgrade}

| Point d’entrée | Type de requête HTTP | Commentaire |
|--- |--- |--- |
| `/libs/dam/cfm/maintenance.json` | `GET` | |
| **Paramètres de requête** | **Valeur**. | |
| action | status | |
| jobId | `<UUID>` | `jobId` renvoyé par l’appel pour démarrer la mise à niveau du contenu. |
| **Détails de la réponse** | **Valeur**. | |
| status | Valeurs JSON | Contient le statut détaillé de la mise à niveau du contenu :<ul><li>Mis à jour après chaque intervalle (secondes).</li><li>L&#39;exécution d&#39;un `uuidUpgradeService` se divise en deux phases :<ol><li>phase 0 de mise à niveau des modèles de fragment de contenu</li><li>phase 1 de mise à niveau des fragments de contenu</li></ol></li><li>Dans chaque phase, les statistiques sont mises à jour après chaque intervalle.</li><li>« jobStatus » : « COMPLETED » marque la mise à niveau comme terminée avec succès.</li><li>Les autres valeurs de statut s’expliquent d’elles-mêmes.</li></ul> |

### Exemple de demande de statut de mise à niveau du contenu {#example-content-upgrade-status-request}

+++Demande

```http
GET http://localhost:4502/libs/dam/cfm/maintenance.json?action=status&jobId=91af43a6-63ff-45e5-ac7b-06ccf565bdfa
Authorization: _REPLACE_WITH_VALID_AUTH_
Accept: application/json
```

+++

+++Réponse

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

Outre le statut d’une mise à niveau de contenu en cours d’exécution obtenu à partir du point d’entrée HTTP, les journaux AEM fournissent des informations détaillées sur la progression au niveau du contenu. Par exemple :

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

En outre, après le traitement de chaque segment (lot) de fragments de contenu et de modèles, un statut cumulé est consigné, résumant la progression jusqu’à présent. Par exemple :

```xml
com.adobe.cq.dam.cfm.impl.servicing.PhaseChainProcessor Phase phase-x, processed a segment, stats: {successCount=29, skippedCount=0, errorCount=1}
```

+++

### Abandon d’une mise à niveau de contenu {#abort-a-content-upgrade}

>[!CAUTION]
>
>Abandon d’une mise à niveau de contenu (ce n’est pas un essai) :
>
>* n’annule aucune des modifications déjà apportées.
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
| status | Valeurs JSON | Contient le statut détaillé de la mise à niveau du contenu :<ul><li>Le statut à noter est « jobStatus » : « ABORTED ».<br>Après une action d’abandon, les segments de données en attente ne sont pas traités.</li><li>Si le jobStatus est « COMPLETED » avant un abandon, l&#39;appel n&#39;a aucun effet.</li></ul> |

### Exemple d’abandon d’une demande de mise à niveau du contenu {#example-abort-content-upgrade-request}

+++Demande

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

+++Réponse

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
