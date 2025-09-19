---
title: Forms Experience Builder - Bibliothèque de prompts
description: Collection de modèles de prompts et d’exemples éprouvés pour créer des formulaires avec l’aide de l’IA dans l’interface d’utilisation de gestion de Forms, l’éditeur de formulaires adaptatifs et l’éditeur universel.
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: c8f64082-a23f-4919-ad66-042faad77d31
source-git-commit: de524aeddd5f53cbd713ff0523222966752ebbc0
workflow-type: tm+mt
source-wordcount: '2193'
ht-degree: 38%

---


# Forms Experience Builder - Bibliothèque de prompts

Collection de modèles et d’exemples de prompts réutilisables pour Forms Experience Builder. Cette bibliothèque rationalisée se concentre sur les deux méthodes de création principales (créer à partir de zéro ou importer et convertir) avec une prise en charge améliorée des champs intelligents optimisés par LLM et la cohérence de la marque.

>[!NOTE]
>
> Forms Experience Builder est disponible dans le cadre du programme d’accès anticipé. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque de prompts est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les prompts, les exemples et les bonnes pratiques peuvent changer à mesure que Forms Experience Builder continue d’évoluer dans le cadre du programme des utilisateurs et utilisatrices initiaux.

## Utilisation de cette bibliothèque de prompts

Cette bibliothèque fournit des modèles de prompt réutilisables pour les cas courants de création de formulaires. Pour connaître l’ensemble des bonnes pratiques, consultez le [Guide de prise en main de Forms Experience Builder](/help/forms/experience-builder/forms-experience-builder-getting-started.md).

### Conseils rapides relatifs à cette bibliothèque

- **Commencer par des exemples** : utilisez les prompts fournis comme modèles et adaptez-les à vos besoins.
- **Deux méthodes de création** : choisissez entre Créer à partir de zéro et Importer et convertir.
- **Précision** : ajoutez vos propres détails aux exemples génériques.
- **Tester minutieusement** : toujours valider les résultats dans votre environnement spécifique.

### Modèles et styles de marque

**Préparez les ressources de marque à l’avance pour créer des formulaires cohérents :**

- **Modèles de marque** - Préparez des modèles de formulaire normalisés avec les couleurs, les polices et les modèles de disposition de votre entreprise
- **Instructions de style** - Définissez un style de champ, des conceptions de bouton et des normes d’espacement cohérents que Forms Experience Builder peut appliquer
- **Bibliothèque de composants** - Travaillez avec votre équipe de développement pour préparer des composants de formulaire réutilisables qui correspondent à votre identité de marque
- **Ressources visuelles** : préparez les logos, les icônes et les éléments d’arrière-plan pour les intégrer aux formulaires.


## Exemples de développement incrémentiel

Ces exemples montrent comment créer des formulaires pas à pas, en commençant par simplement et en procédant pas à pas :

### Exemple 1 : création pas à pas d’un formulaire de contact

**Étape 1 : démarrer simplement :**

    Créez un formulaire de contact de base avec des champs de nom, d’e-mail et de message

**Étape 2 : ajouter la validation :**

    Rendre les champs @name et @email obligatoires avec la validation appropriée

**Étape 3 : améliorer l’expérience d’utilisation :**

    Ajoutez le texte de l’espace réservé : @name « Votre nom complet », @email « your.email@company.com » @message « Dites-nous comment nous pouvons vous aider »

**Étape 4 : ajouter des fonctionnalités avancées :**

    Ajoutez une liste déroulante queryType avec les options suivantes : « Question générale », « Demande d’assistance », « Demande de renseignements sur les ventes », « Partenariat »

**Étape 5 : implémenter une logique conditionnelle :**

    /create-rule affiche @urgencyLevel liste déroulante (faible, Medium, élevé) uniquement lorsque la @inquiryType est égale à « Demande d’assistance »

### Exemple 2 : création pas à pas d’un formulaire d’enregistrement

**Étape 1 : structure de base :**

    Créer un formulaire d’enregistrement d’utilisateur avec le panneau Informations personnelles

**Étape 2 : ajouter des champs obligatoires :**

    Ajoutez des champs pour les @firstName, les @lastName, les @email et les @phoneNumber avec la validation appropriée

**Étape 3 : ajouter une logique commerciale :**

    Créer une règle : si @age a moins de 18 ans, afficher la section d’informations sur le parent/tuteur

**Étape 4 : améliorer avec les préférences :**

    Ajouter un panneau de préférences avec @newsletterSubscription, @marketingConsent, @termsAccepted

