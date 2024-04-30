---
title: Créer un formulaire à l’aide de la création basée sur les documents pour le service de diffusion AEM Forms Edge
description: Créez rapidement des formulaires parfaits. ⚡Création basée sur des documents + AEM Forms Edge Delivery = vitesse époustouflante et formulaires compatibles avec l’optimisation du moteur de recherche pour des utilisateurs et utilisatrices plus heureux et plus d’efficacité des recherches.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: ht
source-wordcount: '889'
ht-degree: 100%

---


# Créer un formulaire à l’aide de la création basée sur les documents pour le service de diffusion AEM Forms Edge

À l’ère numérique actuelle, la création de formulaires conviviaux est essentielle pour toute entreprise. La création basée sur des document d’AEM Forms Edge Delivery permet de créer des formulaires à l’aide d’outils familiers comme Microsoft Word ou Google Docs. Ces formulaires envoient des données directement vers un fichier Microsoft Excel ou Google Sheets, ce qui vous permet d’utiliser l’écosystème dynamique et les API robustes de Google Sheets, Microsoft Excel et Microsoft SharePoint afin de traiter facilement les données envoyées ou de démarrer un workflow d’entreprise existant.

Ce guide vous emmène tout au long des étapes suivantes :

* Préparation de votre feuille de calcul : découvrez comment configurer un fichier Excel ou Google Sheets pour la collecte de données et y ajouter des champs de formulaire.
* Envoi de données à votre feuille : apprenez à envoyer des données à votre feuille à l’aide de requêtes POST.
* Publication du formulaire : intégrez le formulaire à votre page AEM Sites ou publiez-le en tant que page autonome.

Que vous soyez novice ou que vous utilisiez ces outils de manière professionnelle, ce guide vous permet de créer de beaux formulaires fonctionnels qui plaisent aux utilisateurs et utilisatrices. Découvrons ensemble la création efficace de formulaires : voyons les détails dès maintenant !

## Avant de commencer

`WIP`

## Préparer votre feuille de calcul pour recevoir des données

1. Créez un fichier Microsoft Excel ou Google Sheet, n’importe où sous votre répertoire de projet AEM Edge Delivery sur Microsoft OneDrive ou Google Drive. Ce document utilise une feuille Google nommée `contact-us.xlsx`, située à la racine d’un projet Adobe Experience Manager (AEM).

1. Assurez-vous que l’utilisateur ou l’utilisatrice AEM (par exemple helix@adobe.com) configuré pour votre projet dispose d’autorisations de modification pour la feuille.

1. Ouvrez le classeur que vous avez créé et remplacez le nom de la feuille par défaut par « entrant ».

   >[!NOTE]
   >
   > Si la feuille « entrant » n’existe pas, AEM n’enverra aucune donnée à ce classeur.

1. Prévisualisez la feuille dans le sidekick.

   >[!NOTE]
   >
   >Même si vous avez déjà prévisualisé la feuille, vous devez la prévisualiser à nouveau après la première création de la feuille « entrant ».

