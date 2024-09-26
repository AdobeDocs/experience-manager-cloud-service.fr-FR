---
title: Migration des groupes
description: Présentation de la migration des groupes dans AEM as a Cloud Service.
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
source-git-commit: 1f9526f8e8aa6a070e95827fab16431b0ee7566b
workflow-type: tm+mt
source-wordcount: '1315'
ht-degree: 10%

---


# Migration des groupes {#group-migration}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_groupmigration"
>title="Migration des groupes"
>abstract="L’outil de transfert de contenu permet de copier des groupes de votre système Adobe Experience Manager (AEM) existant vers AEM as a Cloud Service."

>[!NOTE]
>Pour les versions précédentes de l’outil de mappage des utilisateurs, consultez la [documentation des versions antérieures](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md).

## Présentation {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermigration"
>title="Les utilisateurs et utilisatrices ne sont pas migrés."
>abstract="L’outil de transfert de contenu ne migre plus les utilisateurs et utilisatrices. Ceux-ci doivent être gérés dans Admin Console."
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/onboarding/journey/admin-console" text="Documentation dʼAEM Admin Console"
>additional-url="https://adminconsole.adobe.com/" text="AEM Admin Console"

Dans le cadre du parcours de transition vers Adobe Experience Manager (AEM) as a Cloud Service, les groupes doivent être migrés des systèmes AEM existants vers AEM as a Cloud Service. Cette tâche est effectuée par l’outil de transfert de contenu.

