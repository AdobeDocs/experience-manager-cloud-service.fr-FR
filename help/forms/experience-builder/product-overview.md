---
title: Créateur d’expériences de formulaires
description: Créer des formulaires performants plus rapidement à l’aide de fragments de formulaire
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Developer
exl-id: 183e999c-9896-49a2-b29b-7c77da380df9
source-git-commit: 1d378e6c8ac714779e77314d3457a14d40cd222f
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 32%

---

# Vue d’ensemble

AEM Forms Experience Builder tire parti de Generative AI pour accélérer la création de formulaires numériques au moyen du langage naturel. Cet outil puissant permet aux utilisateurs techniques et non techniques de concevoir, modifier et optimiser des formulaires de qualité professionnelle à l’aide d’une interface simple et conversationnelle.

Forms Experience Builder permet la création rapide de formulaires par le biais de l’IA conversationnelle tout en permettant aux utilisateurs non techniques de créer des formulaires sophistiqués sans connaissances en codage. Vous pouvez concevoir des mises en page complexes, implémenter des règles de validation et configurer des actions d’envoi par le biais de commandes de conversation simples.

## Fonctionnalités principales

Forms Experience Builder propose deux workflows principaux pour créer des formulaires numériques puissants :

### Création de formulaires optimisée par l’IA

**Génération de formulaires en langage naturel**

Créez des formulaires complets à partir de zéro à l’aide de descriptions simples en anglais. Il vous suffit de décrire vos besoins, tels que « Crée un formulaire de commentaires client avec des échelles de notation et des champs de commentaire. », et le créateur d’expériences de formulaires génère la structure de formulaire appropriée. Vous utilisez le créateur d’expériences des éditeurs visuels pour ajouter des champs, des règles de validation et une logique d’envoi.

**Gestion dynamique des champs**

Ajoutez, modifiez ou supprimez des champs de formulaire par le biais de commandes de conversation. L’IA comprend le contexte et peut suggérer intelligemment des types de champs, des règles de validation et des améliorations de l’interface d’utilisation en fonction de vos besoins.

**Optimisation de la mise en page**

Mettez à jour les mises en page et configurations de formulaire via le langage naturel. Demandez des modifications telles que « Modifie la disposition du formulaire dans la disposition de l’assistant » et le créateur d’expériences de formulaire appliquera le style et les ajustements de disposition appropriés.

### Import et conversion intelligents

Transformer des documents existants en expériences digitales interactives. Forms Experience Builder prend en charge divers formats, analysant le contenu chargé pour détecter les types de champ, conserver les dispositions et améliorer les formulaires grâce à une conception réactive et une logique avancée. Les formats pris en charge sont les suivants :

- **Acroforms** : PDF forms interactif avec structures de champ existantes
- **PDF XFA** : architectures de formulaires complexes basées sur XML
- **PDF plats** : documents statiques convertis en formulaires interactifs
- **Images et captures d’écran** : JPG, formats PNG
- **Formulaires manuscrits** : esquisses et photographies de formulaires papier


## Démonstration de Forms Experience Builder {#forms-experience-builder-demo}

