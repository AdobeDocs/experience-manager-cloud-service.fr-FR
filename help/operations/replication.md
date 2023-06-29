---
title: Réplication
description: Distribution et dépannage de la réplication.
exl-id: c84b4d29-d656-480a-a03a-fbeea16db4cd
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '1339'
ht-degree: 46%

---

# Réplication {#replication}

Adobe Experience Manager as a Cloud Service utilise la variable [Distribution de contenu Sling](https://sling.apache.org/documentation/bundles/content-distribution.html) possibilité de déplacer le contenu à répliquer vers un service de pipeline s’exécutant sur Adobe Developer en dehors de l’exécution AEM.

>[!NOTE]
>
>Pour en savoir plus, consultez [Distribution](/help/overview/architecture.md#content-distribution).

## Méthodes de publication de contenu {#methods-of-publishing-content}

>[!NOTE]
>
>Si vous souhaitez publier du contenu en bloc, utilisez la variable [Processus de publication de l’arborescence de contenu](#publish-content-tree-workflow).
>Cette étape de workflow est conçue spécifiquement pour Cloud Service et peut gérer efficacement de grandes payloads.
>Il n’est pas recommandé de créer votre propre code personnalisé de publication en masse.
>Si vous devez personnaliser pour une raison quelconque, vous pouvez déclencher cette étape de workflow/workflow à l’aide des API de workflow existantes.
>Il est toujours recommandé de ne publier que le contenu qui doit être publié. Et soyez prudent lorsque vous n’essayez pas de publier un grand nombre de contenus, si ce n’est nécessaire. Cependant, il n’existe aucune limite quant à la quantité de contenu que vous pouvez envoyer par le biais du processus Publier l’arborescence de contenu .

### Publication/annulation de publication rapide – Publication/annulation de publication planifiée {#publish-unpublish}

Cette fonctionnalité vous permet de publier immédiatement les pages sélectionnées, sans les options supplémentaires possibles grâce à l’approche Gérer la publication .

Pour plus d’informations, voir [Gestion de la publication](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#manage-publication).

### Heures d’activation et de désactivation – Configuration du déclenchement {#on-and-off-times-trigger-configuration}

Les autres possibilités d’**Heure d’activation** et d’**Heure de désactivation** sont disponibles dans l’[onglet De base des Propriétés de la page](/help/sites-cloud/authoring/fundamentals/page-properties.md#basic).

Pour réaliser la réplication automatique pour cette fonction, activez **Réplication automatique** dans le [Configuration OSGi](/help/implementing/deploying/configuring-osgi.md) **Activation de la configuration de déclenchement désactivée**:

![Configuration OSGi d’activation et de désactivation du déclenchement](/help/operations/assets/replication-on-off-trigger.png)

### Gérer la publication {#manage-publication}

La fonction Gérer la publication offre plus d’options que Publication rapide, ce qui permet d’inclure des pages enfants, de personnaliser les références et de lancer les workflows applicables et d’offrir la possibilité de publier ultérieurement.

L’inclusion des enfants d’un dossier pour l’option &quot;Publier ultérieurement&quot; appelle le workflow Publier l’arborescence de contenu, décrit dans cet article.

Vous trouverez des informations plus détaillées sur la gestion de la publication dans la [documentation sur les principes de publication](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#manage-publication).

### Workflow de publication de l’arborescence de contenu {#publish-content-tree-workflow}

Vous pouvez déclencher une réplication d’arborescence en choisissant **Outils – Workflow – Modèles** et en copiant le modèle de workflow prêt à l’emploi **Publier l’arborescence de contenu**, comme illustré ci-dessous :

![La carte de processus Publier l’arborescence de contenu](/help/operations/assets/publishcontenttreeworkflow.png)

Ne modifiez pas ou n’appelez pas le modèle d’origine. Assurez-vous plutôt de copier le modèle, puis de modifier ou d’appeler cette copie.

Comme tous les workflows, il peut également être appelé via l’API. Pour plus d’informations, voir [Interaction avec les workflows par programmation](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-program-interaction.html?lang=fr#extending-aem).

Vous pouvez également créer un modèle de processus qui utilise la variable `Publish Content Tree` étape du processus :

1. Sur la page d’accueil d’AEM as a Cloud Service, accédez à **Outils – Workflow – Modèles**.
1. Sur la page Modèles de processus, appuyez sur **Créer** dans le coin supérieur droit de l’écran.
1. Ajoutez un titre et un nom à votre modèle. Pour plus d’informations, voir [Création de modèles de workflow](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=fr).
1. Sélectionnez le modèle nouvellement créé dans la liste, puis appuyez sur **Modifier**.
1. Dans la fenêtre suivante, faites un glisser-déposer de l’étape du processus dans le flux de modèle actuel :

   ![Étape du processus](/help/operations/assets/processstep.png)

1. Sélectionnez l’étape Processus dans le flux et sélectionnez **Configurer** en appuyant sur l’icône de clé à molette.
1. Sélectionnez la **Processus** et sélectionnez `Publish Content Tree` dans la liste déroulante, puis cochez la case **Avance du gestionnaire** case à cocher

   ![Activation d’arborescence](/help/operations/assets/newstep.png)

1. Définissez des paramètres supplémentaires dans le champ **Arguments**. Plusieurs arguments séparés par des virgules peuvent être assemblés. Par exemple :

   `enableVersion=true,agentId=publish,includeChildren=true`


   >[!NOTE]
   >
   >Pour obtenir la liste des paramètres, reportez-vous à la section **Paramètres** ci-dessous.

1. Appuyez sur **Terminé** pour enregistrer le modèle de workflow.

**Paramètres**

* `includeChildren` (valeur booléenne, valeur par défaut : `false`). La valeur `false` signifie que seul le chemin est publié ; `true` signifie que les enfants sont également publiés.
* `replicateAsParticipant` (valeur booléenne, valeur par défaut : `false`). S’il est configuré comme `true`, la réplication utilise la balise `userid` du principal qui a exécuté l’étape de participant.
* `enableVersion` (valeur booléenne, valeur par défaut : `true`). Ce paramètre détermine si une nouvelle version est créée lors de la réplication.
* `agentId` (valeur de chaîne, la valeur par défaut signifie que seuls les agents pour la publication sont utilisés). Il est recommandé d’être explicite concernant agentId ; par exemple, attribuez-lui la valeur : publier. Définir l’agent sur `preview` publie sur le service d’aperçu.
* `filters` (valeur string, la valeur par défaut signifie que tous les chemins sont activés). Les valeurs disponibles sont les suivantes :
   * `onlyActivated` - activez uniquement les pages qui ont (déjà) été activées. Cette option agit, en quelque sorte, comme une réactivation.
   * `onlyModified` : activez uniquement les chemins déjà activés et dont la date de modification est postérieure à la date d’activation.
   * Vous pouvez utiliser la commande OU avec une barre verticale « | ». Par exemple, `onlyActivated|onlyModified`.

**Journalisation**

Lorsque l’étape du workflow d’activation de l’arborescence démarre, elle consigne ses paramètres de configuration au niveau du journal INFO. Lorsque les chemins sont activés, une instruction INFO est également consignée.

Une dernière instruction INFO est consignée une fois que l’étape du workflow a répliqué tous les chemins.

Vous pouvez également augmenter le niveau de journalisation des enregistreurs ci-dessous. `com.day.cq.wcm.workflow.process.impl` à DEBUG/TRACE pour obtenir plus d’informations sur le journal.

En cas d’erreur, l’étape du workflow se termine par une `WorkflowException`, qui encapsule l’exception sous-jacente.

Vous trouverez ci-dessous des exemples de journaux générés lors d’un exemple de workflow d’arborescence de contenu de publication :

```
21.04.2021 19:14:55.566 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.treeactivation.TreeActivationWorkflowProcess TreeActivation options: replicateAsParticipant=false(userid=workflow-process-service), agentId=publish, chunkSize=100, filter=, enableVersion=false
```

```
21.04.2021 19:14:58.541 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.ChunkedReplicator closing chunkedReplication-VolatileWorkItem_node1_var_workflow_instances_server60_2021-04-20_brian-tree-replication-test-2_1, 17 paths replicated in 2971 ms
```

**Prise en charge de la reprise**

Le workflow traite le contenu par blocs, chacun représentant un sous-ensemble du contenu complet à publier. Si le workflow est arrêté par le système, il redémarre et traite le bloc qui n’a pas encore été traité. Une instruction de journal indique que le contenu a été repris à partir d’un chemin spécifique.

### API de réplication {#replication-api}

Vous pouvez publier du contenu à l’aide de l’API de réplication présentée dans AEM as a Cloud Service.

Pour plus d’informations, voir [Documentation de l’API](https://javadoc.io/doc/com.adobe.aem/aem-sdk-api/latest/com/day/cq/replication/package-summary.html).

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

**Réplication à l’aide d’agents spécifiques**

Lors de la réplication de ressources, comme dans l’exemple ci-dessus, seuls les agents principaux par défaut sont utilisés. Dans AEM as a Cloud Service, cela signifie uniquement que l’agent appelé &quot;publish&quot;, qui connecte l’auteur au niveau de publication.

Pour prendre en charge la fonctionnalité d’aperçu, un nouvel agent appelé « preview » a été ajouté, qui n’est pas principal par défaut. Cet agent est utilisé pour connecter l’auteur au niveau aperçu. Si vous souhaitez répliquer uniquement par le biais de l’agent d’aperçu, vous devez sélectionner explicitement cet agent d’aperçu au moyen d’une `AgentFilter`.

Voir l’exemple suivant :

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

Si vous ne fournissez pas un tel filtre et n’utilisez que l’agent « publish », l’agent « preview » n’est pas appliqué et l’action de réplication n’affecte pas le niveau d’aperçu.

L’ensemble `ReplicationStatus` d’une ressource n’est modifié que si l’action de réplication comprend au moins un agent principal par défaut. Dans l’exemple ci-dessus, ce flux n’était pas le cas. La réplication utilisait simplement l’agent &quot;preview&quot;. Par conséquent, vous devez utiliser la nouvelle variable `getStatusForAgent()` qui permet d’interroger l’état d’un agent spécifique. Cette méthode fonctionne également pour l’agent « publish ». Elle renvoie une valeur non nulle si une action de réplication a été effectuée à l’aide de l’agent fourni.

### Méthodes d’invalidation de contenu {#invalidating-content}

Vous pouvez directement invalider le contenu en utilisant Sling Content Invalidation (SCD) de l’auteur (méthode préférée) ou en utilisant l’API de réplication pour appeler l’agent de réplication de vidage de publication de Dispatcher. Voir [Mise en cache](/help/implementing/dispatcher/caching.md) pour plus d’informations.

**Limites de capacité de l’API de réplication**

Répliquez moins de 100 chemins à la fois, 500 étant la limite. Au-dessus de la limite, une `ReplicationException` est généré.
Si la logique de votre application ne nécessite pas de réplication atomique, cette limite peut être dépassée en définissant la variable `ReplicationOptions.setUseAtomicCalls` sur false, qui accepte n’importe quel nombre de chemins, mais crée en interne des compartiments pour rester en dessous de cette limite.

La taille du contenu transmis par appel de réplication ne doit pas dépasser `10 MB`. Cette règle inclut les noeuds et les propriétés, mais pas les binaires (les modules de workflow et les modules de contenu sont considérés comme des binaires).


## Résolution des problèmes {#troubleshooting}

Pour résoudre les problèmes de réplication, accédez aux files d’attente de réplication dans l’interface utilisateur web du service d’auteur AEM :

1. Dans le menu AEM, accédez à **Outils > Déploiement > Distribution**
2. Sélectionnez la carte **Publication**.
   ![État](assets/publish-status.png "État")
3. Vérifiez l’état de la file d’attente qui doit être de couleur verte.
4. Vous pouvez tester la connexion au service de réplication.
5. Sélectionnez l’onglet **Logs** (Journaux) qui affiche l’historique des publications de contenu.

![Journaux](assets/publish-logs.png "Journaux")

S’il n’a pas été possible de publier le contenu, l’intégralité de la publication est restaurée à partir du service de publication AEM.
Dans ce cas, la file d’attente principale modifiable affiche un état rouge et doit être examinée pour identifier les éléments qui ont provoqué l’annulation de la publication. En cliquant sur cette file d’attente, les éléments en attente s’affichent, à partir desquels un seul élément ou tous les éléments peuvent être effacés si nécessaire.
