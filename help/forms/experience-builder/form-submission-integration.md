---
title: Envoi et intégration du formulaire
description: Découvrez comment configurer les envois de formulaires et intégrer les formulaires Forms Experience Builder à des systèmes externes, des API et des workflows métier.
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Developer
exl-id: c772556b-dab6-4fa8-b728-1fe52c6596a4
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '915'
ht-degree: 1%

---

# Envoi et intégration du formulaire

>[!NOTE]
>
> Forms Experience Builder est disponible dans le cadre d’un programme d’accès anticipé. Avant de commencer, vérifiez que vous avez demandé et obtenu l’accès.

Forms Experience Builder offre de puissantes fonctionnalités d’intégration pour connecter vos formulaires à des systèmes externes, des API et des workflows métier. Ce guide explique comment configurer les envois de formulaire et divers scénarios d’intégration.

## Options de configuration de l’envoi

### Soumissions par e-mail

Configurez les formulaires pour envoyer les envois par e-mail :

**Configuration de base des e-mails :**

- Définition des adresses e-mail des destinataires
- Configurer des modèles d’e-mail
- Ajout de destinataires en Cci et Cci
- Configurer des notifications par e-mail

**Fonctionnalités de messagerie avancées :**

- Sélection dynamique de destinataires
- Modèles d’e-mail avec données de formulaire
- Gestion des pièces jointes
- Confirmation de diffusion par e-mail

### Intégration de l’API REST

Connectez les formulaires aux API et services externes :

**Configuration du point d’entrée de l’API :**

- Définition des URL d’API REST
- Configuration des méthodes d’authentification
- Définition des paramètres et des en-têtes de requête
- Gérer les données de réponse

**Mappage des données :**

- Mappage des champs de formulaire aux paramètres de l’API
- Transformer les formats de données
- Gestion des structures JSON imbriquées
- Gérer les réponses d’erreur

### Intégration du stockage dans le cloud

Stockez les envois de formulaire dans les services d’espace de stockage :

**Plateformes prises en charge :**

- Microsoft Azure Blob Storage
- Amazon S3
- Google Cloud Storage
- SharePoint Online

**Options de configuration :**

- Définition des informations d’identification de stockage
- Configuration des structures de dossiers
- Définir les conventions de dénomination des fichiers
- Gestion des autorisations d’accès

### Intégration des workflows

Connecter des formulaires aux workflows de processus métier :

**Microsoft Power Automate :**

- Déclencher des workflows lors de l’envoi du formulaire
- Transmission des données de formulaire aux étapes du workflow
- Gérer les réponses de workflow
- Gestion des processus de validation

**Workflow Adobe :**

- Intégration au workflow AEM
- Configurer des chaînes de validation
- Configuration des étapes de notification
- Gestion du traitement des documents

## Configuration des envois de formulaire

### Étape 1 : accéder à la configuration de l’envoi

1. Ouvrez votre formulaire dans Forms Experience Builder
2. Accéder aux paramètres d’envoi
3. Sélectionnez « Configurer l’envoi du formulaire »
4. Choisissez votre type d’intégration

### Étape 2 : configurer les envois par e-mail

**Configuration de base des e-mails :**

    Configurer l’envoi d’e-mail à hr@company.com avec :
    - Objet : « Demande d’un nouvel employé »
    - Inclure les données de formulaire dans le corps de l’e-mail
    - Envoyer une confirmation au demandeur

**Configuration avancée des e-mails :**

    Configurer le routage dynamique des e-mails :
    - Si le service est égal à « IT », envoyez à it-hr@company.com
    - Si le service est égal à « Ventes », envoyez à sales-hr@company.com
    - Par défaut à hr@company.com

### Étape 3 : configurer l&#39;intégration de l&#39;API

**Configuration de l’API REST :**

    Envoyer les données de formulaire au point d’entrée REST :
    - URL : https://api.company.com/forms/submit
    - Méthode : POST
    - Authentification : jeton porteur
    - Type de contenu : application/json

**Exemple de mapping de données :**

    Mappez les champs de formulaire avec API :
    - firstName -> user.first_name
    -> user.last_name
    - email -> user.email_address
    - department -> user.department_id

### Étape 4 : configurer l’espace de stockage dans le cloud

**Configuration du stockage Blob Azure :**

    Stocker les envois de formulaire dans Azure:
    - Conteneur : form-submission
    - Dossier : /{year}/{month}/{day}/
    - Format de fichier : JSON avec pièces jointes
    - Niveau d’accès : privé

## Exemples d’intégration

### Formulaire de commentaires client

**Configuration de l’envoi :**

- Notification électronique à l’équipe d’assistance
- Stockage des données dans le système CRM via l’API
- Créer automatiquement un ticket d’assistance
- Envoyer un e-mail de confirmation au client

**Implémentation :**
Envoyez le formulaire de commentaires client à :
1. <support@company.com> d’e-mail avec détails de formulaire
2. Publier dans l’API CRM pour créer l’enregistrement du client
3. Déclencher le workflow de création de ticket d’assistance
4. Envoyer un e-mail de remerciement au client

### Formulaire d’intégration des employés

