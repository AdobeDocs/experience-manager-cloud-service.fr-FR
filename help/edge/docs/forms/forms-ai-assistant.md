---
title: Assistant AI pour AEM Forms (Forms Experience Builder)
description: Créer des formulaires puissants plus rapidement à l’aide de fragments de formulaire
feature: Edge Delivery Services
hide: true
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: 2db966405b5326d735083a66b2625d6d973ad7db
workflow-type: tm+mt
source-wordcount: '2354'
ht-degree: 2%

---


# Assistant AI pour AEM Forms (Forms Experience Builder)

>[!NOTE]
>
>
> La fonctionnalité Assistant AI pour AEM Forms (Forms Experience Builder) est disponible sous le **programme destiné aux utilisateurs et utilisatrices précoces**. Si vous êtes intéressé, envoyez un e-mail rapide à partir de votre adresse professionnelle à mailto:aem-forms-ea@adobe.com pour demander l’accès à la fonctionnalité.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette documentation est actuellement testée par rapport au produit et est sujette à mises à jour et révisions. Les fonctionnalités, commandes et exemples peuvent changer à mesure que l’assistant AI pour AEM Forms continue d’évoluer au cours du programme destiné aux utilisateurs et utilisatrices précoces.

L’assistant AI pour AEM Forms (Forms Experience Builder) améliore votre expérience de création en rationalisant les tâches courantes de création de formulaires grâce à des invites de langage naturel. Disponible dans l’interface utilisateur de gestion de Forms, l’éditeur de Forms adaptatif et l’éditeur universel, il vous permet de créer plus intelligemment et plus rapidement en prenant en charge les actions de création et de configuration. Ce guide vous aidera à démarrer et à tirer le meilleur parti de ses fonctionnalités.

## Prise en main

Avant d’entrer dans le vif du sujet, découvrez les principes de base de l’accès et de l’interaction avec l’assistant d’IA.

### Accès à l’assistant d’IA

Vous pouvez accéder à l’assistant d’IA à partir de trois emplacements différents dans AEM Forms :

1. **Interface utilisateur de gestion de Forms**
   - Accédez à : Adobe Experience Manager > Forms > Forms et documents .
   - Recherchez l’icône de l’assistant AI sur le côté gauche de l’interface
   - Cliquez sur l’icône pour ouvrir le panneau de l’assistant AI

   ![Icône de l’assistant AI*](/help/edge/docs/forms/assets/forms-manager.gif)

2. **Éditeur de Forms adaptatif**
   - Accédez à : Adobe Experience Manager > Forms > Forms et documents .
   - Sélectionner et ouvrir un formulaire pour le modifier
   - Cliquez sur l’icône de l’assistant AI dans l’interface de l’éditeur

   ![Icône de l’assistant AI*](/help/edge/docs/forms/assets/adaptive-forms-editor.gif)

3. **Éditeur universel**

   - Accédez à : Adobe Experience Manager > Forms > Forms et documents .
   - Recherchez l’icône de l’assistant AI sur le côté gauche de l’interface
   - Cliquez sur l’icône de l’assistant AI dans l’interface de l’éditeur

L’assistant d’IA adapte ses fonctionnalités en fonction de votre emplacement et de votre tâche actuels, fournissant ainsi une assistance pertinente pour chaque contexte.

### Comment interagir :

- Il vous suffit de saisir votre demande en langage naturel.
- Utilisez `/` pour afficher la liste des commandes ou actions rapides disponibles.
- Référencez des champs de formulaire spécifiques à l’aide de `@fieldName` (par exemple, `@firstName`, `@emailAddress`) lorsque vous souhaitez que l’assistant configure ou mette à jour ce champ particulier.
- Vous pouvez charger des images, des PDF, des fichiers de format graphique ou d’autres ressources de conception pour aider l’assistant d’IA à mieux comprendre vos besoins.


### Démarrage rapide

Lancez-vous rapidement en regardant notre vidéo d’introduction :

