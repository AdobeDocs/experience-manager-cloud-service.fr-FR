---
title: Forms Experience Builder - Guide de dépannage
description: Guide de dépannage complet pour Forms Experience Builder, couvrant les problèmes courants, les solutions et les techniques de débogage pour la création et la gestion des formulaires.
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: 6a7810fd-2860-410b-867d-8d29afd5297d
source-git-commit: fe34b44d02c308e7d18a08dd05f21abc67bd0cb2
workflow-type: tm+mt
source-wordcount: '2282'
ht-degree: 1%

---


# Forms Experience Builder - Guide de dépannage

>[!NOTE]
>
> Forms Experience Builder est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail de votre adresse professionnelle à `aem-forms-ea@adobe.com` pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : ce guide de dépannage est en cours de test par rapport au produit et est sujet à des mises à jour et des révisions. Les problèmes, les solutions et les techniques de débogage peuvent changer à mesure que Forms Experience Builder continue d’évoluer pendant le programme d’adoption précoce.

Ce guide de dépannage complet vous permet d’identifier, de diagnostiquer et de résoudre les problèmes courants rencontrés lors de l’utilisation de Forms Experience Builder. Le guide est organisé par catégories de problèmes avec des correctifs rapides et des solutions détaillées.

## Référence rapide - Problèmes courants

| Problème | Quick Fix |
|-------|-----------|
| **Interface non chargée** | Actualiser le navigateur, vérifier la connexion Internet, vérifier les autorisations d&#39;accès anticipé |
| **Les commandes ne fonctionnent pas** | Essayez de `/help` ou utilisez le langage naturel au lieu des commandes de barre oblique. |
| **@fieldName non reconnu** | Vérifier l’orthographe, s’assurer que le champ existe en premier, vérifier la syntaxe du nom du champ |
| **Échec du chargement du fichier** | Utilisez PDF/JPG/PNG de moins de 10 Mo pour vérifier la compatibilité des formats de fichier. |
| **L’apparence du formulaire est incorrecte** | Soyez plus précis : « Rendez-le compatible avec les appareils mobiles » au lieu de « réparer la mise en page » |
| **Échec de l’intégration** | Vérification des informations d’identification et des autorisations d’API, vérification de la disponibilité des points d’entrée |
| **Formulaire non envoyé** | Vérifier la configuration et les règles de validation de l’action d’envoi |
| **Erreurs de validation non affichées** | Vérifier les paramètres de validation des champs et l’emplacement des messages d’erreur |
| **Problèmes de disposition mobile** | Vérifier les paramètres de Responsive Design et le dimensionnement des champs |
| **Les champs n’apparaissent pas** | Vérifier la logique conditionnelle et les règles de visibilité |
| **Échecs d’import** | Vérifier la compatibilité des formats de fichiers et les limites de taille |
| **Problèmes de performances** | Optimiser le nombre de champs et supprimer les validations inutiles |
| **Problèmes d’accessibilité** | Vérifier les libellés de champ, les attributs ARIA et l’ordre de tabulation |

**Vous avez encore besoin d&#39;aide ?** Type `/help` suivi de votre question spécifique ou contactez votre administrateur système pour obtenir une assistance technique.

## Problèmes d’accès et d’authentification

### Impossible D’Accéder À Forms Experience Builder

**Symptômes :**

- Interface de Forms Experience Builder non visible
- « Accès refusé » ou messages d’erreur similaires
- Icône Forms Experience Builder manquante dans l’éditeur

**Solutions :**

1. **Vérifier l’inscription anticipée au programme**
   - Confirmer que vous avez été approuvé pour le programme des utilisateurs et utilisatrices précoces
   - Vérifiez que votre demande a été envoyée à partir de votre e-mail de travail officiel
   - Contactez `aem-forms-ea@adobe.com` si l’accès est toujours en attente

2. **Vérifiez la configuration de l’environnement**
   - Vérifiez qu’AEM Forms est activé pour votre environnement.
   - Vérifiez que vous utilisez un navigateur pris en charge (Chrome, Firefox, Safari, Edge)
   - Effacer le cache et les cookies du navigateur
   - Désactiver les extensions de navigateur susceptibles d’interférer

