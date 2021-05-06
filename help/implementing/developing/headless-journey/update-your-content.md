---
title: Mise à jour de votre contenu via les API AEM Assets
description: Dans cette partie du Parcours de développement AEM sans fil, découvrez comment utiliser l’API REST pour accéder au contenu de vos fragments de contenu et le mettre à jour.
hide: true
hidefromtoc: true
index: false
exl-id: 8d133b78-ca36-4c3b-815d-392d41841b5c
translation-type: tm+mt
source-git-commit: 0c47dec1e96fc3137d17fc3033f05bf1ae278141
workflow-type: tm+mt
source-wordcount: '1657'
ht-degree: 71%

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

## API HTTP Assets {#assets-http-api}

L’[API HTTP AEM Assets](/help/assets/mac-api-assets.md) englobe :

* l’API REST Assets,
* y compris la prise en charge des fragments de contenu

L’implémentation actuelle de l’API HTTP Assets est basée sur le style architectural **REST**.

L’API REST Assets permet aux développeurs de Adobe Experience Manager en tant que Cloud Service d’accéder au contenu (stocké dans AEM) directement via l’API HTTP, via **CRUD** opérations (Créer, Lire, Mettre à jour, Supprimer).

L’API permet d’utiliser Adobe Experience Manager as a Cloud Service en tant que système de gestion de contenu (CMS) sans interface utilisateur en fournissant des services de contenu à une application frontale JavaScript. Ou toute autre application pouvant exécuter des requêtes HTTP et gérer les réponses JSON.

Par exemple, les applications à page unique (SPA), basées sur une structure ou personnalisées, nécessitent du contenu fourni via une API, souvent au format JSON.

Bien que les composants de base AEM fournissent une API très complète, flexible et personnalisable pouvant traiter les opérations de lecture requises à cette fin, et dont la sortie JSON peut être personnalisée, ils ne nécessitent pas de connaissances sur AEM WCM (Web Content Management) pour la mise en œuvre, car ils doivent être hébergés sur des pages reposant sur des modèles AEM dédiés. Les entreprises de développement d’applications sur une seule page n’ont pas toutes accès à ces connaissances.

Dans ce cas, l’API REST Assets peut être utilisée. Elle permet aux développeurs d’accéder à des ressources (par exemple, des images et des fragments de contenu) directement, sans devoir d’abord les intégrer dans une page puis diffuser leur contenu au format JSON sérialisé.

>[!NOTE]
>
>Il est impossible de personnaliser la sortie JSON de l’API REST Assets.

L’API REST Assets permet également aux développeurs de modifier du contenu, en créant, en mettant à jour ou en supprimant des ressources, des fragments de contenu et des dossiers.

L’API REST Assets :

* suit le principe HATEOAS
* met en œuvre le format SIREN

## Conditions préalables {#prerequisites}

L’API REST Assets est disponible pour chaque installation prête à l’emploi d’une version récente d’Adobe Experience Manager as a Cloud Service.

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
   <td><p>Optimisé pour une utilisation dans une application sur une seule page (SPA) ou tout autre contexte (utilisant du contenu).</p> <p>Peut également contenir des informations de disposition.</p> </td>
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
   <td><p>L’accès en écriture résout généralement une instance d’auteur.</p> <p>Un accès en lecture peut également être redirigé vers une instance de publication.</p> </td>
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
>* CORS/AEM expliqué
>* Vidéo - Développement pour CORS et AEM

>



Il est recommandé d’utiliser OAuth dans les environnements ayant des exigences d’authentification spécifiques.

## Fonctionnalités disponibles {#available-features}

Les fragments de contenu sont un type spécifique de ressource ; voir Utilisation des fragments de contenu.

Pour plus d’informations sur les fonctions disponibles dans l’API, voir :

* L’API REST Assets
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

Pour plus d’informations sur l’utilisation de l’API REST d’AEM Assets, vous pouvez vous reporter à :

* API HTTP des ressources Adobe Experience Manager
* Prise en charge des fragments de contenu dans l’API HTTP AEM Assets 

## Eléments suivants {#whats-next}

Maintenant que vous avez terminé cette partie du Parcours de développement AEM sans tête, vous devez :

* Comprenez l’API HTTP AEM Assets.
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

