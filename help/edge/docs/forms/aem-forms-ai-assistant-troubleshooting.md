---
title: Forms Experience Builder - Guide de résolution des problèmes
description: Guide de résolution des problèmes complet pour Forms Experience Builder, couvrant les problèmes courants, les solutions et les techniques de débogage pour la création et la gestion des formulaires.
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: 6a7810fd-2860-410b-867d-8d29afd5297d
source-git-commit: fe34b44d02c308e7d18a08dd05f21abc67bd0cb2
workflow-type: tm+mt
source-wordcount: '2282'
ht-degree: 100%

---


# Forms Experience Builder - Guide de résolution des problèmes

>[!NOTE]
>
> Forms Experience Builder est disponible dans le cadre du programme d’accès anticipé. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : ce guide de résolution des problèmes est en cours de test produit. Il est sujet à des mises à jour et des révisions. Les problèmes, les solutions et les techniques de débogage peuvent changer à mesure que Forms Experience Builder continue d’évoluer pendant le programme d’accès anticipé.

Ce guide de résolution des problèmes complet permet d’identifier, de diagnostiquer et de résoudre les problèmes courants rencontrés lors de l’utilisation de Forms Experience Builder. Le guide est organisé par catégories de problèmes avec des correctifs rapides et des solutions détaillées.

## Référence rapide - Problèmes courants

| Problème | Correctif rapide |
|-------|-----------|
| **L’interface ne se charge pas.** | Actualiser le navigateur, vérifier la connexion Internet, vérifier les autorisations d’accès anticipé |
| **Les commandes ne fonctionnent pas.** | Essayer `/help` ou utiliser le langage naturel au lieu des commandes à barre oblique |
| **@fieldName n’est pas reconnu** | Vérifier l’orthographe, s’assurer d’abord que le champ existe, vérifier la syntaxe du nom du champ |
| **Le chargement du fichier échoue.** | Utiliser un fichier PDF/JPG/PNG de moins de 10 Mo, vérifier la compatibilité du format du fichier |
| **Le formulaire semble incorrect.** | Préciser : « Le rendre compatible avec les appareils mobiles » au lieu de « Corriger la mise en page » |
| **L’intégration échoue** | Vérifier les informations d’identification et les autorisations d’API, vérifier la disponibilité du point d’entrée |
| **Le formulaire n’est pas envoyé.** | Vérifier la configuration de l’action Envoyer et les règles de validation |
| **Des erreurs de validation ne s’affichent pas** | Vérifier les paramètres de validation des champs et l’emplacement des messages d’erreur |
| **Problèmes de mise en page pour appareils mobiles** | Vérifier les paramètres de conception réactive et le dimensionnement des champs |
| **Les champs n’apparaissent pas** | Vérifier la logique conditionnelle et les règles de visibilité |
| **Échecs d’import** | Vérifier la compatibilité du format du fichier et les limites de taille |
| **Problèmes de performances** | Optimiser le nombre de champs et supprimer les validations inutiles |
| **Problèmes d’accessibilité** | Vérifier les libellés des champs, les attributs ARIA et l’ordre des onglets |

**Vous avez encore besoin d’aide ?** Saisissez `/help` suivi de votre question spécifique ou contactez votre administrateur ou administratrice système pour obtenir une assistance technique.

## Problèmes d’accès et d’authentification

### Impossible d’accéder à Forms Experience Builder

**Symptômes :**

- Interface de Forms Experience Builder non visible
- « Accès refusé » ou messages d’erreur similaires
- Icône Forms Experience Builder manquante dans l’éditeur

**Solutions :**

1. **Vérifier l’inscription au programme d’accès anticipé**
   - Confirmer votre approbation dans le cadre du programme d’accès anticipé
   - Vérifier que votre demande a été envoyée à partir de votre adresse e-mail professionnelle officielle
   - Contacter `aem-forms-ea@adobe.com` si l’accès est toujours en attente

2. **Vérifier la configuration de l’environnement**
   - Vérifier qu’AEM Forms est activé pour votre environnement
   - Vérifier que vous utilisez un navigateur pris en charge (Chrome, Firefox, Safari, Edge).
   - Effacer la mémoire cache du navigateur et les cookies
   - Désactiver les extensions de navigateur susceptibles d’interférer

