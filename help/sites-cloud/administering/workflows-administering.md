---
title: Administration d’instances de workflows
description: Découvrez comment administrer les instances de flux de travail
translation-type: tm+mt
source-git-commit: c19079b1be36c4e87962491f263ddf97ab98f831
workflow-type: tm+mt
source-wordcount: '934'
ht-degree: 67%

---


# Administration d’instances de workflow {#administering-workflow-instances}

La console de workflows fournit plusieurs outils permettant d’administrer les instances de workflows pour vérifier qu’elles s’exécutent comme prévu.

Différentes consoles sont à votre disposition pour administrer les workflows. Use the [global navigation](/help/sites-cloud/authoring/getting-started/basic-handling.md#global-navigation) to open the **Tools** pane, then select **Workflow**:

* **Modèles** : gérez les définitions de workflows.
* **Instances** : affichez et gérez l’exécution des instances de workflows.
* **Lanceurs** : gérez le lancement des workflows.
* **Archiver** : affichez l’historique des workflows correctement terminés.
* **Échecs** : affichez l’historique des workflows terminés avec des erreurs.
* **Affectation** automatique : Configuration de l’affectation automatique de workflows aux modèles

## Suivi du statut des instances de workflows {#monitoring-the-status-of-workflow-instances}

1. Avec la navigation, sélectionnez **Outil**, puis **Workflows**.
1. Sélectionnez **Instances** pour afficher la liste des instances de workflows en cours.

   ![wf-97](/help/sites-cloud/administering/assets/wf-97.png)


## Rechercher des instances de processus {#search-workflow-instances}

1. Avec la navigation, sélectionnez **Outil**, puis **Workflows**.
1. Sélectionnez **Instances** pour afficher la liste des instances de workflows en cours. Sur le rail supérieur, dans le coin gauche, sélectionnez **Filtres**. Vous pouvez également utiliser les touches alt+1. La boîte de dialogue suivante s’affiche :

   ![wf-99-1](/help/sites-cloud/administering/assets/wf-99-1.png)

1. Dans la boîte de dialogue Filtre, sélectionnez les critères de recherche de processus. Vous pouvez effectuer des recherches en fonction de ces entrées :

   * Chemin d’accès de la charge : Sélectionner un chemin spécifique
   * Modèle de flux de travail : Sélectionner un modèle de processus
   * Destinataire : Sélectionner un responsable de processus
   * Type : Tâche, élément de flux de travail ou échec du flux de travail
   * Etat de la tâche : Principal, complet ou arrêté
   * Où je suis : Propriétaire ET cessionnaire, propriétaire uniquement, cessionnaire uniquement
   * Date de début : Date de début avant ou après une date spécifiée
   * Date de fin : Date de fin avant ou après une date spécifiée
   * Date d&#39;échéance : Date d&#39;échéance avant ou après une date spécifiée
   * Date de mise à jour : Date mise à jour avant ou après une date spécifiée

## Suspension, reprise ou arrêt d’une instance de workflows {#suspending-resuming-and-terminating-a-workflow-instance}

1. Avec la navigation, sélectionnez **Outil**, puis **Workflows**.
1. Sélectionnez **Instances** pour afficher la liste des instances de workflows en cours.

   ![wf-96-1](/help/sites-cloud/administering/assets/wf-96-1.png)

1. Sélectionnez un élément spécifique, puis utilisez **Arrêter**, **Suspendre** ou **Reprendre**, selon le cas. Une confirmation et/ou d’autres détails sont requis :

   ![wf-97-1](/help/sites-cloud/administering/assets/wf-97-1.png)

## Affichage des workflows archivés {#viewing-archived-workflows}

1. Avec la navigation, sélectionnez **Outil**, puis **Workflows**.

1. Sélectionnez **Archiver** pour afficher la liste des instances de workflows qui se sont terminées avec succès.

   ![wf-98](/help/sites-cloud/administering/assets/wf-98.png)

   >[!NOTE]
   >Le statut d’abandon est considéré comme un arrêt réussi, car il se produit suite à une action de l’utilisateur. Par exemple :
   >
   >* Utilisation de l’action **Terminer**
   >* lorsqu’une page, soumise à un flux de travail, est supprimée (force), le flux de travail est arrêté


1. Sélectionnez un élément spécifique, puis **Ouvrir l’historique** pour afficher plus de détails :

   ![wf-99](/help/sites-cloud/administering/assets/wf-99.png)

## Correction des échecs d’instance de workflows {#fixing-workflow-instance-failures}

Lorsqu’un workflow échoue, AEM fournit la console **Échecs** pour vous permettre d’enquêter et de prendre la mesure appropriée une fois la cause d’origine traitée :

* **Détails** d’échec Ouvre une fenêtre pour afficher la variable 
**Message** d’échec, **étape** et pile **** d’échec.

* **Ouvrir l’historique** Affiche des détails sur l’historique des workflows.

* **Relancer l’étape** Exécute à nouveau l’instance du composant d’étape de test. Utilisez la commande Recommencer l’étape après avoir corrigé la cause de l’erreur d’origine. Par exemple, relancez l’étape après avoir corrigé un bogue dans le script que l’étape de processus exécute.
* **Arrêter** Arrêter le processus si l&#39;erreur a provoqué une situation irréconciliable pour le processus. Par exemple, le flux de travail peut s’appuyer sur des conditions environnementales telles que des informations dans le référentiel qui ne sont plus valides pour l’instance de flux de travail.
* **Arrêter et réessayer** Similaire à **Arrêter**, à ceci près qu’une nouvelle instance de workflow est lancée à l’aide de la charge utile, du titre et de la description d’origine.

Pour examiner les échecs, puis reprendre ou arrêter le workflow par la suite, utilisez les étapes suivantes :

1. Avec la navigation, sélectionnez **Outil**, puis **Workflows**.

1. Sélectionnez **Échecs** pour afficher la liste des instances de workflows qui ne se sont pas terminées avec succès.
1. Sélectionnez un élément spécifique, puis l’action appropriée :

   ![wf-47](/help/sites-cloud/administering/assets/wf-47.png)

## Purge régulière des instances de workflow {#regular-purging-of-workflow-instances}

Réduire le nombre d’instances de workflow améliore les performances du moteur de workflows. Vous pouvez donc purger régulièrement les instances de workflows terminées ou en cours d’exécution du référentiel.

Configurez la **configuration de la purge du workflow Adobe Granite** pour purger les instances de workflows en fonction de leur âge et de leur statut. Vous pouvez également purger les instances de workflows de tous les modèles ou d’un modèle spécifique.

Vous pouvez également créer plusieurs configurations du service pour purger les instances de workflows qui répondent à différents critères. Par exemple, créez une configuration qui purge les instances d’un modèle de workflow particulier lorsqu’elles s’exécutent beaucoup plus longtemps que prévu. Créez une autre configuration qui purge tous les workflows terminés après un certain nombre de jours pour réduire la taille du référentiel.

Pour configurer le service, vous pouvez configurer les fichiers de configuration OSGi voir les fichiers [de configuration](/help/implementing/deploying/configuring-osgi.md)OSGi. Le tableau suivant décrit les propriétés dont vous avez besoin pour l’une ou l’autre méthode.

>[!NOTE]
>Pour ajouter la configuration au référentiel, le PID de service est :
>`com.adobe.granite.workflow.purge.Scheduler`
>Le service étant un service d’usine, le nom du nœud `sling:OsgiConfig` nécessite un suffixe d’identifiant, tel que :
>`com.adobe.granite.workflow.purge.Scheduler-myidentifier`

<table>
 <tbody>
  <tr>
   <th>Nom de propriété (console Web)</th>
   <th>Nom de propriété OSGi</th>
   <th>Description</th>
  </tr>
  <tr>
   <td>Nom de la tâche</td>
   <td>scheduledpurge.name</td>
   <td>Nom descriptif de la purge planifiée.</td>
  </tr>
  <tr>
   <td>État du workflow</td>
   <td>scheduledpurge.workflowStatus</td>
   <td><p>Statut des instances de workflowsà purger. Les valeurs suivantes sont valides :</p>
    <ul>
     <li>TERMINÉ : les instances de workflows terminées sont purgées.</li>
     <li>EN COURS : les instances de workflows en cours d’exécution sont purgées.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Modèles à purger</td>
   <td>scheduledpurge.modelIds</td>
   <td><p>ID des modèles de workflows à purger. L’ID est le chemin d’accès au nœud de modèle, par exemple :<br /> /conf/global/settings/workflow/models/dam/update_asset/jcr:content/model<br /> Pour purger les instances de tous les modèles de workflows, ne spécifiez aucune valeur.</p> <p>Pour spécifier plusieurs modèles, cliquez sur le bouton + dans la console Web. </p> </td>
  </tr>
  <tr>
   <td>Âge de workflow</td>
   <td>scheduledpurge.daysold</td>
   <td>L’âge des instances de workflows à purger, exprimé en jours.</td>
  </tr>
 </tbody>
</table>

## Définition de la taille maximale de la boîte de réception {#setting-the-maximum-size-of-the-inbox}

You can set the maximum size of the inbox by configuring the **Adobe Granite Workflow Service**, see [add an OSGi configuration to the repository](/help/implementing/deploying/configuring-osgi.md). Le tableau suivant décrit la propriété que vous configurez.

>[!NOTE]
>Pour ajouter la configuration au référentiel, le PID de service est :
>`com.adobe.granite.workflow.core.WorkflowSessionFactory`.

| Nom de propriété (console Web) | Nom de propriété OSGi |
|---|---|
| Taille maximale de la Requête de la boîte de réception | granite.workflow.inboxQuerySize |

