---
title: Mise en cache dans AEM as a Cloud Service
description: 'Mise en cache dans AEM as a Cloud Service '
feature: Dispatcher
translation-type: tm+mt
source-git-commit: 69c865dbc87ca021443e53b61440faca8fa3c4d4
workflow-type: tm+mt
source-wordcount: '1534'
ht-degree: 99%

---


# Présentation {#intro}

Le trafic emprunte un réseau de diffusion de contenu pour parvenir à une couche de serveur web Apache, destinée à prendre en charge les modules, y compris le Dispatcher. Pour améliorer les performances, le Dispatcher sert essentiellement de cache pour limiter les traitements des nœuds de publication.
Il est possible d’appliquer des règles à la configuration du Dispatcher pour modifier les paramètres d’expiration du cache par défaut, ce qui entraîne la mise en cache sur le réseau de diffusion de contenu. Notez que le Dispatcher respecte également les en-têtes d’expiration de cache qui en résultent si `enableTTL` est activé dans sa configuration, ce qui implique qu’il actualisera un contenu spécifique même en dehors du contenu en cours de republication.

Cette page décrit également comment le cache du Dispatcher est invalidé, ainsi que le fonctionnement de la mise en cache du navigateur concernant les bibliothèques côté client.

## Mise en cache {#caching}

### HTML/texte {#html-text}

* par défaut, mis en cache par le navigateur pendant cinq minutes, en fonction de l’en-tête `cache-control` émis par la couche Apache. Le réseau de diffusion de contenu respecte également cette valeur.
* le paramètre de mise en cache HTML/Texte par défaut peut être désactivé en définissant la variable `DISABLE_DEFAULT_CACHING` dans `global.vars` :

```
Define DISABLE_DEFAULT_CACHING
```

Cela peut s’avérer utile, par exemple, lorsque votre logique commerciale nécessite un réglage précis de l’en-tête d’âge (avec une valeur basée sur le jour du calendrier) puisque, par défaut, l’en-tête d’âge est défini sur 0. Cela étant, **faites preuve de prudence lorsque vous désactivez la mise en cache par défaut.**

* Peut être remplacé pour tout le contenu HTML/texte en définissant la variable `EXPIRATION_TIME` dans `global.vars` avec les outils du Dispatcher SDK AEM as a Cloud Service.
* Peut être remplacé à un niveau plus détaillé par les directives mod_headers apache suivantes :

   ```
   <LocationMatch "^/content/.*\.(html)$">
        Header set Cache-Control "max-age=200"
        Header set Age 0
   </LocationMatch>
   ```

   Faites preuve de prudence lorsque vous définissez des en-têtes de contrôle du cache global ou ceux qui correspondent à une expression régulière (regex) large afin qu’ils ne soient pas appliqués au contenu que vous souhaitez peut-être garder confidentiel. Envisagez l’utilisation de plusieurs directives pour vous assurer que les règles sont appliquées de manière extrêmement détaillée. Ceci étant dit, AEM as a Cloud Service va supprimer l’en-tête de cache s’il détecte qu’il a été appliqué à un élément considéré comme impossible à mettre en cache par le Dispatcher, comme décrit dans la documentation du Dispatcher. Pour forcer AEM à toujours appliquer la mise en cache, vous pouvez ajouter l’option « always » comme suit :

   ```
   <LocationMatch "^/content/.*\.(html)$">
        Header always set Cache-Control "max-age=200"
        Header set Age 0
   </LocationMatch>
   ```

   Vous devez vous assurer qu’un fichier sous `src/conf.dispatcher.d/cache` comporte la règle suivante (qui se trouve dans la configuration par défaut) :

   ```
   /0000
   { /glob "*" /type "allow" }
   ```

* Pour empêcher la mise en cache d’un contenu spécifique, définissez l’en-tête Cache-Control sur *private*. Par exemple, les éléments suivants empêcheraient la mise en cache du contenu html situé sous un répertoire nommé **myfolder** :

   ```
      <LocationMatch "/content/myfolder/.*\.(html)$">.  // replace with the right regex
      Header set Cache-Control “private”
     </LocationMatch>
   ```

   >[!NOTE]
   >D’autres méthodes, y compris le [projet ACS Commons AEM dispatcher-ttl](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/), ne remplaceront pas les valeurs.

### Bibliothèques côté client (js, css) {#client-side-libraries}

