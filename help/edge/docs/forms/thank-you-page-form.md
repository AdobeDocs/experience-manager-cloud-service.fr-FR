---
title: Afficher un message de remerciement personnalisé après l’envoi du formulaire
description: Découvrez comment configurer les pages de remerciement et la redirection pour le bloc de formulaires afin d’optimiser l’expérience client et de rationaliser les parcours des utilisateurs et utilisatrices.
feature: Edge Delivery Services
exl-id: e6c66b22-dc52-49e3-a920-059adb5be22f
role: Admin, Architect, Developer
source-git-commit: 4356fcc73a9c33a11365b1eb3f2ebee5c9de24f0
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 25%

---

# Afficher un message de remerciement personnalisé après l’envoi du formulaire

Une fois qu’un utilisateur a envoyé un formulaire, il est essentiel de fournir une expérience transparente au moyen d’un message de remerciement. Il confirme non seulement la réussite de l’envoi, mais il améliore également la satisfaction des utilisateurs et les oriente davantage dans leur parcours.

* **Message de remerciement** : un message de remerciement est une pierre angulaire de l’expérience utilisateur, offrant des informations rassurantes et véhiculant des informations importantes tout en renforçant l’identité de marque. Il sert de reconnaissance directe de l’action de l’utilisateur, favorisant un sentiment d’achèvement et de satisfaction.

* **Redirection** : une redirection joue un rôle essentiel pour orienter les utilisateurs vers les destinations appropriées, optimiser l’engagement et, en fin de compte, augmenter les taux de conversion. En guidant de manière transparente les utilisateurs vers l’étape suivante de leur parcours, une redirection garantit une navigation fluide. Par exemple, rediriger l’utilisateur vers la page des paiements après avoir collecté les détails initiaux.

Le comportement par défaut du bloc de formulaires adaptatifs consiste à afficher le message de remerciement suivant lors de l’envoi. Le message s’affiche en haut du formulaire lors de l’envoi réussi du formulaire.

![Message de remerciement par défaut](/help/edge/assets/thank-you-message.png)

Vous avez toutefois la possibilité de personnaliser cette expérience en fonction de vos besoins spécifiques. Les options incluent :

* Afficher un message de remerciement personnalisé après l’envoi du formulaire
* Rediriger les utilisateurs vers une autre page après envoi pour effectuer d’autres actions.