3. **Vérification des autorisations utilisateur**
   - Vérifiez que vous disposez des rôles utilisateur et des autorisations appropriés
   - Demandez à votre administrateur système quels sont ses droits d’accès
   - Vérifiez que vous êtes connecté avec le compte approprié

### Problèmes de chargement de l’interface

**Symptômes :**

- Interface vierge ou partiellement chargée
- Utilisation des indicateurs de chargement qui ne sont pas terminés
- Erreurs JavaScript dans la console du navigateur

**Solutions :**

1. **Dépannage du navigateur**
   - Actualisez la page (Ctrl+F5 ou Cmd+Maj+R)
   - Essayez un autre navigateur ou un mode incognito/privé.
   - Rechercher les mises à jour du navigateur et procéder à l’installation si disponible
   - Désactivez temporairement les bloqueurs d’annonces publicitaires et les extensions de confidentialité.

2. **Connectivité réseau**
   - Vérifier une connexion Internet stable
   - Vérifier si le pare-feu d’entreprise bloque les domaines requis
   - Testez si possible une autre connexion réseau.
   - Contactez l’assistance informatique pour les problèmes de configuration réseau.

3. **Problèmes de cache et de stockage**
   - Effacer le cache du navigateur et le stockage local
   - Réinitialiser les paramètres du navigateur aux valeurs par défaut
   - Vérification de l’espace disque disponible sur votre appareil
   - Essayez d’accéder à partir d’un autre appareil.

## Problèmes liés aux commandes et aux interactions

### Les Commandes De Barre Oblique Ne Fonctionnent Pas

**Symptômes :**

- `/create-form` ou autres commandes de barre oblique non reconnues
- Aucune suggestion de saisie automatique n’apparaît
- Les commandes génèrent des messages d’erreur

**Solutions :**

1. **Vérification de la syntaxe de la commande**
   - Vérifiez que le format de commande est correct : `/command-name description`
   - Vérifier les fautes de frappe dans les noms de commande
   - Utiliser le langage naturel comme alternative : « Créer un formulaire de contact »
   - Essayez `/help` vérifier la disponibilité des commandes.

2. **Commandes Spécifiques Au Contexte**
   - Vérifiez que vous vous trouvez dans le bon contexte d’éditeur (éditeur universel ou éditeur de Forms adaptatif).
   - Certaines commandes ne fonctionnent que dans des environnements spécifiques
   - Vérifier la référence des commandes pour les exigences de contexte

3. **Autres approches**
   - Utiliser le langage naturel au lieu des commandes de barre oblique
   - Répartition des commandes complexes en requêtes plus petites et plus simples
   - Essayez de créer des formulaires étape par étape au lieu d’une seule commande complexe.

### Les Références De Champ Ne Fonctionnent Pas

**Symptômes :**

- `@fieldName` références non reconnues
- Messages d’erreur relatifs à des champs inconnus
- Les modifications de champ ne s’appliquent pas correctement

**Solutions :**

1. **Vérification du nom du champ**
   - Vérifier l’orthographe exacte des noms de champ (sensible à la casse)
   - Vérifier que le champ existe avant de le référencer
   - Utiliser le nom de champ exact tel que créé, et non le libellé d’affichage
   - Vérifier les conventions de dénomination des champs (camelCase, snake_case, etc.)

2. **Syntaxe de référence du champ**
   - Utiliser la syntaxe `@fieldName` appropriée sans espaces
   - Éviter les caractères spéciaux dans les références de champ
   - Rechercher les caractères invisibles ou les problèmes de mise en forme
   - Essayez de recréer manuellement la référence du champ.

3. **Débogage des références de champ**
   - Répertorier d’abord tous les champs existants : « Afficher tous les champs de formulaire actuels »
   - Créer des champs avant de les référencer dans les règles
   - Utiliser des noms de champ simples sans caractères complexes
   - Références de champ de test une par une

## Problèmes de création et de conception de formulaire

### Le formulaire ne se crée pas comme prévu

**Symptômes :**

- Il manque des champs demandés dans le formulaire généré
- Mises en page ou types de champs incorrects
- La structure du formulaire ne correspond pas à la description.

