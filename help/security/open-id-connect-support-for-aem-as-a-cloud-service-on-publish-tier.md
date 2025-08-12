---
title: Prise en charge d’Open ID Connect pour AEM as a Cloud Service au niveau publication
description: Découvrez comment configurer Open ID Connect (OIDC) pour AEM as a Cloud Service au niveau publication
feature: Security
role: Admin
exl-id: d2f30406-546c-4a2f-ba88-8046dee3e09b
source-git-commit: bf35f847f6f00d21915dfedb10cf38ea74344988
workflow-type: tm+mt
source-wordcount: '1469'
ht-degree: 4%

---

# Prise en charge d’Open ID Connect pour AEM as a Cloud Service au niveau publication

## Présentation {#introduction}

À mesure que les entreprises modernisent leurs expériences digitales, la gestion sécurisée et évolutive des identités devient une exigence fondamentale. Adobe Experience Manager (AEM) Cloud Service prend désormais en charge OpenID Connect (OIDC) au niveau Publication, ce qui permet une intégration transparente et normalisée avec les principaux fournisseurs d’identité (IdP) tels que Entra ID (Azure AD), Google, Okta, Auth0, Ping Identity, ForgeRock et les fournisseurs d’identité pris en charge par OIDC.

OIDC est une couche d’identité qui complète le protocole OAuth 2.0 et qui permet une authentification utilisateur robuste tout en restant simple pour les développeurs. Il est largement adopté pour les scénarios de portail business-to-consumer (B2C), intranet et partenaire, où des fédérations d’identités et de connexion utilisateur sécurisées sont requises.

Jusqu’à présent, les clients AEM étaient chargés de mettre en œuvre leur propre logique de connexion personnalisée au niveau Publication, ce qui augmentait le temps de développement et introduisait des défis de maintenance et de sécurité à long terme. Grâce à la prise en charge native d’OIDC, AEM Cloud Service supprime cette charge en fournissant un mécanisme d’authentification sécurisé, extensible et pris en charge par Adobe pour les utilisateurs finaux accédant aux environnements de publication.

Que vous diffusiez un site web client personnalisé ou un portail interne authentifié, OIDC sur l’instance de publication simplifie la fédération des identités et réduit les risques grâce à une gouvernance d’identité centralisée. Il aide également les entreprises à se conformer aux normes de conformité et de sécurité modernes sans sacrifier leur agilité.

## Configurer AEM pour l’authentification OIDC {#configure-aem-oidc-authentication}

### Prérequis {#prerequisits}

Nous supposons que les informations suivantes sont disponibles ou définies :

1. Chemins d’accès au contenu à protéger dans le référentiel AEM
1. Identifiant de l’IdP à configurer. Il peut s’agir de n’importe quelle chaîne

Informations provenant de la configuration de l’IdP :

1. Identifiant client configuré dans l’IdP
1. Secret client configuré dans le fournisseur d’identité. Si PKCE a été configuré sur l’Idp, le secret client n’est pas disponible. Ne stockez pas la valeur en texte brut dans le fichier de configuration. Utiliser un secret CM et le référencer
1. Étendues configurées sur le fournisseur d’identité. Au moins la portée `openid` doit être fournie
1. Indique si PKCE est activé sur l’IdP
1. La `callbackUrl` est définie à l’aide de l’un des chemins configurés définis au point 1 et en ajoutant le suffixe : `/j_security_check`
1. `baseUrl` d’accès au fichier `.well-known` standard. Par exemple, si l’URL connue est : `https://login.microsoftonline.com/53279d7a-438f-41cd-a6a0-fdb09efc8891/v2.0/.well-known/openid-configuration` l’`baseUrl` est : `https://login.microsoftonline.com/53279d7a-438f-41cd-a6a0-fdb09efc8891`

### Présentation des fichiers de configuration {#overview-of-the-configuration-files}

Vous trouverez ci-dessous une liste des fichiers qui doivent être configurés :

