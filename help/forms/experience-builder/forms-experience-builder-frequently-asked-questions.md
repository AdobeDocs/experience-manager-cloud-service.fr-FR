---
title: Forms Experience Builder - Questions fréquentes
description: Trouvez des réponses aux questions courantes sur Forms Experience Builder, y compris sur la configuration, l’utilisation, le dépannage et les bonnes pratiques.
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: de524aeddd5f53cbd713ff0523222966752ebbc0
workflow-type: tm+mt
source-wordcount: '1060'
ht-degree: 1%

---


# Forms Experience Builder - Questions fréquentes

>[!NOTE]
>
> Forms Experience Builder est disponible dans le cadre d’un programme d’accès anticipé. Avant de commencer, vérifiez que vous avez demandé et obtenu l’accès.

Cette FAQ répond aux questions les plus courantes à propos de Forms Experience Builder, de la configuration de base aux fonctionnalités avancées et au dépannage.

## Questions générales

### Qu’est-ce que Forms Experience Builder ?

Forms Experience Builder est un outil de création de formulaires optimisé par l’IA qui vous permet de créer des formulaires numériques sophistiqués à l’aide d’un langage de conversation. Au lieu des interfaces traditionnelles par glisser-déposer ou d’un codage complexe, vous décrivez simplement ce que vous souhaitez, et l’IA crée le formulaire pour vous.

### Qui peut utiliser Forms Experience Builder ?

Forms Experience Builder est conçu pour :

- **Créateurs et créatrices de formulaires** qui souhaitent créer des formulaires rapidement et efficacement
- **Utilisateurs professionnels** qui doivent créer des formulaires sans expertise technique
- **Développeurs** qui souhaitent utiliser l’IA pour le prototypage de formulaire rapide
- **Administrateurs** qui doivent configurer et gérer les workflows de création de formulaires

### Forms Experience Builder est-il disponible pour tous les clients AEM Forms ?

Forms Experience Builder est actuellement disponible via un programme d’accès anticipé. Contactez votre représentant Adobe pour demander l’accès et en savoir plus sur la disponibilité pour votre organisation.

## Installation et configuration

### Quelles sont les conditions préalables à l’utilisation de Forms Experience Builder ?

Avant d’utiliser Forms Experience Builder, vérifiez que vous disposez des éléments suivants :

- Accès à Forms Experience Builder via le programme d’accès anticipé
- AEM Forms as a Cloud Service avec composants principaux de Forms adaptatif
- Compréhension de base des concepts de formulaire et des exigences commerciales

Pour connaître les exigences techniques de configuration détaillées, voir [Déploiement et configuration de Forms Experience Builder](deploy-forms-experience-builder.md).

### Comment activer Forms Experience Builder dans mon environnement ?

La configuration de Forms Experience Builder dépend de votre mise en œuvre d’AEM Forms :

**Pour Edge Delivery Services :**

- Préparation de votre projet pour Edge Delivery Services Forms
- Activation de Forms Experience Builder dans l’éditeur universel

**Pour les formulaires basés sur les composants principaux :**

- Assurez-vous que les composants principaux de Forms adaptatif sont activés
- Configuration du Forms Experience Builder dans l’éditeur de Forms adaptatif

### Puis-je utiliser Forms Experience Builder avec des formulaires existants ?

Oui, Forms Experience Builder peut utiliser des formulaires existants de plusieurs manières :

- Importer et convertir un PDF forms existant
- Améliorer les formulaires adaptatifs existants à l’aide de fonctionnalités optimisées par l’IA
- Ajouter des champs intelligents aux structures de formulaires actuelles

## Création de formulaires

### Comment créer mon premier formulaire ?

Commencez par une description simple de ce que vous souhaitez :

    Créez un formulaire de contact avec des champs de nom, d’e-mail et de message

L’IA génère la structure de formulaire de base, que vous pouvez ensuite améliorer avec des fonctionnalités supplémentaires, la validation et le style.

### Quels types de formulaires puis-je créer ?

Forms Experience Builder prend en charge différents types de formulaires :

- Formulaires de contact et de commentaires
- Formulaires d’inscription et d’intégration
- Formulaires d&#39;enquête et d&#39;évaluation
- Formulaires à plusieurs étapes avec logique conditionnelle
- Forms avec chargements de fichiers et validation complexe

### Puis-je créer des formulaires à plusieurs étapes ?

Oui, vous pouvez créer des formulaires à plusieurs étapes à l’aide du langage naturel :

    Créez un formulaire progressif en 3 étapes : informations personnelles, préférences, confirmation

L’IA configure automatiquement la structure du formulaire avec une navigation entre les étapes.

### Comment ajouter une validation aux champs de formulaire ?

Ajoutez la validation à l’aide des commandes de langage naturel :

    @email un champ obligatoire avec validation du format des e-mails
    Ajoutez la validation du format des numéros de téléphone aux États-Unis à @phoneNumber
    Définissez la validation de l’âge : doit être âgé de 18 ans ou plus pour la @dateOfBirth

## Fonctionnalités avancées

### Que sont les champs intelligents optimisés par LLM ?