**Configuration de l’envoi :**

- Envoyer un e-mail à l’équipe RH avec les informations sur la nouvelle embauche
- Stockage de documents dans SharePoint
- Déclencher le workflow d’intégration
- Création de comptes utilisateur dans divers systèmes

**Implémentation :**
Traiter l’intégration des employés :
1. <hr@company.com> par e-mail avec les détails de l’employé
2. Charger des documents dans le dossier des employés de SharePoint
3. Démarrer le workflow d’intégration dans Power Automate
4. Créer des comptes dans le système des ressources humaines, le courrier électronique et d’autres outils

### Formulaire de génération de leads

**Configuration de l’envoi :**

- Stockage des données de prospect dans une plateforme d’automatisation du marketing
- Envoyer une notification à l&#39;équipe commerciale
- Ajout d’un prospect au système CRM
- Déclencher la séquence d’e-mails de relance

**Implémentation :**
Génération de piste de processus :
1. PUBLIER les données de prospect dans l’API Marketo
2. Créer un enregistrement de prospect dans Salesforce
3. Envoyer un courrier électronique à l’équipe de vente avec les détails du prospect
4. Démarrer la séquence de maturation automatisée des e-mails

## Scénarios d’intégration avancés

### Traitement de formulaire à plusieurs étapes

**Intégration de workflows complexes :**

- Valider les données de formulaire par rapport à des systèmes externes
- Traiter les paiements par le biais de passerelles de paiement
- Générer des documents et des contrats
- Envoi de notifications à plusieurs parties prenantes

### Validation des données en temps réel

**Validation basée sur l’API :**

- Validation des adresses e-mail dans le répertoire de l’entreprise
- Vérifier la disponibilité des produits dans le système d&#39;inventaire
- Vérification des informations client dans CRM
- Valider les informations de paiement

### Routage de l’envoi conditionnel

**Routage dynamique basé sur les données de formulaire :**

- Acheminer vers différents services en fonction du type de demande
- Envoyer à différents systèmes en fonction du niveau du client
- Traitement différent en fonction du statut d’achèvement du formulaire
- Gérer différentes règles métier par région

## Sécurité et conformité

### Protection des données

**Chiffrement et sécurité :**

- Chiffrement des données sensibles en transit
- Jetons et informations d’identification d’API sécurisés
- Implémenter des contrôles d’accès appropriés
- Respect des règles de conservation des données

### Exigences de conformité

**RGPD et confidentialité :**

- Implémentation de la gestion du consentement
- Fournir des fonctionnalités d’exportation de données
- Activer les demandes de suppression de données
- Tenir à jour les journaux d&#39;audit

**Normes du secteur :**

- Conformité à la loi HIPAA pour les formulaires de soins de santé
- DSS PCI pour le traitement des paiements
- Conformité SOX pour les formulaires financiers
- Réglementations spécifiques au secteur

## Tests et validation

### Test de l’envoi

**Scénarios de test :**

- Vérifier la diffusion et le formatage des e-mails
- Tester la connectivité de l’API et le mappage des données
- Validation des chargements de l’espace de stockage
- Vérifier la fonctionnalité de déclencheur de workflow

**Gestion des erreurs :**

- Test des scénarios d’échec du réseau
- Valider l’affichage du message d’erreur
- Vérifier les mécanismes de reprise
- Vérifier les options de secours

### Optimisation des performances

**Stratégies d’optimisation :**

- Implémentation du traitement asynchrone
- Utiliser des opérations par lots pour les données en bloc
- Optimisation de la fréquence des appels API
- Mettre en cache les données fréquemment consultées

## Résolution des problèmes d’intégration

### Problèmes courants

**Problèmes de diffusion des e-mails :**

- Vérifier la configuration du serveur SMTP
- Vérification des adresses e-mail des destinataires
- Vérifier les paramètres du filtre anti-spam
- Tester le formatage du modèle d’e-mail

**Problèmes d’intégration des API :**

- Vérification des URL de point d’entrée de l’API
- Vérifier les informations d’authentification
- Valider le format et les en-têtes de la requête
- Vérifier la gestion des réponses de l’API

**Problèmes d’intégration du stockage :**

- Confirmer les informations d’identification de stockage
- Vérification des autorisations de dossier
- Vérification des limites de chargement de fichier
- Tester la connectivité réseau

### Obtention d’aide

Pour les problèmes d’intégration :

- Consultez la [FAQ sur Forms Experience Builder](forms-experience-builder-frequently-asked-questions.md)
- Consultez le [&#x200B; Guide de prise en main &#x200B;](forms-experience-builder-getting-started.md)
- Contactez votre administrateur système pour obtenir une assistance technique
- Consultez la documentation de l’API pour les services externes.

## Articles connexes

- [Présentation de Forms Experience Builder](product-overview.md)
- [Prise en main de Forms Experience Builder](forms-experience-builder-getting-started.md)
- [Déploiement et configuration de Forms Experience Builder](deploy-forms-experience-builder.md)
- [Import et conversion intelligents](intelligent-import-conversion.md)
- [Questions fréquentes](forms-experience-builder-frequently-asked-questions.md)
