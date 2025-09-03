---
title: Bonnes pratiques pour le mappage des utilisateurs et des utilisatrices de service et la définition des utilisateurs et des utilisatrices de service dans Sling
description: Découvrir les bonnes pratiques pour le mappage des utilisateurs et des utilisatrices de service et la définition des utilisateurs et des utilisatrices de service dans Sling
exl-id: 72f0dcbf-b4e6-4a73-8232-3574a212ac19
feature: Security
role: Admin
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: ht
source-wordcount: '1883'
ht-degree: 100%

---

# Bonnes pratiques pour le mappage des utilisateurs et des utilisatrices de service et la définition des utilisateurs et des utilisatrices de service dans Sling {#best-practices-for-sling-service-user-mapping-and-service-user-definition}

## Mappage d’utilisateurs et d’utilisatrices de service {#service-user-mapping}

Pour ajouter un mappage de votre service aux utilisateurs et utilisatrices système correspondants, vous devez créer une configuration d’usine pour le service `ServiceUserMapper`. Afin de rester dans un fonctionnement modulaire, de telles configurations peuvent être fournies à l’aide du mécanisme « d’amendement » Sling (voir [SLING-3578](https://issues.apache.org/jira/browse/SLING-3578) pour plus d’informations). La méthode recommandée pour installer de telles configurations avec votre lot consiste à l’ajouter au modèle d’approvisionnement de démarrage rapide, comme décrit dans l’exemple suivant :

```
org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended-my-mapping
    user.default=""
    user.mapping=[
        "com.adobe.cq.my-bundle:my-subservice\=[content-writer-service]",
        "com.adobe.cq.my-bundle:my-subservice-different-task\="[myfeature-configuration-writer-service,content-reader-service]"
    ]
```

### Format de mappage {#mapping-format}

Depuis AEM 6.4, le format de mappage est défini comme suit :

>[!NOTE]
>
>Le composant `userName` est obsolète et ne doit plus être utilisé.

```
bundleId [:subserviceName] = userName | [principalNames]   
```

`bundleId` et `subserviceName` identifient le service, `userName/principalNames` identifie l’utilisateur ou l’utilisatrice de service et `principalNames` est une liste séparée par des virgules.

Notez également que `principalNames` est la liste des noms principaux des utilisateurs et des utilisatrices de service qui, par défaut, sont identiques aux identifiants.


**Bonne pratique**

* Noms de sous-service pour différentes tâches : si les services de votre lot effectuent différentes tâches, il est recommandé d’identifier les `subserviceNames` pour les regrouper par tâches.
* Si un service donné effectue différentes opérations (par exemple, la lecture du contenu d’une ressource et la mise à jour d’informations dans une sous-arborescence de `/var`), il est recommandé de refléter cela en agrégeant différentes entités de service qui reflètent l’opération individuelle, en agrégeant par exemple le `dam-reader-service` commun avec votre `assetreport-writer-service` spécifique à une fonction.
* Chaque service est idéalement lié à un ensemble d’opérations très spécifique et limité.
* Le nouveau format avec `[one,or,multiple,principalNames]` est la méthode recommandée pour définir des mappages d’utilisateurs et d’utilisatrices de service à partir d’AEM 6.4.

Vous trouverez ci-dessous une liste des raisons justifiant de modifier le format et pourquoi Adobe vous recommande de l’utiliser au lieu d’un mappage de version uniquement pour un seul identifiant d’utilisateur ou d’utilisatrice :

* Possibilité de réutiliser les utilisateurs et les utilisatrices de service en combinant les besoins spécifiques des clientes et des clients avec des tâches courantes
* Éviter la duplication des configurations d’autorisations
* Meilleure compréhension des autorisations (et des tâches) réelles gérées par un service donné
* Pas d’obligation d’appartenance explicite à un groupe pour les utilisateurs et les utilisatrices de service. Cela peut avoir des effets secondaires problématiques lorsque les autorisations du groupe sont modifiées.
* Améliorations des performances et évolutivité

## Résolution de mappage et connexion au service {#mapping-resolution-and-service-login}

### Résolution du mappage des services {#service-mapping-resolution}

La séquence d’appels pour résoudre le mappage des services est décrite ci-dessous :

1. Rechercher un mappage `principalNames` actif pour les `bundleId` et `subserviceName` donnés
1. Mappage de `principalNames` pour le `bundleId` et le `subserviceName` null
1. Mappage de `userName` pour le `bundleId` et le `subserviceName`
1. Mappage de `userName` pour le `bundleId` et le `subserviceName` null
1. Mappage par défaut
1. Utilisateur ou utilisatrice par défaut

### Référentiel Sling - Connexion au service {#slingrepository-servicelogin}

La séquence d’obtention d’un service `Session/ResourceResolver` fonctionne comme suit :

1. Obtenez les noms principaux à partir de `ServiceUserMapper` => connectez-vous au référentiel avec pré-authentification comme décrit ci-dessous.
1. Récupérez l’identifiant de l’utilisateur ou de l’utilisatrice à partir de `ServiceUserMapper`.
1. Recherchez une `1ServiceUserConfiguration` obsolète pour l’ID d’utilisateur ou d’utilisatrice actuel.
1. Connectez-vous au service Sling par défaut avec l’identifiant de l’utilisateur ou de l’utilisatrice (par exemple, une séquence de `createAdministrativeSession` avec emprunt de l’identité de l’identifiant de l’utilisateur ou de l’utilisatrice de service).

Le nouveau mappage avec les noms principaux entraîne la connexion simplifiée suivante au référentiel :

* Un jeu de noms principaux est traité comme la ou les entités à utiliser pour renseigner `Subject`.
* La connexion au référentiel peut par conséquent être préauthentifiée.
* Pas de résolution d’appartenance à un groupe.

  >[!NOTE]
  >
  >Toutes les autorisations requises doivent être déclarées pour les utilisateurs et les utilisatrices de service. L’autorisation « tout le monde » et les autres autorisations de groupe ne sont plus héritées.

* Aucune connexion d’administration supplémentaire n’est créée pour disposer du service `Session/ResourceResolver`.

### ServiceUserConfiguration obsolète {#deprecated-serviceUserConfiguration}

Notez que le fait de spécifier un seul nom d’utilisateur ou d’utilisatrice dans le mappage est similaire au `ServiceUserConfiguration.simpleSubjectPopulation` existant. Avec le nouveau format, la solution fournie par `ServiceUserConfiguration` peut être directement appliquée à l’aide du mappage des utilisateurs et des utilisatrices de service. `ServiceUserConfiguration` a donc été abandonné pour AEM et toutes ses utilisations existantes ont été remplacées.

## Utilisateurs et utilisatrices de service {#service-users}

### Réutiliser des utilisateurs et des utilisatrices de service existants {#reusing-existing-service-users}

Il est recommandé de réutiliser les utilisateurs et utilisatrices de service existants si les conditions suivantes sont remplies :

* Vos besoins correspondent aux intentions des utilisateurs et utilisatrices de service existants.
* Votre service nécessite d’effectuer une tâche courante qui est assurée par des utilisateurs et utilisatrices de service courants et existants. Dans ce cas, il est recommandé de réutiliser les utilisateurs et utilisatrices de service au lieu d’impliquer une duplication.
* Votre service nécessite une tâche spécifique assurée par des utilisateurs et utilisatrices de service existants. Si vous n’en avez pas la certitude, demandez à l’équipe chargée des fonctionnalités qui la possède.

Ne réutilisez pas les utilisateurs et les utilisatrices de service existants dans les cas suivants :

* Vous devez modifier leurs autorisations concernant d’autres éléments pour que cela fonctionne.
* Si vous n’avez besoin que d’un petit sous-ensemble des autorisations que ceux-ci fournissent et que vous les réutilisez uniquement parce que cela permet à votre fonctionnalité de fonctionner, et non en raison d’une correspondance réelle.
* Si leur nom indique une intention totalement différente de celle dont vous avez besoin. Choisir cette option uniquement parce que c’est celle qui fonctionne peut entraîner des problèmes dans le futur, car l’équipe chargée des fonctionnalités qui est propriétaire d’un service spécifique peut modifier les autorisations et entraîner une détérioration du fonctionnement de votre fonctionnalité.

### Créer un utilisateur ou une utilisatrice de service {#creating-a-service-user}

Après avoir vérifié qu’aucun utilisateur ni aucune utilisatrice de service dans AEM ne peut correspondre à votre cas d’utilisation et que les problèmes RTC correspondants ont été approuvés, vous pouvez poursuivre et ajouter le nouvel utilisateur ou la nouvelle utilisatrice au contenu par défaut. Idéalement, une personne membre de l’équipe de sécurité étendue est impliquée dans le vote RTC, assurez-vous donc d’impliquer également les parties prenantes appropriées.

**Convention de nommage**

L’équipe de sécurité d’AEM a défini la convention de nommage suivante pour que les utilisateurs et les utilisatrices de service ajoutent de la cohérence pour les nouveaux utilisateurs et les nouvelles utilisatrices de service et améliorent leur lisibilité et leur maintenance.

Un nom d’utilisateur ou d’utilisatrice de service est composé de 3 éléments séparés par un tiret **« - »** :

1. L’entité/la fonctionnalité logique ciblée par les opérations du service (évitez les fragments de chemins susceptibles d’être modifiés).
1. La tâche que les services vont effectuer.
1. L’élément **« service »** à la fin pour repérer facilement à partir de l’identifiant et du nom principal que l’utilisateur ou l’utilisatrice est un utilisateur ou une utilisatrice de service.

**Bonnes pratiques**

* Ne mélangez pas différentes entités/fonctionnalités. Partagez-les entre des utilisateurs et des utilisatrices de service individuels et agrégez-les dans le mappage si votre service a des besoins différents.
* Limitez-vous à une tâche bien définie par utilisateur ou utilisatrice de service. Partagez-la si vous devez accorder trop d’autorisations ou des autorisations sans rapport avec celle-ci.
* Prenez le temps d’identifier le besoin réel de votre service.
* Prenez le temps de trouver un nom d’utilisateur ou d’utilisatrice de service adapté, explicite et représentatif.
* Demandez des commentaires et des avis : les développeurs et les développeuses qui ne connaissent pas votre fonctionnalité doivent être en mesure de lire et de comprendre vos intentions. Ils pourraient à l’avenir être chargés de réaliser des corrections ou de la maintenance sur celle-ci.

En fin de compte, le nom d’utilisateur ou d’utilisatrice de service doit montrer les éléments suivants :

* Comment il est destiné à être utilisé et s’il peut être réutilisé :

   * Très générique : `content-writer-service`. Il peut être réutilisé sans risque pour une agrégation si votre ou vos services doivent également pouvoir lire tout le contenu.
   * Très spécifique : `asset-linkshare-service`. Il ne peut pas être réutilisé sans risque, sauf si votre service effectue également un partage de lien des ressources.

* Voici à quoi peuvent ressembler le jeu de fonctionnalités et la configuration des autorisations :

   * L’entité logique doit correspondre à la configuration des autorisations :

      * Un `content-foo-service` ne doit être associé qu’aux opérations sur le contenu. Il serait incorrect de lui attribuer des autorisations pour opérer sur d’autres entités telles que la configuration ou les utilisateurs et les utilisatrices.
      * Un service spécifique tel que `personalization-foo-service` doit également disposer d’autorisations spécifiques. Si vous accordez des autorisations sur tout le contenu, celles-ci ne sont plus spécifiques. Indiquez cela dans le nom ou réutilisez des utilisateurs et utilisatrices communs dans l’agrégation.
      * Un service spécifique à une fonctionnalité, tel que `msm-xyz-service`, ne doit posséder que des autorisations liées à MSM. N’étendez pas les autorisations à des fonctionnalités différentes telles que la gestion de la configuration des communautés ou la configuration des utilisateurs et des utilisatrices Screens.

   * La tâche doit correspondre aux autorisations :

      * Un `foo-reader-service` ne doit être en mesure de lire que les éléments standard. N’accordez jamais d’autorisations d’écriture.
      * Un `foo-writer-service` peut être amené à effectuer des opérations d’écriture. Cependant, il ne doit pas lui être accordé d’autorisations de lecture ou de modification du contrôle d’accès au contenu.
      * Un `foo-replicator-service` peut être amené à devoir disposer de l’autorisation `crx:replicate`.

**Exemples**

Exemples pour `configuration-reader-service` :

* Le nom indique qu’il fait référence aux configurations en général et non à la configuration d’une fonctionnalité particulière, telle que la configuration de l’intégration DM. Un utilisateur de service spécifiquement ciblé ou une utilisatrice de service spécifiquement ciblée pour lire la configuration d’une telle intégration doit plutôt porter le nom `dmconfig-reader-service` ou `s7config-reader-service`.

  >[!NOTE]
  >
  >Aucune information de chemin n’est incluse dans les noms. Les configurations ont été déplacées de `/etc` vers `/conf`.

* La section task-element indique que les services liés à cet utilisateur ou à cette utilisatrice n’effectuent que des opérations de lecture.

Exemples pour `userproperties-copy-service` :

* Les services liés à cet utilisateur ou à cette utilisatrice de service vont agir sur des propriétés d’utilisateur ou d’utilisatrice ou de groupe, telles que des profils ou des préférences.
* Il est spécifiquement destiné à uniquement copier ces informations, par opposition à un nom comme `userproperties-writer-service` qui inclut d’autres types d’opérations d’écriture. Par conséquent, il est possible que la configuration des autorisations pour ces tâches de copie autorise uniquement l’ajout d’éléments à un emplacement donné, et la suppression d’éléments à un autre emplacement.

**Bonnes pratiques relatives à la configuration des autorisations**

* Utilisez toujours la configuration de contrôle d’accès basée sur une entité pour les utilisateurs et les utilisatrices de service. Pour plus d’informations, consultez les exemples ci-dessous :

   * Autorisez le marquage des utilisateurs et des utilisatrices de service et de leurs autorisations comme du contenu d’application non modifiable dans Skyline.
   * Il n’est pas nécessaire de créer des chemins et des structures d’arborescence.

* Vous devez seulement accorder des autorisations : ne les révoquez jamais.
* Limiter les autorisations

   * N’accordez que l’ensemble minimum d’autorisations nécessaire.
   * Pour plus d’informations, consultez la documentation relative au [Mappage des privilèges aux éléments](https://jackrabbit.apache.org/oak/docs/security/privilege/mappingtoitems.html) et au [Mappage des appels API aux privilèges](https://jackrabbit.apache.org/oak/docs/security/privilege/mappingtoprivileges.html).
   * N’accordez pas d’autorisations pour `jcr:all`. Il ne s’agit probablement pas de l’ensemble minimum.

* Réduire la portée

   * Placez des politiques de contrôle d’accès dans des sous-arborescences spécifiques aux fonctionnalités.
   * En cas d’éléments distribués : utilisez des restrictions pour limiter la portée (consultez [la documentation](https://jackrabbit.apache.org/oak/docs/security/authorization/restriction.html) pour la liste des restrictions intégrées).

* Garantir la cohérence

   * Assurez la cohérence des autorisations par rapport à l’entité et à la tâche que vous avez utilisées dans le nom d’utilisateur ou d’utilisatrice de service.
   * Évitez d’ajouter des autorisations sans rapport. Par exemple, il serait étrange d’accorder à un `workflow-administration-service` l’autorisation d’effectuer des opérations de gestion des utilisateurs et des utilisatrices dans `/home/users/screens` ou de lui permettre de lire s7-config.

* Exhaustivité

   * Assurez-vous que votre service dispose de toutes les autorisations dont il a besoin pour exécuter les tâches pour lesquelles il est conçu. Votre service doit être prêt à l’emploi, y compris dans les environnements clients.
   * Ne vous attendez jamais à ce que les clientes et clients étendent la configuration des autorisations, et ne leur demandez pas non plus (voir l’exemple ci-dessous `/apps`).

* Éviter la duplication des configurations d’autorisations

   * Réutilisez les utilisateurs et les utilisatrices de service communs.
   * Regroupez-les avec vos utilisateurs et vos utilisatrices de service spécifiques à une fonctionnalité qui fournissent en plus l’autorisation spécifique dont vous avez besoin.

* Ne fractionnez pas la configuration des autorisations entre différentes fonctionnalités. Si vous avez à le faire, cela indique que votre utilisateur ou utilisatrice de service n’a pas une définition correcte ou effectue trop d’actions différentes.
* Ne placez pas les utilisateurs et les utilisatrices de service dans des groupes, pour les raisons suivantes :

   * Cela mélange les informations d’implémentation des utilisateurs et des utilisatrices de service avec des groupes « publics ».
   * Vous ne contrôlez pas les modifications des autorisations (sujettes aux révocations et aux octrois de privilèges).
   * Performances de connexion et d’évaluation
   * Ne fonctionne pas avec une configuration de contrôle d’accès basée sur une entité.

* L’accès au nœud user-home (ou à toute sous-arborescence qu’il contient), qui n’a pas de chemin d’accès prévisible, est obtenu par l’initialisation du référentiel (repo init) à l’aide de home(`userId`). Consultez la [documentation](https://sling.apache.org/documentation/bundles/repository-initialization.html) Sling relative à l’initialisation du référentiel (repo init) pour plus d’informations.
* RTC : créez un problème RTC dédié si vous modifiez les autorisations d’un utilisateur ou d’une utilisatrice de service qui existe et assurez-vous de le faire examiner par l’équipe de sécurité.

**Création avec l’initialisation du référentiel**

Utilisez toujours `repo-init` pour définir les utilisateurs et les utilisatrices de service, ainsi que la configuration de leurs autorisations, et placez-les dans la section appropriée du modèle de fonctionnalité Quickstart :

**Bonnes pratiques**

* Utilisez toujours `repo-init` pour créer une utilisateur ou une utilisatrice de service.
* Spécifiez toujours un chemin intermédiaire pour la création d’utilisateurs et d’utilisatrices de service.
* Tous les utilisateurs et utilisatrices de service intégrés dans AEM doivent se trouver sous `system/cq:services/internal`.
* Ajoutez ceci au chemin relatif intermédiaire pour regrouper les utilisateurs et les utilisatrices de service par fonctionnalité : `system/cq:services/internal/<your-feature>`.
* Les utilisateurs et les utilisatrices de service définis par le client ou la cliente doivent se trouver sous `system/cq:services/<customer-intermediate-rel-path>`, et jamais sous l’arborescence interne.
* Utilisez un **chemin forcé** au lieu d’un **chemin** si un utilisateur ou une utilisatrice existe déjà et doit se voir déplacer vers le nouvel emplacement qui prend en charge l’autorisation basée sur une entité.

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

### Nettoyer les utilisateurs et utilisatrices de service et les autorisations {#cleanup-service-users-and-permissions}

La commande d’initialisation de référentiel (repo init) suivante peut être utilisée pour nettoyer les utilisateurs et les utilisatrices de service inutilisés et leurs autorisations :

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

### Tester les utilisateurs et les utilisatrices de service {#testing-service-users}

Il est essentiel d’écrire des tests côté serveur pour les utilisateurs et les utilisatrices de service et pour la configuration de leurs autorisations. Cela permet non seulement de vérifier que votre configuration fonctionne en pratique, mais également de repérer les révocations et les erreurs imprévues lors de modifications du contenu de contrôle d’accès ou des utilisateurs et des utilisatrices de service.

La bibliothèque `com.adobe.granite.testing.clients` fournit de nombreux utilitaires qui facilitent l’écriture de SST pour les utilisateurs et les utilisatrices de service.
