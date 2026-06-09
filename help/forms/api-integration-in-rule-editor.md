---
title: Intégration de l’API dans l’éditeur de règles pour Forms
description: Découvrez les dernières améliorations apportées au service Invoke dans l’éditeur de règles, notamment comment intégrer des API pour le Forms adaptatif basé sur les composants principaux sans utiliser de modèle de données de formulaire.
feature: Adaptive Forms, Core Components, Edge Delivery Services
role: User, Developer
level: Beginner, Intermediate
keywords: intégration d’API dans l’éditeur de règles, améliorations du service d’appel
badgeSaas: label="AEM Forms" type="Positive" tooltip="S’applique à AEM Forms)."
exl-id: fc51f86d-e672-4513-b473-6700757a0c3d
source-git-commit: 2c4a963786db1b5dabf16c5d96be950bb7ad7807
workflow-type: tm+mt
source-wordcount: '1554'
ht-degree: 2%

---

# Intégration de l’API dans l’éditeur de règles

<span>L’intégration de l’API dans l’éditeur de règles se trouve dans le programme des utilisateurs précoces. Vous pouvez écrire à `aem-forms-ea@adobe.com` depuis votre adresse e-mail officielle pour rejoindre le programme d’accès anticipé et demander l’accès à la fonctionnalité.</span>

>[!NOTE]
>
> L’éditeur visuel de règles prend en charge l’intégration d’API dans le Forms adaptatif en fonction des composants principaux et du Forms [Edge Delivery Services créé dans l’éditeur universel](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md).

L’éditeur visuel de règles d’un Forms adaptatif prend en charge l’intégration directe d’API sans créer de modèle de données de formulaire. Vous pouvez vous connecter à un point d’entrée de l’API en saisissant l’URL de l’API (au format JSON) ou en important la configuration via une commande cURL. Une fois intégrée, l’action **Invoke Service** peut être utilisée pour appeler l’API.

Les champs de formulaire peuvent être mappés directement aux paramètres d’entrée définis dans la configuration de l’API. De même, les paramètres de sortie peuvent être mappés à des champs de formulaire à l’aide de l’option **payload d’événement** pour la réponse d’API correspondante.

En outre, l’éditeur visuel de règles vous permet de définir des gestionnaires **succès** et **échec** lors de l’appel d’un service. Les gestionnaires de succès spécifient les actions à exécuter après un appel API réussi, tandis que les gestionnaires d’échec définissent la manière dont le formulaire doit répondre lorsqu’une erreur se produit.

## Comparaison : méthodes d’intégration d’API

| Aspect | Intégration de l’API avec le modèle de données de formulaire (FDM) | Intégration directe de l’API (via *Créer une intégration d’API*) |
|--------------------------------|---------------------------------------------------------------------|-----------------------------------------------------------|
| **Objectif** | Intégration d’API centralisée et réutilisable dans plusieurs formulaires | Intégration rapide d’API spécifique au formulaire |
| **Emplacement de configuration** | Création et modification dans l’éditeur de modèle de données de formulaire (console AEM) | Créé et modifié directement dans l’éditeur de règles de formulaire adaptatif |
| **Complexité** | Effort de configuration plus élevé (nécessite le mappage et la configuration) | Simple et léger |
| **Le Mieux Adapté À** | Cas d’utilisation d’entreprise ou à grande échelle avec plusieurs formulaires | Petits formulaires, prototypes ou appels d’API uniques |

## Configuration d’intégration d’API

La capture d’écran ci-dessous affiche la fenêtre de configuration de l’intégration API :

![Configuration de l’intégration de l’API](/help/forms/assets/api-integration-configuration.png)

### Principales options de configuration

**Configuration de l’intégration de l’API**

