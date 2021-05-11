---
title: Mise à jour de votre contenu via les API AEM Assets
description: Dans cette partie du Parcours de développement AEM sans fil, découvrez comment utiliser l’API REST pour accéder au contenu de vos fragments de contenu et le mettre à jour.
hide: true
hidefromtoc: true
index: false
exl-id: 8d133b78-ca36-4c3b-815d-392d41841b5c
translation-type: tm+mt
source-git-commit: 4a36cd3206784c0e4e3ed3d7007c83f44f1d5ee0
workflow-type: tm+mt
source-wordcount: '1130'
ht-degree: 49%

---

# Mise à jour de votre contenu via les API AEM Assets {#update-your-content}

>[!CAUTION]
>
>TRAVAUX EN COURS - La création de ce document est en cours et ne doit pas être comprise comme complète ou définitive ni être utilisée à des fins de production.

Dans cette partie du [AEM Parcours de développement sans affichage,](overview.md) apprenez à utiliser l’API REST pour accéder au contenu de vos fragments de contenu et le mettre à jour.

## L&#39;histoire jusqu&#39;à présent {#story-so-far}

Dans le document précédent de l&#39;parcours sans tête AEM, [Comment accéder à votre contenu par l&#39;intermédiaire des API de Diffusion AEM](access-your-content.md) vous avez appris à accéder à votre contenu sans tête en AEM par l&#39;API GraphQL  et vous devez maintenant :

* Avoir une bonne compréhension de GraphQL.
* Découvrez comment fonctionne l’API AEM GraphQL.
* Comprendre quelques exemples pratiques de requêtes.

Cet article s’appuie sur ces principes de base pour vous aider à comprendre comment mettre à jour votre contenu sans en-tête existant dans AEM via l’API REST.

## Intention {#objective}

* **Audience** : Avancé
* **Objectif** : Découvrez comment utiliser l’API REST pour accéder au contenu de vos fragments de contenu et le mettre à jour :
   * Présentation de l’API HTTP AEM Assets.
   * Présente et discute de la prise en charge du fragment de contenu dans l’API.
   * Illustrer les détails de l’API.

<!--
  * Look at sample code to see how things work in practice.
-->

## Pourquoi avez-vous besoin de l’API HTTP Ressources pour le fragment de contenu {#why-http-api}

Lors de l’étape précédente du Parcours sans en-tête, vous avez appris à utiliser l’API AEM GraphQL pour récupérer votre contenu à l’aide de requêtes.

Alors pourquoi une autre API est-elle nécessaire ?

L’API HTTP Assets vous permet de **lire** votre contenu, mais il vous permet également de **créer**, **mettre à jour** et **supprimer** le contenu - actions qui ne sont pas possibles avec l’API GraphQL.

L’API REST Assets est disponible pour chaque installation prête à l’emploi d’une version récente d’Adobe Experience Manager as a Cloud Service.

## API HTTP Assets {#assets-http-api}

L’API HTTP Assets englobe :

* l’API REST Assets,
* y compris la prise en charge des fragments de contenu

L’implémentation actuelle de l’API HTTP Assets repose sur le style architectural **REST** et vous permet d’accéder au contenu (stocké dans l’AEM) via les opérations **CRUD** (Créer, Lire, Mettre à jour, Supprimer).

Grâce à ces opérations, l’API vous permet d’utiliser Adobe Experience Manager en tant que Cloud Service en tant que CMS (Gestion de contenu System) sans tête en fournissant Content Services à une application frontale JavaScript. Ou toute autre application pouvant exécuter des requêtes HTTP et gérer les réponses JSON. Par exemple, les applications à page unique (SPA), basées sur une structure ou personnalisées, nécessitent du contenu fourni via une API, souvent au format JSON.

<!--
>[!NOTE]
>
>It is not possible to customize JSON output from the Assets REST API. 

The Assets REST API:

* follows the HATEOAS principle
* implements the SIREN format

## Key Concepts {#key-concepts}

The Assets REST API offers REST-style access to assets stored within an AEM instance. 

It uses the `/api/assets` endpoint and requires the path of the asset to access it (without the leading `/content/dam`). 

* This means that to access the asset at:
  * `/content/dam/path/to/asset`
* You need to request:
  * `/api/assets/path/to/asset` 

For example, to access `/content/dam/wknd/en/adventures/cycling-tuscany`, request `/api/assets/wknd/en/adventures/cycling-tuscany.json` 

>[!NOTE]
>Access over:
>
>* `/api/assets` **does not** need the use of the `.model` selector.
>* `/content/path/to/page` **does** require the use of the `.model` selector.

The HTTP method determines the operation to be executed:

* **GET** - to retrieve a JSON representation of an asset or a folder
* **POST** - to create new assets or folders
* **PUT** - to update the properties of an asset or folder
* **DELETE** - to delete an asset or folder

>[!NOTE]
>
>The request body and/or URL parameters can be used to configure some of these operations; for example, define that a folder or an asset should be created by a **POST** request.

