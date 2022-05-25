---
title: Mise en cache dans AEM as a Cloud Service
description: 'Mise en cache dans AEM as a Cloud Service '
feature: Dispatcher
exl-id: 4206abd1-d669-4f7d-8ff4-8980d12be9d6
source-git-commit: 2df0c88d82554362879f6302e8f7c784cb96d2b8
workflow-type: tm+mt
source-wordcount: '2183'
ht-degree: 63%

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
* peut être remplacé à un niveau plus détaillé, y compris le contrôle indépendant du réseau de diffusion de contenu et du cache du navigateur, avec les directives apache mod_headers suivantes :

   ```
   <LocationMatch "^/content/.*\.(html)$">
        Header set Cache-Control "max-age=200"
        Header set Surrogate-Control "max-age=3600"
        Header set Age 0
   </LocationMatch>
   ```

   >[!NOTE]
   >L’en-tête Surrogate-Control s’applique au réseau de diffusion de contenu géré par l’Adobe. Si vous utilisez un [CDN géré par le client](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn.html?lang=en#point-to-point-CDN), un en-tête différent peut être requis en fonction de votre fournisseur de réseau de diffusion de contenu.

   Faites preuve de prudence lorsque vous définissez des en-têtes de contrôle du cache global ou ceux qui correspondent à une expression régulière (regex) large afin qu’ils ne soient pas appliqués au contenu que vous souhaitez peut-être garder confidentiel. Envisagez l’utilisation de plusieurs directives pour vous assurer que les règles sont appliquées de manière extrêmement détaillée. Ceci étant dit, AEM as a Cloud Service va supprimer l’en-tête de cache s’il détecte qu’il a été appliqué à un élément considéré comme impossible à mettre en cache par le Dispatcher, comme décrit dans la documentation du Dispatcher. Pour forcer AEM à toujours appliquer les en-têtes de mise en cache, vous pouvez ajouter l’option **always** comme suit :

   ```
   <LocationMatch "^/content/.*\.(html)$">
        Header unset Cache-Control
        Header unset Expires
        Header always set Cache-Control "max-age=200"
        Header set Age 0
   </LocationMatch>
   ```

   Vous devez vous assurer qu’un fichier sous `src/conf.dispatcher.d/cache` comporte la règle suivante (qui se trouve dans la configuration par défaut) :

   ```
   /0000
   { /glob "*" /type "allow" }
   ```

* Pour empêcher la mise en cache d’un contenu spécifique **dans le CDN**, définissez l’en-tête Cache-Control sur *private*. Par exemple, les éléments suivants empêcheraient la mise en cache du contenu HTML situé dans un répertoire nommé **secure** dans le CDN :

   ```
      <LocationMatch "/content/secure/.*\.(html)$">.  // replace with the right regex
      Header unset Cache-Control
      Header unset Expires
      Header always set Cache-Control “private”
     </LocationMatch>
   ```

   >[!NOTE]
   >D’autres méthodes, y compris le [projet ACS Commons AEM dispatcher-ttl](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/), ne remplaceront pas les valeurs.

   >[!NOTE]
   >Veuillez noter que le Dispatcher peut toujours mettre en cache le contenu en fonction de ses propres [règles de mise en cache](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17497.html). Pour rendre le contenu réellement privé, veillez à ce qu’il ne soit pas mis en cache par le Dispatcher.

### Bibliothèques côté client (js, css) {#client-side-libraries}

* En utilisant la structure de bibliothèque côté client d’AEM, le code JavaScript et CSS est généré de manière à ce que les navigateurs puissent le mettre en cache indéfiniment, puisque toute modification se manifeste sous la forme de nouveaux fichiers avec un chemin d’accès unique.  En d’autres termes, du code HTML faisant référence aux bibliothèques clientes sera produit au besoin afin que vous puissiez découvrir un nouveau contenu au fur et à mesure de sa publication. Le contrôle du cache est défini sur non modifiable (immutable) ou 30 jours (30 days) pour les navigateurs plus anciens qui ne respectent pas la valeur non modifiable.
* Voir la section [Bibliothèques côté client et cohérence des versions](#content-consistency) pour en savoir plus.

### Images et tout contenu suffisamment volumineux pour être stocké dans le stockage d’objets blob {#images}

Le comportement par défaut des programmes créés après la mi-mai 2022 (en particulier, pour les identifiants de programme supérieurs à 65 000) est de mettre en cache par défaut, tout en respectant le contexte d’authentification de la requête. Les programmes plus anciens (id de programme égal ou inférieur à 65 000) ne mettent pas en cache le contenu de l’objet Blob par défaut.

Dans les deux cas, les en-têtes de mise en cache peuvent être remplacés à un niveau de granularité plus fin au niveau de la couche Apache/dispatcher à l’aide de l’Apache. `mod_headers` par exemple :

```
   <LocationMatch "^/content/.*\.(jpeg|jpg)$">
     Header set Cache-Control "max-age=222"
     Header set Age 0
   </LocationMatch>
```

Lors de la modification des en-têtes de mise en cache au niveau de la couche du Dispatcher, veillez à ne pas mettre en cache trop largement. Consultez la discussion dans la section HTML/texte . [above](#html-text)). Assurez-vous également que les ressources destinées à être conservées en privé (plutôt que mises en cache) ne font pas partie de la variable `LocationMatch` filtres de directive.

#### Nouveau comportement de mise en cache par défaut {#new-caching-behavior}

La couche AEM définit les en-têtes de cache selon que l’en-tête de cache a déjà été défini et la valeur du type de requête. Notez que si aucun en-tête de contrôle du cache n’a été défini, le contenu public est mis en cache et le trafic authentifié est défini sur privé. Si un en-tête de contrôle du cache a été défini, les en-têtes du cache ne seront pas touchés.

| L’en-tête de contrôle du cache existe ? | Type de demande | AEM définit les en-têtes de cache sur |
|------------------------------|---------------|------------------------------------------------|
| Non | public | Cache-Control: public, max-age=600, non modifiable |
| Non | authentifié | Cache-Control: privé, max-age=600, non modifiable |
| Oui | quelconque | inchangé |

Bien que cela ne soit pas recommandé, il est possible de modifier le nouveau comportement par défaut pour suivre l’ancien comportement (identifiants de programme égaux ou inférieurs à 65 000) en définissant la variable d’environnement Cloud Manager. `AEM_BLOB_ENABLE_CACHING_HEADERS` sur false.

#### Ancien comportement de mise en cache par défaut {#old-caching-behavior}

Par défaut, le calque AEM ne met pas en cache le contenu blob.

>[!NOTE]
>Il est recommandé de modifier l’ancien comportement par défaut pour qu’il soit cohérent avec le nouveau comportement (identifiants de programme supérieurs à 65 000) en définissant la variable d’environnement Cloud Manager AEM_BLOB_ENABLE_CACHING_HEADERS sur true. Si le programme est déjà actif, vérifiez qu’après les modifications, le contenu se comporte comme prévu.

>[!NOTE]
>Les autres méthodes, dont la méthode [dispatcher-ttl AEM projet ACS Commons](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/), ne remplace pas les valeurs.

### Autres types de fichiers de contenu dans le magasin de nœuds {#other-content}

* Aucune mise en cache par défaut.
* La valeur par défaut ne peut pas être définie avec la variable `EXPIRATION_TIME` utilisée pour les types de fichiers html/texte.
* L’expiration du cache peut être définie avec la même stratégie LocationMatch décrite dans la section html/texte en spécifiant l’expression régulière appropriée.

### Autres optimisations {#further-optimizations}

* Éviter d’utiliser `User-Agent` dans le `Vary` en-tête . Les anciennes versions de la configuration par défaut du Dispatcher (antérieures à l’archétype version 28) l’incluaient et nous vous recommandons de la supprimer en suivant les étapes ci-dessous.
   * Recherchez les fichiers vhost dans `<Project Root>/dispatcher/src/conf.d/available_vhosts/*.vhost`
   * Supprimez ou commentez la ligne : `Header append Vary User-Agent env=!dont-vary` de tous les fichiers vhost, à l’exception de default.vhost, qui est en lecture seule
* Utilisez la variable `Surrogate-Control` en-tête pour contrôler la mise en cache du réseau CDN indépendamment de la mise en cache du navigateur
* Envisager d’appliquer [`stale-while-revalidate`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control#stale-while-revalidate) et [`stale-if-error`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control#stale-if-error) afin de permettre l’actualisation de l’arrière-plan et d’éviter les pertes de cache, en maintenant le contenu à jour et rapide pour les utilisateurs.
   * Il existe de nombreuses façons d&#39;appliquer ces directives, mais en ajoutant 30 minutes `stale-while-revalidate` à tous les en-têtes de contrôle du cache est un bon point de départ.
* Voici quelques exemples pour divers types de contenu, qui peuvent être utilisés comme guide lors de la configuration de vos propres règles de mise en cache. Veuillez soigneusement réfléchir et tester votre configuration et vos exigences spécifiques :

   * Mettez en cache les ressources de bibliothèque cliente modifiables pendant 12h et l’actualisation en arrière-plan après 12h.

      ```
      <LocationMatch "^/etc\.clientlibs/.*\.(?i:json|png|gif|webp|jpe?g|svg)$">
         Header set Cache-Control "max-age=43200,stale-while-revalidate=43200,stale-if-error=43200,public" "expr=%{REQUEST_STATUS} < 400"
         Header set Age 0
      </LocationMatch>
      ```

   * Mettre en cache les ressources de bibliothèque cliente non modifiables à long terme (30 jours) avec actualisation de l’arrière-plan afin d’éviter la fonction MISS.

      ```
      <LocationMatch "^/etc\.clientlibs/.*\.(?i:js|css|ttf|woff2)$">
         Header set Cache-Control "max-age=2592000,stale-while-revalidate=43200,stale-if-error=43200,public,immutable" "expr=%{REQUEST_STATUS} < 400"
         Header set Age 0
      </LocationMatch>
      ```

   * Mise en cache des pages de HTML pendant 5 min avec actualisation en arrière-plan 1 h sur le navigateur et 12 h sur le réseau de diffusion de contenu. Les en-têtes de contrôle du cache seront toujours ajoutés. Il est donc important de s’assurer que les pages HTML correspondantes sous /content/* sont destinées à être publiques. Si ce n’est pas le cas, pensez à utiliser une expression régulière plus spécifique.

      ```
      <LocationMatch "^/content/.*\.html$">
         Header unset Cache-Control
         Header always set Cache-Control "max-age=300,stale-while-revalidate=3600" "expr=%{REQUEST_STATUS} < 400"
         Header always set Surrogate-Control "stale-while-revalidate=43200,stale-if-error=43200" "expr=%{REQUEST_STATUS} < 400"
         Header set Age 0
      </LocationMatch>
      ```

   * Mettez en cache les réponses json de l’exportateur de modèles Sling/services de contenu pendant 5 minutes avec une actualisation en arrière-plan de 1 h sur le navigateur et de 12 h sur le réseau de diffusion de contenu.

      ```
      <LocationMatch "^/content/.*\.model\.json$">
         Header set Cache-Control "max-age=300,stale-while-revalidate=3600" "expr=%{REQUEST_STATUS} < 400"
         Header set Surrogate-Control "stale-while-revalidate=43200,stale-if-error=43200" "expr=%{REQUEST_STATUS} < 400"
         Header set Age 0
      </LocationMatch>
      ```

   * Mettez en cache les URL non modifiables du composant d’image principal à long terme (30 jours) avec actualisation de l’arrière-plan afin d’éviter la mise à niveau.

      ```
      <LocationMatch "^/content/.*\.coreimg.*\.(?i:jpe?g|png|gif|svg)$">
         Header set Cache-Control "max-age=2592000,stale-while-revalidate=43200,stale-if-error=43200,public,immutable" "expr=%{REQUEST_STATUS} < 400"
         Header set Age 0
      </LocationMatch>
      ```

   * Mise en cache de ressources modifiables de la gestion des actifs numériques (DAM), telles que des images et des vidéos, pendant 24 h, et actualisation de l’arrière-plan après 12 h, afin d’éviter la fonction MISS

      ```
      <LocationMatch "^/content/dam/.*\.(?i:jpe?g|gif|js|mov|mp4|png|svg|txt|zip|ico|webp|pdf)$">
         Header set Cache-Control "max-age=43200,stale-while-revalidate=43200,stale-if-error=43200" "expr=%{REQUEST_STATUS} < 400"
         Header set Age 0
      </LocationMatch>
      ```

### Comportement de la requête d’HEAD {#request-behavior}

Lorsqu’une demande d’HEAD est reçue sur le réseau de diffusion de contenu Adobe pour une ressource qui est **not** mise en cache, la requête est transformée et reçue par le Dispatcher et/ou l’instance d’AEM en tant que requête de GET. Si la réponse peut être mise en cache, les requêtes HEAD suivantes seront diffusées à partir du réseau de diffusion de contenu. Si la réponse ne peut pas être mise en cache, les requêtes HEAD suivantes seront transmises au Dispatcher et/ou à l’instance d’AEM pendant une période qui dépend de la variable `Cache-Control` TTL.

## Invalidation du cache du Dispatcher {#disp}

En général, il n’est pas nécessaire d’invalider le cache du Dispatcher. Vous devriez au contraire vous fier au Dispatcher qui actualise son cache lorsque le contenu est republié et au réseau de diffusion de contenu qui respecte les en-têtes d’expiration du cache.

### Invalidation du cache du Dispatcher pendant l’activation/la désactivation {#cache-activation-deactivation}

Comme les versions précédentes d’AEM, la publication ou l’annulation de publication des pages effacera le contenu du cache du Dispatcher. Si un problème de mise en cache est suspecté, les clients doivent republier les pages en question et s’assurer qu’un hôte virtuel correspond à ServerAlias localhost, obligatoire pour l’invalidation du cache du Dispatcher.


Lorsque l’instance de publication reçoit une nouvelle version d’une page ou d’une ressource de l’auteur, elle utilise l’agent de vidage pour invalider les chemins d’accès appropriés sur son Dispatcher. Le chemin d’accès mis à jour est supprimé du cache du Dispatcher, ainsi que de ses parents, jusqu’à un niveau (que vous pouvez configurer à l’aide de [statfileslevel](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=fr#invalidating-files-by-folder-level)).

### Invalidation explicite du cache du Dispatcher {#explicit-invalidation}

En général, il n’est pas nécessaire d’invalider manuellement le contenu du Dispatcher, mais cela est possible si nécessaire.

>[!NOTE]
>Avant AEM as a Cloud Service, il existait deux manières d’invalider le cache du Dispatcher.
>
>1. Appeler l’agent de réplication, en spécifiant l’agent de vidage de publication du Dispatcher
>2. Appeler directement l’API `invalidate.cache` (par exemple, `POST /dispatcher/invalidate.cache`)

>
>L’approche d’API `invalidate.cache` du Dispatcher ne sera plus prise en charge puisqu’elle ne concerne qu’un nœud Dispatcher spécifique. AEM as a Cloud Service fonctionne au niveau du service, et non au niveau du nœud individuel. Les instructions d’invalidation figurant sur la page [Invalidation des pages mises en cache à partir d’AEM](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html?lang=fr) ne sont donc plus valides pour AEM as a Cloud Service.

L’agent de vidage de réplication doit être utilisé. Cette opération peut être réalisée en utilisant l’[API de réplication](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/replication/Replicator.html). Le point d’entrée de l’agent de vidage n’est pas configurable, mais il est préconfiguré pour pointer sur le Dispatcher, conformément au service de publication exécutant l’agent de vidage. L’agent de vidage peut généralement être déclenché par des événements ou des workflows OSGi.

<!-- Need to find a new link and/or example -->
<!-- 
and for an example of flushing the cache, see the [API example page](https://helpx.adobe.com/experience-manager/using/aem64_replication_api.html) (specifically the `CustomStep` example issuing a replication action of type ACTIVATE to all available agents). 
-->

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
