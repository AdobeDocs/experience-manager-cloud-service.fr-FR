---
title: Vue d’ensemble d’Edge Delivery Services pour AEM Forms
description: Découvrez comment utiliser Edge Delivery Services pour créer et diffuser des formulaires hautes performances avec AEM Forms, ce qui permet un développement rapide et une collecte de données rationalisée.
feature: Edge Delivery Services
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
role: Admin, Architect, Developer
source-git-commit: 1ddf97f56e5a9b7c95959da47a748f5a6d128e43
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 8%

---


# Edge Delivery Services pour AEM Forms


Edge Delivery Services pour AEM Forms constitue un ensemble de services composable qui permet un environnement de développement rapide où les auteurs et les autrices peuvent mettre à jour, publier et lancer de nouveaux formulaires rapidement. Ces services offrent des expériences de formulaires exceptionnelles et à fort impact qui favorisent l’engagement et les conversions. Ces expériences de formulaires sont faciles à créer et à développer.

* **Expériences plus rapides :** les Forms sont diffusés à partir d’un réseau de diffusion de contenu (CDN) global, ce qui garantit leur chargement rapide pour les utilisateurs et les utilisatrices.
* **Développement rapide :** un processus de développement rationalisé permet des mises à jour plus rapides. Les modifications peuvent être publiées sans attendre les longues versions de pipeline.
* **Création flexible :** faites votre choix parmi divers outils pour créer des formulaires, y compris la création basée sur des documents (Microsoft Word, Google Docs/Sheets) ou un éditeur visuel de WYSIWYG (éditeur universel).

## Fonctionnement

Avec Edge Delivery Services, la structure et le contenu de votre formulaire peuvent résider dans des sources telles qu’AEM as a Cloud Service, Microsoft SharePoint ou Google Drive. Ce contenu est publié sur un réseau CDN global. Lorsqu’un utilisateur visite votre site, le formulaire est diffusé directement à partir du serveur de réseau CDN Edge le plus proche pour des performances optimales.

![Diagramme d’architecture simplifié présentant les sources de contenu, un réseau CDN et l’utilisateur.](/help/forms/assets/eds-simplified-architecture.png)
**Architecture Edge Delivery Services simplifiée avec Forms**

Les données envoyées par les utilisateurs et utilisatrices peuvent être envoyées vers différentes destinations, d’une simple feuille de calcul à un puissant serveur principal AEM pour un traitement ultérieur.

## Choix d’une méthode de création

Vous pouvez créer des formulaires de plusieurs manières pour vos sites Edge Delivery Services. La meilleure méthode dépend des compétences de votre équipe, de la complexité du formulaire et des exigences de votre projet.

![Arborescence de décision pour vous aider à choisir une méthode de création de formulaire.](/help/forms/assets/eds-authoring-selection.png)
**Arborescence de décision de création de formulaire**

### Création basée sur des documents

Cette méthode vous permet de [créer des formulaires à l’aide de Microsoft Word ou Google Docs/Sheets](/help/edge/docs/forms/create-forms.md). Vous définissez des champs de formulaire, des libellés et des types dans un document à l’aide d’un format de tableau spécifique. Edge Delivery Services convertit ce document en formulaire HTML interactif.

**Fonctionnalités :**

* Créez dans des outils familiers : Word, Google Docs ou Google Sheets.
* Définissez des champs tels que des entrées de texte, des e-mails, des listes déroulantes, des cases à cocher et des boutons radio.
* Définissez des règles de validation de base, telles que les champs obligatoires.
* Intégrez Google reCAPTCHA pour la protection contre le spam.
* Prise en charge des chargements de fichiers.
* Envoyez directement les données à une feuille de calcul ou à une adresse e-mail.
* Étendez avec du code personnalisé via GitHub pour les composants avancés et le style.

**Idéal pour :**

* Les équipes qui utilisent principalement les éditeurs de document pour la création de contenu.
* Création rapide de formulaires simples à modérément complexes.
* Collecte simple de données dans une feuille de calcul ou un e-mail.

Les envois de formulaires basés sur des documents sont généralement gérés par le [service d’envoi AEM Forms](/help/forms/forms-submission-service.md), qui achemine les données vers une feuille de calcul ou une adresse e-mail configurée.

### Création avec l’éditeur universel

L’éditeur universel [ fournit une interface WYSIWYG moderne](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) qui permet de créer des formulaires avec une expérience de glisser-déposer.

**Fonctionnalités :**

* Créateur de formulaires visuel, par glisser-déposer avec une bibliothèque de composants préconfigurés.
* Configurez la validation en temps réel et une logique commerciale complexe (par exemple, afficher/masquer des champs en fonction des sélections d’utilisateurs et d’utilisatrices).
* Aperçu en direct pour différents appareils.
* Une intégration profonde avec les fonctionnalités d’AEM as a Cloud Service telles que les fragments de contenu, les workflows AEM et les autorisations utilisateur.
* Création et modification de formulaires assistées par l’IA via l’« Experience Builder ».

**Idéal pour :**

* Création de formulaires complexes avec une logique conditionnelle, des panneaux à plusieurs étapes ou une personnalisation.
* Les équipes (par exemple, les spécialistes marketing, les utilisateurs professionnels) qui préfèrent les outils visuels.
* Projets nécessitant une forte intégration avec le serveur principal AEM pour le traitement des données et les workflows.

