---
title: Mise à jour des fragments de contenu pour un filtrage GraphQL optimisé.
description: Découvrez comment mettre à jour vos fragments de contenu pour le filtrage GraphQL optimisé dans Adobe Experience Manager as a Cloud Service pour une diffusion de contenu découplée.
exl-id: 211f079e-d129-4905-a56a-4fddc11551cc
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 63%

---

# Mise à jour des fragments de contenu pour un filtrage GraphQL optimisé {#updating-content-fragments-for-optimized-graphql-filtering}

Pour optimiser les performances de vos filtres GraphQL, exécutez une procédure pour mettre à jour vos fragments de contenu.

>[!NOTE]
>
>Après avoir mis à jour vos fragments de contenu, vous pouvez suivre les recommandations relatives à l’[Optimisation des requêtes GraphQL](/help/headless/graphql-api/graphql-optimization.md).


## Conditions préalables {#prerequisites}

Il existe des conditions préalables pour cette tâche :

1. Assurez-vous de disposer au minimum de la version 2023.1.0 d’AEM as a Cloud Service.

1. Assurez-vous que l’utilisateur ou l’utilisatrice qui effectue la tâche dispose des autorisations requises :

   * au minimum, la variable `Deployment Manager` dans Cloud Manager est requis.

## Mise à jour des fragments de contenu {#updating-content-fragments}

1. Activez la mise à jour en définissant les variables suivantes pour votre instance à l’aide de l’interface utilisateur de Cloud Manager :

   ![Configuration de l’environnement de Cloud Manager](assets/cfm-graphql-update-01.png " Configuration de l´environnement de Cloud Manager").

   Les variables disponibles sont les suivantes :

   <table style="table-layout:auto">
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
      <td>« CF_MIGRATION_ENABLED » </td>
      <td>`1` </td>
      <td>`0` </td>
      <td>Tous </td>
      <td> </td>
      <td>Variable </td>
      <td>Active(!=0) ou désactive (0) le déclenchement du traitement de la migration des fragments de contenu. </td>
     </tr>
     <tr>
      <td>2</td>
      <td>« CF_MIGRATION_ENFORCE » </td>
      <td>`1` </td>
      <td>`0` </td>
      <td>Tous </td>
      <td> </td>
      <td>Variable </td>
      <td>Assurer (!=0) rémigration des fragments de contenu.<br>La définition de cet indicateur sur 0 effectue une migration incrémentielle des CF. Cela signifie que si la tâche est arrêtée pour une raison quelconque, l’exécution suivante de la tâche commence la migration à partir du point où elle a été arrêtée. La première migration est recommandée pour l’application (valeur=1). </td>
     </tr>
     <tr>
      <td>3</td>
      <td>« CF_MIGRATION_BATCH » </td>
      <td>`50` </td>
      <td>`50` </td>
      <td>Tous </td>
      <td> </td>
      <td>Variable </td>
      <td>Taille du lot pour enregistrer le nombre de fragments de contenu après la migration.<br>Cela correspond au nombre de CF qui sont enregistrés dans le référentiel en un seul lot et peut être utilisé pour optimiser le nombre d’écritures dans le référentiel. </td>
     </tr>
     <tr>
      <td>4</td>
      <td>« CF_MIGRATION_LIMIT » </td>
      <td>`1 000` </td>
      <td>`1 000` </td>
      <td>Tous </td>
      <td> </td>
      <td>Variable </td>
      <td>Nombre maximal de fragments de contenu à traiter à la fois.<br>Voir aussi les notes de « CF_MIGRATION_INTERVAL ». </td>
     </tr>
     <tr>
      <td>5</td>
      <td>« CF_MIGRATION_INTERVAL » </td>
      <td>`60` </td>
      <td>`600` </td>
      <td>Tous </td>
      <td> </td>
      <td>Variable </td>
      <td>Intervalle (en secondes) de traitement des fragments de contenu restants jusqu’à la prochaine limite<br>Cet intervalle est également considéré comme un temps d’attente avant le démarrage de la tâche et comme un délai entre le traitement de chaque nombre de CF_MIGRATION_LIMIT suivant.<br>(*)</td>
     </tr>
    </tbody>
   </table>

   >[!NOTE]
   >
   >(*)
   >
   >La valeur de `CF_MIGRATION_INTERVAL` peut également vous aider à faire une estimation du temps d’exécution total nécessaire au traitement de la migration.
   >
   >Par exemple :
   >
   >* Nombre total de fragments de contenu = 20 000.
   >* CF_MIGRATION_LIMIT = 1 000.
   >* CF_MIGRATION_INTERNAL = 60 (Sec).
   >* Durée approximative requise pour terminer la migration = 60 + (20 000/1 000 * 60) = 1 260 secondes = 21 minutes.
   >  Les « 60 » secondes supplémentaires ajoutées au début sont dues au retard initial lors du démarrage du traitement.
   >
   >Il s’agit uniquement de la variable *minimum* temps requis pour terminer la tâche, sans inclure l’heure d’E/S. Le temps réel pourrait être supérieur à cette estimation.

