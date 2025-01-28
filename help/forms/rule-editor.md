---
title: Comment utiliser l’éditeur de règles pour ajouter des règles aux champs de formulaire afin d’ajouter un comportement dynamique et de créer une logique complexe à un formulaire adaptatif ?
description: L’éditeur de règles de Forms adaptatif vous permet d’ajouter un comportement dynamique et de créer une logique complexe dans des formulaires sans codage ni script.
feature: Adaptive Forms, Foundation Components
role: User, Developer
level: Beginner, Intermediate
exl-id: 6fd38e9e-435e-415f-83f6-3be177738c00
source-git-commit: b5340c23f0a2496f0528530bdd072871f0d70d62
workflow-type: tm+mt
source-wordcount: '6492'
ht-degree: 96%

---

# Ajout de règles à un formulaire adaptatif {#adaptive-forms-rule-editor}

>[!NOTE]
>
> Adobe recommande d’utiliser la capture de données moderne et extensible [composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr) pour [créer un nouveau Forms adaptatif](/help/forms/creating-adaptive-form-core-components.md) ou [ajouter un Forms adaptatif aux pages AEM Sites](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Ces composants représentent une avancée significative dans la création de formulaires adaptatifs, ce qui garantit des expériences utilisateur impressionnantes. Cet article décrit une ancienne approche de création de Forms adaptatif à l’aide de composants de base.

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM as a Cloud Service (composants de base) | Cet article |
| AEM as a Cloud Service (composants principaux) | [Cliquez ici](/help/forms/rule-editor-core-components.md) |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html) |

## Vue d’ensemble {#overview}

La fonctionnalité d’éditeur de règles permet aux utilisateurs professionnels et aux développeurs de formulaires de créer des règles sur des objets de formulaire adaptatif. Ces règles déterminent les actions à déclencher sur des objets de formulaire en fonction des conditions prédéfinies, des entrées de l’utilisateur et des actions de l’utilisateur sur le formulaire. Cela permet de rationaliser davantage l’expérience de remplissage du formulaire en assurant précision et vitesse.

L’éditeur de règles fournit une interface utilisateur intuitive et simplifiée pour la création de règles. L’éditeur de règles met un éditeur visuel à disposition de tous les utilisateurs.<!-- In addition, only for forms power users, rule editor provides a code editor to write rules and scripts. --> Vous pouvez exécuter différentes actions sur des objets de formulaire adaptatif utilisant des règles, comme :

* Afficher ou masquer un objet
* Activer ou désactiver un objet
* Définir une valeur pour un objet
* Valider la valeur d’un objet
* Exécuter les fonctions de calcul de la valeur d’un objet
* Appeler un service de modèle de données de formulaire et exécuter une opération
* Définir la propriété d’un objet

