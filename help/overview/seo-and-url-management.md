---
title: Bonnes pratiques de gestion des URL et de l’optimisation pour les moteurs de recherche pour Adobe Experience Manager Sites as a Cloud Service
description: Bonnes pratiques de gestion des URL et de l’optimisation pour les moteurs de recherche pour Adobe Experience Manager Sites as a Cloud Service
exl-id: abe3f088-95ff-4093-95a1-cfc610d4b9e9
source-git-commit: f0e9fe0bdf35cc001860974be1fa2a7d90f7a3a9
workflow-type: tm+mt
source-wordcount: '3709'
ht-degree: 80%

---

# Bonnes pratiques de gestion des URL et de l’optimisation pour les moteurs de recherche pour Adobe Experience Manager Sites as a Cloud Service{#seo-and-url-management-best-practices-for-aem}

L’optimisation pour les moteurs de recherche est devenue une préoccupation essentielle pour de nombreux spécialistes du marketing. Par conséquent, l’optimisation pour les moteurs de recherche doit être prise en compte dans de nombreux projets Adobe Experience Manager (AEM) as a Cloud Service.

Le présent document commence par décrire certaines [bonnes pratiques relatives à l’optimisation pour les moteurs de recherche](#seo-best-practices) et explique comment les suivre lors d’une mise en œuvre d’AEM as a Cloud Service. Il approfondit ensuite certaines des [étapes de mise en œuvre plus complexes](#aem-configurations) abordées dans la première section.

## Bonnes pratiques relatives à l’optimisation pour les moteurs de recherche {#seo-best-practices}

Cette section décrit certaines bonnes pratiques générales d’optimisation pour les moteurs de recherche.

### URL {#urls}

Il existe certaines bonnes pratiques reconnues dans les URL.

Dans votre projet AEM, lors de l’évaluation des URL, posez-vous la question suivante :

*&quot;Si un utilisateur voit cette URL et qu’aucun des contenus de la page n’est visible, peut-il décrire ce qu’était cette page ?&quot;*

Si la réponse est oui, alors l’URL fonctionne probablement bien pour un moteur de recherche.

Voici quelques conseils généraux sur la construction de vos URL pour l’optimisation pour les moteurs de recherche :

* Utilisez des tirets pour séparer les mots.

   * Nommez les pages en utilisant des tirets (-) comme séparateurs.
   * Évitez d’utiliser des majuscules, des traits de soulignement et des espaces.

* Dans la mesure du possible, évitez d’utiliser des paramètres de requête. Si nécessaire, limitez-les à deux ou moins.

   * Utilisez la structure de répertoire pour indiquer l’architecture des informations, le cas échéant.
   * Si une structure de répertoires n’est pas désirable, utilisez des sélecteurs Sling dans l’URL plutôt que des chaînes de requêtes. En plus de fournir une valeur pour l’optimisation du moteur de recherche, les sélecteurs Sling permettent la mise en cache des pages pour le Dispatcher.

* Plus une URL est lisible, mieux c’est ; faites figurer des mots-clés pour valoriser l’URL.

   * Lors de l’utilisation de sélecteurs sur une page, les sélecteurs qui fournissent une valeur sémantique sont recommandés.
   * Si un humain ne peut pas lire votre URL, un moteur de recherche ne le peut pas non plus.
   * Par exemple :
     `mybrand.com/products/product-detail.product-category.product-name.html`
est préférable à `mybrand.com/products/product-detail.1234.html`

* Évitez autant que possible les sous-domaines, car les moteurs de recherche les traitent comme des entités différentes et réduisent la valeur du site pour l’optimisation du moteur de recherche.

   * Utilisez plutôt des sous-chemins de premier niveau. Par exemple, utilisez `es.mybrand.com/home.html` plutôt que `www.mybrand.com/es/home.html`.

   * Planifiez la hiérarchie de contenu afin qu’elle corresponde à la façon dont le contenu est présenté, conformément à cette consigne.

* L’efficacité des mots-clés dans les URL diminue à mesure que la longueur de l’URL et la position du mot-clé augmentent. En d&#39;autres termes, plus court est mieux.

   * Utilisez les techniques et fonctionnalités de raccourcissement d’URL fournies par AEM pour supprimer les éléments d’URL inutiles.
   * Par exemple, `mybrand.com/en/myPage.html` est préférable à `mybrand.com/content/my-brand/en/myPage.html`.

* Utilisez des URL canoniques.

   * Si une URL peut être fournie à partir de différents chemins ou avec différents paramètres ou sélecteurs, veillez à utiliser une balise `rel=canonical` sur la page.

   * Cela peut être inclus dans le code du modèle d’AEM.

* Dans la mesure du possible, faites correspondre les URL aux titres des pages.

   * Les auteurs de contenu doivent être encouragés à suivre cette pratique.

* Prise en charge de l’insensibilité à la casse dans les demandes d’URL.

   * Configurez le Dispatcher afin de réécrire toutes les requêtes entrantes en minuscules.
   * Formez les auteurs de contenu à créer toutes les pages à l’aide de lettres minuscules.

* Assurez-vous que chaque page n’est diffusée qu’à partir d’un seul protocole.

   * Parfois, les sites sont diffusés sur `http` jusqu’à ce qu’un utilisateur atteigne une page avec, par exemple, un formulaire de passage en caisse ou de connexion, auquel moment il passe à `https`. En cas de liaison depuis cette page, si l’utilisateur ou l’utilisatrice peut revenir aux pages `http` et y accéder par `https`, le moteur de recherche les suit comme deux pages distinctes.

   * Actuellement, Google préfère les pages `https` aux pages `http`. Pour cette raison, il est souvent plus facile pour tous de diffuser l’ensemble du site `https`.

### Configuration du serveur {#server-configuration}

En termes de configuration du serveur, vous pouvez accomplir les étapes suivantes pour vous assurer que seul le contenu approprié est analysé :

* Utilisez un fichier `robots.txt` pour empêcher l’analyse de tout contenu qui ne doit pas être indexé.

   * Bloc **all** analyse sur les environnements de test.

* Lors du lancement d’un nouveau site avec des URL mises à jour, implémentez des redirections 301 pour vous assurer que votre classement d’optimisation pour les moteurs de recherche existant n’est pas perdu.
* Incluez une favicon pour votre site.
* Mettez en oeuvre un plan de site XML pour faciliter l’analyse de votre contenu par les moteurs de recherche. Veillez à inclure un plan de site mobile pour les sites mobiles et/ou réactifs.

## Configurations AEM {#aem-configurations}

Cette section décrit les étapes requises de façon à configurer AEM afin qu’il suive ces recommandations d’optimisation pour les moteurs de recherche.

### Utilisation de sélecteurs Sling {#using-sling-selectors}

Auparavant, des paramètres de requête étaient généralement utilisés lors de la création d’une application web d’entreprise.

La tendance des dernières années a été de les supprimer afin que les URL soient plus lisibles. Sur de nombreuses plates-formes, cela implique la mise en œuvre de redirections sur le serveur web ou réseau de diffusion de contenu, mais Sling simplifie cela. Sling selectors :

* Améliorez la lisibilité des URL.
* permettent de mettre les pages en cache sur le Dispatcher et améliorent souvent la sécurité ;
* permettent de traiter le contenu directement, plutôt que de disposer d’une classe servlet générique qui récupère le contenu. Vous pouvez ainsi profiter des avantages des listes ACL que vous appliquez au référentiel et des filtres que vous appliquez sur le Dispatcher.

#### Utilisation de sélecteurs pour les servlets {#using-selectors-for-servlets}

AEM propose deux options lors de l’écriture de servlets :

* **bin** servlets
* **Sling** servlets

Les exemples suivants illustrent comment enregistrer des servlets qui suivent ces deux schémas, ainsi que l’avantage obtenu grâce à l’utilisation des servlets Sling.

#### Servlets bin (un niveau vers le bas) {#bin-servlets-one-level-down}

Les servlets **bin** suivent le schéma issu de la programmation J2EE auquel nombre de développeurs sont habitués. La servlet est enregistrée à un chemin spécifique qui, dans le cas d’AEM, se trouve généralement sous `/bin`, et vous extrayez les paramètres de requête nécessaires dans la chaîne de requête.

L’annotation SCR pour ce type de servlet doit ressembler à ce qui suit :

```
@SlingServlet(paths = "/bin/myApp/myServlet", extensions = "json", methods = "GET")
```

Vous extrayez ensuite les paramètres à partir de la chaîne de requête via l’objet `SlingHttpServletRequest` inclus dans la méthode `doGet`, par exemple :

```
String myParam = req.getParameter("myParam");
```

L’URL résultante utilisée doit ressembler à ce qui suit :

`https://www.mydomain.com/bin/myApp/myServlet.json?myParam=myValue`

Cette approche comporte quelques points à prendre en compte :

* L’URL elle-même perd sa valeur en termes d’optimisation pour les moteurs de recherche. Les utilisateurs accédant au site, y compris les moteurs de recherche, ne reçoivent aucune valeur sémantique de l’URL, car l’URL représente un chemin d’accès programmatique et non la hiérarchie du contenu.
* La présence de paramètres de requête dans l’URL signifie que le Dispatcher ne pourra pas mettre la réponse en cache.
* Si vous souhaitez sécuriser cette servlet, vous devez mettre en œuvre votre propre logique de sécurité personnalisée dans la servlet.
* Le Dispatcher doit être configuré (avec soin) afin d’exposer `/bin/myApp/myServlet`. Exposer simplement `/bin` permettrait d’accéder à certaines servlets qui ne doivent pas être ouvertes pour les visiteurs du site.

#### Servlets Sling (un niveau vers le bas) {#sling-servlets-one-level-down}

**Sling** Les servlets vous permettent d’enregistrer votre servlet de la manière opposée. Plutôt que de vous adresser à une servlet et de spécifier le contenu dont vous souhaitez qu’elle effectue le rendu en fonction des paramètres de requête, vous devez aborder le contenu souhaité et spécifier la servlet qui doit effectuer le rendu du contenu en fonction des sélecteurs Sling.

L’annotation SCR pour ce type de servlet doit ressembler à ce qui suit :

```
@SlingServlet(resourceTypes = "myBrand/components/pages/myPageType", selectors = "myRenderer", extensions = "json", methods="GET")
```

Dans ce cas, la ressource que l’URL adresse (une instance de la ressource `myPageType`) est accessible dans la servlet automatiquement. Pour y accéder, vous devez appeler :

```
Resource myPage = req.getResource();
```

L’URL résultante utilisée doit ressembler à ce qui suit :

`https://www.mydomain.com/content/my-brand/my-page.myRenderer.json`

Les avantages de cette approche sont les suivants :

* Vous pouvez créer la valeur d’optimisation pour les moteurs de recherche, acquise par la sémantique présente dans la hiérarchie de votre site et le nom de la page.
* Comme aucun paramètre de requête n’est présent, le Dispatcher peut mettre la réponse en cache. En outre, toutes les mises à jour apportées à la page adressée invalident ce cache lorsque la page est activée.
* Toutes les listes ACL appliquées à `/content/my-brand/my-page` prennent effet lorsqu’un utilisateur ou une utilisatrice tente d’accéder à cette servlet.
* Le Dispatcher aura déjà été configuré pour diffuser ce contenu en tant que fonction de diffusion du site web. Aucune configuration supplémentaire n’est requise.

### Réécriture d’URL {#url-rewriting}

Dans AEM, toutes les pages web sont stockées sous `/content/my-brand/my-content`. Cela peut être utile du point de vue de la gestion des données de référentiel. Toutefois, il ne s’agit pas nécessairement de la manière dont vous souhaitez que vos clients voient votre site et cela peut être en conflit avec la recommandation d’optimisation pour les moteurs de recherche selon laquelle les URL doivent être aussi courtes que possible. En outre, vous pouvez diffuser plusieurs sites web depuis la même instance AEM et différents noms de domaines.

Cette section décrit les options disponibles dans AEM pour gérer ces URL et les présenter aux utilisateurs d’une manière plus lisible et tenant davantage compte de l’optimisation pour les moteurs de recherche.

#### URL de redirection vers un microsite {#vanity-urls}

Si un auteur souhaite qu’une page soit accessible depuis un autre emplacement à des fins publicitaires, les URL de redirection vers un microsite d’AEM, définies page par page, peuvent être utiles. Afin d’ajouter une URL de redirection vers un microsite pour une page, accédez à la console **Sites** et modifiez les propriétés de la page. Au bas de l’onglet **Basique** se trouve une section dans laquelle peuvent être ajoutées les URL de redirection vers un microsite. Gardez à l’esprit que le fait que la page soit accessible via plusieurs URL réduit la valeur d’optimisation pour les moteurs de recherche de la page en question. Par conséquent, une balise d’URL canonique doit être ajoutée à la page afin d’éviter ce problème.

#### Noms de pages localisés {#localized-page-names}

Vous pouvez afficher les noms de pages localisés pour les utilisateurs de contenu traduit. Par exemple :

* plutôt que de demander à un utilisateur hispanophone d’accéder à :
  `www.mydomain.com/es/home.html`

* il serait préférable que l’URL soit :
  `www.mydomain.com/es/casa.html`.

La difficulté de localiser le nom de la page est que de nombreux outils de localisation disponibles sur la plateforme AEM reposent sur la correspondance des noms de page entre les paramètres régionaux pour que le contenu reste synchronisé.

La propriété `sling:alias` permet de pallier cette difficulté. `sling:alias` peut être ajouté comme propriété à n’importe quelle ressource pour donner un nom d’alias à la ressource. Dans l’exemple précédent, vous auriez :

* une page dans le JCR à :
  `…/es/home`

* à laquelle vous ajoutez ensuite une propriété :
  `sling:alias` = `casa`

Les outils de traduction d’AEM tels que le gestionnaire multisite peuvent ainsi conserver des relations entre :

* `/en/home`

* `/es/home`

Tout en permettant aux utilisateurs finaux d’interagir avec le nom de la page dans leur langue maternelle.

>[!NOTE]
>
>La propriété `sling:alias` peut être définie à l’aide de la [propriété Alias lors de la modification des propriétés de la page](/help/sites-cloud/authoring/fundamentals/page-properties.md#advanced).

#### /etc/map {#etc-map}

Dans une installation AEM standard :

* pour la configuration OSGi
  **Apache Sling Resource Resolver Factory**
(`org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl`)

* la propriété
  **Emplacement de mappage** (`resource.resolver.map.location`)

* a pour défaut la valeur `/etc/map`.

Les définitions de mappage peuvent être ajoutées à cet emplacement pour mapper des requêtes entrantes, réécrire des URL sur des pages dans AEM, ou les deux.

Pour créer un mappage, créez un nœud `sling:Mapping` à cet emplacement sous `/http` ou `/https`. En fonction des propriétés `sling:match` et `sling:internalRedirect` définies sur ce nœud, AEM redirigera tout le trafic pour l’URL correspondante vers la valeur spécifiée dans la propriété `internalRedirect`.

Bien qu’il s’agisse de l’approche documentée dans la documentation officielle d’AEM et de Sling, cette mise en œuvre ne fournit qu’une prise en charge limitée des expressions régulières par rapport aux options disponibles en utilisant directement `SlingResourceResolver`. De plus, une telle mise en œuvre des mappages peut entraîner des problèmes d’invalidation du cache du Dispatcher.

Voici un exemple de la manière dont ce problème se produit :

1. Un utilisateur visite votre site web et demande `https://www.mydomain.com/my-page.html`.
1. Le Dispatcher transmet cette requête au serveur de publication.
1. En utilisant `/etc/map`, le serveur de publication résout cette requête en `/content/my-brand/my-page` et effectue le rendu de la page.

1. Le Dispatcher met la réponse en cache à l’adresse `/my-page.html` et renvoie la réponse à l’utilisateur.
1. Un créateur/une créatrice de contenu modifie cette page et l’active.
1. L’agent de vidage du Dispatcher envoie une demande d’invalidation pour `/content/my-brand/my-page`**.** Étant donné que le Dispatcher ne possède pas de page mise en cache dans ce chemin, l’ancien contenu reste en cache et est périmé.

Il existe plusieurs façons de configurer des règles de vidage du Dispatcher personnalisées qui mappent les URL plus courtes aux URL plus longues à des fins d’invalidation du cache.

Cependant, il existe également un moyen plus simple de gérer cela :

1. **Règles SlingResourceResolver**

   À l’aide de la console web (par exemple, localhost:4502/system/console/configMgr), vous pouvez configurer le résolveur de ressources Sling :

   * **Apache Sling Resource Resolver Factory**
     `(org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl)`.

   Il est conseillé d’établir les mappages requis pour raccourcir les URL sous la forme d’expressions régulières, puis de définir ces configurations sous un nœud OsgiConfignode, `config.publish`, qui est inclus dans votre version.

   Plutôt que de définir les mappages dans `/etc/map`, vous pouvez les attribuer directement à la propriété **Mappages d’URL** (`resource.resolver.mapping`) :

   ```xml
   resource.resolver.mapping="[/content/my-brand/(.*)</$1]"
   ```

   Dans cet exemple simple, vous supprimez `/content/my-brand/` du début de toute URL où il est présent.

   Cela convertirait une URL :

   * de `/content/my-brand/my-page.html`
   * en simplement `/my-page.html`

   Cela est conforme à la pratique recommandée de conserver les URL aussi courtes que possible.

1. **Mappage de la sortie d’URL sur les pages**

   Après avoir défini vos mappages dans le résolveur de ressource Apache Sling (Apache Sling Resource Resolver), vous devez les utiliser dans vos composants pour vous assurer que les URL que vous générez sur vos pages sont courtes et ordonnées. Vous pouvez effectuer cette opération à l’aide de la fonction de mappage de `ResourceResolver`.

   Par exemple, si vous mettez en œuvre un composant de navigation personnalisée qui répertorie les enfants de la page en cours, vous pouvez utiliser la méthode de mappage comme suit :

   ```
   for (Page child : children) {
     String childUrl = resourceResolver.map(request, child.getPath());
     //Output the childUrl on the page here
   }
   ```

#### Apache HTTP Server mod_rewrite {#apache-http-server-mod-rewrite}

Jusqu’à présent, vous avez mis en œuvre des mappages avec la logique dans vos composants pour utiliser ces mappages lors de la génération des URL sur les pages.

La gestion de ces URL raccourcies lorsqu’elles entrent dans le Dispatcher constitue la pièce finale du puzzle ; c’est là que `mod_rewrite` entre en jeu. Le plus grand avantage de l’utilisation de `mod_rewrite` est que les URL sont mappées à leur forme longue. *before* ils sont envoyés au module de Dispatcher. Cela signifie que le Dispatcher demande l’URL longue au serveur de publication et la met en cache en conséquence. Par conséquent, toutes les demandes de vidage du Dispatcher entrant à partir du serveur de publication invalideront correctement ce contenu.

Pour mettre en œuvre ces règles, vous pouvez ajouter des éléments `RewriteRule` sous votre hôte virtuel dans la configuration Apache HTTP Server. Si vous souhaitez développer les URL raccourcies de l’exemple précédent, vous pouvez mettre en œuvre une règle qui ressemble à ce qui suit :

```
<VirtualHost *:80>
  ServerName www.mydomain.com
  RewriteEngine on
  RewriteRule ^/(.*)$ /content/my-brand/$1 [PT,L]
  …
</VirtualHost>
```

### Balises d’URL canoniques {#canonical-url-tags}

Les balises d’URL canoniques sont des balises de lien placées dans l’en-tête d’un document de HTML afin de clarifier la manière dont les moteurs de recherche doivent traiter une page lors de l’indexation du contenu. Elles présentent l’avantage de s’assurer qu’une page (et ses différentes versions) sera indexée comme étant la même, même si l’URL menant vers la page peut contenir des différences.

Par exemple, si un site offre une version d’une page compatible avec les imprimantes, un moteur de recherche indexerait potentiellement cette page indépendamment de la version standard de la page. La balise canonique indique au moteur de recherche qu’elles sont identiques.

Exemples :

* `<https://www.mydomain.com/my-brand/my-page.html>`
* `<https://www.mydomain.com/my-brand/my-page.print.html>`

Les deux appliqueraient la balise suivante à la tête de la page :

```xml
<link rel="canonical" href="my-brand/my-page.html"/>
```

`href` peut être relatif ou absolu. Le code doit être inclus dans le balisage de la page pour déterminer l’URL canonique de la page et générer cette balise.

### Configuration du Dispatcher pour le non-respect de la casse {#configuring-the-dispatcher-for-case-insensitivity}

La bonne pratique consiste à afficher toutes les pages en minuscules. Cependant, vous ne souhaitez pas qu’un utilisateur obtienne un 404 lorsqu’il accède à votre site web à l’aide de lettres majuscules dans son URL. Pour cette raison, Adobe recommande d’ajouter une règle de réécriture dans la configuration Apache HTTP Server de façon à mapper toutes les URL entrantes vers une version en lettres minuscules. En outre, les créateurs de contenu doivent être formés pour créer leurs pages avec des noms en minuscules.

Pour configurer Apache afin de forcer le trafic entrant à être écrit en minuscules, ajoutez les éléments suivants à la configuration `vhost` :

```xml
RewriteEngine On
RewriteMap lowercase int:tolower
```

De plus, ajoutez le code suivant au tout début du fichier `htaccess` :

```xml
RewriteCond $1 [A-Z]
RewriteRule ^(.*)$ /${lowercase:$1} [R=301,L]
```

### Mise en œuvre de robots.txt pour protéger les environnements de développement {#implementing-robots-txt-to-protect-development-environments}

Les moteurs de recherche *doivent* normalement vérifier la présence d’un fichier `robots.txt` à la racine du site avant d’analyser votre site. Si les principaux moteurs de recherche comme Google, Yahoo ou Bing le font, d’autres ne le font pas.

La façon la plus simple de bloquer l’accès à l’ensemble de votre site consiste à placer un fichier nommé `robots.txt` à la racine du site avec le contenu suivant :

```xml
User-agent: *
Disallow: /
```

Sur un environnement de production, vous pouvez également choisir de désactiver certains chemins que vous ne voulez pas voir indexer.

La mise en garde au moment de placer l’objet `robots.txt` à la racine du site, les requêtes de purge de Dispatcher peuvent effacer ce fichier et les mappages d’URL risquent de placer la racine du site à un autre emplacement que le fichier `DOCROOT` comme défini dans la configuration Apache HTTP Server. Pour cette raison, il est courant de placer ce fichier sur l’instance de création à la racine du site et de le répliquer dans l’instance de publication.

### Création d’un plan de site XML sur AEM {#building-an-xml-sitemap-on-aem}

Les navigateurs utilisent des plans de site XML pour mieux comprendre la structure des sites web. Bien que le fait de fournir un plan de site ne garantisse pas un meilleur référencement sur les moteurs de recherche, c’est une pratique recommandée. Vous pouvez conserver manuellement un fichier XML sur le serveur web afin qu’il soit utilisé comme plan de site, mais il est conseillé de le générer par programmation, ce qui garantit que, lorsque les créateurs créent du contenu, le plan de site reflète automatiquement leurs modifications.

AEM utilise le [module de plan de site Apache Sling](https://github.com/apache/sling-org-apache-sling-sitemap) pour générer des plans de site XML, un module qui offre un large éventail d’options permettant aux développeurs et aux éditeurs de tenir à jour un plan de site XML Sites.

Le module de plan de site Apache Sling fait la distinction entre un plan de site de niveau supérieur et un plan de site imbriqué, tous deux générés pour toute ressource dont la propriété `sling:sitemapRoot` est définie sur `true`. En règle générale, les plans de site sont rendus à l’aide de sélecteurs localisés par le chemin du plan de site de niveau supérieur de l’arborescence, qui correspond à la ressource qui n’a aucun autre ancêtre racine du plan de site. Cette racine de plan de site de niveau supérieur expose également l’index de plan de site, qui est normalement ce que le propriétaire d’un site doit configurer dans le portail de configuration du moteur de recherche ou ajouter au fichier `robots.txt` du site.

Prenons l’exemple d’un site qui définit une racine de plan de site de niveau supérieur à l’adresse `my-page` et une racine de plan de site imbriqué à l’emplacement `my-page/news`, afin de générer un plan de site dédié pour les pages de la sous-arborescence news. Les URL pertinentes résultantes seraient :

* `<https://www.mydomain.com/my-brand/my-page.sitemap-index.xml>`
* `<https://www.mydomain.com/my-brand/my-page.sitemap.xml>`
* `<https://www.mydomain.com/my-brand/my-page.sitemap.news-sitemap.html>`

>[!NOTE]
>
> Les sélecteurs `sitemap` et `sitemap-index` peuvent interférer avec les implémentations personnalisées. Si vous ne souhaitez pas utiliser la fonctionnalité de produit, configurez votre propre servlet de manière à ce que ces sélecteurs disposent d’un `service.ranking` supérieur à 0.

Dans la configuration par défaut, la boîte de dialogue Propriétés de la page permet d’identifier une page en tant que racine du plan du site et, comme décrit ci-dessus, de générer un plan du site lui-même et de ses descendants. Ce comportement est implémenté par les implémentations de l’interface `SitemapGenerator` et peut être étendu en ajoutant d’autres implémentations. Cependant, comme la fréquence de régénération des plans de site XML dépend fortement des workflows et des workloads de création de contenu, le produit n’est livré avec aucune configuration de `SitemapScheduler`. Elle offre à la fonctionnalité un accord préalable effectif.

Pour activer la tâche en arrière-plan qui génère les plans de site XML, une `SitemapScheduler` doit être configuré. Pour ce faire, créez une configuration OSGI pour le `org.apache.sling.sitemap.impl.SitemapScheduler` de l’ID persistante. L’expression du planificateur `0 0 0 * * ?` peut être utilisée comme point de départ pour régénérer tous les plans de site XML, une fois par jour à minuit.

![Plan de site Apache Sling – Planificateur](assets/sling-sitemap-scheduler.png)

La tâche de génération du plan de site peut s’exécuter sur les instances de niveau création et publication. Dans la plupart des cas, il est recommandé d’exécuter la génération sur les instances de niveau publication, car les URL canoniques appropriées ne peuvent être générées qu’à ce niveau (en raison des règles de mappage des ressources Sling généralement présentes uniquement sur les instances de niveau publication). Cependant, il est possible d’intégrer en tant que plug-in une implémentation personnalisée du mécanisme d’externalisation utilisé pour générer les URL canoniques en implémentant l’interface [SitemapLinkExternalizer](https://javadoc.io/doc/com.adobe.cq.wcm/com.adobe.aem.wcm.seo/latest/com/adobe/aem/wcm/seo/sitemap/externalizer/SitemapLinkExternalizer.html). Si une implémentation personnalisée peut générer les URL canoniques d’un plan de site sur les instances de niveau création, le `SitemapScheduler` peut être configuré pour le mode d’exécution création et la charge de travail de génération du plan de site XML peut être répartie entre les instances du cluster de services création. Dans ce scénario, une attention particulière doit être accordée à la manipulation de contenus qui n’ont pas encore été publiés, qui ont été modifiés ou qui ne sont visibles que par un groupe restreint d’utilisateurs.

AEM Sites contient une implémentation par défaut d’un `SitemapGenerator` qui parcourt une arborescence de pages pour générer un plan de site. Il est préconfiguré pour ne générer que les URL canoniques d’un site et des alternatives linguistiques, le cas échéant. Il peut également être configuré pour inclure la date de dernière modification d’une page, si nécessaire. Pour ce faire, activez l’option *Ajouter la dernière modification* de la configuration *Optimisation du moteur de recherche Adobe AEM - Générateur de plan de site de l’arborescence de page* et sélectionnez une *Dernière modification de source*. Lorsque les plans de site sont générés au niveau de publication, il est recommandé d’utiliser la date `cq:lastModified`.

![Optimisation du moteur de recherche Adobe AEM - Configuration du générateur de plans de site de l’arborescence de page](assets/sling-sitemap-pagetreegenerator.png)

Pour limiter le contenu d’un plan de site, les interfaces de service suivantes peuvent être mises en œuvre si nécessaire :

* Un [SitemapPageFilter](https://javadoc.io/doc/com.adobe.cq.wcm/com.adobe.aem.wcm.seo/latest/com/adobe/aem/wcm/seo/sitemap/SitemapPageFilter.html) peut être mis en œuvre pour masquer des pages dans les plans de site XML générés par le générateur de plans de site spécifique à AEM Sites.
* Un [SitemapProductFilter](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/sitemap/SitemapProductFilter.html) ou [SitemapCategoryFilter](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/sitemap/SitemapCategoryFilter.html) peut être mis en œuvre pour filtrer les produits ou les catégories à partir des plans de site XML générés par les générateurs de plans de site spécifiques du [Commerce Integration Framework](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/home.html?lang=fr).

Si les implémentations par défaut ne fonctionnent pas dans un cas d’utilisation particulier ou si les points d’extension ne sont pas suffisamment flexibles, un `SitemapGenerator` personnalisé peut être mis en œuvre pour prendre le contrôle intégral du contenu d’un plan de site généré. L’exemple suivant illustre la procédure à suivre, en utilisant la logique de mise en œuvre par défaut pour AEM Sites. Il utilise le [ResourceTreeSitemapGenerator](https://javadoc.io/doc/org.apache.sling/org.apache.sling.sitemap/latest/org/apache/sling/sitemap/spi/generator/ResourceTreeSitemapGenerator.html) comme point de départ pour parcourir une arborescence de pages :

```
import java.util.Optional;

import org.apache.sling.api.resource.Resource;
import org.apache.sling.sitemap.SitemapException;
import org.apache.sling.sitemap.builder.Sitemap;
import org.apache.sling.sitemap.builder.Url;
import org.apache.sling.sitemap.spi.common.SitemapLinkExternalizer;
import org.apache.sling.sitemap.spi.generator.ResourceTreeSitemapGenerator;
import org.apache.sling.sitemap.spi.generator.SitemapGenerator;
import org.jetbrains.annotations.NotNull;
import org.osgi.service.component.annotations.Component;
import org.osgi.service.component.annotations.Reference;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import com.adobe.aem.wcm.seo.sitemap.PageTreeSitemapGenerator;
import com.day.cq.wcm.api.Page;

@Component(
    service = SitemapGenerator.class,
    property = { "service.ranking:Integer=20" }
)
public class SitemapGeneratorImpl extends ResourceTreeSitemapGenerator {

    private static final Logger LOG = LoggerFactory.getLogger(SitemapGeneratorImpl.class);

    @Reference
    private SitemapLinkExternalizer externalizer;
    @Reference
    private PageTreeSitemapGenerator defaultGenerator;

    @Override
    protected void addResource(@NotNull String name, @NotNull Sitemap sitemap, Resource resource) throws SitemapException {
        Page page = resource.adaptTo(Page.class);
        if (page == null) {
            LOG.debug("Skipping resource at {}: not a page", resource.getPath());
            return;
        }
        String location = externalizer.externalize(resource);
        Url url = sitemap.addUrl(location + ".html");
        // add any additional content to the Url like lastmod, change frequency, etc
    }

    @Override
    protected final boolean shouldFollow(@NotNull Resource resource) {
        return super.shouldFollow(resource)
            && Optional.ofNullable(resource.adaptTo(Page.class)).map(this::shouldFollow).orElse(Boolean.TRUE);
    }

    private boolean shouldFollow(Page page) {
        // add additional conditions to stop traversing some pages
        return !defaultGenerator.isProtected(page);
    }

    @Override
    protected final boolean shouldInclude(@NotNull Resource resource) {
        return super.shouldInclude(resource)
            && Optional.ofNullable(resource.adaptTo(Page.class)).map(this::shouldInclude).orElse(Boolean.FALSE);
    }

    private boolean shouldInclude(Page page) {
        // add additional conditions to stop including some pages
        return defaultGenerator.isPublished(page)
            && !defaultGenerator.isNoIndex(page)
            && !defaultGenerator.isRedirect(page)
            && !defaultGenerator.isProtected(page);
    }
}
```

De plus, la fonctionnalité mise en œuvre pour les plans de site XML peut également être utilisée dans différents cas d’utilisation, par exemple pour ajouter le lien canonique ou des variantes linguistiques à l’en-tête d’une page. Reportez-vous à l’interface [SeoTags](https://javadoc.io/doc/com.adobe.cq.wcm/com.adobe.aem.wcm.seo/latest/com/adobe/aem/wcm/seo/SeoTags.html) pour plus d’informations.

### Création de redirections 301 pour les URL héritées {#creating-redirects-for-legacy-urls}

Lors du lancement d’un site avec une nouvelle structure, la mise en œuvre et le test des redirections 301 dans Apache HTTP Server sont importants pour deux raisons :

* Les URL héritées ont créé une valeur d’optimisation pour les moteurs de recherche au fil du temps. En implémentant une redirection, le moteur de recherche peut appliquer cette valeur à la nouvelle URL.
* Les utilisateurs de votre site peuvent avoir créé des signets sur ces pages. En implémentant des redirections, vous pouvez vous assurer d’orienter l’utilisateur vers la page du nouveau site qui correspond le mieux à l’emplacement où il tentait d’accéder à l’ancien site.

Veillez à consulter la section Ressources supplémentaires qui suit pour obtenir des instructions sur la mise en œuvre des redirections 301, ainsi que pour en savoir plus sur un outil permettant de tester que vos redirections fonctionnent comme prévu.

## Ressources supplémentaires {#additional-resources}

Pour plus d’informations, consultez les ressources supplémentaires suivantes :

<!--
* [Resource Mapping](/help/sites-deploying/resource-mapping.md)
-->

* [https://moz.com/blog/seo-cheat-sheet-anatomy-of-a-url](https://moz.com/blog/seo-cheat-sheet-anatomy-of-a-url)
* [https://moz.com/blog/15-seo-best-practices-for-structuring-urls](https://moz.com/blog/15-seo-best-practices-for-structuring-urls)
* [https://mysiteauditor.com/blog/top-10-most-important-seo-tips-for-url-optimization/](https://mysiteauditor.com/blog/top-10-most-important-seo-tips-for-url-optimization/)
* [https://sling.apache.org/documentation/the-sling-engine/servlets.html](https://sling.apache.org/documentation/the-sling-engine/servlets.html)
* [https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
* [https://httpd.apache.org/docs/current/mod/mod_rewrite.html](https://httpd.apache.org/docs/current/mod/mod_rewrite.html)
* [https://moz.com/blog/canonical-url-tag-the-most-important-advancement-in-seo-practices-since-sitemaps](https://moz.com/blog/canonical-url-tag-the-most-important-advancement-in-seo-practices-since-sitemaps)
* [https://www.robotstxt.org/robotstxt.html](https://www.robotstxt.org/robotstxt.html)
* [https://www.internetmarketingninjas.com/blog/search-engine-optimization/](https://www.internetmarketingninjas.com/blog/search-engine-optimization/)
* [https://github.com/Adobe-Marketing-Cloud/tools/tree/master/dispatcher/redirectTester](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/dispatcher/redirectTester)
* [https://adobe-consulting-services.github.io/](https://adobe-consulting-services.github.io/)
* [https://github.com/apache/sling-org-apache-sling-sitemap](https://github.com/apache/sling-org-apache-sling-sitemap)
