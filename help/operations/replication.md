---
title: Réplication
description: Distribution et dépannage de la réplication.
exl-id: c84b4d29-d656-480a-a03a-fbeea16db4cd
translation-type: tm+mt
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

### Processus de l’arborescence de contenu de publication {#publish-content-tree-workflow}

Vous pouvez déclencher une réplication d&#39;arborescence en choisissant **Outils - Processus - Modèles** et en copiant le modèle de flux de travaux prêt à l&#39;emploi **Publier l&#39;arborescence du contenu**, comme illustré ci-dessous :

![](/help/operations/assets/publishcontenttreeworkflow.png)

Ne modifiez pas ou n’appelez pas le modèle d’origine. Assurez-vous plutôt de copier d’abord le modèle, puis de modifier ou d’appeler cette copie.

Comme tous les workflows, il peut également être appelé via l’API. Pour plus d’informations, voir [Interaction avec des Workflows par programmation](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-program-interaction.html?lang=en#extending-aem).

Vous pouvez également y parvenir en créant un modèle de processus qui utilise l&#39;étape de processus `Publish Content Tree` :

1. Depuis la page d&#39;accueil de l&#39;AEM en tant que Cloud Service, accédez à **Outils - Processus - Modèles**
1. Dans la page Modèles de processus, appuyez sur **Créer** dans le coin supérieur droit de l’écran.
1. Ajoutez un titre et un nom à votre modèle. Pour plus d’informations, voir [Création de modèles de flux de travail](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html).
1. Sélectionnez le modèle nouvellement créé dans la liste, puis appuyez sur **Modifier**.
1. Dans la fenêtre suivante, faites glisser et déposez l’étape de processus dans le flux de modèle actuel :

   ![Étape du processus](/help/operations/assets/processstep.png)

1. Cliquez sur l’étape Processus dans le flux et sélectionnez **Configurer** en appuyant sur l’icône de clé à molette.
1. Cliquez sur l&#39;onglet **Processus** et sélectionnez `Publish Content Tree` dans la liste déroulante.

   ![Treactivation](/help/operations/assets/newstep.png)

1. Définissez d’autres paramètres dans le champ **Arguments**. Plusieurs arguments séparés par des virgules peuvent faire l’objet d’une chaîne. Par exemple :

   `enableVersion=true,agentId=publish`


   >[!NOTE]
   >
   >Pour la liste des paramètres, voir la section **Paramètres** ci-dessous.

1. Appuyez sur **Terminé** pour enregistrer le modèle Workflow.

**Paramètres**

* `replicateAsParticipant` (valeur booléenne, par défaut :  `false`). Si elle est configurée comme `true`, la réplication utilise `userid` du principal qui a exécuté l&#39;étape du participant.
* `enableVersion` (valeur booléenne, par défaut :  `true`). Ce paramètre détermine si une nouvelle version est créée lors de la réplication.
* `agentId` (valeur de chaîne, par défaut, tous les agents activés sont utilisés).
* `filters` (valeur de chaîne, par défaut, tous les chemins sont activés). Les valeurs disponibles sont les suivantes :
   * `onlyActivated` - seuls les chemins qui ne sont pas marqués comme activés seront activés.
   * `onlyModified` - activer uniquement les chemins déjà activés et dont la date de modification est postérieure à la date d&#39;activation.
   * La valeur ci-dessus peut être OUed avec une barre verticale &quot;|&quot;. Par exemple, `onlyActivated|onlyModified`.

**Journalisation**

Lorsque l&#39;activation d&#39;arborescence des flux de travaux débuts, elle consigne ses paramètres de configuration au niveau de la journalisation INFO. Lorsque les chemins sont activés, une instruction INFO est également consignée.

Une instruction INFO finale sera alors consignée après la réplication de tous les chemins par l&#39;étape du flux de travail.

De plus, vous pouvez augmenter le niveau de journalisation des journaux sous `com.day.cq.wcm.workflow.process.impl` en DEBUG/TRACE pour obtenir encore plus d&#39;informations de journalisation.

En cas d’erreur, l’étape du flux de travail se termine par `WorkflowException`, qui encapsule l’exception sous-jacente.

Vous trouverez ci-dessous des exemples de journaux générés au cours d’un exemple de flux de travaux d’arborescence de contenu de publication :

```
21.04.2021 19:14:55.566 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.treeactivation.TreeActivationWorkflowProcess TreeActivation options: replicateAsParticipant=false(userid=workflow-process-service), agentId=publish, chunkSize=100, filter=, enableVersion=false
```

```
21.04.2021 19:14:58.541 [cm-p123-e456-aem-author-797aaaf-wkkqt] *INFO* [JobHandler: /var/workflow/instances/server60/2021-04-20/brian-tree-replication-test-2_1:/content/wknd/us/en/adventures] com.day.cq.wcm.workflow.process.impl.ChunkedReplicator closing chunkedReplication-VolatileWorkItem_node1_var_workflow_instances_server60_2021-04-20_brian-tree-replication-test-2_1, 17 paths replicated in 2971 ms
```

**Prise en charge de la reprise**

Le processus traite le contenu en blocs, chacun représentant un sous-ensemble du contenu complet à publier. Si, pour une raison quelconque, le processus est arrêté par le système, il redémarre et traite le bloc qui n&#39;a pas encore été traité. Une instruction de journal indique que le contenu a été repris à partir d&#39;un chemin d&#39;accès spécifique.

## Dépannage {#troubleshooting}

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
