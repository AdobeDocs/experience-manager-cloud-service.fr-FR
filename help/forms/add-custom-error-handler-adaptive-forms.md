---
title: Ajouter des gestionnaires d’erreurs personnalisés dans les formulaires adaptatifs pour les formulaires adaptatifs AEM
description: AEM Forms fournit des gestionnaires de réussite et d’erreur prêts à l’emploi pour un formulaire à l’aide du point d’entrée REST configuré pour appeler un service externe. Vous pouvez ajouter un gestionnaire d’erreurs par défaut et un gestionnaire d’erreurs personnalisé dans un formulaire adaptatif AEM.
keywords: Ajouter un gestionnaire d’erreurs personnalisé, ajouter un gestionnaire d’erreurs par défaut, ajouter un gestionnaire d’erreurs dans le formulaire, utiliser le service d’appel de l’éditeur de règles pour ajouter un gestionnaire d’erreurs personnalisé, configurer l’éditeur de règles pour ajouter un gestionnaire d’erreurs personnalisé, ajouter un gestionnaire d’erreurs personnalisé à l’aide de l’éditeur de règles
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Foundation Components
exl-id: 198a26a9-d6bb-457d-aab8-0a5d15177c48
role: User, Developer
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '2308'
ht-degree: 90%

---

# Ajout de gestionnaires d’erreur personnalisés dans AEM Adaptive Forms {#error-handlers-in-adaptive-form}

>[!NOTE]
>
> Adobe recommande d’utiliser la capture de données moderne et extensible [composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr) pour [créer un nouveau Forms adaptatif](/help/forms/creating-adaptive-form-core-components.md) ou [ajouter un Forms adaptatif aux pages AEM Sites](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Ces composants représentent une avancée significative dans la création de formulaires adaptatifs, ce qui garantit des expériences utilisateur impressionnantes. Cet article décrit une ancienne approche de création de Forms adaptatif à l’aide de composants de base.

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/standard-validation-error-messages-adaptive-forms.html?lang=fr) |
| AEM as a Cloud Service | Cet article |

AEM Forms fournit des gestionnaires de succès et d’erreur prêts à l’emploi pour les envois de formulaires. Il fournit également une fonctionnalité pour personnaliser les fonctions du gestionnaire d’erreurs. Par exemple, vous pouvez appeler un workflow personnalisé dans le serveur principal pour des codes d’erreur spécifiques ou informer le client ou la cliente que le service ne fonctionne pas. Les gestionnaires sont des fonctions côté client qui s’exécutent selon la réponse du serveur. Lorsqu’un service extérieur est sollicité via API, les données sont transmises au serveur pour validation, ce qui renvoie une réponse au client ou à la cliente avec des informations concernant le succès ou l’erreur de l’envoi. Les informations sont transmises comme paramètres au gestionnaire approprié pour exécuter la fonction. Un gestionnaire d’erreurs permet de gérer et d’afficher les erreurs ou les problèmes de validation rencontrés.

![workflow du gestionnaire d’erreurs pour comprendre comment ajouter un gestionnaire d’erreurs personnalisé dans les formulaires](/help/forms/assets/error-handler-workflow.png)

Le formulaire adaptatif valide les entrées que vous fournissez dans les champs en fonction de critères de validation prédéfinis et vérifie diverses erreurs renvoyées par le point d&#39;entrée REST configuré pour appeler un service externe. Vous pouvez définir les critères de validation en fonction de la source de données que vous utilisez avec le formulaire adaptatif. Par exemple, si vous utilisez des services web RESTful comme source de données, vous pouvez définir les critères de validation dans un fichier de définition Swagger.

Si les valeurs d’entrée répondent aux critères de validation, les valeurs sont envoyées à la source de données, sinon le formulaire adaptatif affiche un message d’erreur à l’aide d’un gestionnaire d’erreurs. De la même manière, les formulaires adaptatifs s’intègrent à des gestionnaires d’erreurs personnalisés pour effectuer des validations de données. Si les valeurs d’entrée ne répondent pas aux critères de validation, les messages d’erreur s’affichent au niveau du champ dans le formulaire adaptatif. Cela se produit lorsque le message d’erreur de validation renvoyé par le serveur est au format standard du message.


## Utilisation des gestionnaires d’erreurs {#uses-of-error-handler}

Les gestionnaires d’erreurs sont utilisés à diverses fins. Certaines des utilisations des fonctions de gestionnaire d’erreurs sont répertoriées ci-dessous :

