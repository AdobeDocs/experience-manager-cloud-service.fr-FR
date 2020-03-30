---
title: ' de contenu'
description: ' de contenu '
translation-type: tm+mt
source-git-commit: 00912ea1085da2c50ec79ac35bd53d36fd8a9509

---


#  de contenu dans AEM en tant que service Cloud {#content-delivery}

La page actuelle détaille le de contenu du service de publication dans AEM en tant que service Cloud. Le de contenu du service de publication comprend :

* CDN (généralement géré par Adobe)
* Répartiteur AEM
* Publication AEM

Le flux de données est le suivant :

1. L’URL est ajoutée dans le navigateur.
1. Requête effectuée sur le réseau de diffusion de contenu mappé à ce domaine dans le DNS
1. Si le contenu est entièrement mis en cache sur le réseau de diffusion de contenu, celui-ci l’affiche dans le navigateur.
1. Si le contenu n’est pas entièrement mis en cache, le réseau de diffusion de contenu appelle Dispatcher (par proxy inverse).
1. Si le contenu est entièrement mis en cache sur Dispatcher, celui-ci l’affiche sur le réseau de diffusion de contenu.
1. Si le contenu n’est pas entièrement mis en cache, Dispatcher appelle la publication AEM (par proxy inverse).
1. Le contenu est rendu par le navigateur, qui peut également le mettre en cache, selon les en-têtes

Le type de contenu HTML/texte est défini pour expirer après 300 s (5 minutes) au niveau de la couche du répartiteur, seuil que le cache du répartiteur et le CDN respectent tous deux. Lors des redéploiements du service de publication, le cache du répartiteur est effacé puis réchauffé avant que les nouveaux noeuds de publication n’acceptent le trafic.

Les sections ci-dessous fournissent des informations plus détaillées sur les  de contenu, notamment la configuration du CDN et la mise en cache.

Des informations sur la réplication du service d’auteur au service de publication sont disponibles [ici](/help/operations/replication.md).

## Réseau de diffusion de contenu {#cdn}

Le service AEM as Cloud est fourni avec un CDN intégré. Son principal objectif est de réduire la latence en diffusant du contenu pouvant être mis en cache à partir des noeuds CDN au bord, près du navigateur. Il est entièrement géré et configuré pour des performances optimales des applications AEM.

Au total, AEM   deux options :

1. CDN géré AEM - CDN prêt à l’emploi d’AEM. Il s’agit d’une option étroitement intégrée qui ne nécessite pas un investissement client important pour prendre en charge l’intégration CDN avec AEM.
1. Le CDN géré par le client pointe vers le CDN géré AEM - le client pointe son propre CDN vers le CDN prêt à l’emploi d’AEM. Le client devra toujours gérer son propre CDN, mais l’investissement dans l’intégration avec AEM est modéré.

La première option doit répondre à la plupart des exigences de performances et de sécurité du client. De plus, cela demande un effort client minimal.

La deuxième option sera autorisée au cas par cas. La décision est basée sur la satisfaction de certaines conditions préalables, y compris, mais sans s’y limiter, le client ayant une intégration héritée avec son fournisseur CDN difficile à abandonner.

Vous trouverez ci-dessous une matrice de décision pour comparer les deux options. Vous trouverez des informations plus détaillées dans les sections qui suivent.

| Détails | CDN géré AEM | Le CDN géré par le client pointe vers le CDN AEM |
|---|---|---|
| **Effort client** | Aucun, il est complètement intégré. Il suffit de pointer CNAME vers le CDN géré AEM. | Modérez l’investissement des clients. Le client doit gérer son propre CDN. |
| **Conditions préalables** | Aucun | Le CDN existant est onéreux à remplacer. Doit démontrer un test de charge réussi avant de commencer à fonctionner. |
| **expertise CDN** | Aucun | Nécessite au moins une ressource d&#39;ingénierie à temps partiel avec une connaissance approfondie du réseau de diffusion de contenu capable de configurer le réseau de diffusion de contenu du client. |
| **Sécurité** | Géré par Adobe. | Géré par Adobe (et éventuellement par le client sur son propre CDN). |
| **Les performances** | Optimisé par Adobe. | Bénéficiera de certaines fonctionnalités de CDN AEM, mais peut-être d’un faible accès aux performances en raison du saut supplémentaire. **Remarque**: Des sauts de CDN client à Fast CDN susceptibles d&#39;être efficaces). |
| **Mise en cache** | Prend en charge les en-têtes de cache appliqués au répartiteur. | Prend en charge les en-têtes de cache appliqués au répartiteur. |
| **Fonctions de compression d’images et de vidéos** | Peut fonctionner avec Adobe Dynamic Media. | Peut fonctionner avec Adobe Dynamic Media ou avec la solution d’image/vidéo CDN gérée par le client. |

