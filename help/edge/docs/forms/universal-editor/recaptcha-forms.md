---
title: Ajout de Google reCAPTCHA à Forms dans l’éditeur universel
description: Guide d’implémentation de la protection reCAPTCHA de Google dans les formulaires Edge Delivery Services pour prévenir le spam et les attaques automatisées
feature: Edge Delivery Services
keywords: reCAPTCHA dans les formulaires, Utilisation de reCAPTCHA dans l’éditeur universel, Ajout de reCAPTCHA dans les formulaires, sécurité des formulaires, protection contre les spams
role: Developer, Admin
level: Intermediate
exl-id: 1f28bd13-133f-487e-8b01-334be7c08a3f
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '1290'
ht-degree: 5%

---


# Ajout de Google reCAPTCHA à Forms dans l’éditeur universel

Google reCAPTCHA permet de protéger les formulaires en faisant la distinction entre les utilisateurs humains et les robots automatisés. Ce guide explique comment implémenter les versions reCAPTCHA Enterprise et Standard dans l’éditeur universel.

**Objectifs:**

- Sélectionner la solution reCAPTCHA appropriée
- Configuration de reCAPTCHA Enterprise ou Standard
- Ajouter reCAPTCHA à vos formulaires
- Validation et test de l’implémentation
- Surveillance et optimisation des performances

## Prérequis

Avant de commencer, vérifiez que vous disposez des éléments suivants :

### Conditions d’accès

- Accès à la création dans AEM as a Cloud Service
- Accès à l’éditeur universel avec des autorisations d’édition de formulaire
- Inscription au programme d’accès anticipé pour les fonctionnalités reCAPTCHA

### Exigences techniques

- Compte Google actif
- Pour les entreprises : projet Google Cloud Platform avec facturation activée
- Pour Standard : compte reCAPTCHA Google
- Propriété de domaine vérifiée pour vos formulaires

### Exigences en matière de connaissances

- Compréhension de base d’AEM Forms et de l’éditeur universel
- Familiarité avec les configurations de service cloud
- Compréhension des concepts de sécurité des formulaires

## Pourquoi utiliser reCAPTCHA dans votre Forms ?

| ![Sécurité](/help/edge/docs/forms/universal-editor/assets/security.svg) | ![Protection contre les robots](/help/edge/docs/forms/universal-editor/assets/bot-protection.svg) | ![Expérience client](/help/edge/docs/forms/universal-editor/assets/user-experience.svg) |
|:-------------:|:-------------:|:-------------:|
| **Sécurité renforcée** | **Protection contre les robots et les spams** | **Expérience client transparente** |
| Protéger les formulaires contre les activités et les attaques frauduleuses | Empêcher les robots automatisés d’envoyer des formulaires | Le reCAPTCHA invisible ne perturbe pas les utilisateurs légitimes |

**Concept clé :** reCAPTCHA utilise le machine learning pour analyser le comportement des utilisateurs et attribue un score (0,0 à 1,0) indiquant la probabilité d’interaction humaine. Des scores plus élevés indiquent des utilisateurs humains ; des scores plus faibles suggèrent des robots.

**Exemple :** un formulaire de calcul des taxes gérant des données sensibles nécessite une protection contre les attaques automatisées. reCAPTCHA vérifie que les envois proviennent de vrais utilisateurs, et non de robots.

## Choisir votre solution reCAPTCHA

Edge Delivery Services Forms prend en charge deux options Google reCAPTCHA. Utilisez les critères suivants pour sélectionner la solution appropriée :

### Guide de décision rapide

**Utilisez reCAPTCHA Enterprise si vous disposez des éléments suivants**

- Formulaires à trafic élevé (>10 000 demandes/mois)
- Exigences de conformité strictes (RGPD, SOX, HIPAA)
- Besoin d’analyses et de rapports avancés
- Budget pour les fonctionnalités de sécurité premium
- Déploiements multidomaines complexes

**Utilisez reCAPTCHA Standard si vous avez :**

- Trafic faible à modéré (&lt;10 000 requêtes/mois)
- Besoins de base en matière de sécurité
- Budget limité (niveau gratuit)
- Configuration simple sur un seul domaine
- Découvrez reCAPTCHA

### Comparaison détaillée

| **Fonctionnalité** | **reCAPTCHA Enterprise** | **reCAPTCHA Standard** |
|-------------|--------------------------|------------------------|
| **Coût** | Payé (tarification basée sur l’utilisation) | Libre |
| **Limite de demande** | Illimité | 1M requêtes/mois |
| **Analyses avancées** | Rapports détaillés | Statistiques de base uniquement |
| **Règles personnalisées** | Règles spécifiques au compte | Règles globales uniquement |
| **Prise en charge multidomaine** | Gestion avancée | Prise en charge de base |
| **SLA** | Garantie de disponibilité de 99,9 % | Meilleur effort |
| **Assistance** | Assistance Entreprise | soutien communautaire |
| **Conformité** | De niveau entreprise | Conformité aux normes |