* **Validation** : la gestion des erreurs commence par la validation des entrées utilisateur par rapport à des règles ou critères prédéfinis. Lorsque les utilisateurs et utilisatrices remplissent un formulaire adaptatif, le gestionnaire d’erreurs valide l’entrée afin de s’assurer qu’elle respecte le format, la longueur ou toute autre contrainte requise.

* **Fournir des commentaires en temps réel** : lorsqu’une erreur est détectée, le gestionnaire d’erreurs affiche des commentaires immédiats à l’utilisateur ou à l’utilisatrice, tels que des messages d’erreur intégrés sous les champs de formulaire correspondants. Ces commentaires permettent aux utilisateurs et utilisatrices d’identifier et de corriger les erreurs sans avoir à envoyer le formulaire et attendre une réponse.


* **Affichage des messages d’erreur** : lorsqu’un envoi de formulaire adaptatif rencontre une erreur de validation, le gestionnaire d’erreurs affiche un message d’erreur approprié. Les messages d’erreur doivent être clairs, concis et mettre en évidence les champs spécifiques qui nécessitent une attention particulière.

* **Mise en surbrillance du champ erroné** : pour attirer l’attention de l’utilisateur et de l’utilisatrice sur des champs incorrects spécifiques, le gestionnaire d’erreurs surligne ou distingue visuellement les champs correspondants. Cette action est effectuée en modifiant la couleur de l’arrière-plan, en ajoutant une icône ou une bordure, ou tout autre indice visuel qui aide les utilisateurs ou les utilisatrices à localiser et à corriger rapidement les erreurs.


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

* `errorCausedBy` décrit le motif de l’échec.
* `errors` mentionne l’expression SOM des champs qui ont échoué aux critères de validation avec le message d’erreur de validation.
* Champ `originCode` ajouté par AEM et contenant le code d’état http renvoyé par le service externe.
* Champ `originMessage` ajouté par AEM et contenant les données d’erreur brutes renvoyées par le service externe.

Avec les améliorations des fonctionnalités et les mises à jour ultérieures dans les versions d’AEM Forms, la structure existante de réponse aux échecs a été changée en un nouveau format basé sur RFC7807, qui est rétrocompatible avec la structure de réponse aux échecs existante :

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
> * Assurez-vous que la structure de la réponse d’erreur inclut : **fieldName** ou **dataRef**.
> * Assurez-vous que l’en-tête **ContentType** est **application/problème+json**.

Où :

* `type (required)` spécifie le type d’échec. Il peut s’agir de l’une des valeurs suivantes :
   * `SERVER_SIDE_VALIDATION` indique un échec en raison de la validation côté serveur.
   * `FORM_SUBMISSION` indique un échec lors de l’envoi du formulaire.
   * `SERVICE_INVOCATION` indique un échec lors de l’appel de service tiers.
   * `FAILURE` indique un échec général.
   * `VALIDATION_ERROR` indique un échec en raison d’une erreur de validation.

* `title (optional)` fournit un titre ou une brève description de l’échec.
* `detail (optional)` fournit des détails supplémentaires sur l’échec, si nécessaire.
* `instance (optional)` représente une instance ou un identifiant associé à l’échec et permet de suivre ou d’identifier l’occurrence spécifique de l’échec.
* `validationErrors (required)` contient des informations sur les erreurs de validation. Les champs suivants sont inclus :
   * `fieldname` mentionne l’expression SOM des champs qui ont échoué aux critères de validation.
   * `dataRef` représente le chemin JSON ou XPath des champs qui ont échoué à la validation.
   * `details` contiennent le message d’erreur de validation avec le champ erroné.
* `originCode (optional)` est un champ ajouté par AEM, qui contient le code d’état http renvoyé par le service externe.
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

  ![Expression SOM d’un champ de formulaire adaptatif permettant d’afficher la réponse d’erreur dans le gestionnaire d’erreurs personnalisé.](/help/forms/assets/custom-error-handler-somexpression.png)

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

  ![Référence de données d’un champ de formulaire adaptatif permettant d’afficher la réponse d’erreur dans le gestionnaire d’erreurs personnalisé.](/help/forms/assets/custom-errorhandler-dataref.png)

Vous pouvez afficher la valeur de dataRef dans la fenêtre **[!UICONTROL Propriétés]** d’un composant de formulaire.

+++


## Ajouter un gestionnaire d’erreurs à l’aide de l’éditeur de règles {#add-error-handler-using-rule-editor}

