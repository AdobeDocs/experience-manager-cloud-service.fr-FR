---
title: De feuilles de calcul à Forms - Gestion des validations des champs de bloc de formulaire
description: Créez des formulaires puissants plus rapidement à l’aide des feuilles de calcul et des champs de bloc de formulaire. Ce guide vous aide à créer des validations personnalisées pour les champs Bloc Forms d’EDS.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 0604838311bb9ab195789fad755b0910e09519fd
workflow-type: tm+mt
source-wordcount: '964'
ht-degree: 1%

---


# Activation de votre formulaire pour envoyer des données

Après avoir créé et prévisualisé le formulaire, activez la feuille correspondante pour accepter les données. Pour commencer à accepter des données, configurez votre feuille de calcul afin d’inclure les en-têtes qui correspondent aux données que vous avez l’intention de collecter. Tous les en-têtes ajoutés à la feuille &#39;shared-default&#39; doivent également être présents dans la feuille &#39;incoming&#39; sous un tableau.

L’exemple suivant affiche les champs d’un formulaire &quot;contact-us&quot; :

![Champs d’un formulaire de contact](/help/edge/assets/contact-us-form-excel-sheet-fields.png)


Une fois cette configuration terminée, votre formulaire devient prêt à accepter les envois. Vous pouvez utiliser l’une des méthodes suivantes pour permettre à votre feuille de calcul d’accepter les données :

