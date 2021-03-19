---
title: Configuration de la synchronisation de Live Copies
description: Découvrez les puissantes options de synchronisation Live Copy disponibles et comment les configurer et les personnaliser en fonction des besoins de votre projet.
feature: Gestionnaire de plusieurs sites
role: Administrator
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '2358'
ht-degree: 33%

---


# Configuration de la synchronisation de Live Copies {#configuring-live-copy-synchronization}

Adobe Experience Manager fournit un certain nombre de configurations de synchronisation prêtes à l’emploi. Avant d’utiliser les Live Copies, tenez compte des points suivants pour définir comment et quand les Live Copies sont synchronisées avec leur contenu source.

1. Déterminer si les configurations de déploiement existantes répondent à vos besoins
1. Si les configurations de déploiement existantes ne le font pas, décidez si vous devez créer les vôtres.
1. Spécifiez les configurations de déploiement à utiliser pour vos Live Copies.

## Configurations du déploiement installées et personnalisées {#installed-and-custom-rollout-configurations}

Cette section contient des informations sur les configurations du déploiement installées et les actions de synchronisation qu’elles utilisent, ainsi que sur la création de configurations personnalisées, si nécessaire.

>[!CAUTION]
>
>Il n&#39;est pas recommandé de mettre à jour ou de modifier une configuration de déploiement prête à l&#39;emploi **mais**. Si une action active personnalisée est requise, elle doit être ajoutée dans une configuration de déploiement personnalisée.

### Déclencheurs de déploiement {#rollout-triggers}

Chaque configuration du déploiement utilise un déclencheur qui entraîne la survenue du déploiement. Il peut s’agir de l’un des déclencheurs suivants :

* **Au déploiement** : La  **** commande de déploiement est utilisée sur la page d’impression bleue ou la commande de  **** synchronisation est utilisée sur la page Live Copy.
* **En cas de modification** : la page source est modifiée.
* **En cas d’activation** : la page source est activée.
* **En cas de désactivation** : la page source est désactivée.

>[!NOTE]
>
>L&#39;utilisation du déclencheur **On Modification** peut avoir un impact sur les performances. Pour plus d’informations, voir [Meilleures pratiques MSM](best-practices.md#onmodify).

### Configurations du déploiement {#rollout-configurations}

Le tableau suivant liste les configurations de déploiement prêtes à l&#39;emploi avec AEM. Le tableau contient les actions de déclenchement et de synchronisation de chaque configuration du déploiement. Si les actions de configuration du déploiement installées ne répondent pas à vos exigences, vous pouvez [créer une autre configuration du déploiement](#creating-a-rollout-configuration).

