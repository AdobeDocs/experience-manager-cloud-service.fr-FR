---
title: Forms Experience Builder
description: Créer des formulaires puissants plus rapidement à l’aide de fragments de formulaire
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: 750674bbd29ec1b29388579d77c7c15bd89335ab
workflow-type: tm+mt
source-wordcount: '1180'
ht-degree: 3%

---


# Présentation de Forms Experience Builder

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette documentation est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les fonctionnalités, commandes et exemples peuvent changer à mesure que le Forms Experience Builder continue d’évoluer au cours du programme destiné aux utilisateurs et utilisatrices précoces.

Forms Experience Builder tire parti de la puissance de l’intelligence artificielle pour Adobe Experience Manager (AEM) Forms. Cette solution innovante transforme la manière dont les entreprises créent, gèrent et optimisent leurs formulaires numériques grâce à des interactions en langage naturel et à une automatisation intelligente.

Basé sur des technologies web modernes et optimisé par des services d’IA avancés, le Forms Experience Builder permet aux utilisateurs techniques et non techniques de créer des formulaires sophistiqués de qualité professionnelle par le biais d’interfaces de conversation. Que vous soyez un analyste commercial ayant besoin d’un simple formulaire d’enregistrement ou un développeur créant des workflows complexes à plusieurs étapes, le Forms Experience Builder simplifie l’ensemble du processus de création de formulaires.

## Interface Conversationnelle

Forms Experience Builder fournit une interface intuitive basée sur les conversations qui rend la création de formulaires aussi simple que de discuter :

```
┌─────────────────────────────────────────────────────────┐
│ Forms Experience Builder                               │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  👤 User: Create a customer feedback form              │
│                                                         │
│  🤖 AI: I'll help you create a feedback form. What    │
│       type of feedback do you want to collect?         │
│                                                         │
│  👤 User: Product reviews with ratings and comments    │
│                                                         │
│  🤖 AI: Perfect! I've created a feedback form with:   │
│       * Product rating (1-5 stars)                     │
│       * Comment field                                   │
│       * Customer email (optional)                       │
│       * Submit to email notification                    │
│                                                         │
│  👤 User: Add a field for product category             │
│                                                         │
│  🤖 AI: Added a dropdown field with common categories  │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

## Fonctionnalités principales

### Création de formulaires optimisée par l’IA

**Génération de formulaires en langage naturel**

Créez des formulaires complets à partir de zéro à l’aide de descriptions en anglais simples. Il vous suffit de décrire vos besoins, tels que « Créer un formulaire de commentaires client avec des échelles de notation et des champs de commentaire », et le Forms Experience Builder génère la structure de formulaire appropriée, les types de champs et les règles de validation.

**Dynamic Field Management**

Ajouter, modifier ou supprimer des champs de formulaire par le biais de commandes de conversation. L’IA comprend le contexte et peut suggérer intelligemment des types de champs, des règles de validation et des améliorations de l’interface utilisateur en fonction de vos besoins.

**Optimisation de la disposition**

Mettez à jour les dispositions et configurations de formulaire en langage naturel. Demandez des modifications telles que « Rendre le formulaire plus convivial pour les appareils mobiles » ou « Réorganiser les champs dans un flux logique » et le Forms Experience Builder appliquera les réglages de style et de disposition appropriés.

### Importation et conversion intelligentes

Conversion de **PDF en formulaire**

Transformez des documents PDF statiques en formulaires interactifs et dynamiques. Chargez n’importe quel document PDF et Forms Experience Builder analyse la structure pour créer un formulaire numérique correspondant avec les types de champs et la validation appropriés.

**URL vers la conversion de formulaire**

Convertissez des formulaires ou des pages Web existants en AEM Forms. Il vous suffit de fournir une URL pour que le Forms Experience Builder extrait les éléments de formulaire et les recrée en tant qu’AEM Forms natif avec des fonctionnalités améliorées.

**Prise en charge de fichiers multiformats**

Gérez divers types de fichiers pour la création de formulaires, y compris les PDF, les images, les captures d’écran et les modèles de formulaire existants. Le Forms Experience Builder peut les traiter et les convertir en AEM Forms fonctionnel.

### Logique de formulaire avancée et intégration

**Génération de règles intelligente**

Créez des règles de validation de formulaire et de logique commerciale complexes via le langage naturel. Forms Experience Builder peut générer une logique conditionnelle sophistiquée, des dépendances de champs et des règles de validation qui nécessitent généralement des connaissances approfondies en codage.

**Configuration complète de l’action Envoyer**

Configurez les envois de formulaire à intégrer à vos systèmes d’entreprise existants :

- **Intégration de la messagerie électronique** : configurer des notifications et des confirmations automatisées par courrier électronique
- **Points d’entrée de l’API REST** : connexion à des applications et services personnalisés
- **Stockage dans le cloud** : intégration à Azure Blob Storage, SharePoint et OneDrive
- **Automatisation des workflows** : connexion à Power Automate et Workfront Fusion
- **Plateformes marketing** : intégration directe à Marketo pour la gestion des prospects
- **Workflows AEM** : tirer parti des fonctionnalités existantes des workflows AEM

**Analyses de performances**

Analysez les performances de conversion de formulaire et les modèles d’interaction client. Le Forms Experience Builder fournit des informations sur l’efficacité des formulaires et suggère des optimisations pour améliorer les taux d’achèvement et l’expérience utilisateur.

## Fonctionnement

Le créateur d’expérience Forms suit une approche simple et conversationnelle :

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│  1. Describe    │───▶│  2. AI Creates  │───▶│  3. Refine &    │
│  Your Form      │    │  Initial Form   │    │  Configure      │
│  Requirements   │    │                 │    │                 │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         │                       │                       │
         ▼                       ▼                       ▼
┌─────────────────────────────────────────────────────────────────┐
│  "Create a loan application form"  →  Form with relevant        │
│  "Add conditional logic"           →  fields and basic          │
│  "Connect to CRM system"           →  validation rules          │
└─────────────────────────────────────────────────────────────────┘
```