3. **Vérifier les autorisations d’utilisation**
   - Vérifier que vous disposez des rôles utilisateur ou utilisatrice et des autorisations appropriés
   - Vérifier auprès de votre administrateur ou administratrice système les droits d’accès
   - Vérifier que vous êtes connecté avec le compte approprié

### Problèmes de chargement de l’interface

**Symptômes :**

- Interface vierge ou partiellement chargée
- Changement d’indicateurs de chargement qui n’aboutissent pas
- Erreurs JavaScript dans la console du navigateur

**Solutions :**

1. **Résolution des problèmes liés au navigateur**
   - Actualiser la page (Ctrl+F5 ou Cmd+Maj+R)
   - Essayer un autre navigateur ou le mode incognito/privé
   - Rechercher les mises à jour du navigateur et installer le cas échéant
   - Désactiver temporairement les bloqueurs de publicités et les extensions de confidentialité

2. **Connectivité réseau**
   - Vérifier la stabilité de la connexion Internet
   - Vérifier si le pare-feu d’entreprise bloque les domaines requis
   - Tester avec une autre connexion réseau si possible
   - Contacter l’assistance informatique pour les problèmes de configuration réseau

3. **Problèmes de mémoire cache et de stockage**
   - Effacer la mémoire cache du navigateur et le stockage local
   - Réinitialiser les paramètres du navigateur aux valeurs par défaut
   - Vérifier l’espace disque disponible sur votre appareil
   - Essayer d’accéder à partir d’un autre appareil

## Problèmes de commande et d’interaction

### Les commandes à barre oblique ne fonctionnent pas

**Symptômes :**

- `/create-form` ou d’autres commandes à barre oblique ne sont pas reconnues
- Aucune suggestion de saisie semi-automatique n’apparaît
- Les commandes génèrent des messages d’erreur

**Solutions :**

1. **Vérification de la syntaxe de la commande**
   - Vérifier que le format de commande est correct : `/command-name description`
   - Rechercher les fautes de frappe dans les noms de commandes
   - Utiliser le langage naturel comme alternative : « Créer un formulaire de contact »
   - Essayer `/help` pour vérifier la disponibilité des commandes

2. **Commandes spécifiques au contexte**
   - Vérifier que vous vous trouvez dans le bon contexte d’éditeur (éditeur universel ou éditeur de formulaires adaptatifs)
   - Certaines commandes ne fonctionnent que dans des environnements spécifiques
   - Vérifier la référence des commandes pour les exigences de contexte

3. **Autres approches**
   - Utiliser le langage naturel au lieu des commandes à barre oblique
   - Décomposer les commandes complexes en requêtes plus petites et plus simples
   - Essayer de créer des formulaires étape par étape au lieu d’une seule commande complexe

### Les références de champ ne fonctionnent pas

**Symptômes :**

- Les références `@fieldName` ne sont pas reconnues
- Messages d’erreur sur des champs inconnus
- Les modifications de champ ne s’appliquent pas correctement

**Solutions :**

1. **Vérification du nom du champ**
   - Vérifier l’orthographe exacte des noms de champs (sensibles à la casse)
   - Vérifier que le champ existe avant de le référencer
   - Utiliser le nom de champ exact tel que créé, et non le libellé d’affichage
   - Vérifier les conventions de dénomination des champs (camelCase, snake_case, etc.)

2. **Syntaxe de référence du champ**
   - Utiliser la syntaxe `@fieldName` appropriée sans espaces
   - Éviter les caractères spéciaux dans les références de champ
   - Rechercher les caractères invisibles ou les problèmes de mise en forme
   - Essayer de recréer manuellement la référence de champ

3. **Débogage des références de champ**
   - Répertorier d’abord tous les champs existants : « Afficher tous les champs de formulaire actuels »
   - Créer des champs avant de les référencer dans les règles
   - Utiliser des noms de champs simples sans caractères complexes
   - Tester les références de champ une par une

## Problèmes de création et de conception de formulaire

### Le formulaire n’est pas créé comme prévu

**Symptômes :**

- Champs demandés manquants dans le formulaire généré
- Types de champs ou mises en page incorrects
- La structure du formulaire ne correspond pas à la description

