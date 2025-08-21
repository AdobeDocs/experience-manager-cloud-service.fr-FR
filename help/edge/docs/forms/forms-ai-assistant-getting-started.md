---
title: Prise en main de Forms Experience Builder
description: Découvrez comment utiliser Forms Experience Builder pour créer et gérer des formulaires avec divulgation progressive pour tous les types d’utilisateurs
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: b8f64082-a23f-4919-ad66-042faad77d30
source-git-commit: 750674bbd29ec1b29388579d77c7c15bd89335ab
workflow-type: tm+mt
source-wordcount: '1720'
ht-degree: 15%

---


# Prise en main de Forms Experience Builder

>[!NOTE]
>
> La fonctionnalité Forms Experience Builder est disponible dans le cadre du **programme destiné aux utilisateurs et utilisatrices précoces**. Si vous êtes intéressé, envoyez un e-mail rapide à partir de votre adresse professionnelle à `aem-forms-ea@adobe.com` pour demander l’accès à la fonctionnalité.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette documentation est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les fonctionnalités, commandes et exemples peuvent changer à mesure que le Forms Experience Builder continue d’évoluer au cours du programme destiné aux utilisateurs et utilisatrices précoces.

Ce guide complet vous aide à commencer à créer et gérer des formulaires à l’aide de la technologie d’IA conversationnelle. Que vous soyez un débutant à la recherche de la création de votre premier formulaire ou un utilisateur expérimenté cherchant à tirer parti de fonctionnalités sophistiquées, vous trouverez des informations détaillées et des exemples pratiques pour guider votre parcours à travers les fonctionnalités du Forms Experience Builder.

## Conditions préalables et configuration

### &#x200B;1. Demander l’accès

Si vous n’avez pas accès à Forms Experience Builder :

1. **Demander l&#39;accès** : envoyez un e-mail à [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) à partir de votre e-mail professionnel.
2. **Inclure les informations** : nom de l’organisation et détails du projet
3. **En attente d’approbation** : Adobe examinera et fournira des instructions d’intégration.

### &#x200B;2. Vérifiez que Forms est activé

Avant d’utiliser Forms Experience Builder, vérifiez qu’[AEM Forms est activé pour votre environnement](/help/forms/setup-forms-cloud-service.md).


### &#x200B;3. Configuration De Votre Environnement


* **Pour Edge Delivery Services (EDS) :**

   * [Configuration de l’environnement pour Edge Delivery Services Forms](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)
   * [Création d’un formulaire à partir du modèle Edge Delivery Forms](/help/edge/docs/forms/universal-editor/create-forms.md)

* **Pour les formulaires basés sur les composants principaux :**

   * Sur votre instance Adobe Experience Manager, accédez à Forms > Forms et documents
   * [Créer une page à l’aide du modèle de composants principaux](/help/forms/creating-adaptive-form-core-components.md)

## Démarrage rapide

### Accès au Forms Experience Builder

**Éditeur universel**

* Ouvrez votre page EDS dans l’éditeur universel.
* Recherchez l’icône Forms Experience Builder dans le panneau de gauche
* Cliquer pour ouvrir l’interface de conversation

**Éditeur de formulaires adaptatifs**

* Accédez à : AEM > Forms > Forms et documents .
* Créer ou ouvrir un formulaire basé sur des composants principaux pour le modifier
* Cliquez sur l’icône Forms Experience Builder dans la barre d’outils de l’éditeur

### Votre premier formulaire

Essayez cette conversation simple pour commencer :

```
👤 You: "Create a simple contact form"
🤖 AI: "I'll create a contact form with name, email, and message fields for you."

👤 You: "Make the email field required"
🤖 AI: "Updated the email field to be required with validation."
```

### Commandes Essentielles

| Symbole | Objectif | Utilisation |
|--------|---------|------------|
| `/` | Actions rapides et raccourcis | Saisissez `/create` pour la création de formulaire, `/help` pour obtenir de l’aide |
| `@` | Référencer les champs de formulaire existants | Tapez `@fieldName` pour modifier des champs spécifiques (par exemple, `@email`) |
| Texte brut | Conversation naturelle | Décrivez ce que vous souhaitez : « Ajouter un champ de numéro de téléphone obligatoire » |

### Conseils pour réussir

* **Soyez précis** : « Ajouter un champ d’e-mail obligatoire avec validation » fonctionne mieux que « Ajouter un e-mail »
* **Référencer des champs existants** : utiliser des `@fieldName` lors de la modification de formulaires
* **Demander de l’aide** : saisissez `/help` suivi de votre question
* **Itérer** : effectuez une modification à la fois pour obtenir de meilleurs résultats

