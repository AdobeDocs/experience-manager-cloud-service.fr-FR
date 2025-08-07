---
title: Configurer des actions d’envoi pour AEM Forms avec Edge Delivery Services
description: Découvrez comment configurer des actions d’envoi dans AEM Forms à l’aide d’Edge Delivery Services. Choisissez entre le service d’envoi de formulaires et l’action d’envoi de l’instance de publication AEM pour gérer les données de formulaire de manière sécurisée et efficace.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 8f490054-f7b6-40e6-baa3-3de59d0ad290
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '855'
ht-degree: 13%

---

# Configuration des actions Envoyer pour AEM Forms

Configurez la gestion de l’envoi des formulaires pour acheminer les données vers des feuilles de calcul, des e-mails ou des systèmes principaux à l’aide d’AEM Forms avec Edge Delivery Services.

## Guide de décision rapide

Choisissez votre méthode d’envoi :

| Méthode | Idéal pour | Complexité de la configuration | Cas d’utilisation |
|--------|----------|------------------|-----------|
| **Service d’envoi Forms** | Capture de données simple | Faible | Formulaires de contact, enquêtes, collecte de données de base |
| **Envoi de la publication AEM** | Workflows complexes | Élevée | Intégrations d’entreprise, traitement personnalisé, workflows |

## Prérequis

Avant de configurer les actions d’envoi, vérifiez les points suivants :

- Instance AEM Forms as a Cloud Service
- Projet Edge Delivery Services configuré
- Formulaire créé à l’aide de la création de documents ou de l’éditeur universel
- Autorisations requises pour les destinations cibles (feuilles de calcul, systèmes de messagerie ou AEM)

+++ Méthode 1 : service d’envoi Forms

Le service d’envoi Forms est un point d’entrée hébergé sur Adobe idéal pour les scénarios de capture de données simples.

### Destinations prises en charge

- **Feuilles de calcul** : Google Sheets, Microsoft Excel (OneDrive/SharePoint)
- **E-mail** : envoyez les données de formulaire aux adresses e-mail spécifiées

### Étapes de configuration

1. **Configurer l’accès à la destination**
   - Pour les feuilles de calcul : octroyer l’autorisation de modification pour `forms@adobe.com` sur une feuille de calcul cible
   - Pour les e-mails : vérifier que les adresses e-mail des destinataires sont accessibles

2. **Configurer l’envoi du formulaire**
   - Ouvrez votre formulaire dans l’environnement de création
   - Définir l’action d’envoi sur « Forms Submission Service »
   - Spécifier l’URL ou les adresses e-mail de la feuille de calcul cible
   - Enregistrer et publier le formulaire

3. **Tester l’envoi**
   - Envoi de données de test via le formulaire
   - Vérifier que les données apparaissent dans la destination cible
   - Vérifier les journaux d’erreurs en cas d’échec de l’envoi

### Remarques importantes

- Le compte de service `forms@adobe.com` nécessite un accès en modification aux feuilles de calcul cibles
- Les notifications par e-mail sont envoyées immédiatement après l’envoi du formulaire
- La validation des données se produit au niveau du service

![Flux du service d’envoi Forms](/help/forms/assets/eds-fss.png)

+++

+++ Méthode 2 : envoi de l’instance de publication AEM

Envoyez directement les données de formulaire à votre instance de publication AEM as a Cloud Service pour un traitement complexe.

### Quand utiliser la publication AEM

- Workflows AEM personnalisés requis après l’envoi
- Intégration du modèle de données de formulaire (FDM) aux bases de données
- Intégrations de services tiers (Marketo, Power Automate, Workfront Fusion)
- Azure Blob Storage ou bibliothèques de documents SharePoint
- Logique complexe de validation ou de traitement côté serveur

### Actions d’envoi disponibles

