---
title: 'Créateur de formulaires : choisissez votre approche'
description: Comparez les créateurs de formulaires et trouvez l’approche appropriée pour créer des formulaires adaptatifs. Que vous soyez un créateur de formulaires ayant besoin de modèles ou de créer des formulaires complexes, choisissez le créateur de formulaires le mieux adapté à vos besoins.
keywords: créateur de formulaires, AEM forms, créateur de formulaires, créer des formulaires, créateur de formulaires, formulaires adaptatifs, composants principaux, composants de base, services de diffusion edge, créer des formulaires
feature: Adaptive Forms, Core Components, Edge Delivery Services
role: User, Developer, Admin
level: Beginner
exl-id: choose-form-builder-guide
source-git-commit: ab84a96d0e206395063442457a61f274ad9bed23
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 9%

---


# Créateur de formulaires : choisissez votre approche {#choose-your-form-builder}

Adobe Experience Manager (AEM) Forms propose trois puissantes approches de création de formulaires, chacune conçue pour différents cas d’utilisation, exigences techniques et destinations de publication. Que vous soyez un créateur de formulaires à la recherche de modèles ou un développeur ou une développeuse créant des formulaires complexes, ce guide vous aide à choisir le créateur de formulaires approprié pour votre projet.

## Guide de décision rapide

Utilisez cette référence rapide pour identifier le créateur de formulaires le mieux adapté à vos besoins :

| **Si vous avez besoin de...** | **Choisir** |
|-------------------|------------|
| **Formulaires modernes et évolutifs dotés des dernières fonctionnalités** | Composants principaux |
| **Formulaires ultra-rapides pour les sites web à trafic élevé** | Éditeur universel |
| **Conserver les formulaires existants ou les intégrations héritées** | Composants de base |
| **Création visuelle par glisser-déposer** | Composants principaux ou éditeur universel |
| **Création de formulaires basés sur des feuilles de calcul** | Création basée sur des documents |
| **Diffusion omnicanal (web, mobile, kiosques)** | Composants principaux (avec API découplées) |
| **Applications front-end personnalisées (React, Angular)** | Composants principaux (avec API découplées) |
| **Contrôle total du rendu des formulaires** | Composants principaux (avec API découplées) |

## Présentation des options du créateur de formulaires

AEM Forms propose trois approches principales de création de formulaires, chacune conçue pour différents types de créateurs de formulaires et de cas d’utilisation. Que vous ayez besoin d’un simple créateur de formulaires pour des tâches rapides ou de fonctionnalités avancées de créateur de formulaires pour des projets complexes, il existe une approche qui répond à vos besoins :

### Créateur de formulaires des composants de base

Les composants de base représentent l’expérience de création AEM Forms classique. Bien qu’elles soient toujours prises en charge, elles sont principalement recommandées pour la maintenance des formulaires existants plutôt que pour la création de nouveaux formulaires.

**Caractéristiques principales :**

- Interface de création d’AEM traditionnelle
- Stabilité éprouvée des workflows existants
- Limité à la publication uniquement dans AEM
- Bibliothèque de composants de base

### Créateur de formulaires des composants principaux

Les composants principaux fournissent les dernières fonctionnalités d’AEM Forms avec des performances, une accessibilité et une flexibilité améliorées. Ce créateur de formulaires est idéal pour les créateurs et créatrices de formulaires qui ont besoin de résultats professionnels dotés de fonctionnalités modernes. Il prend en charge la publication AEM et Edge Delivery Services et produit automatiquement des formulaires découplés pour une diffusion pilotée par les API sur plusieurs plateformes.

**Caractéristiques principales :**

- Composants modernes et normalisés
- Amélioration des performances et de l’accessibilité
- Options de publication flexibles (AEM + Edge Delivery)
- Fonctionnalités de personnalisation avancées
- Architecture durable
- Génération automatique de formulaires découplés pour une diffusion omnicanal

### Éditeur universel (Edge Delivery Services)

L’éditeur universel offre deux approches de création puissantes pour Edge Delivery Services : la création visuelle WYSIWYG et la création basée sur des documents à l’aide de feuilles de calcul. Cette approche de créateur de formulaires est parfaite pour les utilisateurs et utilisatrices qui souhaitent créer des formulaires rapidement avec des performances exceptionnelles.

**Caractéristiques principales :**

- Performances exceptionnelles (scores Lighthouse élevés)
- deux méthodes de création : WYSIWYG et basées sur des documents ;
- Optimisé pour Edge Delivery Services
- Performances exceptionnelles et SEO
- Développement et déploiement rapides


## Comparaison détaillée

### Fonctionnalités techniques

| **Fonction** | **Foundation** | **Base** | **Éditeur universel** | **Basé sur les documents** |
|----------------|----------------|----------|---------------------|-------------------|
| **Complexité du formulaire** | Réglages de base | Avancé | Avancé | Simple à modérée |
| **Moteur de règles** | Avancé | Avancé | Avancé | Limitée |
| **Composants personnalisés** | ✅ | ✅ | ✅ | ✅ |
| **Thèmes** | ✅ | ✅ | Au niveau du projet | Au niveau du projet |
| **Modèles** | ✅ | ✅ | Contenu initial uniquement |  |
| **Fragments** | ✅ | ✅ | ✅ | ✅ |
| **Localisation** | ✅ | ✅ | Via AEM Sites | Manuelle/Fonctions |

### Intégration et soumission

