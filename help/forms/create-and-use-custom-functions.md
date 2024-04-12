---
title: Création et ajout de fonctions personnalisées dans un formulaire adaptatif
description: AEM Forms prend en charge les fonctions personnalisées qui permettent aux utilisateurs de créer et d’utiliser leurs propres fonctions dans l’éditeur de règles.
keywords: Ajoutez une fonction personnalisée, utilisez une fonction personnalisée, créez une fonction personnalisée, utilisez une fonction personnalisée dans l’éditeur de règles.
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Core Components
exl-id: 24607dd1-2d65-480b-a831-9071e20c473d
source-git-commit: e71e247f5b6de806b36c5c759b29e7273511f94e
workflow-type: tm+mt
source-wordcount: '3108'
ht-degree: 3%

---


<span class="preview"> Cet article contient du contenu pour certaines fonctionnalités de version anticipée. Ces fonctions de préversion sont accessibles uniquement via notre [canal de version préliminaire](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features). Les fonctionnalités du programme de version préliminaire sont les suivantes :
* Prise en charge facultative des paramètres dans les fonctions personnalisées
* Fonction de mise en cache des fonctions personnalisées
* Les objets de champ et d’objet de portée globale prennent en charge les fonctions personnalisées
* Prise en charge des fonctionnalités JavaScript modernes telles que les fonctions de flèche et de gauche (prise en charge d’ES10).
Assurez-vous que la variable [Le composant principal est défini sur la version 3.0.8](https://github.com/adobe/aem-core-forms-components) pour utiliser des fonctions de préversion dans une fonction personnalisée. </span>

# Fonctions personnalisées dans le Forms adaptatif (composants principaux)

## Présentation

AEM Forms prend en charge les fonctions personnalisées, ce qui permet aux utilisateurs de définir des fonctions JavaScript pour l’implémentation de règles métier complexes. Ces fonctions personnalisées étendent les capacités des formulaires en facilitant la manipulation et le traitement des données saisies pour répondre aux exigences spécifiées. Ils permettent également une modification dynamique du comportement du formulaire en fonction de critères prédéfinis.

### Utilisation de fonctions personnalisées {#uses-of-custom-function}

Les avantages des fonctions personnalisées dans les Forms adaptatives sont les suivants :

* **Traitement des données**: les fonctions personnalisées aident à traiter les données saisies dans les champs de formulaires.
* **Validation des données**: les fonctions personnalisées vous permettent d’effectuer des vérifications personnalisées sur les entrées de formulaire et de fournir des messages d’erreur spécifiés.
* **Comportement dynamique**: les fonctions personnalisées vous permettent de contrôler le comportement dynamique de vos formulaires en fonction de conditions spécifiques. Vous pouvez, par exemple, afficher/masquer des champs, modifier les valeurs de champ ou ajuster dynamiquement la logique du formulaire.
* **Intégration**: vous pouvez utiliser des fonctions personnalisées pour l’intégration à des API ou services externes. Il permet de récupérer des données provenant de sources externes, d’envoyer des données à des points de terminaison Rest externes ou d’effectuer des actions personnalisées basées sur des événements externes.

Les fonctions personnalisées sont essentiellement des bibliothèques clientes ajoutées dans le fichier JavaScript. Une fois que vous avez créé une fonction personnalisée, elle est disponible dans l’éditeur de règles pour sélection par l’utilisateur dans un formulaire adaptatif. Les fonctions personnalisées sont identifiées par les annotations JavaScript dans l’éditeur de règles.

### Annotations JavaScript prises en charge pour une fonction personnalisée {#js-annotations}

Les annotations JavaScript sont utilisées pour fournir des métadonnées pour le code JavaScript. Il comprend des commentaires commençant par des symboles spécifiques, par exemple /** et @. Les annotations fournissent des informations importantes sur les fonctions, variables et autres éléments du code. Le formulaire adaptatif prend en charge les annotations JavaScript suivantes pour les fonctions personnalisées :

#### Nom

Le nom est utilisé pour identifier la fonction personnalisée dans l’éditeur de règles d’un formulaire adaptatif. Les syntaxes suivantes sont utilisées pour nommer une fonction personnalisée :

* `@name [functionName] <Function Name>`
* `@function [functionName] <Function Name>`
* `@func [functionName] <Function Name>`.
  `functionName` est le nom de la fonction. Les espaces ne sont pas autorisés.
  `<Function Name>` est le nom d’affichage de la fonction dans l’éditeur de règles d’un formulaire adaptatif.
Si le nom de la fonction est identique à celui de la fonction elle-même, vous pouvez l’omettre. `[functionName]` de la syntaxe . <!-- For example,  in the `calculateAge` custom function, the name is defined as:
`* @name calculateAge` -->

#### Paramètre

Le paramètre est une liste d’arguments utilisés par les fonctions personnalisées. Une fonction peut prendre en charge plusieurs paramètres. Les syntaxes suivantes sont utilisées pour définir un paramètre dans une fonction personnalisée :

* `@param {type} name <Parameter Description>`
* `@argument` `{type} name <Parameter Description>`
* `@arg` `{type}` `name <Parameter Description>`.
  `{type}` représente le type de paramètre.  Les types de paramètres autorisés sont les suivants :
   * string : représente une seule valeur de chaîne.
   * number : représente une seule valeur numérique.
   * boolean : représente une seule valeur booléenne (true ou false).
   * string[]: représente un tableau de valeurs de chaîne.
   * nombre[]: représente un tableau de valeurs numériques.
   * boolean[]: représente un tableau de valeurs booléennes.
   * date : représente une seule valeur de date.
   * date[]: représente un tableau de valeurs de date.
   * array : représente un tableau générique contenant des valeurs de différents types.
   * object : représente l’objet de formulaire transmis à une fonction personnalisée au lieu de transmettre directement sa valeur.
   * scope : représente l’objet global utilisé par les fonctions personnalisées au moment de l’exécution. Il est déclaré comme dernier paramètre dans les annotations JavaScript et n’est pas visible dans l’éditeur de règles d’un formulaire adaptatif. Le paramètre scope accède à l’objet du formulaire ou du composant pour déclencher la règle ou l’événement requis pour le traitement du formulaire.

    Le type de paramètre n’est pas sensible à la casse et les espaces ne sont pas autorisés dans le nom du paramètre.
    
    `&lt;parameter description=&quot;&quot;>` contient des détails sur l’objet du paramètre. Il peut avoir plusieurs mots.
    
    Par défaut, tous les paramètres sont obligatoires. Vous pouvez définir un paramètre comme facultatif en ajoutant `=` après le type de paramètre ou en encadrant le nom du paramètre dans `[]`. Les paramètres définis comme facultatifs dans les annotations JavaScript sont affichés comme facultatifs dans l’éditeur de règles.
    Pour définir une variable comme paramètre facultatif, vous pouvez utiliser l’une des syntaxes suivantes :
    
    * `@param {type=} Input1`
    
    Dans la ligne de code ci-dessus, &quot;Input1&quot; est un paramètre facultatif sans valeur par défaut. Pour déclarer un paramètre facultatif avec la valeur par défaut :
    `@param {string=&lt;value>} input1`
    
    `input1` comme paramètre facultatif avec la valeur par défaut définie sur `value`.
    
    * `@param {type} [Input1]`
    
    Dans la ligne de code ci-dessus, &quot;Input1&quot; est un paramètre facultatif sans valeur par défaut. Pour déclarer un paramètre facultatif avec la valeur par défaut :
    `@param {array} [input1=&lt;value>]
    `input1` est un paramètre facultatif de type tableau avec la valeur par défaut définie sur `value`.
    Assurez-vous que le type de paramètre est entre accolades. {} et le nom du paramètre est entre crochets [].
    
    Examinez le fragment de code suivant, où input2 est défini comme paramètre facultatif :
    
    &quot;javascript
    
    /**
    * fonction de paramètre facultative
    * @name OptionalParameterFunction
    * @param {string} input1
    * @param {string=} input2
    * @return {string}
    */
    function OptionalParameterFunction(input1, input2) {
    let result = &quot;Result: &quot;;
    result += input1;
    if (input2)== null) {
    result += &quot; + input2;
    }
    le résultat du retour;
    }
    &quot;
    
    L’illustration suivante s’affiche à l’aide de la fonction personnalisée &quot;OptionalParameterFunction&quot; dans l’éditeur de règles :
    
    &lt;!>— ![Paramètres facultatifs ou obligatoires ](/help/forms/assets/optional-default-params.png) —>
    
    Vous pouvez enregistrer la règle sans spécifier de valeur pour les paramètres requis, mais la règle n’est pas exécutée et affiche un message d’avertissement :
    
    &lt;!>— ![avertissement de règle incomplète](/help/forms/assets/incomplete-rule.png) —>
    
    Lorsque l’utilisateur laisse le paramètre facultatif vide, la valeur &quot;Non défini&quot; est transmise à la fonction personnalisée pour le paramètre facultatif.

