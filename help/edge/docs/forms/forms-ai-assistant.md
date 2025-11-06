---
title: Assistant IA pour AEM Forms (Créateur d’expériences de formulaires)
description: Créer des formulaires performants plus rapidement à l’aide de fragments de formulaire
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 100%

---


# Prise en main de l’assistant IA pour AEM Forms (Créateur d’expériences de formulaires)

>[!NOTE]
>
>
> La fonctionnalité d’assistant IA pour AEM Forms (Forms Experience Builder) est disponible dans le cadre du **programme d’accès anticipé**. Si cela vous intéresse, envoyez un e-mail rapide à l’adresse mailto:aem-forms-ea@adobe.com depuis votre adresse e-mail professionnelle pour demander l’accès à la fonctionnalité.

>[!IMPORTANT]
>
> **Documentation susceptible de modification** : cette documentation est actuellement testée par rapport au produit et peut faire l’objet de mises à jour et de révisions. Les fonctionnalités, commandes et exemples peuvent changer à mesure que l’assistant IA pour AEM Forms continue d’évoluer au cours du programme destiné aux utilisateurs et utilisatrices précoces.

L’assistant IA pour AEM Forms transforme la création de formulaires : il vous suffit de décrire vos besoins en langage naturel afin de voir vos formulaires prendre vie. Disponible dans l’interface d’utilisation de gestion des formulaires, l’éditeur de formulaires adaptatifs et l’éditeur universel, il comprend votre intention et crée exactement ce que vous recherchez.

## Prise en main : parlez-lui, tout simplement

L’assistant IA fonctionne comme une conversation avec une personnes compétente. Au lieu d’apprendre des menus et des paramètres complexes, vous décrivez simplement ce que vous souhaitez créer.

### Démarrage rapide

Lancez-vous rapidement en regardant notre vidéo d’introduction :

