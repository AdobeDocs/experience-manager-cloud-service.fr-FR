---
title: Workflows de réplication d’arborescence dans AEM as a Cloud Service
description: Découvrez comment répliquer des hiérarchies de contenu profondes à l’aide de l’étape de workflow Activation d’arborescence et des workflows associés dans AEM as a Cloud Service.
feature: Operations
role: Admin
source-git-commit: d6555eebfa13a400f084ef4edefb92b4471adcac
workflow-type: tm+mt
source-wordcount: '1078'
ht-degree: 49%

---

# Workflows de réplication d’arborescence dans AEM as a Cloud Service {#tree-replication-workflows}

Lorsque vous devez publier une grande branche de l’arborescence de contenu, la publication page par page standard peut être lente et gourmande en ressources. AEM as a Cloud Service propose des approches basées sur des workflows qui répliquent des hiérarchies de contenu profondes en blocs gérables, s’interrompent lorsque les files d’attente de réplication sont occupées et reprennent en cas d’interruption.

Utilisez l’étape **Workflow d’activation de l’arborescence** pour la réplication d’arborescence en bloc. Il s’agit de l’approche recommandée pour les payloads volumineux. Le **workflow de publication de l’arborescence de contenu** reste documenté à titre de référence, mais il est obsolète au profit de l’étape d’activation de l’arborescence.

Pour plus d’informations sur la réplication, voir [Réplication](/help/operations/replication.md).

## Étape du workflow d’activation de l’arborescence {#tree-activation}

L’étape de workflow Activation de l’arborescence est destinée à répliquer de manière performante une hiérarchie profonde de nœuds de contenu. Il se met automatiquement en pause lorsque la file d’attente devient trop volumineuse afin de permettre à d’autres réplications de se poursuivre en parallèle avec une latence minimale.

Créez un modèle de workflow qui utilise l’étape de processus `TreeActivation` :

1. Sur la page d’accueil d’AEM as a Cloud Service, accédez à **Outils – Workflow – Modèles**.
1. Sur la page Modèles de workflow, appuyez sur **Créer** dans l’angle supérieur droit de l’écran.
1. Ajoutez un titre et un nom à votre modèle. Pour plus d’informations, voir [Création de modèles de workflow](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=fr).
1. Sélectionnez le modèle créé dans la liste, puis appuyez sur **Modifier**
1. Dans la fenêtre suivante, supprimez l’étape qui s’affiche par défaut
1. Glissez-déposez l’étape de processus dans le flux de modèle actuel :

   ![Étape du processus](/help/operations/assets/processstep.png)

1. Sélectionnez l’étape du processus dans le flux et sélectionnez **Configurer** en appuyant sur l’icône en forme de clé à molette.
1. Sélectionnez l’onglet **Processus**, puis `Publish Content Tree` dans la liste déroulante, puis cochez la case **Avance du gestionnaire**

   ![Activation d’arborescence](/help/operations/assets/new-treeactivationstep.png)

1. Définissez des paramètres supplémentaires dans le champ **Arguments**. Plusieurs arguments séparés par des virgules peuvent être assemblés. Par exemple :

   `enableVersion=false,agentId=publish,chunkSize=50,maxTreeSize=500000,dryRun=false,filters=onlyModified,maxQueueSize=10`

   >[!NOTE]
   >
   >Pour obtenir la liste des paramètres, reportez-vous à la section **Paramètres** ci-dessous.

1. Appuyez sur **Terminé** pour enregistrer le modèle de workflow.

**Paramètres**

| Nom | par défaut | Description |
| -------------- | ------- | --------------------------------------------------------------- |
| path |         | chemin racine à partir duquel commencer |
| agentId | Publication | Agent qui reçoit la réplication (`publish` ou `preview`) |
| chunkSize | 50 | Nombre de chemins à regrouper en une seule réplication |
| maxTreeSize | 500000 | Nombre maximal de nœuds pour qu’une arborescence soit considérée comme petite |
| maxQueueSize | 10 | Nombre maximal d’éléments dans la file d’attente de réplication |
| enableVersion | false | Activer le contrôle de version |
| dryRun | false | Lorsque la valeur est définie sur true, la réplication n’est pas appelée. |
| userId |         | uniquement pour le travail. Dans le workflow, l’utilisateur qui appelle le workflow est utilisé |
| filtres |         | Liste des noms de filtre de nœud. Consultez les filtres pris en charge ci-dessous |

**Filtres de prise en charge**

| Nom | Description |
| ------------- | ------------------------------------------- |
| onlyModified | Nœuds : nouveaux et préexistants qui ont été modifiés depuis la dernière publication. |
| onlyActivated | Nœuds : qui ont été publiés avant la dernière publication |


**Prise en charge de la reprise**

Le workflow traite le contenu par blocs, chacun représentant un sous-ensemble du contenu complet à publier.  Si le workflow est arrêté par le système, il continue là où il s’est arrêté.

**Surveillance de la progression du workflow**

1. Sur la page d’accueil d’AEM as a Cloud Service, accédez à **Outils - Général - Tâches**.
1. Examinez la ligne correspondant à votre workflow. La colonne *progress* indique la progression de la réplication. Par exemple, il peut afficher 41/564 et, lors du rafraîchissement, il peut être mis à jour à 52/564.

   ![Progression de l’activation de l’arborescence](/help/operations/assets/treeactivation-progress.png)