>[!VIDEO](https://video.tv.adobe.com/v/3463164/)

## Intégration et conditions préalables

Forms Experience Builder est actuellement disponible via un programme d’accès anticipé. Pour demander l’accès, envoyez un e-mail à [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) à partir de votre ID d’e-mail officiel.

Experience Builder nécessite un environnement de création de production AEM Forms as a Cloud Service avec des [composants principaux de Forms adaptatif](/help/forms/enable-adaptive-forms-core-components.md).

## Accèder au Forms Experience Builder


1. Accédez à **AEM > Forms > Forms et documents**.
1. Cliquez sur **Créer** puis sélectionnez **Formulaire adaptatif**
1. Utilisez l’Assistant pour créer un formulaire à l’aide d’un modèle [Composants principaux](/help/forms/creating-adaptive-form-core-components.md) ou [Edge Delivery Services](/help/edge/docs/forms/universal-editor/create-forms.md), selon vos besoins, et ouvrez le formulaire pour le modifier.
1. Sélectionnez l’icône **Forms Experience Builder** dans la barre d’outils de l’éditeur pour ouvrir l’interface de Forms Experience Builder afin de créer des formulaires en langage naturel.


| ![Éditeur Forms adaptatif - Forms Experience Builder](/help/edge/docs/forms/assets/adaptive-forms-editor.gif "Éditeur Forms adaptatif - Forms Experience Builder") | ![Éditeur universel - Forms Experience Builder](/help/forms/assets/ue-forms-experience-builder.gif "Éditeur universel - Forms Experience Builder") |
|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| *Éditeur de formulaires adaptatifs* | *Éditeur universel* |

<!-- >

## Learn more on key capabilities {#key-capabilities-forms-experience-builder}

<table>
<td>
   <a href="/help/forms/experience-builder/forms-experience-builder-getting-started.md">
   <img alt="Getting started with Forms Experience Builder" src="./assets/getting-started.png" />
   </a>
   <div>
      <a href="/help/forms/experience-builder/forms-experience-builder-getting-started.md">
      <strong>Getting started with Forms Experience Builder</strong>
      </a>
   </div>
   <p>
      <em>Learn the basics of creating your first form using AI-powered capabilities.</em>
   </p>
</td>

<td>
   <a href="/help/forms/experience-builder/forms-experience-builder-llm-smart-fields.md">
   <img alt="LLM-enhanced smart fields" src="./assets/llm-smart-fields.png" />
   </a>
   <div>
      <a href="/help/forms/experience-builder/forms-experience-builder-llm-smart-fields.md">
      <strong>LLM-enhanced smart fields</strong>
      </a>
   </div>
   <p>
      <em>Learn how to create fields with pre-populated options using AI knowledge base.</em>
   </p>
</td>

<td>
   <a href="/help/forms/experience-builder/forms-experience-builder-prompt-examples-library.md">
   <img alt="AI-powered form creation" src="./assets/ai-form-creation.png" />
   </a>
   <div>
      <a href="/help/forms/experience-builder/forms-experience-builder-prompt-examples-library.md">
      <strong>AI-powered form creation</strong>
      </a>
   </div>
   <p>
      <em>Learn how to utilize natural language to create and modify forms.</em>
   </p>
</td>
</table>

<table>
<td>
   <a href="/help/forms/experience-builder/intelligent-import-conversion.md">
   <img alt="Intelligent import and conversion" src="./assets/intelligent-import.png" />
   </a>
   <div>
      <a href="/help/forms/experience-builder/intelligent-import-conversion.md">
      <strong>Intelligent import and conversion</strong>
      </a>
   </div>
   <p>
      <em>Learn how to transform existing documents into interactive digital forms</em>
   </p>
</td>

<td>
   <a href="/help/forms/experience-builder/form-submission-integration.md">
   <img alt="Form submission and integration" src="./assets/form-submission.png" />
   </a>
   <div>
      <a href="/help/forms/experience-builder/form-submission-integration.md">
      <strong>Form submission and integration</strong>
      </a>
   </div>
   <p>
      <em>Learn how to configure form submissions to integrate with your business systems.</em>
   </p>
</td>

<td>
   <a href="/help/forms/experience-builder/forms-experience-builder-frequently-asked-questions.md">
   <img alt="Forms Experience Builder frequently asked questions" src="./assets/faq-banner.jpg" />
   </a>
   <div>
      <a href="/help/forms/experience-builder/forms-experience-builder-frequently-asked-questions.md">
      <strong>Frequently asked questions</strong>
      </a>
   </div>
   <p>
      <em>Get responses to common questions about Forms Experience Builder capabilities and usage.</em>
   </p>
</td>
</table> -->



<!--
**Comprehensive Submit Action Configuration**

Configure form submissions to integrate with your existing business systems:

- **Email Integration**: Set up automated email notifications and confirmations
- **REST API Endpoints**: Connect to custom applications and services
- **Cloud Storage**: Integrate with Azure Blob Storage, SharePoint, and OneDrive
- **Workflow Automation**: Connect to Power Automate and Workfront Fusion
- **Marketing Platforms**: Direct integration with Marketo for lead management
- **AEM Workflows**: Leverage existing AEM workflow capabilities
-->


## Commencez à explorer

Voici quelques façons de commencer à explorer le créateur d’expérience Forms :

- **Créer des formulaires de manière incrémentielle** : commencez par un formulaire simple et ajoutez une complexité étape par étape. Par exemple, créez un formulaire de contact de base, puis ajoutez des règles de validation, du texte d’espace réservé et une logique conditionnelle. [En savoir plus](/help/forms/experience-builder/forms-experience-builder-prompt-examples-library.md#incremental-development-examples).

- **Créer des champs intelligents** : utilisez les connaissances de l’IA pour créer des champs avec des options préremplies contextuelles, telles qu’une liste déroulante de tous les pays, des principaux aéroports ou des intitulés de poste standard. [En savoir plus](/help/forms/experience-builder/forms-experience-builder-prompt-examples-library.md#llm-enhanced-smart-fields).

- **Implémenter une logique métier complexe** : définissez des règles conditionnelles qui affichent ou masquent des sections de formulaire en fonction des entrées de l’utilisateur. Par exemple, créez une règle qui affiche une section « Informations sur le conjoint » uniquement lorsque l’état civil d’un utilisateur est « Marié ». [En savoir plus](/help/forms/experience-builder/forms-experience-builder-prompt-examples-library.md#rule-creation--business-logic).

- **Intégration à vos systèmes** : configurez les envois de formulaire pour qu’ils se connectent à vos workflows métier existants, qu’il s’agisse d’envoyer des données à une API REST, de créer un nouveau prospect dans votre CRM ou d’enregistrer des documents dans le stockage cloud. [En savoir plus](/help/forms/experience-builder/forms-experience-builder-prompt-examples-library.md#data-integration--submission).

<!-- ## Onboarding

The Forms Experience Builder is currently available through an Early Access Program. To request access, follow these steps:

1. **Gather your information**: You will need the following details:
    - IMS Organization ID
    - Program ID
    - Project Details (timeline, scope, use cases)
    - Your Official Work Email

   If you need help finding your IMS Organization ID and Program ID, refer to the [Adobe Experience Cloud Organization Setup Guide](/help/onboarding/cloud-manager-introduction.md) and the [Program and Environment Management](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) documentation.

2. **Send an access request**: Email [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) with all the information gathered in the previous step. 

    Access to the Forms Experience Builder is limited and subject to approval based on program capacity and alignment with early access criteria. 

## Getting started

To get started with the Forms Experience Builder, visit the [Forms Experience Builder documentation](/help/forms/experience-builder/forms-experience-builder-getting-started.md).

-->
