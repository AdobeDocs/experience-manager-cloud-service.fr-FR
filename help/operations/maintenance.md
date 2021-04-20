---
title: Tâches de maintenance dans AEM as a Cloud Service
description: Tâches de maintenance dans AEM as a Cloud Service
exl-id: 5b114f94-be6e-4db4-bad3-d832e4e5a412
translation-type: tm+mt
source-git-commit: 8adead735a5c3c0a03ee6f81372c1714634932ec
workflow-type: tm+mt
source-wordcount: '1004'
ht-degree: 96%

---

# Tâches de maintenance dans AEM as a Cloud Service

Les tâches de maintenance sont des processus qui s’exécutent selon un calendrier afin d’optimiser le référentiel. Avec AEM as a Cloud Service, le besoin des clients de configurer les propriétés opérationnelles des tâches de maintenance est minime. Les clients peuvent concentrer leurs ressources sur des préoccupations de niveau application, laissant les opérations d’infrastructure à Adobe.

Pour plus d’informations sur les tâches de maintenance, consultez les pages suivantes :

* [Guide de maintenance d’AEM](https://helpx.adobe.com/fr/experience-manager/kb/AEM6-Maintenance-Guide.html)
* [Tâches de maintenance du tableau de bord des opérations](https://helpx.adobe.com/fr/experience-manager/6-5/sites/administering/using/operations-dashboard.html#AutomatedMaintenanceTasks)

## Configuration des tâches de maintenance

Dans les versions précédentes d’AEM, vous pouviez configurer les tâches de maintenance à l’aide de la carte de maintenance (Outils > Opérations > Maintenance). Dans AEM as a Cloud Service, la carte de maintenance n’est plus disponible. Les configurations doivent donc être validées pour le contrôle source et déployées à l’aide de Cloud Manager. Adobe gérera les tâches de maintenance qui n’exigent pas de décisions de la part du client (par exemple, la récupération de l’espace mémoire du magasin de données) tandis que d’autres tâches de maintenance peuvent être configurées par le client (reportez-vous au tableau ci-dessous).

>[!CAUTION]
>
>Adobe se réserve le droit de remplacer les paramètres de configuration de la tâche de maintenance d’un client afin d’atténuer des problèmes tels que la dégradation des performances.

Le tableau suivant illustre les tâches de maintenance disponibles au moment de la diffusion d’AEM as a Cloud Service.

| Tâche de maintenance | Qui gère la configuration | Comment configurer (facultatif) |
|---|---|---|
| Récupération de l’espace mémoire du magasin de données | Adobe | S/O – appartient entièrement à Adobe. |
| Purge de version | Adobe | Gestion entièrement réalisée par Adobe, mais à l’avenir, les clients pourront configurer certains paramètres. |
| Purge du journal d’audit | Adobe | Gestion entièrement réalisée par Adobe, mais à l’avenir, les clients pourront configurer certains paramètres. |
| Nettoyage des binaires Lucene | Adobe | Non utilisée et donc désactivée par Adobe. |
| Purge des tâches ad hoc | Client | Doit s’effectuer dans github. <br> Remplacez le nœud de configuration de fenêtre de maintenance prêt à l’emploi sous `/libs` en créant des propriétés sous le dossier `/apps/settings/granite/operations/maintenance/granite_weekly` ou `granite_daily`. Consultez le tableau de fenêtre de maintenance ci-dessous pour en savoir plus sur la configuration. <br> Activez la tâche de maintenance en ajoutant un autre nœud sous le nœud ci-dessus (nommez-le `granite_TaskPurgeTask`) avec les propriétés adéquates. <br> Configurez les propriétés OSGI. Consultez la [documentation sur les tâches de maintenance AEM 6.5](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |
| Purge du workflow | Client | Doit s’effectuer dans github. <br> Remplacez le nœud de configuration de fenêtre de maintenance prêt à l’emploi sous `/libs` en créant des propriétés sous le dossier `/apps/settings/granite/operations/maintenance/granite_weekly` ou `granite_daily`. Consultez le tableau de fenêtre de maintenance ci-dessous pour en savoir plus sur la configuration. <br> Activez la tâche de maintenance en ajoutant un autre nœud sous le nœud ci-dessus (nommez-le `granite_WorkflowPurgeTask`) avec les propriétés adéquates. <br> Configurez les propriétés OSGI. Consultez la [documentation sur les tâches de maintenance AEM 6.5](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |
| Purge du projet | Client | Doit s’effectuer dans github. <br> Remplacez le nœud de configuration de fenêtre de maintenance prêt à l’emploi sous `/libs` en créant des propriétés sous le dossier `/apps/settings/granite/operations/maintenance/granite_weekly` ou `granite_daily`. Consultez le tableau de fenêtre de maintenance ci-dessous pour en savoir plus sur la configuration. <br> Activez la tâche de maintenance en ajoutant un nœud sous le nœud ci-dessus (nommez-le `granite_ProjectPurgeTask`) avec les propriétés adéquates. <br> Configurez les propriétés OSGI. Consultez la [documentation sur les tâches de maintenance AEM 6.5](https://helpx.adobe.com/experience-manager/kb/AEM6-Maintenance-Guide.html) |

Les clients peuvent planifier chacune des tâches de maintenance Purger le workflow, Purger les tâches ad hoc et Purger le projet pour que ces tâches s’exécutent pendant les fenêtres de maintenance quotidienne, hebdomadaire ou mensuelle. Ces configurations doivent être modifiées directement dans le contrôle de code source. Le tableau ci-dessous décrit les paramètres de configuration disponibles pour chaque fenêtre.

<table>
  <tr>
    <th>Configuration de la fenêtre de maintenance</th>
    <th>Qui gère la configuration</th>
    <th>Type de configuration</th>
    <th>Emplacement</th>
    <th>Exemple</th>
    <th>Paramètres</th>
  </tr>
  <tr>
    <td>Quotidienne</td>
    <td>Client</td>
    <td>Définition de nœud JCR</td>
    <td>Voir l’emplacement 1 ci-dessous</td>
    <td>Voir l’exemple de code 1 ci-dessous</td>
  <td>
  <strong>windowSchedule</strong> = daily (cette valeur ne doit pas être modifiée)
  <strong>windowStartTime</strong> = HH:MM dans un format horaire de 24 heures. Définit à quel moment les tâches de maintenance associées à la fenêtre de maintenance quotidienne doivent commencer à s’exécuter.
  <strong>windowEndTime</strong> = HH:MM dans un format horaire de 24 heures. Définit à quel moment les tâches de maintenance associées à la fenêtre de maintenance quotidienne doivent arrêter de s’exécuter si elles ne sont pas déjà terminées.
  </td> 
  </tr>
  <tr>
    <td>Hebdomadaire</td>
    <td>Client</td>
    <td>Définition de nœud JCR</td>
    <td>Voir l'emplacement 2 ci-dessous</td>
    <td>Voir l’exemple de code 2 ci-dessous</td>
    <td>
    <strong>windowSchedule</strong> = hebdomadaire (cette valeur ne doit pas être modifiée)
    <strong>windowStartTime</strong> = HH:MM dans un format horaire de 24 heures. Définit à quel moment les tâches de maintenance associées à la fenêtre de maintenance hebdomadaire doivent commencer à s’exécuter.
    <strong>windowEndTime</strong> = HH:MM dans un format horaire de 24 heures. Définit à quel moment les tâches de maintenance associées à la fenêtre de maintenance hebdomadaire doivent arrêter de s’exécuter si elles ne sont pas déjà terminées.
    <strong>windowScheduleWeekdays = tableau de 2 valeurs comprises entre 1 et 7 (par exemple, [5,5]).</strong> La première valeur du tableau désigne le jour de début planifié de la tâche et la seconde le jour de fin où la tâche doit être arrêtée. L’heure exacte du début et de la fin est régie par les paramètres windowStartTime et windowEndTime, respectivement.
    </td> 
  </tr>
  <tr>
    <td>Mensuel</td>
    <td>Client</td>
    <td>Définition de nœud JCR</td>
    <td>Voir l'emplacement 3 ci-dessous</td>
    <td>Voir l’exemple de code 3 ci-dessous</td>
    <td>
    <strong>windowSchedule</strong> = daily (cette valeur ne doit pas être modifiée)
    <strong>windowStartTime</strong> = HH:MM dans un format horaire de 24 heures. Définit à quel moment les tâches de maintenance associées à la fenêtre de maintenance mensuelle doivent commencer à s’exécuter.
    <strong>windowEndTime</strong> = HH:MM dans un format horaire de 24 heures. Définit à quel moment les tâches de maintenance associées à la fenêtre de maintenance mensuelle doivent arrêter de s’exécuter si elles ne sont pas déjà terminées.
    <strong>windowScheduleWeekdays = tableau de 2 valeurs comprises entre 1 et 7 (par exemple, [5,5]).</strong> La première valeur du tableau désigne le jour de début planifié de la tâche et la seconde le jour de fin où la tâche doit être arrêtée. L’heure exacte du début et de la fin est régie par les paramètres windowStartTime et windowEndTime, respectivement.
    <strong>windowFirstLastStartDay – 0/1</strong> 0 pour planifier la première semaine du mois ou 1 pour planifier la dernière semaine du mois. En l’absence de valeur, les tâches sont planifiées chaque jour, comme régi par le paramètre windowScheduleWeekdays tous les mois.
    </td> 
    </tr>
</table>

Emplacements:

1. /apps/settings/granite/operations/maintenance/granite_daily
2. /apps/settings/granite/operations/maintenance/granite_weekly
3. /apps/settings/granite/operations/maintenance/granite_mensuel

Exemples de code :

Exemple de code 1

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

Exemple de code 2

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

Exemple de code 3

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

| Configuration de la fenêtre de maintenance | Qui gère la configuration | Type de configuration | Emplacement | Exemple | Paramètres |
|---|---|---|---|---|---|
| Quotidienne | Client | Définition de nœud JCR | Voir l&#39;emplacement 2 ci-dessous | Voir l’exemple de code 2 ci-dessous | **** windowSchedule = daily (cette valeur ne doit pas être modifiée). <br> **** windowStartTime = HH:MM dans un format horaire de 24 heures. Définit à quel moment les tâches de maintenance associées à la fenêtre de maintenance quotidienne doivent commencer à s’exécuter. <br> **** windowEndTime = HH:MM dans un format horaire de 24 heures. Définit à quel moment les tâches de maintenance associées à la fenêtre de maintenance quotidienne doivent arrêter de s’exécuter si elles ne sont pas déjà terminées. |
