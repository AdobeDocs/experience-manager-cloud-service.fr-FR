---
title: Prise en charge des fragments de contenu Adobe Experience Manager as a Cloud Service dans l’API HTTP Assets
description: Découvrez la prise en charge des fragments de contenu dans l’API HTTP Assets, un élément important de la fonctionnalité de diffusion Adobe Experience Manager sans interface utilisateur.
feature: Content Fragments,Assets HTTP API
exl-id: d72cc0c0-0641-4fd6-9f87-745af5f2c232
source-git-commit: 674db680f46a4fd4772cb10fe7cb396652354dfe
workflow-type: tm+mt
source-wordcount: '1804'
ht-degree: 57%

---

# Prise en charge des fragments de contenu dans l’API HTTP AEM Assets {#content-fragments-support-in-aem-assets-http-api}

## Vue d’ensemble {#overview}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/extending/assets-api-content-fragments.html) |
| AEM as a Cloud Service | Cet article |

Découvrez la prise en charge des fragments de contenu dans l’API HTTP Assets, un élément important de la fonctionnalité de diffusion Adobe Experience Manager (AEM) sans interface utilisateur.

>[!NOTE]
>
>La variable [API ouvertes du modèle de fragment de contenu et de fragment de contenu](/help/headless/content-fragment-openapis.md) sont également disponibles.

