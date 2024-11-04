---
title: Comment utiliser des appels de fonction asynchrones dans l’éditeur de règles visuel ?
description: Appels de fonctions asynchrones dans l’éditeur de règles visuel
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
source-git-commit: f6e1de0c2cc2c056b3bfcea6ce5d7aaed041f6f8
workflow-type: tm+mt
source-wordcount: '1437'
ht-degree: 2%

---


# Utilisation de fonctions asynchrones dans un formulaire adaptatif basées sur des composants principaux

L’ [ éditeur de règles dans Adaptive Forms](/help/forms/rule-editor-core-components.md) prend en charge les fonctions asynchrones, ce qui vous permet d’intégrer et de gérer les opérations qui nécessitent l’attente de processus externes ou la récupération de données sans interrompre l’interaction de l’utilisateur avec le formulaire.

## Quels facteurs déterminent l’utilisation des fonctions asynchrones ou synchrones ?

La gestion efficace de l’interaction utilisateur est essentielle pour créer une expérience fluide. Les fonctions synchrones et asynchrones constituent deux approches courantes de gestion des opérations.

**Les fonctions synchrones** exécutent des tâches les unes après les autres, ce qui entraîne l’application à attendre que chaque opération se termine avant de continuer. Cela peut entraîner des retards et une expérience utilisateur moins attrayante, en particulier lorsque des tâches impliquent l’attente de ressources externes, telles que les chargements de fichiers ou la récupération de données.

Supposons, par exemple, qu’un utilisateur charge une image, que l’intégralité du formulaire s’arrête en attendant que le téléchargement soit terminé. Cette pause empêche l’utilisateur d’interagir avec d’autres champs, ce qui entraîne frustration et retards. Pendant qu’ils attendent que l’image soit traitée, toute information saisie peut être perdue s’ils s’éloignent ou s’ils perdent patience, ce qui rend l’expérience encombrante et inefficace.

En revanche, les **fonctions asynchrones** permettent aux tâches de s’exécuter simultanément. Cela signifie que les utilisateurs peuvent continuer à interagir avec l’application pendant l’exécution des processus en arrière-plan. Les opérations asynchrones améliorent la réactivité, ce qui permet aux utilisateurs de recevoir des commentaires immédiats et de maintenir l’engagement sans interruption.

Inversement, avec une approche asynchrone, les utilisateurs peuvent charger des images en arrière-plan tout en continuant à remplir le reste du formulaire de manière transparente. L’interface reste réactive, ce qui permet des mises à jour en temps réel et des commentaires immédiats au fur et à mesure du chargement. Cela améliore l’engagement des utilisateurs, assurant une expérience fluide sans interruption.

![Fonctions asynchrones et synchrones](/help/forms/assets/sync-async.png){align=center}

## Mise en oeuvre de fonctions asynchrones pour le Forms adaptatif

Vous pouvez implémenter les fonctions asynchrones pour Adaptive Forms à l’aide des types de règles suivants dans l’éditeur de règles :