En utilisant l’action [Appeler un service de l’éditeur de règles](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=fr#invoke), vous définissez le critère de validation en fonction de la source de données que vous utilisez avec le formulaire adaptatif. Par exemple, si vous utilisez des services web RESTful comme source de données, vous pouvez définir les critères de validation dans un fichier de définition Swagger. En utilisant les fonctions de gestionnaire d’erreurs et l’éditeur de règles dans les formulaires adaptatifs, vous pouvez contrôler et personnaliser efficacement la gestion des erreurs. Vous définissez les conditions à l’aide de l’éditeur de règles et configurez les actions à effectuer lorsque la règle est déclenchée. Un formulaire adaptatif valide les entrées que vous fournissez dans les champs en fonction de critères de validation prédéfinis. Si les valeurs d’entrée ne répondent pas aux critères de validation, les messages d’erreur s’affichent au niveau du champ dans un formulaire adaptatif.

>[!NOTE]
>
> * Pour utiliser des gestionnaires d’erreurs avec l’action Appel du service de l’éditeur de règles, configurez le Forms adaptatif avec un modèle de données de formulaire (FDM).
> * Un gestionnaire d’erreurs par défaut est fourni pour afficher les messages d’erreur sur les champs si la réponse à l’erreur se trouve dans le schéma standard. Vous pouvez également appeler le gestionnaire d’erreurs par défaut à partir de la fonction de gestionnaire d’erreur personnalisé.

L’éditeur de règles vous permet d’effectuer les opérations suivantes :

* [Ajouter la fonction de gestionnaire d’erreurs par défaut](#add-default-errror-handler)
* [Ajouter la fonction de gestionnaire d’erreurs personnalisé](#add-custom-error-handler-function)


### Ajouter la fonction de gestionnaire d’erreurs par défaut {#add-default-errror-handler}

Un gestionnaire d’erreurs par défaut est pris en charge pour afficher les messages d’erreur sur les champs si la réponse d’erreur se trouve dans le schéma standard ou dans un échec de validation côté serveur.
Pour comprendre comment créer et utiliser un gestionnaire d’erreurs par défaut à l’aide de l’action [Appeler un service de l’éditeur de règles](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=fr#invoke), prenons un exemple de formulaire adaptatif simple à deux champs, **Identifiant de l’animal domestique** et **Nom de l’animal domestique** et utilisons un gestionnaire d’erreurs standard sur le champ **Identifiant de l’animal domestique** pour vérifier les différentes erreurs renvoyées par le point d’entrée REST configuré pour appeler un service externe, par exemple, `200 - OK`,`404 - Not Found`, `400 - Bad Request`. Pour ajouter un gestionnaire d’erreur par défaut à l’aide de l’action Appeler un service de l’éditeur de règles, procéder comme suit :

1. Ouvrez un formulaire adaptatif en mode création, sélectionnez un composant de formulaire et sélectionnez **[!UICONTROL Éditeur de règles]** pour ouvrir ce dernier.
1. Sélectionnez **[!UICONTROL Créer]**.
1. Définissez une condition dans la section **Lorsque** de la règle. Par exemple, **lorsque le [Nom du champ Identifiant de l&#39;animal domestique]** est modifié. L’option Sélectionner est modifiée à partir de la liste déroulante **Sélectionner un état**.
1. Dans la section **Alors**, sélectionnez **[!UICONTROL Appeler un service]** dans la liste déroulante **Sélectionner une action**. 
1. Sélectionnez un **service Post** et ses liaisons de données correspondantes dans la section **Entrée**. Par exemple, pour valider **Pet ID**, sélectionnez un **service Post** comme **GET /pet/{petId}** et sélectionnez **Pet ID** dans la section **Entrée**.
1. Sélectionnez les liaisons de données dans la section **Sortie**. Par exemple, sélectionnez **Nom de l’animal domestique** dans la section **Sortie**.
1. Sélectionner **[!UICONTROL Gestionnaire d’erreurs par défaut]** dans la section **Gestionnaire d’erreurs** .
1. Cliquez sur **[!UICONTROL Terminé]**.

![ajouter un gestionnaire d’erreurs par défaut pour les contrôles de validation de champ dans un formulaire](/help/forms/assets/default-error-handler.png)

À la suite de cette règle, les valeurs que vous saisissez pour **Identifiant de l’animal domestique** vérifient la validation du **Nom de l’animal domestique** à l’aide du service externe appelé par le point d&#39;entrée REST. Si les critères de validation basés sur la source de données échouent, les messages d’erreur s’affichent au niveau du champ.

![afficher le message d’erreur par défaut lorsque vous ajoutez un gestionnaire d’erreurs par défaut dans un formulaire pour gérer les réponses d’erreur](/help/forms/assets/default-error-message.png)

### Ajouter la fonction de gestionnaire d’erreurs personnalisé

Vous pouvez ajouter une fonction de gestionnaire d’erreurs personnalisé pour effectuer certaines des actions suivantes :

* gérer les réponses d’erreur qui utilisent des réponses d’erreur non standard ou standard. Il est important de noter que ces réponses d’erreur non standard ne sont pas conformes au [schéma standard des réponses d’erreur](#failure-response-format).
* envoyer des événements Analytics à n’importe quelle plateforme Analytics ; Par exemple, Adobe Analytics.
* afficher la boîte de dialogue modale avec les messages d’erreur.

Outre les actions mentionnées, les gestionnaires d’erreurs personnalisés peuvent être utilisés pour exécuter des fonctions personnalisées répondant à des besoins spécifiques de l’utilisateur ou de l’utilisatrice.

Le gestionnaire d’erreurs personnalisé est une fonction (bibliothèque cliente) conçue pour répondre aux erreurs renvoyées par un service externe et fournir une réponse personnalisée aux utilisateurs finaux et utilisatrices finales. Toute bibliothèque cliente avec l’annotation `@errorHandler` est considérée comme une fonction de gestionnaire d’erreurs personnalisé. Cette annotation permet d’identifier la fonction de gestionnaire d’erreurs spécifiée dans le fichier `.js`.
Pour comprendre comment créer et utiliser un gestionnaire d’erreurs personnalisé à l’aide de l’action [Service Invoke de l’éditeur de règles](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=fr#invoke), prenons un exemple de formulaire adaptatif avec deux champs, **Identifiant d’animal domestique** et **Nom de l’animal domestique** et utilisez un gestionnaire d’erreurs personnalisé sur le champ **Identifiant d’animal domestique** pour vérifier les différentes erreurs renvoyées par le point d’entrée REST configuré pour appeler un service externe, par exemple : `200 - OK`,`404 - Not Found`, `400 - Bad Request`.

Pour ajouter et utiliser un gestionnaire d’erreurs personnalisé dans un formulaire adaptatif, procédez comme suit :

1. [Ajout d’une fonction personnalisée pour le gestionnaire d’erreurs](#1-add-the-custom-function-for-the-error-handler)
2. [Utilisez l’éditeur de règles pour configurer le gestionnaire d’erreurs personnalisé.](#use-custom-error-handler)

#### &#x200B;1. Ajoutez la fonction personnalisée pour le gestionnaire d’erreurs

Pour savoir comment ajouter des fonctions personnalisées, cliquez sur [Créer des fonctions personnalisées dans un formulaire adaptatif basé sur les composants principaux](/help/forms/custom-function-core-component-create-function.md#create-a-custom-function).

<!-- To create a custom error function, perform the following steps:

1. [Clone your AEM Forms as a Cloud Service Repository](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#accessing-git). 
2. Create a folder under the `[AEM Forms as a Cloud Service repository folder]/apps/` folder. For example, create a folder named as `experience-league`
3. Navigate to `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/experience-league/` and create a `ClientLibraryFolder` as `clientlibs`.
4. Create a folder named `js`.
5. Navigate to the `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/clientlibs/js` folder. -->

1. Ajoutez le code ci-dessous pour le gestionnaire d’erreurs personnalisé dans le fichier JavaScript, par exemple `function.js`. Le fichier comprend le code du gestionnaire d’erreurs personnalisé.
Ajoutons le code suivant au fichier JavaScript pour afficher la réponse et les en-têtes, reçus du point d’entrée du service REST, dans la console du navigateur.

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

   >[!NOTE]
   >
   > * Pour appeler le gestionnaire d’erreurs par défaut depuis votre gestionnaire d’erreurs personnalisé, la ligne suivante de l’exemple de code est utilisée : `guidelib.dataIntegrationUtils.defaultErrorHandler(response, headers) `
   > * Dans le fichier `.content.xml`, ajoutez les propriétés `allowProxy` et `categories` pour utiliser la bibliothèque cliente de gestionnaire d’erreurs personnalisé dans un formulaire adaptatif.
   >
   >   * `allowProxy = [Boolean]true`
   >   * `categories= customfunctionsdemo`
   >       Par exemple, dans ce cas, [custom-errorhandler-name] est fourni comme `customfunctionsdemo`.


1. Ajoutez, validez et transmettez les modifications dans le référentiel.

<!--

<!--
1. Save the `function.js` file.
1. Navigate to the `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/clientlibs/js` folder.
2. Add a text file as `js.txt`. The file contains:

    ```javascript
        #base=js
        functions.js
    ```

3. Save the `js.txt` file.    
The created folder structure looks like:

    ![Created Client Library Folder Structure](/help/forms/assets/customclientlibrary_folderstructure.png) 
    using the below commands:
         
    ```javascript

        git add .
        git commit -a -m "Adding error handling files"
        git push
    ```
-->

1. [Exécutez le pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=fr#setup-pipeline).

Une fois le pipeline exécuté, le gestionnaire d’erreurs personnalisé devient disponible dans l’éditeur de règles de formulaire adaptatif. Maintenant, apprenons comment configurer et utiliser un gestionnaire d’erreurs personnalisé à l’aide du service Invoke de l’éditeur de règles dans AEM Forms.

#### 2. Utiliser l’éditeur de règles pour configurer le gestionnaire d’erreurs personnalisé {#use-custom-error-handler}

Avant d’implémenter le gestionnaire d’erreurs personnalisé dans un formulaire adaptatif, assurez-vous que le nom de la bibliothèque cliente de la **[!UICONTROL Catégorie de bibliothèque cliente]** s’aligne sur le nom spécifié dans l’option Catégories du fichier `.content.xml`.

![Ajout du nom de la bibliothèque cliente dans la configuration du conteneur de formulaires adaptatifs](/help/forms/assets/client-library-category-name.png)

Dans ce cas, le nom de la bibliothèque cliente est fourni comme `customfunctionsdemo` dans le fichier `.content.xml`.

Pour utiliser un gestionnaire d’erreurs personnalisé à l’aide de l’action **[!UICONTROL Service Invoke de l’éditeur de règles]** :

1. Ouvrez un formulaire adaptatif en mode création, sélectionnez un composant de formulaire et sélectionnez **[!UICONTROL Éditeur de règles]** pour ouvrir ce dernier.
1. Sélectionnez **[!UICONTROL Créer]**.
1. Définissez une condition dans la section **Lorsque** de la règle. Par exemple, lorsque **[Nom du champ Identifiant de l’animal]** est modifié, sélectionnez **est modifié** dans la liste déroulante **Sélectionner un état**.
1. Dans la section **Alors**, sélectionnez **[!UICONTROL Service Invoke]** dans la liste déroulante **Sélectionner une action**.
1. Sélectionnez un **service Post** et ses liaisons de données correspondantes dans la section **Entrée**. Par exemple, pour valider **Pet ID**, sélectionnez un **service Post** comme **GET /pet/{petId}** et sélectionnez **Pet ID** dans la section **Entrée**.
1. Sélectionnez les liaisons de données dans la section **Sortie**. Par exemple, sélectionnez **Nom de l’animal** dans la section **Sortie**.
1. Sélectionnez **[!UICONTROL Gestionnaire d’erreurs personnalisé]** dans la section **[!UICONTROL Gestionnaire d’erreurs]**.
1. Cliquez sur **[!UICONTROL Terminé]**.

![ajouter un gestionnaire d’erreurs personnalisé dans un formulaire pour gérer les réponses aux erreurs](/help/forms/assets/custom-error-handler.png)

À la suite de cette règle, les valeurs que vous saisissez pour **Identifiant d’animal** vérifient la validation du **Nom de l’animal** à l’aide du service externe appelé par le point d’entrée REST. Si les critères de validation basés sur la source de données échouent, les messages d’erreur s’affichent au niveau du champ.

![ajouter un gestionnaire d’erreurs personnalisé dans un formulaire pour gérer les réponses aux erreurs](/help/forms/assets/custom-error-handler-message.png)

Ouvrez la console du navigateur et vérifiez le message d’erreur de validation de la réponse et de l’en-tête reçus du point d’entrée du service REST.


La fonction de gestionnaire d’erreurs personnalisé est chargée de l’exécution d’actions supplémentaires telles que l’affichage d’une boîte de dialogue modale ou l’envoi d’un événement d’analyse, en fonction de la réponse à l’erreur. Une fonction de gestionnaire d’erreurs personnalisé offre la possibilité de personnaliser la gestion des erreurs en fonction des besoins spécifiques de l’utilisateur ou utilisatrice.

