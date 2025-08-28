---
title: Ajouter des sections répétables à un formulaire
description: Ajouter des sections répétables à un formulaire EDS
feature: Edge Delivery Services
exl-id: 062d5a88-48ca-421f-bf0d-1483e3cfee28
role: Admin, Architect, Developer
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: ht
source-wordcount: '531'
ht-degree: 100%

---

# Ajouter des sections répétables à un formulaire

Le bloc de formulaires adaptatifs permet d’ajouter ou de rendre répétable une section ou un composant d’un formulaire. Cela permet aux utilisateurs et utilisatrices de saisir plusieurs fois des informations pour le même type de données, facilitant ainsi la collecte d’informations telles que l’expérience professionnelle ou la formation.

Prenons l’exemple d’un formulaire utilisé pour collecter des informations sur l’expérience professionnelle d’une personne. Vous pouvez avoir une section répétable pour capturer les détails de chaque emploi précédent. La section répétable contient généralement des champs tels que le nom de l’entreprise, l’intitulé du poste, les dates de début et de fin d’emploi, et les responsabilités. La personne utilisatrice peut ajouter plusieurs instances de la section répétable pour saisir des informations sur chaque emploi qu’elle a effectué.

À la fin de cet article, vous saurez :

- [créer une section répétable dans un formulaire ;](#add-repeatable-sections-to-a-form)
- [définir le nombre minimum ou maximum de répétitions dans un formulaire.](#set-minimum-or-maximum-number-of-repetitions-for-a-repeatable-section)

## Créer une section répétable

La création d’une section répétable dans un formulaire permet aux utilisateurs et utilisatrices de saisir plusieurs instances d’un même ensemble de données, permettant ainsi de collecter efficacement des informations répétitives. Pour créer une section répétable dans un formulaire :

1. Accédez au dossier du projet Edge Delivery sur Microsoft SharePoint ou Google Workspace et ouvrez votre feuille de calcul.

1. Ajoutez un champ de formulaire avec la propriété `type` définie sur `fieldset`.
1. Spécifiez le `Name` du champ. La propriété name est utilisée pour créer une section répétable.
1. Activez la répétabilité en définissant `repeatable` sur `true`.
1. Spécifiez un `label` descriptif pour le champ. Il sert d’en-tête à la section répétable.

   Reportez-vous à l’image ci-dessous pour obtenir l’illustration d’une section d’historique d’emploi dans un formulaire de candidature.

   ![](/help/edge/assets/repeatable-section-example-job-application-form.png)

1. Pour chaque champ que vous souhaitez inclure dans la section, définissez sa propriété `Fieldset` sur le même nom que celui choisi à l’étape 3.

   Par exemple, désignez `experience` dans la propriété Fieldset de tous les champs pertinents à inclure dans la section `employment history`.

   ![Exemple d’un champ de section répétable et ses propriétés](/help/edge/assets/repeatable-section--mention-fieldset-name-example-job-application-form.png)

1. Utilisez [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) pour prévisualiser et publier la feuille. La section répétable est ajoutée au formulaire.

   Sous la section répétable, les utilisateurs et utilisatrices trouvent un bouton **Ajouter** intuitif, ce qui facilite l’ajout de plusieurs sections.

   ![Section répétable, bouton Ajouter pour ajouter plusieurs sections](/help/edge/assets/repeatable-section-example.png)


## Définir le nombre minimum et maximum de répétitions

Dans la conception de formulaire, il est préférable de définir le nombre minimum et maximum de répétitions pour les sections répétables. Ce faisant, vous établissez le contrôle et la cohérence tout en guidant efficacement les utilisateurs et utilisatrices. Pour définir le nombre minimum ou maximum de répétitions :

1. Accédez au dossier du projet Edge Delivery sur Microsoft SharePoint ou Google Workspace et ouvrez votre feuille de calcul.

1. Pour un champ de `type` `fieldset` et la propriété `repeatable` définie sur `true` :

   - définissez la propriété `min` pour spécifier le nombre minimum de répétitions possibles de la section.

   - définissez la propriété `max` pour spécifier le nombre maximum de répétitions possibles de la section.

   ![Définition des propriétés minimum et maximum pour spécifier le nombre de répétitions possibles de la section](/help/edge/assets/repeatable-section-set-min-max.png)

1. Utilisez [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) pour prévisualiser et publier la feuille.

   Lors de l’ajout d’une section répétable, les utilisateurs et utilisatrices trouvent une icône **Supprimer** intuitive, ce qui facilite la suppression des sections répétables. Une fois ajoutées, ces sections ne peuvent pas être réduites à moins d’instances que le nombre spécifié par la propriété `min`. Cela garantit le respect des exigences minimales de remplissage du formulaire définies.


