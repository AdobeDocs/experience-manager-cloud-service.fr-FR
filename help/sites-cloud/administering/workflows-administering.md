---
title: Administration d’instances de workflow
description: Découvrez comment gérer les instances de workflow à l’aide de la console de workflow
feature: Administering
role: Admin
exl-id: d2adb5e8-3f0e-4a3b-b7d0-dbbc5450e45f
solution: Experience Manager Sites
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1286'
ht-degree: 98%

---

# Administration d’instances de workflow {#administering-workflow-instances}

La console de workflows fournit plusieurs outils permettant d’administrer les instances de workflow pour vérifier qu’elles s’exécutent comme prévu.

Différentes consoles sont à votre disposition pour administrer les workflows. Utilisez la [navigation globale](/help/sites-cloud/authoring/basic-handling.md#global-navigation) pour ouvrir le panneau **Outils**, puis sélectionnez **Workflows** :

* **Modèles** : gérez les définitions des workflows
* **Instances** : affichez et gérez l’exécution des instances de workflow.
* **Lanceurs** : gérez le lancement des workflows
* **Archive** : affichez l’historique des workflows correctement terminés
* **Échecs** : affichez l’historique des workflows terminés avec des erreurs
* **Attribution automatique** : configurez l’attribution automatique des workflows aux modèles

## Suivi du statut des instances de workflow {#monitoring-the-status-of-workflow-instances}

1. Avec la navigation, sélectionnez **Outil**, puis **Workflows**.
1. Sélectionnez **Instances** pour afficher la liste des instances de workflow en cours d’exécution.
1. Sur le rail supérieur, dans le coin droit, les instances de workflow affichent **Workflows en cours d’exécution**, **Statut**, et **Détails**.
1. **Workflows en cours d’exécution** indique le nombre de workflows en cours d’exécution et leur statut. Par exemple, dans les images données, le nombre de **workflows en cours d’exécution** et le **statut** de l’instance AEM sont affichés :

   * **Statut : sain**
     ![status-healthy](/help/sites-cloud/administering/assets/status-healthy.png)

   * **Statut : non sain**
     ![status-unhealthy](/help/sites-cloud/administering/assets/status-unhealthy.png)

1. Si vous souhaitez avoir des **détails sur le statut** des instances de workflow, cliquez sur **Détails** pour afficher le **nombre d’instances de workflows en cours d’exécution**, les **instances de workflow terminées**, les **instances de workflow abandonnées**, **instances de workflow en échec**, etc. Par exemple, ci-dessous, les images données qui affichent les **détails sur le statut** avec :

   * **Détails sur le statut : sain**
     ![status-details-healthy](/help/sites-cloud/administering/assets/status-details-healthy.png)

   * **Détails sur le statut : non sain**
     ![status-details-unhealthy](/help/sites-cloud/administering/assets/status-details-unhealthy.png)

   >[!NOTE]
   >
   > Pour maintenir une instance de workflow saine, consultez les rubriques [Purge régulière des instances de workflow](#regular-purging-of-workflow-instances) ou [Bonnes pratiques en matière de workflows](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-best-practices.html).

## Rechercher des instances de workflow {#search-workflow-instances}

1. Avec la navigation, sélectionnez **Outil**, puis **Workflows**.
1. Sélectionnez **Instances** pour afficher la liste des instances de workflow en cours. Sur le rail supérieur, dans le coin gauche, sélectionnez **Filtres**. Vous pouvez également utiliser les touches alt+1. La boîte de dialogue suivante s’affiche :

   ![wf-99-1](/help/sites-cloud/administering/assets/wf-99-1.png)

1. Dans la boîte de dialogue Filtre, sélectionnez les critères de recherche de workflow. Vous pouvez effectuer des recherches en fonction des entrées suivantes :

   * Chemin d’accès à la charge utile : sélectionnez un chemin spécifique
   * Modèle de workflow : sélectionnez un modèle de workflow
   * Cessionnaire : sélectionnez un cessionnaire de workflow
   * Type : tâche, élément de workflow ou échec de workflow
   * Statut de la tâche : active, complète ou terminée
   * Où j’en suis : Propriétaire ET cessionnaire, Propriétaire uniquement, Cessionnaire uniquement
   * Date de début : date de début avant ou après une date spécifiée
   * Date de fin : date de fin avant ou après une date spécifiée
   * Échéance : date d’échéance avant ou après une date spécifiée
   * Date de mise à jour : date de mise à jour avant ou après une date spécifiée

## Suspension, reprise ou arrêt d’une instance de workflows {#suspending-resuming-and-terminating-a-workflow-instance}

1. Avec la navigation, sélectionnez **Outils**, puis **Workflows**.
1. Sélectionnez **Instances** pour afficher la liste des instances de workflow en cours.

   ![wf-96-1](/help/sites-cloud/administering/assets/wf-96-1.png)

1. Sélectionnez un élément spécifique, puis utilisez **Arrêter**, **Suspendre** ou **Reprendre**, selon le cas. Une confirmation et/ou d’autres détails sont requis :

   ![wf-97-1](/help/sites-cloud/administering/assets/wf-97-1.png)

   >[!NOTE]
   >
   >
   >Pour arrêter ou abandonner un workflow, celui-ci doit être en attente d’une intervention de l’utilisateur ou utilisatrice, par exemple dans une étape de participant ou participante. Toute tentative d’abandon d’un workflow en cours d’exécution de traitements (threads actifs en cours d’exécution) peut ne pas produire les résultats escomptés.


## Affichage des workflows archivés {#viewing-archived-workflows}

1. Avec la navigation, sélectionnez **Outils**, puis **Workflows**.

1. Sélectionnez **Archiver** pour afficher la liste des instances de workflow qui se sont terminées avec succès.

   ![archived-instances](/help/sites-cloud/administering/assets/archived-instances.png)

   >[!NOTE]
   >
   >
   >Le statut d’abandon est considéré comme une interruption réussie, car il se produit suite à une action de l’utilisateur ou utilisatrice. Par exemple :
   >
   >* L’utilisation de la fonction **Arrêter**
   >* Lorsqu’une page, soumise à un workflow, est supprimée (de force), le workflow est arrêté.

1. Sélectionnez un élément spécifique, puis **Ouvrir l’historique** pour afficher plus de détails :

   ![wf-99](/help/sites-cloud/administering/assets/wf-99.png)

## Correction des échecs d’instance de workflows {#fixing-workflow-instance-failures}

Lorsqu’un workflow échoue, AEM fournit la console **Échecs** pour vous permettre d’enquêter et de prendre la mesure appropriée une fois la cause d’origine traitée :

* **Détails de l’échec**
Ouvre une fenêtre pour afficher le **Message d’échec**, **Step et **Pile des échecs**.

* **Ouvrir l’historique**
Affiche des détails sur l’historique des workflows.

* **Relancer l’étape** Exécute à nouveau l’instance du composant d’étape de test. Utilisez la commande Relancer l’étape après avoir corrigé la cause de l’erreur initiale. Par exemple, relancez l’étape après avoir corrigé un bogue dans le script que l’étape de processus exécute.
* **Arrêter** Arrêtez le workflow si l’erreur a provoqué une situation irrémédiable pour le workflow. Par exemple, le workflow peut se baser sur des conditions environnementales comme des informations figurant dans le référentiel qui ne sont plus valides pour l’instance de workflow.
* **Arrêter et réessayer** Similaire à **Arrêter**, à ceci près qu’une nouvelle instance de workflow est lancée à l’aide de la payload, du titre et de la description d’origine.

Pour examiner les échecs, puis reprendre ou arrêter le workflow par la suite, utilisez les étapes suivantes :

1. Avec la navigation, sélectionnez **Outil**, puis **Workflows**.

1. Sélectionnez **Échecs** pour afficher la liste des instances de workflow qui ne se sont pas terminées avec succès.
1. Sélectionnez un élément spécifique, puis l’action appropriée :

![workflow-failure](/help/sites-cloud/administering/assets/workflow-failure.png)

## Purge régulière des instances de workflow {#regular-purging-of-workflow-instances}

Réduire le nombre d’instances de workflow améliore les performances du moteur de workflows. Vous pouvez donc purger régulièrement les instances de workflow terminées ou en cours d’exécution du référentiel.

Configurez la **configuration de la purge du workflow Adobe Granite** pour purger les instances de workflows en fonction de leur âge et de leur statut. Vous pouvez également purger les instances de workflow de tous les modèles ou d’un modèle spécifique.

Vous pouvez également créer plusieurs configurations du service pour purger les instances de workflow qui répondent à différents critères. Par exemple, créez une configuration qui purge les instances d’un modèle de workflow particulier lorsqu’elles s’exécutent beaucoup plus longtemps que prévu. Créez une autre configuration qui purge tous les workflows terminés après quelques jours afin de minimiser la taille du référentiel.

Pour configurer le service, vous pouvez configurer les fichiers de configuration OSGi (voir [Fichiers de configuration OSGi](/help/implementing/deploying/configuring-osgi.md)). Le tableau suivant décrit les propriétés dont vous avez besoin pour l’une ou l’autre de ces méthodes.

>[!NOTE]
>Pour ajouter la configuration au référentiel, le PID de service est :
>`com.adobe.granite.workflow.purge.Scheduler`
>Le service étant un service d’usine, le nom du nœud `sling:OsgiConfig` nécessite un suffixe d’identifiant, tel que :
>`com.adobe.granite.workflow.purge.Scheduler-myidentifier`

<table>
 <tbody>
  <tr>
   <th>Nom de propriété (console web)</th>
   <th>Nom de propriété OSGi</th>
   <th>Description</th>
  </tr>
  <tr>
   <td>Nom du traitement</td>
   <td>scheduledpurge.name</td>
   <td>Nom explicite de la purge planifiée.</td>
  </tr>
  <tr>
   <td>Statut du workflow</td>
   <td>scheduledpurge.workflowStatus</td>
   <td><p>Statut des instances de workflow à purger. Les valeurs suivantes sont valides :</p>
    <ul>
     <li>TERMINÉ : les instances de workflow terminées sont purgées.</li>
     <li>EN COURS : les instances de workflow en cours d’exécution sont purgées.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Modèles à purger</td>
   <td>scheduledpurge.modelIds</td>
   <td><p>ID des modèles de workflows à purger. L’ID est le chemin d’accès au nœud de modèle, par exemple :<br /> /conf/global/settings/workflow/models/dam/update_asset/jcr:content/model<br /> Pour purger les instances de tous les modèles de workflows, ne spécifiez aucune valeur.</p> <p>Pour spécifier plusieurs modèles, cliquez sur le bouton + dans la console web. </p> </td>
  </tr>
  <tr>
   <td>Âge du workflow</td>
   <td>scheduledpurge.daysell</td>
   <td>L’âge des instances de workflow à purger, exprimé en jours.</td>
  </tr>
 </tbody>
</table>

## Définition de la taille maximale de la boîte de réception {#setting-the-maximum-size-of-the-inbox}

Vous pouvez définir la taille maximale de la boîte de réception en configurant le **service de workflow Adobe Granite** ; voir [Ajouter une configuration OSGi au référentiel](/help/implementing/deploying/configuring-osgi.md). Le tableau suivant décrit la propriété que vous pouvez configurer.

>[!NOTE]
>Pour ajouter la configuration au référentiel, le PID de service est :
>`com.adobe.granite.workflow.core.WorkflowSessionFactory`.

| Nom de propriété (console web) | Nom de propriété OSGi |
|---|---|
| Taille de requête de boîte de réception maximale | granite.workflow.inboxQuerySize |

## Utilisation de variables de workflow pour les banques de données détenues par le client {#using-workflow-variables-customer-datastore}

Les données traitées par les workflows sont stockées dans l’enregistrement fourni par Adobe (JCR). Par nature, ces données peuvent être sensibles. Vous pouvez enregistrer toutes les métadonnées et les données définies par l’utilisateur ou l’utilisatrice dans votre propre espace de stockage géré au lieu de celui fourni par Adobe. Ces sections décrivent comment configurer ces variables pour un enregistrement externe.

### Définition du modèle pour utiliser l’enregistrement externe des métadonnées {#set-model-for-external-storage}

Au niveau du modèle de workflow, un indicateur est fourni pour indiquer que le modèle (et ses instances d’exécution) dispose d’un enregistrement externe des métadonnées. Les variables de workflow ne seront pas conservées dans le JCR pour les instances de workflow des modèles marqués pour l’enregistrement externe.

La propriété *userMetadataPersistenceEnabled* sera stockée dans le *nœud jcr:content* du modèle de workflow. Cet indicateur sera conservé dans les métadonnées de workflow sous le nom *cq:userMetaDataCustomPersistenceEnabled*.

L’illustration ci-dessous montre comment définir l’indicateur dans un workflow.

![workflow-externalize-config](/help/sites-cloud/administering/assets/workflow-externalize-config.png)

### API pour les métadonnées dans un enregistrement externe {#apis-for-metadata-external-storage}

Pour stocker les variables en externe, vous devez implémenter les API exposées par le workflow.

UserMetaDataPersistenceContext

Les exemples suivants vous montrent comment utiliser l’API.

```
@ProviderType
public interface UserMetaDataPersistenceContext {
 
    /**
     * Gets the workflow for persistence
     * @return workflow
     */
    Workflow getWorkflow();
 
    /**
     * Gets the workflow id for persistence
     * @return workflowId
     */
    String getWorkflowId();
 
    /**
     * Gets the user metadata persistence id
     * @return userDataId
     */
    String getUserDataId();
}
```

UserMetaDataPersistenceProvider

```
/**
 * This provider can be implemented to store the user defined workflow-data metadata in a custom storage location
 */
@ConsumerType
public interface UserMetaDataPersistenceProvider {
 
   /**
    * Retrieves the metadata using a unique identifier
    * @param userMetaDataPersistenceContext
    * @param metaDataMap of user defined workflow data metaData
    * @throws WorkflowException
    */
   void get(UserMetaDataPersistenceContext userMetaDataPersistenceContext, MetaDataMap metaDataMap) throws WorkflowException;
 
   /**
    * Stores the given metadata to the custom storage location
    * @param userMetaDataPersistenceContext
    * @param metaDataMap metadata map
    * @return the unique identifier that can be used to retrieve metadata. If null is returned, then workflowId is used.
    * @throws WorkflowException
    */
   String put(UserMetaDataPersistenceContext userMetaDataPersistenceContext, MetaDataMap metaDataMap) throws WorkflowException;
 
} 
```
