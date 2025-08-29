---
title: Intégration de l’API dans l’éditeur de règles pour Forms
description: Découvrez les dernières améliorations apportées au service Invoke dans l’éditeur de règles, notamment comment intégrer des API pour le Forms adaptatif basé sur les composants principaux sans utiliser de modèle de données de formulaire.
feature: Adaptive Forms, Core Components, Edge Delivery Services
role: User, Developer
level: Beginner, Intermediate
keywords: intégration de l’API dans l’éditeur de règles, appeler les améliorations du service
source-git-commit: 5d25204516cb46334c4d594c16852b033f3e6c90
workflow-type: tm+mt
source-wordcount: '1017'
ht-degree: 0%

---


# Intégration de l’API dans l’éditeur de règles

<span>L’intégration de l’API dans l’éditeur de règles se trouve dans le programme des utilisateurs précoces. Vous pouvez écrire à `aem-forms-ea@adobe.com` à partir de votre ID d’e-mail officiel pour rejoindre le programme des utilisateurs et utilisatrices précoces et demander l’accès à la fonctionnalité.</span>

L’éditeur visuel de règles d’un Forms adaptatif prend en charge l’intégration directe d’API sans créer de modèle de données de formulaire. Vous pouvez vous connecter à un point d’entrée de l’API en saisissant l’URL de l’API (au format JSON) ou en important la configuration via une commande cURL. Une fois intégrée, l’action **Invoke Service** peut être utilisée pour appeler l’API.

Les champs de formulaire peuvent être mappés directement aux paramètres d’entrée définis dans la configuration de l’API. De même, les paramètres de sortie peuvent être mappés à des champs de formulaire à l’aide de l’option **payload d’événement** pour la réponse d’API correspondante.

En outre, l’éditeur visuel de règles vous permet de définir des gestionnaires **succès** et **échec** lors de l’appel d’un service. Les gestionnaires de succès spécifient les actions à exécuter après un appel API réussi, tandis que les gestionnaires d’échec définissent la manière dont le formulaire doit répondre lorsqu’une erreur se produit.

>[!NOTE]
>
> L’intégration de l’API dans l’éditeur de règles s’applique également à Edge Delivery Services Forms.

## Comparaison : méthodes d’intégration d’API

| Aspect | Intégration de l’API avec le modèle de données de formulaire (FDM) | Intégration directe de l’API (via *Créer une intégration d’API*) |
|--------------------------------|---------------------------------------------------------------------|-----------------------------------------------------------|
| **Objectif** | Intégration d’API centralisée et réutilisable dans plusieurs formulaires | Intégration rapide d’API spécifique au formulaire |
| **Emplacement de configuration** | Création et modification dans l’éditeur de modèle de données de formulaire (console AEM) | Créé et modifié directement dans l’éditeur de règles de formulaire adaptatif |
| **Complexité** | Effort de configuration plus élevé (nécessite le mappage et la configuration) | Simple et léger |
| **Le Mieux Adapté À** | Cas d’utilisation d’entreprise ou à grande échelle avec plusieurs formulaires | Petits formulaires, prototypes ou appels d’API uniques |

## Configuration de l’intégration de l’API

La capture d’écran ci-dessous affiche la fenêtre de configuration de l’intégration API :

![Configuration de l’intégration de l’API](/help/forms/assets/api-integration-configuration.png)

### Principales options de configuration

**Configuration de l’intégration de l’API**

* **Importer depuis cURL** : configurez votre intégration d’API en collant une commande cURL prête à l’emploi au lieu de saisir manuellement des détails tels que l’URL de l’API, la méthode HTTP, les en-têtes et les paramètres.
* **Nom d’affichage** : nom personnalisé du service API.
* **URL de l’API** : point d’entrée du service d’API.
* **Sélectionner la méthode HTTP** : méthode de requête HTTP utilisée pour appeler l’API.
* **Type de contenu** : définit le format de requête et de réponse.
* **Chiffrement requis** : (facultatif) garantit le chiffrement des données sensibles pendant la transmission.
* **Exécuter sur le client** : lorsqu’il est activé, l’appel API est effectué à partir du client (navigateur) plutôt que du serveur.

