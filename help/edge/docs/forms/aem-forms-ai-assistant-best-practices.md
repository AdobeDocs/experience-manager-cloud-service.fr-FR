---
title: Créateur d’expériences de formulaires - Meilleures pratiques
description: Bonnes pratiques complètes relatives à la création de formulaires efficaces avec Forms Experience Builder, couvrant la conception, l’expérience d’utilisation, les performances et la cohérence de la marque.
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: fe34b44d02c308e7d18a08dd05f21abc67bd0cb2
workflow-type: tm+mt
source-wordcount: '2072'
ht-degree: 100%

---


# Créateur d’expériences de formulaires - Meilleures pratiques

>[!NOTE]
>
> Forms Experience Builder est disponible dans le cadre du programme d’accès anticipé. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : ce guide des bonnes pratiques est en cours de test produit. Il est sujet à des mises à jour et des révisions. Les bonnes pratiques, les recommandations et les exemples peuvent changer à mesure que Forms Experience Builder continue d’évoluer pendant le programme d’accès anticipé.

Ce guide complet fournit les bonnes pratiques éprouvées pour créer des formulaires efficaces et conviviaux à l’aide de Forms ExperienceBuilder. Ces pratiques sont issues d’implémentations réussies et de commentaires des utilisateurs et utilisatrices de divers secteurs d’activité et cas d’utilisation.

## Bonnes pratiques relatives à la conception de formulaire

### Faire simple

**Commencer avec les champs essentiels**

- Ne commencer qu’avec les informations les plus nécessaires pour réduire la surcharge des utilisateurs et utilisatrices.
- Ajouter progressivement de la complexité en fonction des besoins des utilisateurs et utilisatrices et des exigences métier.
- Éviter de demander des informations dont vous n’avez pas réellement besoin ou que vous n’utiliserez pas.
- Tenir compte du temps et de la charge cognitive de l’utilisateur ou de l’utilisatrice lors de la conception de formulaires.

**Utiliser des libellés clairs et explicites**

- Rendre évidentes les fonctions des champs avec des libellés explicites.
- Éviter le jargon technique ou la terminologie interne que les utilisateurs et utilisatrices ne comprendront pas.
- Appliquer des conventions de dénomination cohérentes sur l’ensemble des formulaires.
- Fournir un contexte lorsque les exigences en matière de champs ne sont peut-être pas évidentes.

**Fournir des conseils utiles**

- Inclure du texte d’aide pour les champs complexes avec des exemples et des exigences de mise en forme.
- Utiliser du texte d’espace réservé pour afficher les formats d’entrée attendus.
- Fournir des instructions claires pour les chargements de fichiers, notamment les formats et les limites de taille acceptés.
- Guider les utilisateurs et utilisatrices tout au long des processus à plusieurs étapes avec des indicateurs de progression.

**Tester minutieusement**

- Valider tous les chemins d’accès et scénarios d’utilisation avant le déploiement.
- Tester les formulaires auprès d’utilisateurs et utilisatrices réels de votre audience cible.
- Vérifier que toute la logique conditionnelle fonctionne comme prévu.
- S’assurer que la gestion des erreurs fournit des commentaires clairs et exploitables.

### Divulgation progressive

**Afficher les champs pertinents en fonction du contexte**

- N’afficher les champs supplémentaires que lorsqu’ils deviennent pertinents par rapport aux sélections des utilisateurs et utilisatrices.
- Utiliser une logique conditionnelle pour réduire la charge cognitive et la longueur du formulaire.
- Regrouper les champs associés dans des sections logiques.
- Masquer les options avancées tant que les utilisateurs et utilisatrices n’indiquent pas en avoir besoin.

**Exemple de mise en œuvre :**

    Créer une règle qui n’affiche le panneau @spouseInformation que lorsque @maritalStatus est égal à « Marié(e) »

**Effacer la navigation et la progression**

- Aider les utilisateurs et utilisatrices à déterminer où ils se situent dans des formulaires à plusieurs étapes.
- Fournir une navigation claire entre les sections de formulaire.
- Afficher les indicateurs de progression pour les formulaires plus longs.
- Autoriser les utilisateurs et utilisatrices à enregistrer la progression et à revenir ultérieurement.

## Bonnes pratiques relatives à l’expérience d’utilisation

### Conception « Le mobile d’abord »

**Documentation sur la mise en page réactive**

