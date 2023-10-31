---
title: Ajouter des gestionnaires d’erreurs personnalisés dans les formulaires adaptatifs pour les formulaires adaptatifs AEM
seo-title: Error Handlers in Adaptive Forms for AEM Adaptive Forms
description: AEM Forms fournit des gestionnaires de réussite et d’erreur prêts à l’emploi pour un formulaire utilisant le point d’entrée REST configuré pour appeler un service externe. Vous pouvez ajouter un gestionnaire d’erreurs par défaut ainsi qu’un gestionnaire d’erreurs personnalisé dans un formulaire adaptatif AEM.
seo-description: Error handler function and Rule Editor in Adaptive Forms helps you to effectively manage and customize error handling. You can add a default error handler as well as custom error handler in an AEM Adaptive Form.
keywords: Ajoutez un gestionnaire d’erreurs personnalisé, ajoutez un gestionnaire d’erreurs par défaut, ajoutez un gestionnaire d’erreurs dans le formulaire, utilisez le service d’appel de l’éditeur de règles pour ajouter un gestionnaire d’erreurs personnalisé, configurez l’éditeur de règles pour ajouter un gestionnaire d’erreurs personnalisé , ajoutez un gestionnaire d’erreurs personnalisé à l’aide de l’éditeur de règles
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms
exl-id: 198a26a9-d6bb-457d-aab8-0a5d15177c48
source-git-commit: 1dd0bbbe8a366b38a923e61bd987e248c2f78e86
workflow-type: tm+mt
source-wordcount: '2445'
ht-degree: 79%

---

# Ajout de gestionnaires d’erreurs personnalisés dans AEM Forms adaptatif {#error-handlers-in-adaptive-form}

<span class="preview"> Adobe recommande d’utiliser la capture de données moderne et extensible. [Composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr) pour [création d’un Forms adaptatif](/help/forms/creating-adaptive-form-core-components.md) ou [Ajout de Forms adaptatif à des pages AEM Sites](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Ces composants représentent une avancée significative dans la création de Forms adaptatif, ce qui garantit des expériences utilisateur impressionnantes. Cet article décrit l’approche plus ancienne de la création de Forms adaptatif à l’aide de composants de base. </span>

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/standard-validation-error-messages-adaptive-forms.html) |
| AEM as a Cloud Service | Cet article |

AEM Forms fournit des gestionnaires de succès et d’erreurs prêts à l’emploi pour les soumissions de formulaires. Il fournit également une fonctionnalité pour personnaliser les fonctions du gestionnaire d’erreurs. Par exemple, vous pouvez appeler un workflow personnalisé dans le serveur principal pour des codes d’erreur spécifiques ou informer le client ou la cliente que le service est indisponible. Les gestionnaires sont des fonctions côté client qui s’exécutent en fonction de la réponse du serveur. Lorsqu’un service externe est appelé à l’aide des API, les données sont transmises au serveur pour validation, qui renvoie une réponse au client ou à la cliente avec des informations sur le succès ou l’erreur de la soumission. Les informations sont transmises en tant que paramètres au gestionnaire approprié pour exécuter la fonction. Un gestionnaire d’erreurs permet de gérer et d’afficher les erreurs ou les problèmes de validation rencontrés.

![workflow du gestionnaire d’erreurs pour comprendre comment ajouter un gestionnaire d’erreurs personnalisé dans les formulaires](/help/forms/assets/error-handler-workflow.png)

Le formulaire adaptatif valide les entrées que vous fournissez dans les champs en fonction de critères de validation prédéfinis et vérifie diverses erreurs renvoyées par le point de terminaison REST configuré pour appeler un service externe. Vous pouvez définir les critères de validation en fonction de la source de données que vous utilisez avec le formulaire adaptatif. Par exemple, si vous utilisez des services web RESTful comme source de données, vous pouvez définir les critères de validation dans un fichier de définition Swagger.

Si les valeurs d’entrée répondent aux critères de validation, les valeurs sont envoyées à la source de données, sinon le formulaire adaptatif affiche un message d’erreur à l’aide d’un gestionnaire d’erreurs. De la même manière que cette approche, Adaptive Forms s’intègre aux gestionnaires d’erreurs personnalisés pour effectuer des validations de données. Si les valeurs d’entrée ne répondent pas aux critères de validation, les messages d’erreur s’affichent au niveau du champ dans le formulaire adaptatif. Cela se produit lorsque le message d’erreur de validation renvoyé par le serveur est au format standard du message.


