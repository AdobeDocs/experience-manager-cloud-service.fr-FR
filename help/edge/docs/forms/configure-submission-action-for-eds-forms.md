---
title: Configurer des actions d’envoi pour AEM Forms avec Edge Delivery Services
description: Découvrez comment configurer des actions d’envoi dans AEM Forms à l’aide d’Edge Delivery Services. Choisissez entre le service d’envoi de formulaires et l’action d’envoi de l’instance de publication AEM pour gérer les données de formulaire de manière sécurisée et efficace.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 8f490054-f7b6-40e6-baa3-3de59d0ad290
source-git-commit: 2d16a9bd1f498dd0f824e867fd3b5676fb311bb3
workflow-type: ht
source-wordcount: '810'
ht-degree: 100%

---

# Configurer les actions Envoyer pour AEM Forms

Configurez la gestion de l’envoi de formulaire pour acheminer les données vers des feuilles de calcul, des e-mails ou des systèmes back-end à l’aide d’AEM Forms avec Edge Delivery Services.

## Guide de décision rapide

Choisissez votre méthode d’envoi :

| Méthode | Idéale pour | Complexité de la configuration | Cas d’utilisation |
|--------|----------|------------------|-----------|
| **Service d’envoi de formulaires** | Capture de données simple | Faible | Formulaires de contact, enquêtes, collecte de données de base |
| **Envoi de publication AEM** | Workflows complexes | Élevée | Intégrations d’entreprise, traitement personnalisé, workflows |

## Conditions préalables

Avant de configurer les actions d’envoi, vérifiez les points suivants :

- Instance AEM Forms as a Cloud Service
- Projet Edge Delivery Services configuré
- Formulaire créé à l’aide de la création de documents ou de l’éditeur universel
- Autorisations requises pour les destinations cibles (feuilles de calcul, systèmes de messagerie ou AEM)

+++ Méthode 1 : service d’envoi de formulaires

Le service d’envoi de formulaires est un point d’entrée hébergé par Adobe idéal pour les scénarios de capture de données simples.

### Destinations prises en charge

- **Feuilles de calcul** : Google Sheets, Microsoft Excel (OneDrive/SharePoint).
- **E-mail** : envoyer les données de formulaire aux adresses e-mail spécifiées

### Étapes de configuration

1. **Configuration de l’accès à la destination**
   - Pour les feuilles de calcul : octroyez l’autorisation de modification pour `forms@adobe.com` sur une feuille de calcul cible.
   - Pour les e-mails : vérifiez que les adresses e-mail des personnes destinataires sont accessibles.

2. **Configuration de l’envoi de formulaire**
   - Ouvrez votre formulaire dans l’environnement de création.
   - Définissez l’action Envoyer sur « Service d’envoi de formulaires ».
   - Indiquez l’URL de la feuille de calcul ou les adresses e-mail cibles.
   - Enregistrez et publiez le formulaire.

3. **Test de l’envoi**
   - Envoyez les données de test via le formulaire.
   - Vérifiez que les données apparaissent dans la destination cible.
   - Consultez les journaux d’erreurs en cas d’échec de l’envoi.

### Remarques importantes

- Le compte de service `forms@adobe.com` nécessite un accès en modification aux feuilles de calcul cibles.
- Les notifications par e-mail sont envoyées immédiatement après l’envoi du formulaire.
- La validation des données se produit au niveau du service.

![Flux du service d’envoi de formulaires](/help/forms/assets/eds-fss.png)

+++

+++ Méthode 2 : envoi de publication AEM

Envoyez directement les données de formulaire à votre instance de publication AEM as a Cloud Service pour un traitement complexe.

### Quand utiliser la publication AEM

- Workflows AEM personnalisés requis après l’envoi
- Intégration du modèle de données de formulaire (FDM) aux bases de données
- Intégrations de services tiers (Marketo, Power Automate, Workfront Fusion)
- Bibliothèques de données de stockage Azure Blob ou SharePoint
- Logique complexe de validation ou de traitement côté serveur

### Actions d’envoi disponibles