**Étape 5 : ajouter le chargement de fichier :**

    Incluez un champ de chargement de fichier pour les @profilePicture dont la taille est limitée à 5 Mo

## Création et gestion de formulaires

**Contexte d’utilisation :** lorsque vous devez créer de nouveaux formulaires ou modifier des formulaires existants.

**Utilisation :** choisissez l’une des deux approches suivantes : Créer en partant de zéro ou Importer et convertir (voir [Guide de prise en main](/help/forms/experience-builder/forms-experience-builder-getting-started.md).

**Exemple de prompt : création simple de formulaire :**

    Créer un formulaire de commentaires client avec :
    - Évaluation du produit (1 à 5 étoiles)
    - Champ de commentaire pour des commentaires détaillés
    - E-mail du client (facultatif)
    - Envoyer à une notification par e-mail

**Exemple de prompt : création de formulaire complexe :**

    Créez un formulaire d’intégration complet des employés avec :
    
    **&#x200B;**&#x200B;Section des renseignements personnels :**
    - Nom complet (prénom, milieu, dernier)
    - Date de naissance avec validation de l’âge
    - Coordonnées (adresse e-mail, téléphone, adresse)
    - Coordonnées d’urgence
    
    Coordonnées professionnelles :**
    - Choix du poste et du service
    - Date de début avec validation du jour ouvrable
    - Informations salariales avec avis de confidentialité
    - Structure de déclaration&#x200B;**Chargement du document :**
    
    - Reprise/Chargement du CV (PDF, DOC, DOCX)
    - Documents de vérification de l’identité
    - Formulaires fiscaux et informations bancaires
    - Emploi signé agreement
    **&#x200B;**&#x200B;Préférences:**
    
    - Sélection des avantages avec le calculateur de coûts
    - Préférences du programme de travail
    - Exigences de formation
    - Besoins en équipement
    Règles de validation:**
    
    - Validation du format des e-mails
    - Validation du format des numéros de téléphone
    - Tous les documents requis doivent être chargés
    - Les conditions doivent être acceptées
    **Soumettre des actions:**
    - Envoyer un e-mail de confirmation au nouvel employé
    
    - Notifier le service des RH
    - Créer un enregistrement d’employé dans le système des RH
    - Planifier une réunion d’orientation
     
     

**Prompts de gestion des formulaires :**

    Importez ce formulaire de demande PDF et convertissez-le en formulaire adaptatif avec validation améliorée
    
    Mettez à jour le formulaire de contact existant pour inclure les identifiants de médias sociaux et la méthode de contact préférée
    
    Réorganisez le formulaire d’inscription en un assistant en 3 étapes : informations personnelles, préférences, confirmation

## Gestion et validation des champs

**Contexte d’utilisation :** lorsque vous devez ajouter, modifier ou configurer des champs de formulaire.

**Méthode d’utilisation :** soyez précis lorsque vous travaillez sur les types de champs, les règles de validation et les attentes en matière d’expérience d’utilisation.

**Exemple de prompt : ajout d’un champ de base :**

    Ajoutez un champ de saisie de texte pour « Nom de la société » avec l’espace réservé « Entrez le nom de votre société »

**Exemple de prompt : configuration avancée des champs :**

    Ajoutez une section d’adresse complète avec :
    
    **Adresse postale :**
    - Ligne d’adresse 1 (obligatoire, 100 caractères max.)
    - Ligne d’adresse 2 (facultatif, 100 caractères max.)
    - Ville (obligatoire, liste déroulante avec villes communes)
    - État/Province (obligatoire, liste déroulante)
    - Code postal (obligatoire, validation du format)
    - Pays (obligatoire, valeur par défaut « États-Unis »)
    
    **Règles de validation :**
    - Le code postal doit correspondre à la sélection d’État
    - La ligne d’adresse 1 ne peut pas être vide
    - La ville doit être valide pour l’État sélectionné
    
    **Expérience utilisateur : Saisie automatique pour les champs d’adresse
    - Effacer les libellés et le texte d’aide
    - Champs d’entrée compatibles avec les appareils mobiles
     
     
- Conformité en matière d’accessibilité
**Prompts de configuration de champs :**

    Rendre @email champ obligatoire avec la validation en temps réel et le message d’erreur personnalisé
    
    Ajouter une liste déroulante pour les @country avec des options pour les États-Unis, le Canada, le Royaume-Uni, l’Allemagne, la France et « Autre »
    
    Configurer @phoneNumber champ au format (XXX) XXX-XXXX et validation
    
    Ajouter un champ de chargement de fichier pour les @resume avec des restrictions PDF et DOC, 5 Mo max

## Champs intelligents améliorés par LLM

**Contexte d’utilisation :** lorsque vous avez besoin de champs avec des options préremplies qui exploitent la base de connaissances de l’IA.

**Méthode d’utilisation :** demandez champs qui nécessitent des jeux de données complets. L’IA peut renseigner automatiquement les options à l’aide de ses connaissances intégrées.

### Champs géographiques et de localisation

**Aéroports et transports :**

    Ajouter un menu déroulant pour les aéroports de départ avec tous les principaux aéroports internationaux
    Ajouter le champ de l&#39;aéroport d&#39;arrivée avec les codes IATA et les noms complets
    Créer un champ pour l&#39;aéroport le plus proche de l&#39;emplacement de l&#39;utilisateur
    Ajouter une sélection de gares pour les villes européennes

**Régions administratives :**

    Ajouter une liste complète des États américains avec des abréviations
    Créer une liste déroulante de pays avec des codes ISO et des noms complets
    Ajouter un champ pour les grandes villes du monde avec des fuseaux horaires
    Inclure une liste déroulante des provinces et territoires canadiens
    Ajouter un champ pour les comtés et zones postales du Royaume-Uni

### Données relatives aux entreprises et au secteur

**Classifications des entreprises :**

    Ajoutez un champ pour la classification des industries avec les codes SCIAN
    Créez une liste déroulante des types d&#39;entités commerciales (LLC, Corporation, Société de personnes, etc.)
    Ajouter un champ pour les catégories de taille d’entreprise (démarrage, PME, entreprise)
    Inclure la sélection de service pour les grandes organisations
    Ajouter un champ pour les types de services professionnels

**Classifications professionnelles :**

    Ajoutez un champ pour les titres de poste avec des rôles courants du secteur
    Créez une liste déroulante des certifications professionnelles par champ
    Incluez les niveaux de formation avec les types de diplômes
    Ajoutez un champ pour les périodes d’expérience
    Créez une sélection pour les langages et les structures de programmation

### Normes et réglementation

**Financier et juridique :**

    Ajouter un champ pour les codes devise avec des symboles et des taux de change
    Créer une liste déroulante des types d&#39;ID taxe par pays
    Inclure un champ pour les types de documents juridiques
    Ajouter des options de mode de paiement avec des fonctions de sécurité
    Créer une sélection pour les établissements bancaires par pays

**Normes techniques :**

    Ajout d’une liste déroulante de types de format de fichier avec les extensions
    Inclusion des options de protocole réseau
    Ajout d’un champ pour les types et versions de base de données
    Création d’une sélection pour les méthodes d’authentification d’API

### Soins de santé et médical

**Classifications médicales :**

    Ajouter un champ pour les spécialités médicales
    Créer une liste déroulante de médicaments courants avec des noms génériques
    Inclure un champ pour les types de fournisseurs d’assurance
    Ajouter une sélection pour les relations de contact en cas d’urgence médicale
    Créer un champ pour les restrictions alimentaires et les allergies

### Intelligence temporelle et calendaire

**Options de date et d’heure :**

    Ajouter un champ pour les heures ouvrables avec gestion des fuseaux horaires
    Créer une liste déroulante des jours fériés par pays
    Inclure des options saisonnières avec périodes
    Ajouter un champ pour la réservation de salle de conférence avec disponibilité
    Créer une sélection pour les modèles de réunion récurrents

### Catégories de produits et de services

**Classifications d’e-commerce :**

    Ajouter un champ pour les catégories de produits avec des sous-catégories
    Créer une liste déroulante de modes d’expédition avec des estimations de diffusion
    Inclure un champ pour les options de politique de retour
    Ajouter une sélection pour les niveaux de priorité des clients
    Créer un champ pour les cycles de facturation des abonnements

**Exemples de prompts de champ intelligent :**

    « Ajouter un champ aéroport de départ avec tous les principaux aéroports du monde entier, y compris les codes IATA et les noms de ville »
    
    « Créer un champ industriel complet à l&#39;aide de la classification SCIAN standard avec des sous-catégories technologiques »
    
    « Inclure un menu déroulant de certification professionnelle qui s&#39;adapte en fonction du champ d&#39;emploi sélectionné »
    
    « Ajouter un champ de numéro de téléphone international qui se formate en fonction du pays sélectionné »
    
    « Créer un champ de sélection d&#39;université avec les principaux établissements organisés par pays et classement »

## Création de règles et logique commerciale

**Contexte d’utilisation :** lorsque vous devez implémenter une logique conditionnelle, des règles de validation ou des processus d’entreprise.

**Méthode d’utilisation :** décrivez clairement la logique commerciale, en spécifiant les conditions et les actions.

**Exemple de prompt : logique conditionnelle simple :**

    Créer une règle qui n’affiche le panneau @spouseInformation que lorsque @maritalStatus est égal à « Marié(e) »

**Exemple de prompt : règles métier complexes :**

    Mettre en œuvre une validation complète de la demande de prêt :
    
    **Validation des revenus :**
    - Si la @annualIncome est inférieure à 30000:
    - Afficher le message d’avertissement : « Les revenus peuvent être insuffisants pour le montant du prêt demandé »
    - Exiger une documentation supplémentaire sur les revenus
    - Afficher le message : « Une documentation supplémentaire peut être requise »
    - Si la @annualIncome @age est supérieure à 100000:
    - Afficher les options de services Premium
    - Activer la case à cocher de traitement prioritaire
    
    **Validation en fonction de l’âge :**
    - Si la section d’informations sur le parent/tuteur est inférieure à 18:
    - Rendre le chargement de la signature du parent obligatoire
    - Modifier le texte du bouton sur « Soumettre pour révision »
    - Si @age est 65 dossier:
    - Afficher les options de remise senior
    - Ajouter la section Préférences d’accessibilité
     

**Prompts spécifiques aux règles :**

    Créez une **règle de visibilité** qui affiche @spouseInformation panneau uniquement lorsque l’@maritalStatus est égal à « Marié(e) » ou « Partenariat domestique »
    
    Ajoutez **divulgation progressive** où des questions supplémentaires apparaissent sur la base des réponses précédentes. Commencez par les informations de base, puis affichez les suivis appropriés
    
    Implémentez **les valeurs par défaut intelligentes** où @country sélection définit automatiquement les champs associés. Autoriser le remplacement manuel

## Intégration et envoi de données

**Opportunité d’utilisation :** lorsque vous devez connecter des formulaires à des systèmes principaux, des bases de données ou des services externes.

**Méthode d’utilisation :** commencer par la configuration de base de l’envoi, puis ajouter des intégrations supplémentaires de manière incrémentielle. Spécifiez le type d’intégration, les exigences en matière de format de données et les préférences de gestion des erreurs.

**Exemple de prompt : commencer par l’envoi de base :**

    Configurer l’envoi du formulaire de base pour l’@applicationForm :
    
    **Envoi du Principal :**
    - Envoyer les données de formulaire au point d’entrée REST : `/api/v1/applications`
    - Formater les données au format JSON
    - Afficher le message de succès : « Application envoyée avec succès »
    - Afficher le message d’erreur si l’envoi échoue : « Envoi ayant échoué, veuillez réessayer »

**Ajoutez ensuite des actions secondaire pas à pas :**

    Ajouter une notification par e-mail aux @applicationForm : envoyez un e-mail de confirmation à @email adresse avec le numéro de référence de l’application
    
    Ajoutez l’intégration CRM aux @applicationForm : créez un enregistrement de prospect avec @firstName, @lastName, @email et définissez le statut sur « Nouvelle application »

**Exemple de prompt : envoi multicanal standard :**

**&#x200B; **     Configurer l’envoi de formulaire avec plusieurs destinations de données :
    
    **Envoi de Principal :**
    - Envoyer des données de formulaire au point d’entrée REST : `/api/v1/applications`
    - Inclure l’en-tête d’authentification avec la clé API
    - Formater les données au format JSON avec des objets imbriqués pour l’adresse et l’activité
    - Gérer la réponse de succès (201) en affichant le message de remerciement
    
    **Actions Secondaires :**
    - Envoyer un e-mail de notification au demandeur à @email adresse
    - Copier les données d’application dans le système de suivi
    - Déclencher un processus d’approbation
    - Créer un enregistrement dans CRM avec statut d’application échoue, enregistre les données localement et réessaye
    
    - Affiche un message d’erreur convivial : « Envoi temporairement indisponible »
    - Fournit une option pour télécharger les données de formulaire en tant que sauvegarde
    - Envoie un e-mail d’alerte à l’équipe d’administration à propos de l’échec de l’envoi
    Flux de succès :**
    - Redirige vers la page de confirmation avec le numéro de référence de l’application
    
    - Envoie un e-mail de confirmation avec les étapes suivantes
    - Affiche le délai de traitement estimé
     
     

**Prompts spécifiques à l’intégration :**

    Connectez ce formulaire au système **CRM** pour créer de nouveaux prospects. Mappez @firstName sur FirstName, @email sur Email, définissez LeadSource sur « Web Form » et Status sur « New »
    
    Configurez **déclencheur de workflow** lorsque le formulaire est envoyé. Transmettez toutes les données de formulaire et déclenchez le processus d’approbation avec la notification du responsable
    
    Configurez **l’intégration de la base de données** pour enregistrer les envois de formulaire en tant qu’enregistrements. Créez un dossier pour chaque envoi contenant des documents chargés



## Référence des commandes

### Commandes essentielles

| Commande | Meilleurs cas d’utilisation | Exemple |
|---------|---------------|---------|
| `/create-form` | Démarrage de nouveaux formulaires | `/create-form employee onboarding with personal info and benefits selection` |
| `/add-form` | Ajout de formulaires aux pages | `/add-form newsletter signup with email and preferences` |
| `/update-layout` | Modification de la structure d’un formulaire | `/update-layout wizard with 4 steps: info, preferences, review, confirm` |
| `/update-field` | Modification des propriétés des champs | `/update-field @email to be mandatory with real-time validation` |
| `/create-rule` | Ajout d’un comportement dynamique | `/create-rule show @spouseInfo if @maritalStatus equals "Married"` |
| `/create-panel` | Organisation des sections de formulaire | `/create-panel Employment Details with job title, company, salary fields` |
| `/add-panel` | Conversion de conceptions | `/add-panel from uploaded form image with field recognition` |
| `/help` | Obtention d’assistance | `/help how to implement multi-step validation?` |

### Références des champs

Utilisez la syntaxe `@fieldName` pour référencer les champs existants dans vos prompts :

- `@email` - Champ E-mail de référence
- `@firstName` - Champ Prénom de référence
- `@maritalStatus` - Champ État civil de référence

### Types de composants

**Composants d’entrée :**

- `text`, `email`, `number`, `tel`, `date`, `checkbox`, `radio`, `dropdown`, `file`, `textarea`

**Composants de conteneur :**

- `fieldset`, `panel`, `repeatable`, `wizard`

### Propriétés des composants

**Propriétés universelles (tous les composants)**

- **Type** : type de composant
- **Nom** : identifiant du champ pour l’envoi du formulaire
- **Libellé** : texte d’affichage du champ
- **Description** : texte d’aide pour le champ
- **Visible** : booléen pour la visibilité initiale
- **Obligatoire** : valeur booléenne pour les champs obligatoires

**Propriétés des champs d’entrée :**

- **Valeur** : valeur par défaut/initiale
- **Espace réservé** : texte d’indice pour les champs de saisie
- **Min.** : valeur minimale (pour les nombres/dates)
- **Max.** : valeur maximale (pour les nombres/dates)

**Propriétés de chargement de fichier :**

- **Accepter** : types de fichiers (.pdf, .doc, .docx, .jpg, .png, etc.)
- **Multiple** : valeur booléenne pour la sélection de plusieurs fichiers

**Propriétés du contrôle de sélection :**

- **Options** : choix des listes déroulantes (liste séparée par des virgules)
- **Coché** : sélection par défaut des cases à cocher/cases d’option

**Propriétés du conteneur :**

- **Fieldset** : regroupement des champs associés
- **Répétable** : valeur booléenne pour les sections répétables

**Propriétés avancées :**

- **Expression visible** : formule de visibilité conditionnelle (=formule)
- **Expression de valeur** : formule pour les valeurs calculées (=formule)

### Commandes d’intégration

**Actions d’envoi :**

- Notifications par e-mail
- Envois de l’API REST
- Espace de stockage dans le cloud (Azure, SharePoint)
- Automatisation des workflows (Power Automate, Workfront Fusion)
- Plateformes marketing (Marketo)
- Intégrations CRM

### Instructions relatives à la syntaxe des prompts

- **Références de champ** : utilisez `@fieldName` pour les champs existants.
- **Commandes** : utilisez `/command` pour des actions spécifiques.
- **Langage naturel** : décrivez les exigences de manière claire et spécifique.

### Liste de contrôle de validation :

Pour consulter les bonnes pratiques et les instructions relatives à la validation, consultez le [Guide de prise en main de Forms Experience Builder](/help/forms/experience-builder/forms-experience-builder-getting-started.md).

*Cette bibliothèque de prompts est continuellement mise à jour en fonction des commentaires des utilisateurs et utilisatrices et des nouvelles fonctionnalités de Forms Experience Builder. Pour consulter les derniers exemples et fonctionnalités, consultez la [documentation d’AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html?lang=fr).*
