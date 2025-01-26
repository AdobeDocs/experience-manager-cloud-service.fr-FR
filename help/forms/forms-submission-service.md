---
Title: How to use forms submission service for submitting forms?
Description: Learn how to use forms submission service for submitting forms.
Keywords: Use form submission service, Submit form using form submission service
feature: Edge Delivery Services
Role: User, Developer
exl-id: 12b4edba-b7a1-4432-a299-2f59b703d583
source-git-commit: ae31df22c723c58addd13485259e92abb4d4ad54
workflow-type: tm+mt
source-wordcount: '835'
ht-degree: 1%

---

# Service de soumission Forms avec Edge Delivery Services Forms

Le service d’envoi Forms vous permet de stocker les données des envois de formulaire dans n’importe quelle feuille de calcul, telle que OneDrive, SharePoint ou Google Sheets, ce qui vous permet d’accéder facilement aux données de formulaire et de les gérer sur votre plateforme de feuille de calcul préférée.

![Service d’envoi Forms](/help/forms/assets/form-submission-service.png)

## Avantages de l’utilisation du service Forms Submission

L’utilisation du service d’envoi Forms avec des feuilles de calcul présente les avantages suivants :

* **Intégration directe** : vous pouvez configurer des formulaires pour envoyer directement des données à une feuille de calcul spécifiée, ce qui élimine la nécessité d’un transfert manuel de données.
* **Structure des données** : lors de la configuration de l’envoi, vous pouvez mapper les champs de formulaire aux colonnes de feuille de calcul correspondantes pour le stockage de données organisé.
* **Contrôle d’accès** : vous pouvez tirer parti des autorisations existantes pour contrôler qui peut accéder aux données de formulaire envoyées et les modifier, en fonction du service de feuille de calcul choisi.

## Prérequis

Vous trouverez ci-dessous les conditions préalables requises pour utiliser le service Forms Submission :

* Assurez-vous que votre projet AEM dispose du dernier bloc de formulaire adaptatif.
* Assurez-vous que votre référentiel Git est ajouté à la place sur la liste autorisée pour utiliser le service d’envoi de Forms. Veuillez [mailto:aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) avec le nom de votre organisation GitHub et le nom du référentiel pour les ajouter à la liste autorisée pour utiliser le service d’envoi de Forms.

## Configuration du service d’envoi Forms

Créez un projet AEM configuré avec le bloc de Forms adaptatif. Reportez-vous à l’article [Prise en main - Tutoriel pour les développeurs](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/tutorial) pour savoir comment créer un projet AEM. Mettez à jour le fichier `fstab.yaml` dans votre projet. Remplacez la référence existante par le chemin d’accès au dossier que vous avez partagé avec le `forms@adobe.com` .

