---
title: Mise à jour des fragments de contenu pour la pagination et le tri
description: Découvrez comment mettre à jour les fragments de contenu pour la pagination et le tri dans Adobe Experience Manager as a Cloud Service pour une diffusion de contenu sans interface utilisateur.
source-git-commit: 130f653a1b0db55ea6d49a87be1215001223bf78
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 6%

---


# Mise à jour des fragments de contenu pour la pagination et le tri dans le filtrage GraphQL {#updating-content-fragments-for-paging-and-sorting-graphql-filtering}

Pour optimiser les performances de vos filtres GraphQL, vous devez exécuter une procédure pour mettre à jour vos fragments de contenu.

>[!NOTE]
>
>Après avoir mis à jour vos fragments de contenu, vous pouvez suivre les recommandations relatives à la [Optimisation des requêtes GraphQL](/help/headless/graphql-api/graphql-optimization.md).


## Prérequis {#prerequisites}

Assurez-vous de disposer d’un minimum de la version 2023.1.0 d’AEM as a Cloud Service.

## Mise à jour des fragments de contenu {#updating-content-fragments}

Pour exécuter la procédure, procédez comme suit :

1. Activez la mise à jour en définissant les variables suivantes pour votre instance à l’aide de l’interface utilisateur de Cloud Manager :

   ![Configuration de l’environnement de Cloud Manager](assets/cfm-graphql-update-01.png "Configuration de l’environnement de Cloud Manager")

   Les variables disponibles sont les suivantes :

   <table>
    <tbody>
     <tr>
      <th> </th>
      <th>Nom</th>
      <th>Valeur</th>
      <th>Valeur par défaut</th>
      <th>Service</th>
      <th>Appliqué</th>
      <th>Type</th>
      <th>Remarques</th>
     </tr>
     <tr>
      <td>1</td>
      <td>`AEM_RELEASE_CHANNEL` </td>
      <td>`prerelrelease` </td>
      <td> </td>
      <td>Tous </td>
      <td> </td>
      <td>Variable </td>
      <td>Requis pour activer la fonction. </td>
     </tr>
     <tr>
      <td>2</td>
      <td>`CF_MIGRATION_ENABLED` </td>
      <td>`1` </td>
      <td>`0` </td>
      <td>Tous </td>
      <td> </td>
      <td>Variable </td>
      <td>Enables(!=0) ou désactive (0) le déclenchement de la tâche de migration de fragments de contenu. </td>
     </tr>
     <tr>
      <td>3</td>
      <td>`CF_MIGRATION_ENFORCE` </td>
      <td>`1` </td>
      <td>`0` </td>
      <td>Tous </td>
      <td> </td>
      <td>Variable </td>
      <td>Application (!=0) rémigration des fragments de contenu.<br>La définition de cet indicateur sur 0 entraînera une migration incrémentielle des CF. Cela signifie que si la tâche est arrêtée pour une raison quelconque, la prochaine exécution de la tâche démarre la migration à partir du point où elle a été arrêtée. Notez que la toute première migration est recommandée (value=1). </td>
     </tr>
     <tr>
      <td>4</td>
      <td>`CF_MIGRATION_BATCH` </td>
      <td>`50` </td>
      <td>`50` </td>
      <td>Tous </td>
      <td> </td>
      <td>Variable </td>
      <td>Taille du lot pour l’enregistrement du nombre de fragments de contenu après la migration.<br>Cela correspond au nombre de CF qui seront enregistrés dans le référentiel dans un lot et peut être utilisé pour optimiser le nombre d’écritures dans le référentiel. </td>
     </tr>
     <tr>
      <td>5</td>
      <td>`CF_MIGRATION_LIMIT` </td>
      <td>`1 000` </td>
      <td>`1 000` </td>
      <td>Tous </td>
      <td> </td>
      <td>Variable </td>
      <td>Nombre maximal de fragments de contenu à traiter à la fois.<br>Voir aussi les notes de "CF_MIGRATION_INTERVAL". </td>
     </tr>
     <tr>
      <td>6</td>
      <td>`CF_MIGRATION_INTERVAL` </td>
      <td>`60` </td>
      <td>`600` </td>
      <td>Tous </td>
      <td> </td>
      <td>Variable </td>
      <td>Intervalle (secondes) de traitement des fragments de contenu restants jusqu’à la prochaine limite<br>Cet intervalle est également considéré comme un temps d’attente avant le démarrage de la tâche, ainsi que comme un délai entre le traitement de chaque nombre de CF_MIGRATION_LIMIT suivant.<br>(*)</td>
     </tr>
    </tbody>
   </table>

   >[!NOTE]
   >
   >(*)
   >
   >La valeur de `CF_MIGRATION_INTERVAL` peut également vous aider à approximer le temps d’exécution total de la tâche de migration.
   >
   >Par exemple :
   >
   >* Nombre total de fragments de contenu = 20 000
   >* CF_MIGRATION_LIMIT = 1 000
   >* CF_MIGRATION_INTERNAL = 60 (Sec)
   >* Durée approximative requise pour terminer la migration = 60 + (20,000/1000 * 60) = 1260 secondes = 21 minutes
      >  La &quot;60&quot; seconde supplémentaire ajoutée au début est due au délai initial lors du démarrage de la tâche.

   >
   >Vous devez également savoir qu’il s’agit uniquement de la variable *minimum* temps requis pour terminer la tâche, sans inclure l’heure d’E/S. Le temps réel pourrait être beaucoup plus important que cette estimation.