## Exemples de cas d’utilisation

### Formulaire de demande de prêt

```
┌─────────────────────────────────────────────────────────┐
│ Loan Application - Multi-Step Form                    │
├─────────────────────────────────────────────────────────┤
│ Step 1: Personal Information                           │
│  🏠 Property Type: [Primary] [Investment] [Commercial] │
│  💰 Loan Amount: [$_______] (triggers different paths) │
│  📊 Income Verification: [W2] [Self-Employed] [Other]  │
│                                                         │
│ Step 2: Financial Details (conditional based on above) │
│  ↳ If Self-Employed: Show tax returns, profit/loss     │
│  ↳ If W2: Show employment history, pay stubs           │
│  ↳ Complex debt-to-income calculations                 │
│                                                         │
│ Step 3: Compliance & Review                            │
│  📋 Regulatory disclosures, digital signatures         │
│  🔍 Automated eligibility pre-screening                │
└─────────────────────────────────────────────────────────┘
```

### Formulaire de demande de remboursement d&#39;assurance

```
┌─────────────────────────────────────────────────────────┐
│ Insurance Claim - Adaptive Form                        │
├─────────────────────────────────────────────────────────┤
│ 🚗 Claim Type: [Auto] [Property] [Health] [Business]   │
│                                                         │
│ ↳ Auto Selected: Shows accident details, police report │
│ ↳ Property: Shows damage assessment, repair estimates  │
│ ↳ Health: Shows medical provider network, pre-auth     │
│                                                         │
│ 📎 Dynamic Document Requirements:                       │
│   * Photos/videos of damage                            │
│   * Police reports (auto only)                         │
│   * Medical records (health only)                      │
│   * Repair estimates (property only)                   │
│                                                         │
│ 🔄 Real-time claim status updates                      │
└─────────────────────────────────────────────────────────┘
```

### Scénarios de migration et de conversion

Transformez vos formulaires existants en puissantes expériences digitales grâce à la conversion optimisée par l’IA.


### 📄 de PDF au numérique

**Des documents statiques aux formulaires interactifs**

Transformez PDF forms avec plus de 50 champs en expériences digitales dynamiques grâce à des calculs automatisés et à une conception réactive aux appareils mobiles.

**Principaux avantages :**

- Calculs de taxe automatisés et dépendances de champs
- Signatures numériques et intégration des fichiers électroniques
- Optimisation de la disposition réactive pour les appareils mobiles
- Réduction de 95 % des erreurs de traitement

**Idéal pour :** formulaires fiscaux, applications gouvernementales, documents commerciaux complexes

**Gain de temps :** 2 à 3 heures → 15 minutes par formulaire



### Modernisation de XFA héritée de 🏛️

**Insufflez une nouvelle vie dans des formes dépassées**

Convertissez des applications XFA complexes en assistants modernes à plusieurs étapes avec validation en temps réel et conformité en matière d’accessibilité.

**Principaux avantages :**

- Interface d’assistant rationalisée à plusieurs étapes
- Validation en temps réel avec aide contextuelle
- Intégration de bases de données gouvernementales
- Conformité complète à WCAG 2.1 en matière d’accessibilité

**Idéal pour** autorisations gouvernementales, applications d’entreprise, formulaires de conformité