>[!NOTE]
>
> Pour personnaliser le message de remerciement en fonction de vos besoins, reportez-vous à la [feuille de calcul d&#39;enquête](/help/edge/docs/forms/assets/enquiry.xlsx) ci-après.

## Configurer un message de remerciement personnalisé

Si vous souhaitez afficher un message de remerciement personnalisé lors de l’envoi réussi d’un formulaire, vous pouvez configurer votre feuille de calcul pour l’afficher.

Pour configurer un message de remerciement personnalisé pour votre bloc de formulaires adaptatifs, procédez comme suit :

1. Accédez au dossier du projet Edge Delivery sur Microsoft SharePoint ou Google Workspace et ouvrez votre feuille de calcul.
1. Ajoutez un message de remerciement personnalisé dans la colonne `value` pour le type de champ `submit` dans la feuille de calcul.

   ![Message de remerciement personnalisé](/help/edge/docs/forms/assets/thankyou-custommessage.png)

   Par exemple, ajoutez le message `Submission Successful!` dans la colonne `value` pour le type de champ `submit`.

1. Prévisualisez et publiez la feuille à l’aide d’[AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

   ![Message de remerciement personnalisé](/help/edge/docs/forms/assets/customized-thank-you-message.png)

## Rediriger les utilisateurs vers une autre page après envoi

La redirection d’un utilisateur vers une autre page après l’envoi du formulaire peut améliorer l’expérience utilisateur en fournissant des informations pertinentes, en confirmant les actions et en guidant les utilisateurs vers les résultats souhaités. Par exemple :

* une fois qu’un utilisateur a rempli un formulaire d’achat, il est redirigé vers une page de paiement pour terminer la transaction en toute sécurité.
* lors de l’envoi d’un formulaire d’enregistrement pour un événement ou un webinaire, les utilisateurs sont redirigés vers une page de confirmation qui affiche les détails de l’événement, tels que la date, l’heure et l’emplacement.

Pour rediriger les utilisateurs vers une autre page, procédez comme suit :

1. Accédez au dossier du projet Edge Delivery sur Microsoft SharePoint ou Google Workspace et ouvrez votre feuille de calcul.
1. Collez l’URL dans la colonne `value` pour le type de champ `submit` dans la feuille de calcul afin de rediriger l’utilisateur lors de l’envoi réussi du formulaire.
Pour rediriger la page vers une autre page, utilisez l’URL de la page [Documentation Edge Delivery](https://www.aem.live/docs/).

   ![Merci de l’URL de redirection](/help/edge/docs/forms/assets/thankyou-redirecturl.png)

1. Prévisualisez et publiez la feuille à l’aide d’[AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

   ![Message Redirect Thankyou](/help/edge/docs/forms/assets/thankyou-redirectpage.gif)

Vous pouvez également créer un fichier de document et ajouter son URL de prévisualisation dans la colonne `value` pour le type de champ `submit`.

Une fois qu’un utilisateur a envoyé un formulaire, il est important de fournir un message de remerciement clair. Cela confirme la réussite de l’envoi et améliore la satisfaction de l’utilisateur.

## Voir également

{{see-more-forms-eds}}

<!--
## Configuring a custom thank you message

The default behavior of Adaptive Forms Block is to display the following thank you message on submission. The message is displayed on the top of the form. 

![default thank you message](/help/edge/assets/thank-you-message.png)


Follow the below steps to configure a custom thank you message for your Adaptive Forms Block:

1. Access your AEM Project on your local machine or GitHub repository.

2. Navigate to [AEM Project Folder]\blocks\form\submit.js file for editing.

3. Locate the following code 

    ```JavaScript

        thankYouMessage.innerHTML = payload?.body?.thankYouMessage || 'Thanks for your submission';

    ```

4. Replace the default message with your custom message. For example, 


    ```JavaScript

        thankYouMessage.innerHTML = payload?.body?.thankYouMessage || 'Your submission has been received and noted.';

    ```


1. Save the file. Commit the updated file to your GitHub Repository. Now, when you submit a form, the custom thank you message is displayed. For example,

![Custom thank you message](/help/edge/assets/custom-thank-you-message.png)

* **Thank you message**: A thank you message is a cornerstone of user experience, offering reassurance and conveying important information while reinforcing brand identity. It serves as a direct acknowledgment of the user's action, fostering a sense of completion and satisfaction.

* **Redirect**: A redirect plays a pivotal role in steering users towards relevant destinations, optimizing engagement, and ultimately boosting conversion rates. By seamlessly guiding users to the next step in their journey, a redirect ensures a smooth navigation experience. For example, redirecting user to payments page after collecting initial details. 

In the Adaptive Forms Block, the default behavior is to display a thank you message. However, you have the flexibility to tailor this experience to meet your specific needs. Options include:

* [Configuring a custom thank you message to align with your brand and communication goals](#configuring-the-thank-you-page-and-message) 
* [Redirecting users to another page post-submission for further action](#redirect-users-to-another-page-post-submission)

## Redirect users to another page post-submission

Redirecting a user to another page after form submission can enhance user experience by providing relevant information, confirming actions, and guiding users towards desired outcomes. For example, 

* after a user completes a purchase form, they are redirected to a payment page to complete the transaction securely. 
* upon submitting a registration form for an event or webinar, users are redirected to a confirmation page displaying event details, such as date, time, and location.

To redirect the "thankyou" page to a different page, use the [website redirects](https://www.aem.live/docs/redirects) spreadsheet. 





1. Access your AEM Edge Delivery project folder on Microsoft SharePoint or Google Workspace.
1. Create a Microsoft Word or Google Docs file named "thankyou" within your project directory.
1. Add your thank you message to the "thankyou" file. </br>
   
    ![Example thank you page](/help/edge/assets/sample-thankyou-page.png) 

1. Use AEM Sidekick to preview and publish the "thankyou" file.

 Your Adaptive Forms Block displays the "thankyou" page on form submission. 

## Redirect users to another page post-submission

By default, the Adaptive Forms Block redirects the users to the "thankyou" page. To redirect users to a page other than the default "thankyou" page, you have two options: 

* [Replace the "thankyou" page with a different page](#replace-the-existing-thankyou-page) 
* [Use website redirects for "thankyou" page redirection](#use-website-redirects-for-thankyou-page-redirection) 

### Replace the "thankyou" page

1. Open the "[EDS Project]/blocks/form/form.js" file for editing.
1. Change the `thankyou` page in the following line to page of your choice:

    ```JavaScript

    window.location.href = form.dataset?.redirect || 'thankyou';

    ```

    For example,

    ```JavaScript

    window.location.href = form.dataset?.redirect || 'payment';
        
    ```
    
    >[!NOTE]
    >
    > Ensure that a page with the same name exists in your Edge Delivery Services project folder on either Microsoft SharePoint or Google Workspace. If the page does not exist, proceed to create and publish it.  

1. Proceed to check in the updated 'form.js' folder and its underlying files to your Edge Delivery Services project on GitHub. This update ensures that the form now redirects to the updated page as specified.

1. Ensure that the page exists in your EDS project folder and publish it.


### Use website redirects for "thankyou" page redirection

Redirecting a user to another page after form submission can enhance user experience by providing relevant information, confirming actions, and guiding users towards desired outcomes. For example, 

* after a user completes a purchase form, they are redirected to a payment page to complete the transaction securely. 
* upon submitting a registration form for an event or webinar, users are redirected to a confirmation page displaying event details, such as date, time, and location.

To redirect the "thankyou" page to a different page, use the [website redirects](https://www.aem.live/docs/redirects) spreadsheet. 



## See also

{{see-more-forms-eds}}