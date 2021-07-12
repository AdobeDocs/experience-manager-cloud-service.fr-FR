---
title: Réplication
description: Distribution et dépannage de la réplication.
exl-id: c84b4d29-d656-480a-a03a-fbeea16db4cd
source-git-commit: e6e5fb6eebcd39b46dc4234999e18de9b8e3950e
workflow-type: tm+mt
source-wordcount: '1185'
ht-degree: 65%

---

# Réplication {#replication}

Adobe Experience Manager as a Cloud Service utilise la fonctionnalité de [distribution de contenu Sling](https://sling.apache.org/documentation/bundles/content-distribution.html) pour déplacer le contenu à répliquer vers un service de pipeline s’exécutant sur Adobe I/O, en dehors d’AEM.

>[!NOTE]
>
>Pour en savoir plus, consultez [Distribution](/help/core-concepts/architecture.md#content-distribution).

## Méthodes de publication de contenu {#methods-of-publishing-content}

### Publication/annulation de publication rapide – Publication/annulation de publication planifiée {#publish-unpublish}

Cela vous permet de publier immédiatement la ou les pages sélectionnées, sans les options supplémentaires possibles grâce à l’approche Gérer la publication .

Pour plus d’informations, voir [Gestion de la publication](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#manage-publication).

### Heures d’activation et de désactivation – Configuration du déclenchement {#on-and-off-times-trigger-configuration}

Les autres possibilités d’**Heure d’activation** et d’**Heure de désactivation** sont disponibles dans l’[onglet De base des Propriétés de la page](/help/sites-cloud/authoring/fundamentals/page-properties.md#basic).

Pour réaliser la réplication automatique dans ce cas, vous devez activer **Auto Replicate** (Réplication automatique) dans **On Off Trigger Configuration** (Configuration d’activation et de désactivation du déclenchement) de la [configuration OSGi](/help/implementing/deploying/configuring-osgi.md) :

![Configuration OSGi d’activation et de désactivation du déclenchement](/help/operations/assets/replication-on-off-trigger.png)

### Gérer la publication  {#manage-publication}

La méthode Gérer la publication propose plus d’options que Publication rapide, dont la possibilité d’inclure des pages enfants, de personnaliser les références ou encore de lancer n’importe quel workflow applicable. Elle offre également la possibilité de publier la page à une date ultérieure.

L’inclusion des enfants d’un dossier pour l’option &quot;Publier plus tard&quot; appelle le workflow Publier l’arborescence de contenu, décrit dans cet article.

Vous trouverez des informations plus détaillées sur la gestion de la publication dans la [documentation sur les principes de publication](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#manage-publication).

### Activation d’une arborescence {#tree-activation}

>[!NOTE]
>
>Cette approche doit être considérée comme obsolète, car elle ne conserve pas les états et est moins évolutive que les autres approches. Il est recommandé à l’Adobe d’utiliser plutôt des méthodes de gestion de publication ou de workflow.

Pour exécuter une activation d’arborescence :

1. Dans le menu Accueil AEM, accédez à **Outils > Déploiement > Distribution**.
2. Sélectionnez la carte **publish**
3. Une fois dans l’interface utilisateur de la console Web de publication, **sélectionnez Distribute**

   ![Distribuer](assets/publish-distribute.png "Distribuer")
4. Sélectionnez le chemin dans l’explorateur de chemins d’accès, choisissez d’ajouter un nœud, une arborescence ou supprimez-les, si nécessaire, puis sélectionnez **Submit** (Envoyer).

### Workflow de publication de l’arborescence de contenu {#publish-content-tree-workflow}

Vous pouvez déclencher une réplication d’arborescence en choisissant **Outils – Workflow – Modèles** et en copiant le modèle de workflow prêt à l’emploi **Publier l’arborescence de contenu**, comme illustré ci-dessous :

![](/help/operations/assets/publishcontenttreeworkflow.png)

Ne modifiez pas ou n’appelez pas le modèle d’origine. Assurez-vous plutôt de copier le modèle, puis de modifier ou d’appeler cette copie.

Comme tous les workflows, il peut également être appelé via l’API. Pour plus d’informations, voir [Interaction avec les workflows par programmation](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-program-interaction.html?lang=fr#extending-aem).

Vous pouvez également y parvenir en créant un modèle de workflow qui utilise l’étape`Publish Content Tree` :

1. Sur la page d’accueil d’AEM as a Cloud Service, accédez à **Outils – Workflow – Modèles**
1. Sur la page Modèles de workflow, appuyez sur **Créer** dans l’angle supérieur droit de l’écran.
1. Ajoutez un titre et un nom à votre modèle. Pour plus d’informations, voir [Création de modèles de workflow](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=fr)
1. Sélectionnez le modèle nouvellement créé dans la liste, puis appuyez sur **Modifier**.
1. Dans la fenêtre suivante, faites un glisser-déposer de l’étape du processus dans le flux de modèle actuel :

   ![Étape du processus](/help/operations/assets/processstep.png)

1. Cliquez sur l’étape Processus dans le flux et sélectionnez **Configurer** en appuyant sur l’icône en forme de clé à molette.
1. Cliquez sur l’onglet **Processus** et sélectionnez `Publish Content Tree` dans la liste déroulante.

   ![Activation d’arborescence](/help/operations/assets/newstep.png)

1. Définissez des paramètres supplémentaires dans le champ **Arguments**. Il est possible d’associer plusieurs arguments séparés par des virgules. Par exemple :

   `enableVersion=true,agentId=publish`


   >[!NOTE]
   >
   >Pour obtenir la liste des paramètres, reportez-vous à la section **Paramètres** ci-dessous.

1. Appuyez sur **Terminé** pour enregistrer le modèle de workflow.

**Paramètres**

* `replicateAsParticipant` (valeur booléenne, valeur par défaut : `false`). S’il est configuré comme `true`, la réplication utilise la balise `userid` de l’entité qui a exécuté l’étape de participant.
* `enableVersion` (valeur booléenne, valeur par défaut : `true`). Ce paramètre détermine si une nouvelle version est créée lors de la réplication.
* `agentId` (valeur string, la valeur par défaut signifie que seuls les agents pour la publication sont utilisés). Il est recommandé d’être explicite sur l’agentId ; par exemple, définissez la valeur : publier. La définition de l’agent sur `preview` entraîne la publication sur le service d’aperçu.
* `filters` (valeur de chaîne, valeur par défaut, tous les chemins sont activés). Les valeurs disponibles sont les suivantes :
   * `onlyActivated` : seuls les chemins qui ne sont pas marqués comme activés seront activés.
   * `onlyModified` : activez uniquement les chemins déjà activés et dont la date de modification est postérieure à la date d’activation.
   * Vous pouvez utiliser la commande OU avec une barre verticale « | ». Par exemple, `onlyActivated|onlyModified`.

**Journalisation**

Lorsque l’étape du workflow d’activation de l’arborescence démarre, elle consigne ses paramètres de configuration au niveau du journal INFO. Lorsque les chemins sont activés, une instruction INFO est également consignée.

Une dernière instruction INFO sera alors consignée une fois que l’étape du workflow aura répliqué tous les chemins.

De plus, vous pouvez augmenter le niveau de journalisation des enregistreurs sous `com.day.cq.wcm.workflow.process.impl` en le fixant à DEBUG/TRACE pour obtenir encore plus d’informations sur le journal.

En cas d’erreur, l’étape du workflow s’arrête avec une balise `WorkflowException` qui représente l’exception sous-jacente.

Vous trouverez ci-dessous des exemples de journaux générés lors d’un exemple de workflow de publication d’arborescence de contenu :

```
21.04.2021 19:14:55.566 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.treeactivation.TreeActivationWorkflowProcess TreeActivation options: replicateAsParticipant=false(userid=workflow-process-service), agentId=publish, chunkSize=100, filter=, enableVersion=false
```

```
21.04.2021 19:14:58.541 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.ChunkedReplicator closing chunkedReplication-VolatileWorkItem_node1_var_workflow_instances_server60_2021-04-20_brian-tree-replication-test-2_1, 17 paths replicated in 2971 ms
```

**Prise en charge de la reprise**

Le workflow traite le contenu par blocs, chacun représentant un sous-ensemble du contenu complet à publier. Si, pour une raison quelconque, le workflow est arrêté par le système, il redémarre et traite le bloc qui n’a pas encore été traité. Une instruction de journal indique que le contenu a été repris à partir d’un chemin spécifique.

### API de réplication {#replication-api}

Vous pouvez publier du contenu à l’aide de l’API de réplication présentée dans AEM en tant que Cloud Service.

Pour plus d’informations, voir la [documentation de l’API](https://javadoc.io/doc/com.adobe.aem/aem-sdk-api/latest/com/day/cq/replication/package-summary.html).

**Utilisation de base de l’API**

```
@Reference
Replicator replicator;
@Reference
ReplicationStatusProvider replicationStatusProvider;

....
Session session = ...
// Activate a single page to all agents, which are active by default
replicator.replicate(session,ReplicationActionType.ACTIVATE,"/content/we-retail/en");
// Activate multiple pages (but try to limit it to approx 100 at max)
replicator.replicate(session,ReplicationActionType.ACTIVATE, new String[]{"/content/we-retail/en","/content/we-retail/de"});

// ways to get the replication status
Resource enResource = resourceResolver.getResource("/content/we-retail/en");
Resource deResource = resourceResolver.getResource("/content/we-retail/de");
ReplicationStatus enStatus = enResource.adaptTo(ReplicationStatus.class);
// if you need to get the status for more more than 1 resource at once, this approach is more performant
Map<String,ReplicationStatus> allStatus = replicationStatusProvider.getBatchReplicationStatus(enResource,deResource);
```

**Réplication avec des agents spécifiques**

Lors de la réplication des ressources comme dans l’exemple ci-dessus, seuls les agents principaux par défaut seront utilisés. Dans AEM en tant que Cloud Service, il s’agit uniquement de l’agent nommé &quot;publish&quot;, qui connecte l’auteur au niveau de publication.

Pour prendre en charge la fonctionnalité d’aperçu, un nouvel agent appelé &quot;aperçu&quot; a été ajouté, qui n’est pas principal par défaut. Cet agent est utilisé pour connecter l’auteur au niveau d’aperçu. Si vous souhaitez répliquer uniquement par le biais de l’agent de prévisualisation, vous devez sélectionner explicitement cet agent de prévisualisation via un `AgentFilter`.

Voir l’exemple ci-dessous pour savoir comment procéder :

```
private static final String PREVIEW_AGENT = "preview";

ReplicationStatus beforeStatus = enResource.adaptTo(ReplicationStatus.class); // beforeStatus.isActivated == false

ReplicationOptions options = new ReplicationOptions();
options.setFilter(new AgentFilter() {
  @Override
  public boolean isIncluded (Agent agent) {
    return agent.getId().equals(PREVIEW_AGENT);
  }
});
// will replicate only to preview
replicator.replicate(session,ReplicationActionType.ACTIVATE,"/content/we-retail/en", options);

ReplicationStatus afterStatus = enResource.adaptTo(ReplicationStatus.class); // afterStatus.isActivated == false
ReplicationStatus previewStatus = afterStatus.getStatusForAgent(PREVIEW_AGENT); // previewStatus.isActivated == true
```

Si vous ne fournissez pas un tel filtre et n’utilisez que l’agent &quot;publish&quot;, l’agent &quot;preview&quot; n’est pas utilisé et l’action de réplication n’affecte pas le niveau de prévisualisation.

L’ensemble `ReplicationStatus` d’une ressource n’est modifié que si l’action de réplication comprend au moins un agent principal par défaut. Dans l’exemple ci-dessus, ce n’est pas le cas, car la réplication utilise uniquement l’agent &quot;aperçu&quot;. Par conséquent, vous devez utiliser la nouvelle méthode `getStatusForAgent()`, qui permet d’interroger le statut d’un agent spécifique. Cette méthode fonctionne également pour l’agent &quot;publish&quot;. Elle renvoie une valeur non nulle si une action de réplication a été effectuée à l’aide de l’agent fourni.

## Résolution des problèmes {#troubleshooting}

Pour résoudre les problèmes de réplication, accédez aux files d’attente de réplication dans l’interface utilisateur web du service d’auteur AEM :

1. Dans le menu Accueil AEM, accédez à **Outils > Déploiement > Distribution**.
2. Sélectionnez la carte **publish**
   ![État](assets/publish-status.png "État")
3. Vérifiez l’état de la file d’attente qui doit être de couleur verte.
4. Vous pouvez tester la connexion au service de réplication.
5. Sélectionnez l’onglet **Logs** (Journaux) qui affiche l’historique des publications de contenu.

![Journaux](assets/publish-logs.png "Journaux")

S’il n’a pas été possible de publier le contenu, l’intégralité de la publication est restaurée à partir du service de publication AEM.
Dans ce cas, les files d’attente doivent être examinées afin d’identifier les éléments qui ont provoqué l’annulation de la publication. Suite à un clic sur une file d’attente signalée par un état rouge, celle contenant des éléments en attente s’affiche. Il est possible d’y effacer un ou tous les éléments, si nécessaire.