**Solutions :**

1. **Amélioration de la spécificité de l&#39;invite**
   - être plus détaillés dans les descriptions de formulaire ;
   - Spécifier les types de champs exacts et les exigences de validation
   - Inclure les préférences de disposition et les exigences en matière d’expérience utilisateur
   - Diviser les formulaires complexes en requêtes incrémentielles plus petites

2. **Approche de développement itératif**
   - Commencer avec la structure de formulaire de base
   - Ajout incrémentiel de champs et de fonctionnalités
   - Tester chaque ajout avant de continuer
   - Affiner par la conversation plutôt que par une requête complexe unique

3. **Exemple de meilleures invites**

   Au lieu de :

       Créer un formulaire pour les clients
   
   Utilisez :

       Créer un formulaire de contact client avec :
       - Nom complet (champ de texte obligatoire)
       - Adresse e-mail (obligatoire avec validation)
       - Numéro de téléphone (facultatif, formaté)
       - Message (zone de texte requise, 500 caractères max.)
       - Envoyer à une notification par e-mail
   
### Problèmes de mise en page et de style

**Symptômes :**

- Le formulaire semble endommagé sur les appareils mobiles
- Espacement ou alignement incohérent
- Les champs ne s’affichent pas correctement
- Mauvaise hiérarchie visuelle

**Solutions :**

1. **Réactivité mobile**
   - Demander des optimisations spécifiques aux appareils mobiles : « Rendre ce formulaire compatible avec les appareils mobiles »
   - Définition des exigences en matière de Responsive Design
   - Test sur les appareils mobiles réels
   - Utiliser des dispositions à une seule colonne pour les appareils mobiles

2. **Améliorations de la disposition**
   - Précisez les exigences de mise en page : « Organisez les champs d’adresse en deux colonnes ».
   - Demander un style spécifique : « Utiliser des couleurs professionnelles et une typographie propre »
   - Spécification des besoins en espacement et alignement
   - Demander la conformité en matière d’accessibilité

3. **Cohérence de la marque**
   - Préparer les directives de la marque avant la création du formulaire
   - Incluez des codes couleur et des polices spécifiques dans les requêtes
   - Utiliser un style cohérent dans tous les formulaires
   - Créer des modèles de marque à réutiliser

### Problèmes de logique conditionnelle

**Symptômes :**

- Règles ne se déclenchant pas comme prévu
- Les champs ne s’affichent/ne se masquent pas correctement
- La logique de validation ne fonctionne pas.
- Échec des règles métier complexes

**Solutions :**

1. **Simplification des règles**
   - Scinder les règles complexes en conditions plus petites et plus simples
   - Tester chaque règle individuellement avant la combinaison
   - Utilisez des conditions claires et spécifiques : « Afficher les @spouseInfo lorsque @maritalStatus est égal à « Marié(e) ».
   - Évitez initialement les logiques imbriquées ou trop complexes

2. **Test et débogage des règles**
   - Tester tous les chemins d’accès et scénarios utilisateur possibles
   - Vérifier les noms et valeurs de champ dans des conditions
   - Vérifier le respect de la casse dans les conditions de règle
   - Utilisation du mode de débogage pour suivre l’exécution des règles

3. **Implémentation de la logique commerciale**
   - Documentez clairement les exigences commerciales avant l’implémentation.
   - Implémenter des règles de manière incrémentielle et tester chaque étape
   - Fournir des commentaires clairs de l’utilisateur ou de l’utilisatrice lors du déclenchement des règles
   - Gérer les cas Edge et les scénarios d’exception

## Problèmes d’importation et de conversion de fichiers

### Échecs d’importation PDF

**Symptômes :**

- Les fichiers PDF ne sont ni chargés ni traités
- Il manque des champs ou du contenu dans les formulaires convertis
- Messages d’erreur lors de la conversion dans PDF
- Mauvaise reconnaissance de champ de PDF

**Solutions :**