**Impact :** achèvement 70 % plus rapide, 90 % moins d’erreurs




### 📱 une capture d’écran au format numérique

**Transformez n’importe quel formulaire papier en une expérience digitale**

Chargez une image de n’importe quel formulaire papier et observez les champs d’extraction de l’IA, optimisez la mise en page et créez des formulaires numériques prêts pour l’intégration.

**Principaux avantages :**

- Détection intelligente du type de champ (précision supérieure ou égale à 99 %)
- Génération de mises en page réactives optimisée
- Validation améliorée au-delà du papier original
- Architecture prête pour l’intégration

**Idéal pour :** applications papier, formulaires manuscrits, documents hérités

**Temps de traitement :** 2 heures → 5 minutes par formulaire



### Amélioration d’🌐 HTML

**Optimiser vos formulaires web existants**

Ajoutez une validation avancée, une logique conditionnelle et un envoi multicanal aux formulaires HTML de base sans interrompre les fonctionnalités existantes.

**Principaux avantages :**

- Logique et règles de validation avancées
- Comportements de champ conditionnel et workflows
- Options d’envoi multicanal
- Analyses intégrées et suivi des performances

**Idéal pour :** formulaires de contact, formulaires d’enregistrement, applications web simples

**Amélioration de la conversion :** +40 % avec une expérience utilisateur améliorée


## Forms Experience Builder par rapport au développement traditionnel

| Aspect | Création de formulaire traditionnelle | Forms Experience Builder |
|--------|---------------------------|----------------------|
| **Heure de création** | 2-3 jours | 2-3 heures |
| **Connaissances techniques** | Obligatoire | Non requis |
| **Règles de validation** | Codage manuel | Langage naturel |
| **Optimisation mobile** | CSS/JS manuel | Automatique |
| **Accessibilité** | Implémentation manuelle | Conformité intégrée |
| **Mises à jour** | Modifications de code requises | Langage naturel |


## Avantages pour les organisations

### Création de formulaire démocratisée

Permet aux utilisateurs non techniques de créer des formulaires sophistiqués sans connaissances en programmation. Les analystes commerciaux, les experts en la matière et les créateurs de contenu peuvent traduire directement leurs besoins en formulaires fonctionnels par le biais de conversations en langage naturel.

### Rentabilité réduite (TTV)

Accélérez considérablement le développement des formulaires de quelques jours à quelques heures. Ce qui nécessitait auparavant des cycles de développement étendus peut désormais être réalisé en une seule session grâce à l’IA conversationnelle, ce qui permet une mise sur le marché plus rapide des initiatives numériques.

### Simplicité de l&#39;interface

Éliminez la courbe d’apprentissage grâce à une interface de conversation intuitive. Les utilisateurs peuvent créer des formulaires complexes en langage naturel au lieu d’apprendre à créer des outils de formulaires techniques, ce qui réduit le temps de formation et accroît l’adoption.

### Adaptation des efforts de modernisation

Modernisez efficacement les portefeuilles de formulaires hérités. Convertissez des formulaires PDF, XFA et HTML existants en expériences digitales réactives tout en préservant la logique commerciale et en améliorant l’expérience utilisateur sur l’ensemble de votre écosystème de formulaires.

## Prise en main

Pour commencer à utiliser Forms Experience Builder, consultez la [documentation de Forms Experience Builder](forms-ai-assistant-getting-started.md). Vous pouvez accéder au Forms Experience Builder par le biais de l’éditeur AEM Forms ou de l’éditeur universel, selon votre choix de workflow.

Pour les entreprises qui cherchent à transformer leurs processus de création de formulaires, le Forms Experience Builder offre une solution puissante et intuitive qui combine la flexibilité de l’IA conversationnelle avec la robustesse de la gestion des formulaires de niveau entreprise.

## Intégration et accès anticipé

Forms Experience Builder est actuellement disponible dans le cadre du programme d’accès anticipé (EA). Pour participer et obtenir l’accès, procédez comme suit :

1. Assurez-vous d’utiliser l’adresse e-mail professionnelle officielle associée à votre organisation.
2. Envoyez un e-mail à [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) pour demander l’accès à Forms Experience Builder.
3. Incluez le nom de votre organisation et les détails pertinents du projet dans votre demande pour accélérer le processus d’intégration.

>[!NOTE]
>
> L’accès à Forms Experience Builder est limité aux participants approuvés du programme d’accès anticipé. Adobe examinera votre demande et fournira des instructions supplémentaires pour l’intégration si vous êtes éligible.

Pour plus d’informations sur le programme d’accès anticipé et ses fonctionnalités, consultez la [documentation sur l’accès anticipé d’AEM Forms](/help/forms/early-access-ea-features.md).

