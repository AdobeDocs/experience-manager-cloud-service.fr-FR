---
title: Service de soumission Forms pour Edge Delivery Services
description: Stockez les envois de formulaire directement dans les feuilles de calcul à l’aide du service d’envoi Forms hébergé Adobe. Découvrez l’installation, la configuration et l’utilisation des API pour l’intégration de Google Sheets, OneDrive et SharePoint.
keywords: Service d’envoi Forms, formulaires Edge Delivery Services, intégration de feuilles de calcul, formulaires Google Sheets, formulaires OneDrive, formulaires SharePoint, collecte de données de formulaire
feature: Edge Delivery Services
role: User, Developer, Admin
level: Beginner, Intermediate
exl-id: 12b4edba-b7a1-4432-a299-2f59b703d583
source-git-commit: 4ed2444dac60fe08ae3de13f62aa7a400c06473a
workflow-type: tm+mt
source-wordcount: '1545'
ht-degree: 2%

---

# Service de soumission Forms pour Edge Delivery Services

Forms Submission Service est une solution hébergée par Adobe qui stocke automatiquement les données d’envoi de formulaires directement dans vos feuilles de calcul préférées : Google Sheets, Microsoft OneDrive ou SharePoint. Vous n’avez ainsi plus besoin d’une infrastructure back-end complexe, tout en assurant la collecte et la gestion des données en temps réel.

## Vue d’ensemble

![Service d’envoi Forms](/help/forms/assets/form-submission-service.png)
*Figure : Workflow du service d’envoi de Forms - de l’envoi du formulaire au stockage des feuilles de calcul*

+++ Qui Doit Utiliser Ce Service ?

**Parfait pour :**

- **Créateurs de contenu** création de formulaires de collecte de données simples
- **Petites entreprises** ayant besoin de workflows de la forme à la feuille de calcul rapides
- **Équipes marketing** collecte des informations sur les prospects
- **Organisateurs d&#39;événements** gestion des inscriptions

**Envisagez des alternatives pour :**

- Workflows complexes nécessitant une logique personnalisée
- Intégrations d’entreprise avec des bases de données
- Forms nécessitant une validation ou un traitement avancés

+++

+++ Cas d’utilisation courants

| Cas d’utilisation | Exemple | Avantage de feuille de calcul |
|----------|---------|-------------------|
| **Contactez Forms** | Demandes de renseignements sur le site Web → Google Sheets | Suivi et import CRM facilités |
| **Enregistrement de l’événement** | Inscriptions à la conférence → Excel Online | Suivi des participants en temps réel |
| **Génération de piste** | Abonnements à la newsletter → SharePoint | Analyse des campagnes marketing |
| **Collecte de commentaires** | Réponses à un questionnaire → feuilles Google | Visualisation rapide des données |

+++

## Principaux avantages

Le service de soumission de Forms offre plusieurs avantages pour la collecte de données rationalisée :

+++ Configuration simplifiée

- **Aucune infrastructure principale** requise - Adobe héberge le point d’entrée d’envoi
- **Intégration directe** avec les tableurs populaires
- **Mappage automatique des données** des champs de formulaire aux colonnes des feuilles de calcul

+++


+++ Real-Time Data Management

- **Capture instantanée des données** - les envois apparaissent immédiatement dans votre feuille de calcul
- **Stockage structuré** - colonnes organisées pour une analyse facile
- **Collaboration en direct** - plusieurs membres de l’équipe peuvent accéder aux données et les analyser

+++

+++ Sécurité et contrôle d’accès intégrés

- **Tire parti des autorisations existantes** - Utilisez les commandes de partage de votre plateforme de feuilles de calcul.
- **sécurité gérée par Adobe** - point d’entrée d’envoi sécurisé avec protection de niveau entreprise
- **Propriété des données** - vos données restent dans la plateforme de feuille de calcul choisie

+++

## Prérequis

Avant de configurer le service d’envoi de Forms, vérifiez que vous disposez des éléments suivants :



+++ Exigences techniques

- **Référentiel GitHub** configurez pour votre projet Edge Delivery Services avec le dernier bloc de Forms adaptatif installé
- **Validation des accès** - Référentiel ajouté à la place sur la liste autorisée

+++

+++ Configuration de Spreadsheet Platform


Choisissez l’une des plateformes prises en charge :

- **Google Sheets** - Compte Google avec autorisations de création de feuilles
- **Microsoft OneDrive** - Compte Microsoft 365 avec accès à Excel Online
- **SharePoint** - Accès à SharePoint avec autorisations de liste/bibliothèque

