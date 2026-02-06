---
title: Intégrer l’interface utilisateur associée pour les communications interactives d’exécution
description: Découvrez comment intégrer l’interface utilisateur d’AEM Forms Associate à votre application pour permettre aux professionnels en contact avec la clientèle de générer des communications interactives personnalisées en temps réel sur les instances de publication.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
hide: true
hidefromtoc: true
source-git-commit: b76f6dfe2462cec187d549234e9050f8ca9a8cdf
workflow-type: tm+mt
source-wordcount: '1078'
ht-degree: 2%

---


# Intégrer l’interface utilisateur associée à votre application

<span> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à partir de votre adresse professionnelle à `aem-forms-ea@adobe.com` pour demander l’accès.</span>

Cet article explique comment intégrer l’interface utilisateur Associer à votre application, ce qui permet aux professionnels en contact avec les clients, tels que les associés de terrain et les agents de service, de générer des communications interactives personnalisées en temps réel sur les instances de publication.

## Prérequis

Avant d’intégrer l’interface utilisateur associée à votre application, vérifiez les points suivants :

- Communication interactive créée et publiée
- Navigateur avec prise en charge des fenêtres contextuelles activée
- Associer [les utilisateurs doivent faire partie du groupe forms-associates](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/administrator-help/setup-organize-users/creating-configuring-roles#assign-a-role-to-users-and-groups)
- Authentification configurée à l’aide de n’importe quel [mécanisme d’authentification pris en charge par AEM](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/authentication/authentication) (par exemple, SAML 2.0, OAuth ou gestionnaires d’authentification personnalisés)

>[!NOTE]
>
>- Cet article illustre la configuration de l’authentification à l’aide de SAML 2.0 avec [Microsoft Entra ID (Azure AD) comme fournisseur d’identité](https://learn.microsoft.com/en-us/power-pages/security/authentication/openid-settings).
>- Pour l’interface utilisateur associée, des configurations SAML supplémentaires sont requises en plus de la configuration standard expliquée dans l’article [ Authentification SAML 2.0 ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/authentication/saml-2-0). Consultez la section [Configurations SAML supplémentaires pour l’interface utilisateur associée](#additional-saml-configurations-for-associate-ui) pour plus d’informations.

### Configurations SAML supplémentaires pour l’interface utilisateur associée

Lors de la configuration de l’authentification SAML 2.0 pour l’interface utilisateur associée, vous devez appliquer les paramètres spécifiques suivants dans vos fichiers de configuration OSGi.

#### Gestionnaire d’authentification SAML

Le gestionnaire d’authentification SAML est une configuration d’usine OSGi qui permet plusieurs configurations SAML pour différentes arborescences de ressources. Cela permet des déploiements AEM multisites et vous permet d’ajouter des ressources d’interface utilisateur associées à votre configuration SAML existante.

Créez le fichier `com.adobe.granite.auth.saml.SamlAuthenticationHandler~saml.cfg.json` dans `ui.config/src/main/content/jcr_root/apps/<project-name>/osgiconfig/config.publish` :

```json
  {
    "path": ["/libs/fd/associate"],
    "serviceProviderEntityId": "https://publish-p{program-id}-e{env-id}.adobeaemcloud.com",
    "assertionConsumerServiceURL": "https://publish-p{program-id}-e{env-id}.adobeaemcloud.com/libs/fd/associate/saml_login"
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

L’authentificateur Sling applique l’authentification pour accéder aux ressources de l’interface utilisateur associées sur l’instance de publication.

Mettez à jour le fichier `org.apache.sling.engine.impl.auth.SlingAuthenticator~saml.cfg.json` dans `ui.config/src/main/content/jcr_root/apps/<project-name>/osgiconfig/config.publish` :

```json
{
  "sling.auth.requirements": ["+/libs/fd/associate/ui.html"],
  "sling.auth.anonymous": false
}
```

#### Filtre Dispatcher

Ajoutez les règles suivantes pour vous assurer que les API de communications interactives et l’interface utilisateur associée fonctionnent correctement sur l’instance de publication.

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

Cette section vous guide tout au long du lancement de l’interface utilisateur associée à partir de votre propre application. Pour commencer rapidement, suivez ces étapes, en commençant par un exemple de page HTML prêt à l’emploi, puis configurez-le pour votre environnement.

### Étape 1 : commencez par l’exemple de page HTML

Pour tester rapidement et comprendre le fonctionnement de l’intégration de l’interface utilisateur associée, utilisez l’exemple de page HTML suivant. Copiez ce code dans un fichier HTML et ouvrez-le dans votre navigateur.

Cet exemple fournit une interface de formulaire simple où vous pouvez saisir les détails de votre communication interactive et lancer l’interface utilisateur associée en un seul clic.

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

### Étape 2 : configurer l’URL de votre instance de publication

Avant de pouvoir lancer l’interface utilisateur associée, vous devez pointer l’exemple vers votre instance de publication AEM Forms Cloud Service.

Dans l’exemple HTML ci-dessus, localisez la ligne suivante dans la section `<script>` :

```javascript
const AEM_URL = 'https://publish-p{program-id}-e{env-id}.adobeaemcloud.com/libs/fd/associate/ui.html';
```

Remplacez les valeurs d’espace réservé par les détails de votre environnement réel :
- `{program-id}` : identifiant de votre programme AEM Cloud Service
- `{env-id}` : identifiant de votre environnement

Par exemple, si votre ID de programme est `12345` et que l’ID d’environnement est `67890`, l’URL devient :

```javascript
const AEM_URL = 'https://publish-p12345`-e67890.adobeaemcloud.com/libs/fd/associate/ui.html';
```

>[!NOTE]
>
> Pour des raisons de sécurité, les paramètres tels que l’ID de communication interactive, le service de préremplissage et les paramètres de service ne sont pas transmis via l’URL. Au lieu de cela, ces paramètres sont transmis en toute sécurité à l’aide de l’API `postMessage` JavaScript.

### Étape 3 : comprendre la fonction d’intégration de JavaScript

L’exemple d’HTML utilise la fonction JavaScript suivante pour lancer l’interface utilisateur associée. Cette fonction valide l’ID IC, construit la payload de données, ouvre l’interface utilisateur associée dans une nouvelle fenêtre de navigateur et envoie les données à l’aide de l’API `postMessage` du navigateur.

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

La fonction accepte quatre paramètres : l’ID IC (obligatoire), le nom du service de préremplissage, les paramètres de service de préremplissage et des options supplémentaires. Ces paramètres sont structurés dans la payload de données comme décrit ci-dessous.

### Étape 4 : comprendre la structure de la payload des données

**Format de payload :**

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
| `prefill` | Facultatif | Contient la configuration du service pour le préremplissage des données |
| `prefill.serviceName` | Facultatif | Nom du service de modèle de données de formulaire à appeler pour le préremplissage des données |
| `prefill.serviceParams` | Facultatif | Paires clé-valeur transmises au service de préremplissage |
| `options` | Facultatif | Propriétés supplémentaires prises en charge pour le rendu PDF : paramètres régionaux, includeAttachments, embedFonts, makeAccessible |

#### Exemples de payload de données

**Payload minimale (ID IC uniquement)**

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

**Avec Données De Préremplissage**

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

**Avec les options de rendu PDF**

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
      "locale": "en_US",
      "includeAttachments": "true",
      "webOptimized": "false",
      "embedFonts": "false",
      "makeAccessible": "false"
  }
}
```

### Étape 5 : saisir l’ID IC et lancer l’interface utilisateur associée

Vous êtes maintenant prêt à lancer l’interface utilisateur associée à l’aide de la page d’exemple d’HTML :

1. **Saisissez l’ID IC** : dans le champ **ID IC**, saisissez l’identifiant de votre communication interactive publiée. Il s’agit du seul champ obligatoire.

2. **Configuration du service de préremplissage** (facultatif) : si vous souhaitez préremplir l’IC avec des données dynamiques, saisissez le nom du service de modèle de données de formulaire dans le champ **Service de préremplissage**. Par exemple, utilisez `FdmTestData` pour les données d’exemple ou `IC-FDM` pour les données de test.

3. **Ajouter des paramètres de service** (facultatif) : dans le champ **Paramètres de service (JSON)**, saisissez un objet JSON avec les paramètres requis par votre service de préremplissage. Par exemple :

   ```json
   {"customerId": "101", "accountNumber": "ACC-98765"}
   ```

4. **Définir les options de PDF** (facultatif) : dans le champ **Options (JSON)**, configurez les options de rendu telles que les paramètres régionaux, les pièces jointes ou les paramètres d’accessibilité.

5. **Cliquez sur Launch Associate UI** : cliquez sur le bouton **Launch Associate UI**. Une nouvelle fenêtre de navigateur s’ouvre avec l’interface utilisateur associée, préchargée avec votre communication interactive.

>[!NOTE]
>
> Si la fenêtre ne s’ouvre pas, vérifiez que votre navigateur autorise les fenêtres pop-up pour ce site.

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