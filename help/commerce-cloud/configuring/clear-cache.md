---
title: Effacer le cache du composant et du GraphQL
description: Découvrez comment activer et vérifier la fonctionnalité d’effacement du cache dans AEM CIF.
feature: Commerce Integration Framework
role: Admin
exl-id: f89c07c7-631f-41a4-b5b9-0f629ffc36f0
source-git-commit: fb8b2645c0401d1358c7751db03a138dc2de2664
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 2%

---

# Effacer le cache du composant et du GraphQL {#clear-cache}

Ce document fournit un guide complet sur l’activation et la vérification de la fonctionnalité d’effacement du cache dans AEM CIF.

>[!NOTE]
>
> Cette fonctionnalité est expérimentale.

## Activation de la fonction Effacer le cache dans la configuration de CIF {#enable-clear-cache}

Par défaut, la fonction d’effacement du cache est désactivée dans la configuration de CIF. Pour l’activer, vous devez ajouter les éléments suivants à vos projets correspondants :

* Activez la `/bin/cif/invalidate-cache` de servlet qui vous permet de déclencher l’API clear-cache avec leurs requêtes correspondantes en ajoutant la configuration `com.adobe.cq.cif.cacheinvalidation.internal.InvalidateCacheNotificationImpl.cfg.json` dans votre projet comme illustré [ici](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config.author/com.adobe.cq.cif.cacheinvalidation.internal.InvalidateCacheNotificationImpl.cfg.json).
  >[!NOTE]
  >
  > La configuration doit être activée uniquement pour les instances de création.

* Activez le listener pour effacer le cache de chaque instance d’AEM (publication et création) en ajoutant la configuration `com.adobe.cq.commerce.core.cacheinvalidation.internal.InvalidateCacheSupport.cfg.json` dans votre projet, comme illustré [ici](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config/com.adobe.cq.commerce.core.cacheinvalidation.internal.InvalidateCacheSupport.cfg.json).
   * La configuration doit être activée pour les instances de création et de publication.
   * Activation du cache de Dispatcher (facultatif) : vous pouvez activer le paramètre Effacer le cache du Dispatcher en définissant la propriété `enableDispatcherCacheInvalidation` sur true dans la configuration ci-dessus. Cette option permet d’effacer le cache du Dispatcher.
     >[!NOTE]
     >
     > Cela ne fonctionne qu’avec les instances de publication.

   * Veillez également à indiquer le modèle correspondant qui convient à votre produit, à votre catégorie et à la page CMS qui doit être ajoutée au fichier de configuration ci-dessus pour le supprimer du cache du Dispatcher.

* Pour améliorer les performances des requêtes SQL afin de trouver la page correspondante associée au produit et à la catégorie, ajoutez l’index correspondant dans votre projet (recommandé). Pour plus d’informations, voir [cifCacheInvalidationSupport](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.apps/src/main/content/jcr_root/_oak_index/cifCacheInvalidationSupport/.content.xml).

## Vérification de la fonctionnalité Effacer le cache {#verify-clear-cache}

Pour vérifier que tout est correctement configuré :

