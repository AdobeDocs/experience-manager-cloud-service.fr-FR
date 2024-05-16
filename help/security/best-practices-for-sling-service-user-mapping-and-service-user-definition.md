---
title: Bonnes pratiques pour le mappage des utilisateurs et la définition d’utilisateur du service Sling
description: Découvrez les bonnes pratiques relatives au mappage des utilisateurs du service sling et à la définition des utilisateurs du service.
source-git-commit: b6f7b6996b377ecfa372742ce1ad22139547ebdd
workflow-type: tm+mt
source-wordcount: '1884'
ht-degree: 0%

---


# Bonnes pratiques pour le mappage des utilisateurs et la définition d’utilisateur du service Sling {#best-practices-for-sling-service-user-mapping-and-service-user-definition}

## Mappage des utilisateurs du service {#service-user-mapping}

Pour ajouter un mappage de votre service au ou aux utilisateurs système correspondants, vous devez créer une configuration de fabrique pour la variable `ServiceUserMapper` service. Pour maintenir ce module, de telles configurations peuvent être fournies à l’aide du mécanisme &quot;d’amendement&quot; Sling (voir [SLING-3578](https://issues.apache.org/jira/browse/SLING-3578) pour plus de détails). La méthode recommandée pour installer de telles configurations avec votre lot consiste à l’ajouter au modèle de configuration de démarrage rapide, comme décrit dans l’exemple suivant :

```
org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended-my-mapping
    user.default=""
    user.mapping=[
        "com.adobe.cq.my-bundle:my-subservice\=[content-writer-service]",
        "com.adobe.cq.my-bundle:my-subservice-different-task\="[myfeature-configuration-writer-service,content-reader-service]"
    ]
```

### Format de mappage {#mapping-format}

Depuis AEM 6.4, le format de mappage est défini comme suit :

>[!NOTE]
>
>La variable `userName` est obsolète et ne doit plus être utilisé.

```
bundleId [:subserviceName] = userName | [principalNames]   
```

`bundleId` et `subserviceName` identifier le service, `userName/principalNames` identifier l’utilisateur du service et `principalNames` est une liste séparée par des virgules.

Notez également que `principalNames` est la liste des noms principaux des utilisateurs du service qui, prêts à l’emploi, sont identiques à l’identifiant.


**Bonne pratique**

* Noms de sous-service pour différentes tâches : si les services de votre lot effectuent différentes tâches, il est recommandé d’identifier `subserviceNames` pour les regrouper par tâches
* Si un service donné effectue différentes opérations (par exemple, la lecture du contenu d’une ressource et la mise à jour des informations sous une sous-arborescence de `/var`), il est recommandé de refléter cela en agrégeant différentes entités de service reflétant l’opération individuelle, comme l’agrégation de la commune `dam-reader-service` avec votre fonction spécifique `assetreport-writer-service`
* Chaque service est idéalement lié à un ensemble d’opérations très spécifique et limité.
* Le nouveau format avec `[one,or,multiple,principalNames]` est la méthode recommandée pour définir des mappages d’utilisateurs de service à partir d’AEM 6.4.

Vous trouverez ci-dessous une liste des raisons de modifier le format et pourquoi Adobe vous recommande de l’utiliser au lieu du mappage de version uniquement pour un seul ID utilisateur :

* La possibilité de réutiliser les utilisateurs du service en combinant les besoins spécifiques des clients avec les tâches courantes
* Éviter la duplication de la configuration des autorisations
* Meilleure compréhension des autorisations (et des tâches) efficaces qu’un service donné effectue
* Il n’est pas nécessaire d’appartenir à un groupe explicite pour les utilisateurs du service. Cela peut avoir des effets secondaires gênants lorsque les autorisations de groupe changent
* Améliorations des performances et évolutivité

## Résolution de mappage et connexion au service {#mapping-resolution-and-service-login}

### Résolution du mappage des services {#service-mapping-resolution}

La séquence d’appels pour résoudre le mappage de service décrite ci-dessous :

1. Rechercher actif `principalNames` mappage pour le donné `bundleId` et `subserviceName`
1. `principalNames` mappage pour la variable `bundleId` et nul `subserviceName`
1. `userName` mappage pour la variable `bundleId` et `subserviceName`
1. `userName` mappage pour `bundleId` et nul `subserviceName`
1. Mappage par défaut
1. Utilisateur par défaut

### SlingRepository - Service Login {#slingrepository-servicelogin}

La séquence d’obtention d’un service `Session/ResourceResolver` fonctionne comme suit :

1. Obtenir les noms principaux à partir de `ServiceUserMapper` => connexion au référentiel pré-authentification comme décrit ci-dessous
1. Récupération de l’ID utilisateur depuis `ServiceUserMapper`
1. Recherchez l’ID utilisateur actuel 1ServiceUserConfiguration obsolète.
1. Connexion par défaut au service Sling avec l’ID utilisateur (par exemple, une séquence de `createAdministrativeSession` et emprunter l’identité de l’ID utilisateur du service)

Le nouveau mappage avec les noms principaux entraîne la connexion simplifiée suivante au référentiel :

* Un jeu de noms principaux est traité comme le ou les principaux actifs à utiliser pour renseigner la variable `Subject`
* La connexion au référentiel peut donc être préauthentifiée.
* Aucune résolution d’appartenance à un groupe

  >[!NOTE]
  >
  >Toutes les autorisations requises doivent être déclarées pour les utilisateurs du service. &quot;everyone&quot; et autres autorisations de groupe ne seront plus héritées.

* Aucun admin-login supplémentaire pour que le service -`Session/ResourceResolver` sont créées.

### ServiceUserConfiguration obsolète {#deprecated-serviceUserConfiguration}

Notez que la spécification d’un seul nom d’utilisateur dans le mappage équivaut à la valeur existante `ServiceUserConfiguration.simpleSubjectPopulation`. Avec le nouveau format, la solution fournie par la variable `ServiceUserConfiguration` peuvent être directement répercutés avec le mappage utilisateur du service. La variable `ServiceUserConfiguration` a donc été abandonné pour AEM et toutes les utilisations existantes ont été remplacées.

## Utilisateurs et utilisatrices de service {#service-users}

### Réutilisation d’utilisateurs de service existants {#reusing-existing-service-users}

Il est recommandé de réutiliser les utilisateurs existants du service si les conditions suivantes sont remplies :

* Vos besoins correspondent à l’intention de l’utilisateur du service existant.
* Votre service nécessite d’effectuer une tâche commune qui est couverte par un utilisateur de service commun existant. Dans ce cas, il est recommandé de réutiliser l’utilisateur du service au lieu d’introduire la duplication.
* Votre service nécessite une tâche spécifique couverte par un utilisateur de service existant. Si vous n’en êtes pas sûr, demandez à l’équipe de fonctionnalités qui la possède.

Ne réutilisez pas les utilisateurs du service existant si :

* Vous devez modifier son autorisation de manière sans rapport avec elle pour qu’elle fonctionne.
* Si vous n’avez besoin que d’un petit sous-ensemble de l’autorisation qu’il fournit et que vous le réutilisez simplement parce que cela fait fonctionner votre fonctionnalité, non parce qu’il s’agit d’une correspondance réelle.
* Si son nom indique une intention totalement différente de celle dont vous avez besoin. Le choix de cette option, car elle fonctionne, peut entraîner des problèmes dans le futur, car l’équipe de fonctionnalités propriétaire d’un service spécifique peut modifier les autorisations et interrompre votre fonctionnalité.

### Création d’un utilisateur de service {#creating-a-service-user}

Une fois que vous avez vérifié qu’aucun utilisateur de service existant dans AEM n’est applicable à votre cas d’utilisation et que les problèmes RTC correspondants ont été approuvés, vous pouvez poursuivre et ajouter le nouvel utilisateur au contenu par défaut. Idéalement, un membre de l&#39;équipe de sécurité étendue est impliqué dans le vote du RTC, donc veillez à impliquer également les parties prenantes appropriées.

**Convention d’appellation**

L’équipe de sécurité d’AEM a défini la convention d’affectation des noms suivante pour que les utilisateurs du service ajoutent de la cohérence aux nouveaux utilisateurs du service et améliorent leur lisibilité et leur maintenabilité.

Un nom d’utilisateur de service se compose de 3 éléments séparés par un tiret **&#39;-&#39;**:

1. L’entité/la fonctionnalité logique ciblée par les opérations de service (évitez les éléments de chemins qui peuvent changer)
1. La tâche que les services vont effectuer
1. Tracking **&#39;service&#39;** pour repérer facilement à partir de l’identifiant et du nom principal que l’utilisateur est un utilisateur du service.

**Bonnes pratiques**

* Ne mélangez pas différentes entités/fonctionnalités. Partage avec des utilisateurs individuels du service et agrégation dans le mappage si votre service a des besoins différents
* Limitez-vous à une tâche bien définie par utilisateur de service. Partage si vous finissez par accorder trop d’autorisations ou des autorisations non liées
* Passez du temps à identifier le besoin réel de votre service.
* Consacrez du temps à trouver un nom d’utilisateur de service bon, significatif et auto-explicatif
* Demandez des commentaires et des commentaires : les développeurs qui ne connaissent pas votre fonctionnalité devraient être en mesure de lire et de comprendre vos intentions. Il se pourrait qu&#39;à l&#39;avenir ils soient chargés de le réparer ou de le maintenir.

À la fin, le nom d’utilisateur du service doit afficher :

* Comment il est destiné à être utilisé et s’il peut être réutilisé :

   * Très générique : `content-writer-service`. Peut être réutilisé dans l’agrégation si votre ou vos services doivent également pouvoir lire tout le contenu
   * Très spécifique : `asset-linkshare-service`. Il n’est pas si sûr de réutiliser votre service, sauf si celui-ci effectue également un partage de lien des ressources.

* À quoi peuvent ressembler le jeu de fonctionnalités et la configuration des autorisations :

   * L’entité logique doit correspondre à la configuration de l’autorisation :

      * A `content-foo-service` ne doit être associé qu’aux opérations sur le contenu. L’attribution des autorisations pour opérer sur d’autres entités telles que la configuration ou les utilisateurs serait incorrecte.
      * Un service spécifique comme `personalization-foo-service` doit également être fourni avec des autorisations spécifiques. Si vous obtenez des autorisations sur tout le contenu, cela n’est plus spécifique. Réfléchissez-y dans le nom ou réutilisez un utilisateur commun dans l’agrégation.
      * Un service spécifique à une fonctionnalité, tel que `msm-xyz-service` ne doivent posséder que des autorisations liées à msm. N’étendez pas les autorisations aux fonctionnalités non liées telles que la gestion de la configuration des communautés ou la configuration des utilisateurs Screens.

   * La tâche doit correspondre aux autorisations :

      * A `foo-reader-service` ne doit être en mesure de lire que les éléments standard. Ne jamais accorder d’autorisations d’écriture
      * A `foo-writer-service` peuvent être censés effectuer des opérations d’écriture. Cependant, il ne doit pas lui être accordé d’autorisations de lecture/modification du contenu du contrôle d’accès.
      * A `foo-replicator-service` peut avoir la valeur `crx:replicate` accordé.

**Exemples**

Exemples pour `configuration-reader-service`:

* Le nom indique qu’il fait référence aux configurations en général et non à la configuration d’une fonctionnalité particulière, comme la configuration de l’intégration DM. Un utilisateur de service spécifiquement ciblé pour lire la configuration d’une telle intégration doit plutôt être nommé `dmconfig-reader-service` ou `s7config-reader-service`

  >[!NOTE]
  >
  >Aucune information de chemin n’est incluse dans l’attribution de noms. Les configurations ont été déplacées d’ `/etc` to `/conf`.

* L’élément task-element indique que les services liés à cet utilisateur effectuent uniquement des opérations de lecture.

Exemples pour `userproperties-copy-service`:

* Les services liés à cet utilisateur de service fonctionneront sur des propriétés d’utilisateur/de groupe telles que des profils ou des préférences.
* Il est spécifiquement destiné à copier ces informations par opposition à un nom comme `userproperties-writer-service` qui inclurait tous les types d’opérations d’écriture. Par conséquent, il est possible que la configuration des autorisations pour ces tâches de copie autorise uniquement l’ajout d’éléments à un emplacement et la suppression d’éléments à un autre emplacement.

**Bonnes pratiques pour la configuration des autorisations**

* Utilisez toujours la configuration du contrôle d’accès basé sur l’entité de sécurité pour les utilisateurs du service. Pour plus d’informations, voir les exemples ci-dessous :

   * Autoriser les utilisateurs du service à marquer et leurs autorisations comme contenu d’application non modifiable dans la ligne d’horizon
   * Pas besoin de créer des chemins et des structures arborescentes

* N’octroyez que des autorisations, jamais refusez
* Limitez les autorisations.

   * N’accordez que le jeu minimal d’autorisations nécessaire
   * Pour plus d’informations, consultez la [Mappage des privilèges aux éléments](https://jackrabbit.apache.org/oak/docs/security/privilege/mappingtoitems.html) et [Mappage des appels d’API aux privilèges](https://jackrabbit.apache.org/oak/docs/security/privilege/mappingtoprivileges.html) documentation
   * N’accordez pas d’autorisation pour `jcr:all`. Ce n&#39;est probablement pas l&#39;ensemble minimal.

* Réduire la portée

   * Placez des stratégies de contrôle d’accès dans des sous-arborescences spécifiques aux fonctionnalités
   * En cas d’éléments distribués : utilisez des restrictions pour limiter la portée (consultez [la documentation](http://jackrabbit.apache.org/oak/docs/security/authorization/restriction.html) pour la liste des restrictions intégrées).

* Garantir la cohérence

   * Rendre les autorisations cohérentes avec l’entité et la tâche que vous avez utilisées dans le nom d’utilisateur du service
   * Évitez d’ajouter des autorisations non liées. Par exemple, il serait étrange d’avoir une `workflow-administration-service` et lui accorder les autorisations d’effectuer des opérations de gestion des utilisateurs à l’adresse `/home/users/screens` ou laissez-le lire s7-config.

* Complétude

   * Assurez-vous que votre service dispose de toutes les autorisations dont il a besoin pour exécuter les tâches qu’il a été conçu pour exécuter. Votre service doit être prêt à l’emploi, également dans les environnements clients.
   * Ne vous attendez jamais à ce que les clients développent la configuration des autorisations (par exemple, ci-dessous `/apps`)

* Éviter la duplication de la configuration des autorisations

   * Réutiliser les utilisateurs du service commun
   * Regroupez-les avec les utilisateurs de votre service spécifique qui fournissent l’autorisation spécifique dont vous avez besoin en outre.

* Ne fractionnez pas la configuration des autorisations entre différentes fonctionnalités. La nécessité de le faire indique que l’utilisateur de votre service n’est pas bien défini ou fait trop de choses différentes.
* Ne placez pas les utilisateurs du service dans des groupes, car :

   * Il mélange les détails de mise en oeuvre des utilisateurs du service avec des groupes &quot;publics&quot;.
   * Vous ne contrôlez pas les modifications des autorisations (sujets aux régressions et aux réaffectations de privilèges).
   * Performances de la connexion et de l’évaluation
   * Ne fonctionne pas avec la configuration automatique basée sur l’entité

* L’accès au noeud user-home (ou à toute sous-arborescence qui y est contenue), qui n’a pas de chemin d’accès prévisible est obtenu dans le référentiel init à l’aide de home(`userId`). Voir l’initialisation du référentiel sling [documentation](https://sling.apache.org/documentation/bundles/repository-initialization.html) pour plus d’informations.
* RTC : créez un problème RTC dédié si vous modifiez les autorisations d’un utilisateur de service existant et assurez-vous de le faire examiner par l’équipe de sécurité.

**Création avec initialisation du référentiel**

Toujours utiliser `repo-init` pour définir les utilisateurs du service, ainsi que leur configuration des autorisations, et les placer dans la section appropriée du modèle de fonctionnalité Quickstart :

**Bonnes pratiques**

* Toujours utiliser `repo-init` pour créer l’utilisateur du service
* Toujours spécifier un chemin intermédiaire pour la création d’utilisateurs de services
* Tous les utilisateurs du service intégré pour AEM doivent se trouver sous `system/cq:services/internal`
* Ajoutez en outre au chemin relatif intermédiaire le chemin d’accès au groupe des utilisateurs du service par fonction : `system/cq:services/internal/<your-feature>`
* Les utilisateurs du service défini par le client doivent se trouver sous `system/cq:services/<customer-intermediate-rel-path>` et jamais sous l’arborescence interne
* Utilisation **avec chemin forcé** au lieu de **avec chemin** si un utilisateur existe déjà et doit être déplacé vers le nouvel emplacement qui prend en charge l’autorisation basée sur l’entité.

**Exemples**

```
create service user my-new-feature-readcomment-service with path system/cq:services/internal/myfeature
set principal ACL for my-new-feature-readcomment-service
    allow rep:readProperties on /content/myFeature restriction(rep:itemNames,commentTitle,commentDate,commentTxt)
end
```

```
create service user my-existing-feature-addcomment-service with forced path system/cq:services/internal/myfeature
set principal ACL for my-existing-feature-addcomment-service
    allow jcr:addChildNodes,rep:addProperties on /content/myfeature restrictions(rep:glob,*/comments/*)
end
```

```
create service user myfeature-ims-service with path system/cq:services/internal/myfeature
set principal ACL for myfeature-ims-service
    allow jcr:read on home(myfeature-ims-service)
end
```

### Utilisateurs et autorisations du service de nettoyage {#cleanup-service-users-and-permissions}

La commande d’initialisation de référentiel suivante peut être utilisée pour nettoyer les utilisateurs de service inutilisés et leurs autorisations :

```
# Remove the principal-based access control policy for principal my-feature-service
delete principal ACL for my-feature-service

# Remove all resource-based access control entries (ACEs) for principal my-feature-service
delete ACL for my-feature-service

# Disable the service user
disable service user my-feature-service : "My feature is no longer used"

# Remove the service user
delete service my-feature-service 
```

### Utilisateurs du service de test {#testing-service-users}

Il est essentiel d’écrire des tests côté serveur pour les utilisateurs du service et leur configuration des autorisations. Cela permet non seulement de vérifier que votre configuration fonctionne vraiment, mais également de repérer les régressions et les erreurs involontaires lors de la modification du contenu de contrôle d’accès ou des utilisateurs du service.

La variable `com.adobe.granite.testing.clients` La bibliothèque fournit de nombreux utilitaires qui facilitent l’écriture de SST pour les utilisateurs de services.