- [Envoyer au point d’entrée REST](/help/forms/configure-submit-action-restpoint.md)
- [Envoyer un e-mail via des services de messagerie AEM](/help/forms/configure-submit-action-send-email.md)
- [Envoyer à l’aide du modèle de données de formulaire](/help/forms/configure-data-sources.md)
- [Appeler le workflow AEM](/help/forms/aem-forms-workflow-step-reference.md)
- [Envoyer à SharePoint](/help/forms/configure-submit-action-sharepoint.md)
- [Envoyer à OneDrive](/help/forms/configure-submit-action-onedrive.md)
- [Envoyer au stockage Blob Azure](/help/forms/configure-submit-action-azure-blob-storage.md)
- [Envoyer à Microsoft Power Automate](/help/forms/forms-microsoft-power-automate-integration.md)
- [Envoyer à Adobe Workfront Fusion](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
- [Envoyer à Adobe Marketo Engage](/help/forms/submit-adaptive-form-to-marketo-engage.md)

![Flux d’envoi de publication AEM](/help/forms/assets/eds-aem-publish.png)

### Configuration requise

#### &#x200B;1. Mettre à jour l’URL de l’instance AEM dans Edge Delivery

Mettez à jour l’URL de l’instance AEM Cloud Service dans le fichier `constant.js` du bloc `form` sous `submitBaseUrl`. Vous pouvez configurer l’URL en fonction de votre environnement :

**Pour l’instance Cloud Service**

```js
export const submitBaseUrl = '<aem-publish-instance-URL>';
```

**Pour le développement local**

```js
export const submitBaseUrl = 'http://localhost:<port-number>';
```

#### &#x200B;2. Filtre de référent OSGi

Configurez le filtre de référent pour autoriser vos domaines de site Edge Delivery spécifiques :

1. Créez ou mettez à jour le fichier de configuration OSGi : `org.apache.sling.security.impl.ReferrerFilter.cfg.json`

2. Ajoutez la configuration suivante à vos domaines de site spécifiques :

   ```json
   {
     "allow.empty": false,
     "allow.hosts": [
       "main--abc--adobe.aem.live",
       "main--abc1--adobe.aem.live"
     ],
     "allow.hosts.regexp": [
       "https://.*\\.aem\\.live:443",
       "https://.*\\.aem\\.page:443",
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

3. Déployer la configuration via Cloud Manager

Pour obtenir une configuration détaillée du filtre de référent OSGi, consultez le [Guide du filtre de référent](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/headless/deployment/referrer-filter).

#### &#x200B;3. Problèmes liés à CORS (partage des ressources entre origines multiples)

Configurez les paramètres CORS dans AEM pour autoriser les requêtes provenant de vos domaines de site Edge Delivery spécifiques :

**Localhost du développeur**

```apache
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(http://localhost(:\d+)?$)#" CORSTrusted=true
```

**Sites Edge Delivery : ajoutez chaque domaine de site individuellement**.

```apache
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://main--abc--adobe\.aem\.live$)#" CORSTrusted=true
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://main--abc1--adobe\.aem\.live$)#" CORSTrusted=true
```

**Domaines Franklin hérités (s’ils sont toujours utilisés)**.

```apache
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.page$)#" CORSTrusted=true  
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.live$)#" CORSTrusted=true
```

>[!NOTE]
>
>Remplacez `main--abc--adobe.aem.live` et `main--abc1--adobe.aem.live` par vos domaines de site réels. Chaque site hébergé à partir du même référentiel requiert une entrée de configuration CORS distincte.

Pour obtenir une configuration détaillée de CORS, consultez le [Guide de configuration de CORS](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/configurations/cors).


Pour activer la norme CORS pour votre environnement de développement local, reportez-vous à l’article [Comprendre le partage de ressources entre origines multiples (CORS)](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing).

<!--
#### 4. CDN Redirect Rules

Configure your Edge Delivery CDN to route submissions:

- Route requests from `/adobe/forms/af/submit/...` to your AEM Publish instance
- Implementation varies by CDN provider (Fastly, Akamai, Cloudflare)-->

#### &#x200B;4. Configuration du formulaire

1. Créez un formulaire dans l’éditeur universel.
2. Configurez l’action Envoyer pour cibler l’action AEM Forms.
3. Indiquez le chemin du point d’entrée d’envoi.
4. Publiez le formulaire sur le site Edge Delivery.

+++
<!--
+++ Form Embedding

Embed forms created in one location into different web pages or sites.

### Use Cases

- Reuse standard forms across multiple landing pages
- Include specialized forms in Document-Authored content
- Maintain single form across multiple EDS projects

### CORS Configuration

Configure Cross-Origin Resource Sharing on the form source:

1. **Add CORS Headers** to form source responses:
   - `Access-Control-Allow-Origin: https://your-host-domain.com`
   - `Access-Control-Allow-Methods: GET, OPTIONS`  
   - `Access-Control-Allow-Headers: Content-Type`