## Utilisation des gestionnaires d’erreurs {#uses-of-error-handler}

Les gestionnaires d’erreurs sont utilisés à diverses fins. Certaines des utilisations des fonctions de gestionnaire d’erreurs sont répertoriées ci-dessous :
* **Effectuer une validation** : la gestion des erreurs commence par la validation des entrées utilisateur par rapport à des règles ou critères prédéfinis. Lorsque les utilisateurs ou les utilisatrices remplissent un formulaire adaptatif, le gestionnaire d’erreurs valide l’entrée afin de s’assurer qu’elle respecte le format, la longueur ou toute autre contrainte.

* **Fournir des commentaires en temps réel** : lorsqu’une erreur est détectée, le gestionnaire d’erreurs affiche des commentaires immédiats à l’utilisateur ou à l’utilisatrice, tels que des messages d’erreur intégrés sous les champs de formulaire correspondants. Ces commentaires permettent aux utilisateurs et aux utilisatrices d’identifier et de corriger les erreurs sans avoir à envoyer le formulaire et attendre une réponse.


* **Affichage des messages d’erreur** : lorsqu’un envoi de formulaire adaptatif rencontre une erreur de validation, le gestionnaire d’erreurs affiche un message d’erreur approprié. Les messages d’erreur doivent être clairs, concis et mettre en évidence les champs spécifiques qui nécessitent une attention particulière.

* **Mise en surbrillance du champ erroné** : pour attirer l’attention de l’utilisateur ou de l’utilisatrice sur les champs spécifiques incorrects, le gestionnaire d’erreurs surligne ou distingue visuellement les champs correspondants. Il est effectué en modifiant la couleur d’arrière-plan, en ajoutant une icône ou une bordure, ou tout autre indice visuel qui aide les utilisateurs et les utilisatrices à localiser et à corriger rapidement les erreurs.


## Format de réponse échec/erreur {#failure-response-format}

Un formulaire adaptatif affiche les erreurs au niveau du champ si les messages d’erreur de validation du serveur sont au format standard suivant.
Le code ci-dessous illustre la structure de réponse d’échec existante :

```javascript
   {
    errorCausedBy : "SERVER_SIDE_VALIDATION/SERVICE_INVOCATION_FAILURE"
    errors : [
        {
             somExpression  : <somexpr>
             errorMessage / errorMessages : <validationMsg> / [<validationMsg>, <validationMsg>]
        }
    ]
    originCode : <target error Code>
    originMessage : <unstructured error message returned by service>
    }
```


Où :

* `errorCausedBy` décrit le motif de l’échec..
* `errors` mentionne l’expression SOM des champs qui ont échoué aux critères de validation avec le message d’erreur de validation.
* `originCode` est un champ ajouté par AEM, qui contient le code d’état http renvoyé par le service externe.
* `originMessage` est un champ ajouté par AEM, qui contient les données d’erreur brutes renvoyées par le service externe.

Avec les améliorations des fonctionnalités et les mises à jour ultérieures dans les versions d’AEM Forms, la structure de réponse aux échecs existante a été changée en nouveau format basé sur RFC7807, qui est rétrocompatible avec la structure de réponse aux échecs existante :

```javascript
    {
        "type": "SERVER_SIDE_VALIDATION/FORM_SUBMISSION/SERVICE_INVOCATION/FAILURE/VALIDATION_ERROR", (required)
        "title": "Server side validation failed/Third party service invocation failed", (optional)
        "detail": "", (optional)
        "instance": "", (optional)
        "validationErrors" : [ (required)
            {
                "fieldName":"<SOM expression of the field whose data sent is invalid>",
                "dataRef":<JSONPath (or XPath) of the data element which is invalid>
                "details": ["Error Message(s) for the field"] (required)
    
            }
        ],
        "originCode": <Origin http status code>, (optional - in case of SERVER_SIDE_VALIDATION)
        "originMessage" : "<unstructured error message returned by service>" (optional - in case of SERVER_SIDE_VALIDATION)
    }
```


>[!NOTE]
>
> * Assurez-vous que la structure de la réponse d’erreur inclut **fieldName** ou **dataRef**.
> * Assurez-vous que l’en-tête **ContentType** est **application/problème+json**.

