---
title: Forms Experience Builder
description: Créer des formulaires puissants plus rapidement à l’aide de fragments de formulaire
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: 6134772ea9916fc17fb7fc8a30e18799a81d4994
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 4%

---


# Présentation de Forms Experience Builder

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette documentation est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les fonctionnalités, commandes et exemples peuvent changer à mesure que le Forms Experience Builder continue d’évoluer au cours du programme destiné aux utilisateurs et utilisatrices précoces.

AEM Forms Experience Builder tire parti de la puissance de Generative AI pour démocratiser et accélérer la création et la mise à jour d’expériences de formulaires numériques. En activant des workflows basés sur l’intention pilotés par des interactions en langage naturel, il permet aux utilisateurs et aux utilisatrices de concevoir, modifier et optimiser les formulaires en toute simplicité et rapidité.

Basé sur des technologies web modernes et optimisé par des services d’IA avancés, le Forms Experience Builder permet aux utilisateurs techniques et non techniques de créer des formulaires sophistiqués de qualité professionnelle par le biais d’interfaces de conversation. Cette approche révolutionnaire réduit le délai de rentabilisation de plusieurs jours à plusieurs heures, élimine les obstacles techniques grâce à la simplicité de l’interface et adapte les efforts de modernisation à l’ensemble de votre écosystème de formulaires.



## Fonctionnalités principales

Forms Experience Builder propose deux workflows principaux pour créer des formulaires numériques puissants :

### &#x200B;1. Création de formulaires optimisée par l’IA

**Génération de formulaires en langage naturel**

Créez des formulaires complets à partir de zéro à l’aide de descriptions en anglais simples. Il vous suffit de décrire vos exigences, telles que « Créer un formulaire de commentaires client avec des échelles de notation et des champs de commentaire », pour que le Forms Experience Builder génère la structure de formulaire appropriée. Vous utilisez le créateur d’expériences des éditeurs visuels pour ajouter d’autres champs, des règles de validation et une logique d’envoi.

**Dynamic Field Management**

Ajouter, modifier ou supprimer des champs de formulaire par le biais de commandes de conversation. L’IA comprend le contexte et peut suggérer intelligemment des types de champs, des règles de validation et des améliorations de l’interface utilisateur en fonction de vos besoins.

**Optimisation de la disposition**

Mettez à jour les dispositions et configurations de formulaire en langage naturel. Demandez des modifications telles que « Modification de la disposition du formulaire dans la disposition de l’assistant » et le Forms Experience Builder appliquera le style et les ajustements de disposition appropriés.

**Configuration complète de l’action Envoyer**

Configurez les envois de formulaire à intégrer à vos systèmes d’entreprise existants :

- **Intégration de la messagerie électronique** : configurer des notifications et des confirmations automatisées par courrier électronique
- **Points d’entrée de l’API REST** : connexion à des applications et services personnalisés
- **Stockage dans le cloud** : intégration à Azure Blob Storage, SharePoint et OneDrive
- **Automatisation des workflows** : connexion à Power Automate et Workfront Fusion
- **Plateformes marketing** : intégration directe à Marketo pour la gestion des prospects
- **Workflows AEM** : tirer parti des fonctionnalités existantes des workflows AEM


### &#x200B;2. Importation et conversion intelligentes

**Formats d’importation pris en charge**

Transformer des formulaires et des documents existants en expériences digitales interactives. Forms Experience Builder prend en charge les éléments suivants :

- **Acroforms** : PDF forms interactive avec structures de champ existantes
- **PDF XFA** : architectures de formulaires complexes basées sur XML
- **PDF plats** : documents statiques convertis en formulaires interactifs
- **Images et captures d’écran** : JPG, formats PNG (vérifiez les limites de taille auprès de l’équipe).
- **Forms dessiné à la main** : croquis et photographies de formulaires papier


**Processus de conversion intelligent**

Le contenu chargé est analysé pour :

- Détecter les types de champs et les relations
- Conserver la disposition dans la mesure du possible
- Améliorez avec un design réactif moderne
- Ajouter une validation avancée et une logique conditionnelle
- Optimiser l’accessibilité et l’expérience mobile

## Fonctionnement

Le créateur d’expérience Forms suit une approche simple et conversationnelle :

    ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
    │ 1. Décrire    │───▶│ 2. L’IA crée des │───▶│ 3. Affiner et    │
    │ Votre Formulaire      │    │ formulaire initial   │    │ Configurer      Exigences │
    │   │    │                 │    │                 │
    └─────────────────┘    └─────────────────┘    └─────────────────┘
    │                       │                       │
    │                       │                       │
    ▼                       ▼                       ▼
    ┌───────────────────────────────────────────────────────────────────────────┐
    │ « Créer un formulaire de demande de prêt » → Formulaire avec les informations pertinentes                  │
    │ « Ajouter un champ d’e-mail »           Champs → et de base                          │
    │ « Définir la valeur de l’e-mail envoyé à @firstname@gmail.com » → règles de validation   │
    └───────────────────────────────────────────────────────────────────────────┘

## Exemples de scénarios

