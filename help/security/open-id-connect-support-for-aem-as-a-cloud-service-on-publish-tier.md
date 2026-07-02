---
title: Prise en charge d’Open ID Connect pour AEM as a Cloud Service au niveau publication
description: Découvrez comment configurer Open ID Connect (OIDC) pour AEM as a Cloud Service au niveau publication
feature: Security
role: Admin
exl-id: d2f30406-546c-4a2f-ba88-8046dee3e09b
source-git-commit: c7ab8608da31bf03863fdbe8682dd8d0d0a72fa1
workflow-type: tm+mt
source-wordcount: '3425'
ht-degree: 41%

---

# Prise en charge d’Open ID Connect pour AEM as a Cloud Service au niveau publication {#open-id-connect-support-for-aem-as-a-cloud-service-on-publish-tier}

## Présentation {#introduction}

À mesure que les organisations modernisent leurs expériences numériques, la gestion sécurisée et évolutive des identités devient une exigence fondamentale. Cloud Service d’Adobe Experience Manager (AEM) prend désormais en charge Open ID Connect (OIDC) au niveau publication, ce qui permet une intégration transparente et normalisée avec les principaux fournisseurs d’identité (IdP) tels qu’Entra ID (Azure AD), Google, Okta, Auth0, Ping Identity, ForgeRock et les fournisseurs d’identité pris en charge par OIDC.

OIDC est une couche d’identité qui se place sur le protocole OAuth 2.0 et qui permet une authentification robuste des personnes, tout en restant simple pour les développeurs et développeuses. Il est largement adopté pour les scénarios de business-to-consumer (B2C), d’intranet et de portails partenaires, où des fédérations d’identités et de connexion sécurisées sont requises.

Jusqu’à présent, les clientes et clients AEM devaient mettre en œuvre leur propre logique de connexion personnalisée au niveau publication, ce qui accroissait les délais de développement et introduisait des difficultés de maintenance et de sécurité à long terme. Grâce à la prise en charge native d’OIDC, AEM Cloud Service élimine cette responsabilité en proposant un mécanisme d’authentification sécurisé, extensible et pris en charge par Adobe pour les utilisateurs et utilisatrices qui accèdent aux environnements de publication.

Qu’il s’agisse de diffuser un site web client personnalisé ou un portail interne authentifié, OIDC installé au niveau publication simplifie la fédération des identités et réduit les risques grâce à une gouvernance d’identité centralisée. Il aide également les organisations à respecter les normes de conformité et de sécurité modernes sans sacrifier leur agilité.

## Configurer AEM pour l’authentification OIDC {#configure-aem-oidc-authentication}

### Prérequis {#prerequisits}

Nous supposons que les informations suivantes sont disponibles ou définies :

1. Chemins d’accès au contenu à protéger dans le référentiel AEM.
1. Identifiant de l’IdP à configurer. Il peut s’agir de n’importe quelle chaîne.

Informations provenant de la configuration d’IdP :

1. ID client configuré dans l’IdP.
1. Secret client configuré dans l’IdP. Si PKCE a été configuré sur l’IdP, le secret client n’est pas disponible. Ne stockez pas la valeur en texte brut dans le fichier de configuration. Utiliser un secret CM et le référencer
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

Dans certains environnements, le fournisseur d’identité (IdP) peut ne pas exposer un point d’entrée `.well-known` valide.Dans ce cas, les points d’entrée requis peuvent être définis manuellement en spécifiant les propriétés suivantes dans le fichier de configuration.Dans ce mode de configuration, la propriété `baseUrl` ne doit pas être définie.

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

