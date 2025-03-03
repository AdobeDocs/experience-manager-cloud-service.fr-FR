---
title: Actions Envoyer
description: Configurez les actions Envoyer pour un formulaire adaptatif.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: beee9be7-8215-496b-9fb9-61fba000a055
source-git-commit: 0c6f024594e1b1fd98174914d2c0714dffecb241
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 100%

---

# Action Envoyer pour formulaire adaptatif

Une action Envoyer spécifie la destination des données collectées par le biais d’un formulaire adaptatif. Le processus d’envoi commence lorsque l’utilisateur ou l’utilisatrice clique sur le bouton **[!UICONTROL Envoyer]** du formulaire. AEM Forms propose deux types d’actions d’envoi décrites ci-dessous et vous permet de créer et d’utiliser des actions d’envoi personnalisées pour répondre à vos besoins spécifiques. Les actions d’envoi prêtes à l’emploi sont les suivantes :

<!--To define a Submit Action for an Adaptive Form, you use the Properties dialog of the **Adaptive Form block** in the **Editor**-->

* [Envoyer vers le point d’entrée REST](#rest-endpoint-submission-ue)
* [Envoyer un e-mail](#email-submission-ue)


### Envoyer vers le point d’entrée REST {#rest-endpoint-submission-ue}

L’action Envoyer vers le point d’entrée REST est utilisée pour envoyer les données de formulaire envoyées à un point d’entrée REST spécifié. Le point d’entrée peut appartenir à un serveur interne sur lequel le formulaire est hébergé ou à un serveur externe en utilisant un chemin relatif ou un chemin absolu. Pour envoyer des données au serveur AEM qui héberge le formulaire, utilisez un chemin d’accès relatif correspondant au chemin racine du serveur AEM. Par exemple, `/content/forms/af/SampleForm.html`. Pour envoyer des données vers un autre serveur, utilisez un chemin d’accès absolu.

<!--Configuring the Submit Action to REST Endpoint for Adaptive Forms offers several benefits such as:  
* It facilitates seamless integration of form data with external systems and services via RESTful APIs.  
* Offers flexibility in managing data submissions from Adaptive Forms, accommodating dynamic and complex data structures.  
* Allows dynamic mapping of form fields to parameters within the REST endpoint URL, enabling adaptable and customizable data submissions.
-->



Pour configurer un point d’entrée REST :

1. Ouvrez le formulaire adaptatif dans l’**[!UICONTROL Éditeur]**.
1. Sélectionnez **[!UICONTROL Bloc de formulaire adaptatif]**.
1. Cliquez sur l’icône des propriétés ![propriétés](/help/forms/assets/Smock_Properties_18_N.svg).
1. Sélectionnez l’option **[!UICONTROL Envoyer vers un point d’entrée REST]** dans la liste déroulante **[!UICONTROL Action d’envoi]**.
1. Spécifiez l’URL du point d’entrée REST.
1. Vous pouvez également **Activer la requête POST** et fournir une adresse URL pour la publication de la requête.

![Activer la requête POST pour les formulaires adaptatifs](/help/forms/assets/enable-post-request-ue.png)

>[!NOTE]
>
> * Pour publier des données sur un serveur interne, indiquez le chemin de la ressource. Les données sont publiées avec le chemin de la ressource. Par exemple, `/content/restEndPoint`. Pour ces requêtes de publication, les informations d’authentification de la requête d’envoi sont utilisées.
> * Pour publier des données sur un serveur externe, indiquez une URL. Le format d’URL est le suivant : `https://host:port/path_to_rest_end_point`. Assurez-vous de configurer le chemin pour que la requête POST soit traitée anonymement.

### Envoyer un e-mail {#email-submission-ue}

L’action d’envoi Envoyer un e-mail vous permet d’envoyer un e-mail à une ou plusieurs personnes destinataires lors de l’envoi du formulaire. La configuration Envoyer un e-mail permet de créer un e-mail qui peut inclure des données de formulaire dans un format prédéfini. Par exemple, envisagez le modèle suivant où le nom du client ou de la cliente, l’adresse d’expédition, le nom de l’État et le code postal sont récupérés à partir des données de formulaire envoyées. [En savoir plus sur les modèles d’e-mail dans les formulaires adaptatifs](/help/forms/html-email-templates-in-adaptive-forms.md). Voici quelques avantages de la configuration d’un formulaire adaptatif avec une action d’envoi Envoyer un e-mail :

1. Elle permet une communication rapide, car les données de formulaire sont directement envoyées aux destinataires d’e-mail désignés.
1. Elle permet de rationaliser le workflow en intégrant directement les envois de formulaire dans les notifications par e-mail.
1. Elle permet aux entreprises de personnaliser le contenu des e-mails, afin qu’il réponde à des besoins de communication spécifiques.

![Propriétés de formulaire adaptatif dans l’éditeur universel](/help/forms/assets/submit-actions-ue.png)


Pour configurer une action d’envoi en tant qu’e-mail pour l’envoi du formulaire :

1. Ouvrez le formulaire adaptatif dans l’**Éditeur**.
1. Sélectionnez votre **[!UICONTROL Bloc de formulaire adaptatif]**.
1. Cliquez sur l’icône des propriétés ![propriétés](/help/forms/assets/Smock_Properties_18_N.svg).
1. Sélectionnez l’option **[!UICONTROL Envoyer un e-mail]** dans la liste déroulante **[!UICONTROL Action d’envoi]**.
1. Une fois que vous avez sélectionné l’option d’envoi d’e-mail, vous pouvez configurer les propriétés suivantes, comme illustré dans l’image ci-dessous.

<table>
  <thead>
    <tr>
      <th>Image</th>
      <th>Propriété</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
    <td rowspan="7"><img src="/help/forms/assets/email-config-ue.png" alt="Configuration du canal e-mail"></td> 
    <td><b>De</td>
    <td>Indiquez l’adresse e-mail d’expédition.</td>
    </tr>
    <tr>
      <td><b>À</td>
      <td>Indiquez les principales personnes destinataires de l’e-mail. Vous pouvez ajouter plusieurs adresses e-mail en les séparant par des virgules.</td>
    </tr>
    <tr>
      <td><b>Cc</td>
      <td>Indiquez les destinataires qui doivent recevoir une copie carbone (Cc) de l’e-mail.</td>
    </tr>
    <tr>
      <td><b>Cci</td>
      <td>Spécifiez les destinataires qui doivent recevoir une copie carbone invisible (Cci) de l’e-mail.</td>
    </tr>
    <tr>
      <td><b>Objet</td>
      <td>Indiquez l’objet de l’e-mail.</td>
    </tr>
    <tr>
      <td><b>Utiliser un modèle externe</td>
      <td>Permet d’utiliser un modèle d’e-mail externe pour mettre en forme le contenu de l’e-mail. Indiquez l’URL ou le chemin d’accès au modèle externe pour intégrer un modèle d’e-mail préconçu hébergé dans votre dossier AEM Assets.</td>
    </tr>
    <tr>
      <td><b>Inclure une pièce jointe</td>
      <td>Indique si les données de formulaire envoyées doivent inclure une pièce jointe envoyée par le biais du formulaire dans l’e-mail. Les formats de pièce jointe pris en charge sont PDF, XML et JSON.</td>
    </tr>
  </tbody>
</table>






<!--
        
        * **From**: The email address of the sender.
        * **To**: Specify the primary recipients of the email, multiple email addresses can be added, separated by commas.
        * **CC**: Specify the recipients who should receive a carbon copy (CC) of the email.
        * **BCC**: Specify the recipients who should receive a blind carbon copy (BCC) of the email.
        * **Subject**: Specify the subject line of the email.
        * **Use External Template**: Enables the use of an external email template for formatting the email content. Provide the URL or path to the External template path to integrate a pre-designed email template hosted in your AEM Assets folder.
        * **Include Attachment**: Specifies whether the submitted form data should include an attachment submitted through the form in the email.

    {width=50%,height=50%}![Enable post request for adaptive forms](/help/forms/assets/email-config-ue.png)

-->

## Afficher un message de remerciement personnalisé lors de l’envoi du formulaire adaptatif {#submit-action-message-ue}

L’option Lors de l’envoi vous permet de configurer un message d’action d’envoi lors de l’envoi du formulaire adaptatif. Pour configurer un message d’action d’envoi pour votre formulaire :

1. Ouvrez le formulaire adaptatif dans l’**Éditeur**.
1. Sélectionnez votre **[!UICONTROL Bloc de formulaire adaptatif]**.
1. Cliquez sur l’icône des propriétés ![propriétés](/help/forms/assets/Smock_Properties_18_N.svg).
1. En cliquant, l’option suivante s’affiche :
   * **[!UICONTROL Lors de l’envoi]** : cette option vous permet de personnaliser un message à afficher lorsqu’un formulaire est envoyé. Par défaut, un message personnalisé « Merci pour votre envoi du formulaire » s’affiche pour l’utilisateur ou l’utilisatrice lorsqu’un formulaire est envoyé.
Vous pouvez également personnaliser le message de remerciement lors de l’envoi du formulaire en sélectionnant l’option **[!UICONTROL Afficher le message]** et en ajoutant/modifiant votre message dans l’**Éditeur** de texte enrichi.


## Voir également

{{universal-editor-see-also}}

