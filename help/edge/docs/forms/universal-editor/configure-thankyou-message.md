---
title: Comment configurer une page de redirection ou un message de remerciement
description: Découvrez comment les utilisateurs et utilisatrices peuvent voir affiché un message de remerciement ou être redirigés vers une page web que les personnes chargées de la création de formulaires peuvent configurer lors de la phase de création.
feature: Adaptive Forms, Edge Delivery Services
role: User
level: Intermediate
exl-id: cacd7b0a-aad0-4b5d-a6a0-e4bac4cb196d
source-git-commit: fd3c53cf5a6d1c097a5ea114a831ff626ae7ad7e
workflow-type: tm+mt
source-wordcount: '1139'
ht-degree: 99%

---

# Configurer des messages de remerciement et des URL de redirection

Les expériences post-envoi ont un impact significatif sur la satisfaction des utilisateurs et utilisatrices et les taux de remplissage des formulaires. L’éditeur universel d’Adobe fournit des options complètes pour configurer ce que les utilisateurs et utilisatrices voient après l’envoi des formulaires, que ce soit par le biais de messages de remerciement personnalisés ou de redirections stratégiques vers des pages spécifiques.

Cet article fournit des instructions détaillées sur l’implémentation des messages de remerciement et des URL de redirection, y compris des considérations techniques, des bonnes pratiques et des directives d’expérience clientèle pour maximiser l’efficacité de vos envois de formulaire.

## Prérequis

Avant de configurer les expériences post-envoi, vérifiez les points suivants :

**Configuration technique :**

- Accès à l’éditeur universel avec les autorisations appropriées
- Formulaire adaptatif existant créé dans l’éditeur universel
- Compréhension des exigences de votre organisation en matière d’URL de redirection

**Considérations relatives à la planification :**

- **Stratégie des messages** : définissez le ton, la longueur et les informations spécifiques à inclure dans les messages de remerciement.
- **Stratégie de redirection** : identifiez les pages cibles et assurez-vous qu’elles sont optimisées pour les expériences post-remplissage des formulaires.
- **Intégration d’analyse** : planifiez le suivi des interactions des utilisateurs et des utilisatrices avec les messages de remerciement ou les destinations de redirection.

## Configurer des messages de remerciement

Les messages de remerciement confirment immédiatement la réussite de l’envoi du formulaire et peuvent inclure du contenu personnalisé, les étapes suivantes ou des informations importantes relatives à l’envoi du formulaire par l’utilisateur ou l’utilisatrice.

### Quand utiliser les messages de remerciement

Les messages de remerciement sont plus efficaces lorsque :

- **Simple confirmation** : les utilisateurs et utilisatrices ont besoin d’une confirmation sans exigences de navigation supplémentaires.
- **Contenu didactique** : vous devez indiquer les étapes suivantes spécifiques ou des informations importantes.
- **Cohérence de la marque** : le message peut être conçu pour s’aligner sur le style de communication de votre entreprise.
- **Expérience d’une seule page** : les utilisateurs et utilisatrices doivent rester sur la page active pour assurer la continuité du workflow.

### Étapes de mise en œuvre

**1. Accéder aux propriétés du formulaire**

Ouvrez votre formulaire adaptatif dans l’éditeur universel et cliquez sur l’icône **Modifier les propriétés du formulaire** dans la barre d’outils. Cela ouvre la boîte de dialogue complète des propriétés du formulaire.

![Icône Propriétés du formulaire](/help/forms/assets/ue-form-properties-icon.png)

**2. Accéder à la configuration du remerciement**

Dans la boîte de dialogue Propriétés du formulaire, sélectionnez l’onglet **Remerciement** pour accéder aux options de configuration après l’envoi.

![Propriétés de formulaire de l’éditeur universel](/help/forms/assets/ue-form-properties.png)

**3. Configurer l’affichage du message**

Sélectionnez **Afficher le message** dans les options disponibles.

![merci](/help/edge/docs/forms/universal-editor/assets/thankyou-ue.png)

**4. Créer le contenu de votre message**

Dans le champ **Contenu du message**, rédigez votre message de remerciement à l’aide de l’éditeur de texte enrichi. L’éditeur prend en charge les éléments suivants :

