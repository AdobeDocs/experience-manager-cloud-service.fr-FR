---
title: Préparer votre feuille de calcul pour accepter des données
description: Créez plus rapidement des formulaires performants à l’aide de feuilles de calcul et de champs du bloc de formulaires adaptatifs.
feature: Edge Delivery Services
exl-id: 0643aee5-3a7f-449f-b086-ed637ae53b5a
role: Admin, Architect, Developer
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 100%

---

# Configurer vos feuilles de calcul Google Sheets ou fichiers Microsoft Excel pour commencer à accepter des données


Une fois que vous avez [créé et prévisualisé le formulaire](/help/edge/docs/forms/create-forms.md), il est temps d’activer la feuille de calcul correspondante pour commencer à recevoir des données. Vous pouvez :

- [Activer manuellement la feuille de calcul pour accepter des données](#manually-enable-the-spreadsheet-to-accept-data)
- [Utiliser des API d’administration pour permettre à une feuille de calcul d’accepter des données](#use-admin-apis-to-enable-a-spreadsheet-to-accept-data)

![Écosystème de création basé sur des documents](/help/edge/assets/document-based-authoring-workflow-enable-sheet-to-accept-data.png)


<!--

>[!VIDEO](https://video.tv.adobe.com/v/3427489?quality=12&learn=on)

-->

## Activer manuellement la feuille de calcul pour accepter des données

Pour permettre à la feuille de calcul d’accepter des données

1. Ouvrez la feuille de calcul qui comporte votre formulaire et ajoutez-y une nouvelle feuille en la renommant `incoming`. Par exemple, le classeur Microsoft Excel de formulaires [enquiry](/help/edge/assets/enquiry.xlsx).

   >[!WARNING]
   >
   > Si la feuille `incoming` n’est pas présente, AEM n’envoie aucune donnée à la feuille de calcul.

1. Dans cette feuille, insérez un tableau nommé « intake_form ». Sélectionnez le nombre de colonnes requis pour correspondre aux noms des champs de votre formulaire. Ensuite, dans la barre d’outils, accédez à Insérer > Tableau et cliquez sur OK.

1. Remplacez le nom du tableau par « intake_form ». Dans Microsoft Excel, pour modifier le nom du tableau, sélectionnez-le, puis cliquez sur Conception du tableau.

1. Ajoutez ensuite les noms des champs de formulaire en tant qu’en-têtes de tableau. Pour vous assurer que les champs sont exactement les mêmes, vous pouvez les copier et les coller à partir de la feuille « shared-aem ».  Dans votre feuille « shared-aem », sélectionnez et copiez les identifiants de formulaires répertoriés sous la colonne « Name », à l’exception du champ d’envoi.

1. Dans la feuille « incoming », sélectionnez Collage spécial > Transposer les lignes en colonnes pour copier les identifiants de champ sous forme d’en-têtes de colonne dans cette nouvelle feuille. Ne conservez que les champs dont les données doivent être capturées, les autres peuvent être ignorés.

   Chaque valeur dans la colonne `Name` de la feuille `shared-aem`, à l’exception du bouton d’envoi, peut servir d’en-tête dans la feuille `incoming`. Prenons l’exemple de l’image suivante illustrant les en-têtes d’un formulaire « enquiry » :

   ![Champs d’un formulaire contact-us](/help/edge/assets/contact-us-form-excel-sheet-fields.png)

1. Utilisez l’extension [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) pour prévisualiser les mises à jour du formulaire. Votre feuille est maintenant prête à accepter les envois de formulaire entrants.

   >[!NOTE]
   >
   >Même si vous avez déjà prévisualisé la feuille, vous devez la prévisualiser à nouveau après la première création de la feuille `incoming`.


Une fois que les noms de champ sont ajoutés à la feuille `incoming`, votre formulaire est prêt à accepter des envois. Vous pouvez prévisualiser le formulaire et envoyer des données à la feuille à l’aide de celui-ci.

Une fois la feuille configurée pour recevoir des données, vous pouvez [prévisualiser le formulaire](/help/edge/docs/forms/create-forms.md#preview-the-form-using-your-edge-delivery-service-eds-page) <!--or [use POST requests](#use-admin-apis-to-send-data-to-your-sheet)--> pour commencer à envoyer des données à la feuille.

>[!WARNING]
>
>  Les feuilles « shared-aem » ne doivent jamais contenir d’informations personnelles identifiables ou de données sensibles que vous ne souhaitez pas rendre accessibles au public.


## Utiliser des API d’administration pour permettre à une feuille de calcul d’accepter des données

Vous pouvez également envoyer une requête POST au formulaire pour lui permettre d’accepter des données et configurer des en-têtes pour la feuille `incoming`. Lors de la réception de la requête POST, le service analyse le corps de la requête et génère de manière autonome les en-têtes et les feuilles essentiels nécessaires à l’ingestion des données.

Pour utiliser les API d’administration afin de permettre à une feuille de calcul d’accepter des données :


1. Ouvrez le classeur que vous avez créé et remplacez le nom de la feuille par défaut par `incoming`.

   >[!WARNING]
   >
   > Si la feuille `incoming` n’existe pas, AEM n’enverra aucune donnée à ce classeur.

1. Prévisualisez la feuille dans le sidekick.

   >[!NOTE]
   >
   >Même si vous avez déjà prévisualisé la feuille, vous devez la prévisualiser à nouveau après la première création de la feuille `incoming`.

1. Envoyez la requête POST pour générer les en-têtes appropriés dans la feuille `incoming`, puis ajoutez la feuille `shared-default` à votre feuille de calcul, si elle n’existe pas déjà.

   Pour comprendre comment mettre en forme la requête POST afin de configurer votre feuille, reportez-vous à la [Documentation de l’API d’administration](https://www.aem.live/docs/admin.html#tag/authentication/operation/profile). Vous pouvez consulter l’exemple ci-dessous :

   **Requête**

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


   **Réponse**

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

   Vous pouvez utiliser des outils tels que curl ou Postman pour exécuter cette requête POST, comme illustré ci-dessous :

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

   La requête POST mentionnée ci-dessus fournit des données d’exemple, y compris les champs de formulaire et leurs valeurs d’exemple respectives. Ces données sont utilisées par le service d’administration pour configurer le formulaire.

   Votre formulaire peut maintenant accepter des données. Vous constatez également les modifications suivantes dans votre feuille de calcul :

## Modifications automatiques de la feuille une fois qu’elle est activée pour accepter des données.

Une fois que la feuille est configurée pour recevoir des données, vous constatez les modifications suivantes dans votre feuille de calcul :

Une feuille nommée « Slack » est ajoutée à votre classeur Excel ou à votre feuille Google Sheets. Dans cette feuille, vous pouvez configurer des notifications automatiques pour un canal Slack désigné chaque fois que de nouvelles données sont ingérées dans votre feuille de calcul. Actuellement, AEM prend en charge les notifications exclusivement destinées à l’organisation Slack de l’équipe d’ingénierie AEM et à l’organisation de l’assistance aux entreprises d’Adobe.

1. Pour configurer les notifications Slack, saisissez l’« identifiant de l’équipe » de l’espace de travail Slack et le « nom du canal » ou l’« identifiant ». Vous pouvez également demander au Slackbot (avec la commande debug) l’« identifiant d’équipe » et l’« identifiant du canal ». Il est préférable d’utiliser l’« identifiant du canal » plutôt que le « nom du canal », car il n’est pas modifié lorsque le canal est renommé.

   >[!NOTE]
   >
   > Les formulaires plus anciens ne contenaient pas la colonne « identifiant d’équipe ». L’« identifiant d’équipe » a été inclus dans la colonne du canal, séparé par « # » ou « / ».

1. Saisissez le titre de votre choix et sous les champs, saisissez le nom des champs que vous souhaitez voir dans la notification Slack. Chaque en-tête doit être séparé par une virgule (par exemple, nom, adresse e-mail).

   >[!WARNING]
   >
   >  Les feuilles « shared-default » ne doivent jamais contenir d’informations personnelles identifiables ou de données sensibles que vous ne souhaitez pas rendre accessibles au public.



Ensuite, vous pouvez [personnaliser le message de remerciement](/help/edge/docs/forms/thank-you-page-form.md).

