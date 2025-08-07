---
title: Comment créer des formulaires dans AEM ?
description: Découvrez les différentes plateformes de création de formulaires disponibles dans Adobe Experience Manager (AEM) et choisissez celle qui convient le mieux à vos besoins.
feature: Edge Delivery Services, Adaptive Forms, Core Components
role: User, Developer
exl-id: bd9cb623-c272-4cdf-ad39-f97043f781a6
hide: true
hidefromToC: true
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '1075'
ht-degree: 100%

---

# Comment créer des formulaires dans Adobe Experience Manager (AEM) ?

Adobe Experience Manager (AEM) offre une plateforme flexible permettant de créer des formulaires attrayants, réactifs, dynamiques et adaptatifs. Il repose sur une interface d’utilisation intuitive et un riche ensemble de composants prêts à l’emploi dédiés à la création et à la gestion de formulaires adaptatifs. Les formulaires peuvent être créés avec ou sans modèle de formulaire ou schéma, selon vos besoins.

## Points essentiels à prendre en compte lors du choix d’une plateforme de création

AEM propose plusieurs options de création de formulaires permettant de créer des formulaires interactifs et attrayants. Lors de la sélection d’un environnement de création de formulaires, tenez compte des facteurs suivants :

| 📝 **Remarque** | 💡 **Que demander** |
|----------------------|--------------------|
| **Expertise d’utilisation** | Qui sera responsable de la création des formulaires (équipe de développement, utilisateurs et utilisatrices professionnels, ou créateurs et créatrices de contenu) ? |
| **Complexité du formulaire** | Le formulaire a-t-il besoin de règles avancées, de sections dynamiques ou d’intégrations ? |
| **Besoins en matière de réutilisation** | Des parties du formulaire seront-elles réutilisées dans différents formulaires ou projets ? |
| **Flexibilité de la conception** | Avez-vous besoin d’une gestion totale de la mise en page, des thèmes et du style ? |
| **Exigences en matière d’intégration** | Le formulaire doit-il se connecter à des modèles de données, des workflows ou des systèmes externes ? |
| **Facilité d’utilisation** | La plateforme est-elle adaptée au niveau de compétence technique de votre équipe ? |
| **Performance et évolutivité** | Le formulaire sera-t-il utilisé à grande échelle ou dans des environnements à trafic élevé ? |
| **Diffusion omnicanal** | Le formulaire sera-t-il utilisé sur des sites web, des applications mobiles, des kiosques ou plusieurs canaux ? |
| **Flexibilité de publication** | Quelle est la destination de publication des formulaires sur AEM, Edge Delivery, et seront-ils publiés sur des applications personnalisées ? |

## Vue d’ensemble des méthodes de création de formulaires dans AEM

AEM prend en charge plusieurs méthodes de création, chacune adaptée aux différents besoins de chaque personne, aux niveaux de compétences techniques et aux destinations de publication.

- [Composants de base](/help/forms/create-adaptive-form-tutorial.md) : utilisez les composants de base pour créer des formulaires interactifs traditionnels. Idéal pour les formulaires qui s’intègrent à des systèmes hérités ou reposent sur des workflows établis de longue date. Les formulaires créées avec des composants de base peuvent uniquement être publiées sur AEM et ne sont pas compatibles avec Edge Delivery Services.

- [Composants principaux](/help/forms/creating-adaptive-form-core-components.md) : utilisez les composants principaux pour créer des formulaires modernes, réactifs et évolutifs. Ils prennent en charge la réutilisation et l’accessibilité, et offrent de meilleures performances. Les formulaires créés avec les composants principaux peuvent être publiés sur AEM et Edge Delivery Services, ce qui offre une plus grande flexibilité entre les plateformes.