<div class="columns">
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Transform PDF Forms to Digital Forms">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">Transformation de PDF forms en Forms numérique</p>
                    <p class="is-size-6">Convertissez des documents Acroforms, XFA PDF ou plat PDF en formulaires numériques réactifs et interactifs dotés de fonctionnalités améliorées.</p>
                </div>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Modernize Legacy XFA Forms">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">Moderniser l’ancien Forms XFA</p>
                    <p class="is-size-6">Transformez des applications XFA complexes en expériences numériques modernes et accessibles grâce à des workflows utilisateur améliorés.</p>
                </div>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Convert Screenshots to Digital Forms">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">Convertir des captures d’écran en Forms numérique</p>
                    <p class="is-size-6">Transformez des images, des captures d’écran ou des formulaires dessinés à la main en expériences digitales entièrement fonctionnelles.</p>
                </div>
            </div>
        </div>
    </div>
</div>

<!-- #### Import and Enhance Web Forms

Import existing HTML forms and enhance them with advanced features while preserving existing functionality.

**Key benefits:**

- Advanced validation and business logic
- Conditional field behaviors
- Multi-channel submission options
- Enhanced user experience design -->

## Forms Experience Builder par rapport au développement traditionnel

| Aspect | Création de formulaire traditionnelle | Forms Experience Builder |
|--------|---------------------------|----------------------|
| **Heure de création** | 2-3 jours | 2-3 heures |
| **Connaissances techniques** | Obligatoire | Non requis |
| **Règles de validation** | Codage manuel | Langage naturel |
| **Accessibilité** | Implémentation manuelle | Conformité intégrée |


## Avantages pour les organisations

<div class="columns">
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Democratized Form Creation">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">Création de formulaire démocratisée</p>
                    <p class="is-size-6">Permettre aux utilisateurs non techniques de créer des formulaires sophistiqués sans connaissances en programmation grâce à des conversations en langage naturel.</p>
                </div>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Reduced Time to Value (TTV)">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">Rentabilité réduite (TTV)</p>
                    <p class="is-size-6">Accélérez considérablement le développement des formulaires, de quelques jours à quelques heures, ce qui permet une mise sur le marché plus rapide des initiatives numériques.</p>
                </div>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Interface Simplicity">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">Simplicité de l'interface</p>
                    <p class="is-size-6">Éliminez la courbe d’apprentissage grâce à une interface conversationnelle intuitive, ce qui réduit le temps de formation et accroît l’adoption.</p>
                </div>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Scaling Modernization Efforts">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">Adaptation des efforts de modernisation</p>
                    <p class="is-size-6">Modernisez efficacement les portfolios de formulaires hérités, en préservant la logique commerciale et en améliorant l’expérience utilisateur sur l’ensemble de votre écosystème de formulaires.</p>
                </div>
            </div>
        </div>
    </div>
</div>

## Intégration

Forms Experience Builder est actuellement disponible dans le cadre du programme d’accès anticipé (EA). Pour participer et y accéder, vous aurez besoin des informations suivantes :

### Informations requises

- **ID d’organisation IMS** : identifiant de votre organisation Adobe
- **ID de programme** : identifiant de programme spécifique dans Adobe Experience Cloud
- **Détails du projet** : calendrier, portée et cas d’utilisation prévus
- **E-mail professionnel officiel** : associé au compte Adobe de votre entreprise


### Comment obtenir l’ID d’organisation IMS et l’ID de programme

Pour obtenir des instructions détaillées afin de localiser votre ID d’organisation IMS et votre ID de programme, voir :

- [Guide de configuration de l’organisation Adobe Experience Cloud](/help/onboarding/cloud-manager-introduction.md)
- [Gestion des programmes et de l&#39;environnement](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)

### Demander l’accès

1. Rassemblez votre identifiant d’organisation IMS et votre identifiant de programme à l’aide des guides ci-dessus
2. Envoyer un e-mail à [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) pour demander l’accès
3. Inclure dans votre demande :
   - Nom de l’organisation et ID de l’organisation IMS
   - ID de programme
   - Chronologie et portée du projet
   - Cas d’utilisation prévus et objectifs commerciaux

>[!IMPORTANT]
>
> **Programme de disponibilité limitée** : l’accès à Forms Experience Builder est soumis à l’approbation des parties prenantes internes. Adobe examinera votre demande en fonction de la capacité du programme et de l&#39;alignement sur les critères d&#39;accès anticipé. L’approbation n’est pas garantie et dépend de la disponibilité actuelle du programme.

Pour plus d’informations sur le programme d’accès anticipé et ses fonctionnalités, consultez la [documentation sur l’accès anticipé d’AEM Forms](/help/forms/early-access-ea-features.md).


## Prise en main

Pour commencer à utiliser Forms Experience Builder, consultez la [documentation de Forms Experience Builder](forms-ai-assistant-getting-started.md). Vous pouvez accéder au Forms Experience Builder par le biais de l’éditeur AEM Forms ou de l’éditeur universel, selon votre choix de workflow.

Pour les entreprises qui cherchent à transformer leurs processus de création de formulaires, le Forms Experience Builder offre une solution puissante et intuitive qui combine la flexibilité de l’IA conversationnelle avec la robustesse de la gestion des formulaires de niveau entreprise.
