---
title: Composants principaux de Forms adaptatif par rapport aux composants de base de Edge Delivery Services Forms
description: Comparaison technique des approches de création d’AEM Forms - Composants principaux, Edge Delivery Services Forms et Composants de base. Architecture, rendu, fonctionnalités et cas d’utilisation.
keywords: comparaison des formulaires adaptatifs, composants principaux, composants de base, formulaires des services de diffusion edge, comparaison des formulaires AEM, comparaison du créateur de formulaires
role: Architect, Developer, Admin
level: Intermediate
feature: Adaptive Forms, Core Components, Edge Delivery Services
exl-id: adaptive-forms-comparison
source-git-commit: 37799555babb15809409ec5cda8a1c46ceff24f2
workflow-type: tm+mt
source-wordcount: '1953'
ht-degree: 10%

---


# Forms adaptative : composants principaux par rapport à Edge Delivery Services Forms par rapport aux composants de base

Adobe Experience Manager (AEM) Forms propose trois approches distinctes pour créer des expériences de capture de données : Forms adaptatif basé sur les composants principaux, Edge Delivery Services Forms et Forms adaptatif basé sur les composants de base. Chaque approche possède une architecture, un modèle de rendu et un cas d’utilisation cible différents. Cet article fournit une comparaison technique pour aider les architectes de solution, les développeurs et les clients AEM à sélectionner l’approche appropriée en fonction de leurs besoins.

## Vue d’ensemble

Ces trois types de formulaires ont pour but de capturer des données utilisateur et de les intégrer aux systèmes principaux. Cependant, elles diffèrent en termes d’architecture sous-jacente, d’emplacement de rendu des formulaires, de mode de diffusion et de fonctionnalités prises en charge.

| Approche | Statut | Cas d’utilisation du Principal |
|----------|--------|------------------|
| **Composants principaux** | Recommandé pour les nouveaux formulaires | Formulaires modernes et évolutifs nécessitant la création dans AEM avec des options de publication flexibles |
| **Edge Delivery Services Forms** | Recommandé pour les sites critiques | Formulaires hautes performances diffusés à partir de la périphérie avec déploiement rapide |
| **Composants de base** | Mode de maintenance | Formulaires existants nécessitant la prise en charge des fonctionnalités héritées |

## Forms adaptatif basé sur les composants principaux

### Définition

Les composants principaux de Forms adaptatif sont un ensemble de 30 composants open source compatibles avec BEM qui reposent sur les composants principaux de gestion de contenu web de Adobe Experience Manager. Ils représentent l’approche recommandée d’Adobe pour créer un nouveau Forms adaptatif, fournir une architecture moderne, des performances améliorées et la génération automatique de formulaires découplés.

### Architecture

Les composants principaux utilisent une architecture de composants modulaire normalisée :