- Concevoir des formulaires en se focalisant sur les utilisateurs et utilisatrices sur appareils mobiles.
- Utiliser des mises en page à une seule colonne pour les appareils mobiles.
- S’assurer que les cibles tactiles sont de taille appropriée (44 pixels minimum).
- Tester les formulaires sur différentes tailles et orientations d’appareils.

**Interactions optimisées pour le tactile**

- Implémenter des boutons et des champs de saisie plus grands pour les interfaces tactiles.
- Utiliser des types de saisie appropriés pour déclencher des claviers sur appareils mobiles corrects.
- Éviter les interactions impliquant un pointage qui ne fonctionnent pas sur les appareils tactiles.
- Fournir des commentaires visuels clairs pour les interactions des utilisateurs et utilisatrices.

### Conformité en matière d’accessibilité

**Règles WCAG 2.1**

- Suivre les règles Web Content Accessibility Guidelines de conception inclusive.
- Vérifier que les rapports de contraste des couleurs sont corrects (4,5 :1 minimum pour le texte normal).
- Fournir un texte secondaire pour toutes les images et icônes.
- Implémenter une structure d’en-tête et du HTML sémantique appropriés.

**Navigation au clavier**

- S’assurer que tous les éléments de formulaire sont accessibles via la navigation au clavier.
- Fournir des indicateurs de sélection clairs pour tous les éléments interactifs.
- Implémenter un ordre de tabulation logique par le biais de champs de formulaire.
- Inclure des liens de saut de navigation pour les formulaires complexes.

**Prise en charge de lecteur d’écran**

- Utiliser des libellés ARIA et des descriptions appropriés pour les champs de formulaire.
- Fournir des messages d’erreur clairs qui sont présentés sur les lecteurs d’écran.
- S’assurer que les modifications de contenu dynamique sont correctement annoncées.
- Tester les formulaires avec le logiciel de lecteur d’écran effectif.

### Optimisation des performances

**Vitesse de chargement**

- Optimiser les temps de chargement des formulaires en réduisant la taille de l’offre groupée initiale.
- Implémenter le chargement différé pour les sections de formulaire non critiques.
- Optimiser les images et les ressources pour la diffusion web
- Activer des stratégies de mise en cache appropriées pour les ressources statiques.

**Performances d’exécution**

- Utiliser un minutage de validation approprié pour trouver un équilibre entre expérience d’utilisation et performances.
- Implémenter le rebond pour la validation en temps réel afin de réduire les requêtes du serveur.
- Mettre en mémoire cache les données fréquemment consultées et les résultats de validation.
- Optimiser l’exécution de la logique conditionnelle pour les formulaires complexes.

**Enregistrement automatique et protection des données**

- Implémenter l’enregistrement automatique de la progression du formulaire pour éviter la perte de données.
- Fournir une fonctionnalité hors ligne pour remplir le formulaire lorsque cela est possible.
- Inclure la logique de nouvelle tentative pour les envois ayant échoué.
- Proposer des options d’export de données à des fins de sauvegarde pour les utilisateurs et utilisatrices.

## Bonnes pratiques relatives à la cohérence de la marque

### Préparer les ressources de marque à l’avance

**Création de modèles de marque**

- Développer des modèles de formulaire normalisés avec l’identité visuelle de votre organisation.
- Inclure des modèles de couleurs, de typographie et de mise en page cohérents.
- Préparer des composants réutilisables qui correspondent aux directives de votre marque.
- Documenter des normes de style pour une implémentation cohérente entre les équipes.

**Définition de directives de style**

- Définir des normes de style de champ, de conception de boutons et d’espacement cohérentes.
- Créer un guide de style qui comprend des codes couleur, des spécifications de police et des règles de mise en page.
- Définir des modèles d’interaction et des directives d’animation.
- Préparer des messages d’erreur et du texte d’aide spécifiques à la marque.

**Création d’une bibliothèque de composants**

- Créer des composants de formulaire réutilisables correspondant à votre identité de marque.
- Développer des modèles de navigation et des éléments d’interface d’utilisation cohérents.
- Préparer des icônes, des logos et des ressources visuelles de marque pour l’intégration de formulaire.
- Définir des modèles pour les types de formulaires courants (contact, enregistrement, commentaires).

### Stratégies d’implémentation de marque

**Prompts de style pour la cohérence**