## Fonctionnalités principales

### Création de Forms de deux façons

#### &#x200B;1. Créer à partir de zéro

Décrivez les exigences de votre formulaire en langage naturel. Forms Experience Builder génère ensuite la structure complète du formulaire :

**Exemples :**

* « Créez un formulaire de demande de prêt avec des informations personnelles, des détails financiers et des chargements de documents. »
* « Créer un formulaire de commentaires des clients avec des évaluations, des commentaires et des catégories de produits »
* « J&#39;ai besoin d&#39;un formulaire d&#39;inscription en plusieurs étapes pour une conférence avec traitement des paiements »

#### &#x200B;2. Importer et convertir

Transformez les formulaires et documents existants en expériences modernes et interactives :

**Sources prises en charge :**

* **PDF forms** : chargement de PDF statiques → formulaires numériques interactifs avec validation
* **Captures d’écran/Images** : photo de formulaires papier → versions numériques fonctionnelles
* **HTML Forms** : formulaires web de base → AEM Forms amélioré avec des fonctionnalités avancées
* **XFA Forms** : formulaires Adobe hérités → formulaires réactifs modernes
* **URL** : formulaires web existants → AEM Forms natif avec une expérience utilisateur améliorée

**Importer :**

1. Cliquez sur l’icône de pièce jointe dans l’interface de Forms Experience Builder
2. Chargez votre fichier (PDF, image, conception Figma, etc.)
3. Décrivez vos exigences :
   * « Convertir ce formulaire PDF en version numérique »
   * « Créer un formulaire correspondant à cette disposition de capture d’écran »
   * « Crée ce formulaire à partir de mon design Figma. »

**Types de fichiers pris en charge :**

* **Images** (PNG, JPG, GIF) : dispositions de formulaires, maquettes d’interface utilisateur, formulaires numérisés
* **Fichiers PDF** : formulaires, spécifications, documents existants
* **Fichiers Figma** : prototypes de conception, directives de marque
* **Fichiers de conception** : références visuelles, guides de style

### Interactions clés

#### Ajout d’éléments au formulaire

**Ajouts de base :**

```
👤 You: "Add a section for personal information"
🤖 AI: "Added a personal information panel with standard fields"

👤 You: "Include a file upload for resume"
🤖 AI: "Added a secure file upload component for documents"

👤 You: "Add a dropdown for country selection"
🤖 AI: "Added a country dropdown with common options"
```

**Spécifications détaillées :**

```
👤 You: "Add a personal information panel with fields for full name, date of birth, phone number, and email address"
🤖 AI: "Created a personal information panel with all requested fields and appropriate validation"

👤 You: "Include a secure file upload component for documents, limited to PDF files under 5MB"
🤖 AI: "Added a file upload field with PDF restriction and 5MB size limit"

👤 You: "Add a country dropdown with options for USA, Canada, UK, and Germany"
🤖 AI: "Added a country dropdown with the specified options"
```

#### Création d’un comportement dynamique

**Approche simple :**

```
👤 You: "Show additional fields when 'Other' is selected"
🤖 AI: "Created a conditional rule that shows additional fields when 'Other' is chosen"

👤 You: "Make the email field required"
🤖 AI: "Updated the email field to be required with validation"

👤 You: "Calculate the total automatically"
🤖 AI: "Added calculation logic to automatically compute totals"
```

**Règles métier complexes :**

```
👤 You: "Show the spouse information fields only when marital status is set to 'Married'"
🤖 AI: "Created a conditional rule that displays spouse fields based on marital status"

👤 You: "Calculate the total cost by multiplying quantity and price, then add 10% tax"
🤖 AI: "Added calculation logic with quantity, price, and tax computation"

👤 You: "Enable the submit button only when all required fields are completed and terms are accepted"
🤖 AI: "Created validation logic that enables submission only when all conditions are met"
```

#### Mise en page et conception de formulaire

**Modifications de la mise en page :**

```
👤 You: "Make this a multi-step form"
🤖 AI: "Converted the form to a progressive layout with navigation"

👤 You: "Organize fields in two columns"
🤖 AI: "Updated the layout to display fields in a two-column arrangement"

👤 You: "Convert to an accordion layout"
🤖 AI: "Transformed the form to use accordion-style sections"
```

**Améliorations de la conception :**