1. Surveillez la progression et la fin de la mise à jour.

   Pour ce faire, surveillez les journaux en mode de création et la publication Golden à partir de :

   * `com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob`

      * Journaux de création ; par exemple :

        ```shell
        23.01.2023 13:13:45.926 *INFO* [sling-threadpool-09cbdb47-4d99-4c4c-b6d5-781b635ee21b-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob This instance<dd9ffdc1-0c28-4d04-9a96-5d4d223e457e> is the leader, will schedule the upgrade schedule job.
        ...
        23.01.2023 13:13:45.941 *INFO* [sling-threadpool-09cbdb47-4d99-4c4c-b6d5-781b635ee21b-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Scheduling content fragments upgrade from version 0 to 1, slingJobId: 2023/1/23/13/13/50e1a575-4cd7-497b-adf0-62cb5768eedb_0, enforce: true, limit: 1000, batch: 50, interval: 60s
        
        23.01.2023 13:20:40.960 *INFO* [sling-threadpool-09cbdb47-4d99-4c4c-b6d5-781b635ee21b-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Finished content fragments upgrade in 6m, slingJobId: 2023/1/23/13/13/50e1a575-4cd7-497b-adf0-62cb5768eedb_0, status: MaintenanceJobStatus{jobState=SUCCEEDED, statusMessage='Upgrade to version '1' succeeded.', errors=[], successCount=3781, failedCount=0, skippedCount=0}
        ```

      * Journaux de publication Golden ; par exemple :

        ```shell
        23.01.2023 12:35:05.150 *INFO* [sling-threadpool-8abcc1bb-cdcb-46d4-8565-942ad8a73209-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob This instance<ad1b399e-77be-408e-bc3f-57097498fddb> is the leader, will schedule the upgrade schedule job.
        
        23.01.2023 12:35:05.161 *INFO* [sling-threadpool-8abcc1bb-cdcb-46d4-8565-942ad8a73209-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Scheduling content fragments upgrade from version 0 to 1, slingJobId: 2023/1/23/12/34/ad1b399e-77be-408e-bc3f-57097498fddb_0, enforce: true, limit: 1000, batch: 50, interval: 60s
        ...
        23.01.2023 12:40:45.180 *INFO* [sling-threadpool-8abcc1bb-cdcb-46d4-8565-942ad8a73209-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Finished content fragments upgrade in 5m, slingJobId: 2023/1/23/12/34/ad1b399e-77be-408e-bc3f-57097498fddb_0, status: MaintenanceJobStatus{jobState=SUCCEEDED, statusMessage='Upgrade to version '1' succeeded.', errors=[], successCount=3781, failedCount=0, skippedCount=0}
        ```

   Les clients et clientes qui ont activé l’accès aux journaux d’environnement à l’aide de Splunk peuvent utiliser l’exemple de requête ci-dessous pour surveiller le processus de mise à niveau. Pour plus d’informations sur l’activation de la journalisation Splunk, voir [Débogage dans les environnements de production et d’évaluation](/help/implementing/developing/introduction/logging.md#debugging-production-and-stage).

   ```splunk
   index=<indexName> sourcetype=aemerror aem_envId=<environmentId> msg="*com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Finished*" 
   (aem_tier=golden-publish OR aem_tier=author) | table _time aem_tier pod_name msg | sort -_time desc
   ```

   Où :

   * `environmentId` - un identifiant de l’environnement client ; par exemple, `e1234`
   * `indexName` - un nom d’index client, collectant les événements `aemerror`

   Exemple de sortie :

   <table style="table-layout:auto">
     <thead>
       <tr>
       <th>_time</th>
       <th>aem_tier</th>
       <th>pod_name</th>
       <th>msg</th>
       </tr>
     </thead> 
     <tbody>
       <tr>
         <td>2023-04-21 06:00:35.723</td>
         <td>author</td>
         <td>cm-p1234-e1234-aem-author-76d6dc4b79-8lsb5</td>
         <td>[sling-threadpool-bb5da4dd-6b05-4230-93ea-1d5cd242e24f-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Finished content fragments upgrade in 391m, slingJobId: 2023/4/20/23/16/db7963df-e267-489b-b69a-5930b0dadb37_0, status: MaintenanceJobStatus{jobState=SUCCEEDED, statusMessage='Upgrade to version '1' succeeded.', errors=[], successCount=36756, failedCount=0, skippedCount=0}</td>
       </tr>
       <tr>
         <td>2023-04-21 06:05:48.207</td>
         <td>golden-publish</td>
         <td>cm-p1234-e1234-aem-golden-publish-644487c9c5-lvkv2</td>
         <td>[sling-threadpool-284b9a9a-8454-461e-9bdb-44866c6ddfb1-(apache-sling-job-thread-pool)-1-Content Fragment Upgrade Job Queue Config(cfm/upgrader)] com.adobe.cq.dam.cfm.impl.upgrade.UpgradeJob Finished content fragments upgrade in 211m, slingJobId: 2023/4/20/23/15/66c1690a-cdb7-4e66-bc52-90f33394ddfc_0, status: MaintenanceJobStatus{jobState=SUCCEEDED, statusMessage='Upgrade to version '1' succeeded.', errors=[], successCount=19557, failedCount=0, skippedCount=0}</td>
       </tr>
     </tbody>
   <table>

1. Désactivez la procédure de mise à jour.

   >[!IMPORTANT]
   >
   >Cette étape est obligatoire pour terminer la mise à niveau.

   Une fois la procédure de mise à jour exécutée, réinitialisez la variable d’environnement cloud `CF_MIGRATION_ENABLED` sur « 0 » pour déclencher le recyclage de tous les pods.

   <table style="table-layout:auto">
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
      <td>« CF_MIGRATION_ENABLED » </td>
      <td>`0` </td>
      <td>`0` </td>
      <td>Tous </td>
      <td> </td>
      <td>Variable </td>
      <td>Désactive(0) (ou Active(!= 0) le déclenchement de la tâche de migration de fragment de contenu. </td>
     </tr>
    </tbody>
   </table>

   >[!NOTE]
   >
   >Ceci est important pour le niveau de publication, car la mise à jour du contenu est effectuée uniquement sur la publication en or. Lorsque le recyclage des capsules, toutes les capsules de publication standard sont basées sur la publication en or.

1. Vérifiez que la procédure de mise à jour est terminée.

   Vous pouvez vérifier la réussite de la mise à jour à l’aide du navigateur de référentiels dans la Developer console de Cloud Manager pour vérifier les données de fragment de contenu.

   * Avant la première migration, la variable `cfGlobalVersion` n’existe pas.
Par conséquent, la présence de cette propriété, sur le nœud JCR `/content/dam` avec la valeur `1`, confirme la fin de la migration.

   * Vous pouvez également vérifier les propriétés suivantes sur les fragments de contenu individuels :

      * `_strucVersion` doit avoir la valeur de `1`.
      * La structure `indexedData` doit exister.

     >[!NOTE]
     >
     >La procédure met à jour les fragments de contenu sur les instances d’auteur et de Publish.
     >
     >Par conséquent, Adobe vous recommande d’effectuer la vérification par le biais de l’explorateur de référentiel pour *au moins* un auteur *et* une instance Publish.

## Limites {#limitations}

Gardez à l’esprit les limites suivantes :

* L’optimisation des performances des filtres GraphQL n’est possible qu’après une mise à jour complète de tous vos fragments de contenu (indiquée par la présence de la variable `cfGlobalVersion` pour le noeud JCR. `/content/dam`)

* Si des fragments de contenu sont importés à partir d’un module de contenu (à l’aide de `crx/de`) après l’exécution de la procédure de mise à jour, ces fragments de contenu ne sont pas pris en compte dans les résultats de la requête GraphQL tant que la procédure de mise à jour n’est pas exécutée à nouveau.
