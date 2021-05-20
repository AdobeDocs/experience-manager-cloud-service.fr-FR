---
title: Réplication
description: Distribution et dépannage de la réplication.
exl-id: c84b4d29-d656-480a-a03a-fbeea16db4cd
source-git-commit: eb92c66f2b9e8e6ec859114da2de049747ec251e
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 39%

---

# Réplication {#replication}

Adobe Experience Manager as a Cloud Service utilise la fonctionnalité de [distribution de contenu Sling](https://sling.apache.org/documentation/bundles/content-distribution.html) pour déplacer le contenu à répliquer vers un service de pipeline s’exécutant sur Adobe I/O, en dehors d’AEM.

>[!NOTE]
>
>Pour en savoir plus, consultez [Distribution](/help/core-concepts/architecture.md#content-distribution).

## Méthodes de publication de contenu {#methods-of-publishing-content}

### Publication/annulation de publication rapide – Publication/annulation de publication planifiée {#publish-unpublish}

Ces fonctionnalités standard d’AEM pour les auteurs sont inchangées avec AEM Cloud Service.

### Heures d’activation et de désactivation – Configuration du déclenchement {#on-and-off-times-trigger-configuration}

Les autres possibilités d’**Heure d’activation** et d’**Heure de désactivation** sont disponibles dans l’[onglet De base des Propriétés de la page](/help/sites-cloud/authoring/fundamentals/page-properties.md#basic).

Pour réaliser la réplication automatique dans ce cas, vous devez activer **Auto Replicate** (Réplication automatique) dans **On Off Trigger Configuration** (Configuration d’activation et de désactivation du déclenchement) de la [configuration OSGi](/help/implementing/deploying/configuring-osgi.md) :

![Configuration OSGi d’activation et de désactivation du déclenchement](/help/operations/assets/replication-on-off-trigger.png)

### Activation d’une arborescence {#tree-activation}

Pour exécuter une activation d’arborescence :

1. Dans le menu Accueil AEM, accédez à **Outils > Déploiement > Distribution**.
2. Sélectionnez la carte **forwardPublisher**.
3. Une fois dans l’interface utilisateur de la console web forwardPublisher, sélectionnez **Distribute** (Distribuer).

   ![Distribuer](assets/distribute.png "Distribuer")
4. Sélectionnez le chemin dans l’explorateur de chemins d’accès, choisissez d’ajouter un nœud, une arborescence ou supprimez-les, si nécessaire, puis sélectionnez **Submit** (Envoyer).

### Processus de publication de l’arborescence de contenu {#publish-content-tree-workflow}

Vous pouvez déclencher une réplication d’arborescence en choisissant **Outils - Processus - Modèles** et en copiant le modèle de workflow d’usine **Publier l’arborescence de contenu**, comme illustré ci-dessous :

![](/help/operations/assets/publishcontenttreeworkflow.png)

Ne modifiez pas ou n’appelez pas le modèle d’origine. Veillez plutôt à copier le modèle, puis à le modifier ou à l’appeler.

Comme tous les workflows, il peut également être appelé via l’API. Pour plus d’informations, voir [Interaction avec les workflows par programmation](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-program-interaction.html?lang=en#extending-aem).

Vous pouvez également y parvenir en créant un modèle de processus qui utilise l’étape de processus `Publish Content Tree` :

1. Sur la page d’accueil AEM as a Cloud Service, accédez à **Outils - Workflow - Modèles**
1. Sur la page Modèles de processus , appuyez sur **Créer** dans le coin supérieur droit de l’écran.
1. Ajoutez un titre et un nom à votre modèle. Pour plus d’informations, voir [Création de modèles de processus](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html)
1. Sélectionnez le modèle nouvellement créé dans la liste, puis appuyez sur **Modifier**.
1. Dans la fenêtre suivante, placez l’étape du processus dans le flux de modèle actuel :

   ![Étape du processus](/help/operations/assets/processstep.png)

1. Cliquez sur l’étape Processus dans le flux et sélectionnez **Configurer** en appuyant sur l’icône de clé à molette.
1. Cliquez sur l’onglet **Processus** et sélectionnez `Publish Content Tree` dans la liste déroulante.

   ![Treeactivation](/help/operations/assets/newstep.png)

1. Définissez des paramètres supplémentaires dans le champ **Arguments**. Plusieurs arguments séparés par des virgules peuvent être associés. Par exemple :

   `enableVersion=true,agentId=publish`


   >[!NOTE]
   >
   >Pour obtenir la liste des paramètres, reportez-vous à la section **Paramètres** ci-dessous.

1. Appuyez sur **Done** (Terminé) pour enregistrer le modèle Workflow.

**Paramètres**

* `replicateAsParticipant` (valeur booléenne, valeur par défaut :  `false`). S’il est configuré comme `true`, la réplication utilise la balise `userid` de l’entité qui a exécuté l’étape de participant.
* `enableVersion` (valeur booléenne, valeur par défaut :  `true`). Ce paramètre détermine si une nouvelle version est créée lors de la réplication.
* `agentId` (valeur de chaîne, la valeur par défaut signifie que tous les agents activés sont utilisés).
* `filters` (valeur de chaîne, valeur par défaut, tous les chemins sont activés). Les valeurs disponibles sont les suivantes :
   * `onlyActivated` : seuls les chemins qui ne sont pas marqués comme activés seront activés.
   * `onlyModified` - activez uniquement les chemins déjà activés et dont la date de modification est postérieure à la date d’activation.
   * Vous pouvez utiliser la commande OU avec une barre verticale &quot;|&quot;. Par exemple, `onlyActivated|onlyModified`.

**Journalisation**

Lorsque l’étape du workflow d’activation de l’arborescence démarre, elle consigne ses paramètres de configuration au niveau du journal INFO. Lorsque les chemins sont activés, une instruction INFO est également consignée.

Une dernière instruction INFO sera alors consignée une fois que l’étape du workflow aura répliqué tous les chemins.

De plus, vous pouvez augmenter le niveau de journalisation des enregistreurs sous `com.day.cq.wcm.workflow.process.impl` en DEBUG/TRACE pour obtenir encore plus d’informations sur le journal.

En cas d’erreur, l’étape du workflow s’arrête avec une balise `WorkflowException` qui enveloppe l’exception sous-jacente.

Vous trouverez ci-dessous des exemples de journaux générés lors d’un exemple de workflow d’arborescence de contenu de publication :

```
21.04.2021 19:14:55.566 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.treeactivation.TreeActivationWorkflowProcess TreeActivation options: replicateAsParticipant=false(userid=workflow-process-service), agentId=publish, chunkSize=100, filter=, enableVersion=false
```

```
21.04.2021 19:14:58.541 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.ChunkedReplicator closing chunkedReplication-VolatileWorkItem_node1_var_workflow_instances_server60_2021-04-20_brian-tree-replication-test-2_1, 17 paths replicated in 2971 ms
```

**Prise en charge de la reprise**

Le workflow traite le contenu par blocs, chacun représentant un sous-ensemble du contenu complet à publier. Si, pour une raison quelconque, le workflow est arrêté par le système, il redémarre et traite le bloc qui n’a pas encore été traité. Une instruction de journal indique que le contenu a été repris à partir d’un chemin spécifique.

## Résolution des problèmes {#troubleshooting}

Pour résoudre les problèmes de réplication, accédez aux files d’attente de réplication dans l’interface utilisateur web du service d’auteur AEM :

1. Dans le menu Accueil AEM, accédez à **Outils > Déploiement > Distribution**.
2. Sélectionnez la carte **forwardPublisher**.
   ![État](assets/status.png "État")
3. Vérifiez l’état de la file d’attente qui doit être de couleur verte.
4. Vous pouvez tester la connexion au service de réplication.
5. Sélectionnez l’onglet **Logs** (Journaux) qui affiche l’historique des publications de contenu.

![Journaux](assets/logs.png "Journaux")

S’il n’a pas été possible de publier le contenu, l’intégralité de la publication est restaurée à partir du service de publication AEM.
Dans ce cas, les files d’attente doivent être examinées afin d’identifier les éléments qui ont provoqué l’annulation de la publication. Suite à un clic sur une file d’attente signalée par un état rouge, celle contenant des éléments en attente s’affiche. Il est possible d’y effacer un ou tous les éléments, si nécessaire.
