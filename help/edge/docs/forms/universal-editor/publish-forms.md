---
title: Publication de Forms adaptatif avec Edge Delivery Services
description: Découvrez comment publier, configurer et accéder au Forms adaptatif à l’aide de Edge Delivery Services pour une utilisation en production.
feature: Edge Delivery Services
role: Admin, Architect, Developer
level: Intermediate
keywords: publication de formulaires, Edge Delivery Services, configuration de formulaire, CORS, filtre de référent
exl-id: ba1c608d-36e9-4ca1-b87b-0d1094d978db
source-git-commit: 05c0d8fd16cc8bd805a0e8644d3145685fe6fa12
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 2%

---

# Publication de Forms adaptatif avec Edge Delivery Services

La publication d’un formulaire adaptatif le rend disponible sur Edge Delivery Services pour que les utilisateurs finaux puissent y accéder et l’envoyer. Ce processus comprend trois phases principales : publication du formulaire, configuration des paramètres de sécurité et accès au formulaire dynamique.

**Ce que vous allez accomplir**

- Publication de votre formulaire dans Edge Delivery Services
- Configurer les paramètres de sécurité pour l’envoi de formulaire
- Accéder au formulaire publié et le vérifier
- Configurer le routage d’URL et les politiques CORS appropriés

## Prérequis

- Formulaire adaptatif créé à l’aide du modèle Edge Delivery Services
- Formulaire testé et prêt à être utilisé en production
- Autorisations d’auteur AEM Forms
- Accès à Cloud Manager (pour la configuration de production)
- Accès des développeurs au code bloc de formulaire (pour la configuration de l’envoi)

## Présentation du processus de publication

La publication de formulaires dans Edge Delivery Services suit une approche en trois phases :

- **Phase 1 : publication du formulaire** - Publiez votre formulaire sur le réseau CDN et vérifiez le statut de publication
- **Phase 2 : configuration de la sécurité** - Configurez les politiques CORS et les filtres de référent pour des envois sécurisés
- **Phase 3 : accès et validation** - Tester la fonctionnalité de formulaire et valider l’ensemble du workflow

Chaque phase s’appuie sur la précédente pour assurer un déploiement sécurisé et fonctionnel.

### Phase 1 : Publier Votre Formulaire

+++ Étape 1 : lancer la publication

1. **Accéder à votre formulaire** : ouvrez votre formulaire adaptatif dans l’éditeur universel
2. **Démarrer la publication** : cliquez sur l’icône **Publier** dans la barre d’outils

   ![Cliquer sur Publier](/help/forms/assets/publish-icon-eds-form.png)

+++


+++ Étape 2 : vérifier et confirmer

1. **Vérification de la publication des ressources** : le système affiche toutes les ressources en cours de publication, y compris votre formulaire

   ![Publication en un clic](/help/forms/assets/on-click-publish.png)

2. **Confirmer la publication** : cliquez sur **Publier** pour continuer
3. **Vérifier la réussite** : recherchez le message de confirmation

   ![Publication réussie](/help/forms/assets/publish-success.png)

+++


+++ Étape 3 : vérification du statut de publication

**Vérifier le statut** : cliquez de nouveau sur l’icône **Publier** pour afficher le statut actuel

![Statut de publication](/help/forms/assets/publish-status.png)

**Point de contrôle de validation :**

- Le formulaire affiche le statut « Publié » dans l’éditeur
- Aucun message d’erreur lors du processus de publication
- Le formulaire apparaît dans la liste des ressources publiées

+++


+++ Gestion du Forms publié

**Pour dépublier un formulaire :**

1. Ouvrez votre formulaire dans l’éditeur
2. Cliquez sur le menu à trois points (⋯) dans le coin supérieur droit
3. Sélectionnez **Dépublier**

![Dépublier le formulaire](/help/forms/assets/unpublish--form.png)

+++


### Phase 2 : configuration des paramètres de sécurité

+++ Pourquoi une configuration de sécurité est requise

Pour activer l’envoi sécurisé de formulaires, vous devez configurer les paramètres de sécurité qui :

- Autoriser Edge Delivery Services à envoyer des données à AEM
- Empêcher tout accès non autorisé à votre instance AEM
- Activer CORS (partage de ressources entre origines multiples) pour les envois de formulaire
- Filtrer les requêtes pour autoriser uniquement les domaines Edge Delivery légitimes

>[!IMPORTANT]
>
>**Obligatoire pour la production** : ces configurations sont obligatoires pour que les envois de formulaire fonctionnent dans les environnements de production.

+++



+++ Étape 1 : configurer l’URL d’envoi de formulaire

**Objectif** : envoyer directement des formulaires à votre instance AEM

**Emplacement du fichier** : `blocks/form/constant.js` dans votre projet Edge Delivery Services

**Exemples de configuration :**

```javascript
// Production Environment
export const submitBaseUrl = 'https://publish-p120-e12.adobeaemcloud.com';

// Local Development Environment  
export const submitBaseUrl = 'http://localhost:4503';

// Staging Environment
export const submitBaseUrl = 'https://publish-staging-p120-e12.adobeaemcloud.com';
```

