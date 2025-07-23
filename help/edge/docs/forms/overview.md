---
title: Vue d’ensemble d’Edge Delivery Services pour AEM Forms
description: Créez et diffusez des formulaires hautement performants sur Adobe Experience Manager Edge Delivery Services, en mettant l’accent sur l’approche de création utilisant l’éditeur universel.
feature: Edge Delivery Services
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
role: Admin, Architect, Developer
source-git-commit: 37b20a97942f381b46ce36a6a3f72ac019bba5b7
workflow-type: ht
source-wordcount: '890'
ht-degree: 100%

---


# Edge Delivery Services pour AEM Forms


Edge Delivery Services pour AEM Forms constitue un ensemble de services composable qui permet un environnement de développement rapide où les auteurs et les autrices peuvent mettre à jour, publier et lancer de nouveaux formulaires rapidement. Ces services offrent des expériences de formulaires exceptionnelles et à fort impact qui favorisent l’engagement et les conversions. Ces expériences de formulaires sont faciles à créer et à développer.

Ces services permettent d’effectuer les opérations suivantes :

* **Créer des expériences d’inscription avec les outils de votre choix :** augmentez l’efficacité de la création en découplant les sources de contenu. Vous pouvez utiliser la création basée sur des documents (Microsoft SharePoint ou Google Drive) et la création WYSIWYG (éditeur universel ou éditeur de formulaires adaptatifs). Vous pouvez utiliser plusieurs sources de contenu sur le même site de formulaires et utiliser vos outils de création préférés, tels que Microsoft Excel, Google Sheets, l’éditeur unversel ou l’éditeur de formulaires adaptatifs.

* **Offrir des expériences d’inscription numérique exceptionnelles :** proposez des expériences d’inscription numérique qui se chargent et génèrent leur rendu rapidement, et surveillez en permanence les performances de vos formulaires grâce à la télémétrie opérationnelle. Des temps de chargement plus rapides et une expérience client optimisée contribuent à des taux d’achèvement de formulaire et de conversion plus élevés.

* **Utiliser l’ensemble d’outils destiné à l’équipe de développement :** Edge Delivery Services pour AEM Forms utilise du HTML brut, du code CSS moderne et du code Vanilla JavaScript pour créer des expériences exceptionnelles, en évitant la courbe abrupte d’apprentissage d’un framework spécifique. Une personne chargée du développement disposant de compétences de développement web de base peut personnaliser et créer facilement des composants de formulaire et des expériences. Il n’est pas nécessaire d’attendre l’exécution d’un pipeline. Il vous suffit d’enregistrer votre code dans GitHub pour que vos modifications soient appliquées.

## Choix d’une méthode de création


Adobe Experience Manager (AEM) Edge Delivery Services (EDS) vous permet de diffuser des expériences web extrêmement rapides et évolutives à partir du serveur Edge. Ce guide explique **comment créer et publier des formulaires pour ces expériences**, avec une hiérarchie de recommandations précise :

* **Éditeur universel (UE) - Le meilleur choix pour la plupart des équipes**
* **Création basée sur des documents (documents/feuilles) - Idéal pour des formulaires rapides et simples**
* **Création de documents (DA) - À utiliser pour incorporer des formulaires dans des pages créées via DA**

Après avoir lu le guide, vous pourrez choisir la bonne méthode de création, comprendre les options d’envoi et suivre les étapes ultérieures pour les formulaires prêts pour la production.


| Équipe et recrutement | Méthode recommandée | Pourquoi ? |
|--------------------|--------------------|-----|
| Les personnes spécialistes du marketing et de la conception doivent pouvoir disposer d’un contrôle visuel, d’une logique conditionnelle ou d’intégrations AEM. | **Éditeur universel** | Glisser-déposer, règles avancées, envois à FSS ou à l’instance de publication AEM |
| Personnes créant du contenu et travaillant déjà dans Word/Google Docs/Sheets ; capture simple de données vers une feuille de calcul/un e-mail. | **Création basée sur des documents** | Outils familiers, chemin d’accès le plus rapide pour les formulaires de base |
| Pages de sites web élaborées dans la **création de documents (DA)** | **Incorporer** un formulaire UE ou basé sur un document dans la page DA | DA ne permet pas de créer de formulaires. |


## Méthodes de création en détail

### Éditeur universel

<span class="preview"> Il s’agit d’une fonctionnalité de version préliminaire accessible par le biais de notre <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features">canal de version préliminaire</a>. </span>

L’[Éditeur universel](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) est un outil visuel de création par glisser-déposer destiné aux personnes spécialistes du marketing et de la conception, qui associe vitesse et puissance de niveau professionnel :

