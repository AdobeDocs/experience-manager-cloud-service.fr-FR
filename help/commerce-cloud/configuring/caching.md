---
title: Mise en cache et performances
description: Découvrez les différentes configurations disponibles pour activer GraphQL et la mise en cache de contenu afin d’optimiser les performances de votre implémentation commerciale.
exl-id: 21ccdab8-4a2d-49ce-8700-2cbe129debc6
feature: Commerce Integration Framework
role: Admin
index: false
source-git-commit: 173b70aa6f9ad848d0f80923407bf07540987071
workflow-type: tm+mt
source-wordcount: '811'
ht-degree: 96%

---

# Mise en cache et performances {#caching}

## Mise en cache de la réponse du composant et de GraphQL {#graphql}

Les composants principaux AEM CIF prennent déjà en charge la mise en cache des réponses GraphQL pour les composants individuels. Cette fonctionnalité peut être utilisée pour réduire considérablement le nombre d’appels d’arrière-plan GraphQL. Une mise en cache efficace peut être réalisée, en particulier pour les requêtes qui se répètent, comme la récupération de l’arborescence des catégories pour un composant de navigation ou la récupération de toutes les valeurs d’agrégations/de facettes disponibles affichées sur les pages de recherche de produits et de catégories.

Pour les composants principaux AEM CIF, la mise en cache étant configurée composant par composant, il est possible de contrôler si (et pendant combien de temps) les requêtes/réponses GraphQL sont mises en cache pour chaque composant. Il est également possible de définir le comportement de mise en cache des services OSGi à l’aide du client GraphQL.

### Configuration {#configuration}

Une fois configuré pour un composant donné, le cache commence à stocker les requêtes et les réponses GraphQL telles que définies par chaque entrée de configuration du cache. La taille du cache et la durée de mise en cache de chaque entrée sont définies projet par projet, selon, par exemple, les éléments suivants :

* Fréquence à laquelle les données du catalogue peuvent changer.
* Le degré d’importance pour un composant d’afficher toujours les dernières données possibles, etc.

Il n’y a pas d’invalidation du cache. Par conséquent, agissez prudemment lors de la définition des durées du cache.

Lors de la configuration de la mise en cache des composants, le nom du cache doit correspondre au nom des composants **proxy** que vous définissez dans votre projet.

Avant d’envoyer une requête GraphQL, le client ou la cliente vérifie si cette requête **exacte** est déjà mise en cache et renvoie éventuellement la réponse mise en cache. Pour correspondre, la requête GraphQL _doit_ doit correspondre exactement. En d’autres termes, la requête, le nom de l’opération (le cas échéant) et les variables (le cas échéant) _doivent_ doivent tous être égaux à la requête mise en cache. En outre, tous les en-têtes HTTP personnalisés qui peuvent être définis _doivent_ être également identiques. Par exemple, l’en-tête `Store` Adobe Commerce _doit_ correspondre.

### Exemples {#examples}

Adobe recommande de configurer une certaine mise en cache pour le service de recherche qui récupère toutes les valeurs des agrégations/facettes disponibles affichées sur les pages de recherche de produits et de catégories. Ces valeurs ne changent généralement que lorsqu’un nouvel attribut est ajouté aux produits, par exemple. Par conséquent, la durée de cette entrée de cache peut être « importante » si l’ensemble des attributs de produit ne change pas souvent. Bien que cette entrée soit spécifique au projet, Adobe recommande des valeurs de quelques minutes dans les phases de développement du projet et de quelques heures sur des systèmes de production stables.

Ce paramètre est généralement configuré avec l’entrée de cache suivante :

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:10:3600
```

Un autre exemple de scénario dans lequel la fonction de mise en cache GraphQl est recommandée est le composant de navigation. Cela est dû au fait qu’elle envoie la même requête GraphQL sur toutes les pages. Dans ce cas, l’entrée de cache est généralement définie sur :

```
venia/components/structure/navigation:true:10:600
```

Considérons ici que le [magasin de référence Venia](https://github.com/adobe/aem-cif-guides-venia) est utilisé. Notez l’utilisation du nom du proxy de composant `venia/components/structure/navigation`, et **non pas** le nom du composant de navigation CIF (`core/cif/components/structure/navigation/v1/navigation`).

La mise en cache d’autres composants doit être définie projet par projet, généralement en coordination avec la mise en cache configurée au niveau du Dispatcher. N’oubliez pas qu’il n’y a pas d’invalidation active de ces caches. Par conséquent, la durée de mise en cache doit être soigneusement définie. Il n’existe aucune valeur « universelle » qui correspondrait à tous les projets et cas d’utilisation possibles. Assurez-vous de définir une stratégie de mise en cache au niveau du projet qui correspond au mieux aux exigences de votre projet.

## Mise en cache du Dispatcher {#dispatcher}

La mise en cache de pages ou de fragments AEM dans le [Dispatcher AEM](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=fr) constitue une bonne pratique pour un projet AEM. En règle générale, elle repose sur des techniques d’invalidation qui garantissent qu’un contenu modifié dans AEM est correctement mis à jour dans le Dispatcher. Cette fonctionnalité est essentielle à la stratégie de mise en cache du Dispatcher AEM.

Outre le CIF du contenu géré par AEM, une page peut généralement afficher des données commerciales récupérées dynamiquement à partir d’Adobe Commerce via GraphQL. Bien que la structure de la page elle-même puisse ne jamais changer, le contenu commercial peut changer. C’est notamment le cas si des données de produit, telles que le nom et le prix, changent dans Adobe Commerce.

Afin de garantir que les pages CIF sont mises en cache pendant une durée limitée dans le Dispatcher AEM, Adobe recommande d’utiliser l’[Invalidation temporelle du cache](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=fr#configuring-time-based-cache-invalidation-enablettl) (mise en cache basée sur TTL) lors de la mise en cache de pages CIF dans le Dispatcher AEM. Cette fonctionnalité peut être configurée en AEM avec le package [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/) supplémentaire.

Avec la mise en cache TTL, un développeur définit généralement une ou plusieurs durées de mise en cache pour les pages AEM sélectionnées. Cette durée garantit que les pages CIF ne sont mises en cache dans le Dispatcher AEM que pendant la durée configurée et que le contenu est fréquemment mis à jour.

>[!NOTE]
>
>Bien que les données côté serveur puissent être mises en cache par le Dispatcher AEM, certains composants CIF, tels que les composants `product`, `productlist` et `searchresults` récupèrent en général à nouveau les prix des produits dans une requête de navigateur côté client lorsque la page est chargée. Ainsi, le contenu dynamique crucial est toujours récupéré au chargement de la page.

## Ressources supplémentaires {#additional}

* [Magasin de référence Venia](https://github.com/adobe/aem-cif-guides-venia)
* [Configuration de la mise en cache GraphQL](https://github.com/adobe/commerce-cif-graphql-client#caching)
* [AEM Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=fr)