**Point de contrôle de validation :**

- `constant.js` fichier mis à jour avec l’URL de publication AEM appropriée
- L’URL correspond à votre environnement (production, évaluation ou local).
- Pas de barre oblique de fin dans l’URL

+++



+++ Étape 2 : configurer les paramètres CORS

**Objectif** : autoriser les demandes d’envoi de formulaire provenant de domaines Edge Delivery Services

**Implémentation** : ajoutez la configuration CORS à votre Dispatcher AEM ou à votre configuration Apache

```apache
# Local Development Environment
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(http://localhost(:\d+)?$)#" CORSTrusted=true

# Edge Delivery Services - Preview/Stage Environment  
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.page$)#" CORSTrusted=true

# Edge Delivery Services - Production Environment
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.live$)#" CORSTrusted=true
```

**Point de contrôle de validation :**

- Règles CORS appliquées à la configuration du Dispatcher
- Tous les domaines requis (localhost, hlx.page, hlx.live) sont inclus
- Configuration déployée dans l’environnement cible

**Documentation de référence :**

- [ Guide de configuration CORS ](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/configurations/cors)
- [Documentation sur le filtre Référent](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/headless/deployment/referrer-filter)

+++



+++ Étape 3 : Configurer le filtre Référent

**Objectif** : limiter les opérations d’écriture aux domaines Edge Delivery Services autorisés

**Méthode d’implémentation** : configuration via Cloud Manager dans AEM as a Cloud Service

**Fichier de configuration** : ajoutez à la configuration OSGi de votre projet.

```json
{
  "allow.empty": false,
  "allow.hosts": [],
  "allow.hosts.regexp": [
    "https://.*\\.hlx\\.page:443",
    "https://.*\\.hlx\\.live:443"
  ],
  "filter.methods": [
    "POST",
    "PUT", 
    "DELETE",
    "COPY",
    "MOVE"
  ],
  "exclude.agents.regexp": [
    ""
  ]
}
```

**Répartition de la configuration :**

- **`allow.empty`** : rejette les requêtes sans en-tête référent
- **`allow.hosts.regexp`** : autorise les requêtes provenant des domaines Edge Delivery Services
- **`filter.methods`** : applique le filtrage à ces méthodes HTTP
- **`exclude.agents.regexp`** : agents utilisateurs exclus du filtrage

**Point de contrôle de validation :**

- Configuration du filtrage des référents déployée via Cloud Manager
- Configuration active sur l’instance de publication AEM
- L’envoi de formulaire de test fonctionne à partir du domaine Edge Delivery Services
- Les domaines non autorisés ne peuvent pas envoyer de formulaires

**Documentation de référence :**

- [Configuration du filtrage des référents via Cloud Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing)

+++


### Phase 3 : Accéder Au Formulaire Publié



+++ Structure d’URL pour Edge Delivery Services

**Format d’URL standard :**

```
https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>
```

**Composants d’URL :**

- **`<branch>`** : nom de la branche Git (généralement `main`)
- **`<repo>`** : nom du référentiel
- **`<owner>`** : nom d’utilisateur ou d’organisation GitHub
- **`<form_name>`** : nom de votre formulaire (en minuscules, avec des tirets)

**URL spécifiques à un environnement :**

```
# Production Environment (.aem.live)
https://main--universaleditor--wkndforms.aem.live/content/forms/af/wknd-form

# Preview Environment (.aem.page) 
https://main--universaleditor--wkndforms.aem.page/content/forms/af/wknd-form
```

+++



+++ Étapes de validation finales

**Vérifier l’accessibilité du formulaire :**

1. **Tester le chargement du formulaire** : consultez l’URL de votre formulaire et confirmez qu’il se charge correctement
2. **Tester l’envoi du formulaire** : remplissez et envoyez le formulaire pour vérifier le traitement des données
3. **Vérifier le responsive design** : testez le formulaire sur différents appareils et tailles d’écran
4. **Valider la sécurité** : assurez-vous que CORS et le filtre référent fonctionnent correctement

**Résultats attendus :**

- Le formulaire se charge sans erreur
- Tous les champs de formulaire s’affichent correctement
- Processus d’envoi de formulaire réussis
- Les données apparaissent dans la destination configurée (feuille de calcul, e-mail, etc.)
- Aucune erreur de console liée à CORS ou aux politiques de sécurité

+++


## Étapes suivantes


- [Configuration des actions d’envoi de formulaire](/help/edge/docs/forms/universal-editor/submit-action.md)
- [Donner un style et un thème à vos formulaires](/help/edge/docs/forms/universal-editor/style-theme-forms.md)
- [Création de dispositions de formulaires réactifs](/help/edge/docs/forms/universal-editor/responsive-layout.md)
- [Ajouter une protection reCAPTCHA](/help/edge/docs/forms/universal-editor/recaptcha-forms.md)



