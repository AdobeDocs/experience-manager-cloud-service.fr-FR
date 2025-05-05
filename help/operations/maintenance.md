---
title: Tâches de maintenance dans AEM as a Cloud Service
description: Découvrez les tâches de maintenance dans AEM as a Cloud Service et comment les configurer.
exl-id: 5b114f94-be6e-4db4-bad3-d832e4e5a412
feature: Operations
role: Admin
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '2043'
ht-degree: 40%

---


# Tâches de maintenance dans AEM as a Cloud Service {#maintenance-tasks-in-aem-as-a-cloud-service}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_maintenance"
>title="Tâches de maintenance"
>abstract="Les tâches de maintenance sont des processus qui s’exécutent selon un calendrier afin d’optimiser le référentiel. Avec AEM as a Cloud Service, le besoin des clients de configurer les propriétés opérationnelles des tâches de maintenance est minime. Les clients peuvent concentrer leurs ressources sur des préoccupations de niveau application, laissant les opérations d’infrastructure à Adobe."

Les tâches de maintenance sont des processus qui s’exécutent selon un calendrier afin d’optimiser le référentiel. Avec AEM as a Cloud Service, le besoin des clients de configurer les propriétés opérationnelles des tâches de maintenance est minime. Les clients peuvent concentrer leurs ressources sur des préoccupations de niveau application, laissant les opérations d’infrastructure à Adobe.

## Configuration des tâches de maintenance {#maintenance-tasks-configuring}

Dans les versions précédentes d’AEM, vous pouviez configurer les tâches de maintenance à l’aide de la carte de maintenance (Outils > Opérations > Maintenance). Dans AEM as a Cloud Service, la carte de maintenance n’est plus disponible. Les configurations doivent donc être validées pour le contrôle source et déployées à l’aide de Cloud Manager. Adobe gère les tâches de maintenance dont les paramètres ne peuvent pas être configurés par les clients (par exemple, la récupération de l’espace mémoire du magasin de données). D’autres tâches de maintenance peuvent être configurées par les clients, comme décrit dans le tableau ci-dessous.

>[!CAUTION]
>
>Adobe se réserve le droit de remplacer les paramètres de configuration de la tâche de maintenance d’un client ou d’une cliente afin d’atténuer des problèmes tels que la dégradation des performances.

Le tableau suivant illustre les tâches de maintenance disponibles.

