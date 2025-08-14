---
title: Comment configurer une page de redirection ou un message de remerciement
description: Découvrez comment les utilisateurs et utilisatrices peuvent voir affiché un message de remerciement ou être redirigés vers une page web que les personnes chargées de la création de formulaires peuvent configurer lors de la phase de création.
feature: Adaptive Forms, Edge Delivery Services
role: User
level: Intermediate
source-git-commit: 07160248d5b5817d155a118475878ce04a687a32
workflow-type: tm+mt
source-wordcount: '1133'
ht-degree: 3%

---


# Configuration des messages de remerciement et des URL de redirection

Les expériences post-envoi ont un impact significatif sur la satisfaction des utilisateurs et les taux de remplissage des formulaires. L’éditeur universel d’Adobe fournit des options complètes pour configurer ce que les utilisateurs voient après l’envoi des formulaires, que ce soit par le biais de messages de remerciement personnalisés ou de redirections stratégiques vers des pages spécifiques.

Cet article fournit des conseils détaillés sur l’implémentation des messages de remerciement et des URL de redirection, y compris des considérations techniques, des bonnes pratiques et des directives d’expérience utilisateur pour maximiser l’efficacité de vos envois de formulaire.

## Prérequis

Avant de configurer des expériences après envoi, vérifiez les points suivants :

**Configuration technique :**

- Accès à l’éditeur universel avec les autorisations appropriées
- Formulaire adaptatif existant créé dans l’éditeur universel
- Compréhension des exigences de votre organisation en matière d’URL de redirection

**Considérations relatives à la planification :**

- **Stratégie des messages** : définissez le ton, la longueur et les informations spécifiques à inclure dans les messages de remerciement.
- **Stratégie de redirection** : identifiez les pages cibles et assurez-vous qu’elles sont optimisées pour les expériences d’achèvement post-formulaire
- **Intégration d’Analytics** : planifiez le suivi des interactions utilisateur avec les messages de remerciement ou les destinations de redirection

## Configurer Les Messages De Remerciement

Les messages de remerciement confirment immédiatement la réussite de l’envoi du formulaire et peuvent inclure du contenu personnalisé, les étapes suivantes ou des informations importantes relatives à l’envoi du formulaire par l’utilisateur.

### Quand utiliser les messages de remerciement

Les messages de remerciement fonctionnent mieux lorsque :

- **Simple acquittement** : les utilisateurs ont besoin d’une confirmation sans exigences de navigation supplémentaires
- **Contenu didactique** : vous devez indiquer les étapes suivantes spécifiques ou des informations importantes
- **Cohérence de la marque** : le message peut être conçu pour s’aligner sur le style de communication de votre entreprise
- **Expérience d’une seule page** : les utilisateurs doivent rester sur la page active pour assurer la continuité du workflow

### Étapes de mise en œuvre

**1. Accédez aux propriétés du formulaire**

Ouvrez votre formulaire adaptatif dans l’éditeur universel et cliquez sur l’icône **Modifier les propriétés du formulaire** dans la barre d’outils. Cela ouvre la boîte de dialogue complète des propriétés du formulaire.

**2. Accédez à la configuration de remerciement**

Dans la boîte de dialogue Propriétés du formulaire , sélectionnez l’onglet **Merci** pour accéder aux options de configuration après l’envoi.

**3. Configurez l’affichage des messages**

Sélectionnez **Afficher le message** dans les options disponibles. L’éditeur de contenu de message est alors activé avec des fonctionnalités de texte enrichi.

**4. Créez le contenu de votre message**

Dans le champ **Contenu du message**, rédigez votre message de remerciement à l’aide de l’éditeur de texte enrichi. L’éditeur prend en charge les éléments suivants :

- **Mise en forme du texte** : options gras, italique, souligné et couleur
- **Listes** : listes à puces et numérotées pour organiser les informations
- **Liens** : liens directs vers les ressources appropriées ou les étapes suivantes.
- **Modification en plein écran** : cliquez sur l’icône de développement pour agrandir l’espace de travail de modification

### Considérations techniques

**Comportement d’affichage des messages :**

- Les messages s’affichent dans un recouvrement modal immédiatement après l’envoi du formulaire
- Le contenu prend en charge la mise en forme HTML et conserve un design réactif
- Les messages peuvent être ignorés par les utilisateurs ou configurés avec des minuteries de fermeture automatique

**Instructions de contenu :**

- Concevoir des messages concis tout en fournissant les informations nécessaires
- Inclure des étapes suivantes claires, le cas échéant
- Pensez à inclure des numéros de référence ou des détails de confirmation
- Garantir un formatage adapté aux appareils mobiles

### Exemple d’implémentation

     Merci pour votre envoi !
    
    Votre demande a été reçue et le numéro de référence qui vous a été attribué est #REF-2024-001234.
    
    **Que se passe-t-il ensuite ?**
    - Vous recevrez un e-mail de confirmation dans les 15 minutes
    - Notre équipe examinera votre demande dans les 2 jours ouvrables
    - Nous vous contacterons directement si des informations supplémentaires sont nécessaires
    
    **Besoin d’aide?** Contactez notre équipe de support à l’adresse support@example.com

## Configuration des URL de redirection

Les URL de redirection dirigent automatiquement les utilisateurs vers des pages spécifiques après l’envoi du formulaire, ce qui permet une intégration transparente avec les workflows existants ou la redirection d’utilisateurs vers du contenu pertinent.

### Quand utiliser les URL de redirection

Les URL de redirection sont optimales pour :

- **Intégration de workflow** : rediriger les utilisateurs vers des tableaux de bord, des pages de compte ou les étapes suivantes d’un processus
- **Diffusion de contenu** : présentation des produits, services ou informations pertinents en fonction des réponses apportées au formulaire
- **Suivi Analytics** : redirection vers des pages avec des implémentations de suivi spécifiques
- **Processus à plusieurs étapes** : faire passer les utilisateurs à la phase suivante de workflows complexes