>[!NOTE]
>
>L’[API HTTP Assets](/help/assets/mac-api-assets.md) englobe les éléments suivants :
>
>* API REST Assets
>* Prise en charge des fragments de contenu
>
>L’implémentation actuelle de l’API HTTP Assets est basée sur le style architectural [REST](https://fr.wikipedia.org/wiki/Representational_state_transfer).

>[!NOTE]
>
>Pour obtenir les informations les plus récentes sur les API de Experience Manager, consultez également la page [API ADOBE EXPERIENCE MANAGER AS A CLOUD SERVICE](https://developer.adobe.com/experience-cloud/experience-manager-apis/).

La variable [API REST Assets](/help/assets/mac-api-assets.md) permet aux développeurs d’Adobe Experience Manager as a Cloud Service d’accéder au contenu (stocké dans AEM) directement via l’API HTTP, au moyen des opérations CRUD (Create, Read, Update, Delete).

L’API vous permet d’utiliser Adobe Experience Manager as a Cloud Service en tant que CMS (Content Management System) sans interface utilisateur en fournissant Content Services à une application frontale JavaScript. Ou toute autre application pouvant exécuter des requêtes HTTP et gérer les réponses JSON.

Par exemple, les [applications monopages](/help/implementing/developing/hybrid/introduction.md), basées sur la structure ou personnalisées, nécessitent du contenu fourni via l’API HTTP, souvent au format JSON.

while [Composants principaux d’AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr) fournir une API personnalisable pouvant traiter les opérations de lecture requises à cette fin et dont la sortie JSON peut être personnalisée ; elles nécessitent AEM savoir-faire WCM (Web Content Management) pour la mise en oeuvre ; En effet, elles doivent être hébergées sur des pages basées sur des modèles d’AEM dédiés. Les entreprises de développement d’applications sur une seule page n’ont pas toutes accès à ces connaissances.

Dans ce cas, l’API REST Assets peut être utilisée. Elle permet aux développeurs d’accéder à des ressources (par exemple, des images et des fragments de contenu) directement, sans devoir d’abord les intégrer dans une page puis diffuser leur contenu au format JSON sérialisé.

>[!NOTE]
>
>Il est impossible de personnaliser la sortie JSON de l’API REST Assets.

L’API REST Assets permet également aux développeurs de modifier du contenu en créant, en mettant à jour ou en supprimant des ressources, des fragments de contenu et des dossiers existants.

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
* Requête :
   * `/api/assets/path/to/asset`

Par exemple, pour accéder à `/content/dam/wknd/en/adventures/cycling-tuscany`, demandez `/api/assets/wknd/en/adventures/cycling-tuscany.json`

>[!NOTE]
>Accès via :
>
>* `/api/assets` **ne nécessite pas** l’utilisation du sélecteur `.model`.
>* `/content/path/to/page` **nécessite** l’utilisation du sélecteur `.model`.

La méthode HTTP détermine l’opération à exécuter :

* **GET** : pour récupérer une représentation JSON d’une ressource ou d’un dossier
* **POST** - pour créer des ressources ou des dossiers
* **PUT** : pour mettre à jour les propriétés d’une ressource ou d’un dossier
* **SUPPRIMER** - pour supprimer une ressource ou un dossier.

>[!NOTE]
>
>Le corps de la requête et/ou les paramètres URL peuvent être utilisés pour configurer certaines de ces opérations ; par exemple, spécifier qu’un dossier ou une ressource doivent être créés par une requête **POST**.

Le format exact des requêtes prises en charge est défini dans la documentation [Référence de l’API](/help/assets/content-fragments/assets-api-content-fragments.md#api-reference).

>[!NOTE]
>
>La variable [API ouvertes du modèle de fragment de contenu et de fragment de contenu](/help/headless/content-fragment-openapis.md) sont également disponibles.

### Comportement transactionnel {#transactional-behavior}

Toutes les requêtes sont atomiques.

Cela signifie que les requêtes suivantes (`write`) ne peuvent pas être combinées en une seule transaction pouvant aboutir ou échouer en tant qu’entité unique.

### API REST AEM (Assets) et composants AEM {#aem-assets-rest-api-versus-aem-components}

<table>
 <thead>
  <tr>
   <td>Aspect</td>
   <td>API REST Assets<br/> </td>
   <td>Composant AEM<br/> (composants utilisant des modèles Sling)</td>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>Cas d’utilisation pris en charge</td>
   <td>Objectif général.</td>
   <td><p>Optimisé pour une utilisation dans une application monopage ou tout autre contexte (utilisant du contenu).</p> <p>Il peut également contenir des informations de mise en page.</p> </td>
  </tr>
  <tr>
   <td>Opérations prises en charge</td>
   <td><p>Créer, Lire, Mettre à jour, Supprimer.</p> <p>Avec des opérations supplémentaires, selon le type d’entité.</p> </td>
   <td>Lecture seule.</td>
  </tr>
  <tr>
   <td>Accès</td>
   <td><p>Il est accessible directement.</p> <p>Utilise le point d’entrée <code>/api/assets </code>, mappé sur <code>/content/dam</code> (dans le référentiel).</p> 
   <p>Voici un exemple de chemin : <code>/api/assets/wknd/en/adventures/cycling-tuscany.json</code></p>
   </td>
    <td><p>Il doit être référencé par le biais d’un composant AEM sur une page AEM.</p> <p>Utilise le sélecteur <code>.model</code> pour créer la représentation JSON.</p> <p>Voici un exemple de chemin :<br/> <code>/content/wknd/language-masters/en/adventures/cycling-tuscany.model.json</code></p> 
   </td>
  </tr>
  <tr>
   <td>Sécurité</td>
   <td><p>Plusieurs options sont possibles.</p> <p>OAuth est proposé ; peut être configuré séparément de la configuration standard.</p> </td>
   <td>Utilise la configuration AEM standard.</td>
  </tr>
  <tr>
   <td>Remarques architecturales</td>
   <td><p>L’accès en écriture s’adresse généralement à une instance d’auteur.</p> <p>La lecture peut également être dirigée vers une instance de publication.</p> </td>
   <td>Cette approche étant en lecture seule, elle est généralement utilisée pour les instances de publication.</td>
  </tr>
  <tr>
   <td>Sortie</td>
   <td>Sortie SIREN basée sur JSON : détaillée, mais puissante. Il permet de naviguer dans le contenu.</td>
   <td>Sortie propriétaire basée sur JSON ; configurable via les modèles Sling. La navigation dans la structure de contenu est difficile à mettre en œuvre (mais pas nécessairement impossible).</td>
  </tr>
 </tbody>
</table>

### Sécurité {#security}

Si l’API REST Assets est utilisée dans un environnement sans conditions d’authentification spécifiques, AEM filtre CORS doit être configuré correctement.

>[!NOTE]
>
>Pour en savoir plus, voir :
>
>* [CORS/AEM expliqué](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=fr)
>* [Vidéo - Développement pour CORS avec AEM (04:06)](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/develop-for-cross-origin-resource-sharing.html?lang=fr)
>

Il est recommandé d’utiliser OAuth dans les environnements ayant des exigences d’authentification spécifiques.

## Fonctionnalités disponibles {#available-features}

Les fragments de contenu sont un type spécifique de ressource. Voir [Utilisation de fragments de contenu](/help/assets/content-fragments/content-fragments.md).

Pour plus d’informations sur les fonctionnalités disponibles via l’API, voir :

* L’[API REST Assets](/help/assets/mac-api-assets.md)
* [Types d’entité](/help/assets/content-fragments/assets-api-content-fragments.md#entity-types), où sont expliquées les fonctionnalités propres à chaque type pris en charge (en fonction des fragments de contenu).

>[!NOTE]
>
>La variable [API ouvertes du modèle de fragment de contenu et de fragment de contenu](/help/headless/content-fragment-openapis.md) sont également disponibles.

### Pagination {#paging}

L’API REST Assets prend en charge la pagination (pour les demandes de GET) au moyen des paramètres d’URL :

* `offset` : nombre de premières entités (enfants) à extraire
* `limit` : nombre maximal d’entités renvoyées

La réponse contient des informations de pagination dans le cadre de la fonction `properties` de la sortie SIREN. Ceci `srn:paging` contient le nombre total d’entités (enfants) ( `total`), le décalage et la limite ( `offset`, `limit`) comme spécifié dans la requête.

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

Les dossiers servent de conteneurs pour les ressources et d’autres dossiers. Ils reflètent la structure du référentiel de contenu AEM.

L’API REST Assets expose l’accès aux propriétés d’un dossier. Par exemple, son nom et son titre. Les ressources sont exposées en tant qu’entités enfants de dossiers et de sous-dossiers.

>[!NOTE]
>
>Selon le type de ressource des ressources et dossiers enfants, la liste des entités enfants peut déjà contenir l’ensemble complet des propriétés qui définissent l’entité enfant respective. Une autre possibilité consiste à afficher uniquement un jeu limité de propriétés pour une entité dans cette liste d’entités enfants.

### Assets {#assets}

Si une ressource est demandée, la réponse renvoie ses métadonnées, telles que le titre, le nom et d’autres informations, telles que définies par le schéma de ressource correspondant.

Les données binaires d’une ressource sont exposées sous la forme d’un lien SIREN de type `content`.

Les ressources peuvent comporter plusieurs rendus. Elles sont généralement exposées en tant qu’entités enfants, à l’exception du rendu de miniature, qui est exposé sous la forme d’un lien de type `thumbnail` (`rel="thumbnail"`).

### Fragments de contenu {#content-fragments}

Un [fragment de contenu](/help/assets/content-fragments/content-fragments.md) est un type de ressource spécial. Il permet d’accéder aux données structurées, telles que les textes, les nombres, les dates, etc.

Comme il existe plusieurs différences au sein des ressources *standard* (telles que les images ou le son), certaines règles supplémentaires s’appliquent pour les gérer.

#### Représentation {#representation}

Les fragments de contenu :

* N’exposent aucune donnée binaire.
* Sont contenus dans la sortie JSON (dans la variable `properties` ).

* Ils sont aussi considérés comme atomiques. En d’autres termes, les éléments et les variations sont exposés dans les propriétés du fragment par rapport aux liens ou aux entités enfants. Cela permet un accès efficace à la payload d’un fragment.

#### Modèles et fragments de contenu {#content-models-and-content-fragments}

Actuellement, les modèles qui définissent la structure d’un fragment de contenu ne sont pas exposés via une API HTTP. Par conséquent, la variable *client* doit connaître le modèle d’un fragment (au moins un minimum), bien que la plupart des informations puissent être déduites de la charge utile, car les types de données, etc., font partie de la définition.

Pour créer un fragment de contenu, le chemin (référentiel interne) du modèle doit être indiqué.

#### Contenu associé {#associated-content}

Le contenu associé n’est pas exposé.

## Utiliser {#using}

L’utilisation peut varier selon que vous utilisez un environnement de création AEM ou de publication, ainsi que votre cas d’utilisation spécifique.

* Il est recommandé de lier la création à une instance d’auteur ([et il n’existe actuellement aucun moyen de répliquer un fragment pour le publier à l’aide de cette API.](/help/assets/content-fragments/assets-api-content-fragments.md#limitations)).
* La diffusion est possible à partir des deux, car AEM diffuse le contenu demandé au format JSON uniquement.

   * Le stockage et la diffusion depuis une instance d’auteur AEM doivent suffire pour les applications de bibliothèque multimédia situées derrière le pare-feu.

   * Pour une diffusion web en direct, une instance de publication AEM est recommandée.

>[!CAUTION]
>
>La configuration de Dispatcher sur AEM instances cloud peut bloquer l’accès à `/api`.

>[!NOTE]
>
>Voir [Référence d’API](/help/assets/content-fragments/assets-api-content-fragments.md#api-reference). En particulier, [API Adobe Experience Manager Assets – Fragments de contenu](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/assets-api-content-fragments/index.html).
>
>La variable [API ouvertes du modèle de fragment de contenu et de fragment de contenu](/help/headless/content-fragment-openapis.md) sont également disponibles.

## Limites {#limitations}

Il existe quelques restrictions :

* **Les modèles de fragment de contenu ne sont actuellement pas pris en charge** : ils ne peuvent pas être lus ni créés. Pour pouvoir créer ou mettre à jour un fragment de contenu existant, les développeurs doivent connaître le chemin correct vers le modèle de fragment de contenu. Actuellement, la seule méthode pour obtenir un aperçu de ces éléments est via l’interface utilisateur d’administration.
* **Les références sont ignorées**. Actuellement, il n’existe aucune vérification pour savoir si un fragment de contenu existant est référencé. Par conséquent, la suppression d’un fragment de contenu, par exemple, peut entraîner des problèmes sur une page contenant une référence au fragment de contenu en question.
* **Type de données JSON** La sortie de l’API REST de la variable *Type de données JSON* is *sortie basée sur des chaînes*.

## Codes d’état et messages d’erreur {#status-codes-and-error-messages}

Les codes d’état suivants s’affichent dans les circonstances pertinentes :

* **200** (OK)

  Affiché dans le scénario suivant :

   * demande d’un fragment de contenu au moyen de `GET`
   * mise à jour réussie d’un fragment de contenu au moyen de `PUT`

* **201** (Créé)

  Affiché dans le scénario suivant :

   * création réussie d’un fragment de contenu au moyen de `POST`

* **404** (Introuvable)

  Affiché dans le scénario suivant :

   * le fragment de contenu demandé n’existe pas

* **500** (Erreur interne du serveur)

  >[!NOTE]
  >
  >Cette erreur est renvoyée :
  >
  >* lorsqu’une erreur ne pouvant pas être identifiée avec un code spécifique s’est produite ;
  >* lorsque la payload donnée n’était pas valide.

  L’exemple suivant répertorie les scénarios courants lorsque cet état d’erreur est renvoyé, ainsi que le message d’erreur (à espacement fixe) généré :

   * Le dossier parent n’existe pas (lors de la création d’un fragment de contenu au moyen de `POST`)
   * Aucun modèle de fragment de contenu n’est fourni (cq:model est manquant) ou ne peut être lu (en raison d’un chemin d’accès non valide ou d’un problème d’autorisation) ou il n’existe aucun modèle de fragment valide :

      * `No content fragment model specified`
      * `Cannot create a resource of given model '/foo/bar/qux'`

   * Impossible de créer le fragment de contenu (problème d’autorisation potentiel) :

      * `Could not create content fragment`

   * Le titre et/ou la description n’ont pas pu être mis à jour :

      * `Could not set value on content fragment`

   * Impossible de définir les métadonnées :

      * `Could not set metadata on content fragment`

   * Élément de contenu introuvable ou impossible à mettre à jour

      * `Could not update content element`
      * `Could not update fragment data of element`

  Les messages d’erreur détaillés sont renvoyés de la manière suivante :

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

## Référence d’API {#api-reference}

Pour accéder aux références d’API détaillées :

* [API Adobe Experience Manager Assets – Fragments de contenu](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/assets-api-content-fragments/index.html)

* [API HTTP Assets](/help/assets/mac-api-assets.md)

   * [Fonctionnalités disponibles](/help/assets/mac-api-assets.md#available-features)

* La variable [API ouvertes du modèle de fragment de contenu et de fragment de contenu](/help/headless/content-fragment-openapis.md) sont également disponibles.

## Ressources supplémentaires {#additional-resources}

Pour en savoir plus, voir :

* [Documentation de l’API HTTP Assets](/help/assets/mac-api-assets.md)
* [Session AEM Gem : OAuth](https://experienceleague.adobe.com/docs/events/experience-manager-gems-recordings/gems2014/aem-oauth-server-functionality-in-aem.html)
