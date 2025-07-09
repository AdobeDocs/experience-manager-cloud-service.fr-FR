---
title: Vue d’ensemble d’Edge Delivery Services pour AEM Forms
description: Edge Delivery Services pour AEM Forms conçu pour des performances de pointe, vous permet d’envisager l’avenir de la collecte de données rationalisée et de l’interaction client.
feature: Edge Delivery Services
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
role: Admin, Architect, Developer
source-git-commit: bca160763fdd1e96f1350ac74eb76ff7c26ac00b
workflow-type: tm+mt
source-wordcount: '1874'
ht-degree: 7%

---


# Prise en main de Forms sur AEM Edge Delivery Services

<span class="preview">Il s’agit d’une fonctionnalité de version préliminaire accessible par le biais de notre [canal de version préliminaire](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=fr#new-features). </span>

Ce guide vous aide à comprendre et à implémenter des formulaires à l’aide de Adobe Experience Manager (AEM) Edge Delivery Services (EDS). Que vous créiez un formulaire de contact simple ou un outil de collecte de données complexe, cette page vous guide tout au long des options.

## Présentation de Forms dans Edge Delivery Services

Edge Delivery Services est une solution moderne d’Adobe qui permet de diffuser du contenu web, y compris des formulaires, avec des performances et une agilité exceptionnelles. En utilisant Edge Delivery Services pour vos formulaires, vous pouvez :

* **Offrez des expériences plus rapides :** les Forms se chargent incroyablement rapidement, car elles sont diffusées à partir d’un réseau mondial de serveurs Edge (CDN) proche de vos utilisateurs. Cela améliore la satisfaction des utilisateurs et peut augmenter les taux de remplissage des formulaires.
* **Mettre à jour Forms plus facilement :** l’approche Edge Delivery Services permet souvent des cycles de développement et des mises à jour de contenu plus rapides, ce qui vous permet d’adapter rapidement vos formulaires.
* **Créer un Forms moderne et réactif :** créez des formulaires qui s’affichent avec élégance et qui fonctionnent de manière transparente sur n’importe quel appareil.
* **Bénéficiez de l’évolutivité et de la fiabilité :** vos formulaires seront aussi robustes et évolutifs que l’infrastructure Edge sous-jacente.

Ce guide :

* Expliquez les différentes manières de créer (créer) des formulaires pour vos sites Edge Delivery.
* Vous montrer comment configurer ce qui se passe après l’envoi d’un formulaire par un utilisateur (actions d’envoi).
* Vous aider à choisir les meilleures méthodes pour vos besoins spécifiques et les compétences de l&#39;équipe.
* Fournissez des diagrammes architecturaux et des bonnes pratiques.

## Termes Clés À Connaître

* **Edge Delivery Services (EDS) : architecture d’Adobe** la performance d’abord pour diffuser du contenu AEM via des réseaux de diffusion de contenu. Également appelé le projet Franklin.
* **AEM Forms:** Solution Adobe pour la création, la gestion et le traitement des formulaires.
* **Éditeur universel (UE) :** éditeur visuel WYSIWYG pour le contenu AEM, y compris les formulaires.
* **Création basée sur des documents :** création de formulaires à l’aide de Microsoft Word ou Google Docs/Sheets.
* **Création de documents (DA) :** service hébergé par Adobe pour la création de contenu (y compris des pages pouvant héberger des formulaires) pour Edge Delivery Services.
* **Service d’envoi Forms (FSS) :** service Adobe qui simplifie l’envoi de données de formulaire vers des feuilles de calcul ou des e-mails.
* **Instance de publication AEM :** environnement AEM actif pouvant traiter des envois de formulaires complexes.
* **PARTAGE DE RESSOURCES CROSS-ORIGIN (CORS) :** fonctionnalité de sécurité de navigateur qui doit être configurée lors de l’incorporation de formulaires provenant de différents domaines.
* **CDN (réseau de diffusion de contenu) :** réseau de serveurs qui diffuse rapidement du contenu web aux utilisateurs en fonction de leur emplacement géographique.


**Diagramme conceptuel de l’interaction de formulaire Edge Delivery Services**

<!--  
```mermaid
graph LR
    User[User on Device] >|Interacts| EdgeForm[Edge-Delivered Form Page]
    EdgeForm >|Loads Instantly| CDN[CDN Edge Server]
    CDN >|Serves Content| User
    EdgeForm >|Submits Data| Backend[Backend Processing - e.g. Forms Submission Service / AEM Publish]
    style User fill:#f9f,stroke:#333,stroke-width:2px
    style EdgeForm fill:#ccf,stroke:#333,stroke-width:2px
    style CDN fill:#9cf,stroke:#333,stroke-width:2px
    style Backend fill:#fca,stroke:#333,stroke-width:2px
``` -->

![Interaction de formulaire](/help/forms/assets/eds-form-interaction.png)
Ce diagramme montre un utilisateur interagissant avec un formulaire diffusé rapidement via un réseau CDN. Les données qu’ils envoient sont ensuite gérées par un système principal.

## Comment Forms fonctionne-t-il avec Edge ?

Avec EDS, le contenu de votre site web (y compris la structure de vos formulaires) peut provenir de diverses sources telles qu’AEM as a Cloud Service, SharePoint, Google Drive ou le service de création de documents (DA). Ce contenu est ensuite publié sur un réseau CDN global. Lorsqu’un utilisateur visite votre site, le contenu est diffusé directement à partir du serveur de réseau CDN le plus proche, assurant ainsi une vitesse maximale.

<!--*   **Where AEM Forms Fit In**
    Forms in an EDS architecture are designed to be:
    *   **Fast Loading:** Form structures are often simple HTML rendered client-side.
    *   **Decoupled:** The visual part of the form (frontend) is separate from where the data goes after submission (backend).
    *   **Flexible to Create:** You have different tools to build your forms.
    *   **Configurable for Submission:** You can send data to simple services or powerful AEM backends.-->

**Architecture Edge Delivery Services simplifiée avec Forms**

<!--
```mermaid
    graph TD
        UserStart[<img src='https://img.icons8.com/ios-filled/50/000000/user.png' width='30' /> User on Device] >|Interacts| EdgeForm[Edge-Delivered Form Page]
        EdgeForm >|Loads Instantly| CDN[CDN Edge Server]
        CDN >|Serves Content| UserEnd[<img src='https://img.icons8.com/ios-filled/50/000000/user.png' width='30' /> User on Device]
        EdgeForm >|Submits Data| Backend[Backend Processing - Form Submission Service / AEM Publish]

        style UserStart fill:#f9f,stroke:#333,stroke-width:2px
        style UserEnd fill:#f9f,stroke:#333,stroke-width:2px
        style EdgeForm fill:#ccf,stroke:#333,stroke-width:2px
        style CDN fill:#9cf,stroke:#333,stroke-width:2px
        style Backend fill:#fca,stroke:#333,stroke-width:2px
``` -->

![ Architecture ](/help/forms/assets/eds-simplified-architecture.png)
Ce diagramme présente le parcours : les formulaires sont définis dans un système de création, publiés sur Edge, diffusés aux utilisateurs et utilisatrices, et les données envoyées sont traitées par un serveur principal.

## Choix de la méthode de création de formulaire

Vous disposez de trois méthodes principales pour créer des formulaires pour vos sites Edge Delivery Services. Votre choix dépendra des compétences de votre équipe, de la complexité du formulaire et des besoins de votre projet.

### Quelle approche de création vous convient le mieux ?

Utilisez cette arborescence de décision pour effectuer les choix suivants :

**Arborescence de décision de création de formulaire**
<!--    
```mermaid
    graph TD
        A{Start: I need to create a form for an Edge Delivery Services site} > B{What are my team's primary content creation tools & skills?}
        B -- "We mainly use Word / Google Docs / Sheets" > C{How complex is the form and where does the data need to go?}
        B -- "We use AEM and prefer visual tools (Marketers or Designers)" > D[Use Universal Editor - WYSIWYG]
        B -- "Our site content is managed in Document Authoring (DA)" > E[Use Document Authoring - Embed Forms]
        C -- "Simple to moderate form, data to a spreadsheet or email" > F[Use Document-Based Authoring]
        C -- "More complex logic or needs AEM backend integration" > D
        E > G[Create form using Document-Based Authoring or Universal Editor, then embed in your DA page]

        style A fill:#f9f,stroke:#333,stroke-width:2px
        style F fill:#ccf,stroke:#333,stroke-width:2px
        style D fill:#ccf,stroke:#333,stroke-width:2px
        style G fill:#ccf,stroke:#333,stroke-width:2px
``` -->

![Sélection de la bonne plateforme](/help/forms/assets/eds-authoring-selection.png)

Cette arborescence de décision vous permet de sélectionner une méthode de création en fonction des besoins de votre équipe et de votre formulaire.

### Création de Forms avec des documents (Word/Google Docs)

Cette méthode est idéale pour [créer rapidement des formulaires si votre équipe maîtrise Microsoft Word ou Google Docs/Sheets](/help/edge/docs/forms/create-forms.md).

**Fonctionnement : du document au formulaire web**

Vous définissez les champs, étiquettes et types de votre formulaire directement dans un document Word ou une feuille Google à l’aide d’un format de tableau spécial ou d’un « bloc de formulaire ». Lorsque vous publiez ce document, Edge Delivery Services le convertit automatiquement en un formulaire HTML prêt pour le web avec lequel les utilisateurs peuvent interagir sur votre site.

**Fonctionnalités**

* Créez dans des outils familiers : Word, Google Docs, Google Sheets.
* Définir des champs : entrées de texte, e-mail, listes déroulantes, cases à cocher, boutons radio, zones de texte.
* Ajoutez des étiquettes, des espaces réservés et des messages d’aide.
* Définissez des règles de validation de base : champs obligatoires, format des e-mails.
* Intégrez reCAPTCHA pour la protection contre le spam.
* Autoriser les chargements de fichiers.
* Publier instantanément : les modifications apportées à votre document sont rapidement répercutées sur le site actif.
* Étendre avec du code personnalisé : les utilisateurs expérimentés peuvent ajouter des composants de formulaire personnalisés et un style via GitHub.

**Considérations**

* Votre équipe utilise régulièrement Word ou Google Docs/Sheets pour le contenu.
* Vous devez créer rapidement des formulaires simples à modérément complexes.
* Vous souhaitez envoyer les données de formulaire directement à une feuille de calcul ou à une adresse e-mail avec une configuration minimale.

**Fonctionnement Des Envois (Principalement Le Service D’Envoi Forms)**

Les Forms créées de cette manière [envoient généralement leurs données au service d’envoi AEM Forms](/help/forms/forms-submission-service.md). Vous la configurez (souvent dans le document source lui-même) pour envoyer des données à une feuille de Google, à un fichier Excel sur OneDrive/SharePoint ou sous la forme d’un e-mail.

**Concept de création basé sur les documents**
<!--    
```mermaid
    graph LR
        subgraph Authoring["You define your form in a Google Sheet or Word Document"]
        Sheet[Spreadsheet or Document with field definitions:\nField Name - Type - Label\nemail - email - Email Address\nmessage - textarea - Your Message]
    end

        Sheet >|Edge Delivery Services automatically converts it| JSON[Internal Form Definition as JSON]
    JSON >|A 'Form Block' on your page renders it as| HTMLForm[Live HTML Form on Your Website]

        style Sheet fill:#e6ffe6,stroke:#333
        style JSON fill:#e6e6ff,stroke:#333
        style HTMLForm fill:#ffe6e6,stroke:#333
```-->

![Basé sur les documents](/help/forms/assets/eds-doc-based.png)
Ce diagramme montre comment un formulaire défini dans un document devient un formulaire web en ligne.

### Forms visuellement avec l’éditeur universel

L’[éditeur universel](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) offre une interface moderne par glisser-déposer pour créer des formulaires directement dans votre navigateur web.

**Fonctionnement : glisser-déposer la création de formulaire**

Vous utilisez une interface visuelle pour faire glisser des composants de formulaire (champs de saisie, boutons, listes déroulantes, etc.) sur votre page. Vous pouvez ensuite configurer les propriétés de chaque composant (libellés, validation, etc.) via un panneau de propriétés. L’éditeur universel vous affiche un aperçu en temps réel de votre formulaire.

**Fonctionnalités**

* Création de formulaires visuels avec une bibliothèque de composants préconfigurés.
* Configurer la validation en temps réel et la logique commerciale (par exemple, afficher/masquer les champs en fonction des sélections).
* Consultez les aperçus en direct pour différents appareils (bureau, mobile).
* Intégrez-la à des fonctionnalités AEM telles que les fragments de contenu, les workflows AEM et les autorisations utilisateur.
* Utilisez « Experience Builder » pour obtenir de l’aide de l’IA pour créer ou modifier des formulaires à l’aide d’invites.

**Considérations**

* Vous devez créer des formulaires complexes avec une logique conditionnelle, des panneaux à plusieurs étapes ou une personnalisation.
* Votre équipe (par exemple, spécialistes marketing, utilisateurs professionnels) préfère les outils visuels.
* Vous avez besoin d’une forte intégration à AEM as a Cloud Service pour la gouvernance, les workflows ou l’utilisation de ressources AEM dans vos formulaires.

**Fonctionnement des envois (service d’envoi Forms ou publication AEM)**

Forms créé avec l’éditeur universel peut :

* Utilisez le simple service d’envoi [Forms](/help/forms/forms-submission-service.md) (pour envoyer des données vers des feuilles de calcul ou des e-mails).
* Envoyez des données à votre instance de publication AEM pour un traitement plus avancé (comme le démarrage d’un workflow AEM, l’utilisation du modèle de données de formulaire ou l’intégration à d’autres systèmes d’entreprise).

**Concept de l’éditeur universel**

<!--    
```mermaid
    graph TD
    subgraph UE_Interface["Universal Editor Interface in your Browser"]
        Toolbar[Editor Toolbar and Asset Finder]
        Canvas[Your Page with the Form Being Built]
        ComponentPalette[Available Form Components:\nInput / Dropdown / Button\nDrag and drop]
        PropertiesPanel[Configure Selected Component:\nLabel / Validation / Rules]
    end
    ComponentPalette >|Drag & Drop onto| Canvas
    Canvas >|Select a component to edit its| PropertiesPanel
    UE_Interface >|Creates| RenderedForm[Live Form on Your Website]

    style UE_Interface fill:#f0f8ff,stroke:#333
    style RenderedForm fill:#ffe6e6,stroke:#333
```-->

![Éditeur universel](/help/forms/assets/eds-ue-based.png)

Ce diagramme présente les principales parties de l’éditeur universel utilisées pour la création de formulaires.

### Utilisation de Forms avec la création de documents (DA)

[La création de documents (DA)](https://www.aem.live/developer/da-tutorial) est un service hébergé par Adobe qui permet de créer et de gérer le contenu de votre site web principal (pages, articles) qui sera diffusé via Edge Delivery Services. Il s’agit d’une alternative à l’utilisation de SharePoint ou de Google Drive pour votre contenu source Edge Delivery Services.

**Présentation de la création de documents (DA) pour le contenu Edge Delivery Services**

La création de documents fournit un environnement de création de niveau entreprise à l’aide du système de conception Adobe (Spectrum) et du modèle de document AEM (blocs, sections). Il est conçu pour la gestion de contenu structuré pour EDS.

**Comment DA gère Forms (incorporation, pas création directe)**

DA n’est **pas un outil permettant de créer des formulaires à partir de zéro**. Au lieu de cela, vous utilisez DA pour créer vos pages web, puis vous *incorporez* des formulaires (créés à l’aide de la création basée sur les documents ou de l’éditeur universel) dans ces pages créées par DA.

**Étapes d’intégration de Forms à vos pages DA**

1. **Créez votre formulaire :** Créez votre formulaire à l’aide de l’une des méthodes suivantes :
   * Création basée sur des documents (Word/Google Docs)
   * Éditeur universel

1. **Publier votre formulaire :** assurez-vous que ce formulaire est publié et accessible via sa propre URL Edge Delivery (par exemple, `https://your-eds-project.hlx.page/forms/contact-us`).
1. **Créer votre page dans DA :** créez ou modifiez la page dans la création de documents à l’endroit où vous souhaitez que le formulaire apparaisse.
1. **Incorporer le formulaire :** utilisez un « bloc » ou un composant spécifique dans votre page DA pour référencer et incorporer le formulaire à partir de son URL. La page DA récupère et affiche alors ce formulaire créé en externe.

**Création de documents avec formulaire incorporé**
<!--
```mermaid
    graph TD
    subgraph FormCreation["1. Create Form using other methods"]
        UE_Form[Universal Editor Form] >|Published to| FormLocation[Form lives at its own Edge Delivery Services URL:\nfor example: /forms/my-contact-form]
        DocBased_Form[Document-Based Form] >|Published to| FormLocation
    end

    subgraph DA_Content["2. Author Page in Document Authoring"]
        DAPage[Your Web Page Authored in DA\nExample: /main-site/landing-page]
        EmbedBlock[On DA Page, add 'Embed Form' Block\nPoints to /forms/my-contact-form]
    end

    DAPage > EmbedBlock
    User[User visits your DA Page] > DAPage
    EmbedBlock >|DA Page fetches and displays| FormLocation[The Form appears on your DA Page]

    style FormCreation fill:#e6ffe6,stroke:#333
    style DA_Content fill:#ffe6cc,stroke:#333
    style FormLocation fill:#ccf,stroke:#333
```-->

![Création de documents](/help/forms/assets/eds-da-based.png)

Ce diagramme montre que vous créez d’abord un formulaire à l’aide de l’UE ou de documents, puis que vous l’incorporez dans une page que vous créez dans Document Authoring.


### Comparaison des options de création

| Critères | Création basée sur des documents | Éditeur universel (WYSIWYG) | Forms dans la création de documents (DA) |
|----------------------------------|---------------------------------------|-----------------------------------------|-------------------------------------------|
| **Outil de création de Principal** | Word/Google Docs/Sheets | Navigateur (éditeur universel d’AEM) | N/A (les Forms sont *incorporées*) |
| **Niveau de compétence de l’équipe** | Familiarisez-vous avec les éditeurs de document | Familiarisez-vous avec les outils web visuels | Utilise les données pour le contenu de la page |
| **Complexité standard des formulaires** | Simple à modérée | Modéré à complexe, de niveau entreprise | Dépend du formulaire incorporé |
| **Option d’envoi 1 (simple)** | Service de soumission Forms (sur feuille/e-mail) | Service de soumission Forms (sur feuille/e-mail) | Suit la configuration du formulaire incorporé |
| **Option de soumission 2 (Avancée)** | S/O | Publication AEM (workflow, FDM, etc.) | Suit la configuration du formulaire incorporé |
| **Intégration du serveur principal AEM** | Minimal | Élevée (avec envoi de l’instance de publication AEM) | Indirectement, via le formulaire de l’éditeur universel incorporé |
| **Idéal Pour...** | Création rapide de formulaires simples par les équipes de contenu, capture rapide de données. | Spécialistes marketing, utilisateurs professionnels ayant besoin d’un contrôle visuel, de formulaires complexes ou d’une intégration approfondie d’AEM. | Sites où le contenu principal est géré dans DA, ce qui nécessite des formulaires provenant d’autres sources. |

**Arborescence de décision améliorée**
<!--
```mermaid
    graph TD
    A{Start Here: I need a form on my Edge Delivery Services Site} > B{What's my team's main authoring tool & skill for form content?};
    B -- "Word/Google Docs" > C{How complex is the form & data destination?};
    C -- "Simple form, data to Sheet/Email" > Sol1[CHOOSE: Document-Based Authoring + Forms Submission Service];
    C -- "Needs more logic OR AEM backend\nlike Workflow or FDM" > Sol2[CONSIDER: Can Universal Editor meet this need better?];

    B -- "AEM User / Visual Editor needed\nMarketer or Designer" > D{Where does the form data need to go?};
    D -- "Simple - to Sheet/Email" > Sol3[CHOOSE: Universal Editor + Forms Submission Service];
    D -- "Advanced - AEM Workflow, FDM,\n3rd Party via AEM" > Sol4[CHOOSE: Universal Editor + AEM Publish Submissions\nRequires additional setup];

    B -- "Our main site content is in Document Authoring (DA)" > Sol5[STRATEGY: Author form using Sol1, Sol2, Sol3 or Sol4 first\nTHEN embed that form into your DA page];

    A > F{Will this form be embedded or fetched from another site or domain?};
    F -- "Yes" > G[IMPORTANT: Configure CORS on the site hosting the form.\nEnsure any form JavaScript blocks are available where the form is displayed];

    style Sol1 fill:#90ee90,stroke:#333
    style Sol2 fill:#fffacd,stroke:#333
    style Sol3 fill:#90ee90,stroke:#333
    style Sol4 fill:#90ee90,stroke:#333
    style Sol5 fill:#add8e6,stroke:#333
    style G fill:#ffb6c1,stroke:#333
```-->

![ Arborescence de décision ](/help/forms/assets/eds-enhanced-decision.png)

## Comparaison des fonctionnalités des méthodes de création

Le tableau suivant présente une comparaison détaillée des fonctionnalités clés des différentes méthodes de création de formulaires AEM, afin de vous aider à sélectionner l’approche la plus adaptée à vos besoins.

| **Fonction** | **Éditeur universel (WYSIWYG)** | **Création basée sur des documents** | **Création de documents (DA)** |
|-----------------------------------------|-------------------------------|-----------------------------|-----------------------------|
| **Composition unifiée avec Sites** | ✅ |                              | ✅ (avec formulaires incorporés) |
| **Prise en charge des formulaires incorporés** | ✅ | ✅ | ✅ (intégration à partir de l’éditeur universel ou de documents) |
| **Règles (comportement dynamique)** | Éditeur de règles avancé avec fonctions personnalisées | Limitées : afficher/masquer, calculer la valeur, fonctions personnalisées | Dépend du formulaire incorporé |
| **Prise en charge des pièces jointes** | ✅ | ℹ️ (Accès anticipé) | Dépend du formulaire incorporé |
| **Prise en charge de CAPTCHA** | reCAPTCHA Enterprise | reCAPTCHA Enterprise | Dépend du formulaire incorporé |
| **Fonctionnalités d’envoi** | REST, E-mail, FDM, Workflow, SharePoint, OneDrive, Azure Blob, Power Automate, Workfront Fusion (EA) | Feuille de calcul uniquement | Suit la configuration du formulaire incorporé |
| **Schéma de données** | FDM, personnalisé | Personnalisé | Basé sur un formulaire incorporé |
| **Pré-remplissage** | 💡 (via l’assistant) | ✅ | Dépend du formulaire incorporé |
| **Fragments** | ✅ | ✅ | Dépend du formulaire incorporé |
| **Éditeur de règles visuel** | ✅ |                              |                              |
| **Localisation** | 💡 (via Sites) | ℹ️ (Excel/Sheets manual) | Dépend du formulaire incorporé |
| **Schéma de données (arborescence de données)** | 💡 (via l’extension d’interface utilisateur) |                              |                              |
| **Prise en charge de modèles** | Only Initial Content |                              |                              |
| **Portail** |                               |                              |                              |
| **Thème** | ℹ️ (au niveau du projet) | ℹ️ (au niveau du projet) | ℹ️ (basé sur le site d’hébergement) |
| **Composant personnalisé** | ✅ | ✅ | ✅ (si le composant incorporé le prend en charge) |
| **Fonctions prêtes à l’emploi et personnalisées** | ✅ | ✅ | ✅ (dans un formulaire incorporé) |
| **Référence du fragment** |                               |                              |                              |
| **Intégration de Sign** |                               |                              |                              |
| **Expérimentation** | ✅ | ✅ | Dépend du contexte d’intégration |
| **Gestion des tâches via Workfront** | ✅ |                              |                              |
| **Extension personnalisée** | 💡 |                              |                              |
| **Personnalisation de l’éditeur** | ✅ (via l’extension d’interface utilisateur) |                              |                              |
| **Action Envoyer** | ✅ | Feuille de calcul uniquement | Basé sur un formulaire incorporé |

<!--

## Best Practices for Creating Forms

Building great forms goes beyond just the technology. Here's how to ensure your forms are user-friendly and achieve their goals:

* **Designing User-Friendly and Accessible Forms**

  *   **Use Clear, Visible Labels:** Every form field needs a `<label>`. Don't rely only on placeholder text (text inside the input field), as it disappears when users type and is bad for accessibility.
        *   *Good:* `<label for="email">Email Address:</label> <input type="email" id="email" placeholder="you@example.com">`
        *   *Bad:* `<input type="email" placeholder="Email Address">`
  *   **Keep it Simple:** Use standard HTML input types (`<input type="date">`, `<input type="tel">`) where possible. They often have better mobile support and accessibility than complex custom widgets.
  *   **Logical Order and Grouping:** Arrange fields in a way that makes sense to the user. Group related fields together using `<fieldset>` and `<legend>`.
  *   **Provide Clear Instructions:** For any fields that might be confusing, offer concise help text or tooltips.
  *   **Keyboard Navigation:** Ensure users can navigate through your entire form using only the keyboard (Tab, Shift+Tab, Enter, Spacebar).
  *   **Error Handling:** Make errors obvious and easy to correct. Display error messages next to the relevant field and explain what needs to be fixed.

* **Ensuring Your Forms Load Quickly and Are Visible**

  *   **Place Forms Prominently:** If a form is important, make sure users can see it easily without too much scrolling ("above the fold" if possible). Adobe's research shows many forms get low interaction because they are hidden.
  *   **Optimize Assets:** Keep any custom JavaScript or CSS for your forms as small as possible to ensure fast load times. Edge Delivery Services helps with the base page load, but heavy form scripts can still slow things down.

* **Handling User Data Responsibly**
  *   **Ask Only What You Need:** The less Personal Identifiable Information (PII) you ask for, the better. Every field is a potential reason for a user to abandon the form.
  *   **Be Transparent:** Clearly explain *why* you need certain information and *how it will be used*. Link to your privacy policy. This builds trust.

* **Improving User Experience: Captcha Alternatives**

  * **Rethink Visible Captchas:** Those "type the wavy text" or "click all the traffic lights" tests can be very frustrating for users, especially those with disabilities, and often lead to high drop-off rates.

*   **Consider Alternatives:**
    *   **Honeypot Fields:** Add a hidden field that only bots would fill out. If it has data, the submission is likely spam.
    *   **Time-Based Checks:** Measure how quickly a form is submitted. Submissions that are too fast are often bots.
    *   **Invisible reCAPTCHA (v3):** This Google service analyzes user behavior in the background and only presents a challenge if the user seems suspicious. This is often a much better user experience.

**Form Design Do's and Don'ts**

```mermaid
    graph LR
subgraph GoodFormUX [Do ✅ - For Better Forms]
    direction LR
    ClearLabels[Use Visible <label> Tags for All Fields]
    SimpleInputs[Prefer Standard HTML Input Types]
    KeyboardNav[Ensure Full Keyboard Navigation]
    ClearErrors[Show Clear, Actionable Error Messages]
    MinimalPII[Ask Only for Necessary Information]
    TransparentUse[Explain How Data is Used - Privacy Info]
    InvisibleCaptcha[Use Invisible or Behavioral CAPTCHA]
    ProminentPlacement[Make Form Easy to Find on Page]
end

subgraph BadFormUX [Don't ❌ - Avoid These]
    direction LR
    PlaceholderOnly[Only Use Placeholder Text for Labels]
    ComplexWidgets[Use Overly Complex Custom Widgets]
    PoorErrors[Vague or Missing Error Messages]
    ExcessivePII[Request Excessive Personal Data]
    VisibleHardCaptcha[Use Hard-to-Solve Visible CAPTCHAs]
    HiddenForm[Hide the Form Deep in the Page]
end

style GoodFormUX fill:#e6ffe6,stroke:#333
style BadFormUX fill:#ffe6e6,stroke:#333
```

## Quick Decision Guide: Choosing the Right Form Strategy

Let's bring it all together to help you decide on the best approach for your forms.

*   **Matching Form Features to Your Project Goals**
    *   **For speed and simplicity with basic data capture (to spreadsheets/email):** Document-Based Authoring with the Forms Submission Service is often your fastest route.
    *   **For visually rich forms with potential for AEM backend integration:** Universal Editor is your tool. You can start with the Forms Submission Service for simple needs and scale to full AEM Publish submissions for complex workflows.
    *   **If your site content is managed in Document Authoring (DA):** You'll create forms using one of the above methods and then embed them into your DA pages. The submission logic will be tied to how the original embedded form was configured.-->

Pour tirer parti de ce que vous avez appris, voici comment aller de l’avant :

[Choisissez votre stratégie d’envoi](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md) décidez si votre projet nécessite la simplicité du service d’envoi de Forms (idéal pour la sortie par feuille de calcul/e-mail) ou la flexibilité et l’intégration du serveur principal offertes par les actions d’envoi de l’instance de publication AEM.

Reportez-vous à l’article [ Bonnes pratiques pour la création de Forms ](/help/edge/docs/forms/universal-editor/best-pratices-eds-forms.md) pour savoir comment concevoir des formulaires efficaces, accessibles et conviviaux.

## Étapes suivantes

Ce guide présente un aperçu de l’utilisation de forms avec AEM Edge Delivery Services. Pour obtenir des instructions détaillées sur les configurations spécifiques, reportez-vous à la documentation Adobe Experience Manager officielle :

* [Création basée sur des documents avec Edge Delivery Services Forms](/help/edge/docs/forms/tutorial.md)
* [Éditeur universel avec Edge Delivery Services Forms](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
* [Création de documents (DA) et incorporation de contenu](https://www.aem.live/developer/da-tutorial)
* [Service de soumission AEM Forms](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md)


<!-- 
# Edge Delivery Services for AEM Forms
 

Edge Delivery Services for AEM Forms is a composable set of services that enables a rapid development environment where authors can update, publish, and launch new forms rapidly. These services deliver exceptional and high impact forms experiences that drive engagement and conversions. These forms experiences are easy to author and develop.

These services enable you to:

* **Create enrolment experiences with tools of your choice:** Increase authoring efficiency by decoupling content sources. Out of the box you can use Document-based Authoring (Microsoft SharePoint or Google Drive), WYSIWYG Authoring (Universal Editor or Adaptive Forms Editor). You can work with multiple content sources on the same forms site and use your preferred authoring tools, such as Microsoft Excel, Google Sheets, Universal Editor, or Adaptive Forms Editor.

* **Deliver exceptional Digital Enrolment experiences:** Deliver Digital Enrolment experiences that load and render quickly and continuously monitor your forms performance through Operational Telemetry. Faster loading times and optimized user experience contribute to higher form completion and conversion rates. 

* **Use developer friendly toolset:** Edge Delivery Services for AEM Forms
 uses plain HTML, modern CSS, and vanilla JavaScript to create exceptional experiences, avoiding the steep learning curve of a specific framework. A developer with basic web development skills can customize and easily build form components and experiences. There is no need to wait for a pipeline to run, just check-in your code into GitHub and your changes are live.

## Edge Delivery Services for AEM Forms Overview {#edge-overview}

Edge Delivery Services for AEM Forms allows for a high degree of flexibility in how you author forms on your website. You can author content and forms with [WYSIWYG Authoring](/help/forms/creating-adaptive-form-core-components.md) as well as [Document-based Authoring](/help/edge/docs/forms/create-forms.md). Edge Delivery Services for AEM Forms
 provide a forms block, known as [Adaptive Forms Block](/help/edge/docs/forms/create-forms.md) to add a form to your Edge Delivery Services site.

For example, you author forms directly in Microsoft Excel or Google Sheets and these spreadsheets are transformed into forms for your website. Any new form or form content, such as a new form field, is instantly available on your website without requiring a rebuild process.

The following diagram illustrates how you can edit forms in Microsoft Excel or Google Sheets (Document-based Authoring) and publish to Edge Delivery Services. It also shows the AEM publishing method using the WYSIWYG Authoring (Universal Editor or Adaptive Forms Editor).

![Publish to Edge Delivery Services and AEM](/help/edge/docs/forms/assets/AEM-forms-with-EDS-publishing.png)

Edge Delivery Services for AEM Forms uses GitHub so customers can manage and deploy code directly from their GitHub repository. For example, you can write forms in either [Google Sheets](/help/edge/docs/forms/create-forms.md) or [Microsoft Excel](/help/edge/docs/forms/create-forms.md) and the components of your forms can be developed by using CSS and JavaScript in a GitHub repository.

When your forms are ready, you can use the [AEM Sidekick](/help/edge/docs/forms/tutorial.md#preview-and-publish-your-content), a chrome browser extension, to preview and publish content updates.

![Install AEM SideKick](/help/edge/assets/aem-sidekick-preview-publish-forms.png)

The choice between the [Document-based Authoring ](#document-based-authoring-features) and [WYSIWYG Authoring](#wysiwyg-authoring-features) depends on your specific requirements:

* For simple forms that just collect basic information with a few fields (think contact us forms, lead generation forms, or service request forms), and where you need quick data connectivity using a spreadsheet, the [Document-based Authoring](#document-based-authoring-features) is a good fit. You can build these forms like you would build a document in Google Sheets or Microsoft Excel. 

* For complex forms, like forms requiring multiple panels, complex rules and business logic, data manipulation, integration with external systems, or streamlined workflows using AEM features, then [WYSIWYG Authoring](#wysiwyg-authoring-features) is a better option. 


### Key Features of Document-based Authoring and WYSIWYG Authoring

Document-based Authoring offers a basic set of features and WYSIWYG Authoring unlocks additional capabilities beyond the Document-based Authoring, empowering you to build more complex and interactive forms. The key features of both Document-based Authoring and WYSIWYG Authoring are:

#### Document-based Authoring features

Document-based Authoring  allows you to create forms using familiar tools like Microsoft Excel or Google Sheets. These forms offer the following functionalities:

* Accessible components for a user-friendly experience.
* Standardized HTML structure for consistent rendering.
* Rules and validations to ensure data accuracy.
* File attachment options for collecting additional information.
* Google reCAPTCHA integration for spam protection.
* Ability to create custom form components for specific needs.
* Submit form data directly to Microsoft Excel or Google Sheets or email addresses.
* Monitor your forms performance through Operational Telemetry

#### WYSIWYG Authoring features

WYSIWYG Authoring provides WYSIWYG interfaces (Universal Editor and Adaptive Forms Editor) for building forms and offers all the capabilities of Document-based Authoring, plus a wide range of additional features:

* Advanced rules editor for creating complex logic.
* Server-side extensibility for custom functionalities.
* WYSIWYG editing experience for easy form creation and visualization.
* Document of record functionality to create tamper-proof archives of submitted data.
* Integration with Adobe Sign for electronic signatures.
* Integration with Adobe Workfront Fusion to triggering Adobe Workfront Fusion scenarios upon form submission.
* Integration with various data sources for pre-populating forms and submitting data.
* Form Data Model (FDM) for defining data structure and interactions with various data sources.
* Ability to choose from multiple submit actions for handling form submissions, including submitting data to Microsoft SharePoint, Microsoft OneDrive, Adobe Workfront Fusion, Salesforce, Microsoft Dynamics, many more data sources.

The all above features are also available via Adaptive Forms Editor. 

In essence, WYSIWYG Authoring (Universal Editor and [Adaptive Forms Editor](/help/forms/creating-adaptive-form-core-components.md)) builds upon the foundation of [Document-based Authoring](/help/edge/docs/forms/create-forms.md), providing a more advanced toolkit for creating and managing complex forms. 

>[!NOTE]
>
>
> The WYSIWYG Authoring capability is available under the early-adopter program. If you are interested, send a quick email from your work address to aem-forms-ea@adobe.com to request access to the capability.

### Edge Delivery Services for AEM Forms

: Authoring, Publishing, and Submission of Forms  

The following diagrams illustrate the process of creating, publishing, and submitting forms using Document-based Authoring and WYSIWYG Authoring.

![Document-based Authoring](/help/edge/assets/document-based-authoring-workflow.png)

![WYSIWYG Authoring](/help/edge/assets/wysiwyg-authoring-workflow.png)

## Start creating forms

* [Get started with Edge Delivery Services for AEM Forms](/help/edge/docs/forms/tutorial.md)
* [Create a form using Google Sheets or Microsoft Excel](/help/edge/docs/forms/create-forms.md)
* [Set up your Google Sheets or Microsoft Excel files to start accepting data​](/help/edge/docs/forms/submit-forms.md)
* [Publish your form and start collecting data](/help/edge/docs/forms/publish-forms.md)
* [Customize the look of your forms​](/help/edge/docs/forms/style-theme-forms.md)
* [Add repeatable sections to a form​](/help/edge/docs/forms/repeatable-forms.md)
* [Show a custom thank you message after form submission​](/help/edge/docs/forms/thank-you-page-form.md)
* [Adaptive Form Block components and their properties](/help/edge/docs/forms/form-components.md)
* [Real Use Monitoring](https://www.aem.live/developer/rum#authentication)

<!-- 

## Start creating forms

<div>

  <style>
    .card-container {
        width: calc(33.33% - 10px);;
        margin: 5px;
        border: 1px solid #ccc;
        border-radius: 5px;
        padding: 5px;
        box-sizing: border-box;
        transition: background-color 0.3s ease; /* Adding transition effect */
    }
    .card-container:hover {
        background-color: #f0f0f0; /* Changing background color on hover */
    }
</style>

<div style="display: flex; flex-wrap: wrap; justify-content: space-between; margin: -5px;">
    <div class="card-container">
        <a href="/help/edge/docs/forms/create-forms.md">
            <img src="/help/edge/assets/smock_devices_18_n.svg" alt="Create a form using Edge Delivery Services forms" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Create a form using Google Sheets or Microsoft Excel</b>
        </a>
        <p>Create forms that load and render quickly and automatically reflows on mobile devices.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/create-forms.md#manually-configure-a-spreadsheet-to-accept-data">   
            <img src="/help/edge/assets/smock_platformdatamapping_18_n.svg" alt="Submit form" alt="Use Form Fragments in an Edge Delivery Services Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Submit form to spreadsheet</b>
        </a>
        <p>Submit forms directly to your Microsoft Excel or Google Sheets.</p>
    </div>
     <div class="card-container">
        <a href="/help/edge/docs/forms/style-theme-forms.md">
            <img src="/help/edge/assets/smock_imageautomode_18_N.svg" alt="Apply styles or themes to an Edge Delivery Services form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Customize a theme</b>
        </a>
        <p>Create a consistent brand image by applying the same theme across forms.</p>
    </div>
      <div class="card-container">
        <a href="/help/edge/docs/forms/validate-forms.md">
            <img src="/help/edge/assets/smock_condition_18_n.svg" alt="Add validations to form fields" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Apply field validations</b>
        </a>
        <p>Reduce errors and frustration by checking form inputs for proper formatting.</p>
    </div> 
            <div class="card-container">
        <a href="/help/edge/docs/forms/rules-forms.md">
            <img src="/help/edge/assets/smock_documentfragment_18_n.svg" alt="Use rules to add dynamic behaviour to a form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Use rules to add dynamic behaviour to a form</b>
        </a>
        <p>Reuse preconfigured fragments across multiple forms.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/translate-forms.md">  
            <img src="/help/edge/assets/smock_abc_18_n.svg" alt="Translate an Edge Delivery Services Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Translate a form</b>
        </a>
        <p>Extend the reach of your forms while keeping costs in check.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/repeatable-forms.md">  
            <img src="/help/edge/assets/smock_addto_18_n.svg" alt="Add repeatable sections to an Edge Delivery Services Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Add repeatable sections</b>
        </a>
        <p>Effortlessly create and add repeatable sections to a form.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/custom-components-forms.md"> 
            <img src="/help/edge/assets/smock_userdeveloper_18_n.svg" alt="Create custom forms components using standard JavaScript and CSS"  style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Create custom components</b>
        </a>
        <p>Use standard JavaScript and CSS to create components and themes.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/recaptacha-forms.md">  
            <img src="/help//edge/assets/smock_keyclock_18_n.svg" alt="Use reCAPTCHA in an Edge Delivery Services Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Use reCAPTCHA</b>
        </a>
        <p>Use OOTB reCAPTCHA integration for robust spam and bot protection.</p>
    </div>


</div>


</br>


-->
