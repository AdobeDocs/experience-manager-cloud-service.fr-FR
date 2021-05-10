---
title: Mise à jour de votre contenu via les API AEM Assets
description: Dans cette partie du Parcours de développement AEM sans fil, découvrez comment utiliser l’API REST pour accéder au contenu de vos fragments de contenu et le mettre à jour.
hide: true
hidefromtoc: true
index: false
exl-id: 8d133b78-ca36-4c3b-815d-392d41841b5c
translation-type: tm+mt
source-git-commit: 787af0d4994bf1871c48aadab74d85bd7c3c94fb
workflow-type: tm+mt
source-wordcount: '1668'
ht-degree: 68%

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

L’[API HTTP AEM Assets](/help/assets/mac-api-assets.md) englobe :

* l’API REST Assets,
* y compris la prise en charge des fragments de contenu

L’implémentation actuelle de l’API HTTP Assets est basée sur le style architectural **REST**.

L’API REST Assets permet aux développeurs de Adobe Experience Manager en tant que Cloud Service d’accéder au contenu (stocké dans AEM) directement via l’API HTTP, via **CRUD** opérations (Créer, Lire, Mettre à jour, Supprimer).

Grâce à ces opérations, l’API vous permet d’utiliser Adobe Experience Manager en tant que Cloud Service en tant que CMS (Gestion de contenu System) sans tête en fournissant Content Services à une application frontale JavaScript. Ou toute autre application pouvant exécuter des requêtes HTTP et gérer les réponses JSON. Par exemple, les applications à page unique (SPA), basées sur une structure ou personnalisées, nécessitent du contenu fourni via une API, souvent au format JSON.

>[!NOTE]
>
>Il est impossible de personnaliser la sortie JSON de l’API REST Assets.

L’API REST Assets :

* suit le principe HATEOAS
* met en œuvre le format SIREN

## Concepts clés {#key-concepts}

L’API Assets REST offre l’accès de style REST aux ressources stockées dans une instance AEM.

Elle utilise le point d’entrée `/api/assets` et requiert le chemin d’accès de la ressource pour y accéder (sans `/content/dam` qui précède).

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


La méthode HTTP détermine l’opération à exécuter :

* **GET** : pour récupérer une représentation JSON d’une ressource ou d’un dossier
* **POST** : pour créer des ressources ou des dossiers
* **PUT** : pour mettre à jour les propriétés d’une ressource ou d’un dossier
* **DELETE** : pour supprimer une ressource ou un dossier

>[!NOTE]
>
>Le corps de la requête et/ou les paramètres URL peuvent être utilisés pour configurer certaines de ces opérations ; par exemple, spécifier qu’un dossier ou une ressource doivent être créés par une requête **POST**.

Le format exact des requêtes prises en charge est défini dans la documentation Référence d’API.

### Comportement transactionnel {#transactional-behavior}

Toutes les requêtes sont atomiques.

Cela signifie que les requêtes suivantes (`write`) ne peuvent pas être combinées en une seule transaction pouvant aboutir ou échouer en tant qu’entité unique.

### Sécurité {#security}

Si l’API REST Assets est utilisée dans un environnement sans conditions d’authentification spécifiques, le filtre CORS d’AEM doit être configuré correctement.

>[!NOTE]
>
>Pour plus d’informations, voir :
>
>* CORS/AEM expliqué
>* Vidéo - Développement pour CORS et AEM


Il est recommandé d’utiliser OAuth dans les environnements ayant des exigences d’authentification spécifiques.

## Fonctionnalités disponibles {#available-features}

Les fragments de contenu sont un type spécifique de ressource ; voir Utilisation des fragments de contenu.

Pour plus d’informations sur les fonctions disponibles dans l’API, voir :

* L’API REST Ressources (Ressources supplémentaires)
* Types d’entité, où sont expliquées les fonctionnalités propres à chaque type pris en charge (en fonction des fragments de contenu).

### Pagination {#paging}

L’API REST Assets prend en charge la pagination (pour les requêtes GET) via les paramètres d’URL :

* `offset` : nombre de premières entités (enfants) à extraire
* `limit` : nombre maximal d’entités renvoyées

La réponse contiendra les informations de pagination dans la section `properties` de la sortie SIREN. Cette propriété `srn:paging` contient le nombre d’entités (enfants) (`total`), le décalage et la limite (`offset`, `limit`) tels que spécifiés dans la requête.

>[!NOTE]
>
>La pagination est généralement appliquée aux entités de conteneur (c’est-à-dire les dossiers ou les ressources comportant des rendus), car elle a trait aux enfants de l’entité demandée.

#### Exemple : pagination {#example-paging}

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

## Types d’entités {#entity-types}

### Dossiers {#folders}

