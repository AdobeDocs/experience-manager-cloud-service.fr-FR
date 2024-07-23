---
title: Quels sont les différents types d’opérateurs et événements disponibles dans l’éditeur de règles d’un formulaire adaptatif en fonction des composants principaux ?
description: L’éditeur de règles de Forms adaptatif prend en charge divers types d’opérateurs et événements.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
source-git-commit: 780c68f0c21ef94ff6a73ce991370100b1a88db9
workflow-type: tm+mt
source-wordcount: '1921'
ht-degree: 50%

---


# Types d’opérateurs et événements dans l’éditeur de règles d’un formulaire adaptatif basé sur les composants principaux

Dans AEM Forms as a Cloud, l’éditeur de règles comprend divers types d’opérateurs et événements qui vous permettent de définir et d’exécuter facilement des conditions et des actions complexes.

Les types d’opérateurs disponibles dans l’éditeur de règles d’un formulaire adaptatif offrent un cadre robuste pour créer des conditions précises. Ils vous permettent de manipuler des données, d’effectuer des calculs et de combiner plusieurs conditions de manière logique et cohérente. Que vous compariez des valeurs, effectuiez des opérations arithmétiques ou manipuliez des chaînes, ces opérateurs garantissent que vos règles sont à la fois flexibles et puissantes.

Les événements de l’éditeur de règles servent de déclencheurs pour activer vos règles. Ils définissent les actions spécifiques qui se produisent lorsque certaines conditions sont remplies. En exploitant différents types d’événements, vous pouvez automatiser les réponses à un large éventail de scénarios, par exemple les interactions utilisateur, les heures planifiées, les modifications des données et les états du système. Avec la possibilité de spécifier ces déclencheurs, vous pouvez créer des règles dynamiques et réactives qui répondent à vos besoins spécifiques.

En comprenant et en utilisant les types d’opérateurs et les événements disponibles, vous pouvez exploiter tout le potentiel de l’éditeur de règles, ce qui vous permet de créer des règles efficaces et efficientes qui répondent à vos besoins uniques et améliorent les fonctionnalités globales du système.

## Types d’opérateur et événements disponibles dans l’éditeur de règles {#available-operator-types-and-events-in-rule-editor}

L’éditeur de règles fournit les opérateurs logiques et les événements suivants à l’aide desquels vous pouvez créer des règles.

* **est égal à**
* **n&#39;est pas égal à**
* **Commence par**
* **Se termine par**
* **Contient**
* **Ne contient pas**
* **Est vide**
* **N’est pas vide**
* **A sélectionné :** renvoie la valeur True lorsque l’utilisateur sélectionne une option donnée pour une case à cocher, une liste déroulante, un bouton radio.
* **Est initialisé (événement) :** renvoie la valeur True si un objet de formulaire est généré dans le navigateur.
* **Est modifié (événement) :** renvoie la valeur True si l’utilisateur modifie la valeur saisie ou l’option sélectionnée pour un objet de formulaire.

<!--
* **Navigation(event):** Returns true when the user clicks a navigation object. Navigation objects are used to move between panels. 
* **Step Completion(event):** Returns true when a step of a rule completes.
* **Successful Submission(event):** Returns true on successful submission of data to a form data model.
* **Error in Submission(event):**  Returns true on unsuccessful submission of data to a form data model. -->

### Types de règle disponibles dans l’éditeur de règles {#available-rule-types-in-rule-editor}

