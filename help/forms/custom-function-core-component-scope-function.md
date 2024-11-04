---
title: Présentation des objets scope dans les fonctions personnalisées
description: Le formulaire prend en charge les objets scope dans les fonctions personnalisées qui sont transmises en dernier argument aux fonctions lors de l’exécution de la règle.
keywords: Portée d’objets dans des fonctions personnalisées, des objets globaux, des objets de champ.
feature: Adaptive Forms, Core Components
role: User, Developer
source-git-commit: af211649a4f22d06f4e8669335a8267ee948a408
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 1%

---


# Objet Scope dans les fonctions personnalisées

Dans les Forms adaptatives, un objet de portée est transmis en tant que dernier argument aux fonctions lorsqu’une règle est exécutée. Il peut être utilisé pour lire les propriétés de formulaire/champ et modifier le formulaire au sein des fonctions. L’objet scope contient un objet proxy en lecture seule pour le formulaire, l’événement déclenché et le champ cible. Les propriétés de formulaire et de champ sont accessibles à l’aide de l’objet scope en ajoutant `$`, par exemple `scope.form.$id` et `scope.field.$id`, respectivement.

## Fonctions de modification de formulaire utilisant l’objet scope

L’objet Scope dispose des fonctions suivantes pour la modification du formulaire :

| Fonction | Syntaxe | Description | Exemple de code |
|-----------------|----------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|-----------------------------|
| **setProperty** | `setProperty(any $element, any $payload)` | Définit une propriété de `$element` à l’aide de `$payload`. | [Cliquez ici](/help/forms/custom-function-core-components-use-cases.md#show-a-panel-using-the-setproperty-rule) pour afficher l’exemple. |
| **validate** | `validate([any $element])` | Exécute la validation sur `$element`. Si aucun élément n’est fourni, le formulaire entier est validé. | [Cliquez ici](/help/forms/custom-function-core-components-use-cases.md#validate-the-field) pour afficher l’exemple. |
| **reset** | `reset([any $element])` | Réinitialise le `$element`. Si aucun élément n’est fourni, il réinitialise l’intégralité du formulaire. | [Cliquez ici](/help/forms/custom-function-core-components-use-cases.md#reset-a-panel) pour afficher l’exemple. |
| **importData** | `importData(any $payload)` | Importe les données dans le formulaire, en remplaçant toutes les données de formulaire existantes. | [Cliquez ici](/help/forms/custom-function-core-components-use-cases.md#pre-fill-the-field-with-a-value-when-the-form-loads) pour afficher l’exemple. |
| **exportData** | `exportData()` | Renvoie les données du formulaire. | [Cliquez ici](/help/forms/custom-function-core-components-use-cases.md#submit-altered-data-to-the-server) pour afficher l’exemple. |
| **submitForm** | `submitForm(any $data [, boolean $validate_form = true, string $submit_as = 'multipart/form-data'])` | Déclenche l’envoi d’un formulaire. Le paramètre `$data` spécifie ce qui doit être envoyé et `$submit_as` définit le type de contenu (par défaut &quot;multipart/form-data&quot;). L’ `$validate_form` facultatif détermine si le formulaire doit être validé (par défaut : true). En cas de succès, `submitSuccess` est déclenché ; en cas d’échec, `submitError` est déclenché. | [Cliquez ici](/help/forms/custom-function-core-components-use-cases.md#submit-altered-data-to-the-server) pour afficher l’exemple. |
| **setFocus** | `setFocus(any $element [, FocusOption $focusOption])` | Définit la cible d’action sur le `$element`, qui peut être un panneau ou un champ. Si aucun élément n’est fourni, le focus est défini sur le champ qui a déclenché la règle. Le paramètre facultatif `$focusOption` (de type énumération `FocusOption`) indique s’il faut se concentrer sur &#39;nextItem&#39; ou &#39;previousItem&#39; par rapport à `$element`. Si un panneau est spécifié, la navigation est limitée à ce panneau ; avec un champ, la navigation se fait dans le panneau parent. | [Cliquez ici](/help/forms/custom-function-core-components-use-cases.md#set-focus-on-the-specific-field) pour afficher l’exemple. |
| **dispatchEvent** | `dispatchEvent(any $element, string $eventName [, any $payload])` | Détermine un événement de type `$eventName` sur l’élément spécifié par `$element`. Si aucun élément n’est fourni, l’événement est distribué sur le formulaire. Le `$payload` facultatif est mis à la disposition des expressions gérant l’événement. | [Cliquez ici](/help/forms/custom-function-core-components-use-cases.md#add-or-delete-repeatable-panel-using-the-dispatchevent-property) pour afficher l’exemple. |
| **markFieldAsInvalid** | `markFieldAsInvalid(string $fieldIdentifier, string $validationMessage [, any $option = {useId: true}])` | Marque le champ identifié par `$fieldIdentifier` comme non valide et définit le message de validation sur `$validationMessage`. Le paramètre facultatif `$option` spécifie si `$fieldIdentifier` est interprété comme `id`, `name` ou `dataRef`. La valeur par défaut est `{useId: true}` et les valeurs prises en charge sont `{useId: true}`, `{useDataRef: true}` et `{useQualifiedName: true}`. | [Cliquez ici](/help/forms/custom-function-core-components-use-cases.md#to-display-a-custom-message-at-the-field-level-and-marking-the-field-as-invalid) pour afficher l’exemple. |

## Voir également

{{see-also-rule-editor}}