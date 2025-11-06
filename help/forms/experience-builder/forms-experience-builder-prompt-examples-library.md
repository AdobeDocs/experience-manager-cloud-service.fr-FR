---
title: Forms Experience Builder - Bibliothèque de prompts
description: Collection de modèles de prompts et d’exemples éprouvés pour créer des formulaires avec l’aide de l’IA dans l’interface d’utilisation de gestion de Forms, l’éditeur de formulaires adaptatifs et l’éditeur universel.
hide: true
index: false
hidefromtoc: true
role: Admin, Developer
exl-id: 48eb137c-fe12-4e4f-b845-3321ca8b6075
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '2193'
ht-degree: 99%

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

- **Modèles de marque** : préparez des modèles de formulaire standardisés avec les couleurs, les polices et les modèles de disposition de votre entreprise.
- **Directives de style** : définissez un style de champ, des conceptions de bouton et des normes d’espacement cohérents que le créateur d’expériences de formulaires peut appliquer.
- **Bibliothèque de composants** : travaillez avec votre équipe de développement pour préparer des composants de formulaire réutilisables qui correspondent à votre identité de marque.
- **Ressources visuelles** : préparez les logos, les icônes et les éléments d’arrière-plan pour les intégrer aux formulaires.


## Exemples de développement incrémentiel

Ces exemples montrent comment créer des formulaires pas à pas, en commençant par simplement et en procédant pas à pas :

### Exemple 1 : création pas à pas d’un formulaire de contact

**Étape 1 : démarrer simplement :**

    Crée un formulaire de contact avec des champs de nom, d’adresse e-mail, de téléphone et de message

**Étape 2 : ajouter la validation :**

    Rends les champs @name et @email obligatoires avec la validation appropriée

**Étape 3 : améliorer l’expérience client :**

    Ajoute le texte de l’espace réservé : @name « Votre nom complet », @email « votre.e-mail@entreprise.com » @message « Dites-nous comment nous pouvons vous aider »

**Étape 4 : ajouter des fonctionnalités avancées :**

    Ajoute une liste déroulante queryType avec les options « Question générale », « Demande d’assistance », « Demande commerciale », « Partenariat »

**Étape 5 : implémenter une logique conditionnelle :**

    /create-rule – Affiche la liste déroulante @urgencyLevel (faible, moyen, élevé) uniquement lorsque @inquiryType est égal à « Demande d’assistance »

### Exemple 2 : création pas à pas d’un formulaire d’enregistrement

**Étape 1 : structure de base :**

    Crée un formulaire d’enregistrement d’utilisateur ou utilisatrice avec le panneau d’informations personnelles

**Étape 2 : ajouter des champs obligatoires :**

    Ajoutez des champs pour @firstName, @lastName, @email et @phoneNumber avec la validation appropriée

**Étape 3 : ajouter une logique commerciale :**

    Crée une règle : si @age est inférieur à 18 ans, affiche la section d’informations sur le parent ou la parente, ou le tuteur ou la tutrice

**Étape 4 : améliorer avec des préférences :**

    Ajoute un panneau de préférences avec @newsletterSubscription, @marketingConsent, @termsAccepted

**Étape 5 : ajouter le chargement de fichier :**

    Inclus un champ de chargement de fichier pour @profilePicture avec une taille limitée à 5 Mo

## Création et gestion de formulaires

**Contexte d’utilisation :** lorsque vous devez créer de nouveaux formulaires ou modifier des formulaires existants.