L’éditeur de règles fournit un ensemble de types de règle prédéfinis que vous pouvez utiliser pour créer des règles. Examinons en détail chaque type de règle. Pour plus d’informations sur l’écriture de règles dans l’éditeur de règles, voir [Écrire des règles](/help/forms/rule-editor-core-components-user-interface.md#write-rules).

#### [!UICONTROL Lorsque] {#whenruletype}

Le type de règle **[!UICONTROL Lorsque]** suit le concept de règle d’**action alternative de condition-action** ou parfois simplement le concept de **condition-action**. Dans ce type de règle, vous spécifiez d’abord une condition à évaluer, puis une action à déclencher si la condition est remplie (`True`). Lors de l’utilisation du type de règle Lorsque, vous pouvez utiliser plusieurs opérateurs ET et OU afin de créer des [expressions imbriquées](/help/forms/rule-editor-core-components-usecases.md#nested-expressions).

Avec le type de règle Lorsque, vous pouvez évaluer une condition sur un objet de formulaire et exécuter des actions sur un ou plusieurs objets.

En clair, un type de règle Lorsque standard est structuré comme suit :

`When on Object A:`

`(Condition 1 AND Condition 2 OR Condition 3) is TRUE;`

`Then, do the following:`

`Action 2 on Object B;`
`AND`
&quot;Action 3 sur Objet C ;

`Else, do the following:`

`Action 2 on Object C;`
_

Lorsque vous avez un composant à valeurs multiples, comme des boutons radio ou une liste, les options sont récupérées automatiquement et mises à disposition du créateur de la règle lorsque vous créez une règle pour ce composant. Vous n’avez pas besoin de saisir à nouveau les valeurs de l’option.

Prenons l’exemple d’une liste comportant quatre options : rouge, bleu, vert et jaune. Lors de la création de la règle, les options (boutons radio) sont automatiquement récupérées et mises à la disposition de l’auteur de la règle comme suit :

![Options d’affichage à valeurs multiples](assets/multivaluefcdisplaysoptions.png)

Lorsque vous créez une règle Lorsque, vous pouvez déclencher l’action Effacer la valeur de. L’action Effacer la valeur d’efface la valeur de l’objet spécifié. L’option Effacer la valeur de comme dans l’instruction Lorsque vous permet de créer des conditions complexes avec plusieurs champs. Vous pouvez ajouter l’instruction Else pour ajouter d’autres conditions.

![Effacer la valeur de](assets/clearvalueof.png)

>[!NOTE]
>
> Lorsque le type de règle ne prend en charge que les instructions de niveau unique, alors les instructions else.

##### Plusieurs champs autorisés dans [!UICONTROL When] {#allowed-multiple-fields}

Dans la condition **When**, vous avez la possibilité d’ajouter d’autres champs à l’exception du champ auquel la règle est appliquée.

Par exemple, en utilisant le type de règle Lorsque , vous pouvez évaluer une condition sur différents objets de formulaire et effectuer l’action suivante :

Lorsque :

(Objet A, condition 1)

ET/OU

(Objet B, condition 2)

Ensuite, procédez comme suit :

Action 1 sur Objet A

_

![Plusieurs champs autorisés dans When](/help/forms/assets/allowed-multiple-field-when.png)

**Considérations lors de l’utilisation de plusieurs champs autorisés dans la fonction de condition Lorsque**

* Assurez-vous que le [composant principal est défini sur la version 3.0.14 ou ultérieure](https://github.com/adobe/aem-core-forms-components) pour utiliser cette fonctionnalité dans l’éditeur de règles.
* Si des règles sont appliquées à différents champs dans la condition Lorsque , la règle se déclenche même si un seul de ces champs est modifié.


<!--
* It is not possible to add multiple fields in the When condition while applying rules to a button.

##### To enable Allowed Multiple fields in When condition feature

Allowed Multiple fields in When condition feature is disabled by default. To enable this feature, add a custom property at the template policy:

1. Open the corresponding template associated with an Adaptive Form in the template editor.
1. Select the existing policy as **formcontainer-policy**.
1. Navigate to the **[!UICONTROL Structure]**  view and, from the **[!UICONTROL Allowed Components]** list, open the **[!UICONTROL Adaptive Forms Container]** policy.
1. Go to the **[!UICONTROL Custom Properties]** tab and to add a custom property, click **[!UICONTROL Add]**.
1. Specify the **Group Name** of your choice. For example, in our case, we added the group name as **allowedfeature**.
1. Add the **key** and **value** pair as follows:
   * key: fd:changeEventBehaviour
   * value: deps
1. Click **[!UICONTROL Done]**. -->

Si plusieurs champs autorisés de la fonction de condition Lorsque rencontrent des problèmes, suivez les étapes de dépannage comme suit :

1. Ouvrez le formulaire adaptatif en mode de modification.
1. Ouvrez l’explorateur de contenu et sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La fenêtre du conteneur de formulaires adaptatifs s’ouvre.
1. Cliquez sur Terminé et enregistrez à nouveau la boîte de dialogue.

**[!UICONTROL Masquer]** Masque l’objet spécifié.

**[!UICONTROL Afficher]** Affiche l’objet spécifié.

**[!UICONTROL Activer]** Active l’objet spécifié.

**[!UICONTROL Désactiver]** Désactive l’objet spécifié.

**[!UICONTROL Appeler le service]** : appelle un service configuré dans un modèle de données de formulaire (FDM). Lorsque vous sélectionnez l’opération Appel du service, un champ s’affiche. Lorsque vous appuyez sur le champ, il affiche tous les services configurés dans tous les modèles de données de formulaire (FDM) sur votre instance [!DNL Experience Manager]. Lorsque vous sélectionnez un service de modèle de données de formulaire, des champs supplémentaires permettant de mapper des objets de formulaires avec des paramètres d’entrée et de sortie pour le service spécifié s’affichent. Voir l’exemple de règle pour appeler les services de modèle de données de formulaire (FDM).

Outre le service Form Data Model, vous pouvez spécifier une URL WSDL directe pour appeler un service Web. Cependant, un service de modèle de données de formulaire possède de nombreux avantages et l’approche recommandée permettant d’appeler un service.

Pour plus d’informations sur la configuration des services dans le modèle de données de formulaire (FDM), voir [[!DNL Experience Manager Forms] Intégration de données](data-integration.md).

**[!UICONTROL Définir la valeur de]** Calcule et définit la valeur de l’objet spécifié. Vous pouvez définir la valeur de l’objet sur une chaîne, la valeur d’un autre objet, la valeur calculée à l’aide d’une expression ou d’une fonction mathématique, la valeur d’une propriété d’un objet ou la valeur de sortie d’un service de modèle de données de formulaire configuré. Lorsque vous choisissez l’option de service Web, elle affiche tous les services configurés dans tous les modèles de données de formulaire (FDM) sur votre instance [!DNL Experience Manager]. Lorsque vous sélectionnez un service de modèle de données de formulaire, des champs supplémentaires permettant de mapper des objets de formulaires avec des paramètres d’entrée et de sortie pour le service spécifié s’affichent.

Pour plus d’informations sur la configuration des services dans le modèle de données de formulaire (FDM), voir [[!DNL Experience Manager Forms] Intégration de données](data-integration.md).

Le type de règle **[!UICONTROL Définir la propriété]** permet de définir la valeur d’une propriété de l’objet spécifié en fonction d’une action de condition. Vous pouvez définir la propriété sur l’une des options suivantes :
* visible (booléen)
* label.value (String)
* label.visible (booléen)
* description (chaîne)
* enabled (booléen)
* readOnly (booléen)
* obligatoire (booléen)
* screenReaderText (String)
* valid (booléen)
* errorMessage (chaîne)
* default (Number, String, Date)
* enumNames (String[])
* chartType (chaîne)

Par exemple, il vous permet de définir des règles pour afficher la zone de texte lorsqu’un utilisateur clique sur un bouton. Vous pouvez utiliser une fonction personnalisée, un objet de formulaire, une propriété d’objet ou une sortie de service pour définir une règle.

![Définir la propriété](assets/set_property_rule_new.png)

Pour définir une règle basée sur une fonction personnalisée, sélectionnez **[!UICONTROL Sortie de fonction]** dans la liste déroulante, puis faites glisser et déposez une fonction personnalisée à partir de l’onglet **[!UICONTROL Fonctions]**. Si l’action de condition est remplie, la zone de saisie de texte est visible.

Pour définir une règle basée sur un objet de formulaire, sélectionnez **[!UICONTROL Objet de formulaire]** dans la liste déroulante, puis faites glisser et déposez un objet de formulaire à partir de l’onglet **[!UICONTROL Objets de formulaire]**. Si l’action de condition est remplie, la zone de saisie de texte est visible dans le formulaire adaptatif.

Une règle Définir la propriété basée sur une propriété d’objet permet de rendre la zone de saisie de texte visible dans un formulaire adaptatif en fonction d’une autre propriété d’objet incluse dans le formulaire adaptatif.

La figure suivante illustre un exemple d’activation dynamique de la case à cocher en fonction du masquage ou de l’affichage d’une zone de texte dans un formulaire adaptatif :

![Propriété de l’objet](assets/object_property_set_property_new.png)

**[!UICONTROL Effacer la valeur de]** : efface la valeur de l’objet spécifié.

**[!UICONTROL Définir la cible d’action]**: définit la cible d’action sur l’objet spécifié.

**[!UICONTROL Submit Form]** Envoie le formulaire.

**[!UICONTROL Reset]** Réinitialise le formulaire ou l’objet spécifié.

**[!UICONTROL Validate]** : valide le formulaire ou l’objet spécifié.

**[!UICONTROL Ajouter une instance]** : ajoute une instance de la ligne de panneau ou de tableau répétable spécifiée.

**[!UICONTROL Supprimer une instance]** : supprime une instance de la ligne de panneau ou de tableau répétable spécifiée.

**[!UICONTROL Sortie de fonction]** Définit une règle basée sur des fonctions prédéfinies ou des fonctions personnalisées.

**[!UICONTROL Accédez à]** Accédez à d’autres ressources de Forms adaptatif, telles que des images ou des fragments de document, ou une URL externe. <!-- For more information, see [Add button to the Interactive Communication](create-interactive-communication.md#addbuttontothewebchannel). -->

**[!UICONTROL Dispatch Event]** déclenche des actions ou des comportements spécifiques en fonction de conditions ou d’événements prédéfinis.

#### [!UICONTROL Définir la valeur de] {#set-value-of}

Le type de règle **[!UICONTROL Définir la valeur de]** permet de définir la valeur d’un objet de formulaire selon que la condition spécifiée est remplie ou non. La valeur peut être définie sur la valeur d’un autre objet, d’une chaîne littérale, la valeur dérivée d’une expression ou d’une fonction mathématique, la valeur d’une propriété d’un autre objet ou la sortie d’un service de modèle de données de formulaire. De même, vous pouvez vérifier la condition d’un composant, d’une chaîne, d’une propriété ou les valeurs dérivées d’une fonction ou d’une expression mathématique.

Notez que le type de règle **Définir la valeur de** n’est pas disponible pour tous les objets de formulaire, comme les boutons de panneaux et de barres d’outils. Une règle Définir la valeur de standard possède la structure suivante :

Définissez la valeur de Objet A sur :

(chaîne ABC) OU
(propriété d’objet X de Objet C) OU
(valeur d’une fonction) OU
(valeur d’une expression mathématique) OU
(valeur de sortie d’un service de modèle de données) ;

Lorsque (facultatif) :

(Condition 1 ET Condition 2 ET Condition 3) est TRUE ;

L’exemple suivant sélectionne la valeur de `Question2` en tant que `True` et définit la valeur de `Result` en tant que `correct`.

![Set-value-web-service](assets/set-value-web-service.png)

Exemple de règle Définir la valeur à l’aide du service de modèle de données de formulaire.

#### [!UICONTROL Afficher] {#show}

Le type de règle **[!UICONTROL Afficher]** permet de créer une règle pour afficher ou masquer un objet de formulaire selon qu’une condition est remplie ou non. Le type de règle Afficher déclenche également l’action Masquer au cas où la condition ne serait pas remplie ou renverrait `False`.

Une règle standard Afficher est structurée comme suit :

`Show Object A;`

`When:`

`(Condition 1 OR Condition 2 OR Condition 3) is TRUE;`

`Else:`

`Hide Object A;`

#### [!UICONTROL Masquer] {#hide}

De la même manière que pour le type de règle Afficher, vous pouvez utiliser le type de règle **[!UICONTROL Masquer]** pour afficher ou masquer un objet de formulaire selon qu’une condition est remplie ou non. Le type de règle Masquer déclenche également l’action Afficher au cas où la condition ne serait pas remplie ou renverrait `False`.

Une règle standard Masquer est structurée comme suit :

`Hide Object A;`

`When:`

`(Condition 1 AND Condition 2 AND Condition 3) is TRUE;`

`Else:`

`Show Object A;`

#### [!UICONTROL Activer] {#enable}

Le type de règle **[!UICONTROL Activer]** permet d’activer ou de désactiver un objet de formulaire selon qu’une condition est remplie ou non. Le type de règle Activer déclenche également l’action Désactiver au cas où la condition ne serait pas remplie ou renverrait `False`.

Une règle Activer standard est structurée comme suit :

`Enable Object A;`

`When:`

`(Condition 1 AND Condition 2 AND Condition 3) is TRUE;`

`Else:`

`Disable Object A;`

#### [!UICONTROL Désactiver] {#disable}

De la même manière que le type de règle Activer, le type de règle **[!UICONTROL Désactiver]** permet d’activer ou de désactiver un objet de formulaire selon qu’une condition est remplie ou non. Le type de règle Désactiver déclenche également l’action Activer au cas où la condition ne serait pas remplie ou renverrait `False`.

Une règle Désactiver standard est structurée comme suit :

`Disable Object A;`

`When:`

`(Condition 1 OR Condition 2 OR Condition 3) is TRUE;`

`Else:`

`Enable Object A;`

#### [!UICONTROL Valider] {#validate}

Le type de règle **[!UICONTROL Valider]** valide la valeur d’un champ à l’aide d’une expression. Par exemple, vous pouvez créer une expression pour vérifier que la zone de texte permettant de spécifier un nom ne contient pas de caractères spéciaux ni de nombres.

Une règle Valider standard est structurée comme suit :

`Validate Object A;`

`Using:`

`(Expression 1 AND Expression 2 AND Expression 3) is TRUE;`

>[!NOTE]
>
>Si la valeur spécifiée n’est pas conforme à la règle Valider, vous pouvez afficher un message de validation à l’utilisateur ou utilisatrice. Vous pouvez spécifier le message dans le champ **[!UICONTROL Message de validation du script]** dans les propriétés de composant dans la barre latérale.

![Script-validation](assets/script-validation.png)

<!--
### [!UICONTROL Set Options Of] {#setoptionsof}

The **[!UICONTROL Set Options Of]** rule type enables you to define rules to add check boxes dynamically to the Adaptive Form. You can use a Form Data Model or a custom function to define the rule.

To define a rule based on a custom function, select **[!UICONTROL Function Output]** from the drop-down list, and drag-and-drop a custom function from the **[!UICONTROL Functions]** tab. The number of checkboxes defined in the custom function are added to the Adaptive Form.

![Custom Functions](assets/custom_functions_set_options_new.png)

To create a custom function, see [custom functions in rule editor](#custom-functions).

To define a rule based on a form data model:

1. Select **[!UICONTROL Service Output]** from the drop-down list.
1. Select the data model object.
1. Select a data model object property from the **[!UICONTROL Display Value]** drop-down list. The number of checkboxes in the Adaptive Form is derived from the number of instances defined for that property in the database.
1. Select a data model object property from the **[!UICONTROL Save Value]** drop-down list.

![FDM set options](assets/fdm_set_options_new.png) -->

## Étape suivante

Examinons maintenant les [exemples d’un éditeur de règles pour un formulaire adaptatif basé sur les composants principaux](/help/forms/rule-editor-core-components-usecases.md).

## Voir également

{{see-also-rule-editor}}