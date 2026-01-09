---
title: API AEM Forms Communications - Présentation
description: Présentation des API Communications d’AEM Forms, y compris les méthodes d’authentification et la référence API complète
role: Developer, User
feature: Adaptive Forms, APIs & Integrations
hide: true
hidefromtoc: true
index: false
source-git-commit: e2f57a32fcc098a2331ad74540a3d48832c2b3c3
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 6%

---


# API AEM Forms - Présentation

Les API d’AEM Forms fournissent une suite complète d’API natives dans le cloud conçues pour aider les entreprises à automatiser les workflows de documents.

Les API d’AEM Forms sont structurées et accessibles via deux consoles principales :

* [Adobe Developer Console (ADC)](https://developer.adobe.com/developer-console/) - Adobe Developer Console est la passerelle vers les API, les événements, le runtime et App Builder d’Adobe.

* [AEM Developer Console](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console) - AEM Developer Console permet d’accéder aux détails, aux configurations, aux comptes techniques et aux informations d’identification de service au niveau de l’environnement, afin de prendre en charge les tâches opérationnelles et d’intégration.

Différentes API prennent en charge différentes [&#x200B; méthodes d’authentification &#x200B;](#authentication-methods).

## Méthodes d’authentification

Les différentes API Forms utilisent différentes méthodes d’authentification en fonction de leur calendrier de publication :

* [OAuth serveur à serveur](/help/forms/oauth-api-authetication.md)
* [JWT (JSON Web Token) serveur à serveur](/help/forms/jwt-api-authentication.md)

Les API antérieures prenaient en charge l’authentification serveur à serveur basée sur JWT, qui est configurée et gérée via AEM Developer Console. Les API plus récentes utilisent l’authentification de serveur à serveur OAuth et sont configurées via Adobe Developer Console.

>[!NOTE]
>
> Adobe normalise la méthode d’authentification sur toutes les API et intègre progressivement les API à Adobe Developer Console, qui prend en charge la méthode d’authentification de serveur à serveur OAuth.

## Présentation de la classification d’API

Toutes les API d’AEM Forms sont divisées en deux parties principales :

* [API de diffusion et d’exécution de formulaire adaptatif](https://developer-stage.adobe.com/experience-cloud/experience-manager-apis/api/stable/forms/)

* [API de communication AEM Forms](#aem-forms-communications-apis)

| Détails | API de diffusion et d’exécution de formulaire adaptatif | API de communication |
|--------------|----------------------------|--------------------------|
| Objectif | Gérer les opérations de diffusion et d’exécution de formulaires adaptatifs | Génération et manipulation de documents |
| Cas d’utilisation | - Rendu du formulaire<br>- Préremplissage de données<br>- Envois de formulaires<br>- Gestion des brouillons | - Génération de PDF <br>- Fusion de documents <br>- Traitement par lots <br>- Opérations d’impression |
| Méthode d’autorisation | Prend en charge les méthodes d’authentification de serveur à serveur/utilisateur OAuth. | Prend en charge l’authentification de serveur à serveur, au format JWT ou OAuth, selon l’API. Une API ne peut pas prendre en charge les deux méthodes d’authentification. |

### API AEM Forms Communications

Les API Communications sont le principal point d’intérêt des opérations centrées sur les documents.

Le tableau ci-dessous répertorie toutes les [API AEM Forms Communications](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/) ainsi que leurs méthodes d’authentification et modèles d’exécution pris en charge :

#### API de génération de documents


| Point d’entrée de l’API | Description | Modèle d’exécution | Méthode d&#39;authentification |
| ----- | ------ |------- | ------ |
| [/adobe/forms/batch/output/config](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Configuration/operation/CreateBatchConfig) | Crée une configuration de lot pour les traitements de génération de documents. | Asynchrone/par lot | [&#x200B; JWT &#x200B;](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/batch/output/config/{configName}](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Configuration/operation/GetBatchConfigbyName) | Récupère les détails d’une configuration de lot spécifique. | Asynchrone/par lot | [&#x200B; JWT &#x200B;](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/batch/output/config/configs](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Configuration/operation/GetAllBatchConfigs) | Renvoie une liste de toutes les configurations de lot disponibles. | Asynchrone/par lot | [&#x200B; JWT &#x200B;](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/batch/output/config/{configName}/execution](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Execution/operation/StartBatchRun) | Démarre une exécution de génération de sortie par lots à l’aide d’une configuration . | Asynchrone/par lot | [&#x200B; JWT &#x200B;](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/batch/output/config/{configName}/execution/{executionId}](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Execution/operation/GetBatchRunInstanceState) | Récupère le statut d’exécution d’un traitement par lots. | Asynchrone/par lot | [&#x200B; JWT &#x200B;](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/batch/output/config/{configName}/exécutions](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Execution/operation/GetAllRunningInstancesForBatch) | Répertorie toutes les instances en cours d’exécution pour une configuration de lot spécifique. | Asynchrone/par lot | [&#x200B; JWT &#x200B;](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/doc/v1/generatePDFOutput](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-sync/#tag/Communications-Services/paths/~1adobe~1forms~1doc~1v1~1generatePDFOutput/post) | Génère une sortie PDF de manière synchrone en fonction de modèles et de données. | Synchrone | [Oauth](/help/forms/oauth-api-authetication.md) |
| [/adobe/forms/doc/v1/generatePrintedOutput](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-sync/#tag/Batch-Execution/operation/GetAllRunningInstancesForBatch) | Génère des formats de sortie prêts à l’impression (par exemple, PCL, PostScript). | Synchrone | [Oauth](/help/forms/oauth-api-authetication.md) |
| [/adobe/forms/doc/v1/generate/afp](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-sync/#tag/Communications-Services/paths/~1adobe~1forms~1doc~1v1~1generate~1afp/post) | Génère une sortie AFP pour l&#39;impression de gros volumes. | Synchrone | [Oauth](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/generate/pdfform](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFForm) | Rend un formulaire PDF (XFA/XDP) avec des données fusionnées. | Synchrone | [Oauth](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/generate/pdfform/jobs/{id}/status](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFFormJobStatus) | Récupère le statut d’une tâche de génération de formulaire PDF. | Synchrone | [Oauth](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/generate/pdfform/jobs/{id}/result](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFFormJobResult) | Récupère la sortie/le résultat d’une tâche de formulaire PDF terminée. | Synchrone | [Oauth](/help/forms/oauth-api-authetication.md) |


#### API de manipulation de documents

| Point d’entrée de l’API | Description | Modèle d’exécution | Méthode d&#39;authentification |
| ------------------ | ---------------- | ----------| ---------- |
| [/adobe/forms/assembler/ddx/invoke](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/assembler-sync/#tag/DDX-execution/operation/InvokeDDX) | Exécute les instructions DDX pour combiner, fractionner ou manipuler des fichiers PDF. | Synchrone | [&#x200B; JWT &#x200B;](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/assembler/pdfa/convert](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/assembler-sync/#tag/Document-conversion/operation/ConvertToPDFA) | Convertit un document PDF au format PDF/A. | Synchrone | [&#x200B; JWT &#x200B;](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/assembler/pdfa/validate](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/assembler-sync/#tag/Document-validation/operation/CheckIsPDFA) | Valide si un PDF est conforme à la norme PDF/A | Synchrone | [&#x200B; JWT &#x200B;](/help/forms/jwt-api-authentication.md) |

#### API de conversion de documents

| Point d’entrée de l’API | Description | Modèle d’exécution | Méthode d&#39;authentification |
|--------- | -------|---------|----------------------|
| [/adobe/document/convert/pdftoxdp](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Conversion/paths/~1convert~1pdftoxdp/post) | Convertit un formulaire PDF au format XDP. | Synchrone | [Oauth](/help/forms/oauth-api-authetication.md) |

#### API d’extraction de documents

| Point d’entrée de l’API | Description | Modèle d’exécution | Méthode d&#39;authentification |
|---------| -------|---------|----------------------|
| [/adobe/forms/doc/v1/extract/pdfproperties](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Extraction/paths/~1extract~1pdfproperties/post) | Extrait les propriétés et les informations structurelles d’un PDF. | Synchrone | [Oauth](/help/forms/oauth-api-authetication.md) |
| [/adobe/forms/doc/v1/extract/usagerights](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/extractUsageRights) | Extrait les droits d’utilisation incorporés dans un PDF. | Synchrone | [Oauth](/help/forms/oauth-api-authetication.md) |
| [/adobe/forms/doc/v1/extract/metadata](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Extraction/paths/~1extract~1metadata/post) | Extrait les métadonnées telles que le titre, l’auteur et les mots-clés. | Synchrone | [Oauth](/help/forms/oauth-api-authetication.md) |
| [/adobe/forms/doc/v1/extract/data](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/exportData) | Extrait les données de formulaire (XML/JSON) de PDF forms. | Synchrone | [Oauth](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/extract/security](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Extraction/paths/~1extract~1security/post) | Extrait les paramètres de sécurité tels que les autorisations et le chiffrement. | Synchrone | [Oauth](/help/forms/oauth-api-authetication.md) |

#### API de transformation de documents


| Point d’entrée de l’API | Description | Modèle d’exécution | Méthode d&#39;authentification |
|--------|---------|---------|----------------------|
| [/adobe/document/transform/metadata](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Transformation/paths/~1transform~1metadata/post) | Met à jour ou ajoute des métadonnées dans un document PDF. | Synchrone | [Oauth](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/field/signature/add](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Transformation/paths/~1field~1signature~1add/post) | Ajoute un champ de signature numérique à un PDF. | Synchrone | [Oauth](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/field/signature/clear](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Transformation/paths/~1field~1signature~1clear/post) | Efface le contenu d’un champ de signature. | Synchrone | [Oauth](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/field/signature/remove](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Transformation/paths/~1field~1signature~1remove/post) | Supprime un champ de signature d’un PDF. | Synchrone | [Oauth](/help/forms/oauth-api-authetication.md) |

#### API Document Assurance

| Point d’entrée de l’API | Description | Modèle d’exécution | Méthode d&#39;authentification |
|---------|-------|---------|----------------------|
| [/adobe/document/assure/usagerights](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/applyUsageRights) | Applique des droits d’utilisation à un PDF (par exemple, commentaire, remplissage, signature). | Synchrone | [Oauth](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/assure/encrypt](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Assurance/paths/~1assure~1encrypt/post) | Chiffre un PDF avec mot de passe ou certificat de sécurité. | Synchrone | [Oauth](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/assure/decrypt](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Assurance/paths/~1assure~1decrypt/post) | Déchiffre un document PDF sécurisé. | Synchrone | [Oauth](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/assure/sign](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Assurance/paths/~1assure~1sign/post) | Signe numériquement un document PDF. | Synchrone | [Oauth](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/assure/certifie](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Assurance/paths/~1assure~1certify/post) | Certifie un PDF avec un certificat numérique. | Synchrone | [Oauth](/help/forms/oauth-api-authetication.md) |


## Étapes connexes

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


>[!MORELIKETHIS]
>
>* [Présentation des communications AEM Forms as a Cloud Service](/help/forms/aem-forms-cloud-service-communications-introduction.md)
>* [Architecture AEM Forms as a Cloud Service pour les API Adaptive Forms et Communication](/help/forms/aem-forms-cloud-service-architecture.md)
>* [Traitement des communications - API synchrones](/help/forms/aem-forms-cloud-service-communications.md)
>* [Traitement des communications - API par lots](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)
>* [Traitement des communications - API à la demande](/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md)
