---
title: Utilisation de fonctions personnalisées dans un formulaire adaptatif
description: AEM Forms prend en charge les fonctions personnalisées, qui permettent aux utilisateurs de créer et d’utiliser leurs propres fonctions dans l’éditeur de règles.
keywords: Ajoutez une fonction personnalisée, utilisez une fonction personnalisée, créez une fonction personnalisée, utilisez une fonction personnalisée dans l’éditeur de règles.
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Core Components
exl-id: 24607dd1-2d65-480b-a831-9071e20c473d
role: User, Developer
source-git-commit: fecbebde808c545a84889da5610a79c088f2f459
workflow-type: tm+mt
source-wordcount: '1286'
ht-degree: 54%

---


# Présentation des fonctions personnalisées des formulaires adaptatifs basés sur les composants principaux

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/adaptive-forms-core-components/create-and-use-custom-functions-core-components) |
| AEM as a Cloud Service | Cet article |

AEM Forms prend en charge des fonctions personnalisées, ce qui permet aux utilisateurs et utilisatrices de définir des fonctions JavaScript pour implémenter des règles métier complexes. Ces fonctions personnalisées étendent les fonctionnalités des formulaires en facilitant la manipulation et le traitement des données saisies afin de répondre à des exigences spécifiques. Ils permettent de modifier dynamiquement le comportement du formulaire en fonction de critères prédéfinis. Les fonctions personnalisées permettent également aux développeurs et développeuses d’appliquer une logique de validation complexe, d’effectuer des calculs dynamiques et de contrôler l’affichage ou le comportement des éléments de formulaire en fonction des interactions utilisateur ou de critères prédéfinis.

