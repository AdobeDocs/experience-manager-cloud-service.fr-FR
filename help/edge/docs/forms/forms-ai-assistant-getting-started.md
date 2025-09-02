---
title: Prise en main de Forms Experience Builder
description: Découvrez comment utiliser Forms Experience Builder pour créer et gérer des formulaires avec divulgation progressive pour tous les types d’utilisateurs
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: fe34b44d02c308e7d18a08dd05f21abc67bd0cb2
workflow-type: tm+mt
source-wordcount: '2013'
ht-degree: 6%

---


# Prise en main de Forms Experience Builder

>[!NOTE]
>
> La fonctionnalité Forms Experience Builder est disponible dans le cadre du programme **Accès anticipé (EA)**. Si vous êtes intéressé, envoyez un e-mail rapide à partir de votre adresse professionnelle à `aem-forms-ea@adobe.com` pour demander l’accès à la fonctionnalité.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette documentation est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les fonctionnalités, commandes et exemples peuvent changer à mesure que le Forms Experience Builder continue d’évoluer pendant le programme d’accès anticipé.

Ce guide complet vous aide à commencer à créer et gérer des formulaires à l’aide de la technologie d’IA conversationnelle. Que vous soyez un débutant à la recherche de la création de votre premier formulaire ou un utilisateur expérimenté cherchant à tirer parti de fonctionnalités sophistiquées, vous trouverez des informations détaillées et des exemples pratiques pour guider votre parcours à travers les fonctionnalités du Forms Experience Builder.

## Conditions préalables et configuration

### &#x200B;1. Demander l’accès

Forms Experience Builder est actuellement disponible dans le cadre du programme d’accès anticipé (EA). Pour participer et y accéder, vous aurez besoin des informations suivantes :

**Informations requises**

- **ID d’organisation IMS** : identifiant de votre organisation Adobe
- **ID de programme** : identifiant de programme spécifique dans Adobe Experience Cloud
- **Détails du projet** : calendrier, portée et cas d’utilisation prévus
- **E-mail professionnel officiel** : associé au compte Adobe de votre entreprise

**Comment obtenir l’identifiant de l’organisation IMS et l’identifiant du programme**

Pour obtenir des instructions détaillées afin de localiser votre ID d’organisation IMS et votre ID de programme, voir :

