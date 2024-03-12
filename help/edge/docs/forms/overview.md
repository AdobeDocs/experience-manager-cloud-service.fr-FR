---
title: Présentation des Edge Delivery Services AEM Forms
description: Les Edge Delivery Services AEM Forms conçus pour des performances optimales vous permettent d’envisager l’avenir de la collecte de données rationalisée et de l’engagement des utilisateurs.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
source-git-commit: bae9a5178c025b3bafa8ac2da75a1203206c16e1
workflow-type: tm+mt
source-wordcount: '989'
ht-degree: 0%

---

# Edge Delivery Services AEM Forms

AEM Forms Edge Delivery Services est un ensemble de services composable qui permet un environnement de développement rapide dans lequel les auteurs peuvent rapidement mettre à jour, publier et lancer de nouveaux formulaires. Ces services offrent des expériences de formulaires exceptionnelles et à fort impact qui favorisent l’engagement et les conversions. Ces expériences de formulaires sont faciles à créer et à développer.

Ces services permettent d’effectuer les opérations suivantes :

* **Créez des expériences d’inscription avec les outils de votre choix :** Augmentez l’efficacité de la création en découplant les sources de contenu. Vous pouvez utiliser la création basée sur les documents (lecteur Microsoft SharePoint ou Google) et la création AEM (éditeur de Forms adaptatif). Vous pouvez utiliser plusieurs sources de contenu sur le même site de formulaires et utiliser vos outils de création préférés, tels que Microsoft Excel, Google Sheets ou Adaptive Forms Editor.

* **Offrir des expériences d’inscription numérique exceptionnelles :** Proposez des expériences d’inscription numérique qui se chargent et s’affichent rapidement. Des temps de chargement plus rapides et une expérience utilisateur optimisée contribuent à des taux de remplissage et de conversion plus élevés du formulaire.

* **Utilisez l’ensemble d’outils destiné aux développeurs :** AEM Forms Edge Delivery Services utilise du HTML brut, du code CSS moderne et du code JavaScript vanille pour créer des expériences exceptionnelles, en évitant la courbe d’apprentissage détaillée d’une structure spécifique. Un développeur disposant de compétences de développement web de base peut personnaliser et créer facilement des composants de formulaire et des expériences. Il n’est pas nécessaire d’attendre l’exécution d’un pipeline. Il vous suffit d’archiver votre code dans GitHub pour que vos modifications soient activées.

## Présentation des Edge Delivery Services AEM Forms {#edge-overview}

Les services de diffusion Edge d’AEM Forms offrent une grande flexibilité quant à la manière dont vous créez des formulaires sur votre site web. Vous pouvez créer du contenu et des formulaires avec [Création AEM](/help/forms/creating-adaptive-form-core-components.md) ainsi que [Création basée sur des documents](/help/edge/docs/forms/create-forms.md). Les Edge Delivery Services AEM Forms fournissent un bloc de formulaires, appelé [Bloc Forms adaptatif](/help/edge/docs/forms/create-forms.md) pour ajouter un formulaire à votre site d’Edge Delivery Services.

Par exemple, vous créez des formulaires directement dans Microsoft Excel ou Google Sheets et ces feuilles de calcul sont transformées en formulaires pour votre site web. Tout nouveau contenu de formulaire ou de formulaire, tel qu’un nouveau champ de formulaire, est instantanément disponible sur votre site web sans qu’un processus de reconstruction ne soit nécessaire.

Le diagramme suivant illustre la manière dont vous pouvez modifier des formulaires dans Microsoft Excel ou Google Sheets (création basée sur un document) et les publier dans des Edge Delivery Services. Il affiche également la méthode de publication AEM à l’aide de l’éditeur de Forms adaptatif (création AEM).

![Architecture d’Edge Delivery.](/help/edge/assets/AEM-forms-with-EDS-publishing.png)

AEM Forms Edge Delivery Services utilise GitHub pour permettre aux clients de gérer et déployer le code directement à partir de leur référentiel GitHub. Par exemple, vous pouvez écrire des formulaires dans : [Google Sheets](/help/edge/docs/forms/create-forms.md) ou [Microsoft Excel](/help/edge/docs/forms/create-forms.md) et les composants de vos formulaires peuvent être développés en utilisant CSS et JavaScript dans un référentiel GitHub.

