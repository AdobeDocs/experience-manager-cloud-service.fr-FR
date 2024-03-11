---
title: Préparation de votre feuille de calcul pour l’acceptation des données
description: Créez des formulaires puissants plus rapidement à l’aide de feuilles de calcul et de champs de bloc Forms adaptatifs !
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 0643aee5-3a7f-449f-b086-ed637ae53b5a
source-git-commit: d91254b52c257a3758da200a2c74b736ca457884
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 1%

---

# Préparation de votre feuille de calcul pour l’acceptation des données


Une fois que vous [création et prévisualisation du formulaire](/help/edge/docs/forms/create-forms.md), il est temps d’activer la feuille de calcul correspondante pour commencer à recevoir des données.

![Écosystème de création basé sur les documents](/help/edge/assets/document-based-authoring-workflow-enable-sheet-to-accept-data.png)

<!-- 
>[!VIDEO](https://video.tv.adobe.com/v/3427489?quality=12&learn=on)

-->

Pour activer la feuille de calcul :

1. Ouvrez la feuille de calcul qui comporte votre formulaire et ajoutez-y une nouvelle feuille en la renommant `incoming`.

   >[!WARNING]
   >
   > Si la variable `incoming` n’est pas présente, AEM n’envoie aucune donnée à la feuille de calcul.

1. Dans cette feuille, insérez un tableau nommé &quot;prise_forme&quot;. Sélectionnez le nombre de colonnes requis pour correspondre aux noms des champs de votre formulaire. Ensuite, dans la barre d’outils, accédez à Insérer > Tableau et cliquez sur OK.

1. Remplacez le nom de la table par &quot;ingestion_form&quot;. Dans Microsoft Excel, pour modifier le nom du tableau, sélectionnez-le, puis cliquez sur Conception de tableau.

1. Ajoutez ensuite les noms des champs de formulaire en tant qu’en-têtes de tableau. Pour vous assurer que les champs sont exactement les mêmes, vous pouvez les copier et les coller à partir de la feuille &quot;shared-default&quot;.  Dans votre feuille &quot;shared-default&quot;, sélectionnez et copiez les ID de formulaire répertoriés sous la colonne &quot;Nom&quot;, à l’exception du champ d’envoi.

1. Dans la feuille &quot;entrante&quot;, sélectionnez Coller spécial > Transposer les lignes en colonnes pour copier les identifiants de champ sous forme d’en-têtes de colonne dans cette nouvelle feuille. Conservez uniquement les champs dont les données doivent capturer d’autres champs qui peuvent être ignorés.

   Chaque valeur de la variable `Name` de la colonne `shared-default` , à l’exception du bouton d’envoi, peut servir d’en-tête dans la `incoming` feuille. Prenons l’exemple de l’image suivante illustrant les en-têtes d’un formulaire de &quot;contact-us&quot; :

   ![Champs d’un formulaire de contact](/help/edge/assets/contact-us-form-excel-sheet-fields.png)



1. Utilisez l’extension AEM Sidekick pour prévisualiser les mises à jour du formulaire. Votre feuille est maintenant prête à accepter les envois de formulaire entrants.

   >[!NOTE]
   >
   >Même si vous avez déjà prévisualisé la feuille, vous devez la prévisualiser à nouveau après avoir créé la `incoming` feuille pour la première fois.


Une fois que les noms de champ sont ajoutés au `incoming` , votre formulaire devient prêt à accepter les envois. Vous pouvez prévisualiser le formulaire et envoyer les données à la feuille à l’aide de celui-ci.

Une fois la feuille configurée pour recevoir des données, vous pouvez [prévisualiser le formulaire à l’aide du bloc Forms adaptatif](/help/edge/docs/forms/create-forms.md#preview-the-form-using-your-edge-delivery-service-eds-page) ou [utilisation de requêtes de POST](#use-admin-apis-to-send-data-to-your-sheet) pour commencer à envoyer des données à la feuille.

>[!WARNING]
>
>  Jamais les feuilles &quot;shared-default&quot; ne devraient contenir d’informations d’identification personnelle ou de données sensibles que vous ne connaissez pas lorsque vous êtes connecté au public.


## (Facultatif) Utilisez les API d’administration pour activer une feuille de calcul afin d’accepter des données.

Vous pouvez également envoyer une demande de POST au formulaire pour lui permettre d’accepter des données et de configurer des en-têtes pour le `incoming` feuille. Lors de la réception de la demande du POST, le service analyse le corps de la demande et génère de manière autonome les en-têtes et les feuilles essentiels nécessaires à l’ingestion des données.

Pour utiliser les API d’administration afin d’activer une feuille de calcul pour accepter des données :


1. Ouvrez le classeur que vous avez créé et modifiez le nom de la feuille par défaut en `incoming`.

   >[!WARNING]
   >
   > Si la variable `incoming` n’existe pas, AEM n’enverra aucune donnée à ce classeur.

1. Aperçu de la feuille dans le sidekick.

   >[!NOTE]
   >
   >Même si vous avez déjà prévisualisé la feuille, vous devez la prévisualiser à nouveau après avoir créé la `incoming` feuille pour la première fois.

1. Envoyez la demande au POST pour générer les en-têtes appropriés dans la `incoming` , puis ajoutez le `shared-default` des feuilles à votre feuille de calcul, si elle n’existe pas déjà.

   Pour comprendre comment formater la requête du POST pour configurer votre feuille, reportez-vous à la section [Documentation de l’API d’administration](https://www.aem.live/docs/admin.html#tag/authentication/operation/profile). Vous pouvez consulter l’exemple ci-dessous :

   **Requête**

   ```JSON
   POST 'https://admin.hlx.page/form/{owner}/{repo}/{branch}/contact-us.json' \
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

   Vous pouvez utiliser des outils tels que curl ou Postman pour exécuter cette requête de POST, comme illustré ci-dessous :

   ```JSON
   curl -s -i -X POST 'https://admin.hlx.page/form/wkndforms/portal/main/contact-us.json' \
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

   La requête de POST mentionnée ci-dessus fournit des données d’exemple, y compris les champs de formulaire et leurs valeurs d’exemple respectives. Ces données sont utilisées par le service d’administration pour configurer le formulaire.

   Votre formulaire peut maintenant accepter des données. Vous constatez également les modifications suivantes dans votre feuille de calcul :

## Modifications automatiques de la feuille une fois qu’elle est activée pour accepter les données.


Une fois que la feuille est configurée pour recevoir des données, vous constatez les modifications suivantes dans votre feuille de calcul :

Une feuille nommée &quot;Slack&quot; est ajoutée à votre classeur Excel ou à votre feuille de calcul Google. Dans cette feuille, vous pouvez configurer des notifications automatiques pour un canal de Slack désigné chaque fois que de nouvelles données sont ingérées dans votre feuille de calcul. Actuellement, AEM prend en charge les notifications exclusivement destinées à l’organisation de Slack d’ingénierie AEM et à l’Adobe d’assistance aux entreprises.

1. Pour configurer les notifications de Slack, saisissez l’&quot;TeamId&quot; de l’espace de travail du Slack et le &quot;nom du canal&quot; ou &quot;ID&quot;. Vous pouvez également demander au slack-bot (avec la commande debug) pour &quot;TeamId&quot; et &quot;channel ID&quot;. Il est préférable d’utiliser &quot;l’identifiant du canal&quot; plutôt que le &quot;nom du canal&quot;, car cela permet de survivre aux renommes du canal.

   >[!NOTE]
   >
   > Les formulaires plus anciens ne contenaient pas la colonne &quot;TeamId&quot;. L’ID d’équipe a été inclus dans la colonne du canal, séparé par un &quot;#&quot; ou &quot;/&quot;.

1. Saisissez le titre de votre choix et sous les champs , saisissez le nom des champs que vous souhaitez voir dans la notification du Slack. Chaque en-tête doit être séparé par une virgule (par exemple, nom, email).

   >[!WARNING]
   >
   >  Jamais les feuilles &quot;shared-default&quot; ne devraient contenir d’informations d’identification personnelle ou de données sensibles que vous ne connaissez pas lorsque vous êtes connecté au public.


## Envoi de données à votre feuille {#send-data-to-your-sheet}

Une fois la feuille définie pour recevoir des données, vous pouvez [prévisualiser le formulaire à l’aide du bloc Forms adaptatif](/help/edge/docs/forms/create-forms.md#preview-the-form-using-your-edge-delivery-service-eds-page) ou [Utilisation des API d’administration](#use-admin-apis-to-send-data-to-your-sheet) pour commencer à envoyer des données à la feuille.

### Utiliser les API d’administration pour envoyer des données à votre feuille

Vous pouvez envoyer des demandes de POST directement à votre formulaire à l’aide de hlx.page, hlx.live ou de votre domaine de production pour envoyer des données.


```JSON
POST https://branch–repo–owner.hlx.(page|live)/email-form
POST https://my-domain.com/email-form
```

>[!NOTE]
>
> L’URL ne doit pas avoir l’extension .json. Vous devez publier la feuille pour que les opérations de POST fonctionnent sur `.live` ou sur le domaine de production.

#### Formatage des données de formulaire

Il existe plusieurs manières de formater les données de formulaire dans le corps du POST. Vous pouvez utiliser :

* tableau de `name:value` paires :

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

  Par exemple :

  ```JSON
  curl -s -i -X POST 'https://main--portal--wkndforms.hlx.page/contact-us' \
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



* un objet avec `key:value` paires :

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

  Par exemple,

  ```JSON
  curl -s -i -X POST 'https://admin.hlx.page/form/wkndforms/portal/main/contact-us.json' \
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

* encodé URL (`x-www-form-urlencoded`) corps (avec `content-type` défini sur l’en-tête `application/x-www-form-urlencoded`)

  ```Shell
  'Email=kent%40wknd.com&Name=clark&Subject=Regarding+Product+Inquiry&Message=I   +have+some+questions+about+your+products.&Phone=123-456-7890&Company=Adobe+Inc.&   Country=United+States&PreferredContactMethod=Email&SubscribeToNewsletter=true'
  ```

  Par exemple,

  ```Shell
  curl -s -i -X POST \
    -d 'Email=kent%40wknd.com&Name=clark&Subject=Regarding+Product+Inquiry&   Message=I+have+some+questions+about+your+products.&Phone=123-456-7890& Company=Adobe+Inc.&Country=United+States&PreferredContactMethod=Email&   SubscribeToNewsletter=true' \
    https://main--portal--wkndforms.hlx.live/contact-us
  ```

Vous pouvez ensuite personnaliser le message de remerciement, [configurer une page de remerciement](/help/edge/docs/forms/thank-you-page-form.md), ou [redirections de jeux](/help/edge/docs/forms/thank-you-page-form.md).