**Solutions :**

1. **Améliorer la spécificité du prompt**
   - Être plus précis dans les descriptions de formulaire
   - Spécifier les types de champs et les exigences de validation exacts
   - Inclure les préférences de mise en page et les exigences d’expérience d’utilisation
   - Décomposer les formulaires complexes en requêtes plus petites et incrémentielles

2. **Approche de développement itérative**
   - Commencer avec la structure de formulaire de base
   - Ajouter des champs et des fonctionnalités de manière incrémentielle
   - Tester chaque ajout avant de continuer
   - Affiner via une conversation plutôt que via une seule requête complexe

3. **Exemples de meilleurs prompts**

   Au lieu de :

       Créer un formulaire pour les clientes et clients
   
   Utilisez :

       Créer un formulaire de contact client et cliente avec :
     - Nom complet (champ de texte obligatoire)
     - Adresse e-mail (obligatoire avec validation)
     - Numéro de téléphone (facultatif, mis en forme)
     - Message (zone de texte obligatoire, 500 caractères max.)
     - Envoyer à une notification par e-mail
   
### Problèmes de mise en page et de style

**Symptômes :**

- Le formulaire semble tronqué sur les appareils mobiles
- Espacement ou alignement incohérent
- Les champs ne s’affichent pas correctement.
- Mauvaise hiérarchie visuelle

**Solutions :**

1. **Réactivité des appareils mobiles**
   - Demander des optimisations spécifiques aux appareils mobiles : « Rends ce formulaire compatible avec les appareils mobiles ».
   - Définir des exigences en matière de conception réactive
   - Tester sur des appareils mobiles réels
   - Utiliser des dispositions à une seule colonne pour les appareils mobiles

2. **Améliorations de la mise en page**
   - Préciser les exigences de mise en page : « Organise les champs d’adresse en deux colonnes ».
   - Demander un style spécifique : « Utiliser des couleurs professionnelles et une typographie propre »
   - Spécifier les besoins en espacement et alignement
   - Demander la conformité en matière d’accessibilité

3. **Cohérence de la marque**
   - Préparer les directives de la marque avant la création du formulaire
   - Inclure des codes couleur et des polices spécifiques dans les requêtes
   - Utiliser un style cohérent pour tous les formulaires
   - Créer des modèles de marque à réutiliser

### Problèmes de logique conditionnelle

**Symptômes :**

- Règles ne se déclenchant pas comme prévu
- Les champs ne s’affichent/ne se masquent pas correctement
- La logique de validation ne fonctionne pas.
- Échec des règles métier complexes

**Solutions :**

1. **Simplification des règles**
   - Scinder les règles complexes en conditions plus petites et plus simples
   - Tester chaque règle individuellement avant la combinaison
   - Utiliser des conditions claires et spécifiques : « Afficher les @spouseInfo lorsque @maritalStatus est égal à &quot;Marié(e)&quot; ».
   - Éviter initialement les logiques imbriquées ou trop complexes

2. **Règles de tests et débogage**
   - Tester tous les chemins d’accès et scénarios utilisateur possibles
   - Vérifier les noms et valeurs de champ en condition
   - Vérifier le respect de la casse dans les conditions de règle
   - Utiliser le mode de débogage pour suivre l’exécution des règles

3. **Implémentation de la logique commerciale**
   - Documenter clairement les exigences commerciales avant l’implémentation
   - Implémenter les règles de manière incrémentielle et tester chaque étape
   - Fournir les commentaires clairs de l’utilisateur ou de l’utilisatrice lors du déclenchement des règles
   - Gérer les cas Edge et les scénarios d’exception

## Problèmes d’import et de conversion de fichiers

### Échecs d’import de fichiers PDF

**Symptômes :**

- Fichiers PDF ni chargés ni traités
- Champs ou contenu manquants dans les formulaires convertis
- Messages d’erreur lors de la conversion en PDF
- Mauvaise reconnaissance de champs de PDF

**Solutions :**

1. **Format et taille du fichier**
   - S’assurer que les fichiers PDF font moins de 10 Mo
   - Utiliser des fichiers PDF basés sur du texte de haute qualité (et non des images numérisées)
   - Vérifier que le fichier PDF n’est pas protégé par un mot de passe ou chiffré
   - Essayer de convertir le fichier PDF au format d’image si l’extraction de texte échoue