Les champs intelligents optimisés pour LLM sont des champs de formulaire intelligents préremplis avec des options pertinentes provenant de bases de connaissances d’IA. Par exemple :

- Listes déroulantes par pays avec tous les pays du monde
- Classifications de secteur avec des codes standard
- Données géographiques avec les états, villes et codes postaux

### Comment importer des documents existants dans des formulaires ?

Vous pouvez importer différents types de documents :

- **PDF forms** : chargement de PDF statiques ou interactifs
- **Images** : téléchargez des photos de formulaires papier ou des captures d’écran
- **Fichiers de conception** : importez des conceptions Figma ou d’autres formats de conception.

Utilisez l’icône de pièce jointe dans Forms Experience Builder pour charger votre document et décrire vos exigences de conversion.

### Puis-je intégrer des formulaires à des systèmes externes ?

Oui, Forms Experience Builder prend en charge diverses options d’intégration :

- Envois d’e-mails avec des modèles personnalisés
- Intégration de l’API REST avec des services externes
- Intégration du stockage dans le cloud (Azure, AWS, Google Cloud)
- Intégration des workflows (Power Automate, workflow AEM)

## Résolution des problèmes

### L’IA ne comprend pas ma demande. Que dois-je faire ?

Essayez les approches suivantes :

- Soyez plus précis dans votre description
- Décomposer les requêtes complexes en étapes plus petites
- Utiliser des références de champs (@fieldName) pour les modifications ciblées
- Fournissez des exemples clairs de ce que vous souhaitez

### La validation de mon formulaire ne fonctionne pas. Comment puis-je le réparer ?

Vérifiez ces problèmes courants :

- Vérifiez que les noms des champs correspondent exactement (sensible à la casse).
- Assurez-vous que la syntaxe de validation est correcte
- Test individuel des règles de validation
- Vérifier les messages d’erreur pour des problèmes spécifiques

### La logique conditionnelle ne se déclenche pas correctement. Qu&#39;est-ce qui ne va pas ?

Dépannage de la logique conditionnelle en :

- S’assurer que les noms de champ sont correctement référencés
- Vérification de la syntaxe et des conditions des règles
- Test avec différentes combinaisons d’entrée
- Vérification de la correspondance entre les types de champs et les exigences des règles

### L’interface ne se charge pas. Que dois-je faire ?

Essayez les solutions suivantes :

- Actualisez votre navigateur et effacez le cache
- Vérifier votre connexion Internet
- Vérifier que vous disposez des autorisations d’accès appropriées
- Contactez votre administrateur système si les problèmes persistent

## Bonnes pratiques

### Comment créer de meilleurs formulaires avec Forms Experience Builder ?

Suivez ces bonnes pratiques :

- **Soyez précis** : fournissez des descriptions détaillées de ce que vous souhaitez
- **Démarrer simple** : commencez par une structure de base et ajoutez progressivement la complexité.
- **Test approfondi** : valider toutes les fonctionnalités de formulaire avant le déploiement
- **Utiliser le développement incrémentiel** : créez des formulaires étape par étape

### Que dois-je éviter lors de la création de formulaires ?

Évitez les erreurs courantes suivantes :

- Être trop vague dans vos descriptions
- Essayer de tout créer en même temps
- Ignorer les tests et la validation
- Ne pas tenir compte de la réactivité mobile

### Comment puis-je m’assurer que mes formulaires sont accessibles ?

Forms Experience Builder comprend des fonctionnalités d’accessibilité :

- Vérification automatique de la conformité WCAG
- Compatibilité des lecteurs d’écran
- Prise en charge de la navigation au clavier
- Options du mode Contraste élevé

## Intégration et déploiement

### Comment déployer les formulaires créés avec Forms Experience Builder ?

Les Forms créées avec Forms Experience Builder suivent les processus de déploiement AEM Forms standard :

- Publication de formulaires dans l’environnement de création AEM
- Configuration des points d’entrée d’envoi de formulaire
- Configurer des workflows de traitement de formulaire
- Tester les formulaires dans l’environnement de production

### Puis-je personnaliser les réponses et le comportement de l’IA ?

Oui, vous pouvez configurer différents aspects :

- Style de réponse (concis, détaillé, équilibré)
- Préférences linguistiques et terminologie
- Options de personnalisation de l’interface
- Paramètres d’accessibilité

### Comment puis-je obtenir de l’aide sur Forms Experience Builder ?

Pour une prise en charge supplémentaire :

- Consultez le [ Guide de prise en main ](forms-experience-builder-getting-started.md)
- Consultez le [guide de déploiement et de configuration](deploy-forms-experience-builder.md)
- Contactez votre administrateur système
- Contactez l’assistance Adobe pour les problèmes techniques

## Articles connexes

- [Présentation de Forms Experience Builder](product-overview.md)
- [Prise en main de Forms Experience Builder](forms-experience-builder-getting-started.md)
- [Déploiement et configuration de Forms Experience Builder](deploy-forms-experience-builder.md)
- [Champs intelligents améliorés par LLM](forms-experience-builder-llm-smart-fields.md)
- [Import et conversion intelligents](intelligent-import-conversion.md)
- [Envoi et intégration du formulaire](form-submission-integration.md)