- **Mise en forme du texte** : options gras, italique, souligné et couleur.
- **Listes** : listes à puces et numérotées pour organiser les informations.
- **Liens** : liens directs vers les ressources appropriées ou les étapes suivantes.
- **Modification en plein écran** : cliquez sur l’icône de développement pour agrandir l’espace de travail de modification.

### Considérations techniques

**Comportement d’affichage des messages :**

- Les messages s’affichent dans un recouvrement modal immédiatement après l’envoi du formulaire.
- Le contenu prend en charge la mise en forme HTML et conserve une conception réactive.
- Les messages peuvent être ignorés par les utilisateurs et les utilisatrices ou configurés avec des minuteries de fermeture automatique.

**Instructions sur le contenu :**

- Concevez des messages concis tout en fournissant les informations nécessaires.
- Incluez des étapes suivantes claires, le cas échéant.
- Pensez à inclure des numéros de référence ou des détails de confirmation.
- Assurez-vous que la mise en forme est adaptée aux appareils mobiles.

### Exemple de mise en œuvre

    Merci pour votre envoi.
    
    Votre demande a été reçue et le numéro de référence qui vous a été attribué est #REF-2024-001234.
    
    **Prochaines étapes :**
    - Vous recevrez un e-mail de confirmation dans 15 minutes.
    - Notre équipe examinera votre demande sous 2 jours ouvrables.
    - Nous vous contacterons directement en cas de besoin d’informations supplémentaires.
    
    **Besoin d’aide ?** Contactez notre équipe d’assistance à l’adresse support@example.com.

## Configurer des URL de redirection

Les URL de redirection dirigent automatiquement les utilisateurs et les utilisatrices vers des pages spécifiques après l’envoi du formulaire, ce qui permet une intégration transparente avec les workflows existants ou la redirection des utilisateurs et utilisatrices vers du contenu pertinent.

### Quand utiliser les URL de redirection

Les URL de redirection sont optimales pour :

- **L’intégration de workflow** : redirigez les utilisateurs et les utilisatrices vers des tableaux de bord, des pages de compte ou les étapes suivantes d’un processus.
- **La diffusion de contenu** : présentation des produits, services ou informations pertinents en fonction des réponses apportées au formulaire.
- **Le suivi d’analyse** : redirection vers des pages avec des implémentations de suivi spécifiques.
- **Les processus à plusieurs étapes** : faire passer les utilisateurs et les utilisatrices à la phase suivante de workflows complexes.

### Étapes de mise en œuvre

**1. Accéder aux propriétés du formulaire**

Ouvrez votre formulaire adaptatif dans l’éditeur universel et cliquez sur l’icône **Modifier les propriétés du formulaire** pour ouvrir la boîte de dialogue de configuration du formulaire.

![Icône Propriétés du formulaire](/help/forms/assets/ue-form-properties-icon.png)

**2. Accéder à la configuration du remerciement**

Sélectionnez l’onglet **Remerciement** dans la boîte de dialogue Propriétés du formulaire pour accéder aux options de configuration de redirection.

![Propriétés de formulaire de l’éditeur universel](/help/forms/assets/ue-form-properties.png)

**3. Activer la fonctionnalité de redirection**

Choisissez **Rediriger vers une URL** parmi les options disponibles après l’envoi.

![rediriger](/help/edge/docs/forms/universal-editor/assets/redirect-ue.png)

**4. Configurer l’URL de destination**

Saisissez l’URL cible dans le champ fourni. Le système prend en charge plusieurs formats d’URL pour une implémentation flexible.

### Options de configuration de l’URL

**URL absolues**

Adresses web complètes comprenant le protocole et le domaine :

    https://www.example.com/thank-you
    https://dashboard.example.com/user/profile

**Chemins relatifs**

Chemins d’accès relatifs à votre domaine actuel :

    /thank-you
    /dashboard/user-profile
    ../confirmation-page.html

**Références aux pages AEM Sites**

Références à d’autres pages dans votre implémentation d’AEM Sites :

    /content/mysite/en/thank-you
    /content/mysite/en/next-steps

### Considérations techniques

**Comportement de redirection :**

- Les redirections se produisent immédiatement après l’envoi du formulaire.
- L’historique du navigateur comprend la redirection pour une fonctionnalité correcte du bouton Précédent.
- Le minutage de redirection peut être configuré avec des délais facultatifs.

