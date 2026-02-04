---
title: Appeler une interface utilisateur associée sur l’instance de publication
description: Découvrez comment intégrer et appeler l’interface utilisateur d’AEM Forms Associate sur les instances de publication pour permettre aux professionnels en contact avec les clients de générer des communications interactives personnalisées en temps réel.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
hide: true
hidefromtoc: true
source-git-commit: 2f3badafddfdfe1dd21eb74be7189102aa0474bc
workflow-type: tm+mt
source-wordcount: '831'
ht-degree: 3%

---


# Générer des communications personnalisées avec l’interface utilisateur associée

<span> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à partir de votre adresse professionnelle à `aem-forms-ea@adobe.com` pour demander l’accès.</span>

L’interface utilisateur Associé peut être directement appelée sur les instances de publication, ce qui permet aux professionnels en contact avec les clients, tels que les associés de terrain et les agents de service, de générer des communications personnalisées en temps réel lors des interactions des clients.

Le tableau ci-dessous décrit les différents scénarios réels dans lesquels l’interface utilisateur d’Associate peut être utilisée pour envoyer des messages personnalisés aux clients :

| Industrie | Cas d’utilisation |
|----------|----------|
| **Services financiers** | Générer des lettres de confirmation de prêt en temps réel, des relevés de compte et des résumés de profil de risque lors des réunions clients |
| **Assurance** | Produire instantanément des cartes de preuve d&#39;assurance et des résumés de disposition des réclamations aux comptoirs de service |
| **Healthcare** | Créez des résumés de plans de traitement des patients avec les montants et les calendriers de rémunération calculés |
| **Gouvernement** | Générer sur place des rapports de vérification de la police, des reçus de services aux citoyens et des résumés de mise à jour des cas |

## Prérequis

Avant d’intégrer l’interface utilisateur associée à votre application, vérifiez les points suivants :

