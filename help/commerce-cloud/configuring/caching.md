---
title: Mise en cache et performances
description: Mise en cache et performances
translation-type: tm+mt
source-git-commit: 2997a28e79b51e88ececbd46c81dbc6a6c443e68
workflow-type: tm+mt
source-wordcount: '830'
ht-degree: 2%

---


# Mise en cache et performances {#caching}

## Mise en cache de la réponse du composant et du graphique QL {#graphql}

Les composants principaux AEM CIF prennent déjà en charge la mise en cache des réponses GraphQL pour les composants individuels. Cette fonctionnalité peut être utilisée pour réduire le nombre d&#39;appels GraphQL d&#39;arrière-plan par un facteur important. Une mise en cache efficace peut être réalisée, en particulier pour les requêtes qui se répètent, comme la récupération de l’arborescence des catégories pour un composant de navigation ou la récupération de toutes les valeurs d’agrégation/facette disponibles affichées dans les pages de recherche et de catégorie de produits.

Pour les composants principaux CIF AEM, la mise en cache est configurée sur la base des composants, de sorte qu’il est possible de contrôler si (et pendant combien de temps) les requêtes/réponses GraphQL sont mises en cache pour chaque composant. Il est également possible de définir le comportement de mise en cache des services OSGi à l’aide du client GraphQL.

### Configuration

Une fois configuré pour un composant donné, le cache début le stockage des requêtes et réponses GraphQL telles que définies par chaque entrée de configuration du cache. La taille du cache et la durée de mise en cache de chaque entrée doivent être définies sur la base d&#39;un projet, en fonction, par exemple, de la fréquence à laquelle les données du catalogue peuvent changer, de l&#39;importance cruciale qu&#39;un composant affiche toujours les dernières données possibles, etc. Notez qu’il n’y a pas d’invalidation du cache. Soyez donc prudent lors de la définition des durées du cache.

Lors de la configuration de la mise en cache pour les composants, le nom du cache doit correspondre au nom des composants **proxy** que vous définissez dans votre projet.

Avant d’envoyer une requête GraphQL, le client vérifie si cette requête est déjà mise en cache et renvoie éventuellement la réponse mise en cache si elle est **exacte** . Pour établir une correspondance, la requête GraphQL DOIT correspondre exactement, c&#39;est-à-dire que la requête, le nom de l&#39;opération (le cas échéant), les variables (le cas échéant) DOIVENT toutes être égales à la requête mise en cache, ainsi que tous les en-têtes HTTP personnalisés qui peuvent être définis DOIVENT également être identiques. Par exemple, l’en-tête du Magento `Store` DOIT correspondre.

### Exemples

Nous vous recommandons de configurer une certaine mise en cache pour le service de recherche qui récupère toutes les valeurs d’agrégation/facette disponibles affichées dans les pages de recherche et de catégorie de produits. Ces valeurs ne changent généralement que lorsqu’un nouvel attribut est par exemple ajouté à des produits. Par conséquent, la durée de cette entrée de cache peut être &quot;importante&quot; si l’ensemble d’attributs de produit ne change pas souvent. Bien que ce soit spécifique au projet, nous recommandons des valeurs de quelques minutes dans les phases de développement du projet et de quelques heures sur des systèmes de production stables.

Il est généralement configuré avec l’entrée de cache suivante :

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:10:3600
```

Un autre exemple de scénario où la fonction de mise en cache de GraphQl est recommandée est le composant de navigation, car il envoie la même requête GraphQL sur toutes les pages. Dans ce cas, l’entrée de cache est généralement définie sur :

```
venia/components/structure/navigation:true:10:600
```

lors de la prise en compte du magasin [de référence](https://github.com/adobe/aem-cif-guides-venia) Venia est utilisé. Notez l’utilisation du nom du proxy de composant `venia/components/structure/navigation`et **non** le nom du composant de navigation CIF (`core/cif/components/structure/navigation/v1/navigation`).

La mise en cache d’autres composants doit être définie sur la base d’un projet, généralement en coordination avec la mise en cache configurée au niveau du Dispatcher. N’oubliez pas qu’il n’y a pas d’invalidation active de ces caches. Par conséquent, la durée de mise en cache doit être soigneusement définie. Il n’existe aucune valeur &quot;taille unique&quot; qui correspondrait à tous les projets et cas d’utilisation possibles. Assurez-vous de définir une stratégie de mise en cache au niveau du projet qui correspond le mieux aux exigences de votre projet.

## Mise en cache du répartiteur {#dispatcher}

La mise en cache de pages ou de fragments AEM dans l’Dispatcher [](https://docs.adobe.com/content/help/fr-FR/experience-manager-dispatcher/using/dispatcher.html) AEM est la meilleure pratique pour tout projet AEM. En règle générale, il repose sur des techniques d’invalidation qui garantissent que tout contenu modifié dans AEM est correctement mis à jour dans le Dispatcher. Il s’agit d’une fonctionnalité essentielle de la stratégie de mise en cache des Dispatchers AEM.

Outre le contenu géré par AEM pur, une page peut généralement afficher des données commerciales récupérées dynamiquement à partir d’un Magento via GraphQL. Bien que la structure de la page elle-même ne puisse jamais changer, le contenu du commerce peut changer, par exemple, si certaines données de produit (nom, prix, etc.) changent dans le Magento.

Pour nous assurer que les pages CIF peuvent être mises en cache pendant une durée limitée dans le répartiteur d&#39;AEM, nous vous recommandons donc d&#39;utiliser l&#39;invalidation [du cache basée sur le](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#configuring-time-based-cache-invalidation-enablettl) temps (également appelée mise en cache basée sur TTL) lors de la mise en cache des pages CIF dans l&#39;Dispatcher AEM. Cette fonctionnalité peut être configurée en AEM avec le package [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/) supplémentaire.

Avec la mise en cache TTL, un développeur définit généralement une ou plusieurs durées de mise en cache pour les pages AEM sélectionnées. Ainsi, les pages CIF ne sont mises en cache que dans le répartiteur AEM jusqu’à la durée configurée et le contenu est fréquemment mis à jour.

>[!NOTE]
>
>Bien que les données côté serveur puissent être mises en cache par le répartiteur AEM, certains composants CIF comme le `product`, `productlist`et `searchresults` les composants récupèrent toujours les prix des produits dans une demande de navigateur côté client lorsque la page est chargée. Ainsi, le contenu dynamique essentiel est toujours récupéré au chargement de la page.

## Ressources supplémentaires

- [Magasin de référence Venia](https://github.com/adobe/aem-cif-guides-venia)
- [Configuration de la mise en cache GraphQL](https://github.com/adobe/commerce-cif-graphql-client#caching)
- [AEM Dispatcher](https://docs.adobe.com/content/help/fr-FR/experience-manager-dispatcher/using/dispatcher.html)