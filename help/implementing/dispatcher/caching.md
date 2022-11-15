---
title: Mise en cache dans AEM as a Cloud Service
description: Mise en cache dans AEM as a Cloud Service
feature: Dispatcher
exl-id: 4206abd1-d669-4f7d-8ff4-8980d12be9d6
source-git-commit: 18f8a0737dbcce643a5949fb5f942e73f066fa59
workflow-type: tm+mt
source-wordcount: '2666'
ht-degree: 69%

---

# Présentation {#intro}

Le trafic transite par le réseau de diffusion de contenu vers une couche de serveur web Apache, qui prend en charge les modules, y compris Dispatcher. Afin d’améliorer les performances, Dispatcher est principalement utilisé comme cache pour limiter le traitement sur les noeuds de publication.
Des règles peuvent être appliquées à la configuration de Dispatcher pour modifier les paramètres d’expiration de cache par défaut, ce qui entraîne la mise en cache sur le réseau de diffusion de contenu. Notez que Dispatcher respecte également les en-têtes d’expiration de cache qui en résultent si `enableTTL` est activé dans la configuration de Dispatcher, ce qui implique qu’il actualisera du contenu spécifique même en dehors du contenu en cours de republication.

Cette page décrit également comment le cache de Dispatcher est invalidé et comment la mise en cache fonctionne au niveau du navigateur en ce qui concerne les bibliothèques côté client.

## Mise en cache {#caching}

### HTML/texte {#html-text}

* par défaut, mis en cache par le navigateur pendant cinq minutes, en fonction de la variable `cache-control` en-tête émis par le calque Apache. Le réseau de diffusion de contenu respecte également cette valeur.
* le paramètre de mise en cache HTML/Texte par défaut peut être désactivé en définissant la variable `DISABLE_DEFAULT_CACHING` dans `global.vars` :

```
Define DISABLE_DEFAULT_CACHING
```

Cela peut s’avérer utile, par exemple, lorsque votre logique commerciale nécessite un réglage précis de l’en-tête d’âge (avec une valeur basée sur le jour du calendrier) puisque, par défaut, l’en-tête d’âge est défini sur 0. Cela étant, **faites preuve de prudence lorsque vous désactivez la mise en cache par défaut.**