>[!VIDEO](https://video.tv.adobe.com/v/3463164/)


Cette vidéo présente le lancement de l’assistant dans tous les environnements, une interaction de base et un aperçu de ses fonctionnalités.

## Référence des commandes de l’assistant AI

| Commande | Description | Objectif | Contexte d’utilisation | Exemples | Fonctions clés |
|---------|-------------|---------|---------------|----------|--------------|
| /create-form | Démarrer un nouveau formulaire dans l’interface utilisateur de gestion de Forms ou dans l’éditeur Forms | Lance la création d’un formulaire entièrement nouveau à partir de zéro. | Interface utilisateur de gestion de Forms, éditeur de Forms adaptatif | /create-form enquête sur les commentaires des clients basée sur PDF joint | Fournit des options pour la structure des formulaires et crée le formulaire. **Prend en charge les pièces jointes** pour les références de conception |
| /add-form | Ajouter un nouveau formulaire dans l’éditeur universel | Ajoute un nouveau bloc de formulaire ou composant dans l’éditeur universel | Éditeur universel pour Edge Delivery Services | Formulaire de contact /add-form avec nom et adresse électronique | Insère des blocs de formulaire, fonctionne avec la modification par blocs. **Prend en charge les pièces jointes** pour des conseils de mise en page |
| /update-layout | Remplacez la disposition du formulaire par un accordéon, un onglet, un assistant ou une conception réactive à une seule page. | Modifie la disposition structurelle globale et le modèle de navigation | Tous les environnements d’édition | Assistant /update-layout en 3 étapes | Accordéon, onglets, assistant, options réactives sur une seule page |
| /update-field | Modifier les propriétés et la configuration des champs de formulaire existants | Modifie les attributs de champ tels que les libellés, la validation, la mise en forme et le comportement | Tous les environnements d’édition | /update-field @email être obligatoire avec la validation | Libellés, règles de validation, types de champs, valeurs par défaut, visibilité. **Prend en charge les pièces jointes** pour les exemples de conception de champ |
| /create-rule | Créer un comportement dynamique et une logique conditionnelle pour les formulaires | Implémente la logique commerciale, les calculs et les interactions conditionnelles. | Tous les environnements d’édition | /create-rule @spouseName si @maritalStatus est égal à « Marié(e) » | Visibilité conditionnelle, calculs, validation, définition de valeurs |
| /create-panel | Créer un nouveau panneau (conteneur pour regrouper les champs associés) | Ajoute des conteneurs structurels pour organiser logiquement les champs de formulaire | Tous les environnements d’édition | /create-panel Informations personnelles avec nom, adresse e-mail, téléphone | Regroupement de champs, titres, options de disposition, sections réductibles. **Prend en charge les pièces jointes** pour les références de disposition de panneau |
| /add-panel | Conversion d’une image en panneau de formulaire dans l’éditeur universel | Utilise l’IA pour analyser les images chargées et les convertir en panneaux de formulaires structurés | Éditeur universel | /add-panel à partir de l’image de formulaire chargée | Reconnaissance des images, conversion visuelle en fonctionnalité, conservation des mises en page. **Nécessite des pièces jointes** pour l’analyse des images |
| /configure-submit | Configurer les actions d’envoi de formulaire et la gestion des données | Définit ce qui se produit lorsque les utilisateurs envoient le formulaire rempli | Tous les environnements d’édition | /configure-submit pour envoyer un e-mail à `support@company.com` | E-mail, API REST, workflows, feuilles de calcul, bases de données, Power Automate |
| /help | Accéder à l’assistance et à la documentation dans l’assistant d’IA | Aide contextuelle, conseils et réponses sur AEM Forms | Tous les environnements d’édition | /help comment créer des formulaires à plusieurs étapes ? | Explications des fonctionnalités, guides, bonnes pratiques, dépannage |

### Catégories de commande

| Catégorie | Commandes | Cas d’utilisation de Principal |
|----------|----------|-------------------|
| Création du formulaire | /create-form, /add-form | Démarrage de nouveaux formulaires, ajout de blocs de formulaire |
| Structure et disposition | /update-layout, /create-panel, /add-panel | Organisation de la structure des formulaires, conception visuelle |
| Gestion de champ | /update-field | Configuration d’éléments de formulaire individuels |
| Logique et règles | /create-rule | Ajout d’un comportement dynamique et validation |
| Envoi | /configure-submit | Configurer la gestion des données et les workflows |
| Assistance | /help | Obtention d’aide et de documentation |

### Instructions de syntaxe

| Elément | Format | Exemple | Remarques |
|---------|--------|---------|-------|
| Commandes | /command-name | /create-form | Toujours commencer par une barre oblique |
| Références de champ | @fieldName | @email, @firstName | Utiliser le symbole @ pour les champs existants |
| Langage Naturel | Commande + description | /create-rule afficher le champ si la condition | Combiner des commandes avec du texte descriptif |
| Plusieurs actions | Commandes distinctes | /create-panel puis /update-layout | Appliquer une commande à la fois |


### Fonctionnalités spécifiques à un environnement

| Environnement | Commandes disponibles | Particularités |
|-------------|-------------------|------------------|
| Interface utilisateur de gestion de Forms | /create-form, /help | Création et gestion au niveau du formulaire |
| Éditeur de Forms adaptatif et éditeur universel | Toutes les commandes | Ensemble complet de fonctionnalités, configuration détaillée |



### Syntaxe de la référence du champ (éléments contextuels)

Utilisez des `@fieldName` pour référencer les champs existants :

- `@firstName` - Champ Prénom
- `@email` - Champ e-mail
- `@phoneNumber` - Champ Numéro de téléphone
- `@dateOfBirth` - Champ Date de naissance

### Types de composants

Cette liste couvre les types de composants courants. L’IA peut reconnaître des variations ou des types plus spécialisés, mais l’utilisation de ces termes précis donne les meilleurs résultats :

- `text input` - Champ de texte monoligne
- `text area` - Champ de texte multiligne
- `dropdown` - Sélectionner la liste
- `checkbox` - Case à cocher unique
- `checkbox group` - Cases à cocher multiples
- `radio group` - Groupe de boutons radio
- `date picker` - Sélection de la date
- `file upload` - Pièce jointe
- `panel` - Conteneur pour le regroupement des champs


## Fonctionnalités principales et exemples d’invites développés

L’assistant d’IA comprend un large éventail de commandes. Voici quelques exemples pour illustrer sa puissance. N’oubliez pas d’utiliser des termes précis pour des composants tels que « panneau », « saisie de texte », « case à cocher », etc.

| Catégorie de fonctionnalités | Description | Exemples d’invites |
| ------------------------- | --------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Création de formulaire** | Démarrez un nouveau formulaire à partir de zéro ou en fonction d’une description. | `Create a new form titled 'Employee Onboarding'.` <br> `Generate a customer feedback form with fields for name, email, rating (1-5 stars), and comments.` <br> `Start a simple contact form with name, email, and message fields.` <br> `Design a multi-page registration form for an event.` <br> `Create a form based on the attached PDF template.` |
| **Importer la conception** | Convertissez une conception existante (image, Figma, PDF) en un formulaire AEM. | `Import the form design from this uploaded PDF file.` <br> `Convert the uploaded Figma design into an adaptive form, focusing on the 'User Profile' frame.` <br> `Use this JPEG image of our old paper form to create a new digital version.` <br> `Create a form based on the layout of the attached PNG.` <br> `Recreate the form shown in the attached screenshot with modern styling.` |
| **Ajout de composants et de panneaux** | Ajoutez différents champs de formulaire et conteneurs structurels (panneaux). | `Add a text input field for 'First Name'.` <br> `Add a 'Personal Details' panel with fields for full name, date of birth, and phone number.` <br> `Insert a checkbox group for 'Interests' with options: Technology, Sports, Music.` <br> `Add a file upload component for 'Resume'.` <br> `Create a repeatable panel named 'WorkExperience' with fields for company, title, and dates.` <br> `Add a panel matching the layout shown in the attached design mockup.` |
| **Réglages de la disposition** | Modifiez la structure et l’aspect de la disposition de votre formulaire. | `Change the 'Personal Details' panel to a two-column layout.` <br> `Set the overall form layout to a wizard (multi-step) navigation.` <br> `Make the header section span the full width of the form.` <br> `Adjust the spacing between fields in the 'Address' panel to be compact.` <br> `Align all field labels to the left.` <br> `Update the form layout to match the attached wireframe.` |
| **Création et logique des règles** | Implémentez le comportement dynamique, les calculs et la visibilité conditionnelle. | `Make the 'Spouse Name' field visible only if 'Marital Status' is selected as 'Married'.` <br> `Calculate the 'Total Amount' by multiplying @quantity and @price.` <br> `Enable the submit button only when the @termsAndConditions checkbox is checked.` <br> `Set the value of @countryCode to '+1' if @country is 'United States'.` <br> `If @age is less than 18, show a message 'Must be 18 or older'.` |
| **Mise à jour des propriétés du champ** | Modifier les attributs de champs de formulaire spécifiques tels que les libellés, les espaces réservés, etc. | `Change the label of @email to 'Primary Email Address'.` <br> `Set the @comment field to be a multi-line text area.` <br> `Make the @phoneNumber field mandatory.` <br> `Add placeholder text 'Enter your ZIP code' to the @zipCode field.` <br> `Change the @country field to a dropdown and populate it with: USA, Canada, UK, Germany.` <br> `Update the help description for @password to 'Must include an uppercase letter, a number, and be at least 8 characters long.'` <br> `Set the maximum length of the @username field to 15 characters.` <br> `Configure the @dateOfBirth field to use a date picker.` <br> `Style the @email field to match the design shown in the attached image.` |
| **Actions Envoyer** | Définissez ce qui se produit lorsqu’un utilisateur envoie le formulaire. | `Configure the form to submit data to the REST endpoint /api/v2/application-submit.` <br> `Set up an email submission to hr@example.com and sales@example.com on successful submission.` <br> `Trigger an AEM workflow named 'NewLeadProcessing' when this form is submitted.` <br> `On submit, redirect the user to a thank you page at /content/thankyou.html.` |
| **Thème** | Appliquez les thèmes AEM Forms existants pour appliquer un style à votre formulaire. | `Apply the 'Modern Business' theme to this form.` <br> `Switch to the 'Accessible Dark' theme.` <br> `Revert to the default canvas theme.` <br> `Apply styling that matches the brand guidelines shown in the attached style guide.` |
| **Navigation et structure** | Ajoutez des éléments de navigation ou réorganisez des parties du formulaire. | `Add a 'Next' button to the current panel and a 'Previous' button to the next panel.` <br> `Create a Table of Contents based on the form's panels.` <br> `Move the 'Address' panel to be before the 'Contact Information' panel.` |
| **Validation** | Définissez des règles de validation spécifiques pour les champs . | `Set a regex pattern for the @employeeID field to be 'EMP\d{5}'.` <br> `Ensure the @age field only accepts numeric values between 18 and 99.` <br> `Validate the @email field to ensure it is a valid email format.` |
| **Plan de révision** (éditeur universel) | Prévisualiser les modifications proposées par l&#39;assistant avant exécution. | `Add a contact form with fields for name, email, subject, and message.` (L&#39;assistant affichera un plan des composants et des propriétés qu&#39;il créera, puis vous cliquerez sur « Appliquer »). <br> `Create a form based on the attached design file.` (L&#39;assistant analyse la pièce jointe et affiche un plan détaillé avant l&#39;implémentation). |

## Bonnes pratiques pour des résultats optimaux

Pour tirer le meilleur parti de l’assistant d’IA, tenez compte des conseils suivants :

- **Démarrer simple, créer progressivement :** commencez par des commandes plus petites et spécifiques (par exemple, « Ajouter une entrée de texte pour « Prénom ») plutôt que des requêtes à plusieurs étapes trop complexes au départ.
- **Utilisez la terminologie d’AEM Forms :** utilisez des termes tels que « panneau », « champ de saisie de texte », « groupe de cases à cocher », « action d’envoi », « règle », etc., pour une meilleure compréhension par l’assistant.
- **Référencer les champs clairement :** lors de la configuration de champs existants, utilisez la notation `@fieldName` (par exemple, `Make @firstName mandatory`).
- **Passer en revue les plans** Passez toujours en revue soigneusement les plans pour les modifications proposées par l’assistant dans l’éditeur universel avant de cliquer sur « Appliquer ».
- **Valider manuellement :** une fois que l’assistant a apporté des modifications, prévisualisez et testez toujours votre formulaire pour vous assurer qu’il se comporte et s’affiche comme prévu. L’IA est un outil puissant, mais la validation finale est essentielle.
- **Itérer et affiner :** si la première invite ne produit pas le résultat exact, essayez de reformuler ou de ventiler la requête en plus petites étapes.
- **Laisser un commentaire :** utilisez le mécanisme de commentaire intégré pour aider l’assistant à apprendre et à s’améliorer (voir la section « Commentaires et assistance »).

## Aide sur les produits avec l’assistant d’IA

L’assistant AI pour AEM Forms n’est pas seulement destiné à la création ; il peut également vous aider à apprendre, à comprendre et à utiliser diverses fonctionnalités d’AEM Forms.

### Rubriques d’aide prises en charge

Vous pouvez poser à l&#39;assistant des questions telles que :

- « Comment créer entièrement un formulaire adaptatif ? »
- « En quoi consiste un panneau dans le Forms adaptatif et comment est-il utilisé ? »
- « Expliquez comment appliquer un thème à un formulaire. »
- « Quels types de disposition sont pris en charge pour les formulaires et les panneaux ? »
- « Comment configurer différentes actions d’envoi, telles que l’envoi d’un e-mail ? »
- « Pouvez-vous me guider sur l’utilisation d’un design Figma pour créer un formulaire ? »
- « Quel est le meilleur moyen de créer un formulaire à plusieurs étapes ? »

### Comment demander de l’aide :

1. Ouvrez l’assistant d’IA dans l’interface utilisateur de gestion de Forms ou l’éditeur de Forms adaptatif.
2. Saisissez votre question en langage naturel (par exemple, « Comment ajouter un panneau répétable ? »).
3. L&#39;assistant répondra par :
   - Instructions détaillées.
   - Explications des concepts AEM Forms.
   - Liens vers la documentation Adobe Experience League appropriée, le cas échéant.

### Conseils pour obtenir une aide plus efficace :

- **Soyez précis** Posez une question claire à la fois.
- **Utiliser des mots-clés :** permet d’inclure des mots-clés relatifs aux fonctionnalités d’AEM Forms ou aux éléments de l’interface utilisateur (par exemple, « éditeur de formulaires adaptatifs », « éditeur de règles », « thème »).
- **Reformuler si nécessaire :** si l’assistant ne comprend pas ou ne fournit pas les informations souhaitées, essayez de simplifier votre question ou d’utiliser des termes différents.


## Résolution des problèmes courants

- **L’Assistant Ne Répond Pas :**
   - Assurez-vous de travailler activement dans un environnement pris en charge (interface utilisateur de gestion Forms, éditeur de Forms adaptatif ou éditeur universel).
   - Vérifiez votre connexion Internet.
   - Essayez de fermer et de rouvrir le panneau de l’assistant AI.

- **Réponses inexactes ou inattendues :**
   - Reformulez votre demande pour être plus spécifique ou plus simple.
   - Ventilez une requête complexe en commandes individuelles plus petites.
   - Vérifiez que vous utilisez la terminologie AEM Forms standard.

- **Problèmes d’importation de conception (PDF/Figma/Image) :**
   - Vérifiez que le fichier de conception est clair, bien structuré et lisible.
   - Assurez-vous que le format de fichier est pris en charge (PDF, lien Figma, types d’image courants tels que PNG, JPG).
   - Pour Figma, assurez-vous que le cadre que vous ciblez est clairement défini et accessible.

- **Le Champ N’`@fieldName` Pas Reconnu :**
   - Vérifiez à nouveau le nom exact du champ dans votre formulaire. Les noms des champs sont sensibles à la casse et doivent correspondre précisément.
   - Assurez-vous que le champ existe déjà si vous tentez de le modifier.


## Commentaires et assistance

Votre contribution est inestimable pour l’amélioration continue de l’assistant d’IA.

- **Fournir des commentaires :** utilisez la commande ou le bouton intégré **« Fournir des commentaires »** dans l’interface de l’assistant d’IA pour partager vos expériences, signaler des problèmes ou suggérer des améliorations. (par exemple, vous pouvez saisir `/feedback` ou rechercher une icône de commentaires).
- **Assistance officielle :** pour les problèmes critiques ou toute assistance supplémentaire, contactez les canaux d’assistance officiels d’Adobe ou les contacts d’assistance désignés de votre organisation.



## Utilisation des pièces jointes

L’assistant AI prend en charge les pièces jointes pour améliorer votre expérience de création et de configuration de formulaires. Vous pouvez joindre différents types de fichiers pour fournir un contexte visuel, des références de conception ou des formulaires existants à convertir.

### Types de pièce jointe pris en charge

| Type de fichier | Cas d’utilisation | Commandes Prenant En Charge Les Pièces Jointes | Exemples |
|-----------|-----------|-----------------------------------|----------|
| **Images** (PNG, JPG, JPEG, GIF) | Références de disposition de formulaire, maquettes d’interface utilisateur, analyses de formulaires papier | /create-form, /add-form, /create-panel, /add-panel, /update-field | Charger une capture d’écran de la mise en page souhaitée |
| **Fichiers PDF** | Formulaires existants à convertir, spécifications de conception | /create-form, /add-form, /create-panel, /add-panel | Convertir les formulaires de demande PDF |
| **Fichiers Figma** | Concevoir des références système, des prototypes d’interface utilisateur | /create-form, /add-form, /create-panel | Importer les cadres de conception Figma |
| **Fichiers de conception** (esquisse, exportations Adobe XD) | Références de conception visuelle | /create-form, /add-form, /create-panel | Composants du système de conception de référence |

### Utilisation des pièces jointes

1. **Joignez avant ou avec votre commande :**

   - Cliquez sur l’icône de pièce jointe dans l’interface de l’assistant AI
   - Sélectionnez le ou les fichiers sur votre appareil
   - Saisissez la commande référençant le fichier joint

2. **Pièces jointes de référence dans les commandes :**

   ```
   /create-form based on the attached PDF application form
   /add-panel using the layout shown in the uploaded image
   /create-panel following the design in the attached Figma file
   /update-field @email to match the style in the attached screenshot
   ```

3. **Plusieurs pièces jointes :**

   - Vous pouvez joindre plusieurs fichiers à des fins de comparaison ou de référence
   - Spécifiez la pièce jointe à utiliser : « à l’aide de la première image jointe » ou « en fonction du fichier PDF »

### Bonnes pratiques relatives aux pièces jointes

- **Images claires et de haute qualité :** assurez-vous que les images chargées sont claires et lisibles pour une meilleure analyse de l’IA
- **Noms de fichiers pertinents :** utilisez des noms de fichier descriptifs pour aider l’IA à comprendre le contexte
- **Focus unique :** chaque pièce jointe doit se concentrer sur un aspect spécifique (disposition, conception des champs, etc.)
- **Formats pris en charge :** utilisez les formats courants (PNG, JPG, PDF) pour une meilleure compatibilité.
- **Taille du fichier :** conservez les pièces jointes de moins de 10 Mo pour une vitesse de traitement optimale

### Exemple de workflows de pièce jointe

**Conversion d’un formulaire papier :**

1. Scannez ou photographiez clairement le formulaire papier
2. Charger le fichier image
3. Utiliser la commande : `/create-form based on the attached form image, converting all fields to digital equivalents`

**Correspondance d’un système de conception :**

1. Exporter ou créer une capture d’écran des composants de conception pertinents
2. Joindre la référence de conception
3. Utiliser la commande : `/create-panel following the visual style and layout shown in the attached design`

**Référence de style de champ :**

1. Joindre une capture d’écran de l’aspect du champ souhaité
2. Utiliser la commande : `/update-field @email to match the styling and layout shown in the attached image`

## Contenu connexe

[Assistant AEM Forms AI - Bibliothèque d’invites](/help/edge/docs/forms/ai-assistant-prompt-library.md)

## Utilisation des pièces jointes

L’assistant AI prend en charge les pièces jointes pour améliorer votre expérience de création et de configuration de formulaires. Vous pouvez joindre différents types de fichiers pour fournir un contexte visuel, des références de conception ou des formulaires existants à convertir.

### Types de pièce jointe pris en charge

| Type de fichier | Cas d’utilisation | Commandes Prenant En Charge Les Pièces Jointes | Exemples |
|-----------|-----------|-----------------------------------|----------|
| **Images** (PNG, JPG, JPEG, GIF) | Références de disposition de formulaire, maquettes d’interface utilisateur, analyses de formulaires papier | /create-form, /add-form, /create-panel, /add-panel, /update-field | Charger une capture d’écran de la mise en page souhaitée |
| **Fichiers PDF** | Formulaires existants à convertir, spécifications de conception | /create-form, /add-form, /create-panel, /add-panel | Convertir les formulaires de demande PDF |
| **Fichiers Figma** | Concevoir des références système, des prototypes d’interface utilisateur | /create-form, /add-form, /create-panel | Importer les cadres de conception Figma |
| **Fichiers de conception** (esquisse, exportations Adobe XD) | Références de conception visuelle | /create-form, /add-form, /create-panel | Composants du système de conception de référence |

### Utilisation des pièces jointes

1. **Joignez avant ou avec votre commande :**

   - Cliquez sur l’icône de pièce jointe dans l’interface de l’assistant AI
   - Sélectionnez le ou les fichiers sur votre appareil
   - Saisissez la commande référençant le fichier joint

2. **Pièces jointes de référence dans les commandes :**

   ```
   /create-form based on the attached PDF application form
   /add-panel using the layout shown in the uploaded image
   /create-panel following the design in the attached Figma file
   /update-field @email to match the style in the attached screenshot
   ```

3. **Plusieurs pièces jointes :**

   - Vous pouvez joindre plusieurs fichiers à des fins de comparaison ou de référence
   - Spécifiez la pièce jointe à utiliser : « à l’aide de la première image jointe » ou « en fonction du fichier PDF »

### Bonnes pratiques relatives aux pièces jointes

- **Images claires et de haute qualité :** assurez-vous que les images chargées sont claires et lisibles pour une meilleure analyse de l’IA
- **Noms de fichiers pertinents :** utilisez des noms de fichier descriptifs pour aider l’IA à comprendre le contexte
- **Focus unique :** chaque pièce jointe doit se concentrer sur un aspect spécifique (disposition, conception des champs, etc.)
- **Formats pris en charge :** utilisez les formats courants (PNG, JPG, PDF) pour une meilleure compatibilité.
- **Taille du fichier :** conservez les pièces jointes de moins de 10 Mo pour une vitesse de traitement optimale

### Exemple de workflows de pièce jointe

**Conversion d’un formulaire papier :**

1. Scannez ou photographiez clairement le formulaire papier
2. Charger le fichier image
3. Utiliser la commande : `/create-form based on the attached form image, converting all fields to digital equivalents`

**Correspondance d’un système de conception :**

1. Exporter ou créer une capture d’écran des composants de conception pertinents
2. Joindre la référence de conception
3. Utiliser la commande : `/create-panel following the visual style and layout shown in the attached design`

**Référence de style de champ :**

1. Joindre une capture d’écran de l’aspect du champ souhaité
2. Utiliser la commande : `/update-field @email to match the styling and layout shown in the attached image`