**Utilisation :** choisissez l’une des deux approches suivantes : Créer en partant de zéro ou Importer et convertir (voir [Guide de prise en main](/help/forms/experience-builder/forms-experience-builder-getting-started.md).

**Exemple de prompt : création simple de formulaire :**

    Créez un formulaire de commentaires client avec :
    - Une évaluation du produit (1 à 5 étoiles)
    - Un champ de commentaire pour des commentaires détaillés
    - L’adresse e-mail du client ou de la cliente (facultatif)
    - Un envoi d’une notification par e-mail lors de la soumission

**Exemple de prompt : création de formulaire complexe :**

    Créez un formulaire complet d’intégration du personnel comprenant les éléments suivants :
    
    **Informations personnelles :**
    - Nom complet (prénom, deuxième prénom, nom de famille)
    - Date de naissance avec validation de l’âge
    - Coordonnées (e-mail, téléphone, adresse)
    - Contact d’urgence
    
    **Détails de l’emploi :**
    - Sélection du poste et du service
    - Date de début avec validation des jours ouvrables
    - Informations salariales avec mention de confidentialité
    - Structure hiérarchique
    
    **Chargement de documents :**
    - C.V. (PDF, DOC, DOCX)
    - Documents d’identité pour vérification
    - Formulaires fiscaux et informations bancaires
    - Contrat de travail signé
    
    **Préférences :**
    - Choix des avantages avec calculateur de coûts
    - Préférences d’horaires de travail
    - Besoins en formation
    - Besoins en équipement
    
    **Règles de validation :**
    - Validation du format de l’e-mail
    - Validation du format du numéro de téléphone
    - L’âge doit être de 18 ans ou plus
    - Tous les documents requis doivent être chargés
    - Les conditions générales doivent être acceptées
    
    **Actions d’envoi :**
    - Envoyer un e-mail de confirmation au nouvel employé ou à la nouvelle employée
    - Notifier le service RH
    - Créer le dossier de la personne employée dans le système RH
    - Planifier la réunion d’orientation

**Prompts de gestion des formulaires :**

    Importez ce formulaire de candidature PDF et convertissez-le en formulaire adaptatif avec une validation améliorée
    
    Mettez à jour le formulaire de contact existant pour inclure les identifiants de réseaux sociaux et la méthode de contact préférée
    
    Réorganisez le formulaire d’inscription en un assistant en 3 étapes : informations personnelles, préférences, confirmation

## Gestion et validation des champs

**Contexte d’utilisation :** lorsque vous devez ajouter, modifier ou configurer des champs de formulaire.

**Méthode d’utilisation :** soyez précis lorsque vous travaillez sur les types de champs, les règles de validation et les attentes en matière d’expérience d’utilisation.

**Exemple de prompt : ajout d’un champ de base :**

    Ajoutez un champ de saisie de texte pour « Nom de la société » avec l’espace réservé « Saisissez le nom de votre société. »

**Exemple de prompt : configuration avancée des champs :**

    Ajoutez une section complète d’adresse avec les éléments suivants :
    
    **Rue :**
    - Ligne d’adresse 1 (obligatoire, maximum 100 caractères)
    - Ligne d’adresse 2 (facultatif, maximum 100 caractères)
    - Ville (obligatoire, liste déroulante de villes courantes)
    - État/province (obligatoire, liste déroulante)
    - Code postal (obligatoire, validation du format)
    - Pays (obligatoire, valeur par défaut définie sur « France »)
    
    **Règles de validation :**
    - Le code postal doit correspondre à l’état sélectionné
    - La ligne d’adresse 1 ne doit pas être vide
    - La ville doit être valide pour l’état sélectionné
    
    **Expérience d’utilisation :**
    - Saisie semi-automatique pour les champs d’adresse
    - Libellés clairs et texte d’aide
    - Champs de saisie adaptés aux appareils mobiles
    - Conformité en matière d’accessibilité

**Prompts de configuration de champs :**

    Rendez le champ @email obligatoire avec une validation en temps réel et un message d’erreur personnalisé
    
    Ajoutez un menu déroulant pour @country avec les options États-Unis, Canada, Royaume-Uni, Allemagne, France et « Autre »
    
    Configurez le champ @phoneNumber avec le format (XXX) XXX-XXXX et une validation
    
    Ajoutez un champ de chargement de fichier pour @resume, limité aux formats PDF et DOC, avec une taille maximale de 5 Mo

## Champs intelligents améliorés par LLM

**Contexte d’utilisation :** lorsque vous avez besoin de champs avec des options préremplies qui exploitent la base de connaissances de l’IA.

**Méthode d’utilisation :** demandez champs qui nécessitent des jeux de données complets. L’IA peut renseigner automatiquement les options à l’aide de ses connaissances intégrées.

### Champs géographiques et de localisation

**Aéroports et transports :**

    Ajoutez un menu déroulant pour les aéroports de départ avec tous les principaux aéroports internationaux
    Ajoutez le champ de l’aéroport d&#39;arrivée avec les codes IATA et les noms complets
    Créez un champ pour l’aéroport le plus proche de l’emplacement de l’utilisateur ou de l’utilisatrice
    Ajoutez une sélection de gares pour les villes européennes

**Régions administratives :**

    Ajoutez une liste complète des États américains avec des abréviations
    Créez une liste déroulante de pays avec des codes ISO et des noms complets
    Ajoutez un champ pour les grandes villes du monde avec des fuseaux horaires
    Incluez une liste déroulante des provinces et territoires canadiens
    Ajoutez un champ pour les comtés et zones postales du Royaume-Uni

### Données relatives aux entreprises et au secteur

**Classifications des entreprises :**

    Ajoutez un champ pour la classification des industries avec les codes SCIAN
    Créez une liste déroulante des types d’entités commerciales (SARL, société, partenariat, etc.)
    Ajoutez un champ pour les catégories de taille d’entreprise (startup, PME, société)
    Incluez la sélection de service pour les grandes organisations
    Ajoutez un champ pour les types de services professionnels

**Classifications professionnelles :**

    Ajoutez un champ pour les intitulés de poste avec des rôles courants du secteur
    Créez une liste déroulante des certifications professionnelles par champ
    Incluez les niveaux de formation avec les types de diplômes
    Ajoutez un champ pour les périodes d’expérience
    Créez une sélection pour les langages et les structures de programmation

### Normes et réglementation

**Financier et juridique :**

    Ajoutez un champ pour les codes de devise avec des symboles et des taux de change
    Créez une liste déroulante des types d’identifiants fiscaux par pays
    Incluez un champ pour les types de documents juridiques
    Ajoutez des options de mode de paiement avec des fonctions de sécurité
    Créez une sélection pour les établissements bancaires par pays

**Normes techniques :**

    Ajoutez une liste déroulante des types de formats de fichiers avec leurs extensions
    Incluez des options de protocoles réseau
    Ajoutez un champ pour les types et les versions de bases de données
    Créez une sélection pour les méthodes d’authentification d’API

### Soins de santé et médical

**Classifications médicales :**

    Ajoutez un champ pour les spécialités médicales
    Créer une liste déroulante de médicaments courants avec des noms génériques
    Incluez un champ pour les types de compagnies d’assurance
    Ajoutez une sélection pour les relations de contact en cas d’urgence médicale
    Créez un champ pour les restrictions alimentaires et les allergies

### Intelligence temporelle et calendaire

**Options de date et d’heure :**

    Ajoutez un champ pour les heures ouvrables avec gestion des fuseaux horaires
    Créez une liste déroulante des jours fériés par pays
    Incluez des options saisonnières avec des périodes
    Ajoutez un champ pour la réservation de salle de conférence avec des disponibilités
    Créez une sélection pour les modèles de réunion récurrents

### Catégories de produits et de services

**Classifications d’e-commerce :**

    Ajoutez un champ pour les catégories de produits avec des sous-catégories
    Créez une liste déroulante de modes d’expédition avec des estimations des livraisons
    Incluez un champ pour les options de politique de retour
    Ajoutez une sélection pour les niveaux de priorité des clientes et clients
    Créez un champ pour les cycles de facturation des abonnements

**Exemples de prompts de champ intelligent :**

    « Ajoutez un champ pour l’aéroport de départ comprenant tous les grands aéroports du monde, avec les codes IATA et les noms de villes »
    
    « Créez un champ complet pour le secteur d’activité en utilisant la classification standard NAICS avec des sous-catégories technologiques »
    
    « Incluez une liste déroulante des certifications professionnelles qui s’adapte en fonction du domaine d’emploi sélectionné »
    
    « Ajoutez un champ de numéro de téléphone international qui se met en forme selon le pays sélectionné »
    
    « Créez un champ de sélection d’université avec les principaux établissements classés par pays et par rang »

## Création de règles et logique commerciale

**Contexte d’utilisation :** lorsque vous devez implémenter une logique conditionnelle, des règles de validation ou des processus d’entreprise.

**Méthode d’utilisation :** décrivez clairement la logique commerciale, en spécifiant les conditions et les actions.

**Exemple de prompt : logique conditionnelle simple :**

    Créer une règle qui n’affiche le panneau @spouseInformation que lorsque @maritalStatus est égal à « Marié(e) ».

**Exemple de prompt : règles métier complexes :**

    Mettez en œuvre une validation complète des demandes de prêt :
    
    **Validation des revenus :**
    - Si @annualIncome sont inférieurs à 30 000 :
    - Affichez le message d’avertissement : « Les revenus peuvent être insuffisants pour le montant de prêt demandé »
    - Exigez des documents de revenus supplémentaires
    - Affichez le message : « Des documents supplémentaires peuvent être requis »
    - Si @annualIncome sont supérieurs à 100 000 :
    - Affichez les options des services premium
    - Activez la case à cocher de traitement prioritaire
    
    **Validation en fonction de l’âge :**
    - Si @age est inférieur à 18 :
    - Affichez la section informations du parent/tuteur/tutrice
    - Rendez le téléversement de la signature du parent obligatoire
    - Modifiez le texte du bouton d’envoi en « Envoyer pour révision »
    - Si @age est égal ou supérieur à 65 :
    - Affichez les options de réduction senior
    - Ajoutez une section pour les préférences d’accessibilité

**Prompts spécifiques aux règles :**

    Créez une **règle de visibilité** qui affiche le panneau @spouseInformation uniquement lorsque @maritalStatus est égal à « Marié(e) » ou « Pacsé(e) »
    
    Ajoutez **divulgation progressive** où des questions supplémentaires apparaissent sur la base des réponses précédentes. Commencez par les informations de base, puis affichez les suivis appropriés
    
    Implémentez **les valeurs par défaut intelligentes** où la sélection de @country définit automatiquement les champs associés. Autorisez le remplacement manuel

## Intégration et envoi de données

**Opportunité d’utilisation :** lorsque vous devez connecter des formulaires à des systèmes principaux, des bases de données ou des services externes.

**Méthode d’utilisation :** commencer par la configuration de base de l’envoi, puis ajouter des intégrations supplémentaires de manière incrémentielle. Spécifiez le type d’intégration, les exigences en matière de format de données et les préférences de gestion des erreurs.

**Exemple de prompt : commencer par l’envoi de base :**

    Configure l’envoi du formulaire de base pour @applicationForm :
    
    **Envoi principal :**
    – Envoie les données de formulaire au point d’entrée REST : `/api/v1/applications`
    – Formate les données au format JSON
    – Affiche le message de succès : « Demande envoyée avec succès »
    – Affiche le message d’erreur si l’envoi échoue : « Échec de l’envoi, réessayez »

**Ajoutez ensuite des actions secondaire pas à pas :**

    Ajoute une notification par e-mail à @applicationForm : envoie un e-mail de confirmation à @email adresse avec le numéro de référence de la demande
    
    Ajoute l’intégration CRM à @applicationForm : crée un enregistrement de lead avec @firstName, @lastName, @email et définissez le statut sur « Nouvelle demande »

**Exemple de prompt : envoi multicanal standard :**

    Configure l’envoi de formulaire avec plusieurs destinations de données :
    
    **Envoi principal :**
    – Envoie des données de formulaire au point d’entrée REST : `/api/v1/applications`
    – Inclus l’en-tête d’authentification avec la clé d’API
    – Formate les données au format JSON avec des objets imbriqués pour l’adresse et l’activité
    – Gère la réponse de succès (201) en affichant le message de remerciement
    
    **Actions secondaires :**
    – Envoie un e-mail de notification au demandeur ou à la demandeuse à l’adresse @email
    – Copie les données de la demande dans le système de suivi
    – Déclenche un processus d’approbation
    – Crée un enregistrement dans CRM avec le statut de lead « Nouvelle demande »
    
    **Gestion des erreurs :**
    – En cas d’échec de l’envoi, enregistre les données localement et réessaie
    – Affiche un message d’erreur convivial : « Envoi temporairement indisponible »
    – Fournis une option pour télécharger les données de formulaire en tant que sauvegarde
    – Envoie un e-mail d’alerte à l’équipe d’administration à propos de l’échec de l’envoi
    
    **Flux de succès :**
    – Redirige vers la page de confirmation avec le numéro de référence de la demande
    – Envoie un e-mail de confirmation avec les étapes suivantes
    – Affiche le délai de traitement estimé

**Prompts spécifiques à l’intégration :**

    Connecte ce formulaire au **système CRM** pour créer de nouveaux leads. Mappe @firstName à FirstName, @email sur Email, définis LeadSource sur « Formulaire web » et Status sur « Nouveau »
    
    Configure le **déclencheur de workflow** lorsque le formulaire est envoyé. Transmets toutes les données de formulaire et déclenche le workflow d’approbation avec une notification aux responsables
    
    Configure l’**intégration de la base de données** pour enregistrer les envois de formulaire en tant qu’enregistrements. Crée un dossier pour chaque envoi contenant des documents chargés



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