1. La sélection de la ligne et son ouverture fournissent des détails supplémentaires sur le statut de l’exécution du workflow.

   ![Détails du statut d’activation de l’arborescence](/help/operations/assets/treeactivation-progress-details.png)



## Workflow de publication de l’arborescence de contenu {#publish-content-tree-workflow}

>[!NOTE]
>
>Cette fonctionnalité est abandonnée au profit de l’étape d’activation de l’arborescence plus performante, qui peut être incluse dans un workflow personnalisé.

+++ Cliquez ici pour en savoir plus sur cette fonctionnalité obsolète.

Vous pouvez déclencher une réplication d’arborescence en choisissant **Outils – Workflow – Modèles** et en copiant le modèle de workflow prêt à l’emploi **Publier l’arborescence de contenu**, comme illustré ci-dessous :

![Carte du workflow Publier l’arborescence de contenu](/help/operations/assets/publishcontenttreeworkflow.png)

N’appelez pas le modèle d’origine. Veillez plutôt à copier le modèle et à appeler cette copie.

Comme tous les workflows, il peut également être appelé via l’API. Pour plus d’informations, voir [Interaction avec les workflows par programmation](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-program-interaction.html?lang=fr#extending-aem).

Vous pouvez également créer un modèle de workflow qui utilise l’étape de processus `Publish Content Tree`.

1. Sur la page d’accueil d’AEM as a Cloud Service, accédez à **Outils – Workflow – Modèles**.
1. Sur la page Modèles de workflow, appuyez sur **Créer** dans l’angle supérieur droit de l’écran.
1. Ajoutez un titre et un nom à votre modèle. Pour plus d’informations, voir [Création de modèles de workflow](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=fr).
1. Sélectionnez le modèle créé dans la liste, puis appuyez sur **Modifier**
1. Dans la fenêtre suivante, faites un glisser-déposer de l’étape du processus dans le flux de modèle actuel :

   ![Étape du processus](/help/operations/assets/processstep.png)

1. Sélectionnez l’étape du processus dans le flux et sélectionnez **Configurer** en appuyant sur l’icône en forme de clé à molette.
1. Sélectionnez l’onglet **Processus**, puis `Publish Content Tree` dans la liste déroulante, puis cochez la case **Avance du gestionnaire**

   ![Activation d’arborescence](/help/operations/assets/newstep.png)

1. Définissez des paramètres supplémentaires dans le champ **Arguments**. Plusieurs arguments séparés par des virgules peuvent être assemblés. Par exemple :

   `enableVersion=true,agentId=publish,includeChildren=true`


   >[!NOTE]
   >
   >Pour obtenir la liste des paramètres, reportez-vous à la section **Paramètres** ci-dessous.

1. Appuyez sur **Terminé** pour enregistrer le modèle de workflow.

**Paramètres**

* `includeChildren` (valeur booléenne, valeur par défaut : `false`). La valeur `false` signifie que seul le chemin est publié. `true` signifie que les enfants sont également publiés.
* `replicateAsParticipant` (valeur booléenne, valeur par défaut : `false`). S’il est configuré comme `true`, la réplication utilise la balise `userid` du principal qui a exécuté l’étape de participant.
* `enableVersion` (valeur booléenne, valeur par défaut : `false`). Ce paramètre détermine si une nouvelle version est créée lors de la réplication.
* `agentId` (valeur de chaîne, la valeur par défaut signifie que seuls les agents pour la publication sont utilisés). Spécifiez explicitement l’agent cible, par exemple, `publish` pour le niveau de publication en direct ou `preview` pour le niveau d’aperçu.
* `filters` (valeur de chaîne, la valeur par défaut signifie que tous les chemins sont activés). Les valeurs disponibles sont les suivantes :
   * `onlyActivated` - activez uniquement les pages qui ont (déjà) été activées. Cette option agit, en quelque sorte, comme une réactivation.
   * `onlyModified` : activez uniquement les chemins déjà activés et dont la date de modification est postérieure à la date d’activation.
   * Vous pouvez utiliser la commande OU avec une barre verticale « | ». Par exemple, `onlyActivated|onlyModified`.

**Journalisation**

Lorsque l’étape du workflow d’activation de l’arborescence démarre, elle consigne ses paramètres de configuration sur le logLevel INFO. Lorsque les chemins sont activés, une instruction INFO est également consignée.

Une dernière instruction INFO est alors consignée une fois que l’étape du workflow aura répliqué tous les chemins.

De plus, vous pouvez augmenter le logLevel des enregistreurs sous `com.day.cq.wcm.workflow.process.impl` jusqu’à à DEBUG/TRACE pour obtenir encore plus d’informations sur le journal.

En cas d’erreur, l’étape du workflow s’arrête avec `WorkflowException` qui représente l’exception sous-jacente.

Vous trouverez ci-dessous des exemples de journaux générés lors d’un exemple de workflow de publication d’arborescence de contenu :

```
21.04.2021 19:14:55.566 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.treeactivation.TreeActivationWorkflowProcess TreeActivation options: replicateAsParticipant=false(userid=workflow-process-service), agentId=publish, chunkSize=100, filter=, enableVersion=false
```

```
21.04.2021 19:14:58.541 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.ChunkedReplicator closing chunkedReplication-VolatileWorkItem_node1_var_workflow_instances_server60_2021-04-20_brian-tree-replication-test-2_1, 17 paths replicated in 2971 ms
```

+++
