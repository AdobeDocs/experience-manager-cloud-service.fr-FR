---
title: Réplication
description: Découvrez la distribution et le dépannage de la réplication dans AEM as a Cloud Service.
exl-id: c84b4d29-d656-480a-a03a-fbeea16db4cd
feature: Operations
role: Admin
source-git-commit: d6555eebfa13a400f084ef4edefb92b4471adcac
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 34%

---

# Réplication {#replication}

Adobe Experience Manager as a Cloud Service utilise la fonctionnalité de [distribution de contenu Sling](https://sling.apache.org/documentation/bundles/content-distribution.html) pour déplacer le contenu à répliquer vers un service de pipeline s’exécutant sur Adobe Developer, en dehors d’AEM.

>[!NOTE]
>
>Pour en savoir plus, consultez [Distribution](/help/overview/architecture.md#content-distribution).

## Méthodes de publication de contenu {#methods-of-publishing-content}

>[!NOTE]
>
>Si vous souhaitez publier du contenu en masse, créez un workflow à l’aide de l’étape [&#x200B; Workflow d’activation de l’arborescence &#x200B;](/help/operations/tree-replication-workflows.md#tree-activation), qui peut gérer efficacement des payloads volumineux.
>Il n’est pas recommandé de créer votre propre code personnalisé de publication en masse.
>Si, pour une raison quelconque, vous devez effectuer une personnalisation, vous pouvez déclencher un workflow avec cette étape à l’aide des API de workflow existantes.
>Il est toujours recommandé de ne publier que le contenu qui doit être publié. Et soyez prudent en évitant de publier un grand nombre de contenus, si ce n’est pas nécessaire. Cependant, il n’existe aucune limite quant à la quantité de contenu que vous pouvez envoyer par le biais des workflows avec l’étape de workflow d’activation de l’arborescence.

### Publication/dépublication rapide – Publication/dépublication planifiée {#publish-unpublish}

Cette fonction permet de publier immédiatement la ou les pages sélectionnées, sans les options supplémentaires possibles, via l’approche Gérer la publication.

Pour plus d’informations, voir [Gestion de la publication](/help/sites-cloud/authoring/sites-console/publishing-pages.md#manage-publication).

### Heures d’activation et de désactivation – Configuration du déclenchement {#on-and-off-times-trigger-configuration}

Les autres possibilités d’**Heure d’activation** et d’**Heure de désactivation** sont disponibles dans l’[onglet De base des Propriétés de la page](/help/sites-cloud/authoring/sites-console/page-properties.md#basic).

Pour réaliser la réplication automatique de cette fonction, activez **Réplication automatique** dans la **Configuration d’activation et de désactivation du déclenchement** de la [configuration OSGi](/help/implementing/deploying/configuring-osgi.md) :

![Configuration OSGi d’activation et de désactivation du déclenchement](/help/operations/assets/replication-on-off-trigger.png)

### Gérer la publication {#manage-publication}

La méthode Gérer la publication propose plus d’options que Publication rapide, dont la possibilité d’inclure des pages enfants, de personnaliser les références ou encore de lancer n’importe quel workflow applicable. Elle offre également la possibilité de publier la page à une date ultérieure.

L’inclusion des enfants d’un dossier pour l’option « Publier ultérieurement » appelle le workflow Publier l’arborescence de contenu, décrit dans [Workflows de réplication d’arborescence](/help/operations/tree-replication-workflows.md#publish-content-tree-workflow).

Vous trouverez des informations plus détaillées sur la gestion de la publication dans la [documentation sur les principes de publication](/help/sites-cloud/authoring/sites-console/publishing-pages.md#manage-publication).

Pour répliquer des hiérarchies de contenu profondes en bloc, utilisez une approche basée sur des workflows. Voir [Workflows de réplication de l’arborescence](/help/operations/tree-replication-workflows.md) pour l’étape de workflow recommandée d’activation de l’arborescence, les paramètres de configuration et les conseils de surveillance. Le workflow obsolète Publier l’arborescence de contenu y est également documenté à titre de référence.

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
// if you need to get the status for more than 1 resource at once, this approach is more performant
Map<String,ReplicationStatus> allStatus = replicationStatusProvider.getBatchReplicationStatus(enResource,deResource);
```

**Agents de réplication**

AEM as a Cloud Service fournit deux agents de réplication prédéfinis qui acheminent le contenu de l’auteur vers un niveau cible via la distribution de contenu Sling :

* **publication** — Réplique le contenu activé au niveau de publication en direct. Cet agent est activé par défaut et est utilisé lorsque vous effectuez une publication à partir de l’interface utilisateur, des workflows ou de l’API de réplication, sauf indication contraire.
* **preview** — Réplique le contenu vers le niveau d’aperçu afin que les auteurs puissent examiner les modifications avant leur mise en ligne. Cet agent n&#39;est pas activé par défaut.

Vous pouvez afficher et surveiller les deux agents à partir de **Outils** > **Déploiement** > **Distribution** :

![Agents de distribution affichant les agents de publication et &#x200B;](/help/operations/assets/replication-agents.png " prévisualisation")

La sélection d’une carte d’agent ouvre son statut, ses journaux et les [détails de la file d’attente](#replication-queues).

**Réplication à l’aide d’agents spécifiques**

Lorsque vous répliquez avec l’API, comme illustré ci-dessus, seuls les agents activés par défaut sont utilisés ; dans AEM as a Cloud Service, il s’agit uniquement de **publication**. Pour répliquer exclusivement vers le niveau d’aperçu, transmettez une `AgentFilter` qui sélectionne l’agent d’aperçu :

Considérez l’exemple suivant :

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

Si vous répliquez sans `AgentFilter`, seule la variable **publier** est utilisée et le niveau d’aperçu n’est pas affecté.

La `ReplicationStatus` globale d’une ressource est mise à jour uniquement lorsque la réplication comprend au moins un agent activé par défaut. Dans l’exemple ci-dessus, seul le **preview** a été utilisé, donc `ReplicationStatus.isActivated` reste `false`. Utilisez des `getStatusForAgent()` pour vérifier le statut d’un agent spécifique, par exemple, `getStatusForAgent("preview")` après une réplication en prévisualisation uniquement ou `getStatusForAgent("publish")` pour le niveau de publication actif.

### Méthodes d’invalidation de contenu {#invalidating-content}

Vous pouvez directement invalider le contenu à l’aide de l’invalidation du contenu Sling (SCD) de l’auteur ou de l’autrice (méthode préférée) ou en utilisant l’API de réplication pour appeler l’agent de réplication de vidage du Dispatcher de publication. Reportez-vous à la page [Mise en cache](/help/implementing/dispatcher/caching.md) pour plus d’informations.

**Limites de capacité de l’API de réplication**

Répliquez moins de 100 chemins à la fois, 500 étant la limite. Au-dessus de la limite, une `ReplicationException` est générée.
Si la logique de votre application ne nécessite pas de réplication atomique, cette limite peut être dépassée en définissant la `ReplicationOptions.setUseAtomicCalls` sur false. Ainsi, un nombre quelconque de chemins d’accès est accepté, mais des compartiments sont créés en interne pour rester au-dessous de cette limite.

La taille du contenu transmis par appel de réplication ne doit pas dépasser `10 MB`. Cette règle inclut les nœuds et les propriétés, mais pas les fichiers binaires (les modules de workflow et les modules de contenu sont considérés comme des fichiers binaires).


## Files d’attente de réplication {#replication-queues}

Chaque agent de réplication affiche deux files d’attente de réplication. AEM as a Cloud Service n’affiche plus de file d’attente distincte pour chaque capsule de publication, le niveau de publication étant automatiquement mis à l’échelle, les files d’attente par capsule ajoutent de la complexité, sans avantage pratique. Le statut de la file d&#39;attente est consolidé comme suit :

* **persisted** — La modification est stockée de manière durable au niveau de publication. Une fois qu’un élément a effacé cette file d’attente, le contenu est conservé ; les instances de publication atteignent un état cohérent au fil du temps.
* **entièrement publié** — La modification est active sur toutes les capsules de publication et le cache de Dispatcher est effacé pour les chemins affectés. Une fois qu’un élément a effacé cette file d’attente, les visiteurs reçoivent le contenu mis à jour.

### Surveiller les files d’attente de réplication {#monitor-replication-queues}

1. Dans AEM [navigation globale](/help/sites-cloud/authoring/basic-handling.md#global-navigation), accédez à **Outils** > **Déploiement**.

   ![Accédez à Distribution à partir de la navigation Outils](/help/operations/assets/replication-agent-navigation.png "Distribution")

1. Sélectionnez **Distribution**, puis ouvrez la vignette de l’agent **publication** ou **aperçu**.

1. Dans l’onglet **Statut**, vérifiez que chaque file d’attente présente un statut intègre. Consultez **Éléments en attente** pour le travail en attente de traitement et **Dernier élément traité** pour l’activité récente.

   ![Files d’attente de réplication affichant les files d’attente &#x200B;](/help/operations/assets/replication-queues.png " réplication persistantes et entièrement publiées")

1. Sélectionnez **Tester la connexion** pour vérifier que l’agent peut accéder au service de distribution.
1. Sélectionnez l’onglet **Logs** pour afficher l’historique des publications de contenu.

   ![Journaux &#x200B;](/help/operations/assets/publish-logs.png " réplication")

## Résolution des problèmes {#troubleshooting}

Si le contenu ne peut pas être publié, la publication est annulée à partir du service de publication AEM. Utilisez [Surveiller les files d’attente de réplication](#monitor-replication-queues) pour ouvrir l’onglet de l’agent **Statut** et identifier la file d’attente concernée.

Lorsqu’une file d’attente affiche un statut rouge, passez en revue ses éléments en attente pour déterminer ce qui a provoqué l’échec. Sélectionnez la file d’attente pour afficher les éléments en attente, puis effacez des éléments individuels ou l’ensemble de la file d’attente si nécessaire.
