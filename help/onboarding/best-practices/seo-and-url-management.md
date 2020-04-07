---
title: Bonnes pratiques de gestion du référencement et des URL pour Adobe Experience Manager en tant que service Cloud
seo-title: Bonnes pratiques de gestion du référencement et des URL pour Adobe Experience Manager en tant que service Cloud
translation-type: tm+mt
source-git-commit: 70e76205e82b491fa77f65cd4257a79dda17b882

---


# Bonnes pratiques de gestion du référencement et des URL pour Adobe Experience Manager en tant que service Cloud{#seo-and-url-management-best-practices-for-aem}

L’optimisation pour les moteurs de recherche est devenue une préoccupation essentielle pour de nombreux spécialistes du marketing. Par conséquent, les préoccupations d’optimisation du référencement doivent être traitées sur de nombreux projets Adobe Experience Manager (AEM) en tant que projet de service Cloud.

This document first describes some [SEO best practices](#seo-best-practices) and recommendations for achieving these on an AEM as a Cloud Service implementation. Il approfondit ensuite certaines des [étapes de mise en œuvre plus complexes](#aem-configurations) abordées dans la première section.

## Meilleures pratiques relatives à l’optimisation pour les moteurs de recherche {#seo-best-practices}

Cette section décrit certaines meilleures pratiques générales d’optimisation pour les moteurs de recherche.

### URL {#urls}

Il existe des meilleures pratiques généralement acceptées en ce qui concerne les URL.

Dans votre projet AEM, lors de l’évaluation des URL, posez-vous la question suivante :

« Si un utilisateur voyait cette URL, mais aucun des éléments de contenu de la page, pourrait-il décrire ce qu’est cette page ? »

Si la réponse est oui, il est probable que l’URL fonctionne pour un moteur de recherche.

Voici quelques conseils généraux sur la façon d’optimiser les URL pour les moteurs de recherche :

* Utilisez des tirets pour séparer les mots.

   * Nommez les pages en utilisant des tirets (-) comme séparateurs.
   * Évitez d’utiliser la casse mixte, les soulignements et les espaces.

* Évitez si possible d’utiliser des paramètres de requête. Si nécessaire, limitez-les à deux ou moins.

   * Utilisez la structure de répertoires pour indiquer l’architecture d’informations, si disponible.
   * Si une structure de répertoires n’est pas une option, utilisez des sélecteurs Sling dans l’URL plutôt que des chaînes de requête. Outre la valeur d’optimisation fournie pour les moteurs de recherche, les sélecteurs Sling permettront également la mise en cache des pages pour le Dispatcher.

* Plus une URL est lisible, mieux c’est ; faire figurer des mots-clés dans l’URL permet d’accroître la valeur.

   * Si vous utilisez des sélecteurs sur une page, il est préférable d’opter pour des sélecteurs avec une valeur sémantique.
   * Si une personne ne peut pas lire votre URL, un moteur de recherche ne le peut pas non plus.
   * Par exemple :
      `mybrand.com/products/product-detail.product-category.product-name.html`
est préférable à `mybrand.com/products/product-detail.1234.html`

* Évitez autant que possible les sous-domaines, car les moteurs de recherche les traitent comme des entités, en réduisant la valeur d’optimisation du site pour les moteurs de recherche.

   * Utilisez plutôt des sous-chemins de premier niveau. For example, instead of `es.mybrand.com/home.html`, use `www.mybrand.com/es/home.html`.

   * Planifiez la hiérarchie de contenu afin qu’elle corresponde à la façon dont le contenu est présenté en fonction de cette consigne.

* L’efficacité des mots-clés dans les URL réduit à mesure qu’augmentent la longueur de l’URL et la position du mot-clé. En d’autres termes, plus c’est court, mieux c’est.

   * Utilisez les techniques et les fonctions de raccourcissement des URL fournies par AEM pour supprimer les éléments superflus des URL.
   * Par exemple, `mybrand.com/en/myPage.html` est préférable à `mybrand.com/content/my-brand/en/myPage.html`.

* Utilisez des URL réglementaires.

   * When a URL can be served from different paths or with different parameters or selectors, make sure to use a `rel=canonical` tag on the page.

   * Elle peut être incluse dans le code du modèle AEM.

* Dans la mesure du possible, faites correspondre les URL aux titres des pages.

   * Incitez les auteurs de contenu à suivre cette pratique.

* Soutenez la non-sensibilité à la casse dans les requêtes d’URL.

   * Configurez le Dispatcher afin de réécrire toutes les requêtes entrantes en minuscules.
   * Formez les auteurs de contenu afin qu’ils créent toutes les pages en utilisant des minuscules.

* Assurez-vous que chaque page est diffusée uniquement à partir d’un protocole.

   * Il arrive que des sites soient diffusés via `http` jusqu’à ce qu’un utilisateur arrive sur une page avec, par exemple, un formulaire de passage en caisse ou de connexion, où il passe alors en `https`. En cas de liaison depuis cette page, si l’utilisateur peut revenir aux pages `http` et y accéder par `https`, le moteur de recherche les suit comme deux pages distinctes.

   * Google currently prefers `https` pages to `http` ones. Pour cette raison, il est parfois plus facile pour tous les acteurs de diffuser l’ensemble du site par `https`.

### Configuration du serveur {#server-configuration}

En termes de configuration du serveur, vous pouvez accomplir les étapes suivantes pour vous assurer que seul le contenu approprié est analysé :

* Use a `robots.txt` file to block crawling of any content that should not be indexed.

   * Bloquez **toute** analyse sur les environnements de test.

* Lorsque vous lancez un nouveau site avec des URL mises à jour, mettez en œuvre des redirections 301 afin de vous assurer que le classement d’optimisation pour les moteurs de recherche existant n’est pas perdu.
* Incluez une icône favorite pour votre site.
* Mettez en œuvre un plan de site XML de façon à permettre aux moteurs de recherche d’analyser votre contenu. Veillez à inclure un plan de site mobile pour les sites mobiles et/ou réactifs.

## Configurations AEM {#aem-configurations}

Cette section décrit les étapes requises de façon à configurer AEM afin qu’il suive ces recommandations d’optimisation pour les moteurs de recherche.

### Utilisation de sélecteurs Sling {#using-sling-selectors}

Auparavant, des paramètres de requête étaient généralement utilisés lors de la création d’une application web d’entreprise.

La tendance ces dernières années a été de les supprimer afin de rendre les URL plus lisibles. Sur de nombreuses plates-formes, cela implique la mise en œuvre de redirections sur le serveur web ou réseau de diffusion de contenu, mais Sling simplifie cela. Les sélecteurs Sling :

* améliorent la lisibilité des URL ;
* permettent de mettre les pages en cache sur le Dispatcher et améliorent souvent la sécurité ;
* permettent de traiter le contenu directement, plutôt que de disposer d’une servlet générique qui récupère le contenu. Vous pouvez ainsi profiter des avantages des listes ACL que vous appliquez au référentiel et des filtres que vous appliquez sur le Dispatcher.

#### Utilisation de sélecteurs pour les servlets {#using-selectors-for-servlets}

AEM offre deux options lors de la rédaction de servlets :

* Servlets **bin**
* Servlets **Sling**

Les exemples suivants illustrent comment enregistrer des servlets qui suivent ces deux schémas, ainsi que l’avantage obtenu grâce à l’utilisation des servlets Sling.

#### Servlets bin (un niveau vers le bas) {#bin-servlets-one-level-down}

Les servlets **bin** suivent le schéma issu de la programmation J2EE auquel nombre de développeurs sont habitués. The servlet is registered at a specific path, which in the case of AEM is usually under `/bin`, and you extract the needed request parameters from the query string.

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

Avec cette approche, quelques points doivent être pris en considération :

* L’URL elle-même perd sa valeur en termes d’optimisation pour les moteurs de recherche. Les utilisateurs accédant au site, y compris les moteurs de recherche, ne reçoivent aucune valeur sémantique de l’URL, car l’URL représente un chemin programmatique et non la hiérarchie du contenu.
* La présence de paramètres de requête dans l’URL signifie que le Dispatcher ne pourra pas mettre la réponse en cache.
* Si vous souhaitez sécuriser cette servlet, vous devez mettre en œuvre votre propre logique de sécurité personnalisée dans la servlet.
* The dispatcher must be configured (carefully) to expose `/bin/myApp/myServlet`. Simply exposing `/bin` would allow access to certain servlets that should not be open to site visitors.

#### Servlets Sling (un niveau vers le bas) {#sling-servlets-one-level-down}

Les servlets **Sling** permettent d’enregistrer la servlet dans le sens opposé. Plutôt que d’adresser une servlet et de spécifier le contenu dont la servlet doit effectuer le rendu en fonction des paramètres de requête, vous adressez le contenu souhaité et spécifiez la servlet qui doit effectuer le rendu selon des sélecteurs Sling.

L’annotation SCR pour ce type de servlet doit ressembler à ce qui suit :

```
@SlingServlet(resourceTypes = "myBrand/components/pages/myPageType", selectors = "myRenderer", extensions = "json”, methods=”GET”)
```

Dans ce cas, la ressource que l’URL adresse (une instance de la ressource `myPageType`) est accessible dans la servlet automatiquement. Pour y accéder, vous appelez :

```
Resource myPage = req.getResource();
```

L’URL résultante utilisée doit ressembler à ce qui suit :

`https://www.mydomain.com/content/my-brand/my-page.myRenderer.json`

Les avantages de cette approche sont les suivants :

* Vous pouvez coder la valeur de l’optimisation pour les moteurs de recherche, acquise grâce à la sémantique présente dans la hiérarchie du site et le nom de la page.
* Comme aucun paramètre de requête n’est présent, le Dispatcher peut mettre la réponse en cache. En outre, toutes les mises à jour apportées à la page adressée invalident ce cache lorsque la page est activée.
* All ACLs applied to `/content/my-brand/my-page` will come into effect when a user tries to access this servlet.
* Le Dispatcher aura déjà été configuré pour diffuser ce contenu en tant que fonction de diffusion du site web. Aucune configuration supplémentaire n’est nécessaire.

### Réécriture d’URL {#url-rewriting}

In AEM, all of your web pages are stored under `/content/my-brand/my-content`. Ceci peut être utile du point de vue de la gestion des données de référentiel. Toutefois, il ne s’agit pas nécessairement de la manière dont vous souhaitez que vos clients voient votre site et cela peut être en conflit avec la recommandation d’optimisation pour les moteurs de recherche selon laquelle les URL doivent être aussi courtes que possible. De plus, vous pouvez diffuser plusieurs sites Web à partir de la même instance AEM et de noms de domaine différents.

Cette section décrit les options disponibles dans AEM pour gérer ces URL et les présenter aux utilisateurs d’une manière plus lisible et tenant davantage compte de l’optimisation pour les moteurs de recherche.

#### URL de redirection vers un microsite {#vanity-urls}

Si un auteur souhaite qu’une page soit accessible depuis un autre emplacement à des fins publicitaires, les URL de redirection vers un microsite d’AEM, définies page par page, peuvent être utiles. To add a vanity URL for a page, navigate to it in the **Sites** console and edit the page properties. At the bottom of the **Basic** tab, you see a section where vanity URLs can be added. Gardez à l’esprit que le fait d’avoir la page accessible via plusieurs URL fragmentera la valeur d’optimisation du référencement de la page. Une balise URL canonique doit donc être ajoutée à la page pour éviter ce problème.

#### Noms de pages localisés {#localized-page-names}

Vous pouvez afficher les noms de pages localisés pour les utilisateurs de contenu traduit. Par exemple :

* Plutôt que d’avoir un utilisateur hispanophone, accédez à :
   `www.mydomain.com/es/home.html`

* Il serait préférable que l’URL soit :
   `www.mydomain.com/es/casa.html`.

La difficulté en matière de localisation du nom d’une page réside dans le fait que plusieurs outils de localisation disponibles sur la plate-forme AEM nécessitent que les noms de cette page correspondent dans toutes les langues de manière à ce que le contenu reste synchronisé.

La propriété `sling:alias` permet de pallier cette difficulté. `sling:alias` peut être ajouté comme propriété à n’importe quelle ressource pour donner un nom d’alias à la ressource. Dans l’exemple précédent, vous auriez :

* Une page du JCR à l’adresse suivante :
   `…/es/home`

* Ajoutez ensuite une propriété :
   `sling:alias` = `casa`

Les outils de traduction d’AEM tels que le gestionnaire multisite peuvent ainsi conserver des relations entre :

* `/en/home`

* `/es/home`

Tout en permettant aux utilisateurs finaux d’interagir avec le nom de la page dans leur langue maternelle.

>[!NOTE]
>
>La `sling:alias` propriété peut être définie à l’aide de la propriété [Alias lors de la modification des propriétés](/help/sites-cloud/authoring/fundamentals/page-properties.md#advanced)de la page.

#### /etc/map {#etc-map}

Dans une installation AEM standard :

* pour la configuration OSGi
   **Fabrique de résolveur de ressource Apache Sling**
( `org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl`)

* la propriété
   **Emplacement** de mappage ( `resource.resolver.map.location`)

* defaults to `/etc/map`.

Les définitions de mappage peuvent être ajoutées à cet emplacement pour mapper des requêtes entrantes, réécrire des URL sur des pages dans AEM, ou les deux.

To create a new mapping, create a new `sling:Mapping` node in this location under `/http` or `/https`. Based on the `sling:match` and `sling:internalRedirect` properties that are set on this node, AEM will redirect all traffic for the matched URL to the value specified in the `internalRedirect` property.

Bien qu’il s’agisse de l’approche documentée dans la documentation officielle d’AEM et de Sling, cette mise en œuvre ne fournit qu’une prise en charge limitée des expressions régulières par rapport aux options disponibles en utilisant directement `SlingResourceResolver`. De plus, une telle mise en œuvre des mappages peut entraîner des problèmes d’invalidation du cache du Dispatcher.

Voici un exemple de la manière dont ce problème se produit :

1. A user visits your website and requests `https://www.mydomain.com/my-page.html`
1. Le Dispatcher transmet cette requête au serveur de publication.
1. Using `/etc/map`, the publish server resolves this request to `/content/my-brand/my-page` and renders the page.

1. The dispatcher caches the response at `/my-page.html` and returns the response to the user.
1. Un auteur de contenu modifie cette page et l’active.
1. The dispatcher flush agent sends an invalidation request for `/content/my-brand/my-page`**.**Etant donné que le répartiteur ne dispose pas d’une page mise en cache sur ce chemin d’accès, l’ancien contenu reste en cache et sera obsolète.

Il existe plusieurs façons de configurer les règles de vidage du Dispatcher qui mappent les URL plus courtes aux URL plus longues à des fins d’invalidation du cache.

Toutefois, il existe également une manière plus simple de gérer cela :

1. **Règles de SlingResourceResolver**

   À l’aide de la console web (par exemple, localhost:4502/system/console/configMgr), vous pouvez configurer le résolveur de ressource Sling :

   * **Fabrique de résolveur de ressource Apache Sling**
      `(org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl)`.
   Il est conseillé d’établir les mappages requis pour raccourcir les URL sous la forme d’expressions régulières, puis de définir ces configurations sous un nœud OsgiConfignode, `config.publish`, qui est inclus dans votre version.

   Rather than defining your mappings in `/etc/map`, they can be assigned directly to the property **URL Mappings** ( `resource.resolver.mapping`):

   ```xml
   resource.resolver.mapping="[/content/my-brand/(.*)</$1]"
   ```

   In this simple example, you are removing `/content/my-brand/` from the beginning of any URL where it is present.

   Cela convertirait une URL :

   * de `/content/my-brand/my-page.html`
   * to just `/my-page.html`
   Cela est en conformité avec la pratique recommandée d’avoir des URL aussi courtes que possible.

1. **Mappage de la sortie des URL sur les pages**

   Après avoir défini vos mappages dans le résolveur de ressource Apache Sling, vous devez les utiliser dans vos composants pour vous assurer que les URL que vous générez sur vos pages sont courtes et ordonnées. You can do this by using the map function of the `ResourceResolver`.

   Par exemple, si vous mettez en œuvre un composant de navigation personnalisée qui répertorie les enfants de la page en cours, vous pouvez utiliser la méthode de mappage comme suit :

   ```
   for (Page child : children) {
     String childUrl = resourceResolver.map(request, child.getPath());
     //Output the childUrl on the page here
   }
   ```

#### Apache HTTP Server mod_rewrite {#apache-http-server-mod-rewrite}

Jusqu’à présent, vous avez implémenté des mappages avec la logique de vos composants pour utiliser ces mappages lors de la sortie d’URL sur nos pages.

La gestion de ces URL raccourcies lorsqu’elles entrent dans le Dispatcher constitue la pièce finale du puzzle ; c’est là que `mod_rewrite` entre en jeu. L’utilisation de `mod_rewrite` a pour principal avantage que les URL sont mappées vers leur forme complète *avant* leur envoi au module de Dispatcher. Cela signifie que le Dispatcher demande l’URL longue au serveur de publication et la met en cache en conséquence. Par conséquent, toutes les demandes de vidage du Dispatcher entrant à partir du serveur de publication invalideront correctement ce contenu.

Pour mettre en œuvre ces règles, vous pouvez ajouter des éléments `RewriteRule` sous votre hôte virtuel dans la configuration Apache HTTP Server. Si vous souhaitez développer les URL raccourcies de l’exemple précédent, vous pouvez mettre en œuvre une règle qui ressemble à ce qui suit :

```
<VirtualHost *:80>
  ServerName www.mydomain.com
  RewriteEngine on
  RewriteRule ^/(.*)$ /content/my-brand/$1 [PT,L]
  …
</VirtualHost>
```

### Balises d’URL réglementaires {#canonical-url-tags}

Les balises d’URL réglementaires sont des balises de lien placées dans l’en-tête d’un document HTML pour savoir comment les moteurs de recherche doivent traiter une page au cours de l’indexation du contenu. Elles présentent l’avantage de s’assurer qu’une page (et ses différentes versions) sera indexée comme étant la même, même si l’URL menant vers la page peut contenir des différences.

Par exemple, si un site offre une version d’une page compatible avec les imprimantes, un moteur de recherche indexerait potentiellement cette page indépendamment de la version standard de la page. La balise réglementaire indique au moteur de recherche qu’elles sont identiques.

Exemples :

* https://www.mydomain.com/my-brand/my-page.html
* https://www.mydomain.com/my-brand/my-page.print.html

Les deux appliqueraient la balise suivante à la tête de la page :

```xml
<link rel=”canonical” href=”my-brand/my-page.html”/>
```

`href` peut être relatif ou absolu. Le code doit être inclus dans le balisage de la page pour déterminer l’URL réglementaire de la page et générer cette balise.

### Configuration du Dispatcher pour la non-sensibilité à la casse {#configuring-the-dispatcher-for-case-insensitivity}

Il est recommandé de diffuser toutes les pages en utilisant des minuscules. Cependant, vous ne souhaitez pas qu’un utilisateur obtienne une erreur 404 lorsqu’il accède à votre site web avec une URL contenant des lettres majuscules. Pour cette raison, Adobe recommande d’ajouter une règle de réécriture dans la configuration du serveur Apache HTTP afin de mapper toutes les URL entrantes en minuscules. En outre, les auteurs de contenu doivent être formés pour créer leurs pages avec des noms en minuscules.

Pour configurer Apache afin de forcer le trafic entrant à être écrit en minuscules, ajoutez les éléments suivants à la configuration `vhost` :

```xml
RewriteEngine On
RewriteMap lowercase int:tolower
```

En outre, ajoutez le code suivant au tout début du fichier `htaccess` :

```xml
RewriteCond $1 [A-Z]
RewriteRule ^(.*)$ /${lowercase:$1} [R=301,L]
```

### Mise en œuvre de robots.txt pour protéger les environnements de développement {#implementing-robots-txt-to-protect-development-environments}

Les moteurs de recherche *doivent* normalement vérifier la présence d’un fichier `robots.txt` à la racine du site avant d’analyser votre site. Doit être souligné ici parce que si les principaux moteurs de recherche comme Google, Yahoo ou Bing le respectent tous, certains moteurs de recherche étrangers ne le font pas.

La façon la plus simple de bloquer l’accès à l’ensemble de votre site consiste à placer un fichier nommé `robots.txt` à la racine du site avec le contenu suivant :

```xml
User-agent: *
Disallow: /
```

Sur un environnement de production, vous pouvez également choisir de désactiver certains chemins que vous ne voulez pas voir indexer.

The caveat with placing the `robots.txt` file at the site root is that dispatcher flush requests may clear this file out and URL mappings will likely place the site root somewhere different than the `DOCROOT` as defined in the Apache HTTP Server configuration. Pour cette raison, il est courant de placer ce fichier sur l’instance de création à la racine du site et de le répliquer dans l’instance de publication.

### Création d’un plan de site XML sur AEM {#building-an-xml-sitemap-on-aem}

Les robots d’indexation utilisent les plans de site XML pour mieux comprendre la structure des sites web. Bien que le fait de fournir un plan de site ne garantisse pas un meilleur référencement sur les moteurs de recherche, c’est une pratique recommandée. Vous pouvez conserver manuellement un fichier XML sur le serveur web afin qu’il soit utilisé comme plan de site, mais il est conseillé de le générer par programmation, ce qui garantit que, lorsque les auteurs créent du contenu, le plan de site reflète automatiquement leurs modifications.

Pour générer un plan de site par programmation, enregistrez une servlet Sling qui écoute les appels de `sitemap.xml`. La servlet peut ensuite utiliser la ressource fournie par le biais de l’API de servlet pour afficher la page en cours et ses enfants, produisant ainsi le XML. Le fichier XML est alors mis en cache sur le Dispatcher. Cet emplacement doit être référencé dans la propriété sitemap du fichier `robots.txt`. En outre, une règle de vidage personnalisée doit être mise en œuvre pour veiller à vider ce fichier chaque fois qu’une nouvelle page est activée.

>[!NOTE]
>
>You can register a Sling Servlet to listen for the selector `sitemap` with the extension `xml`. La servlet traitera alors la requête chaque fois qu’une URL se termine par :
>    `/<path-to>/page.sitemap.xml`
Vous pouvez alors obtenir la ressource demandée par la requête et générer un plan de site à partir de ce point dans l’arborescence de contenu à l’aide des API JCR.
L’avantage d’une telle approche se révèle lorsque plusieurs sites sont diffusés à partir d’une même instance. A request to `/content/siteA.sitemap.xml` would generate a sitemap for `siteA` while a request for `/content/siteB.sitemap.xml` would generate a sitemap for `siteB` without the need for writing additional code.

### Création de redirections 301 pour les URL héritées {#creating-redirects-for-legacy-urls}

Lors du lancement d’un site avec une nouvelle structure, la mise en oeuvre et le test des redirections 301 dans Apache HTTP Server sont importants pour deux raisons :

* Au fil du temps, les URL héritées ont accumulé de la valeur en matière de référencement sur les moteurs de recherche. La mise en œuvre d’une redirection permet au moteur de recherche d’appliquer cette valeur à la nouvelle URL.
* Les utilisateurs de votre site peuvent avoir créé des signets sur ces pages. En mettant en œuvre des redirections, vous êtes assuré de diriger l’utilisateur vers la page du nouveau site qui correspond le mieux à l’emplacement auquel il tentait d’accéder sur l’ancien site.

Veillez à consulter la section Ressources supplémentaires qui suit pour obtenir des instructions sur la mise en œuvre des redirections 301, ainsi qu’un outil pour tester que vos redirections fonctionnent comme prévu.

## Ressources supplémentaires {#additional-resources}

Pour plus d’informations, voir les ressources supplémentaires suivantes :

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
* [https://www.internetmarketingninjas.com/blog/search-engine-optimization/301-redirects/](https://www.internetmarketingninjas.com/blog/search-engine-optimization/301-redirects/)
* [https://github.com/Adobe-Marketing-Cloud/tools/tree/master/dispatcher/redirectTester](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/dispatcher/redirectTester)
* [https://adobe-consulting-services.github.io/](https://adobe-consulting-services.github.io/)