The exact format of supported requests is defined in the API Reference documentation. 

### Transactional Behavior {#transactional-behavior}

All requests are atomic.

This means that subsequent (`write`) requests cannot be combined into a single transaction that could succeed or fail as a single entity.

### Security {#security}

If the Assets REST API is used within an environment without specific authentication requirements, AEM's CORS filter needs to be configured correctly.

>[!NOTE]
>
>For further information see:
>
>* CORS/AEM explained
>* Video - Developing for CORS with AEM

In environments with specific authentication requirements, OAuth is recommended.

## Available Features {#available-features}

Content Fragments are a specific type of Asset, see Working with Content Fragments.

For further information about features available through the API see:

* The Assets REST API (Additional Resources) 
* Entity Types, where the features specific to each supported type (as relevant to Content Fragments) are explained 

### Paging {#paging}

The Assets REST API supports paging (for GET requests) via the URL parameters:

* `offset` - the number of the first (child) entity to retrieve
* `limit` - the maximum number of entities returned

The response will contain paging information as part of the `properties` section of the SIREN output. This `srn:paging` property contains the total number of (child) entities ( `total`), the offset and the limit ( `offset`, `limit`) as specified in the request.

>[!NOTE]
>
>Paging is typically applied on container entities (i.e. folders or assets with renditions), as it relates to the children of the requested entity.

#### Example: Paging {#example-paging}

`GET /api/assets.json?offset=2&limit=3`

```json
...
"properties": {
    ...
    "srn:paging": {
        "total": 7,
        "offset": 2,
        "limit": 3
    }
    ...
}
...
```

## Entity Types {#entity-types}

### Folders {#folders}

Folders act as containers for assets and other folders. They reflect the structure of the AEM content repository.

The Assets REST API exposes access to the properties of a folder; for example its name, title, etc. Assets are exposed as child entities of folders, and sub-folders.

>[!NOTE]
>
>Depending on the asset type of the child assets and folders the list of child entities may already contain the full set of properties that defines the respective child entity. Alternatively, only a reduced set of properties may be exposed for an entity in this list of child entities.

### Assets {#assets}

If an asset is requested, the response will return its metadata; such as title, name and other information as defined by the respective asset schema.

The binary data of an asset is exposed as a SIREN link of type `content`.

Assets can have multiple renditions. These are typically exposed as child entities, one exception being a thumbnail rendition, which is exposed as a link of type `thumbnail` ( `rel="thumbnail"`).
-->

## API HTTP Assets et fragments de contenu {#assets-http-api-content-fragments}

Les fragments de contenu sont utilisés pour la diffusion sans en-tête et un fragment de contenu est un type spécial de fichier. Ils sont utilisés pour accéder à des données structurées, telles que des textes, des chiffres, des dates, entre autres.

<!--
As there are several differences to *standard* assets (such as images or audio), some additional rules apply to handling them.

### Representation {#representation}

Content fragments:

* Do not expose any binary data.
* Are completely contained in the JSON output (within the `properties` property).

* Are also considered atomic, i.e. the elements and variations are exposed as part of the fragment's properties vs. as links or child entities. This allows for efficient access to the payload of a fragment.

### Content Models and Content Fragments {#content-models-and-content-fragments}

Currently the models that define the structure of a content fragment are not exposed through an HTTP API. Therefore the *consumer* needs to know about the model of a fragment (at least a minimum) - although most information can be inferred from the payload; as data types, etc. are part of the definition.

To create a new content fragment, the (internal repository) path of the model has to be provided.

### Associated Content {#associated-content}

Associated content is currently not exposed.
-->

## Utilisation de l’API REST Assets {#using-aem-assets-rest-api}

### Accédez à l’adresse {#access}

L’API REST Assets utilise le point de terminaison `/api/assets` et nécessite le chemin d’accès de la ressource pour y accéder (sans le point de terminaison `/content/dam` en haut).

* Cela signifie que pour accéder à la ressource à l’adresse suivante :
   * `/content/dam/path/to/asset`
* Vous devez demander :
   * `/api/assets/path/to/asset`

Par exemple, pour accéder à `/content/dam/wknd/en/adventures/cycling-tuscany`, demandez `/api/assets/wknd/en/adventures/cycling-tuscany.json`

>[!NOTE]
>Accès via :
>
>* `/api/assets` **ne nécessite pas** l’utilisation du sélecteur `.model`.
>* `/content/path/to/page` **nécessite** l’utilisation du sélecteur `.model`.


### Opération {#operation}

La méthode HTTP détermine l’opération à exécuter :

* **GET** : pour récupérer une représentation JSON d’une ressource ou d’un dossier
* **POST** : pour créer des ressources ou des dossiers
* **PUT** : pour mettre à jour les propriétés d’une ressource ou d’un dossier
* **DELETE** : pour supprimer une ressource ou un dossier