Où :
* `type (required)` spécifie le type d’échec. Les valeurs peuvent être les suivantes :
   * `SERVER_SIDE_VALIDATION` indique un échec en raison de la validation côté serveur.
   * `FORM_SUBMISSION` indique un échec lors de l’envoi du formulaire
   * `SERVICE_INVOCATION` indique un échec lors d’un appel de service tiers.
   * `FAILURE` indique un échec général.
   * `VALIDATION_ERROR` indique un échec en raison d’une erreur de validation.

* `title (optional)` fournit un titre ou une brève description de l’échec.
* `detail (optional)` fournit des détails supplémentaires sur l’échec, si nécessaire.
* `instance (optional)` représente une instance ou un identifiant associé à l’échec et permet de suivre ou d’identifier l’occurrence spécifique de l’échec.
* `validationErrors (required)` contient des informations sur les erreurs de validation. Les champs suivants sont inclus :
   * `fieldname` mentionne l’expression SOM des champs qui ont échoué aux critères de validation.
   * `dataRef` représente le chemin JSON ou XPath des champs qui ont échoué à la validation.
   * `details` contiennent le message d’erreur de validation avec le champ en erreur.
* `originCode (optional)` est un champ ajouté par AEM, qui contient le code d’état http renvoyé par le service externe
* `originMessage (optional)` est un champ ajouté par AEM, qui contient les données d’erreur brutes renvoyées par le service externe.

### Exemple de format de réponse d’erreur {#sample-error-response-format}

Voici quelques options pour afficher les réponses d’erreur :

+++  Basé sur la propriété fieldName du formulaire adaptatif


* **`Header:`** `content-type:application/problem+json`
* **`Response:`**

  ```javascript
          {
              "type": "VALIDATION_ERROR",
              "validationErrors": [
              {
              "fieldName": "guide[0].guide1[0].guideRootPanel[0].textbox1686647736683[0]",
              "dataRef": "",
              "details": [
              "Invalid ID supplied. Provided value is not correct!"
          ]
          }
          ]}
  ```

  Vous pouvez afficher l’expression SOM de n’importe quel champ d’un formulaire adaptatif en appuyant sur le champ et en sélectionnant **[!UICONTROL Afficher l’expression SOM]**.

  ![Expression SOM d’un champ de formulaire adaptatif permettant d’afficher la réponse d’erreur dans le gestionnaire d’erreurs personnalisé](/help/forms/assets/custom-error-handler-somexpression.png)

+++


+++ Basé sur la propriété dataRef du formulaire adaptatif

* **`Header:`** `content-type:application/problem+json`
* **`Response:`**

  ```javascript
      {
          "type": "VALIDATION_ERROR",
          "validationErrors": [
          {
              "fieldName": "",
              "dataRef": "/Pet/id",
              "details": [
              "Invalid ID supplied. Provided value is not correct!"
              ]
              }
      ]}
  ```

  ![Référence de données d’un champ de formulaire adaptatif permettant d’afficher la réponse d’erreur dans le gestionnaire d’erreurs personnalisé](/help/forms/assets/custom-errorhandler-dataref.png)

Vous pouvez afficher la valeur de dataRef dans la fenêtre **[!UICONTROL Propriétés]** d’un composant de formulaire.

+++


## Ajouter un gestionnaire d’erreurs à l’aide de l’éditeur de règles {#add-error-handler-using-rule-editor}