1. Préparez la feuille en ajoutant des en-têtes correspondant aux données que vous insérez. L’exemple suivant affiche les champs d’un formulaire « contact-us » :

   ![Champs d’un formulaire contact-us](/help/edge/assets/contact-us-form-excel-sheet-fields.png)

   Vous pouvez effectuer cette opération manuellement ou à l’aide d’une requête POST sur l’itinéraire du formulaire dans le service d’administration AEM. Le service d’administration examine les données du corps POST et génère les en-têtes, tableaux et feuilles appropriés nécessaires à l’ingestion efficace des données et à la mise à profit du service de formulaires.

   Pour comprendre comment mettre en forme la requête POST afin de configurer votre feuille, reportez-vous à la [Documentation de l’API d’administration](https://www.hlx.live/docs/admin.html#tag/form). Vous pouvez également consulter l’exemple ci-dessous :

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
   
   {"rowCount":2,"columns":["Email","Name","Subject","Message","Phone","Company","Country","PreferredContactMethod","SubscribeToNewsletter"]}%
   ```

   Vous pouvez utiliser des outils tels que curl ou Postman pour exécuter cette requête POST, comme illustré ci-dessous :

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

La requête POST mentionnée ci-dessus fournit des données d’exemple, y compris les champs de formulaire et leurs valeurs d’exemple respectives. Ces données sont utilisées par le service d’administration pour configurer le formulaire.

Bien que le service d’administration recommande de configurer votre feuille, si vous préférez créer les en-têtes manuellement, reportez-vous au document intitulé [Configuration manuelle de feuille de formulaire](https://www.hlx.live/docs/manual-forms-sheet-setup).

Lors de l’envoi de la requête POST au service d’administration, vous constaterez les modifications suivantes dans votre classeur :

* Une nouvelle feuille nommée « shared-default » est ajoutée à votre classeur Excel ou à votre feuille Google Sheets. Les données présentes dans la feuille « shared-default » sont récupérées lors d’une requête GET à la feuille. Cette feuille de calcul constitue un emplacement optimal pour utiliser des formules de feuille de calcul afin de résumer les données entrantes, ce qui permet de les utiliser dans d’autres contextes.

  Les feuilles « shared-default » ne doivent en aucun cas contenir d’informations personnelles identifiables ou de données sensibles que vous ne souhaitez pas rendre accessibles au public.

* Une feuille nommée « slack » est ajoutée à votre classeur Excel ou à votre feuille Google Sheets. Dans cette feuille, vous pouvez configurer des notifications automatiques pour un canal Slack désigné chaque fois que de nouvelles données sont ingérées dans votre feuille de calcul. Actuellement, AEM prend en charge les notifications exclusivement destinées à l’organisation Slack de l’équipe d’ingénierie AEM et à l’organisation de l’assistance aux entreprises d’Adobe.

   1. Pour configurer les notifications Slack, saisissez l’« identifiant d’équipe » de l’espace de travail Slack et le « nom de canal » ou l’« identifiant ». Vous pouvez également demander au Slackbot (avec la commande debug) l’« identifiant d’équipe » et l’« identifiant du canal ». Il est préférable d’utiliser l’« identifiant du canal » plutôt que le « nom du canal », car il n’est pas modifié lorsque le canal est renommé.

      >[!NOTE]
      >
      > Les formulaires plus anciens ne contenaient pas la colonne « identifiant d’équipe ». L’« identifiant d’équipe » a été inclus dans la colonne du canal, séparé par « # » ou « / ».

   1. Saisissez le titre de votre choix et, sous les champs, saisissez le nom des champs que vous souhaitez voir dans la notification Slack. Chaque en-tête doit être séparé par une virgule (par exemple, nom, adresse e-mail).

La feuille est maintenant configurée pour recevoir des données et vous pouvez lui envoyer des requêtes POST directement à l’aide de hlx.page, hlx.live ou de votre domaine de production.


## Envoyer des données à votre feuille {#send-data-to-your-sheet}

Une fois que la feuille est configurée pour recevoir des données, vous pouvez lui envoyer des requêtes POST directement à l’aide de hlx.page, hlx.live ou de votre domaine de production, pour envoyer des données.

```JSON
POST https://branch–repo–owner.hlx.(page|live)/email-form
POST https://my-domain.com/email-form
```

>[!NOTE]
>
> L’URL ne doit pas avoir l’extension .json. Vous devez publier la feuille pour que les opérations POST fonctionnent sur le domaine .live ou sur le domaine de production.

### Formater des données pour EDS Forms

Il existe plusieurs manières de formater les données de formulaire dans le corps POST.

* Tableau de paires nom:valeur :

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

  par exemple,

  ```JSON
      curl -s -i -X POST 'https://main--portal--wkndforms.hlx.page/contact-us' \
          --header 'Content-Type: application/json' \
          --data '{
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
          }'
  
* Objet avec paires clé:valeur

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

* `x-www-form-urlencoded` body (l’en-tête `content-type` doit être défini sur `application/x-www-form-urlencoded`)
&#39;firstname=bruce&amp;lastname=banner&amp;email=bruce%40example.com&#39;



