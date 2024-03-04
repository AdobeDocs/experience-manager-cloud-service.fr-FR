---
title: Création et ajout de fonctions personnalisées dans un formulaire adaptatif
description: AEM Forms prend en charge les fonctions personnalisées qui permettent aux utilisateurs de créer et d’utiliser leurs propres fonctions dans l’éditeur de règles.
keywords: Ajoutez une fonction personnalisée, utilisez une fonction personnalisée, créez une fonction personnalisée, utilisez une fonction personnalisée dans l’éditeur de règles.
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Core Components
source-git-commit: 46fbed98a806f62dd1882eb0085d4338c5cd51a7
workflow-type: tm+mt
source-wordcount: '1108'
ht-degree: 26%

---


# Fonctions personnalisées dans le Forms adaptatif (composants principaux)

## Introduction

AEM Forms prend en charge les fonctions personnalisées, ce qui permet aux utilisateurs de définir des fonctions JavaScript pour l’implémentation de règles métier complexes. Ces fonctions personnalisées étendent les capacités des formulaires en facilitant la manipulation et le traitement des données saisies pour répondre aux exigences spécifiées. Ils permettent également une modification dynamique du comportement du formulaire en fonction de critères prédéfinis.
Dans les Forms adaptatives, vous pouvez utiliser des fonctions personnalisées dans les [éditeur de règles d’un formulaire adaptatif](/help/forms/rule-editor-core-components.md) pour créer des règles de validation spécifiques pour les champs de formulaire.

Comprenons l’utilisation de la fonction personnalisée dans laquelle les utilisateurs saisissent l’adresse électronique et vous souhaitez vous assurer que l’adresse électronique saisie respecte un format spécifique (elle contient un symbole &quot;@&quot; et un nom de domaine). Créez une fonction personnalisée &quot;ValidateEmail&quot; qui prend l’adresse email en entrée et renvoie true si elle est valide et false dans le cas contraire.

```javascript
function ValidateEmail(inputText)
{
    var email = /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/;
    if(inputText.value.match(email))
        {
            alert("Valid email address!");
            return true;
        }
    else
    {
        alert("Invalid email address!");
        return false;
    }
}
```

Dans l’exemple ci-dessus, lorsque l’utilisateur tente d’envoyer le formulaire, la fonction personnalisée &quot;ValidateEmail&quot; est appelée pour vérifier si l’adresse électronique saisie est valide.

### Utilisation de fonctions personnalisées {#uses-of-custom-function}

Les avantages des fonctions personnalisées dans les Forms adaptatives sont les suivants :

* **Manipulation des données**: les fonctions personnalisées manipulent et traitent les données saisies dans les champs de formulaires.
* **Validation des données**: les fonctions personnalisées vous permettent d’effectuer des vérifications personnalisées sur les entrées de formulaire et de fournir des messages d’erreur spécifiés.
* **Comportement dynamique**: les fonctions personnalisées vous permettent de contrôler le comportement dynamique de vos formulaires en fonction de conditions spécifiques. Vous pouvez, par exemple, afficher/masquer des champs, modifier les valeurs de champ ou ajuster dynamiquement la logique du formulaire.
* **Intégration**: vous pouvez utiliser des fonctions personnalisées pour l’intégration à des API ou services externes. Il permet de récupérer des données provenant de sources externes, d’envoyer des données à des points de terminaison Rest externes ou d’effectuer des actions personnalisées basées sur des événements externes.

## Annotations JS prises en charge

Assurez-vous que la fonction personnalisée que vous créez est accompagnée de la fonction `jsdoc` au-dessus.

Balises `jsdoc` prises en charge :

* Syntaxe
**Privé** : `@private`
Une fonction privée n’est pas incluse comme fonction personnalisée.

* Syntaxe
**Nom** : `@name funcName <Function Name>`
Autrement,`,` vous pouvez utiliser : `@function funcName <Function Name>` **ou** `@func` `funcName <Function Name>`.
  `funcName` est le nom de la fonction (les espaces ne sont pas autorisés).
  `<Function Name>` est le nom d’affichage de la fonction.

