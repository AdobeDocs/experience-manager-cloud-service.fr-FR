---
title: Forms Experience Builder - Bonnes pratiques
description: Bonnes pratiques complètes relatives à la création de formulaires efficaces avec Forms Experience Builder, couvrant la conception, l’expérience utilisateur, les performances et la cohérence de la marque.
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: fe34b44d02c308e7d18a08dd05f21abc67bd0cb2
workflow-type: tm+mt
source-wordcount: '2072'
ht-degree: 0%

---


# Forms Experience Builder - Bonnes pratiques

>[!NOTE]
>
> Forms Experience Builder est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail de votre adresse professionnelle à `aem-forms-ea@adobe.com` pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : ce guide des bonnes pratiques est en cours de test par rapport au produit et est sujet à des mises à jour et des révisions. Les bonnes pratiques, recommandations et exemples peuvent changer à mesure que Forms Experience Builder continue d’évoluer pendant le programme d’adoption précoce.

Ce guide complet fournit les bonnes pratiques éprouvées pour créer des formulaires efficaces et conviviaux à l’aide de Forms Experience Builder. Ces pratiques sont issues d’implémentations réussies et de commentaires des utilisateurs et utilisatrices de divers secteurs d’activité et cas d’utilisation.

## Bonnes pratiques relatives à la conception de formulaire

### Restez simple

**Commencer avec les champs essentiels**

- Commencez avec uniquement les informations les plus nécessaires pour réduire la surcharge des utilisateurs
- Ajoutez progressivement la complexité en fonction des besoins des utilisateurs et des exigences commerciales.
- Évitez de demander des informations dont vous n’avez pas réellement besoin ou que vous n’utilisez pas
- Tenir compte du temps et de la charge cognitive de l’utilisateur ou de l’utilisatrice lors de la conception de formulaires

**Utiliser Des Libellés Clairs Et Descriptifs**

- Rendre les fonctions de champ immédiatement visibles avec des libellés descriptifs
- Évitez le jargon technique ou la terminologie interne que les utilisateurs ne comprendront pas
- Appliquer des conventions d’étiquetage cohérentes dans l’ensemble des formulaires
- Fournir un contexte lorsque les exigences en matière de champs peuvent ne pas être évidentes

**Fournissez Des Conseils Utiles**

- Incluez le texte d’aide pour les champs complexes avec des exemples et des exigences de mise en forme
- Utiliser un texte d’espace réservé pour afficher les formats d’entrée attendus
- Fournir des instructions claires pour les chargements de fichiers, y compris les formats et les limites de taille acceptés
- Guider les utilisateurs à travers des processus à plusieurs étapes avec des indicateurs de progression

**Tester minutieusement**

- Valider tous les chemins d’accès et scénarios utilisateur avant le déploiement
- Tester des formulaires avec des utilisateurs réels de votre audience cible
- Vérifiez que toute logique conditionnelle fonctionne comme prévu.
- Assurez-vous que la gestion des erreurs fournit des commentaires clairs et exploitables.

### Divulgation Progressive

**Afficher les champs pertinents en fonction du contexte**

- Afficher les champs supplémentaires uniquement lorsqu’ils deviennent pertinents pour les sélections des utilisateurs
- Utiliser la logique conditionnelle pour réduire la charge cognitive et la longueur du formulaire
- Regroupez les champs associés dans des sections logiques
- Masquez les options avancées jusqu’à ce que les utilisateurs et utilisatrices indiquent en avoir besoin

**Exemple d’implémentation :**

    Créez une règle qui affiche @spouseInformation panneau uniquement lorsque @maritalStatus est égal à « Marié(e) »

**Effacer la navigation et la progression**

- Aider les utilisateurs à comprendre où ils se trouvent dans les formulaires à plusieurs étapes
- Fournir une navigation claire entre les sections de formulaire
- Afficher les indicateurs de progression pour les formulaires plus longs
- Autoriser les utilisateurs à enregistrer la progression et à revenir ultérieurement

## Bonnes pratiques relatives à l’expérience utilisateur

### Conception mobile-first

**Optimisation de la disposition réactive**