1. Surveillez la progression et la fin de la mise à jour.

   Pour ce faire, surveillez les journaux sur l’auteur et la publication en or à partir de :

   * `com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob`

      * Journaux de création ; par exemple :

         ```shell
         23.01.2023 13:13:45.926 *INFO* [sling-threadpool-09cbdb47-4d99-4c4c-b6d5-781b635ee21b-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob This instance<dd9ffdc1-0c28-4d04-9a96-5d4d223e457e> is the leader, will schedule the upgrade schedule job.
         ...
         23.01.2023 13:13:45.941 *INFO* [sling-threadpool-09cbdb47-4d99-4c4c-b6d5-781b635ee21b-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Scheduling content fragments upgrade from version 0 to 1, slingJobId: 2023/1/23/13/13/50e1a575-4cd7-497b-adf0-62cb5768eedb_0, enforce: true, limit: 1000, batch: 50, interval: 60s
         
         23.01.2023 13:20:40.960 *INFO* [sling-threadpool-09cbdb47-4d99-4c4c-b6d5-781b635ee21b-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Finished content fragments upgrade in 6m, slingJobId: 2023/1/23/13/13/50e1a575-4cd7-497b-adf0-62cb5768eedb_0, status: MaintenanceJobStatus{jobState=SUCCEEDED, statusMessage='Upgrade to version '1' succeeded.', errors=[], successCount=3781, failedCount=0, skippedCount=0}
         ```
   * Logs de publication en or ; par exemple :

      ```shell
      23.01.2023 12:35:05.150 *INFO* [sling-threadpool-8abcc1bb-cdcb-46d4-8565-942ad8a73209-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob This instance<ad1b399e-77be-408e-bc3f-57097498fddb> is the leader, will schedule the upgrade schedule job.
      
      23.01.2023 12:35:05.161 *INFO* [sling-threadpool-8abcc1bb-cdcb-46d4-8565-942ad8a73209-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Scheduling content fragments upgrade from version 0 to 1, slingJobId: 2023/1/23/12/34/ad1b399e-77be-408e-bc3f-57097498fddb_0, enforce: true, limit: 1000, batch: 50, interval: 60s
      ...
      23.01.2023 12:40:45.180 *INFO* [sling-threadpool-8abcc1bb-cdcb-46d4-8565-942ad8a73209-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Finished content fragments upgrade in 5m, slingJobId: 2023/1/23/12/34/ad1b399e-77be-408e-bc3f-57097498fddb_0, status: MaintenanceJobStatus{jobState=SUCCEEDED, statusMessage='Upgrade to version '1' succeeded.', errors=[], successCount=3781, failedCount=0, skippedCount=0}
      ```


1. Désactivez la procédure de mise à jour.

   >[!IMPORTANT]
   >
   >Cette étape est requise pour terminer la mise à niveau.

   Une fois la procédure de mise à jour exécutée, réinitialisez la variable d’environnement cloud. `CF_MIGRATION_ENABLED` à &quot;0&quot;, pour déclencher le recyclage de toutes les capsules.

   <table>
    <tbody>
     <tr>
      <th> </th>
      <th>Nom</th>
      <th>Valeur</th>
      <th>Valeur par défaut</th>
      <th>Service</th>
      <th>Appliqué</th>
      <th>Type</th>
      <th>Remarques</th>
     </tr>
     <tr>
      <td></td>
      <td>`CF_MIGRATION_ENABLED` </td>
      <td>`0` </td>
      <td>`0` </td>
      <td>Tous </td>
      <td> </td>
      <td>Variable </td>
      <td>Désactive(0) (ou Active(!= 0) Déclenchement de la tâche de migration de fragments de contenu. </td>
     </tr>
    </tbody>
   </table>

   >[!NOTE]
   >
   >Ceci est particulièrement important pour le niveau de publication, car la mise à jour du contenu est effectuée uniquement sur la publication en or. Lorsque vous recyclez des capsules, toutes les capsules de publication normales sont basées sur la publication en or.

1. Vérifiez que la procédure de mise à jour est terminée.

   Vous pouvez vérifier la réussite de la mise à jour à l’aide du navigateur de référentiel dans la console de développement de Cloud Manager pour vérifier les données de fragment de contenu.

   * Avant la première migration, la variable `cfGlobalVersion` n’existera pas.
Par conséquent, la présence de cette propriété, sur le noeud JCR `/content/dam` avec la valeur `1`, confirme la fin de la migration.

   * Vous pouvez également vérifier les propriétés suivantes sur les fragments de contenu individuels :

      * `_strucVersion` doit avoir la valeur de `1`
      * `indexedData` La structure doit exister

      >[!NOTE]
      >
      >La procédure met à jour les fragments de contenu sur les instances de création et de publication.
      >
      >Par conséquent, il est recommandé d’effectuer la vérification via le navigateur de référentiel pour *au moins* un auteur *et* une instance de publication.


## Limites {#limitations}

Gardez à l’esprit les limites suivantes :

* L’optimisation des performances des filtres GraphQL ne sera possible qu’après une mise à jour complète de tous vos fragments de contenu (indiquée par la présence de la variable `cfGlobalVersion` pour le noeud JCR. `/content/dam`)

* Si des fragments de contenu sont importés à partir d’un module de contenu (à l’aide de `crx/de`) après l’exécution de la procédure de mise à jour, ces fragments de contenu ne seront pas pris en compte dans les résultats de la requête GraphQL, tant que la procédure de mise à jour n’aura pas été exécutée à nouveau.