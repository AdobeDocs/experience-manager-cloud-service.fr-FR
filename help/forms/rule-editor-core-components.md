---
title: Comment utiliser l’éditeur de règles pour ajouter des règles à des champs de formulaire afin d’ajouter un comportement dynamique et de créer une logique complexe à un formulaire adaptatif basé sur des composants principaux ?
description: L’éditeur de règles de Forms adaptatif vous permet d’ajouter un comportement dynamique et de créer une logique complexe dans des formulaires sans codage ni script.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
badgeSaas: label="AEM Forms" type="Positive" tooltip="S’applique à AEM Forms)."
exl-id: 1292f729-c6eb-4e1b-b84c-c66c89dc53ae
source-git-commit: 89b0f2a8ca9d2f60365a5c3962b0b4e826f79b3e
workflow-type: tm+mt
source-wordcount: '1180'
ht-degree: 64%

---


# Présentation de l’éditeur de règles pour le formulaire adaptatif basé sur les composants principaux

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM as a Cloud Service (Composants principaux) | Cet article |
| AEM as a Cloud Service (Composants de base) | [Cliquer ici](/help/forms/rule-editor.md) |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html) |

Dans un formulaire adaptatif basé sur les composants principaux, la fonctionnalité d’éditeur de règles permet aux utilisateurs professionnels et aux développeurs de créer des règles pour les objets de formulaire adaptatif. Ces règles déterminent les actions à déclencher sur des objets de formulaire en fonction des conditions prédéfinies, des entrées de l’utilisateur et des actions de l’utilisateur sur le formulaire. Cette fonctionnalité permet de rationaliser davantage l’expérience de remplissage de formulaire, en garantissant précision et vitesse.

L’éditeur de règles fournit une interface utilisateur intuitive et simplifiée permettant de créer des règles. Il propose un éditeur visuel qui s’adresse à tous les utilisateurs et utilisatrices, ce qui leur permet de créer et de gérer des règles sans avoir besoin de connaissances techniques approfondies. Cette approche visuelle permet aux utilisateurs et utilisatrices de comprendre et d’implémenter plus facilement la logique souhaitée dans leurs formulaires.

Voici quelques-unes des actions clés que vous pouvez effectuer sur des objets de formulaire adaptatif utilisant des règles :

* Afficher ou masquer un objet
* Activer ou désactiver un objet
* Définir une valeur pour un objet
* Valider la valeur d’un objet
* Exécuter les fonctions de calcul de la valeur d’un objet
* appeler un service de modèle de données de formulaire (FDM) et exécuter une opération ;
* définir la propriété d’un objet ;

