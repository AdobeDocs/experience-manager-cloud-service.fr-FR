---
title: Assistant AI pour AEM Forms (Forms Experience Builder)
description: Créer des formulaires puissants plus rapidement à l’aide de fragments de formulaire
feature: Edge Delivery Services
hide: true
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: a8d64082-a23f-4919-ad66-042faad77d29
source-git-commit: ab071b9159f3d4db275313080d7c14a46096c4de
workflow-type: tm+mt
source-wordcount: '1141'
ht-degree: 1%

---

# Assistant AI pour AEM Forms (Forms Experience Builder)

>[!NOTE]
>
>
> La fonctionnalité Assistant AI pour AEM Forms (Forms Experience Builder) est disponible sous le **programme destiné aux utilisateurs et utilisatrices précoces**. Si vous êtes intéressé, envoyez un e-mail rapide à partir de votre adresse professionnelle à mailto:aem-forms-ea@adobe.com pour demander l’accès à la fonctionnalité.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette documentation est actuellement testée par rapport au produit et est sujette à mises à jour et révisions. Les fonctionnalités, commandes et exemples peuvent changer à mesure que l’assistant AI pour AEM Forms continue d’évoluer au cours du programme destiné aux utilisateurs et utilisatrices précoces.

L’assistant d’IA pour AEM Forms transforme la création de formulaires : il vous suffit de décrire vos besoins en langage naturel et de voir vos formulaires prendre vie. Disponible dans l’interface utilisateur de gestion de Forms, l’éditeur de Forms adaptatif et l’éditeur universel, il comprend votre intention et crée exactement ce que vous recherchez.

## Prise en main : parlez-en simplement

L’assistant d’IA fonctionne comme une conversation avec un collègue compétent. Au lieu d’apprendre des menus et des paramètres complexes, vous décrivez simplement ce que vous souhaitez créer.

### Démarrage rapide

Lancez-vous rapidement en regardant notre vidéo d’introduction :

