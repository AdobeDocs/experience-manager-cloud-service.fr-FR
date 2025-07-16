---
title: Configurer des actions d’envoi pour AEM Forms avec Edge Delivery Services
description: Découvrez comment configurer des actions d’envoi dans AEM Forms à l’aide d’Edge Delivery Services. Choisissez entre le service d’envoi de formulaires et l’action d’envoi de l’instance de publication AEM pour gérer les données de formulaire de manière sécurisée et efficace.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 8f490054-f7b6-40e6-baa3-3de59d0ad290
source-git-commit: 75d8ea4f0913e690e3374d62c6e7dcc44ea74205
workflow-type: tm+mt
source-wordcount: '2166'
ht-degree: 99%

---

# Configurer les envois de formulaires : où vont vos données ?

Lorsqu’un utilisateur ou une utilisatrice clique sur **Envoyer** dans votre formulaire, vous devez indiquer à Edge Delivery Services la manière de traiter ces données. Vous disposez de deux options principales :

## Méthode 1 : utilisation du service d’envoi AEM Forms (simplifié)

Ce service est idéal pour les actions courantes et simples comme l’envoi de données à une feuille de calcul ou un e-mail.

**De quoi s’agit-il et en quoi peut-il vous être utile ?**

Le [service d’envoi de formulaires](/help/forms/forms-submission-service.md) est un point d’entrée hébergé par Adobe. Lorsque votre formulaire lui envoie des données, ce service prend le relais et effectue une action préconfigurée. Il est conçu pour être facile à configurer. Vous pouvez configurer : l’envoi aux feuilles de calcul ou à l’e-mail :

* **Envoyer à une feuille de calcul :** ajoutez automatiquement les données de formulaire envoyées sous la forme d’une nouvelle ligne dans Google Sheet ou un fichier Microsoft Excel (stocké sur OneDrive ou SharePoint).
* **Envoyer un e-mail :** envoyez un e-mail contenant les données de formulaire à une ou plusieurs adresses e-mail que vous spécifiez.

#### Important : configuration requise

* **Accéder aux feuilles de calcul :** pour envoyer des données à Google Sheet ou à un fichier Excel sur OneDrive/SharePoint, le compte de service Adobe (souvent `forms@adobe.com`) a généralement besoin d’une **autorisation de modification** sur cette feuille de calcul.
* **Programme d’accès anticipé :** certaines fonctionnalités de ce service, en particulier pour les feuilles de calcul, peuvent faire partie d’un programme d’accès anticipé. Vous devrez peut-être demander l’accès en envoyant un e-mail à `aem-forms-ea@adobe.com` ou en remplissant un formulaire Adobe spécifique avec les détails de votre projet. Consultez toujours la documentation Adobe la plus récente.

**Organigramme du service d’envoi de formulaires**
<!--
```mermaid
    graph TD
    UserForm[User Submits Form on Your EDS Site] >|Data Sent| FormSubmissionService[AEM Forms Submission Service]
    FormSubmissionService -- "If configured for Google Sheets" > GoogleSheet[Data written to Google Sheet]
    FormSubmissionService -- "If configured for Excel (OneDrive or SharePoint)" > ExcelSheet[Data written to Excel]
    FormSubmissionService -- "If configured for Email" > Email[Email with data is sent]

    style UserForm fill:#ccf,stroke:#333
    style FormSubmissionService fill:#fca,stroke:#333
    style GoogleSheet fill:#90ee90,stroke:#333
    style ExcelSheet fill:#90ee90,stroke:#333
    style Email fill:#add8e6,stroke:#333
```-->
![Envoi de formulaires](/help/forms/assets/eds-fss.png)

Cet organigramme montre la façon dont le service d’envoi de formulaire récupère les données envoyées et les envoie à une feuille de calcul ou un e-mail configuré.

## Méthode 2 : envoi à votre instance de publication AEM (avancé)

Pour les besoins plus complexes, les [formulaires (en particulier ceux créés avec l’éditeur universel) peuvent envoyer des données directement à votre instance de publication AEM as a Cloud Service](/help/forms/configure-submit-actions-core-components.md). Cela permet d’exploiter toute la puissance du serveur principal d’AEM.

**À quel moment faut-il procéder à l’envoi à l’instance de publication AEM ?**