**Les deux solutions offrent les avantages suivants**

- Détection basée sur les scores (échelle de 0,0 à 1,0)
- Opération invisible (aucune interaction utilisateur requise)
- Détection de robots optimisée par machine learning
- Évaluation des risques en temps réel

## Configurer reCAPTCHA Enterprise


+++ Étape 1 : préparation de l’environnement cloud Google

**Conditions requises:**

1. Projet Google Cloud avec facturation activée
2. Identifiant du projet (depuis le tableau de bord GCP)
3. Vérification de domaine pour vos formulaires
4. Accès des administrateurs à GCP et AEM

**Configuration:**

1. Création ou sélection d’un projet Google Cloud
   - Accédez à la [console cloud Google](https://console.cloud.google.com/)
   - Créer un projet ou en sélectionner un existant
   - Notez votre ID de projet

2. Activer l’API reCAPTCHA Enterprise
   - Accédez à API et services > Bibliothèque .
   - Recherchez « reCAPTCHA Enterprise API ».
   - Cliquez sur Activer

3. Créer des informations d’identification d’API
   - Accédez à API et services > Informations d’identification .
   - Cliquez sur Créer des identifiants > Clé API .
   - Copier et stocker votre clé API

4. Créer une clé de site
   - Accédez à Sécurité > reCAPTCHA Enterprise
   - Cliquez sur Créer une clé
   - Choisir le type de clé basé sur les scores
   - Ajouter votre ou vos domaine(s)
   - Définir le score de seuil (recommandé : 0,5)

**Point de contrôle de validation :** vérifiez que vous disposez des éléments suivants :

- ID du projet
- Clé API
- Clé de site
- Domaine vérifié dans Google Cloud

+++

+++ Étape 2 : Configurer le conteneur de configuration cloud d’AEM

![Configuration du cloud étape par étape](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)
*Figure : activation des configurations cloud pour votre conteneur de formulaires*

**Configuration:**

1. Accéder au navigateur de configuration
   - Connectez-vous à votre instance de création AEM.
   - Accédez à Outils > Général > Explorateur de configurations

2. Activer les configurations cloud
   - Recherchez le conteneur de configuration de votre formulaire
   - Sélectionner les propriétés
   - Vérifier les configurations cloud
   - Cliquez sur Enregistrer et fermer .

3. Vérifier la configuration
   - Confirmez que les « Configurations cloud » s’affichent dans les propriétés du conteneur.

**Point de contrôle de validation :**

- Configurations cloud activées pour votre conteneur
- Le conteneur apparaît dans l’explorateur de configurations
- Les propriétés affichent « Configurations cloud » comme étant activées

+++

+++ Étape 3 : configuration de reCAPTCHA Enterprise Service dans AEM

![écran de configuration reCAPTCHA Enterprise](/help/edge/docs/forms/universal-editor/assets/recaptcha-enterprise.png)
*Image : interface de configuration reCAPTCHA Enterprise dans AEM*

**Configuration:**

1. Accéder à la configuration reCAPTCHA
   - Accédez à Outils > Services cloud > reCAPTCHA .
   - Sélectionnez le conteneur de configuration de votre formulaire
   - Cliquez sur Créer .

2. Configurer les paramètres d’entreprise
   - Titre : nom descriptif (par exemple, « Production reCAPTCHA »)
   - Nom : nom du système (généré automatiquement ou personnalisé)
   - Version : sélectionnez ReCAPTCHA Enterprise
   - ID de projet : saisissez votre ID de projet Google Cloud
   - Clé du site : saisissez la clé du site à partir de Google Cloud
   - Clé API : saisissez votre clé API Google Cloud
   - Type de clé : sélectionnez la clé de site basée sur les scores .

3. Définir un seuil de sécurité
   - Score du seuil : défini entre 0.0 et 1.0
   - Valeurs recommandées :
      - 0.7-0.9 : Haute sécurité (peut bloquer certains utilisateurs légitimes)
      - 0.5-0.7 : Sécurité équilibrée (recommandé)
      - 0.1-0.5 : sécurité réduite (permet plus d’utilisateurs)

4. Enregistrer et publier
   - Cliquez sur Créer pour enregistrer la configuration
   - Cliquez sur Publier pour la rendre disponible

**Point de contrôle de validation :**

- Configuration enregistrée avec succès
- Tous les champs obligatoires remplis
- Configuration publiée et visible
- Aucun message d’erreur

+++

## Configurer reCAPTCHA Standard

+++Étape 1 : obtenir des clés API reCAPTCHA (voir les détails)

>[!IMPORTANT]
>
> Edge Delivery Services Forms ne prend en charge que reCAPTCHA v2 (basé sur les scores). N’utilisez pas la version case à cocher.

**Génération de clé :**

1. Accès à la console reCAPTCHA de Google

   - Accédez à [Google reCAPTCHA Admin Console](https://www.google.com/recaptcha/admin)
   - Connexion avec votre compte Google

2. Créer un site

   - Cliquez sur + pour ajouter un nouveau site
   - Libellé : saisissez un nom explicite
   - reCAPTCHA Type : sélectionnez reCAPTCHA v2 > « Je ne suis pas un robot » Invisible
   - Domaines : ajoutez vos domaines de formulaire
   - Accepter les conditions et cliquer sur Envoyer

3. Collectez Vos Clés

   - Clé du site : copiez la clé du site (clé publique).
   - Clé secrète : copiez la clé secrète (clé privée)

**Point de contrôle de validation :**

- Site créé dans la console reCAPTCHA

- Clé de site obtenue

- Clé secrète obtenue

- Domaine(s) ajouté(s) et vérifié(s)

+++

+++Étape 2 : Configurer le conteneur de configuration cloud AEM (voir les détails)

Suivez le même processus que dans la configuration Enterprise :

1. Activation des configurations cloud dans l’explorateur de configurations

2. Vérifier la configuration du conteneur

3. Confirmer que les paramètres sont enregistrés

+++

+++Étape 3 : Configurer le service standard reCAPTCHA dans AEM (voir les détails)

Écran de configuration ![reCAPTCHA Standard](/help/edge/docs/forms/universal-editor/assets/recaptcha.png)
*Figure : interface de configuration de reCAPTCHA Standard dans AEM*

**Configuration:**

1. Accéder à la configuration reCAPTCHA

   - Accédez à Outils > Services cloud > reCAPTCHA .
   - Sélectionnez le conteneur de configuration de votre formulaire
   - Cliquez sur Créer .

2. Configurer les paramètres standard

   - Titre : nom descriptif (par exemple, « Standard reCAPTCHA »)
   - Nom : nom du système (généré automatiquement ou personnalisé)
   - Version : sélectionnez ReCAPTCHA v2
   - Clé de site : saisissez la clé de site reCAPTCHA de Google
   - Clé secrète : saisissez votre clé secrète Google reCAPTCHA

3. Enregistrer et publier

   - Cliquez sur Créer pour enregistrer la configuration
   - Cliquez sur Publier pour la rendre disponible

**Point de contrôle de validation :**

- Configuration créée sans erreur

- Les deux clés saisies correctement

- Configuration publiée

- La configuration apparaît dans la liste

+++

## Ajouter reCAPTCHA à votre formulaire

Après avoir configuré le service reCAPTCHA, ajoutez une protection à votre formulaire comme suit :

![Ajout du composant reCAPTCHA à un formulaire](/help/edge/docs/forms/universal-editor/assets/add-recaptcha-component.png)
*Image : ajout du composant Captcha invisible à votre formulaire*

+++1. Ouvrir un formulaire dans l’éditeur universel
Accédez à votre formulaire dans AEM Sites et cliquez sur Modifier pour l’ouvrir dans l’éditeur universel. Attendez que l’éditeur se charge.

- Accédez à votre formulaire dans AEM Sites
- Cliquez sur Modifier pour ouvrir dans l’éditeur universel.
- Attendez que l’éditeur se charge
+++

+++2. Localisation de la structure du formulaire
Dans l’arborescence de contenu (panneau de gauche), recherchez la section de votre formulaire adaptatif et développez la structure du formulaire pour afficher les points d’insertion.

- Dans l’arborescence de contenu (panneau de gauche), recherchez la section Formulaire adaptatif
- Développez la structure du formulaire pour afficher les points d’insertion
+++

+++3. Ajout du composant reCAPTCHA
Ajoutez le composant Captcha (invisible) à votre formulaire.

- Cliquez sur l’icône Ajouter (+) dans la section de votre formulaire
- Dans la liste des composants, sélectionnez Captcha (invisible)
- Vous pouvez également faire glisser et déposer le composant depuis le panneau composants
+++

+++4. Configurer Le Composant (Facultatif)
Sélectionnez le composant captcha nouvellement ajouté et vérifiez qu’il utilise votre configuration reCAPTCHA.

- Sélectionnez le composant captcha nouvellement ajouté
- Dans le panneau Propriétés , vérifiez qu’il utilise votre configuration reCAPTCHA
- Aucune configuration supplémentaire n’est nécessaire pour l’installation de base
+++

+++5. Publier Vos Modifications
Publiez vos modifications et vérifiez qu’il n’y a aucune erreur.

- Cliquez sur Publier dans l’éditeur universel
- Attendre la confirmation
- Vérifiez qu’aucune erreur ne s’affiche.
+++

### Vérifier la mise en œuvre

Votre formulaire protégé est désormais disponible à l’adresse :

```
https://<branch>--<repo>--<owner>.aem.live/content/forms/af/
<form-name>
```

**Exemple d’URL :**

```
https://main--my-forms--company.aem.live/content/forms/af/
contact-form
```
