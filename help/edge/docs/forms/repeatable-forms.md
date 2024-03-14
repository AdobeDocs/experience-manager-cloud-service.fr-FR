---
title: Ajout de sections répétables à un formulaire
description: Ajout de sections répétables à un formulaire EDS
feature: Edge Delivery Services
exl-id: 062d5a88-48ca-421f-bf0d-1483e3cfee28
source-git-commit: 5eee563a9a425ef187afed69a8159d8b1298dad7
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 14%

---

# Ajout de sections répétables à un formulaire

Le bloc Forms adaptatif permet d’ajouter ou de rendre répétable une section ou un composant d’un formulaire. Cela permet aux utilisateurs de saisir plusieurs fois des informations pour le même type de données, ce qui facilite la collecte d’informations telles que l’expérience professionnelle ou le cursus de formation.

Prenons l’exemple d’un formulaire utilisé pour collecter des informations sur l’expérience professionnelle d’une personne. Vous pouvez avoir une section répétable pour capturer les détails de chaque emploi précédent. La section répétable contient généralement des champs tels que le nom de l’entreprise, l’intitulé du poste, les dates de début et de fin d’emploi, et les responsabilités. La personne utilisatrice peut ajouter plusieurs instances de la section répétable pour saisir des informations sur chaque emploi qu’elle a effectué.

À la fin de cet article, vous saurez :

* [Création d’une section répétable dans un formulaire](#add-repeatable-sections-to-a-form)
* [Définir le nombre minimum ou maximum de répétitions dans un formulaire](#set-minimum-or-maximum-number-of-repetitions-for-a-repeatable-section)

## Création d’une section répétable

La création d’une section répétable dans un formulaire permet aux utilisateurs de saisir plusieurs instances d’un même ensemble de données, ce qui permet une collecte efficace d’informations répétitives. Pour créer une section répétable dans un formulaire :

1. Accédez au dossier de projet Edge Deliver sur Microsoft SharePoint ou Google Workspace et ouvrez votre feuille de calcul.

1. Ajoutez un champ de formulaire avec la fonction `type` définie sur `fieldset`
1. Spécifier `Name` du champ . La propriété name est utilisée pour créer une section répétable.
1. Activation de la répétabilité en définissant `repeatable` to `true`.
1. Spécification d’une description `label` pour le champ . Il sert d’en-tête à la section répétable.

   Reportez-vous à l’image ci-dessous pour obtenir l’illustration d’une section de l’historique de l’emploi dans un formulaire de demande d’emploi.

   ![](/help/edge/assets/repeatable-section-example-job-application-form.png)

1. Pour chaque champ que vous souhaitez inclure dans la section , définissez ses `Fieldset` du même nom que celui choisi à l’étape 3.

   Par exemple, désigner `experience` dans la propriété Fieldset de tous les champs pertinents à inclure dans la propriété `employment history` .

   ![exemple d’un champ de section répétable et ses propriétés](/help/edge/assets/repeatable-section--mention-fieldset-name-example-job-application-form.png)

1. Utilisation [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) pour prévisualiser et publier la feuille. La section répétable est ajoutée au formulaire.

   Sous la section répétable, les utilisateurs trouvent une **Ajouter** , ce qui facilite l’ajout de plusieurs sections.

   ![section répétable, bouton Ajouter pour ajouter plusieurs sections ](/help/edge/assets/repeatable-section-example.png)


## Définition des répétitions minimales et maximales

Dans la conception de formulaire, il est préférable de définir des répétitions minimales et maximales pour les sections répétables. Ce faisant, vous établissez le contrôle et la cohérence tout en guidant efficacement les utilisateurs. Pour définir un nombre minimal ou maximal de répétitions :

1. Accédez au dossier de projet Edge Deliver sur Microsoft SharePoint ou Google Workspace et ouvrez votre feuille de calcul.

1. Pour un champ de `type` `fieldset` et `repeatable` définie sur `true`:

   * définissez la variable `min` pour spécifier le nombre minimal de répétitions de la section.

   * définissez la variable `max` pour spécifier le nombre maximal de répétitions possibles de la section.

   ![Définissez les propriétés min. et max. pour spécifier le nombre de répétitions de la section.](/help/edge/assets/repeatable-section-set-min-max.png)

1. Utilisation [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) pour prévisualiser et publier la feuille.

   Lors de l’ajout d’une section répétable, les utilisateurs trouvent une **Supprimer** , ce qui facilite la suppression des sections répétables. Une fois ajoutées, ces sections ne peuvent pas être réduites à moins d’instances que spécifié par la variable `min` . Cela garantit le respect des exigences minimales définies pour la fin du formulaire.

<!--

For example, consider a form used to collect information from users applying for a loan. . You may have a repeatable section for capturing details of each co-applicant. The repeatable section would typically contain fields such as co-co-applicant

The form allows users to provide personal information, including details of the co-applicants. Users can enter details for co-applicants, with this section being repeatable.

![Repeatable sections in forms](/help/forms/assets/eds-repeatable.png)

## Prerequisites

The [Adaptive Forms Block is enabled](/help/edge/docs/forms/create-forms.md) for your Edge Delivery Services project. 

## Add a repeatable section to a form 

Let's take an example of a loan application form. The form enables users to submit personal information. You can include co-applicant details using repeatable sections, with the option to add a minimum and maximum of three co-applicant sections.

"_You can use a Microsoft Excel file on your SharePoint Site or Google Sheet file on Google Drive to develop a form. Examples in this document are based on a [Microsoft Excel file on your SharePoint Site](https://www.aem.live/docs/setup-customer-SharePoint)._" 


To add repeatable sections in Edge Delivery:

1. [Author a form using Microsoft Excel](#author-form)
2. [Preview and publish the form](#preview-form)

### Author a form using Microsoft Excel {#author-form}

1. Go to your Edge Deliver project folder on Microsoft SharePoint or Google Workspace and open your spreadsheet. For example, open an a spreadsheet named `loan-application.xlsx`.

1. Add a new columns labeled `Repeatable` to the sheet contaning your form fields. By default, the `shared-default` sheet contains the form fields.  

1. Add new columns labeled as `Repeatable`, `Min`, and `Max` in your Microsoft Excel file.
1. Specify the value for the `Repeatable` column as `True` for the fieldset that you want to make repeatable.
1. Specify the values for the `Min` and `Max` columns. The `Min` value represents the minimum number of occurrences for which the panel repeats, while the `Max` value represents the maximum number of occurrences for which the panel repeats.
1. Save your Microsoft Excel file.
     
>[!NOTE]
>
> Here is the [Loan application](/help/forms/assets/loan-application.xlsx) excel sheet for your reference. 

### Preview/Publish the form using your Edge Delivery Service

1. Open or create new document file in a Microsft SharePoint Site to embed the Excel sheet  in it using a `Form Block`. For example, open the `index` file and add a `Form Block`.
2. Open the command prompt, navigate to your AEM Edge Delivery project directory on your local machine, and execute the command as `aem up`.

The form is accessible at `https://localhost:3000`, where clicking the `Add` button adds new repeatable section for entering co-applicant details. You can also delete the the repeatable section by clicking the `Delete` button. 

>[!NOTE]
>
> If you encounter a "Page Not Found" error while accessing your form at localhost, add the directory name of the Microsoft SharePoint Site in front of the URL where your form is located. For example, `http://localhost:3000/<dir-name>/`

-->


## Voir également

{{see-more-forms-eds}}
