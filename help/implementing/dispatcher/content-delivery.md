---
title: ' Diffusion de contenu'
description: ' Diffusion de contenu '
translation-type: ht
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14

---


# Diffusion de contenu dans AEM as a Cloud Service {#content-delivery}

La page actuelle détaille la diffusion du contenu du service de publication dans AEM as a Cloud Service. La diffusion du contenu du service de publication comprend :

* CDN (généralement géré par Adobe)
* AEM Dispatcher
* Publication AEM

Le flux de données est le suivant :

1. L’URL est ajoutée dans le navigateur.
1. Requête effectuée sur le réseau de diffusion de contenu mappé à ce domaine dans le DNS
1. Si le contenu est entièrement mis en cache sur le réseau de diffusion de contenu, celui-ci l’affiche dans le navigateur.
1. Si le contenu n’est pas entièrement mis en cache, le réseau de diffusion de contenu appelle Dispatcher (par proxy inverse).
1. Si le contenu est entièrement mis en cache sur Dispatcher, celui-ci l’affiche sur le réseau de diffusion de contenu.
1. Si le contenu n’est pas entièrement mis en cache, Dispatcher appelle la publication AEM (par proxy inverse).
1. Le rendu du contenu est effectué par le navigateur, qui peut également le mettre en cache, selon les en-têtes

Le type de contenu HTML/texte est défini pour expirer après 300 s (5 minutes) au niveau de la couche du Dispatcher, un seuil que le cache du Dispatcher et le réseau de diffusion de contenu respectent. Lors des redéploiements du service de publication, le cache du Dispatcher est effacé puis réchauffé avant que les nouveaux nœuds de publication n’acceptent le trafic.

Les sections ci-dessous fournissent des informations plus détaillées sur la diffusion de contenu, notamment la configuration du CDN et la mise en cache.

Des informations sur la réplication du service de création vers le service de publication sont disponibles [ici](/help/operations/replication.md).

## Réseau de diffusion de contenu {#cdn}

AEM as a Cloud Service est fourni avec un réseau de diffusion de contenu intégré. Son principal objectif est de réduire la latence en fournissant du contenu pouvant être mis en cache à partir des nœuds CDN en périphérie, près du navigateur. Il est entièrement géré et configuré afin de permettre des performances optimales des applications AEM.

Au total, AEM offre deux options :

1. Réseau de diffusion de contenu géré par AEM, le réseau de diffusion de contenu prêt à l’emploi d’AEM. Il s’agit d’une option étroitement intégrée qui ne nécessite pas d’investissement client important dans la prise en charge de l’intégration du réseau de diffusion de contenu avec AEM.
1. Le réseau de diffusion de contenu géré par le client pointe vers le réseau de diffusion de contenu géré par AEM ; le client pointe son propre réseau de diffusion de contenu vers le réseau de diffusion de contenu prêt à l’emploi d’AEM. Le client devra toujours gérer son propre réseau de diffusion de contenu, mais l’investissement dans l’intégration avec AEM est modéré.

La première option devrait répondre à la plupart des exigences en matière de performances et de sécurité du client. De plus, elle demande un effort minimal au client.

La deuxième option sera autorisée au cas par cas. La décision est basée sur la satisfaction de certaines conditions préalables, y compris, mais sans s’y limiter, le fait que le client possède une intégration héritée avec son fournisseur de réseau de diffusion de contenu difficile à abandonner.

Vous trouverez ci-dessous une matrice de décision pour comparer les deux options. Vous trouverez des informations plus détaillées dans les sections qui suivent.