- Concevoir des formulaires avec des utilisateurs mobiles comme principale considération
- Utiliser des dispositions à une seule colonne pour les appareils mobiles
- Assurez-vous que les cibles tactiles sont de taille appropriée (44 px minimum)
- Tester des formulaires sur différentes tailles et orientations d’appareil

**Interactions tactiles**

- Implémenter des boutons et des champs de saisie plus volumineux pour les interfaces tactiles
- Utiliser des types d’entrée appropriés pour déclencher des claviers mobiles corrects
- Évitez les interactions qui ne fonctionnent pas sur les appareils tactiles et qui sont dépendantes du pointage
- Fournissez des commentaires visuels clairs pour les interactions utilisateur.

### Conformité à l’accessibilité

**Instructions relatives à WCAG 2.1**

- Appliquez les consignes d’accessibilité du contenu web pour une conception inclusive
- Assurez-vous que les rapports de contraste des couleurs sont corrects (minimum 4,5 :1 pour le texte normal)
- Fournissez un texte secondaire pour toutes les images et icônes
- Implémenter une structure d’en-tête et une HTML sémantique appropriées

**Navigation au clavier**

- Assurez-vous que tous les éléments de formulaire sont accessibles via la navigation au clavier
- Fournir des indicateurs de focus clairs pour tous les éléments interactifs
- Implémenter un ordre de tabulation logique par le biais des champs de formulaire
- Inclure des liens de navigation ignorés pour les formulaires complexes

**Prise en charge de Screens Reader**

- Utiliser des libellés ARIA et des descriptions appropriés pour les champs de formulaire
- Fournir des messages d’erreur clairs qui sont annoncés aux lecteurs d’écran
- Assurez-vous que les modifications du contenu dynamique sont correctement annoncées
- Tester les formulaires avec le logiciel de lecteur d’écran actuel

### Optimisation des performances

**Vitesse de chargement**

- Optimisation des temps de chargement des formulaires en réduisant la taille du lot initial
- Implémenter le chargement différé pour les sections de formulaire non critiques
- Optimisation des images et des ressources pour la diffusion web
- Activation des stratégies de mise en cache appropriées pour les ressources statiques

**Performances d’exécution**

- Utiliser un timing de validation approprié pour équilibrer expérience utilisateur et performances
- Implémenter le rebond pour la validation en temps réel afin de réduire les requêtes du serveur
- Mettre en cache les données fréquemment consultées et les résultats de validation
- Optimiser l’exécution de la logique conditionnelle pour les formulaires complexes

**Enregistrement automatique et protection des données**

- Implémenter l’enregistrement automatique de la progression du formulaire pour éviter la perte de données
- Fournir une fonctionnalité hors ligne lorsque cela est possible pour remplir le formulaire
- Inclure la logique de reprise pour les envois ayant échoué
- Offrir des options d’exportation de données en tant que sauvegarde pour les utilisateurs

## Bonnes pratiques en matière de cohérence des marques

### Préparation préalable de Brand Assets

**Créer des modèles de marque**

- Développez des modèles de formulaire normalisés avec l’identité visuelle de votre entreprise.
- Inclure des modèles de couleurs, de typographie et de mise en page cohérents
- Préparer des composants réutilisables qui correspondent aux directives de votre marque
- Normes de style de document pour une implémentation cohérente entre les équipes

**Définir des directives de style**

- Définir des normes de style de champ, de conception des boutons et d’espacement cohérentes
- Créez un guide de style qui comprend des codes couleur, des spécifications de police et des règles de disposition
- Définir des modèles d’interaction et des instructions d’animation
- Préparer des messages d’erreur et du texte d’aide spécifiques à la marque

**Créer une bibliothèque de composants**

- Créer des composants de formulaire réutilisables correspondant à votre identité de marque
- Développement de modèles de navigation et d’éléments d’interface utilisateur cohérents
- Préparation des icônes de marque, des logos et des ressources visuelles pour l’intégration de formulaires
- Établissez des modèles pour les types de formulaires courants (contact, enregistrement, commentaires)

### Stratégies d’implémentation de marque

**Invite de style pour la cohérence**