1. **Format et taille du fichier**
   - Assurez-vous que les fichiers PDF font moins de 10 Mo
   - Utiliser des fichiers PDF textuels de haute qualité (et non des images numérisées)
   - Vérifiez que PDF n’est pas protégé par mot de passe ou chiffré.
   - Essayez de convertir PDF au format d’image si l’extraction de texte échoue.

2. **Optimisation de la qualité de PDF**
   - Utiliser des fichiers PDF avec des champs de formulaire clairs et bien définis
   - Garantir un bon contraste et un texte lisible
   - Éviter les dispositions complexes ou les éléments qui se chevauchent
   - Fournissez un contexte supplémentaire dans la demande de conversion

3. **Amélioration de la conversion**
   - Décrivez en détail la structure de formulaire attendue
   - Spécifier les types de champs et les exigences de validation
   - Demandes d’améliorations spécifiques : « Ajouter la réactivité et la validation mobiles »
   - Vérifier et affiner manuellement les formulaires convertis

### Problèmes de conversion d’images et de captures d’écran

**Symptômes :**

- Mauvaise reconnaissance de champ à partir des images
- Mises en page ou types de champs incorrects
- Éléments de formulaire manquants
- Erreurs de conversion ou délais d’expiration

**Solutions :**

1. **Exigences de qualité d’image**
   - Utiliser des images haute résolution (minimum 300 DPI)
   - Assurer un bon éclairage et un bon contraste
   - Évitez les ombres, les reflets ou les déformations
   - Recadrer les images pour se concentrer uniquement sur le contenu du formulaire

2. **Formats d’image optimaux**
   - Utiliser des formats PNG ou JPG pour obtenir de meilleurs résultats
   - Éviter les images compressées GIF ou de faible qualité
   - Vérifiez que le texte est clairement lisible dans l’image
   - Essayez différentes orientations d’image si nécessaire.

3. **Conseils de conversion**
   - Fournir des descriptions détaillées de la structure des formulaires
   - Spécifiez explicitement les types de champs et les exigences.
   - Améliorations spécifiques aux demandes pendant la conversion
   - Être prêt à effectuer des réglages manuels après la conversion

## Problèmes d’intégration et de soumission

### Échecs d’envoi du formulaire

**Symptômes :**

- Forms n’a pas été envoyé
- Messages d’erreur lors de l’envoi
- Les données n’atteignent pas les destinations prévues
- Erreurs de délai d’expiration lors de l’envoi

**Solutions :**

1. **Configuration de l’action Envoyer**
   - Vérifiez que l’action d’envoi est correctement configurée.
   - Vérification des points d’entrée d’API et des informations d’authentification
   - Tester d’abord avec un envoi simple par e-mail
   - Valider les exigences en matière de format des données

2. **Réseau et connectivité**
   - Vérifier la connectivité Internet et la stabilité du réseau
   - Vérifier que les paramètres du pare-feu autorisent les envois de formulaire
   - Test à partir de différentes connexions réseau
   - Vérifier les restrictions de sécurité ou le proxy d’entreprise

3. **Problèmes de validation des données**
   - Vérifiez que tous les champs obligatoires sont renseignés.
   - Vérifier que les formats de données correspondent aux exigences de l’API
   - Rechercher les caractères spéciaux ou les problèmes de codage
   - Tester d’abord avec un jeu de données minimal

### Problèmes d’intégration des API

**Symptômes :**

- Les points d’entrée de l’API REST ne répondent pas
- Échecs d&#39;authentification
- Incohérences du format des données
- Délais d’expiration ou erreurs d’intégration

**Solutions :**

1. **Vérification de la configuration API**
   - Vérifiez que les URL des points d’entrée de l’API sont correctes et accessibles.
   - Vérification des informations d’identification et des autorisations d’authentification
   - Test indépendant des points d’entrée d’API à l’aide d’outils tels que Postman
   - Vérifiez que l’API accepte le format de données correct (JSON, XML, etc.)

2. **Problèmes de mappage des données**
   - Assurez-vous que les noms des champs de formulaire correspondent aux exigences des paramètres de l’API
   - Rechercher les champs obligatoires qui peuvent être manquants
   - Vérifier la compatibilité des types de données (chaînes, nombres, dates)
   - Tester avec des exemples de données pour identifier les problèmes de mappage

