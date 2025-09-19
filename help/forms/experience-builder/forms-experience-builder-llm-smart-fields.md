---
title: Champs intelligents améliorés par LLM dans Forms Experience Builder
description: Découvrez comment créer des champs de formulaire intelligents avec des options préremplies à l’aide de la base de connaissances de l’IA pour les données géographiques, les classifications d’entreprise et les normes du secteur.
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: de524aeddd5f53cbd713ff0523222966752ebbc0
workflow-type: tm+mt
source-wordcount: '1474'
ht-degree: 0%

---


# Champs intelligents améliorés par LLM dans Forms Experience Builder {#llm-enhanced-smart-fields}

Forms Experience Builder tire parti de la puissance des grands modèles de langage (LLM) pour créer des champs de formulaire intelligents avec des options préremplies qui s’appuient sur des bases de connaissances complètes. Cette fonctionnalité élimine le besoin de rechercher et de saisir manuellement des jeux de données volumineux, améliorant considérablement l’efficacité et la précision de la création de formulaires.

## Que sont les champs intelligents optimisés par LLM ? {#what-are-llm-smart-fields}

Les champs intelligents optimisés pour LLM sont des champs de formulaire qui sont automatiquement renseignés avec des données complètes et précises à l’aide de la base de connaissances intégrée de l’IA. Au lieu de créer manuellement des listes déroulantes ou des jeux d’options, vous pouvez demander des champs qui nécessitent des jeux de données volumineux, et l’IA générera automatiquement les options appropriées.

**Principaux avantages :**

* **Jeux de données complets** - Accès à des informations complètes et à jour sur plusieurs domaines
* **Population automatique** - Pas besoin de rechercher et de saisir manuellement les données
* **Formats normalisés** - Utilise des codes, des classifications et des conventions de dénomination standard
* **Options contextuelles** - Les champs peuvent s’adapter en fonction des autres sélections de formulaire
* **Gain de temps** - Réduit le temps de création de formulaire de quelques heures à quelques minutes

## Quand utiliser les champs intelligents améliorés par LLM ? {#when-to-use-smart-fields}

Utilisez des champs intelligents optimisés par LLM lorsque vous avez besoin des éléments suivants :

* **Jeux de données complets** - Champs nécessitant des informations complètes et normalisées
* **Normes du secteur** - Classifications, codes ou données réglementaires
* **Informations géographiques** - Lieux, régions ou divisions administratives
* **Données professionnelles** - Titres de poste, certifications ou classifications de secteur
* **Normes techniques** - Formats de fichiers, protocoles ou spécifications système

## Champs géographiques et de localisation {#geographic-location-fields}

Créez des champs basés sur l’emplacement avec des données géographiques et des informations administratives complètes.

### Aéroports et transports

**Aéroports internationaux avec codes IATA :**

    Ajouter un menu déroulant pour les aéroports de départ avec tous les principaux aéroports internationaux
    Ajouter le champ de l&#39;aéroport d&#39;arrivée avec les codes IATA et les noms complets
    Créer un champ pour l&#39;aéroport le plus proche de l&#39;emplacement de l&#39;utilisateur
    Ajouter une sélection de gares pour les villes européennes

**Exemples d’invites :**

* « Ajouter un champ d&#39;aéroport de départ avec tous les principaux aéroports du monde entier, y compris les codes IATA et les noms de ville »
* « Créer une liste déroulante d’aéroport d’arrivée avec les aéroports internationaux organisés par continent »
* « Inclure une sélection de gares pour les grandes villes européennes avec des codes de gare »

### Régions administratives

**Pays, états et provinces :**

    Ajouter une liste complète des États américains avec des abréviations
    Créer une liste déroulante de pays avec des codes ISO et des noms complets
    Ajouter un champ pour les grandes villes du monde avec des fuseaux horaires
    Inclure une liste déroulante des provinces et territoires canadiens
    Ajouter un champ pour les comtés et zones postales du Royaume-Uni

**Exemples d’invites :**

* « Créer un champ de sélection de pays avec des codes de pays ISO et des noms complets »
* « Ajout d’une liste déroulante d’État américain avec les abréviations des États et les noms complets. »
* « Incluez un champ Province canadienne avec les territoires et les codes postaux. »
* « Créez un champ de villes du monde avec les principales zones métropolitaines et les fuseaux horaires »

## Données relatives aux entreprises et au secteur {#business-industry-data}

Tirez parti de classifications professionnelles et de données professionnelles complètes pour les formulaires d’entreprise.

### Classifications d&#39;entreprise