* Modifications WYSIWYG en temps réel et prévisualisation des appareils.
* Intégration directe à des ressources, des workflows et un modèle de données de formulaire (FDM) d’AEM.
* Transmission transparente aux développeurs et développeuses de composants personnalisés en JS/CSS classique.
* Éditeur de règles avancé pour créer une logique complexe.
* Extensibilité côté serveur pour les fonctionnalités personnalisées.
* Expérience d’édition WYSIWYG pour une création et une visualisation de formulaire simples.
* Fonctionnalité de document d’enregistrement pour créer des archives inviolables de données envoyées.
* Intégration à Adobe Sign pour les signatures électroniques.
* Intégration à Adobe Workfront Fusion pour déclencher des scénarios Adobe Workfront Fusion lors de l’envoi du formulaire.
* Intégration à différentes sources de données pour préremplir les formulaires et envoyer des données.
* Modèle de données de formulaire (FDM) pour définir la structure des données et les interactions avec diverses sources de données.
* Possibilité de choisir parmi plusieurs actions d’envoi pour gérer les envois de formulaire, y compris envoyer des données à Microsoft SharePoint, Microsoft OneDrive, Adobe Workfront Fusion, Salesforce, Microsoft Dynamics, et de nombreuses autres sources de données.
* Envoyer à l’aide des actions d’envoi du service d’envoi de formulaires (FSS) ou de l’instance de publication AEM

**Recommandation** : démarrez chaque nouveau projet de formulaire avec l’éditeur universel, sauf si votre équipe est axée à 100 % sur les documents et que le formulaire est très basique.


### Création basée sur des documents (à l’aide de Microsoft Word ou de Google Sheets)

La [création basée sur des documents](/help/edge/docs/forms/tutorial.md) est idéale pour créer des formulaires peu complexes à l’aide d’outils familiers tels que Microsoft Word, Google Docs ou Google Sheets. Cette méthode convient parfaitement aux équipes de contenu qui ont besoin d’une méthode rapide et simple pour créer des formulaires.

* Composants accessibles pour une expérience conviviale.
* Structure HTML normalisée pour un rendu cohérent.
* Règles et validations pour garantir la précision des données.
* Options de fichier joint pour la collecte d’informations supplémentaires.
* Intégration de Google reCAPTCHA pour la protection contre les spams.
* Possibilité de créer des composants de formulaire personnalisés pour des besoins spécifiques.
* Envoi des données de formulaire directement à Microsoft Excel ou Google Sheets ou à des adresses e-mail.
* Surveiller les performances de vos formulaires grâce à la télémétrie opérationnelle


### Incorporer des formulaires dans la création de documents (DA)

La création de documents (DA) est conçue pour créer du contenu de page structuré et ne prend pas en charge la création de formulaires natifs. Pour ajouter un formulaire à une page produite par DA, vous pouvez créer le formulaire à l’aide de l’**éditeur universel** (recommandé) ou de la création basée sur des documents et l’incorporer à la page de création de documents.

## Publication de formulaires Edge Delivery Services {#edge-overview}

Le diagramme suivant illustre comment modifier des formulaires dans Microsoft Excel ou Google Sheets (création basée sur des documents) et les publier sur Edge Delivery Services. Il présente également la méthode de publication d’AEM à l’aide de la création WYSIWYG (éditeur universel).

![Publication sur Edge Delivery Services et AEM](/help/edge/docs/forms/assets/AEM-forms-with-EDS-publishing.png)


<!-- 
## Feature Comparison

| Capability | Universal Editor | Document-Based | Document Authoring |
|------------|-----------------|----------------|--------------------|
| Visual drag-and-drop | ✅ | – | – |
| Advanced rules editor | ✅ | Limited | – |
| Attachments | ✅ | EA | – |
| reCAPTCHA Enterprise | ✅ | ✅ | Depends on embed |
| Submit to spreadsheet/email | ✅ (FSS) | ✅ (FSS) | Via embed |
| Submit to AEM workflows/FDM | ✅ | – | Via UE embed |
| Custom components (JS/CSS) | ✅ | ✅ | Via embed |
| Localization via Sites | ✅ | Manual | Via embed |

-->

## Étapes suivantes

* [Fonctionnalités de l’éditeur universel d’Edge Delivery Services pour les formulaires](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
* [Créer votre premier formulaire à l’aide de l’éditeur universel](/help/edge/docs/forms/universal-editor/create-forms.md)
* [Créez votre premier formulaire à l’aide de Google Sheets ou de Microsoft Excel](/help/edge/docs/forms/tutorial.md).
* [Incorporer des formulaires dans la création de documents (DA)](https://www.aem.live/developer/da-tutorial?lang=fr)


Tout est maintenant prêt pour que vous puissiez créer votre premier formulaire performant avec AEM Edge Delivery Services.


<!-- 

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