* Syntaxe
**Paramètre** : `@param {type} name <Parameter Description>`
Autrement, vous pouvez utiliser : `@argument` `{type} name <Parameter Description>` **ou** `@arg` `{type}` `name <Parameter Description>`.
Affiche les paramètres utilisés par la fonction. Une fonction peut comporter plusieurs balises de paramètre, une balise pour chaque paramètre dans l’ordre d’occurrence.
  `{type}` représente le type de paramètre. Les types de paramètre sont les suivants :

   1. chaîne
   2. nombre
   3. booléen
   4. portée
   5. chaîne[]
   6. nombre[]
   7. boolean[]
   8. date
   9. date[]
   10. tableau
   11. objet

  `scope` fait référence à un objet global spécial fourni par le composant d’exécution de formulaires. Il doit s’agir du dernier paramètre et il n’est pas visible par l’utilisateur dans l’éditeur de règles. Vous pouvez utiliser la portée pour accéder à un objet proxy de formulaire et de champ lisible pour lire les propriétés, l’événement qui a déclenché la règle et un ensemble de fonctions pour manipuler le formulaire.

  `object` type est utilisé pour transmettre l’objet de champ lisible dans le paramètre à une fonction personnalisée au lieu de transmettre la valeur.

  Tous les types de paramètre sont classés dans l’une des catégories ci-dessus. Ils sont tous pris en charge. Assurez-vous que vous sélectionnez l’un des types ci-dessus. Les types ne sont pas sensibles à la casse. Les espaces ne sont pas autorisés dans le nom du paramètre.  La description du paramètre peut contenir plusieurs mots.

* **Paramètre facultatif**
Syntaxe : `@param {type=} name <Parameter Description>`
Vous pouvez également utiliser : `@param {type} [name] <Parameter Description>`
Par défaut, tous les paramètres sont obligatoires. Vous pouvez marquer un paramètre facultatif en ajoutant `=` dans le type du paramètre ou en mettant le nom du paramètre entre crochets.
Par exemple, déclarons `Input1` comme paramètre facultatif :
   * `@param {type=} Input1`
   * `@param {type} [Input1]`

* Syntaxe
**Type de retour** : `@return {type}`
Autrement, vous pouvez utiliser `@returns {type}`.
Ajoute des informations sur la fonction, comme son objectif.
{type} représente le type de valeur renvoyée de la fonction. Les types de valeur renvoyée autorisés sont les suivants :

   1. chaîne
   2. nombre
   3. booléen
   4. chaîne[]
   5. nombre[]
   6. boolean[]
   7. date
   8. date[]
   9. tableau
   10. objet

Tous les autres types de retour sont classés en dessous de l’un des précédents. Ils sont tous pris en charge. Assurez-vous que vous sélectionnez l’un des types ci-dessus. Les types de valeur renvoyée ne sont pas sensibles à la casse.

## Remarques relatives à la création de fonctions personnalisées {#considerations}

Pour répertorier les fonctions personnalisées dans l’éditeur de règles, vous pouvez les déclarer dans l’un des formats suivants :

* **Instruction de fonction avec ou sans commentaires jsdoc**

Vous pouvez créer une fonction personnalisée avec ou sans commentaires jsdoc.

```javascript
    function functionName(parameters) 
        {
            // code to be executed
        }
```
<!--

* **Arrow function with mandatory jsdoc comment**

Some of the examples to create Arrow functions are:
```javascript
    /**
    * test function
    * @name testFunction test function
    * @param {string} a some parameter description
    * @param {string} b another parameter description
    * @return {string}
    */
    testFunction = (a, b) => {
    return a + b;
    };
```

    * @param {string=} b another parameter description
      /** */
    testFunction1=(a) => (return a)
    /** */
    testFunction2 = a => a + 100;-->

* **Expression de fonction avec commentaire jsdoc obligatoire**

Pour répertorier les fonctions personnalisées dans l’éditeur de règles d’un formulaire adaptatif, créez des fonctions personnalisées au format suivant :

```javascript
    /**
    * test function
    * @name testFunction test function
    * @param {string} input1 parameter description
    * @param {string} input2 another parameter description
    * @return {string}
    */
    testFunction = function(input1,input2)
        {
            // code to be executed
        }
```

<!--
* @param {string=} input2 another parameter description
The functions that are not supported in the custom function list are:
* Generator functions
* Async/Await functions 
* Method definitions
* Class methods
* Default parameters
* Rest parameters -->

>[!NOTE]
>
> Vous pouvez vérifier les `error.log` pour les erreurs, telles que les fonctions personnalisées qui ne sont pas répertoriées dans l’éditeur de règles.