2. **Optimisation de la qualité du fichier PDF**
   - Utiliser des fichiers PDF avec des champs de formulaire clairs et bien définis
   - Assurer un bon contraste et un texte lisible
   - Éviter les mises en page complexes ou les éléments qui se chevauchent
   - Fournir du contexte supplémentaire dans la requête de conversion

3. **Amélioration de la conversion**
   - Décrire en détail la structure du formulaire attendue
   - Spécifier les types de champs et les exigences de validation
   - Demander des améliorations spécifiques : « Ajouter la réactivité et la validation sur les appareils mobiles »
   - Vérifier et affiner manuellement les formulaires convertis

### Problèmes de conversion d’image et de capture d’écran

**Symptômes :**

- Mauvaise reconnaissance des champs à partir des images
- Types de champs ou mises en page incorrects
- Éléments de formulaire manquants
- Erreurs ou délais d’expiration de conversion

**Solutions :**

1. **Exigences de qualité d’image**
   - Utiliser des images haute résolution (300 DPI minimum)
   - Assurer un bon éclairage et un bon contraste
   - Éviter les ombres, les reflets ou les distorsions
   - Recadrer les images pour ne cibler que le contenu du formulaire

2. **Formats d’image optimaux**
   - Utiliser les formats PNG ou JPG pour obtenir de meilleurs résultats
   - Éviter les GIF ou les images compressées de faible qualité
   - Vérifier que le texte est clairement lisible dans l’image
   - Essayer différentes orientations d’image si nécessaire

3. **Conseils de conversion**
   - Fournir des descriptions détaillées de la structure du formulaire
   - Spécifier explicitement les types de champs et les exigences
   - Demander des améliorations spécifiques pendant la conversion
   - Être prêt à effectuer des réglages manuels après la conversion

## Problèmes d’intégration et d’envoi

### Échecs d’envoi du formulaire

**Symptômes :**

- Les formulaire ne sont pas envoyés
- Messages d’erreur lors de l’envoi
- Les données n’atteignent pas les destinations prévues
- Erreurs de délai d’expiration lors de l’envoi

**Solutions :**

1. **Configuration de l’action Envoyer**
   - Vérifier que l’action Envoyer est correctement configurée
   - Vérifier les points d’entrée d’API et les informations d’authentification
   - Tester d’abord avec un envoi simple par e-mail
   - Valider les exigences de format des données

2. **Réseau et connectivité**
   - Vérifier la connectivité Internet et la stabilité du réseau
   - Vérifier que les paramètres du pare-feu autorisent les envois de formulaires
   - Tester à partir d’autres connexions réseau
   - Vérifier les restrictions du proxy d’entreprise ou de sécurité

3. **Problèmes de validation des données**
   - Vérifier que tous les champs obligatoires sont renseignés
   - Vérifier que les formats de données correspondent aux exigences de l’API
   - Rechercher les problèmes de caractères spéciaux ou de codage
   - Tester d’abord avec un jeu de données minimal

### Problèmes d’intégration d’API

**Symptômes :**

- Les points d’entrée de l’API REST ne répondent pas
- Échecs d’authentification
- Le format des données ne correspond pas
- Délais d’expiration ou erreurs d’intégration

**Solutions :**

1. **Vérification de la configuration de l’API**
   - Vérifier que les URL des points d’entrée de l’API sont correctes et accessibles
   - Vérifier les informations d’authentification et les autorisations
   - Tester les points d’entrée d’API indépendamment à l’aide d’outils tels que Postman
   - Vérifier que l’API accepte le format de données correct (JSON, XML, etc.)

2. **Problèmes de mappage des données**
   - Vérifier que les noms des champs du formulaire correspondent aux exigences des paramètres de l’API
   - Rechercher des champs obligatoires qui peuvent être manquants
   - Vérifier la compatibilité du type de données (chaînes, nombres, dates)
   - Tester avec des données d’exemple pour identifier des problèmes de mappage

3. **Gestion des erreurs et débogage**
   - Activer la journalisation détaillée des erreurs pour les appels d’API
   - Vérifier les codes de réponse d’API et les messages d’erreur
   - Implémenter une logique de nouvelle tentative pour les échecs temporaires
   - Fournir des options de secours aux utilisateurs et utilisatrices en cas d’échec de l’API

