---
title: Mappage de ressource
description: Découvrez comment définir des redirections, des URL de redirection vers un microsite et des hôtes virtuels pour AEM à l’aide du mappage des ressources.
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
feature: Configuring
exl-id: 1a1bb23c-d1d1-4e2b-811b-753e6a90a01b
source-git-commit: 7260649eaab303ba5bab55ccbe02395dc8159949
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 56%

---

# Mappage de ressource{#resource-mapping}

Le mappage de ressources permet de définir des redirections, des URL de redirection vers un microsite et des hôtes virtuels pour AEM.

Par exemple, vous pouvez utiliser ces mappages pour :

* faire précéder toutes les requêtes de `/content` afin que la structure interne soit masquée pour les visiteurs de votre site web ;
* définir une redirection afin que toutes les requêtes en direction de la page `/content/en/gateway` de votre site Web soient redirigées vers `https://gbiv.com/`.

Un mappage HTTP possible consiste à préfixer toutes les demandes à `localhost:4503` avec le répertoire `/content`. Un mappage de ce type peut être utilisé pour masquer la structure interne vis-à-vis des visiteurs du site web, car il rend :

`localhost:4503/content/we-retail/en/products.html`

Pour y accéder à l’aide de :

`localhost:4503/we-retail/en/products.html`

Comme le mappage ajoute automatiquement le préfixe `/content` to `/we-retail/en/products.html`.

>[!CAUTION]
>
>Les URL Vanity ne prennent pas en charge les modèles regex.

>[!NOTE]
>
>Voir la documentation Sling et les sections [Mappages pour la résolution de ressource](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) et [Ressources](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) pour plus d’informations.

## Affichage des définitions de mappage {#viewing-mapping-definitions}

Les mappages forment deux listes que le résolveur de ressources JCR évalue (de haut en bas) pour trouver une correspondance.

Ces listes peuvent être visualisées (ainsi que des informations de configuration) sous l’option **JCR ResourceResolver** de la console Felix ; par exemple, `https://<*host*>:<*port*>/system/console/jcrresolver` :

* Configuration indique la configuration actuelle (telle que définie pour le [résolveur de ressource Apache Sling](/help/overview/seo-and-url-management.md#etc-map)). 

* Test de configuration. Cela permet de saisir une URL ou un chemin d’accès vers la ressource. Cliquez sur **Résoudre** ou **Carte** pour confirmer la manière dont le système transforme l’entrée.

* **Resolver Map Entries (Entrées de mappage du résolveur)** La liste des entrées utilisées par les méthodes ResourceResolver.resolve pour mapper les URL aux ressources. 

* **Mapping Map Entries (Entrées de mappage)** La liste des entrées utilisées par les méthodes ResourceResolver.map pour mapper les chemins d’accès des ressources aux URL.

Les deux listes affichent différentes entrées, y compris celles définies par défaut par les applications. Ces entrées visent souvent à simplifier les URL de l’utilisateur.

La paire de listes a **Modèle**, une expression régulière associée à la requête, avec une **Remplacement** qui définit la redirection à imposer.

Par exemple :

**Modèle** `^[^/]+/[^/]+/welcome$`

Déclenche :

**Remplacement** `/libs/cq/core/content/welcome.html`.

Pour rediriger une requête :

`https://localhost:4503/welcome` ``

Pour :

`https://localhost:4503/libs/cq/core/content/welcome.html`

De nouvelles définitions de mappage sont créées dans le référentiel.

>[!NOTE]
>
>De nombreuses ressources sont disponibles pour expliquer comment définir des expressions régulières. Par exemple : [https://www.regular-expressions.info/](https://www.regular-expressions.info/).

### Création de définitions de mappage dans AEM {#creating-mapping-definitions-in-aem}

Dans une installation standard d’AEM, vous trouverez le dossier suivant :

`/etc/map/http`

Ce dossier est la structure utilisée lors de la définition des mappages pour le protocole HTTP. D’autres dossiers (`sling:Folder`) peuvent être créés sous `/etc/map` pour tout autre protocole que vous souhaitez mapper.

#### Configuration d’une redirection interne vers /content {#configuring-an-internal-redirect-to-content}

Pour créer le mappage qui préfixe toute demande de https://localhost:4503/ avec `/content` :

1. À l’aide de CRXDE, accédez à `/etc/map/http`.

1. Créez un nœud :

   * **Type** `sling:Mapping` ce type de nœud est conçu pour de tels mappages, même si son utilisation n’est pas obligatoire.

   * **Nom** `localhost_any`

1. Cliquez sur **Enregistrer tout**.
1. **Ajoutez** les propriétés suivantes à ce nœud :

   * **Nom** `sling:match`

      * **Type** `String`

      * **Valeur** `localhost.4503/`

   * **Nom** `sling:internalRedirect`

      * **Type** `String`

      * **Valeur** `/content/`

1. Cliquez sur **Enregistrer tout**.

Ce mappage gère une requête telle que :
`localhost:4503/geometrixx/en/products.html`
comme si :
`localhost:4503/content/geometrixx/en/products.html`
a été demandé.

>[!NOTE]
>
>Voir [Ressources](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) dans la documentation Sling pour plus d’informations sur les propriétés sling disponibles et leur configuration.
>Par exemple : [Interpolation de chaîne](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html#string-interpolation-for-etcmap) s’avère utile, car il vous permet de configurer un mappage qui récupère par valeurs d’environnement au moyen de variables d’environnement.

>[!NOTE]
>
>Vous pouvez utiliser `/etc/map.publish` pour conserver les configurations dans l’environnement de publication. Ces configurations doivent être répliquées et le nouvel emplacement ( `/etc/map.publish`) configuré pour la variable **Emplacement du mappage** de [Apache Sling Resource Resolver](/help/overview/seo-and-url-management.md#etc-map) de l’environnement de publication.