<!-- Rule editor replaces the scripting capabilities in [!DNL Experience Manager 6.1 Forms] and earlier releases. However, your existing scripts are preserved in the new rule editor. For more information about working with existing scripts in the rule editor, see [Impact of rule editor on existing scripts](rule-editor.md#p-impact-of-rule-editor-on-existing-scripts-p). -->

Les utilisateurs ajoutés au groupe `forms-power-users` peuvent créer des scripts et modifier des scripts existants. Les utilisateurs appartenant au groupe [!DNL forms-users] peuvent utiliser les scripts, mais ne peuvent ni en créer ni en modifier.

Reportez-vous à l’article [&#x200B; Différence entre l’éditeur de règles de base et l’éditeur de règles des composants principaux &#x200B;](/help/forms/rule-editor-core-components-difference-tables.md) pour une comparaison détaillée.

<!--
## Difference between Rule editor in Core Components and Rule Editor in Foundation Components

{{rule-editor-diff}}

>[!NOTE]
>
> To see how to create and use custom functions in detail, refer to [Custom functions in Adaptive Forms (Core Components)](/help/forms/create-and-use-custom-functions.md) article.

-->

## Présentation d’une règle {#understanding-a-rule}

Une règle est une combinaison d’actions et de conditions. Dans l’éditeur de règles, les actions incluent des activités telles que masquer, afficher, activer, désactiver ou calculer la valeur d’un objet dans un formulaire. Les conditions sont des expressions booléennes qui sont évaluées en effectuant des vérifications et des opérations sur l’état, la valeur ou la propriété d’un objet de formulaire. Les actions sont exécutées en fonction de la valeur (`True` ou `False`) renvoyée par l’évaluation d’une condition.

L’éditeur de règles fournit un ensemble de types de règle prédéfinis, tels que Lorsque, Afficher, Masquer, Activer, Désactiver, Définir la valeur de et Valider pour vous aider à créer des règles. Chaque type de règle vous permet de définir des conditions et des actions dans une règle. Le document décrit de façon plus détaillée chaque type de règle.

Une règle suit généralement l’un des concepts suivants :

**Condition-action** Dans ce concept, une règle définit d’abord une condition suivie d’une action à déclencher. Le concept est comparable à l’instruction if-then des langages de programmation.

Dans l’éditeur de règles, le type de règle **Lorsque** applique le concept de condition-action.

**Action-condition** Dans ce concept, une règle définit d’abord une action à déclencher suivie de conditions d’évaluation. Une autre variante de ce concept est une action alternative d’action-condition, qui définit également une action alternative à déclencher si la condition renvoie la valeur False.

Les types de règle Afficher, Masquer, Activer, Désactiver, Définir la valeur de et Valider de l’éditeur de règles appliquent le concept de règle d’action-condition. Par défaut, l’action alternative d’Afficher est Masquer et l’action alternative d’Activer est Désactiver, et inversement. Vous ne pouvez pas modifier l’action alternative par défaut.

>[!NOTE]
>
>Les types de règle disponibles, y compris les conditions et actions que vous définissez dans l’éditeur de règles, dépendent également du type d’objet de formulaire sur lequel vous créez une règle. L’éditeur de règles affiche uniquement les types de règle et les options valides lors de la création des instructions de condition et d’action pour un type particulier d’objet de formulaire. Par exemple, vous ne voyez pas les types Valider et Définir la valeur de pour un objet de panneau.

Pour plus d’informations sur les types de règles disponibles dans l’éditeur de règles, reportez-vous à la section [Types de règles disponibles dans l’éditeur de règles](rule-editor.md#p-available-rule-types-in-rule-editor-p).

### Recommandations pour la sélection d’un concept de règle {#guidelines-for-choosing-a-rule-construct}

Même si vous pouvez obtenir la plupart des cas d’utilisation avec n’importe quel concept de règle, voici quelques recommandations pour sélectionner un concept plutôt qu’un autre. Pour plus d’informations sur les règles disponibles dans l’éditeur de règles, reportez-vous à la section [Types de règles disponibles dans l’éditeur de règles](rule-editor.md#p-available-rule-types-in-rule-editor-p).

* Lors de la création d’une règle, réfléchissez d’abord au contexte de l’objet pour lequel vous la créez. Supposons que vous souhaitiez masquer ou afficher le champ B en fonction de la valeur spécifiée par un utilisateur ou une utilisatrice dans le champ A. Dans ce cas, vous évaluez une condition sur le champ A, et selon la valeur qu’elle renvoie, vous déclenchez une action sur le champ B.

  Par conséquent, si vous créez une règle pour le champ B (l’objet pour lequel vous évaluez une condition), utilisez le concept de condition-action ou le type de règle Lorsque. De même, utilisez le concept d’action-condition ou le type de règle Afficher ou Masquer pour le champ A.

* Parfois, vous devez exécuter plusieurs actions en fonction d’une condition. Dans pareils cas, il est recommandé d’utiliser le concept de condition-action. Dans ce concept, vous pouvez évaluer une condition une fois et spécifier plusieurs instructions d’action.

  Par exemple, pour masquer les champs B, C et D en fonction de la condition qui vérifie la valeur spécifiée par un utilisateur ou une utilisatrice dans le champ A, écrivez une règle avec le concept de condition-action ou le type de règle Lorsque dans le champ A et spécifiez les actions pour contrôler la visibilité des champs B, C et D. Dans le cas contraire, vous avez besoin de trois règles distinctes sur les champs B, C et D, où chaque règle vérifie la condition et affiche ou masque le champ correspondant. Dans cet exemple, il est plus efficace d’écrire le type de règle Lorsque sur un objet plutôt que le type de règle Afficher ou Masquer sur trois objets.

* Pour déclencher une action en fonction de plusieurs conditions, il est recommandé d’utiliser un concept action-condition. Par exemple, pour afficher et masquer le champ A en évaluant les conditions sur les champs B, C et D, utilisez le type de règle Afficher ou Masquer sur le champ A.
* Utilisez le concept de condition-action ou d’action-condition si la règle contient une action pour une condition.
* Si une règle recherche une condition et effectue une action immédiatement lors de la fourniture d’une valeur dans un champ ou de la sortie d’un champ, il est recommandé de créer une règle avec un concept de condition-action ou le type de règle Lorsque sur le champ sur lequel la condition est évaluée.
* La condition dans la règle Lorsque est évaluée lorsqu’un utilisateur modifie la valeur de l’objet pour lequel la règle Lorsque est appliquée. Cependant, si vous souhaitez déclencher l’action lorsque la valeur change du côté serveur, comme lorsque vous préremplissez la valeur, il est recommandé de créer une règle Lorsque qui déclenche l’action lors de l’initialisation du champ.
* Lorsque vous créez des règles pour les menus déroulants, les boutons radio ou les cases à cocher, les options ou les valeurs de ces objets de formulaire sont préremplies dans l’éditeur de règles.

Pour comprendre comment utiliser l’interface utilisateur pour l’écriture et la gestion de règles dans un éditeur de règles, reportez-vous à l’article [Interface utilisateur de l’éditeur de règles pour le Forms adaptatif basé sur les composants principaux](/help/forms/rule-editor-core-components-user-interface.md).

## Voir également

{{see-also-rule-editor}}