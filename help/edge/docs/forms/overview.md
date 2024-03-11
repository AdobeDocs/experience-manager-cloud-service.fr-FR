---
title: Présentation des Edge Delivery Services AEM Forms
description: Les Edge Delivery Services AEM Forms conçus pour des performances optimales vous permettent d’envisager l’avenir de la collecte de données rationalisée et de l’engagement des utilisateurs.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
source-git-commit: 67d9eaaf18725403f6a152b04e022cdca6902de0
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 2%

---

# Edge Delivery Services AEM Forms

AEM Forms Edge Delivery Services est un ensemble de services composable qui permet un environnement de développement rapide dans lequel les auteurs peuvent rapidement mettre à jour et publier, et où les nouveaux formulaires sont lancés rapidement.

AEM Forms Edge Delivery Services offre des expériences de formulaires exceptionnelles qui stimulent l’engagement et les conversions et permettent des expériences à fort impact qui sont faciles à créer et à développer.

Ces services permettent d’effectuer les opérations suivantes :

* **Créez des expériences d’inscription avec les outils de votre choix :** Augmentez l’efficacité de la création en découplant les sources de contenu. Vous pouvez utiliser la création basée sur des documents (Microsoft SharePoint ou Google Drive) et la création AEM (Adaptive Forms Editor). Ainsi, vous pouvez utiliser plusieurs sources de contenu sur le même formulaire et utiliser vos outils de création préférés, tels que Microsoft Excel, Google Sheets ou Adaptive Forms Editor.

* **Offrir des expériences d’inscription numérique exceptionnelles :** Proposez des expériences d’inscription numérique qui se chargent et s’affichent rapidement. Des temps de chargement plus rapides et une expérience utilisateur optimisée contribuent à des taux de remplissage et de conversion plus élevés du formulaire.

* **Utilisez l’ensemble d’outils destiné aux développeurs :** AEM Forms utilise du HTML brut, du code CSS moderne et du code JavaScript vanille pour créer des expériences exceptionnelles, en évitant la courbe d’apprentissage détaillée d’une structure spécifique. Un développeur disposant de compétences de développement web de base peut personnaliser et créer facilement des composants de formulaire et des expériences. Il n’est pas nécessaire d’attendre l’exécution d’un pipeline. Il vous suffit d’archiver votre code dans Github pour que vos modifications soient en ligne.

## Présentation des Edge Delivery Services AEM Forms {#edge-overview}

Le diagramme suivant illustre comment modifier des formulaires dans Microsoft Excel ou Google Sheets (modification basée sur des documents) et les publier dans des Edge Delivery Services. Il affiche également la méthode de publication AEM à l’aide de l’éditeur de Forms adaptatif.

![Architecture d’Edge Delivery.](/help/edge/assets/AEM-forms-with-EDS-publishing.png)

AEM Forms Edge Delivery Services est un ensemble de services composables qui offre une grande flexibilité quant à la manière dont vous créez des formulaires sur votre site web. Vous pouvez utiliser AEM gestion de contenu avec [Création AEM](/help/forms/creating-adaptive-form-core-components.md) ainsi que [création basée sur des documents](/help/edge/docs/forms/create-forms.md).

Par exemple, vous créez des formulaires directement dans Microsoft Excel ou Google Sheets et ces feuilles de calcul sont transformées en formulaires pour votre site web. Tout nouveau contenu de formulaire, tel qu’un nouveau champ de formulaire, est instantanément disponible sur votre site web sans qu’un processus de reconstruction ne soit nécessaire.

