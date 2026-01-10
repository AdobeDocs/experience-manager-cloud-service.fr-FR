---
title: Comment configurer l’authentification de serveur à serveur OAuth ?
description: Découvrez comment configurer l’authentification de serveur à serveur OAuth pour Adobe Experience Manager Forms as a Cloud Service
role: Admin, Developer, User
feature: Adaptive Forms, APIs & Integrations
hide: true
hidefromtoc: true
index: false
source-git-commit: 6bd2e1698cceaf8fe47e19e0645d0782c916644a
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 4%

---


# Authentification de serveur à serveur OAuth

L’authentification de serveur à serveur OAuth permet un accès sécurisé par jeton aux API de communication d’AEM Forms sans nécessiter d’interaction de l’utilisateur. L’authentification serveur à serveur OAuth est prise en charge par Adobe Developer Console.

## Conditions préalables

Avant de commencer, vérifiez que les conditions préalables suivantes sont remplies :

* Assurez-vous d’avoir [accès au Adobe Developer Console](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/requirements/access-rights) spécifique à l’environnement que vous utilisez.
* [Attribuez le rôle d’administrateur système ou de développeur dans le Adobe Admin Console](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-manager/content/requirements/role-based-permissions) pour activer l’accès au Adobe Developer Console.

## Comment générer un jeton d’accès à l’aide de l’authentification de serveur à serveur OAuth ?

Suivez les étapes ci-dessous pour générer un jeton d’accès à partir de la console Adobe Developer et effectuez votre premier appel API via l’authentification de serveur à serveur OAuth.

### &#x200B;1. Configuration du projet Adobe Developer Console

