---
title: Configuration de la page de remerciement pour EDS Forms
description: Découvrez comment configurer les pages de remerciement et la redirection pour EDS Forms afin d’optimiser l’expérience utilisateur et de rationaliser les parcours utilisateur.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: cadeccd916884ca2437e2b2684771c181cc8281e
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 1%

---


# Afficher la page de remerciement ou le formulaire de redirection après envoi

Une fois qu’un utilisateur a envoyé un formulaire, il est essentiel de fournir une expérience transparente au moyen d’une page de remerciement ou d’une redirection. Ces éléments confirment non seulement la réussite de l’envoi, mais améliorent également la satisfaction des utilisateurs et les guident davantage dans leur parcours.

* **Page de remerciement**: une page de remerciement est la pierre angulaire de l’expérience utilisateur, offrant des informations rassurantes et véhiculant des informations importantes tout en renforçant l’identité de marque. Il sert de reconnaissance directe de l’action de l’utilisateur, favorisant un sentiment d’achèvement et de satisfaction.

* **Rediriger**: une redirection joue un rôle essentiel pour orienter les utilisateurs vers des destinations pertinentes, optimiser l’engagement et, en fin de compte, augmenter les taux de conversion. En guidant de manière transparente les utilisateurs vers l’étape suivante de leur parcours, une redirection garantit une navigation fluide. Par exemple, rediriger l’utilisateur vers la page des paiements après avoir collecté les détails initiaux.

Dans le bloc Forms adaptatif, le comportement par défaut est d’afficher une page de remerciement. Vous avez toutefois la possibilité de personnaliser cette expérience en fonction de vos besoins spécifiques. Les options incluent :

* [Configuration de la page de remerciement et du message pour vous aligner sur vos objectifs en matière de marque et de communication](#configuring-the-thank-you-page-and-message)
* [Redirection des utilisateurs vers une autre page après envoi](#redirect-users-to-another-page-post-submission), en améliorant davantage leur parcours

## Configuration de la page de remerciement et du message

Le comportement par défaut du bloc Forms adaptatif est d’afficher la page de remerciement lors de l’envoi. Pour configurer la page de remerciement de votre bloc Adaptive Forms, procédez comme suit :

1. Accédez à votre dossier de projet de diffusion Edge AEM sur Microsoft SharePoint ou Google Workspace.
1. Créez un fichier Microsoft Word ou Google Docs nommé &quot;Merci&quot; dans le répertoire de votre projet.
1. Ajoutez votre message de remerciement au fichier &quot;Merci&quot;. </br>

   ![Exemple de page de remerciement](/help/edge/assets/sample-thankyou-page.png)

1. Utilisez AEM Sidekick pour prévisualiser et publier le fichier &quot;thankyou&quot;.

Votre bloc Forms adaptatif affiche la page de remerciement lors de l’envoi du formulaire.

## Rediriger les utilisateurs vers une autre page après envoi

Par défaut, le bloc Forms adaptatif redirige les utilisateurs vers la page de remerciement. Pour rediriger les utilisateurs vers une page autre que la page de remerciement par défaut, deux options s’offrent à vous :

* soit remplacer la page &quot;Merci&quot; existante par une autre page, soit
* redirigez la page &quot;thankyou&quot; vers une autre page de votre choix.

### Remplacez la page &quot;Merci&quot; existante.

1. Ouvrez le[Projet EDS]/blocks/form/form.js&quot; pour modification.
1. Modifiez la variable `thankyou` dans la ligne suivante à la page de votre choix :

   ```JavaScript
   window.location.href = form.dataset?.redirect || 'thankyou';
   ```

   Par exemple,

   ```JavaScript
   window.location.href = form.dataset?.redirect || 'payment';
   ```

   >[!NOTE]
   >
   > Assurez-vous qu’il existe une page portant le même nom dans le dossier de projet du service de diffusion Edge sur Microsoft SharePoint ou Google Workspace. Si la page n’existe pas, créez-la et publiez-la.

1. Continuez pour archiver le dossier &quot;form.js&quot; mis à jour et ses fichiers sous-jacents dans votre projet de service de diffusion Edge sur GitHub. Cette mise à jour garantit que le formulaire redirige désormais vers la page mise à jour, comme indiqué.

1. Assurez-vous que la page existe dans votre dossier de projet EDS et publiez-la.


### Utilisation des redirections de site web

Configurez une redirection de site web pour rediriger la page &quot;Merci&quot; vers une autre page. Voir [Documentation sur les redirections](https://www.aem.live/docs/redirects) pour obtenir des instructions détaillées.

## En savoir plus

* [Composants de formulaire](/help/edge/docs/forms/form-components.md)
* [Propriétés des champs de formulaire](/help/edge/docs/forms/eds-form-field-properties)
* [Créer et prévisualiser un formulaire](/help/edge/docs/forms/create-forms.md)
* [Activer le formulaire pour envoyer des données](/help/edge/docs/forms/submit-forms.md)
* [Publier un formulaire sur la page de sites](/help/edge/docs/forms/publish-eds-forms.md)
* [Ajouter des validations à des champs de formulaire](/help/edge/docs/forms/validate-forms.md)
* [Modifier les thèmes et le style du formulaire](/help/edge/docs/forms/style-theme-forms.md)