<table style="table-layout:auto">
 <tbody>
  <tr>
    <th>Tâche de maintenance</th>
    <th>Qui gère la configuration</th>
    <th>Comment configurer (facultatif)</th>
  </tr>  
  <tr>
    <td>Récupération de l’espace mémoire du magasin de données</td>
    <td>Adobe</td>
    <td>S/O – appartient entièrement à Adobe.</td>
  </td> 
  </tr>
  <tr>
    <td>Purge de version</td>
    <td>Client</td>
    <td>La purge de version est actuellement désactivée par défaut, mais la politique peut être configurée, comme décrit dans la section <a href="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/operations/maintenance#purge_tasks"> Tâches de maintenance de purge de version et de journal d’audit </a>.<br/><br/>La purge sera bientôt activée par défaut et ces valeurs pourront être remplacées.<br>
   </td>
  </td>
  </tr>
  <tr>
    <td>Purge du journal d’audit</td>
    <td>Client</td>
    <td>La purge du journal d’audit est actuellement désactivée par défaut, mais la politique peut être configurée, comme décrit dans la section <a href="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/operations/maintenance#purge_tasks">Tâches de maintenance de purge de version et de purge du journal d’audit</a>.<br/><br/>La purge sera bientôt activée par défaut et ces valeurs pourront être remplacées.<br>
   </td>
   </td>
  </tr>
  <tr>
    <td>Nettoyage des binaires Lucene</td>
    <td>Adobe</td>
    <td>Non utilisée et donc désactivée par Adobe.</td>
  </td>
  </tr>
  <tr>
    <td>Purge des tâches ad hoc</td>
    <td>Client</td>
    <td>
    <p>Doit s’effectuer dans git. Remplacez le nœud de configuration de fenêtre de maintenance prêt à l’emploi sous <code>/libs</code> en créant des propriétés sous le dossier <code>/apps/settings/granite/operations/maintenance/granite_weekly</code>, <code>granite_daily</code> ou <code>granite_monthly</code>.</p>
    <p>Consultez le tableau de fenêtre de maintenance ci-dessous pour en savoir plus sur la configuration. Activez la tâche de maintenance en ajoutant un autre nœud sous le nœud ci-dessus. Nommez-le <code>granite_TaskPurgeTask</code>, avec l’attribut <code>sling:resourceType</code> défini sur <code>granite/operations/components/maintenance/task</code> et l’attribut <code>granite.maintenance.name</code> défini sur <code>TaskPurge</code>. Configurez les propriétés OSGI. Voir <code>com.adobe.granite.taskmanagement.impl.purge.TaskPurgeMaintenanceTask</code> pour la liste des propriétés.</p>
  </td>
  </tr>
    <tr>
    <td>Purge du workflow</td>
    <td>Client</td>
    <td>
    <p>Doit s’effectuer dans git. Remplacez le nœud de configuration de fenêtre de maintenance prêt à l’emploi sous <code>/libs</code> en créant des propriétés sous le dossier <code>/apps/settings/granite/operations/maintenance/granite_weekly</code>, <code>granite_daily</code> ou <code>granite_monthly</code>. Consultez le tableau de fenêtre de maintenance ci-dessous pour en savoir plus sur la configuration.</p>
    <p>Activez la tâche de maintenance en ajoutant un autre nœud sous le nœud ci-dessus (nommez-le <code>granite_WorkflowPurgeTask</code>) avec les propriétés adéquates. Configurez les propriétés OSGI. Consultez la <a href="https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/workflows-administering.html?lang=fr#regular-purging-of-workflow-instances">documentation sur les tâches de maintenance AEM 6.5</a>.</p>
  </td>
  </tr>
  <tr>
    <td>Purge du projet</td>
    <td>Client</td>
    <td>
    <p>Doit s’effectuer dans git. Remplacez le nœud de configuration de fenêtre de maintenance prêt à l’emploi sous <code>/libs</code> en créant des propriétés sous le dossier <code>/apps/settings/granite/operations/maintenance/granite_weekly</code>, <code>granite_daily</code> ou <code>granite_monthly</code>. Consultez le tableau de fenêtre de maintenance ci-dessous pour en savoir plus sur la configuration.</p>
    <p>Activez la tâche de maintenance en ajoutant un autre nœud sous le nœud ci-dessus (nommez-le <code>granite_ProjectPurgeTask</code>) avec les propriétés adéquates. Consultez la liste des <a href="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/deploying/configuring-osgi">propriétés OSGi</a> pour la configuration de purge des projets d’Adobe <b></b> .</p>
  </td>
  </tr>
  </tbody>
</table>

