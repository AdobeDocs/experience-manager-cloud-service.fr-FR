---
title: Tâches de maintenance dans AEM en tant que service Cloud
description: 'Tâches de maintenance dans AEM en tant que service Cloud '
translation-type: tm+mt
source-git-commit: 8fba31951276d7e0de1f3bd079e42e431edaff4e
workflow-type: tm+mt
source-wordcount: '892'
ht-degree: 2%

---


# Tâches de maintenance dans AEM en tant que service Cloud

Les Tâches de maintenance sont des processus qui s’exécutent selon un calendrier afin d’optimiser le référentiel. Avec AEM en tant que service Cloud, la nécessité pour les clients de configurer les propriétés opérationnelles des tâches de maintenance est minimale. Les clients peuvent concentrer leurs ressources sur les préoccupations au niveau de l&#39;application, laissant les opérations d&#39;infrastructure à Adobe.

Pour plus d&#39;informations sur les tâches de maintenance, consultez les pages suivantes :

* [Guide de maintenance d’AEM](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html)
* [Tâches de maintenance du Tableau de bord d&#39;exploitation](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/operations-dashboard.html#AutomatedMaintenanceTasks)

## Configuration des tâches de maintenance

Dans les versions précédentes d’AEM, vous pouviez configurer des tâches de maintenance à l’aide de la carte de maintenance (Outils > Opérations > Maintenance). Pour AEM en tant que service Cloud, la carte de maintenance n’est plus disponible. Les configurations doivent donc être validées pour le contrôle de code source et déployées à l’aide de Cloud Manager. Adobe va gérer les tâches de maintenance qui n&#39;exigent pas de décisions de la part des clients (par exemple, la collecte des déchets de la banque de données) tandis que d&#39;autres tâches de maintenance peuvent être configurées par le client (voir le tableau ci-dessous).

>[!CAUTION]
>
>Adobe se réserve le droit de remplacer les paramètres de configuration de la tâche de maintenance d’un client afin d’atténuer des problèmes tels que la dégradation des performances.

Le tableau suivant illustre les tâches de maintenance disponibles au moment de la publication d’AEM as a Cloud Service.

| Tâche de maintenance | À qui appartient la configuration | Comment configurer (facultatif) |
|---|---|---|
| Collecte des déchets de la banque de données | Adobe | S/O - Entièrement détenu par Adobe |
| Purge de version | Adobe | Entièrement détenu par Adobe, mais à l&#39;avenir, les clients pourront configurer certains paramètres. |
| Purge du journal d&#39;audit | Adobe | Entièrement détenu par Adobe, mais à l&#39;avenir, les clients pourront configurer certains paramètres. |
| Nettoyage des binaires Lucene | Adobe | Inutilisé et par conséquent désactivé par Adobe. |
| Purger les Tâches ad hoc | Client | Ça doit être fait en github. <br> Remplacez le noeud de configuration de la fenêtre de maintenance sous `/libs` et `/apps` par `/conf/global/settings/granite/operations/maintenance/granite_weekly` ou `granite_daily`. Consultez le tableau de la fenêtre de maintenance ci-dessous pour en savoir plus sur la configuration. <br> Activez la tâche de maintenance en ajoutant un autre noeud sous le noeud ci-dessus (nommez-le `granite_TaskPurgeTask`) avec les propriétés appropriées. <br> Configurez les propriétés OSGI. Consultez la documentation de la Tâche de maintenance [AEM 6.5.](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |
| Purge du processus | Client | Ça doit être fait en github. <br> Remplacez le noeud de configuration de la fenêtre de maintenance sous `/libs` et `/apps` par `/conf/global/settings/granite/operations/maintenance/granite_weekly` ou `granite_daily`. Consultez le tableau de la fenêtre de maintenance ci-dessous pour en savoir plus sur la configuration. <br> Activez la tâche de maintenance en ajoutant un autre noeud sous le noeud ci-dessus (nommez-le `granite_WorkflowPurgeTask`) avec les propriétés appropriées. <br> Configuration des propriétés OSGI Voir la documentation de la Tâche de maintenance [AEM 6.5](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |
| Purge du projet | Client | Ça doit être fait en github. <br> Remplacez le noeud de configuration de la fenêtre de maintenance sous `/libs` et `/apps` par `/conf/global/settings/granite/operations/maintenance/granite_weekly` ou `granite_daily`. Consultez le tableau de la fenêtre de maintenance ci-dessous pour en savoir plus sur la configuration. <br> Activez la tâche de maintenance en ajoutant un noeud sous le noeud ci-dessus (nommez-le `granite_ProjectPurgeTask`) avec les propriétés appropriées. <br> Configuration des propriétés OSGI Voir la documentation de la Tâche de maintenance [AEM 6.5](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |

Les clients peuvent planifier l&#39;exécution de chacune des tâches de maintenance Purger le flux de travail, Purger les Tâches ad hoc et Purger le projet pendant les périodes de maintenance quotidienne, hebdomadaire ou mensuelle. Ces configurations doivent être modifiées directement dans le contrôle de code source. Le tableau ci-dessous décrit les paramètres de configuration disponibles pour chaque fenêtre.

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
    <td>Définition de noeud JCR</td>
    <td><code>/conf/global/settings/granite/operations/maintenance/granite_daily </code> (qui remplace le noeud dans <code>/apps</code> et <code>/libs</code>)</td>
    <td>Voir l'exemple de code 1 ci-dessous</td>
   <td>
    <ul>
    <li><strong>windowSchedule</strong> = daily (cette valeur ne doit pas être modifiée)</li>
    <li><strong>windowStartTime</strong> = HH:MM utilisant comme horloge de 24 heures. Définit le moment où les Tâches de maintenance associées à la fenêtre de maintenance quotidienne doivent commencer à s'exécuter.</li>
    <li><strong>windowEndTime</strong> = HH:MM utilisant comme horloge de 24 heures. Définit quand les Tâches de maintenance associées à la fenêtre Maintenance quotidienne doivent cesser d'être exécutées si elles ne sont pas encore terminées.</li>
    </ul> </td> 
  </tr>
  <tr>
    <td>Hebdomadaire</td>
    <td>Client</td>
    <td>Définition de noeud JCR</td>
    <td><code>/conf/global/settings/granite/operations/maintenance/granite_weekly</code> (qui remplace le noeud dans <code>/apps</code> et <code>/libs</code>)</td>
    <td>Voir l'exemple de code 2 ci-dessous</td>
     <td>
    <ul>
    <li><strong>windowSchedule</strong> = hebdomadaire (cette valeur ne doit pas être modifiée)</li>
    <li><strong>windowStartTime</strong> = HH:MM utilisant comme horloge de 24 heures. Définit le moment où les Tâches de maintenance associées à la fenêtre de maintenance hebdomadaire doivent commencer à s'exécuter.</li>
    <li><strong>windowEndTime</strong> = HH:MM utilisant comme horloge de 24 heures. Définit quand les Tâches de maintenance associées à la fenêtre de maintenance hebdomadaire doivent cesser d'être exécutées si elles ne sont pas encore terminées.</li>
    <li><strong>windowScheduleWeekdays = Tableau de 2 valeurs comprises entre 1 et 7. par ex. [5,5].</strong> La première valeur du tableau est le jour de début de la planification de la tâche et la seconde est le jour de fin de l'arrêt de la tâche. L’heure exacte du début et de la fin est régie par windowStartTime et windowEndTime, respectivement.</li>
    </ul> </td> 
  </tr>
  <tr>
    <td>Mensuel</td>
    <td>Client</td>
    <td>Définition de noeud JCR</td>
    <td><code>/conf/global/settings/granite/operations/maintenance/granite_monthly</code> (qui remplace le noeud dans <code>/apps</code> et <code>/libs</code>)</td>
    <td>Voir l'exemple de code 3 ci-dessous</td>
     <td>
    <ul>
    <li><strong>windowSchedule</strong> = daily (cette valeur ne doit pas être modifiée)</li>
    <li><strong>windowStartTime</strong> = HH:MM utilisant comme horloge de 24 heures. Définit le moment où les Tâches de maintenance associées à la fenêtre de maintenance mensuelle doivent commencer à s'exécuter.</li>
    <li><strong>windowEndTime</strong> = HH:MM utilisant comme horloge de 24 heures. Définit quand les Tâches de maintenance associées à la fenêtre de maintenance mensuelle doivent cesser d'être exécutées si elles ne sont pas encore terminées.</li>
    <li><strong>windowScheduleWeekdays = Tableau de 2 valeurs comprises entre 1 et 7. par ex. [5,5].</strong> La première valeur du tableau est le jour de début de la planification de la tâche et la seconde est le jour de fin de l'arrêt de la tâche. L’heure exacte du début et de la fin est régie par windowStartTime et windowEndTime, respectivement.</li>
    <li><strong>windowFirstLastStartDay - 0/1</strong> 0 pour planifier la première semaine du mois ou 1 pour planifier la dernière semaine du mois. L’absence d’une valeur planifierait efficacement les tâches tous les jours, comme régi par windowScheduleWeekdays tous les mois.</li>
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
