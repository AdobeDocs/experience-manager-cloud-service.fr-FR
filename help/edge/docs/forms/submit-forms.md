---
title: Préparer votre feuille de calcul pour accepter des données
description: Créez plus rapidement des formulaires performants à l’aide de feuilles de calcul et de champs du bloc de formulaires adaptatifs.
feature: Edge Delivery Services
exl-id: 0643aee5-3a7f-449f-b086-ed637ae53b5a
role: Admin, Architect, Developer
source-git-commit: cb914f76b0b785a89b20ef5eaacbc36e8217944b
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 65%

---

# Configurer vos feuilles de calcul Google Sheets ou fichiers Microsoft Excel pour commencer à accepter des données


Une fois que vous avez [créé et prévisualisé le formulaire](/help/edge/docs/forms/create-forms.md), il est temps d’activer la feuille de calcul correspondante pour commencer à recevoir des données. Vous pouvez activer manuellement la feuille de calcul pour accepter des données ou utiliser des API d’administration pour permettre à une feuille de calcul d’accepter des données.

![Écosystème de création basé sur des documents](/help/edge/assets/document-based-authoring-workflow-enable-sheet-to-accept-data.png)

<!-- 
>[!VIDEO](https://video.tv.adobe.com/v/3427489?quality=12&learn=on)

-->


## Activer manuellement la feuille de calcul pour accepter des données

Pour permettre à la feuille de calcul d’accepter des données

1. Ouvrez la feuille de calcul contenant votre formulaire et ajoutez une nouvelle feuille, en la renommant `incoming`. Par exemple, le classeur Excel [query](/help/edge/assets/enquiry.xlsx) de Microsoft.

   >[!WARNING]
   >
   > Si la feuille `incoming` n’est pas présente, AEM n’envoie aucune donnée à la feuille de calcul.

1. Dans cette feuille, insérez un tableau nommé « intake_form ». Sélectionnez le nombre de colonnes requis pour correspondre aux noms des champs de votre formulaire. Ensuite, dans la barre d’outils, accédez à Insérer > Tableau et cliquez sur OK.

1. Remplacez le nom du tableau par « intake_form ». Dans Microsoft Excel, pour modifier le nom du tableau, sélectionnez-le, puis cliquez sur Conception du tableau.

1. Ajoutez ensuite les noms des champs de formulaire en tant qu’en-têtes de tableau. Pour vous assurer que les champs sont exactement les mêmes, vous pouvez les copier et les coller à partir de la feuille « shared-aem ».  Dans votre feuille « shared-aem », sélectionnez et copiez les ID de formulaire répertoriés sous la colonne « Nom », à l’exception du champ d’envoi.

1. Dans la feuille « incoming », sélectionnez Collage spécial > Transposer les lignes en colonnes pour copier les identifiants de champ sous forme d’en-têtes de colonne dans cette nouvelle feuille. Ne conservez que les champs dont les données doivent être capturées, les autres peuvent être ignorés.

   Chaque valeur dans la colonne `Name` de la feuille `shared-aem`, à l’exception du bouton d’envoi, peut servir d’en-tête dans la feuille `incoming`. Prenons l’exemple de l’image suivante illustrant les en-têtes d’un formulaire « requête » :

   ![Champs d’un formulaire contact-us](/help/edge/assets/contact-us-form-excel-sheet-fields.png)

1. Utilisez l’extension [AEM Sidekick ](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) pour prévisualiser les mises à jour des formulaires. Votre feuille est maintenant prête à accepter les envois de formulaire entrants.

   >[!NOTE]
   >
   >Même si vous avez déjà prévisualisé la feuille, vous devez la prévisualiser à nouveau après la première création de la feuille `incoming`.


Une fois que les noms de champs sont ajoutés à la feuille `incoming`, votre formulaire est prêt à accepter des envois. Vous pouvez prévisualiser le formulaire et envoyer des données à la feuille à l’aide de celui-ci.

Une fois la feuille configurée pour recevoir des données, vous pouvez [prévisualiser le formulaire](/help/edge/docs/forms/create-forms.md#preview-the-form-using-your-edge-delivery-service-eds-page) <!--or [use POST requests](#use-admin-apis-to-send-data-to-your-sheet)--> commencer à envoyer des données à la feuille.

>[!WARNING]
>
>  Les feuilles « shared-aem » ne doivent jamais contenir d’informations d’identification personnelle ou de données sensibles que vous n’êtes pas à l’aise de voir accessibles au public.

<!--
### Use Admin APIs to enable a spreadsheet to accept data

You can also send a POST request to the form to enable it to accept data and configure headers for the `incoming` sheet. Upon receiving the POST request, the service analyzes the body of request and autonomously generates the essential headers and sheets needed for data ingestion.

To use Admin APIs to enable a spreadsheet to accept data: 


1. Open the workbook that you have created and change the name of the default sheet to `incoming`. 

    >[!WARNING] 
    >
    > If the `incoming` sheet doesn't exist, AEM won't send any data to this workbook.

1. Preview the sheet in the sidekick.

    >[!NOTE] 
    >
    >Even if you have previewed the sheet before, you must preview it again after creating the `incoming` sheet for the first time.

1. Send the POST request to generate the appropriate headers in the `incoming` sheet, and add the `shared-default` sheets to your spread sheet, if it does not exist already.

    To understand how to format the POST request for setting up your sheet, refer to the [Admin API documentation](https://www.aem.live/docs/admin.html#tag/authentication/operation/profile). You can look at the example provided below: 

    **Request** 
    
    ```JSON

    POST 'https://admin.aem.page/form/{owner}/{repo}/{branch}/contact-us.json' \
    --header 'Content-Type: application/json' \
    --data '{
        "data": {
            "Email": "john@wknd.com",
            "Name": "John",
            "Subject": "Regarding Product Inquiry",
            "Message": "I have some questions about your products.",
            "Phone": "123-456-7890",
            "Company": "Adobe Inc.",
            "Country": "United States",
            "PreferredContactMethod": "Email",
            "SubscribeToNewsletter": true
        }
    }'

    ```


    **Response**

    ```JSON

    HTTP/2 200 
    content-type: application/json
    x-invocation-id: 1b3bd30a-8cfb-4f85-a662-4b1f7cf367c5
    cache-control: no-store, private, must-revalidate
    accept-ranges: bytes
    date: Sat, 10 Feb 2024 09:26:48 GMT
    via: 1.1 varnish
    x-served-by: cache-del21736-DEL
    x-cache: MISS
    x-cache-hits: 0
    x-timer: S1707557205.094883,VS0,VE3799
    strict-transport-security: max-age=31557600
    content-length: 138

    {"rowCount":2,"columns":["Email","Name","Subject","Message","Phone","Company","Country",      "PreferredContactMethod","SubscribeToNewsletter"]}%

    ```

    You can use tools like curl or Postman to execute this POST request, as demonstrated below:

    ```JSON

    curl -s -i -X POST 'https://admin.aem.page/form/wkndform/wefinance/main/contact-us.json' \
        --header 'Content-Type: application/json' \
        --data '{
            "data": {
                "Email": "john@wknd.com",
                "Name": "John",
                "Subject": "Regarding Product Inquiry",
                "Message": "I have some questions about your products.",
                "Phone": "123-456-7890",
                "Company": "Wknd Inc.",
                "Country": "United States",
                "PreferredContactMethod": "Email",
                "SubscribeToNewsletter": true
        }
    }'

    ```

    The above mentioned POST request provides sample data, including both form fields and their respective sample values. This data is used by the Admin service to set up the form.

    Your form is now enabled to accept data. You also observe the following changes in your spreadsheet: 

## Automatic changes to sheet once it is enabled to accept data. 

Once the sheet is set to recieve data, you observe the following changes in your spreadsheet: 

A sheet named "Slack" is added to your Excel Workbook or Google Sheet. In this sheet, you can configure automatic notifications for a designated Slack channel whenever new data is ingested into your spreadsheet. At present, AEM supports notifications exclusively to the AEM Engineering Slack organization and the Adobe Enterprise Support organization.

1. To set up Slack notifications enter the "teamId" of the Slack workspace and the "channel name" or "ID". You can also ask the slack-bot (with the debug command) for the "teamId" and the "channel ID". Using the "channel ID" instead of the "channel name" is preferable, as it survives channel renames.

    >[!NOTE] 
    >
    > Older forms didn't have the "teamId" column. The "teamId" was included in the channel column, separated by a "#" or "/".

1. Enter any title that you want and under fields enter the names of the fields you want to see in the Slack notification. Each heading should be separated by a comma (For example name, email).

    >[!WARNING] 
    >
    >  Never should the "shared-default" sheets contain any personally identifiable information or sensitive data that you are not comfortable with being publicly accessible.



<!--
## Send data to your sheet {#send-data-to-your-sheet}

After the sheet is set to receive data, you can [preview the form using Adaptive Forms Block](/help/edge/docs/forms/create-forms.md#preview-the-form-using-your-edge-delivery-service-eds-page) or [use Admin APIs](#use-admin-apis-to-send-data-to-your-sheet) to start sending data to the sheet.

### Use Admin APIs to send data to your sheet

You can send POST requests directly to your form using aem.page, aem.live, or your production domain, to send data. 


```JSON

POST https://branch–repo–owner.aem.(page|live)/email-form
POST https://my-domain.com/email-form

```

>[!NOTE] 
>
> The URL should not have the .json extension. You must publish the sheet for POST operations to function on `.live` or on the production domain.

#### Formatting the form data

There are a few different ways that you can format the form data in the POST body. You can use: 

* array of `name:value` pairs: 
    
    ```JSON
    
    {
      "data": [
        { "name": "name", "value": "Clark Kent" },
        { "name": "email", "value": "superman@example.com" },
        { "name": "subject", "value": "Regarding Product Inquiry" },
        { "name": "message", "value": "I have some questions about your products." },
        { "name": "phone", "value": "123-456-7890" },
        { "name": "company", "value": "Example Inc." },
        { "name": "country", "value": "United States" },
        { "name": "preferred_contact_method", "value": "Email" },
        { "name": "newsletter_subscribe", "value": true }
      ]
    }

    ```

    For example

    ```JSON

    curl -s -i -X POST 'https://main--wefinance--wkndform.aem.page/contact-us' \
        --header 'Content-Type: application/json' \
        --data '{
        "data": [
            { "name": "name", "value": "Clark Kent" },
            { "name": "email", "value": "superman@example.com" },
            { "name": "subject", "value": "Regarding Product Inquiry" },
            { "name": "message", "value": "I have some questions about your        products." },
            { "name": "phone", "value": "123-456-7890" },
            { "name": "company", "value": "Example Inc." },
            { "name": "country", "value": "United States" },
            { "name": "preferred_contact_method", "value": "Email" },
            { "name": "newsletter_subscribe", "value": true }
        ]
    }'

    ```



* an object with `key:value` pairs:

    ```JSON

        {
          "data": {
            "name": "Jessica Jones",
            "email": "jj@example.com",
            "subject": "Regarding Product Inquiry",
            "message": "I have some questions about your products.",
            "phone": "123-456-7890",
            "company": "Example Inc.",
            "country": "United States",
            "preferred_contact_method": "Email",
            "newsletter_subscribe": true
          }
        }

    ```

    For example,

    ```JSON

    curl -s -i -X POST 'https://admin.aem.page/form/wkndform/wefinance/main/contact-us.json' \
    --header 'Content-Type: application/json' \
    --data '{
        "data": {
            "Email": "khushwant@wknd.com",
            "Name": "khushwant",
            "Subject": "Regarding Product Inquiry",
            "Message": "I have some questions about your products.",
            "Phone": "123-456-7890",
            "Company": "Adobe Inc.",
            "Country": "United States",
            "PreferredContactMethod": "Email",
            "SubscribeToNewsletter": true
        }
    }'

    ```

* URL encoded (`x-www-form-urlencoded`) body (with `content-type` header set to `application/x-www-form-urlencoded`)

    ```Shell

    'Email=kent%40wknd.com&Name=clark&Subject=Regarding+Product+Inquiry&Message=I   +have+some+questions+about+your+products.&Phone=123-456-7890&Company=Adobe+Inc.&   Country=United+States&PreferredContactMethod=Email&SubscribeToNewsletter=true'

    ```

    For example, if your project's repository is named "wefinance", it's located under the account owner "wkndform", and you're using the "main" branch.,

    ```Shell

    curl -s -i -X POST \
      -d 'Email=kent%40wknd.com&Name=clark&Subject=Regarding+Product+Inquiry&   Message=I+have+some+questions+about+your+products.&Phone=123-456-7890& Company=Adobe+Inc.&Country=United+States&PreferredContactMethod=Email&   SubscribeToNewsletter=true' \
      https://main--wefinance--wkndform.aem.live/contact-us

    ```
-->

Ensuite, vous pouvez [personnaliser le message de remerciement](/help/edge/docs/forms/thank-you-page-form.md).

## Voir également

{{see-more-forms-eds}}