### CDN géré AEM {#aem-managed-cdn}

La préparation du de contenu à l’aide du CDN prêt à l’emploi d’Adobe est simple, comme décrit ci-dessous :

1. Vous fournirez le certificat SSL et la clé secrète signés à Adobe en partageant un lien vers un formulaire sécurisé contenant ces informations. Veuillez vous coordonner avec le service clientèle sur ce .
   **Remarque :** Aem as a Cloud Service ne prend pas en charge les certificats DV (Domain Validated).
1. Vous devez informer le service clientèle :
   * quel domaine personnalisé doit être associé à un   donné, tel que défini par l’ID de et l’ID de.
   * si une liste blanche d’adresses IP est nécessaire pour limiter le trafic à un   donné.
1. Le service clientèle coordonnera alors avec vous le timing d’un enregistrement DNS CNAME, en pointant son nom de domaine complet vers `adobe-aem.map.fastly.net`.
1. Vous serez averti(e) lorsque les certificats SSL arriveront à expiration afin de pouvoir soumettre à nouveau les nouveaux certificats SSL.

**Limitation du trafic**

Par défaut, dans le cas d’une configuration CDN gérée par Adobe, tout le trafic public peut se diriger vers le service de publication, tant pour la production que pour la non-production (développement et étape)  . Si vous souhaitez limiter le trafic au service de publication pour un   donné (par exemple, limiter l’évaluation par une plage d’adresses IP), vous devez demander au service clientèle de configurer ces restrictions.

### Le CDN du client pointe vers le CDN géré AEM {#point-to-point-CDN}

Pris en charge si vous souhaitez utiliser votre CDN existant, mais ne pouvez pas satisfaire aux exigences d’un CDN géré par le client. Dans ce cas, vous gérez votre propre CDN, mais pointez sur le CDN géré par Adobe.

Veuillez prendre note que :

1. Vous devez avoir un CDN existant.
1. Tu dois le gérer.
1. Vous devez être en mesure de configurer le CDN pour travailler avec Aem en tant que service Cloud. Reportez-vous aux instructions de configuration ci-dessous.
1. Vous devez avoir des experts en ingénierie de CDN qui sont sur appel au cas où des problèmes liés à votre projet se poseraient.
1. Vous devez effectuer et réussir un test de charge avant d’accéder à la production.

Instructions de configuration :

1. Définissez l’ `X-Forwarded-Host` en-tête avec le nom de domaine.
1. Définissez l’en-tête de l’hôte avec le domaine  du, qui est l’entrée CDN d’Adobe. La valeur doit provenir d’Adobe.
1. Envoyez l’en-tête SNI au  . Tout comme l’en-tête Hôte, l’en-tête sni doit être le domaine  .
1. Définissez le `X-Edge-Key`, qui est nécessaire pour acheminer correctement le trafic vers les serveurs AEM. La valeur doit provenir d’Adobe.

Avant d’accepter le trafic en direct, vous devez vérifier auprès de l’assistance clientèle d’Adobe que le de trafic de bout en bout fonctionne correctement.

## Mise en cache {#caching}

La mise en cache sur le CDN peut être configurée à l’aide des règles du répartiteur. Notez que le répartiteur respecte également les en-têtes d’expiration du cache qui en résultent si `enableTTL` est activé dans la configuration du répartiteur, ce qui implique qu’il actualisera un contenu spécifique même en dehors du contenu en cours de republication.

### HTML/Texte {#html-text}

* par défaut, mis en cache par le navigateur pendant cinq minutes, en fonction de l’en-tête de contrôle du cache émis par le calque apache. Le CDN respecte également cette valeur.
* peut être remplacé pour tout le contenu HTML/texte en définissant la `EXPIRATION_TIME` variable dans `global.vars` l’utilisation d’AEM en tant qu’outil de répartiteur de SDK de service cloud.

Vous devez vous assurer qu’un fichier sous `src/conf.dispatcher.d/cache` comporte la règle suivante :

```
/0000
{ /glob "*" /type "allow" }
```

* peuvent être remplacées à un niveau de grains plus fin par les directives apache mod_headers suivantes :

```
<LocationMatch "\.(html)$">
        Header set Cache-Control "max-age=200"
</LocationMatch>
```

Vous devez vous assurer qu’un fichier sous `src/conf.dispatcher.d/cache` comporte la règle suivante (qui se trouve dans la configuration par défaut) :

```
/0000
{ /glob "*" /type "allow" }
```