3. **Gestion des erreurs et débogage**
   - Activer la journalisation détaillée des erreurs pour les appels API
   - Vérification des codes de réponse API et des messages d’erreur
   - Implémenter une logique de reprise pour les échecs temporaires
   - Fournir des options de secours aux utilisateurs en cas d’échec de l’API

### Problèmes d&#39;intégration des e-mails

**Symptômes :**

- E-mails de confirmation non envoyés
- E-mails allant dans des dossiers de spam
- Formatage d’e-mail incorrect
- Données de formulaire manquantes dans les e-mails

**Solutions :**

1. **Configuration des e-mails**
   - Vérifier que les adresses e-mail sont correctement formatées
   - Vérifier les paramètres SMTP et l’authentification
   - Tester d’abord avec des adresses e-mail simples
   - Vérification des autorisations et des quotas de serveur de messagerie

2. **Optimisation de la diffusion des e-mails**
   - Utiliser les en-têtes d’e-mail et les informations de l’expéditeur appropriés
   - Éviter les mots de déclenchement de spam dans les objets
   - Inclure les mécanismes de désabonnement appropriés
   - Tester la diffusion d’e-mails vers différents fournisseurs

3. **Contenu et formatage**
   - Vérifier que les données de formulaire sont correctement formatées dans les e-mails
   - Rechercher les caractères spéciaux ou les problèmes de codage
   - Tester des modèles d’e-mail avec différentes combinaisons de données
   - Garantir l’accessibilité et la lisibilité du contenu des e-mails

## Problèmes de performance et de chargement

### Chargement de formulaire lent

**Symptômes :**

- Le chargement initial de Forms prend beaucoup de temps
- Interactions utilisateur lentes
- Délais d’expiration pendant les opérations de formulaire
- Mauvaises performances sur les appareils mobiles

**Solutions :**

1. **Optimisation des formulaires**
   - Réduction du nombre de champs et de la complexité
   - Mise en œuvre du chargement différé pour les sections non critiques
   - Optimisation des images et des ressources pour la diffusion web
   - Supprimer la logique ou les règles de validation inutiles

2. **Optimisation du navigateur et de l’appareil**
   - Effacer le cache du navigateur et les fichiers temporaires
   - Fermez les onglets de navigateur et les applications inutiles
   - Vérifier la mémoire et le stockage disponibles du périphérique
   - Essayez différents navigateurs pour comparer les performances

3. **Optimisation du réseau**
   - Tester avec différentes connexions réseau
   - Vérifiez si le réseau est encombré ou si la bande passante est limitée.
   - Utilisez une connexion câblée au lieu du WiFi si possible.
   - Contactez le support informatique pour les problèmes de performances du réseau

### Problèmes de performances de validation

**Symptômes :**

- Réponses de validation lentes
- Affichage retardé du message d’erreur
- Gel du formulaire pendant la validation
- Erreurs de délai d’expiration lors de la validation du champ

**Solutions :**

1. **Optimisation de la validation**
   - Réduction de la fréquence de validation en temps réel
   - Implémenter le rebond pour les appels de validation
   - Simplification des règles de validation complexes
   - Utilisez la validation côté client si possible.

2. **Simplification des règles**
   - Scinder la validation complexe en règles plus petites
   - Supprimer les validations inutiles entre champs
   - Optimisation de la logique conditionnelle pour les performances
   - Mettre en cache les résultats de validation le cas échéant

3. **Amélioration de l’expérience utilisateur**
   - Fournir des commentaires immédiats pour des validations simples
   - Utiliser la validation progressive plutôt que le temps réel pour les règles complexes
   - Afficher les indicateurs de chargement lors des processus de validation
   - Autoriser les utilisateurs à continuer pendant les processus de validation en arrière-plan

## Dépannage avancé

### Mode de débogage et diagnostics

**Activer les informations de débogage**

Utilisez ces invites pour obtenir des informations plus détaillées sur les problèmes de formulaire :

    Activer le mode de débogage pour identifier les problèmes liés à l’envoi du formulaire et à la validation des champs
    
    Analyser les erreurs de formulaire : vérifier les règles de validation, les réponses de l’API et les modèles de saisie utilisateur
    
    Afficher des informations détaillées sur la structure du formulaire et la configuration des champs

