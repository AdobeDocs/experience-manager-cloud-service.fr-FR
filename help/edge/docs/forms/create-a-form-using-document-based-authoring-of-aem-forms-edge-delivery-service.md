---
title: Création d’un formulaire à l’aide de la création de documents pour le service de diffusion AEM Forms Edge
description: Créez rapidement des formulaires parfaits. ⚡ AEM Forms Edge Delivery + création documentée = vitesse époustouflante et formulaires compatibles avec l’optimisation pour les moteurs de recherche et les utilisateurs plus heureux.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 20%

---


# Création d’un formulaire à l’aide de la création de documents pour le service de diffusion AEM Forms Edge

À l’ère numérique actuelle, la création de formulaires conviviaux est essentielle pour toute entreprise. La création basée sur des documents d’AEM Forms Edge Delivery vous permet de créer des formulaires à l’aide d’outils familiers tels que Word ou Google Docs. Ces formulaires envoient des données directement à un fichier Microsoft Excel ou Google Sheets, ce qui vous permet d’utiliser un écosystème dynamique et des API robustes de Google Sheets, Microsoft Excel et Microsoft Share pour traiter facilement les données envoyées ou lancer un processus d’entreprise existant.

Ce guide vous guide tout au long des étapes suivantes :

* Préparation de votre feuille de calcul : découvrez comment configurer un fichier Excel ou Google Sheets pour la collecte de données et y ajouter des champs de formulaire.
* Envoyer des données à votre feuille : apprenez à envoyer des données à votre feuille à l’aide de requêtes de POST.
* Publier le formulaire : intégrez le formulaire à votre page AEM Sites ou publiez-le en tant que page autonome.

Que vous soyez novice ou professionnel, ce guide vous permet de créer de belles formes fonctionnelles que les utilisateurs aiment. Déverrouillons la création efficace de formulaires - plongeons maintenant !

## Avant de commencer

`WIP`

## Préparation de votre feuille de calcul pour la réception de données

1. Créez un classeur Microsoft Excel ou une feuille de calcul Google n’importe où sous votre répertoire de projet Edge Delivery AEM sur Microsoft OneDrive ou Google Drive. Ce document utilise une feuille Google nommée `contact-us.xlsx`, situé à la racine d’un projet Adobe Experience Manager (AEM).

1. Assurez-vous que l’utilisateur AEM (par exemple helix@adobe.com) configuré pour votre projet dispose des autorisations de modification pour la feuille.

1. Ouvrez le classeur que vous avez créé et remplacez le nom de la feuille par défaut par &quot;entrant&quot;.

   >[!NOTE]
   >
   > Si la feuille &quot;entrante&quot; n’existe pas, AEM n’enverra aucune donnée à ce classeur.

1. Prévisualisez la feuille dans le sidekick.

   >[!NOTE]
   >
   >Même si vous avez déjà prévisualisé la feuille, vous devez la prévisualiser à nouveau après avoir créé la feuille &quot;entrante&quot; pour la première fois.

1. Préparez la feuille en ajoutant des en-têtes correspondant aux données que vous insérez. L’exemple suivant affiche les champs d’un formulaire &quot;contact-us&quot; :

   ![Champs d’un formulaire contact-us](/help/edge/assets/contact-us-form-excel-sheet-fields.png)

   Vous pouvez effectuer cette opération manuellement ou à l’aide d’une requête de POST sur l’itinéraire du formulaire dans le service d’administration AEM. Le service d’administration examine les données du corps du POST et génère les en-têtes, tableaux et feuilles appropriés nécessaires à l’ingestion efficace des données et à la mise à profit du service Forms.

   Pour comprendre comment mettre en forme la requête POST afin de configurer votre feuille, reportez-vous à la [Documentation de l’API d’administration](https://www.hlx.live/docs/admin.html#tag/form). En outre, consultez l’exemple fourni ci-dessous :

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

La requête de POST mentionnée ci-dessus fournit des données d’exemple, y compris les champs de formulaire et leurs valeurs d’exemple respectives. Ces données sont utilisées par le service d’administration pour configurer le formulaire.

Bien que le service d’administration recommande de configurer votre feuille, si vous préférez créer les en-têtes manuellement, reportez-vous au document intitulé [Configuration manuelle de la feuille Forms](https://www.hlx.live/docs/manual-forms-sheet-setup).

Lors de l’envoi de la demande de POST au service d’administration, vous constaterez les modifications suivantes dans votre classeur :

* Une nouvelle feuille nommée &quot;shared-default&quot; est ajoutée à votre classeur Excel ou feuille Google. Les données présentes dans la feuille &quot;shared-default&quot; sont récupérées lors d’une demande de GET à la feuille. Cette feuille de calcul constitue un emplacement optimal pour utiliser des formules de feuille de calcul afin de résumer les données entrantes, ce qui la rend propre à la consommation dans d’autres contextes.

  En aucun cas la feuille &quot;shared-default&quot; ne doit contenir d’informations d’identification personnelle ou de données sensibles que vous n’êtes pas à l’aise avec l’accessibilité publique.

* Une feuille nommée &quot;slack&quot; est ajoutée à votre classeur Excel ou à votre feuille de calcul Google. Dans cette feuille, vous pouvez configurer des notifications automatiques pour un canal Slack désigné chaque fois que de nouvelles données sont ingérées dans votre feuille de calcul. Actuellement, AEM prend en charge les notifications exclusivement destinées à l’organisation Slack de l’équipe d’ingénierie AEM et à l’organisation de l’assistance aux entreprises d’Adobe.

   1. Pour configurer les notifications de Slack, saisissez l’&quot;TeamId&quot; de l’espace de travail du Slack et le &quot;nom du canal&quot; ou &quot;ID&quot;. Vous pouvez également demander au Slackbot (avec la commande debug) l’« identifiant d’équipe » et l’« identifiant du canal ». Il est préférable d’utiliser l’« identifiant du canal » plutôt que le « nom du canal », car il n’est pas modifié lorsque le canal est renommé.

      >[!NOTE]
      >
      > Les formulaires plus anciens ne contenaient pas la colonne « identifiant d’équipe ». L’« identifiant d’équipe » a été inclus dans la colonne du canal, séparé par « # » ou « / ».

   1. Saisissez le titre de votre choix et sous les champs , saisissez le nom des champs que vous souhaitez voir dans la notification du Slack. Chaque en-tête doit être séparé par une virgule (par exemple, nom, adresse e-mail).

La feuille est maintenant configurée pour recevoir des données et vous pouvez lui envoyer des demandes de POST directement à l’aide de hlx.page, hlx.live ou de votre domaine de production.


## Envoyer des données à votre feuille {#send-data-to-your-sheet}

Une fois que la feuille est configurée pour recevoir des données, vous pouvez lui envoyer des requêtes de POST directement à l’aide de hlx.page, hlx.live ou de votre domaine de production, pour envoyer des données.

```JSON
POST https://branch–repo–owner.hlx.(page|live)/email-form
POST https://my-domain.com/email-form
```

>[!NOTE]
>
> L’URL ne doit pas avoir l’extension .json. Vous devez publier la feuille pour que les opérations du POST fonctionnent sur .live ou sur le domaine de production.

### Formatage des données pour EDS Forms

Il existe plusieurs façons de formater les données de formulaire dans le corps du POST.

* Tableau de paires nom:valeur :

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
  
* Objet avec paires clé-valeur

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

* `x-www-form-urlencoded` body (`content-type` L’en-tête doit être défini sur `application/x-www-form-urlencoded`) &#39;firstname=bruce&amp;lastname=banner&amp;email=bruce%40example.com&#39;



