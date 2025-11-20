---
title: Prise en charge d’Open ID Connect pour AEM as a Cloud Service au niveau publication
description: Découvrez comment configurer Open ID Connect (OIDC) pour AEM as a Cloud Service au niveau publication
feature: Security
role: Admin
exl-id: d2f30406-546c-4a2f-ba88-8046dee3e09b
source-git-commit: 75c2dbc4f1d77de48764e5548637f95bee9264dd
workflow-type: tm+mt
source-wordcount: '1986'
ht-degree: 71%

---

# Prise en charge d’Open ID Connect pour AEM as a Cloud Service au niveau publication {#open-id-connect-support-for-aem-as-a-cloud-service-on-publish-tier}

## Présentation {#introduction}

À mesure que les organisations modernisent leurs expériences numériques, la gestion sécurisée et évolutive des identités devient une exigence fondamentale. Cloud Service d’Adobe Experience Manager (AEM) prend désormais en charge Open ID Connect (OIDC) au niveau publication, ce qui permet une intégration transparente et normalisée avec les principaux fournisseurs d’identité (IdP) tels qu’Entra ID (Azure AD), Google, Okta, Auth0, Ping Identity, ForgeRock et les fournisseurs d’identité pris en charge par OIDC.

OIDC est une couche d’identité qui se place sur le protocole OAuth 2.0 et qui permet une authentification robuste des personnes, tout en restant simple pour les développeurs et développeuses. Il est largement adopté pour les scénarios de business-to-consumer (B2C), d’intranet et de portails partenaires, où des fédérations d’identités et de connexion sécurisées sont requises.

Jusqu’à présent, les clientes et clients AEM devaient mettre en œuvre leur propre logique de connexion personnalisée au niveau publication, ce qui accroissait les délais de développement et introduisait des difficultés de maintenance et de sécurité à long terme. Grâce à la prise en charge native d’OIDC, AEM Cloud Service élimine cette responsabilité en proposant un mécanisme d’authentification sécurisé, extensible et pris en charge par Adobe pour les utilisateurs et utilisatrices qui accèdent aux environnements de publication.

Qu’il s’agisse de diffuser un site web client personnalisé ou un portail interne authentifié, OIDC installé au niveau publication simplifie la fédération des identités et réduit les risques grâce à une gouvernance d’identité centralisée. Il aide également les organisations à respecter les normes de conformité et de sécurité modernes sans sacrifier leur agilité.

## Configurer AEM pour l’authentification OIDC {#configure-aem-oidc-authentication}

### Prérequis {#prerequisits}

Nous partons de l’hypothèse que les informations suivantes sont disponibles ou définies :

1. Chemins d’accès au contenu à protéger dans le référentiel AEM.
1. Identifiant de l’IdP à configurer. Il peut s’agir de n’importe quelle chaîne.

Informations provenant de la configuration d’IdP :

1. ID client configuré dans l’IdP.
1. Secret client configuré dans l’IdP. Si PKCE a été configuré sur l’IdP, le secret client n’est pas disponible. Ne stockez pas la valeur en texte brut dans le fichier de configuration. Utiliser un secret CM et le référencer
1. Étendues configurées sur l’IdP. Il est nécessaire de fournir au moins l’étendue `openid`.
1. Indique si PKCE est activé ou non sur l’IdP.
1. L’`callbackUrl` est définie à l’aide de l’un des chemins configurés définis au point 1 et en ajoutant le suffixe : `/j_security_check`
1. L’`baseUrl` permettant d’accéder au fichier `.well-known` standard. Par exemple, si l’URL connue est : `https://login.microsoftonline.com/53279d7a-438f-41cd-a6a0-fdb09efc8891/v2.0/.well-known/openid-configuration`, l’`baseUrl` est : `https://login.microsoftonline.com/53279d7a-438f-41cd-a6a0-fdb09efc8891`.

### Vue d’ensemble des fichiers de configuration {#overview-of-the-configuration-files}

Vous trouverez ci-dessous une liste des fichiers qui doivent être configurés :

