---
title: Présentation des objets de portée dans les fonctions personnalisées
description: Le formulaire prend en charge les objets de portée dans les fonctions personnalisées qui sont transmises en tant que dernier argument aux fonctions lors de l’exécution de la règle.
keywords: objets portée dans les fonctions personnalisées, les objets globaux, les objets de champ.
feature: Adaptive Forms, Core Components
role: User, Developer
exl-id: 248c75a5-6335-41d2-aa0a-28a20a710f88
source-git-commit: e2bc958104bd9b75845ad2c213eec18d2560a3a4
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 3%

---

# Objet portée dans les fonctions personnalisées

Dans le Forms adaptatif, un objet de portée est transmis en tant que dernier argument aux fonctions lorsqu’une règle est exécutée. Il peut être utilisé pour lire les propriétés du formulaire/champ et modifier le formulaire à partir des fonctions . L’objet portée contient un objet proxy en lecture seule pour le formulaire, l’événement déclenché et le champ cible. Vous pouvez accéder aux propriétés du formulaire et du champ à l’aide de l’objet portée en ajoutant `$`, par exemple `scope.form.$id` et `scope.field.$id`, respectivement.

## Fonctions de modification de formulaire utilisant l’objet d’étendue

L’objet Portée possède les fonctions suivantes pour la modification de formulaire :

| Fonction | Syntaxe | Description | Exemple de code |
|-----------------|--------|-------------|-------------|
| **setProperty** | `setProperty(any $element, any $payload)` | Définit une propriété sur le champ cible à l’aide de l’`$payload` . | [Cliquez ici](/help/forms/custom-function-core-components-use-cases.md#show-a-panel-using-the-setproperty-rule) pour voir l’exemple. |
| **valider** | `validate([any $element])` | Exécute la validation sur le champ cible. Exécute la validation sur l’ensemble du formulaire si aucune cible n’est fournie et renvoie un tableau des erreurs de validation. | [Cliquez ici](/help/forms/custom-function-core-components-use-cases.md#validate-the-field) pour voir l’exemple. |
| **reset** *(obsolète)* | `reset([any $element])` | Obsolète. Utilisez `dispatchEvent($target, 'reset')` à la place. Réinitialise le champ cible ou, si aucune cible n’est fournie, réinitialise l’ensemble du formulaire. | [Cliquez ici](/help/forms/custom-function-core-components-use-cases.md#reset-a-panel) pour voir l’exemple. |
| **importData** | `importData(any $payload)` | Importe des données dans le formulaire, en remplaçant toutes les données de formulaire existantes. Si `qualifiedName` est spécifié, les données sont importées uniquement dans ce champ de conteneur. | [Cliquez ici](/help/forms/custom-function-core-components-use-cases.md#pre-fill-the-field-with-a-value-when-the-form-loads) pour voir l’exemple. |
| **exportData** | `exportData()` | Renvoie les données du formulaire. | [Cliquez ici](/help/forms/custom-function-core-components-use-cases.md#submit-altered-data-to-the-server) pour voir l’exemple. |
| **submitForm** | `submitForm(any $data [, boolean $validate_form = true, string $submit_as = 'multipart/form-data'])` | Déclenche l’envoi d’un formulaire. Vous pouvez spécifier les éléments à envoyer via le paramètre `$payload` et définir le type de contenu via le paramètre `$contentType` . Par défaut, les données sont envoyées en tant que `multipart/form-data`. Le paramètre facultatif `$validateForm` indique si le formulaire doit être validé avant envoi (valeur par défaut : true). En cas de réussite, `submitSuccess` est déclenché ; en cas d’échec, `submitError` est déclenché. | [Cliquez ici](/help/forms/custom-function-core-components-use-cases.md#submit-altered-data-to-the-server) pour voir l’exemple. |
| **setFocus** | `setFocus(any $element [, FocusOption $focusOption])` | Définit le focus sur le champ cible, qui peut être un panneau ou un champ de formulaire. Si aucune cible n’est fournie, le focus est défini sur le champ qui a déclenché la règle. Le paramètre `$focusOption` facultatif spécifie si l’élément suivant ou précédent relatif à la cible doit être ciblé. Valeurs prises en charge : `'nextItem'`, `'previousItem'`. Si vous utilisez cette option avec un panneau, la navigation est limitée à ce panneau. Si vous utilisez cette option avec un champ, la navigation s’effectue dans le panneau parent de ce champ. | [Cliquez ici](/help/forms/custom-function-core-components-use-cases.md#set-focus-on-the-specific-field) pour voir l’exemple. |
| **dispatchEvent** | `dispatchEvent(any $element, string $eventName [, any $payload])` | Distribue un événement de type `$eventName` sur l’élément déterminé par `$target`. Si aucune cible n’est fournie, l’événement est distribué sur le formulaire. Le `$payload` facultatif est disponible pour les expressions qui gèrent l’événement. Le paramètre facultatif `$dispatch` contrôle le comportement de propagation des événements. | [Cliquez ici](/help/forms/custom-function-core-components-use-cases.md#add-or-delete-repeatable-panel-using-the-dispatchevent-property) pour voir l’exemple. |
| **markFieldAsInvalid** | `markFieldAsInvalid(string $fieldIdentifier, string $validationMessage [, any $option = {useId: true}])` | Marque le champ identifié par `$fieldIdentifier` comme non valide et affiche le `$validationMessage`. Le paramètre facultatif `$option` indique si `$fieldIdentifier` est interprété comme `id`, `dataRef` ou `qualifiedName`. La valeur par défaut est `{useId: true}`. Valeurs prises en charge : `{useId: true}`, `{useDataRef: true}`, `{useQualifiedName: true}`. | [Cliquez ici](/help/forms/custom-function-core-components-use-cases.md#to-display-a-custom-message-at-the-field-level-and-marking-the-field-as-invalid) pour voir l’exemple. |

## Voir également

{{see-also-rule-editor}}