* [Appel de fonction asynchrone](#using-asynchronous-function-calls-in-the-visual-rule-editor)
* [Sortie de fonction](#how-to-use-function-output-rule-type)

## Comment utiliser le type de règle Appel de fonction asynchrone ?

<span class="preview"> Il s’agit d’une fonctionnalité de préversion accessible par le biais de notre [canal de pré-version](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/release-notes/prerelease#new-features). </span>

Vous pouvez écrire les [fonctions personnalisées](/help/forms/custom-function-core-component-create-function.md) pour les opérations asynchrones et configurer les fonctions asynchrones à l’aide du type de règle **[!UICONTROL Appel de fonction asynchrone]** dans l’éditeur de règles.

### Exploration du type de règle Appel de fonction asynchrone via un cas d’utilisation

Envisagez un formulaire d’enregistrement sur un site web où les utilisateurs saisissent un mot de passe unique (OTP). Le panneau d’ajout de détails utilisateur s’affiche uniquement après avoir saisi le bon processus OTP. Si le protocole OTP est incorrect, le panneau reste masqué et un message d’erreur s’affiche à l’écran.

![Login-form](/help/forms/assets/rule-editor-login-form.png) {width-50%}

Dans un formulaire d’enregistrement, lorsque l’utilisateur clique sur le bouton **Confirmer** , la fonction `matchOTP()` est appelée de manière asynchrone pour vérifier l’OTP renseignée. La fonction `matchOTP()` est implémentée en tant que [fonction personnalisée](/help/forms/custom-function-core-component-create-function.md). En utilisant le type de règle **[!UICONTROL Appel de fonction asynchrone]** dans l’éditeur de règles, vous pouvez configurer la fonction `matchOTP()` dans l’éditeur de règles d’un formulaire adaptatif. Vous pouvez également implémenter les rappels de succès et d’échec dans l’éditeur de règles.

La figure suivante illustre les étapes à suivre pour utiliser le type de règle **[!UICONTROL Appel de fonction asynchrone]** pour appeler des fonctions asynchrones pour le Forms adaptatif :

![Workflow d’ajout de fonctions asynchrones](/help/forms/assets/workflow-to-add-async-func.png){width=50%, align=center}

### 1. Créez une fonction personnalisée pour l’opération asynchrone dans le fichier JS.

>[!NOTE]
>
> * L’éditeur de règles d’un formulaire affiche uniquement les fonctions avec un type de retour `Promise` lorsque vous sélectionnez le type de règle **Appel de fonction asynchrone**.
> * Pour savoir comment créer une fonction personnalisée, reportez-vous à l’article intitulé [Création d’une fonction personnalisée pour un formulaire adaptatif basé sur des composants principaux](/help/forms/custom-function-core-component-create-function.md).

La fonction `matchOTP()` est implémentée en tant que fonction personnalisée. Le code ci-dessous est ajouté dans le fichier JS de la fonction personnalisée :

```JavaScript
/**
 * generates the otp for success use case
 * @param {string} otp
 * @return {PROMISE}
 */
function matchOTP(otp) {
     return new Promise((resolve, reject) => {
        // Perform some asynchronous operation here
         asyncOperationForOTPMatch(otp, (error, result) => {
            if (error) {
                // On failure, call reject(error)
                reject(error);
            } else {
                // On success, call resolve(result)
                resolve(result);
            }
        });
    });
}

/**
 * generates the otp
 */
function asyncOperationForOTPMatch(otp, callback) {
    setTimeout(() => {
        if(otp === '111') {
            callback( null, {'valid':'true'});    
        } else {
            callback( {'valid':'false'}, null);
        }
    }, 1000);
}
```

Le code définit une fonction `matchOTP()` qui génère une promesse de validation asynchrone d’un mot de passe unique (OTP). Il utilise une fonction `asyncOperationForOTPMatch()` pour simuler le processus de correspondance OTP. La fonction vérifie si l’OTP fourni est égal à `111`. Si l’OTP saisi est correct, il appelle le rappel avec la valeur null pour l’erreur et un objet indiquant que l’OTP est valide `({'valid':'true'})`. Si l’OTP n’est pas valide, il appelle le rappel avec un objet d’erreur `({'valid':'false'})` et la valeur null pour le résultat.

### 2. Configuration de la fonction asynchrone dans l’éditeur de règles

Effectuez les étapes suivantes pour configurer une fonction asynchrone dans l’éditeur de règles :

1. [Créez une règle pour utiliser une fonction asynchrone à l’aide du type de règle d’appel de fonction asynchrone](#21-create-a-rule-to-use-asynchronous-function-using-the-async-function-call-rule-type)
1. [Mise en oeuvre des rappels pour la fonction asynchrone](#22-implement-the-callbacks-for-asynchronous-function)

#### 2.1 Création d’une règle pour utiliser une fonction asynchrone à l’aide du type de règle d’appel de fonction asynchrone

Pour créer une règle pour utiliser une opération asynchrone, utilisez le type de règle **[!UICONTROL Appel de fonction asynchrone]**, procédez comme suit :

1. Ouvrez un formulaire adaptatif en mode création, sélectionnez un composant de formulaire et sélectionnez **[!UICONTROL Éditeur de règles]** pour ouvrir ce dernier.
1. Sélectionnez **[!UICONTROL Créer]**.
1. Créez une condition dans la section **When** de la règle pour un clic sur un bouton. Par exemple, un clic est effectué sur **Lorsque[Confirmer]** est effectué.
1. Dans la section **Then** , sélectionnez **[!UICONTROL Async Function call]** dans la liste déroulante **Select Action** .
Lorsque vous sélectionnez **[!UICONTROL Appel de fonction asynchrone]** et que les fonctions avec le type de retour `Promise` s’affichent.
1. Sélectionnez la fonction asynchrone dans la liste. Par exemple, sélectionnez la fonction `matchOTP()` et ses rappels `Add success callback` et `add failure callback` apparaissent.
1. Sélectionnez maintenant les liaisons **[!UICONTROL Input]**. Par exemple, sélectionnez **[!UICONTROL Input]** comme `Form Object` et comparez-le au champ `OTP`.

La capture d’écran ci-dessous affiche la règle :

![type de règle](/help/forms/assets/asyn-function-rule-type.png)

Vous pouvez maintenant procéder à l’implémentation des rappels : `Success` et `Failure` pour la fonction `matchOTP`.

#### 2.2 Mise en oeuvre des rappels pour la fonction asynchrone

Implémentez les méthodes de rappel de succès et d’échec pour la fonction asynchrone à l’aide de l’éditeur de règles visuel.

**Créer une règle pour la méthode `Add Success callback`**

Créons une règle pour afficher le panneau `userdetails`, si l’OTP correspond à la valeur `111`.

1. Cliquez sur **[!UICONTROL Ajouter un rappel de succès]**.
1. Cliquez sur **[!UICONTROL Ajouter une instruction]** pour créer la règle.
1. Créez une condition dans la section **When** de la règle.
1. Sélectionnez la **[!UICONTROL sortie de fonction]** > **[!UICONTROL Get Event Payload]**.

   >[!NOTE]
   >
   > La fonction **[!UICONTROL Get Event Payload]** récupère les données associées à un événement spécifique pour gérer dynamiquement les interactions utilisateur.

1. Sélectionnez les liaisons correspondantes dans la section **Input** . Par exemple, sélectionnez **[!UICONTROL String]** et saisissez `valid`. Comparez la chaîne entrée à `true`.
1. Dans la section **Then** (Alors), sélectionnez **[!UICONTROL Show]** (Afficher) dans la liste déroulante **Select Action** (Sélectionner une action). Par exemple, affichez le panneau `userdetails`.
1. Cliquez sur **[!UICONTROL Ajouter une instruction]**.
1. Sélectionnez **[!UICONTROL Masquer]** dans la liste déroulante **Sélectionner une action**. Par exemple, masquez la zone de texte `error message`.
1. Cliquez sur **[!UICONTROL Terminé]**.

![Appel de succès](/help/forms/assets/rule-editor-success-callback.png){width=50%, height=50%}

Reportez-vous à la capture d’écran ci-dessous, où l’utilisateur accède à l’OTP sous la forme `111`, et où le panneau `User Details` s’affiche lorsque l’utilisateur clique sur le bouton `Confirm`.

![Succès](/help/forms/assets/success.gif)

**Créer une règle pour la méthode `Add Failure callback`**

Créons une règle pour afficher un message d’échec si l’OTP ne correspond pas à la valeur `111`.

1. Cliquez sur **[!UICONTROL Ajouter un rappel d’échec]**.

1. Cliquez sur **[!UICONTROL Ajouter une instruction]** pour créer la règle.
1. Créez une condition dans la section **When** de la règle.
1. Sélectionnez la **[!UICONTROL sortie de fonction]** > **[!UICONTROL Get Event Payload]**.
1. Sélectionnez les liaisons correspondantes dans la section **Input** . Par exemple, sélectionnez **[!UICONTROL String]** et saisissez `valid`. Comparez la chaîne entrée à `false`.
1. Dans la section **Then** (Alors), sélectionnez **[!UICONTROL Show]** (Afficher) dans la liste déroulante **Select Action** (Sélectionner une action). Par exemple, affichez la zone de texte `error message`.
1. Cliquez sur **[!UICONTROL Ajouter une instruction]**.
1. Sélectionnez **[!UICONTROL Masquer]** dans la liste déroulante **Sélectionner une action**. Par exemple, masquez le panneau `userdetails`.
1. Cliquez sur **[!UICONTROL Terminé]**.

![Méthode de rappel d’échec](/help/forms/assets/rule-editor-failure-callback.png){width=50%, height=50%}

Reportez-vous à la capture d’écran ci-dessous, où l’utilisateur saisit l’OTP comme `123`, et où le message d’erreur s’affiche lorsque l’utilisateur clique sur le bouton `Confirm`.

![Échec](/help/forms/assets/failure.gif)

La capture d’écran ci-dessous affiche la règle complète pour l’utilisation de l’**[!UICONTROL appel de fonction asynchrone]** afin de mettre en oeuvre une fonction asynchrone :

![Règle pour l’appel de fonction asynchrone](/help/forms/assets/rule-editor-async-callbacks.png)

Vous pouvez également modifier les rappels en cliquant sur **[!UICONTROL Modifier le rappel de succès]** et **[!UICONTROL Modifier le rappel d’échec]**.

## Comment utiliser le type de règle de sortie de fonction ?

Vous pouvez également appeler les fonctions asynchrones indirectement à l’aide des fonctions synchrones. Les fonctions synchrones sont exécutées à l’aide du type de règle **[!UICONTROL Sortie de fonction]** dans l’éditeur de règles d’un formulaire adaptatif.

Consultez le code ci-dessous pour découvrir comment appeler des fonctions asynchrones à l’aide du type de règle **[!UICONTROL Function Output]** :

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

Pour en voir le fonctionnement, ajoutons un bouton et créons une règle pour le bouton qui appelle la fonction asynchrone lors d’un clic sur un bouton.

![création d’une règle pour la fonction asynchrone](/help/forms/assets/rule-for-async-funct.png){width=50%}

Reportez-vous à la capture d’écran de la fenêtre de console ci-dessous pour démontrer que lorsque l’utilisateur clique sur le bouton `Fetch`, la fonction personnalisée `callAsyncFunction` est appelée, ce qui à son tour appelle une fonction asynchrone `asyncFunction`. Inspect dans la fenêtre de la console pour afficher la réponse à un clic sur le bouton :

![Fenêtre de console](/help/forms/assets/async-custom-funct-console.png)

## Voir également

{{see-also-rule-editor}}