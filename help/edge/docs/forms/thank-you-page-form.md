---
title: Afficher un message de remerciement personnalisé après l’envoi du formulaire
description: Découvrez comment configurer les pages de remerciement et la redirection pour le bloc de formulaires afin d’optimiser l’expérience client et de rationaliser les parcours des utilisateurs et utilisatrices.
feature: Edge Delivery Services
exl-id: e6c66b22-dc52-49e3-a920-059adb5be22f
role: Admin, Architect, Developer
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: ht
source-wordcount: '557'
ht-degree: 100%

---

# Afficher un message de remerciement personnalisé après l’envoi du formulaire

Une fois qu’un utilisateur ou une utilisatrice a envoyé un formulaire, il est essentiel de fournir une expérience transparente au moyen d’un message de remerciement. Cela confirme non seulement la réussite de l’envoi, mais améliore également la satisfaction des utilisateurs et utilisatrices et les guide davantage dans leur parcours.

- **Message de remerciement** : un message de remerciement est une pierre angulaire de l’expérience client, offrant des informations rassurantes et véhiculant des informations importantes tout en renforçant l’identité de marque. Il sert de reconnaissance directe de l’action de l’utilisateur, favorisant un sentiment d’achèvement et de satisfaction.

- **Redirection** : une redirection joue un rôle essentiel pour orienter les utilisateurs et utilisatrices vers les destinations appropriées, optimiser l’engagement et, en fin de compte, augmenter les taux de conversion. En guidant de manière transparente les utilisateurs et utilisatrices vers l’étape suivante de leur parcours, une redirection garantit une navigation fluide. Par exemple, rediriger l’utilisateur ou l’utilisatrice vers la page des paiements après avoir collecté les détails initiaux.

Le comportement par défaut du bloc de formulaires adaptatifs consiste à afficher le message de remerciement suivant lors de l’envoi. Le message s’affiche en haut du formulaire lors de la réussite de l’envoi de ce dernier.

![Message de remerciement par défaut](/help/edge/assets/thank-you-message.png)

Vous avez toutefois la possibilité de personnaliser cette expérience en fonction de vos besoins spécifiques. Les options disponibles sont les suivantes :

- Afficher un message de remerciement personnalisé après l’envoi du formulaire
- Rediriger les utilisateurs et utilisatrices vers une autre page après envoi pour effectuer d’autres actions

>[!NOTE]
>
> Pour personnaliser le message de remerciement en fonction de vos besoins, reportez-vous à la [feuille de calcul de demande](/help/edge/docs/forms/assets/enquiry.xlsx) ci-après.

## Configurer un message de remerciement personnalisé

Si vous souhaitez afficher un message de remerciement personnalisé lors de la réussite de l’envoi d’un formulaire, vous pouvez configurer votre feuille de calcul pour réaliser cette action.

Pour configurer un message de remerciement personnalisé pour votre bloc de formulaires adaptatifs, procédez comme suit :

1. Accédez au dossier du projet Edge Delivery sur Microsoft SharePoint ou Google Workspace et ouvrez votre feuille de calcul.
1. Ajoutez un message de remerciement personnalisé dans la colonne `value` pour le type de champ `submit` dans la feuille de calcul.

   ![Message de remerciement personnalisé](/help/edge/docs/forms/assets/thankyou-custommessage.png)

   Par exemple, ajoutez le message `Submission Successful!` dans la colonne `value` pour le type de champ `submit`.

1. Prévisualisez et publiez la feuille à l’aide d’[AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

   ![Message de remerciement personnalisé](/help/edge/docs/forms/assets/customized-thank-you-message.png)

## Rediriger les utilisateurs et utilisatrices vers une autre page après envoi

La redirection d’un utilisateur ou d’une utilisatrice vers une autre page après l’envoi du formulaire peut améliorer l’expérience utilisateur en fournissant des informations pertinentes, en confirmant les actions et en guidant les utilisateurs et utilisatrices vers les résultats souhaités. Par exemple :

- après le remplissage d’un formulaire d’achat, l’utilisateur ou utilisatrice est redirigé vers une page de paiement pour terminer la transaction en toute sécurité.
- lors de l’envoi d’un formulaire d’enregistrement pour un événement ou un webinaire, les utilisateurs et utilisatrices sont redirigés vers une page de confirmation qui affiche les détails de l’événement tels que la date, l’heure et l’emplacement.

Pour rediriger les utilisateurs et utilisatrices vers une autre page, procédez comme suit :

1. Accédez au dossier du projet Edge Delivery sur Microsoft SharePoint ou Google Workspace et ouvrez votre feuille de calcul.
1. Collez l’URL dans la colonne `value` pour le type de champ `submit` dans la feuille de calcul afin de rediriger l’utilisateur ou l’utilisatrice lors de la réussite de l’envoi du formulaire.
Pour rediriger la page vers une autre page, utilisez l’URL de la page [Documentation Edge Delivery](https://www.aem.live/docs/).

   ![URL de redirection de message de remerciement](/help/edge/docs/forms/assets/thankyou-redirecturl.png)

1. Prévisualisez et publiez la feuille à l’aide d’[AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

   ![Message de remerciement de redirection](/help/edge/docs/forms/assets/thankyou-redirectpage.gif)

Vous pouvez également créer un fichier document et ajouter son URL de prévisualisation dans la colonne `value` pour le type de champ `submit`.

Une fois qu’un utilisateur ou une utilisatrice a envoyé un formulaire, il est important de fournir un message de remerciement clair. Cela confirme la réussite de l’envoi et améliore la satisfaction de l’utilisateur ou utilisatrice.

