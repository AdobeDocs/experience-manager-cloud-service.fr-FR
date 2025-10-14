---
title: Comment utiliser les appels de fonction asynchrones dans l’éditeur de règles visuel ?
description: Appels de fonctions asynchrones dans l’éditeur de règles visuel
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
exl-id: a240ba26-a6d8-4643-8acb-1d8812dac61f
source-git-commit: 2cae8bb1050bc4538f4645d9f064b227fb947d75
workflow-type: tm+mt
source-wordcount: '1409'
ht-degree: 7%

---

# Utilisation de fonctions asynchrones dans un formulaire adaptatif basé sur les composants principaux

L’éditeur de règles [&#x200B; d’Adaptive Forms](/help/forms/rule-editor-core-components.md) prend en charge les fonctions asynchrones, ce qui vous permet d’intégrer et de gérer les opérations qui nécessitent d’attendre des processus externes ou la récupération de données sans interrompre l’interaction de l’utilisateur avec le formulaire.

## Quels facteurs déterminent l’utilisation des fonctions asynchrones ou synchrones ?

Une gestion efficace des interactions utilisateur est essentielle pour créer une expérience fluide. Les fonctions synchrones et asynchrones constituent deux approches courantes de la gestion des opérations.

**Fonctions synchrones** exécutent des tâches l’une après l’autre, ce qui entraîne l’attente de l’application pour chaque opération avant de continuer. Cela peut entraîner des retards et une expérience utilisateur moins attrayante, en particulier lorsque les tâches impliquent l’attente de ressources externes, telles que le chargement de fichiers ou la récupération de données.

Supposons, par exemple, qu’un utilisateur charge une image et que l’ensemble du formulaire s’arrête en attendant la fin du chargement. Cette interruption empêche l’utilisateur d’interagir avec d’autres champs, ce qui entraîne une frustration et des retards. En attendant que l’image soit traitée, toute information saisie peut être perdue si la personne quitte la zone ou perd patience, ce qui rend l’expérience lourde et inefficace.

**Les fonctions asynchrones**, en revanche, permettent l’exécution simultanée de tâches. Cela signifie que les utilisateurs peuvent continuer à interagir avec l’application pendant l’exécution des processus en arrière-plan. Les opérations asynchrones améliorent la réactivité, ce qui permet aux utilisateurs de recevoir des commentaires immédiats et de maintenir l’engagement sans interruption.

Inversement, avec une approche asynchrone, les utilisateurs peuvent charger des images en arrière-plan tout en continuant à remplir le reste du formulaire de manière transparente. L’interface reste réactive, ce qui permet des mises à jour en temps réel et des commentaires immédiats au fur et à mesure de la progression du chargement. Il améliore l’interaction client, assurant ainsi une expérience fluide et sans interruptions.

![&#x200B; Fonctions asynchrones et synchrones &#x200B;](/help/forms/assets/sync-async.png){align=center}

## Mise en œuvre de fonctions asynchrones pour le Forms adaptatif

Vous pouvez implémenter les fonctions asynchrones pour le Forms adaptatif à l’aide des types de règles suivants dans l’éditeur de règles :

* [Appel de fonction asynchrone](#using-asynchronous-function-calls-in-the-visual-rule-editor)
* [Sortie de fonction](#how-to-use-function-output-rule-type)

## Comment utiliser le type de règle Appel de fonction asynchrone ?

Vous pouvez écrire les [fonctions personnalisées](/help/forms/custom-function-core-component-create-function.md) pour les opérations asynchrones et configurer les fonctions asynchrones à l’aide du type de règle **[!UICONTROL Appel de fonction asynchrone]** dans l’éditeur de règles.

### Exploration du type de règle Appel de fonction asynchrone via un cas d’utilisation

Prenons l’exemple d’un formulaire d’enregistrement sur un site web dans lequel les utilisateurs saisissent un mot de passe à usage unique (OTP). Le panneau permettant d’ajouter des détails utilisateur ne s’affiche qu’après avoir saisi le mot de passe à usage unique approprié. Si le mot de passe à usage unique est incorrect, le panneau reste masqué et un message d’erreur apparaît à l’écran.

![Formulaire de connexion](/help/forms/assets/rule-editor-login-form.png) {width-50%}

Dans un formulaire d’enregistrement, lorsque l’utilisateur clique sur le bouton **Confirmer**, la fonction `matchOTP()` est appelée de manière asynchrone pour vérifier le mot de passe à usage unique saisi. La fonction `matchOTP()` est implémentée en tant que [&#x200B; fonction personnalisée &#x200B;](/help/forms/custom-function-core-component-create-function.md). À l’aide du type de règle **[!UICONTROL Appel de fonction asynchrone]** dans l’éditeur de règles, vous pouvez configurer la fonction `matchOTP()` dans l’éditeur de règles d’un formulaire adaptatif. Vous pouvez également implémenter les rappels de succès et d’échec dans l’éditeur de règles.

La figure suivante illustre les étapes à suivre pour utiliser le type de règle **[!UICONTROL Appel de fonction asynchrone]** afin d’appeler des fonctions asynchrones pour le Forms adaptatif :

![Workflow d’ajout de fonctions asynchrones](/help/forms/assets/workflow-to-add-async-func.png){width=50%, align=center}

### 1. Écrivez une fonction personnalisée pour l’opération asynchrone dans le fichier JS

>[!NOTE]
>
> * L’éditeur de règles d’un formulaire affiche uniquement les fonctions avec un type de retour de `Promise` lorsque vous sélectionnez le type de règle **Appel de fonction asynchrone**.
> * Pour savoir comment créer une fonction personnalisée, reportez-vous à l’article intitulé [&#x200B; Création d’une fonction personnalisée pour un formulaire adaptatif basé sur des composants principaux &#x200B;](/help/forms/custom-function-core-component-create-function.md).

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

Le code définit une `matchOTP()` de fonction qui génère une promesse de validation d’un mot de passe à usage unique (OTP) de manière asynchrone. Il utilise une fonction `asyncOperationForOTPMatch()` pour simuler le processus de correspondance OTP. La fonction vérifie si le mot de passe à usage unique fourni est égal à `111`. Si le mot de passe à usage unique entré est correct, il appelle le rappel avec la valeur null pour l’erreur et un objet indiquant que le mot de passe à usage unique est valide `({'valid':'true'})`. Si le mot de passe à usage unique n’est pas valide, il appelle le rappel avec un objet d’erreur `({'valid':'false'})` et la valeur null pour le résultat.

### 2. Configuration de la fonction asynchrone dans l’éditeur de règles

Pour configurer la fonction asynchrone dans l’éditeur de règles, procédez comme suit :

1. [Créez une règle pour utiliser la fonction asynchrone à l’aide du type de règle d’appel de fonction asynchrone](#21-create-a-rule-to-use-asynchronous-function-using-the-async-function-call-rule-type)
1. [Implémentez les rappels pour la fonction asynchrone](#22-implement-the-callbacks-for-asynchronous-function)

#### 2.1 Créer une règle pour utiliser la fonction asynchrone à l’aide du type de règle d’appel de fonction asynchrone

Pour créer une règle permettant d’utiliser une opération asynchrone à l’aide du type de règle **[!UICONTROL Appel de fonction asynchrone]**, procédez comme suit :

1. Ouvrez un formulaire adaptatif en mode création, sélectionnez un composant de formulaire et sélectionnez **[!UICONTROL Éditeur de règles]** pour ouvrir ce dernier.
1. Sélectionnez **[!UICONTROL Créer]**.
1. Créez une condition dans la section **Quand** de la règle pour un clic sur un bouton. Par exemple, l’utilisateur clique sur **Lorsque[Confirmer]**.
1. Dans la section **Then**, sélectionnez **[!UICONTROL Async Function call]** dans la liste déroulante **Select Action**.
Lorsque vous sélectionnez **[!UICONTROL Appel de fonction asynchrone]** et les fonctions avec le type de retour `Promise` s’affichent.
1. Sélectionnez la fonction asynchrone dans la liste. Par exemple, sélectionnez la fonction `matchOTP()` et ses rappels au fur et à mesure que `Add success callback` et `add failure callback` apparaissent.
1. Sélectionnez maintenant les liaisons **[!UICONTROL Entrée]**. Par exemple, sélectionnez **[!UICONTROL Entrée]** comme `Form Object` et comparez-le au champ `OTP`.

La capture d’écran ci-dessous affiche la règle :

![&#x200B; type de règle &#x200B;](/help/forms/assets/asyn-function-rule-type.png)

Vous pouvez maintenant procéder à l’implémentation des rappels : `Success` et `Failure` pour la fonction `matchOTP` .

#### 2.2 Implémenter les rappels pour la fonction asynchrone

Implémentez les méthodes de rappel de succès et d’échec pour la fonction asynchrone à l’aide de l’éditeur de règles visuel.

**Créer une règle pour `Add Success callback` méthode**

Créons une règle pour afficher le panneau `userdetails`, si le mot de passe à usage unique correspond à la valeur `111`.

1. Cliquez sur **[!UICONTROL Ajouter un rappel de succès]**.
1. Cliquez sur **[!UICONTROL Ajouter une instruction]** pour créer la règle.
1. Créez une condition dans la section **Quand** de la règle.
1. Sélectionnez la **[!UICONTROL Sortie de fonction]** > **[!UICONTROL Obtenir la payload d’événement]**.

   >[!NOTE]
   >
   > La fonction **[!UICONTROL Get Event Payload]** récupère les données associées à un événement spécifique pour gérer dynamiquement les interactions utilisateur.

1. Sélectionnez ses liaisons correspondantes dans la section **Entrée**. Par exemple, sélectionnez **[!UICONTROL Chaîne]** et saisissez `valid`. Comparez la chaîne saisie à la chaîne `true`.
1. Dans la section **Alors**, sélectionnez **[!UICONTROL Afficher]** dans la liste déroulante **Sélectionner une action**. Par exemple, affichez le panneau `userdetails`.
1. Cliquez sur **[!UICONTROL Ajouter une instruction]**.
1. Sélectionnez **[!UICONTROL Masquer]** dans la liste déroulante **Sélectionner une action**. Par exemple, masquez la zone de texte `error message`.
1. Cliquez sur **[!UICONTROL Terminé]**.

![Appel de succès](/help/forms/assets/rule-editor-success-callback.png){width=50%, height=50%}

Reportez-vous à la capture d’écran ci-dessous, dans laquelle l’utilisateur saisit le mot de passe à usage unique comme `111`, et le panneau `User Details` s’affiche lorsque l’on clique sur le bouton `Confirm`.

![Succès](/help/forms/assets/success.gif)

**Créer une règle pour `Add Failure callback` méthode**

Créons une règle pour afficher un message d’échec si le mot de passe à usage unique ne correspond pas à la valeur `111`.

1. Cliquez sur **[!UICONTROL Ajouter un rappel d’échec]**.

1. Cliquez sur **[!UICONTROL Ajouter une instruction]** pour créer la règle.
1. Créez une condition dans la section **Quand** de la règle.
1. Sélectionnez la **[!UICONTROL Sortie de fonction]** > **[!UICONTROL Obtenir la payload d’événement]**.
1. Sélectionnez ses liaisons correspondantes dans la section **Entrée**. Par exemple, sélectionnez **[!UICONTROL Chaîne]** et saisissez `valid`. Comparez la chaîne saisie à la chaîne `false`.
1. Dans la section **Alors**, sélectionnez **[!UICONTROL Afficher]** dans la liste déroulante **Sélectionner une action**. Par exemple, affichez la zone de texte `error message`.
1. Cliquez sur **[!UICONTROL Ajouter une instruction]**.
1. Sélectionnez **[!UICONTROL Masquer]** dans la liste déroulante **Sélectionner une action**. Par exemple, masquez le panneau `userdetails`.
1. Cliquez sur **[!UICONTROL Terminé]**.

![Méthode de rappel d’échec](/help/forms/assets/rule-editor-failure-callback.png){width=50%, height=50%}

Reportez-vous à la capture d’écran ci-dessous, dans laquelle l’utilisateur saisit le mot de passe à usage unique comme `123`, et le message d’erreur s’affiche lorsque l’utilisateur clique sur le bouton `Confirm`.

![Échec](/help/forms/assets/failure.gif)

La capture d’écran ci-dessous affiche la règle complète pour utiliser **[!UICONTROL Appel de fonction asynchrone]** afin d’implémenter une fonction asynchrone :

![&#x200B; Règle pour l’appel de fonction asynchrone &#x200B;](/help/forms/assets/rule-editor-async-callbacks.png)

Vous pouvez également modifier les rappels en cliquant sur **[!UICONTROL Modifier le rappel de succès]** et **[!UICONTROL Modifier le rappel d’échec]**.

## Comment utiliser le type de règle Sortie de fonction ?

Vous pouvez également appeler les fonctions asynchrones indirectement à l’aide des fonctions synchrones. Les fonctions synchrones sont exécutées à l’aide du type de règle **[!UICONTROL Sortie de fonction]** dans l’éditeur de règles d’un formulaire adaptatif.

Consultez le code ci-dessous pour savoir comment appeler des fonctions asynchrones à l’aide du type de règle **[!UICONTROL Sortie de fonction]** :

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

Dans l’exemple ci-dessus, la fonction asyncFunction est une `asynchronous function`. Elle effectue une opération asynchrone en effectuant une requête `GET` vers `https://petstore.swagger.io/v2/store/inventory`. Elle attend la réponse avec `await`, analyse le corps de la réponse en tant que JSON à l’aide de `response.json()`, puis renvoie les données. La fonction `callAsyncFunction` est une fonction personnalisée synchrone qui appelle la fonction `asyncFunction` et affiche les données de réponse dans la console. Bien que la fonction `callAsyncFunction` soit synchrone, elle appelle la fonction asynchrone asyncFunction et gère son résultat avec des instructions `then` et `catch`.

Pour voir s’il fonctionne, nous allons ajouter un bouton et créer une règle pour le bouton qui appelle la fonction asynchrone lors d’un clic sur un bouton.

![Création d’une règle pour la fonction asynchrone](/help/forms/assets/rule-for-async-funct.png){width=50%}

Reportez-vous à la capture d’écran de la fenêtre de la console ci-dessous pour démontrer que lorsque l’utilisateur clique sur le bouton `Fetch` , le `callAsyncFunction` de fonction personnalisée est appelé, ce qui appelle à son tour un `asyncFunction` de fonction asynchrone. Inspectez la fenêtre de la console pour afficher la réponse au clic sur le bouton :

![Fenêtre de console](/help/forms/assets/async-custom-funct-console.png)

## Voir également

{{see-also-rule-editor}}