1. Accéder à [Adobe Developer Console](https://developer.adobe.com/console)
2. Connexion avec votre Adobe ID

3. Créer un projet ou accéder à votre projet existant

>[!BEGINTABS]

>[!TAB Pour créer un projet]

1. Dans la section **Démarrage rapide**, cliquez sur **Créer un projet**
2. Un nouveau projet est créé avec un nom par défaut

   ![Créer un projet ADC](/help/forms/assets/adc-home.png)

3. Cliquez sur **Modifier le projet** dans le coin supérieur droit

   ![Modifier projet](/help/forms/assets/adc-edit-project.png)

4. Fournissez un nom significatif (par exemple, « projet de formulaire »).
5. Cliquer sur **Enregistrer**

   ![Modifier le nom du projet](/help/forms/assets/adc-edit-projectname.png)

>[!TAB Pour accéder à votre projet existant ]

1. Cliquez sur **Tous les projets** dans le Adobe Developer Console

   ![Rechercher projets](/help/forms/assets/search-adc-project.png)

2. Recherchez votre projet et cliquez pour l’ouvrir.

   ![Localisation de projets](/help/forms/assets/locate-adc-project.png)

>[!ENDTABS]

### &#x200B;2. Ajouter des API Forms

Ajoutez des API Forms en fonction de vos besoins :

* **API AEM Forms Communications** : à utiliser lorsque vous devez générer, convertir, assembler ou sécuriser des documents (PDF et formats associés).
* **API d’exécution de Forms adaptative** à utiliser lorsque vous devez effectuer le rendu, l’envoi ou le traitement du Forms adaptatif au moment de l’exécution.

>[!BEGINTABS]

>[!TAB Pour les API AEM Forms Communications]

1. Cliquez sur **Ajouter une API**

   ![Ajouter une api](/help/forms/assets/adc-add-api.png)

2. Sélectionnez **API de communication Forms**
   1. Dans la boîte de dialogue _Ajouter une API_, filtrez par **Experience Cloud**
   2. Sélectionnez **« API de communication Forms »**

      ![Ajouter l’API de communication Forms](/help/forms/assets/adc-add-forms-api.png)

   3. Cliquer sur **Suivant**
   4. Sélectionnez la méthode d’authentification **OAuth de serveur à serveur**

      ![Sélectionner la méthode d’authentification](/help/forms/assets/adc-add-authentication-method.png)

>[!TAB Pour les API d’exécution de Forms adaptatif ]

1. **Cliquez sur Ajouter une API**

   ![Ajouter une api](/help/forms/assets/adc-add-api.png)

2. **Sélectionnez l’API de diffusion et d’exécution AEM Forms**
   1. Dans la boîte de dialogue _Ajouter une API_, filtrez par **Experience Cloud**
   2. Sélectionnez **« API de diffusion et d’exécution AEM Forms »**
      ![Ajouter l’API de communication Forms](/help/forms/assets/adc-add-runtime-api.png)

   3. Cliquer sur **Suivant**
   4. Sélectionnez la méthode d’authentification **OAuth de serveur à serveur**.
      ![Sélectionner la méthode d’authentification](/help/forms/assets/adc-add-authentication-method.png)

>[!ENDTABS]

Vous pouvez également ajouter l’API et la méthode d’authentification à votre projet existant en cliquant sur **Ajouter au projet** > **API**\
![Ajouter une API à un projet existant](/help/forms/assets/add-api-existing-project.png)

### &#x200B;3. Ajouter un profil de produit

Le profil de produit fournit des autorisations (ou autorisations) pour que les informations d’identification puissent accéder aux ressources AEM.

1. Sélectionnez le **Profil produit** correspondant à l’URL de votre instance AEM (`https://Service Type -Environment Type-Program XXX-Environment XXX.adobeaemcloud.com`).

   * **Type de service** - spécifie les services ou autorisations associés à l’instance AEM

   * **Type d’environnement** - indique si l’environnement est pour le service de création ou de publication

   * **Programme XXX** - identifie l’ID du programme Cloud Manager

   * **Environnement XXX** - identifie l’identifiant d’environnement spécifique au sein de ce programme.

   >[!NOTE]
   >
   > Les profils de produit sont liés à une instance AEM spécifique (programme + environnement). Sélectionnez toujours le profil qui correspond à l’URL de votre instance.

2. Cliquez sur **Save configured API** (Enregistrer l’API configurée). L’API et le profil de produit sont ajoutés au projet

   ![Sélectionner la configuration du projet](/help/forms/assets/adc-add-product-profile.png)

### &#x200B;4. Générer et enregistrer des informations d’identification

1. Accédez à votre projet dans Adobe Developer Console
2. Cliquez sur les informations d’identification **OAuth de serveur à serveur**
3. Consultez la section **Informations d’identification**

   ![Afficher les informations d’identification](/help/forms/assets/adc-view-credential.png)

**Enregistrer les informations d’identification de l’API**

```text
    API Credentials:
    ================
    Client ID: <your_client_id>
    Client Secret: <your_client_secret>
    Technical Account ID: <tech_account_id>
    Organization ID: <org_id>
    Scopes: AdobeID,openid,read_organizations
```

### &#x200B;5. Génération de jetons d’accès

Générez le jeton d’accès manuellement ou par programmation :

>[!BEGINTABS]

>[!TAB Pour les tests]

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

>[!TAB Pour la production]

Générez des jetons par programmation à l’aide de l’API [Adobe IMS](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/security/setting-up-ims-integrations-for-aem-as-a-cloud-service) :

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

>[!ENDTABS]

Vous pouvez désormais utiliser le jeton d’accès généré pour effectuer un appel API pour les environnements de développement, d’évaluation ou de production.

>
>
> Pour en savoir plus sur l’implémentation serveur à serveur d’OAuth afin de générer un jeton d’accès et d’effectuer des appels API, [cliquez ici](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation).

## Bonnes pratiques : gestion des informations d’identification pour le développement, l’évaluation et la production

* Utilisez toujours des informations d’identification distinctes pour le développement, l’évaluation et la production.

* Mappez chaque information d’identification à l’URL d’environnement AEM appropriée.

* Stockez les secrets en toute sécurité et ne les validez jamais pour le contrôle de code source.

* Effectuez le suivi de la validité des jetons d’accès, car les jetons sont valides pendant 24 heures uniquement.

## Étapes suivantes

Pour savoir comment configurer un environnement pour les API de communication Forms synchrones, consultez [Traitement synchrone des communications AEM Forms as a Cloud Service](/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md).


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