<!--The `error.log` file also displays the methods and parameters that are not supported for custom functions. -->


## Création d’une fonction personnalisée {#create-custom-function}

Créez une bibliothèque cliente pour appeler des fonctions personnalisées dans l’éditeur de règles. Pour plus d’informations, voir [Utilisation des bibliothèques côté client](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html?lang=fr#developing).

Les étapes de création de fonctions personnalisées sont les suivantes :
1. [Créez une bibliothèque cliente.](#create-client-library)
1. [Ajout d’une bibliothèque cliente dans un formulaire adaptatif](#use-custom-function)

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

   >[!NOTE]
   >
   > Si le fichier JavaScript contenant du code pour les fonctions personnalisées comporte une erreur, les fonctions personnalisées ne sont pas répertoriées dans l’éditeur de règles d’un formulaire adaptatif. Vous pouvez également vérifier les `error.log` pour l’erreur.

   <!-- 
    >* AEM Adaptive Form supports the caching of custom functions. If the JavaScript is modified, the caching becomes invalidated, and it is parsed. You can see a message as `Fetched following custom functions list from cache` in the `error.log` file.  -->

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

1. [Exécuter le pipeline.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#setup-pipeline)

Une fois le pipeline exécuté correctement, la fonction personnalisée ajoutée à la bibliothèque cliente devient disponible dans votre [Éditeur de règles de formulaire adaptatif](/help/forms/rule-editor-core-components.md).

### Ajout d’une bibliothèque cliente dans un formulaire adaptatif{#use-custom-function}

Une fois que vous avez déployé votre bibliothèque cliente dans votre environnement Forms CS, utilisez ses fonctionnalités dans votre formulaire adaptatif. Pour ajouter la bibliothèque cliente dans votre formulaire adaptatif

1. Ouvrez votre formulaire en mode d’édition. Pour ouvrir un formulaire en mode d’édition, sélectionnez-le, puis **[!UICONTROL Modifier]**.
1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La fenêtre du conteneur de formulaires adaptatifs s’ouvre.
1. Ouvrez le **[!UICONTROL De base]** et sélectionnez le nom du **[!UICONTROL catégorie de bibliothèque cliente]** dans la liste déroulante (dans ce cas, sélectionnez `customfunctionscategory`).

   ![Ajout de la bibliothèque cliente de fonction personnalisée](/help/forms/assets/clientlib-custom-function.png)

1. Cliquez sur **[!UICONTROL Terminé]** .

Vous pouvez désormais créer une règle pour utiliser des fonctions personnalisées dans l’éditeur de règles.

<!--

Create a rule to use custom function in the rule editor. 

### Support for the optional parameters in custom functions{#support-for-optional-parameter}

AEM supports including optional parameters in JSDocs. These parameters are displayed as optional in the rule editor. There are two ways to add optional parameters in JSDocs:
*  `@param {string=abc} b -- some description for b which is optional`

    In the above line of code, `b` is an optional parameter with the default value set to `abc`. 
    Alternatively, you can define `b` as an optional parameter without assigning any default value as `@param {string=} b -- some description for b which is optional`

* `@param {array} [z=[def,xyz]] - - some description for z which is optional`

    In the above line of code, `z` is an optional parameter of array type with the default value set to `[def , xyz]`. 
    Alternatively, you can define `z` as an optional parameter without assigning any default value as `@param {array} [z=] - - some description for z which is optional`

>[!NOTE]
>
> Ensure that the parameter name is enclosed in square brackets [] and the parameter type is enclosed in curly brackets {}. 

To learn more about how to define optional parameters in JSDocs, [click here](https://jsdoc.app/tags-param).

In the rule editor of an Adaptive Form, the parameters are displayed as `required`. By default the parameters are `required`, if not defined as optional in JSDocs.

  ![Optional or required parameters](/help/forms/assets/optional-default-params.png) 

  You can save the rule without specifying a value for required parameters, but the rule is not executed and displays a warning message as:

  ![incomplete rule warning message](/help/forms/assets/incomplete-rule.png) 
  
  The rule is executed even if you do not specify a value for optional parameters. Undefined values are passed for optional parameters on executing the rule.

  ### Support for field and globals objects in custom functions {#support-field-and-global-objects}

  needs to be discussed

  -->

## Voir également {#see-also}

{{see-also}}





