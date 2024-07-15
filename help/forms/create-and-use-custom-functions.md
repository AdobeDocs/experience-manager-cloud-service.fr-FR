---
title: Création et ajout de fonctions personnalisées dans un formulaire adaptatif
description: AEM Forms prend en charge les fonctions personnalisées qui permettent aux utilisateurs de créer et d’utiliser leurs propres fonctions dans l’éditeur de règles.
keywords: Ajoutez une fonction personnalisée, utilisez une fonction personnalisée, créez une fonction personnalisée, utilisez une fonction personnalisée dans l’éditeur de règles.
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Core Components
exl-id: 24607dd1-2d65-480b-a831-9071e20c473d
role: User, Developer
source-git-commit: 52b87073cad84705b5dc0c6530aff44d1e686609
workflow-type: tm+mt
source-wordcount: '4333'
ht-degree: 2%

---


# Fonctions personnalisées dans le Forms adaptatif (composants principaux)

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/adaptive-forms-core-components/create-and-use-custom-functions) |
| AEM as a Cloud Service | Cet article |

## Présentation

AEM Forms prend en charge les fonctions personnalisées, ce qui permet aux utilisateurs de définir des fonctions JavaScript pour l’implémentation de règles commerciales complexes. Ces fonctions personnalisées étendent les capacités des formulaires en facilitant la manipulation et le traitement des données saisies pour répondre aux exigences spécifiées. Ils permettent également une modification dynamique du comportement du formulaire en fonction de critères prédéfinis.

