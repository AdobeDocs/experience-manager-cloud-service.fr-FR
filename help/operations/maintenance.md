---
title: Tâches de maintenance dans AEM as a Cloud Service
description: Tâches de maintenance dans AEM as a Cloud Service
exl-id: 5b114f94-be6e-4db4-bad3-d832e4e5a412
source-git-commit: 8bd001f6f70ce1aa9a63623b3ad68793fa355c9a
workflow-type: tm+mt
source-wordcount: '999'
ht-degree: 100%

---

# Tâches de maintenance dans AEM as a Cloud Service {#maintenance-tasks-in-aem-as-a-cloud-service}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_maintenance"
>title="Tâches de maintenance"
>abstract="Les tâches de maintenance sont des processus qui s’exécutent selon un calendrier afin d’optimiser le référentiel. Avec AEM as a Cloud Service, le besoin des clients de configurer les propriétés opérationnelles des tâches de maintenance est minime. Les clients peuvent concentrer leurs ressources sur des préoccupations de niveau application, laissant les opérations d’infrastructure à Adobe."

Les tâches de maintenance sont des processus qui s’exécutent selon un calendrier afin d’optimiser le référentiel. Avec AEM as a Cloud Service, le besoin des clients de configurer les propriétés opérationnelles des tâches de maintenance est minime. Les clients peuvent concentrer leurs ressources sur des préoccupations de niveau application, laissant les opérations d’infrastructure à Adobe.

## Configuration des tâches de maintenance

Dans les versions précédentes d’AEM, vous pouviez configurer les tâches de maintenance à l’aide de la carte de maintenance (Outils > Opérations > Maintenance). Dans AEM as a Cloud Service, la carte de maintenance n’est plus disponible. Les configurations doivent donc être validées pour le contrôle source et déployées à l’aide de Cloud Manager. Adobe gère les tâches de maintenance dont les paramètres ne peuvent pas être configurés par les clients (par exemple, la récupération de l’espace mémoire du magasin de données, la purge du journal d’audit, la purge des versions). D’autres tâches de maintenance peuvent être configurées par les clients, comme décrit dans le tableau ci-dessous.

>[!CAUTION]
>
>Adobe se réserve le droit de remplacer les paramètres de configuration de la tâche de maintenance d’un client afin d’atténuer des problèmes tels que la dégradation des performances.