1. Créez le fichier de configuration. Pour cet exemple, nous utiliserons `org.apache.sling.auth.oauth_client.impl.SlingUserInfoProcessorImpl~azure.cfg.json`. Le suffixe `azure` doit être un identifiant unique. Consultez un exemple du fichier de configuration ci-dessous :

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
   * `storeAccessToken` : true si le jeton d’accès doit être stocké dans le référentiel. Par défaut, cette valeur est définie sur false. Définissez-la sur true uniquement si AEM doit accéder aux ressources pour le compte de l’utilisateur ou l’utilisatrice stocké dans des serveurs externes protégés par le même IdP.
   * `storeRefreshToken` : true si le jeton d’actualisation doit être stocké dans le référentiel. Par défaut, cette valeur est définie sur false. Définissez-le sur true uniquement si AEM doit accéder aux ressources pour le compte de l’utilisateur stockées sur des serveurs externes protégés par le même IdP et doit actualiser le jeton à partir de l’IdP.
   * `idpNameInPrincipals` : lorsqu’il est défini sur true, le nom de l’IdP est ajouté comme suffixe aux principaux d’utilisateur et de groupe séparés par un « ; ». Par exemple, si le nom de l’IdP est `azure-idp` et que le nom d’utilisateur est `john.doe`, le principal stocké dans oak est `john.doe;azure-idp`. Cela s’avère utile lorsque plusieurs IDp sont configurés dans oak afin d’éviter les conflits entre les utilisateurs ou les groupes portant le même nom provenant de différents IDp. Vous pouvez également définir cette option pour éviter les conflits avec les utilisateurs ou les groupes créés par d’autres gestionnaires d’authentification tels que Saml.Notez que le jeton d’accès et le jeton d’actualisation sont stockés chiffrés avec la clé principale AEM.


### Configurer le gestionnaire de synchronisation {#configure-the-synchronization-handler}