Les dossiers servent de conteneurs pour les ressources et d’autres dossiers. Ils reflètent la structure du référentiel de contenu AEM.

L’API REST Assets expose l’accès aux propriétés d’un dossier (par exemple, son nom, son titre, etc.). Les ressources sont exposées en tant qu’entités enfants de dossiers et de sous-dossiers.

>[!NOTE]
>
>Selon le type des ressources et des dossiers enfants, la liste des entités enfants peut déjà contenir l’ensemble complet de propriétés qui définissent l’entité enfant respective. Une autre possibilité consiste à afficher uniquement un jeu limité de propriétés pour une entité dans cette liste d’entités enfants.

### Ressources {#assets}

Si une ressource est demandée, la réponse renvoie ses métadonnées, telles que le titre, le nom et les autres informations, comme défini par le schéma des ressources respectives.

Les données binaires d’une ressource sont exposées sous la forme d’un lien SIREN de type `content`.

Les ressources peuvent comporter plusieurs rendus. Elles sont généralement exposées en tant qu’entités enfants, à l’exception du rendu de miniature, qui est exposé sous la forme d’un lien de type `thumbnail` (`rel="thumbnail"`).

### Fragments de contenu {#content-fragments}

Un fragment de contenu est un type spécial de fichier. Il permet d’accéder aux données structurées, telles que les textes, les nombres, les dates, etc.

Comme il existe plusieurs différences au sein des ressources *standard* (telles que les images ou le son), certaines règles supplémentaires s’appliquent pour les gérer.

#### Représentation {#representation}

Les fragments de contenu :

* N’exposent aucune donnée binaire.
* Sont entièrement contenus dans la sortie JSON (dans la propriété `properties`).

* Sont également considérés comme atomiques, c’est-à-dire que les éléments et les variations sont exposés dans les propriétés du fragment et non pas en tant que liens ou entités enfants. Cela permet un accès efficace à la charge utile d’un fragment.

#### Modèles et fragments de contenu  {#content-models-and-content-fragments}

Actuellement, les modèles qui définissent la structure d’un fragment de contenu ne sont pas exposés via une API HTTP. Par conséquent, le *consommateur* doit disposer d’informations sur le modèle d’un fragment (au moins un minimum), bien que la plupart des informations puissent être déduites de la charge utile (par exemple, les types de données, etc.). Font partie de la définition.

Pour créer un fragment de contenu, le chemin (référentiel interne) du modèle doit être indiqué.

#### Contenu associé {#associated-content}

Le contenu associé n’est actuellement pas exposé.

## Utilisation de l’API REST Assets {#using-aem-assets-rest-api}

L’utilisation peut varier selon que vous utilisez un environnement d’auteur ou de publication AEM dans votre cas d’utilisation spécifique.

* Il est vivement recommandé de lier la création à une instance d’auteur ([et il n’existe actuellement aucun moyen de répliquer un fragment pour publier à l’aide de cette API](/help/assets/content-fragments/assets-api-content-fragments.md#limitations)).
* La diffusion est possible à partir des deux à la fois, car AEM traite le contenu demandé au format JSON uniquement.

   * Le stockage et la diffusion à partir d’une instance d’auteur AEM suffisent normalement pour les applications de bibliothèque multimédia opérant derrière le pare-feu.

   * Pour une diffusion web en direct, une instance de publication AEM est recommandée.

>[!CAUTION]
>
>La configuration du dispatcher sur les instances cloud AEM peut bloquer l’accès à `/api`.

>[!NOTE]
>
>Pour plus d’informations, voir la [Référence d’API](/help/assets/content-fragments/assets-api-content-fragments.md#api-reference). En particulier, [API Adobe Experience Manager Assets - Fragments de contenu](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/assets-api-content-fragments/index.html).

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

## Ressources supplémentaires {#additional-resources}

* [REST](https://fr.wikipedia.org/wiki/Representational_state_transfer)
* [Principe HATEOAS](https://fr.wikipedia.org/wiki/HATEOAS)
* [Format SIREN](https://github.com/kevinswiber/siren)
* [API HTTP Assets](/help/assets/mac-api-assets.md)
* [API REST de fragments de contenu](/help/assets/content-fragments/assets-api-content-fragments.md)
   * [Référence d’API](/help/assets/content-fragments/assets-api-content-fragments.md#api-reference)
* [Utilisation de fragments de contenu](/help/assets/content-fragments/content-fragments.md)
* [AEM Core Components](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/introduction.html)
* [CORS/AEM expliqué](https://helpx.adobe.com/fr/experience-manager/kt/platform-repository/using/cors-security-article-understand.html)
* [Vidéo - Développement pour CORS et AEM](https://helpx.adobe.com/fr/experience-manager/kt/platform-repository/using/cors-security-technical-video-develop.html)

