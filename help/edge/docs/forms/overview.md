---
title: Vue d’ensemble d’AEM Forms Edge Delivery Services
description: Les services AEM Forms Edge Delivery Services sont conçus pour des performances optimales, vous permettant d’envisager l’avenir de la collecte de données et de l’interaction client rationalisées.
feature: Edge Delivery Services
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
role: Admin, Architect, Developer
source-git-commit: 5670e0ab7e6cb47bcc2dd7608aa3f01dc4ec0704
workflow-type: tm+mt
source-wordcount: '1043'
ht-degree: 99%

---

# AEM Forms Edge Delivery Services

Les services AEM Forms Edge Delivery Services constituent un ensemble de services composable qui permet un environnement de développement rapide où les auteurs et les autrices peuvent mettre à jour, publier et lancer de nouveaux formulaires rapidement. Ces services offrent des expériences de formulaires exceptionnelles et à fort impact qui favorisent l’engagement et les conversions. Ces expériences de formulaires sont faciles à créer et à développer.

Ces services permettent d’effectuer les opérations suivantes :

* **Créer des expériences d’inscription avec les outils de votre choix :** augmentez l’efficacité de la création en découplant les sources de contenu. Vous pouvez utiliser la création basée sur des documents (Microsoft SharePoint ou Google Drive) et la création WYSIWYG (éditeur universel ou éditeur de formulaires adaptatifs). Vous pouvez utiliser plusieurs sources de contenu sur le même site de formulaires et utiliser vos outils de création préférés, tels que Microsoft Excel, Google Sheets, l’éditeur unversel ou l’éditeur de formulaires adaptatifs.

* **Offrir des expériences d’inscription numérique exceptionnelles :** proposez des expériences d’inscription numérique qui se chargent et s’affichent rapidement et surveillez en permanence les performances de vos formulaires grâce à la surveillance de l’utilisation en temps réel (RUM). Des temps de chargement plus rapides et une expérience client optimisée contribuent à des taux d’achèvement de formulaire et de conversion plus élevés.

* **Utiliser l’ensemble d’outils destiné aux développeurs et développeuses :** AEM Forms Edge Delivery Services utilise du HTML brut, du code CSS moderne et du code Vanilla JavaScript pour créer des expériences exceptionnelles, en évitant la courbe abrupte d’apprentissage d’un framework spécifique. Une personne chargée du développement disposant de compétences de développement web de base peut personnaliser et créer facilement des composants de formulaire et des expériences. Il n’est pas nécessaire d’attendre l’exécution d’un pipeline. Il vous suffit d’enregistrer votre code dans GitHub pour que vos modifications soient appliquées.

## Vue d’ensemble d’AEM Forms Edge Delivery Services {#edge-overview}

Les services AEM Forms Edge Delivery Services offrent une grande flexibilité quant à la manière dont vous créez des formulaires sur votre site web. Vous pouvez créer du contenu et des formulaires avec la [création WYSIWYG](/help/forms/creating-adaptive-form-core-components.md) ainsi que la [création basée sur des documents](/help/edge/docs/forms/create-forms.md). AEM Forms Edge Delivery Services fournit un bloc de formulaires, appelé [bloc de formulaires adaptatifs](/help/edge/docs/forms/create-forms.md), pour ajouter un formulaire à votre site Edge Delivery Services.

Par exemple, vous créez des formulaires directement dans Microsoft Excel ou Google Sheets et ces feuilles de calcul sont transformées en formulaires pour votre site web. Tout nouveau formulaire ou contenu de formulaire, un nouveau champ de formulaire par exemple, est instantanément disponible sur votre site web sans qu’un processus de reconstruction ne soit nécessaire.

Le diagramme suivant illustre comment modifier des formulaires dans Microsoft Excel ou Google Sheets (création basée sur des documents) et les publier sur Edge Delivery Services. Il présente également la méthode de publication d’AEM à l’aide de la création WYSIWYG (éditeur universel ou éditeur de formulaires adaptatifs).

![Publication sur Edge Delivery Services et AEM](/help/edge/docs/forms/assets/AEM-forms-with-EDS-publishing.png)

Les services AEM Forms Edge Delivery Services utilisent GitHub afin que les clientes et les clients puissent gérer et déployer du code directement à partir de leur référentiel GitHub. Par exemple, vous pouvez écrire des formulaires dans [Google Sheets](/help/edge/docs/forms/create-forms.md) ou [Microsoft Excel](/help/edge/docs/forms/create-forms.md) et les composants de vos formulaires peuvent être développés à l’aide de CSS et de JavaScript dans un référentiel GitHub.

