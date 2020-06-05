---
title: Prise en charge des fragments de contenu d’Adobe Experience Manager as a Cloud Service dans l’API Assets HTTP
description: Découvrez la prise en charge des fragments de contenu Adobe Experience Manager as a Cloud Service dans l’API HTTP Assets.
translation-type: tm+mt
source-git-commit: d4a377e963f088f72b34f01103a3877cd699ccb2
workflow-type: tm+mt
source-wordcount: '1892'
ht-degree: 99%

---


# Prise en charge des fragments de contenu dans l’API HTTP AEM Assets{#content-fragments-support-in-aem-assets-http-api}

## Présentation {#overview}

>[!NOTE]
>
>L’[API HTTP AEM Assets](/help/assets/mac-api-assets.md) englobe :
>
>* l’API REST Assets,
>* y compris la prise en charge des fragments de contenu

>
>
L’implémentation actuelle de l’API HTTP Assets est basée sur le style architectural [REST](https://fr.wikipedia.org/wiki/Representational_state_transfer).

L’[API REST Assets](/help/assets/mac-api-assets.md) permet aux développeurs d’Adobe Experience Manager as a Cloud Service d’accéder au contenu (stocké dans AEM) directement via l’API HTTP, via des opérations CRUD (création, lecture, mise à jour et suppression).

L’API permet d’utiliser Adobe Experience Manager as a Cloud Service en tant que système de gestion de contenu (CMS) sans interface utilisateur en fournissant des services de contenu à une application frontale JavaScript. Ou toute autre application pouvant exécuter des requêtes HTTP et gérer les réponses JSON.

Par exemple, les applications monopages, basées sur la structure ou personnalisées, nécessitent du contenu fourni via l’API HTTP, souvent au format JSON.

Bien que les [composants de base AEM](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/introduction.html) fournissent une API très complète, flexible et personnalisable pouvant traiter les opérations de lecture requises à cette fin, et dont la sortie JSON peut être personnalisée, ils ne nécessitent pas de connaissances sur AEM WCM (Web Content Management) pour la mise en œuvre, car ils doivent être hébergés sur des pages reposant sur des modèles AEM dédiés. Les entreprises de développement d’applications monopages n’ont pas toutes accès à ces connaissances.

Dans ce cas, l’API REST Assets peut être utilisée. Elle permet aux développeurs d’accéder à des ressources (par exemple, des images et des fragments de contenu) directement, sans devoir d’abord les intégrer dans une page puis diffuser leur contenu au format JSON sérialisé.

>[!NOTE]
>
>Il est impossible de personnaliser la sortie JSON de l’API REST Assets.

L’API REST Assets permet également aux développeurs de modifier du contenu, en créant, en mettant à jour ou en supprimant des ressources, des fragments de contenu et des dossiers.

L’API REST Assets :

* suit le [principe HATEOAS](https://fr.wikipedia.org/wiki/HATEOAS)

* met en œuvre le [format SIREN](https://github.com/kevinswiber/siren)

## Conditions préalables {#prerequisites}

L’API REST Assets est disponible pour chaque installation prête à l’emploi d’une version récente d’Adobe Experience Manager as a Cloud Service.

## Concepts clés {#key-concepts}

L’API REST Assets offre un accès de type [REST](https://fr.wikipedia.org/wiki/Representational_state_transfer) aux ressources stockées dans une instance AEM.

Elle utilise le point d’entrée `/api/assets` et requiert le chemin d’accès de la ressource pour y accéder (sans `/content/dam` qui précède).

* Cela signifie que pour accéder à la ressource à l’adresse suivante :
   * `/content/dam/path/to/asset`
* Vous devez demander :
   * `/api/assets/path/to/asset`

Par exemple, pour accéder à `/content/dam/wknd/en/adventures/cycling-tuscany`, demandez `/api/assets/wknd/en/adventures/cycling-tuscany.json`

>[!NOTE]
>Accès via :
>* `/api/assets` **ne nécessite pas** l’utilisation du sélecteur `.model`.
>* `/content/assets` **nécessite** l’utilisation du sélecteur `.model`.


La méthode HTTP détermine l’opération à exécuter :

* **GET** : pour récupérer une représentation JSON d’une ressource ou d’un dossier
* **POST** : pour créer des ressources ou des dossiers
* **PUT** : pour mettre à jour les propriétés d’une ressource ou d’un dossier
* **DELETE** : pour supprimer une ressource ou un dossier

>[!NOTE]
>
>Le corps de la requête et/ou les paramètres URL peuvent être utilisés pour configurer certaines de ces opérations ; par exemple, spécifier qu’un dossier ou une ressource doivent être créés par une requête **POST**.

<!--
The exact format of supported requests is defined in the [API Reference](/help/assets/assets-api-content-fragments.md#api-reference) documentation.
-->

### Comportement transactionnel {#transactional-behavior}

Toutes les requêtes sont atomiques.

Cela signifie que les requêtes suivantes (`write`) ne peuvent pas être combinées en une seule transaction pouvant aboutir ou échouer en tant qu’entité unique.

### API REST AEM (Assets) et composants AEM {#aem-assets-rest-api-versus-aem-components}

<table>
 <thead>
  <tr>
   <td>Aspect</td>
   <td>API REST Assets<br/> </td>
   <td>Composant AEM<br/> (composants utilisant des modèles Sling)</td>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>Cas d’utilisation pris en charge</td>
   <td>Objectif général.</td>
   <td><p>Optimisé pour une utilisation dans une application monopage (SPA) ou tout autre contexte (utilisant du contenu).</p> <p>Peut également contenir des informations de disposition.</p> </td>
  </tr>
  <tr>
   <td>Opérations prises en charge</td>
   <td><p>Créer, Lire, Mettre à jour, Supprimer.</p> <p>Avec d’autres opérations selon le type d’entité.</p> </td>
   <td>Lecture seule.</td>
  </tr>
  <tr>
   <td>Accès</td>
   <td><p>Accessible directement.</p> <p>Utilise le point d’entrée <code>/api/assets </code>, mappé sur <code>/content/dam</code> (dans le référentiel).</p> 
   <p>Voici un exemple de chemin : <code>/api/assets/wknd/en/adventures/cycling-tuscany.json</code></p>
   </td>
    <td><p>Doit être référencé via un composant AEM sur une page AEM.</p> <p>Utilise le sélecteur <code>.model</code> pour créer la représentation JSON.</p> <p>Voici un exemple de chemin :<br/> <code>/content/wknd/language-masters/en/adventures/cycling-tuscany.model.json</code></p> 
   </td>
  </tr>
  <tr>
   <td>Sécurité</td>
   <td><p>Plusieurs options sont possibles.</p> <p>OAuth est proposé ; peut être configuré séparément de la configuration standard.</p> </td>
   <td>Utilise la configuration standard d’AEM.</td>
  </tr>
  <tr>
   <td>Remarques sur l’architecture</td>
   <td><p>L’accès en écriture résout généralement une instance d’auteur.</p> <p>Un accès en lecture peut également être redirigée vers une instance de publication.</p> </td>
   <td>Comme cette approche est en lecture seule, elle est généralement utilisée pour les instances de publication.</td>
  </tr>
  <tr>
   <td>Sortie</td>
   <td>Sortie SIREN basée sur JSON : détaillée mais puissante. Permet de naviguer dans le contenu.</td>
   <td>Sortie propriétaire basée sur JSON ; configurable via les modèles Sling. La navigation dans la structure du contenu est difficile à mettre en œuvre (mais pas nécessairement impossible).</td>
  </tr>
 </tbody>
</table>

### Sécurité {#security}

Si l’API REST Assets est utilisée dans un environnement sans conditions d’authentification spécifiques, le filtre CORS d’AEM doit être configuré correctement.

>[!NOTE]
>
>Pour plus d’informations, voir :
>
>* [CORS/AEM expliqué](https://helpx.adobe.com/fr/experience-manager/kt/platform-repository/using/cors-security-article-understand.html)
>* [Vidéo - Développement pour CORS et AEM](https://helpx.adobe.com/fr/experience-manager/kt/platform-repository/using/cors-security-technical-video-develop.html)

>



Il est recommandé d’utiliser OAuth dans les environnements ayant des exigences d’authentification spécifiques.

## Fonctionnalités disponibles {#available-features}

Les fragments de contenu sont un type spécifique de ressource ; voir [Utilisation des fragments de contenu](/help/assets/content-fragments/content-fragments.md).

Pour plus d’informations sur les fonctions disponibles dans l’API, voir :

* L’[API REST Assets](/help/assets/mac-api-assets.md)
* [Types d’entité](/help/assets/assets-api-content-fragments.md#entity-types), où sont expliquées les fonctionnalités propres à chaque type pris en charge (en fonction des fragments de contenu).

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

```
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

Les données binaires d’une ressource sont exposées sous la forme d’un lien SIREN de type `content` (également appelé `rel attribute`).

Les ressources peuvent comporter plusieurs rendus. Elles sont généralement exposées en tant qu’entités enfants, à l’exception du rendu de miniature, qui est exposé sous la forme d’un lien de type `thumbnail` (`rel="thumbnail"`).

### Fragments de contenu {#content-fragments}

Un [fragment de contenu](/help/assets/content-fragments/content-fragments.md) est un type de ressource spécial. Il permet d’accéder aux données structurées, telles que les textes, les nombres, les dates, etc.

Comme il existe plusieurs différences au sein des ressources *standard* (telles que les images ou le son), certaines règles supplémentaires s’appliquent pour les gérer.

#### Représentation  {#representation}

Les fragments de contenu :

* N’exposent aucune donnée binaire.
* Sont entièrement contenus dans la sortie JSON (dans la propriété `properties`).

* Sont également considérés comme atomiques, c’est-à-dire que les éléments et les variations sont exposés dans les propriétés du fragment et non pas en tant que liens ou entités enfants. Cela permet un accès efficace à la charge utile d’un fragment.

#### Modèles et fragments de contenu  {#content-models-and-content-fragments}

Actuellement, les modèles qui définissent la structure d’un fragment de contenu ne sont pas exposés via une API HTTP. Par conséquent, le *consommateur* doit disposer d’informations sur le modèle d’un fragment (au moins un minimum), bien que la plupart des informations puissent être déduites de la charge utile (par exemple, les types de données, etc.). Font partie de la définition.

Pour créer un fragment de contenu, le chemin (référentiel interne) du modèle doit être indiqué.

#### Contenu associé {#associated-content}

Le contenu associé n’est actuellement pas exposé.

## Utilisation de {#using}

L’utilisation peut varier selon que vous utilisez un environnement d’auteur ou de publication AEM dans votre cas d’utilisation spécifique.

* La création est strictement liée à une instance d’auteur ([et il n’existe actuellement aucun moyen de répliquer un fragment pour publier à l’aide de cette API](/help/assets/assets-api-content-fragments.md#limitations)).
* La diffusion est possible à partir des deux à la fois, car AEM traite le contenu demandé au format JSON uniquement.

   * Le stockage et la diffusion à partir d’une instance d’auteur AEM suffisent normalement pour les applications de bibliothèque multimédia opérant derrière le pare-feu.

   * Pour une diffusion web en direct, une instance de publication AEM est recommandée.

>[!CAUTION]
>
>La configuration du dispatcher sur les instances cloud AEM peut bloquer l’accès à `/api`.

<!--
>[!NOTE]
>
>For further details, see the [API Reference](/help/assets/assets-api-content-fragments.md#api-reference). In particular, [Adobe Experience Manager Assets API - Content Fragments](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/assets-api-content-fragments/index.html). 
-->

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

## Restrictions {#limitations}

Il existe quelques restrictions :

* **Les variantes ne peuvent pas être écrites et mises à jour.** Si ces variantes sont ajoutées à une charge utile (par exemple, pour les mises à jour), elles seront ignorées. Toutefois, la variante sera traitée via la diffusion (`GET`).

* **Les modèles de fragment de contenu ne sont actuellement pas pris en charge** : ils ne peuvent pas être lus ni créés. Pour pouvoir créer un fragment de contenu, ou en mettre un existant à jour, les développeurs doivent connaître le chemin correct vers le modèle de fragment de contenu. Actuellement, l’interface utilisateur d’administration est le seul moyen d’obtenir un aperçu des modèles de fragment de contenu.
* **Les références sont ignorées**. Il n’existe actuellement aucune vérification pour savoir si un fragment de contenu existant est référencé ou non. Par conséquent, la suppression d’un fragment de contenu, par exemple, peut entraîner des problèmes sur une page contenant une référence au fragment de contenu en question.

## Codes d’état et messages d’erreur {#status-codes-and-error-messages}

Les codes d’état suivants s’affichent dans les circonstances pertinentes :

* **200** (OK)

   Affiché dans le scénario suivant :

   * demande d’un fragment de contenu via `GET`

   * mise à jour réussie d’un fragment de contenu via `PUT`

* **201** (créé)

   Affiché dans le scénario suivant :

   * création réussie d’un fragment de contenu via `POST`

* **404** (introuvable)

   Affiché dans le scénario suivant :

   * le fragment de contenu demandé n’existe pas

* **** 500 (Erreur interne du serveur)

   >[!NOTE]
   >
   >Cette erreur est renvoyée :
   >
   >    * lorsqu’une erreur ne pouvant pas être identifiée avec un code spécifique s’est produite ;
   >    * lorsque la charge utile donnée n’était pas valide.


   L’exemple suivant répertorie les scénarios courants dans lesquels ce statut d’erreur est renvoyé, avec le message d’erreur (espacement fixe) généré :

   * Le dossier parent n’existe pas (lors de la création d’un fragment de contenu via `POST`)
   * Aucun modèle de fragment de contenu n’est fourni (cq:model est manquant) ou ne peut être lu (en raison d’un chemin d’accès non valide ou d’un problème d’autorisation) ou il n’existe aucun modèle de fragment/modèle valide :

      * `No content fragment model specified`
      * `Cannot create a resource of given model '/foo/bar/qux'`
      * `Cannot adapt the resource '/foo/bar/qux' to a content fragment template`
   * Impossible de créer le fragment de contenu (problème d’autorisation potentiel) :

      * `Could not create content fragment`
   * Le titre et/ou la description n’ont pas pu être mis à jour :

      * `Could not set value on content fragment`
   * Impossible de définir les métadonnées :

      * `Could not set metadata on content fragment`
   * Élément de contenu introuvable ou impossible à mettre à jour

      * `Could not update content element`
      * `Could not update fragment data of element`

   Les messages d’erreur détaillés sont généralement renvoyés de la façon suivante :

   ```xml
   {
     "class": "core/response",
     "properties": {
       "path": "/api/assets/foo/bar/qux",
       "location": "/api/assets/foo/bar/qux.json",
       "parentLocation": "/api/assets/foo/bar.json",
       "status.code": 500,
       "status.message": "...{error message}.."
     }
   }
   ```

## Référence d’API  {#api-reference}

Pour accéder aux références d’API détaillées :
<!--
* [Adobe Experience Manager Assets API - Content Fragments](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/assets-api-content-fragments/index.html)
-->

* [API HTTP Assets](/help/assets/mac-api-assets.md)

   * [Fonctionnalités disponibles](/help/assets/mac-api-assets.md#available-features)

## Ressources supplémentaires {#additional-resources}

Pour plus d’informations, voir :

* [Documentation de l’API HTTP Assets](/help/assets/mac-api-assets.md)
* [Session AEM Gem : OAuth](https://helpx.adobe.com/fr/experience-manager/kt/eseminars/gems/aem-oauth-server-functionality-in-aem.html)

