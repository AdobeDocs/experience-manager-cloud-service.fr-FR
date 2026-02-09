---
title: Migration vers une identité externe et l’appartenance à un groupe dynamique
description: Guide technique pour la migration des utilisateurs et des groupes locaux vers un modèle d’identité externe avec appartenance à un groupe dynamique dans AEM as a Cloud Service
solution: Experience Manager Sites
feature: Security
role: Developer, Admin
source-git-commit: bb4b60523f60b1285c5f2fd2e49f6cc8cff24324
workflow-type: tm+mt
source-wordcount: '2232'
ht-degree: 1%

---

# Migration vers une identité externe et l’appartenance à un groupe dynamique {#migrating-to-external-identity}

## Vue d’ensemble {#overview}

Lorsque la [synchronisation des données](/help/sites-cloud/authoring/personalization/user-and-group-sync-for-publish-tier.md#data-synchronization) est activée dans AEM as a Cloud Service, le gestionnaire d’authentification SAML peut être configuré pour migrer automatiquement vers des identités externes avec appartenance à un groupe dynamique lorsqu’il gère la création d’utilisateurs et de groupes. Si votre projet utilise du code personnalisé pour créer des utilisateurs ou des groupes, vous devez le mettre à jour pour créer des utilisateurs et des groupes externes, par opposition aux utilisateurs et groupes locaux.

### Pourquoi des utilisateurs et des groupes externes sont-ils requis ? {#why-external-required}

La migration des utilisateurs et groupes locaux vers des identités externes avec appartenance à un groupe dynamique est essentielle pour plusieurs raisons essentielles :

**Optimisation des performances :**

* **Écritures réduites dans le référentiel** : l’appartenance traditionnelle à un groupe local nécessite l’écriture des relations d’appartenance dans le référentiel dans une seule propriété à valeurs multiples du nœud de groupe. Avec l’appartenance à un groupe dynamique, les utilisateurs disposent d’une seule propriété `rep:externalPrincipalNames` contenant tous les principaux du groupe, ce qui élimine la nécessité de synchroniser le nœud de groupe
* **Synchronisation plus rapide** : lors de la synchronisation des utilisateurs sur les nœuds de niveau publication, les utilisateurs externes appartenant à un groupe dynamique nécessitent beaucoup moins de transferts de données et d’opérations d’écriture que les utilisateurs locaux appartenant à un groupe traditionnel
* **Évolutivité** : les systèmes comptant un grand nombre d’utilisateurs et de groupes bénéficient considérablement d’une réduction de la surcharge liée aux référentiels. L’appartenance à un groupe dynamique évolue efficacement même avec des groupes très volumineux.

Ce document fournit des conseils techniques pour :

* Comprendre le modèle d’identité externe
* Modification du code personnalisé pour créer des utilisateurs et des groupes externes
* Migration des utilisateurs et groupes locaux existants vers le modèle d’identité externe

## Compréhension de l’identité externe {#understanding-external-identity}

### External Users {#external-users}

Les utilisateurs externes sont identifiés par la propriété `rep:externalId` , qui lie l’utilisateur à un fournisseur d’identité externe. Le format est :

```
userId;idpName
```

Par exemple : `john.doe;saml-idp`.

>[!NOTE]
>
> `idpName` fait référence au nom du fournisseur d’identité (Idp) Oak tel que défini dans la configuration du gestionnaire d’authentification. Pour les intégrations SAML, il s’agit de la valeur définie pour l’attribut `idpIdentifier` dans le gestionnaire d’authentification SAML.

**Propriétés de la clé :**

* `rep:externalId` : propriété obligatoire qui marque un utilisateur comme étant externe (par exemple, `john.doe;saml-idp`)
* `rep:externalPrincipalNames` : propriété à plusieurs valeurs contenant des principaux de groupe externes pour l’appartenance dynamique
* `rep:lastSynced` : date et heure de la dernière synchronisation
* `rep:lastDynamicSync` : date et heure de la dernière synchronisation d’appartenance à un groupe dynamique

### Groupes externes {#external-groups}

Les groupes externes sont également identifiés par la propriété `rep:externalId` et utilisent un format de nom principal :

```
groupId;idpName
```

Par exemple : `content-authors;saml-idp`

### Appartenance à un groupe dynamique {#dynamic-group-membership}

Au lieu de relations directes utilisateur à groupe stockées dans le référentiel, l’appartenance à un groupe dynamique utilise la propriété `rep:externalPrincipalNames` sur le nœud utilisateur . Lorsque l’utilisateur possède un nom principal externe correspondant à l’ID d’un groupe externe, il devient automatiquement membre de ce groupe. Pour plus d’informations, consultez la [documentation d’Apache Oak](https://jackrabbit.apache.org/oak/docs/security/authentication/external/dynamic.html).

**Avantages :**

* Écritures réduites dans le référentiel (aucun nœud d’appartenance à un groupe n’est modifié lorsque des utilisateurs sont ajoutés/supprimés de groupes)
* Synchronisation plus rapide sur les nœuds de niveau publication
* Gestion évolutive de l’appartenance à un groupe
* Compatible avec les exigences de synchronisation des données

## Configuration de l’utilisateur du service {#service-user-configuration}

Toutes les opérations qui créent ou modifient des utilisateurs et des groupes externes doivent être effectuées à l’aide d’un **utilisateur de service** correctement configuré pour contourner la protection par défaut sur les propriétés `rep:externalId` et `rep:externalPrincipalNames`.

### Pourquoi un utilisateur du service est-il requis ? {#why-is-a-service-user-required}

Par défaut, la sécurité d’Oak empêche les sessions régulières de modifier les propriétés protégées telles que :

* `rep:externalId` - Marque les utilisateurs/groupes comme externes
* `rep:externalPrincipalNames` - Stocke les principaux d’appartenance à un groupe dynamique

Seul un utilisateur de service correctement configuré peut modifier ces propriétés.

### Configuration et mappage des utilisateurs de services {#service-user-configuration-mapping}

La configuration d’un utilisateur de service pour gérer les identités externes nécessite trois configurations coordonnées :

1. Créer l’utilisateur du service via `repoinit`
2. Configuration de la protection `ExternalPrincipal`
3. Mappez l’utilisateur du service à votre lot d’applications.

Consultez ci-dessous une description détaillée de ces étapes.

#### Étape 1 : créer l’utilisateur du service via Repoinit {#create-the-serviice-user-via-repoinit}

Cette étape décrit la création de l’utilisateur du service avec les autorisations nécessaires à l’aide d’un script `repoinit`.

**Fichier de configuration :** `org.apache.sling.jcr.repoinit.RepositoryInitializer~group-provisioner.cfg.json`

**Emplacement exemplaire :** `ui.config/src/main/content/jcr_root/apps/yourproject/osgiconfig/config.publish/`

```json
{
  "scripts": [
    "create service user group-provisioner with path system/yourproject",
    "set ACL for group-provisioner\n  allow jcr:read,jcr:readAccessControl,jcr:modifyAccessControl,rep:userManagement,rep:write on /home/users\n  allow jcr:read,jcr:readAccessControl,jcr:modifyAccessControl,rep:userManagement,rep:write on /home/groups\nend"
  ]
}
```

**Présentation des autorisations**

* `jcr:read` : lire les utilisateurs et les groupes
* `jcr:readAccessControl` : lire les listes de contrôle d’accès
* `jcr:modifyAccessControl` : modification des listes ACL (nécessaire pour définir les propriétés)
* `rep:userManagement` : créer et gérer des utilisateurs/groupes
* `rep:write` : propriétés d’écriture, y compris `rep:externalId` et `rep:externalPrincipalNames`

>[!NOTE]
>
>L’utilisateur du service est créé sous `/home/users/system/yourproject` pour conserver son organisation avec d’autres utilisateurs du système.

#### Étape 2 : Configurer la protection ExternalPrincipal {#configure-externalprincipal-protection}

Vous trouverez ci-dessous un exemple de configuration pour placer en liste blanche l’utilisateur du service afin qu’il puisse contourner la protection appliquée aux propriétés d’identité externes.

**Nom du fichier de configuration :** `org.apache.jackrabbit.oak.spi.security.authentication.external.impl.principal.ExternalPrincipalConfiguration.cfg.json`

**Exemple d’emplacement :** `ui.config/src/main/content/jcr_root/apps/yourproject/osgiconfig/config.publish/`

```json
{
  "protectExternalIdentities": "Warn",
  "systemPrincipalNames": [
    "group-provisioner",
    "saml-migration-service"
  ]
}
```

**Propriétés de configuration :**

* `protectExternalIdentities` : contrôle le niveau de protection des propriétés d’identité externe :
   * `"Strict"` : seuls les principaux de système de la liste autorisée peuvent modifier les propriétés externes. Il s’agit du niveau recommandé pour la production.
   * `"Warn"` : consigne les avertissements, mais autorise les modifications. Utile pour le développement/test.
   * `"None"` : aucune protection. Non recommandé.
* `systemPrincipalNames` : liste des noms d’utilisateur de service autorisés à modifier les `rep:externalId` et les `rep:externalPrincipalNames`. Incluez tous les utilisateurs du service qui doivent gérer des identités externes (par exemple, `group-provisioner`, `saml-migration-service`).

>[!IMPORTANT]
>
>Les noms d’utilisateur de service dans `systemPrincipalNames` doivent correspondre exactement aux ID d’utilisateur de service créés dans le script repoinit.

#### Étape 3 : Mappage des utilisateurs du service {#service-user-mapping}

Mappez l’utilisateur du service à votre lot d’applications afin que votre code puisse l’utiliser.

**Fichier de configuration :** `org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended~group-provisioner.cfg.json`

**Location:** `ui.config/src/main/content/jcr_root/apps/yourproject/osgiconfig/config.publish/`

```json
{
  "user.mapping": [
    "yourproject.core:group-provisioner=[group-provisioner]"
  ]
}
```

**Format de mappage :**

* `yourproject.core` : nom symbolique du lot (figurant dans `pom.xml` `<Bundle-SymbolicName>`)
* `group-provisioner` (avant `=`) : nom du sous-service que vous utiliserez dans le code
* `[group-provisioner]` (après `=`) : ID d’utilisateur de service réel créé dans repoinit

### Utilisation de l’utilisateur du service dans le code {#using-the-service-user-in-code}

Lors de l’ouverture d’une session pour effectuer des opérations de migration ou de création d’utilisateurs/groupes, vous devez utiliser l’utilisateur du service :

```java
import org.apache.sling.jcr.api.SlingRepository;

@Reference
private SlingRepository repository;

// Login as the service user
Session serviceSession = repository.loginService("group-provisioner", null);

try {
    UserManager userManager = ((JackrabbitSession) serviceSession).getUserManager();
    // Perform operations...
    serviceSession.save();
} finally {
    if (serviceSession != null && serviceSession.isLive()) {
        serviceSession.logout();
    }
}
```

>[!IMPORTANT]
>
>Si la configuration utilisateur du service n’est pas correcte, les tentatives de définition de `rep:externalId` ou `rep:externalPrincipalNames` échoueront avec des erreurs d’autorisation. Assurez-vous que l’utilisateur du service est correctement configuré dans la configuration `ExternalPrincipal` avant de tenter la migration.

## Exemple de configuration complète {#complete-configuration-example}

Vous trouverez ci-dessous un exemple complet montrant l’ensemble des trois configurations :

### Structure de fichier {#file-structure}

```
ui.config/src/main/content/jcr_root/apps/yourproject/osgiconfig/
└── config.publish/
    ├── org.apache.sling.jcr.repoinit.RepositoryInitializer~group-provisioner.cfg.json
    ├── org.apache.jackrabbit.oak.spi.security.authentication.external.impl.principal.ExternalPrincipalConfiguration.cfg.json
    └── org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended~group-provisioner.cfg.json
```

### Modification du code personnalisé {#modifying-custom-code}

#### Création d’utilisateurs externes {#creating-external-users}

**Before (Local User) :**

```java
UserManager userManager = ((JackrabbitSession) session).getUserManager();
User user = userManager.createUser(userId, password);
```

**Après (Utilisateur Externe) :**

```java
import org.apache.jackrabbit.oak.spi.security.authentication.external.ExternalIdentityRef;

UserManager userManager = ((JackrabbitSession) session).getUserManager();
ValueFactory valueFactory = session.getValueFactory();

// Create user with principal
Principal userPrincipal = new Principal() {
    @Override
    public String getName() {
        return userId;
    }
};

User user = userManager.createUser(userId, null, userPrincipal, null);

// Set rep:externalId
ExternalIdentityRef externalRef = new ExternalIdentityRef(userId, idpName);
String externalId = externalRef.getString(); // Format: userId;idpName
user.setProperty("rep:externalId", valueFactory.createValue(externalId));

// Set sync timestamps to far future (workaround for OAK-12079)
// Set to 10 years in the future to prevent premature cleanup of external group memberships
// See: https://issues.apache.org/jira/browse/OAK-12079
java.util.Calendar future = java.util.Calendar.getInstance();
future.add(java.util.Calendar.YEAR, 10);
user.setProperty("rep:lastSynced", valueFactory.createValue(future));
user.setProperty("rep:lastDynamicSync", valueFactory.createValue(future));

session.save();
```

#### Création de groupes externes {#creating-external-groups}

**Before (Local Group) :**

```java
UserManager userManager = ((JackrabbitSession) session).getUserManager();
Group group = userManager.createGroup(groupId);
```

**Après (Groupe Externe) :**

```java
import org.apache.jackrabbit.oak.spi.security.authentication.external.ExternalIdentityRef;

UserManager userManager = ((JackrabbitSession) session).getUserManager();
ValueFactory valueFactory = session.getValueFactory();

// Create group with principal
Principal groupPrincipal = new Principal() {
    @Override
    public String getName() {
        return groupId;
    }
};

Group group = userManager.createGroup(groupPrincipal);

// Set rep:externalId
ExternalIdentityRef externalRef = new ExternalIdentityRef(groupId, idpName);
String externalId = externalRef.getString(); // Format: groupId;idpName
group.setProperty("rep:externalId", valueFactory.createValue(externalId));

session.save();
```

#### Attribution d’une appartenance à un groupe dynamique {#assigning-dynamic-membership}

**Before (Direct Membership) :**

```java
Group group = (Group) userManager.getAuthorizable(groupId);
User user = (User) userManager.getAuthorizable(userId);
group.addMember(user);
```

**Après (Abonnement Dynamique) :**

```java
User user = (User) userManager.getAuthorizable(userId);
ValueFactory valueFactory = session.getValueFactory();

// Get existing external principal names
Value[] existingValues = user.getProperty("rep:externalPrincipalNames");
List<String> principalNames = new ArrayList<>();

if (existingValues != null) {
    for (Value value : existingValues) {
        principalNames.add(value.getString());
    }
}

// Add new principal name (format: groupId;idpName)
String dynamicGroupPrincipal = groupId + ";" + idpName;
if (!principalNames.contains(dynamicGroupPrincipal)) {
    principalNames.add(dynamicGroupPrincipal);
    
    // Create new Value array
    Value[] newValues = new Value[principalNames.size()];
    for (int i = 0; i < principalNames.size(); i++) {
        newValues[i] = valueFactory.createValue(principalNames.get(i));
    }
    
    // Set the property
    user.setProperty("rep:externalPrincipalNames", newValues);
    
    // Update sync timestamps to far future (workaround for OAK-12079)
    // Set to 10 years in the future to prevent premature cleanup of external group memberships
    // See: https://issues.apache.org/jira/browse/OAK-12079
    java.util.Calendar future = java.util.Calendar.getInstance();
    future.add(java.util.Calendar.YEAR, 10);
    user.setProperty("rep:lastDynamicSync", valueFactory.createValue(future));
    user.setProperty("rep:lastSynced", valueFactory.createValue(future));
}

session.save();
```

## Processus de migration {#migration-process}

La migration des utilisateurs et groupes locaux existants vers l’identité externe n’est pas nécessaire lorsque le code personnalisé a été mis à jour avant l’activation des services de synchronisation des données.

Si des utilisateurs et des groupes locaux ont déjà été conservés dans le référentiel et que l’environnement est utilisé activement, nous vous recommandons d’effectuer une migration en plusieurs étapes comme celle-ci, afin d’éviter les perturbations ou les incohérences.

>[!IMPORTANT]
>
>Toutes les étapes de migration doivent être exécutées à l’aide d’un utilisateur du service correctement configuré (par exemple, `group-provisioner`) qui a reçu les autorisations pour contourner la protection sur les propriétés `rep:externalId` et `rep:externalPrincipalNames`. Voir [Configuration utilisateur du service](#service-user-configuration) pour plus d’informations.

### Étape 1 : Créer une structure de groupe externe {#step-1-create-external-group-structure}

Pour chaque groupe local qui doit être migré :

1. Créez un groupe externe correspondant avec le nom principal : `<localGroupId>;<idpName>`. Utilisez une convention de nommage qui permet de lier des groupes externes à des groupes locaux
1. Définissez la propriété `rep:externalId` sur le groupe externe avec les valeurs suivantes : `<localGroupId>;<idpName>`
1. Ajoutez le groupe externe comme membre du groupe local d’origine.

**Validation**

* Vous pouvez valider les résultats en vérifiant si chaque groupe local possède un groupe externe correspondant. En outre, chaque groupe externe est membre du groupe local correspondant.

**Exemple de point d’entrée de servlet :**

```java
@SlingServletPaths("/bin/migration/step1")
public class MigrationStep1Servlet extends SlingAllMethodsServlet {
    
    @Override
    protected void doPost(SlingHttpServletRequest request, 
                          SlingHttpServletResponse response) {
        String groupPath = request.getParameter("groupPath");
        String idpName = request.getParameter("idpName");

        // Check if the caller is authorized to run the servlet
        isAuthorizedCaller(request, response);

        // Get local group
        Authorizable localGroupAuth = userManager.getAuthorizableByPath(groupPath);
        Group localGroup = (Group) localGroupAuth;
        String localGroupId = localGroup.getID();
        
        // Create external group
        String externalGroupPrincipalName = localGroupId + ";" + idpName;
        // The function createExternalGroup performs the following steps:
        // 1. Creates a new external group with the given principal name (format: "<localGroupId>;<idpName>").
        // 2. Sets the 'rep:externalId' property on the group to mark it as an external group (value: "<localGroupId>;<idpName>").
        // 3. Sets the 'rep:principalName' property for the group if required.
        // 4. Assigns any other required group metadata, such as a title or description, if needed.
        // 5. Persists the new group node in the repository at the appropriate path under /home/groups.
        // 6. Returns the created Group object so it can be used for further operations, such as membership assignment.
        Group externalGroup = createExternalGroup(externalGroupPrincipalName, localGroupId, idpName);
        
        // Add external group to local group
        localGroup.addMember(externalGroup);
        
        session.save();
    }
}
```

**Usage:**

```bash
curl -X POST "http://localhost:4503/bin/migration/step1?groupPath=/home/groups/c/content-authors&idpName=saml-idp"
```

### Étape 2 : convertir des utilisateurs et affecter une appartenance dynamique {#step-2-convert-users-and-assign-dynamic-membership}

Pour chaque utilisateur qui est membre d’un groupe local :

1. Assurez-vous qu’il a `rep:externalId` défini (convertissez-le en utilisateur externe si nécessaire).
1. Pour chaque appartenance à un groupe, ajoutez le principal de groupe externe correspondant à `rep:externalPrincipalNames`
1. Mettre à jour les horodatages de synchronisation

>[!IMPORTANT]
>
>Ignorer les groupes système comme « tout le monde » pendant ce processus.

**Exemple de point d’entrée de servlet :**

```java
@SlingServletPaths("/bin/migration/step2")
public class MigrationStep2Servlet extends SlingAllMethodsServlet {
    
    @Override
    protected void doPost(SlingHttpServletRequest request, 
                          SlingHttpServletResponse response) {
        String userId = request.getParameter("userId");
        String idpName = request.getParameter("idpName");
        
        // Check if the caller is authorized to run the servlet
        isAuthorizedCaller(request, response);

        // Login as the service user
        Session serviceSession = repository.loginService("group-provisioner", null);

        try {
            UserManager userManager = ((JackrabbitSession) serviceSession).getUserManager();
            User user = (User) userManager.getAuthorizable(userId);
            
            // Ensure user has rep:externalId
            Value[] externalIdValues = user.getProperty("rep:externalId");
            if (externalIdValues == null || externalIdValues.length == 0) {
                ExternalIdentityRef externalRef = new ExternalIdentityRef(userId, idpName);
                user.setProperty("rep:externalId", 
                            valueFactory.createValue(externalRef.getString()));
            }
            
            // Get all group memberships
            Iterator<Group> groupIterator = user.declaredMemberOf();
            List<String> principalNames = new ArrayList<>();
            
            while (groupIterator.hasNext()) {
                Group group = groupIterator.next();
                String groupId = group.getID();
                
                // Skip system groups
                if ("everyone".equals(groupId)) {
                    continue;
                }
                
                // Add dynamic group principal
                String dynamicGroupPrincipal = groupId + ";" + idpName;
                principalNames.add(dynamicGroupPrincipal);
            }
            
            // Set rep:externalPrincipalNames
            if (!principalNames.isEmpty()) {
                Value[] newValues = new Value[principalNames.size()];
                for (int i = 0; i < principalNames.size(); i++) {
                    newValues[i] = valueFactory.createValue(principalNames.get(i));
                }
                user.setProperty("rep:externalPrincipalNames", newValues);
            }
            
            // Update timestamps to far future (workaround for OAK-12079)
            // Set to 10 years in the future to prevent premature cleanup of external group memberships
            // See: https://issues.apache.org/jira/browse/OAK-12079
            java.util.Calendar future = java.util.Calendar.getInstance();
            future.add(java.util.Calendar.YEAR, 10);
            user.setProperty("rep:lastDynamicSync", valueFactory.createValue(future));
            user.setProperty("rep:lastSynced", valueFactory.createValue(future));
        
        // Perform operations...
        serviceSession.save();
    } finally {
        if (serviceSession != null && serviceSession.isLive()) {
            serviceSession.logout();
        }
}    }
}
```

**Usage:**

```bash
curl -X POST "http://localhost:4503/bin/migration/step2?userId=john.doe&idpName=saml-idp"
```

**Validation**

Vous pouvez le valider en vérifiant que chaque utilisateur dispose des attributs `rep:externalId` et `rep:externalPrincipalName` avec le `principalName` de chaque groupe externe. Les utilisateurs sont membres des groupes locaux *et* des groupes externes.

### Étape 3 : Supprimer les appartenances directes des utilisateurs {#step-3-remove-direct-user-memberships}

Une fois l’appartenance à un groupe dynamique configurée pour les utilisateurs :

1. Supprimer les appartenances directes des utilisateurs des groupes locaux
1. Conserver les appartenances de groupe à groupe (y compris les appartenances à un groupe externe)

**Exemple de point d’entrée de servlet :**

```java
@SlingServletPaths("/bin/migration/step3")
public class MigrationStep3Servlet extends SlingAllMethodsServlet {
    
    @Override
    protected void doPost(SlingHttpServletRequest request, 
                          SlingHttpServletResponse response) {

        // Check if the caller is authorized to run the servlet
        isAuthorizedCaller(request, response);

        String groupPath = request.getParameter("groupPath");
        
        Authorizable localGroupAuth = userManager.getAuthorizableByPath(groupPath);
        Group localGroup = (Group) localGroupAuth;
        
        // Process each member
        Iterator<Authorizable> members = localGroup.getDeclaredMembers();
        
        while (members.hasNext()) {
            Authorizable member = members.next();
            
            // Remove only user members, keep group members
            if (!member.isGroup()) {
                localGroup.removeMember(member);
            }
        }
        
        session.save();
    }
}
```

**Usage:**

```bash
curl -X POST "http://localhost:4503/bin/migration/step3?groupPath=/home/groups/c/content-authors"
```

**Validation**

* Vous pouvez le valider en vérifiant que chaque groupe local n’a comme membre que le groupe externe correspondant ou d’autres groupes.


## Workflow de migration {#migration-workflow}

### Liste de contrôle préalable à la migration {#pre-migration-checklist}

* [ ] **Configurer l’utilisateur du service** : créez et configurez l’utilisateur du service (par exemple, `group-provisioner`) avec les autorisations appropriées
* [ ] **Vérifier la configuration ExternalPrincipal** : Assurez-vous que l’utilisateur du service est configuré pour contourner la protection sur `rep:externalId` et `rep:externalPrincipalNames`
* [ ] **Tester les autorisations utilisateur du service** : vérifiez que l’utilisateur du service peut définir des propriétés d’identité externes en cours de développement
* [ ] Identifier tout le code personnalisé qui crée des utilisateurs ou des groupes
* [ ] Vérifier et mettre à jour le code personnalisé pour utiliser le modèle d’identité externe
* [ ] Tester le code mis à jour dans l’environnement de développement
* [ ] Inventaire de tous les utilisateurs et groupes locaux existants à migrer
* [ ] Test du processus de migration dans les environnements inférieurs

### Étapes d’exécution {#execution-steps}

1. **Déployer le code mis à jour** : déployez les modifications de code personnalisé pour créer des utilisateurs/groupes externes

1. **Créer des groupes externes** (pour chaque groupe local) :

   ```bash
   curl -X POST "http://localhost:4503/bin/migration/step1?groupPath=/home/groups/g/my-group&idpName=saml-idp"
   ```

1. **Migrer les utilisateurs** (pour chaque utilisateur) :

   ```bash
   curl -X POST "http://localhost:4503/bin/migration/step2?userId=username&idpName=saml-idp"
   ```

1. **Nettoyage** (pour chaque groupe migré) :

   ```bash
   curl -X POST "http://localhost:4503/bin/migration/step3?groupPath=/home/groups/g/my-group"
   ```

1. **Vérifier** : vérifier les appartenances aux groupes d’utilisateurs et tester les autorisations d’accès

1. **Activer la synchronisation des données** : contactez le service clientèle pour activer la fonctionnalité

### Validation après migration {#post-migration-validation}

Vérifiez la migration :

1. **Vérifiez les propriétés de l’utilisateur** :

   Sur les nœuds utilisateur, vérifiez la présence de :

   * `rep:externalId` : le format doit être `userId;idpName`
   * `rep:externalPrincipalNames` : tableau des principaux de groupe au format `groupId;idpName`
   * `rep:lastSynced` : horodatage défini sur un avenir lointain (environ 10 ans à partir de la date de migration)
   * `rep:lastDynamicSync` : horodatage défini sur un avenir lointain (environ 10 ans à partir de la date de migration)

   **Remarque** : les horodatages sont délibérément définis sur une date lointaine comme solution de contournement pour OAK-12079. Il s’agit d’un comportement attendu.

1. **Vérifier les propriétés du groupe** :

   Sur les nœuds de groupe locaux, vérifiez la présence de :

   * Membre de groupe externe avec `groupId;idpName` de format
   * Aucun membre utilisateur direct (uniquement après l’étape 3)

1. **Tester la connexion utilisateur** : vérifiez que les utilisateurs peuvent se connecter et disposent des autorisations appropriées

1. **Tester le contrôle d’accès** : vérifier que les utilisateurs peuvent accéder au contenu protégé par des CUG/ACL

## Résolution des problèmes {#troubleshooting}

### Problèmes courants {#common-issues}

**Problème : erreurs d’autorisation lors de la définition de `rep:externalId` ou de`rep:externalPrincipalNames`**

**Messages d’erreur :**

* `javax.jcr.AccessDeniedException: Access denied`
* `OakAccess0000: Access denied`
* `Cannot set property 'rep:externalId'`

**Solution** : la session doit être ouverte à l’aide d’un utilisateur de service correctement configuré et disposant d’autorisations lui permettant de contourner la protection sur les propriétés d’identité externes.

**Étapes à résoudre :**

1. **Vérifier que l’utilisateur du service existe** : assurez-vous que l’utilisateur du service (par exemple, `group-provisioner`) est créé via repoinit
1. **Vérifier le mappage utilisateur du service** : vérifiez que le servlet ou le service utilise `repository.loginService("group-provisioner", null)`
1. **Vérifier la configuration de ExternalPrincipal** : Vérifiez que `org.apache.jackrabbit.oak.spi.security.authentication.external.impl.principal.ExternalPrincipalConfiguration` est correctement configuré
1. **Vérification des autorisations utilisateur du service** : l’utilisateur du service a besoin d’autorisations `rep:write` et `rep:userManagement` sur `/home/users` et `/home/groups`

Consultez [Configuration utilisateur du service](#service-user-configuration) pour obtenir des instructions de configuration complètes.

**Problème :`OakConstraint0072: Property 'rep:externalPrincipalNames' requires 'rep:externalId' to be present`**

**Solution** : les utilisateurs doivent avoir `rep:externalId` définis avant de `rep:externalPrincipalNames`. Assurez-vous que l’étape 2 convertit d’abord les utilisateurs en utilisateurs externes.

**Problème : les utilisateurs perdent leurs appartenances à un groupe après la migration**

**Solution** : vérifiez que :

* Le groupe externe a été créé avec le format de nom principal correct (`groupId;idpName`)
* Le groupe externe a été ajouté en tant que membre du groupe local (étape 1)
* L’utilisateur dispose de noms principaux externes corrects dans `rep:externalPrincipalNames` (étape 2)
* Le nettoyage de l’étape 3 n’a été effectué qu’une fois les étapes 1 et 2 terminées

**Problème : les appartenances à un groupe externe sont supprimées de manière inattendue après la connexion de l’utilisateur (OAK-12079)**

**Problème** : en raison du bug Oak [OAK-12079](https://issues.apache.org/jira/browse/OAK-12079), le mécanisme de synchronisation d’Oak peut nettoyer prématurément les appartenances à des groupes externes en fonction des horodatages `rep:lastSynced` et `rep:lastDynamicSync`.

**Solution** : définissez les horodatages `rep:lastSynced` et `rep:lastDynamicSync` sur une date ultérieure éloignée (dans 10 ans) au lieu de l’heure actuelle. Cela empêche le processus de nettoyage de la synchronisation de supprimer les appartenances aux groupes externes.

**Implémentation :**

```java
// Workaround for OAK-12079
// Set to 10 years in the future to prevent premature cleanup
// See: https://issues.apache.org/jira/browse/OAK-12079
java.util.Calendar future = java.util.Calendar.getInstance();
future.add(java.util.Calendar.YEAR, 10);
user.setProperty("rep:lastSynced", valueFactory.createValue(future));
user.setProperty("rep:lastDynamicSync", valueFactory.createValue(future));
```

**Pourquoi cela fonctionne** : en définissant la date et l’heure à une date ultérieure éloignée, la logique de synchronisation d’Oak traite ces utilisateurs comme « récemment synchronisés » et ne déclenche pas le processus de nettoyage qui supprimerait les noms principaux externes et les appartenances à un groupe.

**Remarque** : il s’agit d’une solution temporaire en attendant la résolution d’OAK-12079 dans une prochaine version d’Oak. Tous les exemples de code de ce document incluent déjà cette solution.

**Problème : le groupe système « Tout le monde » provoque des erreurs**

**Solution** : toujours ignorer le groupe système « Tout le monde » lors de la migration des utilisateurs (étape 2). Ce groupe est automatiquement géré par AEM.

### Procédure de restauration {#rollback-procedure}

Si la migration rencontre des problèmes :

1. Arrêter le processus de migration
1. Restauration à partir de la sauvegarde si des données critiques ont été affectées
1. Annulez les modifications apportées au code pour créer des utilisateurs et des groupes externes avec une appartenance à un groupe dynamique
1. Examinez et corrigez les problèmes avant de tenter à nouveau la migration.

## Bonnes pratiques {#best-practices}

* **Test approfondi** : testez toujours la migration dans les environnements de développement et d’évaluation avant la production
* **Traitement par lots** : pour les bases d’utilisateurs volumineuses, traitez les migrations par lots pour éviter les problèmes de délai d’expiration
* **Surveillance des performances** : observez les performances du référentiel lors de la migration.
* **Tenir à jour le journal d’audit** : consignez toutes les opérations de migration à des fins de dépannage.
* **Autorisations des utilisateurs des services** : assurez-vous que les servlets de migration utilisent les utilisateurs des services appropriés avec les autorisations requises. L’utilisateur du service doit être configuré dans la configuration ExternalPrincipal pour contourner la protection sur les propriétés `rep:externalId` et `rep:externalPrincipalNames`
* **Opérations idempotentes** : concevez un code de migration à réexécuter en toute sécurité
* **Valider à chaque étape** : vérifiez les résultats après chaque étape de migration avant de continuer

## Sécurisation des servlets de migration {#securing-migration-servlets}

Les servlets de migration disposent de privilèges élevés pour créer et modifier des utilisateurs et des groupes. Il est essentiel de restreindre l’accès à ces points d’entrée pour empêcher tout accès non autorisé.

### Approche recommandée : authentification du compte technique IMS {#recommended-approach-ims-technical-account}

L’approche recommandée consiste à sécuriser ces servlets à l’aide de l’intégration Adobe IMS, en autorisant uniquement un compte technique autorisé à y accéder.

#### Étape 1 : Création d&#39;un compte technique dans AEM Developer Console {#create-a-technical-account-in-aem-developer-console}

1. Accédez à [Experience Manager](https://experience.adobe.com/) puis à **Cloud Manager**
1. Sélectionnez votre programme, puis cliquez sur l’environnement dans lequel vous souhaitez créer le compte technique
1. Cliquez sur **Developer Console** dans le menu ... de l’environnement
1. Dans AEM Developer Console, accédez à l’onglet **Intégrations**
1. Cliquez sur **Créer un compte technique**
1. Attribuez un nom à l’intégration (par exemple, « Compte de service de migration »)
1. Cliquer sur **Créer**
1. Notez les valeurs suivantes de l’intégration créée :
   * **Identifiant client**
   * **Secret client**
   * **ID de compte technique** (il s’agit de l’ID d’utilisateur accédant à vos servlets - format : `XXXXXXXXXXXXXXXXXXXXXXXX@techacct.adobe.com`)

Pour obtenir des instructions détaillées, voir [Documentation sur la génération de jetons d’accès pour les API côté serveur](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md).

Exemple de code pour vérifier si l’appelant est autorisé :

```
    private boolean isAuthorizedCaller(SlingHttpServletRequest request, 
                                       SlingHttpServletResponse response) {

        Session session = request.getResourceResolver().adaptTo(Session.class);
        String callerId = session != null ? session.getUserID() : null;
               
        if (!ALLOWED_TECHNICAL_ACCOUNT.equals(callerId)) {
            LOG.warn("Unauthorized access attempt by user: '{}' (expected: '{}')", callerId,   ALLOWED_TECHNICAL_ACCOUNT);
            response.setStatus(SlingHttpServletResponse.SC_FORBIDDEN);
            return false;
        }
        
        return true;
    }
```

### Défense en profondeur : restrictions basées sur IP {#defense-in-depth-ip-based-restrictions}

Comme couche de sécurité supplémentaire, vous pouvez configurer des règles de réseau CDN pour restreindre l’accès aux points d’entrée de migration par adresse IP. Cela s’avère utile lorsque les migrations sont exécutées à partir d’une infrastructure connue.

>[!NOTE]
>
>Les restrictions d’adresses IP seules ne sont pas suffisantes. Toujours combiner avec les contrôles d’authentification comme décrit ci-dessus.

### Liste de contrôle de sécurité {#security-checklist}

Avant de déployer les servlets de migration vers la production :

* [ ] Créer une intégration IMS dans AEM Developer Console
* [ ] Configurer des servlets pour valider l’identifiant de compte technique
* [ Flux d’authentification ] Test dans les environnements de développement/d’évaluation
* [ ] Envisager des restrictions supplémentaires basées sur les adresses IP au niveau du réseau CDN
* [ ] Planifier la désactivation ou la suppression des servlets de migration une fois la migration terminée
* [ ] l’audit et consignez tous les accès aux points d’entrée de migration.

>[!IMPORTANT]
>
>Une fois la migration terminée, envisagez de désactiver ou de supprimer les servlets de migration de votre déploiement afin d’éliminer tout risque de sécurité potentiel.

## Ressources supplémentaires {#additional-resources}

* [Synchronisation des utilisateurs et des groupes pour le niveau de publication](/help/sites-cloud/authoring/personalization/user-and-group-sync-for-publish-tier.md)
* [Gestionnaire d’authentification SAML 2.0](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/authentication/saml-2-0.html?lang=fr)
* [Fournisseur d’identité externe](https://jackrabbit.apache.org/oak/docs/security/authentication/externalloginmodule.html)
* [Appartenance à un groupe dynamique](https://jackrabbit.apache.org/oak/docs/security/authentication/external/dynamic.html)