**Type d’authentification**

* **Options** : aucune, de base, clé API, OAuth 2.0.

**Paramètres d’entrée**

* **Charger le fichier JSON pour l’entrée** : chargez un exemple de fichier JSON pour renseigner automatiquement les mappages d’entrée.
   * **Name** : nom du paramètre d’entrée requis par l’API.
   * **Type** : type de données de l’entrée (chaîne, nombre, valeur booléenne, etc.).
   * **In** : emplacement du paramètre (requête, en-tête ou corps).
   * **Valeur par défaut** : valeur préremplie si elle n’est pas fournie par l’utilisateur.
   * **Ajouter** : option permettant d’ajouter des paramètres d’entrée supplémentaires.

**Paramètres de sortie**

* **Charger JSON pour Output** : chargez un exemple de réponse d’API pour générer automatiquement des mappages.
   * **Name** : nom du paramètre de sortie de la réponse de l’API.
   * **Type** : type de données attendu du paramètre de sortie (chaîne, nombre, etc.).
   * **In** : définit l’endroit où la valeur mappée est attendue.
   * **Ajouter/Supprimer** : ajoutez de nouveaux mappages ou supprimez des mappages existants.

## Cas pratique : remplir les champs Pays dans un formulaire de demande de visa

**Scénario** : Une agence gouvernementale fournit un formulaire de demande de visa en ligne avec les champs suivants :

1. Nom Complet (Texte)
2. Date de naissance (Date)
3. Pays de nationalité (liste déroulante)
4. Numéro De Passeport (Texte)
5. Pays de délivrance du passeport (liste déroulante)
6. Pays de destination (liste déroulante)
7. Date prévue d’arrivée (date)

Au lieu de conserver une liste statique de pays, le formulaire récupère dynamiquement les informations de pays (continent, capitale, codes ISO Alpha, etc.) à l’aide de l’API **getcountryname** :

`https://secure.geonames.org/countryInfoJSON?username=aemforms`

Cela garantit que les candidats voient toujours une liste actualisée et précise des pays tout en remplissant le formulaire.

### Implémentation à l’aide de l’intégration d’API dans l’éditeur de règles

Vous pouvez intégrer une API sans créer de modèle de données de formulaire en cliquant sur le bouton **Créer une intégration d’API** dans l’éditeur de règles.

![Créer une intégration API](/help/forms/assets/create-api-integration.png)

Un service d’API nommé **getcontendname** est configuré sous **Configuration de l’intégration de l’API** dans l’éditeur de règles :

![ Configuration du point d’entrée REST de l’API ](/help/forms/assets/api-restendpoint.png)

* **URL du point d’entrée de l’API** → `https://secure.geonames.org/countryInfoJSON?username=aemforms`
* **Méthode HTTP** → GET
* **Type de contenu** → JSON
* **Input** → `username` transmis en tant que paramètre de requête (`aemforms`).
* **Output** → les champs de réponse tels que `continent`, `capital`, `countrynames`, `isoAlpha3` et `languages` sont mappés aux champs de formulaire.

Dans le **Formulaire de demande de visa**, les trois champs déroulants **Pays de citoyenneté**, **Pays de délivrance du passeport** et **Pays de destination** sont liés à l’action **Invoquer le service**.

Lorsque le formulaire se charge, la fonction **Invoquer le service** récupère la liste des pays à partir de l’API. La réponse est ensuite mappée pour renseigner automatiquement les options de liste déroulante.

Par exemple, lorsque l’utilisateur ouvre **Pays de citoyenneté**, la liste des pays s’affiche de manière dynamique à partir de la réponse de l’API.

![invoke-service-api-integration](/help/forms/assets/invoke-service-api-integration.png)

![Sortie d’intégration d’API](/help/forms/assets/api-integration-output.png)

