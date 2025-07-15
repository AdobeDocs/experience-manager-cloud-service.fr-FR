---
title: Prise en main de Forms sur AEM Edge Delivery Services
description: Découvrez comment créer et diffuser des formulaires hautement performants sur Adobe Experience Manager Edge Delivery Services, en mettant l’accent sur l’approche de création de l’éditeur universel.
feature: Edge Delivery Services
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
role: Admin, Architect, Developer
source-git-commit: e1ead9342fadbdf82815f082d7194c9cdf6d799d
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 1%

---


# Prise en main de Forms sur AEM Edge Delivery Services

<span class="preview"> Il s’agit d’une fonctionnalité en version préliminaire disponible via notre <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=fr#new-features">canal de version préliminaire</a>. </span>

Adobe Experience Manager (AEM) Edge Delivery Services (EDS) vous permet de diffuser des expériences web extrêmement rapides et évolutives à partir de la périphérie. Ce guide explique **comment créer et publier des formulaires pour ces expériences** avec une hiérarchie de recommandations claire :

1. **Éditeur universel (UE) - Meilleur choix pour la plupart des équipes**
2. **Création basée sur des documents (documents/feuilles) - Idéal pour les formulaires rapides et simples**
3. **Création de documents (DA) - Utilisez pour incorporer des formulaires dans des pages créées par DA**

À la fin, vous pourrez choisir la bonne méthode de création, comprendre les options d’envoi et suivre les étapes suivantes pour les formulaires prêts pour la production.



## Choix d’une méthode de création

| Équipe et exigence | Méthode recommandée | Pourquoi |
|--------------------|--------------------|-----|
| Les marketeurs/concepteurs ont besoin de contrôle visuel, de logique conditionnelle ou d’intégrations AEM | **Éditeur universel** | Glisser-déposer, règles avancées, envois à FSS ou à l’instance de publication AEM |
| Auteurs de contenu travaillant déjà dans Word/Google Docs/Sheets ; capture simple de données dans une feuille de calcul/un e-mail. | **Création basée sur des documents** | Outils familiers, chemin d’accès le plus rapide pour les formulaires de base |
| Pages de site web créées dans **Document Authoring (DA)** | **Incorporer** un formulaire UE ou basé sur un document dans la page DA | DA ne crée pas de formulaires lui-même |


## Méthodes de création en détail

### Éditeur universel

L’éditeur universel est un outil de création visuel par glisser-déposer destiné aux marketeurs et aux concepteurs qui associe vitesse et puissance de niveau professionnel :

* Modification du WYSIWYG en temps réel et aperçu des appareils.
* Règles avancées et interface utilisateur de validation : aucun code requis.
* Intégration directe à des ressources, des workflows et un modèle de données de formulaire (FDM) AEM.
* Transmission transparente aux développeurs et développeuses de composants personnalisés en JS/CSS classique.
* Cibles d’envoi flexibles : commencez simplement avec le **service de soumission Forms (FSS)** ou passez aux **actions d’envoi de publication AEM** au fur et à mesure de l’évolution de vos besoins.

> **Recommandation** : démarrez chaque nouveau projet de formulaire avec l’éditeur universel, sauf si votre équipe est axée à 100 % sur les documents et que le formulaire est très basique.


### Création Basée Sur Des Documents (Documents/Feuilles)

La création basée sur des documents est idéale pour créer des formulaires simples et peu complexes à l’aide d’outils familiers tels que Microsoft Word, Google Docs ou Google Sheets. Cette méthode est idéale pour les équipes de contenu qui ont besoin d’une méthode rapide et simple pour créer des formulaires.

* Définissez des champs de formulaire dans un tableau (documents) ou sous forme de lignes (feuilles).
* Prend en charge la validation de champ de base et Google reCAPTCHA pour la protection contre le spam.
* Les envois de formulaires sont gérés exclusivement par le biais du service d’envoi Forms.
* Publication instantanée : toutes les modifications apportées au document source sont immédiatement répercutées sur le site sans nécessiter de pipeline de déploiement.


### Incorporation de Forms dans la création de documents (DA)

La création de documents est conçue pour créer du contenu de page structuré et ne prend pas en charge la création de formulaires natifs. Pour ajouter un formulaire à une page créée par DA, procédez comme suit :

1. Créez le formulaire à l’aide de l’**Éditeur universel** (recommandé) ou de la création basée sur des documents.
2. Publiez le formulaire pour générer une URL unique (par exemple, `/forms/contact-us`).
3. Dans votre page DA, insérez un bloc **Incorporer le formulaire** et spécifiez l’URL du formulaire publié.

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

1. **Commencer avec l’éditeur universel :** consultez le [guide de prise en main de l’éditeur universel](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) pour commencer à créer des formulaires.
2. **Configurer l’envoi de formulaire :** sélectionnez et configurez la méthode d’envoi souhaitée. Reportez-vous à la section [Service de soumission de Forms](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md) ou Actions de soumission de publication AEM pour obtenir des instructions de configuration.
3. **Appliquer les bonnes pratiques :** passez en revue [les bonnes pratiques de conception de formulaire](/help/edge/docs/forms/universal-editor/best-practices-eds-forms.md) pour garantir l’accessibilité et les performances.
4. **Utiliser la création basée sur des documents :** pour créer des formulaires avec Microsoft Excel ou Google Sheets, suivez le tutoriel [Création basée sur des documents](/help/edge/docs/forms/tutorial.md).
5. **Incorporer Forms dans la création de documents :** si vous créez des pages dans la création de documents, consultez le tutoriel [DA](https://www.aem.live/developer/da-tutorial) pour obtenir des instructions sur l’incorporation de formulaires publiés.

> **Vous êtes maintenant prêt à créer votre premier formulaire hautes performances avec AEM Edge Delivery Services.**