<table style="table-layout:auto">
 <tbody>
  <tr>
    <th>Configuration de la fenêtre de maintenance</th>
    <th>Qui gère la configuration</th>
    <th>Type de configuration</th>
    <th>Paramètres</th>
  </tr>
  <tr>
    <td>Quotidienne</td>
    <td>Client</td>
    <td>Définition de nœud JCR</td>
  <td>
  <p><strong>windowSchedule=daily</strong> (cette valeur ne doit pas être modifiée)</p>
  <p><strong>windowStartTime=HH:MM</strong> dans un format horaire de 24 heures. Définit à quel moment les tâches de maintenance associées à la fenêtre de maintenance quotidienne doivent commencer à s’exécuter.</p>
  <p><strong>windowEndTime=HH:MM</strong> dans un format horaire de 24 heures. Définit à quel moment les tâches de maintenance associées à la fenêtre de maintenance quotidienne doivent arrêter de s’exécuter si elles ne sont pas déjà terminées.</p>
  <p>Une tâche de maintenance ne peut pas être exécutée plusieurs fois pendant ce délai.</p>
  </td> 
  </tr>
  <tr>
    <td>Hebdomadaire</td>
    <td>Client</td>
    <td>Définition de nœud JCR</td>
    <td>
    <p><strong>windowSchedule=weekly</strong> (cette valeur ne doit pas être modifiée)</p>
    <p><strong>windowStartTime=HH:MM</strong> dans un format horaire de 24 heures. Définit à quel moment les tâches de maintenance associées à la fenêtre de maintenance hebdomadaire doivent commencer à s’exécuter.</p>
    <p><strong>windowEndTime=HH:MM</strong> dans un format horaire de 24 heures. Définit à quel moment les tâches de maintenance associées à la fenêtre de maintenance hebdomadaire doivent arrêter de s’exécuter si elles ne sont pas déjà terminées.</p>
    <p>Une tâche de maintenance ne peut pas être exécutée plusieurs fois pendant ce délai.</p>
    <p><strong>windowScheduleWeekdays= tableau de 2 valeurs de 1 à 7 (par exemple, [5,5])</strong> La première valeur du tableau désigne le jour de début planifié du traitement et la seconde le jour de fin où le traitement doit être arrêté. L’heure exacte du début et de la fin est régie par les paramètres windowStartTime et windowEndTime, respectivement.</p>
    </td>
  </tr>
  <tr>
    <td>Mensuel</td>
    <td>Client</td>
    <td>Définition de nœud JCR</td>
    <td>
    <p><strong>windowSchedule=monthly</strong> (cette valeur ne doit pas être modifiée)</p>
    <p><strong>windowStartTime=HH:MM</strong> dans un format horaire de 24 heures. Définit à quel moment les tâches de maintenance associées à la fenêtre de maintenance mensuelle doivent commencer à s’exécuter.</p>
    <p><strong>windowEndTime=HH:MM</strong> dans un format horaire de 24 heures. Définit à quel moment les tâches de maintenance associées à la fenêtre de maintenance mensuelle doivent arrêter de s’exécuter si elles ne sont pas déjà terminées.</p>
    <p>Une tâche de maintenance ne peut pas être exécutée plusieurs fois pendant ce délai.</p>
    <p><strong>windowScheduleWeekdays= tableau de 2 valeurs de 1 à 7 (par exemple, : [5,5])</strong> La première valeur du tableau désigne le jour de début planifié du traitement et la seconde le jour de fin où le traitement doit être arrêté. L’heure exacte du début et de la fin est régie par les paramètres windowStartTime et windowEndTime, respectivement.</p>
    <p><strong>windowFirstLastStartDay= 0/1</strong> 0 pour planifier la première semaine du mois ou 1 pour planifier la dernière semaine du mois. En l’absence de valeur, les tâches sont planifiées le jour régi par le paramètre windowScheduleWeekdays (tous les mois).</p>
    </td>
    </tr>
    </tbody>
</table>

**Emplacements** :

* Quotidien – /apps/settings/granite/operations/maintenance/granite_daily
* Hebdomadaire – /apps/settings/granite/operations/maintenance/granite_weekly
* Mensuel – /apps/settings/granite/operations/maintenance/granite_monthly

**Exemples de code** :

Exemple de code 1 (quotidien)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" 
  xmlns:jcr="http://www.jcp.org/jcr/1.0" 
  jcr:primaryType="sling:Folder"
  sling:configCollectionInherit="true"
  sling:configPropertyInherit="true"
  windowSchedule="daily"
  windowStartTime="03:00"
  windowEndTime="05:00"
 />
```

Exemple de code 2 (hebdomadaire)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" 
   xmlns:jcr="http://www.jcp.org/jcr/1.0"
   jcr:primaryType="sling:Folder"
   sling:configCollectionInherit="true"
   sling:configPropertyInherit="true"
   windowEndTime="15:30"
   windowSchedule="weekly"
   windowScheduleWeekdays="[5,5]"
   windowStartTime="14:30"/>
```

Exemple de code 3 (mensuel)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" 
   xmlns:jcr="http://www.jcp.org/jcr/1.0"
   jcr:primaryType="sling:Folder"
   sling:configCollectionInherit="true"
   sling:configPropertyInherit="true"
   windowEndTime="15:30"
   windowSchedule="monthly"
   windowFirstLastStartDay=0
   windowScheduleWeekdays="[5,5]"
   windowStartTime="14:30"/>
