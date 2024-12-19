---
title: Migration des groupes
description: Présentation de la migration de groupe dans AEM as a Cloud Service.
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
source-git-commit: bb041cf13d5e82fc4135f0849b03eeeed9a5d009
workflow-type: tm+mt
source-wordcount: '1476'
ht-degree: 8%

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

L’un des changements majeurs apportés à AEM as a Cloud Service est l’utilisation entièrement intégrée des Adobe ID pour l’accès au niveau création. Ce processus nécessite l’utilisation d’[Adobe Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html) pour la gestion des utilisateurs et utilisatrices, et des groupes d’utilisateurs et utilisatrices. Les informations de profil utilisateur sont centralisées dans le système Identity Management d’Adobe (IMS) qui fournit une authentification unique pour toutes les applications cloud d’Adobe. Pour plus d’informations, voir [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html?lang=fr#identity-management). En raison de cette modification, les utilisateurs sont automatiquement créés sur AEM lorsqu’ils s’y connectent pour la première fois via IMS.  Par conséquent, le CTT ne migre pas les utilisateurs vers le système cloud.  Les utilisateurs IMS doivent être placés dans des groupes IMS, qui peuvent être des groupes migrés ou de nouveaux groupes placés dans les groupes AEM qui ont reçu l’autorisation d’accéder au contenu AEM en cours de migration.  Ainsi, les utilisateurs du système cloud disposeront du même accès que celui dont ils disposaient sur leur système AEM source.

## Détails de la migration du groupe {#group-migration-detail}

L’outil de transfert de contenu et Cloud Acceleration Manager migrent tous les groupes associés au contenu en cours de migration vers le système cloud. Pour ce faire, l’outil de transfert de contenu copie tous les groupes du système AEM source pendant le processus d’extraction. L’ingestion CAM sélectionne et migre ensuite uniquement certains groupes :

* Si un groupe utilise une politique de liste de contrôle d’accès ou de groupe d’utilisateurs fermé pour le contenu migré, ce groupe est migré, avec quelques exceptions répertoriées ci-dessous.
* Plusieurs groupes sont intégrés et déjà présents sur le système cloud cible ; ils ne sont jamais migrés.
   * Certains groupes intégrés peuvent inclure des groupes de membres qui ne sont _pas_ intégrés ; tout groupe de membres de ce type (membres directs ou membres de membres, etc.) référencé dans une liste de contrôle d’accès ou une politique de groupe d’utilisateurs fermé du contenu migré sera migré, afin de s’assurer que les utilisateurs qui sont membres de ces groupes (directement ou indirectement) conservent leur accès au contenu migré.
* D’autres groupes, tels que ceux introuvables sur une politique ACL ou CUG, ceux déjà sur le système de destination et ceux avec des données limitées par leur unicité déjà sur le système cible, ne seront pas migrés.

Notez que le chemin d’accès consigné/signalé pour un groupe est uniquement le premier à avoir déclenché la migration de ce groupe. Ce groupe peut également se trouver sur d’autres chemins d’accès au contenu.

La plupart des groupes migrés sont configurés pour être gérés par IMS.  Cela signifie qu’un groupe dans IMS portant le même nom sera lié au groupe dans AEM, et tous les utilisateurs IMS du groupe IMS deviendront des utilisateurs AEM et des membres du groupe dans AEM.  Cela permet à ces utilisateurs d’accéder au contenu en fonction des listes de contrôle d’accès ou des politiques de CUG pour le groupe.

Notez que les groupes migrés ne sont plus considérés comme des « groupes locaux » AEM ; il s’agit de groupes prêts pour IMS dans AEM, bien qu’ils n’existent pas encore dans IMS.  Ils doivent être recréés séparément dans IMS afin de pouvoir être synchronisés entre AEM et IMS.  Les groupes peuvent être créés dans IMS par l’intermédiaire d’Admin Console, entre autres méthodes, individuellement ou en bloc.  Voir [Gérer les groupes d’utilisateurs](https://helpx.adobe.com/ca/enterprise/using/user-groups.html) pour plus d’informations sur la création de groupes individuellement ou en bloc sur l’Admin Console.

L’exception à cette configuration IMS concerne les groupes créés par les collections Assets. Lorsqu’une collection est créée sur AEM, des groupes sont créés pour accéder à cette collection. Ces groupes sont migrés vers le système cloud, mais ils ne sont pas configurés pour être gérés par IMS.  Pour ajouter des utilisateurs IMS à ces groupes, ils doivent être ajoutés à la page Propriétés du groupe dans l’interface utilisateur d’Assets, individuellement ou collectivement dans le cadre d’un autre groupe IMS.


## Migration de l’exclusion d’un groupe {#group-migration-option}

Les versions 3.0.20 et ultérieures de CTT incluent une option permettant de désactiver la migration des groupes.  Elle est configurée dans la console OSGI comme suit :

* Ouvrez l’`(http://<server>/system/console/configMgr)` Configuration OSGI .
* Cliquez sur la configuration appelée **Configuration du service d’extraction de l’outil de transfert de contenu**
* Décochez **Inclure les groupes dans la migration** pour désactiver les migrations de groupe
* Cliquez sur **Enregistrer** pour vous assurer que la configuration est enregistrée et active sur le serveur

Lorsque ce paramètre est désactivé, les groupes ne sont pas migrés et il n’y a pas de rapport de migration principale ni de rapport utilisateur.

## Rapport de l’utilisateur {#user-report}

Pendant la migration, les utilisateurs ne sont pas migrés, mais les relations utilisateur-groupe sur le système source sont perdues à moins qu’elles ne soient capturées d’une manière ou d’une autre.  Le rapport d’utilisateur capture certaines de ces informations au format texte dans un rapport d’utilisateur. Chaque utilisateur y est signalé (un par ligne) ainsi qu’une liste des groupes dont il est membre (mais les groupes non migrés ne sont pas placés dans cette liste), sauf si sa liste de groupes est vide, auquel cas l’utilisateur n’apparaît pas. Les groupes signalés avec chaque utilisateur sont ceux dont l’utilisateur est membre directement ou indirectement dans le système source. Comme les groupes du système source peuvent être imbriqués alors qu’ils ne le sont pas dans le système cible, cette liste de groupes prend en charge la nouvelle structure de groupes aplatis dans IMS.

Dans le cas d’une opération d’effacement, puis d’une ingestion autre que l’effacement, les groupes figurant dans la liste d’un utilisateur incluent les groupes migrés dans l’une ou l’autre des phases.

Outre les groupes pour chaque utilisateur, il existe un champ dans le rapport où des notes peuvent être ajoutées pour l&#39;utilisateur (et une description détaillée de la signification de la note se trouve également dans le rapport).  Les notes possibles sont les suivantes :

* Les utilisateurs qui sont référencés directement dans une liste de contrôle d’accès auront la *Note-A* dans leur section de notes, car il ne s’agit pas d’un cas d’utilisation recommandé ou d’une bonne pratique.
* Les utilisateurs qui sont membres directs d&#39;un groupe intégré auront la *Note-B* dans leur section de notes, car il ne s&#39;agit pas non plus d&#39;un cas d&#39;utilisation recommandé ou d&#39;une bonne pratique.

Ces cas peuvent se produire simultanément, et également en même temps que les cas précédents.

Le rapport de l’utilisateur est ajouté à la fin du rapport de migration principal (et en fait donc partie) (voir [Résumé et rapport finaux](#final-summary-and-report) ci-dessous).  Les informations contenues dans ce rapport, y compris les groupes signalés pour chaque utilisateur, peuvent être utilisées pour créer un fichier de chargement utilisateur en bloc qui peut être utilisé dans Admin Console pour créer de nombreux utilisateurs dans IMS en bloc.  Les utilisateurs et utilisatrices IMS existants peuvent également être modifiés en bloc.

Voir [Gérer plusieurs utilisateurs | Chargement CSV en bloc ](https://helpx.adobe.com/ca/enterprise/using/bulk-upload-users.html) pour plus d’informations sur la création ou la modification d’utilisateurs en bloc via l’Admin Console.

## Considérations supplémentaires {#additional-considerations}

* Si le paramètre **Effacer le contenu existant sur l’instance cloud avant l’ingestion** est défini, les groupes précédemment transférés à l’instance de Cloud Service sont supprimés avec l’ensemble du référentiel existant ; un nouveau référentiel est créé dans lequel le contenu est ingéré. Ce processus réinitialise également tous les paramètres, y compris les autorisations sur l’instance de Cloud Service cible, et est valable pour tout utilisateur ajouté au groupe **administrateurs**. L’utilisateur administrateur doit être réajouté au groupe **administrateurs** pour récupérer le jeton d’accès à l’ingestion CTT/CAM.
* Lorsque des ingestions sans effacement sont effectuées (**Effacer le contenu existant** n’est pas défini), si le contenu n’est pas transféré parce qu’il n’a pas été modifié depuis le transfert précédent, les groupes associés à ce contenu ne sont pas transférés non plus. Cette règle est vraie même si les groupes ont changé sur le système source. En effet, les groupes ne sont migrés qu’avec le contenu auquel ils sont associés. Pour cette raison, dans ce cas, les groupes membres d’un groupe sur le système source ne seront pas migrés, à moins qu’ils ne fassent partie d’un autre groupe en cours de migration ou dans la liste de contrôle d’accès des différents contenus en cours de migration. Pour migrer ces groupes par la suite, pensez à utiliser des packages, à supprimer des groupes de la cible et à migrer à nouveau le contenu approprié, ou à effectuer une nouvelle migration à l’aide d’une ingestion par effacement.
* Lors d’une ingestion sans effacement, si un groupe existe avec l’une des mêmes données contraintes d’unicité (rep:principalName, rep:authorizableId, jcr:uuid ou rep:externalId) à la fois sur l’instance AEM source et l’instance AEM Cloud Service cible, le groupe en question n’est _pas_ migré et le groupe existant précédemment sur le système cloud reste inchangé. Elles sont consignées dans le rapport de migration principal.
* Consultez [ Migration de groupes d’utilisateurs fermés ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md) pour en savoir plus sur les groupes utilisés dans une politique de groupe d’utilisateurs fermé (CUG).

## Résumé final et rapport

Une fois l’extraction et l’ingestion terminées avec succès, un rapport est généré, présentant les détails de la migration du groupe. Pour plus d’informations, consultez [ Validation de la migration de groupe ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/validating-content-transfers.md#how-to-validate-group-migration) .
