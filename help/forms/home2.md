---
title: Présentation d’AEM Forms as a Cloud Service
description: Découvrez les fonctionnalités d’AEM Forms pour créer des formulaires adaptatifs, automatiser des processus et gérer des documents numériques. Plateforme complète pour les processus métier pilotés par les formulaires.
landing-page-description: Découvrez comment utiliser AEM Forms as a Cloud Service pour créer des formulaires adaptatifs, traiter des documents et automatiser des processus métier.
keywords: AEM Forms, formulaires adaptatifs, créateur de formulaires, formulaires numériques, automatisation des workflows, services de document, modèle de données de formulaire
role: Admin, Developer, User
feature: Adaptive Forms, Release Information
hide: true
hidefromtoc: true
index: false
exl-id: 50d7ce19-7d76-4ea1-a54c-8ca0e5379982
source-git-commit: eca09e1bf2ba4466f54e915e01218cc89cf5b116
workflow-type: tm+mt
source-wordcount: '2323'
ht-degree: 1%

---

# Présentation d’AEM Forms as a Cloud Service {#introduction}



Adobe Experience Manager Forms as a Cloud Service fournit une plateforme complète pour la création, la gestion et l’optimisation des expériences de formulaires numériques. Les entreprises utilisent AEM Forms pour numériser des processus papier, créer des formulaires web réactifs, automatiser les workflows de documents et diffuser des communications personnalisées à grande échelle.

La plateforme associe des fonctionnalités de création de formulaires à des services back-end robustes, ce qui vous permet de tout créer, des formulaires de contact simples aux applications métier complexes et à plusieurs étapes. Avec une architecture native au cloud, vous bénéficiez de mises à jour automatiques, d’une mise à l’échelle élastique et d’une sécurité de niveau entreprise sans gérer l’infrastructure.

Ce guide présente les principales fonctionnalités organisées tout au long du cycle de vie du formulaire, de la conception initiale à l’optimisation continue.

## Nouveautés dans AEM Forms {#whats-new}

**Dernières mises à jour :**

- **Composant d’entrée de date et d’heure** - Entrée utilisateur améliorée avec l’interface de calendrier et d’horloge pour une sélection de date et d’heure précise
- **Sécurité renforcée du chargement de fichiers** - Validation automatique et vérification des types de contenu pour éviter les formats de fichiers non pris en charge
- **Amélioration de la gestion des erreurs** - Amélioration du débogage avec des codes d’erreur spécifiques pour les actions d’envoi personnalisées
- **Améliorations du document d’enregistrement** - Option permettant d’exclure les champs masqués pour une génération de document plus épurée

**Fonctionnalités de version préliminaire :**

- **Prise en charge du format AFP** - Fonctionnalités d’impression de niveau entreprise avec les API de communication
- **Améliorations apportées à l’éditeur de règles** - Prise en charge moderne de JavaScript, variables dynamiques et règles de panneau contextuelles
- **Méthodes de validation améliorées** - Validation au niveau des panneaux, des champs et des formulaires avec une flexibilité améliorée