>[!VIDEO](https://video.tv.adobe.com/v/3463164/)

### Accès à l’assistant IA

Vous pouvez accéder à l’assistant IA à partir de trois emplacements différents dans AEM Forms :

1. **Interface d’utilisation de gestion des formulaires**
   - Accédez à Adobe Experience Manager > Formulaires > Formulaires et documents.
   - Recherchez l’icône de l’assistant IA sur le côté gauche de l’interface.
   - Cliquez sur l’icône pour ouvrir le panneau de l’assistant IA.

   ![Icône de l’assistant IA*](/help/edge/docs/forms/assets/forms-manager.gif){width="50%"}

2. **Éditeur de formulaires adaptatifs**
   - Accédez à Adobe Experience Manager > Formulaires > Formulaires et documents.
   - Sélectionnez et ouvrez un formulaire pour le modifier.
   - Cliquez sur l’icône de l’assistant IA dans l’interface de l’éditeur.

   ![Icône de l’assistant IA*](/help/edge/docs/forms/assets/adaptive-forms-editor.gif){width="75%"}

3. **Éditeur universel**

   - Accédez à Adobe Experience Manager > Formulaires > Formulaires et documents.
   - Recherchez l’icône de l’assistant IA sur le côté gauche de l’interface.
   - Cliquez sur l’icône de l’assistant IA dans l’interface de l’éditeur.

### Démarrage : conversations simples

La meilleure façon de commencer avec l’assistant IA est de passer par le langage naturel. Procédez comme suit :

**Décrivez simplement ce dont vous avez besoin :**

- « Crée un formulaire de contact pour mon site web. »
- « J’ai besoin d’un formulaire de commentaires clientèle avec des échelles de notation. »
- « Crée un formulaire d’inscription pour mon événement à venir. »
- « Fais une simple enquête sur la satisfaction des produits. »

**Ajoutez des détails au fur et à mesure :**

- « Crée un formulaire de contact avec des champs de nom, d’adresse e-mail, de téléphone et de message. »
- « J’ai besoin d’un formulaire d’inscription en plusieurs étapes pour une conférence. »
- « Crée un formulaire de commentaires clientèle avec des évaluations 5 étoiles et des sections de commentaires. »

**Référencez vos champs existants :**

- « Rends le champ d’e-mail obligatoire » (pour @email)
- « Ajoute la validation au champ du numéro de téléphone » (pour @phoneNumber)
- « Affiche les informations sur le ou la partenaire uniquement si marié(e) est sélectionné. » (pour @spouseInfo et @maritalStatus)

### Ce que vous pouvez également faire

Au-delà du langage naturel, l’assistant IA offre d’autres moyens d’interagir :

- **Charger des fichiers** : joignez des images, des PDF ou des conceptions Figma pour montrer à l’IA ce que vous envisagez.
- **Utiliser des commandes rapides** : saisissez `/` pour afficher les raccourcis disponibles pour les actions courantes.
- **Champs spécifiques à la référence** : utilisez `@fieldName` pour modifier les champs de formulaire existants (par exemple, `@firstName`, `@emailAddress`).

## Ce que vous pouvez créer : des exemples qui fonctionnent

Voici de vrais exemples de ce que vous pouvez accomplir avec un langage simple et naturel :

### Démarrage d’un nouveau formulaire

**Approche simple :**

```
"Create a contact form"
```

**Approche plus détaillée :**

```
"Create a professional contact form for a law firm with fields for name, email, phone, case type, and message. Make it mobile-friendly."
```

**Avec référence de conception :**

```
"Create a contact form based on the attached design mockup. Include all the fields shown in the layout."
```

### Ajout d’éléments au formulaire

**Ajouts de base :**

```
"Add a section for personal information"
"Include a file upload for resume"
"Add a dropdown for country selection"
```

**Spécifications détaillées :**

```
"Add a personal information panel with fields for full name, date of birth, phone number, and email address"
"Include a secure file upload component for documents, limited to PDF files under 5MB"
"Add a country dropdown with options for USA, Canada, UK, and Germany"
```

### Création d’un comportement dynamique

**Approche simple :**

```
"Show additional fields when 'Other' is selected"
"Make the email field required"
"Calculate the total automatically"
```

**Règles métier complexes :**

```
"Show the spouse information fields only when marital status is set to 'Married'"
"Calculate the total cost by multiplying quantity and price, then add 10% tax"
"Enable the submit button only when all required fields are completed and terms are accepted"
```

### Mise en page et conception de formulaire

**Modifications de la mise en page :**

```
"Make this a multi-step form"
"Organize fields in two columns"
"Convert to an accordion layout"
```

**Améliorations de la conception :**

```
"Create a wizard-style form with 3 steps: personal info, preferences, and review"
"Arrange the address fields in a compact two-column layout"
"Update the layout to match the attached wireframe"
```

### Envoi et intégration

**Envoi de base :**

```
"Send form data to our email"
"Save responses to a spreadsheet"
"Redirect to a thank you page"
```

**Intégration avancée :**

```
"Send form submissions to hr@company.com and create a case in our CRM system"
"Submit data to our REST API endpoint and trigger the new customer workflow"
"Email responses to the sales team and add the lead to our marketing automation platform"
```

## Utilisation des pièces jointes

Chargez des fichiers pour aider l’IA à comprendre exactement ce que vous recherchez :

### Types de fichiers pris en charge

| Type de fichier | Idéal pour | Exemple d’utilisation |
|-----------|----------|-------------|
| **Images** (PNG, JPG, GIF) | Mises en page de formulaires, maquettes d’interface d’utilisation, analyses de formulaires papier | « Crée un formulaire correspondant à cette mise en page. » |
| **Fichiers PDF** | Formulaires existants à convertir, spécifications | « Convertis ce formulaire PDF en formulaire numérique. » |
| **Fichiers Figma** | Concevoir des prototypes, des directives de marque | « Crée ce formulaire à partir de mon design Figma. » |
| **Fichiers de conception** | Références visuelles, guides de style | « Reproduis le style dans cette conception. » |

### Utilisation des pièces jointes

1. **Cliquez sur l’icône de pièce jointe** dans l’interface de l’assistant AI.
2. **Sélectionnez un fichier** sur votre ordinateur.
3. **Décrivez ce que vous souhaitez** en référençant le fichier joint :
   - « Créé un formulaire basé sur ce PDF joint. »
   - « Crée un formulaire de contact correspondant à la mise en page dans cette image. »
   - « Convertis ce formulaire papier en version numérique. »

### Bonnes pratiques relatives aux pièces jointes

- **Utilisez des images claires et de haute qualité** pour une meilleure analyse de l’IA.
- **Concentrez-vous sur un concept par pièce jointe** (mise en page, style, etc.)
- **Décrivez ce que vous souhaitez** avec la pièce jointe.
- **Utilisez des fichiers de moins de 10 Mo** pour un traitement optimal.

## Conseils pour obtenir de meilleurs résultats

### Démarrer simplement, puis compléter

- Commencer par une demande de base : « Créer un formulaire de contact »
- Ajouter des détails progressivement : « Ajouter la validation au champ d’e-mail »
- Tester et affiner : « Rendre le champ du numéro de téléphone facultatif »

### Faire preuve de précision lorsque nécessaire

- Au lieu de : « Créer un beau formulaire »
- Essayer : « Utiliser des couleurs professionnelles et une typographie simple »

### Utiliser un langage naturel

- Au lieu de : « Ajouter un composant de saisie de texte »
- Essayer : « Ajouter un champ pour le prénom »

### Référencer des éléments existants

- Utiliser `@fieldName` pour les champs existants : « Rendre @email obligatoire »
- Faire preuve de précision concernant les noms de champ : « Mettre à jour le champ @phoneNumber »

### Décomposer les requêtes complexes

- Au lieu d’une seule longue requête, essayer plusieurs requêtes plus petites
- Créer le formulaire étape par étape
- Tester chaque modification avant de passer à la suivante

## Aide sur les produits et apprentissage

L’Assistant IA peut également vous apprendre à utiliser les fonctionnalités d’AEM Forms :

### Poser des questions du type :

- « Comment créer un formulaire à plusieurs étapes ? »
- « Quelle est la différence entre les panneaux et les sections ? »
- « Comment configurer les notifications par e-mail ? »
- « Quelles sont les bonnes pratiques concernant les formulaires compatibles avec les appareils mobiles ? »
- « Comment appliquer des thèmes à mes formulaires ? »

### Obtenir de l’aide sur :

- Concepts et terminologie d’AEM Forms
- Instructions détaillées relatives aux fonctionnalités complexes
- Bonnes pratiques et recommandations
- Résolution des problèmes courants

## Référence des fonctionnalités avancées

Pour les personnes qui souhaitent explorer les fonctionnalités avancées :

### Commandes rapides

Saisissez `/` pour afficher les raccourcis disponibles :

| Commande | Objectif | Exemple |
|---------|---------|---------|
| `/create-form` | Démarrer un nouveau formulaire | `/create-form customer survey` |
| `/add-form` | Ajouter un formulaire dans l’éditeur universel | `/add-form contact form` |
| `/update-layout` | Modifier la structure du formulaire | `/update-layout wizard with 3 steps` |
| `/update-field` | Modification les propriétés des champs | `/update-field @email to be required` |
| `/create-rule` | Ajouter un comportement dynamique | `/create-rule show @spouse if married` |
| `/create-panel` | Ajouter des conteneurs de champs | `/create-panel Personal Information` |
| `/configure-submit` | Configurer l’envoi des formulaires | `/configure-submit to email support` |
| `/help` | Obtenir de l’aide | `/help multi-step forms` |

### Syntaxe de référence du champ

Utilisez `@fieldName` pour référencer les champs existants :

- `@firstName` - Champ Prénom
- `@email` - Champ E-mail
- `@phoneNumber` - Champ Numéro de téléphone
- `@dateOfBirth` - Champ Date de naissance

### Types de composants

Utilisez ces termes pour obtenir les meilleurs résultats :

- `text input` - Un champ de texte d’une seule ligne
- `text area` - Champ de texte à plusieurs lignes
- `dropdown` - Sélectionner une liste
- `checkbox` - Case à cocher simple
- `checkbox group` - Cases à cocher multiples
- `radio group` - Groupe de cases d’option
- `date picker` - Sélection de la date
- `file upload` - Pièce jointe
- `panel` - Conteneur pour regrouper des champs

## Résolution des problèmes

### Problèmes courants et solutions

**L’Assistant IA ne répond pas :**

- Vérifier votre connexion Internet
- Vérifier que vous vous trouvez dans un environnement pris en charge
- Fermer et rouvrir le panneau de l’Assistant IA

**Résultats inattendus :**

- Essayer de reformuler la requête plus précisément
- Décomposer les requêtes complexes en étapes plus petites
- Utiliser la terminologie AEM Forms standard

**Les références de champ ne fonctionnent pas :**

- Vérifier que les noms des champs sont orthographiés exactement tel qu’ils s’affichent
- Utiliser la syntaxe `@fieldName` pour les champs existants
- Vérifier que le champ existe avant de le référencer

**Problèmes d’import de conception :**

- Vérifier que les fichiers sont clairs et bien structurés
- Utiliser les formats pris en charge (PDF, PNG, JPG, Figma)
- Vérifier que la taille du fichier est inférieure à 10 Mo

## Commentaires et assistance

Aidez-nous à améliorer l’Assistant IA :

- **Envoyer des commentaires** : utiliser le bouton Commentaires dans l’interface de l’Assistant IA
- **Problèmes de rapport** : contactez l’assistance Adobe en passant par les canaux officiels
- **Partager des expériences** : grâce à vos commentaires, nous adaptons davantage l’assistant aux besoins de tous

## Ressources connexes

[Assistant IA AEM Forms - Bibliothèque d’invites](/help/forms/experience-builder/forms-experience-builder-prompt-examples-library.md)
