---
title: Prise en main de Forms Experience Builder
description: Découvrez les bases de la création de votre premier formulaire optimisé par l’IA avec Forms Experience Builder. Tutoriel détaillé avec des exemples et des bonnes pratiques.
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: de524aeddd5f53cbd713ff0523222966752ebbc0
workflow-type: tm+mt
source-wordcount: '1133'
ht-degree: 0%

---


# Prise en main de Forms Experience Builder {#getting-started-forms-experience-builder}

Forms Experience Builder révolutionne la création de formulaires en utilisant l’IA pour transformer les descriptions en langage naturel en formulaires numériques entièrement fonctionnels. Ce guide vous aidera à créer votre premier formulaire et à comprendre les concepts de base qui rendent Forms Experience Builder puissant.

## Qu’est-ce que Forms Experience Builder ? {#what-is-forms-experience-builder}

Forms Experience Builder est un outil de création de formulaires optimisé par l’IA qui vous permet de créer des formulaires numériques sophistiqués à l’aide d’un langage de conversation. Au lieu des interfaces traditionnelles par glisser-déposer ou d’un codage complexe, vous décrivez simplement ce que vous souhaitez, et l’IA crée le formulaire pour vous.

**Fonctionnalités principales :**

* **Création de formulaires en langage naturel** - Décrivez vos exigences en matière de formulaires en langage clair

* **Import et conversion intelligents** - Transformer des documents existants en formulaires interactifs

* **Génération de champs intelligents** - Champs optimisés par l’IA avec des options préremplies

* **Automatisation de la logique commerciale** - Créez des règles conditionnelles et une validation par la conversation

* **Intégration système** - Connectez les formulaires à vos workflows d’entreprise existants.

## Conditions préalables {#prerequisites-getting-started}

Avant de commencer, vérifiez que vous disposez des éléments suivants :

* **Accès à Forms Experience Builder** - Disponible via le programme d’accès anticipé
* **AEM Forms as a Cloud Service** - Environnement de création de production avec composants principaux de Forms adaptatif
* **Compréhension de base** - Familiarité avec les concepts de formulaire et les exigences commerciales

Pour connaître les exigences techniques détaillées en matière de configuration et la configuration de l’environnement, voir [Déployer et configurer Forms Experience Builder](deploy-forms-experience-builder.md).

## Méthodes de création de formulaires {#two-ways-to-create-forms}

Après avoir utilisé l’assistant Forms pour sélectionner un modèle [Composants principaux](/help/forms/creating-adaptive-form-core-components.md) ou un modèle [Edge Delivery Services](/help/edge/docs/forms/universal-editor/create-forms.md), un thème et d’autres options, le Forms Experience Builder propose deux approches principales pour la création de formulaires :

### &#x200B;1. Créer à partir de zéro {#create-from-scratch}

Créer des formulaires à l’aide de descriptions en langage naturel de vos besoins

**Utilisation :**

* Création de formulaires à partir d’exigences

* Créer des formulaires pour de nouveaux processus d’entreprise

* Lorsque vous disposez de spécifications claires mais pas de documents existants

**Exemple :**

    Créer un formulaire de commentaires client avec :
    &#x200B;- Évaluation du produit (1 à 5 étoiles)
    &#x200B;- Champ de commentaire pour des commentaires détaillés
    &#x200B;- E-mail du client (facultatif)
    &#x200B;- Envoyer à une notification par e-mail