* Notez que d’autres méthodes, y compris le projet [](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/)dispatcher-ttl AEM ACS Commons, ne remplaceront pas les valeurs.

### Bibliothèques côté client (js, css) {#client-side-libraries}

* en utilisant la structure de bibliothèque côté client d’AEM, le code JavaScript et CSS est généré de manière à ce que les navigateurs puissent le mettre en cache indéfiniment, puisque toute modification se manifeste sous la forme de nouveaux fichiers avec un chemin d’accès unique.  En d’autres termes, du code HTML faisant référence aux bibliothèques clientes sera produit au besoin afin que les clients puissent découvrir un nouveau contenu au fur et à mesure de sa publication. Le contrôle du cache est défini sur &quot;immuable&quot; ou 30 jours pour les navigateurs plus anciens qui ne respectent pas la valeur &quot;immuable&quot;.
* voir la section Bibliothèques côté [client et cohérence](#content-consistency) des versions pour en savoir plus.

### Images et tout contenu suffisamment volumineux pour être stockés dans l’objet blob  {#images}

* par défaut, non mis en cache
* peuvent être définies à un niveau de granularité plus fin par les directives apache `mod_headers` suivantes :

```
<LocationMatch "^.*.jpeg$">
    Header set Cache-Control "max-age=222"
</LocationMatch>
```

Il est nécessaire de s’assurer qu’un fichier sous src/conf.dispatcher.d/cache comporte la règle suivante (qui se trouve dans la configuration par défaut) :

```
/0000
{ /glob "*" /type "allow" }
```

Assurez-vous que les ressources destinées à être conservées en privé plutôt que mises en cache ne font pas partie du  de directive LocationMatch.

* Notez que d’autres méthodes, y compris le projet [](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/)dispatcher-ttl AEM ACS Commons, ne remplaceront pas les valeurs.

### Autres types de fichiers de contenu dans le magasin de noeuds {#other-content}

* aucune mise en cache par défaut
* default ne peut pas être défini avec la `EXPIRATION_TIME` variable utilisée pour les types de fichiers html/texte
* l’expiration du cache peut être définie avec la même stratégie LocationMatch décrite dans la section html/texte en spécifiant l’expression regex appropriée.

## Dispatcher {#disp}

Le trafic passe par un serveur Web Apache, qui prend en charge les modules, y compris le répartiteur. Le répartiteur est principalement utilisé comme cache pour limiter le traitement sur les noeuds de publication afin d’améliorer les performances.

Comme décrit dans la section de mise en cache du CDN, des règles peuvent être appliquées à la configuration du répartiteur pour modifier les paramètres d’expiration du cache par défaut.

Le reste de cette section décrit les considérations liées à l’invalidation du cache du répartiteur. Pour la plupart des clients, il ne doit pas être nécessaire d’invalider le cache du répartiteur, mais plutôt de compter sur le répartiteur pour actualiser son cache lors de la republication du contenu et sur le CDN pour respecter les en-têtes d’expiration du cache.

### Invalidation du cache Dispatcher pendant l’activation/la désactivation {#cache-activation-deactivation}

Comme les versions précédentes d’AEM, la publication ou l’annulation de publication des pages effacera le contenu du cache du répartiteur. Si un problème de mise en cache est suspecté, les clients doivent republier les pages en question.

Lorsque l’instance de publication reçoit une nouvelle version d’une page ou d’un fichier de l’auteur, elle utilise l’agent de vidage pour invalider les chemins appropriés sur son répartiteur. The updated path is removed from the dispatcher cache, together with its parents, up to a level (you can configure this with the [statfileslevel](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#invalidating-files-by-folder-level).

### Invalidation explicite du cache Dispatcher {#explicit-invalidation}

En général, il n’est pas nécessaire d’invalider manuellement le contenu dans le répartiteur, mais cela est possible si nécessaire, comme décrit ci-dessous.

Avant AEM en tant que service Cloud, il existait deux manières d’invalider le cache du répartiteur.

1. Appeler l’agent de réplication, en spécifiant l’agent de vidage du répartiteur de publication
2. Appel direct de l’ `invalidate.cache` API (par exemple, `POST /dispatcher/invalidate.cache`)

The dispatcher&#39;s `invalidate.cache` API approach will no longer be supported since it addresses only a specific dispatcher node. Le service AEM en tant que service Cloud fonctionne au niveau du service, et non au niveau du noeud individuel. Les instructions d’invalidation figurant dans la page [Invalidation des pages mises en cache à partir de la page AEM](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/page-invalidate.html) ne sont donc plus valides pour AEM en tant que service Cloud.
L&#39;agent de purge de réplication doit être utilisé. Vous pouvez le faire à l’aide de l’API de réplication. The Replication API documentation is available [here](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/Replicator.html) and for an example of flushing the cache, see the [API example page](https://helpx.adobe.com/experience-manager/using/aem64_replication_api.html) specifically the `CustomStep` example issuing a replication action of type ACTIVATE to all available agents. Le point de fin de l’agent de vidage n’est pas configurable, mais il est préconfiguré pour pointer vers le répartiteur, en correspondance avec le service de publication exécutant l’agent de vidage. L&#39;agent de vidage peut généralement être déclenché par  de OSGi ou par  de.

Le diagramme présenté ci-dessous illustre cette situation.

![](assets/cdnc.png "CDNCDN")

Si le cache du répartiteur n’est pas effacé, contactez le service à la [clientèle](https://helpx.adobe.com/support.ec.html) qui peut vider le cache du répartiteur si nécessaire.

Le CDN géré par Adobe respecte les TTL et il n’est donc pas nécessaire qu’il soit vidé. Si un problème est suspecté, [contactez le service d’assistance](https://helpx.adobe.com/support.ec.html) clientèle qui peut vider un cache CDN géré par Adobe si nécessaire.

## Bibliothèques côté client et cohérence de version {#content-consistency}

Les pages sont composées de code HTML, JavaScript, CSS et d’images. Les clients sont encouragés à tirer parti de la structure des bibliothèques côté client (clientlibs) pour importer des ressources JavaScript et CSS dans des pages HTML, en tenant compte des dépendances entre les bibliothèques JS.

La structure clientlibs fournit une gestion automatique des versions, ce qui signifie que les développeurs peuvent archiver les modifications apportées aux bibliothèques JS dans le contrôle de code source et que la dernière version sera disponible lorsqu’un client poussera sa version. Sans cela, les développeurs devraient modifier manuellement le code HTML avec des références à la nouvelle version de la bibliothèque, ce qui est particulièrement onéreux si de nombreux modèles HTML partagent la même bibliothèque.

Lorsque les nouvelles versions des bibliothèques sont publiées en production, les pages HTML de référence sont mises à jour avec de nouveaux liens vers ces versions de bibliothèques mises à jour. Une fois que le cache du navigateur a expiré pour une page HTML donnée, il n’est plus possible que les anciennes bibliothèques soient chargées à partir du cache du navigateur, car il est désormais garanti que la page actualisée (à partir d’AEM) référencera les nouvelles versions des bibliothèques. En d’autres termes, une page HTML actualisée comprend toutes les dernières versions des bibliothèques.

Il s’agit d’un hachage sérialisé, qui est annexé au lien de la bibliothèque cliente, garantissant ainsi une URL avec version unique pour le navigateur afin de mettre en cache le fichier CSS/JS. Le hachage sérialisé n’est mis à jour que lorsque le contenu de la bibliothèque cliente change. En d’autres termes, si des mises à jour non liées se produisent (c’est-à-dire qu’aucune modification n’est apportée au fichier css/js sous-jacent de la bibliothèque cliente) même avec un nouveau déploiement, la référence reste la même, ce qui évite toute perturbation du cache du navigateur.

### Activation des versions Longcache des bibliothèques côté client - AEM en tant que SDK de service Cloud Quickstart {#enabling-longcache}

La bibliothèque cliente par défaut inclut sur une page HTML l’exemple suivant :

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.css" type="text/css">
```

Lorsque le contrôle de version strict clientlib est activé, une clé de hachage à long terme est ajoutée en tant que sélecteur à la bibliothèque cliente. Par conséquent, la référence clientlib ressemble à ceci :

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.lc-7c8c5d228445ff48ab49a8e3c865c562-lc.css" type="text/css">
```

Le contrôle de version strict de clientlib est activé par défaut dans tous les AEM en tant que de services  Cloud.

Pour activer le contrôle de version strict de clientlib dans le kit SDK Quickstart local, effectuez les actions suivantes :

1. Accédez au gestionnaire de configuration OSGi <host>/system/console/configMgr
1. Recherchez la configuration OSGi pour le Gestionnaire de bibliothèques HTML Granite d’Adobe :
   * Cochez la case pour activer le contrôle de version strict.
   * Dans le champ intitulé Clé de cache côté client à long terme, saisissez la valeur de /.*;hachage
1. Enregistrez les modifications. Notez qu’il n’est pas nécessaire d’enregistrer cette configuration dans le contrôle de code source, car AEM en tant que service Cloud activera automatiquement cette configuration dans les  de développement, d’évaluation et de production .
1. Chaque fois que le contenu de la bibliothèque cliente est modifié, une nouvelle clé de hachage est générée et la référence HTML est mise à jour.
