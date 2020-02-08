---
title: Tâches de maintenance dans AEM en tant que service Cloud
description: 'Tâches de maintenance dans AEM en tant que service Cloud '
translation-type: tm+mt
source-git-commit: 8fba31951276d7e0de1f3bd079e42e431edaff4e

---


# Tâches de maintenance dans AEM en tant que service Cloud

Les tâches de maintenance sont des processus qui s’exécutent selon un calendrier afin d’optimiser le référentiel. Avec AEM en tant que service Cloud, la configuration des propriétés opérationnelles des tâches de maintenance par les clients est minimale. Les clients peuvent concentrer leurs ressources sur les préoccupations au niveau de l’application, laissant les opérations d’infrastructure à Adobe.

Pour plus d’informations sur les tâches de maintenance, voir les pages suivantes :

* [Guide de maintenance AEM](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html)
* [Tâches de maintenance du tableau de bord Opérations](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/operations-dashboard.html#AutomatedMaintenanceTasks)

## Configuration des tâches de maintenance

Dans les versions précédentes d’AEM, vous pouviez configurer les tâches de maintenance à l’aide de la carte de maintenance (Outils > Opérations > Maintenance). Pour AEM en tant que service Cloud, la carte de maintenance n’est plus disponible. Les configurations doivent donc être validées pour le contrôle de code source et déployées à l’aide de Cloud Manager. Adobe gérera les tâches de maintenance qui ne nécessitent pas de décisions de la part des clients (par exemple, la collecte de déchets de banque de données), tandis que d’autres tâches de maintenance peuvent être configurées par le client (voir le tableau ci-dessous).

>[!CAUTION]
>
>Adobe se réserve le droit de remplacer les paramètres de configuration des tâches de maintenance d’un client afin d’atténuer des problèmes tels que la dégradation des performances.

Le tableau suivant illustre les tâches de maintenance disponibles au moment de la publication d’AEM en tant que service Cloud.

| Tâche de maintenance | À qui appartient la configuration | Comment configurer (facultatif) |
|---|---|---|
| Collecte de déchets de la banque de données | Adobe | S/O - Propriété complète d’Adobe |
| Purge de version | Adobe | Entièrement détenue par Adobe, mais à l’avenir, les clients pourront configurer certains paramètres. |
| Purge du journal d&#39;audit | Adobe | Entièrement détenue par Adobe, mais à l’avenir, les clients pourront configurer certains paramètres. |
| Nettoyage des binaires Lucene | Adobe | Inutilisé et par conséquent désactivé par Adobe. |
| Purge de tâche ad hoc | Client | Ça doit être fait en github. <br> Remplacez le noeud de configuration de la fenêtre de maintenance sous `/libs` et `/apps` par `/conf/global/settings/granite/operations/maintenance/granite_weekly` ou `granite_daily`. Voir le tableau de la fenêtre de maintenance ci-dessous pour en savoir plus sur la configuration. <br> Activez la tâche de maintenance en ajoutant un autre noeud sous le noeud ci-dessus (nommez-le `granite_TaskPurgeTask`) avec les propriétés appropriées. <br> Configuration des propriétés OSGI reportez-vous à la documentation de la tâche de maintenance [AEM 6.5](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |
| Purge du processus | Client | Ça doit être fait en github. <br> Remplacez le noeud de configuration de la fenêtre de maintenance sous `/libs` et `/apps` par `/conf/global/settings/granite/operations/maintenance/granite_weekly` ou `granite_daily`. Voir le tableau de la fenêtre de maintenance ci-dessous pour en savoir plus sur la configuration. <br> Activez la tâche de maintenance en ajoutant un autre noeud sous le noeud ci-dessus (nommez-le `granite_WorkflowPurgeTask`) avec les propriétés appropriées. <br> Configuration des propriétés OSGI reportez-vous à la documentation de la tâche de maintenance [AEM 6.5](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |
| Purge du projet | Client | Ça doit être fait en github. <br> Remplacez le noeud de configuration de la fenêtre de maintenance sous `/libs` et `/apps` par `/conf/global/settings/granite/operations/maintenance/granite_weekly` ou `granite_daily`. Voir le tableau de la fenêtre de maintenance ci-dessous pour en savoir plus sur la configuration. <br> Activez la tâche de maintenance en ajoutant un noeud sous le noeud ci-dessus (nommez-le `granite_ProjectPurgeTask`) avec les propriétés appropriées. <br> Configuration des propriétés OSGI reportez-vous à la documentation [AEM 6.5 Maintenance Task](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |

Les clients peuvent programmer l’exécution de chacune des tâches de purge de flux de travail, de purge de tâche ad hoc et de maintenance de purge de projet pendant les fenêtres de maintenance quotidiennes, hebdomadaires ou mensuelles. Ces configurations doivent être modifiées directement dans le contrôle de code source. Le tableau ci-dessous décrit les paramètres de configuration disponibles pour chaque fenêtre.

<table>
  <tr>
    <th>Configuration de la fenêtre de maintenance</th>
    <th>À qui appartient la configuration</th>
    <th>Type de configuration</th>
    <th>Emplacement</th>
    <th>Exemple</th>
    <th>Paramètres</th>
  </tr>
  <tr>
    <td>Quotidien</td>
    <td>Client</td>
    <td>Définition du noeud JCR</td>
    <td><code>/conf/global/settings/granite/operations/maintenance/granite_daily </code> (qui remplace le noeud dans <code>/apps</code> et <code>/libs</code>)</td>
    <td>Voir l'exemple de code 1 ci-dessous</td>
   <td>
    <ul>
    <li><strong>windowSchedule</strong> = daily (cette valeur ne doit pas être modifiée)</li>
    <li><strong>windowStartTime</strong> = HH:MM utilisant comme horloge de 24 heures. Définit le moment où les tâches de maintenance associées à la fenêtre de maintenance quotidienne doivent commencer à être exécutées.</li>
    <li><strong>windowEndTime</strong> = HH:MM utilisant comme horloge 24 heures. Définit le moment où les tâches de maintenance associées à la fenêtre Maintenance quotidienne doivent cesser de s'exécuter si elles ne sont pas encore terminées.</li>
    </ul> </td> 
  </tr>
  <tr>
    <td>Hebdomadaire</td>
    <td>Client</td>
    <td>Définition du noeud JCR</td>
    <td><code>/conf/global/settings/granite/operations/maintenance/granite_weekly</code> (qui remplace le noeud dans <code>/apps</code> et <code>/libs</code>)</td>
    <td>Voir l'exemple de code 2 ci-dessous</td>
     <td>
    <ul>
    <li><strong>windowSchedule</strong> = hebdomadaire (cette valeur ne doit pas être modifiée)</li>
    <li><strong>windowStartTime</strong> = HH:MM utilisant comme horloge de 24 heures. Définit le moment où les tâches de maintenance associées à la fenêtre de maintenance hebdomadaire doivent commencer à être exécutées.</li>
    <li><strong>windowEndTime</strong> = HH:MM utilisant comme horloge 24 heures. Définit le moment où les tâches de maintenance associées à la fenêtre de maintenance hebdomadaire doivent cesser de s'exécuter si elles ne sont pas encore terminées.</li>
    <li><strong>windowScheduleWeekdays = Tableau de 2 valeurs de 1 à 7. p. ex. [5,5].</strong> La première valeur du tableau est le jour de début de la planification de la tâche et la seconde est le jour de fin de l’arrêt de la tâche. L’heure exacte du début et de la fin est gouvernée respectivement par windowStartTime et windowEndTime.</li>
    </ul> </td> 
  </tr>
  <tr>
    <td>Mensuel</td>
    <td>Client</td>
    <td>Définition du noeud JCR</td>
    <td><code>/conf/global/settings/granite/operations/maintenance/granite_monthly</code> (qui remplace le noeud dans <code>/apps</code> et <code>/libs</code>)</td>
    <td>Voir l'exemple de code 3 ci-dessous</td>
     <td>
    <ul>
    <li><strong>windowSchedule</strong> = daily (cette valeur ne doit pas être modifiée)</li>
    <li><strong>windowStartTime</strong> = HH:MM utilisant comme horloge de 24 heures. Définit le moment où les tâches de maintenance associées à la fenêtre de maintenance mensuelle doivent commencer à être exécutées.</li>
    <li><strong>windowEndTime</strong> = HH:MM utilisant comme horloge 24 heures. Définit le moment où les tâches de maintenance associées à la fenêtre de maintenance mensuelle doivent cesser de s'exécuter si elles ne sont pas encore terminées.</li>
    <li><strong>windowScheduleWeekdays = Tableau de 2 valeurs de 1 à 7. p. ex. [5,5].</strong> La première valeur du tableau est le jour de début de la planification de la tâche et la seconde est le jour de fin de l’arrêt de la tâche. L’heure exacte du début et de la fin est gouvernée respectivement par windowStartTime et windowEndTime.</li>
    <li><strong>windowFirstLastStartDay - 0/1</strong> 0 pour programmer la première semaine du mois ou 1 pour programmer la dernière semaine du mois. L’absence d’une valeur planifierait efficacement des tâches chaque jour, comme le régit windowScheduleWeekdays tous les mois.</li>
    </ul> </td> 
  </tr>
</table>

Exemple de code 1

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

Exemple de code 2

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

Exemple de code 3

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