- [Guide de configuration de l’organisation Adobe Experience Cloud](/help/onboarding/cloud-manager-introduction.md)
- [Gestion des programmes et de l&#39;environnement](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)

**Demander l’accès**

1. Rassemblez votre identifiant d’organisation IMS et votre identifiant de programme à l’aide des guides ci-dessus
2. Envoyer un e-mail à [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) pour demander l’accès
3. Inclure dans votre demande :
   - Nom de l’organisation et ID de l’organisation IMS
   - ID de programme
   - Chronologie et portée du projet
   - Cas d’utilisation prévus et objectifs commerciaux

>[!IMPORTANT]
>
> **Programme de disponibilité limitée** : l’accès à Forms Experience Builder est soumis à l’approbation des parties prenantes internes. Adobe examinera votre demande en fonction de la capacité du programme et de l&#39;alignement sur les critères d&#39;accès anticipé. L’approbation n’est pas garantie et dépend de la disponibilité actuelle du programme.

### &#x200B;2. Vérifiez que Forms est activé

Avant d’utiliser Forms Experience Builder, vérifiez qu’[AEM Forms est activé pour votre environnement](/help/forms/setup-forms-cloud-service.md).


### &#x200B;3. Configuration De Votre Environnement


- **Pour Edge Delivery Services (EDS) :**

   - [Configuration de l’environnement pour Edge Delivery Services Forms](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)
   - [Création d’un formulaire à partir du modèle Edge Delivery Forms](/help/edge/docs/forms/universal-editor/create-forms.md)

- **Pour les formulaires basés sur les composants principaux :**

   - Sur votre instance Adobe Experience Manager, accédez à Forms > Forms et documents
   - [Créer une page à l’aide du modèle de composants principaux](/help/forms/creating-adaptive-form-core-components.md)


## Démarrage rapide

### Accès au Forms Experience Builder

Forms Experience Builder est disponible dans l’interface utilisateur de gestion de Forms, l’éditeur universel et l’éditeur de Forms adaptatif. Vous pouvez utiliser l’une de ces méthodes pour accéder au formulaire :

**Interface utilisateur de gestion de Forms (pour les composants principaux)**

1. **Accédez à Forms** : accédez à AEM > Forms > Forms et documents.
1. Cliquez sur l’icône Forms Experience Builder dans la barre d’outils. Il se trouve près du coin supérieur gauche de l’interface utilisateur.
   ![Icône de l’assistant IA*](/help/edge/docs/forms/assets/forms-manager.gif){width="50%"}
1. Commencer la création du formulaire de conversation


**Éditeur de Forms adaptatif (pour les composants principaux)**

1. Accédez à AEM > Forms > Forms et documents .
2. [Créer un formulaire à l’aide du modèle Composants principaux](/help/forms/creating-adaptive-form-core-components.md)
3. Ouvrez le formulaire pour le modifier
4. Cliquez sur l’icône Forms Experience Builder dans la barre d’outils de l’éditeur
   ![Icône de l’assistant IA*](/help/edge/docs/forms/assets/adaptive-forms-editor.gif){width="75%"}

5. Commencer la création du formulaire de conversation


**Éditeur universel (pour Edge Delivery Services Forms)**

1. Suivez le guide de configuration de [Edge Delivery Services](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md) pour créer votre page EDS
1. Accédez à la page EDS dans l’éditeur universel.
1. Recherchez l’icône Forms Experience Builder dans le panneau de droite
1. Cliquer pour ouvrir l’interface de conversation



### Votre premier formulaire

| Exemple de conversation |   |
|--------------------------------------------------------------------------------------------------------------------------------------------|---|
| **Essayez cette conversation pour créer un formulaire de contact complet (basé sur la démonstration de Summit) :**<br><br>**Vous :** « Créez un formulaire de contact pour capturer des informations personnelles, y compris le nom complet, l’adresse e-mail, le numéro de téléphone, le nom de la société, l’intitulé de la fonction et un champ de message pour les demandes »<br><br>**AI :** sélectionnez un modèle<br>    Liste déroulante pour sélectionner un modèle <br><br>**AI :** un thème<br>    Liste déroulante pour sélectionner un thème <br><br>**AI :** Créer un formulaire | ![Votre Premier Formulaire](/help/edge/docs/forms/assets/create-form.png) |
| <br>**AI:** Ouvrir le formulaire créé | </br> Le formulaire est créé et ouvert dans l’éditeur |


### Commandes Essentielles

| Symbole | Objectif | Exemple d’utilisation |
|--------|---------|---------------|
| `/` | Actions rapides et raccourcis | `/create-form contact form`, `/help validation rules`, `/update-layout wizard` |
| `@` | Référencer les champs de formulaire existants | `@email`, `@firstName`, `Make @phoneNumber required` |
| Texte brut | Conversation naturelle | « Ajouter un champ de numéro de téléphone obligatoire », « Créer une validation pour l’e-mail » |

**Exemples de commandes spécifiques :**

- `/create-form customer survey` - Crée un formulaire d’enquête auprès des clients
- `/add-field @email validation` - Ajoute la validation au champ d’e-mail existant
- `/create-rule show @spouse if @maritalStatus equals married` - Crée une logique conditionnelle
- `/configure-submit to email support@company.com` - Configuration de l’envoi d’e-mails
- `/help multi-step forms` - Obtient de l’aide sur la création de formulaires à plusieurs étapes

### Conseils pour réussir

- **Soyez précis** : « Ajouter un champ d’e-mail obligatoire avec validation » fonctionne mieux que « Ajouter un e-mail »
- **Référencer des champs existants** : utiliser des `@fieldName` lors de la modification de formulaires
- **Demander de l’aide** : saisissez `/help` suivi de votre question
- **Itérer** : effectuez une modification à la fois pour obtenir de meilleurs résultats


## Méthodes de création d’un formulaire

### &#x200B;1. Commencez par les invites en langage naturel

Décrivez les exigences de votre formulaire en langage naturel. Forms Experience Builder génère ensuite la structure complète du formulaire :

**Exemples :**

- « Créez un formulaire de demande de prêt avec des informations personnelles, des détails financiers et des chargements de documents. »
- « Créer un formulaire de commentaires des clients avec des évaluations, des commentaires et des catégories de produits »
- « J&#39;ai besoin d&#39;un formulaire d&#39;inscription en plusieurs étapes pour une conférence avec traitement des paiements »

### &#x200B;2. Importer et convertir

Transformez les formulaires et documents existants en expériences modernes et interactives :

**Sources prises en charge :**

- **PDF forms** : chargez des PDF statiques pour les convertir en formulaires numériques interactifs avec validations.
- **Captures d’écran ou images** : chargez une photo de formulaires papier pour générer des versions numériques fonctionnelles
- **XFA Forms** : convertir des formulaires XFA hérités en formulaires réactifs modernes

**Importer :**

1. Cliquez sur l’icône de pièce jointe dans l’interface de Forms Experience Builder
2. Chargez votre fichier (PDF, image, conception Figma, etc.)
3. Décrivez vos exigences :
   - « Convertir ce formulaire PDF en version numérique »
   - « Créer un formulaire correspondant à cette disposition de capture d’écran »
   - « Crée ce formulaire à partir de mon design Figma. »

**Types de fichiers pris en charge :**

- **Images** (PNG, JPG, GIF) : dispositions de formulaires, maquettes d’interface utilisateur, formulaires numérisés, schémas dessinés à la main
- **Fichiers PDF** : formulaires existants, spécifications, documents, Acroforms, formulaires XFA
- **Captures d’écran** : captures d’écran d’applications de bureau ou mobiles, photos de formulaires papier, schémas de tableaux blancs
- **Croquis dessinés à la main** : croquis de serviettes, maquettes, dessins de concept (photographiés)

### Interactions clés

#### Ajout d’éléments au formulaire

**Ajouts de base :**

    👤 Vous : « Ajouter une section pour les informations personnelles »
    👤 Vous : « Inclure un téléchargement de fichier pour un CV »
    👤 Vous : « Ajouter une liste déroulante pour la sélection de pays »

**Spécifications détaillées :**

    👤 Vous : « Ajoutez un panneau d’informations personnelles avec des champs pour le nom complet, la date de naissance, le numéro de téléphone et l’adresse e-mail »
    👤 Vous : « Incluez un composant de chargement de fichier sécurisé pour les documents, limité aux fichiers PDF de moins de 5 Mo »
    👤 Vous : « Ajoutez une liste déroulante par pays avec des options pour les États-Unis, le Canada, le Royaume-Uni et l’Allemagne »

#### Création d’un comportement dynamique

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

#### Mise en page et conception de formulaire

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

Forms Experience Builder peut configurer différents points d’entrée d’envoi pour connecter vos formulaires à des systèmes et services externes :

| Type d’action Envoyer | Commande d&#39;installation | Cas d’utilisation |
|------------------|---------------|----------|
| **E-mail** | « Envoyer le formulaire à un e-mail » | Notifications et confirmations pour les envois de formulaire |
| **API REST** | « Envoyer vers le point d’entrée REST » | Applications personnalisées et systèmes tiers |
| **Espace de stockage** | « Enregistrer sur Azure/SharePoint » | Stockage de documents et gestion de fichiers |
| **Workflow** | « Se connecter à Power Automate » | Automatisation et approbations des processus métier |
| **Marketing** | « Intégration à Marketo » | Automatisation de la gestion des leads et du marketing |

**Exemples de configuration d’envoi avancée :**

    👤 Vous : « Envoyer des envois de formulaire à hr@company.com et créer un dossier dans notre système CRM »
    🤖 AI : « Envoi d’e-mail configuré et action d’envoi CRM »
    
    👤 Vous : « Envoyer des données à notre point d’entrée de l’API REST et déclencher le nouveau workflow client »
    🤖 AI : « Configurer l’envoi de l’API REST avec des déclencheurs de workflow »
    
    👤 Vous : « Envoyer des réponses par e-mail à l’équipe commerciale et ajouter le prospect à notre plateforme d’automatisation marketing »
    🤖 AI : « Envoi multicanal configuré avec automatisation des e-mails et du marketing »





## Opérations de formulaire avancées


### Création de règles complexes

Créez une validation sophistiquée et une logique commerciale qui répond aux interactions des utilisateurs et assure l’intégrité des données :

    👤 vous : « Afficher la section d’adresse uniquement si l’utilisateur sélectionne « Adresse de livraison différente » »
    🤖 AI : « Création d’une règle conditionnelle qui affiche/masque le panneau d’adresse en fonction de la sélection de la case à cocher »

### Création de formulaire à plusieurs étapes

    👤 vous : « Créer un formulaire progressif avec 3 étapes : informations personnelles, préférences, confirmation »
    🤖 AI : « Création d’un formulaire progressif avec une navigation entre les étapes et la validation à chaque étape »

### Types de champs avancés

- Chargement de fichier avec validation et restrictions de taille pour la gestion des documents
- Sélecteurs de date avec contraintes et règles de gestion pour la planification
- Listes déroulantes avec des options dynamiques qui changent en fonction des sélections de l’utilisateur
- Cases d&#39;option avec logique conditionnelle pour arbres de décision complexes


### Conversion de PDF en formulaire

    👤 : « Convertir ce PDF en formulaire interactif »
    🤖 IA : « Analyser le PDF et créer un formulaire avec les types de champs et la validation appropriés »





## Aide sur les produits et apprentissages

Forms Experience Builder peut également vous apprendre à utiliser les fonctionnalités d’AEM Forms :

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

## Bonnes pratiques

### Conception de formulaire

- **Restez simple** : commencez par les champs essentiels et ajoutez de la complexité uniquement lorsque cela est nécessaire pour éviter de surcharger les utilisateurs
- **Utiliser des libellés clairs** : rendez les objectifs des champs évidents avec des libellés descriptifs qui guident les utilisateurs et les utilisatrices tout au long du formulaire
- **Fournir un texte d’aide** : guide les utilisateurs à travers des champs complexes avec une aide contextuelle et des exemples
- **Test approfondi** : validez tous les chemins d’accès utilisateur pour vous assurer que les formulaires fonctionnent correctement dans tous les scénarios.

### Expérience utilisateur

- **Divulgation progressive** : afficher les champs pertinents en fonction du contexte pour réduire la charge cognitive et améliorer les taux d’achèvement
- **Navigation claire** : aidez les utilisateurs et les utilisatrices à comprendre où ils se trouvent dans le formulaire et quelles étapes restent
- **Conception réactive** : assurez-vous que les formulaires fonctionnent sur tous les appareils et toutes les tailles d’écran pour une accessibilité maximale
- **Accessibilité** : suivez les directives WCAG pour rendre les formulaires utilisables par les personnes en situation de handicap

### Performance

- **Optimiser le nombre de champs** : demandez uniquement les informations nécessaires pour réduire l’abandon de formulaire et améliorer les taux d’achèvement
- **Utiliser une validation appropriée** : prévenir les erreurs avant l’envoi pour fournir des commentaires et des conseils immédiats
- **Taux d’achèvement des tests** : surveiller et améliorer l’efficacité des formulaires par le biais d’analyses et des commentaires des utilisateurs
- **Mises à jour régulières** : maintenez les formulaires à jour avec les besoins de l’entreprise et les attentes des utilisateurs pour des performances optimales

### Cohérence de la marque

- **Créer des modèles de marque** : préparez les modèles de formulaire de marque avec les couleurs, les polices et le style de votre entreprise avant de commencer la création de formulaire
- **Définir des normes de style** : définissez des styles de bouton, une disposition des champs et des instructions d’espacement cohérents qui peuvent être référencés dans les invites
- **Utiliser des ressources de marque** : préparez les logos, les codes couleur et les directives de la marque pour une référence facile lors de la création de formulaires
- **Bibliothèque de modèles** : créez une collection de modèles de formulaire de marque pour les cas d’utilisation courants (contact, enregistrement, commentaires).
- **Invites de style** : incluez des instructions spécifiques à la marque : « Utiliser le bleu de la société (#1234AB) pour les boutons et les polices d’entreprise Helvetica »



## Résolution des problèmes

| Problème | Quick Fix |
|-------|-----------|
| **Interface non chargée** | Actualiser le navigateur, vérifier la connexion Internet |
| **Les commandes ne fonctionnent pas** | `/help` ou utilisez plutôt le langage naturel |
| **@fieldName non reconnu** | Vérifier l’orthographe et s’assurer que le champ existe en premier |
| **Échec du chargement du fichier** | Utilisez PDF/JPG/PNG de moins de 10 Mo. |
| **L’apparence du formulaire est incorrecte** | Soyez plus précis : « Rendez-le compatible avec les appareils mobiles » |
| **Échec de la configuration d’envoi** | Vérification des informations d’identification et des autorisations d’API |

**Vous avez encore besoin d&#39;aide ?** Type `/help` suivi de votre question spécifique ou contactez votre administrateur système.

Pour obtenir une assistance supplémentaire, reportez-vous à la [bibliothèque d’invites de Forms Experience Builder principale](ai-assistant-prompt-library.md) ou contactez votre administrateur système pour obtenir de l’aide technique.
