---
title: Ajouter Google reCAPTCHA aux formulaires dans l’éditeur universel
description: Guide d’implémentation de la protection reCAPTCHA de Google dans les formulaires Edge Delivery Services pour empêcher le spam et les attaques automatisées
feature: Edge Delivery Services
keywords: reCAPTCHA dans les formulaires, Utilisation de reCAPTCHA dans l’éditeur universel, Ajouter reCAPTCHA dans les formulaires, sécurité des formulaires, protection contre les spams
role: Developer, Admin
level: Intermediate
exl-id: 1f28bd13-133f-487e-8b01-334be7c08a3f
source-git-commit: fd3c53cf5a6d1c097a5ea114a831ff626ae7ad7e
workflow-type: tm+mt
source-wordcount: '1281'
ht-degree: 90%

---


# Ajouter Google reCAPTCHA aux formulaires dans l’éditeur universel

Google reCAPTCHA permet de protéger les formulaires en distinguant les utilisateurs et les utilisatrices humains des robots automatisés. Ce guide explique comment implémenter les versions reCAPTCHA Enterprise et Standard dans l’éditeur universel.

**Objectifs :**

- Sélectionner la solution reCAPTCHA appropriée
- Configurer reCAPTCHA Enterprise ou Standard
- Ajouter reCAPTCHA à vos formulaires
- Valider et tester l’implémentation
- Surveiller et optimiser les performances

## Prérequis

Avant de commencer, vérifiez que vous disposez des éléments suivants :

### Conditions d’accès

- Accès à la création AEM as a Cloud Service
- Accès à l’éditeur universel avec des autorisations d’édition de formulaire

### Exigences techniques

- Compte Google actif
- Pour Enterprise : projet Google Cloud Platform avec facturation activée
- Pour Standard : compte reCAPTCHA Google
- Propriété de domaine vérifiée pour vos formulaires

### Prérequis en matière de connaissances

- Compréhension de base d’AEM Forms et de l’éditeur universel
- Familiarité avec les configurations de service cloud
- Compréhension des concepts de sécurité des formulaires

## Pourquoi utiliser reCAPTCHA dans vos formulaires ?

| ![Sécurité](/help/edge/docs/forms/universal-editor/assets/security.svg) | ![Protection contre les robots](/help/edge/docs/forms/universal-editor/assets/bot-protection.svg) | ![Expérience client](/help/edge/docs/forms/universal-editor/assets/user-experience.svg) |
|:-------------:|:-------------:|:-------------:|
| **Sécurité renforcée** | **Protection contre les robots et les spams** | **Expérience client transparente** |
| Protéger vos formulaires contre les activités frauduleuses et les attaques malveillantes | Empêcher les robots automatisés d’envoyer des formulaires | Le reCAPTCHA invisible ne perturbe pas les utilisateurs et utilisatrices légitimes. |

**Concept clé :** reCAPTCHA utilise le machine learning pour analyser le comportement des utilisateurs et des utilisatrices et attribue un score (0,0 à 1,0) indiquant la probabilité d’interaction humaine. Les scores plus élevés indiquent des utilisateurs et des utilisatrices humains; les scores plus faibles suggèrent des robots.

**Exemple :** un formulaire de calcul des taxes gérant des données sensibles nécessite une protection contre les attaques automatisées. reCAPTCHA vérifie que les envois proviennent de vrais utilisateurs ou utilisatrices, et non de robots.

## Choisir votre solution reCAPTCHA

Les formulaires Edge Delivery Services prennent en charge deux options Google reCAPTCHA : Utilisez les critères suivants pour sélectionner une solution adaptée :

### Guide de décision rapide

**Utilisez reCAPTCHA Enterprise si vous disposez des éléments suivants :**

- Formulaires à trafic élevé (>10 000 requêtes/mois)
- Exigences de conformité strictes (RGPD, SOX, HIPAA)
- Besoin d’analyses et de rapports avancés
- Budget pour les fonctionnalités de sécurité premium
- Déploiements multidomaines complexes

**Utilisez reCAPTCHA Standard si vous disposez des éléments suivants :**

- Trafic faible à modéré (&lt;10 000 requêtes/mois)
- Besoins de base en matière de sécurité
- Budget limité (niveau gratuit)
- Configuration simple sur un seul domaine
- Permière utilisation de reCAPTCHA

### Comparaison détaillée

| **Fonctionnalité** | **reCAPTCHA Enterprise** | **reCAPTCHA Standard** |
|-------------|--------------------------|------------------------|
| **Coût** | Payé (tarification basée sur l’utilisation) | Libre |
| **Limite du nombre de requêtes** | Illimité | 1M requêtes/mois |
| **Analytique avancée :** | Rapports détaillés | Statistiques de base uniquement |
| **Règles personnalisées** | Règles spécifiques au compte | Règles globales uniquement |
| **Prise en charge multidomaine** | Gestion avancée | Assistance de base |
| **SLA** | Garantie de disponibilité de 99,9 % | Meilleur effort |
| **Assistance** | Support Entreprise | Support Communauté |
| **Conformité :** | Niveau Entreprise | Conformité aux normes |

