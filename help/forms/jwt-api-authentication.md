---
title: Comment configurer l’authentification JWT (JSON Web Token) ?
description: Découvrez comment configurer l’authentification JWT (JSON Web Token) pour Adobe Experience Manager Forms as a Cloud Service
role: Admin, Developer, User
feature: Adaptive Forms, APIs & Integrations
hide: true
hidefromtoc: true
index: false
source-git-commit: e2f57a32fcc098a2331ad74540a3d48832c2b3c3
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 5%

---


# Authentification de serveur à serveur JWT (JSON Web Token)

L’authentification serveur à serveur JWT dans AEM Forms, en particulier pour les intégrations côté serveur avec AEM as a Cloud Service, implique un processus spécifique pour interagir en toute sécurité avec les services AEM. L’authentification serveur à serveur JWT est prise en charge par AEM Developer Console.

## Conditions préalables

Avant de commencer, vérifiez que les conditions préalables suivantes sont remplies :

* Assurez-vous d’avoir accès au [Cloud Manager Adobe](https://experience.adobe.com/#/@formsinternal01/cloud-manager/landing.html) spécifique à l’environnement que vous utilisez.
* Attribuez le rôle [Administrateur système ou Développeur pour accéder à Adobe Cloud Manager](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/requirements/access-rights).

## Comment générer un jeton d’accès à l’aide des informations d’identification JWT ?

Suivez les étapes ci-dessous qui vous montrent comment générer un jeton d’accès à partir des informations d’identification JWT.

1. **Adobe Cloud Manager**

   1. Connectez-vous à votre compte [Cloud Manager](https://experience.adobe.com/#/@formsinternal01/cloud-manager/landing.html).
   2. Sur le programme sélectionné, cliquez sur **[!UICONTROL Aperçu du programme]**.

      ![Compte Cloud Manager](/help/forms/assets/jwt-cloud-manager-landing.png)

   3. Dans votre programme, cliquez sur le menu à trois points et sélectionnez **[!UICONTROL Developer Console]**.

      ![Developer Console](/help/forms/assets/jwt-developer-console.png)

2. **AEM Developer Console.**
   1. Connexion à AEM Developer Console
   2. Cliquez sur **[!UICONTROL Intégrations]** dans la barre de menus supérieure.

      ![Intégrations](/help/forms/assets/jwt-integrations.png)

   3. Cliquez sur l’option **[!UICONTROL Créer un compte technique]**.

      ![Créer un compte technique](/help/forms/assets/jwt-creae-new-tech-account.png)

   Une fois que vous avez cliqué sur Créer un compte technique, les informations requises pour générer un jeton d’accès tel que l’identifiant client et le secret client, ainsi que d’autres informations de compte techniques, y compris la clé privée, la clé publique et la date d’expiration, sont générées.

   ![&#x200B; Informations d’identification JWT &#x200B;](/help/forms/assets/jwt-credentials.png)


3. **Générer et enregistrer des informations d’identification**

   1. Enregistrer les informations d’identification d’API

      ```text
      API Credentials:
      ================
      Client ID: <your_client_id>
      Client Secret: <your_client_secret>
      Technical Account ID: <tech_account_id>
      Organization ID: <org_id>
      Scopes: AdobeID,openid,read_organizations
      ```

4. **Génération de jeton d’accès**

   Générez des jetons par programmation à l’aide de la commande cURL :

   **Informations d’identification requises :**

   * ID client
   * Secret client
   * Portées (généralement : `openid, AdobeID, read_organizations, additional_info.projectedProductContext, read_pc.dma_aem_cloud, aem.document`)

   **Point d’entrée du jeton :**

   ```
   https://ims-na1.adobelogin.com/ims/token/v3
   ```

   **Exemple de requête (cURL) :**

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


>[!NOTE]
>
> Pour en savoir plus sur les informations d’identification de service et sur la génération d’un jeton d’accès à l’aide de l’API Adobe IMS, [cliquez ici](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials).

Vous pouvez désormais utiliser le jeton d’accès généré pour effectuer un appel API pour les environnements de développement, d’évaluation ou de production.

## Articles connexes

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


