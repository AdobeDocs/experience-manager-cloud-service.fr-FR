---
title: Prise en main des formulaires sur AEM Edge Delivery Services
description: Découvrez comment créer et diffuser des formulaires hautement performants sur Adobe Experience Manager Edge Delivery Services, en mettant l’accent sur l’approche de création utilisant l’éditeur universel.
feature: Edge Delivery Services
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
role: Admin, Architect, Developer
source-git-commit: ccfb85da187e828b5f7e8b1a8bae3f483209368d
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 100%

---


# Prise en main des formulaires sur AEM Edge Delivery Services

<!--<span class="preview"> This is a pre-release feature available through our <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=fr#new-features">pre-release channel</a>. </span>-->

Adobe Experience Manager (AEM) Edge Delivery Services (EDS) vous permet de diffuser des expériences web extrêmement rapides et évolutives à partir du serveur Edge. Ce guide explique **comment créer et publier des formulaires pour ces expériences**, avec une hiérarchie de recommandations claire :

1. **Éditeur universel (UE) - Le meilleur choix pour la plupart des équipes**
2. **Création basée sur des documents (fichiers texte/feuilles de calcul) - Idéal pour des formulaires rapides et simples**
3. **Création de documents (DA) - Permet d’incorporer des formulaires dans des pages produites par DA**

Après avoir lu le guide, vous pourrez choisir la bonne méthode de création, comprendre les options d’envoi et suivre les étapes ultérieures pour les formulaires prêts pour la production.



## Choix d’une méthode de création

| Équipe et recrutement | Méthode recommandée | Pourquoi ? |
|--------------------|--------------------|-----|
| Les personnes spécialistes du marketing et de la conception doivent pouvoir disposer d’un contrôle visuel, d’une logique conditionnelle ou d’intégrations AEM. | **Éditeur universel** | Glisser-déposer, règles avancées, envois à FSS ou à l’instance de publication AEM |
| Personnes créant du contenu et travaillant déjà dans Word/Google Docs/Sheets ; capture simple de données vers une feuille de calcul/un e-mail. | **Création basée sur des documents** | Outils familiers, chemin d’accès le plus rapide pour les formulaires de base |
| Pages de site web élaborées dans la **création de documents (DA)** | **Incorporer** un formulaire UE ou basé sur un document dans la page DA | DA ne permet pas de créer de formulaires. |


## Méthodes de création en détail

### Éditeur universel

L’éditeur universel est un outil visuel de création par glisser-déposer destiné aux personnes spécialistes du marketing et de la conception, qui associe vitesse et puissance de niveau professionnel :

- Modifications WYSIWYG en temps réel et prévisualisation des appareils.
- Règles avancées et UI de validation : aucun code requis.
- Intégration directe à des ressources, des workflows et un modèle de données de formulaire (FDM) d’AEM.
- Transmission transparente aux développeurs et développeuses de composants personnalisés en JS/CSS classique.
- Cibles d’envoi flexibles : commencez simplement avec le **service d’envoi de formulaires (FSS)** ou passez aux **actions d’envoi de l’instance de publication AEM** au fur et à mesure de l’évolution de vos besoins.

> **Recommandation** : démarrez chaque nouveau projet de formulaire avec l’éditeur universel, sauf si votre équipe est axée à 100 % sur les documents et que le formulaire est très basique.


### Création basée sur des documents (fichiers texte/feuilles de calcul)

La création basée sur des documents est idéale pour créer des formulaires peu complexes à l’aide d’outils familiers tels que Microsoft Word, Google Docs ou Google Sheets. Cette méthode convient parfaitement aux équipes de contenu qui ont besoin d’une méthode rapide et simple pour créer des formulaires.

- Définissez des champs de formulaire dans un tableau (documents) ou sous forme de lignes (feuilles de calcul).
- Prend en charge la validation de champ de base et Google reCAPTCHA pour la protection contre le spam.
- Les envois de formulaires sont gérés exclusivement par le biais du service d’envoi de formulaires.
- Publication instantanée : toutes les modifications apportées au document source sont immédiatement répercutées sur le site sans nécessiter de pipeline de déploiement.


### Incorporer des formulaires dans la création de documents (DA)

La création de documents (DA) est conçue pour créer du contenu de page structuré et ne prend pas en charge la création de formulaires natifs. Pour ajouter un formulaire à une page créée par DA, procédez comme suit :

1. Créez le formulaire à l’aide de l’**Éditeur universel** (recommandé) ou de la création basée sur des documents.
2. Publiez le formulaire pour générer une URL unique (par exemple, `/forms/contact-us`).
3. Dans votre page DA, insérez un bloc **Incorporer le formulaire** et spécifiez l’URL du formulaire publié.

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

1. **Commencer avec l’éditeur universel :** consultez le [guide de prise en main de l’éditeur universel](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) pour commencer à créer des formulaires.
2. **Configurer l’envoi de formulaires :** sélectionnez et configurez la méthode d’envoi souhaitée. Pour obtenir des instructions de configuration, reportez-vous aux actions d’envoi du [service d’envoi de formulaires](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md) ou de l’instance de publication AEM.
3. **Appliquer les bonnes pratiques :** passez en revue [les bonnes pratiques de conception de formulaire](/help/edge/docs/forms/universal-editor/best-practices-eds-forms.md) pour garantir l’accessibilité et les performances.
4. **Utiliser la création basée sur des documents :** pour créer des formulaires avec Microsoft Excel ou Google Sheets, suivez le [tutoriel Création basée sur des documents](/help/edge/docs/forms/tutorial.md).
5. **Incorporer des formulaires dans la création de documents :** si vous élaborez des pages dans la création de documents, consultez le [tutoriel de DA](https://www.aem.live/developer/da-tutorial?lang=fr) pour obtenir des instructions sur l’incorporation de formulaires publiés.

> **Tout est maintenant prêt pour que vous puissiez créer votre premier formulaire hautement performant avec AEM Edge Delivery Services.**