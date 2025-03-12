---
title: Migration des groupes
description: Présentation de la migration de groupe dans AEM as a Cloud Service.
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
source-git-commit: c3a13f75757a478996918c6868a172d75158aafe
workflow-type: tm+mt
source-wordcount: '1914'
ht-degree: 7%

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

L’un des changements majeurs apportés à AEM as a Cloud Service est l’utilisation entièrement intégrée des Adobe ID pour l’accès au niveau création. Ce processus nécessite l’utilisation d’[Adobe Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html) pour la gestion des utilisateurs et utilisatrices, et des groupes d’utilisateurs et utilisatrices. Les informations de profil utilisateur sont centralisées dans le système Adobe Identity Management (IMS) qui fournit une authentification unique pour toutes les applications cloud Adobe. Pour plus d’informations, voir [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html?lang=fr#identity-management). En raison de cette modification, les utilisateurs sont automatiquement créés sur AEM lorsqu’ils s’y connectent pour la première fois via IMS.  Par conséquent, le CTT ne migre pas les utilisateurs vers le système cloud.  Les utilisateurs et utilisatrices IMS doivent être placés dans des groupes IMS, qui peuvent être des groupes migrés, ou de nouveaux groupes placés dans les groupes AEM autorisés à accéder au contenu AEM en cours de migration.  Ainsi, les utilisateurs et utilisatrices du système cloud disposeront du même accès que sur leur système AEM source.

## Détails de la migration du groupe {#group-migration-detail}

L’outil de transfert de contenu et Cloud Acceleration Manager migrent tous les groupes associés au contenu en cours de migration vers le système cloud. Pour ce faire, l’outil de transfert de contenu copie tous les groupes du système AEM source pendant le processus d’extraction. L’ingestion CAM sélectionne et migre ensuite uniquement certains groupes :

* Si un groupe utilise une politique de liste de contrôle d’accès ou de groupe d’utilisateurs fermé pour le contenu migré, ce groupe est migré, avec quelques exceptions répertoriées ci-dessous.
* Plusieurs groupes sont intégrés et déjà présents sur le système cloud cible ; ils ne sont jamais migrés.
   * Certains groupes intégrés peuvent inclure des groupes de membres qui ne sont _pas_ intégrés ; tout groupe de membres de ce type (membres directs ou membres de membres, etc.) référencé dans une liste de contrôle d’accès ou une politique de groupe d’utilisateurs fermé du contenu migré sera migré, afin de s’assurer que les utilisateurs qui sont membres de ces groupes (directement ou indirectement) conservent leur accès au contenu migré.
* D’autres groupes, tels que ceux introuvables sur une politique ACL ou CUG, ceux déjà sur le système de destination et ceux avec des données limitées par leur unicité déjà sur le système cible, ne seront pas migrés.

Notez que le chemin d’accès consigné/signalé pour un groupe est uniquement le premier à avoir déclenché la migration de ce groupe. Ce groupe peut également se trouver sur d’autres chemins d’accès au contenu.

La plupart des groupes migrés sont configurés pour être gérés par IMS.  Cela signifie qu’un groupe dans IMS portant le même nom sera lié au groupe dans AEM et que tous les utilisateurs IMS du groupe IMS deviendront des utilisateurs d’AEM et des membres du groupe dans AEM.  Cela permet à ces utilisateurs d’accéder au contenu en fonction des listes de contrôle d’accès ou des politiques de CUG pour le groupe.

Notez que les groupes migrés ne sont plus considérés comme des « groupes locaux » AEM ; il s’agit de groupes prêts pour IMS dans AEM, bien qu’ils puissent ne pas exister encore dans IMS.  Ils doivent être recréés séparément dans IMS afin de pouvoir être synchronisés entre AEM et IMS.  Les groupes peuvent être créés dans IMS via Admin Console, entre autres méthodes, individuellement ou en bloc.  Voir [Gérer les groupes d’utilisateurs](https://helpx.adobe.com/fr/enterprise/using/user-groups.html) pour plus d’informations sur la création de groupes individuellement ou en bloc sur Admin Console.

L’exception à cette configuration IMS concerne les groupes créés par les collections Assets. Lors de la création d’une collection sur AEM, des groupes sont créés pour accéder à cette collection. Ces groupes sont migrés vers le système cloud, mais ils ne sont pas configurés pour être gérés par IMS.  Pour ajouter des utilisateurs IMS à ces groupes, ils doivent être ajoutés à la page Propriétés du groupe dans l’interface utilisateur d’Assets, individuellement ou collectivement dans le cadre d’un autre groupe IMS.


## Migration de l’exclusion d’un groupe {#group-migration-option}

Les versions 3.0.20 et ultérieures de CTT incluent une option permettant de désactiver la migration des groupes.  Elle est configurée dans la console OSGI comme suit :

* Ouvrez l’`(http://<server>/system/console/configMgr)` Configuration OSGI .
* Cliquez sur la configuration appelée **Configuration du service d’extraction de l’outil de transfert de contenu**
* Décochez **Inclure les groupes dans la migration** pour désactiver les migrations de groupe
* Cliquez sur **Enregistrer** pour vous assurer que la configuration est enregistrée et active sur le serveur

Lorsque ce paramètre est désactivé, les groupes ne sont pas migrés et il n’y a pas de rapport de migration principale ni de rapport utilisateur (voir ci-dessous).

## Rapport de migration principale et rapport utilisateur {#principal-migration-report}

Lorsque des groupes sont inclus pendant la migration (valeur par défaut), un rapport de migration principal est enregistré, qui décrit ce qui se passe avec chaque groupe pendant la migration.  Pour télécharger ce rapport après une ingestion réussie :
* Dans CAM, accédez à Transfert de contenu et sélectionnez Tâches d’ingestion .
* Cliquez sur les points de suspension (...) sur la ligne de l’ingestion en question, puis choisissez « Afficher le résumé principal ».
* Dans la boîte de dialogue qui s’affiche, sélectionnez « Rapport de migration principale » dans la liste déroulante sous « Télécharger un fichier... » et cliquez sur le bouton Télécharger .
* Enregistrez le fichier CSV obtenu.

Voici quelques-unes des informations enregistrées par groupe :
* Si la migration est effectuée, chemin d’accès à la première liste ACL ou au premier groupe d’utilisateurs fermé ayant provoqué la migration du groupe.
* Si le groupe a été migré précédemment ; si l’ingestion en cours n’était pas une ingestion par effacement, certains groupes peuvent avoir été migrés lors d’une ingestion précédente.
* Indique si le groupe est un groupe intégré. Ces groupes ne sont pas migrés, car ils se trouvent toujours dans l’environnement AEMaaCS cible.
* Si le groupe ne faisait pas partie d’une liste de contrôle d’accès ou d’un groupe d’utilisateurs fermé sur le contenu migré, il n’aurait pas été migré.
* Si le groupe était un groupe local, tel qu’un groupe créé par une collection Assets, il a peut-être été migré. Dans ce cas, le mot « local » est ajouté au rapport pour ce groupe.

Pendant la migration, les utilisateurs ne sont pas migrés, mais les relations utilisateur-groupe sur le système source seraient perdues à moins qu’ils ne soient capturés d’une manière ou d’une autre. Le processus d’ingestion capture certaines de ces informations au format texte dans un rapport d’utilisateur, qui se trouve à la fin du rapport de migration principal.

### Rapport de l’utilisateur {#user-report}

Dans la section Rapport utilisateur , les utilisateurs sont signalés (un par ligne), ainsi que leur adresse e-mail et une liste des groupes compatibles IMS qui ont été migrés lors de cette ingestion.  Les groupes qui n’ont pas été migrés, qui ont été migrés lors d’une ingestion précédente ou qui sont des groupes locaux ne sont pas inclus dans la liste.   Si un utilisateur ou une utilisatrice ne fait partie d’aucun groupe activé pour IMS migré et qu’il n’a pas de notes supplémentaires indiquant qu’il s’agit d’un cas spécial (voir **Notes** ci-dessous), cet utilisateur ou cette utilisatrice n’apparaît _pas_ dans le rapport. Les groupes signalés avec chaque utilisateur sont ceux dont l’utilisateur est membre, directement ou indirectement, dans le système source. Comme les groupes du système source peuvent être imbriqués alors qu’ils ne le sont pas dans le système cible, cette liste de groupes prend en charge la nouvelle structure de groupes aplatis dans IMS.

Dans le cas d’une opération d’effacement, puis d’une ingestion sans effacement, les groupes de la liste d’un utilisateur de l’ingestion sans effacement sont uniquement les groupes migrés pendant la phase sans effacement.

#### Remarques {#user-report-notes}

Outre les groupes pour chaque utilisateur, il existe un champ dans le Rapport utilisateur dans lequel des notes sur l’utilisateur peuvent être fournies (et une description détaillée de la signification de la note se trouve également dans le rapport) à titre d’information.  Les notes possibles sont les suivantes :

* **Note-A** Les utilisateurs qui sont référencés directement dans une liste de contrôle d’accès auront la mention *Note-A* dans leur section de notes, car il ne s’agit pas d’un cas d’utilisation recommandé ou d’une bonne pratique.
* **Note B** Les utilisateurs qui sont membres directs d’un groupe intégré auront la *Note B* dans leur section de notes, car il ne s’agit pas non plus d’un cas d’utilisation recommandé ou d’une bonne pratique.
* **Note-C** Les utilisateurs membres directs ou indirects d’un groupe local migré (tel qu’un groupe créé par une collection Assets) verront la note *C* dans leur section de notes, car les groupes locaux ne sont pas configurés pour être gérés par IMS.

Ces cas peuvent se produire simultanément, et également en même temps que les cas précédents.  _Pour plus d’informations sur les groupes auxquels chaque note fait référence pour chaque utilisateur, consultez le journal d’ingestion ; il consigne ces informations pour chaque utilisateur._

Le rapport de l’utilisateur est ajouté à la fin du rapport de migration principale (et en fait donc partie) (voir [Résumé et rapport final](#final-summary-and-report) ci-dessous) pour permettre aux clients de mieux comprendre les groupes et les utilisateurs, ainsi que leurs relations.

## Chargement massif de fichiers {#bulk-upload-files}

Comme les groupes sont migrés uniquement vers AEM as a Cloud Service, ils doivent toujours être ajoutés à IMS pour pouvoir fonctionner correctement avec AEM dans le cloud. En outre, les utilisateurs ne font pas l’objet d’une migration et doivent donc être ajoutés à IMS. L’outil de migration CTT/CAM n’effectue pas cette étape, mais le processus d’ingestion crée deux fichiers de chargement en masse, l’un pour les groupes et l’autre pour les utilisateurs. Ces fichiers peuvent être modifiés, puis utilisés, avec la fonctionnalité de chargement en masse d’Admin Console, pour créer des groupes et des utilisateurs IMS en fonction de vos groupes et utilisateurs AEM.

Voir [Chargement en bloc de groupes et d’utilisateurs vers IMS](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/bulk-principal-uploading.md) pour plus d’informations sur l’utilisation des fichiers de chargement en bloc pour créer des utilisateurs et des groupes à l’aide d’Admin Console.

Voir également [Gérer les utilisateurs](https://helpx.adobe.com/ca/enterprise/using/users.html) pour plus d’informations sur la gestion des utilisateurs d’AEM as a Cloud Service.

## Considérations supplémentaires {#additional-considerations}

* Si le paramètre **Effacer le contenu existant sur l’instance cloud avant l’ingestion** est défini, les groupes précédemment transférés à l’instance Cloud Service sont supprimés avec l’ensemble du référentiel existant ; un nouveau référentiel est créé dans lequel le contenu est ingéré. Ce processus réinitialise également tous les paramètres, y compris les autorisations sur l’instance Cloud Service cible, et est valable pour tout utilisateur ajouté au groupe **administrateurs**. L’utilisateur administrateur doit être réajouté au groupe **administrateurs** pour récupérer le jeton d’accès à l’ingestion CTT/CAM.
* Lorsque des ingestions sans effacement sont effectuées (**Effacer le contenu existant** n’est pas défini), si le contenu n’est pas transféré parce qu’il n’a pas été modifié depuis le transfert précédent, les groupes associés à ce contenu ne sont pas transférés non plus. Cette règle est vraie même si les groupes ont changé sur le système source. En effet, les groupes ne sont migrés qu’avec le contenu auquel ils sont associés. Pour cette raison, dans ce cas, les groupes membres d’un groupe sur le système source ne seront pas migrés, à moins qu’ils ne fassent partie d’un autre groupe en cours de migration ou dans la liste de contrôle d’accès des différents contenus en cours de migration. Pour migrer ces groupes par la suite, pensez à utiliser des packages, à supprimer des groupes de la cible et à migrer à nouveau le contenu approprié, ou à effectuer une nouvelle migration à l’aide d’une ingestion par effacement.
* Lors d’une ingestion sans effacement, si un groupe existe avec l’une des mêmes données contraintes d’unicité (rep:principalName, rep:authorizableId, jcr:uuid ou rep:externalId) à la fois sur l’instance AEM source et l’instance AEM Cloud Service cible, le groupe en question n’est _pas_ migré et le groupe existant précédemment sur le système cloud reste inchangé. Elles sont consignées dans le rapport de migration principal.
* Consultez [ Migration de groupes d’utilisateurs fermés ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md) pour en savoir plus sur les groupes utilisés dans une politique de groupe d’utilisateurs fermé (CUG).

## Résumé final et rapport

Une fois l’extraction et l’ingestion terminées avec succès, un rapport est généré, présentant les détails de la migration du groupe. Pour plus d’informations, consultez [ Validation de la migration de groupe ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/validating-content-transfers.md#how-to-validate-group-migration) .