**Types d’entités métier et métier :**

    Ajoutez un champ pour la classification des industries avec les codes SCIAN
    Créez une liste déroulante des types d&#39;entités commerciales (LLC, Corporation, Société de personnes, etc.)
    Ajouter un champ pour les catégories de taille d’entreprise (démarrage, PME, entreprise)
    Inclure la sélection de service pour les grandes organisations
    Ajouter un champ pour les types de services professionnels

**Exemples d’invites :**

* « Créer un domaine industriel complet à l&#39;aide de la classification SCIAN normalisée avec sous-catégories technologiques »
* « Ajouter une liste déroulante de type entité commerciale avec des structures et des descriptions juridiques »
* « Inclure un champ Taille de société avec des plages de nombres d’employés et des tranches de revenus »

### Classifications professionnelles

**Titres de poste et certifications :**

    Ajoutez un champ pour les titres de poste avec des rôles courants du secteur
    Créez une liste déroulante des certifications professionnelles par champ
    Incluez les niveaux de formation avec les types de diplômes
    Ajoutez un champ pour les périodes d’expérience
    Créez une sélection pour les langages et les structures de programmation

**Exemples d’invites :**

* « Inclure un menu déroulant de certification professionnelle qui s’adapte en fonction du champ de tâche sélectionné »
* « Créez un champ intitulé de poste avec des rôles communs dans les domaines de la technologie, de la santé et de la finance »
* « Ajouter un champ de niveau d’études avec les types de diplômes et les spécialisations »

## Normes et données réglementaires {#standards-regulatory-data}

Accédez à des codes, des classifications et des informations réglementaires normalisés pour les formulaires axés sur la conformité.

### Financier et juridique

**Informations sur la devise, la taxe et le paiement :**

    Ajouter un champ pour les codes devise avec des symboles et des taux de change
    Créer une liste déroulante des types d&#39;ID taxe par pays
    Inclure un champ pour les types de documents juridiques
    Ajouter des options de mode de paiement avec des fonctions de sécurité
    Créer une sélection pour les établissements bancaires par pays

**Exemples d’invites :**

* « Créez un champ de sélection de devise avec des codes ISO, des symboles et les taux de change principaux. »
* « Ajouter un champ de type identifiant de taxe avec des formats d&#39;identification de taxe spécifiques au pays »
* « Incluez un menu déroulant de mode de paiement avec les fonctionnalités de sécurité et les délais de traitement. »

### Normes techniques

**Formats et protocoles de fichiers :**

    Ajout d’une liste déroulante de types de format de fichier avec les extensions
    Inclusion des options de protocole réseau
    Ajout d’un champ pour les types et versions de base de données
    Création d’une sélection pour les méthodes d’authentification d’API

**Exemples d’invites :**

* « Création d’une liste déroulante de format de fichier avec les extensions et les types MIME courants »
* « Ajout d’un champ de sélection de base de données avec des comparaisons de versions et de fonctionnalités »
* « Inclure un champ de méthode d’authentification API avec les niveaux de sécurité »

## Domaine médical et de la santé {#healthcare-medical-fields}

Données médicales et médicales spécialisées pour les formulaires spécifiques au secteur.

### Classifications médicales

**Spécialités et données médicales :**

    Ajouter un champ pour les spécialités médicales
    Créer une liste déroulante de médicaments courants avec des noms génériques
    Inclure un champ pour les types de fournisseurs d’assurance
    Ajouter une sélection pour les relations de contact en cas d’urgence médicale
    Créer un champ pour les restrictions alimentaires et les allergies

**Exemples d’invites :**

* « Créer un domaine de spécialité médicale avec des sous-spécialités et des certifications de conseil »
* « Ajoutez un champ de médicaments avec les noms génériques, les noms de marque et les formes posologiques. »
* « Inclure un champ de fournisseur d’assurance avec les principaux transporteurs et les types de plan »

## Intelligence temporelle et calendaire {#time-calendar-intelligence}

Champs de date et d’heure intelligents avec contexte commercial et intelligence de planification.

### Champs Date et heure

**Heures d’ouverture et planification :**

    Ajouter un champ pour les heures ouvrables avec gestion des fuseaux horaires
    Créer une liste déroulante des jours fériés par pays
    Inclure des options saisonnières avec périodes
    Ajouter un champ pour la réservation de salle de conférence avec disponibilité
    Créer une sélection pour les modèles de réunion récurrents

**Exemples d’invites :**

* « Créer un champ d’heures ouvrables avec des fuseaux horaires et des exceptions de vacances »
* « Ajouter une sélection de jours fériés avec des célébrations spécifiques à chaque pays »
* « Inclure un champ de modèle de réunion récurrent avec des options de fréquence »

## Catégories de produits et de services {#product-service-categories}

Le commerce électronique et les domaines axés sur les services avec une catégorisation complète.

### Classifications e-commerce