* [Configuration manuelle d’une feuille de calcul pour accepter les données](#manually-configure-a-spreadsheet-to-receive-data)

* [Utilisation des API d’administration pour permettre à une feuille de calcul d’accepter des données](#use-admin-apis-to-enable-a-spreadsheet-to-receive-data-use-admin-apis-to-enable-a-spreadsheet-to-recieve-data)

## Configuration manuelle d’une feuille de calcul pour accepter les données

Pour configurer manuellement une feuille de calcul afin d’accepter les données :


1. Ouvrez le classeur que vous avez créé et remplacez le nom de la feuille par défaut par &quot;entrant&quot;.

   >[!WARNING]
   >
   > Si la feuille &quot;entrante&quot; n’existe pas, AEM n’enverra aucune donnée à ce classeur.

1. Préparez la feuille en ajoutant des en-têtes correspondant aux données que vous insérez. L’exemple suivant affiche les champs d’un formulaire &quot;contact-us&quot; :

   ![Champs d’un formulaire de contact](/help/edge/assets/contact-us-form-excel-sheet-fields.png)

1. Aperçu de la feuille dans le sidekick.

   >[!NOTE]
   >
   >Même si vous avez déjà prévisualisé la feuille, vous devez la prévisualiser à nouveau après avoir créé la feuille &quot;entrante&quot; pour la première fois.


## Utilisation des API d’administration pour permettre à une feuille de calcul d’accepter des données

Vous pouvez lancer une requête de POST vers l’itinéraire du formulaire au sein du service d’administration AEM. Lors de la réception des données du corps du POST, le service d’administration les analyse et génère de manière autonome les en-têtes, les tableaux et les feuilles essentiels nécessaires à l’ingestion des données, optimisant ainsi les fonctionnalités du service Forms.

Pour utiliser les API d’administration afin d’activer une feuille de calcul pour accepter des données :


1. Ouvrez le classeur que vous avez créé et remplacez le nom de la feuille par défaut par &quot;entrant&quot;.

   >[!WARNING]
   >
   > Si la feuille &quot;entrante&quot; n’existe pas, AEM n’enverra aucune donnée à ce classeur.

1. Aperçu de la feuille dans le sidekick.

   >[!NOTE]
   >
   >Même si vous avez déjà prévisualisé la feuille, vous devez la prévisualiser à nouveau après avoir créé la feuille &quot;entrante&quot; pour la première fois.

1. Préparez la feuille en ajoutant des en-têtes correspondant aux données que vous insérez.

   Pour ce faire, envoyez une demande de POST à l’itinéraire du formulaire dans le service d’administration AEM. Le service d’administration examine les données du corps du POST et génère les en-têtes, tableaux et feuilles appropriés nécessaires pour ingérer efficacement les données et tirer le meilleur parti du service Forms.

   Pour comprendre comment formater la requête du POST pour configurer votre feuille, reportez-vous à la section [Documentation de l’API d’administration](https://www.hlx.live/docs/admin.html#tag/form). Examinez également l’exemple fourni ci-dessous :

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

   La requête de POST mentionnée précédemment fournit des données d’exemple, y compris les champs de formulaire et leurs valeurs d’exemple respectives. Ces données sont utilisées par le service d’administration pour configurer le formulaire.

   Lors de l’envoi de la demande de POST au service d’administration, vous constatez les modifications suivantes dans votre classeur :

* Une nouvelle feuille nommée &quot;shared-default&quot; est ajoutée à votre classeur Excel ou feuille Google. Les données présentes dans la feuille &quot;shared-default&quot; sont récupérées lors d’une demande de GET à la feuille. Cette feuille constitue un emplacement optimal pour utiliser des formules de feuille de calcul afin de résumer les données entrantes, ce qui les rend propices à la consommation dans d’autres contextes.

  Jamais les feuilles &quot;shared-default&quot; ne devraient contenir d’informations d’identification personnelle ou de données sensibles que vous ne connaissez pas lorsque vous êtes connecté au public.

* Une feuille nommée &quot;Slack&quot; est ajoutée à votre classeur Excel ou à votre feuille de calcul Google. Dans cette feuille, vous pouvez configurer des notifications automatiques pour un canal de Slack désigné chaque fois que de nouvelles données sont ingérées dans votre feuille de calcul. Actuellement, AEM prend en charge les notifications exclusivement destinées à l’organisation de Slack d’ingénierie AEM et à l’Adobe d’assistance aux entreprises.

   1. Pour configurer les notifications de Slack, saisissez l’&quot;TeamId&quot; de l’espace de travail du Slack et le &quot;nom du canal&quot; ou &quot;ID&quot;. Vous pouvez également demander au slack-bot (avec la commande debug) pour &quot;TeamId&quot; et &quot;channel ID&quot;. Il est préférable d’utiliser &quot;l’identifiant du canal&quot; plutôt que le &quot;nom du canal&quot;, car cela permet de survivre aux renommes du canal.

      >[!NOTE]
      >
      > Les formulaires plus anciens ne contenaient pas la colonne &quot;TeamId&quot;. L’ID d’équipe a été inclus dans la colonne du canal, séparé par un &quot;#&quot; ou &quot;/&quot;.

   1. Saisissez le titre de votre choix et sous les champs , saisissez le nom des champs que vous souhaitez voir dans la notification du Slack. Chaque en-tête doit être séparé par une virgule (par exemple, nom, email).

La feuille est maintenant configurée pour recevoir des données, vous pouvez [aperçu du formulaire à l’aide du bloc de formulaires](/help/edge/docs/forms/create-forms.md#preview-the-form-using-your-edge-delivery-service-eds-page) ou [utilisation de requêtes de POST](#use-admin-apis-to-send-data-to-your-sheet) pour commencer à envoyer des données à la feuille.



## Envoi de données à votre feuille {#send-data-to-your-sheet}

Une fois la feuille définie pour recevoir des données, vous pouvez [aperçu du formulaire à l’aide du bloc de formulaires](/help/edge/docs/forms/create-forms.md#preview-the-form-using-your-edge-delivery-service-eds-page) ou [Utilisation des API d’administration](#use-admin-apis-to-send-data-to-your-sheet) pour commencer à envoyer des données à la feuille.

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

## En savoir plus

* [Créer et prévisualiser un formulaire](/help/edge/docs/forms/create-forms.md)
* [Activer le formulaire pour envoyer des données](/help/edge/docs/forms/submit-forms.md)
* [Publier un formulaire sur la page de sites](/help/edge/docs/forms/publish-eds-forms.md)
* [Ajouter des validations à des champs de formulaire](/help/edge/docs/forms/validate-forms.md)
* [Modifier les thèmes et le style du formulaire](/help/edge/docs/forms/style-theme-forms.md)