### Étapes de mise en œuvre

**1. Accédez aux propriétés du formulaire**

Ouvrez votre formulaire adaptatif dans l’éditeur universel et cliquez sur l’icône **Modifier les propriétés du formulaire** pour ouvrir la boîte de dialogue de configuration du formulaire.

**2. Accédez à la configuration de remerciement**

Sélectionnez l’onglet **Merci** dans la boîte de dialogue Propriétés du formulaire pour accéder aux options de configuration de redirection.

**3. Activez la fonctionnalité de redirection**

Choisissez **Rediriger vers l’URL** parmi les options disponibles après l’envoi.

**4. Configurez l’URL de destination**

Saisissez l’URL cible dans le champ fourni. Le système prend en charge plusieurs formats d’URL pour une implémentation flexible.

### Options de configuration de l’URL

**URL absolues**

Adresses web complètes, y compris le protocole et le domaine :

    https://www.example.com/thank-you
    https://dashboard.example.com/user/profile

**Chemins relatifs**

Chemins d’accès relatifs à votre domaine actuel :

    /merci
    /tableau de bord/profil-utilisateur
    ../confirmation-page.html

**Références de page AEM Sites**

Références à d’autres pages dans votre implémentation d’AEM Sites :

    /content/mysite/en/thanks-you
    /content/mysite/en/next-steps

### Considérations techniques

**Comportement de redirection :**

- Les redirections se produisent immédiatement après l’envoi réussi du formulaire
- L’historique du navigateur comprend la redirection pour une fonctionnalité correcte du bouton Précédent
- Le minutage de redirection peut être configuré avec des retards facultatifs

**Validation de l’URL :**

- Le système valide le format de l’URL avant d’autoriser la configuration
- Les URL relatives sont résolues par rapport au domaine actuel
- Les URL externes nécessitent une configuration CORS appropriée si nécessaire.

## Bonnes pratiques et recommandations

### Instructions relatives à l’expérience utilisateur

**Optimisation des messages :**

- **Clarté d’abord** : assurez-vous que les utilisateurs comprennent immédiatement que leur envoi a réussi
- **Ajout de valeur** : fournissez des informations pour aider les utilisateurs à passer aux étapes suivantes
- **Image de marque cohérente** : conservez la voix et le style visuel de votre entreprise
- **Considérations relatives aux appareils mobiles** : tester les messages sur différentes tailles d’écran

**Optimisation de la redirection :**

- **Optimisation des pages** : assurez-vous que les destinations de redirection sont optimisées pour les visiteurs et visiteuses post-formulaire
- **Performances de chargement** : vérifiez que les pages de redirection se chargent rapidement pour conserver l’expérience utilisateur
- **Pertinence du contenu** : assurez-vous que le contenu de redirection est pertinent par rapport au contexte du formulaire

### Considérations relatives à la sécurité

**Validation de l’URL :**

- Implémentez une validation appropriée des URL de redirection pour empêcher les redirections malveillantes.
- Envisager des approches de liste blanche pour les domaines de redirection autorisés
- Surveiller les modèles de redirection à la recherche d’une activité inhabituelle

**Sécurité du contenu :**

- Assainir le contenu du message de remerciement pour éviter l’injection de script
- Mettre en œuvre des politiques de sécurité appropriées pour le contenu de texte enrichi
- Examens réguliers de la sécurité des destinations de redirection

### Analyse et tracking

**Considérations relatives à l’implémentation :**

- **Suivi des objectifs** : configurez des objectifs d’analyse pour les vues de messages de remerciement et les terminaisons de redirection
- **Mappage des parcours utilisateur** : suivez la manière dont les utilisateurs interagissent avec les expériences après envoi
- **Optimisation des conversions** : test A/B de différents messages de remerciement et destinations de redirection

**Stratégies de mesure :**

- Surveiller le temps passé sur les messages de remerciement avant le rejet
- Suivre les taux de clic publicitaire pour les liens dans les messages de remerciement
- Analyse du comportement des utilisateurs sur les pages de destination de redirection

## Points de contrôle de validation

Après avoir configuré votre expérience post-envoi :

**Vérification de la configuration :**

- Les propriétés du formulaire affichent correctement l’option de remerciement sélectionnée
- Le contenu du message s’affiche correctement en mode aperçu
- Les URL de redirection sont correctement formatées et accessibles.
- Tous les liens dans les messages fonctionnent correctement

**Test de l’expérience utilisateur :**

- Envoyer des formulaires de test pour vérifier que l’affichage du message de remerciement est correct
- Tester la fonctionnalité de redirection dans différents navigateurs
- Vérifier la réactivité mobile des messages de remerciement
- Confirmer le chargement correct des destinations de redirection

**Configuration d’Analytics :**

- Codes de suivi correctement implémentés pour les messages de remerciement
- Tracking des destinations de redirection configuré
- Déclenchement correct des événements d’achèvement d’objectif

## Étapes suivantes

Une fois la configuration de l’expérience post-envoi terminée :

- **Surveiller les performances** : consultez les analyses pour comprendre l’interaction des utilisateurs avec les messages de remerciement ou les pages de redirection
- **Itérer et améliorer** : utilisez les commentaires des utilisateurs et les informations sur les données pour affiner votre stratégie post-envoi
- **Implémentation à grande échelle** : appliquez des modèles réussis à d’autres formulaires de votre entreprise.

**Documentation connexe :**

- [Guide de configuration de l’envoi de formulaire](submit-action.md)
- [Bonnes pratiques relatives à l’expérience utilisateur](responsive-layout.md)