>[!NOTE]
>
> Assurez-vous que le [composant principal](https://github.com/adobe/aem-core-forms-components) est défini sur la dernière version pour utiliser les dernières fonctionnalités.

### Utilisation de fonctions personnalisées {#uses-of-custom-function}

Les avantages des fonctions personnalisées dans les Forms adaptatives sont les suivants :
* **Traitement des données** : les fonctions personnalisées aident à traiter les données saisies dans les champs de formulaires.
* **Validation des données** : les fonctions personnalisées vous permettent d’effectuer des vérifications personnalisées sur les entrées de formulaire et de fournir des messages d’erreur spécifiés.
* **Comportement dynamique** : les fonctions personnalisées vous permettent de contrôler le comportement dynamique de vos formulaires en fonction de conditions spécifiques. Vous pouvez, par exemple, afficher/masquer des champs, modifier les valeurs de champ ou ajuster dynamiquement la logique du formulaire.
* **Intégration** : vous pouvez utiliser des fonctions personnalisées pour intégrer des API ou des services externes. Il permet de récupérer des données provenant de sources externes, d’envoyer des données à des points de terminaison Rest externes ou d’effectuer des actions personnalisées basées sur des événements externes.

Les fonctions personnalisées sont essentiellement des bibliothèques clientes ajoutées dans le fichier JavaScript. Une fois que vous avez créé une fonction personnalisée, elle est disponible dans l’éditeur de règles pour sélection par l’utilisateur dans un formulaire adaptatif. Les fonctions personnalisées sont identifiées par les annotations JavaScript dans l’éditeur de règles.

### Annotations JavaScript prises en charge pour la fonction personnalisée {#js-annotations}

Les annotations JavaScript sont utilisées pour fournir des métadonnées pour le code JavaScript. Il comprend des commentaires commençant par des symboles spécifiques, par exemple /** et @. Les annotations fournissent des informations importantes sur les fonctions, variables et autres éléments du code. Le formulaire adaptatif prend en charge les annotations JavaScript suivantes pour les fonctions personnalisées :

#### Nom

Le nom est utilisé pour identifier la fonction personnalisée dans l’éditeur de règles d’un formulaire adaptatif. Les syntaxes suivantes sont utilisées pour nommer une fonction personnalisée :

* `@name [functionName] <Function Name>`
* `@function [functionName] <Function Name>`
* `@func [functionName] <Function Name>`.
  `functionName` est le nom de la fonction. Les espaces ne sont pas autorisés.
  `<Function Name>` est le nom d’affichage de la fonction dans l’éditeur de règles d’un formulaire adaptatif.
Si le nom de la fonction est identique au nom de la fonction elle-même, vous pouvez omettre `[functionName]` dans la syntaxe .

#### Paramètre

Le paramètre est une liste d’arguments utilisés par les fonctions personnalisées. Une fonction peut prendre en charge plusieurs paramètres. Les syntaxes suivantes sont utilisées pour définir un paramètre dans une fonction personnalisée :

* `@param {type} name <Parameter Description>`
* `@argument` `{type} name <Parameter Description>`
* `@arg` `{type}` `name <Parameter Description>`.
  `{type}` représente le type de paramètre.  Les types de paramètres autorisés sont les suivants :

   * string : représente une seule valeur de chaîne.
   * number : représente une seule valeur numérique.
   * boolean : représente une seule valeur booléenne (true ou false).
   * string[] : représente un tableau de valeurs de chaîne.
   * number[] : représente un tableau de valeurs numériques.
   * boolean[] : représente un tableau de valeurs booléennes.
   * date : représente une seule valeur de date.
   * date[] : représente un tableau de valeurs de date.
   * array : représente un tableau générique contenant des valeurs de différents types.
   * object : représente l’objet de formulaire transmis à une fonction personnalisée au lieu de transmettre directement sa valeur.
   * scope : représente l’objet global, qui contient des variables en lecture seule telles que des instances de formulaire, des instances de champ cible et des méthodes permettant d’effectuer des modifications de formulaire dans des fonctions personnalisées. Il est déclaré comme dernier paramètre dans les annotations JavaScript et n’est pas visible dans l’éditeur de règles d’un formulaire adaptatif. Le paramètre scope accède à l’objet du formulaire ou du composant pour déclencher la règle ou l’événement requis pour le traitement du formulaire. Pour plus d’informations sur l’objet Globals et comment l’utiliser, [cliquez ici](/help/forms/create-and-use-custom-functions.md#support-field-and-global-objects).

Le type de paramètre n’est pas sensible à la casse et les espaces ne sont pas autorisés dans le nom du paramètre.

`<Parameter Description>` contient des détails sur l’objectif du paramètre. Il peut avoir plusieurs mots.

**Paramètres facultatifs**
Par défaut, tous les paramètres sont obligatoires. Vous pouvez définir un paramètre comme facultatif en ajoutant `=` après le type de paramètre ou en englobant le nom du paramètre dans `[]`. Les paramètres définis comme facultatifs dans les annotations JavaScript sont affichés comme facultatifs dans l’éditeur de règles.
Pour définir une variable comme paramètre facultatif, vous pouvez utiliser l’une des syntaxes suivantes :

* `@param {type=} Input1`

Dans la ligne de code ci-dessus, `Input1` est un paramètre facultatif sans valeur par défaut. Pour déclarer un paramètre facultatif avec la valeur par défaut :
`@param {string=<value>} input1`

`input1` comme paramètre facultatif avec la valeur par défaut définie sur `value`.

* `@param {type} [Input1]`

Dans la ligne de code ci-dessus, `Input1` est un paramètre facultatif sans valeur par défaut. Pour déclarer un paramètre facultatif avec la valeur par défaut :
`@param {array} [input1=<value>]`
`input1` est un paramètre facultatif de type tableau avec la valeur par défaut définie sur `value`.
Assurez-vous que le type de paramètre est entre accolades {} et que le nom du paramètre est entre crochets.

Examinez le fragment de code suivant, où input2 est défini comme paramètre facultatif :

```javascript
        /**
         * optional parameter function
         * @name OptionalParameterFunction
         * @param {string} input1 
         * @param {string=} input2 
         * @return {string}
        */
        function OptionalParameterFunction(input1, input2) {
        let result = "Result: ";
        result += input1;
        if (input2 !== null) {
            result += " " + input2;
        }
        return result;
        }
```

L’illustration suivante s’affiche à l’aide de la fonction personnalisée `OptionalParameterFunction` dans l’éditeur de règles :

![ Paramètres facultatifs ou obligatoires ](/help/forms/assets/optional-default-params.png)

Vous pouvez enregistrer la règle sans spécifier de valeur pour les paramètres requis, mais la règle n’est pas exécutée et affiche un message d’avertissement :

![Avertissement de règle incomplet](/help/forms/assets/incomplete-rule.png)

Lorsque l’utilisateur laisse le paramètre facultatif vide, la valeur &quot;Non définie&quot; est transmise à la fonction personnalisée pour le paramètre facultatif.

Pour en savoir plus sur la définition de paramètres facultatifs dans JSDocs, [cliquez ici](https://jsdoc.app/tags-param).

#### Type de retour

Le type de retour spécifie le type de valeur que la fonction personnalisée renvoie après l’exécution. Les syntaxes suivantes sont utilisées pour définir un type de retour dans une fonction personnalisée :

* `@return {type}`
* `@returns {type}`
  `{type}` représente le type de retour de la fonction. Les types de retour autorisés sont les suivants :
   * string : représente une seule valeur de chaîne.
   * number : représente une seule valeur numérique.
   * boolean : représente une seule valeur booléenne (true ou false).
   * string[] : représente un tableau de valeurs de chaîne.
   * number[] : représente un tableau de valeurs numériques.
   * boolean[] : représente un tableau de valeurs booléennes.
   * date : représente une seule valeur de date.
   * date[] : représente un tableau de valeurs de date.
   * array : représente un tableau générique contenant des valeurs de différents types.
   * object : représente l’objet de formulaire au lieu de sa valeur directement.

  Le type de retour n’est pas sensible à la casse.

#### Privée

La fonction personnalisée déclarée comme privée n’apparaît pas dans la liste des fonctions personnalisées de l’éditeur de règles d’un formulaire adaptatif. Par défaut, les fonctions personnalisées sont publiques. La syntaxe pour déclarer une fonction personnalisée en tant que privée est `@private`.


## Instructions relatives à la création de fonctions personnalisées

Pour répertorier les fonctions personnalisées dans l’éditeur de règles, vous pouvez utiliser l’un des formats suivants :

### Instruction de fonction avec ou sans commentaires jsdoc

Vous pouvez créer une fonction personnalisée avec ou sans commentaires jsdoc.

```javascript
    function functionName(parameters) 
        {
            // code to be executed
        }
```
Si l’utilisateur n’ajoute aucune annotation JavaScript à la fonction personnalisée, elle est répertoriée dans l’éditeur de règles par son nom de fonction. Toutefois, il est recommandé d’inclure des annotations JavaScript pour améliorer la lisibilité des fonctions personnalisées.

### Fonction Flèche avec annotations ou commentaire JavaScript obligatoires

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

Si l’utilisateur n’ajoute aucune annotation JavaScript à la fonction personnalisée, celle-ci n’est pas répertoriée dans l’éditeur de règles d’un formulaire adaptatif.

### Expression de fonction avec annotations ou commentaire JavaScript obligatoires

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

Si l’utilisateur n’ajoute aucune annotation JavaScript à la fonction personnalisée, celle-ci n’est pas répertoriée dans l’éditeur de règles d’un formulaire adaptatif.

## Créer une fonction personnalisée {#create-custom-function}

Créez une bibliothèque cliente pour appeler des fonctions personnalisées dans l’éditeur de règles. Pour plus d’informations, voir [Utilisation des bibliothèques côté client](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html?lang=fr#developing).

Les étapes de création de fonctions personnalisées sont les suivantes :
1. [Créez une bibliothèque cliente.](#create-client-library)
1. [Ajout d’une bibliothèque cliente à un formulaire adaptatif](#use-custom-function)


### Conditions préalables à la création d’une fonction personnalisée

Avant de commencer à ajouter une fonction personnalisée à votre Forms adaptatif, assurez-vous que vous disposez des éléments suivants :

**Logiciel :**

* **Éditeur de texte brut (IDE)** : bien que tout éditeur de texte brut puisse fonctionner, un environnement de développement intégré (IDE) comme Microsoft Visual Studio Code offre des fonctionnalités avancées pour faciliter la modification.

* **Git :** Ce système de contrôle de version est nécessaire pour gérer les modifications de code. Si vous ne l’avez pas installé, téléchargez-le à partir de https://git-scm.com.

### Créez une bibliothèque cliente. {#create-client-library}

Vous pouvez ajouter des fonctions personnalisées en ajoutant une bibliothèque cliente. Pour créer une bibliothèque cliente, procédez comme suit :

**Cloner le référentiel**

Cloner votre [référentiel as a Cloud Service AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#accessing-git) :

1. Ouvrez la ligne de commande ou la fenêtre de terminal.

1. Accédez à l’emplacement souhaité sur votre ordinateur où stocker le référentiel.

1. Exécutez la commande suivante pour cloner le référentiel :

   `git clone [Git Repository URL]`

Cette commande télécharge le référentiel et crée un dossier local du référentiel cloné sur votre ordinateur. Dans ce guide, nous nous référons à ce dossier en tant que [répertoire de projet AEMaaCS].

**Ajouter un dossier de bibliothèque cliente**

Pour ajouter un nouveau dossier de bibliothèques clientes au [répertoire de projet AEMaaCS], procédez comme suit :

1. Ouvrez le [répertoire de projet AEMaaCS] dans un éditeur.

   ![Structure de dossier de fonctions personnalisées](/help/forms/assets/custom-library-folder-structure.png)

1. Recherchez `ui.apps`.
1. Ajoutez un nouveau dossier. Par exemple, ajoutez un dossier nommé `experience-league`.
1. Accédez au dossier `/experience-league/` et ajoutez un dossier `ClientLibraryFolder`. Par exemple, créez un dossier de bibliothèques clientes nommé `customclientlibs`.

   `Location is: [AEMaaCS project directory]/ui.apps/src/main/content/jcr_root/apps/`

**Ajouter des fichiers et des dossiers au dossier de bibliothèque cliente**

Ajoutez ce qui suit au dossier de bibliothèque cliente ajouté :

* fichier .content.xml
* fichier js.txt
* dossier js

`Location is: [AEMaaCS project directory]/ui.apps/src/main/content/jcr_root/apps/experience-league/customclientlibs/`

1. Dans le `.content.xml`, ajoutez les lignes de code suivantes :

   ```javascript
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
   jcr:primaryType="cq:ClientLibraryFolder"
   categories="[customfunctionscategory]"/>
   ```

   >[!NOTE]
   >
   > Vous pouvez choisir n’importe quel nom pour les propriétés `client library folder` et `categories`.

1. Dans le `js.txt`, ajoutez les lignes de code suivantes :

   ```javascript
         #base=js
       function.js
   ```
1. Dans le dossier `js`, ajoutez le fichier javascript `function.js` qui comprend les fonctions personnalisées :

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
1. Enregistrez les fichiers.

![Structure de dossier de fonctions personnalisées](/help/forms/assets/custom-function-added-files.png)

**Inclure le nouveau dossier dans filter.xml** :

1. Accédez au fichier `/ui.apps/src/main/content/META-INF/vault/filter.xml` dans votre [ répertoire de projet AEMaaCS].

1. Ouvrez le fichier et ajoutez la ligne suivante à la fin :

   `<filter root="/apps/experience-league" />`
1. Enregistrez le fichier.

![filtre de fonction personnalisé xml](/help/forms/assets/custom-function-filterxml.png)

**Déployez le dossier de bibliothèque cliente nouvellement créé dans votre environnement AEM**

Déployez le [répertoire de projet AEMaaCS] d’AEM as a Cloud Service dans votre environnement de Cloud Service. Pour effectuer un déploiement sur votre environnement de Cloud Service :

1. Validez les modifications

   1. Ajoutez, validez et envoyez les modifications dans le référentiel à l’aide des commandes ci-dessous :

   ```javascript
       git add .
       git commit -a -m "Adding custom functions"
       git push
   ```

1. Déployez le code mis à jour :

   1. Déclenchez un déploiement de votre code par le biais du pipeline de pile complète existant. Cette opération génère et déploie automatiquement le code mis à jour.

Si vous n’avez pas encore configuré de pipeline, reportez-vous au guide sur la configuration d’un pipeline pour AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#setup-pipeline).[

Une fois le pipeline exécuté avec succès, la fonction personnalisée ajoutée à la bibliothèque cliente devient disponible dans votre [éditeur de règles de formulaire adaptatif](/help/forms/rule-editor-core-components.md).

### Ajout d’une bibliothèque cliente à un formulaire adaptatif{#use-custom-function}

Une fois que vous avez déployé votre bibliothèque cliente dans votre environnement Forms CS, utilisez ses fonctionnalités dans votre formulaire adaptatif. Pour ajouter la bibliothèque cliente dans votre formulaire adaptatif

1. Ouvrez votre formulaire en mode d’édition. Pour ouvrir un formulaire en mode d’édition, sélectionnez un formulaire et choisissez **[!UICONTROL Modifier]**.
1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La fenêtre du conteneur de formulaires adaptatifs s’ouvre.
1. Ouvrez l’onglet **[!UICONTROL Basic]** et sélectionnez le nom de la **[!UICONTROL catégorie de bibliothèque cliente]** dans la liste déroulante (dans ce cas, sélectionnez `customfunctionscategory`).

   ![Ajout de la bibliothèque cliente de fonction personnalisée](/help/forms/assets/clientlib-custom-function.png)

   >[!NOTE]
   >
   > Plusieurs catégories peuvent être ajoutées en spécifiant une liste séparée par des virgules dans le champ **[!UICONTROL Catégorie de bibliothèque cliente]** .

1. Cliquez sur **[!UICONTROL Terminé]**.

Vous pouvez utiliser la fonction personnalisée dans l’ [ éditeur de règles d’un formulaire adaptatif](/help/forms/rule-editor-core-components.md) à l’aide des [ annotations JavaScript](##js-annotations).

## Utilisation d’une fonction personnalisée dans un formulaire adaptatif

Dans un formulaire adaptatif, vous pouvez utiliser des [fonctions personnalisées dans l’éditeur de règles](/help/forms/rule-editor-core-components.md). Ajoutons le code suivant au fichier JavaScript (`Function.js`) pour calculer l’âge en fonction de la date de naissance (AAAA-MM-JJ). Créez une fonction personnalisée `calculateAge()` qui prend la date de naissance comme entrée et renvoie l’âge :

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

![Fonction personnalisée Calcul de l’âge dans l’éditeur de règles](/help/forms/assets/custom-function-calculate-age.png)

Prévisualisons le formulaire pour observer comment les fonctions personnalisées sont implémentées par le biais de l’éditeur de règles :

![Fonction personnalisée Calcul de l’âge dans l’aperçu de formulaire de l’éditeur de règles](/help/forms/assets/custom-function-age-calculate-form.png)

>[!NOTE]
>
> Vous pouvez vous référer au dossier [custom function](/help/forms/assets//customfunctions.zip) suivant. Téléchargez et installez ce dossier dans votre instance AEM à l’aide du [Gestionnaire de modules](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager).


### Définition des options de liste déroulante à l’aide de fonctions personnalisées

L’éditeur de règles dans les composants principaux ne prend pas en charge la propriété **Set Options of** pour définir les options de liste déroulante au moment de l’exécution. Vous pouvez toutefois définir les options de liste déroulante à l’aide de fonctions personnalisées.

Consultez le code ci-dessous pour découvrir comment définir les options de liste déroulante à l’aide de fonctions personnalisées :

```javascript
    /**
    * @name setEnums
    * @returns {string[]}
    **/
    function setEnums() {
    return ["0","1","2","3","4","5","6"];   
    }

    /**
    * @name setEnumNames
    * @returns {string[]}
    **/
    function setEnumNames() {
    return ["Sunday","Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
    }
```

Dans le code ci-dessus, `setEnums` est utilisé pour définir la propriété `enum` et `setEnumNames` est utilisé pour définir la propriété `enumNames` de la liste déroulante.

Créez une règle pour le bouton `Next` , qui définit la valeur de l’option de liste déroulante lorsque l’utilisateur clique sur le bouton `Next` :

![Options de liste déroulante](/help/forms/assets/drop-down-list-options.png)

Reportez-vous à l’illustration ci-dessous pour démontrer où les options de la liste déroulante sont définies lorsque vous cliquez sur le bouton Afficher :

![Options de liste déroulante dans l’éditeur de règles](/help/forms/assets/drop-down-option-rule-editor.png)



### Prise en charge des fonctions asynchrones dans les fonctions personnalisées {#support-of-async-functions}

Les fonctions personnalisées asynchrones n’apparaissent pas dans la liste de l’éditeur de règles. Cependant, il est possible d’appeler des fonctions asynchrones dans des fonctions personnalisées créées à l’aide d’expressions de fonction synchrones.

![Fonction personnalisée de synchronisation et asynchrone](/help/forms/assets/workflow-for-sync-async-custom-fumction.png)

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

Dans l’exemple ci-dessus, la fonction asyncFunction est `asynchronous function`. Il effectue une opération asynchrone en effectuant une requête `GET` vers `https://petstore.swagger.io/v2/store/inventory`. Il attend la réponse à l’aide de `await`, analyse le corps de la réponse en tant que JSON à l’aide de `response.json()`, puis renvoie les données. La fonction `callAsyncFunction` est une fonction personnalisée synchrone qui appelle la fonction `asyncFunction` et affiche les données de réponse dans la console. Bien que la fonction `callAsyncFunction` soit synchrone, elle appelle la fonction asynchrone asyncFunction et gère son résultat avec des instructions `then` et `catch`.

Pour en voir le fonctionnement, nous allons ajouter un bouton et créer une règle pour le bouton qui appelle la fonction asynchrone lors d’un clic sur un bouton.

![création d’une règle pour la fonction asynchrone](/help/forms/assets/rule-for-async-funct.png)

Reportez-vous à l’illustration de la fenêtre de console ci-dessous pour démontrer que lorsque l’utilisateur clique sur le bouton `Fetch`, la fonction personnalisée `callAsyncFunction` est appelée, ce qui à son tour appelle une fonction asynchrone `asyncFunction`. Inspect dans la fenêtre de la console pour afficher la réponse à un clic sur le bouton :

![Fenêtre de console](/help/forms/assets/async-custom-funct-console.png)

Explorons les fonctionnalités des fonctions personnalisées.

## Diverses fonctionnalités des fonctions personnalisées

Vous pouvez utiliser des fonctions personnalisées pour ajouter des fonctions personnalisées aux formulaires. Ces fonctions prennent en charge diverses fonctionnalités, telles que l’utilisation de champs spécifiques, l’utilisation de champs globaux ou la mise en cache. Cette flexibilité vous permet de personnaliser les formulaires en fonction des besoins de votre entreprise.

### Objets de champ et de portée globale dans les fonctions personnalisées {#support-field-and-global-objects}

Les objets de champ font référence aux composants ou éléments individuels d’un formulaire, tels que les champs de texte et les cases à cocher. L’objet Globals contient des variables en lecture seule, telles que l’instance de formulaire, l’instance de champ cible et des méthodes permettant de modifier le formulaire dans des fonctions personnalisées.

>[!NOTE]
>
> `param {scope} globals` doit être le dernier paramètre et il ne s’affiche pas dans l’éditeur de règles d’un formulaire adaptatif.

<!-- Let us look at the following code snippet:

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
    // Updating the field value with the formatted date and time using setProperty.
    globals.functions.setProperty(field, {value: formattedDateTime});
    }
```

In the above code snippet, a custom function named `updateDateTime` takes parameters such as a field object and a global object. The field represents the textbox object where the formatted date and time value is displayed within the form. -->

Découvrez comment les fonctions personnalisées utilisent des objets de champ et globaux à l’aide d’un formulaire `Contact Us` à l’aide de différents cas d’utilisation.

![Formulaire de contact](/help/forms/assets/contact-us-form.png)

+++ **Cas d’utilisation** : afficher un panneau à l’aide de la règle `SetProperty`

Ajoutez le code suivant dans la fonction personnalisée, comme expliqué dans la section [create-custom-function](#create-custom-function), pour définir le champ de formulaire comme `Required`.

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
> * Vous pouvez configurer les propriétés de champ à l’aide des propriétés disponibles situées dans `[form-path]/jcr:content/guideContainer.model.json`.
> * Les modifications apportées au formulaire à l’aide de la méthode `setProperty` de l’objet Globals sont de nature asynchrone et ne sont pas reflétées lors de l’exécution de la fonction personnalisée.

Dans cet exemple, la validation du panneau `personaldetails` se produit lorsque vous cliquez sur le bouton. Si aucune erreur n’est détectée dans le panneau, un autre panneau, le panneau `feedback`, devient visible lorsque l’utilisateur clique sur le bouton.

Créez une règle pour le bouton `Next` , qui valide le panneau `personaldetails` et rend le panneau `feedback` visible lorsque l’utilisateur clique sur le bouton `Next`.

![Définir la propriété](/help/forms/assets/custom-function-set-property.png)

Reportez-vous à l’illustration ci-dessous pour démontrer où le panneau `personaldetails` est validé en cliquant sur le bouton `Next`. Si tous les champs de `personaldetails` sont validés, le panneau `feedback` devient visible.

![Définir l’aperçu du formulaire de propriété](/help/forms/assets/set-property-form-preview.png)

Si des erreurs sont présentes dans les champs du panneau `personaldetails`, elles s’affichent au niveau du champ lorsque vous cliquez sur le bouton `Next` et le panneau `feedback` reste invisible.

![Définir l’aperçu du formulaire de propriété](/help/forms/assets/set-property-panel.png)

+++

+++ **Cas d’utilisation** : validez le champ.

Ajoutez le code suivant dans la fonction personnalisée, comme expliqué dans la section [create-custom-function](#create-custom-function) , pour valider le champ.

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
> Si aucun argument n’est transmis dans la fonction `validate()`, le formulaire est validé.

Dans cet exemple, un modèle de validation personnalisé est appliqué au champ `contact`. Les utilisateurs doivent saisir un numéro de téléphone commençant par `10` suivi de `8` chiffres. Si l’utilisateur saisit un numéro de téléphone qui ne commence pas par `10` ou qui contient plus ou moins de `8` chiffres, un message d’erreur de validation s’affiche lorsque l’utilisateur clique sur le bouton :

![Modèle de validation d’adresse de courriel](/help/forms/assets/custom-function-validation-pattern.png)

L’étape suivante consiste à créer une règle pour le bouton `Next` qui valide le champ `contact` sur le bouton de clic.

![Modèle de validation](/help/forms/assets/custom-function-validate.png)

Reportez-vous à l’illustration ci-dessous pour démontrer que si l’utilisateur saisit un numéro de téléphone qui ne commence pas par `10`, un message d’erreur s’affiche au niveau du champ :

![Modèle de validation d’adresse de courriel](/help/forms/assets/custom-function-validate-error-message.png)

Si l’utilisateur saisit un numéro de téléphone valide et que tous les champs du panneau `personaldetails` sont validés, le panneau `feedback` s’affiche à l’écran :

![Modèle de validation d’adresse de courriel](/help/forms/assets/validate-form-preview-form.png)

+++

+++ **Cas d’utilisation** : réinitialisation d’un panneau

Ajoutez le code suivant dans la fonction personnalisée, comme expliqué dans la section [create-custom-function](#create-custom-function) , pour réinitialiser le panneau.

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
> Si aucun argument n’est transmis dans la fonction `reset()`, le formulaire est validé.

Dans cet exemple, le panneau `personaldetails` se réinitialise lorsque vous cliquez sur le bouton `Clear` . L’étape suivante consiste à créer une règle pour le bouton `Clear` qui réinitialise le panneau sur le bouton de clic.

![Bouton Effacer](/help/forms/assets/custom-function-reset-field.png)

Consultez l’illustration ci-dessous pour afficher que si l’utilisateur clique sur le bouton `clear`, le panneau `personaldetails` réinitialise :

![Réinitialiser le formulaire](/help/forms/assets/custom-function-reset-form.png)

+++

+++ **Cas d’utilisation** : pour afficher un message personnalisé au niveau du champ et marquer le champ comme non valide

Vous pouvez utiliser la fonction `markFieldAsInvalid()` pour définir un champ comme non valide et définir un message d’erreur personnalisé au niveau du champ. La valeur `fieldIdentifier` peut être `fieldId`, `field qualifiedName` ou `field dataRef`. La valeur de l’objet nommé `option` peut être `{useId: true}`, `{useQualifiedName: true}` ou `{useDataRef: true}`.
Les syntaxes utilisées pour marquer un champ comme non valide et définir un message personnalisé sont les suivantes :

* `globals.functions.markFieldAsInvalid(field.$id,"[custom message]",{useId: true});`
* `globals.functions.markFieldAsInvalid(field.$qualifiedName, "[custom message]", {useQualifiedName: true});`
* `globals.functions.markFieldAsInvalid(field.$dataRef, "[custom message]", {useDataRef: true});`

Ajoutez le code suivant dans la fonction personnalisée, comme expliqué dans la section [create-custom-function](#create-custom-function), pour activer un message personnalisé au niveau du champ.

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

L’étape suivante consiste à créer une règle pour le champ `comments` :

![Marquer le champ comme non valide](/help/forms/assets/custom-function-invalid-field.png)

Voir la démonstration ci-dessous pour afficher que la saisie de commentaires négatifs dans le champ `comments` déclenche l’affichage d’un message personnalisé au niveau du champ :

![Marquer le champ comme formulaire d’aperçu non valide](/help/forms/assets/custom-function-invalidfield-form.png)

Si l’utilisateur saisit plus de 15 caractères dans la zone de texte des commentaires, le champ est validé et le formulaire est envoyé :

![Marquer le champ comme formulaire d’aperçu valide](/help/forms/assets/custom-function-validfield-form.png)

+++

+++ **Cas d’utilisation** : envoi de données modifiées au serveur

La ligne de code suivante :
`globals.functions.submitForm(globals.functions.exportData(), false);` est utilisé pour envoyer les données de formulaire après la manipulation.
* Le premier argument est celui des données à soumettre.
* Le deuxième argument indique si le formulaire doit être validé avant envoi. Il est `optional` et est défini sur `true` par défaut.
* Le troisième argument est le `contentType` de l’envoi, qui est également facultatif avec la valeur par défaut `multipart/form-data`. Les autres valeurs peuvent être `application/json` et `application/x-www-form-urlencoded`.

Ajoutez le code suivant dans la fonction personnalisée, comme expliqué dans la section [create-custom-function](#create-custom-function) , pour envoyer les données manipulées sur le serveur :

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

Dans cet exemple, si l’utilisateur laisse la zone de texte `comments` vide, `NA` est envoyé au serveur lors de l’envoi du formulaire.

Créez maintenant une règle pour le bouton `Submit` qui envoie les données :

![Envoi de données](/help/forms/assets/custom-function-submit-data.png)

Reportez-vous à l’illustration de `console window` ci-dessous pour démontrer que si l’utilisateur laisse la zone de texte `comments` vide, la valeur `NA` est envoyée au serveur :

![Envoi de données dans la fenêtre de console](/help/forms/assets/custom-function-submit-data-form.png)

Vous pouvez également vérifier la fenêtre de la console pour visualiser les données envoyées au serveur :

![Données Inspect dans la fenêtre de console](/help/forms/assets/custom-function-submit-data-console-data.png)

+++

+++ **Cas d’utilisation** : remplacement du succès d’envoi de formulaire et des gestionnaires d’erreurs

Ajoutez la ligne de code suivante, comme expliqué dans la section [create-custom-function](#create-custom-function) , pour personnaliser le message d’envoi ou d’échec pour les envois de formulaire et afficher les messages d’envoi de formulaire dans une boîte modale :

```javascript
/**
 * Handles the success response after a form submission.
 *
 * @param {scope} globals - This object contains a read-only form instance, target field instance, triggered event, and methods for performing form modifications within custom functions.
 * @returns {void}
 */
function customSubmitSuccessHandler(globals) {
    var event = globals.event;
    var submitSuccessResponse = event.payload.body;
    var form = globals.form;

    if (submitSuccessResponse) {
        if (submitSuccessResponse.redirectUrl) {
            window.location.href = encodeURI(submitSuccessResponse.redirectUrl);
        } else if (submitSuccessResponse.thankYouMessage) {
            showModal("success", submitSuccessResponse.thankYouMessage);
        }
    }
}

/**
 * Handles the error response after a form submission.
 *
 * @param {string} customSubmitErrorMessage - The custom error message.
 * @param {scope} globals - This object contains a read-only form instance, target field instance, triggered event, and methods for performing form modifications within custom functions.
 * @returns {void}
 */
function customSubmitErrorHandler(customSubmitErrorMessage, globals) {
    showModal("error", customSubmitErrorMessage);
}
function showModal(type, message) {
    // Remove any existing modals
    var existingModal = document.getElementById("modal");
    if (existingModal) {
        existingModal.remove();
    }

    // Create the modal dialog
    var modal = document.createElement("div");
    modal.setAttribute("id", "modal");
    modal.setAttribute("class", "modal");

    // Create the modal content
    var modalContent = document.createElement("div");
    modalContent.setAttribute("class", "modal-content");

    // Create the modal header
    var modalHeader = document.createElement("div");
    modalHeader.setAttribute("class", "modal-header");
    modalHeader.innerHTML = "<h2>" + (type === "success" ? "Thank You" : "Error") + "</h2>";

    // Create the modal body
    var modalBody = document.createElement("div");
    modalBody.setAttribute("class", "modal-body");
    modalBody.innerHTML = "<p class='" + type + "-message'>" + message + "</p>";

    // Create the modal footer
    var modalFooter = document.createElement("div");
    modalFooter.setAttribute("class", "modal-footer");

    // Create the close button
    var closeButton = document.createElement("button");
    closeButton.setAttribute("class", "close-button");
    closeButton.innerHTML = "Close";
    closeButton.onclick = function() {
        modal.remove();
    };

    // Append the elements to the modal content
    modalFooter.appendChild(closeButton);
    modalContent.appendChild(modalHeader);
    modalContent.appendChild(modalBody);
    modalContent.appendChild(modalFooter);

    // Append the modal content to the modal
    modal.appendChild(modalContent);

    // Append the modal to the document body
    document.body.appendChild(modal);
}
```

Dans cet exemple, lorsque l’utilisateur utilise les fonctions personnalisées `customSubmitSuccessHandler` et `customSubmitErrorHandler`, les messages de succès et d’échec sont affichés dans un modal. La fonction JavaScript `showModal(type, message)` est utilisée pour créer et afficher dynamiquement une boîte de dialogue modale sur un écran.

Maintenant, créez une règle pour envoyer le formulaire avec succès :

![Succès d&#39;envoi de formulaire](/help/forms/assets/form-submission-success.png)

Reportez-vous à l’illustration ci-dessous pour démontrer que lorsque le formulaire est envoyé avec succès, le message de réussite s’affiche dans un modal :

![ Message de succès d&#39;envoi de formulaire](/help/forms/assets/form-submission-success-message.png)

De même, nous allons créer une règle pour les envois de formulaire ayant échoué :

![Échec de l’envoi du formulaire](/help/forms/assets/form-submission-fail.png)

Reportez-vous à l’illustration ci-dessous pour démontrer que lorsque l’envoi du formulaire échoue, le message d’erreur s’affiche dans un modal :

![Message d’échec d’envoi de formulaire](/help/forms/assets/form-submission-fail-message.png)

Pour afficher par défaut le succès et l’échec de l’envoi du formulaire, les fonctions `Default submit Form Success Handler` et `Default submit Form Error Handler` sont disponibles.

Si le gestionnaire d’envoi personnalisé ne fonctionne pas comme prévu dans les AEM de projets ou de formulaires existants, reportez-vous à la section [résolution des problèmes](#troubleshooting) .

+++

+++ **Cas d’utilisation** : effectuer des actions dans une instance spécifique du panneau répétable

Les règles créées à l’aide de l’éditeur de règles visuel sur un panneau répétable s’appliquent à la dernière instance du panneau répétable. Pour écrire une règle pour une instance spécifique du panneau répétable, nous pouvons utiliser une fonction personnalisée.

Créons un autre formulaire pour recueillir des informations sur les voyageurs qui se rendent à destination. Un panneau du voyageur est ajouté en tant que panneau répétable, où l’utilisateur peut ajouter des détails pour 5 voyageurs à l’aide du bouton `Add Traveler`.

![Informations sur le voyageur](/help/forms/assets/traveler-info-form.png)

Ajoutez la ligne de code suivante, comme expliqué dans la section [create-custom-function](#create-custom-function) , pour effectuer des actions dans une instance spécifique du panneau répétable, autre que la dernière :

```javascript
/**
* @name hidePanelInRepeatablePanel
* @param {scope} globals
*/
function hidePanelInRepeatablePanel(globals)
{    
    var repeatablePanel = globals.form.travelerinfo;
    // hides a panel inside second instance of repeatable panel
    globals.functions.setProperty(repeatablePanel[1].traveler, {visible : false});
}  
```

Dans cet exemple, la fonction personnalisée `hidePanelInRepeatablePanel` exécute une action dans une instance spécifique du panneau répétable. Dans le code ci-dessus, `travelerinfo` représente le panneau répétable. Le code `repeatablePanel[1].traveler, {visible: false}` masque le panneau dans la deuxième instance du panneau répétable.

Ajoutons un bouton intitulé `Hide` et ajoutez une règle pour masquer la deuxième instance d’un panneau répétable.

![Masquer la règle de panneau](/help/forms/assets/custom-function-hidepanel-rule.png)

Reportez-vous à la vidéo ci-dessous pour démontrer que lorsque l’utilisateur clique sur `Hide`, le panneau de la seconde instance répétable se cache :

>[!VIDEO](https://video.tv.adobe.com/v/3429554?quality=12&learn=on)

+++

+++ **Usecase** : préremplissez le champ avec une valeur au chargement du formulaire.

Ajoutez la ligne de code suivante, comme expliqué dans la section [create-custom-function](#create-custom-function) , pour charger la valeur prérenseignée dans un champ lorsque le formulaire est initialisé :

```javascript
/**
 * Tests import data
 * @name testImportData
 * @param {scope} globals
 */
function testImportData(globals)
{
    globals.functions.importData(Object.fromEntries([['amount','10000']]));
} 
```

Dans le code ci-dessus, la fonction `testImportData` préremplit le champ `Booking Amount` textbox lors du chargement du formulaire. Supposons que le formulaire de réservation nécessite que le montant minimum de réservation soit `10,000`.

Créons une règle lors de l’initialisation du formulaire, où la valeur du champ `Booking Amount` textbox est préremplie avec une valeur spécifiée au chargement du formulaire :

![Importer une règle de données](/help/forms/assets/custom-function-import-data.png)

Reportez-vous à la capture d’écran ci-dessous, qui montre que lorsque le formulaire se charge, la valeur de la zone de texte `Booking Amount` est préremplie avec une valeur spécifiée :

![Importer le formulaire de règle de données](/help/forms/assets/custom-function-prefill-form.png)

+++

+++ **Usecase** : définissez le focus sur le champ spécifique

Ajoutez la ligne de code suivante, comme expliqué dans la section [create-custom-function](#create-custom-function), pour définir la cible d’action sur le champ spécifié lorsque l’utilisateur clique sur le bouton `Submit` :

```javascript
/**
 * @name testSetFocus
 * @param {object} emailField
 * @param {scope} globals
 */
    function testSetFocus(field, globals)
    {
        globals.functions.setFocus(field);
    }
```

Ajoutons une règle au bouton `Submit` pour définir la cible d’action sur le champ textbox `Email ID` lorsque l’utilisateur clique dessus :

![Définir la règle de focus](/help/forms/assets/custom-function-set-focus.png)

Reportez-vous à la capture d’écran ci-dessous, qui montre que lorsque l’utilisateur clique sur le bouton `Submit`, la cible d’action est définie sur le champ `Email ID` :

![Définir la règle de focus](/help/forms/assets/custom-function-set-focus-form.png)

>[!NOTE]
>
> Vous pouvez utiliser le paramètre facultatif `$focusOption` si vous souhaitez vous concentrer sur le champ suivant ou précédent par rapport au champ `email`.

+++

+++ **Usecase** : ajout ou suppression d’un panneau répétable à l’aide de la propriété `dispatchEvent`

Ajoutez la ligne de code suivante, comme expliqué dans la section [create-custom-function](#create-custom-function) , pour ajouter un panneau lorsque l’utilisateur clique sur le bouton `Add Traveler` à l’aide de la propriété `dispatchEvent` :

```javascript
/**
 * Tests add instance with dispatchEvent
 * @name testAddInstance
 * @param {scope} globals
 */
function testAddInstance(globals)
{
    var repeatablePanel = globals.form.traveler;
    globals.functions.dispatchEvent(repeatablePanel,'addInstance');
}
```

Ajoutons une règle au bouton `Add Traveler` pour ajouter le panneau répétable lorsque l’utilisateur clique dessus :

![Ajouter une règle de panneau](/help/forms/assets/custom-function-add-panel.png)

Reportez-vous au gif ci-dessous, qui indique que lorsque vous cliquez sur le bouton `Add Traveler` , le panneau est ajouté à l’aide de la propriété `dispatchEvent` :

![Ajouter un panneau](/help/forms/assets/custom-function-add-panel.gif)

De même, ajoutez la ligne de code suivante, comme expliqué dans la section [create-custom-function](#create-custom-function) , pour supprimer un panneau lorsque l’utilisateur clique sur le bouton `Delete Traveler` à l’aide de la propriété `dispatchEvent` :

```javascript
/**
 
 * @name testRemoveInstance
 * @param {scope} globals
 */
function testRemoveInstance(globals)
{
    var repeatablePanel = globals.form.traveler;
    globals.functions.dispatchEvent(repeatablePanel, 'removeInstance');
} 
```

Ajoutons une règle au bouton `Delete Traveler` pour supprimer le panneau répétable lorsque l’utilisateur clique dessus :

![Supprimer la règle de panneau](/help/forms/assets/custom-function-delete-panel.png)

Reportez-vous au gif ci-dessous, qui indique que lorsque vous cliquez sur le bouton `Delete Traveler`, le panneau du voyageur est supprimé à l’aide de la propriété `dispatchEvent` :

![Supprimer le panneau](/help/forms/assets/custom-function-delete-panel.gif)

+++

## Prise en charge de la mise en cache d’une fonction personnalisée

Les Forms adaptatives implémentent la mise en cache pour les fonctions personnalisées afin d’améliorer le temps de réponse lors de la récupération de la liste des fonctions personnalisées dans l’éditeur de règles. Un message tel que `Fetched following custom functions list from cache` apparaît dans le fichier `error.log`.

![fonction personnalisée avec prise en charge du cache](/help/forms/assets/custom-function-cache-error.png)

Si les fonctions personnalisées sont modifiées, la mise en cache est invalidée et elle est analysée.

## Résolution des problèmes {#troubleshooting}

* Si le gestionnaire d’envoi personnalisé ne fonctionne pas comme prévu dans AEM projets ou formulaires existants, procédez comme suit :
   * Assurez-vous que la version des [composants principaux est mise à jour vers la version 3.0.18 et ultérieure](https://github.com/adobe/aem-core-forms-components). Toutefois, pour les projets et les formulaires AEM existants, les étapes suivantes sont nécessaires :

   * Pour le projet AEM, l’utilisateur doit remplacer toutes les instances de `submitForm('custom:submitSuccess', 'custom:submitError')` par `submitForm()` et déployer le projet via le pipeline Cloud Manager.

   * Pour les formulaires existants, si les gestionnaires d’envoi personnalisés ne fonctionnent pas correctement, l’utilisateur doit ouvrir et enregistrer la règle `submitForm` sur le bouton **Envoyer** à l’aide de l’éditeur de règles. Cette action remplace la règle existante de `submitForm('custom:submitSuccess', 'custom:submitError')` par `submitForm()` dans le formulaire.


* Si le fichier JavaScript contenant du code pour les fonctions personnalisées comporte une erreur, les fonctions personnalisées ne sont pas répertoriées dans l’éditeur de règles d’un formulaire adaptatif. Pour vérifier la liste des fonctions personnalisées, vous pouvez accéder au fichier `error.log` correspondant à l’erreur. En cas d’erreur, la liste des fonctions personnalisées apparaît vide :

  ![fichier journal d’erreur](/help/forms/assets/custom-function-list-error-file.png)

  En l’absence d’erreur, la fonction personnalisée est récupérée et apparaît dans le fichier `error.log`. Un message sous la forme `Fetched following custom functions list` apparaît dans le fichier `error.log` :

  ![ fichier journal d&#39;erreur avec fonction personnalisée appropriée](/help/forms/assets/custom-function-list-fetched-in-error.png)

## Considérations

* `parameter type` et `return type` ne prennent pas en charge `None`.

* Les fonctions qui ne sont pas prises en charge dans la liste des fonctions personnalisées sont les suivantes :
   * Fonctions du générateur
   * Fonctions asynchrones/attendues
   * Définitions des méthodes
   * Méthodes de classe
   * Paramètres par défaut
   * Paramètres REST

## Voir également {#see-also}

{{see-also}}