>[!NOTE]
>
>Le corps de la requête et/ou les paramètres URL peuvent être utilisés pour configurer certaines de ces opérations ; par exemple, spécifier qu’un dossier ou une ressource doivent être créés par une requête **POST**.

Le format exact des requêtes prises en charge est défini dans la documentation Référence d’API.

L’utilisation peut varier selon que vous utilisez un environnement d’auteur ou de publication AEM dans votre cas d’utilisation spécifique.

* Il est vivement recommandé de lier la création à une instance d’auteur (et il n’existe actuellement aucun moyen de répliquer un fragment pour publier à l’aide de cette API).
* La diffusion est possible à partir des deux à la fois, car AEM traite le contenu demandé au format JSON uniquement.

   * Le stockage et la diffusion à partir d’une instance d’auteur AEM suffisent normalement pour les applications de bibliothèque multimédia opérant derrière le pare-feu.

   * Pour une diffusion web en direct, une instance de publication AEM est recommandée.

>[!CAUTION]
>
>La configuration du dispatcher sur les instances cloud AEM peut bloquer l’accès à `/api`.

>[!NOTE]
>
>Pour plus d’informations, voir la Référence d’API. En particulier, [API Adobe Experience Manager Assets - Fragments de contenu](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/assets-api-content-fragments/index.html).

### Lecture/Diffusion {#read-delivery}

Mode d’utilisation :

`GET /{cfParentPath}/{cfName}.json`

Par exemple :

`http://<host>/api/assets/wknd/en/adventures/cycling-tuscany.json`

La réponse est un JSON sérialisé avec le contenu structuré comme dans le fragment de contenu. Les références sont diffusées en tant qu’URL de référence.

Deux types d’opérations de lecture sont possibles :

* Lecture d’un fragment de contenu spécifique par chemin, ce qui renvoie la représentation JSON du fragment de contenu.
* Lecture d’un dossier de fragments de contenu par chemin : cela renvoie les représentations JSON de tous les fragments de contenu du dossier.

### Créer {#create}

Mode d’utilisation :

`POST /{cfParentPath}/{cfName}`

Le corps doit contenir une représentation JSON du fragment de contenu à créer, notamment tout contenu initial devant être défini sur les éléments de fragment de contenu. Il est obligatoire de définir la propriété `cq:model`, qui doit pointer vers un modèle de fragment de contenu valide. Sans cela, il se produira une erreur. Il est également nécessaire d’ajouter un en-tête `Content-Type`, défini sur `application/json`.

### Mettre à jour {#update}

Mode d’utilisation :

`PUT /{cfParentPath}/{cfName}`

Le corps doit contenir une représentation JSON de ce qui doit être mis à jour pour le fragment de contenu donné.

Il peut simplement s’agir du titre ou de la description d’un fragment de contenu, d’un élément unique ou de toutes les valeurs et/ou métadonnées d’un élément.

### Supprimer {#delete}

Mode d’utilisation :

`DELETE /{cfParentPath}/{cfName}`

Pour plus d’informations sur l’utilisation de l’API REST AEM Assets, vous pouvez vous reporter à :

* API HTTP des ressources Adobe Experience Manager (ressources supplémentaires)
* Prise en charge des fragments de contenu dans l’API HTTP AEM Assets (ressources supplémentaires)

## Eléments suivants {#whats-next}

Maintenant que vous avez terminé cette partie du Parcours de développement AEM sans tête, vous devez :

* Découvrez les bases de l’API HTTP AEM Assets.
* Découvrez comment les fragments de contenu sont pris en charge dans cette API.

<!--
* Have experience with sample code and know how the API works in practice.
-->

Vous devriez continuer votre parcours sans tête AEM en examinant ensuite le document [How to Put It All Together - Your App and Your Content in AEM Headless](put-it-all-together.md) où vous apprendrez à prendre votre projet sans tête et à le préparer pour qu’il soit en direct.

[La manière de créer des applications d’une seule page (SPA) avec ](create-spa.md) AEM vous montrera également comment créer des SPA modifiables à l’aide de la structure de l’éditeur de  d’AEM, ainsi que comment intégrer des  externes, en activant des fonctions de modification si nécessaire.

## Ressources supplémentaires {#additional-resources}

* [API HTTP Assets](/help/assets/mac-api-assets.md)
* [API REST de fragments de contenu](/help/assets/content-fragments/assets-api-content-fragments.md)
   * [Référence d’API](/help/assets/content-fragments/assets-api-content-fragments.md#api-reference)
* [API Adobe Experience Manager Assets - Fragments de contenu](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/assets-api-content-fragments/index.html)
* [Utilisation de fragments de contenu](/help/assets/content-fragments/content-fragments.md)
* [AEM Core Components](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/introduction.html)
* [CORS/AEM expliqué](https://helpx.adobe.com/fr/experience-manager/kt/platform-repository/using/cors-security-article-understand.html)
* [Vidéo - Développement pour CORS et AEM](https://helpx.adobe.com/fr/experience-manager/kt/platform-repository/using/cors-security-technical-video-develop.html)

