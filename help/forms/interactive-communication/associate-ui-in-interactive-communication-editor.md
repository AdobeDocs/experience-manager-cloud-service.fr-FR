---
title: Associer l’interface utilisateur dans l’éditeur de communication interactive
description: Découvrez l’interface utilisateur associée dans l’éditeur de communication interactive en permettant à l’agent face au client de générer des communications personnalisées et conformes.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
badgeSaas: label="AEM Forms" type="Positive" tooltip="S’applique à AEM Forms)."
exl-id: 9ba58659-b14c-4ebc-a6d9-e56a4b6aa48b
source-git-commit: 45b33b8a5afe8ff329f76b65d7e5bd7dea0dcc17
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 3%

---

# Associer l’interface utilisateur dans l’éditeur de communication interactive


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

### &#x200B;2. Création

Conçoit et gère la communication interactive et la configure pour l’interface utilisateur associée (y compris l’activation de la vue associée et d’un workflow facultatif).

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
> Les associés doivent faire partie du groupe **forms-associates**. Pour les auteurs qui effectuent également des envois à partir de l’interface utilisateur associée sur l’instance de création, ajoutez-les également à **workflow-users**.

## Cas d’utilisation dynamiques

L’interface utilisateur d’Associate prend en charge la génération instantanée et personnalisée de documents, essentielle pour les secteurs ayant des besoins de maintenance en temps réel.

| Industrie | Exemples de cas d’utilisation |
|----------|-------------------|
| **Services financiers** | Générer des lettres de confirmation de prêt en temps réel, des résumés de profil de risque, la création de compte. |
| **Assurance** | Produire instantanément des cartes de preuve d&#39;assurance ou des résumés de disposition des réclamations. |
| **Healthcare** | Créez des résumés de plans de traitement des patients avec une copie calculée et des plannings. |
| **Secteur public** | Générer des rapports de vérification de la police, des reçus de services aux citoyens, des lettres d&#39;accusé de réception de grief et des résumés de mise à jour des cas sur place. |
| **Gouvernement** | Créez des résumés de statut de demande, des lettres d&#39;approbation de service et une communication en temps réel pour les inscriptions aux régimes d&#39;assistance sociale. |

## Activation de l’interface utilisateur associée

Les auteurs activent l’interface utilisateur associée et configurent éventuellement un workflow pour les envois dans **Paramètres de communication interactive** :

1. **Activer l&#39;affichage associé** — Dans **Associer les propriétés**, cochez **Activer l&#39;édition d&#39;affichage associé**, puis cliquez sur **Appliquer les modifications** et enregistrez le document.
2. **Configurer le workflow (facultatif)** — Dans **Workflow**, activez **Configurer le workflow pour la mise à jour** Activez, sélectionnez un modèle de workflow et éventuellement définissez un message de réussite et une URL de redirection.
3. **Configurer les champs modifiables** — Activez les champs que les associés peuvent modifier et définir les validations.
4. **Publier et partager** — Publiez l&#39;IC et partagez le lien avec les associés.

Pour obtenir des instructions détaillées sur les captures d’écran et le comportement de l’envoi/du workflow (auteur dans l’instance de création et associé dans l’instance de publication), consultez [&#x200B; Activer et configurer l’interface utilisateur associée pour les communications interactives](/help/forms/interactive-communication/enable-configure-associate-ui.md). Pour créer un workflow qui génère PDF à partir des envois IC, voir [Workflow d’envoi pour l’interface utilisateur associée - Sortie IC Generate PDF](/help/forms/interactive-communication/submission-workflow-associate-ui-ic-pdf.md).

L’**interface utilisateur associée** comble le fossé entre la création de contenu structuré et l’engagement client en temps réel.\
En associant une conception intuitive, une configuration d’arrière-plan robuste et des contrôles de conformité stricts, les entreprises peuvent fournir des communications **rapides, précises et personnalisées** à grande échelle.

## Voir également

- [Activer et configurer l’interface utilisateur associée pour les communications interactives](/help/forms/interactive-communication/enable-configure-associate-ui.md)
- [Configurer les options de liste déroulante pour l’interface utilisateur associée](/help/forms/interactive-communication/associateui/configure-dropdown-options-binding.md)
- [Configuration des variables liées et non liées pour l’interface utilisateur associée](/help/forms/interactive-communication/associateui/configure-bound-unbound-variables-associate-ui.md)
- [Intégrer l’interface utilisateur associée à votre application](/help/forms/interactive-communication/invoke-associate-ui.md)
- [Workflow de soumission pour Associate UI — IC Generate PDF Output](/help/forms/interactive-communication/submission-workflow-associate-ui-ic-pdf.md)