**Données de produit et de service :**

    Ajouter un champ pour les catégories de produits avec des sous-catégories
    Créer une liste déroulante de modes d’expédition avec des estimations de diffusion
    Inclure un champ pour les options de politique de retour
    Ajouter une sélection pour les niveaux de priorité des clients
    Créer un champ pour les cycles de facturation des abonnements

**Exemples d’invites :**

* « Créez un champ de catégorie de produits avec des sous-catégories d’e-commerce et des modèles de SKU »
* « Ajouter un menu déroulant des méthodes d’expédition avec les délais de livraison et les estimations de coûts »
* « Inclure un champ de cycle de facturation d’abonnement avec les fréquences de paiement »

## Bonnes pratiques relatives aux champs intelligents optimisés pour LLM {#best-practices-smart-fields}

### Soyez précis dans vos requêtes

**Bons exemples :**

* « Ajoutez un menu déroulant de pays avec les codes ISO, les noms complets et les informations sur la devise. »
* « Créer un domaine de spécialité médicale avec des certifications de conseil et des sous-spécialités »
* « Inclure un champ de langage de programmation avec les frameworks et les niveaux de compétence »

**Évitez les requêtes vagues :**

* « Ajouter un champ pays »
* « Créer un menu déroulant d’intitulé de poste »
* « Inclure un champ de catégorie de produits »

### Combinaison avec une logique conditionnelle

Les champs intelligents fonctionnent exceptionnellement bien avec les règles conditionnelles :

    Créez un champ de certification professionnelle qui affiche les options pertinentes en fonction du secteur d’activité sélectionné
    Ajoutez un champ Ville qui filtre en fonction du pays sélectionné
    Incluez un champ Université qui s’adapte en fonction du domaine d’études choisi

### Valider et personnaliser

Bien que les champs améliorés par LLM fournissent des données complètes, toujours :

* **Examiner les options générées** pour en vérifier la précision et la pertinence
* **Ajouter des options personnalisées** spécifiques à votre organisation
* **Supprimer les options non pertinentes** pour rationaliser l’expérience utilisateur
* **Tester avec des utilisateurs réels** pour garantir la convivialité

## Techniques de champ intelligent avancées {#advanced-smart-field-techniques}

### Champs basés sur le contexte

Créez des champs qui s’adaptent en fonction d’autres sélections de formulaire :

    Ajoutez un champ de sélection d’université avec les principaux établissements organisés par pays et par classement
    Créez un menu déroulant de certification professionnelle qui affiche les options pertinentes en fonction de la fonction
    Incluez un champ de ville qui filtre en fonction du pays et de la région sélectionnés

### Classifications à plusieurs niveaux

Créer des structures de données hiérarchiques :

    Créez un champ de catégorie de produits avec les catégories principales, les sous-catégories et les types de produits
    Ajoutez un champ géographique avec les niveaux de pays, d’État/province et de ville
    Incluez un champ d’évaluation des compétences avec les catégories, les sous-catégories et les niveaux de compétence

### Intégration avec des données externes

Combinez les connaissances LLM avec les données de votre organisation :

    Ajoutez un champ Service qui comprend à la fois les services standard de l’entreprise et les divisions spécifiques de votre organisation
    Créez un champ de produit qui combine des catégories standard du secteur avec votre catalogue de produits
    Incluez un champ d’emplacement qui fusionne les données géographiques avec les emplacements de vos bureaux

## Résolution des problèmes liés aux champs intelligents {#troubleshooting-smart-fields}

### Problèmes courants et solutions

**Problème : trop d’options générées**

* **Solution** : soyez plus précis dans votre requête ou ajoutez des critères de filtrage
* **Exemple** : au lieu de « tous les pays », demandez « principaux pays partenaires commerciaux »

**Problème : options spécifiques manquantes**

* **Solution** : ajoutez des options personnalisées ou affinez votre invite
* **Exemple** : « Inclure les principaux pays plus [vos pays spécifiques] »

**Problème : informations obsolètes**

* **Solution** : demandez les données actives ou spécifiez des périodes.
* **Exemple** : « Ajouter les jours fériés actuels de 2024 »

### Optimisation des performances

* **Options de limite** : utilisez des filtres pour réduire le nombre d’options générées
* **Divulgation progressive** : Affichez d’abord les options de base, puis autorisez l’extension
* **Mise en cache** : envisagez de mettre en cache les données de champ intelligent fréquemment utilisées

## Articles connexes

* [Prise en main de Forms Experience Builder](forms-experience-builder-getting-started.md)
* [Création de formulaires optimisée par l’IA](forms-experience-builder-prompt-examples-library.md)
* [Création de règles et logique commerciale](forms-experience-builder-prompt-examples-library.md#rule-creation--business-logic)
* [Envoi et intégration du formulaire](form-submission-integration.md)