| **Fonctionnalité** | **Foundation** | **Base** | **Éditeur universel** | **Basé sur les documents** |
|-------------|----------------|----------|---------------------|-------------------|
| **Modèles de données** | FDM, personnalisé | FDM, personnalisé | FDM, personnalisé | Personnalisé |
| **Actions Envoyer** | Plusieurs options | Plusieurs options | Plusieurs options | Feuille de calcul uniquement |
| **Pré-remplissage** | ✅ | ✅ | Via l’assistant | ✅ |
| **CAPTCHA** | Plusieurs types | reCAPTCHA, hCaptcha | reCAPTCHA Enterprise | reCAPTCHA Enterprise |
| **Pièces jointes** | ✅ | ✅ | ✅ | Accès anticipé |
| **Signatures numériques** | ✅ |  |  |  |

### Publication et performances

| **Aspect** | **Foundation** | **Base** | **Éditeur universel** | **Basé sur les documents** |
|------------|----------------|----------|---------------------|-------------------|
| **Publication** | Seulement AEM | AEM + Edge Delivery + API découplées | Edge Delivery | Edge Delivery |
| **Performances** | Standard | Amélioré | Scores Lighthouse élevés | Scores Lighthouse élevés |
| **Optimisation du référencement** | Réglages de base | Bon | Excellent | Excellent |
| **Réactivité mobile** | Bon | Excellent | Excellent | Excellent |

## Choisir le bon créateur

### Choisissez les composants de base si :

- Vous conservez des formulaires existants basés sur Foundation
- Vous avez besoin d’une intégration de signature numérique
- Votre workflow dépend de fonctionnalités Foundation établies
- Vous respectez les exigences de publication réservées à AEM

**Idéal pour :** la maintenance des formulaires, l’intégration des systèmes hérités, les workflows établis.

### Choisissez les composants principaux si :

- Vous créez de nouveaux formulaires modernes
- Vous avez besoin de flexibilité pour publier sur AEM ou Edge Delivery Services
- Vous voulez les dernières fonctionnalités
- Vous avez besoin d’une personnalisation et d’une thématique avancées
- L&#39;accessibilité et la performance sont des priorités
- Vous voulez une technologie à l&#39;épreuve du temps

**Idéal pour :** nouveaux projets, solutions évolutives, expériences web modernes

### Choisissez l’éditeur universel si :

- Vous avez besoin de performances exceptionnelles et de SEO
- Création en cours pour les sites Edge Delivery Services
- Vous avez besoin de formulaires complexes avec des actions personnalisées
- L’intégration à des systèmes externes est requise.

**Idéal pour** sites hautes performances, Edge Delivery Services et les workflows de création visuelle.

### Choisissez la création basée sur des documents si :

- Les utilisateurs professionnels préfèrent la création basée sur des feuilles de calcul
- Vous avez besoin d’un prototypage et d’un déploiement rapides
- Les Forms sont relativement simples (enquêtes, enregistrements, commentaires)
- La collecte de données dans les feuilles de calcul répond à vos besoins
- Aucun workflow d’envoi avancé requis

**Idéal pour :** déploiement rapide, création d’utilisateurs professionnels, collecte de données simple


## Considérations relatives à la migration

### Des composants de base aux composants principaux

- **Approche recommandée :** utilisez l’outil [utilitaire de migration](/help/forms/migration-utility-tool-for-af-core-components.md)
- **Avantages :** fonctionnalités modernes, meilleures performances, fonctionnalité de publication double
- **Effort :** modéré à élevé, selon la complexité du formulaire

### De l’éditeur traditionnel à l’éditeur universel

- **Approche :** reconstruction de formulaires à l’aide de WYSIWYG ou de la création basée sur des documents dans l’éditeur universel
- **Avantages :** performances exceptionnelles, expérience de développement moderne, scores SEO élevés
- **Effort :** élevé pour les formulaires complexes, faible pour les formulaires simples

## Prise en main

Une fois que vous avez choisi votre créateur de formulaires :

### Composants de base

1. [Créer un formulaire adaptatif (composants de base)](/help/forms/creating-adaptive-form.md)
2. [Guide de création des composants de base](/help/forms/introduction-forms-authoring.md)

### Composants principaux

1. [Créer un formulaire adaptatif (composants principaux)](/help/forms/creating-adaptive-form-core-components.md)
2. [Présentation de la fonctionnalité Composants principaux](/help/forms/adaptive-form-core-components-json-schema-form-model.md)

### Éditeur universel (Edge Delivery Services)

1. **Création WYSIWYG :** [Prise en main de l’éditeur universel](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)
2. **Création basée sur des documents :** [créez votre premier formulaire avec des feuilles de calcul](/help/edge/docs/forms/tutorial.md)


## Besoin d’aide pour prendre une décision ?

Vous ne savez toujours pas quel créateur de formulaires choisir ? Tenez compte des facteurs suivants :

- **Expertise de l’équipe :** quel est le niveau de compétence technique de votre équipe ?
- **Chronologie du projet :** à quelle vitesse devez-vous procéder au déploiement ?
- **Exigences de performance :** la vitesse et l’optimisation du moteur de recherche sont-elles essentielles ?
- **Évolutivité future :** devrez-vous développer ou modifier fréquemment les formulaires ?
- **Destination de publication :** où vos formulaires seront-ils publiés ?

Pour obtenir des conseils personnalisés, contactez votre équipe d’implémentation AEM Forms ou l’assistance Adobe.

## Articles connexes

- [Comparaison détaillée de la création de formulaires](/help/edge/docs/forms/authoring-a-form.md)
- [Présentation des composants principaux AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr)
- [Présentation de Edge Delivery Services for Forms](/help/edge/docs/forms/overview.md)
- [Forms adaptatif découplé avec composants principaux](https://experienceleague.adobe.com/fr/docs/experience-manager-headless-adaptive-forms/using/tutorial/build-engaging-forms-using-core-components-and-headless-adaptive-forms-aem-forms-cloud-service)