- [Formulaires Edge Delivery Services](/help/edge/docs/forms/overview.md) : les formulaires Edge Delivery Services révolutionnent la création, l’exécution et le traitement des formulaires. Grâce à Edge Delivery Services, les entreprises peuvent créer des formulaires numériques rapides, sécurisés et hautement disponibles, afin d’améliorer l’expérience d’utilisation et l’efficacité opérationnelle dans un environnement de développement rapide. Vous pouvez créer les formulaires Edge Delivery Services de deux manières :
   - [Création WYSIWYG ](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) : utilisez l’éditeur universel pour la création visuelle de formulaires par glisser-déposer. Idéal pour les créateurs et créatrices de contenu ayant des connaissances techniques limitées. Les formulaires créées avec l’éditeur universel sont diffusées à l’aide d’Edge Delivery Services de façon à permettre un rendu rapide et léger.
   - [Création basée sur un document](/help/edge/docs/forms/tutorial.md) : utilisez des outils tels que Microsoft Excel ou Google Sheets pour définir la structure et le contenu des formulaires. Cette méthode est utile pour les utilisateurs et utilisatrices professionnels qui préfèrent les entrées basées sur une feuille de calcul. Ces formulaires sont généralement publiés par l’intermédiaire d’Edge Delivery Services et sont adaptés aux cas d’utilisation légers et volumineux.
