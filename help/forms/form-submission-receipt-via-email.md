---
title: Comment envoyer un accusé de réception d’envoi de formulaire par courrier électronique dans AEM Forms ?
description: AEM Forms vous permet de configurer l’action Envoyer par messagerie qui envoie un accusé de réception à un utilisateur lors de l’envoi du formulaire.
uuid: c80b1ef4-8fe3-48e0-8fc6-3032dc022a38
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
docset: aem65
source-git-commit: 8ed477ec0c54bb0913562b9581e699c0bdc973ec
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 91%

---


# Envoyer un accusé de réception d’envoi de formulaire par e-mail {#sending-a-form-submission-acknowledgement-via-email}

## Envoi de données de formulaire adaptatif {#adaptive-form-data-submission}

Les formulaires adaptatifs fournissent plusieurs processus d’[actions Envoyer](configuring-submit-actions.md) prêts à l’emploi pour envoyer les données de formulaire à différents points d’entrée.

Par exemple, l’action **[!UICONTROL Envoyer un e-mail]** envoie un e-mail lorsque l’envoi d’un formulaire adaptatif a été réussi. Elle peut également être configurée pour envoyer les données de formulaire et le fichier PDF dans l’e-mail.

Cet article décrit la procédure pour activer l’action E-mail dans un formulaire adaptatif et les différentes configurations fournies.

>[!NOTE]
>
>Vous pouvez également utiliser l’option **[!UICONTROL Envoyer PDF par e-mail]** pour envoyer le formulaire rempli par e-mail en tant que pièce jointe. Les options de configuration disponibles pour cette action sont identiques à celles proposées pour l’action **[!UICONTROL Envoyer un e-mail]**. L’action Envoyer PDF par e-mail est disponible uniquement pour les formulaires adaptatifs basés sur XFA.

## Action Envoyer un e-mail {#email-action}

L’action Envoyer un e-mail permet à un auteur d’envoyer automatiquement un e-mail à un ou plusieurs destinataires lors de l’envoi réussi d’un formulaire adaptatif.

<!-- >>[!NOTE]
>
>To use the Send email action, you need to configure the AEM mail service as described in [Configuring the mail service](/help/sites-administering/notification.md#configuring-the-mail-service).

### Enabling Send email action on an Adaptive Form {#enabling-email-action-on-an-adaptive-form}

1. Open an Adaptive Form in **[!UICONTROL edit]** mode.

1. In the **[!UICONTROL Content]** tab, tap **[!UICONTROL Form Container]** and tap ![configure](assets/configure-icon.svg) to view the Adaptive Form properties.  

1. In the **[!UICONTROL Submission]** section, select **[!UICONTROL Send email]** from the **[!UICONTROL Submit Action]** drop-down list.  

   ![Submit Actions](assets/submission-actions.png)

1. Specify valid email IDs in the **[!UICONTROL To]**, **[!UICONTROL CC]**, and **[!UICONTROL BCC]** fields.

   Specify the subject and the body of the email in the **[!UICONTROL Subject]** and **[!UICONTROL Email Template]** fields, respectively.

   You can also specify variable placeholders in the fields, in which case, the values of the fields are processed when the form is successfully submitted by an user. For more information, see [Using Adaptive Form field names to dynamically create email content](form-submission-receipt-via-email.md#p-using-adaptive-form-field-names-to-dynamically-create-email-content-p).

   Select **[!UICONTROL Include attachments]** if the form includes file attachments and you want to attach these files in the email.

   >[!NOTE]
   >
   >If you choose the **[!UICONTROL Send PDF via Email]** option, you must select the Include attachments option.

1. Click ![save](assets/save_icon.svg) to save the changes. -->

### Utiliser des noms de champ de formulaire adaptatif pour créer dynamiquement le contenu d’un e-mail {#using-adaptive-form-field-names-to-dynamically-create-email-content}

Dans un formulaire adaptatif, les noms de champ sont appelés espaces réservés. Ils sont remplacés par la valeur du champ après l’envoi du formulaire par un utilisateur.

Sous l’action **[!UICONTROL Envoyer un e-mail]**, vous pouvez utiliser des espaces réservés qui sont traités lorsque l’action est effectuée. Cela implique que les en-têtes de l’e-mail (tels que **[!UICONTROL À]**, **[!UICONTROL Cc]**, **[!UICONTROL Cci]**, **[!UICONTROL Objet]**) sont générés lorsque l’utilisateur envoie le formulaire.

Pour définir un espace réservé, spécifiez `${<field name>}` dans un champ après avoir sélectionné **[!UICONTROL Envoyer un e-mail]** comme action Envoyer.

Par exemple, si le formulaire contient le champ **[!UICONTROL Adresse électronique]**, appelé `email_addr` pour capturer l’identifiant d’adresse électronique d’un utilisateur, vous pouvez spécifier les valeurs suivantes dans les champs **[!UICONTROL À]**, **[!UICONTROL Cc]**, ou **[!UICONTROL Cci]**.

`${email_addr}`

Lorsqu’un utilisateur envoie le formulaire, un e-mail est envoyé à l’identifiant d’adresse électronique entré dans le champ `email_addr` du formulaire.

>[!NOTE]
>
>Vous pouvez trouver le nom d’un champ dans la boîte de dialogue **[!UICONTROL Modifier]** de ce champ.

Les espaces réservés aux variables peuvent également être utilisés dans les champs **[!UICONTROL Objet]** et **[!UICONTROL Modèle d’e-mail]**.

Par exemple :

`Hi ${first_name} ${last_name},`

`Your form has been received by our department. It usually takes ten business days to process the request.`

`Regards`

`Administrator`

>[!NOTE]
>
>Les champs des panneaux répétables ne peuvent pas être utilisés en tant qu’espaces réservés aux variables.