* Pour déclencher des workflows AEM personnalisés après l’envoi.
* Pour utiliser le modèle de données de formulaire (FDM) d’AEM à intégrer à des bases de données ou à d’autres systèmes d’entreprise.
* Pour vous connecter à des services tiers tels que Marketo, Microsoft Power Automate ou Adobe Workfront Fusion.
* Pour stocker des données à des emplacements spécifiques tels que le stockage Azure Blob ou des listes/bibliothèques de documents SharePoint (et non uniquement des feuilles de calcul).
* Lorsque vous disposez d’une logique complexe de validation côté serveur ou de traitement des données dans AEM.

**Actions d’envoi disponibles (envois de l’instance de publication AEM)**

* [Envoyer à un point d’entrée REST](/help/forms/configure-submit-action-restpoint.md)
* [Envoyer un e-mail (à l’aide des services de messagerie AEM)](/help/forms/configure-submit-action-send-email.md)
* [Envoyer à l’aide du modèle de données de formulaire (FDM)](/help/forms/configure-data-sources.md)
* [Appeler un workflow AEM](/help/forms/aem-forms-workflow-step-reference.md)
* [Envoyer à SharePoint (sous forme d’éléments de liste ou de documents)](/help/forms/configure-submit-action-sharepoint.md)
* [Envoyer à OneDrive (sous forme de documents)](/help/forms/configure-submit-action-onedrive.md)
* [Envoyer au stockage Blob Azure](/help/forms/configure-submit-action-azure-blob-storage.md)
* [Envoyer à Microsoft Power Automate](/help/forms/forms-microsoft-power-automate-integration.md)
* [Envoyer à Adobe Workfront Fusion](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
* [Envoyer à Adobe Marketo Engage](/help/forms/submit-adaptive-form-to-marketo-engage.md)

>[!NOTE]
>
> Même en cas de ciblage Google Sheet/Excel à partir de l’instance de publication AEM, l’opération implique des étapes de configuration différentes de celles du service d’envoi direct de formulaires.

**Organigramme de l’instance de publication d’AEM**

<!--```mermaid
    graph TD
    UEForm[User Submits Universal Editor Form on EDS Site] >|Data sent to AEM Publish URL - example: /adobe/forms/af/submit/...| AEMPublish[AEM Publish Instance]
    AEMPublish -- Configured to run AEM Workflow > AEMWorkflow[AEM Workflow is Triggered]
    AEMPublish -- Configured to use Form Data Model > FDM[FDM updates Backend System or Database]
    AEMPublish -- Configured for Marketo > Marketo[Data sent to Marketo Engage]
    AEMPublish -- Other configured actions... > OtherIntegrations[...]

    style UEForm fill:#ccf,stroke:#333
    style AEMPublish fill:#fca,stroke:#333
    style AEMWorkflow fill:#add8e6,stroke:#333
    style FDM fill:#add8e6,stroke:#333
    style Marketo fill:#add8e6,stroke:#333
```-->

![Organigramme de l’envoi de l’instance de publication AEM](/help/forms/assets/eds-aem-publish.png)
Cet organigramme présente un envoi de formulaire à l’instance de publication AEM, qui gère ensuite des tâches complexes en arrière-plan.

### Service d’envoi de formulaires ou envois de l’instance de publication AEM

| Fonctionnalité | Service d’envoi de formulaires | Envois de l’instance de publication AEM |
| :- | :- | :-- |
| **Idéal pour** | Capture de données simple dans des feuilles de calcul, notifications par e-mail | Workflows complexes, intégrations d’entreprise, logique personnalisée |
| **Création de formulaires** | Idéal pour les formulaires basés sur des documents ; convient pour les formulaires UE simples | Idéal pour les formulaires créés dans l’éditeur universel |
| **Effort de configuration** | Faible (configuration souvent simple) | Supérieur (nécessite l’instance de publication AEM, Dispatcher, OSGi, configuration du réseau CDN) |
| **Système principal** | Service hébergé sur Adobe | Votre instance de publication AEM as a Cloud Service |
| **Flexibilité** | Limité à Sheet/E-mail | Très flexible, gamme complète d’actions AEM Forms |
| **Exemple** | Données de formulaire de contact vers Google Sheet | Demande de prêt déclenchant un workflow d’approbation AEM |

## Intégrer des formulaires à différents sites ou différentes pages

Parfois, vous souhaitez afficher un formulaire créé et géré à un seul endroit (par exemple, un « site de formulaires » central) sur une autre page web ou un autre site.

### Pourquoi vouloir incorporer un formulaire ?

* Vous disposez d’un formulaire « Nous contacter » standard créé avec l’éditeur universel qui doit apparaître sur plusieurs pages de destination produites dans le cadre de la création basée sur des documents.
* Le contenu principal de votre site web se trouve dans la création de documents (DA) et vous devez inclure un formulaire spécialisé.
* Vous souhaitez réutiliser un seul formulaire bien conçu dans plusieurs projets EDS différents.

### Fonctionnement technique de l’incorporation de formulaires

La page sur laquelle vous souhaitez voir apparaître le formulaire (appelons-la « Page d’accueil ») contient du code (généralement un bloc ou un script spécial). Lorsqu’une personne visite la page d’accueil, ce code envoie une requête à l’URL où le formulaire réel est hébergé (appelons-le « Source du formulaire »). La Source du formulaire renvoie ensuite son code HTML, que la page d’accueil injecte et affiche.

**Architecture de formulaire incorporée**

<!--```mermaid
   graph LR
    User[User] >|Visits| HostPage[Host Page - for example: your-site.com/landing-page]
    HostPage >|Contains code to embed form| FetchForm{Host Page Requests Form HTML}
    FetchForm >|HTTP GET request to the form URL| FormSource[Form Source - for example: forms-repo.hlx.page/my-form]
    FormSource >|Returns form HTML| FetchForm
    FetchForm >|Injects form HTML into page| HostPage
    HostPage >|Displays full page with embedded form| User

    subgraph Submission ["Form Submission from Host Page"]
        HostPage_Form[Embedded form on the host page] >|User submits| TargetEndpoint[Submission endpoint - FSS or AEM Publish]
    end

    style HostPage fill:#e6f3ff,stroke:#333
    style FormSource fill:#ffe6e6,stroke:#333
    style FetchForm fill:#fff2cc,stroke:#333
    style Submission fill:#f0fff0,stroke:#333
```-->
![Architecture de formulaire incorporée](/help/forms/assets/eds-embedded-form.png)
Ce diagramme montre la page d’accueil récupérant le code HTML du formulaire à partir de la Source du formulaire et l’affichant. L’envoi utilise le point d’entrée configuré du formulaire d’origine.

## Configuration de CORS pour des formulaires incorporés

[Le partage de ressources Cross-Origin (CORS)](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing) est une fonctionnalité de sécurité du navigateur. Si votre page hôte (par exemple, `site-a.com`) tente de récupérer un formulaire d’un autre domaine (par exemple, `forms-site-b.com`), le navigateur le bloque, sauf si `forms-site-b.com` l’autorise explicitement via des en-têtes CORS.

Sans en-têtes CORS corrects sur le **serveur de la Source du formulaire**, le navigateur empêche la page hôte de charger le formulaire, et le formulaire incorporé n’apparaît pas.

### Comment configurer CORS sur le site qui diffuse votre formulaire ?

Vous devez configurer le serveur hébergeant la **Source du formulaire** pour qu’il envoie des en-têtes HTTP spécifiques dans sa réponse. La méthode exacte dépend de votre configuration EDS (par exemple, pour les projets Franklin, cela est souvent réalisé dans un fichier de configuration `helix-config.yaml` ou similaire dans votre référentiel GitHub qui contrôle le comportement du réseau CDN ou la logique du programme de travail Edge).
En-têtes clés à ajouter aux réponses de la Source du formulaire :

* `Access-Control-Allow-Origin: <URL_of_Host_Page>` (ex. : `https://your-site.com`). Pour les tests, vous pouvez utiliser `*`, mais pour la production, spécifiez le ou les domaines exacts.
* `Access-Control-Allow-Methods: GET, OPTIONS` (vous aurez peut-être besoin de `POST` si l’envoi du formulaire lui-même est également Cross-Origin, mais les envois sont généralement adressés à un point d’entrée distinct, souvent de même origine ou configuré spécifiquement).
* `Access-Control-Allow-Headers: Content-Type` (et tout autre en-tête personnalisé que la récupération de votre formulaire peut utiliser).

**Exemple (conceptuel pour un fichier de configuration) :**

```yaml
        # In the configuration for the site HOSTING THE FORM (Form Source)
        headers:
          # Apply to paths where your forms are served, e.g., /forms/**
          - path: /forms/**
            custom:
              Access-Control-Allow-Origin: https://host-page-domain.com
              Access-Control-Allow-Methods: GET, OPTIONS
```

## Considérations supplémentaires : réseaux CDN et bases de code multiples (Helix 4)

* **Règles de réseau CDN :** votre réseau CDN peut vous offrir des moyens de traiter les requêtes proxy. Par exemple, une requête à `host-page.com/embedded-form` peut être routée en interne par le réseau CDN pour récupérer du contenu de `form-source.com/actual-form`, ce qui donne l’impression qu’il possède la même origine pour le navigateur. Cette configuration peut être complexe.
* **Bases de code multiples (Helix 4) :** si votre page hôte et votre source de formulaire se trouvent dans des référentiels GitHub différents (communs dans les configurations Helix 4), assurez-vous que tout « bloc de formulaire » de JavaScript nécessaire pour générer ou gérer le formulaire est disponible dans la base de code de la page hôte ou que le HTML de formulaire récupéré à partir de la source de formulaire est autonome avec tous ses JavaScript nécessaires. Les documents originaux mentionnent que pour « helix4 avec des bases de code différentes, vous devez ajouter le bloc de formulaire sur les deux bases de code ».

### Étapes courantes de configuration de l’architecture

Voici quelques méthodes courantes que vous pouvez utiliser pour configurer vos formulaires, en combinant des méthodes de création à des stratégies d’envoi, ainsi qu’à des points de configuration clés.

#### Formulaire basé sur des documents avec envoi de feuille de calcul/e-mail

Il s’agit de la configuration la plus simple. Vous créez votre formulaire dans Word/Google Docs, afin d’envoyer des données à une feuille de calcul ou à un e-mail via le service d’envoi de Forms.

1. Définissez votre formulaire dans un document Word/Google à l’aide de la structure de tableau ou du bloc de formulaire spécifiés.
1. Dans le document (ou la configuration associée), spécifiez l’URL de la feuille de calcul cible ou l’adresse e-mail du service d’envoi de Forms.
1. Assurez-vous que `forms@adobe.com` (ou le compte de service approprié) dispose d’un accès en modification à votre feuille de calcul cible.
1. Publiez votre document sur votre site Edge Delivery.

**Architecture du service d’envoi basé sur les documents + Forms**
<!--
```mermaid
    graph TD
        User[<img src='https://img.icons8.com/ios-filled/50/000000/user.png' width='30' /> User] >|Fills Out| EDS_Page_DocBased[EDS Page with Document-Based Form]
        EDS_Page_DocBased >|Submits Data| FSS[AEM Forms Submission Service]
        FSS > Target[<img src='https://img.icons8.com/color/48/000000/google-sheets.png' width='30' /> Data to Spreadsheet / <img src='https://img.icons8.com/color/48/000000/filled-sent.png' width='30' /> Email Notification]

        Authoring[Form defined in Google Doc/Sheet] >|EDS Syncs & Renders| EDS_Page_DocBased

        style EDS_Page_DocBased fill:#ccf,stroke:#333
        style FSS fill:#fca,stroke:#333
        style Target fill:#90ee90,stroke:#333
        style Authoring fill:#e6ffe6,stroke:#333
```-->

![Architecture du service d’envoi basé sur les documents + Forms](/help/forms/assets/eds-doc-fss.png)

#### Formulaire de l’éditeur universel avec envoi de feuille de calcul/e-mail

Vous utilisez l’éditeur universel visuel pour créer votre formulaire, mais utilisez toujours le service d’envoi simple de Forms pour la capture de données.

1. Créez votre formulaire à l’aide de l’éditeur universel dans AEM.
1. Configurez l’action d’envoi du formulaire dans l’UE pour utiliser l’option « Envoyer au service d’envoi de Forms ».
1. Indiquez l’adresse e-mail ou l’URL de la feuille de calcul cible.
1. Si vous utilisez des feuilles de calcul, assurez-vous que `forms@adobe.com` dispose d’un accès en modification.
1. Publiez la page contenant le formulaire d’AEM sur votre site Edge Delivery.

   **Éditeur universel + Architecture du service d’envoi de formulaires**

   ![Éditeur universel + Architecture du service d’envoi de formulaires](/help/forms/assets/eds-ue-fss.png)

   <!--```mermaid
    graph TD
    User[User] >|Fills Out| EDS_Page_UE[EDS Page with Universal Editor Form]
    EDS_Page_UE >|Submits Data| FSS[AEM Forms Submission Service]
    FSS > Target[Data sent to Google Sheet and Email Notification]
    AuthoringUE[Form built in Universal Editor - AEM] >|AEM Publishes to EDS| EDS_Page_UE
    style EDS_Page_UE fill:#ccf,stroke:#333
    style FSS fill:#fca,stroke:#333
    style Target fill:#90ee90,stroke:#333
    style AuthoringUE fill:#e6f3ff,stroke:#333
    ```
    -->

#### Formulaire de l’éditeur universel avec envoi de l’instance de publication AEM (avancé)

Cette configuration utilise l’éditeur universel pour la création de formulaires et votre instance de publication AEM pour un traitement du système principal puissant (workflows, FDM, etc.). Cela nécessite davantage de configuration.

1. **Créer un formulaire dans UE :** créez votre formulaire dans l’éditeur universel. Configurez son action d’envoi pour qu’il pointe vers une action AEM Forms (par exemple, « Appeler un workflow AEM », « Envoyer à l’aide du modèle de données de formulaire »).
1. **Configuration d’AEM Dispatcher (sur votre niveau de publication AEM) :**
   * **Aucune redirection :** vérifiez que vos règles de Dispatcher ne redirigent *pas* les requêtes effectuées vers des chemins d’accès `/adobe/forms/af/submit/...`.
   * **Autoriser les envois :** modifiez vos filtres Dispatcher (par exemple, dans `filters.any`) pour `allow` explicitement les requêtes POST vers `/adobe/forms/af/submit/...` à partir du domaine ou des adresses IP de votre site Edge Delivery.
1. **Filtre de référent OSGi dans AEM (sur votre niveau de publication AEM) :**
   * Dans la console OSGi AEM (`/system/console/configMgr`), recherchez et configurez le « filtre de référent Apache Sling ».
   * Ajoutez le ou les domaines de votre site Edge Delivery (par exemple, `https://your-eds-domain.hlx.page`, `https://your-custom-eds-domain.com`) à la liste « Autoriser des hôtes » ou « Autoriser des hôtes RegExp ». Cela indique à AEM d’accepter les envois provenant de votre site EDS.
1. **Règle de redirection du réseau CDN (sur votre réseau CDN Edge Delivery) :**
   * Votre site Edge Delivery (par exemple, `your-eds-domain.hlx.page`) doit acheminer correctement les demandes d’envoi vers votre instance de publication AEM.
   * Lors de l’envoi du formulaire sur votre page EDS, il se peut qu’il cible un chemin relatif tel que `/adobe/forms/af/submit/...`. Vous avez besoin d’une règle sur votre réseau CDN Edge Delivery (ou programme de travail Edge) qui indique : « Si une demande arrive sur `your-eds-domain.hlx.page/adobe/forms/af/submit/...`, transférez-la (par proxy ou par redirection) vers `your-aem-publish-instance.com/adobe/forms/af/submit/...`. »
   * La mise en œuvre exacte dépend de votre fournisseur de réseau CDN (par exemple, Fastly VCL, Akamai Property Manager, Cloudflare Workers).
1. **(Facultatif) `constants.js` pour le développement (dans la base de code de votre projet EDS) :**
   * Pour le développement local ou si vos scripts de formulaire côté client doivent connaître l’URL de publication AEM complète, vous pouvez la configurer dans un fichier de configuration `constants.js` ou similaire dans le référentiel GitHub de votre projet Edge Delivery. Exemple :

   ```javascript
       // in your-eds-project/scripts/constants.js
       export const AEM_PUBLISH_URL = 'https://publish-p123-e456.adobeaemcloud.com';
            // Your form submission script might then construct the submit URL:
           // const submitUrl = `${AEM_PUBLISH_URL}/adobe/forms/af/submit/...`;
   ```

1. **Publier :** publiez votre page de formulaire d’AEM vers EDS et assurez-vous que toutes les configurations AEM sont actives sur votre instance de publication AEM.

   **Éditeur universel + Architecture de publication AEM**

![Éditeur universel + Architecture de publication AEM](/help/forms/assets/eds-aem-publish.png)

Ceci affiche le flux : l’utilisateur ou l’utilisatrice effectue des envois sur le site EDS, le réseau CDN achemine vers AEM Dispatcher, puis l’instance de publication AEM le traite.

#### Incorporation d’un formulaire dans une page de création de documents (DA)

Le contenu principal de votre site web est créé dans la création de document (DA). Vous créez votre formulaire séparément à l’aide de la création basée sur des documents ou de l’éditeur universel, puis vous l’incorporez dans votre page DA.

1. **Créer et publier le formulaire :**
   * Utilisez la création basée sur des documents OU l’éditeur universel pour créer votre formulaire.
   * Configurez sa méthode d’envoi (vers le service d’envoi de formulaires ou l’instance de publication AEM, conformément aux configurations 1, 2 ou 3).
   * Publiez ce formulaire afin qu’il soit en ligne sur sa propre URL Edge Delivery (par exemple, `.../forms/my-special-form`).
1. **Configurer CORS :** sur le site/projet Edge Delivery qui héberge ce formulaire autonome, assurez-vous que les en-têtes CORS sont configurés pour permettre au domaine de votre site de création de documents de le récupérer.
1. **Créer une page dans DA :** créez ou modifiez une page dans la création de document.
1. **Incorporer le bloc de formulaire :** utilisez le bloc approprié dans DA pour incorporer une URL externe. Pointez ce bloc vers l’URL de votre formulaire publié autonome.
1. **Publier la page DA :** publiez votre page DA. Le formulaire est maintenant récupéré et affiché.

   **Formulaires incorporés dans l’architecture DA**

   ![Formulaires incorporés dans l’architecture DA](/help/forms/assets/eds-forms-embedd-da.png)

   Ceci montre une page DA extrayant un formulaire à partir d’un autre emplacement EDS. Le formulaire incorporé gère son propre envoi.

## Résolution des problèmes

* **Mon envoi de formulaire ne fonctionne pas.**
   * **Vérifier les erreurs de la console :** ouvrez la console de développement de votre navigateur (généralement F12) et recherchez les erreurs dans l’onglet Réseau ou l’onglet Console lors de l’envoi.
   * **Vérifier l’URL d’envoi :** le formulaire tente-t-il de s’envoyer au point d’entrée correct (URL du service d’envoi de formulaires ou chemin de publication AEM) ?
   * **Service d’envoi de formulaires :** en cas d’envoi vers une feuille de calcul, `forms@adobe.com` a-t-il reçu un accès en modification ? L’URL de la feuille de calcul est-elle correcte ?
   * **Envois de publication AEM :**
      * Votre Dispatcher autorise-t-il les publications à `/adobe/forms/af/submit/...`?
      * Le filtre du référent Sling sur l’instance de publication AEM est-il configuré pour autoriser votre domaine EDS ?
      * Vos règles de redirection du réseau CDN pour `/adobe/forms/af/submit/...` fonctionnent-elles correctement ?

* **Mon formulaire incorporé n’apparaît pas.**

   * **CORS !** Il s’agit du motif le plus fréquent. Recherchez les erreurs CORS dans la console du navigateur. Vérifiez que le site *hébergeant* le formulaire comporte les en-têtes `Access-Control-Allow-Origin` corrects.
   * **URL du formulaire correcte ?** Le code intégré sur la page d’accueil pointe-t-il vers l’URL active correcte du formulaire ?
   * **Blocs JavaScript :** si le rendu du formulaire repose sur un « bloc de formulaire » JavaScript spécifique, le code de ce bloc est-il disponible sur la page hôte ?

* **Un message « 403 Forbidden » ou « 401 Unauthorized » apparaît lors de l’envoi sur l’instance de publication AEM.**

   * Cela pointe souvent vers le filtre de référent Sling sur l’instance de publication AEM qui n’autorise pas les requêtes provenant de votre domaine EDS. Vérifiez à nouveau sa configuration.
   * Il peut également s’agir d’un problème d’authentification/d’autorisation si votre point d’entrée d’envoi AEM le requiert, bien que les envois de formulaires standard soient généralement anonymes.

## Étapes suivantes

Ce guide présente une vue d’ensemble de l’utilisation des formulaires avec AEM Edge Delivery Services. Pour obtenir des instructions détaillées sur les configurations spécifiques, reportez-vous à la documentation officielle d’Adobe Experience Manager :

* [Création basée sur des documents avec les formulaires Edge Delivery Services](/help/edge/docs/forms/tutorial.md)
* [Éditeur universel avec formulaires Edge Delivery Services](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
* [Création de documents (DA) et incorporation de contenu](https://www.aem.live/developer/da-tutorial)
* [Service d’envoi de formulaires AEM](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md)