>[!VIDEO](https://video.tv.adobe.com/v/3473104)



### &#x200B;2. Importer et convertir {#import-and-convert}

Transformer des documents existants en formulaires numériques interactifs.

Avant d’utiliser cette option, chargez votre fichier PDF ou une image du formulaire. Le PDF peut être un formulaire AcroForm ou un formulaire PDF basé sur XFA. Pour [autres types de PDF forms](https://experienceleague.adobe.com/en/docs/experience-manager-learn/forms/document-services/pdf-forms-and-documents), utilisez l’option [Préparer le formulaire](https://helpx.adobe.com/in/acrobat/using/creating-distributing-pdf-forms.html) dans Adobe Acrobat pour les convertir en formulaire Acro

**Utilisation :**

* Conversion d’un PDF forms existant

* Modernisation des processus papier

* Lorsque vous disposez de conceptions de formulaire existantes à améliorer

**Exemple :**

    /create-form convertissez le fichier PDF joint en formulaire adaptatif

>[!VIDEO](https://video.tv.adobe.com/v/3474042)


## Votre premier formulaire : tutoriel détaillé {#first-form-tutorial}

Créons un formulaire de contact simple pour comprendre le workflow de base.

### Étape 1 : Commencez par une description simple {#step-1-simple-description}

Commencez par une description de formulaire de base :

    Créez un formulaire de contact de base avec des champs de nom, d’e-mail et de message

Vous créez ainsi un formulaire contenant trois champs essentiels.

![Formulaire avec trois champs essentiels - créé à l’aide d’une invite en langage naturel](/help/forms/assets/forms-experience-builder-contact-us-form.png)

### Étape 2 : ajouter la validation et les exigences {#step-2-add-validation}

Améliorez le formulaire avec les règles de validation :

    Rendre les champs @name et @email obligatoires avec la validation appropriée

Le symbole `@` fait référence à des champs spécifiques pour les modifications ciblées.

![Ajout de la validation dans le créateur d’expérience de formulaire à l’aide d’une invite en langage naturel](/help/forms/assets/forms-experience-builder-contact-us-form-add-validation.png)


### Étape 3 : améliorer l’expérience utilisateur {#step-3-improve-ux}

Ajoutez du texte d’espace réservé et des conseils utiles :

    Ajoutez le texte de l’espace réservé : @name « Votre nom complet », @email « your.email@company.com » @message « Dites-nous comment nous pouvons vous aider »

![Ajout de la validation à l’aide d’invites en langage naturel dans Forms Experience Builder](/help/forms/assets/forms-experience-builder-contact-us-form-add-placeholder.png)

### Étape 4 : ajout de fonctionnalités avancées {#step-4-advanced-features}

Inclure des fonctionnalités supplémentaires :

    Ajoutez deux listes déroulantes
    
    &#x200B;- queryType avec des options : « Question générale », « Demande d’assistance », « Demande de renseignements sur les ventes », « Partenariat »
    
    &#x200B;- urgenceLevel avec des options (Faible, Medium, Élevé)


![Ajout de composants de liste déroulante à l’aide d’invites en langage naturel dans Forms Experience Builder](/help/forms/assets/forms-experience-builder-contact-us-form-add-dropdown.png)


### Étape 5 : implémenter une logique conditionnelle {#step-5-conditional-logic}

Créez un comportement intelligent et contextuel en ajoutant des règles telles que :

    Masquer la liste déroulante @urgencyLevel lors du chargement du formulaire
    Afficher la liste déroulante @urgencyLevel (Faible, Medium, Élevé) uniquement lorsque la @inquiryType est égale à « Demande d’assistance »

Il s’agit de deux règles distinctes : l’une masque le menu déroulant du niveau d’urgence au chargement du formulaire et l’autre ne l’affiche que lorsque le type de requête est « Demande d’assistance ». Vous devez créer chaque règle avec une invite distincte ; une seule règle peut être créée à la fois.

## Comprendre l’approche de la conversation par l’IA {#ai-conversation-approach}

Forms Experience Builder utilise une interface de conversation où vous pouvez :

### Champs de référence avec symboles @ {#reference-fields}

Utilisez des `@fieldName` pour référencer des champs spécifiques :

    @email un champ obligatoire
    Ajouter une validation à @phoneNumber pour le format US
    Remplacez @submitButton texte par « Envoyer le message »

>[!VIDEO](https://video.tv.adobe.com/v/3474043)


### Utilisation des commandes en langage naturel {#natural-language-commands}

Décrivez ce que vous souhaitez en langage clair :

    &#x200B;- Ajout d’une section pour les informations sur l’entreprise
    &#x200B;- Création d’une liste déroulante pour la sélection d’un service
    &#x200B;- Inclusion d’un chargement de fichier pour la reprise
    &#x200B;- Configuration des notifications par e-mail lors de l’envoi du formulaire

### Création incrémentielle {#build-incrementally}

Commencez simplement et ajoutez progressivement la complexité :

1. **Structure de base** - Commencez par créer les champs essentiels.
2. **Ajouter la validation** - Implémenter les champs obligatoires et la validation du format
3. **Amélioration de l’expérience utilisateur** - Ajout d’espaces réservés, de texte d’aide et de style
4. **Implémenter la logique** - Ajoutez des règles conditionnelles et une logique métier.
5. **Configurer l’envoi** - Configurer le traitement des formulaires et des notifications


## Modèles de formulaire courants {#common-form-patterns}

### Formulaires de contact et de commentaires {#contact-feedback-forms}

**Formulaire de contact de base :**

    Créer un formulaire de contact avec :
    &#x200B;- Nom (obligatoire)
    &#x200B;- E-mail (obligatoire, validé)
    &#x200B;- Liste déroulante Objet (Général, Support, Ventes, Partenariat)
    &#x200B;- Message (obligatoire, multiligne)
    &#x200B;- Bouton Envoyer

**Formulaire de commentaires client :**

    Créer un formulaire de commentaires client avec :
    &#x200B;- Évaluation du produit (1 à 5 étoiles)
    &#x200B;- Champ de commentaire pour des commentaires détaillés
    &#x200B;- E-mail du client (facultatif)
    &#x200B;- Envoyer à une notification par e-mail

### Formulaires d’inscription et d’intégration {#registration-onboarding-forms}

**Enregistrement des utilisateurs :**

    Créer un formulaire d’enregistrement d’utilisateur avec :
    &#x200B;- Informations personnelles (nom, e-mail, téléphone)
    &#x200B;- Préférences du compte (newsletter, notifications)
    &#x200B;- Acceptation des conditions générales
    &#x200B;- Création d’un mot de passe avec validation du niveau de sécurité

**Intégration des employés :**

    Créez un formulaire d’intégration d’employé avec :
    &#x200B;- Informations personnelles et coordonnées
    &#x200B;- Informations sur l’emploi et date de début
    &#x200B;- Chargements de documents (CV, ID, formulaires fiscaux)
    &#x200B;- Sélection des avantages et préférences

### Formulaires d&#39;enquête et d&#39;évaluation {#survey-assessment-forms}

**Enquête de satisfaction client :**

    Créer une enquête de satisfaction client avec :
    &#x200B;- Note globale (échelle 1-10)
    &#x200B;- Notes par catégorie (produit, service, support)
    &#x200B;- Sections de commentaires ouvertes
    &#x200B;- Informations démographiques (facultatif)

**Évaluation des compétences :**

    Créer un formulaire d’évaluation des compétences avec :
    &#x200B;- Catégories de compétences avec niveaux de compétence
    &#x200B;- Durée de l’expérience pour chaque compétence
    &#x200B;- Informations sur la certification et la formation
    &#x200B;- Auto-évaluation et objectifs

## Tests et validation {#testing-validation}

### Toujours tester vos formulaires {#always-test-forms}

Avant de déployer un formulaire :

1. **Tester tous les champs** - Assurez-vous que la validation fonctionne correctement

2. **Vérifier la logique conditionnelle** - Vérifier que les règles se déclenchent correctement

3. **Test de l’envoi** - Confirmez que les données sont traitées correctement

4. **Valider sur différents appareils** - Garantir la compatibilité mobile

5. **Consulter avec les parties prenantes** - Obtenir les commentaires des utilisateurs finaux

### Modèles de validation courants {#validation-patterns}

**Validation des e-mails :**

    Ajouter la validation du format d’e-mail à @email champ

**Validation des numéros de téléphone :**

    Ajouter la validation du format du numéro de téléphone américain à @phoneNumber

**Validation de l’âge :**

    Ajouter une validation d’âge : doit avoir 18 ans ou plus pour @dateOfBirth

**Validation du chargement de fichier :**

    Validation du type de fichier d’ajout : PDF, DOC, DOCX uniquement autorisés pour @resume
    Limite de taille de fichier d’ajout : 5 Mo maximum pour les @resume

## Étapes suivantes {#next-steps}

Maintenant que vous comprenez les principes de base, explorez ces rubriques avancées :

* **[Champs intelligents améliorés par LLM](forms-experience-builder-llm-smart-fields.md)** - Créez des champs avec des options préremplies à l’aide des connaissances de l’IA
* **[Création de formulaires optimisés par l’IA](forms-experience-builder-prompt-examples-library.md)** - Modèles et exemples d’invites avancés
* **[Import et conversion intelligents](intelligent-import-conversion.md)** - Transformer des documents existants en formulaires
* **[Envoi et intégration de formulaires](form-submission-integration.md)** - Connectez les formulaires à vos systèmes d’entreprise


## Articles connexes

* [Présentation de Forms Experience Builder](product-overview.md)
* [Champs intelligents améliorés par LLM](forms-experience-builder-llm-smart-fields.md)
* [Création de formulaires optimisée par l’IA](forms-experience-builder-prompt-examples-library.md)
* [Import et conversion intelligents](intelligent-import-conversion.md)
* [Envoi et intégration du formulaire](form-submission-integration.md)
* [Questions fréquentes](forms-experience-builder-frequently-asked-questions.md)