+++

+++ Autorisations et accès

- **Modifier les autorisations** pour la feuille de calcul cible
- **Fonctionnalités de partage** pour accorder l’accès à `forms@adobe.com`
- **génération de liens** autorisations pour la plateforme de votre choix

+++

>[!TIP]
>
>**Vous découvrez Edge Delivery Services ?** Commencez par le [tutoriel de prise en main](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/tutorial) pour configurer la base de votre projet.

## Méthodes de configuration

Le service d’envoi de Forms propose deux approches de configuration. Choisissez la méthode la mieux adaptée à votre workflow :


+++ Choisissez Votre Méthode De Configuration

| Méthode | Idéal pour | Durée requise | Niveau technique |
|--------|----------|---------------|-----------------|
| **[Configuration manuelle](#manual-configuration)** | Créateurs de contenu, configuration unique | 10 à 15 minutes | Débutant |
| **[Configuration de l’API](#api-configuration)** | Développeurs, workflows automatisés | 5 à 10 minutes | Intermédiaire |

+++

+++ Configuration du projet

Avant de configurer l’une des méthodes, vérifiez que votre base de projet AEM est prête :

1. **Créez ou mettez à jour votre projet AEM** avec le dernier bloc de Forms adaptatif ([tutoriel de prise en main](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/tutorial))

2. **Mettez à jour le`fstab.yaml`** dans la racine de votre projet :

   ```yaml
   # Replace with the path to your shared folder
   mountpoints:
     /: https://drive.google.com/drive/folders/your-shared-folder-id
   ```


3. **Partagez le dossier du projet** avec `forms@adobe.com` (les autorisations de modification sont requises)

+++

## Configuration manuelle

![Processus pour le service d’envoi de formulaires](/help/forms/assets/forms-submission-service-workflow.png)
*Image : workflow complet pour la configuration manuelle du service de soumission Forms*

Suivez ces instructions détaillées pour configurer votre formulaire avec l’envoi de feuille de calcul :



+++ Étape 1 : Créer Votre Définition De Formulaire

Créez votre structure de formulaire à l’aide de Google Sheets ou de Microsoft Excel.

**Étapes de création du formulaire :**

1. **Ouvrez votre plateforme de feuilles de calcul** (Google Sheets ou Microsoft Excel)
2. **Créer une nouvelle feuille de calcul** pour votre projet de formulaire
3. **Nommez votre feuille** (doit être `helix-default` ou `shared-aem`).
4. **Définissez votre structure de formulaire** à l’aide du [guide de création de formulaire](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/create-forms)

![Définition du formulaire](/help/forms/assets/form-submission-definition.png)
*Exemple : définition de formulaire avec des types de champs, des libellés et des règles de validation*

>[!IMPORTANT]
>
>**Exigences en matière de dénomination des feuilles**
>
>Votre feuille de définition de formulaire doit être nommée :
>
>- `helix-default` (recommandé pour les formulaires uniques)
>- `shared-aem` (pour les projets à formulaires multiples)
>
>Les autres noms de feuille ne seront pas reconnus par le système.

**Point de contrôle de validation :**

- La structure du formulaire est complète avec tous les champs obligatoires.
- La feuille est correctement nommée (`helix-default` ou `shared-aem`)
- Les types de champs et les règles de validation sont correctement configurés

+++

+++ Étape 2 : créer la feuille de collecte de données

Configurez une feuille dédiée pour recevoir les données d’envoi de formulaire.

**Configuration de la feuille de données :**

1. **Ajouter une nouvelle feuille** à votre feuille de calcul existante
2. **Nommez la feuille exactement`incoming`** (sensible à la casse).
3. **Configurer des en-têtes de colonne** qui correspondent à vos champs de formulaire.
4. **Enregistrez la feuille de calcul** pour vous assurer que les modifications sont conservées

![Feuille entrante](/help/forms/assets/form-submission-incoming-sheet.png)
*Exemple : feuille entrante avec en-têtes de colonne correspondant aux champs du formulaire*

>[!WARNING]
>
>**Exigence critique**
>
>La feuille doit être nommée exactement `incoming` (en minuscules). Sans cette feuille :
>
>- Les envois de formulaire seront rejetés.
>- Aucune donnée ne sera stockée
>- Les utilisateurs verront les erreurs d’envoi

**Point de contrôle de validation :**

- `incoming` feuille de calcul existe dans votre feuille de calcul
- Les en-têtes des colonnes correspondent aux noms des champs du formulaire
- La feuille est correctement enregistrée et accessible

>[!TIP]
>
>**Conseil pro :** copiez les noms exacts des champs à partir de votre définition de formulaire pour garantir une correspondance parfaite entre les champs de formulaire et les colonnes de la feuille de calcul.

+++

+++ Étape 3 : Partager la feuille de calcul avec Adobe Service

Accordez au service d’envoi Adobe Forms l’accès à votre feuille de calcul.

**Processus de partage :**

1. **Cliquez sur le bouton Partager** dans le coin supérieur droit de votre feuille de calcul
2. **Ajoutez le compte de service Adobe :**

   - E-mail : `forms@adobe.com`
   - Niveau d&#39;autorisation : **Éditeur** (nécessaire pour l&#39;écriture de données)

3. **Envoyer l&#39;invitation de partage**
4. **Copiez le lien de la feuille de calcul** pour l’étape suivante

   ![Partager la feuille entrante](/help/forms/assets/form-submission-share-incoming.png)
   *Processus de partage détaillé pour accorder l’accès au service Adobe*

**Instructions spécifiques à Platform :**

**Feuilles Google:**

- Ajout de `forms@adobe.com` en tant qu’éditeur
- Assurez-vous que « Toute personne disposant du lien peut afficher » est activé
- Copier le lien partageable

**Microsoft Excel (OneDrive/SharePoint) :**

- Ajouter des `forms@adobe.com` avec des autorisations de modification
- Définir le partage de liens sur « Toute personne disposant du lien peut le modifier »
- Copier l’URL de partage

  ![Copier le lien de la feuille entrante](/help/forms/assets/form-submission-copy-link.png)
  *Exemple : copie du lien partageable pour la configuration du formulaire*

**Point de contrôle de validation :**

- `forms@adobe.com` a accès à votre feuille de calcul en tant qu&#39;éditeur
- Le lien de la feuille de calcul est copié et prêt à être utilisé.
- Les autorisations de partage autorisent l’accès externe.

+++

+++ Étape 4 : Connecter le formulaire à la feuille de calcul

Liez votre définition de formulaire à la feuille de calcul d’envoi.

**Connexion Formulaire-Feuille De Calcul:**

1. **Ouvrez votre feuille de calcul de définition de formulaire** (celle qui contient `helix-default` ou `shared-aem` feuille)
2. **Recherchez la ligne Envoyer le champ** dans votre définition de formulaire
3. **Collez le lien de la feuille de calcul copiée** dans la colonne **Action** du champ Envoyer
4. **Enregistrez les modifications** dans votre définition de formulaire

   ![Lier une feuille de calcul](/help/forms/assets/form-submission-sheet-linking.png)

*Exemple : connexion de l’action Envoyer à votre feuille de calcul de collecte de données*

**Publication De Votre Formulaire :**

1. **Ouvrez AEM Sidekick** dans votre navigateur.
2. **Prévisualisez votre formulaire** pour tester la configuration.
3. **Publier le formulaire** pour le rendre actif

**Validation finale :**

- Le lien de la feuille de calcul est correctement ajouté à l’action de champ Envoyer
- La définition du formulaire est enregistrée et publiée
- L’aperçu du formulaire affiche correctement tous les champs
- Le bouton Envoyer est correctement configuré

>[!SUCCESS]
>
>**Configuration terminée !** Votre formulaire est maintenant connecté au service d’envoi Forms. Testez-le en envoyant des données d’exemple et en vérifiant votre feuille de `incoming`.

**Documents de référence :**

- [Exemple complet de feuille de calcul](/help/forms/assets/spreadsheet.xlsx) avec une configuration appropriée
- [Documentation AEM Sidekick](https://www.aem.live/docs/sidekick) pour obtenir des conseils sur la publication

+++

## Configuration de l’API

La méthode API permet aux développeurs d’envoyer par programmation des données au service d’envoi de Forms, idéal pour les workflows automatisés et les intégrations personnalisées.


+++ Quand utiliser l’API

**Parfait pour :**

- Systèmes automatisés de collecte de données
- Implémentations de formulaires personnalisés
- Intégration avec les applications existantes
- Workflows d’envoi de données en bloc

+++

+++ Conditions préalables relatives à l’API

Avant d’utiliser l’API , vérifiez que vous disposez des éléments suivants :

- **paramétrage de la feuille de calcul** terminé (y compris la feuille de `incoming`)
- **Accès au service Adobe** accordé à `forms@adobe.com`
- **ID du formulaire** à partir du formulaire publié
- **Informations sur le référentiel** (nom de l’organisation et du site)

>[!IMPORTANT]
>
>**Étapes de configuration requises**
>
>L’API nécessite la même configuration de feuille de calcul que la configuration manuelle :
>
>- `incoming` feuille doit exister
>- `forms@adobe.com` doit avoir un accès Éditeur
>- La feuille doit être publiée via AEM Sidekick

+++

+++ Point d’entrée et authentification de l’API

**URL de base :** `https://forms.adobe.com/adobe/forms/af/submit/{id}`

**En-têtes requis :**

- `Content-Type: application/json`
- `x-adobe-routing: tier=live,bucket=main--[repository]--[organization]`

**Documentation de l’API :** [Référence complète de l’API](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/references/aem-forms-submission-service/)

+++

+++ Utilisation de Postman

Postman fournit une interface conviviale pour tester les envois d’API.

**Instructions de configuration :**

1. **Créer une requête POST** dans Postman
2. **Configurer le point d’entrée :** `https://forms.adobe.com/adobe/forms/af/submit/{id}`
3. **Remplacer les espaces réservés :**
   - `{id}` → votre ID de formulaire réel
   - `[repository]` → Nom de votre référentiel GitHub
   - `[organization]` → votre organisation/nom d’utilisateur GitHub

**Configuration de la demande:**

```json
POST https://forms.adobe.com/adobe/forms/af/submit/your-form-id

Headers:
Content-Type: application/json
x-adobe-routing: tier=live,bucket=main--your-repo--your-org

Body (JSON):
{
        "data": {
            "startDate": "2025-01-10",
            "endDate": "2025-01-25",
            "destination": "Australia",
            "class": "First Class",
            "budget": "2000",
            "amount": "1000000",
            "name": "Mary",
            "age": "35",
            "subscribe": null,
            "email": "mary@gmail.com"
                }
}
```

**Réponse attendue :**

- **Code d’état :** `201 Created`
- **Les données apparaissent** immédiatement dans votre feuille de calcul `incoming`

![écran postman](/help/forms/assets/postman-api.png)
*Exemple : envoi réussi de l’API à l’aide de l’interface Postman*

+++

+++ Utilisation de la ligne de commande (curl)

Pour les développeurs qui préfèrent une invite de terminal/commande, utilisez curl pour envoyer des données par programmation.

**Configuration de la ligne de commande :**

Remplacez les espaces réservés suivants dans les commandes ci-dessous :

- `{id}` → votre ID de formulaire réel
- `[repository]` → Nom de votre référentiel GitHub
- `[organization]` → votre organisation/nom d’utilisateur GitHub

>[!BEGINTABS]

>[!TAB macOS/Linux]

```bash
curl -X POST "https://forms.adobe.com/adobe/forms/af/submit/your-form-id" \
    --header "Content-Type: application/json" \
  --header "x-adobe-routing: tier=live,bucket=main--your-repo--your-org" \
    --data '{
        "data": {
            "startDate": "2025-01-10",
            "endDate": "2025-01-25",
            "destination": "Australia",
            "class": "First Class",
            "budget": "2000",
            "amount": "1000000",
            "name": "Joe",
            "age": "35",
            "subscribe": null,
      "email": "joe@example.com"
                }
            }'
```

>[!TAB Invite de commandes Windows]

```cmd
curl -X POST "https://forms.adobe.com/adobe/forms/af/submit/your-form-id" ^
    --header "Content-Type: application/json" ^
  --header "x-adobe-routing: tier=live,bucket=main--your-repo--your-org" ^
  --data "{\"data\": {\"startDate\": \"2025-01-10\", \"endDate\": \"2025-01-25\", \"destination\": \"Australia\", \"class\": \"First Class\", \"budget\": \"2000\", \"amount\": \"1000000\", \"name\": \"Joe\", \"age\": \"35\", \"subscribe\": null, \"email\": \"joe@example.com\"}}"
```

>[!TAB Windows PowerShell]

```powershell
$body = @{
  data = @{
    startDate = "2025-01-10"
    endDate = "2025-01-25"
    destination = "Australia"
    class = "First Class"
    budget = "2000"
    amount = "1000000"
    name = "Joe"
    age = "35"
    subscribe = $null
    email = "joe@example.com"
  }
} | ConvertTo-Json -Depth 3

Invoke-RestMethod -Uri "https://forms.adobe.com/adobe/forms/af/submit/your-form-id" `
  -Method POST `
  -Headers @{"Content-Type"="application/json"; "x-adobe-routing"="tier=live,bucket=main--your-repo--your-org"} `
  -Body $body
```

>[!ENDTABS]

+++

+++ Réponse et vérification de l’API

**Réponse réussie :**

```http
HTTP/1.1 201 Created
Connection: keep-alive
Content-Length: 0
X-Request-Id: 02a53839-2340-56a5-b238-67c23ec28f9f
X-Message-Id: 42ecb4dd-b63a-4674-8f1a-05a4a5b0372c
Date: Fri, 10 Jan 2025 13:06:10 GMT
Access-Control-Allow-Origin: *
```

**Vérification des données:**

Une fois l’envoi réussi, vérifiez que les données apparaissent dans votre feuille de calcul :

![feuille mise à jour](/help/forms/assets/updated-sheet.png)
*Exemple : données écrites dans la feuille entrante via l’API*

**Validation de la réponse :**

- **Statut HTTP :** `201 Created` indique un envoi réussi
- **X-Request-Id :** identifiant unique pour le suivi de l’envoi
- **Les données apparaissent** dans votre feuille de `incoming` en quelques secondes
- **Tous les champs de formulaire** sont correctement mappés aux colonnes de la feuille de calcul

+++

## Résolution des problèmes



+++ Problèmes courants et solutions

**Problème : Erreur Interdite 403**

```
Causes: Missing or incorrect access permissions
Solutions:
- Verify forms@adobe.com has Editor access to your spreadsheet
- Check that your repository is added to the allowlist
- Confirm the x-adobe-routing header format
```

**Problème : Erreur 404 Introuvable**

```
Causes: Incorrect Form ID or endpoint URL
Solutions:  
- Verify your Form ID is correct
- Check the API endpoint URL format
- Ensure your form is published and live
```


**Problème : les données n’apparaissent pas dans la feuille de calcul**

```
Causes: Missing 'incoming' sheet or permission issues
Solutions:
- Confirm 'incoming' sheet exists (case-sensitive)
- Verify column headers match form field names exactly
- Check forms@adobe.com has edit permissions
- Ensure spreadsheet is shared properly
```


**Problème : Erreur de format JSON non valide**

```
Causes: Malformed request body
Solutions:
- Validate JSON syntax using online JSON validators
- Ensure proper escaping of special characters
- Check quote marks and brackets are balanced
```


+++

+++ Obtention d’aide

**Canaux d’assistance :**

- **Problèmes d’accès anticipé :** e-mail [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com)
- **Documentation de l’API :** [Référence du développeur](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/references/aem-forms-submission-service/)
- **Assistance communautaire :** [Communauté Adobe Experience League](https://experienceleaguecommunities.adobe.com/?profile.language=fr)

+++

## Étapes suivantes

Maintenant que le service d’envoi Forms est configuré, explorez les rubriques connexes suivantes :


+++ Améliorez votre Forms

- **[Créer un Forms avancé](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/create-forms)** - Ajouter la validation, la logique conditionnelle et le style personnalisé
- **[Guide des composants de formulaire](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/forms-components)** - Explorer les types de champ de formulaire disponibles

+++

+++ Autres méthodes de soumission

- **[Envois de publications AEM](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md)** - Pour les workflows complexes et les intégrations d’entreprise
- **[Actions Envoyer personnalisées](/help/forms/configure-submit-actions-core-components.md)** - Gestion avancée des envois

+++

+++ Gestion des données

- **[Form Analytics](/help/forms/view-understand-aem-forms-analytics-reports.md)** - Suivre les performances et l’utilisation des formulaires
- **[Intégration de données](/help/forms/configure-data-sources.md)** - Connectez les formulaires aux bases de données et aux systèmes CRM

+++

## Résumé

Le service d’envoi de Forms offre une solution puissante et sans code pour collecter des données de formulaire directement dans des feuilles de calcul. Les principaux bénéfices sont les suivants :

- **Configuration rapide** - Aucune infrastructure d’arrière-plan requise
- **Données en temps réel** - Capture immédiate des envois
- **Plateformes flexibles** - Google Sheets, OneDrive ou SharePoint
- **Accès à l’API** - Fonctionnalités d’envoi par programmation
- **Sécurité d’entreprise** : points d’entrée gérés par Adobe avec contrôles d’accès

**Prêt à démarrer ?** Suivez le guide [configuration manuelle](#manual-configuration) pour une configuration visuelle ou accédez à la [configuration de l’API](#api-configuration) pour une intégration par programmation.