| Nom | Description | Déclencheur | [Actions de synchronisation](#synchronization-actions) |
|---|---|---|---|
| Configuration de déploiement standard | Configuration du déploiement standard qui permet de démarrer le processus de déploiement à partir d’un déclencheur de déploiement et d’actions d’exécutions : créer, mettre à jour, supprimer le contenu et trier les nœuds enfants | En cas de déploiement | `contentUpdate`<br>`contentCopy`<br>`contentDelete`<br>`referencesUpdate`<br>`productUpdate`<br>`orderChildren` |
| Activer au moment de l’activation du plan directeur | Publie la Live Copy lorsque la source est publiée | En cas d’activation | `targetActivate` |
| Désactiver au moment de la désactivation du plan directeur | Désactive la Live Copy lorsque la source est désactivée | Lors de la désactivation | `targetDeactivate` |
| Pousser au moment de la modification | Envoie le contenu à la Live Copy lorsque la source est modifiée<br>Utilisez cette configuration de déploiement avec parcimonie car elle utilise le déclencheur Lors de la modification. | En cas de modification | `contentUpdate`<br>`contentCopy`<br>`contentDelete`<br>`referencesUpdate`<br>`orderChildren` |
| Pousser au moment de la modification (peu profond) | Envoie le contenu à la copie dynamique lors de la modification de la page du plan directeur, sans mettre à jour les références (par exemple pour les copies superficielles)<br>Utilisez cette configuration de déploiement avec parcimonie car elle utilise le déclencheur Lors de la modification. | En cas de modification | `contentUpdate`<br>`contentCopy`<br>`contentDelete`<br>`orderChildren` |
| Convertir le lancement | Configuration de déploiement standard pour la promotion des pages de lancement. | En cas de déploiement | `contentUpdate`<br>`contentCopy`<br>`contentDelete`<br>`referencesUpdate`<br>`orderChildren`<br>`markLiveRelationship` |

### Actions de synchronisation {#synchronization-actions}

Le tableau suivant liste les actions de synchronisation prêtes à l’emploi avec AEM.

<!--If the installed actions do not meet your requirements, you can [Create a New Synchronization Action](/help/sites-developing/extending-msm.md#creating-a-new-synchronization-action).-->

| Nom de l’action | Description | Propriétés |
|---|---|---|
| `contentCopy` | Lorsque les noeuds de la source n’existent pas dans Live Copy, cette action copie les noeuds dans Live Copy. [Configurez le service  **Action de copie de contenu MSM de** ](#excluding-properties-and-node-types-from-synchronization) CQ afin de spécifier les types de noeud, les éléments de paragraphe et les propriétés de page à exclure. |  |
| `contentDelete` | Cette action supprime les noeuds de Live Copy qui n’existent pas sur la source. [Configurez le service de suppression  **d’action de contenu MSM** ](#excluding-properties-and-node-types-from-synchronization) CQ pour spécifier les types de noeud, les éléments de paragraphe et les propriétés de page à exclure. |  |
| `contentUpdate` | Cette action met à jour le contenu Live Copy avec les modifications de la source. [Configurez le service  **Action de mise à jour de contenu MSM de** ](#excluding-properties-and-node-types-from-synchronization) CQ afin de spécifier les types de noeud, les éléments de paragraphe et les propriétés de page à exclure. |  |
| `editProperties` | Cette action modifie les propriétés de la Live Copy. La propriété `editMap` détermine quelles propriétés sont modifiées et leur valeur. La valeur de la propriété `editMap` doit utiliser le format suivant : <br>`[property_name_n]#[current_value]#[new_value]`<br>`current_value` et `new_value` sont des expressions régulières et `n` est un entier incrémenté.<br>Par exemple, tenez compte de la valeur suivante pour  `editMap`:<br>`sling:resourceType#/(contentpage` ‖ `homepage)#/mobilecontentpage,cq:template#/contentpage#/mobilecontentpage`<br>Cette valeur modifie les propriétés des noeuds Live Copy comme suit :<br>Les  `sling:resourceType` propriétés qui sont soit définies sur  `contentpage` ou sur lesquelles  `homepage` sont définies sur .`mobilecontentpage`<br>Les  `cq:template` propriétés qui sont définies sur  `contentpage` sont définies sur  `mobilecontentpage`. | `editMap: (String)` identifie la propriété, la valeur actuelle et la nouvelle valeur. Voir la description pour plus d’informations. |
| `notify` | Cette action envoie un événement de page indiquant que la page a été déployée. Pour être averti, un utilisateur doit d’abord s’abonner aux événements de déploiement. |  |
| `orderChildren` | Cette action commande les noeuds enfants en fonction de l&#39;ordre du plan. |  |
| `referencesUpdate` | Cette action de synchronisation met à jour les références sur Live Copy.<br>Il recherche les chemins dans les pages Live Copy qui pointent vers une ressource du plan. Lorsqu’elle est trouvée, elle met à jour le chemin d’accès pour qu’il pointe vers la ressource associée dans Live Copy. Les références qui comportent des cibles en dehors du plan directeur ne sont pas modifiées. <br>[Configurez le service de mise à jour des références MSM de  **CQ** ](#excluding-properties-and-node-types-from-synchronization) afin de spécifier les types de noeud, les éléments de paragraphe et les propriétés de page à exclure. |  |
| `targetVersion` | Cette action crée une version de Live Copy.<br>Cette action doit être la seule action de synchronisation incluse dans une configuration du déploiement. |  |
| `targetActivate` | Cette action active la Live Copy.<br>Cette action doit être la seule action de synchronisation incluse dans une configuration du déploiement. |  |
| `targetDeactivate` | Cette action désactive la Live Copy.<br>Cette action doit être la seule action de synchronisation incluse dans une configuration du déploiement. |  |
| `workflow` | Cette action début le flux de travail défini par la propriété cible (pour les pages uniquement) et prend la Live Copy en charge.<br>Le chemin d’accès à la cible est le chemin d’accès du noeud du modèle. | `target: (String)` est le chemin d’accès au modèle de processus. |
| `mandatory` | Cette action définit l’autorisation de plusieurs ACL sur la page Live Copy sur lecture seule pour un groupe d’utilisateurs spécifique. Les listes de contrôle d’accès suivantes sont configurées : <br>`ActionSet.ACTION_NAME_REMOVE`<br>`ActionSet.ACTION_NAME_SET_PROPERTY`<br>`ActionSet.ACTION_NAME_ACL_MODIFY`<br>Utilisez cette action uniquement pour les pages. | `target: (String)` est l’identifiant du groupe pour lequel vous définissez des autorisations. |
| `mandatoryContent` | Cette action définit l’autorisation de plusieurs ACL sur la page Live Copy sur lecture seule pour un groupe d’utilisateurs spécifique. Les listes de contrôle d’accès suivantes sont configurées : <br>`ActionSet.ACTION_NAME_SET_PROPERTY`<br>`ActionSet.ACTION_NAME_ACL_MODIFY`<br>Utilisez cette action uniquement pour les pages. | `target: (String)` est l’identifiant du groupe pour lequel vous définissez des autorisations. |
| `mandatoryStructure` | Cette action définit l’autorisation de l’ACL `ActionSet.ACTION_NAME_REMOVE` sur la page Live Copy sur lecture seule pour un groupe d’utilisateurs spécifique.<br>Utilisez cette action uniquement pour des pages. | `target: (String)` est l’identifiant du groupe pour lequel vous définissez des autorisations. |
| `VersionCopyAction` | Si la page source/prototype a été publiée au moins une fois, cette action crée une page Live Copy à l&#39;aide de la version publiée. Remarque : cette action n’est disponible que pour la création d’une page Live Copy basée sur une page source publiée, et non pour la mise à jour d’une page Live Copy existante. |  |
| `PageMoveAction` | Le `PageMoveAction` s&#39;applique lorsqu&#39;une page a été déplacée dans le plan.<br>L’action copie plutôt que de déplacer la page Live Copy (associée) de l’emplacement avant le déplacement vers l’emplacement suivant.<br>La page Live Copy  `PageMoveAction` ne change pas à l’emplacement avant le déplacement. Par conséquent, pour les configurations de déploiement consécutives, il a l&#39;état d&#39;une relation active sans schéma.<br>[**** Configurez le service CQ MSM Page Move Action](#excluding-properties-and-node-types-from-synchronization) pour spécifier les types de nœuds, les éléments de paragraphe et les propriétés de page à exclure.<br>Cette action doit être la seule action de synchronisation incluse dans une configuration du déploiement. | Définissez `prop_referenceUpdate: (Boolean)` sur true (par défaut) pour mettre à jour les références. |
| `markLiveRelationship` | Cette action indique qu’il existe une relation dynamique pour le contenu créé au lancement. |  |

<!--
### Creating a Rollout Configuration {#creating-a-rollout-configuration}

You can [create a rollout configuration](/help/sites-developing/extending-msm.md#creating-a-new-rollout-configuration) when the installed rollout configurations do not meet your application requirements by performing the following steps.

1. [Create the rollout configuration](/help/sites-developing/extending-msm.md#create-the-rollout-configuration).
1. [Add synchronization actions to the rollout configuration](/help/sites-developing/extending-msm.md#add-synchronization-actions-to-the-rollout-configuration).

The new rollout configuration is then available to you when configuring rollout configurations on a blueprint or Live Copy page.
-->

### Exclusion des propriétés et des types de nœuds de la synchronisation {#excluding-properties-and-node-types-from-synchronization}

Vous pouvez configurer différents services OSGi qui prennent en charge les actions de synchronisation correspondantes afin qu’ils n’affectent pas des types de nœuds et des propriétés spécifiques. Par exemple, de nombreuses propriétés et sous-noeuds liés au fonctionnement interne de l’AEM ne doivent pas être inclus dans une Live Copy. Seul le contenu pertinent pour l’utilisateur de la page doit être copié.

Lorsque vous utilisez AEM, plusieurs méthodes permettent de gérer les paramètres de configuration pour ces services. Voir [Configuration d’OSGi](/help/implementing/deploying/configuring-osgi.md) pour avoir plus de détails et connaître les pratiques recommandées.

Le tableau ci-dessous répertorie les actions de synchronisation pour lesquelles vous pouvez spécifier les nœuds à exclure. Le tableau contient le nom des services à configurer à l’aide de la console web et le PID pour la configuration à l’aide d’un nœud de référentiel.

| Action de synchronisation | Nom du service dans la console Web | Service PID |
|---|---|---|
| `contentCopy` | Action de copie de contenu MSM CQ | `com.day.cq.wcm.msm.impl.actions.ContentCopyActionFactory` |
| `contentDelete` | Action de suppression de contenu MSM CQ | `com.day.cq.wcm.msm.impl.actions.ContentDeleteActionFactory` |
| `contentUpdate` | Action de mise à jour du contenu MSM CQ | `com.day.cq.wcm.msm.impl.actions.ContentUpdateActionFactory` |
| `PageMoveAction` | Action de déplacement de page MSM CQ | `com.day.cq.wcm.msm.impl.actions.PageMoveActionFactory` |
| `referencesUpdate` | Action de mise à jour des références MSM CQ | `com.day.cq.wcm.msm.impl.actions.ReferencesUpdateActionFactory` |

Le tableau ci-dessous décrit les propriétés que vous pouvez configurer :

| Propriété de la console Web | OSGi, propriété | Description |
|---|---|---|
| Types de noeud exclus | `cq.wcm.msm.action.excludednodetypes` | Expression régulière qui correspond aux types de noeud à exclure de l’action de synchronisation |
| Éléments de paragraphe exclus | `cq.wcm.msm.action.excludedparagraphitems` | Expression régulière qui correspond aux éléments de paragraphe à exclure de l’action de synchronisation |
| Propriétés de page exclues | `cq.wcm.msm.action.excludedprops` | Expression régulière qui correspond aux propriétés de page à exclure de l’action de synchronisation |
| Types de noeuds mixtes ignorés | `cq.wcm.msm.action.ignoredMixin` | Expression régulière qui correspond aux noms des types de noeud de mixin à exclure de l&#39;action de synchronisation (disponible uniquement pour l&#39;action `contentUpdate`) |

#### CQ MSM Content Update Action – Exclusions {#cq-msm-content-update-action-exclusions}

Différents types de nœuds et propriétés sont exclus par défaut. Ils sont définis dans la configuration OSGi du service **CQ MSM Content Update Action** sous **Propriétés de page exclues**.

Par défaut, les propriétés correspondant aux expressions régulières ci-dessous sont exclues (c’est-à-dire non mises à jour) lors du déploiement :

![Régimes d’exclusion Live Copy](../assets/live-copy-exclude.png)

Vous pouvez modifier les expressions en définissant la liste d’exclusions, au besoin.

Par exemple, si vous souhaitez que le **titre** de la page soit inclus dans les modifications prises en compte pour le déploiement, supprimez `jcr:title` des exclusions. Par exemple, dans l’expression régulière :

`jcr:(?!(title)$).*`

### Configuration de la synchronisation pour la mise à jour des références {#configuring-synchronization-for-updating-references}

Vous pouvez configurer différents services OSGi qui prennent en charge les actions de synchronisation correspondantes associées à la mise à jour des références.

Lorsque vous utilisez AEM, plusieurs méthodes permettent de gérer les paramètres de configuration pour ces services. Voir [Configuration d’OSGi](/help/implementing/deploying/configuring-osgi.md) pour avoir plus de détails et connaître les pratiques recommandées.

Le tableau ci-dessous répertorie les actions de synchronisation pour lesquelles vous pouvez spécifier la mise à jour des références. Le tableau contient le nom des services à configurer à l’aide de la console web et le PID pour la configuration à l’aide d’un nœud de référentiel.

| Propriété de la console Web | OSGi, propriété | Description |
|---|---|---|
| Référence de mise à jour sur les LiveCopies imbriquées | `cq.wcm.msm.impl.action.referencesupdate.prop_updateNested` | Sélectionnez cette option dans la console Web ou définissez cette propriété booléenne sur `true` en utilisant la configuration du référentiel pour remplacer les références qui cible toute ressource se trouvant dans la branche de Live Copy la plus élevée. Uniquement disponible pour l&#39;action `referencesUpdate`. |
| Mettre à jour les pages de référence | `cq.wcm.msm.impl.actions.pagemove.prop_referenceUpdate` | Sélectionnez cette option dans la console Web ou définissez cette propriété booléenne sur `true` à l’aide de la configuration du référentiel pour mettre à jour toutes les références afin d’utiliser la page d’origine pour référencer la page Live Copy. Disponible uniquement pour `PageMoveAction`. |

## Spécification des configurations de déploiement à utiliser {#specifying-the-rollout-configurations-to-use}

MSM vous permet de spécifier des ensembles de configurations de déploiement généralement utilisés et, si nécessaire, vous pouvez les remplacer pour des Live Copies spécifiques. MSM fournit différents emplacements pour la spécification des configurations de déploiement à utiliser. L’emplacement détermine si la configuration s’applique à une Live Copy spécifique.

La liste suivante d’emplacements où vous pouvez spécifier les configurations de déploiement à utiliser décrit comment MSM détermine les configurations de déploiement à utiliser pour une Live Copy :

* **[Propriétés](live-copy-sync-config.md#setting-the-rollout-configurations-for-a-live-copy-page) de la page Live Copy :** lorsqu’une page Live Copy est configurée pour utiliser une ou plusieurs configurations de déploiement, MSM utilise ces configurations de déploiement.
* **[Propriétés](live-copy-sync-config.md#setting-the-rollout-configuration-for-a-blueprint-page) de la page Plan :** Lorsqu&#39;une Live Copy est basée sur un plan et que la page Live Copy n&#39;est pas configurée avec une configuration de déploiement, la configuration de déploiement associée à la page source du plan directeur est utilisée.
* **Propriétés de la page parent Live Copy :** lorsque ni la page Live Copy ni la page source du plan directeur ne sont configurées avec une configuration de déploiement, la configuration de déploiement qui s’applique à la page parente de la page Live Copy est utilisée.
* **[Valeur par défaut](live-copy-sync-config.md#setting-the-system-default-rollout-configuration) du système :** lorsque la configuration de déploiement de la page parente de Live Copy ne peut pas être déterminée, la configuration de déploiement par défaut du système est utilisée.

Par exemple, un plan directeur utilise le didacticiel [WKND](/help/implementing/developing/introduction/develop-wknd-tutorial.md) site comme contenu source. Un site est créé à partir du plan directeur. Chaque élément de la liste ci-dessous décrit un scénario d’utilisation distinct des configurations de déploiement :

* Aucune des pages du plan directeur ou des pages Live Copy n&#39;est configurée pour utiliser une configuration de déploiement. MSM utilise la configuration de déploiement par défaut du système pour toutes les pages Live Copy.
* La page racine du site WKND est configurée avec plusieurs configurations de déploiement. MSM utilise ces configurations de déploiement pour toutes les pages Live Copy.
* La page racine du site WKND est configurée avec plusieurs configurations de déploiement et la page racine du site Live Copy est configurée avec un ensemble différent de configurations de déploiement. MSM utilise les configurations de déploiement qui sont configurées sur la page racine du site Live Copy.

### Définition des configurations de déploiement pour une page Live Copy {#setting-the-rollout-configurations-for-a-live-copy-page}

Configurez une page Live Copy avec les configurations de déploiement à utiliser lorsque la page source est déployée. Les pages enfants héritent de la configuration par défaut. Lorsque vous configurez la configuration de déploiement à utiliser, vous remplacez la configuration héritée par la page Live Copy de son parent.

Vous pouvez également configurer les configurations de déploiement pour une page Live Copy lorsque vous [créez la Live Copy](creating-live-copies.md#creating-a-live-copy-of-a-page).

1. Utilisez la console **Sites** pour sélectionner la page Live Copy.
1. Sélectionnez **Propriétés** dans la barre d’outils.
1. Ouvrez l’onglet **Live Copy**.

   La section **Configuration** répertorie les configurations de déploiement dont la page hérite.

   ![Héritage de Live Copy à partir de la page parente](../assets/live-copy-inherit.png)

1. Si nécessaire, ajustez l’indicateur **Héritage de Live Copy**. Si cette option est cochée, la configuration de Live Copy est effective sur tous les enfants.

1. Désélectionnez la propriété **Hériter de la configuration de déploiement du parent**, puis sélectionnez une ou plusieurs configurations de déploiement dans la liste.

   Les configurations de déploiement sélectionnées s’affichent sous la liste déroulante.

   ![Remplacement de l’héritage de configuration de Live Copy](../assets/live-copy-inherit-override.png)

1. Cliquez ou appuyez sur **Enregistrer et fermer**.

### Définition de la configuration du déploiement pour une page de plan directeur {#setting-the-rollout-configuration-for-a-blueprint-page}

Configurez une page de plan directeur avec les configurations de déploiement à utiliser lorsque la page de plan directeur est déployée.

Notez que les pages enfants de la page de plan directeur héritent de la configuration. Lorsque vous configurez la configuration du déploiement à utiliser, il se peut que vous remplaciez la configuration dont la page hérite de son parent.

1. Utilisez la console **Sites** pour sélectionner la page racine du plan.
1. Sélectionnez **Propriétés** dans la barre d’outils.
1. Ouvrez l’onglet **Plan directeur**.
1. Sélectionnez une ou plusieurs **configurations de déploiement** à l’aide du sélecteur de liste déroulante.
1. Conservez vos mises à jour à l’aide de l’option **Enregistrer**.

### Définition de la configuration du déploiement système par défaut {#setting-the-system-default-rollout-configuration}

Pour spécifier une configuration de déploiement à utiliser comme valeur par défaut du système, configurez le service OSGi suivant.

* **Day CQ WCM Live Relationship** Manager avec le PID de service  `com.day.cq.wcm.msm.impl.LiveRelationshipManagerImpl`

Configurez le service à l&#39;aide de la [console Web](/help/implementing/deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) ou d&#39;un [noeud de référentiel](/help/implementing/deploying/configuring-osgi.md#osgi-configuration-in-the-repository).

* Dans la console Web, le nom de la propriété à configurer est **Default rollout config**.
* A l’aide d’un noeud de référentiel, le nom de la propriété à configurer est `liverelationshipmgr.relationsconfig.default`.

Définissez la valeur de cette propriété sur le chemin d’accès à la configuration de déploiement à utiliser comme valeur système par défaut. La valeur par défaut est `/libs/msm/wcm/rolloutconfigs/default`, c&#39;est-à-dire **Config de déploiement standard**.