| Détails | Réseau de diffusion de contenu géré AEM | Le réseau de diffusion de contenu géré par le client pointe vers le réseau de diffusion de contenu AEM |
|---|---|---|
| **Effort du client** | Aucun, le réseau est complètement intégré. Il suffit de pointer CNAME vers le réseau de diffusion de contenu géré par AEM. | Investissement client modéré. Le client doit gérer son propre réseau de diffusion de contenu. |
| **Conditions préalables** | Aucune | Réseau de diffusion de contenu existant onéreux à remplacer. Doit démontrer un test de charge réussi avant sa mise en opération. |
| **Expertise dans le réseau de diffusion de contenu** | Aucune | Nécessite au moins un ingénieur à temps partiel ayant des connaissances approfondies du réseau de diffusion de contenu et capable de configurer le réseau de diffusion de contenu du client. |
| **Sécurité** | Géré par Adobe. | Géré par Adobe (et éventuellement par le client sur son propre réseau de diffusion de contenu). |
| **Performances** | Optimisé par Adobe. | Bénéficiera de certaines fonctionnalités du réseau de diffusion de contenu AEM, mais potentiellement un faible gain en performances en raison du saut supplémentaire. **Remarque** : Sauts du réseau de diffusion de contenu client à un réseau de diffusion de contenu Fastly probablement efficaces. |
| **Mise en cache** | Prend en charge les en-têtes de cache appliqués au Dispatcher. | Prend en charge les en-têtes de cache appliqués au Dispatcher. |
| **Fonctionnalités de compression d’images et de vidéos** | Peut fonctionner avec Adobe Dynamic Media. | Peut fonctionner avec Adobe Dynamic Media ou avec la solution d’image/vidéo du réseau de diffusion de contenu géré par le client. |

### Réseau de diffusion de contenu géré par AEM {#aem-managed-cdn}

La préparation de la diffusion de contenu à l’aide du réseau de diffusion de contenu prêt à l’emploi d’Adobe est simple, comme décrit ci-dessous :

1. Vous fournirez le certificat SSL signé et la clé secrète à Adobe en partageant un lien vers un formulaire sécurisé contenant ces informations. Veuillez coordonner cette tâche avec le service clientèle.
   **Remarque :** AEM as a Cloud Service ne prend pas en charge les certificats DV (Domain Validated, domaines validés).
1. Vous devez indiquer au service clientèle les informations suivantes :
   * Quel domaine personnalisé doit être associé à un environnement donné, tel que défini par l’ID de programme et l’ID d’environnement.
   * Si une liste blanche d’adresses IP est nécessaire pour limiter le trafic à destination d’un environnement donné.
1. Le service clientèle coordonnera alors avec vous le timing d’un enregistrement DNS CNAME, en pointant son nom de domaine complet vers `adobe-aem.map.fastly.net`.
1. Vous serez averti lorsque les certificats SSL arriveront à expiration afin que vous puissiez soumettre à nouveau les nouveaux certificats SSL.

**Limitation du trafic**

Par défaut, dans le cas d’une configuration de réseau de diffusion de contenu géré par Adobe, tout le trafic public peut se diriger vers le service de publication, tant pour les environnements de production que de non-production (de développement et d’évaluation). Si vous souhaitez limiter le trafic à destination du service de publication pour un environnement donné (par exemple, limiter l’évaluation par une plage d’adresses IP), vous devez demander au service clientèle de configurer ces restrictions.

### Le réseau de diffusion de contenu du client pointe vers le réseau de diffusion de contenu géré par AEM {#point-to-point-CDN}

Pris en charge si vous souhaitez utiliser votre réseau de diffusion de contenu existant, mais ne pouvez pas satisfaire aux exigences d’un réseau de diffusion de contenu géré par le client. Dans ce cas, vous gérez votre propre réseau de diffusion de contenu, mais pointez sur le réseau de diffusion de contenu géré par Adobe.

Notez que :

1. Vous devez disposer d’un réseau de diffusion de contenu existant.
1. Vous devez le gérer.
1. Vous devez être en mesure de configurer le réseau de diffusion de contenu pour utiliser AEM as a Cloud Service. Reportez-vous aux instructions de configuration ci-dessous.
1. Vous devez disposer d’ingénieurs maîtrisant les réseaux de diffusion de contenu et disponibles pour résoudre les problèmes associés éventuels.
1. Vous devez effectuer et réussir un test de charge avant de passer en production.

Instructions de configuration :

