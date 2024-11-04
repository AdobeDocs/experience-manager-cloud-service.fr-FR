---
title: Cet article décrit divers cas d’utilisation d’une fonction personnalisée dans un formulaire adaptatif en fonction des composants principaux.
description: L’article décrit différents cas d’utilisation d’une fonction personnalisée dans un formulaire adaptatif en fonction des composants principaux. Les fonctions personnalisées sont utilisées dans l’éditeur de règles pour créer des règles personnalisées pour le formulaire.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
exl-id: df92b91e-f3b0-4a08-bd40-e99edc9a50a5
source-git-commit: 747203ccd3c7e428e2afe27c56e47c3ec18699f6
workflow-type: tm+mt
source-wordcount: '2108'
ht-degree: 0%

---

# Exemples de développement et d’utilisation d’une fonction personnalisée

L’article fournit des exemples détaillés de fonctions personnalisées pour un formulaire adaptatif basées sur des composants principaux, offrant des informations précieuses sur leur mise en oeuvre efficace dans divers scénarios. Les fonctions personnalisées sont utilisées dans l’éditeur de règles d’AEM Forms pour permettre aux développeurs de définir et de contrôler la logique qui régit le comportement des formulaires.
Cet article explore différentes mises en oeuvre de fonctions personnalisées, expliquant comment elles peuvent être utilisées pour personnaliser les formulaires en fonction de besoins spécifiques et améliorer les fonctionnalités globales.

## Définition des options de liste déroulante à l’aide de fonctions personnalisées

L’éditeur de règles dans les composants principaux ne prend pas en charge la propriété **Set Options of** pour définir les options de liste déroulante au moment de l’exécution. Vous pouvez toutefois définir les options de liste déroulante à l’aide de fonctions personnalisées.

Ajoutez le code suivant dans la fonction personnalisée, comme expliqué dans la section [create-custom-function](/help/forms/custom-function-core-component-create-function.md) pour définir les options de liste déroulante à l’aide de fonctions personnalisées :

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

## Afficher un panneau à l’aide de la règle `SetProperty`

Découvrez comment les fonctions personnalisées utilisent les objets de champ et globaux à l’aide d’un formulaire `Contact Us`.

![Formulaire de contact](/help/forms/assets/contact-us-form.png)

Ajoutez le code suivant dans la fonction personnalisée, comme expliqué dans la section [create-custom-function](/help/forms/custom-function-core-component-create-function.md), pour définir le champ de formulaire comme `Required`.

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

## Valider le champ

Découvrez comment les fonctions personnalisées utilisent des objets de champ et globaux pour valider le champ à l’aide d’un formulaire `Contact Us`.

Ajoutez le code suivant dans la fonction personnalisée, comme expliqué dans la section [create-custom-function](/help/forms/custom-function-core-component-create-function.md) , pour valider le champ.

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

## Réinitialisation d’un panneau

Découvrez comment les fonctions personnalisées utilisent des objets de champ et globaux pour réinitialiser le champ à l’aide d’un formulaire `Contact Us`.

Ajoutez le code suivant dans la fonction personnalisée, comme expliqué dans la section [create-custom-function](/help/forms/custom-function-core-component-create-function.md) , pour réinitialiser le panneau.

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

## Pour afficher un message personnalisé au niveau du champ et marquer le champ comme non valide

Découvrez comment les fonctions personnalisées utilisent des objets de champ et globaux pour afficher un message personnalisé au niveau du champ et marquer le champ comme non valide à l’aide d’un formulaire `Contact Us`.

Vous pouvez utiliser la fonction `markFieldAsInvalid()` pour définir un champ comme non valide et définir un message d’erreur personnalisé au niveau du champ. La valeur `fieldIdentifier` peut être `fieldId`, `field qualifiedName` ou `field dataRef`. La valeur de l’objet nommé `option` peut être `{useId: true}`, `{useQualifiedName: true}` ou `{useDataRef: true}`.
Les syntaxes utilisées pour marquer un champ comme non valide et définir un message personnalisé sont les suivantes :

* `globals.functions.markFieldAsInvalid(field.$id,"[custom message]",{useId: true});`
* `globals.functions.markFieldAsInvalid(field.$qualifiedName, "[custom message]", {useQualifiedName: true});`
* `globals.functions.markFieldAsInvalid(field.$dataRef, "[custom message]", {useDataRef: true});`

Ajoutez le code suivant dans la fonction personnalisée, comme expliqué dans la section [create-custom-function](/help/forms/custom-function-core-component-create-function.md), pour activer un message personnalisé au niveau du champ.

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

## Envoi des données modifiées au serveur

Découvrez comment les fonctions personnalisées utilisent des objets de champ et globaux pour envoyer des données manipulées sur le serveur à l’aide d’un formulaire `Contact Us`.