- [Création découplée](https://experienceleague.adobe.com/fr/docs/experience-manager-headless-adaptive-forms/using/tutorial/build-engaging-forms-using-core-components-and-headless-adaptive-forms-aem-forms-cloud-service) : utilisez les API pour réaliser le rendu des formulaires au format JSON pour n’importe quel front-end, par exemple React, Angular, les applications mobiles ou les kiosques, sans dépendre d’AEM. Actuellement, seuls les composants principaux prennent en charge la diffusion découplée. Les formulaires découplés sont idéaux pour les cas d’utilisation omnicanal et sont utilisés indépendamment du rendu des pages d’AEM, ce qui les rend flexibles pour les déploiements front-end personnalisés.

### Analyse comparative des méthodes de création de formulaires AEM

Le tableau suivant présente une comparaison concise des différentes méthodes de création de formulaires AEM, en mettant en évidence les approches, les fonctionnalités, les options de publication et les cas d’utilisation idéaux pour vous aider à sélectionner la méthode la plus adaptée à vos besoins.

| **Considération** | **Composants de base** | **Composants principaux** | **Éditeur universel (WYSIWYG)** | **Création basée sur des documents** | **Création découplée** |
|--------------------------|---------------------------------------------------------------------|------------------------------------------------------------------------|-------------------------------------------------------------------------|---------------------------------------------------------------------------|-------------------------------------------------------------------------|
| **Idéal pour** | La conservation des formulaires et des workflows hérités dans AEM | Les formulaires évolutifs et modernes avec des workflows et des intégrations complexes | La création de formulaires pour les sites Edge Delivery Service avec des exigences complexes | Le prototypage rapide ou les formulaires de base sans services d’envoi avancés | Les expériences omnicanal sur les plateformes (web, mobiles, kiosques, etc.) |
| **Expertise d’utilisation** | Équipe de développement, créateurs et créatrices de contenu | Équipe de développement, créateurs et créatrices de niveau avancé | Utilisateurs et utilisatrices professionnels, créateurs et créatrices de contenu | Utilisateurs et utilisatrices professionnels | Développeurs et développeuses |
| **Complexité du formulaire** | Formulaires de base | Formulaires complexes avec sections dynamiques | Formulaires complexes avec actions personnalisées | Formulaires simples | Formulaires hautement complexes basés sur des API |
| **Flexibilité de conception** | Limitée | Élevée (personnalisation CSS/JS) | Modérée (sur la base de modèles) | Limitée | Élevée (gestion du framework front-end) |
| **Niveau d’intégration** | Workflows AEM de base | Avancé (modèles de données, workflows) | Intégration à des systèmes externes | De base (Google Sheets, Excel) | Contrôle complet via les API |
| **Méthode de publication** | Seulement AEM | AEM et Edge Delivery Services | Edge Delivery Services | Edge Delivery Services | Tout front-end via les API |
| **Performances et SEO** | Standard | Amélioration par rapport aux composants de base | Scores Google Lighthouse élevés pour un rendu plus rapide et un meilleur classement SEO | Scores Google Lighthouse élevés pour un rendu plus rapide et un meilleur classement SEO | Dépend de l’implémentation. |
| **Diffusion omnicanal** | Limitée | Modérée | Modérée | Limitée | Élevée |

<!--
| **Form authoring methods** | **Key Approach** | **Features** | **Publishing Method** | **Use Cases** |
|-----------------------------|------------------|--------------|-----------------------|---------------|
| **Foundation Components** | Classic AEM authoring interface designed for standard web pages. | Includes basic components like text, images, tables, and charts. Limited reuse capabilities and primarily web-based. | Published on AEM only. | Best for maintaining legacy forms and workflows within AEM. |
| **Core Components** | Provides a modern, flexible approach with high customization capabilities. | Component-based authoring within AEM, offering high customization with CSS and JS. Built around accessibility guidelines and integrated with AEM Sites. | Published on AEM and Edge Delivery Services. | Suitable for scalable, modern forms with complex workflows and integrations. |
| **Universal Editor (WYSIWYG)** | Offers a WYSIWYG interface for intuitive form creation. | Forms are designed using an intuitive drag-and-drop interface. These forms inherit look and feel from the configured Edge Delivery Services GitHub repository for the corresponding form. | Published on Edge Delivery Services, achieving high Google Lighthouse scores for faster rendering and better SEO. | Ideal for creating forms for Edge Delivery Service sites and pages, especially scenarios involving complex forms, workflows, custom actions, or integrations with external systems. |
| **Document-based Authoring** | Uses familiar tools like Google Docs and Microsoft Office for form creation. | Forms are designed using spreadsheets, with data directly submitted to Google Sheets or Microsoft Excel. These forms are faster to create and deploy. No prior knowledge of AEM is required to develop custom components and styles for these forms. | Published on Edge Delivery Services, achieving high Google Lighthouse scores for faster rendering and better SEO. | Ideal for quick prototyping or basic forms where advanced submission services are not needed. Well-suited for surveys, registration, or feedback forms requiring data storage in spreadsheets. |
| **Headless Authoring** | Enables API-driven content creation for omnichannel delivery. | Full control via frontend frameworks, allowing content delivery across various platforms through APIs. | Can be integrated with any frontend via APIs. | Ideal for omnichannel experiences across platforms, suitable for web, mobile, kiosks, and more. |-->

### Comparaison des fonctionnalités des méthodes de création de formulaires AEM

Le tableau suivant présente une comparaison détaillée des fonctionnalités clés des différentes méthodes de création de formulaires AEM, afin de vous aider à sélectionner l’approche la plus adaptée à vos besoins.

| **Fonction** | **Composants de base** | **Composants principaux** | **Éditeur universel (WYSIWYG)** | **Création basée sur des documents** | **Création découplée** |
|-----------------------------------------|---------------------------|---------------------|-------------------------------|-----------------------------|------------------------|
| **Composition unifiée avec Sites** | ❌ | ✅ | ✅ | ❌ | ❌ |
| **Prise en charge des formulaires incorporés** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Règles (comportement dynamique)** | Éditeur de règles avancé avec fonctions personnalisées | Éditeur de règles avancé avec fonctions personnalisées | Éditeur de règles avancé avec fonctions personnalisées | Limitées : afficher/masquer, calculer la valeur, fonctions personnalisées | Limitées : nécessite une implémentation personnalisée. |
| **Prise en charge des pièces jointes** | ✅ | ✅ | ✅ | ℹ️ (Accès anticipé) | ❌ |
| **Prise en charge de CAPTCHA** | reCAPTCHA v2/Enterprise, hCaptcha (EA), Turnstile (EA) | reCAPTCHA v2/Enterprise, hCaptcha (EA) | reCAPTCHA Enterprise | reCAPTCHA Enterprise | Nécessite une intégration personnalisée. |
| **Fonctionnalités d’envoi** | Point d’entrée REST, e-mail, modèle de données de formulaire (FDM), appel d’un workflow AEM, SharePoint, OneDrive, stockage Azure Blob, Power Automate, Workfront Fusion (EA) | Point d’entrée REST, e-mail, modèle de données de formulaire (FDM), appel d’un workflow AEM, SharePoint, OneDrive, stockage Azure Blob, Power Automate, Workfront Fusion (EA) | Point d’entrée REST, e-mail, modèle de données de formulaire (FDM), appel d’un workflow AEM, SharePoint, OneDrive, stockage Azure Blob, Power Automate, Workfront Fusion (EA) | Feuille de calcul uniquement | Points d’entrée d’API personnalisés |
| **Schéma de données** | FDM, personnalisé | FDM, personnalisé | FDM, personnalisé | Personnalisé | Personnalisé |
| **Pré-remplissage** | ✅ | ✅ | 💡 (via l’assistant) | ✅ | Implémentation personnalisée |
| **Fragments** | ✅ | ✅ | ✅ | ✅ | ❌ |
| **Éditeur de règles visuel** | ✅ | ✅ | ✅ | ❌ | ❌ |
| **Localisation** | ✅ | ✅ | 💡 (via Sites) | ℹ️ (Excel - Manuel, Fonction Google Sheets) | Implémentation personnalisée |
| **Schéma de données (arborescence de données)** | ✅ | ✅ | 💡 (via l’extension d’UI) | ❌ | Implémentation personnalisée |
| **Prise en charge de modèles** | ✅ | ✅ | Contenu initial uniquement, pas de stratégie | ❌ | Implémentation personnalisée |
| **Portail** | ✅ | ✅ | ❌ | ❌ | ❌ |
| **Création de document de référence** | ✅ | ✅ | 💡 (via Derlina) | ❌ | ❌ |
| **Génération de document de référence** | ✅ | ✅ | 💡 (FORMS-2475 Nouveau) | ❌ | ❌ |
| **Thème** | ✅ | ✅ | ℹ️ (au niveau du projet) | ℹ️ (au niveau du projet) | Implémentation personnalisée |
| **Composant personnalisé** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Fonctions prêtes à l’emploi et personnalisées** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Référence du fragment** | ✅ | ❌ | ❌ | ❌ | ❌ |
| **Intégration de Sign** | ✅ | ❌ | ❌ | ❌ | ❌ |
| **Prise en charge de RTL** | ❌ | ✅ | 💡 | 💡 | Implémentation personnalisée |
| **Expérimentation** | ❌ | ❌ | ✅ | ✅ | Implémentation personnalisée |
| **Gestion des tâches via Workfront** | ❌ | ❌ | ✅ | ❌ | ❌ |
| **Extension personnalisée** | ❌ | ❌ | 💡 | ❌ | Implémentation personnalisée |
| **Personnalisation de l’éditeur** | ❌ | ❌ | ✅ (via l’extension d’UI) | ❌ | Implémentation personnalisée |
| **Action Envoyer** | ✅ | ✅ | ✅ | Feuille de calcul uniquement | Implémentation personnalisée |


## Article connexe

- [Création basée sur des documents à l’aide de Microsoft Excel ou de Google Sheets](/help/edge/docs/forms/create-forms.md)
- [Éditeur universel pour la création WYSIWYG](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/authoring)
- [Créer un formulaire adaptatif (composants de base)](/help/forms/creating-adaptive-form.md)
- [Créer un formulaire adaptatif (composants principaux)](/help/forms/create-an-adaptive-form.md)
