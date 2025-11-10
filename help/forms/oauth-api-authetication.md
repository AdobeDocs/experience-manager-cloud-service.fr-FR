---
title: Comment configurer l’authentification de serveur à serveur OAuth ?
description: Découvrez comment configurer l’authentification de serveur à serveur OAuth pour Adobe Experience Manager Forms as a Cloud Service
role: Admin, Developer, User
feature: Adaptive Forms, APIs & Integrations
hide: true
hidefromToC: true
index: false
source-git-commit: 69704ca8de41c655b59ce6652a4a43b788ba75ec
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 3%

---


# Authentification de serveur à serveur OAuth - Recommandé

L’authentification de serveur à serveur OAuth permet un accès sécurisé par jeton aux API de communication d’AEM Forms sans nécessiter d’interaction de l’utilisateur. Cette méthode est idéale pour les systèmes automatisés, les services principaux et les intégrations qui doivent s’authentifier par programmation.

## Conditions préalables

Avant de commencer, vérifiez que les conditions préalables suivantes sont remplies :

* Assurez-vous d’avoir accès au [Adobe Developer Console](https://developer.adobe.com/console) spécifique à l’environnement que vous utilisez.
* Attribuez le rôle d’administrateur système ou de développeur dans le Adobe Admin Console pour activer l’accès au Adobe Developer Console.

## Comment générer un jeton d’accès à l’aide de l’authentification de serveur à serveur OAuth ?

Suivez les étapes ci-dessous qui vous montrent comment générer un jeton d’accès à partir de la console Adobe Developer et effectuer votre premier appel API via l’authentification serveur à serveur OAuth.


1. Accéder à [Adobe Developer Console](https://developer.adobe.com/console)
2. Connexion avec votre Adobe ID

3. Créer un projet ou accéder à votre projet existant

   **Pour créer un projet, procédez comme suit**

   1. Dans la section **Démarrage rapide**, cliquez sur **Créer un projet**
   2. Un nouveau projet est créé avec un nom par défaut

      ![Créer un projet ADC](/help/forms/assets/adc-home.png)

   3. Cliquez sur **Modifier le projet** dans le coin supérieur droit

      ![Modifier projet](/help/forms/assets/adc-edit-project.png)

   4. Fournissez un nom significatif (par exemple, « projet de formulaire »).
   5. Cliquer sur **Enregistrer**

      ![Modifier le nom du projet](/help/forms/assets/adc-edit-projectname.png)


   **Pour accéder à votre projet existant, procédez comme suit**

   1. Cliquez sur **Tous les projets** dans le Adobe Developer Console

      ![Rechercher projets](/help/forms/assets/search-adc-project.png)

   2. Recherchez votre projet et cliquez pour l’ouvrir.

      ![Localisation de projets](/help/forms/assets/locate-adc-project.png)


      >[!NOTE]
      >
      > Vous pouvez ajouter l’API et la méthode d’authentification à votre projet existant en cliquant sur **Ajouter au projet** > **API**\
      > ![Ajouter une API à un projet existant](/help/forms/assets/add-api-existing-project.png)
      > Pour ajouter une API et une méthode d’authentification, procédez comme expliqué ci-dessous pour votre projet existant.

4. Ajoutez différentes API AEM Forms Communications en fonction de vos besoins.

   **A. Pour les API Document Services**

   1. Cliquez sur **Ajouter une API**

      ![Ajouter une api](/help/forms/assets/adc-add-api.png)

   2. Sélectionnez **API de communication Forms**
      1. Dans la boîte de dialogue _Ajouter une API_, filtrez par **Experience Cloud**
      2. Sélectionnez **« API de communication Forms »**

         ![Ajouter l’API de communication Forms](/help/forms/assets/adc-add-forms-api.png)


   3. Sélectionnez la méthode d’authentification **OAuth de serveur à serveur**

      ![Sélectionner la méthode d’authentification](/help/forms/assets/adc-add-authentication-method.png)


   **B. Pour les API d’exécution de Forms adaptatif**

   1. **Cliquez sur Ajouter une API**
Dans votre projet, cliquez sur le bouton **Ajouter une API**

      ![Ajouter une api](/help/forms/assets/adc-add-api.png)

   2. **Sélectionnez l’API de diffusion et d’exécution AEM Forms**
      1. Dans la boîte de dialogue _Ajouter une API_, filtrez par **Experience Cloud**
      2. Sélectionnez **« API de diffusion et d’exécution AEM Forms »**
      3. Cliquer sur **Suivant**

   3. **Méthode d’authentification**
Sélectionnez la méthode d’authentification **OAuth de serveur à serveur**.


      ![Sélectionner la méthode d’authentification](/help/forms/assets/adc-add-authentication-method.png)

5. **Ajouter un profil de produit** :

   1. Sélectionnez le **profil de produit** approprié en fonction du niveau d’accès requis :

      | Type d’accès | Profil de produit |
      |------------------|----------------------|
      | Accès en lecture seule | `AEM Users - author - Program XXX - Environment XXX` |
      | Accès en lecture/écriture | `AEM Assets Collaborator Users - author - Program XXX - Environment XXX` |
      | Accès administratif complet | `AEM Administrators - author - Program XXX - Environment XXX` |

   2. Sélectionnez le **profil de produit** qui correspond à votre URL de service de création (`https://author-pXXXXX-eYYYYY.adobeaemcloud.com`). Par exemple : sélectionnez `https://author-pXXXXX-eYYYYY.adobeaemcloud.com`.

   3. Cliquez sur **Save configured API** (Enregistrer l’API configurée). L’API et le profil de produit sont ajoutés au projet

      ![Sélectionner la configuration du projet](/help/forms/assets/adc-add-product-profile.png)

6. Générer et enregistrer des informations d’identification

   1. Accédez à votre projet dans Adobe Developer Console
   2. Cliquez sur les informations d’identification **OAuth de serveur à serveur**
   3. Consultez la section **Informations d’identification**

      ![Afficher les informations d’identification](/help/forms/assets/adc-view-credential.png)

   4. Enregistrer les informations d’identification d’API

      ```text
      API Credentials:
      ================
      Client ID: <your_client_id>
      Client Secret: <your_client_secret>
      Technical Account ID: <tech_account_id>
      Organization ID: <org_id>
      Scopes: AdobeID,openid,read_organizations
      ```

7. Génération de jeton d’accès

   **A. Pour les tests**

   Générez manuellement les jetons d’accès dans Adobe Developer Console :

   1. **Accédez à votre projet**
      1. Dans Adobe Developer Console, ouvrez votre projet
      2. Cliquez sur **OAuth de serveur à serveur**

   2. **Générer un jeton d’accès**
      1. Cliquez sur le bouton **Générer un jeton d’accès »** dans la section API de votre projet
      2. Copier le jeton d’accès généré

      ![&#x200B; Générer un jeton d’accès &#x200B;](/help/forms/assets/adc-access-token.png)

      >[!NOTE]
      >
      > Le jeton d’accès est valide pendant **24 heures uniquement**

   **B. Pour la production**

   Générez des jetons par programmation à l’aide de l’API Adobe IMS :

   **Informations d’identification requises :**

   * ID client
   * Secret client
   * Portées (généralement : `openid, AdobeID, read_organizations, additional_info.projectedProductContext, read_pc.dma_aem_cloud, aem.document`)

   **Point d’entrée du jeton :**

   ```
   https://ims-na1.adobelogin.com/ims/token/v3
   ```

   **Exemple de requête (curl) :**

   ```bash
   curl -X POST 'https://ims-na1.adobelogin.com/ims/token/v3' \
   -H 'Content-Type: application/x-www-form-urlencoded' \
   -d 'grant_type=client_credentials' \
   -d 'client_id=<YOUR_CLIENT_ID>' \
   -d 'client_secret=<YOUR_CLIENT_SECRET>' \
   -d 'scope=AdobeID,openid,read_organizations'
   ```

   **Réponse:**

   ```json
   {
   "access_token": "eyJhbGciOiJSUz...",
   "token_type": "bearer",
   "expires_in": 86399
   }
   ```

Vous pouvez désormais utiliser le jeton d’accès généré pour effectuer un appel API pour les environnements de développement, d’évaluation ou de production.

>[!NOTE]
>
> Pour en savoir plus sur l’implémentation serveur à serveur d’OAuth afin de générer un jeton d’accès et d’effectuer des appels API, [cliquez ici](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation).

## Étapes suivantes

Découvrez comment définir un environnement pour les API de communication Forms synchrones (à la demande) et asynchrones (par lots) :

<!-- START CARDS HTML - DO NOT MODIFY BY HAND -->
<div class="columns">
    <!-- Synchronous APIs Card -->
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="AEM Forms Communications APIs - Synchronous">
        <div class="card" style="height: 100%; display: flex; flex-direction: column;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md" title="API synchrones" target="_self" rel="referrer">
                        <img class="is-bordered-r-small" src="/help/forms/assets/sync-api.png" alt="API synchrones"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md" target="_self" rel="referrer" title="API AEM Forms Communications - Synchrones">API AEM Forms Communications - Synchrones</a>
                    </p>
                    <p class="is-size-6">Découvrez comment configurer un environnement pour les API de communications Forms synchrones (à la demande) qui génèrent ou traitent des documents instantanément. </p>
                </div>
                <a href="/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md" target="_self" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
<span class="spectrum-Button-label has-no-wrap has-text-weight-bold">En savoir plus</span>
</a>
            </div>
        </div>
    </div>
    <!-- Asynchronous APIs Card -->
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="AEM Forms Communications APIs - Asynchronous">
        <div class="card" style="height: 100%; display: flex; flex-direction: column;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="/help/forms/aem-forms-cloud-service-communications-batch-processing.md" title="API AEM Forms Communications - Asynchrones" target="_self" rel="referrer">
                        <img class="is-bordered-r-small" src="/help/forms/assets/async-api.png" alt="API asynchrones"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="/help/forms/aem-forms-cloud-service-communications-batch-processing.md" target="_self" rel="referrer" title="API asynchrones">API AEM Forms Communications - Asynchrones (lot)</a>
                    </p>
                    <p class="is-size-6">Découvrez comment configurer un environnement pour les API de communications Forms asynchrones (par lots) qui génèrent ou traitent plusieurs documents de manière planifiée.</p>
                </div>
                <a href="/help/forms/aem-forms-cloud-service-communications-batch-processing.md" target="_self" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
<span class="spectrum-Button-label has-no-wrap has-text-weight-bold">En savoir plus</span>
</a>
            </div>
        </div>
    </div>
</div>
<!-- END CARDS HTML - DO NOT MODIFY BY HAND -->