```
👤 You: "Create a wizard-style form with 3 steps: personal info, preferences, and review"
🤖 AI: "Created a wizard form with three distinct steps and navigation"

👤 You: "Arrange the address fields in a compact two-column layout"
🤖 AI: "Organized address fields in a compact two-column format"

👤 You: "Update the layout to match the attached wireframe"
🤖 AI: "Modified the layout to match the provided design reference"
```

### Configuration de l&#39;intégration

Forms Experience Builder peut configurer différents points d’entrée d’envoi pour connecter vos formulaires à des systèmes et services externes :

| Type d’intégration | Commande d&#39;installation | Cas d’utilisation |
|------------------|---------------|----------|
| **E-mail** | « Envoyer le formulaire à un e-mail » | Notifications et confirmations pour les envois de formulaire |
| **API REST** | « Envoyer vers le point d’entrée REST » | Applications personnalisées et systèmes tiers |
| **Espace de stockage** | « Enregistrer sur Azure/SharePoint » | Stockage de documents et gestion de fichiers |
| **Workflow** | « Se connecter à Power Automate » | Automatisation et approbations des processus métier |
| **Marketing** | « Intégration à Marketo » | Automatisation de la gestion des leads et du marketing |

**Exemples d’intégration avancés :**

```
👤 You: "Send form submissions to hr@company.com and create a case in our CRM system"
🤖 AI: "Configured email submission and CRM integration"

👤 You: "Submit data to our REST API endpoint and trigger the new customer workflow"
🤖 AI: "Set up REST API submission with workflow triggers"

👤 You: "Email responses to the sales team and add the lead to our marketing automation platform"
🤖 AI: "Configured multi-channel submission with email and marketing automation"
```





## Opérations de formulaire avancées


### Création de règles complexes

Créez une validation sophistiquée et une logique commerciale qui répond aux interactions des utilisateurs et assure l’intégrité des données :

```
👤 You: "Show the address section only if the user selects 'Ship to different address'"
🤖 AI: "Created a conditional rule that shows/hides the address panel based on checkbox selection"
```

### Création de formulaire à plusieurs étapes

```
👤 You: "Create a progressive form with 3 steps: personal info, preferences, confirmation"
🤖 AI: "Created a progressive form with navigation between steps and validation at each stage"
```

### Types de champs avancés

* Chargement de fichier avec validation et restrictions de taille pour la gestion des documents
* Sélecteurs de date avec contraintes et règles de gestion pour la planification
* Listes déroulantes avec des options dynamiques qui changent en fonction des sélections de l’utilisateur
* Cases d&#39;option avec logique conditionnelle pour arbres de décision complexes


### Conversion de PDF en formulaire

```
👤 You: "Convert this PDF into an interactive form"
🤖 AI: "Analyzed the PDF and created a form with appropriate field types and validation"
```

### Conversion de l’URL en formulaire

```
👤 You: "Create a form from this website"
🤖 AI: "Extracted form elements and created a native AEM Form with enhanced functionality"
```

### Analyse des performances

```
👤 You: "Analyze this form's conversion performance"
🤖 AI: "Provided insights on form effectiveness and suggested optimizations"
```

### Personnalisation avancée

#### Règles de validation personnalisées

* Dépendances de champs qui créent un comportement de formulaire dynamique en fonction des entrées utilisateur
* Logique conditionnelle complexe qui adapte l’expérience du formulaire aux besoins de l’utilisateur
* Messages d’erreur personnalisés qui fournissent des conseils clairs aux utilisateurs
* Validation entre champs qui garantit la cohérence des données sur plusieurs entrées

#### Optimisation de la disposition

* Réactivité mobile qui garantit le fonctionnement transparent des formulaires sur tous les appareils
* Conformité en matière d’accessibilité qui rend les formulaires utilisables par les personnes en situation de handicap
* Améliorations de la conception visuelle qui améliorent l’interaction client et les taux d’achèvement
* Améliorations de l’expérience utilisateur qui réduisent les frictions et améliorent la satisfaction

#### Workflows d’intégration

* Processus d’approbation en plusieurs étapes qui acheminent les envois de formulaire via les workflows métier
* Transformation de données qui convertit les données de formulaire en formats requis par les systèmes externes
* Logique commerciale personnalisée qui applique des règles et des calculs spécifiques aux envois de formulaires
* Gestion avancée des erreurs permettant une récupération efficace après des problèmes système

## Référence des commandes

### Commandes Essentielles