* **Importer depuis cURL** : configurez votre intégration d’API en collant une commande cURL prête à l’emploi au lieu de saisir manuellement des détails tels que l’URL de l’API, la méthode HTTP, les en-têtes et les paramètres.
* **Nom d’affichage** : nom personnalisé du service API.
* **URL de l’API** : point d’entrée du service d’API.
* **Sélectionner la méthode HTTP** : méthode de requête HTTP utilisée pour appeler l’API.
* **Type de contenu** : définit le format de requête et de réponse.
* **Chiffrement requis** : (facultatif) lorsque cette option est sélectionnée, les payloads de requête et de réponse peuvent être chiffrées à l’aide de fonctions personnalisées dans **function.js**. Un champ **Clé publique** s’affiche. Collez votre clé publique dans ce champ avant d’enregistrer la configuration de l’intégration de l’API.
* **Exécuter sur le client** : lorsqu’il est activé, l’appel API est effectué à partir du client (navigateur) plutôt que du serveur.

>[!NOTE]
>
> Pour connaître les étapes et les exemples de fonctions **chiffrer** et **déchiffrer**, voir [ Chiffrement et déchiffrement](#encryption-and-decryption).

**Type d’authentification**

* **Options** : aucune, de base, clé API.

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

>[!VIDEO](https://video.tv.adobe.com/v/3471606/rule-editor-api-integration/?quality=12&learn=on)

**Scénario** : Une agence gouvernementale fournit un formulaire de demande de visa en ligne avec les champs suivants :

1. Nom Complet (Texte)
2. Date de naissance (Date)
3. Pays de nationalité (liste déroulante)
4. Numéro De Passeport (Texte)
5. Pays de délivrance du passeport (liste déroulante)
6. Pays de destination (liste déroulante)
7. Date prévue d’arrivée (date)

Au lieu de conserver une liste statique de pays, le formulaire récupère dynamiquement les informations de pays (continent, capitale, codes ISO Alpha, etc.) à l’aide de l’API **getcounname** :

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

>[!NOTE]
>
> Vous pouvez [récupérer les valeurs de propriété d’un tableau JSON en appelant une API et en utilisant une fonction personnalisée](/help/forms/invoke-service-enhancements-rule-editor.md#retrieve-property-values-from-a-json-array). Cette approche vous permet d’extraire des valeurs et de les lier directement aux champs du formulaire.

## Modifier une intégration d’API existante

Après avoir créé une intégration d’API, vous pouvez la mettre à jour à partir de l’éditeur de règles sans créer de nouvelle intégration. Lorsqu’une instruction **Invoke Service** fait référence à une intégration d’API, une option **Modifier** est disponible pour cette intégration.

Pour modifier une intégration d’API existante :

1. Ouvrez la règle dans l’éditeur de règles qui contient une instruction **Invoke Service**.
2. Dans l’instruction **Invoke Service**, sélectionnez l’intégration d’API à mettre à jour.
3. Cliquez sur l’icône **Modifier** pour ouvrir la fenêtre **Configuration de l’intégration de l’API**.
4. Mettez à jour l’URL d’API, les paramètres d’authentification, d’entrée et de sortie, ou d’autres paramètres, et enregistrez vos modifications.

![Modifier l’intégration d’API](/help/forms/assets/edit-api-rule-editor.png)

## Chiffrement et déchiffrement

Lorsque **Chiffrement requis** est sélectionné pour une intégration d’API, collez votre clé publique dans le champ **Clé publique** de la fenêtre de configuration de l’intégration d’API. L’éditeur de règles appelle **chiffrer** avant chaque requête sortante et **déchiffrer** après une réponse réussie. Si vous n’ajoutez pas de logique personnalisée dans **function.js**, les deux fonctions renvoient la payload inchangée.

Pour chiffrer et déchiffrer les données de requête et de réponse, ajoutez les fonctions **chiffrer** et **déchiffrer** à **function.js** :

1. Ouvrez le fichier **function.js** pour votre formulaire adaptatif.
2. Ajoutez une fonction **encrypt** pour transformer la requête (corps, en-têtes et options associées) avant l&#39;appel API.
3. Ajoutez une fonction **decrypt** pour transformer la réponse après un appel API réussi. La fonction **decrypt** reçoit la réponse chiffrée et **originalRequest**, qui inclut toutes les **cryptoMetadata** définies pendant le chiffrement.
4. Enregistrez **function.js**, puis testez l’intégration à l’aide de **Invoke Service** dans l’éditeur de règles.

L’exemple de code suivant montre comment ajouter la fonction **encrypt** dans **function.js** :

```javascript
function encrypt(payload) {
    const { body, headers, options } = payload;
    const { encryptedBody, encryptedKey } = await myRsaEncrypt(body);
    return {
        body: encryptedBody,
        headers: { ...headers, 'X-Encrypted-Key': encryptedKey },
        cryptoMetadata: { keyId: 'rsa-2048-v1' },
        options
    };
}
```



**chiffrer (hook de payload de pré-requête)**

La fonction **encrypt** reçoit un objet de payload avec **body**, **headers**, **cryptoMetadata** et **options** facultatifs. Elle renvoie une version modifiée de la même forme. Le champ **options** transfère les paramètres de l’API de récupération (par exemple, `credentials: 'include'`) via le pipeline de requêtes. Les valeurs de **options** sont appliquées à l’appel `fetch()` sous-jacent. Le champ **cryptoMetadata** stocke les données à utiliser lors du déchiffrement. Tout ce que vous définissez dans **cryptoMetadata** pendant le chiffrement est conservé dans **originalRequest.cryptoMetadata** et mis à la disposition de la fonction **decrypt** ultérieurement. Malgré son nom, **encrypt** est un transformateur de pré-requête général. Vous pouvez l’utiliser pour modifier les en-têtes ou le corps de la requête, pas seulement pour le chiffrement cryptographique. L’implémentation par défaut renvoie la payload inchangée.
>>

L’exemple de code suivant illustre une fonction **decrypt** :

```javascript
function decrypt(encryptedData, originalRequest) {
    const { keyId } = originalRequest?.cryptoMetadata || {};
    return await myRsaDecrypt(encryptedData, keyId);
}
```

**déchiffrer (hook de réponse de post-requête)**

La fonction **decrypt** s’exécute après une réponse réussie. Il reçoit le corps de la réponse et **originalRequest**. L’objet **originalRequest** comprend **cryptoMetadata** provenant de votre fonction **encrypt**, ainsi que **url**, **method** et d’autres métadonnées de requête. Il doit renvoyer le corps déchiffré de manière synchrone ou asynchrone. L’implémentation par défaut renvoie les données inchangées. La fonction **decrypt** s’exécute uniquement en cas de réponses réussies. Les réponses d’erreur n’appellent pas **déchiffrer**.

>[!NOTE]
>
> Dans les exemples ci-dessus, remplacez `myRsaEncrypt` et `myRsaDecrypt` par vos fonctions de chiffrement.

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

## Questions fréquentes

* **Dois-je créer un modèle de données de formulaire pour intégrer une API dans le Forms adaptatif ?**\
  Non. Avec l’éditeur visuel de règles, vous pouvez directement intégrer des API à l’aide de l’option **Créer une intégration d’API** sans créer de modèle de données de formulaire. Cette approche est idéale pour les cas d’utilisation légers ou spécifiques aux formulaires.

* **Puis-je sécuriser les appels API effectués à partir de l’éditeur de règles ?**\
  Oui. La configuration de l’intégration d’API fournit des options d’authentification telles que **De base** et **Clé API**. Vous pouvez également sélectionner **Chiffrement requis** et ajouter une logique **chiffrer** et **déchiffrer** personnalisée dans **function.js**. Pour obtenir des étapes de configuration et des exemples, voir [Chiffrement et déchiffrement](#encryption-and-decryption).