#### Type de retour

Le type de retour spécifie le type de valeur que la fonction personnalisée renvoie après l’exécution. Les syntaxes suivantes sont utilisées pour définir un type de retour dans une fonction personnalisée :

* `@return {type}`
* `@returns {type}`
  `{type}` représente le type de retour de la fonction. Les types de retour autorisés sont les suivants :
   * string : représente une seule valeur de chaîne.
   * number : représente une seule valeur numérique.
   * boolean : représente une seule valeur booléenne (true ou false).
   * string[]: représente un tableau de valeurs de chaîne.
   * nombre[]: représente un tableau de valeurs numériques.
   * boolean[]: représente un tableau de valeurs booléennes.
   * date : représente une seule valeur de date.
   * date[]: représente un tableau de valeurs de date.
   * array : représente un tableau générique contenant des valeurs de différents types.
   * object : représente l’objet de formulaire au lieu de sa valeur directement.

  Le type de retour n’est pas sensible à la casse.

#### Privée

La fonction personnalisée, déclarée comme privée, n’apparaît pas dans la liste des fonctions personnalisées de l’éditeur de règles d’un formulaire adaptatif. Par défaut, les fonctions personnalisées sont publiques. La syntaxe permettant de déclarer une fonction personnalisée comme étant privée est `@private`.