**Les deux solutions offrent les avantages suivants :**

- Détection basée sur un score (échelle de 0,0 à 1,0)
- Fonctionnement invisible (aucune interaction des  utilisateurs et des utilisatrices requise)
- Détection des robots basée sur le machine learning
- Évaluation des risques en temps réel

## Configurer reCAPTCHA Enterprise


+++ Étape 1 : préparation de l’environnement cloud Google

**Prérequis :**

1. Projet Google Cloud avec facturation activée
2. Identifiant du projet (depuis le tableau de bord GCP)
3. Vérification de domaine pour vos formulaires
4. Accès des administrateurs et administratrices à GCP et AEM

**Configuration :**

1. Créer ou sélectionner un projet Google Cloud
   - Accédez à la [console Google Cloud](https://console.cloud.google.com/)
   - Créez un projet ou sélectionnez un projet existant
   - Notez votre ID de projet

2. Activez l’API reCAPTCHA Enterprise
   - Accédez à API et services > Bibliothèque
   - Recherchez « reCAPTCHA Enterprise API »
   - Cliquez sur Activer

3. Créer des informations d’identification API
   - Accédez à API et services > Informations d’identification
   - Cliquez sur Créer des informations d’identification > Clé API
   - Copiez et stockez votre clé API

4. Créez une clé de site
   - Accédez à Sécurité > reCAPTCHA Enterprise
   - Cliquez sur Créer une clé
   - Choisissez le type de clé basé sur les scores
   - Ajoutez votre ou vos domaine(s)
   - Définissez le score seuil (recommandé : 0,5)

**Point de contrôle de validation :** vérifiez que vous disposez des éléments suivants :

- ID du projet
- Clé API
- Clé de site
- Domaine vérifié dans Google Cloud

+++

+++ Étape 2 : configurer le conteneur de configuration cloud AEM

![Configuration cloud étape par étape](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)
*Figure : activation des configurations cloud pour votre conteneur de formulaires*

**Configuration :**

1. Accéder au navigateur de configuration
   - Se connecter à votre instance de création AEM
   - Accédez à Outils > Général > Navigateur de configuration

2. Activez les configurations cloud
   - Localisez le conteneur de configuration de votre formulaire
   - Sélectionnez Propriétés
   - Vérifiez les configurations cloud
   - Cliquez sur Enregistrer et fermer

3. Vérifier la configuration
   - Confirmez que les « Configurations cloud » s’affichent dans les propriétés du conteneur.

**Point de contrôle de validation :**

- Configurations cloud activées pour votre conteneur
- Le conteneur apparaît dans l’explorateur de configurations
- Les propriétés affichent « Configurations cloud » comme étant activées

+++

+++ Étape 3 : configurer le service reCAPTCHA Enterprise dans AEM

![écran de configuration reCAPTCHA Enterprise](/help/edge/docs/forms/universal-editor/assets/recaptcha-enterprise.png)
*Figure : interface de configuration reCAPTCHA Enterprise dans AEM*

**Configuration :**

1. Accédez à la configuration reCAPTCHA
   - Accéder à Outils > Services cloud > reCAPTCHA
   - Sélectionner le conteneur de configuration de votre formulaire
   - Cliquer sur Créer

2. Configurer les paramètres Enterprise
   - Titre : nom explicite (par exemple, « Production reCAPTCHA »)
   - Nom : nom du système (généré automatiquement ou personnalisé)
   - Version : sélectionnez ReCAPTCHA Enterprise
   - ID de projet : saisissez votre ID de projet Google Cloud
   - Clé du site : saisissez la clé du site à partir de Google Cloud
   - Clé API : saisissez votre clé API Google Cloud
   - Type de clé : sélectionnez Clé de site basée sur les scores

3. Définissez un seuil de sécurité
   - Score du seuil : défini entre 0,0 et 1,0
   - Valeurs recommandées :
      - 0,7 - 0,9 : haute sécurité (peut bloquer certains utilisateurs et utilisatrices légitimes)
      - 0,5 - 0,7 : sécurité équilibrée (recommandé)
      - 0,1 - 0,5 : sécurité réduite (permet plus d’utilisateurs et d’utilisatrices)

4. Enregistrer et publier
   - Cliquez sur Créer pour enregistrer la configuration.
   - Cliquez sur Publier pour la rendre disponible.

**Point de contrôle de validation :**

- Configuration enregistrée avec succès
- Tous les champs obligatoires remplis
- Configuration publiée et visible
- Aucun message d’erreur

+++

## Configurer reCAPTCHA Standard

+++Étape 1 : obtenir des clés API reCAPTCHA (voir les détails)

>[!IMPORTANT]
>
> Les formulaires Edge Delivery Services ne prennent en charge que les services reCAPTCHA v2 basés sur les scores. N’utilisez pas la version case à cocher.

**Génération de clés :**

1. Accèdez à la console reCAPTCHA de Google.

   - Accédez à la [console d’administration Google reCAPTCHA](https://www.google.com/recaptcha/admin).
   - Connectez-vous avec votre compte Google.

2. Créez un nouveau site.

   - Cliquez sur le signe « + » pour ajouter un nouveau site
   - Libellé : saisissez un nom explicite
   - Type reCAPTCHA : sélectionnez reCAPTCHA v2 > « Je ne suis pas un robot » Invisible
   - Domaines : ajoutez vos domaines de formulaire
   - Acceptez les conditions et cliquez sur Envoyer

3. Collectez Vos Clés

   - Clé du site : copiez la clé du site (clé publique).
   - Clé secrète : copiez la clé secrète (clé privée)

**Point de contrôle de validation :**

- Site créé dans la console reCAPTCHA

- Clé de site obtenue

- Clé secrète obtenue

- Domaine(s) ajouté(s) et vérifié(s)

+++

+++Étape 2 : Configurer le conteneur de configuration cloud AEM (voir les détails)

Suivez le même processus que dans la configuration Enterprise :

1. Activez les configurations cloud dans le navigateur de configuration

2. Vérifiez la configuration du conteneur

3. Confirmez que les paramètres sont enregistrés

+++

+++Étape 3 : Configurer le service standard reCAPTCHA dans AEM (voir les détails)

![Écran de configuration reCAPTCHA Standard](/help/edge/docs/forms/universal-editor/assets/recaptcha.png)
*Figure : interface de configuration de reCAPTCHA Standard dans AEM*

**Configuration :**

1. Accédez à la configuration reCAPTCHA

   - Accéder à Outils > Services cloud > reCAPTCHA
   - Sélectionner le conteneur de configuration de votre formulaire
   - Cliquer sur Créer

2. Configurez les paramètres standard.

   - Titre : nom explicite (par exemple, « reCAPTCHA standard »).
   - Nom : nom du système (généré automatiquement ou personnalisé)
   - Version : sélectionnez ReCAPTCHA v2.
   - Clé de site : saisissez votre clé de site reCAPTCHA Google.
   - Clé secrète : saisissez votre clé secrète reCAPTCHA Google.

3. Enregistrer et publier

   - Cliquez sur Créer pour enregistrer la configuration.
   - Cliquez sur Publier pour la rendre disponible.

**Point de contrôle de validation :**

- Configuration créée sans erreurs

- Les deux clés sont saisies correctement

- Configuration correctement publiée

- La configuration apparaît dans la liste

+++

## Ajouter reCAPTCHA à votre formulaire

Après avoir configuré le service reCAPTCHA, ajoutez une protection à votre formulaire comme suit :

![Ajout du composant reCAPTCHA à un formulaire](/help/edge/docs/forms/universal-editor/assets/add-recaptcha-component.png)
*Figure : ajout du composant Captcha invisible à votre formulaire*

+++&#x200B;1. Ouvrir un formulaire dans l’éditeur universel
Accédez à votre formulaire dans AEM Sites et cliquez sur Modifier pour l’ouvrir dans l’éditeur universel. Attendez que l’éditeur se charge.

- Accédez à votre formulaire dans AEM Sites.
- Cliquez sur Modifier pour ouvrir dans l’éditeur universel.
- Attendez que l’éditeur se charge.
+++

+++&#x200B;2. Localisez la structure du formulaire
Dans l’arborescence de contenu (panneau de gauche), recherchez la section de votre formulaire adaptatif et développez la structure du formulaire pour afficher les points d’insertion.

- Dans l’arborescence de contenu (panneau de gauche), recherchez la section Formulaire adaptatif.
- Développez la structure du formulaire pour afficher les points d’insertion.
+++

+++&#x200B;3. Ajouter le composant reCAPTCHA
Ajoutez le composant Captcha (invisible) à votre formulaire.

- Cliquez sur l’icône Ajouter (+) dans la section de votre formulaire.
- Dans la liste des composants, sélectionnez Captcha (invisible).
- Vous pouvez également faire glisser et déposer le composant depuis le panneau des composants.
+++

+++&#x200B;4. Configurer Le Composant (Facultatif)
Sélectionnez le composant captcha nouvellement ajouté et vérifiez qu’il utilise votre configuration reCAPTCHA.

- Sélectionnez le composant Captcha nouvellement ajouté.
- Dans le panneau Propriétés, vérifiez qu’il utilise votre configuration reCAPTCHA.
- Aucune configuration supplémentaire n’est nécessaire pour l’installation de base.
+++

+++&#x200B;5. Publiez Vos Modifications
Publiez vos modifications et vérifiez qu’il n’y a aucune erreur.

- Cliquez sur Publier dans l’éditeur universel.
- Attendez la confirmation.
- Vérifiez qu’aucune erreur ne s’affiche.
+++

### Vérifiez l’implémentation.

Votre formulaire protégé est désormais disponible à l’adresse :

```
https://<branch>--<repo>--<owner>.aem.live/content/forms/af/
<form-name>
```

**Exemple d’URL :**

```
https://main--my-forms--company.aem.live/content/forms/af/
contact-us-form
```