Vous pouvez [configurer manuellement le service de soumission Forms](#configuring-the-forms-submission-service-manually) ou [configurer le service de soumission Forms à l’aide de l’API](#configuring-the-forms-submission-service-using-api).

### Configuration manuelle du service d’envoi Forms

![Processus pour le service d’envoi de formulaires](/help/forms/assets/forms-submission-service-workflow.png)

#### 1. Créer un formulaire à l’aide d’une définition de formulaire

Créez un formulaire à l’aide de Google Sheets ou de Microsoft Excel. Pour savoir comment créer un formulaire à l’aide d’une définition de formulaire dans Microsoft Excel ou Google Sheets, [cliquez ici](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/create-forms).

La capture d’écran ci-dessous affiche la définition du formulaire utilisée pour créer le formulaire :

![Définition du formulaire](/help/forms/assets/form-submission-definition.png)

#### 2. Activez la feuille de calcul pour accepter les données.

Une fois que vous avez créé et prévisualisé le formulaire, activez la feuille de calcul correspondante pour commencer à recevoir des données. ajoutez une nouvelle feuille en tant que `incoming`. Vous pouvez [activer manuellement la feuille de calcul pour accepter les données](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/submit-forms#manually-enable-the-spreadsheet-to-accept-data).

![Feuille entrante](/help/forms/assets/form-submission-incoming-sheet.png)

>[!WARNING]
>
> Si la feuille de `incoming` n’existe pas, AEM n’envoie aucune donnée à ce classeur.

#### 3. Partager la feuille de calcul et générer un lien.

Pour partager la feuille de calcul avec le compte `forms@adobe.com` et générer un lien, procédez comme suit :

1. Dans Excel ou Google Sheets, cliquez sur le bouton **Partager** dans le coin supérieur droit.
1. Ajoutez le compte `forms@adobe.com` et
Cliquez sur l’icône représentant un œil, sélectionnez l’accès **Modifier**, puis cliquez sur **Envoyer**.

   ![Partager la feuille entrante](/help/forms/assets/form-submission-share-incoming.png)

1. Pour copier le lien de la feuille de calcul, cliquez sur le bouton **Partager** dans le coin supérieur droit, puis sélectionnez **Copier le lien**.

   ![Copier le lien de la feuille entrante](/help/forms/assets/form-submission-copy-link.png)

#### 4. Liez la feuille de calcul dans la définition du formulaire

Pour configurer le service d’envoi de Forms avec Google Sheets ou Microsoft Excel, procédez comme suit :

1. Ouvrez la feuille de calcul contenant la définition du formulaire.
1. Dans la ligne correspondant au champ **Envoyer**, collez le lien de la feuille de calcul copiée dans la colonne **Action**.

   ![Lier une feuille de calcul](/help/forms/assets/form-submission-sheet-linking.png)

1. Prévisualisez et publiez la feuille à l’aide de l’AEM Sidekick [](https://www.aem.live/docs/sidekick) avec le service d’envoi de formulaire mis à jour.

>[!NOTE]
>
> Vous pouvez vous reporter à la [feuille de calcul](/help/forms/assets/spreadsheet.xlsx) pour utiliser le service Forms Submission.

### Configuration du service d’envoi Forms à l’aide de l’API

Vous pouvez également envoyer une demande de **POST** au formulaire pour mettre à jour la feuille de `incoming` avec des données.

>[!NOTE]
>
> * Si la feuille de `incoming` n’existe pas, AEM n’envoie aucune donnée à ce classeur.
> * Partagez la feuille de `incoming` avec le `forms@adobe.com` Adobe Experience Manager et accordez l’accès de modification.
> * Prévisualisez et publiez la feuille de `incoming` dans le sidekick.

Pour savoir comment formater la requête du POST afin de configurer votre feuille, reportez-vous à la documentation [API](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/references/aem-forms-submission-service/). Vous pouvez consulter l’exemple ci-dessous :

Vous pouvez utiliser des outils tels que curl ou Postman pour exécuter cette requête de POST, comme illustré ci-dessous.

* **Utilisation de Postman** :

Par exemple, envoyez la requête ci-dessous dans Postman après avoir remplacé :
* `{id}` avec votre ID de formulaire
* `site or repository` avec le nom de votre site ou référentiel GitHub
* `organization` avec votre nom d’utilisateur GitHub

  ```json
  POST 'https://forms.adobe.com/adobe/forms/af/submit/{id}' \
  --header 'Content-Type: application/json' \
  --header 'x-adobe-routing: tier=live,bucket=main--[site/repository]--[organization]' \
  --data '{
      "data": {
          "startDate": "2025-01-10",
          "endDate": "2025-01-25",
          "destination": "Australia",
          "class": "First Class",
          "budget": "2000",
          "amount": "1000000",
          "name": "Mary",
          "age": "35",
          "subscribe": null,
          "email": "mary@gmail.com"
              }
          }'
  ```

Cliquer sur le bouton **Envoyer** dans Postman renvoie une réponse `201 Created` et la feuille de `incoming` est mise à jour avec les données envoyées.

![écran postman](/help/forms/assets/postman-api.png)

* **Utilisation de la commande Curl** :

Par exemple, exécutez la commande ci-dessous dans le terminal ou à l’invite de commande après avoir remplacé :
* `{id}` avec votre ID de formulaire
* `site or repository` avec le nom de votre site ou référentiel GitHub
* `organization` avec votre nom d’utilisateur GitHub


>[!BEGINTABS]

>[!TAB Pour macOS]

    « json
    curl -X POST « https://forms.adobe.com/adobe/forms/af/submit/{id} » \
    —header « Content-Type : application/json » \
    —header « x-adobe-routing: tier=live,bucket=main—[site/repository]—[organization] » \
    —data &#39;{
    « data »: {
    « startDate »: « 2025-01-10 »,
    « endDate »: « 2025-01-25 »,
    « destination »: « Australia »,
    « class »: « First Class »,
    « budget »: « 2000 »,
    « amount »: « 1000000 »,
    « name »: « Joe »,
    « age »: « 35 »,
    « subscribe »: null,
    « email »: « mary@gmail.com »
    }
    }&#39;
    
     »

>[!TAB Pour Windows OS]

    « json
    
    curl -X POST « https://forms.adobe.com/adobe/forms/af/submit/{id} » ^
    —header « Content-Type : application/json » ^
    —header « x-adobe-routing: tier=live,bucket=main—[site/repository]—[organization] » ^
    —data « {\« data\ »: {\« startDate\ »: \« 2025-01-10\ », \« endDate\ »: \« 2025-01-25\ », \« destination\ »: \« Australia\ », \« class\ »: \« First Class\ », \« budget\ »: \« 2000\ », \« amount\ »: \ »1000000\ », \« name\ »: \« Joe\ », \« age\ »: \« 35\ », \« subscribe\ »: null, \« email\ »: \ »mary@gmail.com\« }} »
    
     »

>[!ENDTABS]

La requête de POST mentionnée ci-dessus met à jour la feuille de `incoming` avec la réponse ci-dessous :

```json
    < HTTP/1.1 201 Created
    < Connection: keep-alive
    < Content-Length: 0
    < X-Request-Id: 02a53839-2340-56a5-b238-67c23ec28f9f
    < X-Message-Id: 42ecb4dd-b63a-4674-8f1a-05a4a5b0372c
    < Accept-Ranges: bytes
    < Date: Fri, 10 Jan 2025 13:06:10 GMT
    < Via: 1.1 varnish
    < Access-Control-Allow-Origin: *
    < X-Served-By: cache-del21750-DEL
    < X-Cache: MISS
    < X-Cache-Hits: 0
    < X-Timer: S1736514370.704084,VS0,VE1234
```

L’écran ci-dessous affiche la capture d’écran de la feuille de `incoming` mise à jour par l’envoi de données à l’aide de l’API :

![feuille mise à jour](/help/forms/assets/updated-sheet.png)

## Voir également

{{see-more-forms-eds}}