Incluez des instructions spécifiques à la marque dans vos prompts :

    Créer un formulaire de contact professionnel en utilisant :
    - Bleu d’entreprise (#003366) pour les boutons principaux et les en-têtes
    - Famille de polices Open Sans pour tous les éléments de texte
    - Taille de police minimale de 16 pixels pour la conformité en matière d’accessibilité
    - Espacement cohérent de 24 pixels entre les sections de formulaire
    - Logo de la société dans l’en-tête avec un positionnement de marque approprié

**Gestion des bibliothèques de modèles**

- Gérer une collection de modèles de formulaires de marque pour les cas d’utilisation courants.
- Gestion de versions de vos modèles de marque pour garantir la cohérence.
- Fournir une documentation claire pour l’utilisation et la personnalisation des modèles.
- Vérifier et mettre à jour régulièrement les ressources de marque pour maintenir les normes actuelles.

>[!NOTE]
>
>**Composants personnalisés** : coordonnez-vous avec l’équipe de développement sur l’utilisation de composants spécifiques à l’organisation et leur compatibilité avec Forms Experience Builder avant d’implémenter des éléments de marque personnalisés.

## Bonnes pratiques relatives au contenu et à la communication

### Approches de création de formulaire

**Deux méthodes principales**

Choisissez la méthode de création la plus adaptée à vos besoins :

1. **Créer en partant de zéro** : idéale pour les nouveaux formulaires avec des exigences spécifiques.
2. **Importer et convertir** : idéale pour moderniser les formulaires et documents existants.

**Prompts en langage naturel**

- Être précis et avoir le souci du détail dans les descriptions de vos formulaires.
- Utiliser un langage clair et professionnel plutôt que des termes techniques.
- Fournir un contexte sur l’objectif et l’audience cible du formulaire.
- Inclure les exigences de validation et de règle métier dans les prompts initiaux.

### Stratégie de développement incrémentiel

**Démarrer simplement, puis complexifier**

- Commencer avec la structure de formulaire de base et les champs essentiels.
- Ajouter des règles de validation et une logique métier de manière incrémentielle.
- Tester chaque ajout avant de passer à l’amélioration suivante.
- Collecter les commentaires des utilisateurs et utilisatrices à chaque étape du développement.

**Exemple d’approche incrémentielle :**

    Étape 1 : « Créer un formulaire de contact de base avec les champs de nom, d’adresse e-mail et de message »
    Étape 2 : « Rendre les champs @name et @email obligatoires avec la validation appropriée »
    Étape 3 : « Ajouter un texte d’espace réservé et un texte d’aide pour guider l’utilisateur ou l’utilisatrice »
    Étape 4 : « Ajouter une logique conditionnelle basée sur le type de requête »

### Bonnes pratiques relatives à la référence de champ

**Conventions de dénomination cohérentes**

- Utiliser des noms de champs clairs et explicites qui correspondent à leur objectif.
- Maintenir des modèles de dénomination cohérents entre les formulaires.
- Utiliser camelCase ou snake_case de manière cohérente dans tous vos formulaires.
- Documenter les conventions de dénomination des champs pour la cohérence de l’équipe.

**Références de champ efficaces**

- Utiliser la syntaxe `@fieldName` lors de la modification des champs existants.
- Préciser à quels champs vous faites référence dans les formulaires complexes.
- Regrouper les modifications de champs associées dans des requêtes uniques.
- Vérifier les noms de champs avant de les utiliser dans une logique conditionnelle.

## Bonnes pratiques relatives à l’intégration et à l’envoi

### Stratégie d’envoi multicanal

**Actions principale et secondaire**

- Configurer des points d’entrée d’envoi principaux pour les processus métier essentiels.
- Configurer des actions secondaires pour les notifications, les confirmations et la sauvegarde des données.
- Implémenter la gestion des erreurs et la logique de nouvelle tentative pour les envois ayant échoué.
- Fournir des commentaires à l’utilisateur ou l’utilisatrice pour tous les états d’envoi (réussite, échec, traitement en cours).

**Planification de l’intégration**

- Commencer avec une configuration d’envoi de base et ajouter des intégrations de manière incrémentielle.
- Tester chaque intégration séparément avant de combiner plusieurs points d’entrée.
- Documenter les exigences d’API et les méthodes d’authentification.
- Planifier les exigences de transformation et de mappage des données.

### Gestion des erreurs et récupération

**Messages d’erreur conviviaux**

- Fournir des messages d’erreur clairs et exploitables qui aident les utilisateurs et utilisatrices à résoudre des problèmes.
- Éviter les codes d’erreur techniques ou les messages système dans le contenu présenté à l’utilisateur ou l’utilisatrice.
- Proposer d’autres actions en cas d’échec de l’envoi principal.
- Inclure des coordonnées pour les utilisateurs et utilisatrices qui ont besoin d’une aide supplémentaire.

**Protection des données et récupération**

- Implémenter l’enregistrement local des données pour la récupération du formulaire en cas d’erreur.
- Fournir des options permettant aux utilisateurs et utilisatrices de télécharger leurs données de formulaire en tant que sauvegarde.
- Configurer la surveillance et les alertes des échecs d’envoi.
- Planifier des procédures de récupération en cas de panne du système ou de maintenance.

## Bonnes pratiques relatives aux performances et à l’analyse

### Surveillance et optimisation

**Mesures clés de performances**

- Suivre les taux d’achèvement des formulaires et les points d’abandon.
- Surveiller les temps de chargement et les modèles d’interaction des utilisateurs et utilisatrices.
- Mesurer l’efficacité de la validation et les taux d’erreur.
- Analyser les commentaires des utilisateurs et utilisatrices et les scores de satisfaction.

**Amélioration continue**

- Vérifier régulièrement l’analyse du formulaire pour identifier les opportunités d’optimisation.
- Exécuter des tests A/B de différentes conceptions de formulaire et de différents flux d’utilisation.
- Collecte et analyse des commentaires des utilisateurs et utilisatrices à des fins d’améliorations itératives.
- Analyse comparative des performances par rapport aux normes du secteur.

### Qualité des données et validation

**Stratégies de validation intelligentes**

- Implémenter la validation en temps réel pour des commentaires des utilisateurs et utilisatrices immédiats.
- Utiliser la validation progressive pour guider les utilisateurs et utilisatrices dans des exigences complexes.
- Fournir des messages de validation clairs qui expliquent comment corriger les erreurs.
- Trouver un équilibre entre rigueur de la validation et expérience d’utilisation.

**Intégrité des données**

- Implémenter la validation entre les champs pour la cohérence des données.
- Utiliser des types de saisie et des contraintes appropriés pour éviter des données non valides.
- Fournir des exemples de format de données et des conseils pour les champs complexes.
- Audit régulier de la qualité des données envoyées et de l’efficacité de la validation.

## Bonnes pratiques relatives à la sécurité et à la conformité

### Protection des données

**Confidentialité dès la conception**

- Ne collecter que les données minimales nécessaires à l’objectif de votre entreprise.
- Implémenter des politiques de conservation et de suppression des données appropriées.
- Fournir des avis de confidentialité et des mécanismes de consentement clairs.
- Garantir la conformité aux réglementations sur la protection des données (RGPD, CCPA, etc.).

**Implémentation de la sécurité**

- Utiliser le chiffrement HTTPS pour tous les envois de formulaires et la transmission de données.
- Implémenter une validation de la saisie et un nettoyage appropriés.
- Configurer un chargement de fichier sécurisé avec les restrictions et l’analyse antivirus appropriées.
- Audits de sécurité réguliers et évaluations des vulnérabilités.

### Considérations relatives à la conformité

**Exigences réglementaires**

- Comprendre et implémenter les exigences de conformité spécifiques au secteur.
- Documenter les mesures de conformité à des fins d’audit.
- Vérifier régulièrement les changements réglementaires et leur impact sur les formulaires.
- Formation du personnel sur les exigences de conformité et la mise en œuvre.

**Conformité en matière d’accessibilité**

- Suivre les règles d’accessibilité WCAG 2.1 AA.
- Test d’accessibilité régulier avec les technologies d’assistance.
- Test utilisateurs et utilisatrices auprès de personnes en situation de handicap.
- Documentation des fonctionnalités d’accessibilité et des mesures de conformité.

## Bonnes pratiques relatives à la collaboration d’équipe

### Documentation et partage des connaissances.

**Documentation sur le formulaire**

- Maintenir une documentation claire sur les objectifs, les exigences et les règles métier des formulaires.
- Documenter les points d’entrée de l’intégration, les flux de données et les dépendances.
- Conserver l’historique des versions et les journaux des modifications pour les mises à jour des formulaires.
- Partager les bonnes pratiques et les leçons apprises entre les équipes.

**Formation et adoption**

- Fournir une formation aux membres de l’équipe sur les fonctionnalités de Forms Experience Builder.
- Définir des directives pour une création de formulaires cohérente dans l’ensemble de l’organisation.
- Sessions régulières de partage des connaissances sur les nouvelles fonctionnalités et les bonnes pratiques.
- Programmes de tutorat pour les nouveaux utilisateurs et les nouvelles utilisatrices de la plateforme.

### Assurance qualité

**Processus de révision**

- Implémenter des processus de révision par les pairs pour la conception et la mise en œuvre des formulaires.
- Définir des protocoles de test pour les fonctionnalités de formulaire et l’expérience d’utilisation.
- Audits réguliers des formulaires existants pour les opportunités d’optimisation.
- Collecte de commentaires des utilisateurs et utilisatrices internes et finaux.

**Normes et instructions**

- Développer des normes organisationnelles pour la conception et la mise en œuvre des formulaires.
- Créer des modèles et des instructions pour les types de formulaires courants.
- Définir des processus d’approbation pour les nouveaux formulaires et les modifications majeures.
- Vérifier et mettre à jour régulièrement les normes organisationnelles.

## Bonnes pratiques avancées

### Champs intelligents améliorés par LLM

**Exploitation des connaissances en IA**

- Utiliser les connaissances intégrées d’IA pour obtenir des options de champ complètes.
- Demander des champs intelligents pour les données géographiques, les classifications métier et les normes du secteur.
- Implémenter une population de champs intelligente pour une meilleure expérience d’utilisation.
- Tester la précision et l’exhaustivité des champs intelligents pour vos cas d’utilisation spécifiques.

**Exemples de champs intelligents**

    « Ajouter un champ d’aéroport de départ avec tous les principaux aéroports du monde entier, incluant les codes IATA »
    « Créer un champ sectoriel complet à l’aide de la classification SCIAN standard »
    « Inclure un menu déroulant de certification professionnelle qui s’adapte en fonction du champ du poste »

### Logique de formulaire avancée

**Règles métier complexes**

- Décomposer une logique métier complexe en composants plus petits et pouvant être testés.
- Documenter clairement les exigences des règles métier avant la mise en œuvre.
- Tester minutieusement les cas Edge et les scénarios d’exception
- Fournir des commentaires d’utilisateurs et d’utilisatrices clairs en cas de violation de règles métier

**Comportement de formulaire dynamique**

- Utiliser la révélation progressive pour afficher les champs pertinents en fonction des entrées des utilisateurs et utilisatrices
- Implémenter des paramètres par défaut intelligents qui peuvent être remplacés par les utilisateurs et utilisatrices
- Créer des formulaires adaptatifs qui s’ajustent en fonction du comportement et des préférences des utilisateurs et utilisatrices.
- Équilibrez l’automatisation avec le contrôle et la transparence des utilisateurs et utilisatrices

## Validation et tests

### Stratégie de test complète

**Tests multi-niveaux**

- Test unitaire pour des composants de formulaire et des règles de validation spécifiques
- Test d’intégration pour les points d’entrée d’envoi et les flux de données
- Test d’acceptation des utilisateurs et utilisatrices avec des groupes représentatifs
- Test de performance sous différentes conditions de charge

**Validation sur plusieurs plateformes**

- Test des formulaires dans différents navigateurs et versions
- Validation de l’expérience mobile sur différents appareils et tailles d’écran
- Test d’accessibilité avec différentes technologies d’assistance
- Test de l’état du réseau pour différentes vitesses de connexion

### Mesures de qualité

**Indicateurs de réussite**

- Taux de remplissage des formulaires supérieurs aux références du secteur
- Faibles taux d’erreur et scores élevés de satisfaction des utilisateurs et utilisatrices
- Temps de chargement rapides et interactions utilisateur réactives
- Intégration réussie aux systèmes et processus back-end

**Surveillance continue**

- Examen régulier des mesures de performances des formulaires et des commentaires des utilisateurs et utilisatrices
- Identification proactive et résolution des problèmes
- Analyse des tendances pour l’utilisation et l’efficacité des formulaires
- Analyse comparative par rapport aux normes et aux bonnes pratiques du secteur

Pour obtenir des conseils supplémentaires et des exemples détaillés, consultez le [Guide de prise en main de Forms Experience Builder](forms-ai-assistant-getting-started.md) et la [Bibliothèque de prompts de Forms Experience Builder](ai-assistant-prompt-library.md).