[Afficher les notes de mise à jour complètes →](/help/release-notes/release-notes-cloud/release-notes-current.md#forms)

## Programme d&#39;accès anticipé {#early-access}

Bénéficiez d’un accès exclusif aux innovations AEM Forms de pointe avant qu’elles ne soient mises à la disposition du public.

**Fonctionnalités d’accès anticipé actuelles :**

- **Assistant AEM Forms AI** - IA générative pour la création automatisée de formulaires, la génération de panneaux et les recommandations d’optimisation
- **Composant Signature tactile** - Capture de signature directe dans les formulaires à l’aide de la souris, du stylet ou d’un écran tactile
- **Intégration directe d’API** - Connexion aux API dans l’éditeur de règles sans nécessiter la configuration du modèle de données de formulaire
- **Optimisation de Forms** - Analyse des performances optimisée par l’IA et suggestions d’amélioration du taux de conversion

**Rejoindre le programme :**
Soyez parmi les premiers à accéder aux innovations et à contribuer à façonner l’avenir d’AEM Forms.

[Demande d’accès →](mailto:aem-forms-ea@adobe.com) | [En savoir plus →](/help/forms/early-access-ea-features.md)


## Fonctionnalités principales {#core-capabilities}

AEM Forms prend en charge l’ensemble du parcours de formulaires numériques, de la création initiale à l’optimisation continue. Chaque phase s’appuie sur la précédente et crée une plateforme complète pour les processus métier pilotés par les formulaires.

**Parcours De Workflow AEM Forms :**

    CRÉER → GOUVERNER → PUBLIER → PROCESSUS DE CAPTURE → D’INTÉGRATION → D’→ SUIVI → D’ARCHIVAGE → AMÉLIORER
    ↓        ↓        ↓         ↓         ↓         ↓          ↓       ↓        ↓
    Design   Révision   Déployer   Collecter   Poignée   Connexion   Magasin de moniteurs   Optimiser
    ↑                                                                              ↓
    ←←←←←←←←←←←←←←← Continuous Improvement Loop ←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←

### Créer : conception et développement de formulaire {#create}

Créez des formulaires adaptatifs à l’aide de plusieurs approches de création personnalisées en fonction de différents besoins et exigences techniques.

**Créateur de formulaires visuels**
Concevez des formulaires réactifs par le biais d’interfaces glisser-déposer à l’aide de [Composants principaux](/help/forms/creating-adaptive-form-core-components.md), [Composants de base](/help/forms/creating-adaptive-form.md) ou [Edge Delivery Services](/help/edge/docs/forms/overview.md). L’éditeur visuel fournit un retour d’informations immédiat tout en conservant un balisage sémantique propre qui fonctionne sur tous les appareils et technologies d’assistance.

**Création basée sur des documents**
Créez des formulaires à l’aide d’outils familiers tels que Microsoft Excel via [Edge Delivery Services](/help/edge/docs/forms/overview.md). Cette approche permet aux auteurs de contenu de créer des formulaires hautes performances sans expertise technique, tout en obtenant des scores Google Lighthouse exceptionnels.

**Modèles et thèmes**
Accélérez la création de formulaires à l’aide de [modèles](/help/forms/template-editor-core-components.md) préconfigurés qui définissent la structure et le contenu initial. Appliquez une stratégie de marque cohérente avec des [thèmes](/help/forms/using-themes-in-core-components.md) qui contrôlent le style visuel sur plusieurs formulaires, assurant ainsi la cohérence de la conception et réduisant le temps de développement.

**Intégrations de données**
Connectez les formulaires aux systèmes principaux pendant la phase de conception. Le [modèle de données de formulaire](/help/forms/create-form-data-models.md) fournit une interface unifiée vers plusieurs sources de données, permettant [préremplissage](/help/forms/prepopulate-adaptive-form-fields.md), [règles de validation](/help/forms/rule-editor-core-components.md) et un flux de données transparent entre les formulaires et les systèmes d’entreprise.

**Validations et logique conditionnelle**
Implémentez la [logique conditionnelle](/help/forms/rule-editor-core-components.md), la divulgation progressive et la validation adaptative pour guider les utilisateurs et utilisatrices à travers des processus complexes. La fonctionnalité [Enregistrer et reprendre](/help/forms/save-core-component-based-form-as-draft.md) permet aux utilisateurs de remplir des formulaires sur plusieurs sessions.

**HTML5 Forms**
Effectuez le rendu des formulaires XFA sous la forme de [formulaires HTML5](/help/forms/introductionhtml5.md) pour les appareils mobiles et les navigateurs hérités. HTML5 Forms offre une expérience mobile native sans modules externes tout en conservant la logique de formulaire et la validation à partir des modèles XDP d’origine.

**Communications interactives**
Créez des communications orientées document telles que des relevés, des factures et des avis à l’aide d’un éditeur visuel. Les [communications interactives](/help/forms/interactive-communication/create-interactive-communication.md) associent du contenu statique à des données dynamiques pour générer des communications personnalisées sur les canaux papier et numériques.

### Gouverner : examen et conformité {#govern}

Établissez des processus de supervision et d’approbation pour vous assurer que les formulaires répondent aux normes organisationnelles et aux exigences réglementaires.

**Validations basées sur des workflows**
Acheminez les conceptions de formulaire par le biais de processus de révision à plusieurs étapes avec des affectations basées sur les rôles. Les parties prenantes peuvent [examiner](/help/forms/create-reviews-forms.md), [commenter](/help/forms/add-comments-annotations-versioning-adaptive-form-core-components.md) et approuver les formulaires avant leur publication, en maintenant le contrôle qualité et la supervision de la conformité à l’aide des [workflows AEM](/help/forms/aem-forms-workflow.md).

**Gestion des versions**
Effectuez le suivi des versions de formulaires et conservez les pistes d’audit pour la conformité réglementaire. Le [contrôle de version](/help/forms/add-comments-annotations-versioning-adaptive-form-core-components.md) intégré vous permet de restaurer des modifications, de comparer des itérations et de conserver des enregistrements historiques pour les audits de conformité.

**Contrôle d’accès et autorisations**
Définissez des autorisations granulaires pour la création, la modification et la publication de formulaires. L’[accès en fonction du rôle](/help/forms/forms-groups-privileges-tasks.md) garantit que seuls les utilisateurs et utilisatrices autorisés peuvent modifier les formulaires, tout en maintenant la séparation des tâches pour les processus métier sensibles.

### Publication : distribution multicanal {#publish}

Déployez des formulaires sur plusieurs canaux et points de contact pour atteindre les utilisateurs où qu’ils se trouvent.

**Publication omnicanale**
Publiez des formulaires dans [AEM Sites](/help/forms/embed-adaptive-form-aem-sites.md), des pages web autonomes, des applications mobiles ou [incorporés dans des systèmes tiers](/help/forms/embed-adaptive-form-core-components-external-web-page.md). La publication mono-source assure la cohérence tout en s’adaptant aux différentes exigences des canaux.

**Localisation et Personalization**
Diffuser des formulaires dans plusieurs langues à l’aide de [workflows de traduction AEM](/help/forms/using-aem-translation-workflow-to-localize-adaptive-forms-core-components.md) avec prise en charge des langues [de gauche à droite et de droite à gauche](/help/forms/right-left-languages.md). Intégrez-la à Adobe Target pour personnaliser les expériences de formulaire en fonction des segments d’utilisateurs, du comportement ou des données contextuelles.

**Optimisation des performances**
Tirez parti de Edge Delivery Services pour un chargement de formulaire ultra-rapide et des performances SEO optimales. Les réseaux de diffusion de contenu garantissent une accessibilité globale avec une latence minimale.

**Portail Forms**
Créez des référentiels de formulaires centralisés dans lesquels les utilisateurs peuvent découvrir des formulaires, y accéder et les gérer. [Forms Portal](/help/forms/configure-forms-portal.md) offre des fonctionnalités de recherche, de catégorisation des formulaires, de gestion des brouillons et de suivi des envois dans une interface unifiée pour une expérience utilisateur améliorée.

### Capture : expérience utilisateur et collecte de données {#capture}

Optimisez l’expérience de remplissage de formulaire pour maximiser les taux de remplissage et la qualité des données.

**Responsive Design**
Forms s’adapte automatiquement aux différentes tailles d’écran et méthodes de saisie. Les commandes optimisées pour les écrans tactiles, la navigation au clavier et la compatibilité des lecteurs d’écran garantissent l’[accessibilité](/help/forms/creating-accessible-adaptive-forms.md) pour tous les types d’utilisateurs.

**Signatures numériques**
Intégrez [Adobe Sign](/help/forms/working-with-adobe-sign.md) pour obtenir des signatures électroniques juridiquement contraignantes dans l’expérience de formulaire. Les utilisateurs et utilisatrices peuvent signer des documents sans quitter le formulaire, ce qui simplifie les processus d’approbation et réduit l’abandon.

**Actions Envoyer**
Configurez les [actions d’envoi](/help/forms/configure-submit-actions-core-components.md) pour définir ce qui se passe lorsque les utilisateurs remplissent et envoient des formulaires. Acheminez les données vers des e-mails, des bases de données, des workflows ou des systèmes externes tout en fournissant des commentaires immédiats et une confirmation aux utilisateurs.

### Processus : gestion et routage des envois {#process}

Gérez les envois de formulaires avec des fonctionnalités robustes de traitement, de validation et de routage.

**Validation et traitement des données**
Garantissez l’intégrité des données grâce à la validation côté serveur et aux règles de traitement automatisées. Transformez, validez et acheminez les données envoyées tout en générant des réceptions, des confirmations ou des documents de suivi pour les utilisateurs.

**API Communications**
Générez, manipulez et sécurisez des documents par programmation via les [API RESTful](/help/forms/aem-forms-cloud-service-communications-introduction.md). Créez des fichiers PDF, des formats prêts à être imprimés, assemblez des documents, appliquez des signatures numériques et traitez des volumes importants d’opérations par lots [opérations](/help/forms/aem-forms-cloud-service-communications-batch-processing.md) pour les workflows de documents à l’échelle de l’entreprise.

**Document d’enregistrement**
Générer automatiquement des enregistrements PDF des envois de formulaire pour la conformité et la confirmation utilisateur. [Document d’enregistrement](/help/forms/generate-document-of-record-core-components.md) crée des versions formatées et imprimables des formulaires remplis avec les données envoyées, fournissant ainsi la documentation officielle pour les transactions et les exigences réglementaires.

**Orchestration des workflows**
Déclenchez des processus métier complexes en fonction des envois de formulaire. Acheminez les données via des chaînes d’approbation, affectez des tâches à des utilisateurs spécifiques et automatisez les opérations de routine tout en conservant les pistes d’audit.

**Gestion des erreurs et récupération**
Des mécanismes de reprise intégrés et un traitement de secours garantissent qu’aucune soumission n’est perdue. La journalisation complète permet de résoudre les problèmes et de gérer les contrats de niveau de service.

### Intégrer : connectivité du serveur principal {#integrate}

Connectez les formulaires aux systèmes d’entreprise et aux sources de données existants pour un flux d’informations transparent.

**Connecteurs Préconfigurés**
Intégration native aux solutions [Salesforce](/help/forms/configure-salesforce.md), [Microsoft Dynamics](/help/forms/configure-msdynamics.md), [SharePoint](/help/forms/connect-forms-to-sharepoint-document-library.md) et Adobe Experience Cloud. Les connecteurs préconfigurés réduisent le temps de développement tout en assurant une synchronisation fiable des données.

**Intégration de l’API RESTful**
Connectez-vous à un service accessible sur le web via des API RESTful via des [actions d’envoi](/help/forms/configure-submit-action-restpoint.md) ou [intégration de données](/help/forms/data-integration.md). Le modèle de données de formulaire abstrait la complexité de l’intégration, fournissant une interface cohérente quelle que soit l’architecture du système sous-jacent.

**Échange De Données En Temps Réel**
Activez le flux de données bidirectionnel entre les formulaires et les systèmes d’entreprise. Préremplissez des formulaires à partir d’enregistrements existants, validez les données actives et mettez à jour plusieurs systèmes simultanément lors de leur envoi grâce à une [&#x200B; intégration de données](/help/forms/data-integration.md) complète.

### Suivi : analyses et surveillance des performances {#track}

comprendre les performances des formulaires et le comportement des utilisateurs grâce à des analyses et une surveillance complètes ;

**Form Analytics**
Suivez les taux d’achèvement, les schémas d’abandon et les interactions au niveau du champ grâce à l’intégration [d’Adobe Analytics](/help/forms/integrate-aem-forms-with-adobe-analytics.md). Identifiez les points de friction, mesurez les entonnoirs de conversion et comprenez le comportement des utilisateurs sur différents segments.

**Surveillance des performances**
Surveillez les temps de chargement des formulaires, les taux de réussite des envois et les performances du système. Les tableaux de bord en temps réel fournissent des informations sur les mesures techniques d’intégrité et d’expérience utilisateur.

**Business Intelligence**
Générer des rapports sur l’utilisation des formulaires, les volumes d’envoi et l’efficacité des processus. Analytics aide à la planification des capacités, à l’optimisation de l’expérience utilisateur et aux améliorations des processus métier.

**Rapports de transaction**
Surveillez l’utilisation des API, les volumes de génération de documents et les [transactions facturables](/help/forms/transaction-reports-billable-apis.md) dans votre déploiement d’AEM Forms. Suivez les schémas de consommation, optimisez l’allocation des ressources et respectez les exigences de licence basées sur l’utilisation.

### Archive : gestion des documents et conformité {#archive}

Stockez et gérez en toute sécurité les envois de formulaires et les documents générés pour une conservation et une conformité à long terme.

**Stockage de documents**
Stockez les documents générés et les envois de formulaires dans le système de gestion des ressources numériques d’AEM ou intégrez-les à des référentiels de documents externes tels que [SharePoint](/help/forms/configure-submit-action-sharepoint.md), [OneDrive](/help/forms/configure-submit-action-onedrive.md) ou [Azure Blob Storage](/help/forms/configure-submit-action-azure-blob-storage.md).

**Conformité et conservation**
Mettre en œuvre des politiques de conservation des données conformes aux exigences réglementaires, notamment le RGPD, le CCPA et la loi HIPAA. [Processus d’archivage automatisés](/help/forms/aem-forms-cloud-service-communications-batch-processing.md) assurez-vous que les documents sont conservés pendant les périodes requises et éliminés en toute sécurité le cas échéant.

**Sécurité et contrôle d’accès**
Appliquez le chiffrement, les signatures numériques et les [contrôles d’accès en fonction du rôle](/help/forms/forms-groups-privileges-tasks.md) aux documents archivés. Les journaux d’audit effectuent le suivi de l’accès aux documents et des modifications pour le reporting de conformité et la supervision de la sécurité.

### Améliorer : Optimisation et amélioration {#improve}

Optimisez en permanence les performances des formulaires et l’expérience utilisateur par le biais d’informations et de tests pilotés par les données.

**Intégration des tests A/B**
Utilisez Adobe Target pour tester différentes dispositions de formulaires, dispositions de champs et flux d’utilisateurs. L’analyse statistique permet d’identifier les approches les plus efficaces pour différents segments d’utilisateurs et cas d’utilisation.

**Optimisation pilotée par Analytics**
Analysez les données de comportement des utilisateurs et utilisatrices afin d’identifier les opportunités d’amélioration. [Consultez et comprenez les rapports d’analyse](/help/forms/view-understand-aem-forms-analytics-reports.md) pour la cartographie thermique, l’analyse des interactions de champs et la reconnaissance des motifs d’abandon afin d’éclairer les améliorations de conception itératives.

**Amélioration Itérative**
Mettez en œuvre des processus d’amélioration continue en fonction des commentaires des utilisateurs, des mesures de performances et des besoins de l’entreprise. Les fonctionnalités de [contrôle de version](/help/forms/add-comments-annotations-versioning-adaptive-form-core-components.md) et de restauration permettent une expérimentation sécurisée et une itération rapide.

## Prise en main {#getting-started}

L&#39;approche que vous adoptez dépend de vos besoins immédiats et de vos objectifs à long terme.

### Démarrage rapide : Forms simple {#quick-start}

Choisissez votre approche de création préférée en fonction de votre expérience technique et de vos exigences de performances :

**Création visuelle de formulaire :**

1. **[Créer des formulaires adaptatifs avec des composants principaux](/help/forms/creating-adaptive-form-core-components.md)** pour des formulaires modernes et réactifs
2. **[Configurer des actions d’envoi](/help/forms/configure-submit-actions-core-components.md)** pour gérer les données de formulaire
3. **[Incorporer des formulaires dans AEM Sites](/help/forms/embed-adaptive-form-aem-sites.md)** ou les partager via des liens directs

**Création basée sur des documents :**

1. **[Créer des formulaires à l’aide d’Excel](/help/edge/docs/forms/create-forms.md)** avec Edge Delivery Services pour les formulaires haute performance
2. **[Publication sur Edge Delivery](/help/edge/docs/forms/publish-forms.md)** pour des vitesses de chargement et une optimisation du moteur de recherche optimales

**Prise en charge des formulaires hérités :**

- **[HTML5 Forms](/help/forms/introductionhtml5.md)** pour le rendu de formulaire XFA optimisé pour les appareils mobiles

### Implémentation avancée : processus métier {#advanced-implementation}

Pour les besoins complexes impliquant plusieurs systèmes, la génération de documents et les workflows d’approbation :

**Intégration et workflows de données :**

1. **[Configurer des modèles de données de formulaire](/help/forms/create-form-data-models.md)** pour connecter les systèmes principaux
2. **[Conception de processus de workflow](/help/forms/aem-forms-workflow.md)** pour la validation et le routage
3. **[Configurer les analyses](/help/forms/integrate-aem-forms-with-adobe-analytics.md)** pour mesurer les performances

**Services de document et communications :**

1. **[Implémentation des API Communications](/help/forms/aem-forms-cloud-service-communications-introduction.md)** pour la génération automatisée de documents
2. **[Créer des communications interactives](/help/forms/interactive-communication/create-interactive-communication.md)** pour les relevés et avis personnalisés
3. **[Configuration du portail Forms](/help/forms/configure-forms-portal.md)** pour une gestion centralisée des formulaires

### Déploiement en entreprise : échelle et gouvernance {#enterprise-deployment}

Pour les déploiements à l’échelle de l’organisation nécessitant gouvernance, conformité et surveillance :

**Architecture et gouvernance :**

1. **[Examen des modèles d’architecture](/help/forms/aem-forms-cloud-service-architecture.md)** pour un déploiement évolutif
2. **[Configuration de la gestion des utilisateurs](/help/forms/forms-groups-privileges-tasks.md)** et des contrôles d’accès
3. **[Configurer des workflows de développement](/help/forms/setup-local-development-environment.md)** pour la collaboration d’équipe

**Migration et surveillance :**

1. **[Planifier les stratégies de migration](/help/forms/migrate-to-forms-as-a-cloud-service.md)** à partir des systèmes existants
2. **[Implémenter la surveillance des transactions](/help/forms/transaction-reports-billable-apis.md)** pour le suivi de l’utilisation et la conformité

<details>
<summary><strong> ❓ questions fréquentes </strong></summary>

**Qu’est-ce qu’un créateur de formulaires ?**
Un créateur de formulaires est un outil qui vous permet de créer des formulaires numériques sans codage. Vous pouvez concevoir des formulaires à l’aide d’interfaces glisser-déposer, ajouter des champs tels que des zones de texte et des listes déroulantes, et les publier en ligne pour collecter des données auprès des utilisateurs.

**Comment créer un formulaire en ligne ?**
Avec AEM Forms, vous pouvez créer des formulaires adaptatifs à l’aide des composants principaux par le biais d’un éditeur visuel par glisser-déposer, créer des formulaires hautes performances avec Edge Delivery Services ou utiliser des composants de base pour des workflows établis. Commencez par sélectionner un modèle, ajoutez des champs de formulaire, configurez des connexions de données et publiez sur plusieurs canaux.

**Qu’est-ce qui fait un bon formulaire en ligne ?**
Les bons formulaires en ligne sont réactifs sur les appareils mobiles, se chargent rapidement, ont des libellés clairs, utilisent l’ordre logique des champs, incluent la validation pour éviter les erreurs et fournissent un retour immédiat aux utilisateurs lors de l’envoi.

**Puis-je intégrer des formulaires à d’autres systèmes d’entreprise ?**
Oui, les créateurs de formulaires modernes offrent des fonctionnalités d’intégration étendues. Vous pouvez connecter des formulaires à des systèmes CRM, des plateformes de marketing par e-mail, des bases de données, un stockage dans le cloud et des outils d’automatisation des workflows afin de rationaliser vos processus d’entreprise.

**Les formulaires en ligne sont-ils sécurisés ?**
Les créateurs de formulaires professionnels incluent des fonctionnalités de sécurité de niveau entreprise telles que le chiffrement des données, la transmission sécurisée des données, les contrôles d’accès et la conformité aux réglementations telles que le RGPD, la loi HIPAA et la loi CCPA pour protéger les informations sensibles.

**Comment ajouter des signatures électroniques à mes formulaires ?**
Les signatures numériques peuvent être intégrées directement aux formulaires à l’aide d’Adobe Sign ou d’autres fournisseurs de signatures électroniques. Cela permet aux utilisateurs de signer des documents dans l’expérience de formulaire, ce qui élimine la nécessité de processus de signature distincts et réduit l’abandon de formulaire.

**Les formulaires peuvent-ils générer automatiquement des documents PDF ?**
Oui, les plateformes de formulaires modernes peuvent générer automatiquement des accusés de réception, des confirmations ou des documents d’enregistrement PDF lors de l’envoi des formulaires. Cela est essentiel pour la conformité, la conservation des enregistrements et la confirmation immédiate aux utilisateurs.

**Comment effectuer le suivi des performances et des analyses des formulaires ?**
L’analyse des formulaires vous aide à comprendre les taux d’achèvement, les modèles d’abandon et le comportement des utilisateurs. L’intégration aux plateformes d’analyse telles qu’Adobe Analytics fournit des informations sur les champs qui provoquent des frictions et sur la manière d’optimiser les taux de conversion.

**Qu’est-ce que l’automatisation des workflows de formulaire ?**
L’automatisation des workflows de formulaire achemine les envois par le biais de processus d’approbation, affecte des tâches aux membres de l’équipe et déclenche des actions dans d’autres systèmes d’entreprise. Cela élimine le traitement manuel et garantit une gestion cohérente des données de formulaire.

**Comment rendre les formulaires accessibles aux utilisateurs en situation de handicap ?**
Les [formulaires accessibles](/help/forms/creating-accessible-adaptive-forms.md) incluent un étiquetage correct, une navigation au clavier, une compatibilité avec les lecteurs d’écran et la conformité aux directives WCAG. Cela permet à tous les utilisateurs et utilisatrices de remplir des formulaires, quelles que soient leurs capacités ou leurs technologies d’assistance.

**Combien coûtent les créateurs de formulaires ?**
Le prix d’AEM Forms as a Cloud Service dépend de vos besoins spécifiques, du volume d’utilisation et des fonctionnalités demandées. Pour obtenir des informations détaillées sur les prix et discuter d’une solution adaptée à votre organisation, contactez le service commercial Adobe ou votre représentant Adobe.

</details>

## Étapes suivantes {#next-steps}

Explorez les fonctionnalités qui correspondent à vos priorités actuelles :

- **[Créer votre premier formulaire](/help/forms/creating-adaptive-form-core-components.md)** pour tester l’environnement de création
- **[Revoir les options d’architecture](/help/forms/aem-forms-cloud-service-architecture.md)** pour la planification du déploiement
- **[Configurer votre environnement de développement](/help/forms/setup-local-development-environment.md)** pour la collaboration d’équipe
- **[Explorer les options d’intégration](/help/forms/data-integration.md)** pour connecter les systèmes existants

Pour obtenir des conseils d’implémentation complets, pensez à Adobe Professional Services afin d’accélérer votre déploiement et d’appliquer les bonnes pratiques dès le départ.