### Techniques d’analyse des erreurs

**Approche de débogage systématique**

1. **Isoler le problème**
   - Tester avec une configuration de formulaire minimale
   - Supprimer temporairement les fonctionnalités complexes
   - Tester séparément les composants individuels
   - Utiliser le processus d’élimination pour identifier la cause première

2. **Collecter des informations de diagnostic**
   - Rechercher les erreurs JavaScript dans la console du navigateur
   - Vérifier les requêtes et les réponses du réseau
   - Documenter les étapes exactes pour reproduire le problème
   - Collecter des captures d’écran et des messages d’erreur

3. **Test des variables d’environnement**
   - Essayer différents navigateurs et appareils
   - Tester avec différents comptes utilisateur et autorisations
   - Vérification dans différents environnements réseau
   - Comparer avec des formulaires de travail ou des configurations

### Analyse et surveillance des journaux

**Débogage de la console du navigateur**

1. Ouvrir les outils de développement du navigateur (F12)
2. Vérification des erreurs dans l’onglet Console pour JavaScript
3. Consultez l’onglet Réseau pour les requêtes ayant échoué
4. Onglet Surveillance des performances pour les opérations lentes

**Modèles d’erreur courants**

- **Erreurs CORS** : problèmes de requêtes entre origines multiples avec les intégrations d’API
- **Échecs d’authentification** : informations d’identification non valides ou jetons expirés
- **Erreurs de validation** : conflits de règles de validation de champ ou erreurs de syntaxe
- **Délais d’expiration du réseau** : connexions réseau lentes ou non fiables

## Obtention d’aide supplémentaire

### Ressources en libre-service

**Système d&#39;aide intégré**

- Utilisation de `/help` commande suivie de questions spécifiques
- Accès à l’aide contextuelle dans l’interface de Forms Experience Builder
- Examinez attentivement les messages d’erreur pour obtenir des conseils spécifiques
- Consultez le Guide de prise en main de [Forms Experience Builder](forms-ai-assistant-getting-started.md)

**Ressources de documentation**

- [Bibliothèque d’invites de Forms Experience Builder](ai-assistant-prompt-library.md)
- [Bonnes pratiques relatives à Forms Experience Builder](aem-forms-ai-assistant-best-practices.md)
- [Documentation AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html?lang=fr)

### Escalade et assistance

**Quand contacter l’assistance**

- Les problèmes persistent après avoir essayé des solutions documentées
- Problèmes systémiques affectant plusieurs utilisateurs
- Problèmes de sécurité ou d’intégrité des données
- Problèmes d’intégration nécessitant une configuration au niveau du système

**Informations à fournir**

- Description détaillée du problème et étapes à suivre pour le reproduire
- Captures d’écran ou enregistrements d’écran du problème
- Informations sur le navigateur et le système
- Messages d’erreur et journaux de la console
- Détails de configuration et d’intégration du formulaire

**Méthodes de contact**

- Administrateur système : pour les problèmes d’environnement et d’accès
- Support technique : pour les problèmes complexes d&#39;intégration et de configuration
- Programme d&#39;accès anticipé : `aem-forms-ea@adobe.com` pour les questions propres au programme

### Communauté et partage des connaissances

**Bonnes pratiques pour la résolution des problèmes**

- Documenter les solutions pour référence future
- Partager les approches de dépannage réussies avec les membres de l’équipe
- Contribuer à la base de connaissances organisationnelle
- Participer aux communautés et forums d&#39;utilisateurs

**Amélioration continue**

- Examen régulier des problèmes communs et des solutions
- Mettre à jour les procédures de dépannage en fonction des nouveaux résultats
- Sessions de formation et de partage des connaissances
- Retour d’informations à l’équipe produit pour les améliorations de fonctionnalités

Ce guide de dépannage est mis à jour en permanence en fonction des commentaires des utilisateurs et des nouvelles fonctionnalités de Forms Experience Builder. Pour obtenir les dernières informations et des ressources supplémentaires, consultez la [documentation d’AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html?lang=fr).