- [Envoyer vers le point d’entrée REST](/help/forms/configure-submit-action-restpoint.md)
- [Envoyer un e-mail via les services de messagerie AEM](/help/forms/configure-submit-action-send-email.md)
- [Envoyer à l’aide du modèle de données de formulaire](/help/forms/configure-data-sources.md)
- [Appeler le processus AEM](/help/forms/aem-forms-workflow-step-reference.md)
- [Envoyer à SharePoint](/help/forms/configure-submit-action-sharepoint.md)
- [Envoyer à OneDrive](/help/forms/configure-submit-action-onedrive.md)
- [Envoyer au stockage Blob Azure](/help/forms/configure-submit-action-azure-blob-storage.md)
- [Envoyer à Microsoft Power Automate](/help/forms/forms-microsoft-power-automate-integration.md)
- [Envoyer à Adobe Workfront Fusion](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
- [Envoyer à Adobe Marketo Engage](/help/forms/submit-adaptive-form-to-marketo-engage.md)

![Flux d’envoi de publication AEM](/help/forms/assets/eds-aem-publish.png)

### Configuration requise

#### &#x200B;1. Configuration AEM Dispatcher

Configurez Dispatcher sur votre instance de publication AEM :

- **Autoriser les chemins d’envoi** : modifiez les `filters.any` pour autoriser les requêtes POST à `/adobe/forms/af/submit/...`
- **Pas de redirection** : assurez-vous que les règles Dispatcher ne redirigent pas les chemins d’envoi de formulaire

#### &#x200B;2. Filtre référent OSGi

Dans la console OSGi AEM (`/system/console/configMgr`) :

1. Recherchez « Apache Sling Referrer Filter »
2. Ajouter votre domaine Edge Delivery à la liste « Hôtes autorisés »
3. Inclure des domaines comme `https://your-eds-domain.hlx.page`

#### &#x200B;3. Règles de redirection CDN

Configurez votre réseau CDN Edge Delivery pour acheminer les envois :

- Acheminer les requêtes de `/adobe/forms/af/submit/...` vers votre instance de publication AEM
- L’implémentation varie selon le fournisseur de réseau CDN (Fastly, Akamai, Cloudflare)

#### &#x200B;4. Configuration du formulaire

1. Création d’un formulaire dans l’éditeur universel
2. Configuration de l’action d’envoi pour cibler l’action AEM Forms
3. Spécifier le chemin du point d’entrée d’envoi
4. Publication du formulaire sur un site Edge Delivery

+++

+++ Incorporation de formulaire (facultatif)

Incorporez les formulaires créés à un emplacement dans différentes pages web ou sites.

### Cas d’utilisation

- Réutilisation de formulaires standard sur plusieurs pages de destination
- Inclure des formulaires spécialisés dans le contenu créé à l’aide de documents
- Tenir à jour un seul formulaire pour plusieurs projets EDS

### Configuration CORS

Configurez le partage de ressources entre origines multiples (CORS) sur la source de formulaire :

1. **Ajoutez des en-têtes CORS** pour former des réponses source :
   - `Access-Control-Allow-Origin: https://your-host-domain.com`
   - `Access-Control-Allow-Methods: GET, OPTIONS`
   - `Access-Control-Allow-Headers: Content-Type`

2. **Exemple de configuration** :

       &#x200B;# Configuration pour le site hébergeant le formulaire
       headers:
       - chemin : /forms/**
       custom:
       Access-Control-Allow-Origin : https://host-domain.com
       Access-Control-Allow-Methods : GET, OPTIONS
   

### Étapes d’incorporation

1. **Créer et publier un formulaire**
   - Créer un formulaire à l’aide de la création de documents ou de l’éditeur universel
   - Configuration de la méthode d’envoi (FSS ou publication AEM)
   - Publier sur une URL autonome

2. **Configurer CORS**
   - Configurer des en-têtes CORS sur le site source du formulaire
   - Autoriser le domaine de la page hôte à récupérer le formulaire

3. **Incorporer dans la page hôte**
   - Ajout d’un bloc d’incorporation de formulaire à la page hôte
   - Pointer le bloc vers l’URL du formulaire publiée
   - Publier la page hôte

![Architecture de formulaire incorporée](/help/forms/assets/eds-embedded-form.png)

+++

+++ Problèmes courants

| Problème | Solution |
|-------|----------|
| **L’envoi du formulaire échoue** | Vérification des erreurs de console, vérification de l’URL du point d’entrée, confirmation des autorisations |
| **Le formulaire incorporé n’apparaît pas** | Configurez les en-têtes CORS sur la source de formulaire et vérifiez l’URL du formulaire. |
| Erreurs **403/401 avec AEM** | Mettre à jour le filtre de référent Sling, vérifier les paramètres d’authentification |
| **Les données n’atteignent pas la feuille de calcul** | Vérifiez que `forms@adobe.com` a un accès en modification, vérifiez l&#39;URL de la feuille de calcul |
| **Erreurs CORS** | Ajouter les en-têtes de `Access-Control-Allow-Origin` appropriés à la source de formulaire |

+++

## Exemples de configurations

+++ Formulaire basé sur des documents avec envoi de feuilles de calcul

1. Création de la structure d’un formulaire dans Google Docs/Sheets
2. Configurer le point d’entrée du service de soumission Forms
3. Octroi de l’accès `forms@adobe.com` modification à la feuille de calcul cible
4. Publier le document sur le site Edge Delivery
5. Tester l’envoi du formulaire et le flux de données

+++

+++ Formulaire d’éditeur universel avec workflow AEM

1. Créer un formulaire dans l’éditeur universel
2. Configurer l’action d’envoi pour « Appeler un workflow AEM »
3. Configurer le Dispatcher et le filtre référent sur l’instance de publication AEM
4. Configurer des règles de routage CDN
5. Publier le formulaire et tester l’exécution du workflow

+++

## Bonnes pratiques

- **Utiliser le service d’envoi Forms** pour les scénarios de capture de données simples
- **Choisissez l’instance de publication AEM** lorsque des processus ou des intégrations complexes sont requis
- **Testez minutieusement** dans l’environnement d’évaluation avant le déploiement en production
- **Surveiller les envois** en utilisant les journaux AEM et les erreurs de la console
- **Implémenter une gestion des erreurs appropriée** pour les envois ayant échoué
- **Valider les données** au niveau du client et du serveur
- **Utilisez HTTPS** pour tous les envois de formulaire et la transmission de données.

## Rubriques connexes

- [Création basée sur les documents avec EDS Forms](/help/edge/docs/forms/tutorial.md)
- [Éditeur universel avec EDS Forms](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
- [Service d’envoi de formulaires AEM](/help/forms/forms-submission-service.md)
- [Configurer les sources de données](/help/forms/configure-data-sources.md)
- [Référence sur les workflows AEM Forms](/help/forms/aem-forms-workflow-step-reference.md)
