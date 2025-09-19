---
title: Déploiement et configuration de Forms Experience Builder
description: Découvrez comment utiliser Forms Experience Builder pour créer et gérer des formulaires avec divulgation progressive pour tous les types d’utilisateurs et d’utilisatrices.
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: de524aeddd5f53cbd713ff0523222966752ebbc0
workflow-type: tm+mt
source-wordcount: '1404'
ht-degree: 32%

---


# Déploiement et configuration de Forms Experience Builder

>[!NOTE]
>
> Forms Experience Builder est disponible dans le cadre d’un programme d’accès anticipé. Avant de commencer, vérifiez que vous avez demandé et obtenu l’accès. Pour obtenir des instructions complètes, consultez la section [Informations d’intégration](product-overview.md#onboarding) .

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette documentation est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les fonctionnalités, commandes et exemples peuvent changer à mesure que le Forms Experience Builder continue d’évoluer pendant le programme d’accès anticipé.

Ce guide complet aide à démarrer la création et la gestion de formulaires avec la technologie d’IA conversationnelle. Que vous débutiez et souhaitiez créer votre premier formulaire, ou que vous cherchiez à exploiter des fonctionnalités sophistiquées, vous trouverez des informations détaillées et des exemples pratiques pour vous guider dans les fonctionnalités de Forms Experience Builder.

## Conditions préalables et configuration

### Conditions d’accès

Avant d’utiliser Forms Experience Builder, vérifiez que vous disposez des éléments suivants :

* **Accès à Forms Experience Builder** - Disponible via le programme d’accès anticipé
* **AEM Forms as a Cloud Service** - Environnement de création de production avec composants principaux de Forms adaptatif
* **Compréhension de base** - Familiarité avec les concepts de formulaire et les exigences commerciales

### Vérifier que Forms est activé

Avant d’utiliser Forms Experience Builder, vérifiez qu’[AEM Forms est activé pour votre environnement](/help/forms/setup-forms-cloud-service.md).

### Configuration de votre environnement

Votre processus de configuration dépend de votre implémentation AEM Forms. Choisissez le chemin d’accès qui correspond à votre projet.

**Pour Edge Delivery Services**

Si vous utilisez Edge Delivery Services Forms et que vous utilisez principalement l’éditeur universel. [Préparez votre projet pour Edge Delivery Services Forms](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md). Il s’agit d’une configuration unique pour activer Forms Experience Builder.

**Pour les formulaires basés sur les composants principaux**

Si vous utilisez un Forms adaptatif basé sur les composants principaux dans l’environnement de création AEM, assurez-vous que [les composants principaux de Forms adaptatif sont activés](/help/forms/enable-adaptive-forms-core-components.md) pour votre environnement.



## Démarrage rapide

### Accéder au créateur d’expérience de formulaires

Vous pouvez accéder au Forms Experience Builder à partir de trois emplacements principaux, en fonction de votre workflow et de votre type de formulaire.


**1. Éditeur de Forms adaptatif (pour les composants principaux)**

Vous pouvez lancer le créateur directement lors de la modification d’un formulaire spécifique.

1. Accédez à **AEM > Forms > Forms et documents**.
1. [Créez un formulaire à l’aide d’un modèle de composants principaux](/help/forms/creating-adaptive-form-core-components.md) ou ouvrez un formulaire existant.
1. Sélectionnez l’icône **Forms Experience Builder** dans la barre d’outils de l’éditeur pour ouvrir l’interface de conversation.

   ![Icône de l’assistant IA*](/help/edge/docs/forms/assets/adaptive-forms-editor.gif){width="75%"}

**1. Éditeur universel (pour Edge Delivery Services Forms)**

Pour les formulaires fournis via Edge Delivery Services, le créateur est intégré à l’éditeur universel.

1. Ouvrez votre formulaire Edge Delivery Services dans l’éditeur universel.
2. Sélectionnez l’icône **Forms Experience Builder** dans le panneau de droite pour lancer l’interface de conversation.

### Votre premier formulaire

| Exemple de conversation |   |
|--------------------------------------------------------------------------------------------------------------------------------------------|---|
| **Essayez cette conversation pour créer un formulaire de contact complet (basé sur la démonstration de Summit) :**<br><br>**Vous :** « Créez un formulaire de contact pour capturer des informations personnelles, y compris le nom complet, l’adresse e-mail, le numéro de téléphone, le nom de la société, l’intitulé de la fonction et un champ de message pour les demandes »<br><br>**AI :** sélectionnez un modèle<br>    Liste déroulante pour sélectionner un modèle <br><br>**AI :** un thème<br>    Liste déroulante pour sélectionner un thème <br><br>**AI :** Créer un formulaire | ![Votre Premier Formulaire](/help/edge/docs/forms/assets/create-form.png) |
| <br>**AI:** Ouvrir le formulaire créé | </br> Le formulaire est créé et ouvert dans l’éditeur |


### Commandes essentielles

| Symbole | Objectif | Exemple d’utilisation |
|--------|---------|---------------|
| `/` | Actions rapides et raccourcis | `/create-form contact form`, `/help validation rules`, `/update-layout wizard` |
| `@` | Référencer les champs de formulaire existants | `@email`, `@firstName`, `Make @phoneNumber required` |
| Texte brut | Conversation naturelle | « Ajouter un champ de numéro de téléphone obligatoire », « Créer une validation pour l’e-mail » |

**Exemples de commandes spécifiques :**

* `/create-form customer survey` - Crée un formulaire d’enquête auprès des clients
* `/add-field @email validation` - Ajoute la validation au champ d’e-mail existant
* `/create-rule show @spouse if @maritalStatus equals married` - Crée une logique conditionnelle
* `/configure-submit to email support@company.com` - Configuration de l’envoi d’e-mails
* `/help multi-step forms` - Obtient de l’aide sur la création de formulaires à plusieurs étapes

### Conseils pour réussir

* **Précisez** : « Ajoute un champ e-mail obligatoire avec validation » est plus efficace que « ajoute e-mail »
* **Référencez des champs existants** : utilisez des `@fieldName` lors de la modification de formulaires
* **Demander de l’aide** : saisissez `/help` suivi de votre question.
* **Itérer** : effectuez une modification à la fois pour obtenir de meilleurs résultats.


## Méthodes pour commencer à créer un formulaire

### Commencer avec les invites en langage naturel

Décrivez les exigences de votre formulaire en langage naturel. Forms Experience Builder génère ensuite la structure complète du formulaire :

**Exemples :**

* « Crée un formulaire de demande de prêt avec des informations personnelles, des détails financiers et des chargements de documents. »
* « Crée un formulaire de commentaires clientèle avec des évaluations, des commentaires et des catégories de produit. »
* « J’ai besoin d’un formulaire d’inscription en plusieurs étapes avec traitement des paiements pour une conférence. »


### Interactions clés

#### Ajouter des éléments de formulaire

**Ajouts de base :**

    👤 Vous : « Ajouter une section pour les informations personnelles »
    👤 Vous : « Inclure un téléchargement de fichier pour un CV »
    👤 Vous : « Ajouter une liste déroulante pour la sélection de pays »

**Spécifications détaillées :**

    👤 Vous : « Ajoutez un panneau d’informations personnelles avec des champs pour le nom complet, la date de naissance, le numéro de téléphone et l’adresse e-mail »
    👤 Vous : « Incluez un composant de chargement de fichier sécurisé pour les documents, limité aux fichiers PDF de moins de 5 Mo »
    👤 Vous : « Ajoutez une liste déroulante par pays avec des options pour les États-Unis, le Canada, le Royaume-Uni et l’Allemagne »

#### Créer un comportement dynamique

**Approche simple :**

    👤 Vous : « Afficher les champs supplémentaires lorsque « Autre » est sélectionné »
    🤖 AI : « Création d’une règle conditionnelle qui affiche des champs supplémentaires lorsque « Autre » est sélectionné »
    
    👤 Vous : « Rendre le champ d’e-mail obligatoire »
    🤖 AI : « Mettre à jour le champ d’e-mail pour qu’il soit obligatoire avec la validation »
    
    👤 Vous : « Calculer le total automatiquement »
    🤖 AI : « Ajout d’une logique de calcul pour calculer automatiquement les totaux »

**Règles métier complexes :**

    👤 Vous : « Afficher les champs d’informations sur le conjoint uniquement lorsque l’état civil est défini sur « Marié(e) » »
    🤖 AI : « Création d’une règle conditionnelle qui affiche les champs de conjoint(e) en fonction de l’état civil »
    
    👤 Vous : « Calculez le coût total en multipliant la quantité et le prix, puis ajoutez la taxe de 10 % »
    🤖 AI : « Ajout d’une logique de calcul avec le calcul de la quantité, du prix et de la taxe »
    
    👤 Vous : « Activez le bouton de soumission uniquement lorsque tous les champs obligatoires sont remplis et que les conditions sont acceptées »
    🤖 AI : « Création d’une logique de validation qui permet la soumission uniquement lorsque toutes les conditions sont remplies »

#### Disposition et conception des formulaires

**Modifications de la mise en page :**

    👤 Vous : « Créer un formulaire à plusieurs étapes »
    🤖 AI : « A converti le formulaire en disposition progressive avec navigation »
    
    👤 Vous : « Organiser les champs en deux colonnes »
    🤖 AI : « A mis à jour la disposition pour afficher les champs dans une disposition à deux colonnes »
    
    👤 Vous : « A converti en disposition en accordéon »
    🤖 AI : « A transformé le formulaire pour utiliser des sections de style accordéon »

**Améliorations de la conception :**

    👤 Vous : « Créez un formulaire de style assistant avec 3 étapes : informations personnelles, préférences et révision »
    🤖 AI : « Création d’un formulaire d’assistant avec trois étapes et une navigation distinctes »
    
    👤 Vous : « Organisez les champs d’adresse dans une disposition compacte à deux colonnes »
    🤖 AI : « Champs d’adresse organisés dans un format compact à deux colonnes »
    
    👤 Vous : « Mettez à jour la disposition pour qu’elle corresponde au cadre filaire joint »
    🤖 AI : « Modification de la disposition pour qu’elle corresponde à la référence de conception fournie »

### Envoyer la configuration

Forms Experience Builder peut configurer différents points d’entrée d’envoi pour connecter vos formulaires à des systèmes et services externes :

| Type d’action Envoyer | Commande de configuration | Cas d’utilisation |
|------------------|---------------|----------|
| **E-mail** | « Envoie le formulaire par e-mail. » | Notifications et confirmations pour les envois de formulaire |
| **API REST** | « Envoie vers le point d’entrée REST. » | Applications personnalisées et systèmes tiers |
| **Espace de stockage dans le cloud** | « Enregistrer sur Azure/SharePoint. » | Stockage de documents et gestion de fichiers |
| **Workflow** | « Connecter à Power Automate. » | Automatisation et approbations des processus métier |
| **Marketing** | « Intégrer à Marketo. » | Automatisation de la gestion des leads et du marketing |

**Exemples de configuration d’envoi avancée :**

    👤 Vous : « Envoyer des envois de formulaire à hr@company.com et créer un dossier dans notre système CRM »
    🤖 AI : « Envoi d’e-mail configuré et action d’envoi CRM »
    
    👤 Vous : « Envoyer des données à notre point d’entrée de l’API REST et déclencher le nouveau workflow client »
    🤖 AI : « Configurer l’envoi de l’API REST avec des déclencheurs de workflow »
    
    👤 Vous : « Envoyer des réponses par e-mail à l’équipe commerciale et ajouter le prospect à notre plateforme d’automatisation marketing »
    🤖 AI : « Envoi multicanal configuré avec automatisation des e-mails et du marketing »





## Opérations de formulaire avancées


### Création de règles complexes

Créez une validation sophistiquée et une logique commerciale qui répond aux interactions des utilisateurs et utilisatrices et garantit l’intégrité des données :

    👤 vous : « Afficher la section d’adresse uniquement si l’utilisateur sélectionne « Adresse de livraison différente » »
    🤖 AI : « Création d’une règle conditionnelle qui affiche/masque le panneau d’adresse en fonction de la sélection de la case à cocher »

### Création de formulaire à plusieurs étapes

    👤 vous : « Créer un formulaire progressif avec 3 étapes : informations personnelles, préférences, confirmation »
    🤖 AI : « Création d’un formulaire progressif avec une navigation entre les étapes et la validation à chaque étape »

### Types de champs avancés

* Chargement de fichier avec validation et restrictions de taille pour la gestion des documents
* Sélecteurs de date avec contraintes et règles métier pour la planification
* Listes déroulantes avec des options dynamiques qui changent en fonction des sélections des utilisateurs et utilisatrices
* Cases d’option avec logique conditionnelle pour arbres de décision complexes


### Conversion de PDF en formulaire

    👤 : « Convertir ce PDF en formulaire interactif »
    🤖 IA : « Analyser le PDF et créer un formulaire avec les types de champs et la validation appropriés »





## Formation et aide sur les produits

Forms Experience Builder peut également vous apprendre à utiliser les fonctionnalités d’AEM Forms :

### Posez des questions telles que :

* « Comment créer un formulaire à plusieurs étapes ? »
* « Quelle est la différence entre les panneaux et les sections ? »
* « Comment configurer les notifications par e-mail ? »
* « Quelles sont les bonnes pratiques concernant les formulaires compatibles avec les appareils mobiles ? »
* « Comment appliquer des thèmes à mes formulaires ? »

### Obtenir de l’aide sur :

* Concepts et terminologie d’AEM Forms
* Instructions détaillées relatives aux fonctionnalités complexes
* Bonnes pratiques et recommandations
* Résolution des problèmes courants


Pour obtenir une assistance supplémentaire, consultez la [bibliothèque principale d’invites de Forms Experience Builder](/help/forms/experience-builder/forms-experience-builder-prompt-examples-library.md) ou contactez l’administrateur ou l’administratrice du système pour une assistance technique.