```

## Tâches de maintenance de purge de version et de journaux d’audit {#purge-tasks}

La purge des versions et du journal d’audit réduit la taille du référentiel et, dans certains scénarios, peut améliorer les performances.

>[!NOTE]
>
>Les clients AEM Guides ne doivent pas configurer la purge de version.

### Paramètres par défaut {#defaults}

Actuellement, la purge n’est pas activée par défaut, mais cela changera à l’avenir. Les environnements créés avant l’activation de la purge par défaut auront un seuil plus prudent afin que la purge ne se produise pas de manière inattendue. Consultez les sections Purge de version et Purge du journal d’audit ci-dessous pour plus d’informations sur la politique de purge par défaut.
<!-- Version purging and audit log purging are on by default, with different default values for environments with ids higher than **TBD** versus those with ids lower than that value. -->

<!-- ### Overriding the default values with a new configuration {#override} -->

Les valeurs de purge par défaut peuvent être remplacées en déclarant un fichier de configuration et en le déployant comme décrit ci-dessous.

<!-- The reason for this behavior is to clarify the ambiguity over whether the default purge values would take effect once you remove the declaration. -->

### Application d’une configuration {#configure-purge}

Déclarez un fichier de configuration et déployez-le comme décrit dans les étapes suivantes.

>[!NOTE]
>Une fois que vous avez déployé le nœud de purge de version dans le fichier de configuration, vous devez le conserver déclaré et ne pas le supprimer. Le pipeline de configuration échoue si vous tentez de le faire.
> 
>De même, une fois que vous avez déployé le nœud de purge du journal d’audit dans le fichier de configuration, vous devez le conserver déclaré et ne pas le supprimer.

**1** Créez un fichier nommé `mt.yaml` ou similaire.

**2** Placez le fichier quelque part sous un dossier de niveau supérieur nommé `config` ou similaire, comme décrit sous [Utilisation de pipelines de configuration](/help/operations/config-pipeline.md#folder-structure).

**3** - Déclarez les propriétés dans le fichier de configuration, parmi lesquelles :

* quelques propriétés au-dessus du nœud de données ; voir [Utilisation des pipelines de configuration](/help/operations/config-pipeline.md#common-syntax) pour une description. La valeur de la propriété `kind` doit être *MaintenanceTasks* et la version doit être définie sur *1*.

* un objet de données avec des objets `versionPurge` et `auditLogPurge`.

Consultez les définitions et la syntaxe des objets `versionPurge` et `auditLogPurge` ci-dessous.

Structurez la configuration comme dans l’exemple suivant :

```
kind: "MaintenanceTasks"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  versionPurge:
    maximumVersions: 15
    maximumAgeDays: 20
    paths: ["/content"]
    minimumVersions: 1
    retainLabelledVersions: false
  auditLogPurge:
    rules:
      - replication:
          maximumAgeDays: 15
          contentPath: "/content"
          types: ["Activate", "Deactivate", "Delete", "Test", "Reverse", "Internal Poll"]
      - pages:
          maximumAgeDays: 15
          contentPath: "/content"
          types: ["PageCreated", "PageModified", "PageMoved", "PageDeleted", "VersionCreated", "PageRestored", "PageValid", "PageInvalid"]
      - dam:
          maximumAgeDays: 15
          contentPath: "/content"
          types: ["ASSET_EXPIRING", "METADATA_UPDATED", "ASSET_EXPIRED", "ASSET_REMOVED", "RESTORED", "ASSET_MOVED", "ASSET_VIEWED", "PROJECT_VIEWED", "PUBLISHED_EXTERNAL", "COLLECTION_VIEWED", "VERSIONED", "ADDED_COMMENT", "RENDITION_UPDATED", "ACCEPTED", "DOWNLOADED", "SUBASSET_UPDATED", "SUBASSET_REMOVED", "ASSET_CREATED", "ASSET_SHARED", "RENDITION_REMOVED", "ASSET_PUBLISHED", "ORIGINAL_UPDATED", "RENDITION_DOWNLOADED", "REJECTED"]