<!-- Rule editor replaces the scripting capabilities in [!DNL Experience Manager 6.1 Forms] and earlier releases. However, your existing scripts are preserved in the new rule editor. For more information about working with existing scripts in the rule editor, see [Impact of rule editor on existing scripts](rule-editor.md#p-impact-of-rule-editor-on-existing-scripts-p). -->

Les utilisateurs ajoutés au groupe des utilisateurs avancés de formulaires peuvent créer des scripts et modifier des scripts existants. Les utilisateurs appartenant au groupe [!DNL forms-users] peuvent utiliser les scripts, mais ne peuvent ni en créer ni en modifier.

## Différences entre l’éditeur de règles dans les composants principaux et l’éditeur de règles dans les composants de base

{{rule-editor-diff}}

## Présentation d’une règle {#understanding-a-rule}

Une règle est une combinaison d’actions et de conditions. Dans l’éditeur de règles, les actions incluent des activités telles que masquer, afficher, activer, désactiver ou calculer la valeur d’un objet dans un formulaire. Les conditions sont des expressions booléennes qui sont évaluées en effectuant des vérifications et des opérations sur l’état, la valeur ou la propriété d’un objet de formulaire. Les actions sont exécutées en fonction de la valeur (`True` ou `False`) renvoyée par l’évaluation d’une condition.

L’éditeur de règles fournit un ensemble de types de règle prédéfinis, tels que Lorsque, Afficher, Masquer, Activer, Désactiver, Définir la valeur de et Valider pour vous aider à créer des règles. Chaque type de règle vous permet de définir des conditions et des actions dans une règle. Le document décrit de façon plus détaillée chaque type de règle.

Une règle suit généralement l’un des concepts suivants :

**Condition-action** Dans ce concept, une règle définit d’abord une condition suivie d’une action à déclencher. Le concept est comparable à l’instruction if-then des langages de programmation.

Dans l’éditeur de règles, le type de règle **Lorsque** applique le concept de condition-action.

**Action-condition** Dans ce concept, une règle définit d’abord une action à déclencher suivie de conditions d’évaluation. Une autre variante de ce concept est une action alternative d’action-condition, qui définit également une action alternative à déclencher si la condition renvoie la valeur False.

Les types de règles Afficher, Masquer, Activer, Désactiver, Définir la valeur de et Valider de l’éditeur de règles appliquent le concept de règle d’action-condition. Par défaut, l’action alternative d’Afficher est Masquer et l’action alternative d’Activer est Désactiver, et inversement. Vous ne pouvez pas modifier l’action alternative par défaut.

>[!NOTE]
>
>Les types de règles disponibles, y compris les conditions et actions que vous définissez dans l’éditeur de règles, dépendent également du type d’objet de formulaire sur lequel vous créez une règle. L’éditeur de règles affiche uniquement les types de règle et les options valides lors de la création des instructions de condition et d’action pour un type particulier d’objet de formulaire. Par exemple, les types de règle Valider, Définir la valeur de, Activer et Désactiver ne s’affichent pas pour un objet de panneau.

Pour plus d’informations sur les types de règles disponibles dans l’éditeur de règles, reportez-vous à la section [Types de règles disponibles dans l’éditeur de règles](rule-editor.md#p-available-rule-types-in-rule-editor-p).

### Recommandations pour la sélection d’un concept de règle {#guidelines-for-choosing-a-rule-construct}

Même si vous pouvez obtenir la plupart des cas d’utilisation avec n’importe quel concept de règle, voici quelques recommandations pour sélectionner un concept plutôt qu’un autre. Pour plus d’informations sur les règles disponibles dans l’éditeur de règles, reportez-vous à la section [Types de règles disponibles dans l’éditeur de règles](rule-editor.md#p-available-rule-types-in-rule-editor-p).

* Lors de la création d’une règle, réfléchissez d’abord au contexte de l’objet pour lequel vous la créez. Supposons que vous souhaitiez masquer ou afficher le champ B en fonction de la valeur spécifiée par un utilisateur ou une utilisatrice dans le champ A. Dans ce cas, vous évaluez une condition sur le champ A, et selon la valeur qu’elle renvoie, vous déclenchez une action sur le champ B.

  Par conséquent, si vous créez une règle pour le champ B (l’objet pour lequel vous évaluez une condition), utilisez le concept de condition-action ou le type de règle Lorsque. De même, utilisez le concept d’action-condition ou le type de règle Afficher ou Masquer pour le champ A.

* Parfois, vous devez exécuter plusieurs actions en fonction d’une condition. Dans pareils cas, il est recommandé d’utiliser le concept de condition-action. Dans ce concept, vous pouvez évaluer une condition une fois et spécifier plusieurs instructions d’action.

  Par exemple, pour masquer les champs B, C et D en fonction de la condition qui vérifie la valeur spécifiée par un utilisateur ou une utilisatrice dans le champ A, écrivez une règle avec le concept de condition-action ou le type de règle Lorsque dans le champ A et spécifiez les actions pour contrôler la visibilité des champs B, C et D. Dans le cas contraire, vous avez besoin de trois règles distinctes sur les champs B, C et D, où chaque règle vérifie la condition et affiche ou masque le champ correspondant. Dans cet exemple, il est plus efficace de créer le type de règle Lorsque sur un objet plutôt que le type de règle Afficher ou Masquer sur trois objets.

* Pour déclencher une action selon plusieurs conditions, il est recommandé d’utiliser le concept d’action-condition. Par exemple, pour afficher et masquer le champ A en évaluant les conditions des champs B, C et D, utilisez le type de règle Afficher ou Masquer sur le champ A.
* Utilisez le concept de condition-action ou d’action-condition si la règle contient une action pour une condition.
* Si une règle vérifie une condition et exécute immédiatement une action en fournissant une valeur dans un champ ou en quittant un champ, il est recommandé de créer une règle avec le concept de condition-action ou le type de règle Lorsque sur le champ sur lequel la condition est évaluée.
* La condition dans la règle Lorsque est évaluée lorsqu’un utilisateur modifie la valeur de l’objet pour lequel la règle Lorsque est appliquée. Cependant, si vous souhaitez déclencher l’action lorsque la valeur change du côté serveur, comme lorsque vous préremplissez la valeur, il est recommandé de créer une règle Lorsque qui déclenche l’action lors de l’initialisation du champ.
* Lorsque vous créez des règles pour les menus déroulants, les boutons radio ou les cases à cocher, les options ou les valeurs de ces objets de formulaire sont préremplies dans l’éditeur de règles.

## Types d’opérateur et événements disponibles dans l’éditeur de règles {#available-operator-types-and-events-in-rule-editor}

L’éditeur de règles fournit les opérateurs logiques et les événements suivants à l’aide desquels vous pouvez créer des règles.

* **est égal à**
* **n&#39;est pas égal à**
* **Commence par**
* **Se termine par**
* **Contient**
* **Est vide**
* **N’est pas vide**
* **A sélectionné :** renvoie la valeur True lorsque l’utilisateur sélectionne une option donnée pour une case à cocher, une liste déroulante, un bouton radio.
* **Est initialisé (événement) :** renvoie la valeur True si un objet de formulaire est généré dans le navigateur.
* **Est modifié (événement) :** renvoie la valeur True si l’utilisateur modifie la valeur saisie ou l’option sélectionnée pour un objet de formulaire.
* **Navigation(event) :** renvoie la valeur True lorsque l’utilisateur clique sur un objet de navigation. Les objets de navigation sont utilisés pour passer d’un panneau à l’autre.
* **Fin d’étape (événement) :** renvoie la valeur True lorsqu’une étape d’une règle se termine.
* **Envoi réussi (événement) :** renvoie la valeur True si les données ont bien été envoyées vers un modèle de données de formulaire.
* **Erreur dans l’envoi (événement) :** renvoie la valeur True si les données n’ont pas été envoyées vers un modèle de données de formulaire.

## Types de règle disponibles dans l’éditeur de règles {#available-rule-types-in-rule-editor}

L’éditeur de règles fournit un ensemble de types de règle prédéfinis que vous pouvez utiliser pour créer des règles. Examinons en détail chaque type de règle. Pour plus d’informations sur la création de règles dans l’éditeur de règles, reportez-vous à la section [Création de règles](rule-editor.md#p-write-rules-p).

### [!UICONTROL Lorsque] {#whenruletype}

Le type de règle **[!UICONTROL Lorsque]** suit le concept de règle d’**action alternative de condition-action** ou parfois simplement le concept de **condition-action**. Dans ce type de règle, vous spécifiez d’abord une condition à évaluer, puis une action à déclencher si la condition est remplie (`True`). Lors de l’utilisation du type de règle Lorsque, vous pouvez utiliser plusieurs opérateurs ET et OU afin de créer des [expressions imbriquées](#nestedexpressions).

Avec le type de règle Lorsque, vous pouvez évaluer une condition sur un objet de formulaire et exécuter des actions sur un ou plusieurs objets.

En clair, un type de règle Lorsque standard est structuré comme suit :

`When on Object A:`

`(Condition 1 AND Condition 2 OR Condition 3) is TRUE;`

`Then, do the following:`

Action 2 sur Objet B ;
ET 
Action 3 sur Objet C ;

_

Lorsque vous avez un composant à valeurs multiples, comme des boutons radio ou une liste, les options sont récupérées automatiquement et mises à disposition du créateur de la règle lorsque vous créez une règle pour ce composant. Vous n’avez pas besoin de saisir à nouveau les valeurs de l’option.

Prenons l’exemple d’une liste comportant quatre options : rouge, bleu, vert et jaune. Lors de la création de la règle, les options (boutons radio) sont automatiquement récupérées et mises à la disposition du créateur ou de la créatrice de la règle comme suit :

![Options d’affichage à valeurs multiples](assets/multivaluefcdisplaysoptions1.png)

Lorsque vous créez une règle Lorsque, vous pouvez déclencher l’action Effacer la valeur de. L’action Effacer la valeur d’efface la valeur de l’objet spécifié. L’option Effacer la valeur de dans l’instruction Lorsque permet de créer des conditions complexes comportant plusieurs champs.

![Effacer la valeur de](assets/clearvalueof1.png)

**[!UICONTROL Masquer]** Masque l’objet spécifié.

**[!UICONTROL Afficher]** Affiche l’objet spécifié.

**[!UICONTROL Activer]** Active l’objet spécifié.

**[!UICONTROL Désactiver]** Désactive l’objet spécifié.

**[!UICONTROL Appel du service]** Appelle un service configuré dans un modèle de données de formulaire (FDM). Lorsque vous sélectionnez l’opération Appel du service, un champ s’affiche. Lorsque vous touchez le champ, il affiche tous les services configurés dans tous les modèles de données de formulaire de votre instance [!DNL Experience Manager]. Lors du choix d’un service de modèle de données de formulaire (FDM), des champs supplémentaires permettant de mapper des objets de formulaire avec des paramètres d’entrée et de sortie pour le service spécifié apparaissent. Reportez-vous à l’exemple de règle pour appeler des services de modèle de données de formulaire.

Outre le service de modèle de données de formulaire, vous pouvez spécifier une URL WSDL directe pour appeler un service Web. Cependant, un service de modèle de données de formulaire possède de nombreux avantages et l’approche recommandée permettant d’appeler un service.

Pour plus d’informations sur la configuration des services dans le modèle de données de formulaire, voir [[!DNL Experience Manager Forms] Intégration de données](data-integration.md).

**[!UICONTROL Définir la valeur de]** Calcule et définit la valeur de l’objet spécifié. Vous pouvez définir cette valeur par une chaîne, la valeur d’un autre objet, la valeur calculée avec une expression ou une fonction mathématique, la valeur d’une propriété d’un objet ou la valeur de sortie d’un service de modèle de données de formulaire configuré. Lorsque vous sélectionnez l’option Service web, elle affiche tous les services configurés dans tous les modèles de données de formulaire de votre instance [!DNL Experience Manager]. Lorsque vous sélectionnez un service de modèle de données de formulaire, des champs supplémentaires s’affichent dans lesquels vous pouvez mapper des objets de formulaire à des paramètres d’entrée et de sortie pour le service spécifié.

Pour plus d’informations sur la configuration des services dans le modèle de données de formulaire, voir [[!DNL Experience Manager Forms] Intégration de données](data-integration.md).

Le type de règle **[!UICONTROL Définir la propriété]** permet de définir la valeur d’une propriété de l’objet spécifié en fonction d’une action de condition. Vous pouvez définir la propriété sur l’une des options suivantes :
* visible (booléen)
* dorExclusion (booléen)
* chartType (chaîne)
* title (chaîne)
* enabled (booléen)
* mandatory (booléen)
* validationsDisabled (booléen)
* validateExpMessage (chaîne)
* value (nombre, chaîne, date)
* items (liste)
* valid (booléen)
* errorMessage (chaîne)

Elle permet, par exemple, de définir des règles pour ajouter dynamiquement des cases à cocher au formulaire adaptatif. Pour définir une règle, vous pouvez utiliser une fonction personnalisée, un objet de formulaire ou une propriété d’objet.

![Définir la propriété](assets/set_property_rule_new1.png)

Pour définir une règle basée sur une fonction personnalisée, sélectionnez **[!UICONTROL Sortie de fonction]** dans la liste déroulante, puis faites glisser et déposez une fonction personnalisée à partir de l’onglet **[!UICONTROL Fonctions]**. Si l’action de condition est remplie, le nombre de cases à cocher définies dans la fonction personnalisée est ajouté au formulaire adaptatif.

Pour définir une règle basée sur un objet de formulaire, sélectionnez **[!UICONTROL Objet de formulaire]** dans la liste déroulante, puis faites glisser et déposez un objet de formulaire à partir de l’onglet **[!UICONTROL Objets de formulaire]**. Si l’action de condition est remplie, le nombre de cases à cocher définies dans l’objet de formulaire est ajouté au formulaire adaptatif.

Une règle Définir la propriété basée sur une propriété d’objet permet d’ajouter le nombre de cases à cocher dans un formulaire adaptatif en fonction d’une autre propriété d’objet incluse dans le formulaire adaptatif.

La figure ci-dessous présente un exemple d’ajout dynamique de cases à cocher en fonction du nombre de listes déroulantes dans le formulaire adaptatif :

![Propriété de l’objet](assets/object_property_set_property_new1.png)

**[!UICONTROL Effacer la valeur de]** : efface la valeur de l’objet spécifié.

**[!UICONTROL Définir la cible d’action]**: définit la cible d’action sur l’objet spécifié.

**[!UICONTROL Enregistrer le formulaire]** : enregistre le formulaire.

**[!UICONTROL Envoyer les formulaires]** : envoie le formulaire.

**[!UICONTROL Réinitialiser le formulaire]** : réinitialise le formulaire.

**[!UICONTROL Valider le formulaire]** : valide le formulaire.

**[!UICONTROL Ajouter une instance]** : ajoute une instance de la ligne de panneau ou de tableau répétable spécifiée.

**[!UICONTROL Supprimer une instance]** : supprime une instance de la ligne de panneau ou de tableau répétable spécifiée.

**[!UICONTROL Accéder à]** : accédez à d’autres <!--Interactive Communications,-->formulaires adaptatifs, d’autres ressources, comme des images ou des fragments de document ou une URL externe. <!-- For more information, see [Add button to the Interactive Communication](create-interactive-communication.md#addbuttontothewebchannel). -->

### [!UICONTROL Définir la valeur de] {#set-value-of}

Le type de règle **[!UICONTROL Définir la valeur de]** permet de définir la valeur d’un objet de formulaire selon que la condition spécifiée est remplie ou non. La valeur peut être définie sur la valeur d’un autre objet, d’une chaîne littérale, la valeur dérivée d’une expression ou d’une fonction mathématique, la valeur d’une propriété d’un autre objet ou la sortie d’un service de modèle de données de formulaire. De même, vous pouvez vérifier la condition d’un composant, d’une chaîne, d’une propriété ou les valeurs dérivées d’une fonction ou d’une expression mathématique.

Notez que le type de règle **Définir la valeur de** n’est pas disponible pour tous les objets de formulaire, comme les boutons de panneaux et de barres d’outils. Une règle Définir la valeur de standard possède la structure suivante :

Définir la valeur d’Objet A sur :

(chaîne ABC) OU
(propriété d’objet X de l’objet C) OU
(valeur d’une fonction) OU
(valeur d’une expression mathématique) OU
(valeur de sortie d’un service de modèle de données ou d’un service Web) ;

Lorsque (facultatif) :

(Condition 1 ET Condition 2 ET Condition 3) est TRUE ;

L’exemple ci-dessous utilise la valeur du champ `dependentid` comme valeur d’entrée et définit la valeur du champ `Relation` comme valeur de sortie de l’argument `Relation` du service de modèle de données de formulaire `getDependent`.

![Set-value-web-service](assets/set-value-web-service1.png)

Exemple de règle Définir la valeur à l’aide du service de modèle de données de formulaire

>[!NOTE]
>
>De plus, vous pouvez utiliser la règle Définir la valeur de pour remplir toutes les valeurs d’un composant de type liste déroulante à partir de la sortie d’un service de modèle de données de formulaire ou d’un service Web. Cependant, assurez-vous que l’argument de sortie que vous choisissez est de type Tableau. Toutes les valeurs renvoyées dans un tableau sont disponibles dans la liste déroulante spécifiée.

### [!UICONTROL Afficher] {#show}

Le type de règle **[!UICONTROL Afficher]** permet de créer une règle pour afficher ou masquer un objet de formulaire selon qu’une condition est remplie ou non. Le type de règle Afficher déclenche également l’action Masquer au cas où la condition ne serait pas remplie ou renverrait `False`.

Une règle standard Afficher est structurée comme suit :

`Show Object A;`

`When:`

`(Condition 1 OR Condition 2 OR Condition 3) is TRUE;`

`Else:`

`Hide Object A;`

### [!UICONTROL Masquer] {#hide}

De la même manière que pour le type de règle Afficher, vous pouvez utiliser le type de règle **[!UICONTROL Masquer]** pour afficher ou masquer un objet de formulaire selon qu’une condition est remplie ou non. Le type de règle Masquer déclenche également l’action Afficher au cas où la condition ne serait pas remplie ou renverrait `False`.

Une règle standard Masquer est structurée comme suit :

`Hide Object A;`

`When:`

`(Condition 1 AND Condition 2 AND Condition 3) is TRUE;`

`Else:`

`Show Object A;`

### [!UICONTROL Activer] {#enable}

Le type de règle **[!UICONTROL Activer]** permet d’activer ou de désactiver un objet de formulaire selon qu’une condition est remplie ou non. Le type de règle Activer déclenche également l’action Désactiver au cas où la condition ne serait pas remplie ou renverrait `False`.

Une règle Activer standard est structurée comme suit :

`Enable Object A;`

`When:`

`(Condition 1 AND Condition 2 AND Condition 3) is TRUE;`

`Else:`

`Disable Object A;`

### [!UICONTROL Désactiver] {#disable}

De la même manière que le type de règle Activer, le type de règle **[!UICONTROL Désactiver]** permet d’activer ou de désactiver un objet de formulaire selon qu’une condition est remplie ou non. Le type de règle Désactiver déclenche également l’action Activer au cas où la condition ne serait pas remplie ou renverrait `False`.

Une règle Désactiver standard est structurée comme suit :

`Disable Object A;`

`When:`

`(Condition 1 OR Condition 2 OR Condition 3) is TRUE;`

`Else:`

`Enable Object A;`

### [!UICONTROL Valider] {#validate}

Le type de règle **[!UICONTROL Valider]** valide la valeur d’un champ à l’aide d’une expression. Par exemple, vous pouvez créer une expression pour vérifier que le champ de texte qui indique un nom ne contient pas de caractères spéciaux ni de nombres.

Une règle Valider standard est structurée comme suit :

`Validate Object A;`

`Using:`

`(Expression 1 AND Expression 2 AND Expression 3) is TRUE;`

>[!NOTE]
>
>Si la valeur spécifiée n’est pas conforme à la règle Valider, vous pouvez afficher un message de validation à l’utilisateur ou utilisatrice. Vous pouvez spécifier le message dans le champ **[!UICONTROL Message de validation du script]** dans les propriétés de composant dans la barre latérale.

![Script-validation](assets/script-validation.png)

### [!UICONTROL Définir les options de] {#setoptionsof}

Le type de règle **[!UICONTROL Définir les options de]** permet de définir des règles pour ajouter dynamiquement des cases à cocher au formulaire adaptatif. Vous pouvez utiliser un modèle de données de formulaire (FDM) ou une fonction personnalisée pour définir la règle.

Pour définir une règle basée sur une fonction personnalisée, sélectionnez **[!UICONTROL Sortie de fonction]** dans la liste déroulante, puis faites glisser et déposez une fonction personnalisée à partir de l’onglet **[!UICONTROL Fonctions]**. Le nombre de cases à cocher définies dans la fonction personnalisée est ajouté au formulaire adaptatif.

![Fonctions personnalisées](assets/custom_functions_set_options_new.png)

Pour créer une fonction personnalisée, voir [Fonctions personnalisées dans l’éditeur de règles](#custom-functions).

Pour définir une règle basée sur un modèle de données de formulaire (FDM) :

1. Sélectionnez **[!UICONTROL Sortie du service]** dans la liste déroulante.
1. Sélectionnez l’objet de modèle de données.
1. Sélectionnez une propriété d’objet de modèle de données dans la liste déroulante **[!UICONTROL Valeur d’affichage]**. Le nombre de cases à cocher dans le formulaire adaptatif est dérivé du nombre d’instances définies pour cette propriété dans la base de données.
1. Sélectionnez une propriété d’objet de modèle de données dans la liste déroulante **[!UICONTROL Enregistrer la valeur]**.

![Options de jeu FDM](assets/fdm_set_options_new.png)

## Présentation de l’interface utilisateur de l’éditeur de règles {#understanding-the-rule-editor-user-interface}

L’éditeur de règles offre une interface utilisateur exhaustive et néanmoins simple, qui permet de créer et de gérer des règles. Vous pouvez lancer l’interface utilisateur de l’éditeur de règles à partir d’un formulaire adaptatif en mode Création.

Pour lancer l’interface utilisateur de l’éditeur de règles :

1. Ouvrez un formulaire adaptatif en mode Création.
1. Sélectionnez l’objet de formulaire pour lequel vous voulez créer une règle, puis ![edit-rules](assets/edit-rules-icon.svg) de la barre d’outils Composant. L’interface utilisateur de l’éditeur de règles s’affiche.

   ![create-rules](assets/create-rules1.png)

   Toutes les règles existantes pour les objets de formulaire sélectionnés sont répertoriées dans cet écran. Pour plus d’informations sur la gestion des règles existantes, voir [Gestion des règles](rule-editor.md#p-manage-rules-p).

1. Sélectionnez **[!UICONTROL Créer]** pour créer une règle. L’éditeur visuel de l’interface utilisateur de l’éditeur de règles s’affiche par défaut la première fois que vous lancez l’éditeur de règles.

   ![Interface utilisateur de l’éditeur de règles](assets/rule-editor-ui1.png)

Examinons en détail chaque composant de l’interface utilisateur de l’éditeur de règles.

### A. Affichage composant-règle {#a-component-rule-display}

Affiche le titre de l’objet de formulaire adaptatif à partir duquel vous avez lancé l’éditeur de règles et le type de règle actuellement sélectionné. Dans l’exemple ci-dessus, l’éditeur de règles est lancé à partir de l’objet de formulaire adaptatif « Salary » et le type de règle sélectionné est Lorsque.

### B. Objets de formulaire et fonctions {#b-form-objects-and-functions-br}

Le volet situé à gauche de l’interface utilisateur de l’éditeur de règles comporte deux onglets: **[!UICONTROL Objets de formulaire]** et **[!UICONTROL Fonctions]**.

L’onglet Objets de formulaire affiche une arborescence de tous les objets contenus dans le formulaire adaptatif. Il affiche le titre et le type des objets. Lors de la création d’une règle, vous pouvez faire glisser-déposer les objets de formulaire dans l’éditeur de règles. Lorsque vous créez ou modifiez une règle en faisant glisser et en déposant un objet ou une fonction dans un espace réservé, cet espace prend automatiquement le type de valeur approprié.

Les objets de formulaire contenant une ou plusieurs règles valides appliquées sont désignés par un point vert. Si l’une des règles appliquées à un objet de formulaire n’est pas valide, l’objet de formulaire est désigné par un point jaune.

L’onglet Fonctions comporte un jeu de fonctions intégrées, comme Somme de, Minimum de, Maximum de, Moyenne de, Nombre de et Valider le formulaire. Vous pouvez utiliser ces fonctions pour calculer des valeurs dans les panneaux et les lignes de tableau répétables et pour les instructions d’action et de condition lors de la création de règles. Cependant, vous pouvez créer des [fonctions personnalisées](#custom-functions).

![L’onglet Fonctions](assets/functions1.png)

>[!NOTE]
>
>Vous pouvez effectuer une recherche de texte dans les noms et titres des objets et des fonctions à partir des onglets Objets de formulaire et Fonctions.

Dans l’arborescence de gauche des objets de formulaire, vous pouvez sélectionner les objets de formulaire pour afficher les règles appliquées à chacun des objets. Vous pouvez non seulement parcourir les règles des différents objets de formulaire mais également copier-coller des règles entre les objets du formulaire. Pour plus d’informations, reportez-vous à la section [Règles de copier-coller](rule-editor.md#p-copy-paste-rules-p).

### C. Basculement entre les objets de formulaire et les fonctions {#c-form-objects-and-functions-toggle-br}

Le bouton Basculer, lorsqu’il est sélectionné, permet de basculer entre le volet des objets de formulaire et celui des fonctions.

### D. Éditeur de règles visuel {#visual-rule-editor}

Lorsque l’interface utilisateur de l’éditeur de règles est en mode éditeur visuel, l’éditeur de règles visuel est la zone dans laquelle vous créez des règles. Il vous permet de sélectionner un type de règle et de définir en conséquence des conditions et des actions. Lors de la définition des conditions et des actions dans une règle, vous pouvez glisser-déposer des objets de formulaire et des fonctions depuis le volet Objets de formulaire et Fonctions.

Pour plus d’informations sur l’utilisation de l’éditeur de règles visuel, voir [Création de règles](rule-editor.md#p-write-rules-p).
<!-- 
### E. Visual-code editors switcher {#e-visual-code-editors-switcher}

Users in the forms-power-users group can access code editor. For other users, code editor is not available. If you have the rights, you can switch from visual editor mode to code editor mode of the rule editor, and conversely, using the switcher right above the rule editor. When you launch rule editor the first time, it opens in the visual editor mode. You can write rules in the visual editor mode or switch to the code editor mode to write a rule script. However, note that if you modify a rule or write a rule in code editor, you cannot switch back to the visual editor for that rule unless you clear the code editor.

[!DNL Experience Manager Forms] tracks the rule editor mode you used last to write a rule. When you launch the rule editor next time, it opens in that mode. However, you can also configure a default mode to open the rule editor in the specified mode. To do so:

1. Go to [!DNL Experience Manager] web console at `https://[host]:[port]/system/console/configMgr`.
1. Click to edit **[!UICONTROL Adaptive Form Configuration Service]**.
1. choose **[!UICONTROL Visual Editor]** or **[!UICONTROL Code Editor]** from the **[!UICONTROL Default Mode for Rule Editor]** drop-down

1. Click **[!UICONTROL Save]**.
-->

### E. Boutons Terminé et Annuler {#done-and-cancel-buttons}

Le bouton **[!UICONTROL Terminé]** permet d’enregistrer une règle. Vous pouvez enregistrer une règle incomplète. Toutefois, les règles incomplètes ne sont pas valides et ne s’exécutent pas. Les règles enregistrées sur un objet de formulaire sont répertoriées lorsque vous lancez l’éditeur de règles la prochaine fois à partir du même objet de formulaire. Vous pouvez gérer des règles existantes dans cette vue. Pour plus d’informations, consultez la section [Gérer les règles](rule-editor.md#p-manage-rules-p).

Le bouton **[!UICONTROL Annuler]** annule tous les changements apportés à une règle et ferme l’éditeur de règles.

## Règles d’écriture {#write-rules}

Vous pouvez créer des règles à l’aide de l’éditeur de règles visuel &lt;!-- ou l’éditeur de code>. Lorsque vous lancez l’éditeur de règles pour la première fois, il s’ouvre en mode d’éditeur visuel. Vous pouvez passer au mode d’éditeur de code et créer des règles. Cependant, si vous créez ou modifiez une règle dans l’éditeur de code, vous ne pouvez pas basculer vers l’éditeur visuel pour cette règle sauf si vous avez désélectionné l’éditeur de code. Lorsque vous lancez l’éditeur de règles la fois suivante, il s’ouvre dans le mode que vous avez utilisé en dernier pour créer une règle.

Tout d&#39;abord, examinons l’écriture de règles utilisant l’éditeur visuel.

### À l’aide de l’éditeur visuel {#using-visual-editor}

Examinons comment créer une règle dans l’éditeur visuel en utilisant l’exemple de formulaire suivant.

![Create-rule-example](assets/create-rule-example.png)

La section Conditions de prêt dans l’exemple de formulaire de demande de prêt requiert des demandeurs et demandeuses de spécifier leur état civil, leur salaire et, si ils ou elles sont marié(e)s, le salaire de leur conjoint(e). D’après les entrées de l’utilisateur ou utilisatrice, la règle permet de calculer le montant d’éligibilité du prêt et l’affiche dans le champ Éligibilité de prêt. Appliquez les règles suivantes pour mettre en œuvre le scénario :

* Le champ Salaire de l’époux ou de l’épouse s’affiche uniquement lorsque la valeur État civil est Marié ou Mariée.
* Le montant d’éligibilité de prêt représente 50 % du salaire total.

Pour créer des règles :

1. Tout d’abord, créez la règle pour contrôler la visibilité du champ Salaire du conjoint en fonction de l’option de l’utilisateur pour le bouton radio État civil.

   Ouvrez le formulaire de demande de prêt en mode Création. Sélectionnez le composant **[!UICONTROL État civil]** et choisissez ![edit-rules](assets/edit-rules-icon.svg). Ensuite, sélectionnez **[!UICONTROL Créer]** pour lancer l’éditeur de règles.

   ![write-rules-visual-editor-1](assets/write-rules-visual-editor-1.png)

   Lorsque vous lancez l’éditeur de règles, la règle Lorsque est sélectionnée par défaut. En outre, l’objet de formulaire (dans ce cas, État civil) d’où vous avez lancé l’éditeur de règles est spécifié dans l’instruction Lorsque.

   Bien que vous ne puissiez pas changer ou modifier l’objet sélectionné, vous pouvez utiliser la liste déroulante de règles, comme indiqué ci-dessous, pour sélectionner un autre type de règle. Si vous souhaitez créer une règle sur un autre objet, sélectionnez Annuler pour quitter l’éditeur de règles et relancez-le depuis l’objet de formulaire de votre choix.

1. Sélectionnez le menu déroulant **[!UICONTROL Sélectionner l’état]** et choisissez **[!UICONTROL est égal à]**. Le champ **[!UICONTROL Saisissez une chaîne]** s’affiche.

   ![write-rules-visual-editor-2](assets/write-rules-visual-editor-2.png)

   Pour le bouton radio État civil, les options **[!UICONTROL Marié(e)]** et **[!UICONTROL Célibataire]** sont définies respectivement sur les valeurs **0** et **1**. Vous pouvez vérifier les valeurs affectées sur l’onglet Titre de la boîte de dialogue Modifier le bouton radio, comme indiqué ci-dessous.

   ![Valeurs de bouton radio dans l’éditeur de règles](assets/radio-button-values.png)

1. Dans le champ **[!UICONTROL Saisissez une chaîne]** dans la règle, indiquez **0**.

   ![write-rules-visual-editor-4](assets/write-rules-visual-editor-4.png)

   Vous avez défini la condition comme `When Marital Status is equal to Married`. Définissez ensuite l’action à effectuer si cette condition est True.

1. Dans l’instruction Alors, sélectionnez **[!UICONTROL Afficher]** dans le menu déroulant **[!UICONTROL Sélectionner une action]**.

   ![write-rules-visual-editor-5](assets/write-rules-visual-editor-5.png)

1. Faites glisser et déposez le champ **[!UICONTROL Salaire du conjoint ou de la conjointe]** de l’onglet Objets de formulaire vers le champ **[!UICONTROL Déposez l’objet ou sélectionnez ici]**. Vous pouvez également sélectionner le champ **[!UICONTROL Déposer l’objet ou sélectionner ici]**, puis le champ **[!UICONTROL Salaire du conjoint ou de la conjointe]** dans le menu contextuel, qui répertorie tous les objets de formulaire dans le formulaire.

   ![write-rules-visual-editor-6](assets/write-rules-visual-editor-6.png)

   La règle s’affiche comme suit dans l’éditeur de règles.

   ![write-rules-visual-editor-7](assets/write-rules-visual-editor-7.png)

1. Cliquez sur **[!UICONTROL Terminé]** pour enregistrer la règle.

1. Répétez les étapes 1 à 5 pour définir une autre règle pour masquer le champ de salaire du conjoint ou de la conjointe si la valeur de l’état civil est Célibataire. La règle s’affiche comme suit dans l’éditeur de règles.

   ![write-rules-visual-editor-8](assets/write-rules-visual-editor-8.png)

   >[!NOTE]
   >
   >Vous pouvez également créer une règle Afficher dans le champ Salaire du conjoint, au lieu de deux règles Lorsque dans le champ État civil pour mettre en œuvre le même comportement.

   ![write-rules-visual-editor-9](assets/write-rules-visual-editor-9.png)

1. Ensuite, créez une règle pour calculer le niveau d’éligibilité de prêt, à hauteur de 50 % du salaire total, puis affichez-la dans le champ Éligibilité de prêt. À cet effet, créez des règles **[!UICONTROL Définir la valeur de]** sur le champ Éligibilité de prêt.

   En mode Création, sélectionnez le champ **[!UICONTROL Éligibilité de prêt]**, puis ![edit-rules](assets/edit-rules-icon.svg). Ensuite, sélectionnez **[!UICONTROL Créer]** pour lancer l’éditeur de règles.

1. Sélectionnez la règle **[!UICONTROL Définir la valeur de]** dans la liste déroulante des règles.

   ![write-rules-visual-editor-10](assets/write-rules-visual-editor-10.png)

1. Choisissez **[!UICONTROL Sélectionner l’option]** et sélectionnez **[!UICONTROL Expression mathématique]**. Un champ permettant de saisir l’expression mathématique s’ouvre.

   ![write-rules-visual-editor-11](assets/write-rules-visual-editor-11.png)

1. Dans le champ d&#39;expression :

   * Sélectionnez ou faites glisser et déposez le champ **[!UICONTROL Salaire]**, de l’onglet Objet de formulaire vers le premier champ **[!UICONTROL Déposez l’objet ou sélectionnez ici]**.

   * Sélectionnez **[!UICONTROL Plus]** dans le champ **[!UICONTROL Sélectionner un opérateur]**.

   * Sélectionnez ou faites glisser et déposez depuis le champ **[!UICONTROL Salaire du conjoint]** de l’onglet Objets de formulaire vers l’autre champ **[!UICONTROL Déposez l’objet ou sélectionnez ici]**.

   ![write-rules-visual-editor-12](assets/write-rules-visual-editor-12.png)

1. Ensuite, sélectionnez la zone en surbrillance autour du champ Expression et choisissez **[!UICONTROL Étendre l’expression]**.

   ![write-rules-visual-editor-13](assets/write-rules-visual-editor-13.png)

   Dans le champ d’expression étendue, sélectionnez **[!UICONTROL divisé par]** dans le champ **[!UICONTROL Sélectionner un opérateur]** et **[!UICONTROL Nombre]** dans le champ **[!UICONTROL Sélectionner une option]**. Ensuite, spécifiez **[!UICONTROL 2]** dans le champ Nombre.

   ![write-rules-visual-editor-14](assets/write-rules-visual-editor-14.png)

   >[!NOTE]
   >
   >Vous pouvez créer des expressions complexes à l’aide de composants, fonctions, expressions mathématiques et valeurs de propriété dans le champ Sélectionner une option.

   Créez ensuite une condition qui, lorsqu’elle renvoie True, permet que l’expression s’exécute.

1. Sélectionnez **[!UICONTROL Ajouter une condition]** pour ajouter une instruction Lorsque.

   ![write-rules-visual-editor-15](assets/write-rules-visual-editor-15.png)

   Dans l’instruction Lorsque :

   * Sélectionnez ou glissez-déposez depuis l’onglet Objets de formulaire le champ **[!UICONTROL État civil]** dans le premier champ **[!UICONTROL Déposez l’objet ou sélectionnez ici]**.

   * Sélectionnez **[!UICONTROL est égal à]** dans le champ **[!UICONTROL Sélectionner un opérateur]**.

   * Sélectionnez Chaîne dans l’autre champ **[!UICONTROL Déposez l’objet ou sélectionnez ici]** et spécifiez **[!UICONTROL Marié(e)]** dans le champ **[!UICONTROL Saisissez la chaîne]**.

   Enfin, la règle s’affiche comme suit dans l’éditeur de règles. ![write-rules-visual-editor-16](assets/write-rules-visual-editor-16.png)

1. Sélectionnez **[!UICONTROL Terminé]**. La règle est enregistrée.

1. Répétez les étapes 7 à 14 pour définir une autre règle pour calculer le montant d’éligibilité si la valeur d’état civil est Célibataire. La règle s’affiche comme suit dans l’éditeur de règles.

   ![write-rules-visual-editor-17](assets/write-rules-visual-editor-17.png)

>[!NOTE]
>
>Vous pouvez également utiliser la règle Définir la valeur de pour calculer l’éligibilité de prêt dans la règle Lorsque que vous avez créée pour afficher ou masquer le champ Salaire du conjoint. La règle combinée résultante, lorsque l’état civil est Célibataire, s’affiche comme suit dans l’éditeur de règles.
>
>De même, vous pouvez entrer une règle combinée pour contrôler la visibilité du champ Salaire de l’époux ou de l’épouse lorsque la valeur d&#39;état civil est Marié ou Mariée.

![write-rules-visual-editor-18](assets/write-rules-visual-editor-18.png)

<!-- ### Using code editor {#using-code-editor}

Users added to the forms-power-users group can use code editor. The rule editor auto generates the JavaScript code for any rule you create using visual editor. You can switch from visual editor to the code editor to view the generated code. However, if you modify the rule code in the code editor, you cannot switch back to the visual editor. If you prefer writing rules in code editor rather than visual editor, you can write rules afresh in the code editor. The visual-code editors switcher helps you switch between the two modes.

The code editor JavaScript is the expression language of Adaptive Forms. All the expressions are valid JavaScript expressions and use Adaptive Forms scripting model APIs. These expressions return values of certain types. For the complete list of Adaptive Forms classes, events, objects, and public APIs, see [JavaScript Library API reference for Adaptive Forms](https://helpx.adobe.com/experience-manager/6-5/forms/javascript-api/index.html).

For more information about guidelines to write rules in the code editor, see [Adaptive Form Expressions](adaptive-form-expressions.md).

While writing JavaScript code in the rule editor, the following visual cues help you with the structure and syntax:

* Syntax highlights

* Auto Indentation

* Hints and suggestions for Form objects, functions, and their properties

* Auto completion of form component names and common JavaScript functions

![javascriptruleeditor](assets/javascriptruleeditor.png)
-->

#### Fonctions personnalisées dans l’éditeur de règles {#custom-functions}

Outre les fonctionnalités prêtes à l’emploi, comme *Somme de*, qui sont répertoriées sous Fonctions, vous pouvez créer des fonctions personnalisées dont vous avez besoin fréquemment. Assurez-vous de la présence de la balise `jsdoc` au-dessus de la fonction que vous créez.

La balise `jsdoc` associée est nécessaire :

* Si vous souhaitez personnaliser la configuration et la description
* Parce qu’il y a plusieurs façons de déclarer une fonction dans`JavaScript,` et que les commentaires permettent de conserver une trace des fonctions.

L’éditeur de règles prend en charge la syntaxe JavaScript ES5 pour les scripts et les fonctions personnalisées.
Pour plus d’informations, consultez [jsdoc.app](https://jsdoc.app/).

Balises `jsdoc` prises en charge :

* Syntaxe
**Privé** : `@private`
Une fonction privée n’est pas incluse comme fonction personnalisée.

* Syntaxe
**Nom** : `@name funcName <Function Name>`
Autrement,`,` vous pouvez utiliser : `@function funcName <Function Name>` **ou** `@func` `funcName <Function Name>`.
  `funcName` est le nom de la fonction (les espaces ne sont pas autorisés).
  `<Function Name>` est le nom d’affichage de la fonction.

* Syntaxe
**Membre** : `@memberof namespace`
Associe un espace de noms à la fonction.

* Syntaxe
**Paramètre** : `@param {type} name <Parameter Description>`
Autrement, vous pouvez utiliser : `@argument` `{type} name <Parameter Description>` **ou** `@arg` `{type}` `name <Parameter Description>`.
Affiche les paramètres utilisés par la fonction. Une fonction peut comporter plusieurs balises de paramètre, une balise pour chaque paramètre dans l’ordre d’occurrence.
  `{type}` représente le type de paramètre. Les types de paramètre sont les suivants :

   1. chaîne
   1. nombre
   1. booléen
   1. portée

  La portée fait référence aux champs d’un formulaire adaptatif. Lorsqu’un formulaire utilise le chargement différé, vous pouvez utiliser `scope` pour accéder à ses champs. Vous pouvez accéder aux champs lorsque les champs sont chargés ou si les champs sont marqués comme généraux.

  Tous les types de paramètre sont classés dans l’une des catégories ci-dessus. Ils sont tous pris en charge. Assurez-vous que vous sélectionnez l’un des types ci-dessus. Les types ne sont pas sensibles à la casse. Les espaces ne sont pas autorisés dans le paramètre `name`. `<Parameter Descrption>` `<parameter>  can have multiple words. </parameter>`

* Syntaxe
**Type de retour** : `@return {type}`
Autrement, vous pouvez utiliser `@returns {type}`.
Ajoute des informations sur la fonction, comme son objectif.
{type} représente le type de valeur renvoyée de la fonction. Les types de valeur renvoyée autorisés sont les suivants :

   1. chaîne
   1. nombre
   1. booléen

  Tous les autres types de retour sont classés en dessous de l’un des précédents. Ils sont tous pris en charge. Assurez-vous que vous sélectionnez l’un des types ci-dessus. Les types de valeur renvoyée ne sont pas sensibles à la casse.

   * **Cette**
syntaxe : `@this currentComponent`

  Utilisez @this pour faire référence au composant Formulaire adaptatif à partir duquel la règle a été créée.

  L’exemple ci-dessous repose sur la valeur du champ. Dans l’exemple ci-dessous, la règle masque un champ dans le formulaire. La partie `this` de `this.value` fait référence au composant Formulaire adaptatif sous-jacent, à partir duquel la règle a été créée.

  ```
     /**
     * @function myTestFunction
     * @this currentComponent
     * @param {scope} scope in which code inside function is run.
     */
     myTestFunction = function (scope) {
        if(this.value == "O"){
              scope.age.visible = true;
        } else {
           scope.age.visible = false;
        }
     }
  ```

  >[!NOTE]
  >
  >Les commentaires avant la fonction personnalisée sont utilisés pour le résumé. Le résumé peut s’étendre sur plusieurs lignes jusqu’à ce qu’une balise soit rencontrée. Limitez la taille à une seule pour une description concise dans le créateur de règles.

**Ajout d’une fonction personnalisée**

Par exemple, vous souhaitez ajouter une fonction personnalisée qui calcule la surface d’un carré. La longueur du côté est la saisie de l’utilisateur ou de l’utilisatrice dans la fonction personnalisée, qui est acceptée à l’aide d’une zone numérique dans votre formulaire. La sortie calculée s’affiche dans une autre zone numérique dans votre formulaire. Pour ajouter une fonction personnalisée, vous devez d’abord créer une bibliothèque cliente, puis l’ajouter au référentiel CRX.

Pour créer une bibliothèque cliente et l’ajouter dans le référentiel CRX :

1. Créez une bibliothèque cliente. Pour plus d’informations, voir [Utilisation des bibliothèques côté client](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html?lang=fr#developing).
1. Dans CRXDE, ajoutez une propriété `categories`catégories possédant une valeur de type chaîne telle que `customfunction` au dossier `clientlib`.

   >[!NOTE]
   >
   >`customfunction`est un exemple de catégorie. Vous pouvez choisir n’importe quel nom pour la catégorie que vous créez dans le dossier `clientlib`.

Une fois que vous avez ajouté votre bibliothèque client dans le référentiel CRX, utilisez-la dans votre formulaire adaptatif. Cela vous permet d’utiliser votre fonction personnalisée comme règle dans votre formulaire. Pour ajouter la bibliothèque cliente dans votre formulaire adaptatif :

1. Ouvrez votre formulaire en mode d’édition.
Pour ouvrir un formulaire en mode d’édition, sélectionnez-le et cliquez sur **[!UICONTROL Ouvrir]**.
1. En mode d’édition, sélectionnez un composant, puis choisissez ![field-level](assets/select_parent_icon.svg) > **[!UICONTROL Conteneur de formulaires adaptatifs]**, et ![cmppr](assets/configure-icon.svg).
1. Dans la barre latérale, sous Nom de bibliothèque cliente, ajoutez votre bibliothèque cliente. (`customfunction` dans l’exemple).

   ![Ajout de la bibliothèque cliente de fonction personnalisée](assets/clientlib.png)

1. Sélectionnez la zone numérique d’entrée, et choisissez ![edit-rules](assets/edit-rules-icon.svg) pour ouvrir l’éditeur de règles.
1. Sélectionnez **[!UICONTROL Créer une règle]**. À l’aide des options indiquées ci-dessous, créez une règle pour enregistrer la valeur au carré de l’entrée dans le champ Sortie de votre formulaire.

   [![Utilisation des fonctions personnalisées pour créer une règle](assets/add_custom_rule_new.png)](assets/add-custom-rule.png)

1. Sélectionnez **[!UICONTROL Terminé]**. Votre fonction personnalisée est ajoutée.

   >[!NOTE]
   >
   > Pour appeler un modèle de données de formulaire (FDM) à partir de l’éditeur de règles à l’aide de fonctions personnalisées, [voir ici](/help/forms/using-form-data-model.md#invoke-services-in-adaptive-forms-using-rules-invoke-services).

#### Types pris en charge pour la déclaration de fonction {#function-declaration-supported-types}

**Instruction de fonction**

```javascript
function area(len) {
    return len*len;
}
```

Cette fonction est incluse sans commentaires `jsdoc`.

**Expression de fonction**

```javascript
var area;
//Some codes later
/** */
area = function(len) {
    return len*len;
};
```

**Expression et instruction de fonction**

```javascript
var b={};
/** */
b.area = function(len) {
    return len*len;
}
```

**Déclaration de fonction en tant que variable**

```javascript
/** */
var x1,
    area = function(len) {
        return len*len;
    },
    x2 =5, x3 =true;
```

Limite : la fonction personnalisée prend uniquement la première déclaration de fonction de la liste des variables, si elles sont ensemble. Vous pouvez utiliser l&#39;expression de fonction pour chaque fonction déclarée.

**Déclaration de fonction en tant qu’objet**

```javascript
var c = {
    b : {
        /** */
        area : function(len) {
            return len*len;
        }
    }
};
```

>[!NOTE]
>
>Assurez-vous que vous utilisez `jsdoc` pour chaque fonction personnalisée. Même si les commentaires `jsdoc` sont recommandés, incluez un commentaire `jsdoc` vide pour marquer votre fonction comme fonction personnalisée. Cela permet la manipulation par défaut de votre fonction personnalisée.

## Gestion des règles {#manage-rules}

Les règles existantes sur un objet de formulaire sont répertoriées lorsque vous sélectionnez l’objet et ![edit-rules1](assets/edit-rules-icon.svg). Vous pouvez afficher le titre et un aperçu du résumé de la règle. En outre, l’interface utilisateur vous permet de développer et d’afficher le résumé complet d’une règle, de changer l’ordre des règles, de les modifier et de les supprimer.

![Liste-rules](assets/list-rules.png)

Vous pouvez effectuer les actions suivantes sur les règles :

* **Développer/Réduire** : la colonne Contenu dans la liste des règles affiche le contenu des règles. Si le contenu entier des règles n’est pas visible dans l’affichage par défaut, sélectionnez ![expand-rule-content](assets/Smock_ChevronDown.svg) pour le développer.

* **Réorganiser** : toute nouvelle règle que vous créez est empilée au bas de la liste des règles. Les règles sont exécutées de haut en bas. La règle en haut s’exécute en premier, suivie des autres règles du même type. Par exemple, si vous avez les règles Lorsque, Afficher, Activer et Lorsque en première, deuxième, troisième et quatrième positions depuis le haut respectivement, la règle Lorsque du haut est exécutée en premier, suivie de la règle Lorsque à la quatrième position. Ensuite, les règles Afficher et Activer seront exécutées.
Vous pouvez modifier l’ordre d’une règle en appuyant sur ![sort-rules](assets/sort-rules.svg) en regard ou la faire glisser et la déposer dans l’ordre souhaité dans la liste.

* **Modifier** : pour modifier une règle, cochez la case située en regard du titre de la règle. Les options de modification et de suppression de la règle s’affichent. Sélectionnez **[!UICONTROL Modifier]** pour afficher la règle sélectionnée dans l’éditeur de règles <!-- in visual  or code editor mode depending on the mode used to create the rule -->.

* **Supprimer** : pour supprimer une règle, sélectionnez-la puis choisissez **[!UICONTROL Supprimer]**.

* **Activer/désactiver** : lorsque vous devez suspendre temporairement l’utilisation d’une règle, vous pouvez sélectionner une ou plusieurs règles et appuyer sur **[!UICONTROL Désactiver]** dans la barre d’outils Actions pour les désactiver. Si une règle est désactivée, elle ne s’exécute pas lors de l’exécution. Pour activer une règle désactivée, vous pouvez la sélectionner puis choisir Activer dans la barre d’outils Actions. La colonne de statut de la règle indique si la règle est activée ou désactivée.

![Désactiver la règle](assets/disablerule.png)

## Règles de copier-coller {#copy-paste-rules}

Vous pouvez copier-coller une règle d’un champ à d’autres champs similaires pour gagner du temps.

Pour copier-coller des règles, procédez comme suit :

1. Sélectionnez l’objet de formulaire à partir duquel vous souhaitez copier une règle puis, dans la barre d’outils des composants, sélectionnez ![edit-rules](assets/edit-rules-icon.svg). L’interface utilisateur de l’éditeur de règles s’affiche avec l’objet de formulaire sélectionné, et les règles existantes s’affichent.

   ![copy rule](assets/copyrule.png)

   Pour plus d’informations sur la gestion des règles existantes, voir [Gestion des règles](rule-editor.md#p-manage-rules-p).

1. Cochez la case en regard du titre de la règle pour afficher les options de gestion de la règle. Sélectionnez **[!UICONTROL Copie]**.

   ![copyrule2](assets/copyrule2.png)

1. Sélectionnez un autre objet de formulaire dans lequel vous souhaitez coller la règle et choisissez **[!UICONTROL Coller]**. De plus, vous pouvez modifier la règle pour y apporter des modifications.

   >[!NOTE]
   >
   >Vous pouvez coller une règle dans un autre objet de formulaire uniquement si cet objet de formulaire prend en charge les événement de la règle copiée. Par exemple, un bouton prend en charge l’événement Cliquer. Vous pouvez coller une règle avec un événement Cliquer sur un bouton mais pas dans une case à cocher.

1. Sélectionnez **[!UICONTROL Terminé]** pour enregistrer la règle.

## Expressions imbriquées {#nestedexpressions}

L’éditeur de règles vous permet d’utiliser plusieurs opérateurs ET et OU afin de créer des règles imbriquées. Vous pouvez fusionner plusieurs opérateurs ET et OU dans les règles.

Voici un exemple de règle imbriquée qui affiche un message concernant l’éligibilité pour un droit de garde lorsque les conditions nécessaires sont remplies à l’intention de l’utilisateur.

![Expression complexe](assets/complexexpression.png)

Vous pouvez également faire glisser et déposer des conditions dans une règle pour la modifier. Appuyez et passez le curseur sur la poignée (![handle](assets/drag-handle.svg)) avant une condition. Une fois le pointeur affiché sous forme de main comme illustré ci-dessous, faites glisser la condition et déposez-la n’importe où dans la règle. La structure de la règle change.

![Glisser-déposer](assets/drag-and-drop.png)

## Conditions d’expression de date {#dateexpression}

L’éditeur de règles vous permet d’utiliser des comparaisons de dates afin de créer des conditions.

Voici un exemple de condition qui contient un objet de texte statique si le prêt hypothécaire sur la maison est déjà utilisé, ce que l’utilisateur ou l’utilisatrice indique en remplissant le champ de date.

Lorsque la date du prêt hypothécaire de la propriété indiquée par l’utilisateur est déjà dépassée, le formulaire adaptatif affiche une remarque concernant le calcul des revenus. La règle ci-dessous compare la date indiquée par l’utilisateur à la date actuelle et si la date indiquée par l’utilisateur est antérieure à la date actuelle, le formulaire affiche le message texte (appelé « Revenu »).

![Condition d’expression de date](assets/dateexpressioncondition.png)

Lorsque la date remplie est antérieure à la date actuelle, le formulaire affiche le message texte (Revenu), comme suit :

![Condition d’expression de date remplie](assets/dateexpressionconditionmet.png)

## Conditions de comparaison des nombres {#number-comparison-conditions}

L’éditeur de règles vous permet de créer des conditions qui comparent deux nombres.

Voici un exemple de condition, qui contient un objet de texte statique si le demandeur habite à l’adresse actuelle depuis moins de 36 mois.

![Condition de comparaison des nombres](assets/numbercomparisoncondition.png)

Lorsque l’utilisateur indique qu’il habite à l’adresse résidentielle actuelle depuis moins de 36 mois, le formulaire affiche une notification indiquant qu’un justificatif de domicile supplémentaire peut être demandé.

![Plus de justificatif demandé](assets/additionalproofrequested.png)

<!-- ## Impact of rule editor on existing scripts {#impact-of-rule-editor-on-existing-scripts}

In [!DNL Experience Manager Forms] versions prior to [!DNL Experience Manager 6.1 Forms] feature pack 1, form authors and developers used to write expressions in the Scripts tab of the Edit component dialog to add dynamic behavior to Adaptive Forms. The Scripts tab is now replaced by the rule editor.

Any scripts or expressions that you must have written in the Scripts tab are available in the rule editor. While you cannot view or edit them in visual editor, if you are a part of the forms-power-users group you can edit scripts in code editor. -->

## Exemples de règles {#example}

### Appeler service de modèle de données de formulaire {#invoke}

Imaginons un service web `GetInterestRates` prenant le montant du prêt, la durée et la cote de solvabilité du demandeur ou de la demandeuse comme valeurs d’entrée et renvoyant un plan de prêt incluant le montant des mensualités et le taux d’intérêt. Vous créez un modèle de données de formulaire à l’aide du service web comme source de données. Vous ajoutez des objets de modèle de données et un service `get` au modèle de formulaire. Le service s’affiche sur l’onglet Services du modèle de données de formulaire. Ensuite, créez un formulaire adaptatif incluant des champs des objets de modèle de données pour capturer les données saisies par l’utilisateur pour le montant et la durée du prêt et la cote de solvabilité. Ajoutez un bouton qui demande au service Web d’extraire les détails du plan. La sortie est renseignée dans les champs appropriés.

La règle ci-dessous indique comment configurer l’action Appel du service pour accomplir l’exemple de scénario.

![Exemple-invoke-services](assets/example-invoke-services.png)

>[!NOTE]
>
>Si l’entrée est de type tableau, les champs qui prennent en charge les tableaux sont visibles dans la section déroulante Sortie.

### Déclenchement de plusieurs actions à l’aide de la règle Lorsque {#triggering-multiple-actions-using-the-when-rule}

Dans un formulaire de demande de prêt, vous voulez savoir si la personne demandant le prêt est un client ou une cliente existante ou non. En fonction des informations fournies par l’utilisateur ou l’utilisatrice, le champ ID du client ou de la cliente doit s’afficher ou se masquer. En outre, vous souhaitez placer le focus sur le champ d’ID de client ou cliente si l’utilisateur ou l’utilisatrice est un client ou une cliente existant. Le formulaire de demande de prêt est composé des éléments suivants :

* Un bouton radio,**[!UICONTROL Êtes-vous déjà client(e) chez Geometrixx ?]**, qui propose les options [!UICONTROL Oui] et [!UICONTROL Non]. La valeur Oui est **0** ; la valeur Non est **1**.

* Un champ de texte, **[!UICONTROL ID de client Geometrixx]**, pour indiquer l’ID du client/de la cliente.

Lorsque vous entrez une règle Lorsque sur le bouton radio pour implémenter ce comportement, la règle s’affiche comme suit dans l’éditeur de règles visuel.

![When-rule-example](assets/when-rule-example.png)

Règle dans l’éditeur visuel

Dans l’exemple de règle, l’instruction suivante dans la section Lorsque est la condition qui, si elle renvoie True, exécute les actions spécifiées dans la section Alors.

<!-- The rule appears as follows in the code editor.

![when-rule-example-code](assets/when-rule-example-code.png) 

Rule in the code editor -->

### Utilisation d’une sortie de fonction dans une règle {#using-a-function-output-in-a-rule}

Dans un formulaire de bon de commande, le tableau ci-dessous permet aux utilisateurs de saisir leurs commandes. Dans le tableau ci-dessous :

* La première ligne est répétable, de sorte que les utilisateurs et utilisatrices puissent commander plusieurs produits et spécifier différentes quantités. Son nom d’élément est `Row1`.
* Le titre de la cellule dans la colonne Quantité de produit de la ligne répétable est Quantité. Le nom de l’élément pour cette cellule est `productquantity`.
* La deuxième ligne du tableau est non répétable, et le titre de la cellule dans la colonne Quantité de produit sur cette ligne est Quantité totale.

![Example-function-table](assets/example-function-table.png)

**A.** Ligne 1 **B.** Quantité **C.** Quantité totale

Maintenant, vous souhaitez ajouter des quantités spécifiées dans la colonne Quantité de produit pour tous les produits et afficher la somme dans la cellule Quantité totale. Vous pouvez obtenir ce résultat en saisissant une règle Définir la valeur de dans la cellule Quantité totale, comme indiqué ci-dessous.

![Example-function-output](assets/example-function-output.png)

Règle dans l’éditeur visuel

<!-- he rule appears as follows in the code editor.

![example-function-output-code](assets/example-function-output-code.png)

Rule in the code editor -->

### Validation d’une valeur de champ à l’aide d’une expression {#validating-a-field-value-using-expression}

Dans le formulaire de bon de commande décrit dans l’exemple précédent, vous souhaitez empêcher l’utilisateur de commander plus d’une quantité d’un produit dont le prix est supérieur à 10 000. À cet effet, vous pouvez créer une règle Valider, comme indiqué ci-dessous.

![Example-validate](assets/example-validate.png)

Règle dans l’éditeur visuel

<!-- The rule appears as follows in the code editor.

![example-validate-code](assets/example-validate-code.png)

Rule in the code editor -->