L’un des changements majeurs apportés à AEM as a Cloud Service est l’utilisation entièrement intégrée des Adobe ID pour l’accès au niveau création. Ce processus nécessite l’utilisation d’[Adobe Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html) pour la gestion des utilisateurs et utilisatrices, et des groupes d’utilisateurs et utilisatrices. Les informations de profil utilisateur sont centralisées dans Adobe Identity Management System (IMS), qui permet l’authentification unique dans toutes les applications cloud d’Adobe. Pour plus d’informations, voir [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html?lang=fr#identity-management). En raison de cette modification, les utilisateurs sont automatiquement créés sur AEM lorsqu’ils se connectent pour la première fois via IMS.  Par conséquent, CTT ne migre pas les utilisateurs vers le système cloud.  Les utilisateurs IMS doivent être placés dans des groupes IMS, qui peuvent être des groupes migrés ou de nouveaux groupes placés dans les groupes AEM qui ont été autorisés à accéder au contenu AEM en cours de migration.  De cette manière, les utilisateurs du système cloud auront le même accès qu’à leur système d’AEM source.

## Détails de la migration de groupe {#group-migration-detail}

L’outil de transfert de contenu et Cloud Acceleration Manager migrent tous les groupes associés au contenu migré vers le système cloud. L’outil de transfert de contenu effectue cette opération en copiant tous les groupes du système d’AEM source pendant le processus d’extraction. L’ingestion CAM sélectionne et migre uniquement certains groupes :

* Un certain nombre de groupes sont intégrés et déjà présents sur le système cloud cible ; ils ne sont jamais migrés.
* Les groupes de membres directs de tout groupe intégré directement ou indirectement référencé dans une ACL ou une stratégie de CUG de contenu migré seront migrés, afin de garantir que les utilisateurs qui sont membres directs ou indirects de ces groupes conservent leur accès au contenu migré.
* Si un groupe se trouve sur une liste de contrôle d’accès ou une stratégie de CUG du contenu migré, ce groupe sera migré.
* D’autres groupes, tels que ceux qui ne figurent pas dans une liste de contrôle d’accès ou une stratégie de CUG, ceux qui se trouvent déjà dans le système de destination et ceux qui disposent déjà de données limitées par l’unicité sur le système cible, ne seront pas migrés.

Notez que le chemin d’accès consigné/signalé pour un groupe n’est que le premier chemin qui a déclenché la migration de ce groupe. Ce groupe peut également se trouver sur d’autres chemins de contenu.

La plupart des groupes migrés sont configurés pour être gérés par IMS.  Cela signifie qu’un groupe dans IMS portant le même nom sera lié au groupe dans AEM, et que tous les utilisateurs IMS du groupe IMS deviendront AEM utilisateurs et membres du groupe dans l’.  Cela permet à ces utilisateurs d’accéder au contenu en fonction des stratégies de listes de contrôle d’accès ou de groupes d’utilisateurs fermés du groupe.

L’exception à cette configuration IMS concerne les groupes créés par les collections Assets. Lorsqu’une collection est créée sur AEM, les groupes sont créés pour accéder à cette collection ; ces groupes sont migrés vers le système cloud, mais ils ne sont pas configurés pour être gérés par IMS.  Pour ajouter des utilisateurs IMS à ces groupes, ils doivent être ajoutés à la page Propriétés du groupe dans l’interface utilisateur d’Assets, individuellement ou collectivement dans le cadre d’un autre groupe IMS.


## Exclusion de la migration de groupe {#group-migration-option}

CTT version 3.0.20 et ultérieure comprend une option pour désactiver la migration des groupes.  Il est configuré dans la console OSGI de la manière suivante :

* Ouvrez la configuration OSGI `(http://<server> /system/console/configMgr)`.
* Cliquez sur la configuration appelée **Configuration du service d’extraction de l’outil de transfert de contenu**
* Décochez la case **Inclure des groupes dans la migration** pour désactiver les migrations de groupes.
* Cliquez sur **Enregistrer** pour vous assurer que la configuration est enregistrée et active sur le serveur.

Si ce paramètre est désactivé, les groupes ne seront pas migrés et il n’y aura pas de rapport Migration des entités de sécurité ou d’utilisateur.

## Rapport de l’utilisateur {#user-report}

Lors de la migration, les utilisateurs ne sont pas migrés, mais les relations utilisateur-groupe sur le système source sont perdues, à moins qu’ils ne soient d’une manière ou d’une autre capturés.  Le rapport utilisateur capture certaines de ces informations au format texte dans un rapport utilisateur. Dans celui-ci, chaque utilisateur est signalé (une par ligne) avec une liste des groupes dont il est membre (mais les groupes non migrés ne sont pas placés dans cette liste), sauf si sa liste de groupes est vide, auquel cas l’utilisateur n’apparaît pas. Les groupes signalés avec chaque utilisateur sont ceux dont l’utilisateur fait partie directement ou indirectement dans le système source. Comme les groupes du système source peuvent être imbriqués alors qu’ils ne le sont pas dans le système cible, cette liste de groupes prend en charge la nouvelle structure de groupe aplati dans IMS.

Dans le cas d’une suppression, puis d’une ingestion non effacée, les groupes de la liste d’un utilisateur incluent les groupes migrés dans l’une ou l’autre phase.

Outre les groupes de chaque utilisateur, le rapport contient un champ dans lequel des notes peuvent être ajoutées à l’utilisateur (et une description détaillée de la signification de la note figure également dans le rapport).  Les notes possibles sont les suivantes :

* Les utilisateurs qui sont référencés directement dans une liste de contrôle d’accès auront *Remarque-A* dans leur section de notes, car il ne s’agit pas d’un cas d’utilisation recommandé ou d’une bonne pratique.
* Les utilisateurs qui sont des membres directs d’un groupe intégré auront *Remarque-B* dans leur section de notes, car il ne s’agit pas non plus d’un cas d’utilisation recommandé ou d’une bonne pratique.

Ces cas peuvent se produire simultanément, et en même temps que les cas précédents.

Le rapport Utilisateur est ajouté à la fin du rapport Migration des principaux (et fait donc partie de celui-ci) (voir [Résumé final et rapport](#final-summary-and-report) ci-dessous).

## Considérations supplémentaires {#additional-considerations}

* Si le paramètre **Wipe existing content on Cloud instance before ingestion** (Effacer le contenu existant sur l’instance cloud avant l’ingestion) est défini, les groupes précédemment transférés sur l’instance de Cloud Service sont supprimés avec l’ensemble du référentiel existant ; un nouveau référentiel est créé dans lequel le contenu est ingéré. Ce processus réinitialise également tous les paramètres, y compris les autorisations sur l’instance de Cloud Service cible. Il est également vrai pour tout utilisateur ajouté au groupe **administrateurs**. L’utilisateur administrateur doit être rajouté au groupe **administrateurs** pour récupérer le jeton d’accès pour l’ingestion CTT/CAM.
* Lorsque des ingérations non effacées sont effectuées (**L’effacement du contenu existant** est annulé), si le contenu n’est pas transféré car il n’a pas été modifié depuis le transfert précédent, les groupes associés à ce contenu ne sont pas transférés non plus. Cette règle est vraie même si les groupes ont changé sur le système source. En effet, les groupes ne sont migrés qu’avec le contenu auquel ils sont associés. C’est pourquoi, dans ce cas, les groupes qui sont membres d’un groupe sur le système source ne seront pas migrés, à moins qu’ils ne fassent partie d’un autre groupe qui est en cours de migration, ou dans la liste de contrôle d’accès de contenu différent en cours de migration. Pour migrer ces groupes par la suite, envisagez d’utiliser des packages, de supprimer des groupes de la cible et de rémigrer le contenu approprié, ou de procéder à une nouvelle migration à l’aide d’une ingestion par suppression.
* Lors d’une ingestion sans suppression, si un groupe existe avec l’une des mêmes données contraintes d’unicité (rep:principalName, rep:authorizableId, jcr:uuid ou rep:externalId) sur l’instance d’AEM source et l’instance AEM Cloud Service cible, le groupe en question est _not_ migré et le groupe existant précédemment sur le système cloud reste inchangé. Il est consigné dans le rapport Migration de l’entité principale.
* Voir [Migration des groupes d’utilisateurs fermés](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md) pour plus d’informations sur les groupes utilisés dans une stratégie de groupe d’utilisateurs fermé (CUG).

## Résumé final et rapport

Une fois l’extraction et l’ingestion terminées, un rapport est généré avec les détails de migration du groupe. Pour plus d’informations, voir [Validation de la migration de groupe](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/validating-content-transfers.md#how-to-validate-group-migration) .