```

Gardez à l’esprit que pour que la configuration soit valide :

* toutes les propriétés doivent être définies. Il n’existe aucune valeur par défaut héritée.
* les types (entiers, chaînes, booléens, etc.) dans les tableaux de propriétés ci-dessous doivent être respectés.

**4** - Créez un pipeline de configuration dans Cloud Manager, comme décrit dans l’article [pipeline de configuration](/help/operations/config-pipeline.md#managing-in-cloud-manager).

### Purge de version {#version-purge}

>[!NOTE]
>
>Les clients AEM Guides ne doivent pas configurer la purge de version.

#### Valeurs par défaut de la purge de version {#version-purge-defaults}

<!-- For version purging, environments with an id higher than **TBD** have the following default values: -->

Actuellement, la purge n’est pas activée par défaut, mais cela changera à l’avenir.

Les environnements créés après l’activation de la purge par défaut ont les valeurs par défaut suivantes :

* Les versions de plus de 30 jours sont supprimées.
* Les cinq versions les plus récentes des 30 derniers jours sont conservées.
* Quelle que soit la règle ci-dessus, la version la plus récente (en plus du fichier actuel) est conservée.

<!-- Environments with an id equal or lower than **TBD** will have the following default values: -->

Les valeurs par défaut des environnements créés avant l’activation de la purge par défaut sont répertoriées ci-dessous. Il est toutefois recommandé de réduire ces valeurs afin d’optimiser les performances.

* Les versions de plus de 7 ans sont supprimées.
* Toutes les versions des 7 dernières années sont conservées.
* Au bout de 7 ans, les versions autres que la version la plus récente (en plus du fichier actuel) sont supprimées.

#### Propriétés de purge de version {#version-purge-properties}

Les propriétés autorisées sont répertoriées ci-dessous.

Les colonnes indiquant *par défaut* indiquent les valeurs par défaut dans le futur, lorsque les valeurs par défaut sont appliquées ; *à déterminer* reflète un identifiant d’environnement qui n’est toujours pas déterminé.

| Propriétés | future valeur par défaut pour env>à déterminer | future valeur par défaut pour env&lt;=à déterminer | obligatoire | Type | Valeurs |
|-----------|--------------------------|-------------|-----------|---------------------|-------------|
| chemin(s) d’accès | [« /content »] | [« /content »] | Oui | tableau de chaînes | Indique sous quels chemins d’accès purger les versions lorsque de nouvelles versions sont créées.  Les clients doivent déclarer cette propriété, mais la seule valeur autorisée est « /content ». |
| maximumAgeDays | 30 | 2557 (7 ans + 2 jours bissextiles) | Oui | Entier | Toute version antérieure à la valeur configurée est supprimée. Si la valeur est 0, la purge n’est pas effectuée en fonction de l’âge de la version. |
| maximumVersions | 5 | 0 (pas de limite) | Oui | Entier | Toute version antérieure à la nième version la plus récente est supprimée. Si la valeur est 0, la purge n’est pas effectuée en fonction du nombre de versions. |
| minimumVersion | 1 | 1 | Oui | Entier | Nombre minimum de versions à conserver, quel que soit l’âge. Notez qu’au moins 1 version est toujours conservée ; sa valeur doit être égale ou supérieure à 1. |
| retainLabellingVersioned | false | false | Oui | booléen | Détermine si les versions explicitement étiquetées seront exclues de la purge. Pour une meilleure optimisation du référentiel, il est recommandé de définir cette valeur sur false. |


**Interactions de propriétés**

Les exemples suivants illustrent l’interaction des propriétés lorsqu’elles sont combinées.

Exemple :

```
maximumAgeDays = 30
maximumVersions = 10
minimumVersions = 2
```

S’il existe 11 versions au jour 23, la version la plus ancienne sera purgée la prochaine fois que la tâche de maintenance de purge s’exécutera, puisque la propriété `maximumVersions` est définie sur 10.

S’il existe 5 versions au jour 31, seules 3 seront purgées, car la propriété `minimumVersions` est définie sur 2.

Exemple :

```
maximumAgeDays = 30
maximumVersions = 0
minimumVersions = 1
```

Aucune version de plus de 30 jours ne sera purgée, car la propriété `maximumVersions` est définie sur 0.

Une version de plus de 30 jours sera conservée.

### Purge du journal d’audit {#audit-purge}

#### Valeurs par défaut de la purge du journal d’audit {#audit-purge-defaults}

<!-- For audit log purging, environments with an id higher than **TBD** have the following default values: -->

Actuellement, la purge n’est pas activée par défaut, mais cela changera à l’avenir.

Les environnements créés après l’activation de la purge par défaut ont les valeurs par défaut suivantes :

* Les journaux d’audit de réplication, de gestion des ressources numériques et de page datant de plus de 7 jours sont supprimés.
* Tous les événements possibles sont consignés.

<!-- Environments with an id equal or lower than **TBD** will have the following default values: -->

Les valeurs par défaut des environnements créés avant l’activation de la purge par défaut sont répertoriées ci-dessous. Il est toutefois recommandé de réduire ces valeurs afin d’optimiser les performances.

* Les journaux d’audit de réplication, de gestion des ressources numériques et de pages de plus de 7 ans sont supprimés.
* Tous les événements possibles sont consignés.

>[!NOTE]
>Il est recommandé aux clients qui ont des exigences réglementaires pour produire des journaux d’audit non modifiables de faire appel à des services externes spécialisés.

#### Propriétés de purge du journal d’audit {#audit-purge-properties}

Les propriétés autorisées sont répertoriées ci-dessous.

Les colonnes indiquant *par défaut* indiquent les valeurs par défaut dans le futur, lorsque les valeurs par défaut sont appliquées ; *à déterminer* reflète un identifiant d’environnement qui n’est toujours pas déterminé.


| Propriétés | future valeur par défaut pour env>à déterminer | future valeur par défaut pour env&lt;=à déterminer | obligatoire | Type | Valeurs |
|-----------|--------------------------|-------------|-----------|---------------------|-------------|
| règles | - | - | Oui | Objet | Un ou plusieurs des nœuds suivants : réplication, pages, gestion des ressources numériques. Chacun de ces nœuds définit des règles, avec les propriétés ci-dessous. Toutes les propriétés doivent être déclarées. |
| maximumAgeDays | 7 jours | pour tout, 2557 (7 ans + 2 jours bissextiles) | Oui | integer | Pour la réplication, les pages ou la gestion des ressources numériques : nombre de jours pendant lesquels les journaux d’audit sont conservés. Les journaux d’audit antérieurs à la valeur configurée sont purgés. |
| contentPath | « /content » | « /content » | Oui | Chaîne | Chemin d’accès sous lequel les journaux d’audit seront purgés, pour le type associé. Doit être défini sur « /content ». |
| types | toutes les valeurs | toutes les valeurs | Oui | Tableau de l’énumération | Pour **replication**, les valeurs énumérées sont les suivantes : Activate, Deactivate, Delete, Test, Reverse, Internal Poll. Pour **pages**, les valeurs énumérées sont les suivantes : PageCreated, PageModified, PageMoved, PageDeleted, VersionCreated, PageRestored, PageRolled, PageValid, PageInvalid. Pour **dam**, les valeurs énumérées sont les suivantes : ASSET_EXPIRING, METADATA_UPDATED, ASSET_EXPIRED, ASSET_REMOVED, RESTORED, ASSET_MOVED, ASSET_VIEWED, PROJECT_VIEWED, PUBLISHED_EXTERNAL, COLLECTION_VIEWED, VERSIONED, ADDED_COMMENT, RENDITION_UPDATED, ACCEPTED, DOWNLOADED, SUBASSET_UPDATED, SUBASSET_REMOVED, ASSET_CREATED, ASSET_SHARED, RENDITION_REMOVED, ASSET_PUBLISHED, ORIGINAL_UPDATED, RENDITION_DOWNLOADED, REJETÉ. |