Lorsque vos formulaires sont prêts, vous pouvez utiliser la variable [AEM Sidekick](/help/edge/docs/forms/tutorial.md#preview-and-publish-your-content), une extension de navigateur Chrome, pour prévisualiser et publier des mises à jour de contenu.

![Installer AEM Sidekick](/help/edge/assets/aem-sidekick-preview-publish-forms.png)

Le choix entre [Création basée sur des documents](#document-based-authoring-features) et [Création AEM](#aem-authoring-features) dépend de vos besoins spécifiques :

* Pour les formulaires simples qui ne collectent que des informations de base avec quelques champs (pensez à nous contacter par exemple, des formulaires de génération de pistes ou des formulaires de demande de service), et pour lesquels vous avez besoin d’une connectivité aux données rapide à l’aide d’une feuille de calcul, la variable [Création basée sur des documents](#document-based-authoring-features) est un bon ajustement. Vous pouvez créer ces formulaires comme vous le feriez pour créer un document dans Google Sheets ou Microsoft Excel.

* Pour les formulaires complexes, tels que les formulaires qui nécessitent plusieurs panneaux, des règles complexes et une logique métier, la manipulation de données, l’intégration à des systèmes externes ou des processus simplifiés à l’aide de fonctionnalités d’AEM, [Création AEM](#aem-authoring-features) est une meilleure option.


### Fonctions clés de la création basée sur les documents et de la création AEM

La création basée sur les documents offre un ensemble de fonctionnalités de base et AEM création déverrouille des fonctionnalités supplémentaires au-delà de la création basée sur les documents , ce qui vous permet de créer des formulaires interactifs et plus complexes. Les principales fonctionnalités de la création basée sur les documents et de la création AEM sont les suivantes :

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

AEM Authoring fournit une interface WYSIWYG (Adaptive Forms Editor) pour la création de formulaires et offre toutes les fonctionnalités de la création basée sur les documents, ainsi qu’un large éventail de fonctionnalités supplémentaires :

* Éditeur de règles avancé pour créer une logique complexe.
* Extensibilité côté serveur pour les fonctionnalités personnalisées.
* Expérience d’édition WYSIWYG pour une création et une visualisation de formulaire simples.
* Fonctionnalité de document d’enregistrement pour créer des archives de données envoyées à l’épreuve des modifications.
* Intégration à Adobe Sign pour les signatures électroniques.
* Intégration à Adobe Workfront Fusion pour déclencher des scénarios de fusion Adobe Workfront lors de l’envoi du formulaire.
* Intégration à différentes sources de données pour préremplir les formulaires et envoyer des données.
* Modèle de données de formulaire pour définir la structure des données et les interactions avec diverses sources de données.
* Possibilité de choisir parmi plusieurs actions d’envoi pour gérer les envois de formulaire, y compris envoyer des données à Microsoft SharePoint, Microsoft OneDrive, Adobe Workfront Fusion, Salesforce, Microsoft Dynamics, et bien plus de sources de données.

Essentiellement, [Création AEM](/help/forms/creating-adaptive-form-core-components.md) s&#39;appuie sur les principes fondamentaux de [Création basée sur des documents](/help/edge/docs/forms/create-forms.md), fournissant une boîte à outils plus avancée pour la création et la gestion de formulaires complexes.

>[!NOTE]
>
>
> La fonctionnalité de création d’AEM est disponible dans le cadre du programme d’adoption précoce. Si vous êtes intéressé, envoyez un email rapide à l’adresse aem-forms-ea@adobe.com pour demander l’accès à la fonctionnalité.

### Edge Delivery Services AEM Forms : création. Publication et envoi de Forms

Les diagrammes suivants illustrent le processus de création, de publication et d’envoi de formulaires à l’aide de la création et de la création AEM basées sur des documents.

![Création basée sur des documents ](/help/edge/assets/document-based-authoring-workflow.png)

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