En utilisant l’action [Service d’appel de l’éditeur de règles](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=fr#invoke), vous définissez les critères de validation en fonction de la source de données que vous utilisez avec le formulaire adaptatif. Si vous utilisez des services web RESTful comme source de données, vous pouvez définir les critères de validation dans un fichier de définition Swagger. En utilisant les fonctions de gestionnaire d’erreurs et l’éditeur de règles dans Adaptive Forms, vous pouvez gérer et personnaliser efficacement la gestion des erreurs. Vous définissez les conditions à l’aide de l’éditeur de règles et configurez les actions à effectuer lorsque la règle est déclenchée. Un formulaire adaptatif valide les entrées que vous fournissez dans les champs en fonction de critères de validation prédéfinis. Si les valeurs d’entrée ne répondent pas aux critères de validation, les messages d’erreur s’affichent au niveau du champ dans un formulaire adaptatif.

>[!NOTE]
>
> * Pour utiliser des gestionnaires d’erreurs avec l’action de service Invoke de l’éditeur de règles, configurez les formulaires adaptatifs avec un modèle de données de formulaire.
> * Un gestionnaire d’erreurs par défaut est fourni pour afficher les messages d’erreur sur les champs si la réponse à l’erreur se trouve dans le schéma standard. Vous pouvez également appeler le gestionnaire d’erreurs par défaut à partir de la fonction de gestionnaire d’erreurs personnalisée.

L’éditeur de règles vous permet d’effectuer les opérations suivantes :
* [Ajouter la fonction de gestionnaire d’erreurs par défaut](#add-default-errror-handler)
* [Ajouter une fonction de gestionnaire d’erreurs personnalisé](#add-custom-errror-handler)


### Ajouter la fonction de gestionnaire d’erreurs par défaut {#add-default-errror-handler}

Un gestionnaire d’erreurs par défaut est pris en charge pour afficher les messages d’erreur sur les champs si la réponse d’erreur se trouve dans le schéma standard ou dans un échec de validation côté serveur.
Pour comprendre comment utiliser un gestionnaire d’erreurs par défaut à l’aide de la méthode [Service d’appel de l’éditeur de règles](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=fr#invoke) , prenez un exemple de formulaire adaptatif simple avec deux champs, **Identifiant de paramètre prédéfini** et **Nom du paramètre prédéfini** et utilisez un gestionnaire d’erreurs par défaut au niveau de l’événement **Identifiant de paramètre prédéfini** pour vérifier les différentes erreurs renvoyées par le point de terminaison REST configuré pour appeler un service externe, par exemple : `200 - OK`,`404 - Not Found`, `400 - Bad Request`. Pour ajouter un gestionnaire d’erreurs par défaut à l’aide de l’action Invoke Service de l’éditeur de règles, procédez comme suit :

1. Ouvrez un formulaire adaptatif en mode création, sélectionnez un composant de formulaire et appuyez sur **[!UICONTROL Éditeur de règles]** pour ouvrir ce dernier.
1. Appuyez sur **[!UICONTROL Créer]**.
1. Définissez une condition dans la section **Lorsque** de la règle. Par exemple : **When[Nom du champ Identifiant de l’animal domestique]** est modifiée. L’option Sélectionner est modifiée à partir du **Sélectionner un état** liste déroulante.
1. Dans la section **Then** (Alors), sélectionnez **[!UICONTROL Invoke Service]** (Appeler un service) dans la liste déroulante **Select Action** (Sélectionner une action).
1. Sélectionnez un **service Post** et ses liaisons de données correspondantes dans la section **Entrée**. Par exemple, pour valider **Identifiant d’animal domestique**, sélectionnez un **service Post** comme **GET /pet/{petId}**, puis sélectionnez **Identifiant d’animal domestique** dans la section **Entrée**.
1. Sélectionnez les liaisons de données dans la section **Sortie**. Sélectionner **Nom du paramètre prédéfini** dans le **Sortie** .
1. Sélectionner **[!UICONTROL Gestionnaire d’erreurs par défaut]** de la **Gestionnaire d’erreurs** .
1. Cliquez sur **[!UICONTROL Terminé]**.

![ajouter un gestionnaire d’erreurs par défaut pour les contrôles de validation de champ dans un formulaire](/help/forms/assets/default-error-handler.png)

À la suite de cette règle, les valeurs que vous saisissez pour **Identifiant d’animal domestique** vérifie la validation du **Nom de l’animal domestique** à l’aide du service externe appelé par le point d’entrée REST. Si les critères de validation basés sur la source de données échouent, les messages d’erreur s’affichent au niveau du champ.

![afficher le message d’erreur par défaut lorsque vous ajoutez un gestionnaire d’erreur par défaut dans un formulaire pour gérer les réponses d’erreur ;](/help/forms/assets/default-error-message.png)

### Ajouter une fonction de gestionnaire d’erreurs personnalisé {#add-custom-errror-handler}

Vous pouvez ajouter une fonction de gestionnaire d’erreurs personnalisé pour effectuer certaines des actions suivantes :

* gérer les réponses d’erreur qui utilisent des réponses d’erreur non standard ou standard. Il est important de noter que ces réponses d’erreur non standard ne sont pas conformes au [schéma standard des réponses d’erreur](#failure-response-format).
* envoyer des événements d’analyse à n’importe quelle plate-forme analytics. Par exemple, Adobe Analytics.
* afficher la boîte de dialogue modale avec les messages d’erreur.

Outre les actions mentionnées, les gestionnaires d’erreurs personnalisés peuvent être utilisés pour exécuter des fonctions personnalisées répondant à des besoins spécifiques de l’utilisateur.

Le gestionnaire d’erreurs personnalisé est une fonction (bibliothèque cliente) conçue pour répondre aux erreurs renvoyées par un service externe et fournir une réponse personnalisée aux utilisateurs et utilisatrices finaux. Toute bibliothèque cliente avec l’annotation `@errorHandler` est considérée comme une fonction de gestionnaire d’erreurs personnalisé. Cette annotation permet d’identifier la fonction de gestionnaire d’erreurs spécifiée dans le fichier `.js`.
Pour comprendre comment créer et utiliser un gestionnaire d’erreurs personnalisé à l’aide de l’action [Service Invoke de l’éditeur de règles](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=fr#invoke), prenons un exemple de formulaire adaptatif avec deux champs, **Identifiant d’animal domestique** et **Nom de l’animal domestique** et utilisez un gestionnaire d’erreurs personnalisé sur le champ **Identifiant d’animal domestique** pour vérifier les différentes erreurs renvoyées par le point d’entrée REST configuré pour appeler un service externe, par exemple : `200 - OK`,`404 - Not Found`, `400 - Bad Request`.

Pour ajouter et utiliser un gestionnaire d’erreurs personnalisé dans un formulaire adaptatif, procédez comme suit :
1. [Créez un gestionnaire d’erreurs personnalisé](#create-custom-error-message)
1. [Utilisez l’éditeur de règles pour configurer le gestionnaire d’erreurs personnalisé](#use-custom-error-handler)

#### 1. Créer un gestionnaire d’erreurs personnalisé {#create-custom-error-message}

Pour créer une fonction de gestionnaire d’erreur personnalisée, procédez comme suit :

1. [Cloner votre référentiel AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#accessing-git).
1. Créez un dossier sous le `[AEM Forms as a Cloud Service repository folder]/apps/` dossier. Par exemple, créez un dossier nommé comme `experience-league`
1. Accédez à `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/experience-league/` et créez un `ClientLibraryFolder` as `clientlibs`.
1. Créez un dossier nommé `js`.
1. Accédez au dossier `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/clientlibs/js`.
1. Ajoutez un fichier JavaScript, par exemple `function.js`. Le fichier comprend le code du gestionnaire d’erreurs personnalisé.
Ajoutons le code suivant au fichier JavaScript pour afficher la réponse et les en-têtes reçus du point d’entrée du service REST dans la console du navigateur.

   ```javascript
       /**
       * Custom Error handler
       * @name customErrorHandler Custom Error Handler Function
       * @errorHandler
       */
       function customErrorHandler(response, headers)
       {
           console.log("Custom Error Handler processing start...");
           console.log("response:"+JSON.stringify(response));
           console.log("headers:"+JSON.stringify(headers));
           guidelib.dataIntegrationUtils.defaultErrorHandler(response, headers);
           console.log("Custom Error Handler processing end...");
       }
   ```

   Pour appeler le gestionnaire d’erreurs par défaut à partir de votre gestionnaire d’erreurs personnalisé, la ligne suivante de l’exemple de code est utilisée :
   `guidelib.dataIntegrationUtils.defaultErrorHandler(response, headers) `

   >[!NOTE]
   >
   > Dans le `.content.xml` , ajoutez le fichier `allowProxy` et `categories` propriétés.
   >
   > * `allowProxy = [Boolean]true`
   > * `categories= customfunctionsdemo`
   >Par exemple, dans ce cas : [custom-errorhandler-name] est fourni en tant que `customfunctionsdemo`.

1. Enregistrez le fichier `function.js`.
1. Accédez au dossier `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/clientlibs/js`.
1. Ajoutez un fichier texte en tant que `js.txt`. Le fichier contient :

   ```javascript
       #base=js
       functions.js
   ```

1. Enregistrez le fichier `js.txt`.\
   La structure de dossiers créée ressemble à ce qui suit :

   ![Structure de dossier de bibliothèque cliente créée](/help/forms/assets/customclientlibrary_folderstructure.png)

   >[!NOTE]
   >
   > Pour en savoir plus sur la création de fonctions personnalisées, cliquez sur [fonctions personnalisées dans l’éditeur de règles](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-rules-and-use-expressions-in-an-adaptive-form/rule-editor.html?lang=fr#write-rules).

1. Ajoutez, validez et envoyez les modifications dans le référentiel à l’aide des commandes ci-dessous :

   ```javascript
       git add .
       git commit -a -m "Adding error handling files"
       git push
   ```

1. [Exécuter le pipeline.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#setup-pipeline)

Une fois le pipeline exécuté, le gestionnaire d’erreurs personnalisé devient disponible dans l’éditeur de règles de formulaire adaptatif. Maintenant, apprenons comment configurer et utiliser un gestionnaire d’erreurs personnalisé à l’aide du service Invoke de l’éditeur de règles dans AEM Forms.

#### 2. Utiliser l’éditeur de règles pour configurer le gestionnaire d’erreurs personnalisé {#use-custom-error-handler}

Avant d’implémenter le gestionnaire d’erreurs personnalisé dans un formulaire adaptatif, assurez-vous que le nom de la bibliothèque cliente dans la variable **[!UICONTROL Catégorie de bibliothèque cliente]** s’aligne sur le nom spécifié dans l’option categories de la variable `.content.xml` fichier .

![Ajout du nom de la bibliothèque cliente dans la configuration du conteneur de formulaires adaptatifs](/help/forms/assets/client-library-category-name.png)

Dans ce cas, le nom de la bibliothèque cliente est fourni comme suit : `customfunctionsdemo` dans le `.content.xml` fichier .

Pour utiliser un gestionnaire d’erreurs personnalisé à l’aide de l’action **[!UICONTROL Service Invoke de l’éditeur de règles]** :

1. Ouvrez un formulaire adaptatif en mode création, sélectionnez un composant de formulaire et appuyez sur **[!UICONTROL Éditeur de règles]** pour ouvrir ce dernier.
1. Appuyez sur **[!UICONTROL Créer]**.
1. Définissez une condition dans la section **Lorsque** de la règle. Par exemple, lorsque **[Nom du champ Identifiant de l’animal domestique]** est modifié, sélectionnez **est modifié** dans la liste déroulante **Sélectionner un état**.
1. Dans la section **Then** (Alors), sélectionnez **[!UICONTROL Invoke Service]** (Appeler un service) dans la liste déroulante **Select Action** (Sélectionner une action).
1. Sélectionnez un **service Post** et ses liaisons de données correspondantes dans la section **Entrée**. Par exemple, pour valider **Identifiant d’animal domestique**, sélectionnez un **service Post** comme **GET /pet/{petId}**, puis sélectionnez **Identifiant d’animal domestique** dans la section **Entrée**.
1. Sélectionnez les liaisons de données dans la section **Sortie**. Par exemple, sélectionnez **Nom de l’animal domestique** dans la section **Sortie**.
1. Sélectionnez **[!UICONTROL Gestionnaire d’erreurs personnalisé]** dans la section **[!UICONTROL Gestionnaire d’erreurs]**.
1. Cliquez sur **[!UICONTROL Terminé]**.

![ajouter un gestionnaire d’erreurs personnalisé dans un formulaire pour gérer les réponses aux erreurs](/help/forms/assets/custom-error-handler.png)

À la suite de cette règle, les valeurs que vous saisissez pour **Identifiant d’animal domestique** vérifie la validation du **Nom de l’animal domestique** à l’aide du service externe appelé par le point d’entrée REST. Si les critères de validation basés sur la source de données échouent, les messages d’erreur s’affichent au niveau du champ.

![ajouter un gestionnaire d’erreurs personnalisé dans un formulaire pour gérer les réponses aux erreurs](/help/forms/assets/custom-error-handler-message.png)

Ouvrez la console du navigateur et vérifiez le message d’erreur de validation de la réponse et de l’en-tête reçus du point d’entrée du service REST.


La fonction de gestionnaire d’erreurs personnalisé est chargée de l’exécution d’actions supplémentaires telles que l’affichage d’une boîte de dialogue modale ou l’envoi d’un événement d’analyse, en fonction de la réponse à l’erreur. Une fonction de gestionnaire d’erreurs personnalisé offre la possibilité de personnaliser la gestion des erreurs en fonction des besoins spécifiques de l’utilisateur ou utilisatrice.

<!-- 

## Configure Adaptive Form submission to add custom handlers {#configure-adaptive-form-submission}

If the server validation error message does not display in the standard format, you can enable asynchronous submission and add a custom error handler on Adaptive Form submission to convert the message into a standard format.

### Configure asynchronous Adaptive Form submission {#configure-asynchronous-adaptive-form-submission}

Before adding custom handler, you must configure the adaptive form for asynchronous submission. Execute the following steps:

1. In adaptive form authoring mode, select the Form Container object and tap ![adaptive form properties](assets/configure_icon.png) to open its properties.
1. In the **[!UICONTROL Submission]** properties section, enable **[!UICONTROL Use asynchronous submission]**.
1. Select **[!UICONTROL Revalidate on server]** to validate the input field values on server before submission.
1. Select the Submit Action:

    * Select **[!UICONTROL Submit using Form Data Model]** and select the appropriate data model, if you are using RESTful web service based [form data model](work-with-form-data-model.md) as the data source.
    * Select **[!UICONTROL Submit to REST Service endpoint]** and specify the **[!UICONTROL Redirect URL/Path]**, if you are using RESTful web services as the data source.

    ![adaptive form submission properties](assets/af_submission_properties.png)

1. Tap ![Save](assets/save_icon.png) to save the properties.

### Add custom error handler on Adaptive Form submission {#add-custom-error-handler-af-submission}

AEM Forms provides out-of-the-box success and error handlers for form submissions. Handlers are client-side functions that execute based on the server response. When an Adaptive Form is submitted, the data is transmitted to the server for validation, which returns a response to the client with information about the success or error event for the submission. The information is passed as parameters to the relevant handler to execute the function.

Execute the following steps to add custom error handler on Adaptive Form submission:

1. Open an Adaptive Form in authoring mode, select any form object, and tap  to open the rule editor.
1. Select **[!UICONTROL Form]** in the Form Objects tree and tap **[!UICONTROL Create]**.
1. Select **[!UICONTROL Error in Submission]** from the Event drop-down list.
1. Write a rule to convert custom error structure to the standard error structure and tap **[!UICONTROL Done]** to save the rule.

The following is a sample code to convert a custom error structure to the standard error structure:

```javascript
var data = $event.data;
var som_map = {
    "id": "guide[0].guide1[0].guideRootPanel[0].Pet[0].id_1[0]",
    "name": "guide[0].guide1[0].guideRootPanel[0].Pet[0].name_2[0]",
    "status": "guide[0].guide1[0].guideRootPanel[0].Pet[0].status[0]"
};

var errorJson = {};
errorJson.errors = [];

if (data) {
    if (data.originMessage) {
        var errorData;
        try {
            errorData = JSON.parse(data.originMessage);
        } catch (err) {
            // not in json format
        }

        if (errorData) {
            Object.keys(errorData).forEach(function(key) {
                var som_key = som_map[key];
                if (som_key) {
                    var error = {};
                    error.somExpression = som_key;
                    error.errorMessage = errorData[key];
                    errorJson.errors.push(error);
                }
            });
        }
        window.guideBridge.handleServerValidationError(errorJson);
    } else {
        window.guideBridge.handleServerValidationError(data);
    }
}
```

The `var som_map` lists the SOM expression of the Adaptive Form fields that you want to transform into the standard format. You can view the SOM expression of any field in an adaptive form by tapping the field and selecting **[!UICONTROL View SOM Expression]**.

Using this custom error handler, the adaptive form converts the fields listed in `var som_map` to standard error message format. As a result, the validation error messages display at field-level in the adaptive form.

 -->


## Voir également {#see-also}

{{see-also}}
* [Création et utilisation de gestionnaires d’erreurs personnalisés dans Forms adaptatif (composants principaux)](/help/forms/add-custom-error-handler-adaptive-forms-core-components.md)

<!--

>[!MORELIKETHIS]
>
>* [Create style or themes for your forms](/help/forms/using-themes-in-core-components.md)
>* [Create or add an Adaptive Form to AEM Sites page](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)

-->