Incluez des instructions spécifiques à la marque dans vos invites :

    Créer un formulaire de contact professionnel en utilisant :
    - Bleu d’entreprise (#003366) pour les boutons principaux et les en-têtes
    - Ouvrir la famille de polices Sans pour tous les éléments de texte
    - Taille de police minimale de 16 px pour la conformité en matière d’accessibilité
    - Espacement cohérent de 24 px entre les sections de formulaire
    - Logo de la société dans l’en-tête avec un positionnement de marque approprié

**Gestion de la bibliothèque de modèles**

- Gérer une collection de modèles de formulaires de marque pour les cas d’utilisation courants
- Contrôlez les versions de vos modèles de marque pour garantir la cohérence
- Fournir une documentation claire pour l’utilisation et la personnalisation des modèles
- Examen et mise à jour réguliers des ressources de la marque pour maintenir les normes actuelles

>[!NOTE]
>
>**Composants personnalisés** : collaborez avec votre équipe de développement sur l’utilisation de composants spécifiques à une organisation et leur compatibilité avec Forms Experience Builder avant de mettre en œuvre des éléments de marque personnalisés.

## Bonnes pratiques relatives au contenu et à la communication

### Approches de création de formulaire

**Deux méthodes de Principal**

Choisissez la méthode de création la plus adaptée à vos besoins :

1. **Créer en partant de zéro** : idéal pour les nouveaux formulaires avec des exigences spécifiques
2. **Importer et convertir** : idéal pour moderniser les formulaires et documents existants

**Invites en langage naturel**

- Soyez précis et détaillé dans les descriptions de vos formulaires.
- Utilisez un langage clair et axé sur les affaires plutôt que des termes techniques.
- Fournissez un contexte sur l’objectif du formulaire et l’audience cible
- Inclure les exigences de validation et de règle métier dans les invites initiales

### Stratégie de développement incrémentiel

**Démarrage simple, complexité de création**

- Commencez par la structure de formulaire de base et les champs essentiels.
- Ajouter des règles de validation et une logique métier de manière incrémentielle
- Testez chaque ajout avant de passer à l’amélioration suivante
- Collectez les commentaires des utilisateurs et utilisatrices à chaque étape du développement.

**Exemple d’approche incrémentielle :**

    Étape 1 : « Créer un formulaire de contact de base avec le nom, l’adresse e-mail et les champs de message »
    Étape 2 : « Rendre les champs @name et @email obligatoires avec la validation appropriée »
    Étape 3 : « Ajouter un texte d’espace réservé et un texte d’aide pour aider l’utilisateur »
    Étape 4 : « Ajouter une logique conditionnelle basée sur le type de requête »

### Bonnes pratiques relatives aux références de champ

**Conventions de dénomination cohérentes**

- Utilisez des noms de champ clairs et descriptifs qui correspondent à leur objectif.
- Conserver des modèles de dénomination cohérents dans les formulaires
- Utilisez camelCase ou snake_case de manière cohérente dans tous vos formulaires
- Conventions de dénomination des champs de document pour la cohérence de l’équipe

**Références de champ effectives**

- Utiliser la syntaxe `@fieldName` lors de la modification de champs existants
- Précisez à quels champs vous faites référence dans les formulaires complexes
- Regrouper les modifications de champs associées dans des requêtes uniques
- Vérifier les noms de champ avant de les utiliser dans une logique conditionnelle

## Bonnes pratiques d’intégration et d’envoi

### Stratégie de soumission multicanal

**Actions Principal et Secondaires**

- Configuration des points d’entrée d’envoi principaux pour les processus métier principaux
- Configurer des actions secondaires pour les notifications, les confirmations et la sauvegarde des données
- Implémenter la logique de gestion des erreurs et de reprise pour les envois ayant échoué
- Fournir des commentaires à l’utilisateur pour tous les états d’envoi (succès, échec, traitement)

**Planification de l’intégration**

- Commencez par la configuration d’envoi de base et ajoutez des intégrations de manière incrémentielle
- Testez chaque intégration séparément avant de combiner plusieurs points d’entrée
- Exigences en matière d’API de document et méthodes d’authentification
- Planifier les exigences de transformation et de mappage des données

### Gestion des erreurs et récupération

**Messages d’erreur conviviaux**

- Fournir des messages d’erreur clairs et exploitables qui aident les utilisateurs à résoudre des problèmes
- Évitez les codes d’erreur techniques ou les messages système dans le contenu destiné à l’utilisateur
- Proposer d’autres actions en cas d’échec de l’envoi principal
- Incluez les coordonnées des utilisateurs qui ont besoin d’aide supplémentaire

**Protection et récupération des données**

- Implémenter la sauvegarde des données locales pour la récupération du formulaire après une erreur
- Fournir des options aux utilisateurs pour télécharger leurs données de formulaire en tant que sauvegarde
- Configurer la surveillance et les alertes pour les échecs d’envoi
- Planifier les procédures de récupération en cas de panne du système ou de maintenance

## Bonnes pratiques relatives aux performances et à l’analyse

### Surveillance et optimisation

**Mesures de performances clés**

- Suivre les taux d’achèvement des formulaires et les points d’abandon
- Surveillance des temps de chargement et des schémas d’interaction des utilisateurs
- Mesurer l’efficacité de la validation et les taux d’erreur
- Analysez les commentaires des utilisateurs et utilisatrices et les scores de satisfaction.

**Amélioration continue**

- Révision régulière des analyses de formulaires pour identifier les opportunités d’optimisation
- Tests A/B de différentes conceptions de formulaire et de différents flux d’utilisateurs
- Collecte et analyse des commentaires des utilisateurs pour des améliorations itératives
- Analyse comparative des performances par rapport aux normes du secteur

### Qualité et validation des données

**Stratégies de validation intelligentes**

- Implémenter la validation en temps réel pour les commentaires immédiats des utilisateurs et utilisatrices
- Utiliser la validation progressive pour guider les utilisateurs et utilisatrices à travers des exigences complexes
- Fournir des messages de validation clairs qui expliquent comment corriger les erreurs
- Équilibrez la rigueur de la validation avec les considérations relatives à l’expérience utilisateur.

**Intégrité des données**

- Implémenter la validation entre champs pour la cohérence des données
- Utilisez des types d’entrée et des contraintes appropriés pour empêcher les données non valides
- Fournir des exemples de format de données et des conseils pour les champs complexes
- Audit régulier de la qualité des données soumises et de l’efficacité de la validation

## Bonnes pratiques en matière de sécurité et de conformité

### Protection des données

**Confidentialité par conception**

- Collectez uniquement les données minimales nécessaires à l’objectif de votre entreprise
- Implémenter des politiques de conservation et de suppression des données appropriées
- Fournir des avis de confidentialité et des mécanismes de consentement clairs
- Garantir la conformité aux réglementations relatives à la protection des données (RGPD, CCPA, etc.)

**Implémentation de la sécurité**

- Utiliser le chiffrement HTTPS pour tous les envois de formulaires et la transmission de données
- Implémenter une validation et une désinfection des entrées appropriées
- Configurez un chargement de fichier sécurisé avec les restrictions et l&#39;analyse de virus appropriées
- Audits de sécurité réguliers et évaluations des vulnérabilités

### Considérations relatives à la conformité

**Exigences réglementaires**

- Comprendre et mettre en œuvre les exigences de conformité spécifiques au secteur
- Documenter les mesures de conformité à des fins d&#39;audit
- Examen régulier des modifications réglementaires et de leur impact sur les formulaires
- Formation du personnel sur les exigences de conformité et la mise en œuvre

**Conformité à l’accessibilité**

- Suivez les directives d’accessibilité de WCAG 2.1 AA
- Tests d’accessibilité réguliers avec les technologies d’assistance
- Test des utilisateurs auprès de personnes en situation de handicap
- Documentation des fonctionnalités d’accessibilité et des mesures de conformité

## Bonnes pratiques relatives à Team Collaboration

### Documentation et partage des connaissances

**Documentation du formulaire**

- Conservez une documentation claire sur les objectifs, les exigences et les règles métier des formulaires
- Points d’entrée de l’intégration des documents, flux de données et dépendances
- Conserver l’historique des versions et les journaux des modifications pour les mises à jour de formulaire
- Partager les bonnes pratiques et les leçons apprises entre les équipes

**Formation et adoption**

- Fournir une formation aux membres de l’équipe sur les fonctionnalités de Forms Experience Builder
- Établissez des directives pour la création cohérente de formulaires dans l’ensemble de l’organisation
- Sessions régulières de partage des connaissances sur les nouvelles fonctionnalités et les bonnes pratiques
- Programmes de tutorat pour les nouveaux utilisateurs de la plateforme

### Assurance qualité

**Processus de révision**

- Mettre en œuvre des processus d’examen par les pairs pour la conception et la mise en œuvre des formulaires
- Établir des protocoles de test pour les fonctionnalités de formulaire et l’expérience utilisateur
- Audits réguliers des formulaires existants pour les opportunités d’optimisation
- Collecte de commentaires des utilisateurs internes et des utilisateurs finaux

**Normes et lignes directrices**

- Développer des normes organisationnelles pour la conception et la mise en œuvre des formulaires
- Création de modèles et d’instructions pour les types de formulaires courants
- Définir des processus d’approbation pour les nouveaux formulaires et les modifications majeures
- Examen et mise à jour réguliers des normes organisationnelles

## Bonnes pratiques avancées

### Champs intelligents améliorés par LLM

**Exploiter les connaissances en IA**

- Utiliser les connaissances intégrées de l’IA pour obtenir des options de champ complètes
- Demandez des champs intelligents pour les données géographiques, les classifications professionnelles et les normes du secteur
- Implémenter une population de champs intelligente pour une meilleure expérience utilisateur
- Tester la précision et l’exhaustivité des champs intelligents pour vos cas d’utilisation spécifiques

**Exemples de champs intelligents**

    « Ajouter un champ pour l&#39;aéroport de départ avec tous les principaux aéroports du monde entier, y compris les codes IATA »
    « Créer un champ industriel complet à l&#39;aide de la classification SCIAN standard »
    « Inclure un menu déroulant de certification professionnelle qui s&#39;adapte en fonction du champ d&#39;emploi »

### Logique de formulaire avancée

**Règles métier complexes**

- Décomposer une logique commerciale complexe en composants plus petits et testables
- Documentez clairement les exigences des règles métier avant l’implémentation.
- Tester minutieusement les cas Edge et les scénarios d’exception
- Fournir des commentaires utilisateur clairs en cas de violation de règles métier

**Comportement de formulaire dynamique**

- Utilisation de la divulgation progressive pour afficher les champs pertinents en fonction des entrées de l’utilisateur
- Implémenter des paramètres par défaut intelligents qui peuvent être remplacés par les utilisateurs
- Créer des formulaires adaptatifs qui s’ajustent en fonction du comportement et des préférences des utilisateurs et utilisatrices
- Équilibrez l’automatisation avec le contrôle et la transparence des utilisateurs

## Validation et tests

### Stratégie de test complète

**Test multiniveau**

- Test unitaire pour des composants de formulaire individuels et des règles de validation
- Tests d’intégration pour les points d’entrée d’envoi et les flux de données
- Test d’acceptation des utilisateurs avec des groupes d’utilisateurs représentatifs
- Test de performance sous différentes conditions de charge

**Validation sur plusieurs plateformes**

- Tester des formulaires dans différents navigateurs et versions
- Validation de l’expérience mobile sur différents appareils et tailles d’écran
- Tests d’accessibilité avec différentes technologies d’assistance
- Test de l’état du réseau pour différentes vitesses de connexion

### Mesures de qualité

**Indicateurs de succès**

- Taux de remplissage des formulaires supérieurs aux références du secteur
- Faibles taux d’erreur et scores de satisfaction client élevés
- Temps de chargement rapides et interactions utilisateur réactives
- Intégration réussie avec les systèmes et processus principaux

**Surveillance continue**

- Examen régulier des mesures de performances des formulaires et des commentaires des utilisateurs et utilisatrices
- Identification proactive et résolution des problèmes
- Analyse des tendances pour l’utilisation et l’efficacité des formulaires
- Analyse comparative par rapport aux normes et aux bonnes pratiques du secteur

Pour obtenir des conseils supplémentaires et des exemples détaillés, consultez le [Guide de prise en main de Forms Experience Builder](forms-ai-assistant-getting-started.md) et la [Bibliothèque d’invites de Forms Experience Builder](ai-assistant-prompt-library.md).