| Symbole | Objectif | Utilisation |
|--------|---------|------------|
| `/` | Actions rapides et raccourcis | Saisissez `/create` pour la création de formulaire, `/help` pour obtenir de l’aide |
| `@` | Référencer les champs de formulaire existants | Tapez `@fieldName` pour modifier des champs spécifiques (par exemple, `@email`) |
| Texte brut | Conversation naturelle | Décrivez ce que vous souhaitez : « Ajouter un champ de numéro de téléphone obligatoire » |

### Commandes de barre oblique

| Commande | Contexte | Exemple d’utilisation |
|---------|---------|---------------|
| `/create-form` | Tous les environnements | `/create-form customer survey` |
| `/add-form` | Éditeur universel | `/add-form contact form` |
| `/update-layout` | Éditeur de formulaires | `/update-layout wizard with 3 steps` |
| `/update-field` | Éditeur de formulaires | `/update-field @email to be required` |
| `/create-rule` | Éditeur de formulaires | `/create-rule show @spouse if married` |
| `/create-panel` | Éditeur de formulaires | `/create-panel Personal Information` |
| `/configure-submit` | Éditeur de formulaires | `/configure-submit to email support` |
| `/help` | Tous les environnements | `/help multi-step forms` |

### Références de champ

Utilisez `@fieldName` pour référencer les champs existants :

* `@firstName`, `@lastName` * Champs de nom
* `@email`, `@phoneNumber` * Champs de contact
* `@address`, `@city`, `@zipCode` * Champs d’adresse
* `@dateOfBirth`, `@startDate` * Champs de date

### Types de composant

Utilisez les termes suivants pour décrire les éléments de formulaire :

* `text input` * Champ de texte monoligne
* `text area` * Champ de texte multiligne
* `dropdown` * Sélectionner une liste avec des options
* `checkbox` * Case à cocher unique
* `checkbox group` * Cases à cocher multiples
* `radio group` * Groupe de boutons radio
* `date picker` * Champ de sélection de date
* `file upload` * Champ de pièce jointe
* `panel` * Conteneur pour le regroupement des champs

### Commandes d’intégration

| Service | Commande Langage Naturel | Conditions requises |
|---------|--------------------------|--------------|
| E-mail | « Envoyer des envois à [e-mail] » | Adresse e-mail valide |
| API REST | « Envoyer vers le point d’entrée REST [URL] » | Point d’entrée et informations d’identification de l’API |
| Stockage Azure | « Enregistrer des fichiers sur le stockage Azure » | Configuration du compte de stockage |
| SharePoint | « Stocker dans SharePoint [site] » | Accès au site SharePoint |
| Power Automate | « Déclencher le flux Power Automate » | Configuration de flux |
| Marketo | « Ajouter des prospects à Marketo » | Informations d’identification de l’API Marketo |

### Conseils

1. **Utiliser le langage naturel** : l’IA comprend les requêtes complexes et peut interpréter les exigences détaillées
2. **Soyez précis** : les descriptions détaillées donnent de meilleurs résultats et génèrent des formulaires plus précis
3. **Itérer** : affinez les formulaires par la conversation pour obtenir une expérience utilisateur parfaite
4. **Utiliser le contexte** : référencez les éléments de formulaire existants pour tirer parti de ce que vous possédez déjà.
5. **Tester minutieusement** : valider tous les scénarios utilisateur pour s’assurer que les formulaires fonctionnent comme prévu

## Aide sur les produits et apprentissages

Forms Experience Builder peut également vous apprendre à utiliser les fonctionnalités d’AEM Forms :

### Poser des questions du type :

* « Comment créer un formulaire à plusieurs étapes ? »
* « Quelle est la différence entre les panneaux et les sections ? »
* « Comment configurer les notifications par e-mail ? »
* « Quelles sont les bonnes pratiques concernant les formulaires compatibles avec les appareils mobiles ? »
* « Comment appliquer des thèmes à mes formulaires ? »

### Obtenir de l’aide sur :

* Concepts et terminologie d’AEM Forms
* Instructions détaillées relatives aux fonctionnalités complexes
* Bonnes pratiques et recommandations
* Résolution des problèmes courants

## Bonnes pratiques

### Conception de formulaire