>[!NOTE]
>
> Assurez-vous que le [composant principal](https://github.com/adobe/aem-core-forms-components) est défini sur la dernière version pour utiliser les dernières fonctionnalités.

## Utilisations des fonctions personnalisées {#uses-of-custom-function}

Les avantages des fonctions personnalisées dans les formulaires adaptatifs sont les suivants :
* **Traitement des données** : les fonctions personnalisées aident à traiter les données saisies dans les champs de formulaires.
* **Validation des données** : les fonctions personnalisées vous permettent d’effectuer des vérifications personnalisées sur les entrées de formulaire et de fournir des messages d’erreur spécifiés.
* **Comportement dynamique** : les fonctions personnalisées vous permettent de contrôler le comportement dynamique de vos formulaires en fonction de conditions spécifiques. Vous pouvez, par exemple, afficher/masquer des champs, modifier les valeurs de champ ou ajuster dynamiquement la logique du formulaire.
* **Intégration** : vous pouvez utiliser des fonctions personnalisées pour intégrer des API ou des services externes. Cela permet de récupérer des données provenant de sources externes, d’envoyer des données à des points d’entrée Rest externes ou d’effectuer des actions personnalisées basées sur des événements externes.

Les fonctions personnalisées sont essentiellement des bibliothèques clientes ajoutées dans le fichier JavaScript. Une fois que vous avez créé une fonction personnalisée, elle devient disponible dans l’éditeur de règles pour être sélectionnée par l’utilisateur dans un formulaire adaptatif. Les fonctions personnalisées sont identifiées par les annotations JavaScript dans l’éditeur de règles.

## Annotations JavaScript prises en charge pour la fonction personnalisée {#js-annotations}

Les annotations JavaScript sont utilisées pour fournir des métadonnées pour le code JavaScript. Il comprend des commentaires commençant par des symboles spécifiques, par exemple /** et @. Les annotations fournissent des informations importantes sur les fonctions, variables et autres éléments du code. Le formulaire adaptatif prend en charge les annotations JavaScript suivantes pour les fonctions personnalisées :

### Nom

Le nom est utilisé pour identifier la fonction personnalisée dans l’éditeur de règles d’un formulaire adaptatif. Les syntaxes suivantes sont utilisées pour nommer une fonction personnalisée :

* `@name [functionName] <Function Name>`
* `@function [functionName] <Function Name>`
* `@func [functionName] <Function Name>`.
  `functionName` est le nom de la fonction. Les espaces ne sont pas autorisés.
  `<Function Name>` est le nom d’affichage de la fonction dans l’éditeur de règles d’un formulaire adaptatif.
Si le nom de la fonction est identique au nom de la fonction elle-même, vous pouvez omettre `[functionName]` dans la syntaxe.

### Paramètre

Le paramètre est une liste d’arguments utilisés par des fonctions personnalisées. Une fonction peut prendre en charge plusieurs paramètres. Les syntaxes suivantes sont utilisées pour définir un paramètre dans une fonction personnalisée :

* `@param {type} name <Parameter Description>`
* `@argument` `{type} name <Parameter Description>`
* `@arg` `{type}` `name <Parameter Description>`.
  `{type}` représente le type de paramètre.  Les types de paramètre autorisés sont les suivants :

   * Chaîne : représente une seule valeur de chaîne.
   * Nombre : représente une seule valeur numérique.
   * Booléen : représente une seule valeur booléenne (true ou false).
   * Chaîne[] : représente un tableau de valeurs de chaîne.
   * Nombre[] : représente un tableau de valeurs numériques.
   * Booléen[] : représente un tableau de valeurs booléennes.
   * Date : représente une seule valeur de date.
   * Date[] : représente un tableau de valeurs de date.
   * array : représente un tableau générique contenant des valeurs de différents types.
   * object : représente l’objet de formulaire transmis à une fonction personnalisée au lieu de transmettre directement sa valeur.
   * portée : représente l’objet global, qui contient des variables en lecture seule telles que des instances de formulaire, des instances de champ cible et des méthodes permettant d’effectuer des modifications de formulaire dans des fonctions personnalisées. Il est déclaré comme le dernier paramètre dans les annotations JavaScript et n’est pas visible dans l’éditeur de règles d’un formulaire adaptatif. Le paramètre scope accède à l’objet du formulaire ou du composant pour déclencher la règle ou l’événement requis pour le traitement du formulaire. Pour plus d&#39;informations sur l&#39;objet Globals et son utilisation, [cliquez ici](/help/forms/custom-function-core-component-scope-function.md).

Le type de paramètre n’est pas sensible à la casse et les espaces ne sont pas autorisés dans le nom du paramètre.

`<Parameter Description>` contient des détails sur l’objectif du paramètre. Il peut contenir plusieurs mots.

#### Paramètres facultatifs

Par défaut, tous les paramètres sont obligatoires. Vous pouvez définir un paramètre comme facultatif en ajoutant `=` après le type de paramètre ou en encadrant le nom du paramètre dans `[]`. Les paramètres définis comme facultatifs dans les annotations JavaScript sont affichés comme facultatifs dans l’éditeur de règles.
Pour définir une variable comme paramètre facultatif, vous pouvez utiliser l’une des syntaxes suivantes :

* `@param {type=} Input1`

Dans la ligne de code ci-dessus, `Input1` est un paramètre facultatif sans valeur par défaut. Pour déclarer un paramètre facultatif avec la valeur par défaut :
`@param {string=<value>} input1`

`input1` comme paramètre facultatif avec la valeur par défaut définie sur `value`.

* `@param {type} [Input1]`

Dans la ligne de code ci-dessus, `Input1` est un paramètre facultatif sans valeur par défaut. Pour déclarer un paramètre facultatif avec la valeur par défaut :
`@param {array} [input1=<value>]`
`input1` est un paramètre facultatif de type tableau dont la valeur par défaut est définie sur `value`.
Assurez-vous que le type de paramètre est placé entre crochets {} et que le nom du paramètre est placé entre crochets.

Tenez compte du fragment de code suivant, où input2 est défini comme un paramètre facultatif :

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

![Paramètres facultatifs ou obligatoires ](/help/forms/assets/optional-default-params.png)

Vous pouvez enregistrer la règle sans spécifier de valeur pour les paramètres requis, mais la règle n’est pas exécutée et affiche un message d’avertissement comme suit :

![avertissement de règle incomplète](/help/forms/assets/incomplete-rule.png)

Lorsque l’utilisateur ou l’utilisatrice laisse le paramètre facultatif vide, la valeur « Non défini » est transmise à la fonction personnalisée pour le paramètre facultatif.

Pour en savoir plus sur la définition de paramètres facultatifs dans les JSDocs, [cliquez ici](https://jsdoc.app/tags-param).

### Type de retour

Le type de retour spécifie le type de valeur que la fonction personnalisée renvoie après l’exécution. Les syntaxes suivantes sont utilisées pour définir un type de retour dans une fonction personnalisée :

* `@return {type}`
* `@returns {type}`
  `{type}` représente le type de retour de la fonction. Les types de retour autorisés sont les suivants :
   * Chaîne : représente une seule valeur de chaîne.
   * Nombre : représente une seule valeur numérique.
   * Booléen : représente une seule valeur booléenne (true ou false).
   * Chaîne[] : représente un tableau de valeurs de chaîne.
   * Nombre[] : représente un tableau de valeurs numériques.
   * Booléen[] : représente un tableau de valeurs booléennes.
   * Date : représente une seule valeur de date.
   * Date[] : représente un tableau de valeurs de date.
   * array : représente un tableau générique contenant des valeurs de différents types.
   * object : représente l’objet de formulaire au lieu de sa valeur directement.

  Le type de retour ne respecte pas la casse.

### Privée

La fonction personnalisée déclarée privée n’apparaît pas dans la liste des fonctions personnalisées de l’éditeur de règles d’un formulaire adaptatif. Par défaut, les fonctions personnalisées sont publiques. La syntaxe pour déclarer une fonction personnalisée en tant que privée est `@private`.


## Instructions relatives à la création de fonctions personnalisées

Pour répertorier les fonctions personnalisées dans l’éditeur de règles, vous pouvez utiliser l’un des formats suivants :

### Instruction de fonction avec ou sans commentaires jsdoc

Vous pouvez créer une fonction personnalisée avec ou sans commentaires jsdoc.

```javascript
    function functionName(parameters) 
        {
            // code to be executed
        }
```
Si l’utilisateur ou l’utilisatrice n’ajoute aucune annotation JavaScript à la fonction personnalisée, elle est répertoriée dans l’éditeur de règles par son nom de fonction. Toutefois, il est recommandé d’inclure des annotations JavaScript pour améliorer la lisibilité des fonctions personnalisées.

### Fonction arrow avec annotations ou commentaire JavaScript obligatoires

Vous pouvez créer une fonction personnalisée à l’aide d’une syntaxe de fonction arrow :

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

Si l’utilisateur ou l’utilisatrice n’ajoute aucune annotation JavaScript à la fonction personnalisée, celle-ci n’est pas répertoriée dans l’éditeur de règles d’un formulaire adaptatif.

### Expression de fonction avec annotations ou commentaire JavaScript obligatoires

Pour répertorier les fonctions personnalisées dans l’éditeur de règles d’un formulaire adaptatif, créez des fonctions personnalisées au format suivant :

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

Si l’utilisateur ou l’utilisatrice n’ajoute aucune annotation JavaScript à la fonction personnalisée, celle-ci n’est pas répertoriée dans l’éditeur de règles d’un formulaire adaptatif.

## Étape suivante

Pour créer et utiliser une fonction personnalisée dans votre formulaire adaptatif, reportez-vous à l’article [Création d’une fonction personnalisée pour un formulaire adaptatif basé sur des composants principaux](/help/forms/custom-function-core-component-create-function.md).

## Voir également

{{see-also-rule-editor}}