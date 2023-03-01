---
title: Prise en charge d’OAuth2 pour le service de messagerie
description: Prise en charge d’OAuth2 du service de messagerie dans Adobe Experience Manager as a Cloud Service
exl-id: 93e7db8b-a8bf-4cc7-b7f0-cda481916ae9
source-git-commit: 9f9c1c45b27e249e7051af1fe5eea7580aceab15
workflow-type: ht
source-wordcount: '674'
ht-degree: 100%

---

# Prise en charge d’OAuth2 pour le service de messagerie {#oauth2-support-for-the-mail-service}

AEM as a Cloud Service offre la prise en charge d’OAuth2 pour son service de messagerie intégré, afin de permettre aux entreprises de se conformer aux exigences en matière de messagerie sécurisée.

Vous pouvez configurer OAuth pour plusieurs fournisseurs de messagerie. Vous trouverez ci-dessous des instructions détaillées pour configurer le service de messagerie d’AEM afin de l’authentifier via OAuth2 avec Microsoft Office 365 Outlook. D’autres fournisseurs peuvent être configurés de la même manière.

Pour plus d’informations sur le service de messagerie d’AEM as a Cloud Service, voir [Envoi d’e-mail](/help/implementing/developing/introduction/development-guidelines.md#sending-email).

## Microsoft Outlook {#microsoft-outlook}

1. Accédez à [https://portal.azure.com/](https://portal.azure.com/) et connectez-vous.
1. Recherchez le **répertoire Azure principal** dans la barre de recherche et cliquez sur le résultat. Vous pouvez également accéder directement à [https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview)
1. Cliquez sur **Enregistrement de l’application** - **Nouvel enregistrement**

   ![](assets/oauth-outlook1.png)

1. Renseignez les informations selon vos besoins, puis cliquez sur **Enregistrer**
1. Accédez à l’application nouvellement créée, puis sélectionnez **Autorisations API**
1. Accédez à **Ajouter une autorisation** - **Autorisation graphique** - **Autorisations déléguées**
1. Sélectionnez les autorisations ci-dessous pour votre application, puis cliquez sur **Ajouter une autorisation** :
   * `https://graph.microsoft.com/SMTP.Send`
   * `https://graph.microsoft.com/Mail.Read`
   * `https://graph.microsoft.com/Mail.Send`
   * `https://graph.microsoft.com/User.Read`
   * `openid`
   * `offline_access`
   * `email`
   * `profile`
1. Accédez à **Authentification** - **Ajouter une plateforme** - **Web**, et dans la section **URL de redirection**, ajoutez les URL ci-dessous, une avec et une sans barre oblique :
   * `http://localhost/`
   * `http://localhost`
1. Appuyez sur **Configurer** après avoir ajouté chaque URL et configuré vos paramètres en fonction de vos besoins.
1. Ensuite, accédez à **Certificats et secrets**, cliquez sur **Nouveau secret client** et suivez les étapes à l’écran pour créer un secret. Veillez à prendre note de ce secret pour une utilisation ultérieure.
1. Appuyez sur **Aperçu** dans le volet de gauche et copiez les valeurs pour **ID d’application (client)** et **ID de répertoire (locataire)** pour une utilisation ultérieure.

Pour effectuer une récapitulation, vous aurez besoin des informations suivantes pour configurer OAuth2 pour le service de messagerie du côté AEM :

* L’URL d’authentification, qui sera créée avec l’identifiant du client. Elle se présente comme suit : `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/authorize`
* L’URL du jeton, qui sera construite avec l’ID du locataire. Elle se présente comme suit : `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/token`
* L’URL d’actualisation, qui sera créée avec l’ID du locataire. Elle se présente comme suit : `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/token`
* L’ID client
* Le secret client

### Génération du jeton d’actualisation {#generating-the-refresh-token}

Ensuite, vous devez générer le jeton d’actualisation, qui fera partie de la configuration OSGi lors d’une étape ultérieure.

Pour ce faire, procédez comme suit :

1. Ouvrez l’URL suivante dans le navigateur après avoir remplacé `clientID` et `tenantID` par les valeurs propres à votre compte : `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/authorize?client_id=<clientId>&response_type=code&redirect_uri=http://localhost&response_mode=query&scope=https://graph.microsoft.com/SMTP.Send https://graph.microsoft.com/Mail.Read https://graph.microsoft.com/Mail.Send https://graph.microsoft.com/User.Read email openid profile offline_access&state=12345`
1. Octroyer l’autorisation si demandé
1. L’URL redirige vers un nouvel emplacement, construit au format suivant : `http://localhost/?code=<code>&state=12345&session_state=4f984c6b-cc1f-47b9-81b2-66522ea83f81#`
1. Copiez la valeur de `<code>` dans l’exemple ci-dessus.
1. Utilisez la commande cURL suivante pour obtenir le refreshToken. Vous devez remplacer tenantID, clientID et clientSecret par les valeurs de votre compte, ainsi que par la valeur de `<code>` :

   ```
   curl --location --request POST 'https://login.microsoftonline.com/<tenantId>/oauth2/v2.0/token' \
   --header 'Content-Type: application/x-www-form-urlencoded' \
   --header 'Cookie: buid=0.ARgAep0nU49DzUGmoP2wnvyIkcQjsx26HEpOnvHS0akqXQgYAAA.AQABAAEAAAD--DLA3VO7QrddgJg7Wevry9XPJSKbGVlPt5NWYxLtTl3K1W0LwHXelrffApUo_K02kFrkvmGm94rfBT94t25Zq4bCd5IM3yFOjWb3V22yDM7-rl112sLzbBQBRCL3QAAgAA; esctx=AQABAAAAAAD--DLA3VO7QrddgJg7Wevr4a8wBjYcNbBXRievdTOd15caaeAsQdXeBAQA3tjVQaxmrOXFGkKaE7HBzsJrzA-ci4RRpor-opoo5gpGLh3pj_iMZuqegQPEb1V5sUVQV8_DUEbBv5YFV2eczS5EAhLBAwAd1mHx6jYOL8LwZNDFvd2-MhVXwPd6iKPigSuBxMogAA; x-ms-gateway-slice=estsfd; stsservicecookie=estsfd; fpc=Auv6lTuyAP1FuOOCfj9w0U_5vR5dAQAAALDXP9gOAAAAwIpkkQEAAACT2T_YDgAAAA' \
   --data-urlencode 'client_id=<clientID>' \
   --data-urlencode 'scope=https://graph.microsoft.com/SMTP.Send https://graph.microsoft.com/Mail.Read https://graph.microsoft.com/Mail.Send https://graph.microsoft.com/User.Read email openid profile offline_access' \
   --data-urlencode 'redirect_uri=http://localhost' \
   --data-urlencode 'grant_type=authorization_code' \
   --data-urlencode 'client_secret=<clientSecret>' \
   --data-urlencode 'code=<code>'
   ```

1. Prenez note des éléments refreshToken et accessToken.

### Validation des jetons {#validating-the-tokens}

Avant de poursuivre la configuration d’OAuth côté AEM, veillez à valider les éléments accessToken et refreshToken avec la procédure suivante :

1. Générez l’accessToken à l’aide du refreshToken produit lors de la procédure précédente. Pour ce faire, utilisez l’URL suivante, en remplaçant les valeurs de `<client_id>`,`<client_secret>` et `<refreshToken>` :

   ```
   curl --location --request POST 'https://login.microsoftonline.com/<tenetId>/oauth2/v2.0/token' \
   --header 'Content-Type: application/x-www-form-urlencoded' \
   --header 'Cookie: buid=0.ARgAep0nU49DzUGmoP2wnvyIkcQjsx26HEpOnvHS0akqXQgYAAA.AQABAAEAAAD--DLA3VO7QrddgJg7Wevry9XPJSKbGVlPt5NWYxLtTl3K1W0LwHXelrffApUo_K02kFrkvmGm94rfBT94t25Zq4bCd5IM3yFOjWb3V22yDM7-rl112sLzbBQBRCL3QAAgAA; esctx=AQABAAAAAAD--DLA3VO7QrddgJg7Wevr4a8wBjYcNbBXRievdTOd15caaeAsQdXeBAQA3tjVQaxmrOXFGkKaE7HBzsJrzA-ci4RRpor-opoo5gpGLh3pj_iMZuqegQPEb1V5sUVQV8_DUEbBv5YFV2eczS5EAhLBAwAd1mHx6jYOL8LwZNDFvd2-MhVXwPd6iKPigSuBxMogAA; x-ms-gateway-slice=estsfd; stsservicecookie=estsfd; fpc=Auv6lTuyAP1FuOOCfj9w0U_IezHLAQAAAPeNSdgOAAAA' \
   --data-urlencode 'client_id=<client_id>' \
   --data-urlencode 'scope=https://graph.microsoft.com/SMTP.Send https://graph.microsoft.com/Mail.Read https://graph.microsoft.com/Mail.Send https://graph.microsoft.com/User.Read email openid profile offline_access' \
   --data-urlencode 'redirect_uri=http://localhost' \
   --data-urlencode 'grant_type=refresh_token' \
   --data-urlencode 'client_secret=<client_secret>' \
   --data-urlencode 'refresh_token=<refreshToken>'
   ```

1. Envoyez un courrier électronique à l’aide d’accessToken pour vérifier s’il fonctionne correctement.

>[!NOTE]
>
> Vous pouvez obtenir la collection d’API Postman à partir de [cet emplacement](https://docs.microsoft.com/fr-fr/azure/active-directory/develop/v2-oauth2-auth-code-flow).

### Intégration à AEM as a Cloud Service {#integration-with-aem-as-a-cloud-service}

1. Créez un fichier de propriétés OSGI appelé `com.day.cq.mailer.oauth.impl.OAuthConfigurationProviderImpl.cfg.json` sous `/apps/<my-project>/osgiconfig/config` avec la syntaxe suivante :

   ```
   {
       authUrl: "<Authorization Url>",
       tokenUrl: "<Token Url>",
       clientId: "<clientID>",
       clientSecret: "$[secret:SECRET_SMTP_OAUTH_CLIENT_SECRET]",
       scopes: [
          "scope1",
          "scope2"
       ],
       authCodeRedirectUrl: "http://localhost",
       refreshUrl: "<Refresh token Url>",
       refreshToken: "$[secret:SECRET_SMTP_OAUTH_REFRESH_TOKEN]"
   }
   ```

1. Renseignez les champs `authUrl`, `tokenUrl` et `refreshURL` en les construisant comme décrit dans la section précédente.
1. Ajoutez les portées suivantes à la configuration :
   * `https://graph.microsoft.com/SMTP.Send`
   * `https://graph.microsoft.com/Mail.Read`
   * `https://graph.microsoft.com/Mail.Send`
   * `https://graph.microsoft.com/User.Read`
   * `openid`
   * `offline_access`
   * `email`
   * `profile`
1. Créez un fichier de propriétés OSGI `called com.day.cq.mailer.DefaultMailService.cfg.json`
sous 
`/apps/<my-project>/osgiconfig/config` avec la syntaxe suivante :

   ```
   {
    "smtp.host": "<smtp hostname>"
    "smtp.user": "<user account that logged into get the oauth tokens>",
    "smtp.password": "value not used",
    "smtp.port": 587,
    "from.address": "<from address used for sending>"
    "smtp.ssl": false,
    "smtp.starttls": true,
    "smtp.requiretls": true,
    "debug.email": false,
    "oauth.flow": true
   }
   ```

1. Pour Outlook, la valeur de configuration `smtp.host` est `smtp.office365.com`
1. Au moment de l’exécution, transmettez les secrets `refreshToken values` et `clientSecret` à l’aide de l’API des variables Cloud Manager, comme décrit [ici](/help/implementing/deploying/configuring-osgi.md#setting-values-via-api). Les valeurs des variables `SECRET_SMTP_OAUTH_REFRESH_TOKEN` et `SECRET_SMTP_OAUTH_CLIENT_SECRET` doivent être définies.

### Résolution des problèmes {#troubleshooting}

Si le service de messagerie ne fonctionne pas correctement, vous devrez, dans la plupart des cas, régénérer le `refreshToken` comme décrit ci-dessus, en transmettant la nouvelle valeur via l’API Cloud Manager. Le déploiement de la nouvelle valeur prend quelques minutes.