1. Définissez l’en-tête `X-Forwarded-Host` avec le nom de domaine.
1. Définissez l’en-tête de l’hôte avec le domaine d’origine, qui est l’entrée du réseau de diffusion de contenu d’Adobe. La valeur doit provenir d’Adobe.
1. Envoyez l’en-tête SNI à l’origine. Tout comme l’en-tête d’hôte, l’en-tête SNI doit être le domaine d’origine.
1. Définissez la valeur `X-Edge-Key`, qui est nécessaire pour acheminer correctement le trafic vers les serveurs AEM. La valeur doit provenir d’Adobe.

Avant d’accepter le trafic en direct, vous devez vérifier auprès du service clientèle d’Adobe que le trafic de bout en bout fonctionne correctement.

## Mise en cache {#caching}

La mise en cache sur le réseau de diffusion de contenu peut être configurée à l’aide des règles du Dispatcher. Notez que le Dispatcher respecte également les en-têtes d’expiration de cache qui en résultent si `enableTTL` est activé dans sa configuration, ce qui implique qu’il actualisera un contenu spécifique même en dehors du contenu en cours de republication.

### HTML/texte {#html-text}

* Par défaut, mis en cache par le navigateur pendant cinq minutes, en fonction de l’en-tête de contrôle du cache émis par la couche apache. Le réseau de diffusion de contenu respecte également cette valeur.
* Peut être remplacé pour tout le contenu HTML/texte en définissant la variable `EXPIRATION_TIME` dans `global.vars` avec les outils du Dispatcher SDK AEM as a Cloud Service.
* Peut être remplacé à un niveau plus détaillé par les directives mod_headers apache suivantes :

```
<LocationMatch "\.(html)$">
        Header set Cache-Control "max-age=200"
</LocationMatch>
```

Vous devez vous assurer qu’un fichier sous `src/conf.dispatcher.d/cache` comporte la règle suivante (qui se trouve dans la configuration par défaut) :

```
/0000
{ /glob "*" /type "allow" }
```

* Notez que d’autres méthodes, y compris le [projet ACS Commons AEM dispatcher-ttl](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/), ne remplaceront pas les valeurs.

### Bibliothèques côté client (js, css) {#client-side-libraries}