* Peut être remplacé pour tout le contenu HTML/texte en définissant la variable `EXPIRATION_TIME` dans `global.vars` avec les outils du Dispatcher SDK AEM as a Cloud Service.
* peut être remplacé à un niveau plus détaillé, y compris le contrôle indépendant du réseau de diffusion de contenu et du cache du navigateur, avec l’Apache suivante `mod_headers` directives :

   ```
   <LocationMatch "^/content/.*\.(html)$">
        Header set Cache-Control "max-age=200"
        Header set Surrogate-Control "max-age=3600"
        Header set Age 0
   </LocationMatch>
   ```

   >[!NOTE]
   >L’en-tête Surrogate-Control s’applique au réseau de diffusion de contenu géré par Adobe. Si vous utilisez un [réseau de diffusion de contenu géré par le client](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn.html?lang=fr#point-to-point-CDN), un en-tête différent peut être requis en fonction de votre fournisseur de réseau de diffusion de contenu.

   Soyez prudent lorsque vous définissez des en-têtes de contrôle du cache global ou ceux qui correspondent à une expression régulière large afin qu’ils ne soient pas appliqués au contenu que vous devez garder privé. Envisagez l’utilisation de plusieurs directives pour vous assurer que les règles sont appliquées de manière extrêmement détaillée. Cela dit, AEM as a Cloud Service supprime l’en-tête du cache s’il détecte qu’il a été appliqué à ce qu’il détecte comme pouvant être mis en cache par Dispatcher, comme décrit dans la documentation de Dispatcher. Pour forcer AEM à toujours appliquer les en-têtes de mise en cache, vous pouvez ajouter l’option **always** comme suit :

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
   >Veuillez noter que Dispatcher peut toujours mettre en cache le contenu en fonction des siens. [règles de mise en cache](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17497.html?lang=fr). Pour rendre le contenu réellement privé, vous devez vous assurer qu’il n’est pas mis en cache par Dispatcher.

### Bibliothèques côté client (js, css) {#client-side-libraries}

* En utilisant la structure de bibliothèque côté client d’AEM, le code JavaScript et CSS est généré de manière à ce que les navigateurs puissent le mettre en cache indéfiniment, puisque toute modification se manifeste sous la forme de nouveaux fichiers avec un chemin d’accès unique.  En d’autres termes, du code HTML faisant référence aux bibliothèques clientes sera produit au besoin afin que vous puissiez découvrir un nouveau contenu au fur et à mesure de sa publication. Le contrôle du cache est défini sur non modifiable (immutable) ou 30 jours (30 days) pour les navigateurs plus anciens qui ne respectent pas la valeur non modifiable.
* Voir la section [Bibliothèques côté client et cohérence des versions](#content-consistency) pour en savoir plus.

### Images et tout contenu suffisamment volumineux pour être stocké dans le stockage blob {#images}

Le comportement par défaut des programmes créés après la mi-mai 2022 (en particulier, pour les identifiants de programme supérieurs à 65 000) est de mettre en cache par défaut, tout en respectant le contexte d’authentification de la requête. Les programmes plus anciens (id de programme égal ou inférieur à 65 000) ne mettent pas en cache le contenu de l’objet Blob par défaut.

Dans les deux cas, les en-têtes de mise en cache peuvent être remplacés à un niveau de détail plus fin au niveau de la couche Apache/Dispatcher en utilisant l’Apache `mod_headers` par exemple :

```
   <LocationMatch "^/content/.*\.(jpeg|jpg)$">
     Header set Cache-Control "max-age=222"
     Header set Age 0
   </LocationMatch>
```

Lors de la modification des en-têtes de mise en cache au niveau de la couche de Dispatcher, veillez à ne pas mettre en cache trop largement. Consultez la discussion dans la section HTML/texte . [above](#html-text). Assurez-vous également que les ressources destinées à être conservées en privé (plutôt que mises en cache) ne font pas partie des filtres de directive `LocationMatch`.

#### Nouveau comportement de mise en cache par défaut {#new-caching-behavior}

La couche AEM définit les en-têtes de cache selon que l’en-tête de cache a déjà été défini et la valeur du type de requête. Notez que si aucun en-tête de contrôle du cache n’a été défini, le contenu public est mis en cache et le trafic authentifié est défini sur privé. Si un en-tête de contrôle du cache a été défini, les en-têtes du cache restent intacts.

| L’en-tête de contrôle du cache existe ? | Type de demande | AEM définit les en-têtes de cache sur |
|------------------------------|---------------|------------------------------------------------|
| Non | public | Cache-Control: public, max-age=600, immutable |
| Non | authentifié | Cache-Control: private, max-age=600, immutable |
| Oui | quelconque | inchangé |

Bien que cela ne soit pas recommandé, il est possible de modifier le nouveau comportement par défaut pour suivre l’ancien comportement (identifiants de programme égaux ou inférieurs à 65 000) en définissant la variable d’environnement Cloud Manager. `AEM_BLOB_ENABLE_CACHING_HEADERS` sur false.

#### Ancien comportement de mise en cache par défaut {#old-caching-behavior}

Par défaut, le calque AEM ne met pas en cache le contenu blob.

>[!NOTE]
>Il est recommandé de modifier l’ancien comportement par défaut pour qu’il soit cohérent avec le nouveau comportement (identifiants de programme supérieurs à 65 000) en définissant la variable d’environnement Cloud Manager AEM_BLOB_ENABLE_CACHING_HEADERS sur true. Si le programme est déjà actif, vérifiez que le contenu se comporte comme prévu une fois les modifications appliquées.

>[!NOTE]
>Les autres méthodes, y compris celle du [projet ACS Commons AEM dispatcher-ttl](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/), ne permettront pas de remplacer les valeurs.

### Autres types de fichiers de contenu dans le magasin de nœuds {#other-content}

* Aucune mise en cache par défaut.
* La valeur par défaut ne peut pas être définie avec la variable `EXPIRATION_TIME` utilisée pour les types de fichiers html/texte.
* L’expiration du cache peut être définie avec la même stratégie LocationMatch décrite dans la section html/texte en spécifiant l’expression régulière appropriée.

### Autres optimisations {#further-optimizations}

* Évitez d’utiliser `User-Agent` dans l’en-tête `Vary`. Les anciennes versions de la configuration par défaut de Dispatcher (antérieures à l’archétype version 28) l’incluaient et nous vous recommandons de la supprimer en suivant les étapes ci-dessous.
   * Recherchez les fichiers vhost dans `<Project Root>/dispatcher/src/conf.d/available_vhosts/*.vhost`.
   * Supprimez ou mettez en commentaire la ligne : `Header append Vary User-Agent env=!dont-vary` de tous les fichiers vhost, à l’exception de default.vhost, qui est en lecture seule.
* Utilisez l’en-tête `Surrogate-Control` pour contrôler la mise en cache du réseau CDN indépendamment de la mise en cache du navigateur.
* Envisagez d’appliquer les directives [`stale-while-revalidate`](https://developer.mozilla.org/fr-FR/docs/Web/HTTP/Headers/Cache-Control#stale-while-revalidate) et [`stale-if-error`](https://developer.mozilla.org/fr-FR/docs/Web/HTTP/Headers/Cache-Control#stale-if-error) afin de permettre l’actualisation de l’arrière-plan et d’éviter les pertes de cache, en maintenant le contenu à jour et rapide pour les utilisateurs.
   * Il existe de nombreuses façons d’appliquer ces directives, mais en ajoutant un `stale-while-revalidate` de 30 minutes à tous les en-têtes de contrôle du cache est un bon point de départ.
* Voici quelques exemples de divers types de contenu qui peuvent être utilisés comme vous guider lors de la configuration de vos propres règles de mise en cache. Réfléchissez à la spécificité de votre configuration et de vos exigences et testez-les soigneusement :

   * Mettez en cache les ressources de bibliothèque cliente modifiables pendant 12 h et l’actualisation en arrière-plan après 12 h.

      ```
      <LocationMatch "^/etc\.clientlibs/.*\.(?i:json|png|gif|webp|jpe?g|svg)$">
         Header set Cache-Control "max-age=43200,stale-while-revalidate=43200,stale-if-error=43200,public" "expr=%{REQUEST_STATUS} < 400"
         Header set Age 0
      </LocationMatch>
      ```

   * Mettez en cache les ressources de bibliothèque cliente non modifiables à long terme (30 jours) avec actualisation de l’arrière-plan afin d’éviter la fonction MISS.

      ```
      <LocationMatch "^/etc\.clientlibs/.*\.(?i:js|css|ttf|woff2)$">
         Header set Cache-Control "max-age=2592000,stale-while-revalidate=43200,stale-if-error=43200,public,immutable" "expr=%{REQUEST_STATUS} < 400"
         Header set Age 0
      </LocationMatch>
      ```

   * Mettez en cache des pages HTML pendant 5 min avec une actualisation en arrière-plan de 1 h sur le navigateur et de 12 h sur le réseau de diffusion de contenu. Les en-têtes de contrôle du cache seront toujours ajoutés. Il est donc important de s’assurer que les pages HTML correspondantes sous /content/* sont destinées à être publiques. Si ce n’est pas le cas, pensez à utiliser une expression régulière plus spécifique.

      ```
      <LocationMatch "^/content/.*\.html$">
         Header unset Cache-Control
         Header always set Cache-Control "max-age=300,stale-while-revalidate=3600" "expr=%{REQUEST_STATUS} < 400"
         Header always set Surrogate-Control "stale-while-revalidate=43200,stale-if-error=43200" "expr=%{REQUEST_STATUS} < 400"
         Header set Age 0
      </LocationMatch>
      ```

   * Mettez en cache les réponses json de l’exportateur de modèles services/Sling de contenu pendant 5 minutes avec une actualisation en arrière-plan de 1 h sur le navigateur et de 12 h sur le réseau de diffusion de contenu.

      ```
      <LocationMatch "^/content/.*\.model\.json$">
         Header set Cache-Control "max-age=300,stale-while-revalidate=3600" "expr=%{REQUEST_STATUS} < 400"
         Header set Surrogate-Control "stale-while-revalidate=43200,stale-if-error=43200" "expr=%{REQUEST_STATUS} < 400"
         Header set Age 0
      </LocationMatch>
      ```

   * Mettez en cache les URL non modifiables du composant d’image principal à long terme (30 jours) avec actualisation de l’arrière-plan afin d’éviter la fonction MISS.

      ```
      <LocationMatch "^/content/.*\.coreimg.*\.(?i:jpe?g|png|gif|svg)$">
         Header set Cache-Control "max-age=2592000,stale-while-revalidate=43200,stale-if-error=43200,public,immutable" "expr=%{REQUEST_STATUS} < 400"
         Header set Age 0
      </LocationMatch>
      ```

   * Mettez en cache des ressources modifiables de la gestion des actifs numériques (DAM), telles que des images et des vidéos, pendant 24 h, avec actualisation de l’arrière-plan après 12 h afin d’éviter la fonction MISS.

      ```
      <LocationMatch "^/content/dam/.*\.(?i:jpe?g|gif|js|mov|mp4|png|svg|txt|zip|ico|webp|pdf)$">
         Header set Cache-Control "max-age=43200,stale-while-revalidate=43200,stale-if-error=43200" "expr=%{REQUEST_STATUS} < 400"
         Header set Age 0
      </LocationMatch>
      ```

### Comportement de la requête HEAD {#request-behavior}

Lorsqu’une demande d’HEAD est reçue sur le réseau de diffusion de contenu Adobe pour une ressource qui est **not** mise en cache, la requête est transformée et reçue par Dispatcher et/ou l’instance d’AEM en tant que requête de GET. Si la réponse peut être mise en cache, les requêtes HEAD suivantes seront diffusées à partir du réseau de diffusion de contenu. Si la réponse ne peut pas être mise en cache, les requêtes HEAD suivantes seront transmises à Dispatcher et/ou à l’instance AEM pendant une période qui dépend de la variable `Cache-Control` TTL.

### Paramètres de campagne marketing {#marketing-parameters}

Les URL de site Web incluent souvent des paramètres de campagne marketing qui servent à suivre le succès d’une campagne. Pour utiliser efficacement le cache du Dispatcher, il est recommandé de configurer le `ignoreUrlParams` property as [documenté ici](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=fr#ignoring-url-parameters).

Le `ignoreUrlParams` ne doit pas être commentée et doit référencer le fichier `conf.dispatcher.d/cache/marketing_query_parameters.any`. Le fichier peut être modifié en supprimant les commentaires des lignes correspondant aux paramètres relatifs à vos canaux marketing. Vous pouvez également ajouter d’autres paramètres.

```
/ignoreUrlParams {
{{ /0001 { /glob "*" /type "deny" }}}
{{ $include "../cache/marketing_query_parameters.any"}}
}
```

## Invalidation du cache du Dispatcher {#disp}

En règle générale, il n’est pas nécessaire d’invalider le cache de Dispatcher. Vous devez plutôt vous fier au Dispatcher qui actualise son cache lorsque le contenu est republié et au réseau de diffusion de contenu qui respecte les en-têtes d’expiration du cache.

### Invalidation du cache du Dispatcher pendant l’activation/la désactivation {#cache-activation-deactivation}

Comme les versions précédentes d’AEM, la publication ou l’annulation de publication des pages efface le contenu du cache de Dispatcher. Si un problème de mise en cache est suspecté, les clients doivent republier les pages en question et s’assurer qu’un hôte virtuel correspondant à la variable `ServerAlias` localhost, qui est requis pour l’invalidation du cache de Dispatcher.

Lorsque l’instance de publication reçoit une nouvelle version d’une page ou d’une ressource de l’auteur, elle utilise l’agent de vidage pour invalider les chemins appropriés sur son Dispatcher. Le chemin d’accès mis à jour est supprimé du cache de Dispatcher, ainsi que de ses parents, jusqu’à un niveau (vous pouvez le configurer avec l’événement [statfileslevel](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=fr#invalidating-files-by-folder-level)).

## Invalidation explicite du cache de Dispatcher {#explicit-invalidation}

Adobe recommande de s’appuyer sur des en-têtes de cache standard pour contrôler le cycle de vie de la diffusion du contenu. Cependant, si nécessaire, il est possible d’invalider le contenu directement dans Dispatcher.

La liste suivante contient des scénarios dans lesquels vous souhaitez peut-être invalider explicitement le cache (tout en écoutant éventuellement la fin de l’invalidation) :

* Après avoir publié du contenu tel que des fragments d’expérience ou des fragments de contenu, invalidation du contenu publié et mis en cache qui référence ces éléments.
* Notification d’un système externe une fois que les pages référencées ont été correctement invalidées.

Il existe deux méthodes pour invalider explicitement le cache :

* L’approche recommandée consiste à utiliser Sling Content Distribution (SCD) à partir de l’environnement de création.
* En utilisant l’API de réplication pour appeler l’agent de réplication de vidage de publication de Dispatcher.

Les approches diffèrent en termes de disponibilité de niveau, de capacité à dédupliquer les événements et de garantie de traitement des événements. Le tableau ci-dessous résume ces options :

<table style="table-layout:auto">
 <tbody>
  <tr>
    <th>S/O</th>
    <th>Disponibilité des niveaux</th>
    <th>Déduplication </th>
    <th>Garantie </th>
    <th>Action </th>
    <th>Impact </th>
    <th>Description </th>
  </tr>  
  <tr>
    <td>API Sling Content Distribution (SCD)</td>
    <td>Création</td>
    <td>Utilisation possible de l’API Discovery ou de l’activation du <a href="https://github.com/apache/sling-org-apache-sling-distribution-journal/blob/e18f2bd36e8b43814520e87bd4999d3ca77ce8ca/src/main/java/org/apache/sling/distribution/journal/impl/publisher/DistributedEventNotifierManager.java#L146-L149">mode de déduplication</a>.</td>
    <td>Au moins une fois.</td>
    <td>
     <ol>
       <li>AJOUTER</li>
       <li>SUPPRIMER</li>
       <li>INVALIDER</li>
     </ol>
     </td>
    <td>
     <ol>
       <li>Niveau hiérarchique/de statut</li>
       <li>Niveau hiérarchique/de statut</li>
       <li>Ressource de niveau uniquement</li>
     </ol>
     </td>
    <td>
     <ol>
       <li>Publie du contenu et invalide le cache.</li>
       <li>Supprime le contenu et invalide le cache.</li>
       <li>Invalide le contenu sans le publier.</li>
     </ol>
     </td>
  </tr>
  <tr>
    <td>API de réplication</td>
    <td>Publication</td>
    <td>Impossible, événement généré sur chaque instance de publication.</td>
    <td>Meilleur effort.</td>
    <td>
     <ol>
       <li>ACTIVER</li>
       <li>DÉSACTIVER</li>
       <li>SUPPRIMER</li>
     </ol>
     </td>
    <td>
     <ol>
       <li>Niveau hiérarchique/de statut</li>
       <li>Niveau hiérarchique/de statut</li>
       <li>Niveau hiérarchique/de statut</li>
     </ol>
     </td>
    <td>
     <ol>
       <li>Publie du contenu et invalide le cache.</li>
       <li>À partir du niveau de création/publication - supprime le contenu et invalide le cache.</li>
       <li><p><strong>À partir du niveau de création</strong> - Supprime le contenu et invalide le cache (s’il est déclenché à partir du niveau de création AEM sur l’agent de publication).</p>
           <p><strong>À partir du niveau de publication</strong> - Invalide uniquement le cache (s’il est déclenché à partir du niveau Publication AEM sur l’agent de vidage ou de vidage ressource seule).</p>
       </li>
     </ol>
     </td>
  </tr>
  </tbody>
</table>

Veuillez noter que les deux actions directement liées à l’invalidation du cache sont l’invalidation de l’API Sling Content Distribution (SCD) et la désactivation de l’API de réplication.

De plus, à partir du tableau, nous observons que :

* L’API SCD est nécessaire lorsque chaque événement doit être garanti, par exemple lors d’une synchronisation avec un système externe qui nécessite des connaissances précises. S’il existe un événement de mise à l’échelle de niveau publication au moment de l’appel d’invalidation, un événement supplémentaire est généré lorsque chaque nouvelle publication traite l’invalidation.

* L’utilisation de l’API de réplication n’est pas un cas d’utilisation courant, mais doit être utilisée lorsque le déclencheur d’invalidation du cache provient du niveau de publication et non du niveau de création. Cela peut s’avérer utile si la durée de vie du Dispatcher est configurée.

En conclusion, si vous souhaitez invalider le cache de Dispatcher, l’option recommandée est d’utiliser l’action Invalider de l’API SCD de l’auteur. De plus, vous pouvez également écouter l’événement afin de déclencher d’autres actions en aval.

### Distribution de contenu Sling (SCD) {#sling-distribution}

>[!NOTE]
>Lorsque vous utilisez les instructions présentées ci-dessous, sachez que vous devez tester le code personnalisé dans un environnement de développement AEM Cloud Service et non localement.

Lors de l’utilisation de l’action SCD depuis l&#39;environnement de création, le modèle d’implémentation est le suivant :

1. À partir de l’environnement de création, écrivez du code personnalisé pour appeler l’[API](https://sling.apache.org/documentation/bundles/content-distribution.html) de distribution de contenu sling, en transmettant l’action invalider avec une liste de chemins :

```
@Reference
private Distributor distributor;

ResourceResolver resolver = ...; // the resource resolver used for authorizing the request
String agentName = "publish";    // the name of the agent used to distribute the request

String pathToInvalidate = "/content/to/invalidate";
DistributionRequest distributionRequest = new SimpleDistributionRequest(DistributionRequestType.INVALIDATE, false, pathToInvalidate);
distributor.distribute(agentName, resolver, distributionRequest);
```

* (Facultatif) Prêtez attention à un événement qui reflète la ressource invalidée pour toutes les instances de Dispatcher :


```
package org.apache.sling.distribution.journal.shared;

import org.apache.sling.discovery.DiscoveryService;
import org.apache.sling.distribution.journal.impl.event.DistributionEvent;
import org.osgi.service.component.annotations.Component;
import org.osgi.service.component.annotations.Reference;
import org.osgi.service.event.Event;
import org.osgi.service.event.EventHandler;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import static org.apache.sling.distribution.DistributionRequestType.INVALIDATE;
import static org.apache.sling.distribution.event.DistributionEventProperties.DISTRIBUTION_PATHS;
import static org.apache.sling.distribution.event.DistributionEventProperties.DISTRIBUTION_TYPE;
import static org.apache.sling.distribution.event.DistributionEventTopics.AGENT_PACKAGE_DISTRIBUTED;
import static org.osgi.service.event.EventConstants.EVENT_TOPIC;

@Component(immediate = true, service = EventHandler.class, property = {
        EVENT_TOPIC + "=" + AGENT_PACKAGE_DISTRIBUTED
})
public class InvalidatedHandler implements EventHandler {
    private static final Logger LOG = LoggerFactory.getLogger(InvalidatedHandler.class);

    @Reference
    private DiscoveryService discoveryService;

    @Override
    public void handleEvent(Event event) {

        String distributionType = (String) event.getProperty(DISTRIBUTION_TYPE);

        if (INVALIDATE.name().equals(distributionType)) {
            boolean isLeader = discoveryService.getTopology().getLocalInstance().isLeader();
            // process the OSGi event on the leader author instance
            if (isLeader) {
                String[] paths = (String[]) event.getProperty(DISTRIBUTION_PATHS);
                String packageId = (String) event.getProperty(DistributionEvent.PACKAGE_ID);
                invalidated(paths, packageId);
            }
        }
    }

    private void invalidated(String[] paths, String packageId) {
        // custom logic
        LOG.info("Successfully applied package with id {}, paths {}", packageId, paths);
    }
}
```

<!-- Optionally, instead of using the isLeader approach, one could add an OSGi configuration for the PID org.apache.sling.distribution.journal.impl.publisher.DistributedEventNotifierManager and property deduplicateEvent=true. But we'll stick with just one strategy and not mention it (double-check this).**review this**-->

* (Facultatif) Exécutez la logique commerciale de la méthode `invalidated(String[] paths, String packageId)` ci-dessus.

>[!NOTE]
>
>Le réseau de diffusion de contenu Adobe n’est pas vidé lorsque Dispatcher est invalidé. Le réseau CDN géré par Adobe respecte les durées de vies et il n’est donc pas nécessaire qu’il soit vidé.

### API de réplication {#replication-api}

Ci-dessous, se trouve présenté le modèle d’implémentation lors de l’utilisation de l’action de désactivation de l’API de réplication :

1. Au niveau de la publication, appelez l’API de réplication pour déclencher l’agent de réplication de vidage de publication de Dispatcher.

Le point de terminaison de l’agent de vidage n’est pas configurable, mais il est plutôt préconfiguré pour pointer vers Dispatcher, avec le service de publication qui s’exécute en même temps que l’agent de vidage.

L’agent de vidage peut généralement être déclenché par des codes personnalisés basés sur des événements ou des workflows OSGi.

```
String[] paths = …
ReplicationOptions options = new ReplicationOptions();
options.setSynchronous(true);
options.setFilter( new AgentFilter {
  public boolean isIncluded (Agent agent) {
   return agent.getId().equals(“flush”);
  }
});

Replicator.replicate (session,ReplicationActionType.DELETE,paths, options);
```

<!-- In general, it will not be necessary to manually invalidate content in the dispatcher, but it is possible if needed.

>[!NOTE]
>Prior to AEM as a Cloud Service, there were two ways of invalidating the dispatcher cache.
>
>1. Invoke the replication agent, specifying the publish dispatcher flush agent
>2. Directly calling the `invalidate.cache` API (for example, `POST /dispatcher/invalidate.cache`)
>
>The dispatcher's `invalidate.cache` API approach will no longer be supported since it addresses only a specific dispatcher node. AEM as a Cloud Service operates at the service level, not the individual node level and so the invalidation instructions in the [Invalidating Cached Pages From AEM](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html) page are not longer valid for AEM as a Cloud Service.

The replication flush agent should be used. This can be done using the [Replication API](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/replication/Replicator.html). The flush agent endpoint is not configurable but pre-configured to point to the dispatcher, matched with the publish service running the flush agent. The flush agent can typically be triggered by OSGi events or workflows.

<!-- Need to find a new link and/or example -->
<!-- 
and for an example of flushing the cache, see the [API example page](https://helpx.adobe.com/experience-manager/using/aem64_replication_api.html) (specifically the `CustomStep` example issuing a replication action of type ACTIVATE to all available agents). 

The diagram presented below illustrates this.

![CDN](assets/cdnd.png "CDN")

If there is a concern that the dispatcher cache isn't clearing, contact [customer support](https://helpx.adobe.com/support.ec.html) who can flush the dispatcher cache if necessary.

The Adobe-managed CDN respects TTLs and thus there is no need fo it to be flushed. If an issue is suspected, [contact customer support](https://helpx.adobe.com/support.ec.html) support who can flush an Adobe-managed CDN cache as necessary. -->

## Bibliothèques côté client et cohérence entre les versions {#content-consistency}

Les pages sont composées de HTMLS, de JavaScript, de CSS et d’images. Nous vous recommandons d’utiliser le [framework de bibliothèques côté client (clientlibs)](/help/implementing/developing/introduction/clientlibs.md) pour importer des ressources JavaScript et CSS dans des pages HTML, en tenant compte des dépendances entre les bibliothèques JS.

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
1. Enregistrez les modifications. Il n’est pas nécessaire d’enregistrer cette configuration dans le contrôle de code source, car AEM as a Cloud Service active automatiquement cette configuration dans les environnements de développement, d’évaluation et de production.
1. Chaque fois que le contenu de la bibliothèque cliente est modifié, une nouvelle clé de hachage est générée et la référence HTML est mise à jour.