Le tableau suivant illustre les tâches de maintenance disponibles au moment de la diffusion d’AEM as a Cloud Service.

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
    <td>Adobe</td>
    <td>Pour que le niveau de création reste performant, les versions plus anciennes de chaque élément de contenu sous le nœud <code>/content</code> du référentiel sont purgés selon le comportement suivant :<br><br> <!--Alexandru: please leave the two line breaks in place, otherwise spacing won't render properly-->
     <ol>
       <li>Les versions de plus de 30 jours sont supprimées</li>
       <li>Les 5 versions les plus récentes des 30 derniers jours sont conservées.</li>
       <li>Quelle que soit la règle ci-dessus, la version la plus récente est conservée.</li>
     </ol><br>REMARQUE : Le comportement décrit ci-dessus est appliqué par défaut pour les nouveaux environnements créés après le 14 mars 2022. Envoyez un ticket d’assistance clientèle si vous avez besoin de paramètres différents.</td>
  </td>
  </tr>
  <tr>
    <td>Purge du journal d’audit</td>
    <td>Adobe</td>
    <td>Pour que le niveau de création reste performant, les journaux d’audit plus anciens de chaque élément de contenu sous le nœud <code>/content</code> du référentiel sont purgés selon le comportement suivant :<br><br> <!-- See above for the two line breaks -->
     <ol>
       <li>Pour le contrôle de réplication, les journaux d’audit datant de plus de 3 jours sont supprimés.</li>
       <li>Pour le contrôle du DAM (Assets), les journaux d’audit datant de plus de 30 jours sont supprimés.</li>
       <li>Pour le contrôle des pages, les journaux de plus de 3 jours sont supprimés.</li>
     </ol><br>REMARQUE : Le comportement décrit ci-dessus est appliqué par défaut pour les nouveaux environnements créés après le 14 mars 2022. Envoyez un ticket d’assistance clientèle si vous avez besoin de paramètres différents.</td>
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
    <p>Doit s’effectuer dans git. Remplacez le nœud de configuration de fenêtre de maintenance prêt à l’emploi sous <code>/libs</code> en créant des propriétés sous le dossier <code>/apps/settings/granite/operations/maintenance/granite_weekly</code> ou <code>granite_daily</code>.</p>
    <p>Consultez le tableau de fenêtre de maintenance ci-dessous pour en savoir plus sur la configuration. Activez la tâche de maintenance en ajoutant un autre nœud sous le nœud ci-dessus (nommez-le <code>granite_TaskPurgeTask</code>) avec les propriétés adéquates. Configurez les propriétés OSGI.</p>
  </td>
  </tr>
    <tr>
    <td>Purge du workflow</td>
    <td>Client</td>
    <td>
    <p>Doit s’effectuer dans git. Remplacez le nœud de configuration de fenêtre de maintenance prêt à l’emploi sous <code>/libs</code> en créant des propriétés sous le dossier <code>/apps/settings/granite/operations/maintenance/granite_weekly</code> ou <code>granite_daily</code>. Consultez le tableau de fenêtre de maintenance ci-dessous pour en savoir plus sur la configuration.</p>
    <p>Activez la tâche de maintenance en ajoutant un autre nœud sous le nœud ci-dessus (nommez-le <code>granite_WorkflowPurgeTask</code>) avec les propriétés adéquates. Configurez les propriétés OSGI. Consultez la <a href="https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/workflows-administering.html?lang=fr#regular-purging-of-workflow-instances">documentation sur les tâches de maintenance AEM 6.5</a>.</p>
  </td>
  </tr>
  <tr>
    <td>Purge du projet</td>
    <td>Client</td>
    <td>
    <p>Doit s’effectuer dans git. Remplacez le nœud de configuration de fenêtre de maintenance prêt à l’emploi sous <code>/libs</code> en créant des propriétés sous le dossier <code>/apps/settings/granite/operations/maintenance/granite_weekly</code> ou <code>granite_daily</code>. Consultez le tableau de fenêtre de maintenance ci-dessous pour en savoir plus sur la configuration.</p>
    <p>Activez la tâche de maintenance en ajoutant un autre nœud sous le nœud ci-dessus (nommez-le <code>granite_ProjectPurgeTask</code>) avec les propriétés adéquates. Configurez les propriétés OSGI.</p>
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
    <p><strong>windowScheduleWeekdays= tableau de 2 valeurs de 1 à 7 (ex. : [5,5])</strong> La première valeur du tableau désigne le jour de début planifié de la tâche et la seconde le jour de fin où la tâche doit être arrêtée. L’heure exacte du début et de la fin est régie par les paramètres windowStartTime et windowEndTime, respectivement.</p>
    </td>
  </tr>
  <tr>
    <td>Mensuel</td>
    <td>Client</td>
    <td>Définition de nœud JCR</td>
    <td>
    <p><strong>windowSchedule=daily</strong> (cette valeur ne doit pas être modifiée)</p>
    <p><strong>windowStartTime=HH:MM</strong> dans un format horaire de 24 heures. Définit à quel moment les tâches de maintenance associées à la fenêtre de maintenance mensuelle doivent commencer à s’exécuter.</p>
    <p><strong>windowEndTime=HH:MM</strong> dans un format horaire de 24 heures. Définit à quel moment les tâches de maintenance associées à la fenêtre de maintenance mensuelle doivent arrêter de s’exécuter si elles ne sont pas déjà terminées.</p>
    <p><strong>windowScheduleWeekdays= tableau de 2 valeurs de 1 à 7 (ex. : [5,5])</strong> La première valeur du tableau désigne le jour de début planifié de la tâche et la seconde le jour de fin où la tâche doit être arrêtée. L’heure exacte du début et de la fin est régie par les paramètres windowStartTime et windowEndTime, respectivement.</p>
    <p><strong>windowFirstLastStartDay= 0/1</strong> 0 pour planifier la première semaine du mois ou 1 pour planifier la dernière semaine du mois. En l’absence de valeur, les tâches sont planifiées chaque jour, comme régi par le paramètre windowScheduleWeekdays tous les mois.</p>
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
