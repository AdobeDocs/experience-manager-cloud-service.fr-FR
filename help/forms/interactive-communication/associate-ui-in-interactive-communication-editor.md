---
title: Associer l’interface utilisateur dans l’éditeur de communication interactive
description: Découvrez l’interface utilisateur associée dans l’éditeur de communication interactive en permettant à l’agent face au client de générer des communications personnalisées et conformes.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: 19270498fa60f860b31400ad40705ecd2f821cf8
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 3%

---


# Associer l’interface utilisateur dans l’éditeur de communication interactive

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

L’**interface utilisateur associée** est une interface simplifiée spécialisée reposant sur l’éditeur de communications interactives (IC). Il est conçu pour les professionnels en contact avec les clients, tels que les associés de terrain et les agents de service, afin de générer des communications personnalisées, conformes et précises en temps réel lors des interactions en direct.

![Rechercher document IC](/help/forms/interactive-communication/assets/associate-ui-preview.png)

## Associer l’interface utilisateur

L’interface utilisateur d’Associate offre un espace de travail propre à deux panneaux qui permet une génération de communication rapide et sécurisée :

### Volet De Gauche : Entrée De Données

- Les associés saisissent ou confirment les informations spécifiques au client.
- Les validations, les textes d’assistance et les champs obligatoires permettent une saisie précise.

### Panneau De Droite : Aperçu En Temps Réel

- Affiche un aperçu instantané du document final.
- Met automatiquement à jour au fur et à mesure que l’associé remplit les données.

### Génération instantanée de documents

- Générer ou télécharger la communication finalisée.

## Personnages et responsabilités de l’utilisateur

L’interface utilisateur d’Associate repose sur trois rôles principaux, chacun ayant des responsabilités distinctes :

### &#x200B;1. Administrateur

Responsable de la configuration du système, de la gouvernance, des intégrations principales et de l’accès utilisateur.

| Responsabilité | Cible d’action |
|---------------|-------|
| Configuration du système | Configure l’infrastructure de base, les groupes d’utilisateurs, les modèles de données de formulaire (FDM) et la sortie . |
| Gouvernance et sécurité | Gère les autorisations utilisateur et assure la conformité du système. |
| Gestion de l’intégration | Conserve les intégrations du serveur principal et les connexions actives aux données client. |

### &#x200B;2. Auteur

Conçoit et gère la communication interactive à l’aide de l’interface utilisateur associée. ß

| Responsabilité | Cible d’action |
|---------------|-------|
| Création et conception IC | Crée une mise en page, une marque et une structure de document conforme. |
| Configuration de champ | Mappe les champs de données et définit les champs modifiables, obligatoires et en lecture seule. |
| Publication et activation | Publie l’IC et partage le lien pour l’accès associé. |

### &#x200B;3. Associé

Utilise l’interface utilisateur d’Associate pour aider les clients, mettre à jour les informations et générer des communications conformes.


| Responsabilité | Cible d’action |
|---------------|-------|
| Confirmation des données | Remplit ou valide les données client via le panneau de saisie de gauche. |
| Aperçu et validation | Garantit la précision à l’aide du panneau d’aperçu en temps réel. |
| Diffusion | Génère le PDF/l’email et l’envoie via des canaux approuvés. |

>[!NOTE]
>
> L’associé doit faire partie du groupe **forms-associates**.

## Cas d’utilisation dynamiques

L’interface utilisateur d’Associate prend en charge la génération instantanée et personnalisée de documents, essentielle pour les secteurs ayant des besoins de maintenance en temps réel.

| Industrie | Exemples de cas d’utilisation |
|----------|-------------------|
| **Services financiers** | Générer des lettres de confirmation de prêt en temps réel, des résumés de profil de risque, la création de compte. |
| **Assurance** | Produire instantanément des cartes de preuve d&#39;assurance ou des résumés de disposition des réclamations. |
| **Healthcare** | Créez des résumés de plans de traitement des patients avec une copie calculée et des plannings. |
| **Secteur public** | Générer des rapports de vérification de la police, des reçus de services aux citoyens, des lettres d&#39;accusé de réception de grief et des résumés de mise à jour des cas sur place. |
| **Gouvernement** | Créez des résumés de statut de demande, des lettres d&#39;approbation de service et une communication en temps réel pour les inscriptions aux régimes d&#39;assistance sociale. |

## Activation du workflow d’IU associée

L’auteur peut suivre les étapes ci-dessous pour configurer et publier une communication interactive (IC) pour l’accès à l’interface utilisateur associée :

>[!NOTE]
>
> Composants pris en charge pour les associés : champ de date, champ numérique, champ de texte.

### Création de l’ID

Concevez et configurez la communication interactive en veillant à ce que le branding, les liaisons de données, les règles de conformité et les intégrations soient correctement définis.

### Activer l’interface utilisateur d’Associate

Dans la barre d’actions supérieure, activez l’option Associer l’interface utilisateur afin de rendre l’interface utilisateur disponible pour l’interface pilotée par les associés.

### Activer l’interface utilisateur associée dans le composant

### Configurer les champs modifiables

Dans la section Champs obligatoires , activez les champs que les associés peuvent modifier.
Définissez des validations pour garantir une entrée de données précise et contrôlée.

### Publier l’ID

Après avoir finalisé toutes les configurations, publiez la communication interactive pour un accès sécurisé.

### Partager l&#39;IC publié avec des associés

Fournissez le lien IC publié à l&#39;associé, ce qui lui permet de s&#39;authentifier, de saisir des informations spécifiques au client et de générer la communication finale avec des entrées valides.

L’**interface utilisateur associée** comble le fossé entre la création de contenu structuré et l’engagement client en temps réel.\
En associant une conception intuitive, une configuration d’arrière-plan robuste et des contrôles de conformité stricts, les entreprises peuvent fournir des communications **rapides, précises et personnalisées** à grande échelle.