>[!VIDEO](https://video.tv.adobe.com/v/3463164/)

### Accès à l’assistant d’IA

Vous pouvez accéder à l’assistant d’IA à partir de trois emplacements différents dans AEM Forms :

1. **Interface utilisateur de gestion de Forms**
   - Accédez à : Adobe Experience Manager > Forms > Forms et documents .
   - Recherchez l’icône de l’assistant AI sur le côté gauche de l’interface
   - Cliquez sur l’icône pour ouvrir le panneau de l’assistant AI

   ![Icône de l’assistant AI*](/help/edge/docs/forms/assets/forms-manager.gif){width="50%"}

2. **Éditeur de Forms adaptatif**
   - Accédez à : Adobe Experience Manager > Forms > Forms et documents .
   - Sélectionner et ouvrir un formulaire pour le modifier
   - Cliquez sur l’icône de l’assistant AI dans l’interface de l’éditeur

   ![Icône de l’assistant AI*](/help/edge/docs/forms/assets/adaptive-forms-editor.gif){width="75%"}

3. **Éditeur universel**

   - Accédez à : Adobe Experience Manager > Forms > Forms et documents .
   - Recherchez l’icône de l’assistant AI sur le côté gauche de l’interface
   - Cliquez sur l’icône de l’assistant AI dans l’interface de l’éditeur

### Démarrage : conversations simples

La meilleure façon de commencer avec l’assistant d’IA est de passer par le langage naturel. Procédez comme suit :

**Décrivez simplement ce dont vous avez besoin**

- « Créer un formulaire de contact pour mon site web »
- « J’ai besoin d’un formulaire de commentaires client avec des échelles de notation »
- « Créer un formulaire d&#39;inscription pour mon événement à venir »
- « Faire une simple enquête sur la satisfaction des produits »

**Ajoutez des détails au fur et à mesure :**

- « Créer un formulaire de contact avec des champs de nom, d’adresse e-mail, de téléphone et de message »
- « J’ai besoin d’un formulaire d’inscription en plusieurs étapes pour une conférence »
- « Créer un formulaire de commentaires client avec des évaluations 5 étoiles et des sections de commentaires »

**Référencez vos champs existants :**

- « Rendre le champ d’e-mail obligatoire » (par @email)
- « Ajouter la validation au champ du numéro de téléphone » (par @phoneNumber)
- « Afficher les informations sur le conjoint uniquement si marié est sélectionné » (par @spouseInfo et @maritalStatus)

### Ce Que Vous Pouvez Également Faire

Au-delà du langage naturel, l’assistant d’IA offre d’autres moyens d’interagir :

- **Charger des fichiers** : joignez des images, des PDF ou des conceptions Figma pour montrer à l’IA ce que vous envisagez
- **Utiliser des commandes rapides** : saisissez `/` pour afficher les raccourcis disponibles pour les actions courantes
- **Champs spécifiques à la référence** : utilisez `@fieldName` pour modifier les champs de formulaire existants (par exemple, `@firstName`, `@emailAddress`)

## Ce Que Vous Pouvez Créer : Des Exemples Qui Fonctionnent

Voici de vrais exemples de ce que vous pouvez accomplir avec un langage simple et naturel :

### Démarrer un nouveau formulaire

**Approche simple :**

```
"Create a contact form"
```

**Approche plus détaillée :**

```
"Create a professional contact form for a law firm with fields for name, email, phone, case type, and message. Make it mobile-friendly."
```

**Avec référence de conception :**

```
"Create a contact form based on the attached design mockup. Include all the fields shown in the layout."
```

### Ajout d’éléments de formulaire

**Ajouts de base :**

```
"Add a section for personal information"
"Include a file upload for resume"
"Add a dropdown for country selection"
```

**Spécifications détaillées :**

```
"Add a personal information panel with fields for full name, date of birth, phone number, and email address"
"Include a secure file upload component for documents, limited to PDF files under 5MB"
"Add a country dropdown with options for USA, Canada, UK, and Germany"
```

### Création d’un comportement dynamique

**Logique simple :**

```
"Show additional fields when 'Other' is selected"
"Make the email field required"
"Calculate the total automatically"
```

**Règles métier complexes :**

```
"Show the spouse information fields only when marital status is set to 'Married'"
"Calculate the total cost by multiplying quantity and price, then add 10% tax"
"Enable the submit button only when all required fields are completed and terms are accepted"
```

### Mise en page et conception de formulaire

**Modifications de la mise en page :**

```
"Make this a multi-step form"
"Organize fields in two columns"
"Convert to an accordion layout"
```

**Améliorations de la conception :**

```
"Create a wizard-style form with 3 steps: personal info, preferences, and review"
"Arrange the address fields in a compact two-column layout"
"Update the layout to match the attached wireframe"
```

### Envoi et intégration

**Envoi de base :**

```
"Send form data to our email"
"Save responses to a spreadsheet"
"Redirect to a thank you page"
```

**Intégration avancée :**

```
"Send form submissions to hr@company.com and create a case in our CRM system"
"Submit data to our REST API endpoint and trigger the new customer workflow"
"Email responses to the sales team and add the lead to our marketing automation platform"
```

## Utilisation des pièces jointes

Chargez des fichiers pour aider l’IA à comprendre exactement ce que vous recherchez :

### Types de fichiers pris en charge

| Type de fichier | Idéal Pour | Exemple d’utilisation |
|-----------|----------|-------------|
| **Images** (PNG, JPG, GIF) | Dispositions de formulaires, maquettes d’interface utilisateur, analyses de formulaires papier | « Créer un formulaire correspondant à cette disposition » |
| **Fichiers PDF** | Formulaires existants à convertir, spécifications | « Convertir ce formulaire PDF en formulaire numérique » |
| **Fichiers Figma** | Concevoir des prototypes, des directives de marque | « Créer ce formulaire à partir de mon design Figma » |
| **Fichiers de conception** | Références visuelles, guides de style | « Respecter le style dans cette conception » |

### Utilisation des pièces jointes

1. **Cliquez sur l’icône de pièce jointe** dans l’interface de l’assistant AI
2. **Sélectionnez votre fichier** sur votre appareil
3. **Décrivez ce que vous souhaitez** en référençant le fichier joint :
   - « Création d’un formulaire basé sur ce PDF joint »
   - « Créer un formulaire de contact correspondant à la mise en page dans cette image »
   - « Convertir ce formulaire papier en version numérique »

### Bonnes pratiques relatives aux pièces jointes

- **Utilisez des images claires et de haute qualité** pour une meilleure analyse de l’IA.
- **Concentrez-vous sur un concept par pièce jointe** (disposition, style, etc.)
- **Décrivez ce que vous souhaitez** ainsi que la pièce jointe
- **Conserver les fichiers de moins de 10 Mo** pour un traitement optimal

## Conseils pour obtenir de meilleurs résultats

### Démarrer simple, créer

- Commencez par les demandes de base : « Créer un formulaire de contact »
- Ajouter les détails progressivement : « Ajouter la validation au champ d’e-mail »
- Tester et affiner : « Rendre le champ du téléphone facultatif »

### Soyez Précis Si Nécessaire

- Au lieu de : « Faites en sorte qu’il ait l’air correct »
- Essayer : « Utiliser des couleurs professionnelles et une typographie propre »

### Utiliser le langage naturel

- Au lieu de : « Ajouter un composant de saisie de texte »
- Essayer : « Ajouter un champ pour le prénom »

### Référencer des éléments existants

- Utiliser des `@fieldName` pour les champs existants : « Rendre @email obligatoire »
- Soyez précis concernant les noms de champ : « Mettre à jour le champ de @phoneNumber »

### Répartition Des Requêtes Complexes

- Au lieu d’une grande requête, essayez plusieurs requêtes plus petites
- Créer votre formulaire étape par étape
- Tester chaque modification avant de passer à la suivante

## Aide et apprentissage du produit

L’assistant AI peut également vous apprendre à utiliser les fonctionnalités d’AEM Forms :

### Posez Des Questions Telles Que :

- « Comment créer un formulaire à plusieurs étapes ? »
- « Quelle est la différence entre les panneaux et les sections ? »
- « Comment configurer les notifications par e-mail ? »
- « Quelles sont les bonnes pratiques relatives aux formulaires compatibles avec les appareils mobiles ? »
- « Comment appliquer des thèmes à mes formulaires ? »

### Obtenez De L’Aide Sur :

- Concepts et terminologie d’AEM Forms
- Instructions détaillées sur les fonctionnalités complexes
- Bonnes pratiques et recommandations
- Résolution des problèmes courants

## Référence des fonctionnalités avancées

Pour les utilisateurs qui souhaitent explorer les fonctionnalités avancées :

### Commandes rapides

Saisissez `/` pour afficher les raccourcis disponibles :

| Commande | Objectif | Exemple |
|---------|---------|---------|
| `/create-form` | Démarrer un nouveau formulaire | `/create-form customer survey` |
| `/add-form` | Ajouter un formulaire dans l’éditeur universel | `/add-form contact form` |
| `/update-layout` | Modifier la structure du formulaire | `/update-layout wizard with 3 steps` |
| `/update-field` | Modification des propriétés des champs | `/update-field @email to be required` |
| `/create-rule` | Ajout d’un comportement dynamique | `/create-rule show @spouse if married` |
| `/create-panel` | Ajouter des conteneurs de champs | `/create-panel Personal Information` |
| `/configure-submit` | Configurer l’envoi du formulaire | `/configure-submit to email support` |
| `/help` | Obtenir de l’aide | `/help multi-step forms` |

### Syntaxe de référence du champ

Utilisez des `@fieldName` pour référencer les champs existants :

- `@firstName` - Champ Prénom
- `@email` - Champ e-mail
- `@phoneNumber` - Champ Numéro de téléphone
- `@dateOfBirth` - Champ Date de naissance

### Types de composants

Utilisez ces termes pour obtenir de meilleurs résultats :

- `text input` - Champ de texte monoligne
- `text area` - Champ de texte multiligne
- `dropdown` - Sélectionner la liste
- `checkbox` - Case à cocher unique
- `checkbox group` - Cases à cocher multiples
- `radio group` - Groupe de boutons radio
- `date picker` - Sélection de la date
- `file upload` - Pièce jointe
- `panel` - Conteneur pour le regroupement des champs

## Résolution des problèmes

### Problèmes courants et solutions

**L’assistant AI ne répond pas :**

- Vérifier votre connexion Internet
- Vérifiez que vous vous trouvez dans un environnement pris en charge
- Fermez et rouvrez le panneau de l’assistant AI

**Résultats inattendus :**

- Essayez de reformuler votre requête plus précisément
- Répartition des requêtes complexes en étapes plus petites
- Utiliser la terminologie AEM Forms standard

**Les Références De Champ Ne Fonctionnent Pas :**

- Les noms des champs de vérification sont orthographiés exactement comme ils apparaissent
- Utiliser la syntaxe `@fieldName` pour les champs existants
- Assurez-vous que le champ existe avant de le référencer

**Problèmes d’importation de conception :**

- Vérifier que les fichiers sont clairs et bien structurés
- Utiliser les formats pris en charge (PDF, PNG, JPG, Figma)
- Assurez-vous que la taille du fichier est inférieure à 10 Mo

## Commentaires et assistance

Aidez-nous à améliorer l’assistant d’IA :

- **Fournir un retour d’informations** : utilisez le bouton Commentaires dans l’interface de l’assistant d’IA
- **Problèmes de rapport** : contactez l’assistance Adobe par le biais des canaux officiels
- **Partage d’expériences** : vos commentaires contribuent à rendre l’assistant mieux adapté à tous

## Ressources connexes

[Assistant AEM Forms AI - Bibliothèque d’invites](/help/edge/docs/forms/ai-assistant-prompt-library.md)