Pour en savoir plus sur la définition de paramètres facultatifs dans JSDocs, [cliquez ici](https://jsdoc.app/tags-param).

## Instructions relatives à la création de fonctions personnalisées {#considerations}

Pour répertorier les fonctions personnalisées dans l’éditeur de règles, vous pouvez utiliser l’un des formats suivants :

* **Instruction de fonction avec ou sans commentaires jsdoc**

Vous pouvez créer une fonction personnalisée avec ou sans commentaires jsdoc.

```javascript
    function functionName(parameters) 
        {
            // code to be executed
        }
```
Si l’utilisateur n’ajoute aucune annotation JavaScript à la fonction personnalisée, elle est répertoriée dans l’éditeur de règles par son nom de fonction. Toutefois, il est recommandé d’inclure des annotations JavaScript pour améliorer la lisibilité des fonctions personnalisées.

* **Fonction de flèche avec annotations JavaScript ou commentaire obligatoires**

Vous pouvez créer une fonction personnalisée à l’aide d’une syntaxe de fonction de flèche :

```javascript
    /**
    * test function
    * @name testFunction 
    * @param {string} a parameter description
    * @param {string=} b parameter description
    * @return {string}
    */
    testFunction = (a, b) => {
    return a + b;
    };
    /** */
    testFunction1=(a) => (return a)
    /** */
    testFunction2 = a => a + 100;
    
```

* **Expression de fonction avec annotations ou commentaire JavaScript obligatoires**

Pour répertorier les fonctions personnalisées dans l’éditeur de règles d’un formulaire adaptatif, créez des fonctions personnalisées au format suivant :

```javascript
    /**
    * test function
    * @name testFunction 
    * @param {string} input1 parameter description
    * @param {string=} input2 parameter description
    * @return {string}
    */
    testFunction = function(input1,input2)
        {
            // code to be executed
        }
```

## Création d’une fonction personnalisée {#create-custom-function}

Créez une bibliothèque cliente pour appeler des fonctions personnalisées dans l’éditeur de règles. Pour plus d’informations, voir [Utilisation des bibliothèques côté client](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html?lang=fr#developing).

Les étapes de création de fonctions personnalisées sont les suivantes :
1. [Créez une bibliothèque cliente.](#create-client-library)
1. [Ajout d’une bibliothèque cliente à un formulaire adaptatif](#use-custom-function)

### Créez une bibliothèque cliente. {#create-client-library}

Vous pouvez ajouter des fonctions personnalisées en ajoutant la bibliothèque cliente. Pour créer une bibliothèque cliente, procédez comme suit :

1. [Clonage de votre référentiel as a Cloud Service AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#accessing-git).
1. Créez un dossier sous le dossier `[AEM Forms as a Cloud Service repository folder]/apps/`. Par exemple, créez un dossier nommé `experience-league`.
1. Accédez à `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/experience-league/` et créez un `ClientLibraryFolder`. Par exemple, créez un dossier de bibliothèque cliente en tant que `customclientlibs`.
1. Ajout d’une propriété `categories` avec une valeur de type chaîne. Par exemple, affectez la valeur `customfunctionscategory` à la fonction `categories` pour la propriété `customclientlibs` dossier.

   >[!NOTE]
   >
   > Vous pouvez choisir n’importe quel nom pour `client library folder` et `categories` .

1. Créez un dossier nommé `js`.
1. Accédez au dossier `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/customclientlibs/js`.
1. Ajoutez un fichier JavaScript, par exemple : `function.js`. Le fichier comprend le code de la fonction personnalisée.
1. Enregistrez le fichier `function.js`.
1. Accédez au dossier `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/customclientlibs/js`.
1. Ajoutez un fichier texte en tant que `js.txt`. Le fichier contient :

   ```javascript
       #base=js
       functions.js
   ```

1. Enregistrez le fichier `js.txt`.
1. Ajoutez, validez et envoyez les modifications dans le référentiel à l’aide des commandes ci-dessous :

   ```javascript
       git add .
       git commit -a -m "Adding custom functions"
       git push
   ```

1. [Exécution du pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#setup-pipeline) pour déployer la fonction personnalisée.

Une fois le pipeline exécuté correctement, la fonction personnalisée ajoutée à la bibliothèque cliente devient disponible dans votre [Éditeur de règles de formulaire adaptatif](/help/forms/rule-editor-core-components.md).

### Ajout d’une bibliothèque cliente à un formulaire adaptatif{#use-custom-function}

Une fois que vous avez déployé votre bibliothèque cliente dans votre environnement Forms CS, utilisez ses fonctionnalités dans votre formulaire adaptatif. Pour ajouter la bibliothèque cliente dans votre formulaire adaptatif

1. Ouvrez votre formulaire en mode d’édition. Pour ouvrir un formulaire en mode d’édition, sélectionnez-le, puis **[!UICONTROL Modifier]**.
1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La fenêtre du conteneur de formulaires adaptatifs s’ouvre.
1. Ouvrez le **[!UICONTROL De base]** et sélectionnez le nom du **[!UICONTROL catégorie de bibliothèque cliente]** dans la liste déroulante (dans ce cas, sélectionnez `customfunctionscategory`).

   ![Ajout de la bibliothèque cliente de fonction personnalisée](/help/forms/assets/clientlib-custom-function.png)

   >[!NOTE]
   >
   > Plusieurs catégories peuvent être ajoutées en spécifiant une liste séparée par des virgules dans la variable **[!UICONTROL Catégorie de bibliothèque cliente]** champ .

1. Cliquez sur **[!UICONTROL Terminé]**.

Vous pouvez utiliser la fonction personnalisée dans la variable [éditeur de règles d’un formulaire adaptatif](/help/forms/rule-editor-core-components.md) en utilisant la variable [Annotations JavaScript](##js-annotations).

## Utilisation d’une fonction personnalisée dans un formulaire adaptatif

Dans un formulaire adaptatif, vous pouvez utiliser [fonctions personnalisées dans l’éditeur de règles](/help/forms/rule-editor-core-components.md). Ajoutons le code suivant au fichier JavaScript (`Function.js` ) pour calculer l’âge en fonction de la date de naissance (AAAA-MM-JJ). Création d’une fonction personnalisée en tant que `calculateAge()` qui prend la date de naissance comme entrée et renvoie l’âge :

```javascript
    /**
        * Calculates Age
        * @name calculateAge
        * @param {object} field
        * @return {string} 
    */

    function calculateAge(field) {
    var dob = new Date(field);
    var now = new Date();

    var age = now.getFullYear() - dob.getFullYear();
    var monthDiff = now.getMonth() - dob.getMonth();

    if (monthDiff < 0 || (monthDiff === 0 && now.getDate() < dob.getDate())) {
    age--;
    }

    return age;
    }
```

Dans l’exemple ci-dessus, lorsque l’utilisateur saisit la date de naissance au format (AAAA-MM-JJ), la fonction personnalisée `calculateAge` est appelée et renvoie l’âge.

![Calculez la fonction personnalisée Age dans l’éditeur de règles](/help/forms/assets/custom-function-calculate-age.png)

Prévisualisons le formulaire pour observer comment les fonctions personnalisées sont implémentées par le biais de l’éditeur de règles :

![Fonction personnalisée Calcul de l’âge dans l’aperçu de formulaire de l’éditeur de règles](/help/forms/assets/custom-function-age-calculate-form.png)

>[!NOTE]
>
> Vous pouvez vous référer aux [fonction personnalisée](/help/forms/assets//customfunctions.zip) dossier. Téléchargez et installez ce dossier dans votre instance AEM à l’aide du [Gestionnaire de modules](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager).

### Prise en charge des fonctions asynchrones dans les fonctions personnalisées {#support-of-async-functions}

Les fonctions personnalisées asynchrones n’apparaissent pas dans la liste de l’éditeur de règles. Cependant, il est possible d’appeler des fonctions asynchrones dans des fonctions personnalisées créées à l’aide d’expressions de fonction synchrones.

![Fonction personnalisée Sync et asynchrone](/help/forms/assets/workflow-for-sync-async-custom-fumction.png)

>[!NOTE]
>
> L’avantage de l’appel de fonctions asynchrones dans les fonctions personnalisées est que les fonctions asynchrones permettent l’exécution simultanée de plusieurs tâches, avec le résultat de chaque fonction utilisée dans les fonctions personnalisées.

Consultez le code ci-dessous pour découvrir comment nous pouvons appeler des fonctions asynchrones à l’aide de fonctions personnalisées :

```javascript
    
    async function asyncFunction() {
    const response = await fetch('https://petstore.swagger.io/v2/store/inventory');
    const data = await response.json();
    return data;
    }

    /**
    * callAsyncFunction
    * @name callAsyncFunction callAsyncFunction
    */
    function callAsyncFunction() {
    asyncFunction()
        .then(responseData => {
        console.log('Response data:', responseData);
        })
        .catch(error => {
         console.error('Error:', error);
    });
}
```

Dans l’exemple ci-dessus, la fonction asyncFunction est une `asynchronous function`. Il effectue une opération asynchrone en effectuant une `GET` demande à `https://petstore.swagger.io/v2/store/inventory`. Il attend la réponse en utilisant `await`, analyse le corps de la réponse au format JSON à l’aide de la variable `response.json()`, puis renvoie les données. La variable `callAsyncFunction` est une fonction personnalisée synchrone qui appelle la fonction `asyncFunction` et affiche les données de réponse dans la console. Bien que la variable `callAsyncFunction` est synchrone, elle appelle la fonction asynchroneFunction asynchrone et gère son résultat avec `then` et `catch` des instructions.

Pour en voir le fonctionnement, nous allons ajouter un bouton et créer une règle pour le bouton qui appelle la fonction asynchrone lors d’un clic sur un bouton.

![création d’une règle pour la fonction asynchrone](/help/forms/assets/rule-for-async-funct.png)

Reportez-vous à l’illustration de la fenêtre de console ci-dessous pour démontrer que lorsque l’utilisateur clique sur la variable `Fetch` bouton, fonction personnalisée `callAsyncFunction` est appelé, ce qui appelle à son tour une fonction asynchrone. `asyncFunction`. Inspect dans la fenêtre de la console pour afficher la réponse lorsque vous cliquez sur le bouton :

![Fenêtre de la console](/help/forms/assets/async-custom-funct-console.png)

Explorons les fonctionnalités des fonctions personnalisées.

## Diverses fonctionnalités des fonctions personnalisées

Vous pouvez utiliser des fonctions personnalisées pour ajouter des fonctions personnalisées aux formulaires. Ces fonctions prennent en charge diverses fonctionnalités, telles que l’utilisation de champs spécifiques, l’utilisation de champs globaux ou la mise en cache. Cette flexibilité vous permet de personnaliser les formulaires en fonction des besoins de votre entreprise.

### Objets de champ et de portée globale dans les fonctions personnalisées {#support-field-and-global-objects}

Les objets de champ font référence aux composants ou éléments individuels d’un formulaire, tels que les champs de texte et les cases à cocher. Les objets de portée globale se rapportent aux variables globales ou aux paramètres accessibles dans tout le formulaire. Examinons le fragment de code suivant :

```JavaScript
    /**
    * updateDateTime
    * @name updateDateTime
    * @param {object} field
    * @param {scope} globals 
    */
    function updateDateTime(field, globals) {
    // Accessing the Date object from the global scope
    var currentDate = new Date();
    // Formatting the date and time
    var formattedDateTime = currentDate.toLocaleString();
    // Updating the field value with the formatted date and time
    field.value = formattedDateTime;
    }
```

>[!NOTE]
>
> La variable `param {scope} globals` doit être le dernier paramètre et il ne s’affiche pas dans l’éditeur de règles d’un formulaire adaptatif.

Dans le fragment de code ci-dessus, une fonction personnalisée nommée `updateDateTime` prend des paramètres tels qu’un objet de champ et un objet global. Les objets date et heure sont accessibles à l’aide de la portée globale. Le champ représente l’objet textbox dans lequel les valeurs de date et d’heure formatées sont affichées dans le formulaire.

Découvrez comment les fonctions personnalisées utilisent les objets champ et global à l’aide d’un `Contact Us` formulaire utilisant des cas d’utilisation différents.

![Formulaire de contact](/help/forms/assets/contact-us-form.png)

#### **Cas d’utilisation**: affichez un panneau à l’aide de la fonction `SetProperty` règle

Ajoutez le code suivant dans la fonction personnalisée, comme expliqué dans la section [create-custom-function](#create-custom-function) pour définir le champ de formulaire comme `Required`.

```javascript
    
    /**
    * enablePanel
    * @name enablePanel
    * @param {object} field1
    * @param {object} field2
    * @param {scope} globals 
    */

    function enablePanel(field1,field2, globals)
    {
       if(globals.functions.validate(field1).length === 0)
       {
       globals.functions.setProperty(field2, {visible: true});
       }
    }
```

>[!NOTE]
>
> Vous pouvez configurer les propriétés de champ à l’aide des propriétés disponibles dans `[form-path]/jcr:content/guideContainer.model.json`.

Dans cet exemple, la validation de la variable `personaldetails` s’affiche lorsque vous cliquez sur le bouton. Si aucune erreur n’est détectée dans le panneau, un autre panneau, la variable `feedback` devient visible lorsque vous cliquez sur le bouton.

Créons une règle pour le `Next` , qui valide la variable `personaldetails` et crée la variable `feedback`  visible lorsque l’utilisateur clique sur le panneau `Next` bouton .

![Définir la propriété](/help/forms/assets/custom-function-set-property.png)

Reportez-vous à l’illustration ci-dessous pour démontrer où la variable `personaldetails` est validé lorsque vous cliquez sur le bouton `Next` bouton . Dans le cas contraire, tous les champs de la variable `personaldetails` sont validées, la variable `feedback` devient visible.

![Définir l’aperçu du formulaire de propriété](/help/forms/assets/set-property-form-preview.png)

Si des erreurs sont présentes dans les champs de la variable `personaldetails` , elles s’affichent au niveau du champ lorsque vous cliquez sur le `Next` et le bouton `feedback` reste invisible.

![Définir l’aperçu du formulaire de propriété](/help/forms/assets/set-property-panel.png)

#### **Cas d’utilisation**: validez le champ.

Ajoutez le code suivant dans la fonction personnalisée, comme expliqué dans la section [create-custom-function](#create-custom-function) pour valider le champ.

```javascript
    /**
    * validateField
    * @name validateField
    * @param {object} field
    * @param {scope} globals
    */
    function validateField(field,globals)
    {
    
        globals.functions.validate(field);
    
    }   
```

>[!NOTE]
>
> Si aucun argument n’est transmis dans la variable `validate()` , il valide le formulaire.

Dans cet exemple, un modèle de validation personnalisé est appliqué au `contact` champ . Les utilisateurs doivent saisir un numéro de téléphone commençant par `10` suivie de `8` des chiffres. Si l’utilisateur saisit un numéro de téléphone qui ne commence pas par `10` ou contient plus ou moins `8` chiffres, un message d’erreur de validation s’affiche lorsque vous cliquez sur le bouton :

![Modèle de validation de l’adresse électronique](/help/forms/assets/custom-function-validation-pattern.png)

L’étape suivante consiste à créer une règle pour le `Next` qui valide la variable `contact` sur le bouton cliquez.

![Modèle de validation](/help/forms/assets/custom-function-validate.png)

Reportez-vous à l’illustration ci-dessous pour démontrer que si l’utilisateur saisit un numéro de téléphone qui ne commence pas par `10`, un message d’erreur s’affiche au niveau du champ :

![Modèle de validation de l’adresse électronique](/help/forms/assets/custom-function-validate-error-message.png)

Si l’utilisateur saisit un numéro de téléphone valide et tous les champs de la variable `personaldetails` sont validées, la variable `feedback` s’affiche à l’écran :

![Modèle de validation de l’adresse électronique](/help/forms/assets/validate-form-preview-form.png)

#### **Cas d’utilisation**: réinitialisation d’un panneau

Ajoutez le code suivant dans la fonction personnalisée, comme expliqué dans la section [create-custom-function](#create-custom-function) pour réinitialiser le panneau.

```javascript
    /**
    * resetField
    * @name  resetField
    * @param {string} input1
    * @param {object} field
    * @param {scope} globals 
    */
    function  resetField(field,globals)
    {
    
        globals.functions.reset(field);
    
    }
```

>[!NOTE]
>
> Si aucun argument n’est transmis dans la variable `reset()` , il valide le formulaire.

Dans cet exemple, la variable `personaldetails` réinitialise le panneau lorsque vous cliquez sur `Clear` bouton . L’étape suivante consiste à créer une règle pour la variable `Clear` pour réinitialiser le panneau sur le bouton.

![Bouton Effacer](/help/forms/assets/custom-function-reset-field.png)

Consultez l’illustration ci-dessous pour afficher que si l’utilisateur clique sur le bouton `clear` , le bouton `personaldetails` réinitialisations du panneau :

![Réinitialiser le formulaire](/help/forms/assets/custom-function-reset-form.png)

#### **Cas d’utilisation**: pour afficher un message personnalisé au niveau du champ et marquer le champ comme non valide

Vous pouvez utiliser la variable `markFieldAsInvalid()` pour définir un champ comme non valide et définir un message d’erreur personnalisé au niveau du champ. La variable `fieldIdentifier` peut être `fieldId`, ou `field qualifiedName`, ou `field dataRef`. La valeur de l’objet nommé `option` peut être `{useId: true}`, `{useQualifiedName: true}`, ou `{useDataRef: true}`.
Les syntaxes utilisées pour marquer le champ comme non valide et définir un message personnalisé sont les suivantes :

* `globals.functions.markFieldAsInvalid(field.$id,"[custom message]",{useId: true});`
* `globals.functions.markFieldAsInvalid(field.$qualifiedName, "[custom message]", {useQualifiedName: true});`
* `globals.functions.markFieldAsInvalid(field.$dataRef, "[custom message]", {useDataRef: true});`

Ajoutez le code suivant dans la fonction personnalisée, comme expliqué dans la section [create-custom-function](#create-custom-function) pour activer le message personnalisé au niveau du champ.

```javascript
    /**
    * customMessage
    * @name customMessage
    * @param {object} field
    * @param {scope} globals 
    */
    function customMessage(field, globals) {
    const minLength = 15;
    const comments = field.$value.trim();
    if (comments.length < minLength) {
        globals.functions.markFieldAsInvalid(field.$id, "Comments must be at least 15 characters long.", { useId: true });
    }
}
```

Dans cet exemple, si l’utilisateur saisit moins de 15 caractères dans la zone de texte des commentaires, un message personnalisé s’affiche au niveau du champ.

L’étape suivante consiste à créer une règle pour la variable `comments` field :

![Marquer le champ comme non valide](/help/forms/assets/custom-function-invalid-field.png)

Voir la démonstration ci-dessous pour afficher la saisie de commentaires négatifs dans la variable `comments` déclenche l’affichage d’un message personnalisé au niveau du champ :

![Marquer le champ comme formulaire d’aperçu non valide](/help/forms/assets/custom-function-invalidfield-form.png)

Si l’utilisateur saisit plus de 15 caractères dans la zone de texte des commentaires, le champ est validé et le formulaire est envoyé :

![Marquer un champ comme formulaire d’aperçu valide](/help/forms/assets/custom-function-validfield-form.png)


#### **Cas d’utilisation**: envoi de données modifiées au serveur

La ligne de code suivante :
`globals.functions.submitForm(globals.functions.exportData(), false);` sert à envoyer les données de formulaire après manipulation.
* Le premier argument est celui des données à soumettre.
* Le deuxième argument indique si le formulaire doit être validé avant envoi. Il s’agit de `optional` et définissez sur `true` par défaut.
* Le troisième argument est le suivant : `contentType` de l’envoi, qui est également `optional` avec la valeur par défaut comme `multipart/form-data`.

Ajoutez le code suivant dans la fonction personnalisée, comme expliqué dans la section [create-custom-function](#create-custom-function) pour envoyer les données manipulées sur le serveur :

```javascript
    /**
    * submitData
    * @name submitData
    * @param {object} field
    * @param {scope} globals 
    */

    function submitData(globals)
    {
    
    var data = globals.functions.exportData();
    if(!data.comments) {
    data.comments = 'NA';
    }
    console.log('After update:{}',data);
    globals.functions.submitForm(data, false);
    }
```

Dans cet exemple, si l’utilisateur quitte la fonction `comments` textbox vide, le champ `NA` est envoyée au serveur lors de l’envoi du formulaire.

Créez maintenant une règle pour le `Submit` qui envoie les données :

![Envoi de données](/help/forms/assets/custom-function-submit-data.png)

Reportez-vous à l’illustration du `console window` ci-dessous pour démontrer que si l’utilisateur quitte la fonction `comments` textbox vide, puis la valeur comme `NA` est envoyé au serveur :

![Envoi des données dans la fenêtre de console](/help/forms/assets/custom-function-submit-data-form.png)

Vous pouvez également vérifier la fenêtre de la console pour visualiser les données envoyées au serveur :

![Données Inspect dans la fenêtre de console](/help/forms/assets/custom-function-submit-data-console-data.png)

## Prise en charge de la mise en cache d’une fonction personnalisée

Les Forms adaptatives implémentent la mise en cache pour les fonctions personnalisées afin d’améliorer le temps de réponse lors de la récupération de la liste des fonctions personnalisées dans l’éditeur de règles. Un message sous la forme `Fetched following custom functions list from cache` apparaît dans la variable `error.log` fichier .

![fonction personnalisée avec prise en charge du cache](/help/forms/assets/custom-function-cache-error.png)

Si les fonctions personnalisées sont modifiées, la mise en cache est invalidée et elle est analysée.

## Résolution des problèmes

Si le fichier JavaScript contenant du code pour les fonctions personnalisées comporte une erreur, les fonctions personnalisées ne sont pas répertoriées dans l’éditeur de règles d’un formulaire adaptatif. Pour vérifier la liste des fonctions personnalisées, vous pouvez accéder au `error.log` pour l’erreur. En cas d’erreur, la liste des fonctions personnalisées apparaît vide :

![fichier journal des erreurs](/help/forms/assets/custom-function-list-error-file.png)

En l’absence d’erreur, la fonction personnalisée est récupérée et apparaît dans la variable `error.log` fichier . Un message sous la forme `Fetched following custom functions list` apparaît dans la variable `error.log` fichier :

![fichier journal d’erreurs avec fonction personnalisée appropriée](/help/forms/assets/custom-function-list-fetched-in-error.png)

## Considérations

* La variable `parameter type` et `return type` ne pas prendre en charge `None`.

* Les fonctions qui ne sont pas prises en charge dans la liste des fonctions personnalisées sont les suivantes :
   * Fonctions du générateur
   * Fonctions asynchrones/attendues
   * Définitions des méthodes
   * Méthodes de classe
   * Paramètres par défaut
   * Paramètres REST

## Voir également {#see-also}

{{see-also}}