* Déclenchez le servlet correspondant à l’instance de création AEM, par exemple [http://localhost:4502/bin/cif/invalidate-cache](http://localhost:4502/bin/cif/invalidate-cache) et vous devriez obtenir une réponse HTTP 200.
* Vérifiez qu’un nœud a été créé sous le chemin suivant dans les instances d’auteur : `/var/cif/cacheinvalidation`. Le nom du nœud suit ce modèle : `cmd_{{timestamp}}`.
* Vérifiez que le même nœud a été créé dans chaque instance de publication.

Maintenant, pour vérifier si les caches sont correctement effacés :
1. Accédez aux pages PLP et PDP correspondantes.
2. Mettez à jour un nom de produit ou de catégorie dans le moteur de commerce. Les modifications ne sont pas répercutées immédiatement dans AEM en fonction des configurations du cache.
3. Déclenchez l’API de servlet, comme illustré ici :

   ```
   curl --location '{Author AEM Instance Url}/bin/cif/invalidate-cache' \
   --header 'Content-Type: application/json' \
   --header 'Authorization: ••••••' \ // Mandatory
   --header 'Cookie: private_content_version=0299c5e4368a1577a6f454a61370317b' \
   --data '{
       "productSkus": ["Sku1", "Sku2"], // Optional: Pass the corresponding sku which got updated.
       "categoryUids":["CategoryUid"], // Optional : Pass the corresponding category-uid which got updated.
       "storePath": "/content/venia/us/en", // Mandatory : Needs to be given to know for which site we are removing the clear cache.
   }'
   ```
Si tout se passe bien, les nouvelles modifications sont répercutées dans chaque instance. Si les modifications ne sont pas visibles sur l’instance de publication, essayez d’accéder aux pages appropriées du PLP et du PDP dans une fenêtre de navigateur privée/privée.

>[!NOTE]
>
> Les instances de publication peuvent avoir plusieurs niveaux de calques de cache. Cette fonctionnalité n’est responsable que de l’effacement du cache de la mémoire interne d’AEM et du Dispatcher.

## Effacer l’API d’invalidation du cache {#clear-cache-api}

Il s’agit de l’API que vous devez déclencher chaque fois que vous souhaitez effacer du cache les données liées au commerce d’AEM.

Type de demande : `POST`

### En-têtes

| Paramètre | Valeur | Obligatoire | Commentaire |
|------------------------------|-------------------|---|---|
| `Content-Type` | `application/json` | Obligatoire |  |
| `Authorization` | Informations d’identification de l’utilisateur de l’auteur correspondant (type d’authentification : authentification de base) | Obligatoire | Ajoutez le nom d’utilisateur et le mot de passe correspondants. |


### Payload

Le tableau suivant présente les attributs existants prêts à l’emploi fournis par la fonctionnalité. Ces propriétés `InvalidateType` doivent être données en combinaison avec un attribut obligatoire (tel que `storePath`).

| `invalidateType` | Valeur | Type (Tableau/Chaîne/Booléen) | Cela effacera-t-il le cache du Dispatcher ? | Commentaire |
|------------------------------|-------------------|---|---|---|
| `productSkus` | SKU du produit, qui doit être invalidé à partir du cache. | Tableau | Oui | Effacez le cache de la mémoire interne à l&#39;aide du motif suivant :<br>```"\"sku\":\\s*\""```<br>Dispatcher<br><ul><li>Effacez le cache de page PDP des SKU correspondants.</li><li>Effacer le cache de la page de catégories correspondante dans laquelle ils existent (en fonction de la réponse GraphQL de Commerce)</li><li>Effacez le cache en fonction de la requête suivante :</li></ul><br>```SELECT content.[jcr:path] FROM [nt:unstructured] AS content<br>WHERE ISDESCENDANTNODE(content, '{storePath}')<br>AND ( (content.[product] IN ('sku1','sku2') AND content.[productType] = 'combinedSku')<br> OR (content.[selection] IN ('sku1','sku2') AND content.[selectionType] IN ('combinedSku', 'sku')))``` |
| `categoryUids` | UID de la catégorie - qui doit être invalidé à partir du cache. | Tableau | Oui | Effacez le cache de la mémoire interne à l&#39;aide du motif suivant :<br>```"\"uid\"\\s*:\\s*\\{\"id\"\\s*:\\s*\""```<br>Dispatcher<br><ul><li>Effacez le cache des pages de catégorie pour les données correspondantes (y compris sa page de catégorie enfant).</li><li>Effacer toutes les pages du PDP qui ont les catégories correspondantes</li><li>Effacez le cache en fonction de la requête suivante :</li></ul><br>```SELECT content.[jcr:path] FROM [nt:unstructured] AS content<br>WHERE ISDESCENDANTNODE(content,'{storePath}')<br>AND ((content.[categoryId] in ('category1','category2')<br>AND content.[categoryIdType] in ('uid'))<br>OR (content.[category] in ('category1','category2') AND content.[categoryType] in ('uid')))``` |
| `regexPatterns` | Si vous devez effacer les données de réponse GraphQL en fonction du modèle RegEx, utilisez cette option. | Tableau | Non | |
| `cacheNames` | Ces valeurs sont définies sous la configuration du client CIF GraphQL correspondante > Configuration du cache de StorePath correspondant > Configuration du GraphQL de GraphQL | Tableau | Non | |
| `invalidateAll` | Vrai ou faux | Booléen | Oui | |

Ce tableau indique la propriété obligatoire qui doit être transmise dans chaque appel API :

| Propriété | Valeur | Type (Tableau/Chaîne/Booléen) | Cela effacera-t-il le cache du Dispatcher ? | Commentaire |
|------------------------------|-------------------|---|---|---|
| `storePath` | Valeur correspondante du chemin d’accès au site à partir duquel le cache doit être supprimé (exemple : `/content/venia/us/en` comme référence avec le projet Venia). | Chaîne | Oui | Ceci doit être administré avec l’association de `invalidateType.` |

### Exemple de requête API

```
curl --location 'https://author-p10603-e145552-cmstg.adobeaemcloud.com/bin/cif/invalidate-cache' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--header 'Cookie: private_content_version=0299c5e4368a1577a6f454a61370317b' \
--data '{
"productSkus": ["VP01", "VT10"], // This will clear cache for the corresponding pages related with mentioned skus.
"categoryUids":["Mjk="], // This will clear cache for the corresponding pages related with mentioned categories.
"regexPatterns":["\"uid\"\\s*:\\s*\\{\"id\"\\s*:\\s*\"(Mjk=)\"", "\"sku\":\\s*\"(VP02|VP03)\""],
"cacheNames": ["venia/components/commerce/product"], // If this been added then it will clear respective caches for the corresponding storepath
"storePath": "/content/venia/us/en"
}'
```

## Extensibilité {#clear-cache-extensibility}

Cette fonctionnalité offre non seulement ses fonctionnalités de base, mais également son extensibilité, ce qui permet aux développeurs de l’exploiter et de la personnaliser davantage selon les besoins.

### Extension de l’attribut existant {#existing-attribute}

Dans les cas où le cache doit être effacé, mais qui ne sont pas actuellement couverts par la fonctionnalité basée sur les attributs existante (comme `categoryUids`), vous pouvez vous reporter à [ce fichier de référence](https://github.com/adobe/aem-cif-guides-venia/blob/main/core/src/main/java/com/venia/core/models/commerce/services/cacheinvalidation/ExtendedCategoryUidInvalidation.java) pour ajouter de nouveaux modèles et définir des `invalidatePaths` supplémentaires qui doivent être effacés du cache au-delà de ce que gère l’implémentation actuelle.

### Ajout d’un nouvel attribut personnalisé {#new-custom-attribute}

Si, par exemple, vous ne souhaitez pas utiliser l’attribut existant pour effacer le cache, vous avez la possibilité de créer votre propre attribut et de définir sa fonctionnalité correspondante.

* Si vous devez uniquement effacer le cache de la mémoire interne d’AEM (la réponse graphql), vous devez suivre [cette référence](https://github.com/adobe/aem-cif-guides-venia/blob/main/core/src/main/java/com/venia/core/models/commerce/services/cacheinvalidation/CustomInvalidation.java).
* Si vous devez effacer le cache de la mémoire interne et du cache du Dispatcher, vous devez suivre [cette référence](https://github.com/adobe/aem-cif-guides-venia/blob/main/core/src/main/java/com/venia/core/models/commerce/services/cacheinvalidation/CustomDispatcherInvalidation.java).
  >[!NOTE]
  >
  > Vous pouvez ignorer le cache d’effacement interne en renvoyant `null` pour la méthode `getPatterns()` .