### Problèmes d’intégration des e-mails

**Symptômes :**

- Les e-mails de confirmation ne sont pas envoyés
- Les e-mails arrivent dans des dossiers de spams
- Mise en forme d’e-mail incorrecte
- Données de formulaire manquantes dans les e-mails

**Solutions :**

1. **Configuration du canal e-mail**
   - Vérifier que les adresses e-mail sont correctement formatées
   - Vérifier les paramètres SMTP et l’authentification
   - Tester d’abord avec des adresses e-mail simples
   - Vérifier les autorisations et les quotas du serveur de messagerie

2. **Optimisation de la remise des e-mails**
   - Utiliser les en-têtes d’e-mail et les informations de la personne expéditrice appropriés
   - Éviter les mots déclencheurs de spams dans les objets
   - Inclure les mécanismes de désabonnement appropriés
   - Tester la remise des e-mails à différents fournisseurs

3. **Contenu et mise en forme**
   - Vérifier que les données de formulaire sont correctement mises en forme dans les e-mails
   - Rechercher les problèmes de caractères spéciaux ou de codage
   - Tester des modèles d’e-mail avec différentes combinaisons de données
   - Garantir l’accessibilité et la lisibilité du contenu des e-mails

## Problèmes de performance et de chargement

### Chargement de formulaire lent

**Symptômes :**

- Chargement initial des formulaires prend beaucoup de temps
- Interactions utilisateur lentes
- Délais d’expiration pendant les opérations de formulaire
- Mauvaises performances sur les appareils mobiles

**Solutions :**

1. **Optimisation des formulaires**
   - Réduire le nombre de champs et la complexité
   - Mettre en œuvre le chargement différé pour les sections non critiques
   - Optimiser les images et les ressources pour la diffusion web
   - Supprimer la logique ou les règles de validation inutiles

2. **Optimisation du navigateur et de l’appareil**
   - Effacer la mémoire cache du navigateur et les fichiers temporaires
   - Fermer les onglets du navigateur et les applications inutiles
   - Vérifier la mémoire et le stockage disponibles du périphérique
   - Essayer différents navigateurs pour comparer les performances

3. **Optimisation du réseau**
   - Tester avec différentes connexions réseau
   - Vérifier si le réseau est encombré ou si la bande passante est limitée
   - Utiliser une connexion câblée au lieu du WiFi si possible
   - Contacter le support informatique pour les problèmes de performances du réseau

### Validation des problèmes de performances

**Symptômes :**

- Réponses de validation lentes
- Affichage retardé du message d’erreur
- Gel du formulaire pendant la validation
- Erreurs de délai d’expiration lors de la validation du champ

**Solutions :**

1. **Optimisation de la validation**
   - Réduire la fréquence de validation en temps réel
   - Implémenter le rebond pour les appels de validation
   - Simplifier les règles de validation complexes
   - Utiliser la validation côté client si possible

2. **Simplification des règles**
   - Scinder la validation complexe en règles plus petites
   - Supprimer les validations inutiles entre champs
   - Optimiser la logique conditionnelle pour les performances
   - Mettre en cache les résultats de validation le cas échéant

3. **Améliorations de l’expérience client**
   - Fournir des commentaires immédiats pour des validations simples
   - Utiliser la validation progressive plutôt qu’en temps réel pour les règles complexes
   - Afficher les indicateurs de chargement lors des processus de validation
   - Autoriser les utilisateurs et les utilisatrices à continuer pendant les processus de validation en arrière-plan

## Dépannage avancé

### Mode de débogage et diagnostics

**Activer les informations de débogage**

Utilisez ces invites pour obtenir des informations plus détaillées sur les problèmes de formulaire :

    Active le mode de débogage pour identifier les problèmes liés à l’envoi du formulaire et à la validation des champs
    
    Analyse les erreurs de formulaire : vérifie les règles de validation, les réponses de l’API et les modèles de saisie utilisateur
    
    Affiche des informations détaillées sur la structure du formulaire et la configuration des champs

### Techniques d’analyse des erreurs

**Approche de débogage systématique**