Au moins un gestionnaire de synchronisation doit être configuré pour synchroniser les utilisateurs authentifiés dans Oak. Pour plus d’informations, consultez [cette page](https://jackrabbit.apache.org/oak/docs/security/authentication/external/defaultusersync.html).

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

Pendant le développement, les délais d’expiration peuvent être réduits à une valeur inférieure (par exemple : 1 s) afin d’accélérer les tests de synchronisation des utilisateurs et des groupes dans oak.Vous trouverez ci-dessous certains des attributs les plus pertinents à configurer dans DefaultSyncHandler. Notez que l’appartenance à un groupe dynamique doit toujours être activée dans les services cloud.

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

L’utilisateur est authentifié par un jeton d’ID et des attributs supplémentaires sont récupérés à partir du point d’entrée `userInfo` défini pour l’IdP. Le `UserInfoProcessor` est chargé de transformer les données reçues du fournisseur d’identité en informations d’identification et attributs qu’AEM peut utiliser pour la synchronisation des utilisateurs.

#### Quand créer un UserInfoProcessor personnalisé {#when-to-create-custom-userinfoprocessor}

La valeur par défaut [SlingUserInfoProcessorImpl](https://github.com/apache/sling-org-apache-sling-auth-oauth-client/blob/master/src/main/java/org/apache/sling/auth/oauth_client/impl/SlingUserInfoProcessorImpl.java) gère les revendications OIDC standard et la synchronisation des groupes. Vous aurez peut-être besoin d’une implémentation personnalisée si vous devez :

* Extraire et traiter des revendications personnalisées à partir du jeton d’ID ou de la réponse UserInfo
* Transformer ou mapper des revendications à différents noms d’attribut
* Implémenter une logique personnalisée pour l’extraction de groupe à partir de revendications imbriquées
* Ajouter des attributs utilisateur supplémentaires qui ne font pas partie du profil OIDC standard
* Traiter les jetons d’accès ou actualiser les jetons pour des cas d’utilisation spécifiques
* Intégration à des systèmes externes pour enrichir les données utilisateur lors de l’authentification

#### Présentation de l’interface UserInfoProcessor {#understanding-userinfoprocessor-interface}

L’interface `UserInfoProcessor` du package `org.apache.sling.auth.oauth_client.spi` définit deux méthodes :

```java
public interface UserInfoProcessor {
    /**
     * Process the UserInfo and token response to create OIDC credentials
     *
     * @param userInfo - JSON response from the UserInfo endpoint (may be null)
     * @param tokenResponse - JSON response from the token endpoint
     * @param oidcSubject - The subject claim from the ID token
     * @param idp - The configured IDP name
     * @return OidcAuthCredentials containing user attributes and group memberships
     */
    @NotNull OidcAuthCredentials process(
        @Nullable String userInfo,
        @NotNull String tokenResponse,
        @NotNull String oidcSubject,
        @NotNull String idp
    );

    /**
     * @return The name of the OIDC connection this processor is associated with
     */
    @NotNull String connection();
}
```

L’objet `OidcAuthCredentials` renvoyé vous permet d’effectuer les opérations suivantes :
* Définir les attributs utilisateur via `setAttribute(key, value)` : ils sont synchronisés en fonction des mappages de propriété `DefaultSyncHandler`
* Ajouter des appartenances à des groupes via `addGroup(groupName)` - ces groupes sont créés/synchronisés dans AEM

#### Exemple : implémentation de UserInfoProcessor personnalisée {#custom-userinfoprocessor-implementation}

Vous trouverez ci-dessous un exemple complet montrant comment implémenter un `UserInfoProcessor` personnalisé :

```java
package com.mycompany.aem.auth;

import java.nio.charset.StandardCharsets;
import java.util.Base64;

import org.apache.sling.auth.oauth_client.spi.OidcAuthCredentials;
import org.apache.sling.auth.oauth_client.spi.UserInfoProcessor;
import org.jetbrains.annotations.NotNull;
import org.jetbrains.annotations.Nullable;
import org.osgi.service.component.annotations.Activate;
import org.osgi.service.component.annotations.Component;
import org.osgi.service.metatype.annotations.AttributeDefinition;
import org.osgi.service.metatype.annotations.Designate;
import org.osgi.service.metatype.annotations.ObjectClassDefinition;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import com.google.gson.JsonObject;
import com.google.gson.JsonParser;

/**
 * Custom UserInfoProcessor that extracts additional claims from the ID token
 * and adds custom user attributes and group memberships.
 */
@Component(service = UserInfoProcessor.class, property = {"service.ranking:Integer=50"})
@Designate(ocd = CustomUserInfoProcessor.Config.class, factory = true)
public class CustomUserInfoProcessor implements UserInfoProcessor {

    private static final Logger logger = LoggerFactory.getLogger(CustomUserInfoProcessor.class);

    @ObjectClassDefinition(name = "Custom UserInfo Processor")
    @interface Config {
        @AttributeDefinition(name = "Connection Name", description = "OIDC Connection Name")
        String connection();
    }

    private final String connection;

    @Activate
    public CustomUserInfoProcessor(Config config) {
        this.connection = config.connection();
        logger.info("CustomUserInfoProcessor activated for connection: {}", connection);
    }

    @Override
    public @NotNull OidcAuthCredentials process(
            @Nullable String userInfo,
            @NotNull String tokenResponse,
            @NotNull String oidcSubject,
            @NotNull String idp) {

        // Parse the token response to extract tokens
        JsonObject tokenJson = JsonParser.parseString(tokenResponse).getAsJsonObject();
        String accessToken = tokenJson.has("access_token") ?
            tokenJson.get("access_token").getAsString() : null;
        String idToken = tokenJson.has("id_token") ?
            tokenJson.get("id_token").getAsString() : null;

        logger.debug("Processing authentication for subject: {}", oidcSubject);

        // Decode and extract claims from ID Token
        JsonObject claims = null;
        if (idToken != null) {
            claims = decodeJwtPayload(idToken);
            logger.debug("Extracted claims from ID token: {}", claims);
        }

        // Create credentials object
        OidcAuthCredentials credentials = new OidcAuthCredentials(oidcSubject, idp);
        credentials.setAttribute(".token", "");

        // Extract standard profile attributes
        if (claims != null) {
            // Standard OIDC claims
            setAttributeIfPresent(credentials, claims, "given_name", "profile/given_name");
            setAttributeIfPresent(credentials, claims, "family_name", "profile/family_name");
            setAttributeIfPresent(credentials, claims, "email", "profile/email");
            setAttributeIfPresent(credentials, claims, "name", "profile/name");

            // Custom claims from your IdP
            setAttributeIfPresent(credentials, claims, "department", "profile/department");
            setAttributeIfPresent(credentials, claims, "employee_id", "profile/employeeId");
            setAttributeIfPresent(credentials, claims, "job_title", "profile/jobTitle");
        }

        // Extract group memberships from claims
        if (claims != null && claims.has("groups")) {
            if (claims.get("groups").isJsonArray()) {
                claims.get("groups").getAsJsonArray().forEach(group -> {
                    credentials.addGroup(group.getAsString());
                });
            }
        }

        // Optionally store tokens if needed for later API calls
        // Note: Only store tokens if your application needs to call external APIs
        // on behalf of the user. Tokens are encrypted before storage.
        if (accessToken != null) {
            credentials.setAttribute("access_token", accessToken);
        }

        return credentials;
    }

    @Override
    public @NotNull String connection() {
        return connection;
    }

    /**
     * Helper method to set attribute if present in claims
     */
    private void setAttributeIfPresent(OidcAuthCredentials credentials,
                                      JsonObject claims,
                                      String claimName,
                                      String attributeName) {
        if (claims.has(claimName) && !claims.get(claimName).isJsonNull()) {
            String value = claims.get(claimName).getAsString();
            if (value != null && !value.isEmpty()) {
                credentials.setAttribute(attributeName, value);
            }
        }
    }

    /**
     * Decode JWT payload (middle part) to extract claims
     */
    private JsonObject decodeJwtPayload(String jwt) {
        try {
            String[] parts = jwt.split("\\.");
            if (parts.length != 3) {
                logger.warn("Invalid JWT format");
                return null;
            }

            // Decode the payload (second part)
            String payload = parts[1];
            // Add padding if needed
            payload = payload + "====".substring(0, (4 - payload.length() % 4) % 4);
            // Replace URL-safe characters
            payload = payload.replace('-', '+').replace('_', '/');

            byte[] decoded = Base64.getDecoder().decode(payload);
            String json = new String(decoded, StandardCharsets.UTF_8);
            return JsonParser.parseString(json).getAsJsonObject();
        } catch (Exception e) {
            logger.error("Failed to decode JWT payload", e);
            return null;
        }
    }
}
```

#### Configuration {#custom-userinfoprocessor-configuration}

Créez un fichier de configuration pour votre `UserInfoProcessor` personnalisé dans votre projet AEM sous `ui.config/src/main/content/jcr_root/apps/myapp/osgiconfig/config.publish/` :

**com.mycompany.aem.auth.CustomUserInfoProcessor~azure.cfg.json**

```json
{
  "connection": "azure"
}
```

La configuration doit correspondre au nom de connexion défini dans votre configuration `OidcConnectionImpl`. La propriété `service.ranking` dans l’annotation `@Component` (définie sur `50` dans l’exemple) détermine la priorité si plusieurs processeurs sont enregistrés pour la même connexion. Les classements supérieurs sont prioritaires sur le `SlingUserInfoProcessorImpl` par défaut (qui possède un classement de `0`).

#### Dépendances {#custom-userinfoprocessor-dependencies}

Ajoutez les dépendances suivantes au `pom.xml` de votre module principal :

```xml
<dependency>
    <groupId>org.apache.sling</groupId>
    <artifactId>org.apache.sling.auth.oauth-client</artifactId>
    <version>0.1.7</version>
    <scope>provided</scope>
</dependency>
<dependency>
    <groupId>com.google.code.gson</groupId>
    <artifactId>gson</artifactId>
    <version>2.8.9</version>
    <scope>provided</scope>
</dependency>
```

#### Synchronisation des attributs avec DefaultSyncHandler {#synchronizing-custom-attributes}

Pour vous assurer que vos attributs personnalisés sont conservés dans les nœuds utilisateur dans le JCR, mettez à jour votre configuration `DefaultSyncHandler` pour inclure des mappages de propriété :

**org.apache.jackrabbit.oak.spi.security.authentication.external.impl.DefaultSyncHandler~azure.cfg.json**

```json
{
  "user.expirationTime": "1h",
  "user.membershipExpTime": "1h",
  "user.propertyMapping": [
    "profile/givenName=profile/given_name",
    "profile/familyName=profile/family_name",
    "rep:fullname=profile/name",
    "profile/email=profile/email",
    "profile/department=profile/department",
    "profile/employeeId=profile/employeeId",
    "profile/jobTitle=profile/jobTitle",
    "access_token=access_token"
  ],
  "user.pathPrefix": "azure",
  "handler.name": "azure"
}
```

Le format est `jcrPropertyPath=credentialAttributeName`. Le côté gauche est l’endroit où la propriété est stockée dans le nœud utilisateur sous `/home/users`, et le côté droit correspond au nom d’attribut que vous avez défini dans le `UserInfoProcessor` à l’aide de `credentials.setAttribute()`.

#### Déploiement et tests {#custom-userinfoprocessor-deployment}

1. **Générez et déployez** votre projet AEM contenant le `UserInfoProcessor` personnalisé :

   ```bash
   mvn clean install -PautoInstallPackage
   ```

2. **Vérifiez l’enregistrement** dans la console OSGi sur `/system/console/components` :
   * Recherchez le nom de votre classe de processeur personnalisée
   * Vérifiez que le composant est actif et que la configuration de connexion est correcte

3. **Test du flux d’authentification** :
   * Accès à un chemin protégé configuré dans votre `OidcAuthenticationHandler`
   * Une fois l’authentification réussie, vérifiez le nœud utilisateur dans CRXDE à l’adresse `/home/users/<prefix>/<username>`
   * Vérifier que les attributs personnalisés sont synchronisés
   * Vérifier les appartenances aux groupes sous `/home/groups`

4. **Activez la journalisation du débogage** pour résoudre les problèmes :

   ```
   Logger: com.mycompany.aem.auth
   Log Level: DEBUG
   ```

#### Bonnes pratiques {#custom-userinfoprocessor-best-practices}

* **Réduire le stockage des jetons** : stockez uniquement les jetons d’accès ou actualisez les jetons si votre application doit effectuer des appels API vers des services externes pour le compte des utilisateurs et utilisatrices. Les jetons sont chiffrés, mais ajoutent une surcharge.
* **Valider les revendications** : vérifiez toujours si les revendications existent et ne sont pas nulles avant de les traiter.
* **Gestion des erreurs** : consignez les erreurs de manière appropriée, mais assurez-vous que le flux d’authentification peut se terminer même si des revendications facultatives sont manquantes.
* **Performances** : allégez la logique de traitement, car elle s’exécute à chaque authentification.
* **Sécurité** : ne consignez jamais d’informations sensibles telles que des jetons complets ou des mots de passe utilisateur. Utilisez `substring()` si vous enregistrez des jetons à des fins de débogage.
* **Tests** : effectuez des tests avec divers profils utilisateur de votre fournisseur d’identité pour vous assurer que toutes les variations de réclamation sont gérées correctement.

### Configuration de la liste de contrôle d’accès pour les groupes externes {#configure-acl-for-external-groups}

Lorsque les utilisateurs sont authentifiés via OIDC, leurs appartenances à un groupe sont généralement synchronisées à partir du fournisseur d’identité externe.Ces groupes externes sont créés dynamiquement dans le référentiel AEM, mais ne sont pas automatiquement associés à des entrées de contrôle d’accès.Pour que les utilisateurs disposent des autorisations appropriées, des listes de contrôle d’accès (ACL) doivent être explicitement définies pour ces groupes.

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
   * Client : `tennat-id`,
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

## Redirection personnalisée après l’authentification {#custom-redirect-after-authentication}

Par défaut, après une authentification OIDC réussie, les utilisateurs sont redirigés vers l’URL demandée à l’origine. Vous pouvez toutefois personnaliser ce comportement à l’aide du paramètre de requête `redirect`.

### Utilisation du paramètre de redirection

Lors du lancement de l’authentification, vous pouvez spécifier une URL de redirection personnalisée en ajoutant le paramètre `redirect` à votre requête d’authentification :

```
/content/wknd/us/en/adventures?redirect=/content/wknd/us/en/welcome
```

Dans cet exemple, après une authentification réussie, l’utilisateur est redirigé vers `/content/wknd/us/en/welcome` au lieu de la page demandée d’origine.

### Contraintes de sécurité

Pour des raisons de sécurité, le paramètre `redirect` présente les restrictions suivantes :

* **Doit être un chemin relatif** : l’URL de redirection doit commencer par `/` (par exemple, `/content/mysite/dashboard`).
* **Pas de redirections intersites** : les URL absolues (par exemple, `https://external-site.com`) ne sont pas autorisées
* **Aucune URL relative au protocole** : les URL commençant par `//` sont rejetées pour empêcher les redirections relatives au protocole

Si une URL de redirection non valide est fournie, l’authentification échoue avec une erreur.

### Exemples de cas d’utilisation

1. **Page d’accueil après la connexion** : redirigez les utilisateurs vers une page d’accueil personnalisée après leur première connexion

   ```
   /content/mysite/secure-area?redirect=/content/mysite/welcome
   ```

2. **Redirection de tableau de bord** : redirigez les utilisateurs vers un tableau de bord spécifique après l’authentification

   ```
   /content/mysite/login?redirect=/content/mysite/user/dashboard
   ```

3. **Liaison profonde** : permet aux utilisateurs de s’authentifier, puis d’accéder à une ressource spécifique

   ```
   /content/mysite/protected?redirect=/content/mysite/protected/specific-document
   ```

## Configurer la déconnexion unique {#configure-single-logout}

Par défaut, la déconnexion d’AEM efface uniquement la session AEM locale (cookie de connexion). La session de l’utilisateur sur le fournisseur d’identité (IdP) reste active. Revenir à un chemin protégé peut donc réauthentifier l’utilisateur en silence sans demander à nouveau ses informations d’identification.

Pour mettre également fin à la session au niveau de l’IdP, AEM prend en charge la **Déconnexion unique initiée par SP** (également appelée Déconnexion initiée par RP *RP*, comme défini par la [&#x200B; Spécification de connexion initiée par RP OpenID Connect &#x200B;](https://openid.net/specs/openid-connect-rpinitiated-1_0.html)). Lorsqu’il est activé, AEM redirige le navigateur vers la `end_session_endpoint` de l’IdP afin que ce dernier puisse mettre fin à sa propre session avant de renvoyer l’utilisateur vers une page configurée.

### Fonctionnement de la déconnexion unique {#how-single-logout-works}

1. L’utilisateur déclenche la déconnexion, généralement en demandant une `/system/sling/logout?resource=<protected-path>`. Le paramètre `resource` permet à l’authentificateur Sling d’acheminer la déconnexion vers le gestionnaire d’authentification OIDC approprié.
1. AEM efface le cookie de connexion local.
1. AEM redirige le navigateur vers le `end_session_endpoint` de l’IdP, en ajoutant :
   * `post_logout_redirect_uri` : emplacement auquel l&#39;IdP doit envoyer l&#39;utilisateur après la déconnexion.
   * `id_token_hint` : jeton d’ID stocké par l’utilisateur (le cas échéant), dont de nombreux IdP ont besoin pour se déconnecter sans invite.
1. L’IdP met fin à sa session et redirige le navigateur vers le `post_logout_redirect_uri`.

Si la déconnexion unique initiée par le fournisseur de services est désactivée ou si l’IdP n’expose pas de `end_session_endpoint`, la déconnexion efface simplement la session AEM locale.

### Modifications de configuration requises {#single-logout-configuration}

L’activation de la déconnexion unique nécessite des modifications dans les quatre fichiers de configuration décrits précédemment dans ce document.

#### &#x200B;1. Ajouter le `end_session_endpoint` à la connexion OIDC {#single-logout-connection}

La `endSessionEndpoint` est l’URL de l’IdP utilisée pour mettre fin à la session IdP.

* Lorsque la connexion est configurée avec un `baseUrl` (c’est-à-dire que l’IdP expose un point d’entrée `.well-known` valide), le `end_session_endpoint` est lu automatiquement à partir des métadonnées du fournisseur et ne doit **pas** être défini explicitement.
* Lorsque les points d’entrée sont configurés manuellement (pas de `baseUrl`) ou que les métadonnées de l’IdP n’annoncent pas un `end_session_endpoint`, définissez-le explicitement.

**org.apache.sling.auth.oauth_client.impl.OidcConnectionImpl~azure.cfg.json**

```
{
  "name":"azure",
  "scopes":[
    "openid"
  ],
  "baseUrl":"https://login.microsoftonline.com/tenant-id/v2.0",
  "clientId":"client-id",
  "clientSecret":"secret",
  "endSessionEndpoint":"https://login.microsoftonline.com/tenant-id/oauth2/v2.0/logout"
}
```

#### &#x200B;2. Activer la déconnexion initiée par SP sur le gestionnaire d&#39;authentification {#single-logout-handler}

**org.apache.sling.auth.oauth_client.impl.OidcAuthenticationHandler~azure.cfg.json**

```
{
  "path":[
    "/content/wknd/us/en/adventures"
  ],
  "callbackUri":"https://www.mywebsite.com/content/wknd/us/en/adventures/j_security_check",
  "idp":"azure",
  "defaultConnectionName":"azure",
  "enableSPInitiatedSingleLogout":true,
  "logoutRedirectPath":"/content/wknd/us/en/logout-complete",
  "logoutRedirectAllowedHosts":[
    "www.mywebsite.com"
  ]
}
```

Configurez les propriétés comme suit :

* `enableSPInitiatedSingleLogout` : définissez sur `true` pour rediriger vers le `end_session_endpoint` de l’IdP lors de la déconnexion. Lorsqu’elle est `false` (valeur par défaut), la déconnexion efface uniquement la session AEM locale.
* `logoutRedirectPath` : chemin d’accès redirigé par l’IdP après la déconnexion. Il est utilisé comme `post_logout_redirect_uri`. La valeur par défaut est `/`.
* `logoutRedirectAllowedHosts` : **obligatoire lorsque `enableSPInitiatedSingleLogout` est `true`.** Liste des noms d’hôte autorisés dans le `post_logout_redirect_uri`. Cela empêche les attaques open-redirect via `Host` usurpation d’en-tête : si l’hôte de requête ne figure pas dans cette liste, le premier hôte autorisé est utilisé à la place.

>[!IMPORTANT]
>Si `enableSPInitiatedSingleLogout` est `true` mais `logoutRedirectAllowedHosts` est vide, le gestionnaire d’authentification **ne parvient pas à activer**. Il s’agit d’une protection délibérée contre les vulnérabilités de redirection ouverte. Répertoriez toujours tous les noms d’hôte public à partir desquels les utilisateurs se déconnectent.

#### &#x200B;3. Stocker le jeton d’ID pour `id_token_hint` {#single-logout-store-id-token}

La plupart des IdP nécessitent le paramètre `id_token_hint` pour terminer la déconnexion sans demander confirmation à l&#39;utilisateur. Pour rendre le jeton d’ID disponible au moment de la déconnexion, activez `storeIdToken` dans la configuration `SlingUserInfoProcessor`. Le jeton d’ID est chiffré avec la clé principale d’AEM avant d’être stocké.

**org.apache.sling.auth.oauth_client.impl.SlingUserInfoProcessorImpl~azure.cfg.json**

```
{
  "connection": "azure",
  "groupsInIdToken": true,
  "groupsClaimName": "groups",
  "storeAccessToken": false,
  "storeRefreshToken": false,
  "storeIdToken": true
}
```

* `storeIdToken` : définissez sur `true` pour stocker le jeton d’ID (chiffré) afin qu’il puisse être envoyé en tant que `id_token_hint` lors de la déconnexion. La valeur par défaut est `false`.

#### &#x200B;4. Conservation du jeton d’ID via le gestionnaire de synchronisation {#single-logout-sync-id-token}

Pour que le jeton d’ID stocké soit lisible lors de la déconnexion, ajoutez un mappage `id_token` au mappage des propriétés `DefaultSyncHandler` afin qu’il soit conservé sur le nœud utilisateur.

**org.apache.jackrabbit.oak.spi.security.authentication.external.impl.DefaultSyncHandler~azure.cfg.json**

```
{
  "user.expirationTime":"1h",
  "user.membershipExpTime":"1h",
  "group.expirationTime": "1d",
  "user.propertyMapping":[
    "profile/givenName=profile/given_name",
    "profile/familyName=profile/family_name",
    "rep:fullname=profile/name",
    "profile/email=profile/email",
    "id_token=id_token"
  ],
  "user.pathPrefix":"azure",
  "handler.name":"azure"
}
```

Le format de mappage est `jcrPropertyPath=credentialAttributeName`. Le `id_token=id_token` d’entrée conserve le jeton d’ID chiffré défini par le `SlingUserInfoProcessor` sur le nœud de l’utilisateur, où le gestionnaire de déconnexion le lit à nouveau pour créer le `id_token_hint`.

>[!IMPORTANT]
>Le jeton d’ID est conservé sur le nœud utilisateur et doit être disponible sur l’instance de publication qui gère la demande de déconnexion. Au niveau Publication, les nœuds utilisateur ne sont propagés entre les instances que lorsque la [synchronisation des données](/help/sites-cloud/authoring/personalization/user-and-group-sync-for-publish-tier.md#data-synchronization) est activée. Activez la synchronisation des données afin que le jeton d’ID stocké soit disponible pour l’instance qui traite la déconnexion, sinon le `id_token_hint` pourrait être manquant.

>[!NOTE]
>Si le jeton d’ID n’est pas stocké (ou ne peut pas être lu), la déconnexion se poursuit (AEM redirige vers le `end_session_endpoint` sans `id_token_hint`). En fonction de l’IdP, l’utilisateur peut alors être invité à confirmer la déconnexion.

### Personnalisation de la redirection après la déconnexion {#single-logout-redirect-parameter}

De la même manière que pour le flux de connexion, la destination après la déconnexion peut être remplacée par requête en ajoutant un paramètre `redirect` à la requête de déconnexion :

```
/system/sling/logout?resource=/content/wknd/us/en/adventures&redirect=/content/wknd/us/en/goodbye
```

Les mêmes contraintes de sécurité que la [redirection de connexion](#custom-redirect-after-authentication) s’appliquent : la valeur doit être un **chemin relatif** (commençant par un seul `/`) et l’hôte qui en résulte est validé par rapport à `logoutRedirectAllowedHosts`. Si la validation du paramètre `redirect` échoue, AEM revient au `logoutRedirectPath` configuré.

## Comment migrer du gestionnaire d’authentification SAML vers le gestionnaire d’authentification OID

Lorsqu’AEM est déjà configuré avec un gestionnaire d’authentification SAML et que les utilisateurs sont présents dans le référentiel avec la [synchronisation des données](/help/sites-cloud/authoring/personalization/user-and-group-sync-for-publish-tier.md#data-synchronization) activée, des conflits peuvent se produire entre les utilisateurs SAML d’origine et les nouveaux utilisateurs OIDC.

1. Configurez le [OidcAuthenticationHandler](#configure-oidc-authentication-handler) et activez le `idpNameInPrincipals` dans la configuration [SlingUserInfoProcessor](#configure-slinguserinfoprocessor)
1. Configuration [ACL pour les groupes externes](#configure-acl-for-external-groups).
1. Après la connexion des utilisateurs, les anciens utilisateurs créés par le gestionnaire d’authentification SAML peuvent être supprimés.

>[!NOTE]
>Une fois que le gestionnaire d’authentification SAML est désactivé et que le gestionnaire d’authentification OIDC est activé, si la [synchronisation des données](/help/sites-cloud/authoring/personalization/user-and-group-sync-for-publish-tier.md#data-synchronization) n’est pas activée, les sessions existantes ne sont plus valides. Les utilisateurs devront s’authentifier à nouveau, ce qui entraîne la création de nœuds d’utilisateur OIDC dans le référentiel.