De même, les **Pays d’émission du passeport** et **Pays de destination** utilisent le même appel API, ce qui garantit des données cohérentes et à jour dans les trois champs.

## Mise en œuvre du mécanisme de reprise en cas d’échec de l’API

Lorsqu’une requête d’API échoue, il est souvent utile de relancer la requête avant de signaler une erreur à l’utilisateur. Vous pouvez implémenter un mécanisme d’interrogation et de reprise en écrivant du code personnalisé dans le fichier **function.js**.

L’exemple suivant montre comment gérer les échecs d’API avec jusqu’à deux tentatives de reprise et un retour exponentiel entre les reprises :

```javascript
/**
 * Handles request retries with up to 2 retry attempts
 * @param {function} requestFn - The request function to execute
 * @return {Promise} A promise that resolves with the response or rejects after all retries
 */
function retryHandler(requestFn) {
    const MAX_RETRIES = 2;
    
    /**
     * Attempts the request with retry metadata
     * @param {number} retryCount - Current retry attempt count
     * @return {Promise} The request promise
     */
    function attemptRequest(retryCount = 0) {
        // Include retry metadata if this is a retry
        const requestOptions = retryCount > 0 ? {
            headers: {
                'X-Retry': 'true',
                'X-Retry-Count': retryCount.toString(),
                'X-Retry-Time': new Date().toISOString()
            },
            body: {
                retry: true,
                retryCount: retryCount,
                timestamp: Date.now()
            }
        } : undefined;

        return requestFn(requestOptions)
            .then(function(response) {
                if (response && response.status >= 400) {
                    console.warn('Request failed with status ' + response.status);
                    throw new Error('Request failed with status ' + response.status);
                }
                return response;
            })
            .catch(function(error) {
                console.warn('Request attempt ' + (retryCount + 1) + ' failed:', error.message);
                
                // Retry if max attempts not reached
                if (retryCount < MAX_RETRIES) {
                    console.log('Retrying request, attempt ' + (retryCount + 2) + ' of ' + (MAX_RETRIES + 1));
                    
                    // Exponential backoff delay: 1s, 2s, 4s...
                    const delay = Math.pow(2, retryCount) * 1000;
                    
                    return new Promise(function(resolve) {
                        setTimeout(resolve, delay);
                    }).then(function() {
                        return attemptRequest(retryCount + 1);
                    });
                } else {
                    // All retries exhausted
                    console.error('All retry attempts failed. Final error:', error.message);
                    throw new Error('Request failed after ' + (MAX_RETRIES + 1) + ' attempts: ' + error.message);
                }
            });
    }
    
    // Start the first attempt
    return attemptRequest(0);
}
```

Dans le code ci-dessus, la fonction **retryHandler** gère les requêtes d’API avec des reprises automatiques en cas d’échec. Il prend une fonction de requête (requestFn) et tente de soumettre la requête jusqu’à deux fois, en ajoutant des métadonnées pour chaque nouvelle tentative.

>[!NOTE]
>
> Pour obtenir des instructions détaillées sur l’ajout de fonctions personnalisées, reportez-vous à l’article [Présentation des fonctions personnalisées pour le Forms adaptatif basé sur les composants principaux](/help/forms/create-and-use-custom-functions.md).

## Questions fréquentes

* **Dois-je créer un modèle de données de formulaire pour intégrer une API dans le Forms adaptatif ?**\
  Non. Avec l’éditeur visuel de règles, vous pouvez directement intégrer des API à l’aide de l’option **Créer une intégration d’API** sans créer de modèle de données de formulaire. Cette approche est idéale pour les cas d’utilisation légers ou spécifiques aux formulaires.

* **Puis-je sécuriser les appels API effectués à partir de l’éditeur de règles ?**\
  Oui. La configuration de l’intégration d’API fournit des options d’authentification telles que **De base, Clé API et OAuth 2.0**. Vous pouvez également activer **Chiffrement requis** pour vous assurer que les données sensibles sont transmises en toute sécurité.