Forms créé avec l’éditeur universel peut utiliser le service d’envoi [Forms](/help/forms/forms-submission-service.md) ou être configuré pour utiliser [les actions d’envoi fournies prêtes à l’emploi pour la gestion avancée des données](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md), telles que l’envoi de données à un workflow AEM, un point d’entrée REST ou une base de données.

### Incorporation de Forms dans les pages de création de documents

[La création de documents (DA)](https://www.aem.live/developer/da-tutorial) est un service hébergé par Adobe qui permet de gérer le contenu d’un site web pour Edge Delivery Services. Bien que DA ne soit pas lui-même un outil de création de formulaires, vous pouvez l’utiliser pour créer des pages web, puis incorporer des formulaires créés avec d’autres méthodes.

**Fonctionnement :**

1. **Créer le formulaire :** créez votre formulaire à l’aide de la création basée sur des documents ou de l’éditeur universel.
2. **Publier le formulaire :** assurez-vous que le formulaire est publié et accessible sur sa propre URL.
3. **Incorporer dans DA :** sur votre page de création de documents, ajoutez un bloc qui référence l’URL du formulaire pour l’incorporer.

Cette approche est destinée aux équipes qui utilisent la création de documents comme système de gestion de contenu principal pour les sites Edge Delivery Services.

## Comparaison des méthodes de création

| Critères | Création basée sur des documents | Éditeur universel (WYSIWYG) | Forms dans la création de documents (DA) |
|----------------------------------|---------------------------------------|-----------------------------------------|-------------------------------------------|
| **Outil de création de Principal** | Word/Google Docs/Sheets | Navigateur (éditeur universel d’AEM) | N/A (les Forms sont *incorporées*) |
| **Niveau de compétence de l’équipe** | Familiarisez-vous avec les éditeurs de document | Familiarisez-vous avec les outils web visuels | Utilise les données pour le contenu de la page |
| **Complexité standard des formulaires** | Simple à modérée | Modéré à complexe, de niveau entreprise | Dépend du formulaire incorporé |
| **Options d’envoi** | Service de soumission Forms (sur feuille/e-mail) | Service d’envoi de Forms, Publication AEM (workflow, modèle de données de formulaire, intégrations tierces) | Suit la configuration du formulaire incorporé |
| **Intégration du serveur principal AEM** | Minimal | Élevée (avec envoi de l’instance de publication AEM) | Indirectement, via le formulaire de l’éditeur universel incorporé |
| **Idéal Pour...** | Création rapide de formulaires simples par les équipes de contenu, capture rapide de données. | Spécialistes du marketing et utilisateurs professionnels ayant besoin d’un contrôle visuel, de formulaires complexes ou d’une intégration AEM approfondie. | Sites où le contenu principal est géré dans DA. |

<!-- 
## Detailed Feature Comparison

| **Capability**                        | **Universal Editor (WYSIWYG)** | **Document-based Authoring** | **Document Authoring (DA)** |
|-----------------------------------------|-------------------------------|-----------------------------|-----------------------------|
| **Unified Composition with Sites**    | ✅                            |                              | ✅ (with embedded forms)     |
| **Embedding Form Support**            | ✅                            | ✅                          | ✅ (embed from Universal Editor or Docs)   |
| **Rules (Dynamic Behavior)**          | Advanced rules editor with custom functions | Limited: Show/hide, compute value, custom functions | Depends on embedded form     |
| **Attachment Support**                | ✅                            | ℹ️ (Early Access)           | Depends on embedded form     |
| **CAPTCHA Support**                   | reCAPTCHA Enterprise          | reCAPTCHA Enterprise       | Depends on embedded form     |
| **Submission Features**               | REST, Email, FDM, Workflow, SharePoint, OneDrive, Azure Blob, Power Automate, Workfront Fusion (EA) | Only Spreadsheet            | Follows embedded form's setup |
| **Data Schema**                       | FDM, Custom                   | Custom                      | Based on embedded form       |
| **Pre-fill**                          | 💡 (via Wizard)               | ✅                          | Depends on embedded form     |
| **Fragments**                         | ✅                            | ✅                          | Depends on embedded form     |
| **Visual Rule Editor**                | ✅                            |                              |                              |
| **Localization**                      | 💡 (via Sites)                | ℹ️ (Excel/Sheets manual)    | Depends on embedded form     |
| **Template Support**                  | Only Initial Content          |                              |                              |
| **Theme**                             | ℹ️ (at project level)         | ℹ️ (at project level)        | ℹ️ (based on hosting site)    |
| **Custom Component**                  | ✅                            | ✅                          | ✅ (if embedded component supports it) |
| **Experimentation**                   | ✅                            | ✅                          | Depends on embed context     |
| **Submit Action**                     | ✅                            | Only Spreadsheet            | Based on embedded form       |
-->



## Étapes suivantes

* [Création d’un formulaire avec la création basée sur des documents](/help/edge/docs/forms/tutorial.md)
* [Découvrez l’éditeur universel pour Forms](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
* [Configurer les actions d’envoi de formulaire](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md)
* [En savoir plus sur la création de documents (DA)](https://www.aem.live/developer/da-tutorial)