Lorsque vos formulaires sont prêts, vous pouvez utiliser [AEM Sidekick](/help/edge/docs/forms/tutorial.md#preview-and-publish-your-content), une extension de navigateur Chrome, pour prévisualiser et publier les mises à jour de contenu.

![Installation d’AEM Sidekick](/help/edge/assets/aem-sidekick-preview-publish-forms.png)

Le choix entre la [création basée sur des documents](#document-based-authoring-features) et la [création WYSIWYG ](#wysiwyg-authoring-features) dépend de vos besoins spécifiques :

* Pour les formulaires simples qui ne collectent que des informations de base avec quelques champs (les formulaires de contact, les formulaires de génération de leads ou les formulaires de demande de service, par exemple), et pour lesquels vous avez besoin d’une connectivité aux données rapide à l’aide d’une feuille de calcul, la [création basée sur des documents](#document-based-authoring-features) est le choix idéal. Vous pouvez créer ces formulaires comme vous le feriez pour créer un document dans Google Sheets ou Microsoft Excel.

* Pour les formulaires complexes, tels que les formulaires qui nécessitent plusieurs panneaux, des règles et une logique commerciale complexes, une manipulation de données, une intégration à des systèmes externes ou des workflows simplifiés à l’aide de fonctionnalités d’AEM, la [création WYSIWYG](#wysiwyg-authoring-features) est une meilleure option.


### Fonctionnalités clés de la création basée sur des documents et de la création WYSIWYG

La création basée sur des documents offre un ensemble de fonctionnalités de base et la création WYSIWYG déverrouille des fonctionnalités supplémentaires par rapport à la création basée sur des documents, ce qui vous permet de créer des formulaires plus complexes et interactifs. Les principales fonctionnalités de la création basée sur des documents et de la création WYSIWYG sont les suivantes :

#### Fonctionnalités de création basée sur des documents

La création basée sur des documents vous permet de créer des formulaires à l’aide d’outils familiers tels que Microsoft Excel ou Google Sheets. Ces formulaires offrent les fonctionnalités suivantes :

* Composants accessibles pour une expérience conviviale.
* Structure HTML normalisée pour un rendu cohérent.
* Règles et validations pour garantir la précision des données.
* Options de fichier joint pour la collecte d’informations supplémentaires.
* Intégration de Google reCAPTCHA pour la protection contre les spams.
* Possibilité de créer des composants de formulaire personnalisés pour des besoins spécifiques.
* Envoi des données de formulaire directement à Microsoft Excel ou Google Sheets ou à des adresses e-mail.
* Contrôler les performances de vos formulaires grâce à la surveillance de l’utilisation en temps réel (RUM).

#### Fonctionnalités de la création WYSIWYG

La création WYSIWYG fournit une interface WYSIWYG (éditeur universel et éditeur de formulaires adaptatifs) pour la création de formulaires et offre toutes les fonctionnalités de la création basée sur les documents, ainsi qu’un large éventail de fonctionnalités supplémentaires :

* Éditeur de règles avancé pour créer une logique complexe.
* Extensibilité côté serveur pour les fonctionnalités personnalisées.
* Expérience d’édition WYSIWYG pour une création et une visualisation de formulaire simples.
* Fonctionnalité de document d’enregistrement pour créer des archives inviolables de données envoyées.
* Intégration à Adobe Sign pour les signatures électroniques.
* Intégration à Adobe Workfront Fusion pour déclencher des scénarios Adobe Workfront Fusion lors de l’envoi du formulaire.
* Intégration à différentes sources de données pour préremplir les formulaires et envoyer des données.
* Modèle de données de formulaire (FDM) pour définir la structure des données et les interactions avec diverses sources de données.
* Possibilité de choisir parmi plusieurs actions d’envoi pour gérer les envois de formulaire, y compris envoyer des données à Microsoft SharePoint, Microsoft OneDrive, Adobe Workfront Fusion, Salesforce, Microsoft Dynamics, et de nombreuses autres sources de données.

Toutes les fonctionnalités ci-dessus sont également disponibles via l’éditeur de Forms adaptatif.

Essentiellement, la création WYSIWYG (éditeur universel et [éditeur de formulaires adaptatifs](/help/forms/creating-adaptive-form-core-components.md)) s’appuie sur les principes fondamentaux de la [création basée sur des documents](/help/edge/docs/forms/create-forms.md), fournissant une boîte à outils plus avancée pour la création et la gestion de formulaires complexes.

>[!NOTE]
>
>
> La fonctionnalité de création WYSIWYG est disponible dans le cadre du programme d’adoption précoce. Si cela vous intéresse, envoyez un e-mail à l’adresse aem-forms-ea@adobe.com à partir de votre adresse e-mail professionnelle pour demander l’accès à la fonctionnalité.

### AEM Forms Edge Delivery Services : création, publication et envoi de formulaires

Les diagrammes suivants illustrent le processus de création, de publication et d’envoi de formulaires à l’aide de la création basée sur des documents et de la création WYSIWYG.

![Création basée sur des documents](/help/edge/assets/document-based-authoring-workflow.png)

![Création WYSIWYG](/help/edge/assets/wysiwyg-authoring-workflow.png)

## Commencer à créer des formulaires

* [Prise en main d’AEM Forms Edge Delivery Services](/help/edge/docs/forms/tutorial.md)
* [Créer un formulaire à l’aide de Google Sheets ou de Microsoft Excel](/help/edge/docs/forms/create-forms.md)
* [Configurer vos fichiers Google Sheets ou Microsoft Excel pour accepter des données](/help/edge/docs/forms/submit-forms.md)
* [Publier votre formulaire et commencer à collecter des données](/help/edge/docs/forms/publish-forms.md)
* [Personnaliser l’apparence de vos formulaires](/help/edge/docs/forms/style-theme-forms.md)
* [Ajouter des sections répétables à un formulaire](/help/edge/docs/forms/repeatable-forms.md)
* [Afficher un message de remerciement personnalisé après l’envoi du formulaire](/help/edge/docs/forms/thank-you-page-form.md)
* [Composants de bloc de formulaire adaptatif et leurs propriétés](/help/edge/docs/forms/form-components.md)
* [Surveillance à usage réel](https://www.aem.live/developer/rum#authentication)

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