* **Restez simple** : commencez par les champs essentiels et ajoutez de la complexité uniquement lorsque cela est nécessaire pour éviter de surcharger les utilisateurs
* **Utiliser des libellés clairs** : rendez les objectifs des champs évidents avec des libellés descriptifs qui guident les utilisateurs et les utilisatrices tout au long du formulaire
* **Fournir un texte d’aide** : guide les utilisateurs à travers des champs complexes avec une aide contextuelle et des exemples
* **Test approfondi** : validez tous les chemins d’accès utilisateur pour vous assurer que les formulaires fonctionnent correctement dans tous les scénarios.

### Expérience utilisateur

* **Divulgation progressive** : afficher les champs pertinents en fonction du contexte pour réduire la charge cognitive et améliorer les taux d’achèvement
* **Navigation claire** : aidez les utilisateurs et les utilisatrices à comprendre où ils se trouvent dans le formulaire et quelles étapes restent
* **Conception réactive** : assurez-vous que les formulaires fonctionnent sur tous les appareils et toutes les tailles d’écran pour une accessibilité maximale
* **Accessibilité** : suivez les directives WCAG pour rendre les formulaires utilisables par les personnes en situation de handicap

### Performance

* **Optimiser le nombre de champs** : demandez uniquement les informations nécessaires pour réduire l’abandon de formulaire et améliorer les taux d’achèvement
* **Utiliser une validation appropriée** : prévenir les erreurs avant l’envoi pour fournir des commentaires et des conseils immédiats
* **Taux d’achèvement des tests** : surveiller et améliorer l’efficacité des formulaires par le biais d’analyses et des commentaires des utilisateurs
* **Mises à jour régulières** : maintenez les formulaires à jour avec les besoins de l’entreprise et les attentes des utilisateurs pour des performances optimales

### Cohérence de la marque

* **Créer des modèles de marque** : préparez les modèles de formulaire de marque avec les couleurs, les polices et le style de votre entreprise avant de commencer la création de formulaire
* **Définir des normes de style** : définissez des styles de bouton, une disposition des champs et des instructions d’espacement cohérents qui peuvent être référencés dans les invites
* **Utiliser des ressources de marque** : préparez les logos, les codes couleur et les directives de la marque pour une référence facile lors de la création de formulaires
* **Bibliothèque de modèles** : créez une collection de modèles de formulaire de marque pour les cas d’utilisation courants (contact, enregistrement, commentaires).
* **Invites de style** : incluez des instructions spécifiques à la marque : « Utiliser le bleu de la société (#1234AB) pour les boutons et les polices d’entreprise Helvetica »

### Conseils pour obtenir de meilleurs résultats

**Démarrer simple, créer**

* Commencer par une demande de base : « Créer un formulaire de contact »
* Ajouter des détails progressivement : « Ajouter la validation au champ d’e-mail »
* Tester et affiner : « Rendre le champ du numéro de téléphone facultatif »

**Soyez Précis Si Nécessaire**

* Au lieu de : « Créer un beau formulaire »
* Essayer : « Utiliser des couleurs professionnelles et une typographie simple »

**Utiliser le langage naturel**

* Au lieu de : « Ajouter un composant de saisie de texte »
* Essayer : « Ajouter un champ pour le prénom »

**Référencer des éléments existants**

* Utiliser `@fieldName` pour les champs existants : « Rendre @email obligatoire »
* Faire preuve de précision concernant les noms de champ : « Mettre à jour le champ @phoneNumber »

**Ventilez Les Requêtes Complexes**

* Au lieu d’une seule longue requête, essayer plusieurs requêtes plus petites
* Créer le formulaire étape par étape
* Tester chaque modification avant de passer à la suivante

## Résolution des problèmes

| Problème | Quick Fix |
|-------|-----------|
| **Interface non chargée** | Actualiser le navigateur, vérifier la connexion Internet |
| **Les commandes ne fonctionnent pas** | `/help` ou utilisez plutôt le langage naturel |
| **@fieldName non reconnu** | Vérifier l’orthographe et s’assurer que le champ existe en premier |
| **Échec du chargement du fichier** | Utilisez PDF/JPG/PNG de moins de 10 Mo. |
| **L’apparence du formulaire est incorrecte** | Soyez plus précis : « Rendez-le compatible avec les appareils mobiles » |
| **Échec de l’intégration** | Vérification des informations d’identification et des autorisations d’API |

**Vous avez encore besoin d&#39;aide ?** Type `/help` suivi de votre question spécifique ou contactez votre administrateur système.

Pour obtenir une assistance supplémentaire, reportez-vous à la [bibliothèque d’invites de Forms Experience Builder principale](ai-assistant-prompt-library.md) ou contactez votre administrateur système pour obtenir de l’aide technique.