2. **Example Configuration**:

        # Configuration for site hosting the form
        headers:
          - path: /forms/**
            custom:
              Access-Control-Allow-Origin: https://host-domain.com
              Access-Control-Allow-Methods: GET, OPTIONS

### Embedding Steps

1. **Create and Publish Form**
   - Build form using Document Authoring or Universal Editor
   - Configure submission method (FSS or AEM Publish)
   - Publish to standalone URL

2. **Configure CORS**
   - Set up CORS headers on form source site
   - Allow host page domain to fetch form

3. **Embed in Host Page**
   - Add form embedding block to host page
   - Point block to published form URL
   - Publish host page

![Embedded Form Architecture](/help/forms/assets/eds-embedded-form.png)

+++-->

+++ Problèmes courants

| Problème | Solution |
|-------|----------|
| **L’envoi du formulaire échoue** | Vérifier les erreurs de console, vérifier l’URL du point d’entrée, confirmer les autorisations |
| **Le formulaire incorporé n’apparaît pas** | Configurer des en-têtes CORS sur la source du formulaire, vérifier l’URL du formulaire |
| **Erreurs 403/401 avec AEM** | Mettre à jour le filtre de référent Sling, vérifier les paramètres d’authentification |
| **Les données n’atteignent pas la feuille de calcul** | Vérifier que `forms@adobe.com` a un accès en modification, vérifier l’URL de la feuille de calcul |
| **Erreurs CORS** | Ajouter les en-têtes `Access-Control-Allow-Origin` appropriés à la source du formulaire |

+++

## Exemples de configurations

+++ Formulaire basé sur des documents avec envoi de feuille de calcul

1. Créer la structure de formulaire dans Google Docs/Sheets
2. Configurer le point d’entrée du service d’envoi de formulaires
3. Octroyer à `forms@adobe.com` un accès en modification à la feuille de calcul cible
4. Publier le document sur le site Edge Delivery
5. Tester l’envoi du formulaire et le flux de données

+++

+++ Formulaire d’éditeur universel avec workflow AEM

1. Créer un formulaire dans l’éditeur universel
2. Configurer l’action Envoyer sur « Appeler un workflow AEM »
3. Configurer Dispatcher et le filtre de référent sur la publication AEM
4. Configurer des règles de routage CDN
5. Publier le formulaire et tester l’exécution du workflow

+++

## Bonnes pratiques

- **Utilisez le service d’envoi de formulaire** pour les scénarios de capture de données simples.
- **Choisissez la publication AEM** lorsqu’un traitement ou des intégrations complexes sont requis.
- **Testez minutieusement** dans l’environnement d’évaluation avant le déploiement en production.
- **Surveillez les envois** à l’aide des journaux AEM et des erreurs de la console.
- **Implémentez une gestion des erreurs appropriée** pour les envois ayant échoué.
- **Validez les données** au niveau du client et du serveur.
- **Utilisez HTTPS** pour tous les envois de formulaires et la transmission de données.

## Rubriques connexes

- [Création basée sur des documents avec EDS Forms](/help/edge/docs/forms/tutorial.md)
- [Éditeur universel avec EDS Forms](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
- [Service d’envoi AEM Forms](/help/forms/forms-submission-service.md)
- [Configurer des sources de données](/help/forms/configure-data-sources.md)
- [Référence du workflow AEM Forms](/help/forms/aem-forms-workflow-step-reference.md)