* En utilisant la structure de bibliothèque côté client d’AEM, le code JavaScript et CSS est généré de manière à ce que les navigateurs puissent le mettre en cache indéfiniment, puisque toute modification se manifeste sous la forme de nouveaux fichiers avec un chemin d’accès unique. En d’autres termes, du code HTML faisant référence aux bibliothèques clientes sera produit au besoin afin que vous puissiez découvrir un nouveau contenu au fur et à mesure de sa publication. Le contrôle du cache cache-control est défini sur non modifiable (immutable) ou 30 jours (30 days) pour les navigateurs plus anciens qui ne respectent pas la valeur non modifiable.
* Voir la section [Bibliothèques côté client et cohérence des versions](#content-consistency) pour en savoir plus.

### Images et tout contenu suffisamment volumineux pour être stocké dans le stockage blob {#images}

* Par défaut, non mis en cache
* Peuvent être définis à un niveau de détail supérieur par les directives `mod_headers` apache suivantes :

```
<LocationMatch "^.*.jpeg$">
    Header set Cache-Control "max-age=222"
</LocationMatch>
```

Vous devez vous assurer qu’un fichier sous src/conf.dispatcher.d/cache comporte la règle suivante (qui se trouve dans la configuration par défaut) :

```
/0000
{ /glob "*" /type "allow" }
```

Assurez-vous que les ressources destinées à être conservées en privé plutôt que mises en cache ne font pas partie des filtres de directive LocationMatch.

* Notez que d’autres méthodes, y compris le [projet ACS Commons AEM dispatcher-ttl](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/), ne remplaceront pas les valeurs.

### Autres types de fichiers de contenu dans le magasin de nœuds {#other-content}

* Aucune mise en cache par défaut.
* La valeur par défaut ne peut pas être définie avec la variable `EXPIRATION_TIME` utilisée pour les types de fichiers html/texte.
* L’expiration du cache peut être définie avec la même stratégie LocationMatch décrite dans la section html/texte en spécifiant l’expression régulière appropriée.

## Dispatcher {#disp}

Le trafic passe par un serveur web apache, qui prend en charge les modules, y compris le Dispatcher. Le Dispatcher est principalement utilisé comme cache pour limiter le traitement sur les nœuds de publication afin d’améliorer les performances.

Comme décrit dans la section de mise en cache du réseau de diffusion de contenu, des règles peuvent être appliquées à la configuration du Dispatcher pour modifier les paramètres d’expiration de cache par défaut.

Le reste de cette section décrit les considérations liées à l’invalidation du cache du Dispatcher. Pour la plupart des clients, il ne doit pas être nécessaire d’invalider le cache du Dispatcher, mais plutôt de laisser le Dispatcher actualiser son cache lors de la republication du contenu, et le réseau de diffusion de contenu respecter les en-têtes d’expiration du cache.

### Invalidation du cache du Dispatcher pendant l’activation/la désactivation {#cache-activation-deactivation}

Comme les versions précédentes d’AEM, la publication ou l’annulation de publication des pages effacera le contenu du cache du Dispatcher. Si un problème de mise en cache est suspecté, les clients doivent republier les pages en question.

Lorsque l’instance de publication reçoit une nouvelle version d’une page ou d’une ressource de l’auteur, elle utilise l’agent de vidage pour invalider les chemins d’accès appropriés sur son Dispatcher. Le chemin d’accès mis à jour est supprimé du cache du Dispatcher, ainsi que de ses parents, jusqu’à un niveau (que vous pouvez configurer à l’aide de [statfileslevel](https://docs.adobe.com/content/help/fr-FR/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#invalidating-files-by-folder-level)).

### Invalidation explicite du cache du Dispatcher {#explicit-invalidation}

En général, il n’est pas nécessaire d’invalider manuellement le contenu du Dispatcher, mais cela est possible si nécessaire, comme décrit ci-dessous.

Avant AEM as a Cloud Service, il existait deux manières d’invalider le cache du Dispatcher.

1. Appeler l’agent de réplication, en spécifiant l’agent de vidage de publication du Dispatcher
2. Appeler directement l’API `invalidate.cache` (par exemple, `POST /dispatcher/invalidate.cache`)

L’approche d’API `invalidate.cache` du Dispatcher ne sera plus prise en charge puisqu’elle ne concerne qu’un nœud Dispatcher spécifique. AEM as a Cloud Service fonctionne au niveau du service, et non au niveau du nœud individuel. Les instructions d’invalidation figurant sur la page [Invalidation des pages mises en cache à partir d’AEM](https://docs.adobe.com/content/help/fr-FR/experience-manager-dispatcher/using/configuring/page-invalidate.html) ne sont donc plus valides pour AEM as a Cloud Service.
À la place, l’agent de vidage de réplication doit être utilisé. Cette opération peut être réalisée en utilisant l’API de réplication. La documentation de l’API de réplication est disponible [ici](https://helpx.adobe.com/fr/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/Replicator.html). Pour obtenir un exemple de vidage du cache, consultez la [page d’exemple de l’API](https://helpx.adobe.com/fr/experience-manager/using/aem64_replication_api.html), et plus particulièrement, l’exemple `CustomStep` qui émet une action de réplication de type ACTIVATE pour tous les agents disponibles. Le point d’entrée de l’agent de vidage n’est pas configurable, mais il est préconfiguré pour pointer sur le Dispatcher, conformément au service de publication exécutant l’agent de vidage. L’agent de vidage peut généralement être déclenché par des événements ou des workflows OSGi.

Le diagramme ci-dessous illustre cela.

![Réseau de diffusion de contenu](assets/cdnd.png "Réseau de diffusion de contenu")

Si le cache du Dispatcher n’est pas effacé, contactez le [service clientèle](https://helpx.adobe.com/fr/support.ec.html), qui pourra le vider si nécessaire.

Le réseau de diffusion de contenu géré par Adobe respecte les TTL et il n’est donc pas nécessaire qu’il soit vidé. Si un problème est suspecté, [contactez le service clientèle](https://helpx.adobe.com/fr/support.ec.html), qui pourra vider un cache de réseau de diffusion de contenu géré par Adobe si nécessaire.

## Bibliothèques côté client et cohérence entre les versions {#content-consistency}

Les pages sont composées de code HTML, JavaScript et CSS, ainsi que d’images. Nous vous recommandons d’utiliser les bibliothèques côté client (clientlibs) pour importer des ressources JavaScript et CSS dans des pages HTML, en tenant compte des dépendances entre les bibliothèques JS.

Le framework clientlibs fournit une gestion automatique des versions, ce qui signifie que les développeurs peuvent archiver les modifications apportées aux bibliothèques JS dans le contrôle de code source et que la dernière version sera disponible lorsqu’un client transfère sa version. Sans cela, les développeurs devraient modifier manuellement le code HTML avec des références à la nouvelle version de la bibliothèque, ce qui est particulièrement onéreux si de nombreux modèles HTML partagent la même bibliothèque.

Lorsque les nouvelles versions des bibliothèques sont publiées en production, les pages HTML de référence sont mises à jour avec de nouveaux liens vers ces versions de bibliothèques mises à jour. Une fois que le cache du navigateur a expiré pour une page HTML donnée, il n’est plus possible que les anciennes bibliothèques soient chargées à partir du cache du navigateur, car il est désormais garanti que la page actualisée (à partir d’AEM) référencera les nouvelles versions des bibliothèques. En d’autres termes, une page HTML actualisée comprend toutes les dernières versions des bibliothèques.

Le mécanisme mis en œuvre ici consiste en un hachage sérialisé, qui est annexé au lien de la bibliothèque cliente, garantissant ainsi une URL unique et dont les versions sont contrôlées pour le navigateur afin de mettre en cache le fichier CSS/JS. Le hachage sérialisé n’est mis à jour que lorsque le contenu de la bibliothèque cliente change. En d’autres termes, si des mises à jour non liées se produisent (c’est-à-dire qu’aucune modification n’est apportée au css/js sous-jacent de la bibliothèque cliente) même avec un nouveau déploiement, la référence reste la même, ce qui minimise les perturbations du cache du navigateur.

### Activation des versions Longcache des bibliothèques côté client – démarrage rapide (Quickstart) du SDK AEM as a Cloud Service {#enabling-longcache}

Les inclusions clientlib par défaut sur une page HTML ressemblent à l’exemple suivant :

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.css" type="text/css">
```

Lorsque le contrôle de version clientlib strict est activé, une clé de hachage à long terme est ajoutée en tant que sélecteur à la bibliothèque cliente. Par conséquent, la référence clientlib ressemble à ceci :

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.lc-7c8c5d228445ff48ab49a8e3c865c562-lc.css" type="text/css">
```

Le contrôle de version clientlib strict est activé par défaut dans tous les environnements AEM as a Cloud Service.

Pour activer le contrôle de version clientlib strict dans le démarrage rapide (Quickstart) du SDK local, effectuez les actions suivantes :

1. Accédez au gestionnaire de configuration OSGi `<host>/system/console/configMgr`
1. Recherchez la configuration OSGi du gestionnaire de bibliothèques HTML Adobe Granite :
   * Cochez la case pour activer le contrôle de version strict.
   * Dans le champ Long term client side cache key (Clé de cache côté client à long terme), saisissez la valeur /.*;hash
1. Enregistrez les modifications. Notez qu’il n’est pas nécessaire d’enregistrer cette configuration dans le contrôle de code source, car AEM as a Cloud Service l’activera automatiquement dans les environnements de développement, d’évaluation et de production.
1. Chaque fois que le contenu de la bibliothèque cliente est modifié, une nouvelle clé de hachage est générée et la référence HTML est mise à jour.