1. **Isoler le problème**
   - Testez avec une configuration de formulaire minimale.
   - Supprimez temporairement les fonctionnalités complexes.
   - Testez séparément les composants individuels.
   - Utilisez le processus d’élimination pour identifier la cause première.

2. **Collecter des informations de diagnostic**
   - Vérifiez la console du navigateur afin d’identifier les erreurs JavaScript.
   - Vérifiez les requêtes réseau et leurs réponses.
   - Documentez précisément les étapes permettant de reproduire le problème.
   - Rassemblez des captures d’écran et des messages d’erreur.

3. **Tester les variables d’environnement**
   - Effectuez des essais sur différents navigateurs et périphériques
   - Testez avec différents comptes et autorisations attribués à l’utilisateur ou l’utilisatrice.
   - Vérifiez dans divers environnements réseau.
   - Comparez avec des formulaires de travail ou des configurations.

### Analyse et surveillance des journaux

**Débogage de la console du navigateur**

1. Ouvrez les outils de développement du navigateur (F12).
2. Vérifiez l’onglet Console afin d’identifier les erreurs JavaScript.
3. Examinez l’onglet Réseau pour détecter les requêtes ayant échoué.
4. Surveillez l’onglet Performances afin d’identifier les opérations lentes.

**Modèles d’erreurs fréquents**

- **Erreurs CORS** : problèmes de requêtes inter-origines avec les intégrations API
- **Échecs d’authentification** : informations d’identification non valides ou jetons expirés
- **Erreurs de validation** : conflits de règles de validation de champ ou erreurs de syntaxe
- **Délais d’expiration du réseau** : connexions réseau lentes ou instables

## Obtention d’aide supplémentaire

### Ressources en libre-service

**Système d&#39;aide intégré**

- Utilisez la commande `/help` suivie de questions spécifiques.
- Accéder à l’aide contextuelle dans l’interface Forms Experience Builder
- Examiner attentivement les messages d’erreur pour obtenir des conseils spécifiques
- Consulter le [Guide de prise en main de Forms Experience Builder](forms-ai-assistant-getting-started.md)

**Ressources de documentation**

- [Bibliothèque d’invites de Forms Experience Builder](ai-assistant-prompt-library.md)
- [Meilleures Pratiques relatives à Forms Experience Builder](aem-forms-ai-assistant-best-practices.md)
- [Documentation dʼAEM Forms](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html?lang=fr)

### Escalade et assistance

**Quand contacter l’assistance**

- Les problèmes persistent après l’application des solutions documentées
- Problèmes à l’échelle du système affectant plusieurs utilisateurs ou utilisatrices
- Problèmes de sécurité ou d’intégrité des données
- Problèmes d’intégration nécessitant une configuration au niveau du système

**Informations à fournir**

- Description détaillée du problème et étapes à suivre pour le reproduire
- Captures d’écran ou enregistrements d’écran du problème
- Informations sur le navigateur et le système
- Messages d’erreur et journaux de la console
- Détails de la configuration et de l’intégration de formulaire

**Méthodes de contact**

- Administrateur ou administratrice système : pour les problèmes d’environnement et d’accès
- Support technique : pour les problèmes d’intégration et de configuration complexes
- Programme d’accès anticipé : `aem-forms-ea@adobe.com` pour les problèmes propres au programme

### Communauté et partage de connaissances

**Bonnes pratiques relatives à la résolution de problème**

- Documenter les solutions pour référence ultérieure
- Partager les approches de résolution des problèmes concluantes avec les membres de l’équipe
- Contribuer à la base de connaissances de l’organisation
- Participer aux communautés et forums d’utilisateurs et d’utilisatrices

**Amélioration continue**

- Examen régulier des problèmes courants et des solutions
- Mettre à jour les procédures de résolution des problèmes en fonction des nouveaux résultats
- Sessions de formation et de partage de connaissances
- Commentaires à l’équipe produit pour les améliorations de fonctionnalités

Ce guide de résolution des problèmes est continuellement mis à jour en fonction des commentaires des utilisateurs et utilisatrices et des nouvelles fonctionnalités de Forms Experience Builder. Pour consulter les dernières informations et les ressources supplémentaires, consultez la [documentation d’AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html?lang=fr).