La ligne de code suivante :
`globals.functions.submitForm(globals.functions.exportData(), false);` est utilisé pour envoyer les données de formulaire après la manipulation.
* Le premier argument est celui des données à soumettre.
* Le deuxième argument indique si le formulaire doit être validé avant envoi. Il est `optional` et est défini sur `true` par défaut.
* Le troisième argument est le `contentType` de l’envoi, qui est également facultatif avec la valeur par défaut `multipart/form-data`. Les autres valeurs peuvent être `application/json` et `application/x-www-form-urlencoded`.

Ajoutez le code suivant dans la fonction personnalisée, comme expliqué dans la section [create-custom-function](/help/forms/custom-function-core-component-create-function.md) , pour envoyer les données manipulées sur le serveur :

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

## Remplacer le succès d’envoi du formulaire et les gestionnaires d’erreurs

Découvrez comment les fonctions personnalisées utilisent les objets de champ et globaux pour remplacer les gestionnaires d’envoi à l’aide d’un formulaire `Contact Us`.

Ajoutez la ligne de code suivante, comme expliqué dans la section [create-custom-fonctionnalités](/help/forms/custom-function-core-component-create-function.md), pour personnaliser le message d’envoi ou d’échec pour les envois de formulaire et afficher les messages d’envoi de formulaire dans une zone modale :

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

## Exécution d’actions dans une instance spécifique du panneau répétable

Les règles créées à l’aide de l’éditeur de règles visuel sur un panneau répétable s’appliquent à la dernière instance du panneau répétable. Pour écrire une règle pour une instance spécifique du panneau répétable, nous pouvons utiliser une fonction personnalisée.

Créons un autre formulaire sous la forme `Booking Form` pour collecter des informations sur les voyageurs se dirigeant vers une destination. Un panneau du voyageur est ajouté en tant que panneau répétable, où l’utilisateur peut ajouter des détails pour 5 voyageurs à l’aide du bouton `Add Traveler`.

![Informations sur le voyageur](/help/forms/assets/traveler-info-form.png)

Ajoutez la ligne de code suivante, comme expliqué dans la section [create-custom-function](/help/forms/custom-function-core-component-create-function.md) , pour effectuer des actions dans une instance spécifique du panneau répétable, autre que la dernière :

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

## Préremplir le champ avec une valeur au chargement du formulaire

Découvrez comment les fonctions personnalisées utilisent des objets de champ et globaux pour préremplir un champ à l’aide d’un `Booking Form`.

Ajoutez la ligne de code suivante, comme expliqué dans la section [create-custom-function](/help/forms/custom-function-core-component-create-function.md) , pour charger la valeur prérenseignée dans un champ lorsque le formulaire est initialisé :

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

## Définir la cible d’action sur le champ spécifique

Découvrez comment les fonctions personnalisées utilisent les objets de champ et globaux pour définir le focus sur des champs spécifiques avec l’aide d’un `Booking Form`.

Ajoutez la ligne de code suivante, comme expliqué dans la section [create-custom-function](/help/forms/custom-function-core-component-create-function.md), pour définir la cible d’action sur le champ spécifié lorsque l’utilisateur clique sur le bouton `Submit` :

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

## Ajouter ou supprimer un panneau répétable à l’aide de la propriété `dispatchEvent`

Découvrez comment les fonctions personnalisées utilisent des objets de champ et globaux pour ajouter ou supprimer un panneau répétable à l’aide de la propriété `dispatchEvent` avec l’aide d’un `Booking Form`.

Ajoutez la ligne de code suivante, comme expliqué dans la section [create-custom-function](/help/forms/custom-function-core-component-create-function.md) , pour ajouter un panneau lorsque l’utilisateur clique sur le bouton `Add Traveler` à l’aide de la propriété `dispatchEvent` :

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


## Résolution des problèmes

* Si le gestionnaire d’envoi personnalisé ne fonctionne pas comme prévu dans AEM projets ou formulaires existants, procédez comme suit :
   * Assurez-vous que la version des [composants principaux est mise à jour vers la version 3.0.18 et ultérieure](https://github.com/adobe/aem-core-forms-components). Toutefois, pour les projets et les formulaires AEM existants, les étapes suivantes sont nécessaires :

   * Pour le projet AEM, l’utilisateur doit remplacer toutes les instances de `submitForm('custom:submitSuccess', 'custom:submitError')` par `submitForm()` et déployer le projet via le pipeline Cloud Manager.

   * Pour les formulaires existants, si les gestionnaires d’envoi personnalisés ne fonctionnent pas correctement, l’utilisateur doit ouvrir et enregistrer la règle `submitForm` sur le bouton **Envoyer** à l’aide de l’éditeur de règles. Cette action remplace la règle existante de `submitForm('custom:submitSuccess', 'custom:submitError')` par `submitForm()` dans le formulaire.

## Voir également

{{see-also-rule-editor}}