1. **Connexion OIDC** : elle sera utilisée par le `OidcAuthenticationHandler` pour authentifier les utilisateurs ou utilisatrices, ou par d&#39;autres composants pour [autoriser l’accès aux ressources protégées par l’IdP à l’aide d’OAuth](https://github.com/apache/sling-org-apache-sling-auth-oauth-client).
1. **Gestionnaire d’authentification OIDC** : il s’agit du gestionnaire d’authentification utilisé pour authentifier les utilisateurs et utilisatrices qui accèdent aux chemins configurés.
1. **UserInfoProcessor** : ce composant traite les informations reçues par l’IdP. Il peut être étendu par les clientes et clients pour implémenter une logique personnalisée.
1. [**Gestionnaire de synchronisation par défaut**](https://jackrabbit.apache.org/oak/docs/security/authentication/external/defaultusersync.html) : ce composant crée l’utilisateur ou l’utilisatrice dans le référentiel.
1. [**ExternalLoginModule**](https://jackrabbit.apache.org/oak/docs/security/authentication/externalloginmodule.html) : ce composant authentifie l’utilisateur ou l’utilisatrice dans le référentiel oak local.

Le diagramme suivant montre la façon dont les éléments de configuration mentionnés sont liés. Notez que puisqu’il s’agit de composants `ServiceFactory`, l’`~uniqueid` peut être n’importe quelle chaîne unique aléatoire :

![Diagramme de configuration OIDC](/help/security/assets/oidc-diagram.png)

### Configurer la connexion OIDC {#configure-the-oidc-connection}

Tout d’abord, nous devons configurer la connexion OIDC. Il est possible de configurer plusieurs connexions OIDC. Chacune doit avoir un nom différent.

1. Créez un fichier `.cfg.json` qui hébergera la configuration. Par exemple, vous pouvez utiliser `org.apache.sling.auth.oauth_client.impl.OidcConnectionImpl~azure.cfg.json` - le suffixe **azure** doit être un identifiant unique pour la connexion.
1. Suivez le format de configuration de l’exemple ci-dessous :

   ```
   {
    "name":"azure",
    "scopes":[
      "openid"
    ],
    "baseUrl":"<https://login.microsoftonline.com/tenant-id/v2.0>",
    "clientId":"client-id-from-idp",
    "clientSecret":"xxxxxx"
   }
   ```

Dans certains environnements, le fournisseur d’identité (IdP) peut ne pas exposer un point d’entrée `.well-known` valide.
Dans ce cas, les points d’entrée requis peuvent être définis manuellement en spécifiant les propriétés suivantes dans le fichier de configuration.
Dans ce mode de configuration, la propriété `baseUrl` ne doit pas être définie.

```
"authorizationEndpoint": "https://idp-url/oauth2/v1/authorize",
"tokenEndpoint": "https://idp-url/oauth2/v1/token",
"jwkSetURL":"https://idp-url/oauth2/v1/keys",
"issuer": "https://idp-url"
```

1. Configurez ses propriétés comme suit :
   * Le **« nom »** peut être défini par l’utilisateur ou l’utilisatrice.
   * `baseUrl`, `clientid` et `clientSecret` sont des valeurs de configuration qui proviennent de l’IdP.
   * Les étendues doivent contenir au moins la valeur `openid`.

### Configurer le gestionnaire d’authentification OIDC {#configure-oidc-authentication-handler}

Configurez maintenant le gestionnaire d’authentification OIDC. Il est possible de configurer plusieurs connexions OIDC. Chacune doit avoir un nom différent. Si elles partagent le même [fournisseur d’identité externe OAK](https://jackrabbit.apache.org/oak/docs/security/authentication/identitymanagement.html), elles peuvent partager des utilisateurs et des utilisatrices.

1. Créez le fichier de configuration. Pour cet exemple, nous utiliserons `org.apache.sling.auth.oauth_client.impl.OidcAuthenticationHandler~azure.cfg.json`. Le suffixe `azure` doit être un identifiant unique. Consultez un exemple du fichier de configuration ci-dessous :

   ```
   {
     "path":"/content/tests/us/en/test-7",
     "callbackUri":"http://localhost:14503/content/tests/us/en/test-7/j_security_check",
     "pkceEnabled":false,
     "defaultConnectionName":"azure"
     "idp": "azure-idp"
   }
   ```

1. Configurez ensuite ses propriétés comme suit :
   * `path` : chemin d’accès à protéger
   * `callbackUri` : chemin d&#39;accès à protéger, en ajoutant le suffixe : `/j_security_check`. Ce même callbackUri doit également être configuré dans l’IdP distant en tant qu’URL de redirection.
   * `defaultConnectionName` : configurez avec le nom défini pour la connexion OIDC à l’étape précédente.
   * `pkceEnabled` : `true` clé de vérification pour l’échange de code (PKCE) sur le flux de code d’autorisation
   * `idp` : nom du [fournisseur d’identité externe OAK](https://jackrabbit.apache.org/oak/docs/security/authentication/identitymanagement.html). Notez qu’un fournisseur d’identité OAK différent ne peut pas partager d’utilisateurs, d’utilisatrices ou de groupes.

### Configurer SlingUserInfoProcessor {#configure-slinguserinfoprocessor}

1. Créez le fichier de configuration. Pour cet exemple, nous utiliserons `org.apache.sling.auth.oauth_client.impl.SlingUserInfoProcessor~azure.cfg.json`. Le suffixe `azure` doit être un identifiant unique. Consultez un exemple du fichier de configuration ci-dessous :

   ```
   {
      "groupsInIdToken":true,
      "groupsClaimName": "groups",
      "connection":"azure",
      "storeAccessToken": false,
      "storeRefreshToken": false,
      "idpNameInPrincipals": true
   }
   ```

1. Configurez ensuite ses propriétés comme suit :
   * `groupsInIdToken` : défini sur true si les groupes sont envoyés dans le jeton d’ID. Si la valeur est false ou n’est pas spécifiée, les groupes sont lus à partir du point d’entrée UserInfo.
   * `groupsClaimName` : le nom de la réclamation contient les groupes à synchroniser dans AEM.
   * `connection` : configurez avec le nom défini pour la connexion OIDC à l’étape précédente.
   * `storeAccessToken` : true si le jeton d’accès doit être stocké dans le référentiel. Par défaut, cette valeur est définie sur false. Définissez-la sur true uniquement si AEM doit accéder aux ressources pour le compte de l’utilisateur ou l’utilisatrice stocké dans des serveurs externes protégés par le même IdP.
   * `storeRefreshToken` : true si le jeton d’actualisation doit être stocké dans le référentiel. Par défaut, cette valeur est définie sur false. Définissez-le sur true uniquement si AEM doit accéder aux ressources pour le compte de l’utilisateur stockées sur des serveurs externes protégés par le même IdP et doit actualiser le jeton à partir de l’IdP.
   * `idpNameInPrincipals` : lorsqu’il est défini sur true, le nom de l’IdP est ajouté comme suffixe aux principaux d’utilisateur et de groupe séparés par un « ; ». Par exemple, si le nom de l’IdP est `azure-idp` et que le nom d’utilisateur est `john.doe`, le principal stocké dans oak est `john.doe;azure-idp`. Cela s’avère utile lorsque plusieurs IDp sont configurés dans oak afin d’éviter les conflits entre les utilisateurs ou les groupes portant le même nom provenant de différents IDp. Vous pouvez également définir cette option pour éviter les conflits avec les utilisateurs ou les groupes créés par d’autres gestionnaires d’authentification tels que Saml.
Notez que le jeton d’accès et le jeton d’actualisation sont stockés chiffrés avec la clé principale AEM.


### Configurer le gestionnaire de synchronisation {#configure-the-synchronization-handler}

Au moins un gestionnaire de synchronisation doit être configuré pour synchroniser les utilisateurs et utilisatrices authentifiés dans Oak. Pour plus d’informations, consultez [cette page](https://jackrabbit.apache.org/oak/docs/security/authentication/external/defaultusersync.html).

Créez un fichier nommé `org.apache.jackrabbit.oak.spi.security.authentication.external.impl.DefaultSyncHandler~azure.cfg.json`. Le suffixe **azure** doit être un identifiant unique. Pour plus d’informations sur la configuration de ses propriétés, consultez la [documentation sur la synchronisation des utilisateurs et utilisatrices et des groupes Oak](https://jackrabbit.apache.org/oak/docs/security/authentication/external/defaultusersync.html). Vous trouverez un exemple de configuration ci-dessous :

```
{
  "user.expirationTime":"1h",
  "user.membershipExpTime":"1h",
  "group.expirationTime": "1d"
  "user.propertyMapping":[
    "profile/givenName=profile/given_name",
    "profile/familyName=profile/family_name",
    "rep:fullname=profile/name",
    "profile/email=profile/email",
    "access_token=access_token",
    "refresh_token=refresh_token"
  ],
  "user.pathPrefix":"azure",
  "handler.name":"azure"
}
```

Pendant le développement, les délais d’expiration peuvent être réduits à une valeur inférieure (par exemple : 1 s) afin d’accélérer les tests de synchronisation des utilisateurs et des groupes dans oak.
Vous trouverez ci-dessous certains des attributs les plus pertinents à configurer dans DefaultSyncHandler. Notez que l’appartenance à un groupe dynamique doit toujours être activée dans les services cloud.

| Nom de la propriété | Remarques | Valeur suggérée |
|---|---|---|
| `user.expirationTime` | Durée jusqu’à ce que la synchronisation d’une personne expire. Les utilisateurs et utilisatrices ne sont synchronisés qu’après l’heure d’expiration. | 1h |
| `user.membershipExpTime` | Durée jusqu’à ce que l’abonnement d’une personne synchronisée expire. Les abonnements des utilisateurs et utilisatrices ne sont synchronisés qu’après l’heure d’expiration. | 1h |
| `user.dynamicMembership` | Nous vous recommandons d’activer l’appartenance dynamique à un groupe. | true |
| `user.enforceDynamicMembership` | Nous vous recommandons d’activer l’application de l’appartenance dynamique à un groupe. | true |
| `group.dynamicGroups` | Nous vous recommandons d’activer les groupes dynamiques. | true |
| user.propertyMapping | L’implémentation fournie pour `UserInfoProcessor` synchronise uniquement quelques propriétés. Elle peut être modifiée et personnalisée. | <code>« profile/givenName=profile/given_name »,</code><br><code>« profile/familyName=profile/family_name »,</code><br><code>« rep:fullname=profile/name »,</code><br><code>« profile/email=profile/email »,</code><br><code>&quot;access_token=access_token&quot;,</code><br><code>« refresh_token=refresh_token »</code> |
| `user.membershipNestingDepth` | Renvoie la profondeur maximale de l’imbrication de groupes lorsque les relations d’appartenance sont synchronisées. Une valeur égale à 0 désactive la recherche de l’appartenance à un groupe. Une valeur égale à 1 ajoute uniquement les groupes directs d’un utilisateur. Cette valeur n’a aucun effet sur la synchronisation de groupes individuels, mais uniquement sur la synchronisation d’une ascendance d’abonnement d’utilisateurs et d’utilisatrices. | 1 |

### Configurer le module de connexion externe {#configure-the-external-login-module}

Enfin, vous devez configurer le module de connexion externe.

1. Créez un fichier nommé `org.apache.jackrabbit.oak.spi.security.authentication.external.impl.ExternalLoginModuleFactory~azure.cfg.json`. Découvrez un exemple de configuration ci-dessous :

   ```
   {
    "sync.handlerName":"azure",
    "idp.name":"azure-idp"
   }
   ```

1. Configurez ses propriétés comme suit :

   * `sync.handlerName` : nom du gestionnaire de synchronisation défini précédemment
   * `idp.name` : fournisseur d’identité OAK défini dans le gestionnaire d’authentification OIDC

### Facultatif : implémentation d’un UserInfoProcessor personnalisé {#implement-a-custom-userinfoprocessor}

L’utilisateur ou l’utilisatrice est authentifié par un jeton d’ID et des attributs supplémentaires sont récupérés dans le point d’entrée `userInfo` défini pour l’IdP. Si d’autres opérations non standard doivent être effectuées, une implémentation personnalisée du [UserInfoProcessor](https://github.com/apache/sling-org-apache-sling-auth-oauth-client/blob/master/src/main/java/org/apache/sling/auth/oauth_client/impl/SlingUserInfoProcessorImpl.java) est l’implémentation par défaut provenant de Sling.

### Configuration de la liste de contrôle d’accès pour les groupes externes {#configure-acl-for-external-groups}

Lorsque les utilisateurs sont authentifiés via OIDC, leurs appartenances à un groupe sont généralement synchronisées à partir du fournisseur d’identité externe.
Ces groupes externes sont créés dynamiquement dans le référentiel AEM, mais ne sont pas automatiquement associés à des entrées de contrôle d’accès.
Pour que les utilisateurs disposent des autorisations appropriées, des listes de contrôle d’accès (ACL) doivent être explicitement définies pour ces groupes.

Deux approches principales sont disponibles.

### Option 1 — Groupes Locaux

Le groupe externe peut être ajouté en tant que membre d’un groupe local qui possède déjà les listes de contrôle d’accès requises.
* Le groupe externe doit exister dans le référentiel, ce qui se produit automatiquement lorsqu’un utilisateur appartenant à ce groupe se connecte pour la première fois.
* Cette option est généralement préférable lorsque des groupes d’utilisateurs fermés sont en cours d’utilisation, car le groupe local existe dans les environnements de création et de publication.

### Option 2 — Listes de contrôle d’accès directes sur des groupes externes via RepoInit

Les listes de contrôle d’accès peuvent être appliquées directement à des groupes externes à l’aide de scripts RepoInit.
* Cette approche est plus efficace et est recommandée lorsque les CUG ne sont pas utilisés.
* L’exemple suivant illustre une configuration RepoInit qui attribue des autorisations de lecture à un groupe externe. L’option `ignoreMissingPrincipal` permet la création de la liste de contrôle d’accès même si le groupe n’existe pas encore dans le référentiel :

  ```
  {
    "scripts":[
      "set ACL for \"my-group;my-idp\"  (ACLOptions=ignoreMissingPrincipal)\r\n  allow jcr:read on /content/wknd/us/en/magazine\r\nend"
    ]
  }    
  ```

>[!NOTE]
>L’interface utilisateur Autorisations AEM peut être utilisée pour inspecter les listes de contrôle d’accès affectées aux principaux du groupe

## Exemple : configuration de l’authentification OIDC avec Azure Active Directory

### Configurer une nouvelle application dans Azure Active Directory {#configure-a-new-application-in-azure-ad}

1. Créez une application dans Azure Active Directory en vous reportant à la [documentation Azure Active Directory](https://learn.microsoft.com/fr-fr/power-pages/security/authentication/openid-settings#create-an-app-registration-in-azure).  Consultez ci-dessous l’écran montrant à quoi doit ressembler la vue d’ensemble de l’application :

   ![Vue d’ensemble de l’application](/help/security/assets/odic-application-overview.png)

1. Si des rôles de groupe ou d’application sont requis, reportez-vous à la [documentation](https://learn.microsoft.com/fr-fr/entra/external-id/customers/how-to-use-app-roles-customers) pour les activer pour l’application et les envoyer dans le jeton d’ID. Voici un exemple de groupes configurés :

![ID de jeton de réclamation OIDC](/help/security/assets/oidc-claim-id-token.png)

1. Suivez les étapes décrites précédemment pour créer les fichiers de configuration requis. Voici un exemple spécifique à Azure AD dans lequel :
   * Nous définissons le nom de la connexion OIDC, du gestionnaire d’authentification et de DefaultSyncHandler comme suit : `azure`
   * L’URL du site web est : `www.mywebsite.com`
   * Nous protégeons le `/content/wknd/us/en/adventures` de chemin d’accès accessible uniquement aux utilisateurs authentifiés membres du groupe `adventures`
   * Le client ou la cliente est : `tennat-id`,
   * L’ID de client ou cliente est : `client-id`,
   * Le secret est : `secret`,
   * Les groupes sont envoyés dans le jeton d’ID dans une réclamation appelée : `groups`.

### org.apache.sling.auth.oauth_client.impl.OidcConnectionImpl~azure.cfg.json

```
{
  "name":"azure",
  "scopes":[
    openid", "User.Read", "profile", "email"
  ],
  "baseUrl":"https://login.microsoftonline.com/tenant-id/v2.0",
  "clientId":"client-id",
  "clientSecret":"secret"
}
```

### org.apache.sling.auth.oauth_client.impl.OidcAuthenticationHandler~azure.cfg.json

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

### org.apache.jackrabbit.oak.spi.security.authentication.external.impl.ExternalLoginModuleFactory~azure.cfg.json

```
{
  "sync.handlerName":"azure",
  "idp.name":"azure"
}
```

### org.apache.jackrabbit.oak.spi.security.authentication.external.impl.DefaultSyncHandler~azure.cfg.json

```
{
  "user.expirationTime":"1h",
  "user.membershipExpTime":"1h",
  "group.expirationTime": "1d"
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

### org.apache.sling.jcr.repoinit.RepositoryInitializer~azure.cfg.json

```
{
  "scripts":[
    "set ACL for \"adventures;azure\"  (ACLOptions=ignoreMissingPrincipal)\r\n  allow jcr:read on /content/wknd/us/en/adventures\r\nend"
  ]
}
```

### org.apache.sling.auth.oauth_client.impl.SlingUserInfoProcessorImpl~azure.cfg.json

```
{
  "groupsInIdToken": "true",
  "storeAccessToken": "false",
  "storeRefreshToken": "false",
  "connection": "azure",
  "groupsClaimName": "groups"
}
```

### Informations supplémentaires sur les groupes Azure AD {#additional-information-about-azure-ad-groups}

Afin de configurer un groupe pour l’application d’entreprise dans le portail Microsoft Azure, vous devez rechercher l’application dans **Applications d’entreprise** et ajouter les groupes : <!-- Alexandru: this bit cound be clearer-->.

![Ajout de groupe OIDC](/help/security/assets/oidc-ad-additional-info.png)

Pour activer la revendication de groupe dans le jeton d’ID, ajoutez-la dans la section **Configuration du jeton** du portail Microsoft Azure : <!-- Alexandru: this bit cound be clearer as well-->.

![ID du jeton de réclamation OIDC](/help/security/assets/oidc-claim-id-token.png)

La configuration de `SlingUserInfoProcessor` doit être modifiée comme dans l’exemple ci-dessous.

Le nom de fichier qui doit être modifié est `org.apache.sling.auth.oauth_client.impl.SlingUserInfoProcessorImpl.cfg.json`. Le contenu doit être configuré comme suit :

```
{
  "connection": "azure",
  "groupsInIdToken": "true",
  "storeAccessToken": "false",
  "storeRefreshToken": "false"
}
```

## Comment migrer du gestionnaire d’authentification SAML vers le gestionnaire d’authentification OID

Lorsqu’AEM est déjà configuré avec un gestionnaire d’authentification SAML et que les utilisateurs sont présents dans le référentiel avec la [synchronisation des données](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/sites/authoring/personalization/user-and-group-sync-for-publish-tier#data-synchronization) activée, des conflits peuvent se produire entre les utilisateurs SAML d’origine et les nouveaux utilisateurs OIDC.

1. Configurez le [OidcAuthenticationHandler](#configure-oidc-authentication-handler) et activez le `idpNameInPrincipals` dans la configuration [SlingUserInfoProcessor](#configure-slinguserinfoprocessor)
1. Configuration [ACL pour les groupes externes](#configure-acl-for-external-groups).
1. Après la connexion des utilisateurs, les anciens utilisateurs créés par le gestionnaire d’authentification SAML peuvent être supprimés.

>[!NOTE]
>Une fois que le gestionnaire d’authentification SAML est désactivé et que le gestionnaire d’authentification OIDC est activé, si la [synchronisation des données](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/sites/authoring/personalization/user-and-group-sync-for-publish-tier#data-synchronization) n’est pas activée, les sessions existantes ne sont plus valides. Les utilisateurs devront s’authentifier à nouveau, ce qui entraîne la création de nœuds d’utilisateur OIDC dans le référentiel.