- Communication interactive créée et publiée
- Navigateur avec prise en charge des fenêtres contextuelles activée
- Associer [les utilisateurs doivent faire partie du groupe forms-associates](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/administrator-help/setup-organize-users/creating-configuring-roles#assign-a-role-to-users-and-groups)
- Authentification configurée - [SAML 2.0](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/authentication/saml-2-0)

>[!NOTE]
>
> Pour l’interface utilisateur associée, des configurations SAML supplémentaires sont requises en plus de la configuration standard expliquée dans l’article [&#x200B; Authentification SAML 2.0 &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/authentication/saml-2-0). Consultez la section [Configurations SAML supplémentaires pour l’interface utilisateur associée](#additional-saml-configurations-for-associate-ui) pour plus d’informations.

### Configurations SAML supplémentaires pour l’interface utilisateur associée

Lors de la configuration de l’authentification SAML 2.0 pour l’interface utilisateur associée, vous devez appliquer les paramètres spécifiques suivants dans vos fichiers de configuration OSGi.

#### Gestionnaire d’authentification SAML

Créez le fichier `com.adobe.granite.auth.saml.SamlAuthenticationHandler~saml.cfg.json` dans `ui.config/src/main/content/jcr_root/apps/<project-name>/osgiconfig/config.publish` :

```json
  {
    "path": ["/libs/fd/associate"],
    "serviceProviderEntityId": "https://publish-p{program-id}-e{env-id}.adobeaemcloud.com",
    "assertionConsumerServiceURL": "https://publish-p{program-id}-e{env-id}.adobeaemcloud.com/libs/fd/associate/saml_login",
    "idpUrl": "https://login.microsoftonline.com/{azure-tenant-id}/saml2",
    "idpCertAlias": "{your-certificate-alias}",
    "idpIdentifier": "https://sts.windows.net/{azure-tenant-id}/",
    "userIDAttribute": "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name",
    "createUser": true,
    "userIntermediatePath": "saml",
    "synchronizeAttributes": [
      "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname=profile/givenName",
      "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname=profile/familyName",
      "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress=profile/email"
      ],
      "addGroupMemberships": true,
      "defaultGroups": ["forms-associates"],
      "defaultRedirectUrl": "/libs/fd/associate/ui.html",
      "idpHttpRedirect": false,
      "service.ranking": 5002
  }
```

| Propriété | Description |
|----------|-------------|
| `path` | Doit être défini sur `/libs/fd/associate` pour l’interface utilisateur associée |
| `defaultGroups` | Définissez sur `forms-associates` pour affecter automatiquement des utilisateurs au groupe requis |
| `defaultRedirectUrl` | Redirige les utilisateurs authentifiés vers l’interface utilisateur associée |
| `idpHttpRedirect` | Doit être `false` pour le flux initié par le SP |
| `idpCertAlias` | Doit correspondre exactement à l’alias du certificat dans Trust Store (sensible à la casse). |

#### Authentificateur Sling

Mettez à jour le fichier `org.apache.sling.engine.impl.auth.SlingAuthenticator~saml.cfg.json` dans `ui.config/src/main/content/jcr_root/apps/<project-name>/osgiconfig/config.publish` :

```json
{
  "sling.auth.requirements": ["+/libs/fd/associate/ui.html"],
  "sling.auth.anonymous": false
}
```

#### Filtre Dispatcher

S’il n’est pas déjà présent, ajoutez les règles suivantes à votre fichier `dispatcher/src/conf.dispatcher.d/filters/filters.any` :

```json
  # Allow Interactive Communications APIs and Associate UI
  /XXXX { /type "allow" /method '(GET|OPTIONS)' /url "/adobe/communications" }
  /XXXX { /type "allow" /method '(GET|POST|OPTIONS)' /url "/adobe/communications/*" }
  /XXXX { /type "allow" /method "GET" /url "/content/dam/fd:fonts/*" }
  /XXXX { /type "allow" /method '(GET|OPTIONS)' /url "/libs/fd/associate/*" }
```

>[!NOTE]
>
> Remplacez `XXXX` par la séquence numérique appropriée utilisée dans votre fichier `filters.any` existant.

## Appel de l’interface utilisateur associée sur l’instance de publication

Pour appeler l’interface utilisateur associée à partir de votre application, configurez l’URL de l’instance de publication, préparez la payload de données et utilisez la fonction d’intégration pour lancer l’interface utilisateur associée dans une nouvelle fenêtre de navigateur.

### Étape 1 : configurer l’URL de l’instance de publication

L’interface utilisateur associée est accessible via un point d’entrée spécifique sur votre instance de publication AEM Forms Cloud Service :

```javascript
const AEM_URL = 'https://publish-p{program-id}-e{env-id}.adobeaemcloud.com/libs/fd/associate/ui.html';
```

Remplacez `{program-id}` et `{env-id}` par vos valeurs d’environnement réelles.

### Étape 2 : préparation du payload de données

Structurez la payload de données au format suivant :

```javascript
const data = {
  id: "your-ic-id",              // Required: Interactive Communication ID
  prefill: {                      // Optional: Data to prefill the IC
    serviceName: "YourService",
    serviceParams: { key: "value" }
  },
  options: {}                     // Optional: Additional configuration options
};
```

**Composants de payload :**

| Composant | Requis | Description |
|-----------|----------|-------------|
| `id` | Oui | Identifiant de la communication interactive (IC) à charger |
| `prefill` | Facultatif | Contient la configuration du service pour le préremplissage des données. |
| `prefill.serviceName` | Facultatif | Nom du service de modèle de données de formulaire à appeler pour le préremplissage des données |
| `prefill.serviceParams` | Facultatif | Paires clé-valeur transmises au service de préremplissage |
| `options` | Facultatif | Propriétés supplémentaires prises en charge pour le rendu PDF : paramètres régionaux, includeAttachments, embedFonts, makeAccessible |

### Étape 3 : implémentation de la fonction d’intégration

Créez une fonction JavaScript pour lancer l’interface utilisateur associée et gérer la communication du message :

```javascript
function launchAssociateUI(icId, prefillService, prefillParams, options) {
  if (!icId) {
    console.error('IC ID required');
    return;
  }
   
  const data = {
    id: icId,
    prefill: {
      serviceName: prefillService || '',
      serviceParams: prefillParams || {}
    },
    options: options || {}
  };
   
  const AEM_URL = 'https://your-aem.adobeaemcloud.com/libs/fd/associate/ui.html';
  const win = window.open(AEM_URL, '_blank');
   
  if (!win) {
    alert('Please enable pop-ups for this site');
    return;
  }
   
  const readyHandler = (event) => {
    if (event.data && event.data.type === 'READY' && event.data.source === 'APP') {
      win.postMessage({ type: 'INIT', source: 'PORTAL', data: data }, '*');
      window.removeEventListener('message', readyHandler);
    }
  };
   
  window.addEventListener('message', readyHandler);
   
  // Fallback timeout in case READY message is missed
  setTimeout(() => {
    if (win && !win.closed) {
      win.postMessage({ type: 'INIT', source: 'PORTAL', data: data }, '*');
      window.removeEventListener('message', readyHandler);
    }
  }, 1000);
}
```

### Étape 4 : appeler la fonction

Appelez la fonction avec les paramètres appropriés :

```javascript
// Basic invocation with IC ID only
launchAssociateUI('12345', '', {}, {});

// With prefill service
launchAssociateUI('12345', 'FdmTestData', 
  { customerId: '101'}, {});

// With all parameters
launchAssociateUI('12345', 'FdmTestData', 
  { policyNumber: 'POL-123' }, 
  { locale: 'en', acrobatVersion: 'Acrobat_11' });
```

## Tester votre intégration avec un exemple de page HTML

Pour observer comment l’interface utilisateur associée apparaît sur le front-end et tester votre intégration, voici un exemple simple d’HTML. Cet exemple de page vous permet de saisir l’ID d’IC, de configurer les paramètres de service de préremplissage, de définir les options de PDF et de lancer l’interface utilisateur associée sur votre instance de publication.

```html
<!DOCTYPE html>
<html>
<head>
  <title>Associate UI Integration</title>
  <style>
    body { 
      font-family: sans-serif; 
      max-width: 600px; 
      margin: 50px auto; 
      padding: 20px; 
    }
    .form-group { 
      margin: 20px 0; 
    }
    label { 
      display: block; 
      margin-bottom: 5px; 
      font-weight: bold; 
    }
    input, textarea { 
      width: 100%; 
      padding: 8px; 
      border: 1px solid #ccc; 
      border-radius: 4px; 
      box-sizing: border-box;
    }
    textarea { 
      height: 80px; 
      font-family: monospace; 
    }
    button { 
      padding: 10px 20px; 
      margin: 5px; 
      cursor: pointer; 
      border-radius: 4px;
    }
    .btn-primary { 
      background: #007bff; 
      color: white; 
      border: none; 
    }
    .btn-primary:hover {
      background: #0056b3;
    }
    .error { 
      color: red; 
      font-size: 12px; 
      display: none; 
    }
  </style>
</head>
<body>
  <h1>Launch Associate UI</h1>
  
  <form id="form">
    <div class="form-group">
      <label>IC ID *</label>
      <input type="text" id="icId" placeholder="Enter Interactive Communication ID" required>
    </div>
    
    <div class="form-group">
      <label>Prefill Service</label>
      <input type="text" id="serviceName" placeholder="e.g., CustomerDataService">
    </div>
    
    <div class="form-group">
      <label>Service Parameters (JSON)</label>
      <textarea id="serviceParams" placeholder='{"customerId": "12345"}'>{}</textarea>
      <span id="paramsError" class="error">Invalid JSON format</span>
    </div>
    
    <div class="form-group">
      <label>Options (JSON)</label>
      <textarea id="options" placeholder='{"mode": "edit", "locale": "en_US"}'>{}</textarea>
      <span id="optionsError" class="error">Invalid JSON format</span>
    </div>
    
    <button type="button" onclick="reset()">Reset</button>
    <button type="button" class="btn-primary" onclick="launch()">Launch Associate UI</button>
  </form>

  <script>
    // Replace with your AEM Publish instance URL
    const AEM_URL = 'https://publish-p{program-id}-e{env-id}.adobeaemcloud.com/libs/fd/associate/ui.html';
    
    function validateJSON(str, errorId) {
      const err = document.getElementById(errorId);
      try {
        const obj = JSON.parse(str || '{}');
        err.style.display = 'none';
        return obj;
      } catch (e) {
        err.style.display = 'block';
        return null;
      }
    }
    
    function launch() {
      const icId = document.getElementById('icId').value.trim();
      if (!icId) { 
        alert('IC ID is required'); 
        return; 
      }
      
      const params = validateJSON(document.getElementById('serviceParams').value, 'paramsError');
      const opts = validateJSON(document.getElementById('options').value, 'optionsError');
      
      if (!params || !opts) { 
        alert('Please fix JSON errors before launching'); 
        return; 
      }
      
      const data = {
        id: icId,
        prefill: {
          serviceName: document.getElementById('serviceName').value.trim(),
          serviceParams: params
        },
        options: opts
      };
      
      const win = window.open(AEM_URL, '_blank');
      if (!win) { 
        alert('Pop-up blocked. Please enable pop-ups for this site.'); 
        return; 
      }
      
      const handler = (e) => {
        if (e.data && e.data.type === 'READY' && e.data.source === 'APP') {
          win.postMessage({ type: 'INIT', source: 'PORTAL', data }, '*');
          window.removeEventListener('message', handler);
        }
      };
      
      window.addEventListener('message', handler);
      
      // Fallback timeout in case READY message is missed
      setTimeout(() => {
        if (win && !win.closed) {
          win.postMessage({ type: 'INIT', source: 'PORTAL', data }, '*');
          window.removeEventListener('message', handler);
        }
      }, 1000);
    }
    
    function reset() {
      document.getElementById('form').reset();
      document.getElementById('serviceParams').value = '{}';
      document.getElementById('options').value = '{}';
      document.getElementById('paramsError').style.display = 'none';
      document.getElementById('optionsError').style.display = 'none';
    }
  </script>
</body>
</html>
```

### Fonctionnement de l’exemple

1. **Champ ID IC** : renseignez l’identifiant de la communication interactive (obligatoire)
2. **Service de préremplissage** : spécifiez le nom du service de modèle de données de formulaire pour le préremplissage des données
3. **Paramètres de service** : saisissez l’objet JSON avec les paramètres à transmettre au service de préremplissage
4. **Options** : renseignez les options de configuration de PDF, par exemple, les paramètres régionaux, includeAttachments, embedFonts, makeAccessible
5. **Bouton Lancer** : ouvre l’interface utilisateur associée dans une nouvelle fenêtre et envoie les données d’initialisation

## Exemples de payload de données

### Payload minimale (IC uniquement)

Utilisez cette option lorsqu’aucune donnée de préremplissage n’est requise :

```json
{
  "id": "12345",
  "prefill": { 
    "serviceName": "", 
    "serviceParams": {} 
  },
  "options": {}
}
```

### Avec données de préremplissage

Utilisez ceci pour remplir dynamiquement l’IC avec des données client :

```json
{
  "id": "12345",
  "prefill": {
    "serviceName": "IC_FDM",
    "serviceParams": {
      "customerId": "101",
      "accountNumber": "ACC-98765"
    }
  },
  "options": {}
}
```

### Avec la configuration des options

Utilisez cette option pour spécifier des options de rendu supplémentaires :

```json
{
  "id": "12345",
  "prefill": {
    "serviceName": "IC_FDM",
    "serviceParams": {
      "customerId": "101",
      "accountNumber": "ACC-98765"
    }
  },
  "options": { 
      locale: "en_US",
      includeAttachments: "true",
      webOptimized: "false",
      embedFonts: "false",
      makeAccessible: "false"
  }
}
```

## Résolution des problèmes

### Fenêtre contextuelle bloquée

**Problème** : la fenêtre Associer l’interface utilisateur ne s’ouvre pas.

**Solution** :
- Activation des fenêtres contextuelles pour votre domaine dans les paramètres du navigateur
- Assurez-vous que `window.open()` est appelé à partir d’une action de l’utilisateur (par exemple, clic sur un bouton).
- Tester avec différents navigateurs pour identifier le comportement de blocage

### Données non chargées

**Problème** : la communication interactive s’ouvre mais les données ne sont pas renseignées.

**Solution** :
- Vérifiez que l&#39;ID IC est correct et que l&#39;IC est publié
- Vérifiez la console du navigateur afin d’identifier les erreurs JavaScript.
- Assurez-vous que la structure `postMessage` correspond exactement à la spécification
- Vérifiez que le service de modèle de données de formulaire est correctement configuré.

### Erreur d’authentification

**Problème** : l’utilisateur reçoit une erreur d’authentification à l’ouverture de l’interface utilisateur associée.

**Solution** :
- Configurez l’authentification SAML 2.0 sur l’instance de publication
- Vérifiez que l’utilisateur fait partie du groupe **forms-associates**
- Vérifier les paramètres de temporisation de session

### Erreurs CORS

**Problème** : erreurs de partage de ressources entre origines multiples dans la console.

**Solution** :
- Pour le développement : utiliser `'*'` comme origine cible dans `postMessage`
- Pour la production : spécifiez l’URL d’origine exacte de votre application
- Vérifiez que les paramètres CORS de l’instance de publication autorisent votre domaine d’application

<!--## Best Practices

When implementing the Associate UI integration, follow these best practices:

1. **Validation**: Always validate the IC ID and JSON payload before sending
2. **Error Handling**: Implement proper error handling for `window.open()` failures
3. **User Experience**: Display a loading indicator while the Associate UI initializes
4. **Memory Management**: Remove event listeners after initialization to prevent memory leaks
5. **Testing**: Test the integration with popup blockers enabled to ensure graceful handling
6. **User Permissions**: Verify users have appropriate access to the forms-associates group-->

## Voir également

- [Associer l’interface utilisateur dans l’éditeur de communication interactive](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md)
- [Communications interactives sur le cloud](/help/forms/early-access-ea-features.md#interactive-communications-on-cloud)
- [Fonctionnalités d’accès anticipé](/help/forms/early-access-ea-features.md)