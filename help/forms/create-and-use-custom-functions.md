---
title: Création et ajout de fonctions personnalisées dans un formulaire adaptatif
description: AEM Forms prend en charge les fonctions personnalisées qui permettent aux utilisateurs de créer et d’utiliser leurs propres fonctions dans l’éditeur de règles.
keywords: Ajoutez une fonction personnalisée, utilisez une fonction personnalisée, créez une fonction personnalisée, utilisez une fonction personnalisée dans l’éditeur de règles.
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Core Components
source-git-commit: 94a290964a92f8c6ed353d9c77f3dd3b8a5598a4
workflow-type: tm+mt
source-wordcount: '778'
ht-degree: 14%

---


# Fonctions personnalisées dans le Forms adaptatif (composants principaux)

## Introduction

AEM Forms prend en charge les fonctions personnalisées, ce qui permet aux utilisateurs de définir des fonctions JavaScript pour l’implémentation de règles métier complexes. Ces fonctions personnalisées étendent les capacités des formulaires en facilitant la manipulation et le traitement des données saisies pour répondre aux exigences spécifiées. Ils permettent également une modification dynamique du comportement du formulaire en fonction de critères prédéfinis.
Dans les Forms adaptatives, vous pouvez utiliser des fonctions personnalisées dans les [éditeur de règles d’un formulaire adaptatif](/help/forms/rule-editor.md#custom-functions) pour créer des règles de validation spécifiques pour les champs de formulaire.

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

Voici quelques avantages de l’utilisation de fonctions personnalisées dans les Forms adaptatives :

* **Manipulation des données**: les fonctions personnalisées manipulent et traitent les données saisies dans les champs de formulaires.
* **Validation des données**: les fonctions personnalisées vous permettent d’effectuer des vérifications personnalisées sur les entrées de formulaire et de fournir des messages d’erreur spécifiés.
* **Comportement dynamique**: les fonctions personnalisées vous permettent de contrôler le comportement dynamique de vos formulaires en fonction de conditions spécifiques. Vous pouvez, par exemple, afficher/masquer des champs, modifier les valeurs de champ ou ajuster dynamiquement la logique du formulaire.
* **Intégration**: vous pouvez utiliser des fonctions personnalisées pour l’intégration à des API ou services externes. Il permet de récupérer des données provenant de sources externes, d’envoyer des données à des points de terminaison Rest externes ou d’effectuer des actions personnalisées basées sur des événements externes.

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

* **Fonction Flèche avec commentaire jsdoc obligatoire**

Voici quelques exemples de création de fonctions Flèche :

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

<!-- 
    * @param {string=} b another parameter description
      /** */
    testFunction1=(a) => (return a)
    /** */
    testFunction2 = a => a + 100;-->

* **Expression de fonction avec commentaire jsdoc obligatoire**

Créez des fonctions personnalisées dans les formats suivants pour les répertorier dans l’éditeur de règles d’un formulaire adaptatif. Par exemple :

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
> Vous pouvez vérifier les `error.log` en cas d’erreurs, telles que des fonctions personnalisées, ne sont pas répertoriées dans l’éditeur de règles.

<!--The `error.log` file also displays the methods and parameters that are not supported for custom functions. -->


## Création d’une fonction personnalisée {#create-custom-function}

Créez une bibliothèque cliente pour appeler des fonctions personnalisées dans l’éditeur de règles. Pour plus d’informations, voir [Utilisation des bibliothèques côté client](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html?lang=fr#developing).

Les étapes de création de fonctions personnalisées sont les suivantes :
1. [Créez une bibliothèque cliente.](#create-client-library)
1. [Ajout d’une bibliothèque cliente dans un formulaire adaptatif](#use-custom-function)

### Créez une bibliothèque cliente. {#create-client-library}

Vous pouvez ajouter des fonctions personnalisées en ajoutant la bibliothèque cliente. Pour créer une bibliothèque cliente, procédez comme suit :

1. [Clonage de votre référentiel as a Cloud Service AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#accessing-git).
1. Créez un dossier sous le dossier `[AEM Forms as a Cloud Service repository folder]/apps/`. Par exemple, créez un dossier nommé comme `experience-league`
1. Accédez à `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/experience-league/` et créez un `ClientLibraryFolder` as `es6clientlibs`.
1. Ajout d’une propriété `categories`avec une valeur de type chaîne comme `es6customfunctions` à la fonction `es6clientlibs` dossier.

   >[!NOTE]
   >
   >`es6customfunctions`est un exemple de catégorie. Vous pouvez choisir n’importe quel nom pour la catégorie.

1. Créez un dossier nommé `js`.
1. Accédez au dossier `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/es6clientlibs/js`.
1. Ajoutez un fichier JavaScript, par exemple : `function.js`. Le fichier comprend le code de la fonction personnalisée.

   >[!NOTE]
   >
   >* Si le fichier JavaScript contenant du code pour les fonctions personnalisées comporte une erreur, les fonctions personnalisées ne sont pas répertoriées dans l’éditeur de règles d’un formulaire adaptatif. Vous pouvez également vérifier les `error.log` pour l’erreur.

   <!-- 
    >* AEM Adaptive Form supports the caching of custom functions. If the JavaScript is modified, the caching becomes invalidated, and it is parsed. You can see a message as `Fetched following custom functions list from cache` in the `error.log` file.  -->

1. Enregistrez le fichier `function.js`.
1. Accédez au dossier `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/es6clientlibs/js`.
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

Une fois le pipeline exécuté correctement, la fonction personnalisée ajoutée à la bibliothèque cliente devient disponible dans votre [Éditeur de règles de formulaire adaptatif](/help/forms/rule-editor.md).

### Ajout d’une bibliothèque cliente dans un formulaire adaptatif{#use-custom-function}

Après avoir ajouté votre bibliothèque cliente, utilisez-la dans votre formulaire adaptatif. Il vous permet d’utiliser votre [fonction personnalisée en tant que règle dans votre formulaire](/help/forms/rule-editor.md#custom-functions). Pour ajouter la bibliothèque cliente dans votre formulaire adaptatif :

1. Ouvrez votre formulaire en mode d’édition.
Pour ouvrir un formulaire en mode d’édition, sélectionnez-le, puis **[!UICONTROL Ouvrir]**.
1. En mode d’édition, sélectionnez un composant, puis sélectionnez ![champ-level](assets/select_parent_icon.svg) > **[!UICONTROL Conteneur de formulaires adaptatifs]**, puis sélectionnez ![cmppr](assets/configure-icon.svg).
1. Dans la barre latérale, sous Nom de bibliothèque cliente, ajoutez votre bibliothèque cliente. (`es6customfunctions` dans l’exemple).

   ![Ajout de la bibliothèque cliente de fonction personnalisée](/help/forms/assets/clientlib-custom-function.png)

Créez une règle pour utiliser une fonction personnalisée dans l’éditeur de règles.

<!--

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