1. **Connexion OIDC** : elle sera utilisée par le `OidcAuthenticationHandler` pour authentifier les utilisateurs, ou par d&#39;autres composants pour [autoriser l&#39;accès aux ressources protégées par l&#39;IdP à l&#39;aide d&#39;OAuth](https://github.com/apache/sling-org-apache-sling-auth-oauth-client)
1. **Gestionnaire d’authentification OIDC** : il s’agit du gestionnaire d’authentification utilisé pour authentifier les utilisateurs qui accèdent aux chemins configurés
1. **UserInfoProcessor** : ce composant traite les informations reçues par l’IdP. Il peut être étendu par les clients pour implémenter une logique personnalisée
1. [**Gestionnaire de synchronisation par défaut**](https://jackrabbit.apache.org/oak/docs/security/authentication/external/defaultusersync.html) : ce composant crée l’utilisateur dans le référentiel
1. [**ExternalLoginModule**](https://jackrabbit.apache.org/oak/docs/security/authentication/externalloginmodule.html) : ce composant authentifie l’utilisateur dans le référentiel oak local.

Le diagramme suivant montre comment les éléments de configuration mentionnés sont liés. Notez que puisqu’il s’agit de composants `ServiceFactory`, la `~uniqueid` peut être n’importe quelle chaîne unique aléatoire :

![diagramme de configuration OIDC](/help/security/assets/oidc-diagram.png)

### Configurer la connexion OIDC {#configure-the-oidc-connection}

Tout d’abord, nous devons configurer la connexion OIDC. Plusieurs connexions OIDC peuvent être configurées et chacune doit avoir un nom différent.

1. Créez un fichier `.cfg.json` qui hébergera la configuration. Par exemple, vous pouvez utiliser `org.apache.sling.auth.oauth_client.impl.OidcConnectionImpl~azure.cfg.json` - le suffixe **azure** doit être un identifiant unique pour la connexion
1. Suivez le format de configuration dans l’exemple ci-dessous :

   ```
   {
    "name":"azure",
    "scopes":[
      "openid"
    ],
    "baseUrl":"<https://login.microsoftonline.com/53279d7a-438f-41cd-a6a0-fdb09efc8891/v2.0>",
    "clientId":"5199fc45-8000-473e-ac63-989f1a78759f",
    "clientSecret":"xxxxxx"
   }
   ```

1. Configurez ses propriétés comme suit :
   * Le **« nom »** peut être défini par l’utilisateur ou l’utilisatrice
   * `baseUrl`, `clientid` et `clientSecret` sont des valeurs de configuration qui proviennent de l’IdP.
   * Les portées doivent contenir au moins la valeur `openid`.

### Configurer le gestionnaire d’authentification OIDC {#configure-oidc-authentication-handler}

Configurez maintenant le gestionnaire d’authentification OIDC. Plusieurs connexions OIDC peuvent être configurées. Chaque doit avoir un nom différent. S’ils partagent le même [fournisseur d’identité externe OAK](https://jackrabbit.apache.org/oak/docs/security/authentication/identitymanagement.html), ils peuvent partager des utilisateurs.

1. Créez le fichier de configuration. Pour cet exemple, nous utiliserons `org.apache.sling.auth.oauth_client.impl.OidcConnectionImpl~azure.cfg.json`. Le suffixe `azure` doit être un identifiant unique. Consultez un exemple du fichier de configuration ci-dessous :

   ```
   {
     "path":"/content/tests/us/en/test-7",
     "callbackUri":"http://localhost:14503/content/tests/us/en/test-7/j_security_check",
     "pkceEnabled":false,
     "defaultConnectionName":"azure"
     "idp": "azure-idp"
   }
   ```

1. Configurez ensuite ses propriétés comme suit :
   * `path` : chemin d’accès à protéger
   * `callbackUri` : dans le chemin d&#39;accès à protéger, en ajoutant le suffixe : `/j_security_check`
   * `defaultConnectionName` : configurez avec le même nom que celui défini pour la connexion OIDC à l’étape précédente+
   * `pkceEnabled` : `true` la clé de vérification pour l’échange de code (PKCE) sur le flux de code d’autorisation
   * `idp` : nom du [fournisseur d’identité externe OAK](https://jackrabbit.apache.org/oak/docs/security/authentication/identitymanagement.html). Notez qu’un fournisseur d’identité OAK différent ne peut pas partager des utilisateurs, des utilisatrices ou des groupes

### Configuration de SlingUserInfoProcessor

1. Créez le fichier de configuration. Pour cet exemple, nous utiliserons `org.apache.sling.auth.oauth_client.impl.SlingUserInfoProcessor~azure.cfg.json`. Le suffixe `azure` doit être un identifiant unique. Consultez un exemple du fichier de configuration ci-dessous :

   ```
   {
      "groupsInIdToken":true,
      "groupsClaimName": "groups",
      "connection":"azure",
      "storeAccessToken": false,
      "storeRefreshToken": false
   }
   ```

1. Configurez ensuite ses propriétés comme suit :
   * `groupsInIdToken` : défini sur true si les groupes sont envoyés dans le jeton d’ID. Si la valeur est false ou n’est pas spécifiée, les groupes sont lus à partir du point d’entrée UserInfo.
   * `groupsClaimName` : le nom de la réclamation contient les groupes à synchroniser dans AEM.
   * `connection` : configurez avec le même nom que celui défini pour la connexion OIDC à l’étape précédente
   * `storeAccessToken` : true si le jeton d’accès doit être stocké dans le référentiel. Par défaut, cette valeur est définie sur false. Définissez-le sur true uniquement si AEM doit accéder aux ressources pour le compte de l’utilisateur stocké dans des serveurs externes protégés par le même IdP.
   * `storeRefreshToken` : true si le jeton d’actualisation doit être stocké dans le référentiel. Par défaut, cette valeur est définie sur false. Définissez-le sur true uniquement si AEM doit accéder aux ressources pour le compte de l’utilisateur stockées sur des serveurs externes protégés par le même IdP et doit actualiser le jeton à partir de l’IdP.
Notez que le jeton d’accès et le jeton d’actualisation sont stockés chiffrés avec la clé principale AEM.


### Configuration du gestionnaire de synchronisation {#configure-the-synchronization-handler}

Au moins un gestionnaire de synchronisation doit être configuré pour synchroniser les utilisateurs authentifiés dans Oak. Pour plus d’informations, consultez [cette](https://jackrabbit.apache.org/oak/docs/security/authentication/external/defaultusersync.html) page.

Créez un fichier nommé `org.apache.jackrabbit.oak.spi.security.authentication.external.impl.DefaultSyncHandler~azure.cfg.json`. Le suffixe **azure** doit être un identifiant unique. Pour plus d’informations sur la configuration de ses propriétés, consultez la [documentation sur la synchronisation des utilisateurs et des groupes Oak](https://jackrabbit.apache.org/oak/docs/security/authentication/external/defaultusersync.html). Vous trouverez un exemple de configuration ci-dessous :

```
{
  "user.expirationTime":"300s",
  "user.membershipExpTime":"300s",
  "user.propertyMapping":[
    "profile/familyName=profile/familyName",
    "profile/givenName=profile/givenName",
    "rep:fullname=cn",
    "profile/email=profile/email",
    "oauth-tokens"
  ],
  "user.pathPrefix":"azure",
  "handler.name":"azure"
}
```

Vous trouverez ci-dessous certains des attributs les plus pertinents à configurer dans DefaultSyncHandler. Notez que l’appartenance à un groupe dynamique doit toujours être activée dans les services cloud.

| Nom de la propriété | Remarques | Valeur suggérée |
|---|---|---|
| `user.expirationTime` | Durée jusqu’à ce qu’un utilisateur synchronisé expire. Les utilisateurs sont synchronisés uniquement après l’heure d’expiration. | 1h |
| `user.membershipExpTime` | Durée jusqu’à ce qu’une adhésion d’utilisateur synchronisé expire. Les appartenances des utilisateurs ne sont synchronisées qu’après l’heure d’expiration. | 1h |
| `user.dynamicMembership` | Nous vous recommandons d’activer l’appartenance dynamique à un groupe | true |
| `user.enforceDynamicMembership` | Nous vous recommandons d’activer l’application de l’appartenance dynamique à un groupe | true |
| `group.dynamicGroups` | Nous vous recommandons d’activer les groupes dynamiques | true |
| user.propertyMapping | L’implémentation fournie de `UserInfoProcessor` synchronise uniquement quelques propriétés. Il peut être modifié et personnalisé. | <code>« profile/givenName=profile/given_name »,</code><br><code>« profile/familyName=profile/family_name »,</code><br><code>« rep:fullname=profile/name »,</code><br><code>« profile/email=profile/email »,</code><br><code>« access_token=access_token »,</code><br><code>« refresh_token=refresh_token »</code> |  |
| `user.membershipNestingDepth` | Renvoie la profondeur maximale de l’imbrication de groupes lorsque les relations d’appartenance sont synchronisées. Une valeur égale à 0 désactive la recherche de l’appartenance à un groupe. Une valeur égale à 1 ajoute uniquement les groupes directs d’un utilisateur. Cette valeur n’a aucun effet sur la synchronisation de groupes individuels, mais uniquement sur la synchronisation d’une ascendance d’abonnement d’utilisateurs et d’utilisatrices. | 1 |

### Configuration du module de connexion externe {#configure-the-external-login-module}

Enfin, vous devez configurer le module de connexion externe.

1. Créez un fichier nommé `org.apache.jackrabbit.oak.spi.security.authentication.external.impl.ExternalLoginModuleFactory~azure.cfg.json`. Consultez un exemple de configuration ci-dessous :

   ```
   {
    "sync.handlerName":"azure",
    "idp.name":"azure-idp"
   }
   ```

1. Configurez ses propriétés comme suit :

   * `sync.handlerName` : nom du gestionnaire de synchronisation défini précédemment
   * `idp.name` : fournisseur d’identité OAK défini dans le gestionnaire d’authentification OIDC

### Facultatif : Implémentation d’un UserInfoProcessor personnalisé {#implement-a-custom-userinfoprocessor}

L’utilisateur est authentifié par un jeton d’ID et des attributs supplémentaires sont récupérés dans le point d’entrée `userInfo` défini pour l’IdP. Si d’autres opérations non standard doivent être effectuées, une implémentation personnalisée du [UserInfoProcessor](https://github.com/apache/sling-org-apache-sling-auth-oauth-client/blob/master/src/main/java/org/apache/sling/auth/oauth_client/impl/SlingUserInfoProcessorImpl.java) est l’implémentation par défaut de Sling.

## Exemple : configurer l’authentification OIDC avec Azure Active Directory

### Configurer une nouvelle application dans Azure Active Directory {#configure-a-new-application-in-azure-ad}

1. Créez une application dans Azure Active Directory en suivant la [documentation Azure Active Directory](https://learn.microsoft.com/en-us/power-pages/security/authentication/openid-settings#create-an-app-registration-in-azure).  Consultez ci-dessous l’écran détaillant la présentation de l’application :

   ![Présentation de l’application](/help/security/assets/odic-application-overview.png)

1. Si des groupes ou des rôles d’application sont requis, suivez la [documentation](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-use-app-roles-customers) pour les activer pour l’application et envoyez-les dans le jeton d’ID. Voici un exemple de groupes configurés :

![ID du jeton de réclamation OIDC](/help/security/assets/oidc-claim-id-token.png)

1. Suivez les étapes décrites précédemment pour créer les fichiers de configuration requis. Ci-dessous un exemple spécifique à Azure AD où :
   * Nous définissons le nom de Oidc Connection, Authentication Handler et DefaultSyncHandler comme suit : `azure`
   * L’URL du site web est : `www.mywebsite.com`
   * Nous protégeons le chemin `/content/wknd/us/en/adventures`
   * Tennant est : `tennat-id`,
   * L’identifiant client est : `client-id`,
   * Le secret est : `secret`,
   * Les groupes sont envoyés dans le jeton d’ID dans une réclamation appelée : `groups`

#### org.apache.sling.auth.oauth_client.impl.OidcConnectionImpl~azure.cfg.json

```
{
  "name":"azure",
  "scopes":[
    openid", "User.Read", "profile", "email
  ],
  "baseUrl":"https://login.microsoftonline.com/tenant-id/v2.0",
  "clientId":"client-id",
  "clientSecret":"secret"
}
```

#### org.apache.sling.auth.oauth_client.impl.OidcAuthenticationHandler~azure.cfg.json

```
{
  "callbackUri":"https://www.mywebsite.com/content/wknd/us/en/adventures/j_security_check",
  "path":[
    "/content/wknd/us/en/adventures"
  ],
  "idp":"azure",
  "defaultConnectionName":"azure"
}
```

#### org.apache.jackrabbit.oak.spi.security.authentication.external.impl.ExternalLoginModuleFactory~azure.cfg.json

```
{
  "sync.handlerName":"azure",
  "idp.name":"azure"
}
```

#### org.apache.jackrabbit.oak.spi.security.authentication.external.impl.DefaultSyncHandler~azure.cfg.json

```
{
  "user.expirationTime":"1s",
  "user.membershipExpTime":"1s",
  "user.propertyMapping":[
    "profile/givenName=profile/given_name",
    "profile/familyName=profile/family_name",
    "rep:fullname=profile/name",
    "profile/email=profile/email",
    "access_token=access_token",
    "refresh_token=refresh_token"
  ],
  "user.pathPrefix":"azure",
  "group.pathPrefix": "oidc",
  "user.membershipNestingDepth": "1",
  "handler.name":"azure"
}
```

#### org.apache.sling.auth.oauth_client.impl.SlingUserInfoProcessorImpl~azure.cfg.json

```
{
  "groupsInIdToken": "true",
  "storeAccessToken": "false",
  "storeRefreshToken": "false",
  "connection": "azure",
  "groupsClaimName": "groups"
}
```

### Informations supplémentaires sur les groupes Azure AD {#additional-information-about-azure-ad-groups}

Pour configurer un groupe pour l’application d’entreprise dans le portail Azure Microsoft, vous devez rechercher l’application dans : **Applications d’entreprise** et ajouter les groupes : <!-- Alexandru: this bit cound be clearer-->

![OIDC Group add](/help/security/assets/oidc-ad-additional-info.png)

Pour activer la revendication de groupe dans le jeton d’ID, ajoutez la revendication dans la section **Configuration du jeton** du portail Azure Microsoft : <!-- Alexandru: this bit cound be clearer as well-->

![ID du jeton de réclamation OIDC](/help/security/assets/oidc-claim-id-token.png)

La configuration de `SlingUserInfoProcessor` doit être modifiée comme dans l’exemple ci-dessous.

Le nom de fichier qui doit être modifié est `org.apache.sling.auth.oauth_client.impl.SlingUserInfoProcessorImpl.cfg.json`. Le contenu doit être configuré comme suit :

```
{
  "connection": "azure",
  "groupsInIdToken": "true",
  "storeAccessToken": "false",
  "storeRefreshToken": "false"
}
```