* En utilisant la structure de bibliothèque côté client d’AEM, le code JavaScript et CSS est généré de manière à ce que les navigateurs puissent le mettre en cache indéfiniment, puisque toute modification se manifeste sous la forme de nouveaux fichiers avec un chemin d’accès unique. En d’autres termes, du code HTML faisant référence aux bibliothèques clientes sera produit au besoin afin que vous puissiez découvrir un nouveau contenu au fur et à mesure de sa publication. Le contrôle du cache cache-control est défini sur non modifiable (immutable) ou 30 jours (30 days) pour les navigateurs plus anciens qui ne respectent pas la valeur non modifiable.
* Voir la section [Bibliothèques côté client et cohérence des versions](#content-consistency) pour en savoir plus.

### Images et tout contenu suffisamment volumineux pour être stocké dans le stockage blob {#images}

* Par défaut, non mis en cache
* Peuvent être définis à un niveau de détail supérieur par les directives `mod_headers` apache suivantes :

   ```
      <LocationMatch "^/content/.*\.(jpeg|jpg)$">
        Header set Cache-Control "max-age=222"
        Header set Age 0
      </LocationMatch>
   ```

   Consultez la discussion dans la section html/text ci-dessus pour veiller à ne pas appliquer excessivement la mise en cache et pour savoir comment forcer AEM à toujours appliquer la mise en cache avec l’option « always ».

   Vous devez vous assurer qu’un fichier sous `src/conf.dispatcher.d/`cache comporte la règle suivante (qui se trouve dans la configuration par défaut) :

   ```
   /0000
   { /glob "*" /type "allow" }
   ```

   Assurez-vous que les ressources destinées à être conservées en privé plutôt que mises en cache ne font pas partie des filtres de directive LocationMatch.

   >[!NOTE]
   >D’autres méthodes, y compris le [projet ACS Commons AEM dispatcher-ttl](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/), ne remplaceront pas les valeurs.

### Autres types de fichiers de contenu dans le magasin de nœuds {#other-content}

* Aucune mise en cache par défaut.
* La valeur par défaut ne peut pas être définie avec la variable `EXPIRATION_TIME` utilisée pour les types de fichiers html/texte.
* L’expiration du cache peut être définie avec la même stratégie LocationMatch décrite dans la section html/texte en spécifiant l’expression régulière appropriée.

## Invalidation du cache du Dispatcher {#disp}

En général, il n’est pas nécessaire d’invalider le cache du Dispatcher. Vous devriez au contraire vous fier au Dispatcher qui actualise son cache lorsque le contenu est republié et au réseau de diffusion de contenu qui respecte les en-têtes d’expiration du cache.

### Invalidation du cache du Dispatcher pendant l’activation/la désactivation {#cache-activation-deactivation}

Comme les versions précédentes d’AEM, la publication ou l’annulation de publication des pages effacera le contenu du cache du Dispatcher. Si un problème de mise en cache est suspecté, les clients doivent republier les pages en question.

Lorsque l’instance de publication reçoit une nouvelle version d’une page ou d’une ressource de l’auteur, elle utilise l’agent de vidage pour invalider les chemins d’accès appropriés sur son Dispatcher. Le chemin d’accès mis à jour est supprimé du cache du Dispatcher, ainsi que de ses parents, jusqu’à un niveau (que vous pouvez configurer à l’aide de [statfileslevel](https://docs.adobe.com/content/help/fr-FR/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#invalidating-files-by-folder-level)).

### Invalidation explicite du cache du Dispatcher {#explicit-invalidation}

En général, il n’est pas nécessaire d’invalider manuellement le contenu du Dispatcher, mais cela est possible si nécessaire, comme décrit ci-dessous.

Avant AEM as a Cloud Service, il existait deux manières d’invalider le cache du Dispatcher.

1. Appeler l’agent de réplication, en spécifiant l’agent de vidage de publication du Dispatcher
2. Appeler directement l’API `invalidate.cache` (par exemple, `POST /dispatcher/invalidate.cache`)

L’approche d’API `invalidate.cache` du Dispatcher ne sera plus prise en charge puisqu’elle ne concerne qu’un nœud Dispatcher spécifique. AEM as a Cloud Service fonctionne au niveau du service, et non au niveau du nœud individuel. Les instructions d’invalidation figurant sur la page [Invalidation des pages mises en cache à partir d’AEM](https://docs.adobe.com/content/help/fr-FR/experience-manager-dispatcher/using/configuring/page-invalidate.html) ne sont donc plus valides pour AEM as a Cloud Service.
À la place, l’agent de vidage de réplication doit être utilisé. Cette opération peut être réalisée en utilisant l’API de réplication. La documentation de l’API de réplication est disponible [ici](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/replication/Replicator.html). Pour obtenir un exemple de vidage du cache, consultez la [page d’exemple de l’API](https://helpx.adobe.com/fr/experience-manager/using/aem64_replication_api.html), et plus particulièrement, l’exemple `CustomStep` qui émet une action de réplication de type ACTIVATE pour tous les agents disponibles. Le point d’entrée de l’agent de vidage n’est pas configurable, mais il est préconfiguré pour pointer sur le Dispatcher, conformément au service de publication exécutant l’agent de vidage. L’agent de vidage peut généralement être déclenché par des événements ou des workflows OSGi.

Le schéma ci-dessous illustre cela.

![Réseau de diffusion de contenu](assets/cdnd.png "Réseau de diffusion de contenu")

Si le cache du Dispatcher n’est pas effacé, contactez le [service clientèle](https://helpx.adobe.com/fr/support.ec.html), qui pourra le vider si nécessaire.

Le réseau de diffusion de contenu géré par Adobe respecte les TTL et il n’est donc pas nécessaire qu’il soit vidé. Si un problème est suspecté, [contactez le service clientèle](https://helpx.adobe.com/support.ec.html), qui pourra vider un cache de réseau de diffusion de contenu géré par Adobe si nécessaire.

## Bibliothèques côté client et cohérence entre les versions {#content-consistency}

Les pages sont composées de code HTML, JavaScript et CSS, ainsi que d’images. Nous vous recommandons d’utiliser le [framework de bibliothèques côté client (clientlibs)](/help/implementing/developing/introduction/clientlibs.md) pour importer des ressources JavaScript et CSS dans des pages HTML, en tenant compte des dépendances entre les bibliothèques JS.

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