**Validation de l’URL :**

- Le système valide le format de l’URL avant d’autoriser la configuration.
- Les URL relatives sont résolues par rapport au domaine actuel.
- Les URL externes nécessitent une configuration CORS appropriée le cas échéant.

## Bonnes pratiques et recommandations

### Conseils pour l’expérience d’utilisation

**Optimisation des messages :**

- **La clarté avant tout** : assurez-vous que les utilisateurs et les utilisatrices comprennent immédiatement que leur envoi a réussi.
- **Ajout de valeur** : fournissez des informations pour aider les utilisateurs et les utilisatrices à passer aux étapes suivantes.
- **Image de marque cohérente** : conservez l’identité verbale et le style visuel de votre entreprise.
- **Considérations relatives aux appareils mobiles** : testez les messages sur différentes tailles d’écran.

**Optimisation de la redirection :**

- **Optimisation des pages** : assurez-vous que les destinations de redirection sont optimisées pour les visiteurs et visiteuses après le remplissage des formulaires.
- **Performances de chargement** : vérifiez que les pages de redirection se chargent rapidement pour conserver une bonne expérience d’utilisation.
- **Pertinence du contenu** : assurez-vous que le contenu de redirection est pertinent par rapport au contexte du formulaire.

### Considérations relatives à la sécurité

**Validation de l’URL :**

- Implémentez une validation appropriée des URL de redirection pour empêcher les redirections malveillantes.
- Envisagez des approches de liste autorisée pour les domaines de redirection autorisés.
- Surveillez les modèles de redirection à la recherche d’une activité inhabituelle.

**Sécurité du contenu :**

- Assainissez le contenu du message de remerciement pour éviter l’injection de script.
- Mettez en œuvre des politiques de sécurité appropriées pour le contenu de texte enrichi.
- Contrôlez régulièrement la sécurité des destinations de redirection.

### Analyse et tracking

**Considérations relatives à l’implémentation :**

- **Suivi des objectifs** : configurez des objectifs d’analyse pour les vues de messages de remerciement et les terminaisons de redirection.
- **Mappage des parcours des utilisateurs et utilisatrices** : suivez la manière dont les utilisateurs et utilisatrices interagissent avec les expériences post-envoi.
- **Optimisation des conversions** : effectuez des tests A/B avec différents messages de remerciement et destinations de redirection.

**Stratégies de mesure :**

- Surveillez le temps passé sur les messages de remerciement avant le rejet.
- Suivez les taux de clics des liens dans les messages de remerciement.
- Analysez le comportement des utilisateurs et utilisatrices sur les pages de destination de redirection.

## Points de contrôle de validation

Après avoir configuré votre expérience post-envoi :

**Vérification de la configuration :**

- Les propriétés du formulaire affichent correctement l’option de remerciement sélectionnée.
- Le contenu du message s’affiche correctement en mode aperçu.
- Les URL de redirection sont correctement formatées et accessibles.
- Tous les liens dans les messages fonctionnent correctement.

**Test de l’expérience d’utilisation :**

- Envoyez des formulaires de test pour vérifier que l’affichage du message de remerciement est correct.
- Testez la fonctionnalité de redirection dans différents navigateurs.
- Vérifiez la réactivité mobile des messages de remerciement.
- Vérifiez que les destinations de redirection se chargent correctement.

**Configuration de l’analyse :**

- Codes de suivi correctement implémentés pour les messages de remerciement.
- Suivi des destinations de redirection configuré.
- Déclenchement correct des événements d’achèvement d’objectif.

## Étapes suivantes

Après avoir configuré votre expérience post-envoi :

- **Surveiller les performances** : consultez les analyses pour comprendre l’interaction des utilisateurs et utilisatrices avec les messages de remerciement ou les pages de redirection.
- **Itérer et améliorer** : utilisez les commentaires des utilisateurs et utilisatrices et les informations sur les données pour affiner votre stratégie post-envoi.
- **Mettre à l’échelle l’implémentation** : appliquez des modèles éprouvés à d’autres formulaires de votre entreprise.

**Documentation connexe :**

- [Guide de configuration de l’envoi de formulaire](submit-action.md)
- [Bonnes pratiques relatives à l’expérience d’utilisation](responsive-layout.md)