Edge Delivery Services utilise GitHub afin que les clientes et les clients puissent gérer et déployer du code directement à partir de leur référentiel GitHub. Par exemple, vous pouvez écrire des formulaires dans : [Google Sheets ou Microsoft Excel](/help/edge/docs/forms/create-forms.md) et les composants de vos formulaires peuvent être développés en utilisant CSS et JavaScript dans GitHub. Lorsque vous êtes prêt, vous pouvez utiliser la variable [AEM Sidekick](/help/edge/docs/forms/tutorial.md#preview-and-publish-your-content) extension de navigateur pour prévisualiser et publier les mises à jour de contenu.

![Installer AEM Sidekick](/help/edge/assets/install-aem-sidekick.png)

AEM Forms Edge Delivery Services fournit un bloc de formulaires, appelé [Bloc Forms adaptatif](/help/edge/docs/forms/create-forms.md) pour ajouter un formulaire à votre site d’Edge Delivery Services.

Le choix entre [création basée sur des documents](#document-based-authoring-features) et [Création AEM](#aem-authoring-features) dépend de vos besoins spécifiques.

Pour les formulaires simples qui collectent des informations de base comme des noms et des courriers électroniques (pensez à nous contacter par des formulaires, des formulaires de génération de prospects ou des formulaires de demande de service), et où vous n’avez besoin que des données pour accéder à une feuille de calcul, la variable [Création basée sur des documents](/help/edge/docs/forms/create-forms.md) est parfaite. Vous pouvez créer ces formulaires comme vous le feriez avec un document dans les documents Google.

Si vos formulaires deviennent plus complexes, par exemple s’ils nécessitent plusieurs panneaux, des règles complexes et une logique métier, une manipulation de données, une intégration à des systèmes externes ou des workflows rationalisés à l’aide des fonctionnalités d’AEM, [Création AEM](/help/forms/creating-adaptive-form-core-components.md) est une meilleure option.


### Fonctions clés de la création basée sur les documents et de la création AEM

La création basée sur les documents offre un ensemble de fonctionnalités de base et AEM création déverrouille des fonctionnalités supplémentaires au-delà de la création basée sur les documents, ce qui vous permet de créer des formulaires interactifs et plus complexes. Les principales fonctionnalités de la création basée sur les documents et de la création AEM sont les suivantes :

<!-- 

>[!BEGINTABS]

>[!TAB Document-based authoring]

Document-based authoring is a versatile option suitable for creating simple forms with essential functionalities. It allows you to integrate various input types like text fields, dropdown menus, and radio buttons, enabling you to collect user data effectively. It offers a basic version of rules to add dynamic behaviour to forms. Key features of Document-based authoring are: 

* **[HTML5-based Form Field components](/help/edge/docs/forms/form-components.md)**: AEM Forms Edge Delivery Services allow you to create user-friendly and interactive forms using form components based on HTML5 [input types](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types), <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea">textarea</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">select</a>, and <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset</a>  elements. These components cater to different types of data collection and can be easily customized to fit your specific needs.  

* **Accessibility**: The fields in the form block are accessible. Each label is linked with its respective input element, and IDs are auto-generated for linking. Descriptions associated with fields are linked via the aria-describedby attribute. Keyboard navigation using the standard Tab/Shift + Tab keys is supported.

* **[Styling](/help/edge/docs/forms/style-theme-forms.md)**: Each form field has a fixed HTML structure that can be easily decorated using custom CSS or JavaScript files. Selectors for targeting fields in CSS and JS are provided based on type and name. You can easily create new selectors due to the standradized structure and style your form. 

* **Basic Rules**: Easily create logic that adjusts field visibility, validation, and behavior based on user input or predefined conditions. Rules offer a flexible and intuitive way to add intelligence to your forms, ensuring they adapt seamlessly based on user inputs.

* **Validations**: Before submission, the form is validated, and invalid fields are appropriately marked with error messages displayed to the user. Adaptive Forms Block support all the HTML form validation, supported by modern browsers, and provide additional validation mechanism like validation script, file size, file type, overall file size, and more. 

* **File Uploads**: You can add file attachment capabilities to your forms. Whether you need to gather documents, images, or other files from your users, file upload functionality serves you effortlessly. With custom handling options available, you can tailor the file upload process to suit your specific requirements.

* **reCAPTCHA**: Benefit from seamless integration of Google reCAPTCHA into your forms with our out-of-the-box (OOTB) support. Safeguard your forms against fraudulent activities, spam, and abuse, while maintaining a smooth and uninterrupted user experience. Adaptive Forms Block supports reCaptcha V3 and reCaptcha Enterprise. 

* **Send email notification on form submission**: Eliminate the hassle of manual follow-ups and ensure timely communication with our built-in email automation for form submissions. This integrated solution lets you effortlessly notify relevant parties, including sending form data, whenever someone fills out a form on your website. No need for complex configurations or additional tools – it's ready to use out of the box.

>[!TAB AEM Authoring]

AEM Authoring unlocks additional capabilities beyond the document-based authoring, empowering you to build more complex and interactive forms. In additon to the features of Document-based authoring, AEM authoring offers the following additional features:  

* Advanced Rules: Define logic-based actions within your forms. You can use rules to conditionally show or hide form sections, pre-populate fields based on user input, and perform various validations to ensure data integrity.

* Server-side extensibility: Extend the functionalities of your forms by integrating them with server-side logic. This allows you to perform complex calculations, interact with external systems, and automate specific tasks based on user actions within the form.
* Streamline workflows and data management: Leverage the power of AEM to:
    * Design user-friendly forms using AEM editors.
    * Generate a "Document of Record" for secure and tamper-proof archiving of submitted data.
    * Facilitate e-signing with Adobe Sign for a smooth and secure signing experience.
    * Automate business processes through AEM workflows, triggering actions based on form submissions.
    * Effortlessly integrate with various data sources, enabling seamless data flow and exchange.

>[!ENDTABS]



## Start creating forms

-->

#### Fonctionnalités de création basées sur des documents

La création basée sur les documents vous permet de créer des formulaires à l’aide d’outils familiers tels que Microsoft Excel ou Google Sheets. Ces formulaires offrent les fonctionnalités suivantes :

* Composants accessibles pour une expérience conviviale.
* Structure de HTML normalisée pour un rendu cohérent.
* Règles et validations pour garantir la précision des données.
* Options de pièce jointe pour la collecte d’informations supplémentaires.
* Intégration de Google reCAPTCHA pour la protection anti-spam.
* Possibilité de créer des composants de formulaire personnalisés pour des besoins spécifiques.
* Envoyez les données de formulaire directement à Microsoft Excel ou Google Sheets ou à des adresses électroniques.

#### AEM Fonctionnalités de création

AEM Création (à l’aide de l’éditeur de Forms adaptatif) fournit une interface WYSIWYG pour la création de formulaires et offre toutes les fonctionnalités de la création basée sur les documents, ainsi qu’un large éventail de fonctionnalités supplémentaires :

* Éditeur de règles avancé pour créer une logique complexe.
* Extensibilité côté serveur pour les fonctionnalités personnalisées.
* Expérience d’édition WYSIWYG pour une création et une visualisation de formulaire simples.
* Fonctionnalité de document d’enregistrement pour créer des archives de données envoyées à l’épreuve des modifications.
* Intégration à Adobe Sign pour les signatures électroniques.
* Intégration à Adobe Workfront Fusion pour déclencher des scénarios de fusion Adobe Workfront lors de l’envoi du formulaire.
* Intégration à différentes sources de données pour préremplir les formulaires et envoyer des données.
* Modèle de données de formulaire pour définir la structure des données et les interactions avec diverses sources de données.
* Possibilité de configurer plusieurs actions d’envoi pour gérer les envois de formulaire, y compris envoyer des données à Microsoft SharePoint, Microsoft OneDrive, Adobe Workfront Fusion, Salesforce, Microsoft Dynamics, et bien plus de sources de données.

Essentiellement, la création d’AEM s’appuie sur les bases de la création basée sur les documents, ce qui offre une boîte à outils plus avancée pour la création et la gestion de formulaires complexes.

### Workflow de création

![Création basée sur des documents](/help/edge/assets/document-based-authoring-workflow.png)

![Création AEM](/help/edge/assets/aem-authoring-workflow.png)


## Commencer à créer des formulaires

* [Prise en main des Edge Delivery Services AEM Forms](/help/edge/docs/forms/tutorial.md)
* [Création d’un formulaire à l’aide de feuilles de calcul Google ou de Microsoft Excel](/help/edge/docs/forms/create-forms.md)
* [Configurez vos feuilles de calcul Google Sheets ou fichiers Excel Microsoft pour commencer à accepter les données &#x200B;](/help/edge/docs/forms/submit-forms.md)
* [Publier votre formulaire et commencer à collecter des données](/help/edge/docs/forms/publish-forms.md)
* [Personnalisation de l’aspect de vos formulaires &#x200B;](/help/edge/docs/forms/style-theme-forms.md)
* [Ajout de sections répétables à un &#x200B; de formulaire](/help/edge/docs/forms/repeatable-forms.md)
* [Afficher un message de remerciement personnalisé après l’envoi du formulaire &#x200B;](/help/edge/docs/forms/thank-you-page-form.md)
* [Composants de bloc de formulaire adaptatif et leurs propriétés](/help/edge/docs/forms/form-components.md)



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
            <img src="/help/edge/assets/smock_devices_18_n.svg" alt="Create a form using eds forms" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Create a form using Google Sheets or Microsoft Excel</b>
        </a>
        <p>Create forms that load and render quickly and automatically reflows on mobile devices.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/create-forms.md#manually-configure-a-spreadsheet-to-accept-data">   
            <img src="/help/edge/assets/smock_platformdatamapping_18_n.svg" alt="Submit form" alt="Use Form Fragments in an EDS Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Submit form to spreadsheet</b>
        </a>
        <p>Submit forms directly to your Microsoft Excel or Google Sheets.</p>
    </div>
     <div class="card-container">
        <a href="/help/edge/docs/forms/style-theme-forms.md">
            <img src="/help/edge/assets/smock_imageautomode_18_N.svg" alt="Apply styles or themes to an eds form" style="border-radius: 5px;"> </b>
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
            <img src="/help/edge/assets/smock_abc_18_n.svg" alt="Translate an EDS Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Translate a form</b>
        </a>
        <p>Extend the reach of your forms while keeping costs in check.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/repeatable-forms.md">  
            <img src="/help/edge/assets/smock_addto_18_n.svg" alt="Add repeatable sections to an EDS Form" style="border-radius: 5px;"> </b>
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
            <img src="/help//edge/assets/smock_keyclock_18_n.svg" alt="Use reCAPTCHA in an EDS Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Use reCAPTCHA</b>
        </a>
        <p>Use OOTB reCAPTCHA integration for robust spam and bot protection.</p>
    </div>


</div>


</br>


-->