- **Principes de base des composants** : repose sur les composants principaux de gestion de contenu web d’AEM
- **Méthodologie de style** : conventions CSS BEM (Block Element Modifier)
- **Stockage de contenu** : référentiel JCR avec nœuds de contenu structuré
- **Rendu** : rendu côté serveur dans AEM avec rendu côté client découplé en option
- **Source** : open-source (disponible sur [GitHub](https://github.com/adobe/aem-core-forms-components))

### Modèle de rendu

Les composants principaux prennent en charge plusieurs modèles de rendu :

1. **Rendu côté serveur (SSR)** : le rendu Forms est effectué sur le serveur AEM et fournit une HTML complète au navigateur
2. **Rendu découplé** : Forms expose les représentations JSON via des API pour le rendu côté client dans React, Angular ou d’autres frameworks
3. **Rendu hybride** : combinaison du rendu serveur et client pour des performances optimales

### Options de publication

- Instances de publication AEM
- Edge Delivery Services (une fois configuré)
- API découplées pour les applications front-end personnalisées

### Fonctions clés

| Catégorie | Fonctionnalités |
|----------|-------------|
| **Composants** | 30 composants normalisés, notamment la zone de texte, la zone numérique, le sélecteur de date, la liste déroulante, le groupe de cases à cocher, le bouton radio, la pièce jointe, l’assistant, l’accordéon et les onglets horizontaux/verticaux |
| **Modèles de formulaire** | Schéma JSON (v4 et 2020-12), modèle de données de formulaire (FDM), modèles XDP/XFA (limité) |
| **Moteur de règles** | Éditeur de règles visuel avec logique conditionnelle, validation, appel de service, fonctions personnalisées |
| **Actions Envoyer** | Point d’entrée REST, e-mail, workflow AEM, SharePoint, OneDrive, stockage Blob Azure, Power Automate, Workfront Fusion, modèle de données de formulaire |
| **Pré-remplissage** | Service de préremplissage du modèle de données de formulaire, services de préremplissage personnalisés |
| **CAPTCHA** | reCAPTCHA, hCaptcha, tourniquet |
| **Document d’enregistrement** | Génération de PDF avec des modèles personnalisés ou prêts à l’emploi |
| **Accessibilité** | Compatible WCAG, libellés ARIA, navigation au clavier, prise en charge des lecteurs d’écran |
| **Localisation** | Prise en charge multilingue via le workflow de traduction d’AEM |
| **Contrôle de version** | Contrôle de version du contenu hérité d’AEM Sites |

### Prérequis

- **AEM Forms as a Cloud Service** : composants principaux activés par défaut
- **AEM 6.5 Forms** : nécessite une activation via l’archétype AEM
- **Autorisations utilisateur** : l’utilisateur doit se trouver dans `forms-users` groupe
- **Modèle** : modèle de formulaire adaptatif (composant principal) requis
- **Thème** : thème de la zone de travail (OOTB) ou thème personnalisé

### Limites

- **Contraintes de schéma JSON** : type nul, types d’union (any), constructions OneOf/AnyOf/AllOf/NOT prises en charge
- **Écarts entre les composants** : bloc Adobe Sign, signature tactile, graphique, choix d’image non disponible (disponible dans les composants de base)
- **Fonctions personnalisées** : fonctions de générateur, async/await, méthodes de classe non prises en charge
- **Signatures numériques** : non disponible nativement (contrairement aux composants de base)

### Quand l’utiliser

**Recommandé pour :**

- Projets de développement de nouveaux formulaires
- Entreprises nécessitant une architecture moderne et gérable
- Projets nécessitant une publication flexible (AEM + Edge Delivery + Headless)
- Applications frontales personnalisées (React, Angular) via des API découplées
- Projets donnant la priorité aux performances et à l’accessibilité
- Exigences en matière de diffusion omnicanal (web, mobile, kiosques)

**Non recommandé pour :**

- Forms nécessitant une intégration Adobe Sign (utilisez les composants de base)
- Formulaires simples dans lesquels les performances de Edge Delivery Services sont essentielles
- Formulaires existants basés sur un composant de base (conservés dans Foundation sauf lors de la migration)

## Edge Delivery Services pour AEM Forms

### Définition

Edge Delivery Services (EDS) Forms est un ensemble de services composables permettant de créer et de diffuser des formulaires via Adobe Experience Manager Edge Delivery Services. Ils permettent un développement rapide des formulaires avec des performances exceptionnelles grâce à une diffusion basée sur le serveur Edge, un rendu côté client et plusieurs méthodes de création.

### Architecture

EDS Forms utilise une architecture edge-first découplée :

- **Sources de contenu** : Microsoft SharePoint, Google Drive (basé sur les documents) ou Universal Editor (WYSIWYG)
- **Référentiel de code** : GitHub
- **Diffusion de contenu** : réseau CDN Edge Delivery Services
- **Rendu** : rendu côté client à l’aide de JavaScript vanilla
- **Bloc de formulaire** : le bloc Forms adaptatif traite les définitions de formulaire et génère HTML

### Modèle de rendu

EDS Forms utilise exclusivement le rendu côté client :

1. Définition de formulaire stockée au format JSON (convertie à partir d’une feuille de calcul ou créée dans l’éditeur universel)
2. JSON récupéré à partir du serveur Edge : `https://<branch>--<repo>--<owner>.aem.live/<form>.json`
3. Le bloc JavaScript de Forms adaptatif traite les fichiers JSON.
4. HTML généré dynamiquement dans le navigateur
5. CSS appliqué pour le style

**Modèle de structure HTML :**

```html
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required="{Required}">
   <label for="{FieldId}" class="field-label">Label</label>
   <input type="{Type}" id="{FieldId}" name="{Name}">
   <div class="field-description" id="{FieldId}-description">Help text</div>
</div>
```

### Méthodes de création

EDS Forms prend en charge deux approches de création :

#### Éditeur universel (WYSIWYG)

- Interface visuelle par glisser-déposer
- Prévisualisation en temps réel avec simulation de l’appareil
- Éditeur de règles avancé pour la logique conditionnelle
- Intégration du modèle de données de formulaire (FDM)
- Intégration des workflows AEM
- Prise en charge des composants personnalisés
- Création basée sur des modèles

#### Création basée sur des documents

- Création de feuilles Microsoft Excel ou Google Sheets
- Définition d’un formulaire basé sur une feuille de calcul
- Publication instantanée (les modifications sont immédiatement répercutées)
- Convient aux formulaires simples à modérément complexes

### Options d’envoi

**Service d’envoi Forms (FSS) :**

- Envoyer aux feuilles Google
- Envoyer à Microsoft Excel (OneDrive/SharePoint)
- Notifications par e-mail

**Actions d’envoi de publication AEM :**

- Point d’entrée REST
- Services de messagerie AEM
- Modèle de données de formulaire
- Processus AEM
- SharePoint/OneDrive
- Stockage Azure Blob
- Microsoft Power Automate
- Adobe Workfront Fusion
- Adobe Marketo Engage

### Fonctions clés

| Catégorie | Fonctionnalités |
|----------|-------------|
| **Composants** | Tous les types d’entrée HTML5, groupes de cases à cocher, groupes de cases d’option, liste déroulante, panneaux, sections répétables, pièce jointe de fichier, accordéon, assistant, modal |
| **Validation** | Validation au niveau du champ (obligatoire, min/max, modèle), messages de validation personnalisés |
| **Règles** | Visibilité conditionnelle, expressions de valeur, règles pilotées par les événements |
| **Intégrations** | Adobe Sign, Salesforce, Microsoft Dynamics, tests A/B |
| **Sécurité** | reCAPTCHA Enterprise, hCaptcha, configuration CORS |
| **Analytics** | Adobe Experience Platform Web SDK, vues de formulaires et suivi des envois |

### Prérequis

**Pour La Création Basée Sur Des Documents :**

- Compte GitHub
- Compte Google Drive ou Microsoft SharePoint
- Nœud/npm pour le développement local
- Projet AEM avec bloc de Forms adaptatif configuré
- Partager le dossier avec `forms@adobe.com` (modifier les autorisations)

**Pour l’éditeur universel :**

- Instance AEM Forms as a Cloud Service
- Projet Edge Delivery Services configuré
- Autorisations requises pour les destinations cibles

**Pour l’envoi de la publication AEM :**

- URL de l’instance AEM Cloud Service configurée
- Configuration du filtre de référent OSGi
- Configuration CORS des domaines de site Edge Delivery

### Limites

**Création basée sur des documents :**

- Dénomination de feuille limitée à `helix-default` et `shared-aem`
- Idéal pour les formulaires à faible complexité
- Fonctionnalités de règles limitées
- Aucun workflow AEM (sans envoi de l’instance de publication AEM)
- Aucune intégration de modèle de données de formulaire

**Éditeur universel:**

- Les imports statiques/dynamiques ne sont pas pris en charge dans les fonctions personnalisées
- Les fragments de formulaire peuvent uniquement être modifiés de manière autonome
- Fonctionnalité d’incorporation de formulaire dans le développement

**Général:**

- Les feuilles de `shared-aem` ne doivent pas contenir de PII (accessibles au public)
- Configuration CORS requise pour les envois entre origines multiples
- Filtre référent OSGi requis pour les envois de l’instance de publication AEM

### Quand l’utiliser

**Recommandé pour :**

- Sites web stratégiques nécessitant des scores Lighthouse élevés
- Sites utilisant déjà Edge Delivery Services
- Développement et déploiement rapides des formulaires
- Capture de données de complexité simple à modérée
- Équipes préférant la création basée sur des feuilles de calcul (basée sur des documents)
- Projets nécessitant une mise sur le marché rapide

**Non recommandé pour :**

- Forms nécessitant un traitement côté serveur étendu
- Intégration profonde avec les systèmes hérités sans API REST
- Exigences de formulaire hors ligne
- Organisations nécessitant des frameworks JavaScript spécifiques (React, Angular) avec contrôle total

## Forms adaptatif basé sur les composants de base

### Définition

Les composants de base représentent l’approche de création AEM Forms classique. Il s’agit des composants Forms adaptatifs d’origine qui sont disponibles dans AEM Forms depuis de nombreuses années. Bien que toujours pris en charge, Adobe recommande les composants de base principalement pour la maintenance des formulaires existants plutôt que pour la création de nouveaux formulaires.

### Architecture

Les composants de base utilisent l’architecture traditionnelle d’AEM :

- **Modèle de contenu** : composant `cq:Page` de gestion de contenu web avec structure de contenu JCR
- **Structure racine** : `guideContainer` (racine) → `rootPanel` → `items` (champs de formulaire)
- **Rendu** : rendu côté serveur avec JavaScript côté client
- **Expressions SOM** : modèle d’objet de script pour référencer des objets de formulaire

### Modèle de rendu

Les composants de base utilisent le rendu côté serveur :

1. Contenu de formulaire stocké dans le référentiel JCR
2. Le serveur AEM traite la structure des formulaires.
3. Effectuer le rendu d’HTML et l’envoyer au navigateur
4. Le JavaScript côté client gère l’interactivité et la validation

### Fonctions clés

| Catégorie | Fonctionnalités |
|----------|-------------|
| **Composants** | Plus de 40 composants, y compris tous les équivalents des composants principaux, plus : bloc Adobe Sign, graphique, signature tactile, choix de l’image, étape de résumé, liste des pièces jointes |
| **Modèles de formulaire** | Modèle de données de formulaire (FDM), modèles XDP/XFA, schéma XML (XSD), schéma JSON |
| **Moteur de règles** | Éditeur visuel + éditeur de code (pour le groupe forms-power-users) |
| **Signatures numériques** | Intégration d’Adobe Sign, signature tactile |
| **Actions Envoyer** | Plusieurs actions prêtes à l’emploi similaires aux composants principaux |

### Composants exclusifs à Foundation

Les composants suivants sont **disponibles uniquement** dans les composants de base :

- Bloc Adobe Sign
- Graphique
- Liste des pièces jointes
- Espace réservé de note de bas de page
- Choix d’image
- Signature tactile
- Étape de résumé
- Captcha Turnstile

### Prérequis

- AEM Forms as a Cloud Service ou AEM 6.5 Forms
- Modèle de formulaire adaptatif (Foundation)
- Utilisateur dans `forms-users` groupe

### Limites

- **Publication** : uniquement pour AEM (pas d’API Edge Delivery Services ou Headless)
- **Performances** : performances standard (non optimisées pour les scores Lighthouse)
- **Architecture** : architecture héritée sans conformité BEM
- **Open Source** : non open source
- **Développement futur** : mode Maintenance ; nouvelles fonctionnalités principalement ajoutées aux composants principaux.

### Quand l’utiliser

**Recommandé pour :**

- Gestion des formulaires Foundation existants
- Forms nécessitant l’intégration d’Adobe Sign ou de la signature tactile
- Workflows dépendant de fonctionnalités Foundation établies
- Projets avec des exigences de publication AEM uniquement
- Forms nécessitant des composants exclusifs à Foundation (graphique, choix de l’image)

**Non recommandé pour :**

- Développement d’un nouveau formulaire (utilisation des composants principaux)
- Projets nécessitant une publication Edge Delivery Services
- API de formulaire découplé
- Implémentations critiques pour les performances
- Projets donnant la priorité à une architecture à l’épreuve du temps

## Tableau de comparaison

| Paramètre | Composants principaux | Edge Delivery Services pour AEM Forms | Composants de base |
|-----------|-----------------|-----------------------------|-----------------------|
| **Statut** | Recommandé pour les nouveaux formulaires | Recommandé pour les sites à hautes performances | Mode de maintenance |
| **Architecture** | Modulaire, compatible BEM | Edge-first, découplé | Gestion de contenu web traditionnelle |
| **Rendu** | Côté serveur + Headless | Côté client uniquement | Côté serveur |
| **Publication** | AEM + Edge Delivery + API découplées | Edge Delivery Services uniquement | Seulement AEM |
| **Création** | Editeur d&#39;AEM Forms | Éditeur universel pour les feuilles de calcul | Editeur d&#39;AEM Forms |
| **Performances** | Bon (amélioré par rapport à Foundation) | Excellent (scores Lighthouse élevés) | Standard |
| **Nombre de composants** | 30 | 20+ (tous les types d’entrée HTML5) | 40+ |
| **Ouvrir Source** | Oui (GitHub) | Oui | Non |
| **Modèle de données de formulaire** | ✅ | ✅ (éditeur universel uniquement) | ✅ |
| **Schéma JSON** | ✅ | Limitée | ✅ |
| **Prise en charge de XDP/XFA** | Limitée | ❌ | ✅ |
| **Schéma XML** | ❌ | ❌ | ✅ |
| **Moteur de règles** | Éditeur visuel avancé | Avancé (Éditeur Universel) / Limité (Basé Sur Les Documents) | Éditeur visuel et de code avancé |
| **Signatures numériques** | ❌ | ❌ | ✅ |
| **Adobe Sign** | ❌ | Via l’intégration | ✅ (bloc natif) |
| **Document d’enregistrement** | ✅ | ✅ | ✅ |
| **Options CAPTCHA** | reCAPTCHA, hCaptcha | reCAPTCHA Enterprise, hCAPTCHA | reCAPTCHA, hCaptcha, tourniquet |
| **Workflow AEM** | ✅ | ✅ (via l’instance de publication AEM) | ✅ |
| **API Headless** | ✅ (automatique) | ❌ | ❌ |
| **Accessibilité** | Conforme à WCAG | Conforme à WCAG | Éléments de base |
| **Vitesse de déploiement** | Basé sur un pipeline | Instantané (validation en direct) | Basé sur un pipeline |
| **Style** | BEM CSS, Thèmes | CSS, thèmes au niveau du projet | CSS, thèmes |
| **Contrôle de version** | ✅ (hérité de Sites) | Basé sur Git | ✅ |
| **Localisation** | Workflow de traduction AEM | Workflow manuel/AEM Sites | Workflow de traduction AEM |

## Matrice de décision

| Condition requise | Approche recommandée |
|-------------|---------------------|
| Développement de nouveaux formulaires | Composants principaux |
| Gestion des formulaires existants | Composants de base (jusqu’à la migration) |
| Performances critiques (scores Lighthouse élevés) | Edge Delivery Services pour AEM Forms |
| Diffusion découplée/omnicanale | Composants principaux |
| Intégration d’Adobe Sign | Composants de base |
| Création basée sur des feuilles de calcul | Edge Delivery Services (Basé Sur Les Documents) |
| Création visuelle de WYSIWYG avec diffusion Edge | Edge Delivery Services (éditeur universel) |
| Intégrations d’entreprise complexes | Composants principaux ou composants de base |
| Prototypage rapide | Edge Delivery Services (Basé Sur Les Documents) |
| Prise en charge des modèles XFA/XDP | Composants de base |
| Interface frontale React/Angular personnalisée | Composants principaux (API découplées) |

## Considérations relatives à la migration

### des composants de base en composants principaux ;

- **Outil** : outils de modernisation d’AEM (utilitaire de conversion de Forms)
- **Effort** : modéré à élevé selon la complexité du formulaire
- **Considérations** :
   - Les règles nécessitent une recréation manuelle
   - Les composants exclusifs à Foundation (bloc Adobe Sign, signature tactile, graphique) sont supprimés lors de la migration
   - Paramètres de traduction non transférés
   - Les fonctions personnalisées nécessitent une réécriture

### Traditionnel vers Edge Delivery Services

- **Approche** : reconstruction de formulaires à l’aide de l’éditeur universel ou de la création basée sur des documents
- **Effort** : élevé pour les formulaires complexes, faible pour les formulaires simples
- **Avantages** : amélioration significative des performances, expérience de développement moderne

## Lacunes et ambiguïtés dans la documentation

La documentation des zones suivantes est incomplète ou ambiguë :

1. **Prise en charge des composants principaux XDP/XFA** : la documentation indique une prise en charge « limitée », mais ne spécifie pas de limites exactes
2. **Incorporation de formulaire Edge Delivery Services** : marqué comme « Bientôt disponible » dans la documentation ; statut actuel non clair
3. **Version future des composants de base** : aucun calendrier d’obsolescence explicite décrit comme « mode de maintenance »
4. **Couverture d’API découplée** : parité exacte des fonctionnalités entre les formulaires rendus par le serveur et découplés non documentée
5. **Performance Benchmarks** : aucune comparaison des scores spécifiques de Lighthouse entre les approches n’est fournie

## Ressources connexes

- [Créer un formulaire adaptatif (composants principaux)](/help/forms/creating-adaptive-form-core-components.md)
- [Créer un formulaire adaptatif (composants de base)](/help/forms/creating-adaptive-form.md)
- [Présentation de Edge Delivery Services Forms](/help/edge/docs/forms/overview.md)
- [Prise en main de l’éditeur universel](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)
- [Tutoriel Sur La Création Basée Sur Des Documents](/help/edge/docs/forms/tutorial.md)
- [Outil Utilitaire de migration](/help/forms/migration-utility-tool-for-af-core-components.md)
- [Composants principaux AEM Forms sur GitHub](https://github.com/adobe/aem-core-forms-components)
